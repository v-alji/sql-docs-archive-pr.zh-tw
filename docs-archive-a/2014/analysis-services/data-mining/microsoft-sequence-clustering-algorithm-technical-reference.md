---
title: Microsoft 時序群集演算法技術參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MAXIMUM_SEQUENCE_STATES parameter
- MINIMUM_SUPPORT parameter
- MAXIMUM_STATES parameter
- sequence clustering algorithms [Analysis Services]
- CLUSTER_COUNT parameter
ms.assetid: 251c369d-6b02-4687-964e-39bf55c9b009
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3e09018fad9c291ec1f47bbb776797d634950381
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584843"
---
# <a name="microsoft-sequence-clustering-algorithm-technical-reference"></a><span data-ttu-id="16834-102">Microsoft 時序群集演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="16834-102">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>
  <span data-ttu-id="16834-103">Microsoft 時序叢集演算法是一種混合式演算法，它使用 Markov 鏈結分析來識別已排序的時序，並結合此分析的結果與叢集技術，根據模型中的時序和其他屬性產生叢集。</span><span class="sxs-lookup"><span data-stu-id="16834-103">The Microsoft Sequence Clustering algorithm is a hybrid algorithm that uses Markov chain analysis to identify ordered sequences, and combines the results of this analysis with clustering techniques to generate clusters based on the sequences and other attributes in the model.</span></span> <span data-ttu-id="16834-104">本主題描述演算法的實作、如何自訂演算法，以及時序叢集模型的特殊需求。</span><span class="sxs-lookup"><span data-stu-id="16834-104">This topic describes the implementation of the algorithm, how to customize the algorithm, and special requirements for sequence clustering models.</span></span>  
  
 <span data-ttu-id="16834-105">如需有關演算法的一般詳細資訊，包括如何瀏覽和查詢時序叢集模型，請參閱＜ [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md)＞。</span><span class="sxs-lookup"><span data-stu-id="16834-105">For more general information about the algorithm, including how to browse and query sequence clustering models, see [Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md).</span></span>  
  
## <a name="implementation-of-the-microsoft-sequence-clustering-algorithm"></a><span data-ttu-id="16834-106">Microsoft 時序群集演算法的實作</span><span class="sxs-lookup"><span data-stu-id="16834-106">Implementation of the Microsoft Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="16834-107">Microsoft 時序叢集模型使用 Markov 模型來識別時序，並判斷時序的機率。</span><span class="sxs-lookup"><span data-stu-id="16834-107">The Microsoft Sequence Clustering model uses Markov models to identify sequences and determine the probability of sequences.</span></span> <span data-ttu-id="16834-108">Markov 模型是一種導向圖形，可儲存不同狀態間的轉換。</span><span class="sxs-lookup"><span data-stu-id="16834-108">A Markov model is a directed graph that stores the transitions between different states.</span></span> <span data-ttu-id="16834-109">Microsoft 時序叢集演算法使用 n 順序的 Markov 鏈結，而非隱藏的 Markov 模型。</span><span class="sxs-lookup"><span data-stu-id="16834-109">The Microsoft Sequence Clustering algorithm uses n-order Markov chains, not a Hidden Markov model.</span></span>  
  
 <span data-ttu-id="16834-110">Markov 鏈結中的順序數目會告訴您使用多少個狀態判斷目前狀態的機率。</span><span class="sxs-lookup"><span data-stu-id="16834-110">The number of orders in a Markov chain tells you how many states are used to determine the probability of the current states.</span></span> <span data-ttu-id="16834-111">在第一優先順序的 Markov 模型中，目前狀態的機率僅取決於先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="16834-111">In a first-order Markov model, the probability of the current state depends only on the previous state.</span></span> <span data-ttu-id="16834-112">在第二優先順序的 Markov 鏈結中，狀態的機率取決於先前的兩個狀態，以此類推。</span><span class="sxs-lookup"><span data-stu-id="16834-112">In a second-order Markov chain, the probability of a state depends on the previous two states, and so forth.</span></span> <span data-ttu-id="16834-113">轉換矩陣會針對每個 Markov 鏈結儲存每個狀態組合的轉換。</span><span class="sxs-lookup"><span data-stu-id="16834-113">For each Markov chain, a transition matrix stores the transitions for each combination of states.</span></span> <span data-ttu-id="16834-114">當 Markov 鏈結的長度增加時，矩陣的大小也會以指數方式增加，而且該矩陣會變得相當疏鬆。</span><span class="sxs-lookup"><span data-stu-id="16834-114">As the length of the Markov chain increases, the size of the matrix also increases exponentially, and the matrix becomes extremely sparse.</span></span> <span data-ttu-id="16834-115">處理時間也會等比例地增加。</span><span class="sxs-lookup"><span data-stu-id="16834-115">Processing time also increases proportionally.</span></span>  
  
 <span data-ttu-id="16834-116">這可能有助於使用點選流分析的範例視覺化鏈結，以分析網頁的查閱次數。</span><span class="sxs-lookup"><span data-stu-id="16834-116">It might be helpful to visualize the chain by using the example of clickstream analysis, which analyzes visits to Web pages on a site.</span></span> <span data-ttu-id="16834-117">每個使用者都會針對每個工作階段建立一長串的點選。</span><span class="sxs-lookup"><span data-stu-id="16834-117">Each user creates a long sequence of clicks for each session.</span></span> <span data-ttu-id="16834-118">當您建立模型來分析網站上的使用者行為時，用於定型的資料集就是轉換為圖形的一連串 URL，其中包含相同點選路徑之所有執行個體的計數。</span><span class="sxs-lookup"><span data-stu-id="16834-118">When you create a model to analyze user behavior on a Web site, the data set used for training is a sequence of URLs, converted to a graph that includes the count of all instances of the same click path.</span></span> <span data-ttu-id="16834-119">例如，此圖形包含使用者從第 1 頁移到第 2 頁的機率 (10%)、使用者從第 1 頁移到第 3 頁的機率 (20%) 等等。</span><span class="sxs-lookup"><span data-stu-id="16834-119">For example, the graph contains the probability that the user moves from page 1 to page 2 (10%), the probability that the user moves from page 1 to page 3 (20%), and so forth.</span></span> <span data-ttu-id="16834-120">當您將所有可能的路徑與路徑片段放在一起時，您會取得可能比任何單一已觀察路徑更長、更複雜的圖形。</span><span class="sxs-lookup"><span data-stu-id="16834-120">When you put all the possible paths and pieces of the paths together, you obtain a graph that might be much longer and more complex than any single observed path.</span></span>  
  
 <span data-ttu-id="16834-121">根據預設，Microsoft 時序群集演算法使用 Expectation Maximization (EM) 群集方法。</span><span class="sxs-lookup"><span data-stu-id="16834-121">By default, the Microsoft Sequence Clustering algorithm uses the Expectation Maximization (EM) method of clustering.</span></span> <span data-ttu-id="16834-122">如需詳細資訊，請參閱 [Microsoft 群集演算法技術參考](microsoft-clustering-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="16834-122">For more information, see [Microsoft Clustering Algorithm Technical Reference](microsoft-clustering-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="16834-123">群集的目標為循序與非循序屬性。</span><span class="sxs-lookup"><span data-stu-id="16834-123">The targets of clustering are both the sequential and nonsequential attributes.</span></span> <span data-ttu-id="16834-124">每個群集都會使用機率分配隨機選取。</span><span class="sxs-lookup"><span data-stu-id="16834-124">Each cluster is randomly selected using a probability distribution.</span></span> <span data-ttu-id="16834-125">每個群集都有一個代表一組完整路徑的 Markov 鏈結，以及包含時序狀態轉換和機率的矩陣。</span><span class="sxs-lookup"><span data-stu-id="16834-125">Each cluster has a Markov chain that represents the complete set of paths, and a matrix that contains the sequence state transitions and probabilities.</span></span> <span data-ttu-id="16834-126">根據初始分配，貝氏機率分類規則用於計算特定群集中任何屬性的機率，包括時序。</span><span class="sxs-lookup"><span data-stu-id="16834-126">Based on the initial distribution, Bayes rule is used to calculate the probability of any attribute, including a sequence, in a specific cluster.</span></span>  
  
 <span data-ttu-id="16834-127">Microsoft 時序叢集演算法支援模型額外的非循序屬性。</span><span class="sxs-lookup"><span data-stu-id="16834-127">The Microsoft Sequence Clustering algorithm supports the additional of nonsequential attributes to the model.</span></span> <span data-ttu-id="16834-128">也就是說，這些額外的屬性會結合時序屬性，就像在一般叢集模型般建立具有類似屬性之案例的群集。</span><span class="sxs-lookup"><span data-stu-id="16834-128">This means that these additional attributes are combined with the sequence attributes to create clusters of cases with similar attributes, just like in a typical clustering model.</span></span>  
  
 <span data-ttu-id="16834-129">時序群集模型傾向於建立比一般叢集模型還要更多的叢集。</span><span class="sxs-lookup"><span data-stu-id="16834-129">A sequence clustering model tends to create many more clusters than a typical clustering model.</span></span> <span data-ttu-id="16834-130">因此，Microsoft 時序群集演算法會根據時序及其他屬性執行 *「群集分解」*(Cluster Decomposition) 來分割群集。</span><span class="sxs-lookup"><span data-stu-id="16834-130">Therefore, the Microsoft Sequence Clustering algorithm performs *cluster decomposition*to separate clusters based on sequences and other attributes.</span></span>  
  
### <a name="feature-selection-in-a-sequence-clustering-model"></a><span data-ttu-id="16834-131">時序叢集模型中的特徵選取</span><span class="sxs-lookup"><span data-stu-id="16834-131">Feature Selection in a Sequence Clustering Model</span></span>  
 <span data-ttu-id="16834-132">特徵選取不會在建立時序時叫用，但是特徵選取會在群集階段套用。</span><span class="sxs-lookup"><span data-stu-id="16834-132">Feature selection is not invoked when building sequences; however, feature selection applies at the clustering stage.</span></span>  
  
|<span data-ttu-id="16834-133">模型類型</span><span class="sxs-lookup"><span data-stu-id="16834-133">Model type</span></span>|<span data-ttu-id="16834-134">特徵選取方法</span><span class="sxs-lookup"><span data-stu-id="16834-134">Feature Selection Method</span></span>|<span data-ttu-id="16834-135">註解</span><span class="sxs-lookup"><span data-stu-id="16834-135">Comments</span></span>|  
|----------------|------------------------------|--------------|  
|<span data-ttu-id="16834-136">時序群集</span><span class="sxs-lookup"><span data-stu-id="16834-136">Sequence Clustering</span></span>|<span data-ttu-id="16834-137">未使用</span><span class="sxs-lookup"><span data-stu-id="16834-137">Not used</span></span>|<span data-ttu-id="16834-138">尚未叫用特徵選取。不過，您可以藉由設定 MINIMUM_SUPPORT 和 MINIMUM_PROBABILIITY 參數的值，控制演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="16834-138">Feature selection is not invoked; however, you can control the behavior of the algorithm by setting the value of the parameters MINIMUM_SUPPORT and MINIMUM_PROBABILIITY.</span></span>|  
|<span data-ttu-id="16834-139">叢集</span><span class="sxs-lookup"><span data-stu-id="16834-139">Clustering</span></span>|<span data-ttu-id="16834-140">有趣性分數</span><span class="sxs-lookup"><span data-stu-id="16834-140">Interestingness score</span></span>|<span data-ttu-id="16834-141">雖然群集演算法可以使用離散或離散化的演算法，但每個屬性的分數都會計算為距離，而且是連續的；因此會使用有趣性分數。</span><span class="sxs-lookup"><span data-stu-id="16834-141">Although the clustering algorithm may use discrete or discretized algorithms, the score of each attribute is calculated as a distance and is continuous; therefore the interestingness score is used.</span></span>|  
  
 <span data-ttu-id="16834-142">如需詳細資訊，請參閱 [Feature Selection](../../sql-server/install/feature-selection.md)。</span><span class="sxs-lookup"><span data-stu-id="16834-142">For more information, see [Feature Selection](../../sql-server/install/feature-selection.md).</span></span>  
  
### <a name="optimizing-performance"></a><span data-ttu-id="16834-143">最佳化效能</span><span class="sxs-lookup"><span data-stu-id="16834-143">Optimizing Performance</span></span>  
 <span data-ttu-id="16834-144">Microsoft 時序群集演算法支援各種最佳化處理的方式：</span><span class="sxs-lookup"><span data-stu-id="16834-144">The Microsoft Sequence Clustering algorithm supports various ways to optimize processing:</span></span>  
  
-   <span data-ttu-id="16834-145">設定 CLUSTER_COUNT 參數的值來控制所產生之群集的數目。</span><span class="sxs-lookup"><span data-stu-id="16834-145">Controlling the number of clusters generated, by setting a value for the CLUSTER_COUNT parameter.</span></span>  
  
-   <span data-ttu-id="16834-146">增加 MINIMUM_SUPPORT 參數的值來減少當做屬性加入之時序的數目。</span><span class="sxs-lookup"><span data-stu-id="16834-146">Reducing the number of sequences included as attributes, by increasing the value of the MINIMUM_SUPPORT parameter.</span></span> <span data-ttu-id="16834-147">因此，系統會刪除極少數的序列。</span><span class="sxs-lookup"><span data-stu-id="16834-147">As a result, rare sequences are eliminated.</span></span>  
  
-   <span data-ttu-id="16834-148">處理模型前，將相關的屬性分組來降低複雜度。</span><span class="sxs-lookup"><span data-stu-id="16834-148">Reducing complexity before processing the model, by grouping related attributes.</span></span>  
  
 <span data-ttu-id="16834-149">一般而言，您可以利用數種方式，使 n 順序 Markov 鏈結模式的效能最佳化：</span><span class="sxs-lookup"><span data-stu-id="16834-149">In general, you can optimize the performance of an n-order Markov chain mode in several ways:</span></span>  
  
-   <span data-ttu-id="16834-150">控制可能時序的長度。</span><span class="sxs-lookup"><span data-stu-id="16834-150">Controlling the length of the possible sequences.</span></span>  
  
-   <span data-ttu-id="16834-151">以程式設計方式減少 n 的值。</span><span class="sxs-lookup"><span data-stu-id="16834-151">Programmatically reducing the value of n.</span></span>  
  
-   <span data-ttu-id="16834-152">只儲存超過指定之臨界值的機率。</span><span class="sxs-lookup"><span data-stu-id="16834-152">Storing only probabilities that exceed a specified threshold.</span></span>  
  
 <span data-ttu-id="16834-153">這些方法的完整討論超出本主題的範圍。</span><span class="sxs-lookup"><span data-stu-id="16834-153">A complete discussion of these methods is beyond the scope of this topic.</span></span>  
  
## <a name="customizing-the-sequence-clustering-algorithm"></a><span data-ttu-id="16834-154">自訂時序群集演算法</span><span class="sxs-lookup"><span data-stu-id="16834-154">Customizing the Sequence Clustering Algorithm</span></span>  
 <span data-ttu-id="16834-155">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集演算法支援數個會影響所產生之採礦模型的行為、效能和精確度的參數。</span><span class="sxs-lookup"><span data-stu-id="16834-155">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports parameters that affect the behavior, performance, and accuracy of the resulting mining model.</span></span> <span data-ttu-id="16834-156">您也可以設定控制演算法處理定型資料之方式的模型旗標，修改已完成之模型的行為。</span><span class="sxs-lookup"><span data-stu-id="16834-156">You can also modify the behavior of the completed model by setting modeling flags that control the way the algorithm processes training data.</span></span>  
  
### <a name="setting-algorithm-parameters"></a><span data-ttu-id="16834-157">設定演算法參數</span><span class="sxs-lookup"><span data-stu-id="16834-157">Setting Algorithm Parameters</span></span>  
 <span data-ttu-id="16834-158">下表描述可搭配 Microsoft 時序群集演算法使用的參數。</span><span class="sxs-lookup"><span data-stu-id="16834-158">The following table describes the parameters that can be used with the Microsoft Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="16834-159">CLUSTER_COUNT</span><span class="sxs-lookup"><span data-stu-id="16834-159">CLUSTER_COUNT</span></span>  
 <span data-ttu-id="16834-160">指定演算法要建立的大約群集數目。</span><span class="sxs-lookup"><span data-stu-id="16834-160">Specifies the approximate number of clusters to be built by the algorithm.</span></span> <span data-ttu-id="16834-161">如果無法從資料建立大約群集數目，則演算法會盡可能建立最多的群集。</span><span class="sxs-lookup"><span data-stu-id="16834-161">If the approximate number of clusters cannot be built from the data, the algorithm builds as many clusters as possible.</span></span> <span data-ttu-id="16834-162">將 CLUSTER_COUNT 參數設定為 0，會導致演算法使用啟發式來判斷可建立的最佳群集數目。</span><span class="sxs-lookup"><span data-stu-id="16834-162">Setting the CLUSTER_COUNT parameter to 0 causes the algorithm to use heuristics to best determine the number of clusters to build.</span></span>  
  
 <span data-ttu-id="16834-163">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="16834-163">The default is 10.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16834-164">指定非零的數字做為演算法的提示，這樣會繼續尋找指定之數字的目標，但最後可能會找到更多或更少的結果。</span><span class="sxs-lookup"><span data-stu-id="16834-164">Specifying a non-zero number acts as a hint to the algorithm, which proceeds with the goal of finding the specified number, but may end up finding more or less.</span></span>  
  
 <span data-ttu-id="16834-165">MINIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="16834-165">MINIMUM_SUPPORT</span></span>  
 <span data-ttu-id="16834-166">指定支援屬性建立群集所需之案例的最小數目。</span><span class="sxs-lookup"><span data-stu-id="16834-166">Specifies the minimum number of cases that is required in support of an attribute to create a cluster.</span></span>  
  
 <span data-ttu-id="16834-167">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="16834-167">The default is 10.</span></span>  
  
 <span data-ttu-id="16834-168">MAXIMUM_SEQUENCE_STATES</span><span class="sxs-lookup"><span data-stu-id="16834-168">MAXIMUM_SEQUENCE_STATES</span></span>  
 <span data-ttu-id="16834-169">指定一個順序可以具有的最大狀態數目。</span><span class="sxs-lookup"><span data-stu-id="16834-169">Specifies the maximum number of states that a sequence can have.</span></span>  
  
 <span data-ttu-id="16834-170">將此值設定為大於 100 的數字，可能會導致演算法建立一個無法提供有用資訊的模型。</span><span class="sxs-lookup"><span data-stu-id="16834-170">Setting this value to a number greater than 100 may cause the algorithm to create a model that does not provide meaningful information.</span></span>  
  
 <span data-ttu-id="16834-171">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="16834-171">The default is 64.</span></span>  
  
 <span data-ttu-id="16834-172">MAXIMUM_STATES</span><span class="sxs-lookup"><span data-stu-id="16834-172">MAXIMUM_STATES</span></span>  
 <span data-ttu-id="16834-173">針對演算法支援的非順序屬性指定最大狀態數目。</span><span class="sxs-lookup"><span data-stu-id="16834-173">Specifies the maximum number of states for a non-sequence attribute that the algorithm supports.</span></span> <span data-ttu-id="16834-174">如果非順序屬性的狀態數目大於狀態的最大數目，演算法會使用屬性最常用的狀態，並將其餘的狀態視為 `Missing` 。</span><span class="sxs-lookup"><span data-stu-id="16834-174">If the number of states for a non-sequence attribute is greater than the maximum number of states, the algorithm uses the attribute's most popular states and treats the remaining states as `Missing`.</span></span>  
  
 <span data-ttu-id="16834-175">預設值為 100。</span><span class="sxs-lookup"><span data-stu-id="16834-175">The default is 100.</span></span>  
  
### <a name="modeling-flags"></a><span data-ttu-id="16834-176">模型旗標</span><span class="sxs-lookup"><span data-stu-id="16834-176">Modeling Flags</span></span>  
 <span data-ttu-id="16834-177">下列模型旗標受到支援，可搭配 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序叢集演算法使用。</span><span class="sxs-lookup"><span data-stu-id="16834-177">The following modeling flags are supported for use with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="16834-178">NOT NULL</span><span class="sxs-lookup"><span data-stu-id="16834-178">NOT NULL</span></span>  
 <span data-ttu-id="16834-179">表示資料行不能包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="16834-179">Indicates that the column cannot contain a null.</span></span> <span data-ttu-id="16834-180">如果 Analysis Services 在模型定型期間遇到 Null 值，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="16834-180">An error will result if Analysis Services encounters a null during model training.</span></span>  
  
 <span data-ttu-id="16834-181">適用於採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="16834-181">Applies to the mining structure column.</span></span>  
  
 <span data-ttu-id="16834-182">MODEL_EXISTENCE_ONLY</span><span class="sxs-lookup"><span data-stu-id="16834-182">MODEL_EXISTENCE_ONLY</span></span>  
 <span data-ttu-id="16834-183">表示資料行將被視為擁有兩個可能狀態：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="16834-183">Means that the column will be treated as having two possible states: `Missing` and `Existing`.</span></span> <span data-ttu-id="16834-184">Null 值會被視為 `Missing` 值。</span><span class="sxs-lookup"><span data-stu-id="16834-184">A null is treated as a `Missing` value.</span></span>  
  
 <span data-ttu-id="16834-185">適用於採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="16834-185">Applies to the mining model column.</span></span>  
  
 <span data-ttu-id="16834-186">如需如何在採礦模型中使用 Missing 值，以及遺漏值如何影響機率分數的詳細資訊，請參閱[遺漏值&#40;Analysis Services - 資料採礦&#41;](missing-values-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="16834-186">For more information about the use of Missing values in mining models, and how missing values affect probability scores, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16834-187">需求</span><span class="sxs-lookup"><span data-stu-id="16834-187">Requirements</span></span>  
 <span data-ttu-id="16834-188">案例資料表必須有一個案例識別碼資料行。</span><span class="sxs-lookup"><span data-stu-id="16834-188">The case table must have a case ID column.</span></span> <span data-ttu-id="16834-189">案例資料表可以選擇性地包含儲存案例之相關屬性的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="16834-189">Optionally the case table can contain other columns that store attributes about the case.</span></span>  
  
 <span data-ttu-id="16834-190">Microsoft 時序群集演算法需要儲存為巢狀資料表的時序資訊。</span><span class="sxs-lookup"><span data-stu-id="16834-190">The Microsoft Sequence Clustering algorithm requires sequence information, stored as a nested table.</span></span> <span data-ttu-id="16834-191">巢狀資料表必須有一個單一的 Key Sequence 資料行。</span><span class="sxs-lookup"><span data-stu-id="16834-191">The nested table must have a single Key Sequence column.</span></span> <span data-ttu-id="16834-192">`Key Sequence` 資料行可以包含能夠儲存的任何資料類型，包括字串資料類型，但資料行對於每個案例，必須包含唯一的值。</span><span class="sxs-lookup"><span data-stu-id="16834-192">A `Key Sequence` column can contain any type of data that can be sorted, including string data types, but the column must contain unique values for each case.</span></span> <span data-ttu-id="16834-193">此外，處理模型前，您必須確認案例資料表與巢狀資料表都根據與資料表相關的索引鍵，以遞增方式排序。</span><span class="sxs-lookup"><span data-stu-id="16834-193">Moreover, before you process the model, you must ensure that both the case table and the nested table are sorted in ascending order on the key that relates the tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16834-194">如果您建立使用 Microsoft 時序演算法但不使用時序資料行的模型，所產生的模型將不包含任何時序，但是將只根據模型中包含的其他屬性群集案例。</span><span class="sxs-lookup"><span data-stu-id="16834-194">If you create a model that uses the Microsoft Sequence algorithm but do not use a sequence column, the resulting model will not contain any sequences, but will simply cluster cases based on other attributes that are included in the model.</span></span>  
  
### <a name="input-and-predictable-columns"></a><span data-ttu-id="16834-195">輸入和可預測資料行</span><span class="sxs-lookup"><span data-stu-id="16834-195">Input and Predictable Columns</span></span>  
 <span data-ttu-id="16834-196">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集演算法支援下表所列的特定輸入資料行和可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="16834-196">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports the specific input columns and predictable columns that are listed in the following table.</span></span> <span data-ttu-id="16834-197">如需內容類型用於採礦模型時所代表意義的詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="16834-197">For more information about what the content types mean when used in a mining model, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
|<span data-ttu-id="16834-198">資料行</span><span class="sxs-lookup"><span data-stu-id="16834-198">Column</span></span>|<span data-ttu-id="16834-199">內容類型</span><span class="sxs-lookup"><span data-stu-id="16834-199">Content types</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="16834-200">輸入屬性</span><span class="sxs-lookup"><span data-stu-id="16834-200">Input attribute</span></span>|<span data-ttu-id="16834-201">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="16834-201">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Table, and Ordered</span></span>|  
|<span data-ttu-id="16834-202">可預測屬性</span><span class="sxs-lookup"><span data-stu-id="16834-202">Predictable attribute</span></span>|<span data-ttu-id="16834-203">Continuous、Cyclical、Discrete、Discretized、Table 和 Ordered</span><span class="sxs-lookup"><span data-stu-id="16834-203">Continuous, Cyclical, Discrete, Discretized, Table, and Ordered</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16834-204">備註</span><span class="sxs-lookup"><span data-stu-id="16834-204">Remarks</span></span>  
  
-   <span data-ttu-id="16834-205">請使用 [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) 函數以預測時序。</span><span class="sxs-lookup"><span data-stu-id="16834-205">Use the [PredictSequence &#40;DMX&#41;](/sql/dmx/predictsequence-dmx) function for Prediction of Sequences.</span></span> <span data-ttu-id="16834-206">如需有關支援序列預測之版本的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2012 (版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="16834-206">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Sequence Prediction, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
-   <span data-ttu-id="16834-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序叢集演算法不支援使用預測模型標記語言 (PMML) 來建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="16834-207">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm does not support using the Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
-   <span data-ttu-id="16834-208">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時序群集演算法支援鑽研、OLAP 採礦模型的使用，以及資料採礦維度的使用。</span><span class="sxs-lookup"><span data-stu-id="16834-208">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering algorithm supports drillthrough, the use of OLAP mining models, and the use of data mining dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16834-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16834-209">See Also</span></span>  
 <span data-ttu-id="16834-210">[Microsoft 時序群集演算法](microsoft-sequence-clustering-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="16834-210">[Microsoft Sequence Clustering Algorithm](microsoft-sequence-clustering-algorithm.md) </span></span>  
 <span data-ttu-id="16834-211">[時序群集模型查詢範例](clustering-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="16834-211">[Sequence Clustering Model Query Examples](clustering-model-query-examples.md) </span></span>  
 [<span data-ttu-id="16834-212">時序叢集模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="16834-212">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)  
  
  
