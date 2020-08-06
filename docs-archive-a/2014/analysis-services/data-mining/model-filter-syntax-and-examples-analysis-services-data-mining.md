---
title: 模型篩選語法和範例 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filter syntax [data mining]
- filters [data mining]
- filters [Analysis Services]
ms.assetid: c729d9b3-8fda-405e-9497-52b2d7493eae
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7ca200d179c0fe81b948793a4b4478f71502657
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687373"
---
# <a name="model-filter-syntax-and-examples-analysis-services---data-mining"></a><span data-ttu-id="850b6-102">模型篩選語法和範例 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="850b6-102">Model Filter Syntax and Examples (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="850b6-103">本節提供了有關模型篩選語法的詳細資訊，以及範例運算式。</span><span class="sxs-lookup"><span data-stu-id="850b6-103">This section provides detailed information about the syntax for model filters, together with sample expressions.</span></span>  
  
 
  
##  <a name="filter-syntax"></a><a name="bkmk_Syntax"></a> <span data-ttu-id="850b6-104">Filter Syntax</span><span class="sxs-lookup"><span data-stu-id="850b6-104">Filter Syntax</span></span>  
 <span data-ttu-id="850b6-105">篩選運算式通常相當於 WHERE 子句的內容。</span><span class="sxs-lookup"><span data-stu-id="850b6-105">Filter expressions generally are equivalent to the content of a WHERE clause.</span></span> <span data-ttu-id="850b6-106">您可以使用邏輯運算子 `AND`、`OR` 和 `NOT` 來連接多項條件。</span><span class="sxs-lookup"><span data-stu-id="850b6-106">You can connect multiple conditions by using the logical operators `AND`, `OR`, and `NOT`.</span></span>  
  
 <span data-ttu-id="850b6-107">在巢狀資料表中，您也可以使用 `EXISTS` 和 `NOT EXISTS` 運算子。</span><span class="sxs-lookup"><span data-stu-id="850b6-107">In nested tables, you can also use the `EXISTS` and `NOT EXISTS` operators.</span></span> <span data-ttu-id="850b6-108">如果子查詢至少傳回一個資料列，`EXISTS` 條件就會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="850b6-108">An `EXISTS` condition evaluates to `true` if the subquery returns at least one row.</span></span> <span data-ttu-id="850b6-109">在您想要將模型限制為包含巢狀資料表中特定值的案例中，這會很有用：例如，至少購買過一次某個項目的客戶。</span><span class="sxs-lookup"><span data-stu-id="850b6-109">This is useful in cases where you want to restrict the model to cases that contain a particular value in the nested table: for example, customers who have purchased an item at least once.</span></span>  
  
 <span data-ttu-id="850b6-110">如果子查詢中指定的條件不存在，`NOT EXISTS` 條件就會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="850b6-110">A `NOT EXISTS` condition evaluates to `true` if the condition specified in the subquery does not exist.</span></span> <span data-ttu-id="850b6-111">例如，當您想要將模型限制為從未購買過特定項目的客戶時。</span><span class="sxs-lookup"><span data-stu-id="850b6-111">An example is when you want to restrict the model to customers who have never purchased a particular item.</span></span>  
  
 <span data-ttu-id="850b6-112">一般語法如下：</span><span class="sxs-lookup"><span data-stu-id="850b6-112">The general syntax is as follows:</span></span>  
  
```  
<filter>::=<predicate list>  | ( <predicate list> )  
<predicate list>::= <predicate> | [<logical_operator> <predicate list>]   
<logical_operator::= AND| OR  
<predicate>::= NOT <predicate>|( <predicate> ) <avPredicate> | <nestedTablePredicate> | ( <predicate> )   
<avPredicate>::= <columnName> <operator> <scalar> | <columnName> IS [NOT] NULL  
<operator>::= = | != | <> | > | >= | < | <=  
<nestedTablePredicate>::= EXISTS (<subquery>)  
<subquery>::=SELECT * FROM <columnName>[ WHERE  <predicate list> ]  
```  
  
 <span data-ttu-id="850b6-113">*出*</span><span class="sxs-lookup"><span data-stu-id="850b6-113">*filter*</span></span>  
 <span data-ttu-id="850b6-114">包含一個或多個由邏輯運算子連接的述詞。</span><span class="sxs-lookup"><span data-stu-id="850b6-114">Contains one or more predicates, connected by logical operators.</span></span>  
  
 <span data-ttu-id="850b6-115">*predicate list*</span><span class="sxs-lookup"><span data-stu-id="850b6-115">*predicate list*</span></span>  
 <span data-ttu-id="850b6-116">一個或多個由邏輯運算子分隔的有效篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="850b6-116">One or more valid filter expressions, separated by logical operators.</span></span>  
  
 <span data-ttu-id="850b6-117">*columnName*</span><span class="sxs-lookup"><span data-stu-id="850b6-117">*columnName*</span></span>  
 <span data-ttu-id="850b6-118">採礦結構資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="850b6-118">The name of a mining structure column.</span></span>  
  
 <span data-ttu-id="850b6-119">logical operator</span><span class="sxs-lookup"><span data-stu-id="850b6-119">logical operator</span></span>  
 <span data-ttu-id="850b6-120">`AND`, `OR`, `NOT`</span><span class="sxs-lookup"><span data-stu-id="850b6-120">`AND`, `OR`, `NOT`</span></span>  
  
 <span data-ttu-id="850b6-121">*avPredicate*</span><span class="sxs-lookup"><span data-stu-id="850b6-121">*avPredicate*</span></span>  
 <span data-ttu-id="850b6-122">只能套用至純量採礦結構資料行的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="850b6-122">Filter expression that can be applied to scalar mining structure column only.</span></span> <span data-ttu-id="850b6-123">*avPredicate* 運算式可用於模型篩選或巢狀資料表篩選中。</span><span class="sxs-lookup"><span data-stu-id="850b6-123">An *avPredicate* expression can be used in both model filters or nested table filters.</span></span>  
  
 <span data-ttu-id="850b6-124">使用下列任何運算子的運算式只能套用至連續資料行。</span><span class="sxs-lookup"><span data-stu-id="850b6-124">An expression that uses any of the following operators can only be applied to a continuous column.</span></span> <span data-ttu-id="850b6-125">:</span><span class="sxs-lookup"><span data-stu-id="850b6-125">:</span></span>  
  
-   <span data-ttu-id="850b6-126">**\<** (小於) </span><span class="sxs-lookup"><span data-stu-id="850b6-126">**\<** (less than)</span></span>  
  
-   <span data-ttu-id="850b6-127">**>** (大於) </span><span class="sxs-lookup"><span data-stu-id="850b6-127">**>** (greater than)</span></span>  
  
-   <span data-ttu-id="850b6-128">**>=** (大於或等於) </span><span class="sxs-lookup"><span data-stu-id="850b6-128">**>=** (greater than or equal to)</span></span>  
  
-   <span data-ttu-id="850b6-129">**\<=** (小於或等於) </span><span class="sxs-lookup"><span data-stu-id="850b6-129">**\<=** (less than or equal to)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="850b6-130">不論資料類型為何，這些運算子都無法套用至 `Discrete`、`Discretized` 或 `Key` 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="850b6-130">Regardless of the data type, these operators cannot be applied to a column that has the type `Discrete`, `Discretized`, or `Key`.</span></span>  
  
 <span data-ttu-id="850b6-131">使用下列任何運算子的運算式可以套用至連續、離散、離散化或索引鍵資料行：</span><span class="sxs-lookup"><span data-stu-id="850b6-131">An expression that uses any of the following operators can be applied to a continuous, discrete, discretized, or key column:</span></span>  
  
-   <span data-ttu-id="850b6-132">**=** (等於) </span><span class="sxs-lookup"><span data-stu-id="850b6-132">**=** (equals)</span></span>  
  
-   <span data-ttu-id="850b6-133">**！ =** (不等於) </span><span class="sxs-lookup"><span data-stu-id="850b6-133">**!=** (not equal to)</span></span>  
  
-   <span data-ttu-id="850b6-134">**是 NULL**</span><span class="sxs-lookup"><span data-stu-id="850b6-134">**IS NULL**</span></span>  
  
 <span data-ttu-id="850b6-135">如果 *avPredicate*套用至離散化資料行，篩選中所用的值就可以是特定值區中的任何值。</span><span class="sxs-lookup"><span data-stu-id="850b6-135">If the argument, *avPredicate*, applies to a discretized column, the value used in the filter can be any value in a specific bucket.</span></span>  
  
 <span data-ttu-id="850b6-136">換言之，雖然您沒有將條件定義為 `AgeDisc = '25-35'`，但是系統仍會計算並使用該間隔中的值。</span><span class="sxs-lookup"><span data-stu-id="850b6-136">In other words, you do not define the condition as `AgeDisc = '25-35'`, but instead compute and then use a value from that interval.</span></span>  
  
 <span data-ttu-id="850b6-137">例如：  `AgeDisc = 27`  表示與 27 位於相同間隔中的任何值，在此情況中就是 25-35。</span><span class="sxs-lookup"><span data-stu-id="850b6-137">Example:  `AgeDisc = 27`  means any value in the same interval as 27, which in this case is 25-35.</span></span>  
  
 <span data-ttu-id="850b6-138">*nestedTablePredicate*</span><span class="sxs-lookup"><span data-stu-id="850b6-138">*nestedTablePredicate*</span></span>  
 <span data-ttu-id="850b6-139">套用至巢狀資料表的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="850b6-139">Filter expression that applies to a nested table.</span></span> <span data-ttu-id="850b6-140">它只能用於模型篩選中。</span><span class="sxs-lookup"><span data-stu-id="850b6-140">Can be used in model filters only.</span></span>  
  
 <span data-ttu-id="850b6-141">*nestedTablePredicate*的子查詢引數只能套用至資料表採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="850b6-141">The sub-query argument of the argument, *nestedTablePredicate*, can only apply to a table mining structure column</span></span>  
  
 <span data-ttu-id="850b6-142">子查詢</span><span class="sxs-lookup"><span data-stu-id="850b6-142">subquery</span></span>  
 <span data-ttu-id="850b6-143">SELECT 陳述式，後面接著一個有效的述詞或述詞清單。</span><span class="sxs-lookup"><span data-stu-id="850b6-143">A SELECT statement followed by a valid predicate or list of predicates.</span></span>  
  
 <span data-ttu-id="850b6-144">所有述詞都必須屬於 *avPredicates*中所描述的類型。</span><span class="sxs-lookup"><span data-stu-id="850b6-144">All the predicates must be of the type described in *avPredicates*.</span></span> <span data-ttu-id="850b6-145">此外，這些述詞只能參考目前巢狀資料表中由 *columnName*引數所識別的資料行。</span><span class="sxs-lookup"><span data-stu-id="850b6-145">Furthermore, the predicates can refer only to columns that are included in the current nested table, identified by the argument, *columnName*.</span></span>  
  
### <a name="limitations-on-filter-syntax"></a><span data-ttu-id="850b6-146">篩選語法的限制</span><span class="sxs-lookup"><span data-stu-id="850b6-146">Limitations on Filter Syntax</span></span>  
 <span data-ttu-id="850b6-147">下列限制會套用至篩選：</span><span class="sxs-lookup"><span data-stu-id="850b6-147">The following restrictions apply to filters:</span></span>  
  
-   <span data-ttu-id="850b6-148">篩選只能包含簡易述詞。</span><span class="sxs-lookup"><span data-stu-id="850b6-148">A filter can contain only simple predicates.</span></span> <span data-ttu-id="850b6-149">這些述詞包括數學運算子、純量和資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="850b6-149">These include mathematical operators, scalars, and column names.</span></span>  
  
-   <span data-ttu-id="850b6-150">篩選語法不支援使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="850b6-150">User-defined functions are not supported in the filter syntax.</span></span>  
  
-   <span data-ttu-id="850b6-151">篩選語法不支援非布林運算子，例如加號或減號。</span><span class="sxs-lookup"><span data-stu-id="850b6-151">Non-Boolean operators, such as the plus or minus signs, are not supported in the filter syntax.</span></span>  
  
## <a name="examples-of-filters"></a><span data-ttu-id="850b6-152">篩選的範例</span><span class="sxs-lookup"><span data-stu-id="850b6-152">Examples of Filters</span></span>  
 <span data-ttu-id="850b6-153">下列範例將示範套用至採礦模型之篩選的使用方式。</span><span class="sxs-lookup"><span data-stu-id="850b6-153">The following examples demonstrate the use of filters applied to a mining model.</span></span> <span data-ttu-id="850b6-154">如果您使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 來建立篩選運算式，在 [篩選] 對話方塊的 [屬性]\*\*\*\* 視窗和 [運算式]\*\*\*\* 窗格中，您只會看見顯示在 WITH FILTER 關鍵字之後的字串。</span><span class="sxs-lookup"><span data-stu-id="850b6-154">If you create the filter expression by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Property** window and the **Expression** pane of the filter dialog box, you would see only the string that appears after the WITH FILTER keywords.</span></span> <span data-ttu-id="850b6-155">在該處加入採礦結構定義的目的是為了讓人更容易了解資料行類型和使用方式。</span><span class="sxs-lookup"><span data-stu-id="850b6-155">Here, the definition of the mining structure is included to make it easier to understand the column type and usage.</span></span>  
  
###  <a name="example-1-typical-case-level-filtering"></a><a name="bkmk_Ex1"></a> <span data-ttu-id="850b6-156">範例 1：一般案例層級的篩選</span><span class="sxs-lookup"><span data-stu-id="850b6-156">Example 1: Typical Case-Level Filtering</span></span>  
 <span data-ttu-id="850b6-157">這則範例會顯示一個簡易篩選，它可將模型中使用的案例限制為職業是建築師而且年齡超過 30 歲的客戶。</span><span class="sxs-lookup"><span data-stu-id="850b6-157">This example shows a simple filter that restricts the cases used in the model to customers whose occupation is architect and whose age is over 30.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_1  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH FILTER (Age > 30 AND Occupation='Architect')  
```  
  

  
###  <a name="example-2-case-level-filtering-using-nested-table-attributes"></a><a name="bkmk_Ex2"></a> <span data-ttu-id="850b6-158">範例 2：使用巢狀資料表屬性的案例層級篩選</span><span class="sxs-lookup"><span data-stu-id="850b6-158">Example 2: Case-Level Filtering using Nested Table Attributes</span></span>  
 <span data-ttu-id="850b6-159">如果您的採礦結構包含巢狀資料表，就可以篩選巢狀資料表中是否存某個值，或篩選包含特定值的巢狀資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="850b6-159">If your mining structure contains nested tables, you can either filter on the existence of a value in a nested table, or filter on nested table rows that contain a specific value.</span></span> <span data-ttu-id="850b6-160">這則範例會將模型所使用的案例限制為年齡超過 30 歲而且至少有一次購買包含牛奶的客戶。</span><span class="sxs-lookup"><span data-stu-id="850b6-160">This example restricts the cases used for the model to customers over the age of 30 who made at least one purchase that included milk.</span></span>  
  
 <span data-ttu-id="850b6-161">如此範例所示，篩選僅使用模型中包含的資料行並非必要條件。</span><span class="sxs-lookup"><span data-stu-id="850b6-161">As this example shows, it is not necessary that the filter use only columns that are included in the model.</span></span> <span data-ttu-id="850b6-162">巢狀資料表 **Products** 屬於採礦結構的一部分，但是不包含在採礦模型中。</span><span class="sxs-lookup"><span data-stu-id="850b6-162">The nested table **Products** is part of the mining structure, but is not included in the mining model.</span></span> <span data-ttu-id="850b6-163">不過，您仍然可以篩選巢狀資料表中的值和屬性。</span><span class="sxs-lookup"><span data-stu-id="850b6-163">However, you can still filter on values and attributes in the nested table.</span></span> <span data-ttu-id="850b6-164">若要檢視這些案例的詳細資料，您必須啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="850b6-164">To view the details of these cases, drillthrough must be enabled.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_2  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT  
)  
WITH DRILLTHROUGH,   
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk')  
)  
```  
  
 
  
###  <a name="example-3-case-level-filtering-on-multiple-nested-table-attributes"></a><a name="bkmk_Ex3"></a> <span data-ttu-id="850b6-165">範例 3：多個巢狀資料表屬性的案例層級篩選</span><span class="sxs-lookup"><span data-stu-id="850b6-165">Example 3: Case-Level Filtering on Multiple Nested Table Attributes</span></span>  
 <span data-ttu-id="850b6-166">此範例顯示三個部分的篩選：第一個條件會套用至案例資料表、第二個條件會套用至巢狀資料表中的屬性，而第三個條件會套用至其中一個巢狀資料表資料行中的特定值。</span><span class="sxs-lookup"><span data-stu-id="850b6-166">This example shows a three-part filter: a condition applies to the case table, another condition to an attribute in the nested table, and another condition on a specific value in one of the nested table columns.</span></span>  
  
 <span data-ttu-id="850b6-167">篩選中的第一個條件 `Age > 30`會套用至案例資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="850b6-167">The first condition in the filter, `Age > 30`, applies to a column in the case table.</span></span> <span data-ttu-id="850b6-168">其餘條件則會套用至巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="850b6-168">The remaining conditions apply to the nested table.</span></span>  
  
 <span data-ttu-id="850b6-169">第二個條件 `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`會檢查巢狀資料表中是否至少有一次購買包含牛奶。</span><span class="sxs-lookup"><span data-stu-id="850b6-169">The second condition, `EXISTS (SELECT * FROM Products WHERE ProductName='Milk'`, checks for the presence of at least one purchase in the nested table that included milk.</span></span> <span data-ttu-id="850b6-170">第三個條件 `Quantity>=2`表示客戶必須在單一交易中，至少購買過兩個單位的牛奶。</span><span class="sxs-lookup"><span data-stu-id="850b6-170">The third condition, `Quantity>=2`, means that the customer must have purchased at least two units of milk in a single transaction.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_3  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
)  
)  
FILTER (Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity >= 2)   
)  
```  
  

  
###  <a name="example-4-case-level-filtering-on-absence-of-nested-table-attributes"></a><a name="bkmk_Ex4"></a> <span data-ttu-id="850b6-171">範例 4：巢狀資料表屬性不存在的案例層級篩選</span><span class="sxs-lookup"><span data-stu-id="850b6-171">Example 4: Case-Level Filtering On Absence of Nested Table Attributes</span></span>  
 <span data-ttu-id="850b6-172">這則範例會顯示如何透過篩選巢狀資料表中不存在的屬性，將案例限制為沒有購買特定項目的客戶。</span><span class="sxs-lookup"><span data-stu-id="850b6-172">This example shows how to limit cases to customer who did not purchase a specific item, by filtering on the absence of an attribute in the nested table.</span></span> <span data-ttu-id="850b6-173">在此範例中，模型是使用年齡超過 30 歲而且從未購買過牛奶的客戶進行培訓。</span><span class="sxs-lookup"><span data-stu-id="850b6-173">In this example, the model is trained using customers over the age of 30 who have never bought milk.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_4  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName  
)  
)  
FILTER (Age > 30 AND NOT EXISTS (SELECT * FROM Products WHERE ProductName='Milk') )  
```  
  

  
###  <a name="example-5-filtering-on-multiple-nested-table-values"></a><a name="bkmk_Ex5"></a> <span data-ttu-id="850b6-174">範例 5：多個巢狀資料表值的篩選</span><span class="sxs-lookup"><span data-stu-id="850b6-174">Example 5: Filtering on Multiple Nested Table Values</span></span>  
 <span data-ttu-id="850b6-175">此範例的目的是要顯示巢狀資料表篩選。</span><span class="sxs-lookup"><span data-stu-id="850b6-175">The purpose of the example is to show nested table filtering.</span></span> <span data-ttu-id="850b6-176">巢狀資料表篩選是在案例篩選之後套用的，而且只會限制巢狀資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="850b6-176">The nested table filter is applied after the case filter, and only restricts nested table rows.</span></span>  
  
 <span data-ttu-id="850b6-177">這個模型可能會包含多個具有空白巢狀資料表的案例，因為沒有指定 EXISTS。</span><span class="sxs-lookup"><span data-stu-id="850b6-177">This model could contain multiple cases with empty nested tables because EXISTS is not specified.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_5  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
WITH DRILLTHROUGH  
```  
  

  
###  <a name="example-6-filtering-on-nested-table-attributes-and-exists"></a><a name="bkmk_Ex6"></a> <span data-ttu-id="850b6-178">範例 6：巢狀資料表屬性的篩選和 EXISTS</span><span class="sxs-lookup"><span data-stu-id="850b6-178">Example 6: Filtering on Nested Table Attributes and EXISTS</span></span>  
 <span data-ttu-id="850b6-179">在此範例中，巢狀資料表的篩選會將資料列限制為包含牛奶或瓶裝水的資料列。</span><span class="sxs-lookup"><span data-stu-id="850b6-179">In this example, the filter on the nested table restricts the rows to those that contain either milk or bottled water.</span></span> <span data-ttu-id="850b6-180">然後，系統會使用 `EXISTS` 陳述式來限制模型中的案例。</span><span class="sxs-lookup"><span data-stu-id="850b6-180">Then, the cases in the model are restricted by using an `EXISTS` statement.</span></span> <span data-ttu-id="850b6-181">這樣做可確保巢狀資料表不是空的。</span><span class="sxs-lookup"><span data-stu-id="850b6-181">This makes sure that the nested table is not empty.</span></span>  
  
```  
ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_6  
(  
CustomerId,  
Age,  
Occupation,  
MaritalStatus PREDICT,  
Products PREDICT  
(  
ProductName KEY,  
Quantity        
) WITH FILTER(ProductName='Milk' OR ProductName='bottled water')  
)  
FILTER (EXISTS (Products))  
```  
  

  
###  <a name="example-7-complex-filter-combinations"></a><a name="bkmk_Ex7"></a> <span data-ttu-id="850b6-182">範例 7：複雜的篩選組合</span><span class="sxs-lookup"><span data-stu-id="850b6-182">Example 7: Complex Filter Combinations</span></span>  
 <span data-ttu-id="850b6-183">這個模型的狀況與範例 4 的狀況很相似，但是更為複雜。</span><span class="sxs-lookup"><span data-stu-id="850b6-183">The scenario for this model resembles that of Example 4, but is far more complex.</span></span> <span data-ttu-id="850b6-184">**ProductsOnSale**的嵌套資料表具有篩選準則， `(OnSale)` 表示**OnSale**的值必須 `true` 針對**ProductName**中列出的產品。</span><span class="sxs-lookup"><span data-stu-id="850b6-184">The nested table, **ProductsOnSale**, has the filter condition `(OnSale)` meaning that the value of **OnSale** must be `true` for the product listed in **ProductName**.</span></span> <span data-ttu-id="850b6-185">其中， **OnSale** 是結構資料行。</span><span class="sxs-lookup"><span data-stu-id="850b6-185">Here, **OnSale** is a structure column.</span></span>  
  
 <span data-ttu-id="850b6-186">篩選的第二個部分（針對**productsnotonsale) **）會重複此語法，但會篩選**OnSale**值為的產品 `not true``(!OnSale)` 。</span><span class="sxs-lookup"><span data-stu-id="850b6-186">The second part of the filter, for **ProductsNotOnSale**, repeats this syntax, but filters on products for which the value of **OnSale** is `not true``(!OnSale)`.</span></span>  
  
 <span data-ttu-id="850b6-187">最後，這些條件會組合並在案例資料表中加入一項額外的限制。</span><span class="sxs-lookup"><span data-stu-id="850b6-187">Finally, the conditions are combined and one additional restriction is added to the case table.</span></span> <span data-ttu-id="850b6-188">其結果是針對年齡超過 25 歲的所有客戶，根據 **ProductsOnSale** 清單中包含的案例來預測 **ProductsOnSale** 清單中的購買產品。</span><span class="sxs-lookup"><span data-stu-id="850b6-188">The result is to predict purchases of products in the **ProductsNotOnSale** list, based on the cases that are included in the **ProductsOnSale** list, for all customers over the age of 25.</span></span>  
  
 `ALTER MINING STRUCTURE MyStructure  ADD MINING MODEL MyModel_7`  
  
 `(`  
  
 `CustomerId,`  
  
 `Age,`  
  
 `Occupation,`  
  
 `MaritalStatus,`  
  
 `ProductsOnSale`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(OnSale),`  
  
 `ProductsNotOnSale PREDICT ONLY`  
  
 `(`  
  
 `ProductName KEY`  
  
 `) WITH FILTER(!OnSale)`  
  
 `)`  
  
 `WITH DRILLTHROUGH,`  
  
 `FILTER (EXISTS (ProductsOnSale) AND EXISTS(ProductsNotOnSale) AND Age > 25)`  
  
  
  
###  <a name="example-8-filtering-on-dates"></a><a name="bkmk_Ex8"></a> <span data-ttu-id="850b6-189">範例 8：日期的篩選</span><span class="sxs-lookup"><span data-stu-id="850b6-189">Example 8: Filtering on Dates</span></span>  
 <span data-ttu-id="850b6-190">您可以篩選日期輸入資料行，就如同任何其他資料一樣。</span><span class="sxs-lookup"><span data-stu-id="850b6-190">You can filter input columns on dates, as you would any other data.</span></span> <span data-ttu-id="850b6-191">日期/時間類型的資料行中包含的日期為連續日期，因此您可以使用如大於 (>) 或小於 (<) 等運算子指定日期範圍。</span><span class="sxs-lookup"><span data-stu-id="850b6-191">Dates contained in a column of type date/time are continuous values; therefore, you can specify a date range by using operators such as greater than (>) or less than (<).</span></span> <span data-ttu-id="850b6-192">如果您的資料來源不是以 Continuous 資料類型而是離散或文字值來表示日期，則無法篩選日期範圍，而必須指定個別的離散值。</span><span class="sxs-lookup"><span data-stu-id="850b6-192">If your data source does not represent dates by a Continuous data type, but as discrete or text values, you cannot filter on a date range, but must specify individual discrete values.</span></span>  
  
 <span data-ttu-id="850b6-193">不過，如果篩選所使用的日期資料行也是時間序列模型的索引鍵資料行，則無法在模型的日期資料行上建立篩選。</span><span class="sxs-lookup"><span data-stu-id="850b6-193">However, you cannot create a filter on the date column in a time series model if the date column used for the filter is also the key column for the model.</span></span> <span data-ttu-id="850b6-194">這是因為時間序列模型和時序群集模型中，日期資料行可能會當做 `KeyTime` 或 `KeySequence` 類型處理。</span><span class="sxs-lookup"><span data-stu-id="850b6-194">That is because, in time series models and sequence clustering models, the date column might be handled as type `KeyTime` or `KeySequence`.</span></span>  
  
 <span data-ttu-id="850b6-195">如果您必須在時間序列模型中篩選連續值，可以在採礦結構中建立資料行的複本，然後在新的資料行上篩選模型。</span><span class="sxs-lookup"><span data-stu-id="850b6-195">If you need to filter on continuous dates in a time series model, you can create a copy of the column in the mining structure, and filter the model on the new column.</span></span>  
  
 <span data-ttu-id="850b6-196">例如，下列運算式代表已加入至預測模型中 `Continuous` 類型之日期資料行的篩選。</span><span class="sxs-lookup"><span data-stu-id="850b6-196">For example, the following expression represents a filter on a date column of type `Continuous` that has been added to the Forecasting model.</span></span>  
  
 `=[DateCopy] > '12:31:2003:00:00:00'`  
  
> [!NOTE]  
>  <span data-ttu-id="850b6-197">請注意，您加入至模型的額外資料行可能會影響結果。</span><span class="sxs-lookup"><span data-stu-id="850b6-197">Note that any extra columns that you add to the model might affect the results.</span></span> <span data-ttu-id="850b6-198">因此，如果您不想要在序列計算中使用資料行，應該只將資料行加入至採礦結構，而不是加入至模型。</span><span class="sxs-lookup"><span data-stu-id="850b6-198">Therefore, if you do not want the column to be used in computation of the series, you should add the column only to the mining structure, and not to the model.</span></span> <span data-ttu-id="850b6-199">您也可以將資料行上的模型旗標設定為 `PredictOnly` 或 `Ignore`。</span><span class="sxs-lookup"><span data-stu-id="850b6-199">You can also set the model flag on the column to `PredictOnly` or to `Ignore`.</span></span> <span data-ttu-id="850b6-200">如需詳細資訊，請參閱[模型旗標 &#40;資料採礦&#41;](modeling-flags-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="850b6-200">For more information, see [Modeling Flags &#40;Data Mining&#41;](modeling-flags-data-mining.md).</span></span>  
  
 <span data-ttu-id="850b6-201">對於其他模型類型，日期可以當做輸入準則或篩選準則，就如同任何其他資料行一樣。</span><span class="sxs-lookup"><span data-stu-id="850b6-201">For other model types, you can use dates as input criteria or filter criteria just like you would in any other column.</span></span> <span data-ttu-id="850b6-202">不過，如果您必須使用 `Continuous` 資料類型不支援的特定資料粒度層級，可以使用運算式擷取要用於篩選和分析的單位，在資料來源中建立衍生值。</span><span class="sxs-lookup"><span data-stu-id="850b6-202">However, if you need to use a specific level of granularity that is not supported by a `Continuous` data type, you can create a derived value in the data source by using expressions to extract the unit to use in filtering and analysis.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="850b6-203">當您指定日期作為篩選準則時，不論目前作業系統的日期格式為何，都必須使用下列格式： `mm/dd/yyyy`。</span><span class="sxs-lookup"><span data-stu-id="850b6-203">When you specify a dates as filter criteria, you must use the following format, regardless of the date format for the current OS: `mm/dd/yyyy`.</span></span> <span data-ttu-id="850b6-204">任何其他格式都會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="850b6-204">Any other format results in an error.</span></span>  
  
 <span data-ttu-id="850b6-205">例如，如果您想要篩選客服中心結果，只顯示週末，可以在資料來源檢視中建立運算式以擷取每個日期的工作天名稱，然後將該工作天名稱值用於輸入或當做篩選的離散值。</span><span class="sxs-lookup"><span data-stu-id="850b6-205">For example, if you want to filter your call center results to show only weekends, you can create an expression in the data source view that extracts the weekday name for each date, and then use that weekday name value for input or as a discrete value in filtering.</span></span> <span data-ttu-id="850b6-206">請記得，重複值會影響模型，因此您應該只使用其中一個資料行，而不是日期資料行加上衍生值。</span><span class="sxs-lookup"><span data-stu-id="850b6-206">Just remember that repeating values can affect the model, so you should use only one of the columns, not the date column plus the derived value.</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="850b6-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="850b6-207">See Also</span></span>  
 <span data-ttu-id="850b6-208">[&#40;Analysis Services 的採礦模型篩選-資料採礦&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="850b6-208">[Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="850b6-209">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="850b6-209">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
