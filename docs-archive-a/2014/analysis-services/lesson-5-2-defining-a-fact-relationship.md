---
title: 定義事實關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4b49a078-6848-4286-bc71-cf4862d29064
author: minewiskan
ms.author: owend
ms.openlocfilehash: 26f8068301c424d5aea9f54e882ceb8a4dc72806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606462"
---
# <a name="defining-a-fact-relationship"></a><span data-ttu-id="49be7-102">定義事實關聯性</span><span class="sxs-lookup"><span data-stu-id="49be7-102">Defining a Fact Relationship</span></span>
  <span data-ttu-id="49be7-103">使用者有時候想要按事實資料表中的資料項目建立量值維度，或查詢事實資料表中的其他特定相關資訊，例如與特定銷售事實相關的發票號碼或訂單號碼。</span><span class="sxs-lookup"><span data-stu-id="49be7-103">Users sometimes want to be able to dimension measures by data items that are in the fact table or to query the fact table for specific additional related information, such as invoice numbers or purchase order numbers related to specific sales facts.</span></span> <span data-ttu-id="49be7-104">當您依據這樣的事實資料表項目來定義維度時，這種維度稱為「事實維度」\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-104">When you define a dimension based on such a fact table item, the dimension is called a *fact dimension*.</span></span> <span data-ttu-id="49be7-105">事實維度也稱為變質維度。</span><span class="sxs-lookup"><span data-stu-id="49be7-105">Fact dimensions are also known as degenerate dimensions.</span></span> <span data-ttu-id="49be7-106">事實維度對於將相關事實資料表資料列 (例如，與特定發票號碼相關的所有資料列) 分組很有幫助。</span><span class="sxs-lookup"><span data-stu-id="49be7-106">Fact dimensions are useful for grouping together related fact table rows, such as all the rows that are related to a particular invoice number.</span></span> <span data-ttu-id="49be7-107">雖然您可以將這項資訊放在關聯式資料庫的個別維度資料表中，但為這項資訊建立個別的維度資料表並無好處，因為維度資料表與事實資料表的成長速率一樣，只會建立重複資料和產生不必要的複雜性而已。</span><span class="sxs-lookup"><span data-stu-id="49be7-107">Although you can put this information in a separate dimension table in the relational database, creating a separate dimension table for the information provides no benefit because the dimension table would grow at the same rate as the fact table, and would just create duplicate data and unnecessary complexity.</span></span>

 <span data-ttu-id="49be7-108">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]中，您可以決定是否要在 MOLAP 維度結構中重複事實維度資料來增加查詢效能，或是否要將事實維度定義成 ROLAP 維度，以犧牲查詢效能的代價來節省儲存空間。</span><span class="sxs-lookup"><span data-stu-id="49be7-108">Within [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can determine whether to duplicate the fact dimension data in a MOLAP dimension structure for increased query performance, or whether to define the fact dimension as a ROLAP dimension to save storage space at the expense of query performance.</span></span> <span data-ttu-id="49be7-109">當您以 MOLAP 儲存模式來儲存維度時，所有維度成員除了儲存在量值群組的資料分割外，還會以高度壓縮的 MOLAP 結構而儲存在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="49be7-109">When you store a dimension with the MOLAP storage mode, all the dimension members are stored in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in a highly compressed MOLAP structure, in addition to being stored in the measure group's partitions.</span></span> <span data-ttu-id="49be7-110">當您使用 ROLAP 儲存模式來儲存維度時，只有維度定義會儲存在 MOLAP 結構中，在查詢時，維度成員本身會從基礎關聯式事實資料表中進行查詢。</span><span class="sxs-lookup"><span data-stu-id="49be7-110">When you store a dimension with the ROLAP storage mode, only the dimension definition is stored in the MOLAP structure-the dimension members themselves are queried from the underlying relational fact table at query time.</span></span> <span data-ttu-id="49be7-111">您可以依據事實維度查詢的頻率、一般查詢傳回的資料列數、查詢的效能和處理成本，來決定適當的儲存模式。</span><span class="sxs-lookup"><span data-stu-id="49be7-111">You decide the appropriate storage mode based on how frequently the fact dimension is queried, the number of rows returned by a typical query, the performance of the query, and the processing cost.</span></span> <span data-ttu-id="49be7-112">將維度定義為 ROLAP 並不需要所有使用該維度的 Cube 都以 ROLAP 儲存模式來儲存。</span><span class="sxs-lookup"><span data-stu-id="49be7-112">Defining a dimension as ROLAP does not require that all cubes that use the dimension also be stored with the ROLAP storage mode.</span></span> <span data-ttu-id="49be7-113">每個維度的儲存模式可獨立設定。</span><span class="sxs-lookup"><span data-stu-id="49be7-113">The storage mode for each dimension can be configured independently.</span></span>

 <span data-ttu-id="49be7-114">當您定義事實維度時，可在事實維度和量值群組之間定義事實關聯性。</span><span class="sxs-lookup"><span data-stu-id="49be7-114">When you define a fact dimension, you can define the relationship between the fact dimension and the measure group as a fact relationship.</span></span> <span data-ttu-id="49be7-115">下列條件約束適用於事實關聯性：</span><span class="sxs-lookup"><span data-stu-id="49be7-115">The following constraints apply to fact relationships:</span></span>

-   <span data-ttu-id="49be7-116">資料粒度屬性必須是維度的索引鍵資料行，它會在維度和事實資料表的事實之間建立一對一關聯性。</span><span class="sxs-lookup"><span data-stu-id="49be7-116">The granularity attribute must be the key column for the dimension, which creates a one-to-one relationship between the dimension and the facts in the fact table.</span></span>

-   <span data-ttu-id="49be7-117">維度只能與單一量值群組之間有事實關聯性。</span><span class="sxs-lookup"><span data-stu-id="49be7-117">A dimension can have a fact relationship with only a single measure group.</span></span>

> [!NOTE]
>  <span data-ttu-id="49be7-118">另外，事實維度在每次更新到事實關聯性參考的量值群組之後必須累加更新。</span><span class="sxs-lookup"><span data-stu-id="49be7-118">Fact dimensions must be incrementally updated after every update to the measure group that the fact relationship references.</span></span>

 <span data-ttu-id="49be7-119">如需詳細資訊，請參閱 [維度關聯性](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)和 [定義事實關聯性及事實關聯性屬性](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="49be7-119">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), and [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md).</span></span>

 <span data-ttu-id="49be7-120">在本主題的工作中，您會依據 [FactInternetSales]\*\*\*\* 事實資料表中的 [CustomerPONumber]\*\*\*\* 資料行來加入新的 Cube 維度。</span><span class="sxs-lookup"><span data-stu-id="49be7-120">In the tasks in this topic, you add a new cube dimension based on the **CustomerPONumber** column in the **FactInternetSales** fact table.</span></span> <span data-ttu-id="49be7-121">接著會將這個新的 Cube 維度和 [網際網路銷售]\*\*\*\* 量值群組之間的關聯性定義為事實關聯性。</span><span class="sxs-lookup"><span data-stu-id="49be7-121">You then define the relationship between this new cube dimension and the **Internet Sales** measure group as a fact relationship.</span></span>

## <a name="defining-the-internet-sales-orders-fact-dimension"></a><span data-ttu-id="49be7-122">定義網際網路銷售訂單事實維度</span><span class="sxs-lookup"><span data-stu-id="49be7-122">Defining the Internet Sales Orders Fact Dimension</span></span>

1.  <span data-ttu-id="49be7-123">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 [維度]\*\*\*\*，然後按一下 [新增維度]。</span><span class="sxs-lookup"><span data-stu-id="49be7-123">In Solution Explorer, right-click **Dimensions**, and then click **New Dimension**.</span></span>

2.  <span data-ttu-id="49be7-124">在 [歡迎使用維度精靈]\*\*\*\* 頁面上，按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-124">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>

3.  <span data-ttu-id="49be7-125">在 [選取建立方法]\*\*\*\* 頁面上，確認已選取 [使用現有的資料表]\*\*\*\* 選項，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-125">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>

4.  <span data-ttu-id="49be7-126">在 [指定來源資訊]\*\*\*\* 頁面上，確認已選取 **Adventure Works DW 2012** 資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="49be7-126">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>

5.  <span data-ttu-id="49be7-127">在 [主資料表]\*\*\*\* 清單中，選取 [InternetSales]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-127">In the **Main table** list, select **InternetSales**.</span></span>

6.  <span data-ttu-id="49be7-128">在 [索引鍵資料行]\*\*\*\* 清單中，確認已列出 [SalesOrderNumber]\*\*\*\* 和 [SalesOrderLineNumber]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-128">In the **Key columns** list, verify that **SalesOrderNumber** and **SalesOrderLineNumber** are listed.</span></span>

7.  <span data-ttu-id="49be7-129">在 [名稱資料行]\*\*\*\* 清單中，選取 [SalesOrderLineNumber]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-129">In the **Name column** list, select **SalesOrderLineNumber**.</span></span>

8.  <span data-ttu-id="49be7-130">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="49be7-130">Click **Next**.</span></span>

9. <span data-ttu-id="49be7-131">在 [選取相關資料表]\*\*\*\* 頁面上，清除所有資料表旁的核取方塊，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-131">On the **Select Related Tables** page, clear the check boxes beside all of the tables, and then click **Next**.</span></span>

10. <span data-ttu-id="49be7-132">在 [選取維度屬性]\*\*\*\* 頁面上，按兩次標頭中的核取方塊，以便清除所有核取方塊。</span><span class="sxs-lookup"><span data-stu-id="49be7-132">On the **Select Dimension Attributes** page, click the check box in the header twice to clear all of the check boxes.</span></span> <span data-ttu-id="49be7-133">[銷售訂單號碼]\*\*\*\* 屬性會維持選取狀態，因為它是索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="49be7-133">The **Sales Order Number** attribute will remain selected because it is the key attribute.</span></span>

11. <span data-ttu-id="49be7-134">選取 [客戶採購單號碼]\*\*\*\* 屬性，然後按一下 [下一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-134">Select the **Customer PO Number** attribute, and then click **Next**.</span></span>

12. <span data-ttu-id="49be7-135">在 [正在完成精靈]\*\*\*\* 頁面上，將名稱變更為 [網際網路銷售訂單的詳細資料]\*\*\*\*，然後按一下 [完成]\*\*\*\* 完成精靈。</span><span class="sxs-lookup"><span data-stu-id="49be7-135">On the **Completing the Wizard** page, change the name to **Internet Sales Order Details** and then click **Finish** to complete the wizard.</span></span>

13. <span data-ttu-id="49be7-136">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="49be7-136">On the **File** menu, click **Save All**.</span></span>

14. <span data-ttu-id="49be7-137">在 [**網際網路銷售訂單詳細資料**] 維度之 [維度設計師] 的 [**屬性**] 窗格中，選取 [**銷售訂單號碼**]，然後將屬性視窗中的 [**名稱**] 屬性變更為`Item Description.`</span><span class="sxs-lookup"><span data-stu-id="49be7-137">In the **Attributes** pane of the Dimension Designer for the **Internet Sales Order Details** dimension, select **Sales Order Number**, and then change the **Name** property in the Properties window to `Item Description.`</span></span>

15. <span data-ttu-id="49be7-138">在 [ **NameColumn** ] 屬性資料格中，按一下 [流覽] 按鈕\*\* ( ...] ) **。在 [**名稱資料行**] 對話方塊中，從 [**來源資料表**] 清單中選取 [**產品**]，針對 [**來源\*\*] 資料行選取 [ **product.englishproductname** ]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="49be7-138">In the **NameColumn** property cell, click the browse button **(...)**. In the **Name Column** dialog box, select **Product** from the **Source table** list, select **EnglishProductName** for the **Source column**, and then click **OK**.</span></span>

16. <span data-ttu-id="49be7-139">將 [SalesOrderNumber]\*\*\*\* 資料行從 [資料來源檢視]\*\*\*\* 窗格中的 [InternetSales]\*\*\*\* 資料表拖曳到 [屬性]\*\*\*\* 窗格，以這個方式將 [銷售訂單號碼]\*\*\*\* 屬性加入維度。</span><span class="sxs-lookup"><span data-stu-id="49be7-139">Add the **Sales Order Number** attribute to the dimension by dragging the **SalesOrderNumber** column from the **InternetSales** table in the **Data Source View** pane to the **Attributes** pane.</span></span>

17. <span data-ttu-id="49be7-140">將 [新**銷售訂單號碼**] 屬性的 [**名稱**] 屬性變更為 `Order Number` ，並將 [ **OrderBy** ] 屬性變更為 [索引**鍵**]。</span><span class="sxs-lookup"><span data-stu-id="49be7-140">Change the **Name** property of the new **Sales Order Number** attribute to `Order Number`, and change the **OrderBy** property to **Key**.</span></span>

18. <span data-ttu-id="49be7-141">在 [**階層**] 窗格中，依序建立 [**網際網路銷售訂單**] 使用者階層，其中包含 `Order Number` 和**專案描述**層級。</span><span class="sxs-lookup"><span data-stu-id="49be7-141">In the **Hierarchies** pane, create an **Internet Sales Orders** user hierarchy that contains the `Order Number` and **Item Description** levels, in that order.</span></span>

19. <span data-ttu-id="49be7-142">在 [屬性]\*\*\*\* 窗格，選取 [網際網路銷售訂單的詳細資料]\*\*\*\*，然後在 [屬性] 視窗中檢閱 [StorageMode]\*\*\*\* 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="49be7-142">In the **Attributes** pane, select **Internet Sales Order Details**, and then review the value for the **StorageMode** property in the Properties window.</span></span>

     <span data-ttu-id="49be7-143">請注意，依預設，這個維度是儲存為 MOLAP 維度。</span><span class="sxs-lookup"><span data-stu-id="49be7-143">Notice that, by default, this dimension is stored as a MOLAP dimension.</span></span> <span data-ttu-id="49be7-144">雖然將儲存模式變更為 ROLAP 可節省處理時間和儲存空間，但卻是以犧牲查詢效能為代價。</span><span class="sxs-lookup"><span data-stu-id="49be7-144">Although changing the storage mode to ROLAP will save processing time and storage space, it occurs at the expense of query performance.</span></span> <span data-ttu-id="49be7-145">基於這個教學課程的目的，您將使用 MOLAP 做為儲存模式。</span><span class="sxs-lookup"><span data-stu-id="49be7-145">For the purposes of this tutorial, you will use MOLAP as the storage mode.</span></span>

20. <span data-ttu-id="49be7-146">若要將新建立的維度新增至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 當成 Cube 維度，請切換至 [Cube 設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-146">To add the newly created dimension to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube as a cube dimension, switch to **Cube Designer**.</span></span> <span data-ttu-id="49be7-147">在 [Cube 結構]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下 [維度]\*\*\*\* 窗格，然後選取 [新增 Cube 維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-147">On the **Cube Structure** tab, right-click in the **Dimensions** pane and select **Add Cube Dimension**.</span></span>

21. <span data-ttu-id="49be7-148">在 [加入 Cube 維度]\*\*\*\* 對話方塊中，選取 [網際網路銷售訂單的詳細資料]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-148">In the **Add Cube Dimension**.dialog box, select **Internet Sales Order Details** and then click **OK**.</span></span>

## <a name="defining-a-fact-relationship-for-the-fact-dimension"></a><span data-ttu-id="49be7-149">定義 Fact 維度的事實關聯性</span><span class="sxs-lookup"><span data-stu-id="49be7-149">Defining a Fact Relationship for the Fact Dimension</span></span>

1.  <span data-ttu-id="49be7-150">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 的 [Cube 設計師] 中，按一下 [維度使用方式]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="49be7-150">In the Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="49be7-151">請注意，[網際網路銷售訂單的詳細資料]\*\*\*\* Cube 維度會自動設定為具有事實關聯性，正如其唯一圖示所示。</span><span class="sxs-lookup"><span data-stu-id="49be7-151">Notice that the **Internet Sales Order Details** cube dimension is automatically configured as having a fact relationship, as shown by the unique icon.</span></span>

2.  <span data-ttu-id="49be7-152">在 [**網際網路銷售**] 量值群組和 [**網際網路銷售訂單詳細資料**] 維度的交集處，按一下 [**專案描述**] 儲存格中的 [流覽]**按鈕 (]**) ，以檢查事實關聯性屬性。</span><span class="sxs-lookup"><span data-stu-id="49be7-152">Click the browse button (**...**) in the **Item Description** cell, at the intersection of the **Internet Sales** measure group and the **Internet Sales Order Details** dimension, to review the fact relationship properties.</span></span>

     <span data-ttu-id="49be7-153">此時會開啟 [定義關聯性]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="49be7-153">The **Define Relationship** dialog box opens.</span></span> <span data-ttu-id="49be7-154">請注意，您不能設定任何這些屬性。</span><span class="sxs-lookup"><span data-stu-id="49be7-154">Notice that you cannot configure any of the properties.</span></span>

     <span data-ttu-id="49be7-155">下圖顯示 [定義關聯性]\*\*\*\* 對話方塊中的事實關聯性屬性。</span><span class="sxs-lookup"><span data-stu-id="49be7-155">The following image shows the fact relationship properties in the **Define Relationship** dialog box.</span></span>

     <span data-ttu-id="49be7-156">![[定義關聯性] 對話方塊](../../2014/tutorials/media/l5-factrelationship-2.gif "定義關聯性對話方塊")</span><span class="sxs-lookup"><span data-stu-id="49be7-156">![Define Relationship dialog box](../../2014/tutorials/media/l5-factrelationship-2.gif "Define Relationship dialog box")</span></span>

3.  <span data-ttu-id="49be7-157">按一下 [取消]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-157">Click **Cancel**.</span></span>

## <a name="browsing-the-cube-by-using-the-fact-dimension"></a><span data-ttu-id="49be7-158">使用 Fact 維度來瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="49be7-158">Browsing the Cube by Using the Fact Dimension</span></span>

1.  <span data-ttu-id="49be7-159">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*，將所做的變更部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的執行個體及處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="49be7-159">On the **Build** menu, click **Deploy Analysis Services Tutorial** to deploy the changes to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and process the database.</span></span>

2.  <span data-ttu-id="49be7-160">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，按一下 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="49be7-160">After deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="49be7-161">從 [資料] 窗格中清除所有量值和階層，然後將 [網際網路銷售 - 銷售量]\*\*\*\* 量值加入 [資料] 窗格的資料區域。</span><span class="sxs-lookup"><span data-stu-id="49be7-161">Clear all measures and hierarchies from the data pane, and then add the **Internet Sales-Sales Amount** measure to the data area of the data pane.</span></span>

4.  <span data-ttu-id="49be7-162">在 [中繼資料] 窗格中，依序展開 [客戶]\*\*\*\*、[位置]\*\*\*\*、[客戶地理位置]\*\*\*\*、[成員]\*\*\*\*、[所有客戶]\*\*\*\*、[澳大利亞]\*\*\*\*、[昆士蘭]\*\*\*\*、[布里斯本]\*\*\*\*、[4000]\*\*\*\*，以滑鼠右鍵按一下 [Adam Powell]\*\*\*\*，然後按一下 [加入至篩選]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="49be7-162">In the metadata pane, expand **Customer**, expand **Location**, expand **Customer Geography**, expand **Members**, expand **All Customers**, expand **Australia**, expand **Queensland**, expand **Brisbane**, expand **4000**, right-click **Adam Powell**, and then click **Add to Filter**.</span></span>

     <span data-ttu-id="49be7-163">以篩選方式限制傳回給單一客戶的銷售訂單，可讓使用者向下鑽研大型事實資料表的基礎詳細資料，而不致使查詢效能有重大損失。</span><span class="sxs-lookup"><span data-stu-id="49be7-163">Filtering to limit the sales orders returned to a single customer lets the user drill down to the underlying detail in a large fact table without suffering a significant loss in query performance.</span></span>

5.  <span data-ttu-id="49be7-164">將 [網際網路銷售訂單的詳細資料]\*\*\*\* 維度中的 [網際網路銷售訂單]\*\*\*\* 使用者定義階層加入 [資料] 窗格的資料列區域。</span><span class="sxs-lookup"><span data-stu-id="49be7-164">Add the **Internet Sales Orders** user-defined hierarchy from the **Internet Sales Order Details** dimension to the row area of the data pane.</span></span>

     <span data-ttu-id="49be7-165">請注意，銷售訂單號碼和 Adam Powell 對應的網際網路銷售量會出現在 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="49be7-165">Notice that the sales order numbers and the corresponding Internet sales amounts for Adam Powell appear in the data pane.</span></span>

     <span data-ttu-id="49be7-166">下圖顯示先前步驟所產生的結果。</span><span class="sxs-lookup"><span data-stu-id="49be7-166">The following image shows the result of the previous steps.</span></span>

     <span data-ttu-id="49be7-167">![網際網路銷售額-銷售額的維度](../../2014/tutorials/media/l5-factrelationship-3.gif "網際網路銷售額-銷售額的維度")</span><span class="sxs-lookup"><span data-stu-id="49be7-167">![Dimensioning of Internet Sales-Sales Amount](../../2014/tutorials/media/l5-factrelationship-3.gif "Dimensioning of Internet Sales-Sales Amount")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="49be7-168">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="49be7-168">Next Task in Lesson</span></span>
 [<span data-ttu-id="49be7-169">定義多對多關聯性</span><span class="sxs-lookup"><span data-stu-id="49be7-169">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)

## <a name="see-also"></a><span data-ttu-id="49be7-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49be7-170">See Also</span></span>
 <span data-ttu-id="49be7-171">[維度關聯](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)性[定義事實關聯性和事實關聯性屬性](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="49be7-171">[Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md) [Define a Fact Relationship and Fact Relationship Properties](multidimensional-models/define-a-fact-relationship-and-fact-relationship-properties.md)</span></span>


