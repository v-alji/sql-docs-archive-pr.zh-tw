---
title: 使用維護計畫精靈 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.ag.maintwiz.planprop.f1
- sql12.ag.maintwiz.task.f1
- sql12.ag.maintwiz.maintcleanup.f1
- sql12.ag.maintwiz.indexdefrag.f1
- sql12.ag.maintwiz.order.f1
- sql12.ag.maintwiz.histcleanup.f1
- sql12.ag.maintwiz.backuplog.f1
- sql12.ag.maintwiz.progress.f1
- sql12.ag.maintwiz.execagentjob.f1
- sql12.ag.maintwiz.integrity.f1
- sql12.ag.maintwiz.welcome.f1
- sql12.ag.maintwiz.backupdiff.f1
- sql12.ag.maintwiz.server.f1
- sql12.ag.maintwiz.summary.f1
- sql12.ag.maintwiz.backupfull.f1
- sql12.ag.maintwiz.report.f1
- sql12.ag.maintwiz.shrinkdb.f1
- sql12.ag.maintwiz.reindex.f1
- sql12.ag.maintwiz.updatestats.f1
helpviewer_keywords:
- Maintenance Plan Wizard
- Database Maintenance Plan Wizard
- Database Maintenance Plan Wizard, starting
ms.assetid: db65c726-9892-480c-873b-3af29afcee44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ac134bbd4c65da4700990b69b09134230e98903f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592699"
---
# <a name="use-the-maintenance-plan-wizard"></a><span data-ttu-id="2f71c-102">使用維護計畫精靈</span><span class="sxs-lookup"><span data-stu-id="2f71c-102">Use the Maintenance Plan Wizard</span></span>
  <span data-ttu-id="2f71c-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的維護計畫精靈，建立單一伺服器或多伺服器維護計畫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-103">This topic describes how to create a single server or multiserver maintenance plan using the Maintenance Plan Wizard in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="2f71c-104">[維護計畫精靈] 會建立可讓 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 定期執行的維護計畫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-104">The Maintenance Plan Wizard creates a maintenance plan that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can run on a regular basis.</span></span> <span data-ttu-id="2f71c-105">這樣可讓您依指定間隔執行各種資料庫管理工作，包括備份、資料庫完整性檢查，或資料庫統計資料更新。</span><span class="sxs-lookup"><span data-stu-id="2f71c-105">This allows you to perform various database administration tasks, including backups, database integrity checks, or database statistics updates, at specified intervals.</span></span>  
  
 <span data-ttu-id="2f71c-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2f71c-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2f71c-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2f71c-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2f71c-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="2f71c-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="2f71c-109">安全性</span><span class="sxs-lookup"><span data-stu-id="2f71c-109">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="2f71c-110">在 SQL Server Management Studio 中使用維護計畫精靈建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="2f71c-110">Creating a maintenance plan using the Maintenance Plan Wizard in SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2f71c-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="2f71c-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="2f71c-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="2f71c-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2f71c-113">若要建立多伺服器維護計畫，必須設定多伺服器環境，其中包含一個主要伺服器以及一或多個目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f71c-113">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured.</span></span> <span data-ttu-id="2f71c-114">多伺服器維護計畫必須在主要伺服器上建立和維護。</span><span class="sxs-lookup"><span data-stu-id="2f71c-114">Multiserver maintenance plans must be created and maintained on the master server.</span></span> <span data-ttu-id="2f71c-115">您可以在目標伺服器上檢視這些計畫，但不能加以維護。</span><span class="sxs-lookup"><span data-stu-id="2f71c-115">These plans can be viewed, but not maintained, on target servers.</span></span>  
  
-   <span data-ttu-id="2f71c-116">**db_ssisadmin** 角色和 **dc_admin** 角色的成員可以將其權限提高為 **系統管理員**。</span><span class="sxs-lookup"><span data-stu-id="2f71c-116">Members of the **db_ssisadmin** and **dc_admin** roles may be able to elevate their privileges to **sysadmin**.</span></span> <span data-ttu-id="2f71c-117">能夠提高權限是因為這些角色可以修改 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝；這些封裝可藉由使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 **sysadmin** 安全性內容由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行。</span><span class="sxs-lookup"><span data-stu-id="2f71c-117">This elevation of privilege can occur because these roles can modify [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages; these packages can be executed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **sysadmin** security context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="2f71c-118">若要在執行維護計畫、資料收集組和其他 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時預防此權限提高，請將執行封裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業設為使用有限權限的 Proxy 帳戶，或是只將 **系統管理員** 成員加入 **db_ssisadmin** 和 **dc_admin** 角色。</span><span class="sxs-lookup"><span data-stu-id="2f71c-118">To guard against this elevation of privilege when running maintenance plans, data collection sets, and other [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, configure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs that run packages to use a proxy account with limited privileges or only add **sysadmin** members to the **db_ssisadmin** and **dc_admin** roles.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2f71c-119">Security</span><span class="sxs-lookup"><span data-stu-id="2f71c-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2f71c-120">權限</span><span class="sxs-lookup"><span data-stu-id="2f71c-120">Permissions</span></span>  
 <span data-ttu-id="2f71c-121">若要建立或管理維護計畫，您必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="2f71c-121">To create or manage maintenance plans, you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="2f71c-122">只有在使用者是 **sysadmin** 固定伺服器角色的成員時，[物件總管] 才會顯示 **[維護計畫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="2f71c-122">Object Explorer only displays the **Maintenance Plans** node for users who are members of the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-maintenance-plan-wizard"></a><a name="SSMSProcedure"></a><span data-ttu-id="2f71c-123">使用維護計畫嚮導</span><span class="sxs-lookup"><span data-stu-id="2f71c-123">Using Maintenance Plan Wizard</span></span>  
  
#### <a name="to-start-the-maintenance-plan-wizard"></a><span data-ttu-id="2f71c-124">啟動維護計畫精靈</span><span class="sxs-lookup"><span data-stu-id="2f71c-124">To start the Maintenance Plan Wizard</span></span>  
  
1.  <span data-ttu-id="2f71c-125">展開要在其中建立管理計畫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f71c-125">Expand the server where you want to create your management plan.</span></span>  
  
2.  <span data-ttu-id="2f71c-126">展開 **[管理]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f71c-126">Expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="2f71c-127">以滑鼠右鍵按一下 [維護計畫] 資料夾，然後選取 [維護計畫精靈]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-127">Right-click the **Maintenance Plans** folder and select **Maintenance Plan Wizard**.</span></span>  
  
4.  <span data-ttu-id="2f71c-128">在 **[SQL Server 維護計畫精靈]** 頁面上，按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-128">On the **SQL Server Maintenance Plan Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="2f71c-129">在 **[選取計畫屬性]** 頁面上：</span><span class="sxs-lookup"><span data-stu-id="2f71c-129">On the **Select Plan Properties** page:</span></span>  
  
    1.  <span data-ttu-id="2f71c-130">在 **[名稱]** 方塊中，輸入您要建立之維護計畫的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f71c-130">In the **Name** box, enter the name of the maintenance plan you are creating.</span></span>  
  
    2.  <span data-ttu-id="2f71c-131">在 **[描述]** 方塊中，簡要描述您的維護計畫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-131">In the **Description** box, briefly describe your maintenance plan.</span></span>  
  
    3.  <span data-ttu-id="2f71c-132">在 **[執行身分]** 清單中，指定 Microsoft SQL Server Agent 執行維護計畫時使用的認證。</span><span class="sxs-lookup"><span data-stu-id="2f71c-132">In the **Run as** list, specify the credential that Microsoft SQL Server Agent uses when executing the maintenance plan.</span></span>  
  
    4.  <span data-ttu-id="2f71c-133">選取 **[對每一項工作個別排程]** 或 **[對整個計畫單一排程或沒有排程]** ，指定維護計畫的週期性排程。</span><span class="sxs-lookup"><span data-stu-id="2f71c-133">Select either **Separate schedules for each task** or **Single schedule for the entire plan or no schedule** to specify the recurring schedule of the maintenance plan.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="2f71c-134">如果您選取 **[對每一項工作個別排程]**，則需針對維護計畫中的每一項工作執行下面 **e.**</span><span class="sxs-lookup"><span data-stu-id="2f71c-134">If you select **Separate schedules for each task**, you will need to follow the steps in **e.**</span></span> <span data-ttu-id="2f71c-135">中的步驟。</span><span class="sxs-lookup"><span data-stu-id="2f71c-135">below for each task in your maintenance plan.</span></span>  
  
    5.  <span data-ttu-id="2f71c-136">如果您選取 **[對整個計畫單一排程或沒有排程]** ，請按一下 **[排程]** 底下的 **[變更]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-136">If you selected **Single schedule for the entire plan or no schedule**, under **Schedule**, click **Change**.</span></span>  
  
        1.  <span data-ttu-id="2f71c-137">在 [新增作業排程] 對話方塊的 [名稱] 方塊中，輸入作業排程的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f71c-137">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
        2.  <span data-ttu-id="2f71c-138">在 **[排程類型]** 清單，選取排程類型：</span><span class="sxs-lookup"><span data-stu-id="2f71c-138">On the **Schedule type** list, select the type of schedule:</span></span>  
  
            -   <span data-ttu-id="2f71c-139">**當 SQL Server Agent 啟動時自動啟動**</span><span class="sxs-lookup"><span data-stu-id="2f71c-139">**Start automatically when SQL Server Agent starts**</span></span>  
  
            -   <span data-ttu-id="2f71c-140">**只要 CPU 閒置就啟動**</span><span class="sxs-lookup"><span data-stu-id="2f71c-140">**Start whenever the CPUs become idle**</span></span>  
  
            -   <span data-ttu-id="2f71c-141">**重複執行**：</span><span class="sxs-lookup"><span data-stu-id="2f71c-141">**Recurring**.</span></span> <span data-ttu-id="2f71c-142">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-142">This is the default selection.</span></span>  
  
            -   <span data-ttu-id="2f71c-143">**一次**</span><span class="sxs-lookup"><span data-stu-id="2f71c-143">**One time**</span></span>  
  
        3.  <span data-ttu-id="2f71c-144">選取或清除 **[已停用]** 核取方塊，以啟用或停用排程。</span><span class="sxs-lookup"><span data-stu-id="2f71c-144">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
        4.  <span data-ttu-id="2f71c-145">如果您選取 **[重複執行]** ：</span><span class="sxs-lookup"><span data-stu-id="2f71c-145">If you select **Recurring**:</span></span>  
  
            1.  <span data-ttu-id="2f71c-146">在 **[頻率]** 底下的 **[發生於]** 清單中，指定發生頻率：</span><span class="sxs-lookup"><span data-stu-id="2f71c-146">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
                -   <span data-ttu-id="2f71c-147">如果您選取 **[每天]** ，在 **[重複頻率]** 方塊中，輸入幾天重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="2f71c-147">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
                -   <span data-ttu-id="2f71c-148">如果您選取 **[每週]** ，在 **[重複頻率]** 方塊中，輸入幾週重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="2f71c-148">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="2f71c-149">選取一週中執行作業排程是在星期幾。</span><span class="sxs-lookup"><span data-stu-id="2f71c-149">Select the day or days of the week on which the job schedule is run.</span></span>  
  
                -   <span data-ttu-id="2f71c-150">如果您選取 **[每月]** ，可以選取 **[天]** 或 **[於]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-150">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                    -   <span data-ttu-id="2f71c-151">如果您選取 **[天]** ，請輸入執行作業排程的當月日期以及幾個月重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="2f71c-151">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="2f71c-152">例如，若要在每兩個月的 15 日執行一次作業排程，請選取 [日]，然後在第一個方塊中輸入 "15"，並在第二個方塊中輸入 "2"。</span><span class="sxs-lookup"><span data-stu-id="2f71c-152">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="2f71c-153">請注意，在第二個方塊中允許的最大數目是 "99"。</span><span class="sxs-lookup"><span data-stu-id="2f71c-153">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                    -   <span data-ttu-id="2f71c-154">如果您選取 **[於]** ，請選取執行作業排程的當月一週中特定的星期幾，以及幾個月重複一次作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="2f71c-154">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="2f71c-155">例如，若要在每兩個月的最後一個工作日執行一次作業排程，請選取 [日]，然後從第一個清單中選取 [最後一個]，並從第二個清單中選取 [工作日]，然後在最後一個方塊中輸入 "2"。</span><span class="sxs-lookup"><span data-stu-id="2f71c-155">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="2f71c-156">您也可以在前兩個清單中選取 [第一個]、[第二個]、[第三個] 或 [第四個]，以及特定工作日 (例如：星期日或星期三)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-156">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="2f71c-157">請注意，在最後一個方塊中允許的最大數目是 "99"。</span><span class="sxs-lookup"><span data-stu-id="2f71c-157">Please note that the largest number allowed in the last box is "99".</span></span>  
  
            2.  <span data-ttu-id="2f71c-158">在 **[每日頻率]** 底下，指定在執行作業排程當天重複作業排程的頻率：</span><span class="sxs-lookup"><span data-stu-id="2f71c-158">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
                -   <span data-ttu-id="2f71c-159">如果您選取 **[執行一次於]** ，請在 **[執行一次於]** 方塊中輸入執行作業排程的當天特定時間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-159">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="2f71c-160">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="2f71c-160">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
                -   <span data-ttu-id="2f71c-161">如果您選取 **[重複執行於每]** ，請在 **[頻率]** 底下指定在所選當天執行作業排程的頻率。</span><span class="sxs-lookup"><span data-stu-id="2f71c-161">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="2f71c-162">例如，若要在執行作業排程的當天每 2 個小時重複一次作業排程，請選取 [發生間隔]，在第一個方塊中輸入 "2"，然後從清單中選取 [小時]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-162">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="2f71c-163">您也可以從這個清單中選取 [分鐘] 和 [秒]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-163">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="2f71c-164">請注意，在第一個方塊中允許的最大數目是 "100"。</span><span class="sxs-lookup"><span data-stu-id="2f71c-164">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                     <span data-ttu-id="2f71c-165">在 **[開始時間]** 方塊中，輸入作業排程應該開始執行的時間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-165">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="2f71c-166">在 **[結束時間]** 方塊中，輸入作業排程應該停止重複的時間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-166">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="2f71c-167">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="2f71c-167">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            3.  <span data-ttu-id="2f71c-168">在 **[持續時間]** 底下的 **[開始日期]** ，輸入您希望作業排程開始執行的日期。</span><span class="sxs-lookup"><span data-stu-id="2f71c-168">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="2f71c-169">選取 **[結束日期]** 或 **[沒有結束日期]** ，以指示作業排程應該停止執行的日期。</span><span class="sxs-lookup"><span data-stu-id="2f71c-169">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="2f71c-170">如果您選取 **[結束日期]** ，請輸入您希望作業排程停止執行的日期。</span><span class="sxs-lookup"><span data-stu-id="2f71c-170">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
        5.  <span data-ttu-id="2f71c-171">如果您選取 [執行一次]，請在 [僅執行一次於] 底下的 [日期] 方塊中，輸入將要執行作業排程的日期。</span><span class="sxs-lookup"><span data-stu-id="2f71c-171">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="2f71c-172">在 **[時間]** 方塊中，輸入將要執行作業排程的時間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-172">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="2f71c-173">輸入時、分鐘和秒的時間，以及上午或下午。</span><span class="sxs-lookup"><span data-stu-id="2f71c-173">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        6.  <span data-ttu-id="2f71c-174">在 **[摘要]** 底下的 **[描述]** ，確認所有作業排程設定是否都正確。</span><span class="sxs-lookup"><span data-stu-id="2f71c-174">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
        7.  <span data-ttu-id="2f71c-175">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-175">Click **OK**.</span></span>  
  
    6.  <span data-ttu-id="2f71c-176">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-176">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="2f71c-177">在 **[選取目標伺服器]** 頁面上，選取要執行維護計畫所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f71c-177">On the **Select Target Servers** page, select the servers where you want to run the maintenance plan.</span></span> <span data-ttu-id="2f71c-178">只有設定為主要伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體才會顯示這個頁面。</span><span class="sxs-lookup"><span data-stu-id="2f71c-178">This page is only visible on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances that are configured as master servers.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f71c-179">若要建立多伺服器維護計畫，必須設定多伺服器環境，其中包含一個主要伺服器以及一或多個目標伺服器，而且應將本機伺服器設為主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f71c-179">To create a multiserver maintenance plan, a multiserver environment containing one master server and one or more target servers must be configured, and the local server should be configured as a master server.</span></span> <span data-ttu-id="2f71c-180">在多伺服器環境中，這個頁面會顯示 (本機) **(local)** 主要伺服器以及所有相對應的目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f71c-180">In multiserver environments, this page displays the **(local)** master server and all corresponding target servers.</span></span>  
  
7.  <span data-ttu-id="2f71c-181">在 **[選取維護工作]** 頁面上，選取一個或多個要加入至計畫的維護工作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-181">On the **Select Maintenance Tasks** page, select one or more maintenance tasks to add to the plan.</span></span> <span data-ttu-id="2f71c-182">選取所有必要的工作之後，按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-182">When you have selected all of the necessary tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f71c-183">在這裡選取的工作，將會決定您在下面的 [選取維護工作順序]\*\*\*\* 頁面之後需要完成的頁面。</span><span class="sxs-lookup"><span data-stu-id="2f71c-183">The tasks you select here will determine which pages you will need to complete after the **Select Maintenance Task Order** page below.</span></span>  
  
8.  <span data-ttu-id="2f71c-184">在 [選取維護工作順序] 頁面上選取一項工作，然後按一下 [上移...] 或 [下移...]，即可變更其執行順序。</span><span class="sxs-lookup"><span data-stu-id="2f71c-184">On the **Select Maintenance Task Order** page, select a task and click either **Move Up...** or **Move Down...** to change its order of execution.</span></span> <span data-ttu-id="2f71c-185">完成後或是您對目前的工作順序感到滿意時，按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-185">When finished, or if you are satisfied with the current order of tasks, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f71c-186">如果您在上面的 [選取計畫屬性]\*\*\*\* 頁面中選取了 [對每一項工作個別排程]\*\*\*\*，您將無法變更此頁面上維護工作的順序。</span><span class="sxs-lookup"><span data-stu-id="2f71c-186">If you selected **Separate schedules for each task** on the **Select Plan Properties** page above, you will not be able to change the order of the maintenance tasks on this page.</span></span>  
  
#### <a name="define-database-check-integrity-checkdb-tasks"></a><span data-ttu-id="2f71c-187">定義資料庫檢查完整性 (CHECKDB) 工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-187">Define Database Check Integrity (CHECKDB) Tasks</span></span>  
  
1.  <span data-ttu-id="2f71c-188">在 **[定義資料庫檢查完整性工作]** 頁面上，選擇要檢查其中使用者和系統資料表及索引之配置和結構整合性的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-188">On the **Define Database Check Integrity Task** page, choose the database or databases where the allocation and structural integrity of user and system tables and indexes will be checked.</span></span> <span data-ttu-id="2f71c-189">藉由執行 `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，這項工作就可確實回報任何有關資料庫完整性的問題，以便系統管理員或資料庫擁有者稍後解決。</span><span class="sxs-lookup"><span data-stu-id="2f71c-189">By running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement, this task ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span> <span data-ttu-id="2f71c-190">如需詳細資訊，請參閱 [DBCC CHECKDB &#40;TRANSACT-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)完成時，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-190">For more information, see [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="2f71c-191">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-191">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-192">[資料庫] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-192">**Databases** list</span></span>  
     <span data-ttu-id="2f71c-193">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-193">Specify the databases affected by this task.</span></span>  
  
    -   <span data-ttu-id="2f71c-194">**所有資料庫**</span><span class="sxs-lookup"><span data-stu-id="2f71c-194">**All databases**</span></span>  
  
         <span data-ttu-id="2f71c-195">產生維護計畫，該計畫會對所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行此工作，但 **tempdb** 除外。</span><span class="sxs-lookup"><span data-stu-id="2f71c-195">Generate a maintenance plan that runs this task against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
    -   <span data-ttu-id="2f71c-196">**系統資料庫**</span><span class="sxs-lookup"><span data-stu-id="2f71c-196">**System databases**</span></span>  
  
         <span data-ttu-id="2f71c-197">產生維護計畫，該計畫會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行此工作，但 **tempdb** 和使用者建立的資料庫除外。</span><span class="sxs-lookup"><span data-stu-id="2f71c-197">Generate a maintenance plan that runs this task against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb** and user-created databases.</span></span>  
  
    -   <span data-ttu-id="2f71c-198">**所有使用者資料庫 (不包括 master、model、msdb、tempdb)**</span><span class="sxs-lookup"><span data-stu-id="2f71c-198">**All user databases (excluding master, model, msdb, tempdb)**</span></span>  
  
         <span data-ttu-id="2f71c-199">產生維護計畫，針對所有使用者建立的資料庫執行此工作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-199">Generate a maintenance plan that runs this task against all user-created databases.</span></span> <span data-ttu-id="2f71c-200">不會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行任何維護工作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-200">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
    -   <span data-ttu-id="2f71c-201">**下列資料庫**</span><span class="sxs-lookup"><span data-stu-id="2f71c-201">**These databases**</span></span>  
  
         <span data-ttu-id="2f71c-202">產生維護計畫，僅針對那些已選取的資料庫執行此工作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-202">Generate a maintenance plan that runs this task against only those databases that are selected.</span></span> <span data-ttu-id="2f71c-203">如果選擇此選項，則必須在清單中至少選取一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-203">At least one database in the list must be selected if this option is chosen.</span></span>  
  
     <span data-ttu-id="2f71c-204">[包含索引] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-204">**Include indexes** check box</span></span>  
     <span data-ttu-id="2f71c-205">檢查所有的索引頁面以及資料表資料頁面的完整性。</span><span class="sxs-lookup"><span data-stu-id="2f71c-205">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
#### <a name="define-database-shrink-tasks"></a><span data-ttu-id="2f71c-206">定義資料庫壓縮工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-206">Define Database Shrink Tasks</span></span>  
  
1.  <span data-ttu-id="2f71c-207">在 **[定義壓縮資料庫工作]** 頁面上，使用 `DBCC SHRINKDATABASE` 陳述式搭配 `NOTRUNCATE` 或 `TRUNCATEONLY` 選項建立嘗試縮減所選取資料庫大小的工作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-207">On the **Define Shrink Database Task** page, create a task that attempts to reduce the size of the selected databases by using the `DBCC SHRINKDATABASE` statement, with either the `NOTRUNCATE` or `TRUNCATEONLY` option.</span></span> <span data-ttu-id="2f71c-208">如需詳細資訊，請參閱 [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-208">For more information, see [DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql).</span></span> <span data-ttu-id="2f71c-209">完成時，按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-209">When complete, click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="2f71c-210">為壓縮檔案所移動的資料可散佈至檔案中的任何可用位置。</span><span class="sxs-lookup"><span data-stu-id="2f71c-210">Data that is moved to shrink a file can be scattered to any available location in the file.</span></span> <span data-ttu-id="2f71c-211">如此會造成索引片段，並可能導致大範圍之索引搜尋的查詢效能變慢。</span><span class="sxs-lookup"><span data-stu-id="2f71c-211">This causes index fragmentation and can slow the performance of queries that search a range of the index.</span></span> <span data-ttu-id="2f71c-212">若要消除資料片段，可考慮在壓縮之後重建該檔案的索引。</span><span class="sxs-lookup"><span data-stu-id="2f71c-212">To eliminate the fragmentation, consider rebuilding the indexes on the file after shrinking.</span></span>  
  
     <span data-ttu-id="2f71c-213">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-213">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-214">[資料庫] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-214">**Databases** list</span></span>  
     <span data-ttu-id="2f71c-215">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-215">Specify the databases affected by this task.</span></span> <span data-ttu-id="2f71c-216">如需有關此清單上可用選項的詳細資訊，請參閱上述步驟 9。</span><span class="sxs-lookup"><span data-stu-id="2f71c-216">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="2f71c-217">[當資料庫超過下列大小時則進行壓縮] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-217">**Shrink database when it grows beyond** box</span></span>  
     <span data-ttu-id="2f71c-218">指定使工作執行的大小 (MB)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-218">Specify the size in megabytes that causes the task to execute.</span></span>  
  
     <span data-ttu-id="2f71c-219">[壓縮後要保持的可用空間量] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-219">**Amount of free space to remain after shrink** box</span></span>  
     <span data-ttu-id="2f71c-220">當資料庫檔案中的可用空間達到此大小時停止壓縮 (以百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-220">Stop shrinking when free space in database files reaches this size (as a percentage).</span></span>  
  
     <span data-ttu-id="2f71c-221">**將釋放的空間保留在資料庫檔案中**</span><span class="sxs-lookup"><span data-stu-id="2f71c-221">**Retain freed space in database files**</span></span>  
     <span data-ttu-id="2f71c-222">資料庫會壓縮至連續的分頁，但並不會取消分頁的配置，而且資料庫檔案不會壓縮。</span><span class="sxs-lookup"><span data-stu-id="2f71c-222">The database is condensed to contiguous pages but the pages are not deallocated, and the database files do not shrink.</span></span> <span data-ttu-id="2f71c-223">如果您預期資料庫會再次展開，且您不希望重新配置空間，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-223">Use this option if you expect the database to expand again, and you do not want to reallocate space.</span></span> <span data-ttu-id="2f71c-224">如果使用這個選項，則會儘量不壓縮資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-224">With this option, the database files do not shrink as much as possible.</span></span> <span data-ttu-id="2f71c-225">這會使用 NOTRUNCATE 選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-225">This uses the NOTRUNCATE option.</span></span>  
  
     <span data-ttu-id="2f71c-226">**將釋放的空間交還給作業系統**</span><span class="sxs-lookup"><span data-stu-id="2f71c-226">**Return freed space to operating system**</span></span>  
     <span data-ttu-id="2f71c-227">資料庫會緊縮至連續的分頁，且分頁會釋放給作業系統，以供其他程式使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-227">The database is condensed to contiguous pages and the pages are released back to the operating system for use by other programs.</span></span> <span data-ttu-id="2f71c-228">此資料庫檔案會盡可能壓縮。</span><span class="sxs-lookup"><span data-stu-id="2f71c-228">This database files shrink as much as possible.</span></span> <span data-ttu-id="2f71c-229">這會使用 TRUNCATEONLY 選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-229">This uses the TRUNCATEONLY option.</span></span> <span data-ttu-id="2f71c-230">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-230">This is the default option.</span></span>  
  
#### <a name="define-the-index-tasks"></a><span data-ttu-id="2f71c-231">定義索引工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-231">Define the Index Tasks</span></span>  
  
1.  <span data-ttu-id="2f71c-232">在 [定義重新組織索引工作]On the  頁面上選取伺服器並移動其中的索引頁面，使其成為更有搜尋效率的順序。</span><span class="sxs-lookup"><span data-stu-id="2f71c-232">On the **Define Reorganize Index Task** page, select the server or servers where you'll be moving index pages into a more efficient search order.</span></span> <span data-ttu-id="2f71c-233">此工作會使用 `ALTER INDEX ... REORGANIZE` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-233">This task uses the `ALTER INDEX ... REORGANIZE` statement.</span></span> <span data-ttu-id="2f71c-234">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-234">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).</span></span> <span data-ttu-id="2f71c-235">完成時，按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-235">When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="2f71c-236">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-236">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-237">[資料庫] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-237">**Databases** list</span></span>  
     <span data-ttu-id="2f71c-238">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-238">Specify the databases affected by this task.</span></span> <span data-ttu-id="2f71c-239">如需有關此清單上可用選項的詳細資訊，請參閱上述步驟 9。</span><span class="sxs-lookup"><span data-stu-id="2f71c-239">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="2f71c-240">[物件] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-240">**Object** list</span></span>  
     <span data-ttu-id="2f71c-241">限制 [選取範圍] 清單僅顯示資料表或檢視，或兩者都顯示。</span><span class="sxs-lookup"><span data-stu-id="2f71c-241">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="2f71c-242">此清單只有在從上述 **[資料庫]** 清單選擇單一資料庫時才可使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-242">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="2f71c-243">[選取範圍] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-243">**Selection** list</span></span>  
     <span data-ttu-id="2f71c-244">指定受此工作影響的資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="2f71c-244">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="2f71c-245">[物件] 方塊中的 **[資料表和檢視]** 為選取狀態時無法使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-245">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="2f71c-246">[壓縮大型物件] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-246">**Compact large objects** check box</span></span>  
     <span data-ttu-id="2f71c-247">可能時取消配置給資料表和檢視的空間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-247">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="2f71c-248">此選項使用 `ALTER INDEX ... LOB_COMPACTION = ON`。</span><span class="sxs-lookup"><span data-stu-id="2f71c-248">This option uses `ALTER INDEX ... LOB_COMPACTION = ON`.</span></span>  
  
2.  <span data-ttu-id="2f71c-249">在 [定義重建索引工作] 頁面上，選取要在其中重新建立多個索引的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-249">On the **Define Rebuild Index Task** page, select the database or databases where you'll be re-creating multiple indexes.</span></span> <span data-ttu-id="2f71c-250">此工作會使用 `ALTER INDEX ... REBUILD PARTITION` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-250">This task uses the `ALTER INDEX ... REBUILD PARTITION` statement.</span></span> <span data-ttu-id="2f71c-251">如需詳細資訊，請參閱 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)。)完成後，按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-251">For more information, see [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).) When complete, click **Next**.</span></span>  
  
     <span data-ttu-id="2f71c-252">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-252">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-253">[資料庫] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-253">**Databases** list</span></span>  
     <span data-ttu-id="2f71c-254">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-254">Specify the databases affected by this task.</span></span> <span data-ttu-id="2f71c-255">如需有關此清單上可用選項的詳細資訊，請參閱上述步驟 9。</span><span class="sxs-lookup"><span data-stu-id="2f71c-255">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="2f71c-256">[物件] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-256">**Object** list</span></span>  
     <span data-ttu-id="2f71c-257">限制 [選取範圍] 清單僅顯示資料表或檢視，或兩者都顯示。</span><span class="sxs-lookup"><span data-stu-id="2f71c-257">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="2f71c-258">此清單只有在從上述 **[資料庫]** 清單選擇單一資料庫時才可使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-258">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="2f71c-259">[選取範圍] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-259">**Selection** list</span></span>  
     <span data-ttu-id="2f71c-260">指定受此工作影響的資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="2f71c-260">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="2f71c-261">[物件] 方塊中的 **[資料表和檢視]** 為選取狀態時無法使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-261">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="2f71c-262">[可用空間選項] 區域</span><span class="sxs-lookup"><span data-stu-id="2f71c-262">**Free space options** area</span></span>  
     <span data-ttu-id="2f71c-263">顯示將填滿因數套用至索引和資料表的選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-263">Presents options for applying fill factor to indexes and tables.</span></span>  
  
     <span data-ttu-id="2f71c-264">**預設每頁可用空間**</span><span class="sxs-lookup"><span data-stu-id="2f71c-264">**Default free space per page**</span></span>  
     <span data-ttu-id="2f71c-265">使用預設的可用空間量重新組織頁面。</span><span class="sxs-lookup"><span data-stu-id="2f71c-265">Reorganizes the pages with the default amount of free space.</span></span> <span data-ttu-id="2f71c-266">這會卸除資料庫中的資料表索引，並以建立索引時指定的填滿因數重新建立它們。</span><span class="sxs-lookup"><span data-stu-id="2f71c-266">This will drop the indexes on the tables in the database and re-create them with the fill factor that was specified when the indexes were created.</span></span> <span data-ttu-id="2f71c-267">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-267">This is the default option.</span></span>  
  
     <span data-ttu-id="2f71c-268">[將每頁可用空間變更為] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-268">**Change free space per page to** box</span></span>  
     <span data-ttu-id="2f71c-269">將資料庫中的資料表索引卸除，並以新的、自動計算的填滿因數重新建立它們，以在索引頁面上保留指定的可用空間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-269">Drop the indexes on the tables in the database and re-create them with a new, automatically calculated fill factor, thereby reserving the specified amount of free space on the index pages.</span></span> <span data-ttu-id="2f71c-270">百分比愈高，在索引頁面上保留的可用空間就愈多，而索引也愈大。</span><span class="sxs-lookup"><span data-stu-id="2f71c-270">The higher the percentage, the more free space is reserved on the index pages, and the larger the index grows.</span></span> <span data-ttu-id="2f71c-271">有效的數值範圍為 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="2f71c-271">Valid values are from 0 through 100.</span></span> <span data-ttu-id="2f71c-272">使用 `FILLFACTOR` 選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-272">Uses the `FILLFACTOR` option.</span></span>  
  
     <span data-ttu-id="2f71c-273">[進階選項] 區域</span><span class="sxs-lookup"><span data-stu-id="2f71c-273">**Advanced options** area</span></span>  
     <span data-ttu-id="2f71c-274">顯示用於排序索引和重新索引的其他選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-274">Presents additional options for sorting indexes and reindexing.</span></span>  
  
     <span data-ttu-id="2f71c-275">[在 tempdb 中排序結果]核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-275">**Sort results in tempdb** check box</span></span>  
     <span data-ttu-id="2f71c-276">使用 `SORT_IN_TEMPDB` 選項，該選項會決定要暫時儲存索引建立期間所產生中繼排序結果的位置。</span><span class="sxs-lookup"><span data-stu-id="2f71c-276">Uses the `SORT_IN_TEMPDB` option which determines where the intermediate sort results, generated during index creation, are temporarily stored.</span></span> <span data-ttu-id="2f71c-277">如果不需要排序作業，或可以在記憶體中執行排序，便會忽略 `SORT_IN_TEMPDB` 選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-277">If a sort operation is not required, or if the sort can be performed in memory, the `SORT_IN_TEMPDB` option is ignored.</span></span>  
  
     <span data-ttu-id="2f71c-278">[重新索引時，索引保留在線上] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-278">**Keep index online while reindexing** check box</span></span>  
     <span data-ttu-id="2f71c-279">使用 `ONLINE` 選項，此選項可讓使用者在索引作業期間存取基礎資料表或叢集索引資料，以及任何相關的非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="2f71c-279">Uses the `ONLINE` option which allows users to access the underlying table or clustered index data and any associated nonclustered indexes during index operations.</span></span> <span data-ttu-id="2f71c-280">選取此選項會啟動其他索引的選項，而這些索引不允許線上重建：[不要重建索引] 和 [離線重建索引]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-280">Selecting this option activates additional options for rebuilding indexes that do not allow for online rebuilds: **Do not rebuild indexes** and **Rebuild indexes offline**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f71c-281">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的所有版本都無法使用線上索引作業。</span><span class="sxs-lookup"><span data-stu-id="2f71c-281">Online index operations are not available in every edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="2f71c-282">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2f71c-282">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
#### <a name="define-the-update-statistics-task"></a><span data-ttu-id="2f71c-283">定義更新統計資料工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-283">Define the Update Statistics Task</span></span>  
  
1.  <span data-ttu-id="2f71c-284">在 **[定義更新統計資料工作]** 頁面上，定義要更新其中資料表和索引統計資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-284">On the **Define Update Statistics Task** page, define the database or databases on which table and index statistics will be updated.</span></span> <span data-ttu-id="2f71c-285">此工作會使用 `UPDATE STATISTICS` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-285">This task uses the `UPDATE STATISTICS` statement.</span></span> <span data-ttu-id="2f71c-286">如需詳細資訊，請參閱[更新統計資料 &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) 完成時，請按一下 [下一步]</span><span class="sxs-lookup"><span data-stu-id="2f71c-286">For more information, see [UPDATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/update-statistics-transact-sql) When finished, click **Next**</span></span>  
  
     <span data-ttu-id="2f71c-287">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-287">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-288">[資料庫] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-288">**Databases** list</span></span>  
     <span data-ttu-id="2f71c-289">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-289">Specify the databases affected by this task.</span></span> <span data-ttu-id="2f71c-290">如需有關此清單上可用選項的詳細資訊，請參閱上述步驟 9。</span><span class="sxs-lookup"><span data-stu-id="2f71c-290">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="2f71c-291">[物件] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-291">**Object** list</span></span>  
     <span data-ttu-id="2f71c-292">限制 [選取範圍] 清單僅顯示資料表或檢視，或兩者都顯示。</span><span class="sxs-lookup"><span data-stu-id="2f71c-292">Limit the **Selection** list to display tables, views, or both.</span></span> <span data-ttu-id="2f71c-293">此清單只有在從上述 **[資料庫]** 清單選擇單一資料庫時才可使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-293">This list is only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="2f71c-294">[選取範圍] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-294">**Selection** list</span></span>  
     <span data-ttu-id="2f71c-295">指定受此工作影響的資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="2f71c-295">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="2f71c-296">[物件] 方塊中的 **[資料表和檢視]** 為選取狀態時無法使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-296">Not available when **Tables and Views** is selected in the Object box.</span></span>  
  
     <span data-ttu-id="2f71c-297">**所有現有的統計資料**</span><span class="sxs-lookup"><span data-stu-id="2f71c-297">**All existing statistics**</span></span>  
     <span data-ttu-id="2f71c-298">同時更新資料行與索引的統計資料。</span><span class="sxs-lookup"><span data-stu-id="2f71c-298">Update statistics for both columns and indexes.</span></span>  
  
     <span data-ttu-id="2f71c-299">**僅限資料行統計資料**</span><span class="sxs-lookup"><span data-stu-id="2f71c-299">**Column statistics only**</span></span>  
     <span data-ttu-id="2f71c-300">僅更新資料行統計資料。</span><span class="sxs-lookup"><span data-stu-id="2f71c-300">Only update column statistics.</span></span> <span data-ttu-id="2f71c-301">使用 `WITH COLUMNS` 選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-301">Uses the `WITH COLUMNS` option.</span></span>  
  
     <span data-ttu-id="2f71c-302">**僅限索引統計資料**</span><span class="sxs-lookup"><span data-stu-id="2f71c-302">**Index statistics only**</span></span>  
     <span data-ttu-id="2f71c-303">僅更新索引統計資料。</span><span class="sxs-lookup"><span data-stu-id="2f71c-303">Only update index statistics.</span></span> <span data-ttu-id="2f71c-304">使用 `WITH INDEX` 選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-304">Uses the `WITH INDEX` option.</span></span>  
  
     <span data-ttu-id="2f71c-305">**掃描類型**</span><span class="sxs-lookup"><span data-stu-id="2f71c-305">**Scan type**</span></span>  
     <span data-ttu-id="2f71c-306">用來蒐集更新統計資料的掃描類型。</span><span class="sxs-lookup"><span data-stu-id="2f71c-306">Type of scan used to gather updated statistics.</span></span>  
  
     <span data-ttu-id="2f71c-307">**完整掃描**</span><span class="sxs-lookup"><span data-stu-id="2f71c-307">**Full scan**</span></span>  
     <span data-ttu-id="2f71c-308">讀取資料表或檢視中的所有資料列來蒐集統計資料。</span><span class="sxs-lookup"><span data-stu-id="2f71c-308">Read all rows in the table or view to gather the statistics.</span></span>  
  
     <span data-ttu-id="2f71c-309">**取樣者**</span><span class="sxs-lookup"><span data-stu-id="2f71c-309">**Sample by**</span></span>  
     <span data-ttu-id="2f71c-310">當收集較大資料表或檢視的統計資料時，指定要取樣的資料表或索引檢視百分比或資料列數。</span><span class="sxs-lookup"><span data-stu-id="2f71c-310">Specify the percentage of the table or indexed view, or the number of rows to sample when collecting statistics for larger tables or views.</span></span>  
  
#### <a name="define-the-history-cleanup-task"></a><span data-ttu-id="2f71c-311">定義記錄清除工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-311">Define the History Cleanup Task</span></span>  
  
1.  <span data-ttu-id="2f71c-312">在 **[定義記錄清除工作]** 頁面上，定義要捨棄其中舊工作記錄的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-312">On the **Define History Cleanup Task** page, define the database or databases where you want to discard old task history.</span></span> <span data-ttu-id="2f71c-313">此工作會使用 `EXEC sp_purge_jobhistory`、 `EXEC sp_maintplan_delete_log`和 `EXEC sp_delete_backuphistory` 陳述式移除 **msdb** 資料表中的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="2f71c-313">This task uses the `EXEC sp_purge_jobhistory`, `EXEC sp_maintplan_delete_log`, and `EXEC sp_delete_backuphistory` statements to remove history information from the **msdb** tables.</span></span> <span data-ttu-id="2f71c-314">完成後，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-314">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="2f71c-315">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-315">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-316">**選取要刪除的記錄資料**</span><span class="sxs-lookup"><span data-stu-id="2f71c-316">**Select the historical data to delete**</span></span>  
     <span data-ttu-id="2f71c-317">選擇要刪除的工作資料類型</span><span class="sxs-lookup"><span data-stu-id="2f71c-317">Chose the type of task data to delete/</span></span>  
  
     <span data-ttu-id="2f71c-318">**備份與還原記錄**</span><span class="sxs-lookup"><span data-stu-id="2f71c-318">**Backup and restore history**</span></span>  
     <span data-ttu-id="2f71c-319">保留最近建立備份時的記錄，有助於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在您要還原資料庫時，建立復原計畫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-319">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="2f71c-320">保留期限至少應該是完整資料庫備份的頻率。</span><span class="sxs-lookup"><span data-stu-id="2f71c-320">The retention period should be at least the frequency of full database backups.</span></span>  
  
     <span data-ttu-id="2f71c-321">**SQL Server Agent 作業記錄**</span><span class="sxs-lookup"><span data-stu-id="2f71c-321">**SQL Server Agent Job history**</span></span>  
     <span data-ttu-id="2f71c-322">這個記錄可以幫助您疑難排解失敗的作業，或判斷資料庫動作為何發生。</span><span class="sxs-lookup"><span data-stu-id="2f71c-322">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="2f71c-323">**維護計畫記錄**</span><span class="sxs-lookup"><span data-stu-id="2f71c-323">**Maintenance Plan history**</span></span>  
     <span data-ttu-id="2f71c-324">這個記錄可以幫助您疑難排解失敗的維護計畫作業，或判斷資料庫動作為何發生。</span><span class="sxs-lookup"><span data-stu-id="2f71c-324">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
     <span data-ttu-id="2f71c-325">**移除早於下列時限的記錄資料**</span><span class="sxs-lookup"><span data-stu-id="2f71c-325">**Remove historical data older than**</span></span>  
     <span data-ttu-id="2f71c-326">指定您想要刪除的項目之存在時間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-326">Specify age of items that you want to delete.</span></span> <span data-ttu-id="2f71c-327">您可以指定 [小時]、[天]、[週] (預設)、[月] 或 [年]</span><span class="sxs-lookup"><span data-stu-id="2f71c-327">You can specify **Hour(s)**, **Day(s)**, **Week(s)** (the default), **Month(s)**, or **Year(s)**</span></span>  
  
#### <a name="define-the-execute-agent-job-task"></a><span data-ttu-id="2f71c-328">定義執行代理程式作業工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-328">Define the Execute Agent Job Task</span></span>  
  
1.  <span data-ttu-id="2f71c-329">在 **[定義執行代理程式作業工作]** 頁面的 **[可用的 SQL Server Agent 作業]** 底下，選擇要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="2f71c-329">On the **Define Execute Agent Job Task** page, under **Available SQL Server Agent jobs**, choose the job or jobs to run.</span></span> <span data-ttu-id="2f71c-330">如果沒有 SQL Agent 作業，就無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-330">This option will not be available if you have no SQL Agent jobs.</span></span> <span data-ttu-id="2f71c-331">此工作會使用 `EXEC sp_start_job` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-331">This task uses the `EXEC sp_start_job` statement.</span></span> <span data-ttu-id="2f71c-332">如需詳細資訊，請參閱 [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql) 完成時，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-332">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)When finished, click **Next**.</span></span>  
  
#### <a name="define-backup-tasks"></a><span data-ttu-id="2f71c-333">定義備份工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-333">Define Backup Tasks</span></span>  
  
1.  <span data-ttu-id="2f71c-334">在 [Define Backup Database (Full) Task] (定義備份資料庫 (完整) 工作) 頁面上，選取要執行完整備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-334">On the **Define Backup Database (Full) Task** page, select the database or databases on which to run a full backup.</span></span> <span data-ttu-id="2f71c-335">此工作會使用 `BACKUP DATABASE` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-335">This task uses the `BACKUP DATABASE` statement.</span></span> <span data-ttu-id="2f71c-336">如需詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-336">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="2f71c-337">完成後，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-337">When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="2f71c-338">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-338">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-339">[備份類型] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-339">**Backup type** list</span></span>  
     <span data-ttu-id="2f71c-340">顯示要執行的備份類型。</span><span class="sxs-lookup"><span data-stu-id="2f71c-340">Displays the type of backup to be performed.</span></span> <span data-ttu-id="2f71c-341">這是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2f71c-341">This is read-only.</span></span>  
  
     <span data-ttu-id="2f71c-342">[資料庫] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-342">**Databases** list</span></span>  
     <span data-ttu-id="2f71c-343">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-343">Specify the databases affected by this task.</span></span> <span data-ttu-id="2f71c-344">如需有關此清單上可用選項的詳細資訊，請參閱上述步驟 9。</span><span class="sxs-lookup"><span data-stu-id="2f71c-344">See step 9, above, for more information on the available options on this list.</span></span>  
  
     <span data-ttu-id="2f71c-345">**備份元件**</span><span class="sxs-lookup"><span data-stu-id="2f71c-345">**Backup component**</span></span>  
     <span data-ttu-id="2f71c-346">選取 [資料庫]，即可備份整個資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-346">Select **Database** to back up the entire database.</span></span> <span data-ttu-id="2f71c-347">選取 **[檔案與檔案群組]** ，即可僅備份資料庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="2f71c-347">Select **File and filegroups** to back up only a portion of the database.</span></span> <span data-ttu-id="2f71c-348">如果已選取，請提供檔案或檔案群組名稱。</span><span class="sxs-lookup"><span data-stu-id="2f71c-348">If selected, provide the file or filegroup name.</span></span> <span data-ttu-id="2f71c-349">在 **[資料庫]** 方塊中選取多個資料庫時，僅能指定 **[備份元件]** 的 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-349">When multiple databases are selected in the **Databases** box, only specify **Databases** for the **Backup components**.</span></span> <span data-ttu-id="2f71c-350">若要執行檔案或檔案群組備份，請為每個資料庫建立工作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-350">To perform file or filegroup backups, create a task for each database.</span></span> <span data-ttu-id="2f71c-351">這些選項只有在從上述 **[資料庫]** 清單選擇單一資料庫時才可使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-351">These options are only available if a single database is chosen from the **Databases** list above.</span></span>  
  
     <span data-ttu-id="2f71c-352">[備份組逾期時間] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-352">**Backup set will expire** check box</span></span>  
     <span data-ttu-id="2f71c-353">指定何時可以覆寫這個備份的備份組。</span><span class="sxs-lookup"><span data-stu-id="2f71c-353">Specifies when the backup set for this backup can be overwritten.</span></span> <span data-ttu-id="2f71c-354">選取 **[之後]** ，然後輸入到期的天數，或選取 **[於]** ，然後輸入到期日。</span><span class="sxs-lookup"><span data-stu-id="2f71c-354">Select **After** and enter a number of days to expiration, or select **On** and enter a date of expiration.</span></span> <span data-ttu-id="2f71c-355">如果選取 **[URL]** 做為備份目的地，則會停用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-355">This option is disabled if **URL** is selected as the backup destination.</span></span>  
  
     <span data-ttu-id="2f71c-356">**備份至**</span><span class="sxs-lookup"><span data-stu-id="2f71c-356">**Back up to**</span></span>  
     <span data-ttu-id="2f71c-357">指定要用來備份資料庫的媒體。</span><span class="sxs-lookup"><span data-stu-id="2f71c-357">Specifies the medium on which to back up the database.</span></span> <span data-ttu-id="2f71c-358">選取 **[磁碟]** 、 **[磁帶]** 或 **[URL]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-358">Select **Disk**, **Tape**, or **URL**.</span></span> <span data-ttu-id="2f71c-359">唯有安裝在包含資料庫之電腦的磁帶裝置可以使用。</span><span class="sxs-lookup"><span data-stu-id="2f71c-359">Only tape devices attached to the computer containing the database are available.</span></span>  
  
     <span data-ttu-id="2f71c-360">**跨越一或多個檔案備份資料庫**</span><span class="sxs-lookup"><span data-stu-id="2f71c-360">**Back up database(s) across one or more files**</span></span>  
     <span data-ttu-id="2f71c-361">按一下 [新增]，即可開啟 [選取備份目的地] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2f71c-361">Click **Add** to open the **Select Backup Destination** dialog box.</span></span> <span data-ttu-id="2f71c-362">如果選取 [URL] 做為備份目的地，則會停用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-362">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="2f71c-363">按一下 **[移除]** ，即可從方塊中移除檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-363">Click **Remove** to remove a file from the box.</span></span>  
  
     <span data-ttu-id="2f71c-364">按一下 **[內容]** ，即可讀取檔案標頭，並顯示檔案目前的備份內容。</span><span class="sxs-lookup"><span data-stu-id="2f71c-364">Click **Contents** to read the file header and display the current backup contents of the file.</span></span>  
  
     <span data-ttu-id="2f71c-365">[選取備份目的地] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-365">**Select Backup Destination** dialog box</span></span>  
     <span data-ttu-id="2f71c-366">選取檔案、磁帶機或備份裝置做為備份目的地。</span><span class="sxs-lookup"><span data-stu-id="2f71c-366">Select the file, tape drive, or backup device for the backup destination.</span></span> <span data-ttu-id="2f71c-367">如果選取 [URL] 做為備份目的地，則會停用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-367">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="2f71c-368">[如果備份檔案存在] 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-368">**If backup files exist** list</span></span>  
     <span data-ttu-id="2f71c-369">指定如何處理現有的備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-369">Specify how to handle existing backups.</span></span> <span data-ttu-id="2f71c-370">選取 **[附加]** ，即可在檔案或磁帶中之任何現有的備份後面加入新的備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-370">Select **Append** to add the new backups after any existing backups in the file or on the tape.</span></span> <span data-ttu-id="2f71c-371">選取 **[覆寫]** 以移除檔案或磁帶的舊內容，並以此新的備份取代。</span><span class="sxs-lookup"><span data-stu-id="2f71c-371">Select **Overwrite** to remove the old content of a file or tape, and replace it with this new backup.</span></span>  
  
     <span data-ttu-id="2f71c-372">**為每個資料庫建立一個備份檔案**</span><span class="sxs-lookup"><span data-stu-id="2f71c-372">**Create a backup file for every database**</span></span>  
     <span data-ttu-id="2f71c-373">在資料夾方塊裡所指定的位置中，建立備份檔案，</span><span class="sxs-lookup"><span data-stu-id="2f71c-373">Create a backup file in the location specified in the folder box.</span></span> <span data-ttu-id="2f71c-374">為選取的每個資料庫建立一個檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-374">One file is created for each database selected.</span></span> <span data-ttu-id="2f71c-375">如果選取 [URL] 做為備份目的地，則會停用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-375">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="2f71c-376">[為每個資料庫建立一個子目錄] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-376">**Create a sub-directory for each database** check box</span></span>  
     <span data-ttu-id="2f71c-377">根據維護計劃針對要備份的資料庫，在指定的磁碟目錄下建立一個子目錄，以放置資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-377">Create a sub-directory under the specified disk directory that contains the database backup for each database being backed up as part of the maintenance plan.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2f71c-378">子目錄會繼承上層目錄的權限。</span><span class="sxs-lookup"><span data-stu-id="2f71c-378">The sub-directory will inherit permissions from the parent directory.</span></span> <span data-ttu-id="2f71c-379">限制權限以避免未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="2f71c-379">Restrict permissions to avoid unauthorized access.</span></span>  
  
     <span data-ttu-id="2f71c-380">[資料夾] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-380">**Folder** box</span></span>  
     <span data-ttu-id="2f71c-381">指定包含自動建立的資料庫檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2f71c-381">Specify the folder to contain the automatically created database files.</span></span> <span data-ttu-id="2f71c-382">如果選取 [URL] 做為備份目的地，則會停用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-382">This option is disabled if you selected URL as the backup destination.</span></span>  
  
     <span data-ttu-id="2f71c-383">**SQL 認證**</span><span class="sxs-lookup"><span data-stu-id="2f71c-383">**SQL Credential**</span></span>  
     <span data-ttu-id="2f71c-384">選取用來驗證 Azure 儲存體的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="2f71c-384">Select a SQL Credential used to authenticate to Azure Storage.</span></span> <span data-ttu-id="2f71c-385">如果沒有現有可用的 SQL 認證，請按一下 **[建立]** 按鈕建立新的 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="2f71c-385">If you do not have an existing SQL Credential you can use, click the **Create** button to create a new SQL Credential.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2f71c-386">在您按一下 **[建立]** 時開啟的對話方塊需要管理憑證或訂閱的發行設定檔。</span><span class="sxs-lookup"><span data-stu-id="2f71c-386">The dialog that opens when you click **Create** requires a management certificate or the publishing profile for the subscription.</span></span> <span data-ttu-id="2f71c-387">如果您無法存取管理憑證或發行設定檔，可以使用 Transact-SQL 或 SQL Server Management Studio 來指定儲存體帳戶名稱和存取金鑰資訊，藉以建立 SQL 認證。</span><span class="sxs-lookup"><span data-stu-id="2f71c-387">If you do not have access to the management certificate or publishing profile, you can create a SQL Credential by specifying the storage account name and access key information using Transact-SQL or SQL Server Management Studio.</span></span> <span data-ttu-id="2f71c-388">請參閱[建立認證](../security/authentication-access/create-a-credential.md#Credential)主題中的範例程式碼，以使用 transact-sql 來建立認證。</span><span class="sxs-lookup"><span data-stu-id="2f71c-388">See the sample code in the [To create a credential](../security/authentication-access/create-a-credential.md#Credential) topic to create a credential using Transact-SQL.</span></span> <span data-ttu-id="2f71c-389">或者，使用 SQL Server Management Studio，在資料庫引擎執行個體中，以滑鼠右鍵按一下 **[安全性]**、選取 **[新增]**，然後選取 **[認證]**。</span><span class="sxs-lookup"><span data-stu-id="2f71c-389">Alternatively, using SQL Server Management Studio, from the database engine instance, right click **Security**, select **New**, and select **Credential**.</span></span> <span data-ttu-id="2f71c-390">針對 **[識別]** 指定儲存體帳戶名稱，並且在 **[密碼]** 欄位中指定存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f71c-390">Specify the storage account name for **Identity** and the access key in the **Password** field.</span></span>  
  
     <span data-ttu-id="2f71c-391">**Azure 儲存體容器**</span><span class="sxs-lookup"><span data-stu-id="2f71c-391">**Azure storage container**</span></span>  
     <span data-ttu-id="2f71c-392">指定 Azure 儲存體容器的名稱</span><span class="sxs-lookup"><span data-stu-id="2f71c-392">Specify the name of the Azure storage container</span></span>  
  
     <span data-ttu-id="2f71c-393">**URL 前置詞：**</span><span class="sxs-lookup"><span data-stu-id="2f71c-393">**URL prefix:**</span></span>  
     <span data-ttu-id="2f71c-394">這會根據儲存在 SQL 認證中的儲存體帳戶資訊，以及您指定的 Azure 儲存體容器名稱自動產生。</span><span class="sxs-lookup"><span data-stu-id="2f71c-394">This is automatically generated based on the storage account information stored in the SQL Credential, and Azure storage container name you specified.</span></span> <span data-ttu-id="2f71c-395">建議您除非使用的網域採用 **\<storage account>.blob.core.windows.net** 以外的格式，否則請勿編輯此欄位中的資訊。</span><span class="sxs-lookup"><span data-stu-id="2f71c-395">We recommend that you do not edit the information in this field unless you are using a domain that uses a format other than **\<storage account>.blob.core.windows.net**.</span></span>  
  
     <span data-ttu-id="2f71c-396">[備份副檔名] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-396">**Backup file extension** box</span></span>  
     <span data-ttu-id="2f71c-397">指定備份檔案所用的副檔名。</span><span class="sxs-lookup"><span data-stu-id="2f71c-397">Specify the extension to use for the backup files.</span></span> <span data-ttu-id="2f71c-398">預設值是 .bak。</span><span class="sxs-lookup"><span data-stu-id="2f71c-398">The default is .bak.</span></span>  
  
     <span data-ttu-id="2f71c-399">[驗證備份完整性] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-399">**Verify backup integrity** check box</span></span>  
     <span data-ttu-id="2f71c-400">確認備份組是完整的，且所有磁碟區都可以讀取。</span><span class="sxs-lookup"><span data-stu-id="2f71c-400">Verify that the backup set is complete and that all volumes are readable.</span></span>  
  
     <span data-ttu-id="2f71c-401">**備份加密**</span><span class="sxs-lookup"><span data-stu-id="2f71c-401">**Backup Encryption**</span></span>  
     <span data-ttu-id="2f71c-402">若要建立加密的備份，請核取 [加密備份] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f71c-402">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="2f71c-403">選取要加密步驟所要使用的加密演算法，並提供現有憑證或非對稱金鑰清單中的憑證或非對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f71c-403">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="2f71c-404">可用於加密的演算法包括：</span><span class="sxs-lookup"><span data-stu-id="2f71c-404">The available algorithms for encryption are:</span></span>  
  
    -   <span data-ttu-id="2f71c-405">AES 128</span><span class="sxs-lookup"><span data-stu-id="2f71c-405">AES 128</span></span>  
  
    -   <span data-ttu-id="2f71c-406">AES 192</span><span class="sxs-lookup"><span data-stu-id="2f71c-406">AES 192</span></span>  
  
    -   <span data-ttu-id="2f71c-407">AES 256</span><span class="sxs-lookup"><span data-stu-id="2f71c-407">AES 256</span></span>  
  
    -   <span data-ttu-id="2f71c-408">三重 DES</span><span class="sxs-lookup"><span data-stu-id="2f71c-408">Triple DES</span></span>  
  
     <span data-ttu-id="2f71c-409">如果選擇附加至現有的備份集，則會停用加密選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-409">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
  
     <span data-ttu-id="2f71c-410">這建議作法是讓您備份憑證或金鑰，並將其儲存在不同位置，而不是加密備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-410">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
  
     <span data-ttu-id="2f71c-411">僅支援位於可延伸金鑰管理 (EKM) 中的金鑰。</span><span class="sxs-lookup"><span data-stu-id="2f71c-411">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
     <span data-ttu-id="2f71c-412">**[設定備份壓縮]** 清單</span><span class="sxs-lookup"><span data-stu-id="2f71c-412">**Set backup compression**  list</span></span>  
     <span data-ttu-id="2f71c-413">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (或更新的版本) 中，選取下列其中一個 [備份壓縮](../backup-restore/backup-compression-sql-server.md) 值：</span><span class="sxs-lookup"><span data-stu-id="2f71c-413">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), select one the following [backup compression](../backup-restore/backup-compression-sql-server.md) values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="2f71c-414">**使用預設伺服器設定**</span><span class="sxs-lookup"><span data-stu-id="2f71c-414">**Use the default server setting**</span></span>|<span data-ttu-id="2f71c-415">按一下即可使用伺服器層級的預設值。</span><span class="sxs-lookup"><span data-stu-id="2f71c-415">Click to use the server-level default.</span></span> <span data-ttu-id="2f71c-416">此預設值是由 [備份壓縮預設] 伺服器組態選項所設定。</span><span class="sxs-lookup"><span data-stu-id="2f71c-416">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="2f71c-417">有關如何檢視這個選項目前之設定的詳細資訊，請參閱 [檢視或設定備份壓縮預設伺服器組態選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-417">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
    |<span data-ttu-id="2f71c-418">**壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="2f71c-418">**Compress backup**</span></span>|<span data-ttu-id="2f71c-419">不論目前的伺服器層級預設值為何，按一下即可壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-419">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="2f71c-420">**\*\* 重要 \*\*** 根據預設，壓縮會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="2f71c-420">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="2f71c-421">因此，您可能會想要在資源管理員限制 CPU 使用量的工作階段中建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-421">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the Resource Governor.</span></span> <span data-ttu-id="2f71c-422">如需詳細資訊，請參閱本主題稍後介紹的＜ [使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-422">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
    |<span data-ttu-id="2f71c-423">**不要壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="2f71c-423">**Do not compress backup**</span></span>|<span data-ttu-id="2f71c-424">不論目前的伺服器層級預設值為何，按一下即可建立未壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2f71c-424">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
2.  <span data-ttu-id="2f71c-425">在 [Define Backup Database (Differential) Task (定義備份資料庫 (差異式) 工作)] 頁面上，選取要執行部分備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-425">On the **Define Backup Database (Differential) Task** page, select the database or databases on which to run a partial backup.</span></span> <span data-ttu-id="2f71c-426">如需有關此頁面上可用選項的詳細資訊，請參閱上述步驟 16 中的定義清單。</span><span class="sxs-lookup"><span data-stu-id="2f71c-426">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="2f71c-427">此工作會使用 `BACKUP DATABASE ... WITH DIFFERENTIAL` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-427">This task uses the `BACKUP DATABASE ... WITH DIFFERENTIAL` statement.</span></span> <span data-ttu-id="2f71c-428">如需詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-428">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span>  <span data-ttu-id="2f71c-429">完成後，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-429">When finished, click **Next**.</span></span>  
  
3.  <span data-ttu-id="2f71c-430">在 [Define Backup Database (Transaction Log) Task (定義備份資料庫 (交易記錄) 工作)] 頁面上，選取要執行交易記錄備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f71c-430">On the **Define Backup Database (Transaction Log) Task** page, select the database or databases on which to run a backup for a transaction log.</span></span> <span data-ttu-id="2f71c-431">如需有關此頁面上可用選項的詳細資訊，請參閱上述步驟 16 中的定義清單。</span><span class="sxs-lookup"><span data-stu-id="2f71c-431">See the definition list in step 16, above, for more information about the available options on this page.</span></span> <span data-ttu-id="2f71c-432">此工作會使用 `BACKUP LOG` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-432">This task uses the `BACKUP LOG` statement.</span></span> <span data-ttu-id="2f71c-433">如需詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2f71c-433">For more information, see [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).</span></span> <span data-ttu-id="2f71c-434">完成後，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-434">When finished, click **Next**.</span></span>  
  
#### <a name="define-maintenance-cleanup-tasks"></a><span data-ttu-id="2f71c-435">定義維護清除工作</span><span class="sxs-lookup"><span data-stu-id="2f71c-435">Define Maintenance Cleanup Tasks</span></span>  
  
1.  <span data-ttu-id="2f71c-436">在 **[定義維護清除工作]** 頁面上，指定維護計畫中要刪除的檔案類型，包括維護計畫和資料庫備份檔案所建立的文字報表。</span><span class="sxs-lookup"><span data-stu-id="2f71c-436">On the **Define Maintenance Cleanup Task** page, specify the types of files to delete as part of the maintenance plan, including text reports created by maintenance plans and database backup files.</span></span> <span data-ttu-id="2f71c-437">此工作會使用 `EXEC xp_delete_file` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-437">This task uses the `EXEC xp_delete_file` statement.</span></span> <span data-ttu-id="2f71c-438">完成後，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-438">When finished, click **Next**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2f71c-439">此工作不會自動刪除所指定目錄的子資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-439">This task does not automatically delete files in the subfolders of the specified directory.</span></span> <span data-ttu-id="2f71c-440">這項預防措施可降低利用「維護清除」工作刪除檔案這類惡意攻擊的可能性。</span><span class="sxs-lookup"><span data-stu-id="2f71c-440">This precaution reduces the possibility of a malicious attack that uses the Maintenance Cleanup task to delete files.</span></span> <span data-ttu-id="2f71c-441">如果您要刪除第一層子資料夾中的檔案，必須選取 [包含第一層的子資料夾]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-441">If you want to delete files in first-level subfolders, you must select **Include first-level subfolders**.</span></span>  
  
     <span data-ttu-id="2f71c-442">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-442">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-443">**刪除下列類型的檔案**</span><span class="sxs-lookup"><span data-stu-id="2f71c-443">**Delete files of the following type**</span></span>  
     <span data-ttu-id="2f71c-444">指定要刪除的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="2f71c-444">Specify the type of files to be deleted.</span></span>  
  
     <span data-ttu-id="2f71c-445">**備份檔案**</span><span class="sxs-lookup"><span data-stu-id="2f71c-445">**Backup files**</span></span>  
     <span data-ttu-id="2f71c-446">刪除資料庫備份檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-446">Delete database backup files.</span></span>  
  
     <span data-ttu-id="2f71c-447">**維護計畫文字報表**</span><span class="sxs-lookup"><span data-stu-id="2f71c-447">**Maintenance Plan text reports**</span></span>  
     <span data-ttu-id="2f71c-448">刪除先前執行之維護計畫的文字報表。</span><span class="sxs-lookup"><span data-stu-id="2f71c-448">Delete text reports of previously run maintenance plans.</span></span>  
  
     <span data-ttu-id="2f71c-449">**檔案位置**</span><span class="sxs-lookup"><span data-stu-id="2f71c-449">**File location**</span></span>  
     <span data-ttu-id="2f71c-450">指定要刪除之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="2f71c-450">Specify path to files to be deleted.</span></span>  
  
     <span data-ttu-id="2f71c-451">**刪除特定檔案**</span><span class="sxs-lookup"><span data-stu-id="2f71c-451">**Delete specific file**</span></span>  
     <span data-ttu-id="2f71c-452">刪除 [檔案名稱] 文字方塊中提供的特定檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-452">Delete the specific file provided in the **File name** text box.</span></span>  
  
     <span data-ttu-id="2f71c-453">**根據副檔名搜尋資料夾並刪除檔案**</span><span class="sxs-lookup"><span data-stu-id="2f71c-453">**Search folder and delete files based on an extension**</span></span>  
     <span data-ttu-id="2f71c-454">刪除指定之資料夾中具有指定之副檔名的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-454">Delete all files with the specified extension in the specified folder.</span></span> <span data-ttu-id="2f71c-455">使用此方法即可同時刪除多個檔案，例如 Tuesday 資料夾中副檔名為 .bak 的所有備份檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-455">Use this to delete multiple files at once, such as all backup files in the Tuesday folder with the .bak extension.</span></span>  
  
     <span data-ttu-id="2f71c-456">[資料夾] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-456">**Folder** box</span></span>  
     <span data-ttu-id="2f71c-457">包含要刪除檔案的資料夾路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="2f71c-457">Path and name of the folder containing the files to be deleted.</span></span>  
  
     <span data-ttu-id="2f71c-458">[副檔名] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-458">**File extension** box</span></span>  
     <span data-ttu-id="2f71c-459">提供要刪除的檔案副檔名。</span><span class="sxs-lookup"><span data-stu-id="2f71c-459">Provide the file extension of the files to be deleted.</span></span> <span data-ttu-id="2f71c-460">若要同時刪除多個檔案，像是 Tuesday 資料夾中副檔名為 .bak 的所有備份檔案，請指定 .bak。</span><span class="sxs-lookup"><span data-stu-id="2f71c-460">To delete multiple files at one time, like all backup files with the .bak extension in the Tuesday folder, specify .bak.</span></span>  
  
     <span data-ttu-id="2f71c-461">[包含第一層的子資料夾] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-461">**Include first-level subfolders** check box</span></span>  
     <span data-ttu-id="2f71c-462">從 [資料夾] 所指定資料夾底下的第一層子資料夾中，刪除具有 [副檔名] 中所指定之副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="2f71c-462">Delete files with the extension specified for **File extension** from first-level subfolders under the folder specified in **Folder**.</span></span>  
  
     <span data-ttu-id="2f71c-463">在工作執行階段依據檔案存在時間刪除檔案 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-463">**Delete files based on the age of the file at task run time** check box</span></span>  
     <span data-ttu-id="2f71c-464">在 [刪除早於下列時限的檔案] 方塊中提供數字以及時間單位，以指定您要刪除之檔案的最低存在時間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-464">Specify the minimum age of the files that you want to delete by providing a number, and unit of time in the **Delete files older than the following** box.</span></span>  
  
     <span data-ttu-id="2f71c-465">**刪除早於下列時限的檔案**</span><span class="sxs-lookup"><span data-stu-id="2f71c-465">**Delete files older than the following**</span></span>  
     <span data-ttu-id="2f71c-466">提供數字以及時間單位 ([小時]、[日]、[週]、[月] 或 [年])，指定要刪除之檔案的最低存在時間。</span><span class="sxs-lookup"><span data-stu-id="2f71c-466">Specify the minimum age of the files that you want to delete by providing a number, and unit of time (**Hour**, **Day**, **Week**, **Month**, or **Year**).</span></span> <span data-ttu-id="2f71c-467">存在時間超過指定時間的檔案會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="2f71c-467">Files older than the time frame specified will be deleted.</span></span>  
  
#### <a name="select-report-options"></a><span data-ttu-id="2f71c-468">選取報表選項</span><span class="sxs-lookup"><span data-stu-id="2f71c-468">Select Report Options</span></span>  
  
1.  <span data-ttu-id="2f71c-469">在 **[選取報表選項]** 頁面上，選取儲存或散發維護計畫動作報表的選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-469">On the **Select Report Options** page, select options for saving or distributing a report of the maintenance plan actions.</span></span> <span data-ttu-id="2f71c-470">此工作會使用 `EXEC sp_notify_operator` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f71c-470">This task uses the `EXEC sp_notify_operator` statement.</span></span> <span data-ttu-id="2f71c-471">如需詳細資訊，請參閱 [sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql) 完成時，請按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="2f71c-471">For more information, see [sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql).When finished, click **Next**.</span></span>  
  
     <span data-ttu-id="2f71c-472">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="2f71c-472">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="2f71c-473">[將報表寫入文字檔] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-473">**Write a report to a text file** check box</span></span>  
     <span data-ttu-id="2f71c-474">在檔案中儲存報表。</span><span class="sxs-lookup"><span data-stu-id="2f71c-474">Save the report in a file.</span></span>  
  
     <span data-ttu-id="2f71c-475">[資料夾位置] 方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-475">**Folder location** box</span></span>  
     <span data-ttu-id="2f71c-476">指定包含報表的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="2f71c-476">Specify the location of the file that will contain the report.</span></span>  
  
     <span data-ttu-id="2f71c-477">[以電子郵件傳送報表] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f71c-477">**E-mail report** check box</span></span>  
     <span data-ttu-id="2f71c-478">工作失敗時傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="2f71c-478">Send an e-mail when a task fails.</span></span> <span data-ttu-id="2f71c-479">若要使用這個工作，您必須先啟用 Database Mail，並正確設定 MSDB 作為郵件主機資料庫，同時擁有具有效電子郵件地址的 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式操作員。</span><span class="sxs-lookup"><span data-stu-id="2f71c-479">To use this task you must have Database Mail enabled and correctly configured with MSDB as a Mail Host Database, and have a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator with a valid e-mail address.</span></span>  
  
     <span data-ttu-id="2f71c-480">**代理程式操作員**</span><span class="sxs-lookup"><span data-stu-id="2f71c-480">**Agent operator**</span></span>  
     <span data-ttu-id="2f71c-481">指定電子郵件的收件者。</span><span class="sxs-lookup"><span data-stu-id="2f71c-481">Specify the recipient of the e-mail.</span></span>  
  
     <span data-ttu-id="2f71c-482">**郵件設定檔**</span><span class="sxs-lookup"><span data-stu-id="2f71c-482">**Mail profile**</span></span>  
     <span data-ttu-id="2f71c-483">指定定義電子郵件寄件者的設定檔。</span><span class="sxs-lookup"><span data-stu-id="2f71c-483">Specify the profile that defines the sender of the e-mail.</span></span>  
  
#### <a name="complete-the-wizard"></a><span data-ttu-id="2f71c-484">完成精靈</span><span class="sxs-lookup"><span data-stu-id="2f71c-484">Complete the Wizard</span></span>  
  
1.  <span data-ttu-id="2f71c-485">在 **[完成精靈]** 頁面上，確認之前所有頁面上的選擇，然後按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-485">On the **Complete the Wizard** page, verify the choices made on the previous pages, and click **Finish**.</span></span>  
  
2.  <span data-ttu-id="2f71c-486">在 **[維護精靈進度]** 頁面上，監視有關維護計畫精靈之動作的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="2f71c-486">On the **Maintenance Wizard Progress** page, monitor status information about the actions of the Maintenance Plan Wizard.</span></span> <span data-ttu-id="2f71c-487">根據您在精靈中選取的選項，[進度] 頁面可能會包含一個或多個動作。</span><span class="sxs-lookup"><span data-stu-id="2f71c-487">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="2f71c-488">頂端的方塊會顯示精靈的整體狀態以及精靈已接收的狀態、錯誤和警告訊息數。</span><span class="sxs-lookup"><span data-stu-id="2f71c-488">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="2f71c-489">**[維護精靈進度]** 頁面上提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="2f71c-489">The following options are available on the **Maintenance Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="2f71c-490">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="2f71c-490">**Details**</span></span>  
     <span data-ttu-id="2f71c-491">提供從精靈所採取的動作傳回的動作、狀態和任何訊息。</span><span class="sxs-lookup"><span data-stu-id="2f71c-491">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="2f71c-492">**動作**</span><span class="sxs-lookup"><span data-stu-id="2f71c-492">**Action**</span></span>  
     <span data-ttu-id="2f71c-493">指定每個動作的類型和名稱。</span><span class="sxs-lookup"><span data-stu-id="2f71c-493">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="2f71c-494">**狀態**</span><span class="sxs-lookup"><span data-stu-id="2f71c-494">**Status**</span></span>  
     <span data-ttu-id="2f71c-495">指出整個精靈動作傳回 [成功] 或 [失敗] 的值。</span><span class="sxs-lookup"><span data-stu-id="2f71c-495">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="2f71c-496">**訊息**</span><span class="sxs-lookup"><span data-stu-id="2f71c-496">**Message**</span></span>  
     <span data-ttu-id="2f71c-497">提供從程序所傳回的任何錯誤或警告訊息。</span><span class="sxs-lookup"><span data-stu-id="2f71c-497">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="2f71c-498">**Report**</span><span class="sxs-lookup"><span data-stu-id="2f71c-498">**Report**</span></span>  
     <span data-ttu-id="2f71c-499">建立包含 [建立分割區精靈] 結果的報表。</span><span class="sxs-lookup"><span data-stu-id="2f71c-499">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="2f71c-500">選項為 **[檢視報表]** 、 **[將報表儲存到檔案]** 、 **[複製報表到剪貼簿]** 和 **[以電子郵件傳送報表]** 。</span><span class="sxs-lookup"><span data-stu-id="2f71c-500">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="2f71c-501">**檢視報表**</span><span class="sxs-lookup"><span data-stu-id="2f71c-501">**View Report**</span></span>  
     <span data-ttu-id="2f71c-502">開啟 [檢視報表] 對話方塊，其中包含 [建立分割區精靈] 進度的文字報表。</span><span class="sxs-lookup"><span data-stu-id="2f71c-502">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="2f71c-503">**將報表儲存到檔案**</span><span class="sxs-lookup"><span data-stu-id="2f71c-503">**Save Report to File**</span></span>  
     <span data-ttu-id="2f71c-504">開啟 [另存報表] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2f71c-504">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="2f71c-505">**複製報表到剪貼簿**</span><span class="sxs-lookup"><span data-stu-id="2f71c-505">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="2f71c-506">將精靈進度報表的結果複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="2f71c-506">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="2f71c-507">**[以電子郵件傳送報表]**</span><span class="sxs-lookup"><span data-stu-id="2f71c-507">**Send Report as Email**</span></span>  
     <span data-ttu-id="2f71c-508">將精靈進度報表的結果複製到電子郵件。</span><span class="sxs-lookup"><span data-stu-id="2f71c-508">Copies the results of the wizard's progress report into an email message.</span></span>  
  
  
