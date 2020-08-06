---
title: 設定健康狀態原則 (SQL Server 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 030aac3b-8901-4c41-91ed-aba96420276c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c5ee466dd2d5bac2ea64364bfc78de8f2f5bea10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592694"
---
# <a name="configure-health-policies-sql-server-utility"></a><span data-ttu-id="4868d-102">設定健康情況原則 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="4868d-102">Configure Health Policies (SQL Server Utility)</span></span>
  <span data-ttu-id="4868d-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 公用程式儀表板，針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體和資料層應用程式檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式資源參數。</span><span class="sxs-lookup"><span data-stu-id="4868d-103">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility dashboard in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility resource parameters for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and data-tier applications.</span></span> <span data-ttu-id="4868d-104">如需詳細資訊，請參閱 [SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="4868d-104">For more information, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 <span data-ttu-id="4868d-105">若要檢視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式健全狀況原則結果，請從 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]連接到公用程式控制點。</span><span class="sxs-lookup"><span data-stu-id="4868d-105">To view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility health policy results, connect to a utility control point from [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="4868d-106">如需詳細資訊，請參閱 [使用公用程式總管來管理 SQL Server 公用程式](use-utility-explorer-to-manage-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="4868d-106">For more information, see [Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4868d-107">可以針對資料層應用程式和受管理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體來設定公用程式健全狀況原則。</span><span class="sxs-lookup"><span data-stu-id="4868d-107">Utility health policies can be configured for data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4868d-108">您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對所有資料層應用程式和受管理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來以全域方式定義健全狀況原則，或者可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式內針對每一個資料層應用程式及每一個受管理的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體來個別定義健全狀況原則。</span><span class="sxs-lookup"><span data-stu-id="4868d-108">Health policies can be defined globally for all data-tier applications and managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, or they can be defined individually for each data-tier application and for each managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility.</span></span>  
  
## <a name="monitoring-policies-for-data-tier-applications"></a><span data-ttu-id="4868d-109">監視資料層應用程式的原則</span><span class="sxs-lookup"><span data-stu-id="4868d-109">Monitoring Policies for Data-tier Applications</span></span>  
 <span data-ttu-id="4868d-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料層應用程式的使用量過高和使用量過低原則如下：</span><span class="sxs-lookup"><span data-stu-id="4868d-110">Overutilization and underutilization policies for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data-tier applications are as follows:</span></span>  
  
-   <span data-ttu-id="4868d-111">資料層應用程式的處理器使用率。</span><span class="sxs-lookup"><span data-stu-id="4868d-111">Data-tier application processor utilization.</span></span>  
  
-   <span data-ttu-id="4868d-112">適用於資料庫檔案的資料層應用程式檔案空間。</span><span class="sxs-lookup"><span data-stu-id="4868d-112">Data-tier application file space for database files.</span></span>  
  
-   <span data-ttu-id="4868d-113">適用於存放磁碟區的資料層應用程式檔案空間。</span><span class="sxs-lookup"><span data-stu-id="4868d-113">Data-tier application file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="4868d-114">電腦處理器使用率。</span><span class="sxs-lookup"><span data-stu-id="4868d-114">Computer processor utilization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4868d-115">對於資料層應用程式而言，存放磁碟區和處理器使用率是唯讀原則。</span><span class="sxs-lookup"><span data-stu-id="4868d-115">Storage volume and processor utilization are read-only policies for data-tier applications.</span></span>  
  
 <span data-ttu-id="4868d-116">如需有關檢視或變更資料層應用程式之全域監視原則的詳細資訊，請參閱[公用程式管理 &#40;SQL Server 公用程式&#41;](../../database-engine/utility-administration-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="4868d-116">For more information about viewing or changing global monitoring policies for data-tier applications, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="4868d-117">如需有關檢視或變更個別資料層應用程式監視原則的詳細資訊，請參閱[部署的資料層應用程式詳細資料 &#40;SQL Server 公用程式&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="4868d-117">For more information about viewing or changing monitoring policies for individual data-tier applications, see [Deployed Data-tier Application Details &#40;SQL Server Utility&#41;](../../database-engine/deployed-data-tier-application-details-sql-server-utility.md).</span></span>  
  
## <a name="monitoring-policies-for-managed-instances-of-sql-server"></a><span data-ttu-id="4868d-118">SQL Server Managed 執行個體的監視原則</span><span class="sxs-lookup"><span data-stu-id="4868d-118">Monitoring Policies for Managed Instances of SQL Server</span></span>  
 <span data-ttu-id="4868d-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Managed 執行個體的使用量過高和使用量過低原則如下：</span><span class="sxs-lookup"><span data-stu-id="4868d-119">Overutilization and underutilization policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are as follows:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4868d-120">執行個體處理器使用率。</span><span class="sxs-lookup"><span data-stu-id="4868d-120">instance processor utilization.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4868d-121">執行個體檔案空間。</span><span class="sxs-lookup"><span data-stu-id="4868d-121">instance file space for database files.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4868d-122">執行個體檔案空間。</span><span class="sxs-lookup"><span data-stu-id="4868d-122">instance file space for storage volumes.</span></span>  
  
-   <span data-ttu-id="4868d-123">電腦處理器使用率。</span><span class="sxs-lookup"><span data-stu-id="4868d-123">Computer processor utilization.</span></span>  
  
 <span data-ttu-id="4868d-124">如需有關檢視或變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體之全域監視原則的詳細資訊，請參閱[公用程式管理 &#40;SQL Server 公用程式&#41;](../../database-engine/utility-administration-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="4868d-124">For more information about viewing or changing global monitoring policies for managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="4868d-125">如需有關檢視或變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 個別受管理的執行個體之監視原則的詳細資訊，請參閱[受管理的執行個體詳細資料 &#40;SQL Server 公用程式&#41;](../../database-engine/managed-instance-details-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="4868d-125">For more information about viewing or changing monitoring policies for individual managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Managed Instance Details &#40;SQL Server Utility&#41;](../../database-engine/managed-instance-details-sql-server-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4868d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4868d-126">See Also</span></span>  
 <span data-ttu-id="4868d-127">[SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="4868d-127">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 [<span data-ttu-id="4868d-128">降低 CPU 使用量原則的雜訊 &#40;SQL Server 公用程式&#41;</span><span class="sxs-lookup"><span data-stu-id="4868d-128">Reduce Noise in CPU Utilization Policies &#40;SQL Server Utility&#41;</span></span>](reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
  
