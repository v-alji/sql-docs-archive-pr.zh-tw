---
title: 準備輸入追蹤資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c14fd3d2-5770-47c2-a851-cc13ddbc9bf5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c13dddcf29f93940fa4eae6b2849dcfb278ae3b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703645"
---
# <a name="prepare-the-input-trace-data"></a><span data-ttu-id="7d846-102">準備輸入追蹤資料</span><span class="sxs-lookup"><span data-stu-id="7d846-102">Prepare the Input Trace Data</span></span>
  <span data-ttu-id="7d846-103">您必須先從分散式重新執行管理工具開始前置處理階段，以準備輸入追蹤資料，才能透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 功能啟動分散式重新執行。</span><span class="sxs-lookup"><span data-stu-id="7d846-103">Before you can start a distributed replay with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay feature, you must prepare the input trace data by initiating the preprocess stage from the distributed replay administration tool.</span></span> <span data-ttu-id="7d846-104">在前置處理階段中，分散式重新執行控制器會處理追蹤資料並產生中繼檔案：</span><span class="sxs-lookup"><span data-stu-id="7d846-104">In the preprocess stage, the distributed replay controller processes the trace data and generates an intermediate file:</span></span>  
  
 <span data-ttu-id="7d846-105">![分散式重新執行前置處理階段](../../database-engine/media/preprocess.gif "分散式重新執行前置處理階段")</span><span class="sxs-lookup"><span data-stu-id="7d846-105">![Distributed replay preprocess stage](../../database-engine/media/preprocess.gif "Distributed replay preprocess stage")</span></span>  
  
 <span data-ttu-id="7d846-106">如需前置處理階段的詳細資訊，請參閱 [SQL Server Distributed Replay](sql-server-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="7d846-106">For more information about the preprocess stage, see [SQL Server Distributed Replay](sql-server-distributed-replay.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d846-107">輸入追蹤資料必須在相容於 Distributed Replay 的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中擷取。</span><span class="sxs-lookup"><span data-stu-id="7d846-107">The input trace data must be captured in a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is compatible with Distributed Replay.</span></span> <span data-ttu-id="7d846-108">輸入追蹤資料也必須相容於您要針對它重新執行追蹤資料的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="7d846-108">The input trace data must also be compatible with the target server that you want to replay the trace data against.</span></span> <span data-ttu-id="7d846-109">如需有關版本需求的詳細資訊，請參閱＜ [Distributed Replay Requirements](distributed-replay-requirements.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7d846-109">For more information about version requirements, see [Distributed Replay Requirements](distributed-replay-requirements.md).</span></span>  
  
### <a name="to-prepare-the-input-trace-data"></a><span data-ttu-id="7d846-110">若要準備輸入追蹤資料</span><span class="sxs-lookup"><span data-stu-id="7d846-110">To prepare the input trace data</span></span>  
  
1.  <span data-ttu-id="7d846-111">**(選擇性) 修改前置處理組態設定**：如果您想要修改前置處理組態設定 (例如要篩選系統工作階段或設定最大閒置時間)，必須修改以 XML 為基礎的前置處理組態檔 `DReplay.exe.preprocess.config` 的 `<PreprocessModifiers>` 元素。</span><span class="sxs-lookup"><span data-stu-id="7d846-111">**(Optional) Modify preprocess configuration settings**: If you want to modify the preprocess configuration settings, such as whether to filter system sessions or to configure the maximum idle time, you must modify the `<PreprocessModifiers>` element of the XML-based preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span> <span data-ttu-id="7d846-112">如果您修改前置處理組態檔，我們建議您修改複本，而不是原始版本。</span><span class="sxs-lookup"><span data-stu-id="7d846-112">If you modify the preprocess configuration file, we recommend that you modify a copy rather than the original.</span></span> <span data-ttu-id="7d846-113">若要修改設定，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7d846-113">To modify settings, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="7d846-114">建立預設前置處理組態檔 `DReplay.exe.preprocess.config`的複本，並重新命名新的檔案。</span><span class="sxs-lookup"><span data-stu-id="7d846-114">Make a copy of the default preprocess configuration file, `DReplay.exe.preprocess.config`, and rename the new file.</span></span> <span data-ttu-id="7d846-115">預設前置處理組態檔位於管理工具的安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d846-115">The default preprocess configuration file is located in the administration tool installation folder.</span></span>  
  
    2.  <span data-ttu-id="7d846-116">修改新組態檔中的前置處理組態設定。</span><span class="sxs-lookup"><span data-stu-id="7d846-116">Modify the preprocess configuration settings in the new configuration file.</span></span>  
  
    3.  <span data-ttu-id="7d846-117">當起始前置處理階段 (下一步) 時，使用 *preprocess* 選項的 **config_file** 參數來指定已修改組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="7d846-117">When initiating the preprocess stage (the next step), use the *config_file* parameter of the **preprocess** option to specify the location of the modified configuration file.</span></span>  
  
     <span data-ttu-id="7d846-118">如需前置處理組態檔的詳細資訊，請參閱 [設定 Distributed Replay](configure-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="7d846-118">For more information about the preprocess configuration file, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span>  
  
2.  <span data-ttu-id="7d846-119">**開始前置處理階段**：若要準備輸入追蹤資料，您必須透過 [前置處理] 選項執行管理工具。</span><span class="sxs-lookup"><span data-stu-id="7d846-119">**Initiate the preprocess stage**: To prepare the input trace data, you must run the administration tool with the **preprocess** option.</span></span> <span data-ttu-id="7d846-120">如需詳細資訊，請參閱[前置處理選項 &#40;Distributed Replay 管理工具&#41;](preprocess-option-distributed-replay-administration-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="7d846-120">For more information, see [Preprocess Option &#40;Distributed Replay Administration Tool&#41;](preprocess-option-distributed-replay-administration-tool.md).</span></span>  
  
    1.  <span data-ttu-id="7d846-121">開啟 Windows 命令提示字元公用程式 (`CMD.exe`)，並瀏覽至 Distributed Replay 管理工具 (`DReplay.exe`) 的安裝位置。</span><span class="sxs-lookup"><span data-stu-id="7d846-121">Open the Windows Command Prompt utility (`CMD.exe`), and navigate to the installation location of the Distributed Replay administration tool (`DReplay.exe`).</span></span>  
  
    2.  <span data-ttu-id="7d846-122">(選擇性) 使用 *controller* 參數 **-m**指定控制器 (如果控制器服務是在與管理工具不同的電腦上執行)。</span><span class="sxs-lookup"><span data-stu-id="7d846-122">(Optional) Use the *controller* parameter, **-m**, to specify the controller, if the controller service is running on a computer different from the administration tool.</span></span>  
  
    3.  <span data-ttu-id="7d846-123">使用 *input_trace_file* 參數 **-i**，指定輸入追蹤檔案的位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="7d846-123">Use the *input_trace_file* parameter, **-i**, to specify the location and name of the input trace files.</span></span>  
  
    4.  <span data-ttu-id="7d846-124">使用 *controller_working_directory* 參數 **-d**，指定控制器上應該儲存中繼檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="7d846-124">Use the *controller_working_directory* parameter, **-d**, to specify where the intermediate file should be saved on the controller.</span></span>  
  
    5.  <span data-ttu-id="7d846-125">(選擇性) 使用 *config_file* 參數 **-c**，指定前置處理組態檔的位置。</span><span class="sxs-lookup"><span data-stu-id="7d846-125">(Optional) Use the *config_file* parameter, **-c**, to specify location of the preprocess configuration file.</span></span> <span data-ttu-id="7d846-126">如果已修改預設前置處理組態檔的複本，使用此參數指向新的組態檔。</span><span class="sxs-lookup"><span data-stu-id="7d846-126">Use this parameter to point to the new configuration file if you have modified a copy of the default preprocess configuration file.</span></span>  
  
    6.  <span data-ttu-id="7d846-127">(選擇性) 使用 *status_interval* 參數 **-f**，指定是否要讓管理工具以不同於 30 秒的頻率顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="7d846-127">(Optional) Use the *status_interval* parameter, **-f**, to specify if you want the administration tool to display status messages at a frequency different than 30 seconds.</span></span>  
  
     <span data-ttu-id="7d846-128">例如，若要在控制器服務所在的電腦上起始前置處理階段，指定追蹤檔案位於 `c:\trace1.trc`、控制器工作目錄位於 `c:\WorkingDir` ，而且以預設值 30 秒的頻率顯示狀態訊息，需要語法： `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span><span class="sxs-lookup"><span data-stu-id="7d846-128">For example, initiating the preprocess stage on the same computer as the controller service, for a trace file located at `c:\trace1.trc`, a controller working directory located at `c:\WorkingDir` , and a status message displayed at the default value of 30 seconds, requires the syntax: `dreplay preprocess -i c:\trace1.trc -d c:\WorkingDir`</span></span>  
  
3.  <span data-ttu-id="7d846-129">在前置處理階段完成之後，中繼檔案會儲存在控制器工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="7d846-129">After the preprocess stage is complete, the intermediate file is stored in the controller working directory.</span></span> <span data-ttu-id="7d846-130">若要起始事件重新執行階段，您必須以 **replay** 選項執行管理工具。</span><span class="sxs-lookup"><span data-stu-id="7d846-130">To initiate the event replay stage, you must run the administration tool with the **replay** option.</span></span> <span data-ttu-id="7d846-131">如需詳細資訊，請參閱 [重新執行追蹤資料](replay-trace-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7d846-131">For more information, see [Replay Trace Data](replay-trace-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d846-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d846-132">See Also</span></span>  
 <span data-ttu-id="7d846-133">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="7d846-133">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 <span data-ttu-id="7d846-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span><span class="sxs-lookup"><span data-stu-id="7d846-134">[Distributed Replay Requirements](distributed-replay-requirements.md) </span></span>  
 <span data-ttu-id="7d846-135">[管理工具命令列選項 &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span><span class="sxs-lookup"><span data-stu-id="7d846-135">[Administration Tool Command-line Options &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md) </span></span>  
 [<span data-ttu-id="7d846-136">設定 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="7d846-136">Configure Distributed Replay</span></span>](configure-distributed-replay.md)  
  
  
