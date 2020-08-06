---
title: 管理點對點拓撲 (複寫 Transact-SQL 程式設計) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, peer-to-peer replication
ms.assetid: 4d0fa941-f9ea-4a14-aed9-34df593fc6f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a73af1c1f3a7196d87f77681ee9d62a3ef248a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593968"
---
# <a name="administer-a-peer-to-peer-topology-replication-transact-sql-programming"></a><span data-ttu-id="53748-102">管理點對點拓撲 (複寫 Transact-SQL 程式設計)</span><span class="sxs-lookup"><span data-stu-id="53748-102">Administer a Peer-to-Peer Topology (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="53748-103">管理點對點拓撲與管理一般的異動複寫拓撲類似，但有一些需要特殊考量的地方。</span><span class="sxs-lookup"><span data-stu-id="53748-103">Administering a peer-to-peer topology is similar to administering a typical transactional replication topology, but there are a number of areas with special considerations.</span></span> <span data-ttu-id="53748-104">管理點對點拓撲的主要差別在於有些變更需要 *「停止」*(Quiesce) 系統。</span><span class="sxs-lookup"><span data-stu-id="53748-104">The principal difference in administering a peer-to-peer topology is that some changes require the system to be *quiesced*.</span></span> <span data-ttu-id="53748-105">停止系統包括停止所有節點上已發行資料表的活動，並確定每個節點已收到來自其他所有節點的所有變更。</span><span class="sxs-lookup"><span data-stu-id="53748-105">Quiescing a system involves stopping activity on published tables at all nodes and ensuring that each node has received all changes from all other nodes.</span></span> <span data-ttu-id="53748-106">如需詳細資訊，請參閱[停止複寫拓撲 &#40;複寫 Transact-SQL 程式設計&#41;](quiesce-a-replication-topology-replication-transact-sql-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="53748-106">For more information, see [Quiesce a Replication Topology &#40;Replication Transact-SQL Programming&#41;](quiesce-a-replication-topology-replication-transact-sql-programming.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="53748-107">在點對點拓撲中，散發者無法使用比提取訂閱者還舊的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="53748-107">In a peer-to-peer topology, the distributor cannot be using an earlier version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] than a pull subscriber.</span></span>  
  
### <a name="to-add-an-article-to-an-existing-configuration"></a><span data-ttu-id="53748-108">若要將發行項加入至現有的組態</span><span class="sxs-lookup"><span data-stu-id="53748-108">To add an article to an existing configuration</span></span>  
  
1.  <span data-ttu-id="53748-109">停止系統。</span><span class="sxs-lookup"><span data-stu-id="53748-109">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="53748-110">停止拓撲中每個節點的「散發代理程式」。</span><span class="sxs-lookup"><span data-stu-id="53748-110">Stop the Distribution Agent at each node in the topology.</span></span> <span data-ttu-id="53748-111">如需詳細資訊，請參閱[複寫代理程式可執行檔概念](../concepts/replication-agent-executables-concepts.md)或[啟動和停止複寫代理程式 &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="53748-111">For more information, see [Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md) or [Start and Stop a Replication Agent &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md).</span></span>  
  
3.  <span data-ttu-id="53748-112">執行 CREATE TABLE 陳述式，在拓撲中的每個節點加入新資料表。</span><span class="sxs-lookup"><span data-stu-id="53748-112">Execute the CREATE TABLE statement to add the new table at each node in the topology.</span></span>  
  
4.  <span data-ttu-id="53748-113">使用 [bcp 公用程式](../../../tools/bcp-utility.md)，以手動方式在所有節點大量複製新資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="53748-113">Bulk copy the data for the new table manually at all nodes by using the [bcp utility](../../../tools/bcp-utility.md).</span></span>  
  
5.  <span data-ttu-id="53748-114">執行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) ，在拓撲中的每個節點建立新發行項。</span><span class="sxs-lookup"><span data-stu-id="53748-114">Execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) to create the new article at each node in the topology.</span></span> <span data-ttu-id="53748-115">如需詳細資訊，請參閱 [定義發行項](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="53748-115">For more information, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="53748-116">在執行 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 之後，複寫會將發行項自動加入至拓撲中的訂閱。</span><span class="sxs-lookup"><span data-stu-id="53748-116">After [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) is executed, replication automatically adds the article to the subscriptions in the topology.</span></span>  
  
6.  <span data-ttu-id="53748-117">重新啟動拓撲中每個節點的「散發代理程式」。</span><span class="sxs-lookup"><span data-stu-id="53748-117">Restart the Distribution Agents at each node in the topology.</span></span>  
  
### <a name="to-make-schema-changes-to-a-publication-database"></a><span data-ttu-id="53748-118">若要對發行集資料庫進行結構描述變更</span><span class="sxs-lookup"><span data-stu-id="53748-118">To make schema changes to a publication database</span></span>  
  
1.  <span data-ttu-id="53748-119">停止系統。</span><span class="sxs-lookup"><span data-stu-id="53748-119">Quiesce the system.</span></span>  
  
2.  <span data-ttu-id="53748-120">執行資料定義語言 (DDL) 陳述式，修改已發行資料表的結構描述。</span><span class="sxs-lookup"><span data-stu-id="53748-120">Execute the data definition language (DDL) statements to modify the schema of published tables.</span></span> <span data-ttu-id="53748-121">如需受支援結構描述變更的詳細資訊，請參閱[對發行集資料庫進行結構描述變更](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="53748-121">For more information about supported schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
3.  <span data-ttu-id="53748-122">在已發行資料表上繼續活動之前，請再次停止系統。</span><span class="sxs-lookup"><span data-stu-id="53748-122">Before you resume activity on published tables, quiesce the system again.</span></span> <span data-ttu-id="53748-123">如此可確保在複寫任何新的資料變更之前，所有節點都已接收到結構描述變更。</span><span class="sxs-lookup"><span data-stu-id="53748-123">This ensures that schema changes have been received by all nodes before any new data changes are replicated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53748-124">範例</span><span class="sxs-lookup"><span data-stu-id="53748-124">Example</span></span>  
 <span data-ttu-id="53748-125">下列範例示範如何在擁有兩個節點的現有點對點複寫拓撲中，加入新的資料表發行項。</span><span class="sxs-lookup"><span data-stu-id="53748-125">The following example demonstrates how to add a new table article to an existing peer-to-peer replication topology that has two nodes.</span></span>  
  
 [!code-sql[HowTo#sp_addp2particle_createtables](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createtables)]  
  
 [!code-sql[HowTo#sp_addp2particle_cmdline](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_cmdline)]  
  
 [!code-sql[HowTo#sp_addp2particle_createarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/addp2particle.sql#sp_addp2particle_createarticle)]  
  
## <a name="see-also"></a><span data-ttu-id="53748-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53748-126">See Also</span></span>  
 <span data-ttu-id="53748-127">[複寫管理常見問題集](frequently-asked-questions-for-replication-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="53748-127">[Replication Administration FAQ](frequently-asked-questions-for-replication-administrators.md) </span></span>  
 <span data-ttu-id="53748-128">[SQL Server 資料庫的備份與還原](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="53748-128">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="53748-129">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="53748-129">Peer-to-Peer Transactional Replication</span></span>](../transactional/peer-to-peer-transactional-replication.md)  
  
  
