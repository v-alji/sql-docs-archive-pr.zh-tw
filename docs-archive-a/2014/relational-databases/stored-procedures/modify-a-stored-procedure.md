---
title: 修改預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying stored procedures
- editing stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: 13396239-6100-48ce-aa34-461358d99c92
author: stevestein
ms.author: sstein
ms.openlocfilehash: 906f0e06650da505094d18774ce86dab53d53f38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686869"
---
# <a name="modify-a-stored-procedure"></a><span data-ttu-id="42f67-102">修改預存程序</span><span class="sxs-lookup"><span data-stu-id="42f67-102">Modify a Stored Procedure</span></span>
    
##  <a name="this-topic-describes-how-to-modify-a-stored-procedure-in-sscurrent-by-using-ssmanstudiofull-or-tsql"></a><a name="Top"></a> <span data-ttu-id="42f67-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="42f67-103">This topic describes how to modify a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="42f67-104">**開始之前：** [限制事項](#Restrictions)、[安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="42f67-104">**Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="42f67-105">**若要更改程序，請使用：** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="42f67-105">**To alter a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="42f67-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="42f67-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="42f67-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="42f67-107">Limitations and Restrictions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="42f67-108">預存程序無法修改成 CLR 預存程序，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="42f67-108">stored procedures cannot be modified to be CLR stored procedures and vice versa.</span></span>  
  
 <span data-ttu-id="42f67-109">如果先前的程序定義是利用 WITH ENCRYPTION 或 WITH RECOMPILE 來建立的，只有在 ALTER PROCEDURE 陳述式包括這些選項時，才會啟用這些選項。</span><span class="sxs-lookup"><span data-stu-id="42f67-109">If the previous procedure definition was created using WITH ENCRYPTION or WITH RECOMPILE, these options are enabled only if they are included in the ALTER PROCEDURE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="42f67-110">Security</span><span class="sxs-lookup"><span data-stu-id="42f67-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="42f67-111">權限</span><span class="sxs-lookup"><span data-stu-id="42f67-111">Permissions</span></span>  
 <span data-ttu-id="42f67-112">需要程序的 ALTER PROCEDURE 權限。</span><span class="sxs-lookup"><span data-stu-id="42f67-112">Requires ALTER PROCEDURE permission on the procedure.</span></span>  
  
##  <a name="how-to-modify-a-stored-procedure"></a><a name="Procedures"></a> <span data-ttu-id="42f67-113">如何修改預存程序</span><span class="sxs-lookup"><span data-stu-id="42f67-113">How to Modify a Stored Procedure</span></span>  
 <span data-ttu-id="42f67-114">您可以使用下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="42f67-114">You can use one of the following:</span></span>  
  
-   [<span data-ttu-id="42f67-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42f67-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="42f67-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42f67-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="42f67-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42f67-117">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="42f67-118">**若要在 Management Studio 中修改程序**</span><span class="sxs-lookup"><span data-stu-id="42f67-118">**To modify a procedure in Management Studio**</span></span>  
  
1.  <span data-ttu-id="42f67-119">在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="42f67-119">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="42f67-120">依序展開 **[資料庫]** 、程序所屬的資料庫，以及 **[可程式性]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-120">Expand **Databases**, expand the database in which the procedure belongs, and then expand **Programmability**.</span></span>  
  
3.  <span data-ttu-id="42f67-121">展開 [預存程序]，以滑鼠右鍵按一下要修改的程序，然後按一下 [修改]。</span><span class="sxs-lookup"><span data-stu-id="42f67-121">Expand **Stored Procedures**, right-click the procedure to modify, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="42f67-122">修改預存程序的文字。</span><span class="sxs-lookup"><span data-stu-id="42f67-122">Modify the text of the stored procedure.</span></span>  
  
5.  <span data-ttu-id="42f67-123">若要測試語法，請在 **[查詢]** 功能表上按一下 **[剖析]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-123">To test the syntax, on the **Query** menu, click **Parse**.</span></span>  
  
6.  <span data-ttu-id="42f67-124">若要將所做的修改儲存至程序定義，請在 **[查詢]** 功能表上按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-124">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
7.  <span data-ttu-id="42f67-125">若要將更新的程序定義儲存為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼，請在 **[檔案]** 功能表上按一下 **[另存新檔]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-125">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="42f67-126">接受檔案名稱，或將它取代成新名稱，然後按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-126">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="42f67-127">驗證所有使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="42f67-127">Validate all user input.</span></span> <span data-ttu-id="42f67-128">在使用者輸入完成驗證前，請勿加以串連。</span><span class="sxs-lookup"><span data-stu-id="42f67-128">Do not concatenate user input before you validate it.</span></span> <span data-ttu-id="42f67-129">請勿執行由未經驗證之使用者輸入所建構的命令。</span><span class="sxs-lookup"><span data-stu-id="42f67-129">Never execute a command constructed from unvalidated user input.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="42f67-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42f67-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="42f67-131">**若要在查詢編輯器中修改程序**</span><span class="sxs-lookup"><span data-stu-id="42f67-131">**To modify a procedure in Query Editor**</span></span>  
  
1.  <span data-ttu-id="42f67-132">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="42f67-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="42f67-133">展開 **[資料庫]** ，展開程序所屬的資料庫。</span><span class="sxs-lookup"><span data-stu-id="42f67-133">Expand **Databases**, expand the database in which the procedure belongs.</span></span> <span data-ttu-id="42f67-134">或者，從工具列的可用資料庫清單中選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="42f67-134">Or, from the tool bar, select the database from the list of available databases.</span></span> <span data-ttu-id="42f67-135">針對此範例，請選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="42f67-135">For this example, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
3.  <span data-ttu-id="42f67-136">按一下 **[檔案]** 功能表上的 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-136">On the **File** menu, click **New Query**.</span></span>  
  
4.  <span data-ttu-id="42f67-137">將下列範例複製並貼入查詢編輯器中。</span><span class="sxs-lookup"><span data-stu-id="42f67-137">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="42f67-138">範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。</span><span class="sxs-lookup"><span data-stu-id="42f67-138">The example creates the `uspVendorAllInfo` procedure, which returns the names of all the vendors in the [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] database, the products they supply, their credit ratings, and their availability.</span></span>  
  
    ```  
  
    IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
        DROP PROCEDURE Purchasing.uspVendorAllInfo;  
    GO  
    CREATE PROCEDURE Purchasing.uspVendorAllInfo  
    WITH EXECUTE AS CALLER  
    AS  
        SET NOCOUNT ON;  
        SELECT v.Name AS Vendor, p.Name AS 'Product name',   
          v.CreditRating AS 'Rating',   
          v.ActiveFlag AS Availability  
        FROM Purchasing.Vendor v   
        INNER JOIN Purchasing.ProductVendor pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product p  
          ON pv.ProductID = p.ProductID   
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
5.  <span data-ttu-id="42f67-139">按一下 **[檔案]** 功能表上的 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-139">On the **File** menu, click **New Query**.</span></span>  
  
6.  <span data-ttu-id="42f67-140">將下列範例複製並貼入查詢編輯器中。</span><span class="sxs-lookup"><span data-stu-id="42f67-140">Copy and paste the following example into the query editor.</span></span> <span data-ttu-id="42f67-141">下列範例會修改 `uspVendorAllInfo` 程序。</span><span class="sxs-lookup"><span data-stu-id="42f67-141">The example modifies the `uspVendorAllInfo` procedure.</span></span> <span data-ttu-id="42f67-142">它會移除 EXECUTE AS CALLER 子句，並修改程序主體，使其只傳回提供指定之產品的供應商。</span><span class="sxs-lookup"><span data-stu-id="42f67-142">The EXECUTE AS CALLER clause is removed and the body of the procedure is modified to return only those vendors that supply the specified product.</span></span> <span data-ttu-id="42f67-143">`LEFT` 和 `CASE` 函數可自訂結果集的外觀。</span><span class="sxs-lookup"><span data-stu-id="42f67-143">The `LEFT` and `CASE` functions customize the appearance of the result set.</span></span>  
  
    ```  
    ALTER PROCEDURE Purchasing.uspVendorAllInfo  
        @Product varchar(25)   
    AS  
        SET NOCOUNT ON;  
        SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
        'Rating' = CASE v.CreditRating   
            WHEN 1 THEN 'Superior'  
            WHEN 2 THEN 'Excellent'  
            WHEN 3 THEN 'Above average'  
            WHEN 4 THEN 'Average'  
            WHEN 5 THEN 'Below average'  
            ELSE 'No rating'  
            END  
        , Availability = CASE v.ActiveFlag  
            WHEN 1 THEN 'Yes'  
            ELSE 'No'  
            END  
        FROM Purchasing.Vendor AS v   
        INNER JOIN Purchasing.ProductVendor AS pv  
          ON v.BusinessEntityID = pv.BusinessEntityID   
        INNER JOIN Production.Product AS p   
          ON pv.ProductID = p.ProductID   
        WHERE p.Name LIKE @Product  
        ORDER BY v.Name ASC;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="42f67-144">若要將所做的修改儲存至程序定義，請在 **[查詢]** 功能表上按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-144">To save the modifications to the procedure definition, on the **Query** menu, click **Execute**.</span></span>  
  
8.  <span data-ttu-id="42f67-145">若要將更新的程序定義儲存為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼，請在 **[檔案]** 功能表上按一下 **[另存新檔]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-145">To save the updated procedure definition as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, on the **File** menu, click **Save As**.</span></span> <span data-ttu-id="42f67-146">接受檔案名稱，或將它取代成新名稱，然後按一下 **[儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="42f67-146">Accept the file name or replace it with a new name, and then click **Save**.</span></span>  
  
9. <span data-ttu-id="42f67-147">若要執行修改過的預存程序，請執行下列範例。</span><span class="sxs-lookup"><span data-stu-id="42f67-147">To run the modified stored procedure, execute the following example.</span></span>  
  
    ```  
    EXEC Purchasing.uspVendorAllInfo N'LL Crankarm';  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="42f67-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42f67-148">See Also</span></span>  
 [<span data-ttu-id="42f67-149">ALTER PROCEDURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="42f67-149">ALTER PROCEDURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-procedure-transact-sql)  
  
  
