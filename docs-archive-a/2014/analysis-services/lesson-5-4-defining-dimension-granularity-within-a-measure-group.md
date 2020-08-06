---
title: 在量值群組內定義維度資料細微性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4f079485-9eb4-405c-9a20-81258298b810
author: minewiskan
ms.author: owend
ms.openlocfilehash: dd1119da70631d66debdf79ecf8c911eedd06d44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594806"
---
# <a name="defining-dimension-granularity-within-a-measure-group"></a><span data-ttu-id="59254-102">在量值群組內定義維度資料粒度</span><span class="sxs-lookup"><span data-stu-id="59254-102">Defining Dimension Granularity within a Measure Group</span></span>
  <span data-ttu-id="59254-103">使用者希望維度事實資料基於不同的用途有不同的資料粒度或具體性。</span><span class="sxs-lookup"><span data-stu-id="59254-103">Users will want to dimension fact data at different granularity or specificity for different purposes.</span></span> <span data-ttu-id="59254-104">例如可能記錄每一天轉售商的銷售資料或網際網路銷售，但銷售配額資訊可能只有當月或當季才有。</span><span class="sxs-lookup"><span data-stu-id="59254-104">For example, sales data for reseller or internet sales may be recorded for each day, whereas sales quota information may only exist at the month or quarter level.</span></span> <span data-ttu-id="59254-105">在這些案例中，使用者希望時間維度對每一個不同的事實資料表有不同的資料粒度或詳細層級。</span><span class="sxs-lookup"><span data-stu-id="59254-105">In these scenarios, users will want a time dimension with a different grain or level of detail for each of these different fact tables.</span></span> <span data-ttu-id="59254-106">雖然您能夠以這種不同的資料粒度將新資料庫維度定義為時間維度，但有更容易的方法，就是使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="59254-106">While you could define a new database dimension as a time dimension with this different grain, there is an easier way with [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="59254-107">根據預設，在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中，當維度使用於量值群組內，該維度內的資料粒度是以維度的索引鍵屬性為基礎。</span><span class="sxs-lookup"><span data-stu-id="59254-107">By default in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], when a dimension is used within a measure group, the grain of the data within that dimension is based on the key attribute of the dimension.</span></span> <span data-ttu-id="59254-108">例如，當 [時間] 維度是包括在量值群組內，且 [時間] 維度的預設資料粒度是每天，則量值群組內的該維度的預設資料粒度就是每天。</span><span class="sxs-lookup"><span data-stu-id="59254-108">For example, when a time dimension is included within a measure group and the default grain of the time dimension is daily, the default grain of that dimension within the measure group is daily.</span></span> <span data-ttu-id="59254-109">這適合許多情況，例如本教學課程中的 [網際網路銷售]\*\*\*\* 和 [轉售商銷售]\*\*\*\* 量值群組。</span><span class="sxs-lookup"><span data-stu-id="59254-109">Many times this is appropriate, such as for the **Internet Sales** and **Reseller Sales** measure groups in this tutorial.</span></span> <span data-ttu-id="59254-110">不過，當這種維度包含在其他類型的量值群組中，例如在銷售配額或預算量值群組中，則每月或每季資料粒度會更加適合。</span><span class="sxs-lookup"><span data-stu-id="59254-110">However, when such a dimension is included in other types of measure groups, such as in a sales quota or budget measure group, a monthly or quarterly grain is generally more appropriate.</span></span>  
  
 <span data-ttu-id="59254-111">若要對 Cube 維度指定預設資料粒度以外的資料粒度，您必須在 [Cube 設計師] 的 [維度使用方式]\*\*\*\* 索引標籤上，修改特定量值群組內使用的 Cube 維度的資料粒度屬性。</span><span class="sxs-lookup"><span data-stu-id="59254-111">To specify a grain for a cube dimension other than the default grain, you modify the granularity attribute for a cube dimension as used within a particular measure group on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="59254-112">當您將特定量值群組內的維度資料粒度變更為該維度的索引鍵屬性以外的屬性時，必須保證該量值群組中的所有其他屬性均與新的資料粒度屬性直接或間接相關。</span><span class="sxs-lookup"><span data-stu-id="59254-112">When you change the grain of a dimension within a specific measure group to an attribute other than the key attribute for that dimension, you must guarantee that all other attributes in the measure group are directly or indirectly related to new granularity attribute.</span></span> <span data-ttu-id="59254-113">您可以在所有其他屬性與指定為量值群組中的資料粒度屬性的那個屬性之間指定屬性關聯性，來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="59254-113">You do this by specifying attribute relationships between all other attributes and the attribute that is specified as the granularity attribute in the measure group.</span></span> <span data-ttu-id="59254-114">在本案例中，您會定義其他的屬性關聯性，而不是移動屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="59254-114">In this case, you define additional attribute relationships rather than move attribute relationships.</span></span> <span data-ttu-id="59254-115">實際上，對維度中的其餘屬性來說，指定為資料粒度屬性的屬性會成為量值群組內的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="59254-115">The attribute that is specified as the granularity attribute effectively becomes the key attribute within the measure group for the remaining attributes in the dimension.</span></span> <span data-ttu-id="59254-116">如果您未適當地指定屬性關聯性， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 將無法正確彙總各值，您將在這個主題的工作中看到這種情況。</span><span class="sxs-lookup"><span data-stu-id="59254-116">If you do not specify attribute relationships appropriately, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will not be able to aggregate values correctly, as you will see in the tasks in this topic.</span></span>  
  
 <span data-ttu-id="59254-117">如需詳細資訊，請參閱 [維度關聯性](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)、 [定義一般關聯性及一般關聯性屬性](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="59254-117">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), [Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md).</span></span>  
  
 <span data-ttu-id="59254-118">在這個主題的工作中，您會加入 [銷售配額] 量值群組，以及在這個量值群組中將 [日期] 維度的資料粒度定義為每月。</span><span class="sxs-lookup"><span data-stu-id="59254-118">In the tasks in this topic, you add a Sales Quotas measure group and define the granularity of the Date dimension in this measure group to be monthly.</span></span> <span data-ttu-id="59254-119">然後您會在月份屬性和其他維度屬性之間定義屬性關聯性，以確定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 可正確彙總各值。</span><span class="sxs-lookup"><span data-stu-id="59254-119">You then define attribute relationships between the month attribute and other dimension attributes to ensure that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] aggregates values correctly.</span></span>  
  
## <a name="adding-tables-and-defining-the-sales-quotas-measure-group"></a><span data-ttu-id="59254-120">加入資料表及定義 [銷售配額] 量值群組</span><span class="sxs-lookup"><span data-stu-id="59254-120">Adding Tables and Defining the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="59254-121">請切換到 [Adventure Works DW 2012]\*\*\*\* 資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="59254-121">Switch to the **Adventure Works DW 2012** data source view.</span></span>  
  
2.  <span data-ttu-id="59254-122">以滑鼠右鍵按一下 [**圖表召集人**] 窗格中的任何位置，然後按一下 [**新增圖表**]，再為圖表命名 `Sales Quotas` 。</span><span class="sxs-lookup"><span data-stu-id="59254-122">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and then name the diagram `Sales Quotas`.</span></span>  
  
3.  <span data-ttu-id="59254-123">從 [資料表] 窗格將 [**員工**]、[**銷售**領域] 和 [資料表] 拖曳 `Date` 至 [**圖表**] 窗格。 **Tables**</span><span class="sxs-lookup"><span data-stu-id="59254-123">Drag the **Employee**, **Sales Territory**, and `Date` tables from the **Tables** pane to the **Diagram** pane.</span></span>  
  
4.  <span data-ttu-id="59254-124">以滑鼠右鍵按一下 [圖表]\*\*\*\* 窗格中的任何位置，並選取 [加入/移除資料表]\*\*\*\* 即可將 [FactSalesQuota]\*\*\*\* 資料表加入 [圖表]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="59254-124">Add the **FactSalesQuota** table to the **Diagram** pane by right-clicking anywhere in the **Diagram** pane and selecting **Add/Remove Tables**.</span></span>  
  
     <span data-ttu-id="59254-125">請注意，[SalesTerritory]\*\*\*\* 資料表是透過 [員工]\*\*\*\* 資料表而連結到 [FactSalesQuota]\*\*\*\* 資料表。</span><span class="sxs-lookup"><span data-stu-id="59254-125">Notice that the **SalesTerritory** table is linked to the **FactSalesQuota** table through the **Employee** table.</span></span>  
  
5.  <span data-ttu-id="59254-126">檢閱 [FactSalesQuota]\*\*\*\* 資料表中的資料行，然後瀏覽這個資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="59254-126">Review the columns in the **FactSalesQuota** table and then explore the data in this table.</span></span>  
  
     <span data-ttu-id="59254-127">請注意，這個資料表內的資料粒度是日曆季，這是 [FactSalesQuota] 資料表的最低層級詳細資料。</span><span class="sxs-lookup"><span data-stu-id="59254-127">Notice that the grain of the data within this table is the calendar quarter, which is the lowest level of detail in the FactSalesQuota table.</span></span>  
  
6.  <span data-ttu-id="59254-128">在 [資料來源視圖設計工具] 中，將**FactSalesQuota**資料表的 [ **FriendlyName** ] 屬性變更為 `SalesQuotas` 。</span><span class="sxs-lookup"><span data-stu-id="59254-128">In Data Source View Designer, change the **FriendlyName** property of the **FactSalesQuota** table to `SalesQuotas`.</span></span>  
  
7.  <span data-ttu-id="59254-129">請切換到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程的 Cube，然後按一下 [Cube 結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="59254-129">Switch to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>  
  
8.  <span data-ttu-id="59254-130">以滑鼠右鍵按一下 [**量值**] 窗格中的任何位置，按一下 [**新增量值群組**]，按一下 `SalesQuotas` [**新增量值群組**] 對話方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="59254-130">Right-click anywhere in the **Measures** pane, click **New Measure Group**, click `SalesQuotas` in the **New Measure Group** dialog box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="59254-131">`Sales Quotas`量值群組會出現在 [**量值**] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="59254-131">The `Sales Quotas` measure group appears in the **Measures** pane.</span></span> <span data-ttu-id="59254-132">在 [**維度**] 窗格中，請注意， `Date` 也會根據資料庫維度定義新的 cube 維度 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="59254-132">In the **Dimensions** pane, notice that a new `Date` cube dimension is also defined, based on the `Date` database dimension.</span></span> <span data-ttu-id="59254-133">會定義新的時間相關 Cube 維度，是因為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 不知道 [FactSalesQuota]\*\*\*\* 事實資料表中的 [DateKey]\*\*\*\* 資料行是與哪一個現有的時間相關 Cube 維度有關，這個事實資料表就是 Sales Quotas 量值群組的基礎。</span><span class="sxs-lookup"><span data-stu-id="59254-133">A new time-related cube dimension is defined because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] does not know which of the existing time-related cube dimensions to relate to the **DateKey** column in the **FactSalesQuota** fact table that underlies the Sales Quotas measure group.</span></span> <span data-ttu-id="59254-134">稍後您會在這個主題的另一項工作中加以變更。</span><span class="sxs-lookup"><span data-stu-id="59254-134">You will change this later in another task in this topic.</span></span>  
  
9. <span data-ttu-id="59254-135">展開 `Sales Quotas` 量值群組。</span><span class="sxs-lookup"><span data-stu-id="59254-135">Expand the `Sales Quotas` measure group.</span></span>  
  
10. <span data-ttu-id="59254-136">在 [量值]\*\*\*\* 窗格中，選取 [銷售量配額]\*\*\*\*，然後在 [屬性] 視窗中將 [FormatString]\*\*\*\* 屬性的值設為 [貨幣]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-136">In the **Measures** pane, select **Sales Amount Quota**, and then set the value for the **FormatString** property to **Currency** in the Properties window.</span></span>  
  
11. <span data-ttu-id="59254-137">選取 [**銷售配額計數**] 量值，然後 `#,#` 在 [屬性視窗中輸入作為 [**格式**] 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="59254-137">Select the **Sales Quotas Count** measure, and then type `#,#` as the value for the **FormatString** property in the Properties window.</span></span>  
  
12. <span data-ttu-id="59254-138">從量值群組中刪除 [**日曆季**] 量值 `Sales Quotas` 。</span><span class="sxs-lookup"><span data-stu-id="59254-138">Delete the **Calendar Quarter** measure from the `Sales Quotas` measure group.</span></span>  
  
     [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="59254-139">偵測到作為 [日曆季] 量值基礎的資料行是包含量值的資料行。</span><span class="sxs-lookup"><span data-stu-id="59254-139">detected the column that underlies the Calendar Quarter measure as a column that contains measures.</span></span> <span data-ttu-id="59254-140">不過，這個資料行和 CalendarYear 資料行都包含您稍後在這個主題中用於連結 [銷售配額] 量值群組與 [日期] 維度的值。</span><span class="sxs-lookup"><span data-stu-id="59254-140">However, this column and the CalendarYear column contain the values that you will use to link the Sales Quotas measure group to the Date dimension later in this topic.</span></span>  
  
13. <span data-ttu-id="59254-141">在 [**量值**] 窗格中，以滑鼠右鍵按一下 `Sales Quotas` 量值群組，然後按一下 [**新增量值**]。</span><span class="sxs-lookup"><span data-stu-id="59254-141">In the **Measures** pane, right-click the `Sales Quotas` measure group, and then click **New Measure**.</span></span>  
  
     <span data-ttu-id="59254-142">此時會開啟 [新增量值]\*\*\*\* 對話方塊，它包含使用類型為 [總和]\*\*\*\* 的量值可用的來源資料行。</span><span class="sxs-lookup"><span data-stu-id="59254-142">The **New Measure** dialog box opens, containing the available source columns for a measure with a usage type of **Sum**.</span></span>  
  
14. <span data-ttu-id="59254-143">在 [**新增量值**] 對話方塊中，選取 [**使用**方式] 清單中的 [**相異計數**]，確認已在 [來源資料行] 清單中選取 [ `SalesQuotas` **EmployeeKey** ]，然後按一下 **[確定]**。 **Source table** **Source column**</span><span class="sxs-lookup"><span data-stu-id="59254-143">In the **New Measure** dialog box, select **Distinct count** in the **Usage** list, verify that `SalesQuotas` is selected in the **Source table** list, select **EmployeeKey** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="59254-144">請注意，量值是建立在一個叫作 [銷售配額 1]\*\*\*\* 的新量值群組中。</span><span class="sxs-lookup"><span data-stu-id="59254-144">Notice that the measure is created in a new measure group named **Sales Quotas 1**.</span></span> <span data-ttu-id="59254-145">而 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的相異計數量值則建立在其自己的量值群組中，以使處理效能最大化。</span><span class="sxs-lookup"><span data-stu-id="59254-145">Distinct count measures in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are created in their own measure groups to maximize processing performance.</span></span>  
  
15. <span data-ttu-id="59254-146">將 [**員工索引鍵相異計數**] 量值的 [**名稱**] 屬性值變更為 `Sales Person Count` ，然後輸入做為 `#,#` [**格式**名稱] 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="59254-146">Change the value for the **Name** property for the **Employee Key Distinct Count** measure to `Sales Person Count`, and then type `#,#` as the value for the **FormatString** property.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="59254-147">按日期瀏覽銷售配額量值群組中的量值</span><span class="sxs-lookup"><span data-stu-id="59254-147">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="59254-148">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-148">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="59254-149">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，按一下 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="59254-149">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>  
  
3.  <span data-ttu-id="59254-150">按一下 Excel 捷徑，然後按一下 [啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-150">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="59254-151">在 [樞紐分析表欄位清單] 中，展開 `Sales Quotas` 量值群組，然後將 [**銷售量配額**] 量值拖曳至 [值] 區域。</span><span class="sxs-lookup"><span data-stu-id="59254-151">In the PivotTable Field List, expand the `Sales Quotas` measure group, and then drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="59254-152">展開 [銷售領域]\*\*\*\* 維度，然後將 [銷售領域]\*\*\*\* 使用者定義階層拖曳至 [資料列標籤]。</span><span class="sxs-lookup"><span data-stu-id="59254-152">Expand the **Sales Territory** dimension, and then drag the **Sales Territories** user-defined hierarchy to Row Labels.</span></span>  
  
     <span data-ttu-id="59254-153">請注意，[銷售領域] Cube 維度與 [事實銷售配額] 資料表並無直接或間接關係，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="59254-153">Notice that the Sales Territory cube dimension is not related, directly or indirectly, to the Fact Sales Quota table, as shown in the following image.</span></span>  
  
     <span data-ttu-id="59254-154">![銷售領域 cube 維度](../../2014/tutorials/media/l5-granularity-2.gif "銷售區域 Cube 維度")</span><span class="sxs-lookup"><span data-stu-id="59254-154">![Sales Territory cube dimension](../../2014/tutorials/media/l5-granularity-2.gif "Sales Territory cube dimension")</span></span>  
  
     <span data-ttu-id="59254-155">在這個主題的下一系列的步驟中，您將會在這個維度與這個事實資料表之間定義參考維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="59254-155">In the next series of steps in this topic you will define a reference dimension relationship between this dimension and this fact table.</span></span>  
  
6.  <span data-ttu-id="59254-156">將 [銷售領域]\*\*\*\* 使用者階層從 [資料列標籤] 區域移至 [資料行標籤] 區域。</span><span class="sxs-lookup"><span data-stu-id="59254-156">Move the **Sales Territories** user hierarchy from the Rows Labels area to the Column Labels area.</span></span>  
  
7.  <span data-ttu-id="59254-157">在樞紐分析表欄位清單中，選取 [銷售領域]\*\*\*\* 使用者定義階層，然後按一下右側的向下箭號。</span><span class="sxs-lookup"><span data-stu-id="59254-157">In the PivotTable Field list, select the **Sales Territories** user-defined hierarchy, and then click the down arrow to the right.</span></span>  
  
     <span data-ttu-id="59254-158">![欄位清單中的銷售領域階層](../../2014/tutorials/media/l5-granularity-1a.png "欄位清單中的銷售領域階層")</span><span class="sxs-lookup"><span data-stu-id="59254-158">![Sales Territories hierarchy in the field list](../../2014/tutorials/media/l5-granularity-1a.png "Sales Territories hierarchy in the field list")</span></span>  
  
8.  <span data-ttu-id="59254-159">在篩選中，按一下 [全選] 核取方塊以清除所有選取項目，然後只選擇 [北美洲]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-159">In the filter, click the Select All checkbox to clear all the selections, and then choose just **North America**.</span></span>  
  
     <span data-ttu-id="59254-160">![用來選取北美的篩選窗格](../../2014/tutorials/media/l5-granularity-1b.png "用來選取北美的篩選窗格")</span><span class="sxs-lookup"><span data-stu-id="59254-160">![Filter pane for selecting North America](../../2014/tutorials/media/l5-granularity-1b.png "Filter pane for selecting North America")</span></span>  
  
9. <span data-ttu-id="59254-161">在 [樞紐分析表欄位清單] 中，展開 [] `Date` 。</span><span class="sxs-lookup"><span data-stu-id="59254-161">In the PivotTable Field List, expand `Date`.</span></span>  
  
10. <span data-ttu-id="59254-162">將 [Date.Fiscal Date]\*\*\*\* 使用者階層拖曳至 [資料列標籤]</span><span class="sxs-lookup"><span data-stu-id="59254-162">Drag the **Date.Fiscal Date** user hierarchy to Row Labels</span></span>  
  
11. <span data-ttu-id="59254-163">在樞紐分析表上，按一下 [資料列標籤] 旁邊的向下鍵。</span><span class="sxs-lookup"><span data-stu-id="59254-163">On the PivotTable, click the down arrow next to Row Labels.</span></span> <span data-ttu-id="59254-164">清除 [FY 2008]\*\*\*\* 之外的所有年份。</span><span class="sxs-lookup"><span data-stu-id="59254-164">Clear all of the years except for **FY 2008**.</span></span>  
  
     <span data-ttu-id="59254-165">請注意，只有 [**月**] 層級的**2007 年7月**成員才會出現，而不是 [月1日]、[ **2007**]、[8 月] **、[2007**] 和 [9 月]、[ **month** ] 層級的 [ **2007**成員]，而且只會出現層級的**2007**成員 `Date` ，而非</span><span class="sxs-lookup"><span data-stu-id="59254-165">Notice that only the **July 2007** member of the **Month** level appears, instead of the **July, 2007**, **August, 2007**, and **September, 2007** members of **Month** level, and that only the **July 1, 2007** member of the `Date` level appears, instead of all 31 days.</span></span> <span data-ttu-id="59254-166">之所以會發生這種行為，是因為事實資料表中的資料細微性是在季層級，而維度的細微性 `Date` 是每日層級。</span><span class="sxs-lookup"><span data-stu-id="59254-166">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the `Date` dimension is the daily level.</span></span> <span data-ttu-id="59254-167">您會在這個主題的下一項工作中變更這種行為。</span><span class="sxs-lookup"><span data-stu-id="59254-167">You will change this behavior in the next task in this topic.</span></span>  
  
     <span data-ttu-id="59254-168">同樣也請注意，月和日層級的 [銷售量配額]\*\*\*\* 值與季層級的值相同，都是 $13,733,000.00。</span><span class="sxs-lookup"><span data-stu-id="59254-168">Notice also that the **Sales Amount Quota** value for the month and day levels is the same value as for the quarter level, $13,733,000.00.</span></span> <span data-ttu-id="59254-169">這是因為 [銷售配額] 量值群組中的資料最低層級是在季層級。</span><span class="sxs-lookup"><span data-stu-id="59254-169">This is because the lowest level of data in the Sales Quotas measure group is at the quarter level.</span></span> <span data-ttu-id="59254-170">您會在第 6 課變更這種行為。</span><span class="sxs-lookup"><span data-stu-id="59254-170">You will change this behavior in Lesson 6.</span></span>  
  
     <span data-ttu-id="59254-171">下圖顯示 [銷售量配額]\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="59254-171">The following image shows the values for **Sales Amount Quota**.</span></span>  
  
     <span data-ttu-id="59254-172">![銷售額配額的值](../../2014/tutorials/media/l5-granularity-3.png "銷售額配額的值")</span><span class="sxs-lookup"><span data-stu-id="59254-172">![Values for Sales Amount Quota](../../2014/tutorials/media/l5-granularity-3.png "Values for Sales Amount Quota")</span></span>  
  
## <a name="defining-dimension-usage-properties-for-the-sales-quotas-measure-group"></a><span data-ttu-id="59254-173">定義 [銷售配額] 量值群組的維度使用方式屬性</span><span class="sxs-lookup"><span data-stu-id="59254-173">Defining Dimension Usage Properties for the Sales Quotas Measure Group</span></span>  
  
1.  <span data-ttu-id="59254-174">針對 [員工]\*\*\*\* 維度開啟 [維度設計師]，以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的 [SalesTerritoryKey]\*\*\*\*，然後按一下 [從資料行新增屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-174">Open Dimension Designer for the **Employee** dimension, right-click **SalesTerritoryKey** in the **Data Source View** pane, and then click **New Attribute from Column**.</span></span>  
  
2.  <span data-ttu-id="59254-175">在 [屬性]\*\*\*\* (attribute) 窗格中，選取 [SalesTerritoryKey]\*\*\*\*，然後在 [屬性] (property) 視窗中，將 [AttributeHierarchyVisible]\*\*\*\* 屬性 (property) 設定為 [False]\*\*\*\*、將 [AttributeHierarchyOptimizedState]\*\*\*\* 屬性 (property) 設定為 [NotOptimized]\*\*\*\*，並且將 [AttributeHierarchyOrdered]\*\*\*\* 屬性 (property) 設定為 [False]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-175">In the **Attributes** pane, select **SalesTerritoryKey**, and then set the **AttributeHierarchyVisible** property to **False** in the Properties window, set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, and set the **AttributeHierarchyOrdered** property to **False**.</span></span>  
  
     <span data-ttu-id="59254-176">將 [**銷售**領域] 維度連結至 [銷售 `Sales Quotas` **配額 1** ] 量值群組做為參考維度時，需要此屬性。</span><span class="sxs-lookup"><span data-stu-id="59254-176">This attribute is required to link the **Sales Territory** dimension to the `Sales Quotas` and **Sales Quotas 1** measure groups as a referenced dimension.</span></span>  
  
3.  <span data-ttu-id="59254-177">在教學課程 cube 的 Cube 設計師中 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，按一下 [**維度使用**方式] 索引標籤，然後檢查 [ `Sales Quotas` **銷售配額 1** ] 量值群組內的維度使用方式。</span><span class="sxs-lookup"><span data-stu-id="59254-177">In Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab, and then review the dimension usage within the `Sales Quotas` and **Sales Quotas 1** measure groups.</span></span>  
  
     <span data-ttu-id="59254-178">請注意， **Employee**和 `Date` cube 維度會透過一般關聯性連結至**sales Quotasand sales 配額 1**量值群組。</span><span class="sxs-lookup"><span data-stu-id="59254-178">Notice that the **Employee** and `Date` cube dimensions are linked to the **Sales Quotasand Sales Quotas 1** measure groups through regular relationships.</span></span> <span data-ttu-id="59254-179">也請注意，[銷售領域]\*\*\*\* Cube 維度並未連結到其中任何量值群組。</span><span class="sxs-lookup"><span data-stu-id="59254-179">Notice also that the **Sales Territory** cube dimension is not linked to either of these measure groups.</span></span>  
  
4.  <span data-ttu-id="59254-180">按一下 [**銷售**領域] 維度和量值群組交集處的資料格，然後 `Sales Quotas` 按一下 [流覽] 按鈕 (**...** ]) 。[**定義關聯**性] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="59254-180">Click the cell at the intersection of the **Sales Territory** dimension and the `Sales Quotas` measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="59254-181">在 [選取關聯性類型]\*\*\*\* 清單中，選取 [參考的]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-181">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
6.  <span data-ttu-id="59254-182">在 [中繼維度]\*\*\*\* 清單中，選取 [員工]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-182">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
7.  <span data-ttu-id="59254-183">在 [參考維度屬性]\*\*\*\* 清單中，選取 [銷售領域地區]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-183">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
8.  <span data-ttu-id="59254-184">在 [中繼維度屬性]\*\*\*\* 清單中，選取 [銷售領域索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-184">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="59254-185">([銷售領域地區] 屬性的索引鍵資料行是 SalesTerritoryKey 資料行)。</span><span class="sxs-lookup"><span data-stu-id="59254-185">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
9. <span data-ttu-id="59254-186">確認已選取 [具體化]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="59254-186">Verify that the **Materialize** check box is selected.</span></span>  
  
10. <span data-ttu-id="59254-187">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="59254-187">Click **OK**.</span></span>  
  
11. <span data-ttu-id="59254-188">在 [**銷售**領域] 維度和 [**銷售配額 1** ] 量值群組的交集處，按一下資料格，然後按一下 [流覽] 按鈕 (**...** ]) 。[**定義關聯**性] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="59254-188">Click the cell at the intersection of the **Sales Territory** dimension and the **Sales Quotas 1** measure group and then click the browse button (**...**). The **Define Relationship** dialog box opens.</span></span>  
  
12. <span data-ttu-id="59254-189">在 [選取關聯性類型]\*\*\*\* 清單中，選取 [參考的]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-189">In the **Select relationship type** list, select **Referenced**.</span></span>  
  
13. <span data-ttu-id="59254-190">在 [中繼維度]\*\*\*\* 清單中，選取 [員工]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-190">In the **Intermediate dimension** list, select **Employee**.</span></span>  
  
14. <span data-ttu-id="59254-191">在 [參考維度屬性]\*\*\*\* 清單中，選取 [銷售領域地區]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-191">In the **Reference dimension attribute** list, select **Sales Territory Region.**</span></span>  
  
15. <span data-ttu-id="59254-192">在 [中繼維度屬性]\*\*\*\* 清單中，選取 [銷售領域索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-192">In the **Intermediate dimension attribute** list, select **Sales Territory Key**.</span></span> <span data-ttu-id="59254-193">([銷售領域地區] 屬性的索引鍵資料行是 SalesTerritoryKey 資料行)。</span><span class="sxs-lookup"><span data-stu-id="59254-193">(The key column for the Sales Territory Region attribute is the SalesTerritoryKey column.)</span></span>  
  
16. <span data-ttu-id="59254-194">確認已選取 [具體化]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="59254-194">Verify that the **Materialize** check box is selected.</span></span>  
  
17. <span data-ttu-id="59254-195">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="59254-195">Click **OK**.</span></span>  
  
18. <span data-ttu-id="59254-196">刪除 `Date` cube 維度。</span><span class="sxs-lookup"><span data-stu-id="59254-196">Delete the `Date` cube dimension.</span></span>  
  
     <span data-ttu-id="59254-197">您不需要有四個時間相關的 cube 維度，而是使用量值群組中的 [**訂單日期**] cube 維度， `Sales Quotas` 做為維度銷售配額的日期。</span><span class="sxs-lookup"><span data-stu-id="59254-197">Instead of having four time-related cube dimensions, you will use the **Order Date** cube dimension in the `Sales Quotas` measure group as the date against which sales quotas will be dimensioned.</span></span> <span data-ttu-id="59254-198">您也會使用這個 Cube 維度做為 Cube 中的主要日期維度。</span><span class="sxs-lookup"><span data-stu-id="59254-198">You will also use this cube dimension as the primary date dimension in the cube.</span></span>  
  
19. <span data-ttu-id="59254-199">在 [**維度**] 清單中，將 [**訂單日期**] cube 維度重新命名為 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="59254-199">In the **Dimensions** list, rename the **Order Date** cube dimension to `Date`.</span></span>  
  
     <span data-ttu-id="59254-200">將 [**訂單日期**] cube 維度重新命名，可 `Date` 讓使用者更容易瞭解其在這個 cube 中做為主要日期維度的角色。</span><span class="sxs-lookup"><span data-stu-id="59254-200">Renaming the **Order Date** cube dimension to `Date` makes it easier for users to understand its role as the primary date dimension in this cube.</span></span>  
  
20. <span data-ttu-id="59254-201">在 **...** `Sales Quotas` 量值群組和維度交集的資料格中，按一下 [流覽] 按鈕 (...) 。 `Date`</span><span class="sxs-lookup"><span data-stu-id="59254-201">Click the browse button (**...**) in the cell at the intersection of the `Sales Quotas` measure group and the `Date` dimension.</span></span>  
  
21. <span data-ttu-id="59254-202">在 [定義關聯性]\*\*\*\* 對話方塊中，選取 [選取關聯性類型]\*\*\*\* 清單中的 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-202">In the **Define Relationship** dialog box, select **Regular** in the **Select relationship type** list.</span></span>  
  
22. <span data-ttu-id="59254-203">在 [資料粒度屬性]\*\*\*\* 清單中，選取 [日曆季]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-203">In the **Granularity attribute** list, select **Calendar Quarter**.</span></span>  
  
     <span data-ttu-id="59254-204">請注意，會出現警告通知您，因為您已選取非索引鍵屬性做為資料粒度屬性，所以必須以指定為成員屬性的方式，來確定所有其他屬性均與資料粒度屬性直接或間接有關。</span><span class="sxs-lookup"><span data-stu-id="59254-204">Notice that a warning appears to notify you that because you have selected a non-key attribute as the granularity attribute, you must make sure that all other attributes are directly or indirectly related to the granularity attribute by specifying them as member properties.</span></span>  
  
23. <span data-ttu-id="59254-205">在 [定義關聯性]\*\*\*\* 對話方塊的 [關聯性]\*\*\*\* 區域中，將 [日期] Cube 維度之基礎資料表中的 [CalendarYear]\*\*\*\* 及 [CalendarQuarter]\*\*\*\* 維度資料行，與 [銷售配額] 量值群組之基礎資料表中的 [CalendarYear]\*\*\*\* 及 [CalendarQuarter]\*\*\*\* 資料行相連結，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-205">In the **Relationship** area of the **Define Relationship** dialog box, link the **CalendarYear** and **CalendarQuarter** dimension columns from the table that underlies the Date cube dimension to the **CalendarYear** and **CalendarQuarter** columns in the table that underlies the Sales Quota measure group, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="59254-206">「日曆季」是定義為「銷售配額」量值群組中之日期 Cube 維度的資料粒度屬性，但 [日期] 屬性仍會是「網際網路銷售」及「轉售商銷售」量值群組的資料粒度屬性。</span><span class="sxs-lookup"><span data-stu-id="59254-206">The Calendar Quarter is defined as the granularity attribute for the Date cube dimension in the Sales Quotas measure group, but the Date attribute continues to be the granularity attribute for the Internet Sales and Reseller Sales measure groups.</span></span>  
  
24. <span data-ttu-id="59254-207">對 [銷售配額 1]\*\*\*\* 量值群組重複前面 4 個步驟。</span><span class="sxs-lookup"><span data-stu-id="59254-207">Repeat the previous four steps for the **Sales Quotas 1** measure group.</span></span>  
  
## <a name="defining-attribute-relationships-between-the-calendar-quarter-attribute-and-the-other-dimension-attributes-in-the-date-dimension"></a><span data-ttu-id="59254-208">在日曆季屬性和日期維度的其他維度屬性之間定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="59254-208">Defining Attribute Relationships Between the Calendar Quarter Attribute and the Other Dimension Attributes in the Date Dimension</span></span>  
  
1.  <span data-ttu-id="59254-209">針對維度，切換到**維度設計師** `Date` ，然後按一下 [**屬性關聯**性] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="59254-209">Switch to **Dimension Designer** for the `Date` dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="59254-210">請注意，雖然 [日曆年度] 是透過 [**日曆半\*\*\*\*年**] 屬性連結到 [**日曆季**]，但會計日曆屬性只會連結至另一個。它們不會連結到 [**日曆季**] 屬性，因此不會在 `Sales Quotas` 量值群組中正確匯總。</span><span class="sxs-lookup"><span data-stu-id="59254-210">Notice that although **Calendar Year** is linked to **Calendar Quarter** through the **Calendar Semester** attribute, the fiscal calendar attributes are linked only to one another; they are not linked to the **Calendar Quarter** attribute and therefore will not aggregate correctly in the `Sales Quotas` measure group.</span></span>  
  
2.  <span data-ttu-id="59254-211">在圖表中，以滑鼠右鍵按一下 [日曆季]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-211">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="59254-212">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [日曆季]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="59254-213">將 [相關屬性]\*\*\*\* 設定為 [會計季度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-213">Set the **Related Attribute** to **Fiscal Quarter**.</span></span>  
  
4.  <span data-ttu-id="59254-214">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="59254-214">Click **OK**.</span></span>  
  
     <span data-ttu-id="59254-215">請注意，會出現一則警告訊息，指出該 `Date` 維度包含一個或多個重複的屬性關聯性，當非索引鍵屬性當做資料細微性屬性使用時，可能會導致無法匯總資料。</span><span class="sxs-lookup"><span data-stu-id="59254-215">Notice that a warning message appears stating that the `Date` dimension contains one or more redundant attribute relationships that may prevent data from being aggregated when a non-key attribute is used as a granularity attribute.</span></span>  
  
5.  <span data-ttu-id="59254-216">刪除 [月份]\*\*\*\* 屬性與 [會計季度]\*\*\*\* 屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="59254-216">Delete the attribute relationship between the **Month Name** attribute and the **Fiscal Quarter** attribute.</span></span>  
  
6.  <span data-ttu-id="59254-217">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="59254-217">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="browsing-the-measures-in-the-sales-quota-measure-group-by-date"></a><span data-ttu-id="59254-218">按日期瀏覽銷售配額量值群組中的量值</span><span class="sxs-lookup"><span data-stu-id="59254-218">Browsing the Measures in the Sales Quota Measure Group by Date</span></span>  
  
1.  <span data-ttu-id="59254-219">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-219">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="59254-220">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，按一下 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-220">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>  
  
3.  <span data-ttu-id="59254-221">按一下 Excel 捷徑，然後按一下 [啟用]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-221">Click the Excel shortcut, and then click **Enable**.</span></span>  
  
4.  <span data-ttu-id="59254-222">將 [銷售量配額]\*\*\*\* 量值拖曳至 [值] 區域。</span><span class="sxs-lookup"><span data-stu-id="59254-222">Drag the **Sales Amount Quota** measure to the Values area.</span></span>  
  
5.  <span data-ttu-id="59254-223">將 [銷售領域]\*\*\*\* 使用者階層拖曳至 [資料行標籤]，然後針對 [北美洲]\*\*\*\* 篩選。</span><span class="sxs-lookup"><span data-stu-id="59254-223">Drag the **Sales Territories** user hierarchy to the Column Labels, and then filter on **North America**.</span></span>  
  
6.  <span data-ttu-id="59254-224">將 [Date.FiscalDate]\*\*\*\* 使用者階層拖曳至 [資料列標籤] 中，然後按一下樞紐分析表上 [資料列標籤]\*\*\*\* 旁邊的向下箭號，並清除 [FY 2008]\*\*\*\* 以外的所有核取方塊，只顯示 2008 會計年度。</span><span class="sxs-lookup"><span data-stu-id="59254-224">Drag the **Date.FiscalDate** user hierarchy to the Row Labels, and then click the down arrow next to **Row Labels** on the PivotTable, and clear all check boxes other than **FY 2008**, to display only fiscal year 2008.</span></span>  
  
7.  <span data-ttu-id="59254-225">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="59254-225">Click OK.</span></span>  
  
8.  <span data-ttu-id="59254-226">依序展開 [FY 2008]\*\*\*\*、[H1 FY 2008]\*\*\*\* 和 [Q1 FY 2008]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="59254-226">Expand **FY 2008**, expand **H1 FY 2008**, and then expand **Q1 FY 2008**.</span></span>  
  
     <span data-ttu-id="59254-227">下圖顯示適用於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的樞紐分析表，其 [銷售配額] 量值群組已正確建立維度。</span><span class="sxs-lookup"><span data-stu-id="59254-227">The following image shows a PivotTable for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, with the Sales Quota measure group dimensioned correctly.</span></span>  
  
     <span data-ttu-id="59254-228">請注意，會計季度層級的每一個成員都有與季層級相同的值。</span><span class="sxs-lookup"><span data-stu-id="59254-228">Notice that each member of the fiscal quarter level has the same value as the quarter level.</span></span> <span data-ttu-id="59254-229">使用 [Q1 FY 2008]\*\*\*\* 當作範例，[Q1 FY 2008]\*\*\*\* 的配額 $9,180,000.00 也是其每個成員的值。</span><span class="sxs-lookup"><span data-stu-id="59254-229">Using **Q1 FY 2008** as an example, the quota of $9,180,000.00 for **Q1 FY 2008** is also the value for each of its members.</span></span> <span data-ttu-id="59254-230">之所以會發生這種行為，是因為事實資料表中的資料粒度是在季層級，而 [日期] 維度的資料粒度也是在季層級。</span><span class="sxs-lookup"><span data-stu-id="59254-230">This behavior occurs because the grain of the data in the fact table is at the quarter level and the grain of the Date dimension is also at the quarter level.</span></span> <span data-ttu-id="59254-231">在第 6 課，您將了解如何按比例配置每月的季量。</span><span class="sxs-lookup"><span data-stu-id="59254-231">In Lesson 6, you will learn how to allocate the quarterly amount proportionally to each month.</span></span>  
  
     <span data-ttu-id="59254-232">![正確建立維度的銷售配額量值群組](../../2014/tutorials/media/l5-granularity-7.gif "正確建立維度的銷售配額量值群組")</span><span class="sxs-lookup"><span data-stu-id="59254-232">![Sales Quota measure group dimensioned correctly](../../2014/tutorials/media/l5-granularity-7.gif "Sales Quota measure group dimensioned correctly")</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="59254-233">下一課</span><span class="sxs-lookup"><span data-stu-id="59254-233">Next Lesson</span></span>  
 [<span data-ttu-id="59254-234">第6課：定義計算</span><span class="sxs-lookup"><span data-stu-id="59254-234">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="59254-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59254-235">See Also</span></span>  
 <span data-ttu-id="59254-236">[維度關聯性](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span><span class="sxs-lookup"><span data-stu-id="59254-236">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) </span></span>  
 <span data-ttu-id="59254-237">[定義一般關聯性和一般關聯性屬性](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span><span class="sxs-lookup"><span data-stu-id="59254-237">[Define a Regular Relationship and Regular Relationship Properties](multidimensional-models/define-a-regular-relationship-and-regular-relationship-properties.md) </span></span>  
 [<span data-ttu-id="59254-238">在資料來源檢視設計工具中使用圖表 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="59254-238">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
