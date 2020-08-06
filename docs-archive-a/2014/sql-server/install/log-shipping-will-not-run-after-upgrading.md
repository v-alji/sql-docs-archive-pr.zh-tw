---
title: 升級之後，將不會執行記錄傳送 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b2af60743cb2cbf9bf455397fe052c4e81f5a06d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606605"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a><span data-ttu-id="b4b7c-102">升級之後，不會執行記錄傳送</span><span class="sxs-lookup"><span data-stu-id="b4b7c-102">Log shipping will not run after upgrading</span></span>
  <span data-ttu-id="b4b7c-103">Upgrade Advisor 偵測到您正在使用記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="b4b7c-103">Upgrade Advisor has detected that you are using log shipping.</span></span> [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] <span data-ttu-id="b4b7c-104">記錄傳送與 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的記錄傳送不相容，也不能直接升級。</span><span class="sxs-lookup"><span data-stu-id="b4b7c-104">log shipping is incompatible with log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] and cannot be upgraded directly.</span></span> <span data-ttu-id="b4b7c-105">請在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之後，使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或預存程序重新設定記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="b4b7c-105">After upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], reconfigure log shipping using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b7c-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4b7c-106">See Also</span></span>  
 <span data-ttu-id="b4b7c-107">[SQL Server Agent 記錄傳送作業類別目錄會導致升級失敗](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span><span class="sxs-lookup"><span data-stu-id="b4b7c-107">[SQL Server Agent log shipping job category causes upgrade to fail](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span></span>  
 <span data-ttu-id="b4b7c-108">[升級會將 SQL Server Agent 的使用者 Proxy 帳戶變更為暫時的 UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span><span class="sxs-lookup"><span data-stu-id="b4b7c-108">[Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md) </span></span>  
 <span data-ttu-id="b4b7c-109">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="b4b7c-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="b4b7c-110">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="b4b7c-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
