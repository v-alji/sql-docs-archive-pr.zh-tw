---
title: 判斷是否應將資料表或預存程序移植至記憶體內部 OLTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- Analyze, Migrate, Report
- AMR
ms.assetid: c1ef96f1-290d-4952-8369-2f49f27afee2
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e517cff394bc0c813e34763469f75147a0a16c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595980"
---
# <a name="determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp"></a><span data-ttu-id="d342a-102">判斷是否應將資料表或預存程序匯出至記憶體中 OLTP</span><span class="sxs-lookup"><span data-stu-id="d342a-102">Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP</span></span>
  <span data-ttu-id="d342a-103">中的交易效能收集器 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 可協助您評估記憶體內部 OLTP 是否能改善資料庫應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="d342a-103">The transaction performance collector in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] helps you evaluate if In-Memory OLTP will improve your database application's performance.</span></span> <span data-ttu-id="d342a-104">交易效能分析報表還會指出應用程式啟用記憶體中 OLTP 所需執行的工作。</span><span class="sxs-lookup"><span data-stu-id="d342a-104">The transaction performance analysis report also indicates how much work you must do to enable In-Memory OLTP in your application.</span></span> <span data-ttu-id="d342a-105">識別您要匯出至記憶體內部 OLTP 的磁碟資料表之後，即可使用 [記憶體最佳化建議程式](memory-optimization-advisor.md)協助您遷移資料表。</span><span class="sxs-lookup"><span data-stu-id="d342a-105">After you identify a disk-based table to port to In-Memory OLTP, you can use the [Memory Optimization Advisor](memory-optimization-advisor.md), to help you migrate the table.</span></span> <span data-ttu-id="d342a-106">同樣地， [Native Compilation Advisor](native-compilation-advisor.md) 可協助您將預存程序匯出為原生編譯的預存程序。</span><span class="sxs-lookup"><span data-stu-id="d342a-106">Similarly, the [Native Compilation Advisor](native-compilation-advisor.md) will help you port a stored procedure to a natively compiled stored procedure.</span></span>  
  
 <span data-ttu-id="d342a-107">本主題將討論如何執行以下工作：</span><span class="sxs-lookup"><span data-stu-id="d342a-107">This topic will discuss how to:</span></span>  
  
-   <span data-ttu-id="d342a-108">設定管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="d342a-108">Configure Management Data Warehouse.</span></span>  
  
-   <span data-ttu-id="d342a-109">設定資料收集。</span><span class="sxs-lookup"><span data-stu-id="d342a-109">Configure data collection.</span></span>  
  
-   <span data-ttu-id="d342a-110">產生交易效能分析報表來識別效能關鍵的資料表和預存程序。</span><span class="sxs-lookup"><span data-stu-id="d342a-110">Generate transaction performance analysis reports to identify performance-critical tables and stored procedures.</span></span>  
  
 <span data-ttu-id="d342a-111">如需移轉方法的資訊，請參閱 [In-Memory OLTP - 一般工作負載模式和移轉考量](https://msdn.microsoft.com/library/dn673538.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d342a-111">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
 <span data-ttu-id="d342a-112">交易效能收集器和交易效能分析報表將協助您完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="d342a-112">The transaction performance collector and the transaction performance analysis reports help you accomplish the following tasks:</span></span>  
  
-   <span data-ttu-id="d342a-113">分析您的工作負載，判斷記憶體中 OLTP 是否可改善效能。</span><span class="sxs-lookup"><span data-stu-id="d342a-113">Analyze your workload to determine if In-Memory OLTP will improve performance.</span></span> <span data-ttu-id="d342a-114">交易效能收集器會收集和評估您的工作負載的效能特性。</span><span class="sxs-lookup"><span data-stu-id="d342a-114">The transaction performance collector collects and evaluates the performance characteristics of your workload.</span></span> <span data-ttu-id="d342a-115">.</span><span class="sxs-lookup"><span data-stu-id="d342a-115">.</span></span> <span data-ttu-id="d342a-116">交易效能分析報表接著會建議轉換成記憶體中 OLTP 後獲益最多的資料表和預存程序。</span><span class="sxs-lookup"><span data-stu-id="d342a-116">The transaction performance analysis report then recommends tables and stored procedures that would benefit most from conversion to In-Memory OLTP.</span></span>  
  
-   <span data-ttu-id="d342a-117">協助您規劃及執行移轉為記憶體中 OLTP 的作業。</span><span class="sxs-lookup"><span data-stu-id="d342a-117">Help you plan and execute your migration to In-Memory OLTP.</span></span> <span data-ttu-id="d342a-118">從磁碟資料表移轉到記憶體最佳化資料表，其間的移轉路徑可能會很費時。</span><span class="sxs-lookup"><span data-stu-id="d342a-118">The migration path from a disk based table to a memory-optimized table can be time consuming.</span></span> <span data-ttu-id="d342a-119">記憶體最佳化 Advisor 可協助您識別將資料表移至記憶體中 OLTP 之前必須先從資料表移除的不相容項目。</span><span class="sxs-lookup"><span data-stu-id="d342a-119">The Memory-Optimization Advisor helps you identify the incompatibilities in your table that you must remove before moving the table to In-Memory OLTP.</span></span> <span data-ttu-id="d342a-120">記憶體最佳化 Advisor 也可協助您了解將資料表移轉到記憶體最佳化的資料表時，將對應用程式造成什麼影響。</span><span class="sxs-lookup"><span data-stu-id="d342a-120">The Memory-Optimization Advisor also helps you understand the impact that the migration of a table to a memory-optimized table will have on your application.</span></span>  
  
     <span data-ttu-id="d342a-121">當您想要規劃移轉至記憶體中 OLTP 的作業，以及想要將部分資料表和預存程序移轉至記憶體中 OLTP 時，都可以檢查您的應用程式能否獲益於記憶體中 OLTP。</span><span class="sxs-lookup"><span data-stu-id="d342a-121">You can see if your application would benefit from In-Memory OLTP, when you want to plan your migration to In-Memory OLTP, and whenever you work to migrate some of your tables and stored procedures to In-Memory OLTP.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d342a-122">資料庫系統的效能取決於各種不同的因素，並不是所有因素都可由交易效能收集器來觀察和測量。</span><span class="sxs-lookup"><span data-stu-id="d342a-122">The performance of a database system is dependent on a variety of factors, not all of which the transaction performance collector can observe and measure.</span></span> <span data-ttu-id="d342a-123">因此，交易效能分析報表不保證實際的效能增益將會符合預測 (如果進行了任何預測)。</span><span class="sxs-lookup"><span data-stu-id="d342a-123">Therefore, the transaction performance analysis report does not guarantee actual performance gains will match its predictions, if any predictions are made.</span></span>  
  
 <span data-ttu-id="d342a-124">當您安裝時，當您選取 [**管理工具-基本**] 或 [**管理工具-Advanced** ] 時，就會安裝交易效能收集器和產生交易效能分析報表的功能 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d342a-124">The transaction performance collector and the ability to generate a transaction performance analysis report are installed when you select **Management Tools-Basic** or **Management Tools-Advanced** when you install [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="d342a-125">最佳做法</span><span class="sxs-lookup"><span data-stu-id="d342a-125">Best Practices</span></span>  
 <span data-ttu-id="d342a-126">建議的工作流程如以下流程圖所示。</span><span class="sxs-lookup"><span data-stu-id="d342a-126">The recommended workflow is illustrated in the following flowchart.</span></span> <span data-ttu-id="d342a-127">黃色節點代表選用程序：</span><span class="sxs-lookup"><span data-stu-id="d342a-127">The yellow nodes represent optional procedures:</span></span>  
  
 <span data-ttu-id="d342a-128">![AMR 工作流程](../../database-engine/media/amr-1.gif "AMR 工作流程")</span><span class="sxs-lookup"><span data-stu-id="d342a-128">![AMR workflow](../../database-engine/media/amr-1.gif "AMR workflow")</span></span>  
  
 <span data-ttu-id="d342a-129">您可以使用任何方法來建立效能基準，包括但不限於使用效能計數器記錄或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 活動監視器。</span><span class="sxs-lookup"><span data-stu-id="d342a-129">You can use any method to establish a performance baseline, including but not limited to using performance counter logs or the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Activity Monitor.</span></span> <span data-ttu-id="d342a-130">您的效能基準和比較中所要使用的資訊包括：</span><span class="sxs-lookup"><span data-stu-id="d342a-130">The information to use in your performance baseline and your comparisons are:</span></span>  
  
-   <span data-ttu-id="d342a-131"> 的 CPU 耗用量。</span><span class="sxs-lookup"><span data-stu-id="d342a-131">CPU consumption of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d342a-132"> 的記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="d342a-132">Memory consumption of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d342a-133"> 的 I/O 活動。</span><span class="sxs-lookup"><span data-stu-id="d342a-133">I/O activity of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d342a-134">在處理交易時的執行個體交易輸送量。</span><span class="sxs-lookup"><span data-stu-id="d342a-134">Transaction throughput of the instance while processing transactions.</span></span>  
  
 <span data-ttu-id="d342a-135">交易效能收集器每隔 15 分鐘擷取一次資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-135">The transaction performance collector captures data every 15 minutes.</span></span> <span data-ttu-id="d342a-136">為了取得實用的結果，請執行交易效能收集器至少一個小時。</span><span class="sxs-lookup"><span data-stu-id="d342a-136">To obtain usable results, run the transaction performance collector for at least one hour.</span></span> <span data-ttu-id="d342a-137">為了取得最佳結果，請讓交易效能收集器有充裕的執行時間，以擷取主要案例所需的資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-137">To obtain best results, run the transaction performance collector for as much time as needed to capture data for your primary scenarios.</span></span> <span data-ttu-id="d342a-138">唯有在您完成資料的收集之後，再產生交易效能分析報表。</span><span class="sxs-lookup"><span data-stu-id="d342a-138">Generate a transaction performance analysis report only after you have finished gathering data.</span></span>  
  
 <span data-ttu-id="d342a-139">將交易效能收集器設定為在生產環境的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上執行，並收集開發 (測試) 環境中 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上的資料，以確保負擔最低。</span><span class="sxs-lookup"><span data-stu-id="d342a-139">Configure the transaction performance collector to run on your [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in production and collect the data on a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in your development (test) environment to ensure minimum overhead.</span></span> <span data-ttu-id="d342a-140">如需如何將資料儲存在遠端實例上的管理資料倉儲資料庫中的詳細資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱在[遠端 SQL Server 實例上設定資料收集](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md#xxx)。</span><span class="sxs-lookup"><span data-stu-id="d342a-140">For information on how to save data in a Management Data Warehouse database on a remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance, see [Configure Data Collection on a Remote SQL Server Instance](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md#xxx).</span></span>  
  
## <a name="performance-impacts"></a><span data-ttu-id="d342a-141">效能影響</span><span class="sxs-lookup"><span data-stu-id="d342a-141">Performance Impacts</span></span>  
 <span data-ttu-id="d342a-142">交易效能收集器是由兩個資料收集組所組成：</span><span class="sxs-lookup"><span data-stu-id="d342a-142">The transaction performance collector consists of two data collection sets:</span></span>  
  
-   <span data-ttu-id="d342a-143">資料表使用分析</span><span class="sxs-lookup"><span data-stu-id="d342a-143">Table Usage Analysis</span></span>  
  
-   <span data-ttu-id="d342a-144">預存程序分析</span><span class="sxs-lookup"><span data-stu-id="d342a-144">Stored Procedure Analysis</span></span>  
  
 <span data-ttu-id="d342a-145">收集組每隔十五分鐘會從三個動態管理檢視 (DMV) 收集資料，並將資料上傳到設定為當做管理資料倉儲的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d342a-145">The collection sets collect data from three dynamic management views (DMV) every fifteen minutes, and upload the data to the database configured to act as the Management Data Warehouse.</span></span> <span data-ttu-id="d342a-146">上傳收集的資料對於效能的影響很低。</span><span class="sxs-lookup"><span data-stu-id="d342a-146">Uploading the collected data incurs minimal performance impact.</span></span>  
  
## <a name="use-the-transaction-performance-collector"></a><span data-ttu-id="d342a-147">使用交易效能收集器</span><span class="sxs-lookup"><span data-stu-id="d342a-147">Use the Transaction Performance Collector</span></span>  
 <span data-ttu-id="d342a-148">以下步驟需要 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d342a-148">The following steps require [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d342a-149">請勿在分析期間變更結構描述 (例如，新增或移除資料庫，或建立或卸除資料表)。</span><span class="sxs-lookup"><span data-stu-id="d342a-149">Do not change the schema (for example, add or remove databases or create or drop tables) during profiling.</span></span> <span data-ttu-id="d342a-150">如果您在收集資料時變更資料庫的結構描述，納入報表中的資料庫可能會不準確。</span><span class="sxs-lookup"><span data-stu-id="d342a-150">If you change the schema of a database while collecting data, the database may not be accurately included in the report.</span></span>  
  
### <a name="configure-management-data-warehouse"></a><span data-ttu-id="d342a-151">設定管理資料倉儲</span><span class="sxs-lookup"><span data-stu-id="d342a-151">Configure Management Data Warehouse</span></span>  
 <span data-ttu-id="d342a-152">管理資料倉儲必須設定為使用交易效能收集器。</span><span class="sxs-lookup"><span data-stu-id="d342a-152">Management Data Warehouse must be configured to use the transaction performance collector.</span></span>  
  
 <span data-ttu-id="d342a-153">您收集資料所在的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體版本 (設定檔) 應該與設定管理資料倉儲的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本相同或更舊。</span><span class="sxs-lookup"><span data-stu-id="d342a-153">The version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that you will collect data on (profile) should be the same version or older than the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where Management Data Warehouse is configured.</span></span>  
  
1.  <span data-ttu-id="d342a-154">在物件總管中，展開 [管理]。</span><span class="sxs-lookup"><span data-stu-id="d342a-154">In Object Explorer, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="d342a-155">以滑鼠右鍵按一下 [**資料收集**]**並選取 [** 工作]，然後**設定 [管理資料倉儲**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-155">Right click **Data Collection** and select **Tasks** and then **Configure Management Data Warehouse**.</span></span> <span data-ttu-id="d342a-156">[**設定管理資料倉儲 Wizard]** 隨即開始。</span><span class="sxs-lookup"><span data-stu-id="d342a-156">The **Configure Management Data Warehouse Wizard** begins.</span></span>  
  
3.  <span data-ttu-id="d342a-157">按 **[下一步]** 以選取將作為管理資料倉儲的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d342a-157">Click **Next** to select the database that will act as the Management Data Warehouse.</span></span>  
  
4.  <span data-ttu-id="d342a-158">按一下 [**新增**] 以建立新的資料庫來保存設定檔資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-158">Click **New** to create a new database to hold the profile data.</span></span> <span data-ttu-id="d342a-159">當您完成建立資料庫之後，請按一下嚮導中的 **[下一步**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-159">After you finish creating the database, click **Next** in the wizard.</span></span>  
  
5.  <span data-ttu-id="d342a-160">精靈中的下一個步驟可讓您加入使用者和登入。</span><span class="sxs-lookup"><span data-stu-id="d342a-160">The next step in the wizard lets you add users and logins.</span></span> <span data-ttu-id="d342a-161">您可以將登入對應到 MDW 執行個體的角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="d342a-161">You may map logins to role memberships for the MDW instance.</span></span> <span data-ttu-id="d342a-162">從本機執行個體收集資料並不一定要這樣做。</span><span class="sxs-lookup"><span data-stu-id="d342a-162">This is not required to collect data from the local instance.</span></span> <span data-ttu-id="d342a-163">如果您不是從本機執行個體收集資料，您可以將資料庫角色成員資格 `mdw_admin` 授與將執行即將分析之交易的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d342a-163">If you are not collecting data from the local instance, you can grant database role membership `mdw_admin` to the account that will run transactions that will be profiled.</span></span> <span data-ttu-id="d342a-164">完成時，按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d342a-164">When done, click **Next**.</span></span>  
  
6.  <span data-ttu-id="d342a-165">確定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 正在執行中。</span><span class="sxs-lookup"><span data-stu-id="d342a-165">Make sure that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
7.  <span data-ttu-id="d342a-166">在下一個畫面上，按一下 **[完成] 結束**嚮導。</span><span class="sxs-lookup"><span data-stu-id="d342a-166">On the next screen, click **Finish** to exit the wizard.</span></span>  
  
### <a name="configure-data-collection-on-a-local-ssnoversion-instance"></a><span data-ttu-id="d342a-167">在本機 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上設定資料收集</span><span class="sxs-lookup"><span data-stu-id="d342a-167">Configure Data Collection on a Local [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>  
 <span data-ttu-id="d342a-168">資料收集需要啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent。</span><span class="sxs-lookup"><span data-stu-id="d342a-168">Data collection requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to be started.</span></span> <span data-ttu-id="d342a-169">您只需要在伺服器上設定一個資料收集器。</span><span class="sxs-lookup"><span data-stu-id="d342a-169">You only need to configure one data collector on a server.</span></span>  
  
 <span data-ttu-id="d342a-170">您可以在 SQL Server 2012 或更新版本的上設定資料收集器 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d342a-170">A data collector can be configured on a SQL Server 2012 or later version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d342a-171">若要設定資料收集，以便上傳至相同執行個體上的管理資料倉儲資料庫：</span><span class="sxs-lookup"><span data-stu-id="d342a-171">To configure data collection to upload to a Management Data Warehouse database on the same instance,</span></span>  
  
1.  <span data-ttu-id="d342a-172">在**物件總管**中，展開 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-172">In **Object Explorer**, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="d342a-173">以滑鼠右鍵按一下 [**資料收集**] **、選取 [** 工作]，然後**設定 [資料收集**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-173">Right click **Data Collection**, select **Tasks**, and then **Configure Data Collection**.</span></span> <span data-ttu-id="d342a-174">[**設定資料收集嚮導]** 隨即開始。</span><span class="sxs-lookup"><span data-stu-id="d342a-174">The **Configure Data Collection Wizard** begins.</span></span>  
  
3.  <span data-ttu-id="d342a-175">按 **[下一步]** 以選取將收集設定檔資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d342a-175">Click **Next** to select the database that will collect the profile data.</span></span>  
  
4.  <span data-ttu-id="d342a-176">選取目前的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體以及該執行個體上的管理資料倉儲資料庫。</span><span class="sxs-lookup"><span data-stu-id="d342a-176">Select the current [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and a Management Data Warehouse database on that instance.</span></span>  
  
5.  <span data-ttu-id="d342a-177">在標示 [**選取您要啟用的資料收集器集合**] 的方塊中，選取 [**交易效能收集組**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-177">In the box labeled **Select data collector sets you want to enable**, select **Transaction Performance Collection Sets**.</span></span> <span data-ttu-id="d342a-178">完成時按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d342a-178">Click **Next** when done.</span></span>  
  
6.  <span data-ttu-id="d342a-179">驗證選取項目。</span><span class="sxs-lookup"><span data-stu-id="d342a-179">Verify the selections.</span></span> <span data-ttu-id="d342a-180">按 [**上一步**] 修改設定。</span><span class="sxs-lookup"><span data-stu-id="d342a-180">Click **Back** to modify the settings.</span></span> <span data-ttu-id="d342a-181">完成時按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="d342a-181">Click **Finish** when done.</span></span>  
  
###  <a name="configure-data-collection-on-a-remote-ssnoversion-instance"></a><a name="xxx"></a><span data-ttu-id="d342a-182">設定遠端實例上的資料收集 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d342a-182">Configure Data Collection on a Remote [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance</span></span>  
 <span data-ttu-id="d342a-183">您必須在收集資料所在的執行個體上啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 才能進行資料收集。</span><span class="sxs-lookup"><span data-stu-id="d342a-183">Data collection requires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent to be started on the instance that will collect the data.</span></span>  
  
 <span data-ttu-id="d342a-184">您可以在 SQL Server 2012 或更新版本的上設定資料收集器 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d342a-184">A data collector can be configured on a SQL Server 2012 or later version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d342a-185">您需要使用正確認證建立的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Proxy，資料收集器才能將資料上傳到執行個體上的管理資料倉儲資料庫 (此執行個體與即將分析交易的地方不同)。</span><span class="sxs-lookup"><span data-stu-id="d342a-185">You need a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy established with the correct credential for a data collector to upload data to a Management Data Warehouse database on an instance that is different from where transactions will be profiled.</span></span> <span data-ttu-id="d342a-186">若要啟用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Proxy，您必須先使用具有網域功能的登入建立認證。</span><span class="sxs-lookup"><span data-stu-id="d342a-186">To enable a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy, you must first establish a credential with a domain-enabled login.</span></span> <span data-ttu-id="d342a-187">具有網域功能的登入必須是管理資料倉儲資料庫的 `mdw_admin` 群組成員。</span><span class="sxs-lookup"><span data-stu-id="d342a-187">The domain-enabled login must be a member of `mdw_admin` group for the Management Data Warehouse database.</span></span> <span data-ttu-id="d342a-188">如需如何建立認證的相關資訊，請參閱[如何：建立認證 (SQL Server Management Studio) ](../security/authentication-access/create-a-credential.md) 。</span><span class="sxs-lookup"><span data-stu-id="d342a-188">See [How to: Create a Credential (SQL Server Management Studio)](../security/authentication-access/create-a-credential.md) for information on how to create a credential.</span></span>  
  
 <span data-ttu-id="d342a-189">若要設定資料收集，以便上傳至不同執行個體上的管理資料倉儲資料庫：</span><span class="sxs-lookup"><span data-stu-id="d342a-189">To configure data collection to upload to a Management Data Warehouse database on a different instance,</span></span>  
  
1.  <span data-ttu-id="d342a-190">在包含您想要遷移至記憶體中 OLTP 之磁片物件的實例上，展開物件總管中的 [**管理**] 節點。</span><span class="sxs-lookup"><span data-stu-id="d342a-190">On the instance that contains the disk-based objects that you want to migrate to In-Memory OLTP, expand the **Management** node in Object Explorer.</span></span>  
  
2.  <span data-ttu-id="d342a-191">以滑鼠右鍵按一下 [**資料收集**]**並選取 [** 工作]，然後**設定 [資料收集**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-191">Right click **Data Collection** and select **Tasks** and then **Configure Data Collection**.</span></span> <span data-ttu-id="d342a-192">[**設定資料收集嚮導]** 隨即開始。</span><span class="sxs-lookup"><span data-stu-id="d342a-192">The **Configure Data Collection Wizard** begins.</span></span>  
  
3.  <span data-ttu-id="d342a-193">按 **[下一步]** 以選取將收集設定檔資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d342a-193">Click **Next** to select the database that will collect the profile data.</span></span>  
  
4.  <span data-ttu-id="d342a-194">確認另一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上有管理資料倉儲資料庫存在。</span><span class="sxs-lookup"><span data-stu-id="d342a-194">Make sure that a Management Data Warehouse database exists on the other [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span>  
  
5.  <span data-ttu-id="d342a-195">選取另一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體和該執行個體上的管理資料倉儲資料庫。</span><span class="sxs-lookup"><span data-stu-id="d342a-195">Select another [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and a Management Data Warehouse database on that instance.</span></span>  
  
     <span data-ttu-id="d342a-196">您收集資料所在的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體版本 (設定檔) 應該與設定管理資料倉儲的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本相同或更舊。</span><span class="sxs-lookup"><span data-stu-id="d342a-196">The version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance that you will collect data on (profile) should be the same version or older than the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where Management Data Warehouse is configured.</span></span>  
  
6.  <span data-ttu-id="d342a-197">在標示 [**選取您要啟用的資料收集器集合**] 的方塊中，選取 [**交易效能收集組**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-197">In the box labeled **Select data collector sets you want to enable**, select **Transaction Performance Collection Sets**.</span></span>  
  
7.  <span data-ttu-id="d342a-198">選取 [**使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理程式 proxy 進行遠端上傳**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-198">Select **Use a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy for remote uploads**.</span></span>  
  
8.  <span data-ttu-id="d342a-199">完成時按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d342a-199">Click **Next** when done.</span></span>  
  
9. <span data-ttu-id="d342a-200">選取 Proxy。</span><span class="sxs-lookup"><span data-stu-id="d342a-200">Select the proxy.</span></span>  
  
     <span data-ttu-id="d342a-201">如果您要建立新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Proxy，</span><span class="sxs-lookup"><span data-stu-id="d342a-201">If you want to create a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy,</span></span>  
  
    1.  <span data-ttu-id="d342a-202">按一下 [**新增**] 以顯示 [**新 Proxy 帳戶**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d342a-202">Click **New** to display the **New Proxy Account** dialog box.</span></span>  
  
    2.  <span data-ttu-id="d342a-203">在 [**新 Proxy 帳戶**] 對話方塊中，輸入 proxy 的名稱，選取認證，然後選擇性地輸入描述。</span><span class="sxs-lookup"><span data-stu-id="d342a-203">In the **New Proxy Account** dialog box, enter the name of the proxy, select the credential, and optionally enter a description.</span></span> <span data-ttu-id="d342a-204">然後，按一下 [**主體**]。</span><span class="sxs-lookup"><span data-stu-id="d342a-204">Then, click **Principals**.</span></span>  
  
    3.  <span data-ttu-id="d342a-205">按一下 [**新增**]，然後選取 [ **Msdb**角色]。</span><span class="sxs-lookup"><span data-stu-id="d342a-205">Click **Add** and select **Msdb** role.</span></span>  
  
    4.  <span data-ttu-id="d342a-206">選取 `dc_proxy` 並按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d342a-206">Select `dc_proxy` and click **OK**.</span></span> <span data-ttu-id="d342a-207">然後再按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d342a-207">Then click **OK** again.</span></span>  
  
     <span data-ttu-id="d342a-208">選取正確的 proxy 之後，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d342a-208">After the correct proxy is selected, click **Next**.</span></span>  
  
10. <span data-ttu-id="d342a-209">若要設定系統收集組，請檢查**系統收集組**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d342a-209">To configure System Collection Sets, check **System Collection Sets** and click **Next**.</span></span>  
  
11. <span data-ttu-id="d342a-210">驗證選取項目。</span><span class="sxs-lookup"><span data-stu-id="d342a-210">Verify the selections.</span></span> <span data-ttu-id="d342a-211">按 [**上一步**] 修改設定。</span><span class="sxs-lookup"><span data-stu-id="d342a-211">Click **Back** to modify the settings.</span></span> <span data-ttu-id="d342a-212">完成時完成**完成]** 。</span><span class="sxs-lookup"><span data-stu-id="d342a-212">Clicck **Finish** when done.</span></span>  
  
 <span data-ttu-id="d342a-213">資料收集組現在應該已經設定妥，並且正在您的執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="d342a-213">Data collection sets should now be configured and running on your instance.</span></span>  
  
### <a name="generate-reports"></a><span data-ttu-id="d342a-214">產生報表</span><span class="sxs-lookup"><span data-stu-id="d342a-214">Generate Reports</span></span>  
 <span data-ttu-id="d342a-215">您可以用滑鼠右鍵按一下管理資料倉儲的資料庫，然後依序選取 [**報表**]、[**管理資料倉儲**] 和 **[交易效能分析總覽**]，來產生交易效能分析報表。</span><span class="sxs-lookup"><span data-stu-id="d342a-215">You can generate transaction performance analysis reports by right clicking the database of the Management Data Warehouse and selecting **Reports**, then **Management Data Warehouse**, and then **Transaction Performance Analysis Overview**.</span></span>  
  
 <span data-ttu-id="d342a-216">報表會收集工作負載伺服器上所有使用者資料庫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d342a-216">The report collects information about all user databases on the workload server.</span></span> <span data-ttu-id="d342a-217">如果您的管理資料倉儲 (MDW) 資料庫位於本機電腦上，則會在報表中看見 MDW 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d342a-217">If your Management Data Warehouse (MDW) database is on the local computer, you will see the MDW database(s) in the report.</span></span>  
  
 <span data-ttu-id="d342a-218">CPU 時間與經過時間的比率較高的預存程序就是移轉作業的候選。</span><span class="sxs-lookup"><span data-stu-id="d342a-218">A stored procedure with high ratio of CPU time to elapsed time is a candidate for migration.</span></span> <span data-ttu-id="d342a-219">報表會顯示所有資料表參考，因為原生方式編譯預存程序只能參考記憶體最佳化資料表，而這些資料表可能會增加移轉成本。</span><span class="sxs-lookup"><span data-stu-id="d342a-219">The report shows all table references, because natively compiled stored procedures can only reference memory-optimized tables, which can add to the migration cost.</span></span>  
  
 <span data-ttu-id="d342a-220">資料表的詳細報表包含三個部分：</span><span class="sxs-lookup"><span data-stu-id="d342a-220">The details report for a table consists of three sections:</span></span>  
  
-   <span data-ttu-id="d342a-221">掃描統計資料部分</span><span class="sxs-lookup"><span data-stu-id="d342a-221">Scan Statistics Section</span></span>  
  
     <span data-ttu-id="d342a-222">此部分包含單一資料表，將顯示所收集有關資料庫資料表上掃描次數的統計資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-222">This section includes a single table that shows the statistics that were collected about scans on the database table.</span></span> <span data-ttu-id="d342a-223">資料行如下：</span><span class="sxs-lookup"><span data-stu-id="d342a-223">The columns are:</span></span>  
  
    -   <span data-ttu-id="d342a-224">總存取數百分比。</span><span class="sxs-lookup"><span data-stu-id="d342a-224">Percent of total accesses.</span></span> <span data-ttu-id="d342a-225">整個資料庫活動中，此資料表上掃描次數與搜尋次數百分比。</span><span class="sxs-lookup"><span data-stu-id="d342a-225">The percentage of scans and seeks on this table with respect to the activity of the entire database.</span></span> <span data-ttu-id="d342a-226">此百分比愈高，表示與資料庫中的其他資料表相較下，較大量使用此資料表。</span><span class="sxs-lookup"><span data-stu-id="d342a-226">The higher this percentage, the more heavily used the table is compared to other tables in the database.</span></span>  
  
    -   <span data-ttu-id="d342a-227">查閱統計資料/範圍掃描統計資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-227">Lookup Statistics/Range Scan Statistics.</span></span> <span data-ttu-id="d342a-228">此資料行記錄分析期間，資料表上執行的點查閱及範圍掃描 (索引掃描及資料表掃描) 數。</span><span class="sxs-lookup"><span data-stu-id="d342a-228">This column records the number of point lookups and range scans (index scans and table scans) conducted on the table during profiling.</span></span> <span data-ttu-id="d342a-229">每筆交易的平均值為預估。</span><span class="sxs-lookup"><span data-stu-id="d342a-229">Average per transaction is an estimate.</span></span>  
  
    -   <span data-ttu-id="d342a-230">Interop 改善和原生改善。</span><span class="sxs-lookup"><span data-stu-id="d342a-230">Interop Gain and Native Gain.</span></span> <span data-ttu-id="d342a-231">這些資料行可預估當資料表轉換成記憶體最佳化資料表時，點查閱或範圍掃描將會得到的效能獲益量。</span><span class="sxs-lookup"><span data-stu-id="d342a-231">These columns estimate the amount of performance benefit a point lookup or range scan would have if the table is converted to a memory-optimized table.</span></span>  
  
-   <span data-ttu-id="d342a-232">競爭統計資料部分</span><span class="sxs-lookup"><span data-stu-id="d342a-232">Contention Statistics Section</span></span>  
  
     <span data-ttu-id="d342a-233">此部分包含在資料庫資料表上顯示競爭的資料表。</span><span class="sxs-lookup"><span data-stu-id="d342a-233">This section includes a table that shows contention on the database table.</span></span> <span data-ttu-id="d342a-234">如需有關資料庫閂鎖和鎖定的詳細資訊，請參閱[鎖定架構](https://msdn.microsoft.com/library/aa224738\(v=sql.80\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="d342a-234">For more information regarding database latches and locks, please see [Locking Architecture](https://msdn.microsoft.com/library/aa224738\(v=sql.80\).aspx).</span></span> <span data-ttu-id="d342a-235">資料行如下：</span><span class="sxs-lookup"><span data-stu-id="d342a-235">The columns are as follows:</span></span>  
  
    -   <span data-ttu-id="d342a-236">總等候次數百分比。</span><span class="sxs-lookup"><span data-stu-id="d342a-236">Percent of total waits.</span></span> <span data-ttu-id="d342a-237">與資料庫活動相比，此資料庫資料表上閂鎖和鎖定等候數的百分比。</span><span class="sxs-lookup"><span data-stu-id="d342a-237">The percentage of latch and lock waits on this database table compared to activity of the database.</span></span> <span data-ttu-id="d342a-238">此百分比愈高，表示與資料庫中的其他資料表相較下，較大量使用此資料表。</span><span class="sxs-lookup"><span data-stu-id="d342a-238">The higher this percentage, the more heavily used the table is compared to other tables in the database.</span></span>  
  
    -   <span data-ttu-id="d342a-239">閂鎖統計資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-239">Latch Statistics.</span></span> <span data-ttu-id="d342a-240">這些資料行記錄關於此資料表查詢的閂鎖等候數。</span><span class="sxs-lookup"><span data-stu-id="d342a-240">These columns record the number of latch waits for queries involving for this table.</span></span> <span data-ttu-id="d342a-241">如需閂鎖的詳細資訊，[請參閱閂鎖。](https://msdn.microsoft.com/library/aa224727\(v=SQL.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d342a-241">For information on latches, see [Latching](https://msdn.microsoft.com/library/aa224727\(v=SQL.80\).aspx).</span></span> <span data-ttu-id="d342a-242">此數字越高，表示資料表有越多閂鎖競爭。</span><span class="sxs-lookup"><span data-stu-id="d342a-242">The higher this number, the more latch contention on the table.</span></span>  
  
    -   <span data-ttu-id="d342a-243">鎖定統計資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-243">Lock Statistics.</span></span> <span data-ttu-id="d342a-244">此資料行群組記錄頁面鎖定取得數以及查詢此資料表的等候數。</span><span class="sxs-lookup"><span data-stu-id="d342a-244">This group of columns record the number of page lock acquisitions and waits for queries for this table.</span></span> <span data-ttu-id="d342a-245">如需鎖定的詳細資訊，請參閱[瞭解 SQL Server 中的鎖定](https://msdn.microsoft.com/library/aa213039\(v=SQL.80\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="d342a-245">For more information on locks, see [Understanding Locking in SQL Server](https://msdn.microsoft.com/library/aa213039\(v=SQL.80\).aspx).</span></span> <span data-ttu-id="d342a-246">等候數越多，表示資料表上越多鎖定競爭。</span><span class="sxs-lookup"><span data-stu-id="d342a-246">The more waits, the more lock contention on the table.</span></span>  
  
-   <span data-ttu-id="d342a-247">移轉難度部分</span><span class="sxs-lookup"><span data-stu-id="d342a-247">Migration Difficulties Section</span></span>  
  
     <span data-ttu-id="d342a-248">此部分包含顯示將此資料庫資料表轉換成記憶體最佳化資料表之難度的資料表。</span><span class="sxs-lookup"><span data-stu-id="d342a-248">This section includes a table that shows the difficulty of converting this database table to a memory-optimized table.</span></span> <span data-ttu-id="d342a-249">較高的難度評等表示較難轉換資料表。</span><span class="sxs-lookup"><span data-stu-id="d342a-249">A higher difficulty rating indicates more difficultly to convert the table.</span></span> <span data-ttu-id="d342a-250">若要查看要轉換此資料庫資料表的詳細資料，請使用[記憶體優化 Advisor](memory-optimization-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="d342a-250">To see details to convert this database table, please use the [Memory Optimization Advisor](memory-optimization-advisor.md).</span></span>  
  
 <span data-ttu-id="d342a-251">資料表詳細資料包表的掃描和競爭統計資料是從[sys. dm_db_index_operational_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql)收集和匯總。</span><span class="sxs-lookup"><span data-stu-id="d342a-251">Scan and contention statistics on the table details report is gathered and aggregated from [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).</span></span>  
  
 <span data-ttu-id="d342a-252">預存程序的詳細資料報表包含兩個部分：</span><span class="sxs-lookup"><span data-stu-id="d342a-252">The details report for a stored procedure consists of two sections:</span></span>  
  
-   <span data-ttu-id="d342a-253">執行統計資料部分</span><span class="sxs-lookup"><span data-stu-id="d342a-253">Execution Statistics Section</span></span>  
  
     <span data-ttu-id="d342a-254">此部分包含的資料表將顯示所收集有關預存程序之執行的統計資料。</span><span class="sxs-lookup"><span data-stu-id="d342a-254">This section includes a table that shows the statistics that were collected about the stored procedure's executions.</span></span> <span data-ttu-id="d342a-255">資料行如下：</span><span class="sxs-lookup"><span data-stu-id="d342a-255">The columns are as follows:</span></span>  
  
    -   <span data-ttu-id="d342a-256">快取的時間。</span><span class="sxs-lookup"><span data-stu-id="d342a-256">Cached Time.</span></span> <span data-ttu-id="d342a-257">此執行計畫快取的時間。</span><span class="sxs-lookup"><span data-stu-id="d342a-257">The time this execution plan is cached.</span></span> <span data-ttu-id="d342a-258">如果預存程序從計畫快取卸除並重新輸入，每個快取都需要時間。</span><span class="sxs-lookup"><span data-stu-id="d342a-258">If the stored procedure drops out of the plan cache and re-enters, there will be times for each cache.</span></span>  
  
    -   <span data-ttu-id="d342a-259">總 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="d342a-259">Total CPU Time.</span></span> <span data-ttu-id="d342a-260">在分析期間，預存程序所耗用的總 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="d342a-260">The total CPU time that the stored procedure consumed during profiling.</span></span> <span data-ttu-id="d342a-261">此數字愈高，預存程序使用的 CPU 越多。</span><span class="sxs-lookup"><span data-stu-id="d342a-261">The higher this number, the more CPU the stored procedure used.</span></span>  
  
    -   <span data-ttu-id="d342a-262">總執行時間。</span><span class="sxs-lookup"><span data-stu-id="d342a-262">Total Execution Time.</span></span> <span data-ttu-id="d342a-263">在分析期間，預存程序使用的總執行時間量。</span><span class="sxs-lookup"><span data-stu-id="d342a-263">The total amount of execution time the stored procedure used during profiling.</span></span> <span data-ttu-id="d342a-264">此數字和 CPU 時間之間的差異愈高，預存程序使用 CPU 的效率越低。</span><span class="sxs-lookup"><span data-stu-id="d342a-264">The higher the difference between this number and the CPU time is, the less efficiently the stored procedure is using the CPU.</span></span>  
  
    -   <span data-ttu-id="d342a-265">快取遺漏總數。</span><span class="sxs-lookup"><span data-stu-id="d342a-265">Total Cache Missed.</span></span> <span data-ttu-id="d342a-266">在分析期間，預存程序的執行所導致的快取遺漏數 (從實體儲存體讀取)。</span><span class="sxs-lookup"><span data-stu-id="d342a-266">The number of cache misses (reads from physical storage) that is caused by the stored procedure's executions during profiling.</span></span>  
  
    -   <span data-ttu-id="d342a-267">執行計數。</span><span class="sxs-lookup"><span data-stu-id="d342a-267">Execution Count.</span></span> <span data-ttu-id="d342a-268">在分析期間，此預存程序執行的次數。</span><span class="sxs-lookup"><span data-stu-id="d342a-268">The number of times this stored procedure executed during profiling.</span></span>  
  
-   <span data-ttu-id="d342a-269">資料表參考部分</span><span class="sxs-lookup"><span data-stu-id="d342a-269">Table References Section</span></span>  
  
     <span data-ttu-id="d342a-270">此部分包含的資料表是顯示此預存程序所參考的資料表。</span><span class="sxs-lookup"><span data-stu-id="d342a-270">This section includes a table that shows the tables to which this stored procedure refers.</span></span> <span data-ttu-id="d342a-271">將預存程序轉換至原生方式編譯預存程序之前，必須將所有這些資料表轉換為記憶體最佳化資料表，且必須放置在相同的伺服器和資料庫上。</span><span class="sxs-lookup"><span data-stu-id="d342a-271">Before converting the stored procedure into a natively compiled stored procedure, all of these tables must be converted to memory-optimized tables, and they must stay on the same server and database.</span></span>  
  
 <span data-ttu-id="d342a-272">預存程式詳細資料包表的執行統計資料是從[sys. dm_exec_procedure_stats &#40;transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql)收集和匯總。</span><span class="sxs-lookup"><span data-stu-id="d342a-272">Execution Statistics on the stored procedure details report is gathered and aggregated from [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql).</span></span> <span data-ttu-id="d342a-273">參考是從 sys.databases 取得[sql_expression_dependencies &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="d342a-273">The references are obtained from [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql).</span></span>  
  
 <span data-ttu-id="d342a-274">若要查看如何將預存程式轉換成原生編譯預存程式的詳細資料，請使用[Native 編譯](native-compilation-advisor.md)建議程式。</span><span class="sxs-lookup"><span data-stu-id="d342a-274">To see details about how to convert a stored procedure to a natively compiled stored procedure, please use the [Native Compilation Advisor](native-compilation-advisor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d342a-275">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d342a-275">See Also</span></span>  
 [<span data-ttu-id="d342a-276">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="d342a-276">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
