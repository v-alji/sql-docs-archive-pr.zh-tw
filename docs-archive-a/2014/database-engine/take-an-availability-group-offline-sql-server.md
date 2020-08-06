---
title: 改變可用性群組離線
description: 離線設定 Always On 可用性群組的步驟
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: rothja
ms.author: jroth
ms.openlocfilehash: db2f56befe6905b9c3de6bd1ab6a2e5a4a00b1b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596879"
---
# <a name="take-an-availability-group-offline-sql-server"></a><span data-ttu-id="f6ae4-103">讓可用性群組離線 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f6ae4-103">Take an Availability Group Offline (SQL Server)</span></span>
  <span data-ttu-id="f6ae4-104">本主題描述如何使用 [!INCLUDE[tsql](../includes/tsql-md.md)] 和更新版本中的 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] ，將 AlwaysOn 可用性群組從 ONLINE 狀態變成 OFFLINE 狀態。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-104">This topic describes how to take an AlwaysOn availability group from the ONLINE state to the OFFLINE state by using [!INCLUDE[tsql](../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] and later versions.</span></span> <span data-ttu-id="f6ae4-105">同步認可資料庫不會有資料遺失，因為如果有任何未同步處理的同步認可複本，OFFLINE 作業就會引發錯誤並且讓可用性群組維持 ONLINE 狀態。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-105">There is no data loss for synchronous-commit databases because if any synchronous-commit replica is not synchronized, the OFFLINE operation raises an error and leaves the availability group ONLINE.</span></span> <span data-ttu-id="f6ae4-106">讓可用性群組保持上線可保護未同步處理的同步認可資料庫，避免可能的資料遺失。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-106">Keeping the availability group online protects unsynchronized synchronous-commit databases from possible data loss.</span></span> <span data-ttu-id="f6ae4-107">在可用性群組離線之後，其資料庫就無法供用戶端使用，而且您無法讓可用性群組恢復上線。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-107">After an availability group goes offline, its databases become unavailable to clients and you cannot bring the availability group back online.</span></span> <span data-ttu-id="f6ae4-108">因此，只有在從某一個 WSFC 叢集將可用性群組資源移轉至另一個叢集時，才讓可用性群組離現。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-108">Therefore, take an availability group offline only to migrate the availability group resources from one WSFC cluster to another.</span></span>  
  
 <span data-ttu-id="f6ae4-109">跨叢集移轉 [!INCLUDE[ssHADR](../includes/sshadr-md.md)]期間，如果任何應用程式直接連接到可用性群組的主要複本，則必須讓可用性群組離線。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-109">During a cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)], if any applications connect directly to the primary replica of an availability group, the availability group must be taken offline.</span></span> <span data-ttu-id="f6ae4-110">[!INCLUDE[ssHADR](../includes/sshadr-md.md)] 的跨叢集移轉支援以最短的可用性群組停機時間進行作業系統升級。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-110">Cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] supports OS upgrade with minimal downtime of availability groups.</span></span> <span data-ttu-id="f6ae4-111">典型的案例是使用 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] 的跨叢集移轉將作業系統升級為 [!INCLUDE[win8](../includes/win8-md.md)] 或 [!INCLUDE[win8srv](../includes/win8srv-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-111">The typical scenario is to use cross-cluster migration of [!INCLUDE[ssHADR](../includes/sshadr-md.md)] for OS upgrade to [!INCLUDE[win8](../includes/win8-md.md)] or [!INCLUDE[win8srv](../includes/win8srv-md.md)].</span></span> <span data-ttu-id="f6ae4-112">如需詳細資訊，請參閱[針對作業系統升級進行 AlwaysOn 可用性群組的跨叢集移轉](https://msdn.microsoft.com/library/jj873730.aspx)。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-112">For more information, see [Cross-Cluster Migration of AlwaysOn Availability Groups for OS Upgrade](https://msdn.microsoft.com/library/jj873730.aspx).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6ae4-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="f6ae4-113">Before You Begin</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f6ae4-114">OFFLINE 選項只可用於跨叢集移轉可用性群組資源。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-114">Use the OFFLINE option only for a cross-cluster migration of availability group resources.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f6ae4-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="f6ae4-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="f6ae4-116">您輸入 OFFLINE 命令所在的伺服器執行個體必須執行 [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] 或更新版本 (Enterprise Edition 或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-116">The server instance on which you enter the OFFLINE command must be running [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] or above (Enterprise edition or above).</span></span>  
  
-   <span data-ttu-id="f6ae4-117">可用性群組目前必須在線上。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-117">The availability group must currently be online.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="f6ae4-118">建議</span><span class="sxs-lookup"><span data-stu-id="f6ae4-118">Recommendations</span></span>  
 <span data-ttu-id="f6ae4-119">在您讓可用性群組離線之前，請先刪除可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-119">Before you take the availability group offline, delete the availability group listener or listeners.</span></span> <span data-ttu-id="f6ae4-120">如需詳細資訊，請參閱 [移除可用性群組接聽程式 &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-120">For more information, see [Remove an Availability Group Listener &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6ae4-121">Security</span><span class="sxs-lookup"><span data-stu-id="f6ae4-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6ae4-122">權限</span><span class="sxs-lookup"><span data-stu-id="f6ae4-122">Permissions</span></span>  
 <span data-ttu-id="f6ae4-123">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-123">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6ae4-124">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6ae4-124">Using Transact-SQL</span></span>  
 <span data-ttu-id="f6ae4-125">**讓可用性群組離線**</span><span class="sxs-lookup"><span data-stu-id="f6ae4-125">**To take an availability group offline**</span></span>  
  
1.  <span data-ttu-id="f6ae4-126">連接到主控可用性群組之可用性複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-126">Connect to a server instance that hosts an availability replica for the availability group.</span></span> <span data-ttu-id="f6ae4-127">此複本可以是主要複本或次要複本。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-127">This replica can be the primary replica or a secondary replica.</span></span>  
  
2.  <span data-ttu-id="f6ae4-128">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f6ae4-128">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="f6ae4-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span><span class="sxs-lookup"><span data-stu-id="f6ae4-129">ALTER AVAILABILITY GROUP *group_name* OFFLINE</span></span>  
  
     <span data-ttu-id="f6ae4-130">其中 <群組名稱> 是可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-130">where *group_name* is the name of the availability group.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f6ae4-131">範例</span><span class="sxs-lookup"><span data-stu-id="f6ae4-131">Example</span></span>  
 <span data-ttu-id="f6ae4-132">下列範例會讓 `AccountsAG` 可用性群組離線。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-132">The following example takes the `AccountsAG` availability group offline.</span></span>  
  
```sql
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="follow-up-after-the-availability-group-goes-offline"></a><a name="FollowUp"></a> <span data-ttu-id="f6ae4-133">後續操作：可用性群組離線之後</span><span class="sxs-lookup"><span data-stu-id="f6ae4-133">Follow Up: After the Availability Group Goes Offline</span></span>  
  
-   <span data-ttu-id="f6ae4-134">**OFFLINE 作業的記錄：** OFFLINE 作業起始所在的 WSFC 節點身分識別會同時儲存在 WSFC 叢集記錄檔和 SQL ERRORLOG 中。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-134">**Logging of OFFLINE operation:**  The identity of the WSFC node where the OFFLINE operation was initiated is stored in both the WSFC cluster log and the SQL ERRORLOG.</span></span>  
  
-   <span data-ttu-id="f6ae4-135">**如未在群組離線前刪除可用性群組接聽程式：** 如果您要將可用性群組移轉至另一個 WSFC 叢集，請刪除接聽程式的 VNN 和 VIP。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-135">**If you did not delete the availability group listener before taking the group offline:**  If you are migrating the availability group to another WSFC cluster, delete the VNN and VIP of the listener.</span></span> <span data-ttu-id="f6ae4-136">您可以使用容錯移轉叢集管理主控台、 [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell Cmdlet 或 [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx)刪除它們。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-136">You can delete them by using either the Failover Cluster Management console, the [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) PowerShell cmdlet, or [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx).</span></span> <span data-ttu-id="f6ae4-137">請注意，cluster.exe 在 Windows 8 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="f6ae4-137">Note that cluster.exe is deprecated on Windows 8.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f6ae4-138">相關工作</span><span class="sxs-lookup"><span data-stu-id="f6ae4-138">Related Tasks</span></span>  
  
-   [<span data-ttu-id="f6ae4-139">移除可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ae4-139">Remove an Availability Group Listener &#40;SQL Server&#41;</span></span>](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="f6ae4-140">變更伺服器執行個體的 HADR 叢集內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ae4-140">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="f6ae4-141">相關內容</span><span class="sxs-lookup"><span data-stu-id="f6ae4-141">Related Content</span></span>  
  
-   <span data-ttu-id="f6ae4-142">[SQL Server 2012 技術文件](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f6ae4-142">[SQL Server 2012 Technical Articles](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)</span></span>  
  
-   [<span data-ttu-id="f6ae4-143">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="f6ae4-143">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="f6ae4-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6ae4-144">See Also</span></span>  
 [<span data-ttu-id="f6ae4-145">AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f6ae4-145">AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/always-on-availability-groups-sql-server.md)  
