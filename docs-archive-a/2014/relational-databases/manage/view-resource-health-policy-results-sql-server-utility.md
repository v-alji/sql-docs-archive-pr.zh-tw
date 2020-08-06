---
title: 檢視資源健全狀況原則結果 (SQL Server 公用程式) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4ab30ad0e87782f8187370a53747be4cf5d313d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701104"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a><span data-ttu-id="0e800-102">檢視資源健全狀況原則結果 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="0e800-102">View Resource Health Policy Results (SQL Server Utility)</span></span>
  <span data-ttu-id="0e800-103">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 中使用公用程式儀表板，針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 受管理的執行個體和資料層應用程式檢視 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 公用程式資源參數。</span><span class="sxs-lookup"><span data-stu-id="0e800-103">Use the Utility dashboard in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="0e800-104">如需詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="0e800-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="view-sql-server-utility-resource-health-policy-results"></a><span data-ttu-id="0e800-105">檢視 SQL Server 公用程式資源健全狀況原則結果</span><span class="sxs-lookup"><span data-stu-id="0e800-105">View SQL Server Utility resource health policy results.</span></span>  
  
1.  <span data-ttu-id="0e800-106">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (SSMS) 中，按一下 [檢視]，然後按一下 [公用程式總管]，檢視公用程式總管瀏覽窗格。</span><span class="sxs-lookup"><span data-stu-id="0e800-106">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (SSMS), click **View**, then click **Utility Explorer** to view the Utility Explorer navigation pane.</span></span> <span data-ttu-id="0e800-107">若要檢視此內容窗格，請按一下 **[檢視]** ，然後按一下 **[公用程式總管內容]** 。</span><span class="sxs-lookup"><span data-stu-id="0e800-107">To view the content pane, click **View**, then click **Utility Explorer Content**.</span></span>  
  
2.  <span data-ttu-id="0e800-108">在瀏覽窗格中，按一下 ![[連線到公用程式]](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")。</span><span class="sxs-lookup"><span data-stu-id="0e800-108">In the navigation pane, click ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Connect to Utility**.</span></span> <span data-ttu-id="0e800-109">如果您尚未建立公用程式控制點 (UCP) 或是您尚未將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體或資料層應用程式註冊到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 公用程式內，請參閱 [SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="0e800-109">If you have not created a utility control point (UCP) or if you have not enrolled instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or data-tier applications into the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Utility, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
3.  <span data-ttu-id="0e800-110">按一下 [UCP] 節點，檢視 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 受管理的執行個體和資料層應用程式的摘要資料 (按一下滑鼠右鍵重新整理)。</span><span class="sxs-lookup"><span data-stu-id="0e800-110">Click the UCP node to view summary data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="0e800-111">儀表板資料會顯示在內容窗格中。</span><span class="sxs-lookup"><span data-stu-id="0e800-111">Dashboard data is displayed in the content pane.</span></span>  
  
4.  <span data-ttu-id="0e800-112">按一下 [受管理的執行個體] 節點，檢視 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 受管理執行個體的清單檢視資料 (按一下滑鼠右鍵重新整理)。</span><span class="sxs-lookup"><span data-stu-id="0e800-112">Click the **Managed Instances** node to view list view data for managed instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (right-click to refresh).</span></span> <span data-ttu-id="0e800-113">清單檢視資料會顯示在內容窗格中。</span><span class="sxs-lookup"><span data-stu-id="0e800-113">List view data is displayed in the content pane.</span></span>  
  
5.  <span data-ttu-id="0e800-114">按一下 [部署的資料層應用程式] 節點，檢視資料層應用程式的清單檢視資料 (按一下滑鼠右鍵重新整理)。</span><span class="sxs-lookup"><span data-stu-id="0e800-114">Click the **Deployed Data-tier Applications** node to view list view data for data-tier applications (right-click to refresh).</span></span> <span data-ttu-id="0e800-115">清單檢視資料會顯示在內容窗格中。</span><span class="sxs-lookup"><span data-stu-id="0e800-115">List view data is displayed in the content pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e800-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e800-116">See Also</span></span>  
 <span data-ttu-id="0e800-117">[SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="0e800-117">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="0e800-118">[降低 CPU 使用量原則的雜訊 &#40;SQL Server 公用程式&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0e800-118">[Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md) </span></span>  
 <span data-ttu-id="0e800-119">[部署的資料層應用程式詳細資料 &#40;SQL Server 公用程式&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0e800-119">[Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md) </span></span>  
 <span data-ttu-id="0e800-120">[受管理的執行個體詳細資料 &#40;SQL Server 公用程式&#41;](../../database-engine/managed-instance-details-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="0e800-120">[Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="0e800-121">公用程式管理 &#40;SQL Server 公用程式&#41;</span><span class="sxs-lookup"><span data-stu-id="0e800-121">Utility Administration &#40;SQL Server Utility&#41;</span></span>](../../database-engine/utility-administration-sql-server-utility.md)  
  
  
