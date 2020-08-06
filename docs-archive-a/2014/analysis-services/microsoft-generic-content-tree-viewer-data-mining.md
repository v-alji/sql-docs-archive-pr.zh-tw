---
title: Microsoft 一般內容樹狀檢視器 (資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0dab06d6af8f2c5af029d9ce831f518faa4067e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707957"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a><span data-ttu-id="05d98-102">Microsoft 一般內容樹狀檢視器 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="05d98-102">Microsoft Generic Content Tree Viewer (Data Mining)</span></span>
  <span data-ttu-id="05d98-103">**[Microsoft 一般內容樹狀檢視器]** 會以標準 HTML 資料表格式來顯示資料採礦模式內容的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="05d98-103">The **Microsoft Generic Content Tree Viewer** displays detailed information about the contents of a data mining mode in a standardized HTML table format.</span></span> <span data-ttu-id="05d98-104">此檢視很有用，因為它會公開模型的基礎結構，以及有關係數、值分佈等項目的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="05d98-104">This view is useful because it exposes the underlying structure of the model, as well details about coefficients, the distribution of values, and much more.</span></span>  
  
 <span data-ttu-id="05d98-105">資料表中顯示的實際內容會依照使用的演算法而變更，可能包含資料行、規則、屬性 (Property)、屬性 (Attribute)、節點和公式。</span><span class="sxs-lookup"><span data-stu-id="05d98-105">The actual content displayed in the table varies depending on the algorithm that was used and might include columns, rules, properties, attributes, nodes, and formulas.</span></span> <span data-ttu-id="05d98-106">如需模型內容以及如何解譯每個模型類型之資訊的詳細資訊，請參閱[採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](data-mining/mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="05d98-106">For more information about model content, and how to interpret the information for each model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="05d98-107">檢視器中顯示的資訊會使用以採礦模型的內容結構描述資料列集為基礎的通用結構。</span><span class="sxs-lookup"><span data-stu-id="05d98-107">The information that is displayed in the viewer uses a common structure that is based on the content schema rowset for mining models.</span></span> <span data-ttu-id="05d98-108">內容結構描述資料列集是一般架構，可用來儲存資料採礦模型的模式、統計資料和其他內容。</span><span class="sxs-lookup"><span data-stu-id="05d98-108">The content schema rowset is a generic framework for storing patterns, statistics, and other contents of a data mining model.</span></span> <span data-ttu-id="05d98-109">如需採礦模型的資料採礦結構描述資料列集中的資料行清單，請參閱 [DMSCHEMA_MINING_MODEL_CONTENT 資料列集](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)。</span><span class="sxs-lookup"><span data-stu-id="05d98-109">For a list of the columns in the data mining schema rowset for mining models, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
## <a name="options"></a><span data-ttu-id="05d98-110">選項</span><span class="sxs-lookup"><span data-stu-id="05d98-110">Options</span></span>  
 <span data-ttu-id="05d98-111">**節點標題 (唯一識別碼)**</span><span class="sxs-lookup"><span data-stu-id="05d98-111">**Node caption (Unique ID)**</span></span>  
 <span data-ttu-id="05d98-112">此窗格顯示所選採礦模型中所有節點的清單。</span><span class="sxs-lookup"><span data-stu-id="05d98-112">This pane displays a list of all the nodes in the selected mining model.</span></span> <span data-ttu-id="05d98-113">樹狀目錄中排列節點的方式根據要檢視的模型類型而不同。</span><span class="sxs-lookup"><span data-stu-id="05d98-113">The way the nodes are arranged in the tree is different depending on the type of model you are viewing.</span></span>  
  
 <span data-ttu-id="05d98-114">您可以按一下每個節點，以在 **[節點詳細資料]** 窗格中顯示有關節點的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="05d98-114">You can click each node to display details about the node in the **Node details** pane.</span></span>  
  
 <span data-ttu-id="05d98-115">**[節點詳細資料]**</span><span class="sxs-lookup"><span data-stu-id="05d98-115">**Node details**</span></span>  
 <span data-ttu-id="05d98-116">顯示有關選取之節點內容的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="05d98-116">Displays detailed information about the content of the selected node.</span></span> <span data-ttu-id="05d98-117">每個節點都會以標準化格式儲存其資訊，但資料表中每行的內容和精確度取決於要檢視的模型類型或節點類型。</span><span class="sxs-lookup"><span data-stu-id="05d98-117">Each node stores its information in a standardized format, but the contents and significance of each line of the table depends on the type of model or type of node that you are viewing.</span></span> <span data-ttu-id="05d98-118">例如，針對表示關聯模型中之規則的節點和表示決策樹模型中之樹狀目錄的節點所儲存的資訊不同。</span><span class="sxs-lookup"><span data-stu-id="05d98-118">For example, the information stored for a node that represents a rule in an association model contains different information than a node that represents a tree in a decision trees model.</span></span>  
  
 <span data-ttu-id="05d98-119">如需如何解譯特定模型類型之節點資訊的相關資訊，請參閱[採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](data-mining/mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="05d98-119">For information about how to interpret the node information for a specific model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d98-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d98-120">See Also</span></span>  
 <span data-ttu-id="05d98-121">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="05d98-121">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="05d98-122">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="05d98-122">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="05d98-123">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="05d98-123">Data Mining Queries</span></span>](data-mining/data-mining-queries.md)  
  
  
