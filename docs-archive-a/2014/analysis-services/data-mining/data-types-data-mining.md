---
title: 資料類型 (資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9027ff3928f40d43f16bb31b52e0c1d52e072847
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607161"
---
# <a name="data-types-data-mining"></a><span data-ttu-id="8ec50-102">資料類型 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="8ec50-102">Data Types (Data Mining)</span></span>
  <span data-ttu-id="8ec50-103">當您在中建立採礦模型或採礦結構時 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您必須為該採礦結構中的每個資料行定義資料類型。</span><span class="sxs-lookup"><span data-stu-id="8ec50-103">When you create a mining model or a mining structure in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you must define the data types for each of the columns in the mining structure.</span></span> <span data-ttu-id="8ec50-104">此資料類型會告訴資料採礦引擎，資料來源中的資料是數值還是文字，以及應該如何處理資料。</span><span class="sxs-lookup"><span data-stu-id="8ec50-104">The data type tells the data mining engine whether the data in the data source is numerical or text, and how the data should be processed.</span></span> <span data-ttu-id="8ec50-105">例如，如果您的來源資料包含數值資料，您可以指定數字應該視為整數還是使用小數位數。</span><span class="sxs-lookup"><span data-stu-id="8ec50-105">For example, if your source data contains numerical data, you can specify whether the numbers be treated as integers or by using decimal places.</span></span>  
  
 <span data-ttu-id="8ec50-106">每一個資料類型都會支援一個或多個內容類型。</span><span class="sxs-lookup"><span data-stu-id="8ec50-106">Each data type supports one or more content types.</span></span> <span data-ttu-id="8ec50-107">藉由設定內容類型，您可以自訂處理資料行資料的方式或是計算採礦模型資料的方式。</span><span class="sxs-lookup"><span data-stu-id="8ec50-107">By setting the content type, you can customize the way that data in the column is processed or calculated in the mining model.</span></span>  
  
 <span data-ttu-id="8ec50-108">例如，如果您在資料行中有數值資料，您可以選擇將資料當做數值或文字資料類型來處理。</span><span class="sxs-lookup"><span data-stu-id="8ec50-108">For example, if you have numeric data in a column, you can choose to handle it either as a numeric or text data type.</span></span> <span data-ttu-id="8ec50-109">如果您選擇數值資料類型，您可以設定幾種不同的內容類型：您可以離散化數字，或是將數字當做連續值來處理。</span><span class="sxs-lookup"><span data-stu-id="8ec50-109">If you choose the numeric data type, you can set several different content types: you can discretize the numbers, or handle them as continuous values.</span></span> <span data-ttu-id="8ec50-110">如需所有內容類型的清單，請參閱 [內容類型 &#40;資料採礦&#41;](content-types-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="8ec50-110">For a list of all the content types, see [Content Types &#40;Data Mining&#41;](content-types-data-mining.md).</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8ec50-111">支援以下採礦結構資料行的資料類型：</span><span class="sxs-lookup"><span data-stu-id="8ec50-111">supports the following data types for mining structure columns:</span></span>  
  
|<span data-ttu-id="8ec50-112">資料類型</span><span class="sxs-lookup"><span data-stu-id="8ec50-112">Data Type</span></span>|<span data-ttu-id="8ec50-113">支援的內容類型</span><span class="sxs-lookup"><span data-stu-id="8ec50-113">Supported Content Types</span></span>|  
|---------------|-----------------------------|  
|`Text`|<span data-ttu-id="8ec50-114">Cyclical、Discrete、Discretized、Key Sequence、Ordered、Sequence</span><span class="sxs-lookup"><span data-stu-id="8ec50-114">Cyclical, Discrete, Discretized, Key Sequence, Ordered, Sequence</span></span>|  
|`Long`|<span data-ttu-id="8ec50-115">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence、Time</span><span class="sxs-lookup"><span data-stu-id="8ec50-115">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="8ec50-116">Classified</span><span class="sxs-lookup"><span data-stu-id="8ec50-116">Classified</span></span>|  
|`Boolean`|<span data-ttu-id="8ec50-117">Cyclical、Discrete、Ordered</span><span class="sxs-lookup"><span data-stu-id="8ec50-117">Cyclical, Discrete, Ordered</span></span>|  
|`Double`|<span data-ttu-id="8ec50-118">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered、Sequence、Time</span><span class="sxs-lookup"><span data-stu-id="8ec50-118">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered, Sequence, Time</span></span><br /><br /> <span data-ttu-id="8ec50-119">Classified</span><span class="sxs-lookup"><span data-stu-id="8ec50-119">Classified</span></span>|  
|`Date`|<span data-ttu-id="8ec50-120">Continuous、Cyclical、Discrete、Discretized、Key、Key Sequence、Key Time、Ordered</span><span class="sxs-lookup"><span data-stu-id="8ec50-120">Continuous, Cyclical, Discrete, Discretized, Key, Key Sequence, Key Time, Ordered</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="8ec50-121">只有協力廠商演算法才支援 Time 和 Sequence 內容類型。</span><span class="sxs-lookup"><span data-stu-id="8ec50-121">The Time and Sequence content types are only supported by third-party algorithms.</span></span> <span data-ttu-id="8ec50-122">系統支援 Cyclical 和 Ordered 內容類型，但是大部分的演算法將它們視為離散值，因此不會執行特殊處理。</span><span class="sxs-lookup"><span data-stu-id="8ec50-122">The Cyclical and Ordered content types are supported, but most algorithms treat them as discrete values and do not perform special processing.</span></span>  
  
## <a name="specifying-a-data-type"></a><span data-ttu-id="8ec50-123">指定資料類型</span><span class="sxs-lookup"><span data-stu-id="8ec50-123">Specifying a Data Type</span></span>  
 <span data-ttu-id="8ec50-124">如果您使用資料採礦延伸模組 (DMX) 直接建立採礦模型，當您定義此模型時，可以針對每一個資料行定義資料類型，而且 Analysis Services 將會同時建立具有指定之資料類型的對應採礦結構。</span><span class="sxs-lookup"><span data-stu-id="8ec50-124">If you create the mining model directly by using Data Mining Extensions (DMX), you can define the data type for each column as you define the model, and Analysis Services will create the corresponding mining structure with the specified data types at the same time.</span></span> <span data-ttu-id="8ec50-125">如果您使用精靈建立採礦模型或採礦結構，Analysis Services 將會建議一個資料類型，或者，您也可以從清單中選擇資料類型。</span><span class="sxs-lookup"><span data-stu-id="8ec50-125">If you create the mining model or mining structure by using a wizard, Analysis Services will suggest a data type, or you can choose a data type from a list.</span></span>  
  
## <a name="changing-a-data-type"></a><span data-ttu-id="8ec50-126">變更資料類型</span><span class="sxs-lookup"><span data-stu-id="8ec50-126">Changing a Data Type</span></span>  
 <span data-ttu-id="8ec50-127">如果您變更資料行的資料類型，一定要重新處理採礦結構及根據該結構的任何採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8ec50-127">If you change the data type of a column, you must always reprocess the mining structure and any mining models that are based on that structure.</span></span> <span data-ttu-id="8ec50-128">有時當您變更資料類型時，該資料行就不能再用於特定的模型中。</span><span class="sxs-lookup"><span data-stu-id="8ec50-128">Sometimes if you change the data type, that column can no longer be used in a particular model.</span></span> <span data-ttu-id="8ec50-129">在這種情況下，當您重新處理模型時，Analysis Services 將會引發錯誤，或是處理此模型，但是不處理該特定資料行。</span><span class="sxs-lookup"><span data-stu-id="8ec50-129">In that case, Analysis Services will either raise an error when you reprocess the model, or will process the model but leave out that particular column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec50-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ec50-130">See Also</span></span>  
 <span data-ttu-id="8ec50-131">[&#40;資料採礦&#41;的內容類型](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8ec50-131">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="8ec50-132">[DMX&#41;&#40;內容類型](/sql/dmx/content-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="8ec50-132">[Content Types &#40;DMX&#41;](/sql/dmx/content-types-dmx) </span></span>  
 <span data-ttu-id="8ec50-133">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8ec50-133">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8ec50-134">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8ec50-134">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="8ec50-135">[DMX&#41;的資料類型 &#40;](/sql/dmx/data-types-dmx) </span><span class="sxs-lookup"><span data-stu-id="8ec50-135">[Data Types &#40;DMX&#41;](/sql/dmx/data-types-dmx) </span></span>  
 <span data-ttu-id="8ec50-136">[採礦模型資料行](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="8ec50-136">[Mining Model Columns](mining-model-columns.md) </span></span>  
 [<span data-ttu-id="8ec50-137">採礦結構資料行</span><span class="sxs-lookup"><span data-stu-id="8ec50-137">Mining Structure Columns</span></span>](mining-structure-columns.md)  
  
  
