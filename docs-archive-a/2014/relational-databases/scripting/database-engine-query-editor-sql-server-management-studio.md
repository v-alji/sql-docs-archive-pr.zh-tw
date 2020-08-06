---
title: Database Engine 查詢編輯器
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.tsqlquery.f1
dev_langs:
- TSQL
helpviewer_keywords:
- Query Editor [Database Engine]
- Transact-SQL Editor See Query Editor [Database Engine]
- Database Engine Query Editor See Query Editor [Database Engine]
- Query Editor [Database Engine], Toolbar
- editors [SQL Server Management Studio], Database Engine Query Editor
- Query Editor [Database Engine], Features
- SQL Server Management Studio [SQL Server], Database Engine Query Editor
ms.assetid: 05cfae9b-96d5-4a35-a098-0bc3a548bcfc
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dcb4298ec55181ea3c979228e8decf681483f74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584372"
---
# <a name="database-engine-query-editor-sql-server-management-studio"></a><span data-ttu-id="f2284-102">Database Engine 查詢編輯器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="f2284-102">Database Engine Query Editor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="f2284-103">使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器，建立及執行包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f2284-103">Use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to create and run scripts containing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="f2284-104">此編輯器也支援執行包含 **sqlcmd** 命令的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f2284-104">The editor also supports running scripts that contain **sqlcmd** commands.</span></span>  
  
## <a name="transact-sql-f1-help"></a><span data-ttu-id="f2284-105">Transact-SQL F1 說明</span><span class="sxs-lookup"><span data-stu-id="f2284-105">Transact-SQL F1 Help</span></span>  
 <span data-ttu-id="f2284-106">當您選取 F1 時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器支援將您連結至特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的參考主題。</span><span class="sxs-lookup"><span data-stu-id="f2284-106">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports linking you to the reference topic for a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement when you select F1.</span></span> <span data-ttu-id="f2284-107">若要執行這項操作，請反白顯示 Transact-SQL 陳述式的名稱，然後選取 F1。</span><span class="sxs-lookup"><span data-stu-id="f2284-107">To do so, highlight the name of a Transact-SQL statement and then select F1.</span></span> <span data-ttu-id="f2284-108">接著，說明搜尋引擎會搜尋具有符合您反白顯示的字串之 F1 說明屬性的主題。</span><span class="sxs-lookup"><span data-stu-id="f2284-108">The help search engine will then search for a topic that has an F1 help attribute that matches the string you highlighted.</span></span>  
  
 <span data-ttu-id="f2284-109">如果說明搜尋引擎找不到具有完全符合您反白顯示的字串之 F1 說明關鍵字的主題，則會顯示此主題。</span><span class="sxs-lookup"><span data-stu-id="f2284-109">If the help search engine does not find a topic with an F1 help keyword that exactly matches the string you highlighted, then this topic is displayed.</span></span> <span data-ttu-id="f2284-110">在這種情況下，有兩種方法可以找到您正在尋找的說明：</span><span class="sxs-lookup"><span data-stu-id="f2284-110">In that case, there are two approaches to finding the help you are looking for:</span></span>  
  
-   <span data-ttu-id="f2284-111">複製您反白顯示的編輯器字串，並將它貼入《SQL Server 線上叢書》的 [搜尋] 索引標籤，然後進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="f2284-111">Copy and paste the editor string you highlighted into the search tab of SQL Server Books Online and do a search.</span></span>  
  
-   <span data-ttu-id="f2284-112">僅反白顯示 Transact-SQL 陳述式可能符合套用至主題之 F1 說明關鍵字的部分，然後再次選取 F1。</span><span class="sxs-lookup"><span data-stu-id="f2284-112">Highlight only the part of the Transact-SQL statement likely to match an F1 help keyword applied to a topic and select F1 again.</span></span> <span data-ttu-id="f2284-113">搜尋引擎要求您反白顯示的字串與指派給主題的 F1 說明關鍵字完全相符。</span><span class="sxs-lookup"><span data-stu-id="f2284-113">The search engine requires an exact match between the string you highlighted and an F1 help keyword assigned to a topic.</span></span> <span data-ttu-id="f2284-114">如果您反白顯示的字串包含環境獨有的元素 (例如資料行或參數名稱)，搜尋引擎不會產生符合的結果。</span><span class="sxs-lookup"><span data-stu-id="f2284-114">If the string you highlighted contains elements unique to your environment, such as column or parameter names, the search engine will not get a match.</span></span> <span data-ttu-id="f2284-115">反白顯示的字串範例包括：</span><span class="sxs-lookup"><span data-stu-id="f2284-115">Examples of the strings to highlight include:</span></span>  
  
    -   <span data-ttu-id="f2284-116">Transact-SQL 陳述式的名稱，例如 SELECT、CREATE DATABASE 或 BEGIN TRANSACTION。</span><span class="sxs-lookup"><span data-stu-id="f2284-116">The name of a Transact-SQL statement, such as SELECT, CREATE DATABASE or BEGIN TRANSACTION.</span></span>  
  
    -   <span data-ttu-id="f2284-117">內建函數的名稱，例如 SERVERPROPERTY 或 @@VERSION。</span><span class="sxs-lookup"><span data-stu-id="f2284-117">The name of a built-in function, such as SERVERPROPERTY, or @@VERSION.</span></span>  
  
    -   <span data-ttu-id="f2284-118">系統預存程序資料表的名稱，或是檢視表，例如 sys.data_spaces 或 sp_tableoption。</span><span class="sxs-lookup"><span data-stu-id="f2284-118">The name of a system stored procedure table, or view, such as sys.data_spaces or sp_tableoption.</span></span>  
  
## <a name="working-with-the-database-engine-query-editor"></a><span data-ttu-id="f2284-119">使用 Database Engine 查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="f2284-119">Working With the Database Engine Query Editor</span></span>  
 <span data-ttu-id="f2284-120">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器是在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中實作的四個編輯器之一。</span><span class="sxs-lookup"><span data-stu-id="f2284-120">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is one of four editors implemented in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f2284-121">如需在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中實作之功能及您可以使用編輯器執行之主要工作的描述，請參閱[查詢與文字編輯器 &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="f2284-121">For a description of the functionality implemented in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor and the main tasks you can perform using the editor, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="f2284-122">SQL 編輯器工具列</span><span class="sxs-lookup"><span data-stu-id="f2284-122">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="f2284-123">當 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器開啟時，SQL 編輯器工具列會顯示下列按鈕。</span><span class="sxs-lookup"><span data-stu-id="f2284-123">When the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor is open, the SQL Editor toolbar appears with the following buttons.</span></span>  
  
 <span data-ttu-id="f2284-124">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="f2284-124">**Connect**</span></span>  
 <span data-ttu-id="f2284-125">隨即開啟 [連接到伺服器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2284-125">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="f2284-126">使用此對話方塊可建立與伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="f2284-126">Use this dialog box to establish a connection to a server.</span></span>  
  
 <span data-ttu-id="f2284-127">**中斷連線**</span><span class="sxs-lookup"><span data-stu-id="f2284-127">**Disconnect**</span></span>  
 <span data-ttu-id="f2284-128">中斷目前查詢編輯器的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="f2284-128">Disconnects the current Query Editor from the server.</span></span>  
  
 <span data-ttu-id="f2284-129">**變更連接**</span><span class="sxs-lookup"><span data-stu-id="f2284-129">**Change Connection**</span></span>  
 <span data-ttu-id="f2284-130">隨即開啟 [連接到伺服器]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2284-130">Opens the **Connect to Server** dialog box.</span></span> <span data-ttu-id="f2284-131">使用此對話方塊可建立與不同伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="f2284-131">Use this dialog box to establish a connection to a different server.</span></span>  
  
 <span data-ttu-id="f2284-132">**使用目前的連接新增查詢**</span><span class="sxs-lookup"><span data-stu-id="f2284-132">**New Query with Current Connection**</span></span>  
 <span data-ttu-id="f2284-133">開新的 [查詢編輯器] 視窗，並使用目前 [查詢編輯器] 視窗中的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="f2284-133">Opens a new Query Editor window and uses the connection information from the current Query Editor window.</span></span>  
  
 <span data-ttu-id="f2284-134">**可用的資料庫**</span><span class="sxs-lookup"><span data-stu-id="f2284-134">**Available Databases**</span></span>  
 <span data-ttu-id="f2284-135">變更連接到同一伺服器的其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="f2284-135">Change the connection to a different database on the same server.</span></span>  
  
 <span data-ttu-id="f2284-136">**執行**</span><span class="sxs-lookup"><span data-stu-id="f2284-136">**Execute**</span></span>  
 <span data-ttu-id="f2284-137">執行選取的程式碼，或是在未選取任何程式碼時，執行查詢編輯器中的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2284-137">Executes the selected code or, if no code is selected, executes all the code in the Query Editor.</span></span>  
  
 <span data-ttu-id="f2284-138">**偵錯**</span><span class="sxs-lookup"><span data-stu-id="f2284-138">**Debug**</span></span>  
 <span data-ttu-id="f2284-139">啟用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f2284-139">Enables the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="f2284-140">此偵錯工具支援偵錯動作，例如設定中斷點、監看變數及逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2284-140">This debugger supports debugging actions such as setting breakpoints, watching variables, and stepping through code.</span></span>  
  
 <span data-ttu-id="f2284-141">**取消執行查詢**</span><span class="sxs-lookup"><span data-stu-id="f2284-141">**Cancel Executing Query**</span></span>  
 <span data-ttu-id="f2284-142">將取消要求傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f2284-142">Sends a cancellation request to the server.</span></span> <span data-ttu-id="f2284-143">部份查詢無法立即取消，必須等候適當的取消條件。</span><span class="sxs-lookup"><span data-stu-id="f2284-143">Some queries cannot be canceled immediately, but must wait for a suitable cancellation condition.</span></span> <span data-ttu-id="f2284-144">當取消交易之後，交易回復時可能產生延遲。</span><span class="sxs-lookup"><span data-stu-id="f2284-144">When transactions are canceled, delays might occur while transactions are rolled back.</span></span>  
  
 <span data-ttu-id="f2284-145">**剖析**</span><span class="sxs-lookup"><span data-stu-id="f2284-145">**Parse**</span></span>  
 <span data-ttu-id="f2284-146">檢查選取之程式碼的語法。</span><span class="sxs-lookup"><span data-stu-id="f2284-146">Check the syntax of the selected code.</span></span> <span data-ttu-id="f2284-147">如果未選取任何程式碼，則會檢查 [查詢編輯器] 視窗中所有程式碼的語法。</span><span class="sxs-lookup"><span data-stu-id="f2284-147">If no code is selected, checks the syntax of the all code in the Query Editor window.</span></span>  
  
 <span data-ttu-id="f2284-148">**顯示估計執行計畫**</span><span class="sxs-lookup"><span data-stu-id="f2284-148">**Display Estimated Execution Plan**</span></span>  
 <span data-ttu-id="f2284-149">在未實際執行查詢的情況下，向查詢處理器要求查詢執行計畫，並且將計畫顯示在 [執行計畫]  視窗中。</span><span class="sxs-lookup"><span data-stu-id="f2284-149">Requests a query execution plan from the query processor without actually executing the query, and displays the plan in the **Execution plan** window.</span></span> <span data-ttu-id="f2284-150">此計畫會使用索引統計資料，當做執行查詢時，每個部分預期將傳回的預估資料列數。</span><span class="sxs-lookup"><span data-stu-id="f2284-150">This plan uses index statistics as an estimate of the number of rows that are expected to be returned during each part of the query execution.</span></span> <span data-ttu-id="f2284-151">使用的實際查詢計劃可以與預估的執行計畫不同。</span><span class="sxs-lookup"><span data-stu-id="f2284-151">The actual query plan that is used can be different from the estimated execution plan.</span></span> <span data-ttu-id="f2284-152">如果傳回的資料列數與預估的資料列數差異極大，而且查詢處理器為了要提高效率而變更計畫時，就可能發生這個情況。</span><span class="sxs-lookup"><span data-stu-id="f2284-152">This can occur if the number of rows that are returned is significantly different from the estimate, and the query processor changes the plan to be more efficient.</span></span>  
  
 <span data-ttu-id="f2284-153">**查詢選項**</span><span class="sxs-lookup"><span data-stu-id="f2284-153">**Query Options**</span></span>  
 <span data-ttu-id="f2284-154">隨即開啟 [查詢選項]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2284-154">Opens the **Query Options** dialog box.</span></span> <span data-ttu-id="f2284-155">使用此對話方塊可設定查詢執行與查詢結果的預設選項。</span><span class="sxs-lookup"><span data-stu-id="f2284-155">Use this dialog box to configure the default options for query execution and for query results.</span></span>  
  
 <span data-ttu-id="f2284-156">**啟用 IntelliSense**</span><span class="sxs-lookup"><span data-stu-id="f2284-156">**IntelliSense Enabled**</span></span>  
 <span data-ttu-id="f2284-157">指定 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中是否有提供 IntelliSense 功能。</span><span class="sxs-lookup"><span data-stu-id="f2284-157">Specifies whether IntelliSense functionality is available in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="f2284-158">**包括實際執行計畫**</span><span class="sxs-lookup"><span data-stu-id="f2284-158">**Include Actual Execution Plan**</span></span>  
 <span data-ttu-id="f2284-159">執行查詢、傳回查詢結果以及查詢使用的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="f2284-159">Executes the query, returns the query results, and the execution plan that was used for the query.</span></span> <span data-ttu-id="f2284-160">這些會當做圖形化查詢計劃出現在 **[執行計畫]** 視窗中。</span><span class="sxs-lookup"><span data-stu-id="f2284-160">These appear as a graphical query plan in the **Execution plan** window.</span></span>  
  
 <span data-ttu-id="f2284-161">**包括用戶端統計資料**</span><span class="sxs-lookup"><span data-stu-id="f2284-161">**Include Client Statistics**</span></span>  
 <span data-ttu-id="f2284-162">包括 [用戶端統計資料]  視窗，其中包含關於查詢、網路封包的統計資料，以及查詢經過的時間。</span><span class="sxs-lookup"><span data-stu-id="f2284-162">Includes a **Client Statistics** window that contains statistics about the query and about the network packets, and the elapsed time of the query.</span></span>  
  
 <span data-ttu-id="f2284-163">**以文字顯示結果**</span><span class="sxs-lookup"><span data-stu-id="f2284-163">**Results to Text**</span></span>  
 <span data-ttu-id="f2284-164">在 [結果]  視窗中以文字傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="f2284-164">Returns the query results as text in the **Results** window.</span></span>  
  
 <span data-ttu-id="f2284-165">**以方格顯示結果**</span><span class="sxs-lookup"><span data-stu-id="f2284-165">**Results to Grid**</span></span>  
 <span data-ttu-id="f2284-166">在 [結果]  視窗中以一或多個方格傳回查詢結果。</span><span class="sxs-lookup"><span data-stu-id="f2284-166">Returns the query results as one or more grids in the **Results** window.</span></span>  
  
 <span data-ttu-id="f2284-167">**將結果存檔**</span><span class="sxs-lookup"><span data-stu-id="f2284-167">**Results to File**</span></span>  
 <span data-ttu-id="f2284-168">執行查詢時，會開啟 [儲存結果]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f2284-168">When the query executes, the **Save Results** dialog box opens.</span></span> <span data-ttu-id="f2284-169">在 **[儲存於]** 中，選取您想要用來儲存檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f2284-169">In **Save In**, select the folder in which you want to save the file.</span></span> <span data-ttu-id="f2284-170">在 **[檔案名稱]** 中輸入檔案的名稱，然後按一下 **[儲存]** ，將查詢結果另存為使用 .rpt 副檔名的 **[報表]** 檔案。</span><span class="sxs-lookup"><span data-stu-id="f2284-170">In **File name**, type the name of the file, and then click **Save** to save the query results as a **Report** file that has the .rpt extension.</span></span> <span data-ttu-id="f2284-171">若要使用進階選項，請按一下 [儲存]\*\*\*\* 按鈕上的向下箭頭，然後按一下 [使用編碼方式儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2284-171">For advanced options, click the down-arrow on the **Save** button, and then click **Save with Encoding**.</span></span>  
  
 <span data-ttu-id="f2284-172">**註解選取範圍**</span><span class="sxs-lookup"><span data-stu-id="f2284-172">**Comment Selection**</span></span>  
 <span data-ttu-id="f2284-173">在行頭加入註解運算子 (--)，將目前的行標示為註解。</span><span class="sxs-lookup"><span data-stu-id="f2284-173">Makes the current line a comment by adding a comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="f2284-174">**取消註解選取範圍**</span><span class="sxs-lookup"><span data-stu-id="f2284-174">**Uncomment Selection**</span></span>  
 <span data-ttu-id="f2284-175">在行頭移除任何註解運算子 (--)，將目前的行標示為使用中的來源陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2284-175">Makes the current line an active source statement by removing any comment operator (--) at the beginning of the line.</span></span>  
  
 <span data-ttu-id="f2284-176">**減少行縮排**</span><span class="sxs-lookup"><span data-stu-id="f2284-176">**Decrease Line Indent**</span></span>  
 <span data-ttu-id="f2284-177">移除行頭的空白，將此行的文字移到左邊。</span><span class="sxs-lookup"><span data-stu-id="f2284-177">Moves the text of the line to the left by removing blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="f2284-178">**增加行縮排**</span><span class="sxs-lookup"><span data-stu-id="f2284-178">**Increase Line Indent**</span></span>  
 <span data-ttu-id="f2284-179">在行頭加入空白，將此行的文字移到右邊。</span><span class="sxs-lookup"><span data-stu-id="f2284-179">Moves the text of the line to the right by adding blanks at the beginning of the line.</span></span>  
  
 <span data-ttu-id="f2284-180">**指定範本參數的值**</span><span class="sxs-lookup"><span data-stu-id="f2284-180">**Specify Values for Template Parameters**</span></span>  
 <span data-ttu-id="f2284-181">開啟一個對話方塊，讓您指定預存程序和函數中之參數的值。</span><span class="sxs-lookup"><span data-stu-id="f2284-181">Opens a dialog box that you can use to specify values for parameters in stored procedures and functions.</span></span>  
  
 <span data-ttu-id="f2284-182">您也可以加入 SQL 編輯器工具列，其方式是選取 **[檢視]** 功能表、選取 **[工具列]** ，然後選取 **[SQL 編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="f2284-182">You can also add the SQL Editor toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **SQL Editor**.</span></span> <span data-ttu-id="f2284-183">如果您在沒有任何 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗開啟時加入 SQL 編輯器工具列，則所有的按鈕都將無法使用。</span><span class="sxs-lookup"><span data-stu-id="f2284-183">If you add the SQL Editor toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
## <a name="sql-editor-toolbar"></a><span data-ttu-id="f2284-184">SQL 編輯器工具列</span><span class="sxs-lookup"><span data-stu-id="f2284-184">SQL Editor Toolbar</span></span>  
 <span data-ttu-id="f2284-185">當開啟 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗時，您可以加入 [偵錯] 工具列，其方式是選取 **[檢視]** 功能表、選取 **[工具列]**，然後選取 **[偵錯]**。</span><span class="sxs-lookup"><span data-stu-id="f2284-185">When a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window is open, you can add the Debug toolbar by selecting the **View** menu, selecting **Toolbars**, and then selecting **Debug**.</span></span> <span data-ttu-id="f2284-186">如果您在沒有任何 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗開啟時加入 [偵錯] 工具列，則所有的按鈕都將無法使用。</span><span class="sxs-lookup"><span data-stu-id="f2284-186">If you add the Debug toolbar when no [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor windows are open, all the buttons are unavailable.</span></span>  
  
 <span data-ttu-id="f2284-187">**繼續**</span><span class="sxs-lookup"><span data-stu-id="f2284-187">**Continue**</span></span>  
 <span data-ttu-id="f2284-188">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗中執行程式碼，直到遇到中斷點為止。</span><span class="sxs-lookup"><span data-stu-id="f2284-188">Runs the code in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window until a breakpoint is encountered.</span></span>  
  
 <span data-ttu-id="f2284-189">**全部中斷**</span><span class="sxs-lookup"><span data-stu-id="f2284-189">**Break All**</span></span>  
 <span data-ttu-id="f2284-190">設定偵錯工具在遇到中斷時，中斷附加偵錯工具的所有處理序。</span><span class="sxs-lookup"><span data-stu-id="f2284-190">Sets the debugger to break all processes to which the debugger is attached when a break occurs.</span></span>  
  
 <span data-ttu-id="f2284-191">**停止調試**</span><span class="sxs-lookup"><span data-stu-id="f2284-191">**Stop Debugging**</span></span>  
 <span data-ttu-id="f2284-192">讓選取的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗移出偵錯模式，並還原標準執行模式。</span><span class="sxs-lookup"><span data-stu-id="f2284-192">Takes the selected [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window out of debug mode, and restores the standard execution mode.</span></span>  
  
 <span data-ttu-id="f2284-193">**顯示下一個陳述式**</span><span class="sxs-lookup"><span data-stu-id="f2284-193">**Show Next Statement**</span></span>  
 <span data-ttu-id="f2284-194">將游標移到下一個要執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2284-194">Moves the cursor to the next statement to be executed.</span></span>  
  
 <span data-ttu-id="f2284-195">**逐步執行**</span><span class="sxs-lookup"><span data-stu-id="f2284-195">**Step Into**</span></span>  
 <span data-ttu-id="f2284-196">系統會執行下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2284-196">The next statement is run.</span></span> <span data-ttu-id="f2284-197">如果此陳述式會叫用 Transact-SQL 預存程序、函數或觸發程序，偵錯工具就會顯示包含模組程式碼的新 [查詢編輯器]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="f2284-197">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the debugger displays a new **Query Editor** window that contains the code of the module.</span></span> <span data-ttu-id="f2284-198">此視窗會處於偵錯模式中，而且執行作業會在模組的第一個陳述式上暫停。</span><span class="sxs-lookup"><span data-stu-id="f2284-198">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="f2284-199">接著，您就可以透過如設定中斷點或逐步執行程式碼，在模組之間移動。</span><span class="sxs-lookup"><span data-stu-id="f2284-199">You can then move through the module, for example, by setting breakpoints or stepping through the code.</span></span>  
  
 <span data-ttu-id="f2284-200">**不進入一步**</span><span class="sxs-lookup"><span data-stu-id="f2284-200">**Step Over**</span></span>  
 <span data-ttu-id="f2284-201">系統會執行下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="f2284-201">The next statement is run.</span></span> <span data-ttu-id="f2284-202">如果此陳述式會叫用 Transact-SQL 預存程序、函數或觸發程序，此模組就會執行直到完成為止，而且結果會傳回給呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2284-202">If the statement invokes a Transact-SQL stored procedure, function, or trigger, the module is run until it finishes and the results are returned to the calling code.</span></span> <span data-ttu-id="f2284-203">如果您確定模組中沒有任何錯誤，就可以不進入此模組。</span><span class="sxs-lookup"><span data-stu-id="f2284-203">If you are sure there are no errors in the module, you can step over it.</span></span> <span data-ttu-id="f2284-204">在呼叫模組之後的陳述式上會暫停執行。</span><span class="sxs-lookup"><span data-stu-id="f2284-204">Execution pauses on the statement that follows the call to the module.</span></span>  
  
 <span data-ttu-id="f2284-205">**跳出**</span><span class="sxs-lookup"><span data-stu-id="f2284-205">**Step Out**</span></span>  
 <span data-ttu-id="f2284-206">跳回下一個最高的呼叫層級 (函數、預存程序或觸發程序)。</span><span class="sxs-lookup"><span data-stu-id="f2284-206">Step back to the next highest calling level (function, stored procedure, or trigger).</span></span> <span data-ttu-id="f2284-207">執行作業會在呼叫預存程序、函數或觸發程序之後的陳述式上暫停。</span><span class="sxs-lookup"><span data-stu-id="f2284-207">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
 <span data-ttu-id="f2284-208">**Windows**</span><span class="sxs-lookup"><span data-stu-id="f2284-208">**Windows**</span></span>  
 <span data-ttu-id="f2284-209">開啟 [中斷點]\*\*\*\* 視窗或 [即時運算]\*\*\*\* 視窗。</span><span class="sxs-lookup"><span data-stu-id="f2284-209">Opens either the **Breakpoint** window or the **Immediate** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2284-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2284-210">See Also</span></span>  
 [<span data-ttu-id="f2284-211">SQL Server Management Studio 鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="f2284-211">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  
