---
title: 建立測試集 (資料採礦嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.holdout.f1
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab22597224f5c6c6006a02af81fa6583886d93b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596409"
---
# <a name="create-testing-set-data-mining-wizard"></a><span data-ttu-id="52dec-102">建立測試集 (資料採礦精靈)</span><span class="sxs-lookup"><span data-stu-id="52dec-102">Create Testing Set (Data Mining Wizard)</span></span>
  <span data-ttu-id="52dec-103">使用 [建立測試集]\*\*\*\* 頁面來指定用於定型的資料量，以及保留用於測試集的資料量。</span><span class="sxs-lookup"><span data-stu-id="52dec-103">Use the **Create Testing Set** page to specify how much of the data is to be used for training, and how much is to be reserved for use as a test set.</span></span> <span data-ttu-id="52dec-104">在建立採礦結構時將資料分割成定型集和測試集，可以更輕鬆地評估您稍後建立的採礦模型的正確性。</span><span class="sxs-lookup"><span data-stu-id="52dec-104">Separating data into a training and testing set when you create a mining structure makes it much easier to assess the accuracy of mining models that you create later.</span></span>  
  
 <span data-ttu-id="52dec-105">您可以將測試資料量指定為百分比，或者可以指定數字以限制用於測試的案例數。</span><span class="sxs-lookup"><span data-stu-id="52dec-105">You can specify the amount of testing data as a percentage, or you can specify a number to limit the number of cases used for testing.</span></span> <span data-ttu-id="52dec-106">如果同時指定了用於測試的案例百分比以及案例數上限，則這兩種設定都會使用，且測試資料集會包含較少的案例數。</span><span class="sxs-lookup"><span data-stu-id="52dec-106">If you specify both a percentage and a maximum number of cases to use for testing, both settings are used, and the testing data set contains the smaller number of cases.</span></span> <span data-ttu-id="52dec-107">根據預設，測試會使用 30% 的資料，定型則使用 70%，且測試案例數沒有上限。</span><span class="sxs-lookup"><span data-stu-id="52dec-107">By default, 30 percent of data is used for testing, 70 percent for training, and there is no maximum number of test cases.</span></span>  
  
 <span data-ttu-id="52dec-108">根據預設， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會產生用來啟動資料分割的數值種子。</span><span class="sxs-lookup"><span data-stu-id="52dec-108">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates a numeric seed that is used to start partitioning.</span></span> <span data-ttu-id="52dec-109">此種子是根據採礦結構的名稱而定。</span><span class="sxs-lookup"><span data-stu-id="52dec-109">This seed is based on the name of the mining structure.</span></span> <span data-ttu-id="52dec-110">如果想要在採礦結構的名稱變更時仍確保資料分割維持相同狀況，可以設定採礦結構的 HoldoutSeed 屬性來指定種子的值。</span><span class="sxs-lookup"><span data-stu-id="52dec-110">If you want to ensure that the partition stays the same even if the name of the mining structure is changed, you can specify a value for the seed, by setting the HoldoutSeed property of the mining structure.</span></span> <span data-ttu-id="52dec-111">如果變更鑑效組種子，則必須重新處理結構。</span><span class="sxs-lookup"><span data-stu-id="52dec-111">If you change the holdout seed, you must reprocess the structure.</span></span>  
  
 <span data-ttu-id="52dec-112">如果您稍後想要變更測試或定型資料的數量，您可以 `HoldoutMaxCases` `HoldoutMaxPercent` 使用 [**屬性**] 視窗來修改資料採礦結構上的和屬性。</span><span class="sxs-lookup"><span data-stu-id="52dec-112">If you later want to change the amount of testing or training data, you can modify the `HoldoutMaxCases` and `HoldoutMaxPercent` properties on the data mining structure by using the **Properties** window.</span></span> <span data-ttu-id="52dec-113">不過，在進行變更後，必須重新處理採礦結構及所有相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="52dec-113">However, after you make the change you must reprocess the mining structure and all associated mining models.</span></span> <span data-ttu-id="52dec-114">同時適用下列限制：</span><span class="sxs-lookup"><span data-stu-id="52dec-114">The following limitations also apply:</span></span>  
  
-   <span data-ttu-id="52dec-115">只有當資料採礦結構是儲存於 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]時，才支援資料採礦結構的資料分割。</span><span class="sxs-lookup"><span data-stu-id="52dec-115">Partitioning of a data mining structure is supported only when the data mining structure is stored in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="52dec-116">舊版的不支援快取資料 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 分割資訊，以進行採礦結構。</span><span class="sxs-lookup"><span data-stu-id="52dec-116">Earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] do not support caching of partition information for mining structures.</span></span>  
  
-   <span data-ttu-id="52dec-117">如果採礦結構包含 Key Time 資料行 (必須用於時間序列採礦模型)，則無法對採礦結構進行資料分割。</span><span class="sxs-lookup"><span data-stu-id="52dec-117">You cannot partition a mining structure if the mining structure contains a Key Time column, which is required for time series mining models.</span></span>  
  
-   <span data-ttu-id="52dec-118">如果想要預測儲存於巢狀資料表中的值，則無法分割資料。</span><span class="sxs-lookup"><span data-stu-id="52dec-118">You cannot partition data if you are trying to predict a value that is stored in a nested table.</span></span>  
  
 <span data-ttu-id="52dec-119">**如需詳細資訊，請參閱** [測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md)、[建立關聯式採礦結構](data-mining/create-a-relational-mining-structure.md)、[資料採礦基本教學課程](../../2014/tutorials/basic-data-mining-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="52dec-119">**For More Information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md), [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="52dec-120">選項</span><span class="sxs-lookup"><span data-stu-id="52dec-120">Options</span></span>  
 <span data-ttu-id="52dec-121">**測試資料的百分比**</span><span class="sxs-lookup"><span data-stu-id="52dec-121">**Percentage of data for testing**</span></span>  
 <span data-ttu-id="52dec-122">請按一下向上或向下箭號來增加或減少用來當做定型集的資料百分比，或在文字方塊中輸入 0 和 100 之間的值。</span><span class="sxs-lookup"><span data-stu-id="52dec-122">Click the up and down arrows to increase or decrease the percentage of data to use as a training set, or type a value between 0 and 100 in the text box.</span></span>  
  
 <span data-ttu-id="52dec-123">**測試資料集中的案例數上限**</span><span class="sxs-lookup"><span data-stu-id="52dec-123">**Maximum number of cases in testing data set**</span></span>  
 <span data-ttu-id="52dec-124">輸入數字，以限制可用於測試的案例數。</span><span class="sxs-lookup"><span data-stu-id="52dec-124">Type a number to limit the number of cases that can be used for testing.</span></span>  
  
 <span data-ttu-id="52dec-125">如果指定的值大於資料中的實際案例數，就會使用所有的案例。</span><span class="sxs-lookup"><span data-stu-id="52dec-125">If you specify a number that is larger than the number of actual cases in the data, all the cases will be used.</span></span>  
  
 <span data-ttu-id="52dec-126">預設值是 NULL。</span><span class="sxs-lookup"><span data-stu-id="52dec-126">The default is NULL.</span></span> <span data-ttu-id="52dec-127">這表示沒有限制。</span><span class="sxs-lookup"><span data-stu-id="52dec-127">This means there is no limit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52dec-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52dec-128">See Also</span></span>  
 <span data-ttu-id="52dec-129">[資料採礦嚮導 F1 說明 &#40;Analysis Services-資料採礦&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="52dec-129">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="52dec-130">[建議相關資料行 &#40;Data 採集 Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="52dec-130">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="52dec-131">[指定資料表類型 &#40;資料採礦嚮導&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="52dec-131">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="52dec-132">[指定資料行的內容和資料類型 &#40;[Data] [Wizard]&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)</span><span class="sxs-lookup"><span data-stu-id="52dec-132">[Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)</span></span>  
  
  
