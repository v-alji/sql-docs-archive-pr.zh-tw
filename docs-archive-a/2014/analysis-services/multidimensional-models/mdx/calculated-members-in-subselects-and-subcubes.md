---
title: 子選擇和 Subcube 中的匯出成員 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e35e8f7-ae1c-4549-8432-accf036d2373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6e6f4277c864b637c7fc5d93232ac6ebd8c4bb4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597414"
---
# <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="2c30c-102">子選擇和 Subcube 中的導出成員</span><span class="sxs-lookup"><span data-stu-id="2c30c-102">Calculated Members in Subselects and Subcubes</span></span>
  <span data-ttu-id="2c30c-103">在舊版，子選擇或 Subcube 中不允許使用導出成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-103">In previous releases, calculated members were not allowed in subselects or subcubes.</span></span> <span data-ttu-id="2c30c-104">但是從 SQL Server 2008 開始，您可以使用導出成員，並透過連接屬性啟用。</span><span class="sxs-lookup"><span data-stu-id="2c30c-104">However, starting with SQL Server 2008 they are allowed and enabled by a connection property.</span></span> <span data-ttu-id="2c30c-105">此外，SQL Server 2008 R2 也導入了子選擇和 Subcube 中導出成員的新行為。</span><span class="sxs-lookup"><span data-stu-id="2c30c-105">In addition, a new behavior for calculated members, in subselects and subcubes, was introduced in SQL Server 2008 R2.</span></span>  
  
## <a name="calculated-members-in-subselects-and-subcubes"></a><span data-ttu-id="2c30c-106">子選擇和 Subcube 中的導出成員</span><span class="sxs-lookup"><span data-stu-id="2c30c-106">Calculated Members in Subselects and Subcubes</span></span>  
 <span data-ttu-id="2c30c-107">`SubQueries`中的連接字串屬性 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> 或 `DBPROPMSMDSUBQUERIES` 支援的 xmla 屬性中的屬性[&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)會在子選擇或 subcube 上定義匯出成員或匯出集的行為或額度。</span><span class="sxs-lookup"><span data-stu-id="2c30c-107">The `SubQueries` connection string property in <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> or the `DBPROPMSMDSUBQUERIES` property in [Supported XMLA Properties &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) defines the behavior or allowance of calculated members or calculated sets on subselects or subcubes.</span></span> <span data-ttu-id="2c30c-108">在本文的內容中，除非另有說明，否則子選擇同時指子選擇和 Subcube。</span><span class="sxs-lookup"><span data-stu-id="2c30c-108">In the context of this document, subselect refers to subselects and subcubes unless otherwise stated.</span></span>  
  
 <span data-ttu-id="2c30c-109">SubQueries 屬性允許下列值。</span><span class="sxs-lookup"><span data-stu-id="2c30c-109">The SubQueries property allows the following values.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c30c-110">值</span><span class="sxs-lookup"><span data-stu-id="2c30c-110">Value</span></span>|<span data-ttu-id="2c30c-111">描述</span><span class="sxs-lookup"><span data-stu-id="2c30c-111">Description</span></span>|  
|<span data-ttu-id="2c30c-112">0</span><span class="sxs-lookup"><span data-stu-id="2c30c-112">0</span></span>|<span data-ttu-id="2c30c-113">子選擇或 Subcube 中不允許使用導出成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-113">Calculated members are not allowed in subselects or subcubes.</span></span><br /><br /> <span data-ttu-id="2c30c-114">評估子選擇或 Subcube 時，如果參考導出成員就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c30c-114">An error is raised when evaluating the subselect or subcube if a calculated member is referenced.</span></span>|  
|<span data-ttu-id="2c30c-115">1</span><span class="sxs-lookup"><span data-stu-id="2c30c-115">1</span></span>|<span data-ttu-id="2c30c-116">子選擇或 Subcube 中允許使用導出成員，但是在傳回的子空間中未導入上階成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-116">Calculated members are allowed in subselects or subcubes but no ascendant members are introduced in the returning subspace.</span></span>|  
|<span data-ttu-id="2c30c-117">2</span><span class="sxs-lookup"><span data-stu-id="2c30c-117">2</span></span>|<span data-ttu-id="2c30c-118">子選擇或 Subcube 中允許使用導出成員，而且在傳回的子空間中導入上階成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-118">Calculated members are allowed in subselects or subcubes and ascendant members are introduced in the returning subspace.</span></span> <span data-ttu-id="2c30c-119">此外，在選取導出成員時允許使用混合資料粒度。</span><span class="sxs-lookup"><span data-stu-id="2c30c-119">Also, mixed granularity is allowed in the selection of calculated members.</span></span>|  
  
 <span data-ttu-id="2c30c-120">如果在 SubQueries 屬性中使用值 1 或 2，即可允許導出成員用來篩選子選擇的傳回子空間。</span><span class="sxs-lookup"><span data-stu-id="2c30c-120">Using values of 1 or 2 in the SubQueries property allows calculated members to be used to filter the returning subspace of subselects.</span></span>  
  
 <span data-ttu-id="2c30c-121">範例將有助於釐清概念；首先必須建立導出成員，然後發出子選擇查詢，以示範上述行為。</span><span class="sxs-lookup"><span data-stu-id="2c30c-121">An example will help clarify the concept; first a calculated member must be created and then a subselect query issued to show the above mentioned behavior.</span></span>  
  
 <span data-ttu-id="2c30c-122">下列範例會建立一個在 [Geography].[Geography] 階層的 Washington 州底下加入 [Seattle Metro] 市的導出成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-122">The following sample creates a calculated member that adds [Seattle Metro] as a city to the [Geography].[Geography] hierarchy under Washington state.</span></span>  
  
 <span data-ttu-id="2c30c-123">若要執行範例，連接字串必須包含有 1 值的 SubQueries 屬性，而且所有 MDX 陳述式必須在相同工作階段中執行。</span><span class="sxs-lookup"><span data-stu-id="2c30c-123">To run the example, the connection string must contain the SubQueries property with a value of 1 and all MDX statements must be run in the same session.</span></span>  
  
 <span data-ttu-id="2c30c-124">首先發出下列 MDX 運算式：</span><span class="sxs-lookup"><span data-stu-id="2c30c-124">First issue the following MDX expression:</span></span>  
  
```  
//Remember to set Subqueries=1 in the connection string prior  
//to issue these commands  
//--> AS2008 behavior  
CREATE MEMBER [Adventure Works].[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]   
   AS  AGGREGATE(   
                 {   
                   [Geography].[Geography].[City].&[Bellevue]&[WA]  
                 , [Geography].[Geography].[City].&[Issaquah]&[WA]  
                 , [Geography].[Geography].[City].&[Redmond]&[WA]  
                 , [Geography].[Geography].[City].&[Seattle]&[WA]  
                 }  
                )    
```  
  
 <span data-ttu-id="2c30c-125">接著發出下列 MDX 查詢，以查看子選擇中允許的導出成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-125">Then issue the following MDX query to see calculated members allowed in subselects.</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]} on 0 from [Adventure Works])  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="2c30c-126">取得的結果為：</span><span class="sxs-lookup"><span data-stu-id="2c30c-126">The obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="2c30c-127">All Periods</span><span class="sxs-lookup"><span data-stu-id="2c30c-127">All Periods</span></span>|<span data-ttu-id="2c30c-128">CY 2001</span><span class="sxs-lookup"><span data-stu-id="2c30c-128">CY 2001</span></span>|<span data-ttu-id="2c30c-129">CY 2002</span><span class="sxs-lookup"><span data-stu-id="2c30c-129">CY 2002</span></span>|<span data-ttu-id="2c30c-130">CY 2003</span><span class="sxs-lookup"><span data-stu-id="2c30c-130">CY 2003</span></span>|<span data-ttu-id="2c30c-131">CY 2004</span><span class="sxs-lookup"><span data-stu-id="2c30c-131">CY 2004</span></span>|  
|<span data-ttu-id="2c30c-132">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="2c30c-132">Seattle Metro Agg</span></span>|<span data-ttu-id="2c30c-133">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="2c30c-133">$2,383,545.69</span></span>|<span data-ttu-id="2c30c-134">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="2c30c-134">$291,248.93</span></span>|<span data-ttu-id="2c30c-135">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="2c30c-135">$763,557.02</span></span>|<span data-ttu-id="2c30c-136">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="2c30c-136">$915,832.36</span></span>|<span data-ttu-id="2c30c-137">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="2c30c-137">$412,907.37</span></span>|  
  
 <span data-ttu-id="2c30c-138">如上述，當 SubQueries=1 時，傳回的子空間中沒有 [Seattle Metro] 的上階，因此 [Geography].[Geography].allmembers 只包含導出成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-138">As said before, the ascendants of [Seattle Metro] do not exist in the returned subspace, when SubQueries=1, hence [Geography].[Geography].allmembers only contains the calculated member.</span></span>  
  
 <span data-ttu-id="2c30c-139">如果在連接字串中使用 SubQueries=2 來執行範例，取得的結果為：</span><span class="sxs-lookup"><span data-stu-id="2c30c-139">If the example is run using SubQueries=2, in the connection string, the obtained results are:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="2c30c-140">All Periods</span><span class="sxs-lookup"><span data-stu-id="2c30c-140">All Periods</span></span>|<span data-ttu-id="2c30c-141">CY 2001</span><span class="sxs-lookup"><span data-stu-id="2c30c-141">CY 2001</span></span>|<span data-ttu-id="2c30c-142">CY 2002</span><span class="sxs-lookup"><span data-stu-id="2c30c-142">CY 2002</span></span>|<span data-ttu-id="2c30c-143">CY 2003</span><span class="sxs-lookup"><span data-stu-id="2c30c-143">CY 2003</span></span>|<span data-ttu-id="2c30c-144">CY 2004</span><span class="sxs-lookup"><span data-stu-id="2c30c-144">CY 2004</span></span>|  
|<span data-ttu-id="2c30c-145">All Geographies</span><span class="sxs-lookup"><span data-stu-id="2c30c-145">All Geographies</span></span>|<span data-ttu-id="2c30c-146">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-146">(null)</span></span>|<span data-ttu-id="2c30c-147">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-147">(null)</span></span>|<span data-ttu-id="2c30c-148">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-148">(null)</span></span>|<span data-ttu-id="2c30c-149">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-149">(null)</span></span>|<span data-ttu-id="2c30c-150">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-150">(null)</span></span>|  
|<span data-ttu-id="2c30c-151">美國</span><span class="sxs-lookup"><span data-stu-id="2c30c-151">United States</span></span>|<span data-ttu-id="2c30c-152">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-152">(null)</span></span>|<span data-ttu-id="2c30c-153">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-153">(null)</span></span>|<span data-ttu-id="2c30c-154">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-154">(null)</span></span>|<span data-ttu-id="2c30c-155">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-155">(null)</span></span>|<span data-ttu-id="2c30c-156">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-156">(null)</span></span>|  
|<span data-ttu-id="2c30c-157">Washington</span><span class="sxs-lookup"><span data-stu-id="2c30c-157">Washington</span></span>|<span data-ttu-id="2c30c-158">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-158">(null)</span></span>|<span data-ttu-id="2c30c-159">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-159">(null)</span></span>|<span data-ttu-id="2c30c-160">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-160">(null)</span></span>|<span data-ttu-id="2c30c-161">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-161">(null)</span></span>|<span data-ttu-id="2c30c-162">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-162">(null)</span></span>|  
|<span data-ttu-id="2c30c-163">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="2c30c-163">Seattle Metro Agg</span></span>|<span data-ttu-id="2c30c-164">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="2c30c-164">$2,383,545.69</span></span>|<span data-ttu-id="2c30c-165">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="2c30c-165">$291,248.93</span></span>|<span data-ttu-id="2c30c-166">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="2c30c-166">$763,557.02</span></span>|<span data-ttu-id="2c30c-167">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="2c30c-167">$915,832.36</span></span>|<span data-ttu-id="2c30c-168">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="2c30c-168">$412,907.37</span></span>|  
  
 <span data-ttu-id="2c30c-169">如上述，使用 SubQueries=2 時，傳回的子空間中有 [Seattle Metro] 的上階，但沒有這些成員的值，因為沒有可提供彙總的一般成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-169">As said before, when using SubQueries=2, the ascendants of [Seattle Metro] exist in the returned subspace but no values exist for those members because there is no regular members to provide for the aggregations.</span></span> <span data-ttu-id="2c30c-170">因此，在這個範例中，針對導出成員的所有上階成員提供 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="2c30c-170">Therefore, NULL values are provided for all ascendant members of the calculated member in this example.</span></span>  
  
 <span data-ttu-id="2c30c-171">若要了解以上的行為，請務必了解導出成員不同於一般成員，並不會提供其父系的彙總；前者表示只單獨依照導出成員來篩選，會導致空上階，因為沒有可提供產生子空間之彙總值的一般成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-171">To understand the above behavior, it helps to understand that calculated members do not contribute to the aggregations of their parents as regular members do; the former implies that filtering by calculated members alone will lead to empty ascendants because there are no regular members to contribute to the aggregated values of the resulting subspace.</span></span> <span data-ttu-id="2c30c-172">如果您將一般成員加入至篩選運算式，彙總值就會來自這些一般成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-172">If you add regular members to the filtering expression then the aggregated values will come from those regular members.</span></span> <span data-ttu-id="2c30c-173">繼續上述的範例，如果 Oregon 州的 Portland 市以及 Washington 州的 Spokane 市加入至出現導出成員的相同軸中，如下列 MDX 運算式所示：</span><span class="sxs-lookup"><span data-stu-id="2c30c-173">Continuing with the above example, if the cities of Portland, in Oregon, and the city of Spokane, in Washington, are added to the same axis where the calculated member appears; as shown in the next MDX expression:</span></span>  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {  
               [Seattle Metro Agg]  
             , [Geography].[Geography].[City].&[Portland]&[OR]  
             , [Geography].[Geography].[City].&[Spokane]&[WA]  
             } on 0 from [Adventure Works]  
     )  
Where [Measures].[Reseller Sales Amount]  
```  
  
 <span data-ttu-id="2c30c-174">則會取得下列結果。</span><span class="sxs-lookup"><span data-stu-id="2c30c-174">The following results are obtained.</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="2c30c-175">All Periods</span><span class="sxs-lookup"><span data-stu-id="2c30c-175">All Periods</span></span>|<span data-ttu-id="2c30c-176">CY 2001</span><span class="sxs-lookup"><span data-stu-id="2c30c-176">CY 2001</span></span>|<span data-ttu-id="2c30c-177">CY 2002</span><span class="sxs-lookup"><span data-stu-id="2c30c-177">CY 2002</span></span>|<span data-ttu-id="2c30c-178">CY 2003</span><span class="sxs-lookup"><span data-stu-id="2c30c-178">CY 2003</span></span>|<span data-ttu-id="2c30c-179">CY 2004</span><span class="sxs-lookup"><span data-stu-id="2c30c-179">CY 2004</span></span>|  
|<span data-ttu-id="2c30c-180">All Geographies</span><span class="sxs-lookup"><span data-stu-id="2c30c-180">All Geographies</span></span>|<span data-ttu-id="2c30c-181">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="2c30c-181">$235,171.62</span></span>|<span data-ttu-id="2c30c-182">$419.46</span><span class="sxs-lookup"><span data-stu-id="2c30c-182">$419.46</span></span>|<span data-ttu-id="2c30c-183">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-183">$4,996.25</span></span>|<span data-ttu-id="2c30c-184">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="2c30c-184">$131,788.82</span></span>|<span data-ttu-id="2c30c-185">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="2c30c-185">$97,967.09</span></span>|  
|<span data-ttu-id="2c30c-186">美國</span><span class="sxs-lookup"><span data-stu-id="2c30c-186">United States</span></span>|<span data-ttu-id="2c30c-187">$235,171.62</span><span class="sxs-lookup"><span data-stu-id="2c30c-187">$235,171.62</span></span>|<span data-ttu-id="2c30c-188">$419.46</span><span class="sxs-lookup"><span data-stu-id="2c30c-188">$419.46</span></span>|<span data-ttu-id="2c30c-189">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-189">$4,996.25</span></span>|<span data-ttu-id="2c30c-190">$131,788.82</span><span class="sxs-lookup"><span data-stu-id="2c30c-190">$131,788.82</span></span>|<span data-ttu-id="2c30c-191">$97,967.09</span><span class="sxs-lookup"><span data-stu-id="2c30c-191">$97,967.09</span></span>|  
|<span data-ttu-id="2c30c-192">Oregon</span><span class="sxs-lookup"><span data-stu-id="2c30c-192">Oregon</span></span>|<span data-ttu-id="2c30c-193">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-193">$30,968.25</span></span>|<span data-ttu-id="2c30c-194">$419.46</span><span class="sxs-lookup"><span data-stu-id="2c30c-194">$419.46</span></span>|<span data-ttu-id="2c30c-195">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-195">$4,996.25</span></span>|<span data-ttu-id="2c30c-196">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="2c30c-196">$17,442.97</span></span>|<span data-ttu-id="2c30c-197">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="2c30c-197">$8,109.56</span></span>|  
|<span data-ttu-id="2c30c-198">Portland</span><span class="sxs-lookup"><span data-stu-id="2c30c-198">Portland</span></span>|<span data-ttu-id="2c30c-199">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-199">$30,968.25</span></span>|<span data-ttu-id="2c30c-200">$419.46</span><span class="sxs-lookup"><span data-stu-id="2c30c-200">$419.46</span></span>|<span data-ttu-id="2c30c-201">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-201">$4,996.25</span></span>|<span data-ttu-id="2c30c-202">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="2c30c-202">$17,442.97</span></span>|<span data-ttu-id="2c30c-203">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="2c30c-203">$8,109.56</span></span>|  
|<span data-ttu-id="2c30c-204">97205</span><span class="sxs-lookup"><span data-stu-id="2c30c-204">97205</span></span>|<span data-ttu-id="2c30c-205">$30,968.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-205">$30,968.25</span></span>|<span data-ttu-id="2c30c-206">$419.46</span><span class="sxs-lookup"><span data-stu-id="2c30c-206">$419.46</span></span>|<span data-ttu-id="2c30c-207">$4,996.25</span><span class="sxs-lookup"><span data-stu-id="2c30c-207">$4,996.25</span></span>|<span data-ttu-id="2c30c-208">$17,442.97</span><span class="sxs-lookup"><span data-stu-id="2c30c-208">$17,442.97</span></span>|<span data-ttu-id="2c30c-209">$8,109.56</span><span class="sxs-lookup"><span data-stu-id="2c30c-209">$8,109.56</span></span>|  
|<span data-ttu-id="2c30c-210">Washington</span><span class="sxs-lookup"><span data-stu-id="2c30c-210">Washington</span></span>|<span data-ttu-id="2c30c-211">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="2c30c-211">$204,203.37</span></span>|<span data-ttu-id="2c30c-212">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-212">(null)</span></span>|<span data-ttu-id="2c30c-213">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-213">(null)</span></span>|<span data-ttu-id="2c30c-214">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="2c30c-214">$114,345.85</span></span>|<span data-ttu-id="2c30c-215">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="2c30c-215">$89,857.52</span></span>|  
|<span data-ttu-id="2c30c-216">Spokane</span><span class="sxs-lookup"><span data-stu-id="2c30c-216">Spokane</span></span>|<span data-ttu-id="2c30c-217">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="2c30c-217">$204,203.37</span></span>|<span data-ttu-id="2c30c-218">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-218">(null)</span></span>|<span data-ttu-id="2c30c-219">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-219">(null)</span></span>|<span data-ttu-id="2c30c-220">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="2c30c-220">$114,345.85</span></span>|<span data-ttu-id="2c30c-221">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="2c30c-221">$89,857.52</span></span>|  
|<span data-ttu-id="2c30c-222">99202</span><span class="sxs-lookup"><span data-stu-id="2c30c-222">99202</span></span>|<span data-ttu-id="2c30c-223">$204,203.37</span><span class="sxs-lookup"><span data-stu-id="2c30c-223">$204,203.37</span></span>|<span data-ttu-id="2c30c-224">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-224">(null)</span></span>|<span data-ttu-id="2c30c-225">(Null)</span><span class="sxs-lookup"><span data-stu-id="2c30c-225">(null)</span></span>|<span data-ttu-id="2c30c-226">$114,345.85</span><span class="sxs-lookup"><span data-stu-id="2c30c-226">$114,345.85</span></span>|<span data-ttu-id="2c30c-227">$89,857.52</span><span class="sxs-lookup"><span data-stu-id="2c30c-227">$89,857.52</span></span>|  
|<span data-ttu-id="2c30c-228">Seattle Metro Agg</span><span class="sxs-lookup"><span data-stu-id="2c30c-228">Seattle Metro Agg</span></span>|<span data-ttu-id="2c30c-229">$2,383,545.69</span><span class="sxs-lookup"><span data-stu-id="2c30c-229">$2,383,545.69</span></span>|<span data-ttu-id="2c30c-230">$291,248.93</span><span class="sxs-lookup"><span data-stu-id="2c30c-230">$291,248.93</span></span>|<span data-ttu-id="2c30c-231">$763,557.02</span><span class="sxs-lookup"><span data-stu-id="2c30c-231">$763,557.02</span></span>|<span data-ttu-id="2c30c-232">$915,832.36</span><span class="sxs-lookup"><span data-stu-id="2c30c-232">$915,832.36</span></span>|<span data-ttu-id="2c30c-233">$412,907.37</span><span class="sxs-lookup"><span data-stu-id="2c30c-233">$412,907.37</span></span>|  
  
 <span data-ttu-id="2c30c-234">在以上的結果中，[All Geographies]、[United States]、[Oregon] 和 [Washington] 的彙總值來自 &[Portland]&[OR] 和 &[Spokane]&[WA] 的下階彙總。</span><span class="sxs-lookup"><span data-stu-id="2c30c-234">In the above results the aggregated values for [All Geographies], [United States], [Oregon] and [Washington] come from aggregating over the descendants of &[Portland]&[OR] and &[Spokane]&[WA].</span></span> <span data-ttu-id="2c30c-235">沒有任何值來自導出成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-235">Nothing comes from the calculated member.</span></span>  
  
### <a name="remarks"></a><span data-ttu-id="2c30c-236">備註</span><span class="sxs-lookup"><span data-stu-id="2c30c-236">Remarks</span></span>  
 <span data-ttu-id="2c30c-237">子選擇或 Subcube 運算式中只允許使用全域或工作階段導出成員。</span><span class="sxs-lookup"><span data-stu-id="2c30c-237">Only global or session calculated members are allowed in the subselect or subcube expressions.</span></span> <span data-ttu-id="2c30c-238">如果 MDX 運算式中擁有查詢導出成員，在評估子選擇或 Subcube 運算式時就會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c30c-238">Having query calculated members in the MDX expression will raise an error when the subselect or subcube expression is evaluated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c30c-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c30c-239">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 <span data-ttu-id="2c30c-240">[查詢中的子選擇](subselects-in-queries.md) </span><span class="sxs-lookup"><span data-stu-id="2c30c-240">[Subselects in Queries](subselects-in-queries.md) </span></span>  
 [<span data-ttu-id="2c30c-241">支援的 XMLA 屬性 &#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="2c30c-241">Supported XMLA Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)  
  
  
