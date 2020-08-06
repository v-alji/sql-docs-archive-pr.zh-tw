---
title: 自動產生 Code 以外的屬性值 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b82f6f81-6e9c-4918-9ea9-4ab5f5d11b15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8db6c89bdce2a11a5a54ed3a763a7bc41bd7f1be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599050"
---
# <a name="automatically-generate-attribute-values-other-than-code-master-data-services"></a><span data-ttu-id="56c7c-102">自動產生 Code 以外的屬性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="56c7c-102">Automatically Generate Attribute Values Other Than Code (Master Data Services)</span></span>
  <span data-ttu-id="56c7c-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，當您希望每次套用商務規則時，自動將整數指派為值，請自動為實體的屬性自動產生值。</span><span class="sxs-lookup"><span data-stu-id="56c7c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's attribute values when you want an integer to be automatically assigned as the value each time business rules are applied.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="56c7c-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="56c7c-104">Prerequisites</span></span>  
 <span data-ttu-id="56c7c-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="56c7c-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="56c7c-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="56c7c-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="56c7c-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="56c7c-107">You must be a model administrator.</span></span> <span data-ttu-id="56c7c-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="56c7c-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="56c7c-109">數值屬性必須存在。</span><span class="sxs-lookup"><span data-stu-id="56c7c-109">A numeric attribute must exist.</span></span> <span data-ttu-id="56c7c-110">如需詳細資訊，請參閱[建立數值屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="56c7c-110">For more information, see [Create a Numeric Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-numeric-attribute-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-an-attribute-value"></a><span data-ttu-id="56c7c-111">若要自動產生屬性值</span><span class="sxs-lookup"><span data-stu-id="56c7c-111">To automatically generate an attribute value</span></span>  
  
1.  <span data-ttu-id="56c7c-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="56c7c-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="56c7c-113">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="56c7c-113">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="56c7c-114">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="56c7c-114">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="56c7c-115">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="56c7c-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="56c7c-116">從 [成員類型]\*\*\*\* 清單中，選取要套用商務規則的成員類型。</span><span class="sxs-lookup"><span data-stu-id="56c7c-116">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="56c7c-117">從 [屬性]\*\*\*\* 清單中，保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56c7c-117">From the **Attribute** list, leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="56c7c-118">按一下 [加入商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56c7c-118">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="56c7c-119">按一下 [編輯選取的商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56c7c-119">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="56c7c-120">在 [元件]\*\*\*\* 窗格中，展開 [動作]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="56c7c-120">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="56c7c-121">在 [預設] 節點中，按一下 [預設為產生的值]\*\*\*\*，然後將其拖曳至 [THEN]\*\*\*\* 窗格的 [動作]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="56c7c-121">In the Default Value node, click **defaults to a generated value** and drag it to the **THEN** pane's **Actions** label.</span></span>  
  
11. <span data-ttu-id="56c7c-122">在 [屬性]\*\*\*\* 窗格中，按一下擁有您要產生之值的屬性，並將其拖曳至 [編輯動作]\*\*\*\* 窗格的 [選取屬性]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="56c7c-122">In the **Attributes** pane, click the attribute with the value you want to generated and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="56c7c-123">在 [開始]\*\*\*\* 和 [遞增量]\*\*\*\* 方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="56c7c-123">Type a value in the **Start with** and **Increment by** boxes.</span></span> <span data-ttu-id="56c7c-124">如果成員已存在，則將根據最大的現有值設定值。</span><span class="sxs-lookup"><span data-stu-id="56c7c-124">If members already exist, the value will be set based on the highest existing value.</span></span> <span data-ttu-id="56c7c-125">例如，如果最大的現有值為 299，而且您將 [遞增量]\*\*\*\* 設定為 **1**，則下一個成員的值將設為 300。</span><span class="sxs-lookup"><span data-stu-id="56c7c-125">For example, if the highest existing value is 299 and you set **Increment by** to **1**, the next member's value will be set to 300.</span></span>  
  
13. <span data-ttu-id="56c7c-126">在 [編輯動作]\*\*\*\* 窗格中，按一下 [儲存項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56c7c-126">In the **Edit Action** pane, click **Save item**.</span></span>  
  
14. <span data-ttu-id="56c7c-127">按一下 [上一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56c7c-127">Click **Back**.</span></span>  
  
15. <span data-ttu-id="56c7c-128">(選擇性) 在 [商務規則維護]\*\*\*\* 頁面上，針對包含商務規則的資料列，按兩下 [名稱]\*\*\*\*、[描述]\*\*\*\* 或 [通知]\*\*\*\* 資料行中的資料格，以更新值。</span><span class="sxs-lookup"><span data-stu-id="56c7c-128">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
16. <span data-ttu-id="56c7c-129">按一下 [發行商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56c7c-129">Click **Publish business rules**.</span></span>  
  
17. <span data-ttu-id="56c7c-130">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="56c7c-130">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="56c7c-131">規則狀態會變更為 [作用中]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56c7c-131">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="56c7c-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="56c7c-132">Next Steps</span></span>  
  
-   [<span data-ttu-id="56c7c-133">根據商務規則驗證特定成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56c7c-133">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="56c7c-134">根據商務規則驗證版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56c7c-134">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="56c7c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56c7c-135">See Also</span></span>  
 <span data-ttu-id="56c7c-136">[自動建立程式碼 &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56c7c-136">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 <span data-ttu-id="56c7c-137">[商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56c7c-137">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="56c7c-138">驗證 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56c7c-138">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
  
