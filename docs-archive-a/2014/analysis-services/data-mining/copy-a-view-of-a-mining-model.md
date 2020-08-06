---
title: 複製採礦模型的視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clipboards [data mining]
- Mining Model Viewer [Analysis Services], clipboards
- copying mining models to clipboard
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36d4d372bd235cd1cc0c043ff98151091e242269
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686549"
---
# <a name="copy-a-view-of-a-mining-model"></a><span data-ttu-id="f5057-102">複製採礦模型的檢視</span><span class="sxs-lookup"><span data-stu-id="f5057-102">Copy a View of a Mining Model</span></span>
  <span data-ttu-id="f5057-103">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，資料採礦設計師的 [採礦模型檢視器]\*\*\*\* 索引標籤，對每一種類型的採礦模型都會使用個別的檢視器。</span><span class="sxs-lookup"><span data-stu-id="f5057-103">The **Mining Model Viewer** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] uses a separate viewer for each type of mining model.</span></span> <span data-ttu-id="f5057-104">有幾個檢視器含有一些元件，您可將其內容複製至剪貼簿，再將剪貼簿內容複製到文件或影像操作軟體。</span><span class="sxs-lookup"><span data-stu-id="f5057-104">Several of the viewers have components from which you can copy the contents to the Clipboard, and from there paste the contents into a document or into image manipulation software.</span></span> <span data-ttu-id="f5057-105">下列元件可以使用此功能：</span><span class="sxs-lookup"><span data-stu-id="f5057-105">The following components make this functionality available:</span></span>  
  
-   <span data-ttu-id="f5057-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 群集檢視器和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集檢視器中的群集圖表</span><span class="sxs-lookup"><span data-stu-id="f5057-106">Cluster Diagram in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="f5057-107">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 樹狀檢視器和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列檢視器中的決策樹</span><span class="sxs-lookup"><span data-stu-id="f5057-107">Decision Tree in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series Viewer</span></span>  
  
-   <span data-ttu-id="f5057-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集檢視器中的狀態轉換</span><span class="sxs-lookup"><span data-stu-id="f5057-108">State Transitions in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster Viewer</span></span>  
  
-   <span data-ttu-id="f5057-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 關聯規則檢視器、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類檢視器和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 樹狀檢視器中的相依性網路</span><span class="sxs-lookup"><span data-stu-id="f5057-109">Dependency Network in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules Viewer, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes Viewer, and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tree Viewer</span></span>  
  
-   <span data-ttu-id="f5057-110">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般內容樹狀檢視器之 [節點詳細資料] 窗格中的採礦模型內容</span><span class="sxs-lookup"><span data-stu-id="f5057-110">Mining model content, from the Node Details pane of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer</span></span>  
  
 <span data-ttu-id="f5057-111">您可以複製完整的採礦模型表示，或只複製檢視器可見的部分。</span><span class="sxs-lookup"><span data-stu-id="f5057-111">You can copy the complete representation of the mining model, or just the part that is visible in the viewer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="f5057-112">當您使用檢視器複製模型時，不會建立新的模型物件。</span><span class="sxs-lookup"><span data-stu-id="f5057-112">When you copy a model using the viewer, it does not create a new model object.</span></span> <span data-ttu-id="f5057-113">若要建立新模型，您必須使用精靈或資料採礦設計師。</span><span class="sxs-lookup"><span data-stu-id="f5057-113">To create a new model, you must use either the wizard, or the Data Mining Designer,.</span></span> <span data-ttu-id="f5057-114">如需詳細資訊，請參閱 [建立採礦模型的複本](make-a-copy-of-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="f5057-114">For more information, see [Make a Copy of a Mining Model](make-a-copy-of-a-mining-model.md).</span></span>  
  
### <a name="to-copy-the-complete-model-to-the-clipboard"></a><span data-ttu-id="f5057-115">將完整的模型複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="f5057-115">To copy the complete model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="f5057-116">從 [採礦模型檢視器]\*\*\*\* 索引標籤的 [採礦模型]\*\*\*\* 清單中，選取您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f5057-116">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="f5057-117">選取適當的索引標籤，例如 [相依性網路]\*\*\*\* 索引標籤，然後按一下該索引標籤之工具列上的 [複製整個圖表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5057-117">Select the appropriate tab, such as the **Dependency Network** tab, and then click **Copy Entire Graph** on the toolbar of that tab.</span></span>  
  
### <a name="to-copy-the-visible-piece-of-the-model-to-the-clipboard"></a><span data-ttu-id="f5057-118">若要將模型的可見部份複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="f5057-118">To copy the visible piece of the model to the Clipboard</span></span>  
  
1.  <span data-ttu-id="f5057-119">從 [採礦模型檢視器]\*\*\*\* 索引標籤的 [採礦模型]\*\*\*\* 清單中，選取您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f5057-119">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="f5057-120">選取適合的索引標籤，例如 [相依性網路]\*\*\*\* 索引標籤，然後放大或縮小，在您要的層級上檢視模型。</span><span class="sxs-lookup"><span data-stu-id="f5057-120">Select the appropriate tab, such as the **Dependency Network** tab, and then zoom in or out to view the model at the level that you want.</span></span>  
  
3.  <span data-ttu-id="f5057-121">按一下所選取索引標籤之工具列上的 [複製圖表檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5057-121">Click **Copy Graph View** on the toolbar of the selected tab.</span></span>  
  
### <a name="to-copy-the-mining-model-content-to-the-clipboard"></a><span data-ttu-id="f5057-122">將採礦模型內容複製到剪貼簿</span><span class="sxs-lookup"><span data-stu-id="f5057-122">To copy the mining model content to the Clipboard</span></span>  
  
1.  <span data-ttu-id="f5057-123">從 [採礦模型檢視器]\*\*\*\* 索引標籤的 [採礦模型]\*\*\*\* 清單中，選取您要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f5057-123">From the **Mining Model** list on the **Mining Model Viewer** tab, select the mining model that you want to view.</span></span>  
  
2.  <span data-ttu-id="f5057-124">從 [檢視器]\*\*\*\* 下拉式清單中，選取 [Microsoft 一般內容樹狀檢視器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5057-124">From the **Viewer** drop-down list, select **Microsoft Generic Content Tree Viewer**.</span></span>  
  
3.  <span data-ttu-id="f5057-125">在 [節點標題 (唯一 ID)]\*\*\*\* 窗格中，按一下節點。</span><span class="sxs-lookup"><span data-stu-id="f5057-125">In the **Node Caption (Unique ID)** pane, click a node.</span></span>  
  
4.  <span data-ttu-id="f5057-126">以滑鼠右鍵按一下 [節點詳細資料]\*\*\*\* 窗格，然後選取 [全選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5057-126">Right-click the **Node Details** pane and then select **Select All**.</span></span>  
  
5.  <span data-ttu-id="f5057-127">再次以滑鼠右鍵按一下 [節點詳細資料]\*\*\*\* 窗格，然後選取 [複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5057-127">Right-click the **Node Details** pane again and select **Copy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5057-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5057-128">See Also</span></span>  
 [<span data-ttu-id="f5057-129">採礦模型檢視器工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="f5057-129">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
  
