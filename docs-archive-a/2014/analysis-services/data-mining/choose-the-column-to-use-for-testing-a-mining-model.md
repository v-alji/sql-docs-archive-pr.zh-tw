---
title: 選擇用來測試採礦模型的資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- columns [data mining], predictable mining columns
- Mining Accuracy Chart [Analysis Services], columns
- predictable mining columns [Analysis Services]
ms.assetid: c6a8f23a-da21-4f31-9521-99460d624649
author: minewiskan
ms.author: owend
ms.openlocfilehash: 326a7084600695d95d3a132f633041e9abad045b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597460"
---
# <a name="choose-the-column-to-use-for-testing-a-mining-model"></a><span data-ttu-id="dc830-102">選擇用於測試採礦模型的資料行</span><span class="sxs-lookup"><span data-stu-id="dc830-102">Choose the Column to Use for Testing a Mining Model</span></span>
  <span data-ttu-id="dc830-103">在您可以衡量採礦模型的精確度之前，您必須決定您想要評估哪一種結果。</span><span class="sxs-lookup"><span data-stu-id="dc830-103">Before you can measure the accuracy of a mining model, you must decide which outcome it is that you want to assess.</span></span> <span data-ttu-id="dc830-104">大多數的資料採礦模型都會要求您至少選擇一個資料行，以便在您建立模型時當做可預測的屬性使用。</span><span class="sxs-lookup"><span data-stu-id="dc830-104">Most data mining models require that you choose at least one column to use as the predictable attribute when you create the model.</span></span> <span data-ttu-id="dc830-105">因此，當您測試模型的精確度時，您通常必須選取該屬性進行測試。</span><span class="sxs-lookup"><span data-stu-id="dc830-105">Therefore, when you test the accuracy of the model, you generally must select that attribute to test.</span></span>  
  
 <span data-ttu-id="dc830-106">下列清單描述在選擇測試用的可預測屬性時的一些其他考量事項：</span><span class="sxs-lookup"><span data-stu-id="dc830-106">The following list describes some additional considerations for choosing the predictable attribute to use in testing:</span></span>  
  
-   <span data-ttu-id="dc830-107">某些類型的資料採礦模型可以預測多個屬性（例如類神經網路），以便探索許多屬性之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="dc830-107">Some types of data mining models can predict multiple attributes-such as neural networks, which can explore the relationships between many attributes.</span></span>  
  
-   <span data-ttu-id="dc830-108">其他類型的採礦模型（例如叢集模型）則不一定要有可預測的屬性。</span><span class="sxs-lookup"><span data-stu-id="dc830-108">Other types of mining models-such as clustering models-do not necessarily have a predictable attribute.</span></span> <span data-ttu-id="dc830-109">除非群集模型擁有可預測的屬性，否則無法加以測試。</span><span class="sxs-lookup"><span data-stu-id="dc830-109">Clustering models cannot be tested unless they have a predictable attribute.</span></span>  
  
-   <span data-ttu-id="dc830-110">建立散佈圖或是衡量迴歸模型的精確度需要您選擇連續可預測屬性當做結果。</span><span class="sxs-lookup"><span data-stu-id="dc830-110">To create a scatter plot or measure the accuracy of a regression model requires that you choose a continuous predictable attribute as the outcome.</span></span> <span data-ttu-id="dc830-111">在該情況下，您不能指定目標值。</span><span class="sxs-lookup"><span data-stu-id="dc830-111">In that case, you cannot specify a target value.</span></span> <span data-ttu-id="dc830-112">如果您要建立散佈圖以外的任何項目，基礎採礦結構資料行也必須具有 [離散]\*\*\*\* 或 [離散化]\*\*\*\* 的內容類型。</span><span class="sxs-lookup"><span data-stu-id="dc830-112">If you are creating anything other than a scatter plot, the underlying mining structure column must also have a content type of **Discrete** or **Discretized**.</span></span>  
  
-   <span data-ttu-id="dc830-113">如果您選擇離散屬性當作可預測的結果，您也可以指定目標值，或是將 [預測值]\*\*\*\* 欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="dc830-113">If you choose a discrete attribute as the predictable outcome, you can also specify a target value, or you can leave the **Predict Value** field blank.</span></span> <span data-ttu-id="dc830-114">如果您包含**預測值**，則圖表只會測量模型在預測目標值時的有效性。</span><span class="sxs-lookup"><span data-stu-id="dc830-114">If you include a **Predict Value**, the chart will measure only the model's effectiveness at predicting the target value.</span></span> <span data-ttu-id="dc830-115">如果您未指定目標結果，將會衡量此模型對於預測所有結果的精確度。</span><span class="sxs-lookup"><span data-stu-id="dc830-115">If you do not specify a target outcome, the model is measured for its accuracy in predicting all outcomes.</span></span>  
  
-   <span data-ttu-id="dc830-116">如果您想要在單一精確度圖表中包含多個模型並加以比較，則所有模型都必須使用相同的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="dc830-116">If you want to include multiple models and compare them in a single accuracy chart, all models must use the same predictable column.</span></span>  
  
-   <span data-ttu-id="dc830-117">當您建立交叉驗證報表時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 將會自動分析具有相同可預測屬性的所有模型。</span><span class="sxs-lookup"><span data-stu-id="dc830-117">When you create a cross-validation report, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will automatically analyze all models that have the same predictable attribute.</span></span>  
  
-   <span data-ttu-id="dc830-118">當選取 [同步處理預測資料行和值]\*\*\*\* 選項時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會自動選擇擁有相同名稱和相符之資料類型的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="dc830-118">When the option, **Synchronize Prediction columns and Values**, is selected, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] automatically chooses predictable columns that have the same names and matching data types.</span></span> <span data-ttu-id="dc830-119">如果您的資料行不符合這些準則，您可以關閉這個選項，並手動選擇可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="dc830-119">If your columns do not meet these criteria, you can turn off this option and manually choose a predictable column.</span></span> <span data-ttu-id="dc830-120">如果您正在使用外部資料集來測試模型 (此資料集擁有的資料行與模型的資料行不同)，您可能需要進行這項處理。</span><span class="sxs-lookup"><span data-stu-id="dc830-120">You might need to do this if you are testing the model with an external data set that has different columns than the model.</span></span> <span data-ttu-id="dc830-121">但是，如果您選擇具有錯誤資料類型的資料行，您將會得到錯誤或錯誤結果。</span><span class="sxs-lookup"><span data-stu-id="dc830-121">However, if you choose a column with the wrong the type of data you will either get an error or bad results.</span></span>  
  
### <a name="specify-the-outcome-to-predict"></a><span data-ttu-id="dc830-122">指定預測的結果</span><span class="sxs-lookup"><span data-stu-id="dc830-122">Specify the outcome to predict</span></span>  
  
1.  <span data-ttu-id="dc830-123">按兩下採礦結構，在資料採礦設計師中將它開啟。</span><span class="sxs-lookup"><span data-stu-id="dc830-123">Double-click the mining structure to open it in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="dc830-124">選取 **[採礦精確度圖表]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dc830-124">Select the **Mining Accuracy Chart** tab.</span></span>  
  
3.  <span data-ttu-id="dc830-125">選取 [輸入選擇]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dc830-125">Select the **Input Selection** tab.</span></span>  
  
4.  <span data-ttu-id="dc830-126">在 [輸入選擇]\*\*\*\* 索引標籤的 [可預測資料行名稱]\*\*\*\* 底下，針對併入圖表中的每個模型選取可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="dc830-126">On the **Input Selection** tab, under **Predictable Column Name**, select a predictable column for each model that you include in the chart.</span></span>  
  
     <span data-ttu-id="dc830-127">[可預測資料行名稱]\*\*\*\* 方塊中提供的採礦模型資料行只限於使用類型設定為 [預測]\*\*\*\* 或 [僅預測]\*\*\*\* 的資料行。</span><span class="sxs-lookup"><span data-stu-id="dc830-127">The mining model columns that are available in the **Predictable Column Name** box are only those with the usage type set to **Predict** or **Predict Only**.</span></span>  
  
5.  <span data-ttu-id="dc830-128">如果您要判斷模型的增益，您必須從 [預測值]\*\*\*\* 清單中選取要衡量的特定結果值。</span><span class="sxs-lookup"><span data-stu-id="dc830-128">If you want to determine the lift for a model, you must select a specific outcome value to measure, for by choosing from the **Predict Value** list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc830-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc830-129">See Also</span></span>  
 <span data-ttu-id="dc830-130">[選擇和對應模型測試資料](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="dc830-130">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 [<span data-ttu-id="dc830-131">選擇精確度圖表類型及設定圖表選項</span><span class="sxs-lookup"><span data-stu-id="dc830-131">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
