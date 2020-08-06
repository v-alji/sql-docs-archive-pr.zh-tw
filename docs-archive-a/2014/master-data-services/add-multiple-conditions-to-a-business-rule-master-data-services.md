---
title: 將多個條件新增至商務規則 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c62b8dfa4f459958d12bd384b85aa74bef382b21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597896"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a><span data-ttu-id="ddd14-102">將多個條件加入至商務規則 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ddd14-102">Add Multiple Conditions to a Business Rule (Master Data Services)</span></span>
  <span data-ttu-id="ddd14-103">如果您想要比較複雜的規則，請在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中將多個 **AND** 或 **OR** 條件新增至商務規則。</span><span class="sxs-lookup"><span data-stu-id="ddd14-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], add multiple **AND** or **OR** conditions to a business rule when you want a more complex rule.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ddd14-104">如果您建立使用 **OR** 運算子的商務規則，請考慮為每個可獨立評估的條件陳述式建立不同的規則。</span><span class="sxs-lookup"><span data-stu-id="ddd14-104">If you create a business rule that uses the **OR** operator, consider creating a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="ddd14-105">然後您可以視需要排除規則，提供更多彈性和輕鬆疑難排解。</span><span class="sxs-lookup"><span data-stu-id="ddd14-105">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ddd14-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ddd14-106">Prerequisites</span></span>  
 <span data-ttu-id="ddd14-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="ddd14-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ddd14-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="ddd14-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="ddd14-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="ddd14-109">You must be a model administrator.</span></span> <span data-ttu-id="ddd14-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd14-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="ddd14-111">商務規則必須存在。</span><span class="sxs-lookup"><span data-stu-id="ddd14-111">A business rule must exist.</span></span> <span data-ttu-id="ddd14-112">如需詳細資訊，請參閱[建立及發行商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd14-112">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a><span data-ttu-id="ddd14-113">若要將多個條件加入至商務規則</span><span class="sxs-lookup"><span data-stu-id="ddd14-113">To add multiple conditions to a business rule</span></span>  
  
1.  <span data-ttu-id="ddd14-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="ddd14-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="ddd14-115">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="ddd14-115">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="ddd14-116">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="ddd14-116">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="ddd14-117">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="ddd14-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="ddd14-118">從 [**成員類型**] 清單中，選取成員的類型。</span><span class="sxs-lookup"><span data-stu-id="ddd14-118">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="ddd14-119">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddd14-119">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="ddd14-120">按一下您想要編輯之商務規則的資料列。</span><span class="sxs-lookup"><span data-stu-id="ddd14-120">Click the row for the business rule you want to edit.</span></span>  
  
8.  <span data-ttu-id="ddd14-121">按一下 [編輯選取的商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddd14-121">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="ddd14-122">在 [**元件**] 窗格中，展開 [**邏輯運算子**] 節點。</span><span class="sxs-lookup"><span data-stu-id="ddd14-122">In the **Components** pane, expand the **Logical Operators** node.</span></span>  
  
10. <span data-ttu-id="ddd14-123">按一下 [ **and** ] 或 [ **or** ]，並將它拖曳至 [ **IF** ] 窗格的**和**標籤。</span><span class="sxs-lookup"><span data-stu-id="ddd14-123">Click **AND** or **OR** and drag it to the **IF** pane's **AND** label.</span></span>  
  
11. <span data-ttu-id="ddd14-124">在 [元件]\*\*\*\* 窗格中，展開 [條件]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="ddd14-124">In the **Components** pane, expand the **Conditions** node.</span></span>  
  
12. <span data-ttu-id="ddd14-125">按一下條件，並將它拖曳至 [ **IF** ] 窗格，並將其拖曳至步驟10中的**and**或**or**標籤。</span><span class="sxs-lookup"><span data-stu-id="ddd14-125">Click a condition and drag it to **IF** pane, to the **AND** or **OR** label from step 10.</span></span>  
  
13. <span data-ttu-id="ddd14-126">在 [**屬性**] 窗格中，按一下屬性，並將它拖曳至 [**編輯條件**] 窗格的 [**選取屬性**] 標籤。</span><span class="sxs-lookup"><span data-stu-id="ddd14-126">In the **Attributes** pane, click an attribute and drag it to the **Edit Condition** pane's **Select attribute** label.</span></span>  
  
14. <span data-ttu-id="ddd14-127">在 [**編輯條件**] 窗格中，完成所有必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="ddd14-127">In the **Edit Condition** pane, complete any required fields.</span></span>  
  
15. <span data-ttu-id="ddd14-128">在 [編輯條件]\*\*\*\* 窗格中，按一下 [儲存項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ddd14-128">In the **Edit Condition** pane, click **Save item**.</span></span>  
  
16. <span data-ttu-id="ddd14-129">（選擇性）若要加入更多條件，請從 [**元件**] 窗格中，將**and** **或 or 拖曳至** **IF**窗格中的任何**and** **或 or。**</span><span class="sxs-lookup"><span data-stu-id="ddd14-129">Optionally, to add more conditions, from the **Components** pane, drag **AND** or **OR** to any **AND** or **OR** in the **IF** pane.</span></span> <span data-ttu-id="ddd14-130">接著遵循上述步驟 13 - 15。</span><span class="sxs-lookup"><span data-stu-id="ddd14-130">Then follow steps 13-15.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="ddd14-131">若要刪除條件，請按一下條件的名稱，然後在 [**編輯條件**] 窗格中，按一下 [**刪除專案**]。</span><span class="sxs-lookup"><span data-stu-id="ddd14-131">To delete a condition, click the name of the condition and in the **Edit Condition** pane, click **Delete item**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd14-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd14-132">See Also</span></span>  
 <span data-ttu-id="ddd14-133">[商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ddd14-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 <span data-ttu-id="ddd14-134">[變更商務規則名稱 &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ddd14-134">[Change a Business Rule Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md) </span></span>  
 [<span data-ttu-id="ddd14-135">設定商務規則來傳送通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ddd14-135">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
