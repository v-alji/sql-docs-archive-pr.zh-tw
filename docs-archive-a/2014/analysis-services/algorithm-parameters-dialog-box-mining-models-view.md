---
title: '[演算法參數] 對話方塊 ([採礦模型] View) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
author: minewiskan
ms.author: owend
ms.openlocfilehash: 303d8b5bd3437690c65873e106a94cf2ce8eb9f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593223"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a><span data-ttu-id="e7d19-102">演算法參數對話方塊 (採礦模型檢視)</span><span class="sxs-lookup"><span data-stu-id="e7d19-102">Algorithm Parameters Dialog Box (Mining Models View)</span></span>
  <span data-ttu-id="e7d19-103">使用 [演算法參數]\*\*\*\* 對話方塊，即可調整所選取模型特定的演算法參數。</span><span class="sxs-lookup"><span data-stu-id="e7d19-103">Use the **Algorithm Parameters** dialog box to adjust algorithm parameters that are specific to the selected model.</span></span> <span data-ttu-id="e7d19-104">當您變更演算法參數時，您通常會變更採礦模型的結果。</span><span class="sxs-lookup"><span data-stu-id="e7d19-104">When you change an algorithm parameter, you will usually change the results of the mining model.</span></span> <span data-ttu-id="e7d19-105">每一個參數影響結果的方式取決於您所使用的演算法和資料而定。</span><span class="sxs-lookup"><span data-stu-id="e7d19-105">The way that each parameter affects the results depends on the algorithm you are using, and on your data.</span></span> <span data-ttu-id="e7d19-106">如需詳細資訊，請參閱 [自訂採礦模型和結構](data-mining/customize-mining-models-and-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="e7d19-106">For more information, see [Customize Mining Models and Structure](data-mining/customize-mining-models-and-structure.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e7d19-107">選項</span><span class="sxs-lookup"><span data-stu-id="e7d19-107">Options</span></span>  
 <span data-ttu-id="e7d19-108">**參數**</span><span class="sxs-lookup"><span data-stu-id="e7d19-108">**Parameters**</span></span>  
 <span data-ttu-id="e7d19-109">列出所選取採礦模型可以使用的參數。</span><span class="sxs-lookup"><span data-stu-id="e7d19-109">Lists the parameters that are available for the selected mining model.</span></span>  
  
 <span data-ttu-id="e7d19-110">下列清單描述可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="e7d19-110">The following list describes the available columns.</span></span>  
  
|<span data-ttu-id="e7d19-111">資料行</span><span class="sxs-lookup"><span data-stu-id="e7d19-111">Column</span></span>|<span data-ttu-id="e7d19-112">描述</span><span class="sxs-lookup"><span data-stu-id="e7d19-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e7d19-113">**參數**</span><span class="sxs-lookup"><span data-stu-id="e7d19-113">**Parameter**</span></span>|<span data-ttu-id="e7d19-114">列出參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="e7d19-114">List the name of the parameter.</span></span>|  
|<span data-ttu-id="e7d19-115">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="e7d19-115">**Value**</span></span>|<span data-ttu-id="e7d19-116">只有當您要變更參數的預設值時，才輸入值。</span><span class="sxs-lookup"><span data-stu-id="e7d19-116">Enter a value only if you want to change the default value of the parameter.</span></span>|  
|<span data-ttu-id="e7d19-117">**預設值**</span><span class="sxs-lookup"><span data-stu-id="e7d19-117">**Default**</span></span>|<span data-ttu-id="e7d19-118">如果您在 [值]\*\*\*\* 資料行中並未提供值，則會列出演算法使用之參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="e7d19-118">List the default value of the parameter that the algorithm will use if you do not supply a value in the **Value** column.</span></span>|  
|<span data-ttu-id="e7d19-119">**Range**</span><span class="sxs-lookup"><span data-stu-id="e7d19-119">**Range**</span></span>|<span data-ttu-id="e7d19-120">列出可以輸入到 [值]\*\*\*\* 資料行之可能值的範圍。</span><span class="sxs-lookup"><span data-stu-id="e7d19-120">List the range of possible values that you can enter into the **Value** column.</span></span> <span data-ttu-id="e7d19-121">範圍可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="e7d19-121">The ranges can be one of the following:</span></span><br /><br /> <span data-ttu-id="e7d19-122">離散清單，例如1、2、3</span><span class="sxs-lookup"><span data-stu-id="e7d19-122">A discrete list, such as 1, 2, 3</span></span><br /><br /> <span data-ttu-id="e7d19-123">內含範圍，例如 [0，100]</span><span class="sxs-lookup"><span data-stu-id="e7d19-123">An inclusive range, such as [0, 100]</span></span><br /><br /> <span data-ttu-id="e7d19-124">專有範圍，例如 (0,... ) </span><span class="sxs-lookup"><span data-stu-id="e7d19-124">An exclusive range, such as (0,...)</span></span><br /><br /> <span data-ttu-id="e7d19-125">組合，例如 [0,... ) </span><span class="sxs-lookup"><span data-stu-id="e7d19-125">A combination, such as [0,...)</span></span>|  
  
 <span data-ttu-id="e7d19-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="e7d19-126">**Description**</span></span>  
 <span data-ttu-id="e7d19-127">描述 [參數]\*\*\*\* 清單中選取的參數。</span><span class="sxs-lookup"><span data-stu-id="e7d19-127">Describes the selected parameter in the **Parameters** list.</span></span>  
  
 <span data-ttu-id="e7d19-128">**加入**</span><span class="sxs-lookup"><span data-stu-id="e7d19-128">**Add**</span></span>  
 <span data-ttu-id="e7d19-129">按一下此選項，可將其他演算法特定的參數加入至清單中。</span><span class="sxs-lookup"><span data-stu-id="e7d19-129">Click to add additional, algorithm specific-parameters to the list.</span></span> <span data-ttu-id="e7d19-130">加入參數之後，您可以在 [參數]\*\*\*\* 資料行中輸入正確的名稱，並提供 [值]\*\*\*\* 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="e7d19-130">After adding the parameter, you can enter the correct name in the **Parameter** column and provide a value in the **Value** column.</span></span>  
  
 <span data-ttu-id="e7d19-131">**移除**</span><span class="sxs-lookup"><span data-stu-id="e7d19-131">**Remove**</span></span>  
 <span data-ttu-id="e7d19-132">按一下此選項，可從清單中刪除自訂參數。</span><span class="sxs-lookup"><span data-stu-id="e7d19-132">Click to delete a custom parameter from the list.</span></span>  
  
 <span data-ttu-id="e7d19-133">如果您從清單中刪除其中一個標準 Analysis Services 演算法參數，此參數仍然會在模型中使用，但是將會使用該參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="e7d19-133">If you delete one of the standard Analysis Services algorithm parameters from the list, the parameter will still be used in the model, but with the default values for that parameter.</span></span> <span data-ttu-id="e7d19-134">此參數不會永久刪除，而且下次當您開啟對話方塊時就會出現。</span><span class="sxs-lookup"><span data-stu-id="e7d19-134">The parameter is not permanently deleted and will appear the next time that you open the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d19-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7d19-135">See Also</span></span>  
 <span data-ttu-id="e7d19-136">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e7d19-136">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="e7d19-137">[[採礦模型] 視圖 &#40;資料採礦模型設計工具&#41;](mining-models-view-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="e7d19-137">[Mining Models View &#40;Data Mining Model Designer&#41;](mining-models-view-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="e7d19-138">移動資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="e7d19-138">Moving Data Mining Objects</span></span>](data-mining/moving-data-mining-objects.md)  
  
  
