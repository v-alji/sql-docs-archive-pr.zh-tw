---
title: 服務帳戶 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58e49467a28e816c6592b1ded212b5aea0e6bc55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701770"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a><span data-ttu-id="ad081-102">服務帳戶 (設定資料庫鏡像安全性精靈)</span><span class="sxs-lookup"><span data-stu-id="ad081-102">Service Accounts (Configure Database Mirroring Security Wizard)</span></span>
  <span data-ttu-id="ad081-103">在使用 Windows 驗證時，如果伺服器執行個體使用不同的帳戶，請指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad081-103">When using Windows Authentication, if the server instances use different accounts, specify the service accounts for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ad081-104">這些服務帳戶必須全都是網域帳戶 (在同一或受信任的網域中)。</span><span class="sxs-lookup"><span data-stu-id="ad081-104">These service accounts must all be domain accounts (in the same or trusted domains).</span></span>  
  
 <span data-ttu-id="ad081-105">如果所有伺服器執行個體都使用相同的網域帳戶，或是使用以憑證為基礎的驗證，則請將欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="ad081-105">If all the server instances use the same domain account or use certificate-based authentication, leave the fields blank.</span></span> <span data-ttu-id="ad081-106">只要按一下 **[完成]**，精靈就會根據目前精靈的帳戶自動設定帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad081-106">Simply click **Finish**, and the wizard automatically configures the accounts based on the account of the current wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ad081-107">如果伺服器執行個體的資料庫鏡像端點設定為使用憑證，則服務帳戶欄位必須保留空白。</span><span class="sxs-lookup"><span data-stu-id="ad081-107">If the database mirroring endpoints of the server instances are configured to use certificates, you must leave the service account fields empty.</span></span>  
  
 <span data-ttu-id="ad081-108">**若要使用 SQL Server Management Studio 設定資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="ad081-108">**To configure database mirroring by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="ad081-109">使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ad081-109">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
-   [<span data-ttu-id="ad081-110">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="ad081-110">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="ad081-111">選項。</span><span class="sxs-lookup"><span data-stu-id="ad081-111">Options</span></span>  
 <span data-ttu-id="ad081-112">**主體**</span><span class="sxs-lookup"><span data-stu-id="ad081-112">**Principal**</span></span>  
 <span data-ttu-id="ad081-113">指定主體伺服器執行個體的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad081-113">Specify the service account of the principal server instance.</span></span> <span data-ttu-id="ad081-114">以大寫輸入網域名稱：</span><span class="sxs-lookup"><span data-stu-id="ad081-114">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="ad081-115">*DOMAINNAME* \\使用者*名稱*</span><span class="sxs-lookup"><span data-stu-id="ad081-115">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="ad081-116">**鏡像**</span><span class="sxs-lookup"><span data-stu-id="ad081-116">**Mirror**</span></span>  
 <span data-ttu-id="ad081-117">指定鏡像伺服器執行個體的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad081-117">Specify the service account of the mirror server instance.</span></span> <span data-ttu-id="ad081-118">以大寫輸入網域名稱：</span><span class="sxs-lookup"><span data-stu-id="ad081-118">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="ad081-119">*DOMAINNAME* \\使用者*名稱*</span><span class="sxs-lookup"><span data-stu-id="ad081-119">*DOMAINNAME*\\*username*</span></span>  
  
 <span data-ttu-id="ad081-120">**證明**</span><span class="sxs-lookup"><span data-stu-id="ad081-120">**Witness**</span></span>  
 <span data-ttu-id="ad081-121">指定見證伺服器執行個體的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="ad081-121">Specify the service account of the witness server instance.</span></span> <span data-ttu-id="ad081-122">以大寫輸入網域名稱：</span><span class="sxs-lookup"><span data-stu-id="ad081-122">Enter the domain name in upper case:</span></span>  
  
 <span data-ttu-id="ad081-123">*DOMAINNAME* \\使用者*名稱*</span><span class="sxs-lookup"><span data-stu-id="ad081-123">*DOMAINNAME*\\*username*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad081-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad081-124">See Also</span></span>  
 <span data-ttu-id="ad081-125">[資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="ad081-125">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="ad081-126">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ad081-126">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="ad081-127">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ad081-127">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="ad081-128">設定資料庫鏡像的登入帳戶，或 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ad081-128">Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
