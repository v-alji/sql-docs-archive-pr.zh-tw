---
title: 定義未知的成員和 Null 處理屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d9abb09c-9bfa-4e32-b530-8590e4383566
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdd6504bec4f129f64d9bef6f6b0138e917888e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594816"
---
# <a name="defining-the-unknown-member-and-null-processing-properties"></a><span data-ttu-id="de7e5-102">定義未知的成員和 Null 處理屬性</span><span class="sxs-lookup"><span data-stu-id="de7e5-102">Defining the Unknown Member and Null Processing Properties</span></span>
  <span data-ttu-id="de7e5-103">當 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 處理維度時，資料來源檢視中之資料表或檢視內基礎資料行的所有相異值會在維度中擴展屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-103">When [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] processes a dimension, all the distinct values from the underlying columns in the tables, or views in the data source view, populate the attributes in the dimension.</span></span> <span data-ttu-id="de7e5-104">如果 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在處理期間發現 Null 值，它預設會將這個 Null 轉換成零 (若為數值資料行) 或空字串 (若為字串資料行)。</span><span class="sxs-lookup"><span data-stu-id="de7e5-104">If [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] encounters a null value during processing, by default, it converts this null to a zero for numeric columns or to an empty string for string columns.</span></span> <span data-ttu-id="de7e5-105">您可以在基礎關聯式資料倉儲的擷取、轉換和載入過程中，修改這些預設值或轉換 Null 值 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="de7e5-105">You can modify the default settings or convert null values in your extract, transform, and load process (if any) of the underlying relational data warehouse.</span></span> <span data-ttu-id="de7e5-106">此外，您也可以設定下列三個屬性，藉以讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 將 Null 值轉換成指定的值：維度的 [UnknownMember]\*\*\*\* 和 [UnknownMemberName]\*\*\*\* 屬性 (property)，以及維度索引鍵屬性 (attribute) 的 [NullProcessing]\*\*\*\* 屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="de7e5-106">Additionally, you can have [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] convert the null value to a designated value by configuring three properties: the **UnknownMember** and **UnknownMemberName** properties for the dimension, and the **NullProcessing** property for the dimension's key attribute.</span></span>

 <span data-ttu-id="de7e5-107">「維度精靈」和「Cube 精靈」將會根據維度的索引鍵屬性是否可為 Null，或者雪花維度的根屬性是否以可為 Null 的資料行為基礎，自動為您啟用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-107">The Dimension Wizard and the Cube Wizard will enable these properties for you based on whether the key attribute of a dimension is nullable or the root attribute of a snowflake dimension is based on a nullable column.</span></span> <span data-ttu-id="de7e5-108">在這些情況下，索引鍵屬性 (attribute) 的 [NullProcessing]\*\*\*\* 屬性 (property) 將會設定為 [UnknownMember]\*\*\*\*，而 [UnknownMember]\*\*\*\* 屬性 (property) 則會設定為 [可見]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-108">In these cases, the **NullProcessing** property of the key attribute will be set to **UnknownMember** and the **UnknownMember** property will be set to **Visible**.</span></span>

 <span data-ttu-id="de7e5-109">但是，當您以累加方式建立雪花維度時 (就如同我們在這個教學課程中處理 [產品] 維度的方式一樣)，或者當您使用 [維度設計師] 定義維度，然後將這些現有的維度合併到 Cube 中時，可能必須以手動方式設定 [UnknownMember]\*\*\*\* 和 [NullProcessing]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-109">However, when you build snowflaked dimensions incrementally, as we are doing with the Product dimension in this tutorial, or when you define dimensions using Dimension Designer and then incorporate these existing dimensions into a cube, the **UnknownMember** and **NullProcessing** properties might need to be set manually.</span></span>

 <span data-ttu-id="de7e5-110">在這個主題的工作中，您會從雪花資料表將產品類別目錄和產品子類別目錄屬性加入 [產品] 維度中，而且您將把雪花資料表加入 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 資料來源檢視中。</span><span class="sxs-lookup"><span data-stu-id="de7e5-110">In the tasks in this topic, you will add the product category and product subcategory attributes to the Product dimension from snowflaked tables that you will add to the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW data source view.</span></span> <span data-ttu-id="de7e5-111">接著，您將啟用 [產品] 維度的 [ **UnknownMember** ] 屬性、指定 `Assembly Components` 作為 [ **UnknownMemberName** ] 屬性的值、將 `Subcategory` 和屬性與 [產品名稱] 屬性建立關聯，然後 `Category` 針對連結雪花資料表的成員索引鍵屬性定義自訂錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="de7e5-111">You will then enable the **UnknownMember** property for the Product dimension, specify `Assembly Components` as the value for the **UnknownMemberName** property, relate the `Subcategory` and `Category` attributes to the product name attribute, and then define custom error handling for the member key attribute that links the snowflaked tables.</span></span>

> [!NOTE]
>  <span data-ttu-id="de7e5-112">如果您最初使用「Cube 精靈」定義 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 時已經加入了 [子類別目錄] 和 [類別目錄] 屬性，系統就會自動執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="de7e5-112">If you have added the Subcategory and Category attributes when you originally defined the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube using the Cube Wizard, these steps would have been performed for you automatically.</span></span>

## <a name="reviewing-error-handling-and-unknown-member-properties-in-the-product-dimension"></a><span data-ttu-id="de7e5-113">在 [產品] 維度中檢閱錯誤處理方式和未知的成員屬性</span><span class="sxs-lookup"><span data-stu-id="de7e5-113">Reviewing Error Handling and Unknown Member Properties in the Product Dimension</span></span>

1.  <span data-ttu-id="de7e5-114">請針對 [產品]\*\*\*\* 維度切換到 [維度設計師]，按一下 [維度結構]\*\*\*\* 索引標籤，然後在 [屬性]\*\*\*\* 窗格中選取 [產品]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-114">Switch to Dimension Designer for the **Product** dimension, click the **Dimension Structure** tab, and then select **Product** in the **Attributes** pane.</span></span>

     <span data-ttu-id="de7e5-115">這可讓您檢視及修改維度本身的屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-115">This enables you to view and modify the properties of the dimension itself.</span></span>

2.  <span data-ttu-id="de7e5-116">在 [屬性] 視窗中，檢閱 [UnknownMember]\*\*\*\* 和 [UnknownMemberName]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-116">In the Properties window, review the **UnknownMember** and **UnknownMemberName** properties.</span></span>

     <span data-ttu-id="de7e5-117">請注意，[UnknownMember]\*\*\*\* 屬性並未啟用，因為它的值是設定為 [無]\*\*\*\*，而不是 [可見]\*\*\*\* 或 [隱藏]\*\*\*\*，而且沒有為 [UnknownMemberName]\*\*\*\* 屬性指定任何名稱。</span><span class="sxs-lookup"><span data-stu-id="de7e5-117">Notice that the **UnknownMember** property is not enabled, because its value is set to **None** instead of **Visible** or **Hidden**, and that no name is specified for the **UnknownMemberName** property.</span></span>

3.  <span data-ttu-id="de7e5-118">在 [屬性] 視窗的 [ErrorConfiguration]\*\*\*\* 屬性資料格中選取 [(自訂)]\*\*\*\*，然後展開 [ErrorConfiguration]\*\*\*\* 屬性集合。</span><span class="sxs-lookup"><span data-stu-id="de7e5-118">In the Properties window, select **(custom)** in the **ErrorConfiguration** property cell, and then expand the **ErrorConfiguration** properties collection.</span></span>

     <span data-ttu-id="de7e5-119">將 [ErrorConfiguration]\*\*\*\* 屬性設定為 [(自訂)]\*\*\*\*，可讓您檢視預設的錯誤組態設定，這麼做並不會變更任何設定。</span><span class="sxs-lookup"><span data-stu-id="de7e5-119">Setting the **ErrorConfiguration** property to **(custom)** allows you to view the default error configuration settings - it does not change any settings.</span></span>

4.  <span data-ttu-id="de7e5-120">檢閱索引鍵和 Null 索引鍵錯誤組態屬性，但不做任何變更。</span><span class="sxs-lookup"><span data-stu-id="de7e5-120">Review the key and null key error configuration properties, but do not make any changes.</span></span>

     <span data-ttu-id="de7e5-121">請注意，依預設，當 Null 索引鍵轉換成未知的成員時，會忽略與這項轉換相關的處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="de7e5-121">Notice that, by default, when null keys are converted to the unknown member and the processing error associated with this conversion is ignored.</span></span>

     <span data-ttu-id="de7e5-122">下圖顯示 [ErrorConfiguration]\*\*\*\* 屬性集合的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="de7e5-122">The following image shows the property settings for the **ErrorConfiguration** properties collection.</span></span>

     <span data-ttu-id="de7e5-123">![ErrorConfiguration 屬性集合](../../2014/tutorials/media/l4-productdimensionerrorconfig-1.gif "ErrorConfiguration 屬性集合")</span><span class="sxs-lookup"><span data-stu-id="de7e5-123">![ErrorConfiguration property collection](../../2014/tutorials/media/l4-productdimensionerrorconfig-1.gif "ErrorConfiguration property collection")</span></span>

5.  <span data-ttu-id="de7e5-124">按一下 [**瀏覽器**] 索引標籤，確認已**在 [階層**] 清單中選取 [**產品型號線**]，然後展開 [] `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="de7e5-124">Click the **Browser** tab, verify that **Product Model Lines** is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>

     <span data-ttu-id="de7e5-125">請注意 [產品線] 層級的 5 個成員。</span><span class="sxs-lookup"><span data-stu-id="de7e5-125">Notice the five members of the Product Line level.</span></span>

6.  <span data-ttu-id="de7e5-126">依序展開 [元件]\*\*\*\* 和 [模型名稱]\*\*\*\* 層級的未標記成員。</span><span class="sxs-lookup"><span data-stu-id="de7e5-126">Expand **Components**, and then expand the unlabeled member of the **Model Name** level.</span></span>

     <span data-ttu-id="de7e5-127">這個層級包含在建立其他元件時所使用的組件元件，從 [Adjustable Race]\*\*\*\* 產品開始，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="de7e5-127">This level contains the assembly components that are used when building other components, starting with the **Adjustable Race** product, as shown in the following image.</span></span>

     <span data-ttu-id="de7e5-128">![用來建立其他元件的組件元件](../../2014/tutorials/media/l4-productdimensionerrorconfig-2.gif "用來建立其他元件的組件元件")</span><span class="sxs-lookup"><span data-stu-id="de7e5-128">![Assembly components used to build other components](../../2014/tutorials/media/l4-productdimensionerrorconfig-2.gif "Assembly components used to build other components")</span></span>

## <a name="defining-attributes-from-snowflaked-tables-and-a-product-category-user-defined-hierarchy"></a><span data-ttu-id="de7e5-129">定義雪花資料表中的屬性和產品類別目錄使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="de7e5-129">Defining Attributes from Snowflaked Tables and a Product Category User-Defined Hierarchy</span></span>

1.  <span data-ttu-id="de7e5-130">請針對 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 資料來源檢視，開啟 [資料來源檢視設計工具]，選取 [圖表組合管理]\*\*\*\* 窗格中的 [轉售商銷售]\*\*\*\*，然後按一下 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [資料來源檢視]\*\*\*\* 功能表中的 [加入/移除物件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-130">Open Data Source View Designer for the [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW data source view, select **Reseller Sales** in the **Diagram Organizer** pane, and then click **Add/Remove Objects** on the **Data Source View** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

     <span data-ttu-id="de7e5-131">此時會開啟 [加入/移除資料表]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="de7e5-131">The **Add/Remove Tables** dialog box opens.</span></span>

2.  <span data-ttu-id="de7e5-132">在 [包含的物件]\*\*\*\* 清單中，選取 [DimProduct (dbo)]\*\*\*\*，然後按一下 [加入相關資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-132">In the **Included objects** list, select **DimProduct (dbo)**, and then click **Add Related Tables**.</span></span>

     <span data-ttu-id="de7e5-133">[DimProductSubcategory (dbo)]\*\*\*\* 和 [FactProductInventory (dbo)]\*\*\*\* 隨即加入。</span><span class="sxs-lookup"><span data-stu-id="de7e5-133">Both **DimProductSubcategory (dbo)** and **FactProductInventory (dbo)** are added.</span></span> <span data-ttu-id="de7e5-134">移除 [FactProductInventory (dbo)]\*\*\*\*，只將 [DimProductSubcategory (dbo)]\*\*\*\* 資料表加入 [包含的物件]\*\*\*\* 清單。</span><span class="sxs-lookup"><span data-stu-id="de7e5-134">Remove **FactProductInventory (dbo)** so that just the **DimProductSubcategory (dbo)** table is added to the **Included objects** list.</span></span>

3.  <span data-ttu-id="de7e5-135">預設選取 [DimProductSubcategory (dbo)]\*\*\*\* 資料表作為最新加入的資料表之後，再按一次 [加入相關資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-135">With the **DimProductSubcategory (dbo)** table selected by default as the table most recently added, click **Add Related Tables** again.</span></span>

     <span data-ttu-id="de7e5-136">此時會將 [DimProductCategory (dbo)]\*\*\*\* 資料表加入 [包含的物件]\*\*\*\* 清單。</span><span class="sxs-lookup"><span data-stu-id="de7e5-136">The **DimProductCategory (dbo)** table is added to the **Included objects** list.</span></span>

4.  <span data-ttu-id="de7e5-137">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="de7e5-137">Click **OK**.</span></span>

5.  <span data-ttu-id="de7e5-138">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 [格式]\*\*\*\* 功能表中，指向 [自動配置]\*\*\*\*，然後按一下 [圖表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-138">On the **Format** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], point to **Auto Layout**, and then click **Diagram**.</span></span>

     <span data-ttu-id="de7e5-139">請注意，[DimProductSubcategory (dbo)]\*\*\*\* 資料表和 [DimProductCategory (dbo)]\*\*\*\* 資料表彼此連結，並且透過 [Product]\*\*\*\* 資料表連結到 [ResellerSales]\*\*\*\* 資料表。</span><span class="sxs-lookup"><span data-stu-id="de7e5-139">Notice that the **DimProductSubcategory (dbo)** table and **DimProductCategory (dbo)** table are linked to each other, and also to the **ResellerSales** table through the **Product** table.</span></span>

6.  <span data-ttu-id="de7e5-140">請針對 [產品]\*\*\*\* 維度切換到 [維度設計師]，然後按一下 [維度結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="de7e5-140">Switch to Dimension Designer for the **Product** dimension, and then click the **Dimension Structure** tab.</span></span>

7.  <span data-ttu-id="de7e5-141">以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的任何位置，然後按一下 [顯示所有資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-141">Right-click anywhere in the **Data Source View** pane, and then click **Show All Tables**.</span></span>

8.  <span data-ttu-id="de7e5-142">在 [資料來源檢視]\*\*\*\* 窗格中，尋找 [DimProductCategory]\*\*\*\* 資料表，以滑鼠右鍵按一下該資料表中的 [ProductCategoryKey]\*\*\*\*，然後按一下 [從資料行新增屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-142">In the **Data Source View** pane, locate the **DimProductCategory** table, right-click **ProductCategoryKey** in that table, and then click **New Attribute from Column**.</span></span>

9. <span data-ttu-id="de7e5-143">在 [**屬性**] 窗格中，將這個新屬性的名稱變更為 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="de7e5-143">In the **Attributes** pane, change the name of this new attribute to `Category`.</span></span>

10. <span data-ttu-id="de7e5-144">在屬性視窗中，按一下 [ **NameColumn** ] 屬性欄位，然後按一下 [流覽 (**...**) ] 按鈕，開啟 [**名稱資料行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="de7e5-144">In the Properties window, click in the **NameColumn** property field and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span>

11. <span data-ttu-id="de7e5-145">選取 [來源資料行]\*\*\*\* 清單中的 [EnglishProductCategoryName]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-145">Select **EnglishProductCategoryName** in the **Source column** list and then click **OK**.</span></span>

12. <span data-ttu-id="de7e5-146">在 [資料來源檢視]\*\*\*\* 窗格中，尋找 [DimProductSubcategory]\*\*\*\* 資料表，以滑鼠右鍵按一下該資料表中的 [ProductSubcategoryKey]\*\*\*\*，然後按一下 [從資料行新增屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-146">In the **Data Source View** pane, locate the **DimProductSubcategory** table, right-click **ProductSubcategoryKey** in that table, and then click **New Attribute from Column**.</span></span>

13. <span data-ttu-id="de7e5-147">在 [**屬性**] 窗格中，將這個新屬性的名稱變更為 `Subcategory` 。</span><span class="sxs-lookup"><span data-stu-id="de7e5-147">In the **Attributes** pane, change the name of this new attribute to `Subcategory`.</span></span>

14. <span data-ttu-id="de7e5-148">在屬性視窗中，按一下 [ **NameColumn** ] 屬性欄位，然後按一下 [流覽\*\* ( ... ) \*\* ] 按鈕，開啟 [**名稱資料行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="de7e5-148">In the Properties window, click in the **NameColumn** property field and then click the browse **(...)** button to open the **Name Column** dialog box.</span></span>

15. <span data-ttu-id="de7e5-149">選取 [來源資料行]\*\*\*\* 清單中的 [EnglishProductSubcategoryName]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-149">Select **EnglishProductSubcategoryName** in the **Source column** list and then click **OK**.</span></span>

16. <span data-ttu-id="de7e5-150">建立名為「**產品類別目錄**」的新使用者定義階層，由上而下的層級（從上到下）： `Category` 、 `Subcategory` 和**產品名稱**。</span><span class="sxs-lookup"><span data-stu-id="de7e5-150">Create a new user-defined hierarchy called **Product Categories** with the following levels, in order from top to bottom: `Category`, `Subcategory`, and **Product Name**.</span></span>

17. <span data-ttu-id="de7e5-151">指定 `All Products` 作為 [產品類別目錄] 使用者定義階層之 [ **AllMemberName** ] 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="de7e5-151">Specify `All Products` as the value for the **AllMemberName** property of the Product Categories user-defined hierarchy.</span></span>

## <a name="browsing-the-user-defined-hierarchies-in-the-product-dimension"></a><span data-ttu-id="de7e5-152">在產品維度中瀏覽使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="de7e5-152">Browsing the User-Defined Hierarchies in the Product Dimension</span></span>

1.  <span data-ttu-id="de7e5-153">在 [產品]\*\*\*\* 維度的 [維度設計師]\*\*\*\* 的 [維度結構]\*\*\*\* 索引標籤的工具列上，按一下 [處理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-153">On the toolbar of the **Dimension Structure** tab of **Dimension Designer** for the **Product** dimension, click **Process**.</span></span>

2.  <span data-ttu-id="de7e5-154">按一下 [是]\*\*\*\* 建立及部署專案，然後按一下 [執行]\*\*\*\* 處理 [產品]\*\*\*\* 維度。</span><span class="sxs-lookup"><span data-stu-id="de7e5-154">Click **Yes** to build and deploy the project, and then click **Run** to process the **Product** dimension.</span></span>

3.  <span data-ttu-id="de7e5-155">處理成功之後，在 [處理進度]\*\*\*\* 對話方塊中依序展開 [Processing Dimension 'Product' completed successfully (產品維度已順利處理完成)]\*\*\*\*、[Processing Dimension Attribute 'Product Name' completed (產品名稱維度屬性已處理完成)]\*\*\*\* 和 [SQL 查詢 1]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-155">When processing has succeeded, expand **Processing Dimension 'Product' completed successfully** in the **Process Progress** dialog box, expand **Processing Dimension Attribute 'Product Name' completed**, and then expand **SQL queries 1**.</span></span>

4.  <span data-ttu-id="de7e5-156">按一下 SELECT DISTINCT 查詢，然後按一下 [檢視詳細資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-156">Click the SELECT DISTINCT query and then click **View Details**.</span></span>

     <span data-ttu-id="de7e5-157">請注意，WHERE 子句已加入 SELECT DISTINCT 子句中，它會移除在 ProductSubcategoryKey 資料行中沒有值的那些產品，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="de7e5-157">Notice that a WHERE clause has been added to the SELECT DISTINCT clause that removes those products that have no value in the ProductSubcategoryKey column, as shown in the following image.</span></span>

     <span data-ttu-id="de7e5-158">![顯示 WHERE 子句的 SELECT DISTINCT 子句](../../2014/tutorials/media/l4-productnametraceline-1.gif "顯示 WHERE 子句的 SELECT DISTINCT 子句")</span><span class="sxs-lookup"><span data-stu-id="de7e5-158">![SELECT DISTINCT clause showing WHERE clause](../../2014/tutorials/media/l4-productnametraceline-1.gif "SELECT DISTINCT clause showing WHERE clause")</span></span>

5.  <span data-ttu-id="de7e5-159">按三次 [關閉]\*\*\*\* 來關閉所有處理中的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="de7e5-159">Click **Close** three times to close all processing dialog boxes.</span></span>

6.  <span data-ttu-id="de7e5-160">請針對 [產品]\*\*\*\* 維度按一下 [維度設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-160">Click the **Browser** tab in Dimension Designer for the **Product** dimension, and then click **Reconnect**.</span></span>

7.  <span data-ttu-id="de7e5-161">確認**產品型號行**出現在 [階層 **] 清單中**，展開 `All Products` ，然後展開 [**元件**]。</span><span class="sxs-lookup"><span data-stu-id="de7e5-161">Verify that **Product Model Lines** appears in the **Hierarchy** list, expand `All Products`, and then expand **Components**.</span></span>

8.  <span data-ttu-id="de7e5-162">**在 [階層**] 清單中選取 [**產品類別目錄**]，展開 `All Products` ，然後展開 [**元件**]。</span><span class="sxs-lookup"><span data-stu-id="de7e5-162">Select **Product Categories** in the **Hierarchy** list, expand `All Products`, and then expand **Components**.</span></span>

     <span data-ttu-id="de7e5-163">請注意，沒有任何組件元件出現。</span><span class="sxs-lookup"><span data-stu-id="de7e5-163">Notice that none of the assembly components appear.</span></span>

 <span data-ttu-id="de7e5-164">若要修改上一個工作中所述的行為，您將啟用 Products 維度的**UnknownMember**屬性、設定**UnknownMemberName**屬性的值、將和模型名稱屬性的**NullProcessing**屬性 `Subcategory` 設定**Model Name**為**UnknownMember**、將屬性定義為 `Category` 屬性的相關屬性，然後將 `Subcategory` **產品線**屬性定義為**模型名稱**屬性的相關屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-164">To modify the behavior mentioned in the previous task, you will enable the **UnknownMember** property of the Products dimension, set a value for the **UnknownMemberName** property, set the **NullProcessing** property for the `Subcategory` and **Model Name** attributes to **UnknownMember**, define the `Category` attribute as a related attribute of the `Subcategory` attribute, and then define the **Product Line** attribute as a related attribute of the **Model Name** attribute.</span></span> <span data-ttu-id="de7e5-165">這些步驟將會使 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在沒有 [SubcategoryKey]\*\*\*\* 資料行值的每一項產品中使用未知的成員名稱值，如下一項工作所示。</span><span class="sxs-lookup"><span data-stu-id="de7e5-165">These steps will cause [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to use the unknown member name value for each product that does not have a value for the **SubcategoryKey** column, as you will see in the following task.</span></span>

## <a name="enabling-the-unknown-member-defining-attribute-relationships-and-specifying-custom-processing-properties-for-nulls"></a><span data-ttu-id="de7e5-166">啟用未知的成員、定義屬性關聯性及指定 Null 的自訂處理屬性</span><span class="sxs-lookup"><span data-stu-id="de7e5-166">Enabling the Unknown Member, Defining Attribute Relationships, and Specifying Custom Processing Properties for Nulls</span></span>

1.  <span data-ttu-id="de7e5-167">在 [產品]\*\*\*\* 維度的 [維度設計師] 中，按一下 [維度結構]\*\*\*\* 索引標籤，然後在 [屬性]\*\*\*\* 窗格中選取 [產品]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-167">Click the **Dimension Structure** tab in Dimension Designer for the **Product** dimension, and then select **Product** in the **Attributes** pane.</span></span>

2.  <span data-ttu-id="de7e5-168">在 [**屬性**] 視窗中，將 [ **UnknownMember** ] 屬性變更為 [**可見**]，然後將 [ **UnknownMemberName** ] 屬性的值變更為 `Assembly Components` 。</span><span class="sxs-lookup"><span data-stu-id="de7e5-168">In the **Properties** window, change the **UnknownMember** property to **Visible**, and then change the value for the **UnknownMemberName** property to `Assembly Components`.</span></span>

     <span data-ttu-id="de7e5-169">將 [UnknownMember]\*\*\*\* 屬性變更為 [可見]\*\*\*\* 或 [隱藏]\*\*\*\* 會啟用維度的 [UnknownMember]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-169">Changing the **UnknownMember** property to either **Visible** or **Hidden** enables the **UnknownMember** property for the dimension.</span></span>

3.  <span data-ttu-id="de7e5-170">按一下 **[屬性關聯性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="de7e5-170">Click the **Attribute Relationships** tab.</span></span>

4.  <span data-ttu-id="de7e5-171">在圖表中，以滑鼠右鍵按一下 `Subcategory` 屬性，然後選取 [**新增屬性關聯**性]。</span><span class="sxs-lookup"><span data-stu-id="de7e5-171">In the diagram, right-click the `Subcategory` attribute and then select **New Attribute Relationship**.</span></span>

5.  <span data-ttu-id="de7e5-172">在 [**建立屬性關聯**性] 對話方塊中，[**來源屬性**] 是 `Subcategory` 。</span><span class="sxs-lookup"><span data-stu-id="de7e5-172">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is `Subcategory`.</span></span> <span data-ttu-id="de7e5-173">將**相關屬性**設定為 `Category` 。</span><span class="sxs-lookup"><span data-stu-id="de7e5-173">Set the **Related Attribute** to `Category`.</span></span> <span data-ttu-id="de7e5-174">然後，保持關聯性類型設定為 [彈性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-174">Leave the relationship type set to **Flexible**.</span></span>

6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]

7.  <span data-ttu-id="de7e5-175">在 [屬性]\*\*\*\* 窗格中，選取 [子類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-175">In the **Attributes** pane, select **Subcategory.**</span></span>

8.  <span data-ttu-id="de7e5-176">在 [屬性] 視窗中，展開 [KeyColumns]\*\*\*\* 屬性，然後展開 [DimProductSubcategory.ProductSubcategoryKey (Integer)]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-176">In the Properties window, expand the **KeyColumns** property and then expand the **DimProductSubcategory.ProductSubcategoryKey (Integer)** property.</span></span>

9. <span data-ttu-id="de7e5-177">將 [NullProcessing]\*\*\*\* 屬性變更為 [UnknownMember]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-177">Change the **NullProcessing** property to **UnknownMember**.</span></span>

10. <span data-ttu-id="de7e5-178">在 [屬性]\*\*\*\* 窗格中，選取 [模型名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-178">In the **Attributes** pane, select **Model Name**.</span></span>

11. <span data-ttu-id="de7e5-179">在 [屬性] 視窗中，展開 [KeyColumns]\*\*\*\* 屬性，然後展開 [Product.ModelName (WChar)]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="de7e5-179">In the Properties window, expand the **KeyColumns** property and then expand the **Product.ModelName (WChar)** property.</span></span>

12. <span data-ttu-id="de7e5-180">將 [NullProcessing]\*\*\*\* 屬性變更為 [UnknownMember]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-180">Change the **NullProcessing** property to **UnknownMember**.</span></span>

     <span data-ttu-id="de7e5-181">由於這些變更，當在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] `Subcategory` 處理期間遇到屬性或**模型名稱**屬性的 null 值時，未知的成員值會取代為索引鍵值，而使用者定義階層將會正確地進行結構化。</span><span class="sxs-lookup"><span data-stu-id="de7e5-181">Because of these changes, when [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] encounters a null value for the `Subcategory` attribute or the **Model Name** attribute during processing, the unknown member value will be substituted as the key value, and the user-defined hierarchies will be constructed correctly.</span></span>

## <a name="browsing-the-product-dimension-again"></a><span data-ttu-id="de7e5-182">再次瀏覽 [產品] 維度</span><span class="sxs-lookup"><span data-stu-id="de7e5-182">Browsing the Product Dimension Again</span></span>

1.  <span data-ttu-id="de7e5-183">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-183">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="de7e5-184">順利完成部署之後，針對 [產品]\*\*\*\* 維度按一下 [維度設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="de7e5-184">When deployment has successfully completed, click the **Browser** tab in Dimension Designer for the **Product** dimension, and then click **Reconnect**.</span></span>

3.  <span data-ttu-id="de7e5-185">確認已**在 [階層**] 清單中選取 [**產品類別目錄**]，然後展開 [] `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="de7e5-185">Verify that **Product Categories** is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>

     <span data-ttu-id="de7e5-186">請注意，此時「組件元件」會出現成為 [類別目錄] 層級的新成員。</span><span class="sxs-lookup"><span data-stu-id="de7e5-186">Notice that Assembly Components appears as a new member of the Category level.</span></span>

4.  <span data-ttu-id="de7e5-187">展開 `Assembly Components` 層級的成員 `Category` ，然後展開 `Assembly Components` `Subcategory` 層級的成員。</span><span class="sxs-lookup"><span data-stu-id="de7e5-187">Expand the `Assembly Components` member of the `Category` level and then expand the `Assembly Components` member of the `Subcategory` level.</span></span>

     <span data-ttu-id="de7e5-188">請注意，所有組件元件現在都會出現在 [產品名稱]\*\*\*\* 層級，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="de7e5-188">Notice that all the assembly components now appear at the **Product Name** level, as shown in the following image.</span></span>

     <span data-ttu-id="de7e5-189">![顯示組件元件的產品名稱層級](../../2014/tutorials/media/l4-assemblycomponents-1.gif "顯示組件元件的產品名稱層級")</span><span class="sxs-lookup"><span data-stu-id="de7e5-189">![Product Name level showing assembly components](../../2014/tutorials/media/l4-assemblycomponents-1.gif "Product Name level showing assembly components")</span></span>

## <a name="next-lesson"></a><span data-ttu-id="de7e5-190">下一課</span><span class="sxs-lookup"><span data-stu-id="de7e5-190">Next Lesson</span></span>
 [<span data-ttu-id="de7e5-191">第5課：定義維度和量值群組之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="de7e5-191">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)


