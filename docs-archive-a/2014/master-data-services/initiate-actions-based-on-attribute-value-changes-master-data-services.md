---
title: 根據屬性值變更來起始動作 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], tracking attribute changes
- change tracking groups [Master Data Services], initiating actions
ms.assetid: 5e4402ce-31db-4774-a2a1-552335f87693
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 50931b9f9c4bd5d08596d485ba695143b9c6594e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687954"
---
# <a name="initiate-actions-based-on-attribute-value-changes-master-data-services"></a><span data-ttu-id="f5c40-102">根據屬性值變更來起始動作 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f5c40-102">Initiate Actions Based on Attribute Value Changes (Master Data Services)</span></span>
  <span data-ttu-id="f5c40-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立商務規則，以根據屬性值變更來起始動作，</span><span class="sxs-lookup"><span data-stu-id="f5c40-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to initiate actions based on changes to attribute values.</span></span> <span data-ttu-id="f5c40-104">例如，當特定的屬性值變更時，您可能想要變更值、傳送通知，或啟動外部工作流程。</span><span class="sxs-lookup"><span data-stu-id="f5c40-104">For example, when a specific attribute value changes, you may want to change a value, send a notification, or start an external workflow.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f5c40-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f5c40-105">Prerequisites</span></span>  
 <span data-ttu-id="f5c40-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="f5c40-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f5c40-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="f5c40-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="f5c40-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="f5c40-108">You must be a model administrator.</span></span> <span data-ttu-id="f5c40-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c40-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f5c40-110">您的屬性必須位於變更追蹤群組。</span><span class="sxs-lookup"><span data-stu-id="f5c40-110">Your attributes must be in a change tracking group.</span></span> <span data-ttu-id="f5c40-111">如需詳細資訊，請參閱 [將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="f5c40-111">See [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) for more information.</span></span>  
  
### <a name="to-create-a-business-rule-to-initiate-actions-based-on-attribute-value-changes"></a><span data-ttu-id="f5c40-112">若要建立商務規則，以根據屬性值變更來起始動作</span><span class="sxs-lookup"><span data-stu-id="f5c40-112">To create a business rule to initiate actions based on attribute value changes</span></span>  
  
1.  <span data-ttu-id="f5c40-113">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="f5c40-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f5c40-114">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="f5c40-114">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="f5c40-115">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="f5c40-115">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f5c40-116">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="f5c40-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="f5c40-117">從 [成員類型]\*\*\*\* 清單中，選取要套用商務規則的成員類型。</span><span class="sxs-lookup"><span data-stu-id="f5c40-117">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="f5c40-118">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-118">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="f5c40-119">按一下 [加入商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-119">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="f5c40-120">按一下 [編輯選取的商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-120">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="f5c40-121">在 [元件]\*\*\*\* 窗格中，展開 [條件]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="f5c40-121">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="f5c40-122">將 [數值比較]\*\*\*\* 節點底下的 [已變更]\*\*\*\* 拖曳至 [IF]\*\*\*\* 窗格的 [條件]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="f5c40-122">Under the **Value comparison** node, drag **has changed** to the **IF** pane's **Conditions** label.</span></span>  
  
11. <span data-ttu-id="f5c40-123">在 [**屬性**] 窗格中，按一下屬性，並將它拖曳至 [**編輯條件**] 窗格的 [**選取屬性**] 標籤。</span><span class="sxs-lookup"><span data-stu-id="f5c40-123">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span> <span data-ttu-id="f5c40-124">此屬性對規則沒有作用，因此請選取任何可用屬性。</span><span class="sxs-lookup"><span data-stu-id="f5c40-124">This attribute has no effect on the rule, so select any available attribute.</span></span>  
  
12. <span data-ttu-id="f5c40-125">在 [編輯條件]\*\*\*\* 窗格的 [變更追蹤群組]\*\*\*\* 方塊中，輸入已指派為必要條件的變更追蹤群組編號。</span><span class="sxs-lookup"><span data-stu-id="f5c40-125">In the **Edit Condition** pane, in the **Change tracking group** box, type the number of the change tracking group that you assigned as part of the prerequisites.</span></span>  
  
13. <span data-ttu-id="f5c40-126">在 [編輯條件]\*\*\*\* 窗格中，按一下 [儲存項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-126">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="f5c40-127">在 [元件]\*\*\*\* 窗格中，展開 [動作]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="f5c40-127">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="f5c40-128">按一下動作並將它拖曳至 [THEN]\*\*\*\* 窗格的 [動作]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="f5c40-128">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="f5c40-129">在 [屬性]\*\*\*\* 窗格中，按一下屬性並將它拖曳至 [編輯動作]\*\*\*\* 窗格的 [選取屬性]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="f5c40-129">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="f5c40-130">在 [編輯動作]\*\*\*\* 窗格中，完成任何必要欄位。</span><span class="sxs-lookup"><span data-stu-id="f5c40-130">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="f5c40-131">在 [編輯動作]\*\*\*\* 窗格中，按一下 [儲存項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-131">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="f5c40-132">按一下 [上一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-132">Click **Back**.</span></span>  
  
20. <span data-ttu-id="f5c40-133">(選擇性) 在 [商務規則維護]\*\*\*\* 頁面上，針對包含商務規則的資料列，按兩下 [名稱]\*\*\*\*、[描述]\*\*\*\* 或 [通知]\*\*\*\* 資料行中的資料格，以更新值。</span><span class="sxs-lookup"><span data-stu-id="f5c40-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f5c40-134">只針對包含驗證動作的規則才傳送通知。</span><span class="sxs-lookup"><span data-stu-id="f5c40-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
21. <span data-ttu-id="f5c40-135">按一下 [發行商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-135">Click **Publish business rules**.</span></span>  
  
22. <span data-ttu-id="f5c40-136">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f5c40-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="f5c40-137">規則狀態會變更為 [作用中]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5c40-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f5c40-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f5c40-138">Next Steps</span></span>  
  
-   <span data-ttu-id="f5c40-139">遵循下列其中一個程序，將商務規則套用至資料：</span><span class="sxs-lookup"><span data-stu-id="f5c40-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="f5c40-140">根據商務規則驗證特定成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5c40-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="f5c40-141">根據商務規則驗證版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5c40-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="f5c40-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5c40-142">See Also</span></span>  
 <span data-ttu-id="f5c40-143">[將屬性新增至變更追蹤群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f5c40-143">[Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) </span></span>  
 [<span data-ttu-id="f5c40-144">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5c40-144">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
