---
title: 執行預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.executeprocedure.f1
- sql12.swb.executeprocedure.general.f1
helpviewer_keywords:
- stored procedures [SQL Server], parameters
- extended stored procedures [SQL Server], executing
- system stored procedures [SQL Server], executing
- stored procedures [SQL Server], executing
- user-defined stored procedures [SQL Server]
ms.assetid: a0b1337d-2059-4872-8c62-3f967d8b170f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c679ba7af3ac9f60d312b33c0346e50687387476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599402"
---
# <a name="execute-a-stored-procedure"></a><span data-ttu-id="1160a-102">執行預存程序</span><span class="sxs-lookup"><span data-stu-id="1160a-102">Execute a Stored Procedure</span></span>
  <span data-ttu-id="1160a-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 執行 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-103">This topic describes how to execute a stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1160a-104">有兩種不同的方法可執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-104">There are two different ways to execute a stored procedure.</span></span> <span data-ttu-id="1160a-105">第一種是最常用的方法，可讓應用程式或使用者呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-105">The first and most common approach is for an application or user to call the procedure.</span></span> <span data-ttu-id="1160a-106">第二種方法是設定讓程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體啟動時自動執行。</span><span class="sxs-lookup"><span data-stu-id="1160a-106">The second approach is to set the procedure to run automatically when an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts.</span></span> <span data-ttu-id="1160a-107">當應用程式或使用者呼叫程序時， [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE 或 EXEC 關鍵字會在呼叫中明確陳述。</span><span class="sxs-lookup"><span data-stu-id="1160a-107">When a procedure is called by an application or user, the [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE or EXEC keyword is explicitly stated in the call.</span></span> <span data-ttu-id="1160a-108">如果程序是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次中的第一個陳述式，則呼叫和執行程序時也可以不用關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1160a-108">Alternatively, the procedure can be called and executed without the keyword if the procedure is the first statement in the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span>  
  
 <span data-ttu-id="1160a-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1160a-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1160a-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1160a-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1160a-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="1160a-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1160a-112">建議</span><span class="sxs-lookup"><span data-stu-id="1160a-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1160a-113">安全性</span><span class="sxs-lookup"><span data-stu-id="1160a-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1160a-114">**若要執行預存程序，使用：**</span><span class="sxs-lookup"><span data-stu-id="1160a-114">**To execute a stored procedure, using:**</span></span>  
  
     [<span data-ttu-id="1160a-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1160a-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1160a-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1160a-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1160a-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="1160a-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1160a-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="1160a-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1160a-119">比對系統程序名稱時，會使用呼叫資料庫定序。</span><span class="sxs-lookup"><span data-stu-id="1160a-119">The calling database collation is used when matching system procedure names.</span></span> <span data-ttu-id="1160a-120">因此，您務必在程序呼叫中使用大小寫完全相符的系統程序名稱。</span><span class="sxs-lookup"><span data-stu-id="1160a-120">Therefore, always use the exact case of system procedure names in procedure calls.</span></span> <span data-ttu-id="1160a-121">例如，如果此程式碼是在有區分大小寫定序的資料庫內容中執行，就會失敗：</span><span class="sxs-lookup"><span data-stu-id="1160a-121">For example, this code will fail if it is executed in the context of a database that has a case-sensitive collation:</span></span>  
  
    ```sql  
    EXEC SP_heLP; -- Will fail to resolve because SP_heLP does not equal sp_help  
    ```  
  
     <span data-ttu-id="1160a-122">若要顯示完全相符的系統程序名稱，請查詢 [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) 和 [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="1160a-122">To display the exact system procedure names, query the [sys.system_objects](/sql/relational-databases/system-catalog-views/sys-system-objects-transact-sql) and [sys.system_parameters](/sql/relational-databases/system-catalog-views/sys-system-parameters-transact-sql) catalog views.</span></span>  
  
-   <span data-ttu-id="1160a-123">如果使用者定義程序與系統程序的名稱相同，則使用者定義程序可能永遠不會執行。</span><span class="sxs-lookup"><span data-stu-id="1160a-123">If a user-defined procedure has the same name as a system procedure, the user-defined procedure might not ever execute.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1160a-124">建議</span><span class="sxs-lookup"><span data-stu-id="1160a-124">Recommendations</span></span>  
  
-   <span data-ttu-id="1160a-125">執行系統預存程序</span><span class="sxs-lookup"><span data-stu-id="1160a-125">Executing System Stored Procedures</span></span>  
  
     <span data-ttu-id="1160a-126">系統程序會以 **sp_** 前置詞開頭。</span><span class="sxs-lookup"><span data-stu-id="1160a-126">System procedures begin with the prefix **sp_**.</span></span> <span data-ttu-id="1160a-127">由於這些程序會以邏輯的方式出現在所有使用者和系統定義的資料庫中，因此可以從任何資料庫中執行，而不必完整限定程序名稱。</span><span class="sxs-lookup"><span data-stu-id="1160a-127">Because they logically appear in all user- and system- defined databases, they can be executed from any database without having to fully quality the procedure name.</span></span> <span data-ttu-id="1160a-128">不過，我們建議您使用結構描述將所有系統程序名稱限定為 **sys** 結構描述名稱，以避免名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="1160a-128">However, we recommend schema-qualifying all system procedure names with the **sys** schema name to prevent name conflicts.</span></span> <span data-ttu-id="1160a-129">下列範例示範呼叫系統程序的建議方法。</span><span class="sxs-lookup"><span data-stu-id="1160a-129">The following example demonstrates the recommended method of calling a system procedure.</span></span>  
  
    ```sql  
    EXEC sys.sp_who;  
    ```  
  
-   <span data-ttu-id="1160a-130">執行使用者自訂預存程序</span><span class="sxs-lookup"><span data-stu-id="1160a-130">Executing User-defined Stored Procedures</span></span>  
  
     <span data-ttu-id="1160a-131">當執行使用者定義的程序時，我們建議以結構描述名稱限定程序名稱。</span><span class="sxs-lookup"><span data-stu-id="1160a-131">When executing a user-defined procedure, we recommend qualifying the procedure name with the schema name.</span></span> <span data-ttu-id="1160a-132">這種作法可稍微提升效能，因為 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 不必搜尋多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="1160a-132">This practice gives a small performance boost because the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] does not have to search multiple schemas.</span></span> <span data-ttu-id="1160a-133">如果資料庫在多個結構描述中有相同名稱的程序，它還可以避免執行錯誤的程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-133">It also prevents executing the wrong procedure if a database has procedures with the same name in multiple schemas.</span></span>  
  
     <span data-ttu-id="1160a-134">下列範例示範執行使用者定義程序的建議方法。</span><span class="sxs-lookup"><span data-stu-id="1160a-134">The following example demonstrates the recommended method to execute a user-defined procedure.</span></span> <span data-ttu-id="1160a-135">您會發現程序接受一個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1160a-135">Notice that the procedure accepts one input parameter.</span></span> <span data-ttu-id="1160a-136">如需指定輸入和輸出參數的相關資訊，請參閱 [指定參數](specify-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1160a-136">For information about specifying input and output parameters, see [Specify Parameters](specify-parameters.md).</span></span>  
  
    ```sql  
    USE AdventureWorks2012;  
    GO  
    EXEC dbo.uspGetEmployeeManagers @BusinessEntityID = 50;  
    ```  
  
     <span data-ttu-id="1160a-137">-或-</span><span class="sxs-lookup"><span data-stu-id="1160a-137">-Or-</span></span>  
  
    ```sql  
    EXEC AdventureWorks2012.dbo.uspGetEmployeeManagers 50;  
    GO  
    ```  
  
     <span data-ttu-id="1160a-138">如果指定的是非限定使用者定義程序，則 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 會以下列順序搜尋該程序：</span><span class="sxs-lookup"><span data-stu-id="1160a-138">If a nonqualified user-defined procedure is specified, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] searches for the procedure in the following order:</span></span>  
  
    1.  <span data-ttu-id="1160a-139">目前資料庫的 **sys** 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1160a-139">The **sys** schema of the current database.</span></span>  
  
    2.  <span data-ttu-id="1160a-140">如果在批次或動態 SQL 中執行，則為呼叫端的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="1160a-140">The caller's default schema if it is executed in a batch or in dynamic SQL.</span></span> <span data-ttu-id="1160a-141">或者，如果非限定程序名稱出現在其他程序定義的主體內，則接下來會掃描包含這個其他程序的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1160a-141">Or, if the nonqualified procedure name appears inside the body of another procedure definition, the schema that contains this other procedure is searched next.</span></span>  
  
    3.  <span data-ttu-id="1160a-142">目前資料庫中的 **dbo** 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1160a-142">The **dbo** schema in the current database.</span></span>  
  
-   <span data-ttu-id="1160a-143">自動執行預存程序</span><span class="sxs-lookup"><span data-stu-id="1160a-143">Executing Stored Procedures Automatically</span></span>  
  
     <span data-ttu-id="1160a-144">標記為自動執行的程序會在每次 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動時執行，且 **master** 資料庫會在該啟動處理序期間復原。</span><span class="sxs-lookup"><span data-stu-id="1160a-144">Procedures marked for automatic execution are executed every time [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] starts and the **master** database is recovered during that startup process.</span></span> <span data-ttu-id="1160a-145">設定自動執行程序在執行資料庫維護作業或讓程序做為背景處理序連續執行時相當實用。</span><span class="sxs-lookup"><span data-stu-id="1160a-145">Setting up procedures to execute automatically can be useful for performing database maintenance operations or for having procedures run continuously as background processes.</span></span> <span data-ttu-id="1160a-146">自動執行的另一個用處就是讓程序執行 **tempdb**中的系統或維護工作，如建立全域的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="1160a-146">Another use for automatic execution is to have the procedure perform system or maintenance tasks in **tempdb**, such as creating a global temporary table.</span></span> <span data-ttu-id="1160a-147">這樣可確保在 **啟動期間重新建立** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，這個暫存資料表一定會存在。</span><span class="sxs-lookup"><span data-stu-id="1160a-147">This makes sure that such a temporary table will always exist when **tempdb** is re-created during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
     <span data-ttu-id="1160a-148">自動執行的程序運作時所使用的權限與 **sysadmin** (系統管理員) 固定伺服器角色的成員相同。</span><span class="sxs-lookup"><span data-stu-id="1160a-148">A procedure that is automatically executed operates with the same permissions as members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="1160a-149">程序所產生的任何錯誤訊息都會寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="1160a-149">Any error messages generated by the procedure are written to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log.</span></span>  
  
     <span data-ttu-id="1160a-150">對於您能擁有的啟動程序數量並沒有限制，但請留意每一程序執行時都會佔用掉一個工作者執行緒。</span><span class="sxs-lookup"><span data-stu-id="1160a-150">There is no limit to the number of startup procedures you can have, but be aware that each consumes one worker thread while executing.</span></span> <span data-ttu-id="1160a-151">如果您在啟動時必須執行多個程序但是並不需要同時執行它們，那麼您可以讓某一個程序成為啟動程序並且讓它叫用其他的程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-151">If you must execute multiple procedures at startup but do not need to execute them in parallel, make one procedure the startup procedure and have that procedure call the other procedures.</span></span> <span data-ttu-id="1160a-152">這樣就只會使用一個工作者執行緒。</span><span class="sxs-lookup"><span data-stu-id="1160a-152">This uses only one worker thread.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="1160a-153">請不要從自動執行的程序傳回任何結果集。</span><span class="sxs-lookup"><span data-stu-id="1160a-153">Do not return any result sets from a procedure that is executed automatically.</span></span> <span data-ttu-id="1160a-154">因為這類程序是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而非應用程式或使用者執行，所以結果集會無處可去。</span><span class="sxs-lookup"><span data-stu-id="1160a-154">Because the procedure is being executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instead of an application or user, there is nowhere for the result sets to go.</span></span>  
  
-   <span data-ttu-id="1160a-155">設定、清除和控制自動執行</span><span class="sxs-lookup"><span data-stu-id="1160a-155">Setting, Clearing, and Controlling Automatic Execution</span></span>  
  
     <span data-ttu-id="1160a-156">只有系統管理員 (**sa**) 可以將程序標示為自動執行。</span><span class="sxs-lookup"><span data-stu-id="1160a-156">Only the system administrator (**sa**) can mark a procedure to execute automatically.</span></span> <span data-ttu-id="1160a-157">此外，該程序必須位於 **master** 資料庫中，由 **sa**所擁有，並且不能有輸入或輸出參數。</span><span class="sxs-lookup"><span data-stu-id="1160a-157">In addition, the procedure must be in the **master** database, owned by **sa**, and cannot have input or output parameters.</span></span>  
  
     <span data-ttu-id="1160a-158">使用 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 可以：</span><span class="sxs-lookup"><span data-stu-id="1160a-158">Use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to:</span></span>  
  
    1.  <span data-ttu-id="1160a-159">指定一個現有的程序做為啟動程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-159">Designate an existing procedure as a startup procedure.</span></span>  
  
    2.  <span data-ttu-id="1160a-160">停止某個程序在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動時執行。</span><span class="sxs-lookup"><span data-stu-id="1160a-160">Stop a procedure from executing at [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] startup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1160a-161">Security</span><span class="sxs-lookup"><span data-stu-id="1160a-161">Security</span></span>  
 <span data-ttu-id="1160a-162">如需詳細資訊，請參閱 [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql) 和 [EXECUTE AS 子句 &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="1160a-162">For more information, see [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql) and [EXECUTE AS Clause &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1160a-163">權限</span><span class="sxs-lookup"><span data-stu-id="1160a-163">Permissions</span></span>  
 <span data-ttu-id="1160a-164">如需詳細資訊，請參閱 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-164">For more information, see the "Permissions" section in [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1160a-165">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1160a-165">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="1160a-166">若要執行預存程序</span><span class="sxs-lookup"><span data-stu-id="1160a-166">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="1160a-167">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，展開該執行個體，然後展開 [資料庫] 。</span><span class="sxs-lookup"><span data-stu-id="1160a-167">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], expand that instance, and then expand **Databases**.</span></span>  
  
2.  <span data-ttu-id="1160a-168">依序展開您要的資料庫、 **[可程式性]** 和 **[預存程序]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-168">Expand the database that you want, expand **Programmability**, and then expand **Stored Procedures**.</span></span>  
  
3.  <span data-ttu-id="1160a-169">以滑鼠右鍵按一下您要的使用者定義預存程序，然後按一下 [執行預存程序]。</span><span class="sxs-lookup"><span data-stu-id="1160a-169">Right-click the user-defined stored procedure that you want and click **Execute Stored Procedure**.</span></span>  
  
4.  <span data-ttu-id="1160a-170">在 **[執行程序]** 對話方塊中，指定每個參數的值，以及是否應傳遞 null 值。</span><span class="sxs-lookup"><span data-stu-id="1160a-170">In the **Execute Procedure** dialog box, specify a value for each parameter and whether it should pass a null value.</span></span>  
  
     <span data-ttu-id="1160a-171">**參數**</span><span class="sxs-lookup"><span data-stu-id="1160a-171">**Parameter**</span></span>  
     <span data-ttu-id="1160a-172">指出參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="1160a-172">Indicates the name of the parameter.</span></span>  
  
     <span data-ttu-id="1160a-173">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="1160a-173">**Data Type**</span></span>  
     <span data-ttu-id="1160a-174">指出參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1160a-174">Indicates the data type of the parameter.</span></span>  
  
     <span data-ttu-id="1160a-175">**輸出參數**</span><span class="sxs-lookup"><span data-stu-id="1160a-175">**Output Parameter**</span></span>  
     <span data-ttu-id="1160a-176">指出這是否為輸出參數。</span><span class="sxs-lookup"><span data-stu-id="1160a-176">Indicates if this is an output parameter.</span></span>  
  
     <span data-ttu-id="1160a-177">**傳遞 Null 值**</span><span class="sxs-lookup"><span data-stu-id="1160a-177">**Pass Null Value**</span></span>  
     <span data-ttu-id="1160a-178">傳遞 NULL 作為參數的值。</span><span class="sxs-lookup"><span data-stu-id="1160a-178">Pass a NULL as the value of the parameter.</span></span>  
  
     <span data-ttu-id="1160a-179">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="1160a-179">**Value**</span></span>  
     <span data-ttu-id="1160a-180">呼叫程序時輸入參數的值。</span><span class="sxs-lookup"><span data-stu-id="1160a-180">Type the value for the parameter when calling the procedure.</span></span>  
  
5.  <span data-ttu-id="1160a-181">若要執行預存程序，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-181">To execute the stored procedure, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1160a-182">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1160a-182">Using Transact-SQL</span></span>  
  
#### <a name="to-execute-a-stored-procedure"></a><span data-ttu-id="1160a-183">若要執行預存程序</span><span class="sxs-lookup"><span data-stu-id="1160a-183">To execute a stored procedure</span></span>  
  
1.  <span data-ttu-id="1160a-184">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1160a-184">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1160a-185">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-185">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1160a-186">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-186">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1160a-187">此範例示範如何執行需要一個參數的預存程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-187">This example shows how to execute a stored procedure that expects one parameter.</span></span> <span data-ttu-id="1160a-188">此範例會執行 `uspGetEmployeeManagers` 預存程序，並指定值  `6` 做為 `@EmployeeID` 參數。</span><span class="sxs-lookup"><span data-stu-id="1160a-188">The example executes the `uspGetEmployeeManagers` stored procedure with the value  `6` specified as the `@EmployeeID` parameter.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC dbo.uspGetEmployeeManagers 6;  
GO  
```  
  
#### <a name="to-set-or-clear-a-procedure-for-executing-automatically"></a><span data-ttu-id="1160a-189">若要設定或清除自動執行的程序</span><span class="sxs-lookup"><span data-stu-id="1160a-189">To set or clear a procedure for executing automatically</span></span>  
  
1.  <span data-ttu-id="1160a-190">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1160a-190">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1160a-191">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-191">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1160a-192">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-192">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1160a-193">此範例示範如何使用 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 設定自動執行程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-193">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to set a procedure for automatic execution.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionName = ] 'startup'   
    , @OptionValue = 'on';  
```  
  
#### <a name="to-stop-a-procedure-from-executing-automatically"></a><span data-ttu-id="1160a-194">若要停止自動執行程序</span><span class="sxs-lookup"><span data-stu-id="1160a-194">To stop a procedure from executing automatically</span></span>  
  
1.  <span data-ttu-id="1160a-195">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1160a-195">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1160a-196">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-196">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1160a-197">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="1160a-197">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1160a-198">此範例示範如何使用 [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) 設定停止自動執行程序。</span><span class="sxs-lookup"><span data-stu-id="1160a-198">This example shows how to use [sp_procoption](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql) to stop a procedure from executing automatically.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_procoption @ProcName = '<procedure name>'   
    , @OptionValue = 'off';  
```  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="1160a-199">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1160a-199">Example (Transact-SQL)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1160a-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1160a-200">See Also</span></span>  
 <span data-ttu-id="1160a-201">[指定參數](specify-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="1160a-201">[Specify Parameters](specify-parameters.md) </span></span>  
 <span data-ttu-id="1160a-202">[設定 scan for startup procs 伺服器組態選項](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="1160a-202">[Configure the scan for startup procs Server Configuration Option](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md) </span></span>  
 <span data-ttu-id="1160a-203">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1160a-203">[EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql) </span></span>  
 <span data-ttu-id="1160a-204">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1160a-204">[CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) </span></span>  
 [<span data-ttu-id="1160a-205">預存程序 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="1160a-205">Stored Procedures &#40;Database Engine&#41;</span></span>](stored-procedures-database-engine.md)  
  
  
