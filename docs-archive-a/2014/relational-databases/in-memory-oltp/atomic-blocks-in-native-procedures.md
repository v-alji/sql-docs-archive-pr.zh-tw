---
title: 不可部分完成的區塊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 40e0e749-260c-4cfc-a848-444d30c09d85
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ca8f5b4d767ef0fe836cd260f8d12dd5b40c75d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592007"
---
# <a name="atomic-blocks"></a><span data-ttu-id="f4e20-102">不可部分完成的區塊</span><span class="sxs-lookup"><span data-stu-id="f4e20-102">Atomic Blocks</span></span>
  <span data-ttu-id="f4e20-103">`BEGIN ATOMIC` 是 ANSI SQL 標準的一部分。</span><span class="sxs-lookup"><span data-stu-id="f4e20-103">`BEGIN ATOMIC` is part of the ANSI SQL standard.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f4e20-104">只有在最上層原生編譯預存程序才支援不可部分完成的區塊。</span><span class="sxs-lookup"><span data-stu-id="f4e20-104">supports atomic blocks only at the top-level of natively compiled stored procedures.</span></span>  
  
-   <span data-ttu-id="f4e20-105">每個原生編譯預存程序剛好包含一個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="f4e20-105">Every natively compiled stored procedure contains exactly one block of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="f4e20-106">這是 ATOMIC 區塊。</span><span class="sxs-lookup"><span data-stu-id="f4e20-106">This is an ATOMIC block.</span></span>  
  
-   <span data-ttu-id="f4e20-107">非原生、解譯的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序和隨選批次不支援不可部分完成的區塊。</span><span class="sxs-lookup"><span data-stu-id="f4e20-107">Non-native, interpreted [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and ad hoc batches do not support atomic blocks.</span></span>  
  
 <span data-ttu-id="f4e20-108">不可部分完成的區塊會在交易內執行 (以不可分割方式)。</span><span class="sxs-lookup"><span data-stu-id="f4e20-108">Atomic blocks are executed (atomically) within the transaction.</span></span> <span data-ttu-id="f4e20-109">區塊中的所有陳述式將會成功，或是整個區塊將會回復到區塊開頭所建立的儲存點。</span><span class="sxs-lookup"><span data-stu-id="f4e20-109">Either all statements in the block succeed or the entire block will be rolled back to the savepoint that was created at the start of the block.</span></span> <span data-ttu-id="f4e20-110">此外，對於不可部分完成的區塊而言，工作階段設定是固定的。</span><span class="sxs-lookup"><span data-stu-id="f4e20-110">In addition, the session settings are fixed for the atomic block.</span></span> <span data-ttu-id="f4e20-111">在工作階段中以不同設定執行相同的不可部分完成的區塊將會產生相同的行為，與目前工作階段的設定無關。</span><span class="sxs-lookup"><span data-stu-id="f4e20-111">Executing the same atomic block in sessions with different settings will result in the same behavior, independent of the settings of the current session.</span></span>  
  
## <a name="transactions-and-error-handling"></a><span data-ttu-id="f4e20-112">交易和錯誤處理</span><span class="sxs-lookup"><span data-stu-id="f4e20-112">Transactions and Error Handling</span></span>  
 <span data-ttu-id="f4e20-113">如果交易已經存在於工作階段 (因為執行 `BEGIN TRANSACTION` 陳述式的批次和交易依然使用中)，則啟動不可部分完成的區塊將會在交易中建立儲存點。</span><span class="sxs-lookup"><span data-stu-id="f4e20-113">If a transaction already exists on a session (because a batch executed a `BEGIN TRANSACTION` statement and the transaction remains active), then starting an atomic block will create a savepoint in the transaction.</span></span> <span data-ttu-id="f4e20-114">如果區塊結束而沒有發生例外狀況，則會認可針對區塊建立的儲存點，但在工作階段層級的交易認可之前不會認可交易。</span><span class="sxs-lookup"><span data-stu-id="f4e20-114">If the block exits without an exception, the savepoint that was created for the block commits, but the transaction will not commit until the transaction at the session level commits.</span></span> <span data-ttu-id="f4e20-115">如果區塊擲回例外狀況，則會回復區塊的作用，但是工作階段層級的交易將會繼續，除非例外狀況讓交易毀滅。</span><span class="sxs-lookup"><span data-stu-id="f4e20-115">If the block throws an exception, the effects of the block are rolled back but the transaction at the session level will proceed, unless the exception is transaction-dooming.</span></span> <span data-ttu-id="f4e20-116">例如，寫入衝突將會毀滅交易，但類型轉換錯誤則不會。</span><span class="sxs-lookup"><span data-stu-id="f4e20-116">For example a write conflict is transaction-dooming, but not a type casting error.</span></span>  
  
 <span data-ttu-id="f4e20-117">如果工作階段上沒有使用中交易，`BEGIN ATOMIC` 將會開始新的交易。</span><span class="sxs-lookup"><span data-stu-id="f4e20-117">If there is no active transaction on a session, `BEGIN ATOMIC` will start a new transaction.</span></span> <span data-ttu-id="f4e20-118">如果區塊範圍之外未擲回任何例外狀況，此交易將會在區塊結尾認可。</span><span class="sxs-lookup"><span data-stu-id="f4e20-118">If no exception is thrown outside the scope of the block, the transaction will be committed at the end of the block.</span></span> <span data-ttu-id="f4e20-119">如果區塊擲回例外狀況 (也就是說，未在區塊內捕捉及處理例外狀況)，交易將會回復。</span><span class="sxs-lookup"><span data-stu-id="f4e20-119">If the block throws an exception (that is, the exception is not caught and handled within the block), the transaction will be rolled back.</span></span> <span data-ttu-id="f4e20-120">如果交易橫跨單一不可部分完成的區塊 (單一原生編譯的預存程序)，您就不需要撰寫明確的 `BEGIN TRANSACTION` 和 `COMMIT` 或 `ROLLBACK` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f4e20-120">For transactions that span a single atomic block (a single natively compiled stored procedure), you do not need to write explicit `BEGIN TRANSACTION` and `COMMIT` or `ROLLBACK` statements.</span></span>  
  
 <span data-ttu-id="f4e20-121">原生編譯的預存程序支援 `TRY`、`CATCH` 和 `THROW` 建構用於錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="f4e20-121">Natively compiled stored procedures support the `TRY`, `CATCH`, and `THROW` constructs for error handling.</span></span> <span data-ttu-id="f4e20-122">不支援 `RAISERROR`。</span><span class="sxs-lookup"><span data-stu-id="f4e20-122">`RAISERROR` is not supported.</span></span>  
  
 <span data-ttu-id="f4e20-123">下列範例說明使用不可部分完成的區塊和原生編譯預存程序處理錯誤的行為：</span><span class="sxs-lookup"><span data-stu-id="f4e20-123">The following example illustrates the error handling behavior with atomic blocks and natively compiled stored procedures:</span></span>  
  
```sql  
-- sample table  
CREATE TABLE dbo.t1 (  
  c1 int not null primary key nonclustered  
)  
WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- sample proc that inserts 2 rows  
CREATE PROCEDURE dbo.usp_t1 @v1 bigint not null, @v2 bigint not null  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC  
WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english', DELAYED_DURABILITY = ON)  
  
  INSERT dbo.t1 VALUES (@v1)  
  INSERT dbo.t1 VALUES (@v2)  
  
END  
GO  
  
-- insert two rows  
EXEC dbo.usp_t1 1, 2  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify the rows 1 and 2 were committed  
SELECT c1 FROM dbo.t1  
GO  
  
-- execute proc with arithmetic overflow  
EXEC dbo.usp_t1 3, 4444444444444  
GO  
-- expected error message:  
-- Msg 8115, Level 16, State 0, Procedure usp_t1  
-- Arithmetic overflow error converting bigint to data type int.  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 was not committed; usp_t1 has been rolled back  
SELECT c1 FROM dbo.t1  
GO  
  
-- start a new transaction  
BEGIN TRANSACTION  
  -- insert rows 3 and 4  
  EXEC dbo.usp_t1 3, 4  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify the rows 3 and 4 were inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
  -- catch the arithmetic overflow error  
  BEGIN TRY  
    EXEC dbo.usp_t1 5, 4444444444444  
  END TRY  
  BEGIN CATCH  
    PRINT N'Error occurred: ' + error_message()  
  END CATCH  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify rows 3 and 4 are still in the table, and row 5 has not been inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
COMMIT  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 and 4 has been committed  
SELECT c1 FROM dbo.t1  
ORDER BY c1  
GO  
```  
  
 <span data-ttu-id="f4e20-124">記憶體最佳化資料表特有的以下錯誤訊息會毀滅交易。</span><span class="sxs-lookup"><span data-stu-id="f4e20-124">The following error messages specific to memory-optimized tables are transaction dooming.</span></span> <span data-ttu-id="f4e20-125">如果發生在不可部分完成的區塊範圍內，將會造成交易中止：10772、41301、41302、41305、41325、41332 和 41333。</span><span class="sxs-lookup"><span data-stu-id="f4e20-125">If they occur in the scope of an atomic block, they will cause the transaction to abort: 10772, 41301, 41302, 41305, 41325, 41332, and 41333.</span></span>  
  
## <a name="session-settings"></a><span data-ttu-id="f4e20-126">工作階段設定</span><span class="sxs-lookup"><span data-stu-id="f4e20-126">Session Settings</span></span>  
 <span data-ttu-id="f4e20-127">當編譯預存程序時，將會修復不可部分完成的區塊內的工作階段設定。</span><span class="sxs-lookup"><span data-stu-id="f4e20-127">The session settings in atomic blocks are fixed when the stored procedure is compiled.</span></span> <span data-ttu-id="f4e20-128">某些設定可以使用 `BEGIN ATOMIC` 來指定，而其他設定則一律固定為相同的值。</span><span class="sxs-lookup"><span data-stu-id="f4e20-128">Some settings can be specified with `BEGIN ATOMIC` while other settings are always fixed to the same value.</span></span>  
  
 <span data-ttu-id="f4e20-129">`BEGIN ATOMIC` 需要以下選項：</span><span class="sxs-lookup"><span data-stu-id="f4e20-129">The following options are required with `BEGIN ATOMIC`:</span></span>  
  
|<span data-ttu-id="f4e20-130">必要設定</span><span class="sxs-lookup"><span data-stu-id="f4e20-130">Required Setting</span></span>|<span data-ttu-id="f4e20-131">描述</span><span class="sxs-lookup"><span data-stu-id="f4e20-131">Description</span></span>|  
|----------------------|-----------------|  
|`TRANSACTION ISOLATION LEVEL`|<span data-ttu-id="f4e20-132">支援的值為 `SNAPSHOT`、`REPEATABLEREAD` 和 `SERIALIZABLE`。</span><span class="sxs-lookup"><span data-stu-id="f4e20-132">Supported values are `SNAPSHOT`, `REPEATABLEREAD`, and `SERIALIZABLE`.</span></span>|  
|`LANGUAGE`|<span data-ttu-id="f4e20-133">判斷日期和時間格式及系統訊息。</span><span class="sxs-lookup"><span data-stu-id="f4e20-133">Determines date and time formats and system messages.</span></span> <span data-ttu-id="f4e20-134">[sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) 中的所有語言和別名都受到支援。</span><span class="sxs-lookup"><span data-stu-id="f4e20-134">All languages and aliases in [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) are supported.</span></span>|  
  
 <span data-ttu-id="f4e20-135">以下是選擇性設定：</span><span class="sxs-lookup"><span data-stu-id="f4e20-135">The following settings are optional:</span></span>  
  
|<span data-ttu-id="f4e20-136">選擇性設定</span><span class="sxs-lookup"><span data-stu-id="f4e20-136">Optional Setting</span></span>|<span data-ttu-id="f4e20-137">描述</span><span class="sxs-lookup"><span data-stu-id="f4e20-137">Description</span></span>|  
|----------------------|-----------------|  
|`DATEFORMAT`|<span data-ttu-id="f4e20-138">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期格式都受到支援。</span><span class="sxs-lookup"><span data-stu-id="f4e20-138">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date formats are supported.</span></span> <span data-ttu-id="f4e20-139">當指定時，`DATEFORMAT` 會覆寫與 `LANGUAGE` 相關聯的預設日期格式。</span><span class="sxs-lookup"><span data-stu-id="f4e20-139">When specified, `DATEFORMAT` overrides the default date format associated with `LANGUAGE`.</span></span>|  
|`DATEFIRST`|<span data-ttu-id="f4e20-140">當指定時，`DATEFIRST` 會覆寫與 `LANGUAGE` 相關聯的預設值。</span><span class="sxs-lookup"><span data-stu-id="f4e20-140">When specified, `DATEFIRST` overrides the default associated with `LANGUAGE`.</span></span>|  
|`DELAYED_DURABILITY`|<span data-ttu-id="f4e20-141">支援的值為 `OFF` 和 `ON`。</span><span class="sxs-lookup"><span data-stu-id="f4e20-141">Supported values are `OFF` and `ON`.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f4e20-142">交易認可可能是完全持久、預設值或延遲的持久。如需詳細資訊，請參閱[控制交易持久性](../logs/control-transaction-durability.md)。</span><span class="sxs-lookup"><span data-stu-id="f4e20-142">transaction commits can be either fully durable, the default, or delayed durable.For more information, see [Control Transaction Durability](../logs/control-transaction-durability.md).</span></span>|  
  
 <span data-ttu-id="f4e20-143">對於所有原生編譯預存程序中所有不可部分完成的區塊，下列 SET 選項都有相同的系統預設值：</span><span class="sxs-lookup"><span data-stu-id="f4e20-143">The following SET options have the same system default value for all atomic blocks in all natively compiled stored procedures:</span></span>  
  
|<span data-ttu-id="f4e20-144">Set 選項</span><span class="sxs-lookup"><span data-stu-id="f4e20-144">Set Option</span></span>|<span data-ttu-id="f4e20-145">不可部分完成的區塊的系統預設值</span><span class="sxs-lookup"><span data-stu-id="f4e20-145">System Default for Atomic Blocks</span></span>|  
|----------------|--------------------------------------|  
|<span data-ttu-id="f4e20-146">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="f4e20-146">ANSI_NULLS</span></span>|<span data-ttu-id="f4e20-147">開啟</span><span class="sxs-lookup"><span data-stu-id="f4e20-147">ON</span></span>|  
|<span data-ttu-id="f4e20-148">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="f4e20-148">ANSI_PADDING</span></span>|<span data-ttu-id="f4e20-149">開啟</span><span class="sxs-lookup"><span data-stu-id="f4e20-149">ON</span></span>|  
|<span data-ttu-id="f4e20-150">ANSI_WARNING</span><span class="sxs-lookup"><span data-stu-id="f4e20-150">ANSI_WARNING</span></span>|<span data-ttu-id="f4e20-151">開啟</span><span class="sxs-lookup"><span data-stu-id="f4e20-151">ON</span></span>|  
|<span data-ttu-id="f4e20-152">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="f4e20-152">ARITHABORT</span></span>|<span data-ttu-id="f4e20-153">開啟</span><span class="sxs-lookup"><span data-stu-id="f4e20-153">ON</span></span>|  
|<span data-ttu-id="f4e20-154">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="f4e20-154">ARITHIGNORE</span></span>|<span data-ttu-id="f4e20-155">OFF</span><span class="sxs-lookup"><span data-stu-id="f4e20-155">OFF</span></span>|  
|<span data-ttu-id="f4e20-156">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="f4e20-156">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="f4e20-157">開啟</span><span class="sxs-lookup"><span data-stu-id="f4e20-157">ON</span></span>|  
|<span data-ttu-id="f4e20-158">IDENTITY_INSERT</span><span class="sxs-lookup"><span data-stu-id="f4e20-158">IDENTITY_INSERT</span></span>|<span data-ttu-id="f4e20-159">OFF</span><span class="sxs-lookup"><span data-stu-id="f4e20-159">OFF</span></span>|  
|<span data-ttu-id="f4e20-160">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="f4e20-160">NOCOUNT</span></span>|<span data-ttu-id="f4e20-161">開啟</span><span class="sxs-lookup"><span data-stu-id="f4e20-161">ON</span></span>|  
|<span data-ttu-id="f4e20-162">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="f4e20-162">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="f4e20-163">OFF</span><span class="sxs-lookup"><span data-stu-id="f4e20-163">OFF</span></span>|  
|<span data-ttu-id="f4e20-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="f4e20-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="f4e20-165">開啟</span><span class="sxs-lookup"><span data-stu-id="f4e20-165">ON</span></span>|  
|<span data-ttu-id="f4e20-166">ROWCOUNT</span><span class="sxs-lookup"><span data-stu-id="f4e20-166">ROWCOUNT</span></span>|<span data-ttu-id="f4e20-167">0</span><span class="sxs-lookup"><span data-stu-id="f4e20-167">0</span></span>|  
|<span data-ttu-id="f4e20-168">TEXTSIZE</span><span class="sxs-lookup"><span data-stu-id="f4e20-168">TEXTSIZE</span></span>|<span data-ttu-id="f4e20-169">0</span><span class="sxs-lookup"><span data-stu-id="f4e20-169">0</span></span>|  
|<span data-ttu-id="f4e20-170">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="f4e20-170">XACT_ABORT</span></span>|<span data-ttu-id="f4e20-171">OFF</span><span class="sxs-lookup"><span data-stu-id="f4e20-171">OFF</span></span><br /><br /> <span data-ttu-id="f4e20-172">未捕捉到的例外狀況會造成不可部分完成的區塊回復，但是並不會造成交易中止，除非錯誤會毀滅交易。</span><span class="sxs-lookup"><span data-stu-id="f4e20-172">Uncaught exceptions cause the atomic block to roll back, but not cause the transaction to abort unless the error is transaction dooming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4e20-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4e20-173">See Also</span></span>  
 [<span data-ttu-id="f4e20-174">原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="f4e20-174">Natively Compiled Stored Procedures</span></span>](natively-compiled-stored-procedures.md)  
  
  
