---
title: 設定容錯移轉叢集上的 FILESTREAM | Microsoft 文件
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 29541bbcfd323a85a3fa751f60904fd1a26e1199
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686987"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="6d862-102">設定容錯移轉叢集上的 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="6d862-102">Set Up FILESTREAM on a Failover Cluster</span></span>
  <span data-ttu-id="6d862-103">此主題描述如何在容錯移轉叢集上設定 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="6d862-103">This topic describes how to enable FILESTREAM on a failover cluster.</span></span> <span data-ttu-id="6d862-104">在您嘗試進行這個程序之前，應該先了解 [容錯移轉叢集](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) 並啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="6d862-104">Before you try this procedure, you should understand [failover clustering](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) and have FILESTREAM enabled.</span></span> <span data-ttu-id="6d862-105">如需如何啟用 FILESTREAM 的相關資訊，請參閱 [啟用及設定 FILESTREAM](enable-and-configure-filestream.md)。</span><span class="sxs-lookup"><span data-stu-id="6d862-105">For information about how to enable FILESTREAM, see [Enable and Configure FILESTREAM](enable-and-configure-filestream.md).</span></span>  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a><span data-ttu-id="6d862-106">在容錯移轉叢集上設定 FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="6d862-106">To set up FILESTREAM on a failover cluster</span></span>  
  
1.  <span data-ttu-id="6d862-107">設定容錯移轉叢集的主要節點。</span><span class="sxs-lookup"><span data-stu-id="6d862-107">Set up the primary node for the failover cluster.</span></span>  
  
     <span data-ttu-id="6d862-108">設定完成之後，請使用 [SQL Server 組態管理員]，在主要節點上啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="6d862-108">After the setup finishes, enable FILESTREAM on the primary node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="6d862-109">這樣就會啟用需要 Windows Admin 權限的設定。</span><span class="sxs-lookup"><span data-stu-id="6d862-109">This enables the settings that require Windows Admin privileges.</span></span> <span data-ttu-id="6d862-110">如果需要進行遠端存取，請選取 [允許遠端用戶端具有 FILESTREAM 資料的資料流存取權]。</span><span class="sxs-lookup"><span data-stu-id="6d862-110">If remote access is required, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span> <span data-ttu-id="6d862-111">這樣將會建立檔案共用叢集資源。</span><span class="sxs-lookup"><span data-stu-id="6d862-111">This will create a file-share cluster resource.</span></span>  
  
2.  <span data-ttu-id="6d862-112">設定被動節點。</span><span class="sxs-lookup"><span data-stu-id="6d862-112">Set up a passive node.</span></span>  
  
     <span data-ttu-id="6d862-113">設定完成之後，請使用 [SQL Server 組態管理員]，在被動節點上啟用 FILESTREAM。</span><span class="sxs-lookup"><span data-stu-id="6d862-113">After the setup finishes, enable FILESTREAM on the passive node by using **SQL Server Configuration Manager**.</span></span> <span data-ttu-id="6d862-114">您針對 [Windows 共用名稱] 指定的名稱必須在叢集的所有節點中相同。</span><span class="sxs-lookup"><span data-stu-id="6d862-114">The name that you specify for **Windows Share Name** must be the same across all nodes in the cluster.</span></span>  
  
3.  <span data-ttu-id="6d862-115">若要加入更多被動節點，請重複步驟 2。</span><span class="sxs-lookup"><span data-stu-id="6d862-115">To add more passive nodes, repeat step 2.</span></span>  
  
4.  <span data-ttu-id="6d862-116">加入所有節點之後，請在每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上執行 sp_configure 預存程序，完成此程序。</span><span class="sxs-lookup"><span data-stu-id="6d862-116">After all the nodes are added, complete the process by executing the sp_configure stored procedure on each instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="6d862-117">若要隨時在叢集中加入並啟用其他節點，您可以重複步驟 2、3 和 4。</span><span class="sxs-lookup"><span data-stu-id="6d862-117">To add and enable additional nodes to the cluster at any time, you can repeat steps 2, 3, and 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d862-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d862-118">See Also</span></span>  
 <span data-ttu-id="6d862-119">[伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6d862-119">[Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="6d862-120">[建立新的 SQL Server 容錯移轉叢集 &#40;安裝程式&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span><span class="sxs-lookup"><span data-stu-id="6d862-120">[Create a New SQL Server Failover Cluster &#40;Setup&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md) </span></span>  
 <span data-ttu-id="6d862-121">[移除 SQL Server 容錯移轉叢集執行個體 &#40;安裝程式&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span><span class="sxs-lookup"><span data-stu-id="6d862-121">[Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md) </span></span>  
 [<span data-ttu-id="6d862-122">在 SQL Server 容錯移轉叢集中新增或移除節點 &#40;安裝程式&#41;</span><span class="sxs-lookup"><span data-stu-id="6d862-122">Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;</span></span>](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
