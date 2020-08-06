---
title: DataSources 和 DataSets 集合參考 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f951a4aa-da55-4e43-8579-4a5d4480d11f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 560a42daf4d4580adde5b6100fe23f2c646fff08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599377"
---
# <a name="datasources-and-datasets-collection-references-report-builder-and-ssrs"></a><span data-ttu-id="0d08b-102">DataSources 和 DataSets 集合參考 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="0d08b-102">DataSources and DataSets Collection References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0d08b-103">`DataSources` 集合代表報表中使用的所有資料來源。</span><span class="sxs-lookup"><span data-stu-id="0d08b-103">The `DataSources` collection represents all the data sources used in a report.</span></span> <span data-ttu-id="0d08b-104">同樣地，`DataSets` 集合則代表報表中所有資料來源的所有資料集。</span><span class="sxs-lookup"><span data-stu-id="0d08b-104">Similarly, the `DataSets` collection represents all the datasets for all the data sources in a report.</span></span> <span data-ttu-id="0d08b-105">請使用 [報表資料]  窗格以階層的方式檢視報表資料集 (排列在所參考資料來源的下方)。</span><span class="sxs-lookup"><span data-stu-id="0d08b-105">Use the **Report Data** pane for a hierarchical view of report datasets organized under the data source they reference.</span></span> <span data-ttu-id="0d08b-106">如果加入這些集合的參考，就不會在預覽報表時看到值。</span><span class="sxs-lookup"><span data-stu-id="0d08b-106">If you include references to these collections, you will not see values when previewing your report.</span></span> <span data-ttu-id="0d08b-107">只有發行報表至報表伺服器後，才可以使用這些集合。</span><span class="sxs-lookup"><span data-stu-id="0d08b-107">These collections are only available after the report has been published to a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="datasources"></a><span data-ttu-id="0d08b-108">DataSources</span><span class="sxs-lookup"><span data-stu-id="0d08b-108">DataSources</span></span>  
 <span data-ttu-id="0d08b-109">`DataSources` 集合代表已發行報表定義中參考的資料來源。</span><span class="sxs-lookup"><span data-stu-id="0d08b-109">The `DataSources` collection represents the data sources referenced in a published report definition.</span></span> <span data-ttu-id="0d08b-110">您可以選擇在報表中加入這項資訊，以記錄報表資料的來源。</span><span class="sxs-lookup"><span data-stu-id="0d08b-110">You may choose to include this information in your report to document the source of the report data.</span></span> <span data-ttu-id="0d08b-111">這個集合在 [預覽]  模式中無法使用。</span><span class="sxs-lookup"><span data-stu-id="0d08b-111">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="0d08b-112">下表描述 `DataSources` 集合內的變數。</span><span class="sxs-lookup"><span data-stu-id="0d08b-112">The following table describes the variables within the `DataSources` collection.</span></span>  
  
|<span data-ttu-id="0d08b-113">**變數**</span><span class="sxs-lookup"><span data-stu-id="0d08b-113">**Variable**</span></span>|`Type`|<span data-ttu-id="0d08b-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="0d08b-114">**Description**</span></span>|  
|------------------|--------------|---------------------|  
|`DataSourceReference`|`String`|<span data-ttu-id="0d08b-115">報表伺服器上資料來源定義的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="0d08b-115">The full path of the data source definition on the report server.</span></span> <span data-ttu-id="0d08b-116">例如，您可以包含報表用來做為報表記錄一部分的所有資料來源的清單。</span><span class="sxs-lookup"><span data-stu-id="0d08b-116">For example, you might include a list of all the data sources a report used as part of a report history.</span></span> <span data-ttu-id="0d08b-117">以下範例將示範名為 AdventureWorks2012 的資料來源完整路徑：</span><span class="sxs-lookup"><span data-stu-id="0d08b-117">The following example shows the full path for the data source named AdventureWorks2012:</span></span><br /><br /> <span data-ttu-id="0d08b-118">`/DataSources/AdventureWorks2012`.</span><span class="sxs-lookup"><span data-stu-id="0d08b-118">`/DataSources/AdventureWorks2012`.</span></span>|  
|`Type`|`String`|<span data-ttu-id="0d08b-119">資料來源的資料提供者類型。</span><span class="sxs-lookup"><span data-stu-id="0d08b-119">The type of data provider for the data source.</span></span> <span data-ttu-id="0d08b-120">例如： `SQL` 。</span><span class="sxs-lookup"><span data-stu-id="0d08b-120">For example, `SQL`.</span></span>|  
  
## <a name="datasets"></a><span data-ttu-id="0d08b-121">DataSets</span><span class="sxs-lookup"><span data-stu-id="0d08b-121">DataSets</span></span>  
 <span data-ttu-id="0d08b-122">`DataSets` 集合代表報表定義中參考的資料集。</span><span class="sxs-lookup"><span data-stu-id="0d08b-122">The `DataSets` collection represents the datasets referenced in a report definition.</span></span> <span data-ttu-id="0d08b-123">您可以選擇將查詢加入報表的文字方塊中，這樣如果使用者想要知道報表中到底有什麼資料，就可以看到原始的命令文字。</span><span class="sxs-lookup"><span data-stu-id="0d08b-123">You may choose to include the query in the report in a text box, so a user interested in exactly which data is in the report can see the original command text.</span></span> <span data-ttu-id="0d08b-124">這個集合在 [預覽]\*\*\*\* 模式中無法使用。</span><span class="sxs-lookup"><span data-stu-id="0d08b-124">This collection is not available in **Preview** mode.</span></span> <span data-ttu-id="0d08b-125">下表描述 `DataSets` 集合的成員。</span><span class="sxs-lookup"><span data-stu-id="0d08b-125">The following table describes the members of the `DataSets` collection.</span></span>  
  
|<span data-ttu-id="0d08b-126">**成員**</span><span class="sxs-lookup"><span data-stu-id="0d08b-126">**Member**</span></span>|`Type`|<span data-ttu-id="0d08b-127">**說明**</span><span class="sxs-lookup"><span data-stu-id="0d08b-127">**Description**</span></span>|  
|----------------|--------------|---------------------|  
|`CommandText`|`String`|<span data-ttu-id="0d08b-128">針對資料庫資料來源，此查詢是用來擷取資料來源中的資料。</span><span class="sxs-lookup"><span data-stu-id="0d08b-128">For database data sources, this is the query used to retrieve data from the data source.</span></span> <span data-ttu-id="0d08b-129">如果查詢是運算式，則此為評估運算式。</span><span class="sxs-lookup"><span data-stu-id="0d08b-129">If the query is an expression, this is the evaluated expression.</span></span>|  
|`RewrittenCommandText`|`String`|<span data-ttu-id="0d08b-130">資料提供者的擴充 CommandText 值。</span><span class="sxs-lookup"><span data-stu-id="0d08b-130">The data provider's expanded CommandText value.</span></span> <span data-ttu-id="0d08b-131">此值通常用於含有對應至報表參數之查詢參數的報表。</span><span class="sxs-lookup"><span data-stu-id="0d08b-131">This is typically used for reports with query parameters that are mapped to report parameters.</span></span> <span data-ttu-id="0d08b-132">當命令文字參數參考擴充至針對已對應報表參數所選取的常數值時，資料提供者會設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="0d08b-132">The data provider sets this property when expanding the command text parameter references into the constant values selected for the mapped report parameters.</span></span>|  
  
### <a name="using-query-expressions"></a><span data-ttu-id="0d08b-133">使用查詢運算式</span><span class="sxs-lookup"><span data-stu-id="0d08b-133">Using Query Expressions</span></span>  
 <span data-ttu-id="0d08b-134">您可以利用運算式來定義資料集內包含的查詢。</span><span class="sxs-lookup"><span data-stu-id="0d08b-134">You can use expressions to define the query that is contained in a dataset.</span></span> <span data-ttu-id="0d08b-135">您可以使用此功能來設計報表，在此報表中會根據使用者的輸入、其他資料集內的資料，或其他變數來變更查詢。</span><span class="sxs-lookup"><span data-stu-id="0d08b-135">You can use this feature to design reports in which the query changes based on input from the user, data in other datasets, or other variables.</span></span> <span data-ttu-id="0d08b-136">如需查詢的詳細資訊，請參閱[報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="0d08b-136">For more information about queries, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d08b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d08b-137">See Also</span></span>  
 <span data-ttu-id="0d08b-138">[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0d08b-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0d08b-139">運算式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0d08b-139">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
