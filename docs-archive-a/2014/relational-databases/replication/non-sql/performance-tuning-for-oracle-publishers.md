---
title: Oracle 發行者的效能微調 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], performance tuning
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 83d660eee839d525fa0bdabf88a313da0ed44244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584389"
---
# <a name="performance-tuning-for-oracle-publishers"></a><span data-ttu-id="28bf5-102">Oracle 發行者的效能微調</span><span class="sxs-lookup"><span data-stu-id="28bf5-102">Performance Tuning for Oracle Publishers</span></span>
  <span data-ttu-id="28bf5-103">Oracle 發行架構與 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 發行架構相似；因此，微調 Oracle 複寫效能的第一步需要按照 [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md)中的一般微調建議進行。</span><span class="sxs-lookup"><span data-stu-id="28bf5-103">The Oracle publishing architecture is similar to the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publishing architecture; therefore the first step in tuning Oracle replication for performance requires following the general tuning recommendations found in [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md).</span></span>  
  
 <span data-ttu-id="28bf5-104">此外，還提供了兩個與效能有關的「Oracle 發行者」選項：</span><span class="sxs-lookup"><span data-stu-id="28bf5-104">In addition there are two options for Oracle Publishers that are performance related:</span></span>  
  
-   <span data-ttu-id="28bf5-105">指定適當的發行選項：[Oracle] 或 [Oracle 閘道]。</span><span class="sxs-lookup"><span data-stu-id="28bf5-105">Specifying the appropriate publishing option: Oracle or Oracle Gateway.</span></span>  
  
-   <span data-ttu-id="28bf5-106">設定交易集作業，以便用適當的間隔處理「發行者」端的變更。</span><span class="sxs-lookup"><span data-stu-id="28bf5-106">Configuring the transaction set job to process changes on the Publisher at an appropriate interval.</span></span>  
  
## <a name="specifying-the-appropriate-publishing-option"></a><span data-ttu-id="28bf5-107">指定適當的發行選項</span><span class="sxs-lookup"><span data-stu-id="28bf5-107">Specifying the Appropriate Publishing Option</span></span>  
 <span data-ttu-id="28bf5-108">Oracle Gateway 選項提供比 Oracle Complete 選項更好的效能；不過此選項不可用於多個交易式發行集內發行同一資料表。</span><span class="sxs-lookup"><span data-stu-id="28bf5-108">The Oracle Gateway option provides improved performance over the Oracle Complete option; however, this option cannot be used to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="28bf5-109">資料表最多可以出現在單一交易式發行集，以及任意多個快照集發行集內。</span><span class="sxs-lookup"><span data-stu-id="28bf5-109">A table can appear in at most one transactional publication and any number of snapshot publications.</span></span> <span data-ttu-id="28bf5-110">若您需要在多個交易式發行集內發行同一資料表，請選擇 Oracle Complete 選項。</span><span class="sxs-lookup"><span data-stu-id="28bf5-110">If you need to publish the same table in multiple transactional publications, choose the Oracle Complete option.</span></span> <span data-ttu-id="28bf5-111">在「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」端識別「Oracle 發行者」時，請指定此選項。</span><span class="sxs-lookup"><span data-stu-id="28bf5-111">Specify this option when identifying the Oracle Publisher at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="28bf5-112">如需詳細資訊，請參閱 [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="28bf5-112">For more information, see [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
## <a name="configuring-the-transaction-set-job"></a><span data-ttu-id="28bf5-113">設定交易集作業</span><span class="sxs-lookup"><span data-stu-id="28bf5-113">Configuring the Transaction Set Job</span></span>  
 <span data-ttu-id="28bf5-114">已發行的 Oracle 資料表之變更會以群組 (稱為交易集) 方式進行處理。</span><span class="sxs-lookup"><span data-stu-id="28bf5-114">Changes to published Oracle tables are processed in groups called transaction sets.</span></span> <span data-ttu-id="28bf5-115">為確保交易一致性，每個交易集在散發資料庫中均視為單一交易。</span><span class="sxs-lookup"><span data-stu-id="28bf5-115">To ensure transactional consistency, each transaction set is committed as a single transaction at the distribution database.</span></span> <span data-ttu-id="28bf5-116">如果交易集變得很大，則無法視為單一交易進行有效地處理。</span><span class="sxs-lookup"><span data-stu-id="28bf5-116">If the transaction set becomes too large, it cannot be processed efficiently as a single transaction.</span></span>  
  
 <span data-ttu-id="28bf5-117">依預設，交易集只能由「記錄讀取器代理程式」建立。</span><span class="sxs-lookup"><span data-stu-id="28bf5-117">By default, transaction sets are created only by the Log Reader Agent.</span></span> <span data-ttu-id="28bf5-118">如果在頻繁變更活動期間，「記錄讀取器代理程式」未執行，或無法從「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」連接到「Oracle 發行者」，則交易集會變得巨大而無法管理。</span><span class="sxs-lookup"><span data-stu-id="28bf5-118">If, during periods of high change activity, the Log Reader Agent does not run or cannot connect from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher, transaction sets can become unmanageably large.</span></span> <span data-ttu-id="28bf5-119">若要防止出現此問題，請確定定期建立交易集，即使「記錄讀取器代理程式」未執行或無法連接到「Oracle 發行者」。</span><span class="sxs-lookup"><span data-stu-id="28bf5-119">To prevent this problem, ensure that transaction sets are created at regular intervals, even if the Log Reader Agent does not run or cannot connect to the Oracle Publisher.</span></span>  
  
 <span data-ttu-id="28bf5-120">交易集可以使用 Xactset 作業 (由複寫安裝的 Oracle 資料庫作業) 來建立，Xactset 作業使用與「記錄讀取器代理程式」相同的機制建立交易集。</span><span class="sxs-lookup"><span data-stu-id="28bf5-120">Transaction sets can be created with the Xactset job (an Oracle database job installed by replication), which uses the same mechanism that the Log Reader Agent does to create sets.</span></span> <span data-ttu-id="28bf5-121">每次執行此作業時，均會建立一個新的交易集。</span><span class="sxs-lookup"><span data-stu-id="28bf5-121">Each time the job runs, a new transaction set is created.</span></span> <span data-ttu-id="28bf5-122">下次執行「記錄讀取器代理程式」時，代理程式會處理所有已建立的任一交易集。</span><span class="sxs-lookup"><span data-stu-id="28bf5-122">The next time that the Log Reader Agent runs, the agent processes any sets that have been created.</span></span> <span data-ttu-id="28bf5-123">如果在處理完全部現有交易集後仍有擱置的變更，「記錄讀取器代理程式」會建立並處理一個或多個額外的交易集。</span><span class="sxs-lookup"><span data-stu-id="28bf5-123">If there are still pending changes after all existing transaction sets have been processed, the Log Reader Agent creates and processes one or more additional transaction sets.</span></span>  
  
 <span data-ttu-id="28bf5-124">若要設定交易集作業，請參閱[設定 Oracle 發行者的交易集作業 &#40;複寫 Transact-SQL 程式設計&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)。</span><span class="sxs-lookup"><span data-stu-id="28bf5-124">To configure the transaction set job, see [Configure the Transaction Set Job for an Oracle Publisher &#40;Replication Transact-SQL Programming&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bf5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28bf5-125">See Also</span></span>  
 <span data-ttu-id="28bf5-126">[設定 Oracle 發行者](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="28bf5-126">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="28bf5-127">Oracle 發行概觀</span><span class="sxs-lookup"><span data-stu-id="28bf5-127">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
