---
title: MSSQL_ENG014157 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0682d740d82c995d64427f56aabce24b8a48ca65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594498"
---
# <a name="mssql_eng014157"></a><span data-ttu-id="c0894-102">MSSQL_ENG014157</span><span class="sxs-lookup"><span data-stu-id="c0894-102">MSSQL_ENG014157</span></span>
    
## <a name="message-details"></a><span data-ttu-id="c0894-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="c0894-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0894-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c0894-104">Product Name</span></span>|<span data-ttu-id="c0894-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c0894-105">SQL Server</span></span>|  
|<span data-ttu-id="c0894-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c0894-106">Event ID</span></span>|<span data-ttu-id="c0894-107">14157</span><span class="sxs-lookup"><span data-stu-id="c0894-107">14157</span></span>|  
|<span data-ttu-id="c0894-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c0894-108">Event Source</span></span>|<span data-ttu-id="c0894-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c0894-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c0894-110">元件</span><span class="sxs-lookup"><span data-stu-id="c0894-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="c0894-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c0894-111">Symbolic Name</span></span>||  
|<span data-ttu-id="c0894-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c0894-112">Message Text</span></span>|<span data-ttu-id="c0894-113">由訂閱者 '%s' 建立給發行集 '%s' 的訂閱已經過期且已經卸除。</span><span class="sxs-lookup"><span data-stu-id="c0894-113">The subscription created by Subscriber '%s' to publication '%s' has expired and has been dropped.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c0894-114">說明</span><span class="sxs-lookup"><span data-stu-id="c0894-114">Explanation</span></span>  
 <span data-ttu-id="c0894-115">「訂閱者」必須在發行集保留期限中指定的時間內與「發行者」同步。</span><span class="sxs-lookup"><span data-stu-id="c0894-115">A Subscriber must synchronize with the Publisher within the time specified in the publication retention period.</span></span> <span data-ttu-id="c0894-116">如果「訂閱者」未於這個期限內同步，訂閱便會過期。</span><span class="sxs-lookup"><span data-stu-id="c0894-116">If a Subscriber does not synchronize within this period, the subscription expires.</span></span> <span data-ttu-id="c0894-117">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="c0894-117">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c0894-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c0894-118">User Action</span></span>  
 <span data-ttu-id="c0894-119">訂閱必須重新建立和初始化，「訂閱者」才能再次開始接收資料變更：</span><span class="sxs-lookup"><span data-stu-id="c0894-119">The subscription must be re-created and initialized before the Subscriber can begin receiving data changes again:</span></span>  
  
-   <span data-ttu-id="c0894-120">如需建立訂閱的資訊，請參閱[訂閱發行集](subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="c0894-120">For information about creating subscriptions, see [Subscribe to Publications](subscribe-to-publications.md).</span></span>  
  
-   <span data-ttu-id="c0894-121">如需初始化訂閱的詳細資訊，請參閱[初始化訂閱](initialize-a-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="c0894-121">For information about initializing subscriptions, see [Initialize a Subscription](initialize-a-subscription.md).</span></span>  
  
 <span data-ttu-id="c0894-122">如果訂閱資料庫包含尚未與「發行者」同步的變更，您可以使用 [tablediff Utility](../../tools/tablediff-utility.md) 判斷發行集和訂閱資料庫中不同的資料列。</span><span class="sxs-lookup"><span data-stu-id="c0894-122">If the subscription database contains changes that have not been synchronized with the Publisher, you can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span>  
  
 <span data-ttu-id="c0894-123">您可以建立發行集保留期限，以避免訂閱過期。</span><span class="sxs-lookup"><span data-stu-id="c0894-123">You can increase the publication retention period to avoid having subscriptions expire.</span></span> <span data-ttu-id="c0894-124">請小心設定最大值，因為這個值可能導致儲存更多資料和中繼資料，結果影響效能。</span><span class="sxs-lookup"><span data-stu-id="c0894-124">Use caution in setting a high value, because this can result in more data and metadata being stored, which affects performance.</span></span> <span data-ttu-id="c0894-125">如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md)。</span><span class="sxs-lookup"><span data-stu-id="c0894-125">For more information, see [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0894-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0894-126">See Also</span></span>  
 [<span data-ttu-id="c0894-127">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="c0894-127">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
