---
title: 第10課：建立階層 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4d0982a05c37c28167e44e3f9f082ea5113b59bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700450"
---
# <a name="lesson-10-create-hierarchies"></a><span data-ttu-id="ea50e-102">第 10 課：建立階層</span><span class="sxs-lookup"><span data-stu-id="ea50e-102">Lesson 10: Create Hierarchies</span></span>
  <span data-ttu-id="ea50e-103">在這一課，您將建立階層。</span><span class="sxs-lookup"><span data-stu-id="ea50e-103">In this lesson, you will create hierarchies.</span></span> <span data-ttu-id="ea50e-104">階層是以層級排列的資料行群組；例如，[地理位置] 階層可能有 [國家/地區]、[州省]、[縣市]、[縣 (市)] 的子層級。</span><span class="sxs-lookup"><span data-stu-id="ea50e-104">Hierarchies are groups of columns arranged in levels; for example, a Geography hierarchy might have sub-levels for Country, State, County, and City.</span></span> <span data-ttu-id="ea50e-105">階層可以與報告用戶端應用程式欄位清單中的其他資料行分開顯示，讓用戶端使用者更易於在報告中導覽及包含階層。</span><span class="sxs-lookup"><span data-stu-id="ea50e-105">Hierarchies can appear separate from other columns in a reporting client application field list, making them easier for client users to navigate and include in a report.</span></span> <span data-ttu-id="ea50e-106">如需詳細資訊，請參閱[ &#40;SSAS 表格式&#41;](tabular-models/hierarchies-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="ea50e-106">To learn more, see [Hierarchies &#40;SSAS Tabular&#41;](tabular-models/hierarchies-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="ea50e-107">若要建立階層，您將使用 [圖表檢視]\*\* 中的模型設計師。</span><span class="sxs-lookup"><span data-stu-id="ea50e-107">To create hierarchies, you will use the model designer in *Diagram View*.</span></span> <span data-ttu-id="ea50e-108">不支援在模型設計師的 [資料檢視] 中建立及管理階層。</span><span class="sxs-lookup"><span data-stu-id="ea50e-108">Creating and managing hierarchies is not supported in the model designer in Data View.</span></span>  
  
 <span data-ttu-id="ea50e-109">這堂課的預估完成時間：**20 分鐘**</span><span class="sxs-lookup"><span data-stu-id="ea50e-109">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ea50e-110">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ea50e-110">Prerequisites</span></span>  
 <span data-ttu-id="ea50e-111">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="ea50e-111">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="ea50e-112">在執行本課程的工作之前，您應已完成上一課： [第 9 課：建立檢視方塊](lesson-8-create-perspectives.md)。</span><span class="sxs-lookup"><span data-stu-id="ea50e-112">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 9: Create Perspectives](lesson-8-create-perspectives.md).</span></span>  
  
## <a name="create-hierarchies"></a><span data-ttu-id="ea50e-113">建立階層</span><span class="sxs-lookup"><span data-stu-id="ea50e-113">Create Hierarchies</span></span>  
  
#### <a name="to-create-a-category-hierarchy-in-the-product-table"></a><span data-ttu-id="ea50e-114">在產品資料表中建立類別目錄階層</span><span class="sxs-lookup"><span data-stu-id="ea50e-114">To create a Category hierarchy in the Product table</span></span>  
  
1.  <span data-ttu-id="ea50e-115">在模型設計師中，按一下 `Model` 功能表，然後指向 [**模型視圖**]，再按一下 [**圖表視圖**]。</span><span class="sxs-lookup"><span data-stu-id="ea50e-115">In the model designer, click on the `Model` menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ea50e-116">使用模型設計師右上方的 [迷你地圖] 控制項，即可變更您可以在 [圖表檢視] 中檢視物件的方式。</span><span class="sxs-lookup"><span data-stu-id="ea50e-116">Use the Minimap controls at the top-right of the model designer to change how you can view objects in Diagram View.</span></span> <span data-ttu-id="ea50e-117">如果您將物件重新定位在 [圖表檢視] 中，該檢視會在您儲存專案時保留。</span><span class="sxs-lookup"><span data-stu-id="ea50e-117">If you reposition objects in Diagram View, that view will be retained when you save the project.</span></span>  
  
2.  <span data-ttu-id="ea50e-118">在模型設計師中，以滑鼠右鍵按一下 `Product` 資料表，然後按一下 [**建立**階層]。</span><span class="sxs-lookup"><span data-stu-id="ea50e-118">In the model designer, right-click the `Product` table, and then click **Create Hierarchy**.</span></span> <span data-ttu-id="ea50e-119">新的階層會出現在資料表視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="ea50e-119">A new hierarchy appears at the bottom of the table window.</span></span>  
  
3.  <span data-ttu-id="ea50e-120">在階層名稱中，輸入來重新命名階層， `Category` 然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="ea50e-120">In the hierarchy name, rename the hierarchy by typing `Category`, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="ea50e-121">在 `Product` 資料表中，按一下 [ **Product Category Name** ] 資料行，然後將它拖曳到階層 `Category` 中，然後在名稱頂端放開 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="ea50e-121">In the `Product` table, click the **Product Category Name** column, then drag it to the `Category` hierarchy, and then release on top of the `Category` name.</span></span>  
  
5.  <span data-ttu-id="ea50e-122">在階層中 `Category` ，以滑鼠右鍵按一下 [ **Product Category Name** ] 資料行，然後按一下 [**重新命名**]，再輸入 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="ea50e-122">In the `Category` hierarchy, right-click the **Product Category Name** column, then click **Rename**, and then type `Category`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ea50e-123">重新命名階層中的資料行，並不會將資料表中的該資料行重新命名。</span><span class="sxs-lookup"><span data-stu-id="ea50e-123">Renaming a column in a hierarchy does not rename that column in the table.</span></span> <span data-ttu-id="ea50e-124">階層中的資料行只是資料表中資料行的表示。</span><span class="sxs-lookup"><span data-stu-id="ea50e-124">A column in a hierarchy is just a representation of the column in the table.</span></span>  
  
6.  <span data-ttu-id="ea50e-125">在 `Product` 資料表中，以滑鼠右鍵按一下 [**產品子類別目錄名稱**] 資料行，然後在內容功能表中指向 [**加入至**階層]，然後按一下 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="ea50e-125">In the `Product` table, right-click the **Product Subcategory Name** column, then in the context menu, point to **Add to Hierarchy**, and then click `Category`.</span></span>  
  
7.  <span data-ttu-id="ea50e-126">將**產品子類別目錄名稱**重新命名為 `Subcategory` 。</span><span class="sxs-lookup"><span data-stu-id="ea50e-126">Rename **Product Subcategory Name** to `Subcategory`.</span></span>  
  
8.  <span data-ttu-id="ea50e-127">使用 click 和拖曳，或使用內容功能表中的 [**加入至**階層] 命令，將 [**模型名稱**] 和 [**產品名稱**] 資料行 (依序加入) ，並將它們放在 [**產品子類別目錄名稱**] 資料行下方。</span><span class="sxs-lookup"><span data-stu-id="ea50e-127">By using click and drag, or by using the **Add to Hierarchy** command in the context menu, add the **Model Name** and **Product Name** columns (in order) and place them beneath the **Product Subcategory Name** column.</span></span> <span data-ttu-id="ea50e-128">分別重新命名這些資料行 `Model` 和 `Product` 。</span><span class="sxs-lookup"><span data-stu-id="ea50e-128">Rename these columns `Model` and `Product`, respectively.</span></span>  
  
#### <a name="to-create-hierarchies-in-the-date-table"></a><span data-ttu-id="ea50e-129">在日期資料表中建立階層</span><span class="sxs-lookup"><span data-stu-id="ea50e-129">To create hierarchies in the Date table</span></span>  
  
1.  <span data-ttu-id="ea50e-130">在模型設計師中，以滑鼠右鍵按一下 [日期]\*\*\*\* 資料表，然後按一下 [建立階層]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea50e-130">In the model designer, right-click the **Date** table, and then click **Create Hierarchy**.</span></span>  
  
2.  <span data-ttu-id="ea50e-131">將階層重新命名為 **Calendar**。</span><span class="sxs-lookup"><span data-stu-id="ea50e-131">Rename the hierarchy to **Calendar**.</span></span>  
  
3.  <span data-ttu-id="ea50e-132">依序加入下列資料行，然後將它們重新命名：</span><span class="sxs-lookup"><span data-stu-id="ea50e-132">Add the following columns, in-order, and then rename them:</span></span>  
  
    |<span data-ttu-id="ea50e-133">資料行</span><span class="sxs-lookup"><span data-stu-id="ea50e-133">Column</span></span>|<span data-ttu-id="ea50e-134">重新命名為：</span><span class="sxs-lookup"><span data-stu-id="ea50e-134">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="ea50e-135">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="ea50e-135">Calendar Year</span></span>|<span data-ttu-id="ea50e-136">Year</span><span class="sxs-lookup"><span data-stu-id="ea50e-136">Year</span></span>|  
    |<span data-ttu-id="ea50e-137">Calendar Semester</span><span class="sxs-lookup"><span data-stu-id="ea50e-137">Calendar Semester</span></span>|<span data-ttu-id="ea50e-138">半年度</span><span class="sxs-lookup"><span data-stu-id="ea50e-138">Semester</span></span>|  
    |<span data-ttu-id="ea50e-139">Calendar Quarter</span><span class="sxs-lookup"><span data-stu-id="ea50e-139">Calendar Quarter</span></span>|<span data-ttu-id="ea50e-140">季</span><span class="sxs-lookup"><span data-stu-id="ea50e-140">Quarter</span></span>|  
    |<span data-ttu-id="ea50e-141">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="ea50e-141">Month Calendar</span></span>|<span data-ttu-id="ea50e-142">Month</span><span class="sxs-lookup"><span data-stu-id="ea50e-142">Month</span></span>|  
    |<span data-ttu-id="ea50e-143">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="ea50e-143">Day Of Month</span></span>|<span data-ttu-id="ea50e-144">天</span><span class="sxs-lookup"><span data-stu-id="ea50e-144">Day</span></span>|  
  
4.  <span data-ttu-id="ea50e-145">在 [日期]\*\*\*\* 資料表中重複上述步驟，建立 [Fiscal]\*\*\*\* 階層，包括下列資料行：</span><span class="sxs-lookup"><span data-stu-id="ea50e-145">In the **Date** table, repeat the above steps, creating a **Fiscal** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="ea50e-146">資料行</span><span class="sxs-lookup"><span data-stu-id="ea50e-146">Column</span></span>|<span data-ttu-id="ea50e-147">重新命名為：</span><span class="sxs-lookup"><span data-stu-id="ea50e-147">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="ea50e-148">Fiscal Year</span><span class="sxs-lookup"><span data-stu-id="ea50e-148">Fiscal Year</span></span>|<span data-ttu-id="ea50e-149">Year</span><span class="sxs-lookup"><span data-stu-id="ea50e-149">Year</span></span>|  
    |<span data-ttu-id="ea50e-150">Fiscal Semester</span><span class="sxs-lookup"><span data-stu-id="ea50e-150">Fiscal Semester</span></span>|<span data-ttu-id="ea50e-151">半年度</span><span class="sxs-lookup"><span data-stu-id="ea50e-151">Semester</span></span>|  
    |<span data-ttu-id="ea50e-152">Fiscal Quarter</span><span class="sxs-lookup"><span data-stu-id="ea50e-152">Fiscal Quarter</span></span>|<span data-ttu-id="ea50e-153">季</span><span class="sxs-lookup"><span data-stu-id="ea50e-153">Quarter</span></span>|  
    |<span data-ttu-id="ea50e-154">Month Calendar</span><span class="sxs-lookup"><span data-stu-id="ea50e-154">Month Calendar</span></span>|<span data-ttu-id="ea50e-155">Month</span><span class="sxs-lookup"><span data-stu-id="ea50e-155">Month</span></span>|  
    |<span data-ttu-id="ea50e-156">Day Of Month</span><span class="sxs-lookup"><span data-stu-id="ea50e-156">Day Of Month</span></span>|<span data-ttu-id="ea50e-157">天</span><span class="sxs-lookup"><span data-stu-id="ea50e-157">Day</span></span>|  
  
5.  <span data-ttu-id="ea50e-158">最後，在 [日期]\*\*\*\* 資料表中重複上述步驟，建立 [Production Calendar]\*\*\*\* 階層，包括下列資料行：</span><span class="sxs-lookup"><span data-stu-id="ea50e-158">Finally, in the **Date** table, repeat the above steps, creating a **Production Calendar** hierarchy, including the following columns:</span></span>  
  
    |<span data-ttu-id="ea50e-159">資料行</span><span class="sxs-lookup"><span data-stu-id="ea50e-159">Column</span></span>|<span data-ttu-id="ea50e-160">重新命名為：</span><span class="sxs-lookup"><span data-stu-id="ea50e-160">Rename to:</span></span>|  
    |------------|----------------|  
    |<span data-ttu-id="ea50e-161">Calendar Year</span><span class="sxs-lookup"><span data-stu-id="ea50e-161">Calendar Year</span></span>|<span data-ttu-id="ea50e-162">Year</span><span class="sxs-lookup"><span data-stu-id="ea50e-162">Year</span></span>|  
    |<span data-ttu-id="ea50e-163">Week Number Of Year</span><span class="sxs-lookup"><span data-stu-id="ea50e-163">Week Number Of Year</span></span>|<span data-ttu-id="ea50e-164">週</span><span class="sxs-lookup"><span data-stu-id="ea50e-164">Week</span></span>|  
    |<span data-ttu-id="ea50e-165">週中的日</span><span class="sxs-lookup"><span data-stu-id="ea50e-165">Day Of Week</span></span>|<span data-ttu-id="ea50e-166">天</span><span class="sxs-lookup"><span data-stu-id="ea50e-166">Day</span></span>|  
  
## <a name="next-steps"></a><span data-ttu-id="ea50e-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ea50e-167">Next Steps</span></span>  
 <span data-ttu-id="ea50e-168">若要繼續進行本教學課程，請前往下一課： [第 11 課：建立資料分割](lesson-10-create-partitions.md)。</span><span class="sxs-lookup"><span data-stu-id="ea50e-168">To continue this tutorial, go to the next lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
  
