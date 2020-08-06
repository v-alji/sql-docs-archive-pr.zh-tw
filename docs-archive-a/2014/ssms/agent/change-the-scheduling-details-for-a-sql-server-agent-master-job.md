---
title: 變更 SQL Server Agent 主要作業的排程詳細資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: f5414451-4d8e-464b-bd9e-f2b70c6899b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85546bc93e6626bfcc85a28f06a4c2fe24fe9fd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606586"
---
# <a name="change-the-scheduling-details-for-a-sql-server-agent-master-job"></a><span data-ttu-id="dbc11-102">Change the Scheduling Details for a SQL Server Agent Master Job</span><span class="sxs-lookup"><span data-stu-id="dbc11-102">Change the Scheduling Details for a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="dbc11-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中變更作業定義的排程詳細資料。</span><span class="sxs-lookup"><span data-stu-id="dbc11-103">This topic describes how to change the scheduling details for a job definition in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="dbc11-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="dbc11-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="dbc11-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="dbc11-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="dbc11-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="dbc11-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="dbc11-107">安全性</span><span class="sxs-lookup"><span data-stu-id="dbc11-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="dbc11-108">**若要使用下列項目來變更作業定義的排程詳細資料：**</span><span class="sxs-lookup"><span data-stu-id="dbc11-108">**To change the scheduling details for a job definition, using:**</span></span>  
  
     [<span data-ttu-id="dbc11-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dbc11-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="dbc11-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dbc11-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="dbc11-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="dbc11-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="dbc11-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="dbc11-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="dbc11-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要作業無法同時存在於本機和遠端伺服器內。</span><span class="sxs-lookup"><span data-stu-id="dbc11-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dbc11-114">Security</span><span class="sxs-lookup"><span data-stu-id="dbc11-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dbc11-115">權限</span><span class="sxs-lookup"><span data-stu-id="dbc11-115">Permissions</span></span>  
 <span data-ttu-id="dbc11-116">除非您是系統管理員 ( **sysadmin** ) 固定伺服器角色的成員，否則您只能修改您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="dbc11-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="dbc11-117">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dbc11-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="dbc11-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="dbc11-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="dbc11-119">若要變更作業定義的排程詳細資料</span><span class="sxs-lookup"><span data-stu-id="dbc11-119">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="dbc11-120">在 **[物件總管]** 中，按一下加號，展開包含您想要編輯其排程之作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="dbc11-120">In **Object Explorer,** click the plus sign to expand the server that contains the job whose schedule you want to edit.</span></span>  
  
2.  <span data-ttu-id="dbc11-121">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="dbc11-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="dbc11-122">按一下加號展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dbc11-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="dbc11-123">以滑鼠右鍵按一下您想要編輯其排程的作業，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dbc11-123">Right-click the job whose schedule you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="dbc11-124">在 [**作業屬性-**_job_name_ ] 對話方塊的 [**選取頁面**] 底下，**選取 [** 排程]。</span><span class="sxs-lookup"><span data-stu-id="dbc11-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Schedules**.</span></span> <span data-ttu-id="dbc11-125">如需有關此頁面上可用選項的詳細資訊，請參閱[作業屬性：新增作業 &#40;排程頁面&#41;](job-properties-new-job-schedules-page.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc11-125">For more information on the available options on this page, see [Job Properties: New Job &#40;Schedules Page&#41;](job-properties-new-job-schedules-page.md).</span></span>  
  
6.  <span data-ttu-id="dbc11-126">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="dbc11-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dbc11-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="dbc11-127">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-scheduling-details-for-a-job-definition"></a><span data-ttu-id="dbc11-128">若要變更作業定義的排程詳細資料</span><span class="sxs-lookup"><span data-stu-id="dbc11-128">To change the scheduling details for a job definition</span></span>  
  
1.  <span data-ttu-id="dbc11-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbc11-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="dbc11-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="dbc11-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="dbc11-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="dbc11-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled status of the NightlyJobs schedule to 0   
    -- and sets the owner to terrid.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_schedule  
        @name = 'NightlyJobs',  
        @enabled = 0,  
        @owner_login_name = 'terrid' ;  
    GO  
    ```  
  
 <span data-ttu-id="dbc11-132">如需詳細資訊，請參閱[sp_update_schedule &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dbc11-132">For more information, see [sp_update_schedule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-schedule-transact-sql).</span></span>  
  
  
