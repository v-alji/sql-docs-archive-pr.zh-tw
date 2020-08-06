---
title: 停用或啟用作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- stopping jobs
- disabling jobs
- SQL Server Agent jobs, disabling
- jobs [SQL Server Agent], disabling
ms.assetid: 5041261f-0c32-4d4a-8bee-59a6c16200dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42fe7cbeed1e2ff3f93b1afef52b165a7d660ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584967"
---
# <a name="disable-or-enable-a-job"></a><span data-ttu-id="7d2c2-102">停用或啟用作業</span><span class="sxs-lookup"><span data-stu-id="7d2c2-102">Disable or Enable a Job</span></span>
  <span data-ttu-id="7d2c2-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中停用 [!INCLUDE[tsql](../../includes/tsql-md.md)]Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-103">This topic describes how to disable a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="7d2c2-104">當您停用作業時，該項作業並未刪除，而且必要時可以重新啟用。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-104">When you disable a job, it is not deleted and can be enabled again when necessary.</span></span>  
  
 <span data-ttu-id="7d2c2-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="7d2c2-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="7d2c2-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="7d2c2-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="7d2c2-107">安全性</span><span class="sxs-lookup"><span data-stu-id="7d2c2-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="7d2c2-108">**若要使用下列項目停用或啟用作業：**</span><span class="sxs-lookup"><span data-stu-id="7d2c2-108">**To disable or enable a job, using:**</span></span>  
  
     [<span data-ttu-id="7d2c2-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7d2c2-109">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="7d2c2-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7d2c2-110">Transact-SQL</span></span>](#TSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="7d2c2-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="7d2c2-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7d2c2-112">Security</span><span class="sxs-lookup"><span data-stu-id="7d2c2-112">Security</span></span>  
 <span data-ttu-id="7d2c2-113">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-113">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="7d2c2-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="7d2c2-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="7d2c2-115">若要停用或啟用作業</span><span class="sxs-lookup"><span data-stu-id="7d2c2-115">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="7d2c2-116">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-116">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="7d2c2-117">展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-117">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="7d2c2-118">展開 [作業]\*\*\*\*，然後以滑鼠右鍵按一下要停用或啟用的作業。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-118">Expand **Jobs**, and then right-click the job that you want to disable or enable.</span></span>  
  
4.  <span data-ttu-id="7d2c2-119">若要停用作業，請按一下 **[停用]**。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-119">To disable a job, click **Disable**.</span></span> <span data-ttu-id="7d2c2-120">若要啟用作業，請按一下 **[啟用]**。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-120">To enable a job, click **Enable**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="7d2c2-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="7d2c2-121">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-enable-a-job"></a><span data-ttu-id="7d2c2-122">若要停用或啟用作業</span><span class="sxs-lookup"><span data-stu-id="7d2c2-122">To disable or enable a job</span></span>  
  
1.  <span data-ttu-id="7d2c2-123">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7d2c2-124">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7d2c2-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the name, description, and enables status of the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @new_name = N'NightlyBackups -- Disabled',  
        @description = N'Nightly backups disabled during server migration.',  
        @enabled = 1 ;  
    GO  
    ```  
  
 <span data-ttu-id="7d2c2-126">如需詳細資訊，請參閱[sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="7d2c2-126">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
