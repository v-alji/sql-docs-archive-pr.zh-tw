---
title: 從 SQL Server Agent 主要作業中移除步驟 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 871e6162-1221-464d-8f7f-7e454dcd9edb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5996971225ee0b300b307c5af24dec464dbfd43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606556"
---
# <a name="remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="cb1ee-102">從 SQL Server Agent 主要作業中移除步驟</span><span class="sxs-lookup"><span data-stu-id="cb1ee-102">Remove Steps from a SQL Server Agent Master Job</span></span>
  <span data-ttu-id="cb1ee-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中移除 SQL Server Agent 主要作業的步驟。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-103">This topic describes how to remove steps from a SQL Server Agent master job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cb1ee-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="cb1ee-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cb1ee-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="cb1ee-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cb1ee-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="cb1ee-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cb1ee-107">安全性</span><span class="sxs-lookup"><span data-stu-id="cb1ee-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cb1ee-108">**若要使用下列項目，從 SQL Server Agent 主要作業中移除步驟：**</span><span class="sxs-lookup"><span data-stu-id="cb1ee-108">**To remove steps from a SQL Server Agent master job, using:**</span></span>  
  
     [<span data-ttu-id="cb1ee-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cb1ee-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cb1ee-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cb1ee-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cb1ee-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="cb1ee-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cb1ee-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="cb1ee-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="cb1ee-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 主要作業無法同時存在於本機和遠端伺服器內。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-113">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent master job cannot be targeted at both local and remote servers.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cb1ee-114">Security</span><span class="sxs-lookup"><span data-stu-id="cb1ee-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cb1ee-115">權限</span><span class="sxs-lookup"><span data-stu-id="cb1ee-115">Permissions</span></span>  
 <span data-ttu-id="cb1ee-116">除非您是系統管理員 ( **sysadmin** ) 固定伺服器角色的成員，否則您只能修改您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-116">Unless you are a member of the **sysadmin** fixed server role, you can only modify jobs that you own.</span></span> <span data-ttu-id="cb1ee-117">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-117">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cb1ee-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cb1ee-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="cb1ee-119">若要從 SQL Server Agent 主要作業中移除步驟</span><span class="sxs-lookup"><span data-stu-id="cb1ee-119">To remove steps from a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="cb1ee-120">在 **[物件總管]** 中，按一下加號，展開包含您想要刪除步驟之作業的伺服器。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-120">In **Object Explorer,** click the plus sign to expand the server that contains the job where you want to delete steps.</span></span>  
  
2.  <span data-ttu-id="cb1ee-121">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-121">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="cb1ee-122">按一下加號展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-122">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="cb1ee-123">以滑鼠右鍵按一下您想要刪除步驟的作業，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-123">Right-click the job where you want to delete steps and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="cb1ee-124">在 [**作業屬性-**_job_name_ ] 對話方塊的 [**選取頁面**] 底下，選取 [**步驟**]。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-124">In the **Job Properties -**_job_name_ dialog box, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="cb1ee-125">在 **[作業步驟清單]** 底下，選取您想要刪除的作業步驟，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-125">Under **Job step list**, select the job step you want to delete and click **Delete**.</span></span>  
  
7.  <span data-ttu-id="cb1ee-126">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cb1ee-127">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cb1ee-127">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-steps-from-a-sql-server-agent-master-job"></a><span data-ttu-id="cb1ee-128">若要從 SQL Server Agent 主要作業中移除步驟</span><span class="sxs-lookup"><span data-stu-id="cb1ee-128">To remove steps from a SQL Server Agent master job</span></span>  
  
1.  <span data-ttu-id="cb1ee-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cb1ee-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cb1ee-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- removes job step 1 from the job Weekly Sales Data Backup   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="cb1ee-132">如需詳細資訊，請參閱[sp_delete_jobstep &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cb1ee-132">For more information, see [sp_delete_jobstep &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-jobstep-transact-sql).</span></span>  
  
  
