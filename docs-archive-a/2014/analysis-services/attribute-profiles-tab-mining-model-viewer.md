---
title: '[屬性設定檔] 索引標籤 () 的採礦模型檢視器 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
ms.openlocfilehash: 61c81b95f030bf1a69aed165bd64e58ff9af8339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593168"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a><span data-ttu-id="16839-102">屬性設定檔索引標籤 (採礦模型檢視器)</span><span class="sxs-lookup"><span data-stu-id="16839-102">Attribute Profiles Tab (Mining Model Viewer)</span></span>
  <span data-ttu-id="16839-103">可以使用 **[屬性設定檔]** 索引標籤，來查看貝氏機率分類模型狀態中輸入值的分佈如何影響結果屬性的每個狀態。</span><span class="sxs-lookup"><span data-stu-id="16839-103">Use the **Attribute Profiles** tab to see how the distribution of input values in a Naive Bayes model state contribute to each state of the outcome attribute.</span></span> <span data-ttu-id="16839-104">值的分佈會顯示為彩色長條圖，而且所有分佈都會以表格格式呈現，以便更輕鬆地比較值。</span><span class="sxs-lookup"><span data-stu-id="16839-104">The distribution of values is shown as a colored histogram, all distributions presented in a tabular format, to make it easier to compare values.</span></span>  
  
 <span data-ttu-id="16839-105">\*\*如需詳細資訊，請參閱 \*\* [Microsoft 貝氏機率分類演算法](data-mining/microsoft-naive-bayes-algorithm.md)、[使用 Microsoft 貝氏機率分類檢視器瀏覽模型](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="16839-105">**For More Information:** [Microsoft Naive Bayes Algorithm](data-mining/microsoft-naive-bayes-algorithm.md), [Browse a Model Using the Microsoft Naive Bayes Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="16839-106">選項</span><span class="sxs-lookup"><span data-stu-id="16839-106">Options</span></span>  
 <span data-ttu-id="16839-107">**重新整理檢視器內容**</span><span class="sxs-lookup"><span data-stu-id="16839-107">**Refresh viewer content**</span></span>  
 <span data-ttu-id="16839-108">在檢視器中重新載入採礦模型。</span><span class="sxs-lookup"><span data-stu-id="16839-108">Reload the mining model in the viewer.</span></span>  
  
 <span data-ttu-id="16839-109">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="16839-109">**Mining Model**</span></span>  
 <span data-ttu-id="16839-110">在目前採礦結構中選擇要檢視的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="16839-110">Choose a mining model to view, from those in the current mining structure.</span></span> <span data-ttu-id="16839-111">採礦模型會在其關聯的檢視器中開啟。</span><span class="sxs-lookup"><span data-stu-id="16839-111">The mining model will open in its associated viewer.</span></span>  
  
 <span data-ttu-id="16839-112">**檢視者**</span><span class="sxs-lookup"><span data-stu-id="16839-112">**Viewer**</span></span>  
 <span data-ttu-id="16839-113">選擇用來瀏覽選取之採礦模型的檢視器。</span><span class="sxs-lookup"><span data-stu-id="16839-113">Choose a viewer to use to explore the selected mining model.</span></span> <span data-ttu-id="16839-114">可以選擇為每個採礦模型提供的自訂檢視器，或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 採礦內容檢視器。</span><span class="sxs-lookup"><span data-stu-id="16839-114">You can choose the custom viewer provided for each mining model, or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Mining Content Viewer.</span></span> <span data-ttu-id="16839-115">還可以使用外掛程式檢視器 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="16839-115">You can also use plug-in viewers if they are available.</span></span>  
  
 <span data-ttu-id="16839-116">**顯示圖例**</span><span class="sxs-lookup"><span data-stu-id="16839-116">**Show Legend**</span></span>  
 <span data-ttu-id="16839-117">選取此選項可顯示圖例符號，該圖例符號會將 [狀態]\*\*\*\* 中的每個值對應至分佈圖表中使用的色彩。</span><span class="sxs-lookup"><span data-stu-id="16839-117">Select this option to display a key that matches each value in **States** to one of the colors used in the distribution chart.</span></span>  
  
 <span data-ttu-id="16839-118">**長條圖列**</span><span class="sxs-lookup"><span data-stu-id="16839-118">**Histogram bars**</span></span>  
 <span data-ttu-id="16839-119">選取長條圖中要包含多少個圖列。</span><span class="sxs-lookup"><span data-stu-id="16839-119">Select how many bars to include in the histogram.</span></span> <span data-ttu-id="16839-120">如果圖列的總數超出您選擇要顯示的總數，就會保留最重要的圖列，並將其餘的圖列一起放入 **[其他]** 群組中。</span><span class="sxs-lookup"><span data-stu-id="16839-120">If more bars exist than you choose to display, the bars of highest importance are retained, and the remaining bars are grouped together into **Other**.</span></span>  
  
 <span data-ttu-id="16839-121">**可預測**</span><span class="sxs-lookup"><span data-stu-id="16839-121">**Predictable**</span></span>  
 <span data-ttu-id="16839-122">從採礦模型選取可預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="16839-122">Select a predictable column from the mining model.</span></span>  
  
 <span data-ttu-id="16839-123">**屬性設定檔**</span><span class="sxs-lookup"><span data-stu-id="16839-123">**Attribute Profiles**</span></span>  
 <span data-ttu-id="16839-124">該表格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="16839-124">The table contains the following columns:</span></span>  
  
|<span data-ttu-id="16839-125">值</span><span class="sxs-lookup"><span data-stu-id="16839-125">Value</span></span>|<span data-ttu-id="16839-126">描述</span><span class="sxs-lookup"><span data-stu-id="16839-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16839-127">**屬性**</span><span class="sxs-lookup"><span data-stu-id="16839-127">**Attributes**</span></span>|<span data-ttu-id="16839-128">列出採礦模型中包含的採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="16839-128">Lists the mining model columns contained within the mining model.</span></span>|  
|<span data-ttu-id="16839-129">**狀態**</span><span class="sxs-lookup"><span data-stu-id="16839-129">**States**</span></span>|<span data-ttu-id="16839-130">此為選擇性的資料行，用來描述屬性對應資料列之色彩所代表的狀態。</span><span class="sxs-lookup"><span data-stu-id="16839-130">An optional column that describes what state the color in the corresponding row of attributes represents.</span></span> <span data-ttu-id="16839-131">使用 **[顯示圖例]** 核取方塊即可加入或移除。</span><span class="sxs-lookup"><span data-stu-id="16839-131">Add or remove by using the **Show Legend** check box.</span></span>|  
|<span data-ttu-id="16839-132">**人數**</span><span class="sxs-lookup"><span data-stu-id="16839-132">**Population**</span></span>|<span data-ttu-id="16839-133">顯示整個結果集之屬性的散發。</span><span class="sxs-lookup"><span data-stu-id="16839-133">Displays the distribution of the attribute across the whole dataset.</span></span>|  
|<span data-ttu-id="16839-134">**可預測變數之狀態的資料行**</span><span class="sxs-lookup"><span data-stu-id="16839-134">**Column for states of predictable attribute**</span></span>|<span data-ttu-id="16839-135">為可預測資料行的每個狀態顯示一個資料行，其中每個資料列都會對應至模型中的某個輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="16839-135">Displays a column for each state of the predictable column, with each row corresponding to an input attribute in the model.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16839-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16839-136">See Also</span></span>  
 <span data-ttu-id="16839-137">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="16839-137">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="16839-138">[&#40;資料採礦模型設計工具的採礦模型檢視器&#41;](mining-model-viewers-data-mining-model-designer.md) </span><span class="sxs-lookup"><span data-stu-id="16839-138">[Mining Model Viewers &#40;Data Mining Model Designer&#41;](mining-model-viewers-data-mining-model-designer.md) </span></span>  
 [<span data-ttu-id="16839-139">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="16839-139">Data Mining Model Viewers</span></span>](data-mining/data-mining-model-viewers.md)  
  
  
