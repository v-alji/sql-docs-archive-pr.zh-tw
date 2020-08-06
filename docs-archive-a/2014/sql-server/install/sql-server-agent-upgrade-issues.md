---
title: SQL Server Agent 升級問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server Agent
- SQL Server Agent, upgrades
ms.assetid: 77e303ff-febd-4103-ae5d-6e5b85bc8009
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ac234a757510af5ebfac261ea6d3e7e57d2f426f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700621"
---
# <a name="sql-server-agent-upgrade-issues"></a><span data-ttu-id="c32ee-102">SQL Server Agent 升級問題</span><span class="sxs-lookup"><span data-stu-id="c32ee-102">SQL Server Agent Upgrade Issues</span></span>
  <span data-ttu-id="c32ee-103">下列主題描述的是可能會影響升級的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式問題。</span><span class="sxs-lookup"><span data-stu-id="c32ee-103">The following topics describe the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent issues that might affect an upgrade.</span></span> <span data-ttu-id="c32ee-104">這些主題會描述一些可讓您採取的動作，以便減少這些變更對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境的影響。</span><span class="sxs-lookup"><span data-stu-id="c32ee-104">The topics describe actions that you can take to help reduce the effect of these changes on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c32ee-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="c32ee-105">In This Section</span></span>  
  
-   [<span data-ttu-id="c32ee-106">已取代資料庫維護計畫</span><span class="sxs-lookup"><span data-stu-id="c32ee-106">Database maintenance plans superseded</span></span>](../../../2014/sql-server/install/database-maintenance-plans-superseded.md)  
  
-   [<span data-ttu-id="c32ee-107">只有系統管理員使用者可以將作業步驟記錄檔寫入檔案系統</span><span class="sxs-lookup"><span data-stu-id="c32ee-107">Only sysadmin users can write job step log files to the file system</span></span>](../../../2014/sql-server/install/only-sysadmin-users-can-write-job-step-log-files-to-the-file-system.md)  
  
-   [<span data-ttu-id="c32ee-108">使用新的預存程序取代 xp_sqlagent_proxy_account 擴充預存程序的使用方式</span><span class="sxs-lookup"><span data-stu-id="c32ee-108">Replace usage of the xp_sqlagent_proxy_account extended stored procedure with new stored procedures</span></span>](../../../2014/sql-server/install/replace-xp-sqlagent-proxy-account-extended-sp-with-new-stored-procedures.md)  
  
-   [<span data-ttu-id="c32ee-109">SQL Server Agent 記錄傳送作業類別目錄會造成升級失敗</span><span class="sxs-lookup"><span data-stu-id="c32ee-109">SQL Server Agent log shipping job category causes upgrade to fail</span></span>](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)  
  
-   [<span data-ttu-id="c32ee-110">SQL Server Agent 服務無法使用 SQL Server 驗證</span><span class="sxs-lookup"><span data-stu-id="c32ee-110">SQL Server Agent Service cannot use SQL Server Authentication</span></span>](../../../2014/sql-server/install/sql-server-agent-service-cannot-use-sql-server-authentication.md)  
  
-   [<span data-ttu-id="c32ee-111">更新 SQL Server Agent 作業步驟中的語彙基元語法</span><span class="sxs-lookup"><span data-stu-id="c32ee-111">Update token syntax in SQL Server Agent job steps</span></span>](../../../2014/sql-server/install/update-token-syntax-in-sql-server-agent-job-steps.md)  
  
-   [<span data-ttu-id="c32ee-112">先升級所有目標伺服器後再升級主要伺服器</span><span class="sxs-lookup"><span data-stu-id="c32ee-112">Upgrade all target servers before upgrading the master server</span></span>](../../../2014/sql-server/install/upgrade-all-target-servers-before-upgrading-the-master-server.md)  
  
-   [<span data-ttu-id="c32ee-113">升級會將 SQL Server Agent 使用者 Proxy 帳戶變更為暫時的 UpgradedProxyAccount</span><span class="sxs-lookup"><span data-stu-id="c32ee-113">Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount</span></span>](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)  
  
## <a name="see-also"></a><span data-ttu-id="c32ee-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c32ee-114">See Also</span></span>  
 <span data-ttu-id="c32ee-115">[SQL Server 2014 Upgrade Advisor &#91;新的&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="c32ee-115">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="c32ee-116">解決升級問題</span><span class="sxs-lookup"><span data-stu-id="c32ee-116">Resolving Upgrade Issues</span></span>](../../../2014/sql-server/install/resolving-upgrade-issues.md)  
  
  
