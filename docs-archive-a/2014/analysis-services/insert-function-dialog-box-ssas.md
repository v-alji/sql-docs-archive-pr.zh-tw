---
title: " (SSAS) 的 [插入函數] 對話方塊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- SQL12.ASVS.BIDTOOLSET.INSERTFUNCTIONDB.F1
ms.assetid: c4b36d8f-2328-45f7-8bd4-cc0111571e25
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0d92dd34e671dc026215d79e7eaed88bebfac15f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596402"
---
# <a name="insert-function-dialog-box-ssas"></a><span data-ttu-id="08fbc-102">插入函數對話方塊 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="08fbc-102">Insert Function Dialog Box (SSAS)</span></span>
  <span data-ttu-id="08fbc-103">**[插入函數]** 對話方塊可讓您從函數清單選擇建立公式時可以使用的函數。</span><span class="sxs-lookup"><span data-stu-id="08fbc-103">The **Insert Function** dialog box enables you to choose from a list of functions that can be used when building formulas.</span></span> <span data-ttu-id="08fbc-104">若要從模型設計師存取此對話方塊，在每個資料表上方的公式列中，按一下函數 (**fx**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="08fbc-104">To access this dialog box from the model designer, in the formula bar above each table, click the function (**fx**) button.</span></span> <span data-ttu-id="08fbc-105">如需有關選擇於公式中使用之函數的詳細資訊，請參閱＜DAX 簡介＞和＜建立公式＞。</span><span class="sxs-lookup"><span data-stu-id="08fbc-105">For more information about choosing functions to use in formulas, see DAX Introduction and Build a Formula.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08fbc-106">項目</span><span class="sxs-lookup"><span data-stu-id="08fbc-106">Item</span></span>|<span data-ttu-id="08fbc-107">描述</span><span class="sxs-lookup"><span data-stu-id="08fbc-107">Description</span></span>|  
|<span data-ttu-id="08fbc-108">**選取類別**</span><span class="sxs-lookup"><span data-stu-id="08fbc-108">**Select a category**</span></span>|<span data-ttu-id="08fbc-109">如果您約略知道所需要的函數種類，請從清單選擇一個類別目錄，或者選取 **[全部]** 來檢視依字母順序排列的函數清單。</span><span class="sxs-lookup"><span data-stu-id="08fbc-109">If you have a general idea which kind of function you need, choose a category from the list; or select **All** to view an alphabetical list of functions.</span></span>|  
|<span data-ttu-id="08fbc-110">**選取函式**</span><span class="sxs-lookup"><span data-stu-id="08fbc-110">**Select a function**</span></span>|<span data-ttu-id="08fbc-111">顯示所選類別目錄中的函數清單。</span><span class="sxs-lookup"><span data-stu-id="08fbc-111">Displays a list of the functions in the selected category.</span></span>|  
|<span data-ttu-id="08fbc-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="08fbc-112">**Description**</span></span>|<span data-ttu-id="08fbc-113">顯示函數用途的描述，以及任何必要或選用的引數，例如資料行名稱和運算式。</span><span class="sxs-lookup"><span data-stu-id="08fbc-113">Displays a description of what the function does, together with any required or optional arguments, such as column names and expressions.</span></span>|  
  
## <a name="function-categories"></a><span data-ttu-id="08fbc-114">函數類別目錄</span><span class="sxs-lookup"><span data-stu-id="08fbc-114">Function Categories</span></span>  
 <span data-ttu-id="08fbc-115">Data Analysis Expressions (DAX) 會在 [插入函數]\*\*\*\* 對話方塊中提供下列類型的函數類別目錄。</span><span class="sxs-lookup"><span data-stu-id="08fbc-115">Data Analysis Expressions (DAX) provides the following types of function categories in the **Insert Functions** dialog box.</span></span>  
  
 <span data-ttu-id="08fbc-116">全部</span><span class="sxs-lookup"><span data-stu-id="08fbc-116">All</span></span>  
  
 <span data-ttu-id="08fbc-117">日期和時間</span><span class="sxs-lookup"><span data-stu-id="08fbc-117">Date & Time</span></span>  
  
 <span data-ttu-id="08fbc-118">Filter</span><span class="sxs-lookup"><span data-stu-id="08fbc-118">Filter</span></span>  
  
 <span data-ttu-id="08fbc-119">邏輯</span><span class="sxs-lookup"><span data-stu-id="08fbc-119">Logical</span></span>  
  
 <span data-ttu-id="08fbc-120">數學與三角函數</span><span class="sxs-lookup"><span data-stu-id="08fbc-120">Math & Trig</span></span>  
  
 <span data-ttu-id="08fbc-121">統計</span><span class="sxs-lookup"><span data-stu-id="08fbc-121">Statistical</span></span>  
  
 <span data-ttu-id="08fbc-122">Text</span><span class="sxs-lookup"><span data-stu-id="08fbc-122">Text</span></span>  
  
## <a name="measures-and-formulas"></a><span data-ttu-id="08fbc-123">量值和公式</span><span class="sxs-lookup"><span data-stu-id="08fbc-123">Measures and Formulas</span></span>  
 <span data-ttu-id="08fbc-124">只有在您建立公式時，才可以使用 **[插入函數]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="08fbc-124">The **Insert Function** dialog box is available only when you are building a formula.</span></span> <span data-ttu-id="08fbc-125">您可以在計算結果欄、樞紐分析表或樞紐分析圖中建立計算。</span><span class="sxs-lookup"><span data-stu-id="08fbc-125">You can create calculations either in a calculated column, or in a PivotTable or PivotChart.</span></span> <span data-ttu-id="08fbc-126">您針對在樞紐分析表中使用而明確建立的公式也稱為 *「量值」*(Measure)。</span><span class="sxs-lookup"><span data-stu-id="08fbc-126">Formulas that you build expressly for use in a PivotTable are also called *measures*.</span></span> <span data-ttu-id="08fbc-127">如需詳細資訊，請參閱[建立導出資料行 &#40;SSAS 表格式&#41;](tabular-models/ssas-calculated-columns-create-a-calculated-column.md) 和[建立及管理量值 &#40;SSAS 表格式&#41;](tabular-models/measures-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="08fbc-127">For more information, see [Create a Calculated Column &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns-create-a-calculated-column.md) and [Create and Manage Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fbc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08fbc-128">See Also</span></span>  
 [<span data-ttu-id="08fbc-129">計算 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="08fbc-129">Calculations &#40;SSAS Tabular&#41;</span></span>](tabular-models/calculations-ssas-tabular.md)  
  
  
