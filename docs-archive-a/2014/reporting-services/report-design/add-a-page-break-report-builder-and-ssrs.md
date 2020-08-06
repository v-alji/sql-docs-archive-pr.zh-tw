---
title: 新增分頁符號 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3846cd48-2787-47e9-b13b-7fc45a205f68
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55d6be3ae47827c5a8ff4a5b36e3ff2ce80e1034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585041"
---
# <a name="add-a-page-break-report-builder-and-ssrs"></a><span data-ttu-id="35d0e-102">加入分頁符號 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="35d0e-102">Add a Page Break (Report Builder and SSRS)</span></span>
  <span data-ttu-id="35d0e-103">您可以在資料區內的矩形、資料區或群組中加入分頁符號，以控制每頁的資料量。</span><span class="sxs-lookup"><span data-stu-id="35d0e-103">You can add a page break to rectangles, data regions, or groups within data regions to control the amount of information on each page.</span></span> <span data-ttu-id="35d0e-104">加入分頁符號可以改善已發行報表的效能，因為在檢視報表時，只有每個頁面上的項目需要進行處理。</span><span class="sxs-lookup"><span data-stu-id="35d0e-104">Adding page breaks can improve the performance of published reports because only the items on each page have to be processed as you view the report.</span></span> <span data-ttu-id="35d0e-105">當整個報表只有單一頁面時，必須先將所有的項目進行處理，才能檢視報表。</span><span class="sxs-lookup"><span data-stu-id="35d0e-105">When the whole report is a single page, all items must be processed before you can view the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-break-to-a-data-region"></a><span data-ttu-id="35d0e-106">將分頁符號加入至資料區域</span><span class="sxs-lookup"><span data-stu-id="35d0e-106">To add a page break to a data region</span></span>  
  
1.  <span data-ttu-id="35d0e-107">在設計介面上，以滑鼠右鍵按一下資料區域的角控點，然後按一下 [Tablix 屬性]  。</span><span class="sxs-lookup"><span data-stu-id="35d0e-107">On the design surface, right-click the corner handle of the data region and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="35d0e-108">在 **[一般]** 索引標籤的 **[分頁符號選項]** 下方，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="35d0e-108">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="35d0e-109">**在前方加入分頁符號**—</span><span class="sxs-lookup"><span data-stu-id="35d0e-109">**Add a page break before**.</span></span> <span data-ttu-id="35d0e-110">如果要在資料表之前加入分頁符號，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="35d0e-110">Select this option when you want to add a page break before the table.</span></span>  
  
    -   <span data-ttu-id="35d0e-111">**在後方加入分頁符號**—</span><span class="sxs-lookup"><span data-stu-id="35d0e-111">**Add a page break after**.</span></span> <span data-ttu-id="35d0e-112">如果要在資料表之後加入分頁符號，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="35d0e-112">Select this option when you want to add a page break after the table.</span></span>  
  
    -   <span data-ttu-id="35d0e-113">**盡可能將資料表納入一個頁面**—</span><span class="sxs-lookup"><span data-stu-id="35d0e-113">**Fit table on one page if possible**.</span></span> <span data-ttu-id="35d0e-114">如果要將資料放入單一頁面，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="35d0e-114">Select this option when you want the data to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-rectangle"></a><span data-ttu-id="35d0e-115">將分頁符號加入至矩形</span><span class="sxs-lookup"><span data-stu-id="35d0e-115">To add a page break to a rectangle</span></span>  
  
1.  <span data-ttu-id="35d0e-116">在設計介面上，以滑鼠右鍵按一下要新增分頁符號的矩形，然後按一下 [矩形屬性]  。</span><span class="sxs-lookup"><span data-stu-id="35d0e-116">On the design surface, right-click the rectangle where you want to add a page break, and then click **Rectangle Properties**.</span></span>  
  
2.  <span data-ttu-id="35d0e-117">在 **[一般]** 索引標籤的 **[分頁符號選項]** 下方，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="35d0e-117">On the **General** tab, under **Page break options**, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="35d0e-118">**在前方加入分頁符號**—</span><span class="sxs-lookup"><span data-stu-id="35d0e-118">**Add a page break before**.</span></span> <span data-ttu-id="35d0e-119">如果要在矩形之前加入分頁符號，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="35d0e-119">Select this option when you want to add a page break before the rectangle.</span></span>  
  
    -   <span data-ttu-id="35d0e-120">**在後方加入分頁符號**—</span><span class="sxs-lookup"><span data-stu-id="35d0e-120">**Add a page break after**.</span></span> <span data-ttu-id="35d0e-121">如果要在矩形之後加入分頁符號，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="35d0e-121">Select this option when you want to add a page break after the rectangle.</span></span>  
  
    -   <span data-ttu-id="35d0e-122">**省略分頁符號上的框線**—</span><span class="sxs-lookup"><span data-stu-id="35d0e-122">**Omit border on page break**.</span></span> <span data-ttu-id="35d0e-123">如果不要顯示分頁符號上的框線，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="35d0e-123">Select this option when you do not want a border on the page break.</span></span>  
  
    -   <span data-ttu-id="35d0e-124">**盡可能將內容保持在一頁**—</span><span class="sxs-lookup"><span data-stu-id="35d0e-124">**Keep contents together on a single page, if possible**.</span></span> <span data-ttu-id="35d0e-125">如果要將矩形內部的內容放入單一頁面，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="35d0e-125">Select this option when you want contents inside the rectangle to stay on one page.</span></span>  
  
### <a name="to-add-a-page-break-to-a-row-group-in-a-table-matrix-or-list"></a><span data-ttu-id="35d0e-126">若要將分頁符號加入至資料表、矩陣或清單中的資料列群組</span><span class="sxs-lookup"><span data-stu-id="35d0e-126">To add a page break to a row group in a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="35d0e-127">在 [群組] 窗格中，以滑鼠右鍵按一下資料列群組，然後按一下 [群組屬性]  。</span><span class="sxs-lookup"><span data-stu-id="35d0e-127">In the Grouping pane, right-click a row group, and then click **Group Properties**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="35d0e-128">系統就會忽略資料行群組上的分頁符號。</span><span class="sxs-lookup"><span data-stu-id="35d0e-128">Page breaks are ignored on column groups.</span></span>  
  
2.  <span data-ttu-id="35d0e-129">在 **[分頁符號]** 索引標籤上，選取 **[在群組的每個執行個體之間]** ，以在資料表中的每個群組執行個體之間加入分頁符號。</span><span class="sxs-lookup"><span data-stu-id="35d0e-129">On the **Page Breaks** tab, select **Between each instance of a group** to add a page break between each instance of a group in the table.</span></span>  
  
3.  <span data-ttu-id="35d0e-130">或者，也可以選取 **[也在群組的開頭]** 或 **[也在群組的結尾]** ，指定在資料表中的群組開頭或結尾處加入分頁符號。</span><span class="sxs-lookup"><span data-stu-id="35d0e-130">Optionally, select **Also at the start of a group** or **Also at the end of a group** to specify that a page break be added when a group starts or ends in the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d0e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35d0e-131">See Also</span></span>  
 <span data-ttu-id="35d0e-132">[Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="35d0e-132">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="35d0e-133">[轉譯行為 &#40;報表產生器及 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="35d0e-133">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="35d0e-134">頁首和頁尾 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="35d0e-134">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
