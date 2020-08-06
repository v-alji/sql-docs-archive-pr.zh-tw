---
title: 控制報表散發 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], report distribution
- subscriptions [Reporting Services], e-mail
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- subscriptions [Reporting Services], security
- mail [Reporting Services]
ms.assetid: 8f15e2c6-a647-4b05-a519-1743b5d8654c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: de8a27801ef89f10bf303cee17d1c2d0e1081c5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584296"
---
# <a name="control-report-distribution"></a><span data-ttu-id="b1e94-102">控制報表散發</span><span class="sxs-lookup"><span data-stu-id="b1e94-102">Control Report Distribution</span></span>
  <span data-ttu-id="b1e94-103">您可以設定報表伺服器，以減少與電子郵件和檔案共用散發相關聯的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="b1e94-103">You can configure a report server to reduce the security risks associated with e-mail and file share distribution.</span></span>  
  
## <a name="securing-reports"></a><span data-ttu-id="b1e94-104">保護報表的安全</span><span class="sxs-lookup"><span data-stu-id="b1e94-104">Securing Reports</span></span>  
 <span data-ttu-id="b1e94-105">控制報表散發的第一個步驟是保護報表的安全，以避免未授權的存取。</span><span class="sxs-lookup"><span data-stu-id="b1e94-105">The first step in controlling report distribution is to secure the report against unauthorized access.</span></span> <span data-ttu-id="b1e94-106">若要在訂閱中使用，報表對個別傳遞都必須使用相同的預存認證組。</span><span class="sxs-lookup"><span data-stu-id="b1e94-106">To be used in a subscription, a report must use a stored set of credentials that do not vary for individual deliveries.</span></span> <span data-ttu-id="b1e94-107">可以存取報表伺服器上之報表的任何使用者，都可以執行報表，並可能散發報表。</span><span class="sxs-lookup"><span data-stu-id="b1e94-107">Any user who can access the report on the report server can run it and possibly distribute it.</span></span> <span data-ttu-id="b1e94-108">若要避免發生此情況，您必須限制只有需要報表的使用者才可以存取報表。</span><span class="sxs-lookup"><span data-stu-id="b1e94-108">To prevent this from occurring, you must limit report access to only those users who require it.</span></span> <span data-ttu-id="b1e94-109">如需詳細資訊，請參閱[保護報表和資源](security/secure-reports-and-resources.md)和[安全資料夾](security/secure-folders.md)。</span><span class="sxs-lookup"><span data-stu-id="b1e94-109">For more information, see [Secure Reports and Resources](security/secure-reports-and-resources.md) and [Secure Folders](security/secure-folders.md).</span></span>  
  
 <span data-ttu-id="b1e94-110">使用資料庫安全性以授權存取的高度機密報表，無法透過訂閱方式散發。</span><span class="sxs-lookup"><span data-stu-id="b1e94-110">Highly confidential reports that use database security to authorize access cannot be distributed by way of subscription.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1e94-111">報表會當成檔案傳輸。</span><span class="sxs-lookup"><span data-stu-id="b1e94-111">Reports are transported as files.</span></span> <span data-ttu-id="b1e94-112">適用於檔案的風險和保護，同樣適用於儲存在磁碟或當做附加檔案傳送的報表。</span><span class="sxs-lookup"><span data-stu-id="b1e94-112">The risks and safeguards that apply to files apply equally to reports that are saved to disk or sent as attachments.</span></span> <span data-ttu-id="b1e94-113">任何對檔案有存取權的使用者都可以自由地散發或使用檔案。</span><span class="sxs-lookup"><span data-stu-id="b1e94-113">Any user who has access to a file can distribute or use the file at his or her discretion.</span></span>  
  
## <a name="controlling-e-mail-delivery"></a><span data-ttu-id="b1e94-114">控制電子郵件傳遞</span><span class="sxs-lookup"><span data-stu-id="b1e94-114">Controlling E-Mail Delivery</span></span>  
 <span data-ttu-id="b1e94-115">您可以設定報表伺服器，來限制只能散發電子郵件至特定主機網域。</span><span class="sxs-lookup"><span data-stu-id="b1e94-115">You can configure a report server to limit e-mail distribution to specific host domains.</span></span> <span data-ttu-id="b1e94-116">例如，您可以防止報表伺服器將報表傳遞至 RSReportServer 組態檔中所列網域以外的所有網域。</span><span class="sxs-lookup"><span data-stu-id="b1e94-116">For example, you can prevent a report server from delivering a report to all domains except those listed in the RSReportServer configuration file.</span></span>  
  
 <span data-ttu-id="b1e94-117">您也可以組態組態設定，以隱藏訂閱中的 [收件者]  欄位。</span><span class="sxs-lookup"><span data-stu-id="b1e94-117">You can also set configuration settings to hide the **To** field in a subscription.</span></span> <span data-ttu-id="b1e94-118">在此情況下，報表只會傳遞給定義訂閱的使用者。</span><span class="sxs-lookup"><span data-stu-id="b1e94-118">In this case, reports are delivered only to the user defining the subscription.</span></span> <span data-ttu-id="b1e94-119">然而，在報表傳送給使用者之後，您無法明確地防止其被轉送。</span><span class="sxs-lookup"><span data-stu-id="b1e94-119">However, after a report is sent to a user, you cannot explicitly prevent it from being forwarded.</span></span>  
  
 <span data-ttu-id="b1e94-120">控制報表散發最有效的方式，是將報表伺服器設定為只傳送報表伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="b1e94-120">The most effective way to control report distribution is to configure a report server to send only a report server URL.</span></span> <span data-ttu-id="b1e94-121">報表伺服器使用 Windows 驗證和以角色為基礎的驗證模型，來控制對報表的存取。</span><span class="sxs-lookup"><span data-stu-id="b1e94-121">The report server uses Windows Authentication and a role-based authorization model to control access to a report.</span></span> <span data-ttu-id="b1e94-122">如果使用者意外地透過電子郵件接收到未被授權檢視的報表，報表伺服器將不會顯示報表。</span><span class="sxs-lookup"><span data-stu-id="b1e94-122">If a user accidentally receives through e-mail a report that he or she is not authorized to view, the report server will not display the report.</span></span>  
  
## <a name="controlling-file-share-delivery"></a><span data-ttu-id="b1e94-123">控制檔案共用傳遞</span><span class="sxs-lookup"><span data-stu-id="b1e94-123">Controlling File Share Delivery</span></span>  
 <span data-ttu-id="b1e94-124">檔案共用傳遞用於傳送報表到硬碟中的檔案。</span><span class="sxs-lookup"><span data-stu-id="b1e94-124">File share delivery is used to send a report to a file on a hard disk.</span></span> <span data-ttu-id="b1e94-125">檔案儲存至磁碟後，就不再受到報表伺服器用於控制使用者存取之以角色為基礎的安全性模型的規範。</span><span class="sxs-lookup"><span data-stu-id="b1e94-125">After the file has been saved to disk, it is no longer subject to the role-based security model that the report server uses to control user access.</span></span> <span data-ttu-id="b1e94-126">若要保護已傳遞至磁碟的報表，您可以為檔案本身或包含檔案的資料夾加上存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="b1e94-126">To secure a report that has been delivered to disk, you can place Access Control Lists (ACLs) on the file itself or on the folder that contains it.</span></span> <span data-ttu-id="b1e94-127">視您的作業系統而定，可能有其他的安全性選項。</span><span class="sxs-lookup"><span data-stu-id="b1e94-127">Additional security options might be available, depending on your operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e94-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1e94-128">See Also</span></span>  
 <span data-ttu-id="b1e94-129">[針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="b1e94-129">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="b1e94-130">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="b1e94-130">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="b1e94-131">建立及管理原生模式報表伺服器的訂閱</span><span class="sxs-lookup"><span data-stu-id="b1e94-131">Create and Manage Subscriptions for Native Mode Report Servers</span></span>](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)  
  
  
