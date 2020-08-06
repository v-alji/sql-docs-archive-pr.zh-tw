---
title: 在異動複寫中發行預存程序執行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], stored procedures and
- transactional replication, publishing stored procedure execution
ms.assetid: f4686f6f-c224-4f07-a7cb-92f4dd483158
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0fb5c40db46772cabcb5d1df19e03aced749e1c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706366"
---
# <a name="publishing-stored-procedure-execution-in-transactional-replication"></a><span data-ttu-id="bb65a-102">在異動複寫中發行預存程序執行</span><span class="sxs-lookup"><span data-stu-id="bb65a-102">Publishing Stored Procedure Execution in Transactional Replication</span></span>
  <span data-ttu-id="bb65a-103">如果您有一或多個預存程序在「發行者」端執行並且影響到已發行的資料表，請考慮在發行集中包含這些預存程序，以做為預存程序執行發行項。</span><span class="sxs-lookup"><span data-stu-id="bb65a-103">If you have one or more stored procedures that execute at the Publisher and affect published tables, consider including those stored procedures in your publication as stored procedure execution articles.</span></span> <span data-ttu-id="bb65a-104">初始化訂閱時，會將程序的定義 (CREATE PROCEDURE 陳述式) 複寫到訂閱者；在發行者端執行程序時，複寫會在訂閱者端執行對應的程序。</span><span class="sxs-lookup"><span data-stu-id="bb65a-104">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span> <span data-ttu-id="bb65a-105">這可在執行大批量作業時大幅提升效能，因為只會複寫程序執行，而無需複寫每個資料列的個別變更。</span><span class="sxs-lookup"><span data-stu-id="bb65a-105">This can provide significantly better performance for cases where large batch operations are performed, because only the procedure execution is replicated, bypassing the need to replicate the individual changes for each row.</span></span> <span data-ttu-id="bb65a-106">例如，假設您在發行集資料庫中建立了下列預存程序：</span><span class="sxs-lookup"><span data-stu-id="bb65a-106">For example, assume you create the following stored procedure in the publication database:</span></span>  
  
```  
CREATE PROC give_raise AS  
UPDATE EMPLOYEES SET salary = salary * 1.10  
```  
  
 <span data-ttu-id="bb65a-107">此程序讓公司的 10,000 位員工每人增加 10% 的收入。</span><span class="sxs-lookup"><span data-stu-id="bb65a-107">This procedure gives each of the 10,000 employees in your company a 10 percent pay increase.</span></span> <span data-ttu-id="bb65a-108">當您在「發行者」執行此預存程序，它會更新每一位員工的薪水。</span><span class="sxs-lookup"><span data-stu-id="bb65a-108">When you execute this stored procedure at the Publisher, it updates the salary for each employee.</span></span> <span data-ttu-id="bb65a-109">沒有預存程序執行複寫時，更新會傳送到「訂閱者」，做為較大的多步驟交易：</span><span class="sxs-lookup"><span data-stu-id="bb65a-109">Without the replication of stored procedure execution, the update would be sent to Subscribers as a large, multi-step transaction:</span></span>  
  
```  
BEGIN TRAN  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 1'  
UPDATE EMPLOYEES SET salary = salary * 1.10 WHERE PK = 'emp 2'  
```  
  
 <span data-ttu-id="bb65a-110">然後重複 10,000 次，完成所有更新。</span><span class="sxs-lookup"><span data-stu-id="bb65a-110">And this repeats for 10,000 updates.</span></span>  
  
 <span data-ttu-id="bb65a-111">有預存程序執行複寫時，複寫僅傳送命令以在「訂閱者」端執行預存程序，而不會將所有更新寫入散發資料庫，然後透過網路將它們傳送到「訂閱者」：</span><span class="sxs-lookup"><span data-stu-id="bb65a-111">With the replication of stored procedure execution, replication sends only the command to execute the stored procedure at the Subscriber, rather than writing all the updates to the distribution database and then sending them over the network to the Subscriber:</span></span>  
  
```  
EXEC give_raise  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bb65a-112">預存程序複寫並不適用於所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="bb65a-112">Stored procedure replication is not appropriate for all applications.</span></span> <span data-ttu-id="bb65a-113">如果發行項經水平篩選，以使「發行者」與「訂閱者」端的資料列組不同，則在兩端執行相同的預存程序將傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="bb65a-113">If an article is filtered horizontally, so that there are different sets of rows at the Publisher than at the Subscriber, executing the same stored procedure at both returns different results.</span></span> <span data-ttu-id="bb65a-114">同樣地，如果更新是基於其他非複寫資料表的子查詢，則在「發行者」和「訂閱者」端執行相同的預存程序也將傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="bb65a-114">Similarly, if an update is based on a subquery of another, nonreplicated table, executing the same stored procedure at both the Publisher and Subscriber returns different results.</span></span>  
  
 <span data-ttu-id="bb65a-115">**若要發行預存程序的執行**</span><span class="sxs-lookup"><span data-stu-id="bb65a-115">**To publish the execution of a stored procedure**</span></span>  
  
-   <span data-ttu-id="bb65a-116">SQL Server Management Studio：[在交易式發行集中發行預存程序的執行項 &#40;SQL Server Management Studio&#41;](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span><span class="sxs-lookup"><span data-stu-id="bb65a-116">SQL Server Management Studio: [Publish the Execution of a Stored Procedure in a Transactional Publication &#40;SQL Server Management Studio&#41;](../publish/publish-execution-of-stored-procedure-in-transactional-publication.md)</span></span>  
  
-   <span data-ttu-id="bb65a-117">複寫 Transact-sql 程式設計： [&#40;transact-sql&#41;執行 sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) ，並為參數指定 ' serializable proc exec ' (建議的) 或 ' proc exec ' 的值 **@type** 。</span><span class="sxs-lookup"><span data-stu-id="bb65a-117">Replication Transact-SQL Programming: execute [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and specify a value of 'serializable proc exec' (recommended) or 'proc exec' for the parameter **@type**.</span></span> <span data-ttu-id="bb65a-118">如需定義發行項的詳細資訊，請參閱[定義發行項](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="bb65a-118">For more information about defining articles, see [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="modifying-the-procedure-at-the-subscriber"></a><span data-ttu-id="bb65a-119">在訂閱者端修改程序</span><span class="sxs-lookup"><span data-stu-id="bb65a-119">Modifying the Procedure at the Subscriber</span></span>  
 <span data-ttu-id="bb65a-120">根據預設值，「發行者」的預存程序定義會傳播到各個「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="bb65a-120">By default, the stored procedure definition at the Publisher is propagated to each Subscriber.</span></span> <span data-ttu-id="bb65a-121">但是，您也可以在「訂閱者」端修改預存程序。</span><span class="sxs-lookup"><span data-stu-id="bb65a-121">However, you can also modify the stored procedure at the Subscriber.</span></span> <span data-ttu-id="bb65a-122">若您想在「發行者」和「訂閱者」執行不同的邏輯，這個方式就非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="bb65a-122">This is useful if you want different logic to be executed at the Publisher and Subscriber.</span></span> <span data-ttu-id="bb65a-123">例如，考慮 **sp_big_delete**這個「發行者」的預存程序有兩個功能：它會從複寫資料表 **big_table1** 刪除 1,000,000 個資料列，然後更新非複寫的資料表 **big_table2**。</span><span class="sxs-lookup"><span data-stu-id="bb65a-123">For example, consider **sp_big_delete**, a stored procedure at the Publisher that has two functions: it deletes 1,000,000 rows from the replicated table **big_table1** and updates the nonreplicated table **big_table2**.</span></span> <span data-ttu-id="bb65a-124">若要降低網路資源的需求，您應該透過發行 **sp_big_delete**，將一百萬個資料列刪除做為預存程序傳播。</span><span class="sxs-lookup"><span data-stu-id="bb65a-124">To reduce the demand on network resources, you should propagate the 1 million row delete as a stored procedure by publishing **sp_big_delete**.</span></span> <span data-ttu-id="bb65a-125">在「訂閱者」端，您可以將 **sp_big_delete** 修改為只刪除一百萬個資料列，並且不執行後續對 **big_table2**的更新。</span><span class="sxs-lookup"><span data-stu-id="bb65a-125">At the Subscriber, you can modify **sp_big_delete** to delete only the 1 million rows and not perform the subsequent update to **big_table2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb65a-126">依預設，使用 ALTER PROCEDURE 在「發行者」上所作的任何變更都將傳播到「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="bb65a-126">By default, any changes made using ALTER PROCEDURE at the Publisher are propagated to the Subscriber.</span></span> <span data-ttu-id="bb65a-127">若要防止發生這種情況，請在執行 ALTER PROCEDURE 之前停用結構描述變更的傳播。</span><span class="sxs-lookup"><span data-stu-id="bb65a-127">To prevent this, disable the propagation of schema changes before executing ALTER PROCEDURE.</span></span> <span data-ttu-id="bb65a-128">如需結構描述變更的資訊，請參閱[對發行集資料庫進行結構描述變更](../publish/make-schema-changes-on-publication-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="bb65a-128">For information about schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
## <a name="types-of-stored-procedure-execution-articles"></a><span data-ttu-id="bb65a-129">預存程序執行發行項的類型</span><span class="sxs-lookup"><span data-stu-id="bb65a-129">Types of Stored Procedure Execution Articles</span></span>  
 <span data-ttu-id="bb65a-130">可以透過兩種不同方式發行預存程序的執行：序列化程序執行發行項與程序執行發行項。</span><span class="sxs-lookup"><span data-stu-id="bb65a-130">There are two different ways in which the execution of a stored procedure can be published: serializable procedure execution article and procedure execution article.</span></span>  
  
-   <span data-ttu-id="bb65a-131">建議使用序列化方式，因為這種方式只有當程序在序列化交易的內容中執行時，才會複寫程序執行。</span><span class="sxs-lookup"><span data-stu-id="bb65a-131">The serializable option is recommended because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="bb65a-132">若預存程序從序列化交易外部執行時，對已發行的資料表中所做的資料變更，會複寫為一連串的 DML 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bb65a-132">If the stored procedure is executed from outside a serializable transaction, changes to data in published tables are replicated as a series of DML statements.</span></span> <span data-ttu-id="bb65a-133">這個行為保證「訂閱者」的資料可以和「發行者」的資料一致。</span><span class="sxs-lookup"><span data-stu-id="bb65a-133">This behavior contributes to making data at the Subscriber consistent with data at the Publisher.</span></span> <span data-ttu-id="bb65a-134">這個方法對於批次作業而言特別有用，例如大型的清除作業。</span><span class="sxs-lookup"><span data-stu-id="bb65a-134">This is especially useful for batch operations, such as large cleanup operations.</span></span>  
  
-   <span data-ttu-id="bb65a-135">利用程序執行選項可以將執行複寫到所有「訂閱者」，而不管預存程序中的個別陳述式是否成功。</span><span class="sxs-lookup"><span data-stu-id="bb65a-135">With the procedure execution option, it is possible that execution could be replicated to all Subscribers regardless of whether individual statements in the stored procedure were successful.</span></span> <span data-ttu-id="bb65a-136">此外，因為預存程序對資料所做的變更，可以發生在多個交易中，「訂閱者」的資料可能不會與「發行者」的資料一致。</span><span class="sxs-lookup"><span data-stu-id="bb65a-136">Furthermore, because changes made to data by the stored procedure can occur within multiple transactions, data at the Subscribers might not be consistent with data at the Publisher.</span></span> <span data-ttu-id="bb65a-137">若要處理這些問題，「訂閱者」必須是唯讀的，而且您所使用的隔離等級必須大於讀取未認可。</span><span class="sxs-lookup"><span data-stu-id="bb65a-137">To address these issues, it is required that Subscribers are read-only and that you use an isolation level greater than read uncommitted.</span></span> <span data-ttu-id="bb65a-138">如果您使用讀取未認可，則對已發行資料表中所做的資料變更會複寫為一連串的 DML 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bb65a-138">If you use read uncommitted, changes to data in published tables are replicated as a series of DML statements.</span></span>  
  
 <span data-ttu-id="bb65a-139">以下範例說明當您將程序的複寫設定為序列化程序發行項 (Article) 時的建議方式。</span><span class="sxs-lookup"><span data-stu-id="bb65a-139">The following example illustrates why it is recommended that you set up replication of procedures as serializable procedure articles.</span></span>  
  
```  
BEGIN TRANSACTION T1  
SELECT @var = max(col1) FROM tableA  
UPDATE tableA SET col2 = <value>   
   WHERE col1 = @var   
  
BEGIN TRANSACTION T2  
INSERT tableA VALUES <values>  
COMMIT TRANSACTION T2  
```  
  
 <span data-ttu-id="bb65a-140">上面的範例假設交易 T1 的 SELECT 比交易 T2 的 INSERT 先發生。</span><span class="sxs-lookup"><span data-stu-id="bb65a-140">In the previous example, it is assumed that the SELECT in transaction T1 happens before the INSERT in transaction T2.</span></span>  
  
 <span data-ttu-id="bb65a-141">如果程序並非在序列化交易內執行 (隔離等級設定為 SERIALIZABLE)，交易 T2 便可插入新的資料列到 T1 的 SELECT 陳述式範圍內，並在 T1 之前認可。</span><span class="sxs-lookup"><span data-stu-id="bb65a-141">If the procedure is not executed within a serializable transaction (with isolation level set to SERIALIZABLE), transaction T2 will be allowed to insert a new row within the range of the SELECT statement in T1 and it will commit before T1.</span></span> <span data-ttu-id="bb65a-142">這也表示 T2 會比 T1 先套用於「訂閱者」。</span><span class="sxs-lookup"><span data-stu-id="bb65a-142">This also means that it will be applied at the Subscriber before T1.</span></span> <span data-ttu-id="bb65a-143">當 T1 套用於「訂閱者」時，SELECT 傳回的值可能和位於「發行者」時的值不同，並且可能導致 UPDATE 產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="bb65a-143">When T1 is applied at the Subscriber, the SELECT can potentially return a different value than at the Publisher and can result in a different outcome from the UPDATE.</span></span>  
  
 <span data-ttu-id="bb65a-144">如果程序執行於序列化交易內，交易 T2 則不被允許在 T2 的 SELECT 陳述式所涵蓋的範圍內插入。</span><span class="sxs-lookup"><span data-stu-id="bb65a-144">If the procedure is executed within a serializable transaction, transaction T2 will not be allowed to insert within the range covered by the SELECT statement in T2.</span></span> <span data-ttu-id="bb65a-145">此動作會被封鎖直到 T1 認可而確保「訂閱者」有相同的結果為止。</span><span class="sxs-lookup"><span data-stu-id="bb65a-145">It will be blocked until T1 commits ensuring the same results at the Subscriber.</span></span>  
  
 <span data-ttu-id="bb65a-146">當您在序列化交易內執行程序時，鎖定的時間更長且可能導致並行性降低。</span><span class="sxs-lookup"><span data-stu-id="bb65a-146">Locks will be held longer when you execute the procedure within a serializable transaction and may result in reduced concurrency.</span></span>  
  
## <a name="the-xact_abort-setting"></a><span data-ttu-id="bb65a-147">XACT_ABORT 設定</span><span class="sxs-lookup"><span data-stu-id="bb65a-147">The XACT_ABORT Setting</span></span>  
 <span data-ttu-id="bb65a-148">複寫預存程序執行時，執行預存程序之工作階段的設定應將 XACT_ABORT 指定為 ON。</span><span class="sxs-lookup"><span data-stu-id="bb65a-148">When replicating stored procedure execution, the setting for the session executing the stored procedure should specify XACT_ABORT ON.</span></span> <span data-ttu-id="bb65a-149">如果 XACT_ABORT 設定為 OFF，並在「發行者」端執行程序時出現錯誤，則「訂閱者」端也會出現相同的錯誤，導致「散發代理程式」失敗。</span><span class="sxs-lookup"><span data-stu-id="bb65a-149">If XACT_ABORT is set to OFF, and an error occurs during execution of the procedure at the Publisher, the same error will occur at the Subscriber, causing the Distribution Agent to fail.</span></span> <span data-ttu-id="bb65a-150">將 XACT_ABORT 指定為 ON 可確保「發行者」端執行期間遇到的任何錯誤，都會使整個執行回復，以避免「散發代理程式」失敗。</span><span class="sxs-lookup"><span data-stu-id="bb65a-150">Specifying XACT_ABORT ON ensures that any errors encountered during execution at the Publisher cause the entire execution to be rolled back, avoiding the Distribution Agent failure.</span></span> <span data-ttu-id="bb65a-151">如需設定 XACT_ABORT 的詳細資訊，請參閱 [SET XACT_ABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-xact-abort-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bb65a-151">For more information about setting XACT_ABORT, see [SET XACT_ABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-xact-abort-transact-sql).</span></span>  
  
 <span data-ttu-id="bb65a-152">如果您需要將 XACT_ABORT 設定為 OFF，請指定「散發代理程式」的 **-SkipErrors** 參數。</span><span class="sxs-lookup"><span data-stu-id="bb65a-152">If you require a setting of XACT_ABORT OFF, specify the **-SkipErrors** parameter for the Distribution Agent.</span></span> <span data-ttu-id="bb65a-153">這將允許代理程式在遇到錯誤後，繼續在「訂閱者」端套用變更。</span><span class="sxs-lookup"><span data-stu-id="bb65a-153">This allows the agent to continue applying changes at the Subscriber even if an error is encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb65a-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb65a-154">See Also</span></span>  
 [<span data-ttu-id="bb65a-155">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="bb65a-155">Article Options for Transactional Replication</span></span>](article-options-for-transactional-replication.md)  
  
  
