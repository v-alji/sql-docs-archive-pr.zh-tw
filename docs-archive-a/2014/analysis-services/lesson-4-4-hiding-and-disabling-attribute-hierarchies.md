---
title: 隱藏及停用屬性階層 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095039c2-7104-414c-a9a6-327b03ce79df
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc043c68d2a83424a14707799fd90bf893abc12d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709993"
---
# <a name="hiding-and-disabling-attribute-hierarchies"></a><span data-ttu-id="04d04-102">隱藏及停用屬性階層</span><span class="sxs-lookup"><span data-stu-id="04d04-102">Hiding and Disabling Attribute Hierarchies</span></span>
  <span data-ttu-id="04d04-103">根據預設，系統會在維度中建立每個屬性的屬性階層，而且每個階層都可用來建立事實資料的維度。</span><span class="sxs-lookup"><span data-stu-id="04d04-103">By default, an attribute hierarchy is created for every attribute in a dimension, and each hierarchy is available for dimensioning fact data.</span></span> <span data-ttu-id="04d04-104">這個階層是由「全部」層級和詳細資料層級 (含階層的所有成員) 所組成。</span><span class="sxs-lookup"><span data-stu-id="04d04-104">This hierarchy consists of an "All" level and a detail level containing all members of the hierarchy.</span></span> <span data-ttu-id="04d04-105">如同您已學到的，您可以將屬性組織成使用者自訂階層，在 Cube 中提供導覽路徑。</span><span class="sxs-lookup"><span data-stu-id="04d04-105">As you have already learned, you can organize attributes into user-defined hierarchies to provide navigation paths in a cube.</span></span> <span data-ttu-id="04d04-106">在某些情況下，您可以停用或隱藏某些屬性及其階層。</span><span class="sxs-lookup"><span data-stu-id="04d04-106">Under certain circumstances, you may want to disable or hide some attributes and their hierarchies.</span></span> <span data-ttu-id="04d04-107">例如，某些屬性如保險號碼或身分證號碼、薪水、出生日期和登入資訊等，使用者不能利用這些屬性來建立 Cube 資訊的維度。</span><span class="sxs-lookup"><span data-stu-id="04d04-107">For example, certain attributes such as social security numbers or national identification numbers, pay rates, birth dates, and login information are not attributes by which users will dimension cube information.</span></span> <span data-ttu-id="04d04-108">相反地，這項資訊通常只是做為特定屬性成員的詳細資料來檢視。</span><span class="sxs-lookup"><span data-stu-id="04d04-108">Instead, this information is generally only viewed as details of a particular attribute member.</span></span> <span data-ttu-id="04d04-109">您可以隱藏這些屬性階層，讓屬性只顯示成特定屬性的成員屬性。</span><span class="sxs-lookup"><span data-stu-id="04d04-109">You may want to hide these attribute hierarchies, leaving the attributes visible only as member properties of a specific attribute.</span></span> <span data-ttu-id="04d04-110">您也可以讓其他屬性的成員 (例如客戶名稱或郵遞區號) 只透過使用者階層而非透過獨立屬性階層來檢視。</span><span class="sxs-lookup"><span data-stu-id="04d04-110">You may also want to make members of other attributes, such as customer names or postal codes, visible only when they are viewed through a user hierarchy instead of independently through an attribute hierarchy.</span></span> <span data-ttu-id="04d04-111">這麼做的原因是為了顯示屬性階層中的全部相異成員。</span><span class="sxs-lookup"><span data-stu-id="04d04-111">One reason to do so may be the sheer number of distinct members in the attribute hierarchy.</span></span> <span data-ttu-id="04d04-112">最後，為了增進處理效能，您應該將使用者不再用來瀏覽的屬性階層停用。</span><span class="sxs-lookup"><span data-stu-id="04d04-112">Finally, to improve processing performance, you should disable attribute hierarchies that users will not use for browsing.</span></span>

 <span data-ttu-id="04d04-113">**AttributeHierarchyEnabled** 屬性的值決定是否建立屬性階層。</span><span class="sxs-lookup"><span data-stu-id="04d04-113">The value of the **AttributeHierarchyEnabled** property determines whether an attribute hierarchy is created.</span></span> <span data-ttu-id="04d04-114">如果這個屬性設為 **False**，則不建立屬性階層，且屬性不得做為使用者階層中的一個層級；屬性階層只得以成員屬性的身分存在。</span><span class="sxs-lookup"><span data-stu-id="04d04-114">If this property is set to **False**, the attribute hierarchy is not created and the attribute cannot be used as a level in a user hierarchy; the attribute hierarchy exists as a member property only.</span></span> <span data-ttu-id="04d04-115">不過，已停用的屬性階層仍然可以用來排序另一個屬性的成員。</span><span class="sxs-lookup"><span data-stu-id="04d04-115">However, a disabled attribute hierarchy can still be used to order the members of another attribute.</span></span> <span data-ttu-id="04d04-116">如果 **AttributeHierarchyEnabled** 屬性的值設為 **True**，則 **AttributeHierarchyVisible** 屬性的值將決定是否不論屬性階層在使用者自訂階層中的用法為何皆會顯示。</span><span class="sxs-lookup"><span data-stu-id="04d04-116">If the value of the **AttributeHierarchyEnabled** property is set to **True**, the value of the **AttributeHierarchyVisible** property determines whether the attribute hierarchy is visible independent of its use in a user-defined hierarchy.</span></span>

 <span data-ttu-id="04d04-117">啟用屬性階層之後，您可以指定下列另外 3 個屬性的值：</span><span class="sxs-lookup"><span data-stu-id="04d04-117">When an attribute hierarchy is enabled, you may want to specify values for the following three additional properties:</span></span>

-   <span data-ttu-id="04d04-118">**IsAggregatable**</span><span class="sxs-lookup"><span data-stu-id="04d04-118">**IsAggregatable**</span></span>

     <span data-ttu-id="04d04-119">依預設，會對所有屬性階層定義 (全部) 層級。</span><span class="sxs-lookup"><span data-stu-id="04d04-119">By default, an (All) level is defined for all attribute hierarchies.</span></span> <span data-ttu-id="04d04-120">若要為啟用的屬性階層停用 (全部) 層級，請將這個屬性的值設為 **False**。</span><span class="sxs-lookup"><span data-stu-id="04d04-120">To disable the (All) level for an enabled attribute hierarchy, set the value for this property to **False**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="04d04-121">如果某個屬性的 **IsAggregatable** 屬性設為 false，其就只能當做使用者定義階層的根使用，而且必須指定預設的成員 (否則， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 引擎將會為您選擇一個成員)。</span><span class="sxs-lookup"><span data-stu-id="04d04-121">An attribute that has its **IsAggregatable** property set to false can only be used as the root of a user-defined hierarchy and must have a default member specified (otherwise, one will be chosen for you by the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] engine).</span></span>

-   <span data-ttu-id="04d04-122">**AttributeHierarchyOrdered**</span><span class="sxs-lookup"><span data-stu-id="04d04-122">**AttributeHierarchyOrdered**</span></span>

     <span data-ttu-id="04d04-123">依預設， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在處理期間會排序已啟用屬性階層的成員，然後按 **OrderBy** 屬性的值來儲存成員，例如按名稱或索引鍵。</span><span class="sxs-lookup"><span data-stu-id="04d04-123">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] orders the members of enabled attribute hierarchies during processing, and then stores the members by the value of the **OrderBy** property, such as by Name or Key.</span></span> <span data-ttu-id="04d04-124">如果您不在乎排序，可將這個屬性的值設為 **False**，來增加處理效能。</span><span class="sxs-lookup"><span data-stu-id="04d04-124">If you do not care about ordering, you can increase processing performance by setting the value of this property to **False**.</span></span>

-   <span data-ttu-id="04d04-125">**AttributeHierarchyOptimizedState**</span><span class="sxs-lookup"><span data-stu-id="04d04-125">**AttributeHierarchyOptimizedState**</span></span>

     <span data-ttu-id="04d04-126">依預設， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在處理期間會為每一個已啟用的屬性階層建立一個索引，來改進查詢效能。</span><span class="sxs-lookup"><span data-stu-id="04d04-126">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates an index for each enabled attribute hierarchy during processing, to improve query performance.</span></span> <span data-ttu-id="04d04-127">如果您不打算使用屬性階層來瀏覽，可將這個屬性的值設為 **NotOptimized**，來增加處理效能。</span><span class="sxs-lookup"><span data-stu-id="04d04-127">If you do not plan to use an attribute hierarchy for browsing, you can increase processing performance by setting the value of this property to **NotOptimized**.</span></span> <span data-ttu-id="04d04-128">不過，如果您使用隱藏的階層做為維度的索引鍵屬性，則建立屬性成員的索引仍然可以改進效能。</span><span class="sxs-lookup"><span data-stu-id="04d04-128">However, if you use a hidden hierarchy as the key attribute for the dimension, creating an index of the attribute members will still improve performance.</span></span>

 <span data-ttu-id="04d04-129">如果屬性階層已停用，則這些屬性不適用。</span><span class="sxs-lookup"><span data-stu-id="04d04-129">These properties do not apply if an attribute hierarchy is disabled.</span></span>

 <span data-ttu-id="04d04-130">在這個主題的工作中，您會在 [員工] 維度中停用不用於瀏覽的保險號碼和其他屬性。</span><span class="sxs-lookup"><span data-stu-id="04d04-130">In the tasks in this topic, you will disable social security numbers and other attributes in the Employee dimension that will not be used for browsing.</span></span> <span data-ttu-id="04d04-131">然後您會在 [客戶] 維度中隱藏客戶名稱和郵遞區號屬性階層。</span><span class="sxs-lookup"><span data-stu-id="04d04-131">You will then hide the customer name and postal code attribute hierarchies in the Customer dimension.</span></span> <span data-ttu-id="04d04-132">這些階層中大量的屬性成員會使得瀏覽這些階層的速度變得很慢 (與使用者階層無關)。</span><span class="sxs-lookup"><span data-stu-id="04d04-132">The large number of attribute members in these hierarchies will make browsing these hierarchies very slow independent of a user hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-employee-dimension"></a><span data-ttu-id="04d04-133">在 [員工] 維度中設定屬性階層的屬性</span><span class="sxs-lookup"><span data-stu-id="04d04-133">Setting Attribute Hierarchy Properties in the Employee Dimension</span></span>

1.  <span data-ttu-id="04d04-134">切換到適用於 [員工] 維度的維度設計師，然後按一下 [瀏覽器]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="04d04-134">Switch to Dimension Designer for the Employee dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="04d04-135">確認下列屬性階層有出現在 [階層]\*\*\*\* 清單中：</span><span class="sxs-lookup"><span data-stu-id="04d04-135">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="04d04-136">**底薪**</span><span class="sxs-lookup"><span data-stu-id="04d04-136">**Base Rate**</span></span>

    -   <span data-ttu-id="04d04-137">**Birth Date**</span><span class="sxs-lookup"><span data-stu-id="04d04-137">**Birth Date**</span></span>

    -   <span data-ttu-id="04d04-138">**登入識別碼**</span><span class="sxs-lookup"><span data-stu-id="04d04-138">**Login ID**</span></span>

    -   <span data-ttu-id="04d04-139">**管理員 SSN**</span><span class="sxs-lookup"><span data-stu-id="04d04-139">**Manager SSN**</span></span>

    -   <span data-ttu-id="04d04-140">**SSN**</span><span class="sxs-lookup"><span data-stu-id="04d04-140">**SSN**</span></span>

3.  <span data-ttu-id="04d04-141">切換至 [維度結構]\*\*\*\* 索引標籤，然後在 [屬性]\*\*\*\* 窗格中選擇下列屬性。</span><span class="sxs-lookup"><span data-stu-id="04d04-141">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane.</span></span> <span data-ttu-id="04d04-142">您可以在按住 CTRL 鍵的同時，按一下每個量值，藉以選取多個量值：</span><span class="sxs-lookup"><span data-stu-id="04d04-142">You can select multiple measures by clicking each while holding down the CTRL key:</span></span>

    -   <span data-ttu-id="04d04-143">**底薪**</span><span class="sxs-lookup"><span data-stu-id="04d04-143">**Base Rate**</span></span>

    -   <span data-ttu-id="04d04-144">**Birth Date**</span><span class="sxs-lookup"><span data-stu-id="04d04-144">**Birth Date**</span></span>

    -   <span data-ttu-id="04d04-145">**登入識別碼**</span><span class="sxs-lookup"><span data-stu-id="04d04-145">**Login ID**</span></span>

    -   <span data-ttu-id="04d04-146">**管理員 SSN**</span><span class="sxs-lookup"><span data-stu-id="04d04-146">**Manager SSN**</span></span>

    -   <span data-ttu-id="04d04-147">**SSN**</span><span class="sxs-lookup"><span data-stu-id="04d04-147">**SSN**</span></span>

4.  <span data-ttu-id="04d04-148">在 [屬性] 視窗中，針對已選取的屬性，將 **AttributeHierarchyEnabled** 屬性的值設為 **False**。</span><span class="sxs-lookup"><span data-stu-id="04d04-148">In the Properties window, set the value of the **AttributeHierarchyEnabled** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="04d04-149">請注意，在 [屬性]\*\*\*\* 窗格中，每個屬性的圖示已變更為指示該屬性未啟用。</span><span class="sxs-lookup"><span data-stu-id="04d04-149">Notice in the **Attributes** pane that the icon for each attribute has changed to indicate that the attribute is not enabled.</span></span>

     <span data-ttu-id="04d04-150">下圖顯示針對已選取的屬性，將 **AttributeHierarchyEnabled** 屬性設為 False。</span><span class="sxs-lookup"><span data-stu-id="04d04-150">The following image shows the **AttributeHierarchyEnabled** property set to False for the selected attributes.</span></span>

     <span data-ttu-id="04d04-151">![AttributeHierarchyEnabled 屬性設定為 False](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "AttributeHierarchyEnabled 屬性設定為 False")</span><span class="sxs-lookup"><span data-stu-id="04d04-151">![AttributeHierarchyEnabled property set to False](../../2014/tutorials/media/l4-hierarchyenabled-1.gif "AttributeHierarchyEnabled property set to False")</span></span>

5.  <span data-ttu-id="04d04-152">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04d04-152">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

6.  <span data-ttu-id="04d04-153">順利完成處理之後，切換到 [瀏覽器]\*\*\*\* 索引標籤、按一下 [重新連接]\*\*\*\*，然後試著瀏覽已修改的屬性階層。</span><span class="sxs-lookup"><span data-stu-id="04d04-153">When processing has successfully completed, switch to the **Browser** tab, click **Reconnect**, and then try to browse the modified attribute hierarchies.</span></span>

     <span data-ttu-id="04d04-154">請注意，已修改屬性的成員不會顯示在 [階層]\*\*\*\* 清單中的屬性階層，供您瀏覽。</span><span class="sxs-lookup"><span data-stu-id="04d04-154">Notice that the members of the modified attributes are not available for browsing as attribute hierarchies in the **Hierarchy** list.</span></span> <span data-ttu-id="04d04-155">如果您嘗試加入其中一個已停用的屬性階層做為使用者階層中的一個層級，您會收到錯誤訊息，通知您必須啟用屬性階層才能參與使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="04d04-155">If you try to add one of the disabled attribute hierarchies as a level in a user hierarchy, you will receive an error notifying you that the attribute hierarchy must be enabled to participate in a user-defined hierarchy.</span></span>

## <a name="setting-attribute-hierarchy-properties-in-the-customer-dimension"></a><span data-ttu-id="04d04-156">在客戶維度中設定屬性階層的屬性</span><span class="sxs-lookup"><span data-stu-id="04d04-156">Setting Attribute Hierarchy Properties in the Customer Dimension</span></span>

1.  <span data-ttu-id="04d04-157">切換到適用於 [客戶] 維度的維度設計師，然後按一下 [瀏覽器]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="04d04-157">Switch to Dimension Designer for the Customer dimension, and then click the **Browser** tab.</span></span>

2.  <span data-ttu-id="04d04-158">確認下列屬性階層有出現在 [階層]\*\*\*\* 清單中：</span><span class="sxs-lookup"><span data-stu-id="04d04-158">Verify that the following attribute hierarchies appear in the **Hierarchy** list:</span></span>

    -   <span data-ttu-id="04d04-159">**全名**</span><span class="sxs-lookup"><span data-stu-id="04d04-159">**Full Name**</span></span>

    -   <span data-ttu-id="04d04-160">**郵遞區號**</span><span class="sxs-lookup"><span data-stu-id="04d04-160">**Postal Code**</span></span>

3.  <span data-ttu-id="04d04-161">切換到 [維度結構]\*\*\*\* 索引標籤，然後使用 CTRL 鍵同時選取多個屬性，來選取 [屬性]\*\*\*\* 窗格中的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="04d04-161">Switch to the **Dimension Structure** tab, and then select the following attributes in the **Attributes** pane by using the CTRL key to select multiple attributes at the same time:</span></span>

    -   <span data-ttu-id="04d04-162">**全名**</span><span class="sxs-lookup"><span data-stu-id="04d04-162">**Full Name**</span></span>

    -   <span data-ttu-id="04d04-163">**郵遞區號**</span><span class="sxs-lookup"><span data-stu-id="04d04-163">**Postal Code**</span></span>

4.  <span data-ttu-id="04d04-164">在 [屬性] 視窗中，針對已選取的屬性，將 **AttributeHierarchyVisible** 屬性的值設為 **False** 。</span><span class="sxs-lookup"><span data-stu-id="04d04-164">In the Properties window, set the value of the **AttributeHierarchyVisible** property to **False** for the selected attributes.</span></span>

     <span data-ttu-id="04d04-165">因為這些屬性階層的成員將用於建立事實資料的維度，所以將這些屬性階層的成員排序和最佳化，可改進效能。</span><span class="sxs-lookup"><span data-stu-id="04d04-165">Because the members of these attribute hierarchies will be used for dimensioning fact data, ordering and optimizing the members of these attribute hierarchies will improve performance.</span></span> <span data-ttu-id="04d04-166">因此，不得變更這些屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="04d04-166">Therefore, the properties of these attributes should not be changed.</span></span>

     <span data-ttu-id="04d04-167">下圖顯示 **AttributeHierarchyVisible** 屬性設為 False。</span><span class="sxs-lookup"><span data-stu-id="04d04-167">The following image shows the **AttributeHierarchyVisible** property set to False.</span></span>

     <span data-ttu-id="04d04-168">![AttributeHierarchyVisible 屬性設定為 False](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "AttributeHierarchyVisible 屬性設定為 False")</span><span class="sxs-lookup"><span data-stu-id="04d04-168">![AttributeHierarchyVisible property set to False](../../2014/tutorials/media/l4-hierarchyvisible-1.gif "AttributeHierarchyVisible property set to False")</span></span>

5.  <span data-ttu-id="04d04-169">從 [屬性]\*\*\*\* 窗格，將 [郵遞區號]\*\*\*\* 屬性拖曳到 [客戶地理位置]\*\*\*\* 使用者階層中 (位於 [階層和層級]\*\*\*\* 窗格的 [縣 (市)]\*\*\*\* 層級下)。</span><span class="sxs-lookup"><span data-stu-id="04d04-169">Drag the **Postal Code** attribute from the **Attributes** pane into the **Customer Geography** user hierarchy in the **Hierarchies and Levels** pane, immediately under the **City** level.</span></span>

     <span data-ttu-id="04d04-170">請注意，隱藏的屬性仍然成為使用者階層中的一個層級。</span><span class="sxs-lookup"><span data-stu-id="04d04-170">Notice that a hidden attribute can still become a level in a user hierarchy.</span></span>

6.  <span data-ttu-id="04d04-171">在 [建立]\*\*\*\* 功能表上，按一下 [部署 Analysis Services 教學課程]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04d04-171">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

7.  <span data-ttu-id="04d04-172">順利完成部署之後，針對 [客戶] 維度切換到 [瀏覽器]\*\*\*\* 索引標籤，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04d04-172">When deployment has successfully completed, switch to the **Browser** tab for the Customer dimension, and then click **Reconnect**.</span></span>

8.  <span data-ttu-id="04d04-173">嘗試從 [階層]\*\*\*\* 清單中選取任何一個已修改的屬性階層。</span><span class="sxs-lookup"><span data-stu-id="04d04-173">Try to select either of the modified attribute hierarchies from the **Hierarchy** list.</span></span>

     <span data-ttu-id="04d04-174">請注意，兩個已修改的屬性階層都不會出現在 [階層]\*\*\*\* 清單中。</span><span class="sxs-lookup"><span data-stu-id="04d04-174">Notice that neither of the modified attribute hierarchies appears in the **Hierarchy** list.</span></span>

9. <span data-ttu-id="04d04-175">在 [階層]\*\*\*\* 清單中，選取 [客戶地理位置]\*\*\*\*，然後在瀏覽器窗格中瀏覽每一個層級。</span><span class="sxs-lookup"><span data-stu-id="04d04-175">In the **Hierarchy** list, select **Customer Geography**, and then browse each level in the browser pane.</span></span>

     <span data-ttu-id="04d04-176">請注意，[郵遞區號]\*\*\*\* 和 [全名]\*\*\*\* 這兩個隱藏的層級會出現在使用者自訂階層中。</span><span class="sxs-lookup"><span data-stu-id="04d04-176">Notice that the hidden levels, **Postal Code** and **Full Name**, are visible in the user-defined hierarchy.</span></span>

## <a name="next-task-in-lesson"></a><span data-ttu-id="04d04-177">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="04d04-177">Next Task in Lesson</span></span>
 [<span data-ttu-id="04d04-178">依次要屬性來排序屬性成員</span><span class="sxs-lookup"><span data-stu-id="04d04-178">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)


