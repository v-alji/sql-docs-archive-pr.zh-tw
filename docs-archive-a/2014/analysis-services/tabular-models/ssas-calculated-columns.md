---
title: " (SSAS 表格式) 的計算結果欄 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e1011278-556d-4984-b01d-a37f8a33b304
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5d77b36ee3327d1b9e0d31ac97e5dbe135093a63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686482"
---
# <a name="calculated-columns-ssas-tabular"></a><span data-ttu-id="2eecf-102">導出資料行 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="2eecf-102">Calculated Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="2eecf-103">表格式模型中的導出資料行可讓您將新資料加入至模型。</span><span class="sxs-lookup"><span data-stu-id="2eecf-103">Calculated columns, in tabular models, allow you to add new data to your model.</span></span> <span data-ttu-id="2eecf-104">您可以建立 DAX 公式來定義資料行的資料列層級值，而不是將值貼入或匯入資料行。</span><span class="sxs-lookup"><span data-stu-id="2eecf-104">Instead of pasting or importing values into the column, you create a DAX formula that defines the column's row level values.</span></span> <span data-ttu-id="2eecf-105">然後就可以像是其他任何資料行一樣，在報表、樞紐分析表或樞紐分析圖中使用導出資料行。</span><span class="sxs-lookup"><span data-stu-id="2eecf-105">The calculated column can then be used in a report, PivotTable, or PivotChart as would any other column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2eecf-106">在 DirectQuery 模式下的表格式模型不支援導出資料行。</span><span class="sxs-lookup"><span data-stu-id="2eecf-106">Calculated columns are not supported for tabular models in DirectQuery mode.</span></span> <span data-ttu-id="2eecf-107">如需詳細資訊，請參閱 [DirectQuery 模式 &#40;SSAS 表格式&#41;](directquery-mode-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="2eecf-107">For more information, see [DirectQuery Mode &#40;SSAS Tabular&#41;](directquery-mode-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="2eecf-108">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="2eecf-108">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="2eecf-109">優點</span><span class="sxs-lookup"><span data-stu-id="2eecf-109">Benefits</span></span>](#bkmk_understanding)  
  
-   [<span data-ttu-id="2eecf-110">命名計算結果欄</span><span class="sxs-lookup"><span data-stu-id="2eecf-110">Naming a Calculated Column</span></span>](#bkmk_naming)  
  
-   [<span data-ttu-id="2eecf-111">計算結果欄的效能</span><span class="sxs-lookup"><span data-stu-id="2eecf-111">Performance of Calculated Columns</span></span>](#bkmk_perf)  
  
-   [<span data-ttu-id="2eecf-112">相關工作</span><span class="sxs-lookup"><span data-stu-id="2eecf-112">Related Tasks</span></span>](#bkmk_rel_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_understanding"></a> <span data-ttu-id="2eecf-113">優點</span><span class="sxs-lookup"><span data-stu-id="2eecf-113">Benefits</span></span>  
 <span data-ttu-id="2eecf-114">導出資料行中的公式與 Excel 中的公式非常類似。</span><span class="sxs-lookup"><span data-stu-id="2eecf-114">Formulas in calculated columns are much like formulas in Excel.</span></span> <span data-ttu-id="2eecf-115">然而與 Excel 不同的是，您不能為資料表中不同的資料列建立不同的公式，DAX 公式會自動套用到整個資料行。</span><span class="sxs-lookup"><span data-stu-id="2eecf-115">Unlike Excel, however, you cannot create different formulas for different rows in a table; instead, the DAX formula is automatically applied to the entire column.</span></span>  
  
 <span data-ttu-id="2eecf-116">當資料行包含公式時，會針對每個資料列計算其值。</span><span class="sxs-lookup"><span data-stu-id="2eecf-116">When a column contains a formula, the value is computed for each row.</span></span> <span data-ttu-id="2eecf-117">當您輸入有效的公式時，即會計算資料行的結果。</span><span class="sxs-lookup"><span data-stu-id="2eecf-117">The results are calculated for the column when you enter a valid formula.</span></span> <span data-ttu-id="2eecf-118">資料行值日後將視需要進行重新計算，例如當基礎資料重新整理之時。</span><span class="sxs-lookup"><span data-stu-id="2eecf-118">Column values are then recalculated as necessary, such as when the underlying data is refreshed.</span></span>  
  
 <span data-ttu-id="2eecf-119">您可以根據量值及其他導出資料行，建立導出資料行。</span><span class="sxs-lookup"><span data-stu-id="2eecf-119">You can create calculated columns that are based on measures and other calculated columns.</span></span> <span data-ttu-id="2eecf-120">例如，您可以建立一個導出資料行，以便從文字字串中擷取數字，然後將該數字使用在另一個導出資料行中。</span><span class="sxs-lookup"><span data-stu-id="2eecf-120">For example, you might create one calculated column to extract a number from a string of text, and then use that number in another calculated column.</span></span>  
  
 <span data-ttu-id="2eecf-121">導出資料行會以現有資料表中的資料為基礎，或透過 DAX 公式建立。</span><span class="sxs-lookup"><span data-stu-id="2eecf-121">A calculated column is based on data that you already have in an existing table, or created by using a DAX formula.</span></span> <span data-ttu-id="2eecf-122">例如，您可以選擇串連值、執行加法、擷取子字串，或比較其他欄位中的值。</span><span class="sxs-lookup"><span data-stu-id="2eecf-122">For example, you might choose to concatenate values, perform addition, extract substrings, or compare the values in other fields.</span></span> <span data-ttu-id="2eecf-123">若要加入導出資料行，模型中至少必須有一個資料表。</span><span class="sxs-lookup"><span data-stu-id="2eecf-123">To add a calculated column, you must have at least one table in your model.</span></span>  
  
 <span data-ttu-id="2eecf-124">此範例示範導出資料行中的簡單公式：</span><span class="sxs-lookup"><span data-stu-id="2eecf-124">This example demonstrates a simple formula in a calculated column:</span></span>  
  
```  
=EOMONTH([StartDate],0])  
  
```  
  
 <span data-ttu-id="2eecf-125">此公式從 StartDate 資料行中擷取月份。</span><span class="sxs-lookup"><span data-stu-id="2eecf-125">This formula extracts the month from the StartDate column.</span></span> <span data-ttu-id="2eecf-126">接著再計算資料表中每個資料列的月底值。</span><span class="sxs-lookup"><span data-stu-id="2eecf-126">It then calculates the end of the month value for each row in the table.</span></span> <span data-ttu-id="2eecf-127">第二個參數是指定在 StartDate 當月之前或之後的月數，本例為 0 即表示同一個月份。</span><span class="sxs-lookup"><span data-stu-id="2eecf-127">The second parameter specifies the number of months before or after the month in StartDate; in this case, 0 means the same month.</span></span> <span data-ttu-id="2eecf-128">例如，若 StartDate 資料行的值為 6/1/2001，則導出資料行的值將是 6/30/2001。</span><span class="sxs-lookup"><span data-stu-id="2eecf-128">For example, if the value in the StartDate column is 6/1/2001, the value in the calculated column will be 6/30/2001.</span></span>  
  
##  <a name="naming-a-calculated-column"></a><a name="bkmk_naming"></a><span data-ttu-id="2eecf-129">命名計算結果欄</span><span class="sxs-lookup"><span data-stu-id="2eecf-129">Naming a Calculated Column</span></span>  
 <span data-ttu-id="2eecf-130">根據預設，新的導出資料行會加入至資料表中其他資料行的右邊，而且將自動為這類資料行指派預設名稱 **CalculatedColumn1**、 **CalculatedColumn2**，依此類推。</span><span class="sxs-lookup"><span data-stu-id="2eecf-130">By default, new calculated columns are added to the right of other columns in a table, and the column is automatically assigned the default name of **CalculatedColumn1**, **CalculatedColumn2**, and so forth.</span></span> <span data-ttu-id="2eecf-131">您也可以在資料行上按一下滑鼠右鍵，然後按一下 [插入資料行]，在兩個現有的資料行之間建立新資料行。</span><span class="sxs-lookup"><span data-stu-id="2eecf-131">You can also right click a column, and then click Insert Column to create a new column between two existing columns.</span></span> <span data-ttu-id="2eecf-132">您可以按一下再拖曳，來重新排列相同資料表中的資料行，也可以在建立資料行之後，重新命名資料行；但是，您應該注意下列有關變更導出資料行的限制：</span><span class="sxs-lookup"><span data-stu-id="2eecf-132">You can rearrange columns within the same table by clicking and dragging, and you can rename columns after they are created; however, you should be aware of the following restrictions on changes to calculated columns:</span></span>  
  
-   <span data-ttu-id="2eecf-133">每個資料行名稱在資料表中都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2eecf-133">Each column name must be unique within a table.</span></span>  
  
-   <span data-ttu-id="2eecf-134">在相同的模型中，請避免使用已經用於量值的名稱。</span><span class="sxs-lookup"><span data-stu-id="2eecf-134">Avoid names that have already been used for measures within the same model.</span></span> <span data-ttu-id="2eecf-135">雖然量值和導出資料行可能使用相同的名稱，但是如果這些名稱不是唯一的，可能會發生計算錯誤。</span><span class="sxs-lookup"><span data-stu-id="2eecf-135">Although it is possible for a measure and a calculated column to have the same name, if names are not unique you can get calculation errors.</span></span> <span data-ttu-id="2eecf-136">為避免不小心叫用量值，如果指的是資料行，請務必使用完整的資料行參考。</span><span class="sxs-lookup"><span data-stu-id="2eecf-136">To avoid accidentally invoking a measure, when referring to a column always use a fully qualified column reference.</span></span>  
  
-   <span data-ttu-id="2eecf-137">當您重新命名導出資料行時，必須手動更新依賴此資料行的所有公式。</span><span class="sxs-lookup"><span data-stu-id="2eecf-137">When you rename a calculated column, any formulas that rely on the column must be updated manually.</span></span> <span data-ttu-id="2eecf-138">只要您不是處於手動更新模式，公式的結果都會自動更新。</span><span class="sxs-lookup"><span data-stu-id="2eecf-138">Unless you are in manual update mode, updating the results of formulas takes place automatically.</span></span> <span data-ttu-id="2eecf-139">不過，這項作業可能需要花一些時間。</span><span class="sxs-lookup"><span data-stu-id="2eecf-139">However, this operation might take some time.</span></span>  
  
-   <span data-ttu-id="2eecf-140">資料行的名稱中不能使用某些字元。</span><span class="sxs-lookup"><span data-stu-id="2eecf-140">There are some characters that cannot be used within the names of columns.</span></span> <span data-ttu-id="2eecf-141">如需詳細資訊，請參閱 [PowerPivot 的 DAX 語法規格](/dax/dax-syntax-reference)中的＜命名需求＞。</span><span class="sxs-lookup"><span data-stu-id="2eecf-141">For more information, see "Naming Requirements" in [DAX Syntax Specification for PowerPivot](/dax/dax-syntax-reference).</span></span>  
  
##  <a name="performance-of-calculated-columns"></a><a name="bkmk_perf"></a><span data-ttu-id="2eecf-142">計算結果欄的效能</span><span class="sxs-lookup"><span data-stu-id="2eecf-142">Performance of Calculated Columns</span></span>  
 <span data-ttu-id="2eecf-143">導出資料行的公式可能會比量值所使用的公式更耗費資源。</span><span class="sxs-lookup"><span data-stu-id="2eecf-143">The formula for a calculated column can be more resource-intensive than the formula used for a measure.</span></span> <span data-ttu-id="2eecf-144">其中一個原因是：導出資料行的結果永遠是針對資料表中的每個資料列計算，而量值僅針對報表、樞紐分析表或樞紐分析圖中所用篩選定義的資料格計算。</span><span class="sxs-lookup"><span data-stu-id="2eecf-144">One reason is that the result for a calculated column is always calculated for each row in a table, whereas a measure is only calculated for the cells defined by the filter used in a report, PivotTable, or PivotChart.</span></span> <span data-ttu-id="2eecf-145">例如，包含一百萬個資料列的資料表所擁有的導出資料行永遠都會有一百萬個結果，在效能上也會有對應的影響。</span><span class="sxs-lookup"><span data-stu-id="2eecf-145">For example, a table with a million rows will always have a calculated column with a million results, and a corresponding effect on performance.</span></span> <span data-ttu-id="2eecf-146">但是，樞紐分析表通常會套用資料列和資料行標題來篩選資料，因此，只會針對樞紐分析表內每一個資料格中的資料子集來計算量值。</span><span class="sxs-lookup"><span data-stu-id="2eecf-146">However, a PivotTable generally filters data by applying row and column headings; therefore, a measure is calculated only for the subset of data in each cell of the PivotTable.</span></span>  
  
 <span data-ttu-id="2eecf-147">公式通常與該公式中參考之物件具有相依性，例如評估值的其他資料行或運算式。</span><span class="sxs-lookup"><span data-stu-id="2eecf-147">A formula has dependencies on the objects that are referenced in the formula, such as other columns or expressions that evaluate values.</span></span> <span data-ttu-id="2eecf-148">舉例來說，以另一個資料行做為根據的導出資料行或是包含具有資料行參考之運算式的計算，必須等到評估另一個資料行的結果之後，才會評估出結果。</span><span class="sxs-lookup"><span data-stu-id="2eecf-148">For example, a calculated column that is based on another column, or a calculation that contains an expression with a column reference, cannot be evaluated until the other column is evaluated.</span></span> <span data-ttu-id="2eecf-149">預設情況下，活頁簿會啟用自動重新整理，因此在更新值或重新整理公式時，任何這類相依性都有可能影響效能。</span><span class="sxs-lookup"><span data-stu-id="2eecf-149">By default, automatic refresh is enabled in workbooks; therefore, all such dependencies can affect performance while values are updated and formulas refreshed.</span></span>  
  
 <span data-ttu-id="2eecf-150">為了避免當您在建立導出資料行時發生效能問題，請遵循以下指導方針：</span><span class="sxs-lookup"><span data-stu-id="2eecf-150">To avoid performance issues when you create calculated columns, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="2eecf-151">分多個步驟建立公式並將結果儲存到資料行，讓您能夠驗證結果及評估效能，而不要建立包含許多複雜相依性的單一公式。</span><span class="sxs-lookup"><span data-stu-id="2eecf-151">Rather than create a single formula that contains many complex dependencies, create the formulas in steps, with results saved to columns, so that you can validate the results and assess performance.</span></span>  
  
-   <span data-ttu-id="2eecf-152">修改資料通常需要重新計算導出資料行。</span><span class="sxs-lookup"><span data-stu-id="2eecf-152">Modification of data will often require that calculated columns be recalculated.</span></span> <span data-ttu-id="2eecf-153">您可以將重新計算模式設定為手動來防止重新計算；不過，如果導出資料行中有任何不正確的值，則該資料行將呈灰色，直到您重新整理與重新計算資料為止。</span><span class="sxs-lookup"><span data-stu-id="2eecf-153">You can prevent this by setting the recalculation mode to manual; however, if any values in the calculated column are incorrect the column will be grayed out until you refresh and recalculate the data.</span></span>  
  
-   <span data-ttu-id="2eecf-154">如果您變更或刪除資料表之間的關聯性，使用這些資料表中之資料行的公式將會變成無效。</span><span class="sxs-lookup"><span data-stu-id="2eecf-154">If you change or delete relationships between tables, formulas that use columns in those tables will become invalid.</span></span>  
  
-   <span data-ttu-id="2eecf-155">如果您建立包含循環相依性或自我參考相依性的公式，將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2eecf-155">If you create a formula that contains a circular or self-referencing dependency, an error will occur.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_rel_tasks"></a> <span data-ttu-id="2eecf-156">相關工作</span><span class="sxs-lookup"><span data-stu-id="2eecf-156">Related Tasks</span></span>  
  
|<span data-ttu-id="2eecf-157">主題</span><span class="sxs-lookup"><span data-stu-id="2eecf-157">Topic</span></span>|<span data-ttu-id="2eecf-158">描述</span><span class="sxs-lookup"><span data-stu-id="2eecf-158">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2eecf-159">建立導出資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="2eecf-159">Create a Calculated Column &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns-create-a-calculated-column.md)|<span data-ttu-id="2eecf-160">此主題中的工作描述如何將新導出資料行加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="2eecf-160">Tasks in this topic describe how to add a new calculated column to a table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2eecf-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2eecf-161">See Also</span></span>  
 <span data-ttu-id="2eecf-162">[&#40;SSAS 表格式&#41;的資料表和資料行](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="2eecf-162">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="2eecf-163">[&#40;SSAS 表格式&#41;的量值](measures-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="2eecf-163">[Measures &#40;SSAS Tabular&#41;](measures-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="2eecf-164">計算 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="2eecf-164">Calculations &#40;SSAS Tabular&#41;</span></span>](calculations-ssas-tabular.md)  
  
  
