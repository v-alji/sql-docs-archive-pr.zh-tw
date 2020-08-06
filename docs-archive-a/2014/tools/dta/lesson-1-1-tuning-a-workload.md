---
title: 微調工作負載 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
author: stevestein
ms.author: sstein
ms.openlocfilehash: f95aab55d402ac72228dcc4326ad00ea15e7471f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703625"
---
# <a name="tuning-a-workload"></a><span data-ttu-id="83b84-102">微調工作負載</span><span class="sxs-lookup"><span data-stu-id="83b84-102">Tuning a Workload</span></span>
  <span data-ttu-id="83b84-103">您可以利用 Database Engine Tuning Advisor 來找出最好的實體資料庫設計，以改進您選擇要微調的資料庫和資料表的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="83b84-103">The Database Engine Tuning Advisor can be used to find the best physical database design for query performance on the databases and tables that you select for tuning.</span></span>  
  
 <span data-ttu-id="83b84-104">此工作會使用 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="83b84-104">This task uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="83b84-105">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="83b84-105">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="83b84-106">若要安裝範例資料庫，請參閱＜ [安裝 SQL Server 範例和範例資料庫](http://sqlserversamples.codeplex.com)＞。</span><span class="sxs-lookup"><span data-stu-id="83b84-106">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
### <a name="tune-a-workload-transact-sql-script-file"></a><span data-ttu-id="83b84-107">微調工作負載 Transact-SQL 指令碼檔案</span><span class="sxs-lookup"><span data-stu-id="83b84-107">Tune a workload Transact-SQL script file</span></span>  
  
1.  <span data-ttu-id="83b84-108">從下列步驟複製一個或多個範例 SELECT 陳述式：「A.</span><span class="sxs-lookup"><span data-stu-id="83b84-108">Copy a sample SELECT statement or statements from "A.</span></span> <span data-ttu-id="83b84-109">使用 SELECT 擷取資料列和資料行＞(在 [SELECT 範例 &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql) 中)，然後將陳述式貼入 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="83b84-109">Using SELECT to retrieve rows and columns" in [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql) and paste the statements into the Query Editor of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="83b84-110">在您很容易找到的目錄中，將檔案儲存成 **MyScript.sql**。</span><span class="sxs-lookup"><span data-stu-id="83b84-110">Save the file as **MyScript.sql** in a directory where you can easily find it.</span></span>  
  
2.  <span data-ttu-id="83b84-111">啟動 Database Engine Tuning Advisor。</span><span class="sxs-lookup"><span data-stu-id="83b84-111">Start Database Engine Tuning Advisor.</span></span> <span data-ttu-id="83b84-112">請參閱 [啟動 Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="83b84-112">See [Launching Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="83b84-113">在 Database Engine Tuning Advisor GUI 右窗格的 [工作階段名稱]\*\*\*\* 中，輸入 **MySession**。</span><span class="sxs-lookup"><span data-stu-id="83b84-113">In the right pane of the Database Engine Tuning Advisor GUI, type **MySession** in **Session name**.</span></span>  
  
4.  <span data-ttu-id="83b84-114">選取 [工作負載]\*\*\*\* 的 [檔案]\*\*\*\*，然後按一下 [瀏覽工作負載檔案]\*\*\*\* 按鈕，來尋找您在步驟 1 儲存的 **MyScript.sql** 檔。</span><span class="sxs-lookup"><span data-stu-id="83b84-114">Select **File** for your **Workload**, and click the **Browse for a workload file** button to locate the **MyScript.sql** file that you saved in Step 1.</span></span>  
  
5.  <span data-ttu-id="83b84-115">在 [工作負載分析的資料庫]\*\*\*\* 清單中選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，在 [選取要微調的資料庫與資料表]\*\*\*\* 方格中選取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]，並保留已選取的 [儲存微調記錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="83b84-115">Select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Database for workload analysis** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Select databases and tables to tune** grid, and leave **Save tuning log** selected.</span></span> <span data-ttu-id="83b84-116">[工作負載分析的資料庫]\*\*\*\* 指定在微調工作負載時 Database Engine Tuning Advisor 所連接的第一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="83b84-116">**Database for workload analysis** specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="83b84-117">在微調開始之後，Database Engine Tuning Advisor 會連接到工作負載包含的 `USE DATABASE` 陳述式所指定的資料庫。</span><span class="sxs-lookup"><span data-stu-id="83b84-117">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
6.  <span data-ttu-id="83b84-118">按一下 [**微調選項**] 索引標籤。您不會在此練習中設定任何微調選項，但請花點時間檢查預設的微調選項。</span><span class="sxs-lookup"><span data-stu-id="83b84-118">Click the **Tuning Options** tab. You will not set any tuning options for this practice, but take a moment to review the default tuning options.</span></span> <span data-ttu-id="83b84-119">請按 F1 鍵來檢視這個索引標籤頁的說明。</span><span class="sxs-lookup"><span data-stu-id="83b84-119">Press F1 to view the Help for this tabbed page.</span></span> <span data-ttu-id="83b84-120">請按一下 [進階選項]\*\*\*\* 來檢視其他微調選項。</span><span class="sxs-lookup"><span data-stu-id="83b84-120">Click **Advanced Options** to view additional tuning options.</span></span> <span data-ttu-id="83b84-121">如需這裡所顯示之微調選項的相關資訊，請按一下 [進階微調選項]\*\*\*\* 對話方塊中的 [說明]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="83b84-121">Click **Help** in the **Advanced Tuning Options** dialog box for information about the tuning options that are displayed there.</span></span> <span data-ttu-id="83b84-122">請按一下 [取消]\*\*\*\* 來關閉 [進階微調選項]\*\*\*\* 對話方塊，保持選取預設的選項。</span><span class="sxs-lookup"><span data-stu-id="83b84-122">Click **Cancel** to close the **Advanced Tuning Options** dialog box, leaving the default options selected.</span></span>  
  
7.  <span data-ttu-id="83b84-123">按一下工具列上的 **[開始分析]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="83b84-123">Click the **Start Analysis** button on the toolbar.</span></span> <span data-ttu-id="83b84-124">當 Database Engine Tuning Advisor 分析工作負載時，您可以在 [**進度**] 索引標籤上監視狀態。微調完成時，會顯示 [**建議**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="83b84-124">While Database Engine Tuning Advisor is analyzing the workload, you can monitor the status on the **Progress** tab. When tuning is complete, the **Recommendations** tab is displayed.</span></span>  
  
     <span data-ttu-id="83b84-125">如果您收到關於微調停止日期和時間的錯誤，請檢查主要 [**微調選項**]**索引標籤**上的 [停止時間]。請確定 [**停止**日期] 和 [時間] 大於目前的日期和時間，如有必要，請變更它們。</span><span class="sxs-lookup"><span data-stu-id="83b84-125">If you receive an error about the tuning stop date and time, check the **Stop at** time on the main **Tuning Options** tab. Make sure the **Stop at** date and time are greater than the current date and time, and if necessary, change them.</span></span>  
  
8.  <span data-ttu-id="83b84-126">完成分析之後，在 [動作]\*\*\*\* 功能表上，按一下 [儲存建議]\*\*\*\*，將建議儲存成一份 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="83b84-126">After the analysis completes, save your recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script by clicking **Save Recommendations** on the **Actions** menu.</span></span> <span data-ttu-id="83b84-127">在 [另存新檔]\*\*\*\* 對話方塊中，導覽到用來儲存建議指令碼的目錄，再輸入 **MyRecommendations** 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="83b84-127">In the **Save As** dialog box, navigate to the directory where you want to save the recommendations script, and type the file name **MyRecommendations**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="83b84-128">總結</span><span class="sxs-lookup"><span data-stu-id="83b84-128">Summary</span></span>  
 <span data-ttu-id="83b84-129">您已完成 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫之簡單 SELECT 陳述式工作負載的微調。</span><span class="sxs-lookup"><span data-stu-id="83b84-129">You have completed tuning a simple SELECT statement workload on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="83b84-130">另外，Database Engine Tuning Advisor 也可以利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤檔和資料表來作為微調工作負載。</span><span class="sxs-lookup"><span data-stu-id="83b84-130">The Database Engine Tuning Advisor can also take [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace files and tables as tuning workloads.</span></span> <span data-ttu-id="83b84-131">下一項工作告訴您如何檢視和解譯練習微調結果所得出的微調建議。</span><span class="sxs-lookup"><span data-stu-id="83b84-131">The next task shows you how to view and interpret the tuning recommendations that you received as a result of the practice tuning.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="83b84-132">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="83b84-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="83b84-133">檢視微調建議</span><span class="sxs-lookup"><span data-stu-id="83b84-133">Viewing Tuning Recommendations</span></span>](lesson-1-2-viewing-tuning-recommendations.md)  
  
  
