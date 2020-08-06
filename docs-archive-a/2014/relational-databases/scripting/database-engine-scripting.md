---
title: Database Engine 指令碼
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], PowerShell
- scripts [SQL Server]
- scripting [SQL Server Database Engine]
- scripting [SQL Server Database Engine], PowerShell
ms.assetid: 9978a884-59a2-4e7f-a82a-335149f3a261
author: rothja
ms.author: jroth
ms.openlocfilehash: 79dca27e2aa5f2c0bc473534e0a8b204345b3993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584370"
---
# <a name="database-engine-scripting"></a><span data-ttu-id="59356-102">Database Engine 指令碼</span><span class="sxs-lookup"><span data-stu-id="59356-102">Database Engine Scripting</span></span>
  <span data-ttu-id="59356-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 支援使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell 指令碼環境來管理 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體和執行個體中的物件。</span><span class="sxs-lookup"><span data-stu-id="59356-103">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] supports the [!INCLUDE[msCoName](../../includes/msconame-md.md)] PowerShell scripting environment to manage instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the objects in the instances.</span></span> <span data-ttu-id="59356-104">此外，您也可以在與指令碼環境非常相似的環境中，建立並執行含有 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 XQuery 的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="59356-104">You can also build and run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries that contain [!INCLUDE[tsql](../../includes/tsql-md.md)] and XQuery in environments very similar to scripting environments.</span></span>  
  
## <a name="sql-server-powershell"></a><span data-ttu-id="59356-105">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="59356-105">SQL Server PowerShell</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="59356-106">包含兩個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 嵌入式管理單元，可實作：</span><span class="sxs-lookup"><span data-stu-id="59356-106">includes two [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins that implement:</span></span>  
  
-   <span data-ttu-id="59356-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供者，以便將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件模型階層公開成與檔案系統路徑相似的 PowerShell 路徑。</span><span class="sxs-lookup"><span data-stu-id="59356-107">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider that exposes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model hierarchies as PowerShell paths that are similar to file system paths.</span></span> <span data-ttu-id="59356-108">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件模型類別來管理以路徑之每個節點表示的物件。</span><span class="sxs-lookup"><span data-stu-id="59356-108">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] management object model classes to manage the objects represented at each node of the path.</span></span>  
  
-   <span data-ttu-id="59356-109">一組實作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 命令的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="59356-109">A set of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cmdlets that implement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commands.</span></span> <span data-ttu-id="59356-110">其中一個 Cmdlet 是 **Invoke-Sqlcmd**。</span><span class="sxs-lookup"><span data-stu-id="59356-110">One of the cmdlets is **Invoke-Sqlcmd**.</span></span> <span data-ttu-id="59356-111">這是用來執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 要與公用程式一起執行的查詢腳本 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="59356-111">This is used to run [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query scripts to be run with the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="59356-112">提供了用來執行 PowerShell 的以下功能：</span><span class="sxs-lookup"><span data-stu-id="59356-112">provides these features for running PowerShell:</span></span>  
  
-   <span data-ttu-id="59356-113">可以匯入到 PowerShell 工作階段的 **sqlps** PowerShell 模組，然後此模組會載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 嵌入式管理單元。您可以用互動方式執行隨選 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="59356-113">The **sqlps** PowerShell module that can be imported to a PowerShell session, the module then loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] snap-ins. You can interactively run ad hoc PowerShell commands.</span></span> <span data-ttu-id="59356-114">您可以使用 .\MyFolder\MyScript.ps1 等命令來執行指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="59356-114">You can run script files using a command such as .\MyFolder\MyScript.ps1.</span></span>  
  
-   <span data-ttu-id="59356-115">PowerShell 指令碼檔案可以當做依排程間隔或為了回應系統事件而執行指令碼之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell 作業步驟的輸入使用。</span><span class="sxs-lookup"><span data-stu-id="59356-115">PowerShell script files can be used as input to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell job steps that run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
-   <span data-ttu-id="59356-116">啟動 PowerShell 並匯入 **模組的** sqlps [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式。</span><span class="sxs-lookup"><span data-stu-id="59356-116">The **sqlps** utility that starts PowerShell and imports the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] module.</span></span> <span data-ttu-id="59356-117">然後您可以執行此模組支援的所有動作。</span><span class="sxs-lookup"><span data-stu-id="59356-117">You can then perform all actions supported by the module.</span></span> <span data-ttu-id="59356-118">您可以透過命令提示字元，或在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio 的物件總管樹狀目錄中以滑鼠右鍵按一下節點並選取 [啟動 PowerShell]  ，啟動 **sqlps** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="59356-118">You can start the **sqlps** utility either in a command prompt or by right-clicking on the nodes in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio Object Explorer tree and selecting **Start PowerShell**.</span></span>  
  
## <a name="database-engine-queries"></a><span data-ttu-id="59356-119">Database Engine 查詢</span><span class="sxs-lookup"><span data-stu-id="59356-119">Database Engine Queries</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="59356-120">查詢指令碼包含三種元素：</span><span class="sxs-lookup"><span data-stu-id="59356-120">query scripts contain three types of elements:</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="59356-121">語言陳述式。</span><span class="sxs-lookup"><span data-stu-id="59356-121">language statements.</span></span>  
  
-   <span data-ttu-id="59356-122">XQuery 語言陳述式。</span><span class="sxs-lookup"><span data-stu-id="59356-122">XQuery language statements</span></span>  
  
-   <span data-ttu-id="59356-123">公用程式的命令和變數 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="59356-123">Commands and variables from the `sqlcmd` utility.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="59356-124">提供了三種建立和執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢的環境：</span><span class="sxs-lookup"><span data-stu-id="59356-124">provides three environments for building and running [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries:</span></span>  
  
-   <span data-ttu-id="59356-125">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中，您可以用互動方式執行並偵錯 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="59356-125">You can interactively run and debug [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="59356-126">您可以在單一工作階段中編寫許多陳述式的程式碼並進行偵錯，然後將所有陳述式都儲存在單一指令碼檔案中。</span><span class="sxs-lookup"><span data-stu-id="59356-126">You can code and debug several statements in one session, then save all of the statements in a single script file.</span></span>  
  
-   <span data-ttu-id="59356-127">`sqlcmd`命令提示字元公用程式可讓您以互動方式執行 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢，也可以執行現有的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢腳本檔案。</span><span class="sxs-lookup"><span data-stu-id="59356-127">The `sqlcmd` command prompt utility lets you interactively run [!INCLUDE[ssDE](../../includes/ssde-md.md)] queries, and also run existing [!INCLUDE[ssDE](../../includes/ssde-md.md)] query script files.</span></span>  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="59356-128">您通常會使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 查詢編輯器，以互動方式在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中編寫查詢指令碼檔案的程式碼。</span><span class="sxs-lookup"><span data-stu-id="59356-128">query script files are typically coded interactively in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] by using the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="59356-129">然後，您就可以在下列其中一個環境內開啟此檔案：</span><span class="sxs-lookup"><span data-stu-id="59356-129">The file can later be opened in one of these environments:</span></span>  
  
-   <span data-ttu-id="59356-130">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [檔案]  /[開啟]  功能表，以在新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="59356-130">Use the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **File**/**Open** menu to open the file in a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span>  
  
-   <span data-ttu-id="59356-131">使用 **-i**_input_file_參數，透過公用程式來執行檔案 `sqlcmd` 。</span><span class="sxs-lookup"><span data-stu-id="59356-131">Use the **-i**_input_file_ parameter to run the file with the `sqlcmd` utility.</span></span>  
  
-   <span data-ttu-id="59356-132">使用 **-QueryFromFile** 參數搭配 **PowerShell 指令碼中的** Invoke-Sqlcmd [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Cmdlet 來執行此檔案。</span><span class="sxs-lookup"><span data-stu-id="59356-132">Use the **-QueryFromFile** parameter to run the file with the **Invoke-Sqlcmd** cmdlet in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell scripts.</span></span>  
  
-   <span data-ttu-id="59356-133">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟，依排程間隔或為了回應系統事件而執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="59356-133">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps to run the scripts either at scheduled intervals or in response to system events.</span></span>  
  
 <span data-ttu-id="59356-134">此外，您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [產生指令碼精靈] 來產生 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="59356-134">In addition, you can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Generate Script Wizard to generate [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="59356-135">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的物件總管中，以滑鼠右鍵按一下物件，然後選取 [產生指令碼]  功能表項目。</span><span class="sxs-lookup"><span data-stu-id="59356-135">You can right-click objects in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, then select the **Generate Script** menu item.</span></span> <span data-ttu-id="59356-136">[產生指令碼]  就會啟動此精靈，並逐步引導您完成建立指令碼的程序。</span><span class="sxs-lookup"><span data-stu-id="59356-136">**Generate Script** launches the wizard, which guides you through the process of creating a script.</span></span>  
  
## <a name="database-engine-scripting-tasks"></a><span data-ttu-id="59356-137">Database Engine 指令碼工作</span><span class="sxs-lookup"><span data-stu-id="59356-137">Database Engine Scripting Tasks</span></span>  
  
|<span data-ttu-id="59356-138">工作描述</span><span class="sxs-lookup"><span data-stu-id="59356-138">Task Description</span></span>|<span data-ttu-id="59356-139">主題</span><span class="sxs-lookup"><span data-stu-id="59356-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="59356-140">描述如何使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的程式碼和文字編輯器，以互動方式開發、偵錯和執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="59356-140">Describes how to use the code and text editors in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to interactively develop, debug, and run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts</span></span>|[<span data-ttu-id="59356-141">查詢與文字編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="59356-141">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)|  
|<span data-ttu-id="59356-142">描述如何使用 `sqlcmd` 公用程式，從命令提示字元執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼，包含以互動方式開發指令碼的能力。</span><span class="sxs-lookup"><span data-stu-id="59356-142">Describes how to use the `sqlcmd` utility to run [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts from the command prompt, including the ability to interactively develop scripts.</span></span>|[<span data-ttu-id="59356-143">sqlcmd 使用說明主題</span><span class="sxs-lookup"><span data-stu-id="59356-143">sqlcmd How-to Topics</span></span>](../../database-engine/sqlcmd-how-to-topics.md)|  
|<span data-ttu-id="59356-144">描述如何將 SQL Server 元件整合至 Windows PowerShell 2.0 環境，然後建立 PowerShell 指令碼以管理 SQL Server 執行個體和物件。</span><span class="sxs-lookup"><span data-stu-id="59356-144">Describes how to integrate the SQL Server components into a Windows PowerShell 2.0 environment and then build PowerShell scripts for managing SQL Server instances and objects.</span></span>|[<span data-ttu-id="59356-145">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="59356-145">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)|  
|<span data-ttu-id="59356-146">描述如何使用 [產生和發佈指令碼精靈]  ，建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼以重新建立資料庫中的一個或多個物件。</span><span class="sxs-lookup"><span data-stu-id="59356-146">Describes how to use the **Generate and Publish Scripts** wizard to create [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts that recreate one or more of the objects from a database.</span></span>|[<span data-ttu-id="59356-147">產生指令碼 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="59356-147">Generate Scripts &#40;SQL Server Management Studio&#41;</span></span>](generate-scripts-sql-server-management-studio.md)|  
  
## <a name="see-also"></a><span data-ttu-id="59356-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59356-148">See Also</span></span>  
 <span data-ttu-id="59356-149">[sqlcmd 公用程式](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="59356-149">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="59356-150">教學課程：撰寫 Transact-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="59356-150">Tutorial: Writing Transact-SQL Statements</span></span>](../../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
