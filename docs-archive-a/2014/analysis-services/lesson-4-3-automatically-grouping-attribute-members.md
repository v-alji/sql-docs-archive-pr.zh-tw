---
title: 自動群組屬性成員 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9fb2cda3-a122-4a4c-82e0-3454865eef04
author: minewiskan
ms.author: owend
ms.openlocfilehash: 820231263362a92584a15556e999d69f286349b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710013"
---
# <a name="automatically-grouping-attribute-members"></a><span data-ttu-id="03087-102">自動分組屬性成員</span><span class="sxs-lookup"><span data-stu-id="03087-102">Automatically Grouping Attribute Members</span></span>
  <span data-ttu-id="03087-103">當您瀏覽 Cube 時，通常會按另一個屬性階層的成員建立一個屬性階層成員的維度。</span><span class="sxs-lookup"><span data-stu-id="03087-103">When you browse a cube, you typically dimension the members of one attribute hierarchy by the members of another attribute hierarchy.</span></span> <span data-ttu-id="03087-104">例如，您可以按縣 (市)、按購買的產品或按性別將客戶銷售加以分組。</span><span class="sxs-lookup"><span data-stu-id="03087-104">For example, you might group customer sales by city, by product purchased, or by gender.</span></span> <span data-ttu-id="03087-105">不過，若使用特定類型的屬性， [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 根據屬性階層中成員的散發，自動建立屬性成員的群組會很有説明。</span><span class="sxs-lookup"><span data-stu-id="03087-105">However, with certain types of attributes, it is useful to have [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] automatically create groupings of attribute members based on the distribution of the members within an attribute hierarchy.</span></span> <span data-ttu-id="03087-106">例如，您可以讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 為客戶建立年收入值的群組。</span><span class="sxs-lookup"><span data-stu-id="03087-106">For example, you can have [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] create groups of yearly income values for customers.</span></span> <span data-ttu-id="03087-107">如此一來，瀏覽這個屬性階層的使用者會看到群組的名稱和值而不是成員本身。</span><span class="sxs-lookup"><span data-stu-id="03087-107">When you do this, users who browse the attribute hierarchy will see the names and values of the groups instead of the members themselves.</span></span> <span data-ttu-id="03087-108">這樣可限制使用者看到的層級數，對於分析更有幫助。</span><span class="sxs-lookup"><span data-stu-id="03087-108">This limits the number of levels that are presented to users, which can be more useful for analysis.</span></span>

 <span data-ttu-id="03087-109">[DiscretizationMethod]\*\*\*\* 屬性會決定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 是否建立分組，並決定執行的分組類型。</span><span class="sxs-lookup"><span data-stu-id="03087-109">The **DiscretizationMethod** property determines whether [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groupings, and determines the type of grouping that is performed.</span></span> <span data-ttu-id="03087-110">依預設， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 不會執行任何分組。</span><span class="sxs-lookup"><span data-stu-id="03087-110">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not perform any groupings.</span></span> <span data-ttu-id="03087-111">當您啟用自動分組時，可以讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 依據屬性的結構自動決定最佳群組方法，或是從下列清單中選擇其中一種群組演算法來指定群組方法：</span><span class="sxs-lookup"><span data-stu-id="03087-111">When you enable automatic groupings, you can allow [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to automatically determine the best grouping method based on the structure of the attribute, or you can choose one of the grouping algorithms in the following list to specify the grouping method:</span></span>

 <span data-ttu-id="03087-112">**EqualAreas** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]建立群組範圍，使維度成員的總擴展平均分散于群組中。</span><span class="sxs-lookup"><span data-stu-id="03087-112">**EqualAreas** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates group ranges so that the total population of dimension members is distributed equally across the groups.</span></span>

 <span data-ttu-id="03087-113">**群集** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]藉由在輸入值上執行一維叢集來建立群組，方法是使用具有高斯分佈的 K 表示群集方法。</span><span class="sxs-lookup"><span data-stu-id="03087-113">**Clusters** [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates groups by performing single-dimensional clustering on the input values by using the K-Means clustering method with Gaussian distributions.</span></span> <span data-ttu-id="03087-114">這個選項只對數值資料行有效。</span><span class="sxs-lookup"><span data-stu-id="03087-114">This option is valid only for numeric columns.</span></span>

 <span data-ttu-id="03087-115">在指定群組方法之後，您必須使用 [DiscretizationBucketCount]\*\*\*\* 屬性來指定群組數目。</span><span class="sxs-lookup"><span data-stu-id="03087-115">After you specify a grouping method, you must specify the number of groups, by using the **DiscretizationBucketCount** property.</span></span> <span data-ttu-id="03087-116">如需詳細資訊，請參閱 [群組屬性成員 &#40;分隔&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)</span><span class="sxs-lookup"><span data-stu-id="03087-116">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)</span></span>

 <span data-ttu-id="03087-117">在這個主題的工作中，您將針對下列各項啟用不同群組類型：[客戶]\*\*\*\* 維度中的年收入值、[員工(多數)]\*\*\*\* 維度中的員工病假時數以及 [員工(多數)]\*\*\*\* 維度中的員工休假時數。</span><span class="sxs-lookup"><span data-stu-id="03087-117">In the tasks in this topic, you will enable different types of groupings for the following: the yearly income values in the **Customer** dimension; the number of employee sick leave hours in the **Employees** dimension; and the number of employee vacation hours in the **Employees** dimension.</span></span> <span data-ttu-id="03087-118">然後您會處理及瀏覽 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 來檢視成員群組的效果。</span><span class="sxs-lookup"><span data-stu-id="03087-118">You will then process and browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube to view the effect of the member groups.</span></span> <span data-ttu-id="03087-119">最後，您會修改成員群組屬性來查看這個變更對群組類型的影響。</span><span class="sxs-lookup"><span data-stu-id="03087-119">Finally, you will modify the member group properties to see the effect of the change in grouping type.</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-customer-dimension"></a><span data-ttu-id="03087-120">將 [客戶] 維度中的屬性階層成員分組</span><span class="sxs-lookup"><span data-stu-id="03087-120">Grouping Attribute Hierarchy Members in the Customer Dimension</span></span>

1.  <span data-ttu-id="03087-121">在方案總管中，按兩下 [維度]\*\*\*\* 資料夾中的 [客戶]\*\*\*\*，來針對 [客戶] 維度開啟 [維度設計師]。</span><span class="sxs-lookup"><span data-stu-id="03087-121">In Solution Explorer, double-click **Customer** in the **Dimensions** folder to open Dimension Designer for the Customer dimension.</span></span>

2.  <span data-ttu-id="03087-122">在 [資料來源檢視]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [客戶]\*\*\*\* 資料表，然後按一下 [瀏覽資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-122">In the **Data Source View** pane, right-click the **Customer** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="03087-123">請注意 **YearlyIncome** 資料行的值範圍。</span><span class="sxs-lookup"><span data-stu-id="03087-123">Notice the range of values for the **YearlyIncome** column.</span></span> <span data-ttu-id="03087-124">除非您啟用成員群組，否則這些值會變成 [年收入]\*\*\*\* 屬性階層的成員。</span><span class="sxs-lookup"><span data-stu-id="03087-124">These values become the members of the **Yearly Income** attribute hierarchy, unless you enable member grouping.</span></span>

3.  <span data-ttu-id="03087-125">關閉 [瀏覽 Customer 資料表]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="03087-125">Close the **Explore Customer Table** tab.</span></span>

4.  <span data-ttu-id="03087-126">在 [屬性]\*\*\*\* 窗格中，選取 [年收入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-126">In the **Attributes** pane, select **Yearly Income**.</span></span>

5.  <span data-ttu-id="03087-127">在 [屬性視窗中，將 [ **DiscretizationMethod** ] 屬性的值變更為 [**自動**]，並將 [ **DiscretizationBucketCount** ] 屬性的值變更為 `5` 。</span><span class="sxs-lookup"><span data-stu-id="03087-127">In the Properties window, change the value for the **DiscretizationMethod** property to **Automatic** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

     <span data-ttu-id="03087-128">下圖顯示 [年收入]\*\*\*\* 的已修改屬性。</span><span class="sxs-lookup"><span data-stu-id="03087-128">The following image shows the modified properties for **Yearly Income**.</span></span>

     <span data-ttu-id="03087-129">![年收益的已修改屬性](../../2014/tutorials/media/l4-discretizationmethod-1.gif "年收益的已修改屬性")</span><span class="sxs-lookup"><span data-stu-id="03087-129">![Modified properties for Yearly Income](../../2014/tutorials/media/l4-discretizationmethod-1.gif "Modified properties for Yearly Income")</span></span>

## <a name="grouping-attribute-hierarchy-members-in-the-employee-dimension"></a><span data-ttu-id="03087-130">將 [員工] 維度中的屬性階層成員分組</span><span class="sxs-lookup"><span data-stu-id="03087-130">Grouping Attribute Hierarchy Members in the Employee Dimension</span></span>

1.  <span data-ttu-id="03087-131">針對 [員工] 維度，切換至維度設計師。</span><span class="sxs-lookup"><span data-stu-id="03087-131">Switch to Dimension Designer for the Employee dimension.</span></span>

2.  <span data-ttu-id="03087-132">在 [資料來源檢視]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [員工]\*\*\*\* 資料表，然後按一下 [瀏覽資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-132">In the **Data Source View** pane, right-click the **Employee** table, and then click **Explore Data**.</span></span>

     <span data-ttu-id="03087-133">請注意 **SickLeaveHours** 資料行和 **VacationHours** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="03087-133">Notice the values for the **SickLeaveHours** column and the **VacationHours** column.</span></span>

3.  <span data-ttu-id="03087-134">關閉 [瀏覽 Employee 資料表]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="03087-134">Close the **Explore Employee Table** tab.</span></span>

4.  <span data-ttu-id="03087-135">在 [屬性]\*\*\*\* 窗格中，選取 [病假時數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-135">In the **Attributes** pane, select **Sick Leave Hours**.</span></span>

5.  <span data-ttu-id="03087-136">在 [屬性視窗中，將 [ **DiscretizationMethod** ] 屬性的值變更為 [叢集] **，並將**[ **DiscretizationBucketCount** ] 屬性的值變更為 `5` 。</span><span class="sxs-lookup"><span data-stu-id="03087-136">In the Properties window, change the value for the **DiscretizationMethod** property to **Clusters** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

6.  <span data-ttu-id="03087-137">在 [屬性]\*\*\*\* 窗格中，選取 [假期時數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-137">In the **Attributes** pane, select **Vacation Hours**.</span></span>

7.  <span data-ttu-id="03087-138">在 [屬性視窗中，將 [ **DiscretizationMethod** ] 屬性的值變更為 [**等於] 區域**，並將 [ **DiscretizationBucketCount** ] 屬性的值變更為 `5` 。</span><span class="sxs-lookup"><span data-stu-id="03087-138">In the Properties window, change the value for the **DiscretizationMethod** property to **Equal Areas** and change the value for the **DiscretizationBucketCount** property to `5`.</span></span>

## <a name="browsing-the-modified-attribute-hierarchies"></a><span data-ttu-id="03087-139">瀏覽已修改的屬性階層</span><span class="sxs-lookup"><span data-stu-id="03087-139">Browsing the Modified Attribute Hierarchies</span></span>

1.  <span data-ttu-id="03087-140">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-140">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="03087-141">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師]，然後按一下 [瀏覽器]\*\*\*\* 索引標籤上的 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-141">When deployment has successfully completed, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect** on the **Browser** tab.</span></span>

3.  <span data-ttu-id="03087-142">按一下 Excel 圖示，然後按一下 [啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-142">Click the Excel icon, and then click **Enable**.</span></span>

4.  <span data-ttu-id="03087-143">將 [網際網路銷售 - 銷售量]\*\*\*\* 量值拖曳至樞紐分析表欄位清單的 [值] 區域中。</span><span class="sxs-lookup"><span data-stu-id="03087-143">Drag the **Internet Sales-Sales Amount** measure to the Values area of the PivotTable Field List.</span></span>

5.  <span data-ttu-id="03087-144">在此欄位清單中，展開 [產品]\*\*\*\* 維度，然後將 [產品型號線]\*\*\*\* 使用者階層拖曳到欄位清單的 [資料列標籤]\*\*\*\* 區域。</span><span class="sxs-lookup"><span data-stu-id="03087-144">In the field list, expand the **Product** dimension, and then drag the **Product Model Lines** user hierarchy to the **Row Labels** area of the field list.</span></span>

6.  <span data-ttu-id="03087-145">在欄位清單中，依序展開 [客戶]\*\*\*\* 維度和 [人口統計]\*\*\*\* 顯示資料夾，然後將 [年收入]\*\*\*\* 屬性階層拖曳到 [資料行標籤]\*\*\*\* 區域。</span><span class="sxs-lookup"><span data-stu-id="03087-145">Expand the **Customer** dimension in the field list, expand the **Demographic** display folder, and then drag the **Yearly Income** attribute hierarchy to the **Column Labels** area.</span></span>

     <span data-ttu-id="03087-146">[年收入]\*\*\*\* 屬性階層的成員現在分成六個值區，包括對於年收入不詳的客戶之銷售量的值區。</span><span class="sxs-lookup"><span data-stu-id="03087-146">The members of the **Yearly Income** attribute hierarchy are now grouped into six buckets, including a bucket for sales to customers whose yearly income is unknown.</span></span> <span data-ttu-id="03087-147">但是，並非所有值區都會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="03087-147">Not all buckets are displayed.</span></span>

7.  <span data-ttu-id="03087-148">從資料行區域中移除 [年收入]\*\*\*\* 屬性階層，並移除 [值]\*\*\*\* 區域中的 [網際網路銷售 - 銷售量]\*\*\*\* 量值。</span><span class="sxs-lookup"><span data-stu-id="03087-148">Remove the **Yearly Income** attribute hierarchy from the columns area and remove the **Internet Sales-Sales Amount** measure from the **Values** area.</span></span>

8.  <span data-ttu-id="03087-149">將 [轉售商銷售 - 銷售量]\*\*\*\* 量值新增至資料區域。</span><span class="sxs-lookup"><span data-stu-id="03087-149">Add the **Reseller Sales-Sales Amount** measure to the data area.</span></span>

9. <span data-ttu-id="03087-150">在此欄位清單中，依序展開 [員工]\*\*\*\* 維度和 [組織]\*\*\*\*，然後將 [病假時數]\*\*\*\* 拖曳至 [資料行標籤]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-150">In the field list, expand the **Employee** dimension, expand **Organization**, then drag **Sick Leave Hours** to **Column Labels**.</span></span>

     <span data-ttu-id="03087-151">請注意，所有銷售是由兩個群組的其中之一的員工所完成的。</span><span class="sxs-lookup"><span data-stu-id="03087-151">Notice that all sales are made by employees within one of two groups.</span></span> <span data-ttu-id="03087-152">另請注意，病假時數在 32 - 42 之間的員工比病假時數在 20 - 31 之間的員工有更多銷售。</span><span class="sxs-lookup"><span data-stu-id="03087-152">Notice also that the employees with 32 - 42 sick leave hours made significantly more sales than employees with 20 - 31 sick leave hours.</span></span>

     <span data-ttu-id="03087-153">下圖顯示按員工病假時數建立維度的銷售。</span><span class="sxs-lookup"><span data-stu-id="03087-153">The following image shows sales dimensioned by employee sick leave hours.</span></span>

     <span data-ttu-id="03087-154">![依員工病假時數建立維度的銷售額](../../2014/tutorials/media/l4-discretizationmethod-2.gif "依員工病假時數建立維度的銷售額")</span><span class="sxs-lookup"><span data-stu-id="03087-154">![Sales dimensioned by employee sick leave hours](../../2014/tutorials/media/l4-discretizationmethod-2.gif "Sales dimensioned by employee sick leave hours")</span></span>

10. <span data-ttu-id="03087-155">從 [資料]\*\*\*\* 窗格的資料行區域中移除 [病假時數]\*\*\*\* 屬性階層。</span><span class="sxs-lookup"><span data-stu-id="03087-155">Remove the **Sick Leave Hours** attribute hierarchy from the column area of the **Data** pane.</span></span>

11. <span data-ttu-id="03087-156">將 [假期時數]\*\*\*\* 新增至 [資料]\*\*\*\* 窗格的資料行區域中。</span><span class="sxs-lookup"><span data-stu-id="03087-156">Add **Vacation Hours** to the column area of the **Data** pane.</span></span>

     <span data-ttu-id="03087-157">請注意，依據同等區域群組方法，會出現兩個群組。</span><span class="sxs-lookup"><span data-stu-id="03087-157">Notice that two groups appear, based on the equal areas grouping method.</span></span> <span data-ttu-id="03087-158">其他 3 個群組會隱藏起來，因為它們不包含資料值。</span><span class="sxs-lookup"><span data-stu-id="03087-158">Three other groups are hidden because they contain no data values.</span></span>

## <a name="modifying-grouping-properties-and-reviewing-the-effect-of-the-changes"></a><span data-ttu-id="03087-159">修改群組屬性及檢閱變更的效果</span><span class="sxs-lookup"><span data-stu-id="03087-159">Modifying Grouping Properties and Reviewing the Effect of the Changes</span></span>

1.  <span data-ttu-id="03087-160">針對 [員工]\*\*\*\* 維度切換到 [維度設計師]，然後選取 [屬性]\*\*\*\* 窗格中的 [假期時數]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-160">Switch to Dimension Designer for the **Employee** dimension, and then select **Vacation Hours** in the **Attributes** pane.</span></span>

2.  <span data-ttu-id="03087-161">在 [屬性] 視窗中，將 [DiscretizationBucketCount]\*\*\*\* 屬性的值變更為 [10]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-161">In the Properties window, change the value of the **DiscretizationBucketCount** property to **10.**</span></span>

3.  <span data-ttu-id="03087-162">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="03087-162">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>

4.  <span data-ttu-id="03087-163">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 Cube 設計師。</span><span class="sxs-lookup"><span data-stu-id="03087-163">When deployment has successfully completed, switch back to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>

5.  <span data-ttu-id="03087-164">選取 [瀏覽器]\*\*\*\* 索引標籤上的 [重新連接]\*\*\*\*、按一下 Excel 圖示，然後重新建構樞紐分析表，讓您可以檢視群組方法變更之後的效果：</span><span class="sxs-lookup"><span data-stu-id="03087-164">Click **Reconnect** on the **Browser** tab, click the Excel icon, and then reconstruct the PivotTable so that you can view the effect of the change to the grouping method:</span></span>

    1.  <span data-ttu-id="03087-165">將 [轉售商銷售 - 銷售量] 拖曳至 [值]</span><span class="sxs-lookup"><span data-stu-id="03087-165">Drag Reseller Sales-Sales Amount to Values</span></span>

    2.  <span data-ttu-id="03087-166">將 [假期時數] (在 [員工組織] 資料夾中) 拖曳至 [資料行]</span><span class="sxs-lookup"><span data-stu-id="03087-166">Drag Vacation Hours (in the Employees Organization folder) to Columns</span></span>

    3.  <span data-ttu-id="03087-167">將 [產品型號線] 拖曳至 [資料列]</span><span class="sxs-lookup"><span data-stu-id="03087-167">Drag Product Model Lines to Rows</span></span>

     <span data-ttu-id="03087-168">請注意，現在 [假期時數]\*\*\*\* 屬性有 3 個成員群組有產品的銷售值。</span><span class="sxs-lookup"><span data-stu-id="03087-168">Notice that there are now three groups of members of the **Vacation Hours** attribute that have sales values for products.</span></span> <span data-ttu-id="03087-169">(其他七個群組包含沒有銷售資料的成員)。</span><span class="sxs-lookup"><span data-stu-id="03087-169">(The other seven groups contain members with no sales data.)</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="03087-170">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="03087-170">Next Task in Lesson</span></span>
 [<span data-ttu-id="03087-171">隱藏及停用屬性階層</span><span class="sxs-lookup"><span data-stu-id="03087-171">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)

## <a name="see-also"></a><span data-ttu-id="03087-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03087-172">See Also</span></span>
 [<span data-ttu-id="03087-173">群組屬性成員 &#40;分隔&#41;</span><span class="sxs-lookup"><span data-stu-id="03087-173">Group Attribute Members &#40;Discretization&#41;</span></span>](multidimensional-models/attribute-properties-group-attribute-members.md)


