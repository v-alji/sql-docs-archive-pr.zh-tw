---
title: 檢視 SQL Server Agent 錯誤記錄檔 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], SQL Server Agent
- viewing SQL Server Agent error logs
- displaying SQL Server Agent error logs
- SQL Server Agent, errors
- errors [SQL Server Agent]
ms.assetid: de920425-fa44-469f-b83d-49e3f97e97f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: b88214a158a970a754c5f313bde3d53f2652ae73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703733"
---
# <a name="view-sql-server-agent-error-log-sql-server-management-studio"></a><span data-ttu-id="0c0aa-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0c0aa-102">View SQL Server Agent Error Log (SQL Server Management Studio)</span></span>
  <span data-ttu-id="0c0aa-103">此主題描述如何使用  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-103">This topic describes how to view the  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="0c0aa-104">記錄檔檢視器會顯示許多不同元件的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-104">Log File Viewer displays log information from many different components.</span></span> <span data-ttu-id="0c0aa-105">當記錄檔檢視器開啟時，使用 **[選取記錄]** 窗格以選取您要顯示的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-105">When Log File Viewer is open, use the **Select logs** pane to select the logs you want to display.</span></span> <span data-ttu-id="0c0aa-106">每個記錄檔都會顯示適用於該記錄檔類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-106">Each log displays columns appropriate to that kind of log.</span></span> <span data-ttu-id="0c0aa-107">可用的記錄檔取決於記錄檔檢視器的開啟方式而定。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-107">The logs that are available depend on how Log File Viewer is opened.</span></span>  
  
 <span data-ttu-id="0c0aa-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="0c0aa-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="0c0aa-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="0c0aa-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="0c0aa-111">安全性</span><span class="sxs-lookup"><span data-stu-id="0c0aa-111">Security</span></span>](#Security)  
  
-   [<span data-ttu-id="0c0aa-112">若要使用 SQL Server Management Studio 檢視 SQL Server Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="0c0aa-112">To view the SQL Server Agent error log, using SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="0c0aa-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="0c0aa-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="0c0aa-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="0c0aa-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="0c0aa-115">只有當您擁有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 節點的權限時，[物件總管] 才會顯示該節點。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-115">Object Explorer only displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent node if you have permission to use it.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="0c0aa-116">Security</span><span class="sxs-lookup"><span data-stu-id="0c0aa-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="0c0aa-117">權限</span><span class="sxs-lookup"><span data-stu-id="0c0aa-117">Permissions</span></span>  
 <span data-ttu-id="0c0aa-118">若要執行功能，您必須將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定為使用帳戶認證，此帳戶必須是 **中** sysadmin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-118">To perform its functions, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent must be configured to use the credentials of an account that is a member of the **sysadmin** fixed server role in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0c0aa-119">此帳戶必須擁有下列 Windows 權限：</span><span class="sxs-lookup"><span data-stu-id="0c0aa-119">The account must have the following Windows permissions:</span></span>  
  
-   <span data-ttu-id="0c0aa-120">以服務登入 (SeServiceLogonRight)</span><span class="sxs-lookup"><span data-stu-id="0c0aa-120">Log on as a service (SeServiceLogonRight)</span></span>  
  
-   <span data-ttu-id="0c0aa-121">取代處理序層級 Token (SeAssignPrimaryTokenPrivilege)</span><span class="sxs-lookup"><span data-stu-id="0c0aa-121">Replace a process-level token (SeAssignPrimaryTokenPrivilege)</span></span>  
  
-   <span data-ttu-id="0c0aa-122">略過跨越檢查 (SeChangeNotifyPrivilege)</span><span class="sxs-lookup"><span data-stu-id="0c0aa-122">Bypass traverse checking (SeChangeNotifyPrivilege)</span></span>  
  
-   <span data-ttu-id="0c0aa-123">調整處理序的記憶體配額 (SeIncreaseQuotaPrivilege)</span><span class="sxs-lookup"><span data-stu-id="0c0aa-123">Adjust memory quotas for a process (SeIncreaseQuotaPrivilege)</span></span>  
  
 <span data-ttu-id="0c0aa-124">如需 Agent 服務帳戶所需之 Windows 許可權的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[選取 SQL Server Agent 服務的帳戶](select-an-account-for-the-sql-server-agent-service.md)和[設定 Windows 服務帳戶與許可權](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-124">For more information about the Windows permissions required for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md) and [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="0c0aa-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="0c0aa-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-ssnoversion-agent-error-log"></a><span data-ttu-id="0c0aa-126">若要檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="0c0aa-126">To view the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log</span></span>  
  
1.  <span data-ttu-id="0c0aa-127">在 **[物件總管]** 中，按一下加號展開伺服器，此伺服器包含要檢視的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-127">In **Object Explorer**, click the plus sign to expand the server that contains the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error log that you want to view.</span></span>  
  
2.  <span data-ttu-id="0c0aa-128">按一下加號展開 **[SQL Server Agent]**。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-128">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="0c0aa-129">按一下加號展開 **[錯誤記錄檔]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-129">Click the plus sign to expand the **Error Logs** folder.</span></span>  
  
4.  <span data-ttu-id="0c0aa-130">以滑鼠右鍵按一下要檢視的錯誤記錄檔，然後選取 [檢視代理程式記錄]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-130">Right-click the error log you want to view and select **View Agent Log**.</span></span>  
  
     <span data-ttu-id="0c0aa-131">[**記錄檔檢視器-**_server_name_ ] 對話方塊中有下列選項：</span><span class="sxs-lookup"><span data-stu-id="0c0aa-131">The following options are available in the **Log File Viewer -**_server_name_ dialog box:</span></span>  
  
     <span data-ttu-id="0c0aa-132">**載入記錄**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-132">**Load Log**</span></span>  
     <span data-ttu-id="0c0aa-133">開啟對話方塊供您指定所要載入的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-133">Open a dialog box where you can specify a log file to load.</span></span>  
  
     <span data-ttu-id="0c0aa-134">**匯出**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-134">**Export**</span></span>  
     <span data-ttu-id="0c0aa-135">開啟對話方塊，以讓您將 [記錄檔摘要] 格線中所顯示的資訊匯出至文字檔。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-135">Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.</span></span>  
  
     <span data-ttu-id="0c0aa-136">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-136">**Refresh**</span></span>  
     <span data-ttu-id="0c0aa-137">重新整理所選取之記錄檔的檢視。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-137">Refresh the view of the selected logs.</span></span> <span data-ttu-id="0c0aa-138">當套用任何篩選設定時， **[重新整理]** 按鈕會從目標伺服器重新讀取選取的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-138">The **Refresh** button rereads the selected logs from the target server while applying any filter settings.</span></span>  
  
     <span data-ttu-id="0c0aa-139">**Filter**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-139">**Filter**</span></span>  
     <span data-ttu-id="0c0aa-140">開啟對話方塊，以讓您指定用來篩選記錄檔的設定，例如 [連接]、[日期] 或其他的 [一般] 篩選準則。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-140">Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.</span></span>  
  
     <span data-ttu-id="0c0aa-141">**搜尋**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-141">**Search**</span></span>  
     <span data-ttu-id="0c0aa-142">搜尋記錄檔中的特定文字。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-142">Search the log file for specific text.</span></span> <span data-ttu-id="0c0aa-143">不支援使用萬用字元搜尋。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-143">Searching with wildcard characters is not supported.</span></span>  
  
     <span data-ttu-id="0c0aa-144">**停止**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-144">**Stop**</span></span>  
     <span data-ttu-id="0c0aa-145">停止載入記錄檔項目。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-145">Stops loading the log file entries.</span></span> <span data-ttu-id="0c0aa-146">例如，如果遠端或離線記錄檔需要長時間才能載入，而您只要檢視最新項目時，就可以使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-146">For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.</span></span>  
  
     <span data-ttu-id="0c0aa-147">**記錄檔摘要**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-147">**Log file summary**</span></span>  
     <span data-ttu-id="0c0aa-148">此資訊面板會顯示記錄檔篩選的摘要。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-148">This information panel displays a summary of the log file filtering.</span></span> <span data-ttu-id="0c0aa-149">如果未篩選檔案，則會看到下列文字： **[未套用篩選]** 。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-149">If the file is not filtered, you will see the following text, **No filter applied**.</span></span> <span data-ttu-id="0c0aa-150">若篩選已套用到記錄，則會看到下列文字：**篩選記錄項目的準則：\<filter criteria>** 。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-150">If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.</span></span>  
  
     <span data-ttu-id="0c0aa-151">**選取的資料列詳細資料**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-151">**Selected row details**</span></span>  
     <span data-ttu-id="0c0aa-152">選取資料列以顯示頁面下方有關選取之事件資料列的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-152">Select a row to display additional details about the selected event row at the bottom of the page.</span></span> <span data-ttu-id="0c0aa-153">將資料行拖曳至方格中的新位置，以重新排序資料行。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-153">The columns can be reordered by dragging them to new locations in the grid.</span></span> <span data-ttu-id="0c0aa-154">將方格標頭中的資料行分隔線拖曳至左邊或右邊，以調整資料行大小。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-154">The columns can be resized by dragging the column separator bars in the grid header to the left or right.</span></span> <span data-ttu-id="0c0aa-155">在方格標頭中按兩下資料行分隔線，自動將資料行大小調整為內容寬度。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-155">Double-click the column separator bars in the grid header to automatically size the column to the content width.</span></span>  
  
     <span data-ttu-id="0c0aa-156">**執行個體**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-156">**Instance**</span></span>  
     <span data-ttu-id="0c0aa-157">發生事件之執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-157">The name of the instance on which the event occurred.</span></span> <span data-ttu-id="0c0aa-158">顯示為 *&lt;電腦名稱*\\*執行個體名稱&gt;* 。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-158">This is displayed as *computer name*\\*instance name*.</span></span>  
  
     <span data-ttu-id="0c0aa-159">**日期**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-159">**Date**</span></span>  
     <span data-ttu-id="0c0aa-160">顯示事件的日期。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-160">Displays the date of the event.</span></span>  
  
     <span data-ttu-id="0c0aa-161">**Source**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-161">**Source**</span></span>  
     <span data-ttu-id="0c0aa-162">顯示事件建立的來源功能，例如服務名稱 (如 MSSQLSERVER)。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-162">Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example).</span></span> <span data-ttu-id="0c0aa-163">不是所有記錄檔類型都會出現來源。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-163">This does not appear for all log types.</span></span>  
  
     <span data-ttu-id="0c0aa-164">**訊息**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-164">**Message**</span></span>  
     <span data-ttu-id="0c0aa-165">顯示與事件相關聯的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-165">Displays any messages associated with the event.</span></span>  
  
     <span data-ttu-id="0c0aa-166">**記錄類型**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-166">**Log Type**</span></span>  
     <span data-ttu-id="0c0aa-167">顯示事件所屬之記錄檔的類型。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-167">Displays the type of log to which the event belongs.</span></span> <span data-ttu-id="0c0aa-168">所有選取的記錄檔都會出現在記錄檔摘要視窗中。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-168">All selected logs appear in the log file summary window.</span></span>  
  
     <span data-ttu-id="0c0aa-169">**記錄來源**</span><span class="sxs-lookup"><span data-stu-id="0c0aa-169">**Log Source**</span></span>  
     <span data-ttu-id="0c0aa-170">顯示擷取事件之來源記錄的描述。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-170">Displays a description of the source log in which the event is captured.</span></span>  
  
5.  <span data-ttu-id="0c0aa-171">完成後，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="0c0aa-171">When finished, click **Close**.</span></span>  
  
  
