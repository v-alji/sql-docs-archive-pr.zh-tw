---
title: 定義 Transact-SQL 作業步驟選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc1d6412e52e74ce0c6d987d6189c0c72ffd7df7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687413"
---
# <a name="define-transact-sql-job-step-options"></a><span data-ttu-id="0b932-102">Define Transact-SQL Job Step Options</span><span class="sxs-lookup"><span data-stu-id="0b932-102">Define Transact-SQL Job Step Options</span></span>
  <span data-ttu-id="0b932-103">本主題描述如何 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 使用或 SQL Server 管理物件，在中定義 Agent 作業步驟的選項 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0b932-103">This topic describes how to define options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job steps in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or SQL Server Management Objects.</span></span>  
  
 <span data-ttu-id="0b932-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0b932-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0b932-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0b932-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0b932-106">安全性</span><span class="sxs-lookup"><span data-stu-id="0b932-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="0b932-107">**若要使用下列項目定義 Transact-SQL 作業步驟選項** ：</span><span class="sxs-lookup"><span data-stu-id="0b932-107">**To define Transact-SQL job step options, using:** ,</span></span>  
  
     [<span data-ttu-id="0b932-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0b932-108">SQL Server Management Studio</span></span>](#SSMS)  
  
     [<span data-ttu-id="0b932-109">SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="0b932-109">SQL Server Management Objects</span></span>](#SMO)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0b932-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="0b932-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0b932-111">Security</span><span class="sxs-lookup"><span data-stu-id="0b932-111">Security</span></span>  
 <span data-ttu-id="0b932-112">如需詳細資訊，請參閱＜ [實作 SQL Server Agent 安全性](implement-sql-server-agent-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0b932-112">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="0b932-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0b932-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-transact-sql-job-step-options"></a><span data-ttu-id="0b932-114">若要定義 Transact-SQL 作業步驟選項</span><span class="sxs-lookup"><span data-stu-id="0b932-114">To define Transact-SQL job step options</span></span>  
  
1.  <span data-ttu-id="0b932-115">在 **[物件總管]** 中，展開 **[SQL Server Agent]**，展開 **[作業]**，以滑鼠右鍵按一下要編輯的作業，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0b932-115">In **Object Explorer**, expand **SQL Server Agent**, expand **Jobs**, right-click the job you want to edit, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0b932-116">按一下 **[步驟]** 頁面，再按一下作業步驟，然後按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="0b932-116">Click the **Steps** page, click a job step, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="0b932-117">在 **[作業步驟屬性]** 對話方塊中，確認作業類型是 **Transact-SQL script (TSQL)**，然後選取 **[進階]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="0b932-117">On the **Job Step Properties** dialog, confirm that the job type is **Transact-SQL script (TSQL)**, and then select the **Advanced** page.</span></span>  
  
4.  <span data-ttu-id="0b932-118">從 **[成功時的動作]** 清單中，指定當作業成功時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="0b932-118">Specify an action to take if the job is successful by selecting from the **On success action** list.</span></span>  
  
5.  <span data-ttu-id="0b932-119">在 **[重試次數]** 方塊中輸入 0 到 9999 之間的數字，以指定重試次數。</span><span class="sxs-lookup"><span data-stu-id="0b932-119">Specify a number of retry attempts by entering a number from 0 to 9999 into the **Retry attempts** box.</span></span>  
  
6.  <span data-ttu-id="0b932-120">在 **[重試間隔]** 方塊中輸入 0 到 9999 的分鐘數，以指定重試間隔。</span><span class="sxs-lookup"><span data-stu-id="0b932-120">Specify a retry interval by entering a number of minutes from 0 to 9999 into the **Retry interval** box.</span></span>  
  
7.  <span data-ttu-id="0b932-121">從 **[失敗時的動作]** 清單中，指定當作業失敗時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="0b932-121">Specify an action to take if the job fails by choosing from the **On failure action** list.</span></span>  
  
8.  <span data-ttu-id="0b932-122">如果作業是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼，您可以從下列選項中選擇：</span><span class="sxs-lookup"><span data-stu-id="0b932-122">If the job is a [!INCLUDE[tsql](../../includes/tsql-md.md)] script, you can choose from the following options:</span></span>  
  
    -   <span data-ttu-id="0b932-123">輸入 **[輸出檔案]** 的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b932-123">Enter the name of an **Output file**.</span></span> <span data-ttu-id="0b932-124">根據預設，每次執行作業步驟時都會覆寫此檔案。</span><span class="sxs-lookup"><span data-stu-id="0b932-124">By default the file is overwritten each time the job step executes.</span></span> <span data-ttu-id="0b932-125">如果您不想要覆寫輸出檔，請選取 **[將輸出附加至現有檔案]**。</span><span class="sxs-lookup"><span data-stu-id="0b932-125">If you do not want the output file overwritten, check **Append output to existing file**.</span></span> <span data-ttu-id="0b932-126">此選項僅適用於 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="0b932-126">This option is only available to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="0b932-127">請注意， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 不允許使用者檢視檔案系統上的任意檔案，所以您不能使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來檢視已寫入檔案系統的作業步驟記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0b932-127">Note that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] does not allow users to view arbitrary files on the file system, so you cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view job step logs that are written to the file system.</span></span>  
  
    -   <span data-ttu-id="0b932-128">若要將作業步驟記錄至資料庫資料表，請選取 **[記錄至資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="0b932-128">Check **Log to table** if you want to log the job step to a database table.</span></span> <span data-ttu-id="0b932-129">根據預設，每次執行作業步驟時都會覆寫此資料表內容。</span><span class="sxs-lookup"><span data-stu-id="0b932-129">By default the table contents are overwritten each time the job step executes.</span></span> <span data-ttu-id="0b932-130">如果您不想要覆寫資料表內容，請選取 **[將輸出附加至資料表的現有項目]**。</span><span class="sxs-lookup"><span data-stu-id="0b932-130">If you do not want the table contents overwritten, check **Append output to existing entry in table**.</span></span> <span data-ttu-id="0b932-131">作業步驟執行之後，您可以按一下 **[檢視]** 以檢視這個資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="0b932-131">After the job step executes, you can view the contents of this table by clicking **View**.</span></span>  
  
    -   <span data-ttu-id="0b932-132">如果您希望步驟的記錄中包含輸出，請選取 **[包含步驟輸出於記錄中]** 。</span><span class="sxs-lookup"><span data-stu-id="0b932-132">Check **Include step output in history** if you want the output included in the step's history.</span></span> <span data-ttu-id="0b932-133">只有無錯誤時，才會顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="0b932-133">Output will only be shown if there were no errors.</span></span> <span data-ttu-id="0b932-134">另外，輸出可能被截斷。</span><span class="sxs-lookup"><span data-stu-id="0b932-134">Also, output may be truncated.</span></span>  
  
9. <span data-ttu-id="0b932-135">如果您是 **系統管理員 (sysadmin)** 固定伺服器角色的成員，而您想以不同的 SQL 登入執行這個作業步驟，請從 **[指定執行時的身分]** 清單中選取 SQL 登入。</span><span class="sxs-lookup"><span data-stu-id="0b932-135">If you are a member of the **sysadmin** fixed server role and you want to run this job step as a different SQL login, select the SQL login from the **Run as user** list.</span></span>  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="0b932-136">使用 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="0b932-136">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="0b932-137">**若要定義 Transact-SQL 作業步驟選項**</span><span class="sxs-lookup"><span data-stu-id="0b932-137">**To define Transact-SQL job step options**</span></span>  
  
 <span data-ttu-id="0b932-138">透過所選的程式語言，例如 Visual Basic、Visual C# 或 PowerShell，使用 `JobStep` 類別。</span><span class="sxs-lookup"><span data-stu-id="0b932-138">Use the `JobStep` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell.</span></span>  
  
  
