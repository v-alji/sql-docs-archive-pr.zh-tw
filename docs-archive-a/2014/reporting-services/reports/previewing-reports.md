---
title: 預覽報表
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: fb068937efff71667d7f73c8e7ecd4d9ebfa576b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593287"
---
# <a name="preview-reports-in-sql-server-reporting-services-ssrs"></a><span data-ttu-id="54e00-102">在 SQL Server Reporting Services (SSRS) 中預覽報表</span><span class="sxs-lookup"><span data-stu-id="54e00-102">Preview Reports in SQL Server Reporting Services (SSRS)</span></span>

  <span data-ttu-id="54e00-103">設計報表時，在尚未發行至實際環境之前，您可能會想要先檢視該報表。</span><span class="sxs-lookup"><span data-stu-id="54e00-103">When you design a report, you may want to view it before publishing it to a production environment.</span></span> <span data-ttu-id="54e00-104">您可以利用數種方式進行檢視：在報表設計師中切換到 [預覽] 模式、使用報表設計師中的預覽視窗，以及在測試環境中將報表發行至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="54e00-104">You can do this in several ways: by switching to Preview mode in Report Designer, by using the preview window in Report Designer, and by publishing the report to a report server in a test environment.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="54e00-105">預覽報表時，報表的資料會快取至本機電腦上的檔案。</span><span class="sxs-lookup"><span data-stu-id="54e00-105">When you preview a report, the data for the report is cached to a file on the local computer.</span></span> <span data-ttu-id="54e00-106">當您再次預覽同一份報表時 (使用相同的查詢、參數和認證)，報表設計師會擷取快取複本，而非重新執行查詢。</span><span class="sxs-lookup"><span data-stu-id="54e00-106">When you preview the same report again using the same query, parameters, and credentials, Report Designer retrieves the cached copy rather than rerunning the query.</span></span> <span data-ttu-id="54e00-107">資料檔案會儲存為 *\<reportname>* .rdl。與報表定義檔案位於相同目錄中的資料。</span><span class="sxs-lookup"><span data-stu-id="54e00-107">The data file is saved as *\<reportname>*.rdl.data in the same directory as the report definition file.</span></span> <span data-ttu-id="54e00-108">您關閉報表設計師時，不會刪除此檔案。</span><span class="sxs-lookup"><span data-stu-id="54e00-108">The file is not deleted when you close Report Designer.</span></span>  
  
## <a name="preview-mode"></a><span data-ttu-id="54e00-109">預覽模式</span><span class="sxs-lookup"><span data-stu-id="54e00-109">Preview Mode</span></span>

 <span data-ttu-id="54e00-110">您可以按一下 [**預覽**]，在報表設計師中預覽報表。</span><span class="sxs-lookup"><span data-stu-id="54e00-110">You can preview a report in Report Designer by clicking **Preview**.</span></span> <span data-ttu-id="54e00-111">這會在本機執行報表，使用與報表伺服器相同的報表處理與轉譯功能。</span><span class="sxs-lookup"><span data-stu-id="54e00-111">This runs the report locally, using the same report processing and rendering functionality that is provided with the report server.</span></span> <span data-ttu-id="54e00-112">顯示的報表是互動式影像；您可以選取參數、按一下連結、檢視文件引導模式，以及展開和摺疊報表的隱藏區域。</span><span class="sxs-lookup"><span data-stu-id="54e00-112">The report that is displayed is an interactive image; you can select parameters, click links, view the document map, and expand and collapse hidden areas of the report.</span></span> <span data-ttu-id="54e00-113">您也可以將報表匯出至任何已安裝的轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="54e00-113">You can also export the report to any of the installed rendering formats.</span></span>  
  
## <a name="standalone-preview"></a><span data-ttu-id="54e00-114">獨立預覽</span><span class="sxs-lookup"><span data-stu-id="54e00-114">Standalone Preview</span></span>

 <span data-ttu-id="54e00-115">另一個預覽報表的方式是在偵錯組態下執行報表專案，例如，偵錯您撰寫的自訂組件。</span><span class="sxs-lookup"><span data-stu-id="54e00-115">Another way to preview a report is to run the report project in a debug configuration, for example, to debug custom assemblies that you write.</span></span> <span data-ttu-id="54e00-116">有三種方法可以執行專案：</span><span class="sxs-lookup"><span data-stu-id="54e00-116">There are three ways to run a project:</span></span>  
  
- <span data-ttu-id="54e00-117">按一下 [**調試**程式] 功能表上的 [**啟動**]。</span><span class="sxs-lookup"><span data-stu-id="54e00-117">By clicking **Start** on the **Debug** menu.</span></span>  
  
- <span data-ttu-id="54e00-118">按一下 [標準] 工具列上的 [**啟動**] 按鈕 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="54e00-118">By clicking the **Start** button on the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] standard toolbar.</span></span>  
  
- <span data-ttu-id="54e00-119">可按下 F5。</span><span class="sxs-lookup"><span data-stu-id="54e00-119">By pressing F5.</span></span>  
  
 <span data-ttu-id="54e00-120">如果您使用建立報表但是未部署報表的專案組態，則在目前組態之 `StartItem` 屬性中所指定的報表，會在另一個預覽視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="54e00-120">If you use a project configuration that builds the report but does not deploy it, the report that is specified in the `StartItem` property of the current configuration opens in a separate preview window.</span></span> <span data-ttu-id="54e00-121">預覽視窗顯示報表的方式和功能都與 [預覽] 模式相同。</span><span class="sxs-lookup"><span data-stu-id="54e00-121">The preview window displays the report in the same way and has the same functionality as Preview mode.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="54e00-122">在偵錯報表之前，您必須設定一個啟動項目。</span><span class="sxs-lookup"><span data-stu-id="54e00-122">Before debugging a report, you must set a start item.</span></span> <span data-ttu-id="54e00-123">若要設定起始專案，請在方案總管中，以滑鼠右鍵按一下報表專案，再按一下 [**屬性**]，然後在中 `StartItem` 選取要顯示的報表名稱。</span><span class="sxs-lookup"><span data-stu-id="54e00-123">To set a start item, in Solution Explorer, right-click the report project, click **Properties**, and then in `StartItem`, select the name of the report to display.</span></span>  
  
 <span data-ttu-id="54e00-124">如果您想要預覽並非專案之啟動項目的特定報表，請選取建立報表但未部署報表的組態 (例如 DebugLocal 組態)，以滑鼠右鍵按一下報表，然後按一下 [執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="54e00-124">If you wish to preview a particular report that is not the start item for the project, select a configuration that builds the report but does not deploy it (for example, the DebugLocal configuration), right-click the report, and then click **Run**.</span></span> <span data-ttu-id="54e00-125">您必須選擇並未部署報表的組態；否則，報表將會發行至報表伺服器，而非在本機的預覽視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="54e00-125">You must choose a configuration that does not deploy the report; otherwise, the report will be published to the report server instead of displayed locally in a preview window.</span></span>  
  
## <a name="print-preview"></a><span data-ttu-id="54e00-126">預覽列印</span><span class="sxs-lookup"><span data-stu-id="54e00-126">Print Preview</span></span>

 <span data-ttu-id="54e00-127">當您第一次在 [預覽] 模式或預覽視窗中檢視報表時，報表的檢視類似於 HTML 轉譯延伸模組所產生的報表。</span><span class="sxs-lookup"><span data-stu-id="54e00-127">When you first view a report on in Preview mode or in the preview window, the view of the report resembles a report produced by the HTML rendering extension.</span></span> <span data-ttu-id="54e00-128">這個預覽並不是 HTML，不過報表的配置及分頁與 HTML 的輸出相似。</span><span class="sxs-lookup"><span data-stu-id="54e00-128">The preview is not HTML, but the layout and pagination of the report is similar to HTML output.</span></span>  
  
 <span data-ttu-id="54e00-129">您可以切換到預覽列印模式，以變更檢視來顯示列印的報表。</span><span class="sxs-lookup"><span data-stu-id="54e00-129">You can change the view to represent a printed report by switching to print preview mode.</span></span> <span data-ttu-id="54e00-130">按一下預覽工具列上的 **[預覽列印]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="54e00-130">Click the **Print Preview** button on the preview toolbar.</span></span> <span data-ttu-id="54e00-131">所顯示的報表就如同在實際頁面上所看到的。</span><span class="sxs-lookup"><span data-stu-id="54e00-131">The report will display as though it were on a physical page.</span></span> <span data-ttu-id="54e00-132">這個檢視與影像和 PDF 轉譯延伸模組所產生的輸出類似。</span><span class="sxs-lookup"><span data-stu-id="54e00-132">This view resembles the output produced by the Image and PDF rendering extensions.</span></span> <span data-ttu-id="54e00-133">預覽列印並不是影像或 PDF 檔案，不過報表的配置及分頁與這些格式的輸出相似。</span><span class="sxs-lookup"><span data-stu-id="54e00-133">Print preview is not an image or PDF file, but the layout and pagination of the report is similar the output in those formats.</span></span>  
  
## <a name="publish-to-a-test-server"></a><span data-ttu-id="54e00-134">發佈至測試伺服器</span><span class="sxs-lookup"><span data-stu-id="54e00-134">Publish to a Test Server</span></span>

 <span data-ttu-id="54e00-135">您也可以將報表發行至測試伺服器來測試報表。</span><span class="sxs-lookup"><span data-stu-id="54e00-135">You can also test reports by publishing them to a test server.</span></span> <span data-ttu-id="54e00-136">將報表發行至測試伺服器與發行至實際伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="54e00-136">Publishing a report to a test server is the same as publishing to a production server.</span></span> <span data-ttu-id="54e00-137">如需發行報表的詳細資訊，請參閱 [將報表發行至報表伺服器](publishing-reports-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="54e00-137">For information about publishing a report, see [Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="54e00-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="54e00-138">Next steps</span></span>

 - [<span data-ttu-id="54e00-139">列印報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="54e00-139">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)
 - [<span data-ttu-id="54e00-140">列印報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="54e00-140">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-a-report-report-builder-and-ssrs.md)
 - [<span data-ttu-id="54e00-141">發行報表</span><span class="sxs-lookup"><span data-stu-id="54e00-141">Publish Reports</span></span>](../publish-reports.md)
 - [<span data-ttu-id="54e00-142">將自訂組件與報表搭配使用</span><span class="sxs-lookup"><span data-stu-id="54e00-142">Using Custom Assemblies with Reports</span></span>](../custom-assemblies/using-custom-assemblies-with-reports.md)