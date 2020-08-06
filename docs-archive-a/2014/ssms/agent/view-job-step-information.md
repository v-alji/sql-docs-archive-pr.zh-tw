---
title: 檢視作業步驟資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5d9fc6a006884bc564b5db2bfa8b168c8ae59149
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584279"
---
# <a name="view-job-step-information"></a><span data-ttu-id="d4bd6-102">View Job Step Information</span><span class="sxs-lookup"><span data-stu-id="d4bd6-102">View Job Step Information</span></span>
  <span data-ttu-id="d4bd6-103">本主題說明如何檢視 [作業步驟屬性] 對話方塊中的作業步驟詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-103">This topic describes how to view job step details in the Job Step Properties dialog.</span></span> <span data-ttu-id="d4bd6-104">其中還包括檢視作業步驟輸出的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-104">It also includes information about viewing job step output.</span></span>  
  
-   <span data-ttu-id="d4bd6-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="d4bd6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="d4bd6-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="d4bd6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="d4bd6-107">安全性</span><span class="sxs-lookup"><span data-stu-id="d4bd6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="d4bd6-108">**若要使用下列項目檢視作業步驟資訊：**</span><span class="sxs-lookup"><span data-stu-id="d4bd6-108">**To view job step information, using:**</span></span>  
  
     [<span data-ttu-id="d4bd6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d4bd6-109">SQL Server Management Studio</span></span>](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="d4bd6-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="d4bd6-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="d4bd6-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="d4bd6-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="d4bd6-112">若作業步驟已設定為將輸出寫入資料表或檔案，且作業已至少執行一次，您就可以在 **[作業步驟屬性]** 對話方塊的 **[進階]** 頁面上檢視其輸出。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-112">If the job step has been configured to write its output to a table or file and the job has run at least once, you can view its output on the **Advanced** page of the **Job Step Properties** dialog.</span></span> <span data-ttu-id="d4bd6-113">當作業或作業步驟被刪除後，輸出記錄檔也會自動刪除。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-113">When a job or job step is deleted, the output log is automatically deleted.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="d4bd6-114">Security</span><span class="sxs-lookup"><span data-stu-id="d4bd6-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="d4bd6-115">權限</span><span class="sxs-lookup"><span data-stu-id="d4bd6-115">Permissions</span></span>  
 <span data-ttu-id="d4bd6-116">若您不是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，就只能檢視您所擁有的作業。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-116">You can view only those jobs that you own, unless you are a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="d4bd6-117">此角色的成員可檢視所有作業與作業步驟詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-117">Members of this role can view all jobs and job step details.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="d4bd6-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d4bd6-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-job-step-information"></a><span data-ttu-id="d4bd6-119">若要檢視作業步驟資訊</span><span class="sxs-lookup"><span data-stu-id="d4bd6-119">To view job step information</span></span>  
  
1.  <span data-ttu-id="d4bd6-120">在**物件總管中，** 連接到的實例 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-120">In **Object Explorer,** connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="d4bd6-121">依序展開 [SQL Server Agent]\*\*\*\* 和 [作業]\*\*\*\*、以滑鼠右鍵按一下包含要檢視之作業步驟的作業，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-121">Expand **SQL Server Agent**, expand **Jobs**, right-click the job that contains the job step to be viewed, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d4bd6-122">在 **[作業屬性]** 對話方塊中，按一下 **[步驟]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-122">In the **Job Properties** dialog, click the **Steps** page.</span></span>  
  
4.  <span data-ttu-id="d4bd6-123">按一下所要檢視的作業步驟，再按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-123">Click the job step to be viewed, and click **Edit**.</span></span>  
  
5.  <span data-ttu-id="d4bd6-124">在 **[作業步驟屬性]** 對話方塊的 **[一般]** 頁面上，您可以檢視作業步驟的類型及其功能。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-124">On the **General** page of the **Job Step Properties** dialog, you can view the type of job step and what it does.</span></span>  
  
6.  <span data-ttu-id="d4bd6-125">按一下 **[進階]** 頁面，即可檢視下列項目： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 在作業步驟成功或失敗時所應採取的動作、作業步驟應嘗試多少次、寫入作業步驟輸出的位置，以及執行作業步驟的使用者身分。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-125">Click the **Advanced** page to view the actions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent takes if the job step succeeds or fails, how many times the job step should be attempted, where the job step output is written, and the user the job step runs as.</span></span>  
  
#### <a name="to-view-job-step-output"></a><span data-ttu-id="d4bd6-126">若要檢視作業步驟輸出</span><span class="sxs-lookup"><span data-stu-id="d4bd6-126">To view job step output</span></span>  
  
1.  <span data-ttu-id="d4bd6-127">在 **[作業步驟屬性]** 對話方塊中，按一下 **[進階]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-127">In the **Job Step Properties** dialog, click the **Advanced** page.</span></span>  
  
2.  <span data-ttu-id="d4bd6-128">視您所連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本之不同，您可以如下所示檢視作業步驟輸出檔案或資料表：</span><span class="sxs-lookup"><span data-stu-id="d4bd6-128">Depending on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] you are connected to, you can view either the job step output file or table as follows:</span></span>  
  
    -   <span data-ttu-id="d4bd6-129">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或更新版本時，只有在已核取 **[記錄至資料表]** 時，才可以按一下 **[檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-129">When you are connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or later, you can click **View** only when **Log to table** is checked.</span></span> <span data-ttu-id="d4bd6-130">在這種情況下，作業步驟輸出會寫入 **msdb** 資料庫的 **sysjobstepslogs** 資料表。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-130">In this case, the job step output is written to the **sysjobstepslogs** table in the **msdb** database.</span></span>  
  
    -   <span data-ttu-id="d4bd6-131">若作業步驟輸出寫入檔案中， **[檢視]** 按鈕就會停用。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-131">The **View** button is disabled when job step output is written to a file.</span></span> <span data-ttu-id="d4bd6-132">若要檢視作業步驟輸出檔，請使用 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="d4bd6-132">To view a job step output file, use Notepad.</span></span>  
  
  
