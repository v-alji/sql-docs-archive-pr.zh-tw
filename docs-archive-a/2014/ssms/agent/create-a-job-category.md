---
title: 建立作業類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f6daeeca6253861e8a9dcbb72faa2bd55eb2761
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704677"
---
# <a name="create-a-job-category"></a><span data-ttu-id="b4264-102">建立作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="b4264-102">Create a Job Category</span></span>
  <span data-ttu-id="b4264-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 管理物件，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="b4264-103">This topic describes how to create a job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b4264-104">Agent 提供了內建作業類別目錄，您可將作業指派給這些內建作業類別目錄，或可建立作業類別目錄並指派其作業。</span><span class="sxs-lookup"><span data-stu-id="b4264-104">Agent provides built-in job categories that you can assign jobs to, or you can create a job category and assign jobs to it.</span></span> <span data-ttu-id="b4264-105">作業類別目錄可幫助您組織作業，以便於篩選與分組。</span><span class="sxs-lookup"><span data-stu-id="b4264-105">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="b4264-106">例如，您可以將所有的資料庫備份作業整理在資料庫維護類別中。</span><span class="sxs-lookup"><span data-stu-id="b4264-106">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="b4264-107">您也可以建立您自己的作業類別。</span><span class="sxs-lookup"><span data-stu-id="b4264-107">You can also create your own job categories.</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b4264-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="b4264-108">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b4264-109">限制事項</span><span class="sxs-lookup"><span data-stu-id="b4264-109">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b4264-110">多伺服器類別只存在於主要伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b4264-110">Multiserver categories exist only on a master server.</span></span> <span data-ttu-id="b4264-111">主要伺服器上只有一個預設作業類別目錄：**未分類 (多伺服器)**。</span><span class="sxs-lookup"><span data-stu-id="b4264-111">There is only one default job category available on a master server: [**Uncategorized (Multi-Server)**].</span></span> <span data-ttu-id="b4264-112">下載多伺服器作業之後，其類別目錄會變更為目標伺服器上的 **[來自 MSX 的作業]** 。</span><span class="sxs-lookup"><span data-stu-id="b4264-112">When a multiserver job is downloaded, its category is changed to **Jobs From MSX** at the target server.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b4264-113">Security</span><span class="sxs-lookup"><span data-stu-id="b4264-113">Security</span></span>  
 <span data-ttu-id="b4264-114">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b4264-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="b4264-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b4264-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="b4264-116">若要建立作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="b4264-116">To create a job category</span></span>  
  
1.  <span data-ttu-id="b4264-117">在 **[物件總管]** 中，按一下加號展開要建立作業類別目錄所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b4264-117">In **Object Explorer**, click the plus sign to expand the server where you want to create a job category.</span></span>  
  
2.  <span data-ttu-id="b4264-118">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="b4264-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="b4264-119">以滑鼠右鍵按一下 [作業]\*\*\*\* 資料夾，然後選取 [管理作業類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b4264-119">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="b4264-120">在 [**管理作業類別目錄**_server_name_ ] 對話方塊中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="b4264-120">In the **Manage Job Categories**_server_name_ dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="b4264-121">在新對話方塊的 **[名稱]** 方塊中，輸入新作業類別目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4264-121">In the new dialog box, in the **Name** box, enter a name for the new job category.</span></span>  
  
6.  <span data-ttu-id="b4264-122">選取 **[顯示所有作業]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b4264-122">Select the **Show all jobs** check box.</span></span> <span data-ttu-id="b4264-123">選取對應於作業的方塊，為新的類別目錄選取一個或多個作業。</span><span class="sxs-lookup"><span data-stu-id="b4264-123">Select one or more jobs for the new category by checking the boxes corresponding to the jobs.</span></span>  
  
7.  <span data-ttu-id="b4264-124">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b4264-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="b4264-125">在 [**管理作業類別目錄**_server_name_ ] 對話方塊中 **，按一下 [** 重新整理] 以確定新的作業類別目錄為作用中。</span><span class="sxs-lookup"><span data-stu-id="b4264-125">In the **Manage Job Categories**_server_name_ dialog box, click **Refresh** to ensure that the new job category is active.</span></span> <span data-ttu-id="b4264-126">如果一切如預期，關閉此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b4264-126">If everything looks as expected, close this dialog box.</span></span>  
  
 <span data-ttu-id="b4264-127">如需這些對話方塊的詳細資訊，請參閱[作業類別目錄：管理作業類別](job-categories-manage-job-categories.md)目錄和[作業類別目錄屬性和新的作業類別目錄](job-categories-properties-new-job-category.md)。</span><span class="sxs-lookup"><span data-stu-id="b4264-127">For more information on these dialog boxes, see [Job Categories: Manage Job Categories](job-categories-manage-job-categories.md) and [Job Categories Properties and New Job Category](job-categories-properties-new-job-category.md).</span></span>  

##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="b4264-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b4264-128">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-job-category"></a><span data-ttu-id="b4264-129">若要建立作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="b4264-129">To create a job category</span></span>  
  
1.  <span data-ttu-id="b4264-130">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4264-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b4264-131">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="b4264-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b4264-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b4264-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
 <span data-ttu-id="b4264-133">如需詳細資訊，請參閱[sp_add_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b4264-133">For more information, see [sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).</span></span>  

##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="b4264-134">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="b4264-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="b4264-135">**若要建立作業類別目錄**</span><span class="sxs-lookup"><span data-stu-id="b4264-135">**To create a job category**</span></span>  
  
 <span data-ttu-id="b4264-136">使用所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell 呼叫 `JobCategory` 類別。</span><span class="sxs-lookup"><span data-stu-id="b4264-136">Call the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span> <span data-ttu-id="b4264-137">如需範例程式碼，請參閱 [使用 SQL Server Agent 排程自動管理工作](sql-server-agent.md)。</span><span class="sxs-lookup"><span data-stu-id="b4264-137">For example code, see [Scheduling Automatic Administrative Tasks in SQL Server Agent](sql-server-agent.md).</span></span>  
