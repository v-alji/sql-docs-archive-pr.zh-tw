---
title: 管理作業步驟 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server replication]
- job steps [SQL Server Agent]
- jobs [SQL Server Agent], Integration Services package step
- executable programs as job steps
- operating systems [SQL Server], job steps
- Transact-SQL job step
- job steps [Transact-SQL]
- Integration Services packages, job steps
- replication job steps [SQL Server]
- logs [SQL Server], jobs
- SQL Server Agent jobs, job steps
- ActiveX scripting jobs [SQL Server]
- job steps [Analysis Services]
ms.assetid: 51352afc-a0a4-428b-8985-f9e58bb57c31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7362df13956e44b73d6984691e882bec2f39a1e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597540"
---
# <a name="manage-job-steps"></a><span data-ttu-id="90ff7-102">管理作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-102">Manage Job Steps</span></span>
  <span data-ttu-id="90ff7-103">作業步驟是指作業對資料庫或伺服器所採取的動作，</span><span class="sxs-lookup"><span data-stu-id="90ff7-103">A job step is an action that the job takes on a database or a server.</span></span> <span data-ttu-id="90ff7-104">每一個作業必須至少有一個作業步驟。</span><span class="sxs-lookup"><span data-stu-id="90ff7-104">Every job must have at least one job step.</span></span> <span data-ttu-id="90ff7-105">作業步驟可以是：</span><span class="sxs-lookup"><span data-stu-id="90ff7-105">Job steps can be:</span></span>  
  
-   <span data-ttu-id="90ff7-106">可執行檔程式與作業系統命令。</span><span class="sxs-lookup"><span data-stu-id="90ff7-106">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="90ff7-107">陳述式，包括預存程序和擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="90ff7-107">statements, including stored procedures and extended stored procedures.</span></span>  
  
-   <span data-ttu-id="90ff7-108">PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="90ff7-108">PowerShell scripts.</span></span>  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="90ff7-109">ActiveX Script。</span><span class="sxs-lookup"><span data-stu-id="90ff7-109">ActiveX scripts.</span></span>  
  
-   <span data-ttu-id="90ff7-110">複寫工作。</span><span class="sxs-lookup"><span data-stu-id="90ff7-110">Replication tasks.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="90ff7-111">工作。</span><span class="sxs-lookup"><span data-stu-id="90ff7-111">tasks.</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="90ff7-112">套件。</span><span class="sxs-lookup"><span data-stu-id="90ff7-112">packages.</span></span>  
  
 <span data-ttu-id="90ff7-113">每個作業步驟都是在特定的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-113">Every job step runs in a specific security context.</span></span> <span data-ttu-id="90ff7-114">如果作業步驟指定 Proxy，則作業步驟會在該 Proxy 認證的安全性內容中執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-114">If the job step specifies a proxy, the job step runs in the security context of the credential for the proxy.</span></span> <span data-ttu-id="90ff7-115">如果作業步驟未指定 Proxy，則作業步驟會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-115">If a job step does not specify a proxy, the job step runs in the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account.</span></span> <span data-ttu-id="90ff7-116">只有系統管理員 (sysadmin) 固定伺服器角色的成員，才可以建立未明確指定 Proxy 的作業。</span><span class="sxs-lookup"><span data-stu-id="90ff7-116">Only members of the sysadmin fixed server role can create jobs that do not explicitly specify a proxy.</span></span>  
  
 <span data-ttu-id="90ff7-117">因為作業步驟是在特定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 使用者的環境中執行，因此該使用者需具備讓作業步驟執行所需的權限和組態。</span><span class="sxs-lookup"><span data-stu-id="90ff7-117">Because job steps run in the context of a specific [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user, that user must have the permissions and configuration necessary for the job step to execute.</span></span> <span data-ttu-id="90ff7-118">例如，如果您建立了一個作業，它需要磁碟機代號或通用命名慣例 (UNC) 路徑，則在測試工作時，其作業步驟可能會在您的 Windows 使用者帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-118">For example, if you create a job that requires a drive letter or a Universal Naming Convention (UNC) path, the job steps may run under your Windows user account while testing the tasks.</span></span> <span data-ttu-id="90ff7-119">不過，作業步驟的 Windows 使用者也必須具備必要的權限、磁碟機代號組態或必要磁碟機的存取權，</span><span class="sxs-lookup"><span data-stu-id="90ff7-119">However, the Windows user for the job step must also have the necessary permissions, drive letter configurations, or access to the required drive.</span></span> <span data-ttu-id="90ff7-120">否則，作業步驟會失敗。</span><span class="sxs-lookup"><span data-stu-id="90ff7-120">Otherwise, the job step fails.</span></span> <span data-ttu-id="90ff7-121">若要防止此問題發生，請確定每一個作業步驟的 Proxy，對於作業步驟所執行的工作都具有必要權限。</span><span class="sxs-lookup"><span data-stu-id="90ff7-121">To prevent this problem, ensure that the proxy for each job step has the necessary permissions for the task that the job step performs.</span></span> <span data-ttu-id="90ff7-122">如需詳細資訊，請參閱[SQL Server 資料庫引擎和 Azure SQL Database 的資訊安全中心](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)。</span><span class="sxs-lookup"><span data-stu-id="90ff7-122">For more information, see [Security Center for SQL Server Database Engine and Azure SQL Database](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).</span></span>  
  
## <a name="job-step-logs"></a><span data-ttu-id="90ff7-123">作業步驟記錄</span><span class="sxs-lookup"><span data-stu-id="90ff7-123">Job Step Logs</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90ff7-124">Agent 可以將某些作業步驟的輸出寫入作業系統檔案，或寫入 msdb 資料庫中的 sysjobstepslogs 資料表。</span><span class="sxs-lookup"><span data-stu-id="90ff7-124">Agent can write output from some job steps either to an operating system file or to the sysjobstepslogs table in the msdb database.</span></span> <span data-ttu-id="90ff7-125">以下作業步驟類型可以寫入輸出至兩個目的地：</span><span class="sxs-lookup"><span data-stu-id="90ff7-125">The following job step types can write output to both destinations:</span></span>  
  
-   <span data-ttu-id="90ff7-126">可執行檔程式與作業系統命令。</span><span class="sxs-lookup"><span data-stu-id="90ff7-126">Executable programs and operating system commands.</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="90ff7-127">陳述式。</span><span class="sxs-lookup"><span data-stu-id="90ff7-127">statements.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="90ff7-128">工作。</span><span class="sxs-lookup"><span data-stu-id="90ff7-128">tasks.</span></span>  
  
 <span data-ttu-id="90ff7-129">當執行作業步驟的使用者是系統管理員 (sysadmin) 固定伺服器角色的成員時，這些作業步驟才可以將作業步驟輸出寫入作業系統檔案。</span><span class="sxs-lookup"><span data-stu-id="90ff7-129">Only job steps that are executed by users who are members of the sysadmin fixed server role can write job step output to operating system files.</span></span> <span data-ttu-id="90ff7-130">如果執行作業步驟的使用者是 msdb 資料庫中的 SQLAgentUserRole、SQLAgentReaderRole 或 SQLAgentOperatorRole 固定資料庫角色的成員，則這些作業步驟的輸出只能寫入 sysjobstepslogs 資料表中。</span><span class="sxs-lookup"><span data-stu-id="90ff7-130">If job steps are executed by users who are members of the SQLAgentUserRole, SQLAgentReaderRole, or the SQLAgentOperatorRole fixed database roles in the msdb database, then the output from these job steps can be written only to the sysjobstepslogs table.</span></span>  
  
 <span data-ttu-id="90ff7-131">當作業或作業步驟遭到刪除時，作業步驟記錄也會跟著自動刪除。</span><span class="sxs-lookup"><span data-stu-id="90ff7-131">Job step logs are automatically deleted when jobs or job steps are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90ff7-132">複寫工作和 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝作業步驟的記錄是由其個別的子系統處理，</span><span class="sxs-lookup"><span data-stu-id="90ff7-132">Replication task and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step logging is handled by their respective subsystem.</span></span> <span data-ttu-id="90ff7-133">您不能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 來設定這些作業步驟類型的作業步驟記錄。</span><span class="sxs-lookup"><span data-stu-id="90ff7-133">You cannot use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to configure jog step logging for these types of job steps.</span></span>  
  
## <a name="executable-programs-and-operating-system-commands-as-job-steps"></a><span data-ttu-id="90ff7-134">可執行程式和作業系統命令類型的作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-134">Executable Programs and Operating-System Commands As Job Steps</span></span>  
 <span data-ttu-id="90ff7-135">可執行程式和作業系統命令可以做為作業步驟，</span><span class="sxs-lookup"><span data-stu-id="90ff7-135">Executable programs and operating-system commands can be used as job steps.</span></span> <span data-ttu-id="90ff7-136">這些檔案的副檔名為 .bat、.cmd、.com 或 .exe。</span><span class="sxs-lookup"><span data-stu-id="90ff7-136">These files may have .bat, .cmd, .com, or .exe file extensions.</span></span>  
  
 <span data-ttu-id="90ff7-137">當您使用可執行程式或作業系統命令做為作業步驟時，必須指定：</span><span class="sxs-lookup"><span data-stu-id="90ff7-137">When you use an executable program or an operating-system command as a job step, you must specify:</span></span>  
  
-   <span data-ttu-id="90ff7-138">指令成功時傳回的處理序結束代碼。</span><span class="sxs-lookup"><span data-stu-id="90ff7-138">The process exit code returned if the command was successful.</span></span>  
  
-   <span data-ttu-id="90ff7-139">要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="90ff7-139">The command to execute.</span></span> <span data-ttu-id="90ff7-140">若要執行作業系統命令，此處是指命令本身；</span><span class="sxs-lookup"><span data-stu-id="90ff7-140">To execute an operating system command, this is simply the command itself.</span></span> <span data-ttu-id="90ff7-141">若為外部程式，則是指程式名稱和程式的引數，例如： **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"**</span><span class="sxs-lookup"><span data-stu-id="90ff7-141">For an external program, this is the name of the program and the arguments to the program, for example: **C:\Program Files\Microsoft SQL Server\100\Tools\Binn\sqlcmd.exe -e -q "sp_who"**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="90ff7-142">如果可執行檔不在系統路徑或執行作業步驟的使用者路徑中，您必須提供可執行檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="90ff7-142">You must provide the full path to the executable if the executable is not located in a directory specified in the system path or the path for the user that the job step runs as.</span></span>  
  
## <a name="transact-sql-job-steps"></a><span data-ttu-id="90ff7-143">Transact-SQL 作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-143">Transact-SQL Job Steps</span></span>  
 <span data-ttu-id="90ff7-144">當您建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟時，必須：</span><span class="sxs-lookup"><span data-stu-id="90ff7-144">When you create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step, you must:</span></span>  
  
-   <span data-ttu-id="90ff7-145">識別用來執行作業的資料庫。</span><span class="sxs-lookup"><span data-stu-id="90ff7-145">Identify the database in which to run the job.</span></span>  
  
-   <span data-ttu-id="90ff7-146">輸入要執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="90ff7-146">Type the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement to execute.</span></span> <span data-ttu-id="90ff7-147">陳述式可以呼叫預存程序或擴充預存程序。</span><span class="sxs-lookup"><span data-stu-id="90ff7-147">The statement may call a stored procedure or an extended stored procedure.</span></span>  
  
 <span data-ttu-id="90ff7-148">(選擇性) 您也可以開啟現有的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 檔案做為作業步驟的命令。</span><span class="sxs-lookup"><span data-stu-id="90ff7-148">Optionally, you can open an existing [!INCLUDE[tsql](../../includes/tsql-md.md)] file as the command for the job step.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="90ff7-149">作業步驟不使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Proxy。</span><span class="sxs-lookup"><span data-stu-id="90ff7-149">job steps do not use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxies.</span></span> <span data-ttu-id="90ff7-150">相反地，如果作業步驟的擁有者是系統管理員 (sysadmin) 固定伺服器角色的成員，則作業步驟會以作業步驟的擁有者或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶的身分來執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-150">Instead, the job step runs as the owner of the job step, or as the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account if the owner of the job step is a member of the sysadmin fixed server role.</span></span> <span data-ttu-id="90ff7-151">系統管理員 (sysadmin) 固定伺服器角色的成員也可以指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟在另一個使用者內容之下執行，方法是使用 sp_add_jobstep 預存程序的 *database_user_name* 參數。</span><span class="sxs-lookup"><span data-stu-id="90ff7-151">Members of the sysadmin fixed server role can also specify that [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps run under the context of another user by using the *database_user_name* parameter of the sp_add_jobstep stored procedure.</span></span> <span data-ttu-id="90ff7-152">如需詳細資訊，請參閱[sp_add_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="90ff7-152">For more information, see [sp_add_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="90ff7-153">單一 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟可包含多個批次。</span><span class="sxs-lookup"><span data-stu-id="90ff7-153">A single [!INCLUDE[tsql](../../includes/tsql-md.md)] job step can contain multiple batches.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="90ff7-154">作業步驟可包含內嵌 GO 命令。</span><span class="sxs-lookup"><span data-stu-id="90ff7-154">job steps can contain embedded GO commands.</span></span>  
  
## <a name="powershell-scripting-job-steps"></a><span data-ttu-id="90ff7-155">PowerShell 指令碼作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-155">PowerShell Scripting Job Steps</span></span>  
 <span data-ttu-id="90ff7-156">當您建立 PowerShell 指令碼作業步驟時，必須指定其中一個設定當做此步驟的命令：</span><span class="sxs-lookup"><span data-stu-id="90ff7-156">When you create a PowerShell script job step, you must specify one of two things as the command for the step:</span></span>  
  
-   <span data-ttu-id="90ff7-157">PowerShell 指令碼的文字。</span><span class="sxs-lookup"><span data-stu-id="90ff7-157">The text of a PowerShell script.</span></span>  
  
-   <span data-ttu-id="90ff7-158">要開啟之現有的 PowerShell 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="90ff7-158">An existing PowerShell script file to be opened.</span></span>  
  
 <span data-ttu-id="90ff7-159">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent powershell 子系統會開啟 powershell 會話，並載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] powershell 嵌入式管理單元。當做作業步驟命令使用的 PowerShell 腳本可以參考 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] powershell 提供者和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="90ff7-159">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent PowerShell subsystem opens a PowerShell session and loads the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins. The PowerShell script used as the job step command can reference the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span> <span data-ttu-id="90ff7-160">如需使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 嵌入式管理單元撰寫 PowerShell 指令碼的詳細資訊，請參閱 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="90ff7-160">For more information about writing PowerShell scripts using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell snap-ins, see the [SQL Server PowerShell](../../powershell/sql-server-powershell.md).</span></span>  
  
## <a name="activex-scripting-job-steps"></a><span data-ttu-id="90ff7-161">ActiveX Scripting 作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-161">ActiveX Scripting Job Steps</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="90ff7-162">ActiveX Scripting 作業步驟將從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未來版本的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent 中移除。</span><span class="sxs-lookup"><span data-stu-id="90ff7-162">The ActiveX scripting job step will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="90ff7-163">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="90ff7-163">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="90ff7-164">建立 ActiveX Scripting 作業步驟時，您必須：</span><span class="sxs-lookup"><span data-stu-id="90ff7-164">When you create an ActiveX scripting job step, you must:</span></span>  
  
-   <span data-ttu-id="90ff7-165">確認撰寫作業步驟所用的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="90ff7-165">Identify the scripting language in which the job step is written.</span></span>  
  
-   <span data-ttu-id="90ff7-166">撰寫 ActiveX Script。</span><span class="sxs-lookup"><span data-stu-id="90ff7-166">Write the ActiveX script.</span></span>  
  
 <span data-ttu-id="90ff7-167">您也可以開啟一個現存的 ActiveX Script 檔做為該作業步驟的指令。</span><span class="sxs-lookup"><span data-stu-id="90ff7-167">You can also open an existing ActiveX script file as the command for the job step.</span></span> <span data-ttu-id="90ff7-168">另外，ActiveX Script 命令也可以在外部編譯 (例如，使用 Microsoft Visual Basic)，然後再當成可執行程式來執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-168">Alternatively, ActiveX script commands can be externally compiled (for example, using Microsoft Visual Basic) and then run as executable programs.</span></span>  
  
 <span data-ttu-id="90ff7-169">當作業步驟指令是一個 ActiveX Script 時，您可以使用 SQLActiveScriptHost 物件將輸出列印到作業步驟記錄，或者是建立 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="90ff7-169">When a job step command is an ActiveX script, you can use the SQLActiveScriptHost object to print output to the job step history log or create COM objects.</span></span> <span data-ttu-id="90ff7-170">SQLActiveScriptHost 是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主控系統導入指令碼命名空間內的全域物件。</span><span class="sxs-lookup"><span data-stu-id="90ff7-170">SQLActiveScriptHost is a global object that is introduced by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent hosting system into the script name space.</span></span> <span data-ttu-id="90ff7-171">此物件具有兩個方法 (Print 和 CreateObject)。</span><span class="sxs-lookup"><span data-stu-id="90ff7-171">The object has two methods (Print and CreateObject).</span></span> <span data-ttu-id="90ff7-172">下列範例顯示 ActiveX Scripting 在 Visual Basic Scripting Edition (VBScript) 中如何運作。</span><span class="sxs-lookup"><span data-stu-id="90ff7-172">The following example shows how ActiveX scripting works in Visual Basic Scripting Edition (VBScript).</span></span>  
  
```  
' VBScript example for ActiveX Scripting job step  
' Create a Dmo.Server object. The object connects to the  
' server on which the script is running.  
  
Set oServer = CreateObject("SQLDmo.SqlServer")  
oServer.LoginSecure = True  
oServer.Connect "(local)"  
'Disconnect and destroy the server object  
oServer.DisConnect  
Set oServer = nothing
```  
  
## <a name="replication-job-steps"></a><span data-ttu-id="90ff7-173">複寫作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-173">Replication Job Steps</span></span>  
 <span data-ttu-id="90ff7-174">當您利用複寫建立發行集和訂閱時，依預設會建立複寫作業。</span><span class="sxs-lookup"><span data-stu-id="90ff7-174">When you create publications and subscriptions using replication, replication jobs are created by default.</span></span> <span data-ttu-id="90ff7-175">建立的作業類型取決於複寫類型 (快照式、交易式或合併式) 和所使用的選項。</span><span class="sxs-lookup"><span data-stu-id="90ff7-175">The type of job created is determined by the type of replication (snapshot, transactional, or merge) and the options used.</span></span>  
  
 <span data-ttu-id="90ff7-176">複寫作業步驟會啟動以下複寫代理程式的其中之一：</span><span class="sxs-lookup"><span data-stu-id="90ff7-176">Replication job steps activate one of these replication agents:</span></span>  
  
-   <span data-ttu-id="90ff7-177">快照集代理程式 (快照集作業)</span><span class="sxs-lookup"><span data-stu-id="90ff7-177">Snapshot Agent (Snapshot job)</span></span>  
  
-   <span data-ttu-id="90ff7-178">記錄讀取器代理程式 (LogReader 作業)</span><span class="sxs-lookup"><span data-stu-id="90ff7-178">Log Reader Agent (LogReader job)</span></span>  
  
-   <span data-ttu-id="90ff7-179">散發代理程式 (散發作業)</span><span class="sxs-lookup"><span data-stu-id="90ff7-179">Distribution Agent (Distribution job)</span></span>  
  
-   <span data-ttu-id="90ff7-180">合併代理程式 (合併作業)</span><span class="sxs-lookup"><span data-stu-id="90ff7-180">Merge Agent (Merge job)</span></span>  
  
-   <span data-ttu-id="90ff7-181">佇列讀取器代理程式 (QueueReader 作業)</span><span class="sxs-lookup"><span data-stu-id="90ff7-181">Queue Reader Agent (QueueReader job)</span></span>  
  
 <span data-ttu-id="90ff7-182">設定複寫時，您可以指定以三種方式的其中一種來執行複寫代理程式：在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 啟動之後持續執行、視需要執行或根據排程執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-182">When replication is set up, you can specify to run the replication agents in one of three ways: continuously after [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is started, on demand, or according to a schedule.</span></span> <span data-ttu-id="90ff7-183">如需複寫代理程式的詳細資訊，請參閱 [複寫代理程式概觀](../../relational-databases/replication/agents/replication-agents-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="90ff7-183">For more information about replication agents, see [Replication Agents Overview](../../relational-databases/replication/agents/replication-agents-overview.md).</span></span>  
  
## <a name="analysis-services-job-steps"></a><span data-ttu-id="90ff7-184">SQL Server Analysis Services 作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-184">Analysis Services Job Steps</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="90ff7-185">Agent 支援兩個不同類型的 Analysis Services 作業步驟，即命令作業步驟和查詢作業步驟。</span><span class="sxs-lookup"><span data-stu-id="90ff7-185">Agent supports two distinct types of Analysis Services job steps, command job steps, and query job steps.</span></span>  
  
### <a name="analysis-services-command-job-steps"></a><span data-ttu-id="90ff7-186">SQL Server Analysis Services 命令作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-186">Analysis Services Command Job Steps</span></span>  
 <span data-ttu-id="90ff7-187">當您建立 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 命令作業步驟時，必須：</span><span class="sxs-lookup"><span data-stu-id="90ff7-187">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] command job step, you must:</span></span>  
  
-   <span data-ttu-id="90ff7-188">識別要執行作業步驟的資料庫 OLAP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="90ff7-188">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="90ff7-189">輸入要執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="90ff7-189">Type the statement to execute.</span></span> <span data-ttu-id="90ff7-190">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Execute** 方法的陳述式必須是 XML。</span><span class="sxs-lookup"><span data-stu-id="90ff7-190">The statement must be an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Execute** method.</span></span> <span data-ttu-id="90ff7-191">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Discover** 方法的陳述式不可包含完整的 SOAP Envelope 或 XML。</span><span class="sxs-lookup"><span data-stu-id="90ff7-191">The statement may not contain a complete SOAP envelope or an XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **Discover** method.</span></span> <span data-ttu-id="90ff7-192">請注意，雖然 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 支援完整的 SOAP Envelope 與 **Discover** 方法，但是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟則不支援。</span><span class="sxs-lookup"><span data-stu-id="90ff7-192">Notice that, while [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supports complete SOAP envelopes and the **Discover** method, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps do not.</span></span>  
  
### <a name="analysis-services-query-job-steps"></a><span data-ttu-id="90ff7-193">SQL Server Analysis Services 查詢作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-193">Analysis Services Query Job Steps</span></span>  
 <span data-ttu-id="90ff7-194">當您建立 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 查詢作業步驟時，必須：</span><span class="sxs-lookup"><span data-stu-id="90ff7-194">When you create an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] query job step, you must:</span></span>  
  
-   <span data-ttu-id="90ff7-195">識別要執行作業步驟的資料庫 OLAP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="90ff7-195">Identify the database OLAP server in which to run the job step.</span></span>  
  
-   <span data-ttu-id="90ff7-196">輸入要執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="90ff7-196">Type the statement to execute.</span></span> <span data-ttu-id="90ff7-197">陳述式必須為多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="90ff7-197">The statement must be a multidimensional expressions (MDX) query.</span></span>  
  
 <span data-ttu-id="90ff7-198">如需 MDX 的詳細資訊，請參閱[Mdx 查詢基本概念 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services)。</span><span class="sxs-lookup"><span data-stu-id="90ff7-198">For more information on MDX, see [MDX Query Fundamentals &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services).</span></span>  
  
## <a name="integration-services-packages"></a><span data-ttu-id="90ff7-199">Integration Services 封裝</span><span class="sxs-lookup"><span data-stu-id="90ff7-199">Integration Services Packages</span></span>  
 <span data-ttu-id="90ff7-200">當您建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝作業步驟時，必須執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="90ff7-200">When you create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package job step, you must do the following:</span></span>  
  
-   <span data-ttu-id="90ff7-201">識別封裝的來源。</span><span class="sxs-lookup"><span data-stu-id="90ff7-201">Identify the source of the package.</span></span>  
  
-   <span data-ttu-id="90ff7-202">識別封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="90ff7-202">Identify the location of the package.</span></span>  
  
-   <span data-ttu-id="90ff7-203">如果組態檔是封裝所必要的，請識別組態檔。</span><span class="sxs-lookup"><span data-stu-id="90ff7-203">If configuration files are required for the package, identify the configuration files.</span></span>  
  
-   <span data-ttu-id="90ff7-204">如果命令檔是封裝所必要的，請識別命令檔。</span><span class="sxs-lookup"><span data-stu-id="90ff7-204">If command files are required for the package, identify the command files.</span></span>  
  
-   <span data-ttu-id="90ff7-205">識別要用於封裝的驗證。</span><span class="sxs-lookup"><span data-stu-id="90ff7-205">Identify the verification to use for the package.</span></span> <span data-ttu-id="90ff7-206">例如，您可以指定封裝必須加以簽署，或封裝必須有特定的封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="90ff7-206">For example, you can specify that the package must be signed, or that the package must have a specific package ID.</span></span>  
  
-   <span data-ttu-id="90ff7-207">識別封裝的資料來源。</span><span class="sxs-lookup"><span data-stu-id="90ff7-207">Identify the data sources for the package.</span></span>  
  
-   <span data-ttu-id="90ff7-208">識別封裝的記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="90ff7-208">Identify the log providers for the package.</span></span>  
  
-   <span data-ttu-id="90ff7-209">指定在執行封裝之前要設定的變數和值。</span><span class="sxs-lookup"><span data-stu-id="90ff7-209">Specify variables and values to set before running the package.</span></span>  
  
-   <span data-ttu-id="90ff7-210">識別執行選項。</span><span class="sxs-lookup"><span data-stu-id="90ff7-210">Identify execution options.</span></span>  
  
-   <span data-ttu-id="90ff7-211">新增或修改命令列選項。</span><span class="sxs-lookup"><span data-stu-id="90ff7-211">Add or modify command-line options.</span></span>  
  
 <span data-ttu-id="90ff7-212">請注意，如果您將套件部署至 SSIS 目錄並將 [SSIS 目錄]\*\*\*\* 指定為套件來源，此組態資訊的大部分會從套件中自動取得。</span><span class="sxs-lookup"><span data-stu-id="90ff7-212">Note that if you deployed the package to the SSIS Catalog and you specify **SSIS Catalog** as the package source, much of this configuration information is obtained automatically from the package.</span></span> <span data-ttu-id="90ff7-213">在 [組態]\*\*\*\* 索引標籤下，您可以指定環境、參數值、連接管理員值、屬性覆寫、以及套件是否會在 32 位元執行階段環境中執行。</span><span class="sxs-lookup"><span data-stu-id="90ff7-213">Under the **Configuration** tab you can specify the environment, parameter values, connection manager values, property overrides, and whether the package runs in a 32-bit runtime environment.</span></span>  
  
 <span data-ttu-id="90ff7-214">如需建立用於執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件之作業步驟的詳細資訊，請參閱 [套件的 SQL Server Agent 作業](../../integration-services/packages/sql-server-agent-jobs-for-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="90ff7-214">For more information about creating job steps that run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [SQL Server Agent Jobs for Packages](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="90ff7-215">相關工作</span><span class="sxs-lookup"><span data-stu-id="90ff7-215">Related Tasks</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90ff7-216">**說明**</span><span class="sxs-lookup"><span data-stu-id="90ff7-216">**Description**</span></span>|<span data-ttu-id="90ff7-217">**主題**</span><span class="sxs-lookup"><span data-stu-id="90ff7-217">**Topic**</span></span>|  
|<span data-ttu-id="90ff7-218">描述如何建立包含可執行程式的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="90ff7-218">Describes how to create a job step with an executable program.</span></span>|[<span data-ttu-id="90ff7-219">建立 CmdExec 作業步驟</span><span class="sxs-lookup"><span data-stu-id="90ff7-219">Create a CmdExec Job Step</span></span>](create-a-cmdexec-job-step.md)|  
|<span data-ttu-id="90ff7-220">描述如何重設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 權限。</span><span class="sxs-lookup"><span data-stu-id="90ff7-220">Describes how to reset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent permissions.</span></span>|[<span data-ttu-id="90ff7-221">設定使用者可建立及管理 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="90ff7-221">Configure a User to Create and Manage SQL Server Agent Jobs</span></span>](configure-a-user-to-create-and-manage-sql-server-agent-jobs.md)|  
|<span data-ttu-id="90ff7-222">描述如何建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟。</span><span class="sxs-lookup"><span data-stu-id="90ff7-222">Describes how to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] job step.</span></span>|[<span data-ttu-id="90ff7-223">Create a Transact-SQL Job Step</span><span class="sxs-lookup"><span data-stu-id="90ff7-223">Create a Transact-SQL Job Step</span></span>](create-a-transact-sql-job-step.md)|  
|<span data-ttu-id="90ff7-224">描述如何定義 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Transact-SQL 作業步驟的選項。</span><span class="sxs-lookup"><span data-stu-id="90ff7-224">Describes how to define options for Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Transact-SQL job steps.</span></span>|[<span data-ttu-id="90ff7-225">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="90ff7-225">Define Transact-SQL Job Step Options</span></span>](define-transact-sql-job-step-options.md)|  
|<span data-ttu-id="90ff7-226">描述如何建立 ActiveX 指令碼作業步驟。</span><span class="sxs-lookup"><span data-stu-id="90ff7-226">Describes how to create an ActiveX script job step.</span></span>|[<span data-ttu-id="90ff7-227">Create an ActiveX Script Job Step</span><span class="sxs-lookup"><span data-stu-id="90ff7-227">Create an ActiveX Script Job Step</span></span>](create-an-activex-script-job-step.md)|  
|<span data-ttu-id="90ff7-228">描述如何建立及定義執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services 命令與查詢的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟。</span><span class="sxs-lookup"><span data-stu-id="90ff7-228">Describes how to create and define [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps that execute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Analysis Services commands and queries.</span></span>|[<span data-ttu-id="90ff7-229">Create an Analysis Services Job Step</span><span class="sxs-lookup"><span data-stu-id="90ff7-229">Create an Analysis Services Job Step</span></span>](create-an-analysis-services-job-step.md)|  
|<span data-ttu-id="90ff7-230">描述作業執行期間發生錯誤時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 應該採取的動作。</span><span class="sxs-lookup"><span data-stu-id="90ff7-230">Describes what action [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should take if a failure occurs during job execution.</span></span>|[<span data-ttu-id="90ff7-231">Set Job Step Success or Failure Flow</span><span class="sxs-lookup"><span data-stu-id="90ff7-231">Set Job Step Success or Failure Flow</span></span>](set-job-step-success-or-failure-flow.md)|  
|<span data-ttu-id="90ff7-232">描述如何檢視 [作業步驟屬性] 對話方塊中的作業步驟詳細資料。</span><span class="sxs-lookup"><span data-stu-id="90ff7-232">Describes how to view job step details in the Job Step Properties dialog.</span></span>|[<span data-ttu-id="90ff7-233">View Job Step Information</span><span class="sxs-lookup"><span data-stu-id="90ff7-233">View Job Step Information</span></span>](view-job-step-information.md)|  
|<span data-ttu-id="90ff7-234">描述如何刪除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟記錄。</span><span class="sxs-lookup"><span data-stu-id="90ff7-234">Describes how to delete a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step log.</span></span>|[<span data-ttu-id="90ff7-235">Delete a Job Step Log</span><span class="sxs-lookup"><span data-stu-id="90ff7-235">Delete a Job Step Log</span></span>](delete-a-job-step-log.md)|  
  
## <a name="see-also"></a><span data-ttu-id="90ff7-236">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90ff7-236">See Also</span></span>  
 <span data-ttu-id="90ff7-237">[dbo.sysjobstepslogs &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="90ff7-237">[dbo.sysjobstepslogs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobstepslogs-transact-sql) </span></span>  
 <span data-ttu-id="90ff7-238">[建立作業](create-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="90ff7-238">[Create Jobs](create-jobs.md) </span></span>  
 [<span data-ttu-id="90ff7-239">sp_add_job &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="90ff7-239">sp_add_job &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
