---
title: 作業步驟屬性：新增作業步驟 (Advanced Page) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42820ffbdbb89261e839b5d1011f3a91b5841c86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705861"
---
# <a name="job-step-properties-new-job-step-advanced-page"></a><span data-ttu-id="d09e7-102">作業步驟屬性：新增作業步驟 (進階頁面)</span><span class="sxs-lookup"><span data-stu-id="d09e7-102">Job Step Properties: New Job Step (Advanced Page)</span></span>
  <span data-ttu-id="d09e7-103">使用此頁面來查看和變更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟的屬性。</span><span class="sxs-lookup"><span data-stu-id="d09e7-103">Use this page to view and change the properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step.</span></span>  
  
## <a name="options"></a><span data-ttu-id="d09e7-104">選項</span><span class="sxs-lookup"><span data-stu-id="d09e7-104">Options</span></span>  
 <span data-ttu-id="d09e7-105">**成功時的動作**</span><span class="sxs-lookup"><span data-stu-id="d09e7-105">**On success action**</span></span>  
 <span data-ttu-id="d09e7-106">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在作業步驟成功時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d09e7-106">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step succeeds.</span></span>  
  
 <span data-ttu-id="d09e7-107">**重試次數**</span><span class="sxs-lookup"><span data-stu-id="d09e7-107">**Retry attempts**</span></span>  
 <span data-ttu-id="d09e7-108">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 嘗試重試失敗之作業步驟的次數。</span><span class="sxs-lookup"><span data-stu-id="d09e7-108">Sets the number of times that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent attempts to retry a failed job step.</span></span>  
  
 <span data-ttu-id="d09e7-109">**重試間隔 (分鐘)**</span><span class="sxs-lookup"><span data-stu-id="d09e7-109">**Retry interval (minutes)**</span></span>  
 <span data-ttu-id="d09e7-110">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 嘗試重試之間要等候的時間。</span><span class="sxs-lookup"><span data-stu-id="d09e7-110">Sets the amount of time for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to wait between retry attempts.</span></span>  
  
 <span data-ttu-id="d09e7-111">**失敗時的動作**</span><span class="sxs-lookup"><span data-stu-id="d09e7-111">**On failure action**</span></span>  
 <span data-ttu-id="d09e7-112">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在作業步驟失敗時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d09e7-112">Sets the action for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to perform if the job step fails.</span></span>  
  
## <a name="options-for-transact-sql-job-steps"></a><span data-ttu-id="d09e7-113">Transact-SQL 作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="d09e7-113">Options for Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="d09e7-114">**輸出檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-114">**Output file**</span></span>  
 <span data-ttu-id="d09e7-115">設定作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-115">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="d09e7-116">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d09e7-116">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="d09e7-117">**...**</span><span class="sxs-lookup"><span data-stu-id="d09e7-117">**...**</span></span>  
 <span data-ttu-id="d09e7-118">瀏覽作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-118">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="d09e7-119">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-119">**View**</span></span>  
 <span data-ttu-id="d09e7-120">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，已停用此按鈕來查看輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-120">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="d09e7-121">而改用 [記事本] 來檢視作業步驟輸出檔。</span><span class="sxs-lookup"><span data-stu-id="d09e7-121">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="d09e7-122">**將輸出附加至現有檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-122">**Append output to existing file**</span></span>  
 <span data-ttu-id="d09e7-123">將輸出附加至現有的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-123">Append output to the existing contents of the file.</span></span> <span data-ttu-id="d09e7-124">否則，每次執行作業步驟時會覆寫先前的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-124">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="d09e7-125">**記錄至資料表**</span><span class="sxs-lookup"><span data-stu-id="d09e7-125">**Log to table**</span></span>  
 <span data-ttu-id="d09e7-126">將作業步驟輸出記錄至 **msdb** 資料庫中的 **sysjobstepslogs** 資料表。</span><span class="sxs-lookup"><span data-stu-id="d09e7-126">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="d09e7-127">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-127">**View**</span></span>  
 <span data-ttu-id="d09e7-128">至少執行一次作業步驟之後，按一下 [檢視]\*\*\*\* 即可在資料表中檢視其輸出。</span><span class="sxs-lookup"><span data-stu-id="d09e7-128">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="d09e7-129">**將輸出附加至資料表的現有項目**</span><span class="sxs-lookup"><span data-stu-id="d09e7-129">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="d09e7-130">將輸出附加至現有的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-130">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="d09e7-131">否則，每次執行作業步驟時會覆寫先前的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-131">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="d09e7-132">**包含步驟輸出於記錄中**</span><span class="sxs-lookup"><span data-stu-id="d09e7-132">**Include step output in history**</span></span>  
 <span data-ttu-id="d09e7-133">選取此選項即可將作業步驟的輸出包含於作業記錄中。</span><span class="sxs-lookup"><span data-stu-id="d09e7-133">Select this option to include output from the job step in the job history.</span></span>  
  
 <span data-ttu-id="d09e7-134">**指定執行時的身分**</span><span class="sxs-lookup"><span data-stu-id="d09e7-134">**Run as user**</span></span>  
 <span data-ttu-id="d09e7-135">如果您是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，就可以選取另一個 SQL 登入來執行此作業步驟。</span><span class="sxs-lookup"><span data-stu-id="d09e7-135">If you are a member of the **sysadmin** fixed server role, you can select another SQL login to run this job step.</span></span>  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a><span data-ttu-id="d09e7-136">作業系統 (CmdExec) 作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="d09e7-136">Options for Operating System (CmdExec) Job Steps</span></span>  
 <span data-ttu-id="d09e7-137">**輸出檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-137">**Output file**</span></span>  
 <span data-ttu-id="d09e7-138">設定作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-138">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="d09e7-139">**...**</span><span class="sxs-lookup"><span data-stu-id="d09e7-139">**...**</span></span>  
 <span data-ttu-id="d09e7-140">瀏覽作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-140">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="d09e7-141">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-141">**View**</span></span>  
 <span data-ttu-id="d09e7-142">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，已停用此按鈕來查看輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-142">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="d09e7-143">而改用 [記事本] 來檢視作業步驟輸出檔。</span><span class="sxs-lookup"><span data-stu-id="d09e7-143">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="d09e7-144">**將輸出附加至現有檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-144">**Append output to existing file**</span></span>  
 <span data-ttu-id="d09e7-145">每次執行作業步驟時，將作業步驟輸出附加至先前的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-145">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="d09e7-146">**記錄至資料表**</span><span class="sxs-lookup"><span data-stu-id="d09e7-146">**Log to table**</span></span>  
 <span data-ttu-id="d09e7-147">將作業步驟輸出記錄至 **msdb** 資料庫中的 **sysjobstepslogs** 資料表。</span><span class="sxs-lookup"><span data-stu-id="d09e7-147">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="d09e7-148">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-148">**View**</span></span>  
 <span data-ttu-id="d09e7-149">至少執行一次作業步驟之後，按一下 [檢視]\*\*\*\* 即可在資料表中檢視其輸出。</span><span class="sxs-lookup"><span data-stu-id="d09e7-149">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="d09e7-150">**將輸出附加至資料表的現有項目**</span><span class="sxs-lookup"><span data-stu-id="d09e7-150">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="d09e7-151">將輸出附加至現有的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-151">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="d09e7-152">否則，每次執行作業步驟時會覆寫先前的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-152">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="d09e7-153">**包含步驟輸出於記錄中**</span><span class="sxs-lookup"><span data-stu-id="d09e7-153">**Include step output in history**</span></span>  
 <span data-ttu-id="d09e7-154">選取此選項即可將作業步驟的輸出包含於作業記錄中。</span><span class="sxs-lookup"><span data-stu-id="d09e7-154">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-powershell-job-steps"></a><span data-ttu-id="d09e7-155">PowerShell 作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="d09e7-155">Options for PowerShell Job Steps</span></span>  
 <span data-ttu-id="d09e7-156">**輸出檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-156">**Output file**</span></span>  
 <span data-ttu-id="d09e7-157">設定作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-157">Sets the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="d09e7-158">**...**</span><span class="sxs-lookup"><span data-stu-id="d09e7-158">**...**</span></span>  
 <span data-ttu-id="d09e7-159">瀏覽作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-159">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="d09e7-160">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-160">**View**</span></span>  
 <span data-ttu-id="d09e7-161">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，已停用此按鈕來查看輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-161">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="d09e7-162">而改用 [記事本] 來檢視作業步驟輸出檔。</span><span class="sxs-lookup"><span data-stu-id="d09e7-162">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="d09e7-163">**將輸出附加至現有檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-163">**Append output to existing file**</span></span>  
 <span data-ttu-id="d09e7-164">每次執行作業步驟時，將作業步驟輸出附加至先前的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-164">Appends the job step output to the previous file contents each time it runs.</span></span>  
  
 <span data-ttu-id="d09e7-165">**記錄至資料表**</span><span class="sxs-lookup"><span data-stu-id="d09e7-165">**Log to table**</span></span>  
 <span data-ttu-id="d09e7-166">將作業步驟輸出記錄至 **msdb** 資料庫中的 **sysjobstepslogs** 資料表。</span><span class="sxs-lookup"><span data-stu-id="d09e7-166">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="d09e7-167">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-167">**View**</span></span>  
 <span data-ttu-id="d09e7-168">至少執行一次作業步驟之後，按一下 [檢視]\*\*\*\* 即可在資料表中檢視其輸出。</span><span class="sxs-lookup"><span data-stu-id="d09e7-168">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="d09e7-169">**將輸出附加至資料表的現有項目**</span><span class="sxs-lookup"><span data-stu-id="d09e7-169">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="d09e7-170">將輸出附加至現有的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-170">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="d09e7-171">否則，每次執行作業步驟時會覆寫先前的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-171">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="d09e7-172">**包含步驟輸出於記錄中**</span><span class="sxs-lookup"><span data-stu-id="d09e7-172">**Include step output in history**</span></span>  
 <span data-ttu-id="d09e7-173">選取此選項即可將作業步驟的輸出包含於作業記錄中。</span><span class="sxs-lookup"><span data-stu-id="d09e7-173">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="options-for-replication-queue-reader-job-steps"></a><span data-ttu-id="d09e7-174">複寫佇列讀取器作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="d09e7-174">Options for Replication Queue Reader Job Steps</span></span>  
 <span data-ttu-id="d09e7-175">**Server**</span><span class="sxs-lookup"><span data-stu-id="d09e7-175">**Server**</span></span>  
 <span data-ttu-id="d09e7-176">設定複寫佇列讀取器作業步驟所用的伺服器。</span><span class="sxs-lookup"><span data-stu-id="d09e7-176">Sets the server to use for a replication queue reader job step.</span></span>  
  
 <span data-ttu-id="d09e7-177">**Database**</span><span class="sxs-lookup"><span data-stu-id="d09e7-177">**Database**</span></span>  
 <span data-ttu-id="d09e7-178">設定複寫佇列讀取器作業步驟所用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d09e7-178">Sets the database to use for a replication queue reader job step.</span></span>  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a><span data-ttu-id="d09e7-179">SQL Server Analysis Services 作業步驟的選項</span><span class="sxs-lookup"><span data-stu-id="d09e7-179">Options for SQL Server Analysis Services Job Steps</span></span>  
 <span data-ttu-id="d09e7-180">**輸出檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-180">**Output file**</span></span>  
 <span data-ttu-id="d09e7-181">設定作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-181">Sets the file to use for output from the job step.</span></span> <span data-ttu-id="d09e7-182">只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d09e7-182">This option is available only to members of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="d09e7-183">**...**</span><span class="sxs-lookup"><span data-stu-id="d09e7-183">**...**</span></span>  
 <span data-ttu-id="d09e7-184">瀏覽作業步驟輸出所用的檔案。</span><span class="sxs-lookup"><span data-stu-id="d09e7-184">Browse to the file to use for output from the job step.</span></span>  
  
 <span data-ttu-id="d09e7-185">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-185">**View**</span></span>  
 <span data-ttu-id="d09e7-186">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，會停用檢視輸出檔的這個按鈕。</span><span class="sxs-lookup"><span data-stu-id="d09e7-186">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this button is disabled for viewing output files.</span></span> <span data-ttu-id="d09e7-187">而改用 [記事本] 來檢視作業步驟輸出檔。</span><span class="sxs-lookup"><span data-stu-id="d09e7-187">Instead, use Notepad to view job step output files.</span></span>  
  
 <span data-ttu-id="d09e7-188">**將輸出附加至現有檔案**</span><span class="sxs-lookup"><span data-stu-id="d09e7-188">**Append output to existing file**</span></span>  
 <span data-ttu-id="d09e7-189">將輸出附加至現有的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-189">Append output to the existing contents of the file.</span></span> <span data-ttu-id="d09e7-190">否則，每次執行作業步驟時會覆寫先前的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-190">Otherwise, the previous file contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="d09e7-191">**記錄至資料表**</span><span class="sxs-lookup"><span data-stu-id="d09e7-191">**Log to table**</span></span>  
 <span data-ttu-id="d09e7-192">將作業步驟輸出記錄至 **msdb** 資料庫中的 **sysjobstepslogs** 資料表。</span><span class="sxs-lookup"><span data-stu-id="d09e7-192">Logs job step output to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
 <span data-ttu-id="d09e7-193">**檢視**</span><span class="sxs-lookup"><span data-stu-id="d09e7-193">**View**</span></span>  
 <span data-ttu-id="d09e7-194">至少執行一次作業步驟之後，按一下 [檢視]\*\*\*\* 即可在資料表中檢視其輸出。</span><span class="sxs-lookup"><span data-stu-id="d09e7-194">After the job step has run at least once, click **View** to view its output in the table.</span></span>  
  
 <span data-ttu-id="d09e7-195">**將輸出附加至資料表的現有項目**</span><span class="sxs-lookup"><span data-stu-id="d09e7-195">**Append output to existing entry in table**</span></span>  
 <span data-ttu-id="d09e7-196">將輸出附加至現有的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-196">Appends output to the existing contents of the table.</span></span> <span data-ttu-id="d09e7-197">否則，每次執行作業步驟時會覆寫先前的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="d09e7-197">Otherwise, the previous table contents are overwritten each time the job step runs.</span></span>  
  
 <span data-ttu-id="d09e7-198">**包含步驟輸出於記錄中**</span><span class="sxs-lookup"><span data-stu-id="d09e7-198">**Include step output in history**</span></span>  
 <span data-ttu-id="d09e7-199">選取此選項即可將作業步驟的輸出包含於作業記錄中。</span><span class="sxs-lookup"><span data-stu-id="d09e7-199">Select this option to include output from the job step in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09e7-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d09e7-200">See Also</span></span>  
 [<span data-ttu-id="d09e7-201">管理作業步驟</span><span class="sxs-lookup"><span data-stu-id="d09e7-201">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
