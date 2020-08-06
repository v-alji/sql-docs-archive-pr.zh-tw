---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b137b739d4c1641b88983708df62d2e52fd0eab5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705157"
---
# <a name="mssqlserver_41030"></a><span data-ttu-id="19075-102">MSSQLSERVER_41030</span><span class="sxs-lookup"><span data-stu-id="19075-102">MSSQLSERVER_41030</span></span>
    
## <a name="details"></a><span data-ttu-id="19075-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19075-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19075-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="19075-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="19075-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="19075-105">Event ID</span></span>|<span data-ttu-id="19075-106">41030</span><span class="sxs-lookup"><span data-stu-id="19075-106">41030</span></span>|  
|<span data-ttu-id="19075-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="19075-107">Event Source</span></span>|<span data-ttu-id="19075-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="19075-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="19075-109">元件</span><span class="sxs-lookup"><span data-stu-id="19075-109">Component</span></span>|<span data-ttu-id="19075-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="19075-110">SQLEngine</span></span>|  
|<span data-ttu-id="19075-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="19075-111">Symbolic Name</span></span>|<span data-ttu-id="19075-112">OPEN_CLUSTER_SUB_KEY</span><span class="sxs-lookup"><span data-stu-id="19075-112">OPEN_CLUSTER_SUB_KEY</span></span>|  
|<span data-ttu-id="19075-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="19075-113">Message Text</span></span>|<span data-ttu-id="19075-114">無法開啟 Windows Server 容錯移轉叢集登錄子機碼 '%.\*ls' (錯誤碼 %d)。</span><span class="sxs-lookup"><span data-stu-id="19075-114">Failed to open the Windows Server Failover Clustering registry subkey '%.\*ls' (Error code %d).</span></span>  <span data-ttu-id="19075-115">父機碼是叢集根目錄機碼。</span><span class="sxs-lookup"><span data-stu-id="19075-115">The parent key is the cluster root key.</span></span>  <span data-ttu-id="19075-116">WSFC 服務可能不在執行中、無法以目前狀態存取，或指定的引數無效。</span><span class="sxs-lookup"><span data-stu-id="19075-116">The WSFC service may not be running or may not be accessible in its current state, or the specified arguments are invalid.</span></span> <span data-ttu-id="19075-117">如果已卸除對應的可用性群組，就會發生這種錯誤。</span><span class="sxs-lookup"><span data-stu-id="19075-117">If the corresponding availability group has been dropped, this error is expected.</span></span> <span data-ttu-id="19075-118">如需有關這個錯誤碼的資訊，請參閱 Windows 開發文件中的＜系統錯誤碼＞(System Error Codes)。</span><span class="sxs-lookup"><span data-stu-id="19075-118">For information about this error code, see "System Error Codes" in the Windows Development documentation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19075-119">說明</span><span class="sxs-lookup"><span data-stu-id="19075-119">Explanation</span></span>  
 <span data-ttu-id="19075-120">如果 WSFC 叢集已終結，它會移除與 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 相關的所有登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="19075-120">If a WSFC cluster is destroyed, it removes all registry keys related to [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="19075-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="19075-121">User Action</span></span>  
 <span data-ttu-id="19075-122">在重新建立 WSFC 叢集之後，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體已啟用 AlwaysOn 的每個叢集節點上停用然後重新啟用 AlwaysOn。</span><span class="sxs-lookup"><span data-stu-id="19075-122">After re-creating a WSFC cluster, disable and then re-enable AlwaysOn on every cluster node on which an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is enabled for AlwaysOn.</span></span> <span data-ttu-id="19075-123">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員來執行此工作。</span><span class="sxs-lookup"><span data-stu-id="19075-123">You can use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager for this task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19075-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19075-124">See Also</span></span>  
 <span data-ttu-id="19075-125">[啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="19075-125">[Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="19075-126">SQL Server 的 Windows Server 容錯移轉叢集 &#40;WSFC&#41;</span><span class="sxs-lookup"><span data-stu-id="19075-126">Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server</span></span>](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
