---
title: MSSQL_ENG020598 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8cef26001c353dea94ec9b658dfb38285231bc20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697954"
---
# <a name="mssql_eng020598"></a><span data-ttu-id="7ceaf-102">MSSQL_ENG020598</span><span class="sxs-lookup"><span data-stu-id="7ceaf-102">MSSQL_ENG020598</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7ceaf-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="7ceaf-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ceaf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7ceaf-104">Product Name</span></span>|<span data-ttu-id="7ceaf-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ceaf-105">SQL Server</span></span>|  
|<span data-ttu-id="7ceaf-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7ceaf-106">Event ID</span></span>|<span data-ttu-id="7ceaf-107">20598</span><span class="sxs-lookup"><span data-stu-id="7ceaf-107">20598</span></span>|  
|<span data-ttu-id="7ceaf-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7ceaf-108">Event Source</span></span>|<span data-ttu-id="7ceaf-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7ceaf-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7ceaf-110">元件</span><span class="sxs-lookup"><span data-stu-id="7ceaf-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7ceaf-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7ceaf-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7ceaf-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7ceaf-112">Message Text</span></span>|<span data-ttu-id="7ceaf-113">套用複寫命令時，在訂閱者端找不到資料列。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-113">The row was not found at the Subscriber when applying the replicated command.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7ceaf-114">說明</span><span class="sxs-lookup"><span data-stu-id="7ceaf-114">Explanation</span></span>  
 <span data-ttu-id="7ceaf-115">如果「散發代理程式」嘗試在「訂閱者」端更新資料列，但該資料列已刪除或其主索引鍵已變更，則會在異動複寫中發生這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-115">This error is raised in transactional replication if the Distribution Agent attempts to update a row at the Subscriber, but the row has been deleted or the primary key of the row has been changed.</span></span> <span data-ttu-id="7ceaf-116">依預設，交易式發行集的訂閱者應當成唯讀處理，因為變更並不會傳播回發行者。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-116">By default, Subscribers to transactional publications should be treated as read-only, because changes are not propagated back to the Publisher.</span></span> <span data-ttu-id="7ceaf-117">針對異動複寫，只有在使用可更新訂閱或點對點複寫時，才應於「訂閱者」端進行使用者變更。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-117">For transactional replication, user changes should be made at the Subscriber only if updatable subscriptions or peer-to-peer replication is used.</span></span> <span data-ttu-id="7ceaf-118">如需這些選項的資訊，請參閱＜ [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) ＞和＜ [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-118">For information about these options, see [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) and [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7ceaf-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7ceaf-119">User Action</span></span>  
 <span data-ttu-id="7ceaf-120">**若要解決這個問題：**</span><span class="sxs-lookup"><span data-stu-id="7ceaf-120">**To resolve this problem:**</span></span>  
  
1.  <span data-ttu-id="7ceaf-121">如果在您找到錯誤來源時複寫必須繼續進行的話，請為散發代理程式指定參數 **-SkipErrors 20598** 。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-121">If replication must continue while you identify the source of the error, specify the parameter **-SkipErrors 20598** for the Distribution Agent.</span></span> <span data-ttu-id="7ceaf-122">這可以讓代理程式略過導致錯誤 20598 的變更，同時允許複寫其他變更。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-122">This allows the agent to skip changes that result in error 20598, while allowing other changes to be replicated.</span></span>  
  
2.  <span data-ttu-id="7ceaf-123">識別「訂閱者」端的哪些資料列已刪除，或擁有與「發行者」端對應的資料列不同的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-123">Identify which rows at the Subscriber have been deleted or have a different primary key than the corresponding rows at the Publisher.</span></span> <span data-ttu-id="7ceaf-124">您可以使用 [tablediff Utility](../../tools/tablediff-utility.md) 判斷發行集和訂閱資料庫中不同的資料列。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-124">You can use the [tablediff Utility](../../tools/tablediff-utility.md) to determine which rows are different in the publication and subscription databases.</span></span> <span data-ttu-id="7ceaf-125">如需如何使用這個公用程式與複寫資料庫的資訊，請參閱[比較複寫資料表的差異 &#40;複寫程式設計&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-125">For information about using this utility with replicated databases, see [Compare Replicated Tables for Differences &#40;Replication Programming&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md).</span></span>  
  
3.  <span data-ttu-id="7ceaf-126">在「訂閱者」端使用 **tablediff** 公用程式或其他方法更正資料列。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-126">Correct the rows at the Subscriber using the **tablediff** utility or another method.</span></span>  
  
4.  <span data-ttu-id="7ceaf-127">(選擇性) 移除 **-SkipErrors** 參數。</span><span class="sxs-lookup"><span data-stu-id="7ceaf-127">(Optional) Remove the **-SkipErrors** parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ceaf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ceaf-128">See Also</span></span>  
 [<span data-ttu-id="7ceaf-129">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="7ceaf-129">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
