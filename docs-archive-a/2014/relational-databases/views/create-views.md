---
title: 建立檢視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], creating
ms.assetid: 0b7bd2a1-544c-42ba-8e7b-4822f34d7b64
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8280f6d65d7252cad423abef849207111492c044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585212"
---
# <a name="create-views"></a><span data-ttu-id="86721-102">建立檢視表</span><span class="sxs-lookup"><span data-stu-id="86721-102">Create Views</span></span>
  <span data-ttu-id="86721-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立檢視。</span><span class="sxs-lookup"><span data-stu-id="86721-103">You can create views in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="86721-104">檢視可用於下列目的：</span><span class="sxs-lookup"><span data-stu-id="86721-104">A view can be used for the following purposes:</span></span>  
  
-   <span data-ttu-id="86721-105">對焦 (Focus)、簡化和自訂每位使用者查看資料庫的角度。</span><span class="sxs-lookup"><span data-stu-id="86721-105">To focus, simplify, and customize the perception each user has of the database.</span></span>  
  
-   <span data-ttu-id="86721-106">做為安全機制，讓使用者能夠透過檢視存取資料，但不將直接存取基底資料表的權限授與使用者。</span><span class="sxs-lookup"><span data-stu-id="86721-106">As a security mechanism by allowing users to access data through the view, without granting the users permissions to directly access the underlying base tables.</span></span>  
  
-   <span data-ttu-id="86721-107">提供回溯相容介面以模擬其結構描述已變更的資料表。</span><span class="sxs-lookup"><span data-stu-id="86721-107">To provide a backward compatible interface to emulate a table whose schema has changed.</span></span>  
  
 <span data-ttu-id="86721-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="86721-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="86721-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="86721-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="86721-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="86721-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="86721-111">安全性</span><span class="sxs-lookup"><span data-stu-id="86721-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="86721-112">**使用下列方法建立檢視：**</span><span class="sxs-lookup"><span data-stu-id="86721-112">**To create a view, using:**</span></span>  
  
     [<span data-ttu-id="86721-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86721-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="86721-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86721-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="86721-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="86721-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="86721-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="86721-116">Limitations and Restrictions</span></span>  
 <span data-ttu-id="86721-117">檢視只能建立在目前資料庫中。</span><span class="sxs-lookup"><span data-stu-id="86721-117">A view can be created only in the current database.</span></span>  
  
 <span data-ttu-id="86721-118">檢視最多可有 1,024 個資料行。</span><span class="sxs-lookup"><span data-stu-id="86721-118">A view can have a maximum of 1,024 columns.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="86721-119">Security</span><span class="sxs-lookup"><span data-stu-id="86721-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="86721-120">權限</span><span class="sxs-lookup"><span data-stu-id="86721-120">Permissions</span></span>  
 <span data-ttu-id="86721-121">至少必須有資料庫中的 CREATE VIEW 權限，以及正在建立之檢視表所在之結構描述的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="86721-121">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="86721-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="86721-122">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-view-by-using-the-query-and-view-designer"></a><span data-ttu-id="86721-123">透過使用查詢和檢視表設計工具建立檢視</span><span class="sxs-lookup"><span data-stu-id="86721-123">To create a view by using the Query and View Designer</span></span>  
  
1.  <span data-ttu-id="86721-124">在 **[物件總管]** 中，展開您要建立新檢視表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="86721-124">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="86721-125">以滑鼠右鍵按一下 [檢視]  資料夾，然後按一下 [新增檢視…]  。</span><span class="sxs-lookup"><span data-stu-id="86721-125">Right-click the **Views** folder, then click **New View...**.</span></span>  
  
3.  <span data-ttu-id="86721-126">在 **[加入資料表]** 對話方塊中，從下列索引標籤選取您要包含在新檢視中的元素：[資料表]、[檢視]、[函數] 和 [同義字]。</span><span class="sxs-lookup"><span data-stu-id="86721-126">In the **Add Table** dialog box, select the element or elements that you want to include in your new view from one of the following tabs: Tables, Views, Functions, and Synonyms.</span></span>  
  
4.  <span data-ttu-id="86721-127">按一下 **[加入]** ，然後按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="86721-127">Click **Add**, then click **Close**.</span></span>  
  
5.  <span data-ttu-id="86721-128">在 **[圖表]** 窗格中，選取要包含在新檢視中的資料行或其他元素。</span><span class="sxs-lookup"><span data-stu-id="86721-128">In the **Diagram Pane**, select the columns or other elements to include in the new view.</span></span>  
  
6.  <span data-ttu-id="86721-129">在 **[準則]** 窗格中，選擇資料行的其他排序或篩選準則。</span><span class="sxs-lookup"><span data-stu-id="86721-129">In the **Criteria Pane**, select additional sort or filter criteria for the columns.</span></span>  
  
7.  <span data-ttu-id="86721-130">在 [檔案]  功能表上，按一下 [儲存]  _view name_。</span><span class="sxs-lookup"><span data-stu-id="86721-130">On the **File** menu, click **Save**_view name_.</span></span>  
  
8.  <span data-ttu-id="86721-131">在 **[選擇名稱]** 對話方塊中，輸入新檢視的名稱，並按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="86721-131">In the **Choose Name** dialog box, enter a name for the new view and click **OK**.</span></span>  
  
     <span data-ttu-id="86721-132">如需查詢和檢視表設計工具的詳細資訊，請參閱[查詢和檢視表設計工具 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="86721-132">For more information about the query and view designer, see [Query and View Designer Tools &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="86721-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="86721-133">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-view"></a><span data-ttu-id="86721-134">建立檢視</span><span class="sxs-lookup"><span data-stu-id="86721-134">To create a view</span></span>  
  
1.  <span data-ttu-id="86721-135">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="86721-135">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="86721-136">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="86721-136">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="86721-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="86721-137">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    CREATE VIEW HumanResources.EmployeeHireDate  
    AS  
    SELECT p.FirstName, p.LastName, e.HireDate  
    FROM HumanResources.Employee AS e JOIN Person.Person AS  p  
    ON e.BusinessEntityID = p.BusinessEntityID ;   
    GO  
    -- Query the view  
    SELECT FirstName, LastName, HireDate  
    FROM HumanResources.EmployeeHireDate  
    ORDER BY LastName;  
  
    ```  
  
 <span data-ttu-id="86721-138">如需詳細資訊，請參閱 [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="86721-138">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
  
