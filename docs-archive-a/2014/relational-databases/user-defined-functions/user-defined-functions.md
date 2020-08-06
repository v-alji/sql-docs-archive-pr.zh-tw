---
title: 使用者定義的函式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], components
- user-defined functions [SQL Server], about user-defined functions
ms.assetid: d7ddafab-f5a6-44b0-81d5-ba96425aada4
author: rothja
ms.author: jroth
ms.openlocfilehash: c7e4b1a77f2fe5a13e21d8b3fe59e37931669b30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584336"
---
# <a name="user-defined-functions"></a><span data-ttu-id="d4c1c-102">使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="d4c1c-102">User-Defined Functions</span></span>
  <span data-ttu-id="d4c1c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者定義函數與程式語言函數類似，是可接受參數、執行動作 (如複雜計算) 以及傳回該動作所得值的常式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-103">Like functions in programming languages, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined functions are routines that accept parameters, perform an action, such as a complex calculation, and return the result of that action as a value.</span></span> <span data-ttu-id="d4c1c-104">傳回值可以是單一純量值或結果集。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-104">The return value can either be a single scalar value or a result set.</span></span>  
  
 <span data-ttu-id="d4c1c-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="d4c1c-105">**In This Topic**</span></span>  
  
 [<span data-ttu-id="d4c1c-106">使用者自訂函數的好處</span><span class="sxs-lookup"><span data-stu-id="d4c1c-106">User-defined Function Benefits</span></span>](#Benefits)  
  
 [<span data-ttu-id="d4c1c-107">函數類型</span><span class="sxs-lookup"><span data-stu-id="d4c1c-107">Types of Functions</span></span>](#FunctionTypes)  
  
 [<span data-ttu-id="d4c1c-108">指導方針</span><span class="sxs-lookup"><span data-stu-id="d4c1c-108">Guidelines</span></span>](#Guidelines)  
  
 [<span data-ttu-id="d4c1c-109">函數中有效的語句</span><span class="sxs-lookup"><span data-stu-id="d4c1c-109">Valid Statements in a Function</span></span>](#ValidStatements)  
  
 [<span data-ttu-id="d4c1c-110">結構描述繫結函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-110">Schema Bound Functions</span></span>](#SchemaBound)  
  
 [<span data-ttu-id="d4c1c-111">指定參數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-111">Specifying Parameters</span></span>](#Parameters)  
  
 [<span data-ttu-id="d4c1c-112">相關工作</span><span class="sxs-lookup"><span data-stu-id="d4c1c-112">Related Tasks</span></span>](#Tasks)  
  
##  <a name="user-defined-function-benefits"></a><a name="Benefits"></a><span data-ttu-id="d4c1c-113">使用者定義函數的優點</span><span class="sxs-lookup"><span data-stu-id="d4c1c-113">User-defined Function Benefits</span></span>  
 <span data-ttu-id="d4c1c-114">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用者定義函數的好處如下：</span><span class="sxs-lookup"><span data-stu-id="d4c1c-114">The benefits of using user-defined functions in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are:</span></span>  
  
-   <span data-ttu-id="d4c1c-115">可進行模組化的程式撰寫。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-115">They allow modular programming.</span></span>  
  
     <span data-ttu-id="d4c1c-116">只需建立函數一次，將它儲存在資料庫中，就可以在程式中無限次地隨意呼叫。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-116">You can create the function once, store it in the database, and call it any number of times in your program.</span></span> <span data-ttu-id="d4c1c-117">使用者自訂函數不需透過原始程式碼即可修改 。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-117">User-defined functions can be modified independently of the program source code.</span></span>  
  
-   <span data-ttu-id="d4c1c-118">可加快執行速度。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-118">They allow faster execution.</span></span>  
  
     <span data-ttu-id="d4c1c-119">如同預存程序，[!INCLUDE[tsql](../../includes/tsql-md.md)]  使用者自訂函數可藉由針對重複執行來快取以及重複使用計畫，來降低 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼的編譯成本。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-119">Similar to stored procedures, [!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions reduce the compilation cost of [!INCLUDE[tsql](../../includes/tsql-md.md)] code by caching the plans and reusing them for repeated executions.</span></span> <span data-ttu-id="d4c1c-120">這表示，每次使用時，使用者自訂函數不需要重新剖析和最佳化，所以執行時間可以更快。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-120">This means the user-defined function does not need to be reparsed and reoptimized with each use resulting in much faster execution times.</span></span>  
  
     <span data-ttu-id="d4c1c-121">與 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函數相比，CLR 函數在計算工作、字串處理與商務邏輯等方面提供更顯著的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-121">CLR functions offer significant performance advantage over [!INCLUDE[tsql](../../includes/tsql-md.md)] functions for computational tasks, string manipulation, and business logic.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="d4c1c-122">函數更適用於經常需要存取資料的作業。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-122">functions are better suited for data-access intensive logic.</span></span>  
  
-   <span data-ttu-id="d4c1c-123">可降低網路傳輸量。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-123">They can reduce network traffic.</span></span>  
  
     <span data-ttu-id="d4c1c-124">對於無法以單一純量運算式表示的作業 (例如，根據某些複雜條件約束來篩選資料)，可以利用函數來表示。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-124">An operation that filters data based on some complex constraint that cannot be expressed in a single scalar expression can be expressed as a function.</span></span> <span data-ttu-id="d4c1c-125">接著，您可以在 WHERE 子句中叫用函數，減少傳送到用戶端的資料列數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-125">The function can then invoked in the WHERE clause to reduce the number or rows sent to the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4c1c-126">查詢中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 使用者定義函數只能在單一執行緒上執行 (序列執行計畫)。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] user-defined functions in queries can only be executed on a single thread (serial execution plan).</span></span>  
  
##  <a name="types-of-functions"></a><a name="FunctionTypes"></a><span data-ttu-id="d4c1c-127">函數類型</span><span class="sxs-lookup"><span data-stu-id="d4c1c-127">Types of Functions</span></span>  
 <span data-ttu-id="d4c1c-128">純量函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-128">Scalar Function</span></span>  
 <span data-ttu-id="d4c1c-129">使用者定義純量函數會傳回在 RETURNS 子句中所定義之類型的單一資料值。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-129">User-defined scalar functions return a single data value of the type defined in the RETURNS clause.</span></span> <span data-ttu-id="d4c1c-130">內嵌純量函數並沒有函數主體；純量值為單一陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-130">For an inline scalar function, there is no function body; the scalar value is the result of a single statement.</span></span> <span data-ttu-id="d4c1c-131">若是多重陳述式純量函數，則定義於 BEGIN...END 區塊中的函數主體，會包含傳回單一值的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式系列。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-131">For a multistatement scalar function, the function body, defined in a BEGIN...END block, contains a series of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that return the single value.</span></span> <span data-ttu-id="d4c1c-132">傳回類型可以是任何資料類型，但 `text`、`ntext`、`image`、`cursor` 及 `timestamp` 除外。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-132">The return type can be any data type except `text`, `ntext`, `image`, `cursor`, and `timestamp`.</span></span>  
  
 <span data-ttu-id="d4c1c-133">資料表值函式</span><span class="sxs-lookup"><span data-stu-id="d4c1c-133">Table-Valued Functions</span></span>  
 <span data-ttu-id="d4c1c-134">使用者定義的資料表值函式會傳回 `table` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-134">User-defined table-valued functions return a `table` data type.</span></span> <span data-ttu-id="d4c1c-135">若是內嵌資料表值函式，則不會有函式主體；資料表會是單一 SELECT 陳述式的結果集。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-135">For an inline table-valued function, there is no function body; the table is the result set of a single SELECT statement.</span></span>  
  
 <span data-ttu-id="d4c1c-136">系統函式</span><span class="sxs-lookup"><span data-stu-id="d4c1c-136">System Functions</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="d4c1c-137">提供許多可用以執行各種作業的系統函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-137">provides many system functions that you can use to perform a variety of operations.</span></span> <span data-ttu-id="d4c1c-138">這些函數不能修改。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-138">They cannot be modified.</span></span> <span data-ttu-id="d4c1c-139">如需詳細資訊，請參閱[內建函數 &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions)、[系統預存函式 &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/system-functions-for-transact-sql)，和[動態管理檢視與函數 &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views)。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-139">For more information, see [Built-in Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/functions), [System Stored Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/system-functions-for-transact-sql), and [Dynamic Management Views and Functions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/system-dynamic-management-views).</span></span>  
  
##  <a name="guidelines"></a><a name="Guidelines"></a> <span data-ttu-id="d4c1c-140">指導方針</span><span class="sxs-lookup"><span data-stu-id="d4c1c-140">Guidelines</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="d4c1c-141">造成陳述式取消並且以模組中下一個陳述式繼續 (例如觸發程序或預存程序) 的錯誤會在函式內部以不同方式處理。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-141">errors that cause a statement to be canceled and continue with the next statement in the module (such as triggers or stored procedures) are treated differently inside a function.</span></span> <span data-ttu-id="d4c1c-142">在函數中，這樣的錯誤會造成函數停止執行。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-142">In functions, such errors cause the execution of the function to stop.</span></span> <span data-ttu-id="d4c1c-143">進而導致叫用該函數的陳述式取消。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-143">This in turn causes the statement that invoked the function to be canceled.</span></span>  
  
 <span data-ttu-id="d4c1c-144">BEGIN...END 區塊中的陳述式不能有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-144">The statements in a BEGIN...END block cannot have any side effects.</span></span> <span data-ttu-id="d4c1c-145">函數副作用是在函數的範圍外對資源狀態所做的任何永久變更，例如修改資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-145">Function side effects are any permanent changes to the state of a resource that has a scope outside the function such as a modification to a database table.</span></span> <span data-ttu-id="d4c1c-146">在函數中陳述式只能變更函數的區域性物件，例如本機資料指標或變數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-146">The only changes that can be made by the statements in the function are changes to objects local to the function, such as local cursors or variables.</span></span> <span data-ttu-id="d4c1c-147">在函數中不得執行的動作包括修改資料庫資料表、對函數的非本機資料指標進行運算、傳送電子郵件、試圖修改目錄，以及產生傳回給使用者的結果集。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-147">Modifications to database tables, operations on cursors that are not local to the function, sending e-mail, attempting a catalog modification, and generating a result set that is returned to the user are examples of actions that cannot be performed in a function.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4c1c-148">如果 CREATE FUNCTION 陳述式會對資源產生在發出 CREATE FUNCTION 陳述式時不存在的副作用，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會執行該陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-148">If a CREATE FUNCTION statement produces side effects against resources that do not exist when the CREATE FUNCTION statement is issued, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes the statement.</span></span> <span data-ttu-id="d4c1c-149">不過， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不會執行叫用的函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-149">However, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not execute the function when it is invoked.</span></span>  
  
 <span data-ttu-id="d4c1c-150">查詢中指定的函數真正執行的次數，會因最佳化工具建立的執行計畫而有不同。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-150">The number of times that a function specified in a query is actually executed can vary between execution plans built by the optimizer.</span></span> <span data-ttu-id="d4c1c-151">WHERE 子句中的子查詢所叫用的函數就是一個例子。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-151">An example is a function invoked by a subquery in a WHERE clause.</span></span> <span data-ttu-id="d4c1c-152">子查詢及其函數的執行次數，會因最佳化工具選擇的存取路徑而有不同。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-152">The number of times the subquery and its function is executed can vary with different access paths chosen by the optimizer.</span></span>  
  
##  <a name="valid-statements-in-a-function"></a><a name="ValidStatements"></a><span data-ttu-id="d4c1c-153">函數中有效的語句</span><span class="sxs-lookup"><span data-stu-id="d4c1c-153">Valid Statements in a Function</span></span>  
 <span data-ttu-id="d4c1c-154">函數中有效的陳述式類型包括：</span><span class="sxs-lookup"><span data-stu-id="d4c1c-154">The types of statements that are valid in a function include:</span></span>  
  
-   <span data-ttu-id="d4c1c-155">DECLARE 陳述式，可用來定義對函數而言為本機的資料變數與資料指標。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-155">DECLARE statements can be used to define data variables and cursors that are local to the function.</span></span>  
  
-   <span data-ttu-id="d4c1c-156">指派值給對函數而言為本機的物件，例如使用 SET 指派值給純量及資料表本機變數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-156">Assignments of values to objects local to the function, such as using SET to assign values to scalar and table local variables.</span></span>  
  
-   <span data-ttu-id="d4c1c-157">參考在函數中宣告、開啟、關閉及取消配置的本機資料指標之資料指標運算。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-157">Cursor operations that reference local cursors that are declared, opened, closed, and deallocated in the function.</span></span> <span data-ttu-id="d4c1c-158">不允許將資料傳回用戶端的 FETCH 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-158">FETCH statements that return data to the client are not allowed.</span></span> <span data-ttu-id="d4c1c-159">只允許使用 INTO 子句指派值給本機變數的 FETCH 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-159">Only FETCH statements that assign values to local variables using the INTO clause are allowed.</span></span>  
  
-   <span data-ttu-id="d4c1c-160">除了 TRY...CATCH 陳述式以外的流程控制陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-160">Control-of-flow statements except TRY...CATCH statements.</span></span>  
  
-   <span data-ttu-id="d4c1c-161">含有選取清單及指派值給對函數而言為本機變數之運算式的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-161">SELECT statements containing select lists with expressions that assign values to variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="d4c1c-162">修改對函數而言為本機之資料表變數的 UPDATE、INSERT 及 DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-162">UPDATE, INSERT, and DELETE statements modifying table variables that are local to the function.</span></span>  
  
-   <span data-ttu-id="d4c1c-163">呼叫擴充預存程序的 EXECUTE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-163">EXECUTE statements calling an extended stored procedure.</span></span>  
  
### <a name="built-in-system-functions"></a><span data-ttu-id="d4c1c-164">內建系統函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-164">Built-in System Functions</span></span>  
 <span data-ttu-id="d4c1c-165">下列非決定性內建函數可用於 Transact-SQL 使用者定義函數中。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-165">The following nondeterministic built-in functions can be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d4c1c-166">CURRENT_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="d4c1c-166">CURRENT_TIMESTAMP</span></span>|<span data-ttu-id="d4c1c-167">@@MAX_CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="d4c1c-167">@@MAX_CONNECTIONS</span></span>|  
|<span data-ttu-id="d4c1c-168">GET_TRANSMISSION_STATUS</span><span class="sxs-lookup"><span data-stu-id="d4c1c-168">GET_TRANSMISSION_STATUS</span></span>|<span data-ttu-id="d4c1c-169">@@PACK_RECEIVED</span><span class="sxs-lookup"><span data-stu-id="d4c1c-169">@@PACK_RECEIVED</span></span>|  
|<span data-ttu-id="d4c1c-170">GETDATE</span><span class="sxs-lookup"><span data-stu-id="d4c1c-170">GETDATE</span></span>|<span data-ttu-id="d4c1c-171">@@PACK_SENT</span><span class="sxs-lookup"><span data-stu-id="d4c1c-171">@@PACK_SENT</span></span>|  
|<span data-ttu-id="d4c1c-172">GETUTCDATE</span><span class="sxs-lookup"><span data-stu-id="d4c1c-172">GETUTCDATE</span></span>|<span data-ttu-id="d4c1c-173">@@PACKET_ERRORS</span><span class="sxs-lookup"><span data-stu-id="d4c1c-173">@@PACKET_ERRORS</span></span>|  
|<span data-ttu-id="d4c1c-174">@@CONNECTIONS</span><span class="sxs-lookup"><span data-stu-id="d4c1c-174">@@CONNECTIONS</span></span>|<span data-ttu-id="d4c1c-175">@@TIMETICKS</span><span class="sxs-lookup"><span data-stu-id="d4c1c-175">@@TIMETICKS</span></span>|  
|<span data-ttu-id="d4c1c-176">@@CPU_BUSY</span><span class="sxs-lookup"><span data-stu-id="d4c1c-176">@@CPU_BUSY</span></span>|<span data-ttu-id="d4c1c-177">@@TOTAL_ERRORS</span><span class="sxs-lookup"><span data-stu-id="d4c1c-177">@@TOTAL_ERRORS</span></span>|  
|<span data-ttu-id="d4c1c-178">@@DBTS</span><span class="sxs-lookup"><span data-stu-id="d4c1c-178">@@DBTS</span></span>|<span data-ttu-id="d4c1c-179">@@TOTAL_READ</span><span class="sxs-lookup"><span data-stu-id="d4c1c-179">@@TOTAL_READ</span></span>|  
|<span data-ttu-id="d4c1c-180">@@IDLE</span><span class="sxs-lookup"><span data-stu-id="d4c1c-180">@@IDLE</span></span>|<span data-ttu-id="d4c1c-181">@@TOTAL_WRITE</span><span class="sxs-lookup"><span data-stu-id="d4c1c-181">@@TOTAL_WRITE</span></span>|  
|<span data-ttu-id="d4c1c-182">@@IO_BUSY</span><span class="sxs-lookup"><span data-stu-id="d4c1c-182">@@IO_BUSY</span></span>||  
  
 <span data-ttu-id="d4c1c-183">下列非決定性內建函數不得用於 Transact-SQL 的使用者定義函數中。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-183">The following nondeterministic built-in functions cannot be used in Transact-SQL user-defined functions.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d4c1c-184">NEWID</span><span class="sxs-lookup"><span data-stu-id="d4c1c-184">NEWID</span></span>|<span data-ttu-id="d4c1c-185">RAND</span><span class="sxs-lookup"><span data-stu-id="d4c1c-185">RAND</span></span>|  
|<span data-ttu-id="d4c1c-186">NEWSEQUENTIALID</span><span class="sxs-lookup"><span data-stu-id="d4c1c-186">NEWSEQUENTIALID</span></span>|<span data-ttu-id="d4c1c-187">TEXTPTR</span><span class="sxs-lookup"><span data-stu-id="d4c1c-187">TEXTPTR</span></span>|  
  
 <span data-ttu-id="d4c1c-188">如需決定性與非決定性內建系統函數的清單，請參閱[決定性與非決定性函數](../user-defined-functions/deterministic-and-nondeterministic-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-188">For a list of deterministic and nondeterministic built-in system functions, see [Deterministic and Nondeterministic Functions](../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span>  
  
##  <a name="schema-bound-functions"></a><a name="SchemaBound"></a><span data-ttu-id="d4c1c-189">架構系結函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-189">Schema-Bound Functions</span></span>  
 <span data-ttu-id="d4c1c-190">CREATE FUNCTION 支援 SCHEMABINDING 子句，它可將函數與它參考的任何物件之結構描述繫結在一起，例如資料表、檢視及其他使用者自訂函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-190">CREATE FUNCTION supports a SCHEMABINDING clause that binds the function to the schema of any objects it references, such as tables, views, and other user-defined functions.</span></span> <span data-ttu-id="d4c1c-191">嘗試更改或卸除任何被結構描述繫結函數所參考的物件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-191">An attempt to alter or drop any object referenced by a schema-bound function fails.</span></span>  
  
 <span data-ttu-id="d4c1c-192">要在 CREATE FUNCTION 中指定 SCHEMABINDING，必須先滿足下列條件：</span><span class="sxs-lookup"><span data-stu-id="d4c1c-192">These conditions must be met before you can specify SCHEMABINDING in CREATE FUNCTION:</span></span>  
  
-   <span data-ttu-id="d4c1c-193">函數所參考的所有檢視及使用者自訂函數，都必須是結構描述繫結的。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-193">All views and user-defined functions referenced by the function must be schema-bound.</span></span>  
  
-   <span data-ttu-id="d4c1c-194">函數所參考的所有物件，都必須與函數位於相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-194">All objects referenced by the function must be in the same database as the function.</span></span> <span data-ttu-id="d4c1c-195">這些物件必須利用單一部份或兩部份名稱來加以參考。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-195">The objects must be referenced using either one-part or two-part names.</span></span>  
  
-   <span data-ttu-id="d4c1c-196">您對於函數中參考的所有物件 (資料表、檢視及使用者自訂函數) 必須擁有 REFERENCES 權限。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-196">You must have REFERENCES permission on all objects (tables, views, and user-defined functions) referenced in the function.</span></span>  
  
 <span data-ttu-id="d4c1c-197">您可以利用 ALTER FUNCTION 來移除結構描述繫結。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-197">You can use ALTER FUNCTION to remove the schema binding.</span></span> <span data-ttu-id="d4c1c-198">ALTER FUNCTION 陳述式不用指定 WITH SCHEMABINDING 即可重新定義函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-198">The ALTER FUNCTION statement should redefine the function without specifying WITH SCHEMABINDING.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="d4c1c-199">指定參數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-199">Specifying Parameters</span></span>  
 <span data-ttu-id="d4c1c-200">使用者自訂函數會使用零或多個輸入參數，並會傳回純量值或資料表。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-200">A user-defined function takes zero or more input parameters and returns either a scalar value or a table.</span></span> <span data-ttu-id="d4c1c-201">每一函數最多可以有 1024 個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-201">A function can have a maximum of 1024 input parameters.</span></span> <span data-ttu-id="d4c1c-202">若函數的參數有預設值，在呼叫函數以取得預設值時必須指定 DEFAULT 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-202">When a parameter of the function has a default value, the keyword DEFAULT must be specified when calling the function to get the default value.</span></span> <span data-ttu-id="d4c1c-203">此一行為不同於使用者自訂預存程序中有預設值的參數，在這些預存程序中省略參數亦意謂著省略預設值。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-203">This behavior is different from parameters with default values in user-defined stored procedures in which omitting the parameter also implies the default value.</span></span> <span data-ttu-id="d4c1c-204">使用者自訂函數不支援輸出參數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-204">User-defined functions do not support output parameters.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="d4c1c-205">相關工作</span><span class="sxs-lookup"><span data-stu-id="d4c1c-205">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d4c1c-206">**工作描述**</span><span class="sxs-lookup"><span data-stu-id="d4c1c-206">**Task Description**</span></span>|<span data-ttu-id="d4c1c-207">**主題**</span><span class="sxs-lookup"><span data-stu-id="d4c1c-207">**Topic**</span></span>|  
|<span data-ttu-id="d4c1c-208">描述如何建立 Transact-SQL 使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-208">Describes how to create a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="d4c1c-209">建立使用者定義函式 &#40;資料庫引擎&#41;</span><span class="sxs-lookup"><span data-stu-id="d4c1c-209">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)|  
|<span data-ttu-id="d4c1c-210">描述如何建立 CLR 函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-210">Describes how create a CLR function.</span></span>|[<span data-ttu-id="d4c1c-211">建立 CLR 函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-211">Create CLR Functions</span></span>](../user-defined-functions/create-clr-functions.md)|  
|<span data-ttu-id="d4c1c-212">描述如何建立使用者定義的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-212">Describes how to create a user-defined aggregate function</span></span>|[<span data-ttu-id="d4c1c-213">建立使用者定義彙總</span><span class="sxs-lookup"><span data-stu-id="d4c1c-213">Create User-defined Aggregates</span></span>](../user-defined-functions/create-user-defined-aggregates.md)|  
|<span data-ttu-id="d4c1c-214">描述如何修改 Transact-SQL 使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-214">Describes how to modify a Transact-SQL user-defined function.</span></span>|[<span data-ttu-id="d4c1c-215">修改使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-215">Modify User-defined Functions</span></span>](../user-defined-functions/user-defined-functions.md)|  
|<span data-ttu-id="d4c1c-216">描述如何刪除使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-216">Describes how to delete a user-defined function.</span></span>|[<span data-ttu-id="d4c1c-217">刪除使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-217">Delete User-defined Functions</span></span>](../user-defined-functions/delete-user-defined-functions.md)|  
|<span data-ttu-id="d4c1c-218">描述如何執行使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-218">Describes how to execute a user-defined function.</span></span>|[<span data-ttu-id="d4c1c-219">執行使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-219">Execute User-defined Functions</span></span>](../user-defined-functions/execute-user-defined-functions.md)|  
|<span data-ttu-id="d4c1c-220">描述如何重新命名使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-220">Describes how to rename a user-defined function</span></span>|[<span data-ttu-id="d4c1c-221">重新命名使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-221">Rename User-defined Functions</span></span>](../user-defined-functions/rename-user-defined-functions.md)|  
|<span data-ttu-id="d4c1c-222">描述如何檢視使用者定義函數的定義。</span><span class="sxs-lookup"><span data-stu-id="d4c1c-222">Describes how to view the definition of a user-defined function.</span></span>|[<span data-ttu-id="d4c1c-223">檢視使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="d4c1c-223">View User-defined Functions</span></span>](view-user-defined-functions.md)|  
  
  
