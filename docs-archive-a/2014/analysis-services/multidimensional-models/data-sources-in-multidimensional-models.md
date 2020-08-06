---
title: 多維度模型中的資料來源 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- metadata [Analysis Services]
- Analysis Services objects, data sources
- storing data [Analysis Services], data sources
- data sources [Analysis Services], about data sources
- security [Analysis Services], data sources
- data sources [Analysis Services]
- storage [Analysis Services], data sources
ms.assetid: a16469d9-9d53-4e35-9982-fc06327a9d33
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41386c1c7abb0324aa17df24b3c427ca8cbb5615
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599229"
---
# <a name="data-sources-in-multidimensional-models"></a><span data-ttu-id="d752e-102">多維度模型中的資料來源</span><span class="sxs-lookup"><span data-stu-id="d752e-102">Data Sources in Multidimensional Models</span></span>
  <span data-ttu-id="d752e-103">您匯入或載入多維度模型的所有資料都源自於外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="d752e-103">All data that you import or load into a multidimensional model originates from an external data source.</span></span> <span data-ttu-id="d752e-104">一般來說，來源資料來自於針對報表用途所設計的資料倉儲，但是也可能來自於透過中繼者直接或間接存取的任何關聯式資料庫，例如 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="d752e-104">Typically, source data is from a data warehouse designed for reporting purposes, but it could come from any relational database that is accessed directly or indirectly through an intermediary, such as an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span>  
  
 <span data-ttu-id="d752e-105">**中的** 資料來源 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件會指定與外部資料來源的直接連接。</span><span class="sxs-lookup"><span data-stu-id="d752e-105">A **data source** object in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] specifies a direct connection to an external data source.</span></span> <span data-ttu-id="d752e-106">除了實體位置之外，資料來源物件還會指定連接字串、資料提供者、認證，以及控制連接行為的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="d752e-106">In addition to physical location, a data source object specifies the connection string, data provider, credentials, and other properties that control connection behavior.</span></span>  
  
 <span data-ttu-id="d752e-107">在以下的作業期間會使用資料來源物件所提供的資訊：</span><span class="sxs-lookup"><span data-stu-id="d752e-107">Information provided by the data source object is used during the following operations:</span></span>  
  
-   <span data-ttu-id="d752e-108">取得結構描述資訊和其他中繼資料，這些資料用來將資料來源檢視產生到模型中。</span><span class="sxs-lookup"><span data-stu-id="d752e-108">Get schema information and other metadata used to generate data source views into a model.</span></span>  
  
-   <span data-ttu-id="d752e-109">在處理期間查詢資料或將資料載入模型內。</span><span class="sxs-lookup"><span data-stu-id="d752e-109">Query or load data into a model during processing.</span></span>  
  
-   <span data-ttu-id="d752e-110">對多維度或使用 ROLAP 儲存模式的資料採礦模型執行查詢。</span><span class="sxs-lookup"><span data-stu-id="d752e-110">Run queries against multidimensional or data mining models that use ROLAP storage mode.</span></span>  
  
-   <span data-ttu-id="d752e-111">讀取或寫入遠端資料分割。</span><span class="sxs-lookup"><span data-stu-id="d752e-111">Read or write to remote partitions.</span></span>  
  
-   <span data-ttu-id="d752e-112">連接到連結的物件，以及從目標同步到來源。</span><span class="sxs-lookup"><span data-stu-id="d752e-112">Connect to linked objects, as well as synchronize from target to source.</span></span>  
  
-   <span data-ttu-id="d752e-113">執行更新儲存在關聯式資料庫中之事實資料表資料的回寫作業。</span><span class="sxs-lookup"><span data-stu-id="d752e-113">Perform write back operations that update fact table data stored in a relational database.</span></span>  
  
 <span data-ttu-id="d752e-114">由下而上建立多維度模型時，一開始會建立資料來源物件，然後使用該資料來源物件產生下一個物件： **資料來源檢視**。</span><span class="sxs-lookup"><span data-stu-id="d752e-114">When building a multidimensional model from the bottom up, you start by creating the data source object, and then use it to generate the next object, a **data source view**.</span></span> <span data-ttu-id="d752e-115">資料來源檢視是模型中的資料抽象層，</span><span class="sxs-lookup"><span data-stu-id="d752e-115">A data source view is the data abstraction layer in the model.</span></span> <span data-ttu-id="d752e-116">通常會在資料來源物件之後建立，並使用來源資料庫的結構描述做為基礎。</span><span class="sxs-lookup"><span data-stu-id="d752e-116">It is typically created after the data source object, using the schema of the source database as the basis.</span></span> <span data-ttu-id="d752e-117">不過，您可以選擇其他方式來建立模型，包括從 Cube 和維度開始，然後產生最能支援您的設計之結構描述。</span><span class="sxs-lookup"><span data-stu-id="d752e-117">However, you can choose other ways to build a model, including starting with cubes and dimensions, and generating the schema that best supports your design.</span></span>  
  
 <span data-ttu-id="d752e-118">不論您的建立方式為何，每個模型至少都需要一個指定來源資料連接的資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="d752e-118">Regardless of how you build it, each model requires at least one data source object that specifies a connection to source data.</span></span> <span data-ttu-id="d752e-119">您可以在單一模型中建立多個資料來源物件，使用來自不同來源的資料，或針對特定物件改變連接屬性。</span><span class="sxs-lookup"><span data-stu-id="d752e-119">You can create multiple data source objects in a single model to use data from different sources or vary connection properties for specific objects.</span></span>  
  
 <span data-ttu-id="d752e-120">您可以將資料來源物件與模型中的其他物件分開管理。</span><span class="sxs-lookup"><span data-stu-id="d752e-120">Data source objects can be managed independently of other objects in your model.</span></span> <span data-ttu-id="d752e-121">建立資料來源之後，您可以在稍後變更其屬性，然後對模型進行前置處理以確保正確擷取資料。</span><span class="sxs-lookup"><span data-stu-id="d752e-121">After you create a data source, you can change its properties later, and then preprocess the model to ensure the data is retrieved correctly.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="d752e-122">相關主題和工作</span><span class="sxs-lookup"><span data-stu-id="d752e-122">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="d752e-123">主題</span><span class="sxs-lookup"><span data-stu-id="d752e-123">Topic</span></span>|<span data-ttu-id="d752e-124">描述</span><span class="sxs-lookup"><span data-stu-id="d752e-124">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d752e-125">&#40;SSAS 多維度&#41;支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="d752e-125">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)|<span data-ttu-id="d752e-126">描述可在多維度模型中使用的資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="d752e-126">Describes the types of data sources that can be used in a multidimensional model.</span></span>|  
|[<span data-ttu-id="d752e-127">建立資料來源 &#40;SSAS 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="d752e-127">Create a Data Source &#40;SSAS Multidimensional&#41;</span></span>](create-a-data-source-ssas-multidimensional.md)|<span data-ttu-id="d752e-128">說明如何將資料來源物件加入至多維度模型。</span><span class="sxs-lookup"><span data-stu-id="d752e-128">Explains how to add a data source object to a multidimensional model.</span></span>|  
|[<span data-ttu-id="d752e-129">在方案總管中刪除資料來源 &#40;SSAS 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="d752e-129">Delete a Data Source in Solution Explorer &#40;SSAS Multidimensional&#41;</span></span>](delete-a-data-source-in-solution-explorer-ssas-multidimensional.md)|<span data-ttu-id="d752e-130">使用此程序從多維度模型中刪除資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="d752e-130">Use this procedure to delete a data source object from a multidimensional model.</span></span>|  
|[<span data-ttu-id="d752e-131">設定資料來源屬性 &#40;SSAS 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="d752e-131">Set Data Source Properties &#40;SSAS Multidimensional&#41;</span></span>](set-data-source-properties-ssas-multidimensional.md)|<span data-ttu-id="d752e-132">描述每個屬性，並說明如何設定每個屬性。</span><span class="sxs-lookup"><span data-stu-id="d752e-132">Describes each property and explains how to set each one.</span></span>|  
|[<span data-ttu-id="d752e-133">設定模擬選項 &#40;SSAS - 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="d752e-133">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](set-impersonation-options-ssas-multidimensional.md)|<span data-ttu-id="d752e-134">說明如何設定 [模擬資訊] 對話方塊中的選項。</span><span class="sxs-lookup"><span data-stu-id="d752e-134">Explains how to configure options in the Impersonation Information dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d752e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d752e-135">See Also</span></span>  
 <span data-ttu-id="d752e-136">[資料庫物件 &#40;Analysis Services 多維度資料&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d752e-136">[Database Objects &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/database-objects-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d752e-137">[邏輯架構 &#40;Analysis Services-多維度資料&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="d752e-137">[Logical Architecture &#40;Analysis Services - Multidimensional Data&#41;](olap-logical/understanding-microsoft-olap-logical-architecture.md) </span></span>  
 <span data-ttu-id="d752e-138">[多維度模型中的資料來源視圖](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="d752e-138">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="d752e-139">資料來源和繫結 &#40;SSAS 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="d752e-139">Data Sources and Bindings &#40;SSAS Multidimensional&#41;</span></span>](data-sources-and-bindings-ssas-multidimensional.md)  
  
  
