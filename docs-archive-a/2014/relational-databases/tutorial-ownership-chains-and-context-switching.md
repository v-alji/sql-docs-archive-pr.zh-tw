---
title: 教學課程：擁有權鏈結和內容切換 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- context switching [SQL Server], tutorials
- ownership chains [SQL Server]
ms.assetid: db5d4cc3-5fc5-4cf5-afc1-8d4edc1d512b
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e9072a68dd3179e5900fda06d4fea58b484a37e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593910"
---
# <a name="tutorial-ownership-chains-and-context-switching"></a><span data-ttu-id="486ce-102">Tutorial: Ownership Chains and Context Switching</span><span class="sxs-lookup"><span data-stu-id="486ce-102">Tutorial: Ownership Chains and Context Switching</span></span>
  <span data-ttu-id="486ce-103">這個教學課程利用案例來說明涉及擁有權鏈結和使用者內容切換的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安全性概念。</span><span class="sxs-lookup"><span data-stu-id="486ce-103">This tutorial uses a scenario to illustrate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] security concepts involving ownership chains and user context switching.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="486ce-104">若要執行本教學課程中的程式碼，您必須設定使用混合模式安全性，並已安裝 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="486ce-104">To run the code in this tutorial you must have both Mixed Mode security configured and the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database installed.</span></span> <span data-ttu-id="486ce-105">如需混合模式安全性的詳細資訊，請參閱 [選擇驗證模式](security/choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="486ce-105">For more information about Mixed Mode security, see [Choose an Authentication Mode](security/choose-an-authentication-mode.md).</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="486ce-106">狀況</span><span class="sxs-lookup"><span data-stu-id="486ce-106">Scenario</span></span>  
 <span data-ttu-id="486ce-107">在此狀況中，有兩位使用者需要使用其帳戶來存取 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫內儲存的採購訂單資料。</span><span class="sxs-lookup"><span data-stu-id="486ce-107">In this scenario, two users need accounts to access purchase order data stored in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="486ce-108">需求如下：</span><span class="sxs-lookup"><span data-stu-id="486ce-108">The requirements are as follows:</span></span>  
  
-   <span data-ttu-id="486ce-109">第一個帳戶 (TestManagerUser) 必須能夠看見每筆訂單的所有詳細資料。</span><span class="sxs-lookup"><span data-stu-id="486ce-109">The first account (TestManagerUser) must be able to see all details in every purchase order.</span></span>  
  
-   <span data-ttu-id="486ce-110">第二個帳戶 (TestEmployeeUser) 必須能夠看見訂單號碼、訂貨日期、送貨日期、產品識別碼，以及已部分送達的每筆訂單所採購和收到的貨品數量。</span><span class="sxs-lookup"><span data-stu-id="486ce-110">The second account (TestEmployeeUser) must be able to see the purchase order number, order date, shipping date, product ID numbers, and the ordered and received items per purchase order, by purchase order number, for items where partial shipments have been received.</span></span>  
  
-   <span data-ttu-id="486ce-111">其餘所有帳戶必須保有各自現行的權限。</span><span class="sxs-lookup"><span data-stu-id="486ce-111">All other accounts must retain their current permissions.</span></span>  
  
 <span data-ttu-id="486ce-112">為了滿足此案例的需求，範例將拆成四部分示範擁有權鏈結和內容切換的概念：</span><span class="sxs-lookup"><span data-stu-id="486ce-112">To fulfill the requirements of this scenario, the example is broken into four parts that demonstrate the concepts of ownership chains and context switching:</span></span>  
  
1.  <span data-ttu-id="486ce-113">設定環境。</span><span class="sxs-lookup"><span data-stu-id="486ce-113">Configuring the environment.</span></span>  
  
2.  <span data-ttu-id="486ce-114">建立預存程序用於存取訂單資料。</span><span class="sxs-lookup"><span data-stu-id="486ce-114">Creating a stored procedure to access data by purchase order.</span></span>  
  
3.  <span data-ttu-id="486ce-115">透過預存程序存取資料。</span><span class="sxs-lookup"><span data-stu-id="486ce-115">Accessing the data through the stored procedure.</span></span>  
  
4.  <span data-ttu-id="486ce-116">重設環境。</span><span class="sxs-lookup"><span data-stu-id="486ce-116">Resetting the environment.</span></span>  
  
 <span data-ttu-id="486ce-117">此範例會在每個程式碼區塊中各行附上說明。</span><span class="sxs-lookup"><span data-stu-id="486ce-117">Each code block in this example is explained in line.</span></span> <span data-ttu-id="486ce-118">若要複製整個範例，請參閱本教學課程結尾處的＜ [完整範例](#CompleteExample) ＞一節。</span><span class="sxs-lookup"><span data-stu-id="486ce-118">To copy the complete example, see [Complete Example](#CompleteExample) at the end of this tutorial.</span></span>  
  
## <a name="1-configure-the-environment"></a><span data-ttu-id="486ce-119">1.設定環境</span><span class="sxs-lookup"><span data-stu-id="486ce-119">1. Configure the Environment</span></span>  
 <span data-ttu-id="486ce-120">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 和下列程式碼來開啟 `AdventureWorks2012` 資料庫，然後使用 `CURRENT_USER` [!INCLUDE[tsql](../includes/tsql-md.md)] 語句來檢查 dbo 使用者是否顯示為內容。</span><span class="sxs-lookup"><span data-stu-id="486ce-120">Use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and the following code to open the `AdventureWorks2012` database, and use the `CURRENT_USER` [!INCLUDE[tsql](../includes/tsql-md.md)] statement to check that the dbo user is displayed as the context.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
```  
  
 <span data-ttu-id="486ce-121">如需 CURRENT_USER 陳述式的詳細資訊，請參閱 [CURRENT_USER &#40;Transact-SQL&#41;](/sql/t-sql/functions/current-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="486ce-121">For more information about the CURRENT_USER statement, see [CURRENT_USER &#40;Transact-SQL&#41;](/sql/t-sql/functions/current-user-transact-sql).</span></span>  
  
 <span data-ttu-id="486ce-122">使用下列程式碼，以 dbo 使用者身分在伺服器和 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫中建立兩位使用者。</span><span class="sxs-lookup"><span data-stu-id="486ce-122">Use this code as the dbo user to create two users on the server and in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
GO  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
```  
  
 <span data-ttu-id="486ce-123">如需 CREATE USER 陳述式的詳細資訊，請參閱 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="486ce-123">For more information about the CREATE USER statement, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span> <span data-ttu-id="486ce-124">如需 CREATE LOGIN 陳述式的詳細資訊，請參閱 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="486ce-124">For more information about the CREATE LOGIN statement, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
 <span data-ttu-id="486ce-125">使用下列陳述式，將 `Purchasing` 結構描述的擁有權變更為 `TestManagerUser` 帳戶。</span><span class="sxs-lookup"><span data-stu-id="486ce-125">Use the following code to change the ownership of the `Purchasing` schema to the `TestManagerUser` account.</span></span> <span data-ttu-id="486ce-126">這樣一來，該帳戶對結構描述內含物件就具備了所有的資料操作語言 (DML) 陳述式存取權 (例如 `SELECT` 和 `INSERT` 權限)。</span><span class="sxs-lookup"><span data-stu-id="486ce-126">This allows that account to use all Data Manipulation Language (DML) statement access (such as `SELECT` and `INSERT` permissions) on the objects it contains.</span></span> <span data-ttu-id="486ce-127">`TestManagerUser` 也已獲授與建立預存程序的能力。</span><span class="sxs-lookup"><span data-stu-id="486ce-127">`TestManagerUser` is also granted the ability to create stored procedures.</span></span>  
  
```  
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
```  
  
 <span data-ttu-id="486ce-128">如需 GRANT 陳述式的詳細資訊，請參閱 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="486ce-128">For more information about the GRANT statement, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).</span></span> <span data-ttu-id="486ce-129">如需預存程序的詳細資訊，請參閱[預存程序 &#40;Database Engine&#41;](stored-procedures/stored-procedures-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="486ce-129">For more information about stored procedures, see [Stored Procedures &#40;Database Engine&#41;](stored-procedures/stored-procedures-database-engine.md).</span></span> <span data-ttu-id="486ce-130">如需擁有權限的海報 [!INCLUDE[ssDE](../includes/ssde-md.md)] ，請參閱 [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf) 。</span><span class="sxs-lookup"><span data-stu-id="486ce-130">For a poster of all [!INCLUDE[ssDE](../includes/ssde-md.md)] permissions, see [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf).</span></span>  
  
## <a name="2-create-a-stored-procedure-to-access-data"></a><span data-ttu-id="486ce-131">2.建立預存程序來存取資料</span><span class="sxs-lookup"><span data-stu-id="486ce-131">2. Create a Stored Procedure to Access Data</span></span>  
 <span data-ttu-id="486ce-132">若要在資料庫內切換內容，請使用 EXECUTE AS 陳述式。</span><span class="sxs-lookup"><span data-stu-id="486ce-132">To switch context within a database, use the EXECUTE AS statement.</span></span> <span data-ttu-id="486ce-133">EXECUTE AS 則需要 IMPERSONATE 權限。</span><span class="sxs-lookup"><span data-stu-id="486ce-133">EXECUTE AS requires IMPERSONATE permissions.</span></span>  
  
 <span data-ttu-id="486ce-134">下列程式碼使用 `EXECUTE AS` 陳述式將內容變更為 `TestManagerUser` ，並建立預存程序單僅顯示 `TestEmployeeUser`所需的資料。</span><span class="sxs-lookup"><span data-stu-id="486ce-134">Use the `EXECUTE AS` statement in the following code to change the context to `TestManagerUser` and create a stored procedure showing only the data required by `TestEmployeeUser`.</span></span> <span data-ttu-id="486ce-135">為了滿足需求，預存程序接受訂單號碼做為變數且並未顯示財務資訊，而 WHERE 子句則將結果限制在已部分送達的貨品。</span><span class="sxs-lookup"><span data-stu-id="486ce-135">To satisfy the requirements, the stored procedure accepts one variable for the purchase order number and does not display financial information, and the WHERE clause limits the results to partial shipments.</span></span>  
  
```  
EXECUTE AS LOGIN = 'TestManagerUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader a  
      INNER JOIN Purchasing.PurchaseOrderDetail b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END  
GO  
```  
  
 <span data-ttu-id="486ce-136">目前 `TestEmployeeUser` 尚無權存取任何資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="486ce-136">Currently `TestEmployeeUser` does not have access to any database objects.</span></span> <span data-ttu-id="486ce-137">下列程式碼 (內容仍是 `TestManagerUser` ) 將授與該使用者帳戶透過預存程序查詢基底資料表資訊的能力。</span><span class="sxs-lookup"><span data-stu-id="486ce-137">The following code (still in the `TestManagerUser` context) grants the user account the ability to query base-table information through the stored procedure.</span></span>  
  
```  
GRANT EXECUTE  
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO  
```  
  
 <span data-ttu-id="486ce-138">儘管並未明確指定結構描述，此預存程序係屬 `Purchasing` 結構描述的一部分，因為 `TestManagerUser` 預設即指派到 `Purchasing` 結構描述。</span><span class="sxs-lookup"><span data-stu-id="486ce-138">The stored procedure is part of the `Purchasing` schema, even though no schema was explicitly specified, because `TestManagerUser` is assigned by default to the `Purchasing` schema.</span></span> <span data-ttu-id="486ce-139">您可以利用系統目錄資訊找出物件，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="486ce-139">You can use system catalog information to locate objects, as shown in the following code.</span></span>  
  
```  
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas a  
   INNER JOIN sys.objects b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
```  
  
 <span data-ttu-id="486ce-140">範例的這個部分既已完成，程式碼隨即使用 `REVERT` 陳述式將內容切換回 dbo。</span><span class="sxs-lookup"><span data-stu-id="486ce-140">With this section of the example completed, the code switches context back to dbo using the `REVERT` statement.</span></span>  
  
```  
REVERT;  
GO  
```  
  
 <span data-ttu-id="486ce-141">如需 REVERT 陳述式的詳細資訊，請參閱 [REVERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/revert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="486ce-141">For more information about the REVERT statement, see [REVERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/revert-transact-sql).</span></span>  
  
## <a name="3-access-data-through-the-stored-procedure"></a><span data-ttu-id="486ce-142">3.透過預存程序存取資料</span><span class="sxs-lookup"><span data-stu-id="486ce-142">3. Access Data Through the Stored Procedure</span></span>  
 <span data-ttu-id="486ce-143">`TestEmployeeUser` 除了在 public 資料庫角色中具備登入身分及受指派的權限外，對 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫物件毫無任何權限。</span><span class="sxs-lookup"><span data-stu-id="486ce-143">`TestEmployeeUser` has no permissions on the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database objects other than a login and the rights assigned to the public database role.</span></span> <span data-ttu-id="486ce-144">下列程式碼將因 `TestEmployeeUser` 試圖存取基底資料表而傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="486ce-144">The following code returns an error when `TestEmployeeUser` attempts to access base tables.</span></span>  
  
```  
EXECUTE AS LOGIN = 'TestEmployeeUser'  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* This won't work */  
SELECT *  
FROM Purchasing.PurchaseOrderHeader;  
GO  
SELECT *  
FROM Purchasing.PurchaseOrderDetail;  
GO  
```  
  
 <span data-ttu-id="486ce-145">由於 `TestManagerUser` 憑藉其 `Purchasing` 結構描述擁有權而成為上一節所建立預存程序中參考之物件的擁有者， `TestEmployeeUser` 可透過預存程序存取基底資料表。</span><span class="sxs-lookup"><span data-stu-id="486ce-145">Because the objects referenced by the stored procedure created in the last section are owned by `TestManagerUser` by virtue of the `Purchasing` schema ownership, `TestEmployeeUser` can access the base tables through the stored procedure.</span></span> <span data-ttu-id="486ce-146">下列程式碼仍舊使用 `TestEmployeeUser` 內容，傳遞訂單號碼 952 做為參數。</span><span class="sxs-lookup"><span data-stu-id="486ce-146">The following code, still using the `TestEmployeeUser` context, passes purchase order 952 as a parameter.</span></span>  
  
```  
EXEC Purchasing.usp_ShowWaitingItems 952  
GO  
```  
  
## <a name="4-reset-the-environment"></a><span data-ttu-id="486ce-147">4.重設環境</span><span class="sxs-lookup"><span data-stu-id="486ce-147">4. Reset the Environment</span></span>  
 <span data-ttu-id="486ce-148">下列程式碼使用 `REVERT` 命令，將目前帳戶的內容切換回 `dbo`然後重設環境。</span><span class="sxs-lookup"><span data-stu-id="486ce-148">The following code uses the `REVERT` command to return the context of the current account to `dbo`, and then resets the environment.</span></span>  
  
```  
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
##  <a name="complete-example"></a><a name="CompleteExample"></a><span data-ttu-id="486ce-149">完整範例</span><span class="sxs-lookup"><span data-stu-id="486ce-149">Complete Example</span></span>  
 <span data-ttu-id="486ce-150">本節顯示完整的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="486ce-150">This section displays the complete example code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="486ce-151">下列程式碼剔除了用以示範 `TestEmployeeUser` 無法從基底資料表選取以致發生兩項預期錯誤的部分。</span><span class="sxs-lookup"><span data-stu-id="486ce-151">This code does not include the two expected errors that demonstrate the inability of `TestEmployeeUser` to select from base tables.</span></span>  
  
```  
/*   
Script:       UserContextTutorial.sql  
Author:       Microsoft  
Last Updated: Books Online  
Conditions:   Execute as DBO or sysadmin in the AdventureWorks database  
Section 1:    Configure the Environment   
*/  
USE AdventureWorks2012;  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
/* Create server and database users */  
CREATE LOGIN TestManagerUser   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khx';  
  
GO  
  
CREATE USER TestManagerUser   
   FOR LOGIN TestManagerUser  
   WITH DEFAULT_SCHEMA = Purchasing;  
GO   
  
CREATE LOGIN TestEmployeeUser  
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
GO  
CREATE USER TestEmployeeUser   
   FOR LOGIN TestEmployeeUser;  
GO   
  
/* Change owner of the Purchasing Schema to TestManagerUser */  
ALTER AUTHORIZATION   
   ON SCHEMA::Purchasing   
   TO TestManagerUser;  
GO  
  
GRANT CREATE PROCEDURE   
   TO TestManagerUser   
   WITH GRANT OPTION;  
GO  
  
/*   
Section 2: Switch Context and Create Objects  
*/  
EXECUTE AS LOGIN = 'TestManagerUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
  
/* Note: The user that calls the EXECUTE AS statement must have IMPERSONATE permissions on the target principal */  
CREATE PROCEDURE usp_ShowWaitingItems @ProductID int  
AS  
BEGIN   
   SELECT a.PurchaseOrderID, a.OrderDate, a.ShipDate  
      , b.ProductID, b.OrderQty, b.ReceivedQty  
   FROM Purchasing.PurchaseOrderHeader AS a  
      INNER JOIN Purchasing.PurchaseOrderDetail AS b  
         ON a.PurchaseOrderID = b.PurchaseOrderID  
   WHERE b.OrderQty > b.ReceivedQty  
      AND @ProductID = b.ProductID  
   ORDER BY b.ProductID ASC  
END;  
GO  
  
/* Give the employee the ability to run the procedure */  
GRANT EXECUTE   
   ON OBJECT::Purchasing.usp_ShowWaitingItems  
   TO TestEmployeeUser;  
GO   
  
/* Notice that the stored procedure is located in the Purchasing   
schema. This also demonstrates system catalogs */  
SELECT a.name AS 'Schema'  
   , b.name AS 'Object Name'  
   , b.type AS 'Object Type'  
FROM sys.schemas AS a  
   INNER JOIN sys.objects AS b  
      ON a.schema_id = b.schema_id   
WHERE b.name = 'usp_ShowWaitingItems';  
GO  
  
/* Go back to being the dbo user */  
REVERT;  
GO  
  
/*  
Section 3: Switch Context and Observe Security   
*/  
EXECUTE AS LOGIN = 'TestEmployeeUser';  
GO  
SELECT CURRENT_USER AS 'Current User Name';  
GO  
EXEC Purchasing.usp_ShowWaitingItems 952;  
GO  
  
/*   
Section 4: Clean Up Example  
*/  
REVERT;  
GO  
ALTER AUTHORIZATION   
ON SCHEMA::Purchasing TO dbo;  
GO  
DROP PROCEDURE Purchasing.usp_ShowWaitingItems;  
GO  
DROP USER TestEmployeeUser;  
GO  
DROP USER TestManagerUser;  
GO  
DROP LOGIN TestEmployeeUser;  
GO  
DROP LOGIN TestManagerUser;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="486ce-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="486ce-152">See Also</span></span>  
 [<span data-ttu-id="486ce-153">SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心</span><span class="sxs-lookup"><span data-stu-id="486ce-153">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
