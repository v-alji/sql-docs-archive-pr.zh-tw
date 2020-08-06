---
title: 在報表產生器中預覽報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75b822b318991299c979553ec4baa05005535362
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585104"
---
# <a name="previewing-reports-in-report-builder"></a><span data-ttu-id="f49b0-102">在報表產生器中預覽報表</span><span class="sxs-lookup"><span data-stu-id="f49b0-102">Previewing Reports in Report Builder</span></span>
  <span data-ttu-id="f49b0-103">當您建立報表時，經常預覽報表以確認報表如預期般顯示相當有協助。</span><span class="sxs-lookup"><span data-stu-id="f49b0-103">While you create a report, it is helpful to preview the report often to verify that the report displays what you want.</span></span> <span data-ttu-id="f49b0-104">若要預覽報表，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="f49b0-104">To preview your report, click **Run**.</span></span> <span data-ttu-id="f49b0-105">報表隨即在預覽模式下呈現。</span><span class="sxs-lookup"><span data-stu-id="f49b0-105">The report renders in preview mode.</span></span>  
  
 <span data-ttu-id="f49b0-106">報表產生器會在連接到報表伺服器時使用編輯工作階段，藉以改善預覽經驗。</span><span class="sxs-lookup"><span data-stu-id="f49b0-106">Report Builder improves the preview experience by using edit sessions when connected to a report server.</span></span> <span data-ttu-id="f49b0-107">編輯工作階段會建立一個資料快取，並讓快取中的資料集可以進行重複的報表預覽。</span><span class="sxs-lookup"><span data-stu-id="f49b0-107">The edit session creates a data cache and makes the datasets in the cache available for repeated report previews.</span></span> <span data-ttu-id="f49b0-108">編輯工作階段不是一個您可以直接互動的功能，但是，當您預覽報表並了解報表呈現速度為什麼較快或較慢時，了解何時重新整理快取的資料集將會協助您提升效能。</span><span class="sxs-lookup"><span data-stu-id="f49b0-108">An edit session is not a feature that you interact with directly, but understanding when the cached dataset is refreshed will help you improve performance when you preview a report and understand why the report renders faster or slower.</span></span>  
  
 <span data-ttu-id="f49b0-109">編輯工作階段的其他優點包括，能夠編輯使用內嵌資料來源或參考項目的報表，例如儲存在報表伺服器上的影像或子報表。</span><span class="sxs-lookup"><span data-stu-id="f49b0-109">Other benefits of edit sessions are the abilities to edit reports that use embedded data sources or reference items such as images or subreports that are stored on the report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="improving-preview-performance"></a><span data-ttu-id="f49b0-110">提升預覽效能</span><span class="sxs-lookup"><span data-stu-id="f49b0-110">Improving Preview Performance</span></span>  
 <span data-ttu-id="f49b0-111">您建立和更新報表的方式會影響報表在預覽中呈現的速度。</span><span class="sxs-lookup"><span data-stu-id="f49b0-111">How you create and update reports affects how fast the report renders in preview.</span></span> <span data-ttu-id="f49b0-112">當您第一次預覽依賴伺服器參考的報表時，系統會為您建立編輯工作階段，而且執行報表時所使用的資料會加入到儲存在報表伺服器上的資料快取中。</span><span class="sxs-lookup"><span data-stu-id="f49b0-112">The first time that you preview a report that relies on a server reference, an edit session is created for you and the data used when the report is run is added to a data cache that is stored on the report server.</span></span> <span data-ttu-id="f49b0-113">當您針對報表進行不會影響資料的變更時，報表會使用資料的快取副本。</span><span class="sxs-lookup"><span data-stu-id="f49b0-113">When you make changes to the report that does not affect the data, the cached copy of the data is used by the report.</span></span> <span data-ttu-id="f49b0-114">也就是說，每次預覽報表時，您都看不到資料變更。</span><span class="sxs-lookup"><span data-stu-id="f49b0-114">This means that you will not see data change each time you preview the report.</span></span> <span data-ttu-id="f49b0-115">如果您想要新的資料，請按一下功能區上的 [重新整理]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f49b0-115">If you want new data, click the **Refresh** button on the ribbon.</span></span>  
  
 <span data-ttu-id="f49b0-116">下列動作會重新整理快取，並減慢您下次預覽報表的報表呈現速度：</span><span class="sxs-lookup"><span data-stu-id="f49b0-116">The following actions cause the cache to be refreshed and slow down report rendering the next time you preview the report:</span></span>  
  
-   <span data-ttu-id="f49b0-117">加入、變更或刪除資料集。</span><span class="sxs-lookup"><span data-stu-id="f49b0-117">Add, change, or delete a dataset.</span></span> <span data-ttu-id="f49b0-118">快取資料集包含報表所使用的所有資料集，而且對於任何資料集的修改都會讓快取資料集失效。</span><span class="sxs-lookup"><span data-stu-id="f49b0-118">The cached dataset contains all the datasets that a report uses and modification to any dataset invalidates the cached dataset.</span></span> <span data-ttu-id="f49b0-119">這包括變更資料集中的名稱、查詢或欄位。</span><span class="sxs-lookup"><span data-stu-id="f49b0-119">This includes changing the name, query, or fields in the dataset.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f49b0-120">如果資料集中包含您預期不會使用的大量欄位，您應該考慮更新資料集來省略這些欄位。</span><span class="sxs-lookup"><span data-stu-id="f49b0-120">If the dataset has a large number of fields that you do not expect to use, you should consider updating the dataset to omit those fields.</span></span> <span data-ttu-id="f49b0-121">雖然這樣會建立新的編輯工作階段，而且第一次預覽報表的速度會較慢，但是快取資料集較小有益於報表伺服器的整體效能。</span><span class="sxs-lookup"><span data-stu-id="f49b0-121">Although this creates a new edit session and the first preview of the report is slower, there smaller cached dataset is overall beneficial to the performance of the report server.</span></span>  
  
-   <span data-ttu-id="f49b0-122">加入、變更或刪除資料來源。</span><span class="sxs-lookup"><span data-stu-id="f49b0-122">Add, change, or delete a data source.</span></span> <span data-ttu-id="f49b0-123">這包含變更資料來源的名稱或屬性、資料來源的資料延伸模組，或是資料來源連接的屬性。</span><span class="sxs-lookup"><span data-stu-id="f49b0-123">This includes changing the name or properties of the data source, the data extension of the data source, or the properties of the connection to the data source.</span></span>  
  
-   <span data-ttu-id="f49b0-124">將報表所使用的共用資料來源變更為不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f49b0-124">Change the shared data source that the report uses to a different data source.</span></span>  
  
-   <span data-ttu-id="f49b0-125">變更報表的語言。</span><span class="sxs-lookup"><span data-stu-id="f49b0-125">Change the language of the report.</span></span>  
  
-   <span data-ttu-id="f49b0-126">變更報表所使用的組件或自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="f49b0-126">Change the assemblies or custom code that the report uses.</span></span>  
  
-   <span data-ttu-id="f49b0-127">加入、變更或刪除報表或參數值中的查詢參數。</span><span class="sxs-lookup"><span data-stu-id="f49b0-127">Add, change, or delete the query parameters in the report or parameter values.</span></span>  
  
 <span data-ttu-id="f49b0-128">對於報表配置和資料格式所做的變更不會影響快取資料集。</span><span class="sxs-lookup"><span data-stu-id="f49b0-128">Changes to the report layout and data formatting do not affect the cached dataset.</span></span> <span data-ttu-id="f49b0-129">您可以在不重新整理快取資料集的情況下執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f49b0-129">You can do the following actions without refreshing the cached dataset:</span></span>  
  
-   <span data-ttu-id="f49b0-130">加入或移除資料區，例如資料表、矩陣或圖表。</span><span class="sxs-lookup"><span data-stu-id="f49b0-130">Add or remove data regions such as tables, matrices or charts.</span></span>  
  
-   <span data-ttu-id="f49b0-131">從報表加入或刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="f49b0-131">Add or delete columns from the report.</span></span> <span data-ttu-id="f49b0-132">資料集中的所有欄位都可供報表中的使用者使用。</span><span class="sxs-lookup"><span data-stu-id="f49b0-132">All the fields in the dataset are available to use in the report.</span></span> <span data-ttu-id="f49b0-133">加入或移除報表中的欄位不會影響資料集。</span><span class="sxs-lookup"><span data-stu-id="f49b0-133">Adding or removing fields in the report has no effect on the dataset.</span></span>  
  
-   <span data-ttu-id="f49b0-134">變更欄位在資料表和矩陣中的順序。</span><span class="sxs-lookup"><span data-stu-id="f49b0-134">Change the order of fields in tables and matrices.</span></span>  
  
-   <span data-ttu-id="f49b0-135">加入、變更或刪除資料列和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="f49b0-135">Add, change, or delete row and column groups.</span></span>  
  
-   <span data-ttu-id="f49b0-136">加入、變更或刪除資料值在欄位中的格式。</span><span class="sxs-lookup"><span data-stu-id="f49b0-136">Add, change, or delete formatting of data values in fields.</span></span>  
  
-   <span data-ttu-id="f49b0-137">加入、變更或刪除影像、線條或文字方塊。</span><span class="sxs-lookup"><span data-stu-id="f49b0-137">Add, change, or delete images, lines, or text boxes.</span></span>  
  
-   <span data-ttu-id="f49b0-138">變更分頁符號。</span><span class="sxs-lookup"><span data-stu-id="f49b0-138">Change page breaks.</span></span>  
  
 <span data-ttu-id="f49b0-139">第一次預覽報表時會建立編輯工作階段。</span><span class="sxs-lookup"><span data-stu-id="f49b0-139">The edit session is created the first time that you preview a report.</span></span> <span data-ttu-id="f49b0-140">根據預設，編輯工作階段會持續 7200 秒 (2 小時)。</span><span class="sxs-lookup"><span data-stu-id="f49b0-140">By default, an edit session lasts 7200 seconds (2 hours).</span></span> <span data-ttu-id="f49b0-141">每次執行報表時，此工作階段會重設為 2 小時。</span><span class="sxs-lookup"><span data-stu-id="f49b0-141">The session is reset to two hours every time you run the report.</span></span> <span data-ttu-id="f49b0-142">當編輯工作階段到期時，系統會刪除資料快取。</span><span class="sxs-lookup"><span data-stu-id="f49b0-142">When the edit session expires, the data cache is deleted.</span></span> <span data-ttu-id="f49b0-143">如果編輯工作階段到期，下次您預覽報表時，系統會再次自動建立一個。</span><span class="sxs-lookup"><span data-stu-id="f49b0-143">If the edit session expires, one is automatically created again the next time that you preview the report.</span></span> <span data-ttu-id="f49b0-144">編輯工作階段的到期時間可以設定。</span><span class="sxs-lookup"><span data-stu-id="f49b0-144">The expiration time for edit sessions is configurable.</span></span> <span data-ttu-id="f49b0-145">如果您發現 2 小時太長或太短，請連絡報表伺服器的管理員。</span><span class="sxs-lookup"><span data-stu-id="f49b0-145">If you find that two hours is too long or too short, contact the administrator of the report server.</span></span>  
  
 <span data-ttu-id="f49b0-146">根據預設，資料快取最多可以容納 5 個資料集。</span><span class="sxs-lookup"><span data-stu-id="f49b0-146">By default, the data cache can hold up to five datasets.</span></span> <span data-ttu-id="f49b0-147">如果您使用多個不同的參數值組合，報表可能需要更多資料。</span><span class="sxs-lookup"><span data-stu-id="f49b0-147">If you use many different combinations of parameter values, the report might need more data.</span></span> <span data-ttu-id="f49b0-148">這需要重新整理快取，而且當您下次預覽報表時，報表的呈現速度會更慢。</span><span class="sxs-lookup"><span data-stu-id="f49b0-148">This requires the cache be refreshed and the report renders more slowly the next time that you preview it.</span></span> <span data-ttu-id="f49b0-149">快取中的項目數可以由報表伺服器的管理員設定。</span><span class="sxs-lookup"><span data-stu-id="f49b0-149">The number of entries in the cache is configurable by the administrator of the report server.</span></span>  
  
## <a name="concurrency-of-report-updates"></a><span data-ttu-id="f49b0-150">報表更新並行</span><span class="sxs-lookup"><span data-stu-id="f49b0-150">Concurrency of Report Updates</span></span>  
 <span data-ttu-id="f49b0-151">當您更新報表，並將其儲存到報表伺服器時，您會經常預覽它。</span><span class="sxs-lookup"><span data-stu-id="f49b0-151">Frequently, you preview a report as a step in updating and then saving a report to a report server.</span></span> <span data-ttu-id="f49b0-152">當您正在更新報表時，可能會有其他人正在進行更新，然後同時儲存該報表。</span><span class="sxs-lookup"><span data-stu-id="f49b0-152">When you are updating a report, it is possible that someone else is updating and then saving the report at the same time.</span></span> <span data-ttu-id="f49b0-153">最後儲存的報表是可供未來檢視和更新的報表版本。</span><span class="sxs-lookup"><span data-stu-id="f49b0-153">The report that is saved last is the version of report that is available for future viewing and updating.</span></span> <span data-ttu-id="f49b0-154">這表示，您預覽的報表版本可能不是再次開啟的版本。</span><span class="sxs-lookup"><span data-stu-id="f49b0-154">This means that the version of the report that you previewed might not be the version you reopen.</span></span> <span data-ttu-id="f49b0-155">您可以選擇使用 [報表產生器] 功能表上的 [另存新檔]\*\*\*\* 選項，將報表儲存成新的名稱。</span><span class="sxs-lookup"><span data-stu-id="f49b0-155">You have the option to save the report with a new name by using the **Save As** option on the Report Builder menu.</span></span>  
  
## <a name="external-report-items"></a><span data-ttu-id="f49b0-156">外部報表項目</span><span class="sxs-lookup"><span data-stu-id="f49b0-156">External Report Items</span></span>  
 <span data-ttu-id="f49b0-157">您的報表可能包含的項目包括共用資料來源、外部影像，以及與報表個別儲存的子報表等等。</span><span class="sxs-lookup"><span data-stu-id="f49b0-157">Your report might include items such as shared data sources, external images, and subreports that are stored separately from the report.</span></span> <span data-ttu-id="f49b0-158">由於這些項目會個別儲存，因此可能會移到報表伺服器上的其他位置或是遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="f49b0-158">Because the items are stored separately is possible that they can be moved to a different location on the report server or deleted.</span></span> <span data-ttu-id="f49b0-159">如果發生這個情況，您的報表可能無法預覽。</span><span class="sxs-lookup"><span data-stu-id="f49b0-159">If this happens, your report could fail to preview.</span></span> <span data-ttu-id="f49b0-160">您可以更新報表以指出項目的更新位置；如果項目遭到刪除，則將其取代成現有的項目，或從報表中移除該項目的參考。</span><span class="sxs-lookup"><span data-stu-id="f49b0-160">You can either update the report to indicate the updated location of the item or if the item was deleted, replace it with an existing item, or remove the reference to the item it from the report.</span></span>  
  
 <span data-ttu-id="f49b0-161">如果建立編輯工作階段之後，變更了您報表所使用的子報表，該報表將不會呈現在預覽中。</span><span class="sxs-lookup"><span data-stu-id="f49b0-161">If a subreport used by your report is changed after your edit session was created, the report will not render in preview.</span></span> <span data-ttu-id="f49b0-162">若要成功預覽報表，您應該儲存報表，或按一下 [重新整理]\*\*\*\* 來取得新的資料。</span><span class="sxs-lookup"><span data-stu-id="f49b0-162">To successfully preview the report, you should save the report or click **Refresh** to get fresh data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49b0-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f49b0-163">See Also</span></span>  
 <span data-ttu-id="f49b0-164">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f49b0-164">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="f49b0-165">[將報表專案的格式設定 &#40;報表產生器和 SSRS&#41;](../report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f49b0-165">[Formatting Report Items &#40;Report Builder and SSRS&#41;](../report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f49b0-166">[報表產生器和 SSRS &#40;資料表、矩陣和清單&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f49b0-166">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f49b0-167">[圖表 &#40;報表產生器和 SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f49b0-167">[Charts &#40;Report Builder and SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f49b0-168">[報表產生器和 SSRS &#40;資料表、矩陣和清單&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f49b0-168">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f49b0-169">儲存報表 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="f49b0-169">Saving Reports &#40;Report Builder&#41;</span></span>](saving-reports-report-builder.md)  
  
  
