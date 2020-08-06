---
title: 從採礦模型刪除篩選 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- filters [Analysis Services]
ms.assetid: 91220b21-adbc-49a9-b200-8bf0a724eff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 404c23c0e55bffba2ce8410c9c30d6ad1fa1991b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592329"
---
# <a name="delete-a-filter-from-a-mining-model"></a><span data-ttu-id="b8077-102">從採礦模型刪除篩選</span><span class="sxs-lookup"><span data-stu-id="b8077-102">Delete a Filter from a Mining Model</span></span>
  <span data-ttu-id="b8077-103">當您建立採礦模型的篩選時，您可以在資料來源檢視中的資料子集上建立模型。</span><span class="sxs-lookup"><span data-stu-id="b8077-103">When you create a filter on a mining model, you can create models on a subset of the data in the data source view.</span></span> <span data-ttu-id="b8077-104">篩選對於測試原始資料子集上之模型的精確度也非常實用。</span><span class="sxs-lookup"><span data-stu-id="b8077-104">Filters are also useful for testing the accuracy of the model on a subset of the original data.</span></span>  
  
 <span data-ttu-id="b8077-105">不過，如果想要再次檢視完整的案例集，則必須刪除篩選。</span><span class="sxs-lookup"><span data-stu-id="b8077-105">However, you must delete the filter if you want to view the complete set of cases again.</span></span> <span data-ttu-id="b8077-106">此程序描述如何移除篩選的條件，或完全刪除篩選。</span><span class="sxs-lookup"><span data-stu-id="b8077-106">This procedure describes how to remove conditions on a filter, or delete the filter completely.</span></span>  
  
### <a name="to-delete-a-condition-from-a-filter-on-a-mining-model"></a><span data-ttu-id="b8077-107">若要從採礦模型的篩選刪除條件</span><span class="sxs-lookup"><span data-stu-id="b8077-107">To delete a condition from a filter on a mining model</span></span>  
  
1.  <span data-ttu-id="b8077-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 [方案總管] 中，按一下包含要篩選的採礦模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="b8077-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Solution Explorer, click the mining structure that contains the mining model you want to filter.</span></span>  
  
2.  <span data-ttu-id="b8077-109">按一下 **[採礦模型]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b8077-109">Click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="b8077-110">選擇模型，然後以滑鼠右鍵按一下，開啟快速鍵功能表。</span><span class="sxs-lookup"><span data-stu-id="b8077-110">Select the model, and right-click to open the shortcut menu.</span></span>  
  
     <span data-ttu-id="b8077-111">-或-</span><span class="sxs-lookup"><span data-stu-id="b8077-111">-or-</span></span>  
  
     <span data-ttu-id="b8077-112">選取此模型。</span><span class="sxs-lookup"><span data-stu-id="b8077-112">Select the model.</span></span> <span data-ttu-id="b8077-113">在 **[採礦模型]** 功能表上，選取 **[設定模型篩選器]**。</span><span class="sxs-lookup"><span data-stu-id="b8077-113">On the **Mining Model** menu, select **Set Model Filter**.</span></span>  
  
4.  <span data-ttu-id="b8077-114">在 [模組篩選器]\*\*\*\* 對話方塊中，以滑鼠右鍵在方格中按一下包含所要刪除之條件的資料列。</span><span class="sxs-lookup"><span data-stu-id="b8077-114">In the **Model Filter** dialog box, right-click the row in the grid that contains the condition you want to delete.</span></span>  
  
5.  <span data-ttu-id="b8077-115">選取 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="b8077-115">Select **Delete**.</span></span>  
  
### <a name="to-clear-the-filter-on-a-mining-model-in-the-filter-editor-dialog-box"></a><span data-ttu-id="b8077-116">若要在篩選編輯器對話方塊中清除採礦模型上的篩選</span><span class="sxs-lookup"><span data-stu-id="b8077-116">To clear the filter on a mining model in the Filter Editor dialog box</span></span>  
  
-   <span data-ttu-id="b8077-117">在 [篩選編輯器]\*\*\*\* 對話方塊中，以滑鼠右鍵在方格中按一下任何資料列，然後選取 [全部刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b8077-117">In the **Filter Editor** dialog box, right-click any row in the grid, and select **Delete All**.</span></span>  
  
## <a name="working-with-model-filters-using-the-properties-window"></a><span data-ttu-id="b8077-118">利用屬性視窗使用模型篩選</span><span class="sxs-lookup"><span data-stu-id="b8077-118">Working with Model Filters Using the Properties Window</span></span>  
 <span data-ttu-id="b8077-119">如果想要刪除整個篩選，就不需要開啟篩選編輯器對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b8077-119">If you want to delete the whole filter, you do not need to open the filter editor dialog boxes.</span></span> <span data-ttu-id="b8077-120">您建立的篩選條件可用於採礦模型的 `Filter` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b8077-120">The filter conditions that you created are available in the `Filter` property of the mining model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8077-121">您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中檢視採礦模型的屬性，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中則不能。</span><span class="sxs-lookup"><span data-stu-id="b8077-121">You can view the properties of a mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], but not in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-clear-the-filter-on-a-mining-model-in-solution-explorer"></a><span data-ttu-id="b8077-122">若要在方案總管中清除採礦模型上的篩選</span><span class="sxs-lookup"><span data-stu-id="b8077-122">To clear the filter on a mining model in Solution Explorer</span></span>  
  
1.  <span data-ttu-id="b8077-123">在 [方案總管] 中，按一下包含篩選的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b8077-123">In Solution Explorer, click the mining model that contains the filter.</span></span>  
  
2.  <span data-ttu-id="b8077-124">在 [**屬性**] 視窗中，以滑鼠右鍵按一下屬性中的篩選文字 `Filter` ，然後選取 [**全選**]。</span><span class="sxs-lookup"><span data-stu-id="b8077-124">In the **Properties** window, right-click the filter text in the `Filter` property, and select **Select All**.</span></span>  
  
3.  <span data-ttu-id="b8077-125">按退格鍵或 Delete 鍵。</span><span class="sxs-lookup"><span data-stu-id="b8077-125">Press the Backspace or Delete key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8077-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8077-126">See Also</span></span>  
 <span data-ttu-id="b8077-127">[向下切入至採礦模型的案例資料](drill-through-to-case-data-from-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="b8077-127">[Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md) </span></span>  
 <span data-ttu-id="b8077-128">[採礦模型工作和操作說明](mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="b8077-128">[Mining Model Tasks and How-tos](mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="b8077-129">採礦模型的篩選 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="b8077-129">Filters for Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
  
