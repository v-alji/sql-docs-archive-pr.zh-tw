---
title: 變更採礦模型的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], properties
- properties [data mining]
ms.assetid: aefaeb7f-d174-48d1-a188-0987a3b1196b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 395e6a4cb9c0f0dac0f0c717dfe0695033cad050
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585675"
---
# <a name="change-the-properties-of-a-mining-model"></a><span data-ttu-id="4bd22-102">變更採礦模型的屬性</span><span class="sxs-lookup"><span data-stu-id="4bd22-102">Change the Properties of a Mining Model</span></span>
  <span data-ttu-id="4bd22-103">有些採礦模型屬性可套用至整個模型，有些模型屬性只套用至個別資料行。</span><span class="sxs-lookup"><span data-stu-id="4bd22-103">Some mining model properties apply to the model as a whole, and other model properties apply to individual columns.</span></span> <span data-ttu-id="4bd22-104">例如，`Drillthrough` 屬性可套用至整個模型，它指定案例資料是否應該可用於查詢，`Description` 屬性也是這類屬性。</span><span class="sxs-lookup"><span data-stu-id="4bd22-104">Examples of properties that apply to the entire model would be the `Drillthrough` property, which specifies whether the case data should be available for querying, and the `Description` property.</span></span> <span data-ttu-id="4bd22-105">套用至資料行的屬性包含 `Usage` 和 `ModelingFlags`，它們控制資料行中的資料在模型內的使用方式。</span><span class="sxs-lookup"><span data-stu-id="4bd22-105">Properties that apply to the column include `Usage` and `ModelingFlags`, which control how data in the column is used within the model.</span></span>  
  
 <span data-ttu-id="4bd22-106">下列模型屬性具有可用於建立運算式或設定複雜模型屬性的進階編輯器。</span><span class="sxs-lookup"><span data-stu-id="4bd22-106">The following model properties have advanced editors that you can use to create expressions or configure complex model properties.</span></span> <span data-ttu-id="4bd22-107">下列屬性提供：</span><span class="sxs-lookup"><span data-stu-id="4bd22-107">The following properties provide:</span></span>  
  
-   <span data-ttu-id="4bd22-108">`Filter`屬性：開啟 [[資料集篩選器] 或 [模型篩選器] 對話方塊](../data-set-filter-or-model-filter-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd22-108">`Filter` property: Opens the [Data Set Filter or Model Filter Dialog Box](../data-set-filter-or-model-filter-dialog-box.md).</span></span>  
  
-   <span data-ttu-id="4bd22-109">`AlgorithmParameters`屬性：開啟 [[演算法參數] 對話方塊 &#40;[採礦模型] View&#41;](../algorithm-parameters-dialog-box-mining-models-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd22-109">`AlgorithmParameters` property: Opens the [Algorithm Parameters Dialog Box &#40;Mining Models View&#41;](../algorithm-parameters-dialog-box-mining-models-view.md).</span></span>  
  
 <span data-ttu-id="4bd22-110">如需如何在採礦模型中設定屬性的資訊，請參閱 [採礦模型資料行](mining-model-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="4bd22-110">For information about how to set the properties in a mining model, see [Mining Model Columns](mining-model-columns.md).</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model"></a><span data-ttu-id="4bd22-111">若要變更採礦模型的屬性</span><span class="sxs-lookup"><span data-stu-id="4bd22-111">To change the properties of a mining model</span></span>  
  
1.  <span data-ttu-id="4bd22-112">在資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤中，以滑鼠右鍵按一下包含採礦模型名稱的資料行標題，或方格中包含採礦演算法名稱的資料列，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4bd22-112">In the **Mining Models** tab in Data Mining Designer, right-click either the column header that contains the name of the mining model, or the row in the grid that contains the name of the mining algorithm, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4bd22-113">在畫面右側的 [屬性]\*\*\*\* 視窗中，反白顯示對應到您要變更之屬性的值，然後輸入新值。</span><span class="sxs-lookup"><span data-stu-id="4bd22-113">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
     <span data-ttu-id="4bd22-114">您在設計師中選取其他元素時，新值就會生效。</span><span class="sxs-lookup"><span data-stu-id="4bd22-114">The new value will take effect when you select a different element in the designer.</span></span>  
  
### <a name="to-change-the-properties-of-a-mining-model-column"></a><span data-ttu-id="4bd22-115">變更採礦模型資料行的屬性</span><span class="sxs-lookup"><span data-stu-id="4bd22-115">To change the properties of a mining model column</span></span>  
  
1.  <span data-ttu-id="4bd22-116">在資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤中，以滑鼠右鍵按一下採礦結構資料行和採礦模型交集方格中的資料格，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4bd22-116">In the **Mining Models** tab in Data Mining Designer, right-click the cell in the grid at the intersection of the mining structure column and the mining model, and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="4bd22-117">在畫面右側的 [屬性]\*\*\*\* 視窗中，反白顯示對應到您要變更之屬性的值，然後輸入新值。</span><span class="sxs-lookup"><span data-stu-id="4bd22-117">In the **Properties** window on the right side of the screen, highlight the value that corresponds to the property that you want to change, and enter the new value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4bd22-118">如果 [資料行使用方式] 設定為，則資料 `Ignore` 行的 [**屬性**] 視窗是空白的。</span><span class="sxs-lookup"><span data-stu-id="4bd22-118">If the column usage is set to `Ignore`, the **Properties** window for the column is blank.</span></span>  
  
     <span data-ttu-id="4bd22-119">您在設計師中選取其他元素時，新值就會生效。</span><span class="sxs-lookup"><span data-stu-id="4bd22-119">The new value will take effect when you select a different element in the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd22-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bd22-120">See Also</span></span>  
 [<span data-ttu-id="4bd22-121">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="4bd22-121">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
  
