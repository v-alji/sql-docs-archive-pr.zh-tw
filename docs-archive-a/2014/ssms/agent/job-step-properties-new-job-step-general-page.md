---
title: 作業步驟屬性：新增作業步驟 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepgeneral.f1
ms.assetid: 8d1885ba-4386-4528-8f2b-68c16852720c
author: stevestein
ms.author: sstein
ms.openlocfilehash: c76e1ecb69a1475ec102f143a6a1ca34fbf91e3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598111"
---
# <a name="job-step-properties-new-job-step-general-page"></a><span data-ttu-id="fe4d6-102">作業步驟屬性：新增作業步驟 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="fe4d6-102">Job Step Properties: New Job Step (General Page)</span></span>
  <span data-ttu-id="fe4d6-103">使用此頁面來查看和變更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟的屬性，或定義新的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step, or to define a new job step.</span></span>  
  
 <span data-ttu-id="fe4d6-104">若要導覽至此頁面，請在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 物件總管中，展開 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent，以滑鼠右鍵按一下 [作業]\*\*\*\*，按一下 [新增作業]\*\*\*\*，選取 [步驟]\*\*\*\* 頁面，然後按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-104">To navigate to this page, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, expand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, right-click **Jobs**, click **New Jobs**, select the **Steps** page, and click **New**.</span></span> <span data-ttu-id="fe4d6-105">您也可用滑鼠右鍵按一下物件總管中的作業，按一下 [屬性]\*\*\*\*、選取 [步驟]\*\*\*\* 頁面，然後按一下 [新增]\*\*\*\*、[插入]\*\*\*\* 或 [編輯]\*\*\*\*，以導覽至此頁面。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-105">You can also navigate to this page by right-clicking a job in Object Explorer, clicking **Properties**, selecting the **Steps** page, and clicking **New**, **Insert**, or **Edit**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fe4d6-106">選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-106">Options</span></span>  
 <span data-ttu-id="fe4d6-107">**步驟名稱**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-107">**Step name**</span></span>  
 <span data-ttu-id="fe4d6-108">設定作業步驟的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-108">Set the name of the job step.</span></span>  
  
 <span data-ttu-id="fe4d6-109">**型別**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-109">**Type**</span></span>  
 <span data-ttu-id="fe4d6-110">設定作業步驟使用的子系統。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-110">Set the subsystem that the job step uses.</span></span> <span data-ttu-id="fe4d6-111">根據您選擇的子系統，會顯示定義作業步驟變更的選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-111">Based on the subsystem you choose, the options displayed for defining the job step change.</span></span>  
  
 <span data-ttu-id="fe4d6-112">**執行身分**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-112">**Run as**</span></span>  
 <span data-ttu-id="fe4d6-113">設定作業步驟的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-113">Set the proxy account for the job step.</span></span> <span data-ttu-id="fe4d6-114">系統管理員 (sysadmin) 固定伺服器角色的成員也會指定 [SQL 代理程式服務帳戶]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-114">Members of the sysadmin fixed server role may also specify the **SQL Agent Service Account**.</span></span>  
  
 <span data-ttu-id="fe4d6-115">**Database**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-115">**Database**</span></span>  
 <span data-ttu-id="fe4d6-116">設定作業步驟執行所在的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-116">Set the database that the job step runs in.</span></span> <span data-ttu-id="fe4d6-117">並非所有作業步驟類型都可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-117">This option is not available for all job step types.</span></span>  
  
 <span data-ttu-id="fe4d6-118">**命令**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-118">**Command**</span></span>  
 <span data-ttu-id="fe4d6-119">設定作業步驟執行的命令。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-119">Set the command that the job step runs.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="fe4d6-120">Transact-SQL 作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-120">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="fe4d6-121">**開啟**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-121">**Open**</span></span>  
 <span data-ttu-id="fe4d6-122">從檔案載入命令。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-122">Load the command from a file.</span></span>  
  
 <span data-ttu-id="fe4d6-123">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-123">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-124">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-124">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-125">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-125">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-126">將選取的文字複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-126">Copy the selected text to the Clipboard.</span></span>  
  
 <span data-ttu-id="fe4d6-127">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-127">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-128">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-128">Paste the contents of the Clipboard.</span></span>  
  
 <span data-ttu-id="fe4d6-129">**剖析**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-129">**Parse**</span></span>  
 <span data-ttu-id="fe4d6-130">檢查命令的語法。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-130">Check the syntax of the command.</span></span>  
  
## <a name="options-for-activex-script-job-steps"></a><span data-ttu-id="fe4d6-131">ActiveX 指令碼作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-131">Options for ActiveX Script Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fe4d6-132">將從未來 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent 中移除 ActiveX Scripting 子系統。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-132">The ActiveX Scripting subsystem will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="fe4d6-133">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-133">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="fe4d6-134">**VBScript**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-134">**VBScript**</span></span>  
 <span data-ttu-id="fe4d6-135">指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic Scripting Edition 做為作業步驟的語言。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-135">Specify [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic Scripting Edition as the language for the job steps.</span></span>  
  
 <span data-ttu-id="fe4d6-136">**JScript**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-136">**JScript**</span></span>  
 <span data-ttu-id="fe4d6-137">指定 JScript 做為作業步驟的語言。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-137">Specify JScript as the language for the job steps.</span></span>  
  
 <span data-ttu-id="fe4d6-138">**其他**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-138">**Other**</span></span>  
 <span data-ttu-id="fe4d6-139">輸入以另一種指令碼語言撰寫之作業步驟的語言名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-139">Type the name of the language for job steps written in another scripting language.</span></span>  
  
 <span data-ttu-id="fe4d6-140">**開啟**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-140">**Open**</span></span>  
 <span data-ttu-id="fe4d6-141">從檔案載入命令。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-141">Load the command from a file.</span></span>  
  
 <span data-ttu-id="fe4d6-142">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-142">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-143">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-143">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-144">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-144">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-145">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-145">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-146">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-146">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-147">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-147">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="fe4d6-148">作業系統 (CmdExec) 作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-148">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="fe4d6-149">**成功命令的處理序結束碼**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-149">**Process exit code of a successful command**</span></span>  
 <span data-ttu-id="fe4d6-150">輸入命令傳回表示成功的結束碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-150">Type the exit code that the command returns to indicate success.</span></span>  
  
 <span data-ttu-id="fe4d6-151">**開啟**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-151">**Open**</span></span>  
 <span data-ttu-id="fe4d6-152">從檔案載入命令。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-152">Load the command from a file.</span></span>  
  
 <span data-ttu-id="fe4d6-153">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-153">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-154">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-154">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-155">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-155">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-156">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-156">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-157">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-157">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-158">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-158">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="fe4d6-159">PowerShell 作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-159">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="fe4d6-160">**開啟**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-160">**Open**</span></span>  
 <span data-ttu-id="fe4d6-161">從檔案載入指令碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-161">Load the script from a file.</span></span>  
  
 <span data-ttu-id="fe4d6-162">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-162">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-163">選取指令碼的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-163">Select the text of the script.</span></span>  
  
 <span data-ttu-id="fe4d6-164">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-164">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-165">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-165">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-166">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-166">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-167">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-167">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-distributor-job-steps"></a><span data-ttu-id="fe4d6-168">複寫散發者作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-168">Options for Replication Distributor Job Steps</span></span>  
 <span data-ttu-id="fe4d6-169">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-169">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-170">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-170">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-171">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-171">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-172">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-172">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-173">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-173">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-174">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-174">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-merge-job-steps"></a><span data-ttu-id="fe4d6-175">複寫合併作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-175">Options for Replication Merge Job Steps</span></span>  
 <span data-ttu-id="fe4d6-176">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-176">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-177">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-177">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-178">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-178">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-179">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-179">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-180">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-180">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-181">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-181">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="fe4d6-182">複寫佇列讀取器作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-182">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="fe4d6-183">**Database**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-183">**Database**</span></span>  
 <span data-ttu-id="fe4d6-184">作業步驟將使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-184">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="fe4d6-185">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-185">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-186">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-186">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-187">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-187">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-188">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-188">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-189">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-189">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-190">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-190">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-snapshot-job-steps"></a><span data-ttu-id="fe4d6-191">複寫快照集作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-191">Options for Replication Snapshot Job Steps</span></span>  
 <span data-ttu-id="fe4d6-192">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-192">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-193">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-193">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-194">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-194">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-195">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-195">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-196">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-196">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-197">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-197">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-replication-transaction-log-reader-job-steps"></a><span data-ttu-id="fe4d6-198">複寫交易記錄讀取器作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-198">Options for Replication Transaction-Log Reader Job Steps</span></span>  
 <span data-ttu-id="fe4d6-199">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-199">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-200">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-200">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-201">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-201">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-202">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-202">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-203">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-203">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-204">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-204">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-command-job-steps"></a><span data-ttu-id="fe4d6-205">SQL Server Analysis Services 命令作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-205">Options for SQL Server Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="fe4d6-206">**Server**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-206">**Server**</span></span>  
 <span data-ttu-id="fe4d6-207">選取作業步驟執行所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-207">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="fe4d6-208">**開啟**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-208">**Open**</span></span>  
 <span data-ttu-id="fe4d6-209">從檔案載入命令。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-209">Load the command from a file.</span></span>  
  
 <span data-ttu-id="fe4d6-210">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-210">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-211">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-211">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-212">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-212">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-213">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-213">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-214">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-214">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-215">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-215">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-query-job-steps"></a><span data-ttu-id="fe4d6-216">SQL Server Analysis Services 查詢作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-216">Options for SQL Server Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="fe4d6-217">**Server**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-217">**Server**</span></span>  
 <span data-ttu-id="fe4d6-218">選取作業步驟執行所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-218">Select the server where the job step runs.</span></span>  
  
 <span data-ttu-id="fe4d6-219">**Database**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-219">**Database**</span></span>  
 <span data-ttu-id="fe4d6-220">作業步驟將使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-220">The database to use for the job step.</span></span>  
  
 <span data-ttu-id="fe4d6-221">**開啟**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-221">**Open**</span></span>  
 <span data-ttu-id="fe4d6-222">從檔案載入命令。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-222">Load the command from a file.</span></span>  
  
 <span data-ttu-id="fe4d6-223">**全選**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-223">**Select All**</span></span>  
 <span data-ttu-id="fe4d6-224">選取命令的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-224">Select the text of the command.</span></span>  
  
 <span data-ttu-id="fe4d6-225">**複製**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-225">**Copy**</span></span>  
 <span data-ttu-id="fe4d6-226">複製選取的文字。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-226">Copy the selected text.</span></span>  
  
 <span data-ttu-id="fe4d6-227">**貼上**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-227">**Paste**</span></span>  
 <span data-ttu-id="fe4d6-228">貼上剪貼簿的內容。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-228">Paste the contents of the Clipboard.</span></span>  
  
## <a name="options-for-integration-services-package-execution-job-steps"></a><span data-ttu-id="fe4d6-229">Integration Services 封裝執行作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="fe4d6-229">Options for Integration Services Package Execution Job Steps</span></span>  
  
### <a name="general-tab"></a><span data-ttu-id="fe4d6-230">General Tab</span><span class="sxs-lookup"><span data-stu-id="fe4d6-230">General Tab</span></span>  
 <span data-ttu-id="fe4d6-231">指定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) 封裝所在的位置，以及要使用何種驗證方法。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-231">Specify where the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) package is located and what authentication method to use.</span></span> <span data-ttu-id="fe4d6-232">當您選取這個索引標籤時，可以使用下列選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-232">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="fe4d6-233">**封裝來源**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-233">**Package source**</span></span>  
 <span data-ttu-id="fe4d6-234">指定儲存 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-234">Specify where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="fe4d6-235">選擇下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="fe4d6-235">Choose one of the following:</span></span>  
  
-   <span data-ttu-id="fe4d6-236">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-236">**SQL Server**</span></span>  
  
-   <span data-ttu-id="fe4d6-237">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-237">**File system**</span></span>  
  
-   <span data-ttu-id="fe4d6-238">**SSIS 封裝存放區**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-238">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="fe4d6-239">**Server**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-239">**Server**</span></span>  
 <span data-ttu-id="fe4d6-240">輸入儲存 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-240">Type the server name where the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package is stored.</span></span> <span data-ttu-id="fe4d6-241">唯有當 [套件來源]\*\*\*\* 指定 [SQL Server]\*\*\*\* 或 [SSIS 套件存放區]\*\*\*\* 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-241">This option is only available when **SQL Server** or **SSIS Package Store** is specified for **Package Source**.</span></span>  
  
 <span data-ttu-id="fe4d6-242">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-242">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="fe4d6-243">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 驗證登入 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-243">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="fe4d6-244">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-244">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="fe4d6-245">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-245">Logins to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="fe4d6-246">如果選取這種驗證方法，請輸入適當的 [使用者名稱]\*\*\*\* 和 [密碼]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-246">If this method of authentication is selected, enter the appropriate **User name** and **Password**.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="fe4d6-247">提供驗證的目的在提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-247">Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="fe4d6-248">為了提升安全性，如果可能的話請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-248">For improved security, use Windows Authentication if possible.</span></span>  
  
 <span data-ttu-id="fe4d6-249">**套件**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-249">**Package**</span></span>  
 <span data-ttu-id="fe4d6-250">輸入封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-250">Type the location of the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fe4d6-251">對於受密碼保護的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 套件，按一下 [組態]\*\*\*\* 索引標籤，在 [套件密碼]\*\*\*\* 對話方塊中輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-251">For password-protected [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages, click the **Configurations** tab to enter the password in the **Package Password** dialog box.</span></span> <span data-ttu-id="fe4d6-252">否則，執行受密碼保護之封裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-252">Otherwise, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that executes the password-protected package will fail.</span></span>  
  
### <a name="configurations-tab"></a><span data-ttu-id="fe4d6-253">組態索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-253">Configurations Tab</span></span>  
 <span data-ttu-id="fe4d6-254">指定 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝的組態選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-254">Specify configuration options for the [!INCLUDE[ssIS](../../includes/ssis-md.md)] package.</span></span> <span data-ttu-id="fe4d6-255">當選取這個索引標籤時，可以使用下列選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-255">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="fe4d6-256">**組態檔**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-256">**Configuration files**</span></span>  
 <span data-ttu-id="fe4d6-257">列出封裝的組態檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-257">Lists the configuration files for the package.</span></span>  
  
 <span data-ttu-id="fe4d6-258">**加入**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-258">**Add**</span></span>  
 <span data-ttu-id="fe4d6-259">加入封裝的組態檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-259">Add a configuration file for the package.</span></span>  
  
 <span data-ttu-id="fe4d6-260">**移除**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-260">**Remove**</span></span>  
 <span data-ttu-id="fe4d6-261">移除封裝的組態檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-261">Remove a configuration file for the package.</span></span>  
  
 <span data-ttu-id="fe4d6-262">**上移**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-262">**Move Up**</span></span>  
 <span data-ttu-id="fe4d6-263">將選取的組態檔上移。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-263">Move the selected configuration file up.</span></span>  
  
 <span data-ttu-id="fe4d6-264">**下移**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-264">**Move Down**</span></span>  
 <span data-ttu-id="fe4d6-265">將選取的組態檔下移。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-265">Move the selected configuration file down.</span></span>  
  
### <a name="command-files-tab"></a><span data-ttu-id="fe4d6-266">命令檔索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-266">Command Files Tab</span></span>  
 <span data-ttu-id="fe4d6-267">選取封裝的命令檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-267">Select command files for the package.</span></span> <span data-ttu-id="fe4d6-268">依命令檔在清單中出現的順序處理命令檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-268">Command files are processed in the order in which they appear in the list.</span></span> <span data-ttu-id="fe4d6-269">當您選取這個索引標籤時，可以使用下列選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-269">The following options are available when you select this tab.</span></span>  
  
 <span data-ttu-id="fe4d6-270">**命令檔**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-270">**Command files**</span></span>  
 <span data-ttu-id="fe4d6-271">列出封裝的命令檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-271">Lists the command files for the package.</span></span>  
  
 <span data-ttu-id="fe4d6-272">**加入**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-272">**Add**</span></span>  
 <span data-ttu-id="fe4d6-273">加入命令檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-273">Add a command file.</span></span>  
  
 <span data-ttu-id="fe4d6-274">**移除**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-274">**Remove**</span></span>  
 <span data-ttu-id="fe4d6-275">移除選取的命令檔。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-275">Remove the selected command file.</span></span>  
  
 <span data-ttu-id="fe4d6-276">**上移**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-276">**Move Up**</span></span>  
 <span data-ttu-id="fe4d6-277">將選取的命令檔上移。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-277">Move the selected command file up.</span></span>  
  
 <span data-ttu-id="fe4d6-278">**下移**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-278">**Move Down**</span></span>  
 <span data-ttu-id="fe4d6-279">將選取的命令檔下移。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-279">Move the selected command file down.</span></span>  
  
### <a name="data-sources-tab"></a><span data-ttu-id="fe4d6-280">資料來源索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-280">Data Sources Tab</span></span>  
 <span data-ttu-id="fe4d6-281">檢視在此索引標籤上之封裝中所指定的資料來源。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-281">View the data sources specified in the package on this tab.</span></span>  
  
 <span data-ttu-id="fe4d6-282">**連線管理員**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-282">**Connection Manager**</span></span>  
 <span data-ttu-id="fe4d6-283">檢視資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-283">View the name of the data source.</span></span>  
  
 <span data-ttu-id="fe4d6-284">**說明**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-284">**Description**</span></span>  
 <span data-ttu-id="fe4d6-285">檢視資料來源的描述。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-285">View the description of the data source.</span></span>  
  
 <span data-ttu-id="fe4d6-286">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-286">**Connection String**</span></span>  
 <span data-ttu-id="fe4d6-287">檢視資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-287">View the connection string for the data source.</span></span>  
  
### <a name="execution-options-tab"></a><span data-ttu-id="fe4d6-288">執行選項索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-288">Execution Options Tab</span></span>  
 <span data-ttu-id="fe4d6-289">檢視或變更在此索引標籤上之封裝的執行選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-289">View or change the execution options for the package on this tab.</span></span>  
  
 <span data-ttu-id="fe4d6-290">**發生驗證警告時封裝就失敗**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-290">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="fe4d6-291">如果發生驗證警告時要使封裝執行失敗，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-291">Select this option for package execution to fail if validation warnings occur.</span></span>  
  
 <span data-ttu-id="fe4d6-292">**驗證封裝但不執行**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-292">**Validate package without executing**</span></span>  
 <span data-ttu-id="fe4d6-293">作業步驟要驗證但不執行封裝時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-293">Select this option for the job step to validate, but not execute, the package.</span></span>  
  
 <span data-ttu-id="fe4d6-294">**最大並行可執行檔數目**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-294">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="fe4d6-295">可以同時執行的最大可執行檔數目。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-295">Maximum number of executable files that can run at one time.</span></span>  
  
 <span data-ttu-id="fe4d6-296">**啟用封裝檢查點**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-296">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="fe4d6-297">作業步驟要使用封裝檢查點時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-297">Select this option for the job step to use package checkpoints.</span></span>  
  
 <span data-ttu-id="fe4d6-298">**檢查點檔案**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-298">**Checkpoint file**</span></span>  
 <span data-ttu-id="fe4d6-299">輸入封裝檢查點檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-299">Type the name of the package checkpoint file.</span></span>  
  
 <span data-ttu-id="fe4d6-300">**...**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-300">**...**</span></span>  
 <span data-ttu-id="fe4d6-301">瀏覽以尋找封裝檢查點檔案。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-301">Browse to find the package checkpoint file.</span></span>  
  
 <span data-ttu-id="fe4d6-302">**覆寫重新啟動選項**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-302">**Override restart options**</span></span>  
 <span data-ttu-id="fe4d6-303">若要為此作業步驟指定不同於封裝中所指定的重新啟動選項時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-303">Select this option to specify restart options for this job step that are different from the restart options specified in the package.</span></span>  
  
 <span data-ttu-id="fe4d6-304">**重新啟動選項**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-304">**Restart option**</span></span>  
 <span data-ttu-id="fe4d6-305">選取封裝重新啟動時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-305">Select the action to take when the package restarts.</span></span>  
  
### <a name="logging-tab"></a><span data-ttu-id="fe4d6-306">記錄索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-306">Logging Tab</span></span>  
 <span data-ttu-id="fe4d6-307">檢視或變更在此索引標籤上之封裝的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-307">View or change the log providers for the package on this tab.</span></span>  
  
 <span data-ttu-id="fe4d6-308">**記錄提供者**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-308">**Log Provider**</span></span>  
 <span data-ttu-id="fe4d6-309">選取記錄提供者的 ClassID。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-309">Select the ClassID for the log provider.</span></span>  
  
 <span data-ttu-id="fe4d6-310">**組態字串**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-310">**Configuration String**</span></span>  
 <span data-ttu-id="fe4d6-311">輸入記錄提供者的組態字串。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-311">Type the configuration string for the log provider.</span></span>  
  
 <span data-ttu-id="fe4d6-312">**移除**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-312">**Remove**</span></span>  
 <span data-ttu-id="fe4d6-313">移除記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-313">Removes the log provider.</span></span>  
  
### <a name="set-values-tab"></a><span data-ttu-id="fe4d6-314">設定值索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-314">Set Values Tab</span></span>  
 <span data-ttu-id="fe4d6-315">檢視或變更在此索引標籤上之封裝的屬性值。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-315">View or change property values for the package on this tab.</span></span>  
  
 <span data-ttu-id="fe4d6-316">**屬性路徑**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-316">**Property path**</span></span>  
 <span data-ttu-id="fe4d6-317">檢視或變更屬性的路徑。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-317">View or change the path for the property.</span></span>  
  
 <span data-ttu-id="fe4d6-318">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-318">**Value**</span></span>  
 <span data-ttu-id="fe4d6-319">檢視或變更屬性的值。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-319">View or change the value for the property.</span></span>  
  
 <span data-ttu-id="fe4d6-320">**移除**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-320">**Remove**</span></span>  
 <span data-ttu-id="fe4d6-321">移除屬性。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-321">Removes the property.</span></span>  
  
### <a name="verification-tab"></a><span data-ttu-id="fe4d6-322">驗證索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-322">Verification Tab</span></span>  
 <span data-ttu-id="fe4d6-323">選取在此索引標籤上之作業步驟的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-323">Select the verification options for the job step on this tab.</span></span>  
  
 <span data-ttu-id="fe4d6-324">**只執行簽署的封裝**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-324">**Execute only signed packages**</span></span>  
 <span data-ttu-id="fe4d6-325">只執行已經簽署的封裝。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-325">Run only packages that have been signed.</span></span> <span data-ttu-id="fe4d6-326">選取此選項時，如果封裝未簽署，作業步驟就會失敗。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-326">When this option is selected, the job step fails if the package is unsigned.</span></span>  
  
 <span data-ttu-id="fe4d6-327">**確認封裝組建**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-327">**Verify package build**</span></span>  
 <span data-ttu-id="fe4d6-328">只執行具有特定組建編號的封裝。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-328">Run only packages with a specific build number.</span></span> <span data-ttu-id="fe4d6-329">選取此選項時，如果封裝沒有指定的組建編號，作業步驟就會失敗。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-329">When this option is selected, the job step fails if the package does not have the specified build number.</span></span>  
  
 <span data-ttu-id="fe4d6-330">**建置**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-330">**Build**</span></span>  
 <span data-ttu-id="fe4d6-331">輸入封裝的組建編號。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-331">Type the build number of the package.</span></span>  
  
 <span data-ttu-id="fe4d6-332">**確認封裝識別碼**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-332">**Verify package ID**</span></span>  
 <span data-ttu-id="fe4d6-333">只執行具有特定識別碼的封裝。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-333">Run only packages with a specific ID.</span></span> <span data-ttu-id="fe4d6-334">選取此選項時，如果封裝沒有指定的識別碼，作業步驟就會失敗。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-334">When this option is selected, the job step fails if the package does not have the specified ID.</span></span>  
  
 <span data-ttu-id="fe4d6-335">**封裝識別碼**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-335">**Package ID**</span></span>  
 <span data-ttu-id="fe4d6-336">輸入封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-336">Type the package ID.</span></span>  
  
 <span data-ttu-id="fe4d6-337">**確認版本識別碼**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-337">**Verify version ID**</span></span>  
 <span data-ttu-id="fe4d6-338">只執行具有特定版本識別碼的封裝。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-338">Run only packages with a specific version ID.</span></span> <span data-ttu-id="fe4d6-339">選取此選項時，如果封裝沒有指定的版本識別碼，作業步驟就會失敗。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-339">When this option is selected, the job step fails if the package does not have the specified version ID.</span></span>  
  
 <span data-ttu-id="fe4d6-340">**版本識別碼**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-340">**Version ID**</span></span>  
 <span data-ttu-id="fe4d6-341">輸入版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-341">Type the version ID.</span></span>  
  
### <a name="command-line-tab"></a><span data-ttu-id="fe4d6-342">命令列索引標籤</span><span class="sxs-lookup"><span data-stu-id="fe4d6-342">Command Line Tab</span></span>  
 <span data-ttu-id="fe4d6-343">指定封裝的命令列選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-343">Specify command-line options for the package.</span></span> <span data-ttu-id="fe4d6-344">當選取這個索引標籤時，可以使用下列選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-344">The following options are available when this tab is selected.</span></span>  
  
 <span data-ttu-id="fe4d6-345">**還原原始選項**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-345">**Restore the original options**</span></span>  
 <span data-ttu-id="fe4d6-346">使用此對話方塊中所設定的命令列選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-346">Use the command-line options set in this dialog.</span></span>  
  
 <span data-ttu-id="fe4d6-347">**手動編輯命令列**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-347">**Edit the command line manually**</span></span>  
 <span data-ttu-id="fe4d6-348">指定命令列視窗中的選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-348">Specify options in the command-line window.</span></span>  
  
 <span data-ttu-id="fe4d6-349">**命令列**</span><span class="sxs-lookup"><span data-stu-id="fe4d6-349">**Command line**</span></span>  
 <span data-ttu-id="fe4d6-350">輸入此封裝所用的命令列選項。</span><span class="sxs-lookup"><span data-stu-id="fe4d6-350">Type the command line options to use for this package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4d6-351">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe4d6-351">See Also</span></span>  
 <span data-ttu-id="fe4d6-352">[管理作業步驟](manage-job-steps.md) </span><span class="sxs-lookup"><span data-stu-id="fe4d6-352">[Manage Job Steps](manage-job-steps.md) </span></span>  
 <span data-ttu-id="fe4d6-353">[封裝的 SQL Server Agent 作業](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span><span class="sxs-lookup"><span data-stu-id="fe4d6-353">[SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md) </span></span>  
 [<span data-ttu-id="fe4d6-354">複寫代理程式管理</span><span class="sxs-lookup"><span data-stu-id="fe4d6-354">Replication Agent Administration</span></span>](../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
