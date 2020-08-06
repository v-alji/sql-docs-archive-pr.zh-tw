---
title: 執行 SQL 工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- batches [Integration Services]
- Execute SQL task [Integration Services]
ms.assetid: bebb2e8c-0410-43b2-ac2f-6fc80c8f2e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e77b9f442ae8478c57d5b0e68955b541eda38aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688110"
---
# <a name="execute-sql-task"></a><span data-ttu-id="e8953-102">執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="e8953-102">Execute SQL Task</span></span>
  <span data-ttu-id="e8953-103">「執行 SQL」工作會執行封裝中的 SQL 陳述式或預存程序。</span><span class="sxs-lookup"><span data-stu-id="e8953-103">The Execute SQL task runs SQL statements or stored procedures from a package.</span></span> <span data-ttu-id="e8953-104">工作可以包含逐次執行的單一 SQL 陳述式或多重 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8953-104">The task can contain either a single SQL statement or multiple SQL statements that run sequentially.</span></span> <span data-ttu-id="e8953-105">您可將執行 SQL 工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="e8953-105">You can use the Execute SQL task for the following purposes:</span></span>  
  
-   <span data-ttu-id="e8953-106">截斷資料表或檢視，為插入資料做準備。</span><span class="sxs-lookup"><span data-stu-id="e8953-106">Truncate a table or view in preparation for inserting data.</span></span>  
  
-   <span data-ttu-id="e8953-107">建立、改變和卸除資料庫物件，例如資料表和檢視。</span><span class="sxs-lookup"><span data-stu-id="e8953-107">Create, alter, and drop database objects such as tables and views.</span></span>  
  
-   <span data-ttu-id="e8953-108">將資料載入至事實 (Fact) 和維度 (Dimension) 資料表之前，先重建這些資料表。</span><span class="sxs-lookup"><span data-stu-id="e8953-108">Re-create fact and dimension tables before loading data into them.</span></span>  
  
-   <span data-ttu-id="e8953-109">執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="e8953-109">Run stored procedures.</span></span> <span data-ttu-id="e8953-110">如果 SQL 陳述式叫用會從暫存資料表傳回結果的預存程序，請使用 WITH RESULT SETS 選項來定義結果集的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e8953-110">If the SQL statement invokes a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
-   <span data-ttu-id="e8953-111">將從查詢傳回的資料列集儲存到變數中。</span><span class="sxs-lookup"><span data-stu-id="e8953-111">Save the rowset returned from a query into a variable.</span></span>  
  
 <span data-ttu-id="e8953-112">執行 SQL 工作可搭配「Foreach 迴圈」容器和「For 迴圈」容器，用來執行多個 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8953-112">The Execute SQL task can be used in combination with the Foreach Loop and For Loop containers to run multiple SQL statements.</span></span> <span data-ttu-id="e8953-113">這些容器會實作封裝中重複的控制流程，並且可以重複執行「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="e8953-113">These containers implement repeating control flows in a package and they can run the Execute SQL task repeatedly.</span></span> <span data-ttu-id="e8953-114">例如，若使用「Foreach 迴圈」容器，封裝即可列舉資料夾中的檔案，並重複執行「執行 SQL」工作，以便執行每個檔案中儲存的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8953-114">For example, using the Foreach Loop container, a package can enumerate files in a folder and run an Execute SQL task repeatedly to execute the SQL statement stored in each file.</span></span>  
  
## <a name="connecting-to-a-data-source"></a><span data-ttu-id="e8953-115">連接資料來源</span><span class="sxs-lookup"><span data-stu-id="e8953-115">Connecting to a Data Source</span></span>  
 <span data-ttu-id="e8953-116">執行 SQL 工作可使用不同類型的連接管理員，以連接到其執行 SQL 陳述式或預存程序的資料來源。</span><span class="sxs-lookup"><span data-stu-id="e8953-116">The Execute SQL task can use different types of connection managers to connect to the data source where it runs the SQL statement or stored procedure.</span></span> <span data-ttu-id="e8953-117">此工作可使用下表中列出的連接類型。</span><span class="sxs-lookup"><span data-stu-id="e8953-117">The task can use the connection types listed in the following table.</span></span>  
  
|<span data-ttu-id="e8953-118">連線類型</span><span class="sxs-lookup"><span data-stu-id="e8953-118">Connection type</span></span>|<span data-ttu-id="e8953-119">[ODBC 來源編輯器]</span><span class="sxs-lookup"><span data-stu-id="e8953-119">Connection manager</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="e8953-120">EXCEL</span><span class="sxs-lookup"><span data-stu-id="e8953-120">EXCEL</span></span>|[<span data-ttu-id="e8953-121">Excel 連線管理員</span><span class="sxs-lookup"><span data-stu-id="e8953-121">Excel Connection Manager</span></span>](../connection-manager/excel-connection-manager.md)|  
|<span data-ttu-id="e8953-122">OLE DB</span><span class="sxs-lookup"><span data-stu-id="e8953-122">OLE DB</span></span>|[<span data-ttu-id="e8953-123">OLE DB 連線管理員</span><span class="sxs-lookup"><span data-stu-id="e8953-123">OLE DB Connection Manager</span></span>](../connection-manager/ole-db-connection-manager.md)|  
|<span data-ttu-id="e8953-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="e8953-124">ODBC</span></span>|[<span data-ttu-id="e8953-125">ODBC 連線管理員</span><span class="sxs-lookup"><span data-stu-id="e8953-125">ODBC Connection Manager</span></span>](../connection-manager/odbc-connection-manager.md)|  
|<span data-ttu-id="e8953-126">ADO</span><span class="sxs-lookup"><span data-stu-id="e8953-126">ADO</span></span>|[<span data-ttu-id="e8953-127">ADO 連線管理員</span><span class="sxs-lookup"><span data-stu-id="e8953-127">ADO Connection Manager</span></span>](../connection-manager/ado-connection-manager.md)|  
|<span data-ttu-id="e8953-128">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e8953-128">ADO.NET</span></span>|[<span data-ttu-id="e8953-129">ADO.NET 連線管理員</span><span class="sxs-lookup"><span data-stu-id="e8953-129">ADO.NET Connection Manager</span></span>](../connection-manager/ado-net-connection-manager.md)|  
|<span data-ttu-id="e8953-130">SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="e8953-130">SQLMOBILE</span></span>|[<span data-ttu-id="e8953-131">SQL Server Compact Edition 連線管理員</span><span class="sxs-lookup"><span data-stu-id="e8953-131">SQL Server Compact Edition Connection Manager</span></span>](../connection-manager/sql-server-compact-edition-connection-manager.md)|  
  
## <a name="creating-sql-statements"></a><span data-ttu-id="e8953-132">建立 SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="e8953-132">Creating SQL Statements</span></span>  
 <span data-ttu-id="e8953-133">此工作所使用的 SQL 陳述式來源，可以是包含陳述式的工作屬性、包含一個或多個陳述式的檔案連接，或者包含陳述式的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="e8953-133">The source of the SQL statements used by this task can be a task property that contains a statement, a connection to a file that contains one or multiple statements, or the name of a variable that contains a statement.</span></span> <span data-ttu-id="e8953-134">SQL 陳述式必須以來源資料庫管理系統 (DBMS) 的用語撰寫。</span><span class="sxs-lookup"><span data-stu-id="e8953-134">The SQL statements must be written in the dialect of the source database management system (DBMS).</span></span> <span data-ttu-id="e8953-135">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 查詢](../integration-services-ssis-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-135">For more information, see [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="e8953-136">如果 SQL 陳述式儲存在檔案中，則工作會使用「檔案」連接管理員連接到該檔案。</span><span class="sxs-lookup"><span data-stu-id="e8953-136">If the SQL statements are stored in a file, the task uses a File connection manager to connect to the file.</span></span> <span data-ttu-id="e8953-137">如需相關資訊，請參閱 [File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-137">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e8953-138">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中，您可以使用 [執行 SQL 工作編輯器]  對話方塊輸入 SQL 陳述式，或使用圖形化使用者介面 [查詢產生器]  建立 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="e8953-138">In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can use the **Execute SQL Task Editor** dialog box to type SQL statements, or use **Query Builder**, a graphical user interface for creating SQL queries.</span></span> <span data-ttu-id="e8953-139">如需詳細資訊，請參閱[執行 SQL 工作編輯器 &#40;一般頁面&#41;](../execute-sql-task-editor-general-page.md) 和[查詢產生器](../query-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-139">For more information, see [Execute SQL Task Editor &#40;General Page&#41;](../execute-sql-task-editor-general-page.md) and [Query Builder](../query-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8953-140">「執行 SQL」工作可能無法成功剖析在「執行 SQL」工作外部撰寫的有效 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8953-140">Valid SQL statements written outside the Execute SQL task may not be parsed successfully by the Execute SQL task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8953-141">「執行 SQL」工作會使用 `RecognizeAll` ParseMode 列舉值。</span><span class="sxs-lookup"><span data-stu-id="e8953-141">The Execute SQL Task uses the `RecognizeAll` ParseMode enumeration value.</span></span> <span data-ttu-id="e8953-142">如需詳細資訊，請參閱 [ManagedBatchParser Namespace](https://go.microsoft.com/fwlink/?LinkId=223617)(ManagedBatchParser 命名空間)。</span><span class="sxs-lookup"><span data-stu-id="e8953-142">For more information, see [ManagedBatchParser Namespace](https://go.microsoft.com/fwlink/?LinkId=223617).</span></span>  
  
## <a name="sending-multiple-statements-in-a-batch"></a><span data-ttu-id="e8953-143">在批次中傳送多重陳述式</span><span class="sxs-lookup"><span data-stu-id="e8953-143">Sending Multiple Statements in a Batch</span></span>  
 <span data-ttu-id="e8953-144">如果您在執行 SQL 工作中加入多個陳述式，可將它們組成群組，並在批次中執行。</span><span class="sxs-lookup"><span data-stu-id="e8953-144">If you include multiple statements in an Execute SQL task, you can group them and run them as a batch.</span></span> <span data-ttu-id="e8953-145">若要表示批次結束，請使用 GO 命令。</span><span class="sxs-lookup"><span data-stu-id="e8953-145">To signal the end of a batch, use the GO command.</span></span> <span data-ttu-id="e8953-146">兩個 GO 命令之間的所有 SQL 陳述式，都會在一個批次中傳送至要執行的 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="e8953-146">All the SQL statements between two GO commands are sent in a batch to the OLE DB provider to be run.</span></span> <span data-ttu-id="e8953-147">SQL 命令可包含以 GO 命令分隔的多個批次。</span><span class="sxs-lookup"><span data-stu-id="e8953-147">The SQL command can include multiple batches separated by GO commands.</span></span>  
  
 <span data-ttu-id="e8953-148">您可分組到同一個批次中的 SQL 陳述式有其限制。</span><span class="sxs-lookup"><span data-stu-id="e8953-148">There are restrictions on the kinds of SQL statements that you can group in a batch.</span></span> <span data-ttu-id="e8953-149">如需詳細資訊，請參閱 [陳述式的批次](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-149">For more information, see [Batches of Statements](../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md).</span></span>  
  
 <span data-ttu-id="e8953-150">如果執行 SQL 工作執行一個批次的 SQL 陳述式，則下列規則會套用至該批次︰</span><span class="sxs-lookup"><span data-stu-id="e8953-150">If the Execute SQL task runs a batch of SQL statements, the following rules apply to the batch:</span></span>  
  
-   <span data-ttu-id="e8953-151">只有一個陳述式可傳回結果集，且它必須是批次中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8953-151">Only one statement can return a result set and it must be the first statement in the batch.</span></span>  
  
-   <span data-ttu-id="e8953-152">如果結果集使用結果繫結，則查詢必須傳回相同數目的資料行。</span><span class="sxs-lookup"><span data-stu-id="e8953-152">If the result set uses result bindings, the queries must return the same number of columns.</span></span> <span data-ttu-id="e8953-153">如果查詢傳回不同數目的資料行，工作便會失敗。</span><span class="sxs-lookup"><span data-stu-id="e8953-153">If the queries return a different number of columns, the task fails.</span></span> <span data-ttu-id="e8953-154">不過，即使工作失敗，它執行的查詢 (例如，DELETE 或 INSERT 查詢) 仍會成功。</span><span class="sxs-lookup"><span data-stu-id="e8953-154">However, even if the task fails, the queries that it runs, such as DELETE or INSERT queries, may succeed.</span></span>  
  
-   <span data-ttu-id="e8953-155">如果結果繫結使用資料行名稱，則查詢必須傳回名稱與工作所使用之結果集名稱相同的資料行。</span><span class="sxs-lookup"><span data-stu-id="e8953-155">If the result bindings use column names, the query must return columns that have the same names as the result set names that are used in the task.</span></span> <span data-ttu-id="e8953-156">如果資料行遺失，工作便會失敗。</span><span class="sxs-lookup"><span data-stu-id="e8953-156">If the columns are missing, the task fails.</span></span>  
  
-   <span data-ttu-id="e8953-157">如果工作使用參數繫結，則批次中所有查詢的參數數目和類型都必須相同。</span><span class="sxs-lookup"><span data-stu-id="e8953-157">If the task uses parameter binding, all the queries in the batch must have the same number and types of parameters.</span></span>  
  
## <a name="running-parameterized-sql-commands"></a><span data-ttu-id="e8953-158">執行參數化的 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="e8953-158">Running Parameterized SQL Commands</span></span>  
 <span data-ttu-id="e8953-159">SQL 陳述式和預存程序經常使用輸入參數、輸出參數以及傳回碼。</span><span class="sxs-lookup"><span data-stu-id="e8953-159">SQL statements and stored procedures frequently use input parameters, output parameters, and return codes.</span></span> <span data-ttu-id="e8953-160">執行 SQL 工作支援 `Input`、`Output` 和 `ReturnValue` 等參數類型。</span><span class="sxs-lookup"><span data-stu-id="e8953-160">The Execute SQL task supports the `Input`, `Output`, and `ReturnValue` parameter types.</span></span> <span data-ttu-id="e8953-161">您可以使用 `Input` 類型當做輸入參數，使用 `Output` 當做輸出參數，並使用 `ReturnValue` 當做傳回碼。</span><span class="sxs-lookup"><span data-stu-id="e8953-161">You use the `Input` type for input parameters, `Output` for output parameters, and `ReturnValue` for return codes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8953-162">只有在資料提供者支援參數時，您才能在執行 SQL 工作中使用參數。</span><span class="sxs-lookup"><span data-stu-id="e8953-162">You can use parameters in an Execute SQL task only if the data provider supports them.</span></span>  
  
 <span data-ttu-id="e8953-163">如需在「執行 SQL」工作中使用參數和傳回碼的資訊，請參閱 [執行 SQL 工作中的參數和傳回碼](execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-163">For information on using parameters and return codes in the Execute SQL task, see [Parameters and Return Codes in the Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="specifying-a-result-set-type"></a><span data-ttu-id="e8953-164">指定結果集類型</span><span class="sxs-lookup"><span data-stu-id="e8953-164">Specifying a Result Set Type</span></span>  
 <span data-ttu-id="e8953-165">根據 SQL 命令的類型而定，結果集可能會，也可能不會傳回到執行 SQL 工作。</span><span class="sxs-lookup"><span data-stu-id="e8953-165">Depending on the type of SQL command, a result set may or may not be returned to the Execute SQL task.</span></span> <span data-ttu-id="e8953-166">例如，SELECT 陳述式通常會傳回結果集，INSERT 陳述式則不會。</span><span class="sxs-lookup"><span data-stu-id="e8953-166">For example, a SELECT statement typically returns a result set, but an INSERT statement does not.</span></span> <span data-ttu-id="e8953-167">來自 SELECT 陳述式的結果集可包含零個資料列、一個資料列或多個資料列。</span><span class="sxs-lookup"><span data-stu-id="e8953-167">The result set from a SELECT statement can contain zero rows, one row, or many rows.</span></span> <span data-ttu-id="e8953-168">預存程序亦可傳回整數值，稱為傳回碼，以表示程序的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="e8953-168">Stored procedures can also return an integer value, called a return code, that indicates the execution status of the procedure.</span></span> <span data-ttu-id="e8953-169">在此情況下，結果集是由單一資料列所組成。</span><span class="sxs-lookup"><span data-stu-id="e8953-169">In that case, the result set consists of a single row.</span></span>  
  
 <span data-ttu-id="e8953-170">如需在「執行 SQL」工作中從 SQL 命令擷取結果集的資訊，請參閱 [執行 SQL 工作中的結果集](../result-sets-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-170">For information on retrieving result sets from SQL commands in the Execute SQL task, see [Result Sets in the Execute SQL Task](../result-sets-in-the-execute-sql-task.md).</span></span>  
  
## <a name="troubleshooting-the-execute-sql-task"></a><span data-ttu-id="e8953-171">疑難排解執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="e8953-171">Troubleshooting the Execute SQL Task</span></span>  
 <span data-ttu-id="e8953-172">您可以記錄執行 SQL 工作對外部資料提供者執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e8953-172">You can log the calls that the Execute SQL task makes to external data providers.</span></span> <span data-ttu-id="e8953-173">您可以使用這項記錄功能，疑難排解執行 SQL 工作所執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="e8953-173">You can use this logging capability to troubleshoot the SQL commands that the Execute SQL task runs.</span></span> <span data-ttu-id="e8953-174">若要記錄「執行 SQL」工作對外部資料提供者執行的呼叫，請啟用封裝記錄，然後在封裝層級選取 [診斷] 事件。</span><span class="sxs-lookup"><span data-stu-id="e8953-174">To log the calls that the Execute SQL task makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="e8953-175">如需詳細資訊，請參閱 [封裝執行的疑難排解工具](../troubleshooting/troubleshooting-tools-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-175">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="e8953-176">有時 SQL 命令或預存程序會傳回多個結果集。</span><span class="sxs-lookup"><span data-stu-id="e8953-176">Sometimes a SQL command or stored procedure returns multiple result sets.</span></span> <span data-ttu-id="e8953-177">這些結果集不只包括屬於 `SELECT` 查詢結果的資料列集，也包括屬於 `RAISERROR` 或 `PRINT` 陳述式之錯誤結果的單一值。</span><span class="sxs-lookup"><span data-stu-id="e8953-177">These result sets include not only rowsets that are the result of `SELECT` queries, but single values that are the result of errors of `RAISERROR` or `PRINT` statements.</span></span> <span data-ttu-id="e8953-178">工作是否忽略發生在第一個結果集之後之結果集中的錯誤，將取決於所使用的連接管理員類型：</span><span class="sxs-lookup"><span data-stu-id="e8953-178">Whether the task ignores errors in result sets that occur after the first result set depends on the type of connection manager that is used:</span></span>  
  
-   <span data-ttu-id="e8953-179">使用 OLE DB 和 ADO 連接管理員時，工作會忽略發生在第一個結果集之後的結果集。</span><span class="sxs-lookup"><span data-stu-id="e8953-179">When you use OLE DB and ADO connection managers, the task ignores the result sets that occur after the first result set.</span></span> <span data-ttu-id="e8953-180">因此，使用這些連接管理員時，如果錯誤不屬於第一個結果集的一部分，便會忽略 SQL 命令或預存程序所傳回的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8953-180">Therefore, with these connection managers, the task ignores an error returned by an SQL command or a stored procedure when the error is not part of the first result set.</span></span>  
  
-   <span data-ttu-id="e8953-181">使用 ODBC 和 ADO.NET 連接管理員時，工作不會忽略發生在第一個結果集之後的結果集。</span><span class="sxs-lookup"><span data-stu-id="e8953-181">When you use ODBC and ADO.NET connection managers, the task does not ignore result sets that occur after the first result set.</span></span> <span data-ttu-id="e8953-182">使用這些連接管理員時，如果第一個結果集之外的結果集包含錯誤，工作將會失敗。</span><span class="sxs-lookup"><span data-stu-id="e8953-182">With these connection managers, the task will fail with an error when a result set other than the first result set contains an error.</span></span>  
  
### <a name="custom-log-entries"></a><span data-ttu-id="e8953-183">自訂記錄項目</span><span class="sxs-lookup"><span data-stu-id="e8953-183">Custom Log Entries</span></span>  
 <span data-ttu-id="e8953-184">下表描述「執行 SQL」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="e8953-184">The following table describes the custom log entry for the Execute SQL task.</span></span> <span data-ttu-id="e8953-185">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="e8953-185">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="e8953-186">記錄項目</span><span class="sxs-lookup"><span data-stu-id="e8953-186">Log entry</span></span>|<span data-ttu-id="e8953-187">描述</span><span class="sxs-lookup"><span data-stu-id="e8953-187">Description</span></span>|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|<span data-ttu-id="e8953-188">提供 SQL 陳述式執行階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e8953-188">Provides information about the execution phases of the SQL statement.</span></span> <span data-ttu-id="e8953-189">寫入記錄項目的時機包括在工作取得資料庫連接時、在工作開始準備 SQL 陳述式時，以及在 SQL 陳述式執行完成之後。</span><span class="sxs-lookup"><span data-stu-id="e8953-189">Log entries are written when the task acquires connection to the database, when the task starts to prepare the SQL statement, and after the execution of the SQL statement is completed.</span></span> <span data-ttu-id="e8953-190">準備階段的記錄項目包含工作所使用的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8953-190">The log entry for the prepare phase includes the SQL statement that the task uses.</span></span>|  
  
## <a name="configuring-the-execute-sql-task"></a><span data-ttu-id="e8953-191">設定執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="e8953-191">Configuring the Execute SQL Task</span></span>  
 <span data-ttu-id="e8953-192">您可以利用下列方式設定執行 SQL 工作：</span><span class="sxs-lookup"><span data-stu-id="e8953-192">You can configure the Execute SQL task in the following ways:</span></span>  
  
-   <span data-ttu-id="e8953-193">指定用來連接到資料庫的連接管理員類型。</span><span class="sxs-lookup"><span data-stu-id="e8953-193">Specify the type of connection manager to use to connect to a database.</span></span>  
  
-   <span data-ttu-id="e8953-194">指定 SQL 陳述式傳回的結果集類型。</span><span class="sxs-lookup"><span data-stu-id="e8953-194">Specify the type of result set that the SQL statement returns.</span></span>  
  
-   <span data-ttu-id="e8953-195">指定 SQL 陳述式的逾時。</span><span class="sxs-lookup"><span data-stu-id="e8953-195">Specify a time-out for the SQL statements.</span></span>  
  
-   <span data-ttu-id="e8953-196">指定 SQL 陳述式的來源。</span><span class="sxs-lookup"><span data-stu-id="e8953-196">Specify the source of the SQL statement.</span></span>  
  
-   <span data-ttu-id="e8953-197">指示工作是否要略過 SQL 陳述式的準備階段。</span><span class="sxs-lookup"><span data-stu-id="e8953-197">Indicate whether the task skips the prepare phase for the SQL statement.</span></span>  
  
-   <span data-ttu-id="e8953-198">如果使用 ADO 連接類型，您必須指出 SQL 陳述式是否為預存程序。</span><span class="sxs-lookup"><span data-stu-id="e8953-198">If you use the ADO connection type, you must indicate whether the SQL statement is a stored procedure.</span></span> <span data-ttu-id="e8953-199">如果是其他連接類型，此屬性為唯讀，且其值固定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e8953-199">For other connection types, this property is read-only and its value is always `false`.</span></span>  
  
 <span data-ttu-id="e8953-200">您可以程式設計方式或透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e8953-200">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="e8953-201">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="e8953-201">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e8953-202">&#40;一般頁面&#41;執行 SQL 工作編輯器</span><span class="sxs-lookup"><span data-stu-id="e8953-202">Execute SQL Task Editor &#40;General Page&#41;</span></span>](../execute-sql-task-editor-general-page.md)  
  
-   <span data-ttu-id="e8953-203">[[執行 SQL 工作編輯器] &#40;[參數對應] 頁面&#41;](../execute-sql-task-editor-parameter-mapping-page.md)</span><span class="sxs-lookup"><span data-stu-id="e8953-203">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../execute-sql-task-editor-parameter-mapping-page.md)</span></span>  
  
-   <span data-ttu-id="e8953-204">[[執行 SQL 工作編輯器] &#40;[結果集] 頁面&#41;](../execute-sql-task-editor-result-set-page.md)</span><span class="sxs-lookup"><span data-stu-id="e8953-204">[Execute SQL Task Editor &#40;Result Set Page&#41;](../execute-sql-task-editor-result-set-page.md)</span></span>  
  
-   [<span data-ttu-id="e8953-205">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="e8953-205">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="e8953-206">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="e8953-206">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="e8953-207">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="e8953-207">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="configuring-the-execute-sql-task-programmatically"></a><span data-ttu-id="e8953-208">以程式設計的方式設定執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="e8953-208">Configuring the Execute SQL Task Programmatically</span></span>  
 <span data-ttu-id="e8953-209">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="e8953-209">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ExecuteSQLTask.ExecuteSQLTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="e8953-210">相關工作</span><span class="sxs-lookup"><span data-stu-id="e8953-210">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e8953-211">在執行 SQL 工作中將查詢參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="e8953-211">Map Query Parameters to Variables in an Execute SQL Task</span></span>](../map-query-parameters-to-variables-in-an-execute-sql-task.md)  
  
-   [<span data-ttu-id="e8953-212">在執行 SQL 工作中將結果集對應至變數</span><span class="sxs-lookup"><span data-stu-id="e8953-212">Map Result Sets to Variables in an Execute SQL Task</span></span>](../map-result-sets-to-variables-in-an-execute-sql-task.md)  
  
## <a name="related-content"></a><span data-ttu-id="e8953-213">相關內容</span><span class="sxs-lookup"><span data-stu-id="e8953-213">Related Content</span></span>  
  
-   [<span data-ttu-id="e8953-214">執行 SQL 工作中的參數和傳回碼</span><span class="sxs-lookup"><span data-stu-id="e8953-214">Parameters and Return Codes in the Execute SQL Task</span></span>](execute-sql-task.md)  
  
-   [<span data-ttu-id="e8953-215">執行 SQL 工作中的結果集</span><span class="sxs-lookup"><span data-stu-id="e8953-215">Result Sets in the Execute SQL Task</span></span>](../result-sets-in-the-execute-sql-task.md)  
  
-   [<span data-ttu-id="e8953-216">Transact-SQL 參考 &#40;資料庫引擎41;</span><span class="sxs-lookup"><span data-stu-id="e8953-216">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
-   <span data-ttu-id="e8953-217">mssqltips.com 上的部落格文章： [New Date and Time Functions in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=239783)(SQL Server 2012 中的新日期和時間函數)</span><span class="sxs-lookup"><span data-stu-id="e8953-217">Blog entry, [New Date and Time Functions in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=239783), on mssqltips.com</span></span>  
  
  
