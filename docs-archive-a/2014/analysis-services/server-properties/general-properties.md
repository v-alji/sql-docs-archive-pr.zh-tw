---
title: 一般屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- IdleConnectionTimeout property
- InstanceVisible property
- TempDir property
- AdminTimeout property
- MinIdleSessionTimeout property
- MaxIdleSessionTimeout property
- IdleOrphanSessionTimeout property
- BackupDir property
- CommitTimeout property
- ExternalCommandTimeout property
- Enabled property
- ForceCommitTimeout property
- Port property
- CoordinatorShutdownMode property
- ServerTimeout property
- AllowedBrowsingFolders property
- CoordinatorCancelCount property
- DataDir property
- CoordinatorQueryMaxThreads property
- CoordinatorExecutionMode property
- ExternalConnectionTimeout property
- CollationName property
- EnableFast1033Locale property
- CoordinatorBuildMaxThreads property
- Language property
- StatisticsStoreSize property
- RepositoryConnectionString property
ms.assetid: 88a8117c-396a-469f-a62d-c6f262504021
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca746a1bb57e84cf0f6a8f47622b118c7180eb1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710858"
---
# <a name="general-properties"></a><span data-ttu-id="d6b2f-102">一般屬性</span><span class="sxs-lookup"><span data-stu-id="d6b2f-102">General Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="d6b2f-103">支援下表列出的伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="d6b2f-104">本主題記載 msmdsrv.ini 檔案中，不包含在特定章節中的伺服器屬性，例如 Security、Network 或 ThreadPool。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-104">This topic documents those server properties in the msmdsrv.ini file that are not otherwise included in a specific section, such as Security, Network, or ThreadPool.</span></span> <span data-ttu-id="d6b2f-105">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="d6b2f-106">**適用於** ：多維度與表格式伺服器模式 (除非另有指示)</span><span class="sxs-lookup"><span data-stu-id="d6b2f-106">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="d6b2f-107">非特定類別目錄</span><span class="sxs-lookup"><span data-stu-id="d6b2f-107">Non-Specific Category</span></span>  
 `AdminTimeout`  
 <span data-ttu-id="d6b2f-108">此為帶正負號的 32 位元整數屬性，定義管理員逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-108">A signed 32-bit integer property that defines the administrator timeout in seconds.</span></span> <span data-ttu-id="d6b2f-109">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-109">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="d6b2f-110">此屬性的預設值為零 (0)，表示沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-110">The default value for this property is zero (0), which indicates there is no timeout.</span></span>  
  
 `AllowedBrowsingFolders`  
 <span data-ttu-id="d6b2f-111">字串屬性，以分隔清單指定在 Analysis Services 對話方塊中可儲存、開啟和尋找檔案時可瀏覽的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-111">A string property that specifies in a delimited list the folders that can be browsed when saving, opening, and finding files in Analysis Services dialog boxes.</span></span> <span data-ttu-id="d6b2f-112">Analysis Services 服務帳戶對您加入至清單中的所有資料夾，必須有讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-112">The Analysis Services service account must have read and write permissions to any folders that you add to the list.</span></span>  
  
 `BackupDir`  
 <span data-ttu-id="d6b2f-113">字串屬性，識別預設儲存備份檔案的目錄名稱，在此事件中，不會將路徑指定為 Backup 命令的一部分。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-113">A string property that identifies the name of the directory where backup files are stored by default, in the event a path is not specified as part of the Backup command.</span></span>  
  
 `CollationName`  
 <span data-ttu-id="d6b2f-114">此為識別伺服器定序的字串屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-114">A string property that identifies the server collation.</span></span> <span data-ttu-id="d6b2f-115">如需詳細資訊，請參閱[語言和定序 &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-115">For more information, see [Languages and Collations &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md).</span></span>  
  
 `CommitTimeout`  
 <span data-ttu-id="d6b2f-116">整數屬性，指定伺服器為了認可交易而將等候取得寫入鎖定的時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-116">An integer property that specifies how long (in milliseconds) the server will wait to acquire a write lock for the purpose of committing a transaction.</span></span> <span data-ttu-id="d6b2f-117">通常需要等候期間，因為伺服器必須等候其他鎖定釋放，然後才能取得認可交易的寫入鎖定。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-117">A waiting period is often required because the server must wait for other locks to be released before it can take a write lock that commits the transaction.</span></span>  
  
 <span data-ttu-id="d6b2f-118">此屬性的預設值為零 (0)，表示伺服器會無限期等候。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-118">The default value for this property is zero (0), which indicates that the server will wait indefinitely.</span></span> <span data-ttu-id="d6b2f-119">如需有關鎖定相關屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-119">For more information about lock-related properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorBuildMaxThreads`  
 <span data-ttu-id="d6b2f-120">此為帶正負號的 32 位元整數屬性，定義配置給建立資料分割索引的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-120">A signed 32-bit integer property that defines the maximum number of threads allocated to building partition indexes.</span></span> <span data-ttu-id="d6b2f-121">增加此值就能加速資料分割索引，但要耗用較多記憶體。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-121">Increase this value in order to speed-up partition indexing, at the cost of memory usage.</span></span> <span data-ttu-id="d6b2f-122">如需有關此屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-122">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorCancelCount`  
 <span data-ttu-id="d6b2f-123">此為帶正負號的 32 位元整數屬性，定義伺服器應檢查取消事件是否發生的頻率 (依據內部反覆運算計數)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-123">A signed 32-bit integer property that defines how frequently the server should check whether a Cancel event occurred (based on internal iteration count).</span></span> <span data-ttu-id="d6b2f-124">降低此數字就能以更高的頻率檢查取消事件，但要耗用一般效能。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-124">Decrease this number in order to check for Cancel more frequently, at the expense of general performance.</span></span>  
  
 <span data-ttu-id="d6b2f-125">`CoordinatorCancelCount` 在表格式伺服器模式下將會遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-125">`CoordinatorCancelCount` is ignored in tabular server mode.</span></span>  
  
 `CoordinatorExecutionMode`  
 <span data-ttu-id="d6b2f-126">此為帶正負號的 32 位元整數屬性，定義伺服器會嘗試的最大平行作業數目，包含處理和查詢作業。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-126">A signed 32-bit integer property that defines the maximum number of parallel operations the server will attempt, including processing and querying operations.</span></span> <span data-ttu-id="d6b2f-127">零 (0) 表示伺服器會依據內部演算法決定。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-127">Zero (0) indicates that the server will decide, based on an internal algorithm.</span></span> <span data-ttu-id="d6b2f-128">正數表示總計的最大作業數目。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-128">A positive number indicates the maximum number of operations in total.</span></span> <span data-ttu-id="d6b2f-129">具有反轉符號的負數，表示每個處理器的最大作業數目。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-129">A negative number, with the sign reversed, indicates the maximum number of operations per processor.</span></span>  
  
 <span data-ttu-id="d6b2f-130">`CoordinatorExecutionMode` 在表格式伺服器模式下將會遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-130">`CoordinatorExecutionMode` is ignored in tabular server mode.</span></span>  
  
 <span data-ttu-id="d6b2f-131">此屬性的預設值為 -4，表示伺服器限制為每個處理器 4 個平行作業。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-131">The default value for this property is -4, which indicates the server is limited to 4 parallel operations per processor.</span></span> <span data-ttu-id="d6b2f-132">如需有關此屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-132">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorQueryMaxThreads`  
 <span data-ttu-id="d6b2f-133">此為帶正負號的 32 位元整數屬性，定義查詢解析期間每個資料分割區段的最大執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-133">A signed 32-bit integer property that defines the maximum number of threads per partition segment during query resolution.</span></span> <span data-ttu-id="d6b2f-134">並行使用者的數目愈少此值就愈高，但要耗用較多記憶體。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-134">The fewer the number of concurrent users, the higher this value can be, at the cost of memory.</span></span> <span data-ttu-id="d6b2f-135">相對地，如果有大量的並行使用者，就可能需要降低此值。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-135">Conversely, it may need to be lowered if there are a large number of concurrent users.</span></span>  
  
 `CoordinatorShutdownMode`  
 <span data-ttu-id="d6b2f-136">此為布林值屬性，定義協調器關機模式。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-136">A Boolean property that defines coordinator shutdown mode.</span></span> <span data-ttu-id="d6b2f-137">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-137">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataDir`  
 <span data-ttu-id="d6b2f-138">此為字串屬性，可識別儲存資料的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-138">A string property that identifies the name of the directory where data is stored.</span></span>  
  
 `DeploymentMode`  
 <span data-ttu-id="d6b2f-139">判斷 Analysis Services 伺服器執行個體的運作內容。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-139">Determines the operational context of an Analysis Services server instance.</span></span> <span data-ttu-id="d6b2f-140">在對話方塊、訊息和檔中，此屬性稱為「伺服器模式」。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-140">This property is referred to as 'server mode' in dialog boxes, messages, and documentation.</span></span> <span data-ttu-id="d6b2f-141">根據您在安裝 Analysis Services 時所選取的伺服器模式，此屬性是由 SQL Server 安裝程式所設定。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-141">This property is configured by SQL Server Setup based on the server mode you selected when installing Analysis Services.</span></span> <span data-ttu-id="d6b2f-142">此屬性應該僅被視為內部屬性，永遠使用安裝程式所指定的值。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-142">This property should be considered internal only, always using the value specified by Setup.</span></span>  
  
 <span data-ttu-id="d6b2f-143">這個屬性的有效值包括：</span><span class="sxs-lookup"><span data-stu-id="d6b2f-143">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="d6b2f-144">值</span><span class="sxs-lookup"><span data-stu-id="d6b2f-144">Value</span></span>|<span data-ttu-id="d6b2f-145">描述</span><span class="sxs-lookup"><span data-stu-id="d6b2f-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6b2f-146">0</span><span class="sxs-lookup"><span data-stu-id="d6b2f-146">0</span></span>|<span data-ttu-id="d6b2f-147">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-147">This is the default value.</span></span> <span data-ttu-id="d6b2f-148">它指定多維度模式，用於服務使用 MOLAP、HOLAP 和 ROLAP 儲存以及資料採礦模型的多維度資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-148">It specifies multidimensional mode, used to service multidimensional databases that use MOLAP, HOLAP, and ROLAP storage, as well as data mining models.</span></span>|  
|<span data-ttu-id="d6b2f-149">1</span><span class="sxs-lookup"><span data-stu-id="d6b2f-149">1</span></span>|<span data-ttu-id="d6b2f-150">指定安裝為 PowerPivot for SharePoint 部署一部分的 Analysis Services 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-150">Specifies Analysis Services instances that were installed as part of a PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="d6b2f-151">請勿變更屬於 PowerPivot for SharePoint 安裝一部分之 Analysis Services 執行個體的部署模式屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-151">Do not change the deployment mode property of Analysis Services instance that is part of a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="d6b2f-152">如果您變更模式，PowerPivot 資料將不再於伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-152">PowerPivot data will no longer run on the server if you change the mode.</span></span>|  
|<span data-ttu-id="d6b2f-153">2</span><span class="sxs-lookup"><span data-stu-id="d6b2f-153">2</span></span>|<span data-ttu-id="d6b2f-154">指定用於裝載使用記憶體中儲存或 DirectQuery 儲存之表格式模型資料庫的表格式模式。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-154">Specifies Tabular mode used for hosting tabular model databases that use in-memory storage or DirectQuery storage.</span></span>|  
  
 <span data-ttu-id="d6b2f-155">每個模式彼此之間是獨佔的。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-155">Each mode is exclusive of the other.</span></span> <span data-ttu-id="d6b2f-156">設定為表格式模式的伺服器無法執行包含 Cube 和維度的 Analysis Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-156">A server that is configured for tabular mode cannot run Analysis Services databases that contain cubes and dimensions.</span></span> <span data-ttu-id="d6b2f-157">如果基礎電腦硬體可以支援它，您就可以在相同的電腦上安裝多個 Analysis Services 執行個體，並將每個執行個體設定為使用不同的部署模式。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-157">If the underlying computer hardware can support it, you can install multiple instances of Analysis Services on the same computer and configure each instance to use a different deployment mode.</span></span> <span data-ttu-id="d6b2f-158">請記住，Analysis Services 是非常耗用資源的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-158">Remember that Analysis Services is a resource intensive application.</span></span> <span data-ttu-id="d6b2f-159">建議在相同的系統上，僅針對高階伺服器部署多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-159">Deploying multiple instances on the same system is recommended only for high-end servers.</span></span>  
  
 `EnableFast1033Locale`  
 <span data-ttu-id="d6b2f-160">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-160">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ExternalCommandTimeout`  
 <span data-ttu-id="d6b2f-161">整數屬性，定義命令發出到外部伺服器的逾時 (以秒為單位)，包含關聯式資料來源和外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-161">An integer property that defines the timeout, in seconds, for commands issued to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="d6b2f-162">此屬性的預設值為 3600 (秒)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-162">The default value for this property is 3600 (seconds).</span></span>  
  
 `ExternalConnectionTimeout`  
 <span data-ttu-id="d6b2f-163">整數屬性，定義建立連接到外部伺服器的逾時 (以秒為單位)，包含關聯式資料來源和外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-163">An integer property that defines the timeout, in seconds, for creating connections to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span> <span data-ttu-id="d6b2f-164">如果在連接字串中指定了連接逾時，則會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-164">This property is ignored if a connection timeout is specified on the connection string.</span></span>  
  
 <span data-ttu-id="d6b2f-165">此屬性的預設值為 60 (秒)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-165">The default value for this property is 60 (seconds).</span></span>  
  
 `ForceCommitTimeout`  
 <span data-ttu-id="d6b2f-166">整數屬性，指定在取消目前命令前面的其他命令 (包括進行中的查詢) 之前，寫入認可作業應等候的時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-166">An integer property that specifies how long, in milliseconds, a write commit operation should wait before canceling other commands that preceded the current command, including queries in progress.</span></span> <span data-ttu-id="d6b2f-167">這允許認可交易透過取消較低優先順序的作業 (例如查詢) 來繼續。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-167">This allows the commit transaction to proceed by canceling lower priority operations, such as queries.</span></span>  
  
 <span data-ttu-id="d6b2f-168">此屬性的預設值為 30 秒 (30000 毫秒)，表示在認可交易等候 30 秒之前，不會強制其他命令逾時。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-168">The default value for this property is 30 seconds (30000 milliseconds), which indicates that other commands will not be forced to timeout until the commit transaction has been waiting for 30 seconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6b2f-169">這個事件所取消的查詢和處理序將報告下列錯誤訊息："`Server: The operation has been cancelled`"</span><span class="sxs-lookup"><span data-stu-id="d6b2f-169">Queries and processes cancelled by this event will report the following error message: "`Server: The operation has been cancelled`"</span></span>  
  
 <span data-ttu-id="d6b2f-170">如需有關此屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](https://go.microsoft.com/fwlink/?LinkID=225539)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-170">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d6b2f-171">`ForceCommitTimeout` 適用於 Cube 處理命令和回寫作業。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-171">`ForceCommitTimeout` applies to cube processing commands and to writeback operations.</span></span>  
  
 `IdleConnectionTimeout`  
 <span data-ttu-id="d6b2f-172">整數屬性，指定處於非使用狀態之連接的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-172">An integer property that specifies a timeout, in seconds, for connections that are inactive.</span></span>  
  
 <span data-ttu-id="d6b2f-173">此屬性的預設值為零 (0)，表示閒置連接不會逾時。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-173">The default value for this property is zero (0), which indicates that idle connections will not be timed out.</span></span>  
  
 `IdleOrphanSessionTimeout`  
 <span data-ttu-id="d6b2f-174">整數屬性，定義被遺棄的工作階段要在伺服器記憶體中保留多久 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-174">An integer property that defines how long, in seconds, orphaned sessions will be retained in server memory.</span></span> <span data-ttu-id="d6b2f-175">被遺棄的工作階段是不再具有相關聯連接的工作階段。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-175">An orphaned session is one that no longer has an associated connection.</span></span> <span data-ttu-id="d6b2f-176">預設值是 120 秒。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-176">The default is 120 seconds.</span></span>  
  
 `InstanceVisible`  
 <span data-ttu-id="d6b2f-177">此為布林屬性，表示是否可以看見伺服器執行個體，以探索來自 SQL Server Browser 服務的執行個體要求。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-177">A Boolean property that indicates whether the server instance is visible to discover instance requests from SQL Server Browser service.</span></span> <span data-ttu-id="d6b2f-178">預設值為 True。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-178">The default is True.</span></span> <span data-ttu-id="d6b2f-179">如果將屬性設定為 false，則執行個體對 SQL Server Browser 為不可見。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-179">If you set it to false, the instance is not visible to SQL Server Browser.</span></span>  
  
 `Language`  
 <span data-ttu-id="d6b2f-180">此為定義語言的字串屬性，包含錯誤訊息和數字格式。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-180">A string property that defines the language, including error messages and number formatting.</span></span> <span data-ttu-id="d6b2f-181">此屬性會覆寫 CollationName 屬性。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-181">This property overrides the CollationName property.</span></span>  
  
 <span data-ttu-id="d6b2f-182">此屬性的預設值是空白，表示 CollationName 屬性會定義語言。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-182">The default value for this property is blank, which indicates that the CollationName property defines the language.</span></span>  
  
 `LogDir`  
 <span data-ttu-id="d6b2f-183">此為字串屬性，識別包含伺服器記錄檔的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-183">A string property that identifies the name of the directory that contains server logs.</span></span> <span data-ttu-id="d6b2f-184">這個屬性只適用於當記錄會儲存到磁碟檔案，而非資料庫資料表時 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-184">This property only applies when disk files are used for logging, as opposed to database tables (the default behavior).</span></span>  
  
 `MaxIdleSessionTimeout`  
 <span data-ttu-id="d6b2f-185">整數屬性，定義最長閒置工作階段逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-185">An integer property that defines the maximum idle session timeout, in seconds.</span></span> <span data-ttu-id="d6b2f-186">預設值為零 (0) ，表示會話永遠不會超時。不過，如果伺服器是在資源限制之下，則仍會移除閒置會話。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-186">The default is zero (0), indicating that sessions are never timed out. However, idle sessions will still be removed if the server is under resource constraints.</span></span>  
  
 `MinIdleSessionTimeout`  
 <span data-ttu-id="d6b2f-187">整數屬性，定義最短閒置工作階段逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-187">An integer property that defines the minimum time, in seconds, that idle sessions will timeout.</span></span> <span data-ttu-id="d6b2f-188">預設值是 2700 秒。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-188">The default is 2700 seconds.</span></span> <span data-ttu-id="d6b2f-189">此時間過期之後，就允許伺服器結束閒置工作階段，但只有需要記憶體時才會如此做。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-189">After this time expires, the server is permitted to end the idle session, but will only do so as memory is needed.</span></span>  
  
 `Port`  
 <span data-ttu-id="d6b2f-190">整數屬性，定義伺服器接聽用戶端連接的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-190">An integer property that defines the port number on which server will listen for client connections.</span></span> <span data-ttu-id="d6b2f-191">如果沒有設定，伺服器會動態地找到第一個未使用的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-191">If not set, server dynamically finds first unused port.</span></span>  
  
 <span data-ttu-id="d6b2f-192">此屬性的預設值為零 (0)，因而會預設為通訊埠 2383。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-192">The default value for this property is zero (0), which in turn defaults to port 2383.</span></span> <span data-ttu-id="d6b2f-193">如需通訊埠組態的詳細資訊，請參閱＜ [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-193">For more information about port configuration, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
 `ServerTimeout`  
 <span data-ttu-id="d6b2f-194">整數，定義查詢的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-194">An integer that defines the timeout, in seconds, for queries.</span></span> <span data-ttu-id="d6b2f-195">預設值為 3600 秒 (或 60 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-195">The default is 3600 seconds (or 60 minutes).</span></span> <span data-ttu-id="d6b2f-196">零 (0) 指定任何查詢都不會逾時。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-196">Zero (0) specifies that no queries will timeout.</span></span>  
  
 `TempDir`  
 <span data-ttu-id="d6b2f-197">此為字串屬性，指定儲存暫存檔的位置，在處理、還原以及其他作業期間使用這些暫存檔。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-197">A string property that specifies the location for storing temporary files used during processing, restoring, and other operations.</span></span> <span data-ttu-id="d6b2f-198">此屬性的預設值是由安裝程式所決定的。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-198">The default value for this property is determined by setup.</span></span> <span data-ttu-id="d6b2f-199">如果未指定，則預設值為 Data 目錄。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-199">If not specified, the default is the Data directory.</span></span>  
  
## <a name="requestprioritization-category"></a><span data-ttu-id="d6b2f-200">RequestPrioritization 類別目錄</span><span class="sxs-lookup"><span data-stu-id="d6b2f-200">RequestPrioritization Category</span></span>  
 `Enabled`  
 <span data-ttu-id="d6b2f-201">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-201">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `StatisticsStoreSize`  
 <span data-ttu-id="d6b2f-202">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="d6b2f-202">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b2f-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6b2f-203">See Also</span></span>  
 <span data-ttu-id="d6b2f-204">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="d6b2f-204">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="d6b2f-205">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="d6b2f-205">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
