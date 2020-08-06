---
title: 定義和使用「鑽取動作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 3765f865-2b93-44be-b290-28e3815d5ecb
author: minewiskan
ms.author: owend
ms.openlocfilehash: ea19a9721d87936bc88b5401c71ee550a47bc1ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698725"
---
# <a name="defining-and-using-a-drillthrough-action"></a><span data-ttu-id="3ff5b-102">定義和使用鑽研動作</span><span class="sxs-lookup"><span data-stu-id="3ff5b-102">Defining and Using a Drillthrough Action</span></span>
  <span data-ttu-id="3ff5b-103">依據事實維度測量事實資料的維度，但卻未正確篩選查詢傳回的資料，可能會降低查詢效能。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-103">Dimensioning fact data by a fact dimension without correctly filtering the data that the query returns can cause slow query performance.</span></span> <span data-ttu-id="3ff5b-104">為了避免這種情況，您可以定義鑽研動作，以便限制傳回的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-104">To avoid this, you can define a drillthrough action that restricts the total number of rows that are returned.</span></span> <span data-ttu-id="3ff5b-105">這樣做將會大幅改善查詢效能。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-105">This will significantly improve query performance.</span></span>  
  
 <span data-ttu-id="3ff5b-106">在這個主題的工作中，您要定義鑽研動作，透過網際網路將銷售訂購的詳細資訊傳回給客戶。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-106">In the tasks in this topic, you define a drillthrough action to return order detail information for sales to customers over the Internet.</span></span>  
  
## <a name="defining-the-drillthrough-action-properties"></a><span data-ttu-id="3ff5b-107">定義鑽研動作屬性</span><span class="sxs-lookup"><span data-stu-id="3ff5b-107">Defining the Drillthrough Action Properties</span></span>  
  
1.  <span data-ttu-id="3ff5b-108">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的 [Cube 設計師] 中，按一下 [動作]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-108">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Actions** tab.</span></span>  
  
     <span data-ttu-id="3ff5b-109">[動作]\*\*\*\* 索引標籤含有幾個窗格。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-109">The **Actions** tab includes several panes.</span></span> <span data-ttu-id="3ff5b-110">該索引標籤的左側具有 [動作組合管理]\*\*\*\* 窗格和 [計算工具]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-110">On the left side of the tab are the **Action Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="3ff5b-111">這兩個窗格右邊的窗格是 [顯示]\*\*\*\* 窗格，其中包含在 [動作組合管理]\*\*\*\* 窗格中選取之動作的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-111">The pane to the right of these two panes is the **Display** pane, which contains the details of the action that is selected in the **Action Organizer** pane.</span></span>  
  
     <span data-ttu-id="3ff5b-112">下圖顯示 [Cube 設計師] 的 [動作]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-112">The following image shows the **Actions** tab of Cube Designer.</span></span>  
  
     <span data-ttu-id="3ff5b-113">![Cube 設計師的動作索引標籤](../../2014/tutorials/media/l8-action1.gif "Cube 設計師的動作索引標籤")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-113">![Actions tab of Cube Designer](../../2014/tutorials/media/l8-action1.gif "Actions tab of Cube Designer")</span></span>  
  
2.  <span data-ttu-id="3ff5b-114">在 [動作]\*\*\*\* 索引標籤的工具列上，按一下 [新增鑽研動作]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-114">On the toolbar of the **Actions** tab, click the **New Drillthrough Action** button.</span></span>  
  
     <span data-ttu-id="3ff5b-115">此時，[顯示] 窗格中會出現一個空白的動作範本。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-115">A blank action template appears in the display pane.</span></span>  
  
     <span data-ttu-id="3ff5b-116">![顯示窗格中的空白動作範本](../../2014/tutorials/media/l8-action2.gif "顯示窗格中的空白動作範本")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-116">![Blank Action template in the display pane](../../2014/tutorials/media/l8-action2.gif "Blank Action template in the display pane")</span></span>  
  
3.  <span data-ttu-id="3ff5b-117">在 [**名稱**] 方塊中，將此動作的名稱變更為 `Internet Sales Details Drillthrough Action` 。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-117">In the **Name** box, change the name of this action to `Internet Sales Details Drillthrough Action`.</span></span>  
  
4.  <span data-ttu-id="3ff5b-118">在 [量值群組成員]\*\*\*\* 清單中，選取 [網際網路銷售]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-118">In the **Measure group members** list, select **Internet Sales**.</span></span>  
  
5.  <span data-ttu-id="3ff5b-119">在 [鑽研資料行]\*\*\*\* 方塊中，從 [維度]\*\*\*\* 清單中選取 [網際網路銷售訂單的詳細資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-119">In the **Drillthrough Columns** box, select **Internet Sales Order Details** in the **Dimensions** list.</span></span>  
  
6.  <span data-ttu-id="3ff5b-120">在 [傳回資料行]\*\*\*\* 清單中，選取 [項目描述]\*\*\*\* 和 [訂單號碼]\*\*\*\* 核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-120">In the **Return Columns** list, select the **Item Description** and the **Order Number** check boxes, and then click **OK**.</span></span> <span data-ttu-id="3ff5b-121">下圖所示範的是，程序此時應該顯示的動作範本。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-121">The following image shows the Action template as it should appear at this point in this procedure.</span></span>  
  
     <span data-ttu-id="3ff5b-122">![鑽研資料行方塊](../../2014/tutorials/media/l8-action3.gif "鑽研資料行方塊")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-122">![Drillthrough Columns box](../../2014/tutorials/media/l8-action3.gif "Drillthrough Columns box")</span></span>  
  
7.  <span data-ttu-id="3ff5b-123">展開 [其他屬性]\*\*\*\* 方塊，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-123">Expand the **Additional Properties** box, as shown in the following image.</span></span>  
  
     <span data-ttu-id="3ff5b-124">![其他屬性方塊](../../2014/tutorials/media/l8-action4.gif "其他屬性方塊")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-124">![Additional Properties box](../../2014/tutorials/media/l8-action4.gif "Additional Properties box")</span></span>  
  
8.  <span data-ttu-id="3ff5b-125">在 [**最大資料列數**] 方塊中，輸入 `10` 。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-125">In the **Maximum Rows** box, type `10`.</span></span>  
  
9. <span data-ttu-id="3ff5b-126">在 [**標題**] 方塊中，輸入 `Drillthrough to Order Details...` 。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-126">In the **Caption** box, type `Drillthrough to Order Details...`.</span></span>  
  
     <span data-ttu-id="3ff5b-127">這些設定會限制傳回的資料列數，指定在用戶端應用程式功能表中所顯示的標題。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-127">These settings limit the number of rows returned and specify the caption that appears in the client application menu.</span></span> <span data-ttu-id="3ff5b-128">下圖顯示 [其他屬性]\*\*\*\* 方塊中的這些設定。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-128">The following image shows these settings in the **AdditionalProperties** box.</span></span>  
  
     <span data-ttu-id="3ff5b-129">![其他屬性方塊](../../2014/tutorials/media/l8-action5.gif "其他屬性方塊")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-129">![Additional Properties box](../../2014/tutorials/media/l8-action5.gif "Additional Properties box")</span></span>  
  
## <a name="using-the-drillthrough-action"></a><span data-ttu-id="3ff5b-130">使用鑽研動作</span><span class="sxs-lookup"><span data-stu-id="3ff5b-130">Using the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="3ff5b-131">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-131">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="3ff5b-132">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，按一下 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-132">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="3ff5b-133">啟動 Excel。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-133">Start Excel.</span></span>  
  
4.  <span data-ttu-id="3ff5b-134">將 [網際網路銷售 - 銷售量]\*\*\*\* 量值加入 [值] 區域。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-134">Add the **Internet Sales-Sales Amount** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="3ff5b-135">將 [客戶地理位置]\*\*\*\* 使用者定義階層從 [客戶]\*\*\*\* 維度的 [位置\*\*\*\* 資料夾加入 [報表篩選]\*\*\*\* 區域中。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-135">Add the **Customer Geography** user-defined hierarchy from the **Location** folder in the **Customer** dimension to the **Report Filter** area.</span></span>  
  
6.  <span data-ttu-id="3ff5b-136">在樞紐分析表的 [客戶地理位置]\*\*\*\* 中，加入選取單一客戶的篩選。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-136">On the PivotTable, in **Customer Geography**, add a filter that selects a single customer.</span></span> <span data-ttu-id="3ff5b-137">依序展開 [所有客戶]\*\*\*\*、[澳大利亞]\*\*\*\*、[昆士蘭]\*\*\*\*、[布里斯本]\*\*\*\*、[4000]\*\*\*\*，選取 [Adam Powell]\*\*\*\* 的核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-137">Expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, select the check box for **Adam Powell**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="3ff5b-138">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 到 Adam Powell 的產品總銷售會顯示在資料區域中。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-138">The total sales of products by [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] to Adam Powell are displayed in the data area.</span></span>  
  
7.  <span data-ttu-id="3ff5b-139">以滑鼠右鍵按一下銷售量，指向 [其他動作]\*\*\*\*，然後按一下 [鑽研至訂單詳細資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-139">Right-click on the sales amount, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="3ff5b-140">運送給 Adam Powell 的訂單詳細資料會顯示在 [資料範例檢視器]\*\*\*\* 中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-140">The details of the orders that were shipped to Adam Powell are displayed in the **Data Sample Viewer**, as shown in the following image.</span></span> <span data-ttu-id="3ff5b-141">不過，額外附加的詳細資料，有時候是很有用的，例如，訂購日期、截止日期和出貨日期。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-141">However, some additional details would also be useful, such as the order date, due date, and ship date.</span></span> <span data-ttu-id="3ff5b-142">在下一個程序中，您要加入這些額外的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-142">In the next procedure, you will add these additional details.</span></span>  
  
     <span data-ttu-id="3ff5b-143">![運送給 Adam Powell 的訂購貨品](../../2014/tutorials/media/l8-action6.gif "運送給 Adam Powell 的訂購貨品")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-143">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action6.gif "Orders shipped to Adam Powell")</span></span>  
  
8.  <span data-ttu-id="3ff5b-144">關閉 Excel/</span><span class="sxs-lookup"><span data-stu-id="3ff5b-144">Close Excel/</span></span>  
  
## <a name="modifying-the-drillthrough-action"></a><span data-ttu-id="3ff5b-145">修改鑽研動作</span><span class="sxs-lookup"><span data-stu-id="3ff5b-145">Modifying the Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="3ff5b-146">針對 [網際網路銷售訂單的詳細資料]\*\*\*\* 維度開啟 [維度設計師]。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-146">Open Dimension Designer for the **Internet Sales Order Details** dimension.</span></span>  
  
     <span data-ttu-id="3ff5b-147">請注意，這個維度只定義了三個屬性。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-147">Notice that only three attributes have been defined for this dimension.</span></span>  
  
2.  <span data-ttu-id="3ff5b-148">在 [資料來源檢視]\*\*\*\* 窗格中，以滑鼠右鍵按一下其中一個開放區域，然後按一下 [顯示所有資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-148">In the **Data Source View** pane, right-click an open area, and then click **Show All Tables**.</span></span>  
  
3.  <span data-ttu-id="3ff5b-149">在 [格式]\*\*\*\* 功能表上，指向 [自動版面配置]\*\*\*\*，然後按一下 [圖表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-149">On the **Format** menu, point to **Autolayout** and then click **Diagram**.</span></span>  
  
4.  <span data-ttu-id="3ff5b-150">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的開放區域，藉以找出 **InternetSales (dbo.FactInternetSales)** 資料表。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-150">Locate the **InternetSales (dbo.FactInternetSales)** table by right-clicking in an open area of the **Data Source View** pane.</span></span> <span data-ttu-id="3ff5b-151">然後，依序按一下 [尋找資料表]\*\*\*\*、[InternetSales]\*\*\*\* 和 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-151">Then click **Find Table,** click **InternetSales,** and click **OK**.</span></span>  
  
5.  <span data-ttu-id="3ff5b-152">根據下列資料行，建立新的屬性：</span><span class="sxs-lookup"><span data-stu-id="3ff5b-152">Create new attributes based on the following columns:</span></span>  
  
    -   <span data-ttu-id="3ff5b-153">OrderDateKey</span><span class="sxs-lookup"><span data-stu-id="3ff5b-153">OrderDateKey</span></span>  
  
    -   <span data-ttu-id="3ff5b-154">DueDateKey</span><span class="sxs-lookup"><span data-stu-id="3ff5b-154">DueDateKey</span></span>  
  
    -   <span data-ttu-id="3ff5b-155">ShipDateKey</span><span class="sxs-lookup"><span data-stu-id="3ff5b-155">ShipDateKey</span></span>  
  
6.  <span data-ttu-id="3ff5b-156">將 [**訂單日期**] 索引鍵屬性的 [**名稱**] 屬性變更為 `Order Date` ，然後按一下 [**名稱資料行**] 屬性的 [流覽] 按鈕，然後在 [**名稱資料行**] 對話方塊中，選取 [日期] 做為來源資料表，然後選取 [SimpleDate] 做為源**資料**行。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-156">Change the **Name** property for the **Order Date Key** attribute to `Order Date` Then, click the browse button for the **Name Column** property, and in the **Name Column** dialog box, select **Date** as the source table and select SimpleDate as the source column.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="3ff5b-157">將 [**到期日期**] 索引鍵屬性的 [**名稱**] 屬性變更為 `Due Date` ，然後使用與 [**訂單日期索引鍵**] 屬性相同的方法，將此屬性的 [名稱] 資料**行**屬性變更為 [ \*\*SimpleDate] (WChar) \*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-157">Change the **Name** property for the **Due Date Key** attribute to `Due Date`, and then, by using the same method as the **Order Date Key** attribute, change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
8.  <span data-ttu-id="3ff5b-158">將 [出**貨日期索引鍵**] 屬性的 [**名稱**] 屬性變更為 `Ship Date` ，然後將這個屬性的 [**名稱資料行**] 屬性變更為\*\*SimpleDate (WChar) \*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-158">Change the **Name** property for the **Ship Date Key** attribute to `Ship Date`, and then change the **Name Column** property for this attribute to **Date.SimpleDate (WChar)**.</span></span>  
  
9. <span data-ttu-id="3ff5b-159">針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師] 的 [動作]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-159">Switch to the **Actions** tab of Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
10. <span data-ttu-id="3ff5b-160">在 [鑽研資料行]\*\*\*\* 方塊中，選取核取方塊，以便下列資料行加入 [傳回資料行]\*\*\*\* 清單，然後按一下 [確定]\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="3ff5b-160">In the **Drillthrough Columns** box, select the check boxes to add the following columns to the **Return Columns** list, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="3ff5b-161">Order Date</span><span class="sxs-lookup"><span data-stu-id="3ff5b-161">Order Date</span></span>  
  
    -   <span data-ttu-id="3ff5b-162">Due Date</span><span class="sxs-lookup"><span data-stu-id="3ff5b-162">Due Date</span></span>  
  
    -   <span data-ttu-id="3ff5b-163">Ship Date</span><span class="sxs-lookup"><span data-stu-id="3ff5b-163">Ship Date</span></span>  
  
     <span data-ttu-id="3ff5b-164">下圖所顯示的是這些選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-164">The following image shows these columns selected.</span></span>  
  
     <span data-ttu-id="3ff5b-165">![鑽研資料行方塊](../../2014/tutorials/media/l8-action7.gif "鑽研資料行方塊")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-165">![Drillthrough Columns box](../../2014/tutorials/media/l8-action7.gif "Drillthrough Columns box")</span></span>  
  
## <a name="reviewing-the-modified-drillthrough-action"></a><span data-ttu-id="3ff5b-166">檢閱修改後的鑽研動作</span><span class="sxs-lookup"><span data-stu-id="3ff5b-166">Reviewing the Modified Drillthrough Action</span></span>  
  
1.  <span data-ttu-id="3ff5b-167">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-167">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="3ff5b-168">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換至 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-168">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="3ff5b-169">啟動 Excel。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-169">Start Excel.</span></span>  
  
4.  <span data-ttu-id="3ff5b-170">使用 [值] 區域中的 [網際網路銷售 - 銷售量]\*\*\*\*，以及報表篩選中的 [客戶地理位置]\*\*\*\* 重新建立樞紐分析表。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-170">Recreate the PivotTable using **Internet Sales-Sales Amount** in the Values area and **Customer Geography** in the Report Filter.</span></span>  
  
     <span data-ttu-id="3ff5b-171">加入從 [所有客戶]\*\*\*\*、[澳大利亞]\*\*\*\*、[昆士蘭]\*\*\*\*、[布里斯本]\*\*\*\*、[4000]\*\*\*\*、[Adam Powell]\*\*\*\* 選取的篩選。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-171">Add a filter that selects from **All Customers**, **Australia**, **Queensland**, **Brisbane**, **4000**, **Adam Powell**.</span></span>  
  
5.  <span data-ttu-id="3ff5b-172">按一下 [網際網路銷售 - 銷售量]\*\*\*\* 資料格，指向 [其他動作]\*\*\*\*，然後按一下 [鑽研至訂單詳細資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-172">Click the **Internet Sales-Sales Amount** data cell, point to **Additional Actions**, and then click **Drillthrough to Order Details**.</span></span>  
  
     <span data-ttu-id="3ff5b-173">傳送給 Adam Powell 的訂購詳細資料會顯示在暫存的工作表中。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-173">The details of these orders shipped to Adam Powell are displayed in a temporary worksheet.</span></span> <span data-ttu-id="3ff5b-174">這項資料包括項目描述、訂單號碼、訂購日期、截止日期和出貨日期資訊，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3ff5b-174">This includes item description, order number, order date, due date, and ship date information, as shown in the following image.</span></span>  
  
     <span data-ttu-id="3ff5b-175">![運送給 Adam Powell 的訂購貨品](../../2014/tutorials/media/l8-action8.gif "運送給 Adam Powell 的訂購貨品")</span><span class="sxs-lookup"><span data-stu-id="3ff5b-175">![Orders shipped to Adam Powell](../../2014/tutorials/media/l8-action8.gif "Orders shipped to Adam Powell")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="3ff5b-176">下一課</span><span class="sxs-lookup"><span data-stu-id="3ff5b-176">Next Lesson</span></span>  
 [<span data-ttu-id="3ff5b-177">第9課：定義觀點和翻譯</span><span class="sxs-lookup"><span data-stu-id="3ff5b-177">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ff5b-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ff5b-178">See Also</span></span>  
 <span data-ttu-id="3ff5b-179">[&#40;Analysis Services 多維度資料的動作&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3ff5b-179">[Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3ff5b-180">[多維度模型中的動作](multidimensional-models/actions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="3ff5b-180">[Actions in Multidimensional Models](multidimensional-models/actions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="3ff5b-181">[維度關聯性](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="3ff5b-181">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="3ff5b-182">[定義事實關聯性](lesson-5-2-defining-a-fact-relationship.md) </span><span class="sxs-lookup"><span data-stu-id="3ff5b-182">[Defining a Fact Relationship](lesson-5-2-defining-a-fact-relationship.md) </span></span>  
 [<span data-ttu-id="3ff5b-183">定義事實關聯性及事實關聯性屬性</span><span class="sxs-lookup"><span data-stu-id="3ff5b-183">Define a Fact Relationship and Fact Relationship Properties</span></span>](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)  
  
  
