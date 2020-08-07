---
title: 自動存在 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 56283497-624c-45b5-8a0d-036b0e331d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd35958a364456c12d58392afe3754f6adcf97b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597421"
---
# <a name="autoexists"></a><span data-ttu-id="95bd1-102">自動存在</span><span class="sxs-lookup"><span data-stu-id="95bd1-102">Autoexists</span></span>
  <span data-ttu-id="95bd1-103">「自動存在」\*\* 的概念是將 Cube 空間限制為實際存在於 Cube 中的資料格，相對因建立相同階層中的所有屬性階層成員組合而可能存在的資料格。</span><span class="sxs-lookup"><span data-stu-id="95bd1-103">The concept of *autoexists* limits the cube space to those cells that actually exist in the cube in contraposition to those that might exist as a result of creating all possible combinations of attribute hierarchy members from the same hierarchy.</span></span> <span data-ttu-id="95bd1-104">這是因為某個屬性階層的成員不能與相同維度中另一個屬性階層的成員同時存在。</span><span class="sxs-lookup"><span data-stu-id="95bd1-104">This is because members of one attribute hierarchy cannot exist with members of another attribute hierarchy in the same dimension.</span></span> <span data-ttu-id="95bd1-105">在 SELECT 陳述式中使用相同維度的兩個以上屬性階層時，Analysis Services 會評估屬性的運算式來確認這些屬性的成員有受到正確的限制以符合所有其他屬性的準則。</span><span class="sxs-lookup"><span data-stu-id="95bd1-105">When two or more attribute hierarchies of the same dimension are used in a SELECT statement, Analysis Services evaluates the attributes' expressions to make sure that the members of those attributes are properly confined to meet the criteria of all other attributes.</span></span>  
  
 <span data-ttu-id="95bd1-106">例如，假設您正在使用來自 Geography 維度的屬性。</span><span class="sxs-lookup"><span data-stu-id="95bd1-106">For example, suppose you are working with attributes from the Geography dimension.</span></span> <span data-ttu-id="95bd1-107">如果您所擁有的其中一個運算式會從 City 屬性傳回所有成員，而另一個運算式會將 Country 屬性的成員限制為歐洲所有國家 (地區)，這將會使得 City 成員限制為只有屬於歐洲國家 (地區) 的城市。</span><span class="sxs-lookup"><span data-stu-id="95bd1-107">If you have one expression that returns all members from the City attribute and another expression that confines members from the Country attribute to all countries in Europe, then this will result in the City members being confined to only those cities that belong to countries in Europe.</span></span> <span data-ttu-id="95bd1-108">這是因為 Analysis Services 的自動存在特性所致。</span><span class="sxs-lookup"><span data-stu-id="95bd1-108">This is because of the autoexists characteristic of Analysis Services.</span></span> <span data-ttu-id="95bd1-109">「自動存在」僅適用於相同維度的屬性的原因是，它會嘗試防止某個屬性運算式加入其他屬性運算式中排除的維度記錄。</span><span class="sxs-lookup"><span data-stu-id="95bd1-109">Autoexists only applies to attributes from the same dimension because it tries to prevent the dimension records excluded in one attribute expression from being included by the other attribute expressions.</span></span> <span data-ttu-id="95bd1-110">您也可以將「自動存在」視為不同之屬性運算式在維度資料列上所產生的交集。</span><span class="sxs-lookup"><span data-stu-id="95bd1-110">Autoexists can also be understood as the resulting intersection of the different attributes expressions over the dimension rows.</span></span>  
  
## <a name="cell-existence"></a><span data-ttu-id="95bd1-111">資料格存在性</span><span class="sxs-lookup"><span data-stu-id="95bd1-111">Cell Existence</span></span>  
 <span data-ttu-id="95bd1-112">下列資料格永遠存在：</span><span class="sxs-lookup"><span data-stu-id="95bd1-112">The following cells always exist:</span></span>  
  
-   <span data-ttu-id="95bd1-113">與相同維度中其他階層的成員相交時，每個階層的 (全部) 成員。</span><span class="sxs-lookup"><span data-stu-id="95bd1-113">The (All) member, of every hierarchy, when crossed with members of other hierarchies in the same dimension.</span></span>  
  
-   <span data-ttu-id="95bd1-114">與其非導出同層級相交或與其非導出同層級的父系或下階相交時的導出成員。</span><span class="sxs-lookup"><span data-stu-id="95bd1-114">Calculated members when crossed with their non-calculated siblings, or with the parents or descendants of their non-calculated siblings.</span></span>  
  
## <a name="providing-non-existing-cells"></a><span data-ttu-id="95bd1-115">提供不存在的資料格</span><span class="sxs-lookup"><span data-stu-id="95bd1-115">Providing Non-existing cells</span></span>  
 <span data-ttu-id="95bd1-116">不存在的資料格是系統所提供的資料格，以回應要求不存在於 Cube 中之資料格的查詢或計算。</span><span class="sxs-lookup"><span data-stu-id="95bd1-116">A non-existing cell is a cell provided by the system as a response to a query or calculation that requests a cell that does not exist in the cube.</span></span> <span data-ttu-id="95bd1-117">例如，如果 Cube 有屬於 Geography 維度的 City 屬性階層和 Country 屬性階層，以及 Internet Sales Amount 量值，此 Cube 的空間只會包含同時存在的成員。</span><span class="sxs-lookup"><span data-stu-id="95bd1-117">For example, if you have a cube that has a City attribute hierarchy and a Country attribute hierarchy that belong to the Geography dimension, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="95bd1-118">例如，如果 City 屬性階層包含紐約、倫敦、巴黎、東京及墨爾本等城市，並且 Country 屬性階層包含美國、英國、法國、日本及澳洲等國家 (地區)，則 Cube 的空間不會包含巴黎和美國交集的空間 (資料格)。</span><span class="sxs-lookup"><span data-stu-id="95bd1-118">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="95bd1-119">當查詢不存在的資料格時，不存在的資料格會傳回 Null，也就是說，它們不包含計算，而且您無法定義寫入此空間的計算。</span><span class="sxs-lookup"><span data-stu-id="95bd1-119">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="95bd1-120">例如，下列陳述式包括了不存在的資料格。</span><span class="sxs-lookup"><span data-stu-id="95bd1-120">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="95bd1-121">這個查詢使用 [Members (Set) (MDX)](/sql/mdx/members-set-mdx) 函數來傳回資料行軸上 Gender 屬性階層的成員集合，並且將該集合與資料列軸上 Customer 屬性階層的指定成員集合相交。</span><span class="sxs-lookup"><span data-stu-id="95bd1-121">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="95bd1-122">當您執行上述查詢時，Aaron A. Allen 和 Female 交集處的資料格會顯示 Null。</span><span class="sxs-lookup"><span data-stu-id="95bd1-122">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="95bd1-123">同樣地，Abigail Clark 和 Male 交集處的資料格也會顯示 Null。</span><span class="sxs-lookup"><span data-stu-id="95bd1-123">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="95bd1-124">這些資料格不存在，也不包含值，但在查詢傳回的結果中會出現不存在的資料格。</span><span class="sxs-lookup"><span data-stu-id="95bd1-124">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="95bd1-125">當您使用 [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) 函數傳回相同維度中多個屬性階層之成員的交叉乘積時，自動存在功能會將所傳回的 Tuple 限制於實際存在的 Tuple 集合，而不會傳回整個笛卡兒乘積。</span><span class="sxs-lookup"><span data-stu-id="95bd1-125">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="95bd1-126">例如，執行下列查詢，然後檢查執行的結果。</span><span class="sxs-lookup"><span data-stu-id="95bd1-126">For example, run and then examine the results from the execution of the following query.</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[State-Province].Members  
  ) ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="95bd1-127">請注意，0 是用來指定資料行軸，為 axis(0) (即資料行軸) 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="95bd1-127">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="95bd1-128">上述查詢只會針對查詢中每個屬性階層之同時存在的成員傳回資料格。</span><span class="sxs-lookup"><span data-stu-id="95bd1-128">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="95bd1-129">先前的查詢也可以使用[交叉聯結 (MDX) ](/sql/mdx/crossjoin-mdx)函數的新 \* 變體來撰寫。</span><span class="sxs-lookup"><span data-stu-id="95bd1-129">The previous query can also be written using the new \* variant of the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="95bd1-130">上述查詢也可以撰寫成下列方式：</span><span class="sxs-lookup"><span data-stu-id="95bd1-130">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="95bd1-131">所傳回的資料格值將會相同，不過結果集中的中繼資料將會不同。</span><span class="sxs-lookup"><span data-stu-id="95bd1-131">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="95bd1-132">例如，在上述查詢中，Country 階層已移至 slicer 座標軸 (在 WHERE 子句中)，因此不會明確出現在結果集中。</span><span class="sxs-lookup"><span data-stu-id="95bd1-132">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="95bd1-133">這三個先前的查詢都會示範中自動存在行為的作用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="95bd1-133">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="deep-and-shallow-autoexists"></a><span data-ttu-id="95bd1-134">深層和淺層自動存在</span><span class="sxs-lookup"><span data-stu-id="95bd1-134">Deep and Shallow Autoexists</span></span>  
 <span data-ttu-id="95bd1-135">自動存在以「深層」或「淺層」方式套用至運算式。</span><span class="sxs-lookup"><span data-stu-id="95bd1-135">Autoexists can be applied to the expressions as Deep or Shallow.</span></span> <span data-ttu-id="95bd1-136">「深層自動存在」(`Deep Autoexists`) 表示在套用 slicer 運算式、軸中的子 SELECT 運算式等之後，會評估所有運算式以符合最深層的可能空間。</span><span class="sxs-lookup"><span data-stu-id="95bd1-136">`Deep Autoexists` means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span> <span data-ttu-id="95bd1-137">「淺層自動存在」(`Shallow Autoexists`) 表示在目前運算式之前評估外部運算式，並將這些結果傳遞至目前運算式。</span><span class="sxs-lookup"><span data-stu-id="95bd1-137">`Shallow Autoexists` means that external expressions are evaluated before the current expression and those results are passed to the current expression.</span></span> <span data-ttu-id="95bd1-138">預設值是深層自動存在。</span><span class="sxs-lookup"><span data-stu-id="95bd1-138">The default setting is deep autoexists.</span></span>  
  
 <span data-ttu-id="95bd1-139">下列案例和範例有助於說明不同類型的自動存在。</span><span class="sxs-lookup"><span data-stu-id="95bd1-139">The following scenario and samples will help to illustrate the different types of Autoexistss.</span></span> <span data-ttu-id="95bd1-140">在下列範例中會建立兩個集合：一個當做計算運算式，而另一個當做常數運算式。</span><span class="sxs-lookup"><span data-stu-id="95bd1-140">In the following examples two sets will be created: one as a calculated expression and the other as a constant expression.</span></span>  
  
 `//Obtain the Top 10 best reseller selling products by Name`  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="95bd1-141">取得的結果集為：</span><span class="sxs-lookup"><span data-stu-id="95bd1-141">The obtained result set is:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="95bd1-142">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-142">**Reseller Sales Amount**</span></span>|<span data-ttu-id="95bd1-143">**折扣量**</span><span class="sxs-lookup"><span data-stu-id="95bd1-143">**Discount Amount**</span></span>|<span data-ttu-id="95bd1-144">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-144">**PCT Discount**</span></span>|  
|<span data-ttu-id="95bd1-145">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="95bd1-145">**Mountain-200**</span></span>|<span data-ttu-id="95bd1-146">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="95bd1-146">**$14,356,699.36**</span></span>|<span data-ttu-id="95bd1-147">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="95bd1-147">**$19,012.71**</span></span>|<span data-ttu-id="95bd1-148">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-148">**0.13%**</span></span>|  
|<span data-ttu-id="95bd1-149">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="95bd1-149">**Road-250**</span></span>|<span data-ttu-id="95bd1-150">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="95bd1-150">**$9,377,457.68**</span></span>|<span data-ttu-id="95bd1-151">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="95bd1-151">**$4,032.47**</span></span>|<span data-ttu-id="95bd1-152">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-152">**0.04%**</span></span>|  
|<span data-ttu-id="95bd1-153">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="95bd1-153">**Mountain-100**</span></span>|<span data-ttu-id="95bd1-154">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-154">**$8,568,958.27**</span></span>|<span data-ttu-id="95bd1-155">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-155">**$139,393.27**</span></span>|<span data-ttu-id="95bd1-156">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-156">**1.63%**</span></span>|  
|<span data-ttu-id="95bd1-157">**Road-650**</span><span class="sxs-lookup"><span data-stu-id="95bd1-157">**Road-650**</span></span>|<span data-ttu-id="95bd1-158">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="95bd1-158">**$7,442,141.81**</span></span>|<span data-ttu-id="95bd1-159">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="95bd1-159">**$39,698.30**</span></span>|<span data-ttu-id="95bd1-160">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-160">**0.53%**</span></span>|  
|<span data-ttu-id="95bd1-161">**Touring-1000**</span><span class="sxs-lookup"><span data-stu-id="95bd1-161">**Touring-1000**</span></span>|<span data-ttu-id="95bd1-162">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="95bd1-162">**$6,723,794.29**</span></span>|<span data-ttu-id="95bd1-163">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="95bd1-163">**$166,144.17**</span></span>|<span data-ttu-id="95bd1-164">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-164">**2.47%**</span></span>|  
|<span data-ttu-id="95bd1-165">**Road-550-W**</span><span class="sxs-lookup"><span data-stu-id="95bd1-165">**Road-550-W**</span></span>|<span data-ttu-id="95bd1-166">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="95bd1-166">**$3,668,383.88**</span></span>|<span data-ttu-id="95bd1-167">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="95bd1-167">**$1,901.97**</span></span>|<span data-ttu-id="95bd1-168">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-168">**0.05%**</span></span>|  
|<span data-ttu-id="95bd1-169">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="95bd1-169">**Road-350-W**</span></span>|<span data-ttu-id="95bd1-170">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="95bd1-170">**$3,665,932.31**</span></span>|<span data-ttu-id="95bd1-171">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="95bd1-171">**$20,946.50**</span></span>|<span data-ttu-id="95bd1-172">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-172">**0.57%**</span></span>|  
|<span data-ttu-id="95bd1-173">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="95bd1-173">**HL Mountain Frame**</span></span>|<span data-ttu-id="95bd1-174">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-174">**$3,365,069.27**</span></span>|<span data-ttu-id="95bd1-175">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="95bd1-175">**$174.11**</span></span>|<span data-ttu-id="95bd1-176">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-176">**0.01%**</span></span>|  
|<span data-ttu-id="95bd1-177">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="95bd1-177">**Road-150**</span></span>|<span data-ttu-id="95bd1-178">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="95bd1-178">**$2,363,805.16**</span></span>|<span data-ttu-id="95bd1-179">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="95bd1-179">**$0.00**</span></span>|<span data-ttu-id="95bd1-180">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-180">**0.00%**</span></span>|  
|<span data-ttu-id="95bd1-181">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="95bd1-181">**Touring-3000**</span></span>|<span data-ttu-id="95bd1-182">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="95bd1-182">**$2,046,508.26**</span></span>|<span data-ttu-id="95bd1-183">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="95bd1-183">**$79,582.15**</span></span>|<span data-ttu-id="95bd1-184">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-184">**3.89%**</span></span>|  
  
 <span data-ttu-id="95bd1-185">取得的產品集似乎與 Preferred10Products 相同，因此，確認 Preferred10Products 集合：</span><span class="sxs-lookup"><span data-stu-id="95bd1-185">The obtained set of products seems to be the same as Preferred10Products; so, verifying the Preferred10Products set:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 <span data-ttu-id="95bd1-186">根據以下結果，兩個集合 (Top10SellingProducts、Preferred10Products) 相同</span><span class="sxs-lookup"><span data-stu-id="95bd1-186">As per the following results, both sets (Top10SellingProducts, Preferred10Products) are the same</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="95bd1-187">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-187">**Reseller Sales Amount**</span></span>|<span data-ttu-id="95bd1-188">**折扣量**</span><span class="sxs-lookup"><span data-stu-id="95bd1-188">**Discount Amount**</span></span>|<span data-ttu-id="95bd1-189">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-189">**PCT Discount**</span></span>|  
|<span data-ttu-id="95bd1-190">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="95bd1-190">**Mountain-200**</span></span>|<span data-ttu-id="95bd1-191">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="95bd1-191">**$14,356,699.36**</span></span>|<span data-ttu-id="95bd1-192">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="95bd1-192">**$19,012.71**</span></span>|<span data-ttu-id="95bd1-193">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-193">**0.13%**</span></span>|  
|<span data-ttu-id="95bd1-194">**Road-250**</span><span class="sxs-lookup"><span data-stu-id="95bd1-194">**Road-250**</span></span>|<span data-ttu-id="95bd1-195">**$9,377,457.68**</span><span class="sxs-lookup"><span data-stu-id="95bd1-195">**$9,377,457.68**</span></span>|<span data-ttu-id="95bd1-196">**$4,032.47**</span><span class="sxs-lookup"><span data-stu-id="95bd1-196">**$4,032.47**</span></span>|<span data-ttu-id="95bd1-197">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-197">**0.04%**</span></span>|  
|<span data-ttu-id="95bd1-198">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="95bd1-198">**Mountain-100**</span></span>|<span data-ttu-id="95bd1-199">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-199">**$8,568,958.27**</span></span>|<span data-ttu-id="95bd1-200">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-200">**$139,393.27**</span></span>|<span data-ttu-id="95bd1-201">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-201">**1.63%**</span></span>|  
|<span data-ttu-id="95bd1-202">**Road-650**</span><span class="sxs-lookup"><span data-stu-id="95bd1-202">**Road-650**</span></span>|<span data-ttu-id="95bd1-203">**$7,442,141.81**</span><span class="sxs-lookup"><span data-stu-id="95bd1-203">**$7,442,141.81**</span></span>|<span data-ttu-id="95bd1-204">**$39,698.30**</span><span class="sxs-lookup"><span data-stu-id="95bd1-204">**$39,698.30**</span></span>|<span data-ttu-id="95bd1-205">**0.53%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-205">**0.53%**</span></span>|  
|<span data-ttu-id="95bd1-206">**Touring-1000**</span><span class="sxs-lookup"><span data-stu-id="95bd1-206">**Touring-1000**</span></span>|<span data-ttu-id="95bd1-207">**$6,723,794.29**</span><span class="sxs-lookup"><span data-stu-id="95bd1-207">**$6,723,794.29**</span></span>|<span data-ttu-id="95bd1-208">**$166,144.17**</span><span class="sxs-lookup"><span data-stu-id="95bd1-208">**$166,144.17**</span></span>|<span data-ttu-id="95bd1-209">**2.47%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-209">**2.47%**</span></span>|  
|<span data-ttu-id="95bd1-210">**Road-550-W**</span><span class="sxs-lookup"><span data-stu-id="95bd1-210">**Road-550-W**</span></span>|<span data-ttu-id="95bd1-211">**$3,668,383.88**</span><span class="sxs-lookup"><span data-stu-id="95bd1-211">**$3,668,383.88**</span></span>|<span data-ttu-id="95bd1-212">**$1,901.97**</span><span class="sxs-lookup"><span data-stu-id="95bd1-212">**$1,901.97**</span></span>|<span data-ttu-id="95bd1-213">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-213">**0.05%**</span></span>|  
|<span data-ttu-id="95bd1-214">**Road-350-W**</span><span class="sxs-lookup"><span data-stu-id="95bd1-214">**Road-350-W**</span></span>|<span data-ttu-id="95bd1-215">**$3,665,932.31**</span><span class="sxs-lookup"><span data-stu-id="95bd1-215">**$3,665,932.31**</span></span>|<span data-ttu-id="95bd1-216">**$20,946.50**</span><span class="sxs-lookup"><span data-stu-id="95bd1-216">**$20,946.50**</span></span>|<span data-ttu-id="95bd1-217">**0.57%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-217">**0.57%**</span></span>|  
|<span data-ttu-id="95bd1-218">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="95bd1-218">**HL Mountain Frame**</span></span>|<span data-ttu-id="95bd1-219">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-219">**$3,365,069.27**</span></span>|<span data-ttu-id="95bd1-220">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="95bd1-220">**$174.11**</span></span>|<span data-ttu-id="95bd1-221">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-221">**0.01%**</span></span>|  
|<span data-ttu-id="95bd1-222">**Road-150**</span><span class="sxs-lookup"><span data-stu-id="95bd1-222">**Road-150**</span></span>|<span data-ttu-id="95bd1-223">**$2,363,805.16**</span><span class="sxs-lookup"><span data-stu-id="95bd1-223">**$2,363,805.16**</span></span>|<span data-ttu-id="95bd1-224">**$0.00**</span><span class="sxs-lookup"><span data-stu-id="95bd1-224">**$0.00**</span></span>|<span data-ttu-id="95bd1-225">**0.00%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-225">**0.00%**</span></span>|  
|<span data-ttu-id="95bd1-226">**Touring-3000**</span><span class="sxs-lookup"><span data-stu-id="95bd1-226">**Touring-3000**</span></span>|<span data-ttu-id="95bd1-227">**$2,046,508.26**</span><span class="sxs-lookup"><span data-stu-id="95bd1-227">**$2,046,508.26**</span></span>|<span data-ttu-id="95bd1-228">**$79,582.15**</span><span class="sxs-lookup"><span data-stu-id="95bd1-228">**$79,582.15**</span></span>|<span data-ttu-id="95bd1-229">**3.89%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-229">**3.89%**</span></span>|  
  
 <span data-ttu-id="95bd1-230">下列範例說明深層「自動存在」的概念。</span><span class="sxs-lookup"><span data-stu-id="95bd1-230">The following example will illustrate the concept of deep Autoexists.</span></span> <span data-ttu-id="95bd1-231">在範例中，我們會依照 [Mountain] 群組中的 [Product].[Product Line] 屬性篩選 Top10SellingProducts。</span><span class="sxs-lookup"><span data-stu-id="95bd1-231">In the example we are filtering Top10SellingProducts by [Product].[Product Line] attribute for those in [Mountain] group.</span></span> <span data-ttu-id="95bd1-232">請注意，兩個屬性 (slicer 和 axis) 都屬於相同的維度，也就是 [Product]。</span><span class="sxs-lookup"><span data-stu-id="95bd1-232">Note that both attributes (slicer and axis) belong to the same dimension, [Product].</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `// Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="95bd1-233">產生下列結果集：</span><span class="sxs-lookup"><span data-stu-id="95bd1-233">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="95bd1-234">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-234">**Reseller Sales Amount**</span></span>|<span data-ttu-id="95bd1-235">**折扣量**</span><span class="sxs-lookup"><span data-stu-id="95bd1-235">**Discount Amount**</span></span>|<span data-ttu-id="95bd1-236">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-236">**PCT Discount**</span></span>|  
|<span data-ttu-id="95bd1-237">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="95bd1-237">**Mountain-200**</span></span>|<span data-ttu-id="95bd1-238">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="95bd1-238">**$14,356,699.36**</span></span>|<span data-ttu-id="95bd1-239">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="95bd1-239">**$19,012.71**</span></span>|<span data-ttu-id="95bd1-240">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-240">**0.13%**</span></span>|  
|<span data-ttu-id="95bd1-241">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="95bd1-241">**Mountain-100**</span></span>|<span data-ttu-id="95bd1-242">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-242">**$8,568,958.27**</span></span>|<span data-ttu-id="95bd1-243">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-243">**$139,393.27**</span></span>|<span data-ttu-id="95bd1-244">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-244">**1.63%**</span></span>|  
|<span data-ttu-id="95bd1-245">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="95bd1-245">**HL Mountain Frame**</span></span>|<span data-ttu-id="95bd1-246">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-246">**$3,365,069.27**</span></span>|<span data-ttu-id="95bd1-247">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="95bd1-247">**$174.11**</span></span>|<span data-ttu-id="95bd1-248">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-248">**0.01%**</span></span>|  
|<span data-ttu-id="95bd1-249">**Mountain-300**</span><span class="sxs-lookup"><span data-stu-id="95bd1-249">**Mountain-300**</span></span>|<span data-ttu-id="95bd1-250">**$1,907,249.38**</span><span class="sxs-lookup"><span data-stu-id="95bd1-250">**$1,907,249.38**</span></span>|<span data-ttu-id="95bd1-251">**$876.95**</span><span class="sxs-lookup"><span data-stu-id="95bd1-251">**$876.95**</span></span>|<span data-ttu-id="95bd1-252">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-252">**0.05%**</span></span>|  
|<span data-ttu-id="95bd1-253">**Mountain-500**</span><span class="sxs-lookup"><span data-stu-id="95bd1-253">**Mountain-500**</span></span>|<span data-ttu-id="95bd1-254">**$1,067,327.31**</span><span class="sxs-lookup"><span data-stu-id="95bd1-254">**$1,067,327.31**</span></span>|<span data-ttu-id="95bd1-255">**$17,266.09**</span><span class="sxs-lookup"><span data-stu-id="95bd1-255">**$17,266.09**</span></span>|<span data-ttu-id="95bd1-256">**1.62%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-256">**1.62%**</span></span>|  
|<span data-ttu-id="95bd1-257">**Mountain-400-W**</span><span class="sxs-lookup"><span data-stu-id="95bd1-257">**Mountain-400-W**</span></span>|<span data-ttu-id="95bd1-258">**$592,450.05**</span><span class="sxs-lookup"><span data-stu-id="95bd1-258">**$592,450.05**</span></span>|<span data-ttu-id="95bd1-259">**$303.49**</span><span class="sxs-lookup"><span data-stu-id="95bd1-259">**$303.49**</span></span>|<span data-ttu-id="95bd1-260">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-260">**0.05%**</span></span>|  
|<span data-ttu-id="95bd1-261">**LL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="95bd1-261">**LL Mountain Frame**</span></span>|<span data-ttu-id="95bd1-262">**$521,864.42**</span><span class="sxs-lookup"><span data-stu-id="95bd1-262">**$521,864.42**</span></span>|<span data-ttu-id="95bd1-263">**$252.41**</span><span class="sxs-lookup"><span data-stu-id="95bd1-263">**$252.41**</span></span>|<span data-ttu-id="95bd1-264">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-264">**0.05%**</span></span>|  
|<span data-ttu-id="95bd1-265">**ML Mountain Frame-W**</span><span class="sxs-lookup"><span data-stu-id="95bd1-265">**ML Mountain Frame-W**</span></span>|<span data-ttu-id="95bd1-266">**$482,953.16**</span><span class="sxs-lookup"><span data-stu-id="95bd1-266">**$482,953.16**</span></span>|<span data-ttu-id="95bd1-267">**$206.95**</span><span class="sxs-lookup"><span data-stu-id="95bd1-267">**$206.95**</span></span>|<span data-ttu-id="95bd1-268">**0.04%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-268">**0.04%**</span></span>|  
|<span data-ttu-id="95bd1-269">**ML Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="95bd1-269">**ML Mountain Frame**</span></span>|<span data-ttu-id="95bd1-270">**$343,785.29**</span><span class="sxs-lookup"><span data-stu-id="95bd1-270">**$343,785.29**</span></span>|<span data-ttu-id="95bd1-271">**$161.82**</span><span class="sxs-lookup"><span data-stu-id="95bd1-271">**$161.82**</span></span>|<span data-ttu-id="95bd1-272">**0.05%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-272">**0.05%**</span></span>|  
|<span data-ttu-id="95bd1-273">**Women's Mountain Shorts**</span><span class="sxs-lookup"><span data-stu-id="95bd1-273">**Women's Mountain Shorts**</span></span>|<span data-ttu-id="95bd1-274">**$260,304.09**</span><span class="sxs-lookup"><span data-stu-id="95bd1-274">**$260,304.09**</span></span>|<span data-ttu-id="95bd1-275">**$6,675.56**</span><span class="sxs-lookup"><span data-stu-id="95bd1-275">**$6,675.56**</span></span>|<span data-ttu-id="95bd1-276">**2.56%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-276">**2.56%**</span></span>|  
  
 <span data-ttu-id="95bd1-277">在上述結果集的 Top10SellingProducts 的清單中有七個新成員，而 Mountain-200、Mountain-100 和 HL Mountain Frame 已經移到清單的頂端。</span><span class="sxs-lookup"><span data-stu-id="95bd1-277">In the above result set we have seven newcomers to the list of Top10SellingProducts and Mountain-200, Mountain-100, and HL Mountain Frame have moved to the top of the list.</span></span> <span data-ttu-id="95bd1-278">在先前的結果集中，這三個值散置各處。</span><span class="sxs-lookup"><span data-stu-id="95bd1-278">In the previous result set those three values were interspersed.</span></span>  
  
 <span data-ttu-id="95bd1-279">這稱為「深層自動存在」，因為 Top10SellingProducts 集合經過評估以符合查詢的分割條件。</span><span class="sxs-lookup"><span data-stu-id="95bd1-279">This is called Deep Autoexists, because the Top10SellingProducts set is evaluated to meet the slicing conditions of the query.</span></span> <span data-ttu-id="95bd1-280">「深層自動存在」表示在套用 slicer 運算式、軸中的子 SELECT 運算式等之後，會評估所有運算式以符合最深層的可能空間。</span><span class="sxs-lookup"><span data-stu-id="95bd1-280">Deep Autoexists means that all expressions will be evaluated to meet the deepest possible space after applying the slicer expressions, the sub select expressions in the axis, and so on.</span></span>  
  
 <span data-ttu-id="95bd1-281">不過，使用者可能會想要能夠針對相當於 Preferred10Products 的 Top10SellingProducts 進行分析，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="95bd1-281">However, one might want to be able to do the analysis over the Top10SellingProducts as equivalent to Preferred10Products, as in the following example:</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `set Preferred10Products as '`  
  
 `{[Product].[Model Name].&[Mountain-200],`  
  
 `[Product].[Model Name].&[Road-250],`  
  
 `[Product].[Model Name].&[Mountain-100],`  
  
 `[Product].[Model Name].&[Road-650],`  
  
 `[Product].[Model Name].&[Touring-1000],`  
  
 `[Product].[Model Name].&[Road-550-W],`  
  
 `[Product].[Model Name].&[Road-350-W],`  
  
 `[Product].[Model Name].&[HL Mountain Frame],`  
  
 `[Product].[Model Name].&[Road-150],`  
  
 `[Product].[Model Name].&[Touring-3000]`  
  
 `}'`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Preferred10Products on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="95bd1-282">產生下列結果集：</span><span class="sxs-lookup"><span data-stu-id="95bd1-282">Produces the following result set:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="95bd1-283">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-283">**Reseller Sales Amount**</span></span>|<span data-ttu-id="95bd1-284">**折扣量**</span><span class="sxs-lookup"><span data-stu-id="95bd1-284">**Discount Amount**</span></span>|<span data-ttu-id="95bd1-285">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-285">**PCT Discount**</span></span>|  
|<span data-ttu-id="95bd1-286">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="95bd1-286">**Mountain-200**</span></span>|<span data-ttu-id="95bd1-287">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="95bd1-287">**$14,356,699.36**</span></span>|<span data-ttu-id="95bd1-288">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="95bd1-288">**$19,012.71**</span></span>|<span data-ttu-id="95bd1-289">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-289">**0.13%**</span></span>|  
|<span data-ttu-id="95bd1-290">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="95bd1-290">**Mountain-100**</span></span>|<span data-ttu-id="95bd1-291">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-291">**$8,568,958.27**</span></span>|<span data-ttu-id="95bd1-292">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-292">**$139,393.27**</span></span>|<span data-ttu-id="95bd1-293">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-293">**1.63%**</span></span>|  
|<span data-ttu-id="95bd1-294">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="95bd1-294">**HL Mountain Frame**</span></span>|<span data-ttu-id="95bd1-295">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-295">**$3,365,069.27**</span></span>|<span data-ttu-id="95bd1-296">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="95bd1-296">**$174.11**</span></span>|<span data-ttu-id="95bd1-297">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-297">**0.01%**</span></span>|  
  
 <span data-ttu-id="95bd1-298">在以上的結果中，分割的結果如預期般僅包含屬於 [Product].[Product Line] 中之 [Mountain] 群組的 Preferred10Products 產品，因為 Preferred10Products 是常數運算式。</span><span class="sxs-lookup"><span data-stu-id="95bd1-298">In the above results, the slicing gives a result that contains only those products from Preferred10Products that are part of the [Mountain] group in [Product].[Product Line]; as expected, because Preferred10Products is a constant expression.</span></span>  
  
 <span data-ttu-id="95bd1-299">此結果集也就是所謂的「淺層自動存在」。</span><span class="sxs-lookup"><span data-stu-id="95bd1-299">This result set is also understood as Shallow Autoexists.</span></span> <span data-ttu-id="95bd1-300">這是因為運算式是在分割子句之前接受評估的。</span><span class="sxs-lookup"><span data-stu-id="95bd1-300">This is because the expression is evaluated before the slicing clause.</span></span> <span data-ttu-id="95bd1-301">在先前的範例中，此運算式是常數運算式，用以說明概念。</span><span class="sxs-lookup"><span data-stu-id="95bd1-301">In the previous example, the expression was a constant expression for illustration purposes in order to introduce the concept.</span></span>  
  
 <span data-ttu-id="95bd1-302">「自動存在」行為可以在工作階段層級使用 `Autoexists` 連接字串屬性進行修改。</span><span class="sxs-lookup"><span data-stu-id="95bd1-302">Autoexists behavior can be modified at the session level using the `Autoexists` connection string property.</span></span> <span data-ttu-id="95bd1-303">下列範例會先開啟新的工作階段，並將 *Autoexists=3* 屬性加入到連接字串。</span><span class="sxs-lookup"><span data-stu-id="95bd1-303">The following example begins by opening a new session and adding the *Autoexists=3* property to the connection string.</span></span> <span data-ttu-id="95bd1-304">您必須開啟一個新的連接才能執行範例。</span><span class="sxs-lookup"><span data-stu-id="95bd1-304">You must open a new connection in order to do the example.</span></span> <span data-ttu-id="95bd1-305">一旦利用「自動存在」設定建立連接之後，在該連接完成之前，它都會保持在作用中。</span><span class="sxs-lookup"><span data-stu-id="95bd1-305">Once the connection is established with the Autoexist setting it will remain in effect until that connection is finished.</span></span>  
  
 `with member [Measures].[PCT Discount] AS '[Measures].[Discount Amount]/[Measures].[Reseller Sales Amount]', FORMAT_STRING = 'Percent'`  
  
 `set Top10SellingProducts as 'topcount([Product].[Model Name].children, 10, [Measures].[Reseller Sales Amount])'`  
  
 `//Preferred10Products set removed for clarity`  
  
 `select {[Measures].[Reseller Sales Amount], [Measures].[Discount Amount], [Measures].[PCT Discount]} on 0,`  
  
 `Top10SellingProducts on 1`  
  
 `from [Adventure Works]`  
  
 `where [Product].[Product Line].[Mountain]`  
  
 <span data-ttu-id="95bd1-306">下列結果集現在會顯示「自動存在」的淺層行為。</span><span class="sxs-lookup"><span data-stu-id="95bd1-306">The following result set now shows the shallow behavior of Autoexists.</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="95bd1-307">**Reseller Sales Amount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-307">**Reseller Sales Amount**</span></span>|<span data-ttu-id="95bd1-308">**折扣量**</span><span class="sxs-lookup"><span data-stu-id="95bd1-308">**Discount Amount**</span></span>|<span data-ttu-id="95bd1-309">**PCT Discount**</span><span class="sxs-lookup"><span data-stu-id="95bd1-309">**PCT Discount**</span></span>|  
|<span data-ttu-id="95bd1-310">**Mountain-200**</span><span class="sxs-lookup"><span data-stu-id="95bd1-310">**Mountain-200**</span></span>|<span data-ttu-id="95bd1-311">**$14,356,699.36**</span><span class="sxs-lookup"><span data-stu-id="95bd1-311">**$14,356,699.36**</span></span>|<span data-ttu-id="95bd1-312">**$19,012.71**</span><span class="sxs-lookup"><span data-stu-id="95bd1-312">**$19,012.71**</span></span>|<span data-ttu-id="95bd1-313">**0.13%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-313">**0.13%**</span></span>|  
|<span data-ttu-id="95bd1-314">**Mountain-100**</span><span class="sxs-lookup"><span data-stu-id="95bd1-314">**Mountain-100**</span></span>|<span data-ttu-id="95bd1-315">**$8,568,958.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-315">**$8,568,958.27**</span></span>|<span data-ttu-id="95bd1-316">**$139,393.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-316">**$139,393.27**</span></span>|<span data-ttu-id="95bd1-317">**1.63%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-317">**1.63%**</span></span>|  
|<span data-ttu-id="95bd1-318">**HL Mountain Frame**</span><span class="sxs-lookup"><span data-stu-id="95bd1-318">**HL Mountain Frame**</span></span>|<span data-ttu-id="95bd1-319">**$3,365,069.27**</span><span class="sxs-lookup"><span data-stu-id="95bd1-319">**$3,365,069.27**</span></span>|<span data-ttu-id="95bd1-320">**$174.11**</span><span class="sxs-lookup"><span data-stu-id="95bd1-320">**$174.11**</span></span>|<span data-ttu-id="95bd1-321">**0.01%**</span><span class="sxs-lookup"><span data-stu-id="95bd1-321">**0.01%**</span></span>|  
  
 <span data-ttu-id="95bd1-322">您可以在連接字串中使用自動存在 = [1 | 2 | 3] 參數來修改自動存在行為;如需參數使用方式，請參閱[支援的 Xmla 屬性 &#40;xmla&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)和 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="95bd1-322">Autoexists behavior can be modified by using the AUTOEXISTS=[1|2|3] parameter in the connection string; see [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) and <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> for parameter usage.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bd1-323">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95bd1-323">See Also</span></span>  
 <span data-ttu-id="95bd1-324">[MDX 中的重要概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="95bd1-324">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="95bd1-325">[Cube 空間](cube-space.md) </span><span class="sxs-lookup"><span data-stu-id="95bd1-325">[Cube Space](cube-space.md) </span></span>  
 <span data-ttu-id="95bd1-326">[得到](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="95bd1-326">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="95bd1-327">[使用成員、元組和集合 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="95bd1-327">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="95bd1-328">[視覺效果總計和非視覺化總計](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="95bd1-328">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="95bd1-329">[Mdx 語言參考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="95bd1-329">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="95bd1-330">多維度運算式 &#40;MDX&#41 參考</span><span class="sxs-lookup"><span data-stu-id="95bd1-330">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
