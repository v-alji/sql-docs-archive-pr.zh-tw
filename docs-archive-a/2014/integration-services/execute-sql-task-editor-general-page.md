---
title: " (一般頁面) 執行 SQL 工作編輯器 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executesqltask.general.f1
helpviewer_keywords:
- Execute SQL Task Editor
ms.assetid: beb39086-28ce-46af-b6d8-f7b4fb8d9069
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 32bec035646c976442eb66ff1270b961835b243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592765"
---
# <a name="execute-sql-task-editor-general-page"></a><span data-ttu-id="eb60b-102">執行 SQL 工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="eb60b-102">Execute SQL Task Editor (General Page)</span></span>
  <span data-ttu-id="eb60b-103">使用 [執行 SQL 工作編輯器]  對話方塊的 [一般]  頁面，即可設定「執行 SQL」工作和提供該工作執行的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb60b-103">Use the **General** page of the **Execute SQL Task Editor** dialog box to configure the Execute SQL task and provide the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="eb60b-104">若要了解這項工作，請參閱[執行 SQL 工作](control-flow/execute-sql-task.md)、[執行 SQL 工作中的參數和傳回碼](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)和[執行 SQL 工作中的結果集](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="eb60b-104">To learn about this task, see [Execute SQL Task](control-flow/execute-sql-task.md), [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md), and [Result Sets in the Execute SQL Task](../../2014/integration-services/result-sets-in-the-execute-sql-task.md).</span></span> <span data-ttu-id="eb60b-105">若要深入了解 Transact-SQL 查詢語言，請參閱 [Transact-SQL 參考 &#40;資料庫引擎&#41;](/sql/t-sql/language-reference)。</span><span class="sxs-lookup"><span data-stu-id="eb60b-105">To learn more about the Transact-SQL query language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="eb60b-106">靜態選項</span><span class="sxs-lookup"><span data-stu-id="eb60b-106">Static Options</span></span>  
 <span data-ttu-id="eb60b-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eb60b-107">**Name**</span></span>  
 <span data-ttu-id="eb60b-108">提供唯一的名稱給工作流程中的執行 SQL 工作。</span><span class="sxs-lookup"><span data-stu-id="eb60b-108">Provide a unique name for the Execute SQL task in the workflow.</span></span> <span data-ttu-id="eb60b-109">提供的名稱將顯示在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師內。</span><span class="sxs-lookup"><span data-stu-id="eb60b-109">The name that is provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="eb60b-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="eb60b-110">**Description**</span></span>  
 <span data-ttu-id="eb60b-111">描述執行 SQL 工作。</span><span class="sxs-lookup"><span data-stu-id="eb60b-111">Describe the Execute SQL task.</span></span> <span data-ttu-id="eb60b-112">最佳作法是以其用途描述工作，使封裝可以自我記錄並易於維護。</span><span class="sxs-lookup"><span data-stu-id="eb60b-112">As a best practice, to make packages self-documenting and easier to maintain, describe the task in terms of its purpose.</span></span>  
  
 <span data-ttu-id="eb60b-113">**TimeOut**</span><span class="sxs-lookup"><span data-stu-id="eb60b-113">**TimeOut**</span></span>  
 <span data-ttu-id="eb60b-114">指定工作在逾時之前執行的秒數上限。值為 0 指出無限的時間。</span><span class="sxs-lookup"><span data-stu-id="eb60b-114">Specify the maximum number of seconds the task will run before timing out. A value of 0 indicates an infinite time.</span></span> <span data-ttu-id="eb60b-115">預設值是 0。</span><span class="sxs-lookup"><span data-stu-id="eb60b-115">The default is 0.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb60b-116">如果預存程序藉由提供大於 [逾時]  指定的秒數之連接時間與交易完成時間，使預存程序模擬睡眠功能，就不會發生逾時。</span><span class="sxs-lookup"><span data-stu-id="eb60b-116">Stored procedures do not time out if they emulate sleep functionality by providing time for connections to be made and transactions to complete that is greater than the number of seconds specified by **TimeOut**.</span></span> <span data-ttu-id="eb60b-117">不過，執行查詢的預存程序一律會受到 [逾時]  所指定的時間限制。</span><span class="sxs-lookup"><span data-stu-id="eb60b-117">However, stored procedures that execute queries are always subject to the time restriction specified by **TimeOut**.</span></span>  
  
 <span data-ttu-id="eb60b-118">**CodePage**</span><span class="sxs-lookup"><span data-stu-id="eb60b-118">**CodePage**</span></span>  
 <span data-ttu-id="eb60b-119">指定翻譯變數中的 Unicode 值時要使用的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="eb60b-119">Specify the code page to use when translating Unicode values in variables.</span></span> <span data-ttu-id="eb60b-120">預設值是本機電腦的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="eb60b-120">The default value is the code page of the local computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb60b-121">當「執行 SQL」工作使用 ADO 或 ODBC 連線管理員時， **CodePage** 屬性就無法使用。</span><span class="sxs-lookup"><span data-stu-id="eb60b-121">When the Execute SQL task uses an ADO or ODBC connection manager, the **CodePage** property is not available.</span></span> <span data-ttu-id="eb60b-122">如果您的方案需要使用字碼頁，請使用 OLE DB 或 ADO.NET 連接管理員搭配執行 SQL 工作。</span><span class="sxs-lookup"><span data-stu-id="eb60b-122">If your solution requires the use of a code page, use an OLE DB or an ADO.NET connection manager with the Execute SQL task.</span></span>  
  
 <span data-ttu-id="eb60b-123">**TypeConversionMode**</span><span class="sxs-lookup"><span data-stu-id="eb60b-123">**TypeConversionMode**</span></span>  
 <span data-ttu-id="eb60b-124">將此屬性設為 `Allowed` 時，「執行 SQL」工作會嘗試將輸出參數和查詢結果轉換為指派結果之變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="eb60b-124">When you set this property to `Allowed`, the Execute SQL Task will attempt to convert output parameter and query results to the data type of the variable the results are assigned to.</span></span> <span data-ttu-id="eb60b-125">這適用於 [單一資料列]  結果集類型。</span><span class="sxs-lookup"><span data-stu-id="eb60b-125">This applies to the **Single row** result set type.</span></span>  
  
 <span data-ttu-id="eb60b-126">**ResultSet**</span><span class="sxs-lookup"><span data-stu-id="eb60b-126">**ResultSet**</span></span>  
 <span data-ttu-id="eb60b-127">指定 SQL 陳述式開始執行的預期結果類型。</span><span class="sxs-lookup"><span data-stu-id="eb60b-127">Specify the result type expected by the SQL statement being run.</span></span> <span data-ttu-id="eb60b-128">在 [單一資料列]  、[完整結果集]  、[XML]  或 [無]  之間選擇。</span><span class="sxs-lookup"><span data-stu-id="eb60b-128">Choose among **Single row**, **Full result set**, **XML**, or **None**.</span></span>  
  
 <span data-ttu-id="eb60b-129">**ConnectionType**</span><span class="sxs-lookup"><span data-stu-id="eb60b-129">**ConnectionType**</span></span>  
 <span data-ttu-id="eb60b-130">選擇用來連接到資料來源的連接管理員類型。</span><span class="sxs-lookup"><span data-stu-id="eb60b-130">Choose the type of connection manager to use to connect to the data source.</span></span> <span data-ttu-id="eb60b-131">可用的連接類型包括 **OLE DB**、 **ODBC**、 **ADO**、 **ADO.NET** 和 **SQLMOBILE**。</span><span class="sxs-lookup"><span data-stu-id="eb60b-131">Available connection types include **OLE DB**, **ODBC**, **ADO**, **ADO.NET** and **SQLMOBILE**.</span></span>  
  
 <span data-ttu-id="eb60b-132">**相關主題：** [OLE DB 連線管理員](connection-manager/ole-db-connection-manager.md)、[ODBC 連線管理員](connection-manager/odbc-connection-manager.md)、[ADO 連線管理員](connection-manager/ado-connection-manager.md)、[ADO.NET 連線管理員](connection-manager/ado-net-connection-manager.md)、[SQL Server Compact Edition 連線管理員](connection-manager/sql-server-compact-edition-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="eb60b-132">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [ODBC Connection Manager](connection-manager/odbc-connection-manager.md), [ADO Connection Manager](connection-manager/ado-connection-manager.md), [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [SQL Server Compact Edition Connection Manager](connection-manager/sql-server-compact-edition-connection-manager.md)</span></span>  
  
 <span data-ttu-id="eb60b-133">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="eb60b-133">**Connection**</span></span>  
 <span data-ttu-id="eb60b-134">從已定義的連接管理員清單中選擇連接。</span><span class="sxs-lookup"><span data-stu-id="eb60b-134">Choose the connection from a list of defined connection managers.</span></span> <span data-ttu-id="eb60b-135">若要建立新的連線，請選取 \<**New connection...**>。</span><span class="sxs-lookup"><span data-stu-id="eb60b-135">To create a new connection, select \<**New connection...**>.</span></span>  
  
 <span data-ttu-id="eb60b-136">**SQLSourceType**</span><span class="sxs-lookup"><span data-stu-id="eb60b-136">**SQLSourceType**</span></span>  
 <span data-ttu-id="eb60b-137">選取工作執行之 SQL 陳述式的來源類型。</span><span class="sxs-lookup"><span data-stu-id="eb60b-137">Select the source type of the SQL statement that the task runs.</span></span>  
  
 <span data-ttu-id="eb60b-138">而根據執行 SQL 工作所使用的連接管理員類型，您必須在參數化 SQL 陳述式中使用特定的參數標記。</span><span class="sxs-lookup"><span data-stu-id="eb60b-138">Depending on the connection manager type that Execute SQL task uses, you must use specific parameter markers in parameterized SQL statements.</span></span>  
  
 <span data-ttu-id="eb60b-139">**相關主題：**[執行 sql](control-flow/execute-sql-task.md)工作中的參數化 SQL 命令區段</span><span class="sxs-lookup"><span data-stu-id="eb60b-139">**Related Topics:** Running Parameterized SQL Commands section in [Execute SQL Task](control-flow/execute-sql-task.md)</span></span>  
  
 <span data-ttu-id="eb60b-140">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="eb60b-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="eb60b-141">值</span><span class="sxs-lookup"><span data-stu-id="eb60b-141">Value</span></span>|<span data-ttu-id="eb60b-142">描述</span><span class="sxs-lookup"><span data-stu-id="eb60b-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb60b-143">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="eb60b-143">**Direct input**</span></span>|<span data-ttu-id="eb60b-144">將來源設定為 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb60b-144">Set the source to a Transact-SQL statement.</span></span> <span data-ttu-id="eb60b-145">選取此值會顯示動態選項 [SQLStatement]  。</span><span class="sxs-lookup"><span data-stu-id="eb60b-145">Selecting this value displays the dynamic option, **SQLStatement**.</span></span>|  
|<span data-ttu-id="eb60b-146">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="eb60b-146">**File connection**</span></span>|<span data-ttu-id="eb60b-147">選取包含 Transact-SQL 陳述式的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb60b-147">Select a file that contains a Transact-SQL statement.</span></span> <span data-ttu-id="eb60b-148">選取此選項會顯示動態選項 [FileConnection]  。</span><span class="sxs-lookup"><span data-stu-id="eb60b-148">Setting this option displays the dynamic option, **FileConnection**.</span></span>|  
|<span data-ttu-id="eb60b-149">**變數**</span><span class="sxs-lookup"><span data-stu-id="eb60b-149">**Variable**</span></span>|<span data-ttu-id="eb60b-150">將來源設定為定義 Transact-SQL 陳述式的變數。</span><span class="sxs-lookup"><span data-stu-id="eb60b-150">Set the source to a variable that defines the Transact-SQL statement.</span></span> <span data-ttu-id="eb60b-151">選取此值會顯示動態選項 [SourceVariable]  。</span><span class="sxs-lookup"><span data-stu-id="eb60b-151">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
  
 <span data-ttu-id="eb60b-152">**QueryIsStoredProcedure**</span><span class="sxs-lookup"><span data-stu-id="eb60b-152">**QueryIsStoredProcedure**</span></span>  
 <span data-ttu-id="eb60b-153">指出要執行之指定的 SQL 陳述式是否為預存程序。</span><span class="sxs-lookup"><span data-stu-id="eb60b-153">Indicates whether the specified SQL statement to be run is a stored procedure.</span></span> <span data-ttu-id="eb60b-154">只有工作使用 ADO 連接管理員時，此屬性才會是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="eb60b-154">This property is read/write only if the task uses the ADO connection manager.</span></span> <span data-ttu-id="eb60b-155">否則此屬性是唯讀的，且其值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="eb60b-155">Otherwise the property is read-only and its value is `false`.</span></span>  
  
 <span data-ttu-id="eb60b-156">**BypassPrepare**</span><span class="sxs-lookup"><span data-stu-id="eb60b-156">**BypassPrepare**</span></span>  
 <span data-ttu-id="eb60b-157">指出 SQL 陳述式是否已備妥。</span><span class="sxs-lookup"><span data-stu-id="eb60b-157">Indicate whether the SQL statement is prepared.</span></span>  <span data-ttu-id="eb60b-158">`true` 會略過準備；`false` 會在執行它之前備妥 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb60b-158">`true` skips preparation; `false` prepares the SQL statement before running it.</span></span> <span data-ttu-id="eb60b-159">只有搭配支援準備的 OLE DB 連接，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="eb60b-159">This option is available only with OLE DB connections that support preparation.</span></span>  
  
 <span data-ttu-id="eb60b-160">**相關主題：** [備妥的執行](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span><span class="sxs-lookup"><span data-stu-id="eb60b-160">**Related Topics:**  [Prepared Execution](../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)</span></span>  
  
 <span data-ttu-id="eb60b-161">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="eb60b-161">**Browse**</span></span>  
 <span data-ttu-id="eb60b-162">使用 [開啟]  對話方塊，以尋找包含 SQL 陳述式的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb60b-162">Locate a file that contains a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="eb60b-163">選取要將檔案內容以 SQL 陳述式複製到 **SQLStatement** 屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="eb60b-163">Select a file to copy the contents of the file as a SQL statement into the **SQLStatement** property.</span></span>  
  
 <span data-ttu-id="eb60b-164">**建立查詢**</span><span class="sxs-lookup"><span data-stu-id="eb60b-164">**Build Query**</span></span>  
 <span data-ttu-id="eb60b-165">使用 [查詢產生器]  對話方塊建立 SQL 陳述式，它是用來建立查詢的圖形化工具。</span><span class="sxs-lookup"><span data-stu-id="eb60b-165">Create an SQL statement using the **Query Builder** dialog box, a graphical tool used to create queries.</span></span> <span data-ttu-id="eb60b-166">當 [SQLSourceType]  選項設定為 [直接輸入]  時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="eb60b-166">This option is available when the **SQLSourceType** option is set to **Direct input**.</span></span>  
  
 <span data-ttu-id="eb60b-167">**剖析查詢**</span><span class="sxs-lookup"><span data-stu-id="eb60b-167">**Parse Query**</span></span>  
 <span data-ttu-id="eb60b-168">驗證 SQL 陳述式的語法。</span><span class="sxs-lookup"><span data-stu-id="eb60b-168">Validate the syntax of the SQL statement.</span></span>  
  
## <a name="sqlsourcetype-dynamic-options"></a><span data-ttu-id="eb60b-169">SQLSourceType 動態選項</span><span class="sxs-lookup"><span data-stu-id="eb60b-169">SQLSourceType Dynamic Options</span></span>  
  
### <a name="sqlsourcetype--direct-input"></a><span data-ttu-id="eb60b-170">SQLSourceType = 直接輸入</span><span class="sxs-lookup"><span data-stu-id="eb60b-170">SQLSourceType = Direct input</span></span>  
 <span data-ttu-id="eb60b-171">**SQLStatement**</span><span class="sxs-lookup"><span data-stu-id="eb60b-171">**SQLStatement**</span></span>  
 <span data-ttu-id="eb60b-172">在選項方塊中鍵入要執行的 SQL 陳述式，或者按一下瀏覽按鈕 (...) 在 [輸入 SQL 查詢]  對話方塊中鍵入 SQL 陳述式，或按一下 [建置查詢]  使用 [查詢產生器]  對話方塊來撰寫陳述式。</span><span class="sxs-lookup"><span data-stu-id="eb60b-172">Type the SQL statement to execute in the option box, or click the browse button (...) to type the SQL statement in the **Enter SQL Query** dialog box, or click **Build Query** to compose the statement using the **Query Builder** dialog box.</span></span>  
  
 <span data-ttu-id="eb60b-173">**相關主題：** [查詢產生器](../../2014/integration-services/query-builder.md)</span><span class="sxs-lookup"><span data-stu-id="eb60b-173">**Related Topics:** [Query Builder](../../2014/integration-services/query-builder.md)</span></span>  
  
### <a name="sqlsourcetype--file-connection"></a><span data-ttu-id="eb60b-174">SQLSourceType = 檔案連接</span><span class="sxs-lookup"><span data-stu-id="eb60b-174">SQLSourceType = File connection</span></span>  
 <span data-ttu-id="eb60b-175">**FileConnection**</span><span class="sxs-lookup"><span data-stu-id="eb60b-175">**FileConnection**</span></span>  
 <span data-ttu-id="eb60b-176">選取現有的檔案連線管理員，或按一下 \<**New connection...**> 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="eb60b-176">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="eb60b-177">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="eb60b-177">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="sqlsourcetype--variable"></a><span data-ttu-id="eb60b-178">SQLSourceType = 變數</span><span class="sxs-lookup"><span data-stu-id="eb60b-178">SQLSourceType = Variable</span></span>  
 <span data-ttu-id="eb60b-179">**SourceVariable**</span><span class="sxs-lookup"><span data-stu-id="eb60b-179">**SourceVariable**</span></span>  
 <span data-ttu-id="eb60b-180">選取現有的變數，或按一下 \<**New variable...**> 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="eb60b-180">Select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="eb60b-181">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="eb60b-181">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb60b-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb60b-182">See Also</span></span>  
 <span data-ttu-id="eb60b-183">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="eb60b-183">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="eb60b-184">[[執行 SQL 工作編輯器] &#40;[參數對應] 頁面&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span><span class="sxs-lookup"><span data-stu-id="eb60b-184">[Execute SQL Task Editor &#40;Parameter Mapping Page&#41;](../../2014/integration-services/execute-sql-task-editor-parameter-mapping-page.md) </span></span>  
 <span data-ttu-id="eb60b-185">[[執行 SQL 工作編輯器] &#40;[結果集] 頁面&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)</span><span class="sxs-lookup"><span data-stu-id="eb60b-185">[Execute SQL Task Editor &#40;Result Set Page&#41;](../../2014/integration-services/execute-sql-task-editor-result-set-page.md)</span></span>  
  
  
