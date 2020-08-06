---
title: 控制交易持久性 | Microsoft 文件
ms.custom: ''
ms.date: 05/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- delayed durability
- Lazy Commit
ms.assetid: 3ac93b28-cac7-483e-a8ab-ac44e1cc1c76
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f37bcaf8719f4a2f3b1e7fbca1cf332717bd936e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594547"
---
# <a name="control-transaction-durability"></a><span data-ttu-id="328cb-102">控制交易持久性</span><span class="sxs-lookup"><span data-stu-id="328cb-102">Control Transaction Durability</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="328cb-103">交易認可可能是完全持久 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設值) 或延遲的持久 (也稱為延遲認可)。</span><span class="sxs-lookup"><span data-stu-id="328cb-103">transaction commits can be either fully durable, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default, or delayed durable (also known as lazy commit).</span></span>  
  
 <span data-ttu-id="328cb-104">完全持久交易認可是同步認可，而且只有在交易的記錄檔記錄寫入磁碟之後，才會將認可回報為成功並將控制權傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="328cb-104">Fully durable transaction commits are synchronous and report a commit as successful and return control to the client only after the log records for the transaction are written to disk.</span></span> <span data-ttu-id="328cb-105">延遲的持久交易認可是非同步認可，而且在交易的記錄檔記錄寫入磁碟之前，就會將認可回報為成功。</span><span class="sxs-lookup"><span data-stu-id="328cb-105">Delayed durable transaction commits are asynchronous and report a commit as successful before the log records for the transaction are written to disk.</span></span> <span data-ttu-id="328cb-106">將交易記錄項目寫入磁碟是讓交易能夠持久的必要條件。</span><span class="sxs-lookup"><span data-stu-id="328cb-106">Writing the transaction log entries to disk is required for a transaction to be durable.</span></span> <span data-ttu-id="328cb-107">延遲的持久交易會在交易記錄項目排清至磁碟時變成持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-107">Delayed durable transactions become durable when the transaction log entries are flushed to disk.</span></span>  
  
 <span data-ttu-id="328cb-108">本主題將詳細說明延遲的持久交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-108">This topic details delayed durable transactions.</span></span>  
  
## <a name="full-vs-delayed-transaction-durability"></a><span data-ttu-id="328cb-109">完全與延遲的交易持久性</span><span class="sxs-lookup"><span data-stu-id="328cb-109">Full vs. Delayed Transaction Durability</span></span>  
 <span data-ttu-id="328cb-110">完全與延遲的交易持久性各有其優缺點。</span><span class="sxs-lookup"><span data-stu-id="328cb-110">Both full and delayed transaction durability have their advantages and disadvantages.</span></span> <span data-ttu-id="328cb-111">應用程式可以混合使用完全與延遲的持久交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-111">An application can have a mix of fully and delayed durable transactions.</span></span> <span data-ttu-id="328cb-112">您應該仔細考量業務需求，以及每種交易如何配合這些需求。</span><span class="sxs-lookup"><span data-stu-id="328cb-112">You should carefully consider your business needs and how each fits into those needs.</span></span>  
  
### <a name="full-transaction-durability"></a><span data-ttu-id="328cb-113">完全交易持久性</span><span class="sxs-lookup"><span data-stu-id="328cb-113">Full transaction durability</span></span>  
 <span data-ttu-id="328cb-114">完全持久交易會先將交易記錄寫入磁碟，然後再將控制權傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="328cb-114">Fully durable transactions write the transaction log to disk before returning control to the client.</span></span> <span data-ttu-id="328cb-115">只要符合下列情況，您就應該使用完全持久交易：</span><span class="sxs-lookup"><span data-stu-id="328cb-115">You should use fully durable transactions whenever:</span></span>  
  
-   <span data-ttu-id="328cb-116">您的系統無法容忍任何資料遺失。</span><span class="sxs-lookup"><span data-stu-id="328cb-116">Your system cannot tolerate any data loss.</span></span>   
    <span data-ttu-id="328cb-117">如需何時會遺失部分資料的相關資訊，請參閱 [我何時會遺失資料？](#when-can-i-lose-data) 一節。</span><span class="sxs-lookup"><span data-stu-id="328cb-117">See the section [When can I lose data?](#when-can-i-lose-data) for information on when you can lose some of your data.</span></span>  
  
-   <span data-ttu-id="328cb-118">造成瓶頸的原因不是交易記錄寫入延遲。</span><span class="sxs-lookup"><span data-stu-id="328cb-118">The bottleneck is not due to transaction log write latency.</span></span>  
  
 <span data-ttu-id="328cb-119">延遲的交易持久性可減少記錄 I/O 造成的延遲，方法是將交易記錄檔記錄保留在記憶體中，並且批次寫入交易記錄，因此需要的 I/O 作業較少。</span><span class="sxs-lookup"><span data-stu-id="328cb-119">Delayed transaction durability reduces the latency due to log I/O by keeping the transaction log records in memory and writing to the transaction log in batches, thus requiring fewer I/O operations.</span></span> <span data-ttu-id="328cb-120">延遲的交易持久性可能會減少記錄 I/O 競爭，因而減少系統的等候時間。</span><span class="sxs-lookup"><span data-stu-id="328cb-120">Delayed transaction durability potentially reduces log I/O contention, thus reducing waits in the system.</span></span>  
  
 <span data-ttu-id="328cb-121">**完全交易持久性保證**</span><span class="sxs-lookup"><span data-stu-id="328cb-121">**Full Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="328cb-122">一旦交易認可成功之後，系統中的其他交易就可以看到該筆交易所進行的變更。</span><span class="sxs-lookup"><span data-stu-id="328cb-122">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span> <span data-ttu-id="328cb-123">如需詳細資訊，請參閱[交易隔離等級](../../database-engine/transaction-isolation-levels.md)主題。</span><span class="sxs-lookup"><span data-stu-id="328cb-123">See the topic [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) for more information.</span></span>  
  
-   <span data-ttu-id="328cb-124">持久性是在認可時獲得保證。</span><span class="sxs-lookup"><span data-stu-id="328cb-124">Durability is guaranteed on commit.</span></span> <span data-ttu-id="328cb-125">在交易認可成功並將控制權傳回給用戶端之前，對應的記錄檔記錄都會保存到磁碟。</span><span class="sxs-lookup"><span data-stu-id="328cb-125">Corresponding log records are persisted to disk before the transaction commit succeeds and returns control to the client.</span></span>  
  
### <a name="delayed-transaction-durability"></a><span data-ttu-id="328cb-126">延遲的交易持久性</span><span class="sxs-lookup"><span data-stu-id="328cb-126">Delayed transaction durability</span></span>  
 <span data-ttu-id="328cb-127">延遲的交易持久性是使用磁碟的非同步記錄寫入來達成。</span><span class="sxs-lookup"><span data-stu-id="328cb-127">Delayed transaction durability is accomplished using asynchronous log writes to disk.</span></span> <span data-ttu-id="328cb-128">交易記錄檔記錄會保留在緩衝區中，然後在緩衝區填滿或發生緩衝區排清事件時寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="328cb-128">Transaction log records are kept in a buffer and written to disk when the buffer fills or a buffer flushing event takes place.</span></span> <span data-ttu-id="328cb-129">延遲的交易持久性會同時減少系統中的延遲和競爭，因為：</span><span class="sxs-lookup"><span data-stu-id="328cb-129">Delayed transaction durability reduces both latency and contention within the system because:</span></span>  
  
-   <span data-ttu-id="328cb-130">交易認可處理不會等候記錄 IO 完成並將控制權傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="328cb-130">The transaction commit processing does not wait for log IO to finish and return control to the client.</span></span>  
  
-   <span data-ttu-id="328cb-131">並行交易不太可能會爭用記錄 IO。不過，記錄緩衝區可能會以較大的區塊排清至磁碟，以便減少競爭並提高輸送量。</span><span class="sxs-lookup"><span data-stu-id="328cb-131">Concurrent transactions are less likely to contend for log IO; instead, the log buffer can be flushed to disk in larger chunks, reducing contention, and increasing throughput.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="328cb-132">如果並行程度很高，仍然可能會發生記錄 I/O 競爭，尤其是記錄緩衝區的填滿速度比排清速度快時。</span><span class="sxs-lookup"><span data-stu-id="328cb-132">You may still have log I/O contention if there is a high degree of concurrency, particularly if you fill up the log buffer faster than you flush it.</span></span>  
  
 <span data-ttu-id="328cb-133">**何時使用延遲的交易持久性**</span><span class="sxs-lookup"><span data-stu-id="328cb-133">**When to use delayed transaction durability**</span></span>  
  
 <span data-ttu-id="328cb-134">可因使用延遲的交易持久性而獲益的情形如下：</span><span class="sxs-lookup"><span data-stu-id="328cb-134">Some of the cases in which you could benefit from using delayed transaction durability are:</span></span>  
  
 <span data-ttu-id="328cb-135">**您可以容忍部分資料遺失。** </span><span class="sxs-lookup"><span data-stu-id="328cb-135">**You can tolerate some data loss.**</span></span>  
 <span data-ttu-id="328cb-136">如果您可以容忍部分資料遺失 (只要擁有大部分資料即可，個別記錄並不重要)，延遲的持久性就值得考慮使用。</span><span class="sxs-lookup"><span data-stu-id="328cb-136">If you can tolerate some data loss, for example, where individual records are not critical as long as you have most of the data, then delayed durability may be worth considering.</span></span> <span data-ttu-id="328cb-137">如果您無法容忍任何資料遺失，請勿使用延遲的交易持久性。</span><span class="sxs-lookup"><span data-stu-id="328cb-137">If you cannot tolerate any data loss, do not use delayed transaction durability.</span></span>  
  
 <span data-ttu-id="328cb-138">**您在交易記錄寫入時遇到瓶頸。** </span><span class="sxs-lookup"><span data-stu-id="328cb-138">**You are experiencing a bottleneck on transaction log writes.**</span></span>  
 <span data-ttu-id="328cb-139">如果您的效能問題是由於交易記錄寫入的延遲所造成，則使用延遲的交易持久性可能會讓您的應用程式從中獲益。</span><span class="sxs-lookup"><span data-stu-id="328cb-139">If your performance issues are due to latency in transaction log writes, your application will likely benefit from using delayed transaction durability.</span></span>  
  
 <span data-ttu-id="328cb-140">**您的工作負載具有很高的競爭率。** </span><span class="sxs-lookup"><span data-stu-id="328cb-140">**Your workloads have a high contention rate.**</span></span>  
 <span data-ttu-id="328cb-141">如果您的系統具有高競爭層級的工作負載，就表示花很多時間在等候釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="328cb-141">If your system has workloads with a high contention level much time is lost waiting for locks to be released.</span></span> <span data-ttu-id="328cb-142">延遲的交易持久性會減少認可時間並加快釋放鎖定的速度，因而提高輸送量。</span><span class="sxs-lookup"><span data-stu-id="328cb-142">Delayed transaction durability reduces commit time and thus releases locks faster which results in higher throughput.</span></span>  
  
 <span data-ttu-id="328cb-143">**延遲的交易持久性保證**</span><span class="sxs-lookup"><span data-stu-id="328cb-143">**Delayed Transaction Durability Guarantees**</span></span>  
  
-   <span data-ttu-id="328cb-144">一旦交易認可成功之後，系統中的其他交易就可以看到該筆交易所進行的變更。</span><span class="sxs-lookup"><span data-stu-id="328cb-144">Once transaction commit succeeds, the changes made by the transaction are visible to the other transactions in the system.</span></span>  
  
-   <span data-ttu-id="328cb-145">只有在記憶體中的交易記錄排清至磁碟之後，才會保證交易持久性。</span><span class="sxs-lookup"><span data-stu-id="328cb-145">Transaction durability is guaranteed only following a flush of the in-memory transaction log to disk.</span></span> <span data-ttu-id="328cb-146">記憶體中的交易記錄會在下列情況中排清至磁碟：</span><span class="sxs-lookup"><span data-stu-id="328cb-146">The in-memory transaction log is flushed to disk when:</span></span>  
  
    -   <span data-ttu-id="328cb-147">相同資料庫中的完全持久交易對資料庫進行變更並且成功認可。</span><span class="sxs-lookup"><span data-stu-id="328cb-147">A fully durable transaction in the same database makes a change in the database and successfully commits.</span></span>  
  
    -   <span data-ttu-id="328cb-148">使用者成功執行系統預存程序 `sp_flush_log` 。</span><span class="sxs-lookup"><span data-stu-id="328cb-148">The user executes the system stored procedure `sp_flush_log` successfully.</span></span>  
  
    -   <span data-ttu-id="328cb-149">記憶體中的交易記錄緩衝區填滿並自動排清至磁碟。</span><span class="sxs-lookup"><span data-stu-id="328cb-149">The in-memory transaction log buffer fills up and automatically flushes to disk.</span></span>  
  
     <span data-ttu-id="328cb-150">如果完全持久交易或 sp_flush_log 成功認可，就表示所有先前認可的延遲持久交易都已經變成持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-150">If a fully durable transaction or sp_flush_log successfully commit, all previously committed delayed durability transactions have been made durable.</span></span>  
  
 <span data-ttu-id="328cb-151">記錄可能會定期排清到磁碟。</span><span class="sxs-lookup"><span data-stu-id="328cb-151">The log may be flushed to disk periodically.</span></span> <span data-ttu-id="328cb-152">但是，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會提供持久交易和 sp_flush_log 以外的任何持久性保證。</span><span class="sxs-lookup"><span data-stu-id="328cb-152">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not provide any durability guarantees other than durable transactions and sp_flush_log.</span></span>  
  
## <a name="how-to-control-transaction-durability"></a><span data-ttu-id="328cb-153">如何控制交易持久性</span><span class="sxs-lookup"><span data-stu-id="328cb-153">How to control transaction durability</span></span>  
  
### <a name="database-level-control"></a><span data-ttu-id="328cb-154">資料庫層級控制</span><span class="sxs-lookup"><span data-stu-id="328cb-154">Database level control</span></span>  
 <span data-ttu-id="328cb-155">身為 DBA 的您，可以控制使用者是否能使用下列陳述式，在資料庫上使用延遲的交易持久性。</span><span class="sxs-lookup"><span data-stu-id="328cb-155">You, the DBA, can control whether users can use delayed transaction durability on a database with the following statement.</span></span> <span data-ttu-id="328cb-156">您必須使用 ALTER DATABASE 來設定延遲的持久性設定。</span><span class="sxs-lookup"><span data-stu-id="328cb-156">You must set the delayed durability setting with ALTER DATABASE.</span></span>  
  
```sql  
ALTER DATABASE ... SET DELAYED_DURABILITY = { DISABLED | ALLOWED | FORCED }  
```  
  
 `DISABLED`  
 <span data-ttu-id="328cb-157">[預設值] 使用這項設定時，在資料庫上認可的所有交易都是完全持久，不論認可層級設定為何 (DELAYED_DURABILITY=[ON | OFF])。</span><span class="sxs-lookup"><span data-stu-id="328cb-157">[default] With this setting, all transactions that commit on the database are fully durable, regardless of the commit level setting (DELAYED_DURABILITY=[ON | OFF]).</span></span> <span data-ttu-id="328cb-158">完全不需要進行預存程序變更和重新編譯。</span><span class="sxs-lookup"><span data-stu-id="328cb-158">There is no need for stored procedure change and recompilation.</span></span> <span data-ttu-id="328cb-159">這可讓您確保任何資料都不會因為延遲的持久性而面臨風險。</span><span class="sxs-lookup"><span data-stu-id="328cb-159">This allows you to ensure that no data is ever put at risk by delayed durability.</span></span>  
  
 `ALLOWED`  
 <span data-ttu-id="328cb-160">使用這項設定時，每筆交易的持久性都是在交易層級上決定的 - DELAYED_DURABILITY = { *OFF* | ON }。</span><span class="sxs-lookup"><span data-stu-id="328cb-160">With this setting, each transaction's durability is determined at the transaction level - DELAYED_DURABILITY = { *OFF* | ON }.</span></span> <span data-ttu-id="328cb-161">如需詳細資訊，請參閱不可部分完成[的區塊層級控制-原生編譯的預存程式](#atomic-block-level-control---natively-compiled-stored-procedures)和[COMMIT 層級控制 transact-sql](#commit-level-control---t-sql) 。</span><span class="sxs-lookup"><span data-stu-id="328cb-161">See [Atomic block level control - Natively Compiled Stored Procedures](#atomic-block-level-control---natively-compiled-stored-procedures) and [COMMIT level control - Transact-SQL](#commit-level-control---t-sql) for more information.</span></span>  
  
 `FORCED`  
 <span data-ttu-id="328cb-162">使用這項設定時，在資料庫上認可的每筆交易都是延遲的持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-162">With this setting, every transaction that commits on the database is delayed durable.</span></span> <span data-ttu-id="328cb-163">不論交易是否有指定完全持久 (DELAYED_DURABILITY = OFF) ，交易都是延遲的持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-163">Whether the transaction specifies fully durable (DELAYED_DURABILITY = OFF) or makes no specification, the transaction is delayed durable.</span></span> <span data-ttu-id="328cb-164">當延遲的交易持久性適用於資料庫，而且您不想要變更任何應用程式程式碼時，這項設定就很有用。</span><span class="sxs-lookup"><span data-stu-id="328cb-164">This setting is useful when delayed transaction durability is useful for a database and you do not want to change any application code.</span></span>  
  
### <a name="atomic-block-level-control---natively-compiled-stored-procedures"></a><span data-ttu-id="328cb-165"> ATOMIC 區塊等級控制 - 原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="328cb-165">Atomic block level control - Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="328cb-166">下列程式碼會進入不可部分完成的區塊內部。</span><span class="sxs-lookup"><span data-stu-id="328cb-166">The following code goes inside the atomic block.</span></span>  
  
```sql  
DELAYED_DURABILITY = { OFF | ON }  
```  
  
 `OFF`  
 <span data-ttu-id="328cb-167">[預設值] 交易是完全持久，除非資料庫選項 DELAYED_DURABLITY = FORCED 作用中，此時認可就是非同步，因而成為延遲的持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-167">[default] The transaction is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the commit is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="328cb-168">如需相關資訊，請參閱 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="328cb-168">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="328cb-169">交易是延遲的持久，除非資料庫選項 DELAYED_DURABLITY = DISABLED 作用中，此時認可就是同步，因而成為完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-169">The transaction is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the commit is synchronous and thus fully durable.</span></span>  <span data-ttu-id="328cb-170">如需相關資訊，請參閱 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="328cb-170">See [Database level control](#database-level-control) for more information.</span></span>  
  
 <span data-ttu-id="328cb-171">**範例程式碼：**</span><span class="sxs-lookup"><span data-stu-id="328cb-171">**Example Code:**</span></span>  
  
```sql  
CREATE PROCEDURE <procedureName> ...  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    DELAYED_DURABILITY = ON,  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'English'  
    ...  
)  
END  
```  
  
### <a name="table-1-durability-in-atomic-blocks"></a><span data-ttu-id="328cb-172">表格 1：ATOMIC 區塊的持久性</span><span class="sxs-lookup"><span data-stu-id="328cb-172">Table 1: Durability in Atomic Blocks</span></span>  
  
|<span data-ttu-id="328cb-173">不可部分完成的區塊持久性選項</span><span class="sxs-lookup"><span data-stu-id="328cb-173">Atomic block durability option</span></span>|<span data-ttu-id="328cb-174">無現有的交易</span><span class="sxs-lookup"><span data-stu-id="328cb-174">No existing transaction</span></span>|<span data-ttu-id="328cb-175">交易處理中 (完全或延遲的持久)</span><span class="sxs-lookup"><span data-stu-id="328cb-175">Transaction in process (fully or delayed durable)</span></span>|  
|------------------------------------|-----------------------------|---------------------------------------------------------|  
|`DELAYED_DURABILITY = OFF`|<span data-ttu-id="328cb-176">不可部分完成的區塊會啟動新的完全持久交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-176">Atomic block starts a new fully durable transaction.</span></span>|<span data-ttu-id="328cb-177">不可部分完成的區塊會在現有的交易中建立儲存點，然後開始新的交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-177">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
|`DELAYED_DURABILITY = ON`|<span data-ttu-id="328cb-178">不可部分完成的區塊會啟動新的延遲持久交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-178">Atomic block starts a new delayed durable transaction.</span></span>|<span data-ttu-id="328cb-179">不可部分完成的區塊會在現有的交易中建立儲存點，然後開始新的交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-179">Atomic block creates a save point in the existing transaction, then begins the new transaction.</span></span>|  
  
### <a name="commit-level-control---t-sql"></a><span data-ttu-id="328cb-180">COMMIT 層級控制- (T-sql) </span><span class="sxs-lookup"><span data-stu-id="328cb-180">COMMIT level control - (T-SQL)</span></span>
 <span data-ttu-id="328cb-181">COMMIT 語法已擴充，因此您可以強制延遲的交易持久性。</span><span class="sxs-lookup"><span data-stu-id="328cb-181">The COMMIT syntax is extended so you can force delayed transaction durability.</span></span> <span data-ttu-id="328cb-182">如果資料庫層級的 DELAYED_DURABILITY 是 DISABLED 或 FORCED (請參閱上述說明)，就會忽略這個 COMMIT 選項。</span><span class="sxs-lookup"><span data-stu-id="328cb-182">If DELAYED_DURABILITY is DISABLED or FORCED at the database level (see above) this COMMIT option is ignored.</span></span>  
  
```sql  
COMMIT [ { TRAN | TRANSACTION } ] [ transaction_name | @tran_name_variable ] ] [ WITH ( DELAYED_DURABILITY = { OFF | ON } ) ]  
  
```  
  
 `OFF`  
 <span data-ttu-id="328cb-183">[預設值] 交易 COMMIT 是完全持久，除非資料庫選項 DELAYED_DURABLITY = FORCED 作用中，此時 COMMIT 就是非同步，因而成為延遲的持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-183">[default] The transaction COMMIT is fully durable, unless the database option DELAYED_DURABLITY = FORCED is in effect, in which case the COMMIT is asynchronous and thus delayed durable.</span></span> <span data-ttu-id="328cb-184">如需相關資訊，請參閱 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="328cb-184">See [Database level control](#database-level-control) for more information.</span></span>  
  
 `ON`  
 <span data-ttu-id="328cb-185">交易 COMMIT 是延遲的持久，除非資料庫選項 DELAYED_DURABLITY = DISABLED 作用中，此時 COMMIT 就是同步，因而成為完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-185">The transaction COMMIT is delayed durable, unless the database option DELAYED_DURABLITY = DISABLED is in effect, in which case the COMMIT is synchronous and thus fully durable.</span></span> <span data-ttu-id="328cb-186">如需相關資訊，請參閱 [Database level control](#database-level-control) 。</span><span class="sxs-lookup"><span data-stu-id="328cb-186">See [Database level control](#database-level-control) for more information.</span></span>  
  
### <a name="summary-of-options-and-their-interactions"></a><span data-ttu-id="328cb-187">選項及其互動的摘要</span><span class="sxs-lookup"><span data-stu-id="328cb-187">Summary of options and their interactions</span></span>  
 <span data-ttu-id="328cb-188">下表將摘要說明資料庫層級延遲的持久性設定與認可層級設定之間的互動。</span><span class="sxs-lookup"><span data-stu-id="328cb-188">This table summarizes the interactions between database level delayed durability settings and commit level settings.</span></span> <span data-ttu-id="328cb-189">資料庫層級設定一律優先於認可層級設定。</span><span class="sxs-lookup"><span data-stu-id="328cb-189">Database level settings always take precedence over commit level settings.</span></span>  
  
|<span data-ttu-id="328cb-190">COMMIT 設定/資料庫設定</span><span class="sxs-lookup"><span data-stu-id="328cb-190">COMMIT setting/Database setting</span></span>|<span data-ttu-id="328cb-191">DELAYED_DURABILITY = DISABLED</span><span class="sxs-lookup"><span data-stu-id="328cb-191">DELAYED_DURABILITY = DISABLED</span></span>|<span data-ttu-id="328cb-192">DELAYED_DURABILITY = ALLOWED</span><span class="sxs-lookup"><span data-stu-id="328cb-192">DELAYED_DURABILITY = ALLOWED</span></span>|<span data-ttu-id="328cb-193">DELAYED_DURABILITY = FORCED</span><span class="sxs-lookup"><span data-stu-id="328cb-193">DELAYED_DURABILITY = FORCED</span></span>|  
|--------------------------------------|-------------------------------------|------------------------------------|-----------------------------------|  
|<span data-ttu-id="328cb-194">`DELAYED_DURABILITY = OFF` 資料庫層級交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-194">`DELAYED_DURABILITY = OFF` Database level transactions.</span></span>|<span data-ttu-id="328cb-195">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-195">Transaction is fully durable.</span></span>|<span data-ttu-id="328cb-196">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-196">Transaction is fully durable.</span></span>|<span data-ttu-id="328cb-197">交易是延遲的持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-197">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="328cb-198">`DELAYED_DURABILITY = ON` 資料庫層級交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-198">`DELAYED_DURABILITY = ON` Database level transactions.</span></span>|<span data-ttu-id="328cb-199">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-199">Transaction is fully durable.</span></span>|<span data-ttu-id="328cb-200">交易是延遲的持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-200">Transaction is delayed durable.</span></span>|<span data-ttu-id="328cb-201">交易是延遲的持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-201">Transaction is delayed durable.</span></span>|  
|<span data-ttu-id="328cb-202">`DELAYED_DURABILITY = OFF` 跨資料庫或分散式交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-202">`DELAYED_DURABILITY = OFF` Cross database or distributed transaction.</span></span>|<span data-ttu-id="328cb-203">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-203">Transaction is fully durable.</span></span>|<span data-ttu-id="328cb-204">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-204">Transaction is fully durable.</span></span>|<span data-ttu-id="328cb-205">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-205">Transaction is fully durable.</span></span>|  
|<span data-ttu-id="328cb-206">`DELAYED_DURABILITY = ON` 跨資料庫或分散式交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-206">`DELAYED_DURABILITY = ON` Cross database or distributed transaction.</span></span>|<span data-ttu-id="328cb-207">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-207">Transaction is fully durable.</span></span>|<span data-ttu-id="328cb-208">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-208">Transaction is fully durable.</span></span>|<span data-ttu-id="328cb-209">交易是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-209">Transaction is fully durable.</span></span>|  
  
## <a name="how-to-force-a-transaction-log-flush"></a><span data-ttu-id="328cb-210">如何強制交易記錄排清</span><span class="sxs-lookup"><span data-stu-id="328cb-210">How to force a transaction log flush</span></span>  
 <span data-ttu-id="328cb-211">強制將交易記錄排清至磁碟的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="328cb-211">There are two means to force flush the transaction log to disk.</span></span>  
  
-   <span data-ttu-id="328cb-212">執行任何更改相同資料庫的完全持久交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-212">Execute any fully durable transaction that alters the same database.</span></span> <span data-ttu-id="328cb-213">這會強制將所有先前認可之延遲持久交易的記錄檔記錄排清至磁碟。</span><span class="sxs-lookup"><span data-stu-id="328cb-213">This forces a flush of the log records of all preceding committed delayed durability transactions to disk.</span></span>  
  
-   <span data-ttu-id="328cb-214">執行系統預存程序 `sp_flush_log`。</span><span class="sxs-lookup"><span data-stu-id="328cb-214">Execute the system stored procedure `sp_flush_log`.</span></span> <span data-ttu-id="328cb-215">這個程序會強制將所有先前認可之延遲持久交易的記錄檔記錄排清至磁碟。</span><span class="sxs-lookup"><span data-stu-id="328cb-215">This procedure forces a flush of the log records of all preceding committed delayed durable transactions to disk.</span></span> <span data-ttu-id="328cb-216">如需詳細資訊，請參閱 [sys.sp_flush_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="328cb-216">For more information see [sys.sp_flush_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-flush-log-transact-sql).</span></span>  
  
##  <a name="delayed-durability-and-other-sql-server-features"></a><span data-ttu-id="328cb-217">延遲的持久性和其他 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="328cb-217">Delayed durability and other SQL Server features</span></span>  
 <span data-ttu-id="328cb-218">**變更追蹤和異動資料擷取**</span><span class="sxs-lookup"><span data-stu-id="328cb-218">**Change tracking and change data capture**</span></span>  
 <span data-ttu-id="328cb-219">所有具有變更追蹤的交易都是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-219">All transactions with change tracking are fully durable.</span></span> <span data-ttu-id="328cb-220">如果某筆交易會對啟用變更追蹤的資料表進行任何寫入作業，它就具有變更追蹤屬性。</span><span class="sxs-lookup"><span data-stu-id="328cb-220">A transaction has the change tracking property if it does any write operations to tables that are enabled for change tracking.</span></span> <span data-ttu-id="328cb-221">不支援使用異動資料擷取 (CDC) 之資料庫的延遲持久性。</span><span class="sxs-lookup"><span data-stu-id="328cb-221">The use of delayed durability is not supported for databases which use change data capture (CDC).</span></span>   
  
 <span data-ttu-id="328cb-222">**當機復原**</span><span class="sxs-lookup"><span data-stu-id="328cb-222">**Crash recovery**</span></span>  
 <span data-ttu-id="328cb-223">保證一致性，但是來自已經認可之延遲持久交易的某些變更可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="328cb-223">Consistency is guaranteed, but some changes from delayed durable transactions that have committed may be lost.</span></span>  
  
 <span data-ttu-id="328cb-224">**跨資料庫和 DTC**</span><span class="sxs-lookup"><span data-stu-id="328cb-224">**Cross-database and DTC**</span></span>  
 <span data-ttu-id="328cb-225">如果某筆交易是跨資料庫或分散式交易，不論任何資料庫或交易認可設定為何，它都是完全持久。</span><span class="sxs-lookup"><span data-stu-id="328cb-225">If a transaction is cross-database or distributed, if is fully durable, regardless of any database or transaction commit setting.</span></span>  
  
 <span data-ttu-id="328cb-226">**AlwaysOn 可用性群組和鏡像**</span><span class="sxs-lookup"><span data-stu-id="328cb-226">**Always On Availability Groups and Mirroring**</span></span>  
 <span data-ttu-id="328cb-227">延遲的持久交易無法在主要或任何次要資料庫上保證任何持久性。</span><span class="sxs-lookup"><span data-stu-id="328cb-227">Delayed durable transactions do not guarantee any durability on either the primary or any of the secondaries.</span></span> <span data-ttu-id="328cb-228">此外，它們無法保證任何關於次要資料庫上交易的知識。</span><span class="sxs-lookup"><span data-stu-id="328cb-228">In addition, they do not guarantee any knowledge about the transaction at the secondary.</span></span> <span data-ttu-id="328cb-229">認可之後，從任何同步的次要收到任何確認之前，就會將控制權傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="328cb-229">After commit, control is returned to the client before any acknowledgement is received from any synchronous secondary.</span></span>  
  
 <span data-ttu-id="328cb-230">**容錯移轉叢集**</span><span class="sxs-lookup"><span data-stu-id="328cb-230">**Failover clustering**</span></span>  
 <span data-ttu-id="328cb-231">某些延遲的持久交易寫入可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="328cb-231">Some delayed durable transaction writes might be lost.</span></span>  
  
 <span data-ttu-id="328cb-232">**交易複寫**</span><span class="sxs-lookup"><span data-stu-id="328cb-232">**Transaction Replication**</span></span>  
 <span data-ttu-id="328cb-233">異動複寫不支援延遲的持久交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-233">Delayed durable transactions is not supported with Transactional Replication.</span></span>  
  
 <span data-ttu-id="328cb-234">**記錄傳送**</span><span class="sxs-lookup"><span data-stu-id="328cb-234">**Log shipping**</span></span>  
 <span data-ttu-id="328cb-235">只有已經變成持久的交易才會包含在傳送的記錄中。</span><span class="sxs-lookup"><span data-stu-id="328cb-235">Only transactions that have been made durable are included in the log that is shipped.</span></span>  
  
 <span data-ttu-id="328cb-236">**記錄備份**</span><span class="sxs-lookup"><span data-stu-id="328cb-236">**Log Backup**</span></span>  
 <span data-ttu-id="328cb-237">只有已經變成持久的交易才會包含在備份中。</span><span class="sxs-lookup"><span data-stu-id="328cb-237">Only transactions that have been made durable are included in the backup.</span></span>  
  
## <a name="when-can-i-lose-data"></a><span data-ttu-id="328cb-238">我何時會遺失資料？</span><span class="sxs-lookup"><span data-stu-id="328cb-238">When can I lose data?</span></span>  
 <span data-ttu-id="328cb-239">如果您在任何資料表上實作延遲持久性，您應該了解特定環境會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="328cb-239">If you implement delayed durability on any of your tables, you should understand that certain circumstances can lead to data loss.</span></span> <span data-ttu-id="328cb-240">如果您無法容忍任何資料遺失，就不應該在資料表中使用延遲持久性。</span><span class="sxs-lookup"><span data-stu-id="328cb-240">If you cannot tolerate any data loss, you should not use delayed durability on your tables.</span></span>  
  
### <a name="catastrophic-events"></a><span data-ttu-id="328cb-241">重大事件</span><span class="sxs-lookup"><span data-stu-id="328cb-241">Catastrophic events</span></span>  
 <span data-ttu-id="328cb-242">發生重大事件 (例如伺服器當機) 時，您將遺失所有尚未儲存到磁碟的已認可交易資料。</span><span class="sxs-lookup"><span data-stu-id="328cb-242">In the case of a catastrophic event, like a server crash, you will lose the data for all committed transactions that have not been saved to disk.</span></span> <span data-ttu-id="328cb-243">每當針對資料表中的任何資料表 (持久性記憶體最佳化或以磁碟為基礎的資料表) 執行完全持久交易，或呼叫 `sp_flush_log` 時，即會將延遲的持久交易儲存到磁碟。</span><span class="sxs-lookup"><span data-stu-id="328cb-243">Delayed durable transactions are saved to disk whenever a fully durable transaction is executed against any table (durable memory-optimized or disk-based) in the database, or `sp_flush_log` is called.</span></span> <span data-ttu-id="328cb-244">如果您正在使用延遲的持久交易，您可以在資料庫中建立小型資料表，以便定期更新或定期呼叫 `sp_flush_log` 來儲存所有尚未認可完畢的交易。</span><span class="sxs-lookup"><span data-stu-id="328cb-244">If you are using delayed durable transactions, you may want to create a small table in the database that you can periodically update or periodically call `sp_flush_log` to save all outstanding committed transactions.</span></span> <span data-ttu-id="328cb-245">交易記錄也會在它已滿時排清，但這很難預期且無法控制。</span><span class="sxs-lookup"><span data-stu-id="328cb-245">The transaction log also flushes whenever it becomes full, but that is hard to predict and impossible to control.</span></span>  
  
### <a name="sql-server-shutdown-and-restart"></a><span data-ttu-id="328cb-246">SQL Server 關閉並重新啟動</span><span class="sxs-lookup"><span data-stu-id="328cb-246">SQL Server shutdown and restart</span></span>  
 <span data-ttu-id="328cb-247">針對延遲的持久性， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的意外關機與預期的關機/重新啟動之間並無差異。</span><span class="sxs-lookup"><span data-stu-id="328cb-247">For delayed durability, there is no difference between an unexpected shutdown and an expected shutdown/restart of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="328cb-248">就像重大事件一樣，您應該針對資料遺失進行規劃。</span><span class="sxs-lookup"><span data-stu-id="328cb-248">Like catastrophic events, you should plan for data loss.</span></span> <span data-ttu-id="328cb-249">在規劃好的關機/重新啟動中，部分尚未寫入磁碟的交易可能會先儲存到磁碟，但您不應該規劃相關事項。</span><span class="sxs-lookup"><span data-stu-id="328cb-249">In a planned shutdown/restart some transactions that have not been written to disk may first be saved to disk, but you should not plan on it.</span></span> <span data-ttu-id="328cb-250">對於類似關機/重新啟動的規劃 (不論是規劃或未規劃的) 都會像重大事件一樣遺失資料。</span><span class="sxs-lookup"><span data-stu-id="328cb-250">Plan as though a shutdown/restart, whether planned or unplanned, loses the data the same as a catastrophic event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328cb-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="328cb-251">See Also</span></span>  
 <span data-ttu-id="328cb-252">[交易隔離等級](../../database-engine/transaction-isolation-levels.md) </span><span class="sxs-lookup"><span data-stu-id="328cb-252">[Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) </span></span>  
 [<span data-ttu-id="328cb-253">搭配記憶體最佳化的資料表使用交易隔離等級的方針</span><span class="sxs-lookup"><span data-stu-id="328cb-253">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../in-memory-oltp/memory-optimized-tables.md)  
  
  
