---
title: 記憶體優化資料表上交易的重試邏輯指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2a35c37-4449-49ee-8bba-928028f1de66
author: stevestein
ms.author: sstein
ms.openlocfilehash: c9ffaccefb8d4e0a3044c4858a06029fd4350354
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701581"
---
# <a name="guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables"></a><span data-ttu-id="a348f-102">記憶體最佳化資料表交易的重試邏輯方針</span><span class="sxs-lookup"><span data-stu-id="a348f-102">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>
  <span data-ttu-id="a348f-103">存取記憶體最佳化資料表的交易會產生一些錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="a348f-103">There are error conditions that occur with transactions that access memory-optimized tables.</span></span>  
  
-   41302. <span data-ttu-id="a348f-104">目前交易嘗試更新自從此交易啟動以來已經更新的記錄。</span><span class="sxs-lookup"><span data-stu-id="a348f-104">The current transaction attempted to update a record that has been updated since the transaction started.</span></span>  
  
-   41305. <span data-ttu-id="a348f-105">目前的交易無法認可，因為可重複的讀取驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="a348f-105">The current transaction failed to commit due to a repeatable read validation failure.</span></span>  
  
-   41325. <span data-ttu-id="a348f-106">目前的交易無法認可，因為可序列化驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="a348f-106">The current transaction failed to commit due to a serializable validation failure.</span></span>  
  
-   41301. <span data-ttu-id="a348f-107">目前交易具有相依性的先前交易已經中止，而且目前交易無法再認可。</span><span class="sxs-lookup"><span data-stu-id="a348f-107">A previous transaction that the current transaction took a dependency on has aborted, and the current transaction can no longer commit.</span></span>  
  
 <span data-ttu-id="a348f-108">這些錯誤的常見原因是同時執行中交易之間的干擾。</span><span class="sxs-lookup"><span data-stu-id="a348f-108">A common cause of these errors is interference between concurrently executing transaction.</span></span> <span data-ttu-id="a348f-109">常見的更正動作是重試交易。</span><span class="sxs-lookup"><span data-stu-id="a348f-109">The common corrective action is to retry the transaction.</span></span>  
  
 <span data-ttu-id="a348f-110">如需有關這些錯誤狀況的詳細資訊，請參閱[記憶體優化資料表中交易](../relational-databases/in-memory-oltp/memory-optimized-tables.md)的衝突偵測、驗證和認可相依性檢查一節。</span><span class="sxs-lookup"><span data-stu-id="a348f-110">For more information about these error conditions, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="a348f-111">記憶體最佳化的資料表不能發生死結 (錯誤碼 1205)。</span><span class="sxs-lookup"><span data-stu-id="a348f-111">Deadlocks (error code 1205) cannot occur for memory-optimized tables.</span></span> <span data-ttu-id="a348f-112">鎖定未用於記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="a348f-112">Locks are not used for memory-optimized tables.</span></span> <span data-ttu-id="a348f-113">不過，如果應用程式已經包含死結的重試邏輯，現有邏輯可擴充成包含新的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a348f-113">However, if the application already contains retry logic for deadlocks, the existing logic could be extended to include the new error codes.</span></span>  
  
## <a name="considerations-for-retrying"></a><span data-ttu-id="a348f-114">重試考量</span><span class="sxs-lookup"><span data-stu-id="a348f-114">Considerations for Retrying</span></span>  
 <span data-ttu-id="a348f-115">應用程式通常會發生交易之間的衝突，而需要實作重試邏輯以解決這些衝突。</span><span class="sxs-lookup"><span data-stu-id="a348f-115">Applications will typically encounter conflicts between transactions and need to implement retry logic to resolve those conflicts.</span></span> <span data-ttu-id="a348f-116">遇到的衝突數目取決於一些因素：</span><span class="sxs-lookup"><span data-stu-id="a348f-116">The number of conflicts encountered depends on a number of factors:</span></span>  
  
-   <span data-ttu-id="a348f-117">個別資料列的競爭。</span><span class="sxs-lookup"><span data-stu-id="a348f-117">Contention for individual rows.</span></span> <span data-ttu-id="a348f-118">隨著嘗試更新相同資料列的交易數目增加，發生衝突的可能性也會增加。</span><span class="sxs-lookup"><span data-stu-id="a348f-118">The potential for conflicts increases as the number of transactions attempting to update the same row increases.</span></span>  
  
-   <span data-ttu-id="a348f-119">REPEATABLE READ 交易讀取的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="a348f-119">Number of rows read by REPEATABLE READ transactions.</span></span> <span data-ttu-id="a348f-120">讀取的資料列愈多，並行交易更新其中一些資料列的可能性愈大。</span><span class="sxs-lookup"><span data-stu-id="a348f-120">The more rows read, the greater the chance that some of these rows are updated by concurrent transactions.</span></span> <span data-ttu-id="a348f-121">這會造成可重複的讀取驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="a348f-121">This causes repeatable read validation failures.</span></span>  
  
-   <span data-ttu-id="a348f-122">SERIALIZABLE 交易使用的掃描範圍大小。</span><span class="sxs-lookup"><span data-stu-id="a348f-122">Size of the scan ranges used by SERIALIZABLE transactions.</span></span> <span data-ttu-id="a348f-123">掃描範圍愈大，並行交易導入虛設項目列，造成可序列化驗證失敗的機率愈高。</span><span class="sxs-lookup"><span data-stu-id="a348f-123">The larger the scan ranges, the higher the chance that concurrent transactions will introduce phantom rows, causing serializable validation failures.</span></span>  
  
     <span data-ttu-id="a348f-124">應用程式難以避免這些衝突，因此需要重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="a348f-124">It is difficult for an application to avoid these conflicts, requiring retry logic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a348f-125">存取記憶體最佳化資料表的讀取/寫入交易需要重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="a348f-125">Read-write transactions that access memory-optimized tables require retry logic.</span></span>  
  
### <a name="considerations-for-read-only-transactions-and-natively-compiled-stored-procedures"></a><span data-ttu-id="a348f-126">唯讀交易和原生編譯預存程序的考量</span><span class="sxs-lookup"><span data-stu-id="a348f-126">Considerations for Read-Only Transactions and Natively Compiled Stored Procedures</span></span>  
 <span data-ttu-id="a348f-127">跨越原生編譯預存程序單次執行的唯讀交易不需要 REPEATABLE READ 和 SERIALIZABLE 交易驗證。</span><span class="sxs-lookup"><span data-stu-id="a348f-127">Read-only transactions that span a single execution of a natively compiled stored procedure do not require validation for REPEATABLE READ and SERIALIZABLE transactions.</span></span> <span data-ttu-id="a348f-128">因為交易是唯讀，寫入衝突不會發生。</span><span class="sxs-lookup"><span data-stu-id="a348f-128">Write conflicts cannot occur due to a transaction being read-only.</span></span>  
  
 <span data-ttu-id="a348f-129">不過，相依性失敗可能仍然發生。</span><span class="sxs-lookup"><span data-stu-id="a348f-129">However, dependency failures can still occur.</span></span> <span data-ttu-id="a348f-130">相依性失敗比因衝突所導致的錯誤更少見。</span><span class="sxs-lookup"><span data-stu-id="a348f-130">Dependency failures are rarer than errors resulting from conflicts.</span></span> <span data-ttu-id="a348f-131">因此，在大部分情況下，跨越原生編譯預存程序單次執行的唯讀交易不需要特定重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="a348f-131">Therefore, in many cases, specific retry logic is not required for read-only transactions that span single executions of natively compiled stored procedures.</span></span>  
  
### <a name="considerations-for-read-only-transactions-and-cross-container-transactions"></a><span data-ttu-id="a348f-132">唯讀交易和跨容器交易的考量</span><span class="sxs-lookup"><span data-stu-id="a348f-132">Considerations for Read-Only Transactions and Cross-Container Transactions</span></span>  
 <span data-ttu-id="a348f-133">唯讀跨容器交易是在原生編譯預存程序的內容之外開始，如果記憶體最佳化的資料表都是在 SNAPSHOT 隔離下存取，這類交易不會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="a348f-133">Read-only cross-container transactions, which are transactions that are started outside the context of a natively compiled stored procedure, do not perform validation if the memory-optimized tables are all accessed under SNAPSHOT isolation.</span></span> <span data-ttu-id="a348f-134">不過，當記憶體最佳化的資料表是在 REPEATABLE READ 或 SERIALIZABLE 隔離下存取時，在認可時會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="a348f-134">However, when memory-optimized tables are accessed under REPEATABLE READ or SERIALIZABLE isolation, validation is performed at commit time.</span></span> <span data-ttu-id="a348f-135">在此情況下，可能需要重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="a348f-135">In this case, retry logic may be required.</span></span>  
  
 <span data-ttu-id="a348f-136">如需詳細資訊，請參閱[交易隔離等級](../../2014/database-engine/transaction-isolation-levels.md)中的跨容器交易一節。</span><span class="sxs-lookup"><span data-stu-id="a348f-136">For more information, see the section on Cross-Container Transactions in [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
## <a name="implementing-retry-logic"></a><span data-ttu-id="a348f-137">實作重試邏輯</span><span class="sxs-lookup"><span data-stu-id="a348f-137">Implementing Retry Logic</span></span>  
 <span data-ttu-id="a348f-138">如同存取記憶體最佳化資料表的所有交易，您必須考慮重試邏輯以處理潛在的失敗，例如寫入衝突 (錯誤碼 41302) 或相依性失敗 (錯誤碼 41301)。</span><span class="sxs-lookup"><span data-stu-id="a348f-138">As with all transactions that access memory-optimized tables, you need to consider retry logic to handle potential failures, such as write conflicts (error code 41302) or dependency failures (error code 41301).</span></span> <span data-ttu-id="a348f-139">在多數應用程式中的失敗率都很低，不過仍然必須透過重試交易處理失敗。</span><span class="sxs-lookup"><span data-stu-id="a348f-139">In most applications the failure rate will be low, but it is still necessary to handle failures by retrying the transaction.</span></span> <span data-ttu-id="a348f-140">兩個實作重試邏輯的建議方式如下：</span><span class="sxs-lookup"><span data-stu-id="a348f-140">Two suggested ways of implementing retry logic are:</span></span>  
  
-   <span data-ttu-id="a348f-141">用戶端重試。</span><span class="sxs-lookup"><span data-stu-id="a348f-141">Client-side retries.</span></span> <span data-ttu-id="a348f-142">在一般情況中，用戶端重試是較適合實作重試邏輯的方式。</span><span class="sxs-lookup"><span data-stu-id="a348f-142">Client-side retries is the preferred way to implement retry logic in the general case.</span></span> <span data-ttu-id="a348f-143">用戶端應用程式會擷取交易擲出的錯誤，然後重試交易。</span><span class="sxs-lookup"><span data-stu-id="a348f-143">The client application catches the error thrown by the transaction, and retries the transaction.</span></span> <span data-ttu-id="a348f-144">若現有的用戶端應用程式有處理死結的重試邏輯，您可以擴充應用程式以處理新的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a348f-144">If an existing client application has retry logic to handle deadlocks, you can extend the application to handle the new error codes.</span></span>  
  
-   <span data-ttu-id="a348f-145">使用包裝函式預存程序。</span><span class="sxs-lookup"><span data-stu-id="a348f-145">Using a wrapper stored procedure.</span></span> <span data-ttu-id="a348f-146">用戶端會呼叫解譯的 [!INCLUDE[tsql](../includes/tsql-md.md)] 預存程序，其會呼叫原生編譯的預存程序或執行交易。</span><span class="sxs-lookup"><span data-stu-id="a348f-146">The client calls an interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] stored procedure that calls the natively compiled stored procedure or executes the transaction.</span></span> <span data-ttu-id="a348f-147">包裝函式程序會隨後視需要使用 try/catch 邏輯，擷取錯誤及重試程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="a348f-147">The wrapper procedure then uses try/catch logic to catch the error and retry the procedure call if needed.</span></span> <span data-ttu-id="a348f-148">這可能會在失敗前將該結果傳回用戶端，而且用戶端不會知道要將其捨棄。</span><span class="sxs-lookup"><span data-stu-id="a348f-148">It is possible that results are returned to the client before the failure, and the client would not know to discard them.</span></span> <span data-ttu-id="a348f-149">因此，為了安全起見，最好只搭配不傳回任何結果集至用戶端的原生編譯預存程序來使用此方法。</span><span class="sxs-lookup"><span data-stu-id="a348f-149">Therefore, to be safe, it is best to use this method only with natively compiled stored procedures that do not return any result sets to the client.</span></span>  
  
 <span data-ttu-id="a348f-150">重試邏輯可在 [!INCLUDE[tsql](../includes/tsql-md.md)] 中或在中間層的應用程式程式碼中實作。</span><span class="sxs-lookup"><span data-stu-id="a348f-150">The retry logic can be implemented either in [!INCLUDE[tsql](../includes/tsql-md.md)] or in the application code in the mid-tier.</span></span>  
  
 <span data-ttu-id="a348f-151">考慮重試邏輯的兩個可能原因如下：</span><span class="sxs-lookup"><span data-stu-id="a348f-151">Two possible reasons to consider the retry logic are:</span></span>  
  
-   <span data-ttu-id="a348f-152">用戶端應用程式有其他錯誤碼 (例如 1205) 的重試邏輯，這些錯誤碼是可擴充的。</span><span class="sxs-lookup"><span data-stu-id="a348f-152">The client application has retry logic for other error codes, such as 1205, which you can extend.</span></span>  
  
-   <span data-ttu-id="a348f-153">衝突很少，而使用備妥的執行，減少端對端延遲很重要。</span><span class="sxs-lookup"><span data-stu-id="a348f-153">Conflicts are rare, and it is important to reduce end-to-end latency by using prepared execution.</span></span> <span data-ttu-id="a348f-154">如需直接執行原生編譯預存程式的詳細資訊，請參閱原生[編譯的預存程式](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a348f-154">For more information about executing natively compiled stored procedures directly, see [Natively Compiled Stored Procedures](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="a348f-155">下列範例示範解譯的 [!INCLUDE[tsql](../includes/tsql-md.md)] 預存程序中的重試邏輯，該預存程序包含原生編譯預存程序或跨容器交易的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a348f-155">The following sample shows retry logic in an interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] stored procedure that contains a call either to a natively compiled stored procedure or to a cross-container transaction.</span></span>  
  
```sql  
CREATE PROCEDURE usp_my_procedure @param1 type1, @param2 type2, ...  
AS  
BEGIN  
  -- number of retries - tune based on the workload  
  DECLARE @retry INT = 10  
  
  WHILE (@retry > 0)  
  BEGIN  
    BEGIN TRY  
  
      -- exec usp_my_native_proc @param1, @param2, ...  
  
      --       or  
  
      -- BEGIN TRANSACTION  
      --   ...  
      -- COMMIT TRANSACTION  
  
      SET @retry = 0  
    END TRY  
    BEGIN CATCH  
      SET @retry -= 1  
  
      -- the error number for deadlocks (1205) does not need to be included for   
      -- transactions that do not access disk-based tables  
      IF (@retry > 0 AND error_number() in (41302, 41305, 41325, 41301, 1205))  
      BEGIN  
        -- these error conditions are transaction dooming - rollback the transaction  
        -- this is not needed if the transaction spans a single native proc execution  
        --   as the native proc will simply rollback when an error is thrown   
        IF XACT_STATE() = -1  
          ROLLBACK TRANSACTION  
  
        -- use a delay if there is a high rate of write conflicts (41302)  
        --   length of delay should depend on the typical duration of conflicting transactions  
        -- WAITFOR DELAY '00:00:00.001'  
      END  
      ELSE  
      BEGIN  
        -- insert custom error handling for other error conditions here  
  
        -- throw if this is not a qualifying error condition  
        ;THROW  
      END  
    END CATCH  
  END  
END  
```  
  
## <a name="see-also"></a><span data-ttu-id="a348f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a348f-156">See Also</span></span>  
 <span data-ttu-id="a348f-157">[瞭解記憶體優化資料表上的交易](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a348f-157">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="a348f-158">[記憶體優化資料表中的交易](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="a348f-158">[Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="a348f-159">搭配記憶體最佳化的資料表使用交易隔離等級的方針</span><span class="sxs-lookup"><span data-stu-id="a348f-159">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)  
  
  
