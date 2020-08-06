---
title: 升級 SQL Server 容錯移轉叢集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading failover clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], upgrading
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca08e83c362e714f234a60ee358df3bcb03ade93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595560"
---
# <a name="upgrade-a-sql-server-failover-cluster"></a><span data-ttu-id="7bbca-102">升級 SQL Server 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="7bbca-102">Upgrade a SQL Server Failover Cluster</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="7bbca-103">支援在所有容錯移轉叢集節點上，個別從 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 與 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 容錯移轉叢集，升級 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 及 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7bbca-103">supports upgrade of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all failover cluster nodes.</span></span>  
  
 <span data-ttu-id="7bbca-104">支援詳細資料如下：</span><span class="sxs-lookup"><span data-stu-id="7bbca-104">Support details are as follows:</span></span>  
  
-   <span data-ttu-id="7bbca-105">目前支援從使用者介面和命令提示字元進行升級。</span><span class="sxs-lookup"><span data-stu-id="7bbca-105">Upgrade is supported both through the user interface and from the command prompt.</span></span> <span data-ttu-id="7bbca-106">如需詳細資訊，請參閱[升級 SQL Server 容錯移轉叢集執行個體 &#40;安裝程式&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) 和[從命令提示字元安裝 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="7bbca-106">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) and [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
-   <span data-ttu-id="7bbca-107">從升級 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -您可以在每個容錯移轉叢集節點上，從命令提示字元執行升級，或使用安裝程式 UI 來升級每個叢集節點。</span><span class="sxs-lookup"><span data-stu-id="7bbca-107">Upgrading from [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] - You can run upgrade from the command prompt on each failover cluster node, or by using the Setup UI to upgrade each cluster node.</span></span> <span data-ttu-id="7bbca-108">如果全文檢索搜尋和複寫功能不存在升級的執行個體上，系統就會自動安裝它們，而不會提供省略它們的選項。</span><span class="sxs-lookup"><span data-stu-id="7bbca-108">If Full-text search and Replication features do not exist on the instance being upgraded, they will be installed automatically with no option to omit them.</span></span>  
  
-   <span data-ttu-id="7bbca-109">Service Pack 安裝 - 您必須將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 和修補程式個別套用至所有節點上的 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="7bbca-109">Service pack installation - you must apply [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service packs and patches to [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] failover clusters separately on all nodes.</span></span>  
  
-   <span data-ttu-id="7bbca-110">不支援下列狀況：</span><span class="sxs-lookup"><span data-stu-id="7bbca-110">The following scenarios are not supported:</span></span>  
  
    -   <span data-ttu-id="7bbca-111">您無法從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的獨立執行個體移轉至容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="7bbca-111">You cannot migrate from a stand-alone instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to a failover cluster.</span></span>  
  
    -   <span data-ttu-id="7bbca-112">將功能加入至容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="7bbca-112">Add features to a failover cluster.</span></span> <span data-ttu-id="7bbca-113">例如，您無法將 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 加入至現有的僅限 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="7bbca-113">For example, you cannot add the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] to an existing [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-only failover cluster.</span></span>  
  
    -   <span data-ttu-id="7bbca-114">您無法將容錯移轉叢集節點降級為獨立執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bbca-114">You cannot downgrade a failover cluster node to a stand-alone instance.</span></span>  
  
-   <span data-ttu-id="7bbca-115">如需詳細資訊，請參閱 [AlwaysOn 容錯移轉叢集執行個體 (SQL Server)](always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="7bbca-115">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
## <a name="upgrading-a-ssnoversion-multi-subnet-failover-cluster"></a><span data-ttu-id="7bbca-116">升級 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 多重子網路容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="7bbca-116">Upgrading a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Multi-Subnet Failover Cluster</span></span>  
 <span data-ttu-id="7bbca-117">您無法將非多重子網容錯移轉叢集直接升級 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 多重子網容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="7bbca-117">You cannot directly upgrade a non-multi-subnet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] multi-subnet failover cluster.</span></span> <span data-ttu-id="7bbca-118">如需詳細資訊，請參閱[升級 SQL Server 容錯移轉叢集執行個體 &#40;安裝程式&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="7bbca-118">For more information, see [Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bbca-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bbca-119">See Also</span></span>  
 <span data-ttu-id="7bbca-120">[支援的版本與版本升級](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="7bbca-120">[Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="7bbca-121">[升級 SQL Server 容錯移轉叢集實例 &#40;安裝程式&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="7bbca-121">[Upgrade a SQL Server Failover Cluster Instance &#40;Setup&#41;](upgrade-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="7bbca-122">Install SQL Server 2014 from the Command Prompt</span><span class="sxs-lookup"><span data-stu-id="7bbca-122">Install SQL Server 2014 from the Command Prompt</span></span>](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)  
  
  
