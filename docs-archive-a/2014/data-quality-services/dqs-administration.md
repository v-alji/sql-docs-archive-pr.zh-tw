---
title: DQS 管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- dqs administration
- administration
- dqs,adminstration
ms.assetid: 9940ef5d-f6f6-4dec-9414-1077a4d7f12b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1803759f0ada269960c5abf1c3ee9f528fa53b86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592857"
---
# <a name="dqs-administration"></a><span data-ttu-id="c7522-102">dqs 管理</span><span class="sxs-lookup"><span data-stu-id="c7522-102">DQS Administration</span></span>
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] <span data-ttu-id="c7522-103">(DQS) 可讓您管理在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上執行的各種 DQS 活動、設定與 DQS 活動相關的伺服器層級屬性、設定 Reference Data Service 設定，以及設定 DQS 記錄設定。</span><span class="sxs-lookup"><span data-stu-id="c7522-103">(DQS) allows you to administer and manage various DQS activities performed on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], configure server-level properties related to DQS activities, configure the Reference Data Service settings, and configure DQS log settings.</span></span> <span data-ttu-id="c7522-104">這些操作是透過 **中的** [管理] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]功能完成。</span><span class="sxs-lookup"><span data-stu-id="c7522-104">These things are done through the **Administration** feature in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="c7522-105">根據您在 DQS 中的安全性存取權 (角色) 而定，您會被授與/拒絕對此區域中某些功能的存取。</span><span class="sxs-lookup"><span data-stu-id="c7522-105">Depending upon your security access (role) in DQS, you are granted/denied access to certain functionalities in this area.</span></span>  
  
 <span data-ttu-id="c7522-106">除了這些管理活動之外，本主題也提供不使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]執行管理活動、備份與還原 DQS 資料庫的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c7522-106">Apart from these administration activities, this topic also provides information about an administration activity, backing up and restoring DQS databases, which is not performed using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
 <span data-ttu-id="c7522-107">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 中的管理功能具有下列優點：</span><span class="sxs-lookup"><span data-stu-id="c7522-107">The administration feature in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] has the following benefits:</span></span>  
  
-   <span data-ttu-id="c7522-108">讓資料管理人從 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 監控 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]上的各種 DQS 活動。</span><span class="sxs-lookup"><span data-stu-id="c7522-108">Enables data stewards to monitor various DQS activities on a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] from a [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
-   <span data-ttu-id="c7522-109">讓 DQS 系統管理員從 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 監控 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]上的 DQS 活動，並 *終止* 正在執行的活動或 *停止* 活動中正在執行的程序 (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="c7522-109">Enables DQS administrators to monitor the DQS activities on a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] from a [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and *terminate* a running activity or *stop* a running process within an activity, if required.</span></span>  
  
-   <span data-ttu-id="c7522-110">設定參考資料服務設定，例如使用 Azure Marketplace 和管理直接協力廠商參考資料服務提供者的連線能力。</span><span class="sxs-lookup"><span data-stu-id="c7522-110">Configure reference data service settings such as setting up connectivity with Azure Marketplace and managing direct third-party reference data service providers.</span></span>  
  
-   <span data-ttu-id="c7522-111">設定清理與比對活動的臨界值。</span><span class="sxs-lookup"><span data-stu-id="c7522-111">Configure threshold values for the cleansing and matching activities.</span></span>  
  
-   <span data-ttu-id="c7522-112">啟用/停用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中的通知。</span><span class="sxs-lookup"><span data-stu-id="c7522-112">Enable/disable notifications in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
-   <span data-ttu-id="c7522-113">根據事件的嚴重性層級設定記錄。</span><span class="sxs-lookup"><span data-stu-id="c7522-113">Configure logging based on the severity level of the events.</span></span>  
  
##  <a name="administration-activities-by-using-data-quality-client"></a><a name="AdminUsingClent"></a><span data-ttu-id="c7522-114">使用 Data Quality Client 的系統管理活動</span><span class="sxs-lookup"><span data-stu-id="c7522-114">Administration Activities by Using Data Quality Client</span></span>  
 <span data-ttu-id="c7522-115">這些活動是使用 **中的** [管理] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]功能所執行。</span><span class="sxs-lookup"><span data-stu-id="c7522-115">These activities are performed by using the **Administration** feature in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
### <a name="activity-monitoring"></a><span data-ttu-id="c7522-116">活動監控</span><span class="sxs-lookup"><span data-stu-id="c7522-116">Activity Monitoring</span></span>  
 <span data-ttu-id="c7522-117">**中的** [活動監控] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 畫面會顯示關於在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上執行之每個活動的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c7522-117">The **Activity Monitoring** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] displays detailed information about each activity performed on a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="c7522-118">資料管理人主要使用這個畫面，對 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 應用程式連接的 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 上執行的所有活動執行高階監視。</span><span class="sxs-lookup"><span data-stu-id="c7522-118">This screen will be primarily used by the data steward to perform a high-level monitoring of all the activities performed on the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] that the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application is connected to.</span></span> <span data-ttu-id="c7522-119">這個畫面不提供任何系統層級的監視。</span><span class="sxs-lookup"><span data-stu-id="c7522-119">This screen does not provide any system-level monitoring.</span></span> <span data-ttu-id="c7522-120">此外，這個畫面也可以讓 DQS 系統管理員透過終止正在執行的活動或停止活動中正在執行的程序 (如有需要)，控制某個活動或某個活動中的程序。</span><span class="sxs-lookup"><span data-stu-id="c7522-120">Additionally, this screen also enables the DQS administrators to control an activity or a process within an activity by terminating a running activity or stopping a running process within an activity, if required.</span></span> <span data-ttu-id="c7522-121">系統會顯示知識探索、定義域管理、比對原則、清理、比對，以及 SQL Server Integration Services (SSIS) 式清理的資料。</span><span class="sxs-lookup"><span data-stu-id="c7522-121">The data is displayed for knowledge discovery, domain management, matching policy, cleansing, matching, and SQL Server Integration Services (SSIS)-based cleansing.</span></span>  
  
### <a name="configuration"></a><span data-ttu-id="c7522-122">組態</span><span class="sxs-lookup"><span data-stu-id="c7522-122">Configuration</span></span>  
 <span data-ttu-id="c7522-123">**中的** [組態] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 畫面可讓 DQS 系統管理員進行下列操作：</span><span class="sxs-lookup"><span data-stu-id="c7522-123">The **Configuration** screen in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] enables the DQS administrator to do the following things:</span></span>  
  
-   <span data-ttu-id="c7522-124">**參考資料**：設定參考資料服務提供者： Azure Marketplace 或直接參考資料服務提供者。</span><span class="sxs-lookup"><span data-stu-id="c7522-124">**Reference Data**: Configure reference data service providers: Azure Marketplace or direct reference data service providers.</span></span> <span data-ttu-id="c7522-125">設定參考資料服務提供者之後，您可以在知識庫中的定義域管理活動期間，對應具有參考資料的定義域/複合定義域，然後使用相同的知識庫，在資料品質專案中進行清理活動。</span><span class="sxs-lookup"><span data-stu-id="c7522-125">After you set up the reference data service providers, you can map a domain/composite domain with the reference data during domain management activity in a knowledge base, and then use the same knowledge base for the cleansing activity in a data quality project.</span></span> <span data-ttu-id="c7522-126">它也可讓您指定用來連線到網際網路的 proxy 設定，以使用 Azure Marketplace。</span><span class="sxs-lookup"><span data-stu-id="c7522-126">It also enables you to specify the proxy settings for connecting to the Internet to use Azure Marketplace.</span></span>  
  
-   <span data-ttu-id="c7522-127">**一般設定**：指定資料清理和資料比對的臨界值，以及是否在 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]中啟用分析所使用的通知。</span><span class="sxs-lookup"><span data-stu-id="c7522-127">**General Settings**: Specify the threshold values for data cleansing and data matching, and whether to enable notifications for profiling in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="c7522-128">這些臨界值是由 DQS 在資料品質專案中，於電腦輔助的清理和比對活動期間所使用。</span><span class="sxs-lookup"><span data-stu-id="c7522-128">These threshold values are used by DQS during the computer-assisted cleansing and matching activities in a data quality project.</span></span>  
  
-   <span data-ttu-id="c7522-129">**記錄設定**：DQS 中的記錄檔會記錄在 DQS 中執行的活動，因此在維護和疑難排解期間追蹤運作問題相當實用。</span><span class="sxs-lookup"><span data-stu-id="c7522-129">**Log Settings**: The log files in DQS record the activities performed in DQS, and are useful for tracking operational issues during maintenance and troubleshooting.</span></span> <span data-ttu-id="c7522-130">您可以篩選您要針對各種 DQS 功能 (定義域管理、知識探索、清理、比對以及 Reference Data Services) 記錄的訊息，也可以根據事件的嚴重性層級篩選 DQS 模組。</span><span class="sxs-lookup"><span data-stu-id="c7522-130">You can filter the messages that you want to be logged for various DQS features (domain management, knowledge discovery, cleansing, matching, and reference data services) and DQS modules based on the severity level of the events.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7522-131">**[組態]** 畫面僅適用於擁有 DQS_MAIN 資料庫之 dqs_administrator 角色的使用者。</span><span class="sxs-lookup"><span data-stu-id="c7522-131">The **Configuration** screen is available only for those users who have the dqs_administrator role on the DQS_MAIN database.</span></span>  
  
##  <a name="administration-activities-outside-of-data-quality-client"></a><a name="AdminOutsideClient"></a><span data-ttu-id="c7522-132">Data Quality Client 外部的管理活動</span><span class="sxs-lookup"><span data-stu-id="c7522-132">Administration Activities Outside of Data Quality Client</span></span>  
 <span data-ttu-id="c7522-133">在 Data Quality Client 外部執行的活動包括：</span><span class="sxs-lookup"><span data-stu-id="c7522-133">There activities are performed outside of Data Quality Client:</span></span>  
  
-   <span data-ttu-id="c7522-134">**備份和還原 DQS 資料庫**：DQS 資料庫的備份和還原與任何 SQL Server 資料庫的備份和還原相同，但有專屬於 DQS 的一些考量。</span><span class="sxs-lookup"><span data-stu-id="c7522-134">**Backup and Restore DQS Databases**: The backup and restore of DQS databases is same as backing up and restoring any SQL Server database with some considerations that are specific to DQS.</span></span>  
  
-   <span data-ttu-id="c7522-135">**卸離和附加 DQS 資料庫**：卸離和附加 DQS 資料庫的步驟與卸離和附加任何 SQL Server 資料庫相同，但有專屬於 DQS 的一些考量。</span><span class="sxs-lookup"><span data-stu-id="c7522-135">**Detach and Attach DQS Databases**: The steps to detach and attach DQS databases is same as detaching and attaching any SQL Server database with some considerations that are specific to DQS.</span></span>  
  
 <span data-ttu-id="c7522-136">如需詳細資訊，請參閱＜ [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c7522-136">For more information, see [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c7522-137">相關工作</span><span class="sxs-lookup"><span data-stu-id="c7522-137">Related Tasks</span></span>  
  
|<span data-ttu-id="c7522-138">工作描述</span><span class="sxs-lookup"><span data-stu-id="c7522-138">Task Description</span></span>|<span data-ttu-id="c7522-139">主題</span><span class="sxs-lookup"><span data-stu-id="c7522-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="c7522-140">描述如何監控 DQS 中的活動。</span><span class="sxs-lookup"><span data-stu-id="c7522-140">Describes how to monitor activities in DQS.</span></span>|[<span data-ttu-id="c7522-141">監控 DQS 活動</span><span class="sxs-lookup"><span data-stu-id="c7522-141">Monitor DQS Activities</span></span>](../../2014/data-quality-services/monitor-dqs-activities.md)|  
|<span data-ttu-id="c7522-142">描述如何在 DQS 中設定參考資料設定。</span><span class="sxs-lookup"><span data-stu-id="c7522-142">Describes how to configure reference data settings in DQS.</span></span>|[<span data-ttu-id="c7522-143">設定 DQS 使用參考資料</span><span class="sxs-lookup"><span data-stu-id="c7522-143">Configure DQS to Use Reference Data</span></span>](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|<span data-ttu-id="c7522-144">描述如何設定清理與比對活動的臨界值。</span><span class="sxs-lookup"><span data-stu-id="c7522-144">Describes how to configure threshold values for the cleansing and matching activities.</span></span>|[<span data-ttu-id="c7522-145">設定清理和比對的臨界值</span><span class="sxs-lookup"><span data-stu-id="c7522-145">Configure Threshold Values for Cleansing and Matching</span></span>](../../2014/data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)|  
|<span data-ttu-id="c7522-146">描述如何啟用或停用 DQS 中的通知。</span><span class="sxs-lookup"><span data-stu-id="c7522-146">Describes how to enable or disable notifications in DQS.</span></span>|[<span data-ttu-id="c7522-147">在 DQS 中啟用或停用分析通知</span><span class="sxs-lookup"><span data-stu-id="c7522-147">Enable or Disable Profiling Notifications in DQS</span></span>](../../2014/data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
|<span data-ttu-id="c7522-148">描述如何根據事件的嚴重性層級設定 DQS 記錄。</span><span class="sxs-lookup"><span data-stu-id="c7522-148">Describes how to configure DQS logging based on the severity level of the events.</span></span>|[<span data-ttu-id="c7522-149">為 DQS 記錄檔設定嚴重性層級</span><span class="sxs-lookup"><span data-stu-id="c7522-149">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|<span data-ttu-id="c7522-150">描述如何設定 DQS 記錄的進階設定。</span><span class="sxs-lookup"><span data-stu-id="c7522-150">Describes how to configure advanced settings for DQS logging.</span></span>|[<span data-ttu-id="c7522-151">設定 DQS 記錄檔的進階設定</span><span class="sxs-lookup"><span data-stu-id="c7522-151">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
|<span data-ttu-id="c7522-152">描述如何備份與還原 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7522-152">Describes how to back up and restore DQS databases.</span></span>|[<span data-ttu-id="c7522-153">備份及還原 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="c7522-153">Backing Up and Restoring DQS Databases</span></span>](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|<span data-ttu-id="c7522-154">描述如何卸離及附加 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7522-154">Describes how to detach and attach DQS databases.</span></span>|[<span data-ttu-id="c7522-155">卸離和附加 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="c7522-155">Detaching and Attaching DQS Databases</span></span>](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a><span data-ttu-id="c7522-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7522-156">See Also</span></span>  
 <span data-ttu-id="c7522-157">[DQS 中的參考資料服務](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span><span class="sxs-lookup"><span data-stu-id="c7522-157">[Reference Data Services in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md) </span></span>  
 <span data-ttu-id="c7522-158">[管理 DQS 記錄檔](../../2014/data-quality-services/manage-dqs-log-files.md) </span><span class="sxs-lookup"><span data-stu-id="c7522-158">[Manage DQS Log Files](../../2014/data-quality-services/manage-dqs-log-files.md) </span></span>  
 [<span data-ttu-id="c7522-159">管理 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="c7522-159">Manage DQS Databases</span></span>](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
