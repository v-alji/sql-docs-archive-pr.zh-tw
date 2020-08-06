---
title: 建立新的計畫指南 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.designer.newplanguide.f1
helpviewer_keywords:
- creating plan guides
- plan guides [SQL Server]. creating
ms.assetid: e1ad78bb-4857-40ea-a0c6-dcf5c28aef2f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60ba31e2a63575a316db5befb397bea59c0ad1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606818"
---
# <a name="create-a-new-plan-guide"></a><span data-ttu-id="6a3cd-102">建立新的計畫指南</span><span class="sxs-lookup"><span data-stu-id="6a3cd-102">Create a New Plan Guide</span></span>
  <span data-ttu-id="6a3cd-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立計畫指南。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-103">You can create a plan guide in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="6a3cd-104">計畫指南是將查詢提示或固定的查詢計畫附加至查詢，以影響查詢的最佳化。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-104">Plan guides influence query optimization by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="6a3cd-105">在計畫指南中，指定您要最佳化的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或包含您想要使用的查詢提示的 OPTION 子句，或者是您想要用來將查詢進行最佳化的特定查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-105">In the plan guide, you specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="6a3cd-106">在執行查詢的時候，查詢最佳化工具會比對 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式與計畫指南，在執行階段將 OPTION 子句附加至查詢，或是使用特定的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-106">When the query executes, the query optimizer matches the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide and either attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="6a3cd-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6a3cd-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6a3cd-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6a3cd-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6a3cd-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="6a3cd-109">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="6a3cd-110">安全性</span><span class="sxs-lookup"><span data-stu-id="6a3cd-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6a3cd-111">**使用下列方法建立計畫指南：**</span><span class="sxs-lookup"><span data-stu-id="6a3cd-111">**To create a plan guide, using:**</span></span>  
  
     [<span data-ttu-id="6a3cd-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6a3cd-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6a3cd-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6a3cd-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6a3cd-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="6a3cd-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="6a3cd-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="6a3cd-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="6a3cd-116">sp_create_plan_guide 的引數必須依照顯示順序提供。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-116">The arguments to sp_create_plan_guide must be provided in the order that is shown.</span></span> <span data-ttu-id="6a3cd-117">當您提供 `sp_create_plan_guide` 的參數值時，必須明確指定所有的參數名稱，或是完全不指定。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-117">When you supply values for the parameters of `sp_create_plan_guide`, all parameter names must be specified explicitly, or none at all.</span></span> <span data-ttu-id="6a3cd-118">例如，如果指定了 `@name =`，您也必須指定 `@stmt =`、`@type =` 等等。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-118">For example, if `@name =` is specified, then `@stmt =` , `@type =`, and so on, must also be specified.</span></span> <span data-ttu-id="6a3cd-119">同樣地，如果省略 `@name =`，而只提供參數值，您也必須省略其餘參數名稱，只提供它們的值。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-119">Likewise, if `@name =` is omitted and only the parameter value is provided, the remaining parameter names must also be omitted, and only their values provided.</span></span> <span data-ttu-id="6a3cd-120">引數名稱僅供描述用途，以協助您了解語法。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-120">Argument names are for descriptive purposes only, to help understand the syntax.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6a3cd-121">不會驗證指定的參數名稱是否與使用該名稱之位置中的參數名稱相符。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-121">does not verify that the specified parameter name matches the name for the parameter in the position where the name is used.</span></span>  
  
-   <span data-ttu-id="6a3cd-122">您可以針對相同的查詢和批次或模組，建立一個以上的 OBJECT 或 SQL 計畫指南。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-122">You can create more than one OBJECT or SQL plan guide for the same query and batch or module.</span></span> <span data-ttu-id="6a3cd-123">但是，在任何指定的時間內，只能啟用一個計畫指南。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-123">However, only one plan guide can be enabled at any given time.</span></span>  
  
-   <span data-ttu-id="6a3cd-124">若 @module_or_batch 值參考的預存程序、函數或 DML 觸發程序指定了 WITH ENCRYPTION 子句或是暫時項目，您就不能為這個值建立 OBJECT 類型的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-124">Plan guides of type OBJECT cannot be created for an @module_or_batch value that references a stored procedure, function, or DML trigger that specifies the WITH ENCRYPTION clause or that is temporary.</span></span>  
  
-   <span data-ttu-id="6a3cd-125">試圖卸除或修改計畫指南所參考的函數、預存程序或 DML 觸發程序，不論是已啟用或已停用，都會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-125">Trying to drop or modify a function, stored procedure, or DML trigger that is referenced by a plan guide, either enabled or disabled, causes an error.</span></span> <span data-ttu-id="6a3cd-126">嘗試卸除定義了觸發程序且被計畫指南參考的資料表也會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-126">Trying to drop a table that has a trigger defined on it that is referenced by a plan guide also causes an error.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6a3cd-127">Security</span><span class="sxs-lookup"><span data-stu-id="6a3cd-127">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6a3cd-128">權限</span><span class="sxs-lookup"><span data-stu-id="6a3cd-128">Permissions</span></span>  
 <span data-ttu-id="6a3cd-129">若要建立類型為 OBJECT 的計畫指南，需要所參考物件的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-129">To create a plan guide of type OBJECT, requires ALTER permission on the referenced object.</span></span> <span data-ttu-id="6a3cd-130">若要建立類型為 SQL 或 TEMPLATE 的計畫指南，需要目前資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-130">To create a plan guide of type SQL or TEMPLATE, requires ALTER permission on the current database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6a3cd-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6a3cd-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="6a3cd-132">若要建立計畫指南</span><span class="sxs-lookup"><span data-stu-id="6a3cd-132">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="6a3cd-133">按一下加號，展開您要在其中建立計畫指南的資料庫，然後按一下加號展開 **[可程式性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-133">Click the plus sign to expand the database in which you want to create a plan guide, and then click the plus sign to expand the **Programmability** folder.</span></span>  
  
2.  <span data-ttu-id="6a3cd-134">以滑鼠右鍵按一下 [**計劃指南**] 資料夾，然後選取 [**新增計劃指南**]。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-134">Right-click the **Plan Guides** folder and select **New Plan Guide...**.</span></span>  
  
3.  <span data-ttu-id="6a3cd-135">在 **[新增維護計畫]** 對話方塊中的 **[名稱]** 方塊，輸入計畫指南的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-135">In the **New Plan Guide** dialog box, in the **Name** box, enter the name of the plan guide.</span></span>  
  
4.  <span data-ttu-id="6a3cd-136">在 **[陳述式]** 方塊中，輸入對照套用計畫指南的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-136">In the **Statement** box, enter the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement against which the plan guide is to be applied.</span></span>  
  
5.  <span data-ttu-id="6a3cd-137">在 **[範圍類型]** 清單中，選取在其中顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的實體類型。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-137">In the **Scope type** list, select the type of entity in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="6a3cd-138">這會指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式要與計畫指南比對相符的內容。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-138">This specifies the context for matching the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to the plan guide.</span></span> <span data-ttu-id="6a3cd-139">可能的值是 **OBJECT**、 **SQL**，以及 **TEMPLATE**。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-139">Possible values are **OBJECT**, **SQL**, and **TEMPLATE**.</span></span>  
  
6.  <span data-ttu-id="6a3cd-140">在 **[範圍批次]** 方塊中，輸入在其中顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的批次文字。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-140">In the **Scope batch** box, enter the batch text in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="6a3cd-141">批次文字不能包含 USE\`\`*database* 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-141">The batch text cannot include a USE\`\`*database* statement.</span></span> <span data-ttu-id="6a3cd-142">**[範圍批次]** 方塊只在 **[SQL]** 選定為範圍類型時才可供使用。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-142">The **Scope batch** box is only available when **SQL** is selected as a scope type.</span></span> <span data-ttu-id="6a3cd-143">如果 SQL 是範圍類型，但未在 [範圍批次] 方塊中輸入任何內容時，批次文字的值會設為與 **[陳述式]** 方塊中的值相同。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-143">If nothing is entered in the scope batch box when SQL is the scope type, then the value of the batch text is set to the same value as is in the **Statement** box.</span></span>  
  
7.  <span data-ttu-id="6a3cd-144">在 **[範圍結構描述名稱]** 清單中，輸入包含了該物件的結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-144">In the **Scope schema name** list, enter the name of the schema in which the object is contained.</span></span> <span data-ttu-id="6a3cd-145">**[範圍結構描述名稱]** 方塊只在 **[物件]** 選定為範圍類型時才可供使用。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-145">The **Scope schema name** box is only available when **Object** is selected as a scope type.</span></span>  
  
8.  <span data-ttu-id="6a3cd-146">在 [範圍物件名稱] 方塊中，輸入顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序名稱、使用者定義純量函數名稱、多重陳述式資料表值函數名稱或 DML 觸發程序名稱。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-146">In the **Scope object name** box, enter the name of the [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, user-defined scalar function, multistatement table-valued function, or DML trigger in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement appears.</span></span> <span data-ttu-id="6a3cd-147">**[範圍物件名稱]** 方塊只在 **[物件]** 選定為範圍類型時才可供使用。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-147">The **Scope object name** box is only available when **Object** is selected as a scope type.</span></span>  
  
9. <span data-ttu-id="6a3cd-148">在 **[參數]** 方塊中，輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中內嵌的所有參數的參數名稱與資料類型。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-148">In the **Parameters** box, enter the parameter name and data type of all parameters that are embedded in the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
     <span data-ttu-id="6a3cd-149">只有在下列兩者之一為真時，才套用參數：</span><span class="sxs-lookup"><span data-stu-id="6a3cd-149">Parameters apply only when either of the following is true:</span></span>  
  
    -   <span data-ttu-id="6a3cd-150">範圍類型為 **SQL** 或 **TEMPLATE**。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-150">The scope type is **SQL** or **TEMPLATE**.</span></span> <span data-ttu-id="6a3cd-151">如果是 **TEMPLATE**，參數必須不是 NULL。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-151">If **TEMPLATE**, parameters must not be NULL.</span></span>  
  
    -   <span data-ttu-id="6a3cd-152">[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式是使用已指定參數值的 sp_executesql 提交，或是在將它參數化之後，由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內部進行提交。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-152">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is submitted by using sp_executesql and a value for the parameter is specified, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internally submits a statement after parameterizing it.</span></span>  
  
10. <span data-ttu-id="6a3cd-153">在 **[提示]** 方塊中，輸入套用到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的查詢提示或查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-153">In the **Hints** box, enter the query hints or query plan to be applied to the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="6a3cd-154">如需指定一或多個查詢提示，請輸入有效的 OPTION 子句。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-154">To specify one or more query hints, enter a valid OPTION clause.</span></span>  
  
11. <span data-ttu-id="6a3cd-155">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-155">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6a3cd-156">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6a3cd-156">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-plan-guide"></a><span data-ttu-id="6a3cd-157">若要建立計畫指南</span><span class="sxs-lookup"><span data-stu-id="6a3cd-157">To create a plan guide</span></span>  
  
1.  <span data-ttu-id="6a3cd-158">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-158">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6a3cd-159">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-159">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6a3cd-160">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-160">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
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
  
    ```  
  
 <span data-ttu-id="6a3cd-161">如需詳細資訊，請參閱 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="6a3cd-161">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql).</span></span>  
  
  
