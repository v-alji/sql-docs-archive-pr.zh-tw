---
title: AlwaysOn 用戶端連接 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 360e448e87b16b6fb97384bb9a85525a864eeef5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595290"
---
# <a name="always-on-client-connectivity-sql-server"></a><span data-ttu-id="a77f5-102">AlwaysOn 用戶端連接性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a77f5-102">Always On Client Connectivity (SQL Server)</span></span>
  <span data-ttu-id="a77f5-103">本主題描述 AlwaysOn 可用性群組之用戶端連接的考量，包括用戶端組態和設定的必要條件、限制和建議。</span><span class="sxs-lookup"><span data-stu-id="a77f5-103">This topic describes considerations for client connectivity to AlwaysOn Availability Groups, including prerequisites, restrictions, and recommendations for client configurations and settings.</span></span>  
  
 
  
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a> <span data-ttu-id="a77f5-104">用戶端連接性支援</span><span class="sxs-lookup"><span data-stu-id="a77f5-104">Client Connectivity Support</span></span>  
 <span data-ttu-id="a77f5-105">底下章節提供有關 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 支援用戶端連接性的資訊。</span><span class="sxs-lookup"><span data-stu-id="a77f5-105">The section below provides information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] support for client connectivity.</span></span>  
  
 <span data-ttu-id="a77f5-106">**驅動程式支援**</span><span class="sxs-lookup"><span data-stu-id="a77f5-106">**Driver Support**</span></span>  
  
 <span data-ttu-id="a77f5-107">下表摘要說明 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]的驅動程式支援：</span><span class="sxs-lookup"><span data-stu-id="a77f5-107">The following table summarizes driver support for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:</span></span>  
  
|<span data-ttu-id="a77f5-108">驅動程式</span><span class="sxs-lookup"><span data-stu-id="a77f5-108">Driver</span></span>|<span data-ttu-id="a77f5-109">多重子網路容錯移轉</span><span class="sxs-lookup"><span data-stu-id="a77f5-109">Multi-Subnet Failover</span></span>|<span data-ttu-id="a77f5-110">應用程式的意圖</span><span class="sxs-lookup"><span data-stu-id="a77f5-110">Application Intent</span></span>|<span data-ttu-id="a77f5-111">唯讀路由</span><span class="sxs-lookup"><span data-stu-id="a77f5-111">Read-Only Routing</span></span>|<span data-ttu-id="a77f5-112">多重子網路容錯移轉：快速單一子網路端點容錯移轉</span><span class="sxs-lookup"><span data-stu-id="a77f5-112">Multi-Subnet Failover: Faster Single Subnet Endpoint Failover</span></span>|<span data-ttu-id="a77f5-113">多重子網路容錯移轉：SQL 叢集執行個體的具名執行個體解析</span><span class="sxs-lookup"><span data-stu-id="a77f5-113">Multi-Subnet Failover: Named Instance Resolution For SQL Clustered Instances</span></span>|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|<span data-ttu-id="a77f5-114">SQL Native Client 11.0 ODBC</span><span class="sxs-lookup"><span data-stu-id="a77f5-114">SQL Native Client 11.0 ODBC</span></span>|<span data-ttu-id="a77f5-115">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-115">Yes</span></span>|<span data-ttu-id="a77f5-116">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-116">Yes</span></span>|<span data-ttu-id="a77f5-117">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-117">Yes</span></span>|<span data-ttu-id="a77f5-118">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-118">Yes</span></span>|<span data-ttu-id="a77f5-119">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-119">Yes</span></span>|  
|<span data-ttu-id="a77f5-120">SQL Native Client 11.0 OLEDB</span><span class="sxs-lookup"><span data-stu-id="a77f5-120">SQL Native Client 11.0 OLEDB</span></span>|<span data-ttu-id="a77f5-121">否</span><span class="sxs-lookup"><span data-stu-id="a77f5-121">No</span></span>|<span data-ttu-id="a77f5-122">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-122">Yes</span></span>|<span data-ttu-id="a77f5-123">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-123">Yes</span></span>|<span data-ttu-id="a77f5-124">否</span><span class="sxs-lookup"><span data-stu-id="a77f5-124">No</span></span>|<span data-ttu-id="a77f5-125">否</span><span class="sxs-lookup"><span data-stu-id="a77f5-125">No</span></span>|  
|<span data-ttu-id="a77f5-126">具有連接修補程式的 .NET Framework 4.0 ADO.NET**<sup>\*</sup>**</span><span class="sxs-lookup"><span data-stu-id="a77f5-126">ADO.NET with .NET Framework 4.0 with connectivity patch**<sup>\*</sup>**</span></span> |<span data-ttu-id="a77f5-127">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-127">Yes</span></span>|<span data-ttu-id="a77f5-128">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-128">Yes</span></span>|<span data-ttu-id="a77f5-129">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-129">Yes</span></span>|<span data-ttu-id="a77f5-130">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-130">Yes</span></span>|<span data-ttu-id="a77f5-131">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-131">Yes</span></span>|  
|<span data-ttu-id="a77f5-132">具有連接修補程式的 .NET Framework 3.5 SP1 ADO.NET**<sup>**</sup>\*\*</span><span class="sxs-lookup"><span data-stu-id="a77f5-132">ADO.NET with .NET Framework 3.5 SP1 with connectivity patch **<sup>**</sup>\*\*</span></span> |<span data-ttu-id="a77f5-133">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-133">Yes</span></span>|<span data-ttu-id="a77f5-134">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-134">Yes</span></span>|<span data-ttu-id="a77f5-135">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-135">Yes</span></span>|<span data-ttu-id="a77f5-136">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-136">Yes</span></span>|<span data-ttu-id="a77f5-137">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-137">Yes</span></span>|  
|<span data-ttu-id="a77f5-138">Microsoft JDBC Driver 4.0 for SQL Server</span><span class="sxs-lookup"><span data-stu-id="a77f5-138">Microsoft JDBC driver 4.0 for SQL Server</span></span>|<span data-ttu-id="a77f5-139">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-139">Yes</span></span>|<span data-ttu-id="a77f5-140">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-140">Yes</span></span>|<span data-ttu-id="a77f5-141">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-141">Yes</span></span>|<span data-ttu-id="a77f5-142">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-142">Yes</span></span>|<span data-ttu-id="a77f5-143">是</span><span class="sxs-lookup"><span data-stu-id="a77f5-143">Yes</span></span>|  
  
 <span data-ttu-id="a77f5-144">**<sup>\*</sup>** 下載 ADO .NET 的連線修補程式，.NET Framework 4.0： [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211) 。</span><span class="sxs-lookup"><span data-stu-id="a77f5-144">**<sup>\*</sup>**  Download the connectivity patch for ADO .NET with .NET Framework 4.0: [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211).</span></span>  
  
 <span data-ttu-id="a77f5-145">**<sup>**</sup>\* \* 下載 ADO.NET 與 .NET Framework 3.5 SP1 的連線修補程式： [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347) 。</span><span class="sxs-lookup"><span data-stu-id="a77f5-145">**<sup>**</sup>\*\*  Download the connectivity patch for ADO.NET with .NET Framework 3.5 SP1: [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a77f5-146">若要連接到可用性群組接聽程式，用戶端必須使用 TCP 連接字串。</span><span class="sxs-lookup"><span data-stu-id="a77f5-146">To connect to an availability group listener, a client must use a TCP connection string.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a77f5-147">相關工作</span><span class="sxs-lookup"><span data-stu-id="a77f5-147">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a77f5-148">建立及設定可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a77f5-148">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="a77f5-149">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a77f5-149">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="a77f5-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a77f5-150">See Also</span></span>  
 <span data-ttu-id="a77f5-151">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a77f5-151">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="a77f5-152">[容錯移轉叢集和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a77f5-152">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="a77f5-153">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="a77f5-153">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="a77f5-154">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="a77f5-154">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="a77f5-155">[關於可用性複本的用戶端連線存取 &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a77f5-155">[About Client Connection Access to Availability Replicas &#40;SQL Server&#41;](about-client-connection-access-to-availability-replicas-sql-server.md) </span></span>  
 <span data-ttu-id="a77f5-156">[適用于高可用性和嚴重損壞修復的 Microsoft SQL Server AlwaysOn 解決方案指南](https://go.microsoft.com/fwlink/?LinkId=227600) </span><span class="sxs-lookup"><span data-stu-id="a77f5-156">[Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery](https://go.microsoft.com/fwlink/?LinkId=227600) </span></span>  
 <span data-ttu-id="a77f5-157">[SQL Server AlwaysOn 小組 Blog：官方 SQL Server AlwaysOn 小組的 Blog](https://blogs.msdn.com/b/sqlalwayson/) </span><span class="sxs-lookup"><span data-stu-id="a77f5-157">[SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog](https://blogs.msdn.com/b/sqlalwayson/) </span></span>  
 <span data-ttu-id="a77f5-158">[當您從執行 Windows Server 2003、Windows Vista、Windows Server 2008、Windows 7 或 Windows Server 2008 R2 的電腦重新連接 IPSec 連接時發生長時間延遲](https://support.microsoft.com/kb/980915) </span><span class="sxs-lookup"><span data-stu-id="a77f5-158">[A long time delay occurs when you reconnect an IPSec connection from a computer that is running Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2](https://support.microsoft.com/kb/980915) </span></span>  
 <span data-ttu-id="a77f5-159">[叢集服務大約需要 30 秒來容錯移轉 Windows Server 2008 R2 中的 IPv6 IP 位址](https://support.microsoft.com/kb/2578113) </span><span class="sxs-lookup"><span data-stu-id="a77f5-159">[The Cluster service takes about 30 seconds to fail over IPv6 IP addresses in Windows Server 2008 R2](https://support.microsoft.com/kb/2578113) </span></span>  
 [<span data-ttu-id="a77f5-160">如果叢集與應用程式伺服器之間不存在任何路由器，就會緩慢地進行容錯移轉作業</span><span class="sxs-lookup"><span data-stu-id="a77f5-160">Slow failover operation if no router exists between the cluster and an application server</span></span>](https://support.microsoft.com/kb/2582281)  
  
  
