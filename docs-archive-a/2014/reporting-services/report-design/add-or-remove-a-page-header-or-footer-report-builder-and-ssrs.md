---
title: 新增或移除頁首或頁尾 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 72988623-fee8-4a05-9f72-8fcb8e668576
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b29db3f72323c460360c872a0f60d13a808e3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703869"
---
# <a name="add-or-remove-a-page-header-or-footer-report-builder-and-ssrs"></a><span data-ttu-id="04480-102">加入或移除頁首或頁尾 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="04480-102">Add or Remove a Page Header or Footer (Report Builder and SSRS)</span></span>
  <span data-ttu-id="04480-103">您可以將靜態文字、影像、線條、矩形和框線加入至頁首或頁尾。</span><span class="sxs-lookup"><span data-stu-id="04480-103">You can add static text, images, lines, rectangles, and borders to page headers or footers.</span></span> <span data-ttu-id="04480-104">如果您想要在頁首或頁尾放入變數或計算的資料，可以在文字方塊中放置運算式和資料繫結影像。</span><span class="sxs-lookup"><span data-stu-id="04480-104">You can place expressions and data-bound images in a textbox if you want variable or computed data in a header or footer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04480-105">每一個轉譯延伸模組處理頁首與頁尾的方式不同。</span><span class="sxs-lookup"><span data-stu-id="04480-105">Each rendering extension processes page headers and footers differently.</span></span> <span data-ttu-id="04480-106">如需詳細資訊，請參閱[頁首和頁尾 &#40;報表產生器及 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) 和 [Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="04480-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) and [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-header-or-footer"></a><span data-ttu-id="04480-107">若要加入頁首或頁尾</span><span class="sxs-lookup"><span data-stu-id="04480-107">To add a page header or footer</span></span>  
  
1.  <span data-ttu-id="04480-108">開啟報表。</span><span class="sxs-lookup"><span data-stu-id="04480-108">Open a report.</span></span>  
  
2.  <span data-ttu-id="04480-109">在設計介面上以滑鼠右鍵按一下報表，指向 [插入]  ，然後按一下 [頁首]  或 [頁尾]  。</span><span class="sxs-lookup"><span data-stu-id="04480-109">On the design surface, right-click the report, point to **Insert**, and then click **Header** or **Footer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04480-110">只有在頁首或頁尾尚未成為報表一部分時，才會顯示 [頁首]  和 [頁尾]  選項。</span><span class="sxs-lookup"><span data-stu-id="04480-110">The **Header** and **Footer** options appear only when a header or footer is not already part of the report.</span></span>  
  
### <a name="to-configure-a-page-header-or-footer"></a><span data-ttu-id="04480-111">設定頁首或頁尾</span><span class="sxs-lookup"><span data-stu-id="04480-111">To configure a page header or footer</span></span>  
  
1.  <span data-ttu-id="04480-112">在設計介面上以滑鼠右鍵按一下頁首或頁尾。</span><span class="sxs-lookup"><span data-stu-id="04480-112">On the design surface, right-click the page header or footer.</span></span>  
  
2.  <span data-ttu-id="04480-113">指向 [插入]  ，然後按一下下列其中一個項目，將其加入至頁首或頁尾區域：</span><span class="sxs-lookup"><span data-stu-id="04480-113">Point to **Insert**, and then click one of the following items to add it to the header or footer area:</span></span>  
  
    -   <span data-ttu-id="04480-114">**文字方塊**</span><span class="sxs-lookup"><span data-stu-id="04480-114">**Textbox**</span></span>  
  
    -   <span data-ttu-id="04480-115">**線條**</span><span class="sxs-lookup"><span data-stu-id="04480-115">**Line**</span></span>  
  
    -   <span data-ttu-id="04480-116">**矩形**</span><span class="sxs-lookup"><span data-stu-id="04480-116">**Rectangle**</span></span>  
  
    -   <span data-ttu-id="04480-117">**映像**</span><span class="sxs-lookup"><span data-stu-id="04480-117">**Image**</span></span>  
  
3.  <span data-ttu-id="04480-118">以滑鼠右鍵按一下頁首，然後按一下 [頁首屬性]  來加入框線、背景影像、色彩，或調整頁首的寬度。</span><span class="sxs-lookup"><span data-stu-id="04480-118">Right-click the page header, and then click **Header Properties** to add borders, background images, or colors, or to adjust the width of the header.</span></span> <span data-ttu-id="04480-119">然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04480-119">Then click **OK**.</span></span>  
  
4.  <span data-ttu-id="04480-120">以滑鼠右鍵按一下頁尾，然後按一下 [頁尾屬性]  來新增框線、背景影像、色彩，或調整頁尾的寬度。</span><span class="sxs-lookup"><span data-stu-id="04480-120">Right-click the page footer, and then click **Footer Properties** to add borders, background images, or colors, or to adjust the width of the footer.</span></span> <span data-ttu-id="04480-121">然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="04480-121">Then click **OK**.</span></span>  
  
### <a name="to-remove-a-page-header-or-footer"></a><span data-ttu-id="04480-122">若要移除頁首或頁尾</span><span class="sxs-lookup"><span data-stu-id="04480-122">To remove a page header or footer</span></span>  
  
1.  <span data-ttu-id="04480-123">開啟報表。</span><span class="sxs-lookup"><span data-stu-id="04480-123">Open a report.</span></span>  
  
2.  <span data-ttu-id="04480-124">在設計介面上以滑鼠右鍵按一下頁首或頁尾，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="04480-124">On the design surface, right-click the page header or footer, and then click **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="04480-125">您移除頁首或頁尾時，會將其從報表刪除。</span><span class="sxs-lookup"><span data-stu-id="04480-125">When you remove a page header or footer, you delete it from the report.</span></span> <span data-ttu-id="04480-126">如果您後來又重新加入頁首或頁尾，則先前您加入頁首或頁尾的項目並不會重新出現。</span><span class="sxs-lookup"><span data-stu-id="04480-126">Any items that you previously added to the page header or footer will not reappear if you subsequently add the header or footer again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04480-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04480-127">See Also</span></span>  
 [<span data-ttu-id="04480-128">頁首和頁尾 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="04480-128">Page Headers and Footers &#40;Report Builder and SSRS&#41;</span></span>](page-headers-and-footers-report-builder-and-ssrs.md)  
  
  
