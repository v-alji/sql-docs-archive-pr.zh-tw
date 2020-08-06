---
title: 通知 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- notifications [Master Data Services]
- notifications [Master Data Services], about notifications
- e-mail [Master Data Services]
- e-mail [Master Data Services], about e-mail notifications
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a61825f9450dd5b708aff8c3fc72f0f12732337b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606374"
---
# <a name="notifications-master-data-services"></a><span data-ttu-id="8e971-102">通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8e971-102">Notifications (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="8e971-103">可設定為在商務規則驗證失敗時傳送電子郵件通知，或模型版本的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="8e971-103">can be configured to send an email notification when business rule validation fails or the status of a model version changes.</span></span>  
  
## <a name="how-notifications-are-sent"></a><span data-ttu-id="8e971-104">通知的傳送方式</span><span class="sxs-lookup"><span data-stu-id="8e971-104">How Notifications Are Sent</span></span>  
 <span data-ttu-id="8e971-105">您在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中設定通知。</span><span class="sxs-lookup"><span data-stu-id="8e971-105">You configure notifications in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="8e971-106">通知 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 會在主控資料庫的實例上，使用 Database Mail 來傳送電子郵件訊息 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8e971-106">Notifications send email messages by using Database Mail on the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that hosts the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="8e971-107">如需詳細資訊，請參閱《 [線上叢書》中的](../relational-databases/database-mail/database-mail-configuration-objects.md) Database Mail 組態物件 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8e971-107">For more information about Database Mail, see [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="when-notifications-are-sent"></a><span data-ttu-id="8e971-108">通知的傳送時間</span><span class="sxs-lookup"><span data-stu-id="8e971-108">When Notifications Are Sent</span></span>  
 <span data-ttu-id="8e971-109">設定通知之後，在下列情況下會自動傳送電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="8e971-109">After notifications are configured, automated email notifications can be sent in the following instances.</span></span>  
  
|<span data-ttu-id="8e971-110">執行個體</span><span class="sxs-lookup"><span data-stu-id="8e971-110">Instance</span></span>|<span data-ttu-id="8e971-111">描述</span><span class="sxs-lookup"><span data-stu-id="8e971-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8e971-112">資料的商務規則驗證失敗</span><span class="sxs-lookup"><span data-stu-id="8e971-112">Data fails business rule validation</span></span>|<span data-ttu-id="8e971-113">個別商務規則必須設定為屬性值的商務規則驗證失敗時傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="8e971-113">Individual business rules must be configured to send email when an attribute value fails business rule validation.</span></span> <span data-ttu-id="8e971-114">如需詳細資訊，請參閱 [設定商務規則來傳送通知 &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md)中設定通知。</span><span class="sxs-lookup"><span data-stu-id="8e971-114">For more information, see [Configure Business Rules to Send Notifications &#40;Master Data Services&#41;](configure-business-rules-to-send-notifications-master-data-services.md).</span></span>|  
|<span data-ttu-id="8e971-115">模型版本狀態變更</span><span class="sxs-lookup"><span data-stu-id="8e971-115">Model version status changes</span></span>|<span data-ttu-id="8e971-116">每次模型版本的狀態變更時，身為模型管理員的使用者會自動接收通知。</span><span class="sxs-lookup"><span data-stu-id="8e971-116">Each time a model version's status changes, users that are model administrators receive notifications automatically.</span></span> <span data-ttu-id="8e971-117">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8e971-117">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>|  
  
## <a name="system-settings"></a><span data-ttu-id="8e971-118">系統設定</span><span class="sxs-lookup"><span data-stu-id="8e971-118">System Settings</span></span>  
 <span data-ttu-id="8e971-119">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有一些設定會影響通知。</span><span class="sxs-lookup"><span data-stu-id="8e971-119">There are settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect notifications.</span></span> <span data-ttu-id="8e971-120">您可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫 [系統設定] 資料表中調整這些設定。</span><span class="sxs-lookup"><span data-stu-id="8e971-120">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="8e971-121">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8e971-121">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8e971-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="8e971-122">Related Tasks</span></span>  
  
|<span data-ttu-id="8e971-123">工作描述</span><span class="sxs-lookup"><span data-stu-id="8e971-123">Task Description</span></span>|<span data-ttu-id="8e971-124">主題</span><span class="sxs-lookup"><span data-stu-id="8e971-124">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="8e971-125">設定 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 傳送電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="8e971-125">Configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to send email notifications.</span></span>|[<span data-ttu-id="8e971-126">設定電子郵件通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8e971-126">Configure Email Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-email-notifications-master-data-services.md)|  
|<span data-ttu-id="8e971-127">設定 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在屬性值變更時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="8e971-127">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when attribute values change.</span></span>|[<span data-ttu-id="8e971-128">設定商務規則來傳送通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8e971-128">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](configure-business-rules-to-send-notifications-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="8e971-129">相關內容</span><span class="sxs-lookup"><span data-stu-id="8e971-129">Related Content</span></span>  
  
-   [<span data-ttu-id="8e971-130">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8e971-130">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="8e971-131">版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8e971-131">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="8e971-132">疑難排解電子郵件通知 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="8e971-132">Troubleshooting Email Notifications (Master Data Services)</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)  
  
  
