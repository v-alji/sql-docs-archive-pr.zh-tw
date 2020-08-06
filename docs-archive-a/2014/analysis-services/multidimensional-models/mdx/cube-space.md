---
title: Cube 空間 |Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c3a012b4-9ca0-4fb8-9c26-5ecc0e2e2b2b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0a6a6da73815f06aa5ab80f6ad5a9d06227ed842
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594744"
---
# <a name="cube-space"></a><span data-ttu-id="3f81c-102">Cube 空間</span><span class="sxs-lookup"><span data-stu-id="3f81c-102">Cube Space</span></span>
  <span data-ttu-id="3f81c-103">「Cube 空間」是 Cube 屬性階層中具有 Cube 量值之成員的乘積。</span><span class="sxs-lookup"><span data-stu-id="3f81c-103">Cube space is the product of the members of a cube's attribute hierarchies with the cube's measures.</span></span> <span data-ttu-id="3f81c-104">因此，Cube 空間是由 Cube 所有屬性階層成員和 Cube 量值的組合乘積所決定，定義了 Cube 的大小上限。</span><span class="sxs-lookup"><span data-stu-id="3f81c-104">Therefore, the cube space is determined by the combinatorial product of all attribute hierarchy members in the cube and the cube's measures and defines the maximum size of the cube.</span></span> <span data-ttu-id="3f81c-105">請務必注意，此空間包含屬性階層成員的所有可能組合，甚至還包含在真實世界中被視為不可能的組合，例如城市為巴黎而國家/地區為英國、西班牙、日本、印度或其他地方的組合。</span><span class="sxs-lookup"><span data-stu-id="3f81c-105">It is important to note that this space includes all possible combinations of attribute hierarchy members; even combinations that might be deem as impossible in the real world i.e. combinations where the city is Paris and the countries are England or Spain or Japan or India or elsewhere.</span></span>  
  
## <a name="autoexists-and-cube-space"></a><span data-ttu-id="3f81c-106">自動存在和 Cube 空間</span><span class="sxs-lookup"><span data-stu-id="3f81c-106">Autoexists and cube space</span></span>  
 <span data-ttu-id="3f81c-107">「自動存在」\*\* 的概念將此 Cube 空間限制於實際存在的資料格。</span><span class="sxs-lookup"><span data-stu-id="3f81c-107">The concept of *autoexists* limits this cube space to those cells that actually exist.</span></span> <span data-ttu-id="3f81c-108">維度中屬性階層的成員可能不與相同維度中另一個屬性階層的成員同時存在。</span><span class="sxs-lookup"><span data-stu-id="3f81c-108">Members of an attribute hierarchy in a dimension may not exist with members of another attribute hierarchy in the same dimension.</span></span>  
  
 <span data-ttu-id="3f81c-109">例如，如果 Cube 有 City 屬性階層、Country 屬性階層及 Internet Sales Amount 量值，此 Cube 的空間只會包含同時存在的成員。</span><span class="sxs-lookup"><span data-stu-id="3f81c-109">For example, if you have a cube that has a City attribute hierarchy, a Country attribute hierarchy, and an Internet Sales Amount measure, the space of this cube only includes those members that exist with each other.</span></span> <span data-ttu-id="3f81c-110">例如，如果 City 屬性階層包含紐約、倫敦、巴黎、東京及墨爾本等城市，並且 Country 屬性階層包含美國、英國、法國、日本及澳洲等國家 (地區)，則 Cube 的空間不會包含巴黎和美國交集的空間 (資料格)。</span><span class="sxs-lookup"><span data-stu-id="3f81c-110">For example, if the City attribute hierarchy includes the cities New York, London, Paris, Tokyo, and Melbourne; and the Country attribute hierarchy includes the countries United States, United Kingdom, France, Japan, and Australia; then the space of the cube does not include the space (cell) at the intersection of Paris and United States.</span></span>  
  
 <span data-ttu-id="3f81c-111">當查詢不存在的資料格時，不存在的資料格會傳回 Null，也就是說，它們不包含計算，而且您無法定義寫入此空間的計算。</span><span class="sxs-lookup"><span data-stu-id="3f81c-111">When querying cells that do not exist, non-existing cells return nulls; that is, they cannot contain calculations and you cannot define a calculation that writes to this space.</span></span> <span data-ttu-id="3f81c-112">例如，下列陳述式包括了不存在的資料格。</span><span class="sxs-lookup"><span data-stu-id="3f81c-112">For example, the following statement includes cells that do not exist.</span></span>  
  
```  
SELECT [Customer].[Gender].[Gender].Members ON COLUMNS,  
{[Customer].[Customer].[Aaron A. Allen]  
   ,[Customer].[Customer].[Abigail Clark]} ON ROWS   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3f81c-113">這個查詢使用 [Members (Set) (MDX)](/sql/mdx/members-set-mdx) 函數來傳回資料行軸上 Gender 屬性階層的成員集合，並且將該集合與資料列軸上 Customer 屬性階層的指定成員集合相交。</span><span class="sxs-lookup"><span data-stu-id="3f81c-113">This query uses the [Members (Set) (MDX)](/sql/mdx/members-set-mdx) function to return the set of members of the Gender attribute hierarchy on the column axis, and crosses this set with the specified set of members from the Customer attribute hierarchy on the row axis.</span></span>  
  
 <span data-ttu-id="3f81c-114">當您執行上述查詢時，Aaron A. Allen 和 Female 交集處的資料格會顯示 Null。</span><span class="sxs-lookup"><span data-stu-id="3f81c-114">When you execute the previous query, the cell at the intersection of Aaron A. Allen and Female displays a null.</span></span> <span data-ttu-id="3f81c-115">同樣地，Abigail Clark 和 Male 交集處的資料格也會顯示 Null。</span><span class="sxs-lookup"><span data-stu-id="3f81c-115">Similarly, the cell at the intersection of Abigail Clark and Male displays a null.</span></span> <span data-ttu-id="3f81c-116">這些資料格不存在，也不包含值，但在查詢傳回的結果中會出現不存在的資料格。</span><span class="sxs-lookup"><span data-stu-id="3f81c-116">These cells do not exist and cannot contain a value, but cells that do not exist can appear in the result returned by a query.</span></span>  
  
 <span data-ttu-id="3f81c-117">當您使用 [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) 函數傳回相同維度中多個屬性階層之成員的交叉乘積時，自動存在功能會將所傳回的 Tuple 限制於實際存在的 Tuple 集合，而不會傳回整個笛卡兒乘積。</span><span class="sxs-lookup"><span data-stu-id="3f81c-117">When you use the [Crossjoin (MDX)](/sql/mdx/crossjoin-mdx) function to return the cross-product of attribute hierarchy members from attribute hierarchies in the same dimension, auto-exists limits those tuples being returned to the set of tuples that actually exist, rather than returning a full Cartesian product.</span></span> <span data-ttu-id="3f81c-118">例如，執行下列查詢，然後檢查執行的結果。</span><span class="sxs-lookup"><span data-stu-id="3f81c-118">For example, run and then examine the results from the execution of the following query.</span></span>  
  
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
>  <span data-ttu-id="3f81c-119">請注意，0 是用來指定資料行軸，為 axis(0) (即資料行軸) 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="3f81c-119">Notice that 0 is used to designate the column axis, which is shorthand for axis(0) - which is the column axis.</span></span>  
  
 <span data-ttu-id="3f81c-120">上述查詢只會針對查詢中每個屬性階層之同時存在的成員傳回資料格。</span><span class="sxs-lookup"><span data-stu-id="3f81c-120">The previous query only returns cells for members from each attribute hierarchy in the query that exist with each other.</span></span> <span data-ttu-id="3f81c-121">先前的查詢也可以使用[ \* (交叉聯結)  (MDX) ](/sql/mdx/crossjoin-mdx)函數的新 \* 變體來撰寫。</span><span class="sxs-lookup"><span data-stu-id="3f81c-121">The previous query can also be written using the new \* variant of the [\* (Crossjoin) (MDX)](/sql/mdx/crossjoin-mdx) function.</span></span>  
  
```  
SELECT   
   [Customer].[Country].[United States] *   
      [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="3f81c-122">上述查詢也可以撰寫成下列方式：</span><span class="sxs-lookup"><span data-stu-id="3f81c-122">The previous query could also be written in the following manner:</span></span>  
  
```  
SELECT [Customer].[State-Province].Members  
ON 0   
FROM [Adventure Works]  
WHERE (Measures.[Internet Sales Amount],  
   [Customer].[Country].[United States])  
```  
  
 <span data-ttu-id="3f81c-123">所傳回的資料格值將會相同，不過結果集中的中繼資料將會不同。</span><span class="sxs-lookup"><span data-stu-id="3f81c-123">The cells values returned will be identical, although the metadata in the result set will be different.</span></span> <span data-ttu-id="3f81c-124">例如，在上述查詢中，Country 階層已移至 slicer 座標軸 (在 WHERE 子句中)，因此不會明確出現在結果集中。</span><span class="sxs-lookup"><span data-stu-id="3f81c-124">For example, with the previous query, the Country hierarchy was moved to the slicer axis (in the WHERE clause) and therefore does not appear explicitly in the result set.</span></span>  
  
 <span data-ttu-id="3f81c-125">這三個先前的查詢都會示範中自動存在行為的作用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3f81c-125">Each of these three previous queries demonstrates the effect of the auto-exists behavior in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="user-defined-hierarchies-and-cube-space"></a><span data-ttu-id="3f81c-126">使用者自訂階層和 Cube 空間</span><span class="sxs-lookup"><span data-stu-id="3f81c-126">User-Defined Hierarchies and Cube Space</span></span>  
 <span data-ttu-id="3f81c-127">在本主題的先前範例中，我們都是使用屬性階層來定義 Cube 空間中的位置。</span><span class="sxs-lookup"><span data-stu-id="3f81c-127">The previous examples in this topic define positions in cube space by using attribute hierarchies.</span></span> <span data-ttu-id="3f81c-128">然而，您也可以利用使用者自訂階層 (已經根據維度中的屬性階層加以定義)，定義 Cube 空間中的位置。</span><span class="sxs-lookup"><span data-stu-id="3f81c-128">However, you can also define a position in cube space by using user-defined hierarchies that have been defined based on attribute hierarchies in a dimension.</span></span> <span data-ttu-id="3f81c-129">使用者自訂階層是由屬性階層組成的階層，設計目的為幫助使用者瀏覽 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="3f81c-129">A user-defined hierarchy is a hierarchy of attribute hierarchies designed to facilitate browsing of cube data by users.</span></span>  
  
 <span data-ttu-id="3f81c-130">例如，上節中的 `CROSSJOIN` 查詢也可以撰寫如下：</span><span class="sxs-lookup"><span data-stu-id="3f81c-130">For example, the `CROSSJOIN` query in the previous section could also have been written as follows:</span></span>  
  
```  
SELECT CROSSJOIN  
   (  
      {[Customer].[Country].[United States]},  
         [Customer].[Customer Geography].[State-Province].Members  
   )   
ON 0   
FROM [Adventure Works]  
WHERE Measures.[Internet Sales Amount]  
```  
  
 <span data-ttu-id="3f81c-131">在上述查詢中，Customer 維度內的 Customer Geography 使用者自訂階層是用來定義 Cube 空間中的位置 (先前是使用屬性階層加以定義)。</span><span class="sxs-lookup"><span data-stu-id="3f81c-131">In the previous query, the Customer Geography user-defined hierarchy within the Customer dimension is used to define the position in cube space that was previously defined by using an attribute hierarchy.</span></span> <span data-ttu-id="3f81c-132">使用屬性階層或使用者自訂階層，都可以定義 Cube 空間中的相同位置。</span><span class="sxs-lookup"><span data-stu-id="3f81c-132">The identical position in cube space can be defined by using either attribute hierarchies or user-defined hierarchies.</span></span>  
  
##  <a name="attribute-relationships-and-cube-space"></a><a name="AttribRelationships"></a><span data-ttu-id="3f81c-133">屬性關聯性和 Cube 空間</span><span class="sxs-lookup"><span data-stu-id="3f81c-133">Attribute Relationships and Cube Space</span></span>  
 <span data-ttu-id="3f81c-134">定義相關屬性之間的屬性關聯性後，不僅查詢效能會因著建立適當彙總而提高，與屬性階層成員同時出現的相關屬性階層成員也會因此受影響。</span><span class="sxs-lookup"><span data-stu-id="3f81c-134">Defining attribute relationships between related attributes improves query performance (by facilitating the creation of appropriate aggregations) and affects the member of a related attribute hierarchy that appears with an attribute hierarchy member.</span></span> <span data-ttu-id="3f81c-135">例如，當您定義的 Tuple 包含 City 屬性階層的成員，並且該 Tuple 沒有明確定義 Country 屬性階層成員，您可能預期預設的 Country 屬性階層成員將會是 Country 屬性階層的相關成員。</span><span class="sxs-lookup"><span data-stu-id="3f81c-135">For example, when you define a tuple that includes a member from the City attribute hierarchy and the tuple does not explicitly define the Country attribute hierarchy member, you might expect that the default Country attribute hierarchy member would be the related member of the Country attribute hierarchy.</span></span> <span data-ttu-id="3f81c-136">然而，只有在 City 屬性階層和 Country 屬性階層之間已定義屬性關聯性時，這個狀況才會屬實。</span><span class="sxs-lookup"><span data-stu-id="3f81c-136">However, this is only true if an attribute relationship is defined between the City attribute hierarchy and the Country attribute hierarchy.</span></span>  
  
 <span data-ttu-id="3f81c-137">下列範例會傳回查詢中沒有明確包含之相關屬性階層的成員。</span><span class="sxs-lookup"><span data-stu-id="3f81c-137">The following example returns the member of a related attribute hierarchy that is not included explicitly in the query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Country.CurrentMember.Name  
SELECT Measures.x ON 0,  
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3f81c-138">請注意， `WITH` 關鍵字會與[CURRENTMEMBER (mdx) ](/sql/mdx/current-mdx)和[名稱 (mdx) ](/sql/mdx/members-string-mdx)函數一起使用，以建立要在查詢中使用的匯出成員。</span><span class="sxs-lookup"><span data-stu-id="3f81c-138">Notice that the `WITH` keyword is used with the [CurrentMember (MDX)](/sql/mdx/current-mdx) and [Name (MDX)](/sql/mdx/members-string-mdx) functions to create a calculated member for use in the query.</span></span> <span data-ttu-id="3f81c-139">如需詳細資訊，請參閱[基本 MDX 查詢 &#40;MDX&#41;](mdx-query-the-basic-query.md)。</span><span class="sxs-lookup"><span data-stu-id="3f81c-139">For more information, see [The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md).</span></span>  
  
 <span data-ttu-id="3f81c-140">在上述查詢中，會傳回與 State 屬性階層之每個成員相關的 Country 屬性階層的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="3f81c-140">In the previous query, the name of the member of the Country attribute hierarchy that is associated with each member of the State attribute hierarchy is returned.</span></span> <span data-ttu-id="3f81c-141">預期的 Country 成員會出現 (因為 City 和 Country 屬性之間已定義屬性關聯性)。</span><span class="sxs-lookup"><span data-stu-id="3f81c-141">The expected Country member appears (because an attribute relationship is defined between the City and Country attributes).</span></span> <span data-ttu-id="3f81c-142">然而，如果相同維度中的多個屬性階層之間沒有定義屬性關聯性，則會傳回 (全部) 成員，如下列查詢所說明。</span><span class="sxs-lookup"><span data-stu-id="3f81c-142">However, if no attribute relationship were defined between attribute hierarchies in the same dimension, the (All) member would be returned, as illustrated in the following query.</span></span>  
  
```  
WITH MEMBER Measures.x AS   
   Customer.Education.Currentmember.Name  
SELECT Measures.x  ON 0,   
Customer.City.Members ON 1  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="3f81c-143">在上述查詢中，會傳回 (全部) 成員 ("All Customers")，因為 Education 和 City 之間沒有關聯性。</span><span class="sxs-lookup"><span data-stu-id="3f81c-143">In the previous query, the (All) member ("All Customers") is returned, because there is no relationship between Education and City.</span></span> <span data-ttu-id="3f81c-144">因此，在包含 City 屬性階層但沒有明確提供 Education 成員的任何 Tuple 中，Education 屬性階層的 (全部) 成員將會是 Education 屬性階層的預設成員。</span><span class="sxs-lookup"><span data-stu-id="3f81c-144">Therefore, the (All) member of the Education attribute hierarchy would be the default member of the Education attribute hierarchy used in any tuple involving the City attribute hierarchy where an Education member is not explicitly provided.</span></span>  
  
## <a name="calculation-context"></a><span data-ttu-id="3f81c-145">計算內容</span><span class="sxs-lookup"><span data-stu-id="3f81c-145">Calculation Context</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f81c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f81c-146">See Also</span></span>  
 <span data-ttu-id="3f81c-147">[MDX 中的重要概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="3f81c-147">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="3f81c-148">[得到](tuples.md) </span><span class="sxs-lookup"><span data-stu-id="3f81c-148">[Tuples](tuples.md) </span></span>  
 <span data-ttu-id="3f81c-149">[自動存在](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="3f81c-149">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="3f81c-150">[使用成員、元組和集合 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="3f81c-150">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="3f81c-151">[視覺效果總計和非視覺化總計](visual-totals-and-non-visual-totals.md) </span><span class="sxs-lookup"><span data-stu-id="3f81c-151">[Visual Totals and Non Visual Totals](visual-totals-and-non-visual-totals.md) </span></span>  
 <span data-ttu-id="3f81c-152">[Mdx 語言參考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="3f81c-152">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="3f81c-153">多維度運算式 &#40;MDX&#41 參考</span><span class="sxs-lookup"><span data-stu-id="3f81c-153">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
