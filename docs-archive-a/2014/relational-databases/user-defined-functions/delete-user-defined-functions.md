---
title: 刪除使用者定義函數 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: db1d668a-23b7-4757-a9c5-1bd848ba7f6d
author: rothja
ms.author: jroth
ms.openlocfilehash: e5f6b2b306c4fe8db08b088d9607cfb19ab0f25e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606104"
---
# <a name="delete-user-defined-functions"></a><span data-ttu-id="22b99-102">刪除使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="22b99-102">Delete User-defined Functions</span></span>
  <span data-ttu-id="22b99-103">您可以透過使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或下列項目，刪除 (卸除) [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的使用者定義函數： [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22b99-103">You can delete (drop) user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="22b99-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="22b99-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="22b99-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="22b99-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="22b99-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="22b99-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="22b99-107">安全性</span><span class="sxs-lookup"><span data-stu-id="22b99-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="22b99-108">**若要使用下列項目刪除使用者定義函數：**</span><span class="sxs-lookup"><span data-stu-id="22b99-108">**To delete a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="22b99-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22b99-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="22b99-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22b99-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="22b99-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="22b99-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="22b99-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="22b99-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="22b99-113">如果資料庫中有 Transact-SQL 函數或檢視參考這個函數，並且是利用 SCHEMABINDING 加以建立；或者如果有計算資料行、CHECK 條件約束或 DEFAULT 條件約束參考這個函數，就無法刪除函數。</span><span class="sxs-lookup"><span data-stu-id="22b99-113">You will not be able to delete the function if there are Transact-SQL functions or views in the database that reference this function and were created by using SCHEMABINDING, or if there are computed columns, CHECK constraints, or DEFAULT constraints that reference the function.</span></span>  
  
-   <span data-ttu-id="22b99-114">如果有計算資料行參考這個函數，而且已經產生索引，就無法刪除函數。</span><span class="sxs-lookup"><span data-stu-id="22b99-114">You will not be able to delete the function if there are computed columns that reference this function and have been indexed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="22b99-115">Security</span><span class="sxs-lookup"><span data-stu-id="22b99-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="22b99-116">權限</span><span class="sxs-lookup"><span data-stu-id="22b99-116">Permissions</span></span>  
 <span data-ttu-id="22b99-117">需要函數所屬結構描述的 ALTER 權限，或函數的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="22b99-117">Requires ALTER permission on the schema to which the function belongs, or CONTROL permission on the function.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="22b99-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="22b99-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="22b99-119">若要刪除使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="22b99-119">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="22b99-120">按一下包含要修改之函數的資料庫旁邊的加號。</span><span class="sxs-lookup"><span data-stu-id="22b99-120">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="22b99-121">按一下 **[可程式性]** 資料夾旁的加號。</span><span class="sxs-lookup"><span data-stu-id="22b99-121">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="22b99-122">按一下包含要修改之函數的資料夾旁邊的加號：</span><span class="sxs-lookup"><span data-stu-id="22b99-122">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="22b99-123">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="22b99-123">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="22b99-124">純量值函式</span><span class="sxs-lookup"><span data-stu-id="22b99-124">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="22b99-125">彙總函式</span><span class="sxs-lookup"><span data-stu-id="22b99-125">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="22b99-126">以滑鼠右鍵按一下您想刪除的函數，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="22b99-126">Right-click the function you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="22b99-127">在 **[刪除物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="22b99-127">In the **Delete Object** dialog box, click **OK**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="22b99-128">按一下 [**刪除物件**] 對話方塊中的 [**顯示**相依性]，開啟 [ _function_name_相依**性] 對話方塊**。</span><span class="sxs-lookup"><span data-stu-id="22b99-128">Click **Show Dependencies** in the **Delete Object** dialog box to open the _function_name_**Dependencies** dialog box.</span></span> <span data-ttu-id="22b99-129">這就會顯示相依於函數的所有物件以及函數所相依的所有物件。</span><span class="sxs-lookup"><span data-stu-id="22b99-129">This will show all of the objects that depend on the function and all of the objects on which the function depends.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="22b99-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="22b99-130">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-user-defined-function"></a><span data-ttu-id="22b99-131">若要刪除使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="22b99-131">To delete a user-defined function</span></span>  
  
1.  <span data-ttu-id="22b99-132">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="22b99-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="22b99-133">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="22b99-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="22b99-134">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="22b99-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- creates function called "Sales.ufn_SalesByStore"  
    USE AdventureWorks2012;  
    GO  
    CREATE FUNCTION Sales.ufn_SalesByStore (@storeid int)  
    RETURNS TABLE  
    AS  
    RETURN   
    (  
        SELECT P.ProductID, P.Name, SUM(SD.LineTotal) AS 'Total'  
        FROM Production.Product AS P   
        JOIN Sales.SalesOrderDetail AS SD ON SD.ProductID = P.ProductID  
        JOIN Sales.SalesOrderHeader AS SH ON SH.SalesOrderID = SD.SalesOrderID  
        JOIN Sales.Customer AS C ON SH.CustomerID = C.CustomerID  
        WHERE C.StoreID = @storeid  
        GROUP BY P.ProductID, P.Name  
    );  
    GO  
    ```  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- determines if function exists in database  
    IF OBJECT_ID (N'Sales.fn_SalesByStore', N'IF') IS NOT NULL  
    -- deletes function  
        DROP FUNCTION Sales.fn_SalesByStore;  
    GO  
    ```  
  
 <span data-ttu-id="22b99-135">如需詳細資訊，請參閱 [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="22b99-135">For more information, see [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql).</span></span>  
  
  
