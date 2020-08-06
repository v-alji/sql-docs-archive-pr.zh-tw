---
title: 管理 DQS 記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- logging
- log files
- dqs log files
ms.assetid: 4fccfd24-aede-4882-be69-ec1e82682e16
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ca85772b8cc8aca41b75ad05d028bc444f280378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599684"
---
# <a name="manage-dqs-log-files"></a><span data-ttu-id="38947-102">管理 DQS 記錄檔</span><span class="sxs-lookup"><span data-stu-id="38947-102">Manage DQS Log Files</span></span>
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] <span data-ttu-id="38947-103">(DQS) 記錄檔可幫助您診斷及排除 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]和 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]的疑難問題。</span><span class="sxs-lookup"><span data-stu-id="38947-103">(DQS) log files help you in diagnosing and troubleshooting issue with [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="38947-104">系統會針對 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]和 [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]產生個別記錄檔。</span><span class="sxs-lookup"><span data-stu-id="38947-104">Separate log files are generated for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
 <span data-ttu-id="38947-105">您可以使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 來設定 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 功能和模組的記錄嚴重性設定。</span><span class="sxs-lookup"><span data-stu-id="38947-105">You can use [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] to configure the log severity setting for [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] features and modules.</span></span> <span data-ttu-id="38947-106">此外，您也可以針對 DQS 記錄檔設定一些其他 (進階) 設定，方法是手動變更 DQS_MAIN 資料庫中的 DQS 記錄組態設定及 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 電腦上的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="38947-106">Additionally, you can also configure some other (advanced) settings for the DQS log files by manually changing the DQS log configuration settings in the DQS_MAIN database and an XML file on the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] computer.</span></span>  
  
##  <a name="data-quality-server-log-file"></a><a name="DQSServer"></a><span data-ttu-id="38947-107">資料品質伺服器記錄檔</span><span class="sxs-lookup"><span data-stu-id="38947-107">Data Quality Server Log File</span></span>  
 <span data-ttu-id="38947-108">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄檔 DQServerLog.DQS_MAIN.log 包含在 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]上執行之活動的記錄。</span><span class="sxs-lookup"><span data-stu-id="38947-108">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, DQServerLog.DQS_MAIN.log, includes logs of activities that are run on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="38947-109">您如果安裝了 SQL Server 的預設執行個體，DQServerLog.DQS_MAIN.log 檔案將會位於 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log。</span><span class="sxs-lookup"><span data-stu-id="38947-109">If you installed the default instance of SQL Server, the DQServerLog.DQS_MAIN.log file is available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log.</span></span> <span data-ttu-id="38947-110">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄檔包含以下資訊片段，每個片段都以直立線符號 (|) 分隔：</span><span class="sxs-lookup"><span data-stu-id="38947-110">The [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file contains the following pieces of information, each delimited by a pipe (|):</span></span>  
  
-   <span data-ttu-id="38947-111">日期和時間</span><span class="sxs-lookup"><span data-stu-id="38947-111">Date and time</span></span>  
  
-   <span data-ttu-id="38947-112">執行緒名稱</span><span class="sxs-lookup"><span data-stu-id="38947-112">Thread name</span></span>  
  
-   <span data-ttu-id="38947-113">執行緒識別碼</span><span class="sxs-lookup"><span data-stu-id="38947-113">Thread ID</span></span>  
  
-   <span data-ttu-id="38947-114">記錄嚴重性 (嚴重錯誤、錯誤、警告、資訊和偵錯)</span><span class="sxs-lookup"><span data-stu-id="38947-114">Log severity (FATAL, ERROR, WARN, INFO, and DEBUG)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="38947-115">偵錯記錄嚴重性與詳細資訊相同。</span><span class="sxs-lookup"><span data-stu-id="38947-115">The DEBUG logging severity is same as Verbose.</span></span>  
  
-   <span data-ttu-id="38947-116">UID (內部 DQS 基礎結構識別碼)</span><span class="sxs-lookup"><span data-stu-id="38947-116">UID (internal DQS infrastructure ID)</span></span>  
  
-   <span data-ttu-id="38947-117">命名空間</span><span class="sxs-lookup"><span data-stu-id="38947-117">Namespace</span></span>  
  
-   <span data-ttu-id="38947-118">類別和方法</span><span class="sxs-lookup"><span data-stu-id="38947-118">Class and method</span></span>  
  
-   <span data-ttu-id="38947-119">訊息</span><span class="sxs-lookup"><span data-stu-id="38947-119">Message</span></span>  
  
 <span data-ttu-id="38947-120">除了這些項目以外，記錄檔也會顯示有關應用程式版本、電腦名稱、使用者名稱和作業系統的資訊。</span><span class="sxs-lookup"><span data-stu-id="38947-120">Along with these, the log file also displays information about the application version, computer name, user name, and operating system.</span></span>  
  
 <span data-ttu-id="38947-121">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄檔中的範例項目如下所示：</span><span class="sxs-lookup"><span data-stu-id="38947-121">A sample entry in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file looks like the following:</span></span>  
  
```  
23-08-2013 01:45:29|[]|4|INFO|PUID|InfInfoModuleStarting|Microsoft.Ssdqs.Core.Startup.ServerInit|Starting DQS ServerInit: version [12.0.0.0], machine name [DQS-TEST], user name [NT Service\MSSQLSERVER], operating system [Microsoft Windows NT 6.1.7600.0]...  
```  
  
 <span data-ttu-id="38947-122">DQServerLog.DQS_MAIN.log 檔案是輪替檔案，而且只要現有記錄檔超出 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄組態設定中指定的輪替檔案大小上限時，就會建立新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="38947-122">The DQServerLog.DQS_MAIN.log file is a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log configuration settings.</span></span> <span data-ttu-id="38947-123">如需詳細資訊，請參閱＜ [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)＞。</span><span class="sxs-lookup"><span data-stu-id="38947-123">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="data-quality-client-log-file"></a><a name="DQSClient"></a><span data-ttu-id="38947-124">Data Quality Client 記錄檔</span><span class="sxs-lookup"><span data-stu-id="38947-124">Data Quality Client Log File</span></span>  
 <span data-ttu-id="38947-125">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄檔 DQClientLog.log 包含用戶端記錄。</span><span class="sxs-lookup"><span data-stu-id="38947-125">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file, DQClientLog.log, includes the client side logs.</span></span> <span data-ttu-id="38947-126">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄檔位於 %APPDATA%\SSDQS\Log。</span><span class="sxs-lookup"><span data-stu-id="38947-126">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="38947-127">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄檔包含與伺服器記錄檔類似的一組資訊，但適用於用戶端。</span><span class="sxs-lookup"><span data-stu-id="38947-127">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file contains similar set of information as in the server log file, but for the client side.</span></span>  
  
 <span data-ttu-id="38947-128">就像 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 記錄檔一樣， [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄檔也是輪替檔案，而且只要現有記錄檔超出 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 記錄組態設定中指定的輪替檔案大小上限時，就會建立新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="38947-128">As with the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] log file, the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log file is also a rolling file, and a new log file is created once the existing log file exceeds the rolling file size limit specified in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] log configuration settings.</span></span> <span data-ttu-id="38947-129">如需詳細資訊，請參閱＜ [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)＞。</span><span class="sxs-lookup"><span data-stu-id="38947-129">For more information, see [Configure Advanced Settings for DQS Log Files](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md).</span></span>  
  
##  <a name="dqs-cleansing-component-log-file"></a><a name="DQSCleansing"></a><span data-ttu-id="38947-130">DQS 清理元件記錄檔</span><span class="sxs-lookup"><span data-stu-id="38947-130">DQS Cleansing Component Log File</span></span>  
 <span data-ttu-id="38947-131">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 記錄檔 DQSSSISLog.log 包括使用 [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)]執行之活動的記錄。</span><span class="sxs-lookup"><span data-stu-id="38947-131">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file, DQSSSISLog.log, includes logs of activities performed using the [!INCLUDE[ssDQSCleansingLong](../includes/ssdqscleansinglong-md.md)].</span></span> <span data-ttu-id="38947-132">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 元件記錄檔位於 %APPDATA%\SSDQS\Log。</span><span class="sxs-lookup"><span data-stu-id="38947-132">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] component log file is available at %APPDATA%\SSDQS\Log.</span></span> <span data-ttu-id="38947-133">[!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] 記錄檔包含與伺服器記錄檔類似的一組資訊，但適用於 [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="38947-133">The [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)] log file contains similar set of information as in the server log file, but for the [!INCLUDE[ssDQSCleansing](../includes/ssdqscleansing-md.md)].</span></span>  
  
##  <a name="related-tasks"></a><a name="RT"></a> <span data-ttu-id="38947-134">相關工作</span><span class="sxs-lookup"><span data-stu-id="38947-134">Related Tasks</span></span>  
  
|<span data-ttu-id="38947-135">工作描述</span><span class="sxs-lookup"><span data-stu-id="38947-135">Task Description</span></span>|<span data-ttu-id="38947-136">主題</span><span class="sxs-lookup"><span data-stu-id="38947-136">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="38947-137">描述如何使用 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]來設定 DQS 記錄檔的記錄嚴重性設定。</span><span class="sxs-lookup"><span data-stu-id="38947-137">Describes how to configure log severity settings for DQS log files using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>|[<span data-ttu-id="38947-138">為 DQS 記錄檔設定嚴重性層級</span><span class="sxs-lookup"><span data-stu-id="38947-138">Configure Severity Levels for DQS Log Files</span></span>](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|<span data-ttu-id="38947-139">描述如何手動設定 DQS 記錄檔的進階設定。</span><span class="sxs-lookup"><span data-stu-id="38947-139">Describes how to manually configure advanced settings for DQS log files.</span></span>|[<span data-ttu-id="38947-140">設定 DQS 記錄檔的進階設定</span><span class="sxs-lookup"><span data-stu-id="38947-140">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
  
## <a name="see-also"></a><span data-ttu-id="38947-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38947-141">See Also</span></span>  
 [<span data-ttu-id="38947-142">dqs 管理</span><span class="sxs-lookup"><span data-stu-id="38947-142">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  
