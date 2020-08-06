---
title: 記憶體內部 OLTP 的 SQL Server Management Studio 支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ee847b5f-6a1a-448e-a746-d61a023881ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 644ba0cfdbe2f0043364c633676bbc536c641efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585393"
---
# <a name="sql-server-management-studio-support-for-in-memory-oltp"></a><span data-ttu-id="8b48b-102">SQL Server Management Studio 對記憶體中 OLTP 的支援</span><span class="sxs-lookup"><span data-stu-id="8b48b-102">SQL Server Management Studio Support for In-Memory OLTP</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8b48b-103">是用於管理您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 基礎結構的整合式環境。</span><span class="sxs-lookup"><span data-stu-id="8b48b-103">is an integrated environment for managing your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8b48b-104">提供工具來設定、監視以及管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="8b48b-104">provides tools to configure, monitor, and administer instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8b48b-105">如需詳細資訊，請參閱 [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)</span><span class="sxs-lookup"><span data-stu-id="8b48b-105">For more information, see [SQL Server Management Studio](../../ssms/sql-server-management-studio-ssms.md)</span></span>  
  
 <span data-ttu-id="8b48b-106">本主題中的工作描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 管理記憶體最佳化資料表、記憶體最佳化資料表上的索引、原生編譯預存程序，以及使用者定義的記憶體最佳化資料表類型。</span><span class="sxs-lookup"><span data-stu-id="8b48b-106">The tasks in this topic describe how to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage memory-optimized tables; indexes on memory-optimized tables; natively compiled stored procedures; and user-defined, memory-optimized table types.</span></span>  
  
 <span data-ttu-id="8b48b-107">如需有關如何以程式設計方式建立記憶體最佳化資料表的詳細資訊，請參閱 [建立記憶體最佳化資料表和原生編譯的預存程序](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="8b48b-107">For information on how to programmatically create memory-optimized tables, see [Creating a Memory-Optimized Table and a Natively Compiled Stored Procedure](creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-database-with-a-memory-optimized-data-filegroup"></a><span data-ttu-id="8b48b-108">若要建立具有記憶體最佳化資料檔案群組的資料庫</span><span class="sxs-lookup"><span data-stu-id="8b48b-108">To create a database with a memory-optimized data filegroup</span></span>  
  
1.  <span data-ttu-id="8b48b-109">在 [物件總管] 中，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="8b48b-109">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="8b48b-110">以滑鼠右鍵按一下 [資料庫]，然後按一下 [新增資料庫]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-110">Right-click **Databases**, and then click **New Database**.</span></span>  
  
3.  <span data-ttu-id="8b48b-111">請按一下 [檔案群組] 頁面，以新增記憶體最佳化的資料檔案群組。</span><span class="sxs-lookup"><span data-stu-id="8b48b-111">To add a new memory-optimized data filegroup, click the **Filegroups** page.</span></span> <span data-ttu-id="8b48b-112">在 [記憶體最佳化資料] 下，按一下 [新增檔案群組]，然後輸入記憶體最佳化資料檔案群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="8b48b-112">Under **MEMORY OPTIMIZED DATA**, click **Add filegroup** and then enter the name of the memory-optimized data filegroup.</span></span>  <span data-ttu-id="8b48b-113">標示為 [FILESTREAM 檔案] 的欄代表檔案群組中的容器數目。</span><span class="sxs-lookup"><span data-stu-id="8b48b-113">The column labeled **FILESTREAM Files** represents the number of containers in the filegroup.</span></span> <span data-ttu-id="8b48b-114">容器是在 [一般] 頁面上加入的。</span><span class="sxs-lookup"><span data-stu-id="8b48b-114">Containers are added on the **General** page.</span></span>  
  
4.  <span data-ttu-id="8b48b-115">按一下 [一般] 頁面，將檔案 (容器) 加入檔案群組中。</span><span class="sxs-lookup"><span data-stu-id="8b48b-115">To add a file (container) to the filegroup, click the **General** page.</span></span> <span data-ttu-id="8b48b-116">在 [資料庫檔案] 下，按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-116">Under **Database files**, click **Add**.</span></span> <span data-ttu-id="8b48b-117">將 [檔案類型] 選取為 [FILESTREAM 資料]、指定容器的邏輯名稱、選取記憶體最佳化檔案群組，並且確定 [自動成長/大小上限] 設定為 [無限制]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-117">Select **File Type** as **FILESTREAM Data**, specify the logical name of the container, select the memory-optimized filegroup, and make sure that **Autogrowth / Maxsize** is set to **Unlimited**.</span></span>  
  
     <span data-ttu-id="8b48b-118">如需如何使用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]建立新資料庫的詳細資訊，請參閱[建立資料庫](../databases/create-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="8b48b-118">For more information on how to create a new database by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [Create a Database](../databases/create-a-database.md).</span></span>  
  
### <a name="to-create-a-memory-optimized-table"></a><span data-ttu-id="8b48b-119">若要建立記憶體最佳化的資料表</span><span class="sxs-lookup"><span data-stu-id="8b48b-119">To create a memory-optimized table</span></span>  
  
1.  <span data-ttu-id="8b48b-120">在 [物件總管] 中，以滑鼠右鍵按一下資料庫的 [資料表] 節點，再按一下 [新增]，然後按一下 [記憶體最佳化的資料表]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-120">In **Object Explorer**, right-click the **Tables** node of your database, click **New**, and then click **Memory Optimized Table**.</span></span>  
  
     <span data-ttu-id="8b48b-121">隨即顯示建立記憶體最佳化資料表的範本。</span><span class="sxs-lookup"><span data-stu-id="8b48b-121">A template for creating memory-optimized tables is displayed.</span></span>  
  
2.  <span data-ttu-id="8b48b-122">若要取代範本參數，請在 [查詢] 功能表上，按一下 [指定範本參數的值]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-122">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="8b48b-123">如需有關如何使用範本的詳細資訊，請參閱[範本總管](../../ssms/template/template-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="8b48b-123">For more information on how to use templates, see [Template Explorer](../../ssms/template/template-explorer.md).</span></span>  
  
3.  <span data-ttu-id="8b48b-124">在 [物件總管] 中，資料表的排序是先按照磁碟資料表，然後再按照記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="8b48b-124">In **Object Explorer**, tables will be ordered first by disk-based tables followed by memory-optimized tables.</span></span> <span data-ttu-id="8b48b-125">您可以使用 [物件總管詳細資料]查看所有按照名稱排序的資料表。</span><span class="sxs-lookup"><span data-stu-id="8b48b-125">Use **Object Explorer Details** to see all tables ordered by name.</span></span>  
  
### <a name="to-create-a-natively-compiled-stored-procedure"></a><span data-ttu-id="8b48b-126">若要建立原生編譯的預存程序</span><span class="sxs-lookup"><span data-stu-id="8b48b-126">To create a natively compiled stored procedure</span></span>  
  
1.  <span data-ttu-id="8b48b-127">在 [物件總管] 中，以滑鼠右鍵按一下資料庫的 [預存程序] 節點，再按一下 [新增]，然後按一下 [原生編譯的預存程序]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-127">In **Object Explorer**, right-click the **Stored Procedures** node of your database, click **New**, and then click **Natively Compiled Stored Procedure**.</span></span>  
  
     <span data-ttu-id="8b48b-128">建立原生編譯預存程序的範本會顯示。</span><span class="sxs-lookup"><span data-stu-id="8b48b-128">A template for creating natively compiled stored procedures is displayed.</span></span>  
  
2.  <span data-ttu-id="8b48b-129">若要取代範本參數，請在 [查詢] 功能表上，按一下 [指定範本參數的值]</span><span class="sxs-lookup"><span data-stu-id="8b48b-129">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query menu**.</span></span>  
  
     <span data-ttu-id="8b48b-130">如需有關如何建立新的預存程序的詳細資訊，請參閱[建立預存程序](../stored-procedures/create-a-stored-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="8b48b-130">For more information on how to create a new stored procedure, see [Create a Stored Procedure](../stored-procedures/create-a-stored-procedure.md).</span></span>  
  
### <a name="to-create-a-user-defined-memory-optimized-table-type"></a><span data-ttu-id="8b48b-131">若要建立使用者定義的記憶體最佳化資料表類型</span><span class="sxs-lookup"><span data-stu-id="8b48b-131">To create a user-defined memory-optimized table type</span></span>  
  
1.  <span data-ttu-id="8b48b-132">在 [物件總管]**物件總管** 中，展開資料庫的 [類型] 節點，以滑鼠右鍵按一下 [使用者定義資料表類型] 節點，按一下 [新增]，然後按一下 [使用者定義的記憶體最佳化資料表類型]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-132">In **Object Explorer**, expand the **Types** node of your database, right-click the **User-Defined Table Types** node, click **New**, and then click **User-Defined Memory Optimized Table Type**.</span></span>  
  
     <span data-ttu-id="8b48b-133">建立使用者定義的記憶體最佳化資料表類型的範本隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="8b48b-133">A template for creating user-defined memory-optimized table type is displayed.</span></span>  
  
2.  <span data-ttu-id="8b48b-134">若要取代範本參數，請在 [查詢] 功能表上，按一下 [指定範本參數的值]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-134">To replace the template parameters, click **Specify Values for Template Parameters** on the **Query** menu.</span></span>  
  
     <span data-ttu-id="8b48b-135">如需有關如何建立新的預存程序的詳細資訊，請參閱 [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8b48b-135">For more information on how to create a new stored procedure, see [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).</span></span>  
  
## <a name="memory-monitoring"></a><span data-ttu-id="8b48b-136">記憶體監視</span><span class="sxs-lookup"><span data-stu-id="8b48b-136">Memory Monitoring</span></span>  
  
#### <a name="view-memory-usage-by-memory-optimized-objects-report"></a><span data-ttu-id="8b48b-137">檢視依記憶體最佳化物件的記憶體使用量報表</span><span class="sxs-lookup"><span data-stu-id="8b48b-137">View Memory Usage by Memory-Optimized Objects Report</span></span>  
  
-   <span data-ttu-id="8b48b-138">在 [物件總管] 中，以滑鼠右鍵按一下資料庫，再按一下 [報表]，並按一下 [標準報表]，然後按一下 [依記憶體最佳化物件的記憶體使用量]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-138">In **Object Explorer**, right-click your database, click **Reports**, click **Standard Reports**, and then click **Memory Usage By Memory Optimized Objects**.</span></span>  
  
     <span data-ttu-id="8b48b-139">此報表會提供資料庫中，記憶體最佳化物件使用之記憶體空間的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8b48b-139">This report provides detailed data on the utilization of memory space by memory-optimized objects within the database.</span></span>  
  
#### <a name="view-properties-for-allocated-and-used-memory-for-a-table-database"></a><span data-ttu-id="8b48b-140">檢視資料表、資料庫之「配置的記憶體」與「使用的記憶體」的屬性</span><span class="sxs-lookup"><span data-stu-id="8b48b-140">View Properties for Allocated and Used Memory for a Table, Database</span></span>  
  
1.  <span data-ttu-id="8b48b-141">若要取得記憶體中使用量的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="8b48b-141">To get information about in-memory usage:</span></span>  
  
    -   <span data-ttu-id="8b48b-142">在 [物件總管] 中，以滑鼠右鍵按一下記憶體最佳化的資料表，按一下 [屬性]，然後按一下 [儲存體] 頁面。</span><span class="sxs-lookup"><span data-stu-id="8b48b-142">In **Object Explorer**, right-click on your memory-optimized table, click **Properties**, and then the **Storage** page.</span></span> <span data-ttu-id="8b48b-143">[資料空間] 屬性的值表示資料表資料所用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b48b-143">The value for the **Data Space** property indicates the memory used by the data in the table.</span></span> <span data-ttu-id="8b48b-144">[索引空間] 屬性的值表示資料表索引所用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b48b-144">The value for the **Index Space** property indicates the memory used by the indexes on table.</span></span>  
  
    -   <span data-ttu-id="8b48b-145">在 [物件總管] 中，以滑鼠右鍵按一下資料庫，按一下 [屬性]，然後按一下 [一般] 頁面。</span><span class="sxs-lookup"><span data-stu-id="8b48b-145">In **Object Explorer**, right-click on your database, click **Properties**, and then click the **General** page.</span></span> <span data-ttu-id="8b48b-146">[配置給記憶體最佳化物件的記憶體] 屬性的值表示配置給資料庫中記憶體最佳化物件的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b48b-146">The value for the **Memory Allocated To Memory Optimized Objects** property indicates the memory allocated to memory-optimized objects in the database.</span></span> <span data-ttu-id="8b48b-147">[由記憶體最佳化物件所使用的記憶體] 屬性的值表示資料庫中記憶體最佳化物件所用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b48b-147">The value for the **Memory Used By Memory Optimized Objects** property indicates the memory used by memory-optimized objects in the database.</span></span>  
  
## <a name="supported-features-in-ssmanstudiofull"></a><span data-ttu-id="8b48b-148">下列項目所支援的功能： [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b48b-148">Supported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8b48b-149">支援具有最佳化資料的檔案群組、記憶體最佳化的資料表、索引與原生編譯的預存程序之資料庫的 Database Engine 所支援的功能和作業。</span><span class="sxs-lookup"><span data-stu-id="8b48b-149">supports features and operations that are supported by the database engine on databases with memory-optimized data filegroup, memory-optimized tables, indexes, and natively compiled stored procedures.</span></span>  
  
 <span data-ttu-id="8b48b-150">下列 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 功能已針對資料庫、資料表、預存程序、使用者定義資料表類型或索引物件更新或擴充，可支援 In-Memory OLTP。</span><span class="sxs-lookup"><span data-stu-id="8b48b-150">For database, table, stored procedure, user-defined table type, or index objects, the following [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] features have been updated or extended to support In-Memory OLTP.</span></span>  
  
-   <span data-ttu-id="8b48b-151">物件總管</span><span class="sxs-lookup"><span data-stu-id="8b48b-151">Object Explorer</span></span>  
  
    -   <span data-ttu-id="8b48b-152">操作功能表</span><span class="sxs-lookup"><span data-stu-id="8b48b-152">Context menus</span></span>  
  
    -   <span data-ttu-id="8b48b-153">篩選設定</span><span class="sxs-lookup"><span data-stu-id="8b48b-153">Filter settings</span></span>  
  
    -   <span data-ttu-id="8b48b-154">編寫組件的指令碼為</span><span class="sxs-lookup"><span data-stu-id="8b48b-154">Script As</span></span>  
  
    -   <span data-ttu-id="8b48b-155">工作</span><span class="sxs-lookup"><span data-stu-id="8b48b-155">Tasks</span></span>  
  
    -   <span data-ttu-id="8b48b-156">報表</span><span class="sxs-lookup"><span data-stu-id="8b48b-156">Reports</span></span>  
  
    -   <span data-ttu-id="8b48b-157">屬性</span><span class="sxs-lookup"><span data-stu-id="8b48b-157">Properties</span></span>  
  
    -   <span data-ttu-id="8b48b-158">資料庫工作：</span><span class="sxs-lookup"><span data-stu-id="8b48b-158">Database tasks:</span></span>  
  
        -   <span data-ttu-id="8b48b-159">附加和卸離包含記憶體最佳化資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b48b-159">Attach and detach a database that contains memory-optimized tables.</span></span>  
  
             <span data-ttu-id="8b48b-160">[附加資料庫] 使用者介面並不會顯示記憶體最佳化的資料檔案群組。</span><span class="sxs-lookup"><span data-stu-id="8b48b-160">The **Attach Databases** user interface does not display the memory-optimized data filegroup.</span></span> <span data-ttu-id="8b48b-161">不過，您還是可以附加資料庫，而且將能正確地附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b48b-161">However, you can proceed with attaching the database and the database will be attached correctly.</span></span>  
  
            > [!NOTE]  
            >  <span data-ttu-id="8b48b-162">如果您要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 附加有記憶體最佳化資料檔案群組容器的資料庫，而且在另一部電腦上建立資料庫的記憶體最佳化資料檔案群組容器，這兩部電腦上記憶體最佳化資料檔案群組容器的位置必須相同。</span><span class="sxs-lookup"><span data-stu-id="8b48b-162">If you want to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to attach a database that has a memory-optimized data filegroup container, and if the database's memory-optimized data filegroup container was created on another computer, the location of the memory-optimized data filegroup container must be the same on both computers.</span></span> <span data-ttu-id="8b48b-163">若您希望資料庫的記憶體最佳化資料檔案群組容器的位置在新的電腦上有不同的位置，您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b48b-163">If you want the location of the database's memory-optimized data filegroup container to be different on the new computer, you can, use [!INCLUDE[tsql](../../includes/tsql-md.md)] to attach the database.</span></span> <span data-ttu-id="8b48b-164">在下列範例中，新的電腦上記憶體最佳化資料檔案群組容器的位置為 C:\Folder2。</span><span class="sxs-lookup"><span data-stu-id="8b48b-164">In the following example, the location of the memory-optimized data filegroup container on the new computer is C:\Folder2.</span></span> <span data-ttu-id="8b48b-165">但是，原本在第一部電腦上建立記憶體最佳化資料檔案群組容器的位置是 C:\Folder1。</span><span class="sxs-lookup"><span data-stu-id="8b48b-165">But when the memory-optimized data filegroup container was created, on the first computer, the location was C:\Folder1.</span></span>  
            >   
            >  `CREATE DATABASE[imoltp] ON`  
            >   
            >  `(NAME =N'imoltp',FILENAME=N'C:\Folder2\imoltp.mdf'),`  
            >   
            >  `(NAME =N'imoltp_mod1',FILENAME=N'C:\Folder2\imoltp_mod1'),`  
            >   
            >  `(NAME =N'imoltp_log',FILENAME=N'C:\Folder2\imoltp_log.ldf')`  
            >   
            >  `FOR ATTACH`  
            >   
            >  `GO`  
  
        -   <span data-ttu-id="8b48b-166">產生指令碼。</span><span class="sxs-lookup"><span data-stu-id="8b48b-166">Generate scripts.</span></span>  
  
             <span data-ttu-id="8b48b-167">在 [產生和發佈指令碼精靈] 中，[檢查物件是否存在] 指令碼選項的預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="8b48b-167">In the **Generate and Publish Scripts Wizard**, the default value for **Check for object existence** scripting option is FALSE.</span></span> <span data-ttu-id="8b48b-168">如果精靈的 [設定指令碼編寫選項] 畫面將 [檢查物件是否存在] 指令碼選項的值設為 TRUE，則產生的指令碼會包含 "CREATE PROCEDURE <procedure_name> AS" 和 "ALTER PROCEDURE <procedure_name> <procedure_definition>"。</span><span class="sxs-lookup"><span data-stu-id="8b48b-168">If the value of **Check for object existence** scripting option is set to TRUE in the **Set Scripting Options** screen of the wizard, the script generated would contain "CREATE PROCEDURE <procedure_name> AS" and "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span> <span data-ttu-id="8b48b-169">在執行時，產生的指令碼將傳回錯誤，因為原生編譯預存程序不支援 ALTER PROCEDURE。</span><span class="sxs-lookup"><span data-stu-id="8b48b-169">When executed, the generated script will return an error as ALTER PROCEDURE is not supported on natively compiled stored procedures.</span></span>  
  
             <span data-ttu-id="8b48b-170">若要變更每一個原生編譯預存程序其產生的指令碼：</span><span class="sxs-lookup"><span data-stu-id="8b48b-170">To change the generated script for each natively compiled stored procedure:</span></span>  
  
            1.  <span data-ttu-id="8b48b-171">將 "CREATE PROCEDURE <procedure_name> AS" 中的 "AS" 取代成 "<procedure_definition>"。</span><span class="sxs-lookup"><span data-stu-id="8b48b-171">In "CREATE PROCEDURE <procedure_name> AS", replace "AS" with "<procedure_definition>".</span></span>  
  
            2.  <span data-ttu-id="8b48b-172">刪除 "ALTER PROCEDURE <procedure_name> <procedure_definition>"。</span><span class="sxs-lookup"><span data-stu-id="8b48b-172">Delete "ALTER PROCEDURE <procedure_name> <procedure_definition>".</span></span>  
  
        -   <span data-ttu-id="8b48b-173">複製資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b48b-173">Copy databases.</span></span> <span data-ttu-id="8b48b-174">對於具有記憶體最佳化之物件的資料庫，交易時不會在目的伺服器上建立資料庫及傳送資料。</span><span class="sxs-lookup"><span data-stu-id="8b48b-174">For databases with memory-optimized objects, the creation of the database on the destination server and transfer of data will not be executed within a transaction.</span></span>  
  
        -   <span data-ttu-id="8b48b-175">匯入和匯出資料。</span><span class="sxs-lookup"><span data-stu-id="8b48b-175">Import and export data.</span></span> <span data-ttu-id="8b48b-176">使用 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]匯入和匯出精靈] 的 [從一個或多個資料表或檢視表複製資料] 選項。</span><span class="sxs-lookup"><span data-stu-id="8b48b-176">Use the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export WizardCopy data from one or more tables or views** option.</span></span> <span data-ttu-id="8b48b-177">如果目的地資料表是不存在於目的地資料庫中的記憶體最佳化資料表：</span><span class="sxs-lookup"><span data-stu-id="8b48b-177">If the destination table is a memory-optimized table that does not exist in the destination database:</span></span>  
  
            1.  <span data-ttu-id="8b48b-178">在 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]匯入和匯出精靈] 的 [指定資料表複製或查詢] 畫面，選取 [從一個或多個資料表或檢視表複製資料]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-178">In the **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Import and Export Wizard**, in the **Specify Table Copy or Query** screen, select **Copy data from one or more tables or views**.</span></span> <span data-ttu-id="8b48b-179">然後按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-179">Then click **Next**.</span></span>  
  
            2.  <span data-ttu-id="8b48b-180">按一下 [編輯對應]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-180">Click **Edit Mappings**.</span></span> <span data-ttu-id="8b48b-181">然後選取 [建立目的資料表] 並按一下 [編輯 SQL]。</span><span class="sxs-lookup"><span data-stu-id="8b48b-181">Then select **Create destination table** and click **Edit SQL**.</span></span> <span data-ttu-id="8b48b-182">輸入 CREATE TABLE 語法，在目的地資料庫上建立記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="8b48b-182">Enter the CREATE TABLE syntax for creating a memory-optimized table on the destination database.</span></span> <span data-ttu-id="8b48b-183">按一下 [確定] 並完成此精靈中的其餘步驟。</span><span class="sxs-lookup"><span data-stu-id="8b48b-183">Click **OK** and complete the remaining steps in the wizard.</span></span>  
  
        -   <span data-ttu-id="8b48b-184">維護計畫。</span><span class="sxs-lookup"><span data-stu-id="8b48b-184">Maintenance plans.</span></span> <span data-ttu-id="8b48b-185">記憶體最佳化資料表與其索引上不支援辨識索引和重建索引這兩項維護工作。</span><span class="sxs-lookup"><span data-stu-id="8b48b-185">The maintenance tasks reorganize index and rebuild index are not supported on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="8b48b-186">因此，當重建索引和辨識索引的維護計畫執行時，就會省略所選取資料庫中的記憶體最佳化資料表及其索引。</span><span class="sxs-lookup"><span data-stu-id="8b48b-186">Therefore, when a maintenance plan for rebuild index and reorganize index are executed, the memory-optimized tables and their indexes in the selected databases are omitted.</span></span>  
  
             <span data-ttu-id="8b48b-187">記憶體最佳化資料表及其索引上的範例掃描不支援更新統計資料維護工作。</span><span class="sxs-lookup"><span data-stu-id="8b48b-187">The maintenance task update statistics are not supported with a sample scan on memory-optimized tables and their indexes.</span></span> <span data-ttu-id="8b48b-188">因此，當更新統計資料的維護計畫執行時，記憶體最佳化資料表及其索引的統計資料就會一律更新至 `WITH FULLSCAN, NORECOMPUTE`。</span><span class="sxs-lookup"><span data-stu-id="8b48b-188">Therefore, when a maintenance plan for update statistics is executed, the statistics for memory-optimized tables and their indexes are always updated to `WITH FULLSCAN, NORECOMPUTE`.</span></span>  
  
-   <span data-ttu-id="8b48b-189">物件總管詳細資料窗格</span><span class="sxs-lookup"><span data-stu-id="8b48b-189">Object Explorer details pane</span></span>  
  
-   <span data-ttu-id="8b48b-190">範本總管</span><span class="sxs-lookup"><span data-stu-id="8b48b-190">Template Explorer</span></span>  
  
## <a name="unsupported-features-in-ssmanstudiofull"></a><span data-ttu-id="8b48b-191">不為下列項目所支援的功能： [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b48b-191">Unsupported Features in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="8b48b-192">對於記憶體中 OLTP 物件， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 不支援 Database Engine 所不支援的功能和作業。</span><span class="sxs-lookup"><span data-stu-id="8b48b-192">For In-Memory OLTP objects, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not support features and operations that are also not supported by the database engine.</span></span>  
  
 <span data-ttu-id="8b48b-193">如需不支援功能的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[支援的 SQL Server 功能](unsupported-sql-server-features-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="8b48b-193">For more information on unsupported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features, see [Supported SQL Server Features](unsupported-sql-server-features-for-in-memory-oltp.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b48b-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b48b-194">See Also</span></span>  
 [<span data-ttu-id="8b48b-195">記憶體中 OLTP 的 SQL Server 支援</span><span class="sxs-lookup"><span data-stu-id="8b48b-195">SQL Server Support for In-Memory OLTP</span></span>](sql-server-support-for-in-memory-oltp.md)  
  
  
