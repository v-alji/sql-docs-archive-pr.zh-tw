---
title: 要求屬性值 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], requiring attribute values
- attributes [Master Data Services], requiring values
ms.assetid: a360ef13-0c34-43b8-a87e-2f5d8732d30e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42b412fc42138c5e186c6c7ad42373f20e35f3cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593422"
---
# <a name="require-attribute-values-master-data-services"></a><span data-ttu-id="874ad-102">要求屬性值 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="874ad-102">Require Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="874ad-103">當您想要確保主要資料完整時，在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中要求屬性值。</span><span class="sxs-lookup"><span data-stu-id="874ad-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], require attribute values when you want to ensure your master data is complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="874ad-104">在以網域屬性關聯性為基礎的衍生階層中，不會顯示遺漏網域屬性值的成員。</span><span class="sxs-lookup"><span data-stu-id="874ad-104">Members that are missing domain-based attribute values are not displayed in derived hierarchies that are based on those relationships.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="874ad-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="874ad-105">Prerequisites</span></span>  
 <span data-ttu-id="874ad-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="874ad-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="874ad-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="874ad-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="874ad-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="874ad-108">You must be a model administrator.</span></span> <span data-ttu-id="874ad-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="874ad-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-require-attribute-values"></a><span data-ttu-id="874ad-110">若要要求屬性值</span><span class="sxs-lookup"><span data-stu-id="874ad-110">To require attribute values</span></span>  
  
1.  <span data-ttu-id="874ad-111">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="874ad-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="874ad-112">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="874ad-112">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="874ad-113">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="874ad-113">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="874ad-114">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="874ad-114">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="874ad-115">從 [成員類型]\*\*\*\* 清單中，選取要套用商務規則的成員類型。</span><span class="sxs-lookup"><span data-stu-id="874ad-115">From the **Member Type** list, select a type of member for the business rule to apply to.</span></span>  
  
6.  <span data-ttu-id="874ad-116">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="874ad-116">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="874ad-117">按一下 [加入商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="874ad-117">Click **Add business rule**.</span></span>  
  
8.  <span data-ttu-id="874ad-118">按一下 [編輯選取的商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="874ad-118">Click **Edit selected business rule**.</span></span>  
  
9. <span data-ttu-id="874ad-119">在 [元件]\*\*\*\* 窗格中，展開 [動作]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="874ad-119">In the **Components** pane, expand the **Actions** node.</span></span>  
  
10. <span data-ttu-id="874ad-120">按一下 [**必要**]，並將它拖曳至 [ **THEN** ] 窗格的 [**動作**] 標籤。</span><span class="sxs-lookup"><span data-stu-id="874ad-120">Click **is required** and drag it to the **THEN** pane's **Action** label.</span></span>  
  
11. <span data-ttu-id="874ad-121">在 [屬性]\*\*\*\* 窗格中，按一下屬性並將它拖曳至 [編輯動作]\*\*\*\* 窗格的 [選取屬性]\*\*\*\* 標籤。</span><span class="sxs-lookup"><span data-stu-id="874ad-121">In the **Attributes** pane, click an attribute and drag it to the **Edit Action** pane's **Select attribute** label.</span></span>  
  
12. <span data-ttu-id="874ad-122">在 [編輯動作]\*\*\*\* 窗格中，按一下 [儲存項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="874ad-122">In the **Edit Action** pane, click **Save item**.</span></span>  
  
13. <span data-ttu-id="874ad-123">按一下 [上一步]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="874ad-123">Click **Back**.</span></span>  
  
14. <span data-ttu-id="874ad-124">(選擇性) 在 [商務規則維護]\*\*\*\* 頁面上，針對包含商務規則的資料列，按兩下 [名稱]\*\*\*\*、[描述]\*\*\*\* 或 [通知]\*\*\*\* 資料行中的資料格，以更新值。</span><span class="sxs-lookup"><span data-stu-id="874ad-124">Optionally, on the **Business Rules Maintenance** page, for the row that contains your business rule, double-click a cell in the **Name**, **Description**, or **Notification** column to update the value.</span></span>  
  
15. <span data-ttu-id="874ad-125">按一下 [發行商務規則]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="874ad-125">Click **Publish business rules**.</span></span>  
  
16. <span data-ttu-id="874ad-126">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="874ad-126">On the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="874ad-127">規則狀態會變更為 [作用中]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="874ad-127">The rule's status changes to **Active**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="874ad-128">後續步驟</span><span class="sxs-lookup"><span data-stu-id="874ad-128">Next Steps</span></span>  
  
-   <span data-ttu-id="874ad-129">遵循下列其中一個程序，將商務規則套用至資料：</span><span class="sxs-lookup"><span data-stu-id="874ad-129">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="874ad-130">根據商務規則驗證特定成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="874ad-130">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="874ad-131">根據商務規則驗證版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="874ad-131">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="874ad-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="874ad-132">See Also</span></span>  
 <span data-ttu-id="874ad-133">[商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="874ad-133">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="874ad-134">衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="874ad-134">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
