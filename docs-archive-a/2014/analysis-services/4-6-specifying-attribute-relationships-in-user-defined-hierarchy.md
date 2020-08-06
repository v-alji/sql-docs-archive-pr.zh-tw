---
title: 在使用者自訂階層的屬性之間指定屬性關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 456c2a47-d395-45f9-9efa-89f3fa2ac621
author: minewiskan
ms.author: owend
ms.openlocfilehash: dc2fa03f72039aedd16c82b86ce0dd41b8f59702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592359"
---
# <a name="specifying-attribute-relationships-between-attributes-in-a-user-defined-hierarchy"></a><span data-ttu-id="07ca7-102">在使用者定義階層的屬性之間指定屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="07ca7-102">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>
  <span data-ttu-id="07ca7-103">如同您在這個教學課程中已學到的，您可以將屬性階層組織成使用者階層內的層級，在 Cube 中為使用者提供導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="07ca7-103">As you have already learned in this tutorial, you can organize attribute hierarchies into levels within user hierarchies to provide navigation paths for users in a cube.</span></span> <span data-ttu-id="07ca7-104">使用者階層可代表自然階層，例如縣 (市)、省份和國家 (地區)，或只代表導覽路徑，例如員工姓名、職稱和部門名稱。</span><span class="sxs-lookup"><span data-stu-id="07ca7-104">A user hierarchy can represent a natural hierarchy, such as city, state, and country, or can just represent a navigation path, such as employee name, title, and department name.</span></span> <span data-ttu-id="07ca7-105">對於導覽階層的使用者而言，這兩種類型的使用者階層是一樣的。</span><span class="sxs-lookup"><span data-stu-id="07ca7-105">To the user navigating a hierarchy, these two types of user hierarchies are the same.</span></span>  
  
 <span data-ttu-id="07ca7-106">透過自然階層，當您在構成層級的屬性之間定義屬性關聯性時， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 可使用一個屬性的彙總來取得相關屬性的結果。</span><span class="sxs-lookup"><span data-stu-id="07ca7-106">With a natural hierarchy, if you define attribute relationships between the attributes that make up the levels, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] can use an aggregation from one attribute to obtain the results from a related attribute.</span></span> <span data-ttu-id="07ca7-107">如果屬性之間沒有定義關聯性， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 將從索引鍵屬性中彙總所有非索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-107">If there are no defined relationships between attributes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] will aggregate all non-key attributes from the key attribute.</span></span> <span data-ttu-id="07ca7-108">因此，如果基礎資料支援屬性關聯性，您就應該定義屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-108">Therefore, if the underlying data supports it, you should define attribute relationships between attributes.</span></span> <span data-ttu-id="07ca7-109">定義屬性關聯性可改善維度、資料分割和查詢處理效能。</span><span class="sxs-lookup"><span data-stu-id="07ca7-109">Defining attribute relationships improves dimension, partition, and query processing performance.</span></span> <span data-ttu-id="07ca7-110">如需詳細資訊，請參閱 [定義屬性關聯性](multidimensional-models/attribute-relationships-define.md) 和 [屬性關聯性](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="07ca7-110">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [Attribute Relationships](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).</span></span>  
  
 <span data-ttu-id="07ca7-111">當您定義屬性關聯性時，可以指定彈性或固定的關聯性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-111">When you define attribute relationships, you can specify that the relationship is either flexible or rigid.</span></span> <span data-ttu-id="07ca7-112">如果您定義固定關聯性，當維度更新時， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會保留彙總。</span><span class="sxs-lookup"><span data-stu-id="07ca7-112">If you define a relationship as rigid, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] retains aggregations when the dimension is updated.</span></span> <span data-ttu-id="07ca7-113">如果定義為固定的關聯性實際上有所變更，除非已完全處理維度，否則在處理期間， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-113">If a relationship that is defined as rigid actually changes, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates an error during processing unless the dimension is fully processed.</span></span> <span data-ttu-id="07ca7-114">指定適當的關聯性和關聯性屬性可增加查詢和處理效能。</span><span class="sxs-lookup"><span data-stu-id="07ca7-114">Specifying the appropriate relationships and relationship properties increases query and processing performance.</span></span> <span data-ttu-id="07ca7-115">如需詳細資訊，請參閱 [定義屬性關聯性](multidimensional-models/attribute-relationships-define.md)和 [使用者階層屬性](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="07ca7-115">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md), and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 <span data-ttu-id="07ca7-116">在這個主題的工作中，您會在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案中，為自然使用者階層中的屬性定義屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-116">In the tasks in this topic, you define attribute relationships for the attributes in the natural user hierarchies in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="07ca7-117">這些包括 [客戶]\*\*\*\* 維度中的 [客戶地理位置]\*\*\*\* 階層、[銷售領域]\*\*\*\* 維度中的 [銷售領域]\*\*\*\* 階層、[產品]\*\*\*\* 維度中的 [產品型號線]\*\*\*\* 階層，以及 [日期]\*\*\*\* 維度中的 [會計日期]\*\*\*\* 和 [日曆日期]\*\*\*\* 階層。</span><span class="sxs-lookup"><span data-stu-id="07ca7-117">These include the **Customer Geography** hierarchy in the **Custome**r dimension, the **Sales Territory** hierarchy in the **Sales Territory** dimension, the **Product Model** Lines hierarchy in the **Product** dimension, and the **Fiscal Date** and **Calendar Date** hierarchies in the **Date** dimension.</span></span> <span data-ttu-id="07ca7-118">這些使用者階層全都是自然階層。</span><span class="sxs-lookup"><span data-stu-id="07ca7-118">These user hierarchies are all natural hierarchies.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-customer-geography-hierarchy"></a><span data-ttu-id="07ca7-119">在 [客戶地理位置] 階層中定義屬性的屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="07ca7-119">Defining Attribute Relationships for Attributes in the Customer Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="07ca7-120">針對 [客戶] 維度切換到 [維度設計師]，然後按一下 [維度結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-120">Switch to Dimension Designer for the Customer dimension, and then click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="07ca7-121">在 [階層]\*\*\*\* 窗格中，請注意 [客戶地理位置]\*\*\*\* 使用者定義階層中的層級。</span><span class="sxs-lookup"><span data-stu-id="07ca7-121">In the **Hierarchies** pane, notice the levels in the **Customer Geography** user-defined hierarchy.</span></span> <span data-ttu-id="07ca7-122">這個階層目前只是使用者的向下鑽研路徑，因為您尚未定義任何層級或屬性之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-122">This hierarchy is currently just a drill-down path for users, as no relationship between levels or attributes have been defined.</span></span>  
  
2.  <span data-ttu-id="07ca7-123">按一下 **[屬性關聯性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-123">Click the **Attribute Relationships** tab.</span></span>  
  
     <span data-ttu-id="07ca7-124">請注意，有四種屬性關聯性會將 [地理位置]\*\*\*\* 資料表的非索引鍵屬性連結到 [地理位置]\*\*\*\* 資料表的索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-124">Notice the four attribute relationships that link the non-key attributes from the **Geography** table to the key attribute from the **Geography** table.</span></span> <span data-ttu-id="07ca7-125">[地理位置]\*\*\*\* 屬性與 [全名]\*\*\*\* 屬性相關。</span><span class="sxs-lookup"><span data-stu-id="07ca7-125">The **Geography** attribute is related to the **Full Name** attribute.</span></span> <span data-ttu-id="07ca7-126">[郵遞區號]\*\*\*\* 屬性會透過 [地理位置]\*\*\*\* 屬性間接連結到 [全名]\*\*\*\* 屬性，因為 [郵遞區號]\*\*\*\* 會連結到 [地理位置]\*\*\*\* 屬性，而 [地理位置]\*\*\*\* 屬性則連結到 [全名]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-126">The **Postal Code** attribute is indirectly linked to the **Full Name** attribute through the **Geography** attribute, because the **Postal Code** is linked to the **Geography** attribute and the **Geography** attribute is linked to the **Full Name** attribute.</span></span> <span data-ttu-id="07ca7-127">接著，我們將變更屬性關聯性，如此它們就不會使用 [地理位置]\*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-127">Next, we will change the attribute relationships so that they do not use the **Geography** attribute.</span></span>  
  
3.  <span data-ttu-id="07ca7-128">在圖表中，以滑鼠右鍵按一下 [全名]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-128">In the diagram, right-click the **Full Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
4.  <span data-ttu-id="07ca7-129">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [全名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-129">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Full Name**.</span></span> <span data-ttu-id="07ca7-130">將 [相關屬性]\*\*\*\* 設定為 [郵遞區號]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-130">Set the **Related Attribute** to **Postal Code**.</span></span> <span data-ttu-id="07ca7-131">然後，在 [關聯性類型]\*\*\*\* 清單中，保持關聯性類型設定為 [彈性]\*\*\*\* 的狀態，因為成員之間的關聯性可能會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="07ca7-131">In the **Relationship type** list, leave the relationship type set to **Flexible** because relationships between the members might change over time.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="07ca7-132">此時，圖表中會顯示一個警告圖示，因為關聯性是重複的。</span><span class="sxs-lookup"><span data-stu-id="07ca7-132">A warning icon appears in the diagram because the relationship is redundant.</span></span> <span data-ttu-id="07ca7-133">關聯性**完整名稱**  ->  **Geography** ->  **郵遞區號**已經存在，而您剛建立了關聯性**完整名稱**的  ->  **郵遞區號**。</span><span class="sxs-lookup"><span data-stu-id="07ca7-133">The relationship **Full Name** -> **Geography**-> **Postal Code** already existed, and you just created the relationship **Full Name** -> **Postal Code**.</span></span> <span data-ttu-id="07ca7-134">關係**地理位置** ->  **郵遞區號**現在是多餘的，因此我們會將它移除。</span><span class="sxs-lookup"><span data-stu-id="07ca7-134">The relationship **Geography**-> **Postal Code** is now redundant, so we will remove it.</span></span>  
  
6.  <span data-ttu-id="07ca7-135">在 [屬性關聯性]\*\*\*\* 窗格中，以滑鼠右鍵按一下 [地理位置]\*\*\*\*-> [郵遞區號]\*\*\*\*，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-135">In the **Attribute Relationships** pane, right-click **Geography**-> **Postal Code** and then click **Delete**.</span></span>  
  
7.  <span data-ttu-id="07ca7-136">當 [刪除物件]\*\*\*\* 對話方塊顯示時，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-136">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
8.  <span data-ttu-id="07ca7-137">在圖表中，以滑鼠右鍵按一下 [郵遞區號]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-137">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="07ca7-138">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [郵遞區號]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-138">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="07ca7-139">將 [相關屬性]\*\*\*\* 設定為 [縣 (市)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-139">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="07ca7-140">在 [關聯性類型]\*\*\*\* 清單中，保持關聯性類型設定為 [彈性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-140">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="07ca7-141">關係**地理位置** ->  **City**現在是多餘的，因此我們會將其刪除。</span><span class="sxs-lookup"><span data-stu-id="07ca7-141">The relationship **Geography**-> **City** is now redundant so we will delete it.</span></span>  
  
11. <span data-ttu-id="07ca7-142">在 [屬性關聯性] 窗格中，以滑鼠右鍵按一下 [ **Geography** ->  **City** ]，然後按一下 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="07ca7-142">In the Attribute Relationships pane, right-click **Geography**-> **City** and then click **Delete**.</span></span>  
  
12. <span data-ttu-id="07ca7-143">當 [刪除物件]\*\*\*\* 對話方塊顯示時，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-143">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
13. <span data-ttu-id="07ca7-144">在圖表中，以滑鼠右鍵按一下 [縣 (市)]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-144">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
14. <span data-ttu-id="07ca7-145">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [縣 (市)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-145">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="07ca7-146">將 [相關屬性]\*\*\*\* 設定為 [省份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-146">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="07ca7-147">然後，在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*，因為縣 (市) 和省份之間的關聯性不會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="07ca7-147">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a city and a state will not change over time.</span></span>  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. <span data-ttu-id="07ca7-148">以滑鼠右鍵按一下介於 [地理位置]\*\*\*\* 與 [省份]\*\*\*\* 之間的箭頭，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-148">Right-click the arrow between **Geography** and **State-Province** and then click **Delete**.</span></span>  
  
17. <span data-ttu-id="07ca7-149">當 [刪除物件]\*\*\*\* 對話方塊顯示時，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-149">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
18. <span data-ttu-id="07ca7-150">在圖表中，以滑鼠右鍵按一下 [省份]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-150">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
19. <span data-ttu-id="07ca7-151">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [省份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-151">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="07ca7-152">將 [相關屬性]\*\*\*\* 設定為 [國家地區]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-152">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="07ca7-153">然後，在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*，因為省份和國家地區之間的關聯性不會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="07ca7-153">In the **Relationship type** list, set the relationship type to **Rigid** because the relationship between a state-province and a country-region will not change over time.</span></span>  
  
20. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
21. <span data-ttu-id="07ca7-154">在 [屬性關聯性] 窗格中，以滑鼠右鍵按一下 [**地理位置** ->  **國家/地區**]，然後按一下 [**刪除**]。</span><span class="sxs-lookup"><span data-stu-id="07ca7-154">In the Attribute Relationships pane, right-click **Geography**-> **Country-Region** and then click **Delete**.</span></span>  
  
22. <span data-ttu-id="07ca7-155">當 [刪除物件]\*\*\*\* 對話方塊顯示時，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-155">When the **Delete Objects** dialog box appears, click **OK**.</span></span>  
  
23. <span data-ttu-id="07ca7-156">按一下 [維度結構]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-156">Click the **Dimension Structure** tab.</span></span>  
  
     <span data-ttu-id="07ca7-157">請注意，當您刪除 [地理位置]\*\*\*\* 與其他屬性間的最後一個屬性關聯性時，就會刪除該 [地理位置]\*\*\*\* 本身。</span><span class="sxs-lookup"><span data-stu-id="07ca7-157">Notice that when you delete the last attribute relationship between **Geography** and other attributes, that **Geography** itself is deleted.</span></span> <span data-ttu-id="07ca7-158">這是因為不再使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="07ca7-158">This is because the attribute is no longer used.</span></span>  
  
24. <span data-ttu-id="07ca7-159">在 [檔案] 功能表上，按一下 [**全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="07ca7-159">On the File menu, click **Save All**.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-sales-territory-hierarchy"></a><span data-ttu-id="07ca7-160">在 [銷售領域] 階層中定義屬性的屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="07ca7-160">Defining Attribute Relationships for Attributes in the Sales Territory Hierarchy</span></span>  
  
1.  <span data-ttu-id="07ca7-161">請針對 [銷售領域]\*\*\*\* 維度開啟 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-161">Open Dimension Designer for the **Sales Territory** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="07ca7-162">在圖表中，以滑鼠右鍵按一下 [銷售領域國家 (地區)]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-162">In the diagram, right-click the **Sales Territory Country** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="07ca7-163">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [銷售領域國家 (地區)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-163">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Sales Territory Country**.</span></span> <span data-ttu-id="07ca7-164">將 [相關屬性]\*\*\*\* 設定為 [銷售領域國家 (地區)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-164">Set the **Related Attribute** to **Sales Territory Group**.</span></span> <span data-ttu-id="07ca7-165">在 [關聯性類型]\*\*\*\* 清單中，保持關聯性類型設定為 [彈性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-165">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="07ca7-166">[銷售領域群組]\*\*\*\* 現在連結到 [銷售領域國家 (地區)]\*\*\*\*，而 [銷售領域國家 (地區)]\*\*\*\* 現在則連結到 [銷售領域地區]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-166">**Sales Territory Group** is now linked to **Sales Territory Country**, and **Sales Territory Country** is now linked to **Sales Territory Region**.</span></span> <span data-ttu-id="07ca7-167">其中每個關聯性的 [RelationshipType]\*\*\*\* 屬性會設為 [彈性]\*\*\*\*，因為國家 (地區) 內的地區群組可能會隨著時間而變更，而且將國家 (地區) 分成群組的分組設定也可能會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="07ca7-167">The **RelationshipType** property for each of these relationships is set to **Flexible** because the groupings of regions within a country might change over time and because the groupings of countries into groups might change over time.</span></span>  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-product-model-lines-hierarchy"></a><span data-ttu-id="07ca7-168">在 [產品型號線] 階層中定義屬性的屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="07ca7-168">Defining Attribute Relationships for Attributes in the Product Model Lines Hierarchy</span></span>  
  
1.  <span data-ttu-id="07ca7-169">請針對 [產品]\*\*\*\* 維度開啟 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-169">Open Dimension Designer for the **Product** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="07ca7-170">在圖表中，以滑鼠右鍵按一下 [模型名稱]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-170">In the diagram, right-click the **Model Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="07ca7-171">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [模型名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-171">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Model Name**.</span></span> <span data-ttu-id="07ca7-172">將 [相關屬性]\*\*\*\* 設定為 [產品線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-172">Set the **Related Attribute** to **Product Line**.</span></span> <span data-ttu-id="07ca7-173">在 [關聯性類型]\*\*\*\* 清單中，保持關聯性類型設定為 [彈性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-173">In the **Relationship type** list, leave the relationship type set to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-fiscal-date-hierarchy"></a><span data-ttu-id="07ca7-174">在會計日期階層中定義屬性的屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="07ca7-174">Defining Attribute Relationships for Attributes in the Fiscal Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="07ca7-175">請針對 [日期]\*\*\*\* 維度切換至 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-175">Switch to Dimension Designer for the **Date** dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="07ca7-176">在圖表中，以滑鼠右鍵按一下 [月份]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-176">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="07ca7-177">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [月份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-177">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="07ca7-178">將 [相關屬性]\*\*\*\* 設定為 [會計季度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-178">Set the **Related Attribute** to **Fiscal Quarter**.</span></span> <span data-ttu-id="07ca7-179">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-179">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="07ca7-180">在圖表中，以滑鼠右鍵按一下 [會計季度]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-180">In the diagram, right-click the **Fiscal Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="07ca7-181">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [會計季度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-181">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Quarter**.</span></span> <span data-ttu-id="07ca7-182">將 [相關屬性]\*\*\*\* 設定為 [會計半年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-182">Set the **Related Attribute** to **Fiscal Semester**.</span></span> <span data-ttu-id="07ca7-183">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-183">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="07ca7-184">在圖表中，以滑鼠右鍵按一下 [會計半年度]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-184">In the diagram, right-click the **Fiscal Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="07ca7-185">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [會計半年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-185">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Fiscal Semester**.</span></span> <span data-ttu-id="07ca7-186">將 [相關屬性]\*\*\*\* 設定為 [會計年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-186">Set the **Related Attribute** to **Fiscal Year**.</span></span> <span data-ttu-id="07ca7-187">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-187">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-calendar-date-hierarchy"></a><span data-ttu-id="07ca7-188">在日曆日期階層中定義屬性的屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="07ca7-188">Defining Attribute Relationships for Attributes in the Calendar Date Hierarchy</span></span>  
  
1.  <span data-ttu-id="07ca7-189">在圖表中，以滑鼠右鍵按一下 [月份]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-189">In the diagram, right-click the **Month Name** attribute and then select **New Attribute Relationship**.</span></span>  
  
2.  <span data-ttu-id="07ca7-190">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [月份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-190">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Month Name**.</span></span> <span data-ttu-id="07ca7-191">將 [相關屬性]\*\*\*\* 設定為 [日曆季]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-191">Set the **Related Attribute** to **Calendar Quarter**.</span></span> <span data-ttu-id="07ca7-192">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-192">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="07ca7-193">在圖表中，以滑鼠右鍵按一下 [日曆季]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-193">In the diagram, right-click the **Calendar Quarter** attribute and then select **New Attribute Relationship**.</span></span>  
  
5.  <span data-ttu-id="07ca7-194">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [日曆季]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-194">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Quarter**.</span></span> <span data-ttu-id="07ca7-195">將 [相關屬性]\*\*\*\* 設定為 [日曆半年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-195">Set the **Related Attribute** to **Calendar Semester**.</span></span> <span data-ttu-id="07ca7-196">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-196">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="07ca7-197">在圖表中，以滑鼠右鍵按一下 [日曆半年度]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-197">In the diagram, right-click the **Calendar Semester** attribute and then select **New Attribute Relationship**.</span></span>  
  
8.  <span data-ttu-id="07ca7-198">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [日曆半年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-198">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Calendar Semester**.</span></span> <span data-ttu-id="07ca7-199">將 [相關屬性]\*\*\*\* 設定為 [日曆年度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-199">Set the **Related Attribute** to **Calendar Year**.</span></span> <span data-ttu-id="07ca7-200">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-200">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="defining-attribute-relationships-for-attributes-in-the-geography-hierarchy"></a><span data-ttu-id="07ca7-201">在 [地理位置] 階層中定義屬性的屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="07ca7-201">Defining Attribute Relationships for Attributes in the Geography Hierarchy</span></span>  
  
1.  <span data-ttu-id="07ca7-202">請針對 [地理位置] 維度開啟 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="07ca7-202">Open Dimension Designer for the Geography dimension, and then click the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="07ca7-203">在圖表中，以滑鼠右鍵按一下 [郵遞區號]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-203">In the diagram, right-click the **Postal Code** attribute and then select **New Attribute Relationship**.</span></span>  
  
3.  <span data-ttu-id="07ca7-204">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [郵遞區號]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-204">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **Postal Code**.</span></span> <span data-ttu-id="07ca7-205">將 [相關屬性]\*\*\*\* 設定為 [縣 (市)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-205">Set the **Related Attribute** to **City**.</span></span> <span data-ttu-id="07ca7-206">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [彈性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-206">In the **Relationship type** list, set the relationship type to **Flexible**.</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="07ca7-207">在圖表中，以滑鼠右鍵按一下 [縣 (市)]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-207">In the diagram, right-click the **City** attribute and then select **New Attribute Relationship**.</span></span>  
  
6.  <span data-ttu-id="07ca7-208">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [縣 (市)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-208">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **City**.</span></span> <span data-ttu-id="07ca7-209">將 [相關屬性]\*\*\*\* 設定為 [省份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-209">Set the **Related Attribute** to **State-Province**.</span></span> <span data-ttu-id="07ca7-210">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-210">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="07ca7-211">在圖表中，以滑鼠右鍵按一下 [省份]\*\*\*\* 屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-211">In the diagram, right-click the **State-Province** attribute and then select **New Attribute Relationship**.</span></span>  
  
9. <span data-ttu-id="07ca7-212">在 [建立屬性關聯性]\*\*\*\* 對話方塊中，[來源屬性]\*\*\*\* 是 [省份]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-212">In the **Create Attribute Relationship** dialog box, the **Source Attribute** is **State-Province**.</span></span> <span data-ttu-id="07ca7-213">將 [相關屬性]\*\*\*\* 設定為 [國家地區]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-213">Set the **Related Attribute** to **Country-Region**.</span></span> <span data-ttu-id="07ca7-214">在 [關聯性類型]\*\*\*\* 清單中，將關聯性類型設定為 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-214">In the **Relationship type** list, set the relationship type to **Rigid**.</span></span>  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. <span data-ttu-id="07ca7-215">在圖表中，以滑鼠右鍵按一下 [地理位置索引鍵]\*\*\*\* 屬性，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-215">In the diagram, right-click the **Geography Key** attribute and then select **Properties**.</span></span>  
  
12. <span data-ttu-id="07ca7-216">將 [AttributeHierarchyOptimizedState]\*\*\*\* 屬性設定為 [NotOptimized]\*\*\*\*、將 [AttributeHierarchyOrdered]\*\*\*\* 屬性設定為 [False]\*\*\*\*，並且將 [AttributeHierarchyVisible]\*\*\*\* 屬性設定為 [False]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-216">Set the **AttributeHierarchyOptimizedState** property to **NotOptimized**, set the **AttributeHierarchyOrdered** property to **False**, and set the **AttributeHierarchyVisible** property to **False**.</span></span>  
  
13. <span data-ttu-id="07ca7-217">在 [檔案] 功能表上，按一下 [全部儲存]。</span><span class="sxs-lookup"><span data-stu-id="07ca7-217">On the **File** menu, click **Save All**.</span></span>  
  
14. <span data-ttu-id="07ca7-218">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07ca7-218">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Services Tutorial**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="07ca7-219">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="07ca7-219">Next Task in Lesson</span></span>  
 [<span data-ttu-id="07ca7-220">定義未知的成員和 Null 處理屬性</span><span class="sxs-lookup"><span data-stu-id="07ca7-220">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="07ca7-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07ca7-221">See Also</span></span>  
 <span data-ttu-id="07ca7-222">[定義屬性關聯性](multidimensional-models/attribute-relationships-define.md) </span><span class="sxs-lookup"><span data-stu-id="07ca7-222">[Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) </span></span>  
 [<span data-ttu-id="07ca7-223">使用者階層屬性</span><span class="sxs-lookup"><span data-stu-id="07ca7-223">User Hierarchy Properties</span></span>](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)  
  
  
