---
title: 修改客戶維度 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5b5aed99-1760-4bc7-b248-52ecb0b97ebc
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd5c5c47205a89f8429b0b6f0ba55da266d5e811
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598036"
---
# <a name="modifying-the-customer-dimension"></a><span data-ttu-id="e3411-102">修改 [客戶] 維度</span><span class="sxs-lookup"><span data-stu-id="e3411-102">Modifying the Customer Dimension</span></span>
  <span data-ttu-id="e3411-103">您有許多不同方式可以增加 Cube 中維度的可用性和功能性。</span><span class="sxs-lookup"><span data-stu-id="e3411-103">There are many different ways that you can increase the usability and functionality of the dimensions in a cube.</span></span> <span data-ttu-id="e3411-104">在這個主題的工作中，您會修改 Customer 維度。</span><span class="sxs-lookup"><span data-stu-id="e3411-104">In the tasks in this topic, you modify the Customer dimension.</span></span>  
  
## <a name="renaming-attributes"></a><span data-ttu-id="e3411-105">重新命名屬性</span><span class="sxs-lookup"><span data-stu-id="e3411-105">Renaming Attributes</span></span>  
 <span data-ttu-id="e3411-106">您可以使用 [維度設計師] 的 [維度結構]\*\*\*\* 索引標籤來變更屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="e3411-106">You can change attribute names with the **Dimension Structure** tab of Dimension Designer.</span></span>  
  
#### <a name="to-rename-an-attribute"></a><span data-ttu-id="e3411-107">重新命名屬性</span><span class="sxs-lookup"><span data-stu-id="e3411-107">To rename an attribute</span></span>  
  
1.  <span data-ttu-id="e3411-108">針對 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [客戶] 維度，切換至 [維度設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-108">Switch to **Dimension Designer** for the Customer dimension in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="e3411-109">若要這樣做，請在方案總管的 [維度]\*\*\*\* 節點中，按兩下 [客戶]\*\*\*\* 維度。</span><span class="sxs-lookup"><span data-stu-id="e3411-109">To do this, double-click the **Customer** dimension in the **Dimensions** node of Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="e3411-110">在 [屬性]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [英文國家地區名稱]\*\*\*\*，然後按一下 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-110">In the **Attributes** pane, right-click **English Country Region Name**, and then click **Rename**.</span></span> <span data-ttu-id="e3411-111">將屬性的名稱變更為 `Country-Region` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-111">Change the name of the attribute to `Country-Region`.</span></span>  
  
3.  <span data-ttu-id="e3411-112">請以相同方式變更下列屬性的名稱：</span><span class="sxs-lookup"><span data-stu-id="e3411-112">Change the names of the following attributes in the same manner:</span></span>  
  
    -   <span data-ttu-id="e3411-113">**英文教育**屬性-變更為`Education`</span><span class="sxs-lookup"><span data-stu-id="e3411-113">**English Education** attribute - change to `Education`</span></span>  
  
    -   <span data-ttu-id="e3411-114">**美式職業**屬性-變更為`Occupation`</span><span class="sxs-lookup"><span data-stu-id="e3411-114">**English Occupation** attribute - change to `Occupation`</span></span>  
  
    -   <span data-ttu-id="e3411-115">**州/省名稱**屬性-變更為`State-Province`</span><span class="sxs-lookup"><span data-stu-id="e3411-115">**State Province Name** attribute - change to `State-Province`</span></span>  
  
4.  <span data-ttu-id="e3411-116">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-116">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="creating-a-hierarchy"></a><span data-ttu-id="e3411-117">建立階層</span><span class="sxs-lookup"><span data-stu-id="e3411-117">Creating a Hierarchy</span></span>  
 <span data-ttu-id="e3411-118">您可以將屬性從 [屬性]\*\*\*\* 窗格拖曳到 [階層]\*\*\*\* 窗格，藉以建立新的階層。</span><span class="sxs-lookup"><span data-stu-id="e3411-118">You can create a new hierarchy by dragging an attribute from the **Attributes** pane to the **Hierarchies** pane.</span></span>  
  
#### <a name="to-create-a-hierarchy"></a><span data-ttu-id="e3411-119">若要建立階層</span><span class="sxs-lookup"><span data-stu-id="e3411-119">To create a hierarchy</span></span>  
  
1.  <span data-ttu-id="e3411-120">將 `Country-Region` 屬性從 [**屬性**] 窗格拖曳到**Hierarchies** [階層] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="e3411-120">Drag the `Country-Region` attribute from the **Attributes** pane into the **Hierarchies** pane.</span></span>  
  
2.  <span data-ttu-id="e3411-121">將 `State-Province` 屬性從 [**屬性**] 窗格拖曳到 [階層 **\<new level>** ] **Hierarchies**窗格中的資料格（位於 `Country-Region` 層級底下）。</span><span class="sxs-lookup"><span data-stu-id="e3411-121">Drag the `State-Province` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `Country-Region` level.</span></span>  
  
3.  <span data-ttu-id="e3411-122">將**City**屬性從 [**屬性**] 窗格拖曳到 [階層 **\<new level>** ] **Hierarchies**窗格中的資料格（位於 `State-Province` 層級底下）。</span><span class="sxs-lookup"><span data-stu-id="e3411-122">Drag the **City** attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the `State-Province` level.</span></span>  
  
4.  <span data-ttu-id="e3411-123">在 [**維度結構**] 索引卷**標的 [階層] 窗格中**，以滑鼠右鍵按一下階層**階層的標題**欄，選取 [**重新命名**]，然後輸入 `Customer Geography` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-123">In the **Hierarchies** pane of the **Dimension Structure** tab, right-click the title bar of the **Hierarchy** hierarchy, select **Rename**, and then type `Customer Geography`.</span></span>  
  
     <span data-ttu-id="e3411-124">階層的名稱現在是 `Customer Geography` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-124">The name of the hierarchy is now `Customer Geography`.</span></span>  
  
5.  <span data-ttu-id="e3411-125">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-125">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="adding-a-named-calculation"></a><span data-ttu-id="e3411-126">加入具名計算</span><span class="sxs-lookup"><span data-stu-id="e3411-126">Adding a Named Calculation</span></span>  
 <span data-ttu-id="e3411-127">具名計算是以導出資料行表示的 SQL 運算式，您可以將它加入資料來源檢視的資料表中。</span><span class="sxs-lookup"><span data-stu-id="e3411-127">You can add a named calculation, which is a SQL expression that is represented as a calculated column, to a table in a data source view.</span></span> <span data-ttu-id="e3411-128">這個運算式以資料表的資料行呈現及運作。</span><span class="sxs-lookup"><span data-stu-id="e3411-128">The expression appears and behaves as a column in the table.</span></span> <span data-ttu-id="e3411-129">具名計算可讓您延伸資料來源檢視中現有資料表的關聯式結構描述，而不必修改基礎資料來源中的資料表。</span><span class="sxs-lookup"><span data-stu-id="e3411-129">Named calculations let you extend the relational schema of existing tables in a data source view without modifying the table in the underlying data source.</span></span> <span data-ttu-id="e3411-130">如需詳細資訊，請參閱[在資料來源 View 中定義指名的計算 &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span><span class="sxs-lookup"><span data-stu-id="e3411-130">For more information, see [Define Named Calculations in a Data Source View &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)</span></span>  
  
#### <a name="to-add-a-named-calculation"></a><span data-ttu-id="e3411-131">加入具名計算</span><span class="sxs-lookup"><span data-stu-id="e3411-131">To add a named calculation</span></span>  
  
1.  <span data-ttu-id="e3411-132">在方案總管的**資料來源 Views**資料夾中按兩下，以開啟\*\* [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012\*\*資料來源 view。</span><span class="sxs-lookup"><span data-stu-id="e3411-132">Open the **[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** data source view by double-clicking it in the **Data Source Views** folder in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="e3411-133">在左側的 [資料表]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [客戶]\*\*\*\*，然後按一下 [新增具名計算]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-133">In the **Tables** pane on the left, right-click **Customer**, and then click **New Named Calculation**.</span></span>  
  
3.  <span data-ttu-id="e3411-134">在 [**建立命名計算**] 對話方塊中，于 [資料行名稱] 方塊中輸入，然後在 `FullName` [運算式] 方塊中輸入或複製並貼上下列**Column name** `CASE` 語句： **Expression**</span><span class="sxs-lookup"><span data-stu-id="e3411-134">In the **Create Named Calculation** dialog box, type `FullName` in the **Column name** box, and then type or copy and paste the following `CASE` statement in the **Expression** box:</span></span>  
  
    ```  
    CASE  
       WHEN MiddleName IS NULL THEN  
       FirstName + ' ' + LastName  
       ELSE  
       FirstName + ' ' + MiddleName + ' ' + LastName  
    END  
    ```  
  
     <span data-ttu-id="e3411-135">`CASE`語句會將**FirstName**、 **MiddleName**和**LastName**資料行串連成單一資料行，您將在 [客戶] 維度中用來當做**customer**屬性的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="e3411-135">The `CASE` statement concatenates the **FirstName**, **MiddleName**, and **LastName** columns into a single column that you will use in the Customer dimension as the displayed name for the **Customer** attribute.</span></span>  
  
4.  <span data-ttu-id="e3411-136">按一下 [確定]\*\*\*\*，然後展開 [資料表]\*\*\*\* 窗格中的 [客戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-136">Click **OK**, and then expand **Customer** in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="e3411-137">`FullName`已命名的計算會出現在 Customer 資料表的資料行清單中，並以圖示表示它是名為的計算。</span><span class="sxs-lookup"><span data-stu-id="e3411-137">The `FullName` named calculation appears in the list of columns in the Customer table, with an icon that indicates that it is a named calculation.</span></span>  
  
5.  <span data-ttu-id="e3411-138">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-138">On the **File** menu, click **Save All**.</span></span>  
  
6.  <span data-ttu-id="e3411-139">在 [資料表]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [客戶]\*\*\*\*，然後按一下 [瀏覽資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-139">In the **Tables** pane, right-click **Customer**, and then click **Explore Data**.</span></span>  
  
7.  <span data-ttu-id="e3411-140">檢閱 [瀏覽客戶資料表]\*\*\*\* 檢視中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="e3411-140">Review the last column in the **Explore Customer Table** view.</span></span>  
  
     <span data-ttu-id="e3411-141">請注意， `FullName` 資料行會出現在 [資料來源] 視圖中，將資料從基礎資料來源中的數個數據行正確串連，而不需要修改原始資料來源。</span><span class="sxs-lookup"><span data-stu-id="e3411-141">Notice that the `FullName` column appears in the data source view, correctly concatenating data from several columns from the underlying data source and without modifying the original data source.</span></span>  
  
8.  <span data-ttu-id="e3411-142">關閉 [瀏覽 Customer 資料表]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e3411-142">Close the **Explore Customer Table** tab.</span></span>  
  
## <a name="using-the-named-calculation-for-member-names"></a><span data-ttu-id="e3411-143">針對成員名稱使用具名計算</span><span class="sxs-lookup"><span data-stu-id="e3411-143">Using the Named Calculation for Member Names</span></span>  
 <span data-ttu-id="e3411-144">在資料來源檢視中建立具名計算之後，您就可以使用此具名計算當做屬性 (Attribute) 的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="e3411-144">After you have created a named calculation in the data source view, you can use the named calculation as a property of an attribute.</span></span>  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a><span data-ttu-id="e3411-145">針對成員名稱使用具名計算</span><span class="sxs-lookup"><span data-stu-id="e3411-145">To use the named calculation for member names</span></span>  
  
1.  <span data-ttu-id="e3411-146">針對 [客戶] 維度切換到維度設計師。</span><span class="sxs-lookup"><span data-stu-id="e3411-146">Switch to Dimension Designer for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="e3411-147">在 [維度結構]\*\*\*\* 索引標籤的 [屬性]\*\*\*\* 窗格中，按一下 [客戶索引鍵]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3411-147">In the **Attributes** pane of the **Dimension Structure** tab, click the **Customer Key** attribute.</span></span>  
  
3.  <span data-ttu-id="e3411-148">開啟 [屬性] 視窗，然後按一下標題列上的 [自動隱藏]\*\*\*\* 按鈕，如此它就會保持開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="e3411-148">Open the Properties window and click the **Auto Hide** button on the title bar so that it stays open.</span></span>  
  
4.  <span data-ttu-id="e3411-149">在 [**名稱**] 屬性欄位中，輸入 `Full Name` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-149">In the **Name** property field, type `Full Name`.</span></span>  
  
5.  <span data-ttu-id="e3411-150">按一下底部的 [ **NameColumn** ] 屬性欄位，然後按一下 [流覽 (**...** ]) ] 按鈕，開啟 [名稱資料**行**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e3411-150">Click in the **NameColumn** property field at the bottom, and then click the browse (**...**) button to open the **Name Column** dialog box.</span></span>  
  
6.  <span data-ttu-id="e3411-151">選取 `FullName` [**來源資料行**] 清單底部的，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e3411-151">Select `FullName` at the bottom of the **Source column** list, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="e3411-152">在 [維度結構] 索引標籤中，將 `Full Name` 屬性從 [**屬性**] 窗格拖曳到 [階層 **\<new level>** ] 窗格中 [ **City** ] 層級下的資料格。 **Hierarchies**</span><span class="sxs-lookup"><span data-stu-id="e3411-152">In the Dimensions Structure tab, drag the `Full Name` attribute from the **Attributes** pane into the **\<new level>** cell in the **Hierarchies** pane, underneath the **City** level.</span></span>  
  
8.  <span data-ttu-id="e3411-153">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-153">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-display-folders"></a><span data-ttu-id="e3411-154">定義顯示資料夾</span><span class="sxs-lookup"><span data-stu-id="e3411-154">Defining Display Folders</span></span>  
 <span data-ttu-id="e3411-155">您可以使用顯示資料夾，將使用者和屬性階層分組放到資料夾結構中，以便提高可用性。</span><span class="sxs-lookup"><span data-stu-id="e3411-155">You can use display folders to group user and attribute hierarchies into folder structures to increase usability.</span></span>  
  
#### <a name="to-define-display-folders"></a><span data-ttu-id="e3411-156">若要定義顯示資料夾</span><span class="sxs-lookup"><span data-stu-id="e3411-156">To define display folders</span></span>  
  
1.  <span data-ttu-id="e3411-157">針對 [客戶] 維度開啟 [維度結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e3411-157">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="e3411-158">在 [屬性]\*\*\*\* 窗格中，按住 CTRL 鍵，同時按一下每個屬性，藉以選取下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e3411-158">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="e3411-159">**城市**</span><span class="sxs-lookup"><span data-stu-id="e3411-159">**City**</span></span>  
  
    -   `Country-Region`  
  
    -   <span data-ttu-id="e3411-160">**郵遞區號**</span><span class="sxs-lookup"><span data-stu-id="e3411-160">**Postal Code**</span></span>  
  
    -   `State-Province`  
  
3.  <span data-ttu-id="e3411-161">在 [屬性視窗中，按一下頂端的 [ **attributehierarchydisplayfolder]** ] 屬性欄位， (您可能需要指向它才能查看完整名稱) ，然後輸入 `Location` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-161">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top (you might need to point to it to see the full name), and then type `Location`.</span></span>  
  
4.  <span data-ttu-id="e3411-162">在 [**階層] 窗格**中，按一下 [] `Customer Geography` ，然後在右邊的 [屬性視窗中，選取 `Location` 做為**DisplayFolder**屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e3411-162">In the **Hierarchies** pane, click `Customer Geography`, and then in the Properties window on the right, select `Location` as the value of the **DisplayFolder** property.</span></span>  
  
5.  <span data-ttu-id="e3411-163">在 [屬性]\*\*\*\* 窗格中，按住 CTRL 鍵，同時按一下每個屬性，藉以選取下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e3411-163">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="e3411-164">**Commute Distance**</span><span class="sxs-lookup"><span data-stu-id="e3411-164">**Commute Distance**</span></span>  
  
    -   `Education`  
  
    -   <span data-ttu-id="e3411-165">**性別**</span><span class="sxs-lookup"><span data-stu-id="e3411-165">**Gender**</span></span>  
  
    -   <span data-ttu-id="e3411-166">**House Owner Flag**</span><span class="sxs-lookup"><span data-stu-id="e3411-166">**House Owner Flag**</span></span>  
  
    -   <span data-ttu-id="e3411-167">**Marital Status**</span><span class="sxs-lookup"><span data-stu-id="e3411-167">**Marital Status**</span></span>  
  
    -   <span data-ttu-id="e3411-168">**Number Cars Owned**</span><span class="sxs-lookup"><span data-stu-id="e3411-168">**Number Cars Owned**</span></span>  
  
    -   <span data-ttu-id="e3411-169">**Number Children At Home**</span><span class="sxs-lookup"><span data-stu-id="e3411-169">**Number Children At Home**</span></span>  
  
    -   `Occupation`  
  
    -   <span data-ttu-id="e3411-170">**Total Children**</span><span class="sxs-lookup"><span data-stu-id="e3411-170">**Total Children**</span></span>  
  
    -   <span data-ttu-id="e3411-171">**Yearly Income**</span><span class="sxs-lookup"><span data-stu-id="e3411-171">**Yearly Income**</span></span>  
  
6.  <span data-ttu-id="e3411-172">在 [屬性視窗中，按一下頂端的 [ **attributehierarchydisplayfolder]** ] 屬性欄位，然後輸入 `Demographic` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-172">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field at the top, and then type `Demographic`.</span></span>  
  
7.  <span data-ttu-id="e3411-173">在 [屬性]\*\*\*\* 窗格中，按住 CTRL 鍵，同時按一下每個屬性，藉以選取下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e3411-173">In the **Attributes** pane, select the following attributes by holding down the CTRL key while clicking each of them:</span></span>  
  
    -   <span data-ttu-id="e3411-174">**電子郵件地址**</span><span class="sxs-lookup"><span data-stu-id="e3411-174">**Email Address**</span></span>  
  
    -   <span data-ttu-id="e3411-175">**來電**</span><span class="sxs-lookup"><span data-stu-id="e3411-175">**Phone**</span></span>  
  
8.  <span data-ttu-id="e3411-176">在 [屬性視窗中，按一下 [ **attributehierarchydisplayfolder]** ] 屬性欄位，然後輸入 `Contacts` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-176">In the Properties window, click the **AttributeHierarchyDisplayFolder** property field and type `Contacts`.</span></span>  
  
9. <span data-ttu-id="e3411-177">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-177">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-composite-keycolumns"></a><span data-ttu-id="e3411-178">定義複合 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="e3411-178">Defining Composite KeyColumns</span></span>  
 <span data-ttu-id="e3411-179">[KeyColumns]\*\*\*\* 屬性 (property) 包含代表屬性 (attribute) 之索引鍵的一或多個資料行。</span><span class="sxs-lookup"><span data-stu-id="e3411-179">The **KeyColumns** property contains the column or columns that represent the key for the attribute.</span></span> <span data-ttu-id="e3411-180">在這一課，您會建立**城市**和屬性的複合索引鍵 `State-Province` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-180">In this lesson, you create a composite key for the **City** and `State-Province` attributes.</span></span> <span data-ttu-id="e3411-181">當您需要唯一識別某個屬性時，複合索引鍵便很有用。</span><span class="sxs-lookup"><span data-stu-id="e3411-181">Composite keys can be helpful when you need to uniquely identify an attribute.</span></span> <span data-ttu-id="e3411-182">例如，當您稍後在本教學課程中定義屬性關聯性時， **City**屬性必須唯一識別 `State-Province` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3411-182">For example, when you define attribute relationships later in this tutorial, a **City** attribute must uniquely identify a `State-Province` attribute.</span></span> <span data-ttu-id="e3411-183">不過，不同省份可能會有許多相同名稱的縣 (市) 存在。</span><span class="sxs-lookup"><span data-stu-id="e3411-183">However, there could be several cities with the same name in different states.</span></span> <span data-ttu-id="e3411-184">因此，您將建立由 [縣 (市)]\*\*\*\* 屬性之 [StateProvinceName]\*\*\*\* 和 [City]\*\*\*\* 資料行所組成的複合索引鍵。</span><span class="sxs-lookup"><span data-stu-id="e3411-184">For this reason, you will create a composite key that is composed of the **StateProvinceName** and **City** columns for the **City** attribute.</span></span> <span data-ttu-id="e3411-185">如需詳細資訊，請參閱 [修改屬性 (Attribute) 的 KeyColumn 屬性 (Property)](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md)。</span><span class="sxs-lookup"><span data-stu-id="e3411-185">For more information, see [Modify the KeyColumn Property of an Attribute](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-city-attribute"></a><span data-ttu-id="e3411-186">針對 [縣 (市)] 屬性定義複合 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="e3411-186">To define composite KeyColumns for the City attribute</span></span>  
  
1.  <span data-ttu-id="e3411-187">針對 [客戶] 維度開啟 [維度結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e3411-187">Open the **Dimension Structure** tab for the Customer dimension.</span></span>  
  
2.  <span data-ttu-id="e3411-188">在 [屬性]\*\*\*\* 窗格中，按一下 [縣 (市)]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3411-188">In the **Attributes** pane, click the **City** attribute.</span></span>  
  
3.  <span data-ttu-id="e3411-189">在 [屬性]\*\*\*\* 視窗中靠近底部的 [KeyColumns]\*\*\*\* 欄位中按一下，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-189">In the **Properties** window, click in the **KeyColumns** field near the bottom, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="e3411-190">在 [索引鍵資料行]\*\*\*\* 對話方塊的 [可用的資料行]\*\*\*\* 清單中，選取 [StateProvinceName]\*\*\*\* 資料行，然後按一下 [>]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-190">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **StateProvinceName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="e3411-191">[City]\*\*\*\* 和 [StateProvinceName]\*\*\*\* 資料行現在會顯示在 [索引鍵資料行]\*\*\*\* 清單中。</span><span class="sxs-lookup"><span data-stu-id="e3411-191">The **City** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="e3411-192">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e3411-192">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="e3411-193">若要設定 [縣 (市)]\*\*\*\* 屬性 (attribute) 的 [NameColumn]\*\*\*\* 屬性 (property)，請按一下 [屬性] (property) 視窗中的 [NameColumn]\*\*\*\* 欄位，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-193">To set the **NameColumn** property of the **City** attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="e3411-194">在 [名稱資料行]\*\*\*\* 對話方塊的 [來源資料行]\*\*\*\* 清單中，選取 [City]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-194">In the **Name Column** dialog box, in the **Source column** list, select **City**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="e3411-195">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-195">On the **File** menu, click **Save All**.</span></span>  
  
#### <a name="to-define-composite-keycolumns-for-the-state-province-attribute"></a><span data-ttu-id="e3411-196">針對 [省份] 屬性定義複合 KeyColumns</span><span class="sxs-lookup"><span data-stu-id="e3411-196">To define composite KeyColumns for the State-Province attribute</span></span>  
  
1.  <span data-ttu-id="e3411-197">請確定 [客戶] 維度的 [維度結構]\*\*\*\* 索引標籤為開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="e3411-197">Make sure the **Dimension Structure** tab for the Customer dimension is open.</span></span>  
  
2.  <span data-ttu-id="e3411-198">在 [**屬性**] 窗格中，按一下 `State-Province` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3411-198">In the **Attributes** pane, click the `State-Province` attribute.</span></span>  
  
3.  <span data-ttu-id="e3411-199">在 [屬性]\*\*\*\* 視窗的 [KeyColumns]\*\*\*\* 欄位中按一下，然後按一下瀏覽 (**...**) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-199">In the **Properties** window, click in the **KeyColumns** field, and then click the browse (**...**) button.</span></span>  
  
4.  <span data-ttu-id="e3411-200">在 [索引鍵資料行]\*\*\*\* 對話方塊的 [可用的資料行]\*\*\*\* 清單中，選取 [EnglishCountryRegionName]\*\*\*\* 資料行，然後按一下 [>]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-200">In the **Key Columns** dialog box, in the **Available Columns** list, select the column **EnglishCountryRegionName**, and then click the **>** button.</span></span>  
  
     <span data-ttu-id="e3411-201">[EnglishCountryRegionName]\*\*\*\* 和 [StateProvinceName]\*\*\*\* 資料行現在會顯示在 [索引鍵資料行]\*\*\*\* 清單中。</span><span class="sxs-lookup"><span data-stu-id="e3411-201">The **EnglishCountryRegionName** and **StateProvinceName** columns are now displayed in the **Key Columns** list.</span></span>  
  
5.  <span data-ttu-id="e3411-202">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e3411-202">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="e3411-203">若要設定屬性的**namecolumn**屬性 `State-Province` ，請按一下 [屬性視窗中的 [ **namecolumn** ] 欄位，然後按一下 [流覽 (**...** ]) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-203">To set the **NameColumn** property of the `State-Province` attribute, click the **NameColumn** field in the Properties window, and then click the browse (**...**) button.</span></span>  
  
7.  <span data-ttu-id="e3411-204">在 [名稱資料行]\*\*\*\* 對話方塊的 [來源資料行]\*\*\*\* 清單中，選取 [StateProvinceName]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-204">In the **Name Column** dialog box, in the **Source column** list, select **StateProvinceName**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="e3411-205">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-205">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships"></a><span data-ttu-id="e3411-206">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="e3411-206">Defining Attribute Relationships</span></span>  
 <span data-ttu-id="e3411-207">如果基礎資料支援屬性關聯性，您就應該定義屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="e3411-207">If the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="e3411-208">定義屬性關聯性可加快維度、資料分割和查詢處理的速度。</span><span class="sxs-lookup"><span data-stu-id="e3411-208">Defining attribute relationships speeds up dimension, partition, and query processing.</span></span> <span data-ttu-id="e3411-209">如需詳細資訊，請參閱 [定義屬性關聯性](multidimensional-models/attribute-relationships-define.md) 和 [屬性關聯性](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="e3411-209">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
#### <a name="to-define-attribute-relationships"></a><span data-ttu-id="e3411-210">定義屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="e3411-210">To define attribute relationships</span></span>  
  
1.  <span data-ttu-id="e3411-211">在 [客戶] 維度的 [**維度設計師**] 中，按一下 [**屬性關聯**性] 索引標籤。您可能需要等待。</span><span class="sxs-lookup"><span data-stu-id="e3411-211">In the **Dimension Designer** for the Customer dimension, click the **Attribute Relationships** tab. You might need to wait.</span></span>  
  
2.  <span data-ttu-id="e3411-212">在圖表中，以滑鼠右鍵按一下 [縣 (市)]\*\*\*\* 屬性，然後按一下 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-212">In the diagram, right-click the **City** attribute, and then click **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="e3411-213">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [縣 (市)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-213">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="e3411-214">將**相關屬性**設定為 `State-Province` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-214">Set the **Related Attribute** to `State-Province`.</span></span>  
  
4.  <span data-ttu-id="e3411-215">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-215">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
     <span data-ttu-id="e3411-216">此關聯性類型是 [固定]\*\*\*\*，因為成員之間的關聯性不會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="e3411-216">The relationship type is **Rigid** because relationships between the members will not change over time.</span></span> <span data-ttu-id="e3411-217">例如，某個縣 (市) 成為不同省份一部分的情況並不常見。</span><span class="sxs-lookup"><span data-stu-id="e3411-217">For example, it would be unusual for a city to become part of a different state or province.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="e3411-218">在圖表中，以滑鼠右鍵按一下 `State-Province` 屬性，然後選取 [**新增屬性關聯**性]。</span><span class="sxs-lookup"><span data-stu-id="e3411-218">In the diagram, right-click the `State-Province` attribute and then select **New Attribute Relationship**.</span></span>  
  
7.  <span data-ttu-id="e3411-219">在 [**建立屬性關聯**性] 對話方塊中，[**來源屬性**] 是 `State-Province` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-219">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is `State-Province`.</span></span> <span data-ttu-id="e3411-220">將**相關屬性**設定為 `Country-Region` 。</span><span class="sxs-lookup"><span data-stu-id="e3411-220">Set the **Related Attribute** to `Country-Region`.</span></span>  
  
8.  <span data-ttu-id="e3411-221">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-221">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. <span data-ttu-id="e3411-222">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e3411-222">Click **OK**.</span></span>  
  
10. <span data-ttu-id="e3411-223">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-223">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="deploying-changes-processing-the-objects-and-viewing-the-changes"></a><span data-ttu-id="e3411-224">部署變更、處理物件及檢視變更</span><span class="sxs-lookup"><span data-stu-id="e3411-224">Deploying Changes, Processing the Objects, and Viewing the Changes</span></span>  
 <span data-ttu-id="e3411-225">在變更屬性和階層之後，您必須部署變更及重新處理相關物件，然後才可以檢視變更。</span><span class="sxs-lookup"><span data-stu-id="e3411-225">After you have changed attributes and hierarchies, you must deploy the changes and reprocess the related objects before you can view the changes.</span></span>  
  
#### <a name="to-deploy-the-changes-process-the-objects-and-view-the-changes"></a><span data-ttu-id="e3411-226">部署變更、處理物件及檢視變更</span><span class="sxs-lookup"><span data-stu-id="e3411-226">To deploy the changes, process the objects, and view the changes</span></span>  
  
1.  <span data-ttu-id="e3411-227">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-227">On the **Build** menu of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
2.  <span data-ttu-id="e3411-228">當您收到 [已成功地完成部署]\*\*\*\* 訊息之後，請針對 [客戶] 維度按一下 [維度設計師] 的 [瀏覽器]\*\*\*\* 索引標籤，然後按一下設計師工具列左側的 [重新連接] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-228">After you receive the **Deployment Completed Successfully** message, click the **Browser** tab of Dimension Designer for the Customer dimension, and then click the Reconnect button on the left side of the toolbar of the designer.</span></span>  
  
3.  <span data-ttu-id="e3411-229">確認 `Customer Geography` 已在 [階層] **Hierarchy**清單中選取，然後在瀏覽器窗格中展開 **[全部**]，展開 [**澳大利亞**]，展開 [**新南威爾士**]，然後展開 [ **Coffs Harbour**]。</span><span class="sxs-lookup"><span data-stu-id="e3411-229">Verify that `Customer Geography` is selected in the **Hierarchy** list, and then in the browser pane, expand **All**, expand **Australia**, expand **New South Wales**, and then expand **Coffs Harbour**.</span></span>  
  
     <span data-ttu-id="e3411-230">瀏覽器就會顯示該縣 (市) 的客戶。</span><span class="sxs-lookup"><span data-stu-id="e3411-230">The browser displays the customers in the city.</span></span>  
  
4.  <span data-ttu-id="e3411-231">針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 切換至 [Cube 設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-231">Switch to **Cube Designer** for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span> <span data-ttu-id="e3411-232">若要這樣做，請在**方案總管**的 [Cube]\*\*\*\* 節點中，按兩下 [Analysis Services 教學課程]\*\*\*\* Cube。</span><span class="sxs-lookup"><span data-stu-id="e3411-232">To do this, double-click the **Analysis Services Tutorial** cube in the **Cubes** node of **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="e3411-233">按一下 [瀏覽器]\*\*\*\* 索引標籤，然後按一下設計師工具列上的 [重新連接] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e3411-233">Click the **Browser** tab, and then click the Reconnect button on the toolbar of the designer.</span></span>  
  
6.  <span data-ttu-id="e3411-234">在 [量值群組]\*\*\*\* 窗格中，展開 [客戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e3411-234">In the **Measure Group** pane, expand **Customer**.</span></span>  
  
     <span data-ttu-id="e3411-235">請注意，出現在 [客戶] 底下的只有顯示資料夾和不含顯示資料夾值的屬性，而非冗長的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="e3411-235">Notice that instead of a long list of attributes, only the display folders and the attributes that do not have display folder values appear underneath Customer.</span></span>  
  
7.  <span data-ttu-id="e3411-236">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="e3411-236">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e3411-237">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="e3411-237">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e3411-238">修改產品維度</span><span class="sxs-lookup"><span data-stu-id="e3411-238">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
  
## <a name="see-also"></a><span data-ttu-id="e3411-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3411-239">See Also</span></span>  
 <span data-ttu-id="e3411-240">[維度屬性屬性參考](multidimensional-models/dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e3411-240">[Dimension Attribute Properties Reference](multidimensional-models/dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="e3411-241">[從維度中移除屬性](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="e3411-241">[Remove an Attribute from a Dimension](multidimensional-models/attribute-properties-remove-an-attribute-from-a-dimension.md) </span></span>  
 <span data-ttu-id="e3411-242">[重新命名屬性](multidimensional-models/attribute-properties-rename-an-attribute.md) </span><span class="sxs-lookup"><span data-stu-id="e3411-242">[Rename an Attribute](multidimensional-models/attribute-properties-rename-an-attribute.md) </span></span>  
 [<span data-ttu-id="e3411-243">在資料來源檢視中定義具名計算 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e3411-243">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
