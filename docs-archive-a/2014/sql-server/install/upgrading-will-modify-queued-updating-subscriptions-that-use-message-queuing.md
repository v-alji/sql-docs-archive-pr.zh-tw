---
title: 升級將會修改使用訊息佇列的佇列更新訂閱 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication]
- MSMQ [SQL Server replication]
- queues [SQL Server replication]
- queued updating subscriptions [SQL Server replication]
ms.assetid: 97944de3-fbad-4db1-939a-dcd550bf5893
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d44cbad43d75634cbf8660110cc879522265c54d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710129"
---
# <a name="upgrading-will-modify-queued-updating-subscriptions-that-use-message-queuing"></a><span data-ttu-id="7e2c9-102">升級將會修改使用 Message Queuing 的佇列更新訂閱</span><span class="sxs-lookup"><span data-stu-id="7e2c9-102">Upgrading will modify queued updating subscriptions that use Message Queuing</span></span>
  <span data-ttu-id="7e2c9-103">Upgrade Advisor 偵測到您可能有一或多個使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (也稱為 MSMQ) 的佇列更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-103">Upgrade Advisor detected that you might have one or more queued updating subscriptions that use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="7e2c9-104">複寫不再支援訊息佇列，因此將會修改訂閱以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 佇列。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-104">Replication no longer supports Message Queuing; therefore, the subscriptions will be modified to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span>  
  
 <span data-ttu-id="7e2c9-105">只允許**sql**值。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-105">Only a value of **sql** is allowed.</span></span> <span data-ttu-id="7e2c9-106">在升級期間，系統會將使用訊息佇列的現有發行集修改為使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 佇列。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-106">Existing publications that use Message Queuing are modified during upgrade to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="7e2c9-107">如果您有應用程式是依賴使用 Message Queuing 的佇列更新，這些應用程式都需要重寫，以配合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 佇列。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-107">If you have applications that depend on queued updating using Message Queuing, these applications will have to be rewritten to accommodate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] queue.</span></span> <span data-ttu-id="7e2c9-108">如需有關佇列更新訂閱的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜異動複寫的可更新訂閱＞。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-108">For more information about queued updating subscriptions, see "Updatable Subscriptions for Transactional Replication" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="7e2c9-109">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在升級時，如果 Message Queuing 服務正在執行，升級會移除現有的 Message Queuing 訂閱佇列。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-109">Upgrade will remove the existing Message Queuing subscription queues if the Message Queuing service is running while [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is being upgraded.</span></span>  
  
 <span data-ttu-id="7e2c9-110">如果 Message Queuing 服務未在執行中，請在升級完成後手動移除佇列。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-110">If the Message Queuing service is not running, remove the queues manually after upgrade is complete.</span></span> <span data-ttu-id="7e2c9-111">如需有關如何移除佇列的詳細資訊，請參閱 Windows 文件集。</span><span class="sxs-lookup"><span data-stu-id="7e2c9-111">For more information about how to remove queues, see the Windows documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2c9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e2c9-112">See Also</span></span>  
 [<span data-ttu-id="7e2c9-113">複寫升級問題</span><span class="sxs-lookup"><span data-stu-id="7e2c9-113">Replication Upgrade Issues</span></span>](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
  
