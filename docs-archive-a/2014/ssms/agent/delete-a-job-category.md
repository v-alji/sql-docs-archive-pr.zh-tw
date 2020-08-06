---
title: 刪除作業類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
ms.openlocfilehash: e96dd0461f3dace138b7822cdbaaa2fa242e2cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687410"
---
# <a name="delete-a-job-category"></a><span data-ttu-id="5fade-102">刪除作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="5fade-102">Delete a Job Category</span></span>
  <span data-ttu-id="5fade-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理物件，在中刪除 Agent 作業類別目錄 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5fade-103">This topic describes how to delete a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="5fade-104">作業類別目錄可幫助您組織作業，以便於篩選與分組。</span><span class="sxs-lookup"><span data-stu-id="5fade-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="5fade-105">例如，您可以將所有的資料庫備份作業整理在資料庫維護類別中。</span><span class="sxs-lookup"><span data-stu-id="5fade-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span>  

##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5fade-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="5fade-106">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5fade-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="5fade-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="5fade-108">當您刪除使用者定義的作業類別目錄時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會提示您將已指定給該類別目錄的作業重新指定給其他作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="5fade-108">When you delete a user-defined job category, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent prompts you to reassign the jobs that are assigned to it to another job category.</span></span> <span data-ttu-id="5fade-109">您只能刪除使用者定義的作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="5fade-109">You can only delete user-defined job categories.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5fade-110">Security</span><span class="sxs-lookup"><span data-stu-id="5fade-110">Security</span></span>  
 <span data-ttu-id="5fade-111">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="5fade-111">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="5fade-112">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5fade-112">Using SQL Server Management Studio</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="5fade-113">若要刪除作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="5fade-113">To delete a job category</span></span>  
  
1.  <span data-ttu-id="5fade-114">在 **[物件總管]** 中，按一下加號展開要刪除作業類別目錄所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="5fade-114">In **Object Explorer**, click the plus sign to expand the server where you want to delete a job category.</span></span>  
  
2.  <span data-ttu-id="5fade-115">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="5fade-115">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="5fade-116">以滑鼠右鍵按一下 [作業]\*\*\*\* 資料夾，然後選取 [管理作業類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5fade-116">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="5fade-117">在 [管理作業類別目錄 <伺服器名稱>]\*\*\*\*__ 對話方塊中，選取所要刪除的作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="5fade-117">In the **Manage Job Categories**_server_name_ dialog box, select the job category to delete.</span></span>  
  
5.  <span data-ttu-id="5fade-118">按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="5fade-118">Click **Delete**.</span></span>  
  
6.  <span data-ttu-id="5fade-119">在 **[作業類別目錄]** 對話方塊中，按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="5fade-119">In the **Job Categories** dialog box, click **Yes**.</span></span>  
  
7.  <span data-ttu-id="5fade-120">關閉 [管理作業類別目錄 <伺服器名稱>]\*\*\*\*__ 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5fade-120">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="5fade-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5fade-121">Using Transact-SQL</span></span>  
  
### <a name="to-delete-a-job-category"></a><span data-ttu-id="5fade-122">若要刪除作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="5fade-122">To delete a job category</span></span>  
  
1.  <span data-ttu-id="5fade-123">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5fade-123">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5fade-124">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5fade-124">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5fade-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5fade-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 <span data-ttu-id="5fade-126">如需詳細資訊，請參閱[sp_delete_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5fade-126">For more information, see [sp_delete_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql).</span></span>  

  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="5fade-127">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="5fade-127">Using SQL Server Management Objects</span></span>  

### <a name="to-delete-a-job-category"></a><span data-ttu-id="5fade-128">若要刪除作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="5fade-128">To delete a job category</span></span>
  
 <span data-ttu-id="5fade-129">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell 呼叫 `JobCategory` 類別。</span><span class="sxs-lookup"><span data-stu-id="5fade-129">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
