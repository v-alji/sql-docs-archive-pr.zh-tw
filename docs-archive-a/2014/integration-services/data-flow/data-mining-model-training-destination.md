---
title: 資料採礦模型定型目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingmodeltrainingdest.f1
helpviewer_keywords:
- destinations [Integration Services], Data Mining Model Training
- Data Mining Model Training destination
- mining models [Analysis Services], training
- training mining models
ms.assetid: 6bc8cbe2-46af-4f7b-93d6-86779313c9d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e101a7e374f16b12b3a5aa30a49dbecd2632f06f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596832"
---
# <a name="data-mining-model-training-destination"></a><span data-ttu-id="ab962-102">資料採礦模型定型目的地</span><span class="sxs-lookup"><span data-stu-id="ab962-102">Data Mining Model Training Destination</span></span>
  <span data-ttu-id="ab962-103">「資料採礦模型培訓」目的地藉由傳送目的地接收的資料至資料採礦模型演算法，來培訓資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ab962-103">The Data Mining Model Training destination trains data mining models by passing the data that the destination receives through the data mining model algorithms.</span></span> <span data-ttu-id="ab962-104">如果多個資料採礦模型建立於同一資料採礦結構上，則可以由一個目的地來培訓這些模型。</span><span class="sxs-lookup"><span data-stu-id="ab962-104">Multiple data mining models can be trained by one destination if the models are built on the same data mining structure.</span></span> <span data-ttu-id="ab962-105">如需詳細資訊，請參閱 [採礦結構資料行](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) 和 [採礦模型資料行](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns)。</span><span class="sxs-lookup"><span data-stu-id="ab962-105">For more information, see [Mining Structure Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-structure-columns) and [Mining Model Columns](https://docs.microsoft.com/analysis-services/data-mining/mining-model-columns).</span></span>  
  
## <a name="configuration-of-the-data-mining-model-training-destination"></a><span data-ttu-id="ab962-106">設定資料採礦模型培訓目的地</span><span class="sxs-lookup"><span data-stu-id="ab962-106">Configuration of the Data Mining Model Training Destination</span></span>  
 <span data-ttu-id="ab962-107">如果目標結構和建立於此結構上之模型的案例層級資料行具有 KEY TIME 或 KEY SEQUENCE 類型之內容，則輸入資料必須在該資料行上排序。</span><span class="sxs-lookup"><span data-stu-id="ab962-107">If a case level column of the target structure and the models built on the structure has the content type KEY TIME or KEY SEQUENCE, the input data must be sorted on that column.</span></span> <span data-ttu-id="ab962-108">例如，使用「Microsoft 時間序列」演算法建立之模型使用的內容類型為 KEY TIME。</span><span class="sxs-lookup"><span data-stu-id="ab962-108">For example, models built using the Microsoft Time Series algorithm use the content type KEY TIME.</span></span> <span data-ttu-id="ab962-109">如果輸入資料未排序，則模型的處理可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="ab962-109">If input data is not sorted, the processing of the model may fail.</span></span> <span data-ttu-id="ab962-110">如果資料需要排序，您可使用先前在資料流程中描述的「排序」轉換來排序資料。</span><span class="sxs-lookup"><span data-stu-id="ab962-110">If the data requires sorting, you can use a Sort transformation earlier in the data flow to sort the data.</span></span> <span data-ttu-id="ab962-111">此需求不會套用至內容類型為 KEY 的資料行。</span><span class="sxs-lookup"><span data-stu-id="ab962-111">This requirement does not apply to columns with the KEY content type.</span></span> <span data-ttu-id="ab962-112">如需詳細資訊，請參閱[內容類型 &#40;資料採礦&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) 和[排序轉換](transformations/sort-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="ab962-112">For more information, see [Content Types &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-types-data-mining) and [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab962-113">「資料採礦模型培訓」目的地的輸入必須排序。</span><span class="sxs-lookup"><span data-stu-id="ab962-113">The input to the Data Mining Model training destination must be sorted.</span></span> <span data-ttu-id="ab962-114">若要排序資料，您可以將「資料採礦模型培訓」目的地上游的「排序」目的地併入資料流程中。</span><span class="sxs-lookup"><span data-stu-id="ab962-114">To sort the data, you can include a Sort destination upstream from the Data Mining Model Training destination in the data flow.</span></span> <span data-ttu-id="ab962-115">如需詳細資訊，請參閱 [排序轉換](transformations/sort-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="ab962-115">For more information, see [Sort Transformation](transformations/sort-transformation.md).</span></span>  
  
 <span data-ttu-id="ab962-116">此目的地有一個輸入，但沒有輸出。</span><span class="sxs-lookup"><span data-stu-id="ab962-116">This destination has one input and no output.</span></span>  
  
 <span data-ttu-id="ab962-117">「資料採礦模型定型」目的地會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連線管理員來連線到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體，其中包含目的地所定型的採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="ab962-117">The Data Mining Model Training destination uses an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that contains the mining structure and mining models that the destination trains.</span></span> <span data-ttu-id="ab962-118">如需相關資訊，請參閱 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ab962-118">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 <span data-ttu-id="ab962-119">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="ab962-119">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ab962-120">如需可在 [資料採礦模型培訓編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按一下下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="ab962-120">For more information about the properties that you can set in the **Data Mining Model Training Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ab962-121">資料採礦模型培訓編輯器 &#40;連接索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="ab962-121">Data Mining Model Training Editor &#40;Connection Tab&#41;</span></span>](../data-mining-model-training-editor-connection-tab.md)  
  
-   [<span data-ttu-id="ab962-122">資料採礦模型培訓編輯器 &#40;資料行索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="ab962-122">Data Mining Model Training Editor &#40;Columns Tab&#41;</span></span>](../data-mining-model-training-editor-columns-tab.md)  
  
 <span data-ttu-id="ab962-123">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="ab962-123">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="ab962-124">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="ab962-124">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ab962-125">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ab962-125">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="ab962-126">資料採礦模型定型目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="ab962-126">Data Mining Model Training Destination Custom Properties</span></span>](data-mining-model-training-destination-custom-properties.md)  
  
 <span data-ttu-id="ab962-127">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ab962-127">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
