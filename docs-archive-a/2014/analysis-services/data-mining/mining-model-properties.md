---
title: 採礦模型屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- data mining [Analysis Services], properties
- columns [data mining], properties
- Data Mining Designer
- properties [data mining]
ms.assetid: c5194619-8b31-42be-a95f-585711462945
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb086f4a978ca96de8e6fc99f889f718247629af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598656"
---
# <a name="mining-model-properties"></a><span data-ttu-id="a057b-102">採礦模型屬性</span><span class="sxs-lookup"><span data-stu-id="a057b-102">Mining Model Properties</span></span>
  <span data-ttu-id="a057b-103">採礦模型具有以下種類的屬性：</span><span class="sxs-lookup"><span data-stu-id="a057b-103">Mining models have the following kinds of properties:</span></span>  
  
-   <span data-ttu-id="a057b-104">繼承自採礦結構的屬性，這些屬性可定義此模型所使用之資料的資料類型和內容類型。</span><span class="sxs-lookup"><span data-stu-id="a057b-104">Properties that are inherited from the mining structure that define the data type and content type of the data used by the model;</span></span>  
  
-   <span data-ttu-id="a057b-105">與用來建立採礦模型之演算法相關的屬性，包括任何客戶參數。</span><span class="sxs-lookup"><span data-stu-id="a057b-105">Properties that are related to the algorithm used to create the mining model, including any customer parameters;</span></span>  
  
-   <span data-ttu-id="a057b-106">在模型上定義篩選的屬性，可用來定型模型。</span><span class="sxs-lookup"><span data-stu-id="a057b-106">Properties that define a filter on the model used to train the model.</span></span>  
  
 <span data-ttu-id="a057b-107">採礦模型的屬性一開始是在您建立模型時所定義；但是，您之後可以更改大多數的屬性，包括演算法參數、篩選以及資料行使用方式屬性。</span><span class="sxs-lookup"><span data-stu-id="a057b-107">The properties of a mining model are initially defined when you create the model; however, you can alter most properties later, including the algorithm parameters, filters, and column usage properties.</span></span> <span data-ttu-id="a057b-108">您可藉由使用資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤或使用 AMO 或 XMLA 來變更屬性。</span><span class="sxs-lookup"><span data-stu-id="a057b-108">You change properties by using the **Mining Models** tab of Data Mining Designer, or by using AMO or XMLA.</span></span>  
  
 <span data-ttu-id="a057b-109">每當您變更模型的任何屬性時，您都必須重新處理模型，才能在模型中反映變更。</span><span class="sxs-lookup"><span data-stu-id="a057b-109">Whenever you change any property of a model, you must reprocess the model for the changes to be reflected in the model.</span></span> <span data-ttu-id="a057b-110">即使變更只牽涉到中繼資料 (例如資料行別名或描述)，也需要重新處理。</span><span class="sxs-lookup"><span data-stu-id="a057b-110">Reprocessing is required even if the change only involves metadata, such as adding a column alias or description.</span></span>  
  
## <a name="properties-of-models"></a><span data-ttu-id="a057b-111">模型的屬性</span><span class="sxs-lookup"><span data-stu-id="a057b-111">Properties of Models</span></span>  
 <span data-ttu-id="a057b-112">下表描述採礦模型特有的屬性。</span><span class="sxs-lookup"><span data-stu-id="a057b-112">The following table describes the properties that are specific to mining models.</span></span> <span data-ttu-id="a057b-113">此外，也有一些屬性可以在採礦的個別資料行中設定。</span><span class="sxs-lookup"><span data-stu-id="a057b-113">Additionally, there are properties that you can set on individual columns in the mining</span></span>  
  
|<span data-ttu-id="a057b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a057b-114">Property</span></span>|<span data-ttu-id="a057b-115">描述</span><span class="sxs-lookup"><span data-stu-id="a057b-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a057b-116">**演算法**</span><span class="sxs-lookup"><span data-stu-id="a057b-116">**Algorithm**</span></span>|<span data-ttu-id="a057b-117">設定採礦模型的演算法類型。</span><span class="sxs-lookup"><span data-stu-id="a057b-117">Sets the algorithm type for the mining model.</span></span>|  
|<span data-ttu-id="a057b-118">**AlgorithmParameters**</span><span class="sxs-lookup"><span data-stu-id="a057b-118">**AlgorithmParameters**</span></span>|<span data-ttu-id="a057b-119">設定每一種演算法類型可用的演算法參數的值。</span><span class="sxs-lookup"><span data-stu-id="a057b-119">Sets values for algorithm parameters that are available for each algorithm type.</span></span>|  
|<span data-ttu-id="a057b-120">**Filter**</span><span class="sxs-lookup"><span data-stu-id="a057b-120">**Filter**</span></span>|<span data-ttu-id="a057b-121">設定篩選以套用至用於培訓及測試採礦模型的資料。</span><span class="sxs-lookup"><span data-stu-id="a057b-121">Sets a filter that is applied to the data that is used for training and testing the mining model.</span></span> <span data-ttu-id="a057b-122">篩選定義會與模型一起儲存，並在建立預測查詢或測試模型正確性時選擇性地使用。</span><span class="sxs-lookup"><span data-stu-id="a057b-122">The filter definition is stored with the model and can be used optionally when you create prediction queries, or when you test the accuracy of the model.</span></span><br /><br /> <span data-ttu-id="a057b-123">在培訓模型時，模型篩選並非選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a057b-123">The model filter is not optional when training the model.</span></span>|  
|<span data-ttu-id="a057b-124">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a057b-124">**Name**</span></span>|<span data-ttu-id="a057b-125">設定採礦模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="a057b-125">Sets the name of the mining model.</span></span>|  
|<span data-ttu-id="a057b-126">**AllowDrillThrough**</span><span class="sxs-lookup"><span data-stu-id="a057b-126">**AllowDrillThrough**</span></span>|<span data-ttu-id="a057b-127">指定採礦模型上是否啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="a057b-127">Specifies whether drill through is enabled on the mining model.</span></span>|  
  
## <a name="properties-of-model-columns"></a><span data-ttu-id="a057b-128">模型資料行的屬性</span><span class="sxs-lookup"><span data-stu-id="a057b-128">Properties of Model Columns</span></span>  
 <span data-ttu-id="a057b-129">針對採礦模型中的每一個資料行，您可以設定下列資料採礦特有的屬性。</span><span class="sxs-lookup"><span data-stu-id="a057b-129">You can set the following data mining-specific properties for each column in a mining model.</span></span> <span data-ttu-id="a057b-130">針對採礦結構中的每一個採礦模型，您可以將這些屬性設定為不同的值。</span><span class="sxs-lookup"><span data-stu-id="a057b-130">You can set these properties to a different value for each mining model in a mining structure.</span></span>  
  
|<span data-ttu-id="a057b-131">屬性</span><span class="sxs-lookup"><span data-stu-id="a057b-131">Property</span></span>|<span data-ttu-id="a057b-132">描述</span><span class="sxs-lookup"><span data-stu-id="a057b-132">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a057b-133">**說明**</span><span class="sxs-lookup"><span data-stu-id="a057b-133">**Description**</span></span>|<span data-ttu-id="a057b-134">描述採礦資料行的目的。</span><span class="sxs-lookup"><span data-stu-id="a057b-134">Describes the purpose of the mining column.</span></span>|  
|<span data-ttu-id="a057b-135">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a057b-135">**Name**</span></span>|<span data-ttu-id="a057b-136">設定採礦模型資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="a057b-136">Sets the name of the mining model column.</span></span> <span data-ttu-id="a057b-137">您可以輸入新名稱，為採礦模型資料行提供別名。</span><span class="sxs-lookup"><span data-stu-id="a057b-137">You can type a new name, to provide an alias for the mining model column.</span></span>|  
|<span data-ttu-id="a057b-138">**ModelingFlags**</span><span class="sxs-lookup"><span data-stu-id="a057b-138">**ModelingFlags**</span></span>|<span data-ttu-id="a057b-139">設定資料行的任何演算法特定旗標。</span><span class="sxs-lookup"><span data-stu-id="a057b-139">Sets any algorithm-specific flags for the column.</span></span>|  
|<span data-ttu-id="a057b-140">**SourceColumnID**</span><span class="sxs-lookup"><span data-stu-id="a057b-140">**SourceColumnID**</span></span>|<span data-ttu-id="a057b-141">代表模型資料行所依據之採礦結構資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="a057b-141">Indicates the name of the mining structure column on which the model column is based.</span></span><br /><br /> <span data-ttu-id="a057b-142">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="a057b-142">This property is read-only.</span></span>|  
|<span data-ttu-id="a057b-143">**使用量**</span><span class="sxs-lookup"><span data-stu-id="a057b-143">**Usage**</span></span>|<span data-ttu-id="a057b-144">設定採礦模型如何使用資料行。</span><span class="sxs-lookup"><span data-stu-id="a057b-144">Sets how the column will be used by the mining model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a057b-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a057b-145">See Also</span></span>  
 <span data-ttu-id="a057b-146">[採礦模型資料行](mining-model-columns.md) </span><span class="sxs-lookup"><span data-stu-id="a057b-146">[Mining Model Columns](mining-model-columns.md) </span></span>  
 <span data-ttu-id="a057b-147">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a057b-147">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a057b-148">[採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="a057b-148">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 <span data-ttu-id="a057b-149">[變更採礦模型的屬性](change-the-properties-of-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="a057b-149">[Change the Properties of a Mining Model](change-the-properties-of-a-mining-model.md) </span></span>  
 <span data-ttu-id="a057b-150">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a057b-150">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="a057b-151">[建立關聯式的採礦結構](create-a-relational-mining-structure.md) </span><span class="sxs-lookup"><span data-stu-id="a057b-151">[Create a Relational Mining Structure](create-a-relational-mining-structure.md) </span></span>  
 [<span data-ttu-id="a057b-152">建立模型資料行的別名</span><span class="sxs-lookup"><span data-stu-id="a057b-152">Create an Alias for a Model Column</span></span>](create-an-alias-for-a-model-column.md)  
  
  
