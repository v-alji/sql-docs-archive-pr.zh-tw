---
title: CDC 控制工作編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdccontroltask.config.f1
ms.assetid: 4f09d040-9ec8-4aaa-b684-f632d571f0a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6b60f2a9126dbbda934124b39f36ccd90b4e6cc6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599633"
---
# <a name="cdc-control-task-editor"></a><span data-ttu-id="5cd77-102">CDC 控制工作編輯器</span><span class="sxs-lookup"><span data-stu-id="5cd77-102">CDC Control Task Editor</span></span>
  <span data-ttu-id="5cd77-103">使用 **[CDC 控制工作編輯器]** 對話方塊，即可設定 CDC 控制工作。</span><span class="sxs-lookup"><span data-stu-id="5cd77-103">Use the **CDC Control Task Editor** dialog box to configure the CDC Control task.</span></span> <span data-ttu-id="5cd77-104">CDC 控制工作組態包括定義 CDC 資料庫的連接、CDC 工作作業，以及狀態管理資訊。</span><span class="sxs-lookup"><span data-stu-id="5cd77-104">The CDC Control task configuration includes defining a connection to the CDC database, the CDC task operation and the state management information.</span></span>  
  
 <span data-ttu-id="5cd77-105">若要了解有關 CDC 控制工作的詳細資訊，請參閱＜ [CDC Control Task](control-flow/cdc-control-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5cd77-105">To learn more about the CDC Control task, see [CDC Control Task](control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="5cd77-106">**若要開啟 CDC 控制工作編輯器**</span><span class="sxs-lookup"><span data-stu-id="5cd77-106">**To open the CDC Control Task Editor**</span></span>  
  
1.  <span data-ttu-id="5cd77-107">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 CDC 控制工作的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="5cd77-107">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the CDC Control task.</span></span>  
  
2.  <span data-ttu-id="5cd77-108">在 [控制流程]\*\*\*\* 索引標籤中，按兩下 CDC 控制工作。</span><span class="sxs-lookup"><span data-stu-id="5cd77-108">On the **Control Flow** tab, double-click the CDC Control task.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5cd77-109">選項</span><span class="sxs-lookup"><span data-stu-id="5cd77-109">Options</span></span>  
 <span data-ttu-id="5cd77-110">**SQL Server CDC 資料庫 ADO.NET 連接管理員**</span><span class="sxs-lookup"><span data-stu-id="5cd77-110">**SQL Server CDC database ADO.NET connection manager**</span></span>  
 <span data-ttu-id="5cd77-111">從清單中選取現有的連接管理員，或按一下 [新增]  建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="5cd77-111">Select an existing connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="5cd77-112">此連接必須指向啟用 CDC 而且包含選取之變更資料表的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cd77-112">The connection must be to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that is enabled for CDC and where the selected change table is located.</span></span>  
  
 <span data-ttu-id="5cd77-113">**CDC 控制作業**</span><span class="sxs-lookup"><span data-stu-id="5cd77-113">**CDC Control Operation**</span></span>  
 <span data-ttu-id="5cd77-114">選取要針對此工作執行的作業。</span><span class="sxs-lookup"><span data-stu-id="5cd77-114">Select the operation to run for this task.</span></span> <span data-ttu-id="5cd77-115">所有作業都會使用儲存在 SSIS 封裝變數中的狀態變數，這個變數會儲存狀態並且在封裝中的不同元件之間傳遞狀態。</span><span class="sxs-lookup"><span data-stu-id="5cd77-115">All operations use the state variable that is stored in an SSIS package variable that stores the state and passes it between the different components in the package.</span></span>  
  
-   <span data-ttu-id="5cd77-116">**標記初始載入開始**：此作業是在從不含快照集的使用中資料庫執行初始載入時使用。</span><span class="sxs-lookup"><span data-stu-id="5cd77-116">**Mark initial load start**: This operation is used when executing an initial load from an active database without a snapshot.</span></span> <span data-ttu-id="5cd77-117">初始載入封裝開始讀取來源資料表之前，系統會在初始載入封裝的開頭叫用此作業，以便在來源資料庫中記錄目前的 LSN。</span><span class="sxs-lookup"><span data-stu-id="5cd77-117">It is invoked at the beginning of an initial-load package to record the current LSN in the source database before the initial-load package starts reading the source tables.</span></span> <span data-ttu-id="5cd77-118">這需要來源資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="5cd77-118">This requires a connection to the source database.</span></span>  
  
     <span data-ttu-id="5cd77-119">如果您在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (亦即非 Oracle) 上工作時選取了 [標記初始載入開始]\*\*\*\*，連接管理員中指定的使用者就必須是 **db_owner** 或**系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="5cd77-119">If you select **Mark Initial Load Start** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="5cd77-120">**標記初始載入結束**：此作業是在從不含快照集的使用中資料庫執行初始載入時使用。</span><span class="sxs-lookup"><span data-stu-id="5cd77-120">**Mark initial load end**: This operation is used when executing an initial load from an active database without a snapshot.</span></span> <span data-ttu-id="5cd77-121">初始載入封裝讀取來源資料表完成之後，系統會在初始載入封裝的結尾叫用此作業，以便在來源資料庫中記錄目前的 LSN。</span><span class="sxs-lookup"><span data-stu-id="5cd77-121">It is invoked at the end of an initial-load package to record the current LSN in the source database after the initial-load package finished reading the source tables.</span></span> <span data-ttu-id="5cd77-122">這個 LSN 的決定方式如下：記錄進行此作業時的目前時間，然後在 CDC 資料庫中查詢 `cdc.lsn_time_`mapping 資料表，尋找該時間之後發生的變更。</span><span class="sxs-lookup"><span data-stu-id="5cd77-122">This LSN is determined by recording nthe current time when this operation occurred and then querying the `cdc.lsn_time_`mapping table in the CDC database looking for a change that occurred after that time</span></span>  
  
     <span data-ttu-id="5cd77-123">如果您在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (亦即非 Oracle) 上工作時選取了 [標記初始載入結束]\*\*\*\*，連接管理員中指定的使用者就必須是 **db_owner** 或**系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="5cd77-123">If you select **Mark Initial Load End** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="5cd77-124">**標記 CDC 開始**：此作業會在從快照集資料庫或靜止資料庫進行初始載入時使用。</span><span class="sxs-lookup"><span data-stu-id="5cd77-124">**Mark CDC start**: This operation is used when then the initial load is made from a snapshot database or from a quiescence database.</span></span> <span data-ttu-id="5cd77-125">系統會在初始載入封裝中的任何時間點叫用此作業。</span><span class="sxs-lookup"><span data-stu-id="5cd77-125">It is invoked at any point within the initial load package.</span></span> <span data-ttu-id="5cd77-126">此作業所接受的參數可以是快照集 LSN、快照集資料庫的名稱 (從中自動衍生快照集 LSN)，也可以保留空白 (在此情況中，目前資料庫 LSN 就會當做變更處理封裝的啟始 LSN 使用)。</span><span class="sxs-lookup"><span data-stu-id="5cd77-126">The operation accepts a parameter that can be a snapshot LSN, a name of a snapshot database (from which the snapshot LSN will be derived automatically) or it can be left empty, in which case the current database LSN is used as the start LSN for the change processing package.</span></span>  
  
     <span data-ttu-id="5cd77-127">此作業是用來取代「標記初始載入開始/結束」作業。</span><span class="sxs-lookup"><span data-stu-id="5cd77-127">This operation is used instead of the Mark Initial Load Start/End operations.</span></span>  
  
     <span data-ttu-id="5cd77-128">如果您在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (亦即非 Oracle) 上工作時選取了 [標記 CDC 開始]\*\*\*\*，連接管理員中指定的使用者就必須是 **db_owner** 或**系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="5cd77-128">If you select **Mark CDC Start** when working on [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] CDC (that is, not Oracle) the user specified in the connection manager must be either  **db_owner** or **sysadmin**.</span></span>  
  
-   <span data-ttu-id="5cd77-129">**取得處理範圍**：此作業是在叫用使用 CDC 來源資料流程的資料流程之前用於變更處理封裝中。</span><span class="sxs-lookup"><span data-stu-id="5cd77-129">**Get processing range**: This operation is used in a change processing package before invoking the data flow that uses the CDC Source data flow.</span></span> <span data-ttu-id="5cd77-130">叫用此作業時，它會建立 CDC 來源資料流程所讀取的 LSN 範圍。</span><span class="sxs-lookup"><span data-stu-id="5cd77-130">It establishes a range of LSNs that the CDC Source data flow reads when invoked.</span></span> <span data-ttu-id="5cd77-131">此範圍會儲存在資料流程處理期間 CDC 來源所使用的 SSIS 封裝變數中。</span><span class="sxs-lookup"><span data-stu-id="5cd77-131">The range is stored in an SSIS package variable that is used by the CDC Source during data-flow processing.</span></span>  
  
     <span data-ttu-id="5cd77-132">如需儲存之可能 CDC 狀態的詳細資訊，請參閱 [定義狀態變數](data-flow/define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="5cd77-132">For more information about the possible CDC states that are stored, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
-   <span data-ttu-id="5cd77-133">**標記處理的範圍**：此作業是在 CDC 回合結束時 (CDC 資料流程順利完成之後) 用於變更處理封裝中，以便記錄 CDC 回合中完整處理的最後一個 LSN。</span><span class="sxs-lookup"><span data-stu-id="5cd77-133">**Mark processed range**: This operation is used in a change processing package at the end of a  CDC run (after the CDC data flow is completed successfully) to record the last LSN that was fully processed in the CDC run.</span></span> <span data-ttu-id="5cd77-134">下次執行 `GetProcessingRange` 時，這個位置就會決定下一個處理範圍的開頭。</span><span class="sxs-lookup"><span data-stu-id="5cd77-134">The next time `GetProcessingRange` is executed, this position determines the start of the next processing range.</span></span>  
  
-   <span data-ttu-id="5cd77-135">**重設 CDC 狀態**：此作業是用來重設與目前 CDC 內容相關聯的持續性 CDC 狀態。</span><span class="sxs-lookup"><span data-stu-id="5cd77-135">**Reset CDC state**: This operation is used to reset the persistent CDC state associated with the current CDC context.</span></span> <span data-ttu-id="5cd77-136">執行此作業之後，LSN 時間戳記 `sys.fn_cdc_get_max_lsn` 資料表中的目前最大 LSN 就會變成下一個處理範圍的範圍開頭。</span><span class="sxs-lookup"><span data-stu-id="5cd77-136">After this operation is run, the current maximum LSN from the LSN-timestamp `sys.fn_cdc_get_max_lsn` table becomes the start of the range for the next processing range.</span></span> <span data-ttu-id="5cd77-137">此作業需要來源資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="5cd77-137">This operation requires a connection to the source database.</span></span>  
  
     <span data-ttu-id="5cd77-138">此作業使用時機的範例如下：當您只想要處理新建立的變更記錄，而忽略所有舊的變更記錄時。</span><span class="sxs-lookup"><span data-stu-id="5cd77-138">An example of when this operation is used is when you want to process only the newly created change records and ignore all old change records.</span></span>  
  
 <span data-ttu-id="5cd77-139">**包含 CDC 狀態的變數**</span><span class="sxs-lookup"><span data-stu-id="5cd77-139">**Variable containing the CDC state**</span></span>  
 <span data-ttu-id="5cd77-140">選取儲存工作作業之狀態資訊的 SSIS 封裝變數。</span><span class="sxs-lookup"><span data-stu-id="5cd77-140">Select the SSIS package variable that stores the state information for the task operation.</span></span> <span data-ttu-id="5cd77-141">您應該在開始之前定義變數。</span><span class="sxs-lookup"><span data-stu-id="5cd77-141">You should define a variable before you begin.</span></span> <span data-ttu-id="5cd77-142">如果您選取 **[自動狀態持續性]**，系統就會自動載入並儲存狀態變數。</span><span class="sxs-lookup"><span data-stu-id="5cd77-142">If you select **Automatic state persistence**, the state variable is loaded and saved automatically.</span></span>  
  
 <span data-ttu-id="5cd77-143">如需定義狀態變數的詳細資訊，請參閱 [定義狀態變數](data-flow/define-a-state-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="5cd77-143">For more information about defining the state variable, see [Define a State Variable](data-flow/define-a-state-variable.md).</span></span>  
  
 <span data-ttu-id="5cd77-144">**要啟動 CDC 的 SQL Server LSN/快照集名稱:**</span><span class="sxs-lookup"><span data-stu-id="5cd77-144">**SQL Server LSN to start the CDC/Snapshot name:**</span></span>  
 <span data-ttu-id="5cd77-145">輸入目前的來源資料庫 LSN 或從中執行初始載入以決定 CDC 啟動位置之快照集資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="5cd77-145">Type the current source database LSN or the name of the snapshot database from which the initial load is performed to determine where the CDC starts.</span></span> <span data-ttu-id="5cd77-146">只有當 **[CDC 控制作業]** 設定為 **[標記 CDC 開始]** 時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="5cd77-146">This is available only if the **CDC Control Operation** is set to **Mark CDC Start**.</span></span>  
  
 <span data-ttu-id="5cd77-147">如需有關這些作業的詳細資訊，請參閱＜ [CDC Control Task](control-flow/cdc-control-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5cd77-147">For more information about these operations, see [CDC Control Task](control-flow/cdc-control-task.md)</span></span>  
  
 <span data-ttu-id="5cd77-148">**自動在資料庫資料表中儲存狀態**</span><span class="sxs-lookup"><span data-stu-id="5cd77-148">**Automatically store state in a database table**</span></span>  
 <span data-ttu-id="5cd77-149">選取此核取方塊，可讓 CDC 控制工作自動在指定資料庫所包含的狀態資料表中載入並儲存 CDC 狀態。</span><span class="sxs-lookup"><span data-stu-id="5cd77-149">Select this check box for the CDC Control task to automatically handle loading and storing the CDC state in a state table contained in the specified database.</span></span> <span data-ttu-id="5cd77-150">如果沒有選取此選項，開發人員就必須在封裝啟動時載入 CDC 狀態，而且每次 CDC 狀態變更時都必須儲存狀態。</span><span class="sxs-lookup"><span data-stu-id="5cd77-150">When not selected, the developer must load the CDC State when the package starts and save it whenever the CDC State changes.</span></span>  
  
 <span data-ttu-id="5cd77-151">**儲存狀態之資料庫的連接管理員**</span><span class="sxs-lookup"><span data-stu-id="5cd77-151">**Connection manager for the database where the state is stored**</span></span>  
 <span data-ttu-id="5cd77-152">從清單中選取現有的 ADO.NET 連接管理員，或按一下 [新增] 建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="5cd77-152">Select an existing ADO.NET connection manager from the list, or click New to create a new connection.</span></span> <span data-ttu-id="5cd77-153">這個連接會指向包含狀態資料表的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5cd77-153">This connection is to a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database that contains the State table.</span></span> <span data-ttu-id="5cd77-154">狀態資料表包含狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="5cd77-154">The State table contains the State information.</span></span>  
  
 <span data-ttu-id="5cd77-155">只有當您已選取 **[自動狀態持續性]** 時，才能使用這個選項，而且它是必要參數。</span><span class="sxs-lookup"><span data-stu-id="5cd77-155">This is available only if **Automatic state persistence** is selected and it is a required parameter.</span></span>  
  
 <span data-ttu-id="5cd77-156">**要用於儲存狀態的資料表**</span><span class="sxs-lookup"><span data-stu-id="5cd77-156">**Table to use for storing state**</span></span>  
 <span data-ttu-id="5cd77-157">輸入要用於儲存 CDC 狀態之狀態資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="5cd77-157">Type the name of the state table to be used for storing the CDC state.</span></span> <span data-ttu-id="5cd77-158">指定的資料表必須具有兩個名為 **name** 和 **state** 的資料行，而且這兩個資料行的資料類型都必須是 **varchar (256)**。</span><span class="sxs-lookup"><span data-stu-id="5cd77-158">The table specified must have two columns called **name** and **state** and both columns must be of the data type **varchar (256)**.</span></span>  
  
 <span data-ttu-id="5cd77-159">您可以選擇性地選取 **[新增]** 取得 SQL 指令碼，以便建置含有必要資料行的新狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="5cd77-159">You can optionally select **New** to get an SQL script that builds a new State table with the required columns.</span></span> <span data-ttu-id="5cd77-160">選取 **[自動狀態持續性]** 時，開發人員必須根據上述需求建立狀態資料表。</span><span class="sxs-lookup"><span data-stu-id="5cd77-160">When **Automatic state persistence** is selected, the developer must create a state table according to the requirements listed above.</span></span>  
  
 <span data-ttu-id="5cd77-161">只有當您已選取 **[自動狀態持續性]** 時，才能使用這個選項，而且它是必要參數。</span><span class="sxs-lookup"><span data-stu-id="5cd77-161">This is available only if **Automatic state persistence** is selected and it is a required parameter.</span></span>  
  
 <span data-ttu-id="5cd77-162">**狀態名稱**</span><span class="sxs-lookup"><span data-stu-id="5cd77-162">**State name**</span></span>  
 <span data-ttu-id="5cd77-163">輸入要與持續性 CDC 狀態產生關聯的名稱。</span><span class="sxs-lookup"><span data-stu-id="5cd77-163">Type a name to associate with the persistent CDC state.</span></span> <span data-ttu-id="5cd77-164">使用相同 CDC 內容的完整載入和 CDC 封裝都將指定一般狀態名稱。</span><span class="sxs-lookup"><span data-stu-id="5cd77-164">The full load and CDC packages that work with the same CDC context will specify a common state name.</span></span> <span data-ttu-id="5cd77-165">這個名稱是用於查閱狀態資料表中的狀態資料列。</span><span class="sxs-lookup"><span data-stu-id="5cd77-165">This name is used for looking up the state row in the state table</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd77-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cd77-166">See Also</span></span>  
 [<span data-ttu-id="5cd77-167">CDC 控制工作自訂屬性</span><span class="sxs-lookup"><span data-stu-id="5cd77-167">CDC Control Task Custom Properties</span></span>](control-flow/cdc-control-task-custom-properties.md)  
  
  
