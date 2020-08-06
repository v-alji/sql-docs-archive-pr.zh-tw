---
title: 訂閱類型 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 614ff910b13706485ee9466c884243ff1c9027ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699448"
---
# <a name="subscription-type"></a><span data-ttu-id="ff378-102">訂閱類型</span><span class="sxs-lookup"><span data-stu-id="ff378-102">Subscription Type</span></span>
  <span data-ttu-id="ff378-103">合併式複寫提供兩種訂閱類型：主訂閱與客訂閱 (對照舊版 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分別為全域與本機)。</span><span class="sxs-lookup"><span data-stu-id="ff378-103">Merge replication offers two subscription types: server and client (referred to in previous versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as global and local, respectively).</span></span> <span data-ttu-id="ff378-104">擁有主訂閱的訂閱者可以：</span><span class="sxs-lookup"><span data-stu-id="ff378-104">Subscribers with a server subscription can:</span></span>  
  
-   <span data-ttu-id="ff378-105">重新發行資料給其他訂閱者。</span><span class="sxs-lookup"><span data-stu-id="ff378-105">Republish data to other Subscribers.</span></span>  
  
-   <span data-ttu-id="ff378-106">作為替代同步夥伴。</span><span class="sxs-lookup"><span data-stu-id="ff378-106">Serve as alternate synchronization partners.</span></span>  
  
-   <span data-ttu-id="ff378-107">根據您設定的優先權解決衝突。</span><span class="sxs-lookup"><span data-stu-id="ff378-107">Resolve conflicts according to a priority you set.</span></span>  
  
 <span data-ttu-id="ff378-108">大多數的訂閱者不需要此功能，因此可以使用客訂閱。</span><span class="sxs-lookup"><span data-stu-id="ff378-108">Most Subscribers do not require this functionality and can use a client subscription.</span></span> <span data-ttu-id="ff378-109">客訂閱仍然允許衝突的偵測和解決，但是不會指派優先權給訂閱者：第一個提交變更至發行者的訂閱者，就會是可能引起之任何衝突的成功者。</span><span class="sxs-lookup"><span data-stu-id="ff378-109">Client subscriptions still allow conflict detection and resolution, but Subscribers are not assigned a priority: the first Subscriber to submit a change to the Publisher wins any conflicts that might arise from that change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff378-110">建立訂閱之後，就無法變更訂閱類型。</span><span class="sxs-lookup"><span data-stu-id="ff378-110">Subscription type cannot be changed after a subscription is created.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ff378-111">選項。</span><span class="sxs-lookup"><span data-stu-id="ff378-111">Options</span></span>  
 <span data-ttu-id="ff378-112">**訂閱屬性**</span><span class="sxs-lookup"><span data-stu-id="ff378-112">**Subscription properties**</span></span>  
 <span data-ttu-id="ff378-113">針對每個訂閱者，請從 **[訂閱類型]** 資料行的下拉式清單方塊中選取 **[客訂閱]** 或 **[主訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="ff378-113">For each Subscriber, select **Client** or **Server** from the drop-down list box in the **Subscription Type** column.</span></span> <span data-ttu-id="ff378-114">針對擁有主訂閱的訂閱者，請在 **[衝突解決的優先權]** 資料行中輸入介於 0 和 99.99 之間的數字 (數字愈高，訂閱者的優先權就愈高)。</span><span class="sxs-lookup"><span data-stu-id="ff378-114">For Subscribers with server subscriptions, enter a number between 0 and 99.99 in the **Priority for Conflict Resolution** column (the higher the number, the higher the priority for the Subscriber).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff378-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff378-115">See Also</span></span>  
 <span data-ttu-id="ff378-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="ff378-116">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="ff378-117">[Create a Push Subscription](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="ff378-117">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 [<span data-ttu-id="ff378-118">訂閱發行集</span><span class="sxs-lookup"><span data-stu-id="ff378-118">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
