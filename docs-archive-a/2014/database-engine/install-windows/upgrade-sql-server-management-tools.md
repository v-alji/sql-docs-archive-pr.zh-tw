---
title: 升級 SQL Server 管理工具 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- management tools, upgrading
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
author: stevestein
ms.author: sstein
ms.openlocfilehash: b6424d27a2bc7ecfc60ed01ce144e92802fdaea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594146"
---
# <a name="upgrade-sql-server-management-tools"></a><span data-ttu-id="fc02b-102">升級 SQL Server 管理工具</span><span class="sxs-lookup"><span data-stu-id="fc02b-102">Upgrade SQL Server Management Tools</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="fc02b-103">支援從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更新版本升級。</span><span class="sxs-lookup"><span data-stu-id="fc02b-103">supports upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later.</span></span> <span data-ttu-id="fc02b-104">本主題說明升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理工具和管理元件 (如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent、Database Mail、維護計畫、XPStar 和 XPWeb) 的支援與行為。</span><span class="sxs-lookup"><span data-stu-id="fc02b-104">This topic documents support and behavior for upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Tools and management components such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Database Mail, Maintenance Plans, XPStar, and XPWeb.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fc02b-105">若是本機安裝，您必須以管理員身分執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="fc02b-105">For local installations, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup as an administrator.</span></span> <span data-ttu-id="fc02b-106">如果您是從遠端共用位置執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="fc02b-106">If you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="fc02b-107">已知的升級問題</span><span class="sxs-lookup"><span data-stu-id="fc02b-107">Known Upgrade Issues</span></span>  
 <span data-ttu-id="fc02b-108">在您升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之前，請先考慮以下問題：</span><span class="sxs-lookup"><span data-stu-id="fc02b-108">Consider the following issues before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:</span></span>  
  
### <a name="for-all-upgrade-scenarios"></a><span data-ttu-id="fc02b-109">如果是全部升級狀況：</span><span class="sxs-lookup"><span data-stu-id="fc02b-109">For all upgrade scenarios:</span></span>  
  
-   <span data-ttu-id="fc02b-110">在升級 MSX 伺服器之前，應該要升級所有的 TSX 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fc02b-110">All TSX servers should be upgraded before the MSX server is upgraded.</span></span> <span data-ttu-id="fc02b-111">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中 MSX/TSX 的詳細資訊，請參閱 [將整個企業的管理自動化](../../ssms/agent/automated-administration-across-an-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="fc02b-111">For more information about MSX/TSX in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Automated Administration Across an Enterprise](../../ssms/agent/automated-administration-across-an-enterprise.md).</span></span>  
  
-   <span data-ttu-id="fc02b-112">您必須同時升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的所有元件。</span><span class="sxs-lookup"><span data-stu-id="fc02b-112">All components in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be upgraded at the same time.</span></span> <span data-ttu-id="fc02b-113">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體內， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 和 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]元件的版本號碼都必須相同。</span><span class="sxs-lookup"><span data-stu-id="fc02b-113">Version numbers of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components must be the same in an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="fc02b-114">當您升級到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可以將元件加入到現有的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="fc02b-114">You can add components to an existing installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] at the time that you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="fc02b-115">如需詳細資訊，請參閱[使用安裝精靈升級至 SQL Server 2014 &#40;安裝程式&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="fc02b-115">For more information, see [Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fc02b-116">用戶端工具 (例如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor、sqlcmd 和 osql) 不會升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc02b-116">Client Tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, sqlcmd, and osql are not upgraded to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="fc02b-117">用戶端工具改為使用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的工具進行並存執行。</span><span class="sxs-lookup"><span data-stu-id="fc02b-117">Instead, Client Tools run side-by-side with tools from previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="fc02b-118">支援從舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端工具匯入設定。</span><span class="sxs-lookup"><span data-stu-id="fc02b-118">supports importing settings from earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Tools.</span></span>  
  
-   <span data-ttu-id="fc02b-119">在升級期間，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的驗證將會更新為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證到 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="fc02b-119">Authentication from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will be updated from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to Windows Authentication during upgrade.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fc02b-120">中不支援 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]驗證。</span><span class="sxs-lookup"><span data-stu-id="fc02b-120">Authentication is not supported in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="fc02b-121">在升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的期間，將會保留作業與警示的資料。</span><span class="sxs-lookup"><span data-stu-id="fc02b-121">Data for jobs and alerts will be preserved during upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="fc02b-122">如果要升級的執行個體上有使用 SQLMail，關聯的 XP 將會在升級之後受到支援並啟用。</span><span class="sxs-lookup"><span data-stu-id="fc02b-122">If SQLMail is being used in the instance to be upgraded, associated XPs will be supported and enabled after the upgrade.</span></span> <span data-ttu-id="fc02b-123">否則會將其關閉。</span><span class="sxs-lookup"><span data-stu-id="fc02b-123">Otherwise, they will be off.</span></span>  
  
-   <span data-ttu-id="fc02b-124">Database Mail (也稱為 SQLiMail) 將會與 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]元件一起升級。</span><span class="sxs-lookup"><span data-stu-id="fc02b-124">Database Mail, also known as SQLiMail, will be upgraded with the [!INCLUDE[ssDE](../../includes/ssde-md.md)] component of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="fc02b-125">根據預設，Database Mail 將會在升級之後關閉。</span><span class="sxs-lookup"><span data-stu-id="fc02b-125">By default, Database Mail will be off after upgrade.</span></span> <span data-ttu-id="fc02b-126">任何結構描述更新都應該在升級之後與更新指令碼一致。</span><span class="sxs-lookup"><span data-stu-id="fc02b-126">Any schema updates should be reconciled with an update script after upgrade.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc02b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc02b-127">See Also</span></span>  
 <span data-ttu-id="fc02b-128">[支援的版本與版本升級](supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="fc02b-128">[Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="fc02b-129">[回溯相容性](../../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="fc02b-129">[Backward Compatibility](../../getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="fc02b-130">使用安裝精靈 &#40;安裝程式升級至 SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="fc02b-130">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
