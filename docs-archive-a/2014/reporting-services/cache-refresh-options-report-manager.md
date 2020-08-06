---
title: 快取重新整理選項 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 83b2ef4396c774f3ac344704756cd1c7e90d4e04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595814"
---
# <a name="cache-refresh-options-report-manager"></a><span data-ttu-id="152fd-102">快取重新整理選項 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="152fd-102">Cache Refresh Options (Report Manager)</span></span>
  <span data-ttu-id="152fd-103">使用 [快取重新整理] 選項頁面來建立排程，以供預先載入含報表或共用資料集資料暫存副本的快取。</span><span class="sxs-lookup"><span data-stu-id="152fd-103">Use the Cache Refresh options page to create schedules for preloading the cache with temporary copies of data for a report or for a shared dataset.</span></span> <span data-ttu-id="152fd-104">重新整理計劃包括排程和選項，可指定或覆寫參數的值。</span><span class="sxs-lookup"><span data-stu-id="152fd-104">A refresh plan includes a schedule and the option to specify or override values for parameters.</span></span> <span data-ttu-id="152fd-105">您不能針對共用資料集，覆寫標示為唯讀的參數值。</span><span class="sxs-lookup"><span data-stu-id="152fd-105">For a shared dataset, you cannot override values for parameters that are marked read-only.</span></span> <span data-ttu-id="152fd-106">您可以建立並使用多個重新整理計劃做為重新整理選項頁面的一部分。</span><span class="sxs-lookup"><span data-stu-id="152fd-106">You can create and use more than one refresh plan as part of the refresh options page.</span></span>  
  
 <span data-ttu-id="152fd-107">可讓您加入、刪除、變更及檢視快取重新整理計劃之相關報表和共用資料集的預設角色指派有：[內容管理員]、[我的報表] 和 [發行者]。</span><span class="sxs-lookup"><span data-stu-id="152fd-107">Default role assignments that enable you to add, delete, change, and view related reports and shared datasets for cache refresh plans are Content Manager, My Reports, and Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="152fd-108">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="152fd-108">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="152fd-109">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="152fd-109">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="to-open-the-cache-refresh-plan-properties-page-for-a-report-or-shared-dataset"></a><span data-ttu-id="152fd-110">開啟報表或共用資料集的快取重新整理計劃屬性頁</span><span class="sxs-lookup"><span data-stu-id="152fd-110">To open the Cache Refresh Plan properties page for a report or shared dataset</span></span>  
  
1.  <span data-ttu-id="152fd-111">開啟報表管理員，然後找出您想要設定快取重新整理計劃屬性的報表或共用資料集。</span><span class="sxs-lookup"><span data-stu-id="152fd-111">Open Report Manager, and locate the report or shared dataset for which you want to configure cache refresh plan properties.</span></span>  
  
2.  <span data-ttu-id="152fd-112">將滑鼠停留在報表或共用資料集上方，然後按下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="152fd-112">Hover over the report or shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="152fd-113">在下拉式清單中，按一下 **[管理]**，</span><span class="sxs-lookup"><span data-stu-id="152fd-113">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="152fd-114">[**一般屬性**] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="152fd-114">The **General properties** page opens.</span></span>  
  
4.  <span data-ttu-id="152fd-115">按一下 **[快取重新整理計劃]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="152fd-115">Click the **Cache Refresh Plan** tab.</span></span>  
  
5.  <span data-ttu-id="152fd-116">若要建立新的快取計劃，請按一下 **[新增快取重新整理計劃]**。</span><span class="sxs-lookup"><span data-stu-id="152fd-116">To create a new cache plan, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="152fd-117">您必須啟用並啟動 SQL Server Agent 服務來建立快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-117">You must enable and start the SQL Server Agent service to create a cache refresh plan.</span></span>  
  
6.  <span data-ttu-id="152fd-118">若要建立一份快取計劃，然後加以自訂，請按一下 **[從現有的新增]**。</span><span class="sxs-lookup"><span data-stu-id="152fd-118">To create a copy of a cache plan and then customize it, click **New from Existing**.</span></span>  
  
## <a name="cache-refresh-options"></a><span data-ttu-id="152fd-119">快取重新整理選項</span><span class="sxs-lookup"><span data-stu-id="152fd-119">Cache Refresh Options</span></span>  
 <span data-ttu-id="152fd-120">**刪除**</span><span class="sxs-lookup"><span data-stu-id="152fd-120">**Delete**</span></span>  
 <span data-ttu-id="152fd-121">刪除目前選取的所有重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-121">Deletes all of the currently selected refresh plans.</span></span>  
  
 <span data-ttu-id="152fd-122">**[從現有的新增]**</span><span class="sxs-lookup"><span data-stu-id="152fd-122">**New from existing**</span></span>  
 <span data-ttu-id="152fd-123">當只選取一個快取重新整理計劃時，會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="152fd-123">This option is enabled when one and only one cache refresh plan is selected.</span></span> <span data-ttu-id="152fd-124">這個選項會建立從原始計劃複製的新重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-124">This option will create a new refresh plan which is copied from the original plan.</span></span> <span data-ttu-id="152fd-125">[快取重新整理計劃] 頁面開啟時會預先填入所選取計劃的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="152fd-125">The cache refresh plan page opens pre-populated with details from the plan that was selected.</span></span> <span data-ttu-id="152fd-126">接著，您就可以修改重新整理計劃選項，然後使用新的描述儲存該計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-126">You can then modify the refresh plan options and save the plan with a new description.</span></span>  
  
 <span data-ttu-id="152fd-127">**[新增快取重新整理計劃]**</span><span class="sxs-lookup"><span data-stu-id="152fd-127">**New cache refresh plan**</span></span>  
 <span data-ttu-id="152fd-128">按一下可建立新的重新整理計劃，以用於目前的快取重新整理選項中。</span><span class="sxs-lookup"><span data-stu-id="152fd-128">Click to create a new refresh plan to be used in the current cache refresh options.</span></span>  
  
 <span data-ttu-id="152fd-129">**編輯**</span><span class="sxs-lookup"><span data-stu-id="152fd-129">**Edit**</span></span>  
 <span data-ttu-id="152fd-130">選取這個選項，以編輯目前的重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-130">Select this option to edit the current refresh plan.</span></span>  
  
## <a name="cache-refresh-plan-options"></a><span data-ttu-id="152fd-131">快取重新整理計劃選項</span><span class="sxs-lookup"><span data-stu-id="152fd-131">Cache Refresh Plan Options</span></span>  
 <span data-ttu-id="152fd-132">**說明**</span><span class="sxs-lookup"><span data-stu-id="152fd-132">**Description**</span></span>  
 <span data-ttu-id="152fd-133">指定快取重新整理計劃的描述。</span><span class="sxs-lookup"><span data-stu-id="152fd-133">Specify a description for the cache refresh plan.</span></span>  
  
 <span data-ttu-id="152fd-134">**項目特定排程**</span><span class="sxs-lookup"><span data-stu-id="152fd-134">**Item-specific schedule**</span></span>  
 <span data-ttu-id="152fd-135">選取此選項，可建立僅供此項目使用的排程。</span><span class="sxs-lookup"><span data-stu-id="152fd-135">Select this option to create a schedule that is used only by this item.</span></span>  
  
 <span data-ttu-id="152fd-136">**設定 [報告]**</span><span class="sxs-lookup"><span data-stu-id="152fd-136">**Configure**</span></span>  
 <span data-ttu-id="152fd-137">按一下即可開啟 [排程] 頁面，可用來指定頻率資訊。</span><span class="sxs-lookup"><span data-stu-id="152fd-137">Click to open the Schedule page, which is used to specify frequency information.</span></span>  
  
 <span data-ttu-id="152fd-138">如需詳細資訊，請參閱[新排程：編輯排程頁面 &#40;報表管理員&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="152fd-138">For more information, see [New Schedule: Edit Schedule Page &#40;Report Manager&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="152fd-139">**共用排程**</span><span class="sxs-lookup"><span data-stu-id="152fd-139">**Shared schedule**</span></span>  
 <span data-ttu-id="152fd-140">選取此選項，可選取現有的排程。</span><span class="sxs-lookup"><span data-stu-id="152fd-140">Select this option to select an existing schedule.</span></span>  
  
 <span data-ttu-id="152fd-141">如需詳細資訊，請參閱 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)。</span><span class="sxs-lookup"><span data-stu-id="152fd-141">For more information, see [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md).</span></span>  
  
 **@\<** *Parameter* **>**  
 <span data-ttu-id="152fd-142">指定參數值的其中一個組合。</span><span class="sxs-lookup"><span data-stu-id="152fd-142">Specify one combination of parameter values.</span></span> <span data-ttu-id="152fd-143">此區段只有在目前的資料集或報表具有參數時才會出現。</span><span class="sxs-lookup"><span data-stu-id="152fd-143">This section appears only if the current dataset or report has parameters.</span></span>  
  
 <span data-ttu-id="152fd-144">請參閱下一節中的 [指定參數](#Parameters) 。</span><span class="sxs-lookup"><span data-stu-id="152fd-144">See [Specifying Parameters](#Parameters) in the next section.</span></span>  
  
 <span data-ttu-id="152fd-145">**使用預設值**</span><span class="sxs-lookup"><span data-stu-id="152fd-145">**Use Default**</span></span>  
 <span data-ttu-id="152fd-146">選取此選項，可使用此參數的預先定義預設值。</span><span class="sxs-lookup"><span data-stu-id="152fd-146">Select this option to use the predefined default value for this parameter.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="152fd-147">指定參數</span><span class="sxs-lookup"><span data-stu-id="152fd-147">Specifying Parameters</span></span>  
 <span data-ttu-id="152fd-148">若要建立快取重新整理計劃，每個報表或共用資料集參數都必須有值。</span><span class="sxs-lookup"><span data-stu-id="152fd-148">To create a cache refresh plan, each report or shared dataset parameter must have a value.</span></span> <span data-ttu-id="152fd-149">如果報表或共用資料集項目並沒有在定義中指定預設值，您必須指定一個值。</span><span class="sxs-lookup"><span data-stu-id="152fd-149">If the report or shared dataset item does not have a default value specified in the definition, you must specify a value.</span></span> <span data-ttu-id="152fd-150">如果有預設值，就不需要在此提供值。</span><span class="sxs-lookup"><span data-stu-id="152fd-150">If a default value exists, you do not need to provide one here.</span></span> <span data-ttu-id="152fd-151">如果您提供了任何值，該值就會覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="152fd-151">If you do provide a value, the value overrides the default value.</span></span>  
  
 <span data-ttu-id="152fd-152">若要指定多個參數值組合，請分別為每個值組合建立快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-152">To specify multiple combinations of parameter values, create a separate cache refresh plan for each combination.</span></span>  
  
 <span data-ttu-id="152fd-153">對報表或共用資料集上的參數進行新增、變更及刪除都可能會影響快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-153">Additions, changes, and deletions made to parameters on a report or shared dataset can affect the cache refresh plan.</span></span> <span data-ttu-id="152fd-154">如果您加入含報表預設值的參數、移除參數，或變更共用資料集參數的資料類型或唯讀選項，變更會在下一次處理快取重新整理計劃時生效。</span><span class="sxs-lookup"><span data-stu-id="152fd-154">If you add a parameter with a default value for a report, remove a parameter, or change the data type or the read-only option for a shared dataset parameter, the changes take affect the next time the cache refresh plan is processed.</span></span>  
  
### <a name="shared-dataset-parameters"></a><span data-ttu-id="152fd-155">共用資料集參數</span><span class="sxs-lookup"><span data-stu-id="152fd-155">Shared Dataset Parameters</span></span>  
 <span data-ttu-id="152fd-156">就共用資料集而言，下列資訊是自共用資料集定義衍生而來：</span><span class="sxs-lookup"><span data-stu-id="152fd-156">For a shared dataset, the following information is derived from the shared dataset definition:</span></span>  
  
-   <span data-ttu-id="152fd-157">**名稱** ：指定查詢參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="152fd-157">**Name** Specifies the name of the query parameter.</span></span>  
  
-   <span data-ttu-id="152fd-158">**類型** ：指定查詢參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="152fd-158">**Type** Specifies the data type of the query parameter.</span></span> <span data-ttu-id="152fd-159">由於直到資料提供者處理資料集查詢之前，資料類型都屬未知，所以處理共用資料集之前無法進行資料類型驗證。</span><span class="sxs-lookup"><span data-stu-id="152fd-159">Because this data type is unknown until the data provider processes the dataset query, data type validation cannot occur until the shared dataset is processed.</span></span>  
  
-   <span data-ttu-id="152fd-160">**可為 Null** ：指定 NULL 是否為有效的值。</span><span class="sxs-lookup"><span data-stu-id="152fd-160">**Nullable** Specifies whether NULL is a valid value.</span></span>  
  
-   <span data-ttu-id="152fd-161">**唯讀** ：指定這個參數在共用資料集定義中是否標示為唯讀。</span><span class="sxs-lookup"><span data-stu-id="152fd-161">**ReadOnly** Specifies whether this parameter is marked read-only in the shared dataset definition.</span></span> <span data-ttu-id="152fd-162">唯讀參數不會顯示在快取重新整理選項的參數清單中，而且必須指定預設值做為共用資料集定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="152fd-162">Read only parameters do not appear in the parameter list for cache refresh options and must have a default specified as part of the shared dataset definition.</span></span>  
  
-   <span data-ttu-id="152fd-163">**預設值** ：已在共用資料集定義中指定的預設值。</span><span class="sxs-lookup"><span data-stu-id="152fd-163">**DefaultValues** Default values that have been specified in the shared dataset definition.</span></span> <span data-ttu-id="152fd-164">查詢參數可以是多重值。</span><span class="sxs-lookup"><span data-stu-id="152fd-164">Query parameters can be multivalued.</span></span> <span data-ttu-id="152fd-165">若要覆寫預設值，請在文字方塊提示區域中輸入新的值。</span><span class="sxs-lookup"><span data-stu-id="152fd-165">To override the default values, type new values in the text box prompt areas.</span></span>  
  
 <span data-ttu-id="152fd-166">如果共用資料集定義為參數指定 **[從查詢中忽略]** 選項，就不需要提供預設值。</span><span class="sxs-lookup"><span data-stu-id="152fd-166">If the shared dataset definition specifies the option **Omit from query** for a parameter, you do not need to provide a default value.</span></span> <span data-ttu-id="152fd-167">這個旗標表示查詢中不使用該資料集參數。</span><span class="sxs-lookup"><span data-stu-id="152fd-167">This flag indicates that the dataset parameter is not used in the query.</span></span> <span data-ttu-id="152fd-168">例如，參數顯示在共用資料集定義中，因為該參數是只用於資料集篩選中的報表參數。</span><span class="sxs-lookup"><span data-stu-id="152fd-168">For example, the parameter appears in the shared dataset definition because it is a report parameter that is used in the dataset filter only.</span></span>  
  
 <span data-ttu-id="152fd-169">若要檢視或變更資料集參數選項，您必須編輯共用資料集定義。</span><span class="sxs-lookup"><span data-stu-id="152fd-169">To view or change dataset parameter options, you must edit the shared dataset definition.</span></span> <span data-ttu-id="152fd-170">如需詳細資訊，請參閱 [Manage Shared Datasets](report-data/manage-shared-datasets.md)(管理共用資料集)。</span><span class="sxs-lookup"><span data-stu-id="152fd-170">For more information, see [Manage Shared Datasets](report-data/manage-shared-datasets.md).</span></span>  
  
### <a name="report-parameters"></a><span data-ttu-id="152fd-171">報表參數</span><span class="sxs-lookup"><span data-stu-id="152fd-171">Report Parameters</span></span>  
 <span data-ttu-id="152fd-172">依報表來說，每個參數值都必須有效，才能順利建立快取重新整理計劃。</span><span class="sxs-lookup"><span data-stu-id="152fd-172">For a report, each parameter value must be valid before you can successfully create a cache refresh plan.</span></span> <span data-ttu-id="152fd-173">您必須為每個報表參數輸入或選取預設值。</span><span class="sxs-lookup"><span data-stu-id="152fd-173">You must type or select a default value for each report parameter.</span></span> <span data-ttu-id="152fd-174">您所設定的值會覆寫在報表伺服器上為報表參數定義的預設值。</span><span class="sxs-lookup"><span data-stu-id="152fd-174">The value that you set overrides the default value that is defined for the report parameter on the report server.</span></span>  
  
 <span data-ttu-id="152fd-175">參數必須符合報表伺服器上參數屬性中指定的需求。</span><span class="sxs-lookup"><span data-stu-id="152fd-175">Parameters must conform to the requirements specified in the parameter properties on the report server.</span></span> <span data-ttu-id="152fd-176">例如，如果報表參數的屬性 AllowBlank 是 false，則空字串不是有效的值。</span><span class="sxs-lookup"><span data-stu-id="152fd-176">For example, if the property AllowBlank is false for a report parameter, an empty string is not a valid value.</span></span>  
  
 <span data-ttu-id="152fd-177">若要檢視或變更報表參數選項，必須在報表中編輯報表參數，或是另外在報表伺服器上獨立編輯。</span><span class="sxs-lookup"><span data-stu-id="152fd-177">To view or change report parameter options, you must edit the report parameters in the report, or independently, on the report server.</span></span> <span data-ttu-id="152fd-178">如需詳細資訊，請參閱[&#40;報表產生器和 SSRS&#41;的報表參數概念](report-design/report-parameters-concepts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="152fd-178">For more information, see [Report Parameters Concept &#40;Report Builder and SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md).</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-inactive"></a><span data-ttu-id="152fd-179">導致快取重新整理計劃成為非使用狀態的條件</span><span class="sxs-lookup"><span data-stu-id="152fd-179">Conditions that Cause a Cache Refresh Plan to be Inactive</span></span>  
 <span data-ttu-id="152fd-180">下列條件可能會導致共用資料集或報表快取重新整理計畫變成非使用狀態。</span><span class="sxs-lookup"><span data-stu-id="152fd-180">The following conditions can cause a shared dataset or report cache refresh plan to become inactive.</span></span>  
  
-   <span data-ttu-id="152fd-181">共用資料集快取或報表快取選項會停用。</span><span class="sxs-lookup"><span data-stu-id="152fd-181">The shared dataset cache or report cache option is disabled.</span></span>  
  
-   <span data-ttu-id="152fd-182">必要的參數值為未定義、無效或遺漏。</span><span class="sxs-lookup"><span data-stu-id="152fd-182">The required parameter values are not defined, not valid, or missing.</span></span> <span data-ttu-id="152fd-183">報表的所有查詢都必須有效，報表才會進行處理。</span><span class="sxs-lookup"><span data-stu-id="152fd-183">All queries for a report must be valid before the report will be processed.</span></span> <span data-ttu-id="152fd-184">對於具有子報表的報表，會先處理所有資料集查詢 (包括子報表的資料集在內)。</span><span class="sxs-lookup"><span data-stu-id="152fd-184">For a report that has subreports, all dataset queries, including datasets for the subreport, are processed first.</span></span> <span data-ttu-id="152fd-185">如果無法順利處理任何資料集，報表就無法執行。</span><span class="sxs-lookup"><span data-stu-id="152fd-185">If any dataset cannot be successfully processed, the report cannot run.</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-reactivated"></a><span data-ttu-id="152fd-186">使得快取重新整理計劃重新啟動的條件</span><span class="sxs-lookup"><span data-stu-id="152fd-186">Conditions that Cause a Cache Refresh Plan to be Reactivated</span></span>  
 <span data-ttu-id="152fd-187">計劃處於非使用狀態後，請執行下列其中一項以觸發快取重新整理計劃的評估程序：</span><span class="sxs-lookup"><span data-stu-id="152fd-187">After a plan is inactive, do one of the following to trigger evaluation of a cache refresh plan:</span></span>  
  
-   <span data-ttu-id="152fd-188">變更計劃的選項。</span><span class="sxs-lookup"><span data-stu-id="152fd-188">Change an option for the plan.</span></span>  
  
-   <span data-ttu-id="152fd-189">啟用與重新整理計劃相關聯的共用資料集或報表快取。</span><span class="sxs-lookup"><span data-stu-id="152fd-189">Enable caching for a shared dataset or report that is associated with the refresh plan.</span></span>  
  
-   <span data-ttu-id="152fd-190">為與重新整理計劃關聯的資料集查詢參數清除或選取唯讀選項，然後將新的定義儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="152fd-190">Clear or select the read-only option for a dataset query parameter associated with the refresh plan, and then save the new definition to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152fd-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="152fd-191">See Also</span></span>  
 <span data-ttu-id="152fd-192">[專案層級工作](security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="152fd-192">[Item-Level Tasks](security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="152fd-193">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="152fd-193">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="152fd-194">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="152fd-194">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="152fd-195">[快取多個報表 &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="152fd-195">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="152fd-196">管理共用資料集</span><span class="sxs-lookup"><span data-stu-id="152fd-196">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
  
