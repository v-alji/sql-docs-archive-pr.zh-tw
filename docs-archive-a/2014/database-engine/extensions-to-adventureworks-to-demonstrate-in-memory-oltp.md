---
title: 示範記憶體內部 OLTP 的 AdventureWorks 延伸模組 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0186b7f2-cead-4203-8360-b6890f37cde8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73a87751aa6cd4734f81b60cdd87a62939ba4ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707786"
---
# <a name="extensions-to-adventureworks-to-demonstrate-in-memory-oltp"></a><span data-ttu-id="24e19-102">示範記憶體中 OLTP 的 AdventureWorks 延伸模組</span><span class="sxs-lookup"><span data-stu-id="24e19-102">Extensions to AdventureWorks to Demonstrate In-Memory OLTP</span></span>
    
## <a name="overview"></a><span data-ttu-id="24e19-103">概觀</span><span class="sxs-lookup"><span data-stu-id="24e19-103">Overview</span></span>  
 <span data-ttu-id="24e19-104">此範例示範新的 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 功能 (屬於 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]的一部分)。</span><span class="sxs-lookup"><span data-stu-id="24e19-104">This sample showcases the new [!INCLUDE[hek_2](../includes/hek-2-md.md)] feature, which is part of [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="24e19-105">此範例顯示新的記憶體最佳化資料表和原生編譯的預存程序，並可用來示範 [!INCLUDE[hek_2](../includes/hek-2-md.md)]的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="24e19-105">It shows the new memory-optimized tables and natively-compiled stored procedures, and can be used to demonstrate performance benefits of [!INCLUDE[hek_2](../includes/hek-2-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24e19-106">若要檢視 SQL Server 2016 的這項主題，請參閱 [示範記憶體內 OLTP 的 AdventureWorks 擴充功能](https://msdn.microsoft.com/library/mt465764.aspx)</span><span class="sxs-lookup"><span data-stu-id="24e19-106">To view this topic for SQL Server 2016, see [Extensions to AdventureWorks to Demonstrate In-Memory OLTP](https://msdn.microsoft.com/library/mt465764.aspx)</span></span>  
  
 <span data-ttu-id="24e19-107">此範例會將 AdventureWorks 資料庫中的 5 個資料表移轉至記憶體最佳化資料表，並包含銷售訂單處理的工作負載示範。</span><span class="sxs-lookup"><span data-stu-id="24e19-107">The sample migrates 5 tables in the AdventureWorks database to memory-optimized, and it includes a demo workload for sales order processing.</span></span> <span data-ttu-id="24e19-108">您可以利用此工作負載示範，查看在伺服器上使用 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="24e19-108">You can use this demo workload to see the performance benefit of using [!INCLUDE[hek_2](../includes/hek-2-md.md)] on your server.</span></span>  
  
 <span data-ttu-id="24e19-109">在此範例的描述中，我們會討論將資料表移轉至 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 的利弊，以說明 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]的記憶體最佳化資料表尚未支援的功能。</span><span class="sxs-lookup"><span data-stu-id="24e19-109">In the description of the sample we discuss the tradeoffs that were made in migrating the tables to [!INCLUDE[hek_2](../includes/hek-2-md.md)] to account for the features that are not (yet) supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span>  
  
 <span data-ttu-id="24e19-110">此範例的文件集結構如下：</span><span class="sxs-lookup"><span data-stu-id="24e19-110">The documentation of this sample is structured as follows:</span></span>  
  
-   <span data-ttu-id="24e19-111">安裝範例及執行工作負載示範的[必要條件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="24e19-111">[Prerequisites](#Prerequisites) for installing the sample and running the demo workload</span></span>  
  
-   <span data-ttu-id="24e19-112">[安裝以 AdventureWorks 為基礎的 In-Memory OLTP 範例](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)的指示</span><span class="sxs-lookup"><span data-stu-id="24e19-112">Instructions for [Installing the In-Memory OLTP sample based on AdventureWorks](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)</span></span>  
  
-   <span data-ttu-id="24e19-113">[範例資料表和程式的描述](#Descriptionofthesampletablesandprocedures)-這包括範例中新增至 AdventureWorks 之資料表和程式的描述，以及將 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 一些原始 AdventureWorks 資料表遷移至記憶體優化的考慮。</span><span class="sxs-lookup"><span data-stu-id="24e19-113">[Description of the sample tables and procedures](#Descriptionofthesampletablesandprocedures) - this includes descriptions of the tables and procedures added to AdventureWorks by the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample, as well as considerations for migrating some of the original AdventureWorks tables to memory-optimized</span></span>  
  
-   <span data-ttu-id="24e19-114">執行 [使用工作負載示範的效能度量](#PerformanceMeasurementsusingtheDemoWorkload) 之指示 - 包括安裝及執行 ostress (用於驅動工作負載的工具) 的指示，以及執行工作負載示範本身的指示</span><span class="sxs-lookup"><span data-stu-id="24e19-114">Instructions for performing [Performance Measurements using the Demo Workload](#PerformanceMeasurementsusingtheDemoWorkload) - this includes instructions for installing and running ostress, a tool using for driving the workload, as well as running the demo workload itself</span></span>  
  
-   [<span data-ttu-id="24e19-115">範例中的記憶體和磁碟空間使用量</span><span class="sxs-lookup"><span data-stu-id="24e19-115">Memory and Disk Space Utilization in the Sample</span></span>](#MemoryandDiskSpaceUtilizationintheSample)  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="24e19-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="24e19-116">Prerequisites</span></span>  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<span data-ttu-id="24e19-117">RTM-評估版、開發人員或企業版</span><span class="sxs-lookup"><span data-stu-id="24e19-117">RTM - Evaluation, Developer, or Enterprise edition</span></span>  
  
-   <span data-ttu-id="24e19-118">基於效能測試考量，伺服器的規格必須與您的實際執行環境類似。</span><span class="sxs-lookup"><span data-stu-id="24e19-118">For performance testing, a server with specifications similar to your production environment.</span></span> <span data-ttu-id="24e19-119">您應為此特定範例準備至少 16GB 的記憶體供 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用。</span><span class="sxs-lookup"><span data-stu-id="24e19-119">For this particular sample you should have at least 16GB of memory available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="24e19-120">如需硬體的一般指導方針 [!INCLUDE[hek_2](../includes/hek-2-md.md)] ，請參閱下列 blog 文章：[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span><span class="sxs-lookup"><span data-stu-id="24e19-120">For general guidelines on hardware for [!INCLUDE[hek_2](../includes/hek-2-md.md)], see the following blog post:[https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/](https://cloudblogs.microsoft.com/sqlserver/2013/08/01/hardware-considerations-for-in-memory-oltp-in-sql-server-2014/)</span></span>  
  
##  <a name="installing-the-hek_2-sample-based-on-adventureworks"></a><a name="InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks"></a><span data-ttu-id="24e19-121">安裝以 [!INCLUDE[hek_2](../includes/hek-2-md.md)] AdventureWorks 為基礎的範例</span><span class="sxs-lookup"><span data-stu-id="24e19-121">Installing the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample based on AdventureWorks</span></span>  
 <span data-ttu-id="24e19-122">請遵循下列步驟來安裝範例：</span><span class="sxs-lookup"><span data-stu-id="24e19-122">Follow these steps to install the sample:</span></span>  
  
1.  <span data-ttu-id="24e19-123">下載 AdventureWorks2014 資料庫的完整備份封存：</span><span class="sxs-lookup"><span data-stu-id="24e19-123">Download the archive for the full backup of the AdventureWorks2014 database:</span></span>  
  
    1.  <span data-ttu-id="24e19-124">開啟下列內容： [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661) 。</span><span class="sxs-lookup"><span data-stu-id="24e19-124">Open the following: [https://msftdbprodsamples.codeplex.com/downloads/get/880661](https://msftdbprodsamples.codeplex.com/downloads/get/880661).</span></span>  
  
    2.  <span data-ttu-id="24e19-125">提示將檔案儲存至本機資料夾時。</span><span class="sxs-lookup"><span data-stu-id="24e19-125">When prompted to save the file to a local folder.</span></span>  
  
2.  <span data-ttu-id="24e19-126">將 **AdventureWorks2014.bak** 檔案解壓縮至本機資料夾，例如 'c:\temp'。</span><span class="sxs-lookup"><span data-stu-id="24e19-126">Extract the **AdventureWorks2014.bak** file to a local folder, for example 'c:\temp'.</span></span>  
  
3.  <span data-ttu-id="24e19-127">使用 [!INCLUDE[tsql](../includes/tsql-md.md)] 或 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]還原資料庫備份：</span><span class="sxs-lookup"><span data-stu-id="24e19-127">Restore the database backup using [!INCLUDE[tsql](../includes/tsql-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    1.  <span data-ttu-id="24e19-128">識別目標資料夾和資料檔案的檔案名稱，例如</span><span class="sxs-lookup"><span data-stu-id="24e19-128">Identify the target folder and filename for the data file, for example</span></span>  
  
         <span data-ttu-id="24e19-129">'h:\DATA\AdventureWorks2014_Data.mdf'</span><span class="sxs-lookup"><span data-stu-id="24e19-129">'h:\DATA\AdventureWorks2014_Data.mdf'</span></span>  
  
    2.  <span data-ttu-id="24e19-130">識別目標資料夾和記錄檔的檔案名稱，例如</span><span class="sxs-lookup"><span data-stu-id="24e19-130">Identify the target folder and filename for the log file, for example</span></span>  
  
         <span data-ttu-id="24e19-131">'i:\DATA\AdventureWorks2014_log.ldf'</span><span class="sxs-lookup"><span data-stu-id="24e19-131">'i:\DATA\AdventureWorks2014_log.ldf'</span></span>  
  
        1.  <span data-ttu-id="24e19-132">放置記錄檔的磁碟機應該與放置資料檔案的磁碟機不同，最好使用低度延遲的磁碟機以取得最高效能，例如 SSD 或 PCIe 儲存體。</span><span class="sxs-lookup"><span data-stu-id="24e19-132">The log file should be placed on a different drive than the data file, ideally a low latency drive such as an SSD or PCIe storage, for maximum performance.</span></span>  
  
     <span data-ttu-id="24e19-133">範例 T-SQL 指令碼：</span><span class="sxs-lookup"><span data-stu-id="24e19-133">Example T-SQL script:</span></span>  
  
    ```  
    RESTORE DATABASE [AdventureWorks2014]   
      FROM DISK = N'C:\temp\AdventureWorks2014.bak'   
        WITH FILE = 1,    
      MOVE N'AdventureWorks2014_Data' TO N'h:\DATA\AdventureWorks2014_Data.mdf',    
      MOVE N'AdventureWorks2014_Log' TO N'i:\DATA\AdventureWorks2014_log.ldf'  
     GO  
    ```  
  
4.  <span data-ttu-id="24e19-134">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的查詢視窗中執行下列命令，將資料庫擁有者變更為伺服器上的登入：</span><span class="sxs-lookup"><span data-stu-id="24e19-134">Change the database owner to a login on your server, by running the following command in the query window of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]:</span></span>  
  
    ```  
    ALTER AUTHORIZATION ON DATABASE::AdventureWorks2014 TO [<NewLogin>]  
    ```  
  
5.  <span data-ttu-id="24e19-135">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] 從[SQL Server 2014 RTM 記憶體內部 OLTP 範例](https://go.microsoft.com/fwlink/?LinkID=396372)中，將範例腳本「rtm 範例」下載到本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="24e19-135">Download the sample script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' from [SQL Server 2014 RTM In-Memory OLTP Sample](https://go.microsoft.com/fwlink/?LinkID=396372) to a local folder.</span></span>  
  
6.  <span data-ttu-id="24e19-136">更新腳本 ' RTM Sample .sql ' 中變數 ' checkpoint_files_location ' 的 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 值 [!INCLUDE[hek_2](../includes/hek-2-md.md)] ，以指向檢查點檔案的目標位置 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="24e19-136">Update the value for the variable 'checkpoint_files_location' in the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql', to point to the target location for the [!INCLUDE[hek_2](../includes/hek-2-md.md)] checkpoint files.</span></span> <span data-ttu-id="24e19-137">檢查點檔案應該置於具有適當循序 IO 效能的磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="24e19-137">The checkpoint files should be placed on a drive with good sequential IO performance.</span></span>  
  
     <span data-ttu-id="24e19-138">更新變數 'database_name' 的值，使其指向 AdventureWorks2014 資料庫。</span><span class="sxs-lookup"><span data-stu-id="24e19-138">Update the value for the variable 'database_name' to point to the AdventureWorks2014 database.</span></span>  
  
    1.  <span data-ttu-id="24e19-139">請務必包含反斜線 ' \' 做為路徑名稱的一部分</span><span class="sxs-lookup"><span data-stu-id="24e19-139">Be sure to include the backslash '\' as part of the path name</span></span>  
  
    2.  <span data-ttu-id="24e19-140">範例：</span><span class="sxs-lookup"><span data-stu-id="24e19-140">Example:</span></span>  
  
        ```  
        :setvar checkpoint_files_location "d:\DBData\"  
        ...  
        :setvar database_name "AdventureWorks2014"  
        ```  
  
7.  <span data-ttu-id="24e19-141">請使用下列兩個方式之一來執行範例指令碼：</span><span class="sxs-lookup"><span data-stu-id="24e19-141">Execute the sample script, in one of two ways:</span></span>  
  
    1.  <span data-ttu-id="24e19-142">使用 sqlcmd 命令列公用程式。</span><span class="sxs-lookup"><span data-stu-id="24e19-142">Using the sqlcmd command-line utility.</span></span> <span data-ttu-id="24e19-143">例如，從包含指令碼之資料夾中的命令列提示字元，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="24e19-143">For example, for example by running the following command from the command-line prompt in the folder containing the script:</span></span>  
  
        ```  
        sqlcmd -S . -E -i "ssSQL14 RTM hek_2 Sample.sql"  
        ```  
  
    2.  <span data-ttu-id="24e19-144">使用 Management Studio：</span><span class="sxs-lookup"><span data-stu-id="24e19-144">Using Management Studio:</span></span>  
  
        1.  <span data-ttu-id="24e19-145">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[hek_2](../includes/hek-2-md.md)] 在查詢視窗中開啟腳本 ' RTM 範例 .sql '</span><span class="sxs-lookup"><span data-stu-id="24e19-145">Open the script '[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] RTM [!INCLUDE[hek_2](../includes/hek-2-md.md)] Sample.sql' in a query window</span></span>  
  
        2.  <span data-ttu-id="24e19-146">連接至包含 AdventureWorks2014 資料庫的目標伺服器</span><span class="sxs-lookup"><span data-stu-id="24e19-146">Connect to the target server that contains the database AdventureWorks2014</span></span>  
  
        3.  <span data-ttu-id="24e19-147">按一下 [查詢 > 的 SQLCMD 模式]，以啟用 SQLCMD 模式</span><span class="sxs-lookup"><span data-stu-id="24e19-147">Enable SQLCMD Mode, by clicking on 'Query -> SQLCMD Mode'</span></span>  
  
        4.  <span data-ttu-id="24e19-148">按一下 [執行] 按鈕以執行腳本</span><span class="sxs-lookup"><span data-stu-id="24e19-148">Click the button 'Execute' to run the script</span></span>  
  
##  <a name="description-of-the-sample-tables-and-procedures"></a><a name="Descriptionofthesampletablesandprocedures"></a> <span data-ttu-id="24e19-149">範例資料表和程序描述</span><span class="sxs-lookup"><span data-stu-id="24e19-149">Description of the sample tables and procedures</span></span>  
 <span data-ttu-id="24e19-150">此範例以 AdventureWorks 中的現有資料表為基礎，為產品和銷售訂單建立新資料表。</span><span class="sxs-lookup"><span data-stu-id="24e19-150">The sample creates new tables for products and sales orders, based on existing tables in AdventureWorks.</span></span> <span data-ttu-id="24e19-151">新資料表的結構描述類似現有的資料表，但有一些差異 (如下所述)。</span><span class="sxs-lookup"><span data-stu-id="24e19-151">The schema of the new tables is similar to the existing tables, with a few differences, as explained below.</span></span>  
  
 <span data-ttu-id="24e19-152">新的記憶體最佳化資料表具有後置詞 '_inmem'。</span><span class="sxs-lookup"><span data-stu-id="24e19-152">The new memory-optimized tables carry the suffix '_inmem'.</span></span> <span data-ttu-id="24e19-153">此範例也會包含具有後置詞 '_ondisk' 的對應資料表，這些資料表可用來在系統上的記憶體最佳化資料表與磁碟資料表之間，進行一對一的效能比較。</span><span class="sxs-lookup"><span data-stu-id="24e19-153">The sample also includes corresponding tables carrying the suffix '_ondisk' - these tables can be used to make a one-to-one comparison between the performance of memory-optimized tables and disk-based tables on your system..</span></span>  
  
 <span data-ttu-id="24e19-154">請注意，工作負載中用於比較效能的記憶體最佳化資料表是完全持久且完整記錄的。</span><span class="sxs-lookup"><span data-stu-id="24e19-154">Note that the memory-optimized tables used in the workload for performance comparison are fully durable and fully logged.</span></span> <span data-ttu-id="24e19-155">這些資料表不會為了提升效能而犧牲持久性或可靠性。</span><span class="sxs-lookup"><span data-stu-id="24e19-155">They do not sacrifice durability or reliability to attain the performance gain.</span></span>  
  
 <span data-ttu-id="24e19-156">此範例的目標工作負載是銷售訂單處理，同時也會考量產品和折扣的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="24e19-156">The target workload for this sample is sales order processing, where we consider also information about products and discounts.</span></span> <span data-ttu-id="24e19-157">因此需要 SalesOrderHeader、SalesOrderDetail、Product、SpecialOffer 和 SpecialOfferProduct 資料表。</span><span class="sxs-lookup"><span data-stu-id="24e19-157">To this end, the table SalesOrderHeader, SalesOrderDetail, Product, SpecialOffer, and SpecialOfferProduct.</span></span>  
  
 <span data-ttu-id="24e19-158">兩個新的預存程序 Sales.usp_InsertSalesOrder_inmem 和 Sales.usp_UpdateSalesOrderShipInfo_inmem，可用來插入銷售訂單及更新給定銷售訂單的出貨資訊。</span><span class="sxs-lookup"><span data-stu-id="24e19-158">Two new stored procedures, Sales.usp_InsertSalesOrder_inmem and Sales.usp_UpdateSalesOrderShipInfo_inmem, are used to insert sales orders and to update the shipping information of a given sales order.</span></span>  
  
 <span data-ttu-id="24e19-159">新的結構描述「示範」包含協助程式資料表和預存程序，可執行工作負載示範。</span><span class="sxs-lookup"><span data-stu-id="24e19-159">The new schema 'Demo' contains helper tables and stored procedures to execute a demo workload.</span></span>  
  
 <span data-ttu-id="24e19-160">具體而言， [!INCLUDE[hek_2](../includes/hek-2-md.md)] 範例會將下列物件加入 AdventureWorks：</span><span class="sxs-lookup"><span data-stu-id="24e19-160">Concretely, the [!INCLUDE[hek_2](../includes/hek-2-md.md)] sample adds the following objects to AdventureWorks:</span></span>  
  
### <a name="tables-added-by-the-sample"></a><span data-ttu-id="24e19-161">此範例加入的資料表</span><span class="sxs-lookup"><span data-stu-id="24e19-161">Tables added by the sample</span></span>  
  
#### <a name="the-new-tables"></a><span data-ttu-id="24e19-162">新資料表</span><span class="sxs-lookup"><span data-stu-id="24e19-162">The New Tables</span></span>  
 <span data-ttu-id="24e19-163">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-163">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="24e19-164">銷售訂單的相關標頭資訊。</span><span class="sxs-lookup"><span data-stu-id="24e19-164">Header information about sales orders.</span></span> <span data-ttu-id="24e19-165">每個銷售訂單在此資料表中有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="24e19-165">Each sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="24e19-166">Sales.SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-166">Sales.SalesOrderDetail_inmem</span></span>  
  
-   <span data-ttu-id="24e19-167">銷售訂單的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="24e19-167">Details of sales orders.</span></span> <span data-ttu-id="24e19-168">銷售訂單的每個明細項目在此資料表中有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="24e19-168">Each line item of a sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="24e19-169">Sales.SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-169">Sales.SpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="24e19-170">特殊供應項目的相關資訊，包括與每個特殊供應項目相關聯的折扣百分比。</span><span class="sxs-lookup"><span data-stu-id="24e19-170">Information about special offers, including the discount percentage associated with each special offer.</span></span>  
  
 <span data-ttu-id="24e19-171">Sales.SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-171">Sales.SpecialOfferProduct_inmem</span></span>  
  
-   <span data-ttu-id="24e19-172">特殊供應項目與產品之間的參考資料表。</span><span class="sxs-lookup"><span data-stu-id="24e19-172">Reference table between special offers and products.</span></span> <span data-ttu-id="24e19-173">每個特殊供應項目可能適用於零個或多個產品，而每個產品也可適用於零個或多個特殊供應項目。</span><span class="sxs-lookup"><span data-stu-id="24e19-173">Each special offer can feature zero or more products, and each product can be featured in zero or more special offers.</span></span>  
  
 <span data-ttu-id="24e19-174">Production.Product_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-174">Production.Product_inmem</span></span>  
  
-   <span data-ttu-id="24e19-175">產品的相關資訊，包括產品的標價。</span><span class="sxs-lookup"><span data-stu-id="24e19-175">Information about products, including their list price.</span></span>  
  
 <span data-ttu-id="24e19-176">Demo.DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="24e19-176">Demo.DemoSalesOrderDetailSeed</span></span>  
  
-   <span data-ttu-id="24e19-177">在工作負載示範中用於建構範例銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="24e19-177">Used in the demo workload to construct sample sales orders.</span></span>  
  
 <span data-ttu-id="24e19-178">以磁碟為基礎的資料表變化：</span><span class="sxs-lookup"><span data-stu-id="24e19-178">Disk-based variations of the tables:</span></span>  
  
-   <span data-ttu-id="24e19-179">Sales.SalesOrderHeader_ondisk</span><span class="sxs-lookup"><span data-stu-id="24e19-179">Sales.SalesOrderHeader_ondisk</span></span>  
  
-   <span data-ttu-id="24e19-180">Sales.SalesOrderDetail_ondisk</span><span class="sxs-lookup"><span data-stu-id="24e19-180">Sales.SalesOrderDetail_ondisk</span></span>  
  
-   <span data-ttu-id="24e19-181">Sales.SpecialOffer_ondisk</span><span class="sxs-lookup"><span data-stu-id="24e19-181">Sales.SpecialOffer_ondisk</span></span>  
  
-   <span data-ttu-id="24e19-182">Sales.SpecialOfferProduct_ondisk</span><span class="sxs-lookup"><span data-stu-id="24e19-182">Sales.SpecialOfferProduct_ondisk</span></span>  
  
-   <span data-ttu-id="24e19-183">Production.Product_ondisk</span><span class="sxs-lookup"><span data-stu-id="24e19-183">Production.Product_ondisk</span></span>  
  
#### <a name="differences-between-original-disk-based-and-the-and-new-memory-optimized-tables"></a><span data-ttu-id="24e19-184">原始磁碟資料表與新的記憶體最佳化資料表之間的差異</span><span class="sxs-lookup"><span data-stu-id="24e19-184">Differences between original disk-based and the and new memory-optimized tables</span></span>  
 <span data-ttu-id="24e19-185">大體而言，此範例所導入的新資料表使用與原始資料表相同的資料行和資料類型。</span><span class="sxs-lookup"><span data-stu-id="24e19-185">For the most part, the new tables introduced by this sample use the same columns and the same data types as the original tables.</span></span> <span data-ttu-id="24e19-186">但是仍有一些差異。</span><span class="sxs-lookup"><span data-stu-id="24e19-186">However, there are a few differences.</span></span> <span data-ttu-id="24e19-187">以下列出這些差異及變更的基本原理。</span><span class="sxs-lookup"><span data-stu-id="24e19-187">We list the differences below, along with a rationale for the changes.</span></span>  
  
 <span data-ttu-id="24e19-188">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-188">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="24e19-189">記憶體最佳化資料表支援「預設條件約束」 ，且大部分的預設條件約束在移轉後會保持原狀。</span><span class="sxs-lookup"><span data-stu-id="24e19-189">*Default constraints* are supported for memory-optimized tables, and most default constraints we migrated as is.</span></span> <span data-ttu-id="24e19-190">不過，原始資料表 Sales.SalesOrderHeader 包含兩個預設條件約束，會擷取資料行 OrderDate 和 ModifiedDate 的目前日期。</span><span class="sxs-lookup"><span data-stu-id="24e19-190">However, the original table Sales.SalesOrderHeader contains two default constraints that retrieve the current date, for the columns OrderDate and ModifiedDate.</span></span> <span data-ttu-id="24e19-191">在具有大量並行的高輸送量訂單處理工作負載中，任何全域資源都可能會成為競爭重點。</span><span class="sxs-lookup"><span data-stu-id="24e19-191">In a high throughput order processing workload with a lot of concurrency, any global resource can become a point of contention.</span></span> <span data-ttu-id="24e19-192">系統時間即為這類全域資源。根據觀察，執行插入銷售訂單的 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 工作負載時，系統時間可能會成為瓶頸，特別是在需要針對銷售訂單標頭的多個資料行擷取系統時間，並同時擷取銷售訂單詳細資料時。</span><span class="sxs-lookup"><span data-stu-id="24e19-192">System time is such a global resource, and we have observed that it can become a bottleneck when running an [!INCLUDE[hek_2](../includes/hek-2-md.md)] workload that inserts sales orders, in particular if the system time needs to be retrieved for multiple columns in the sales order header, as well as the sales order details.</span></span> <span data-ttu-id="24e19-193">這個問題已在此範例中獲得解決，只對每個插入的銷售訂單擷取一次系統時間，然後在預存程序 Sales.usp_InsertSalesOrder_inmem 中，將此值做為 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 的日期時間資料行使用。</span><span class="sxs-lookup"><span data-stu-id="24e19-193">The problem is addressed in this sample by retrieving the system time only once for each sales order that is inserted, and use that value for the datetime columns in SalesOrderHeader_inmem and SalesOrderDetail_inmem, in the stored procedure Sales.usp_InsertSalesOrder_inmem.</span></span>  
  
-   <span data-ttu-id="24e19-194">「別名 UDT」\*\* - 原始資料表針對資料行 PurchaseOrderNumber 和 AccountNumber，分別使用兩個別名使用者定義資料類型 (UDT) dbo.OrderNumber 和 dbo.AccountNumber。</span><span class="sxs-lookup"><span data-stu-id="24e19-194">*Alias UDTs* - The original table uses two alias user-defined data types (UDTs) dbo.OrderNumber and dbo.AccountNumber, for the columns PurchaseOrderNumber and AccountNumber, respectively.</span></span> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="24e19-195">不支援在記憶體最佳化資料表中使用別名 UDT，因此新資料表會分別使用系統資料類型 Nvarchar(25) 和 Nvarchar(15)。</span><span class="sxs-lookup"><span data-stu-id="24e19-195">does not support alias UDT for memory-optimized tables, thus the new tables use system data types nvarchar(25) and nvarchar(15), respectively.</span></span>  
  
-   <span data-ttu-id="24e19-196">「索引鍵中的資料行可為 Null」 - 在原始資料表中，資料行 SalesPersonID 可為 Null，但是在新資料表中，資料行不可為 Null，且預設條件約束必須帶有值 (-1)。</span><span class="sxs-lookup"><span data-stu-id="24e19-196">*Nullable columns in index keys* - In the original table, the column SalesPersonID is nullable, while in the new tables the column is not nullable and has a default constraint with value (-1).</span></span> <span data-ttu-id="24e19-197">這是因為記憶體最佳化資料表上的索引不可以在索引鍵中有可為 Null 的資料行，在此情況下，-1 會代替 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="24e19-197">This is because indexes on memory-optimized tables cannot have nullable columns in the index key; -1 is a surrogate for NULL in this case.</span></span>  
  
-   <span data-ttu-id="24e19-198">「計算資料行」 - 由於 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 不支援在記憶體最佳化資料表中使用計算資料行，因此會省略計算資料行 SalesOrderNumber 和 TotalDue。</span><span class="sxs-lookup"><span data-stu-id="24e19-198">*Computed columns* - The computed columns SalesOrderNumber and TotalDue are omitted, as [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] does not support computed columns in memory-optimized tables.</span></span> <span data-ttu-id="24e19-199">新檢視 Sales.vSalesOrderHeader_extended_inmem 會反映資料行 SalesOrderNumber 和 TotalDue。</span><span class="sxs-lookup"><span data-stu-id="24e19-199">The new view Sales.vSalesOrderHeader_extended_inmem reflects the columns SalesOrderNumber and TotalDue.</span></span> <span data-ttu-id="24e19-200">因此，如果需要這些資料行，您可以使用此檢視。</span><span class="sxs-lookup"><span data-stu-id="24e19-200">Therefore, you can use this view if these columns are needed.</span></span>  
  
-   <span data-ttu-id="24e19-201">在*中，記憶體最佳化資料表不支援「外部索引鍵條件約束」*[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24e19-201">*Foreign key constraints* are not supported for memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="24e19-202">此外，SalesOrderHeader_inmem 是範例工作負載中的作用資料表，而外部索引鍵條件約束需要對所有 DML 作業進行額外的處理，因為它需要查閱這些條件約束中參考的其他所有資料表。</span><span class="sxs-lookup"><span data-stu-id="24e19-202">In addition, SalesOrderHeader_inmem is a hot table in the example workload, and foreign keys constraints require additional processing for all DML operations, as it requires lookups in all the other tables referenced in these constraints.</span></span> <span data-ttu-id="24e19-203">因此，此處的假設是應用程式會確保參考完整性，但插入資料列時不會驗證參考完整性。</span><span class="sxs-lookup"><span data-stu-id="24e19-203">Therefore, the assumption is that the app ensures referential integrity, and referential integrity is not validated when rows are inserted.</span></span> <span data-ttu-id="24e19-204">您可以使用預存程序 dbo.usp_ValidateIntegrity 驗證此資料表中資料的參考完整性，其指令碼如下：</span><span class="sxs-lookup"><span data-stu-id="24e19-204">Referential integrity for the data in this table can be verified using the stored procedure dbo.usp_ValidateIntegrity, using the following script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="24e19-205">在 SQ Server 2014 中，記憶體最佳化資料表不支援「檢查條件約束」\*\* 。</span><span class="sxs-lookup"><span data-stu-id="24e19-205">*Check constraints* are not supported for memory-optimized tables in SQ Server 2014.</span></span> <span data-ttu-id="24e19-206">使用下列指令碼可驗證網域完整性及參考完整性：</span><span class="sxs-lookup"><span data-stu-id="24e19-206">Domain integrity is validated along with referential integrity using this script:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="24e19-207">*Rowguid* - Rowguid 資料行會遭到省略。</span><span class="sxs-lookup"><span data-stu-id="24e19-207">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="24e19-208">記憶體最佳化資料表支援 uniqueidentifier，但是 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]不支援 ROWGUIDCOL 選項。</span><span class="sxs-lookup"><span data-stu-id="24e19-208">While uniqueidentifier is support for memory-optimized tables, the option ROWGUIDCOL is not supported in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="24e19-209">這類資料行通常會用於合併式複寫或具有 filestream 資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="24e19-209">Columns of this kind are typically used for either merge replication or tables that have filestream columns.</span></span> <span data-ttu-id="24e19-210">此範例不包含這兩者。</span><span class="sxs-lookup"><span data-stu-id="24e19-210">This sample includes neither.</span></span>  
  
 <span data-ttu-id="24e19-211">Sales.SalesOrderDetail</span><span class="sxs-lookup"><span data-stu-id="24e19-211">Sales.SalesOrderDetail</span></span>  
  
-   <span data-ttu-id="24e19-212">*預設條件約束* - 類似 SalesOrderHeader，預設條件約束要求不得移轉系統日期/時間，而是由插入銷售訂單的預存程序在第一次插入時，負責插入目前的系統日期/時間。</span><span class="sxs-lookup"><span data-stu-id="24e19-212">*Default constraints* - similar to SalesOrderHeader, the default constraint requiring the system date/time is not migrated, instead the stored procedure inserting sales orders takes care of inserting the current system date/time on first insert.</span></span>  
  
-   <span data-ttu-id="24e19-213">*計算資料行* - 由於 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 中的記憶體最佳化資料表不支援計算資料行，因此不會移轉計算資料行 LineTotal。</span><span class="sxs-lookup"><span data-stu-id="24e19-213">*Computed columns* - the computed column LineTotal was not migrated as computed columns are not supported with memory-optimized tables in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="24e19-214">若要存取此資料行，請使用 Sales.vSalesOrderDetail_extended_inmem 檢視。</span><span class="sxs-lookup"><span data-stu-id="24e19-214">To access this column use the view Sales.vSalesOrderDetail_extended_inmem.</span></span>  
  
-   <span data-ttu-id="24e19-215">*Rowguid* - Rowguid 資料行會遭到省略。</span><span class="sxs-lookup"><span data-stu-id="24e19-215">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="24e19-216">如需詳細資訊，請參閱 SalesOrderHeader 資料表的描述。</span><span class="sxs-lookup"><span data-stu-id="24e19-216">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="24e19-217">如需有關「檢查條件約束」 \*\* 和「外部索引鍵條件約束」 \*\* 的詳細資訊，請參閱 SalesOrderHeader 的描述。</span><span class="sxs-lookup"><span data-stu-id="24e19-217">For *check* and *foreign key* constraints see the description of SalesOrderHeader.</span></span> <span data-ttu-id="24e19-218">下列指令碼可用來驗證此資料表的網域和參考完整性：</span><span class="sxs-lookup"><span data-stu-id="24e19-218">The following script can be used to verify domain and referential integrity for this table:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SalesOrderHeader_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
 <span data-ttu-id="24e19-219">Production.Product</span><span class="sxs-lookup"><span data-stu-id="24e19-219">Production.Product</span></span>  
  
-   <span data-ttu-id="24e19-220">*別名 UDT* - 原始資料表使用使用者定義資料類型 dbo.Flag，相當於系統資料類型 bit。</span><span class="sxs-lookup"><span data-stu-id="24e19-220">*Alias UDTs* - the original table uses the user-defined data type dbo.Flag, which is equivalent to the system data type bit.</span></span> <span data-ttu-id="24e19-221">移轉的資料表會改用 bit 資料類型。</span><span class="sxs-lookup"><span data-stu-id="24e19-221">The migrated table uses the bit data type instead.</span></span>  
  
-   <span data-ttu-id="24e19-222">*BIN2 定序*-資料行名稱和 ProductNumber 會包含在索引鍵中，因此必須在中具有 BIN2 定序 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="24e19-222">*BIN2 collation* - The columns Name and ProductNumber are included in index keys, and must thus have BIN2 collations in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].</span></span> <span data-ttu-id="24e19-223">此處的假設是應用程式不依賴定序規格，例如區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="24e19-223">Here, the assumption is that the app does not rely on collation specifics, like case insensitivity.</span></span>  
  
-   <span data-ttu-id="24e19-224">*Rowguid* - Rowguid 資料行會遭到省略。</span><span class="sxs-lookup"><span data-stu-id="24e19-224">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="24e19-225">如需詳細資訊，請參閱 SalesOrderHeader 資料表的描述。</span><span class="sxs-lookup"><span data-stu-id="24e19-225">For details see the description for the table SalesOrderHeader.</span></span>  
  
-   <span data-ttu-id="24e19-226">「唯一條件約束」\*\*, \*\* 及「外部索引鍵條件約束」 \*\* are accounted for in two ways: the stored procedures Product.usp_InsertProduct_inmem 及「外部索引鍵條件約束」 Product.usp_DeleteProduct_inmem can be used to insert 及「外部索引鍵條件約束」 delete products; these procedures validate domain 及「外部索引鍵條件約束」 referential integrity, 及「外部索引鍵條件約束」 will fail if integrity is violated.</span><span class="sxs-lookup"><span data-stu-id="24e19-226">*Unique*, *Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Product.usp_InsertProduct_inmem and Product.usp_DeleteProduct_inmem can be used to insert and delete products; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="24e19-227">此外，下列指令碼可用來驗證網域和參考完整性的現狀：</span><span class="sxs-lookup"><span data-stu-id="24e19-227">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Production.Product')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
    -   <span data-ttu-id="24e19-228">請注意，預存程序 usp_InsertProduct_inmem 和 usp_DeleteProduct_inmem 只會考量移轉資料表之間的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="24e19-228">Note that the store procedures usp_InsertProduct_inmem and usp_DeleteProduct_inmem consider only foreign keys between the migrated tables.</span></span> <span data-ttu-id="24e19-229">而不會考量其他資料表 ProductModel、ProductSubcategory 和 UnitMeasure 的參考。</span><span class="sxs-lookup"><span data-stu-id="24e19-229">References to other tables ProductModel, ProductSubcategory, and UnitMeasure are not considered.</span></span>  
  
 <span data-ttu-id="24e19-230">Sales.SpecialOffer</span><span class="sxs-lookup"><span data-stu-id="24e19-230">Sales.SpecialOffer</span></span>  
  
-   <span data-ttu-id="24e19-231">「檢查條件約束」\*\* 和「外部索引鍵條件約束」 \*\* are accounted for in two ways: the stored procedures Sales.usp_InsertSpecialOffer_inmem 和「外部索引鍵條件約束」 Sales.usp_DeleteSpecialOffer_inmem can be used to insert 和「外部索引鍵條件約束」 delete special offers; these procedures validate domain 和「外部索引鍵條件約束」 referential integrity, 和「外部索引鍵條件約束」 will fail if integrity is violated.</span><span class="sxs-lookup"><span data-stu-id="24e19-231">*Check* and *Foreign Key constraints* are accounted for in two ways: the stored procedures Sales.usp_InsertSpecialOffer_inmem and Sales.usp_DeleteSpecialOffer_inmem can be used to insert and delete special offers; these procedures validate domain and referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="24e19-232">此外，下列指令碼可用來驗證網域和參考完整性的現狀：</span><span class="sxs-lookup"><span data-stu-id="24e19-232">In addition, the follow script can be used to validate domain and referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOffer_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="24e19-233">*Rowguid* - Rowguid 資料行會遭到省略。</span><span class="sxs-lookup"><span data-stu-id="24e19-233">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="24e19-234">如需詳細資訊，請參閱 SalesOrderHeader 資料表的描述。</span><span class="sxs-lookup"><span data-stu-id="24e19-234">For details see the description for the table SalesOrderHeader.</span></span>  
  
 <span data-ttu-id="24e19-235">Sales.SpecialOfferProduct</span><span class="sxs-lookup"><span data-stu-id="24e19-235">Sales.SpecialOfferProduct</span></span>  
  
-   <span data-ttu-id="24e19-236">「外部索引鍵條件約束」\*\* 的說明包含兩點：預存程序 Sales.usp_InsertSpecialOfferProduct_inmem 可用來插入特殊供應項目與產品之間的關聯性，此程序會驗證參考完整性，如果違反完整性則會失敗。</span><span class="sxs-lookup"><span data-stu-id="24e19-236">*Foreign Key constraints* are accounted for in two ways: the stored procedure Sales.usp_InsertSpecialOfferProduct_inmem can be used to insert relationships between special offers and products; this procedures validates referential integrity, and will fail if integrity is violated.</span></span> <span data-ttu-id="24e19-237">此外，下列指令碼可用來驗證參考完整性的現狀：</span><span class="sxs-lookup"><span data-stu-id="24e19-237">In addition, the follow script can be used to validate referential integrity as is:</span></span>  
  
    ```  
    DECLARE @o int = object_id(N'Sales.SpecialOfferProduct_inmem')  
    EXEC dbo.usp_ValidateIntegrity @o  
    ```  
  
-   <span data-ttu-id="24e19-238">*Rowguid* - Rowguid 資料行會遭到省略。</span><span class="sxs-lookup"><span data-stu-id="24e19-238">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="24e19-239">如需詳細資訊，請參閱 SalesOrderHeader 資料表的描述。</span><span class="sxs-lookup"><span data-stu-id="24e19-239">For details see the description for the table SalesOrderHeader.</span></span>  
  
#### <a name="considerations-for-indexes-on-memory-optimized-tables"></a><span data-ttu-id="24e19-240">記憶體最佳化資料表上索引的考量</span><span class="sxs-lookup"><span data-stu-id="24e19-240">Considerations for indexes on memory-optimized tables</span></span>  
 <span data-ttu-id="24e19-241">記憶體最佳化資料表的基準索引為 NONCLUSTERED 索引，支援點查閱 (等號比較述詞的索引搜尋)、範圍掃描 (不等號比較述詞的索引搜尋)、完整索引掃描及依序掃描。</span><span class="sxs-lookup"><span data-stu-id="24e19-241">The baseline index for memory-optimized tables is the NONCLUSTERED index, which supports point lookups (index seek on equality predicate), range scans (index seek in inequality predicate), full index scans, and ordered scans.</span></span> <span data-ttu-id="24e19-242">此外，NONCLUSTERED 索引支援搜尋索引鍵的前置資料行。</span><span class="sxs-lookup"><span data-stu-id="24e19-242">In addition, NONCLUSTERED indexes support searching on leading columns of the index key.</span></span> <span data-ttu-id="24e19-243">事實上，記憶體最佳化的 NONCLUSTERED 索引支援以磁碟為基礎之 NONCLUSTERED 索引支援的所有作業，唯一的例外狀況是回溯掃描。</span><span class="sxs-lookup"><span data-stu-id="24e19-243">In fact memory-optimized NONCLUSTERED indexes support all the operations supported by disk-based NONCLUSTERED indexes, with the only exception being backward scans.</span></span> <span data-ttu-id="24e19-244">因此，使用 NONCLUSTERED 索引對您的索引而言是安全的選擇。</span><span class="sxs-lookup"><span data-stu-id="24e19-244">Therefore, using NONCLUSTERED indexes is a safe choice for your indexes.</span></span>  
  
 <span data-ttu-id="24e19-245">HASH 索引可用來進一步最佳化工作負載。</span><span class="sxs-lookup"><span data-stu-id="24e19-245">HASH indexes are can be used to further optimize the workload.</span></span> <span data-ttu-id="24e19-246">特別是最佳化點查閱和資料列插入。</span><span class="sxs-lookup"><span data-stu-id="24e19-246">They are particularly optimized for point lookups and row inserts.</span></span> <span data-ttu-id="24e19-247">不過請注意，這些索引不支援範圍掃描、依序掃描，或搜尋前置索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="24e19-247">However, one must consider that they do not support range scans, ordered scans, or search on leading index key columns.</span></span> <span data-ttu-id="24e19-248">因此，您需要謹慎地使用這些索引。</span><span class="sxs-lookup"><span data-stu-id="24e19-248">Therefore, care needs to be taken when using these indexes.</span></span> <span data-ttu-id="24e19-249">此外，您必須在建立時指定 bucket_count。</span><span class="sxs-lookup"><span data-stu-id="24e19-249">In addition, it is necessary to specify the bucket_count at create time.</span></span> <span data-ttu-id="24e19-250">此計數通常應該設定為索引鍵數值到兩倍索引鍵數值之間的值，不過高估通常不會造成問題。</span><span class="sxs-lookup"><span data-stu-id="24e19-250">It should usually be set at between one and two times the number of index key values, but overestimating is usually not a problem.</span></span>  
  
 <span data-ttu-id="24e19-251">如需有關 [index guidelines](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) (索引指導方針) 及 [choosing the right bucket_count](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx)(選擇正確的 bucket_count) 之指導方針的詳細資料，請參閱《線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="24e19-251">See Books Online for more details about [index guidelines](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) and guidelines for [choosing the right bucket_count](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="24e19-252">移轉之資料表上的索引已調整為適用於銷售訂單處理工作負載示範。</span><span class="sxs-lookup"><span data-stu-id="24e19-252">The indexes on the migrated tables have been tuned for the demo sales order processing workload.</span></span> <span data-ttu-id="24e19-253">此工作負載需要在 Sales.SalesOrderHeader_inmem 和 Sales.SalesOrderDetail_inmem 資料表中進行插入和點查閱，也需要對 Production.Product_inmem 和 Sales.SpecialOffer_inmem 資料表中的主索引鍵資料行進行點查閱。</span><span class="sxs-lookup"><span data-stu-id="24e19-253">The workload relies on inserts and point lookups in the tables Sales.SalesOrderHeader_inmem and Sales.SalesOrderDetail_inmem, and it also relies on point lookups on the primary key columns in the tables Production.Product_inmem and Sales.SpecialOffer_inmem.</span></span>  
  
 <span data-ttu-id="24e19-254">Sales.SalesOrderHeader_inmem 具有三個索引，基於效能的考量，以及由於此工作負載不需要依序或範圍掃描，這三個索引都是 HASH 索引。</span><span class="sxs-lookup"><span data-stu-id="24e19-254">Sales.SalesOrderHeader_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="24e19-255">(SalesOrderID) 上的 HASH 索引：bucket_count 的大小調整為 1,000 萬 (無條件進位到 1,600 萬)，因為預期的銷售訂單數目為 1,000 萬</span><span class="sxs-lookup"><span data-stu-id="24e19-255">HASH index on (SalesOrderID): bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="24e19-256">(SalesPersonID) 上的 HASH 索引：bucket_count 為 100 萬。</span><span class="sxs-lookup"><span data-stu-id="24e19-256">HASH index on (SalesPersonID): bucket_count is 1 million.</span></span> <span data-ttu-id="24e19-257">提供的資料集沒有很多銷售人員，但容許未來成長使用；此外，如果將 bucket_count 的大小調整至過大，即可避免受到點查閱效能降低的影響。</span><span class="sxs-lookup"><span data-stu-id="24e19-257">The data set provided does not have a lot of sales persons, but this allows for future growth, plus you don't pay a performance penalty for point lookups if the bucket_count is oversized.</span></span>  
  
-   <span data-ttu-id="24e19-258">(CustomerID) 上的 HASH 索引：bucket_count 為 100 萬。</span><span class="sxs-lookup"><span data-stu-id="24e19-258">HASH index on (CustomerID): bucket_count is 1 million.</span></span> <span data-ttu-id="24e19-259">提供的資料集沒有很多客戶，但容許未來成長使用。</span><span class="sxs-lookup"><span data-stu-id="24e19-259">The data set provided does not have a lot of customers, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="24e19-260">Sales.SalesOrderDetail_inmem 具有三個索引，基於效能的考量，以及由於此工作負載不需要依序或範圍掃描，這三個索引都是 HASH 索引。</span><span class="sxs-lookup"><span data-stu-id="24e19-260">Sales.SalesOrderDetail_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="24e19-261">(SalesOrderID, SalesOrderDetailID) 上的 HASH 索引：這是主索引鍵索引，即使 (SalesOrderID, SalesOrderDetailID) 上的查閱不頻繁，針對索引鍵使用雜湊索引仍可加速資料列插入。</span><span class="sxs-lookup"><span data-stu-id="24e19-261">HASH index on (SalesOrderID, SalesOrderDetailID): this is the primary key index, and even though lookups on (SalesOrderID, SalesOrderDetailID) will be infrequent, using a hash index for the key speeds up row inserts.</span></span> <span data-ttu-id="24e19-262">bucket_count 的大小調整為 5,000 萬 (無條件進位到 6,700 萬)：預期的銷售訂單數目為 1,000 萬，放大的用意是為了使每個訂單平均有 5 個項目。</span><span class="sxs-lookup"><span data-stu-id="24e19-262">The bucket_count is sized at 50 million (rounded up to 67 million): the expected number of sales orders is 10 million, and this is sized to have an average of 5 items per order</span></span>  
  
-   <span data-ttu-id="24e19-263">(SalesOrderID) 上的 HASH 索引：銷售訂單的查閱很頻繁，您會想要尋找對應至單一訂單的所有明細項目。</span><span class="sxs-lookup"><span data-stu-id="24e19-263">HASH index on (SalesOrderID): lookups by sales order are frequent: you will want to find all the line items corresponding to a single order.</span></span>  <span data-ttu-id="24e19-264">bucket_count 的大小調整為 1,000 萬 (無條件進位到 1,600 萬)，因為預期的銷售訂單數目為 1,000 萬</span><span class="sxs-lookup"><span data-stu-id="24e19-264">bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="24e19-265">(ProductID) 上的 HASH 索引：bucket_count 為 100 萬。</span><span class="sxs-lookup"><span data-stu-id="24e19-265">HASH index on (ProductID): bucket_count is 1 million.</span></span> <span data-ttu-id="24e19-266">提供的資料集沒有很多產品，但容許未來成長使用。</span><span class="sxs-lookup"><span data-stu-id="24e19-266">The data set provided does not have a lot of product, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="24e19-267">Production.Product_inmem 具有三個索引</span><span class="sxs-lookup"><span data-stu-id="24e19-267">Production.Product_inmem has three indexes</span></span>  
  
-   <span data-ttu-id="24e19-268">(ProductID) 上的 HASH 索引：ProductID 上的查閱位於工作負載示範的關鍵路徑中，因此這是雜湊索引</span><span class="sxs-lookup"><span data-stu-id="24e19-268">HASH index on (ProductID): lookups on ProductID are in the critical path for the demo workload, therefore this is a hash index</span></span>  
  
-   <span data-ttu-id="24e19-269">(Name) 上的 NONCLUSTERED 索引：允許對產品名稱進行依序掃描</span><span class="sxs-lookup"><span data-stu-id="24e19-269">NONCLUSTERED index on (Name): this will allow ordered scans of product names</span></span>  
  
-   <span data-ttu-id="24e19-270">(ProductNumber) 上的 NONCLUSTERED 索引：允許對產品號碼進行依序掃描</span><span class="sxs-lookup"><span data-stu-id="24e19-270">NONCLUSTERED index on (ProductNumber): this will allow ordered scans of product numbers</span></span>  
  
 <span data-ttu-id="24e19-271">Sales.SpecialOffer_inmem 在 (SpecialOfferID) 上具有一個 HASH 索引：特殊供應項目的點查閱在工作負載示範的關鍵過程中。</span><span class="sxs-lookup"><span data-stu-id="24e19-271">Sales.SpecialOffer_inmem has one HASH index on (SpecialOfferID): point lookups of special offers are in the critical part of the demo workload.</span></span> <span data-ttu-id="24e19-272">bucket_count 的大小調整為 100 萬，以允許未來成長使用。</span><span class="sxs-lookup"><span data-stu-id="24e19-272">The bucket_count is sized at 1 million to allow for future growth.</span></span>  
  
 <span data-ttu-id="24e19-273">工作負載示範中不會參考 Sales.SpecialOfferProduct_inmem，因此沒有在此資料表上使用雜湊索引來最佳化工作負載的明顯需求 - (SpecialOfferID, ProductID) 和 (ProductID) 上的索引為 NONCLUSTERED。</span><span class="sxs-lookup"><span data-stu-id="24e19-273">Sales.SpecialOfferProduct_inmem is not referenced in the demo workload, and thus there is no apparent need to use hash indexes on this table to optimize the workload - the indexes on (SpecialOfferID, ProductID) and (ProductID) are NONCLUSTERED.</span></span>  
  
 <span data-ttu-id="24e19-274">請注意，上述的部分 bucket_counts 大小過大，但不包括 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 上索引的 bucket_counts：其大小剛好是 1,000 萬個銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="24e19-274">Notice that in the above some of the bucket_counts are over-sized, but not the bucket_counts for the indexes on SalesOrderHeader_inmem and SalesOrderDetail_inmem: they are sized for just 10 million sales orders.</span></span> <span data-ttu-id="24e19-275">這樣做是為了在記憶體可用量很低的系統上安裝範例，在此情況下，工作負載示範會因為記憶體不足而失敗。</span><span class="sxs-lookup"><span data-stu-id="24e19-275">This was done to allow installing the sample on systems with low memory availability, although in those cases the demo workload will fail with out-of-memory.</span></span> <span data-ttu-id="24e19-276">如果您想要擴充到超過 1,000 萬個銷售訂單，請視需求隨意增加值區計數。</span><span class="sxs-lookup"><span data-stu-id="24e19-276">If you do want to scale well beyond 10 million sales orders, feel free to increase the bucket counts accordingly.</span></span>  
  
#### <a name="considerations-for-memory-utilization"></a><span data-ttu-id="24e19-277">記憶體使用量的考量</span><span class="sxs-lookup"><span data-stu-id="24e19-277">Considerations for memory utilization</span></span>  
 <span data-ttu-id="24e19-278">範例資料庫中的記憶體使用情形在工作負載示範前後的變化，都會在 [記憶體最佳化資料表的記憶體使用量](#Memoryutilizationforthememory-optimizedtables)一節中說明。</span><span class="sxs-lookup"><span data-stu-id="24e19-278">Memory utilization in the sample database, both before and after running the demo workload, is discussed in the Section [Memory utilization for the memory-optimized tables](#Memoryutilizationforthememory-optimizedtables).</span></span>  
  
### <a name="stored-procedures-added-by-the-sample"></a><span data-ttu-id="24e19-279">此範例加入的預存程序</span><span class="sxs-lookup"><span data-stu-id="24e19-279">Stored Procedures added by the sample</span></span>  
 <span data-ttu-id="24e19-280">以下是用於插入銷售訂單及更新出貨詳細資料的兩個主要預存程序：</span><span class="sxs-lookup"><span data-stu-id="24e19-280">The two key stored procedures for inserting sales order and updating shipping details are as follows:</span></span>  
  
-   <span data-ttu-id="24e19-281">Sales.usp_InsertSalesOrder_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-281">Sales.usp_InsertSalesOrder_inmem</span></span>  
  
    -   <span data-ttu-id="24e19-282">在資料庫中插入新的銷售訂單，並輸出該銷售訂單的 SalesOrderID。</span><span class="sxs-lookup"><span data-stu-id="24e19-282">Inserts a new sales order in the database and outputs the SalesOrderID for that sales order.</span></span> <span data-ttu-id="24e19-283">此預存程序會擷取銷售訂單標頭的詳細資料及訂單中的明細項目，以做為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="24e19-283">As input parameters it takes details for the sales order header, as well as the line items in the order.</span></span>  
  
    -   <span data-ttu-id="24e19-284">輸出參數：</span><span class="sxs-lookup"><span data-stu-id="24e19-284">Output parameter:</span></span>  
  
        -   <span data-ttu-id="24e19-285">@SalesOrderID int - 剛插入之銷售訂單的 SalesOrderID</span><span class="sxs-lookup"><span data-stu-id="24e19-285">@SalesOrderID int - the SalesOrderID for the sales order that was just inserted</span></span>  
  
    -   <span data-ttu-id="24e19-286">輸入參數 (必要)：</span><span class="sxs-lookup"><span data-stu-id="24e19-286">Input parameters (required):</span></span>  
  
        -   <span data-ttu-id="24e19-287">@DueDate datetime2</span><span class="sxs-lookup"><span data-stu-id="24e19-287">@DueDate datetime2</span></span>  
  
        -   <span data-ttu-id="24e19-288">@CustomerID int</span><span class="sxs-lookup"><span data-stu-id="24e19-288">@CustomerID int</span></span>  
  
        -   <span data-ttu-id="24e19-289">@BillToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="24e19-289">@BillToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="24e19-290">@ShipToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="24e19-290">@ShipToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="24e19-291">@ShipMethodID [int]</span><span class="sxs-lookup"><span data-stu-id="24e19-291">@ShipMethodID [int]</span></span>  
  
        -   <span data-ttu-id="24e19-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - 包含訂單明細項目的 TVP</span><span class="sxs-lookup"><span data-stu-id="24e19-292">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - TVP that contains the line items of the order</span></span>  
  
    -   <span data-ttu-id="24e19-293">輸入參數 (選擇性)：</span><span class="sxs-lookup"><span data-stu-id="24e19-293">Input parameters (optional):</span></span>  
  
        -   <span data-ttu-id="24e19-294">@Status [tinyint]</span><span class="sxs-lookup"><span data-stu-id="24e19-294">@Status [tinyint]</span></span>  
  
        -   <span data-ttu-id="24e19-295">@OnlineOrderFlag [bit]</span><span class="sxs-lookup"><span data-stu-id="24e19-295">@OnlineOrderFlag [bit]</span></span>  
  
        -   <span data-ttu-id="24e19-296">@PurchaseOrderNumber [nvarchar](25\)</span><span class="sxs-lookup"><span data-stu-id="24e19-296">@PurchaseOrderNumber [nvarchar](25\)</span></span>  
  
        -   <span data-ttu-id="24e19-297">@AccountNumber [nvarchar](15\)</span><span class="sxs-lookup"><span data-stu-id="24e19-297">@AccountNumber [nvarchar](15\)</span></span>  
  
        -   <span data-ttu-id="24e19-298">@SalesPersonID [int]</span><span class="sxs-lookup"><span data-stu-id="24e19-298">@SalesPersonID [int]</span></span>  
  
        -   <span data-ttu-id="24e19-299">@TerritoryID [int]</span><span class="sxs-lookup"><span data-stu-id="24e19-299">@TerritoryID [int]</span></span>  
  
        -   <span data-ttu-id="24e19-300">@CreditCardID [int]</span><span class="sxs-lookup"><span data-stu-id="24e19-300">@CreditCardID [int]</span></span>  
  
        -   <span data-ttu-id="24e19-301">@CreditCardApprovalCode [varchar](15\)</span><span class="sxs-lookup"><span data-stu-id="24e19-301">@CreditCardApprovalCode [varchar](15\)</span></span>  
  
        -   <span data-ttu-id="24e19-302">@CurrencyRateID [int]</span><span class="sxs-lookup"><span data-stu-id="24e19-302">@CurrencyRateID [int]</span></span>  
  
        -   <span data-ttu-id="24e19-303">@Comment nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="24e19-303">@Comment nvarchar(128)</span></span>  
  
-   <span data-ttu-id="24e19-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-304">Sales.usp_UpdateSalesOrderShipInfo_inmem</span></span>  
  
    -   <span data-ttu-id="24e19-305">更新給定銷售訂單的出貨資訊。</span><span class="sxs-lookup"><span data-stu-id="24e19-305">Update the shipping information for a given sales order.</span></span> <span data-ttu-id="24e19-306">這也會更新銷售訂單之所有明細項目的出貨資訊。</span><span class="sxs-lookup"><span data-stu-id="24e19-306">This will also update the shipping information for all line items of the sales order.</span></span>  
  
    -   <span data-ttu-id="24e19-307">這是原生編譯預存程序 Sales.usp_UpdateSalesOrderShipInfo_native 的包裝函式程序，其重試邏輯可處理更新相同訂單之並行交易所時產生的 (非預期) 潛在衝突。</span><span class="sxs-lookup"><span data-stu-id="24e19-307">This is a wrapper procedure for the natively compiled stored procedures Sales.usp_UpdateSalesOrderShipInfo_native with retry logic to deal with (unexpected) potential conflicts with concurrent transactions updating the same order.</span></span> <span data-ttu-id="24e19-308">如需有關重試邏輯的詳細資訊，請參閱 [這裡](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx)的《線上叢書》主題。</span><span class="sxs-lookup"><span data-stu-id="24e19-308">For more information about retry logic see the Books Online topic [here](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="24e19-309">Sales.usp_UpdateSalesOrderShipInfo_native</span><span class="sxs-lookup"><span data-stu-id="24e19-309">Sales.usp_UpdateSalesOrderShipInfo_native</span></span>  
  
    -   <span data-ttu-id="24e19-310">這是實際處理出貨資訊更新的原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="24e19-310">This is the natively compiled stored procedure that actually processes the update to the shipping information.</span></span> <span data-ttu-id="24e19-311">此程序是包裝函式預存程序 Sales.usp_UpdateSalesOrderShipInfo_inmem 呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="24e19-311">It is means to be called from the wrapper stored procedure Sales.usp_UpdateSalesOrderShipInfo_inmem.</span></span> <span data-ttu-id="24e19-312">如果客戶可處理失敗並實作重試邏輯，您便可以直接呼叫此程序，而不需使用包裝函式預存程序。</span><span class="sxs-lookup"><span data-stu-id="24e19-312">If the client can deal with failures and implements retry logic, you can call this procedure directly, rather than using the wrapper stored procedure.</span></span>  
  
 <span data-ttu-id="24e19-313">下列預存程序可用於工作負載示範。</span><span class="sxs-lookup"><span data-stu-id="24e19-313">The following stored procedure is used for the demo workload.</span></span>  
  
-   <span data-ttu-id="24e19-314">Demo.usp_DemoReset</span><span class="sxs-lookup"><span data-stu-id="24e19-314">Demo.usp_DemoReset</span></span>  
  
    -   <span data-ttu-id="24e19-315">透過清空及重新植入 SalesOrderHeader 和 SalesOrderDetail 資料表來重設示範。</span><span class="sxs-lookup"><span data-stu-id="24e19-315">Resets the demo by emptying and reseeding the SalesOrderHeader and SalesOrderDetail tables.</span></span>  
  
 <span data-ttu-id="24e19-316">下列預存程序可用於插入資料至記憶體最佳化資料表及從中刪除資料，同時確保網域和參考完整性。</span><span class="sxs-lookup"><span data-stu-id="24e19-316">The following stored procedures are used for inserting in and deleting from memory-optimized tables while guaranteeing domain and referential integrity.</span></span>  
  
-   <span data-ttu-id="24e19-317">Production.usp_InsertProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-317">Production.usp_InsertProduct_inmem</span></span>  
  
-   <span data-ttu-id="24e19-318">Production.usp_DeleteProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-318">Production.usp_DeleteProduct_inmem</span></span>  
  
-   <span data-ttu-id="24e19-319">Sales.usp_InsertSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-319">Sales.usp_InsertSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="24e19-320">Sales.usp_DeleteSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-320">Sales.usp_DeleteSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="24e19-321">Sales.usp_InsertSpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-321">Sales.usp_InsertSpecialOfferProduct_inmem</span></span>  
  
 <span data-ttu-id="24e19-322">最後，下列預存程序可用來驗證網域和參考完整性。</span><span class="sxs-lookup"><span data-stu-id="24e19-322">Finally the following stored procedure is used to verify domain and referential integrity.</span></span>  
  
1.  <span data-ttu-id="24e19-323">dbo.usp_ValidateIntegrity</span><span class="sxs-lookup"><span data-stu-id="24e19-323">dbo.usp_ValidateIntegrity</span></span>  
  
    -   <span data-ttu-id="24e19-324">選擇性參數：@object_id - 要驗證完整性的物件識別碼</span><span class="sxs-lookup"><span data-stu-id="24e19-324">Optional parameter: @object_id - ID of the object to validate integrity for</span></span>  
  
    -   <span data-ttu-id="24e19-325">此程序依賴資料表 dbo.DomainIntegrity、dbo.ReferentialIntegrity 和 dbo.UniqueIntegrity 取得需要驗證的完整性規則 - 此範例會根據 AdventureWorks 資料庫中原始資料表的檢查、外部索引鍵及唯一條件約束，以填入這些資料表。</span><span class="sxs-lookup"><span data-stu-id="24e19-325">This procedure relies on the tables dbo.DomainIntegrity, dbo.ReferentialIntegrity, and dbo.UniqueIntegrity for the integrity rules that need to be verified - the sample populates these tables based on the check, foreign key, and unique constraints that exist for the original tables in the AdventureWorks database.</span></span>  
  
    -   <span data-ttu-id="24e19-326">此程序依賴協助程式程序 dbo.usp_GenerateCKCheck、dbo.usp_GenerateFKCheck 和 dbo.GenerateUQCheck 來產生執行完整性檢查所需的 T-SQL。</span><span class="sxs-lookup"><span data-stu-id="24e19-326">It relies on the helper procedures dbo.usp_GenerateCKCheck, dbo.usp_GenerateFKCheck, and dbo.GenerateUQCheck to generate the T-SQL needed for performing the integrity checks.</span></span>  
  
##  <a name="performance-measurements-using-the-demo-workload"></a><a name="PerformanceMeasurementsusingtheDemoWorkload"></a> <span data-ttu-id="24e19-327">使用工作負載示範的效能度量</span><span class="sxs-lookup"><span data-stu-id="24e19-327">Performance Measurements using the Demo Workload</span></span>  
 <span data-ttu-id="24e19-328">Ostress 是由 [!INCLUDE[msCoName](../includes/msconame-md.md)] CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 支援小組所開發的命令列工具。</span><span class="sxs-lookup"><span data-stu-id="24e19-328">Ostress is a command-line tool that was developed by the [!INCLUDE[msCoName](../includes/msconame-md.md)] CSS [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] support team.</span></span> <span data-ttu-id="24e19-329">此工具可用來平行執行查詢或執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="24e19-329">This tool can be used to execute queries or run stored procedures in parallel.</span></span> <span data-ttu-id="24e19-330">您可以設定平行執行給定 T-SQL 陳述式的執行緒數目，以及指定此執行緒上應該執行陳述式的次數，ostress 會加快執行緒的速度，並平行執行所有執行緒上的陳述式。</span><span class="sxs-lookup"><span data-stu-id="24e19-330">You can configure the number of threads to run a given T-SQL statement in parallel, and you can specify how many times the statement should be executed on this thread; ostress will spin up the threads and execute the statement on all threads in parallel.</span></span> <span data-ttu-id="24e19-331">所有執行緒完成執行之後，ostress 會報告所有執行緒完成執行所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="24e19-331">After execution finishes for all threads, ostress will report the time taken for all threads to finish execution.</span></span>  
  
### <a name="installing-ostress"></a><span data-ttu-id="24e19-332">安裝 ostress</span><span class="sxs-lookup"><span data-stu-id="24e19-332">Installing ostress</span></span>  
 <span data-ttu-id="24e19-333">Ostress 會當做 RML 公用程式的一部分來安裝，您無法獨立安裝 ostress。</span><span class="sxs-lookup"><span data-stu-id="24e19-333">Ostress is installed as part of the RML Utilities; there is no standalone installation for ostress.</span></span>  
  
 <span data-ttu-id="24e19-334">安裝步驟：</span><span class="sxs-lookup"><span data-stu-id="24e19-334">Installation steps:</span></span>  
  
1.  <span data-ttu-id="24e19-335">從下列頁面下載並執行 RML 公用程式的 x64 安裝套件：[https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span><span class="sxs-lookup"><span data-stu-id="24e19-335">Download and run the x64 installation package for the RML utilities from the following page: [https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx](https://blogs.msdn.com/b/psssql/archive/2013/10/29/cumulative-update-2-to-the-rml-utilities-for-microsoft-sql-server-released.aspx)</span></span>  
  
2.  <span data-ttu-id="24e19-336">如果出現對話方塊，指出特定檔案正在使用，請按一下 [繼續]</span><span class="sxs-lookup"><span data-stu-id="24e19-336">If there is a dialog box saying certain files are in use, click 'Continue'</span></span>  
  
### <a name="running-ostress"></a><span data-ttu-id="24e19-337">執行 ostress</span><span class="sxs-lookup"><span data-stu-id="24e19-337">Running ostress</span></span>  
 <span data-ttu-id="24e19-338">Ostress 會從命令提示字元執行。</span><span class="sxs-lookup"><span data-stu-id="24e19-338">Ostress is run from the command-line prompt.</span></span> <span data-ttu-id="24e19-339">最便利的方式是從「RML CMD 命令提示字元」執行此工具，該工具會當做 RML 公用程式的一部分進行安裝。</span><span class="sxs-lookup"><span data-stu-id="24e19-339">It is most convenient to run the tool from the "RML Cmd Prompt", which is installed as part of the RML Utilities.</span></span>  
  
 <span data-ttu-id="24e19-340">若要開啟 RML CMD 命令提示字元，請遵循下列指示：</span><span class="sxs-lookup"><span data-stu-id="24e19-340">To open the RML Cmd Prompt follow these instructions:</span></span>  
  
 <span data-ttu-id="24e19-341">在 Windows Server 2012 [R2] 以及 Windows 8 和 8.1 中，按一下 Windows 鍵開啟 [開始] 功能表，然後輸入 'rml'。</span><span class="sxs-lookup"><span data-stu-id="24e19-341">In Windows Server 2012 [R2] and in Windows 8 and 8.1, open the start menu by clicking the Windows key, and type 'rml'.</span></span> <span data-ttu-id="24e19-342">按一下搜尋結果清單中的 "RML Cmd Prompt"。</span><span class="sxs-lookup"><span data-stu-id="24e19-342">Click on "RML Cmd Prompt", which will be in the list of search results.</span></span>  
  
 <span data-ttu-id="24e19-343">確定命令提示字元位於 RML 公用程式安裝資料夾中。</span><span class="sxs-lookup"><span data-stu-id="24e19-343">Ensure that the command prompt is located in the RML Utilities installation folder.</span></span> <span data-ttu-id="24e19-344">例如：</span><span class="sxs-lookup"><span data-stu-id="24e19-344">For example:</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP01.jpg)  
  
 <span data-ttu-id="24e19-345">只需執行 ostress.exe 即可顯示 ostress 的命令列選項，而不需要使用任何命令列選項。</span><span class="sxs-lookup"><span data-stu-id="24e19-345">The command-line options for ostress can be seen when simply running ostress.exe without any command-line options.</span></span> <span data-ttu-id="24e19-346">在此範例中執行 ostress 所要考量的主要選項包括：</span><span class="sxs-lookup"><span data-stu-id="24e19-346">The main options to consider for running ostress with this sample are:</span></span>  
  
-   <span data-ttu-id="24e19-347">-S 要連接之 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的名稱</span><span class="sxs-lookup"><span data-stu-id="24e19-347">-S name of [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to</span></span>  
  
-   <span data-ttu-id="24e19-348">-E 使用 Windows 驗證連接 (預設) ;如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請分別使用-您和-P 選項來指定使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="24e19-348">-E use Windows authentication to connect (default); if you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] authentication, use the options -U and -P to specify the username and password, respectively</span></span>  
  
-   <span data-ttu-id="24e19-349">-d：資料庫的名稱，在此範例中為 AdventureWorks2014</span><span class="sxs-lookup"><span data-stu-id="24e19-349">-d name of the database, for this example AdventureWorks2014</span></span>  
  
-   <span data-ttu-id="24e19-350">-Q：要執行的 T-SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="24e19-350">-Q the T-SQL statement to be executed</span></span>  
  
-   <span data-ttu-id="24e19-351">-n：處理每個輸入檔案/查詢的連接數目</span><span class="sxs-lookup"><span data-stu-id="24e19-351">-n number of connections processing each input file/query</span></span>  
  
-   <span data-ttu-id="24e19-352">-r：每個連接執行每個輸入檔案/查詢的反覆運算次數</span><span class="sxs-lookup"><span data-stu-id="24e19-352">-r the number of iterations for each connection to execute each input file/query</span></span>  
  
### <a name="demo-workload"></a><span data-ttu-id="24e19-353">工作負載示範</span><span class="sxs-lookup"><span data-stu-id="24e19-353">Demo Workload</span></span>  
 <span data-ttu-id="24e19-354">工作負載示範中所使用的主要預存程序為 Sales.usp_InsertSalesOrder_inmem/ondisk。</span><span class="sxs-lookup"><span data-stu-id="24e19-354">The main stored procedure used in the demo workload is Sales.usp_InsertSalesOrder_inmem/ondisk.</span></span> <span data-ttu-id="24e19-355">下列指令碼使用範例資料建構資料表值參數 (TVP)，並呼叫程序插入具有 5 個明細項目的銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="24e19-355">The script in the below constructs a table-valued parameter (TVP) with sample data, and calls the procedure to insert a sales order with 5 line items.</span></span>  
  
 <span data-ttu-id="24e19-356">ostress 工具可用來平行執行預存程序呼叫，以模擬同時插入銷售訂單的客戶。</span><span class="sxs-lookup"><span data-stu-id="24e19-356">The ostress tool is used to execute the stored procedure calls in parallel, to simulate clients inserting sales orders concurrently.</span></span>  
  
 <span data-ttu-id="24e19-357">每次壓力執行 Demo.usp_DemoReset 之後，請重設示範。</span><span class="sxs-lookup"><span data-stu-id="24e19-357">Reset the demo after each stress run executing Demo.usp_DemoReset.</span></span> <span data-ttu-id="24e19-358">此程序會刪除記憶體最佳化資料表中的資料列、截斷磁碟資料表，並執行資料庫檢查點。</span><span class="sxs-lookup"><span data-stu-id="24e19-358">This procedure deletes the rows in the memory-optimized tables, truncates the disk-based tables, and executes a database checkpoint.</span></span>  
  
 <span data-ttu-id="24e19-359">下列指令碼會同時執行，以模擬銷售訂單處理工作負載：</span><span class="sxs-lookup"><span data-stu-id="24e19-359">The following script is executed concurrently to simulate a sales order processing workload:</span></span>  
  
```  
DECLARE   
      @i int = 0,   
      @od Sales.SalesOrderDetailType_inmem,   
      @SalesOrderID int,   
      @DueDate datetime2 = sysdatetime(),   
      @CustomerID int = rand() * 8000,   
      @BillToAddressID int = rand() * 10000,   
      @ShipToAddressID int = rand() * 10000,   
      @ShipMethodID int = (rand() * 5) + 1;   
  
INSERT INTO @od   
SELECT OrderQty, ProductID, SpecialOfferID   
FROM Demo.DemoSalesOrderDetailSeed   
WHERE OrderID= cast((rand()*106) + 1 as int);   
  
WHILE (@i < 20)   
BEGIN;   
      EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od;   
      SET @i += 1   
END  
  
```  
  
 <span data-ttu-id="24e19-360">利用此指令碼，每個建構的範例訂單會透過以 WHILE 迴圈執行的 20 個預存程序被插入 20 次。</span><span class="sxs-lookup"><span data-stu-id="24e19-360">With this script, each sample order that is constructed is inserted 20 times, through 20 stored procedures executed in a WHILE loop.</span></span> <span data-ttu-id="24e19-361">此迴圈可用來說明使用資料庫建構範例訂單的情況。</span><span class="sxs-lookup"><span data-stu-id="24e19-361">The loop is used to account for the fact that the database is used to construct the sample order.</span></span> <span data-ttu-id="24e19-362">在一般實際執行環境中，中間層應用程式會建構要插入的銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="24e19-362">In typical production environments, the mid-tier application will construct the sales order to be inserted.</span></span>  
  
 <span data-ttu-id="24e19-363">上述指令碼會將銷售訂單插入記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="24e19-363">The above script inserts sales orders into memory-optimized tables.</span></span> <span data-ttu-id="24e19-364">以 '_ondisk' 取代出現兩次的 '_inmem'，即可衍生將銷售訂單插入磁碟資料表的指令碼。</span><span class="sxs-lookup"><span data-stu-id="24e19-364">The script to insert sales orders into disk-based tables is derived by replacing the two occurrences of '_inmem' with '_ondisk'.</span></span>  
  
 <span data-ttu-id="24e19-365">我們將在數個並行連接下，使用 ostress 工具執行這些指令碼。</span><span class="sxs-lookup"><span data-stu-id="24e19-365">We will use the ostress tool to execute the scripts using several concurrent connections.</span></span> <span data-ttu-id="24e19-366">我們將使用參數 '-n' 來控制連接數目，並使用參數 'r' 來控制每個連接上執行指令碼的次數。</span><span class="sxs-lookup"><span data-stu-id="24e19-366">We will use the parameter '-n' to control the number of connections, and the parameter 'r' to control how many times the script is executed on each connection.</span></span>  
  
#### <a name="functional-validation-of-the-workload"></a><span data-ttu-id="24e19-367">工作負載的功能驗證</span><span class="sxs-lookup"><span data-stu-id="24e19-367">Functional Validation of the Workload</span></span>  
 <span data-ttu-id="24e19-368">若要確認所有專案都能正常運作，我們將從範例測試開始，使用10個並行連接和5次反覆運算，插入總計 10 \* 5 \* 20 = 1000 銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="24e19-368">To verify everything works, we will start with a sample test, using 10 concurrent connects and 5 iterations, inserting a total of 10 \* 5 \* 20 = 1000 sales order.</span></span>  
  
 <span data-ttu-id="24e19-369">在下列命令中，我們假設使用本機電腦上的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="24e19-369">With the below command we assume using the default instance on the local machine.</span></span> <span data-ttu-id="24e19-370">如果您使用具名執行個體或使用遠端伺服器，請使用 -S 參數據以變更伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="24e19-370">If you are using a named instance or using a remote server, change the server name accordingly, using the parameter -S.</span></span>  
  
 <span data-ttu-id="24e19-371">在 RML CMD 命令提示字元中使用下列命令，以在記憶體最佳化資料表中插入 1,000 個銷售訂單：</span><span class="sxs-lookup"><span data-stu-id="24e19-371">Insert 1000 sales orders in memory-optimized tables use the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="24e19-372">按一下 [複製] 按鈕複製命令，然後將其貼入 RML 公用程式命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="24e19-372">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="24e19-373">如果一切如預期運作，您的命令視窗會類似如下。</span><span class="sxs-lookup"><span data-stu-id="24e19-373">If everything works as expected, your command window will look similar to the following.</span></span> <span data-ttu-id="24e19-374">不應該出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="24e19-374">Error messages are not expected.</span></span>  
  
 ![](../../2014/database-engine/media/SQLServer2014RTMIn-MemoryOLTP02.jpg)  
  
 <span data-ttu-id="24e19-375">在 RML CMD 命令提示字元中執行下列命令，以驗證磁碟資料表上的工作負載運作亦如預期：</span><span class="sxs-lookup"><span data-stu-id="24e19-375">Validate that also the workload functions as expected for disk-based tables by running the following command in the RML Cmd Prompt:</span></span>  
  
 <span data-ttu-id="24e19-376">按一下 [複製] 按鈕複製命令，然後將其貼入 RML 公用程式命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="24e19-376">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n10 -r5 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
#### <a name="running-the-workload"></a><span data-ttu-id="24e19-377">執行工作負載</span><span class="sxs-lookup"><span data-stu-id="24e19-377">Running the Workload</span></span>  
 <span data-ttu-id="24e19-378">為了進行規模測試，我們使用 100 個連接插入 1,000 萬個銷售訂單。</span><span class="sxs-lookup"><span data-stu-id="24e19-378">To test at scale we insert 10 million sales orders, using 100 connections.</span></span> <span data-ttu-id="24e19-379">此測試會在適合的伺服器 (例如 8 個實體、16 個邏輯核心) 上適當地執行，並使用基本 SSD 儲存體儲存記錄檔。</span><span class="sxs-lookup"><span data-stu-id="24e19-379">This test performs reasonably on a modest server (e.g., 8 physical, 16 logical cores), and basic SSD storage for the log.</span></span> <span data-ttu-id="24e19-380">如果此測試無法在您的硬體上正常執行，請檢閱 [為執行緩慢的測試疑難排解](#Troubleshootingslow-runningtests)一節。如果您想要降低此測試的壓力程度，請變更參數 '-n' 以減少連線數目。</span><span class="sxs-lookup"><span data-stu-id="24e19-380">If the test does not perform well on your hardware, take look at the Section [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).If you want to reduce the level of stress for this test, lower the number of connections by changing the parameter '-n'.</span></span> <span data-ttu-id="24e19-381">例如，若要將連接計數減少到 40，請將參數 '-n100' 變更為 '-n40'。</span><span class="sxs-lookup"><span data-stu-id="24e19-381">For example to lower the connection count to 40, change the parameter '-n100' to '-n40'.</span></span>  
  
 <span data-ttu-id="24e19-382">我們使用執行工作負載之後由 ostress.exe 報告的經過時間，做為工作負載的效能度量。</span><span class="sxs-lookup"><span data-stu-id="24e19-382">As a performance measure for the workload we use the elapsed time as reported by ostress.exe after running the workload.</span></span>  
  
##### <a name="memory-optimized-tables"></a><span data-ttu-id="24e19-383">記憶體最佳化的資料表</span><span class="sxs-lookup"><span data-stu-id="24e19-383">Memory-optimized tables</span></span>  
 <span data-ttu-id="24e19-384">首先執行記憶體最佳化資料表上的工作負載。</span><span class="sxs-lookup"><span data-stu-id="24e19-384">We will start by running the workload on memory-optimized tables.</span></span> <span data-ttu-id="24e19-385">下列命令會開啟 100 個執行緒，每個執行緒執行 5,000 次反覆運算。</span><span class="sxs-lookup"><span data-stu-id="24e19-385">The following command opens 100 threads, each running for 5,000 iterations.</span></span>  <span data-ttu-id="24e19-386">每次反覆運算會將 20 個銷售訂單插入個別交易。</span><span class="sxs-lookup"><span data-stu-id="24e19-386">Each iteration inserts 20 sales orders in separate transactions.</span></span> <span data-ttu-id="24e19-387">每次反覆運算會插入 20 個訂單，以彌補使用資料庫產生要插入之資料的情況。</span><span class="sxs-lookup"><span data-stu-id="24e19-387">There are 20 inserts per iteration to compensate for the fact that the database is used to generate the data to be inserted.</span></span> <span data-ttu-id="24e19-388">這樣會產生總計 20 \* 5,000 \* 100 = 10,000,000 個銷售訂單的插入。</span><span class="sxs-lookup"><span data-stu-id="24e19-388">This yield a total of 20 \* 5,000 \* 100 = 10,000,000 sales order inserts.</span></span>  
  
 <span data-ttu-id="24e19-389">開啟 RML CMD 命令提示字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="24e19-389">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="24e19-390">按一下 [複製] 按鈕複製命令，然後將其貼入 RML 公用程式命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="24e19-390">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="24e19-391">在具有 8 顆實體 (16 顆邏輯) 核心的測試伺服器上，此作業約需 2 分 5 秒。</span><span class="sxs-lookup"><span data-stu-id="24e19-391">On one test server with a total number of 8 physical (16 logical) cores, this took 2 minutes and 5 seconds.</span></span> <span data-ttu-id="24e19-392">在具有 24 個實體 (48 個邏輯) 核心的第二部測試伺服器上，此作業需要 1 分 0 秒。</span><span class="sxs-lookup"><span data-stu-id="24e19-392">On a second test server with 24 physical (48 logical) cores, this took 1 minute and 0 seconds.</span></span>  
  
 <span data-ttu-id="24e19-393">觀察執行工作負載時的 CPU 使用率，例如使用工作管理員。</span><span class="sxs-lookup"><span data-stu-id="24e19-393">Observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="24e19-394">您會看到 CPU 使用率接近 100%。</span><span class="sxs-lookup"><span data-stu-id="24e19-394">You will see that CPU utilization is close to 100%.</span></span> <span data-ttu-id="24e19-395">如果不是這種情況，則會發生記錄 IO 瓶頸 (也請參閱 [疑難排解執行緩慢的測試](#Troubleshootingslow-runningtests))。</span><span class="sxs-lookup"><span data-stu-id="24e19-395">If this is not the case, you have a log IO bottleneck see also [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).</span></span>  
  
##### <a name="disk-based-tables"></a><span data-ttu-id="24e19-396">磁碟型資料表</span><span class="sxs-lookup"><span data-stu-id="24e19-396">Disk-based tables</span></span>  
 <span data-ttu-id="24e19-397">下列命令會執行磁碟資料表上的工作負載。</span><span class="sxs-lookup"><span data-stu-id="24e19-397">The following command will run the workload on disk-based tables.</span></span> <span data-ttu-id="24e19-398">請注意，執行此工作負載可能需要一些時間，主要是因為系統中發生閂鎖競爭。</span><span class="sxs-lookup"><span data-stu-id="24e19-398">Note that this workload may take a while to execute, which is largely due to latch contention in the system.</span></span> <span data-ttu-id="24e19-399">記憶體最佳化資料表不需閂鎖，因此不會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="24e19-399">Memory-optimized table are latch-free and thus do not suffer from this problem.</span></span>  
  
 <span data-ttu-id="24e19-400">開啟 RML CMD 命令提示字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="24e19-400">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="24e19-401">按一下 [複製] 按鈕複製命令，然後將其貼入 RML 公用程式命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="24e19-401">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2014 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="24e19-402">在具有總數 8 個實體 (16 個邏輯) 核心的測試伺服器上，此作業需要 41 分 25 秒。</span><span class="sxs-lookup"><span data-stu-id="24e19-402">On one test server with a total number of 8 physical (16 logical) cores, this took 41 minutes and 25 seconds.</span></span> <span data-ttu-id="24e19-403">在具有 24 個實體 (48 個邏輯) 核心的第二部測試伺服器上，此作業需要 52 分 16 秒。</span><span class="sxs-lookup"><span data-stu-id="24e19-403">On a second test server with 24 physical (48 logical) cores, this took 52 minutes and 16 seconds.</span></span>  
  
 <span data-ttu-id="24e19-404">在此測試中，記憶體最佳化資料表與磁碟資料表之間出現效能差異的主要因素，是使用磁碟資料表時， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 無法充分運用 CPU。</span><span class="sxs-lookup"><span data-stu-id="24e19-404">The main factor in the performance difference between memory-optimized tables and disk-based tables in this test is the fact that when using disk-based tables, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cannot not fully utilize the CPU.</span></span> <span data-ttu-id="24e19-405">原因在於閂鎖競爭：並行交易嘗試寫入相同的資料頁面，使用閂鎖可確保一次只有一筆交易可以寫入頁面。</span><span class="sxs-lookup"><span data-stu-id="24e19-405">The reason is latch contention: concurrent transactions are attempting to write to the same data page; latches are used to ensure only one transaction at a time can write to a page.</span></span> <span data-ttu-id="24e19-406">[!INCLUDE[hek_2](../includes/hek-2-md.md)] 引擎不需閂鎖，且資料列不是以頁面方式組織。</span><span class="sxs-lookup"><span data-stu-id="24e19-406">The [!INCLUDE[hek_2](../includes/hek-2-md.md)] engine is latch-free, and data rows are not organized in pages.</span></span> <span data-ttu-id="24e19-407">因此，並行交易不會封鎖彼此的插入，因此可讓 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 充分利用 CPU。</span><span class="sxs-lookup"><span data-stu-id="24e19-407">Thus, concurrent transactions do not block each other's inserts, thus enabling [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to fully utilize the CPU.</span></span>  
  
 <span data-ttu-id="24e19-408">您可以觀察執行工作負載時的 CPU 使用率，例如使用工作管理員。</span><span class="sxs-lookup"><span data-stu-id="24e19-408">You can observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="24e19-409">您會看到磁碟資料表的 CPU 使用率遠低於 100%。</span><span class="sxs-lookup"><span data-stu-id="24e19-409">You will see with disk-based tables the CPU utilization is far from 100%.</span></span> <span data-ttu-id="24e19-410">在具有 16 個邏輯處理器的測試組態中，使用率保持在 24% 左右。</span><span class="sxs-lookup"><span data-stu-id="24e19-410">On a test configuration with 16 logical processors, the utilization would hover around 24%.</span></span>  
  
 <span data-ttu-id="24e19-411">或者，您可以使用效能監視器搭配效能計數器 '\SQL Server:Latches\Latch Waits/sec'，檢視每秒的閂鎖等候次數。</span><span class="sxs-lookup"><span data-stu-id="24e19-411">Optionally, you can view the number of latch waits per second using Performance Monitor, with the performance counter '\SQL Server:Latches\Latch Waits/sec'.</span></span>  
  
#### <a name="resetting-the-demo"></a><span data-ttu-id="24e19-412">重設示範</span><span class="sxs-lookup"><span data-stu-id="24e19-412">Resetting the demo</span></span>  
 <span data-ttu-id="24e19-413">若要重設示範，請開啟 RML CMD 命令提示字元，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="24e19-413">To reset the demo, open the RML Cmd Prompt, and execute the following command:</span></span>  
  
```  
ostress.exe -S. -E -dAdventureWorks2014 -Q"EXEC Demo.usp_DemoReset"  
```  
  
 <span data-ttu-id="24e19-414">視硬體而定，此作業可能需要幾分鐘才能執行。</span><span class="sxs-lookup"><span data-stu-id="24e19-414">Depending on the hardware this may take a few minutes to run.</span></span>  
  
 <span data-ttu-id="24e19-415">建議每次執行示範之後將其重設。</span><span class="sxs-lookup"><span data-stu-id="24e19-415">We recommend a reset after every demo run.</span></span> <span data-ttu-id="24e19-416">由於此工作負載只能插入，每次執行會耗用更多記憶體，因此需要重設以防止記憶體不足。</span><span class="sxs-lookup"><span data-stu-id="24e19-416">Because this workload is insert-only, each run will consume more memory, and thus a reset is required to prevent running out of memory.</span></span> <span data-ttu-id="24e19-417">[執行工作負載之後的記憶體使用量](#Memoryutilizationafterrunningtheworkload)章節中會討論執行後的記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="24e19-417">The amount of memory consumed after a run is discussed in Section [Memory utilization after running the workload](#Memoryutilizationafterrunningtheworkload).</span></span>  
  
###  <a name="troubleshooting-slow-running-tests"></a><a name="Troubleshootingslow-runningtests"></a> <span data-ttu-id="24e19-418">為執行緩慢的測試疑難排解</span><span class="sxs-lookup"><span data-stu-id="24e19-418">Troubleshooting slow-running tests</span></span>  
 <span data-ttu-id="24e19-419">測試結果通常會隨硬體而有所不同，也會隨測試執行中使用並行的程度而有所不同。</span><span class="sxs-lookup"><span data-stu-id="24e19-419">Test results will typically vary with hardware, and also the level of concurrency used in the test run.</span></span> <span data-ttu-id="24e19-420">如果結果不如預期，可注意下列幾點：</span><span class="sxs-lookup"><span data-stu-id="24e19-420">A couple of things to look for if the results are not as expected:</span></span>  
  
-   <span data-ttu-id="24e19-421">並行交易數目：在單一執行緒上執行工作負載時，透過 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 提升的效能可能不到兩倍。</span><span class="sxs-lookup"><span data-stu-id="24e19-421">Number of concurrent transactions: When running the workload on a single thread, performance gain with [!INCLUDE[hek_2](../includes/hek-2-md.md)] will likely be less than 2X.</span></span> <span data-ttu-id="24e19-422">只有在高度並行的情況下，閂鎖競爭才會成為嚴重的問題。</span><span class="sxs-lookup"><span data-stu-id="24e19-422">Latch contention is only a big problem if there is a high level of concurrency.</span></span>  
  
-   <span data-ttu-id="24e19-423">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]可用的核心數目很低：這表示系統中的並行程度不高，因為同時執行的交易數目必須與 SQL 可用的核心數目相同。</span><span class="sxs-lookup"><span data-stu-id="24e19-423">Low number of cores available to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]: This means there will be a low level of concurrency in the system, as there can only be as many concurrently executing transactions as there are cores available to SQL.</span></span>  
  
    -   <span data-ttu-id="24e19-424">徵兆：執行磁碟資料表上的工作負載時，如果 CPU 使用率很高，並不是指競爭很多，而是指缺少並行。</span><span class="sxs-lookup"><span data-stu-id="24e19-424">Symptom: if the CPU utilization is high when running the workload on disk-based tables, this means there is not a lot of contention, pointing to a lack of concurrency.</span></span>  
  
-   <span data-ttu-id="24e19-425">記錄磁碟機的速度：如果記錄磁碟機跟不上系統中的交易輸送量層級，則工作負載會在記錄 IO 上成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="24e19-425">Speed of the log drive: If the log drive cannot keep up with the level of transaction throughput in the system, the workload becomes bottlenecked on log IO.</span></span> <span data-ttu-id="24e19-426">雖然 [!INCLUDE[hek_2](../includes/hek-2-md.md)]的記錄效率較高，一旦記錄 IO 成為瓶頸，將會限制可能提升的效能。</span><span class="sxs-lookup"><span data-stu-id="24e19-426">Although logging is more efficient with [!INCLUDE[hek_2](../includes/hek-2-md.md)], if log IO is a bottleneck, the potential performance gain is limited.</span></span>  
  
    -   <span data-ttu-id="24e19-427">徵兆：執行記憶體最佳化資料表上的工作負載時，如果 CPU 使用率離 100% 有段距離或急起急落，可能會發生記錄 IO 瓶頸。</span><span class="sxs-lookup"><span data-stu-id="24e19-427">Symptom: if the CPU utilization is not close to 100% or is very spiky when running the workload on memory-optimized tables, it is possible there is a log IO bottleneck.</span></span> <span data-ttu-id="24e19-428">您可以開啟資源監視器並查看記錄磁碟機的佇列長度，以確認是否發生此瓶頸。</span><span class="sxs-lookup"><span data-stu-id="24e19-428">This can be confirmed by opening Resource Monitor and looking at the queue length for the log drive.</span></span>  
  
##  <a name="memory-and-disk-space-utilization-in-the-sample"></a><a name="MemoryandDiskSpaceUtilizationintheSample"></a> <span data-ttu-id="24e19-429">範例中的記憶體和磁碟空間使用量</span><span class="sxs-lookup"><span data-stu-id="24e19-429">Memory and Disk Space Utilization in the Sample</span></span>  
 <span data-ttu-id="24e19-430">以下將描述範例資料庫之記憶體和磁碟空間使用量的預期結果。</span><span class="sxs-lookup"><span data-stu-id="24e19-430">In the below we describe what to expect in terms of memory and disk space utilization for the sample database.</span></span> <span data-ttu-id="24e19-431">我們也將顯示在具有 16 個邏輯核心的測試伺服器上看到的結果。</span><span class="sxs-lookup"><span data-stu-id="24e19-431">We also show the results we have seen in on a test server with 16 logical cores.</span></span>  
  
###  <a name="memory-utilization-for-the-memory-optimized-tables"></a><a name="Memoryutilizationforthememory-optimizedtables"></a> <span data-ttu-id="24e19-432">記憶體最佳化資料表的記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="24e19-432">Memory utilization for the memory-optimized tables</span></span>  
  
#### <a name="overall-utilization-of-the-database"></a><span data-ttu-id="24e19-433">資料庫的整體使用情況</span><span class="sxs-lookup"><span data-stu-id="24e19-433">Overall utilization of the database</span></span>  
 <span data-ttu-id="24e19-434">下列查詢可用來取得系統中 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 的總記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="24e19-434">The following query can be used to obtain the total memory utilization for [!INCLUDE[hek_2](../includes/hek-2-md.md)] in the system.</span></span>  
  
```  
SELECT type  
   , name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
 <span data-ttu-id="24e19-435">以下是剛建立資料庫之後的快照集：</span><span class="sxs-lookup"><span data-stu-id="24e19-435">Snapshot after the database has just been created:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="24e19-436">**type**</span><span class="sxs-lookup"><span data-stu-id="24e19-436">**type**</span></span>|<span data-ttu-id="24e19-437">**name**</span><span class="sxs-lookup"><span data-stu-id="24e19-437">**name**</span></span>|<span data-ttu-id="24e19-438">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="24e19-438">**pages_MB**</span></span>|  
|<span data-ttu-id="24e19-439">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-439">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-440">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-440">Default</span></span>|<span data-ttu-id="24e19-441">94</span><span class="sxs-lookup"><span data-stu-id="24e19-441">94</span></span>|  
|<span data-ttu-id="24e19-442">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-442">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-443">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="24e19-443">DB_ID_5</span></span>|<span data-ttu-id="24e19-444">877</span><span class="sxs-lookup"><span data-stu-id="24e19-444">877</span></span>|  
|<span data-ttu-id="24e19-445">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-445">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-446">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-446">Default</span></span>|<span data-ttu-id="24e19-447">0</span><span class="sxs-lookup"><span data-stu-id="24e19-447">0</span></span>|  
|<span data-ttu-id="24e19-448">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-448">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-449">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-449">Default</span></span>|<span data-ttu-id="24e19-450">0</span><span class="sxs-lookup"><span data-stu-id="24e19-450">0</span></span>|  
  
 <span data-ttu-id="24e19-451">預設記憶體 Clerk 包含全系統記憶體結構，且規模相對較小。</span><span class="sxs-lookup"><span data-stu-id="24e19-451">The default memory clerks contain system-wide memory structures and are relatively small.</span></span> <span data-ttu-id="24e19-452">使用者資料庫 (在本例中為識別碼 5 的資料庫) 的記憶體 Clerk 約為 900MB。</span><span class="sxs-lookup"><span data-stu-id="24e19-452">The memory clerk for the user database, in this case database with ID 5, is about 900MB.</span></span>  
  
#### <a name="memory-utilization-per-table"></a><span data-ttu-id="24e19-453">每個資料表的記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="24e19-453">Memory utilization per table</span></span>  
 <span data-ttu-id="24e19-454">下列查詢可用來向下鑽研至個別資料表及其索引的記憶體使用量：</span><span class="sxs-lookup"><span data-stu-id="24e19-454">The following query can be used to drill down into the memory utilization of the individual tables and their indexes:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
 <span data-ttu-id="24e19-455">以下顯示範例全新安裝的查詢結果：</span><span class="sxs-lookup"><span data-stu-id="24e19-455">The following shows the results of this query for a fresh installation of the sample:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="24e19-456">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="24e19-456">**Table Name**</span></span>|<span data-ttu-id="24e19-457">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="24e19-457">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="24e19-458">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="24e19-458">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="24e19-459">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-459">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="24e19-460">64</span><span class="sxs-lookup"><span data-stu-id="24e19-460">64</span></span>|<span data-ttu-id="24e19-461">3840</span><span class="sxs-lookup"><span data-stu-id="24e19-461">3840</span></span>|  
|<span data-ttu-id="24e19-462">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="24e19-462">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="24e19-463">1984</span><span class="sxs-lookup"><span data-stu-id="24e19-463">1984</span></span>|<span data-ttu-id="24e19-464">5504</span><span class="sxs-lookup"><span data-stu-id="24e19-464">5504</span></span>|  
|<span data-ttu-id="24e19-465">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-465">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="24e19-466">15316</span><span class="sxs-lookup"><span data-stu-id="24e19-466">15316</span></span>|<span data-ttu-id="24e19-467">663552</span><span class="sxs-lookup"><span data-stu-id="24e19-467">663552</span></span>|  
|<span data-ttu-id="24e19-468">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="24e19-468">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="24e19-469">64</span><span class="sxs-lookup"><span data-stu-id="24e19-469">64</span></span>|<span data-ttu-id="24e19-470">10432</span><span class="sxs-lookup"><span data-stu-id="24e19-470">10432</span></span>|  
|<span data-ttu-id="24e19-471">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-471">SpecialOffer_inmem</span></span>|<span data-ttu-id="24e19-472">3</span><span class="sxs-lookup"><span data-stu-id="24e19-472">3</span></span>|<span data-ttu-id="24e19-473">8192</span><span class="sxs-lookup"><span data-stu-id="24e19-473">8192</span></span>|  
|<span data-ttu-id="24e19-474">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-474">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="24e19-475">7168</span><span class="sxs-lookup"><span data-stu-id="24e19-475">7168</span></span>|<span data-ttu-id="24e19-476">147456</span><span class="sxs-lookup"><span data-stu-id="24e19-476">147456</span></span>|  
|<span data-ttu-id="24e19-477">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-477">Product_inmem</span></span>|<span data-ttu-id="24e19-478">124</span><span class="sxs-lookup"><span data-stu-id="24e19-478">124</span></span>|<span data-ttu-id="24e19-479">12352</span><span class="sxs-lookup"><span data-stu-id="24e19-479">12352</span></span>|  
  
 <span data-ttu-id="24e19-480">如您所見，這些資料表相當小：SalesOrderHeader_inmem 的大小約為 7MB，而 SalesOrderDetail_inmem 的大小約為 15MB。</span><span class="sxs-lookup"><span data-stu-id="24e19-480">As you can see the tables are fairly small: SalesOrderHeader_inmem is about 7MB, and SalesOrderDetail_inmem is about 15MB in size.</span></span>  
  
 <span data-ttu-id="24e19-481">此處值得注意的是，與資料表資料大小相較下，配置給索引的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="24e19-481">What is striking here is the size of the memory allocated for indexes, compared to the size of the table data.</span></span> <span data-ttu-id="24e19-482">這是因為範例中的雜湊索引會預留大小以容納較大的資料。</span><span class="sxs-lookup"><span data-stu-id="24e19-482">That is because the hash indexes in the sample are pre-sized for a larger data size.</span></span> <span data-ttu-id="24e19-483">請注意，雜湊索引有固定的大小，因此其大小不會隨資料表中的資料大小增加。</span><span class="sxs-lookup"><span data-stu-id="24e19-483">Note that hash indexes have a fixed size, and thus their size will not grow with the size of data in the table.</span></span>  
  
####  <a name="memory-utilization-after-running-the-workload"></a><a name="Memoryutilizationafterrunningtheworkload"></a> <span data-ttu-id="24e19-484">執行工作負載之後的記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="24e19-484">Memory utilization after running the workload</span></span>  
 <span data-ttu-id="24e19-485">插入 1,000 萬個銷售訂單之後，總記憶體使用量會類似如下：</span><span class="sxs-lookup"><span data-stu-id="24e19-485">After insert 10 million sales orders, the all-up memory utilization looks similar to the following:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="24e19-486">**type**</span><span class="sxs-lookup"><span data-stu-id="24e19-486">**type**</span></span>|<span data-ttu-id="24e19-487">**name**</span><span class="sxs-lookup"><span data-stu-id="24e19-487">**name**</span></span>|<span data-ttu-id="24e19-488">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="24e19-488">**pages_MB**</span></span>|  
|<span data-ttu-id="24e19-489">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-489">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-490">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-490">Default</span></span>|<span data-ttu-id="24e19-491">146</span><span class="sxs-lookup"><span data-stu-id="24e19-491">146</span></span>|  
|<span data-ttu-id="24e19-492">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-492">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-493">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="24e19-493">DB_ID_5</span></span>|<span data-ttu-id="24e19-494">7374</span><span class="sxs-lookup"><span data-stu-id="24e19-494">7374</span></span>|  
|<span data-ttu-id="24e19-495">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-495">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-496">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-496">Default</span></span>|<span data-ttu-id="24e19-497">0</span><span class="sxs-lookup"><span data-stu-id="24e19-497">0</span></span>|  
|<span data-ttu-id="24e19-498">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-498">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-499">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-499">Default</span></span>|<span data-ttu-id="24e19-500">0</span><span class="sxs-lookup"><span data-stu-id="24e19-500">0</span></span>|  
  
 <span data-ttu-id="24e19-501">如您所見， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 針對範例資料庫中的記憶體最佳化資料表和索引使用小於 8GB 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="24e19-501">As you can see, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is using a bit under 8GB for the memory-optimized tables and indexes in the sample database.</span></span>  
  
 <span data-ttu-id="24e19-502">請在執行一個範例之後，查看每個資料表的詳細記憶體使用量：</span><span class="sxs-lookup"><span data-stu-id="24e19-502">Looking at the detailed memory usage per table after one example run:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="24e19-503">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="24e19-503">**Table Name**</span></span>|<span data-ttu-id="24e19-504">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="24e19-504">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="24e19-505">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="24e19-505">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="24e19-506">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-506">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="24e19-507">5113761</span><span class="sxs-lookup"><span data-stu-id="24e19-507">5113761</span></span>|<span data-ttu-id="24e19-508">663552</span><span class="sxs-lookup"><span data-stu-id="24e19-508">663552</span></span>|  
|<span data-ttu-id="24e19-509">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="24e19-509">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="24e19-510">64</span><span class="sxs-lookup"><span data-stu-id="24e19-510">64</span></span>|<span data-ttu-id="24e19-511">10368</span><span class="sxs-lookup"><span data-stu-id="24e19-511">10368</span></span>|  
|<span data-ttu-id="24e19-512">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-512">SpecialOffer_inmem</span></span>|<span data-ttu-id="24e19-513">2</span><span class="sxs-lookup"><span data-stu-id="24e19-513">2</span></span>|<span data-ttu-id="24e19-514">8192</span><span class="sxs-lookup"><span data-stu-id="24e19-514">8192</span></span>|  
|<span data-ttu-id="24e19-515">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-515">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="24e19-516">1575679</span><span class="sxs-lookup"><span data-stu-id="24e19-516">1575679</span></span>|<span data-ttu-id="24e19-517">147456</span><span class="sxs-lookup"><span data-stu-id="24e19-517">147456</span></span>|  
|<span data-ttu-id="24e19-518">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-518">Product_inmem</span></span>|<span data-ttu-id="24e19-519">111</span><span class="sxs-lookup"><span data-stu-id="24e19-519">111</span></span>|<span data-ttu-id="24e19-520">12032</span><span class="sxs-lookup"><span data-stu-id="24e19-520">12032</span></span>|  
|<span data-ttu-id="24e19-521">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="24e19-521">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="24e19-522">64</span><span class="sxs-lookup"><span data-stu-id="24e19-522">64</span></span>|<span data-ttu-id="24e19-523">3712</span><span class="sxs-lookup"><span data-stu-id="24e19-523">3712</span></span>|  
|<span data-ttu-id="24e19-524">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="24e19-524">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="24e19-525">1984</span><span class="sxs-lookup"><span data-stu-id="24e19-525">1984</span></span>|<span data-ttu-id="24e19-526">5504</span><span class="sxs-lookup"><span data-stu-id="24e19-526">5504</span></span>|  
  
 <span data-ttu-id="24e19-527">我們會看到總計約 6.5GB 的資料。</span><span class="sxs-lookup"><span data-stu-id="24e19-527">We can see a total of about 6.5GB of data.</span></span> <span data-ttu-id="24e19-528">請注意，資料表 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 上的索引大小，與插入銷售訂單之前的索引大小相同。</span><span class="sxs-lookup"><span data-stu-id="24e19-528">Notice that the size of the indexes on the table SalesOrderHeader_inmem and SalesOrderDetail_inmem is the same as the size of the indexes before inserting the sales orders.</span></span> <span data-ttu-id="24e19-529">由於這兩個資料表使用雜湊索引，而雜湊索引是靜態的，因此索引大小不會改變。</span><span class="sxs-lookup"><span data-stu-id="24e19-529">The index size did not change because both tables are using hash indexes, and hash indexes are static.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="24e19-530">重設示範之後</span><span class="sxs-lookup"><span data-stu-id="24e19-530">After demo reset</span></span>  
 <span data-ttu-id="24e19-531">您可以使用預存程序 Demo.usp_DemoReset 重設示範。</span><span class="sxs-lookup"><span data-stu-id="24e19-531">The stored procedure Demo.usp_DemoReset can be used to reset the demo.</span></span> <span data-ttu-id="24e19-532">此預存程序會刪除資料表 SalesOrderHeader_inmem 和 SalesOrderDetail_inmem 中的資料，然後重新植入原始資料表 SalesOrderHeader 和 SalesOrderDetail 中的資料。</span><span class="sxs-lookup"><span data-stu-id="24e19-532">It deletes the data in the tables SalesOrderHeader_inmem and SalesOrderDetail_inmem, and re-seeds the data from the original tables SalesOrderHeader and SalesOrderDetail.</span></span>  
  
 <span data-ttu-id="24e19-533">現在，即使已刪除資料表中的資料列，也不表示會立即回收記憶體。</span><span class="sxs-lookup"><span data-stu-id="24e19-533">Now, even though the rows in the tables have been deleted, this does not mean that memory is reclaimed immediately.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="24e19-534">會視需要在背景回收記憶體最佳化資料表中已刪除資料列的記憶體。</span><span class="sxs-lookup"><span data-stu-id="24e19-534">reclaims memory from deleted rows in memory-optimized tables in the background, as needed.</span></span> <span data-ttu-id="24e19-535">由於系統上沒有交易式工作負載，因此重設示範之後，您會立即看到系統尚未對已刪除的資料列進行記憶體回收：</span><span class="sxs-lookup"><span data-stu-id="24e19-535">You will see that immediately after demo reset, with no transactional workload on the system, memory from deleted rows is not yet reclaimed:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="24e19-536">**type**</span><span class="sxs-lookup"><span data-stu-id="24e19-536">**type**</span></span>|<span data-ttu-id="24e19-537">**name**</span><span class="sxs-lookup"><span data-stu-id="24e19-537">**name**</span></span>|<span data-ttu-id="24e19-538">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="24e19-538">**pages_MB**</span></span>|  
|<span data-ttu-id="24e19-539">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-539">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-540">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-540">Default</span></span>|<span data-ttu-id="24e19-541">2261</span><span class="sxs-lookup"><span data-stu-id="24e19-541">2261</span></span>|  
|<span data-ttu-id="24e19-542">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-542">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-543">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="24e19-543">DB_ID_5</span></span>|<span data-ttu-id="24e19-544">7396</span><span class="sxs-lookup"><span data-stu-id="24e19-544">7396</span></span>|  
|<span data-ttu-id="24e19-545">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-545">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-546">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-546">Default</span></span>|<span data-ttu-id="24e19-547">0</span><span class="sxs-lookup"><span data-stu-id="24e19-547">0</span></span>|  
|<span data-ttu-id="24e19-548">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-548">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-549">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-549">Default</span></span>|<span data-ttu-id="24e19-550">0</span><span class="sxs-lookup"><span data-stu-id="24e19-550">0</span></span>|  
  
 <span data-ttu-id="24e19-551">這是預期的結果：當交易式工作負載執行時，才會回收記憶體。</span><span class="sxs-lookup"><span data-stu-id="24e19-551">This is expected: memory will be reclaimed when the transactional workload is running.</span></span>  
  
 <span data-ttu-id="24e19-552">如果您開始執行第二次工作負載示範，一開始會看到記憶體使用量減少，這是由於之前刪除的資料列遭到清除所致。</span><span class="sxs-lookup"><span data-stu-id="24e19-552">If you start a second run of the demo workload you will see the memory utilization decrease initially, as the previously deleted rows are cleaned up.</span></span> <span data-ttu-id="24e19-553">在工作負載完成之前，記憶體大小會在某些時候再次增加。</span><span class="sxs-lookup"><span data-stu-id="24e19-553">At some point the memory size will increase again, until the workload finishes.</span></span> <span data-ttu-id="24e19-554">重設示範並插入 1,000 萬個資料列之後，記憶體使用量與第一次執行之後的使用量非常相似。</span><span class="sxs-lookup"><span data-stu-id="24e19-554">After inserting 10 million rows after demo reset, the memory utilization will be very similar to the utilization after the first run.</span></span> <span data-ttu-id="24e19-555">例如：</span><span class="sxs-lookup"><span data-stu-id="24e19-555">For example:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="24e19-556">**type**</span><span class="sxs-lookup"><span data-stu-id="24e19-556">**type**</span></span>|<span data-ttu-id="24e19-557">**name**</span><span class="sxs-lookup"><span data-stu-id="24e19-557">**name**</span></span>|<span data-ttu-id="24e19-558">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="24e19-558">**pages_MB**</span></span>|  
|<span data-ttu-id="24e19-559">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-559">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-560">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-560">Default</span></span>|<span data-ttu-id="24e19-561">1863</span><span class="sxs-lookup"><span data-stu-id="24e19-561">1863</span></span>|  
|<span data-ttu-id="24e19-562">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-562">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-563">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="24e19-563">DB_ID_5</span></span>|<span data-ttu-id="24e19-564">7390</span><span class="sxs-lookup"><span data-stu-id="24e19-564">7390</span></span>|  
|<span data-ttu-id="24e19-565">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-565">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-566">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-566">Default</span></span>|<span data-ttu-id="24e19-567">0</span><span class="sxs-lookup"><span data-stu-id="24e19-567">0</span></span>|  
|<span data-ttu-id="24e19-568">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="24e19-568">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="24e19-569">預設</span><span class="sxs-lookup"><span data-stu-id="24e19-569">Default</span></span>|<span data-ttu-id="24e19-570">0</span><span class="sxs-lookup"><span data-stu-id="24e19-570">0</span></span>|  
  
### <a name="disk-utilization-for-memory-optimized-tables"></a><span data-ttu-id="24e19-571">記憶體最佳化資料表的磁碟使用狀況</span><span class="sxs-lookup"><span data-stu-id="24e19-571">Disk utilization for memory-optimized tables</span></span>  
 <span data-ttu-id="24e19-572">您可以使用下列查詢，找到給定時間下，資料庫的檢查點檔案在磁碟上的整體大小：</span><span class="sxs-lookup"><span data-stu-id="24e19-572">The overall on-disk size for the checkpoint files of a database at a given time can be found using the query:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
  
```  
  
#### <a name="initial-state"></a><span data-ttu-id="24e19-573">初始狀態</span><span class="sxs-lookup"><span data-stu-id="24e19-573">Initial state</span></span>  
 <span data-ttu-id="24e19-574">一開始建立範例檔案群組和範例記憶體最佳化資料表時，會預先建立許多檢查點檔案，然後系統會開始填入檔案 (預先建立的檢查點檔案數目取決於系統中的邏輯處理器數目)。</span><span class="sxs-lookup"><span data-stu-id="24e19-574">When the sample filegroup and sample memory-optimized tables are created initially, a number of checkpoint files are pre-created and the system starts filling the files - the number of checkpoint files pre-created depends on the number of logical processors in the system.</span></span> <span data-ttu-id="24e19-575">由於範例一開始非常小，因此預先建立的檔案在初始建立之後，大部分都是空的。</span><span class="sxs-lookup"><span data-stu-id="24e19-575">As the sample is initially very small, the pre-created files will be mostly empty after initial create.</span></span>  
  
 <span data-ttu-id="24e19-576">以下顯示具有 16 個邏輯處理器的機器上之範例在磁碟上的初始大小：</span><span class="sxs-lookup"><span data-stu-id="24e19-576">The following shows the initial on-disk size for the sample on a machine with 16 logical processors:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="24e19-577">**在磁碟上的大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="24e19-577">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="24e19-578">2312</span><span class="sxs-lookup"><span data-stu-id="24e19-578">2312</span></span>|  
  
 <span data-ttu-id="24e19-579">如您所見，檢查點檔案在磁碟上的大小與實際資料大小差距懸殊，磁碟上的大小是 2.3GB，而實際資料大小則接近 30MB。</span><span class="sxs-lookup"><span data-stu-id="24e19-579">As you can see, there is a big discrepancy between the on-disk size of the checkpoint files, which is 2.3GB, and the actual data size, which is closer to 30MB.</span></span>  
  
 <span data-ttu-id="24e19-580">您可以使用下列查詢，更仔細地查看磁碟空間的使用來源。</span><span class="sxs-lookup"><span data-stu-id="24e19-580">Looking closer at where the disk-space utilization comes from, you can use the following query.</span></span> <span data-ttu-id="24e19-581">這個查詢傳回的磁碟大小近似於狀態 5 (REQUIRED FOR BACKUP/HA)、6 (IN TRANSITION TO TOMBSTONE) 或 7 (TOMBSTONE) 的檔案。</span><span class="sxs-lookup"><span data-stu-id="24e19-581">The size on disk returned by this query is approximate for files with state in 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE), or 7 (TOMBSTONE).</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
 <span data-ttu-id="24e19-582">初始狀態的範例結果，與具有 16 個邏輯處理器的伺服器相似：</span><span class="sxs-lookup"><span data-stu-id="24e19-582">For the initial state of the sample, the result will look something like for a server with 16 logical processors:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="24e19-583">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-583">**state_desc**</span></span>|<span data-ttu-id="24e19-584">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-584">**file_type_desc**</span></span>|<span data-ttu-id="24e19-585">**計數**</span><span class="sxs-lookup"><span data-stu-id="24e19-585">**count**</span></span>|<span data-ttu-id="24e19-586">**在磁碟上的大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="24e19-586">**on-disk size MB**</span></span>|  
|<span data-ttu-id="24e19-587">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-587">PRECREATED</span></span>|<span data-ttu-id="24e19-588">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-588">DATA</span></span>|<span data-ttu-id="24e19-589">16</span><span class="sxs-lookup"><span data-stu-id="24e19-589">16</span></span>|<span data-ttu-id="24e19-590">2048</span><span class="sxs-lookup"><span data-stu-id="24e19-590">2048</span></span>|  
|<span data-ttu-id="24e19-591">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-591">PRECREATED</span></span>|<span data-ttu-id="24e19-592">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-592">DELTA</span></span>|<span data-ttu-id="24e19-593">16</span><span class="sxs-lookup"><span data-stu-id="24e19-593">16</span></span>|<span data-ttu-id="24e19-594">128</span><span class="sxs-lookup"><span data-stu-id="24e19-594">128</span></span>|  
|<span data-ttu-id="24e19-595">建構中</span><span class="sxs-lookup"><span data-stu-id="24e19-595">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="24e19-596">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-596">DATA</span></span>|<span data-ttu-id="24e19-597">1</span><span class="sxs-lookup"><span data-stu-id="24e19-597">1</span></span>|<span data-ttu-id="24e19-598">128</span><span class="sxs-lookup"><span data-stu-id="24e19-598">128</span></span>|  
|<span data-ttu-id="24e19-599">建構中</span><span class="sxs-lookup"><span data-stu-id="24e19-599">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="24e19-600">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-600">DELTA</span></span>|<span data-ttu-id="24e19-601">1</span><span class="sxs-lookup"><span data-stu-id="24e19-601">1</span></span>|<span data-ttu-id="24e19-602">8</span><span class="sxs-lookup"><span data-stu-id="24e19-602">8</span></span>|  
  
 <span data-ttu-id="24e19-603">如您所見，預先建立的資料和差異檔案使用了大部分空間。</span><span class="sxs-lookup"><span data-stu-id="24e19-603">As you can see, most of the space is used by precreated data and delta files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="24e19-604">會針對每個邏輯處理器預先建立一組 (資料和差異) 檔案。</span><span class="sxs-lookup"><span data-stu-id="24e19-604">pre-created one pair of (data, delta) files per logical processor.</span></span> <span data-ttu-id="24e19-605">此外，系統會為資料檔案預留 128MB 的大小，並為差異檔案預留 8MB 的大小，以便更有效率地將資料插入這些檔案。</span><span class="sxs-lookup"><span data-stu-id="24e19-605">In addition, data files are pre-sized at 128MB, and delta files at 8MB, in order to make inserting data into these files more efficient.</span></span>  
  
 <span data-ttu-id="24e19-606">記憶體最佳化資料表中的實際資料會包含在單一資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="24e19-606">The actual data in the memory-optimized tables is in the single data file.</span></span>  
  
#### <a name="after-running-the-workload"></a><span data-ttu-id="24e19-607">執行工作負載之後</span><span class="sxs-lookup"><span data-stu-id="24e19-607">After running the workload</span></span>  
 <span data-ttu-id="24e19-608">完成插入 1,000 萬個銷售訂單的單一測試執行之後，磁碟上的整體大小會類似如下 (16 個核心測試伺服器)：</span><span class="sxs-lookup"><span data-stu-id="24e19-608">After a single test run that inserts 10 million sales orders, the overall on-disk size looks something like this (for a 16-core test server):</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="24e19-609">**在磁碟上的大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="24e19-609">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="24e19-610">8828</span><span class="sxs-lookup"><span data-stu-id="24e19-610">8828</span></span>|  
  
 <span data-ttu-id="24e19-611">在磁碟上的大小接近 9GB，與記憶體中的資料大小更接近。</span><span class="sxs-lookup"><span data-stu-id="24e19-611">The on-disk size is close to 9GB, which comes close to the in-memory size of the data.</span></span>  
  
 <span data-ttu-id="24e19-612">請更仔細地查看不同狀態的檢查點檔案大小：</span><span class="sxs-lookup"><span data-stu-id="24e19-612">Looking more closely at the sizes of the checkpoint files across the various states:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="24e19-613">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-613">**state_desc**</span></span>|<span data-ttu-id="24e19-614">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-614">**file_type_desc**</span></span>|<span data-ttu-id="24e19-615">**計數**</span><span class="sxs-lookup"><span data-stu-id="24e19-615">**count**</span></span>|<span data-ttu-id="24e19-616">**在磁碟上的大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="24e19-616">**on-disk size MB**</span></span>|  
|<span data-ttu-id="24e19-617">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-617">PRECREATED</span></span>|<span data-ttu-id="24e19-618">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-618">DATA</span></span>|<span data-ttu-id="24e19-619">16</span><span class="sxs-lookup"><span data-stu-id="24e19-619">16</span></span>|<span data-ttu-id="24e19-620">2048</span><span class="sxs-lookup"><span data-stu-id="24e19-620">2048</span></span>|  
|<span data-ttu-id="24e19-621">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-621">PRECREATED</span></span>|<span data-ttu-id="24e19-622">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-622">DELTA</span></span>|<span data-ttu-id="24e19-623">16</span><span class="sxs-lookup"><span data-stu-id="24e19-623">16</span></span>|<span data-ttu-id="24e19-624">128</span><span class="sxs-lookup"><span data-stu-id="24e19-624">128</span></span>|  
|<span data-ttu-id="24e19-625">建構中</span><span class="sxs-lookup"><span data-stu-id="24e19-625">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="24e19-626">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-626">DATA</span></span>|<span data-ttu-id="24e19-627">1</span><span class="sxs-lookup"><span data-stu-id="24e19-627">1</span></span>|<span data-ttu-id="24e19-628">128</span><span class="sxs-lookup"><span data-stu-id="24e19-628">128</span></span>|  
|<span data-ttu-id="24e19-629">建構中</span><span class="sxs-lookup"><span data-stu-id="24e19-629">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="24e19-630">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-630">DELTA</span></span>|<span data-ttu-id="24e19-631">1</span><span class="sxs-lookup"><span data-stu-id="24e19-631">1</span></span>|<span data-ttu-id="24e19-632">8</span><span class="sxs-lookup"><span data-stu-id="24e19-632">8</span></span>|  
  
 <span data-ttu-id="24e19-633">我們還有 16 組預先建立的檔案，準備在關閉檢查點之後填入。</span><span class="sxs-lookup"><span data-stu-id="24e19-633">We still have 16 pairs of pre-created files, ready to go as checkpoints are closed.</span></span>  
  
 <span data-ttu-id="24e19-634">以及一組建構中的檔案，會在關閉目前的檢查點之前使用。</span><span class="sxs-lookup"><span data-stu-id="24e19-634">There is one pair under construction, which is used until the current checkpoint is closed.</span></span> <span data-ttu-id="24e19-635">連同使用中的檢查點檔案，記憶體中 6.5GB 資料的磁碟空間使用量約為 6.5GB。</span><span class="sxs-lookup"><span data-stu-id="24e19-635">Along with the active checkpoint files this gives about 6.5GB of disk utilization for 6.5GB of data in memory.</span></span> <span data-ttu-id="24e19-636">請注意，索引不會保存在磁碟上，因此在本例中，磁碟上的整體大小會小於記憶體中的大小。</span><span class="sxs-lookup"><span data-stu-id="24e19-636">Recall that indexes are not persisted on disk, and thus the overall size on disk is smaller than the size in memory in this case.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="24e19-637">重設示範之後</span><span class="sxs-lookup"><span data-stu-id="24e19-637">After demo reset</span></span>  
 <span data-ttu-id="24e19-638">重設示範之後，如果系統上沒有交易式工作負載，且沒有資料庫檢查點，則不會立即回收磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="24e19-638">After demo reset, disk space is not reclaimed immediately if there is no transactional workload on the system, and there are not database checkpoints.</span></span> <span data-ttu-id="24e19-639">對於要在各階段移動並在最後捨棄的檢查點檔案而言，需要發生一些檢查點和記錄截斷事件，才會開始合併檢查點檔案，並開始進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="24e19-639">For checkpoint files to be moved through their various stages and eventually be discarded, a number of checkpoints and log truncation events need to happen, to initiate merge of checkpoint files, as well as to initiate garbage collection.</span></span> <span data-ttu-id="24e19-640">如果系統中有交易式工作負載，則會自動發生這些事件 (如果使用完整復原模式，則需要定期備份記錄)，但是當系統閒置時，不會發生這些事件 (如示範情況所示)。</span><span class="sxs-lookup"><span data-stu-id="24e19-640">These will happen automatically if you have a transactional workload in the system [and take regular log backups, in case you are using the FULL recovery model], but not when the system is idle, as in a demo scenario.</span></span>  
  
 <span data-ttu-id="24e19-641">在此範例中，您會在重設示範之後看到類似如下的情況：</span><span class="sxs-lookup"><span data-stu-id="24e19-641">In the example, after demo reset, you may see something like</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="24e19-642">**在磁碟上的大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="24e19-642">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="24e19-643">11839</span><span class="sxs-lookup"><span data-stu-id="24e19-643">11839</span></span>|  
  
 <span data-ttu-id="24e19-644">接近 12GB，明顯大於重設示範之前的 9GB。</span><span class="sxs-lookup"><span data-stu-id="24e19-644">At nearly 12GB, this is significantly more than the 9GB we had before the demo reset.</span></span> <span data-ttu-id="24e19-645">這是因為已開始合併某些檢查點檔案，但尚未安裝部分合併目標，且尚未清除部分合併來源檔案 (如下所示)：</span><span class="sxs-lookup"><span data-stu-id="24e19-645">This is because some checkpoint file merges have been started, but some of the merge targets have not yet been installed, and some of the merge source files have not yet been cleaned up, as can be seen from the following:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="24e19-646">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-646">**state_desc**</span></span>|<span data-ttu-id="24e19-647">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-647">**file_type_desc**</span></span>|<span data-ttu-id="24e19-648">**計數**</span><span class="sxs-lookup"><span data-stu-id="24e19-648">**count**</span></span>|<span data-ttu-id="24e19-649">**在磁碟上的大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="24e19-649">**on-disk size MB**</span></span>|  
|<span data-ttu-id="24e19-650">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-650">PRECREATED</span></span>|<span data-ttu-id="24e19-651">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-651">DATA</span></span>|<span data-ttu-id="24e19-652">16</span><span class="sxs-lookup"><span data-stu-id="24e19-652">16</span></span>|<span data-ttu-id="24e19-653">2048</span><span class="sxs-lookup"><span data-stu-id="24e19-653">2048</span></span>|  
|<span data-ttu-id="24e19-654">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-654">PRECREATED</span></span>|<span data-ttu-id="24e19-655">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-655">DELTA</span></span>|<span data-ttu-id="24e19-656">16</span><span class="sxs-lookup"><span data-stu-id="24e19-656">16</span></span>|<span data-ttu-id="24e19-657">128</span><span class="sxs-lookup"><span data-stu-id="24e19-657">128</span></span>|  
|<span data-ttu-id="24e19-658">使用中</span><span class="sxs-lookup"><span data-stu-id="24e19-658">ACTIVE</span></span>|<span data-ttu-id="24e19-659">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-659">DATA</span></span>|<span data-ttu-id="24e19-660">38</span><span class="sxs-lookup"><span data-stu-id="24e19-660">38</span></span>|<span data-ttu-id="24e19-661">5152</span><span class="sxs-lookup"><span data-stu-id="24e19-661">5152</span></span>|  
|<span data-ttu-id="24e19-662">使用中</span><span class="sxs-lookup"><span data-stu-id="24e19-662">ACTIVE</span></span>|<span data-ttu-id="24e19-663">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-663">DELTA</span></span>|<span data-ttu-id="24e19-664">38</span><span class="sxs-lookup"><span data-stu-id="24e19-664">38</span></span>|<span data-ttu-id="24e19-665">1331</span><span class="sxs-lookup"><span data-stu-id="24e19-665">1331</span></span>|  
|<span data-ttu-id="24e19-666">合併目標</span><span class="sxs-lookup"><span data-stu-id="24e19-666">MERGE TARGET</span></span>|<span data-ttu-id="24e19-667">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-667">DATA</span></span>|<span data-ttu-id="24e19-668">7</span><span class="sxs-lookup"><span data-stu-id="24e19-668">7</span></span>|<span data-ttu-id="24e19-669">896</span><span class="sxs-lookup"><span data-stu-id="24e19-669">896</span></span>|  
|<span data-ttu-id="24e19-670">合併目標</span><span class="sxs-lookup"><span data-stu-id="24e19-670">MERGE TARGET</span></span>|<span data-ttu-id="24e19-671">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-671">DELTA</span></span>|<span data-ttu-id="24e19-672">7</span><span class="sxs-lookup"><span data-stu-id="24e19-672">7</span></span>|<span data-ttu-id="24e19-673">56</span><span class="sxs-lookup"><span data-stu-id="24e19-673">56</span></span>|  
|<span data-ttu-id="24e19-674">已合併來源</span><span class="sxs-lookup"><span data-stu-id="24e19-674">MERGED SOURCE</span></span>|<span data-ttu-id="24e19-675">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-675">DATA</span></span>|<span data-ttu-id="24e19-676">13</span><span class="sxs-lookup"><span data-stu-id="24e19-676">13</span></span>|<span data-ttu-id="24e19-677">1772</span><span class="sxs-lookup"><span data-stu-id="24e19-677">1772</span></span>|  
|<span data-ttu-id="24e19-678">已合併來源</span><span class="sxs-lookup"><span data-stu-id="24e19-678">MERGED SOURCE</span></span>|<span data-ttu-id="24e19-679">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-679">DELTA</span></span>|<span data-ttu-id="24e19-680">13</span><span class="sxs-lookup"><span data-stu-id="24e19-680">13</span></span>|<span data-ttu-id="24e19-681">455</span><span class="sxs-lookup"><span data-stu-id="24e19-681">455</span></span>|  
  
 <span data-ttu-id="24e19-682">由於系統中發生交易活動，因此已安裝合併目標並清除已合併來源。</span><span class="sxs-lookup"><span data-stu-id="24e19-682">Merge targets are installed and merged source are cleaned up as transactional activity happens in the system.</span></span>  
  
 <span data-ttu-id="24e19-683">重設示範並在第二次執行工作負載示範時插入 1,000 萬個銷售訂單之後，您會看到第一次執行工作負載期間所建構的檔案已遭到清除。</span><span class="sxs-lookup"><span data-stu-id="24e19-683">After a second run of the demo workload, inserting 10 million sales orders after the demo reset, you will see that the files constructed during the first run of the workload have been cleaned up.</span></span> <span data-ttu-id="24e19-684">如果您在工作負載執行期間執行數次上述查詢，便會看到檢查點檔案度過各個階段。</span><span class="sxs-lookup"><span data-stu-id="24e19-684">If you run the above query several times while the workload is running, you can see the checkpoint files make their way through the various stages.</span></span>  
  
 <span data-ttu-id="24e19-685">第二次執行工作負載並插入 1,000 萬個銷售訂單之後，您會看到磁碟使用狀況與第一次執行之後的磁碟使用狀況很相似，但不一定相同 (因為系統在本質上是動態的)。</span><span class="sxs-lookup"><span data-stu-id="24e19-685">After the second run of the workload insert 10 million sales orders you will see disk utilization very similar to, though not necessarily the same as after the first run, as the system is dynamic in nature.</span></span> <span data-ttu-id="24e19-686">例如：</span><span class="sxs-lookup"><span data-stu-id="24e19-686">For example:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="24e19-687">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-687">**state_desc**</span></span>|<span data-ttu-id="24e19-688">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="24e19-688">**file_type_desc**</span></span>|<span data-ttu-id="24e19-689">**計數**</span><span class="sxs-lookup"><span data-stu-id="24e19-689">**count**</span></span>|<span data-ttu-id="24e19-690">**在磁碟上的大小 (MB)**</span><span class="sxs-lookup"><span data-stu-id="24e19-690">**on-disk size MB**</span></span>|  
|<span data-ttu-id="24e19-691">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-691">PRECREATED</span></span>|<span data-ttu-id="24e19-692">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-692">DATA</span></span>|<span data-ttu-id="24e19-693">16</span><span class="sxs-lookup"><span data-stu-id="24e19-693">16</span></span>|<span data-ttu-id="24e19-694">2048</span><span class="sxs-lookup"><span data-stu-id="24e19-694">2048</span></span>|  
|<span data-ttu-id="24e19-695">已預先建立</span><span class="sxs-lookup"><span data-stu-id="24e19-695">PRECREATED</span></span>|<span data-ttu-id="24e19-696">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-696">DELTA</span></span>|<span data-ttu-id="24e19-697">16</span><span class="sxs-lookup"><span data-stu-id="24e19-697">16</span></span>|<span data-ttu-id="24e19-698">128</span><span class="sxs-lookup"><span data-stu-id="24e19-698">128</span></span>|  
|<span data-ttu-id="24e19-699">建構中</span><span class="sxs-lookup"><span data-stu-id="24e19-699">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="24e19-700">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-700">DATA</span></span>|<span data-ttu-id="24e19-701">2</span><span class="sxs-lookup"><span data-stu-id="24e19-701">2</span></span>|<span data-ttu-id="24e19-702">268</span><span class="sxs-lookup"><span data-stu-id="24e19-702">268</span></span>|  
|<span data-ttu-id="24e19-703">建構中</span><span class="sxs-lookup"><span data-stu-id="24e19-703">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="24e19-704">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-704">DELTA</span></span>|<span data-ttu-id="24e19-705">2</span><span class="sxs-lookup"><span data-stu-id="24e19-705">2</span></span>|<span data-ttu-id="24e19-706">16</span><span class="sxs-lookup"><span data-stu-id="24e19-706">16</span></span>|  
|<span data-ttu-id="24e19-707">使用中</span><span class="sxs-lookup"><span data-stu-id="24e19-707">ACTIVE</span></span>|<span data-ttu-id="24e19-708">DATA</span><span class="sxs-lookup"><span data-stu-id="24e19-708">DATA</span></span>|<span data-ttu-id="24e19-709">41</span><span class="sxs-lookup"><span data-stu-id="24e19-709">41</span></span>|<span data-ttu-id="24e19-710">5608</span><span class="sxs-lookup"><span data-stu-id="24e19-710">5608</span></span>|  
|<span data-ttu-id="24e19-711">使用中</span><span class="sxs-lookup"><span data-stu-id="24e19-711">ACTIVE</span></span>|<span data-ttu-id="24e19-712">DELTA</span><span class="sxs-lookup"><span data-stu-id="24e19-712">DELTA</span></span>|<span data-ttu-id="24e19-713">41</span><span class="sxs-lookup"><span data-stu-id="24e19-713">41</span></span>|<span data-ttu-id="24e19-714">328</span><span class="sxs-lookup"><span data-stu-id="24e19-714">328</span></span>|  
  
 <span data-ttu-id="24e19-715">在本例中，有兩個檢查點檔案組在「建構中」狀態，這表示多組檔案已移至「建構中」狀態，這可能是由於工作負載中有高度並行所致。</span><span class="sxs-lookup"><span data-stu-id="24e19-715">In this case, there are two checkpoint file pairs in the 'under construction' state, which means multiple file pairs were moved to the 'under construction' state, likely due to the high level of concurrency in the workload.</span></span> <span data-ttu-id="24e19-716">多個並行執行緒會同時要求一個新的檔案組，因此會將一組檔案從「已預先建立」移至「建構中」。</span><span class="sxs-lookup"><span data-stu-id="24e19-716">Multiple concurrent threads required a new file pair at the same time, and thus moved a pair from 'precreated' to 'under construction'.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e19-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24e19-717">See Also</span></span>  
 [<span data-ttu-id="24e19-718">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="24e19-718">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
