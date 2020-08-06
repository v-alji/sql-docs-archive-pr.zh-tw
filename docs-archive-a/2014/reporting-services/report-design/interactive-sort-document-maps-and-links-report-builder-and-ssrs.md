---
title: 互動式排序、文件引導模式及連結 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cc6ef408-4a76-408a-9d3f-033481fe21cf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 35d88e89ed14a205153374d44562e6d3fda92e02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707106"
---
# <a name="interactive-sort-document-maps-and-links-report-builder-and-ssrs"></a><span data-ttu-id="9962c-102">互動式排序、文件引導模式及連結 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9962c-102">Interactive Sort, Document Maps, and Links (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9962c-103">在 Web 架構的環境中，您可以加入讓使用者與報表互動的一些功能。</span><span class="sxs-lookup"><span data-stu-id="9962c-103">In Web-based environments, you can add a number of features that let your users interact with reports.</span></span> <span data-ttu-id="9962c-104">您的使用者可以變更值在報表中的排序次序、顯示或隱藏報表中的項目，或者按一下跳到其他報表或網頁的連結。</span><span class="sxs-lookup"><span data-stu-id="9962c-104">Your users can change the sort order of values in your report, show or hide items in the report, or click links that go to other reports or Web pages.</span></span> <span data-ttu-id="9962c-105">您也可以加入目錄或文件引導模式。</span><span class="sxs-lookup"><span data-stu-id="9962c-105">You can also add a table of contents or document map.</span></span> <span data-ttu-id="9962c-106">您的報表使用者可以按一下目錄或文件引導模式中的項目，跳到報表內的各個區域。</span><span class="sxs-lookup"><span data-stu-id="9962c-106">Your report users can click items in the table of contents or document map to jump to areas within a report.</span></span>  
  
 <span data-ttu-id="9962c-107">報表產生器和報表設計師支援具有下列動作的三種連結類型：</span><span class="sxs-lookup"><span data-stu-id="9962c-107">Report Builder and Report Designer support three types of links with the following actions:</span></span>  
  
-   <span data-ttu-id="9962c-108">**書籤連結** ：跳至報表中的其他區域。</span><span class="sxs-lookup"><span data-stu-id="9962c-108">**Bookmark links** Jump to other areas within the report.</span></span>  
  
-   <span data-ttu-id="9962c-109">**超連結** ：使用 URL 存取跳至指定報表伺服器上網頁或報表位址的 URL。</span><span class="sxs-lookup"><span data-stu-id="9962c-109">**Hyperlinks** Jump to URLs that specify the address of Web pages or reports on a report server by using URL access.</span></span>  
  
-   <span data-ttu-id="9962c-110">**鑽研報表連結** ：跳至相同報表伺服器上的其他報表。</span><span class="sxs-lookup"><span data-stu-id="9962c-110">**Drillthrough report links** Jump to other reports on the same report server.</span></span> <span data-ttu-id="9962c-111">如需詳細資訊，請參閱[鑽研報表 &#40;報表產生器及 SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9962c-111">For more information, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9962c-112">繫結至資料集欄位的連結可能很容易受到惡意竄改。</span><span class="sxs-lookup"><span data-stu-id="9962c-112">Links that are bound to dataset fields can be vulnerable to tampering for malicious purposes.</span></span> <span data-ttu-id="9962c-113">如需詳細資訊，請參閱 msdn.microsoft.com 上《 [線上叢書》](../security/secure-reports-and-resources.md) 中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][保護報表和資源的安全](https://go.microsoft.com/fwlink/?LinkId=154888) 。</span><span class="sxs-lookup"><span data-stu-id="9962c-113">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="9962c-114">您也可以設計包含排序、篩選和可見性之參數參考的運算式，讓使用者控制報表顯示和內容。</span><span class="sxs-lookup"><span data-stu-id="9962c-114">You can also let your users control report display and content by designing expressions that include parameter references for sort, filter, and visibility.</span></span> <span data-ttu-id="9962c-115">如需詳細資訊，請參閱[報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md)、[篩選、分組和排序資料 &#40;報表產生器及 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) 和[新增資料集篩選、資料區域篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="9962c-115">For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md), [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md), and [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="9962c-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="9962c-116">In This Section</span></span>  
 [<span data-ttu-id="9962c-117">互動式排序 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9962c-117">Interactive Sort &#40;Report Builder and SSRS&#41;</span></span>](interactive-sort-report-builder-and-ssrs.md)  
 <span data-ttu-id="9962c-118">說明如何將互動式排序按鈕加入到資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="9962c-118">Explains how to add interactive sort buttons to column headers.</span></span>  
  
 [<span data-ttu-id="9962c-119">建立文件引導模式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9962c-119">Create a Document Map &#40;Report Builder and SSRS&#41;</span></span>](create-a-document-map-report-builder-and-ssrs.md)  
 <span data-ttu-id="9962c-120">說明如何加入目錄，以支援大型報表中的導覽。</span><span class="sxs-lookup"><span data-stu-id="9962c-120">Explains how to add a table of contents to support navigation in a large report.</span></span>  
  
 [<span data-ttu-id="9962c-121">將書籤加入至報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9962c-121">Add a Bookmark to a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-bookmark-to-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="9962c-122">說明如何加入書籤，以便在報表內建立連結。</span><span class="sxs-lookup"><span data-stu-id="9962c-122">Explains how to add bookmarks to create links within a report.</span></span>  
  
 [<span data-ttu-id="9962c-123">將超連結加入到 URL &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9962c-123">Add a Hyperlink to a URL &#40;Report Builder and SSRS&#41;</span></span>](add-a-hyperlink-to-a-url-report-builder-and-ssrs.md)  
 <span data-ttu-id="9962c-124">說明如何加入從報表至 URL 的連結</span><span class="sxs-lookup"><span data-stu-id="9962c-124">Explains how to add a link from your report to a URL</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9962c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9962c-125">See Also</span></span>  
 [<span data-ttu-id="9962c-126">鑽研、向下鑽研、子報表和巢狀資料區 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9962c-126">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
