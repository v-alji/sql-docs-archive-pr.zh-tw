---
title: 建立工作負載群組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group create
- workload groups [SQL Server], create
ms.assetid: 072868ec-ceff-4db6-941b-281af731a067
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 144bcef57b3d6e191b03b1539e9e7382a9085c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594474"
---
# <a name="create-a-workload-group"></a><span data-ttu-id="7eb76-102">建立工作負載群組</span><span class="sxs-lookup"><span data-stu-id="7eb76-102">Create a Workload Group</span></span>
  <span data-ttu-id="7eb76-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]來建立工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="7eb76-103">You can create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
-   <span data-ttu-id="7eb76-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="7eb76-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="7eb76-105">**若要建立工作負載群組，請使用下列方式：** [SQL Server Management Studio](#CreWGProp)、[Transact-SQL](#CreWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="7eb76-105">**To create a workload group, using:**  [SQL Server Management Studio](#CreWGProp), [Transact-SQL](#CreWGTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7eb76-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="7eb76-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="7eb76-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="7eb76-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="7eb76-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="7eb76-108">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="7eb76-109">非對齊式資料分割資料表上之索引建立所耗用的記憶體，與相關的資料分割數目成正比。</span><span class="sxs-lookup"><span data-stu-id="7eb76-109">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="7eb76-110">如果所需的總記憶體超出工作負載群組設定所設的每個查詢限制 (REQUEST_MAX_MEMORY_GRANT_PERCENT)，這個索引建立動作可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="7eb76-110">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="7eb76-111">由於預設工作負載群組允許查詢超過每個查詢限制，而且基於 SQL Server 2005 相容性會啟動所需的記憶體下限，因此使用者或許能夠在預設工作負載群組中執行相同的索引建立動作，但前提是預設資源集區有設定足夠的總記憶體來執行這類查詢。</span><span class="sxs-lookup"><span data-stu-id="7eb76-111">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="7eb76-112">允許索引建立使用比一開始授與之記憶體更多的記憶體工作空間來改善效能。</span><span class="sxs-lookup"><span data-stu-id="7eb76-112">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="7eb76-113">資源管理員支援這種特殊的處理，不過，初始授與和任何額外的記憶體授與都受到工作負載群組和資源集區設定的限制。</span><span class="sxs-lookup"><span data-stu-id="7eb76-113">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="7eb76-114">權限</span><span class="sxs-lookup"><span data-stu-id="7eb76-114">Permissions</span></span>  
 <span data-ttu-id="7eb76-115">建立工作負載群組需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="7eb76-115">Creating a workload group requires CONTROL SERVER permission.</span></span>  
  
##  <a name="create-a-workload-group-using-sql-server-management-studio"></a><a name="CreWGProp"></a> <span data-ttu-id="7eb76-116">使用 SQL Server Management Studio 建立工作負載群組</span><span class="sxs-lookup"><span data-stu-id="7eb76-116">Create a Workload Group Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="7eb76-117">**若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="7eb76-117">**To create a workload group by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="7eb76-118">在 [物件總管] 中，遞迴地向下展開 **[管理]** 節點至包含要修改之工作負載群組的資源集區。</span><span class="sxs-lookup"><span data-stu-id="7eb76-118">In Object Explorer, recursively expand the **Management** node down to and including the resource pool that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="7eb76-119">以滑鼠右鍵按一下 [工作負載群組] 資料夾，然後按一下 [新增工作負載群組]。</span><span class="sxs-lookup"><span data-stu-id="7eb76-119">Right-click the **Workload Groups** folder, and then click **New Workload Group**.</span></span>  
  
3.  <span data-ttu-id="7eb76-120">在 **[資源集區]** 方格中，確定已反白顯示要新增工作負載群組的資源集區。</span><span class="sxs-lookup"><span data-stu-id="7eb76-120">In the **Resource pools** grid, ensure the resource pool where you want to add the workload group is highlighted.</span></span>  
  
4.  <span data-ttu-id="7eb76-121">**[資源集區的工作負載群組]** 方格中會新增一行，其中包含空白名稱和其他資料行的預設值。</span><span class="sxs-lookup"><span data-stu-id="7eb76-121">The **Workload groups for resource pool** grid will have a new line with a blank name and default values in the other columns.</span></span>  
  
5.  <span data-ttu-id="7eb76-122">按一下 **[名稱]** 資料格，然後輸入工作負載群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="7eb76-122">Click the **Name** cell and enter a name for the workload group.</span></span>  
  
6.  <span data-ttu-id="7eb76-123">在資料列中按一下或按兩下要變更預設值的任何其他資料格，然後輸入新值。</span><span class="sxs-lookup"><span data-stu-id="7eb76-123">Click or double-click any other cells in the row you want to change from their default settings, and enter the new values.</span></span>  
  
7.  <span data-ttu-id="7eb76-124">若要儲存變更，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="7eb76-124">To save the changes, click **OK**</span></span>  
  
##  <a name="create-a-workload-group-using-transact-sql"></a><a name="CreWGTSQL"></a> <span data-ttu-id="7eb76-125">使用 Transact-SQL 建立工作負載群組</span><span class="sxs-lookup"><span data-stu-id="7eb76-125">Create a Workload Group Using Transact-SQL</span></span>  
 <span data-ttu-id="7eb76-126">**若要使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="7eb76-126">**To create a workload group by using [!INCLUDE[tsql](../../includes/tsql-md.md)]**</span></span>  
  
1.  <span data-ttu-id="7eb76-127">執行 CREATE WORKLOAD GROUP 陳述式，指定要設定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="7eb76-127">Run the CREATE WORKLOAD GROUP statement specifying the property values to be set.</span></span>  
  
2.  <span data-ttu-id="7eb76-128">執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7eb76-128">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="7eb76-129">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7eb76-129">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="7eb76-130">下列範例會在 `groupAdhoc` 資源集區中建立一個名為 `poolAdhoc`的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="7eb76-130">The following example creates a workload group named `groupAdhoc` in the resource pool named `poolAdhoc`.</span></span>  
  
```  
CREATE WORKLOAD GROUP groupAdhoc  
USING poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7eb76-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eb76-131">See Also</span></span>  
 <span data-ttu-id="7eb76-132">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7eb76-132">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="7eb76-133">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="7eb76-133">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="7eb76-134">[建立資源集區](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="7eb76-134">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="7eb76-135">[變更工作負載群組設定](change-workload-group-settings.md) </span><span class="sxs-lookup"><span data-stu-id="7eb76-135">[Change Workload Group Settings](change-workload-group-settings.md) </span></span>  
 <span data-ttu-id="7eb76-136">[建立和測試分類使用者定義函數](create-and-test-a-classifier-user-defined-function.md) </span><span class="sxs-lookup"><span data-stu-id="7eb76-136">[Create and Test a Classifier User-Defined Function](create-and-test-a-classifier-user-defined-function.md) </span></span>  
 <span data-ttu-id="7eb76-137">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="7eb76-137">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 [<span data-ttu-id="7eb76-138">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="7eb76-138">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
