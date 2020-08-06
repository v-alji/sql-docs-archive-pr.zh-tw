---
title: 定義多對多關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bebb174-148c-4cbb-a285-2f6d536a16d5
author: minewiskan
ms.author: owend
ms.openlocfilehash: fb4e18831ae23b8cf1f0702b357672f7520478a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698794"
---
# <a name="defining-a-many-to-many-relationship"></a><span data-ttu-id="bbc3e-102">定義多對多關聯性</span><span class="sxs-lookup"><span data-stu-id="bbc3e-102">Defining a Many-to-Many Relationship</span></span>
  <span data-ttu-id="bbc3e-103">定義維度時，通常每一個事實只聯結到一個維度成員，而單一維度成員可以與許多不同事實相關聯。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-103">When you define a dimension, typically each fact joins to one and only one dimension member, whereas a single dimension member can be associated with many different facts.</span></span> <span data-ttu-id="bbc3e-104">例如，每個客戶可以有許多張訂單，但是每張訂單只會屬於單一客戶。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-104">For example, each customer can have many orders but each order belongs to a single customer.</span></span> <span data-ttu-id="bbc3e-105">在關係資料庫術語中，這稱為「*一對多關聯性*」。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-105">In relational database terminology, this is referred to as a *one-to-many relationship*.</span></span> <span data-ttu-id="bbc3e-106">不過，有時候單一事實可聯結到多個維度成員。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-106">However, sometimes a single fact can join to multiple dimension members.</span></span> <span data-ttu-id="bbc3e-107">在關聯式資料庫詞彙中，這稱為「多對多關聯性」\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-107">In relational database terminology, this is referred to as a *many-to-many relationship*.</span></span> <span data-ttu-id="bbc3e-108">例如，客戶進行採購有許多原因，而採購原因可能與多個採購相關聯。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-108">For example, a customer may have multiple reasons for making a purchase, and a purchase reason can be associated with multiple purchases.</span></span> <span data-ttu-id="bbc3e-109">聯結資料表是用來定義與每項採購相關的銷售原因。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-109">A join table is used to define the sales reasons that relate to each purchase.</span></span> <span data-ttu-id="bbc3e-110">從這樣的關聯性建構的 [銷售原因] 維度會有多個成員與單一銷售交易有關。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-110">A Sales Reason dimension constructed from such relationships would then have multiple members that relate to a single sales transaction.</span></span> <span data-ttu-id="bbc3e-111">當維度與事實資料表無直接相關時，多對多維度會將維度模型可擴展到典型星形結構描述之外，來支援複雜分析。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-111">Many-to-many dimensions expand the dimensional model beyond the classic star schema and support complex analytics when dimensions are not directly related to a fact table.</span></span>

 <span data-ttu-id="bbc3e-112">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中，您會透過指定一個聯結到維度資料表的中繼事實資料表，在維度和量值群組之間定義多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-112">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you define a many-to-many relationship between a dimension and a measure group by specifying an intermediate fact table that is joined to the dimension table.</span></span> <span data-ttu-id="bbc3e-113">中繼事實資料表再聯結到該事實資料表所聯結的中繼維度資料表。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-113">An intermediate fact table is joined, in turn, to an intermediate dimension table to which the fact table is joined.</span></span> <span data-ttu-id="bbc3e-114">中繼事實資料表與關聯性中維度資料表之間的多對多關聯性，以及中繼事實資料表與中繼維度之間的多對多關聯性，會在主要維度成員與關聯性所指定之量值群組的量值之間建立多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-114">The many-to-many relationships between the intermediate fact table and both the dimension tables in the relationship and the intermediate dimension creates the many-to-many relationships between members of the primary dimension and measures in the measure group that is specified by the relationship.</span></span> <span data-ttu-id="bbc3e-115">若要透過中繼量值群組在維度與量值群組之間定義多對多關聯性，中繼量值群組必須和原始量值群組共用一或多個維度。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-115">In order to define a many-to-many relationship between a dimension and a measure group through an intermediate measure group, the intermediate measure group must share one or more dimensions with the original measure group.</span></span>

 <span data-ttu-id="bbc3e-116">多對多維度的值是相異加總，也就是說，這些值最多只會彙總一次到 [所有成員] 中。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-116">With a many-to-many dimension, values are distinct summed, which means that they do not aggregate more than once to the All member.</span></span>

> [!NOTE]
>  <span data-ttu-id="bbc3e-117">為了支援多對多維度關聯性，必須在所有相關資料表之間的資料來源視圖中定義主鍵-外鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-117">In order to support a many-to-many dimension relationship, a primary key-foreign key relationship must be defined in the data source view between all the tables that are involved.</span></span> <span data-ttu-id="bbc3e-118">否則，當您在 [Cube 設計師] 的 [維度使用方式]\*\*\*\* 索引標籤中建立關聯性時，將無法選取正確的中繼量值群組。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-118">Otherwise, you will not be able to select the correct intermediate measure group when you establish the relationship in the **Dimension Usage** tab of Cube Designer.</span></span>

 <span data-ttu-id="bbc3e-119">如需詳細資訊，請參閱 [維度關聯性](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)和 [定義多對多關聯性及多對多關聯性屬性](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md).</span></span>

 <span data-ttu-id="bbc3e-120">在這個主題的工作中，您會定義 [銷售原因] 維度和 [銷售原因] 量值群組，而且會在 [銷售原因] 維度和 [網際網路銷售] 量值群組之間透過 [銷售原因] 量值群組來定義多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-120">In the tasks in this topic, you define the Sales Reasons dimension and the Sales Reasons measure group, and you define a many-to-many relationship between the Sales Reasons dimension and the Internet Sales measure group through the Sales Reasons measure group.</span></span>

## <a name="adding-required-tables-to-the-data-source-view"></a><span data-ttu-id="bbc3e-121">將必要資料表加入資料來源檢視中</span><span class="sxs-lookup"><span data-stu-id="bbc3e-121">Adding Required Tables to the Data Source View</span></span>

1.  <span data-ttu-id="bbc3e-122">請針對 **Adventure Works DW 2012** 資料來源檢視，開啟資料來源檢視設計師。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-122">Open Data Source View Designer for the **Adventure Works DW 2012** data source view.</span></span>

2.  <span data-ttu-id="bbc3e-123">以滑鼠右鍵按一下 [**圖表召集人**] 窗格中的任何位置，然後按一下 [**新增圖表**]，並指定 `Internet Sales Order Reasons` 做為此新圖表的名稱。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-123">Right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**, and specify `Internet Sales Order Reasons` as the name for this new diagram.</span></span>

3.  <span data-ttu-id="bbc3e-124">將 [InternetSales]\*\*\*\* 資料表從 [資料表]\*\*\*\* 窗格拖曳至 [圖表]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-124">Drag the **InternetSales** table to the **Diagram** pane from the **Tables** pane.</span></span>

4.  <span data-ttu-id="bbc3e-125">以滑鼠右鍵按一下 [圖表]\*\*\*\* 窗格中的任何位置，然後按一下 [新增/移除資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-125">Right-click anywhere in the **Diagram** pane, and then click **Add/Remove Tables**.</span></span>

5.  <span data-ttu-id="bbc3e-126">在 [新增/移除資料表]\*\*\*\* 對話方塊中，將 [DimSalesReason]\*\*\*\* 資料表和 [FactInternetSalesReason]\*\*\*\* 資料表新增至 [包含的物件]\*\*\*\* 清單，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-126">In the **Add/Remove Tables** dialog box, add the **DimSalesReason** table and the **FactInternetSalesReason** table to the **Included objects** list, and then click **OK**.</span></span>

     <span data-ttu-id="bbc3e-127">請注意，相關資料表之間的主鍵-外鍵關聯性會自動建立，因為這些關聯性是在基礎關係資料庫中定義。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-127">Notice that the primary key-foreign key relationships between the tables that are involved are established automatically because those relationships are defined in the underlying relational database.</span></span> <span data-ttu-id="bbc3e-128">如果這些關聯性未定義在基礎關聯式資料庫中，您必須在資料來源檢視中定義它們。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-128">If these relationships were not defined in the underlying relational database, you would have to define them in the data source view.</span></span>

6.  <span data-ttu-id="bbc3e-129">在 [格式]\*\*\*\* 功能表上，指向 [自動配置]\*\*\*\*，然後按一下 [圖表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-129">On the **Format** menu, point to **Auto Layout**, and then click **Diagram**.</span></span>

7.  <span data-ttu-id="bbc3e-130">在 [屬性視窗中，將 [ **DimSalesReason** ] 資料表的 [ **friendlyname** ] 屬性變更為 `SalesReason` ，然後將 [ **FactInternetSalesReason** ] 資料表的 [ **friendlyname** ] 屬性變更為 `InternetSalesReason` 。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-130">In the Properties window, change the **FriendlyName** property of the **DimSalesReason** table to `SalesReason`, and then change the **FriendlyName** property of the **FactInternetSalesReason** table to `InternetSalesReason`.</span></span>

8.  <span data-ttu-id="bbc3e-131">在 [資料表]\*\*\*\* 窗格中，展開 [InternetSalesReason (dbo.FactInternetSalesReason)]\*\*\*\*，並按一下 [SalesOrderNumber]\*\*\*\*，然後在 [屬性] 視窗中檢閱這個資料行的 [DataType]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-131">In the **Tables** pane, expand **InternetSalesReason (dbo.FactInternetSalesReason)**, click **SalesOrderNumber**, and then review the **DataType** property for this data column in the Properties window.</span></span>

     <span data-ttu-id="bbc3e-132">請注意， **SalesOrderNumber** 資料行的資料類型是字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-132">Notice that the data type for the **SalesOrderNumber** column is a string data type.</span></span>

9. <span data-ttu-id="bbc3e-133">檢查資料表中其他資料行的資料類型 `InternetSalesReason` 。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-133">Review the data types for the other columns in the `InternetSalesReason` table.</span></span>

     <span data-ttu-id="bbc3e-134">請注意，這份資料表的其他兩個資料行的資料類型是數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-134">Notice that the data types for the other two columns in this table are numeric data types.</span></span>

10. <span data-ttu-id="bbc3e-135">在 [資料表]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [InternetSalesReason (dbo.FactInternetSalesReason)]\*\*\*\*，然後按一下 [瀏覽資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-135">In the **Tables** pane, right-click **InternetSalesReason (dbo.FactInternetSalesReason)**, and then click **Explore Data**.</span></span>

     <span data-ttu-id="bbc3e-136">請注意，每一份訂單內的每一個行號，都有一個索引鍵值來識別行項目的採構原因，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-136">Notice that, for each line number within each order, a key value identifies the sales reason for the purchase of that line item, as shown in the following image.</span></span>

     <span data-ttu-id="bbc3e-137">![識別購買之銷售原因的索引鍵值](../../2014/tutorials/media/l5-many-to-many-1.gif "識別購買之銷售原因的索引鍵值")</span><span class="sxs-lookup"><span data-stu-id="bbc3e-137">![Key value to identify sales reason for purchases](../../2014/tutorials/media/l5-many-to-many-1.gif "Key value to identify sales reason for purchases")</span></span>

## <a name="defining-the-intermediate-measure-group"></a><span data-ttu-id="bbc3e-138">定義中繼量值群組</span><span class="sxs-lookup"><span data-stu-id="bbc3e-138">Defining the Intermediate Measure Group</span></span>

1.  <span data-ttu-id="bbc3e-139">請針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師]，然後按一下 [Cube 結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-139">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Cube Structure** tab.</span></span>

2.  <span data-ttu-id="bbc3e-140">以滑鼠右鍵按一下 [量值]\*\*\*\* 窗格中的任何位置，然後按一下 [新增量值群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-140">Right-click anywhere in the **Measures** pane, and then click **New Measure Group**.</span></span> <span data-ttu-id="bbc3e-141">如需詳細資訊，請參閱 [在多維度模型中建立量值和量值群組](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-141">For more information, see [Create Measures and Measure Groups in Multidimensional Models](multidimensional-models/create-measures-and-measure-groups-in-multidimensional-models.md).</span></span>

3.  <span data-ttu-id="bbc3e-142">在 [**新增量值群組**] 對話方塊中，于 `InternetSalesReason` [**從資料來源視圖選取資料表**] 清單中選取，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-142">In the **New Measure Group** dialog box, select `InternetSalesReason` in the **Select a table from the data source view** list, and then click **OK**.</span></span>

     <span data-ttu-id="bbc3e-143">請注意，[網際網路銷售原因]\*\*\*\* 量值群組現在出現在 [量值]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-143">Notice that the **Internet Sales Reason** measure group now appears in the **Measures** pane.</span></span>

4.  <span data-ttu-id="bbc3e-144">展開 [網際網路銷售原因]\*\*\*\* 量值群組。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-144">Expand the **Internet Sales Reason** measure group.</span></span>

     <span data-ttu-id="bbc3e-145">請注意，對這個新量值群組只定義了單一量值，即 [網際網路銷售原因計數]\*\*\*\* 量值。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-145">Notice that only a single measure is defined for this new measure group, the **Internet Sales Reason Count** measure.</span></span>

5.  <span data-ttu-id="bbc3e-146">選取 [網際網路銷售原因計數]\*\*\*\*，並在 [屬性] 視窗中檢閱這個量值的屬性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-146">Select **Internet Sales Reason Count** and review the properties of this measure in the Properties window.</span></span>

     <span data-ttu-id="bbc3e-147">請注意，這個量值的 [AggregateFunction]\*\*\*\* 屬性是定義為 [計數]\*\*\*\* 而不是 [總和]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-147">Notice that the **AggregateFunction** property for this measure is defined as **Count** instead of **Sum**.</span></span> [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]<span data-ttu-id="bbc3e-148">選擇 [**計數**] 是因為基礎資料類型是字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-148">chose **Count** because the underlying data type is a string data type.</span></span> <span data-ttu-id="bbc3e-149">基礎事實資料表中的其他兩個資料行並未選取做為量值，因為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 偵測到它們是數值索引鍵而不是實際量值。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-149">The other two columns in the underlying fact table were not selected as measures because [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] detected them as numeric keys instead of as actual measures.</span></span> <span data-ttu-id="bbc3e-150">如需詳細資訊，請參閱 [定義局部加總行為](multidimensional-models/define-semiadditive-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-150">For more information, see [Define Semiadditive Behavior](multidimensional-models/define-semiadditive-behavior.md).</span></span>

6.  <span data-ttu-id="bbc3e-151">在 [屬性] 視窗中，將 [網際網路銷售原因計數]\*\*\*\* 量值的 [可見]\*\*\*\* 屬性變更為 **False**。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-151">In the Properties window, change the **Visible** property of the **Internet Sales Reason Count** measure to **False**.</span></span>

     <span data-ttu-id="bbc3e-152">這個量值的唯一作用是將您接下來要定義的 [銷售原因] 維度聯結到 [網際網路銷售] 量值群組。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-152">This measure will only be used to join the Sales Reason dimension that you will define next to the Internet Sales measure group.</span></span> <span data-ttu-id="bbc3e-153">使用者不會直接瀏覽這個量值。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-153">Users will not browse this measure directly.</span></span>

     <span data-ttu-id="bbc3e-154">下圖顯示 [網際網路銷售原因計數]\*\*\*\* 量值的屬性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-154">The following image shows the properties for the **Internet Sales Reason Count** measure.</span></span>

     <span data-ttu-id="bbc3e-155">![網際網路銷售原因計數量值的屬性](../../2014/tutorials/media/l5-many-to-many-2.gif "網際網路銷售原因計數量值的屬性")</span><span class="sxs-lookup"><span data-stu-id="bbc3e-155">![Properties for Internet Sales Reason Count measure](../../2014/tutorials/media/l5-many-to-many-2.gif "Properties for Internet Sales Reason Count measure")</span></span>

## <a name="defining-the-many-to-many-dimension"></a><span data-ttu-id="bbc3e-156">定義多對多維度</span><span class="sxs-lookup"><span data-stu-id="bbc3e-156">Defining the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="bbc3e-157">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 [維度]\*\*\*\*，然後按一下 [新增維度]。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-157">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="bbc3e-158">在 [歡迎使用維度精靈]\*\*\*\* 頁面上，按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-158">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="bbc3e-159">在 [選取建立方法]\*\*\*\* 頁面上，確認已選取 [使用現有的資料表]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-159">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="bbc3e-160">在 [指定來源資訊]\*\*\*\* 頁面上，確認已選取 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-160">On the **Specify Source Information** page, verify that the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012 data source view is selected.</span></span>

5.  <span data-ttu-id="bbc3e-161">在 [**主資料表**] 清單中，選取 [] `SalesReason` 。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-161">In the **Main table** list, select `SalesReason`.</span></span>

6.  <span data-ttu-id="bbc3e-162">在 [索引鍵資料行]\*\*\*\* 清單中，確認已列出 [SalesReasonKey]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-162">In the **Key columns** list, verify that **SalesReasonKey** is listed.</span></span>

7.  <span data-ttu-id="bbc3e-163">在 [名稱資料行]\*\*\*\* 清單中，選取 [SalesReasonName]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-163">In the **Name column** list, select **SalesReasonName**.</span></span>

8.  <span data-ttu-id="bbc3e-164">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-164">Click **Next**.</span></span>

9. <span data-ttu-id="bbc3e-165">在 [選取維度屬性]\*\*\*\* 頁面上，系統會自動選取 [銷售原因索引鍵]\*\*\*\* 屬性，因為它是索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-165">On the **Select Dimension Attributes** page, the **Sales Reason Key** attribute is automatically selected because it is the key attribute.</span></span> <span data-ttu-id="bbc3e-166">選取 [**銷售原因類型**] 屬性旁的核取方塊，將其名稱變更為 `Sales Reason Type` ，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-166">Select the check box beside the **Sales Reason Reason Type** attribute, change its name to `Sales Reason Type`, and then click **Next**.</span></span>

10. <span data-ttu-id="bbc3e-167">在 [正在完成精靈]\*\*\*\* 頁面上，按一下 [完成]\*\*\*\* 建立 [銷售原因] 維度。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-167">On the **Completing the Wizard** page, click **Finish** to create the Sales Reason dimension.</span></span>

11. <span data-ttu-id="bbc3e-168">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-168">On the **File** menu, click **Save All**.</span></span>

12. <span data-ttu-id="bbc3e-169">在 [**銷售原因**] 維度之 [維度設計師] 的 [**屬性**] 窗格中，選取 [**銷售原因索引鍵**]，然後將屬性視窗中的 [**名稱**] 屬性變更為`Sales Reason.`</span><span class="sxs-lookup"><span data-stu-id="bbc3e-169">In the **Attributes** pane of the Dimension Designer for the **Sales Reason** dimension, select **Sales Reason Key**, and then change the **Name** property in the Properties window to `Sales Reason.`</span></span>

13. <span data-ttu-id="bbc3e-170">在 [維度**設計師] 的**[階層] 窗格中，依該順序建立包含 [層級] 和 [銷售原因] 層級的 [**銷售原因**] 使用者階層 `Sales Reason Type` 。 **Sales Reason**</span><span class="sxs-lookup"><span data-stu-id="bbc3e-170">In the **Hierarchies** pane of the Dimension Designer, create a **Sales Reasons** user hierarchy that contains the `Sales Reason Type` level and the **Sales Reason** level, in that order.</span></span>

14. <span data-ttu-id="bbc3e-171">在屬性視窗中， `All Sales Reasons` 將定義為 [銷售原因] 階層的 [ **AllMemberName** ] 屬性值。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-171">In the Properties window, define `All Sales Reasons` as the value for the **AllMemberName** property of the Sales Reasons hierarchy.</span></span>

15. <span data-ttu-id="bbc3e-172">`All Sales Reasons`將定義為 [銷售原因] 維度的 [ **AttributeAllMemberName** ] 屬性值。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-172">Define `All Sales Reasons` as the value for **AttributeAllMemberName** property of the Sales Reason dimension.</span></span>

16. <span data-ttu-id="bbc3e-173">若要將新建立的維度新增至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 當成 Cube 維度，請切換至 [Cube 設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-173">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="bbc3e-174">在 [Cube 結構]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下 [維度]\*\*\*\* 窗格，然後選取 [新增 Cube 維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-174">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

17. <span data-ttu-id="bbc3e-175">在 [新增 Cube 維度]\*\*\*\* 對話方塊中，選取 [銷售原因]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-175">In the **Add Cube Dimension** dialog box, select **Sales Reason** and then click **OK**.</span></span>

18. <span data-ttu-id="bbc3e-176">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-176">On the **File** menu, click **Save All**.</span></span>

## <a name="defining-the-many-to-many-relationship"></a><span data-ttu-id="bbc3e-177">定義多對多關聯性</span><span class="sxs-lookup"><span data-stu-id="bbc3e-177">Defining the Many to Many Relationship</span></span>

1.  <span data-ttu-id="bbc3e-178">請針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師]，然後按一下 [維度使用方式]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-178">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="bbc3e-179">請注意，[銷售原因]\*\*\*\* 維度與 [網際網路銷售原因]\*\*\*\* 量值群組之間有定義一般關聯性，但是與 [網際網路銷售]\*\*\*\* 或 [轉售商銷售]\*\*\*\* 量值群組之間則沒有定義任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-179">Notice that the **Sales Reason** dimension has a regular relationship defined with the **Internet Sales Reason** measure group, but has no relationship defined with the **Internet Sales** or **Reseller Sales** measure groups.</span></span> <span data-ttu-id="bbc3e-180">也請注意，[網際網路銷售訂單的詳細資料]\*\*\*\* 維度與 [網際網路銷售原因]\*\*\*\* 維度之間有定義一般關聯性，而後者又與 [網際網路銷售]\*\*\*\* 量值群組具有「事實關聯性」\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-180">Notice also that the **Internet Sales Order Details** dimension has a regular relationship defined with the **Internet Sales Reason** dimension, which in turn has a **Fact Relationship** with the **Internet Sales** measure group.</span></span> <span data-ttu-id="bbc3e-181">如果這個維度不存在 (或是另一個同時與 [網際網路銷售原因]\*\*\*\* 和 [網際網路銷售]\*\*\*\* 量值群組具有關聯性的維度不存在)，您就無法定義多對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-181">If this dimension was not present (or another dimension with a relationship with both the **Internet Sales Reason** and the **Internet Sales** measure group were not present), you would not be able to define the many-to-many relationship.</span></span>

2.  <span data-ttu-id="bbc3e-182">在 [網際網路銷售]\*\*\*\* 量值群組和 [銷售原因]\*\*\*\* 維度的交集處，按一下資料格，然後按一下瀏覽按鈕 (**…**)。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-182">Click the cell at the intersection of the **Internet Sales** measure group and the **Sales Reason** dimension and then click the browse button (**...**).</span></span>

3.  <span data-ttu-id="bbc3e-183">在 [定義關聯性]\*\*\*\* 對話方塊中，選取 [選取關聯性類型]\*\*\*\* 清單中的 [多對多]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-183">In the **Define Relationship** dialog box, select **Many-to-Many** in the **Select relationship type** list.</span></span>

     <span data-ttu-id="bbc3e-184">您必須定義連接 [銷售原因] 維度與 [網際網路銷售] 量值群組的中繼量值群組。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-184">You have to define the intermediate measure group that connects the Sales Reason dimension to the Internet Sales measure group.</span></span>

4.  <span data-ttu-id="bbc3e-185">在 [中繼量值群組]\*\*\*\* 清單中，選取 [網際網路銷售原因]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-185">In the **Intermediate measure group** list, select **Internet Sales Reason**.</span></span>

     <span data-ttu-id="bbc3e-186">下圖顯示 [定義關聯性]\*\*\*\* 對話方塊中的變更。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-186">The following image shows the changes in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="bbc3e-187">![[定義關聯性] 對話方塊](../../2014/tutorials/media/l5-many-to-many-3.gif "定義關聯性對話方塊")</span><span class="sxs-lookup"><span data-stu-id="bbc3e-187">![Define Relationship dialog box](../../2014/tutorials/media/l5-many-to-many-3.gif "Define Relationship dialog box")</span></span>

5.  <span data-ttu-id="bbc3e-188">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-188">Click **OK**.</span></span>

     <span data-ttu-id="bbc3e-189">請注意代表 [銷售原因] 維度和 [網際網路銷售] 量值群組之間關聯性的多對多圖示。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-189">Notice the many-to-many icon that represents the relationship between the Sales Reason dimension and the Internet Sales measure group.</span></span>

## <a name="browsing-the-cube-and-the-many-to-many-dimension"></a><span data-ttu-id="bbc3e-190">瀏覽 Cube 與多對多維度</span><span class="sxs-lookup"><span data-stu-id="bbc3e-190">Browsing the Cube and the Many-to-Many Dimension</span></span>

1.  <span data-ttu-id="bbc3e-191">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-191">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="bbc3e-192">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，切換到 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-192">When deployment has successfully completed, switch to the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="bbc3e-193">將 [網際網路銷售 - 銷售量]\*\*\*\* 量值新增至 [資料] 窗格的資料區域。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-193">Add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="bbc3e-194">將 [銷售原因]\*\*\*\* 維度中的 [銷售原因]\*\*\*\* 使用者定義階層新增至 [資料] 窗格的資料列區域。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-194">Add the **Sales Reasons** user-defined hierarchy from the **Sales Reason** dimension to the row area of the data pane.</span></span>

5.  <span data-ttu-id="bbc3e-195">在 [中繼資料] 窗格中，依序展開 [客戶]\*\*\*\*、[位置]\*\*\*\*、[客戶地理位置]\*\*\*\*、[成員]\*\*\*\*、[所有客戶]\*\*\*\* 和 [澳大利亞]\*\*\*\*，並以滑鼠右鍵按一下 [昆士蘭]\*\*\*\*，然後按一下 [新增至篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-195">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, right-click **Queensland**, and then click **Add to Filter**.</span></span>

6.  <span data-ttu-id="bbc3e-196">展開層級的每個成員 `Sales Reason Type` ，以檢查與昆士蘭客戶在網際網路上購買產品的每個原因相關聯的貨幣值 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-196">Expand each member of the `Sales Reason Type` level to review the dollar values that are associated with each reason a customer in Queensland gave for their purchase of an [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] product over the Internet.</span></span>

     <span data-ttu-id="bbc3e-197">請注意，與每一個銷售原因有關聯的總計累加超過總銷售量。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-197">Notice that the totals that are associated with each sales reason add up to more than the total sales.</span></span> <span data-ttu-id="bbc3e-198">這是因為有些客戶針對其採購引用了多個原因。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-198">This is because some customers cited multiple reasons for their purchase.</span></span>

     <span data-ttu-id="bbc3e-199">下圖顯示 [Cube 設計師] 的 [篩選]\*\*\*\* 窗格和 [資料]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="bbc3e-199">The following image shows the **Filter** pane and **Data** pane of Cube Designer.</span></span>

     <span data-ttu-id="bbc3e-200">![Cube 設計師的篩選和資料窗格](../../2014/tutorials/media/l5-many-to-many-5.gif "Cube 設計師的篩選和資料窗格")</span><span class="sxs-lookup"><span data-stu-id="bbc3e-200">![Filter and Data panes of Cube Designer](../../2014/tutorials/media/l5-many-to-many-5.gif "Filter and Data panes of Cube Designer")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="bbc3e-201">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="bbc3e-201">Next Task in Lesson</span></span>
 [<span data-ttu-id="bbc3e-202">在量值群組內定義維度資料粒度</span><span class="sxs-lookup"><span data-stu-id="bbc3e-202">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)

## <a name="see-also"></a><span data-ttu-id="bbc3e-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbc3e-203">See Also</span></span>
 <span data-ttu-id="bbc3e-204">[在資料來源視圖設計工具中使用圖表 &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [維度關聯](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)性[定義多對多關聯性及多對多關聯性屬性](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="bbc3e-204">[Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;](multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md) [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Many-to-Many Relationship and Many-to-Many Relationship Properties](multidimensional-models/define-a-many-to-many-relationship-and-many-to-many-relationship-properties.md)</span></span>


