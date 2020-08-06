---
title: 開啟記錄檔檢視器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269ff10275f7463a8a85249a2a0f06fe9bde364a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594535"
---
# <a name="open-log-file-viewer"></a><span data-ttu-id="90c20-102">開啟記錄檔檢視器</span><span class="sxs-lookup"><span data-stu-id="90c20-102">Open Log File Viewer</span></span>
  <span data-ttu-id="90c20-103">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用記錄檔檢視器，以存取下列記錄中所擷取之錯誤和事件的相關資訊：</span><span class="sxs-lookup"><span data-stu-id="90c20-103">You can use Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to access information about errors and events that are captured in the following logs:</span></span>  
  
-   <span data-ttu-id="90c20-104">稽核集合</span><span class="sxs-lookup"><span data-stu-id="90c20-104">Audit Collection</span></span>  
  
-   <span data-ttu-id="90c20-105">資料收集</span><span class="sxs-lookup"><span data-stu-id="90c20-105">Data Collection</span></span>  
  
-   <span data-ttu-id="90c20-106">Database Mail</span><span class="sxs-lookup"><span data-stu-id="90c20-106">Database Mail</span></span>  
  
-   <span data-ttu-id="90c20-107">作業記錄</span><span class="sxs-lookup"><span data-stu-id="90c20-107">Job History</span></span>  
  
-   <span data-ttu-id="90c20-108">SQL Server</span><span class="sxs-lookup"><span data-stu-id="90c20-108">SQL Server</span></span>  
  
-   <span data-ttu-id="90c20-109">SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="90c20-109">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="90c20-110">Windows 事件 (這些 Windows 事件也可以從事件檢視器存取)。</span><span class="sxs-lookup"><span data-stu-id="90c20-110">Windows events (These Windows events can also be accessed from Event Viewer.)</span></span>  
  
 <span data-ttu-id="90c20-111">從 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]開始，您就可以使用 [已註冊的伺服器] 來檢視本機或遠端 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]記錄檔。</span><span class="sxs-lookup"><span data-stu-id="90c20-111">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can use Registered Servers to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from local or remote instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="90c20-112">當這些執行個體在線上或離線時，您可以使用 [已註冊的伺服器] 來檢視記錄檔。</span><span class="sxs-lookup"><span data-stu-id="90c20-112">By using Registered Servers, you can view the log files when the instances are either online or offline.</span></span> <span data-ttu-id="90c20-113">如需線上存取的詳細資訊，請參閱本主題稍後的＜從已註冊的伺服器檢視線上記錄檔＞程序。</span><span class="sxs-lookup"><span data-stu-id="90c20-113">For more information about online access, see the procedure "To view online log files from Registered Servers" later in this topic.</span></span> <span data-ttu-id="90c20-114">如需如何存取離線 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄檔的詳細資訊，請參閱 [檢視離線記錄檔](view-offline-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="90c20-114">For more information about how to access offline [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files, see [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
 <span data-ttu-id="90c20-115">您可以用許多方式來開啟記錄檔檢視器，端視想要檢視的資訊而定。</span><span class="sxs-lookup"><span data-stu-id="90c20-115">You can open Log File Viewer in several ways, depending on the information that you want to view.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="90c20-116">權限</span><span class="sxs-lookup"><span data-stu-id="90c20-116">Permissions</span></span>  
 <span data-ttu-id="90c20-117">若要存取線上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的記錄檔，需要 securityadmin 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="90c20-117">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="90c20-118">若要存取離線 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的記錄檔，您必須具有 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空間以及儲存記錄檔之資料夾的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="90c20-118">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="90c20-119">如需詳細資訊，請參閱 [檢視離線記錄檔](view-offline-log-files.md)主題中的＜安全性＞一節。</span><span class="sxs-lookup"><span data-stu-id="90c20-119">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
### <a name="security"></a><span data-ttu-id="90c20-120">安全性</span><span class="sxs-lookup"><span data-stu-id="90c20-120">Security</span></span>  
 <span data-ttu-id="90c20-121">需要 securityadmin 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="90c20-121">Requires membership in the securityadmin fixed server role.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="90c20-122">檢視記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-122">View Log Files</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a><span data-ttu-id="90c20-123">若要檢視與一般 SQL Server 活動相關的記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-123">To view logs that are related to general SQL Server activity</span></span>  
  
1.  <span data-ttu-id="90c20-124">在物件總管中，展開 [管理]。</span><span class="sxs-lookup"><span data-stu-id="90c20-124">In Object Explorer, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="90c20-125">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="90c20-125">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="90c20-126">以滑鼠右鍵按一下 [SQL Server 記錄檔]，指向 [檢視]，然後按一下 [SQL Server 記錄檔] 或 [SQL Server 與 Windows 記錄檔]。</span><span class="sxs-lookup"><span data-stu-id="90c20-126">Right-click **SQL Server Logs**, point to **View**, and then click either **SQL Server Log** or **SQL Server and Windows Log**.</span></span>  
  
    -   <span data-ttu-id="90c20-127">展開 [SQL Server 記錄檔]，以滑鼠右鍵按一下任何記錄檔，然後按一下 [檢視 SQL Server 記錄檔]。</span><span class="sxs-lookup"><span data-stu-id="90c20-127">Expand **SQL Server Logs**, right-click any log file, and then click **View SQL Server Log**.</span></span> <span data-ttu-id="90c20-128">您也可以按兩下任何記錄檔。</span><span class="sxs-lookup"><span data-stu-id="90c20-128">You can also double-click any log file.</span></span>  
  
     <span data-ttu-id="90c20-129">這些記錄檔包含 [Database Mail]、[SQL Server]、[SQL Server Agent] 和 [Windows NT]。</span><span class="sxs-lookup"><span data-stu-id="90c20-129">The logs include **Database Mail**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a><span data-ttu-id="90c20-130">若要檢視與作業相關的記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-130">To view logs that are related to jobs</span></span>  
  
-   <span data-ttu-id="90c20-131">在物件總管中，展開 [SQL Server Agent]，以滑鼠右鍵按一下 [作業]，然後按一下 [檢視記錄]。</span><span class="sxs-lookup"><span data-stu-id="90c20-131">In Object Explorer, expand **SQL Server Agent**, right-click **Jobs**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="90c20-132">這些記錄檔包含 [Database Mail]、[作業記錄] 和 [SQL Server Agent]。</span><span class="sxs-lookup"><span data-stu-id="90c20-132">The logs include **Database Mail**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a><span data-ttu-id="90c20-133">若要檢視與維護計畫相關的記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-133">To view logs that are related to maintenance plans</span></span>  
  
-   <span data-ttu-id="90c20-134">在物件總管中，展開 [管理]，以滑鼠右鍵按一下 [維護計畫]，然後按一下 [檢視記錄]。</span><span class="sxs-lookup"><span data-stu-id="90c20-134">In Object Explorer, expand **Management**, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="90c20-135">這些記錄檔包含 [Database Mail]、[作業記錄]、[維護計畫]、[遠端維護計畫] 和 [SQL Server Agent]。</span><span class="sxs-lookup"><span data-stu-id="90c20-135">The logs include **Database Mail**, **Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a><span data-ttu-id="90c20-136">若要檢視與資料收集相關的記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-136">To view logs that are related to Data Collection</span></span>  
  
-   <span data-ttu-id="90c20-137">在物件總管中，展開 [管理]，以滑鼠右鍵按一下 [資料收集]，然後按一下 [檢視記錄]。</span><span class="sxs-lookup"><span data-stu-id="90c20-137">In Object Explorer, expand **Management**, right-click **Data Collection**, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="90c20-138">這些記錄檔包含 [資料收集]、[作業記錄] 和 [SQL Server Agent]。</span><span class="sxs-lookup"><span data-stu-id="90c20-138">The logs include **Data Collection**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a><span data-ttu-id="90c20-139">若要檢視與 Database Mail 相關的記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-139">To view logs that are related to Database Mail</span></span>  
  
-   <span data-ttu-id="90c20-140">在物件總管中，展開 [管理]，以滑鼠右鍵按一下 [Database Mail]，然後按一下 [檢視 Database Mail 記錄]。</span><span class="sxs-lookup"><span data-stu-id="90c20-140">In Object Explorer, expand **Management**, right-click **Database Mail**, and then click **View Database Mail Log**.</span></span>  
  
     <span data-ttu-id="90c20-141">這些記錄檔包含 [Database Mail]、[作業記錄]、[維護計畫]、[遠端維護計畫]、[SQL Server]、[SQL Server Agent] 和 [Windows NT]。</span><span class="sxs-lookup"><span data-stu-id="90c20-141">The logs include **Database Mail, Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="90c20-142">若要檢視與稽核收集相關的記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-142">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="90c20-143">在物件總管中，依序展開 [安全性] 和 [稽核]，以滑鼠右鍵按一下稽核，然後按一下 [檢視稽核記錄]。</span><span class="sxs-lookup"><span data-stu-id="90c20-143">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="90c20-144">這些記錄檔包含 [稽核收集] 和 [Windows NT]。</span><span class="sxs-lookup"><span data-stu-id="90c20-144">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="90c20-145">若要檢視與稽核收集相關的記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-145">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="90c20-146">在物件總管中，依序展開 [安全性] 和 [稽核]，以滑鼠右鍵按一下稽核，然後按一下 [檢視稽核記錄]。</span><span class="sxs-lookup"><span data-stu-id="90c20-146">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="90c20-147">這些記錄檔包含 [稽核收集] 和 [Windows NT]。</span><span class="sxs-lookup"><span data-stu-id="90c20-147">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c20-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90c20-148">See Also</span></span>  
 <span data-ttu-id="90c20-149">[記錄檔檢視器](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="90c20-149">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="90c20-150">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="90c20-150">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="90c20-151">檢視離線記錄檔</span><span class="sxs-lookup"><span data-stu-id="90c20-151">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
