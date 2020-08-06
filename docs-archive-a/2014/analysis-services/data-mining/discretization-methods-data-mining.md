---
title: " (資料採礦) 的離散化方法 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- discretization [Analysis Services]
- columns [data mining], discretization
- THRESHOLDS method
- CLUSTERS method
- DiscretizationBuckets property
- AUTOMATIC method
- EQUAL_AREAS method
- coding [Data Mining]
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
author: minewiskan
ms.author: owend
ms.openlocfilehash: feca59697c1c78a08e629b62856053f2d2ce6d6d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599265"
---
# <a name="discretization-methods-data-mining"></a><span data-ttu-id="5faf5-102">分隔方法 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="5faf5-102">Discretization Methods (Data Mining)</span></span>
  <span data-ttu-id="5faf5-103">某些用來在中建立資料採礦模型的演算法 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 需要特定內容類型，才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="5faf5-103">Some algorithms that are used to create data mining models in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] require specific content types in order to function correctly.</span></span> <span data-ttu-id="5faf5-104">例如， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 貝氏機率分類演算法無法使用連續資料行做為輸入，也無法預測連續值。</span><span class="sxs-lookup"><span data-stu-id="5faf5-104">For example, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes algorithm cannot use continuous columns as input and cannot predict continuous values.</span></span> <span data-ttu-id="5faf5-105">另外，有些資料行可能包含太多值，使得演算法不容易識別資料中的模式來建立模型。</span><span class="sxs-lookup"><span data-stu-id="5faf5-105">Additionally, some columns may contain so many values that the algorithm cannot easily identify interesting patterns in the data from which to create a model.</span></span>  
  
 <span data-ttu-id="5faf5-106">在這些情況下，您可以分隔資料行中的資料，以便使用演算法來產生採礦模型。</span><span class="sxs-lookup"><span data-stu-id="5faf5-106">In these cases, you can discretize the data in the columns to enable the use of the algorithms to produce a mining model.</span></span> <span data-ttu-id="5faf5-107">*「離散化」* (Discretization) 是將值放入值區內的程序，以產生有限數目的可能狀態。</span><span class="sxs-lookup"><span data-stu-id="5faf5-107">*Discretization* is the process of putting values into buckets so that there are a limited number of possible states.</span></span> <span data-ttu-id="5faf5-108">值區本身會被視為已排序且會分隔值。</span><span class="sxs-lookup"><span data-stu-id="5faf5-108">The buckets themselves are treated as ordered and discrete values.</span></span> <span data-ttu-id="5faf5-109">您可以分隔數值和字串資料行。</span><span class="sxs-lookup"><span data-stu-id="5faf5-109">You can discretize both numeric and string columns.</span></span>  
  
 <span data-ttu-id="5faf5-110">您有許多方法可用於分隔資料。</span><span class="sxs-lookup"><span data-stu-id="5faf5-110">There are several methods that you can use to discretize data.</span></span> <span data-ttu-id="5faf5-111">如果資料採礦方案使用關聯式資料，則您可以設定 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> 屬性的值來控制用於分組資料的值區數。</span><span class="sxs-lookup"><span data-stu-id="5faf5-111">If your data mining solution uses relational data, you can control the number of buckets to use for grouping data by setting the value of the <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> property.</span></span> <span data-ttu-id="5faf5-112">預設的值區數為 5。</span><span class="sxs-lookup"><span data-stu-id="5faf5-112">The default number of buckets is 5.</span></span>  
  
 <span data-ttu-id="5faf5-113">如果資料採礦方案使用於自線上分析處理 (Online Analytical Processing, OLAP) Cube 的資料，則資料採礦演算法會使用下列方程式來自動計算要產生的值區數，其中 n 是資料行中相異資料值的數目：</span><span class="sxs-lookup"><span data-stu-id="5faf5-113">If your data mining solution uses data from an Online Analytical Processing (OLAP) cube, the data mining algorithm automatically computes the number of buckets to generate by using the following equation, where n is the number of distinct values of data in the column:</span></span>  
  
 `Number of Buckets = sqrt(n)`  
  
 <span data-ttu-id="5faf5-114">如果您不想要 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 計算值區數目，則可使用 <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> 屬性來手動指定值區數目。</span><span class="sxs-lookup"><span data-stu-id="5faf5-114">If you do not want [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to calculate the number of buckets, you can use the <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> property to manually specify the number of buckets.</span></span>  
  
 <span data-ttu-id="5faf5-115">下表描述您可用於分隔 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中之資料的方法。</span><span class="sxs-lookup"><span data-stu-id="5faf5-115">The following table describes the methods that you can use to discretize data in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="5faf5-116">分隔方法</span><span class="sxs-lookup"><span data-stu-id="5faf5-116">Discretization method</span></span>|<span data-ttu-id="5faf5-117">描述</span><span class="sxs-lookup"><span data-stu-id="5faf5-117">Description</span></span>|  
|---------------------------|-----------------|  
|`AUTOMATIC`|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="5faf5-118">會決定要使用的分隔方法。</span><span class="sxs-lookup"><span data-stu-id="5faf5-118">determines which discretization method to use.</span></span>|  
|`CLUSTERS`|<span data-ttu-id="5faf5-119">演算法會將資料分成群組，流程是先取樣定型資料、初始化為一些隨機點，然後使用 Expectation Maximization (EM) 群集方法來執行 Microsoft 群集演算法的數次反覆運算。</span><span class="sxs-lookup"><span data-stu-id="5faf5-119">The algorithm divides the data into groups by sampling the training data, initializing to a number of random points, and then running several iterations of the Microsoft Clustering algorithm using the Expectation Maximization (EM) clustering method.</span></span> <span data-ttu-id="5faf5-120">`CLUSTERS` 方法很有用，因為它在任何分佈曲線上都可以運作。</span><span class="sxs-lookup"><span data-stu-id="5faf5-120">The `CLUSTERS` method is useful because it works on any distribution curve.</span></span> <span data-ttu-id="5faf5-121">不過，它比其他分隔方法需要更多的處理時間。</span><span class="sxs-lookup"><span data-stu-id="5faf5-121">However, it requires more processing time than the other discretization methods.</span></span><br /><br /> <span data-ttu-id="5faf5-122">這個方法只能用於數值資料行。</span><span class="sxs-lookup"><span data-stu-id="5faf5-122">This method can only be used with numeric columns.</span></span>|  
|`EQUAL_AREAS`|<span data-ttu-id="5faf5-123">演算法會將資料分成數個值的數目相同之群組。</span><span class="sxs-lookup"><span data-stu-id="5faf5-123">The algorithm divides the data into groups that contain an equal number of values.</span></span> <span data-ttu-id="5faf5-124">這個方法最適合標準分佈曲線，但如果分佈中有大量的值集中在連續資料的群組中，則效果不佳。</span><span class="sxs-lookup"><span data-stu-id="5faf5-124">This method is best used for normal distribution curves, but does not work well if the distribution includes a large number of values that occur in a narrow group in the continuous data.</span></span> <span data-ttu-id="5faf5-125">例如，如果有一半項目的成本是 0，則有一半的資料將會出現在曲線的單一點之下。</span><span class="sxs-lookup"><span data-stu-id="5faf5-125">For example, if one-half of the items have a cost of 0, one-half the data will occur under a single point in the curve.</span></span> <span data-ttu-id="5faf5-126">在這樣的分佈中，這個方法會將資料再細分，以建立成多個區域的相等分隔。</span><span class="sxs-lookup"><span data-stu-id="5faf5-126">In such a distribution, this method breaks the data up in an effort to establish equal discretization into multiple areas.</span></span> <span data-ttu-id="5faf5-127">這樣會產生不精確的資料呈現。</span><span class="sxs-lookup"><span data-stu-id="5faf5-127">This produces an inaccurate representation of the data.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5faf5-128">備註</span><span class="sxs-lookup"><span data-stu-id="5faf5-128">Remarks</span></span>  
  
-   <span data-ttu-id="5faf5-129">您可以使用 `EQUAL_AREAS` 方法來分隔字串。</span><span class="sxs-lookup"><span data-stu-id="5faf5-129">You can use the `EQUAL_AREAS` method to discretize strings.</span></span>  
  
-   <span data-ttu-id="5faf5-130">`CLUSTERS` 方法使用 1000 筆隨機取樣記錄來離散化資料。</span><span class="sxs-lookup"><span data-stu-id="5faf5-130">The `CLUSTERS` method uses a random sample of 1000 records to discretize data.</span></span> <span data-ttu-id="5faf5-131">如果您不想要演算法取樣資料，請使用 `EQUAL_AREAS` 方法。</span><span class="sxs-lookup"><span data-stu-id="5faf5-131">Use the `EQUAL_AREAS` method if you do not want the algorithm to sample data.</span></span>  
  
-   <span data-ttu-id="5faf5-132">類神經網路採礦模型提供了一個範例，為您示範如何自訂分隔。</span><span class="sxs-lookup"><span data-stu-id="5faf5-132">The neural network mining model tutorial provides an example of how discretization can be customized.</span></span> <span data-ttu-id="5faf5-133">如需詳細資訊，請參閱[第5課：建立類神經網路和羅吉斯回歸模型 &#40;中繼資料採礦教學課程&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="5faf5-133">For more information, see [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5faf5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5faf5-134">See Also</span></span>  
 <span data-ttu-id="5faf5-135">[&#40;資料採礦&#41;的內容類型](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5faf5-135">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="5faf5-136">[DMX&#41;&#40;內容類型](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="5faf5-136">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="5faf5-137">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5faf5-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="5faf5-138">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5faf5-138">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="5faf5-139">[資料類型 &#40;資料採礦&#41;](data-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="5faf5-139">[Data Types &#40;Data Mining&#41;](data-types-data-mining.md) </span></span>  
 <span data-ttu-id="5faf5-140">[[採礦結構] 資料行](mining-structure-columns.md) </span><span class="sxs-lookup"><span data-stu-id="5faf5-140">[Mining Structure Columns](mining-structure-columns.md) </span></span>  
 [<span data-ttu-id="5faf5-141">資料行分佈 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="5faf5-141">Column Distributions &#40;Data Mining&#41;</span></span>](column-distributions-data-mining.md)  
  
  
