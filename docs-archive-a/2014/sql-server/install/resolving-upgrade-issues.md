---
title: 解決升級問題 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c00b08d40bc8c17013e6af19b5d11b0b7ad78c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606592"
---
# <a name="resolving-upgrade-issues"></a><span data-ttu-id="9647d-102">解決升級問題</span><span class="sxs-lookup"><span data-stu-id="9647d-102">Resolving Upgrade Issues</span></span>
  <span data-ttu-id="9647d-103">本節中的主題描述可以偵測以及無法偵測但會影響升級或升級後續經驗的升級問題。</span><span class="sxs-lookup"><span data-stu-id="9647d-103">The topics in this section describe upgrade issues that can be detected as well as those that cannot be detected, but that might affect the upgrade or post-upgrade experience.</span></span> <span data-ttu-id="9647d-104">這些問題會依照 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件組織。</span><span class="sxs-lookup"><span data-stu-id="9647d-104">The issues are organized by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9647d-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="9647d-105">In This Section</span></span>  
  
-   [<span data-ttu-id="9647d-106">最新升級問題</span><span class="sxs-lookup"><span data-stu-id="9647d-106">Late-Breaking Upgrade Issues</span></span>](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [<span data-ttu-id="9647d-107">資料庫引擎升級問題</span><span class="sxs-lookup"><span data-stu-id="9647d-107">Database Engine Upgrade Issues</span></span>](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [<span data-ttu-id="9647d-108">全文檢索搜尋升級問題</span><span class="sxs-lookup"><span data-stu-id="9647d-108">Full-Text Search Upgrade Issues</span></span>](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [<span data-ttu-id="9647d-109">複寫升級問題</span><span class="sxs-lookup"><span data-stu-id="9647d-109">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [<span data-ttu-id="9647d-110">&#40;Upgrade Advisor Reporting Services 升級問題&#41;</span><span class="sxs-lookup"><span data-stu-id="9647d-110">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [<span data-ttu-id="9647d-111">SQL Server Agent 升級問題</span><span class="sxs-lookup"><span data-stu-id="9647d-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a><span data-ttu-id="9647d-112">妨礙升級的問題</span><span class="sxs-lookup"><span data-stu-id="9647d-112">Issues That Prevent Upgrading</span></span>  
 <span data-ttu-id="9647d-113">舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中有少數組態或設定會使您無法升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9647d-113">A few configurations or settings in a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can prevent you from upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9647d-114">如果安裝程式在您安裝 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時偵測到這些問題，它會停止升級程序並要求您執行 Upgrade Advisor 並修正任何封鎖的問題。</span><span class="sxs-lookup"><span data-stu-id="9647d-114">If Setup detects these issues when you install [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Setup stops the upgrade process and requests that you run Upgrade Advisor and fix any blocking issues.</span></span>  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 <span data-ttu-id="9647d-115">如果下列工作列在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 升級報表上，您就必須執行必要的動作，然後才能升級為 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="9647d-115">If the following tasks are listed on the [!INCLUDE[ssDE](../../includes/ssde-md.md)] upgrade report, you must perform the required actions before you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]:</span></span>  
  
-   [<span data-ttu-id="9647d-116">中斷連結資料庫識別碼 32767</span><span class="sxs-lookup"><span data-stu-id="9647d-116">Detach database ID 32767</span></span>](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [<span data-ttu-id="9647d-117">為符合固定伺服器角色名稱的登入重新命名</span><span class="sxs-lookup"><span data-stu-id="9647d-117">Rename logins matching fixed server role names</span></span>](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [<span data-ttu-id="9647d-118">為使用者 sys 重新命名</span><span class="sxs-lookup"><span data-stu-id="9647d-118">Rename user sys</span></span>](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [<span data-ttu-id="9647d-119">使用 sp_rename 重新命名重複的索引名稱</span><span class="sxs-lookup"><span data-stu-id="9647d-119">Use sp_rename to rename duplicate index name</span></span>](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a><span data-ttu-id="9647d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9647d-120">See Also</span></span>  
 [<span data-ttu-id="9647d-121">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="9647d-121">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
