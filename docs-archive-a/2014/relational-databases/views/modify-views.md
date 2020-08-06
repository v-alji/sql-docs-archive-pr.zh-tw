---
title: 修改檢視 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- views [SQL Server], modifying
- modifying views
- renaming views
ms.assetid: 2d3c14dc-43e5-4324-b8fb-f2692d330b16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 10cf9ecc860d8f9b46a06ac679b0f1a8241000bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595860"
---
# <a name="modify-views"></a><span data-ttu-id="42dea-102">修改檢視</span><span class="sxs-lookup"><span data-stu-id="42dea-102">Modify Views</span></span>
  <span data-ttu-id="42dea-103">定義檢視之後，可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改其定義，不需要卸除和重新建立檢視。</span><span class="sxs-lookup"><span data-stu-id="42dea-103">After you define a view, you can modify its definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] without dropping and re-creating the view by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="42dea-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="42dea-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="42dea-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="42dea-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="42dea-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="42dea-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="42dea-107">安全性</span><span class="sxs-lookup"><span data-stu-id="42dea-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="42dea-108">**使用下列方法修改檢視：**</span><span class="sxs-lookup"><span data-stu-id="42dea-108">**To modify a view, using:**</span></span>  
  
     [<span data-ttu-id="42dea-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42dea-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="42dea-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42dea-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="42dea-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="42dea-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="42dea-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="42dea-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="42dea-113">修改檢視不會影響任何相依物件，像是預存程序或觸發程序，除非檢視的定義變更導致相依物件不再有效。</span><span class="sxs-lookup"><span data-stu-id="42dea-113">Modifying a view does not affect any dependent objects, such as stored procedures or triggers, unless the definition of the view changes in such a way that the dependent object is no longer valid.</span></span>  
  
-   <span data-ttu-id="42dea-114">如果目前所用的檢視是利用 ALTER VIEW 來修改的， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會取得檢視的獨佔結構描述鎖定。</span><span class="sxs-lookup"><span data-stu-id="42dea-114">If a view currently used is modified by using ALTER VIEW, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] takes an exclusive schema lock on the view.</span></span> <span data-ttu-id="42dea-115">當授與鎖定時，檢視並沒有使用中的使用者， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會從程序快取中刪除檢視的所有副本。</span><span class="sxs-lookup"><span data-stu-id="42dea-115">When the lock is granted, and there are no active users of the view, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] deletes all copies of the view from the procedure cache.</span></span> <span data-ttu-id="42dea-116">現有參考這份檢視的計畫會保留在快取中，但在叫用它時，會重新編譯。</span><span class="sxs-lookup"><span data-stu-id="42dea-116">Existing plans referencing the view remain in the cache but are recompiled when invoked.</span></span>  
  
-   <span data-ttu-id="42dea-117">您可以將 ALTER VIEW 套用在索引檢視上；不過，ALTER VIEW 會無條件地卸除檢視的所有索引。</span><span class="sxs-lookup"><span data-stu-id="42dea-117">ALTER VIEW can be applied to indexed views; however, ALTER VIEW unconditionally drops all indexes on the view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="42dea-118">Security</span><span class="sxs-lookup"><span data-stu-id="42dea-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="42dea-119">權限</span><span class="sxs-lookup"><span data-stu-id="42dea-119">Permissions</span></span>  
 <span data-ttu-id="42dea-120">若要執行 ALTER VIEW，至少需要 OBJECT 的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="42dea-120">To execute ALTER VIEW, at a minimum, ALTER permission on OBJECT is required.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="42dea-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="42dea-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="42dea-122">若要修改檢視</span><span class="sxs-lookup"><span data-stu-id="42dea-122">To modify a view</span></span>  
  
1.  <span data-ttu-id="42dea-123">在 **[物件總管]** 中，按一下檢視表所在之資料庫旁邊的加號，然後按一下 **[檢視表]** 資料夾旁邊的加號。</span><span class="sxs-lookup"><span data-stu-id="42dea-123">In **Object Explorer**, click the plus sign next to the database where your view is located and then click the plus sign next to the **Views** folder.</span></span>  
  
2.  <span data-ttu-id="42dea-124">以滑鼠右鍵按一下您要修改的檢視，然後選取 [設計]  。</span><span class="sxs-lookup"><span data-stu-id="42dea-124">Right-click on the view you wish to modify and select **Design**.</span></span>  
  
3.  <span data-ttu-id="42dea-125">在查詢設計工具的圖表窗格中，以下列一個或多個方式變更檢視：</span><span class="sxs-lookup"><span data-stu-id="42dea-125">In the diagram pane of the query designer, make changes to the view in one or more of the following ways:</span></span>  
  
    1.  <span data-ttu-id="42dea-126">對於您要加入或移除的任何元素，選取或清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="42dea-126">Select or clear the check boxes of any elements you wish to add or remove.</span></span>  
  
    2.  <span data-ttu-id="42dea-127">以滑鼠右鍵按一下圖表窗格，並選取 [新增資料表...]  ，然後從 [新增資料表]  對話方塊選取要新增檢視中的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="42dea-127">Right-click within the diagram pane, select **Add Table...**, and then select the additional columns you want to add to the view from the **Add Table** dialog box.</span></span>  
  
    3.  <span data-ttu-id="42dea-128">以滑鼠右鍵按一下您要移除之資料表的標題列，然後選取 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="42dea-128">Right-click the title bar of the table you wish to remove and select **Remove**.</span></span>  
  
4.  <span data-ttu-id="42dea-129">在 [檔案]  功能表上，按一下 [儲存]  _view name_。</span><span class="sxs-lookup"><span data-stu-id="42dea-129">On the **File** menu, click **Save**_view name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="42dea-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="42dea-130">Using Transact-SQL</span></span>  
  
#### <a name="to-modify-a-view"></a><span data-ttu-id="42dea-131">若要修改檢視</span><span class="sxs-lookup"><span data-stu-id="42dea-131">To modify a view</span></span>  
  
1.  <span data-ttu-id="42dea-132">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42dea-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="42dea-133">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="42dea-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="42dea-134">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="42dea-134">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="42dea-135">此範例先建立檢視，然後透過使用 ALTER VIEW 修改此檢視。</span><span class="sxs-lookup"><span data-stu-id="42dea-135">The example first creates a view and then modifies the view by using ALTER VIEW.</span></span> <span data-ttu-id="42dea-136">檢視定義中會加入 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="42dea-136">A WHERE clause is added to the view definition.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    -- Create a view.  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
  
    -- Modify the view by adding a WHERE clause to limit the rows returned.  
    ALTER VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID  
    WHERE HireDate < CONVERT(DATETIME,'20020101',101) ;   
    GO  
    ```  
  
 <span data-ttu-id="42dea-137">如需詳細資訊，請參閱 [ALTER VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="42dea-137">For more information, see [ALTER VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-view-transact-sql).</span></span>  
  
  
