---
title: 定義參考的關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4a34ba52-e3b3-4e8a-8e55-73e0cd5a97bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7b14699ad098ba8c0931c00a3cbd30a6a8026771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606475"
---
# <a name="defining-a-referenced-relationship"></a><span data-ttu-id="d477c-102">定義參考關聯性</span><span class="sxs-lookup"><span data-stu-id="d477c-102">Defining a Referenced Relationship</span></span>
  <span data-ttu-id="d477c-103">本教學課程最特別要注意的事就是，您定義的每一個 Cube 維度所依據的資料表，是透過主索引鍵對外部索引鍵的關聯性，直接連結到量值群組的事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d477c-103">Up to this point in the tutorial, each cube dimension that you defined was based on a table that was directly linked to the fact table for a measure group by a primary key to foreign key relationship.</span></span> <span data-ttu-id="d477c-104">在本主題的工作中，您會透過 [轉售商]\*\*\*\* 維度 (稱為「參考維度」\*\*)，將 [地理位置]\*\*\*\* 維度連結到事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d477c-104">In the tasks in this topic, you link the **Geography** dimension to the fact table for reseller sales through the **Reseller** dimension, which is called a *reference dimension*.</span></span> <span data-ttu-id="d477c-105">這樣可讓使用者按地理位置建立轉售商銷售的維度。</span><span class="sxs-lookup"><span data-stu-id="d477c-105">This enables users to dimension reseller sales by geography.</span></span> <span data-ttu-id="d477c-106">如需詳細資訊，請參閱 [定義參考的關聯性及參考的關聯性屬性](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d477c-106">For more information, see [Define a Referenced Relationship and Referenced Relationship Properties](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md).</span></span>

## <a name="dimensioning-reseller-sales-by-geography"></a><span data-ttu-id="d477c-107">按地理位置建立轉售商銷售的維度</span><span class="sxs-lookup"><span data-stu-id="d477c-107">Dimensioning Reseller Sales by Geography</span></span>

1.  <span data-ttu-id="d477c-108">在方案總管中，以滑鼠右鍵按一下 [Cubes]\*\*\*\* 資料夾中的 [Analysis Services Tutorial]\*\*\*\*，然後按一下 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-108">In Solution Explorer, right-click **Analysis Services Tutorial** in the **Cubes** folder, and then click **Browse**.</span></span>

2.  <span data-ttu-id="d477c-109">從 [資料] 窗格中移除所有階層，然後確認 [轉售商銷售 - 銷售量]\*\*\*\* 量值確實出現在 [資料] 窗格的資料區域中。</span><span class="sxs-lookup"><span data-stu-id="d477c-109">Remove all hierarchies from the data pane, and then verify that the **Reseller Sales-Sales Amount** measure appears in the data area of the data pane.</span></span> <span data-ttu-id="d477c-110">如果沒有，請將它加入至 [資料] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="d477c-110">Add it to the data pane if it is not already there.</span></span>

3.  <span data-ttu-id="d477c-111">從 [中繼資料] 窗格的 [地理位置]\*\*\*\* 維度中，將 [地理位置]\*\*\*\* 使用者定義階層拖曳到 [資料] 窗格的 [將列欄位拖曳到這裡]\*\*\*\* 區域。</span><span class="sxs-lookup"><span data-stu-id="d477c-111">From the **Geography** dimension in the metadata pane, drag the **Geographies** user-defined hierarchy to the **Drop Row Fields Here** area of the data pane.</span></span>

     <span data-ttu-id="d477c-112">請注意，[區域]\*\*\*\* 階層中的 [國家地區]\*\*\*\* 屬性成員未正確設定 [轉售商銷售 - 銷售量]\*\*\*\* 量值的維度。</span><span class="sxs-lookup"><span data-stu-id="d477c-112">Notice that the **Reseller Sales-Sales Amount** measure is not correctly dimensioned by the **Country-Region** attribute members in the **Regions** hierarchy.</span></span> <span data-ttu-id="d477c-113">針對每個 [國家地區]\*\*\*\* 屬性成員，[轉售商銷售 - 銷售量]\*\*\*\* 的值會重複。</span><span class="sxs-lookup"><span data-stu-id="d477c-113">The value for **Reseller Sales-Sales Amount** repeats for each **Country-Region** attribute member.</span></span>

     <span data-ttu-id="d477c-114">![建立維度的轉售商銷售額-銷售額量值](../../2014/tutorials/media/l5-referencedrelationship-1.gif "建立維度的轉售商銷售額-銷售額量值")</span><span class="sxs-lookup"><span data-stu-id="d477c-114">![Dimensioned Reseller Sales-Sales Amount measure](../../2014/tutorials/media/l5-referencedrelationship-1.gif "Dimensioned Reseller Sales-Sales Amount measure")</span></span>

4.  <span data-ttu-id="d477c-115">請針對 **Adventure Works DW 2012** 資料來源檢視，開啟資料來源檢視設計師。</span><span class="sxs-lookup"><span data-stu-id="d477c-115">Open Data Source View Designer for the **Adventure Works DW 2012** data source view.</span></span>

5.  <span data-ttu-id="d477c-116">在 [圖表組合管理]\*\*\*\* 窗格中，檢視 [Geography]\*\*\*\* 資料表與 [ResellerSales]\*\*\*\* 資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="d477c-116">In the **Diagram Organizer** pane, view the relationship between the **Geography** table and the **ResellerSales** table.</span></span>

     <span data-ttu-id="d477c-117">請注意，這些資料表之間沒有直接連結。</span><span class="sxs-lookup"><span data-stu-id="d477c-117">Notice that there is no direct link between these tables.</span></span> <span data-ttu-id="d477c-118">不過，透過 [Reseller]\*\*\*\* 資料表或 [SalesTerritory]\*\*\*\* 資料表，這些資料表之間有間接連結。</span><span class="sxs-lookup"><span data-stu-id="d477c-118">However, there is an indirect link between these tables through either the **Reseller** table or the **SalesTerritory** table.</span></span>

6.  <span data-ttu-id="d477c-119">按兩下代表 [Geography]\*\*\*\* 資料表和 [Reseller]\*\*\*\* 資料表之間關聯性的箭頭。</span><span class="sxs-lookup"><span data-stu-id="d477c-119">Double-click the arrow that represents the relationship between the **Geography** table and the **Reseller** table.</span></span>

     <span data-ttu-id="d477c-120">請注意，在 [編輯關聯性]\*\*\*\* 對話方塊中，[GeographyKey]\*\*\*\* 資料行是 [Geography]\*\*\*\* 資料表中的主索引鍵以及 [Reseller]\*\*\*\* 資料表中的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d477c-120">In the **Edit Relationship** dialog box, notice that the **GeographyKey** column is the primary key in the **Geography** table and the foreign key in the **Reseller** table.</span></span>

7.  <span data-ttu-id="d477c-121">按一下 [取消]\*\*\*\*，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程的 Cube 切換到 [Cube 設計師]，然後按一下 [維度使用方式]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d477c-121">Click **Cancel**, switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Dimension Usage** tab.</span></span>

     <span data-ttu-id="d477c-122">請注意，目前 [地理位置]\*\*\*\* Cube 維度與 [網際網路銷售]\*\*\*\* 量值群組或 [轉售商銷售]\*\*\*\* 量值群組之間沒有關聯性。</span><span class="sxs-lookup"><span data-stu-id="d477c-122">Notice that the **Geography** cube dimension does not currently have a relationship with either the **Internet Sales** measure group or the **Reseller Sales** measure group.</span></span>

8.  <span data-ttu-id="d477c-123">在 [**客戶**] 維度和 [**網際網路銷售**] 量值群組的交集處，按一下 [**全名**] 資料格中的省略號按鈕 (**...**) 。</span><span class="sxs-lookup"><span data-stu-id="d477c-123">Click the ellipsis button (**...**) in the **Full Name** cell at the intersection of the **Customer** dimension and the **Internet Sales** measure group.</span></span>

     <span data-ttu-id="d477c-124">請注意，在 [定義關聯性]\*\*\*\* 對話方塊中，[DimCustomer]\*\*\*\* 維度資料表和 [FactInternetSales]\*\*\*\* 量值群組資料表之間定義的 [一般]\*\*\*\* 關聯性，是依據這些資料表中的 [CustomerKey]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="d477c-124">In the **Define Relationship** dialog box, notice that a **Regular** relationship is defined between the **DimCustomer** dimension table and the **FactInternetSales** measure group table based on the **CustomerKey** column in each of these tables.</span></span> <span data-ttu-id="d477c-125">到目前為止，您在這個教學課程中定義的所有關聯性都是一般關聯性。</span><span class="sxs-lookup"><span data-stu-id="d477c-125">All the relationships that you have defined within this tutorial up to this point have been regular relationships.</span></span>

     <span data-ttu-id="d477c-126">下圖顯示 [定義關聯性]\*\*\*\* 對話方塊，其中在 [DimCustomer]\*\*\*\* 維度資料表和 [FactInternetSales]\*\*\*\* 量值群組資料表之間有一般關聯性。</span><span class="sxs-lookup"><span data-stu-id="d477c-126">The following image shows the **Define Relationship** dialog box with a regular relationship between the **DimCustomer** dimension table and the **FactInternetSales** measure group table.</span></span>

     <span data-ttu-id="d477c-127">![[定義關聯性] 對話方塊](../../2014/tutorials/media/l5-referencedrelationship-4.gif "定義關聯性對話方塊")</span><span class="sxs-lookup"><span data-stu-id="d477c-127">![Define Relationship dialog box](../../2014/tutorials/media/l5-referencedrelationship-4.gif "Define Relationship dialog box")</span></span>

9. <span data-ttu-id="d477c-128">按一下 [取消]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-128">Click **Cancel**.</span></span>

10. <span data-ttu-id="d477c-129">在 [ **Geography** ] 維度和 [**轉售商銷售**] 量值群組的交集處，按一下未命名資料格中的省略號按鈕 (**...**) 。</span><span class="sxs-lookup"><span data-stu-id="d477c-129">Click the ellipsis button (**...**) in the unnamed cell at the intersection of the **Geography** dimension and the **Reseller Sales** measure group.</span></span>

     <span data-ttu-id="d477c-130">在 [定義關聯性]\*\*\*\* 對話方塊中，請注意，[地理位置] Cube 維度和 [轉售商銷售] 量值群組之間目前並未定義關聯性。</span><span class="sxs-lookup"><span data-stu-id="d477c-130">In the **Define Relationship** dialog box, notice that no relationship is currently defined between the Geography cube dimension and the Reseller Sales measure group.</span></span> <span data-ttu-id="d477c-131">您不能定義一般關聯性，因為 [Geography] 維度的維度資料表和 [Reseller Sales] 量值群組的事實資料表之間沒有直接關聯性。</span><span class="sxs-lookup"><span data-stu-id="d477c-131">You cannot define a regular relationship because there is no direct relationship between the dimension table for the Geography dimension and the fact table for the Reseller Sales measure group.</span></span>

11. <span data-ttu-id="d477c-132">在 [選取關聯性類型]\*\*\*\* 清單中，選取 [參考的]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-132">In the **Select relationship type** list, select **Referenced**.</span></span>

     <span data-ttu-id="d477c-133">您可以指定一個直接連接到量值群組資料表的維度 (稱為「中繼維度」\*\*) 來定義參考關聯性，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 可利用它來連結參考維度與事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d477c-133">You define a referenced relationship by specifying a dimension that is directly connected to the measure group table, called an *intermediate dimension*, that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use to link the reference dimension to the fact table.</span></span> <span data-ttu-id="d477c-134">然後，您可以指定一個屬性來連結參考維度與中繼維度。</span><span class="sxs-lookup"><span data-stu-id="d477c-134">You then specify the attribute that links the reference dimension to the intermediate dimension.</span></span>

12. <span data-ttu-id="d477c-135">在 [中繼維度]\*\*\*\* 清單中，選取 [轉售商]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-135">In the **Intermediate dimension** list, select **Reseller**.</span></span>

     <span data-ttu-id="d477c-136">[Geography] 維度的基礎資料表會透過 [Reseller] 維度的基礎資料表連結到事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d477c-136">The underlying table for the Geography dimension is linked to the fact table through the underlying table for the Reseller dimension.</span></span>

13. <span data-ttu-id="d477c-137">在 [參考維度屬性]\*\*\*\* 清單中，選取 [地理位置索引鍵]\*\*\*\*，然後試著選取 [中繼維度屬性]\*\*\*\* 清單中的 [地理位置索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-137">In the **Reference dimension attribute** list, select **Geography Key**, and then try to select **Geography Key** in the **Intermediate dimension attribute** list.</span></span>

     <span data-ttu-id="d477c-138">請注意，[地理位置索引鍵]\*\*\*\* 並沒有出現在 [中繼維度屬性]\*\*\*\* 清單中。</span><span class="sxs-lookup"><span data-stu-id="d477c-138">Notice that **Geography Key** does not appear in the **Intermediate dimension attribute** list.</span></span> <span data-ttu-id="d477c-139">這是因為 [地理位置索引鍵]\*\*\*\* 資料行未定義成 [轉售商]\*\*\*\* 維度中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d477c-139">This is because the **GeographyKey** column is not defined as an attribute in the **Reseller** dimension.</span></span>

14. <span data-ttu-id="d477c-140">按一下 [取消]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-140">Click **Cancel**.</span></span>

 <span data-ttu-id="d477c-141">在下一項工作中，您將定義一個依據 [Reseller] 維度的 [GeographyKey] 資料行的屬性來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="d477c-141">In the next task, you will solve this problem by defining an attribute that is based on the GeographyKey column in the Reseller dimension.</span></span>

## <a name="defining-the-intermediate-dimension-attribute-and-the-referenced-dimension-relationship"></a><span data-ttu-id="d477c-142">定義中繼維度屬性和參考維度關聯性</span><span class="sxs-lookup"><span data-stu-id="d477c-142">Defining the Intermediate Dimension Attribute and the Referenced Dimension Relationship</span></span>

1.  <span data-ttu-id="d477c-143">針對 [轉售商]\*\*\*\* 維度開啟 [維度設計師]，然後在 [資料來源檢視]\*\*\*\* 窗格的 [Reseller]\*\*\*\* 資料表中檢視資料行，並在 [屬性]\*\*\*\* 窗格的 [轉售商]\*\*\*\* 維度中檢視已定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="d477c-143">Open Dimension Designer for the **Reseller** dimension, and view the columns in the **Reseller** table in the **Data Source View** pane, and view the defined attributes in the **Reseller** dimension in the **Attributes** pane.</span></span>

     <span data-ttu-id="d477c-144">請注意，雖然 GeographyKey 是定義成 [Reseller] 資料表中的資料行，但在 [Reseller] 維度中並沒有定義依據這個資料行的維度屬性。</span><span class="sxs-lookup"><span data-stu-id="d477c-144">Notice that although GeographyKey is defined as a column in the Reseller table, no dimension attribute is defined in the Reseller dimension based on this column.</span></span> <span data-ttu-id="d477c-145">[Geography] 是定義成 [Geography] 維度中的維度屬性，因為它是連結維度的基礎資料表與事實資料表的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="d477c-145">Geography is defined as a dimension attribute in the Geography dimension because it is the key column that links the underlying table for that dimension to the fact table.</span></span>

2.  <span data-ttu-id="d477c-146">若要將 [地理位置索引鍵]\*\*\*\* 屬性加入 [轉售商]\*\*\*\* 維度，請以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格中的 [GeographyKey]\*\*\*\*，然後按一下 [從資料行新增屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-146">To add a **Geography Key** attribute to the **Reseller** dimension, right-click **GeographyKey** in the **Data Source View** pane, and then click **New Attribute from Column**.</span></span>

3.  <span data-ttu-id="d477c-147">在 [屬性]\*\*\*\* 窗格中，選取 [地理位置索引鍵]\*\*\*\*，然後在 [屬性] 視窗中，將 [AttributeHierarchyOptimizedState]\*\*\*\* 屬性設定為 [NotOptimized]\*\*\*\*、將 [AttributeHierarchyOrdered]\*\*\*\* 屬性設定為 [False]\*\*\*\*，並且將 [AttributeHierarchyVisible]\*\*\*\* 屬性設定為 [False]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-147">In the **Attributes** pane, select **Geography Key**, and then, in the Properties window, set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, the **AttributeHierarchyOrdered** property to **False**, and the **AttributeHierarchyVisible** property to **False.**</span></span>

     <span data-ttu-id="d477c-148">[Reseller] 維度中的 [Geography Key] 屬性只用來連結 [Geography] 維度與 [Reseller Sales] 事實資料表。</span><span class="sxs-lookup"><span data-stu-id="d477c-148">The Geography Key attribute in the Reseller dimension will only be used to link the Geography dimension to the Reseller Sales fact table.</span></span> <span data-ttu-id="d477c-149">因為它不用於瀏覽，所以定義這個屬性階層的值沒有一個會顯示出來。</span><span class="sxs-lookup"><span data-stu-id="d477c-149">Because it will not be used for browsing, there is no value in defining this attribute hierarchy as visible.</span></span> <span data-ttu-id="d477c-150">而且，屬性階層的排序和最佳化對處理效能只有負面影響。</span><span class="sxs-lookup"><span data-stu-id="d477c-150">Additionally, ordering and optimizing the attribute hierarchy will only negatively affect processing performance.</span></span> <span data-ttu-id="d477c-151">不過，必須啟用屬性才能做為兩個維度之間的連結。</span><span class="sxs-lookup"><span data-stu-id="d477c-151">However, the attribute must be enabled to serve as the link between the two dimensions.</span></span>

4.  <span data-ttu-id="d477c-152">針對教學課程 Cube，切換到 Cube 設計師 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，按一下 [**維度使用**方式] 索引標籤，然後按一下 [**轉售商銷售**] 量值群組和 [ **Geography** ] Cube 維度交集處的省略號按鈕 (**...**) 。</span><span class="sxs-lookup"><span data-stu-id="d477c-152">Switch to Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, click the **Dimension Usage** tab, and then click the ellipsis button (**...**) at the intersection of the **Reseller Sales** measure group and the **Geography** cube dimension.</span></span>

5.  <span data-ttu-id="d477c-153">在 [選取關聯性類型]\*\*\*\* 清單中，選取 [參考的]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-153">In the **Select relationship type** list, select **Referenced**.</span></span>

6.  <span data-ttu-id="d477c-154">在 [中繼維度]\*\*\*\* 清單中，選取 [轉售商]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-154">In the **Intermediate dimension** list, select **Reseller**.</span></span>

7.  <span data-ttu-id="d477c-155">在 [參考維度屬性]\*\*\*\* 清單中，選取 [地理位置索引鍵]\*\*\*\*，然後選取 [中繼維度屬性]\*\*\*\* 清單中的 [地理位置索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-155">In the **Reference dimension attribute** list, select **Geography Key**, and then select **Geography Key** in the **Intermediate dimension attribute** list.</span></span>

     <span data-ttu-id="d477c-156">請注意，已選取 [具體化]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d477c-156">Notice that the **Materialize** check box is selected.</span></span> <span data-ttu-id="d477c-157">這項設定是 MOLAP 維度的預設值。</span><span class="sxs-lookup"><span data-stu-id="d477c-157">This is the default setting for MOLAP dimensions.</span></span> <span data-ttu-id="d477c-158">具體化維度屬性連結，會在處理期間使事實資料表與每個資料列的參考維度之間的連結值具體化，或是儲存在維度的 MOLAP 結構中。</span><span class="sxs-lookup"><span data-stu-id="d477c-158">Materializing the dimension attribute link causes the value of the link between the fact table and the reference dimension for each row to be materialized, or stored, in the dimension's MOLAP structure during processing.</span></span> <span data-ttu-id="d477c-159">這對處理效能及儲存體需求上會有一點影響，但會提升 (偶爾也會大幅提升) 查詢效能。</span><span class="sxs-lookup"><span data-stu-id="d477c-159">This will have a minor effect on processing performance and storage requirements, but will increase query performance (sometimes significantly).</span></span>

8.  <span data-ttu-id="d477c-160">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d477c-160">Click **OK**.</span></span>

     <span data-ttu-id="d477c-161">請注意，[地理位置]\*\*\*\* Cube 維度現在是連結到 [轉售商銷售]\*\*\*\* 量值群組。</span><span class="sxs-lookup"><span data-stu-id="d477c-161">Notice that the **Geography** cube dimension is now linked to the **Reseller Sales** measure group.</span></span> <span data-ttu-id="d477c-162">這個圖示指出其關聯性是參考維度關聯性。</span><span class="sxs-lookup"><span data-stu-id="d477c-162">The icon indicates that the relationship is a referenced dimension relationship.</span></span>

9. <span data-ttu-id="d477c-163">在 [維度使用方式]\*\*\*\* 索引標籤的 [維度]\*\*\*\* 清單中，以滑鼠右鍵按一下 [地理位置]\*\*\*\*，然後按一下 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-163">In the **Dimensions** list on the **Dimension Usage** tab, right-click **Geography**, and then click **Rename**.</span></span>

10. <span data-ttu-id="d477c-164">將這個 cube 維度的名稱變更為 `Reseller Geography` 。</span><span class="sxs-lookup"><span data-stu-id="d477c-164">Change the name of this cube dimension to `Reseller Geography`.</span></span>

     <span data-ttu-id="d477c-165">由於這個 Cube 維度現在是連結到 [轉售商銷售]\*\*\*\* 量值群組，所以使用者可在 Cube 中明確定義其使用方式，如此可避免產生可能的誤解。</span><span class="sxs-lookup"><span data-stu-id="d477c-165">Because this cube dimension is now linked to the **Reseller Sales** measure group, users will benefit from explicitly defining its use in the cube, to avoid possible user confusion.</span></span>

## <a name="successfully-dimensioning-reseller-sales-by-geography"></a><span data-ttu-id="d477c-166">按地理位置成功地建立轉售商銷售的維度</span><span class="sxs-lookup"><span data-stu-id="d477c-166">Successfully Dimensioning Reseller Sales by Geography</span></span>

1.  <span data-ttu-id="d477c-167">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d477c-167">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

2.  <span data-ttu-id="d477c-168">順利完成部署之後，針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，按一下 [Cube 設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d477c-168">When deployment has successfully completed, click the **Browser** tab in Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **Reconnect** button.</span></span>

3.  <span data-ttu-id="d477c-169">在 [中繼資料] 窗格中，展開 `Reseller Geography` ，以滑鼠右鍵按一下 [**地理**位置]，然後按一下 [**加入至資料欄區域**]。</span><span class="sxs-lookup"><span data-stu-id="d477c-169">In the metadata pane, expand `Reseller Geography`, right-click **Geographies**, and then click **Add to Row Area**.</span></span>

     <span data-ttu-id="d477c-170">請注意，[地理位置]\*\*\*\* 使用者定義階層的 [國家地區]\*\*\*\* 屬性現在已正確設定 [轉售商銷售 - 銷售量]\*\*\*\* 量值的維度，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d477c-170">Notice that the **Reseller Sales-Sales Amount** measure is now correctly dimensioned by the **Country-Region** attribute of the **Geographies** user-defined hierarchy, as shown in the following image.</span></span>

     <span data-ttu-id="d477c-171">![[定義關聯性] 對話方塊](../../2014/tutorials/media/l5-referencedrelationship-5.gif "定義關聯性對話方塊")</span><span class="sxs-lookup"><span data-stu-id="d477c-171">![Define Relationship dialog box](../../2014/tutorials/media/l5-referencedrelationship-5.gif "Define Relationship dialog box")</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="d477c-172">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="d477c-172">Next Task in Lesson</span></span>
 [<span data-ttu-id="d477c-173">定義事實關聯性</span><span class="sxs-lookup"><span data-stu-id="d477c-173">Defining a Fact Relationship</span></span>](lesson-5-2-defining-a-fact-relationship.md)

## <a name="see-also"></a><span data-ttu-id="d477c-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d477c-174">See Also</span></span>
 <span data-ttu-id="d477c-175">[屬性關聯](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)性[定義參考的關聯性和參考的關聯性屬性](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)</span><span class="sxs-lookup"><span data-stu-id="d477c-175">[Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) [Define a Referenced Relationship and Referenced Relationship Properties](multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)</span></span>


