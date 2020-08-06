---
title: Aggregate 函式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fcc65f1e60c29ba9ea6a4206b419eb0b13edb0ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596496"
---
# <a name="aggregate-function-report-builder-and-ssrs"></a><span data-ttu-id="20b47-102">彙總函式 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="20b47-102">Aggregate Function (Report Builder and SSRS)</span></span>
  <span data-ttu-id="20b47-103">傳回指定之運算式的自訂彙總，由資料提供者定義。</span><span class="sxs-lookup"><span data-stu-id="20b47-103">Returns a custom aggregate of the specified expression, as defined by the data provider.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a><span data-ttu-id="20b47-104">語法</span><span class="sxs-lookup"><span data-stu-id="20b47-104">Syntax</span></span>  
  
```  
  
Aggregate(expression, scope)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20b47-105">參數</span><span class="sxs-lookup"><span data-stu-id="20b47-105">Parameters</span></span>  
 <span data-ttu-id="20b47-106">*expression*</span><span class="sxs-lookup"><span data-stu-id="20b47-106">*expression*</span></span>  
 <span data-ttu-id="20b47-107">要在其上執行彙總的運算式。</span><span class="sxs-lookup"><span data-stu-id="20b47-107">The expression on which to perform the aggregation.</span></span> <span data-ttu-id="20b47-108">此運算式必須為簡單欄位參考。</span><span class="sxs-lookup"><span data-stu-id="20b47-108">The expression must be a simple field reference.</span></span>  
  
 <span data-ttu-id="20b47-109">*範圍 (scope)*</span><span class="sxs-lookup"><span data-stu-id="20b47-109">*scope*</span></span>  
 <span data-ttu-id="20b47-110">(`String`) 包含要套用彙總函式之報表項目的資料集、群組或資料區的名稱。</span><span class="sxs-lookup"><span data-stu-id="20b47-110">(`String`) The name of a dataset, group, or data region that contains the report items to which to apply the aggregate function.</span></span> <span data-ttu-id="20b47-111">*Scope* 必須是字串常數，而且不得為運算式。</span><span class="sxs-lookup"><span data-stu-id="20b47-111">*Scope* must be a string constant andcannot be an expression.</span></span> <span data-ttu-id="20b47-112">如果未指定 *scope* ，則使用目前的範圍。</span><span class="sxs-lookup"><span data-stu-id="20b47-112">If *scope* is not specified, the current scope is used.</span></span>  
  
## <a name="return-type"></a><span data-ttu-id="20b47-113">傳回類型</span><span class="sxs-lookup"><span data-stu-id="20b47-113">Return Type</span></span>  
 <span data-ttu-id="20b47-114">傳回類型是由資料提供者決定。</span><span class="sxs-lookup"><span data-stu-id="20b47-114">Return type is determined by the data provider.</span></span> <span data-ttu-id="20b47-115">如果資料提供者不支援此函數或無法使用資料，則傳回 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="20b47-115">Returns `Nothing` if the data provider does not support this function or data is not available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20b47-116">備註</span><span class="sxs-lookup"><span data-stu-id="20b47-116">Remarks</span></span>  
 <span data-ttu-id="20b47-117">`Aggregate` 函數會提供一個方式來使用在外部資料來源上計算的彙總。</span><span class="sxs-lookup"><span data-stu-id="20b47-117">The `Aggregate` function provides a way to use aggregates that are calculated on the external data source.</span></span> <span data-ttu-id="20b47-118">這個功能的支援是由資料延伸模組所決定。</span><span class="sxs-lookup"><span data-stu-id="20b47-118">Support for this feature is determined by the data extension.</span></span> <span data-ttu-id="20b47-119">例如，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料處理延伸模組會從 MDX 查詢擷取扁平化的資料列集。</span><span class="sxs-lookup"><span data-stu-id="20b47-119">For example, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension retrieves flattened rowsets from an MDX query.</span></span> <span data-ttu-id="20b47-120">結果集中的某些資料列可能會包含在資料來源伺服器上計算的彙總值。</span><span class="sxs-lookup"><span data-stu-id="20b47-120">Some rows in the result set can contain aggregate values calculated on the data source server.</span></span> <span data-ttu-id="20b47-121">這些值稱為 *「伺服器彙總」* (Server Aggregate)。</span><span class="sxs-lookup"><span data-stu-id="20b47-121">These are known as *server aggregates*.</span></span> <span data-ttu-id="20b47-122">若要在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的圖形化查詢設計工具中檢視伺服器彙總，可以使用工具列的 **[顯示彙總]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="20b47-122">To view server aggregates in the graphical query designer for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the **Show Aggregate** button on the toolbar.</span></span> <span data-ttu-id="20b47-123">如需詳細資訊，請參閱 [Analysis Services MDX 查詢設計工具使用者介面 &#40;報表產生器&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="20b47-123">For more information, see [Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md).</span></span>  
  
 <span data-ttu-id="20b47-124">當您在 Tablix 資料區域的詳細資料列中顯示彙總和詳細資料集值的組合時，一般並不會包含伺服器彙總，因為這些值並非詳細資料。</span><span class="sxs-lookup"><span data-stu-id="20b47-124">When you display the combination of aggregate and detail dataset values on detail rows of a Tablix data region, server aggregates would not typically be included because they are not detail data.</span></span> <span data-ttu-id="20b47-125">不過，您可以顯示針對資料集所擷取的所有值，並自訂計算及顯示彙總資料的方式。</span><span class="sxs-lookup"><span data-stu-id="20b47-125">However, you may want to display all values retrieved for the dataset and customize the way aggregate data is calculated and displayed.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="20b47-126">會在報表的運算式中偵測 `Aggregate` 函數的使用，以用來判斷是否要在詳細資料列中顯示伺服器彙總。</span><span class="sxs-lookup"><span data-stu-id="20b47-126">detects the use of the `Aggregate` function in expressions in your report in order to determine whether to display server aggregates on detail rows.</span></span> <span data-ttu-id="20b47-127">如果在資料區域的運算式中包含 `Aggregate`，則伺服器彙總只會顯示在群組總計或總計資料列中，而不會顯示在詳細資料列中。</span><span class="sxs-lookup"><span data-stu-id="20b47-127">If you include `Aggregate` in an expression in a data region, server aggregates can only appear on group total or grand total rows, not on detail rows.</span></span> <span data-ttu-id="20b47-128">如果想要在詳細資料列中顯示伺服器彙總，請不要使用 `Aggregate` 函數。</span><span class="sxs-lookup"><span data-stu-id="20b47-128">If you want to display server aggregates on detail rows, do not use the `Aggregate` function.</span></span>  
  
 <span data-ttu-id="20b47-129">您可以藉由變更 **[資料集屬性]** 對話方塊的 **[將小計當做詳細資料列]** 選項值來變更這項預設行為。</span><span class="sxs-lookup"><span data-stu-id="20b47-129">You can change this default behavior by changing the value of the **Interpret subtotals as details** option on the **Dataset Properties** dialog box.</span></span> <span data-ttu-id="20b47-130">當這個選項是設定為 `True` 時，所有的資料 (包括伺服器彙總) 會顯示為詳細資料。</span><span class="sxs-lookup"><span data-stu-id="20b47-130">When this option is set to `True`, all data, including server aggregates, appears as detail data.</span></span> <span data-ttu-id="20b47-131">當設定為 `False` 時，伺服器彙總會顯示為總計。</span><span class="sxs-lookup"><span data-stu-id="20b47-131">When set to `False`, server aggregates appear as totals.</span></span> <span data-ttu-id="20b47-132">這個屬性的設定會影響連結至這個資料集的所有資料區域。</span><span class="sxs-lookup"><span data-stu-id="20b47-132">The setting for this property affects all data regions that are linked to this dataset.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20b47-133">所有參考 `Aggregate` 的報表項目的包含群組都必須有其群組運算式的簡單欄位參考，例如 `[FieldName]`。</span><span class="sxs-lookup"><span data-stu-id="20b47-133">All containing groups for the report item that references `Aggregate` must have simple field references for their group expressions, for example, `[FieldName]`.</span></span> <span data-ttu-id="20b47-134">您不能在使用複雜群組運算式的資料區域中使用 `Aggregate`。</span><span class="sxs-lookup"><span data-stu-id="20b47-134">You cannot use `Aggregate` in a data region that uses complex group expressions.</span></span> <span data-ttu-id="20b47-135">若是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料處理延伸模組，則您的查詢必須包含 `LevelProperty` 類型 (而非`MemberProperty`) 的 MDX 欄位，才可支援使用 `Aggregate` 函數的彙總。</span><span class="sxs-lookup"><span data-stu-id="20b47-135">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data processing extension, your query must include MDX fields of type `LevelProperty` (not `MemberProperty`) to support aggregation using the `Aggregate`function.</span></span>  
  
 <span data-ttu-id="20b47-136">*Expression* 可以包含巢狀彙總函式的呼叫，其中包含下列例外和條件：</span><span class="sxs-lookup"><span data-stu-id="20b47-136">*Expression* can contain calls to nested aggregate functions with the following exceptions and conditions:</span></span>  
  
-   <span data-ttu-id="20b47-137">巢狀彙總的*Scope* 必須與外部彙總的範圍相同或是由外部彙總的範圍所限制。</span><span class="sxs-lookup"><span data-stu-id="20b47-137">*Scope* for nested aggregates must be the same as, or contained by, the scope of the outer aggregate.</span></span> <span data-ttu-id="20b47-138">如果是運算式中的所有相異範圍，一個範圍必須與所有其他範圍之間具有子關聯性。</span><span class="sxs-lookup"><span data-stu-id="20b47-138">For all distinct scopes in the expression, one scope must be in a child relationship to all other scopes.</span></span>  
  
-   <span data-ttu-id="20b47-139">巢狀彙總的*Scope* 不得為資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="20b47-139">*Scope* for nested aggregates cannot be the name of a dataset.</span></span>  
  
-   <span data-ttu-id="20b47-140">*運算式*不能包含 `First` 、 `Last` 、 `Previous` 或 `RunningValue` 函數。</span><span class="sxs-lookup"><span data-stu-id="20b47-140">*Expression* must not contain `First`, `Last`, `Previous`, or `RunningValue` functions.</span></span>  
  
-   <span data-ttu-id="20b47-141">*Expression* 不得包含指定 *recursive*的巢狀彙總。</span><span class="sxs-lookup"><span data-stu-id="20b47-141">*Expression* must not contain nested aggregates that specify *recursive*.</span></span>  
  
 <span data-ttu-id="20b47-142">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 和[總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="20b47-142">For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
 <span data-ttu-id="20b47-143">如需遞迴彙總的詳細資訊，請參閱[建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="20b47-143">For more information about recursive aggregates, see [Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).</span></span>  
  
## <a name="comparing-the-aggregate-and-sum-functions"></a><span data-ttu-id="20b47-144">比較 Aggregate 和 Sum 函數</span><span class="sxs-lookup"><span data-stu-id="20b47-144">Comparing the Aggregate and Sum Functions</span></span>  
 <span data-ttu-id="20b47-145">`Aggregate` 函數與 `Sum` 之類的數值彙總函式的不同點在於 `Aggregate` 函數會傳回資料提供者或資料處理延伸模組所計算的值。</span><span class="sxs-lookup"><span data-stu-id="20b47-145">The `Aggregate` function differs from numeric aggregate functions like `Sum` in that the `Aggregate` function returns a value that is calculated by the data provider or data processing extension.</span></span> <span data-ttu-id="20b47-146">數值彙總函式（例如）會傳回一個 `Sum` 值，而報表處理器會根據*範圍*參數所決定之資料集的一組資料來計算該值。</span><span class="sxs-lookup"><span data-stu-id="20b47-146">Numeric aggregate functions like `Sum` return a value that is calculated by the report processor on a set of data from the dataset that is determined by the *scope* parameter.</span></span> <span data-ttu-id="20b47-147">如需詳細資訊，請參閱[彙總函式參考 &#40;報表產生器及 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) 中列出的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="20b47-147">For more information, see the aggregate functions listed in [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20b47-148">範例</span><span class="sxs-lookup"><span data-stu-id="20b47-148">Example</span></span>  
 <span data-ttu-id="20b47-149">下列程式碼範例顯示的運算式會擷取欄位 `LineTotal`的伺服器彙總。</span><span class="sxs-lookup"><span data-stu-id="20b47-149">The following code example shows an expression that retrieves a server aggregate for the field `LineTotal`.</span></span> <span data-ttu-id="20b47-150">運算式會加到屬於群組 `GroupbyOrder`的資料列中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="20b47-150">The expression is added to a cell in a row that belongs to the group `GroupbyOrder`.</span></span>  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## <a name="see-also"></a><span data-ttu-id="20b47-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20b47-151">See Also</span></span>  
 <span data-ttu-id="20b47-152">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="20b47-152">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="20b47-153">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="20b47-153">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="20b47-154">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="20b47-154">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="20b47-155">總計、彙總與內建集合的運算式範圍 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="20b47-155">Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;</span></span>](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
