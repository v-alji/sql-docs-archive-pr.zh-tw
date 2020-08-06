---
title: 查詢用來建立採礦模型的參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
author: minewiskan
ms.author: owend
ms.openlocfilehash: a3802a0d70579f613accbe6abd310da909751b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702158"
---
# <a name="query-the-parameters-used-to-create-a-mining-model"></a><span data-ttu-id="46218-102">查詢用於建立採礦模型的參數</span><span class="sxs-lookup"><span data-stu-id="46218-102">Query the Parameters Used to Create a Mining Model</span></span>
  <span data-ttu-id="46218-103">採礦模型的構成不僅受到定型案例的影響，還會受到在建立模型時所設定參數的影響。</span><span class="sxs-lookup"><span data-stu-id="46218-103">The composition of a mining model is affected not only by the training cases, but by the parameters that were set when the model was created.</span></span> <span data-ttu-id="46218-104">因此，擷取現有模型的參數設定以更加了解模型行為，可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="46218-104">Therefore, you might find it useful to retrieve the parameter settings of an existing model to better understand the behavior of the model.</span></span> <span data-ttu-id="46218-105">擷取參數在記錄該模型的特定版本時也很有用。</span><span class="sxs-lookup"><span data-stu-id="46218-105">Retrieving parameters is also useful when documenting a particular version of that model.</span></span>  
  
 <span data-ttu-id="46218-106">若要尋找建立模型時所用的參數，您可針對其中一個採礦模型結構描述資料列集建立查詢。</span><span class="sxs-lookup"><span data-stu-id="46218-106">To find the parameters that were used when the model was created, you create a query against one of the mining model schema rowsets.</span></span> <span data-ttu-id="46218-107">在 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]中，這些結構描述資料列集已公開為可藉由使用 Transact-SQL 語法而輕鬆查詢的一組系統檢視表。</span><span class="sxs-lookup"><span data-stu-id="46218-107">In [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], these schema rowsets are exposed as a set of system views that you can query easily by using Transact-SQL syntax.</span></span> <span data-ttu-id="46218-108">這項程序描述如何建立查詢，以傳回用來建立指定採礦模型的參數。</span><span class="sxs-lookup"><span data-stu-id="46218-108">This procedure describes how to create a query that returns the parameters that were used to create the specified mining model.</span></span>  
  
### <a name="to-open-a-query-window-for-a-schema-rowset-query"></a><span data-ttu-id="46218-109">開啟結構描述資料列集查詢的查詢視窗</span><span class="sxs-lookup"><span data-stu-id="46218-109">To open a Query window for a schema rowset query</span></span>  
  
1.  <span data-ttu-id="46218-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟包含所要查詢之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="46218-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the model you want to query.</span></span>  
  
2.  <span data-ttu-id="46218-111">以滑鼠右鍵按一下執行個體名稱，選取 [新增查詢]\*\*\*\*，然後選取 [DMX]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46218-111">Right-click the instance name, select **New Query**, and then select **DMX**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46218-112"> 您也可以使用 **[MDX]** 範本針對資料採礦模型建立查詢。</span><span class="sxs-lookup"><span data-stu-id="46218-112">You can also create a query against a data mining model by using the **MDX** template.</span></span>  
  
3.  <span data-ttu-id="46218-113">如果執行個體包含多個資料庫，請從工具列中的 **[可用的資料庫]** 清單選取包含您要查詢之模型的資料庫。</span><span class="sxs-lookup"><span data-stu-id="46218-113">If the instance contains multiple databases, select the database that contains the model you want to query from the **Available Databases** list in the toolbar.</span></span>  
  
### <a name="to-return-model-parameters-for-an-existing-mining-model"></a><span data-ttu-id="46218-114">傳回現有採礦模型的模型參數</span><span class="sxs-lookup"><span data-stu-id="46218-114">To return model parameters for an existing mining model</span></span>  
  
1.  <span data-ttu-id="46218-115">在 DMX 查詢窗格中，輸入或貼上下列文字：</span><span class="sxs-lookup"><span data-stu-id="46218-115">In the DMX query pane, type or paste the following text:</span></span>  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  <span data-ttu-id="46218-116">在 [物件總管] 中，選取所要的採礦模型，然後將它拖曳到 [DMX 查詢] 窗格內的單引號中。</span><span class="sxs-lookup"><span data-stu-id="46218-116">In Object Explorer, select the mining model you want, and then drag it into the DMX Query pane, between the single quotation marks.</span></span>  
  
3.  <span data-ttu-id="46218-117">按 F5, 或按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="46218-117">Press F5, or click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46218-118">範例</span><span class="sxs-lookup"><span data-stu-id="46218-118">Example</span></span>  
 <span data-ttu-id="46218-119">下列程式碼會傳回用來建立您在 [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md)中所建立之採礦模型的參數清單。</span><span class="sxs-lookup"><span data-stu-id="46218-119">The following code returns a list of the parameters that were used to create the mining model that you build in the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="46218-120">這些參數所包含的明確值，會用於伺服器的提供者所提供之採礦服務使用的任何預設值。</span><span class="sxs-lookup"><span data-stu-id="46218-120">These parameters include the explicit values for any defaults used by the mining services available from providers on the server.</span></span>  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 <span data-ttu-id="46218-121">程式碼範例會針對群集模型傳回下列參數：</span><span class="sxs-lookup"><span data-stu-id="46218-121">The code example returns the following parameters for the clustering model:</span></span>  
  
 <span data-ttu-id="46218-122">範例結果：</span><span class="sxs-lookup"><span data-stu-id="46218-122">eExample Results:</span></span>  
  
 <span data-ttu-id="46218-123">MINING_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="46218-123">MINING_PARAMETERS</span></span>  
  
 <span data-ttu-id="46218-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span><span class="sxs-lookup"><span data-stu-id="46218-124">CLUSTER_COUNT=10,CLUSTER_SEED=0,CLUSTERING_METHOD=1,MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_STATES=100,MINIMUM_SUPPORT=1,MODELLING_CARDINALITY=10,SAMPLE_SIZE=50000,STOPPING_TOLERANCE=10</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46218-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46218-125">See Also</span></span>  
 <span data-ttu-id="46218-126">[資料採礦查詢工作和操作說明](data-mining-query-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="46218-126">[Data Mining Query Tasks and How-tos](data-mining-query-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="46218-127">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="46218-127">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
