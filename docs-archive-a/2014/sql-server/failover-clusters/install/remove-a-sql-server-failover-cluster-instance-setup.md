---
title: 移除 SQL Server 容錯移轉叢集執行個體 (安裝程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a4d0ae492481b0677be2d2692fbda0fbc8eb604b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595593"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a><span data-ttu-id="5beca-102">移除 SQL Server 容錯移轉叢集執行個體 (安裝程式)</span><span class="sxs-lookup"><span data-stu-id="5beca-102">Remove a SQL Server Failover Cluster Instance (Setup)</span></span>
  <span data-ttu-id="5beca-103">您可以使用這個程序來解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體。</span><span class="sxs-lookup"><span data-stu-id="5beca-103">Use this procedure to uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover clustered instance.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5beca-104">若要更新或移除 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須是本機系統管理員，並且具有在容錯移轉叢集的所有節點上以服務登入的權限。</span><span class="sxs-lookup"><span data-stu-id="5beca-104">To update or remove a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must be a local administrator with permission to login as a service on all nodes of the failover cluster.</span></span>  
  
 <span data-ttu-id="5beca-105">**開始之前**</span><span class="sxs-lookup"><span data-stu-id="5beca-105">**Before you begin**</span></span>  
  
 <span data-ttu-id="5beca-106">在解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集之前，請先考慮下列重點：</span><span class="sxs-lookup"><span data-stu-id="5beca-106">Consider the following important points before you uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster:</span></span>  
  
-   <span data-ttu-id="5beca-107">若意外解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源將無法啟動。</span><span class="sxs-lookup"><span data-stu-id="5beca-107">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is uninstalled by accident, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resources will fail to start.</span></span> <span data-ttu-id="5beca-108">若要重新安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client，請執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式以安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 必要元件。</span><span class="sxs-lookup"><span data-stu-id="5beca-108">To reinstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, run the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup program to install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prerequisites.</span></span>  
  
-   <span data-ttu-id="5beca-109">如果解除安裝具有一個以上 SQL IP 叢集資源的容錯移轉叢集，您必須使用叢集管理員移除其他 SQL IP 資源。</span><span class="sxs-lookup"><span data-stu-id="5beca-109">If you uninstall a failover cluster that has more than one SQL IP cluster resource, you must remove the additional SQL IP resources using cluster administrator.</span></span>  
  
 <span data-ttu-id="5beca-110">如需命令提示字元語法的資訊，請參閱[從命令提示字元安裝 SQL Server 2014](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)。</span><span class="sxs-lookup"><span data-stu-id="5beca-110">For information about command prompt syntax, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
### <a name="to-uninstall-a-ssnoversion-failover-cluster"></a><span data-ttu-id="5beca-111">解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="5beca-111">To uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster</span></span>  
  
1.  <span data-ttu-id="5beca-112">若要解除安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集，請使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式所提供的「移除節點」功能來分別移除每個節點。</span><span class="sxs-lookup"><span data-stu-id="5beca-112">To uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="5beca-113">如需詳細資訊，請參閱[在 SQL Server 容錯移轉叢集中新增或移除節點 &#40;安裝程式&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)。</span><span class="sxs-lookup"><span data-stu-id="5beca-113">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5beca-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5beca-114">See Also</span></span>  
 [<span data-ttu-id="5beca-115">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="5beca-115">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
