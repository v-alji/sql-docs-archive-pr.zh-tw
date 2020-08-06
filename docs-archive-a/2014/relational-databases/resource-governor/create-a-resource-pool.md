---
title: 建立資源集區 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- resource pools [SQL Server], create
- Resource Governor, resource pool create
ms.assetid: 44dd0567-a4c8-4c72-89ff-e76f6ddef344
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5abd2e60f4f9bb5290b47f95349782f8b26ad8bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606731"
---
# <a name="create-a-resource-pool"></a><span data-ttu-id="c01e2-102">建立資源集區</span><span class="sxs-lookup"><span data-stu-id="c01e2-102">Create a Resource Pool</span></span>
  <span data-ttu-id="c01e2-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]來建立資源集區。</span><span class="sxs-lookup"><span data-stu-id="c01e2-103">You can create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="c01e2-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="c01e2-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="c01e2-105">**若要建立資源集區，請使用下列方式：** [SQL Server Management Studio](#CreRPProp)、[Transact-SQL](#CreRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="c01e2-105">**To create a resource pool, using:**  [SQL Server Management Studio](#CreRPProp), [Transact-SQL](#CreRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c01e2-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="c01e2-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="c01e2-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="c01e2-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="c01e2-108">最大 CPU 百分比必須大於或等於最小 CPU 百分比。</span><span class="sxs-lookup"><span data-stu-id="c01e2-108">The maximum CPU percentage must be equal to or higher than the minimum CPU percentage.</span></span> <span data-ttu-id="c01e2-109">最大記憶體百分比必須大於或等於最小記憶體百分比。</span><span class="sxs-lookup"><span data-stu-id="c01e2-109">The maximum memory percentage must be equal to or higher than the minimum memory percentage.</span></span>  
  
 <span data-ttu-id="c01e2-110">所有資源集區之最小 CPU 百分比和最小記憶體百分比的總和不得超過 100。</span><span class="sxs-lookup"><span data-stu-id="c01e2-110">The sums of the minimum CPU percentages and minimum memory percentages for all resource pools must not exceed 100.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c01e2-111">權限</span><span class="sxs-lookup"><span data-stu-id="c01e2-111">Permissions</span></span>  
 <span data-ttu-id="c01e2-112">建立資源集區需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="c01e2-112">Creating a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-resource-pool-using-sql-server-management-studio"></a><a name="CreRPProp"></a> <span data-ttu-id="c01e2-113">使用 SQL Server Management Studio 建立資源集區</span><span class="sxs-lookup"><span data-stu-id="c01e2-113">Create a Resource Pool Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="c01e2-114">**若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="c01e2-114">**To create a resource pool by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="c01e2-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="c01e2-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="c01e2-116">以滑鼠右鍵按一下 [資源管理員]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="c01e2-116">Right-click **Resource Governor**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="c01e2-117">在 **[資源集區]** 方格中，按一下空白資料列的第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="c01e2-117">In the **Resource pools** grid, click the first column in the empty row.</span></span> <span data-ttu-id="c01e2-118">這個資料行標示有星號 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c01e2-118">This column is labeled with an asterisk (\*).</span></span>  
  
4.  <span data-ttu-id="c01e2-119">按兩下 [名稱] 資料行中的空白儲存格。</span><span class="sxs-lookup"><span data-stu-id="c01e2-119">Double-click the empty cell in the **Name** column.</span></span> <span data-ttu-id="c01e2-120">輸入您想要用於資源集區的名稱。</span><span class="sxs-lookup"><span data-stu-id="c01e2-120">Type in the name that you want to use for the resource pool.</span></span>  
  
5.  <span data-ttu-id="c01e2-121">在資料列中按一下或按兩下要變更的任何其他資料格，然後輸入新值。</span><span class="sxs-lookup"><span data-stu-id="c01e2-121">Click or double-click any other cells in the row you want to change, and enter the new values.</span></span>  
  
6.  <span data-ttu-id="c01e2-122">若要儲存變更，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="c01e2-122">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-resource-pool-using-transact-sql"></a><a name="CreRPTSQL"></a> <span data-ttu-id="c01e2-123">使用 Transact-SQL 建立資源集區</span><span class="sxs-lookup"><span data-stu-id="c01e2-123">Create a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="c01e2-124">**若要使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="c01e2-124">**To create a resource pool by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="c01e2-125">執行 `CREATE RESOURCE POOL` 陳述式，並指定要設定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="c01e2-125">Run the `CREATE RESOURCE POOL` statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="c01e2-126">執行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c01e2-126">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="c01e2-127">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c01e2-127">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="c01e2-128">下列範例會建立名稱為 `poolAdhoc`的資源集區。</span><span class="sxs-lookup"><span data-stu-id="c01e2-128">The following example creates a resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE RESOURCE POOL poolAdhoc  
WITH (MAX_CPU_PERCENT = 20);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c01e2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c01e2-129">See Also</span></span>  
 <span data-ttu-id="c01e2-130">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-130">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="c01e2-131">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-131">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="c01e2-132">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-132">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="c01e2-133">[變更資源集區設定](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-133">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="c01e2-134">[刪除資源集區](delete-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-134">[Delete a Resource Pool](delete-a-resource-pool.md) </span></span>  
 <span data-ttu-id="c01e2-135">[使用範本來設定資源管理員](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-135">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="c01e2-136">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-136">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="c01e2-137">[資源管理員分類函數](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="c01e2-137">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="c01e2-138">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c01e2-138">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="c01e2-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c01e2-139">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
