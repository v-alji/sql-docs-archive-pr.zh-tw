---
title: 測試和驗證工作，以及如何 (資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- predictive modeling [Analysis Services]
- mining structures [Analysis Services], predictive modeling
- Mining Accuracy Chart [Analysis Services], how-to topics
- mining models [Analysis Services], predictive modeling
- predictive accuracy [data mining]
ms.assetid: 3a0b4dc9-5b64-4be1-aa5f-6ff26f43dbf8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10844a7d39e49ab595eb25bb56ed3f4f5d415565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605939"
---
# <a name="testing-and-validation-tasks-and-how-tos-data-mining"></a><span data-ttu-id="84f54-102">測試及驗證工作與操作方法 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="84f54-102">Testing and Validation Tasks and How-tos (Data Mining)</span></span>
  <span data-ttu-id="84f54-103">您可以在 **中使用資料採礦設計師的** [採礦精確度圖表] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 索引標籤，比較採礦結構中之採礦模型的預測精確度。</span><span class="sxs-lookup"><span data-stu-id="84f54-103">You can use the **Mining Accuracy Chart** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to compare the predictive accuracy of the mining models in your mining structure.</span></span>  
  
 <span data-ttu-id="84f54-104">您可以建立四種圖表：</span><span class="sxs-lookup"><span data-stu-id="84f54-104">You can create four kinds of charts:</span></span>  
  
-   <span data-ttu-id="84f54-105">增益圖</span><span class="sxs-lookup"><span data-stu-id="84f54-105">Lift chart</span></span>  
  
-   <span data-ttu-id="84f54-106">收益圖</span><span class="sxs-lookup"><span data-stu-id="84f54-106">Profit chart</span></span>  
  
-   <span data-ttu-id="84f54-107">分類矩陣</span><span class="sxs-lookup"><span data-stu-id="84f54-107">Classification matrix</span></span>  
  
-   <span data-ttu-id="84f54-108">交叉驗證報表</span><span class="sxs-lookup"><span data-stu-id="84f54-108">Cross-validation report</span></span>  
  
 <span data-ttu-id="84f54-109">前三個圖表會使用 **[輸入選擇]** 索引標籤來定義用於產生圖表的資料。</span><span class="sxs-lookup"><span data-stu-id="84f54-109">The first three charts use the **Input Selection** tab to define the data that is used for generating the chart.</span></span>  
  
 <span data-ttu-id="84f54-110">交叉驗證圖表是使用 [**交叉驗證**] 索引標籤上提供的其他輸入所建立。如需詳細資訊，請參閱[交叉驗證 &#40;Analysis Services-資料採礦&#41;](cross-validation-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="84f54-110">The Cross-validation chart is created by using additional inputs, available on the **Cross-Validation** tab. For more information, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](cross-validation-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="84f54-111">如需如何使用採礦精確度圖表的詳細資訊，請參閱[測試和驗證 &#40;資料採礦&#41;](testing-and-validation-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="84f54-111">For more information about how to use the mining accuracy chart, see [Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84f54-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="84f54-112">In This Section</span></span>  
  
-   [<span data-ttu-id="84f54-113">建立增益圖、收益圖或分類矩陣</span><span class="sxs-lookup"><span data-stu-id="84f54-113">Create a Lift Chart, Profit Chart, or Classification Matrix</span></span>](create-a-lift-chart-profit-chart-or-classification-matrix.md)  
  
-   [<span data-ttu-id="84f54-114">建立交叉驗證報表</span><span class="sxs-lookup"><span data-stu-id="84f54-114">Create a Cross-Validation Report</span></span>](create-a-cross-validation-report.md)  
  
-   [<span data-ttu-id="84f54-115">選擇和對應模型測試資料</span><span class="sxs-lookup"><span data-stu-id="84f54-115">Choose and Map Model Testing Data</span></span>](choose-and-map-model-testing-data.md)  
  
-   [<span data-ttu-id="84f54-116">將篩選套用至模型測試資料</span><span class="sxs-lookup"><span data-stu-id="84f54-116">Apply Filters to Model Testing Data</span></span>](apply-filters-to-model-testing-data.md)  
  
-   [<span data-ttu-id="84f54-117">選擇用於測試採礦模型的資料行</span><span class="sxs-lookup"><span data-stu-id="84f54-117">Choose the Column to Use for Testing a Mining Model</span></span>](choose-the-column-to-use-for-testing-a-mining-model.md)  
  
-   [<span data-ttu-id="84f54-118">使用巢狀資料表當做精確度圖表的輸入</span><span class="sxs-lookup"><span data-stu-id="84f54-118">Using Nested Table Data as an Input for an Accuracy Chart</span></span>](using-nested-table-data-as-an-input-for-an-accuracy-chart.md)  
  
  
