---
title: 插入或刪除資料列 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b9642af3-b3ae-4f78-b0be-8f96b79fc313
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fdec24801d1fae3b95c7d75acb5a3add650d523b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707105"
---
# <a name="insert-or-delete-a-row-report-builder-and-ssrs"></a><span data-ttu-id="f30f9-102">插入或刪除資料列 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f30f9-102">Insert or Delete a Row (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f30f9-103">您可以在 Tablix 資料區中加入或刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="f30f9-103">You can add or delete rows in a tablix data region.</span></span> <span data-ttu-id="f30f9-104">Tablix 資料區可以是資料表、矩陣或清單。</span><span class="sxs-lookup"><span data-stu-id="f30f9-104">The tablix data region can be a table, a matrix, or a list.</span></span> <span data-ttu-id="f30f9-105">下列程序不適用於圖表和量測計資料區域。</span><span class="sxs-lookup"><span data-stu-id="f30f9-105">The following procedures do not apply to the chart and gauge data regions.</span></span>  
  
 <span data-ttu-id="f30f9-106">在 Tablix 資料區中，您可以加入與群組相關聯的資料列 (位於群組內部) 或與群組沒有關聯的資料列 (位於群組外部)。</span><span class="sxs-lookup"><span data-stu-id="f30f9-106">In a tablix data region, you can add rows that are associated with a group (inside a group) or that are not associated with a group (outside a group).</span></span> <span data-ttu-id="f30f9-107">位於群組內部的資料列會針對每個唯一的群組值重複一次。</span><span class="sxs-lookup"><span data-stu-id="f30f9-107">A row that is inside a group repeats once per unique group value.</span></span> <span data-ttu-id="f30f9-108">例如，位於群組內部而且以包含色彩名稱之資料行值為基礎的資料列會針對每個不同的色彩名稱重複一次。</span><span class="sxs-lookup"><span data-stu-id="f30f9-108">For example, a row inside a group based on the value in a data column that contains color names, repeats once per distinct color name.</span></span> <span data-ttu-id="f30f9-109">若為巢狀群組，資料列可能會位於子群組外部，但位於父群組內部。</span><span class="sxs-lookup"><span data-stu-id="f30f9-109">For nested groups, a row can be outside the child group but inside the parent group.</span></span> <span data-ttu-id="f30f9-110">在此情況下，資料列會針對父群組中的每個唯一值重複一次。</span><span class="sxs-lookup"><span data-stu-id="f30f9-110">In this case, the row repeats once for each unique value in the parent group.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-the-row-and-column-handles-appear"></a><span data-ttu-id="f30f9-111">選取資料區，以便顯示資料列和資料行控制代碼</span><span class="sxs-lookup"><span data-stu-id="f30f9-111">To select a data region so the row and column handles appear</span></span>  
  
-   <span data-ttu-id="f30f9-112">在 [設計] 檢視中，按一下 Tablix 資料區的左上角，如此資料行和資料列控制代碼就會顯示在上方和旁邊。</span><span class="sxs-lookup"><span data-stu-id="f30f9-112">In Design view, click the upper left corner of the tablix data region so that column and row handles appear above and next to it.</span></span>  
  
     <span data-ttu-id="f30f9-113">如需有關資料區區域的詳細資訊，請參閱[&#40;報表產生器和 SSRS&#41;清單](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f30f9-113">For more information about data region areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-insert-a-row-in-a-selected-data-region"></a><span data-ttu-id="f30f9-114">在選取的資料區中插入資料列</span><span class="sxs-lookup"><span data-stu-id="f30f9-114">To insert a row in a selected data region</span></span>  
  
-   <span data-ttu-id="f30f9-115">以滑鼠右鍵按一下您想要插入資料列的資料列控制代碼，按一下 [插入資料列]  ，然後按一下 [上方]  或 [下方]  。</span><span class="sxs-lookup"><span data-stu-id="f30f9-115">Right-click a row handle where you want to insert a row, click **Insert Row**, and then click **Above** or **Below**.</span></span>  
  
     <span data-ttu-id="f30f9-116">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="f30f9-116">\- or -</span></span>  
  
-   <span data-ttu-id="f30f9-117">在您想要插入資料列的資料區中，以滑鼠右鍵按一下資料格，按一下 [插入資料列]  ，然後按一下 [上方]  或 [下方]  。</span><span class="sxs-lookup"><span data-stu-id="f30f9-117">Right-click a cell in the data region where you want to insert a row, click **Insert Row**, and then click **Above** or **Below**.</span></span>  
  
### <a name="to-delete-a-row-from-a-selected-data-region"></a><span data-ttu-id="f30f9-118">從選取的資料區中刪除資料列</span><span class="sxs-lookup"><span data-stu-id="f30f9-118">To delete a row from a selected data region</span></span>  
  
-   <span data-ttu-id="f30f9-119">選取要刪除的一個或多個資料列，以滑鼠右鍵按一下所選資料列之任一資料列的控制代碼，然後按一下 [刪除資料列]  。</span><span class="sxs-lookup"><span data-stu-id="f30f9-119">Select the row or rows that you want to delete, right-click the handle for one of the rows you selected, and then click **Delete Rows**.</span></span>  
  
     <span data-ttu-id="f30f9-120">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="f30f9-120">\- or -</span></span>  
  
-   <span data-ttu-id="f30f9-121">在您想要刪除資料列的資料區中，以滑鼠右鍵按一下資料格，然後按一下 [刪除資料列]  。</span><span class="sxs-lookup"><span data-stu-id="f30f9-121">Right-click a cell in the data region where you want to delete a row, and then click **Delete Rows**.</span></span>  
  
### <a name="to-insert-a-row-in-a-group-in-a-selected-data-region"></a><span data-ttu-id="f30f9-122">在選取之資料區的群組中插入資料列</span><span class="sxs-lookup"><span data-stu-id="f30f9-122">To insert a row in a group in a selected data region</span></span>  
  
-   <span data-ttu-id="f30f9-123">在您想要插入資料列之 Tablix 資料區的資料列群組區域中，以滑鼠右鍵按一下資料列群組資料格，按一下 [插入資料列]  ，然後按一下 [上方 - 群組外]  、[上方 - 群組內]  、[下方 - 群組內]  或 [下方 - 群組外]  。</span><span class="sxs-lookup"><span data-stu-id="f30f9-123">Right-click a row group cell in the row group area of a tablix data region where you want to insert a row, click **Insert Row**, and then click **Above - Outside Group**, **Above - Inside Group**, **Below - Inside Group**, or **Below - Outside Group**.</span></span>  
  
     <span data-ttu-id="f30f9-124">如此就會在您按一下之資料列群組資料格所表示的群組內部或外部加入資料列。</span><span class="sxs-lookup"><span data-stu-id="f30f9-124">A row is added either inside or outside the group represented by the row group cell you clicked on.</span></span>  
  
### <a name="to-delete-a-row-from-a-group-in-a-selected-data-region"></a><span data-ttu-id="f30f9-125">從選取之資料區的群組中刪除資料列</span><span class="sxs-lookup"><span data-stu-id="f30f9-125">To delete a row from a group in a selected data region</span></span>  
  
-   <span data-ttu-id="f30f9-126">在您想要刪除資料列之 Tablix 資料區的資料列群組區域中，以滑鼠右鍵按一下資料列群組資料格，然後按一下 [刪除資料列]  。</span><span class="sxs-lookup"><span data-stu-id="f30f9-126">Right-click a row group cell in the row group area of a tablix data region where you want to delete a row, and then click **Delete Rows**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f30f9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f30f9-127">See Also</span></span>  
 <span data-ttu-id="f30f9-128">[Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f30f9-128">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f30f9-129">[了解群組 &#40;報表產生器及 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f30f9-129">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f30f9-130">[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f30f9-130">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f30f9-131">[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f30f9-131">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="f30f9-132">[清單 &#40;報表產生器及 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f30f9-132">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="f30f9-133">清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f30f9-133">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
