---
title: 記錄檔檢視器 F1 說明 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.errorlog.f1
helpviewer_keywords:
- Log File Viewer
ms.assetid: 2243845c-4880-4aa0-9ee8-0a97a128996b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6eadb4baa4a47202b40a9cde1eca896022f31d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594542"
---
# <a name="log-file-viewer-f1-help"></a><span data-ttu-id="87703-102">記錄檔檢視器 F1 說明</span><span class="sxs-lookup"><span data-stu-id="87703-102">Log File Viewer F1 Help</span></span>
  <span data-ttu-id="87703-103">記錄檔檢視器會顯示許多不同元件的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="87703-103">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="87703-104">當記錄檔檢視器開啟時，使用 **[選取記錄]** 窗格以選取您要顯示的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87703-104">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="87703-105">每個記錄檔都會顯示適用於該記錄檔類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="87703-105">Each log displays columns appropriate to that kind of log.</span></span>  
  
 <span data-ttu-id="87703-106">可用的記錄檔取決於記錄檔檢視器的開啟方式而定。</span><span class="sxs-lookup"><span data-stu-id="87703-106">The logs that are available depend on how Log File Viewer is opened.</span></span> <span data-ttu-id="87703-107">如需詳細資訊，請參閱 [開啟記錄檔檢視器](open-log-file-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="87703-107">For more information, see [Open Log File Viewer](open-log-file-viewer.md).</span></span>  
  
 <span data-ttu-id="87703-108">您可以在 [工具/選項] 對話方塊的 [SQL Server 物件總管/命令] 頁面中，設定要顯示的稽核記錄檔資料列數目。</span><span class="sxs-lookup"><span data-stu-id="87703-108">The number of rows that are displayed for audit logs can be configured on the **SQL Server Object Explorer/Commands** page of the **Tools/Options** dialog box.</span></span> <span data-ttu-id="87703-109">如需稽核記錄檔顯示之資料行的描述，請參閱 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="87703-109">For descriptions of the columns that are displayed for audit logs, see [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="87703-110">選項。</span><span class="sxs-lookup"><span data-stu-id="87703-110">Options</span></span>  
 <span data-ttu-id="87703-111">**載入記錄**</span><span class="sxs-lookup"><span data-stu-id="87703-111">**Load Log**</span></span>  
 <span data-ttu-id="87703-112">開啟對話方塊供您指定所要載入的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87703-112">Open a dialog box where you can specify a log file to load.</span></span>  
  
 <span data-ttu-id="87703-113">**匯出**</span><span class="sxs-lookup"><span data-stu-id="87703-113">**Export**</span></span>  
 <span data-ttu-id="87703-114">開啟對話方塊，以讓您將 [記錄檔摘要] 格線中所顯示的資訊匯出至文字檔。</span><span class="sxs-lookup"><span data-stu-id="87703-114">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
 <span data-ttu-id="87703-115">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="87703-115">**Refresh**</span></span>  
 <span data-ttu-id="87703-116">重新整理所選取之記錄檔的檢視。</span><span class="sxs-lookup"><span data-stu-id="87703-116">Refresh the view of the selected logs.</span></span> <span data-ttu-id="87703-117">當套用任何篩選設定時， **[重新整理]** 按鈕會從目標伺服器重新讀取選取的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="87703-117">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
 <span data-ttu-id="87703-118">**Filter**</span><span class="sxs-lookup"><span data-stu-id="87703-118">**Filter**</span></span>  
 <span data-ttu-id="87703-119">開啟對話方塊，以讓您指定用來篩選記錄檔的設定，例如 [連接]、[日期] 或其他的 [一般] 篩選準則。</span><span class="sxs-lookup"><span data-stu-id="87703-119">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
 <span data-ttu-id="87703-120">**搜尋**</span><span class="sxs-lookup"><span data-stu-id="87703-120">**Search**</span></span>  
 <span data-ttu-id="87703-121">搜尋記錄檔中的特定文字。</span><span class="sxs-lookup"><span data-stu-id="87703-121">Search the log file for specific text.</span></span> <span data-ttu-id="87703-122">不支援使用萬用字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="87703-122">Searching with wildcard characters is not supported.</span></span>  
  
 <span data-ttu-id="87703-123">**停止**</span><span class="sxs-lookup"><span data-stu-id="87703-123">**Stop**</span></span>  
 <span data-ttu-id="87703-124">停止載入記錄檔項目。</span><span class="sxs-lookup"><span data-stu-id="87703-124">Stops loading the log file entries.</span></span> <span data-ttu-id="87703-125">例如，如果遠端或離線記錄檔需要長時間才能載入，而您只要檢視最新項目時，就可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="87703-125">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
 <span data-ttu-id="87703-126">**記錄檔摘要**</span><span class="sxs-lookup"><span data-stu-id="87703-126">**Log file summary**</span></span>  
 <span data-ttu-id="87703-127">此資訊面板會顯示記錄檔篩選的摘要。</span><span class="sxs-lookup"><span data-stu-id="87703-127">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="87703-128">如果未篩選檔案，則會看到下列文字： **[未套用篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="87703-128">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="87703-129">若篩選已套用到記錄，則會看到下列文字：**篩選記錄項目的準則：\<filter criteria>** 。</span><span class="sxs-lookup"><span data-stu-id="87703-129">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
 <span data-ttu-id="87703-130">**選取的資料列詳細資料**</span><span class="sxs-lookup"><span data-stu-id="87703-130">**Selected row details**</span></span>  
 <span data-ttu-id="87703-131">選取資料列以顯示頁面下方有關選取之事件資料列的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="87703-131">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="87703-132">將資料行拖曳至方格中的新位置，以重新排序資料行。</span><span class="sxs-lookup"><span data-stu-id="87703-132">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="87703-133">將方格標頭中的資料行分隔線拖曳至左邊或右邊，以調整資料行大小。</span><span class="sxs-lookup"><span data-stu-id="87703-133">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="87703-134">在方格標頭中按兩下資料行分隔線，自動將資料行大小調整為內容寬度。</span><span class="sxs-lookup"><span data-stu-id="87703-134">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
 <span data-ttu-id="87703-135">**執行個體**</span><span class="sxs-lookup"><span data-stu-id="87703-135">**Instance**</span></span>  
 <span data-ttu-id="87703-136">發生事件之執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="87703-136">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="87703-137">顯示為 *&lt;電腦名稱*\\*執行個體名稱&gt;* 。</span><span class="sxs-lookup"><span data-stu-id="87703-137">This is displayed as *computer name*\\*instance name*.</span></span>  
  
## <a name="frequently-displayed-columns"></a><span data-ttu-id="87703-138">經常顯示的資料行</span><span class="sxs-lookup"><span data-stu-id="87703-138">Frequently Displayed Columns</span></span>  
 <span data-ttu-id="87703-139">**日期**</span><span class="sxs-lookup"><span data-stu-id="87703-139">**Date**</span></span>  
 <span data-ttu-id="87703-140">顯示事件的日期。</span><span class="sxs-lookup"><span data-stu-id="87703-140">Displays the date of the event.</span></span>  
  
 <span data-ttu-id="87703-141">**Source**</span><span class="sxs-lookup"><span data-stu-id="87703-141">**Source**</span></span>  
 <span data-ttu-id="87703-142">顯示事件建立的來源功能，例如服務名稱 (如 MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="87703-142">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="87703-143">不是所有記錄檔類型都會出現來源。</span><span class="sxs-lookup"><span data-stu-id="87703-143">This does not appear for all log types.</span></span>  
  
 <span data-ttu-id="87703-144">**訊息**</span><span class="sxs-lookup"><span data-stu-id="87703-144">**Message**</span></span>  
 <span data-ttu-id="87703-145">顯示與事件相關聯的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="87703-145">Displays any messages associated with the event.</span></span>  
  
 <span data-ttu-id="87703-146">**記錄類型**</span><span class="sxs-lookup"><span data-stu-id="87703-146">**Log Type**</span></span>  
 <span data-ttu-id="87703-147">顯示事件所屬之記錄檔的類型。</span><span class="sxs-lookup"><span data-stu-id="87703-147">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="87703-148">所有選取的記錄檔都會出現在記錄檔摘要視窗中。</span><span class="sxs-lookup"><span data-stu-id="87703-148">All selected logs appear in the log file summary window.</span></span>  
  
 <span data-ttu-id="87703-149">**記錄來源**</span><span class="sxs-lookup"><span data-stu-id="87703-149">**Log Source**</span></span>  
 <span data-ttu-id="87703-150">顯示擷取事件之來源記錄的描述。</span><span class="sxs-lookup"><span data-stu-id="87703-150">Displays a description of the source log in which the event is captured.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="87703-151">權限</span><span class="sxs-lookup"><span data-stu-id="87703-151">Permissions</span></span>  
 <span data-ttu-id="87703-152">若要存取線上 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的記錄檔，需要 securityadmin 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="87703-152">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="87703-153">若要存取離線 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的記錄檔，您必須具有 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 命名空間以及儲存記錄檔之資料夾的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="87703-153">To access log files for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="87703-154">如需詳細資訊，請參閱 [檢視離線記錄檔](view-offline-log-files.md)主題中的＜安全性＞一節。</span><span class="sxs-lookup"><span data-stu-id="87703-154">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87703-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87703-155">See Also</span></span>  
 <span data-ttu-id="87703-156">[記錄檔檢視器](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="87703-156">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="87703-157">[開啟記錄檔檢視器](open-log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="87703-157">[Open Log File Viewer](open-log-file-viewer.md) </span></span>  
 [<span data-ttu-id="87703-158">檢視離線記錄檔</span><span class="sxs-lookup"><span data-stu-id="87703-158">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
