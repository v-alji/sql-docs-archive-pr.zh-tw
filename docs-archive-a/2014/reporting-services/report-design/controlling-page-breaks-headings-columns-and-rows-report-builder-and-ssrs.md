---
title: 控制分頁符號、標題、資料行和資料列 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8fa41f-a727-4f23-8efb-fd9bb0d4cd1d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7dae06129ee5dc9962538e8d025dca9966325f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598211"
---
# <a name="controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs"></a><span data-ttu-id="798ae-102">控制分頁符號、標題、資料行和資料列 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="798ae-102">Controlling Page Breaks, Headings, Columns, and Rows (Report Builder and SSRS)</span></span>
  <span data-ttu-id="798ae-103">分頁符號可以將報表分割成不同的頁面進行檢視和列印。</span><span class="sxs-lookup"><span data-stu-id="798ae-103">A page break divides a report into separate pages for viewing and printing.</span></span> <span data-ttu-id="798ae-104">當您預覽報表或將它匯出成不同的檔案格式時，分頁符號會決定內容如何納入報表頁面，以便進行最佳檢視。</span><span class="sxs-lookup"><span data-stu-id="798ae-104">Page breaks determine how the content is fitted to a report page for optimal viewing when you preview a report or export it to a different file format.</span></span>  
  
 <span data-ttu-id="798ae-105">加入分頁符號也會提升處理大型報表的效能。</span><span class="sxs-lookup"><span data-stu-id="798ae-105">Adding page breaks also improves the performance of large reports when the are processed.</span></span> <span data-ttu-id="798ae-106">已轉譯的頁面會顯示，而其餘頁面則在背景中轉譯。</span><span class="sxs-lookup"><span data-stu-id="798ae-106">A rendered page is displayed while the rest of the pages are rendered in the background.</span></span> <span data-ttu-id="798ae-107">這可讓您在等待其他頁面可用時，先檢視報表的初始頁面。</span><span class="sxs-lookup"><span data-stu-id="798ae-107">This allows you to begin viewing the initial pages of the report while waiting for additional pages to become available.</span></span>  
  
 <span data-ttu-id="798ae-108">分頁符號可以加入至資料表、矩陣、清單、圖表、量測計或影像等報表項目。</span><span class="sxs-lookup"><span data-stu-id="798ae-108">Page breaks can be added to report items such as a table, matrix, list, chart, gauge, or image.</span></span> <span data-ttu-id="798ae-109">您也可以將分頁符號加入至資料表、矩陣或清單中的群組。</span><span class="sxs-lookup"><span data-stu-id="798ae-109">You can also add page breaks to groups in a table, matrix, or list.</span></span> <span data-ttu-id="798ae-110">分頁符號可以加入至群組之前、之後或之間。</span><span class="sxs-lookup"><span data-stu-id="798ae-110">Page breaks can be added before, after, and between groups.</span></span> <span data-ttu-id="798ae-111">依預設，群組之間的分頁符號不會加入至報表。</span><span class="sxs-lookup"><span data-stu-id="798ae-111">Page breaks between groups are not added to the report by default.</span></span>  
  
 <span data-ttu-id="798ae-112">如需詳細資訊，請參閱[在多個頁面上顯示資料列和資料行標頭 &#40;報表產生器及 SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) 和[在報表中捲動時將標頭保持可見 &#40;報表產生器及 SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="798ae-112">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) and [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="798ae-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="798ae-113">See Also</span></span>  
 <span data-ttu-id="798ae-114">[列出 &#40;報表產生器和 SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="798ae-114">[Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="798ae-115">[控制報表頁面上的 Tablix 資料區顯示 &#40;報表產生器及 SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md) </span><span class="sxs-lookup"><span data-stu-id="798ae-115">[Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md) </span></span>  
 <span data-ttu-id="798ae-116">[群組窗格 &#40;報表產生器&#41;](grouping-pane-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="798ae-116">[Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md) </span></span>  
 [<span data-ttu-id="798ae-117">與群組一起顯示頁首和頁尾 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="798ae-117">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
  
