---
title: 查詢和篩選 (瀏覽器索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.filterpane.f1
ms.assetid: f5cf0bb1-3afb-4856-a2ef-614deb4e7e49
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66bd299e210b3d00384395177cdd6e89d1c00183
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594249"
---
# <a name="query-and-filter-browser-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="65edf-102">查詢和篩選 (瀏覽器索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="65edf-102">Query and Filter (Browser Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="65edf-103">Cube 設計師中的 [瀏覽器]\*\*\*\* 索引標籤區域包含查詢和篩選區域，以協助您從 Cube 選擇用於瀏覽或查詢的資料。</span><span class="sxs-lookup"><span data-stu-id="65edf-103">This area of the **Browser** tab in Cube Designer contains a query and filter area, to help you choose data from the cube to use in browsing or in queries.</span></span> <span data-ttu-id="65edf-104">您可以加入所需的 Cube 物件數，然後在資料區域中檢視結果，或者使用 [在 Excel 中進行分析] 將結果匯出至報表，以視覺化使用者檢使用者使用者檢視資料的方式。</span><span class="sxs-lookup"><span data-stu-id="65edf-104">You can add as many cube objects as you want, and then view the results in the data area, or export the results to a report using Analyze in Excel to visualize how the data would be viewed by end users.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="65edf-105">當您正在處理此區域中的資料時，[瀏覽器]\*\*\*\* 會使用圖形設計模式。</span><span class="sxs-lookup"><span data-stu-id="65edf-105">When you are working with data in this area, by default the **Browser** uses the graphical design mode.</span></span> <span data-ttu-id="65edf-106">不過，您可以使用 MDX，或按一下 [設計模式]\*\*\*\* 切換按鈕，直接編輯該查詢。</span><span class="sxs-lookup"><span data-stu-id="65edf-106">However, you can edit the query directly using MDX, by clicking the **Design Mode** toggle button.</span></span> <span data-ttu-id="65edf-107">當您這樣做時，可讓您設計的窗格會在維度消失時篩選。</span><span class="sxs-lookup"><span data-stu-id="65edf-107">When you do so, the pane that lets you design filters on dimensions disappears.</span></span> <span data-ttu-id="65edf-108">如果您要加入篩選，可以切換回圖形設計模式。</span><span class="sxs-lookup"><span data-stu-id="65edf-108">If you want to add a filter, you can switch back to graphical design mode.</span></span>  
  
 <span data-ttu-id="65edf-109">根據預設，執行查詢時，目前使用者的認證 (而非在 [模擬資訊]\*\*\*\* 頁面中指定的認證) 會用來連接資料來源。</span><span class="sxs-lookup"><span data-stu-id="65edf-109">By default, the credentials of the current user, not the credentials specified in the **Impersonation Information** page, are used to connect to the data source when a query is executed.</span></span> <span data-ttu-id="65edf-110">不過，您也可以按一下 [工具列]\*\*\*\* 上的 [變更使用者]\*\*\*\*，變更查詢或報表的使用者內容。</span><span class="sxs-lookup"><span data-stu-id="65edf-110">However, you can also change the user context for the query or report by clicking **Change User** on the **Toolbar**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="65edf-111">選項</span><span class="sxs-lookup"><span data-stu-id="65edf-111">Options</span></span>  
 <span data-ttu-id="65edf-112">**維度**</span><span class="sxs-lookup"><span data-stu-id="65edf-112">**Dimension**</span></span>  
 <span data-ttu-id="65edf-113">選取要配量 Subcube 的維度。</span><span class="sxs-lookup"><span data-stu-id="65edf-113">Select the dimension on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="65edf-114">**階層**</span><span class="sxs-lookup"><span data-stu-id="65edf-114">**Hierarchy**</span></span>  
 <span data-ttu-id="65edf-115">選取要配量 Subcube 的階層。</span><span class="sxs-lookup"><span data-stu-id="65edf-115">Select the hierarchy on which to slice the subcube.</span></span>  
  
 <span data-ttu-id="65edf-116">**運算子**</span><span class="sxs-lookup"><span data-stu-id="65edf-116">**Operator**</span></span>  
 <span data-ttu-id="65edf-117">選取運算子，定義 [篩選運算式]\*\*\*\* 中的運算式如何套用至所選取階層。</span><span class="sxs-lookup"><span data-stu-id="65edf-117">Select the operator that defines how the expression in **Filter Expression** is applied to the selected hierarchy.</span></span> <span data-ttu-id="65edf-118">下表描述可用的運算子。</span><span class="sxs-lookup"><span data-stu-id="65edf-118">The following table describes the available operators.</span></span>  
  
|<span data-ttu-id="65edf-119">值</span><span class="sxs-lookup"><span data-stu-id="65edf-119">Value</span></span>|<span data-ttu-id="65edf-120">描述</span><span class="sxs-lookup"><span data-stu-id="65edf-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="65edf-121">**等於**</span><span class="sxs-lookup"><span data-stu-id="65edf-121">**Equal**</span></span>|<span data-ttu-id="65edf-122">結果會限制為 **[篩選運算式]** 中定義的集合。</span><span class="sxs-lookup"><span data-stu-id="65edf-122">The results are restricted to the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-123">**不等於**</span><span class="sxs-lookup"><span data-stu-id="65edf-123">**Not Equal**</span></span>|<span data-ttu-id="65edf-124">結果會限制為 **[篩選運算式]** 中定義之集合所排除的成員。</span><span class="sxs-lookup"><span data-stu-id="65edf-124">The results are restricted to the members excluded by the set defined in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-125">**在**</span><span class="sxs-lookup"><span data-stu-id="65edf-125">**In**</span></span>|<span data-ttu-id="65edf-126">結果會限制為 **[篩選運算式]** 中選擇的命名集。</span><span class="sxs-lookup"><span data-stu-id="65edf-126">The results are restricted to the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-127">**不在**</span><span class="sxs-lookup"><span data-stu-id="65edf-127">**Not In**</span></span>|<span data-ttu-id="65edf-128">結果會限制為 **[篩選運算式]** 中選擇之命名集所排除的成員。</span><span class="sxs-lookup"><span data-stu-id="65edf-128">The results are restricted to the members excluded by the named set chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-129">**Contains**</span><span class="sxs-lookup"><span data-stu-id="65edf-129">**Contains**</span></span>|<span data-ttu-id="65edf-130">結果會限制為成員名稱中包含 **[篩選運算式]** 中的字串之成員。</span><span class="sxs-lookup"><span data-stu-id="65edf-130">The results are restricted to members whose member names contain the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-131">**開頭為**</span><span class="sxs-lookup"><span data-stu-id="65edf-131">**Begins With**</span></span>|<span data-ttu-id="65edf-132">結果會限制為成員名稱是以 **[篩選運算式]** 中的字串開頭之成員。</span><span class="sxs-lookup"><span data-stu-id="65edf-132">The results are restricted to members whose member names begin with the string in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-133">**Range (Inclusive)**</span><span class="sxs-lookup"><span data-stu-id="65edf-133">**Range (Inclusive)**</span></span>|<span data-ttu-id="65edf-134">結果會限制為 **[篩選運算式]** 中選擇的範圍。</span><span class="sxs-lookup"><span data-stu-id="65edf-134">The results are restricted to the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-135">**Range (Exclusive)**</span><span class="sxs-lookup"><span data-stu-id="65edf-135">**Range (Exclusive)**</span></span>|<span data-ttu-id="65edf-136">結果會限制為 **[篩選運算式]** 中選擇之範圍所排除的成員。</span><span class="sxs-lookup"><span data-stu-id="65edf-136">The results are restricted to the members excluded by the range chosen in **Filter Expression**.</span></span>|  
|<span data-ttu-id="65edf-137">**MDX**</span><span class="sxs-lookup"><span data-stu-id="65edf-137">**MDX**</span></span>|<span data-ttu-id="65edf-138">結果會限制為 [篩選運算式]\*\*\*\* 中的多維度運算式 (MDX) 運算式集合。</span><span class="sxs-lookup"><span data-stu-id="65edf-138">The results are restricted to the Multidimensional Expressions (MDX) expression set in **Filter Expression**.</span></span>|  
  
 <span data-ttu-id="65edf-139">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="65edf-139">**Filter Expression**</span></span>  
 <span data-ttu-id="65edf-140">鍵入 [運算子]\*\*\*\* 所要評估的運算式，這會限制要瀏覽的結果。</span><span class="sxs-lookup"><span data-stu-id="65edf-140">Type the expression that is to be evaluated by **Operator**, which restricts the results to be browsed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65edf-141">此欄位是一個動態資料輸入元素，外觀會變更以反映選取之運算子所需要的資料類型。</span><span class="sxs-lookup"><span data-stu-id="65edf-141">This field is a dynamic data entry element, changing appearance to reflect the types of data necessary for the selected operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65edf-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65edf-142">See Also</span></span>  
 <span data-ttu-id="65edf-143">[Cube 設計工具 &#40;Analysis Services-多維度資料&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="65edf-143">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="65edf-144">[瀏覽器 &#40;Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="65edf-144">[Browser &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="65edf-145">[工具列 &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="65edf-145">[Toolbar &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="65edf-146">[[在 Excel 中進行分析] &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="65edf-146">[Analyze in Excel &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="65edf-147">中繼資料 &#40;瀏覽器索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="65edf-147">Metadata &#40;Browser Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)  
  
  
