---
title: 快取共用資料集 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4acb1bbe-1c04-4979-b893-dc1b1c5039b6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b08149b075ae3fd267baf2dad0ca342457958c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597615"
---
# <a name="cache-shared-datasets-ssrs"></a><span data-ttu-id="7c8bf-102">快取共用資料集 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7c8bf-102">Cache Shared Datasets (SSRS)</span></span>
  <span data-ttu-id="7c8bf-103">共用資料集的查詢結果可以複製到快取，以便為多個報表提供一致的資料，並改善資料集查詢的回應時間。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-103">Query results for a shared dataset can be copied to a cache to provide consistent data for multiple reports and to improve response time for the dataset query.</span></span> <span data-ttu-id="7c8bf-104">跟報表一樣，您可以設定共用資料集在第一次使用時或指定排程進行快取。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-104">Like reports, you can configure a shared dataset to be cached on first use or by specifying a schedule.</span></span>  
  
 <span data-ttu-id="7c8bf-105">共用資料集可以包含在多個報表中，或做為元件定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-105">A shared dataset can be included in multiple reports or as part of component definitions.</span></span> <span data-ttu-id="7c8bf-106">您可以透過快取共用資料集，為所有使用該資料集的報表提供一致的資料集，而且也減少資料集查詢依外部資料來源執行的次數。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-106">By caching the shared dataset, you provide a consistent set of data for all reports that use it, and also reduce the number of times that the dataset query runs against the external data source.</span></span>  
  
 <span data-ttu-id="7c8bf-107">下列清單提供要快取共用資料集的範例：</span><span class="sxs-lookup"><span data-stu-id="7c8bf-107">The following list provides examples of when to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="7c8bf-108">查詢需要耗費大量時間來執行。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-108">The query takes a substantial amount of time to run.</span></span>  
  
-   <span data-ttu-id="7c8bf-109">查詢使用參數，但一般來說，參數組合的數目很小。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-109">The query takes parameters, but most of the time, the number of parameter combinations is small.</span></span> <span data-ttu-id="7c8bf-110">每個組合都會建立快取的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-110">Each combination creates cached query results.</span></span>  
  
-   <span data-ttu-id="7c8bf-111">查詢以天、週或月在可預測的時間執行。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-111">The query runs at predictable times of the day, week, or month.</span></span>  
  
-   <span data-ttu-id="7c8bf-112">由於在透過電子郵件傳遞的報表中參考共用資料集而執行查詢，在該報表中很可能會有大批人員在短時間內按一下該連結。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-112">The query runs as the result of a shared dataset reference in a report that is delivered via e-mail, where a large number of people are likely to click the link in a short span of time.</span></span>  
  
-   <span data-ttu-id="7c8bf-113">下列清單提供不要快取共用資料集的範例：</span><span class="sxs-lookup"><span data-stu-id="7c8bf-113">The following list provides examples of when not to cache a shared dataset:</span></span>  
  
-   <span data-ttu-id="7c8bf-114">查詢結果必須永遠都包含最新的資料。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-114">The query results must always include the most recent data.</span></span>  
  
-   <span data-ttu-id="7c8bf-115">查詢迅速執行。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-115">The query runs quickly.</span></span>  
  
-   <span data-ttu-id="7c8bf-116">查詢不常執行。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-116">The query runs infrequently.</span></span>  
  
-   <span data-ttu-id="7c8bf-117">查詢使用參數，參數組合的數目很大，而所有組合的可能性都差不多。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-117">The query takes parameters, the number of parameter combinations is large, and no combination is more likely than another.</span></span>  
  
-   <span data-ttu-id="7c8bf-118">共用資料集的資料來源基礎具有提示認證或 Windows 整合式認證。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-118">The data source that the shared dataset is based on has Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="7c8bf-119">共用資料集篩選或查詢包含參考全域集合使用者的運算式。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-119">The shared dataset filter or the query contains an expression with a reference to the global collection User.</span></span>  
  
 <span data-ttu-id="7c8bf-120">如果使用者所選擇的報表參數值與快取結果集所指定的預設值不同，資料集查詢會主動執行，該查詢不會使用快取結果。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-120">If a user chooses report parameter values that differ from the default values that are specified for the cached result set, the dataset query runs actively and the cached results are not used for that query.</span></span>  
  
## <a name="caching-shared-datasets"></a><span data-ttu-id="7c8bf-121">快取共用資料集</span><span class="sxs-lookup"><span data-stu-id="7c8bf-121">Caching Shared Datasets</span></span>  
 <span data-ttu-id="7c8bf-122">若要啟用共用資料集快取，您必須在共用資料集上選取快取選項。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-122">To enable caching for a shared dataset, you must select the cache option on the shared dataset.</span></span> <span data-ttu-id="7c8bf-123">啟用快取之後，共用資料集的查詢結果會在第一次使用時複製到快取中。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-123">After caching is enabled, the query results for a shared dataset are copied to the cache on first use.</span></span> <span data-ttu-id="7c8bf-124">如果共用資料集具有參數，參數的每個組合都會在快取中建立新項目。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-124">If the shared dataset has parameters, each combination of parameters creates a new entry in the cache.</span></span>  
  
 <span data-ttu-id="7c8bf-125">特定參數組合的查詢結果在快取中時，啟動進行處理的所有報表，以及包含具有這些參數值之共用資料集參考的所有報表，都會使用快取的資料。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-125">While the query results for a specific parameter combination are in the cache, each report that is launched for processing and that includes a reference to the shared dataset with those parameter values will use the cached data.</span></span>  
  
 <span data-ttu-id="7c8bf-126">您可以指定資料要在快取中保存到過期的時間。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-126">You can specify how long to keep data in the cache before it expires.</span></span> <span data-ttu-id="7c8bf-127">如需詳細資訊，請參閱[快取頁面、共用資料集 &#40;報表管理員&#41;](../caching-page-shared-datasets-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-127">For more information, see [Caching Page, Shared Datasets &#40;Report Manager&#41;](../caching-page-shared-datasets-report-manager.md).</span></span>  
  
## <a name="preloading-the-cache"></a><span data-ttu-id="7c8bf-128">預先載入快取</span><span class="sxs-lookup"><span data-stu-id="7c8bf-128">Preloading the Cache</span></span>  
 <span data-ttu-id="7c8bf-129">您可以透過建立快取重新整理計劃，以預先載入快取。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-129">You can preload the cache by creating a cache refresh plan.</span></span> <span data-ttu-id="7c8bf-130">針對重新整理計劃，您可以使用項目特定排程或共用排程，指定重新整理的頻率。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-130">With a refresh plan, you can specify how often to refresh the cache by using an item-specific schedule or a shared schedule.</span></span> <span data-ttu-id="7c8bf-131">若要避免產生多個相同項目的快取，您所指定的排程應該有足夠時間來處理外部資料來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-131">To avoid multiple cache entries for the same item, the schedule that you specify should allow enough time for query processing on the external data source.</span></span> <span data-ttu-id="7c8bf-132">例如，如果執行查詢需要 20 分鐘，則重新整理排程應該超過 20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-132">For example, if the query takes 20 minutes to run, the refresh schedule should be greater than 20 minutes.</span></span> <span data-ttu-id="7c8bf-133">如需詳細資訊，請參閱 [Schedules](../subscriptions/schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-133">For more information, see [Schedules](../subscriptions/schedules.md).</span></span>  
  
 <span data-ttu-id="7c8bf-134">若要建立共用資料集的快取重新整理計劃，則應具備下列條件。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-134">To create a cache refresh plan for a shared dataset, the following conditions apply.</span></span>  
  
-   <span data-ttu-id="7c8bf-135">共用資料集必須已啟用快取。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-135">The shared dataset must be enabled for caching.</span></span>  
  
-   <span data-ttu-id="7c8bf-136">共用資料集的共用資料來源基礎不能使用提示認證或 Windows 整合式認證。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-136">The shared data source that the shared dataset depends on cannot use Prompt or Windows Integrated credentials.</span></span>  
  
-   <span data-ttu-id="7c8bf-137">如果共用資料集具有參數，所有未標示為唯讀的參數都必須指定靜態的預設值。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-137">If the shared dataset has parameters, you must specify static default values for each parameter that is not marked read-only.</span></span> <span data-ttu-id="7c8bf-138">唯讀參數一律都使用預設值。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-138">Read-only parameters will always use the default value.</span></span> <span data-ttu-id="7c8bf-139">若要為多個參數組合快取共用資料集，必須分別為每個值組合建立不同的快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-139">To cache a shared dataset for multiple combinations of parameters, you must create a separate cache refresh plan for each combination of values.</span></span> <span data-ttu-id="7c8bf-140">參數不能包含其他資料集的參考。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-140">Parameters cannot contain references to other datasets.</span></span>  
  
-   <span data-ttu-id="7c8bf-141">每個快取重新整理計劃都只與一個共用資料集或報表相關聯。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-141">Each cache refresh plan is associated with only one shared dataset or report.</span></span>  
  
-   <span data-ttu-id="7c8bf-142">您必須在共用資料集上擁有 ReadPolicy 和 UpdatePolicy 權限。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-142">You must have ReadPolicy and UpdatePolicy permissions on the shared dataset.</span></span>  
  
 <span data-ttu-id="7c8bf-143">快取重新整理計劃適用於共用資料集及報表。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-143">Cache refresh plans apply to both shared datasets and reports.</span></span> <span data-ttu-id="7c8bf-144">如需詳細資訊，請參閱[快取重新整理選項 &#40;報表管理員&#41;](../cache-refresh-options-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-144">For more information, see [Cache Refresh Options &#40;Report Manager&#41;](../cache-refresh-options-report-manager.md).</span></span>  
  
## <a name="conditions-that-cause-cache-expiration"></a><span data-ttu-id="7c8bf-145">造成快取逾期的條件</span><span class="sxs-lookup"><span data-stu-id="7c8bf-145">Conditions that Cause Cache Expiration</span></span>  
 <span data-ttu-id="7c8bf-146">下列條件可能會導致共用資料集快取無效。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-146">The following conditions can cause a shared dataset cache to become not valid.</span></span>  
  
-   <span data-ttu-id="7c8bf-147">排程條件過期。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-147">A schedule condition expires.</span></span> <span data-ttu-id="7c8bf-148">發生快取逾時或已到過期時間。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-148">The cache times out or the expiration time occurs.</span></span>  
  
-   <span data-ttu-id="7c8bf-149">共用排程已刪除。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-149">A shared schedule is deleted.</span></span>  
  
-   <span data-ttu-id="7c8bf-150">變更為共用排程。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-150">Changes to a shared schedule.</span></span> <span data-ttu-id="7c8bf-151">共用排程可以暫停，這也會影響快取過期時間。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-151">Shared schedules can be paused, which also affects when a cache expires.</span></span>  
  
-   <span data-ttu-id="7c8bf-152">共用資料集的查詢定義已變更。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-152">The query definition for the shared dataset changes.</span></span>  
  
-   <span data-ttu-id="7c8bf-153">共用資料集之共用資料來源基礎的認證已變更。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-153">The credentials for the shared data source that the shared dataset depends on change.</span></span>  
  
-   <span data-ttu-id="7c8bf-154">共用資料集的快取選項已變更。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-154">The cache options for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="7c8bf-155">共用資料集的唯讀參數預設值已變更。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-155">The default values for read-only parameters for the shared dataset change.</span></span>  
  
-   <span data-ttu-id="7c8bf-156">屬於共用資料集定義一部分的篩選已變更。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-156">The filters that are part of the shared dataset definition change.</span></span>  
  
-   <span data-ttu-id="7c8bf-157">共用資料集已從報表伺服器中刪除。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-157">The shared dataset is deleted from the report server.</span></span> <span data-ttu-id="7c8bf-158">刪除共用資料集時，相關聯的快取複本和快取重新整理計劃也會一併刪除。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-158">When a shared dataset is deleted, associated cached copies and cache refresh plans are also deleted.</span></span>  
  
 <span data-ttu-id="7c8bf-159">共用資料集的快取重新整理計劃更新不會影響已處理的報表。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-159">Updates to cache refresh plans for shared datasets do not affect reports that are already being processed.</span></span> <span data-ttu-id="7c8bf-160">更新快取重新整理計劃只會影響未來啟動而參考共用資料集的報表。</span><span class="sxs-lookup"><span data-stu-id="7c8bf-160">Updating a cache refresh plan affects only future launches of reports that reference the shared dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8bf-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c8bf-161">See Also</span></span>  
 [<span data-ttu-id="7c8bf-162">管理共用資料集</span><span class="sxs-lookup"><span data-stu-id="7c8bf-162">Manage Shared Datasets</span></span>](../report-data/manage-shared-datasets.md)  
  
  
