---
title: 插入或刪除資料行 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9db79e2-7e7d-4359-a706-cb746c94182a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9a6f782dbb6cc1024583926aafe4bab1cfe2d042
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707110"
---
# <a name="insert-or-delete-a-column-report-builder-and-ssrs"></a><span data-ttu-id="a45e0-102">插入或刪除資料行 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a45e0-102">Insert or Delete a Column (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a45e0-103">您可以在 Tablix 資料區中加入或刪除資料行。</span><span class="sxs-lookup"><span data-stu-id="a45e0-103">You can add or delete columns in a tablix data region.</span></span> <span data-ttu-id="a45e0-104">Tablix 資料區可以是資料表、矩陣或清單。</span><span class="sxs-lookup"><span data-stu-id="a45e0-104">The tablix data region can be a table, a matrix, or a list.</span></span> <span data-ttu-id="a45e0-105">下列程序不適用於圖表和量測計資料區域。</span><span class="sxs-lookup"><span data-stu-id="a45e0-105">The following procedures do not apply to the chart and gauge data regions.</span></span>  
  
 <span data-ttu-id="a45e0-106">在 Tablix 資料區中，您可以加入與群組相關聯的資料行 (位於群組內部) 或與群組沒有關聯的資料行 (位於群組外部)。</span><span class="sxs-lookup"><span data-stu-id="a45e0-106">In a tablix data region, you can add columns that are associated with a group (inside a group) or that are not associated with a group (outside a group).</span></span> <span data-ttu-id="a45e0-107">位於群組內部的資料行會針對每個唯一的群組值重複一次。</span><span class="sxs-lookup"><span data-stu-id="a45e0-107">A column that is inside a group repeats once per unique group value.</span></span> <span data-ttu-id="a45e0-108">例如，位於群組內部而且以包含色彩名稱之資料行值為基礎的資料行會針對每個不同的色彩名稱重複一次。</span><span class="sxs-lookup"><span data-stu-id="a45e0-108">For example, a column inside a group based the value in a data column that contains color names, repeats once per distinct color name.</span></span> <span data-ttu-id="a45e0-109">若為巢狀群組，資料行可能會位於子群組外部，但位於父群組內部。</span><span class="sxs-lookup"><span data-stu-id="a45e0-109">For nested groups, a column can be outside the child group but inside the parent group.</span></span> <span data-ttu-id="a45e0-110">在此情況下，資料列會針對父群組中的每個唯一值重複一次。</span><span class="sxs-lookup"><span data-stu-id="a45e0-110">In this case, the row repeats once for each unique value in the parent group.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-that-the-row-and-column-handles-appear"></a><span data-ttu-id="a45e0-111">若要選取資料區，以便顯示資料列和資料行控制代碼</span><span class="sxs-lookup"><span data-stu-id="a45e0-111">To select a data region so that the row and column handles appear</span></span>  
  
-   <span data-ttu-id="a45e0-112">在 [設計] 檢視中，按一下 Tablix 資料區的左上角，如此資料行和資料列控制代碼就會顯示在它的上方和旁邊。</span><span class="sxs-lookup"><span data-stu-id="a45e0-112">In Design view, click the upper left corner of the tablix data region, so that column and row handles appear above and next to it.</span></span>  
  
     <span data-ttu-id="a45e0-113">如需有關資料區區域的詳細資訊，請參閱[&#40;報表產生器和 SSRS&#41;清單](tables-matrices-and-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a45e0-113">For more information about data region areas, see [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-insert-a-column-in-a-selected-data-region"></a><span data-ttu-id="a45e0-114">在選取的資料區中插入資料行</span><span class="sxs-lookup"><span data-stu-id="a45e0-114">To insert a column in a selected data region</span></span>  
  
-   <span data-ttu-id="a45e0-115">以滑鼠右鍵按一下您想要插入資料行的資料行控制代碼、按一下 [插入資料行]  ，然後按一下 [左方]  或 [右方]  。</span><span class="sxs-lookup"><span data-stu-id="a45e0-115">Right-click a column handle where you want to insert a column, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
     <span data-ttu-id="a45e0-116">-- 或 --</span><span class="sxs-lookup"><span data-stu-id="a45e0-116">-- or --</span></span>  
  
-   <span data-ttu-id="a45e0-117">在您想要插入資料列的資料區中，以滑鼠右鍵按一下資料格、按一下 [插入資料行]  ，然後按一下 [左方]  或 [右方]  。</span><span class="sxs-lookup"><span data-stu-id="a45e0-117">Right-click a cell in the data region where you want to insert a row, click **Insert Column**, and then click **Left** or **Right**.</span></span>  
  
### <a name="to-delete-a-column-from-a-selected-data-region"></a><span data-ttu-id="a45e0-118">從選取的資料區中刪除資料行</span><span class="sxs-lookup"><span data-stu-id="a45e0-118">To delete a column from a selected data region</span></span>  
  
-   <span data-ttu-id="a45e0-119">選取您想要刪除的一或多個資料行、以滑鼠右鍵按一下其中一個選取之資料行的控制代碼，然後按一下 [刪除資料行]  。</span><span class="sxs-lookup"><span data-stu-id="a45e0-119">Select the column or columns that you want to delete, right-click the handle for one of the columns you selected, and then click **Delete Columns**.</span></span>  
  
     <span data-ttu-id="a45e0-120">-- 或 --</span><span class="sxs-lookup"><span data-stu-id="a45e0-120">-- or --</span></span>  
  
-   <span data-ttu-id="a45e0-121">在您想要刪除資料行的資料區中，以滑鼠右鍵按一下資料格，然後按一下 [刪除資料行]  。</span><span class="sxs-lookup"><span data-stu-id="a45e0-121">Right-click a cell in the data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
### <a name="to-insert-a-column-in-a-group-in-a-selected-data-region"></a><span data-ttu-id="a45e0-122">在選取之資料區的群組中插入資料行</span><span class="sxs-lookup"><span data-stu-id="a45e0-122">To insert a column in a group in a selected data region</span></span>  
  
-   <span data-ttu-id="a45e0-123">在您想要插入資料行之 Tablix 資料區的資料行群組區域中，以滑鼠右鍵按一下資料行群組資料格、按一下 [插入資料行]  ，然後按一下 [左方 - 群組外]  、[左方 - 群組內]  、[右方 - 群組內]  或 [右方 - 群組外]  。</span><span class="sxs-lookup"><span data-stu-id="a45e0-123">Right-click a column group cell in the column group area of a tablix data region where you want to insert a column, click **Insert Column**, and then click **Left - Outside Group**, **Left - Inside Group**, **Right - Inside Group**, or **Right - Outside Group**.</span></span>  
  
     <span data-ttu-id="a45e0-124">如此就會在您按一下之資料行群組資料格所表示的群組內部或外部加入資料行。</span><span class="sxs-lookup"><span data-stu-id="a45e0-124">A column is added either inside or outside the group represented by the column group cell you clicked on.</span></span>  
  
### <a name="to-delete-a-column-from-a-group-in-a-selected-data-region"></a><span data-ttu-id="a45e0-125">從選取之資料區的群組中刪除資料行</span><span class="sxs-lookup"><span data-stu-id="a45e0-125">To delete a column from a group in a selected data region</span></span>  
  
-   <span data-ttu-id="a45e0-126">在您想要刪除資料行之 Tablix 資料區的資料行群組區域中，以滑鼠右鍵按一下資料行群組資料格，然後按一下 [刪除資料行]  。</span><span class="sxs-lookup"><span data-stu-id="a45e0-126">Right-click a column group cell in the column group area of a tablix data region where you want to delete a column, and then click **Delete Columns**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45e0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a45e0-127">See Also</span></span>  
 <span data-ttu-id="a45e0-128">[了解群組 &#40;報表產生器及 SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a45e0-128">[Understanding Groups &#40;Report Builder and SSRS&#41;](understanding-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a45e0-129">[Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a45e0-129">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a45e0-130">[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a45e0-130">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a45e0-131">[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a45e0-131">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="a45e0-132">[清單 &#40;報表產生器及 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a45e0-132">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a45e0-133">清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a45e0-133">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
