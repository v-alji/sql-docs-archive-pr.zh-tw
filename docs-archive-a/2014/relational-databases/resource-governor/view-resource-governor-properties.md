---
title: 檢視資源管理員屬性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.swb.rg.properties.f1
helpviewer_keywords:
- Resource Governor, properties
ms.assetid: de3510df-f792-4a9d-80fa-f198fd36cdc8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cd7af8f4f8eb3cd0531bc907011846f73f94f6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594470"
---
# <a name="view-resource-governor-properties"></a><span data-ttu-id="318ea-102">檢視資源管理員屬性</span><span class="sxs-lookup"><span data-stu-id="318ea-102">View Resource Governor Properties</span></span>
  <span data-ttu-id="318ea-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 [資源管理員屬性] 頁面來建立或設定資源管理員實體，例如資源集區和工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="318ea-103">You can create or configure Resource Governor entities, such as resource pools and workload groups, by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
1.  <span data-ttu-id="318ea-104">**開始之前：** [權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="318ea-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="318ea-105">**若要檢視資源管理員屬性，請使用：**  [資源管理員屬性頁面](#ViewRGProp)</span><span class="sxs-lookup"><span data-stu-id="318ea-105">**To view Resource Governor properties, using:**  [Resource Governor Properties page](#ViewRGProp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="318ea-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="318ea-106">Before You Begin</span></span>  
 <span data-ttu-id="318ea-107">除了檢視資源管理員實體的屬性之外，還可以使用 **[資源管理員屬性]** 頁面執行多個組態工作。</span><span class="sxs-lookup"><span data-stu-id="318ea-107">In addition to viewing the properties of Resource Governor entities, you can perform several configuration tasks using the **Resource Governor Properties** page.</span></span> <span data-ttu-id="318ea-108">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="318ea-108">For more information, see these topics:</span></span>  
  
-   [<span data-ttu-id="318ea-109">啟用資源管理員</span><span class="sxs-lookup"><span data-stu-id="318ea-109">Enable Resource Governor</span></span>](enable-resource-governor.md)  
  
-   [<span data-ttu-id="318ea-110">停用資源管理員</span><span class="sxs-lookup"><span data-stu-id="318ea-110">Disable Resource Governor</span></span>](disable-resource-governor.md)  
  
-   [<span data-ttu-id="318ea-111">建立資源集區</span><span class="sxs-lookup"><span data-stu-id="318ea-111">Create a Resource Pool</span></span>](create-a-resource-pool.md)  
  
-   [<span data-ttu-id="318ea-112">建立工作負載群組</span><span class="sxs-lookup"><span data-stu-id="318ea-112">Create a Workload Group</span></span>](create-a-workload-group.md)  
  
-   [<span data-ttu-id="318ea-113">變更資源集區設定</span><span class="sxs-lookup"><span data-stu-id="318ea-113">Change Resource Pool Settings</span></span>](change-resource-pool-settings.md)  
  
-   [<span data-ttu-id="318ea-114">變更工作負載群組設定</span><span class="sxs-lookup"><span data-stu-id="318ea-114">Change Workload Group Settings</span></span>](change-workload-group-settings.md)  
  
-   [<span data-ttu-id="318ea-115">移動工作負載群組</span><span class="sxs-lookup"><span data-stu-id="318ea-115">Move a Workload Group</span></span>](move-a-workload-group.md)  
  
 <span data-ttu-id="318ea-116">加入、刪除或移動工作負載群組或資源集區之後，當您按一下 **[確定]** 時，系統就會執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="318ea-116">When you click **OK** after adding, deleting, or moving a workload group or resource pool, the ALTER RESOURCE GOVERNOR RECONFIGURE statement is executed.</span></span>  
  
 <span data-ttu-id="318ea-117">如果建立或重新設定資源集區或工作負載群組的工作失敗，在屬性頁的標題下方會出現摘要錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="318ea-117">If the create or reconfigure operation for the resource pool or workload group fails, a summary error message appears below the title of the property page.</span></span> <span data-ttu-id="318ea-118">若要查看詳細錯誤訊息，按一下錯誤訊息上的向下箭頭。</span><span class="sxs-lookup"><span data-stu-id="318ea-118">To see a detailed error message, click the down arrow on the error message.</span></span>  
  
 <span data-ttu-id="318ea-119">您可以利用查詢 [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) 動態管理檢視的方式，查看目前 is_configuration_pending 的狀況，了解是否有暫止的組態。</span><span class="sxs-lookup"><span data-stu-id="318ea-119">You can determine whether there is a configuration pending by querying the [sys.dm_resource_governor_configuration](/sql/relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql) dynamic management view to get the current status of is_configuration_pending.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="318ea-120">權限</span><span class="sxs-lookup"><span data-stu-id="318ea-120">Permissions</span></span>  
 <span data-ttu-id="318ea-121">檢視資源管理員屬性需要 VIEW SERVER STATER 權限。</span><span class="sxs-lookup"><span data-stu-id="318ea-121">Viewing resource governor properties requires VIEW SERVER STATER permission.</span></span> <span data-ttu-id="318ea-122">資源管理員組態工作需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="318ea-122">The resource governor configuration tasks require CONTROL SERVER permission.</span></span>  
  
##  <a name="view-the-resource-governor-properties-page"></a><a name="ViewRGProp"></a><span data-ttu-id="318ea-123">查看 Resource Governor 屬性頁面</span><span class="sxs-lookup"><span data-stu-id="318ea-123">View the Resource Governor Properties Page</span></span>  
 <span data-ttu-id="318ea-124">**若要使用下列項目中的 [Resource Governor 屬性] 頁面來檢視 Resource Governor 屬性： [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="318ea-124">**To view resource governor properties by using the Resource Governor Properties page in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="318ea-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="318ea-125">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="318ea-126">以滑鼠右鍵按一下 [資源管理員]，然後按一下 [屬性]，這會開啟 [資源管理員屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="318ea-126">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="318ea-127">如需有關該頁中之欄位的說明，請參閱＜ [資源管理員屬性](#RGProp)＞。</span><span class="sxs-lookup"><span data-stu-id="318ea-127">For descriptions of the fields in the page, see [Resource Governor Properties](#RGProp).</span></span>  
  
4.  <span data-ttu-id="318ea-128">若要儲存任何變更，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="318ea-128">To save any changes, click **OK**.</span></span>  
  
##  <a name="resource-governor-properties"></a><a name="RGProp"></a><span data-ttu-id="318ea-129">Resource Governor 屬性</span><span class="sxs-lookup"><span data-stu-id="318ea-129">Resource Governor Properties</span></span>  
 <span data-ttu-id="318ea-130">**分類函數名稱**</span><span class="sxs-lookup"><span data-stu-id="318ea-130">**Classifier function name**</span></span>  
 <span data-ttu-id="318ea-131">從清單中選取以指定分類函數。</span><span class="sxs-lookup"><span data-stu-id="318ea-131">Specify the classifier function by selecting from the list.</span></span>  
  
 <span data-ttu-id="318ea-132">**啟用資源管理員**</span><span class="sxs-lookup"><span data-stu-id="318ea-132">**Enable Resource Governor**</span></span>  
 <span data-ttu-id="318ea-133">以選取或清除核取方塊的方式，啟用或停用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="318ea-133">Enable or disable Resource Governor by selecting or clearing the check box.</span></span>  
  
 <span data-ttu-id="318ea-134">**資源集區**</span><span class="sxs-lookup"><span data-stu-id="318ea-134">**Resource pools**</span></span>  
 <span data-ttu-id="318ea-135">使用提供的方格，建立或變更資源集區組態。</span><span class="sxs-lookup"><span data-stu-id="318ea-135">Create or change resource pool configuration by using the grid that is provided.</span></span> <span data-ttu-id="318ea-136">此方格會填入預先定義的內部與預設集區的資訊。</span><span class="sxs-lookup"><span data-stu-id="318ea-136">This grid is populated with information for the predefined internal and default pools.</span></span> <span data-ttu-id="318ea-137">以按一下集區資料列的第一個資料行的方式，選取要進行作業的集區。</span><span class="sxs-lookup"><span data-stu-id="318ea-137">Select a pool to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="318ea-138">若要建立新的資源集區，請按一下前面有星號 ( **&#42;** ) 的資料列。</span><span class="sxs-lookup"><span data-stu-id="318ea-138">To create a new resource pool, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="318ea-139">**名稱**</span><span class="sxs-lookup"><span data-stu-id="318ea-139">**Name**</span></span>  
 <span data-ttu-id="318ea-140">指定資源集區的名稱。</span><span class="sxs-lookup"><span data-stu-id="318ea-140">Specify the name of the resource pool.</span></span>  
  
 <span data-ttu-id="318ea-141">**最小 CPU %**</span><span class="sxs-lookup"><span data-stu-id="318ea-141">**Minimum CPU %**</span></span>  
 <span data-ttu-id="318ea-142">當 CPU 出現瓶頸時，為在資源集區中的所有要求，指定保證平均 CPU 頻寬使用量。</span><span class="sxs-lookup"><span data-stu-id="318ea-142">Specify the guaranteed average CPU bandwidth for all requests in the resource pool when there is CPU contention.</span></span> <span data-ttu-id="318ea-143">範圍是 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="318ea-143">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="318ea-144">**最大 CPU %**</span><span class="sxs-lookup"><span data-stu-id="318ea-144">**Maximum CPU %**</span></span>  
 <span data-ttu-id="318ea-145">當發生 CPU 競爭時，指定所有要求在此資源集區中將會接收的最大平均 CPU 頻寬。</span><span class="sxs-lookup"><span data-stu-id="318ea-145">Specify the maximum average CPU bandwidth that all requests in this resource pool will receive when there is CPU contention.</span></span> <span data-ttu-id="318ea-146">範圍是 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="318ea-146">Range is 0 to 100.</span></span> <span data-ttu-id="318ea-147">預設設定為 100。</span><span class="sxs-lookup"><span data-stu-id="318ea-147">The default setting is 100.</span></span>  
  
 <span data-ttu-id="318ea-148">**最小記憶體 %**</span><span class="sxs-lookup"><span data-stu-id="318ea-148">**Minimum Memory %**</span></span>  
 <span data-ttu-id="318ea-149">指定為此資源集區所保留的最小記憶體數量 (不與其他資源集區共享)。</span><span class="sxs-lookup"><span data-stu-id="318ea-149">Specify the minimum amount of memory reserved for this resource pool that can not be shared with other resource pools.</span></span> <span data-ttu-id="318ea-150">範圍是 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="318ea-150">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="318ea-151">**最大記憶體 %**</span><span class="sxs-lookup"><span data-stu-id="318ea-151">**Maximum Memory %**</span></span>  
 <span data-ttu-id="318ea-152">指定在此資源集區中，可供要求所用的伺服器記憶體總量。</span><span class="sxs-lookup"><span data-stu-id="318ea-152">Specify the total server memory that can be used by requests in this resource pool.</span></span> <span data-ttu-id="318ea-153">範圍是 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="318ea-153">Range is 0 to 100.</span></span> <span data-ttu-id="318ea-154">預設設定為 100。</span><span class="sxs-lookup"><span data-stu-id="318ea-154">The default setting is 100.</span></span>  
  
 <span data-ttu-id="318ea-155">如需詳細資訊，請參閱[&#40;transact-sql&#41;建立資源集](/sql/t-sql/statements/create-resource-pool-transact-sql)區。</span><span class="sxs-lookup"><span data-stu-id="318ea-155">For more information, see [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql).</span></span>  
  
 <span data-ttu-id="318ea-156">**資源集區的工作負載群組**</span><span class="sxs-lookup"><span data-stu-id="318ea-156">**Workload groups for resource pool**</span></span>  
 <span data-ttu-id="318ea-157">使用提供的方格，建立或變更工作負載群組的組態。</span><span class="sxs-lookup"><span data-stu-id="318ea-157">Create or change the workload group configuration by using the grid that is provided.</span></span> <span data-ttu-id="318ea-158">此方格會填入預先定義的內部與預設群組的資訊。</span><span class="sxs-lookup"><span data-stu-id="318ea-158">This grid is populated with information for the predefined internal and default groups.</span></span> <span data-ttu-id="318ea-159">按一下集區資料列的第一個資料行，選取要進行作業的群組。</span><span class="sxs-lookup"><span data-stu-id="318ea-159">Select a group to work with by clicking the first column in the row for the pool.</span></span> <span data-ttu-id="318ea-160">若要建立新的工作負載群組，請按一下前面有星號 ( **&#42;** ) 的資料列。</span><span class="sxs-lookup"><span data-stu-id="318ea-160">To create a new workload group, click the row that is prefixed by the asterisk (**&#42;**).</span></span>  
  
 <span data-ttu-id="318ea-161">**名稱**</span><span class="sxs-lookup"><span data-stu-id="318ea-161">**Name**</span></span>  
 <span data-ttu-id="318ea-162">指定工作負載群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="318ea-162">Specify the name of the workload group.</span></span>  
  
 <span data-ttu-id="318ea-163">**重要性**</span><span class="sxs-lookup"><span data-stu-id="318ea-163">**Importance**</span></span>  
 <span data-ttu-id="318ea-164">指定在工作負載群組中的要求的相對重要性。</span><span class="sxs-lookup"><span data-stu-id="318ea-164">Specify the relative importance of a request in the workload group.</span></span> <span data-ttu-id="318ea-165">可用的設定為「低」、「中」和「高」。</span><span class="sxs-lookup"><span data-stu-id="318ea-165">Available settings are Low, Medium, and High.</span></span>  
  
 <span data-ttu-id="318ea-166">**最大要求**</span><span class="sxs-lookup"><span data-stu-id="318ea-166">**Maximum Requests**</span></span>  
 <span data-ttu-id="318ea-167">指定在工作負載群組中可允許執行的最大同時要求數。</span><span class="sxs-lookup"><span data-stu-id="318ea-167">Specify the maximum number of simultaneous requests that are allowed to execute in the workload group.</span></span> <span data-ttu-id="318ea-168">必須是 0 或正整數。</span><span class="sxs-lookup"><span data-stu-id="318ea-168">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="318ea-169">**CPU 時間 (秒)**</span><span class="sxs-lookup"><span data-stu-id="318ea-169">**CPU Time (sec)**</span></span>  
 <span data-ttu-id="318ea-170">指定一個要求所能使用的最大 CPU 時間量。</span><span class="sxs-lookup"><span data-stu-id="318ea-170">Specify the maximum amount of CPU time that a request can use.</span></span> <span data-ttu-id="318ea-171">必須是 0 或正整數。</span><span class="sxs-lookup"><span data-stu-id="318ea-171">Must be 0 or a positive integer.</span></span> <span data-ttu-id="318ea-172">如果為 0，時間是無限制。</span><span class="sxs-lookup"><span data-stu-id="318ea-172">If 0, the time is unlimited.</span></span>  
  
 <span data-ttu-id="318ea-173">**記憶體授權 %**</span><span class="sxs-lookup"><span data-stu-id="318ea-173">**Memory Grant %**</span></span>  
 <span data-ttu-id="318ea-174">指定單一要求可由集區中獲取的記憶體最大數量。</span><span class="sxs-lookup"><span data-stu-id="318ea-174">Specify the maximum amount of memory that a single request can take from the pool.</span></span> <span data-ttu-id="318ea-175">範圍是 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="318ea-175">Range is 0 to 100.</span></span>  
  
 <span data-ttu-id="318ea-176">**授與逾時 (秒)**</span><span class="sxs-lookup"><span data-stu-id="318ea-176">**Grant Time-out (sec)**</span></span>  
 <span data-ttu-id="318ea-177">指定在查詢失敗前，一個查詢能夠等待可用資源的最大時間。</span><span class="sxs-lookup"><span data-stu-id="318ea-177">Specify the maximum time that a query can wait for a resource to become available before the query fails.</span></span> <span data-ttu-id="318ea-178">必須是 0 或正整數。</span><span class="sxs-lookup"><span data-stu-id="318ea-178">Must be 0 or a positive integer.</span></span>  
  
 <span data-ttu-id="318ea-179">**平行處理原則的程度**</span><span class="sxs-lookup"><span data-stu-id="318ea-179">**Degree of Parallelism**</span></span>  
 <span data-ttu-id="318ea-180">為平行要求指定最大平行程度 (DOP)。</span><span class="sxs-lookup"><span data-stu-id="318ea-180">Specify the maximum degree of parallelism (DOP) for parallel requests.</span></span> <span data-ttu-id="318ea-181">範圍是 0 到 64。</span><span class="sxs-lookup"><span data-stu-id="318ea-181">Range is 0 to 64.</span></span>  
  
 <span data-ttu-id="318ea-182">如需詳細資訊，請參閱 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) (建立可用性群組 (Transact-SQL))。</span><span class="sxs-lookup"><span data-stu-id="318ea-182">For more information, see [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql).</span></span>  
  
## <a name="view-resource-governor-properties-by-using-transact-sql"></a><span data-ttu-id="318ea-183">使用 Transact-SQL 檢視資源管理員屬性</span><span class="sxs-lookup"><span data-stu-id="318ea-183">View Resource Governor Properties by Using Transact-SQL</span></span>  
 <span data-ttu-id="318ea-184">**使用 Transact-SQL 檢視資源管理員屬性**</span><span class="sxs-lookup"><span data-stu-id="318ea-184">**View resource governor properties by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="318ea-185">若要檢視 Resource Governor 實體的定義，請使用 [Resource Governor 目錄檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="318ea-185">To view the definitions of resource governor entities, use the [Resource Governor Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql).</span></span>  
  
2.  <span data-ttu-id="318ea-186">若要檢視 Resource Governor 實體的目前組態，請使用 [Resource Governor 相關的動態管理檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="318ea-186">To view the current configuration of resource governor entities, use the [Resource Governor Related Dynamic Management Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="318ea-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="318ea-187">See Also</span></span>  
 <span data-ttu-id="318ea-188">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="318ea-188">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="318ea-189">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="318ea-189">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="318ea-190">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="318ea-190">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="318ea-191">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="318ea-191">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 [<span data-ttu-id="318ea-192">資源管理員分類函數</span><span class="sxs-lookup"><span data-stu-id="318ea-192">Resource Governor Classifier Function</span></span>](resource-governor-classifier-function.md)  
  
  
