---
title: 列印報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4bad1b6e-7d94-4b17-9502-ccd3dce0fdd9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3004734226e67ec435e90a4e62895c94173b23d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593328"
---
# <a name="print-reports-report-builder-and-ssrs"></a><span data-ttu-id="6758d-102">列印報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6758d-102">Print Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6758d-103">將報表儲存至報表伺服器之後，您就可以從瀏覽器、報表管理員或任何用來檢視所匯出報表的應用程式，檢視及列印報表。</span><span class="sxs-lookup"><span data-stu-id="6758d-103">After you save a report to a report server, you can view and print the report from a browser, Report Manager, or any application that you use to view an exported report.</span></span> <span data-ttu-id="6758d-104">儲存報表之前，您可以在預覽報表時將它列印出來。</span><span class="sxs-lookup"><span data-stu-id="6758d-104">Before saving a report, you can print it when you preview it.</span></span>  
  
 <span data-ttu-id="6758d-105">所有列印程序都可以視需要，直接在用戶端電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="6758d-105">All print processing is performed on demand and on the client computer.</span></span> <span data-ttu-id="6758d-106">目前沒有伺服器端列印功能，可讓您從報表伺服器直接將列印工作傳送到連接 Web 伺服器的印表機。</span><span class="sxs-lookup"><span data-stu-id="6758d-106">There is no server-side print functionality that enables you to route a print job directly from a report server to a printer that is attached to the Web server.</span></span> <span data-ttu-id="6758d-107">印表機及列印選項是由個別的報表使用者，透過標準 **[列印]** 對話方塊加以選取。</span><span class="sxs-lookup"><span data-stu-id="6758d-107">Printers and print options are selected by individual report users by using a standard **Print** dialog box.</span></span>  
  
 <span data-ttu-id="6758d-108">特別為列印輸出設計報表的作者，可以使用分頁符號、頁首和頁尾、運算式和背景影像，來建立列印專用的報表設計。</span><span class="sxs-lookup"><span data-stu-id="6758d-108">Report authors who design reports specifically for print output can use page breaks, page headers and footers, expressions, and background images to create a print-based design.</span></span> <span data-ttu-id="6758d-109">供列印輸出使用的報表設計元素的範例，包括要列印在每一份報表背面的條款，或是模擬信頭的圖形和文字元素。</span><span class="sxs-lookup"><span data-stu-id="6758d-109">Examples of report design elements intended for print output might include terms and conditions that you print on the back of every report, or graphic and text elements that mimic letterhead.</span></span>  
  
 <span data-ttu-id="6758d-110">由於不同轉譯格式實作的分頁方式有所不同，您可能無法使每一份報表的每一種轉譯格式達到最佳列印輸出結果。</span><span class="sxs-lookup"><span data-stu-id="6758d-110">Due to the way pagination is implemented for different rendering formats, you might not be able to achieve optimum print output results for every report in every rendering format.</span></span> <span data-ttu-id="6758d-111">下列清單將提供範例：</span><span class="sxs-lookup"><span data-stu-id="6758d-111">The following list provides examples:</span></span>  
  
1.  <span data-ttu-id="6758d-112">報表頁面是為了容納不同資料量而設計的。</span><span class="sxs-lookup"><span data-stu-id="6758d-112">Report pages are designed to accommodate variable amounts of data.</span></span> <span data-ttu-id="6758d-113">例如，依據使用者是否以互動方式切換資料列和資料行而定，包括矩陣的報表可能會造成頁面的橫向與縱向成長。</span><span class="sxs-lookup"><span data-stu-id="6758d-113">Reports that include a matrix, for example, can cause a page to grow both horizontally and vertically depending on whether a user interactively toggles rows and columns.</span></span> <span data-ttu-id="6758d-114">未擴充矩陣的使用者得到的列印結果，將與有擴充矩陣的使用者不同。</span><span class="sxs-lookup"><span data-stu-id="6758d-114">A user who does not expand a matrix will get different print results than a user who does.</span></span>  
  
2.  <span data-ttu-id="6758d-115">您無法在相同的報表中，合併橫向和縱向模式的頁面，也無法建立列印配置來取代在瀏覽器或其他應用程式中轉譯的報表配置或與之並存。</span><span class="sxs-lookup"><span data-stu-id="6758d-115">You cannot combine landscape and portrait mode pages in the same report, nor is there a way to create a print-based layout that replaces or exists alongside the layout of a report as rendered in a browser or other application.</span></span>  
  
3.  <span data-ttu-id="6758d-116">就大部分的匯出報表而言，報表列印輸出會包括報表上顯示的所有內容，如使用者在電腦螢幕上看到的一樣。</span><span class="sxs-lookup"><span data-stu-id="6758d-116">For most exported reports, report printouts include everything that is visible on the report, as viewed by the user on a computer monitor.</span></span> <span data-ttu-id="6758d-117">系統會保留報表設計介面中的空白。</span><span class="sxs-lookup"><span data-stu-id="6758d-117">White space from the report design surface is preserved.</span></span> <span data-ttu-id="6758d-118">若要以水平方式加入或移除額外的空白頁面，請變更報表頁面寬度。</span><span class="sxs-lookup"><span data-stu-id="6758d-118">To add or remove extra blank pages horizontally, change the report page width.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6758d-119">如果您使用瀏覽器的 [列印] 命令，則 HTML 報表列印輸出可能只會包含第一頁的內容。</span><span class="sxs-lookup"><span data-stu-id="6758d-119">HTML report printouts may contain only the content on the first page if you are using the browser's Print command.</span></span> <span data-ttu-id="6758d-120">如果您使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 用戶端列印功能來列印 HTML 報表，可以獲得較好的結果。</span><span class="sxs-lookup"><span data-stu-id="6758d-120">You can achieve better results if you print HTML reports using the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] client printing functionality.</span></span> <span data-ttu-id="6758d-121">如需詳細資訊，請參閱 [使用列印控制項從瀏覽器列印報表 &#40;報表產生器及 SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="6758d-121">For more information, see [Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="6758d-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="6758d-122">In This Section</span></span>  
 [<span data-ttu-id="6758d-123">使用列印控制項從瀏覽器列印報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6758d-123">Print Reports from a Browser with the Print Control &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)  
 <span data-ttu-id="6758d-124">描述如何使用用戶端列印功能，從網頁瀏覽器或報表管理員進行報表的列印。</span><span class="sxs-lookup"><span data-stu-id="6758d-124">Describes how to use client-side printing to print reports from your Web browser or Report Manager.</span></span>  
  
 [<span data-ttu-id="6758d-125">從其他應用程式列印報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6758d-125">Print Reports from Other Applications &#40;Report Builder and SSRS&#41;</span></span>](print-reports-from-other-applications-report-builder-and-ssrs.md)  
 <span data-ttu-id="6758d-126">描述如何列印已匯出至另一個應用程式的報表。</span><span class="sxs-lookup"><span data-stu-id="6758d-126">Describes how to print reports exported to another application.</span></span>  
  
 [<span data-ttu-id="6758d-127">列印報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6758d-127">Print a Report &#40;Report Builder and SSRS&#41;</span></span>](print-a-report-report-builder-and-ssrs.md)  
 <span data-ttu-id="6758d-128">提供逐步指示，說明如何列印報表、如何控制頁面邊界，以及如何針對手動分頁轉譯器 (PDF、影像或列印) 所轉譯的報表指定紙張大小。</span><span class="sxs-lookup"><span data-stu-id="6758d-128">Provides step-by-step instructions on how to print a report, how to control the margins on a page, and on how to specify the paper size for reports that will be rendered by hard-page break renderers: PDF, Image, or Print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6758d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6758d-129">See Also</span></span>  
 <span data-ttu-id="6758d-130">[匯出報表 &#40;報表產生器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6758d-130">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6758d-131">[頁首和頁尾 &#40;報表產生器和 SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6758d-131">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](../report-design/page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6758d-132">[&#40;報表產生器和 SSRS&#41;的影像](../report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6758d-132">[Images &#40;Report Builder and SSRS&#41;](../report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6758d-133">Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6758d-133">Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;</span></span>](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)  
  
  
