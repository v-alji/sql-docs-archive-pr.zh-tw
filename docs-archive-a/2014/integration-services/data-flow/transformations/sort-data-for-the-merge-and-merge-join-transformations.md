---
title: 排序合併和合併聯結轉換的資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7bb4e91ad84c6baa52e1d7fb4b0104d835b7e4cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687055"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a><span data-ttu-id="f70fc-102">排序合併和合併聯結轉換的資料</span><span class="sxs-lookup"><span data-stu-id="f70fc-102">Sort Data for the Merge and Merge Join Transformations</span></span>
  <span data-ttu-id="f70fc-103">在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]中，「合併」和「合併聯結」轉換需要針對其輸入排序的資料。</span><span class="sxs-lookup"><span data-stu-id="f70fc-103">In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], the Merge and Merge Join transformations require sorted data for their inputs.</span></span> <span data-ttu-id="f70fc-104">輸入資料必須實際排序，且必須在來源中或上游轉換中設定輸出和輸出資料行的排序選項。</span><span class="sxs-lookup"><span data-stu-id="f70fc-104">The input data must be sorted physically, and sort options must be set on the outputs and the output columns in the source or in the upstream transformation.</span></span> <span data-ttu-id="f70fc-105">如果排序選項表示資料已排序，但實際上資料並未排序，則合併或合併聯結作業的結果可能無法預測。</span><span class="sxs-lookup"><span data-stu-id="f70fc-105">If the sort options indicate that the data is sorted, but the data is not actually sorted, the results of the merge or merge join operation are unpredictable.</span></span>  
  
## <a name="sorting-the-data"></a><span data-ttu-id="f70fc-106">排序資料</span><span class="sxs-lookup"><span data-stu-id="f70fc-106">Sorting the Data</span></span>  
 <span data-ttu-id="f70fc-107">您可以使用下列其中一個方法來排序此資料：</span><span class="sxs-lookup"><span data-stu-id="f70fc-107">You can sort this data by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="f70fc-108">在來源的陳述式中，使用載入資料所使用的 ORDER BY 子句。</span><span class="sxs-lookup"><span data-stu-id="f70fc-108">In the source, use an ORDER BY clause in the statement that is used to load the data.</span></span>  
  
-   <span data-ttu-id="f70fc-109">在資料流程中，將「排序」轉換插入到「合併」或「合併聯結」轉換之前。</span><span class="sxs-lookup"><span data-stu-id="f70fc-109">In the data flow, insert a Sort transformation before the Merge or Merge Join transformation.</span></span>  
  
 <span data-ttu-id="f70fc-110">如果資料是字串資料，「合併」和「合併聯結」轉換都會預期這些字串值已經使用 Windows 定序排序了。</span><span class="sxs-lookup"><span data-stu-id="f70fc-110">If the data is string data, both the Merge and Merge Join transformations expect the string values to have been sorted by using Windows collation.</span></span> <span data-ttu-id="f70fc-111">若要提供字串值給使用 Windows 定序排序的「合併」和「合併聯結」轉換，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="f70fc-111">To provide string values to the Merge and Merge Join transformations that are sorted by using Windows collation, use the following procedure.</span></span>  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a><span data-ttu-id="f70fc-112">若要提供使用 Windows 定序排序的字串值</span><span class="sxs-lookup"><span data-stu-id="f70fc-112">To provide string values that are sorted by using Windows collation</span></span>  
  
-   <span data-ttu-id="f70fc-113">使用「排序」轉換來排序資料。</span><span class="sxs-lookup"><span data-stu-id="f70fc-113">Use a Sort transformation to sort the data.</span></span>  
  
     <span data-ttu-id="f70fc-114">「排序」轉換會使用 Windows 定序來排序字串值。</span><span class="sxs-lookup"><span data-stu-id="f70fc-114">The Sort transformation uses Windows collation to sort string values.</span></span>  
  
     <span data-ttu-id="f70fc-115">-或-</span><span class="sxs-lookup"><span data-stu-id="f70fc-115">-or-</span></span>  
  
-   <span data-ttu-id="f70fc-116">使用 Transact-SQL CAST 運算子，先將 `varchar` 值轉換成 `nvarchar` 值，然後再使用 Transact-SQL ORDER BY 子句來排序資料。</span><span class="sxs-lookup"><span data-stu-id="f70fc-116">Use the Transact-SQL CAST operator to first cast `varchar` values to `nvarchar` values, and then use the Transact-SQL ORDER BY clause to sort the data.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f70fc-117">您無法單獨使用 ORDER BY 子句，因為 ORDER BY 子句會使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 定序來排序字串值。</span><span class="sxs-lookup"><span data-stu-id="f70fc-117">You cannot use the ORDER BY clause alone because the ORDER BY clause uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation to sort string values.</span></span> <span data-ttu-id="f70fc-118">如果您使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 定序，可能會產生與 Windows 定序不同的排序次序，進而導致「合併」或「合併聯結」轉換產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="f70fc-118">The use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] collation might result in a different sort order than Windows collation, which can cause the Merge or Merge Join transformation to produce unexpected results.</span></span>  
  
## <a name="setting-sort-options-on-the-data"></a><span data-ttu-id="f70fc-119">設定資料的排序選項</span><span class="sxs-lookup"><span data-stu-id="f70fc-119">Setting Sort Options on the Data</span></span>  
 <span data-ttu-id="f70fc-120">有兩個重要的排序屬性必須針對將資料提供給「合併」和「合併聯結」轉換的來源或上游轉換設定：</span><span class="sxs-lookup"><span data-stu-id="f70fc-120">There are two important sort properties that must be set for the source or upstream transformation that supplies data to the Merge and Merge Join transformations:</span></span>  
  
-   <span data-ttu-id="f70fc-121">輸出的 `IsSorted` 屬性，表示資料是否經過排序。</span><span class="sxs-lookup"><span data-stu-id="f70fc-121">The `IsSorted` property of the output that indicates whether the data has been sorted.</span></span> <span data-ttu-id="f70fc-122">此屬性必須設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="f70fc-122">This property must be set to `True`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f70fc-123">將 `IsSorted` 屬性的值設定為 `True` 時，不會排序資料。</span><span class="sxs-lookup"><span data-stu-id="f70fc-123">Setting the value of the `IsSorted` property to `True` does not sort the data.</span></span> <span data-ttu-id="f70fc-124">此屬性僅針對資料先前已經過排序的下游元件提供提示。</span><span class="sxs-lookup"><span data-stu-id="f70fc-124">This property only provides a hint to downstream components that the data has been previously sorted.</span></span>  
  
-   <span data-ttu-id="f70fc-125">輸出資料行的 `SortKeyPosition` 屬性，指出資料行是否經過排序、資料行的排序次序，以及排序多個資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="f70fc-125">The `SortKeyPosition` property of output columns that indicates whether a column is sorted, the column's sort order, and the sequence in which multiple columns are sorted.</span></span> <span data-ttu-id="f70fc-126">此屬性必須針對已排序資料的每個資料行設定。</span><span class="sxs-lookup"><span data-stu-id="f70fc-126">This property must be set for each column of sorted data.</span></span>  
  
 <span data-ttu-id="f70fc-127">如果您使用「排序」轉換排序資料，「排序」轉換會同時設定「合併」或「合併聯結」轉換所需的屬性。</span><span class="sxs-lookup"><span data-stu-id="f70fc-127">If you use a Sort transformation to sort the data, the Sort transformation sets both of these properties as required by the Merge or Merge Join transformation.</span></span> <span data-ttu-id="f70fc-128">也就是說，「排序」轉換會將其輸出的 `IsSorted` 屬性設定為 `True`，並設定其輸出資料行的 `SortKeyPosition` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f70fc-128">That is, the Sort transformation sets the `IsSorted` property of its output to `True`, and sets the `SortKeyPosition` properties of its output columns.</span></span>  
  
 <span data-ttu-id="f70fc-129">不過，如果您沒有使用「排序」轉換排序資料，則必須在來源或上游轉換手動設定這些排序屬性。</span><span class="sxs-lookup"><span data-stu-id="f70fc-129">However, if you do not use a Sort transformation to sort the data, you must set these sort properties manually on the source or the upstream transformation.</span></span> <span data-ttu-id="f70fc-130">若要在來源或上游轉換手動設定排序屬性，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="f70fc-130">To manually set the sort properties on the source or upstream transformation, use the following procedure.</span></span>  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a><span data-ttu-id="f70fc-131">若要手動在來源或轉換元件上設定排序屬性</span><span class="sxs-lookup"><span data-stu-id="f70fc-131">To manually set sort attributes on a source or transformation component</span></span>  
  
1.  <span data-ttu-id="f70fc-132">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f70fc-132">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f70fc-133">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="f70fc-133">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f70fc-134">在 **[資料流程]** 索引標籤上，找出適當的來源或上游轉換，或者將其從 **[工具箱]** 拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="f70fc-134">On the **Data Flow** tab, locate the appropriate source or upstream transformation, or drag it from the **Toolbox** to the design surface.</span></span>  
  
4.  <span data-ttu-id="f70fc-135">以滑鼠右鍵按一下元件，然後按一下 [顯示進階編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="f70fc-135">Right-click the component and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="f70fc-136">按一下 **[輸入與輸出屬性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f70fc-136">Click the **Input and Output Properties** tab.</span></span>  
  
6.  <span data-ttu-id="f70fc-137">按一下 [ \*\* \<component name> 輸出\*\*]，並將 `IsSorted` 屬性設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="f70fc-137">Click **\<component name> Output**, and set the `IsSorted` property to `True`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f70fc-138">如果您手動將輸出的 `IsSorted` 屬性設定為 `True` 而且資料未排序，則當您執行封裝時，下游「合併」或「合併聯結」轉換中可能會有資料遺失或是不正確的資料比較。</span><span class="sxs-lookup"><span data-stu-id="f70fc-138">If you manually set the `IsSorted` property of the output to `True` and the data is not sorted, there might be missing data or bad data comparisons in the downstream Merge or Merge Join transformation when you run the package.</span></span>  
  
7.  <span data-ttu-id="f70fc-139">展開 **[輸出資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="f70fc-139">Expand **Output Columns**.</span></span>  
  
8.  <span data-ttu-id="f70fc-140">按一下要表示為已排序的資料行，並按照下列指導方針，將其 `SortKeyPosition` 屬性設定為非零整數值：</span><span class="sxs-lookup"><span data-stu-id="f70fc-140">Click the column that you want to indicate is sorted and set its `SortKeyPosition` property to a nonzero integer value by following these guidelines:</span></span>  
  
    -   <span data-ttu-id="f70fc-141">整數值必須表示數值順序，且從 1 開始並以 1 為遞增值。</span><span class="sxs-lookup"><span data-stu-id="f70fc-141">The integer value must represent a numeric sequence, starting with 1 and incremented by 1.</span></span>  
  
    -   <span data-ttu-id="f70fc-142">正整數值表示遞增排序次序。</span><span class="sxs-lookup"><span data-stu-id="f70fc-142">A positive integer value indicates an ascending sort order.</span></span>  
  
    -   <span data-ttu-id="f70fc-143">負整數值表示遞減排序次序</span><span class="sxs-lookup"><span data-stu-id="f70fc-143">A negative integer value indicates a descending sort order.</span></span> <span data-ttu-id="f70fc-144">(如果設定為負數，數字的絕對值會決定資料行在排序順序中的位置)。</span><span class="sxs-lookup"><span data-stu-id="f70fc-144">(If set to a negative number, the absolute value of the number determines the column's position in the sort sequence.)</span></span>  
  
    -   <span data-ttu-id="f70fc-145">預設值 0 表示未排序資料行。</span><span class="sxs-lookup"><span data-stu-id="f70fc-145">The default value of 0 indicates that the column is not sorted.</span></span> <span data-ttu-id="f70fc-146">針對不參與排序的輸出資料行，將其值保留為 0。</span><span class="sxs-lookup"><span data-stu-id="f70fc-146">Leave the value of 0 for output columns that do not participate in the sort.</span></span>  
  
     <span data-ttu-id="f70fc-147">關於如何設定 `SortKeyPosition` 屬性的範例，請考慮使用將資料載入來源的下列 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="f70fc-147">As an example of how to set the `SortKeyPosition` property, consider the following Transact-SQL statement that loads data in a source:</span></span>  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     <span data-ttu-id="f70fc-148">針對此陳述式，設定每個資料行的 `SortKeyPosition` 屬性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f70fc-148">For this statement, you would set the `SortKeyPosition` property for each column as follows:</span></span>  
  
    -   <span data-ttu-id="f70fc-149">將 ColumnA 的 `SortKeyPosition` 屬性設定為 1。</span><span class="sxs-lookup"><span data-stu-id="f70fc-149">Set the `SortKeyPosition` property of ColumnA to 1.</span></span> <span data-ttu-id="f70fc-150">這表示 ColumnA 是要排序的第一個資料行，而且是以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="f70fc-150">This indicates that ColumnA is the first column to be sorted and is sorted in ascending order.</span></span>  
  
    -   <span data-ttu-id="f70fc-151">將 ColumnB 的 `SortKeyPosition` 屬性設定為 -2。</span><span class="sxs-lookup"><span data-stu-id="f70fc-151">Set the `SortKeyPosition` property of ColumnB to -2.</span></span> <span data-ttu-id="f70fc-152">這表示 ColumnB 是要排序的第二個資料行，而且是以遞減順序排序</span><span class="sxs-lookup"><span data-stu-id="f70fc-152">This indicates that ColumnB is the second column to be sorted and is sorted in descending order</span></span>  
  
    -   <span data-ttu-id="f70fc-153">將 ColumnC 的 `SortKeyPosition` 屬性設定為 3。</span><span class="sxs-lookup"><span data-stu-id="f70fc-153">Set the `SortKeyPosition` property of ColumnC to 3.</span></span> <span data-ttu-id="f70fc-154">這表示 ColumnC 是要排序的第三個資料行，而且是以遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="f70fc-154">This indicates that ColumnC is the third column to be sorted and is sorted in ascending order.</span></span>  
  
9. <span data-ttu-id="f70fc-155">針對每個已排序的資料行重複步驟 8。</span><span class="sxs-lookup"><span data-stu-id="f70fc-155">Repeat step 8 for each sorted column.</span></span>  
  
10. <span data-ttu-id="f70fc-156">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f70fc-156">Click **OK**.</span></span>  
  
11. <span data-ttu-id="f70fc-157">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="f70fc-157">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70fc-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f70fc-158">See Also</span></span>  
 <span data-ttu-id="f70fc-159">[合併轉換](merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="f70fc-159">[Merge Transformation](merge-transformation.md) </span></span>  
 <span data-ttu-id="f70fc-160">[合併聯結轉換](merge-join-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="f70fc-160">[Merge Join Transformation](merge-join-transformation.md) </span></span>  
 <span data-ttu-id="f70fc-161">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="f70fc-161">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="f70fc-162">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="f70fc-162">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="f70fc-163">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="f70fc-163">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
