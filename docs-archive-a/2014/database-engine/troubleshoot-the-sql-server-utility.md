---
title: 針對 SQL Server 公用程式進行疑難排解 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3c139f9f084374aeb711e905ac0c315acc25c6ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704366"
---
# <a name="troubleshoot-the-sql-server-utility"></a><span data-ttu-id="86e73-102">疑難排解 SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="86e73-102">Troubleshoot the SQL Server Utility</span></span>
  <span data-ttu-id="86e73-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式問題的疑難排解可能包括解決 SQL Server 執行個體向 UCP 註冊作業失敗的問題、解決因無法收集資料而導致 UCP 上 Managed 執行個體清單檢視變為灰色圖示的問題、改善效能瓶頸或是解決資源健全狀況的問題。</span><span class="sxs-lookup"><span data-stu-id="86e73-103">Troubleshooting [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility issues might include resolving a failed operation to enroll an instance of SQL Server with a UCP, troubleshooting failed data collection resulting in gray icons in the managed instance list view on a UCP, mitigating performance bottlenecks, or resolving resource health issues.</span></span> <span data-ttu-id="86e73-104">如需有關減少 UCP 所識別之資源健康狀態問題的詳細資訊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱針對[SQL Server 資源健康狀態 &#40;SQL Server 公用程式&#41;進行疑難排解](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="86e73-104">For more information about mitigating resource health issues identified by a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, see [Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).</span></span>  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a><span data-ttu-id="86e73-105">SQL Server 執行個體向 SQL Server 公用程式註冊的作業失敗</span><span class="sxs-lookup"><span data-stu-id="86e73-105">Failed Operation to Enroll an Instance of SQL Server into a SQL Server Utility</span></span>  
 <span data-ttu-id="86e73-106">如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體進行註冊，並且指定隸屬不同於 UCP 所在位置的其他 Active Directory 網域的 Proxy 帳戶，那麼執行個體驗證會順利進行，但是註冊作業會失敗且出現下列錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="86e73-106">If you connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, and you specify a proxy account that belongs to a different Active Directory domain than the domain where the UCP is located, instance validation succeeds, but the enrollment operation fails with the following error message:</span></span>  
  
 <span data-ttu-id="86e73-107">執行 Transact-SQL 陳述式或批次時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86e73-107">An exception occurred while executing a Transact-SQL statement or batch.</span></span> <span data-ttu-id="86e73-108">(Microsoft.SqlServer.ConnectionInfo)</span><span class="sxs-lookup"><span data-stu-id="86e73-108">(Microsoft.SqlServer.ConnectionInfo)</span></span>  
  
 <span data-ttu-id="86e73-109">其他資訊：無法取得關於 Windows NT 群組/使用者 '\<DomainName\AccountName>' 的資訊，錯誤碼 0x5。</span><span class="sxs-lookup"><span data-stu-id="86e73-109">Additional information:  Could not obtain information about Windows NT group/user '\<DomainName\AccountName>', error code 0x5.</span></span> <span data-ttu-id="86e73-110">(Microsoft SQL Server，錯誤：15404)</span><span class="sxs-lookup"><span data-stu-id="86e73-110">(Microsoft SQL Server, Error: 15404)</span></span>  
  
 <span data-ttu-id="86e73-111">這個問題可能會在下列範例狀況中發生：</span><span class="sxs-lookup"><span data-stu-id="86e73-111">This issue occurs in the following example scenario:</span></span>  
  
1.  <span data-ttu-id="86e73-112">UCP 為 "Domain_1" 的成員。</span><span class="sxs-lookup"><span data-stu-id="86e73-112">The UCP is a member of "Domain_1."</span></span>  
  
2.  <span data-ttu-id="86e73-113">目前使用的是單向網域信任關係：換言之，"Domain_1" 並不受到 "Domain_2" 信任，但是 "Domain_2" 已受到 "Domain_1" 信任。</span><span class="sxs-lookup"><span data-stu-id="86e73-113">A one-way domain trust relationship is in place: that is, "Domain_1" is not trusted by "Domain_2" but "Domain_2" is trusted by "Domain_1."</span></span>  
  
3.  <span data-ttu-id="86e73-114">要註冊到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體也是 "Domain_1" 的成員。</span><span class="sxs-lookup"><span data-stu-id="86e73-114">The instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility is also a member of "Domain_1."</span></span>  
  
4.  <span data-ttu-id="86e73-115">在註冊作業期間，連接到的實例， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以使用 "sa" 進行註冊。</span><span class="sxs-lookup"><span data-stu-id="86e73-115">During the enroll operation, connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll using "sa".</span></span> <span data-ttu-id="86e73-116">指定 "Domain_2" 的 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="86e73-116">Specify a proxy account from "Domain_2."</span></span>  
  
5.  <span data-ttu-id="86e73-117">驗證會成功，但是註冊會失敗。</span><span class="sxs-lookup"><span data-stu-id="86e73-117">Validation succeeds but enrollment fails.</span></span>  
  
 <span data-ttu-id="86e73-118">此問題的因應措施是使用上述範例，連接到的實例， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用 "sa" 註冊到公用程式，並從「Domain_1」提供 proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="86e73-118">The workaround for this issue, using the example above, is to connect to the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to enroll into the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility using "sa" and provide a proxy account from "Domain_1."</span></span>  
  
## <a name="failed-wmi-validation"></a><span data-ttu-id="86e73-119">WMI 驗證失敗</span><span class="sxs-lookup"><span data-stu-id="86e73-119">Failed WMI Validation</span></span>  
 <span data-ttu-id="86e73-120">如果沒有在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體上正確設定 WMI，那麼 [建立 UCP] 與 [註冊受管理的執行個體] 作業會顯示警告，但是並不會封鎖作業。</span><span class="sxs-lookup"><span data-stu-id="86e73-120">If WMI is not properly configured on an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the Create UCP and Enroll Managed Instance operations display a warning, but the operation is not blocked.</span></span> <span data-ttu-id="86e73-121">此外，如果您變更 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 帳戶組態而讓 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 不具備存取必要 WMI 類別的權限，那麼在受影響之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 受管理的執行個體上進行的資料收集，會無法上傳到 UCP。</span><span class="sxs-lookup"><span data-stu-id="86e73-121">Additionally, if you change the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent account configuration so that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent does not have permission to required WMI classes, data collection on the affected managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fails to upload to the UCP.</span></span> <span data-ttu-id="86e73-122">如此會造成 UCP 中顯示灰色圖示。</span><span class="sxs-lookup"><span data-stu-id="86e73-122">This results in gray icons in the UCP.</span></span>  
  
 <span data-ttu-id="86e73-123">對於受影響的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]受管理的執行個體，失敗的資料收集會造成 UCP 清單檢視中出現灰色狀態圖示。</span><span class="sxs-lookup"><span data-stu-id="86e73-123">Failed data collection results in gray status icons in the UCP list view for affected managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="86e73-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 受管理的執行個體中的作業記錄指出 sysutility_mi_collect_and_upload 在步驟 2 失敗 (從 PowerShell 指令碼收集的階段資料)。</span><span class="sxs-lookup"><span data-stu-id="86e73-124">The job history on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shows that sysutility_mi_collect_and_upload fails on step 2 (Stage Data Collected from PowerShell Script).</span></span>  
  
 <span data-ttu-id="86e73-125">簡化的錯誤訊息如下：</span><span class="sxs-lookup"><span data-stu-id="86e73-125">The simplified error messages are:</span></span>  
  
 <span data-ttu-id="86e73-126">命令執行已停止因為 Shell 變數 "ErrorActionPreference" 已設定為 [停止: 拒絕存取]。</span><span class="sxs-lookup"><span data-stu-id="86e73-126">Command execution stopped because the shell variable "ErrorActionPreference" is set to Stop: Access denied.</span></span>  
  
 <span data-ttu-id="86e73-127">錯誤： \<Date-time (MM/DD/YYYY HH:MM:SS)> ：在收集 cpu 屬性時攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86e73-127">ERROR: \<Date-time (MM/DD/YYYY HH:MM:SS)>: Caught exception while collecting cpu properties.</span></span>  <span data-ttu-id="86e73-128">WMI 查詢可能已經失敗。</span><span class="sxs-lookup"><span data-stu-id="86e73-128">A WMI query might have failed.</span></span>  <span data-ttu-id="86e73-129">警告。</span><span class="sxs-lookup"><span data-stu-id="86e73-129">WARNING.</span></span>  
  
 <span data-ttu-id="86e73-130">若要解決這個問題，請確認下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="86e73-130">To resolve this issue, verify the following configuration settings:</span></span>  
  
-   <span data-ttu-id="86e73-131">在 Windows Server 2003 上，SQL Server Agent 服務帳戶必須是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]受管理的執行個體中 Windows 效能監視器使用者群組的成員。</span><span class="sxs-lookup"><span data-stu-id="86e73-131">On Windows Server 2003, the SQL Server Agent service must be part of the Windows Performance Monitoring group on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="86e73-132">WMI 服務必須在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]受管理的執行個體上啟用與設定。</span><span class="sxs-lookup"><span data-stu-id="86e73-132">The WMI service must be enabled and configured on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="86e73-133">WMI 儲存機制可能在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]受管理的執行個體上毀損。</span><span class="sxs-lookup"><span data-stu-id="86e73-133">The WMI repository might be corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="86e73-134">效能程式庫可能在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]受管理的執行個體上遺失或毀損。</span><span class="sxs-lookup"><span data-stu-id="86e73-134">The performance library might be missing or corrupt on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="86e73-135">若要確認特定的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體是否已適當設定為會回報資料給 UCP，請確認下列類別可以在特定的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體上使用，而且 SQL Server Agent 服務帳戶可以存取這些類別：</span><span class="sxs-lookup"><span data-stu-id="86e73-135">To verify that the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is configured properly to report data to the UCP, verify that the following classes are available on the specified instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and that they are accessible to SQL Server Agent service account:</span></span>  
  
-   <span data-ttu-id="86e73-136">Win32_MountPoint</span><span class="sxs-lookup"><span data-stu-id="86e73-136">Win32_MountPoint</span></span>  
  
-   <span data-ttu-id="86e73-137">Win32_PerfRawData_PerfProc_Process</span><span class="sxs-lookup"><span data-stu-id="86e73-137">Win32_PerfRawData_PerfProc_Process</span></span>  
  
-   <span data-ttu-id="86e73-138">Win32_PerfRawData_PerfOS_Processor</span><span class="sxs-lookup"><span data-stu-id="86e73-138">Win32_PerfRawData_PerfOS_Processor</span></span>  
  
-   <span data-ttu-id="86e73-139">Win32_Processor</span><span class="sxs-lookup"><span data-stu-id="86e73-139">Win32_Processor</span></span>  
  
-   <span data-ttu-id="86e73-140">Win32_Volume</span><span class="sxs-lookup"><span data-stu-id="86e73-140">Win32_Volume</span></span>  
  
-   <span data-ttu-id="86e73-141">Win32_LogicalDisk</span><span class="sxs-lookup"><span data-stu-id="86e73-141">Win32_LogicalDisk</span></span>  
  
 <span data-ttu-id="86e73-142">您可以在每一個類別上使用 Get-WmiObject PowerShell 指令程式，藉此確認是可以存取每一個類別。</span><span class="sxs-lookup"><span data-stu-id="86e73-142">You can use the Get-WmiObject PowerShell cmdlet on each of the classes to verify that each class is accessible.</span></span> <span data-ttu-id="86e73-143">請在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]受管理的執行個體上執行下列指令程式：</span><span class="sxs-lookup"><span data-stu-id="86e73-143">Run the following cmdlets on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 <span data-ttu-id="86e73-144">如需疑難排解 WMI 的詳細資訊，請參閱[疑難排解 wmi](https://go.microsoft.com/fwlink/?LinkId=178250)。</span><span class="sxs-lookup"><span data-stu-id="86e73-144">For more information about troubleshooting WMI, see [Troubleshooting WMI](https://go.microsoft.com/fwlink/?LinkId=178250).</span></span> <span data-ttu-id="86e73-145">請注意，這些 SQL Server 公用程式作業中的查詢會於本機執行，因此，無法適用 DCOM 與遠端疑難排解內容。</span><span class="sxs-lookup"><span data-stu-id="86e73-145">Note that queries in these SQL Server Utility operations are running locally, so the DCOM and remote troubleshooting content does not apply.</span></span>  
  
## <a name="failed-data-collection"></a><span data-ttu-id="86e73-146">資料收集失敗</span><span class="sxs-lookup"><span data-stu-id="86e73-146">Failed Data Collection</span></span>  
 <span data-ttu-id="86e73-147">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式資料收集事件失敗，請考慮以下的可能性：</span><span class="sxs-lookup"><span data-stu-id="86e73-147">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility data collection events fail, consider the following possibilities:</span></span>  
  
-   <span data-ttu-id="86e73-148">請勿在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的受控執行個體上變更「公用程式資訊」收集組的任何屬性，也請勿手動開啟/關閉資料收集，因為資料收集是由公用程式代理程式作業所控制。</span><span class="sxs-lookup"><span data-stu-id="86e73-148">Do not change any properties of the "Utility Information" collection set on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and do not turn data collection on/off manually, as data collection is controlled by a Utility agent job.</span></span>  
  
-   <span data-ttu-id="86e73-149">WMI 驗證失敗或不受支援。</span><span class="sxs-lookup"><span data-stu-id="86e73-149">Failed or unsupported WMI validation.</span></span> <span data-ttu-id="86e73-150">如需詳細資訊，請參閱本主題稍早的＜WMI 驗證失敗＞一節。</span><span class="sxs-lookup"><span data-stu-id="86e73-150">For more information, see the Failed WMI Validation section earlier in this topic.</span></span>  
  
-   <span data-ttu-id="86e73-151">重新整理受管理的執行個體清單檢視中的資料，因為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 公用程式視點中的資料不會自動重新整理。</span><span class="sxs-lookup"><span data-stu-id="86e73-151">Refresh data in the managed instance list view, as data in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Utility viewpoints does not refresh automatically.</span></span> <span data-ttu-id="86e73-152">若要重新整理資料，請以滑鼠右鍵按一下 **[公用程式總管]** 導覽窗格中的 **[受管理的執行個體]** 節點，然後選取 **[重新整理]**，或是以滑鼠右鍵按一下清單檢視中的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體名稱，然後選取 **[重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="86e73-152">To refresh data, right-click the **Managed Instances** node in the **Utility Explorer Navigation** pane, then select **Refresh**, or right-click on the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name in the list view, then select **Refresh**.</span></span> <span data-ttu-id="86e73-153">請注意，當使用 UCP 註冊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體之後，最多需要 30 分鐘的時間，資料才會第一次出現在 [公用程式總管] 內容窗格的儀表板和視點內。</span><span class="sxs-lookup"><span data-stu-id="86e73-153">Note that after an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] has been enrolled with a UCP, it can take up to 30 minutes for data to first appear in the dashboard and viewpoints in the Utility Explorer content pane.</span></span>  
  
-   <span data-ttu-id="86e73-154">使用 SQL Server 組態管理員可確認 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體是否在執行中。</span><span class="sxs-lookup"><span data-stu-id="86e73-154">Use SQL Server Configuration Manager to verify that the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running.</span></span>  
  
-   <span data-ttu-id="86e73-155">如果資料收集或資料上傳因逾時問題而失敗，請更新 MSDB 資料庫中的 dbo.fn_sysutility_mi_get_collect_script() 函數。</span><span class="sxs-lookup"><span data-stu-id="86e73-155">If data collection or data upload fail due to timeout issues, update the function dbo.fn_sysutility_mi_get_collect_script() in the MSDB database.</span></span> <span data-ttu-id="86e73-156">特別是在 "Invoke-BulkCopyCommand()" 函數中加入下一行：</span><span class="sxs-lookup"><span data-stu-id="86e73-156">Specifically, in the function "Invoke-BulkCopyCommand()" add line:</span></span>  
  
    ```
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     <span data-ttu-id="86e73-157">預設的逾時值是 30 秒。</span><span class="sxs-lookup"><span data-stu-id="86e73-157">The default timeout value is 30 seconds.</span></span>  
  
-   <span data-ttu-id="86e73-158">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體尚未叢集化，請確認 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 服務正在執行中，而且此服務在 UCP 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的 Managed 執行個體上設定為自動啟動。</span><span class="sxs-lookup"><span data-stu-id="86e73-158">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is not clustered, verify that the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running and that the service is set to start automatically on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="86e73-159">請確認目前確實使用有效的帳戶在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的受管理的執行個體上執行資料收集。</span><span class="sxs-lookup"><span data-stu-id="86e73-159">Verify that a valid account is being used to run data collection on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="86e73-160">例如，密碼可能已過期。</span><span class="sxs-lookup"><span data-stu-id="86e73-160">For example, the password may have expired.</span></span> <span data-ttu-id="86e73-161">如果 Proxy 密碼已經過期，請在 SSMS 中更新密碼認證，如下所示：</span><span class="sxs-lookup"><span data-stu-id="86e73-161">If the proxy password has expired, update password credentials in SSMS, as follows:</span></span>  
  
    1.  <span data-ttu-id="86e73-162">在 SSMS 的 **[物件總管]** 中，展開 **[安全性]** 節點，然後展開 **[認證]** 節點。</span><span class="sxs-lookup"><span data-stu-id="86e73-162">In SSMS **Object Explorer**, expand the **Security** node, then expand the **Credentials** node.</span></span>  
  
    2.  <span data-ttu-id="86e73-163">在**UtilityAgentProxyCredential_ \<GUID> **上按一下滑鼠右鍵，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="86e73-163">Right-click on **UtilityAgentProxyCredential_\<GUID>** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="86e73-164">在 [認證屬性] 對話方塊上，視需要更新\*\*UtilityAgentProxyCredential_ \<GUID> \*\*認證的認證。</span><span class="sxs-lookup"><span data-stu-id="86e73-164">On the Credential Properties dialog, update credentials as necessary for the **UtilityAgentProxyCredential_\<GUID>** credential.</span></span>  
  
    4.  <span data-ttu-id="86e73-165">按一下 [確認]\*\*\*\* 以確認變更。</span><span class="sxs-lookup"><span data-stu-id="86e73-165">Click **OK** to confirm the change.</span></span>  
  
-   <span data-ttu-id="86e73-166">TCP/IP 必須在 UCP 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的受管理的執行個體上啟用。</span><span class="sxs-lookup"><span data-stu-id="86e73-166">TCP/IP should be enabled on the UCP and on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="86e73-167">請透過 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態管理員啟用 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="86e73-167">Enable TCP/IP through [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
-   <span data-ttu-id="86e73-168">您應該啟動 UCP 上的 SQL Server Browser 服務，並將它設定為自動啟動。</span><span class="sxs-lookup"><span data-stu-id="86e73-168">The SQL Server Browser service on the UCP should be started and configured to start automatically.</span></span> <span data-ttu-id="86e73-169">如果您的組織阻止使用 SQL Server Browser 服務，請使用下列步驟讓 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的受管理的執行個體連接到 UCP：</span><span class="sxs-lookup"><span data-stu-id="86e73-169">If your organization prevents use of the SQL Server Browser service, use the following steps to allow a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to connect to the UCP:</span></span>  
  
    1.  <span data-ttu-id="86e73-170">在受管理的實例的 Windows 工作列上 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，按一下 [**開始**]，然後按一下 [**執行 ...**]。</span><span class="sxs-lookup"><span data-stu-id="86e73-170">On the Windows taskbar on the managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], click **Start**, then click **Run...**.</span></span>  
  
    2.  <span data-ttu-id="86e73-171">在提供的空間內輸入 "cliconfg.exe"，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="86e73-171">Type "cliconfg.exe" in the space provided, then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="86e73-172">如果系統允許 SQL 用戶端組態公用程式 EXE 啟動，請按一下 **[繼續]**。</span><span class="sxs-lookup"><span data-stu-id="86e73-172">If prompted to allow "SQL Client Configuration Utility EXE" to start, click "**Continue**."</span></span>  
  
    4.  <span data-ttu-id="86e73-173">在 [ **SQL Server 用戶端網路公用程式**] 對話方塊中，選取 [**別名**] 索引標籤，然後按一下 [**新增 ...**]。</span><span class="sxs-lookup"><span data-stu-id="86e73-173">On the **SQL Server Client Network Utility** dialog box, select the **Alias** tab, then click **Add...**.</span></span>  
  
    5.  <span data-ttu-id="86e73-174">在 **[加入網路程式庫組態]** 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="86e73-174">On the **Add Network Library Configuration** dialog box:</span></span>  
  
    6.  <span data-ttu-id="86e73-175">從網路程式庫清單中指定 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="86e73-175">Specify TCP/IP from the list of network libraries.</span></span>  
  
    7.  <span data-ttu-id="86e73-176">在 **[伺服器別名]** 文字方塊中指定 UCP 的 ComputerName\InstanceName。</span><span class="sxs-lookup"><span data-stu-id="86e73-176">Specify the ComputerName\InstanceName of the UCP in the **Server Alias** text box.</span></span>  
  
    8.  <span data-ttu-id="86e73-177">在 **[伺服器名稱]** 文字方塊中指定 UCP 的 ComputerName。</span><span class="sxs-lookup"><span data-stu-id="86e73-177">Specify the ComputerName of the UCP in the **Server Name** text box.</span></span>  
  
    9. <span data-ttu-id="86e73-178">取消核取 **[動態決定通訊埠]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="86e73-178">Uncheck the **Dynamically determine port** checkbox.</span></span>  
  
    10. <span data-ttu-id="86e73-179">在 **[通訊埠編號]** 文字方塊中，指定 UCP 接聽的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="86e73-179">Specify the port number that the UCP is listening on in the **Port number** text box.</span></span>  
  
    11. <span data-ttu-id="86e73-180">按一下 [確定]  以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="86e73-180">Click **OK** to save your changes.</span></span>  
  
    12. <span data-ttu-id="86e73-181">針對連接至未啟用 SQL Server Browser 服務之 UCP 的每一個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 受管理的執行個體，重複執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="86e73-181">Repeat these steps for each managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that connects to a UCP where the SQL Server Browser service is not enabled.</span></span>  
  
-   <span data-ttu-id="86e73-182">確定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的受管理的執行個體連接到網路。</span><span class="sxs-lookup"><span data-stu-id="86e73-182">Ensure that managed instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are connected to the network.</span></span>  
  
-   <span data-ttu-id="86e73-183">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的受管理的執行個體上有資料庫同名但是具有不同的區分大小寫設定，資料庫和它的視點之間的識別可能會不正確，因而導致資料收集失敗。</span><span class="sxs-lookup"><span data-stu-id="86e73-183">If there are databases with the same name but different case-sensitivity settings on a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the identification between the database and its viewpoints can be incorrect, resulting in failed data collection.</span></span> <span data-ttu-id="86e73-184">例如，名為 "MYDATABASE" 的資料庫可能會顯示名為 "MyDatabase" 之資料庫的健全狀態。</span><span class="sxs-lookup"><span data-stu-id="86e73-184">For example, a database named "MYDATABASE" might show health states for a database named "MyDatabase".</span></span> <span data-ttu-id="86e73-185">在這種情況下，不會產生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="86e73-185">No error is generated in this scenario.</span></span> <span data-ttu-id="86e73-186">資料收集失敗也可能是因為 UCP 中顯示的其他物件出現大小寫不符的情況，例如資料庫檔案與檔案群組名稱。</span><span class="sxs-lookup"><span data-stu-id="86e73-186">Failed data collection can also result from case-sensitivity mismatches in other objects displayed in the UCP, like database file and file group names.</span></span>  
  
-   <span data-ttu-id="86e73-187">如果在 Windows Server 2003 電腦上主控 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 受管理的執行個體，則 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 服務帳戶必須屬於效能監視器使用者安全性群組或本機系統管理員群組。</span><span class="sxs-lookup"><span data-stu-id="86e73-187">If a managed instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is hosted on a Windows Server 2003 computer, then the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account must belong to the Performance Monitor Users security group or the local Administrators group.</span></span> <span data-ttu-id="86e73-188">否則，資料收集將會失敗，並產生拒絕存取錯誤。</span><span class="sxs-lookup"><span data-stu-id="86e73-188">Otherwise, data collection will fail with an access denied error.</span></span> <span data-ttu-id="86e73-189">若要將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 服務帳戶加入到效能監視器使用者安全性群組，請使用以下步驟：</span><span class="sxs-lookup"><span data-stu-id="86e73-189">To add a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service account to the Performance Monitor Users security group, use the following steps:</span></span>  
  
    1.  <span data-ttu-id="86e73-190">開啟 **[電腦管理]**，然後展開 **[本機使用者和群組]**，再展開 **[群組]**。</span><span class="sxs-lookup"><span data-stu-id="86e73-190">Open **Computer Management**, then **Local Users and Groups**, then **Groups**.</span></span>  
  
    2.  <span data-ttu-id="86e73-191">以滑鼠右鍵按一下 **[效能監視器使用者]** ，然後選取 **[加入群組]**。</span><span class="sxs-lookup"><span data-stu-id="86e73-191">Right-click **Performance Monitor Users** and select **Add to Group**.</span></span>  
  
    3.  <span data-ttu-id="86e73-192">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="86e73-192">Click **Add**.</span></span>  
  
    4.  <span data-ttu-id="86e73-193">輸入用來執行 SQL Server Agent 服務的帳戶，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="86e73-193">Enter the account that the SQL Server Agent service is running under, then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="86e73-194">如果將使用者加入至這個群組之前，已經使用 UCP 註冊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體，請重新啟動 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 服務。</span><span class="sxs-lookup"><span data-stu-id="86e73-194">If the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] was already enrolled with the UCP before adding the user to this group, restart the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e73-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86e73-195">See Also</span></span>  
 <span data-ttu-id="86e73-196">[SQL Server 公用程式的功能與工作](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="86e73-196">[SQL Server Utility Features and Tasks](../relational-databases/manage/sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="86e73-197">疑難排解 SQL Server 資源健全情況 &#40;SQL Server 公用程式&#41;</span><span class="sxs-lookup"><span data-stu-id="86e73-197">Troubleshoot SQL Server Resource Health &#40;SQL Server Utility&#41;</span></span>](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)
