---
title: 使用查詢編輯器編輯 SQLCMD 指令碼
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], SQLCMD scripts
- SQLCMD scripts
- modifying scripts
- Query Editor [Database Engine], SQLCMD scripts
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: f77b866d-c330-47c9-9e74-0b8d8dff4b31
author: rothja
ms.author: jroth
ms.openlocfilehash: a3466cfc15ea2f4f0c8de5da42f4a1c24c28a575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596626"
---
# <a name="edit-sqlcmd-scripts-with-query-editor"></a><span data-ttu-id="7a0d4-102">使用查詢編輯器編輯 SQLCMD 指令碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-102">Edit SQLCMD Scripts with Query Editor</span></span>
  <span data-ttu-id="7a0d4-103">您可以使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器，以 SQLCMD 指令碼撰寫和編輯查詢。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-103">By using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] you can write and edit queries as SQLCMD scripts.</span></span> <span data-ttu-id="7a0d4-104">當您必須在相同的指令碼中處理 Windows 系統命令和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式時，就可以使用 SQLCMD 指令碼。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-104">You use SQLCMD scripts when you have to process Windows System commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the same script.</span></span>  
  
## <a name="sqlcmd-mode"></a><span data-ttu-id="7a0d4-105">SQLCMD 模式</span><span class="sxs-lookup"><span data-stu-id="7a0d4-105">SQLCMD Mode</span></span>  
 <span data-ttu-id="7a0d4-106">若要使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器來撰寫或編輯 SQLCMD 指令碼，您必須啟用 SQLCMD 指令碼模式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-106">To use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor to write or edit SQLCMD scripts, you must enable the SQLCMD scripting mode.</span></span> <span data-ttu-id="7a0d4-107">根據預設，查詢編輯器不會啟用 SQLCMD 模式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-107">By default, SQLCMD mode is not enabled in the Query Editor.</span></span> <span data-ttu-id="7a0d4-108">您可以按一下工具列上的 **SQLCMD 模式**圖示，或從 [查詢] 功能表中選取 [SQLCMD 模式]啟用指令碼模式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-108">You can enable scripting mode by clicking the **SQLCMD Mode** icon in the toolbar or by selecting **SQLCMD Mode** from the **Query** menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a0d4-109">啟用 SQLCMD 模式就會關閉 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢編輯器中的 IntelliSense 和 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-109">Enabling SQLCMD mode turns off IntelliSense and the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="7a0d4-110">查詢編輯器中的 SQLCMD 指令碼可以使用所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼都使用的相同功能。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-110">SQLCMD scripts in the Query Editor can use the same features that all [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts use.</span></span> <span data-ttu-id="7a0d4-111">這些功能包括：</span><span class="sxs-lookup"><span data-stu-id="7a0d4-111">These features include the following:</span></span>  
  
-   <span data-ttu-id="7a0d4-112">色彩編碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-112">Color Coding</span></span>  
  
-   <span data-ttu-id="7a0d4-113">執行指令碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-113">Executing Scripts</span></span>  
  
-   <span data-ttu-id="7a0d4-114">原始程式碼控制</span><span class="sxs-lookup"><span data-stu-id="7a0d4-114">Source Control</span></span>  
  
-   <span data-ttu-id="7a0d4-115">剖析指令碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-115">Parsing Scripts</span></span>  
  
-   <span data-ttu-id="7a0d4-116">Showplan</span><span class="sxs-lookup"><span data-stu-id="7a0d4-116">Showplan</span></span>  
  
## <a name="enable-sqlcmd-scripting-in-query-editor"></a><span data-ttu-id="7a0d4-117">在查詢編輯器中啟用 SQLCMD 指令碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-117">Enable SQLCMD Scripting in Query Editor</span></span>  
 <span data-ttu-id="7a0d4-118">若要針對使用中 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗開啟 SQLCMD 指令碼，請使用下列程序。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-118">To turn SQLCMD scripting on for an active [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window, use the following procedure.</span></span>  
  
#### <a name="to-switch-a-database-engine-query-editor-window-to-sqlcmd-mode"></a><span data-ttu-id="7a0d4-119">將 Database Engine 查詢編輯器視窗切換到 SQLCMD 模式</span><span class="sxs-lookup"><span data-stu-id="7a0d4-119">To switch a Database Engine Query Editor window to SQLCMD mode</span></span>  
  
1.  <span data-ttu-id="7a0d4-120">在物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [新增查詢]  ，即可開啟新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-120">In Object Explorer, right-click the server, and then click **New Query**, to open a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
2.  <span data-ttu-id="7a0d4-121">在 [查詢]  功能表上，按一下 [SQLCMD 模式]  。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-121">On the **Query** menu, click **SQLCMD Mode**.</span></span>  
  
     <span data-ttu-id="7a0d4-122">查詢編輯器會在其本身的內容中執行 **sqlcmd** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-122">The Query Editor executes **sqlcmd** statements in the context of the Query Editor.</span></span>  
  
3.  <span data-ttu-id="7a0d4-123">在 [SQL 編輯器]  工具列的 [可用資料庫]  清單中，選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-123">On the **SQL Editor** toolbar, in the **Available Databases** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
4.  <span data-ttu-id="7a0d4-124">在查詢編輯器視窗中鍵入下列兩項 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式及 `!!DIR` **sqlcmd** 陳述式：</span><span class="sxs-lookup"><span data-stu-id="7a0d4-124">In the Query Editor window, type the following two [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and the `!!DIR` **sqlcmd** statement:</span></span>  
  
    ```  
    SELECT DISTINCT Type FROM Sales.SpecialOffer;  
    GO  
    !!DIR  
    GO  
    SELECT ProductCategoryID, Name FROM Production.ProductCategory;  
    GO  
    ```  
  
5.  <span data-ttu-id="7a0d4-125">按 F5 執行混合 [!INCLUDE[tsql](../../includes/tsql-md.md)] 與 MS-DOS 陳述式的整個區段。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-125">Press F5 to execute the whole section of mixed [!INCLUDE[tsql](../../includes/tsql-md.md)] and MS-DOS statements.</span></span>  
  
     <span data-ttu-id="7a0d4-126">請注意第 1 個和第 3 個陳述式產生的兩個 SQL 結果窗格。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-126">Notice the two SQL result panes from the first and third statements.</span></span>  
  
6.  <span data-ttu-id="7a0d4-127">在 [結果]  窗格中，按一下 [訊息]  索引標籤來查看這三個陳述式產生的訊息：</span><span class="sxs-lookup"><span data-stu-id="7a0d4-127">In the **Results** pane, click the **Messages** tab to see the messages from all three statements:</span></span>  
  
    -   <span data-ttu-id="7a0d4-128">(6 個資料列受影響)</span><span class="sxs-lookup"><span data-stu-id="7a0d4-128">(6 row(s) affected)</span></span>  
  
    -   \<The directory information>  
  
    -   <span data-ttu-id="7a0d4-129">(4 個資料列受影響)</span><span class="sxs-lookup"><span data-stu-id="7a0d4-129">(4 row(s) affected)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7a0d4-130">從命令列執行時， **sqlcmd** 公用程式允許與作業系統進行完整互動。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-130">When executed from the command line, the **sqlcmd** utility permits full interaction with the operating system.</span></span> <span data-ttu-id="7a0d4-131">當您在 [SQLCMD 模式]\*\*\*\* 中使用 [查詢編輯器] 時，您必須非常小心，不要執行互動式陳述式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-131">When you use the Query Editor in **SQLCMD Mode**, you must be careful not to execute interactive statements.</span></span> <span data-ttu-id="7a0d4-132">[查詢編輯器] 無法回應作業系統提示。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-132">The Query Editor cannot respond to operating system prompts.</span></span>  
  
 <span data-ttu-id="7a0d4-133">如需有關如何執行 SQLCMD 的詳細資訊，請參閱 [sqlcmd 工用程式](../../tools/sqlcmd-utility.md)，或進入 SQLCMD 教學課程。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-133">For more information about how to run SQLCMD, see [sqlcmd Utility](../../tools/sqlcmd-utility.md), or take the SQLCMD tutorial.</span></span>  
  
## <a name="enable-sqlcmd-scripting-by-default"></a><span data-ttu-id="7a0d4-134">依預設，會啟用 SQLCMD 指令碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-134">Enable SQLCMD Scripting by Default</span></span>  
 <span data-ttu-id="7a0d4-135">若要依預設開啟 SQLCMD 指令碼，請在 [工具]\*\*\*\* 功能表中選取 [選項]\*\*\*\*，展開 [執行查詢]\*\*\*\* 和 **SQL Server**，按一下 [一般]\*\*\*\* 頁面，再核取 [預設會以 SQLCMD 模式開啟新查詢]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-135">To turn SQLCMD scripting on by default, on the **Tools** menu select **Options**, expand **Query Execution**, and **SQL Server**, click the **General** page, and then check the **By default open new queries in SQLCMD Mode** box.</span></span>  
  
## <a name="writing-and-editing-sqlcmd-scripts"></a><span data-ttu-id="7a0d4-136">撰寫和編輯 SQLCMD 指令碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-136">Writing and Editing SQLCMD Scripts</span></span>  
 <span data-ttu-id="7a0d4-137">在啟用指令碼模式之後，您便可以撰寫 SQLCMD 命令和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-137">After enabling scripting mode you may write SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="7a0d4-138">適用的規則如下：</span><span class="sxs-lookup"><span data-stu-id="7a0d4-138">The following rules apply:</span></span>  
  
-   <span data-ttu-id="7a0d4-139">SQLCMD 命令必須是行中的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-139">SQLCMD commands must be the first statement on a line.</span></span>  
  
-   <span data-ttu-id="7a0d4-140">每行只能有一個 SQLCMD 命令。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-140">Only one SQLCMD command is permitted on each line.</span></span>  
  
-   <span data-ttu-id="7a0d4-141">SQLCMD 命令前面可以有註解或空格。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-141">SQLCMD commands can be preceded by comments or white space.</span></span>  
  
-   <span data-ttu-id="7a0d4-142">不會執行註解字元內的 SQLCMD 命令。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-142">SQLCMD commands within comment characters are not executed.</span></span>  
  
-   <span data-ttu-id="7a0d4-143">單行註解字元是兩個連字號 (`--)` ，必須在行首。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-143">Single line comment characters are two hyphens (`--)` and must appear at the beginning of a line.</span></span>  
  
-   <span data-ttu-id="7a0d4-144">作業系統命令的前面必須有兩個驚歎號 (`!!`)。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-144">Operating system commands must be preceded by two exclamation points (`!!`).</span></span> <span data-ttu-id="7a0d4-145">兩個驚歎號的命令會使在驚歎號後面的陳述式利用 `cmd.exe` 命令處理器來執行。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-145">The double-exclamation points command causes the statement that follows the exclamation points to be executed using the `cmd.exe` command processor.</span></span> <span data-ttu-id="7a0d4-146">`!!` 之後的文字會當做參數傳給 `cmd.exe`，因此，最後執行的命令列是： `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-146">The text after `!!` is passed in as a parameter to `cmd.exe`, so the final command line will execute as: `"%SystemRoot%\system32\cmd.exe /c <text after !!>"`.</span></span>  
  
-   <span data-ttu-id="7a0d4-147">為了清楚區分 SQLCMD 命令和 [!INCLUDE[tsql](../../includes/tsql-md.md)]，所有 SQLCMD 命令的前面都必須加上冒號 (`:`)。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-147">To make a clear distinction between SQLCMD commands and [!INCLUDE[tsql](../../includes/tsql-md.md)], all SQLCMD commands, need to be prefixed with a colon (`:`).</span></span>  
  
-   <span data-ttu-id="7a0d4-148">使用 `GO` 命令時不需要前置詞或在其之前加上 `!!:`</span><span class="sxs-lookup"><span data-stu-id="7a0d4-148">The `GO` command may be used without preface, or preceded by `!!:`</span></span>  
  
-   <span data-ttu-id="7a0d4-149">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器支援環境變數和定義成 SQLCMD 指令碼一部分的變數，但不支援內建的 SQLCMD 或 **osql** 變數。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-149">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports environment variables and variables that are defined as part of a SQLCMD script, but does not support built-in SQLCMD or **osql** variables.</span></span> <span data-ttu-id="7a0d4-150">由 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 所處理的 SQLCMD 對變數而言，是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-150">SQLCMD processing by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is case sensitive for variables.</span></span> <span data-ttu-id="7a0d4-151">例如，PRINT '$(COMPUTERNAME)' 會產生正確的結果，但是 PRINT '$(ComputerName)' 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-151">For example, PRINT '$(COMPUTERNAME)' produces the correct result, but PRINT '$(ComputerName)' returns an error.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7a0d4-152">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient 以便在正規和 SQLCMD 模式中執行。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-152">uses [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]SqlClient for execution in regular and SQLCMD mode.</span></span> <span data-ttu-id="7a0d4-153">從命令列執行時，SQLCMD 會使用 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-153">When run from the command line, SQLCMD uses the OLE DB provider.</span></span> <span data-ttu-id="7a0d4-154">由於可能套用不同的預設選項，因此，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] SQLCMD 模式中，以及在 SQLCMD 公用程式中執行相同的查詢時，可能會出現不同的行為。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-154">Because different default options may apply, it is possible to get different behavior while executing the same query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] SQLCMD Mode, and in the SQLCMD utility.</span></span>  
  
## <a name="supported-sqlcmd-syntax"></a><span data-ttu-id="7a0d4-155">支援的 SQLCMD 語法</span><span class="sxs-lookup"><span data-stu-id="7a0d4-155">Supported SQLCMD Syntax</span></span>  
 <span data-ttu-id="7a0d4-156">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器支援下列 SQLCMD 指令碼關鍵字：</span><span class="sxs-lookup"><span data-stu-id="7a0d4-156">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor supports the following SQLCMD script keywords:</span></span>  
  
 `[!!:]GO[count]`  
  
 `!! <command>`  
  
 `:exit(statement)`  
  
 `:Quit`  
  
 `:r <filename>`  
  
 `:setvar <var> <value>`  
  
 `:connect server[\instance] [-l login_timeout] [-U user [-P password]]`  
  
 `:on error [ignore|exit]`  
  
 `:error <filename>|stderr|stdout`  
  
 `:out <filename>|stderr|stdout`  
  
> [!NOTE]  
>  <span data-ttu-id="7a0d4-157">對於 `:error` 和 `:out`而言， `stderr` 和 `stdout` 都會將輸出傳到訊息索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-157">For both `:error` and `:out`, `stderr` and `stdout` send output to the messages tab.</span></span>  
  
 <span data-ttu-id="7a0d4-158">查詢編輯器不支援上面所未列出的 SQLCMD 命令。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-158">SQLCMD commands not listed above are not supported in Query Editor.</span></span> <span data-ttu-id="7a0d4-159">當執行包含不支援的 SQLCMD 關鍵字之腳本時，查詢編輯器會 \<ignored command*> 針對每個不支援的關鍵字，將「忽略命令 \*」訊息傳送至目的地。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-159">When a script containing SQLCMD keywords that are not supported is executed, the Query Editor will send an "Ignoring command \*\<ignored command*>" message to the destination for each unsupported keyword.</span></span> <span data-ttu-id="7a0d4-160">指令碼將順利執行，但會忽略不支援的命令。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-160">The script will execute successfully, but the unsupported commands will be ignored.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7a0d4-161">由於您不是從命令列啟動 SQLCMD，因此，當執行查詢編輯器的 SQLCMD 模式時，會有若干限制。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-161">Because you are not starting SQLCMD from the command line, there are some limitations when running Query Editor in SQLCMD Mode.</span></span> <span data-ttu-id="7a0d4-162">您不能傳入變數之類的命令列參數，且因為查詢編輯器沒有回應作業系統提示的能力，您必須小心避免執行互動式的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-162">You cannot pass in command-line parameters such as variables, and, because the Query Editor does not have the ability to respond to operating system prompts, you must be careful not to execute interactive statements.</span></span>  
  
## <a name="color-coding-in-sqlcmd-scripts"></a><span data-ttu-id="7a0d4-163">SQLCMD 指令碼中的色彩編碼</span><span class="sxs-lookup"><span data-stu-id="7a0d4-163">Color Coding in SQLCMD Scripts</span></span>  
 <span data-ttu-id="7a0d4-164">在啟用 SQLCMD 指令碼之後，指令碼會有色彩編碼。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-164">With SQLCMD scripting enabled, scripts will be color coded.</span></span> <span data-ttu-id="7a0d4-165">[!INCLUDE[tsql](../../includes/tsql-md.md)] 關鍵字的色彩編碼維持不變。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-165">The color coding for [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords will remain the same.</span></span> <span data-ttu-id="7a0d4-166">SQLCMD 命令會呈現陰影效果的背景。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-166">SQLCMD commands are presented with a shaded background.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a0d4-167">範例</span><span class="sxs-lookup"><span data-stu-id="7a0d4-167">Example</span></span>  
 <span data-ttu-id="7a0d4-168">下列範例使用 **sqlcmd** 陳述式建立名為 testoutput.txt 的輸出檔、執行兩個 [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT 陳述式，以及一個作業系統命令 (列印目前的目錄)。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-168">The following example uses a **sqlcmd** statement to create an output file called testoutput.txt, executes two [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statements along with one operating system command (to print out the current directory).</span></span> <span data-ttu-id="7a0d4-169">產生的檔案包含 `DIR` 陳述式的訊息輸出，且後面會有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的結果輸出。</span><span class="sxs-lookup"><span data-stu-id="7a0d4-169">The resultant file contains the message output from the `DIR` statement, followed by the results output from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
```  
:out C:\testoutput.txt  
SELECT @@VERSION As 'Server Version'  
!!DIR  
!!:GO  
SELECT @@SERVERNAME AS 'Server Name'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a0d4-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a0d4-170">See Also</span></span>  
 [<span data-ttu-id="7a0d4-171">sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="7a0d4-171">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
