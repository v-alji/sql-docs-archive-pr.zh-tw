---
title: 將分割區配量屬性設定 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 08/05/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], data slices
- data slices [Analysis Services]
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
author: minewiskan
ms.author: owend
ms.openlocfilehash: f42c4536b99ba3fecf9b947942b881a3be72784f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598018"
---
# <a name="set-the-partition-slice-property-analysis-services"></a><span data-ttu-id="4f120-102">設定 Partition Slice 屬性 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="4f120-102">Set the Partition Slice Property (Analysis Services)</span></span>
  <span data-ttu-id="4f120-103">資料配量是協助將查詢導向到適當之分割區資料的重要最佳化功能。</span><span class="sxs-lookup"><span data-stu-id="4f120-103">A data slice is an important optimization feature that helps direct queries to the data of the appropriate partitions.</span></span> <span data-ttu-id="4f120-104">明確設定 Slice 屬性可提升查詢效能，方法是覆寫 MOLAP and HOLAP 分割區所產生的預設配量。</span><span class="sxs-lookup"><span data-stu-id="4f120-104">Explicitly setting the Slice property can improve query performance by overriding default slices generated for MOLAP and HOLAP partitions.</span></span> <span data-ttu-id="4f120-105">此外，Slice 屬性可在處理分割區時，提供額外的驗證檢查。</span><span class="sxs-lookup"><span data-stu-id="4f120-105">Additionally, the Slice property provides an extra validation check when processing the partition.</span></span>  
  
 <span data-ttu-id="4f120-106">您可以在建立分割區之後但在處理分割區之前，使用 Slice 屬性指定資料配量。</span><span class="sxs-lookup"><span data-stu-id="4f120-106">You can specify a data slice after you create a partition, but before processing it, using the Slice property.</span></span> <span data-ttu-id="4f120-107">在 [資料分割] 索引標籤上，展開量值群組，然後以滑鼠右鍵按一下資料分割並選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4f120-107">On the Partitions tab, expand a measure group, right-click a partition, and select **Properties**.</span></span>  
  
## <a name="defining-a-slice"></a><span data-ttu-id="4f120-108">定義配量</span><span class="sxs-lookup"><span data-stu-id="4f120-108">Defining a Slice</span></span>  
 <span data-ttu-id="4f120-109">Slice 屬性的有效值為 MDX 成員、集合或 Tuple。</span><span class="sxs-lookup"><span data-stu-id="4f120-109">Valid values for a slice property are an MDX member, set, or tuple.</span></span> <span data-ttu-id="4f120-110">下列範例說明有效的配量語法：</span><span class="sxs-lookup"><span data-stu-id="4f120-110">The following examples illustrate valid slice syntax:</span></span>  
  
|<span data-ttu-id="4f120-111">配量</span><span class="sxs-lookup"><span data-stu-id="4f120-111">Slice</span></span>|<span data-ttu-id="4f120-112">成員、集合或 Tuple</span><span class="sxs-lookup"><span data-stu-id="4f120-112">Member, set or tuple</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="4f120-113">[Date].[Calendar].[Calendar Year].&[2010]</span><span class="sxs-lookup"><span data-stu-id="4f120-113">[Date].[Calendar].[Calendar Year].&[2010]</span></span>|<span data-ttu-id="4f120-114">在分割區上指定此配量，以包含 2010 年的事實 (假設模型包含日曆年度階層的日期維度，其中 2010 是成員)。</span><span class="sxs-lookup"><span data-stu-id="4f120-114">Specify this slice on a partition containing facts from year 2010 (assuming the model includes a Date dimension with Calendar Year hierarchy, where 2010 is a member).</span></span> <span data-ttu-id="4f120-115">雖然分割區來源 WHERE 子句或資料表可能已依 2010 篩選，指定配量可在處理期間提供額外檢查，並在查詢執行期間提供更鎖定目標的掃描。</span><span class="sxs-lookup"><span data-stu-id="4f120-115">Although the partition source WHERE clause or table might already filter by 2010, specifying the Slice provides an additional check during processing, as well as more targeted scans during query execution.</span></span>|  
|<span data-ttu-id="4f120-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span><span class="sxs-lookup"><span data-stu-id="4f120-116">{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }</span></span>|<span data-ttu-id="4f120-117">在分割區上指定此配量，以包含銷售領域資訊的事實。</span><span class="sxs-lookup"><span data-stu-id="4f120-117">Specify this slice on a partition containing facts that include sales territory information.</span></span> <span data-ttu-id="4f120-118">配量可以是由兩個或多個成員組成的 MDX 集合。</span><span class="sxs-lookup"><span data-stu-id="4f120-118">A slice can be an MDX set consisting of two or more members.</span></span>|  
|<span data-ttu-id="4f120-119">[Measures].[Sales Amount Quota] > '5000'</span><span class="sxs-lookup"><span data-stu-id="4f120-119">[Measures].[Sales Amount Quota] > '5000'</span></span>|<span data-ttu-id="4f120-120">此配量顯示 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4f120-120">This slice shows an MDX expression.</span></span>|  
  
 <span data-ttu-id="4f120-121">分割區的資料配量應該儘量反映分割區中的資料。</span><span class="sxs-lookup"><span data-stu-id="4f120-121">A data slice of a partition should reflect, as closely as possible, the data in the partition.</span></span> <span data-ttu-id="4f120-122">例如，若分割區限制為 2012 資料，則分割區的資料配量應該指定 Time 維度的 2012 成員。</span><span class="sxs-lookup"><span data-stu-id="4f120-122">For example, if a partition is limited to 2012 data, the partition's data slice should specify the 2012 member of the Time dimension.</span></span> <span data-ttu-id="4f120-123">您不一定能夠指定會反映分割區確切內容的資料配量。</span><span class="sxs-lookup"><span data-stu-id="4f120-123">It is not always possible to specify a data slice that reflects the exact contents of a partition.</span></span> <span data-ttu-id="4f120-124">例如，若分割區只包含 1 月和 2 月的資料，但 Time 維度的層級為年、季和月，則分割區精靈無法同時選取 1 月和 2 月的成員。</span><span class="sxs-lookup"><span data-stu-id="4f120-124">For example, if a partition contains data for only January and February, but the levels of the Time dimension are Year, Quarter, and Month, the Partition Wizard cannot select both the January and February members.</span></span> <span data-ttu-id="4f120-125">在此情況下，請選取能反映分割區內容之成員的父系。</span><span class="sxs-lookup"><span data-stu-id="4f120-125">In such cases, select the parent of the members that reflect the partition's contents.</span></span> <span data-ttu-id="4f120-126">在這個範例中，請選取第 1 季。</span><span class="sxs-lookup"><span data-stu-id="4f120-126">In this example, select Quarter 1.</span></span>  
  
 <span data-ttu-id="4f120-127">如需資料配量優點的說明，請參閱＜ [在 SSAS Cube 分割區上設定配量](https://go.microsoft.com/fwlink/?LinkId=317783)＞。</span><span class="sxs-lookup"><span data-stu-id="4f120-127">For an explanation of data slice benefits, see [Set the Slice on your SSAS Cube Partition](https://go.microsoft.com/fwlink/?LinkId=317783).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4f120-128">請注意，資料分割的 Slice 屬性不支援動態多維度運算式 (MDX) 函數 (例如 [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) 或 [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function))。</span><span class="sxs-lookup"><span data-stu-id="4f120-128">Note that dynamic MDX functions (such as [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) or [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) are not supported in the Slice property for partitions.</span></span> <span data-ttu-id="4f120-129">您必須使用明確的 Tuple 或成員參考來定義配量。</span><span class="sxs-lookup"><span data-stu-id="4f120-129">You must define the slice by using explicit tuples or member references.</span></span>  
>   
>  <span data-ttu-id="4f120-130">例如，您必須依特定年份列舉每個成員，而不是使用[： &#40;範圍&#41; &#40;MDX&#41;](/sql/mdx/range-mdx)函數來定義範圍。</span><span class="sxs-lookup"><span data-stu-id="4f120-130">For example, rather than using the [: &#40;Range&#41; &#40;MDX&#41;](/sql/mdx/range-mdx) function to define a range, you would need to enumerate each member by the specific years.</span></span>  
>   
>  <span data-ttu-id="4f120-131">如果您需要定義複雜的配量，我們建議您使用 XMLA Alter 指令碼在配量中定義 Tuple。</span><span class="sxs-lookup"><span data-stu-id="4f120-131">If you need to define a complex slice, we recommend that you define the tuples in the slice by using an XMLA Alter script.</span></span> <span data-ttu-id="4f120-132">然後在處理資料分割區之前，您可以使用 ascmd 命令列工具或 SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) 工作立即執行該指令碼並建立指定集合的成員。</span><span class="sxs-lookup"><span data-stu-id="4f120-132">Then, you can use either the ascmd command-line tool or the SSIS [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) task to run the script and create the specified set of members immediately before you process the partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f120-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f120-133">See Also</span></span>  
 [<span data-ttu-id="4f120-134">建立及管理本機資料分割 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4f120-134">Create and Manage a Local Partition &#40;Analysis Services&#41;</span></span>](create-and-manage-a-local-partition-analysis-services.md)  
  
  
