---
title: 列印報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b96936c9-c387-41a9-8c19-6eb325769ffd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe029019cdf9739153256db399cfa1426d3ba632
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593832"
---
# <a name="print-a-report-report-builder-and-ssrs"></a><span data-ttu-id="768ef-102">列印報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="768ef-102">Print a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="768ef-103">將報表儲存至報表伺服器之後，您就可以從瀏覽器、報表管理員或任何用來檢視所匯出報表的應用程式，檢視及列印報表。</span><span class="sxs-lookup"><span data-stu-id="768ef-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="768ef-104">儲存報表之前，您可以在預覽報表時將它列印出來。</span><span class="sxs-lookup"><span data-stu-id="768ef-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="768ef-105">當您列印報表時，可以指定所要使用的紙張大小。</span><span class="sxs-lookup"><span data-stu-id="768ef-105">When you print a report, you can specify the size of the paper to use.</span></span> <span data-ttu-id="768ef-106">紙張大小會決定報表中的頁數及哪些報表資料適合每一頁的大小。</span><span class="sxs-lookup"><span data-stu-id="768ef-106">The size of the paper determines the number of pages in a report and which report data fits on each page.</span></span> <span data-ttu-id="768ef-107">紙張大小只會影響以硬分頁轉譯器所轉譯的報表：PDF、影像和列印。</span><span class="sxs-lookup"><span data-stu-id="768ef-107">Paper size affects only reports that are rendered with hard page-break renders: PDF, Image, and Print.</span></span> <span data-ttu-id="768ef-108">設定紙張大小對於其他轉譯器沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="768ef-108">Setting the paper size has no effect on other renderers.</span></span> <span data-ttu-id="768ef-109">如需詳細資訊，請參閱[轉譯行為 &#40;報表產生器及 SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="768ef-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="768ef-110">您可以從報表管理員中的報表檢視器工具列或報表產生器中的預覽，將報表匯出到手動分頁轉譯器，或是按一下 [列印] 按鈕來列印報表的複本。</span><span class="sxs-lookup"><span data-stu-id="768ef-110">From the report viewer toolbar in Report Manager or in preview in Report Builder, you can export a report to a hard page-break renderer or click the Print button to print a copy of the report.</span></span> <span data-ttu-id="768ef-111">您可能需要設定紙張大小或是其他版面設定屬性。</span><span class="sxs-lookup"><span data-stu-id="768ef-111">You might need to set the paper size or other page setup properties.</span></span> <span data-ttu-id="768ef-112">使用 **[報表屬性]** 對話方塊可變更版面設定屬性，包括紙張大小。</span><span class="sxs-lookup"><span data-stu-id="768ef-112">Use the **Report Properties** dialog box to change page setup properties, including paper size.</span></span>  
  
 <span data-ttu-id="768ef-113">您可以在兩個不同位置中指定列印頁面邊界：設計模式和執行模式。</span><span class="sxs-lookup"><span data-stu-id="768ef-113">You can specify print page margins in two different locations: in design mode and in run mode.</span></span>  
  
-   <span data-ttu-id="768ef-114">**設計模式。**</span><span class="sxs-lookup"><span data-stu-id="768ef-114">**Design mode.**</span></span> <span data-ttu-id="768ef-115">當您在設計模式中設定頁面邊界時，這些設定就會在您儲存報表時儲存在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="768ef-115">When you set page margins in design mode, these settings are saved in the report definition when you save the report.</span></span>  
  
-   <span data-ttu-id="768ef-116">**執行模式。**</span><span class="sxs-lookup"><span data-stu-id="768ef-116">**Run mode.**</span></span> <span data-ttu-id="768ef-117">當您在執行模式中設定頁面邊界時，這項資訊不會儲存在報表定義中。</span><span class="sxs-lookup"><span data-stu-id="768ef-117">When you set page margins in run mode, this information is not saved in the report definition.</span></span> <span data-ttu-id="768ef-118">下次列印報表時，除非您再次指定列印邊界，否則將會從報表定義中取得設定。</span><span class="sxs-lookup"><span data-stu-id="768ef-118">The next time you print the report, you will get the settings from the report definition, unless you indicate your print margins again.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="768ef-119">在設計或執行模式中，不會顯示列印邊界。</span><span class="sxs-lookup"><span data-stu-id="768ef-119">Print margins are not displayed in design or run modes.</span></span> <span data-ttu-id="768ef-120">設計介面區域與報表的列印區域之間沒有任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="768ef-120">There is no relationship between the design surface area and the print area of your report.</span></span> <span data-ttu-id="768ef-121">若要查看列印邊界，請在執行模式中，於 [功能區] 的 **[執行]** 索引標籤上，按一下 [整頁模式]。</span><span class="sxs-lookup"><span data-stu-id="768ef-121">To see print margins, in run mode, click Print Layout on the **Run** tab on the Ribbon.</span></span>  
  
 <span data-ttu-id="768ef-122">如需報表分頁的詳細資訊，請參閱 [Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="768ef-122">For more information about report paging, see [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-print-a-report-in-report-builder"></a><span data-ttu-id="768ef-123">在報表產生器中列印報表</span><span class="sxs-lookup"><span data-stu-id="768ef-123">To print a report in Report Builder</span></span>  
  
1.  <span data-ttu-id="768ef-124">開啟報表。</span><span class="sxs-lookup"><span data-stu-id="768ef-124">Open a report.</span></span>  
  
2.  <span data-ttu-id="768ef-125">在 [首頁] 索引標籤上，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="768ef-125">On the Home tab, click **Run**.</span></span>  
  
3.  <span data-ttu-id="768ef-126">(選擇性) 按一下 [整頁模式]\*\*\*\* 查看報表列印時的外觀。</span><span class="sxs-lookup"><span data-stu-id="768ef-126">(optional) Click **Print Layout** to see how the report will look when it is printed.</span></span>  
  
4.  <span data-ttu-id="768ef-127">(選擇性) 按一下 [版面設定]\*\*\*\* 設定紙張、方向與邊界。</span><span class="sxs-lookup"><span data-stu-id="768ef-127">(optional) Click **Page Setup** to set paper, orientation, and margins.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="768ef-128">這些設定的預設值來自 [設計] 檢視中所設定的報表屬性。</span><span class="sxs-lookup"><span data-stu-id="768ef-128">The default values for these come from the report properties, which are set in Design view.</span></span> <span data-ttu-id="768ef-129">您在 **[版面設定]** 對話方塊中設定的值只會用於此工作階段。</span><span class="sxs-lookup"><span data-stu-id="768ef-129">The values you set here in the **Page Setup** dialog box are for this session only.</span></span> <span data-ttu-id="768ef-130">當您關閉這份報表並重新開啟時，它就會再次具有預設值。</span><span class="sxs-lookup"><span data-stu-id="768ef-130">When you close this report and reopen it, it will have the default values again.</span></span>  
  
5.  <span data-ttu-id="768ef-131">按一下 **[列印]**。</span><span class="sxs-lookup"><span data-stu-id="768ef-131">Click **Print**.</span></span>  
  
6.  <span data-ttu-id="768ef-132">在 **[列印]** 對話方塊中，選取印表機並指定其他列印選項。</span><span class="sxs-lookup"><span data-stu-id="768ef-132">In the **Print** dialog box, select a printer and specify other printing options.</span></span>  
  
### <a name="to-print-a-report-from-a-web-browser-application"></a><span data-ttu-id="768ef-133">若要從網頁瀏覽器應用程式列印報表</span><span class="sxs-lookup"><span data-stu-id="768ef-133">To print a report from a Web browser application</span></span>  
  
1.  <span data-ttu-id="768ef-134">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="768ef-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="768ef-135">在報表管理員中，導覽到您要列印的報表。</span><span class="sxs-lookup"><span data-stu-id="768ef-135">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="768ef-136">開啟報表。</span><span class="sxs-lookup"><span data-stu-id="768ef-136">Open the report.</span></span>  
  
3.  <span data-ttu-id="768ef-137">在報表頂端的工具列上，按一下 **[列印]** 。</span><span class="sxs-lookup"><span data-stu-id="768ef-137">On the toolbar at the top of the report, click **Print**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="768ef-138">您第一次列印 HTML 報表時，報表伺服器會提示您安裝用於列印的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="768ef-138">The first time you print an HTML report, the report server prompts you to install an ActiveX control used for printing.</span></span> <span data-ttu-id="768ef-139">您必須安裝並設定控制項才能列印。</span><span class="sxs-lookup"><span data-stu-id="768ef-139">You must install and configure the control to print.</span></span>  
  
4.  <span data-ttu-id="768ef-140">在 **[列印]** 對話方塊中，選取一個印表機，然後按一下 **[列印]** 。</span><span class="sxs-lookup"><span data-stu-id="768ef-140">In the **Print** dialog box, select a printer, and then click **Prin**t.</span></span>  
  
### <a name="to-print-a-report-from-other-applications"></a><span data-ttu-id="768ef-141">若要從其他應用程式列印報表</span><span class="sxs-lookup"><span data-stu-id="768ef-141">To print a report from other applications</span></span>  
  
1.  <span data-ttu-id="768ef-142">在報表管理員中，導覽到您要列印的報表。</span><span class="sxs-lookup"><span data-stu-id="768ef-142">In Report Manager, navigate to the report that you want to print.</span></span> <span data-ttu-id="768ef-143">開啟報表。</span><span class="sxs-lookup"><span data-stu-id="768ef-143">Open the report.</span></span>  
  
2.  <span data-ttu-id="768ef-144">在報表頂端的工具列上，選取一種轉譯格式，然後按一下 **[匯出]** 。</span><span class="sxs-lookup"><span data-stu-id="768ef-144">On the toolbar at the top of the report, select a rendering format, and then click **Export**.</span></span> <span data-ttu-id="768ef-145">報表會在對應至轉譯格式的檢視器應用程式中開啟。</span><span class="sxs-lookup"><span data-stu-id="768ef-145">The report opens in a viewer application that corresponds to the rendering format.</span></span>  
  
     <span data-ttu-id="768ef-146">例如，如果您選取 PDF，則報表會在 Adobe Acrobat Reader 中開啟。</span><span class="sxs-lookup"><span data-stu-id="768ef-146">For example, if you select PDF, the report opens in Adobe Acrobat Reader.</span></span>  
  
3.  <span data-ttu-id="768ef-147">在該程式的 **[檔案]** 功能表上，按一下 **[列印]** 。</span><span class="sxs-lookup"><span data-stu-id="768ef-147">On the **File** menu in that program, click **Print**.</span></span>  
  
### <a name="to-change-paper-size"></a><span data-ttu-id="768ef-148">變更紙張大小</span><span class="sxs-lookup"><span data-stu-id="768ef-148">To change paper size</span></span>  
  
1.  <span data-ttu-id="768ef-149">以滑鼠右鍵按一下報表主體的外面，然後按一下 [報表屬性]  。</span><span class="sxs-lookup"><span data-stu-id="768ef-149">Right-click outside of the report body and click **Report Properties**.</span></span>  
  
2.  <span data-ttu-id="768ef-150">在 **[版面設定]** 中，從 **[紙張大小]** 清單選取一個值。</span><span class="sxs-lookup"><span data-stu-id="768ef-150">In **Page Setup**, select a value from the **Paper Size** list.</span></span> <span data-ttu-id="768ef-151">每個選項都會填入 **[寬度]** 和 **[高度]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="768ef-151">Each option populates the **Width** and **Height** properties.</span></span> <span data-ttu-id="768ef-152">您也可以指定自訂大小，其方式是在 **[寬度]** 和 **[高度]** 方塊內輸入數值。</span><span class="sxs-lookup"><span data-stu-id="768ef-152">You can also specify a custom size by typing numeric values in the **Width** and **Height** boxes.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="768ef-153">大小值的預設單位視使用者的地區設定而定。</span><span class="sxs-lookup"><span data-stu-id="768ef-153">Size values have a default unit based on the user's locale settings.</span></span> <span data-ttu-id="768ef-154">若要指定不同的單位，請在數值後面輸入一個實體單位指示項，例如 cm、mm、pt 或 pc。</span><span class="sxs-lookup"><span data-stu-id="768ef-154">To designate a different unit, type a physical unit designator such as cm, mm, pt, or pc after the numeric value.</span></span>  
  
### <a name="to-set-page-margins-in-design-mode"></a><span data-ttu-id="768ef-155">在設計模式中設定頁面邊界</span><span class="sxs-lookup"><span data-stu-id="768ef-155">To set page margins in design mode</span></span>  
  
-   <span data-ttu-id="768ef-156">以滑鼠右鍵按一下設計介面周圍的藍色區域，按一下 [報表屬性]  ，然後按一下 [版面設定]  頁面。</span><span class="sxs-lookup"><span data-stu-id="768ef-156">Right-click the blue area around the design surface, click **Report Properties**, and then click the **Page Setup** page.</span></span>  
  
### <a name="to-set-page-margins-in-run-mode"></a><span data-ttu-id="768ef-157">若要在執行模式中設定頁面邊界</span><span class="sxs-lookup"><span data-stu-id="768ef-157">To set page margins in run mode</span></span>  
  
-   <span data-ttu-id="768ef-158">按一下 **[執行]** 索引標籤上的 **[版面設定]** 。</span><span class="sxs-lookup"><span data-stu-id="768ef-158">Click **Page Setup** on the **Run** tab.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768ef-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="768ef-159">See Also</span></span>  
 <span data-ttu-id="768ef-160">[列印報表 &#40;報表產生器及 SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="768ef-160">[Print Reports &#40;Report Builder and SSRS&#41;](print-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="768ef-161">[匯出報表 &#40;報表產生器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="768ef-161">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="768ef-162">[報表屬性對話方塊、版面設定 &#40;報表產生器&#41;](../report-properties-dialog-box-page-setup-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="768ef-162">[Report Properties Dialog Box, Page Setup &#40;Report Builder&#41;](../report-properties-dialog-box-page-setup-report-builder.md) </span></span>  
 [<span data-ttu-id="768ef-163">報表設計檢視 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="768ef-163">Report Design View &#40;Report Builder&#41;</span></span>](report-design-view-report-builder.md)  
  
  
