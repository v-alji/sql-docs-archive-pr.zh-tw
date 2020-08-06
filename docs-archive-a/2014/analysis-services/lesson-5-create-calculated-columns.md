---
title: 第6課：建立計算結果欄 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcebf61955e230c9e61c955683b897026553cb52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594796"
---
# <a name="lesson-6-create-calculated-columns"></a><span data-ttu-id="cc7cc-102">第 6 課：建立導出資料行</span><span class="sxs-lookup"><span data-stu-id="cc7cc-102">Lesson 6: Create Calculated Columns</span></span>
  <span data-ttu-id="cc7cc-103">在這一課，您將藉由加入導出資料行的方式在模型中建立新資料。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-103">In this lesson, you will create new data in your model by adding calculated columns.</span></span> <span data-ttu-id="cc7cc-104">導出資料行是以已存在模型中的資料為基礎。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-104">A calculated column is based on data that already exists in the model.</span></span> <span data-ttu-id="cc7cc-105">如需詳細資訊，請參閱[導出資料行 &#40;SSAS 表格式&#41;](tabular-models/ssas-calculated-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-105">To learn more, see [Calculated Columns &#40;SSAS Tabular&#41;](tabular-models/ssas-calculated-columns.md).</span></span>  
  
 <span data-ttu-id="cc7cc-106">您將在三個不同資料表中建立五個新的導出資料行。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-106">You will create five new calculated columns in three different tables.</span></span> <span data-ttu-id="cc7cc-107">各項工作的步驟稍有不同。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-107">The steps are slightly different for each task.</span></span> <span data-ttu-id="cc7cc-108">這樣做的目的在於說明，您可以透過數種方式建立新的資料行、重新命名資料行，以及將它們放到資料表中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-108">This is to show you there are several ways to create new columns, rename them, and place them in various locations in a table.</span></span>  
  
 <span data-ttu-id="cc7cc-109">完成本課程的估計時間： **15 分鐘**</span><span class="sxs-lookup"><span data-stu-id="cc7cc-109">Estimated time to complete this lesson: **15 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cc7cc-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="cc7cc-110">Prerequisites</span></span>  
 <span data-ttu-id="cc7cc-111">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="cc7cc-112">在執行本課中的工作之前，您應已完成上一課： [第 5 課：建立關聯性](lesson-4-create-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
## <a name="create-calculated-columns"></a><span data-ttu-id="cc7cc-113">建立導出資料行</span><span class="sxs-lookup"><span data-stu-id="cc7cc-113">Create Calculated Columns</span></span>  
  
#### <a name="create-a-month-calendar-calculated-column-in-the-date-table"></a><span data-ttu-id="cc7cc-114">在日期資料表中建立 Month Calendar 導出資料行</span><span class="sxs-lookup"><span data-stu-id="cc7cc-114">Create a Month Calendar calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="cc7cc-115">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中，按一下 [模型]\*\*\*\* 功能表，然後指向 [模型檢視]\*\*\*\*，再按一下 [資料檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-115">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, then point to **Model View**, and then click **Data View**.</span></span>  
  
     <span data-ttu-id="cc7cc-116">導出資料行只能使用模型設計師在「資料檢視」中建立。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-116">Calculated columns can only be created by using the model designer in Data View.</span></span>  
  
2.  <span data-ttu-id="cc7cc-117">在模型設計師中，按一下 [Date]\*\*\*\* 資料表 (索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-117">In the model designer, click the **Date** table (tab).</span></span>  
  
3.  <span data-ttu-id="cc7cc-118">以滑鼠右鍵按一下 [**日曆季**] 資料行，然後按一下 [**插入資料行**]。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-118">Right-click the **Calendar Quarter** column, and then click **Insert Column**.</span></span>  
  
     <span data-ttu-id="cc7cc-119">名為**CalculatedColumn1**的新資料行會插入 [**日曆季**] 資料行的左側。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-119">A new column named **CalculatedColumn1** is inserted to the left of the **Calendar Quarter** column.</span></span>  
  
4.  <span data-ttu-id="cc7cc-120">在資料表上方的公式列中，輸入下列公式。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-120">In the formula bar above the table, type the following formula.</span></span> <span data-ttu-id="cc7cc-121">「自動完成」會協助您輸入資料行和資料表的完整名稱，並列出可用的函式。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-121">AutoComplete helps you type the fully qualified names of columns and tables, and lists the functions that are available.</span></span>  
  
     `=RIGHT(" " & FORMAT([Month],"#0"), 2) & " - " & [Month Name]`  
  
     <span data-ttu-id="cc7cc-122">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-122">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="cc7cc-123">接著，計算結果欄的所有資料列就會填入值。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-123">Values are then populated for all the rows in the calculated column.</span></span> <span data-ttu-id="cc7cc-124">如果您在資料表中向下捲動，根據每個資料列中的資料，您會看到各資料列在此資料行中會有不同的值。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-124">If you scroll down through the table, you will see that rows can have different values for this column, based on the data that is in each row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cc7cc-125">如果您收到錯誤，請確認公式中的資料行名稱與您在 [第 3 課：重新命名資料行](rename-columns.md)中變更的資料行名稱相符。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-125">If you receive an error, verify the column names in the formula match the column names you changed in [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
5.  <span data-ttu-id="cc7cc-126">將此資料行重新命名為 `Month Calendar` 。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-126">Rename this column to `Month Calendar`.</span></span>  
  
 <span data-ttu-id="cc7cc-127">Month Calendar 導出資料行會提供可排序的月份名稱。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-127">The Month Calendar calculated column provides a sortable name for Month.</span></span>  
  
#### <a name="create-a-day-of-week-calculated-column-in-the-date-table"></a><span data-ttu-id="cc7cc-128">在日期資料表中建立 Day of Week 導出資料行</span><span class="sxs-lookup"><span data-stu-id="cc7cc-128">Create a Day of Week calculated column in the Date table</span></span>  
  
1.  <span data-ttu-id="cc7cc-129">在 [日期]\*\*\*\* 資料表仍為使用中狀態時，按一下 [資料行]\*\*\*\* 功能表，然後按一下 [加入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-129">With the **Date** table still active, click on the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="cc7cc-130">新的資料行就會加入資料表的最右側。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-130">A new column is added to the far right of the table</span></span>  
  
2.  <span data-ttu-id="cc7cc-131">在公式列中，輸入下列公式︰</span><span class="sxs-lookup"><span data-stu-id="cc7cc-131">In the formula bar, type the following formula:</span></span>  
  
     `=RIGHT(" " & FORMAT([Day Number Of Week],"#0"), 2) & " - " & [Day Name]`  
  
     <span data-ttu-id="cc7cc-132">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-132">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="cc7cc-133">將資料行重新命名為 `Day of Week` 。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-133">Rename the column to `Day of Week`.</span></span>  
  
4.  <span data-ttu-id="cc7cc-134">按一下欄位標題，然後將資料行拖曳到 [Day Name]\*\*\*\* 資料行和 [Day of Month]\*\*\*\* 資料行之間。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-134">Click on the column heading, and then drag the column between the **Day Name** column and the **Day of Month** column.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="cc7cc-135">移動資料表中的資料行可使導覽更方便。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-135">Moving columns in your table makes it easier to navigate.</span></span>  
  
 <span data-ttu-id="cc7cc-136">[Day of Week] 導出資料行會提供可排序的星期日期名稱。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-136">The Day of Week calculated column provides a sortable name for the day of week.</span></span>  
  
#### <a name="create-a-product-subcategory-name-calculated-column-in-the-product-table"></a><span data-ttu-id="cc7cc-137">在產品資料表中建立 Product Subcategory Name 導出資料行</span><span class="sxs-lookup"><span data-stu-id="cc7cc-137">Create a Product Subcategory Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="cc7cc-138">在模型設計師中，選取 [產品]\*\*\*\* 資料表。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-138">In the model designer, select the **Product** table.</span></span>  
  
2.  <span data-ttu-id="cc7cc-139">捲動到資料表的最右側。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-139">Scroll to the far right of the table.</span></span> <span data-ttu-id="cc7cc-140">請注意，最右邊的資料行名為 **[新增資料行]** \(斜體)，請按一下資料行標題。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-140">Notice the right-most column is named **Add Column** (italicized), click the column heading.</span></span>  
  
3.  <span data-ttu-id="cc7cc-141">在公式列中，輸入下列公式。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-141">In the formula bar, type the following formula.</span></span>  
  
     `=RELATED('Product Subcategory'[Product Subcategory Name])`  
  
     <span data-ttu-id="cc7cc-142">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-142">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="cc7cc-143">將資料行重新命名為 `Product Subcategory Name` 。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-143">Rename the column to `Product Subcategory Name`.</span></span>  
  
 <span data-ttu-id="cc7cc-144">[Product Subcategory Name] 導出資料行可用來在 [產品] 資料表中建立階層，其中包括來自 [產品子類別目錄] 資料表中 [Product Subcategory Name] 資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-144">The Product Subcategory Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Subcategory Name column in the Product Subcategory table.</span></span> <span data-ttu-id="cc7cc-145">階層不可跨越多個資料表。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-145">Hierarchies cannot span more than one table.</span></span> <span data-ttu-id="cc7cc-146">您稍後將在第 7 課中建立階層。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-146">You will create hierarchies later in Lesson 7.</span></span>  
  
#### <a name="create-a-product-category-name-calculated-column-in-the-product-table"></a><span data-ttu-id="cc7cc-147">在產品資料表中建立 Product Category Name 導出資料行</span><span class="sxs-lookup"><span data-stu-id="cc7cc-147">Create a Product Category Name calculated column in the Product table</span></span>  
  
1.  <span data-ttu-id="cc7cc-148">在 [產品]\*\*\*\* 資料表仍為使用中狀態時，按一下 [資料行]\*\*\*\* 功能表，然後按一下 [加入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-148">With the **Product** table still active, click the **Column** menu, and then click **Add Column**.</span></span>  
  
2.  <span data-ttu-id="cc7cc-149">在公式列中，輸入下列公式︰</span><span class="sxs-lookup"><span data-stu-id="cc7cc-149">In the formula bar, type the following formula:</span></span>  
  
     `=RELATED('Product Category'[Product Category Name])`  
  
     <span data-ttu-id="cc7cc-150">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-150">When you have finished building the formula, press ENTER.</span></span>  
  
3.  <span data-ttu-id="cc7cc-151">將資料行重新命名為 `Product Category Name` 。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-151">Rename the column to `Product Category Name`.</span></span>  
  
 <span data-ttu-id="cc7cc-152">[Product Category Name] 導出資料行可用來在 [產品] 資料表中建立階層，其中包括來自 [產品類別目錄] 資料表中 [Product Category Name] 資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-152">The Product Category Name calculated column is used to create a hierarchy in the Product table which includes data from the Product Category Name column in the Product Category table.</span></span> <span data-ttu-id="cc7cc-153">階層不可跨越多個資料表。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-153">Hierarchies cannot span more than one table.</span></span>  
  
#### <a name="create-a-margin-calculated-column-in-the-internet-sales-table"></a><span data-ttu-id="cc7cc-154">在網際網路銷售資料表中建立 Margin 導出資料行</span><span class="sxs-lookup"><span data-stu-id="cc7cc-154">Create a Margin calculated column in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="cc7cc-155">在模型設計師中，選取 [網際網路銷售]\*\*\*\* 資料表。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-155">In the model designer, select the **Internet Sales** table.</span></span>  
  
2.  <span data-ttu-id="cc7cc-156">加入新資料行。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-156">Add a new column.</span></span>  
  
3.  <span data-ttu-id="cc7cc-157">在公式列中，輸入下列公式︰</span><span class="sxs-lookup"><span data-stu-id="cc7cc-157">In the formula bar, type the following formula:</span></span>  
  
     `=[Sales Amount]-[Total Product Cost]`  
  
     <span data-ttu-id="cc7cc-158">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-158">When you have finished building the formula, press ENTER.</span></span>  
  
4.  <span data-ttu-id="cc7cc-159">將資料行重新命名為 `Margin` 。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-159">Rename the column to `Margin`.</span></span>  
  
5.  <span data-ttu-id="cc7cc-160">將這個資料行拖曳至 [Sales Amount]\*\*\*\* 資料行和 [Tax Amt]\*\*\*\* 資料行之間。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-160">Drag the column between the **Sales Amount** column and the **Tax Amt** column.</span></span>  
  
 <span data-ttu-id="cc7cc-161">[Margin] 導出資料行可用來分析每個 (產品) 資料列的利率。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-161">The Margin calculated column is used to analyze profit margins for each (product) row.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="cc7cc-162">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cc7cc-162">Next Step</span></span>  
 <span data-ttu-id="cc7cc-163">若要繼續進行這一課，請前往下一課： [第 7 課：建立量值](lesson-6-create-measures.md)。</span><span class="sxs-lookup"><span data-stu-id="cc7cc-163">To continue this lesson, go to the next lesson: [Lesson 7: Create Measures](lesson-6-create-measures.md).</span></span>  
  
  
