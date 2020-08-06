---
title: 指定資料行對應對話方塊 () 的挖掘精確度圖表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ede835567f678f4152b3d1944f3c2c7160c6837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598567"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="f49d7-102">指定資料行對應對話方塊 (採礦精確度圖表)</span><span class="sxs-lookup"><span data-stu-id="f49d7-102">Specify Column Mapping Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="f49d7-103">使用 [指定資料行對應]\*\*\*\* 索引標籤可從外部資料來源選取資料表，並且將資料行對應至資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f49d7-103">Use the **Specify Column Mapping** tab to select tables from an external data source and map the columns to a data mining model.</span></span> <span data-ttu-id="f49d7-104">接著您就可以使用該外部資料來測試採礦模型的精確度，並將結果顯示在精確度圖表中。</span><span class="sxs-lookup"><span data-stu-id="f49d7-104">You can then use the external data to test the accuracy of a mining model and displays the results in the accuracy chart.</span></span>  
  
 <span data-ttu-id="f49d7-105">**如需詳細資訊，請參閱：** [測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="f49d7-105">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="f49d7-106">選項</span><span class="sxs-lookup"><span data-stu-id="f49d7-106">Options</span></span>  
 <span data-ttu-id="f49d7-107">**採礦結構**</span><span class="sxs-lookup"><span data-stu-id="f49d7-107">**Mining Structure**</span></span>  
 <span data-ttu-id="f49d7-108">顯示選取的採礦結構，其中包含您要測試的模型。</span><span class="sxs-lookup"><span data-stu-id="f49d7-108">Displays the selected mining structure that contains the model that you will test.</span></span>  
  
 <span data-ttu-id="f49d7-109">**選取結構**</span><span class="sxs-lookup"><span data-stu-id="f49d7-109">**Select Structure**</span></span>  
 <span data-ttu-id="f49d7-110">按一下即可開啟 [選取採礦結構]\*\*\*\* 對話方塊，然後選取不同的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="f49d7-110">Click to open the **Select Mining Structure** dialog box and select a different mining structure.</span></span>  
  
 <span data-ttu-id="f49d7-111">**選取輸入資料表**</span><span class="sxs-lookup"><span data-stu-id="f49d7-111">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="f49d7-112">顯示用來產生增益圖的選取之輸入資料表。</span><span class="sxs-lookup"><span data-stu-id="f49d7-112">Displays the selected input tables that are used to generate the lift chart.</span></span> <span data-ttu-id="f49d7-113">選取其中包含將用來測試模型精確度之測試資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="f49d7-113">Select the table that contains the test data that you will use to test the accuracy of the models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f49d7-114">如果窗格不包含任何資料表，請按一下 [選取案例資料表]\*\*\*\* 以從資料來源檢視新增資料表。</span><span class="sxs-lookup"><span data-stu-id="f49d7-114">If the pane does not contain any tables, click **Select Case Table** to add tables from a data source view.</span></span>  
  
 <span data-ttu-id="f49d7-115">**移除資料表**</span><span class="sxs-lookup"><span data-stu-id="f49d7-115">**Remove Table**</span></span>  
 <span data-ttu-id="f49d7-116">移除選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="f49d7-116">Removes the selected table.</span></span> <span data-ttu-id="f49d7-117">如果尚未選取資料表，或在 [選取輸入資料表]\*\*\*\* 清單中未顯示任何資料表，則此按鈕會停用。</span><span class="sxs-lookup"><span data-stu-id="f49d7-117">This button is disabled if a table has not been selected or if no tables are displayed in the **Select Input Tables** list.</span></span>  
  
 <span data-ttu-id="f49d7-118">**選取案例資料表**</span><span class="sxs-lookup"><span data-stu-id="f49d7-118">**Select Case Table**</span></span>  
 <span data-ttu-id="f49d7-119">按一下即可開啟 [選取資料表]\*\*\*\* 對話方塊，並選取資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="f49d7-119">Click to open the **Select Table** dialog box and select a data source view.</span></span>  
  
 <span data-ttu-id="f49d7-120">**注意**：只有當未選取案例資料表時，才會顯示這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="f49d7-120">**Note** This button appears only if a case table has not been selected.</span></span> <span data-ttu-id="f49d7-121">若要啟用按鈕而使您可以選取不同的案例資料表，請選取所有現有的資料表，然後再按一下 [移除資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f49d7-121">To enable the button so that you can select a different case table, clear the list by selecting all existing tables and then clicking **Remove Table**.</span></span>  
  
 <span data-ttu-id="f49d7-122">**選取巢狀資料表**</span><span class="sxs-lookup"><span data-stu-id="f49d7-122">**Select Nested Table**</span></span>  
 <span data-ttu-id="f49d7-123">開啟 [選取資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f49d7-123">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="f49d7-124">唯有選取了案例資料表時，才會顯示這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="f49d7-124">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="f49d7-125">如果關聯的採礦結構未包含巢狀資料表，這個按鈕就會停用。</span><span class="sxs-lookup"><span data-stu-id="f49d7-125">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="f49d7-126">**修改聯結**</span><span class="sxs-lookup"><span data-stu-id="f49d7-126">**Modify Join**</span></span>  
 <span data-ttu-id="f49d7-127">開啟 [指定巢狀聯結]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f49d7-127">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="f49d7-128">唯有選取了巢狀資料表時，才可以使用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="f49d7-128">This button is active only if the nested table is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49d7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f49d7-129">See Also</span></span>  
 <span data-ttu-id="f49d7-130">[測試和驗證工作，以及如何 &#40;資料採礦&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f49d7-130">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="f49d7-131">&#40;資料採礦&#41;的挖掘精確度圖表設計工具</span><span class="sxs-lookup"><span data-stu-id="f49d7-131">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
