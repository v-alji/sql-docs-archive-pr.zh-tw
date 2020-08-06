---
title: 升級會將 SQL Server Agent 的使用者 Proxy 帳戶變更為暫時的 UpgradedProxyAccount |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2bca80580a50f2acebed1b6fbea2dec1f6458dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584970"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a><span data-ttu-id="156ea-102">升級會將 SQL Server Agent 使用者 Proxy 帳戶變更為暫時的 UpgradedProxyAccount</span><span class="sxs-lookup"><span data-stu-id="156ea-102">Upgrading will change the SQL Server Agent User Proxy Account to the temporary UpgradedProxyAccount</span></span>
  <span data-ttu-id="156ea-103">升級之後，已啟用記錄傳送的資料庫維護計劃將無法啟用。</span><span class="sxs-lookup"><span data-stu-id="156ea-103">Database maintenance plans that have log shipping enabled will not be enabled after upgrade.</span></span>  
  
## <a name="component"></a><span data-ttu-id="156ea-104">元件</span><span class="sxs-lookup"><span data-stu-id="156ea-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="156ea-105">Agent</span><span class="sxs-lookup"><span data-stu-id="156ea-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="156ea-106">描述</span><span class="sxs-lookup"><span data-stu-id="156ea-106">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="156ea-107">提供一組與資料庫維護計劃不直接相容的新記錄傳送功能。</span><span class="sxs-lookup"><span data-stu-id="156ea-107">provides a new set of log shipping functions that are not directly compatible with database maintenance plans.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="156ea-108">更正動作</span><span class="sxs-lookup"><span data-stu-id="156ea-108">Corrective Action</span></span>  
 <span data-ttu-id="156ea-109">擁有包含記錄傳送功能之資料庫維護計劃的 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 使用者應該使用新的功能來設定記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="156ea-109">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] users that have database maintenance plans that contain log shipping functions should configure log shipping by using the new functions.</span></span> <span data-ttu-id="156ea-110">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜記錄傳送＞。</span><span class="sxs-lookup"><span data-stu-id="156ea-110">For more information, search on "log shipping" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156ea-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="156ea-111">See Also</span></span>  
 <span data-ttu-id="156ea-112">[SQL Server Agent 記錄傳送作業類別目錄會導致升級失敗](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span><span class="sxs-lookup"><span data-stu-id="156ea-112">[SQL Server Agent log shipping job category causes upgrade to fail](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md) </span></span>  
 [<span data-ttu-id="156ea-113">升級之後，不會執行記錄傳送</span><span class="sxs-lookup"><span data-stu-id="156ea-113">Log shipping will not run after upgrading</span></span>](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
