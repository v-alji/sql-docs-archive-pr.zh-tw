---
title: 啟動及使用 Database Engine Tuning Advisor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
f1_keywords:
- sql12.dta.advancedtuningoptions.f1
- sql12.dta.general.f1
- sql12.dta.tuningoptions.f1
- sql12.dta.workload.f1
- sql12.dta.progress.f1
- sql12.dta.options.f1
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], starting
ms.assetid: a4e3226a-3917-4ec8-bdf0-472879d231c9
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 46f8e49de657d7021d846c7e57022a580b877f8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701095"
---
# <a name="start-and-use-the-database-engine-tuning-advisor"></a><span data-ttu-id="a92ea-102">啟動及使用 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a92ea-102">Start and Use the Database Engine Tuning Advisor</span></span>
  <span data-ttu-id="a92ea-103">此主題描述如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中啟動及使用 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="a92ea-103">This topic describes how to start and use Database Engine Tuning Advisor in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a92ea-104">如需如何在微調資料庫後檢視及處理結果的資訊，請參閱 [檢視及處理 Database Engine Tuning Advisor 的輸出](database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-104">For information about how to view and work with the results after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
##  <a name="initialize-the-database-engine-tuning-advisor"></a><a name="Initialize"></a> <span data-ttu-id="a92ea-105">初始化 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a92ea-105">Initialize the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="a92ea-106">在第一次使用時， **系統管理員 (sysadmin)** 固定伺服器角色的成員使用者必須初始化 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="a92ea-106">On first use, a user who is member of the **sysadmin** fixed server role must initialize the Database Engine Tuning Advisor.</span></span> <span data-ttu-id="a92ea-107">原因是必須在 `msdb` 資料庫中建立數個系統資料表，以支援微調作業。</span><span class="sxs-lookup"><span data-stu-id="a92ea-107">This is because several system tables must be created in the `msdb` database to support tuning operations.</span></span> <span data-ttu-id="a92ea-108">初始化也可讓屬於 **db_owner** 固定資料庫角色成員的使用者，微調他們所擁有資料庫中資料表的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-108">Initialization also enables users that are members of the **db_owner** fixed database role to tune workloads on tables in databases that they own.</span></span>  
  
 <span data-ttu-id="a92ea-109">具有系統管理員權限的使用者必須執行下列其中一種動作：</span><span class="sxs-lookup"><span data-stu-id="a92ea-109">A user that has system administrator permissions must perform either of the following actions:</span></span>  
  
-   <span data-ttu-id="a92ea-110">使用 Database Engine Tuning Advisor 圖形化使用者介面連接到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="a92ea-110">Use the Database Engine Tuning Advisor graphical user interface to connect to an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="a92ea-111">如需詳細資訊，請參閱本主題稍後的＜ [啟動 Database Engine Tuning Advisor](#Start) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-111">For more information, see [Start the Database Engine Tuning Advisor](#Start) later in this topic.</span></span>  
  
-   <span data-ttu-id="a92ea-112">使用 **dta** 公用程式微調第一個工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-112">Use the **dta** utility to tune the first workload.</span></span> <span data-ttu-id="a92ea-113">如需詳細資訊，請參閱本主題稍後的＜ [使用 dta 公用程式](#dta) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-113">For more information, see [Use the dta Utility](#dta) later in this topic.</span></span>  
  
##  <a name="start-the-database-engine-tuning-advisor"></a><a name="Start"></a> <span data-ttu-id="a92ea-114">啟動 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a92ea-114">Start the Database Engine Tuning Advisor</span></span>  
 <span data-ttu-id="a92ea-115">您可以利用若干不同方法來啟動 Database Engine Tuning Advisor 圖形化使用者介面 (GUI)，以支援各種狀況中的資料庫微調。</span><span class="sxs-lookup"><span data-stu-id="a92ea-115">You can start the Database Engine Tuning Advisor graphical user interface (GUI) in several different ways to support database tuning in a variety of scenarios.</span></span> <span data-ttu-id="a92ea-116">啟動 Database Engine Tuning Advisor 的不同方式包括：從 **[開始]** 功能表、從 **中的** [工具] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]功能表、從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的查詢編輯器，以及從 **中的** [工具] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]功能表。</span><span class="sxs-lookup"><span data-stu-id="a92ea-116">The different ways to start Database Engine Tuning Advisor include: from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], from the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and from the **Tools** menu in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="a92ea-117">當您第一次啟動 Database Engine Tuning Advisor 時，應用程式會顯示一個 **[連接到伺服器]** 對話方塊，供您指定要連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a92ea-117">When you first start Database Engine Tuning Advisor, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a92ea-118">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在執行單一使用者模式時，請勿啟動 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="a92ea-118">Do not start Database Engine Tuning Advisor when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running in single-user mode.</span></span> <span data-ttu-id="a92ea-119">如果伺服器在單一使用者模式，嘗試啟動 Database Engine Tuning Advisor 會傳回錯誤，它將不會啟動。</span><span class="sxs-lookup"><span data-stu-id="a92ea-119">If you attempt to start it while the server is in single-user mode, an error will be returned and Database Engine Tuning Advisor will not start.</span></span> <span data-ttu-id="a92ea-120">如需單一使用者模式的詳細資訊，請參閱 [以單一使用者模式啟動 SQL Server](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-120">For more information about single-user mode, see [Start SQL Server in Single-User Mode](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md).</span></span>  
  
#### <a name="to-start-database-engine-tuning-advisor-from-the-windows-start-menu"></a><span data-ttu-id="a92ea-121">從 Windows 的 [開始] 功能表中啟動 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a92ea-121">To start Database Engine Tuning Advisor from the Windows Start menu</span></span>  
  
1.  <span data-ttu-id="a92ea-122">在 **[開始]** 功能表上，依序指向 **[所有程式]** 、 **[Microsoft SQL Server]** 、 **[效能工具]** ，然後按一下 **[Database Engine Tuning Advisor]** 。</span><span class="sxs-lookup"><span data-stu-id="a92ea-122">On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server**, point to **Performance Tools**, and then click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-management-studio"></a><span data-ttu-id="a92ea-123">若要在 SQL Server Management Studio 中啟動 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a92ea-123">To start the Database Engine Tuning Advisor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="a92ea-124">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [工具] 功能表上，按一下 [Database Engine Tuning Advisor]。</span><span class="sxs-lookup"><span data-stu-id="a92ea-124">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-from-the-sql-server-management-studio-query-editor"></a><span data-ttu-id="a92ea-125">若要從 SQL Server Management Studio 查詢編輯器中啟動 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a92ea-125">To start the Database Engine Tuning Advisor from the SQL Server Management Studio Query Editor</span></span>  
  
1.  <span data-ttu-id="a92ea-126">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中，開啟一個 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-126">Open a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a92ea-127">如需詳細資訊，請參閱[查詢與文字編輯器 &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-127">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="a92ea-128">選取 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼中的一項查詢，或選取整份指令碼，以滑鼠右鍵按一下選取範圍，選擇 [在 Database Engine Tuning Advisor 中分析查詢]。</span><span class="sxs-lookup"><span data-stu-id="a92ea-128">Select a query in the [!INCLUDE[tsql](../../includes/tsql-md.md)] script, or select the entire script, right-click the selection, and choose **Analyze Query in Database Engine Tuning Advisor**.</span></span> <span data-ttu-id="a92ea-129">此時會開啟 Database Engine Tuning Advisor GUI，且會將指令碼匯入來作為一份 XML 檔工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-129">The Database Engine Tuning Advisor GUI opens and imports the script as an XML file workload.</span></span> <span data-ttu-id="a92ea-130">您可以指定工作階段名稱和微調選項來微調做為工作負載的所選 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="a92ea-130">You can specify a session name and tuning options to tune the selected [!INCLUDE[tsql](../../includes/tsql-md.md)] queries as your workload.</span></span>  
  
#### <a name="to-start-the-database-engine-tuning-advisor-in-sql-server-profiler"></a><span data-ttu-id="a92ea-131">若要在 SQL Server Profiler 中啟動 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a92ea-131">To start the Database Engine Tuning Advisor in SQL Server Profiler</span></span>  
  
1.  <span data-ttu-id="a92ea-132">在 SQL Server Profiler 的 **[工具]** 功能表上，按一下 **[Database Engine Tuning Advisor]** 。</span><span class="sxs-lookup"><span data-stu-id="a92ea-132">On the SQL Server Profiler **Tools** menu, click **Database Engine Tuning Advisor**.</span></span>  
  
##  <a name="create-a-workload"></a><a name="Create"></a> <span data-ttu-id="a92ea-133">建立工作負載</span><span class="sxs-lookup"><span data-stu-id="a92ea-133">Create a Workload</span></span>  
 <span data-ttu-id="a92ea-134">工作負載是針對需要微調的一或多個資料庫來執行的一組 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a92ea-134">A workload is a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against a database or databases that you want to tune.</span></span> <span data-ttu-id="a92ea-135">Database Engine Tuning Advisor 會分析這些工作負載，以建議可改善伺服器查詢效能的索引或資料分割策略。</span><span class="sxs-lookup"><span data-stu-id="a92ea-135">Database Engine Tuning Advisor analyzes these workloads to recommend indexes or partitioning strategies that will improve your server's query performance.</span></span>  
  
 <span data-ttu-id="a92ea-136">您可以使用下列其中一個方法，建立新的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-136">You can create a workload by using one of the following methods.</span></span>  
  
-   <span data-ttu-id="a92ea-137">使用計畫快取做為工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-137">Use the plan cache as a workload.</span></span> <span data-ttu-id="a92ea-138">利用此操作，您可以不必手動建立工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-138">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="a92ea-139">如需詳細資訊，請參閱本主題稍後的＜ [微調資料庫](#Tune) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-139">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
-   <span data-ttu-id="a92ea-140">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [查詢編輯器] 或您慣用的文字編輯器，可手動建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-140">Use the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or your favorite text editor to manually create [!INCLUDE[tsql](../../includes/tsql-md.md)] script workloads.</span></span>  
  
-   <span data-ttu-id="a92ea-141">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 建立追蹤檔案或追蹤資料表工作負載</span><span class="sxs-lookup"><span data-stu-id="a92ea-141">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create trace file or trace table workloads</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a92ea-142">使用追蹤資料表做為工作負載時，該資料表必須位於 Database Engine Tuning Advisor 所微調的同一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a92ea-142">When using a trace table as a workload, that table must exist on the same server where Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="a92ea-143">若您在不同的伺服器上建立追蹤資料表，請將其移至 Database Engine Tuning Advisor 正在微調的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a92ea-143">If you create the trace table on a different server, then move it to the server where Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="a92ea-144">工作負載亦可內嵌於 XML 輸入檔中，您也可於該檔中指定各事件的加權。</span><span class="sxs-lookup"><span data-stu-id="a92ea-144">Workloads can also be embedded in an XML input file, where you can also specify a weight for each event.</span></span> <span data-ttu-id="a92ea-145">如需有關指定內嵌工作負載的詳細資訊，請參閱本主題稍後的＜ [建立 XML 輸入檔](#XMLInput) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-145">For more information about specifying embedded workloads, see [Create an XML Input File](#XMLInput) later in this topic.</span></span>  
  
###  <a name="to-create-transact-sql-script-workloads"></a><a name="SSMS"></a> <span data-ttu-id="a92ea-146">建立 Transact-SQL 指令碼工作負載</span><span class="sxs-lookup"><span data-stu-id="a92ea-146">To create Transact-SQL script workloads</span></span>  
  
1.  <span data-ttu-id="a92ea-147">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中啟動 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="a92ea-147">Launch the Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="a92ea-148">如需詳細資訊，請參閱[查詢與文字編輯器 &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-148">For more information, see [Query and Text Editors &#40;SQL Server Management Studio&#41;](../scripting/query-and-text-editors-sql-server-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="a92ea-149">在 [查詢編輯器] 中輸入您的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="a92ea-149">Type your [!INCLUDE[tsql](../../includes/tsql-md.md)] script into the Query Editor.</span></span> <span data-ttu-id="a92ea-150">此指令碼應包含一組 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，可針對您要微調的資料庫來執行。</span><span class="sxs-lookup"><span data-stu-id="a92ea-150">This script should contain a set of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that execute against the database or databases that you want to tune.</span></span>  
  
3.  <span data-ttu-id="a92ea-151">請用 **.sql** 副檔名儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-151">Save the file with a **.sql** extension.</span></span> <span data-ttu-id="a92ea-152">Database Engine Tuning Advisor GUI 及命令列 **dta** 公用程式，都可使用此 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼作為工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-152">The Database Engine Tuning Advisor GUI and the command-line **dta** utility can use this [!INCLUDE[tsql](../../includes/tsql-md.md)] script as a workload.</span></span>  
  
###  <a name="to-create-trace-file-and-trace-table-workloads"></a><a name="Profiler"></a> <span data-ttu-id="a92ea-153">建立追蹤檔及追蹤資料表工作負載</span><span class="sxs-lookup"><span data-stu-id="a92ea-153">To create trace file and trace table workloads</span></span>  
  
1.  <span data-ttu-id="a92ea-154">使用下列其中一種方法啟動 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="a92ea-154">Launch [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a92ea-155">在 **[開始]** 功能表中，依序指向 **[所有程式]** 、 **[Microsoft SQL Server]** 與 **[效能工具]** ，然後按一下 **[SQL Server Profiler]** 。</span><span class="sxs-lookup"><span data-stu-id="a92ea-155">On the **Start** menu, point to **All Programs**, **Microsoft SQL Server**, **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
    -   <span data-ttu-id="a92ea-156">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，按一下 **[工具]** 功能表，然後按一下 **[SQL Server Profiler]** 。</span><span class="sxs-lookup"><span data-stu-id="a92ea-156">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click the **Tools** menu, and then click **SQL Server Profiler**.</span></span>  
  
2.  <span data-ttu-id="a92ea-157">依下列程序，使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [微調] 範本來建立追蹤檔案或資料表：</span><span class="sxs-lookup"><span data-stu-id="a92ea-157">Create a trace file or table as described in the following procedures that uses the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tuning** template:</span></span>  
  
    -   [<span data-ttu-id="a92ea-158">建立追蹤 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="a92ea-158">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
    -   [<span data-ttu-id="a92ea-159">將追蹤結果儲存至檔案 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="a92ea-159">Save Trace Results to a File &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)  
  
         <span data-ttu-id="a92ea-160">Database Engine Tuning Advisor 會假設工作負載追蹤檔案為換用檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-160">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="a92ea-161">如需有關換用檔案的詳細資訊，請參閱＜ [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-161">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
    -   [<span data-ttu-id="a92ea-162">將追蹤結果儲存到資料表 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="a92ea-162">Save Trace Results to a Table &#40;SQL Server Profiler&#41;</span></span>](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)  
  
         <span data-ttu-id="a92ea-163">將追蹤資料表作為工作負載使用之前，請確定已停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="a92ea-163">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
 <span data-ttu-id="a92ea-164">我們建議您使用 SQL Server Profiler [微調] 範本來擷取 Database Engine Tuning Advisor 的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-164">We recommend that you use the SQL Server Profiler Tuning template for capturing workloads for Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="a92ea-165">若您想要使用自己的範本，請確定已擷取下列追蹤事件：</span><span class="sxs-lookup"><span data-stu-id="a92ea-165">If you want to use your own template, ensure that the following trace events are captured:</span></span>  
  
-   <span data-ttu-id="a92ea-166">**RPC:Completed**</span><span class="sxs-lookup"><span data-stu-id="a92ea-166">**RPC:Completed**</span></span>  
  
-   <span data-ttu-id="a92ea-167">**SQL:BatchCompleted**</span><span class="sxs-lookup"><span data-stu-id="a92ea-167">**SQL:BatchCompleted**</span></span>  
  
-   <span data-ttu-id="a92ea-168">**SP:StmtCompleted**</span><span class="sxs-lookup"><span data-stu-id="a92ea-168">**SP:StmtCompleted**</span></span>  
  
 <span data-ttu-id="a92ea-169">您也可以使用這些追蹤事件的 **Starting** 版本，</span><span class="sxs-lookup"><span data-stu-id="a92ea-169">You can also use the **Starting** versions of these trace events.</span></span> <span data-ttu-id="a92ea-170">例如 **SQL:BatchStarting**。</span><span class="sxs-lookup"><span data-stu-id="a92ea-170">For example, **SQL:BatchStarting**.</span></span> <span data-ttu-id="a92ea-171">不過，這些追蹤事件的 **Completed** 版本包含 **Duration** 資料行，能讓 Database Engine Tuning Advisor 更有效率地微調工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-171">However, the **Completed** versions of these trace events include the **Duration** column, which allows Database Engine Tuning Advisor to more effectively tune the workload.</span></span> <span data-ttu-id="a92ea-172">Database Engine Tuning Advisor 不會微調其他類型的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="a92ea-172">Database Engine Tuning Advisor does not tune other types of trace events.</span></span> <span data-ttu-id="a92ea-173">如需這些追蹤事件的詳細資訊，請參閱＜ [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) ＞和＜ [TSQL Event Category](../event-classes/tsql-event-category.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-173">For more information about these trace events, see [Stored Procedures Event Category](../event-classes/stored-procedures-event-category.md) and [TSQL Event Category](../event-classes/tsql-event-category.md).</span></span> <span data-ttu-id="a92ea-174">如需使用「SQL 追蹤」預存程序來建立追蹤檔案工作負載的資訊，請參閱[建立追蹤 &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-174">For information about using the SQL Trace stored procedures to create a trace file workload, see [Create a Trace &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).</span></span>  
  
### <a name="trace-file-or-trace-table-workloads-that-contain-the-loginname-data-column"></a><span data-ttu-id="a92ea-175">包含 LoginName 資料行的追蹤檔案或追蹤資料表工作負載</span><span class="sxs-lookup"><span data-stu-id="a92ea-175">Trace File or Trace Table Workloads That Contain the LoginName Data Column</span></span>  
 <span data-ttu-id="a92ea-176">Database Engine Tuning Advisor 會在微調處理過程中送出「執行程序表」要求。</span><span class="sxs-lookup"><span data-stu-id="a92ea-176">Database Engine Tuning Advisor submits Showplan requests as part of the tuning process.</span></span> <span data-ttu-id="a92ea-177">將包含 **LoginName** 資料行的追蹤資料表或檔案當作工作負載來使用時，Database Engine Tuning Advisor 會模擬 **LoginName**中指定的使用者。</span><span class="sxs-lookup"><span data-stu-id="a92ea-177">When a trace table or file that contains the **LoginName** data column is consumed as a workload, Database Engine Tuning Advisor impersonates the user specified in **LoginName**.</span></span> <span data-ttu-id="a92ea-178">如果此使用者沒有 SHOWPLAN 權限，無法為追蹤所包含的陳述式執行和產生「執行程序表」，Database Engine Tuning Advisor 就不會微調這些陳述式。</span><span class="sxs-lookup"><span data-stu-id="a92ea-178">If this user has not been granted the SHOWPLAN permission, which enables the user to execute and produce Showplans for the statements contained in the trace, Database Engine Tuning Advisor will not tune those statements.</span></span>  
  
##### <a name="to-avoid-granting-the-showplan-permission-to-each-user-specified-in-the-loginname-column-of-the-trace"></a><span data-ttu-id="a92ea-179">若要避免將 SHOWPLAN 權限授與追蹤之 LoginName 資料行所指定的每個使用者</span><span class="sxs-lookup"><span data-stu-id="a92ea-179">To avoid granting the SHOWPLAN permission to each user specified in the LoginName column of the trace</span></span>  
  
1.  <span data-ttu-id="a92ea-180">微調追蹤檔案或資料表工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-180">Tune the trace file or table workload.</span></span> <span data-ttu-id="a92ea-181">如需詳細資訊，請參閱本主題稍後的＜ [微調資料庫](#Tune) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-181">For more information, see [Tune a Database](#Tune) later in this topic.</span></span>  
  
2.  <span data-ttu-id="a92ea-182">檢查微調記錄檔，找出因沒有適當權限而未微調的陳述式。</span><span class="sxs-lookup"><span data-stu-id="a92ea-182">Check the tuning log for statements that were not tuned due to inadequate permissions.</span></span> <span data-ttu-id="a92ea-183">如需詳細資訊，請參閱 [檢視及處理 Database Engine Tuning Advisor 的輸出](database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-183">For more information, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="a92ea-184">從未微調的事件刪除 **LoginName** 資料行來建立新工作負載，然後在新的追蹤檔案或資料表中僅儲存未微調的事件。</span><span class="sxs-lookup"><span data-stu-id="a92ea-184">Create a new workload by deleting the **LoginName** column from the events that were not tuned, and then save only the untuned events in a new trace file or table.</span></span> <span data-ttu-id="a92ea-185">如需從追蹤刪除資料行的詳細資訊，請參閱[指定追蹤檔案的事件及資料行 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) 或[修改現有的追蹤 &#40;Transact-SQL&#41;](../sql-trace/modify-an-existing-trace-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-185">For more information about deleting data columns from a trace, see [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) or [Modify an Existing Trace &#40;Transact-SQL&#41;](../sql-trace/modify-an-existing-trace-transact-sql.md).</span></span>  
  
4.  <span data-ttu-id="a92ea-186">將不含 **LoginName** 資料行的工作負載重新提交給 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="a92ea-186">Resubmit the new workload without the **LoginName** column to Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="a92ea-187">由於追蹤中沒有指定登入資訊，所以 Database Engine Tuning Advisor 將會微調新的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-187">Database Engine Tuning Advisor will tune the new workload because login information is not specified in the trace.</span></span> <span data-ttu-id="a92ea-188">如果陳述式中沒有 **LoginName** ，Database Engine Tuning Advisor 便會模擬啟動微調工作階段的使用者 ( **系統管理員** 固定伺服器角色或 **db_owner** 固定資料庫角色的成員)，來微調該陳述式。</span><span class="sxs-lookup"><span data-stu-id="a92ea-188">If the **LoginName** does not exist for a statement, Database Engine Tuning Advisor tunes that statement by impersonating the user who started the tuning session (a member of either the **sysadmin** fixed server role or the **db_owner** fixed database role).</span></span>  
  
##  <a name="tune-a-database"></a><a name="Tune"></a> <span data-ttu-id="a92ea-189">微調資料庫</span><span class="sxs-lookup"><span data-stu-id="a92ea-189">Tune a Database</span></span>  
 <span data-ttu-id="a92ea-190">若要微調資料庫，您可以使用 Database Engine Tuning Advisor GUI 或 **dta** 公用程式。</span><span class="sxs-lookup"><span data-stu-id="a92ea-190">To tune a database, you can use the Database Engine Tuning Advisor GUI or the **dta** utility.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a92ea-191">使用追蹤資料表作為 Database Engine Tuning Advisor 的工作負載之前，請確定追蹤已經停止。</span><span class="sxs-lookup"><span data-stu-id="a92ea-191">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="a92ea-192">Database Engine Tuning Advisor 不支援使用仍在寫入追蹤事件的追蹤資料表作為工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-192">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
### <a name="use-the-database-engine-tuning-advisor-graphical-user-interface"></a><span data-ttu-id="a92ea-193">使用 Database Engine Tuning Advisor 圖形化使用者介面</span><span class="sxs-lookup"><span data-stu-id="a92ea-193">Use the Database Engine Tuning Advisor Graphical User Interface</span></span>  
 <span data-ttu-id="a92ea-194">在 Database Engine Tuning Advisor GUI，您可以使用計畫快取、工作負載檔案或工作負載資料表來微調資料庫。</span><span class="sxs-lookup"><span data-stu-id="a92ea-194">On the Database Engine Tuning Advisor GUI, you can tune a database by using the plan cache, workload files, or workload tables.</span></span> <span data-ttu-id="a92ea-195">您可以使用 Database Engine Tuning Advisor GUI 輕鬆檢視目前微調工作階段的結果，以及上次微調工作階段的結果。</span><span class="sxs-lookup"><span data-stu-id="a92ea-195">You can use the Database Engine Tuning Advisor GUI to easily view the results of your current tuning session and results of previous tuning sessions.</span></span> <span data-ttu-id="a92ea-196">如需有關使用者介面選項的詳細資訊，請參閱本主題稍後的＜ [使用者介面描述](#UI) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-196">For information about user interface options, see [User Interface Descriptions](#UI) later in this topic.</span></span> <span data-ttu-id="a92ea-197">如需微調資料庫後處理輸出的詳細資訊，請參閱 [檢視及處理 Database Engine Tuning Advisor 的輸出](database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-197">For more information about working with the output after you tune a database, see [View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md).</span></span>  
  
####  <a name="to-tune-a-database-by-using-the-plan-cache"></a><a name="PlanCache"></a> <span data-ttu-id="a92ea-198">使用計畫快取微調資料庫</span><span class="sxs-lookup"><span data-stu-id="a92ea-198">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="a92ea-199">啟動 Database Engine Tuning Advisor，登入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a92ea-199">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a92ea-200">如需詳細資訊，請參閱本主題前面的＜ [啟動 Database Engine Tuning Advisor](#Start) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-200">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="a92ea-201">在 **[一般]** 索引標籤的 **[工作階段名稱]** 中輸入名稱，以建立新的微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="a92ea-201">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span> <span data-ttu-id="a92ea-202">啟動微調工作階段之前，您必須設定 **[一般]** 索引標籤中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a92ea-202">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="a92ea-203">啟動微調工作階段之前，不一定要修改 **[微調選項]** 索引標籤的設定。</span><span class="sxs-lookup"><span data-stu-id="a92ea-203">It is not necessary to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
3.  <span data-ttu-id="a92ea-204">選取 **[計畫快取]** 做為工作負載選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-204">Select **Plan Cache** as the workload option.</span></span> <span data-ttu-id="a92ea-205">Database Engine Tuning Advisor 會選取計畫快取中前 1,000 個用於分析的事件。</span><span class="sxs-lookup"><span data-stu-id="a92ea-205">Database Engine Tuning Advisor selects the top 1,000 events from the plan cache to use for analysis.</span></span>  
  
4.  <span data-ttu-id="a92ea-206">選取一個或多個想要微調的資料庫，並選擇性地從 **[選取的資料表]** 中選擇每個資料庫中的一個或多個資料表。</span><span class="sxs-lookup"><span data-stu-id="a92ea-206">Select the database or databases that you want to tune, and optionally from **Selected Tables**, choose one or more tables from each database.</span></span> <span data-ttu-id="a92ea-207">若要包含所有資料庫的快取項目，請按一下 **[微調選項]** 中的 **[進階選項]** ，然後核取 **[包含來自所有資料庫的計畫快取事件]** 。</span><span class="sxs-lookup"><span data-stu-id="a92ea-207">To include cache entries for all databases, from **Tuning Options**, click **Advanced Options** and then check **Include plan cache events from all databases**.</span></span>  
  
5.  <span data-ttu-id="a92ea-208">核取 **[儲存微調記錄]** ，以儲存微調記錄的副本。</span><span class="sxs-lookup"><span data-stu-id="a92ea-208">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="a92ea-209">若您不想儲存微調記錄的副本，請清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a92ea-209">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="a92ea-210">分析之後，若要檢視微調記錄，您可以開啟工作階段，並選取 **[進度]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a92ea-210">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
6.  <span data-ttu-id="a92ea-211">按一下 **[微調選項]** 索引標籤，並從所列出的選項中選取。</span><span class="sxs-lookup"><span data-stu-id="a92ea-211">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
7.  <span data-ttu-id="a92ea-212">按一下 **[開始分析]** 。</span><span class="sxs-lookup"><span data-stu-id="a92ea-212">Click **Start Analysis**.</span></span>  
  
     <span data-ttu-id="a92ea-213">如果您要在啟動之後停止微調，請選擇 **[動作]** 功能表上的下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="a92ea-213">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="a92ea-214">[停止分析 (附帶建議)] 會停止微調工作階段並提示您確定是否要 Database Engine Tuning Advisor 根據現階段完成的分析產生建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-214">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="a92ea-215">**[停止分析]** 會停止微調工作階段而不產生任何建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-215">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a92ea-216">不支援暫停 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="a92ea-216">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="a92ea-217">若在按下 [停止分析] 或 [停止分析 (附帶建議)] 工具列按鈕之後按下 [開始分析] 工具列按鈕，Database Engine Tuning Advisor 會啟動新的微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="a92ea-217">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
##### <a name="to-tune-a-database-using-a-workload-file-or-table-as-input"></a><span data-ttu-id="a92ea-218">若要使用工作負載檔案或資料表做為輸入以微調資料庫</span><span class="sxs-lookup"><span data-stu-id="a92ea-218">To tune a database using a workload file or table as input</span></span>  
  
1.  <span data-ttu-id="a92ea-219">決定您希望 Database Engine Tuning Advisor 在分析過程中考慮加入、移除或保留的資料庫功能 (索引、索引檢視、分割)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-219">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="a92ea-220">建立工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-220">Create a workload.</span></span> <span data-ttu-id="a92ea-221">如需詳細資訊，請參閱本主題前面的＜ [建立工作負載](#Create) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-221">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="a92ea-222">啟動 Database Engine Tuning Advisor，並登入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a92ea-222">Launch Database Engine Tuning Advisor, and log into an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a92ea-223">如需詳細資訊，請參閱本主題前面的＜ [啟動 Database Engine Tuning Advisor](#Start) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-223">For more information, see [Start the Database Engine Tuning Advisor](#Start) earlier in this topic.</span></span>  
  
4.  <span data-ttu-id="a92ea-224">在 **[一般]** 索引標籤的 **[工作階段名稱]** 中輸入名稱，以建立新的微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="a92ea-224">On the **General** tab, type a name in **Session name** to create a new tuning session.</span></span>  
  
5.  <span data-ttu-id="a92ea-225">選擇 **[工作負載檔案]** 或 **[資料表]** 並輸入檔案的路徑，或在相鄰的文字方塊中輸入資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="a92ea-225">Choose either a **Workload File** or **Table** and type either the path to the file, or the name of the table in the adjacent text box.</span></span>  
  
     <span data-ttu-id="a92ea-226">指定資料表時的格式為</span><span class="sxs-lookup"><span data-stu-id="a92ea-226">The format for specifying a table is</span></span>  
  
    ```  
  
    database_name.schema_name.table_name  
    ```  
  
     <span data-ttu-id="a92ea-227">若要搜尋工作負載檔案或資料表，請按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="a92ea-227">To search for a workload file or table, click **Browse**.</span></span> <span data-ttu-id="a92ea-228">Database Engine Tuning Advisor 會假設工作負載檔案是換用檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-228">Database Engine Tuning Advisor assumes that workload files are rollover files.</span></span> <span data-ttu-id="a92ea-229">如需有關換用檔案的詳細資訊，請參閱＜ [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-229">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
     <span data-ttu-id="a92ea-230">使用追蹤資料表做為工作負載時，該資料表必須位於 Database Engine Tuning Advisor 所微調的同一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a92ea-230">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="a92ea-231">若您在不同的伺服器上建立追蹤資料表，請先將它移到 Database Engine Tuning Advisor 所微調的伺服器上，再用它來作為您的工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-231">If you create the trace table on a different server, move it to the server that Database Engine Tuning Advisor is tuning before using it as your workload.</span></span>  
  
6.  <span data-ttu-id="a92ea-232">選取您在步驟 5 中選取要執行工作負載的資料庫與資料表。</span><span class="sxs-lookup"><span data-stu-id="a92ea-232">Select the databases and tables against which you wish to run the workload that you selected in step 5.</span></span> <span data-ttu-id="a92ea-233">若要選取資料表，請按一下 **[選取的資料表]** 箭頭。</span><span class="sxs-lookup"><span data-stu-id="a92ea-233">To select the tables, click the **Selected Tables** arrow.</span></span>  
  
7.  <span data-ttu-id="a92ea-234">核取 **[儲存微調記錄]** ，以儲存微調記錄的副本。</span><span class="sxs-lookup"><span data-stu-id="a92ea-234">Check **Save tuning log** to save a copy of the tuning log.</span></span> <span data-ttu-id="a92ea-235">若您不想儲存微調記錄的副本，請清除核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a92ea-235">Clear the check box if you do not want to save a copy of the tuning log.</span></span>  
  
     <span data-ttu-id="a92ea-236">分析之後，若要檢視微調記錄，您可以開啟工作階段，並選取 **[進度]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a92ea-236">You can view the tuning log after analysis by opening the session and selecting the **Progress** tab.</span></span>  
  
8.  <span data-ttu-id="a92ea-237">按一下 **[微調選項]** 索引標籤，並從所列出的選項中選取。</span><span class="sxs-lookup"><span data-stu-id="a92ea-237">Click the **Tuning Options** tab and select from the options listed there.</span></span>  
  
9. <span data-ttu-id="a92ea-238">按一下工具列中的 **[開始分析]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a92ea-238">Click the **Start Analysis** button in the toolbar.</span></span>  
  
     <span data-ttu-id="a92ea-239">如果您要在啟動之後停止微調，請選擇 **[動作]** 功能表上的下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="a92ea-239">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
    -   <span data-ttu-id="a92ea-240">[停止分析 (附帶建議)] 會停止微調工作階段並提示您確定是否要 Database Engine Tuning Advisor 根據現階段完成的分析產生建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-240">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
    -   <span data-ttu-id="a92ea-241">**[停止分析]** 會停止微調工作階段而不產生任何建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-241">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a92ea-242">不支援暫停 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="a92ea-242">Pausing Database Engine Tuning Advisor is not supported.</span></span> <span data-ttu-id="a92ea-243">若在按下 [停止分析] 或 [停止分析 (附帶建議)] 工具列按鈕之後按下 [開始分析] 工具列按鈕，Database Engine Tuning Advisor 會啟動新的微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="a92ea-243">If you click the **Start Analysis** toolbar button after clicking either the **Stop Analysis** or **Stop Analysis (With Recommendations)** toolbar buttons, Database Engine Tuning Advisor starts a new tuning session.</span></span>  
  
###  <a name="use-the-dta-utility"></a><a name="dta"></a> <span data-ttu-id="a92ea-244">使用 dta 公用程式</span><span class="sxs-lookup"><span data-stu-id="a92ea-244">Use the dta Utility</span></span>  
 <span data-ttu-id="a92ea-245">[dta 公用程式](../../tools/dta/dta-utility.md) 提供一個命令提示字元可執行檔，您可用來微調資料庫。</span><span class="sxs-lookup"><span data-stu-id="a92ea-245">The [dta utility](../../tools/dta/dta-utility.md) provides a command prompt executable file that you can use to tune databases.</span></span> <span data-ttu-id="a92ea-246">這個公用程式可讓您在批次檔和指令碼中使用 Database Engine Tuning Advisor 的功能。</span><span class="sxs-lookup"><span data-stu-id="a92ea-246">It enables you to use Database Engine Tuning Advisor functionality in batch files and scripts.</span></span> <span data-ttu-id="a92ea-247">您的 **dta** 公用程式會將計畫快取項目、追蹤檔案、追蹤資料表和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼視為工作負載；</span><span class="sxs-lookup"><span data-stu-id="a92ea-247">The **dta** utility takes plan cache entries, trace files, trace tables, and [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts as workloads.</span></span> <span data-ttu-id="a92ea-248">它也會使用符合 Database Engine Tuning Advisor XML 結構描述的 XML 輸入，此結構描述可從此 [Microsoft 網站](https://go.microsoft.com/fwlink/?linkid=43100)取得。</span><span class="sxs-lookup"><span data-stu-id="a92ea-248">It also takes XML input that conforms to the Database Engine Tuning Advisor XML schema, which is available at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100).</span></span>  
  
 <span data-ttu-id="a92ea-249">開始使用 **dta** 公用程式微調工作負載之前，請先考慮下列事項：</span><span class="sxs-lookup"><span data-stu-id="a92ea-249">Consider the following before you begin tuning a workload with the **dta** utility:</span></span>  
  
-   <span data-ttu-id="a92ea-250">使用追蹤資料表做為工作負載時，該資料表必須位於 Database Engine Tuning Advisor 所微調的同一部伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a92ea-250">When using a trace table as a workload, that table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="a92ea-251">如果追蹤資料表是在不同的伺服器上建立的，請將其移動至 Database Engine Tuning Advisor 正在進行微調的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a92ea-251">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
-   <span data-ttu-id="a92ea-252">使用追蹤資料表作為 Database Engine Tuning Advisor 的工作負載之前，請確定追蹤已經停止。</span><span class="sxs-lookup"><span data-stu-id="a92ea-252">Make sure that tracing has stopped before using a trace table as a workload for Database Engine Tuning Advisor.</span></span> <span data-ttu-id="a92ea-253">Database Engine Tuning Advisor 不支援使用仍在寫入追蹤事件的追蹤資料表作為工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-253">Database Engine Tuning Advisor does not support using a trace table to which trace events are still being written as a workload.</span></span>  
  
-   <span data-ttu-id="a92ea-254">如果微調工作階段繼續執行的時間超過您所預期的執行時間，可以按 CTRL+C 停止微調工作階段，並根據現階段完成的分析 **dta** 產生建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-254">If a tuning session continues running longer than you had anticipated it would run, you can press CTRL+C to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="a92ea-255">系統會提示您決定是否要產生建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-255">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="a92ea-256">請再按一下 CTRL+C 來停止微調工作階段，不產生建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-256">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
 <span data-ttu-id="a92ea-257">如需有關 **dta** 公用程式語法和範例的詳細資訊，請參閱＜ [dta Utility](../../tools/dta/dta-utility.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-257">For more information about **dta** utility syntax and examples, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##### <a name="to-tune-a-database-by-using-the-plan-cache"></a><span data-ttu-id="a92ea-258">使用計畫快取微調資料庫</span><span class="sxs-lookup"><span data-stu-id="a92ea-258">To tune a database by using the plan cache</span></span>  
  
1.  <span data-ttu-id="a92ea-259">指定 **-ip** 選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-259">Specify the **-ip** option.</span></span> <span data-ttu-id="a92ea-260">針對所選取資料庫排名前 1,000 個計畫快取事件進行分析。</span><span class="sxs-lookup"><span data-stu-id="a92ea-260">The top 1,000 plan cache events for the selected databases are analyzed.</span></span>  
  
     <span data-ttu-id="a92ea-261">從命令提示字元，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="a92ea-261">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -s SessionName  
    ```  
  
2.  <span data-ttu-id="a92ea-262">若要修改用於分析的事件數，請指定 **-n** 選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-262">To modify the number of events to use for analysis, specify the **-n** option.</span></span> <span data-ttu-id="a92ea-263">下列範例將快取項目數增加為 2,000。</span><span class="sxs-lookup"><span data-stu-id="a92ea-263">The following example increases the number of cache entries to 2,000.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -n 2000-s SessionName1  
    ```  
  
3.  <span data-ttu-id="a92ea-264">若要分析執行個體中所有資料庫的事件，請指定 **-ipf** 選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-264">To analyze events for all databases in the instance, specify the **-ipf** option.</span></span>  
  
    ```  
    dta -E -D DatabaseName -ip -ipf -n 2000 -s SessionName2  
    ```  
  
##### <a name="to-tune-a-database-by-using-a-workload-and-dta-utility-default-settings"></a><span data-ttu-id="a92ea-265">使用工作負載和 dta 公用程式預設值來微調資料庫</span><span class="sxs-lookup"><span data-stu-id="a92ea-265">To tune a database by using a workload and dta utility default settings</span></span>  
  
1.  <span data-ttu-id="a92ea-266">決定您希望 Database Engine Tuning Advisor 在分析過程中考慮加入、移除或保留的資料庫功能 (索引、索引檢視、分割)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-266">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="a92ea-267">建立工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-267">Create a workload.</span></span> <span data-ttu-id="a92ea-268">如需詳細資訊，請參閱本主題前面的＜ [建立工作負載](#Create) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-268">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="a92ea-269">從命令提示字元，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="a92ea-269">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -D DatabaseName -if WorkloadFile -s SessionName  
    ```  
  
     <span data-ttu-id="a92ea-270">其中 `-E` 指定您的微調工作階段使用信任連接 (而非登入識別碼和密碼)，而 `-D` 指定您要微調的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="a92ea-270">where `-E` specifies that your tuning session uses a trusted connection (instead of a login ID and password), `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="a92ea-271">依預設，公用程式會連接到本機電腦上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預設執行個體</span><span class="sxs-lookup"><span data-stu-id="a92ea-271">By default, the utility connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="a92ea-272">(使用 `-S` 選項指定遠端資料庫，如下列程序所示，或指定具名執行個體)。 `-if` 選項指定工作負載檔案 (可以是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼或追蹤檔) 的名稱和路徑，而 `-s` 指定微調工作階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="a92ea-272">(Use the `-S` option to specify a remote database as shown in the following procedure, or to specify a named instance.) The `-if` option specifies the name and path to a workload file (which can be a [!INCLUDE[tsql](../../includes/tsql-md.md)] script or a trace file), and `-s` specifies a name for your tuning session.</span></span>  
  
     <span data-ttu-id="a92ea-273">這裡顯示的四個選項 (資料庫名稱、工作負載、連接類型和工作階段名稱) 都是強制選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-273">The four options shown here (database name, workload, connection type, and session name) are mandatory.</span></span>  
  
##### <a name="to-tune-a-remote-database-or-a-named-instance-for-a-specific-duration"></a><span data-ttu-id="a92ea-274">若要在特定持續期間內微調遠端資料庫或具名執行個體</span><span class="sxs-lookup"><span data-stu-id="a92ea-274">To tune a remote database or a named instance for a specific duration</span></span>  
  
1.  <span data-ttu-id="a92ea-275">決定您希望 Database Engine Tuning Advisor 在分析過程中考慮加入、移除或保留的資料庫功能 (索引、索引檢視、分割)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-275">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="a92ea-276">建立工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-276">Create a workload.</span></span> <span data-ttu-id="a92ea-277">如需詳細資訊，請參閱本主題前面的＜ [建立工作負載](#Create) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-277">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="a92ea-278">從命令提示字元，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="a92ea-278">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -S ServerName\Instance -D DatabaseName -it WorkloadTableName   
    -U LoginID -P Password -s SessionName -A TuningTimeInMinutes  
    ```  
  
     <span data-ttu-id="a92ea-279">其中 `-S` 指定遠端伺服器名稱和執行個體 (或本機伺服器上的具名執行個體)，而 `-D` 指定您要微調的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="a92ea-279">where `-S` specifies a remote server name and instance (or a named instance on the local server) and `-D` specifies the name of the database you want to tune.</span></span> <span data-ttu-id="a92ea-280">`-it` 選項指定工作負載資料表的名稱、 `-U` 和 `-P` 指定遠端資料庫的登入識別碼和密碼、 `-s` 指定微調工作階段名稱，而 `-A` 指定微調工作階段持續期間 (以分鐘為單位)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-280">The `-it` option specifies the name of the workload table, `-U` and `-P` specify the login ID and password to the remote database, `-s` specifies the tuning session name, and `-A` specifies the tuning session duration in minutes.</span></span> <span data-ttu-id="a92ea-281">依預設， **dta** 公用程式會使用 8 小時的微調持續時間。</span><span class="sxs-lookup"><span data-stu-id="a92ea-281">By default, the **dta** utility uses an 8-hour tuning duration.</span></span> <span data-ttu-id="a92ea-282">如果您要讓 Database Engine Tuning Advisor 在不限制時間長度的情況下微調工作負載，請指定 **0** (零) 與 `-A` 選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-282">If you would like Database Engine Tuning Advisor to tune a workload for an unlimited amount of time, specify **0** (zero) with the `-A` option.</span></span>  
  
##### <a name="to-tune-a-database-using-an-xml-input-file"></a><span data-ttu-id="a92ea-283">若要使用 XML 輸入檔微調資料庫</span><span class="sxs-lookup"><span data-stu-id="a92ea-283">To tune a database using an XML input file</span></span>  
  
1.  <span data-ttu-id="a92ea-284">決定您希望 Database Engine Tuning Advisor 在分析過程中考慮加入、移除或保留的資料庫功能 (索引、索引檢視、分割)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-284">Determine the database features (indexes, indexed views, partitioning) you want Database Engine Tuning Advisor to consider adding, removing, or retaining during analysis.</span></span>  
  
2.  <span data-ttu-id="a92ea-285">建立工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-285">Create a workload.</span></span> <span data-ttu-id="a92ea-286">如需詳細資訊，請參閱本主題前面的＜ [建立工作負載](#Create) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-286">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
3.  <span data-ttu-id="a92ea-287">建立 XML 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="a92ea-287">Create an XML input file.</span></span> <span data-ttu-id="a92ea-288">如需詳細資訊，請參閱本主題稍後的＜ [建立 XML 輸入檔](#XMLInput) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-288">For more information, see [Create XML Input Files](#XMLInput) later in this topic.</span></span>  
  
4.  <span data-ttu-id="a92ea-289">從命令提示字元，輸入下列內容：</span><span class="sxs-lookup"><span data-stu-id="a92ea-289">From a command prompt, enter the following:</span></span>  
  
    ```  
    dta -E -S ServerName\Instance -s SessionName -ix PathToXMLInputFile  
    ```  
  
     <span data-ttu-id="a92ea-290">其中 `-E` 指定信任連接、 `-S` 指定遠端伺服器和執行個體，或者本機伺服器上的具名執行特體、 `-s` 指定微調工作階段名稱，而 `-ix` 指定要用於微調工作階段的 XML 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="a92ea-290">where `-E` specifies a trusted connection, `-S` specifies a remote server and instance, or a named instance on the local server, `-s` specifies a tuning session name, and `-ix` specifies the XML input file to use for the tuning session.</span></span>  
  
5.  <span data-ttu-id="a92ea-291">公用程式完成微調工作負載之後，您可以透過 Database Engine Tuning Advisor GUI 來檢視微調工作階段的結果。</span><span class="sxs-lookup"><span data-stu-id="a92ea-291">After the utility finishes tuning the workload, you can view the results of tuning sessions with the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="a92ea-292">或者，您也可以透過 **-ox** 選項，指定將微調建議寫入 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-292">As an alternative, you can also specify that the tuning recommendations be written to an XML file with the **-ox** option.</span></span> <span data-ttu-id="a92ea-293">如需詳細資訊，請參閱 [dta Utility](../../tools/dta/dta-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-293">For more information, see [dta Utility](../../tools/dta/dta-utility.md).</span></span>  
  
##  <a name="create-an-xml-input-file"></a><a name="XMLInput"></a> <span data-ttu-id="a92ea-294">建立 XML 輸入檔</span><span class="sxs-lookup"><span data-stu-id="a92ea-294">Create an XML Input File</span></span>  
 <span data-ttu-id="a92ea-295">如果您是有經驗的 XML 開發人員，即可建立 XML 格式的檔案供 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 用以微調工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-295">If you are an experienced XML developer, you can create XML-formatted files that [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor can use to tune workloads.</span></span> <span data-ttu-id="a92ea-296">若要建立這些 XML 檔案，請使用您喜好的 XML 工具來編輯範例檔，或是根據 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML 結構描述產生執行個體。</span><span class="sxs-lookup"><span data-stu-id="a92ea-296">To create these XML files, use your favorite XML tools to edit a sample file or to generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
 <span data-ttu-id="a92ea-297">您的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中提供 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML 結構描述，其位置如下：</span><span class="sxs-lookup"><span data-stu-id="a92ea-297">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is available in your [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation in the following location:</span></span>  
  
 <span data-ttu-id="a92ea-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span><span class="sxs-lookup"><span data-stu-id="a92ea-298">C:\Program Files\Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\dta\dtaschema.xsd</span></span>  
  
 <span data-ttu-id="a92ea-299">您也可以從這個 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Microsoft 網站 [，線上取得](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)Tuning Advisor XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="a92ea-299">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema is also available online at this [Microsoft Web site](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409).</span></span>  
  
 <span data-ttu-id="a92ea-300">此 URL 可將您帶往具有許多 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML 結構描述的網頁。</span><span class="sxs-lookup"><span data-stu-id="a92ea-300">This URL takes you to a page where many [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML schemas are available.</span></span> <span data-ttu-id="a92ea-301">將網頁向下捲動，直到您找到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 的資料列。</span><span class="sxs-lookup"><span data-stu-id="a92ea-301">Scroll down the page until you reach the row for [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor.</span></span>  
  
#### <a name="to-create-an-xml-input-file-to-tune-workloads"></a><span data-ttu-id="a92ea-302">若要建立 XML 輸入檔來微調工作負載</span><span class="sxs-lookup"><span data-stu-id="a92ea-302">To create an XML input file to tune workloads</span></span>  
  
1.  <span data-ttu-id="a92ea-303">建立工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-303">Create a workload.</span></span> <span data-ttu-id="a92ea-304">您可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中的微調範本來使用追蹤檔案或資料表，或是建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼來重新產生 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的代表性工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-304">You can use a trace file or table by using the tuning template in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], or create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script that reproduces a representative workload for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a92ea-305">如需詳細資訊，請參閱本主題前面的＜ [建立工作負載](#Create) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-305">For more information, see [Create a Workload](#Create) earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="a92ea-306">使用下列其中一種方法來建立 XML 輸入檔：</span><span class="sxs-lookup"><span data-stu-id="a92ea-306">Create an XML input file by one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a92ea-307">將其中一個 [XML 輸入檔範例 &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md)複製並貼到您喜好的 XML 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="a92ea-307">Copy and paste one of the [XML Input File Samples &#40;DTA&#41;](../../tools/dta/xml-input-file-samples-dta.md) into your favorite XML editor.</span></span> <span data-ttu-id="a92ea-308">變更當中的值，指定適合您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝的引數，然後儲存該 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-308">Change the values to specify the appropriate arguments for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, and save the XML file.</span></span>  
  
    -   <span data-ttu-id="a92ea-309">使用您慣用的 XML 工具，根據 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 結構描述產生執行個體。</span><span class="sxs-lookup"><span data-stu-id="a92ea-309">Using your favorite XML tool, generate an instance from the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor XML schema.</span></span>  
  
3.  <span data-ttu-id="a92ea-310">建立 XML 輸入檔之後，將其用為 **dta** 命令列公用程式的輸入值，以微調工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-310">After creating the XML input file, use it as input to the **dta** command-line utility to tune the workload.</span></span> <span data-ttu-id="a92ea-311">如需有關 XML 輸入檔與此公用程式一起使用的詳細資訊，請參閱本主題前面的＜ [使用 dta 公用程式](#dta) ＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-311">For information about using XML input files with this utility, see the section [Use the dta Utililty](#dta) earlier in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a92ea-312">若您想要使用內嵌工作負載 (此為在 XML 輸入檔中直接指定的工作負載)，請使用範例：[含內嵌工作負載的 XML 輸入檔範例 &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="a92ea-312">If you want to use an inline workload, which is a workload that is specified directly in the XML input file, use the sample [XML Input File Sample with Inline Workload &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
##  <a name="user-interface-descriptions"></a><a name="UI"></a> <span data-ttu-id="a92ea-313">使用者介面描述</span><span class="sxs-lookup"><span data-stu-id="a92ea-313">User Interface Descriptions</span></span>  
  
### <a name="tools-menuoptions-page"></a><span data-ttu-id="a92ea-314">工具功能表/選項頁面</span><span class="sxs-lookup"><span data-stu-id="a92ea-314">Tools Menu/Options Page</span></span>  
 <span data-ttu-id="a92ea-315">使用此對話方塊，來指定 Database Engine Tuning Advisor 的一般組態參數。</span><span class="sxs-lookup"><span data-stu-id="a92ea-315">Use this dialog box to specify general configuration parameters for the Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="a92ea-316">**啟動時**</span><span class="sxs-lookup"><span data-stu-id="a92ea-316">**On startup**</span></span>  
 <span data-ttu-id="a92ea-317">指定 Database Engine Tuning Advisor 在啟動時應執行的工作：開啟但沒有資料庫連接、顯示 [新增連接] 對話方塊、顯示新的工作階段，或者載入上次載入的工作階段。</span><span class="sxs-lookup"><span data-stu-id="a92ea-317">Specify what Database Engine Tuning Advisor should do when it is started: open without a database connection, show a **New Connection** dialog box, show a new session, or load the last loaded session.</span></span>  
  
 <span data-ttu-id="a92ea-318">**變更字型**</span><span class="sxs-lookup"><span data-stu-id="a92ea-318">**Change font**</span></span>  
 <span data-ttu-id="a92ea-319">指定 Database Engine Tuning Advisor 資料表所用的字型。</span><span class="sxs-lookup"><span data-stu-id="a92ea-319">Specify the display font used by Database Engine Tuning Advisor tables.</span></span>  
  
 <span data-ttu-id="a92ea-320">**最近使用清單中的項目數目**</span><span class="sxs-lookup"><span data-stu-id="a92ea-320">**Number of items in most recently used lists**</span></span>  
 <span data-ttu-id="a92ea-321">指定在 [檔案] 功能表中的 [最近使用的工作階段] 或 [最近使用的檔案] 之下，要顯示之工作階段或檔案的數目。</span><span class="sxs-lookup"><span data-stu-id="a92ea-321">Specify the number of sessions or files to display under **Recent Sessions** or **Recent Files** in the **File** menu.</span></span>  
  
 <span data-ttu-id="a92ea-322">**記住上次的微調選項**</span><span class="sxs-lookup"><span data-stu-id="a92ea-322">**Remember my last tuning options**</span></span>  
 <span data-ttu-id="a92ea-323">在工作階段之間保留微調選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-323">Retain tuning options between sessions.</span></span> <span data-ttu-id="a92ea-324">依預設為已選取。</span><span class="sxs-lookup"><span data-stu-id="a92ea-324">Selected by default.</span></span> <span data-ttu-id="a92ea-325">清除此核取方塊，即可永遠使用 Database Engine Tuning Advisor 的預設值來啟動。</span><span class="sxs-lookup"><span data-stu-id="a92ea-325">Clear this check box to always start with the Database Engine Tuning Advisor defaults.</span></span>  
  
 <span data-ttu-id="a92ea-326">**永久刪除工作階段之前先詢問**</span><span class="sxs-lookup"><span data-stu-id="a92ea-326">**Ask before permanently deleting sessions**</span></span>  
 <span data-ttu-id="a92ea-327">在刪除工作階段之前先顯示確認對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a92ea-327">Display a confirmation dialog box before deleting sessions.</span></span>  
  
 <span data-ttu-id="a92ea-328">**停止工作階段分析之前先詢問**</span><span class="sxs-lookup"><span data-stu-id="a92ea-328">**Ask before stopping session analysis**</span></span>  
 <span data-ttu-id="a92ea-329">在停止分析工作負載前，先顯示確認對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a92ea-329">Display a confirmation dialog box before stopping analysis of a workload.</span></span>  
  
#### <a name="general-tab-options"></a><span data-ttu-id="a92ea-330">一般索引標籤選項</span><span class="sxs-lookup"><span data-stu-id="a92ea-330">General Tab Options</span></span>  
 <span data-ttu-id="a92ea-331">啟動微調工作階段之前，您必須設定 **[一般]** 索引標籤中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a92ea-331">You must configure the fields in the **General** tab before starting a tuning session.</span></span> <span data-ttu-id="a92ea-332">啟動微調工作階段之前，不需要修改 **[微調選項]** 索引標籤的設定。</span><span class="sxs-lookup"><span data-stu-id="a92ea-332">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="a92ea-333">**[工作階段名稱]**</span><span class="sxs-lookup"><span data-stu-id="a92ea-333">**Session name**</span></span>  
 <span data-ttu-id="a92ea-334">指定工作階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="a92ea-334">Specify a name for the session.</span></span> <span data-ttu-id="a92ea-335">工作階段名稱與微調工作階段的名稱相關聯。</span><span class="sxs-lookup"><span data-stu-id="a92ea-335">The session name associates a name with a tuning session.</span></span> <span data-ttu-id="a92ea-336">您可以參考此名稱，以便稍後檢閱微調工作階段。</span><span class="sxs-lookup"><span data-stu-id="a92ea-336">You can refer to this name to review the tuning session later.</span></span>  
  
 <span data-ttu-id="a92ea-337">**檔案**</span><span class="sxs-lookup"><span data-stu-id="a92ea-337">**File**</span></span>  
 <span data-ttu-id="a92ea-338">指定工作負載的 .sql 指令碼或追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-338">Specify a .sql script or trace file for a workload.</span></span> <span data-ttu-id="a92ea-339">在相關聯的文字方塊中，指定路徑和檔名。</span><span class="sxs-lookup"><span data-stu-id="a92ea-339">Specify the path and filename in the associated text box.</span></span> <span data-ttu-id="a92ea-340">Database Engine Tuning Advisor 會假設工作負載追蹤檔案為換用檔案。</span><span class="sxs-lookup"><span data-stu-id="a92ea-340">Database Engine Tuning Advisor assumes that the workload trace file is a rollover file.</span></span> <span data-ttu-id="a92ea-341">如需有關換用檔案的詳細資訊，請參閱＜ [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a92ea-341">For more information about rollover files, see [Limit Trace File and Table Sizes](../sql-trace/limit-trace-file-and-table-sizes.md).</span></span>  
  
 <span data-ttu-id="a92ea-342">**Table**</span><span class="sxs-lookup"><span data-stu-id="a92ea-342">**Table**</span></span>  
 <span data-ttu-id="a92ea-343">指定工作負載的追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="a92ea-343">Specify a trace table for a workload.</span></span> <span data-ttu-id="a92ea-344">指定相關聯的文字方塊中之追蹤資料表的完整限定名稱如下：</span><span class="sxs-lookup"><span data-stu-id="a92ea-344">Specify the fully qualified name of the trace table in the associated text box as follows:</span></span>  
  
```  
database_name.owner_name.table_name  
```  
  
-   <span data-ttu-id="a92ea-345">將追蹤資料表作為工作負載使用之前，請確定已停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="a92ea-345">Make sure that tracing has stopped before using a trace table as a workload.</span></span>  
  
-   <span data-ttu-id="a92ea-346">追蹤資料表所在的伺服器必須和 Database Engine Tuning Advisor 正在進行微調的伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="a92ea-346">The trace table must exist on the same server that Database Engine Tuning Advisor is tuning.</span></span> <span data-ttu-id="a92ea-347">如果追蹤資料表是在不同的伺服器上建立的，請將其移動至 Database Engine Tuning Advisor 正在進行微調的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a92ea-347">If you create the trace table on a different server, then move it to the server that Database Engine Tuning Advisor is tuning.</span></span>  
  
 <span data-ttu-id="a92ea-348">**[計畫快取]**</span><span class="sxs-lookup"><span data-stu-id="a92ea-348">**Plan Cache**</span></span>  
 <span data-ttu-id="a92ea-349">指定計畫快取做為工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-349">Specify the plan cache as a workload.</span></span> <span data-ttu-id="a92ea-350">利用此操作，您可以不必手動建立工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-350">By doing this, you can avoid having to manually create a workload.</span></span> <span data-ttu-id="a92ea-351">Database Engine Tuning Advisor 會選取前 1,000 個用於分析的事件。</span><span class="sxs-lookup"><span data-stu-id="a92ea-351">Database Engine Tuning Advisor selects the top 1,000 events to use for analysis.</span></span>  
  
 <span data-ttu-id="a92ea-352">**XML**</span><span class="sxs-lookup"><span data-stu-id="a92ea-352">**Xml**</span></span>  
 <span data-ttu-id="a92ea-353">除非您從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]匯入工作負載查詢，否則不會出現。</span><span class="sxs-lookup"><span data-stu-id="a92ea-353">This does not appear unless you import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a92ea-354">若要從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]匯入工作負載：</span><span class="sxs-lookup"><span data-stu-id="a92ea-354">To import a workload query from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:</span></span>  
  
1.  <span data-ttu-id="a92ea-355">在查詢編輯器鍵入查詢，並反白顯示。</span><span class="sxs-lookup"><span data-stu-id="a92ea-355">Type a query into Query Editor and highlight it.</span></span>  
  
2.  <span data-ttu-id="a92ea-356">以滑鼠右鍵按一下反白顯示的查詢，並按一下 [在 Database Engine Tuning Advisor 中分析查詢]。</span><span class="sxs-lookup"><span data-stu-id="a92ea-356">Right-click the highlighted query and click **Analyze Query in Database Engine Tuning Advisor**.</span></span>  
  
 <span data-ttu-id="a92ea-357">**瀏覽工作負載 [檔案或資料表]**</span><span class="sxs-lookup"><span data-stu-id="a92ea-357">**Browse for a workload [file or table]**</span></span>  
 <span data-ttu-id="a92ea-358">選取 [檔案] 或 [資料表] 作為工作負載來源時，請使用此瀏覽按鈕來選取目標。</span><span class="sxs-lookup"><span data-stu-id="a92ea-358">When **File** or **Table** is selected as the workload source, use this browse button to select the target.</span></span>  
  
 <span data-ttu-id="a92ea-359">**預覽 XML 工作負載**</span><span class="sxs-lookup"><span data-stu-id="a92ea-359">**Preview the XML workload**</span></span>  
 <span data-ttu-id="a92ea-360">檢視已從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]匯入的 XML 格式工作負載。</span><span class="sxs-lookup"><span data-stu-id="a92ea-360">View an XML-formatted workload that has been imported from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a92ea-361">**工作負載分析的資料庫**</span><span class="sxs-lookup"><span data-stu-id="a92ea-361">**Database for workload analysis**</span></span>  
 <span data-ttu-id="a92ea-362">指定 Database Engine Tuning Advisor 微調工作負載時，第一個連接的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a92ea-362">Specify the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="a92ea-363">在微調開始之後，Database Engine Tuning Advisor 會連接到工作負載包含的 `USE DATABASE` 陳述式所指定的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a92ea-363">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
 <span data-ttu-id="a92ea-364">**選取要微調的資料庫與資料表**</span><span class="sxs-lookup"><span data-stu-id="a92ea-364">**Select databases and tables to tune**</span></span>  
 <span data-ttu-id="a92ea-365">指定要微調的資料庫與資料表。</span><span class="sxs-lookup"><span data-stu-id="a92ea-365">Specify the databases and tables to be tuned.</span></span> <span data-ttu-id="a92ea-366">若要指定所有資料庫，請選取 **[名稱]** 資料行標題中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a92ea-366">To specify all of the databases, select the check box in the **Name** column heading.</span></span> <span data-ttu-id="a92ea-367">若要指定某些資料庫，請選取資料庫名稱旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a92ea-367">To specify certain databases, select the check box next to the database name.</span></span> <span data-ttu-id="a92ea-368">依預設，所有選取之資料庫的資料表會自動包含在微調工作階段中。</span><span class="sxs-lookup"><span data-stu-id="a92ea-368">By default, all of the tables for selected databases are automatically included in the tuning session.</span></span> <span data-ttu-id="a92ea-369">若要排除資料表，請按一下 **[選取的資料表]** 資料行中的箭頭，然後將您不要微調之資料表旁的核取方塊清除。</span><span class="sxs-lookup"><span data-stu-id="a92ea-369">To exclude tables, click the arrow in the **Selected Tables** column, and then clear the check boxes next to the tables that you do not want to tune.</span></span>  
  
 <span data-ttu-id="a92ea-370">[選取的資料表] 向下箭頭</span><span class="sxs-lookup"><span data-stu-id="a92ea-370">**Selected Tables** down arrow</span></span>  
 <span data-ttu-id="a92ea-371">展開資料表清單，以允許選取個別資料表進行微調。</span><span class="sxs-lookup"><span data-stu-id="a92ea-371">Expand the tables list to allow selecting individual tables for tuning.</span></span>  
  
 <span data-ttu-id="a92ea-372">**[儲存微調記錄]**</span><span class="sxs-lookup"><span data-stu-id="a92ea-372">**Save tuning log**</span></span>  
 <span data-ttu-id="a92ea-373">在工作階段中建立記錄檔並記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="a92ea-373">Create a log and record errors during the session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a92ea-374">Database Engine Tuning Advisor 不會自動為 **[一般]** 索引標籤上顯示的資料表，更新資料列資訊。而是依賴資料庫中的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a92ea-374">Database Engine Tuning Advisor does not automatically update the rows information for the tables displayed on the **General** tab. Instead it relies upon the metadata in the database.</span></span> <span data-ttu-id="a92ea-375">如果您質疑資料列資訊已過期，請為相關物件執行 DBCC UPDATEUSAGE 命令。</span><span class="sxs-lookup"><span data-stu-id="a92ea-375">If you suspect that the rows information is outdated, run the DBCC UPDATEUSAGE command for the relevant objects.</span></span>  
  
##### <a name="tuning-tab-options"></a><span data-ttu-id="a92ea-376">微調選項索引標籤</span><span class="sxs-lookup"><span data-stu-id="a92ea-376">Tuning Tab Options</span></span>  
 <span data-ttu-id="a92ea-377">使用 **[微調選項]** 索引標籤來修改一般微調選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="a92ea-377">Use the **Tuning Options** tab to modify default settings of general tuning options.</span></span> <span data-ttu-id="a92ea-378">啟動微調工作階段之前，不需要修改 **[微調選項]** 索引標籤的設定。</span><span class="sxs-lookup"><span data-stu-id="a92ea-378">You do not have to modify the settings of the **Tuning Options** tab before starting a tuning session.</span></span>  
  
 <span data-ttu-id="a92ea-379">**限制微調時間**</span><span class="sxs-lookup"><span data-stu-id="a92ea-379">**Limit tuning time**</span></span>  
 <span data-ttu-id="a92ea-380">限制目前微調工作階段的時間。</span><span class="sxs-lookup"><span data-stu-id="a92ea-380">Limits the time for the current tuning session.</span></span> <span data-ttu-id="a92ea-381">提供更多微調時間以改善建議的品質。</span><span class="sxs-lookup"><span data-stu-id="a92ea-381">Providing more time for turning improves the quality of the recommendations.</span></span> <span data-ttu-id="a92ea-382">若要確保最佳建議，請勿選取此選項。</span><span class="sxs-lookup"><span data-stu-id="a92ea-382">To ensure the best recommendations, do not select this option.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="a92ea-383">Tuning Advisor 會在分析期間耗用系統資源。</span><span class="sxs-lookup"><span data-stu-id="a92ea-383">Tuning Advisor consumes system resources during analysis.</span></span> <span data-ttu-id="a92ea-384">預期在要微調的伺服器會有較重的工作負載期間之前，您可以使用 **[限制微調時間]** 來停止微調。</span><span class="sxs-lookup"><span data-stu-id="a92ea-384">Use **Limit tuning time** to stop tuning before periods of anticipated heavy workload on the server being tuned.</span></span>  
  
 <span data-ttu-id="a92ea-385">**[進階選項]**</span><span class="sxs-lookup"><span data-stu-id="a92ea-385">**Advanced Options**</span></span>  
 <span data-ttu-id="a92ea-386">使用 [進階微調選項] 對話方塊，即可設定最大空間、最大索引鍵資料行和線上索引建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-386">Use the **Advanced Tuning Options** dialog box to configure the maximum space, maximum key columns, and online index recommendations.</span></span>  
  
 <span data-ttu-id="a92ea-387">**定義建議的最大空間 (MB)**</span><span class="sxs-lookup"><span data-stu-id="a92ea-387">**Define max. space for recommendations (MB)**</span></span>  
 <span data-ttu-id="a92ea-388">鍵入 Database Engine Tuning Advisor 所建議，由實體設計結構使用的最大空間量。</span><span class="sxs-lookup"><span data-stu-id="a92ea-388">Type the maximum amount of space to be used by physical design structures recommended by Database Engine Tuning Advisor.</span></span>  
  
 <span data-ttu-id="a92ea-389">如果此處未輸入任何值，Database Engine Tuning Advisor 會假設採用下列空間限制中的較小者：</span><span class="sxs-lookup"><span data-stu-id="a92ea-389">If no value is entered here, Database Engine Tuning Advisor assumes the smaller of the following space limits:</span></span>  
  
-   <span data-ttu-id="a92ea-390">目前的原始資料大小的三倍，其中包括資料庫中各資料表的堆積和叢集索引的總大小。</span><span class="sxs-lookup"><span data-stu-id="a92ea-390">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="a92ea-391">所有相連硬碟的可用空間，加上原始資料大小。</span><span class="sxs-lookup"><span data-stu-id="a92ea-391">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="a92ea-392">**[包含來自所有資料庫的計畫快取事件]**</span><span class="sxs-lookup"><span data-stu-id="a92ea-392">**Include plan cache events from all databases**</span></span>  
 <span data-ttu-id="a92ea-393">指定分析所有資料庫中的計畫快取事件。</span><span class="sxs-lookup"><span data-stu-id="a92ea-393">Specify that plan cache events from all databases are analyzed.</span></span>  
  
 <span data-ttu-id="a92ea-394">**每個索引的最大資料行數**</span><span class="sxs-lookup"><span data-stu-id="a92ea-394">**Max. columns per index**</span></span>  
 <span data-ttu-id="a92ea-395">指定任何索引中所包含的最大資料行數。</span><span class="sxs-lookup"><span data-stu-id="a92ea-395">Specify the maximum number of columns to include in any index.</span></span> <span data-ttu-id="a92ea-396">預設值為 1023。</span><span class="sxs-lookup"><span data-stu-id="a92ea-396">The default is 1023.</span></span>  
  
 <span data-ttu-id="a92ea-397">**所有建議都是離線**</span><span class="sxs-lookup"><span data-stu-id="a92ea-397">**All recommendations are offline**</span></span>  
 <span data-ttu-id="a92ea-398">產生可能最佳的建議，但不要建議在線上建立任何實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="a92ea-398">Generate the best recommendations possible, but do not recommend that any physical design structures be created online.</span></span>  
  
 <span data-ttu-id="a92ea-399">**如果可能，產生線上建議**</span><span class="sxs-lookup"><span data-stu-id="a92ea-399">**Generate online recommendations where possible**</span></span>  
 <span data-ttu-id="a92ea-400">建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式來實作建議時，即使有較快速的離線方法可以使用，也請選擇可以維持伺服器在線上的實作方法。</span><span class="sxs-lookup"><span data-stu-id="a92ea-400">When creating [!INCLUDE[tsql](../../includes/tsql-md.md)] statements to implement the recommendations, choose methods that can be implemented with the server online, even if a faster offline method is available.</span></span>  
  
 <span data-ttu-id="a92ea-401">**只產生線上建議**</span><span class="sxs-lookup"><span data-stu-id="a92ea-401">**Generate only online recommendations**</span></span>  
 <span data-ttu-id="a92ea-402">只提供伺服器能夠維持在線上的建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-402">Only make recommendations that allow the server to stay online.</span></span>  
  
 <span data-ttu-id="a92ea-403">**停止時間**</span><span class="sxs-lookup"><span data-stu-id="a92ea-403">**Stop at**</span></span>  
 <span data-ttu-id="a92ea-404">提供 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 應該停止的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="a92ea-404">Provide the date and time when [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor should stop.</span></span>  
  
 <span data-ttu-id="a92ea-405">**索引與索引檢視**</span><span class="sxs-lookup"><span data-stu-id="a92ea-405">**Indexes and indexed views**</span></span>  
 <span data-ttu-id="a92ea-406">核取此方塊以包含加入叢集索引、非叢集索引以及索引檢視的建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-406">Check this box to include recommendations for adding clustered indexes, nonclustered indexes, and indexed views.</span></span>  
  
 <span data-ttu-id="a92ea-407">**索引檢視**</span><span class="sxs-lookup"><span data-stu-id="a92ea-407">**Indexed views**</span></span>  
 <span data-ttu-id="a92ea-408">只包含加入索引檢視的建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-408">Only include recommendations for adding indexed views.</span></span> <span data-ttu-id="a92ea-409">不建議叢集與非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="a92ea-409">Clustered and nonclustered indexes will not be recommended.</span></span>  
  
 <span data-ttu-id="a92ea-410">**包含篩選的索引**</span><span class="sxs-lookup"><span data-stu-id="a92ea-410">**Include filtered indexes**</span></span>  
 <span data-ttu-id="a92ea-411">包含加入篩選之索引的建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-411">Include recommendations for adding filtered indexes.</span></span> <span data-ttu-id="a92ea-412">如果您選取下列其中一個實體設計結構，即可使用這個選項：[索引與索引檢視]、[索引] 或 [非叢集索引]。</span><span class="sxs-lookup"><span data-stu-id="a92ea-412">This option is available if you select one of these physical design structures: **Indexes and indexed views**, **Indexes**, or **Nonclustered indexes**.</span></span>  
  
 <span data-ttu-id="a92ea-413">**索引數**</span><span class="sxs-lookup"><span data-stu-id="a92ea-413">**Indexes**</span></span>  
 <span data-ttu-id="a92ea-414">只包含加入叢集與非叢集索引的建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-414">Only include recommendations for adding clustered and nonclustered indexes.</span></span> <span data-ttu-id="a92ea-415">不建議索引檢視。</span><span class="sxs-lookup"><span data-stu-id="a92ea-415">Indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="a92ea-416">**[非叢集索引]**</span><span class="sxs-lookup"><span data-stu-id="a92ea-416">**Nonclustered indexes**</span></span>  
 <span data-ttu-id="a92ea-417">只包含非叢集索引的建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-417">Include recommendations for only nonclustered indexes.</span></span> <span data-ttu-id="a92ea-418">不建議叢集索引與索引檢視。</span><span class="sxs-lookup"><span data-stu-id="a92ea-418">Clustered indexes and indexed views will not be recommended.</span></span>  
  
 <span data-ttu-id="a92ea-419">**只評估現有 PDS 的使用情形**</span><span class="sxs-lookup"><span data-stu-id="a92ea-419">**Evaluate utilization of existing PDS only**</span></span>  
 <span data-ttu-id="a92ea-420">評估目前索引的效能，但不建議其他索引或索引檢視。</span><span class="sxs-lookup"><span data-stu-id="a92ea-420">Evaluate the effectiveness of the current indexes but do not recommend additional indexes or indexed views.</span></span>  
  
 <span data-ttu-id="a92ea-421">**沒有資料分割。**</span><span class="sxs-lookup"><span data-stu-id="a92ea-421">**No partitioning**</span></span>  
 <span data-ttu-id="a92ea-422">不建議資料分割。</span><span class="sxs-lookup"><span data-stu-id="a92ea-422">Do not recommend partitioning.</span></span>  
  
 <span data-ttu-id="a92ea-423">**完整的資料分割**</span><span class="sxs-lookup"><span data-stu-id="a92ea-423">**Full partitioning**</span></span>  
 <span data-ttu-id="a92ea-424">包含資料分割的建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-424">Include recommendations for partitioning.</span></span>  
  
 <span data-ttu-id="a92ea-425">**對齊的資料分割**</span><span class="sxs-lookup"><span data-stu-id="a92ea-425">**Aligned partitioning**</span></span>  
 <span data-ttu-id="a92ea-426">將會對齊新建議的資料分割，以便於維護資料分割。</span><span class="sxs-lookup"><span data-stu-id="a92ea-426">New recommended partitions will be aligned to make partitions easy to maintain.</span></span>  
  
 <span data-ttu-id="a92ea-427">**不要保留任何現有的 PDS**</span><span class="sxs-lookup"><span data-stu-id="a92ea-427">**Do not keep any existing PDS**</span></span>  
 <span data-ttu-id="a92ea-428">建議卸除不必要的現有索引、檢視和資料分割。</span><span class="sxs-lookup"><span data-stu-id="a92ea-428">Recommend dropping unnecessary existing indexes, views, and partitioning.</span></span> <span data-ttu-id="a92ea-429">如果現有的實體設計結構 (PDS) 對工作負載很有用， [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 就不會建議將它卸除。</span><span class="sxs-lookup"><span data-stu-id="a92ea-429">If an existing physical design structure (PDS) is useful to the workload, [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor does not recommend dropping it.</span></span>  
  
 <span data-ttu-id="a92ea-430">**只保留索引**</span><span class="sxs-lookup"><span data-stu-id="a92ea-430">**Keep indexes only**</span></span>  
 <span data-ttu-id="a92ea-431">保留所有現有的索引，但建議卸除不必要的索引檢視與資料分割。</span><span class="sxs-lookup"><span data-stu-id="a92ea-431">Keep all existing indexes but recommend dropping unnecessary indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="a92ea-432">**保留所有現有的 PDS**</span><span class="sxs-lookup"><span data-stu-id="a92ea-432">**Keep all existing PDS**</span></span>  
 <span data-ttu-id="a92ea-433">保留所有現有的索引、索引檢視以及資料分割。</span><span class="sxs-lookup"><span data-stu-id="a92ea-433">Keep all existing indexes, indexed views, and partitioning.</span></span>  
  
 <span data-ttu-id="a92ea-434">**只保留叢集索引**</span><span class="sxs-lookup"><span data-stu-id="a92ea-434">**Keep clustered indexes only**</span></span>  
 <span data-ttu-id="a92ea-435">保留所有現有的叢集索引，但建議卸除不必要的索引檢視、資料分割以及非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="a92ea-435">Keep all existing clustered indexes but recommend dropping unnecessary indexed views, partitions, and nonclustered indexes.</span></span>  
  
 <span data-ttu-id="a92ea-436">**保留對齊的資料分割**</span><span class="sxs-lookup"><span data-stu-id="a92ea-436">**Keep aligned partitioning**</span></span>  
 <span data-ttu-id="a92ea-437">保留目前對齊的資料分割結構，但建議卸除不必要的索引檢視、索引以及非對齊的資料分割。</span><span class="sxs-lookup"><span data-stu-id="a92ea-437">Keep partitioning structures that are currently aligned, but recommend dropping unnecessary indexed views, indexes, and non-aligned partitioning.</span></span> <span data-ttu-id="a92ea-438">建議的任何其他資料分割將對齊目前的資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="a92ea-438">Any additional partitioning recommended will align with the current partitioning scheme.</span></span>  
  
###### <a name="progress-tab-options"></a><span data-ttu-id="a92ea-439">進度索引標籤選項</span><span class="sxs-lookup"><span data-stu-id="a92ea-439">Progress Tab Options</span></span>  
 <span data-ttu-id="a92ea-440">Database Engine Tuning Advisor 的 **[進度]** 索引標籤會在 Database Engine Tuning Advisor 開始分析工作負載之後出現。</span><span class="sxs-lookup"><span data-stu-id="a92ea-440">The **Progress** tab of Database Engine Tuning Advisor appears after Database Engine Tuning Advisor begins analyzing a workload.</span></span>  
  
 <span data-ttu-id="a92ea-441">如果您要在啟動之後停止微調，請選擇 **[動作]** 功能表上的下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="a92ea-441">If you want to stop the tuning session after it has started, choose one of the following options on the **Actions** menu:</span></span>  
  
-   <span data-ttu-id="a92ea-442">[停止分析 (附帶建議)] 會停止微調工作階段並提示您確定是否要 Database Engine Tuning Advisor 根據現階段完成的分析產生建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-442">**Stop Analysis (With Recommendations)** stops the tuning session and prompts you to decide whether you want Database Engine Tuning Advisor to generate recommendations based on the analysis done up to this point.</span></span>  
  
-   <span data-ttu-id="a92ea-443">**[停止分析]** 會停止微調工作階段而不產生任何建議。</span><span class="sxs-lookup"><span data-stu-id="a92ea-443">**Stop Analysis** stops the tuning session without generating any recommendations.</span></span>  
  
 <span data-ttu-id="a92ea-444">**微調進度**</span><span class="sxs-lookup"><span data-stu-id="a92ea-444">**Tuning Progress**</span></span>  
 <span data-ttu-id="a92ea-445">指出進度的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="a92ea-445">Indicates the current status of the progress.</span></span> <span data-ttu-id="a92ea-446">包含已執行的動作數目，以及錯誤、成功與接收之警告訊息的數目。</span><span class="sxs-lookup"><span data-stu-id="a92ea-446">Contains the number of actions performed, and the number of error, success, and warning messages received.</span></span>  
  
 <span data-ttu-id="a92ea-447">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="a92ea-447">**Details**</span></span>  
 <span data-ttu-id="a92ea-448">包含指出狀態的圖示。</span><span class="sxs-lookup"><span data-stu-id="a92ea-448">Contains an icon indicating status.</span></span>  
  
 <span data-ttu-id="a92ea-449">**動作**</span><span class="sxs-lookup"><span data-stu-id="a92ea-449">**Action**</span></span>  
 <span data-ttu-id="a92ea-450">顯示要執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="a92ea-450">Displays the steps being performed.</span></span>  
  
 <span data-ttu-id="a92ea-451">**狀態**</span><span class="sxs-lookup"><span data-stu-id="a92ea-451">**Status**</span></span>  
 <span data-ttu-id="a92ea-452">顯示動作步驟的狀態。</span><span class="sxs-lookup"><span data-stu-id="a92ea-452">Displays the status of the action step.</span></span>  
  
 <span data-ttu-id="a92ea-453">**訊息**</span><span class="sxs-lookup"><span data-stu-id="a92ea-453">**Message**</span></span>  
 <span data-ttu-id="a92ea-454">包含動作步驟所傳回的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="a92ea-454">Contains any messages returned by the action steps.</span></span>  
  
 <span data-ttu-id="a92ea-455">**微調記錄**</span><span class="sxs-lookup"><span data-stu-id="a92ea-455">**Tuning Log**</span></span>  
 <span data-ttu-id="a92ea-456">包含此微調工作階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a92ea-456">Contains information regarding this tuning session.</span></span> <span data-ttu-id="a92ea-457">若要列印此記錄，請以滑鼠右鍵按一下記錄，然後按一下 [列印]。</span><span class="sxs-lookup"><span data-stu-id="a92ea-457">To print this log, right-click the log, and then click **Print**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a92ea-458">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a92ea-458">See Also</span></span>  
 <span data-ttu-id="a92ea-459">[檢視及處理 Database Engine Tuning Advisor 的輸出](database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="a92ea-459">[View and Work with the Output from the Database Engine Tuning Advisor](database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="a92ea-460">dta 公用程式</span><span class="sxs-lookup"><span data-stu-id="a92ea-460">dta Utility</span></span>](../../tools/dta/dta-utility.md)  
  
  
