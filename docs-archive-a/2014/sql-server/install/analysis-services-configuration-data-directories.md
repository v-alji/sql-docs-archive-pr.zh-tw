---
title: Analysis Services 設定-資料目錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
ms.openlocfilehash: e0711c6998e8f931e7d561bb388a0d7809733a44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595536"
---
# <a name="analysis-services-configuration---data-directories"></a><span data-ttu-id="bfb04-102">Analysis Services 組態 - 資料目錄</span><span class="sxs-lookup"><span data-stu-id="bfb04-102">Analysis Services Configuration - Data Directories</span></span>
  <span data-ttu-id="bfb04-103">下表的預設目錄可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間由使用者設定。</span><span class="sxs-lookup"><span data-stu-id="bfb04-103">The default directories in the following table are user-configurable during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="bfb04-104">存取這些檔案的許可權會授與本機系統管理員，以及在安裝期間建立及布建之 SQLServerMSASUser $ \<instance> 安全性群組的成員。</span><span class="sxs-lookup"><span data-stu-id="bfb04-104">Permission to access these files is granted to local administrators and to members of the SQLServerMSASUser$\<instance> security group that is created and provisioned during Setup.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="bfb04-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="bfb04-105">UI element list</span></span>  
  
|<span data-ttu-id="bfb04-106">描述</span><span class="sxs-lookup"><span data-stu-id="bfb04-106">Description</span></span>|<span data-ttu-id="bfb04-107">預設目錄</span><span class="sxs-lookup"><span data-stu-id="bfb04-107">Default directory</span></span>|<span data-ttu-id="bfb04-108">建議</span><span class="sxs-lookup"><span data-stu-id="bfb04-108">Recommendations</span></span>|  
|-----------------|-----------------------|---------------------|  
|<span data-ttu-id="bfb04-109">資料根目錄</span><span class="sxs-lookup"><span data-stu-id="bfb04-109">Data root directory</span></span>|<span data-ttu-id="bfb04-110">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\Msas13.< \olap\data \| 確保 \Program files\Microsoft SQL Server \ 資料夾受到有限許可權的保護。</span><span class="sxs-lookup"><span data-stu-id="bfb04-110">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Data\|Ensure that the \Program files\Microsoft SQL Server\ folder is protected with limited permissions.</span></span> <span data-ttu-id="bfb04-111">在許多組態中，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 效能取決於資料目錄所在之儲存體的效能。</span><span class="sxs-lookup"><span data-stu-id="bfb04-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] performance depends, in many configurations, on the performance of the storage on which the data directory is located.</span></span> <span data-ttu-id="bfb04-112">請將這個目錄放置於附加至系統的最高效能儲存體上。</span><span class="sxs-lookup"><span data-stu-id="bfb04-112">Place this directory on the highest performing storage that is attached to the system.</span></span> <span data-ttu-id="bfb04-113">若為容錯移轉叢集安裝，請確定資料目錄位於共用磁碟上。</span><span class="sxs-lookup"><span data-stu-id="bfb04-113">For failover cluster installations, ensure that data directories are placed on the shared disk.</span></span>|  
|<span data-ttu-id="bfb04-114">記錄檔目錄</span><span class="sxs-lookup"><span data-stu-id="bfb04-114">Log file directory</span></span>|<span data-ttu-id="bfb04-115">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\OLAP\Log \| 這是記錄檔的目錄 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，其中包含 FlightRecorder 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bfb04-115">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Log\|This is the directory for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] log files, and it includes the FlightRecorder log.</span></span> <span data-ttu-id="bfb04-116">如果您增加了飛行記錄器持續時間，請確定記錄檔目錄具有足夠的空間。</span><span class="sxs-lookup"><span data-stu-id="bfb04-116">If you increase the flight recorder duration, ensure that the log directory has adequate space.</span></span>|  
|<span data-ttu-id="bfb04-117">暫存目錄</span><span class="sxs-lookup"><span data-stu-id="bfb04-117">Temp directory</span></span>|<span data-ttu-id="bfb04-118">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\OLAP\Temp \| 將 Temp 目錄放在高效能儲存子系統上。</span><span class="sxs-lookup"><span data-stu-id="bfb04-118">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Temp\|Place the Temp directory on the high performance storage subsystem.</span></span>|  
|<span data-ttu-id="bfb04-119">備份目錄</span><span class="sxs-lookup"><span data-stu-id="bfb04-119">Backup directory</span></span>|<span data-ttu-id="bfb04-120">C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID>\OLAP\Backup \| 這是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 預設備份檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="bfb04-120">C:\Program Files\Microsoft SQL Server\MSAS12.\<InstanceID>\OLAP\Backup\|This is the directory for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] default backup files.</span></span> <span data-ttu-id="bfb04-121">對於 PowerPivot for SharePoint 安裝來說，這也是 PowerPivot 系統服務快取 PowerPivot 資料檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb04-121">For PowerPivot for SharePoint installations, it also where the PowerPivot System Services caches PowerPivot data files.</span></span><br /><br /> <span data-ttu-id="bfb04-122">請確定已設定適當的權限來防止資料遺失，並且確定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服務的使用者群組具有足夠的權限，可寫入備份目錄。</span><span class="sxs-lookup"><span data-stu-id="bfb04-122">Ensure appropriate permissions are set to prevent data loss, and that the user group for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service has adequate permissions to write to the backup directory.</span></span> <span data-ttu-id="bfb04-123">不支援針對備份目錄使用對應的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="bfb04-123">Using a mapped drive for backup directories is not supported.</span></span>|  
  
## <a name="notes"></a><span data-ttu-id="bfb04-124">注意</span><span class="sxs-lookup"><span data-stu-id="bfb04-124">Notes</span></span>  
  
-   <span data-ttu-id="bfb04-125">部署在 SharePoint 伺服陣列上的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體會將應用程式檔案、資料檔案和屬性儲存在內容資料庫與服務應用程式資料庫中。</span><span class="sxs-lookup"><span data-stu-id="bfb04-125">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instances that are deployed on a SharePoint farm store application files, data files, and properties in content databases and service application databases.</span></span>  
  
-   <span data-ttu-id="bfb04-126">將功能加入至現有的安裝時，您不能變更先前安裝之功能的位置，也不能指定新功能的位置。</span><span class="sxs-lookup"><span data-stu-id="bfb04-126">When you add features to an existing installation, you cannot change the location of a previously installed feature, nor can you specify the location for a new feature.</span></span>  
  
-   <span data-ttu-id="bfb04-127">如果您要指定非預設的安裝目錄，請確定安裝資料夾對於此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bfb04-127">If you specify non-default installation directories, ensure that the installation folders are unique to this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bfb04-128">此對話方塊上的任何目錄都不應該與其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中的目錄共用。</span><span class="sxs-lookup"><span data-stu-id="bfb04-128">None of the directories in this dialog box should be shared with directories from other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bfb04-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體內的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件也應該安裝在不同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bfb04-129">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components within an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should also be installed to separate directories.</span></span>  
  
-   <span data-ttu-id="bfb04-130">程式檔和資料檔案無法安裝在下列位置中：</span><span class="sxs-lookup"><span data-stu-id="bfb04-130">Program files and data files cannot be installed in the following situations:</span></span>  
  
    -   <span data-ttu-id="bfb04-131">抽取式磁碟機</span><span class="sxs-lookup"><span data-stu-id="bfb04-131">On a removable disk drive</span></span>  
  
    -   <span data-ttu-id="bfb04-132">使用壓縮的檔案系統</span><span class="sxs-lookup"><span data-stu-id="bfb04-132">On a file system that uses compression</span></span>  
  
    -   <span data-ttu-id="bfb04-133">系統檔案所在的目錄</span><span class="sxs-lookup"><span data-stu-id="bfb04-133">To a directory where system files are located</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb04-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfb04-134">See Also</span></span>  
 [<span data-ttu-id="bfb04-135">SQL Server 的預設和具名執行個體的檔案位置</span><span class="sxs-lookup"><span data-stu-id="bfb04-135">File Locations for Default and Named Instances of SQL Server</span></span>](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
