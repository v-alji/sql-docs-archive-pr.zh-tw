---
title: 在網域控制站上升級至 SQL Server 2008 的服務帳戶需求 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0680e09548e38760f6ac317fec63152486a4e5fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595454"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a><span data-ttu-id="d170a-102">在網域控制站上升級至 SQL Server 2008 的服務帳戶需求</span><span class="sxs-lookup"><span data-stu-id="d170a-102">Service account requirements for upgrading to SQL Server 2008 on a domain controller</span></span>
  <span data-ttu-id="d170a-103">Upgrade Advisor 偵測到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在網域控制站上的網路服務或本地服務帳戶底下執行的實例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d170a-103">Upgrade Advisor detected an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running under a Network Service or Local Service account on a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller.</span></span> <span data-ttu-id="d170a-104">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 網域控制站上安裝 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務不能以本機服務帳戶或網路服務帳戶權限執行。</span><span class="sxs-lookup"><span data-stu-id="d170a-104">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] domain controller, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services cannot run under Local Service account or Network Service account privileges.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d170a-105">元件</span><span class="sxs-lookup"><span data-stu-id="d170a-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="d170a-106">更正動作</span><span class="sxs-lookup"><span data-stu-id="d170a-106">Corrective Action</span></span>  
 <span data-ttu-id="d170a-107">請確定所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶都指派給網域帳戶或本機系統帳戶。</span><span class="sxs-lookup"><span data-stu-id="d170a-107">Make sure that all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service accounts are assigned to either Domain accounts or Local System accounts.</span></span> <span data-ttu-id="d170a-108">如果無法在升級之前進行這項變更，系統將封鎖安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d170a-108">Failure to make this change before upgrading will block Setup.</span></span> <span data-ttu-id="d170a-109">但是，SQL 寫入器、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Active Directory Helper 服務等服務帳戶除外，因為這些服務都已硬式編碼至網路服務帳戶而且無法變更。</span><span class="sxs-lookup"><span data-stu-id="d170a-109">The service accounts SQL Writer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Active Directory Helper services are exceptions because they are hard-coded to the Network Service account and cannot be changed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d170a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d170a-110">See Also</span></span>  
 <span data-ttu-id="d170a-111">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d170a-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d170a-112">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="d170a-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
