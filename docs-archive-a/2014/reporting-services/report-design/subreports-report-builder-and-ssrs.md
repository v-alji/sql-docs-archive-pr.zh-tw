---
title: 子報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab5bea3a-109e-4c25-92d9-494df7c52dd8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ce30cf575148af11d6485125089beace07fd5429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585005"
---
# <a name="subreports-report-builder-and-ssrs"></a><span data-ttu-id="f833b-102">子報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f833b-102">Subreports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f833b-103">子報表是一個報表項目，會在主要報表的主體內顯示另一個報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-103">A subreport is a report item that displays another report inside the body of a main report.</span></span> <span data-ttu-id="f833b-104">報表中子報表的概念類似於網頁中的框架。</span><span class="sxs-lookup"><span data-stu-id="f833b-104">Conceptually, a subreport in a report is similar to a frame in a Web page.</span></span> <span data-ttu-id="f833b-105">它用於在報表中內嵌報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-105">It is used to embed a report within a report.</span></span> <span data-ttu-id="f833b-106">任何報表都可以做為子報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-106">Any report can be used as a subreport.</span></span> <span data-ttu-id="f833b-107">顯示為子報表的報表儲存在報表伺服器上，通常會與父報表儲存在同一個資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f833b-107">The report that is displayed as the subreport is stored on a report server, usually in the same folder as the parent report.</span></span> <span data-ttu-id="f833b-108">您可以設計父報表來傳遞參數給子報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-108">You can design the parent report to pass parameters to the subreport.</span></span> <span data-ttu-id="f833b-109">子報表可以在資料區域中重複，使用參數在每一個子報表執行個體中篩選資料。</span><span class="sxs-lookup"><span data-stu-id="f833b-109">A subreport can be repeated within data regions, using a parameter to filter data in each instance of the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f833b-110">如果您在 Tablix 資料區中使用子報表，則會針對每一個資料列來處理子報表和它的參數。</span><span class="sxs-lookup"><span data-stu-id="f833b-110">If you use a subreport in a tablix data region, the subreport and its parameters will be processed for every row.</span></span> <span data-ttu-id="f833b-111">如果存在許多資料列，請考慮是否使用鑽研報表會更適當。</span><span class="sxs-lookup"><span data-stu-id="f833b-111">If there are many rows, consider whether a drillthrough report is more appropriate.</span></span>  
  
 <span data-ttu-id="f833b-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span><span class="sxs-lookup"><span data-stu-id="f833b-112">![rs_Subreport](../media/rs-subreport.gif "rs_Subreport")</span></span>  
  
 <span data-ttu-id="f833b-113">在此圖中，[銷售訂單] 主報表中顯示的連絡資訊實際上來自 [連絡人] 子報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-113">In this illustration, the contact information displayed in the main Sales Order report actually comes from a Contacts subreport.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-subreports-and-nested-data-regions"></a><span data-ttu-id="f833b-114">比較子報表和巢狀資料區</span><span class="sxs-lookup"><span data-stu-id="f833b-114">Comparing Subreports and Nested Data Regions</span></span>  
 <span data-ttu-id="f833b-115">如果您想要使用子報表顯示不同群組的資料，請考慮改用資料區，例如資料表、矩陣和圖表。</span><span class="sxs-lookup"><span data-stu-id="f833b-115">If you're thinking of using subreports to display separate groups of data, consider using data regions, such as tables, matrices, and charts, instead.</span></span> <span data-ttu-id="f833b-116">只搭配資料區使用報表時，其執行效能可能會比包含子報表的報表更好。</span><span class="sxs-lookup"><span data-stu-id="f833b-116">Reports with data regions only may perform better than reports that include subreports.</span></span>  
  
 <span data-ttu-id="f833b-117">在單一資料區域內從相同的資料來源中巢狀資料群組時，請使用資料區域。</span><span class="sxs-lookup"><span data-stu-id="f833b-117">Use data regions to nest groups of data from the same data source within a single data region.</span></span> <span data-ttu-id="f833b-118">在單一資料區域內從不同的資料來源中巢狀資料群組，請使用子報表，重複使用多個父報表中的子報表，或是在另一個報表中顯示獨立報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-118">Use subreports to nest groups of data from different data sources within a single data region, reuse a subreport in multiple parent reports, or display a standalone report inside of another report.</span></span> <span data-ttu-id="f833b-119">例如，您可以在另一個報表主體中置放多個子報表，以建立「簡報書籍」。</span><span class="sxs-lookup"><span data-stu-id="f833b-119">For example, you can create a "briefing book" by placing multiple subreports inside the body of another report.</span></span>  
  
 <span data-ttu-id="f833b-120">資料區與子報表的功能和彈性相同，但效能更佳。</span><span class="sxs-lookup"><span data-stu-id="f833b-120">Data regions provide much of the same functionality and flexibility as subreports, but with better performance.</span></span> <span data-ttu-id="f833b-121">這是因為報表伺服器會將子報表的每一個執行個體，都視為獨立的報表來處理，所以可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="f833b-121">Because the report server processes each instance of a subreport as a separate report, performance can be impacted.</span></span> <span data-ttu-id="f833b-122">如需詳細資訊，請參閱 [巢狀資料區 &#40;報表產生器及 SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f833b-122">For more information, see [Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md).</span></span>  
  
## <a name="using-parameters-in-subreports"></a><span data-ttu-id="f833b-123">在子報表中使用參數</span><span class="sxs-lookup"><span data-stu-id="f833b-123">Using Parameters in Subreports</span></span>  
 <span data-ttu-id="f833b-124">若要從父報表傳遞參數至子報表，請在做為子報表使用的報表中定義一個報表參數。</span><span class="sxs-lookup"><span data-stu-id="f833b-124">To pass parameters from the parent report to the subreport, define a report parameter in the report that you use as the subreport.</span></span> <span data-ttu-id="f833b-125">當您在父報表中放置子報表時，您可以選取報表參數，以及要從父報表中傳遞給子報表中之報表參數的值。</span><span class="sxs-lookup"><span data-stu-id="f833b-125">When you place the subreport in the parent report, you can select the report parameter and a value to pass from the parent report to the report parameter in the subreport.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f833b-126">您從子報表選取的參數是報表參數，而非查詢參數。</span><span class="sxs-lookup"><span data-stu-id="f833b-126">The parameter that you select from the subreport is a report parameter, not a query parameter.</span></span>  
  
 <span data-ttu-id="f833b-127">您可以在報表主體或資料區域中放置一個子報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-127">You can place a subreport in the main body of the report, or in a data region.</span></span> <span data-ttu-id="f833b-128">如果您在資料區域中放置一個子報表，子報表將在資料區域中重複群組或資料列的每一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="f833b-128">If you place a subreport in a data region, the subreport will repeat with each instance of the group or row in the data region.</span></span> <span data-ttu-id="f833b-129">若要從群組或資料列傳遞值給子報表，請在子報表值屬性中，針對包含要傳遞給子報表參數的值欄位，使用欄位運算式。</span><span class="sxs-lookup"><span data-stu-id="f833b-129">To pass a value from the group or row to the subreport, in the subreport value property, use a field expression for the field containing the value you want to pass to the subreport parameter.</span></span>  
  
 <span data-ttu-id="f833b-130">如需使用子報表的詳細資訊，請參閱[新增子報表和參數 &#40;報表產生器及 SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f833b-130">For more information about working with subreports, see [Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md).</span></span>  
  
## <a name="specifying-subreport-names-and-locations"></a><span data-ttu-id="f833b-131">指定子報表名稱和位置</span><span class="sxs-lookup"><span data-stu-id="f833b-131">Specifying Subreport Names and Locations</span></span>  
 <span data-ttu-id="f833b-132">您可以設計主報表，以便在相同報表伺服器上的不同資料夾中指定子報表。</span><span class="sxs-lookup"><span data-stu-id="f833b-132">You can design a main report to specify a subreport in a different folder on the same report server.</span></span>  
  
 <span data-ttu-id="f833b-133">您用來指定子報表的語法，取決於報表伺服器處於原生模式或 SharePoint 整合模式而定。</span><span class="sxs-lookup"><span data-stu-id="f833b-133">The syntax you use to specify the subreport depends on whether the report server is in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="f833b-134">如需詳細資訊，請參閱[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f833b-134">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="f833b-135">在報表產生器中，若要預覽主報表中的子報表，則兩個報表都必須位在相同的報表伺服器上，或者您必須指定子報表的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="f833b-135">In Report Builder, to preview a subreport in a main report, both reports must be located in the same report server, or you must specify a full path to the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f833b-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f833b-136">See Also</span></span>  
 [<span data-ttu-id="f833b-137">鑽研、向下鑽研、子報表和巢狀資料區 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f833b-137">Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;</span></span>](drillthrough-drilldown-subreports-and-nested-data-regions.md)  
  
  
