---
title: 處理多個作業步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef0fb69b5bfd028977276d8efabc333a21e0feb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584949"
---
# <a name="handle-multiple-job-steps"></a><span data-ttu-id="9f7b3-102">處理多個作業步驟</span><span class="sxs-lookup"><span data-stu-id="9f7b3-102">Handle Multiple Job Steps</span></span>
  <span data-ttu-id="9f7b3-103">如果您的作業有多重作業步驟，則必須指定這些作業步驟的執行順序。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-103">If your job has more than one job step, you must specify the order in which the job steps run.</span></span> <span data-ttu-id="9f7b3-104">這就叫做「流程控制」。\*\*</span><span class="sxs-lookup"><span data-stu-id="9f7b3-104">This is called *control of flow\*\*.*</span></span> <span data-ttu-id="9f7b3-105">您可以加入新的作業步驟，並可隨時重新排列作業步驟的流程；變更內容將會在下次執行作業時生效。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-105">You can add new job steps and rearrange the flow of job steps at any time; the changes take effect the next time the job is run.</span></span> <span data-ttu-id="9f7b3-106">下圖顯示資料庫備份作業的流程控制。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-106">This illustration shows the control of flow for a database backup job.</span></span>  
  
 <span data-ttu-id="9f7b3-107">![SQL Server Agent 作業步驟流程控制](../../database-engine/media/dbflow01.gif "SQL Server Agent 作業步驟流程控制")</span><span class="sxs-lookup"><span data-stu-id="9f7b3-107">![SQL Server Agent job steps control of flow](../../database-engine/media/dbflow01.gif "SQL Server Agent job steps control of flow")</span></span>  
  
 <span data-ttu-id="9f7b3-108">第一個步驟是「備份資料庫」。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-108">The first step is Backup Database.</span></span> <span data-ttu-id="9f7b3-109">如果這個步驟失敗了， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會向定義為接收通知的操作員報告失敗。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-109">If this step fails, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent reports failure to the operator who is defined to receive notification.</span></span> <span data-ttu-id="9f7b3-110">如果「備份資料庫」步驟成功，則作業會繼續進行下一個步驟：「刪除客戶資料」。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-110">If the Backup Database step succeeds, the job proceeds to the next step, "Scrub" Customer Data.</span></span> <span data-ttu-id="9f7b3-111">如果此步驟失敗，則 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 會跳過，並進行「還原資料庫」。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-111">If this step fails, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent skips forward to Restore Database.</span></span> <span data-ttu-id="9f7b3-112">如果「刪除客戶資料」成功，該作業會繼續下一個步驟「更新統計資料」等，直到最後一個步驟的結果為「報告成功」或「報告失敗」。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-112">If "Scrub" Customer Data succeeds, the job proceeds to the next step, Update Statistics, and so on, until the final step either results in Report Success or Report Failure.</span></span>  
  
 <span data-ttu-id="9f7b3-113">您為每個作業步驟的成功與失敗定義一個流程控制動作。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-113">You define a control-of-flow action for the success and failure of each job step.</span></span> <span data-ttu-id="9f7b3-114">您必須指定當作業步驟成功時所要執行的動作，以及作業步驟失敗時所要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-114">You must specify an action to be taken when a job step succeeds and an action to be taken when a job step fails.</span></span> <span data-ttu-id="9f7b3-115">您也可以定義作業步驟失敗時的重試次數和重試間隔。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-115">You can also define the number of retry attempts for failed job steps and the interval between the retry attempts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f7b3-116">當您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 圖形化使用者介面 (GUI)，並從多個步驟作業中刪除一或多個步驟時，GUI 會先移除所有作業步驟，然後再使用正確的 on-success 或 on-failure 參考，重新加入剩餘的步驟。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-116">When you use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent graphical user interface (GUI) and delete one or more steps from a multistep job, the GUI removes all job steps and then adds the remaining steps back with the correct on-success or on-failure references.</span></span> <span data-ttu-id="9f7b3-117">例如，假設您有一項包含五個步驟的作業，其中第一個步驟設定為若順利完成便跳到步驟 4。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-117">For example, suppose you have a job with five steps, and the first step is configured to jump to step 4 if it completes successfully.</span></span> <span data-ttu-id="9f7b3-118">如果您刪除步驟 3，GUI 便會移除此作業的所有步驟，並以更正過的參考加入剩餘的四個步驟 (步驟 1、2、4、5)。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-118">If you delete step 3, the GUI removes all steps for this job and adds the remaining four steps (1, 2, 4, and 5) with corrected references.</span></span> <span data-ttu-id="9f7b3-119">在這個案例下，步驟 1 中的參考將會重新設定為如果步驟 1 順利完成便跳到步驟 3。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-119">In this case, the reference in step 1 would be reconfigured to jump to step 3 if step 1 completes successfully.</span></span>  
  
 <span data-ttu-id="9f7b3-120">作業步驟必須是各自獨立的。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-120">Job steps must be self-contained.</span></span> <span data-ttu-id="9f7b3-121">也就是說，作業不能在作業步驟之間傳遞布林值、資料或數值。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-121">That is, a job cannot pass Boolean values, data, or numeric values between job steps.</span></span> <span data-ttu-id="9f7b3-122">但是，您可以使用永久性資料表或全域暫存資料表，將值從一個 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟傳遞至另一個作業步驟。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-122">You can, however, pass values from one [!INCLUDE[tsql](../../includes/tsql-md.md)] job step to another by using permanent tables or global temporary tables.</span></span> <span data-ttu-id="9f7b3-123">您也可以使用檔案，將執行可執行程式之作業步驟中的值，從一個作業步驟傳遞到另一個作業步驟。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-123">You can pass values from job steps that run executable programs from one job step to another job step by using files.</span></span> <span data-ttu-id="9f7b3-124">例如，由一個作業步驟所執行的可執行檔寫入檔案，再由後續作業步驟所執行的可執行檔來讀取檔案。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-124">For example, the executable run by one job step writes a file, and the executable run by a subsequent job step reads the file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f7b3-125">如果您建立迴圈作業步驟 (作業步驟 1 之後接著作業步驟 2，然後作業步驟 2 再回到作業步驟 1)，當您使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]來建立作業時，會出現警告訊息。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-125">If you create looping job steps (job step 1 is followed by job step 2, then job step 2 returns to job step 1), a warning message appears when the job is created using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9f7b3-126">Agent 會將作業及作業步驟資訊記錄在作業記錄中。</span><span class="sxs-lookup"><span data-stu-id="9f7b3-126">Agent records job and job step information in the job history.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f7b3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f7b3-127">See Also</span></span>  
 <span data-ttu-id="9f7b3-128">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f7b3-128">[sp_add_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql) </span></span>  
 <span data-ttu-id="9f7b3-129">[dbo.sysjobhistory &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f7b3-129">[dbo.sysjobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobhistory-transact-sql) </span></span>  
 <span data-ttu-id="9f7b3-130">[dbo.sys作業 &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f7b3-130">[dbo.sysjobs &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobs-transact-sql) </span></span>  
 <span data-ttu-id="9f7b3-131">[dbo.sysjobsteps &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9f7b3-131">[dbo.sysjobsteps &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobsteps-transact-sql) </span></span>  
 <span data-ttu-id="9f7b3-132">[實作作業](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="9f7b3-132">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="9f7b3-133">管理作業步驟</span><span class="sxs-lookup"><span data-stu-id="9f7b3-133">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  
