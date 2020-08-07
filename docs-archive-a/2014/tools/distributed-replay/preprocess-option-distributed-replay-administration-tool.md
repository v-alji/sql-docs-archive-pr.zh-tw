---
title: 前置處理選項 (Distributed Replay 管理工具) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
ms.openlocfilehash: e7f168d45b03473d958e202bd75116f4519d2fc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593732"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a><span data-ttu-id="bb993-102">前置處理選項 (Distributed Replay 管理工具)</span><span class="sxs-lookup"><span data-stu-id="bb993-102">Preprocess Option (Distributed Replay Administration Tool)</span></span>
  <span data-ttu-id="bb993-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理工具 `DReplay.exe` 是命令列工具，可讓您用來與 Distributed Replay controller 通訊。</span><span class="sxs-lookup"><span data-stu-id="bb993-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay administration tool, `DReplay.exe`, is a command-line tool that you can use to communicate with the distributed replay controller.</span></span> <span data-ttu-id="bb993-104">本主題描述 **preprocess** 命令列選項與對應的語法。</span><span class="sxs-lookup"><span data-stu-id="bb993-104">This topic describes the **preprocess** command-line option and corresponding syntax.</span></span>

 <span data-ttu-id="bb993-105">**preprocess** 選項會起始前置處理階段。</span><span class="sxs-lookup"><span data-stu-id="bb993-105">The **preprocess** option initiates the preprocess stage.</span></span> <span data-ttu-id="bb993-106">在這個階段中，控制器會準備輸入追蹤資料，以便對目標伺服器重新執行。</span><span class="sxs-lookup"><span data-stu-id="bb993-106">During this stage, the controller prepares the input trace data for replay against the target server.</span></span>

 <span data-ttu-id="bb993-107">![主題連結圖示](../../database-engine/media/topic-link.gif "主題連結圖示")如需管理工具語法所使用之語法慣例的詳細資訊，請參閱 [Transact-SQL 語法慣例 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="bb993-107">![Topic link icon](../../database-engine/media/topic-link.gif "Topic link icon") For more information about the syntax conventions that are used with the administration tool syntax, see [Transact-SQL Syntax Conventions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).</span></span>

## <a name="syntax"></a><span data-ttu-id="bb993-108">語法</span><span class="sxs-lookup"><span data-stu-id="bb993-108">Syntax</span></span>

```

      dreplay preprocess [-mcontroller] -iinput_trace_file
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]
```

#### <a name="parameters"></a><span data-ttu-id="bb993-109">參數</span><span class="sxs-lookup"><span data-stu-id="bb993-109">Parameters</span></span>
 <span data-ttu-id="bb993-110">**-m** *控制器*指定控制器的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="bb993-110">**-m** *controller* Specifies the computer name of the controller.</span></span> <span data-ttu-id="bb993-111">您可以使用 "`localhost`" 或 "`.`" 表示本機電腦。</span><span class="sxs-lookup"><span data-stu-id="bb993-111">You can use "`localhost`" or "`.`" to refer to the local computer.</span></span>

 <span data-ttu-id="bb993-112">如果未指定 **-m** 參數，則會使用本機電腦。</span><span class="sxs-lookup"><span data-stu-id="bb993-112">If the **-m** parameter is not specified, the local computer is used.</span></span>

 <span data-ttu-id="bb993-113">**-i** *input_trace_file*指定控制器上輸入追蹤檔案的完整路徑，例如 `D:\Mytrace.trc` 。</span><span class="sxs-lookup"><span data-stu-id="bb993-113">**-i** *input_trace_file* Specifies the full path of the input trace file on the controller, such as `D:\Mytrace.trc`.</span></span> <span data-ttu-id="bb993-114">**-i** 是必要參數。</span><span class="sxs-lookup"><span data-stu-id="bb993-114">The **-i** parameter is required.</span></span>

 <span data-ttu-id="bb993-115">如果相同的目錄中存在換用檔案，系統就會自動載入並使用它們。</span><span class="sxs-lookup"><span data-stu-id="bb993-115">If there are rollover files in the same directory, they will be loaded and used automatically.</span></span> <span data-ttu-id="bb993-116">這些檔案必須遵循檔案換用命名慣例，例如：`Mytrace.trc`、`Mytrace_1.trc`、`Mytrace_2.trc`、`Mytrace_3.trc`... `Mytrace_n.trc`。</span><span class="sxs-lookup"><span data-stu-id="bb993-116">The files must follow the file rollover naming convention, for example: `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, ... `Mytrace_n.trc`.</span></span>

> [!NOTE]
>  <span data-ttu-id="bb993-117">如果您要在控制器以外的電腦上使用管理工具，就必須將輸入追蹤檔案複製到控制器，以便針對此參數使用本機路徑。</span><span class="sxs-lookup"><span data-stu-id="bb993-117">If you are using the administration tool on a different computer than the controller, you will need to copy the input trace files to the controller so that a local path can be used for this parameter.</span></span>

 <span data-ttu-id="bb993-118">**-d** *controller_working_dir*會指定要儲存中繼檔案的控制器上的目錄。</span><span class="sxs-lookup"><span data-stu-id="bb993-118">**-d** *controller_working_dir* Specifies the directory on the controller where the intermediate file will be stored.</span></span> <span data-ttu-id="bb993-119">**-d** 是必要參數。</span><span class="sxs-lookup"><span data-stu-id="bb993-119">The **-d** parameter is required.</span></span>

 <span data-ttu-id="bb993-120">下列為適用需求：</span><span class="sxs-lookup"><span data-stu-id="bb993-120">The following requirements apply:</span></span>

-   <span data-ttu-id="bb993-121">目錄必須位於控制器。</span><span class="sxs-lookup"><span data-stu-id="bb993-121">The directory must reside on the controller.</span></span>

-   <span data-ttu-id="bb993-122">您必須指定以磁碟機代號開頭的完整路徑 (例如 `c:\WorkingDir`)。</span><span class="sxs-lookup"><span data-stu-id="bb993-122">You must specify the full path, starting with a drive letter (for example, `c:\WorkingDir`).</span></span>

-   <span data-ttu-id="bb993-123">路徑結尾不可以是反斜線 "`\`"。</span><span class="sxs-lookup"><span data-stu-id="bb993-123">The path must not end with a backslash "`\`".</span></span>

-   <span data-ttu-id="bb993-124">不支援 UNC 路徑。</span><span class="sxs-lookup"><span data-stu-id="bb993-124">UNC paths are not supported.</span></span>

 <span data-ttu-id="bb993-125">**-c** *config_file*是前置處理設定檔的完整路徑;在儲存于不同的位置時，用來指定前置處理設定檔的位置。</span><span class="sxs-lookup"><span data-stu-id="bb993-125">**-c** *config_file* Is the full path of the preprocess configuration file; used to specify the location of the preprocess configuration file when stored in a different location.</span></span> <span data-ttu-id="bb993-126">此參數可以是 UNC 路徑，也可以位於您執行管理工具所在之電腦的本機。</span><span class="sxs-lookup"><span data-stu-id="bb993-126">This parameter can be a UNC path, or can reside locally on the computer where you run the administration tool.</span></span>

 <span data-ttu-id="bb993-127">如果不需要篩選，或您不想要修改最大閒置時間，則不需要 **-c** 參數。</span><span class="sxs-lookup"><span data-stu-id="bb993-127">The **-c** parameter is not required if no filtering is needed, or if you do not want to modify the maximum idle time.</span></span>

 <span data-ttu-id="bb993-128">如果沒有 **-c** 參數，則會使用預設前置處理組態檔 `DReplay.exe.preprocess.config`。</span><span class="sxs-lookup"><span data-stu-id="bb993-128">Without the **-c** parameter, the default preprocess configuration file, `DReplay.exe.preprocess.config`, is used.</span></span>

 <span data-ttu-id="bb993-129">**-f** *status_interval*指定顯示狀態訊息) 的頻率 (以秒為單位。</span><span class="sxs-lookup"><span data-stu-id="bb993-129">**-f** *status_interval* Specifies the frequency (in seconds) at which to display status messages.</span></span>

 <span data-ttu-id="bb993-130">如果未指定 **-f** ，則預設間隔為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="bb993-130">If **-f** is not specified, the default interval is 30 seconds.</span></span>

## <a name="examples"></a><span data-ttu-id="bb993-131">範例</span><span class="sxs-lookup"><span data-stu-id="bb993-131">Examples</span></span>
 <span data-ttu-id="bb993-132">在此範例中，前置處理階段是使用所有預設設定來起始。</span><span class="sxs-lookup"><span data-stu-id="bb993-132">In this example, the preprocess stage is initiated with all of the default settings.</span></span> <span data-ttu-id="bb993-133">`localhost` 值指出控制器服務與管理工具在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="bb993-133">The value `localhost` indicates that the controller service is running on the same computer as the administration tool.</span></span> <span data-ttu-id="bb993-134">*input_trace_file* 參數會指定輸入追蹤資料的位置 `c:\mytrace.trc`。</span><span class="sxs-lookup"><span data-stu-id="bb993-134">The *input_trace_file* parameter specifies the location of the input trace data, `c:\mytrace.trc`.</span></span> <span data-ttu-id="bb993-135">因為沒有涉及任何追蹤檔案篩選，所以必須指定 **-c** 參數。</span><span class="sxs-lookup"><span data-stu-id="bb993-135">Because there is no trace file filtering involved, the **-c** parameter does have to be specified.</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir
```

 <span data-ttu-id="bb993-136">在此範例中，已起始前置處理階段，而且已指定修改的前置處理組態檔。</span><span class="sxs-lookup"><span data-stu-id="bb993-136">In this example, the preprocess stage is initiated and a modified preprocess configuration file is specified.</span></span> <span data-ttu-id="bb993-137">與上個範例不同的是，如果您將修改過的組態檔儲存在不同的位置，就會使用 **-c** 參數來指向該組態檔。</span><span class="sxs-lookup"><span data-stu-id="bb993-137">Unlike the previous example, the **-c** parameter is used to point to the modified configuration file, if you have stored it in a different location.</span></span> <span data-ttu-id="bb993-138">例如：</span><span class="sxs-lookup"><span data-stu-id="bb993-138">For example:</span></span>

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config
```

 <span data-ttu-id="bb993-139">在修改的前置處理組態檔中，加入了一個篩選條件，它會在分散式重新執行期間篩選出系統工作階段。</span><span class="sxs-lookup"><span data-stu-id="bb993-139">In the modified preprocess configuration file, a filter condition is added that filters out system sessions during distributed replay.</span></span> <span data-ttu-id="bb993-140">此篩選是透過修改前置處理組態檔 `<PreprocessModifiers>` 中的 `DReplay.exe.preprocess.config`元素來加入。</span><span class="sxs-lookup"><span data-stu-id="bb993-140">The filter is added by modifying the `<PreprocessModifiers>` element in the preprocess configuration file, `DReplay.exe.preprocess.config`.</span></span>

 <span data-ttu-id="bb993-141">下面將顯示已修改組態檔的範例：</span><span class="sxs-lookup"><span data-stu-id="bb993-141">The following shows an example of the modified configuration file:</span></span>

```
<?xml version='1.0'?>
<Options>
    <PreprocessModifiers>
        <IncSystemSession>No</IncSystemSession>
        <MaxIdleTime>-1</MaxIdleTime>
    </PreprocessModifiers>
</Options>
```

## <a name="permissions"></a><span data-ttu-id="bb993-142">權限</span><span class="sxs-lookup"><span data-stu-id="bb993-142">Permissions</span></span>
 <span data-ttu-id="bb993-143">您必須以互動使用者、本機使用者或網域使用者帳戶來執行管理工具。</span><span class="sxs-lookup"><span data-stu-id="bb993-143">You must run the administration tool as an interactive user, as either a local user or a domain user account.</span></span> <span data-ttu-id="bb993-144">若要使用本機使用者帳戶，管理工具和控制器必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="bb993-144">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>

 <span data-ttu-id="bb993-145">如需詳細資訊，請參閱 [Distributed Replay 安全性](distributed-replay-security.md)。</span><span class="sxs-lookup"><span data-stu-id="bb993-145">For more information, see [Distributed Replay Security](distributed-replay-security.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb993-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb993-146">See Also</span></span>
 <span data-ttu-id="bb993-147">[準備輸入追蹤資料](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [設定 Distributed Replay](configure-distributed-replay.md)</span><span class="sxs-lookup"><span data-stu-id="bb993-147">[Prepare the Input Trace Data](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [Configure Distributed Replay](configure-distributed-replay.md)</span></span>


