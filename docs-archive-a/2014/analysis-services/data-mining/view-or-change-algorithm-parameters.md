---
title: 查看或變更演算法參數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- mining models [Analysis Services], algorithms
ms.assetid: 151b899b-c27a-4a09-bcf5-5c9f0ec24168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 30719cd50e0c473cf2aab5d9689d27dff4f26343
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594821"
---
# <a name="view-or-change-algorithm-parameters"></a><span data-ttu-id="259b4-102">檢視或變更演算法參數</span><span class="sxs-lookup"><span data-stu-id="259b4-102">View or Change Algorithm Parameters</span></span>
  <span data-ttu-id="259b4-103">您可以變更演算法所提供的參數，您會使用該演算法來建立資料採礦模型，以自訂模型的結果。</span><span class="sxs-lookup"><span data-stu-id="259b4-103">You can change the parameters provided with the algorithms that you use to build data mining models to customize the results of the model.</span></span>  
  
 <span data-ttu-id="259b4-104">中提供的演算法參數不 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 只是模型上的屬性而變更，它們可以用來從根本上改變資料處理、群組和顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="259b4-104">The algorithm parameters provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] change much more than just properties on the model: they can be used to fundamentally alter the way that data is processed, grouped, and displayed.</span></span> <span data-ttu-id="259b4-105">例如，您可以使用演算法參數來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="259b4-105">For example, you can use algorithm parameters to do the following:</span></span>  
  
-   <span data-ttu-id="259b4-106">變更分析的方法，例如叢集方法。</span><span class="sxs-lookup"><span data-stu-id="259b4-106">Change the method of analysis, such as the clustering method.</span></span>  
  
-   <span data-ttu-id="259b4-107">控制特徵選取行為。</span><span class="sxs-lookup"><span data-stu-id="259b4-107">Control feature selection behavior.</span></span>  
  
-   <span data-ttu-id="259b4-108">指定項目集的大小或規則的機率。</span><span class="sxs-lookup"><span data-stu-id="259b4-108">Specify the size of itemsets or the probability of rules.</span></span>  
  
-   <span data-ttu-id="259b4-109">控制決策樹的分支和深度。</span><span class="sxs-lookup"><span data-stu-id="259b4-109">Control branching and depth of decision trees.</span></span>  
  
-   <span data-ttu-id="259b4-110">指定模型建立所使用之內部鑑效組集合的初始值或大小。</span><span class="sxs-lookup"><span data-stu-id="259b4-110">Specify a seed value or the size of the internal holdout set used for model creation.</span></span>  
  
 <span data-ttu-id="259b4-111">為每個演算法提供的參數會有很大的差異；如需您可以為每個演算法設定的參數清單，請參閱本節中的技術參考主題：[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="259b4-111">The parameters provided for each algorithm vary greatly; for a list of the parameters that you can set for each algorithm, see the technical reference topics in this section: [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="change-an-algorithm-parameter"></a><span data-ttu-id="259b4-112">變更演算法參數</span><span class="sxs-lookup"><span data-stu-id="259b4-112">Change an algorithm parameter</span></span>  
  
1.  <span data-ttu-id="259b4-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下您要微調演算法之採礦模型的演算法類型，並選取 [設定演算法參數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="259b4-113">On the **Mining Models** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], right-click the algorithm type of the mining model for which you want to tune the algorithm, and select **Set Algorithm Parameters**.</span></span>  
  
     <span data-ttu-id="259b4-114">就會開啟 **[演算法參數]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="259b4-114">The **Algorithm Parameters** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="259b4-115">在 **[值]** 資料行中，設定您要變更之演算法的新值。</span><span class="sxs-lookup"><span data-stu-id="259b4-115">In the **Value** column, set a new value for the algorithm that you want to change.</span></span>  
  
     <span data-ttu-id="259b4-116">如果您沒有在 **[值]** 資料行中輸入值， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會使用預設參數值。</span><span class="sxs-lookup"><span data-stu-id="259b4-116">If you do not enter a value in the **Value** column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the default parameter value.</span></span> <span data-ttu-id="259b4-117">**[範圍]** 資料行描述您可以輸入的可能值。</span><span class="sxs-lookup"><span data-stu-id="259b4-117">The **Range** column describes the possible values that you can enter.</span></span>  
  
3.  <span data-ttu-id="259b4-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="259b4-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="259b4-119">演算法參數就會以新值設定。</span><span class="sxs-lookup"><span data-stu-id="259b4-119">The algorithm parameter is set with the new value.</span></span> <span data-ttu-id="259b4-120">要等到您重新處理採礦模型之後，參數變更才會反映在該採礦模型中。</span><span class="sxs-lookup"><span data-stu-id="259b4-120">The parameter change will not be reflected in the mining model until you reprocess the model.</span></span>  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a><span data-ttu-id="259b4-121">檢視用於現有模型中的參數</span><span class="sxs-lookup"><span data-stu-id="259b4-121">View the parameters used in an existing model</span></span>  
  
1.  <span data-ttu-id="259b4-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 DMX 查詢視窗。</span><span class="sxs-lookup"><span data-stu-id="259b4-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open a DMX Query window.</span></span>  
  
2.  <span data-ttu-id="259b4-123">輸入類似以下的查詢：</span><span class="sxs-lookup"><span data-stu-id="259b4-123">Type a query like this one:</span></span>  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="259b4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="259b4-124">See Also</span></span>  
 [<span data-ttu-id="259b4-125">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="259b4-125">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
