---
title: 修改 [產品] 維度 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 04c0a778a73371dada92c9ff207a17366a2fbc7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597436"
---
# <a name="modifying-the-product-dimension"></a><span data-ttu-id="7c8ca-102">修改 [產品] 維度</span><span class="sxs-lookup"><span data-stu-id="7c8ca-102">Modifying the Product Dimension</span></span>
  <span data-ttu-id="7c8ca-103">在這個主題的工作中，您會使用具名計算來針對產品線提供更具描述性的名稱、定義 [產品] 維度中的階層，以及指定該階層的 (全部) 成員名稱。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-103">In the tasks in this topic, you use a named calculation to provide more descriptive names for the product lines, define a hierarchy in the Product dimension, and specify the (All) member name for the hierarchy.</span></span> <span data-ttu-id="7c8ca-104">此外，您也會將屬性分組放入顯示資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-104">You also group attributes into display folders.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="7c8ca-105">加入具名計算</span><span class="sxs-lookup"><span data-stu-id="7c8ca-105">Adding a Named Calculation</span></span>  
 <span data-ttu-id="7c8ca-106">您可以將具名計算加入至資料來源檢視中的資料表。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-106">You can add a named calculation to a table in a data source view.</span></span> <span data-ttu-id="7c8ca-107">在下列工作中，您會建立可顯示完整產品線名稱的具名計算。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-107">In the following task, you create a named calculation that displays the full product line name.</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="7c8ca-108">加入具名計算</span><span class="sxs-lookup"><span data-stu-id="7c8ca-108">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="7c8ca-109">若要開啟 [Adventure Works DW 2012]\*\*\*\* 資料來源檢視，請在方案總管的 [資料來源檢視]\*\*\*\* 資料夾中按兩下 [Adventure Works DW 2012]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-109">To open the **Adventure Works DW 2012** data source view, double-click **Adventure Works DW 2012** in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="7c8ca-110">在 [圖表] 窗格的底部，以滑鼠右鍵按一下 [Product]\*\*\*\* 資料表標頭，然後按一下 [新增具名計算]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-110">In the bottom of the diagram pane, right-click the **Product** table header, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="7c8ca-111">在 [**建立指名的計算**] 對話方塊中，于 `ProductLineName` [資料**行名稱**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-111">In the **Create Named Calculation** dialog box, type `ProductLineName` in the **Column name** box.</span></span>  
  
4.  <span data-ttu-id="7c8ca-112">在 [運算式]\*\*\*\* 方塊中，輸入或複製並貼上下列 **CASE** 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7c8ca-112">In the **Expression** box, type or copy and paste the following **CASE** statement:</span></span>  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     <span data-ttu-id="7c8ca-113">這個 **CASE** 陳述式會為 Cube 的每個產品線建立使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-113">This **CASE** statement creates user-friendly names for each product line in the cube.</span></span>  
  
5.  <span data-ttu-id="7c8ca-114">按一下 **[確定]** 以建立 `ProductLineName` 已命名的計算。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-114">Click **OK** to create the `ProductLineName` named calculation.</span></span> <span data-ttu-id="7c8ca-115">您可能需要稍等一下。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-115">You might need to wait.</span></span>  
  
6.  <span data-ttu-id="7c8ca-116">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a><span data-ttu-id="7c8ca-117">修改屬性 (Attribute) 的 NameColumn 屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="7c8ca-117">Modifying the NameColumn Property of an Attribute</span></span>  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a><span data-ttu-id="7c8ca-118">修改屬性 (Attribute) 的 NameColumn 屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="7c8ca-118">To modify the NameColumn property value of an attribute</span></span>  
  
1.  <span data-ttu-id="7c8ca-119">針對 [產品] 維度切換到維度設計師。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-119">Switch to Dimension Designer for the Product dimension.</span></span> <span data-ttu-id="7c8ca-120">若要這樣做，請在方案總管的 [維度]\*\*\*\* 節點中，按兩下 [產品]\*\*\*\* 維度。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-120">To do this, double-click the **Product** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="7c8ca-121">在 [維度結構]\*\*\*\* 索引標籤的 [屬性]\*\*\*\* 窗格中，選取 [產品線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-121">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Line**.</span></span>  
  
3.  <span data-ttu-id="7c8ca-122">在畫面右側的 [屬性視窗中，按一下視窗底部的 [ **NameColumn** ] 屬性欄位，然後按一下 [流覽 (**...** ]) ] 按鈕，開啟 [**名稱資料行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-122">In the Properties window on the right side of the screen, click the **NameColumn** property field at the bottom of the window, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span> <span data-ttu-id="7c8ca-123">(您可能需要按一下畫面右側的 [屬性]\*\*\*\* 索引標籤開啟 [屬性] 視窗)。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-123">(You might need to click the **Properties** tab on the right side of the screen to open the Properties window.</span></span>  
  
4.  <span data-ttu-id="7c8ca-124">選取 `ProductLineName` [**來源資料行**] 清單底部的，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-124">Select `ProductLineName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7c8ca-125">[NameColumn] 欄位現在會包含 **Product.ProductLineName (WChar)** 文字。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-125">The NameColumn field now contains the text, **Product.ProductLineName (WChar)**.</span></span> <span data-ttu-id="7c8ca-126">[產品線]\*\*\*\* 屬性階層的成員現在會顯示產品線的全名，而非產品線的簡稱。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-126">The members of the **Product Line** attribute hierarchy now display the full name of the product line instead of an abbreviated product line name.</span></span>  
  
5.  <span data-ttu-id="7c8ca-127">在 [維度結構]\*\*\*\* 索引標籤的 [屬性]\*\*\*\* 窗格中，選取 [產品金鑰]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-127">In the **Attributes** pane of the **Dimension Structure** tab, select **Product Key**.</span></span>  
  
6.  <span data-ttu-id="7c8ca-128">在 [屬性視窗中，按一下 [ **NameColumn** ] 屬性欄位，然後按一下省略號的流覽 (**...**) ] 按鈕，開啟 [**名稱資料行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-128">In the Properties window, click the **NameColumn** property field, and then click the ellipsis browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
7.  <span data-ttu-id="7c8ca-129">選取 [來源資料行]\*\*\*\* 清單中的 [EnglishProductName]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-129">Select **EnglishProductName** in the **Source column** list, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7c8ca-130">[NameColumn] 欄位現在會包含 **Product.EnglishProductName (WChar)** 文字。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-130">The NameColumn field now contains the text, **Product.EnglishProductName (WChar)**.</span></span>  
  
8.  <span data-ttu-id="7c8ca-131">在 [屬性視窗中，按一下 [**名稱**] 屬性欄位，然後輸入 `Product Name` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-131">In the Properties window, scroll up, click the **Name** property field, and then type `Product Name`.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="7c8ca-132">建立階層</span><span class="sxs-lookup"><span data-stu-id="7c8ca-132">Creating a Hierarchy</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="7c8ca-133">若要建立階層</span><span class="sxs-lookup"><span data-stu-id="7c8ca-133">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="7c8ca-134">將 [產品線]\*\*\*\* 屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-134">Drag the **Product Line** attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="7c8ca-135">將 [型號名稱]\*\*\*\* 屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格的 [\<new level>]\*\*\*\* 資料格中 (位於 [產品線]\*\*\*\* 層級底下)。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-135">Drag the **Model Name** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Product Line** level.</span></span>  
  
3.  <span data-ttu-id="7c8ca-136">將 `Product Name` 屬性從 [**屬性**] 窗格拖曳到 [階層 **\<new level>** ] **Hierarchies**窗格中的資料格（位於 [**模型名稱**] 層級底下）。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-136">Drag the `Product Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **Model Name** level.</span></span> <span data-ttu-id="7c8ca-137">您在上一節中已將 [產品金鑰] 重新命名為 [產品名稱]。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-137">(You renamed Product Key to Product Name in the previous section.)</span></span>  
  
4.  <span data-ttu-id="7c8ca-138">在 [**維度結構**] 索引卷**標的 [階層] 窗格中**，以滑鼠右鍵按一下階層**階層的標題**欄，按一下 [**重新命名**]，然後輸入 `Product Model Lines` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-138">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, click **Rename**, and then type `Product Model Lines`.</span></span>  
  
     <span data-ttu-id="7c8ca-139">階層的名稱現在是 `Product Model Lines` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-139">The name of the hierarchy is now `Product Model Lines`.</span></span>  
  
5.  <span data-ttu-id="7c8ca-140">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-140">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="specifying-folder-names-and-all-member-names"></a><span data-ttu-id="7c8ca-141">指定資料夾名稱和所有成員名稱</span><span class="sxs-lookup"><span data-stu-id="7c8ca-141">Specifying Folder Names and All Member Names</span></span>  
  
#### <a name="to-specify-the-folder-and-member-names"></a><span data-ttu-id="7c8ca-142">若要指定資料夾名稱和成員名稱</span><span class="sxs-lookup"><span data-stu-id="7c8ca-142">To specify the folder and member names</span></span>  
  
1.  <span data-ttu-id="7c8ca-143">在 [屬性]\*\*\*\* 窗格中，按住 CTRL 鍵，同時按一下每個屬性，藉以選取下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c8ca-143">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="7c8ca-144">**類別**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-144">**Class**</span></span>  
  
    -   <span data-ttu-id="7c8ca-145">**色彩**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-145">**Color**</span></span>  
  
    -   <span data-ttu-id="7c8ca-146">**製造天數**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-146">**Days To Manufacture**</span></span>  
  
    -   <span data-ttu-id="7c8ca-147">**Reorder Point**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-147">**Reorder Point**</span></span>  
  
    -   <span data-ttu-id="7c8ca-148">**Safety Stock Level**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-148">**Safety Stock Level**</span></span>  
  
    -   <span data-ttu-id="7c8ca-149">**大小**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-149">**Size**</span></span>  
  
    -   <span data-ttu-id="7c8ca-150">**Size Range**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-150">**Size Range**</span></span>  
  
    -   <span data-ttu-id="7c8ca-151">**Style**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-151">**Style**</span></span>  
  
    -   <span data-ttu-id="7c8ca-152">**Weight**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-152">**Weight**</span></span>  
  
2.  <span data-ttu-id="7c8ca-153">在屬性視窗的 [ **attributehierarchydisplayfolder]** ] 屬性欄位中，輸入 `Stocking` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-153">In the **AttributeHierarchyDisplayFolder** property field in the Properties window, type `Stocking`.</span></span>  
  
     <span data-ttu-id="7c8ca-154">現在您已將這些屬性分組放入單一顯示資料夾。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-154">You have now grouped these attributes into a single display folder.</span></span>  
  
3.  <span data-ttu-id="7c8ca-155">在 [屬性]\*\*\*\* 窗格中，選取下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c8ca-155">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="7c8ca-156">**Dealer Price**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-156">**Dealer Price**</span></span>  
  
    -   <span data-ttu-id="7c8ca-157">**List Price**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-157">**List Price**</span></span>  
  
    -   <span data-ttu-id="7c8ca-158">**Standard Cost**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-158">**Standard Cost**</span></span>  
  
4.  <span data-ttu-id="7c8ca-159">在屬性視窗的 [ **attributehierarchydisplayfolder]** ] 屬性資料格中，輸入 `Financial` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-159">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `Financial`.</span></span>  
  
     <span data-ttu-id="7c8ca-160">現在您已將這些屬性分組放入第二個顯示資料夾。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-160">You have now grouped these attributes into a second display folder.</span></span>  
  
5.  <span data-ttu-id="7c8ca-161">在 [屬性]\*\*\*\* 窗格中，選取下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c8ca-161">In the **Attributes** pane, select the following attributes:</span></span>  
  
    -   <span data-ttu-id="7c8ca-162">**結束日期**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-162">**End Date**</span></span>  
  
    -   <span data-ttu-id="7c8ca-163">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-163">**Start Date**</span></span>  
  
    -   <span data-ttu-id="7c8ca-164">**狀態**</span><span class="sxs-lookup"><span data-stu-id="7c8ca-164">**Status**</span></span>  
  
6.  <span data-ttu-id="7c8ca-165">在屬性視窗的 [ **attributehierarchydisplayfolder]** ] 屬性資料格中，輸入 `History` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-165">In the **AttributeHierarchyDisplayFolder** property cell in the Properties window, type `History`.</span></span>  
  
     <span data-ttu-id="7c8ca-166">現在您已將這些屬性分組放入第三個顯示資料夾。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-166">You have now grouped these attributes into a third display folder.</span></span>  
  
7.  <span data-ttu-id="7c8ca-167">`Product Model Lines`在 [階層] 窗格**Hierarchies**中選取階層，然後將屬性視窗中的 [ **AllMemberName** ] 屬性變更為 `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-167">Select the `Product Model Lines` hierarchy in the **Hierarchies** pane, and then change the **AllMemberName** property in the Properties window to `All Products`.</span></span>  
  
8.  <span data-ttu-id="7c8ca-168">按一下 [**階層] 窗格**的開放區域，然後將屬性視窗頂端的 [ **AttributeAllMemberName** ] 屬性變更為 `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-168">Click an open area of the **Hierarchies** pane, and then change the **AttributeAllMemberName** property at the top of the Properties window to `All Products`.</span></span>  
  
     <span data-ttu-id="7c8ca-169">按一下開放區域可讓您修改 [Product] 維度本身的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-169">Clicking an open area lets you modify properties of the Product dimension itself.</span></span> <span data-ttu-id="7c8ca-170">您也可以在 [屬性]\*\*\*\* 窗格中，按一下屬性清單最上方的 [Product]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-170">You could also click **Product** at the top of the attributes list in the **Attributes** pane.</span></span>  
  
9. <span data-ttu-id="7c8ca-171">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-171">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="7c8ca-172">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="7c8ca-172">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="7c8ca-173">如果基礎資料支援屬性關聯性，您就應該定義屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-173">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="7c8ca-174">定義屬性關聯性可加快維度、資料分割和查詢處理的速度。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-174">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="7c8ca-175">如需詳細資訊，請參閱 [定義屬性關聯性](multidimensional-models/attribute-relationships-define.md) 和 [屬性關聯性](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-175">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="7c8ca-176">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="7c8ca-176">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="7c8ca-177">在 [產品] 維度的 [維度設計師]\*\*\*\* 中，按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-177">In the **Dimension Designer** for the Product dimension, click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="7c8ca-178">在圖表中，以滑鼠右鍵按一下 [型號名稱]\*\*\*\* 屬性，然後按一下 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-178">In the diagram, right-click the **Model Name** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="7c8ca-179">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [模型名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-179">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="7c8ca-180">將 [相關屬性]\*\*\*\* 設定為 [產品線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-180">Set the **Related Attribute** to **Product Line**.</span></span>  
  
     <span data-ttu-id="7c8ca-181">然後，在 [關聯性類型]\*\*\*\* 清單中，保持關聯性類型設定為 [彈性]\*\*\*\* 的狀態，因為成員之間的關聯性可能會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-181">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span> <span data-ttu-id="7c8ca-182">例如，產品型號最後可能會移至不同的產品線。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-182">For example, a product model might eventually be moved to a different product line.</span></span>  
  
4.  <span data-ttu-id="7c8ca-183">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-183">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="7c8ca-184">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-184">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="reviewing-product-dimension-changes"></a><span data-ttu-id="7c8ca-185">檢閱 Product 維度變更</span><span class="sxs-lookup"><span data-stu-id="7c8ca-185">Reviewing Product Dimension Changes</span></span>  
  
#### <a name="to-review-the-product-dimension-changes"></a><span data-ttu-id="7c8ca-186">若要檢閱 Product 維度變更</span><span class="sxs-lookup"><span data-stu-id="7c8ca-186">To review the Product dimension changes</span></span>  
  
1.  <span data-ttu-id="7c8ca-187">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-187">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="7c8ca-188">當您收到 [已成功地完成部署]\*\*\*\* 訊息之後，請針對 [產品]\*\*\*\* 維度按一下 [維度設計師] \*\*\*\* 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下設計師工具列上的 [重新連接] 圖示。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-188">After you have received the **Deployment Completed Successfully** message, click the **Browser** tab of **Dimension Designer** for the **Product** dimension, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="7c8ca-189">確認 `Product Model Lines` 已在 [階層] **Hierarchy**清單中選取，然後展開 [] `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-189">Verify that `Product Model Lines` is selected in the **Hierarchy** list, and then expand `All Products`.</span></span>  
  
     <span data-ttu-id="7c8ca-190">請注意，[**全部**] 成員的名稱會顯示為 `All Products` 。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-190">Notice that the name of the **All** member appears as `All Products`.</span></span> <span data-ttu-id="7c8ca-191">這是因為您已將此階層的**AllMemberName**屬性變更為稍 `All Products` 早在課程中。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-191">This is because you changed the **AllMemberName** property for the hierarchy to `All Products` earlier in the lesson.</span></span> <span data-ttu-id="7c8ca-192">此外，[產品線]\*\*\*\* 層級的成員現在有了使用者易記名稱，而非單一字母的縮寫。</span><span class="sxs-lookup"><span data-stu-id="7c8ca-192">Also, the members of the **Product Line** level now have user-friendly names, instead of single-letter abbreviations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7c8ca-193">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="7c8ca-193">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7c8ca-194">修改日期維度</span><span class="sxs-lookup"><span data-stu-id="7c8ca-194">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c8ca-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c8ca-195">See Also</span></span>  
 <span data-ttu-id="7c8ca-196">[定義資料來源視圖中的已命名計算 &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="7c8ca-196">[Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md) </span></span>  
 <span data-ttu-id="7c8ca-197">[建立使用者定義階層](multidimensional-models/user-defined-hierarchies-create.md) </span><span class="sxs-lookup"><span data-stu-id="7c8ca-197">[Create User-Defined Hierarchies](multidimensional-models/user-defined-hierarchies-create.md) </span></span>  
 [<span data-ttu-id="7c8ca-198">設定屬性階層的 &#40;全部&#41; 層級</span><span class="sxs-lookup"><span data-stu-id="7c8ca-198">Configure the &#40;All&#41; Level for Attribute Hierarchies</span></span>](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
