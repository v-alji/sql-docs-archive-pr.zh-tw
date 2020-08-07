---
title: SQL Server 屬性 (AlwaysOn 高可用性索引標籤) |Microsoft Docs
description: 瞭解如何在 SQL Server 2014 中開啟或關閉 AlwaysOn 可用性群組功能。 查看伺服器實例必須符合此功能的必要條件。
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 3939b40a334746e9ee96441338e2e50791987103
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703658"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a><span data-ttu-id="3a919-104">SQL Server 屬性 (AlwaysOn 高可用性索引標籤)</span><span class="sxs-lookup"><span data-stu-id="3a919-104">SQL Server Properties (AlwaysOn High Availability Tab)</span></span>
  <span data-ttu-id="3a919-105">在 Configuration Manager 中，使用 [ **SQL Server 屬性**] 對話方塊的 [ **AlwaysOn 高可用性**] 索引標籤 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，啟用或停用中的 [AlwaysOn 可用性群組] 功能 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3a919-105">Use the **AlwaysOn High Availability** tab of the **SQL Server Properties** dialog box in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to enable or disable the AlwaysOn Availability Groups feature in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="3a919-106">啟用 AlwaysOn 可用性群組是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體將可用性群組做為高可用性和災害復原方案的必要條件。</span><span class="sxs-lookup"><span data-stu-id="3a919-106">Enabling AlwaysOn Availability Groups is a prerequisite for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to use availability groups as a high availability and disaster recovery solution.</span></span>  
  
##  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="3a919-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="3a919-107">Prerequisites</span></span>  
 <span data-ttu-id="3a919-108">若要啟用 AlwaysOn 可用性群組，伺服器執行個體必須符合下列必要條件：</span><span class="sxs-lookup"><span data-stu-id="3a919-108">To be enabled for AlwaysOn Availability Groups, a server instance must meet the following prerequisites:</span></span>  
  
-   <span data-ttu-id="3a919-109">此伺服器執行個體必須位於 Windows Server 容錯移轉叢集 (WSFC) 節點上。</span><span class="sxs-lookup"><span data-stu-id="3a919-109">The server instance must reside on a Windows Server Failover Clustering (WSFC) node.</span></span>  
  
-   <span data-ttu-id="3a919-110">若要位於相同的可用性群組，執行個體必須位於相同的 WSFC 叢集中。</span><span class="sxs-lookup"><span data-stu-id="3a919-110">To be in the same availability group, instances must be in the same WSFC cluster.</span></span> <span data-ttu-id="3a919-111">可用性群組不可跨越多個 WSFC 叢集。</span><span class="sxs-lookup"><span data-stu-id="3a919-111">An availability group cannot span WSFC clusters.</span></span>  
  
-   <span data-ttu-id="3a919-112">伺服器執行個體必須執行支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="3a919-112">The server instance must be running an edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that supports [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].</span></span>  
  
-   <span data-ttu-id="3a919-113">一次只針對一個伺服器執行個體啟用 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="3a919-113">Enable AlwaysOn Availability Groups for only one server instance at a time.</span></span> <span data-ttu-id="3a919-114">啟用 AlwaysOn 可用性群組之後，等到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務重新啟動後才能為下一個伺服器執行個體啟用。</span><span class="sxs-lookup"><span data-stu-id="3a919-114">After enabling AlwaysOn Availability Groups, wait until the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service has restarted before you enable the next server instance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a919-115">如需功能支援的詳細資訊，以及有關 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]其他必要條件、限制和建議的詳細資訊，請參閱《 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="3a919-115">For information about feature support and for information about additional prerequisites, restrictions, and recommendations for [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
## <a name="dialog-options"></a><span data-ttu-id="3a919-116">對話方塊選項</span><span class="sxs-lookup"><span data-stu-id="3a919-116">Dialog Options</span></span>  
 <span data-ttu-id="3a919-117">**Windows 容錯移轉叢集名稱**</span><span class="sxs-lookup"><span data-stu-id="3a919-117">**Windows failover cluster name**</span></span>  
 <span data-ttu-id="3a919-118">顯示本機電腦為其節點之 WSFC 叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="3a919-118">Displays the name of the WSFC cluster in which the local computer is a node.</span></span>  
  
 <span data-ttu-id="3a919-119">**啟用 AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="3a919-119">**Enable AlwaysOn Availability Groups**</span></span>  
 <span data-ttu-id="3a919-120">使用此核取方塊，在這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上啟用或停用 AlwaysOn 可用性群組，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3a919-120">Use this check box to enable or disable AlwaysOn Availability Groups on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], as follows:</span></span>  
  
-   <span data-ttu-id="3a919-121">如果此核取方塊是空的，表示 AlwaysOn 可用性群組目前停用。</span><span class="sxs-lookup"><span data-stu-id="3a919-121">If this check box is empty, AlwaysOn Availability Groups is currently disabled.</span></span> <span data-ttu-id="3a919-122">若要啟用 AlwaysOn 可用性群組，請選取此核取方塊，按一下 **[確定]**，然後手動重新開機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="3a919-122">To enable AlwaysOn Availability Groups, select this check box, click **OK**, and manually restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
-   <span data-ttu-id="3a919-123">如果已選取此核取方塊，表示 AlwaysOn 可用性群組目前啟用。</span><span class="sxs-lookup"><span data-stu-id="3a919-123">If this check box is already selected, AlwaysOn Availability Groups is currently enabled.</span></span> <span data-ttu-id="3a919-124">若要停用 AlwaysOn 可用性群組，請取消核取核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3a919-124">To disable AlwaysOn Availability Groups, uncheck the check box and click **OK**.</span></span> <span data-ttu-id="3a919-125">這樣伺服器執行個體就會重新啟動。</span><span class="sxs-lookup"><span data-stu-id="3a919-125">This causes the server instance to restart.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="3a919-126">停用 AlwaysOn 可用性群組之後，您應該從伺服器執行個體中移除任何本機可用性複本。</span><span class="sxs-lookup"><span data-stu-id="3a919-126">After disabling AlwaysOn Availability Groups, you should remove any local availability replicas from the server instance.</span></span> <span data-ttu-id="3a919-127">如果移除指定可用性群組的最後一個複本，同時也應該移除此群組。</span><span class="sxs-lookup"><span data-stu-id="3a919-127">If you remove the last replica of a given availability group, you should also remove the group.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="3a919-128">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="3a919-128">UI element list</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a919-129">如需有關停用 AlwaysOn 可用性群組之後的後續動作資訊，以及有關如何建立及設定可用性群組的詳細資訊，請參閱《[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="3a919-129">For more information about follow up after you disable AlwaysOn Availability Groups and for information about how to create and configure availability groups, see [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
