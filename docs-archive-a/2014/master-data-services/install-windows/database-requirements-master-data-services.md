---
title: 資料庫需求 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: fe731839-c5c4-4884-bb6a-644eca28bb30
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b17c04db6805ea412b70644d2ee2c0b7da93b2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599546"
---
# <a name="database-requirements-master-data-services"></a><span data-ttu-id="d677f-102">資料庫需求 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d677f-102">Database Requirements (Master Data Services)</span></span>
  <span data-ttu-id="d677f-103">所有主要資料都儲存在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d677f-103">All master data is stored in a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="d677f-104">裝載這個資料庫的電腦必須執行的實例 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d677f-104">The computer that hosts this database must run an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="d677f-105">使用 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 可在本機或遠端電腦上建立及設定 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d677f-105">Use [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] to create and configure the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database on either a local or a remote computer.</span></span> <span data-ttu-id="d677f-106">如果您將資料庫從某個環境移到另一個環境，就可以將 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 服務和 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 關聯至位於新位置的資料庫，藉以在新的環境中維護資訊。</span><span class="sxs-lookup"><span data-stu-id="d677f-106">If you move the database from one environment to another, you can maintain the information in a new environment by associating the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service and [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] to the database in its new location.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d677f-107">安裝 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 元件的任何電腦都必須獲得授權。</span><span class="sxs-lookup"><span data-stu-id="d677f-107">Any computer on which you install components of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] must be licensed.</span></span> <span data-ttu-id="d677f-108">如需詳細資訊，請參閱使用者授權合約 (EULA)。</span><span class="sxs-lookup"><span data-stu-id="d677f-108">For more information, refer to the End User License Agreement (EULA).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d677f-109">需求</span><span class="sxs-lookup"><span data-stu-id="d677f-109">Requirements</span></span>  
 <span data-ttu-id="d677f-110">建立 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫之前，請確定是否符合下列需求。</span><span class="sxs-lookup"><span data-stu-id="d677f-110">Before you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, ensure the following requirements are met.</span></span>  
  
### <a name="sql-server-edition"></a><span data-ttu-id="d677f-111">SQL Server 版本</span><span class="sxs-lookup"><span data-stu-id="d677f-111">SQL Server Edition</span></span>  
 <span data-ttu-id="d677f-112">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫可以裝載在下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本上：</span><span class="sxs-lookup"><span data-stu-id="d677f-112">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database can be hosted on the following editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="d677f-113">Business Intelligence (64 位元) x64</span><span class="sxs-lookup"><span data-stu-id="d677f-113">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="d677f-114">Enterprise (64 位元) x64</span><span class="sxs-lookup"><span data-stu-id="d677f-114">Enterprise (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="d677f-115">Developer (64 位元) x64</span><span class="sxs-lookup"><span data-stu-id="d677f-115">Developer (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="d677f-116">Business Intelligence (64 位元) x64</span><span class="sxs-lookup"><span data-stu-id="d677f-116">Business Intelligence (64-bit) x64</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="d677f-117">Enterprise (64 位元) x64 - 只能從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise 升級</span><span class="sxs-lookup"><span data-stu-id="d677f-117">Enterprise (64-bit) x64 - Upgrade from [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise only</span></span>  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="d677f-118">Developer (64 位元) x64</span><span class="sxs-lookup"><span data-stu-id="d677f-118">Developer (64-bit) x64</span></span>  
  
-   <span data-ttu-id="d677f-119">Microsoft SQL Server 2008 R2 Enterprise (64 位元) x64</span><span class="sxs-lookup"><span data-stu-id="d677f-119">Microsoft SQL Server 2008 R2 Enterprise (64-bit) x64</span></span>  
  
-   <span data-ttu-id="d677f-120">Microsoft SQL Server 2008 R2 Developer (64 位元) x64</span><span class="sxs-lookup"><span data-stu-id="d677f-120">Microsoft SQL Server 2008 R2 Developer (64-bit) x64</span></span>  
  
 <span data-ttu-id="d677f-121">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="d677f-121">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
### <a name="operating-system"></a><span data-ttu-id="d677f-122">作業系統</span><span class="sxs-lookup"><span data-stu-id="d677f-122">Operating System</span></span>  
 <span data-ttu-id="d677f-123">如需有關支援的 Windows 作業系統和其他需求的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，請參閱[安裝 SQL Server 2014 的硬體和軟體需求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d677f-123">For information about the supported Windows operating systems and other requirements for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)], see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
### <a name="accounts-and-permissions"></a><span data-ttu-id="d677f-124">帳戶和權限</span><span class="sxs-lookup"><span data-stu-id="d677f-124">Accounts and Permissions</span></span>  
  
|<span data-ttu-id="d677f-125">類型</span><span class="sxs-lookup"><span data-stu-id="d677f-125">Type</span></span>|<span data-ttu-id="d677f-126">描述</span><span class="sxs-lookup"><span data-stu-id="d677f-126">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="d677f-127">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="d677f-127">User account</span></span>|<span data-ttu-id="d677f-128">在 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]中，您可以使用 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，來主控 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d677f-128">In [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], you can use a Windows account or a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account to connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to host the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="d677f-129">此使用者帳戶必須屬於 \*\*\*\* 執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d677f-129">The user account must belong to the **sysadmin** server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="d677f-130">如需有關 **系統管理員** 角色的詳細資訊，請參閱 [伺服器層級角色](../../relational-databases/security/authentication-access/server-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="d677f-130">For more information about the **sysadmin** role, see [Server-Level Roles](../../relational-databases/security/authentication-access/server-level-roles.md).</span></span>|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] <span data-ttu-id="d677f-131">系統管理員帳戶</span><span class="sxs-lookup"><span data-stu-id="d677f-131">administrator account</span></span>|<span data-ttu-id="d677f-132">當您建立 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫時，必須指定要成為 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 系統管理員的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d677f-132">When you create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, you must specify a domain user account to be the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="d677f-133">對於所有與這個資料庫有關聯的 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式，這位使用者都可以更新所有功能區域中的所有模型和所有資料。</span><span class="sxs-lookup"><span data-stu-id="d677f-133">For all [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web applications associated with this database, this user can update all models and all data in all functional areas.</span></span> <span data-ttu-id="d677f-134">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d677f-134">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>|  
  
### <a name="database-backup"></a><span data-ttu-id="d677f-135">資料庫備份</span><span class="sxs-lookup"><span data-stu-id="d677f-135">Database Backup</span></span>  
 <span data-ttu-id="d677f-136">最佳做法是根據環境的需求，每天在活動量低的時間備份一次完整的資料庫，然後更頻繁地備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="d677f-136">As a best practice, back up the full database daily at a time of low activity and back up transaction logs more frequently depending on the needs of your environment.</span></span> <span data-ttu-id="d677f-137">如需資料庫備份的詳細資訊，請參閱[備份概觀 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d677f-137">For more information about database backups, see [Backup Overview &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d677f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d677f-138">See Also</span></span>  
 <span data-ttu-id="d677f-139">[安裝 Master Data Services](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d677f-139">[Install Master Data Services](install-master-data-services.md) </span></span>  
 <span data-ttu-id="d677f-140">[建立 Master Data Services 資料庫](create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="d677f-140">[Create a Master Data Services Database](create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="d677f-141">[Master Data Services 資料庫](../master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="d677f-141">[Master Data Services Database](../master-data-services-database.md) </span></span>  
 <span data-ttu-id="d677f-142">[[連接到 Master Data Services 資料庫] 對話方塊](../connect-to-a-master-data-services-database-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="d677f-142">[Connect to a Master Data Services Database Dialog Box](../connect-to-a-master-data-services-database-dialog-box.md) </span></span>  
 [<span data-ttu-id="d677f-143">建立資料庫精靈 &#40;Master Data Services 組態管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="d677f-143">Create Database Wizard &#40;Master Data Services Configuration Manager&#41;</span></span>](../create-database-wizard-master-data-services-configuration-manager.md)  
  
  
