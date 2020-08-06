---
title: 資料採礦) 的資料行發行 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
ms.openlocfilehash: 29aad33535c4cc4d9baf4c453249ce3b51595e78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607171"
---
# <a name="column-distributions-data-mining"></a><span data-ttu-id="4474d-102">資料行散發 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="4474d-102">Column Distributions (Data Mining)</span></span>
  <span data-ttu-id="4474d-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您可以在採礦結構中定義資料行散發，以影響當您建立採礦模型時，演算法如何處理這些資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="4474d-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define column distributions in a mining structure, to affect how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="4474d-104">針對某些演算法，若已知資料行包含值的通用散發，則在處理模型前先定義任何連續資料行的散發很有用。</span><span class="sxs-lookup"><span data-stu-id="4474d-104">For some algorithms, it is useful to define the distribution of any continuous columns before you process the model, if the columns are known to contain common distributions of values.</span></span> <span data-ttu-id="4474d-105">如果您未定義散發，則產生之採礦模型所做出的預測，可能不如定義了散發的預測那般精確，因為演算法能用來解譯資料的資訊比較少。</span><span class="sxs-lookup"><span data-stu-id="4474d-105">If you do not define the distributions, the resulting mining models may produce less accurate predictions than if the distributions were defined, because the algorithms will have less information from which to interpret the data.</span></span>

 <span data-ttu-id="4474d-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中可用的演算法支援下列散發類型：</span><span class="sxs-lookup"><span data-stu-id="4474d-106">The algorithms that are available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support the following distribution types:</span></span>

 <span data-ttu-id="4474d-107">`Normal`連續資料行的值會形成具有一般分佈的長條圖。</span><span class="sxs-lookup"><span data-stu-id="4474d-107">`Normal` The values for the continuous column form a histogram with a normal distribution.</span></span>

 <span data-ttu-id="4474d-108">![使用一般分佈的長條圖](../media/normal-distribution.gif "使用一般分佈的長條圖")</span><span class="sxs-lookup"><span data-stu-id="4474d-108">![Histogram with normal distribution](../media/normal-distribution.gif "Histogram with normal distribution")</span></span>

 <span data-ttu-id="4474d-109">`Log Normal`連續資料行的值會形成長條圖，其中的曲線會在上半部上端伸長，而且會扭曲到低端。</span><span class="sxs-lookup"><span data-stu-id="4474d-109">`Log Normal` The values for the continuous column form a histogram, where the curve is elongated at the upper end and is skewed toward the lower end.</span></span>

 <span data-ttu-id="4474d-110">![使用記錄一般分佈的長條圖](../media/log-normal-distribution.gif "使用記錄一般分佈的長條圖")</span><span class="sxs-lookup"><span data-stu-id="4474d-110">![Histogram with log normal distribution](../media/log-normal-distribution.gif "Histogram with log normal distribution")</span></span>

 <span data-ttu-id="4474d-111">`Uniform`連續資料行的值形成一個平面曲線，其中所有的值都同樣可能。</span><span class="sxs-lookup"><span data-stu-id="4474d-111">`Uniform` The values for the continuous column form a flat curve, in which all values are equally likely.</span></span>

 <span data-ttu-id="4474d-112">![具有統一分佈的長條圖](../media/uniform-distribution.gif "具有統一分佈的長條圖")</span><span class="sxs-lookup"><span data-stu-id="4474d-112">![Histogram with uniform distribution](../media/uniform-distribution.gif "Histogram with uniform distribution")</span></span>

 <span data-ttu-id="4474d-113">如需 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供的演算法的詳細資訊，請參閱[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="4474d-113">For more information about the algorithms that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4474d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4474d-114">See Also</span></span>
 <span data-ttu-id="4474d-115">[內容類型 &#40;資料採礦&#41;](content-types-data-mining.md) [採礦結構 &#40;Analysis Services 資料採礦&#41;分隔](mining-structures-analysis-services-data-mining.md)[方法 &#40;資料採礦&#41;](discretization-methods-data-mining.md)散發 &#40;[DMX&#41;](/sql/dmx/distributions-dmx) [採礦結構資料行](mining-structure-columns.md)</span><span class="sxs-lookup"><span data-stu-id="4474d-115">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) [Discretization Methods &#40;Data Mining&#41;](discretization-methods-data-mining.md) [Distributions &#40;DMX&#41;](/sql/dmx/distributions-dmx) [Mining Structure Columns](mining-structure-columns.md)</span></span>


