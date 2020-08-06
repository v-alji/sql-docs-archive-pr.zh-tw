---
title: 建立及發行商務規則 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], creating
- creating business rules [Master Data Services]
ms.assetid: 6961d636-4d69-468e-81f7-8d0be6a4a039
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4dfca5613a1f328e02b3fd2c7337885a23889207
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599042"
---
# <a name="create-and-publish-a-business-rule-master-data-services"></a><span data-ttu-id="00de7-102">建立及發行商務規則 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="00de7-102">Create and Publish a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="00de7-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立商務規則，確保主要資料的正確性。</span><span class="sxs-lookup"><span data-stu-id="00de7-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a business rule to ensure the accuracy of your master data.</span></span> <span data-ttu-id="00de7-104">建立規則之後，您必須發行它，才能將它套用至資料。</span><span class="sxs-lookup"><span data-stu-id="00de7-104">After you create a rule, you must publish it before you can apply it to data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="00de7-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="00de7-105">Prerequisites</span></span>  
 <span data-ttu-id="00de7-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="00de7-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="00de7-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="00de7-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="00de7-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="00de7-108">You must be a model administrator.</span></span> <span data-ttu-id="00de7-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="00de7-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-create-and-publish-a-business-rule"></a><span data-ttu-id="00de7-110">若要建立及發行商務規則</span><span class="sxs-lookup"><span data-stu-id="00de7-110">To create and publish a business rule</span></span>  
  
1.  <span data-ttu-id="00de7-111">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="00de7-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="00de7-112">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="00de7-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="00de7-113">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="00de7-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="00de7-114">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="00de7-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="00de7-115">從 [成員類型]\*\*\*\* 清單中，選取要套用商務規則的成員類型。</span><span class="sxs-lookup"><span data-stu-id="00de7-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="00de7-116">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="00de7-117">按一下 [加入商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="00de7-118">按一下 [編輯選取的商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="00de7-119">在 [元件]\*\*\*\* 窗格中，展開 [條件]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="00de7-119">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
10. <span data-ttu-id="00de7-120">按一下條件，並將它拖曳至 [ **IF** ] 窗格的 [**條件**] 標籤。</span><span class="sxs-lookup"><span data-stu-id="00de7-120">Click a condition and drag it to the **IF** pane's **Conditions** label.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="00de7-121">您可以按一下滑鼠右鍵並選擇 [**刪除**]，從商務規則中刪除專案。</span><span class="sxs-lookup"><span data-stu-id="00de7-121">You can delete items from your business rule by right-clicking and choosing **Delete**.</span></span>  
  
11. <span data-ttu-id="00de7-122">在 [**屬性**] 窗格中，按一下屬性，並將它拖曳至 [**編輯條件**] 窗格的 [**選取屬性**] 標籤。</span><span class="sxs-lookup"><span data-stu-id="00de7-122">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="00de7-123">在 [**編輯條件**] 窗格中，完成所有必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="00de7-123">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
13. <span data-ttu-id="00de7-124">在 [編輯條件]\*\*\*\* 窗格中，按一下 [儲存項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-124">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="00de7-125">在 [元件]\*\*\*\* 窗格中，展開 [動作]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="00de7-125">In the **Components** pane, expand the **Actions** node.</span></span>  
  
15. <span data-ttu-id="00de7-126">按一下動作並將它拖曳至 [THEN]\*\*\*\* 窗格的 [動作]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="00de7-126">Click an action and drag it to the **THEN** pane's **Action** label.</span></span>  
  
16. <span data-ttu-id="00de7-127">在 [屬性]\*\*\*\* 窗格中，按一下屬性並將它拖曳至 [編輯動作]\*\*\*\* 窗格的 [選取屬性]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="00de7-127">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
17. <span data-ttu-id="00de7-128">在 [編輯動作]\*\*\*\* 窗格中，完成任何必要欄位。</span><span class="sxs-lookup"><span data-stu-id="00de7-128">In the **Edit Action** pane, complete any required fields.</span></span>  
  
18. <span data-ttu-id="00de7-129">在 [編輯動作]\*\*\*\* 窗格中，按一下 [儲存項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-129">In the **Edit Action** pane, click **Save item**.</span></span>  
  
19. <span data-ttu-id="00de7-130">選擇性地將多個條件加入至規則。</span><span class="sxs-lookup"><span data-stu-id="00de7-130">Optionally, add multiple conditions to the rule.</span></span> <span data-ttu-id="00de7-131">如需詳細資訊，請參閱 [將多個條件加入至商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)(管理員 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="00de7-131">For more information, see [Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md).</span></span>  
  
20. <span data-ttu-id="00de7-132">按一下 [上一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-132">Click **Back**.</span></span>  
  
21. <span data-ttu-id="00de7-133">(選擇性) 在 [商務規則維護]\*\*\*\* 頁面上，針對包含商務規則的資料列，按兩下 [名稱]\*\*\*\*、[描述]\*\*\*\* 或 [通知]\*\*\*\* 資料行中的資料格，以更新值。</span><span class="sxs-lookup"><span data-stu-id="00de7-133">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="00de7-134">只針對包含驗證動作的規則才傳送通知。</span><span class="sxs-lookup"><span data-stu-id="00de7-134">Notifications are sent only for rules that include a validation action.</span></span>  
  
22. <span data-ttu-id="00de7-135">按一下 [發行商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-135">Click **Publish business rules**.</span></span>  
  
23. <span data-ttu-id="00de7-136">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="00de7-136">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="00de7-137">規則狀態會變更為 [作用中]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="00de7-137">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="00de7-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="00de7-138">Next Steps</span></span>  
  
-   <span data-ttu-id="00de7-139">遵循下列其中一個程序，將商務規則套用至資料：</span><span class="sxs-lookup"><span data-stu-id="00de7-139">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="00de7-140">根據商務規則驗證特定成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="00de7-140">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="00de7-141">根據商務規則驗證版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="00de7-141">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="00de7-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00de7-142">See Also</span></span>  
 <span data-ttu-id="00de7-143">[設定商務規則來傳送通知 &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="00de7-143">[Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="00de7-144">[變更商務規則名稱 &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="00de7-144">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="00de7-145">將多個條件新增至商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="00de7-145">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)  
  
  
