---
title: SQL Server 容錯移轉叢集安裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: c0e75a7c-85c5-423c-a218-77247bf071aa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d11b892bc3ae3dccfbab5bef01feca325056945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595589"
---
# <a name="sql-server-failover-cluster-installation"></a><span data-ttu-id="63d17-102">SQL Server 容錯移轉叢集安裝</span><span class="sxs-lookup"><span data-stu-id="63d17-102">SQL Server Failover Cluster Installation</span></span>
  <span data-ttu-id="63d17-103">若要安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式來建立及設定容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="63d17-103">To install a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must create and configure a failover cluster instance by running [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
## <a name="installing-a-failover-cluster"></a><span data-ttu-id="63d17-104">安裝容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="63d17-104">Installing a Failover Cluster</span></span>  
 <span data-ttu-id="63d17-105">若要安裝容錯移轉叢集，您必須使用具有本機系統管理員權限的網域帳戶，而且在容錯移轉叢集的所有節點上具有權限，能夠登入為服務以及做為作業系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="63d17-105">To install a failover cluster, you must use a domain account with local administrator rights, permission to log on as a service, and to act as part of the operating system on all nodes in the failover cluster.</span></span> <span data-ttu-id="63d17-106">若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式安裝容錯移轉叢集，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="63d17-106">To install a failover cluster by using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup program, follow these steps:</span></span>  
  
1.  <span data-ttu-id="63d17-107">若要安裝、設定和維護 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集，請使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="63d17-107">To install, configure, and maintain a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
    -   <span data-ttu-id="63d17-108">確認建立容錯移轉叢集執行個體 (例如：叢集磁碟資源、IP 位址和網路名稱) 以及可用於容錯移轉之節點所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="63d17-108">Identify the information you need to create your failover cluster instance (for example, cluster disk resource, IP addresses, and network name) and the nodes available for failover.</span></span> <span data-ttu-id="63d17-109">其他資訊：</span><span class="sxs-lookup"><span data-stu-id="63d17-109">For more information:</span></span>  
  
        -   [<span data-ttu-id="63d17-110">安裝容錯移轉叢集之前</span><span class="sxs-lookup"><span data-stu-id="63d17-110">Before Installing Failover Clustering</span></span>](before-installing-failover-clustering.md)  
  
        -   [<span data-ttu-id="63d17-111">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="63d17-111">Security Considerations for a SQL Server Installation</span></span>](../../install/security-considerations-for-a-sql-server-installation.md)  
  
    -   <span data-ttu-id="63d17-112">您必須先完成組態設定步驟，才能執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式；請使用 [Windows 叢集系統管理員] 執行這些步驟。針對您所要設定的每個容錯移轉叢集執行個體，都必須要有一個 WSFC 群組。</span><span class="sxs-lookup"><span data-stu-id="63d17-112">The configuration steps must take place before you run the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup program; use the Windows Cluster Administrator to carry them out. You must have one WSFC group for each failover cluster instance you want to configure.</span></span>  
  
    -   <span data-ttu-id="63d17-113">您必須確定系統符合最低需求。</span><span class="sxs-lookup"><span data-stu-id="63d17-113">You must ensure that your system meets minimum requirements.</span></span> <span data-ttu-id="63d17-114">如需 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集之特定需求的詳細資訊，請參閱 [安裝容錯移轉叢集之前](before-installing-failover-clustering.md)。</span><span class="sxs-lookup"><span data-stu-id="63d17-114">For more information on specific requirements for a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, see [Before Installing Failover Clustering](before-installing-failover-clustering.md).</span></span>  
  
2.  <span data-ttu-id="63d17-115">新增或移除容錯移轉叢集組態中的節點並不會影響其他叢集節點。</span><span class="sxs-lookup"><span data-stu-id="63d17-115">Add or remove nodes from a failover cluster configuration without affecting the other cluster nodes.</span></span> <span data-ttu-id="63d17-116">如需詳細資訊，請參閱[在 SQL Server 容錯移轉叢集中新增或移除節點 &#40;安裝程式&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="63d17-116">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
    -   <span data-ttu-id="63d17-117">容錯移轉叢集中的所有節點必須為相同平台 (即 32 位元或 64 位元)，而且必須在相同的作業系統版本上執行。</span><span class="sxs-lookup"><span data-stu-id="63d17-117">All nodes in a failover cluster must be of the same platform, either 32-bit or 64-bit, and must run the same operating system edition and version.</span></span> <span data-ttu-id="63d17-118">此外，您必須將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 64 位元版本安裝在執行 Windows 64 位元版本作業系統的 64 位元硬體上。</span><span class="sxs-lookup"><span data-stu-id="63d17-118">Also, 64-bit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] editions must be installed on 64-bit hardware running the 64-bit versions of Windows operating systems.</span></span> <span data-ttu-id="63d17-119">這一版沒有容錯移轉叢集的 WOW64 支援。</span><span class="sxs-lookup"><span data-stu-id="63d17-119">There is no WOW64 support for failover clustering in this release.</span></span>  
  
3.  <span data-ttu-id="63d17-120">為每個容錯移轉叢集執行個體指定多個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="63d17-120">Specify multiple IP addresses for each failover cluster instance.</span></span> <span data-ttu-id="63d17-121">您可以為每個子網路指定多個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="63d17-121">You can specify mutiple IP addresses for each subnet.</span></span> <span data-ttu-id="63d17-122">若在相同的子網路上有多重 IP 位址， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式會將相依性設定為 AND。</span><span class="sxs-lookup"><span data-stu-id="63d17-122">If the mutiple IP addresses are on the same subnet, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup sets the dependency to AND.</span></span> <span data-ttu-id="63d17-123">若正跨多重子網路進行節點的叢集作業， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式會將相依性設定為 OR。</span><span class="sxs-lookup"><span data-stu-id="63d17-123">If you are clustering nodes across multiple subnets, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup sets the dependency to OR.</span></span>  
  
## <a name="ssnoversion-failover-cluster-installation-options"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="63d17-124">容錯移轉叢集安裝選項</span><span class="sxs-lookup"><span data-stu-id="63d17-124">Failover Cluster Installation options</span></span>  
  
##### <a name="option-1-integrated-installation-with-add-node"></a><span data-ttu-id="63d17-125">選項 1：整合式安裝與加入節點</span><span class="sxs-lookup"><span data-stu-id="63d17-125">Option 1: Integrated installation with Add Node</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="63d17-126">整合式容錯移轉叢集安裝包含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="63d17-126">integrated failover cluster installation consists of two steps:</span></span>  
  
1.  <span data-ttu-id="63d17-127">建立並設定單一節點的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="63d17-127">Create and configure a single-node [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance.</span></span> <span data-ttu-id="63d17-128">節點設定完成時，您就擁有可完整運作的容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="63d17-128">At the completion of a successful configuration of the node, you have a fully functional failover cluster instance.</span></span> <span data-ttu-id="63d17-129">此時，它仍沒有高可用性，因為容錯移轉叢集只有單一節點。</span><span class="sxs-lookup"><span data-stu-id="63d17-129">At this time it does not have high-availability because there is only one node in the failover cluster.</span></span>  
  
2.  <span data-ttu-id="63d17-130">在要加入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集的每個節點上，使用「加入節點」功能來執行安裝程式，以便加入該節點。</span><span class="sxs-lookup"><span data-stu-id="63d17-130">On each node to be added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, run Setup with Add Node functionality to add that node.</span></span>  
  
##### <a name="option-2-advancedenterprise-installation"></a><span data-ttu-id="63d17-131">選項 2：進階/企業型安裝</span><span class="sxs-lookup"><span data-stu-id="63d17-131">Option 2: Advanced/Enterprise installation</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="63d17-132">進階/企業型容錯移轉叢集安裝包含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="63d17-132">Advanced/Enterprise failover cluster installation consists of two steps:</span></span>  
  
1.  <span data-ttu-id="63d17-133">在即將成為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集一部分的每個節點上，使用「準備容錯移轉叢集」功能來執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="63d17-133">On each node that will be part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, run Setup with Prepare Failover Cluster functionality.</span></span> <span data-ttu-id="63d17-134">雖然這個步驟會準備即將建立叢集的節點，不過在這個步驟結束時，不會提供任何可運作的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="63d17-134">This step prepares the nodes ready to be clustered, but there is no operational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance at the end of this step.</span></span>  
  
2.  <span data-ttu-id="63d17-135">備妥要建立叢集的節點之後，請在擁有共用磁碟的節點上，使用「完成容錯移轉叢集」功能來執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="63d17-135">After the nodes are prepared for clustering, run Setup on the node that owns the shared disk with the Complete Failover Cluster functionality.</span></span> <span data-ttu-id="63d17-136">這個步驟會設定並完成容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="63d17-136">This step configures and completes the failover cluster instance.</span></span> <span data-ttu-id="63d17-137">在這個步驟結束時，您將擁有可運作的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="63d17-137">At the end of this step, you will have an operational [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="63d17-138">兩種安裝選項都允許多節點 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集安裝。</span><span class="sxs-lookup"><span data-stu-id="63d17-138">Either installation option allows for multi-node [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster installation.</span></span> <span data-ttu-id="63d17-139">已經建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集之後，「加入節點」可用來針對任何一個選項加入其他節點。</span><span class="sxs-lookup"><span data-stu-id="63d17-139">Add Node can be used to add additional nodes for either option after a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster has been created.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="63d17-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝位置的作業系統磁碟機代號在加入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集的所有節點上都必須符合。</span><span class="sxs-lookup"><span data-stu-id="63d17-140">The operating system drive letter for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] install locations must match on all the nodes added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
#### <a name="ip-address-configuration-during-setup"></a><span data-ttu-id="63d17-141">安裝期間的 IP 位址組態</span><span class="sxs-lookup"><span data-stu-id="63d17-141">IP Address Configuration During Setup</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="63d17-142">安裝程式可在執行下列動作時，設定或變更 IP 資源的相依性設定：</span><span class="sxs-lookup"><span data-stu-id="63d17-142">Setup lets you set or change the IP resource dependency settings during the following actions:</span></span>  
  
-   <span data-ttu-id="63d17-143">整合式安裝 - [建立新的 SQL Server 容錯移轉叢集 &#40;安裝程式&#41;](create-a-new-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="63d17-143">Integrated Install - [Create a New SQL Server Failover Cluster &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md)</span></span>  
  
-   <span data-ttu-id="63d17-144">CompleteFailoverCluster (進階安裝) - [建立新的 SQL Server 容錯移轉叢集 &#40;安裝程式&#41;](create-a-new-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="63d17-144">CompleteFailoverCluster (Advanced Install) - [Create a New SQL Server Failover Cluster &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md)</span></span>  
  
-   <span data-ttu-id="63d17-145">加入節點 - [在 SQL Server 容錯移轉叢集中加入或移除節點 &#40;安裝程式&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="63d17-145">Add Node - [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
-   <span data-ttu-id="63d17-146">移除節點 - [在 SQL Server 容錯移轉叢集中加入或移除節點 &#40;安裝程式&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span><span class="sxs-lookup"><span data-stu-id="63d17-146">Remove Node - [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)</span></span>  
  
 <span data-ttu-id="63d17-147">**備註** ：支援 IPV6 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="63d17-147">**Note** IPV6 IP addresses are supported.</span></span>  <span data-ttu-id="63d17-148">如果您同時設定了 IPV4 和 IPV6，而且兩者被視為不同子網路，則 IPV6 預期會先上線。</span><span class="sxs-lookup"><span data-stu-id="63d17-148">If you configure both IPV4 and IPV6 there are treated like different subnets, and IPV6 is expected to come online first.</span></span>  
  
##### <a name="ssnoversion-multi-subnet-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="63d17-149">多重子網路容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="63d17-149">Multi-Subnet Failover Cluster</span></span>  
 <span data-ttu-id="63d17-150">當叢集中的節點位於不同的子網路時，您可以設定 OR 相依性。</span><span class="sxs-lookup"><span data-stu-id="63d17-150">You can set OR dependencies when the nodes on the cluster are on different subnets.</span></span> <span data-ttu-id="63d17-151">但是， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 多重子網路容錯移轉叢集中的每一個節點，必須至少是一個已指定之 IP 位址的可能擁有者。</span><span class="sxs-lookup"><span data-stu-id="63d17-151">However, each node in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] multi-subnet failover cluster must be a possible owner of at least one of IP address specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d17-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63d17-152">See Also</span></span>  
 <span data-ttu-id="63d17-153">[安裝容錯移轉叢集之前](before-installing-failover-clustering.md) </span><span class="sxs-lookup"><span data-stu-id="63d17-153">[Before Installing Failover Clustering](before-installing-failover-clustering.md) </span></span>  
 <span data-ttu-id="63d17-154">[建立新的 SQL Server 容錯移轉叢集 &#40;安裝程式&#41;](create-a-new-sql-server-failover-cluster-setup.md) </span><span class="sxs-lookup"><span data-stu-id="63d17-154">[Create a New SQL Server Failover Cluster &#40;Setup&#41;](create-a-new-sql-server-failover-cluster-setup.md) </span></span>  
 <span data-ttu-id="63d17-155">[從命令提示字元安裝 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="63d17-155">[Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md) </span></span>  
 [<span data-ttu-id="63d17-156">升級 SQL Server 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="63d17-156">Upgrade a SQL Server Failover Cluster</span></span>](../windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  
