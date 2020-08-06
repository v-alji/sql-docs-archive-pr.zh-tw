---
title: 文字型查詢設計工具使用者介面 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10010"
helpviewer_keywords:
- query designers, text-based
ms.assetid: 89fddca5-bd96-4128-9072-5348d1b6e02c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c1415bdfada46ac09c9ab04047d63484593933e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585057"
---
# <a name="text-based-query-designer-user-interface-report-builder"></a><span data-ttu-id="1165d-102">以文字為基礎的查詢設計工具使用者介面 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="1165d-102">Text-based Query Designer User Interface (Report Builder)</span></span>
  <span data-ttu-id="1165d-103">使用以文字為基礎的查詢設計工具，可透過資料來源支援的查詢語言來指定查詢、執行查詢，並在設計階段檢視結果。</span><span class="sxs-lookup"><span data-stu-id="1165d-103">Use the text-based query designer to specify a query using the query language supported by the data source, run the query, and view the results at design time.</span></span> <span data-ttu-id="1165d-104">您可以指定多個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式、自訂資料處理延伸模組的查詢或命令語法，以及指定為運算式的查詢。</span><span class="sxs-lookup"><span data-stu-id="1165d-104">You can specify multiple [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="1165d-105">以文字為基礎的查詢設計工具不會前置處理查詢，而且可以容納各種查詢語法，所以這是許多資料來源類型的預設查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="1165d-105">Because the text-based query designer does not preprocess the query and can accommodate any kind of query syntax, this is the default query designer tool for many data source types.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="1165d-106">當使用者建立與執行查詢時，可以存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="1165d-106">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="1165d-107">您應該授與資料來源的最小權限，例如唯讀權限。</span><span class="sxs-lookup"><span data-stu-id="1165d-107">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>

 <span data-ttu-id="1165d-108">以文字為基礎的查詢設計工具會顯示一個工具列及以下兩個窗格：</span><span class="sxs-lookup"><span data-stu-id="1165d-108">The text-based query designer displays a toolbar and the following two panes:</span></span>

-   <span data-ttu-id="1165d-109">**查詢** ：根據查詢類型顯示查詢文字、資料表名稱或預存程序名稱。</span><span class="sxs-lookup"><span data-stu-id="1165d-109">**Query** Shows the query text, table name, or stored procedure name depending on the query type.</span></span> <span data-ttu-id="1165d-110">並非所有的資料來源類型都提供所有的查詢類型。</span><span class="sxs-lookup"><span data-stu-id="1165d-110">Not all query types are available for all data source types.</span></span> <span data-ttu-id="1165d-111">例如，只有資料來源類型 OLE DB 才支援資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="1165d-111">For example, table name is supported only for the data source type OLE DB.</span></span>

-   <span data-ttu-id="1165d-112">**結果** ：顯示在設計階段執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="1165d-112">**Result** Shows the results of running the query at design time.</span></span>

## <a name="text-based-query-designer-toolbar"></a><span data-ttu-id="1165d-113">以文字為基礎的查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="1165d-113">Text-based Query Designer Toolbar</span></span>
 <span data-ttu-id="1165d-114">以文字為基礎的查詢設計工具為所有的命令類型提供了單一工具列。</span><span class="sxs-lookup"><span data-stu-id="1165d-114">The text-based query designer provides a single toolbar for all the command types.</span></span> <span data-ttu-id="1165d-115">下表列出工具列上的每一個按鈕以及該按鈕的功能。</span><span class="sxs-lookup"><span data-stu-id="1165d-115">The following table lists each button on the toolbar and its function.</span></span>

|<span data-ttu-id="1165d-116">按鈕</span><span class="sxs-lookup"><span data-stu-id="1165d-116">Button</span></span>|<span data-ttu-id="1165d-117">描述</span><span class="sxs-lookup"><span data-stu-id="1165d-117">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="1165d-118">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="1165d-118">**Edit As Text**</span></span>|<span data-ttu-id="1165d-119">在以文字為基礎的查詢設計工具和圖形化查詢設計工具之間切換。</span><span class="sxs-lookup"><span data-stu-id="1165d-119">Toggle between the text-based query designer and the graphical query designer.</span></span> <span data-ttu-id="1165d-120">並非所有的資料來源類型都支援圖形化查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="1165d-120">Not all data source types support graphical query designers.</span></span>|
|<span data-ttu-id="1165d-121">**匯入**</span><span class="sxs-lookup"><span data-stu-id="1165d-121">**Import**</span></span>|<span data-ttu-id="1165d-122">從檔案或報表匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="1165d-122">Import an existing query from a file or report.</span></span> <span data-ttu-id="1165d-123">只支援 sql 和 rdl 檔案類型</span><span class="sxs-lookup"><span data-stu-id="1165d-123">Only file types sql and rdl are supported</span></span>|
|<span data-ttu-id="1165d-124">![執行查詢](../../analysis-services/media/rsqdicon-run.gif "執行查詢")</span><span class="sxs-lookup"><span data-stu-id="1165d-124">![Run the query](../../analysis-services/media/rsqdicon-run.gif "Run the query")</span></span>|<span data-ttu-id="1165d-125">執行查詢，並將結果集顯示在 [結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="1165d-125">Run the query and display the result set in the Result pane.</span></span>|
|<span data-ttu-id="1165d-126">**命令類型**</span><span class="sxs-lookup"><span data-stu-id="1165d-126">**Command Type**</span></span>|<span data-ttu-id="1165d-127">選取 [Text]、[StoredProcedure] 或 [TableDirect]。</span><span class="sxs-lookup"><span data-stu-id="1165d-127">Select **Text**, **StoredProcedure**, or **TableDirect**.</span></span> <span data-ttu-id="1165d-128">如果預存程序含有參數，當您按一下工具列上的 [執行] 時，便會顯示 [定義查詢參數] 對話方塊，您可以依照需要填入值。</span><span class="sxs-lookup"><span data-stu-id="1165d-128">If a stored procedure has parameters, the **Define Query Parameters** dialog box appears when you click **Run** on the toolbar, and you can fill in values as needed.</span></span><br /><br /> <span data-ttu-id="1165d-129">注意:如果預存程序傳回一個以上的結果集，則只會使用第一個結果集來填入資料集。</span><span class="sxs-lookup"><span data-stu-id="1165d-129">Note: If a stored procedure returns more than one result set, only the first result set is used to populate the dataset.</span></span>|

### <a name="command-type-text"></a><span data-ttu-id="1165d-130">Text 命令類型</span><span class="sxs-lookup"><span data-stu-id="1165d-130">Command Type Text</span></span>
 <span data-ttu-id="1165d-131">當您建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料集時，預設會開啟關聯式查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="1165d-131">When you create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dataset, the relational query designer opens by default.</span></span> <span data-ttu-id="1165d-132">若要切換到文字型查詢設計工具，請按一下工具列上的 [當成文字編輯] 切換按鈕。</span><span class="sxs-lookup"><span data-stu-id="1165d-132">To switch to the text-based query designer, click the **Edit As Text** toggle button on the toolbar.</span></span> <span data-ttu-id="1165d-133">以文字為基礎的查詢設計工具會顯示兩個窗格：[查詢] 窗格和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1165d-133">The text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="1165d-134">下圖會標示出各個窗格。</span><span class="sxs-lookup"><span data-stu-id="1165d-134">The following figure labels each pane.</span></span>

 <span data-ttu-id="1165d-135">![一般查詢設計工具，適用於關聯式資料查詢](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "一般查詢設計工具，適用於關聯式資料查詢")</span><span class="sxs-lookup"><span data-stu-id="1165d-135">![Generic query designer, for relational data query](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "Generic query designer, for relational data query")</span></span>

 <span data-ttu-id="1165d-136">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="1165d-136">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="1165d-137">窗格</span><span class="sxs-lookup"><span data-stu-id="1165d-137">Pane</span></span>|<span data-ttu-id="1165d-138">函式</span><span class="sxs-lookup"><span data-stu-id="1165d-138">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="1165d-139">查詢</span><span class="sxs-lookup"><span data-stu-id="1165d-139">Query</span></span>|<span data-ttu-id="1165d-140">顯示 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢文字。</span><span class="sxs-lookup"><span data-stu-id="1165d-140">Displays the [!INCLUDE[tsql](../../../includes/tsql-md.md)] query text.</span></span> <span data-ttu-id="1165d-141">使用此窗格，即可撰寫或編輯 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="1165d-141">Use this pane to write or edit a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query.</span></span>|
|<span data-ttu-id="1165d-142">結果</span><span class="sxs-lookup"><span data-stu-id="1165d-142">Result</span></span>|<span data-ttu-id="1165d-143">顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="1165d-143">Displays the results of the query.</span></span> <span data-ttu-id="1165d-144">若要執行查詢，請以滑鼠右鍵按一下任何窗格，然後按一下 [執行]，或是按一下工具列上的 [執行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1165d-144">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="1165d-145">範例</span><span class="sxs-lookup"><span data-stu-id="1165d-145">Example</span></span>
 <span data-ttu-id="1165d-146">下列查詢會從架構的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008**資料庫資料表中傳回姓氏清單 `ContactType` `Person` 。</span><span class="sxs-lookup"><span data-stu-id="1165d-146">The following query returns the list of last names from the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database `ContactType` table for the `Person` schema.</span></span>

```
SELECT Name FROM Person.ContactType
```

 <span data-ttu-id="1165d-147">當您按一下工具列上的 [執行] 時，[查詢] 窗格中的命令便會執行，而且結果會顯示在 [結果] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="1165d-147">When you click **Run** on the toolbar, the command in the **Query** pane runs and the results are displayed in the **Result** pane.</span></span> <span data-ttu-id="1165d-148">結果集會顯示 20 種連絡人類型的清單，例如「擁有者」或「銷售代理人」。</span><span class="sxs-lookup"><span data-stu-id="1165d-148">The resultset displays a list of 20 types of contacts, for example, Owner or Sales Agent.</span></span>

### <a name="command-type-storedprocedure"></a><span data-ttu-id="1165d-149">StoredProcedure 命令類型</span><span class="sxs-lookup"><span data-stu-id="1165d-149">Command Type StoredProcedure</span></span>
 <span data-ttu-id="1165d-150">當您選取 [命令類型] [StoredProcedure] 時，文字型查詢設計工具會顯示兩個窗格：[查詢] 窗格和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1165d-150">When you select **Command typeStoredProcedure**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="1165d-151">請在 [查詢] 窗格內輸入預存程序名稱，然後按一下工具列上的 [執行]。</span><span class="sxs-lookup"><span data-stu-id="1165d-151">Enter the stored procedure name in the Query pane and click **Run** on the toolbar.</span></span> <span data-ttu-id="1165d-152">如果預存程序使用參數，[定義查詢參數] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1165d-152">If the stored procedures uses parameters, the **Define Query Parameters** dialog box opens.</span></span> <span data-ttu-id="1165d-153">為此預存程序輸入參數值。</span><span class="sxs-lookup"><span data-stu-id="1165d-153">Enter the parameter values for the stored procedure.</span></span> <span data-ttu-id="1165d-154">系統將會針對每一個預存程序輸入參數建立報表參數。</span><span class="sxs-lookup"><span data-stu-id="1165d-154">A report parameter is created for every stored procedure input parameter.</span></span>

 <span data-ttu-id="1165d-155">下圖會在您執行預存程序時，顯示 [查詢] 和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1165d-155">The following figure shows the Query and Results panes when you run a stored procedure.</span></span> <span data-ttu-id="1165d-156">在此情況下，輸入參數是常數。</span><span class="sxs-lookup"><span data-stu-id="1165d-156">In this case, the input parameters are constants.</span></span>

 <span data-ttu-id="1165d-157">![在以文字為基礎查詢設計工具中的預存程序](../../analysis-services/media/rs-relational-text-sp.gif "在以文字為基礎查詢設計工具中的預存程序")</span><span class="sxs-lookup"><span data-stu-id="1165d-157">![Stored procedure in text-based query designer](../../analysis-services/media/rs-relational-text-sp.gif "Stored procedure in text-based query designer")</span></span>

 <span data-ttu-id="1165d-158">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="1165d-158">The following table describes the function of each pane.</span></span>

|<span data-ttu-id="1165d-159">窗格</span><span class="sxs-lookup"><span data-stu-id="1165d-159">Pane</span></span>|<span data-ttu-id="1165d-160">函式</span><span class="sxs-lookup"><span data-stu-id="1165d-160">Function</span></span>|
|----------|--------------|
|<span data-ttu-id="1165d-161">查詢</span><span class="sxs-lookup"><span data-stu-id="1165d-161">Query</span></span>|<span data-ttu-id="1165d-162">顯示預存程序的名稱以及任何輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1165d-162">Displays the name of the stored procedure and any input parameters.</span></span>|
|<span data-ttu-id="1165d-163">結果</span><span class="sxs-lookup"><span data-stu-id="1165d-163">Result</span></span>|<span data-ttu-id="1165d-164">顯示查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="1165d-164">Displays the results of the query.</span></span> <span data-ttu-id="1165d-165">若要執行查詢，請以滑鼠右鍵按一下任何窗格，然後按一下 [執行]，或是按一下工具列上的 [執行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1165d-165">To run the query, right-click in any pane and click **Run**, or click the **Run** button on the toolbar.</span></span>|

#### <a name="example"></a><span data-ttu-id="1165d-166">範例</span><span class="sxs-lookup"><span data-stu-id="1165d-166">Example</span></span>
 <span data-ttu-id="1165d-167">下列查詢會呼叫 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008**預存程式 `uspGetWhereUsedProductID` 。</span><span class="sxs-lookup"><span data-stu-id="1165d-167">The following query calls the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** stored procedure `uspGetWhereUsedProductID`.</span></span> <span data-ttu-id="1165d-168">當您執行查詢時，必須為產品識別碼參數輸入值。</span><span class="sxs-lookup"><span data-stu-id="1165d-168">You must enter a value for the product identification number parameter when you run the query.</span></span>

```
uspGetWhereUsedProductID
```

 <span data-ttu-id="1165d-169">按一下 [執行] \( **!** ) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1165d-169">Click the **Run** (**!**) button.</span></span> <span data-ttu-id="1165d-170">提示輸入查詢參數時，請使用下表來輸入值。</span><span class="sxs-lookup"><span data-stu-id="1165d-170">When prompted for the query parameters, use the following table to enter values.</span></span>

|||
|-|-|
|*@StartProductID*|<span data-ttu-id="1165d-171">820</span><span class="sxs-lookup"><span data-stu-id="1165d-171">820</span></span>|
|*@CheckDate*|<span data-ttu-id="1165d-172">20010115</span><span class="sxs-lookup"><span data-stu-id="1165d-172">20010115</span></span>|

 <span data-ttu-id="1165d-173">對於指定的日期，結果集會顯示 13 個產品識別碼 (使用指定的元件編號) 的清單。</span><span class="sxs-lookup"><span data-stu-id="1165d-173">For the specified date, the result set displays a list of 13 product identifiers that used the specified component number.</span></span>

### <a name="command-type-tabledirect"></a><span data-ttu-id="1165d-174">TableDirect 命令類型</span><span class="sxs-lookup"><span data-stu-id="1165d-174">Command Type TableDirect</span></span>
 <span data-ttu-id="1165d-175">當您選取 [命令類型] [TableDirect] 時，文字型查詢設計工具會顯示兩個窗格：[查詢] 窗格和 [結果] 窗格。</span><span class="sxs-lookup"><span data-stu-id="1165d-175">When you select **Command typeTableDirect**, the text-based query designer presents two panes: the Query pane and the Result pane.</span></span> <span data-ttu-id="1165d-176">當您輸入資料表並按一下 [執行] 按鈕時，便會傳回該資料表的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="1165d-176">When you enter a table and click the **Run** button, all the columns for that table are returned.</span></span>

#### <a name="example"></a><span data-ttu-id="1165d-177">範例</span><span class="sxs-lookup"><span data-stu-id="1165d-177">Example</span></span>
 <span data-ttu-id="1165d-178">針對 OLE DB 的資料來源類型，下列資料集查詢會傳回2008資料庫中所有連絡人類型的結果集 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] **2008** 。</span><span class="sxs-lookup"><span data-stu-id="1165d-178">For a data source type OLE DB, the following dataset query returns a result set for all contact types in the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]**2008** database.</span></span>

 `Person.ContactType`

 <span data-ttu-id="1165d-179">當您輸入資料表名稱 Person.ContactType 時，就等於建立 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式 `SELECT * FROM Person.ContactType`。</span><span class="sxs-lookup"><span data-stu-id="1165d-179">When you enter the table name Person.ContactType, it is the equivalent of creating the [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement `SELECT * FROM Person.ContactType`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1165d-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1165d-180">See Also</span></span>
 <span data-ttu-id="1165d-181">[關聯式查詢設計工具使用者介面 &#40;報表產生器&#41;](relational-query-designer-user-interface-report-builder.md) [查詢設計工具 &#40;報表產生器&#41;](../query-designers-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="1165d-181">[Relational Query Designer User Interface &#40;Report Builder&#41;](relational-query-designer-user-interface-report-builder.md) [Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md)</span></span>


