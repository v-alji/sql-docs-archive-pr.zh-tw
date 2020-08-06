---
title: '[篩選] 對話方塊 ([) 的挖掘精確度圖表 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71e884a9-7ec4-4459-a4c4-87f6c796d478
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcdfb7cd7b425c3f8c4711e8b1812afc12898e1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598049"
---
# <a name="filter-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="147d8-102">篩選對話方塊 (採礦精確度圖表)</span><span class="sxs-lookup"><span data-stu-id="147d8-102">Filter Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="147d8-103">[篩選]\*\*\*\* 對話方塊會幫助您建立可套用至資料集的條件。</span><span class="sxs-lookup"><span data-stu-id="147d8-103">The **Filter** dialog box helps you build conditions that you can apply to a data set.</span></span> <span data-ttu-id="147d8-104">此資料集可以是用於測試的外部資料集，或是用於定型採礦模型的案例資料。</span><span class="sxs-lookup"><span data-stu-id="147d8-104">The data set can be an external data set used for testing, or the case data used to train a mining model.</span></span> <span data-ttu-id="147d8-105">此對話方塊可幫助您建立準則，您可以在 [資料集篩選器]\*\*\*\* 對話方塊或 [模型篩選器]\*\*\*\* 對話方塊中，將這些準則儲存為更複雜之篩選準則的一部分。</span><span class="sxs-lookup"><span data-stu-id="147d8-105">This dialog box helps you build criteria that you can save as part of more complex filter criteria in either the **Data Set Filter** dialog box or the **Model Filter** dialog box.</span></span>  
  
-   <span data-ttu-id="147d8-106">[資料集篩選器]\*\*\*\* 對話方塊可從 [採礦精確度圖表]\*\*\*\* 設計師的 [輸入選擇]\*\*\*\* 索引標籤中存取。</span><span class="sxs-lookup"><span data-stu-id="147d8-106">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="147d8-107">[模型篩選器]\*\*\*\* 對話方塊可從 [資料採礦] 設計工具的 [採礦模型]\*\*\*\* 索引標籤中存取。</span><span class="sxs-lookup"><span data-stu-id="147d8-107">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Mining designer.</span></span>  
  
 <span data-ttu-id="147d8-108">如果您要將篩選套用到採礦模型，請先使用 [模型篩選器]\*\*\*\* 對話方塊來選擇資料表。</span><span class="sxs-lookup"><span data-stu-id="147d8-108">If you are applying a filter to a mining model, first you use the **Model Filter** dialog box to choose a table.</span></span> <span data-ttu-id="147d8-109">然後，您可以使用 [篩選]\*\*\*\* 對話方塊，建立只套用至該資料表的條件。</span><span class="sxs-lookup"><span data-stu-id="147d8-109">Then, you can use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="147d8-110">如果您要建立可套用至外部測試資料集的篩選，請先使用 [資料集篩選器]\*\*\*\* 對話方塊，從資料來源檢視中的資料表清單選擇資料表。</span><span class="sxs-lookup"><span data-stu-id="147d8-110">If you are creating a filter to apply to an external test data set, first you use the **Data Set Filter** dialog box to choose a table from the list of tables in a data source view.</span></span> <span data-ttu-id="147d8-111">然後，您可以使用 [篩選]\*\*\*\* 對話方塊，建立只套用至該資料表的條件。</span><span class="sxs-lookup"><span data-stu-id="147d8-111">Then, you use the **Filter** dialog box to build conditions that apply only to that table.</span></span>  
  
 <span data-ttu-id="147d8-112">在建立套用至單一資料表的一組條件之後，[!INCLUDE[clickOK](../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="147d8-112">After you have created a set of conditions that apply to a single table, [!INCLUDE[clickOK](../includes/clickok-md.md)].</span></span> <span data-ttu-id="147d8-113">您在 [篩選]\*\*\*\* 對話方塊中所做的變更會自動加入上層對話方塊 ([資料集篩選器]\*\*\*\* 或 [模型篩選器]\*\*\*\*) 中的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="147d8-113">The changes that you made in the **Filter** dialog box are automatically added to the filter expression in the parent dialog box, **Data Set Filter** or **Model Filter**.</span></span>  
  
 <span data-ttu-id="147d8-114">如果您將篩選套用至新的資料集，則只會使用現有的資料採礦模型來評估資料集中符合條件的案例。</span><span class="sxs-lookup"><span data-stu-id="147d8-114">If you apply the filter to the new data set, the existing data mining model is used to evaluate only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="147d8-115">但是，如果要將篩選套用至採礦模型本身，則只會針對採礦模型中符合這些準則的案例來評估模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="147d8-115">However, if you apply the filter to the mining model itself, the accuracy of the model is assessed for only those cases within the mining model that meet those criteria.</span></span>  
  
 <span data-ttu-id="147d8-116">**如需詳細資訊，請參閱：** [測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="147d8-116">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="147d8-117">選項</span><span class="sxs-lookup"><span data-stu-id="147d8-117">Options</span></span>  
 <span data-ttu-id="147d8-118">**條件**</span><span class="sxs-lookup"><span data-stu-id="147d8-118">**Conditions**</span></span>  
 <span data-ttu-id="147d8-119">包含資料行的方格，您會在這裡根據 [資料集篩選器]\*\*\*\* 對話方塊中選取的資料表指定資料行的條件。</span><span class="sxs-lookup"><span data-stu-id="147d8-119">A grid that contains columns where you specify conditions on columns from the table that you selected in the **Data Set Filter** dialog box.</span></span>  
  
|<span data-ttu-id="147d8-120">值</span><span class="sxs-lookup"><span data-stu-id="147d8-120">Value</span></span>|<span data-ttu-id="147d8-121">描述</span><span class="sxs-lookup"><span data-stu-id="147d8-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="147d8-122">**和/或**</span><span class="sxs-lookup"><span data-stu-id="147d8-122">**And/Or**</span></span>|<span data-ttu-id="147d8-123">按一下此選項，指定是要將 AND 運算子還是 OR 運算子套用到這一行的條件。</span><span class="sxs-lookup"><span data-stu-id="147d8-123">Click to specify whether to apply the AND operator or the OR operator to the condition on this line.</span></span> <span data-ttu-id="147d8-124">只有當您從 [採礦結構資料行]\*\*\*\* 清單中選取資料行之後，才可以使用這些值。</span><span class="sxs-lookup"><span data-stu-id="147d8-124">These values become available only after you have selected a column from the **Mining Structure Column** list.</span></span>|  
|<span data-ttu-id="147d8-125">**採礦結構資料行**</span><span class="sxs-lookup"><span data-stu-id="147d8-125">**Mining Structure Column**</span></span>|<span data-ttu-id="147d8-126">按一下此選項，從資料表中包含的資料行清單選取資料行，此資料表是您從 [資料集篩選器]\*\*\*\* 對話方塊中的資料來源選取而來。</span><span class="sxs-lookup"><span data-stu-id="147d8-126">Click to select a column from the list of the columns contained in the table that you selected from the data source in the **Data Set Filter** dialog box.</span></span>|  
|<span data-ttu-id="147d8-127">**運算子**</span><span class="sxs-lookup"><span data-stu-id="147d8-127">**Operator**</span></span>|<span data-ttu-id="147d8-128">從清單選取運算子。</span><span class="sxs-lookup"><span data-stu-id="147d8-128">Select an operator from the list.</span></span> <span data-ttu-id="147d8-129">可用的運算子取決於資料行的資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="147d8-129">The operators that are available depend on the data type of the column.</span></span><br /><br /> <span data-ttu-id="147d8-130">如果此資料行包含離散值，則只能使用下列運算子：</span><span class="sxs-lookup"><span data-stu-id="147d8-130">If the column contains discrete values, only the following operators are available:</span></span><br /><br /> <span data-ttu-id="147d8-131">= (equal to)、<> (不等於)、IS NOT NULL、IS NULL。</span><span class="sxs-lookup"><span data-stu-id="147d8-131">= (equal to), <> (not equal to), IS NOT NULL, IS NULL.</span></span><br /><br /> <span data-ttu-id="147d8-132">如果此資料行包含連續值，則也支援大於的運算子和小於運算。</span><span class="sxs-lookup"><span data-stu-id="147d8-132">If the column contains continuous values, operators for greater than and less than operations are also supported.</span></span>|  
|<span data-ttu-id="147d8-133">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="147d8-133">**Value**</span></span>|<span data-ttu-id="147d8-134">輸入當做條件使用的值。</span><span class="sxs-lookup"><span data-stu-id="147d8-134">Type a value to use as a condition.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="147d8-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="147d8-135">See Also</span></span>  
 <span data-ttu-id="147d8-136">[測試和驗證工作，以及如何 &#40;資料採礦&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="147d8-136">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="147d8-137">&#40;資料採礦&#41;的挖掘精確度圖表設計工具</span><span class="sxs-lookup"><span data-stu-id="147d8-137">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
