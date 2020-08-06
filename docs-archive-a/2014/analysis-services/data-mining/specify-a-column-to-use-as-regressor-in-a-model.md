---
title: 在模型中指定當做回歸輸入變數使用的資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 86899d3793985b5e3c07618360d7b6a540935a54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584830"
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a><span data-ttu-id="ddb42-102">在模型中指定當做迴歸輸入變數使用的資料行</span><span class="sxs-lookup"><span data-stu-id="ddb42-102">Specify a Column to Use as Regressor in a Model</span></span>
  <span data-ttu-id="ddb42-103">線性迴歸模型會把可預測屬性的值表示為公式的結果，此公式結合輸入的方式會使資料盡可能地貼近預估迴歸線。</span><span class="sxs-lookup"><span data-stu-id="ddb42-103">A linear regression model represents the value of the predictable attribute as the result of a formula that combines the inputs in such a way that the data is fitted as a closely as possible to an estimated regression line.</span></span> <span data-ttu-id="ddb42-104">這種演算法只接受數值當做輸入，而且會自動偵測提供最佳解的輸入。</span><span class="sxs-lookup"><span data-stu-id="ddb42-104">The algorithm accepts only numeric values as inputs, and automatically detects the inputs that provide the best fit.</span></span>  
  
 <span data-ttu-id="ddb42-105">不過，您可以藉由將 FORCE_REGRESSOR 參數加入模型並且指定所使用的迴歸輸入變數，指定將資料行包含為迴歸輸入變數。</span><span class="sxs-lookup"><span data-stu-id="ddb42-105">However, you can specify that a column be included as a regressor by adding the FORCE_REGRESSOR parameter to the model and specifying the regressors to use.</span></span> <span data-ttu-id="ddb42-106">當屬性具有某種意義 (即使其效果過小而無法由模型偵測出來)，或者您想要確保屬性包含在公式中時，就可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="ddb42-106">You might want to do this in cases where the attribute has meaning even if the effect is too small to be detected by the model, or when you want to ensure that the attribute is included in the formula.</span></span>  
  
 <span data-ttu-id="ddb42-107">下列程序描述如何使用 [類神經網路教學課程](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)所使用的相同範例資料來建立簡單的線性迴歸模型。</span><span class="sxs-lookup"><span data-stu-id="ddb42-107">The following procedure describes how to create a simple linear regression model, using the same sample data that is used for the [neural networks tutorial](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="ddb42-108">此模型不一定很強固，但可以示範如何使用資料採礦設計師自訂線性迴歸模型。</span><span class="sxs-lookup"><span data-stu-id="ddb42-108">The model is not necessarily robust, but demonstrates how to use the Data Mining Designer to customize a linear regression model.</span></span>  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a><span data-ttu-id="ddb42-109">如何建立簡單的線性迴歸模型</span><span class="sxs-lookup"><span data-stu-id="ddb42-109">How to create a simple linear regression model</span></span>  
  
1.  <span data-ttu-id="ddb42-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的**方案總管**中，展開 [採礦結構]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddb42-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, expand **Mining Structures**.</span></span>  
  
2.  <span data-ttu-id="ddb42-111">在設計師中按兩下 Call Center.dmm 將其開啟。</span><span class="sxs-lookup"><span data-stu-id="ddb42-111">Double-click Call Center.dmm to open it in the designer.</span></span>  
  
3.  <span data-ttu-id="ddb42-112">從 [採礦模型]\*\*\*\* 功能表選取 [新增採礦模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddb42-112">From the **Mining Model** menu, select **New Mining Model**.</span></span>  
  
4.  <span data-ttu-id="ddb42-113">針對演算法選取 [Microsoft 線性迴歸]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddb42-113">For the algorithm, select **Microsoft Linear Regression**.</span></span> <span data-ttu-id="ddb42-114">輸入「撥接中心迴歸」\*\*\*\* 當作名稱。</span><span class="sxs-lookup"><span data-stu-id="ddb42-114">For the name, type **Call Center Regression**.</span></span>  
  
5.  <span data-ttu-id="ddb42-115">按照下列指示，在 [採礦模型]\*\*\*\* 索引標籤中變更資料行的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ddb42-115">In the **Mining Models** tab, change the column usage as follows.</span></span> <span data-ttu-id="ddb42-116">未列於下列清單的所有資料行都應該設定為 [忽略]\*\*\*\* (若尚未設定)。</span><span class="sxs-lookup"><span data-stu-id="ddb42-116">All columns not in the following list should be set to **Ignore**, if they are not already.</span></span>  
  
     <span data-ttu-id="ddb42-117">FactCallCenterID**Key**</span><span class="sxs-lookup"><span data-stu-id="ddb42-117">FactCallCenterID**Key**</span></span>  
  
     <span data-ttu-id="ddb42-118">ServiceGrade**PredictOnly**</span><span class="sxs-lookup"><span data-stu-id="ddb42-118">ServiceGrade**PredictOnly**</span></span>  
  
     <span data-ttu-id="ddb42-119">Total Operators**Input**</span><span class="sxs-lookup"><span data-stu-id="ddb42-119">Total Operators**Input**</span></span>  
  
     <span data-ttu-id="ddb42-120">AverageTimePerIssue**Input**</span><span class="sxs-lookup"><span data-stu-id="ddb42-120">AverageTimePerIssue**Input**</span></span>  
  
6.  <span data-ttu-id="ddb42-121">從 [採礦模型]\*\*\*\* 功能表選取 [Set Model Parameters (設定模型參數)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddb42-121">From the **Mining Model** menu, select **Set Model Parameters**.</span></span>  
  
7.  <span data-ttu-id="ddb42-122">針對 FORCE_REGRESSOR 參數，在 [值]\*\*\*\* 資料行中輸入資料行名稱 (將名稱放入方括弧並以逗號分隔)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ddb42-122">For the parameter, FORCE_REGRESSOR, in the **Value** column, type the column names enclosed in brackets and separated by a comma, as follows:</span></span>  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="ddb42-123">演算法將會自動偵測可做為最佳迴歸輸入變數的資料行。</span><span class="sxs-lookup"><span data-stu-id="ddb42-123">The algorithm will automatically detect which columns are the best regressors.</span></span> <span data-ttu-id="ddb42-124">當您想要確定最終公式中是否包含了某資料行時，只需強制使用迴歸輸入變數即可。</span><span class="sxs-lookup"><span data-stu-id="ddb42-124">You only need to force regressors when you want to ensure that a column is included in the final formula.</span></span>  
  
8.  <span data-ttu-id="ddb42-125">從 [採礦模型]\*\*\*\* 功能表選取 [處理模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddb42-125">From the **Mining Model** menu, select **Process Model**.</span></span>  
  
     <span data-ttu-id="ddb42-126">在檢視器中，模型會以包含迴歸公式的單一節點來表示。</span><span class="sxs-lookup"><span data-stu-id="ddb42-126">In the viewer, the model is represented a single node containing the regression formula.</span></span> <span data-ttu-id="ddb42-127">您可以在 [採礦圖例]\*\*\*\* 中檢視公式，或者也可以藉由使用查詢來擷取公式的係數。</span><span class="sxs-lookup"><span data-stu-id="ddb42-127">You can view the formula in the **Mining Legend**, or you can extract the coefficients for the formula by using queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb42-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddb42-128">See Also</span></span>  
 <span data-ttu-id="ddb42-129">[Microsoft 線性回歸演算法](microsoft-linear-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="ddb42-129">[Microsoft Linear Regression Algorithm](microsoft-linear-regression-algorithm.md) </span></span>  
 <span data-ttu-id="ddb42-130">[資料採礦查詢](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="ddb42-130">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="ddb42-131">[Microsoft 線性回歸演算法技術參考](microsoft-linear-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ddb42-131">[Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="ddb42-132">線性迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="ddb42-132">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  
