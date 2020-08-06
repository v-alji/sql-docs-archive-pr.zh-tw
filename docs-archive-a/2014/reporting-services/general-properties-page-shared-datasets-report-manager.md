---
title: 一般屬性頁面、共用資料集 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10798e41-24c3-4e69-893b-7ee6af7fc958
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 31825e61cb40505e9167cc2b930a5b79e5aaa013
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607266"
---
# <a name="general-properties-page-shared-datasets-report-manager"></a><span data-ttu-id="43709-102">一般屬性頁面、共用資料集 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="43709-102">General Properties Page, Shared Datasets (Report Manager)</span></span>
  <span data-ttu-id="43709-103">使用 [共用資料集] 頁面，即可檢視及管理共用資料集項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="43709-103">Use the Shared Dataset page to view and manage properties for a shared dataset item.</span></span>  
  
 <span data-ttu-id="43709-104">您無法從報表管理員檢視或變更共用資料集定義，包括查詢在內。</span><span class="sxs-lookup"><span data-stu-id="43709-104">From Report Manager, you cannot view or change the shared dataset definition, including the query.</span></span> <span data-ttu-id="43709-105">若要變更定義，您必須使用撰寫工具來開啟及修改定義，然後將該定義儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="43709-105">To change the definition, you must use an authoring tool to open and modify the definition and then save it to the report server.</span></span>  
  
 <span data-ttu-id="43709-106">您可以使用共用資料集，從報表、元件及其他使用該資料集的目錄項目，個別管理資料集的設定。</span><span class="sxs-lookup"><span data-stu-id="43709-106">With a shared dataset, you can manage the settings for a dataset separately from reports, components, and other catalog items that use it.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="43709-107">導覽</span><span class="sxs-lookup"><span data-stu-id="43709-107">Navigation</span></span>  
 <span data-ttu-id="43709-108">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="43709-108">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-shared-dataset-properties-page-for-a-shared-dataset"></a><span data-ttu-id="43709-109">開啟共用資料集的共用資料集屬性頁面</span><span class="sxs-lookup"><span data-stu-id="43709-109">To open the Shared Dataset properties page for a shared dataset</span></span>  
  
1.  <span data-ttu-id="43709-110">開啟報表管理員，然後找出您想要設定屬性的共用資料集。</span><span class="sxs-lookup"><span data-stu-id="43709-110">Open Report Manager, and locate shared dataset for which you want to configure properties.</span></span>  
  
2.  <span data-ttu-id="43709-111">將滑鼠停留在共用資料集上方，然後按下拉式箭號。</span><span class="sxs-lookup"><span data-stu-id="43709-111">Hover over the shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="43709-112">在下拉式清單中，按一下 **[管理]**，</span><span class="sxs-lookup"><span data-stu-id="43709-112">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="43709-113">就會開啟 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="43709-113">The General properties page opens.</span></span>  
  
## <a name="options"></a><span data-ttu-id="43709-114">選項。</span><span class="sxs-lookup"><span data-stu-id="43709-114">Options</span></span>  
 <span data-ttu-id="43709-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="43709-115">**Name**</span></span>  
 <span data-ttu-id="43709-116">輸入可用來識別報表伺服器資料夾階層中項目的共用資料集名稱。</span><span class="sxs-lookup"><span data-stu-id="43709-116">Type a name for the shared dataset that is used to identify the item within the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="43709-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="43709-117">**Description**</span></span>  
 <span data-ttu-id="43709-118">提供有關共用資料集的資訊。</span><span class="sxs-lookup"><span data-stu-id="43709-118">Provide information about the shared dataset.</span></span> <span data-ttu-id="43709-119">此描述會顯示在 [內容] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="43709-119">This description appears on the Contents page.</span></span>  
  
 <span data-ttu-id="43709-120">**在清單檢視中隱藏**</span><span class="sxs-lookup"><span data-stu-id="43709-120">**Hide in list view**</span></span>  
 <span data-ttu-id="43709-121">隱藏共用資料集，避免在報表管理員中使用清單檢視模式的使用者看見。</span><span class="sxs-lookup"><span data-stu-id="43709-121">Hide the shared dataset from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="43709-122">清單檢視模式是瀏覽報表伺服器資料夾階層時的預設檢視格式。</span><span class="sxs-lookup"><span data-stu-id="43709-122">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="43709-123">在清單檢視中，項目名稱和描述會跨頁排列。</span><span class="sxs-lookup"><span data-stu-id="43709-123">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="43709-124">替代格式是詳細資料檢視。</span><span class="sxs-lookup"><span data-stu-id="43709-124">The alternative format is details view.</span></span> <span data-ttu-id="43709-125">詳細資料檢視會省略描述，但會包括項目的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="43709-125">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="43709-126">雖然在清單檢視中可以隱藏項目，但在詳細資料檢視中則不行。</span><span class="sxs-lookup"><span data-stu-id="43709-126">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="43709-127">如果想要限制項目的存取，您必須建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="43709-127">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="43709-128">**查詢執行逾時**</span><span class="sxs-lookup"><span data-stu-id="43709-128">**Query execution timeout**</span></span>  
 <span data-ttu-id="43709-129">輸入查詢超時之前的秒數。如果為0，則查詢不會超時。</span><span class="sxs-lookup"><span data-stu-id="43709-129">Type the number of seconds until the query times out. If it is 0, the query does not time out.</span></span>  
  
 <span data-ttu-id="43709-130">**套用**</span><span class="sxs-lookup"><span data-stu-id="43709-130">**Apply**</span></span>  
 <span data-ttu-id="43709-131">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="43709-131">Save your changes.</span></span>  
  
 <span data-ttu-id="43709-132">**刪除**</span><span class="sxs-lookup"><span data-stu-id="43709-132">**Delete**</span></span>  
 <span data-ttu-id="43709-133">從報表伺服器資料庫中移除共用資料集。</span><span class="sxs-lookup"><span data-stu-id="43709-133">Remove the shared dataset from the report server database.</span></span> <span data-ttu-id="43709-134">刪除共用資料集會停用任何報表或快取版本。</span><span class="sxs-lookup"><span data-stu-id="43709-134">Deleting a shared dataset deactivates any reports or cached versions.</span></span> <span data-ttu-id="43709-135">若要重新啟動報表，您必須在報表撰寫工具中開啟每一個報表，並指定具有相同名稱和相同欄位集合的資料集。</span><span class="sxs-lookup"><span data-stu-id="43709-135">To reactivate a report, you must open each one in a report authoring tool, and specify a dataset with the same name and the same field collection.</span></span> <span data-ttu-id="43709-136">或者，您也可以更新每個資料區參考，以使用含相同欄位集合的不同資料集。</span><span class="sxs-lookup"><span data-stu-id="43709-136">Alternatively, you can update each data region reference to use a different dataset with the same field collection.</span></span>  
  
 <span data-ttu-id="43709-137">**移動**</span><span class="sxs-lookup"><span data-stu-id="43709-137">**Move**</span></span>  
 <span data-ttu-id="43709-138">將報表伺服器資料夾階層內的共用資料集重新定位放置。</span><span class="sxs-lookup"><span data-stu-id="43709-138">Relocate a shared dataset within the report server folder hierarchy.</span></span> <span data-ttu-id="43709-139">按一下此按鈕會開啟 [移動項目] 頁面，您可在此瀏覽資料夾以選取新位置。</span><span class="sxs-lookup"><span data-stu-id="43709-139">Clicking this button opens the Move Items page, on which you can browse through folders for a new folder location.</span></span> <span data-ttu-id="43709-140">如需詳細資訊，請參閱[&#40;報表管理員&#41;中移動專案頁面](../../2014/reporting-services/move-items-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="43709-140">For more information, see [Move Items Page &#40;Report Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="43709-141">**下載**</span><span class="sxs-lookup"><span data-stu-id="43709-141">**Download**</span></span>  
 <span data-ttu-id="43709-142">擷取共用資料集定義的複本。</span><span class="sxs-lookup"><span data-stu-id="43709-142">Extract a copy of the shared dataset definition.</span></span> <span data-ttu-id="43709-143">視電腦上定義的檔案關聯而定，檔案會在 Visual Studio 或其他應用程式中開啟。</span><span class="sxs-lookup"><span data-stu-id="43709-143">Depending on the file associations defined on your computer, the file will open in Visual Studio or a different application.</span></span> <span data-ttu-id="43709-144">在大多數情況下，共用資料集會開啟為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="43709-144">In most cases, the shared dataset opens as an XML file.</span></span>  
  
 <span data-ttu-id="43709-145">**Replace**</span><span class="sxs-lookup"><span data-stu-id="43709-145">**Replace**</span></span>  
 <span data-ttu-id="43709-146">使用位於檔案系統中 .rsd 檔案的不同資料集定義，取代共用資料集定義。</span><span class="sxs-lookup"><span data-stu-id="43709-146">Replace the shared dataset definition with a different one from an .rsd file located on the file system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43709-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43709-147">See Also</span></span>  
 <span data-ttu-id="43709-148">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="43709-148">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="43709-149">[[內容] 頁面 &#40;報表管理員&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="43709-149">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="43709-150">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="43709-150">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="43709-151">[快取重新整理選項 &#40;報表管理員&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="43709-151">[Cache Refresh Options &#40;Report Manager&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md) </span></span>  
 <span data-ttu-id="43709-152">[[快取] 頁面，共用資料集 &#40;報表管理員&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="43709-152">[Caching Page, Shared Datasets &#40;Report Manager&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md) </span></span>  
 <span data-ttu-id="43709-153">[管理共用資料集](report-data/manage-shared-datasets.md) </span><span class="sxs-lookup"><span data-stu-id="43709-153">[Manage Shared Datasets](report-data/manage-shared-datasets.md) </span></span>  
 [<span data-ttu-id="43709-154">快取共用資料集 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="43709-154">Cache Shared Datasets &#40;SSRS&#41;</span></span>](report-server/cache-shared-datasets-ssrs.md)  
  
  
