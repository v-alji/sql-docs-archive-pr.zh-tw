---
title: 動作屬性對話方塊 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77b51af0763010676b95fcedb433ab963fc7fcdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597663"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a><span data-ttu-id="87856-102">動作屬性對話方塊 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="87856-102">Action Properties Dialog Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="87856-103">**[動作]** 對話方塊可用於啟用支援連結之圖表、量測計與地圖元素的超連結選項。</span><span class="sxs-lookup"><span data-stu-id="87856-103">The **Action** dialog box can be used to enable hyperlink options for a chart, gauge, and map elements that support links.</span></span> <span data-ttu-id="87856-104">定義動作，讓使用者可以按一下報表與 URL 的連結，便連結至相同報表伺服器或與報表伺服器整合之 SharePoint 網站上的不同報表，或連結至相同報表中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="87856-104">Define an action so that a user can click on the report and link to a URL, to a different report on the same report server or on a SharePoint site that is integrated with a report server, or to a different location in the same report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="87856-105">選項</span><span class="sxs-lookup"><span data-stu-id="87856-105">Options</span></span>  
 <span data-ttu-id="87856-106">**啟用為動作**</span><span class="sxs-lookup"><span data-stu-id="87856-106">**Enable as an action**</span></span>  
 <span data-ttu-id="87856-107">選取一個選項來指示使用者按一下項目時所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="87856-107">Select an option to indicate the action to perform when the user clicks the item.</span></span>  
  
 <span data-ttu-id="87856-108">**None**</span><span class="sxs-lookup"><span data-stu-id="87856-108">**None**</span></span>  
 <span data-ttu-id="87856-109">請選擇這個選項來指出項目沒有動作。</span><span class="sxs-lookup"><span data-stu-id="87856-109">Choose this option to indicate that the item has no action.</span></span>  
  
 <span data-ttu-id="87856-110">**移至報表**</span><span class="sxs-lookup"><span data-stu-id="87856-110">**Go to report**</span></span>  
 <span data-ttu-id="87856-111">選擇此選項即可建立位於報表伺服器之鑽研報表的連結。</span><span class="sxs-lookup"><span data-stu-id="87856-111">Choose this option to create a link to a drillthrough report that is located on a report server.</span></span> <span data-ttu-id="87856-112">當您選取 **[移至報表]** 時會出現下面其他選項。</span><span class="sxs-lookup"><span data-stu-id="87856-112">The following additional options appear when you select **Go to report**.</span></span>  
  
 <span data-ttu-id="87856-113">**指定報表**</span><span class="sxs-lookup"><span data-stu-id="87856-113">**Specify a report**</span></span>  
 <span data-ttu-id="87856-114">輸入或選取您要當做鑽研報表使用之報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="87856-114">Type or select the name of the report that you want to use as a drillthrough report.</span></span> <span data-ttu-id="87856-115">鑽研報表必須位於與此報表相同的報表伺服器上。</span><span class="sxs-lookup"><span data-stu-id="87856-115">Drillthrough reports must be on the same report server as this report.</span></span>  
  
 <span data-ttu-id="87856-116">對於發行到設定為原生模式之報表伺服器的報表，請使用不含副檔名的完整或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="87856-116">For a report published to a report server configured for native mode, use a full or relative path without the file name extension.</span></span> <span data-ttu-id="87856-117">如果此報表與目前的報表在相同資料夾中，則只使用報表名稱。</span><span class="sxs-lookup"><span data-stu-id="87856-117">If the report is in the same folder as the current report, use the name of the report only.</span></span> <span data-ttu-id="87856-118">如果報表位於相同報表伺服器上的不同資料夾中，請使用相對路徑或完整路徑。</span><span class="sxs-lookup"><span data-stu-id="87856-118">If the report is in a different folder on the same report server, use a relative path or a full path.</span></span> <span data-ttu-id="87856-119">相對路徑會從目前的資料夾開始，並將資料夾階層上移，例如，../Folder2/Report1。</span><span class="sxs-lookup"><span data-stu-id="87856-119">A relative path starts from the current folder and moves up the folder hierarchy, for example, ../Folder2/Report1.</span></span> <span data-ttu-id="87856-120">完整路徑則是從 /，也又是主資料夾開始。</span><span class="sxs-lookup"><span data-stu-id="87856-120">A full path starts from /, the Home folder.</span></span> <span data-ttu-id="87856-121">例如，/Reports/Report1。</span><span class="sxs-lookup"><span data-stu-id="87856-121">For example, /Reports/Report1.</span></span>  
  
 <span data-ttu-id="87856-122">對於發行到設定為 SharePoint 整合模式之報表伺服器的報表，請使用包含副檔名 (.rdl) 的完整 URL。</span><span class="sxs-lookup"><span data-stu-id="87856-122">For a report published to a report server configured in SharePoint integrated mode, use a fully qualified URL including the file name extension (.rdl).</span></span> <span data-ttu-id="87856-123">例如，HTTP:// *\<SharePointservername>/\<site>* /documents/report1.rdl。</span><span class="sxs-lookup"><span data-stu-id="87856-123">For example, http://*\<SharePointservername>/\<site>*/Documents/Report1.rdl.</span></span> <span data-ttu-id="87856-124">不支援相對路徑。</span><span class="sxs-lookup"><span data-stu-id="87856-124">Relative paths are not supported.</span></span>  
  
 <span data-ttu-id="87856-125">如需詳細資訊，請參閱 msdn.microsoft.com 之[報表產生器文件](https://go.microsoft.com/fwlink/?LinkId=154494)中的[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="87856-125">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="87856-126">**使用這些參數執行報表**</span><span class="sxs-lookup"><span data-stu-id="87856-126">**Use these parameters to run the report**</span></span>  
 <span data-ttu-id="87856-127">加入參數清單，以傳遞至鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="87856-127">Add a list of parameters to pass to the drillthrough report.</span></span> <span data-ttu-id="87856-128">參數名稱必須符合針對目標報表定義的參數。</span><span class="sxs-lookup"><span data-stu-id="87856-128">The parameter names must match the parameters defined for the target report.</span></span> <span data-ttu-id="87856-129">使用 **[加入]** 和 **[刪除]** 按鈕來加入和移除參數，並使用向上與向下箭頭來排列參數清單的順序。</span><span class="sxs-lookup"><span data-stu-id="87856-129">Use the **Add** and **Delete** buttons to add and remove parameters and use the up and down arrows to order the list of parameters.</span></span>  
  
 <span data-ttu-id="87856-130">**加入**</span><span class="sxs-lookup"><span data-stu-id="87856-130">**Add**</span></span>  
 <span data-ttu-id="87856-131">加入新的參數，以傳遞至鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="87856-131">Add a new parameter to pass to the drillthrough report.</span></span>  
  
 <span data-ttu-id="87856-132">**刪除**</span><span class="sxs-lookup"><span data-stu-id="87856-132">**Delete**</span></span>  
 <span data-ttu-id="87856-133">刪除鑽研報表的參數。</span><span class="sxs-lookup"><span data-stu-id="87856-133">Delete a parameter for the drillthrough report.</span></span>  
  
 <span data-ttu-id="87856-134">**向上箭頭**</span><span class="sxs-lookup"><span data-stu-id="87856-134">**Up arrow**</span></span>  
 <span data-ttu-id="87856-135">將清單中的參數向上移動。</span><span class="sxs-lookup"><span data-stu-id="87856-135">Move the parameter up in the list.</span></span>  
  
 <span data-ttu-id="87856-136">**向下箭頭**</span><span class="sxs-lookup"><span data-stu-id="87856-136">**Down arrow**</span></span>  
 <span data-ttu-id="87856-137">將清單中的參數向下移動。</span><span class="sxs-lookup"><span data-stu-id="87856-137">Move the parameter down in the list.</span></span>  
  
 <span data-ttu-id="87856-138">**名稱**</span><span class="sxs-lookup"><span data-stu-id="87856-138">**Name**</span></span>  
 <span data-ttu-id="87856-139">輸入鑽研報表中定義之參數名稱的文字。</span><span class="sxs-lookup"><span data-stu-id="87856-139">Type text that is the name of a parameter defined in the drillthrough report.</span></span>  
  
 <span data-ttu-id="87856-140">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="87856-140">**Value**</span></span>  
 <span data-ttu-id="87856-141">在鑽研報表中，為具名參數輸入或選取要傳遞的值。</span><span class="sxs-lookup"><span data-stu-id="87856-141">Type or select a value to pass for the named parameter in the drillthrough report.</span></span> <span data-ttu-id="87856-142">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="87856-142">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="87856-143">**省略**</span><span class="sxs-lookup"><span data-stu-id="87856-143">**Omit**</span></span>  
 <span data-ttu-id="87856-144">選取此選項以防止參數執行。</span><span class="sxs-lookup"><span data-stu-id="87856-144">Select to prevent the parameter from running.</span></span> <span data-ttu-id="87856-145">根據預設，不會勾選也不會啟用此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="87856-145">By default, this check box is cleared and not active.</span></span> <span data-ttu-id="87856-146">若要選取此核取方塊，按一下 [運算式]\*\*\*\* (*fx*) 按鈕，然後輸入 **True** 或建立一個運算式。</span><span class="sxs-lookup"><span data-stu-id="87856-146">To select the check box, click the **Expression** (*fx*) button and either type **True** or create an expression.</span></span> <span data-ttu-id="87856-147">當您按一下 **[運算式]** 對話方塊中的 **[確定]** 時，就會選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="87856-147">The check box is selected when you click **OK** in the **Expression** dialog box.</span></span>  
  
 <span data-ttu-id="87856-148">**移至書籤**</span><span class="sxs-lookup"><span data-stu-id="87856-148">**Go to bookmark**</span></span>  
 <span data-ttu-id="87856-149">選擇此選項即可在目前的報表中，定義書籤的連結。</span><span class="sxs-lookup"><span data-stu-id="87856-149">Choose this option to define a link to a bookmark in the current report.</span></span> <span data-ttu-id="87856-150">當您選取 **[移至書籤]** 時會出現下面其他選項。</span><span class="sxs-lookup"><span data-stu-id="87856-150">The following additional option appears when you select **Go to bookmark**.</span></span>  
  
 <span data-ttu-id="87856-151">**選取書籤**</span><span class="sxs-lookup"><span data-stu-id="87856-151">**Select bookmark**</span></span>  
 <span data-ttu-id="87856-152">請輸入或選取書籤識別碼，這是當使用者按一下連結時要跳至的目的地。</span><span class="sxs-lookup"><span data-stu-id="87856-152">Type or select the bookmark ID for the report to jump to when the user clicks the link.</span></span> <span data-ttu-id="87856-153">按一下 [運算式] (**fx**) 按鈕以變更運算式。</span><span class="sxs-lookup"><span data-stu-id="87856-153">Click the Expression (**fx**) button to change the expression.</span></span> <span data-ttu-id="87856-154">書籤識別碼可以是靜態識別碼或者會評估為書籤識別碼的運算式。</span><span class="sxs-lookup"><span data-stu-id="87856-154">The bookmark ID can be either a static ID or an expression that evaluates to a bookmark ID.</span></span> <span data-ttu-id="87856-155">此運算式可包含具有書籤識別碼的欄位。</span><span class="sxs-lookup"><span data-stu-id="87856-155">The expression can include a field that contains a bookmark ID.</span></span>  
  
 <span data-ttu-id="87856-156">若要連結到書籤，您必須先設定報表項目的 [書籤] 屬性。</span><span class="sxs-lookup"><span data-stu-id="87856-156">To link to a bookmark, you must first set the Bookmark property of a report item.</span></span> <span data-ttu-id="87856-157">若要設定 [書籤] 屬性，請選取報表項目，然後在 [屬性] 窗格中輸入書籤識別碼的值或運算式，例如 SalesChart 或 5TopSales。</span><span class="sxs-lookup"><span data-stu-id="87856-157">To set the Bookmark property, select a report item, and in the Properties pane, type a value or expression for the bookmark ID; for example, SalesChart or 5TopSales.</span></span>  
  
 <span data-ttu-id="87856-158">**移至 URL**</span><span class="sxs-lookup"><span data-stu-id="87856-158">**Go to URL**</span></span>  
 <span data-ttu-id="87856-159">請選擇這個選項來定義通往網頁的連結。</span><span class="sxs-lookup"><span data-stu-id="87856-159">Choose this option to define a link to a Web page.</span></span> <span data-ttu-id="87856-160">請輸入或選取網頁的 URL，或會評估結果為網頁 URL 的運算式。</span><span class="sxs-lookup"><span data-stu-id="87856-160">Type or select the URL of a Web page or an expression that evaluates to the URL of a Web page.</span></span> <span data-ttu-id="87856-161">按一下 [運算式]\*\*\*\* (*fx*) 按鈕以變更運算式。</span><span class="sxs-lookup"><span data-stu-id="87856-161">Click the **Expression** (*fx*) button to change the expression.</span></span> <span data-ttu-id="87856-162">這個運算式可以包括含有 URL 的欄位。</span><span class="sxs-lookup"><span data-stu-id="87856-162">This expression can include a field that contains a URL.</span></span> <span data-ttu-id="87856-163">當您選取 **[移至 URL]** 時會出現下面其他選項。</span><span class="sxs-lookup"><span data-stu-id="87856-163">The following additional option appears when you select **Go to URL**.</span></span>  
  
 <span data-ttu-id="87856-164">**選取 URL**</span><span class="sxs-lookup"><span data-stu-id="87856-164">**Select URL**</span></span>  
 <span data-ttu-id="87856-165">輸入或輸入項目的 URL。</span><span class="sxs-lookup"><span data-stu-id="87856-165">Type or enter the URL of the item.</span></span> <span data-ttu-id="87856-166">對於發行到設定為原生模式之報表伺服器的項目，請使用完整或相對路徑，</span><span class="sxs-lookup"><span data-stu-id="87856-166">For an item published to a report server configured for native mode, use a full or relative path.</span></span> <span data-ttu-id="87856-167">例如，HTTP:// *\<servername>* /images/image1.jpg。</span><span class="sxs-lookup"><span data-stu-id="87856-167">For example, http://*\<servername>*/images/image1.jpg.</span></span> <span data-ttu-id="87856-168">對於發行到設定為 SharePoint 整合模式之報表伺服器的專案，請使用完整的 URL (例如，HTTP:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg) 。</span><span class="sxs-lookup"><span data-stu-id="87856-168">For an item published to a report server configured in SharePoint integrated mode, use a fully qualified URL (for example, http://*\<SharePointservername>/\<site>*/Documents/images/image1.jpg).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87856-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87856-169">See Also</span></span>  
 <span data-ttu-id="87856-170">[圖表 &#40;報表產生器和 SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="87856-170">[Charts &#40;Report Builder and SSRS&#41;](report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="87856-171">[對話方塊、窗格和嚮導的報表產生器說明](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="87856-171">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="87856-172">[報表參數 &#40;報表產生器和報表設計師&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="87856-172">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="87856-173">[&#40;報表產生器和 SSRS 加入子報表和參數&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="87856-173">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="87856-174">互動式排序、文件引導模式及連結 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="87856-174">Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;</span></span>](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  
