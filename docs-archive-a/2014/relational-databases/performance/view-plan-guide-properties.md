---
title: 檢視計畫指南屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.planguideprop.general.f1
helpviewer_keywords:
- plan guides [SQL Server], view plan guide properties
- viewing plan guide properties
ms.assetid: 8c0d2f39-59c1-4168-a649-65473f6a771b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af29c66690a43f89106c1f77aca8c3a02eff2ba9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699514"
---
# <a name="view-plan-guide-properties"></a><span data-ttu-id="1cf42-102">檢視計畫指南屬性</span><span class="sxs-lookup"><span data-stu-id="1cf42-102">View Plan Guide Properties</span></span>
  <span data-ttu-id="1cf42-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cf42-103">You can view the properties of plan guides in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)]</span></span>  
  
 <span data-ttu-id="1cf42-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1cf42-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1cf42-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1cf42-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1cf42-106">安全性</span><span class="sxs-lookup"><span data-stu-id="1cf42-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1cf42-107">**使用下列方法來檢視計畫指南的屬性：**</span><span class="sxs-lookup"><span data-stu-id="1cf42-107">**To view the properties of plan guides, using:**</span></span>  
  
     [<span data-ttu-id="1cf42-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1cf42-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1cf42-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1cf42-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1cf42-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="1cf42-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1cf42-111">Security</span><span class="sxs-lookup"><span data-stu-id="1cf42-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1cf42-112">權限</span><span class="sxs-lookup"><span data-stu-id="1cf42-112">Permissions</span></span>  
 <span data-ttu-id="1cf42-113">目錄檢視內中繼資料的可見性會限制在使用者所擁有的安全性實體，或已授與使用者某些權限的安全性實體。</span><span class="sxs-lookup"><span data-stu-id="1cf42-113">The visibility of the metadata in catalog views is limited to securables that either a user owns or on which the user has been granted some permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1cf42-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1cf42-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="1cf42-115">檢視計畫指南的屬性</span><span class="sxs-lookup"><span data-stu-id="1cf42-115">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="1cf42-116">按一下加號，展開您要在其中檢視計畫指南屬性的資料庫，然後按一下加號展開 **[可程式性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cf42-116">Click the plus sign to expand the database in which you want to view the properties of a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="1cf42-117">按一下加號展開 **[計畫指南]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1cf42-117">Click the plus sign to expand the **Plan Guides** folder.</span></span>  
  
3.  <span data-ttu-id="1cf42-118">以滑鼠右鍵按一下要檢視其屬性的計劃指南，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="1cf42-118">Right-click the plan guide of which you want to view the properties and select **Properties**.</span></span>  
  
     <span data-ttu-id="1cf42-119">下列屬性會在 **[計畫指南屬性]** 對話方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="1cf42-119">The following properties show in the **Plan Guide Properties** dialog box.</span></span>  
  
     <span data-ttu-id="1cf42-120">**提示**</span><span class="sxs-lookup"><span data-stu-id="1cf42-120">**Hints**</span></span>  
     <span data-ttu-id="1cf42-121">顯示套用到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的查詢提示或查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="1cf42-121">Displays the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="1cf42-122">當指定了某個查詢計畫做為提示時，會顯示該計畫的 XML 執行程序表輸出。</span><span class="sxs-lookup"><span data-stu-id="1cf42-122">When a query plan is specified as a hint, the XML Showplan output for the plan is displayed.</span></span>  
  
     <span data-ttu-id="1cf42-123">**為已停用**</span><span class="sxs-lookup"><span data-stu-id="1cf42-123">**Is disabled**</span></span>  
     <span data-ttu-id="1cf42-124">顯示計畫指南的狀態。</span><span class="sxs-lookup"><span data-stu-id="1cf42-124">Displays the status of the plan guide.</span></span> <span data-ttu-id="1cf42-125">可能的值為 **True** 和 **False**。</span><span class="sxs-lookup"><span data-stu-id="1cf42-125">Possible values are **True** and **False**.</span></span>  
  
     <span data-ttu-id="1cf42-126">**名稱**</span><span class="sxs-lookup"><span data-stu-id="1cf42-126">**Name**</span></span>  
     <span data-ttu-id="1cf42-127">顯示計畫指南的名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf42-127">Displays the name of the plan guide.</span></span>  
  
     <span data-ttu-id="1cf42-128">**參數**</span><span class="sxs-lookup"><span data-stu-id="1cf42-128">**Parameters**</span></span>  
     <span data-ttu-id="1cf42-129">當範圍類型為 SQL 或 TEMPLATE 時，顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中內嵌的所有參數的名稱與資料類型。</span><span class="sxs-lookup"><span data-stu-id="1cf42-129">When the scope type is SQL or TEMPLATE, displays the name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="1cf42-130">**範圍批次**</span><span class="sxs-lookup"><span data-stu-id="1cf42-130">**Scope batch**</span></span>  
     <span data-ttu-id="1cf42-131">顯示在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中出現的批次文字。</span><span class="sxs-lookup"><span data-stu-id="1cf42-131">Displays the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="1cf42-132">**範圍物件名稱**</span><span class="sxs-lookup"><span data-stu-id="1cf42-132">**Scope object name**</span></span>  
     <span data-ttu-id="1cf42-133">當範圍類型為 OBJECT 時，則顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序、使用者定義純量函數、多重陳述式資料表值函式或其中出現 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式之 DML 觸發程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf42-133">When the scope type is OBJECT, displays the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span>  
  
     <span data-ttu-id="1cf42-134">**範圍結構描述名稱**</span><span class="sxs-lookup"><span data-stu-id="1cf42-134">**Scope schema name**</span></span>  
     <span data-ttu-id="1cf42-135">當範圍類型為 OBJECT 時，顯示包含了該物件的結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf42-135">When the scope type is OBJECT, displays the name of the schema in which the object is contained.</span></span>  
  
     <span data-ttu-id="1cf42-136">**範圍類型**</span><span class="sxs-lookup"><span data-stu-id="1cf42-136">**Scope type**</span></span>  
     <span data-ttu-id="1cf42-137">顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳列式中出現的實體類型。</span><span class="sxs-lookup"><span data-stu-id="1cf42-137">Displays the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="1cf42-138">這會指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式要與計畫指南比對相符的內容。</span><span class="sxs-lookup"><span data-stu-id="1cf42-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="1cf42-139">可能的值是 **OBJECT**、 **SQL**，以及 **TEMPLATE**。</span><span class="sxs-lookup"><span data-stu-id="1cf42-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
     <span data-ttu-id="1cf42-140">**陳述式**</span><span class="sxs-lookup"><span data-stu-id="1cf42-140">**Statement**</span></span>  
     <span data-ttu-id="1cf42-141">顯示對照套用計畫指南的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="1cf42-141">Displays the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is applied.</span></span>  
  
4.  <span data-ttu-id="1cf42-142">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1cf42-142">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1cf42-143">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1cf42-143">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-properties-of-a-plan-guide"></a><span data-ttu-id="1cf42-144">檢視計畫指南的屬性</span><span class="sxs-lookup"><span data-stu-id="1cf42-144">To view the properties of a plan guide</span></span>  
  
1.  <span data-ttu-id="1cf42-145">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1cf42-145">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1cf42-146">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="1cf42-146">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1cf42-147">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="1cf42-147">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- If a plan guide named "Guide1" already exists in the AdventureWorks2012 database, delete it.  
    USE AdventureWorks2012;  
    GO  
    IF OBJECT_ID(N'Guide1') IS NOT NULL  
       EXEC sp_control_plan_guide N'DROP', N'Guide1';  
    GO  
    -- creates a plan guide named Guide1 based on a SQL statement  
    EXEC sp_create_plan_guide   
        @name = N'Guide1',   
        @stmt = N'SELECT TOP 1 *   
                  FROM Sales.SalesOrderHeader   
                  ORDER BY OrderDate DESC',   
        @type = N'SQL',  
        @module_or_batch = NULL,   
        @params = NULL,   
        @hints = N'OPTION (MAXDOP 1)';  
    GO  
    -- Gets the name, created date, and all other relevant property information on the plan guide created above.   
    SELECT name AS plan_guide_name,  
       create_date,  
       query_text,  
       scope_type_desc,  
       OBJECT_NAME(scope_object_id) AS scope_object_name,  
       scope_batch,  
       parameters,  
       hints,  
       is_disabled  
    FROM sys.plan_guides  
    WHERE name = N'Guide1';  
    GO  
    ```  
  
 <span data-ttu-id="1cf42-148">如需詳細資訊，請參閱 [sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1cf42-148">For more information, see [sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql).</span></span>  
  
  
