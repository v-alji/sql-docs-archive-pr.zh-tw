---
title: 變更作業類別目錄的成員資格 | Microsoft Docs
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
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
ms.openlocfilehash: d9ed0db394f63594937ad923734b07fed8050955
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606587"
---
# <a name="change-the-membership-of-a-job-category"></a><span data-ttu-id="04dfa-102">變更作業類別的成員資格</span><span class="sxs-lookup"><span data-stu-id="04dfa-102">Change the Membership of a Job Category</span></span>
  <span data-ttu-id="04dfa-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 SQL Server 管理物件，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中變更作業類別目錄的成員資格。</span><span class="sxs-lookup"><span data-stu-id="04dfa-103">This topic describes how to change the membership of the job category in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="04dfa-104">作業類別目錄可幫助您組織作業，以便於篩選與分組。</span><span class="sxs-lookup"><span data-stu-id="04dfa-104">Job categories help you organize your jobs for easy filtering and grouping.</span></span> <span data-ttu-id="04dfa-105">您可以建立自己的作業類別目錄。</span><span class="sxs-lookup"><span data-stu-id="04dfa-105">You can create your own job categories.</span></span> <span data-ttu-id="04dfa-106">您還可以變更作業類別目錄中的 Microsoft SQL Server Agent 作業成員資格。</span><span class="sxs-lookup"><span data-stu-id="04dfa-106">You can also change Microsoft SQL Server Agent jobs membership in job categories.</span></span>  
  
 <span data-ttu-id="04dfa-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="04dfa-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="04dfa-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="04dfa-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="04dfa-109">安全性</span><span class="sxs-lookup"><span data-stu-id="04dfa-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="04dfa-110">**若要使用下列項目變更作業類別目錄的成員資格：**</span><span class="sxs-lookup"><span data-stu-id="04dfa-110">**To change the membership of a job category, using:**</span></span>  
  
     [<span data-ttu-id="04dfa-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="04dfa-111">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="04dfa-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="04dfa-112">Transact-SQL</span></span>](#TSQL)  
  
     [<span data-ttu-id="04dfa-113">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="04dfa-113">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="04dfa-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="04dfa-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="04dfa-115">Security</span><span class="sxs-lookup"><span data-stu-id="04dfa-115">Security</span></span>  
 <span data-ttu-id="04dfa-116">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="04dfa-116">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="04dfa-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="04dfa-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="04dfa-118">變更作業類別目錄的成員資格</span><span class="sxs-lookup"><span data-stu-id="04dfa-118">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="04dfa-119">在 **[物件總管]** 中，按一下加號展開要編輯作業類別目錄所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="04dfa-119">In **Object Explorer**, click the plus sign to expand the server where you want to edit a job category.</span></span>  
  
2.  <span data-ttu-id="04dfa-120">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="04dfa-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="04dfa-121">以滑鼠右鍵按一下 [作業]\*\*\*\* 資料夾，然後選取 [管理作業類別目錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04dfa-121">Right-click the **Jobs** folder and select **Manage Job Categories**.</span></span>  
  
4.  <span data-ttu-id="04dfa-122">在 [管理作業類別目錄 <伺服器名稱>]\*\*\*\*__ 對話方塊中，選取要編輯的作業類別目錄，然後按一下 [檢視作業]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04dfa-122">In the **Manage Job Categories**_server_name_ dialog box, select the job category that you want to edit, and then click **View Jobs**.</span></span>  
  
5.  <span data-ttu-id="04dfa-123">選取 **[顯示所有作業]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="04dfa-123">Select the **Show all jobs** check box.</span></span>  
  
6.  <span data-ttu-id="04dfa-124">若要將作業加入至類別目錄，在主要方格中選取該作業所對應之 **[選取]** 資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="04dfa-124">To add a job to the category, in the main grid, select the check box in the **Select** column corresponding to the job.</span></span> <span data-ttu-id="04dfa-125">若要移除類別目錄中的作業，請清除該方塊。</span><span class="sxs-lookup"><span data-stu-id="04dfa-125">To remove a job from the category, clear the box.</span></span> <span data-ttu-id="04dfa-126">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="04dfa-126">When finished, click **OK**.</span></span>  
  
7.  <span data-ttu-id="04dfa-127">關閉 [管理作業類別目錄 <伺服器名稱>]\*\*\*\*__ 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="04dfa-127">Close the **Manage Job Categories**_server_name_ dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="04dfa-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="04dfa-128">Using Transact-SQL</span></span>  
  
#### <a name="to-change-the-membership-of-a-job-category"></a><span data-ttu-id="04dfa-129">變更作業類別目錄的成員資格</span><span class="sxs-lookup"><span data-stu-id="04dfa-129">To change the membership of a job category</span></span>  
  
1.  <span data-ttu-id="04dfa-130">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="04dfa-130">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="04dfa-131">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="04dfa-131">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="04dfa-132">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="04dfa-132">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 <span data-ttu-id="04dfa-133">如需詳細資訊，請參閱[sp_update_job &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="04dfa-133">For more information, see [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="04dfa-134">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="04dfa-134">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="04dfa-135">**變更作業類別目錄的成員資格**</span><span class="sxs-lookup"><span data-stu-id="04dfa-135">**To change the membership of a job category**</span></span>  
  
 <span data-ttu-id="04dfa-136">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobCategory` 類別。</span><span class="sxs-lookup"><span data-stu-id="04dfa-136">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
