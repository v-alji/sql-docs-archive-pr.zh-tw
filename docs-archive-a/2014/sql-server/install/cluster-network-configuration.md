---
title: 叢集網路設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 17ab563817a3b9b476dfd566f4a7f2beda98ca26
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595501"
---
# <a name="cluster-network-configuration"></a><span data-ttu-id="7e8c1-102">叢集網路組態</span><span class="sxs-lookup"><span data-stu-id="7e8c1-102">Cluster Network Configuration</span></span>
  <span data-ttu-id="7e8c1-103">使用 **[叢集網路選取]** 頁面，即可指定容錯移轉叢集執行個體的網路資源。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-103">Use the **Cluster Network Selection** page to specify the network resources for your failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7e8c1-104">選項</span><span class="sxs-lookup"><span data-stu-id="7e8c1-104">Options</span></span>  
 <span data-ttu-id="7e8c1-105">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集網路名稱\*\*-這是用來在網路上識別容錯移轉叢集實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-105">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Cluster Network Name** - This is the name used to identify your failover cluster instance on the network.</span></span>  
  
 <span data-ttu-id="7e8c1-106">**網路設定** ：指定容錯移轉叢集執行個體的 IP 類型和 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-106">**Network Settings** - Specify the IP type and IP address for your failover cluster instance.</span></span>  
  
 <span data-ttu-id="7e8c1-107">在加入節點和移除節點作業期間， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集之現有 IP 位址的唯讀清單。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-107">During the Add Node and Remove Node operations, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] displays a read-only list of the existing IP addresses for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="7e8c1-108">整合式安裝：</span><span class="sxs-lookup"><span data-stu-id="7e8c1-108">Integrated Install:</span></span>  
  
    -   <span data-ttu-id="7e8c1-109">如果您要加入支援一組完全相同網路子網路的節點，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集的現有節點支援這組子網路，就無法加入其他 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-109">If you are adding a node that supports an identical set of network subnets supported by the existing nodes of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP addresses can be added.</span></span> <span data-ttu-id="7e8c1-110">相依性設定會維持不變。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-110">The dependency setting remains unchanged.</span></span>  
  
    -   <span data-ttu-id="7e8c1-111">如果您要加入支援子網路子集的節點，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集的現有節點支援這個子集，就無法加入其他 IP 位址資源。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-111">If you are adding a node that supports a subset of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, no additional IP address resources can be added.</span></span> <span data-ttu-id="7e8c1-112">IP 位址資源相依性會設定為 OR，以便反映所有指定的 IP 位址在所有叢集節點上都無效。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-112">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="7e8c1-113">如果您要加入支援其他子網路 (除了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集之現有節點已經支援的子網路以外) 的節點，就可以選擇加入新的有效 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-113">If you are adding a node that supports subnets in addition to the subnets already supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you have the option of adding new valid IP addresses.</span></span> <span data-ttu-id="7e8c1-114">如果指定了新的 IP 位址，IP 位址資源相依性會設定為 OR，以便反映所有指定的 IP 位址在所有叢集節點上都無效。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-114">If new IP addresses are specified, the IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
    -   <span data-ttu-id="7e8c1-115">如果您要加入支援其他網路子網路的節點，但是這個節點不支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集之現有節點所支援的任何子網路，就必須加入其他 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-115">If you are adding a node that supports additional network subnets, but supports none of the subnets supported by the existing nodes on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are required to add additional IP addresses.</span></span> <span data-ttu-id="7e8c1-116">IP 位址資源相依性會設定為 OR，以便反映所有指定的 IP 位址在所有叢集節點上都無效。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-116">The IP address resource dependency is set to OR to reflect that all the specified IP addresses are not valid on all the cluster nodes.</span></span>  
  
-   <span data-ttu-id="7e8c1-117">進階安裝：在安裝的完成步驟期間，請針對容錯移轉叢集執行個體的所有節點和子網路指定 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-117">Advanced Install: During the Complete step of the installation, specify the IP address for all the nodes and subnets for your failover cluster instance.</span></span> <span data-ttu-id="7e8c1-118">您可以針對多重子網路容錯移轉叢集指定多個 IP 位址，但是每個子網路只支援一個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-118">You can specify multiple IP addresses for a multi-subnet failover cluster, but only one IP address per subnet is supported.</span></span> <span data-ttu-id="7e8c1-119">每個備妥的節點都至少應該是一個 IP 位址的擁有者。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-119">Every prepared node should be an owner of at least one IP address.</span></span> <span data-ttu-id="7e8c1-120">如果您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集具有多個子網路，系統就會提示您將 IP 位址資源相依性設為 OR。移除節點：</span><span class="sxs-lookup"><span data-stu-id="7e8c1-120">If you have multiple subnets in your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you are prompted to set the IP address resource dependency to OR.Remove Node:</span></span>  
  
    -   <span data-ttu-id="7e8c1-121">如果所有其餘節點都支援其餘 IP 位址，系統就會提示您將 IP 位址資源相依性設定為 AND。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-121">If the remaining IP addresses are supported on all the remaining nodes, you are prompted to set the IP address resource dependencyto AND.</span></span>  
  
    -   <span data-ttu-id="7e8c1-122">如果所有其餘節點不支援其餘 IP 位址，IP 位址資源相依性就會維持 OR。</span><span class="sxs-lookup"><span data-stu-id="7e8c1-122">If the remaining IP addresses are not supported on all the remaining nodes, the IP address resource dependency is left as OR.</span></span>  
  
  
