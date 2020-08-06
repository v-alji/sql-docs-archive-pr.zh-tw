---
title: 刪除一個或多個作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, deleting
- dropping jobs
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 67dcdad0-57b2-431c-b77f-4ffc926af93d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 436625f9ad629a6b0e574aa046059f4e7e9c2bf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585758"
---
# <a name="delete-one-or-more-jobs"></a><span data-ttu-id="17c36-102">刪除一個或多個作業</span><span class="sxs-lookup"><span data-stu-id="17c36-102">Delete One or More Jobs</span></span>
  <span data-ttu-id="17c36-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、或 SQL Server 管理物件，在中刪除 Agent 作業 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="17c36-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="17c36-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="17c36-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="17c36-105">Security</span><span class="sxs-lookup"><span data-stu-id="17c36-105">Security</span></span>  
 <span data-ttu-id="17c36-106">除非您是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，否則您只能刪除您擁有的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="17c36-106">Unless you are a member of the **sysadmin** fixed server role, you can only delete jobs that you own.</span></span>  
  
 
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="17c36-107">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="17c36-107">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="17c36-108">若要刪除作業</span><span class="sxs-lookup"><span data-stu-id="17c36-108">To delete a job</span></span>  
  
1.  <span data-ttu-id="17c36-109">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="17c36-109">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="17c36-110">展開 **[SQL Server Agent]**，展開 **[作業]**，以滑鼠右鍵按一下要刪除的作業，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="17c36-110">Expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="17c36-111">在 **[刪除物件]** 對話方塊中，確認已選取您要刪除的作業。</span><span class="sxs-lookup"><span data-stu-id="17c36-111">In the **Delete Object** dialog box, confirm that the job you intend to delete is selected.</span></span>  
  
4.  <span data-ttu-id="17c36-112">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="17c36-112">Click **OK**.</span></span>  
  
#### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="17c36-113">若要刪除多個作業</span><span class="sxs-lookup"><span data-stu-id="17c36-113">To delete multiple jobs</span></span>  
  
1.  <span data-ttu-id="17c36-114">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="17c36-114">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="17c36-115">展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="17c36-115">Expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="17c36-116">以滑鼠右鍵按一下 **[作業活動監視器]**，然後按一下 **[檢視作業活動]**。</span><span class="sxs-lookup"><span data-stu-id="17c36-116">Right-click **Job Activity Monitor**, and click **View Job Activity**.</span></span>  
  
4.  <span data-ttu-id="17c36-117">在「作業活動監視器」中，選取要刪除的作業，以滑鼠右鍵按一下選取範圍，然後選擇 **[刪除作業]**。</span><span class="sxs-lookup"><span data-stu-id="17c36-117">In the Job Activity Monitor, select the jobs you want to delete, right-click your selection, and choose **Delete jobs**.</span></span>  
  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="17c36-118">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="17c36-118">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-job"></a><span data-ttu-id="17c36-119">若要刪除作業</span><span class="sxs-lookup"><span data-stu-id="17c36-119">To delete a job</span></span>  
  
1.  <span data-ttu-id="17c36-120">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="17c36-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="17c36-121">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="17c36-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="17c36-122">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="17c36-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    USE msdb ;  
    GO  
  
    EXEC sp_delete_job  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
 <span data-ttu-id="17c36-123">如需詳細資訊，請參閱[sp_delete_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="17c36-123">For more information, see [sp_delete_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-job-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="17c36-124">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="17c36-124">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-multiple-jobs"></a><span data-ttu-id="17c36-125">若要刪除多個作業</span><span class="sxs-lookup"><span data-stu-id="17c36-125">To delete multiple jobs</span></span>
  
 <span data-ttu-id="17c36-126">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobCollection` 類別。</span><span class="sxs-lookup"><span data-stu-id="17c36-126">Use the `JobCollection` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="17c36-127">如需詳細資訊，請參閱 [SQL Server 管理物件 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。</span><span class="sxs-lookup"><span data-stu-id="17c36-127">For more information, see [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).</span></span>  
