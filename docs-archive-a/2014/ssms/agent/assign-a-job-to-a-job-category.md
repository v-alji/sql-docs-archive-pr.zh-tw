---
title: 將作業指派至作業類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 208ff6722a9c18fd4dd0d061575f0d496af27810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606590"
---
# <a name="assign-a-job-to-a-job-category"></a><span data-ttu-id="82a83-102">將作業指派至作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="82a83-102">Assign a Job to a Job Category</span></span>
  <span data-ttu-id="82a83-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理物件，在中將 Agent 作業指派至作業類別目錄 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="82a83-103">This topic describes how to assign [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs to job categories in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="82a83-104">作業類別目錄可幫助您組織作業，以便於篩選與分組。</span><span class="sxs-lookup"><span data-stu-id="82a83-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="82a83-105">例如，您可以將所有的資料庫備份作業整理在資料庫維護類別中。</span><span class="sxs-lookup"><span data-stu-id="82a83-105">For example, you can organize all your database backup jobs in the Database Maintenance category.</span></span> <span data-ttu-id="82a83-106">您可以將作業指派到內建的作業類別目錄，您也可以建立使用者自訂的作業類別目錄，然後將作業指派給它。</span><span class="sxs-lookup"><span data-stu-id="82a83-106">You can assign jobs to built-in job categories, or you can create a user-defined job category and then assign jobs to that.</span></span>  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="82a83-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="82a83-107">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="82a83-108">Security</span><span class="sxs-lookup"><span data-stu-id="82a83-108">Security</span></span>  
 <span data-ttu-id="82a83-109">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="82a83-109">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="82a83-110">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="82a83-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="82a83-111">若要將作業指派至作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="82a83-111">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="82a83-112">在 **[物件總管]** 中，按一下加號展開要將作業指派至作業類別目錄的伺服器。</span><span class="sxs-lookup"><span data-stu-id="82a83-112">In **Object Explorer**, click the plus sign to expand the server where you want to assign a job to a job category.</span></span>  
  
2.  <span data-ttu-id="82a83-113">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="82a83-113">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="82a83-114">按一下加號展開 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="82a83-114">Click the plus sign to expand the **Jobs** folder.</span></span>  
  
4.  <span data-ttu-id="82a83-115">以滑鼠右鍵按一下要編輯的作業，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="82a83-115">Right-click the job you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="82a83-116">在 [**作業屬性-**_job_name_ ] 對話方塊的 [**類別目錄**] 清單中，選取您要指派給作業的作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="82a83-116">In the **Job Properties -**_job_name_ dialog box, in the **Category** list, select the job category you want to assign to the job.</span></span>  
  
6.  <span data-ttu-id="82a83-117">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="82a83-117">Click **OK**.</span></span>  
  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="82a83-118">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="82a83-118">Using Transact-SQL</span></span>  
  
#### <a name="to-assign-a-job-to-a-job-category"></a><span data-ttu-id="82a83-119">若要將作業指派至作業類別目錄</span><span class="sxs-lookup"><span data-stu-id="82a83-119">To assign a job to a job category</span></span>  
  
1.  <span data-ttu-id="82a83-120">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="82a83-120">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="82a83-121">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="82a83-121">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="82a83-122">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="82a83-122">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="82a83-123">如需詳細資訊，請參閱[sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="82a83-123">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="82a83-124">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="82a83-124">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="82a83-125">**若要將作業指派至作業類別目錄**</span><span class="sxs-lookup"><span data-stu-id="82a83-125">**To assign a job to a job category**</span></span>  
  
 <span data-ttu-id="82a83-126">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobCategory` 類別。</span><span class="sxs-lookup"><span data-stu-id="82a83-126">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
  
  
