---
title: 使用 sqlcmd 公用程式
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL statements, executing
- command prompt utilities [SQL Server], sqlcmd
- statements [SQL Server], executing
- sqlcmd utility, about sqlcmd utility
ms.assetid: 3ec89119-7314-43ef-9e91-12e72bb63d62
author: rothja
ms.author: jroth
ms.openlocfilehash: 922f9915272fb2d7fc63487ec135ce44ee91e88b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598263"
---
# <a name="use-the-sqlcmd-utility"></a><span data-ttu-id="dd219-102">使用 sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="dd219-102">Use the sqlcmd Utility</span></span>
  <span data-ttu-id="dd219-103">`sqlcmd` 公用程式是命令列公用程式，可用來執行特定的互動式 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式和指令碼，以及用於自動化 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="dd219-103">The `sqlcmd` utility is a command-line utility for ad hoc, interactive execution of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and scripts and for automating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripting tasks.</span></span> <span data-ttu-id="dd219-104">若要以互動方式使用 `sqlcmd`，或是要建立透過 `sqlcmd` 執行的指令碼檔案，使用者必須了解 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd219-104">To use `sqlcmd` interactively, or to build script files to be run using `sqlcmd`, users must understand [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="dd219-105">一般而言，`sqlcmd` 公用程式的使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="dd219-105">The `sqlcmd` utility is typically used in the following ways:</span></span>  
  
-   <span data-ttu-id="dd219-106">使用者可以像是在命令提示字元中工作一般，以互動的方式輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dd219-106">Users interactively enter [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a manner similar to working at the command prompt.</span></span> <span data-ttu-id="dd219-107">結果會顯示在命令提示字元視窗中。</span><span class="sxs-lookup"><span data-stu-id="dd219-107">The results are displayed at the command prompt.</span></span> <span data-ttu-id="dd219-108">若要開啟 [命令提示字元] 視窗，請按一下 **[開始]**、按一下 **[所有程式]**、指向 **[附屬應用程式]**，然後按一下 **[命令提示字元]**。</span><span class="sxs-lookup"><span data-stu-id="dd219-108">To open a Command Prompt window, click **Start**, click **All Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span> <span data-ttu-id="dd219-109">在命令提示字元中，輸入 `sqlcmd`，後面接著您要使用的一串選項。</span><span class="sxs-lookup"><span data-stu-id="dd219-109">At the command prompt, type `sqlcmd` followed by a list of options that you want.</span></span> <span data-ttu-id="dd219-110">如需所支援選項的完整清單 `sqlcmd` ，請參閱[sqlcmd Utility](../../tools/sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="dd219-110">For a complete list of the options that are supported by `sqlcmd`, see [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
-   <span data-ttu-id="dd219-111">使用者可指定要執行的單一 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，或者將公用程式指向包含要執行之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的文字檔，來提交 `sqlcmd` 工作。</span><span class="sxs-lookup"><span data-stu-id="dd219-111">Users submit a `sqlcmd` job either by specifying a single [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute, or by pointing the utility to a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to execute.</span></span> <span data-ttu-id="dd219-112">輸出通常會導向文字檔，不過，也可以在命令提示字元上顯示。</span><span class="sxs-lookup"><span data-stu-id="dd219-112">The output is usually directed to a text file, but it can also be displayed at the command prompt.</span></span>  
  
-   <span data-ttu-id="dd219-113">[查詢編輯器中的](edit-sqlcmd-scripts-with-query-editor.md) SQLCMD 模式 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dd219-113">[SQLCMD mode](edit-sqlcmd-scripts-with-query-editor.md) in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
-   <span data-ttu-id="dd219-114">SQL Server 管理物件 (SMO)</span><span class="sxs-lookup"><span data-stu-id="dd219-114">SQL Server Management Objects (SMO)</span></span>  
  
-   <span data-ttu-id="dd219-115">SQL Server Agent CmdExec 作業</span><span class="sxs-lookup"><span data-stu-id="dd219-115">SQL Server Agent CmdExec jobs.</span></span>  
  
## <a name="typically-used-sqlcmd-options"></a><span data-ttu-id="dd219-116">一般使用的 sqlcmd 選項</span><span class="sxs-lookup"><span data-stu-id="dd219-116">Typically Used sqlcmd Options</span></span>  
 <span data-ttu-id="dd219-117">以下是最常使用的選項：</span><span class="sxs-lookup"><span data-stu-id="dd219-117">The following options are used most frequently:</span></span>  
  
-   <span data-ttu-id="dd219-118">伺服器選項 (**-S**) ，識別連接的實例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="dd219-118">The server option (**-S**) that identifies the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to which `sqlcmd` connects.</span></span>  
  
-   <span data-ttu-id="dd219-119">驗證選項 (**-E**、 **-U**和 **-P**) ，指定 `sqlcmd` 用來連接到實例的認證 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dd219-119">Authentication options (**-E**, **-U**, and **-P**) that specify the credentials that `sqlcmd` uses to connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd219-120">**-E** 選項是預設值，不需要予以指定。</span><span class="sxs-lookup"><span data-stu-id="dd219-120">The **-E** option is the default and does not have to be specified.</span></span>  
  
-   <span data-ttu-id="dd219-121">輸入選項 (**-q**、 **-q**和 **-i**) ，可識別輸入的位置 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="dd219-121">Input options (**-Q**, **-q**, and **-i**) that identify the location of the input to `sqlcmd`.</span></span>  
  
-   <span data-ttu-id="dd219-122">輸出選項 (**-o**) ，指定要在其中 `sqlcmd` 放置其輸出的檔案。</span><span class="sxs-lookup"><span data-stu-id="dd219-122">The output option (**-o**) that specifies the file in which `sqlcmd` is to put its output.</span></span>  
  
## <a name="connecting-to-the-sqlcmd-utility"></a><span data-ttu-id="dd219-123">連接到 sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="dd219-123">Connecting to the sqlcmd Utility</span></span>  
 <span data-ttu-id="dd219-124">下列是 `sqlcmd` 公用程式的一般用途：</span><span class="sxs-lookup"><span data-stu-id="dd219-124">The following are common uses of the `sqlcmd` utility:</span></span>  
  
-   <span data-ttu-id="dd219-125">使用 Windows 驗證連接到預設執行個體，以互動方式執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="dd219-125">Connecting to a default instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd219-126">在上述範例中，未指定 **-E** ，因為它是預設值，而且會 `sqlcmd` 使用 Windows 驗證連接到預設實例。</span><span class="sxs-lookup"><span data-stu-id="dd219-126">In the previous example, **-E** is not specified because it is the default and `sqlcmd` connects to the default instance by using Windows Authentication.</span></span>  
  
-   <span data-ttu-id="dd219-127">使用 Windows 驗證連接到具名執行個體，以互動方式執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="dd219-127">Connecting to a named instance by using Windows Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName>  
    ```  
  
     <span data-ttu-id="dd219-128">或</span><span class="sxs-lookup"><span data-stu-id="dd219-128">or</span></span>  
  
    ```  
    sqlcmd -S .\<InstanceName>  
    ```  
  
-   <span data-ttu-id="dd219-129">使用 Windows 驗證，並且指定輸入和輸出檔案，以連接到具名執行個體：</span><span class="sxs-lookup"><span data-stu-id="dd219-129">Connecting to a named instance by using Windows Authentication and specifying input and output files:</span></span>  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName> -i <MyScript.sql> -o <MyOutput.rpt>  
    ```  
  
-   <span data-ttu-id="dd219-130">使用 Windows 驗證連接到本機電腦上的預設執行個體、執行查詢，並在查詢完成後讓 `sqlcmd` 繼續執行：</span><span class="sxs-lookup"><span data-stu-id="dd219-130">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, and having `sqlcmd` remain running after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -q "SELECT * FROM AdventureWorks2012.Person.Person"  
    ```  
  
-   <span data-ttu-id="dd219-131">使用 Windows 驗證連接到本機電腦上的預設執行個體、執行查詢、將輸出導向至檔案，然後在查詢完成後結束 `sqlcmd`：</span><span class="sxs-lookup"><span data-stu-id="dd219-131">Connecting to the default instance on the local computer by using Windows Authentication, executing a query, directing the output to a file, and having `sqlcmd` exit after the query has finished running:</span></span>  
  
    ```  
    sqlcmd -Q "SELECT * FROM AdventureWorks2012.Person.Person" -o MyOutput.txt  
    ```  
  
-   <span data-ttu-id="dd219-132">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接到具名執行個體，以互動方式執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式 (`sqlcmd` 會提示您輸入密碼)：</span><span class="sxs-lookup"><span data-stu-id="dd219-132">Connecting to a named instance using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to interactively run [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, with `sqlcmd` prompting for a password:</span></span>  
  
    ```  
    sqlcmd -U MyLogin -S <ComputerName>\<InstanceName>  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd219-133">若要查看 `sqlcmd` 公用程式所支援的選項清單，請執行：`sqlcmd -?`。</span><span class="sxs-lookup"><span data-stu-id="dd219-133">To see a list of the options that are supported by the `sqlcmd` utility run: `sqlcmd -?`.</span></span>  
  
## <a name="running-transact-sql-statements-interactively-by-using-sqlcmd"></a><span data-ttu-id="dd219-134">使用 sqlcmd 以互動方式執行 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="dd219-134">Running Transact-SQL Statements Interactively by Using sqlcmd</span></span>  
 <span data-ttu-id="dd219-135">您可以使用 `sqlcmd` 公用程式，以互動方式在 [命令提示字元] 視窗中執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="dd219-135">You can use the `sqlcmd` utility interactively to execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in a Command Prompt window.</span></span> <span data-ttu-id="dd219-136">若要使用以互動方式執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句 `sqlcmd` ，請執行公用程式，而不使用 **-q**、 **-q**、 **-Z**或 **-i**選項來指定任何輸入檔或查詢。</span><span class="sxs-lookup"><span data-stu-id="dd219-136">To interactively execute [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using `sqlcmd`, run the utility without using the **-Q**, **-q**, **-Z**, or **-i** options to specify any input files or queries.</span></span> <span data-ttu-id="dd219-137">例如：</span><span class="sxs-lookup"><span data-stu-id="dd219-137">For example:</span></span>  
  
 `sqlcmd -S <ComputerName>\<InstanceName>`  
  
 <span data-ttu-id="dd219-138">如果在沒有輸入檔或查詢的情況下執行命令，`sqlcmd` 會連接到指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，然後顯示新的一行，其中在 `1>` 後面跟著的閃爍底線，即稱為 `sqlcmd` 提示字元。</span><span class="sxs-lookup"><span data-stu-id="dd219-138">When the command is executed without input files or queries, `sqlcmd` connects to the specified instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then displays a new line with a `1>` followed by a blinking underscore that is named the `sqlcmd` prompt.</span></span> <span data-ttu-id="dd219-139">`1` 表示此處是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的第一行，而 `sqlcmd` 提示字元則是您開始輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的位置。</span><span class="sxs-lookup"><span data-stu-id="dd219-139">The `1` signifies that this is the first line of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, and the `sqlcmd` prompt is the point at which the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will start when you type it in.</span></span>  
  
 <span data-ttu-id="dd219-140">在 `sqlcmd` 提示字元中，您可以輸入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式及 `sqlcmd` 命令 (例如 `GO` 及 `EXIT`)。</span><span class="sxs-lookup"><span data-stu-id="dd219-140">At the `sqlcmd` prompt, you can type both [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands, such as `GO` and `EXIT`.</span></span> <span data-ttu-id="dd219-141">每個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會放在稱為陳述式快取的緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="dd219-141">Each [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is put in a buffer called the statement cache.</span></span> <span data-ttu-id="dd219-142">這些陳述式會在您輸入 `GO` 命令並按 ENTER 後，傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd219-142">These statements are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] after you type the `GO` command and press ENTER.</span></span> <span data-ttu-id="dd219-143">若要結束 `sqlcmd` ，請在 `EXIT` `QUIT` 新行的開頭輸入或。</span><span class="sxs-lookup"><span data-stu-id="dd219-143">To exit `sqlcmd`, type `EXIT` or `QUIT` at the start of a new line.</span></span>  
  
 <span data-ttu-id="dd219-144">若要清除陳述式快取，請輸入 `:RESET`。</span><span class="sxs-lookup"><span data-stu-id="dd219-144">To clear the statement cache, type `:RESET`.</span></span> <span data-ttu-id="dd219-145">輸入 `^C` 會導致結束 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="dd219-145">Typing `^C` causes `sqlcmd` to exit.</span></span> <span data-ttu-id="dd219-146">在發出 `^C` 命令後，也可以使用 `GO` 來停止執行陳述式快取。</span><span class="sxs-lookup"><span data-stu-id="dd219-146">`^C` can also be used to stop the execution of the statement cache after a `GO` command has been issued.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="dd219-147">在互動式會話中輸入的語句，可以藉由輸入 **： ED**命令和提示來編輯 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="dd219-147">statements that are entered in an interactive session can edited by entering the **:ED** command and the `sqlcmd` prompt.</span></span> <span data-ttu-id="dd219-148">此時會開啟編輯器，而在編輯過 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式並關閉編輯器之後，修訂的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式即顯示於命令視窗。</span><span class="sxs-lookup"><span data-stu-id="dd219-148">The editor will open and, after editing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement and closing the editor, the revised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will appear in the command window.</span></span> <span data-ttu-id="dd219-149">輸入 `GO` 以執行修訂 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句。</span><span class="sxs-lookup"><span data-stu-id="dd219-149">Enter `GO` to run therevised [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span>  
  
## <a name="quoted-strings"></a><span data-ttu-id="dd219-150">使用引號的字串</span><span class="sxs-lookup"><span data-stu-id="dd219-150">Quoted Strings</span></span>  
 <span data-ttu-id="dd219-151">系統會直接使用引號括住的字元，而不做額外處理，但是連續輸入兩個引號以將引號插入字串中的情況除外。</span><span class="sxs-lookup"><span data-stu-id="dd219-151">Characters that are enclosed in quotation marks are used without any additional preprocessing, except that quotations marks can be inserted into a string by entering two consecutive quotation marks.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="dd219-152">會將這個字元順序視為一個引號</span><span class="sxs-lookup"><span data-stu-id="dd219-152">treats this character sequence as one quotation mark.</span></span> <span data-ttu-id="dd219-153">(不過，翻譯動作是在伺服器內進行)。指令碼變數出現於字串時，並不會展開。</span><span class="sxs-lookup"><span data-stu-id="dd219-153">(However, the translation occurs in the server.) Scripting variables will not be expanded when they appear within a string.</span></span>  
  
 <span data-ttu-id="dd219-154">例如：</span><span class="sxs-lookup"><span data-stu-id="dd219-154">For example:</span></span>  
  
 `sqlcmd`  
  
 `PRINT "Length: 5"" 7'";`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Length: 5" 7'`  
  
## <a name="strings-that-span-multiple-lines"></a><span data-ttu-id="dd219-155">跨越多行的字串</span><span class="sxs-lookup"><span data-stu-id="dd219-155">Strings That Span Multiple Lines</span></span>  
 <span data-ttu-id="dd219-156">`sqlcmd` 支援其字串跨越多行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="dd219-156">`sqlcmd` supports scripts that have strings that span multiple lines.</span></span> <span data-ttu-id="dd219-157">例如，下列 `SELECT` 陳述式雖然跨越多行，但是當您輸入 `GO`後按下 ENTER 鍵時，所執行的只是單一的字串。</span><span class="sxs-lookup"><span data-stu-id="dd219-157">For example, the following `SELECT` statement spans multiple lines but is a single string executed when you press the ENTER key after typing `GO`.</span></span>  
  
 `SELECT First line`  
  
 `FROM Second line`  
  
 `WHERE Third line;`  
  
 `GO`  
  
## <a name="interactive-sqlcmd-example"></a><span data-ttu-id="dd219-158">互動的 sqlcmd 範例</span><span class="sxs-lookup"><span data-stu-id="dd219-158">Interactive sqlcmd Example</span></span>  
 <span data-ttu-id="dd219-159">這是您以互動方式執行 `sqlcmd` 時所看到的範例。</span><span class="sxs-lookup"><span data-stu-id="dd219-159">This is an example of what you see when you run `sqlcmd` interactively.</span></span>  
  
 <span data-ttu-id="dd219-160">當您開啟 [命令提示字元] 視窗時，只會出現類似下面這一行：</span><span class="sxs-lookup"><span data-stu-id="dd219-160">When you open a Command Prompt window, there is one line similar to:</span></span>  
  
 `C:\> _`  
  
 <span data-ttu-id="dd219-161">這表示資料夾 `C:\` 是目前的資料夾，如果您指定了檔案名稱，則 Windows 將會在該資料夾中尋找這個檔案。</span><span class="sxs-lookup"><span data-stu-id="dd219-161">This means the folder `C:\` is the current folder, and if you specify a file name, Windows will look for the file in that folder.</span></span>  
  
 <span data-ttu-id="dd219-162">輸入 `sqlcmd`，連接到本機電腦的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設執行個體，[命令提示字元] 視窗的內容如下：</span><span class="sxs-lookup"><span data-stu-id="dd219-162">Type `sqlcmd` to connect to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer, and the contents of the Command Prompt window will be:</span></span>  
  
 `C:\>sqlcmd`  
  
 `1> _`  
  
 <span data-ttu-id="dd219-163">這表示您已經連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，而且 `sqlcmd` 已經準備好要接受 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式與 `sqlcmd` 命令。</span><span class="sxs-lookup"><span data-stu-id="dd219-163">This means you have connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and `sqlcmd` is now ready to accept [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and `sqlcmd` commands.</span></span> <span data-ttu-id="dd219-164">在 `1>` 後面的閃爍底線是 `sqlcmd` 提示字元，該字元標示將顯示您輸入之陳述式與命令的位置。</span><span class="sxs-lookup"><span data-stu-id="dd219-164">The flashing underscore after the `1>` is the `sqlcmd` prompt that marks the location at which the statements and commands you type will be displayed.</span></span> <span data-ttu-id="dd219-165">現在，輸入 `USE AdventureWorks2012` 並按 enter，然後輸入，然後 `GO` 按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="dd219-165">Now, type `USE AdventureWorks2012` and press ENTER, and then type `GO` and press ENTER.</span></span> <span data-ttu-id="dd219-166">[命令提示字元] 視窗的內容將如下所示：</span><span class="sxs-lookup"><span data-stu-id="dd219-166">The contents of the Command Prompt window will be:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `1> _`  
  
 <span data-ttu-id="dd219-167">輸入 `USE AdventureWorks2012` 之後按下 ENTER，會指示 `sqlcmd` 開始新的一行。</span><span class="sxs-lookup"><span data-stu-id="dd219-167">Pressing ENTER after entering `USE AdventureWorks2012` signaled `sqlcmd` to start a new line.</span></span> <span data-ttu-id="dd219-168">輸入 `GO,` 之後按下 ENTER，會指示 `sqlcmd` 將 `USE AdventureWorks2012` 陳述式傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd219-168">Pressing ENTER, after you type `GO,` signaled `sqlcmd` to send the `USE AdventureWorks2012` statement to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="dd219-169">`sqlcmd` 便接著傳回訊息指出 `USE` 陳述式已順利完成，並且顯示新的 `1>` 提示字元，表示可以再輸入新的陳述式或命令。</span><span class="sxs-lookup"><span data-stu-id="dd219-169">`sqlcmd` then returned a message to indicate that the `USE` statement completed successfully and displayed a new `1>` prompt as a signal to enter a new statement or command.</span></span>  
  
 <span data-ttu-id="dd219-170">下列範例顯示當您輸入 `SELECT` 陳述式、再輸入 `GO` 執行 `SELECT`，然後輸入 `EXIT` 結束 `sqlcmd`時，[命令提示字元] 視窗中出現的內容：</span><span class="sxs-lookup"><span data-stu-id="dd219-170">The following example shows what the Command Prompt window contains if you type a `SELECT` statement, a `GO` to execute the `SELECT`, and an `EXIT` to exit `sqlcmd`:</span></span>  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `BusinessEntityID   FirstName                 LastName`  
  
 `----------- -------------------------------- -----------`  
  
 `1           Syed                             Abbas`  
  
 `2           Catherine                        Abel`  
  
 `3           Kim                              Abercrombie`  
  
 `(3 rows affected)`  
  
 `1> EXIT`  
  
 `C:\>`  
  
 <span data-ttu-id="dd219-171">在 `3> GO` 這一行後面的那幾行，是 `SELECT` 陳述式的輸出。</span><span class="sxs-lookup"><span data-stu-id="dd219-171">The lines after line `3> GO` are the output of a `SELECT` statement.</span></span> <span data-ttu-id="dd219-172">產生輸出後， `sqlcmd` 會重設 `sqlcmd` 提示字元，並顯示 `1>`。</span><span class="sxs-lookup"><span data-stu-id="dd219-172">After you generate output, `sqlcmd` resets the `sqlcmd` prompt and displays `1>`.</span></span> <span data-ttu-id="dd219-173">在 `EXIT` 行輸入 `1>`之後，[命令提示字元] 視窗會顯示和您初次開啟這個視窗時同樣的一行。</span><span class="sxs-lookup"><span data-stu-id="dd219-173">After entering `EXIT` at line `1>`, the Command Prompt window displays the same line it did when you first opened it.</span></span> <span data-ttu-id="dd219-174">這表示 `sqlcmd` 已經結束其工作階段。</span><span class="sxs-lookup"><span data-stu-id="dd219-174">This indicates that `sqlcmd` has exited its session.</span></span> <span data-ttu-id="dd219-175">您現在可以輸入另一個 `EXIT` 命令，來關閉 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dd219-175">You can now close the Command Prompt window by typing another `EXIT` command.</span></span>  
  
## <a name="running-transact-sql-script-files-by-using-sqlcmd"></a><span data-ttu-id="dd219-176">使用 sqlcmd 執行 Transact-SQL 指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="dd219-176">Running Transact-SQL Script Files by Using sqlcmd</span></span>  
 <span data-ttu-id="dd219-177">您可以使用 `sqlcmd` 來執行資料庫指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="dd219-177">You can use `sqlcmd` to execute database script files.</span></span> <span data-ttu-id="dd219-178">腳本檔案是文字檔，其中包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句、 `sqlcmd` 命令和腳本變數的混合。</span><span class="sxs-lookup"><span data-stu-id="dd219-178">Script files are text files that contain a mix of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span> <span data-ttu-id="dd219-179">如需如何編寫指令碼變數的詳細資訊，請參閱 [以指令碼變數使用 sqlcmd](sqlcmd-use-with-scripting-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="dd219-179">For more information about how to script variables, see [Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md).</span></span> <span data-ttu-id="dd219-180">`sqlcmd` 在指令碼檔案中使用陳述式、命令及指令碼變數的方式，與它使用互動方式輸入陳述式及命令的方式類似。</span><span class="sxs-lookup"><span data-stu-id="dd219-180">`sqlcmd` works with the statements, commands, and scripting variables in a script file in a manner similar to how it works with statements and commands that are entered interactively.</span></span> <span data-ttu-id="dd219-181">主要的差別在於 `sqlcmd` 會讀取整個輸入檔而不暫停，而不是等待使用者輸入陳述式、命令及指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="dd219-181">The main difference is that `sqlcmd` reads through the input file without pause instead of waiting for a user to enter the statements, commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="dd219-182">建立資料庫指令碼檔案有許多不同的方式：</span><span class="sxs-lookup"><span data-stu-id="dd219-182">There are different ways to create database script files:</span></span>  
  
-   <span data-ttu-id="dd219-183">您可以互動方式在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中建立一組 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]陳述式並進行偵錯，然後將 [查詢] 視窗的內容儲存為指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="dd219-183">You can interactively build and debug a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then save the contents of the Query window as a script file.</span></span>  
  
-   <span data-ttu-id="dd219-184">您可以使用文字編輯器 (如「記事本」)，來建立包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的文字檔。</span><span class="sxs-lookup"><span data-stu-id="dd219-184">You can create a text file that contains [!INCLUDE[tsql](../../includes/tsql-md.md)] statements by using a text editor, such as Notepad.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dd219-185">範例</span><span class="sxs-lookup"><span data-stu-id="dd219-185">Examples</span></span>  
  
### <a name="a-running-a-script-by-using-sqlcmd"></a><span data-ttu-id="dd219-186">A.</span><span class="sxs-lookup"><span data-stu-id="dd219-186">A.</span></span> <span data-ttu-id="dd219-187">使用 sqlcmd 執行指令碼</span><span class="sxs-lookup"><span data-stu-id="dd219-187">Running a script by using sqlcmd</span></span>  
 <span data-ttu-id="dd219-188">啟動「記事本」，然後輸入下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式：</span><span class="sxs-lookup"><span data-stu-id="dd219-188">Start Notepad, and type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 <span data-ttu-id="dd219-189">建立名為 `MyFolder` 的資料夾，然後在資料夾 `MyScript.sql` 中將指令碼儲存為檔案 `C:\MyFolder`。</span><span class="sxs-lookup"><span data-stu-id="dd219-189">Create a folder named `MyFolder` and then save the script as the file `MyScript.sql` in the folder `C:\MyFolder`.</span></span> <span data-ttu-id="dd219-190">在命令提示字元中輸入下列命令，以執行指令碼並將輸出存放在 `MyOutput.txt` 的 `MyFolder`中：</span><span class="sxs-lookup"><span data-stu-id="dd219-190">Enter the following at the command prompt to run the script and put the output in `MyOutput.txt` in `MyFolder`:</span></span>  
  
 `sqlcmd -i C:\MyFolder\MyScript.sql -o C:\MyFolder\MyOutput.txt`  
  
 <span data-ttu-id="dd219-191">當您在「記事本」中檢視 `MyOutput.txt` 的內容時，會看到下列項目：</span><span class="sxs-lookup"><span data-stu-id="dd219-191">When you view the contents of `MyOutput.txt` in Notepad, you will see the following:</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `BusinessEntityID FirstName   LastName`  
  
 `---------------- ----------- -----------`  
  
 `1                Syed        Abbas`  
  
 `2                Catherine   Abel`  
  
 `3                Kim         Abercrombie`  
  
 `(3 rows affected)`  
  
### <a name="b-using-sqlcmd-with-a-dedicated-administrative-connection"></a><span data-ttu-id="dd219-192">B.</span><span class="sxs-lookup"><span data-stu-id="dd219-192">B.</span></span> <span data-ttu-id="dd219-193">透過專用管理連接使用 sqlcmd</span><span class="sxs-lookup"><span data-stu-id="dd219-193">Using sqlcmd with a dedicated administrative connection</span></span>  
 <span data-ttu-id="dd219-194">在下列範例中，使用 `sqlcmd` 透過專用管理員連接 (DAC) 連接到發生封鎖問題的伺服器。</span><span class="sxs-lookup"><span data-stu-id="dd219-194">In the following example, `sqlcmd` is used to connect to a server that has a blocking problem by using the dedicated administrator connection (DAC).</span></span>  
  
 `C:\>sqlcmd -S ServerName -A`  
  
 `1> SELECT blocked FROM sys.dm_exec_requests WHERE blocked <> 0;`  
  
 `2> GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `spid   blocked`  
  
 `------ -------`  
  
 `62       64`  
  
 `(1 rows affected)`  
  
 <span data-ttu-id="dd219-195">使用 `sqlcmd` 結束封鎖處理序。</span><span class="sxs-lookup"><span data-stu-id="dd219-195">Use `sqlcmd` to end the blocking process.</span></span>  
  
 `1> KILL 64;`  
  
 `2> GO`  
  
### <a name="c-using-sqlcmd-to-execute-a-stored-procedure"></a><span data-ttu-id="dd219-196">C.</span><span class="sxs-lookup"><span data-stu-id="dd219-196">C.</span></span> <span data-ttu-id="dd219-197">使用 sqlcmd 執行預存程序</span><span class="sxs-lookup"><span data-stu-id="dd219-197">Using sqlcmd to execute a stored procedure</span></span>  
 <span data-ttu-id="dd219-198">下列範例顯示如何使用 `sqlcmd`來執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="dd219-198">The following example shows how to execute a stored procedure by using `sqlcmd`.</span></span> <span data-ttu-id="dd219-199">建立下列預存程序。</span><span class="sxs-lookup"><span data-stu-id="dd219-199">Create the following stored procedure.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `IF OBJECT_ID ( ' dbo.ContactEmailAddress, 'P' ) IS NOT NULL`  
  
 `DROP PROCEDURE dbo.ContactEmailAddress;`  
  
 `GO`  
  
 `CREATE PROCEDURE dbo.ContactEmailAddress`  
  
 `(`  
  
 `@FirstName nvarchar(50)`  
  
 `,@LastName nvarchar(50)`  
  
 `)`  
  
 `AS`  
  
 `SET NOCOUNT ON`  
  
 `SELECT EmailAddress`  
  
 `FROM Person.Person`  
  
 `WHERE FirstName = @FirstName`  
  
 `AND LastName = @LastName;`  
  
 `SET NOCOUNT OFF`  
  
 <span data-ttu-id="dd219-200">在 `sqlcmd` 提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="dd219-200">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\sqlcmd`  
  
 `1> :Setvar FirstName Gustavo`  
  
 `1> :Setvar LastName Achong`  
  
 `1> EXEC dbo.ContactEmailAddress $(Gustavo),$(Achong)`  
  
 `2> GO`  
  
 `EmailAddress`  
  
 `-----------------------------`  
  
 `gustavo0@adventure-works.com`  
  
### <a name="d-using-sqlcmd-for-database-maintenance"></a><span data-ttu-id="dd219-201">D.</span><span class="sxs-lookup"><span data-stu-id="dd219-201">D.</span></span> <span data-ttu-id="dd219-202">使用 sqlcmd 進行資料庫維護</span><span class="sxs-lookup"><span data-stu-id="dd219-202">Using sqlcmd for database maintenance</span></span>  
 <span data-ttu-id="dd219-203">下列範例顯示如何使用 `sqlcmd` 進行資料庫維護工作。</span><span class="sxs-lookup"><span data-stu-id="dd219-203">The following example shows how to use `sqlcmd` for a database maintenance task.</span></span> <span data-ttu-id="dd219-204">以下列程式碼建立 `C:\BackupTemplate.sql` 。</span><span class="sxs-lookup"><span data-stu-id="dd219-204">Create `C:\BackupTemplate.sql` with the following code.</span></span>  
  
 `USE master;`  
  
 `BACKUP DATABASE [$(db)] TO DISK='$(bakfile)';`  
  
 <span data-ttu-id="dd219-205">在 `sqlcmd` 提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="dd219-205">At the `sqlcmd` prompt, enter the following:</span></span>  
  
 `C:\ >sqlcmd`  
  
 `1> :connect <server>`  
  
 `Sqlcmd: Successfully connected to server <server>.`  
  
 `1> :setvar db msdb`  
  
 `1> :setvar bakfile c:\msdb.bak`  
  
 `1> :r c:\BackupTemplate.sql`  
  
 `2> GO`  
  
 `Changed database context to 'master'.`  
  
 `Processed 688 pages for database 'msdb', file 'MSDBData' on file 2.`  
  
 `Processed 5 pages for database 'msdb', file 'MSDBLog' on file 2.`  
  
 `BACKUP DATABASE successfully processed 693 pages in 0.725 seconds (7.830 MB/sec)`  
  
### <a name="e-using-sqlcmd-to-execute-code-on-multiple-instances"></a><span data-ttu-id="dd219-206">E.</span><span class="sxs-lookup"><span data-stu-id="dd219-206">E.</span></span> <span data-ttu-id="dd219-207">使用 sqlcmd 在多個執行個體上執行程式碼</span><span class="sxs-lookup"><span data-stu-id="dd219-207">Using sqlcmd to execute code on multiple instances</span></span>  
 <span data-ttu-id="dd219-208">下列在檔案中的程式碼會顯示連接到兩個執行個體的指令碼。</span><span class="sxs-lookup"><span data-stu-id="dd219-208">The following code in a file shows a script that connects to two instances.</span></span> <span data-ttu-id="dd219-209">請注意， `GO` 是在連接第二個執行個體之前出現。</span><span class="sxs-lookup"><span data-stu-id="dd219-209">Notice the `GO` before the connection to the second instance.</span></span>  
  
 `:CONNECT <server>\,<instance1>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
 `:CONNECT <server>\,<instance2>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
### <a name="e-returning-xml-output"></a><span data-ttu-id="dd219-210">E.</span><span class="sxs-lookup"><span data-stu-id="dd219-210">E.</span></span> <span data-ttu-id="dd219-211">傳回 XML 輸出</span><span class="sxs-lookup"><span data-stu-id="dd219-211">Returning XML output</span></span>  
 <span data-ttu-id="dd219-212">下列範例顯示 XML 輸出如何在連續資料流中傳回未格式化的資料。</span><span class="sxs-lookup"><span data-stu-id="dd219-212">The following example shows how XML output is returned unformatted, in a continuous stream.</span></span>  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> :XML ON`  
  
 `1> SELECT TOP 3 FirstName + ' ' + LastName + ', '`  
  
 `2> FROM Person.Person`  
  
 `3> GO`  
  
 `Syed Abbas, Catherine Abel, Kim Abercrombie,`  
  
### <a name="f-using-sqlcmd-in-a-windows-script-file"></a><span data-ttu-id="dd219-213">F.</span><span class="sxs-lookup"><span data-stu-id="dd219-213">F.</span></span> <span data-ttu-id="dd219-214">在 Windows 指令碼檔案中使用 sqlcmd</span><span class="sxs-lookup"><span data-stu-id="dd219-214">Using sqlcmd in a Windows script file</span></span>  
 <span data-ttu-id="dd219-215">`sqlcmd`之類的命令 `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` 可以在 .bat 檔案中與 VBScript 一起執行。</span><span class="sxs-lookup"><span data-stu-id="dd219-215">A `sqlcmd`command such as `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` can be executed in a .bat file together with VBScript.</span></span> <span data-ttu-id="dd219-216">在這種情況下，請不要使用互動式選項。</span><span class="sxs-lookup"><span data-stu-id="dd219-216">In this case, do not use interactive options.</span></span> <span data-ttu-id="dd219-217">`sqlcmd` 必須安裝在執行 .bat 檔案的電腦上。</span><span class="sxs-lookup"><span data-stu-id="dd219-217">`sqlcmd` must be installed on the computer that is executing the .bat file.</span></span>  
  
 <span data-ttu-id="dd219-218">首先，建立下列四個檔案：</span><span class="sxs-lookup"><span data-stu-id="dd219-218">First, create the following four files:</span></span>  
  
-   <span data-ttu-id="dd219-219">C:\badscript.sql</span><span class="sxs-lookup"><span data-stu-id="dd219-219">C:\badscript.sql</span></span>  
  
    ```  
    SELECT batch_1_this_is_an_error  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="dd219-220">C:\goodscript.sql</span><span class="sxs-lookup"><span data-stu-id="dd219-220">C:\goodscript.sql</span></span>  
  
    ```  
    SELECT 'batch #1'  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   <span data-ttu-id="dd219-221">C:\returnvalue.sql</span><span class="sxs-lookup"><span data-stu-id="dd219-221">C:\returnvalue.sql</span></span>  
  
    ```  
    :exit(select 100)  
    @echo off  
    C:\windowsscript.bat  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
-   <span data-ttu-id="dd219-222">C:\windowsscript.bat</span><span class="sxs-lookup"><span data-stu-id="dd219-222">C:\windowsscript.bat</span></span>  
  
    ```  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
 <span data-ttu-id="dd219-223">然後，在命令提示字元執行 `C:\windowsscript.bat`：</span><span class="sxs-lookup"><span data-stu-id="dd219-223">Then, at the command prompt, run `C:\windowsscript.bat`:</span></span>  
  
 `C:\>windowsscript.bat`  
  
 `Running badscript.sql`  
  
 `== An error occurred`  
  
 `Running goodscript.sql`  
  
 `Running returnvalue.sql`  
  
 `SQLCMD returned 100 to the command shell`  
  
### <a name="g-using-sqlcmd-to-set-encryption-on-azure-sql-database"></a><span data-ttu-id="dd219-224">G.</span><span class="sxs-lookup"><span data-stu-id="dd219-224">G.</span></span> <span data-ttu-id="dd219-225">使用 sqlcmd 設定 Azure SQL Database 的加密</span><span class="sxs-lookup"><span data-stu-id="dd219-225">Using sqlcmd to set encryption on Azure SQL Database</span></span>  
 <span data-ttu-id="dd219-226">`sqlcmd`可以在上與資料的連接上執行， [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 以指定加密和憑證信任。</span><span class="sxs-lookup"><span data-stu-id="dd219-226">A `sqlcmd`can be executed on a connection to [!INCLUDE[ssSDS](../../includes/sssds-md.md)] data on to specify encryption and certificate trust.</span></span> <span data-ttu-id="dd219-227">有兩個 ' sqlcmd ' ' 選項可用：</span><span class="sxs-lookup"><span data-stu-id="dd219-227">Two \`sqlcmd\`\`\`options are available:</span></span>  
  
-   <span data-ttu-id="dd219-228">-N 參數是由用戶端用來要求加密的連接。</span><span class="sxs-lookup"><span data-stu-id="dd219-228">The -N switch is used by the client to request an encrypted connection.</span></span> <span data-ttu-id="dd219-229">這個選項相當於 ADO.net 選項 `ENCRYPT = true`。</span><span class="sxs-lookup"><span data-stu-id="dd219-229">This option is equivalent to the ADO.net option `ENCRYPT = true`.</span></span>  
  
-   <span data-ttu-id="dd219-230">-C 參數是由用戶端所設定，以隱含方式信任伺服器憑證而且不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="dd219-230">The -C switch is used by the client to configure it to implicitly the trust server certificate and not validate it.</span></span> <span data-ttu-id="dd219-231">這個選項相當於 ADO.net 選項 `TRUSTSERVERCERTIFICATE = true`。</span><span class="sxs-lookup"><span data-stu-id="dd219-231">This option is equivalent to the ADO.net option `TRUSTSERVERCERTIFICATE = true`.</span></span>  
  
 <span data-ttu-id="dd219-232">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 服務不支援 SQL Server 執行個體上的所有可用 `SET` 選項。</span><span class="sxs-lookup"><span data-stu-id="dd219-232">The [!INCLUDE[ssSDS](../../includes/sssds-md.md)] service does not support all the `SET` options available on a SQL Server instance.</span></span> <span data-ttu-id="dd219-233">當對應的 `SET` 選項設定為 `ON` 或 `OFF`時，下列選項會擲回錯誤：</span><span class="sxs-lookup"><span data-stu-id="dd219-233">The following options throw an error when the corresponding `SET` option is set to `ON` or `OFF`:</span></span>  
  
-   <span data-ttu-id="dd219-234">SET ANSI_DEFAULTS</span><span class="sxs-lookup"><span data-stu-id="dd219-234">SET ANSI_DEFAULTS</span></span>  
  
-   <span data-ttu-id="dd219-235">SET ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="dd219-235">SET ANSI_NULLS</span></span>  
  
-   <span data-ttu-id="dd219-236">SET REMOTE_PROC_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="dd219-236">SET REMOTE_PROC_TRANSACTIONS</span></span>  
  
-   <span data-ttu-id="dd219-237">SET ANSI_NULL_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="dd219-237">SET ANSI_NULL_DEFAULT</span></span>  
  
 <span data-ttu-id="dd219-238">以下 SET 選項不會擲回例外狀況，但不能使用。</span><span class="sxs-lookup"><span data-stu-id="dd219-238">The following SET options do not throw exceptions but cannot be used.</span></span> <span data-ttu-id="dd219-239">這些選項已被取代：</span><span class="sxs-lookup"><span data-stu-id="dd219-239">They are deprecated:</span></span>  
  
-   <span data-ttu-id="dd219-240">SET CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="dd219-240">SET CONCAT_NULL_YIELDS_NULL</span></span>  
  
-   <span data-ttu-id="dd219-241">SET ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="dd219-241">SET ANSI_PADDING</span></span>  
  
-   <span data-ttu-id="dd219-242">SET QUERY_GOVERNOR_COST_LIMIT</span><span class="sxs-lookup"><span data-stu-id="dd219-242">SET QUERY_GOVERNOR_COST_LIMIT</span></span>  
  
#### <a name="syntax"></a><span data-ttu-id="dd219-243">語法</span><span class="sxs-lookup"><span data-stu-id="dd219-243">Syntax</span></span>  
 <span data-ttu-id="dd219-244">下列範例會參考 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供者設定的案例，包括： `ForceProtocolEncryption = False`、 `Trust Server Certificate = No`</span><span class="sxs-lookup"><span data-stu-id="dd219-244">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = False`, `Trust Server Certificate = No`</span></span>  
  
 <span data-ttu-id="dd219-245">使用 Windows 認證來連接，並加密通訊：</span><span class="sxs-lookup"><span data-stu-id="dd219-245">Connect using Windows credentials and encrypt communication:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="dd219-246">使用 Windows 認證及信任伺服器憑證進行連接：</span><span class="sxs-lookup"><span data-stu-id="dd219-246">Connect using Windows credentials and trust server certificate:</span></span>  
  
```  
SQLCMD -E -C  
  
```  
  
 <span data-ttu-id="dd219-247">使用 Windows 認證進行連接、加密通訊並信任伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="dd219-247">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="dd219-248">下列範例會參考 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 提供者設定的案例，包括： `ForceProtocolEncryption = True`、 `TrustServerCertificate = Yes`。</span><span class="sxs-lookup"><span data-stu-id="dd219-248">The following examples refer to cases where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider settings include: `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`.</span></span>  
  
 <span data-ttu-id="dd219-249">使用 Windows 認證進行連接、加密通訊並信任伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="dd219-249">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E  
  
```  
  
 <span data-ttu-id="dd219-250">使用 Windows 認證進行連接、加密通訊並信任伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="dd219-250">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N  
  
```  
  
 <span data-ttu-id="dd219-251">使用 Windows 認證進行連接、加密通訊並信任伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="dd219-251">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -T  
  
```  
  
 <span data-ttu-id="dd219-252">使用 Windows 認證進行連接、加密通訊並信任伺服器憑證：</span><span class="sxs-lookup"><span data-stu-id="dd219-252">Connect using Windows credentials, encrypt communication and trust server certificate:</span></span>  
  
```  
SQLCMD -E -N -C  
  
```  
  
 <span data-ttu-id="dd219-253">如果提供者指定 `ForceProtocolEncryption = True` ，則會啟用加密，即使 `Encrypt=No` 在連接字串中。</span><span class="sxs-lookup"><span data-stu-id="dd219-253">If the provider specifies `ForceProtocolEncryption = True` then encryption is enabled even if `Encrypt=No` in the connection string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd219-254">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd219-254">See Also</span></span>  
 <span data-ttu-id="dd219-255">[sqlcmd 公用程式](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="dd219-255">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 <span data-ttu-id="dd219-256">[以指令碼變數使用 sqlcmd](sqlcmd-use-with-scripting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="dd219-256">[Use sqlcmd with Scripting Variables](sqlcmd-use-with-scripting-variables.md) </span></span>  
 <span data-ttu-id="dd219-257">[使用查詢編輯器編輯 SQLCMD 指令碼](edit-sqlcmd-scripts-with-query-editor.md) </span><span class="sxs-lookup"><span data-stu-id="dd219-257">[Edit SQLCMD Scripts with Query Editor](edit-sqlcmd-scripts-with-query-editor.md) </span></span>  
 <span data-ttu-id="dd219-258">[管理作業步驟](../../ssms/agent/manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="dd219-258">[Manage Job Steps](../../ssms/agent/manage-job-steps.md) </span></span>  
 [<span data-ttu-id="dd219-259">建立 CmdExec 作業步驟</span><span class="sxs-lookup"><span data-stu-id="dd219-259">Create a CmdExec Job Step</span></span>](../../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
