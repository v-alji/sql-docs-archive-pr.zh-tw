---
title: 從 SQL Server 公用程式移除 SQL Server 執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.utility.remove.f1
ms.assetid: ae1d126a-46d2-47bf-b339-17c743df6491
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c09897fcd3ac6d82308288391cf54176eef49d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606838"
---
# <a name="remove-an-instance-of-sql-server-from-the-sql-server-utility"></a><span data-ttu-id="a4e0e-102">從 SQL Server 公用程式移除 SQL Server 執行個體</span><span class="sxs-lookup"><span data-stu-id="a4e0e-102">Remove an Instance of SQL Server from the SQL Server Utility</span></span>
  <span data-ttu-id="a4e0e-103">使用下列步驟可從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Managed 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-103">Use the following steps to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="a4e0e-104">這個程序會從 UCP 清單檢視中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，並停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式資料收集。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-104">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection stops.</span></span> <span data-ttu-id="a4e0e-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體則不會解除安裝。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-105">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a4e0e-106">在您使用這個程序從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之前，請確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 SQL Server Agent 服務正在要移除的執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-106">Before you use this procedure to remove an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and SQL Server Agent services are running on the instance to remove.</span></span>  
  
1.  <span data-ttu-id="a4e0e-107">從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的公用程式總管上，按一下 [Managed 執行個體]。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-107">From the Utility Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click on **Managed Instances**.</span></span> <span data-ttu-id="a4e0e-108">在 [公用程式總管] 內容窗格上，觀察 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Managed 執行個體的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-108">Observe the list view of managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the Utility Explorer content pane.</span></span>  
  
2.  <span data-ttu-id="a4e0e-109">在清單檢視的 [SQL Server 執行個體名稱] 資料行中，選取要從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中移除的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-109">In the **SQL Server Instance Name** column of the list view, select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to remove from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="a4e0e-110">以滑鼠右鍵按一下要移除的執行個體，然後選取 [移除受管理的執行個體...]。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-110">Right-click on the instance to remove, and select **Remove Managed Instance...**.</span></span>  
  
3.  <span data-ttu-id="a4e0e-111">為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體指定具有系統管理員權限的認證：按一下 [連接]、確認 [連接到伺服器] 對話方塊中的資訊，然後按一下 [連接]。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-111">Specify credentials with administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: Click **Connect...**, verify the information in the **Connect to Server** dialog box, then click **Connect**.</span></span> <span data-ttu-id="a4e0e-112">您將會在 [移除 Managed 執行個體] 對話方塊中看到登入資訊。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-112">You will see the login information on the **Remove Managed Instance** dialog.</span></span>  
  
4.  <span data-ttu-id="a4e0e-113">若要確認此作業，請按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-113">To confirm the operation, click **OK**.</span></span> <span data-ttu-id="a4e0e-114">若要結束此作業，請按一下 [取消]。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-114">To quit the operation, click **Cancel**.</span></span>  
  
## <a name="manually-remove-a-managed-instance-of-sql-server-from-a-sql-server-utility"></a><span data-ttu-id="a4e0e-115">從 SQL Server 公用程式中手動移除 SQL Server 的 Managed 執行個體</span><span class="sxs-lookup"><span data-stu-id="a4e0e-115">Manually Remove a Managed Instance of SQL Server from a SQL Server Utility</span></span>  
 <span data-ttu-id="a4e0e-116">這個程序會從 UCP 清單檢視中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，並停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式資料收集。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-116">This procedure removes the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the UCP list view and stops [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility data collection.</span></span> <span data-ttu-id="a4e0e-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體則不會解除安裝。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-117">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not uninstalled.</span></span>  
  
 <span data-ttu-id="a4e0e-118">使用 PowerShell，從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Managed 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-118">To use PowerShell to remove a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="a4e0e-119">此指令碼會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a4e0e-119">This script performs the following operations:</span></span>  
  
-   <span data-ttu-id="a4e0e-120">依據伺服器執行個體名稱取得 UCP。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-120">Gets the UCP by server instance name.</span></span>  
  
-   <span data-ttu-id="a4e0e-121">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Managed 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-121">Removes the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
```powershell
# Get Ucp connection  
$UcpServerInstanceName = "ComputerName\InstanceName";  
$UtilityInstance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $UcpServerInstanceName;  
$UcpConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $UtilityInstance.ConnectionContext.SqlConnectionObject;  
$Utility = [Microsoft.SqlServer.Management.Utility.Utility]::Connect($UcpConnection);  
  
# Now remove the ManagedInstance from the SQL Server Utility  
$ServerInstanceName = "ComputerName\InstanceName";  
$Instance = new-object -Type Microsoft.SqlServer.Management.Smo.Server $ServerInstanceName;  
$InstanceConnection = new-object -Type Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection $Instance.ConnectionContext.SqlConnectionObject;  
$ManagedInstance = $Utility.ManagedInstances[$ServerInstanceName];  
$ManagedInstance.Remove($InstanceConnection);  
```  
  
<span data-ttu-id="a4e0e-122">請務必以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與儲存在中的實例名稱完全相同的方式來參考它 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-122">It's important to refer to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name exactly as it is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a4e0e-123">在區分大小寫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中，您必須使用 @@SERVERNAME 傳回的相同大小寫來指定執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-123">On a case-sensitive instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must specify the instance name using the exact casing as returned by @@SERVERNAME.</span></span> 

<span data-ttu-id="a4e0e-124">若要取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Managed 執行個體的執行個體名稱，請在 Managed 執行個體上執行這個查詢：</span><span class="sxs-lookup"><span data-stu-id="a4e0e-124">To get the instance name for the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], run this query on the managed instance:</span></span>  
  
```sql
select @@SERVERNAME AS instance_name  
```  
  
 <span data-ttu-id="a4e0e-125">此時會從 UCP 中完全移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 Managed 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-125">At this point, the managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is fully removed from the UCP.</span></span> <span data-ttu-id="a4e0e-126">下次當您重新整理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式的資料時，它就會從清單檢視中消失。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-126">It disappears from the list view the next time you refresh data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span> <span data-ttu-id="a4e0e-127">這個狀態表示使用者順利完成在 SSMS 使用者介面中移除 Managed 執行個體的作業。</span><span class="sxs-lookup"><span data-stu-id="a4e0e-127">This state is identical to a user successfully going through the remove managed instance operation in the SSMS user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e0e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4e0e-128">See Also</span></span>  
 <span data-ttu-id="a4e0e-129">[使用公用程式總管來管理 SQL Server 公用程式](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="a4e0e-129">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="a4e0e-130">疑難排解 SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="a4e0e-130">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
