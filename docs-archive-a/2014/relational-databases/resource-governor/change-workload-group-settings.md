---
title: 變更工作負載群組設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], alter
- Resource Governor, workload group alter
ms.assetid: 73b6109c-2ad0-4915-b11b-d40d5a0fdc25
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 579aad71d32a629d75f1eecd76e7dacfe32d94f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584373"
---
# <a name="change-workload-group-settings"></a><span data-ttu-id="ea893-102">變更工作負載群組設定</span><span class="sxs-lookup"><span data-stu-id="ea893-102">Change Workload Group Settings</span></span>
  <span data-ttu-id="ea893-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來變更工作負載群組設定。</span><span class="sxs-lookup"><span data-stu-id="ea893-103">You can change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="ea893-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="ea893-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="ea893-105">**若要變更工作負載群組的設定，請使用下列方式：** [SQL Server Management Studio](#ChgWGProp)、[Transact-SQL](#ChgWGTSQL)</span><span class="sxs-lookup"><span data-stu-id="ea893-105">**To change the settings for a workload group, using:**  [SQL Server Management Studio](#ChgWGProp), [Transact-SQL](#ChgWGTSQL)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="ea893-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="ea893-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="ea893-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="ea893-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ea893-108">您可以變更預設工作負載群組和使用者定義工作負載群組的設定。</span><span class="sxs-lookup"><span data-stu-id="ea893-108">You can change the settings of the default workload group and user-defined workload groups.</span></span>  
  
 <span data-ttu-id="ea893-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="ea893-109">**REQUEST_MAX_MEMORY_GRANT_PERCENT**</span></span>  
  
 <span data-ttu-id="ea893-110">非對齊式資料分割資料表上之索引建立所耗用的記憶體，與相關的資料分割數目成正比。</span><span class="sxs-lookup"><span data-stu-id="ea893-110">The memory consumed by index creation on a non-aligned partitioned table is proportional to the number of partitions involved.</span></span> <span data-ttu-id="ea893-111">如果所需的總記憶體超出工作負載群組設定所設的每個查詢限制 (REQUEST_MAX_MEMORY_GRANT_PERCENT)，這個索引建立動作可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="ea893-111">If the total required memory exceeds the per-query limit, (REQUEST_MAX_MEMORY_GRANT_PERCENT) imposed by the workload group setting, this index creation may fail.</span></span> <span data-ttu-id="ea893-112">由於預設工作負載群組允許查詢超過每個查詢限制，而且基於 SQL Server 2005 相容性會啟動所需的記憶體下限，因此使用者或許能夠在預設工作負載群組中執行相同的索引建立動作，但前提是預設資源集區有設定足夠的總記憶體來執行這類查詢。</span><span class="sxs-lookup"><span data-stu-id="ea893-112">Because the default workload group allows a query to exceed the per-query limit with the minimum required memory to start for SQL Server 2005 compatibility, the user may be able to run the same index creation in the default workload group, if the default resource pool has enough total memory configured to run such a query.</span></span>  
  
 <span data-ttu-id="ea893-113">允許索引建立使用比一開始授與之記憶體更多的記憶體工作空間來改善效能。</span><span class="sxs-lookup"><span data-stu-id="ea893-113">Index creation is allowed to use more memory workspace than initially granted for performance.</span></span> <span data-ttu-id="ea893-114">資源管理員支援這種特殊的處理，不過，初始授與和任何額外的記憶體授與都受到工作負載群組和資源集區設定的限制。</span><span class="sxs-lookup"><span data-stu-id="ea893-114">This special handling is supported by Resource Governor, however, the initial grant and any additional memory grant are limited by the workload group and resource pool settings.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ea893-115">權限</span><span class="sxs-lookup"><span data-stu-id="ea893-115">Permissions</span></span>  
 <span data-ttu-id="ea893-116">變更工作負載群組設定需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="ea893-116">Changing workload group settings requires CONTROL SERVER permission.</span></span>  
  
##  <a name="change-workload-group-settings-using-sql-server-management-studio"></a><a name="ChgWGProp"></a> <span data-ttu-id="ea893-117">使用 SQL Server Management Studio 變更工作負載群組設定</span><span class="sxs-lookup"><span data-stu-id="ea893-117">Change Workload Group Settings Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="ea893-118">**若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="ea893-118">**To change workload group settings by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="ea893-119">在 [物件總管] 中，遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 資料夾，此資料夾包含要修改的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="ea893-119">In Object Explorer, recursively expand the **Management** node down to and including the **Workload Groups** folder that contains the workload group to be modified.</span></span>  
  
2.  <span data-ttu-id="ea893-120">以滑鼠右鍵按一下要修改的工作負載群組，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="ea893-120">Right-click the workload group to be modified, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="ea893-121">在 **[資源管理員屬性]** 頁面的 **[資源集區的工作負載群組]** 方格中，選取工作負載群組的資料列 (如果系統沒有自動選取的話)。</span><span class="sxs-lookup"><span data-stu-id="ea893-121">In the **Resource Governor Properties** page, select the row for the workload group in the **Workload groups for resource pool** grid if it is not automatically selected.</span></span>  
  
4.  <span data-ttu-id="ea893-122">在資料列中按一下或按兩下要變更的資料格，然後輸入新值。</span><span class="sxs-lookup"><span data-stu-id="ea893-122">Click or double-click the cells in the row to be changed, and enter the new values.</span></span>  
  
5.  <span data-ttu-id="ea893-123">若要儲存變更，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="ea893-123">To save the changes, click **OK**</span></span>  
  
##  <a name="change-workload-group-settings-using-transact-sql"></a><a name="ChgWGTSQL"></a> <span data-ttu-id="ea893-124">使用 Transact-SQL 變更工作負載群組設定</span><span class="sxs-lookup"><span data-stu-id="ea893-124">Change Workload Group Settings Using Transact-SQL</span></span>  
 <span data-ttu-id="ea893-125">**若要使用 Transact-SQL 來變更工作負載群組設定**</span><span class="sxs-lookup"><span data-stu-id="ea893-125">**To change workload group settings by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="ea893-126">執行 ALTER WORKLOAD GROUP 陳述式，指定要變更的屬性值。</span><span class="sxs-lookup"><span data-stu-id="ea893-126">Run the ALTER WORKLOAD GROUP statement specifying the property values to be changed.</span></span>  
  
2.  <span data-ttu-id="ea893-127">執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ea893-127">Run the ALTER RESOURCE GOVERNOR RECONFIGURE statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="ea893-128">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea893-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="ea893-129">下列範例會變更名為 `groupAdhoc`的工作負載群組的最大記憶體授與百分比設定。</span><span class="sxs-lookup"><span data-stu-id="ea893-129">The following example changes the max memory grant percent setting for the workload group named `groupAdhoc`.</span></span>  
  
```  
ALTER WORKLOAD GROUP groupAdhoc  
WITH (REQUEST_MAX_MEMORY_GRANT_PERCENT = 30);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea893-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea893-130">See Also</span></span>  
 <span data-ttu-id="ea893-131">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ea893-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="ea893-132">[建立工作負載群組](create-a-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="ea893-132">[Create a Workload Group](create-a-workload-group.md) </span></span>  
 <span data-ttu-id="ea893-133">[建立資源集區](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="ea893-133">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="ea893-134">[變更資源集區設定](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="ea893-134">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="ea893-135">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ea893-135">[ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="ea893-136">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ea893-136">[ALTER RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="ea893-137">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ea893-137">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
