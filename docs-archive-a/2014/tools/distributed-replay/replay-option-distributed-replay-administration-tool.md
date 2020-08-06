---
title: 重新執行選項 (Distributed Replay 管理工具) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: a3114d7c2a2a7908e4e010fbf5d80c7d332d264c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707989"
---
# <a name="replay-option-distributed-replay-administration-tool"></a><span data-ttu-id="358f0-102">重新執行選項 (Distributed Replay 管理工具)</span><span class="sxs-lookup"><span data-stu-id="358f0-102">Replay Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="358f0-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是命令列工具，可讓您用來與 Distributed Replay controller 通訊。</span><span class="sxs-lookup"><span data-stu-id="358f0-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="358f0-104">此主題描述 **replay** 命令列選項與對應的語法。</span><span class="sxs-lookup"><span data-stu-id="358f0-104">This topic describes the **replay** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="358f0-105">**replay** 選項會起始事件重新執行階段，控制器在此階段中會分派重新執行資料給指定的用戶端、啟動分散式重新執行，並同步處理用戶端。</span><span class="sxs-lookup"><span data-stu-id="358f0-105">The **replay** option initiates the event replay stage, in which the controller dispatches replay data to the specified clients, launches the distributed replay and synchronizes the clients.</span></span> <span data-ttu-id="358f0-106">另外，參與重新執行的每個用戶端可以記錄重新執行活動，並在本機上儲存結果追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="358f0-106">Optionally, each client participating in the replay can record the replay activity and save a result trace file locally.</span></span>

 <span data-ttu-id="358f0-107">![主題連結圖示](../../database-engine/media/topic-link.gif "主題連結圖示") 如需管理工具語法所使用之語法慣例的詳細資訊，請參閱 [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="358f0-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="358f0-108">語法</span><span class="sxs-lookup"><span data-stu-id="358f0-108">Syntax</span></span>

```

      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]
    [-starget_server] -wclients [-cconfig_file]
    [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="358f0-109">參數</span><span class="sxs-lookup"><span data-stu-id="358f0-109">Parameters</span></span>
 <span data-ttu-id="358f0-110">**-m** *控制器*指定控制器的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="358f0-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="358f0-111">您可以使用 "`localhost`" 或 "`.`" 表示本機電腦。</span><span class="sxs-lookup"><span data-stu-id="358f0-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="358f0-112">如果未指定 **-m** 參數，則會使用本機電腦。</span><span class="sxs-lookup"><span data-stu-id="358f0-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="358f0-113">**-d** *controller_working_dir*會指定要儲存中繼檔案的控制器上的目錄。</span><span class="sxs-lookup"><span data-stu-id="358f0-113">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="358f0-114">**-d** 是必要參數。</span><span class="sxs-lookup"><span data-stu-id="358f0-114">The **-d** parameter is required.</span></span>

 <span data-ttu-id="358f0-115">下列為適用需求：</span><span class="sxs-lookup"><span data-stu-id="358f0-115">The following requirements apply:</span></span>

-   <span data-ttu-id="358f0-116">目錄必須位於控制器。</span><span class="sxs-lookup"><span data-stu-id="358f0-116">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="358f0-117">您必須指定以磁碟機代號開頭的完整路徑 (例如 `c:\WorkingDir`)。</span><span class="sxs-lookup"><span data-stu-id="358f0-117">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="358f0-118">路徑結尾不可以是反斜線 "`\`"。</span><span class="sxs-lookup"><span data-stu-id="358f0-118">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="358f0-119">不支援 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="358f0-119">UNC paths are not supported.</span></span>

 <span data-ttu-id="358f0-120">**-o**會捕獲用戶端的重新執行活動，並將其儲存至 `<ResultDirectory>` 用戶端設定檔中專案所指定路徑中的結果追蹤檔案 `DReplayClient.xml` 。</span><span class="sxs-lookup"><span data-stu-id="358f0-120">**-o** Captures the clients' replay activity and saves it to a result trace file in the path specified by the `<ResultDirectory>` element in the client configuration file, `DReplayClient.xml`.</span></span>

 <span data-ttu-id="358f0-121">未指定 **-o** 參數時，不會產生結果追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="358f0-121">When the **-o** parameter is not specified, the result trace file is not generated.</span></span> <span data-ttu-id="358f0-122">主控台輸出會在重新執行結尾時傳回摘要資訊，但不會提供其他重新執行統計資料。</span><span class="sxs-lookup"><span data-stu-id="358f0-122">The console output returns summary information at the end of replay, but no other replay statistics are available.</span></span>

 <span data-ttu-id="358f0-123">**-s** *target_server*指定要對其重新執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散式工作負載的目標實例。</span><span class="sxs-lookup"><span data-stu-id="358f0-123">**-s** *target_server* Specifies the target instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that the distributed workload should be replayed against.</span></span> <span data-ttu-id="358f0-124">您必須使用以下格式指定這個參數： **server_name[\instance name]** 。</span><span class="sxs-lookup"><span data-stu-id="358f0-124">You must specify this parameter in the format **server_name[\instance name]**.</span></span>

 <span data-ttu-id="358f0-125">不可使用 "`localhost`" 或 "`.`" 當做目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="358f0-125">You cannot use "`localhost`" or "`.`" as the target server.</span></span>

 <span data-ttu-id="358f0-126">如果在重新執行組態檔 **的** 區段中指定了 `<Server>` 元素，則不需要 `<ReplayOptions>` -s `DReplay.exe.replay.config`參數。</span><span class="sxs-lookup"><span data-stu-id="358f0-126">The **-s** parameter is not required if the `<Server>` element is specified in the `<ReplayOptions>` section of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="358f0-127">如果使用了 **-s** 參數，系統會忽略重新執行組態檔之 `<Server>` 區段中的 `<ReplayOptions>` 元素。</span><span class="sxs-lookup"><span data-stu-id="358f0-127">If the **-s** parameter is used, the `<Server>` element in the `<ReplayOptions>` section of the replay configuration file will be ignored.</span></span>

 <span data-ttu-id="358f0-128">**-w** *用戶端*此必要參數是以逗號分隔的清單 (不含空格) 指定應參與 distributed replay 的用戶端電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="358f0-128">**-w** *clients* This required parameter is a comma-separated list (without spaces) that specifies the computer names of clients that should participate in the distributed replay.</span></span> <span data-ttu-id="358f0-129">不允許 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="358f0-129">IP addresses are not allowed.</span></span> <span data-ttu-id="358f0-130">請注意，用戶端必須已經向控制器註冊。</span><span class="sxs-lookup"><span data-stu-id="358f0-130">Be aware that the clients must already be registered with the controller.</span></span>

> [!NOTE]
>  <span data-ttu-id="358f0-131">當用戶端服務啟動時，每個用戶端就會對用戶端組態檔中所指定的控制器進行註冊。</span><span class="sxs-lookup"><span data-stu-id="358f0-131">Each client registers with the controller that is specified in the client configuration file when the client service starts.</span></span>

 <span data-ttu-id="358f0-132">**-c** *config_file*是重新執行設定檔的完整路徑;用來指定儲存在不同位置的位置。</span><span class="sxs-lookup"><span data-stu-id="358f0-132">**-c** *config_file* Is the full path of the replay configuration file; used to specify the location when it is stored in a different location.</span></span>

 <span data-ttu-id="358f0-133">如果要使用重新執行組態檔 **的預設值，則不需要** -c `DReplay.exe.replay.config`參數。</span><span class="sxs-lookup"><span data-stu-id="358f0-133">The **-c** parameter is not required if you want to use the default values of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="358f0-134">**-f** *status_interval*指定顯示狀態 (的頻率（以秒為單位）) 。</span><span class="sxs-lookup"><span data-stu-id="358f0-134">**-f** *status_interval* Specifies the frequency (in seconds) at which to display the status.</span></span>

 <span data-ttu-id="358f0-135">如果未指定 **-f** ，則預設間隔為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="358f0-135">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="358f0-136">範例</span><span class="sxs-lookup"><span data-stu-id="358f0-136">Examples</span></span>
 <span data-ttu-id="358f0-137">在此範例中，分散式重新執行會從修改過的重新執行組態檔 `DReplay.exe.replay.config`，衍生其大部分的行為。</span><span class="sxs-lookup"><span data-stu-id="358f0-137">In this example, the distributed replay derives much of its behavior from a modified replay configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="358f0-138">**-m** 參數會指定一個名為 `controller1` 的電腦，作為控制器。</span><span class="sxs-lookup"><span data-stu-id="358f0-138">The **-m** parameter specifies that a computer named `controller1` acts as the controller.</span></span> <span data-ttu-id="358f0-139">當控制器服務執行於不同的電腦上時，必須指定電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="358f0-139">The computer name must be specified when the controller service is running on a different computer.</span></span>

-   <span data-ttu-id="358f0-140">**-d** 參數會指定控制器上中繼檔案的位置， `c:\WorkingDir`。</span><span class="sxs-lookup"><span data-stu-id="358f0-140">The **-d** parameter specifies the location of the intermediate file on the controller, `c:\WorkingDir`.</span></span>

-   <span data-ttu-id="358f0-141">**-o** 參數會指定每個指定的用戶端擷取重新執行活動，並將其儲存至結果追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="358f0-141">The **-o** parameter specifies that each specified client capture the replay activity and save it to a result trace file.</span></span> <span data-ttu-id="358f0-142">注意:設定檔中的 `<ResultTrace>` 元素可用來指定是否要記錄資料列計數和結果集。</span><span class="sxs-lookup"><span data-stu-id="358f0-142">Note: The `<ResultTrace>` element in the configuration file can be used to specify if row count and result set be recorded.</span></span>

-   <span data-ttu-id="358f0-143">**-w** 參數會指定 `client1` 到 `client4` 的電腦，參與為分散式重新執行中的用戶端。</span><span class="sxs-lookup"><span data-stu-id="358f0-143">The **-w** parameter specifies that computers `client1` through `client4` participate as clients in the distributed replay.</span></span>

-   <span data-ttu-id="358f0-144">**-c** 參數可用以指向修改過的組態檔 `DReplay.exe.replay.config`。</span><span class="sxs-lookup"><span data-stu-id="358f0-144">The **-c** parameter is used to point to the modified configuration file, `DReplay.exe.replay.config`.</span></span>

-   <span data-ttu-id="358f0-145">不需要 **-s** 參數，因為重新執行組態檔 `<Server>` 的 `<ReplayOptions>` 元素中，指定了 `DReplay.exe.replay.config`元素。</span><span class="sxs-lookup"><span data-stu-id="358f0-145">The **-s** parameter is not required because the `<Server>` element is specified in the `<ReplayOptions>` element of the replay configuration file, `DReplay.exe.replay.config`.</span></span>

 <span data-ttu-id="358f0-146">從不同於控制器的電腦執行管理工具時，使用下列語法起始事件重新執行階段：</span><span class="sxs-lookup"><span data-stu-id="358f0-146">The event replay stage is initiated with the following syntax, when the administration tool is run from a different computer than the controller:</span></span>

```
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config
```

 <span data-ttu-id="358f0-147">若要指定同步順序模式， `<SequencingMode>` 檔案的 `DReplay.exe.replay.config` 元素要設為等於 `synchronization`值。</span><span class="sxs-lookup"><span data-stu-id="358f0-147">To specify a synchronous sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `synchronization`.</span></span> <span data-ttu-id="358f0-148">重新執行組態檔的 `<ResultTrace>` 區段要修改，以指定應該記錄資料列計數。</span><span class="sxs-lookup"><span data-stu-id="358f0-148">The `<ResultTrace>` section of the replay configuration file is modified to specify that row count be recorded.</span></span> <span data-ttu-id="358f0-149">下列 XML 範例會示範這些變更：</span><span class="sxs-lookup"><span data-stu-id="358f0-149">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance</Server>
        <SequencingMode>synchronization</SequencingMode>
        <ConnectTimeScale></ConnectTimeScale>
        <ThinkTimeScale></ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

 <span data-ttu-id="358f0-150">若要指定壓力順序模式， `<SequencingMode>` 檔案的 `DReplay.exe.replay.config` 元素要設為等於 `stress`值。</span><span class="sxs-lookup"><span data-stu-id="358f0-150">To specify a stress sequencing mode, the `<SequencingMode>` element of the `DReplay.exe.replay.config` file is set equal to the value `stress`.</span></span> <span data-ttu-id="358f0-151">`<ConnectTimeScale>` 和 `<ThinkTimeScale>` 元素設為 `50` 值 (以指定 50%)。</span><span class="sxs-lookup"><span data-stu-id="358f0-151">The `<ConnectTimeScale>` and `<ThinkTimeScale>` elements are set to the value `50` (to specify 50 percent).</span></span> <span data-ttu-id="358f0-152">如需有關連接時間和思考時間的詳細資訊，請參閱 [設定 Distributed Replay](configure-distributed-replay.md)。</span><span class="sxs-lookup"><span data-stu-id="358f0-152">For more information about connect time and think time, see [Configure Distributed Replay](configure-distributed-replay.md).</span></span> <span data-ttu-id="358f0-153">下列 XML 範例會示範這些變更：</span><span class="sxs-lookup"><span data-stu-id="358f0-153">These changes are shown in the following XML example:</span></span>

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance_name</Server>
        <SequencingMode>stress</SequencingMode>
        <ConnectTimeScale>50</ConnectTimeScale>
        <ThinkTimeScale>50</ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="358f0-154">權限</span><span class="sxs-lookup"><span data-stu-id="358f0-154">Permissions</span></span>
 <span data-ttu-id="358f0-155">您必須以互動使用者、本機使用者或網域使用者帳戶來執行管理工具。</span><span class="sxs-lookup"><span data-stu-id="358f0-155">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="358f0-156">若要使用本機使用者帳戶，管理工具和控制器必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="358f0-156">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="358f0-157">如需詳細資訊，請參閱 [Distributed Replay 安全性](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="358f0-157">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="358f0-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="358f0-158">See Also</span></span>
 <span data-ttu-id="358f0-159">重新執行[追蹤資料](replay-trace-data.md)請參閱重新執行[結果](review-the-replay-results.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [設定 Distributed Replay](configure-distributed-replay.md) [SQL Server Distributed Replay 論壇](https://social.technet.microsoft.com/Forums/sl/sqldru/)[使用 Distributed Replay 來負載測試您的 SQL Server-第2部分](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2)[使用 Distributed Replay 負載測試您的 SQL Server-第1部分](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)</span><span class="sxs-lookup"><span data-stu-id="358f0-159">[Replay Trace Data](replay-trace-data.md) [Review the Replay Results](review-the-replay-results.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md) [SQL Server Distributed Replay Forum](https://social.technet.microsoft.com/Forums/sl/sqldru/) [Using Distributed Replay to Load Test Your SQL Server - Part 2](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2) [Using Distributed Replay to Load Test Your SQL Server - Part 1](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1)</span></span>


