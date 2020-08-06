---
title: 與群組一起顯示頁首和頁尾 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8eb7d648-4df2-491a-96cb-99e55629d617
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: adbb3674a16fc77d04ac3ac490a284894588c657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595739"
---
# <a name="display-headers-and-footers-with-a-group-report-builder-and-ssrs"></a><span data-ttu-id="3109e-102">與群組一起顯示頁首和頁尾 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3109e-102">Display Headers and Footers with a Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3109e-103">您可以協助控制靜態資料列 (例如群組頁首或頁尾) 是否會與動態資料列 (與 Tablix 資料區中的群組有關聯) 一起轉譯。</span><span class="sxs-lookup"><span data-stu-id="3109e-103">You can help control whether a static row, such as a group header or footer, renders with dynamic rows that are associated with a group in a tablix data region.</span></span>  
  
 <span data-ttu-id="3109e-104">若要在多個頁面上重複所有資料行標題或資料列標題，您可以設定 Tablix 資料區的屬性。</span><span class="sxs-lookup"><span data-stu-id="3109e-104">To repeat all the column headings or row headings on multiple pages, you can set properties for the tablix data region.</span></span> <span data-ttu-id="3109e-105">如需詳細資訊，請參閱[在多個頁面上顯示資料列和資料行標頭 &#40;報表產生器及 SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3109e-105">For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="3109e-106">若要控制與巢狀群組相關聯之動態資料列和資料行的轉譯行為，或與標籤或小計相關聯之靜態資料列和資料行的轉譯行為，您必須設定 Tablix 成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="3109e-106">To control the rendering behavior for dynamic rows and columns that are associated with nested groups, or for static rows and columns that are associated with labels or subtotals, you must set properties for the tablix member.</span></span> <span data-ttu-id="3109e-107">Tablix 成員代表靜態或動態資料列或資料行。</span><span class="sxs-lookup"><span data-stu-id="3109e-107">A tablix member represents a static or dynamic row or column.</span></span> <span data-ttu-id="3109e-108">靜態成員會重複一次。</span><span class="sxs-lookup"><span data-stu-id="3109e-108">A static member repeats once.</span></span> <span data-ttu-id="3109e-109">例如，總計資料列就是靜態資料列。</span><span class="sxs-lookup"><span data-stu-id="3109e-109">For example, a grand total row is a static row.</span></span> <span data-ttu-id="3109e-110">動態成員會針對每個群組執行個體重複一次。</span><span class="sxs-lookup"><span data-stu-id="3109e-110">A dynamic member repeats once for each group instance.</span></span> <span data-ttu-id="3109e-111">例如，與具有群組運算式 [Territory] 之群組相關聯的資料列會針對領域的每個唯一值重複一次。</span><span class="sxs-lookup"><span data-stu-id="3109e-111">For example, a row that is associated with a group that has the group expression [Territory] repeats once for each unique value for territory.</span></span> <span data-ttu-id="3109e-112">如需 Tablix 成員的詳細資訊，請參閱 [Tablix 資料區資料格、資料列及資料行 &#40;報表產生器及 SSRS&#41;](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="3109e-112">For more information about tablix members, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="3109e-113">您可以在 [群組] 窗格中選取 Tablix 成員，然後在 [屬性] 窗格中設定 **[KeepWithGroup]** 、 **[KeepTogether]** 和 **[RepeatOnNewPage]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="3109e-113">You can select a tablix member in the Grouping pane and set the properties **KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** in the Properties pane.</span></span> <span data-ttu-id="3109e-114">使用 **[KeepWithGroup]** 可在與群組相同的頁面上顯示群組頁首和頁尾。</span><span class="sxs-lookup"><span data-stu-id="3109e-114">Use **KeepWithGroup** to help display group headers and footers on the same page as the group.</span></span> <span data-ttu-id="3109e-115">使用 **[KeepTogether]** 可以與某個群組的資料列或資料行一併顯示靜態成員。</span><span class="sxs-lookup"><span data-stu-id="3109e-115">Use **KeepTogether** to help display static members with the rows or columns of a group.</span></span> <span data-ttu-id="3109e-116">使用 **[RepeatOnNewPage]** 可在至少顯示一個 **[KeepWithGroup]** 值所指定的完整資料列群組成員執行個體的每一頁上，重複群組頁首或頁尾。</span><span class="sxs-lookup"><span data-stu-id="3109e-116">Use **RepeatOnNewPage** to repeat the group header or footer on every page that displays at least one complete instance of the row group member designated by the **KeepWithGroup** value.</span></span> <span data-ttu-id="3109e-117">資料行群組成員不支援 **[RepeatOnNewPage]** 。</span><span class="sxs-lookup"><span data-stu-id="3109e-117">**RepeatOnNewPage** is not supported for column group members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3109e-118">**KeepWithGroup**、**KeepTogether** 和 **RepeatOnNewPage** 是群組成員屬性，可以使用 [群組] 窗格的 [進階模式]  設定。</span><span class="sxs-lookup"><span data-stu-id="3109e-118">**KeepWithGroup**, **KeepTogether**, and **RepeatOnNewPage** are group member properties that you can set by using the **Advanced Mode** of the Grouping pane.</span></span> <span data-ttu-id="3109e-119">如需詳細資訊，請參閱[群組窗格 &#40;報表產生器&#41;](grouping-pane-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="3109e-119">For more information, see [Grouping Pane &#40;Report Builder&#41;](grouping-pane-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-a-static-row-with-a-set-of-dynamic-rows-associated-with-a-row-group"></a><span data-ttu-id="3109e-120">若要將靜態資料列和一組與資料列群組相關聯的動態資料列保持在一起</span><span class="sxs-lookup"><span data-stu-id="3109e-120">To keep a static row with a set of dynamic rows associated with a row group</span></span>  
  
1.  <span data-ttu-id="3109e-121">在設計介面上，按一下 Tablix 資料區中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="3109e-121">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="3109e-122">[群組] 窗格會顯示資料區的資料列群組和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="3109e-122">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="3109e-123">在 [群組] 窗格的右邊按一下向下箭頭，然後按一下 **[進階模式]** 。</span><span class="sxs-lookup"><span data-stu-id="3109e-123">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="3109e-124">[資料列群組] 窗格會顯示資料列群組階層的階層式靜態和動態成員。</span><span class="sxs-lookup"><span data-stu-id="3109e-124">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="3109e-125">按一下對應至要與群組資料列保持在一起的資料列標頭或頁尾的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="3109e-125">Click the static member that corresponds to the row header or footer that you want to keep with the group rows.</span></span> <span data-ttu-id="3109e-126">[屬性] 窗格會顯示 **[Tablix 成員]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="3109e-126">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="3109e-127">在 [屬性] 窗格中，按一下 [KeepWithGroup]  ，然後從下拉式清單選擇下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="3109e-127">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="3109e-128">**無** ：選取這個選項可指出沒有將此成員與所選取資料列群組的成員保持在一起的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="3109e-128">**None** Select this option to indicate no preference for keeping this member with the members of the selected row group.</span></span>  
  
    -   <span data-ttu-id="3109e-129">**之前** ：選取這個選項可將此成員與先前群組的成員保持在一起。</span><span class="sxs-lookup"><span data-stu-id="3109e-129">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="3109e-130">您可以將此選項用於群組頁尾資料列。</span><span class="sxs-lookup"><span data-stu-id="3109e-130">You might use this for group footer rows.</span></span>  
  
    -   <span data-ttu-id="3109e-131">**之後** ：選取這個選項可將此成員與後續群組的成員保持在一起。</span><span class="sxs-lookup"><span data-stu-id="3109e-131">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="3109e-132">您可以將此選項用於群組頁首資料列。</span><span class="sxs-lookup"><span data-stu-id="3109e-132">You might use this for group header rows.</span></span>  
  
5.  <span data-ttu-id="3109e-133">(選擇性) 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="3109e-133">(Optional) Preview the report.</span></span> <span data-ttu-id="3109e-134">在可能的狀況下，報表轉譯器都會將此成員與指定的資料列群組成員保持在一起。</span><span class="sxs-lookup"><span data-stu-id="3109e-134">Where possible, the report renderer keeps this member with the specified row group members.</span></span>  
  
### <a name="to-keep-a-static-column-with-a-set-of-dynamic-columns-associated-with-a-column-group"></a><span data-ttu-id="3109e-135">若要將靜態資料行和一組與資料行群組相關聯的動態資料行保持在一起</span><span class="sxs-lookup"><span data-stu-id="3109e-135">To keep a static column with a set of dynamic columns associated with a column group</span></span>  
  
1.  <span data-ttu-id="3109e-136">在設計介面上，按一下 Tablix 資料區中的任意位置來選取它。</span><span class="sxs-lookup"><span data-stu-id="3109e-136">On the design surface, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="3109e-137">[群組] 窗格會顯示資料區的資料列群組和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="3109e-137">The Grouping pane displays the row and column groups for the data region.</span></span>  
  
2.  <span data-ttu-id="3109e-138">在 [群組] 窗格的右邊按一下向下箭頭，然後按一下 **[進階模式]** 。</span><span class="sxs-lookup"><span data-stu-id="3109e-138">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="3109e-139">[資料行群組] 窗格會顯示資料行群組階層的階層式靜態和動態成員。</span><span class="sxs-lookup"><span data-stu-id="3109e-139">The Column Groups pane displays the hierarchical static and dynamic members for the column group hierarchy.</span></span>  
  
3.  <span data-ttu-id="3109e-140">按一下對應至要與群組資料行保持在一起的靜態資料行的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="3109e-140">Click the static member that corresponds to the static column that you want to keep with the group columns.</span></span> <span data-ttu-id="3109e-141">[屬性] 窗格會顯示 **[Tablix 成員]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="3109e-141">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
4.  <span data-ttu-id="3109e-142">在 [屬性] 窗格中，按一下 [KeepWithGroup]  ，然後從下拉式清單選擇下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="3109e-142">In the Properties pane, click **KeepWithGroup**, and then choose one of the following values from the drop-down list:</span></span>  
  
    -   <span data-ttu-id="3109e-143">**無** ：選取這個選項可指出沒有將此成員與所選取資料行群組的成員保持在一起的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="3109e-143">**None** Select this option to indicate no preference for keeping this member with the members of the selected column group.</span></span>  
  
    -   <span data-ttu-id="3109e-144">**之前** ：選取這個選項可將此成員與先前群組的成員保持在一起。</span><span class="sxs-lookup"><span data-stu-id="3109e-144">**Before** Select this option to keep this member with the members of the previous group.</span></span> <span data-ttu-id="3109e-145">您可能將此選項用於顯示在所指定資料行群組成員之前的資料行標籤。</span><span class="sxs-lookup"><span data-stu-id="3109e-145">You might use this for column labels that display before the specified column group members.</span></span>  
  
    -   <span data-ttu-id="3109e-146">**之後** ：選取這個選項可將此成員與後續群組的成員保持在一起。</span><span class="sxs-lookup"><span data-stu-id="3109e-146">**After** Select this option to keep this member with the members of the following group.</span></span> <span data-ttu-id="3109e-147">您可能將此選項用於顯示在所指定資料行群組成員之後的資料行總計。</span><span class="sxs-lookup"><span data-stu-id="3109e-147">You might use this for column totals that display after the specified column group members.</span></span>  
  
5.  <span data-ttu-id="3109e-148">(選擇性) 預覽報表。</span><span class="sxs-lookup"><span data-stu-id="3109e-148">(Optional) Preview the report.</span></span> <span data-ttu-id="3109e-149">在可能的狀況下，報表轉譯器都會將此成員與指定的資料行群組成員保持在一起。</span><span class="sxs-lookup"><span data-stu-id="3109e-149">Where possible, the report renderer keeps this member with the specified column group members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3109e-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3109e-150">See Also</span></span>  
 <span data-ttu-id="3109e-151">[Tablix 資料區域儲存格、資料列和資料行 &#40;報表產生器&#41; 和 SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3109e-151">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3109e-152">[Tablix 資料區區域 &#40;報表產生器和 SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3109e-152">[Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3109e-153">[Tablix 資料區 &#40;報表產生器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3109e-153">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3109e-154">[資料表 &#40;報表產生器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3109e-154">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3109e-155">[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3109e-155">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3109e-156">[列出 &#40;報表產生器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3109e-156">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3109e-157">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3109e-157">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
