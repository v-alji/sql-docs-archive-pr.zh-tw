---
title: 叢集節點設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster node configuration
- cluster node configuration, Setup
ms.assetid: cc960cf3-3b55-44f3-961a-eac4ad05d3d9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2e6bf33bce3eb08994e0bd5529394e033673827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595496"
---
# <a name="cluster-node-configuration"></a><span data-ttu-id="09b39-102">叢集節點組態</span><span class="sxs-lookup"><span data-stu-id="09b39-102">Cluster Node Configuration</span></span>
  <span data-ttu-id="09b39-103">您可以使用 [叢集節點組態] 頁面，在容錯移轉叢集執行個體中加入或移除節點。若要安裝或升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須在容錯移轉叢集的每個節點上執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="09b39-103">Use the Cluster Node Configuration page to add or remove nodes from a failover cluster instance.To install or upgrade a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run the Setup program on each node of the failover cluster.</span></span> <span data-ttu-id="09b39-104">若要將節點加入至現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須在要加入至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的節點上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="09b39-104">To add a node to an existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
## <a name="options"></a><span data-ttu-id="09b39-105">選項</span><span class="sxs-lookup"><span data-stu-id="09b39-105">Options</span></span>  
 <span data-ttu-id="09b39-106">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 實例名稱\*\*-使用下拉式清單選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 要修改的容錯移轉叢集實例。</span><span class="sxs-lookup"><span data-stu-id="09b39-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instance Name** - Use the drop-down list to select the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance to modify.</span></span>  
  
 <span data-ttu-id="09b39-107">**此節點的名稱** - 這個欄位將會填入執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="09b39-107">**Name of this node** - This field will be populated with the name of the computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="09b39-108">這是即將在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體中加入或移除的容錯移轉叢集節點。</span><span class="sxs-lookup"><span data-stu-id="09b39-108">This is the failover cluster node that will be added to or removed from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
  
