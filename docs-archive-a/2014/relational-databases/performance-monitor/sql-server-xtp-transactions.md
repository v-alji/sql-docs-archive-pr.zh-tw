---
title: XTP 交易 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 75fa8bc9a673d9e0e018b8578a35af2e46b5044c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698032"
---
# <a name="xtp-transactions"></a><span data-ttu-id="eab3b-102">XTP 交易</span><span class="sxs-lookup"><span data-stu-id="eab3b-102">XTP Transactions</span></span>
  <span data-ttu-id="eab3b-103">XTP 交易效能物件包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中與 XTP 引擎交易相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="eab3b-103">The XTP Transactions performance object contains counters related to XTP engine transactions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="eab3b-104">下表描述**XTP 交易**計數器。</span><span class="sxs-lookup"><span data-stu-id="eab3b-104">This table describes the **XTP Transactions** counters.</span></span>  
  
|<span data-ttu-id="eab3b-105">計數器</span><span class="sxs-lookup"><span data-stu-id="eab3b-105">Counter</span></span>|<span data-ttu-id="eab3b-106">描述</span><span class="sxs-lookup"><span data-stu-id="eab3b-106">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eab3b-107">**串聯中止/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-107">**Cascading aborts/sec**</span></span>|<span data-ttu-id="eab3b-108">(平均) 每秒因為認可相依性回復而回復的交易數。</span><span class="sxs-lookup"><span data-stu-id="eab3b-108">The number of transactions that rolled back to due a commit dependency rollback (on average), per second.</span></span>|  
|<span data-ttu-id="eab3b-109">**採取的認可相依性/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-109">**Commit dependencies taken/sec**</span></span>|<span data-ttu-id="eab3b-110">(平均) 每秒交易採取的認可相依性數目。</span><span class="sxs-lookup"><span data-stu-id="eab3b-110">The number of commit dependencies taken by transactions (on average), per second.</span></span>|  
|<span data-ttu-id="eab3b-111">**準備的唯讀交易/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-111">**Read-only transactions prepared/sec**</span></span>|<span data-ttu-id="eab3b-112">每秒為了認可處理而準備的唯讀交易數。</span><span class="sxs-lookup"><span data-stu-id="eab3b-112">The number of read-only transactions that were prepared for commit processing, per second.</span></span>|  
|<span data-ttu-id="eab3b-113">**儲存點重新整理/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-113">**Save point refreshes/sec**</span></span>|<span data-ttu-id="eab3b-114">(平均) 每秒儲存點「重新整理」的次數。</span><span class="sxs-lookup"><span data-stu-id="eab3b-114">The number of times a savepoint was "refreshed", (on average), per second.</span></span> <span data-ttu-id="eab3b-115">儲存點重新整理是指在交易存留期間，將現有儲存點重設為目前點的時候。</span><span class="sxs-lookup"><span data-stu-id="eab3b-115">A savepoint refresh is when an existing savepoint is reset to the current point in the transaction's lifetime.</span></span>|  
|<span data-ttu-id="eab3b-116">**儲存點回復/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-116">**Save point rollbacks/sec**</span></span>|<span data-ttu-id="eab3b-117">(平均) 每秒交易回復到儲存點的次數。</span><span class="sxs-lookup"><span data-stu-id="eab3b-117">The number of times a transaction rolled back to a save point (on average), per second.</span></span>|  
|<span data-ttu-id="eab3b-118">**建立的儲存點/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-118">**Save points created /sec**</span></span>|<span data-ttu-id="eab3b-119">(平均) 每秒建立的儲存點數。</span><span class="sxs-lookup"><span data-stu-id="eab3b-119">The number of save points created (on average), per second.</span></span>|  
|<span data-ttu-id="eab3b-120">**交易驗證失敗/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-120">**Transaction validation failure/sec**</span></span>|<span data-ttu-id="eab3b-121">(平均) 每秒驗證處理失敗的交易數。</span><span class="sxs-lookup"><span data-stu-id="eab3b-121">The number of transactions that failed validation processing (on average), per second.</span></span>|  
|<span data-ttu-id="eab3b-122">**使用者中止的交易/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-122">**Transactions aborted by user/sec**</span></span>|<span data-ttu-id="eab3b-123">(平均) 每秒使用者中止的交易數。</span><span class="sxs-lookup"><span data-stu-id="eab3b-123">The number of transactions that were aborted by the user (on average), per second.</span></span>|  
|<span data-ttu-id="eab3b-124">**中止的交易/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-124">**Transactions aborted/sec**</span></span>|<span data-ttu-id="eab3b-125">(平均) 每秒中止的交易數，包括由使用者和系統中止的數目。</span><span class="sxs-lookup"><span data-stu-id="eab3b-125">The number of transactions that aborted (both by the user and the system, on average), per second.</span></span>|  
|<span data-ttu-id="eab3b-126">**建立的交易/秒**</span><span class="sxs-lookup"><span data-stu-id="eab3b-126">**Transactions created/sec**</span></span>|<span data-ttu-id="eab3b-127">(平均) 每秒在系統中建立的交易數目。</span><span class="sxs-lookup"><span data-stu-id="eab3b-127">The number of transactions created in the system (on average), per second.</span></span><br /><br /> <span data-ttu-id="eab3b-128">XTP 交易的計數方式跟磁碟交易不同 (如 Databases:Transactions/sec 中所反映)。</span><span class="sxs-lookup"><span data-stu-id="eab3b-128">XTP transactions are counted differently than disk-based transactions (as reflected in Databases:Transactions/sec).</span></span> <span data-ttu-id="eab3b-129">例如，Transactions created/sec 是計算唯讀交易，Databases:Transactions/sec 則不是。</span><span class="sxs-lookup"><span data-stu-id="eab3b-129">For example, Transactions created/sec counts read/only transactions, while Databases:Transactions/sec does not.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eab3b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eab3b-130">See Also</span></span>  
 [<span data-ttu-id="eab3b-131">XTP &#40;記憶體內部 OLTP&#41; 效能計數器</span><span class="sxs-lookup"><span data-stu-id="eab3b-131">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
