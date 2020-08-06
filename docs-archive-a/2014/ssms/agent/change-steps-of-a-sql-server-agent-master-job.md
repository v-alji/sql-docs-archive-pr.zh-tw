---
title: 變更 SQL Server Agent 主要作業的步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 8f1a0ee6-49ff-4080-94ca-d661daeff2a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a9defc17b5b39ab8a322b6da29960eb9968c2e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606588"
---
# <a name="change-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="21c8b-102">變更 SQL Server Agent Master Job 的步驟</span><span class="sxs-lookup"><span data-stu-id="21c8b-102">Change Steps of a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="21c8b-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中變更 SQL Server Agent 主要作業的步驟。</span><span class="sxs-lookup"><span data-stu-id="21c8b-103">This topic describes how to make changes to the steps of a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="21c8b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="21c8b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="21c8b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="21c8b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="21c8b-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="21c8b-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="21c8b-107">安全性</span><span class="sxs-lookup"><span data-stu-id="21c8b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="21c8b-108">**若要使用下列項目來變更 SQL Server Agent 主要作業的步驟：**</span><span class="sxs-lookup"><span data-stu-id="21c8b-108">**To make changes to the steps of a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="21c8b-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="21c8b-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="21c8b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21c8b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="21c8b-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="21c8b-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="21c8b-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="21c8b-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="21c8b-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要作業無法同時存在於本機和遠端伺服器內。</span><span class="sxs-lookup"><span data-stu-id="21c8b-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="21c8b-114">Security</span><span class="sxs-lookup"><span data-stu-id="21c8b-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="21c8b-115">權限</span><span class="sxs-lookup"><span data-stu-id="21c8b-115">Permissions</span></span>  
 <span data-ttu-id="21c8b-116">除非您是系統管理員 ( **sysadmin** ) 固定伺服器角色的成員，否則您只能修改您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="21c8b-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="21c8b-117">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="21c8b-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="21c8b-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="21c8b-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="21c8b-119">若要變更 SQL Server Agent 主要作業的步驟</span><span class="sxs-lookup"><span data-stu-id="21c8b-119">To make changes to the steps of a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="21c8b-120">在 **[物件總管]** 中，按一下加號，展開包含您想要修改步驟之作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="21c8b-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to modify steps.</span></span>  
  
2.  <span data-ttu-id="21c8b-121">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="21c8b-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="21c8b-122">按一下加號展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="21c8b-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="21c8b-123">以滑鼠右鍵按一下您想要修改步驟的作業，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="21c8b-123">Right-click the job where you want to modify steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="21c8b-124">在 [**作業屬性-**_job_name_ ] 對話方塊的 [**選取頁面**] 底下，選取 [**步驟**]。</span><span class="sxs-lookup"><span data-stu-id="21c8b-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="21c8b-125">按一下 [**編輯**]，開啟 [**作業步驟屬性-**_job_step_name_ ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="21c8b-125">Click **Edit** to open the **Job Step Properties -**_job_step_name_ dialog box.</span></span> <span data-ttu-id="21c8b-126">如需此對話方塊中可用選項的詳細資訊，請參閱[作業步驟屬性：新增作業步驟 &#40;一般頁面&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)和[作業步驟屬性：新增作業步驟 &#40;先進頁面&#41;](job-step-properties-new-job-step-advanced-page.md)。</span><span class="sxs-lookup"><span data-stu-id="21c8b-126">For more information on the available options in this dialog box, see [Job Step Properties: New Job Step &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md) and [Job Step Properties: New Job Step &#40;Advanced Page&#41;](job-step-properties-new-job-step-advanced-page.md).</span></span>  
  
7.  <span data-ttu-id="21c8b-127">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="21c8b-127">When finished, click **OK**.</span></span>  
  
8.  <span data-ttu-id="21c8b-128">在 [**作業屬性-**_job_name_ ] 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="21c8b-128">In the **Job Properties -**_job_name_ dialog box, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="21c8b-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="21c8b-129">Using Transact-SQL</span></span>  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a><span data-ttu-id="21c8b-130">若要變更 SQL Server Agent 主要作業的步驟</span><span class="sxs-lookup"><span data-stu-id="21c8b-130">To make changes to the steps of a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="21c8b-131">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="21c8b-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="21c8b-132">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="21c8b-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="21c8b-133">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="21c8b-133">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the number of retry attempts for the first step of the Weekly Sales Data Backup job.   
    -- After running this example, the number of retry attempts is 10   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1,  
        @retry_attempts = 10 ;  
    GO  
    ```  
  
 <span data-ttu-id="21c8b-134">如需詳細資訊，請參閱[sp_update_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="21c8b-134">For more information, see [sp_update_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql).</span></span>  
  
  
