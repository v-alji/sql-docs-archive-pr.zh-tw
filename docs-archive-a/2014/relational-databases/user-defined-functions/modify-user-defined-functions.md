---
title: 修改使用者定義函式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 891c37b3-cb72-411f-9937-ee87e6d95f34
author: rothja
ms.author: jroth
ms.openlocfilehash: 1cf25fef91834e237f5cbaac26350220840830bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606101"
---
# <a name="modify-user-defined-functions"></a><span data-ttu-id="7a8dd-102">修改使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="7a8dd-102">Modify User-defined Functions</span></span>
  <span data-ttu-id="7a8dd-103">您可以透過使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，修改 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-103">You can modify user-defined functions in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7a8dd-104">如下述修改使用者定義函數不會變更函數的權限，也不會影響任何相依函數、預存程序或觸發程序。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-104">Modifying user-defined functions as described below will not change the functions' permissions, nor will it affect any dependent functions, stored procedures, or triggers.</span></span>  
  
 <span data-ttu-id="7a8dd-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7a8dd-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7a8dd-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="7a8dd-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7a8dd-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="7a8dd-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="7a8dd-108">安全性</span><span class="sxs-lookup"><span data-stu-id="7a8dd-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7a8dd-109">**使用下列方式修改使用者定義函數：**</span><span class="sxs-lookup"><span data-stu-id="7a8dd-109">**To modify a user-defined function, using:**</span></span>  
  
     [<span data-ttu-id="7a8dd-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7a8dd-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="7a8dd-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7a8dd-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7a8dd-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="7a8dd-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="7a8dd-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="7a8dd-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7a8dd-114">ALTER FUNCTION 不能用於執行以下任何動作：</span><span class="sxs-lookup"><span data-stu-id="7a8dd-114">ALTER FUNCTION cannot be used to perform any of the following actions:</span></span>  
  
-   <span data-ttu-id="7a8dd-115">將純量值函式變更為資料表值函式，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-115">Change a scalar-valued function to a table-valued function, or vice versa.</span></span>  
  
-   <span data-ttu-id="7a8dd-116">將內嵌函數變更為多重陳述式函數，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-116">Change an inline function to a multistatement function, or vice versa.</span></span>  
  
-   <span data-ttu-id="7a8dd-117">將 Transact-SQL 函數變更為 CLR 函數，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-117">Change a Transact-SQL function to a CLR function, or vice-versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7a8dd-118">Security</span><span class="sxs-lookup"><span data-stu-id="7a8dd-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7a8dd-119">權限</span><span class="sxs-lookup"><span data-stu-id="7a8dd-119">Permissions</span></span>  
 <span data-ttu-id="7a8dd-120">需要函數或結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-120">Requires ALTER permission on the function or on the schema.</span></span> <span data-ttu-id="7a8dd-121">如果此函數指定使用者定義型別，則需要該型別的 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-121">If the function specifies a user-defined type, requires EXECUTE permission on the type.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="7a8dd-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7a8dd-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="7a8dd-123">若要修改使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="7a8dd-123">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="7a8dd-124">按一下包含要修改之函數的資料庫旁邊的加號。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-124">Click on the plus sign next to the database that contains the function you wish to modify.</span></span>  
  
2.  <span data-ttu-id="7a8dd-125">按一下 **[可程式性]** 資料夾旁的加號。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-125">Click on the plus sign next to the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="7a8dd-126">按一下包含要修改之函數的資料夾旁邊的加號：</span><span class="sxs-lookup"><span data-stu-id="7a8dd-126">Click the plus sign next to the folder that contains the function you wish to modify:</span></span>  
  
    -   <span data-ttu-id="7a8dd-127">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="7a8dd-127">Table-valued Function</span></span>  
  
    -   <span data-ttu-id="7a8dd-128">純量值函式</span><span class="sxs-lookup"><span data-stu-id="7a8dd-128">Scalar-valued Function</span></span>  
  
    -   <span data-ttu-id="7a8dd-129">彙總函式</span><span class="sxs-lookup"><span data-stu-id="7a8dd-129">Aggregate Function</span></span>  
  
4.  <span data-ttu-id="7a8dd-130">以滑鼠右鍵按一下您要修改的函數，然後選取 [修改]  。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-130">Right-click the function you want to modify and select **Modify**.</span></span>  
  
5.  <span data-ttu-id="7a8dd-131">在查詢視窗中，對 ALTER FUNCTION 陳述式進行必要的變更。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-131">In the Query Window, make the necessary changes to the ALTER FUNCTION statement.</span></span>  
  
6.  <span data-ttu-id="7a8dd-132">在 [檔案] 功能表上，按一下 [儲存 _function_name_]。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-132">On the **File** menu, click **Save**_function_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="7a8dd-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7a8dd-133">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-user-defined-function"></a><span data-ttu-id="7a8dd-134">若要修改使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="7a8dd-134">To modify a user-defined function</span></span>  
  
1.  <span data-ttu-id="7a8dd-135">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7a8dd-136">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7a8dd-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Scalar-Valued Function  
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetAccountingEndDate]()  
    RETURNS [datetime]   
    AS   
    BEGIN  
        RETURN DATEADD(millisecond, -2, CONVERT(datetime, '20040701', 112));  
    END;  
    ```  
  
    ```  
    -- Table-Valued Function   
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetContactInformation](@PersonID int)  
    RETURNS @retContactInformation TABLE   
    (  
        -- Columns returned by the function  
        [PersonID] int NOT NULL,   
        [FirstName] [nvarchar](50) NULL,   
        [LastName] [nvarchar](50) NULL,   
        [JobTitle] [nvarchar](50) NULL,  
        [BusinessEntityType] [nvarchar](50) NULL  
    )  
    AS   
    -- Returns the first name, last name, job title and business entity type for the specified contact.  
    -- Since a contact can serve multiple roles, more than one row may be returned.  
    BEGIN  
    IF @PersonID IS NOT NULL   
    BEGIN  
         IF EXISTS(SELECT * FROM [HumanResources].[Employee] e   
         WHERE e.[BusinessEntityID] = @PersonID)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, e.[JobTitle], 'Employee'  
              FROM [HumanResources].[Employee] AS e  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = e.[BusinessEntityID]  
              WHERE e.[BusinessEntityID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Purchasing].[Vendor] AS v  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Vendor Contact'   
              FROM [Purchasing].[Vendor] AS v  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Sales].[Store] AS s  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Store Contact'   
              FROM [Sales].[Store] AS s  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Person].[Person] AS p  
         INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
         WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, NULL, 'Consumer'   
              FROM [Person].[Person] AS p  
              INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
              WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL;   
         END  
    RETURN;  
    END;  
    ```  
  
 <span data-ttu-id="7a8dd-138">如需詳細資訊，請參閱 [ALTER FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7a8dd-138">For more information, see [ALTER FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-function-transact-sql).</span></span>  
  
  
