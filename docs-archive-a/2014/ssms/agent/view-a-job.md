---
title: 檢視作業 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], viewing
- viewing jobs
- SQL Server Agent jobs, viewing
- displaying jobs
ms.assetid: d2241a3f-dbcf-433c-b7bc-f96bdf0eac8c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 26406aaf2ba0ac4809eb7ac2c84799469d0468d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607222"
---
# <a name="view-a-job"></a><span data-ttu-id="6abbf-102">檢視作業</span><span class="sxs-lookup"><span data-stu-id="6abbf-102">View a Job</span></span>
  <span data-ttu-id="6abbf-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用或，在中查看 Agent 作業 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6abbf-103">This topic describes how to view [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6abbf-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6abbf-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6abbf-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6abbf-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6abbf-106">安全性</span><span class="sxs-lookup"><span data-stu-id="6abbf-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6abbf-107">**若要使用下列項目檢視作業：**</span><span class="sxs-lookup"><span data-stu-id="6abbf-107">**To view a job, using:**</span></span>  
  
     [<span data-ttu-id="6abbf-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6abbf-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="6abbf-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6abbf-109">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="6abbf-110">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="6abbf-110">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6abbf-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="6abbf-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6abbf-112">Security</span><span class="sxs-lookup"><span data-stu-id="6abbf-112">Security</span></span>  
 <span data-ttu-id="6abbf-113">若您不是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，就只能檢視您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="6abbf-113">You can only view jobs that you own, unless you are a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="6abbf-114">此角色的成員可以檢視所有作業。</span><span class="sxs-lookup"><span data-stu-id="6abbf-114">Members of this role can view all jobs.</span></span> <span data-ttu-id="6abbf-115">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="6abbf-115">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="6abbf-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6abbf-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="6abbf-117">若要檢視作業</span><span class="sxs-lookup"><span data-stu-id="6abbf-117">To view a job</span></span>  
  
1.  <span data-ttu-id="6abbf-118">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="6abbf-118">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="6abbf-119">展開 **[SQL Server Agent]**，然後展開 **[作業]**。</span><span class="sxs-lookup"><span data-stu-id="6abbf-119">Expand **SQL Server Agent**, and then expand **Jobs**.</span></span>  
  
3.  <span data-ttu-id="6abbf-120">以滑鼠右鍵按一下作業，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="6abbf-120">Right-click a job, and then click **Properties**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="6abbf-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6abbf-121">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-job"></a><span data-ttu-id="6abbf-122">若要檢視作業</span><span class="sxs-lookup"><span data-stu-id="6abbf-122">To view a job</span></span>  
  
1.  <span data-ttu-id="6abbf-123">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6abbf-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6abbf-124">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6abbf-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6abbf-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="6abbf-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- lists all aspects of the information for the job NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_job  
        @job_name = N'NightlyBackups',  
        @job_aspect = N'ALL' ;  
    GO  
    ```  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="6abbf-126">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="6abbf-126">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="6abbf-127">**若要檢視作業**</span><span class="sxs-lookup"><span data-stu-id="6abbf-127">**To view a job**</span></span>  
  
 <span data-ttu-id="6abbf-128">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `Job` 類別。</span><span class="sxs-lookup"><span data-stu-id="6abbf-128">Use the `Job` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="6abbf-129">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6abbf-129">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
