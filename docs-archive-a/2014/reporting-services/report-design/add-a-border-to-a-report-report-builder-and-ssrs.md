---
title: 將框線新增至報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 81412f94-2991-4e58-bc05-5ccc0cbf2a75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf4a0c2c117774a0f3b25ca0644796fd067bc971
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707162"
---
# <a name="add-a-border-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="9fdaa-102">在報表中加入框線 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9fdaa-102">Add a Border to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9fdaa-103">您可以藉由將框線加入頁首、頁尾和報表主體本身來在報表中加入框線，而不必加入線條或矩形。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-103">You can add a border to a report by adding borders to the headers, footers, and report body themselves, without adding lines or rectangles.</span></span>  
  
 <span data-ttu-id="9fdaa-104">如果加入了出現在頁首和頁尾的報表框線，不要抑制報表第一頁和最後一頁的頁首及頁尾。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-104">If you add a report border that appears on the page header and footer, do not suppress the header and footer on the first and last pages of the report.</span></span> <span data-ttu-id="9fdaa-105">如果抑制顯示，則報表第一頁和最後一頁之上方或下方的框線將被切斷。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-105">If you do, the border may appear cut off at the top or bottom of the first and last pages of the report.</span></span> <span data-ttu-id="9fdaa-106">如需詳細資訊，請參閱[頁首和頁尾 &#40;報表產生器及 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-106">For more information, see [Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-border-to-a-report"></a><span data-ttu-id="9fdaa-107">在報表中加入框線</span><span class="sxs-lookup"><span data-stu-id="9fdaa-107">To add a border to a report</span></span>  
  
1.  <span data-ttu-id="9fdaa-108">在頁首內以滑鼠右鍵按一下任何項目的外部，然後按一下 [頁首屬性]  。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-108">Right-click in the header outside any items in the header, and click **Header Properties**.</span></span> <span data-ttu-id="9fdaa-109">以您所要的樣式，在 **[框線]** 索引標籤上加入左框線、上框線和右框線。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-109">On the **Border** tab, add a left, top, and right border with the style you want.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9fdaa-110"> 如果您不要在報表中使用頁首，可以將框線放在報表主體的周圍，或是從 **[插入]** 索引標籤加入頁首。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-110">If you do not use headers in your report, you can place borders around just the report body, or you can add headers from the **Insert** tab.</span></span>  
  
2.  <span data-ttu-id="9fdaa-111">在設計介面上以滑鼠右鍵按一下主體內任何項目的外部，然後按一下 [主體屬性]  。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-111">Right-click in the body outside any items on the design surface, and click **Body Properties**.</span></span> <span data-ttu-id="9fdaa-112">以您所要的樣式，在 **[框線]** 索引標籤上加入左框線和右框線。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-112">On the **Border** tab, add a left and right border with the style you want.</span></span>  
  
3.  <span data-ttu-id="9fdaa-113">在頁尾內以滑鼠右鍵按一下任何項目的外部，然後按一下 [頁尾屬性]  。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-113">Right-click in the footer outside any items in the footer, and click **Footer Properties**.</span></span> <span data-ttu-id="9fdaa-114">以您所要的樣式，在 **[框線]** 索引標籤上加入左框線、下框線和右框線。</span><span class="sxs-lookup"><span data-stu-id="9fdaa-114">On the **Border** tab, add a left, bottom, and right border with the style you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fdaa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fdaa-115">See Also</span></span>  
 [<span data-ttu-id="9fdaa-116">矩形和線條 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9fdaa-116">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
  
  
