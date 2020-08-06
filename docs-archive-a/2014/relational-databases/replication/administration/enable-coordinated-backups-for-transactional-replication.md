---
title: 為異動複寫啟用協調備份， (複寫 Transact-sql 程式設計) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77405cd968fa917c3ccc799eb7d168782443eee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709245"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a><span data-ttu-id="34d0b-102">為異動複寫啟用協調備份 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="34d0b-102">Enable Coordinated Backups for Transactional Replication (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="34d0b-103">在啟用異動複寫的資料庫時，可以指定所有的交易必須先備份，才能傳遞到散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="34d0b-103">When enabling a database for transactional replication, you can specify that all transactions must be backed up before being delivered to the distribution database.</span></span> <span data-ttu-id="34d0b-104">也可以在散發資料庫上啟用協調備份，如此在傳播到「散發者」的交易進行備份之前，發行集資料庫的交易記錄都不會遭到截斷。</span><span class="sxs-lookup"><span data-stu-id="34d0b-104">You can also enable coordinated backup on the distribution database so that the transaction log for the publication database is not truncated until transactions that have been propagated to the Distributor have been backed up.</span></span> <span data-ttu-id="34d0b-105">如需詳細資訊，請參閱 [備份與還原快照式和異動複寫的策略](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="34d0b-105">For more information, see [Strategies for Backing Up and Restoring Snapshot and Transactional Replication](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a><span data-ttu-id="34d0b-106">若要為使用異動複寫所發行的資料庫啟用協調備份</span><span class="sxs-lookup"><span data-stu-id="34d0b-106">To enable coordinated backups for a database published with transactional replication</span></span>  
  
1.  <span data-ttu-id="34d0b-107">在發行者端，使用 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 函式傳回發行集資料庫的 **IsSyncWithBackup** 屬性。</span><span class="sxs-lookup"><span data-stu-id="34d0b-107">At the Publisher, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the publication database.</span></span> <span data-ttu-id="34d0b-108">如果函數傳回 **1**，則已經為發行的資料庫啟用協調備份。</span><span class="sxs-lookup"><span data-stu-id="34d0b-108">If the function returns **1**, coordinated backups are already enabled for the published database.</span></span>  
  
2.  <span data-ttu-id="34d0b-109">如果步驟 1 中的函式傳回 **0**，則請在發行集資料庫的發行者端執行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34d0b-109">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Publisher on the publication database.</span></span> <span data-ttu-id="34d0b-110">針對 **\@optname** 指定 **sync with backup** 值，且針對 **\@value** 指定 **true** 值。</span><span class="sxs-lookup"><span data-stu-id="34d0b-110">Specify a value of **sync with backup** for **\@optname**, and **true** for **\@value**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34d0b-111">如果將 **sync with backup** 選項變更為 **false**，則在記錄讀取器執行後或在一個間隔後 (如果記錄讀取器持續執行)，發行集資料庫的截斷點就會更新。</span><span class="sxs-lookup"><span data-stu-id="34d0b-111">If you change the **sync with backup** option to **false**, the truncation point of the publication database will be updated after the Log Reader Agent runs, or after an interval if the Log Reader Agent is running continuously.</span></span> <span data-ttu-id="34d0b-112">最大間隔是由 **-MessageInterval** 代理程式參數 (預設值為 30 秒) 控制。</span><span class="sxs-lookup"><span data-stu-id="34d0b-112">The maximum interval is controlled by the **-MessageInterval** agent parameter (which has a default of 30 seconds).</span></span>  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a><span data-ttu-id="34d0b-113">若要啟用散發資料庫的協調備份</span><span class="sxs-lookup"><span data-stu-id="34d0b-113">To enable coordinated backups for a distribution database</span></span>  
  
1.  <span data-ttu-id="34d0b-114">在散發者端，使用 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 函式傳回散發資料庫的 **IsSyncWithBackup** 屬性。</span><span class="sxs-lookup"><span data-stu-id="34d0b-114">At the Distributor, use the [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) function to return the **IsSyncWithBackup** property of the distribution database.</span></span> <span data-ttu-id="34d0b-115">如果函數傳回 **1**，則已經為散發資料庫啟用協調備份。</span><span class="sxs-lookup"><span data-stu-id="34d0b-115">If the function returns **1**, coordinated backups are already enabled for the distribution database.</span></span>  
  
2.  <span data-ttu-id="34d0b-116">如果步驟 1 中的函式傳回 **0**，則請在散發資料庫的散發者端執行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34d0b-116">If the function in step 1 returns **0**, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) at the Distributor on the distribution database.</span></span> <span data-ttu-id="34d0b-117">為 [ \*\* \@ optname\*\* ] 指定 [**同步備份**] 的值，並為 [ \*\* \@ 值\*\*] 指定 [ **true** ]。</span><span class="sxs-lookup"><span data-stu-id="34d0b-117">Specify a value of **sync with backup** for **\@optname** and **true** for **\@value**.</span></span>  
  
### <a name="to-disable-coordinated-backups"></a><span data-ttu-id="34d0b-118">若要停用協調備份</span><span class="sxs-lookup"><span data-stu-id="34d0b-118">To disable coordinated backups</span></span>  
  
1.  <span data-ttu-id="34d0b-119">在發行集資料庫的發行者端或散發資料庫的散發者端，執行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="34d0b-119">At either the Publisher on the publication database or at the Distributor on the distribution database, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql).</span></span> <span data-ttu-id="34d0b-120">針對 **\@optname** 指定 **sync with backup** 值，且針對 **\@value** 指定 **false** 值。</span><span class="sxs-lookup"><span data-stu-id="34d0b-120">Specify a value of **sync with backup** for **\@optname** and **false** for **\@value**.</span></span>  
  
  
