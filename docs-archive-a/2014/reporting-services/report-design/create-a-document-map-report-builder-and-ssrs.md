---
title: 建立文件引導模式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c200a97b-67f2-499f-8374-3ed1ebe3f33c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a9dad0f8e6ee1d9b9ada44fda0eec5908f27cfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594442"
---
# <a name="create-a-document-map-report-builder-and-ssrs"></a><span data-ttu-id="462dc-102">建立文件引導模式 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="462dc-102">Create a Document Map (Report Builder and SSRS)</span></span>
  <span data-ttu-id="462dc-103">文件引導模式提供了與轉譯報表中之報表項目連結的一組導覽連結。</span><span class="sxs-lookup"><span data-stu-id="462dc-103">A document map provides a set of navigational links to report items in a rendered report.</span></span> <span data-ttu-id="462dc-104">您檢視包含文件引導模式的報表時，報表旁邊會出現另一個側窗格。</span><span class="sxs-lookup"><span data-stu-id="462dc-104">When you view a report that includes a document map, a separate side pane appears next to the report.</span></span> <span data-ttu-id="462dc-105">使用者按一下文件引導模式中的連結，即可跳到顯示該項目的報表頁面。</span><span class="sxs-lookup"><span data-stu-id="462dc-105">A user can click links in the document map to jump to the report page that displays that item.</span></span> <span data-ttu-id="462dc-106">報表區段與群組會以連結的階層排列。</span><span class="sxs-lookup"><span data-stu-id="462dc-106">Report sections and groups are arranged in a hierarchy of links.</span></span> <span data-ttu-id="462dc-107">按一下文件引導模式中的項目，會重新整理報表並顯示文件引導模式中之項目所對應的報表區域。</span><span class="sxs-lookup"><span data-stu-id="462dc-107">Clicking items in the document map refreshes the report and displays the area of the report that corresponds to the item in the document map.</span></span>  
  
 <span data-ttu-id="462dc-108">若要在文件引導模式中加入連結，您可將報表項目的 `DocumentMapLabel` 屬性設定為您所建立的文字，或是將它設定為某個運算式，該運算式會評估為您希望顯示於文件引導模式中的文字。</span><span class="sxs-lookup"><span data-stu-id="462dc-108">To add links to the document map, you set the `DocumentMapLabel` property of the report item to text that you create or to an expression that evaluates to the text that you want display in the document map.</span></span> <span data-ttu-id="462dc-109">您也可以將資料表或矩陣群組的唯一值加入到文件引導模式。</span><span class="sxs-lookup"><span data-stu-id="462dc-109">You can also add the unique values for a table or matrix group to the document map.</span></span> <span data-ttu-id="462dc-110">例如，如果是以色彩為根據的群組，每一個唯一色彩就是報表頁面的連結，可顯示該色彩的群組執行個體。</span><span class="sxs-lookup"><span data-stu-id="462dc-110">For example, for a group based on color, each unique color is a link to the report page that displays the group instance for that color.</span></span>  
  
 <span data-ttu-id="462dc-111">您也可以建立報表的 URL 來覆寫文件引導模式的顯示，讓您可以執行報表而不顯示文件引導模式，然後按一下報表檢視器工具列上的 **[顯示/隱藏文件引導模式]** 按鈕來切換顯示。</span><span class="sxs-lookup"><span data-stu-id="462dc-111">You can also create a URL to a report that overrides the display of the document map, so that you can run the report without displaying the document map, and then click the **Show/Hide Document Map** button on the report viewer toolbar to toggle the display.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="document-maps-and-rendering-extensions"></a><a name="DocMapRenderExtensions"></a> <span data-ttu-id="462dc-112">文件引導模式及轉譯延伸模組</span><span class="sxs-lookup"><span data-stu-id="462dc-112">Document Maps and Rendering Extensions</span></span>  
 <span data-ttu-id="462dc-113">文件引導模式旨在供 HTML 轉譯延伸模組使用，例如，在預覽和報表檢視器中。</span><span class="sxs-lookup"><span data-stu-id="462dc-113">The document map is intended for use in the HTML rendering extension-for example, in Preview and the Report Viewer.</span></span> <span data-ttu-id="462dc-114">其他轉譯延伸模組有不同的方式來表達文件引導模式：</span><span class="sxs-lookup"><span data-stu-id="462dc-114">Other rendering extensions have different ways of articulating a document map:</span></span>  
  
-   <span data-ttu-id="462dc-115">PDF 會將文件引導模式轉譯成 [書籤] 窗格。</span><span class="sxs-lookup"><span data-stu-id="462dc-115">PDF renders a document map as the Bookmarks pane.</span></span>  
  
-   <span data-ttu-id="462dc-116">Excel 會將文件引導模式轉譯成具名工作表，其中包含連結的階層。</span><span class="sxs-lookup"><span data-stu-id="462dc-116">Excel renders a document map as a named worksheet that includes a hierarchy of links.</span></span> <span data-ttu-id="462dc-117">報表區段會在個別工作表中轉譯，這些工作表和文件引導模式包含在同一個活頁簿中。</span><span class="sxs-lookup"><span data-stu-id="462dc-117">Report sections are rendered in separate worksheets that are included with the document map in the same workbook.</span></span>  
  
-   <span data-ttu-id="462dc-118">Word 會將文件引導模式加入為目錄。</span><span class="sxs-lookup"><span data-stu-id="462dc-118">Word includes a document map as the table of contents.</span></span>  
  
-   <span data-ttu-id="462dc-119">Atom、TIFF、XML 與 CSV 則會忽略文件引導模式。</span><span class="sxs-lookup"><span data-stu-id="462dc-119">Atom, TIFF, XML, and CSV ignore document maps.</span></span>  
  
 <span data-ttu-id="462dc-120">如需詳細資訊，請參閱[不同報表轉譯延伸模組的互動式功能 &#40;報表產生器及 SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="462dc-120">For more information, see [Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md).</span></span>  
  
##  <a name="AddRptItemToMap"></a>   
#### <a name="to-add-a-report-item-to-a-document-map"></a><span data-ttu-id="462dc-121">將報表項目加入至文件引導模式中</span><span class="sxs-lookup"><span data-stu-id="462dc-121">To add a report item to a document map</span></span>  
  
1.  <span data-ttu-id="462dc-122">在 [設計] 檢視中，選取要加入至文件引導模式的報表項目，例如資料表、矩陣或量測計。</span><span class="sxs-lookup"><span data-stu-id="462dc-122">In Design view, select the report item such as a table, matrix, or gauge that you want to add to the document map.</span></span> <span data-ttu-id="462dc-123">該報表項目的屬性會出現在 [屬性] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="462dc-123">The report item properties appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="462dc-124">若要選取 Tablix 資料區，請在任何資料格中按一下來顯示資料列和資料行控點，然後按一下角控點。</span><span class="sxs-lookup"><span data-stu-id="462dc-124">To select a tablix data region, click in any cell to display the row and column handles, and then click the corner handle.</span></span>  
  
2.  <span data-ttu-id="462dc-125">在 [屬性] 窗格中，輸入您想要在屬性的檔引導模式中顯示的文字 `DocumentMapLabel` ，或輸入評估為標籤的運算式。</span><span class="sxs-lookup"><span data-stu-id="462dc-125">In the Properties pane, type the text that you want to appear in the document map in the `DocumentMapLabel` property, or enter an expression that evaluates to a label.</span></span> <span data-ttu-id="462dc-126">例如，輸入 **Sales Chart**。</span><span class="sxs-lookup"><span data-stu-id="462dc-126">For example, type **Sales Chart**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="462dc-127">如果看不到 [屬性] 窗格，請在 **[檢視]** 索引標籤的 **[顯示/隱藏]** 群組中，選取 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="462dc-127">If you do not see the Properties pane, on the **View** tab, in the **Show/Hide** group, select **Properties**.</span></span>  
  
3.  <span data-ttu-id="462dc-128">針對您希望出現在文件引導模式中的每個報表項目重複步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="462dc-128">Repeat steps 1 and 2 for every report item that you want to appear in the document map.</span></span>  
  
4.  <span data-ttu-id="462dc-129">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="462dc-129">Click **Run**.</span></span> <span data-ttu-id="462dc-130">報表便會執行，而且文件引導模式會顯示您所建立的標籤。</span><span class="sxs-lookup"><span data-stu-id="462dc-130">The report runs and the document map displays the labels you created.</span></span> <span data-ttu-id="462dc-131">按一下任何連結，即可跳至包含該項目的報表頁面。</span><span class="sxs-lookup"><span data-stu-id="462dc-131">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="AddUniqueValuesToMap"></a>   
#### <a name="to-add-unique-group-values-to-a-document-map"></a><span data-ttu-id="462dc-132">將唯一的群組值加入至文件引導模式中</span><span class="sxs-lookup"><span data-stu-id="462dc-132">To add unique group values to a document map</span></span>  
  
1.  <span data-ttu-id="462dc-133">在 [設計] 檢視中，選取包含您希望顯示在文件引導模式中之群組的資料表、矩陣或清單。</span><span class="sxs-lookup"><span data-stu-id="462dc-133">In Design view, select the table, matrix, or list that contains the group that you want to display in the document map.</span></span> <span data-ttu-id="462dc-134">[群組] 窗格會顯示資料列和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="462dc-134">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="462dc-135">在 [資料列群組] 窗格中，以滑鼠右鍵按一下群組，然後按一下 **[編輯群組]** 。</span><span class="sxs-lookup"><span data-stu-id="462dc-135">In the Row Groups pane, right-click the group, and then click **Edit Group**.</span></span> <span data-ttu-id="462dc-136">**[Tablix 群組屬性]** 對話方塊的 **[一般]** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="462dc-136">The **General** page of the **Tablix Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="462dc-137">按一下 **[進階]** 。</span><span class="sxs-lookup"><span data-stu-id="462dc-137">Click **Advanced**.</span></span>  
  
4.  <span data-ttu-id="462dc-138">在 **[文件引導模式]** 清單方塊中，輸入或選取符合群組運算式的某個運算式。</span><span class="sxs-lookup"><span data-stu-id="462dc-138">In the **Document map** list box, type or select an expression that matches the group expression.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="462dc-139">針對您希望出現在文件引導模式中的每一個群組重複步驟 1 到 4。</span><span class="sxs-lookup"><span data-stu-id="462dc-139">Repeat steps 1-4 for every group that you want to appear in the document map.</span></span>  
  
7.  <span data-ttu-id="462dc-140">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="462dc-140">Click **Run**.</span></span> <span data-ttu-id="462dc-141">報表便會執行，而且文件引導模式會顯示群組值。</span><span class="sxs-lookup"><span data-stu-id="462dc-141">The report runs and the document map displays the group values.</span></span> <span data-ttu-id="462dc-142">按一下任何連結，即可跳至包含該項目的報表頁面。</span><span class="sxs-lookup"><span data-stu-id="462dc-142">Click any link to jump to the report page with that item.</span></span>  
  
 
  
##  <a name="HideMapWhenViewRpt"></a>   
#### <a name="to-hide-the-document-map-when-you-view-a-report"></a><span data-ttu-id="462dc-143">在檢視報表時隱藏文件引導模式</span><span class="sxs-lookup"><span data-stu-id="462dc-143">To hide the document map when you view a report</span></span>  
  
1.  <span data-ttu-id="462dc-144">在報表管理員中，瀏覽至具有文件引導模式的報表。</span><span class="sxs-lookup"><span data-stu-id="462dc-144">In Report Manager, browse to the report that has the document map.</span></span>  
  
     <span data-ttu-id="462dc-145">例如，以 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 範例報表為例，下列 URL 會指定名為 Product Catalog 的報表。</span><span class="sxs-lookup"><span data-stu-id="462dc-145">For example, for the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample reports, the following URL specifies the report named Product Catalog.</span></span>  
  
    ```  
    http://localhost/Reports/Pages/Report.aspx?ItemPath=%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    ```  
  
2.  <span data-ttu-id="462dc-146">複製伺服器上的報表路徑。</span><span class="sxs-lookup"><span data-stu-id="462dc-146">Copy the report path on the server.</span></span> <span data-ttu-id="462dc-147">在此範例中，報表路徑為 `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`。</span><span class="sxs-lookup"><span data-stu-id="462dc-147">In the example, the report path is `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`.</span></span>  
  
3.  <span data-ttu-id="462dc-148">建立具有下列三個元件的新 URL：</span><span class="sxs-lookup"><span data-stu-id="462dc-148">Create a new URL with the following three components:</span></span>  
  
    -   <span data-ttu-id="462dc-149">報表伺服器上的報表檢視器： `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span><span class="sxs-lookup"><span data-stu-id="462dc-149">The report viewer on the report server: `http://localhost/ReportServer/Pages/ReportViewer.aspx?`</span></span>  
  
    -   <span data-ttu-id="462dc-150">您在步驟 1 中複製的報表名稱，例如： `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span><span class="sxs-lookup"><span data-stu-id="462dc-150">The name of the report you copied in step 1, for example: `%2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog`</span></span>  
  
    -   <span data-ttu-id="462dc-151">指定隱藏文件引導模式的裝置資訊參數： `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span><span class="sxs-lookup"><span data-stu-id="462dc-151">The device information parameters that specify hiding the document map: `&rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False`</span></span>  
  
     <span data-ttu-id="462dc-152">下列 URL 是由附加的三個元件所組成 (依據其列出的順序)。</span><span class="sxs-lookup"><span data-stu-id="462dc-152">The following URL consists of these three components appended in the order they are listed.</span></span>  
  
    ```  
    http://localhost/ReportServer/Pages/ReportViewer.aspx?  
    %2fAdventureWorks2012+Sample+Reports%2fProduct+Catalog  
    &rs%3aCommand=Render&rc%3aFormat=HTML4.0&rc%3aDocMap=False  
    ```  
  
     <span data-ttu-id="462dc-153">若要使用這個 URL，請複製它，並移除所有分行符號。</span><span class="sxs-lookup"><span data-stu-id="462dc-153">To use this URL, copy it and remove all line breaks.</span></span>  
  
4.  <span data-ttu-id="462dc-154">在報表管理員中貼上此 URL，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="462dc-154">Paste the URL in Report Manager, and then press ENTER.</span></span> <span data-ttu-id="462dc-155">報表便會執行，而且文件引導模式會隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="462dc-155">The report runs, and the document map is hidden.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="462dc-156"> 如需有關下載範例報表的詳細資訊，請參閱 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)。</span><span class="sxs-lookup"><span data-stu-id="462dc-156">For more information about downloading sample reports, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][Report Builder and Report Designer sample reports](https://go.microsoft.com/fwlink/?LinkId=198283).</span></span>  
>   
>  <span data-ttu-id="462dc-157">如需詳細資訊，請參閱《SQL Server 線上叢書》中 [Reporting Services 文件集](https://go.microsoft.com/fwlink/?linkid=121312) 的＜URL 存取＞。</span><span class="sxs-lookup"><span data-stu-id="462dc-157">For more information, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="462dc-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="462dc-158">See Also</span></span>  
 [<span data-ttu-id="462dc-159">在報表管理員中尋找及檢視報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="462dc-159">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
