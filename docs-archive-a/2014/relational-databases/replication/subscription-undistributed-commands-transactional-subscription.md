---
title: 訂用帳戶、未散發的命令 (交易式訂用帳戶、SQL Server 2005 和更新版本) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bbd82b4f4855c99076404d8b621edca11a7e1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699445"
---
# <a name="subscription-undistributed-commands-transactional-subscription-sql-server-2005-and-later"></a><span data-ttu-id="0a73f-102">訂閱，未散發的命令 (交易式訂閱，SQL Server 2005 和更新的版本)</span><span class="sxs-lookup"><span data-stu-id="0a73f-102">Subscription, Undistributed Commands (Transactional Subscription, SQL Server 2005 and Later)</span></span>
  <span data-ttu-id="0a73f-103">**[未散發的命令]** 索引標籤會顯示散發資料庫中尚未傳遞給選取之訂閱者的命令數目，以及傳遞這些命令的估計時間等相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0a73f-103">The **Undistributed Commands** tab displays information about the number of commands in the distribution database that have not been delivered to the selected Subscriber, and the estimated time to deliver those commands.</span></span> <span data-ttu-id="0a73f-104">如需在散發資料庫中檢視命令的資訊，請參閱 [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0a73f-104">For information about viewing the commands in the distribution database, see [sp_replshowcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0a73f-105">選項</span><span class="sxs-lookup"><span data-stu-id="0a73f-105">Options</span></span>  
 <span data-ttu-id="0a73f-106">**在散發資料庫中，等候要套用到此訂閱者的命令數目**</span><span class="sxs-lookup"><span data-stu-id="0a73f-106">**Number of commands in the distribution database waiting to be applied to this Subscriber**</span></span>  
 <span data-ttu-id="0a73f-107">散發資料庫中尚未傳遞給選取之訂閱者的命令數目。</span><span class="sxs-lookup"><span data-stu-id="0a73f-107">The number of commands in the distribution database that have not been delivered to the selected Subscriber.</span></span> <span data-ttu-id="0a73f-108">由一個 Transact-SQL 資料操作語言 (DML) 陳述式或一個資料定義語言 (DDL) 陳述式組成的命令。</span><span class="sxs-lookup"><span data-stu-id="0a73f-108">A command consists of one Transact-SQL data manipulation language (DML) statement or one data definition language (DDL) statement.</span></span>  
  
 <span data-ttu-id="0a73f-109">**依據過去的效能，估計套用這些命令的時間**</span><span class="sxs-lookup"><span data-stu-id="0a73f-109">**Estimated time to apply these commands, based on past performance**</span></span>  
 <span data-ttu-id="0a73f-110">估計將命令傳遞給訂閱者所需的時間量。</span><span class="sxs-lookup"><span data-stu-id="0a73f-110">The estimated amount of time to deliver commands to the Subscriber.</span></span> <span data-ttu-id="0a73f-111">如果此值大於產生快照集並將其套用至訂閱者所需的時間量，則請考慮重新初始化訂閱者。</span><span class="sxs-lookup"><span data-stu-id="0a73f-111">If this value is greater than the amount of time required to generate and apply a snapshot to the Subscriber, consider reinitializing the Subscriber.</span></span> <span data-ttu-id="0a73f-112">如需詳細資訊，請參閱 [重新初始化訂閱](reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="0a73f-112">For more information, see [Reinitialize Subscriptions](reinitialize-subscriptions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a73f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a73f-113">See Also</span></span>  
 <span data-ttu-id="0a73f-114">[啟動複寫監視器](monitor/start-the-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0a73f-114">[Start the Replication Monitor](monitor/start-the-replication-monitor.md) </span></span>  
 <span data-ttu-id="0a73f-115">[使用複寫監視器監視效能](monitor/monitor-performance-with-replication-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="0a73f-115">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) </span></span>  
 [<span data-ttu-id="0a73f-116">監視複寫</span><span class="sxs-lookup"><span data-stu-id="0a73f-116">Monitoring Replication</span></span>](monitoring-replication.md)  
  
  
