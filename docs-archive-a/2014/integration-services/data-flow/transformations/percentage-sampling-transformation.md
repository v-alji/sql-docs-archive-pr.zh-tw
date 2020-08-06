---
title: 百分比取樣轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e5fe41ecf4a2ca0f9d20eec2c8e10af8ed4cd47b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710782"
---
# <a name="percentage-sampling-transformation"></a><span data-ttu-id="358d7-102">百分比取樣轉換</span><span class="sxs-lookup"><span data-stu-id="358d7-102">Percentage Sampling Transformation</span></span>
  <span data-ttu-id="358d7-103">「百分比取樣」轉換會藉由選取轉換輸入資料列的一部分來建立取樣資料集。</span><span class="sxs-lookup"><span data-stu-id="358d7-103">The Percentage Sampling transformation creates a sample data set by selecting a percentage of the transformation input rows.</span></span> <span data-ttu-id="358d7-104">取樣資料集是從轉換輸出隨機選取的資料列，用來製作輸入的結果取樣代表。</span><span class="sxs-lookup"><span data-stu-id="358d7-104">The sample data set is a random selection of rows from the transformation input, to make the resultant sample representative of the input.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="358d7-105">除了指定的百分比之外，「百分比取樣」轉換還會使用演算法判斷某個資料列是否應包含在取樣輸出中。</span><span class="sxs-lookup"><span data-stu-id="358d7-105">In addition to the specified percentage, the Percentage Sampling transformation uses an algorithm to determine whether a row should be included in the sample output.</span></span> <span data-ttu-id="358d7-106">這表示取樣輸出中資料列的數目可能不會確實反映指定的百分比。</span><span class="sxs-lookup"><span data-stu-id="358d7-106">This means that the number of rows in the sample output may not exactly reflect the specified percentage.</span></span> <span data-ttu-id="358d7-107">例如，指定擁有 25,000 個資料列的輸入資料集的 10%，可能不會產生擁有 2,500 個資料列的取樣；取樣的資料列可能會稍微多一點或少一點。</span><span class="sxs-lookup"><span data-stu-id="358d7-107">For example, specifying 10 percent for an input data set that has 25,000 rows may not generate a sample with 2,500 rows; the sample may have a few more or a few less rows.</span></span>  
  
 <span data-ttu-id="358d7-108">「百分比取樣」轉換對於資料採礦來說特別實用。</span><span class="sxs-lookup"><span data-stu-id="358d7-108">The Percentage Sampling transformation is especially useful for data mining.</span></span> <span data-ttu-id="358d7-109">藉由使用此轉換，即可隨機將資料集細分成兩個資料集：一個用於培訓資料採礦模型，另一個用於測試模型。</span><span class="sxs-lookup"><span data-stu-id="358d7-109">By using this transformation, you can randomly divide a data set into two data sets: one for training the data mining model, and one for testing the model.</span></span>  
  
 <span data-ttu-id="358d7-110">「百分比取樣」轉換對於建立封裝開發作業的取樣資料集來說亦相當實用。</span><span class="sxs-lookup"><span data-stu-id="358d7-110">The Percentage Sampling transformation is also useful for creating sample data sets for package development.</span></span> <span data-ttu-id="358d7-111">藉由套用「百分比取樣」轉換至資料流程，即可一致減少資料集的大小，而同時保留其資料特性。</span><span class="sxs-lookup"><span data-stu-id="358d7-111">By applying the Percentage Sampling transformation to a data flow, you can uniformly reduce the size of the data set while preserving its data characteristics.</span></span> <span data-ttu-id="358d7-112">之後，測試封裝即可更快速地執行，因為它使用更小但更具代表性的資料集。</span><span class="sxs-lookup"><span data-stu-id="358d7-112">The test package can then run more quickly because it uses a small, but representative, data set.</span></span>  
  
## <a name="configuration-the-percentage-sampling-transformation"></a><span data-ttu-id="358d7-113">設定轉換取樣率</span><span class="sxs-lookup"><span data-stu-id="358d7-113">Configuration the Percentage Sampling Transformation</span></span>  
 <span data-ttu-id="358d7-114">您可以指定取樣種子 (Seed)，以修改轉換用來選取資料列的隨機號碼產生器的行為。</span><span class="sxs-lookup"><span data-stu-id="358d7-114">You can specify a sampling seed to modify the behavior of the random number generator that the transformation uses to select rows.</span></span> <span data-ttu-id="358d7-115">如果使用相同的取樣種子 (Seed)，轉換便會固定產生相同的取樣輸出。</span><span class="sxs-lookup"><span data-stu-id="358d7-115">If the same sampling seed is used, the transformation always creates the same sample output.</span></span> <span data-ttu-id="358d7-116">如果未指定種子，轉換會使用作業系統的滴答計數建立隨機號碼。</span><span class="sxs-lookup"><span data-stu-id="358d7-116">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="358d7-117">因此，當您要在開發和測試封裝的過程中驗證轉換結果時，可能會選擇使用標準種子，然後在封裝移至生產時改用隨機種子。</span><span class="sxs-lookup"><span data-stu-id="358d7-117">Therefore, you might choose to use a standard seed when you want to verify the transformation results during the development and testing of a package, and then change to use a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="358d7-118">此轉換與「資料列取樣」轉換相似，但後者是藉由選取指定的輸入資料列數目建立取樣資料集。</span><span class="sxs-lookup"><span data-stu-id="358d7-118">This transformation is similar to the Row Sampling transformation, which creates a sample data set by selecting a specified number of the input rows.</span></span> <span data-ttu-id="358d7-119">如需詳細資訊，請參閱 [資料列取樣轉換](row-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="358d7-119">For more information, see [Row Sampling Transformation](row-sampling-transformation.md).</span></span>  
  
 <span data-ttu-id="358d7-120">百分比取樣轉換包括 `SamplingValue` 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="358d7-120">The Percentage Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="358d7-121">屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="358d7-121">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="358d7-122">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md)和[轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="358d7-122">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="358d7-123">轉換有一個輸入和兩個輸出。</span><span class="sxs-lookup"><span data-stu-id="358d7-123">The transformation has one input and two outputs.</span></span> <span data-ttu-id="358d7-124">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="358d7-124">It does not support an error output.</span></span>  
  
 <span data-ttu-id="358d7-125">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="358d7-125">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="358d7-126">如需可在 [百分比取樣轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請參閱[百分比取樣轉換編輯器](../../percentage-sampling-transformation-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="358d7-126">For more information about the properties that you can set in the **Percentage Sampling Transformation Editor** dialog box, see [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="358d7-127">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="358d7-127">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="358d7-128">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="358d7-128">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="358d7-129">Common Properties</span><span class="sxs-lookup"><span data-stu-id="358d7-129">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="358d7-130">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="358d7-130">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="358d7-131">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](../set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="358d7-131">For more information about how to set properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
