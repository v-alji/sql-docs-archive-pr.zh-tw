---
title: 高可用性 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high availability [SQL Server], Reporting Services
- high availability [Reporting Services]
- Reporting Services, high availability
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dfa0548bc526b007c4301572cd1a8e47a2851e18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607265"
---
# <a name="high-availability-reporting-services"></a><span data-ttu-id="acc29-102">高可用性 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="acc29-102">High Availability (Reporting Services)</span></span>
  <span data-ttu-id="acc29-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器是無狀態伺服器，它會將應用程式資料、內容、屬性和工作階段資訊儲存在兩個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 關聯式資料庫中。</span><span class="sxs-lookup"><span data-stu-id="acc29-103">A [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is a stateless server that stores application data, content, properties, and session information in two [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational databases.</span></span> <span data-ttu-id="acc29-104">因此，確保 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能可用性的最佳方式是進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="acc29-104">As such, the best way to ensure the availability of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] functionality is to do the following:</span></span>  
  
-   <span data-ttu-id="acc29-105">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 的高可用性功能，盡可能增加報表伺服器資料庫的執行時間。</span><span class="sxs-lookup"><span data-stu-id="acc29-105">Use the high availability features of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] to maximize the uptime of the report server databases.</span></span> <span data-ttu-id="acc29-106">如果您將 [!INCLUDE[ssDE](../includes/ssde-md.md)] 執行個體設定為在容錯移轉叢集中執行，就可以在建立報表伺服器資料庫時選取該執行個體。</span><span class="sxs-lookup"><span data-stu-id="acc29-106">If you configure a [!INCLUDE[ssDE](../includes/ssde-md.md)] instance to run in a failover cluster, you can select that instance when you create a report server database.</span></span>  
  
-   <span data-ttu-id="acc29-107">請盡可能使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] 來搭配 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 資料庫和資料來源。</span><span class="sxs-lookup"><span data-stu-id="acc29-107">Use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../includes/sshadr-md.md)] with the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] databases and for data sources, as possible.</span></span> <span data-ttu-id="acc29-108">如需詳細資訊，請參閱 [Reporting Services 與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="acc29-108">For more information, see [Reporting Services with AlwaysOn Availability Groups &#40;SQL Server&#41;](../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="acc29-109">將多個報表伺服器設定為在向外延展部署中執行，其中所有伺服器都會共用單一報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="acc29-109">Configure multiple report servers to run in a scale-out deployment, where all the servers share a single report server database.</span></span> <span data-ttu-id="acc29-110">將多個報表伺服器執行個體 (最好位於不同的伺服器上) 部署在向外延展部署中，有助於在其中一個報表伺服器執行個體無法使用時，提供不中斷的服務。</span><span class="sxs-lookup"><span data-stu-id="acc29-110">Deploying multiple report server instances, preferably on different servers, in a scale-out deployment can help provide uninterrupted service in the event one of the report server instances goes down.</span></span>  
  
 <span data-ttu-id="acc29-111">向外延展部署會提供一種共用資料庫的方式。</span><span class="sxs-lookup"><span data-stu-id="acc29-111">A scale-out deployment provides a way to share a database.</span></span> <span data-ttu-id="acc29-112">如果其中一個報表伺服器無法使用，相同部署中的其他伺服器將繼續運作。</span><span class="sxs-lookup"><span data-stu-id="acc29-112">If one report server goes down, other servers in the same deployment will continue to work.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="acc29-113">無法識別叢集。</span><span class="sxs-lookup"><span data-stu-id="acc29-113">is not cluster-aware.</span></span> <span data-ttu-id="acc29-114">向外延展部署本身不會提供負載平衡。它不會偵測報表伺服器的處理負載，也不會將新的處理要求路由傳送至最不忙碌的伺服器。</span><span class="sxs-lookup"><span data-stu-id="acc29-114">By itself, a scale-out deployment does not provide load balancing; it does not detect the processing loads on a report server and route new processing requests to the least busy server.</span></span> <span data-ttu-id="acc29-115">此外，它不會重新路由傳送完成之前失敗的處理要求。</span><span class="sxs-lookup"><span data-stu-id="acc29-115">It does not re-route processing requests that failed before completion.</span></span> <span data-ttu-id="acc29-116">若要取得負載平衡功能，您必須針對主控報表伺服器的 Web 伺服器設定負載平衡，然後設定向外延展部署中的報表伺服器，讓它們共用相同的報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="acc29-116">To get load balancing features, you must configure load balancing for the Web servers that host the report servers, and then configure the report servers in a scale-out deployment so that they share the same report server database.</span></span>  
  
 <span data-ttu-id="acc29-117">報表伺服器 Web 服務與 Windows 服務會緊密整合而且一起當做單一報表伺服器執行個體執行。</span><span class="sxs-lookup"><span data-stu-id="acc29-117">The Report Server Web service and Windows service are tightly integrated and run together as a single report server instance.</span></span> <span data-ttu-id="acc29-118">您無法個別針對其中一項服務設定可用性。</span><span class="sxs-lookup"><span data-stu-id="acc29-118">You cannot configure availability for one service separately from the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc29-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acc29-119">See Also</span></span>  
 <span data-ttu-id="acc29-120">[高可用性解決方案 &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="acc29-120">[High Availability Solutions &#40;SQL Server&#41;](../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="acc29-121">設定原生模式報表伺服器向外延展部署 &#40;SSRS 設定管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="acc29-121">Configure a Native Mode Report Server Scale-Out Deployment &#40;SSRS Configuration Manager&#41;</span></span>](install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
