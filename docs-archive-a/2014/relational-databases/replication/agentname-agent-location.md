---
title: '&lt;代理程式名稱&gt; 代理程式位置 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentlocation.f1
ms.assetid: dc664d80-fbe3-4586-aba8-a71fa62d14f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7fc39541915b43abd024e1b02022f8a9e61580b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593960"
---
# <a name="ltagentnamegt-agent-location"></a><span data-ttu-id="b8605-102">&lt;代理程式名稱&gt; 代理程式位置</span><span class="sxs-lookup"><span data-stu-id="b8605-102">&lt;AgentName&gt; Agent Location</span></span>
  <span data-ttu-id="b8605-103">合併代理程式 (用於合併訂閱) 和散發代理程式 (用於交易式與快照式訂閱) 會在散發者端或在訂閱者端執行。</span><span class="sxs-lookup"><span data-stu-id="b8605-103">The Merge Agent (for merge subscriptions) and the Distribution Agent (for transactional and snapshot subscriptions) run at the Distributor or at the Subscriber.</span></span> <span data-ttu-id="b8605-104">如果代理程式是在散發者端執行，訂閱就稱為發送訂閱；如果代理程式是在訂閱者端執行，訂閱就稱為提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="b8605-104">If the agent runs at the Distributor, the subscription is referred to as a push subscription; if the agent runs at the Subscriber, it is referred to as a pull subscription.</span></span> <span data-ttu-id="b8605-105">如需發送和提取訂閱的詳細資訊，請參閱[訂閱發行集](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="b8605-105">For more information about push and pull subscriptions, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="b8605-106">透過精靈在此過程中建立的所有訂閱，都屬於選取的類型。</span><span class="sxs-lookup"><span data-stu-id="b8605-106">All subscriptions created in this pass through the wizard will be of the selected type.</span></span> <span data-ttu-id="b8605-107">若要建立兩種類型的訂閱，您就必須執行精靈兩次。</span><span class="sxs-lookup"><span data-stu-id="b8605-107">To create subscriptions of both types, you must run the wizard twice.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8605-108">建立訂閱之後，就無法變更訂閱類型。</span><span class="sxs-lookup"><span data-stu-id="b8605-108">Subscription type cannot be changed after a subscription is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8605-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8605-109">See Also</span></span>  
 <span data-ttu-id="b8605-110">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="b8605-110">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="b8605-111">[Create a Push Subscription](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="b8605-111">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="b8605-112">複寫代理程式概觀</span><span class="sxs-lookup"><span data-stu-id="b8605-112">Replication Agents Overview</span></span>](agents/replication-agents-overview.md)  
  
  
