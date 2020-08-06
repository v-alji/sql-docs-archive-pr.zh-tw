---
title: 資料品質專案 (DQS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: a43fc9c0-19b6-414a-8661-4c7c55e0c03e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 471d528144b6687ffa3aeedb82cf479817c4edc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592868"
---
# <a name="data-quality-projects-dqs"></a><span data-ttu-id="ccbe4-102">資料品質專案 (DQS)</span><span class="sxs-lookup"><span data-stu-id="ccbe4-102">Data Quality Projects (DQS)</span></span>
  <span data-ttu-id="ccbe4-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 中的資料品質專案是使用知識庫改善來源資料品質的一種工具，其方式是執行 *資料清理* 和 *資料比對* 活動，然後將產生的資料匯出到 SQL Server 資料庫或 .csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-103">A data quality project in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a means of using a knowledge base to improve the quality of your source data by performing *data cleansing* and *data matching* activities, and then exporting the resultant data to a SQL Server database or a .csv file.</span></span> <span data-ttu-id="ccbe4-104">您可以建立資料品質專案當做清理專案或比對專案，以執行各自的活動。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-104">You can create a data quality project as a cleansing project or a matching project to perform respective activities.</span></span> <span data-ttu-id="ccbe4-105">清理專案和比對專案可以使用相同的知識庫執行，因為用於資料清理和比對的知識可以內建到相同的知識庫中。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-105">Cleansing and matching projects can be run using the same knowledge base, because knowledge for data cleansing and matching can be built into the same knowledge base.</span></span>  
  
 <span data-ttu-id="ccbe4-106">資料品質專案具有以下優點：</span><span class="sxs-lookup"><span data-stu-id="ccbe4-106">A data quality project has the following benefits:</span></span>  
  
-   <span data-ttu-id="ccbe4-107">可讓您使用 DQS 知識庫中的知識來針對來源資料執行資料清理。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-107">Enables you to perform data cleansing on your source data by using the knowledge in a DQS knowledge base.</span></span>  
  
-   <span data-ttu-id="ccbe4-108">可讓您使用知識庫中的比對原則來針對來源資料執行資料比對。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-108">Enables you to perform data matching on your source data by using the matching policy in a knowledge base.</span></span>  
  
-   <span data-ttu-id="ccbe4-109">提供精靈引導您執行清理和比對活動，並根據您的選擇將資料匯出到 SQL Server 資料庫或 .csv 檔案。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-109">Provides a wizard to guide you through the cleansing and matching activities, and export the data as per your selection to a SQL Server database or to a .csv file.</span></span> <span data-ttu-id="ccbe4-110">資料監管可以使用資料品質專案來執行及控制電腦輔助/互動式清理和資料比對步驟。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-110">The data steward can use the data quality project to run and control the computer-assisted/interactive cleansing and data matching steps.</span></span>  
  
##  <a name="data-quality-project-cleansing-activity"></a><a name="Cleansing"></a><span data-ttu-id="ccbe4-111">資料品質專案：清理活動</span><span class="sxs-lookup"><span data-stu-id="ccbe4-111">Data Quality Project: Cleansing Activity</span></span>  
 <span data-ttu-id="ccbe4-112">清理資料品質專案可讓您根據知識庫來清理來源資料。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-112">A cleansing data quality project enables you to cleanse your source data based on a knowledge base.</span></span> <span data-ttu-id="ccbe4-113">DQS 中的資料清理活動是兩個步驟的程序：</span><span class="sxs-lookup"><span data-stu-id="ccbe4-113">The data cleansing activity in DQS is a two-step process:</span></span>  
  
1.  <span data-ttu-id="ccbe4-114">*電腦輔助* 資料清理程序，可針對知識庫中的知識分析來源資料以及建議變更。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-114">A *computer-assisted* data cleansing process that analyzes source data against the knowledge in the knowledge base, and proposes changes.</span></span> <span data-ttu-id="ccbe4-115">處理過的資料會由 DQS 加以分類 (建議、新的、無效、已更正和正確)，然後顯示給使用者以供進一步處理。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-115">The processed data is categorized (suggested, new, invalid, corrected, and correct) by DQS, and displayed to the user for further processing.</span></span>  
  
2.  <span data-ttu-id="ccbe4-116">*互動式* 清理程序，可讓資料監管核准、拒絕或修改電腦輔助的資料清理程序所提議的資料。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-116">An *interactive* cleansing process that enables the data steward to approve, reject, or modify the data proposed by the computer-assisted data cleansing process.</span></span>  
  
 <span data-ttu-id="ccbe4-117">如需有關資料品質專案中清理活動的詳細資訊，請參閱＜ [Data Cleansing](../../2014/data-quality-services/data-cleansing.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-117">For detailed information about the cleansing activity in a data quality project, see [Data Cleansing](../../2014/data-quality-services/data-cleansing.md).</span></span>  
  
##  <a name="data-quality-project-matching-activity"></a><a name="Matching"></a><span data-ttu-id="ccbe4-118">資料品質專案：比對活動</span><span class="sxs-lookup"><span data-stu-id="ccbe4-118">Data Quality Project: Matching Activity</span></span>  
 <span data-ttu-id="ccbe4-119">比對資料品質專案可讓您根據知識庫中的比對原則來執行比對活動，藉由識別完全相符和大致相符來避免資料重複，藉此讓您移除重複的資料。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-119">A matching data quality project enables you to perform matching activity based on matching policy in a knowledge base to prevent data duplication by identifying exact and approximate matches, and thereby enabling you to remove duplicate data.</span></span> <span data-ttu-id="ccbe4-120">建議您先清理資料，然後再執行資料的比對。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-120">It is recommended that you cleanse your data before running matching on it.</span></span> <span data-ttu-id="ccbe4-121">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="ccbe4-121">To do so:</span></span>  
  
1.  <span data-ttu-id="ccbe4-122">建立資料品質專案、選取 **[清理]** 活動、針對來源資料完成資料清理活動，然後將資料匯出到 SQL Server 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-122">Create a data quality project, select the **Cleansing** activity, complete the data cleansing activity on your source data, and then export it to a table in a SQL Server database.</span></span>  
  
2.  <span data-ttu-id="ccbe4-123">使用包含比對原則的知識庫建立另一個資料品質專案、選取 **[比對]** 活動，然後在 **[對應]** 頁面上選取您在步驟 1 匯出之清理資料所在的資料庫和資料表。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-123">Create another data quality project by using a knowledge base that contains a matching policy, select the **Matching** activity, and then in the **Map** page, select the database and the table where you exported the cleansed data in step 1.</span></span>  
  
3.  <span data-ttu-id="ccbe4-124">針對清理的資料完成比對活動。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-124">Complete the matching activity on the cleansed data.</span></span>  
  
 <span data-ttu-id="ccbe4-125">如需有關資料品質專案中比對活動的詳細資訊，請參閱＜ [Data Matching](../../2014/data-quality-services/data-matching.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-125">For detailed information about the matching activity in a data quality project, see [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
##  <a name="data-profiling-and-notifications"></a><a name="ProfilingNotification"></a><span data-ttu-id="ccbe4-126">資料分析和通知</span><span class="sxs-lookup"><span data-stu-id="ccbe4-126">Data Profiling and Notifications</span></span>  
 <span data-ttu-id="ccbe4-127">在資料品質專案中執行清理和比對活動之後，您可以看到有關 DQS 正在處理之資料的即時統計資料和資訊。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-127">While running the cleansing and matching activities in a data quality project, you can see real-time statistics and information about the data that is being processed by DQS.</span></span> <span data-ttu-id="ccbe4-128">資料分析會幫助您評估清理和比對程序的效用，您也可以判斷資料清理或比對幫助提升資料品質的程度。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-128">Data profiling helps you assess the effectiveness of the cleansing and matching processes, and you can potentially determine the extent to which data cleansing or matching helped improve the data quality.</span></span> <span data-ttu-id="ccbe4-129">DQS 分析會提供兩個資料品質維度： *完整性* (資料存在的程度) 和 *精確度* (可將資料用於預定用途的程度)。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-129">DQS profiling provides two data-quality dimensions: *completeness* (the extent to which data is present) and *accuracy* (the extent to which data can be used for its intended use).</span></span> <span data-ttu-id="ccbe4-130">此外，根據資料分析資訊而定，為了增強資料清理與資料比對作業所採取之動作的相關通知會顯示給使用者。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-130">Further, based on the data profiling information, notifications are displayed to the user on the actions that can be taken to enhance the data cleansing and data matching operations.</span></span> <span data-ttu-id="ccbe4-131">如需有關資料分析和通知的詳細資訊，請參閱＜ [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-131">For detailed information about data profiling and notifications, see [Data Profiling and Notifications in DQS](../../2014/data-quality-services/data-profiling-and-notifications-in-dqs.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="ccbe4-132">相關工作</span><span class="sxs-lookup"><span data-stu-id="ccbe4-132">Related Tasks</span></span>  
  
|<span data-ttu-id="ccbe4-133">工作描述</span><span class="sxs-lookup"><span data-stu-id="ccbe4-133">Task Description</span></span>|<span data-ttu-id="ccbe4-134">主題</span><span class="sxs-lookup"><span data-stu-id="ccbe4-134">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ccbe4-135">描述如何建立資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-135">Describes how to create a data quality project.</span></span>|[<span data-ttu-id="ccbe4-136">建立資料品質專案</span><span class="sxs-lookup"><span data-stu-id="ccbe4-136">Create a Data Quality Project</span></span>](../../2014/data-quality-services/create-a-data-quality-project.md)|  
|<span data-ttu-id="ccbe4-137">描述如何管理 (開啟、解除鎖定、重新命名和刪除) 資料品質專案。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-137">Describes how to manage (open, unlock, rename, and delete) a data quality project.</span></span>|[<span data-ttu-id="ccbe4-138">管理 &#40;開啟、解除鎖定、重新命名和刪除資料品質專案&#41;</span><span class="sxs-lookup"><span data-stu-id="ccbe4-138">Manage &#40;Open, Unlock, Rename, and Delete&#41; a Data Quality Project</span></span>](../../2014/data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)|  
|<span data-ttu-id="ccbe4-139">描述如何在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中開啟 Integration Services 專案。</span><span class="sxs-lookup"><span data-stu-id="ccbe4-139">Describes how to open an Integration Services project in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="ccbe4-140">在 Data Quality Client 中開啟 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="ccbe4-140">Open Integration Services Projects in Data Quality Client</span></span>](../../2014/data-quality-services/open-integration-services-projects-in-data-quality-client.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ccbe4-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccbe4-141">See Also</span></span>  
 [<span data-ttu-id="ccbe4-142">DQS 知識庫與定義域</span><span class="sxs-lookup"><span data-stu-id="ccbe4-142">DQS Knowledge Bases and Domains</span></span>](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
