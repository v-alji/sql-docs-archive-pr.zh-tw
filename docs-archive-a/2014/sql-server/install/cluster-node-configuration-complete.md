---
title: 叢集節點設定 (完成) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64174d54-edee-49b8-9b43-039574bf2ca1
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cc1f8ce4574580746e20c478b23e40485c3e6ecc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595503"
---
# <a name="cluster-node-configuration-complete"></a><span data-ttu-id="2cbc5-102">叢集節點組態 (完成)</span><span class="sxs-lookup"><span data-stu-id="2cbc5-102">Cluster Node Configuration (Complete)</span></span>
  <span data-ttu-id="2cbc5-103">您可以使用 [叢集節點組態 (完成)] 頁面來指定已經準備要建立叢集的現有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。若要安裝或升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須在容錯移轉叢集的每個節點上執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="2cbc5-103">Use the Cluster Node Configuration (Complete) page to specify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that has been prepared for clustering.To install or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run the Setup program on each node of the failover cluster.</span></span> <span data-ttu-id="2cbc5-104">若要將節點加入至現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須在要加入至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的節點上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="2cbc5-104">To add a node to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2cbc5-105">選項</span><span class="sxs-lookup"><span data-stu-id="2cbc5-105">Options</span></span>  
 <span data-ttu-id="2cbc5-106">在下拉式方塊中：</span><span class="sxs-lookup"><span data-stu-id="2cbc5-106">From the drop-down boxes:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2cbc5-107">實例名稱-選取容錯移轉叢集的實例名稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2cbc5-107">instance name - Select the instance name for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
-   <span data-ttu-id="2cbc5-108">此節點的名稱-這個欄位會預先填入安裝程式執行所在的電腦名稱稱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2cbc5-108">Name of this node - This field is pre-populated with the computer name where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program is running.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="2cbc5-109">容錯移轉叢集網路名稱-這個欄位不會預先填入。</span><span class="sxs-lookup"><span data-stu-id="2cbc5-109">Failover Cluster Network Name - This field is not pre-populated.</span></span> <span data-ttu-id="2cbc5-110">您可以針對新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體指定網路名稱。</span><span class="sxs-lookup"><span data-stu-id="2cbc5-110">Specify the network name for the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span> <span data-ttu-id="2cbc5-111">這是在網路上識別容錯移轉叢集執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="2cbc5-111">This is the name that identifies the failover cluster instance on the network.</span></span>  
  
  
