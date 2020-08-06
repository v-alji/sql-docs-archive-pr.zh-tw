---
title: 資料列取樣轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowsamplingtrans.f1
helpviewer_keywords:
- sampling seeds [Integration Services]
- random seeds
- random sampling
- sample data sets [Integration Services]
- Row Sampling transformation
- packages [Integration Services], samples
- datasets [Integration Services], sample
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c56f07d9fafa03752ef8c6572a13c6ad7c02a8c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710777"
---
# <a name="row-sampling-transformation"></a><span data-ttu-id="fc3ba-102">資料列取樣轉換</span><span class="sxs-lookup"><span data-stu-id="fc3ba-102">Row Sampling Transformation</span></span>
  <span data-ttu-id="fc3ba-103">「資料列取樣」轉換是用來取得隨機選取的輸入資料集子集。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-103">The Row Sampling transformation is used to obtain a randomly selected subset of an input dataset.</span></span> <span data-ttu-id="fc3ba-104">您可以指定輸出範例的確實大小，以及指定隨機號碼產生器的種子資料 (Seed)。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-104">You can specify the exact size of the output sample, and specify a seed for the random number generator.</span></span>  
  
 <span data-ttu-id="fc3ba-105">可用於隨機取樣的應用程式有許多種。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-105">There are many applications for random sampling.</span></span> <span data-ttu-id="fc3ba-106">例如，某公司希望隨機選取 50 名員工接受抽獎獎項，即可在員工資料庫上使用「資料列取樣」轉換產生正確的獲獎者數目。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-106">For example, a company that wanted to randomly select 50 employees to receive prizes in a lottery could use the Row Sampling transformation on the employee database to generate the exact number of winners.</span></span>  
  
 <span data-ttu-id="fc3ba-107">在封裝部署期間，「資料列取樣」轉換對於建立小型但具代表性的資料集來說亦相當實用。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-107">The Row Sampling transformation is also useful during package development for creating a small but representative dataset.</span></span> <span data-ttu-id="fc3ba-108">您可以運用豐富的代表性資料測試封裝執行和資料庫轉換，而由於使用隨機取樣而非整個資料集，因此速度更快。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-108">You can test package execution and data transformation with richly representative data, but more quickly because a random sample is used instead of the full dataset.</span></span> <span data-ttu-id="fc3ba-109">由於測試封裝所使用的取樣資料集大小始終相同，因此使用取樣子集亦可讓識別封裝中的效能問題更為容易。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-109">Because the sample dataset used by the test package is always the same size, using the sample subset also makes it easier to identify performance problems in the package.</span></span>  
  
 <span data-ttu-id="fc3ba-110">此轉換與「百分比取樣」轉換相似，但後者是藉由選取某個百分比的輸入資料列建立取樣資料集。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-110">This transformation is similar to the Percentage Sampling transformation, which creates a sample dataset by selecting a percentage of the input rows.</span></span> <span data-ttu-id="fc3ba-111">請參閱 [百分比取樣轉換](percentage-sampling-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-111">See [Percentage Sampling Transformation](percentage-sampling-transformation.md).</span></span>  
  
## <a name="configuring-the-row-sampling-transformation"></a><span data-ttu-id="fc3ba-112">設定資料列取樣轉換</span><span class="sxs-lookup"><span data-stu-id="fc3ba-112">Configuring the Row Sampling Transformation</span></span>  
 <span data-ttu-id="fc3ba-113">「資料列取樣」轉換會藉由選取指定數目的轉換輸入資料列來建立取樣資料集。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-113">The Row Sampling transformation creates a sample dataset by selecting a specified number of the transformation input rows.</span></span> <span data-ttu-id="fc3ba-114">由於是從轉換輸入隨機選取資料列，因此結果取樣即為輸入的代表。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-114">Because the selection of rows from the transformation input is random, the resultant sample is representative of the input.</span></span> <span data-ttu-id="fc3ba-115">您也可以指定隨機號碼產生器使用的種子資料，以影響轉換選取資料列的方式。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-115">You can also specify the seed that is used by the random number generator, to affect how the transformation selects rows.</span></span>  
  
 <span data-ttu-id="fc3ba-116">使用相同轉換輸入上的相同隨機種子資料，會固定建立相同的取樣輸出。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-116">Using the same random seed on the same transformation input always creates the same sample output.</span></span> <span data-ttu-id="fc3ba-117">如果未指定種子，轉換會使用作業系統的滴答計數建立隨機號碼。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-117">If no seed is specified, the transformation uses the tick count of the operating system to create the random number.</span></span> <span data-ttu-id="fc3ba-118">因此，您可以在測試過程中使用相同的種子，以便在開發和測試封裝期間驗證轉換結果，然後在封裝移至實際執行階段時變更為隨機種子。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-118">Therefore, you could use the same seed during testing, to verify the transformation results during the development and testing of the package, and then change to a random seed when the package is moved into production.</span></span>  
  
 <span data-ttu-id="fc3ba-119">資料列取樣轉換包括 `SamplingValue` 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-119">The Row Sampling transformation includes the `SamplingValue` custom property.</span></span> <span data-ttu-id="fc3ba-120">屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-120">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="fc3ba-121">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md)和[轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-121">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="fc3ba-122">此轉換有一個輸入和兩個輸出。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-122">This transformation has one input and two outputs.</span></span> <span data-ttu-id="fc3ba-123">但沒有錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-123">It has no error output.</span></span>  
  
 <span data-ttu-id="fc3ba-124">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="fc3ba-125">如需可在 [資料列取樣轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請參閱[資料列取樣轉換編輯器 &#40;取樣頁面&#41;](../../row-sampling-transformation-editor-sampling-page.md)。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-125">For more information about the properties that you can set in the **Row Sampling Transformation Editor** dialog box, see [Row Sampling Transformation Editor &#40;Sampling Page&#41;](../../row-sampling-transformation-editor-sampling-page.md).</span></span>  
  
 <span data-ttu-id="fc3ba-126">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="fc3ba-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="fc3ba-127">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="fc3ba-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="fc3ba-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="fc3ba-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="fc3ba-129">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="fc3ba-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="fc3ba-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="fc3ba-130">Related Tasks</span></span>  
 [<span data-ttu-id="fc3ba-131">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="fc3ba-131">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
  
