---
title: 查詢資料採礦架構資料列集 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- data mining [Analysis Services], queries
- mining model content
- data mining [Analysis Services], schema rowsets
- schema rowsets [Analysis Services], retrieving
- data mining [Analysis Services], troubleshooting
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: d60c802256454ee68d04392e685fa4acabf6c12e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598679"
---
# <a name="querying-the-data-mining-schema-rowsets-analysis-services---data-mining"></a><span data-ttu-id="c2b96-102">查詢資料採礦結構描述資料列集 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="c2b96-102">Querying the Data Mining Schema Rowsets (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="c2b96-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，許多現有的 OLE DB 資料採礦結構描述資料列集已經公開成一組系統資料表，而且您可以使用資料採礦延伸模組 (DMX) 陳述式來查詢它們。</span><span class="sxs-lookup"><span data-stu-id="c2b96-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], many of the existing OLE DB data mining schema rowsets are exposed as a set of system tables that you can query by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="c2b96-104">透過針對資料採礦結構描述資料列集建立查詢，您可以識別可用的服務、取得模型和結構之狀態的更新，以及找出模型內容或參數的相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c2b96-104">By creating queries against the data mining schema rowset, you can identify the services that are available, get updates on the status of your models and structures, and find out details about the model content or parameters.</span></span> <span data-ttu-id="c2b96-105">如需資料採礦結構描述資料列集的描述，請參閱＜ [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c2b96-105">For a description of the data mining schema rowsets, see [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c2b96-106">您也可以使用 XMLA 來查詢資料採礦結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="c2b96-106">You can also query the data mining schema rowsets by using XMLA.</span></span> <span data-ttu-id="c2b96-107">如需如何在 SQL Server Management Studio 中執行此動作的詳細資訊，請參閱 [使用 XMLA 建立資料採礦查詢](create-a-data-mining-query-by-using-xmla.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b96-107">For more information about how to do this in SQL Server Management Studio, see [Create a Data Mining Query by Using XMLA](create-a-data-mining-query-by-using-xmla.md).</span></span>  
  
## <a name="list-of-data-mining-schema-rowsets"></a><span data-ttu-id="c2b96-108">資料採礦結構描述資料列集的清單</span><span class="sxs-lookup"><span data-stu-id="c2b96-108">List of Data Mining Schema Rowsets</span></span>  
 <span data-ttu-id="c2b96-109">下表列出可能適用於查詢和監視的資料採礦結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="c2b96-109">The following table lists the data mining schema rowsets that may be useful for querying and monitoring.</span></span>  
  
|<span data-ttu-id="c2b96-110">資料列集名稱</span><span class="sxs-lookup"><span data-stu-id="c2b96-110">Rowset name</span></span>|<span data-ttu-id="c2b96-111">描述</span><span class="sxs-lookup"><span data-stu-id="c2b96-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c2b96-112">DMSCHEMA_MINING_MODELS</span><span class="sxs-lookup"><span data-stu-id="c2b96-112">DMSCHEMA_MINING_MODELS</span></span>|<span data-ttu-id="c2b96-113">列出目前環境中的所有採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c2b96-113">Lists all mining models in the current context.</span></span><br /><br /> <span data-ttu-id="c2b96-114">其中包含的資訊如建立的日期、建立模型所使用的參數，以及定型集的大小。</span><span class="sxs-lookup"><span data-stu-id="c2b96-114">Includes such information as the date created, parameters used to create the model, and the size of the training set.</span></span>|  
|<span data-ttu-id="c2b96-115">DMSCHEMA_MINING_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="c2b96-115">DMSCHEMA_MINING_COLUMNS</span></span>|<span data-ttu-id="c2b96-116">列出目前環境之採礦模型中使用的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="c2b96-116">Lists all columns used in mining models in the current context.</span></span><br /><br /> <span data-ttu-id="c2b96-117">其中的資訊包括採礦結構來源資料行的對應、資料類型、精確度，以及可搭配資料行使用的預測函數。</span><span class="sxs-lookup"><span data-stu-id="c2b96-117">Information includes mapping to mining structure source column, data type, precision, and prediction functions that can be used with the column.</span></span>|  
|<span data-ttu-id="c2b96-118">DMSCHEMA_MINING_STRUCTURES</span><span class="sxs-lookup"><span data-stu-id="c2b96-118">DMSCHEMA_MINING_STRUCTURES</span></span>|<span data-ttu-id="c2b96-119">列出目前環境中的所有採礦結構。</span><span class="sxs-lookup"><span data-stu-id="c2b96-119">Lists all mining structure in the current context.</span></span><br /><br /> <span data-ttu-id="c2b96-120">其中的資訊包括是否擴展結構、上次處理結構的日期，以及針對結構所設定之鑑效組資料的定義 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="c2b96-120">Information includes whether the structure is populated, the date the structure was last processed, and the definition of the holdout data set for the structure, if any.</span></span>|  
|<span data-ttu-id="c2b96-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="c2b96-121">DMSCHEMA_MINING_STRUCTURE_COLUMNS</span></span>|<span data-ttu-id="c2b96-122">列出目前環境之採礦結構中使用的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="c2b96-122">Lists all columns used in mining structures in the current context.</span></span><br /><br /> <span data-ttu-id="c2b96-123">其中的資訊包括內容類型和資料類型、Null 屬性，以及資料行是否包含巢狀資料表資料。</span><span class="sxs-lookup"><span data-stu-id="c2b96-123">Information includes content type and data type, nullability, and whether the column contains nested table data.</span></span>|  
|<span data-ttu-id="c2b96-124">DMSCHEMA_MINING_SERVICES</span><span class="sxs-lookup"><span data-stu-id="c2b96-124">DMSCHEMA_MINING_SERVICES</span></span>|<span data-ttu-id="c2b96-125">列出指定之伺服器所提供的所有採礦服務或演算法。</span><span class="sxs-lookup"><span data-stu-id="c2b96-125">Lists all mining services, or algorithms, that are available on the specified server.</span></span><br /><br /> <span data-ttu-id="c2b96-126">其中的資訊包括支援的模型旗標、輸入類型，以及支援的資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="c2b96-126">Information includes supported modeling flags, input types, and supported data source types.</span></span>|  
|<span data-ttu-id="c2b96-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c2b96-127">DMSCHEMA_MINING_SERVICE_PARAMETERS</span></span>|<span data-ttu-id="c2b96-128">列出目前執行個體所提供之採礦服務的所有參數。</span><span class="sxs-lookup"><span data-stu-id="c2b96-128">Lists all parameters for the mining services that are available on the current instance.</span></span><br /><br /> <span data-ttu-id="c2b96-129">其中的資訊包括每個參數的資料類型、預設值，以及上限與下限。</span><span class="sxs-lookup"><span data-stu-id="c2b96-129">Information includes the data type for each parameter, the default values, and the upper and lower limits.</span></span>|  
|<span data-ttu-id="c2b96-130">DMSCHEMA_MODEL_CONTENT</span><span class="sxs-lookup"><span data-stu-id="c2b96-130">DMSCHEMA_MODEL_CONTENT</span></span>|<span data-ttu-id="c2b96-131">如果模型已經經過處理，傳回模型的內容。</span><span class="sxs-lookup"><span data-stu-id="c2b96-131">Returns the content of the model if the model has been processed.</span></span><br /><br /> <span data-ttu-id="c2b96-132">如需詳細資訊，請參閱[採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b96-132">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>|  
|<span data-ttu-id="c2b96-133">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="c2b96-133">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="c2b96-134">列出 Analysis Services 目前執行個體中的所有資料庫 (目錄)。</span><span class="sxs-lookup"><span data-stu-id="c2b96-134">Lists all databases (catalogs) in the current instance of Analysis Services.</span></span>|  
|<span data-ttu-id="c2b96-135">MDSCHEMA_INPUT_DATASOURCES</span><span class="sxs-lookup"><span data-stu-id="c2b96-135">MDSCHEMA_INPUT_DATASOURCES</span></span>|<span data-ttu-id="c2b96-136">列出 Analysis Services 目前執行個體中的所有資料來源。</span><span class="sxs-lookup"><span data-stu-id="c2b96-136">Lists all data sources in the current instance of Analysis Services.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="c2b96-137">資料表中的清單並不完整，因為該清單中只顯示與疑難排解相關的資料列集。</span><span class="sxs-lookup"><span data-stu-id="c2b96-137">The list in the table is not comprehensive; it shows only those rowsets that may be of most interest for troubleshooting.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c2b96-138">範例</span><span class="sxs-lookup"><span data-stu-id="c2b96-138">Examples</span></span>  
 <span data-ttu-id="c2b96-139">下節會針對資料採礦結構描述資料列集提供查詢的一些範例。</span><span class="sxs-lookup"><span data-stu-id="c2b96-139">The following section provides some examples of queries against the data mining schema rowsets.</span></span>  
  
### <a name="example-1-list-data-mining-services"></a><span data-ttu-id="c2b96-140">範例 1：列出資料採礦服務</span><span class="sxs-lookup"><span data-stu-id="c2b96-140">Example 1: List Data Mining Services</span></span>  
 <span data-ttu-id="c2b96-141">下列查詢會傳回目前伺服器所提供之採礦服務的清單，表示已啟用的演算法。</span><span class="sxs-lookup"><span data-stu-id="c2b96-141">The following query returns a list of the mining services that are available on the current server, meaning the algorithms that are enabled.</span></span> <span data-ttu-id="c2b96-142">針對每個採礦服務提供的資料行包括每個演算法所使用的模型旗標與內容類型、每個服務的 GUID，以及可能已經針對每個服務加入的任何預測限制。</span><span class="sxs-lookup"><span data-stu-id="c2b96-142">The columns provided for each mining service include the modeling flags and content types that can be used by each algorithm, the GUID for each service, and any prediction limits that may have been added for each service.</span></span>  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### <a name="example-2-list-mining-model-parameters"></a><span data-ttu-id="c2b96-143">範例 2：列出採礦模型參數</span><span class="sxs-lookup"><span data-stu-id="c2b96-143">Example 2: List Mining Model Parameters</span></span>  
 <span data-ttu-id="c2b96-144">下列範例會傳回建立特定採礦模型所使用的參數：</span><span class="sxs-lookup"><span data-stu-id="c2b96-144">The following example returns the parameters that were used to create a specific mining model:</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### <a name="example-3-list-all-rowsets"></a><span data-ttu-id="c2b96-145">範例 3：列出所有資料列集</span><span class="sxs-lookup"><span data-stu-id="c2b96-145">Example 3: List All Rowsets</span></span>  
 <span data-ttu-id="c2b96-146">下列範例會傳回目前伺服器所提供之資料列集的完整清單：</span><span class="sxs-lookup"><span data-stu-id="c2b96-146">The following example returns a comprehensive list of the rowsets that are available on the current server:</span></span>  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2b96-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2b96-147">See Also</span></span>  
 [<span data-ttu-id="c2b96-148">疑難排解概念 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="c2b96-148">Troubleshooting Concepts (Analysis Services - Data Mining)</span></span>](https://msdn.microsoft.com/library/cc645881.aspx)  
  
  
