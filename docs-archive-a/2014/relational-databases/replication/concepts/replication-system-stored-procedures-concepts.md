---
title: 複寫系統預存程序概念 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- stored procedures [SQL Server replication], programming
- programming [SQL Server replication], system stored procedures
- programming interfaces [SQL Server replication]
- system stored procedures [SQL Server replication]
- replication [SQL Server], how-to topics
ms.assetid: 816d2bda-ed72-43ec-aa4d-7ee3dc25fd8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 50536e5b6816c84dff26c9c9f99c46d02272b7de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709213"
---
# <a name="replication-system-stored-procedures-concepts"></a><span data-ttu-id="d15b2-102">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="d15b2-102">Replication System Stored Procedures Concepts</span></span>
  <span data-ttu-id="d15b2-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，系統預存程序可提供複寫拓撲中所有使用者可設定的功能之程式存取權。</span><span class="sxs-lookup"><span data-stu-id="d15b2-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], programmatic access to all of the user-configurable functionality in a replication topology is provided by system stored procedures.</span></span> <span data-ttu-id="d15b2-104">雖然使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 或是 sqlcmd 命令列公用程式，可以個別執行預存程序，但是撰寫 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼檔案對於執行一連串的邏輯複寫工作非常有幫助。</span><span class="sxs-lookup"><span data-stu-id="d15b2-104">While stored procedures may be executed individually using the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or the sqlcmd command-line utility, it may be beneficial to write [!INCLUDE[tsql](../../../includes/tsql-md.md)] script files that can be executed to perform a logical sequence of replication tasks.</span></span>  
  
 <span data-ttu-id="d15b2-105">指令碼複寫工作提供下列好處：</span><span class="sxs-lookup"><span data-stu-id="d15b2-105">Scripting replication tasks provides the following benefits:</span></span>  
  
-   <span data-ttu-id="d15b2-106">永久保留用以部署複寫拓撲的步驟副本。</span><span class="sxs-lookup"><span data-stu-id="d15b2-106">Keeps a permanent copy of the steps used to deploy your replication topology.</span></span>  
  
-   <span data-ttu-id="d15b2-107">使用單一指令碼來設定多個訂閱者。</span><span class="sxs-lookup"><span data-stu-id="d15b2-107">Uses a single script to configure multiple Subscribers.</span></span>  
  
-   <span data-ttu-id="d15b2-108">讓新資料庫管理員快速上手，讓他們能夠評估、了解、變更或是疑難排解程式碼。</span><span class="sxs-lookup"><span data-stu-id="d15b2-108">Quickly educates new database administrators by enabling them to evaluate, understand, change, or troubleshoot the code.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d15b2-109">指令碼有可能成為安全性弱點的根源；因為它們可以在使用者未查覺或介入的情況下叫用系統函數，且可能以純文字的方式包含安全性認證。</span><span class="sxs-lookup"><span data-stu-id="d15b2-109">Scripts can be the source of security vulnerabilities; they can invoke system functions without user knowledge or intervention and may contain security credentials in plain text.</span></span> <span data-ttu-id="d15b2-110">使用指令碼之前，請先檢閱它們是否有安全性問題。</span><span class="sxs-lookup"><span data-stu-id="d15b2-110">Review scripts for security issues before you use them.</span></span>  
  
## <a name="creating-replication-scripts"></a><span data-ttu-id="d15b2-111">建立複寫指令碼</span><span class="sxs-lookup"><span data-stu-id="d15b2-111">Creating Replication Scripts</span></span>  
 <span data-ttu-id="d15b2-112">從複寫的觀點來看，指令碼是一系列的一或多個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，其中每個陳述式會執行複寫預存程序。</span><span class="sxs-lookup"><span data-stu-id="d15b2-112">From the standpoint of replication, a script is a series of one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements where each statement executes a replication stored procedure.</span></span> <span data-ttu-id="d15b2-113">指令碼是文字檔案，通常具有 .sql 副檔名，可以使用 sqlcmd 公用程式來執行。</span><span class="sxs-lookup"><span data-stu-id="d15b2-113">Scripts are text files, often with a .sql file extension, that can be run using the sqlcmd utility.</span></span> <span data-ttu-id="d15b2-114">當執行指令碼檔案時，公用程式會執行儲存在檔案中的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d15b2-114">When a script file is run, the utility executes the SQL statements stored in the file.</span></span> <span data-ttu-id="d15b2-115">同樣地，在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 專案中可以將指令碼儲存為查詢物件。</span><span class="sxs-lookup"><span data-stu-id="d15b2-115">Similarly, a script can be stored as a query object in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span>  
  
 <span data-ttu-id="d15b2-116">複寫指令碼可以用下列方式建立：</span><span class="sxs-lookup"><span data-stu-id="d15b2-116">Replication scripts can be created in the following ways:</span></span>  
  
-   <span data-ttu-id="d15b2-117">手動建立指令碼。</span><span class="sxs-lookup"><span data-stu-id="d15b2-117">Manually create the script.</span></span>  
  
-   <span data-ttu-id="d15b2-118">使用在複寫精靈中提供的指令碼產生功能或是</span><span class="sxs-lookup"><span data-stu-id="d15b2-118">Use the script generation features that are provided in the replication wizards or</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="d15b2-119">第 1 課：建立 Windows Azure 儲存體物件[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d15b2-119">.</span></span> <span data-ttu-id="d15b2-120">如需詳細資訊，請參閱 [Scripting Replication](../scripting-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="d15b2-120">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
-   <span data-ttu-id="d15b2-121">使用 Replication Management Objects (RMO) 以程式設計的方式產生指令碼來建立 RMO 物件。</span><span class="sxs-lookup"><span data-stu-id="d15b2-121">Use Replication Management Objects (RMOs) to programmatically generate the script to create an RMO object.</span></span>  
  
 <span data-ttu-id="d15b2-122">當您手動建立複寫指令碼時，請記住下列考量：</span><span class="sxs-lookup"><span data-stu-id="d15b2-122">When you manually create replication scripts, keep the following considerations in mind:</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="d15b2-123">指令碼有一或多個批次。</span><span class="sxs-lookup"><span data-stu-id="d15b2-123">scripts have one or more batches.</span></span> <span data-ttu-id="d15b2-124">GO 命令代表批次的結尾。</span><span class="sxs-lookup"><span data-stu-id="d15b2-124">The GO command signals the end of a batch.</span></span> <span data-ttu-id="d15b2-125">如果 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼沒有任何 GO 命令，則會視為單一批次執行。</span><span class="sxs-lookup"><span data-stu-id="d15b2-125">If a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script does not have any GO commands, it is executed as a single batch.</span></span>  
  
-   <span data-ttu-id="d15b2-126">當在單一批次中執行多個複寫預存程序時，在第一個程序之後，在批次中所有後續的程序，前面都必須加上 EXECUTE 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d15b2-126">When executing multiple replication stored procedures in a single batch, after the first procedure, all subsequent procedures in the batch must be preceded by the EXECUTE keyword.</span></span>  
  
-   <span data-ttu-id="d15b2-127">在批次中所有預存程序都必須在批次將執行之前編譯。</span><span class="sxs-lookup"><span data-stu-id="d15b2-127">All stored procedures in a batch must compile before a batch will execute.</span></span> <span data-ttu-id="d15b2-128">不過，只要批次已編譯且執行計劃已建立，就可能會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="d15b2-128">However, once the batch has been compiled, and an execution plan has been created, a run-time error may or may not occur.</span></span>  
  
-   <span data-ttu-id="d15b2-129">當建立指令碼以設定複寫時，應該使用 Windows 驗證來避免在指令碼檔案中儲存安全性認證。</span><span class="sxs-lookup"><span data-stu-id="d15b2-129">When creating scripts to configure replication, you should use Windows Authentication to avoid storing security credentials in the script file.</span></span> <span data-ttu-id="d15b2-130">如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。</span><span class="sxs-lookup"><span data-stu-id="d15b2-130">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
## <a name="sample-replication-script"></a><span data-ttu-id="d15b2-131">範例複寫指令碼</span><span class="sxs-lookup"><span data-stu-id="d15b2-131">Sample Replication Script</span></span>  
 <span data-ttu-id="d15b2-132">您可以執行下列指令碼，在伺服器上安裝發行和散發。</span><span class="sxs-lookup"><span data-stu-id="d15b2-132">The following script can be executed to setup publishing and distribution on a server.</span></span>  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
 <span data-ttu-id="d15b2-133">在本機上可以將這個指令碼儲存為 `instdistpub.sql`，以便在需要時執行或重新執行它。</span><span class="sxs-lookup"><span data-stu-id="d15b2-133">This script can then be saved locally as `instdistpub.sql` so that it can be run or rerun when needed.</span></span>  
  
 <span data-ttu-id="d15b2-134">前述指令碼包括 **sqlcmd** 指令碼變數，在《[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》中有許多複寫程式碼範例使用這些變數。</span><span class="sxs-lookup"><span data-stu-id="d15b2-134">The previous script includes **sqlcmd** scripting variables, which are used in many of the replication code samples in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span> <span data-ttu-id="d15b2-135">指令碼變數是藉由使用 `$(MyVariable)` 語法所定義。</span><span class="sxs-lookup"><span data-stu-id="d15b2-135">Scripting variables are defined by using `$(MyVariable)` syntax.</span></span> <span data-ttu-id="d15b2-136">在命令列或是在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中，可以將變數值傳遞給指令碼。</span><span class="sxs-lookup"><span data-stu-id="d15b2-136">Values for variables can be passed to a script at the command line or in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d15b2-137">如需詳細資訊，請參閱本主題中的下一節「執行複寫指令碼」。</span><span class="sxs-lookup"><span data-stu-id="d15b2-137">For more information, see the next section in this topic, "Executing Replication Scripts."</span></span>  
  
## <a name="executing-replication-scripts"></a><span data-ttu-id="d15b2-138">執行複寫指令碼</span><span class="sxs-lookup"><span data-stu-id="d15b2-138">Executing Replication Scripts</span></span>  
 <span data-ttu-id="d15b2-139">建立之後，複寫指令碼可以用下列其中一種方式來執行：</span><span class="sxs-lookup"><span data-stu-id="d15b2-139">Once created, a replication script can be executed in one of the following ways:</span></span>  
  
### <a name="creating-a-sql-query-file-in-sql-server-management-studio"></a><span data-ttu-id="d15b2-140">在 SQL Server Management Studio 中建立 SQL 查詢檔案</span><span class="sxs-lookup"><span data-stu-id="d15b2-140">Creating a SQL Query File in SQL Server Management Studio</span></span>  
 <span data-ttu-id="d15b2-141">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 專案中，可以將複寫 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼檔案建立成 SQL 查詢檔案。</span><span class="sxs-lookup"><span data-stu-id="d15b2-141">A replication [!INCLUDE[tsql](../../../includes/tsql-md.md)] script file can be created as a SQL Query file in a [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] project.</span></span> <span data-ttu-id="d15b2-142">在寫入指令碼之後，可以為此查詢檔案建立資料庫的連接，而且可以執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="d15b2-142">After the script is written, a connection can be made to the database for this query file and the script can be executed.</span></span> <span data-ttu-id="d15b2-143">如需如何使用建立腳本的詳細資訊 [!INCLUDE[tsql](../../../includes/tsql-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，請參閱[查詢和文字編輯器 &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md)) 。</span><span class="sxs-lookup"><span data-stu-id="d15b2-143">For more information about how to create [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../../scripting/query-and-text-editors-sql-server-management-studio.md)).</span></span>  
  
 <span data-ttu-id="d15b2-144">若要使用包含指令碼變數的指令碼，[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 必須在 **sqlcmd** 模式下執行。</span><span class="sxs-lookup"><span data-stu-id="d15b2-144">To use a script that includes scripting variables, [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] must be running in **sqlcmd** mode.</span></span> <span data-ttu-id="d15b2-145">在 **sqlcmd** 模式中，查詢編輯器會接受 **sqlcmd** 特有的其他語法，例如 `:setvar`，它是用於變數值。</span><span class="sxs-lookup"><span data-stu-id="d15b2-145">In **sqlcmd** mode, the Query Editor accepts additional syntax specific to **sqlcmd**, such as `:setvar`, which is used to a value for a variable.</span></span> <span data-ttu-id="d15b2-146">如需 **sqlcmd** 模式的詳細資訊，請參閱[使用查詢編輯器編輯 SQLCMD 指令碼](../../scripting/edit-sqlcmd-scripts-with-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="d15b2-146">For more information about **sqlcmd** mode, see [Edit SQLCMD Scripts with Query Editor](../../scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span> <span data-ttu-id="d15b2-147">在下列指令碼中，`:setvar` 是用以提供 `$(DistPubServer)` 變數的值。</span><span class="sxs-lookup"><span data-stu-id="d15b2-147">In the following script, `:setvar` is used to provide a value for the `$(DistPubServer)` variable.</span></span>  
  
```  
:setvar DistPubServer N'MyPublisherAndDistributor';  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
--  
-- Additional code goes here  
--  
```  
  
### <a name="using-the-sqlcmd-utility-from-the-command-line"></a><span data-ttu-id="d15b2-148">從命令列使用 sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="d15b2-148">Using the sqlcmd Utility from the Command Line</span></span>  
 <span data-ttu-id="d15b2-149">下列範例示範如何在命令列使用 [sqlcmd 公用程式](../../../tools/sqlcmd-utility.md)來執行 `instdistpub.sql` 指令碼檔案：</span><span class="sxs-lookup"><span data-stu-id="d15b2-149">The following example shows how the command line is used to execute the `instdistpub.sql` script file using the [sqlcmd utility](../../../tools/sqlcmd-utility.md):</span></span>  
  
```  
sqlcmd.exe -E -S sqlserverinstance -i C:\instdistpub.sql -o C:\output.log -v DistPubServer="N'MyDistributorAndPublisher'"  
```  
  
 <span data-ttu-id="d15b2-150">在此範例中，`-E` 參數指出連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時所使用的 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d15b2-150">In this example, the `-E` switch indicates that Windows Authentication is used when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d15b2-151">在使用 Windows 驗證時，在指令碼檔案中不需要儲存使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="d15b2-151">When using Windows Authentication, there is no need to store a username and password in the script file.</span></span> <span data-ttu-id="d15b2-152">指令碼檔案的名稱與路徑是由 `-i` 參數所指定，而輸出檔案的名稱則是由 `-o` 參數所指定 (使用這個參數時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的輸出會寫入這個檔案，而不是主控台)。</span><span class="sxs-lookup"><span data-stu-id="d15b2-152">The name and path of the script file is specified by the `-i` switch and the name of the output file is specified by the `-o` switch (output from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is written to this file instead of the console when this switch is used).</span></span> <span data-ttu-id="d15b2-153">`sqlcmd` 公用程式可讓您在執行階段，使用 `-v` 參數，將指令碼變數傳遞到 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="d15b2-153">The `sqlcmd` utility enables you to pass scripting variables to a [!INCLUDE[tsql](../../../includes/tsql-md.md)] script at runtime using the `-v` switch.</span></span> <span data-ttu-id="d15b2-154">在此範例中，`sqlcmd` 會在執行之前，以值 `N'MyDistributorAndPublisher'` 取代指令碼中 `$(DistPubServer)` 的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="d15b2-154">In this example, `sqlcmd` replaces every instance of `$(DistPubServer)` in the script with the value `N'MyDistributorAndPublisher'` before execution.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d15b2-155">`-X` 參數會停用指令碼變數。</span><span class="sxs-lookup"><span data-stu-id="d15b2-155">The `-X` switch disables scripting variables.</span></span>  
  
### <a name="automating-tasks-in-a-batch-file"></a><span data-ttu-id="d15b2-156">以批次檔自動化工作</span><span class="sxs-lookup"><span data-stu-id="d15b2-156">Automating Tasks in a Batch File</span></span>  
 <span data-ttu-id="d15b2-157">透過使用批次檔，可以在相同的批次檔中，自動化複寫管理工作、複寫同步處理工作以及其他工作。</span><span class="sxs-lookup"><span data-stu-id="d15b2-157">By using a batch file, replication administration tasks, replication synchronization tasks, and other tasks can be automated in the same batch file.</span></span> <span data-ttu-id="d15b2-158">下列批次檔使用 **sqlcmd** 公用程式，卸除和重新建立訂閱資料庫並加入合併提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="d15b2-158">The following batch file uses the **sqlcmd** utility to drop and recreate the subscription database and add a merge pull subscription.</span></span> <span data-ttu-id="d15b2-159">接著檔案會叫用合併代理程式以同步處理新訂閱：</span><span class="sxs-lookup"><span data-stu-id="d15b2-159">Then the file invokes the merge agent to synchronize the new subscription:</span></span>  
  
```  
REM ----------------------Script to synchronize merge subscription ----------------------  
REM -- Creates subscription database and   
REM -- synchronizes the subscription to MergeSalesPerson.  
REM -- Current computer acts as both Publisher and Subscriber.  
REM -------------------------------------------------------------------------------------  
  
SET Publisher=%computername%  
SET Subscriber=%computername%  
SET PubDb=AdventureWorks  
SET SubDb=AdventureWorksReplica  
SET PubName=AdvWorksSalesOrdersMerge  
  
REM -- Drop and recreate the subscription database at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE master IF EXISTS (SELECT * FROM sysdatabases WHERE name='%SubDb%' ) DROP DATABASE %SubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE master CREATE DATABASE %SubDb%"  
  
REM -- Add a pull subscription at the Subscriber  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb% EXEC sp_addmergepullsubscription @publisher = %Publisher%, @publication = %PubName%, @publisher_db = %PubDb%"  
sqlcmd /S%Subscriber% /E /Q"USE %SubDb%  EXEC sp_addmergepullsubscription_agent @publisher = %Publisher%, @publisher_db = %PubDb%, @publication = %PubName%, @subscriber = %Subscriber%, @subscriber_db = %SubDb%, @distributor = %Publisher%"  
  
REM -- This batch file starts the merge agent at the Subscriber to   
REM -- synchronize a pull subscription to a merge publication.  
REM -- The following must be supplied on one line.  
"\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE"  -Publisher  %Publisher% -Subscriber  %Subscriber%  -Distributor %Publisher%  -PublisherDB  %PubDb% -SubscriberDB %SubDb% -Publication %PubName% -PublisherSecurityMode 1 -OutputVerboseLevel 1  -Output  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1 -Validate 3  
  
```  
  
## <a name="scripting-common-replication-tasks"></a><span data-ttu-id="d15b2-160">撰寫一般複寫工作的指令碼</span><span class="sxs-lookup"><span data-stu-id="d15b2-160">Scripting Common Replication Tasks</span></span>  
 <span data-ttu-id="d15b2-161">下列是一些最常使用系統預存程序來編寫指令碼的複寫工作：</span><span class="sxs-lookup"><span data-stu-id="d15b2-161">The following are some of the most common replication tasks can be scripted using system stored procedures:</span></span>  
  
-   <span data-ttu-id="d15b2-162">設定發行和散發</span><span class="sxs-lookup"><span data-stu-id="d15b2-162">Configuring publishing and distribution</span></span>  
  
-   <span data-ttu-id="d15b2-163">修改發行者和散發者屬性</span><span class="sxs-lookup"><span data-stu-id="d15b2-163">Modifying Publisher and Distributor properties</span></span>  
  
-   <span data-ttu-id="d15b2-164">停用發行與散發</span><span class="sxs-lookup"><span data-stu-id="d15b2-164">Disabling publishing and distribution</span></span>  
  
-   <span data-ttu-id="d15b2-165">建立發行集及定義發行項</span><span class="sxs-lookup"><span data-stu-id="d15b2-165">Creating publications and defining articles</span></span>  
  
-   <span data-ttu-id="d15b2-166">刪除發行集及發行項</span><span class="sxs-lookup"><span data-stu-id="d15b2-166">Deleting publications and articles</span></span>  
  
-   <span data-ttu-id="d15b2-167">建立提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-167">Creating a pull subscription</span></span>  
  
-   <span data-ttu-id="d15b2-168">修改提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-168">Modifying a pull subscription</span></span>  
  
-   <span data-ttu-id="d15b2-169">刪除提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-169">Deleting a pull subscription</span></span>  
  
-   <span data-ttu-id="d15b2-170">建立發送訂閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-170">Creating a push subscription</span></span>  
  
-   <span data-ttu-id="d15b2-171">修改提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-171">Modifying a push subscription</span></span>  
  
-   <span data-ttu-id="d15b2-172">刪除發送訂閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-172">Deleting a push subscription</span></span>  
  
-   <span data-ttu-id="d15b2-173">同步處理提取訂閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-173">Synchronizing a pull subscription</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d15b2-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d15b2-174">See Also</span></span>  
 <span data-ttu-id="d15b2-175">[複寫程式設計概念](replication-programming-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="d15b2-175">[Replication Programming Concepts](replication-programming-concepts.md) </span></span>  
 <span data-ttu-id="d15b2-176">[複寫預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d15b2-176">[Replication Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="d15b2-177">編寫複寫指令碼</span><span class="sxs-lookup"><span data-stu-id="d15b2-177">Scripting Replication</span></span>](../scripting-replication.md)  
  
  
