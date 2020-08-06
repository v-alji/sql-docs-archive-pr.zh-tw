---
title: 設定商務規則來傳送通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], configuring notifications
- e-mail [Master Data Services], configuring business rules
- notifications [Master Data Services], configuring business rules
ms.assetid: b24f7b11-ab53-4642-999c-e17b543b3558
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cb1a12167dffe123e55760f031e21499fe22a945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607444"
---
# <a name="configure-business-rules-to-send-notifications-master-data-services"></a><span data-ttu-id="7dc6d-102">設定商務規則來傳送通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7dc6d-102">Configure Business Rules to Send Notifications (Master Data Services)</span></span>
  <span data-ttu-id="7dc6d-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您想要通知使用者屬性值變更時，請設定商務規則來傳送通知。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], configure business rules to send notifications when you want to notify users about attribute value changes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7dc6d-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7dc6d-104">Prerequisites</span></span>  
 <span data-ttu-id="7dc6d-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="7dc6d-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7dc6d-106">您必須擁有存取 [系統管理]\*\*\*\* 和 [使用者及群組的權限]\*\*\*\* 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-106">You must have permission to access the **System Administration** and **User and Group Permissions** functional areas.</span></span> <span data-ttu-id="7dc6d-107">如果您沒有 [使用者及群組的權限]\*\*\*\* 功能區域的權限，就無法檢視傳送通知的目標使用者和群組清單。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-107">If you do not have permission to the **User and Group Permissions** functional area, you cannot view the list of users and groups to send notifications to.</span></span>  
  
-   <span data-ttu-id="7dc6d-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-108">You must be a model administrator.</span></span> <span data-ttu-id="7dc6d-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="7dc6d-110">使用驗證動作的商務規則必須已經存在。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-110">A business rule that uses a validation action must already exist.</span></span> <span data-ttu-id="7dc6d-111">如需詳細資訊，請參閱[建立及發行商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-111">For more information, see [Create and Publish a Business Rule &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="7dc6d-112">接收通知的使用者或群組至少必須針對驗證失敗的屬性擁有 [唯讀]\*\*\*\* 權限。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-112">The user or group that receives the notification must have at least **Read-only** permission to the attribute that fails validation.</span></span> <span data-ttu-id="7dc6d-113">遭明確或隱含拒絕此屬性之權限的使用者或群組將會收到電子郵件，但是無法在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中存取此屬性。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-113">Users or groups that are explicitly or implicitly denied permission to the attribute will receive the email but will not be able to access the attribute in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="7dc6d-114">如果將郵件傳送給群組，只有可存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的群組成員會收到電子郵件。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-114">If mail is sent to a group, only members of the group that have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] will get the email.</span></span>  
  
### <a name="to-configure-business-rules-to-send-notifications"></a><span data-ttu-id="7dc6d-115">若要設定商務規則來傳送通知</span><span class="sxs-lookup"><span data-stu-id="7dc6d-115">To configure business rules to send notifications</span></span>  
  
1.  <span data-ttu-id="7dc6d-116">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7dc6d-117">從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-117">From the menu bar, point to **Manage** and click **Business Rules**.</span></span>  
  
3.  <span data-ttu-id="7dc6d-118">在 [商務規則維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-118">On the **Business Rule Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7dc6d-119">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-119">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="7dc6d-120">從 [**成員類型**] 清單中，選取成員的類型。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-120">From the **Member Type** list, select a type of member.</span></span>  
  
6.  <span data-ttu-id="7dc6d-121">從 [屬性]\*\*\*\* 清單中，選取屬性或保留預設值 [全部]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-121">From the **Attribute** list, select an attribute or leave the default of **All**.</span></span>  
  
7.  <span data-ttu-id="7dc6d-122">在方格中，按兩下商務規則的資料列中的 [**通知**] 欄位。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-122">In the grid, in the row for the business rule, double-click the **Notification** field.</span></span>  
  
8.  <span data-ttu-id="7dc6d-123">從子功能表中，按一下要傳送電子郵件通知給哪一個使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="7dc6d-123">From the sub-menu, click a user or group to send the email notification to.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7dc6d-124">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7dc6d-124">Next Steps</span></span>  
  
-   <span data-ttu-id="7dc6d-125">遵循下列其中一個程序，將商務規則套用至資料：</span><span class="sxs-lookup"><span data-stu-id="7dc6d-125">Apply business rules to data by following one of these procedures:</span></span>  
  
    -   [<span data-ttu-id="7dc6d-126">根據商務規則驗證特定成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7dc6d-126">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
    -   [<span data-ttu-id="7dc6d-127">根據商務規則驗證版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7dc6d-127">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   <span data-ttu-id="7dc6d-128">依照下列方式設定電子郵件通訊協定：</span><span class="sxs-lookup"><span data-stu-id="7dc6d-128">Configure the email protocol as follows:</span></span>  
  
    -   [<span data-ttu-id="7dc6d-129">設定電子郵件通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7dc6d-129">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="7dc6d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dc6d-130">See Also</span></span>  
 <span data-ttu-id="7dc6d-131">[通知 &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7dc6d-131">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 [<span data-ttu-id="7dc6d-132">設定電子郵件通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7dc6d-132">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)  
  
  
