---
title: 在資料區中合併資料格 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 43551300-89b2-4f4e-af09-69084324afaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c69ce8182bda3e0b644893e97b69280a003f5732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703842"
---
# <a name="merge-cells-in-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="3c2f4-102">在資料區中合併資料格 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3c2f4-102">Merge Cells in a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3c2f4-103">您可以在資料區域中合併資料格來結合資料格、增進資料區域外觀，或為資料行群組與資料列群組提供橫跨的標籤。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-103">You can merge cells in a data region to combine cells, improve data region appearance, or provide spanning labels for column groups and row groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c2f4-104">資料格僅能在資料區域的每個區域內進行合併：邊角、資料行標頭、群組定義 (或資料列標頭) 以及主體。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-104">Cells can only be merged within each area of a data region: corner, column headers, group definition (or row headers), and body.</span></span> <span data-ttu-id="3c2f4-105">您無法合併跨越區域界限的資料格。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-105">You cannot merge cells that cross area boundaries.</span></span> <span data-ttu-id="3c2f4-106">例如，您無法將資料區邊角區域中的資料格與資料列群組區域中的資料格合併。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-106">For example, you cannot merge a cell in the data region corner area with a cell in the row group area.</span></span> <span data-ttu-id="3c2f4-107">如需 tablix 區域的詳細資訊，請參閱[&#40;報表產生器和 SSRS&#41;清單](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-107">For more information about tablix areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-merge-cells-in-a-data-region"></a><span data-ttu-id="3c2f4-108">若要在資料區中合併資料格</span><span class="sxs-lookup"><span data-stu-id="3c2f4-108">To merge cells in a data region</span></span>  
  
1.  <span data-ttu-id="3c2f4-109">在報表設計介面的資料區中，按一下要合併的第一個資料格。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-109">In the data region on the report design surface, click the first cell to merge.</span></span> <span data-ttu-id="3c2f4-110">按住滑鼠左鍵，以垂直或水平方向拖曳來選取相鄰的資料格。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-110">Holding the left mouse button down, drag vertically or horizontally to select adjacent cells.</span></span> <span data-ttu-id="3c2f4-111">選取的資料格就會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-111">The selected cells are highlighted.</span></span>  
  
2.  <span data-ttu-id="3c2f4-112">以滑鼠右鍵按一下選取的資料格，然後選取 [合併資料格]  。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-112">Right-click the selected cells and select **Merge Cells**.</span></span> <span data-ttu-id="3c2f4-113">選取的資料格就會結合到單一的資料格中。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-113">The selected cells are combined into a single cell.</span></span>  
  
3.  <span data-ttu-id="3c2f4-114">重複步驟 1 和 2，在資料區域中合併其他相鄰的資料格。</span><span class="sxs-lookup"><span data-stu-id="3c2f4-114">Repeat steps 1 and 2 to merge other adjacent cells in a data region.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2f4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c2f4-115">See Also</span></span>  
 <span data-ttu-id="3c2f4-116">[Tablix 資料區 &#40;報表產生器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c2f4-116">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3c2f4-117">[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c2f4-117">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3c2f4-118">[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c2f4-118">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3c2f4-119">[列出 &#40;報表產生器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3c2f4-119">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3c2f4-120">清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3c2f4-120">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
