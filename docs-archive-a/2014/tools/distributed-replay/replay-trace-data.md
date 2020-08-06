---
title: 重新執行追蹤資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 19ff5285-fb9d-4fd1-97c4-ec72c311c384
author: stevestein
ms.author: sstein
ms.openlocfilehash: d6c929d7c617ba4dc496eedabaccbbe50da32d08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585738"
---
# <a name="replay-trace-data"></a><span data-ttu-id="9ee39-102">重新執行追蹤資料</span><span class="sxs-lookup"><span data-stu-id="9ee39-102">Replay Trace Data</span></span>
  <span data-ttu-id="9ee39-103">在您已經備妥輸入追蹤資料之後，就可以使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 功能啟動分散式重新執行。</span><span class="sxs-lookup"><span data-stu-id="9ee39-103">You can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature after you have prepared the input trace data.</span></span> <span data-ttu-id="9ee39-104">如需詳細資訊，請參閱 [準備輸入追蹤資料](prepare-the-input-trace-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9ee39-104">For more information, see [Prepare the Input Trace Data](prepare-the-input-trace-data.md).</span></span>  
  
 <span data-ttu-id="9ee39-105">您可以使用管理工具的 [重新執行]  選項以起始 Distributed Replay 的事件重新執行階段。</span><span class="sxs-lookup"><span data-stu-id="9ee39-105">Use the administration tool **replay** option to initiate the event replay stage of the distributed replay.</span></span> <span data-ttu-id="9ee39-106">這個階段是由兩個部分組成：追蹤資料分派以及分散式重新執行的啟動和同步處理。</span><span class="sxs-lookup"><span data-stu-id="9ee39-106">This stage consists of two parts: the trace data dispatch and the starting and synchronizing of the distributed replay.</span></span>  
  
 <span data-ttu-id="9ee39-107">![分散式事件重新執行](../../database-engine/media/eventreplay.gif "分散式事件重新執行")</span><span class="sxs-lookup"><span data-stu-id="9ee39-107">![Distributed Event Replay](../../database-engine/media/eventreplay.gif "Distributed Event Replay")</span></span>  
  
 <span data-ttu-id="9ee39-108">您可以在下列其中一種順序模式中重新執行追蹤資料：壓力模式或同步處理模式。</span><span class="sxs-lookup"><span data-stu-id="9ee39-108">You can replay trace data in one of two sequencing modes: stress mode or synchronization mode.</span></span> <span data-ttu-id="9ee39-109">預設行為是在壓力模式中重新執行追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="9ee39-109">The default behavior is to replay trace data in stress mode.</span></span> <span data-ttu-id="9ee39-110">如需有關事件重新執行階段和順序模式的詳細資訊，請參閱＜ [SQL Server Distributed Replay](sql-server-distributed-replay.md)＞</span><span class="sxs-lookup"><span data-stu-id="9ee39-110">For more information about the event replay stage and sequencing modes, see [SQL Server Distributed Replay](sql-server-distributed-replay.md)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ee39-111">輸入追蹤資料必須在相容於 Distributed Replay 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中擷取。</span><span class="sxs-lookup"><span data-stu-id="9ee39-111">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="9ee39-112">輸入追蹤資料也必須相容於您要針對它重新執行追蹤資料的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="9ee39-112">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="9ee39-113">如需有關版本需求的詳細資訊，請參閱＜ [Distributed Replay Requirements](distributed-replay-requirements.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9ee39-113">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-replay-the-trace"></a><span data-ttu-id="9ee39-114">若要重新執行追蹤</span><span class="sxs-lookup"><span data-stu-id="9ee39-114">To replay the trace</span></span>  
  
1.  <span data-ttu-id="9ee39-115">**(選擇性) 修改重新執行組態設定**：如果您想要修改重新執行組態設定 (例如順序模式和各種調整值)，您必須修改以 XML 為基礎之重新執行組態檔 `DReplay.exe.replay.config` 的 `<ReplayOptions>` 元素。</span><span class="sxs-lookup"><span data-stu-id="9ee39-115">**(Optional) Modify replay configuration settings**: If you want to modify the replay configuration settings, such as the sequencing mode and various scaling values, you must modify the `<ReplayOptions>` element of the XML-based replay configuration file `DReplay.exe.replay.config`.</span></span> <span data-ttu-id="9ee39-116">此外，您也可以修改 `<OutputOptions>` 元素來指定輸出設定，例如是否要記錄資料列計數。</span><span class="sxs-lookup"><span data-stu-id="9ee39-116">You can also modify the `<OutputOptions>` element to specify output settings, such as whether to record the row count.</span></span> <span data-ttu-id="9ee39-117">如果您要修改重新執行組態檔，我們建議您修改複本，而不是原始版本。</span><span class="sxs-lookup"><span data-stu-id="9ee39-117">If you modify the replay configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="9ee39-118">若要修改設定，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9ee39-118">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="9ee39-119">建立預設重新執行組態檔 `DReplay.exe.replay.config`的複本，並重新命名新的檔案。</span><span class="sxs-lookup"><span data-stu-id="9ee39-119">Make a copy of the default replay configuration file, `DReplay.exe.replay.config`, and rename the new file.</span></span> <span data-ttu-id="9ee39-120">預設重新執行組態檔位於管理工具的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="9ee39-120">The default replay configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="9ee39-121">修改新組態檔中的重新執行組態設定。</span><span class="sxs-lookup"><span data-stu-id="9ee39-121">Modify the replay configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="9ee39-122">當起始事件重新執行階段 (下一步) 時，使用 [重新執行] 選項的 *config_file* 參數指定已修改組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="9ee39-122">When initiating the event replay stage (the next step), use the *config_file* parameter of the **replay** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="9ee39-123">如需重新執行組態檔的詳細資訊，請參閱 [設定 Distributed Replay](configure-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="9ee39-123">For more information about the replay configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="9ee39-124">**開始事件重新執行階段**：若要啟動 Distributed Replay，您必須透過 [重新執行] 選項執行系統管理工具。</span><span class="sxs-lookup"><span data-stu-id="9ee39-124">**Initiate the event replay stage**: To start the distributed replay, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="9ee39-125">如需詳細資訊，請參閱[重新執行選項 &#40;Distributed Replay 管理工具&#41;](replay-option-distributed-replay-administration-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="9ee39-125">For more information, see [Replay Option &#40;Distributed Replay Administration Tool&#41;](replay-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="9ee39-126">開啟 Windows 命令提示字元公用程式 (`CMD.exe`)，並瀏覽至 Distributed Replay 管理工具 (`DReplay.exe`) 的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="9ee39-126">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="9ee39-127">(選擇性) 使用 *controller* 參數 **-m**指定控制器 (如果控制器服務是在與管理工具不同的電腦上執行)。</span><span class="sxs-lookup"><span data-stu-id="9ee39-127">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="9ee39-128">使用 *controller_working_directory* 參數 **-d**，指定中繼檔案在前置處理階段期間儲存在控制器上的位置。</span><span class="sxs-lookup"><span data-stu-id="9ee39-128">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file was saved on the controller during the preprocess stage.</span></span>  
  
    4.  <span data-ttu-id="9ee39-129">(選擇性) 使用 **-o** 參數，在每個用戶端的結果追蹤檔案中擷取重新執行活動。</span><span class="sxs-lookup"><span data-stu-id="9ee39-129">(Optional) Use the **-o** parameter to capture the replay activity in a result trace file on each client.</span></span>  
  
    5.  <span data-ttu-id="9ee39-130">(選擇性) 使用 *target_server* 參數 **-s**，指定 Distributed Replay Client 應該重新執行追蹤工作負載所在的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ee39-130">(Optional) Use the *target_server* parameter, **-s**, to specify the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] where the distributed replay clients should replay the trace workload.</span></span> <span data-ttu-id="9ee39-131">如果您使用了 `<Server>` 元素，在重新執行組態檔的 `<ReplayOptions>` 元素中指定目標伺服器，就不需要這個參數。</span><span class="sxs-lookup"><span data-stu-id="9ee39-131">This parameter is not required if you used the `<Server>` element to specify the target server in the `<ReplayOptions>` element of the replay configuration file.</span></span>  
  
    6.  <span data-ttu-id="9ee39-132">使用 *clients* 參數 **-w**，指定應該參與重新執行的 Distributed Replay Client。</span><span class="sxs-lookup"><span data-stu-id="9ee39-132">Use the *clients* parameter, **-w**, to specify the distributed replay clients that should participate in the replay.</span></span> <span data-ttu-id="9ee39-133">然後，列出用戶端電腦名稱 (以逗號隔開)。</span><span class="sxs-lookup"><span data-stu-id="9ee39-133">List the client computer names, separated by commas.</span></span> <span data-ttu-id="9ee39-134">注意:不允許 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="9ee39-134">Note: IP addresses are not allowed.</span></span>  
  
    7.  <span data-ttu-id="9ee39-135">(選擇性) 使用 *config_file* 參數 **-c**，指定重新執行組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="9ee39-135">(Optional) Use the *config_file* parameter, **-c**, to specify location of the replay configuration file.</span></span> <span data-ttu-id="9ee39-136">如果已修改預設重新執行組態檔的複本，請使用此參數指向新的組態檔。</span><span class="sxs-lookup"><span data-stu-id="9ee39-136">Use this parameter to point to the new configuration file if you have modified a copy of the default replay configuration file.</span></span>  
  
    8.  <span data-ttu-id="9ee39-137">(選擇性) 使用 *status_interval* 參數 **-f**，指定是否要讓管理工具以不同於 30 秒的頻率顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="9ee39-137">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency other than 30 seconds.</span></span>  
  
     <span data-ttu-id="9ee39-138">例如，下列語法會在控制器服務所在的同一部電腦上起始重新執行階段、使用位於 `c:\WorkingDir`的控制器工作目錄、在每個參與的用戶端上擷取重新執行活動、使用 `client1` 和 `client2` 用戶端來進行重新執行，並且從位於 `c:\modifiedreplay.config`的已修改重新執行組態檔中取得其餘重新執行組態設定：</span><span class="sxs-lookup"><span data-stu-id="9ee39-138">For example, the following syntax initiates the replay stage on the same computer as the controller service, uses a controller working directory located at `c:\WorkingDir`, captures the replay activity on each participating client, uses clients `client1` and `client2` to perform the replay, and obtains the remaining replay configuration settings from a modified replay configuration file located at `c:\modifiedreplay.config`:</span></span>  
  
     `dreplay replay -d c:\WorkingDir -o -w client1,client2 -c c:\modifiedreplay.config`  
  
3.  <span data-ttu-id="9ee39-139">當分散式重新執行完成時，管理工具就會傳回摘要資訊。</span><span class="sxs-lookup"><span data-stu-id="9ee39-139">When the distributed replay has finished, the administration tool returns summary information.</span></span> <span data-ttu-id="9ee39-140">如果您已指定 **-o** 選項，重新執行活動就已經儲存在每個用戶端的結果追蹤檔案中。</span><span class="sxs-lookup"><span data-stu-id="9ee39-140">If you specified the **-o** option, the replay activity has been saved in result trace files on each client.</span></span> <span data-ttu-id="9ee39-141">如需結果追蹤檔案的詳細資訊，請參閱 [檢閱重新執行結果](review-the-replay-results.md)。</span><span class="sxs-lookup"><span data-stu-id="9ee39-141">For more information about the result trace files, see [Review the Replay Results](review-the-replay-results.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee39-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ee39-142">See Also</span></span>  
 <span data-ttu-id="9ee39-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="9ee39-143">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="9ee39-144">[管理工具命令列選項 &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="9ee39-144">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="9ee39-145">設定 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="9ee39-145">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
