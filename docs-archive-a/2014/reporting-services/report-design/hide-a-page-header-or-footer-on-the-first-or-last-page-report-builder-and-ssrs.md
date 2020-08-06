---
title: 隱藏第一頁或最後一頁的頁首或頁尾 (報表產生器及 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f87ce79b-00d7-4458-a17e-e253a20f720d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60c8789fd098df7347e9cc0f583426478aee06e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686785"
---
# <a name="hide-a-page-header-or-footer-on-the-first-or-last-page-report-builder-and-ssrs"></a><span data-ttu-id="a2d4a-102">隱藏第一頁或最後一頁的頁首或頁尾 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a2d4a-102">Hide a Page Header or Footer on the First or Last Page (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a2d4a-103">報表可以包含分別在每個頁面的頂端和底端執行的頁首和頁尾。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-103">A report can contain a page header and page footer that run along the top and bottom of each page, respectively.</span></span> <span data-ttu-id="a2d4a-104">在您加入頁首或頁尾之後，就可以選擇性地隱藏報表第一頁和最後一頁的頁首或頁尾。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-104">After you a add a header or footer, you can selectively hide it on the first and last pages of a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-hide-a-page-header-on-the-first-or-last-page"></a><span data-ttu-id="a2d4a-105">若要隱藏第一頁或最後一頁的頁首</span><span class="sxs-lookup"><span data-stu-id="a2d4a-105">To hide a page header on the first or last page</span></span>  
  
1.  <span data-ttu-id="a2d4a-106">在 [設計] 檢視中，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-106">Open a report in Design view.</span></span>  
  
2.  <span data-ttu-id="a2d4a-107">以滑鼠右鍵按一下頁首，然後按一下 [頁首屬性]  。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-107">Right-click the page header, and then click **Header Properties**.</span></span> <span data-ttu-id="a2d4a-108">[報表頁首屬性]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-108">The **Report Header Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="a2d4a-109">確認未選取 [Display header for this report] (顯示這個報表的頁首)  。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-109">Verify that **Display header for this report** is not selected.</span></span>  
  
4.  <span data-ttu-id="a2d4a-110">在 [列印選項]  區段中，清除每個選項的核取方塊可以在報表的第一頁或最後一頁隱藏顯示。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-110">In the **Print options** section, clear the check box for each option to hide the display on the first or last page of the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-hide-a-page-footer-on-the-first-or-last-page"></a><span data-ttu-id="a2d4a-111">若要隱藏第一頁或最後一頁的頁尾</span><span class="sxs-lookup"><span data-stu-id="a2d4a-111">To hide a page footer on the first or last page</span></span>  
  
1.  <span data-ttu-id="a2d4a-112">在 [設計] 檢視中，開啟報表。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-112">Open a report in Design view.</span></span>  
  
2.  <span data-ttu-id="a2d4a-113">以滑鼠右鍵按一下頁尾，然後按一下 [頁尾屬性]  。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-113">Right-click the page footer, and then click **Footer Properties**.</span></span> <span data-ttu-id="a2d4a-114">[報表頁尾屬性]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-114">The **Report Footer Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="a2d4a-115">確認未選取 [Display footer for this report] (顯示這個報表的頁尾)  。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-115">Verify that **Display footer for this report** is not selected.</span></span>  
  
4.  <span data-ttu-id="a2d4a-116">在 [列印選項]  區段中，清除每個選項的核取方塊可以在報表的第一頁或最後一頁隱藏顯示。</span><span class="sxs-lookup"><span data-stu-id="a2d4a-116">In the **Print options** section, clear the check box for each option to hide the display on the first or last page of the report.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a2d4a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2d4a-117">See Also</span></span>  
 <span data-ttu-id="a2d4a-118">[頁首和頁尾 &#40;報表產生器及 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a2d4a-118">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a2d4a-119">[Reporting Services 中的分頁 &#40;報表產生器及 SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a2d4a-119">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a2d4a-120">加入或移除頁首或頁尾 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a2d4a-120">Add or Remove a Page Header or Footer &#40;Report Builder and SSRS&#41;</span></span>](add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md)  
  
  
