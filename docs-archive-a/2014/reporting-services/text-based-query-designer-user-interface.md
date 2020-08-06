---
title: 以文字為基礎的查詢設計工具使用者介面 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
- sql12.rtp.rptdesigner.dataview.genericquerydesigner.f1
helpviewer_keywords:
- text-based query designer [Reporting Services]
- query designers [Reporting Services], text-based
ms.assetid: 44b7c664-03aa-494e-a484-052b318e810c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1647d69246ba85dfbe0718799441c3687c0beca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706958"
---
# <a name="text-based-query-designer-user-interface"></a><span data-ttu-id="bdacd-102">以文字為基礎的查詢設計工具使用者介面</span><span class="sxs-lookup"><span data-stu-id="bdacd-102">Text-based Query Designer User Interface</span></span>
  <span data-ttu-id="bdacd-103">使用以文字為基礎的查詢設計工具，可透過資料來源支援的查詢語言來指定查詢、執行查詢，並在設計階段檢視結果。</span><span class="sxs-lookup"><span data-stu-id="bdacd-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="bdacd-104">您可以指定多個 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式、自訂資料處理延伸模組的查詢或命令語法，以及指定為運算式的查詢。</span><span class="sxs-lookup"><span data-stu-id="bdacd-104">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="bdacd-105">以文字為基礎的查詢設計工具不會前置處理查詢，而且可以容納各種查詢語法，所以這是許多資料來源類型的預設查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="bdacd-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

 <span data-ttu-id="bdacd-106">以文字為基礎的查詢設計工具會顯示一個工具列及以下兩個窗格：</span><span class="sxs-lookup"><span data-stu-id="bdacd-106">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="bdacd-107">**查詢**顯示查詢文字、資料表名稱或預存程式名稱。</span><span class="sxs-lookup"><span data-stu-id="bdacd-107">**Query** Shows the query text, table name, or stored procedure name.</span></span>

-   <span data-ttu-id="bdacd-108">**結果** ：顯示在設計階段執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="bdacd-108">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="bdacd-109">以文字為基礎的查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="bdacd-109">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="bdacd-110">以文字為基礎的查詢設計工具為所有的命令類型提供了單一工具列。</span><span class="sxs-lookup"><span data-stu-id="bdacd-110">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="bdacd-111">下表列出工具列上的每一個按鈕以及該按鈕的功能。</span><span class="sxs-lookup"><span data-stu-id="bdacd-111">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="bdacd-112">按鈕</span><span class="sxs-lookup"><span data-stu-id="bdacd-112">Button</span></span>|<span data-ttu-id="bdacd-113">描述</span><span class="sxs-lookup"><span data-stu-id="bdacd-113">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="bdacd-114">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="bdacd-114">**Edit As Text**</span></span>|<span data-ttu-id="bdacd-115">在以文字為基礎的查詢設計工具和圖形化查詢設計工具之間切換。</span><span class="sxs-lookup"><span data-stu-id="bdacd-115">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="bdacd-116">並非所有的資料來源類型都支援圖形化查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="bdacd-116">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="bdacd-117">**匯入**</span><span class="sxs-lookup"><span data-stu-id="bdacd-117">**Import**</span></span>|<span data-ttu-id="bdacd-118">從檔案或報表匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="bdacd-118">Import an existing query from a file or report.</span></span> <span data-ttu-id="bdacd-119">只支援 sql 和 rdl 檔案類型。</span><span class="sxs-lookup"><span data-stu-id="bdacd-119">Only file types sql and rdl are supported.</span></span> <span data-ttu-id="bdacd-120">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bdacd-120">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>|
|<span data-ttu-id="bdacd-121">![執行查詢](../analysis-services/media/rsqdicon-run.gif "執行查詢")</span><span class="sxs-lookup"><span data-stu-id="bdacd-121">![Run the query](../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="bdacd-122">執行查詢，並將結果集顯示在 [結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="bdacd-122">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="bdacd-123">**命令類型**</span><span class="sxs-lookup"><span data-stu-id="bdacd-123">**Command Type**</span></span>|<span data-ttu-id="bdacd-124">選取 [Text]、[StoredProcedure] 或 [TableDirect]。</span><span class="sxs-lookup"><span data-stu-id="bdacd-124">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="bdacd-125">如果預存程序含有參數，當您按一下工具列上的 [執行] 時，便會顯示 [定義查詢參數] 對話方塊，您可以依照需要填入值。</span><span class="sxs-lookup"><span data-stu-id="bdacd-125">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span> <span data-ttu-id="bdacd-126">請注意，如果預存程式傳回一個以上的結果集，則只會使用第一個結果集來填入資料集。</span><span class="sxs-lookup"><span data-stu-id="bdacd-126">Note that if a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span><br /><br /> <span data-ttu-id="bdacd-127">對於命令類型的支援會依資料來源類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="bdacd-127">Support for command type varies by data source type.</span></span> <span data-ttu-id="bdacd-128">例如，只有 OLE DB 和 ODBC 支援 [TableDirect]。</span><span class="sxs-lookup"><span data-stu-id="bdacd-128">For example, only OLE DB and ODBC support **TableDirect**.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="bdacd-129">Text 命令類型</span><span class="sxs-lookup"><span data-stu-id="bdacd-129">Command Type Text</span></span>
 <span data-ttu-id="bdacd-130">當您建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料集時，報表設計師預設會顯示圖形化查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="bdacd-130">When you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dataset, Report Designer displays the graphical query designer by default.</span></span> <span data-ttu-id="bdacd-131">若要切換到文字型查詢設計工具，請按一下工具列上的 [當成文字編輯] 切換按鈕。</span><span class="sxs-lookup"><span data-stu-id="bdacd-131">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="bdacd-132">以文字為基礎的查詢設計工具會顯示兩個窗格：[查詢] 窗格和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="bdacd-132">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="bdacd-133">下圖會標示出各個窗格。</span><span class="sxs-lookup"><span data-stu-id="bdacd-133">The following figure labels each pane.</span></span>

 <span data-ttu-id="bdacd-134">![一般查詢設計工具，適用於關聯式資料查詢](../analysis-services/media/rsqd-dsaw-sql-generic.gif "一般查詢設計工具，適用於關聯式資料查詢")</span><span class="sxs-lookup"><span data-stu-id="bdacd-134">![Generic query designer, for relational data query](../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="bdacd-135">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="bdacd-135">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="bdacd-136">窗格</span><span class="sxs-lookup"><span data-stu-id="bdacd-136">Pane</span></span>|<span data-ttu-id="bdacd-137">函式</span><span class="sxs-lookup"><span data-stu-id="bdacd-137">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="bdacd-138">查詢</span><span class="sxs-lookup"><span data-stu-id="bdacd-138">Query</span></span>|<span data-ttu-id="bdacd-139">顯示 [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢文字。</span><span class="sxs-lookup"><span data-stu-id="bdacd-139">Displays the [!INCLUDE[tsql](../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="bdacd-140">使用此窗格，即可撰寫或編輯 [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="bdacd-140">Use this pane to write or edit a [!INCLUDE[tsql](../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="bdacd-141">結果</span><span class="sxs-lookup"><span data-stu-id="bdacd-141">Result</span></span>|<span data-ttu-id="bdacd-142">顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="bdacd-142">Displays the results of the query.</span></span> <span data-ttu-id="bdacd-143">若要執行查詢，請以滑鼠右鍵按一下任何窗格，然後按一下 [執行]，或是按一下工具列上的 [執行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bdacd-143">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="bdacd-144">範例</span><span class="sxs-lookup"><span data-stu-id="bdacd-144">Example</span></span>
 <span data-ttu-id="bdacd-145">下列查詢會從 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫的 `Contact` 資料表傳回姓氏清單。</span><span class="sxs-lookup"><span data-stu-id="bdacd-145">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database `Contact` table.</span></span>

```
SELECT LastName FROM Person.Person;
```

 <span data-ttu-id="bdacd-146">您可以使用 Text 命令類型的任何 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式，包括 `EXEC` 陳述式在內。</span><span class="sxs-lookup"><span data-stu-id="bdacd-146">You can use any [!INCLUDE[tsql](../includes/tsql-md.md)] statement for Command type Text, including `EXEC` statements.</span></span> <span data-ttu-id="bdacd-147">下列查詢會呼叫 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 預存程式 `uspGetEmployeeManagers` ，並傳回識別碼為1之員工的命令鏈。</span><span class="sxs-lookup"><span data-stu-id="bdacd-147">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers` and returns the chain-of-command for the employee with identification number 1.</span></span>

```
EXEC uspGetEmployeeManagers 1;
```

 <span data-ttu-id="bdacd-148">當您按一下工具列上的 [執行] 時，[查詢] 窗格中的命令便會執行，而且結果會顯示在 [結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="bdacd-148">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="bdacd-149">StoredProcedure 命令類型</span><span class="sxs-lookup"><span data-stu-id="bdacd-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="bdacd-150">當您選取 [命令類型] [StoredProcedure] 時，文字型查詢設計工具會顯示兩個窗格：[查詢] 窗格和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="bdacd-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="bdacd-151">請在 [查詢] 窗格內輸入預存程序名稱，然後按一下工具列上的 [執行]。</span><span class="sxs-lookup"><span data-stu-id="bdacd-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="bdacd-152">[定義查詢參數] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="bdacd-152">The Define Query Parameters dialog box opens.</span></span> <span data-ttu-id="bdacd-153">為此預存程序輸入參數值。</span><span class="sxs-lookup"><span data-stu-id="bdacd-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="bdacd-154">將會針對每一個預存程序參數建立報表參數。</span><span class="sxs-lookup"><span data-stu-id="bdacd-154">A report parameter is created for every stored procedure parameter.</span></span>

#### <a name="example"></a><span data-ttu-id="bdacd-155">範例</span><span class="sxs-lookup"><span data-stu-id="bdacd-155">Example</span></span>
 <span data-ttu-id="bdacd-156">下列查詢會呼叫 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 預存程序 `uspGetEmployeeManagers`。</span><span class="sxs-lookup"><span data-stu-id="bdacd-156">The following query calls the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] stored procedure `uspGetEmployeeManagers`.</span></span> <span data-ttu-id="bdacd-157">當您執行查詢時，必須為員工識別碼參數輸入值。</span><span class="sxs-lookup"><span data-stu-id="bdacd-157">You must enter a value for the employee identification number parameter when you run the query.</span></span>

```
uspGetEmployeeManagers;
```

### <a name="command-type-tabledirect"></a><span data-ttu-id="bdacd-158">TableDirect 命令類型</span><span class="sxs-lookup"><span data-stu-id="bdacd-158">Command Type TableDirect</span></span>
 <span data-ttu-id="bdacd-159">當您選取 [命令類型] [TableDirect] 時，文字型查詢設計工具會顯示兩個窗格：[查詢] 窗格和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="bdacd-159">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="bdacd-160">當您輸入資料表並按一下 [執行] 按鈕時，便會傳回該資料表的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="bdacd-160">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="bdacd-161">範例</span><span class="sxs-lookup"><span data-stu-id="bdacd-161">Example</span></span>
 <span data-ttu-id="bdacd-162">下列查詢會傳回 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 資料庫中所有客戶的結果集。</span><span class="sxs-lookup"><span data-stu-id="bdacd-162">The following query returns a result set for all customers in the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>

 `Sales.Customer`

 <span data-ttu-id="bdacd-163">當您輸入資料表名稱 Sales. Customer 時，它就相當於建立 [!INCLUDE[tsql](../includes/tsql-md.md)] 語句 `SELECT * FROM Sales.Customer;` 。</span><span class="sxs-lookup"><span data-stu-id="bdacd-163">When you enter the table name Sales.Customer, it is the equivalent of creating the [!INCLUDE[tsql](../includes/tsql-md.md)] statement `SELECT * FROM Sales.Customer;`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdacd-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdacd-164">See Also</span></span>
 <span data-ttu-id="bdacd-165">[報表設計師 SQL Server Data Tools 中的查詢設計工具 &#40;ssrs&#41;](report-data/query-design-tools-ssrs.md) [報表內嵌資料集和共用資料集 &#40;報表產生器和 ssrs](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)&#41;ssrs SQL Server &#40;的連線類型&#41;[ssrs OLE DB](report-data/ole-db-connection-type-ssrs.md) [ODBC 連接](report-data/odbc-connection-type-ssrs.md)類型 &#40;Ssrs [&#41;&#40;](report-data/sql-server-connection-type-ssrs.md) [報表內嵌資料集和共用資料集&#41;&#40;和 ssrs 報表產生器](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [rsreportdesigner.config 設定檔](report-server/rsreportdesigner-configuration-file.md)</span><span class="sxs-lookup"><span data-stu-id="bdacd-165">[Query Design Tools in Report Designer SQL Server Data Tools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [SQL Server Connection Type &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md) [OLE DB Connection Type &#40;SSRS&#41;](report-data/ole-db-connection-type-ssrs.md) [ODBC Connection Type &#40;SSRS&#41;](report-data/odbc-connection-type-ssrs.md) [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) [RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md)</span></span>


