---
title: 建立 (SSAS 表格式) 的計算結果欄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.as.daxref.CreataCalculatedColumn.f1
ms.assetid: 59440510-2d76-41dc-9b55-edc15259f9da
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdb56ffb2b42aa8225b7eff76b11315ea511fd81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686483"
---
# <a name="create-a-calculated-column-ssas-tabular"></a><span data-ttu-id="66e0d-102">建立導出資料行 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="66e0d-102">Create a Calculated Column (SSAS Tabular)</span></span>
  <span data-ttu-id="66e0d-103">導出資料行可讓您將新資料加入至模型。</span><span class="sxs-lookup"><span data-stu-id="66e0d-103">Calculated columns allow you to add new data to your model.</span></span> <span data-ttu-id="66e0d-104">您可以建立 DAX 公式來定義資料行的資料列層級值，而不是將值貼入或匯入資料行。</span><span class="sxs-lookup"><span data-stu-id="66e0d-104">Instead of pasting or importing values into the column, you create a DAX formula that defines the column's row level values.</span></span> <span data-ttu-id="66e0d-105">當您建立有效的公式，然後按一下 ENTER 時，即會計算並填入導出資料行之每個資料列中的值。</span><span class="sxs-lookup"><span data-stu-id="66e0d-105">The values in each row of a calculated column are calculated and populated when you create a valid formula and then click ENTER.</span></span> <span data-ttu-id="66e0d-106">然後導出資料行就可以像是其他任何資料行，加入至報表應用程式或分析應用程式。</span><span class="sxs-lookup"><span data-stu-id="66e0d-106">The calculated column can then be added to a reporting or analysis application just as would any other column of data.</span></span> <span data-ttu-id="66e0d-107">此主題描述如何在模型設計師中使用 DAX 公式列，來建立新的導出資料行。</span><span class="sxs-lookup"><span data-stu-id="66e0d-107">This topic describes how to create a new calculated column by using the DAX formula bar in the model designer.</span></span>  
  
#### <a name="to-create-a-new-calculated-column"></a><span data-ttu-id="66e0d-108">建立新的導出資料行</span><span class="sxs-lookup"><span data-stu-id="66e0d-108">To create a new calculated column</span></span>  
  
1.  <span data-ttu-id="66e0d-109">在模型設計師的 [資料檢視] 中，選取您要加入導出資料行的資料表，然後按一下 **[資料行]** 功能表，再按一下 **[加入資料行]**。</span><span class="sxs-lookup"><span data-stu-id="66e0d-109">In the model designer, in Data View, select the table to which you want to add a calculated column, then click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="66e0d-110">**[加入資料行]** 將反白顯示於最右側空白資料行，而且游標會移到公式列。</span><span class="sxs-lookup"><span data-stu-id="66e0d-110">**Add Column** is highlighted over the empty rightmost column, and the cursor moves to the formula bar.</span></span>  
  
     <span data-ttu-id="66e0d-111">若要在兩個現有的資料行之間建立新資料行，請以滑鼠右鍵按一下現有的資料行，然後按一下 [插入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66e0d-111">To create a new column between two existing columns, right-click an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="66e0d-112">在公式列中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="66e0d-112">In the formula bar, do one of the following:</span></span>  
  
    -   <span data-ttu-id="66e0d-113">輸入等號，後面接著公式。</span><span class="sxs-lookup"><span data-stu-id="66e0d-113">Type an equal sign followed by a formula.</span></span>  
  
    -   <span data-ttu-id="66e0d-114">輸入等號，後面接著 DAX 函數，然後是函數需要的引數和參數。</span><span class="sxs-lookup"><span data-stu-id="66e0d-114">Type an equal sign, followed by a DAX function, followed by arguments and parameters as required by the function.</span></span>  
  
    -   <span data-ttu-id="66e0d-115">按一下函數按鈕 (**fx**)，然後在 [插入函數]\*\*\*\* 對話方塊中，選取類別目錄和函數，再按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="66e0d-115">Click the function button (**fx**), then in the **Insert Function** dialog box, select a category and function, and then click **OK**.</span></span> <span data-ttu-id="66e0d-116">在公式列中，輸入函數所需的其餘引數和參數。</span><span class="sxs-lookup"><span data-stu-id="66e0d-116">In the formula bar, type the remaining arguments and parameters as required by the function.</span></span>  
  
3.  <span data-ttu-id="66e0d-117">按下 ENTER 鍵接受公式。</span><span class="sxs-lookup"><span data-stu-id="66e0d-117">Press ENTER to accept the formula.</span></span>  
  
     <span data-ttu-id="66e0d-118">整個資料行都會填入公式，而且會針對每個資料列計算值。</span><span class="sxs-lookup"><span data-stu-id="66e0d-118">The entire column is populated with the formula, and a value is calculated for each row.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="66e0d-119">您可以透過巢狀函數，在現有的公式中間使用 DAX 公式自動完成。</span><span class="sxs-lookup"><span data-stu-id="66e0d-119">You can use DAX Formula AutoComplete in the middle of an existing formula with nested functions.</span></span> <span data-ttu-id="66e0d-120">插入點前方的文字用於顯示下拉式清單中的值，而在插入點之後的所有文字則維持不變。</span><span class="sxs-lookup"><span data-stu-id="66e0d-120">The text immediately before the insertion point is used to display values in the drop-down list, and all of the text after the insertion point remains unchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e0d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66e0d-121">See Also</span></span>  
 <span data-ttu-id="66e0d-122">[&#40;SSAS 表格式&#41;的計算結果欄](ssas-calculated-columns.md) </span><span class="sxs-lookup"><span data-stu-id="66e0d-122">[Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md) </span></span>  
 [<span data-ttu-id="66e0d-123">量值 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="66e0d-123">Measures &#40;SSAS Tabular&#41;</span></span>](measures-ssas-tabular.md)  
  
  
