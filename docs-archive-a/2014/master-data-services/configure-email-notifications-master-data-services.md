---
title: 設定電子郵件通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: baf60677435122af00f5ee5492e47bafaa45a3ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607443"
---
# <a name="configure-email-notifications-master-data-services"></a><span data-ttu-id="cea9c-102">設定電子郵件通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cea9c-102">Configure Email Notifications (Master Data Services)</span></span>
  <span data-ttu-id="cea9c-103">當您想要 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 自動傳送電子郵件訊息時，請設定通知電子郵件。</span><span class="sxs-lookup"><span data-stu-id="cea9c-103">Configure notification emails when you want [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email messages automatically.</span></span>  
  
### <a name="to-configure-notifications"></a><span data-ttu-id="cea9c-104">設定通知</span><span class="sxs-lookup"><span data-stu-id="cea9c-104">To configure notifications</span></span>  
  
1.  <span data-ttu-id="cea9c-105">在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中的 **[資料庫]** 頁面上，選取您的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cea9c-105">In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], on the **Database** page, select your [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="cea9c-106">在 **[系統設定]** 區段中，按一下 **[建立設定檔]**。</span><span class="sxs-lookup"><span data-stu-id="cea9c-106">In the **System Settings** section, click **Create Profile**.</span></span>  
  
3.  <span data-ttu-id="cea9c-107">完成所有必要的欄位。</span><span class="sxs-lookup"><span data-stu-id="cea9c-107">Complete all required fields.</span></span> <span data-ttu-id="cea9c-108">如需詳細資訊，請參閱[建立 Database Mail 設定檔和帳戶對話方塊 &#40;Master Data Services 組態管理員&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="cea9c-108">For more information, see [Create Database Mail Profile and Account Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-mail-profile-and-account-dialog-box.md).</span></span>  
  
4.  <span data-ttu-id="cea9c-109">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="cea9c-109">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cea9c-110">當您設定通知之後，就無法使用 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 進行變更。</span><span class="sxs-lookup"><span data-stu-id="cea9c-110">After you configure notifications, you cannot use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to make changes.</span></span> <span data-ttu-id="cea9c-111">您必須直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中進行變更。</span><span class="sxs-lookup"><span data-stu-id="cea9c-111">You must make changes directly in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="cea9c-112">如需詳細資訊，請參閱 [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="cea9c-112">For more information, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="cea9c-113">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cea9c-113">Next Steps</span></span>  
  
-   <span data-ttu-id="cea9c-114">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有一些設定會影響通知。</span><span class="sxs-lookup"><span data-stu-id="cea9c-114">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="cea9c-115">您可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫 [系統設定] 資料表中調整這些設定。</span><span class="sxs-lookup"><span data-stu-id="cea9c-115">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="cea9c-116">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cea9c-116">For more information, see [System Settings &#40;Master Data Services&#41;](system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cea9c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cea9c-117">See Also</span></span>  
 <span data-ttu-id="cea9c-118">[通知 &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cea9c-118">[Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md) </span></span>  
 <span data-ttu-id="cea9c-119">[疑難排解 (Master Data Services) 的電子郵件通知](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span><span class="sxs-lookup"><span data-stu-id="cea9c-119">[Troubleshooting Email Notifications (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx) </span></span>  
 [<span data-ttu-id="cea9c-120">設定商務規則來傳送通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cea9c-120">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
