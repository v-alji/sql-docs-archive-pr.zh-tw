---
title: 管理服務的安全性需求 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent service, security
- services [SQL Server], security
- SQL Server services, security
- WMI Providers [SQL Server]
- server configuration [SQL Server]
- security [SQL Server], services
- services [SQL Server], WMI
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46a777858c01bf3057093d34b29b9a2093668e97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706742"
---
# <a name="security-requirements-for-managing-services"></a><span data-ttu-id="917c9-102">管理服務的安全性需求</span><span class="sxs-lookup"><span data-stu-id="917c9-102">Security Requirements for Managing Services</span></span>
  <span data-ttu-id="917c9-103">若要管理 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，請使用 SQL Server 組態管理員或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="917c9-103">To manage the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Services, use either SQL Server Configuration Manager or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="917c9-104">請使用「叢集管理員」來管理叢集伺服器的服務。</span><span class="sxs-lookup"><span data-stu-id="917c9-104">Manage the services on clustered servers with the Cluster Administrator.</span></span>  
  
 <span data-ttu-id="917c9-105">若要管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務和設定伺服器組態選項，您必須是 **伺服器管理員 (serveradmin)** 固定伺服器角色或 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="917c9-105">To manage the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service and set the server configuration options, you must be a member of the **serveradmin** fixed server role or the **sysadmin** fixed server role.</span></span> <span data-ttu-id="917c9-106">Windows **Administrators** 群組的成員可以啟動和停止服務，還能設定 Windows 提供的伺服器選項。</span><span class="sxs-lookup"><span data-stu-id="917c9-106">Members of the Windows **Administrators** group can start and stop services and configure the server options that Windows provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="917c9-107">服務使用的帳戶必須設定正確的網域、檔案系統和登錄權限，才能正確運作。</span><span class="sxs-lookup"><span data-stu-id="917c9-107">To operate properly, the accounts used for the services must be configured with the correct domain, file system, and registry permissions.</span></span> <span data-ttu-id="917c9-108">如需必要權限的資訊，請參閱 [設定 Windows 服務帳戶與權限](configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="917c9-108">For information about the required permissions, see [Configure Windows Service Accounts and Permissions](configure-windows-service-accounts-and-permissions.md).</span></span>  
  
## <a name="windows-management-instrumentation"></a><span data-ttu-id="917c9-109">Windows Management Instrumentation</span><span class="sxs-lookup"><span data-stu-id="917c9-109">Windows Management Instrumentation</span></span>  
 <span data-ttu-id="917c9-110">「SQL Server 組態管理員」與 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 會使用 Windows Management Instrumentation (WMI)，來顯示和修改部份伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="917c9-110">SQL Server Configuration Manager and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] use Windows Management Instrumentation (WMI) to display and modify some of the server properties.</span></span> <span data-ttu-id="917c9-111">若要管理服務和取得服務狀態，使用者必須擁有存取 WMI 物件的權限。</span><span class="sxs-lookup"><span data-stu-id="917c9-111">To manage services and obtain the status of the services, the user must have rights to access the WMI object.</span></span> <span data-ttu-id="917c9-112">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，以下伺服器屬性頁面會使用 WMI：</span><span class="sxs-lookup"><span data-stu-id="917c9-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the following server property pages use WMI:</span></span>  
  
-   <span data-ttu-id="917c9-113">自動啟動服務</span><span class="sxs-lookup"><span data-stu-id="917c9-113">Autostart Services</span></span>  
  
-   <span data-ttu-id="917c9-114">啟動參數</span><span class="sxs-lookup"><span data-stu-id="917c9-114">Startup Parameters</span></span>  
  
-   <span data-ttu-id="917c9-115">安全性</span><span class="sxs-lookup"><span data-stu-id="917c9-115">Security</span></span>  
  
-   <span data-ttu-id="917c9-116">其他伺服器設定</span><span class="sxs-lookup"><span data-stu-id="917c9-116">Misc Server Settings</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="917c9-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="917c9-117">Related Tasks</span></span>  
 [<span data-ttu-id="917c9-118">設定 WMI 在 SQL Server 工具中顯示伺服器狀態</span><span class="sxs-lookup"><span data-stu-id="917c9-118">Configure WMI to Show Server Status in SQL Server Tools</span></span>](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## <a name="related-content"></a><span data-ttu-id="917c9-119">相關內容</span><span class="sxs-lookup"><span data-stu-id="917c9-119">Related Content</span></span>  
 [<span data-ttu-id="917c9-120">組態管理的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="917c9-120">WMI Provider for Configuration Management Concepts</span></span>](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
