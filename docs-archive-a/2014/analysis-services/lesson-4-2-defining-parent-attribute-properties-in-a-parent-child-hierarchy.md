---
title: 在父子式階層中定義父屬性屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2d78fa73-a13b-4e12-bbd0-43e5307f760c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1dfa4340bdc161809cf3821e5cb1f0609399e1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597423"
---
# <a name="defining-parent-attribute-properties-in-a-parent-child-hierarchy"></a><span data-ttu-id="19ed1-102">定義父子式階層中父屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="19ed1-102">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>
  <span data-ttu-id="19ed1-103">父子式階層是指維度中以兩個資料表資料行為基礎的階層。</span><span class="sxs-lookup"><span data-stu-id="19ed1-103">A parent-child hierarchy is a hierarchy in a dimension that is based on two table columns.</span></span> <span data-ttu-id="19ed1-104">這些資料行會一起定義維度成員之間的階層式關聯性。</span><span class="sxs-lookup"><span data-stu-id="19ed1-104">Together, these columns define the hierarchical relationships among the members of the dimension.</span></span> <span data-ttu-id="19ed1-105">第一個名稱為「成員索引鍵資料行」\*\* 的資料行會識別每個維度成員。</span><span class="sxs-lookup"><span data-stu-id="19ed1-105">The first column, called the *member key column*, identifies each dimension member.</span></span> <span data-ttu-id="19ed1-106">另一個名稱為「父資料行」\*\* 資料行則會識別每個維度成員的父系。</span><span class="sxs-lookup"><span data-stu-id="19ed1-106">The other column, called the *parent column*, identifies the parent of each dimension member.</span></span> <span data-ttu-id="19ed1-107">父屬性的 **NamingTemplate** 屬性決定父子式階層中每個層級的名稱，而 **MembersWithData** 屬性則決定是否應該顯示父成員的資料。</span><span class="sxs-lookup"><span data-stu-id="19ed1-107">The **NamingTemplate** property of a parent attribute determines the name of each level in the parent-child hierarchy, and the **MembersWithData** property determines whether data for parent members should be displayed.</span></span>

 <span data-ttu-id="19ed1-108">如需詳細資訊，[請參閱父子式階層](multidimensional-models/parent-child-dimension.md)，[父子式階層中的屬性](multidimensional-models/parent-child-dimension-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="19ed1-108">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md), [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>

> [!NOTE]
>  <span data-ttu-id="19ed1-109">當您使用「維度精靈」來建立維度時，此精靈會辨識具有父子式關聯性的資料表，並自動定義父子式階層。</span><span class="sxs-lookup"><span data-stu-id="19ed1-109">When you use the Dimension Wizard to create a dimension, the wizard recognizes the tables that have parent-child relationships and automatically defines the parent-child hierarchy for you.</span></span>

 <span data-ttu-id="19ed1-110">在這個主題的工作中，您會建立一個命名範本，而它會在 [Employee (員工)]\*\*\*\* 維度中定義父子式階層中每一個層級的名稱。</span><span class="sxs-lookup"><span data-stu-id="19ed1-110">In the tasks in this topic, you will create a naming template that defines the name for each level in the parent-child hierarchy in the **Employee** dimension.</span></span> <span data-ttu-id="19ed1-111">接著，您將會設定父屬性來隱藏所有的父資料，以便只顯示分葉層級成員的銷售量。</span><span class="sxs-lookup"><span data-stu-id="19ed1-111">You will then configure the parent attribute to hide all parent data, so that only the sales for leaf-level members are displayed.</span></span>

## <a name="browsing-the-employee-dimension"></a><span data-ttu-id="19ed1-112">瀏覽 Employee 維度</span><span class="sxs-lookup"><span data-stu-id="19ed1-112">Browsing the Employee Dimension</span></span>

1.  <span data-ttu-id="19ed1-113">在方案總管中，按兩下 **維度** 資料夾中的 **Employee.dim** ，即可針對 [Employee (員工)] 維度開啟維度設計師。</span><span class="sxs-lookup"><span data-stu-id="19ed1-113">In Solution Explorer, double-click **Employee.dim** in the **Dimensions** folder to open Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="19ed1-114">按一下 [瀏覽器]\*\*\*\* 索引標籤，確認已在 [階層]\*\*\*\* 清單中選取 [Employee (員工)]\*\*\*\*，然後展開 [All Employees (所有員工)]\*\*\*\* 成員。</span><span class="sxs-lookup"><span data-stu-id="19ed1-114">Click the **Browser** tab, verify that **Employees** is selected in the **Hierarchy** list, and then expand the **All Employees** member.</span></span>

     <span data-ttu-id="19ed1-115">請注意，在這個父子式階層中， **Ken J. Sánchez** 為最上層的主管。</span><span class="sxs-lookup"><span data-stu-id="19ed1-115">Notice that **Ken J. Sánchez** is the top-level manager in this parent-child hierarchy.</span></span>

3.  <span data-ttu-id="19ed1-116">選取 **Ken J. Sánchez** 成員。</span><span class="sxs-lookup"><span data-stu-id="19ed1-116">Select the **Ken J. Sánchez** member.</span></span>

     <span data-ttu-id="19ed1-117">請注意，這個成員的層級名稱是 [Level 02 (層級 02)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-117">Notice that the level name for this member is **Level 02**.</span></span> <span data-ttu-id="19ed1-118"> (層級名稱會出現在**目前層級之後：** 緊接在 [**所有員工**] 成員的上方。下一項工作中 ) ，您將為每個層級定義更具描述性的名稱。</span><span class="sxs-lookup"><span data-stu-id="19ed1-118">(The level name appears after **Current level:** immediately above the **All Employees** member.) In the next task, you will define more descriptive names for each level.</span></span>

4.  <span data-ttu-id="19ed1-119">展開 **Ken J. Sánchez** 以檢視向這位主管報告的員工姓名，然後選取 **Brian S. Welcker** 來檢視這個層級的名稱。</span><span class="sxs-lookup"><span data-stu-id="19ed1-119">Expand **Ken J. Sánchez** to view the names of the employees who report to this manager, and then select **Brian S. Welcker** to view the name of this level.</span></span>

     <span data-ttu-id="19ed1-120">請注意，這個成員的層級名稱是 [Level 03 (層級 03)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-120">Notice that the level name for this member is **Level 03**.</span></span>

5.  <span data-ttu-id="19ed1-121">在方案總管中，按兩下 **Cubes** 資料夾的 **Analysis Services Tutorial.cube** ，來針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 開啟 Cube 設計師。</span><span class="sxs-lookup"><span data-stu-id="19ed1-121">In Solution Explorer, double-click **Analysis Services Tutorial.cube** in the **Cubes** folder to open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

6.  <span data-ttu-id="19ed1-122">按一下 **[瀏覽器]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="19ed1-122">Click the **Browser** tab.</span></span>

7.  <span data-ttu-id="19ed1-123">按一下 Excel 圖示，然後在出現啟用連接的提示時，按一下 [啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-123">Click the Excel icon, and then click **Enable** when prompted to enable connections.</span></span>

8.  <span data-ttu-id="19ed1-124">在樞紐分析表欄位清單中，展開 [Reseller Sales (轉售商銷售)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-124">In the PivotTable Field List, expand **Reseller Sales**.</span></span> <span data-ttu-id="19ed1-125">將 [Reseller Sales-Sales Amount (轉售商銷售 - 銷售量)]\*\*\*\* 拖曳至 [值] 區域。</span><span class="sxs-lookup"><span data-stu-id="19ed1-125">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

9. <span data-ttu-id="19ed1-126">在樞紐分析表欄位清單中，展開 [Employee (員工)]\*\*\*\*，然後將 [Employees (員工)]\*\*\*\* 階層拖曳至 [資料列]\*\*\*\* 區域。</span><span class="sxs-lookup"><span data-stu-id="19ed1-126">In the PivotTable Field List, expand **Employee**, and then drag the **Employees** hierarchy to the **Rows** area.</span></span>

     <span data-ttu-id="19ed1-127">[員工] 階層的所有成員都會加入至樞紐分析表報表的資料行 A 中。</span><span class="sxs-lookup"><span data-stu-id="19ed1-127">All the members of the Employees hierarchy are added to column A of the PivotTable report.</span></span>

     <span data-ttu-id="19ed1-128">下列影像顯示展開的 [員工] 階層。</span><span class="sxs-lookup"><span data-stu-id="19ed1-128">The following image shows the Employees hierarchy expanded.</span></span>

10. <span data-ttu-id="19ed1-129">![顯示員工階層的樞紐分析表](../../2014/tutorials/media/l4-employee-1.gif "顯示員工階層的樞紐分析表")</span><span class="sxs-lookup"><span data-stu-id="19ed1-129">![PivotTable showing Employees hierarchy](../../2014/tutorials/media/l4-employee-1.gif "PivotTable showing Employees hierarchy")</span></span>

     <span data-ttu-id="19ed1-130">請注意，每位主管在 [Level 03 (層級 03)] 中達到的銷售量也會顯示在 [Level 04 (層級 04)] 中。</span><span class="sxs-lookup"><span data-stu-id="19ed1-130">Notice that the sales made by each manager in Level 03 are also displayed in Level 04.</span></span> <span data-ttu-id="19ed1-131">這是因為每位主管也是另一位主管的員工。</span><span class="sxs-lookup"><span data-stu-id="19ed1-131">This is because each manager is also an employee of another manager.</span></span> <span data-ttu-id="19ed1-132">在下一項工作中，您會隱藏這些銷售量。</span><span class="sxs-lookup"><span data-stu-id="19ed1-132">In the next task, you will hide these sale amounts.</span></span>

## <a name="modifying-parent-attribute-properties-in-the-employee-dimension"></a><span data-ttu-id="19ed1-133">修改員工維度中父屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="19ed1-133">Modifying Parent Attribute Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="19ed1-134">針對 [Employee (員工)]\*\*\*\* 維度，切換至維度設計師。</span><span class="sxs-lookup"><span data-stu-id="19ed1-134">Switch to Dimension Designer for the **Employee** dimension.</span></span>

2.  <span data-ttu-id="19ed1-135">按一下 [維度結構]\*\*\*\* 索引標籤，然後在 [屬性]\*\*\*\* 窗格中選取 [Employees (員工)]\*\*\*\* 屬性階層。</span><span class="sxs-lookup"><span data-stu-id="19ed1-135">Click the **Dimension Structure** tab, and then select the **Employees** attribute hierarchy in the **Attributes** pane.</span></span>

     <span data-ttu-id="19ed1-136">請注意這個屬性的唯一圖示。</span><span class="sxs-lookup"><span data-stu-id="19ed1-136">Notice the unique icon for this attribute.</span></span> <span data-ttu-id="19ed1-137">這個圖示表示屬性為父子式階層中的父索引鍵。</span><span class="sxs-lookup"><span data-stu-id="19ed1-137">This icon signifies that the attribute is the parent key in a parent-child hierarchy.</span></span> <span data-ttu-id="19ed1-138">也請注意，在 [屬性] 視窗中，該屬性的 **Usage** 屬性是定義為 [父系]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-138">Notice also, in the Properties window, that the **Usage** property for the attribute is defined as **Parent**.</span></span> <span data-ttu-id="19ed1-139">當您設計維度，「維度精靈」就會設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="19ed1-139">This property was set by the Dimension Wizard when the dimension was designed.</span></span> <span data-ttu-id="19ed1-140">此精靈會自動偵測父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="19ed1-140">The wizard automatically detected the parent-child relationship.</span></span>

3.  <span data-ttu-id="19ed1-141">在 [屬性] 視窗中，按一下**NamingTemplate**屬性資料格中的省略符號按鈕 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="19ed1-141">In the Properties window, click the ellipsis button (**...**) in the **NamingTemplate** property cell.</span></span>

     <span data-ttu-id="19ed1-142">在 [層級命名範本]\*\*\*\* 對話方塊中，您會定義可決定父子式階層中層級名稱的層級命名範本，而使用者瀏覽 Cube 時便會看到這些名稱。</span><span class="sxs-lookup"><span data-stu-id="19ed1-142">In the **Level Naming Template** dialog box, you define the level naming template that determines the level names in the parent-child hierarchy that are displayed to users as they browse cubes.</span></span>

4.  <span data-ttu-id="19ed1-143">在第二個數據列中，于 [名稱] 資料行中 **\*** 輸入**Employee \* Level** ，然後按一下第三列。 **Name**</span><span class="sxs-lookup"><span data-stu-id="19ed1-143">In the second row, the **\*** row, type **Employee Level \*** in the **Name** column, and then click the third row.</span></span>

     <span data-ttu-id="19ed1-144">請注意，在 [結果]\*\*\*\* 之下，每一個層級的名稱都變成 "Employee Level"，後面接著循序遞增的數字。</span><span class="sxs-lookup"><span data-stu-id="19ed1-144">Notice under **Result** that each level will now be named "Employee Level" followed by a sequentially increasing number.</span></span>

     <span data-ttu-id="19ed1-145">下圖顯示 [層級命名範本]\*\*\*\* 對話方塊中的變更。</span><span class="sxs-lookup"><span data-stu-id="19ed1-145">The following image shows the changes in the **Level Naming Template** dialog box.</span></span>

     <span data-ttu-id="19ed1-146">![層級命名範本對話方塊](../../2014/tutorials/media/l4-namingtemplate.gif "層級命名範本對話方塊")</span><span class="sxs-lookup"><span data-stu-id="19ed1-146">![Level Naming Template dialog box](../../2014/tutorials/media/l4-namingtemplate.gif "Level Naming Template dialog box")</span></span>

5.  <span data-ttu-id="19ed1-147">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="19ed1-147">Click **OK**.</span></span>

6.  <span data-ttu-id="19ed1-148">在 **Employees** 屬性的屬性視窗中，選取 **MembersWithData** 屬性儲存格的 **NonLeafDataHidden** 來變更 **Employees** 屬性的這個值。</span><span class="sxs-lookup"><span data-stu-id="19ed1-148">In the Properties window for the **Employees** attribute, in the **MembersWithData** property cell, select **NonLeafDataHidden** to change this value for the **Employees** attribute.</span></span>

     <span data-ttu-id="19ed1-149">這會使父子式階層中與非分葉層級成員相關的資料隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="19ed1-149">This will cause data that is related to non-leaf level members in the parent-child hierarchy to be hidden.</span></span>

## <a name="browsing-the-employee-dimension-with-the-modified-attributes"></a><span data-ttu-id="19ed1-150">瀏覽含有已修改屬性的 Employee 維度</span><span class="sxs-lookup"><span data-stu-id="19ed1-150">Browsing the Employee Dimension with the Modified Attributes</span></span>

1.  <span data-ttu-id="19ed1-151">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-151">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="19ed1-152">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 Cube 設計師，然後按一下 [瀏覽器]\*\*\*\* 索引標籤之工具列上的 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-152">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the toolbar of the **Browser** tab.</span></span>

3.  <span data-ttu-id="19ed1-153">按一下 Excel 圖示，然後按一下 [啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="19ed1-153">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="19ed1-154">將 [Reseller Sales-Sales Amount (轉售商銷售 - 銷售量)]\*\*\*\* 拖曳至 [值] 區域。</span><span class="sxs-lookup"><span data-stu-id="19ed1-154">Drag **Reseller Sales-Sales Amount** to the Values area.</span></span>

5.  <span data-ttu-id="19ed1-155">將 [Employees (員工)]\*\*\*\* 階層拖曳至 [資料列標籤] 區域中。</span><span class="sxs-lookup"><span data-stu-id="19ed1-155">Drag the **Employees** hierarchy to the Row Labels area.</span></span>

     <span data-ttu-id="19ed1-156">下圖顯示您對 [Employees] 階層所做的變更。</span><span class="sxs-lookup"><span data-stu-id="19ed1-156">The following image shows the changes that you made to the Employees hierarchy.</span></span> <span data-ttu-id="19ed1-157">請注意，Stephen Y. Jiang 不再顯示為自己的員工。</span><span class="sxs-lookup"><span data-stu-id="19ed1-157">Notice that Stephen Y. Jiang no longer appears as an employee of himself.</span></span>

     <span data-ttu-id="19ed1-158">![已修改的員工階層](../../2014/tutorials/media/l4-employee-2.png "已修改的員工階層")</span><span class="sxs-lookup"><span data-stu-id="19ed1-158">![Modified Employees hierarchy](../../2014/tutorials/media/l4-employee-2.png "Modified Employees hierarchy")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="19ed1-159">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="19ed1-159">Next Task in Lesson</span></span>
 [<span data-ttu-id="19ed1-160">自動分組屬性成員</span><span class="sxs-lookup"><span data-stu-id="19ed1-160">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)

## <a name="see-also"></a><span data-ttu-id="19ed1-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19ed1-161">See Also</span></span>
 <span data-ttu-id="19ed1-162">父子式階層中的父子[式](multidimensional-models/parent-child-dimension.md)階層[屬性](multidimensional-models/parent-child-dimension-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="19ed1-162">[Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md)</span></span>


