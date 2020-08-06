---
title: 使用 Microsoft 一般內容樹狀檢視器來流覽模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining model content, viewing
ms.assetid: 4a5f7c51-c704-4214-b05d-21cf735e6d96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 90d47262a09060a11020e50b3724753799d2d188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606527"
---
# <a name="browse-a-model-using-the-microsoft-generic-content-tree-viewer"></a><span data-ttu-id="db43c-102">使用 Microsoft 一般內容樹狀檢視器瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="db43c-102">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>
  <span data-ttu-id="db43c-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般採礦模型內容檢視器能針對採礦演算法所找到的模式提供詳細的資訊，也可以用來存取在分析程序期間所產生的各種統計資料。</span><span class="sxs-lookup"><span data-stu-id="db43c-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Mining Model Content Viewer provides detailed information about the patterns found by the mining algorithm, and also provides access to various statistics generated during the analysis process.</span></span> <span data-ttu-id="db43c-104">資訊的量及類型是根據使用的演算法而定，但可能包含下列類別：</span><span class="sxs-lookup"><span data-stu-id="db43c-104">The amount and type of information depends on the algorithm that was used, but can include the following categories:</span></span>  
  
-   <span data-ttu-id="db43c-105">資料區段和它們的特性。</span><span class="sxs-lookup"><span data-stu-id="db43c-105">Segments of data, and their characteristics.</span></span>  
  
-   <span data-ttu-id="db43c-106">有關每個群組或整組資料的描述性統計資料。</span><span class="sxs-lookup"><span data-stu-id="db43c-106">Descriptive statistics about each group or about the whole set of data.</span></span>  
  
-   <span data-ttu-id="db43c-107">樹狀結構中的分支或子節點數。</span><span class="sxs-lookup"><span data-stu-id="db43c-107">The number of branches or child nodes in a tree.</span></span>  
  
-   <span data-ttu-id="db43c-108">群集或整組資料的計算，例如變異數和平均。</span><span class="sxs-lookup"><span data-stu-id="db43c-108">Calculations, such as variance and mean, for a cluster or a whole set of data.</span></span>  
  
 <span data-ttu-id="db43c-109">檢視這項資訊有助於更了解分析的結果。</span><span class="sxs-lookup"><span data-stu-id="db43c-109">Viewing this information can help you better understand the results of your analysis.</span></span> <span data-ttu-id="db43c-110">您也可以識別微調的方法，然後重新培訓模型，</span><span class="sxs-lookup"><span data-stu-id="db43c-110">You can also identify ways to fine-tune, and then retrain, your model.</span></span> <span data-ttu-id="db43c-111">或者決定使用不同的演算法進行重新培訓。</span><span class="sxs-lookup"><span data-stu-id="db43c-111">Or, you might decide to retrain by using a different algorithm.</span></span>  
  
## <a name="viewing-mining-model-content"></a><span data-ttu-id="db43c-112">檢視採礦模型內容</span><span class="sxs-lookup"><span data-stu-id="db43c-112">Viewing Mining Model Content</span></span>  
 <span data-ttu-id="db43c-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容檢視器會從採礦模型的 *「內容結構描述資料列集」* (Content Schema Rowset) 顯示資料行、規則、屬性 (Property)、屬性 (Attribute)、節點和其他內容。</span><span class="sxs-lookup"><span data-stu-id="db43c-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Viewer displays the columns, rules, properties, attributes, nodes, and other content from the *content schema rowset* of the mining model.</span></span> <span data-ttu-id="db43c-114">內容結構描述資料列集是一般性架構，用來展示有關資料採礦模型內容的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="db43c-114">The content schema rowset is a generic framework for presenting detailed information about the content of a data mining model.</span></span>  
  
 <span data-ttu-id="db43c-115">此詳細資訊包含在一個 HTML 資料表中，該資料表將模型中的模式、叢集或樹狀表示為節點。</span><span class="sxs-lookup"><span data-stu-id="db43c-115">This detailed information is contained in an HTML table that represents the patterns, clusters, or trees in the model as nodes.</span></span> <span data-ttu-id="db43c-116">您可以按一下各節點，然後將其展開以查看詳細資料，例如公式或數值屬性的相異值計數。</span><span class="sxs-lookup"><span data-stu-id="db43c-116">You can click on each node and expand it to see more detail, such as the formulas or the count of distinct values for a numeric attribute.</span></span> <span data-ttu-id="db43c-117">您也可以瀏覽節點之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="db43c-117">You can also explore the child-parent relationships among the nodes.</span></span>  
  
 <span data-ttu-id="db43c-118">如需採礦模型內容中所使用術語之一般意義的詳細資訊，請參閱[採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="db43c-118">For more information about the general meaning of the terms used in the mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span> <span data-ttu-id="db43c-119">這個主題也包含連結，提供關於特定類型模型之採礦模型內容的資訊。</span><span class="sxs-lookup"><span data-stu-id="db43c-119">The topic also contains links to information about mining model content for specific types of models.</span></span> <span data-ttu-id="db43c-120">每種類型的採礦模型都包含演算法專屬的資訊以及在資料中找到的模式，因此，建議您查閱每個模型類型的技術參考主題，以了解每個模型類型的完整資訊。</span><span class="sxs-lookup"><span data-stu-id="db43c-120">Each type of mining model contains information that is highly specific to the algorithm and the patterns found in the data, so we recommend that you consult the technical reference topic for each model type in order to fully understand each model type.</span></span>  
  
## <a name="querying-mining-model-content"></a><span data-ttu-id="db43c-121">查詢採礦模型內容</span><span class="sxs-lookup"><span data-stu-id="db43c-121">Querying Mining Model Content</span></span>  
 <span data-ttu-id="db43c-122">由 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器所提供的相同資訊，也可藉由查詢採礦模型而提供。</span><span class="sxs-lookup"><span data-stu-id="db43c-122">The same information that is provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer is also available by querying the mining model.</span></span> <span data-ttu-id="db43c-123">您可以藉由使用資料採礦延伸模組 (DMX) 陳述式來針對採礦模型內容建立查詢。</span><span class="sxs-lookup"><span data-stu-id="db43c-123">You can create queries against mining model content by using Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="db43c-124">例如，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，您可以執行下列 DMX 陳述式來執行內容查詢：</span><span class="sxs-lookup"><span data-stu-id="db43c-124">For example, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can run a content query by executing the following DMX statement:</span></span>  
  
```  
SELECT * FROM [<mining model name>].CONTENT  
```  
  
 <span data-ttu-id="db43c-125">如需詳細資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="db43c-125">For more information, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db43c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db43c-126">See Also</span></span>  
 <span data-ttu-id="db43c-127">[Microsoft 一般內容樹狀檢視器 &#40;資料採礦&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="db43c-127">[Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](../microsoft-generic-content-tree-viewer-data-mining.md) </span></span>  
 [<span data-ttu-id="db43c-128">資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="db43c-128">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
  
