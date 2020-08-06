---
title: 可更新的訂閱 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.updatablesubscriptions.f1
ms.assetid: 8e9a13a0-6b24-47c6-9d83-3cbaf08f673d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 447114152365e098420f46d4b7e880e8f2907864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697885"
---
# <a name="updatable-subscriptions"></a><span data-ttu-id="97007-102">可更新的訂閱</span><span class="sxs-lookup"><span data-stu-id="97007-102">Updatable Subscriptions</span></span>
  <span data-ttu-id="97007-103">若為異動複寫，複寫的資料應當成唯讀處理；不過，您可以在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訂閱者端使用可更新訂閱，來修改複寫的資料。</span><span class="sxs-lookup"><span data-stu-id="97007-103">With transactional replication, replicated data should be treated as read-only; however, you can modify replicated data at a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber by using updatable subscriptions.</span></span> <span data-ttu-id="97007-104">如果您需要修改訂閱者端的資料，請視您的需求，使用下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="97007-104">If you need to modify data at the Subscriber, choose one of the following options depending on your requirements.</span></span>  
  
|<span data-ttu-id="97007-105">可更新的訂閱類型</span><span class="sxs-lookup"><span data-stu-id="97007-105">Updatable Subscription Type</span></span>|<span data-ttu-id="97007-106">需求</span><span class="sxs-lookup"><span data-stu-id="97007-106">Requirements</span></span>|  
|---------------------------------|------------------|  
|<span data-ttu-id="97007-107">立即更新</span><span class="sxs-lookup"><span data-stu-id="97007-107">Immediate Updating</span></span>|<span data-ttu-id="97007-108">發行者及訂閱者必須已建立連接，才能更新訂閱者端的資料。</span><span class="sxs-lookup"><span data-stu-id="97007-108">Publisher and Subscriber must be connected to update data at the Subscriber.</span></span>|  
|<span data-ttu-id="97007-109">佇列更新</span><span class="sxs-lookup"><span data-stu-id="97007-109">Queued Updating</span></span>|<span data-ttu-id="97007-110">發行者和訂閱者不需要連接，即可更新訂閱者端的資料。</span><span class="sxs-lookup"><span data-stu-id="97007-110">Publisher and Subscriber do not have to be connected to update data at the Subscriber.</span></span> <span data-ttu-id="97007-111">可以在離線時進行更新，並於稍後在發行者和訂閱者之間進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="97007-111">Updates can be made while offline, and later synchronized between the Publisher and Subscriber.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="97007-112">選項。</span><span class="sxs-lookup"><span data-stu-id="97007-112">Options</span></span>  
 <span data-ttu-id="97007-113">**複寫訂閱者變更**</span><span class="sxs-lookup"><span data-stu-id="97007-113">**Replicate Subscriber changes**</span></span>  
 <span data-ttu-id="97007-114">針對每個應該能夠執行更新的訂閱者，選取 **[複寫]** 資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="97007-114">Select the check box in the **Replicate** column for each Subscriber that should be able to make updates.</span></span> <span data-ttu-id="97007-115">針對能夠執行更新的訂閱者，請從 **[在發行者端認可]** 資料行的下拉式清單方塊中，選取適當的選項：</span><span class="sxs-lookup"><span data-stu-id="97007-115">For those Subscribers that can make updates, select the appropriate option from the drop-down list box in the **Commit at Publisher** column:</span></span>  
  
-   <span data-ttu-id="97007-116">針對立即更新訂閱，請選取 **[同時認可變更]** 。</span><span class="sxs-lookup"><span data-stu-id="97007-116">Select **Simultaneously commit changes** for an immediate updating subscription.</span></span>  
  
-   <span data-ttu-id="97007-117">針對佇列更新訂閱，請選取 **[佇列變更且儘可能認可]** 。</span><span class="sxs-lookup"><span data-stu-id="97007-117">Select **Queue changes and commit when possible** for a queued updating subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97007-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97007-118">See Also</span></span>  
 <span data-ttu-id="97007-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="97007-119">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="97007-120">[Create a Push Subscription](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="97007-120">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="97007-121">[Subscribe to Publications](subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="97007-121">[Subscribe to Publications](subscribe-to-publications.md) </span></span>  
 [<span data-ttu-id="97007-122">Updatable Subscriptions for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="97007-122">Updatable Subscriptions for Transactional Replication</span></span>](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
