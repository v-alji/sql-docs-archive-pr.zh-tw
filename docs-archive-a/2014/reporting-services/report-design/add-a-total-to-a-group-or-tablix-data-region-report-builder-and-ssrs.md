---
title: 將總計新增到群組或 Tablix 資料區 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f626621a37a327ae32664ab9444e72ce4931ac0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585035"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a><span data-ttu-id="4ea72-102">將總計加入到群組或 Tablix 資料區 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="4ea72-102">Add a Total to a Group or Tablix Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="4ea72-103">您可以在 Tablix 資料區中，加入群組的總計或整個資料區域的總計。</span><span class="sxs-lookup"><span data-stu-id="4ea72-103">You can add totals in a tablix data region for a group or for the entire data region.</span></span> <span data-ttu-id="4ea72-104">根據預設，總計是套用篩選之後，群組或資料區域中的數值、非 Null 資料的總和。</span><span class="sxs-lookup"><span data-stu-id="4ea72-104">By default, a total is the sum of the numeric, non-null data in a group or in the data region, after filters are applied.</span></span> <span data-ttu-id="4ea72-105">若要加入群組的總計，在 [群組] 窗格中，按一下群組之快速鍵功能表上的 **[加入總計]** 。</span><span class="sxs-lookup"><span data-stu-id="4ea72-105">To add totals for a group, click **Add Total** on the shortcut menu for the group in the Grouping pane.</span></span> <span data-ttu-id="4ea72-106">若要加入 Tablix 主體區域中個別資料格的總計，按一下資料格之快速鍵功能表上的 **[加入總計]** 。</span><span class="sxs-lookup"><span data-stu-id="4ea72-106">To add totals for an individual cell in the tablix body area, click **Add Total** on the shortcut menu for the cell.</span></span> <span data-ttu-id="4ea72-107">[新增總計]\*\*\*\* 命令與內容相關，而且僅能針對數值欄位啟用。</span><span class="sxs-lookup"><span data-stu-id="4ea72-107">The **Add Total** command is context-sensitive and enabled only for numeric fields.</span></span> <span data-ttu-id="4ea72-108">根據所選取的 Tablix 資料格，您可以在 Tablix 主體區域中選取資料格來加入單一資料格的總計，或者在 Tablix 資料列群組區域或 Tablix 資料行群組區域中選取資料格來加入整個群組的總計。</span><span class="sxs-lookup"><span data-stu-id="4ea72-108">Depending on the tablix cell that you select, you can add a total for a single cell by selecting a cell in the tablix body area or for the entire group by selecting a cell in the tablix row group area or the tablix column group area.</span></span> <span data-ttu-id="4ea72-109">如需 Tablix 資料區的詳細資訊，請參閱 [Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="4ea72-109">For more information about tablix areas, see [Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="4ea72-110">加入總計之後，您可以從內建報表函數的清單，將預設函數 Sum 變更為不同的彙總函數。</span><span class="sxs-lookup"><span data-stu-id="4ea72-110">After you add a total, you can change the default function Sum to a different aggregate function from the list of built-in report functions.</span></span> <span data-ttu-id="4ea72-111">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器和 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)。[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ea72-111">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).[!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]</span></span>  
  
### <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a><span data-ttu-id="4ea72-112">在 Tablix 主體區域中加入個別值的總計</span><span class="sxs-lookup"><span data-stu-id="4ea72-112">To add a total for an individual value in the tablix body area</span></span>  
  
-   <span data-ttu-id="4ea72-113">在 Tablix 資料區域主體區域中，以滑鼠右鍵按一下您要加入總計的資料格。</span><span class="sxs-lookup"><span data-stu-id="4ea72-113">In the tablix data region body area, right-click the cell where you want to add the total.</span></span> <span data-ttu-id="4ea72-114">資料格必須包含數值欄位。</span><span class="sxs-lookup"><span data-stu-id="4ea72-114">The cell must contain a numeric field.</span></span> <span data-ttu-id="4ea72-115">指向 **[加入總計]**，然後按一下 **[資料列]** 或 **[資料行]**。</span><span class="sxs-lookup"><span data-stu-id="4ea72-115">Point to **Add Total**, and then click **Row** or **Column**.</span></span>  
  
     <span data-ttu-id="4ea72-116">目前群組外的新資料列或資料行會加入到資料區域中，其中包含您按下之資料格中欄位的預設總計。</span><span class="sxs-lookup"><span data-stu-id="4ea72-116">A new row or column outside the current group is added to the data region, with a default total for the field in the cell you clicked.</span></span>  
  
     <span data-ttu-id="4ea72-117">如果 Tablix 資料區域是資料表，將會自動加入資料列。</span><span class="sxs-lookup"><span data-stu-id="4ea72-117">If the tablix data region is a table, a row is automatically added.</span></span>  
  
### <a name="to-add-totals-for-a-row-group"></a><span data-ttu-id="4ea72-118">加入資料列群組的總計</span><span class="sxs-lookup"><span data-stu-id="4ea72-118">To add totals for a row group</span></span>  
  
-   <span data-ttu-id="4ea72-119">在 Tablix 資料區域資料列群組區域中，以滑鼠右鍵按一下您要加總之資料列群組區域中的資料格，指向 [新增總計]\*\*\*\*，然後按一下 [之前]\*\*\*\* 或 [之後]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ea72-119">In the tablix data region row group area, right-click a cell in the row group area for which you want totals, point to **Add Total**, and then click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="4ea72-120">目前群組外的新資料列會加入到資料區域中，然後會在資料列中加入每個數值欄位的預設總計。</span><span class="sxs-lookup"><span data-stu-id="4ea72-120">A new row outside the current group is added to the data region, and then a default total is added for each numeric field in the row.</span></span>  
  
### <a name="to-add-totals-for-a-column-group"></a><span data-ttu-id="4ea72-121">加入資料行群組的總計</span><span class="sxs-lookup"><span data-stu-id="4ea72-121">To add totals for a column group</span></span>  
  
-   <span data-ttu-id="4ea72-122">在 Tablix 資料區域資料列群組區域中，以滑鼠右鍵按一下您要加總之資料行群組區域中的資料格，指向 [新增總計]\*\*\*\*，然後按一下 [之前]\*\*\*\* 或 [之後]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4ea72-122">In the tablix data region row group area, right-click a cell in the column group area for which you want totals, then point to **Add Total**, and click **Before** or **After**.</span></span>  
  
     <span data-ttu-id="4ea72-123">目前群組外的新資料行會加入到資料區域中，然後會在資料行中加入每個數值欄位的預設總計。</span><span class="sxs-lookup"><span data-stu-id="4ea72-123">A new column outside the current group is added to the data region, and then a default total is added for each numeric field in the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea72-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ea72-124">See Also</span></span>  
 <span data-ttu-id="4ea72-125">[總計、匯總和內建集合的運算式範圍 &#40;報表產生器和 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span><span class="sxs-lookup"><span data-stu-id="4ea72-125">[Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md) </span></span>  
 <span data-ttu-id="4ea72-126">[Tablix 資料區 &#40;報表產生器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ea72-126">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ea72-127">[資料表 &#40;報表產生器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ea72-127">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ea72-128">[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ea72-128">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4ea72-129">[列出 &#40;報表產生器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4ea72-129">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="4ea72-130">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4ea72-130">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
