---
title: 設定資料庫引擎執行個體 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 84e36fcb-2c78-48e8-8e4b-bf784a3ee557
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: af7408ff66d1f0e41369ba095ce51ea590d316e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607097"
---
# <a name="configure-database-engine-instances-sql-server"></a><span data-ttu-id="edca0-102">設定 Database Engine 執行個體 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="edca0-102">Configure Database Engine Instances (SQL Server)</span></span>
  <span data-ttu-id="edca0-103">每個 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體都必須設定成符合針對執行個體所裝載之資料庫定義的效能和可用性需求。</span><span class="sxs-lookup"><span data-stu-id="edca0-103">Each instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] must be configured to meet the performance and availability requirements defined for the databases hosted by the instance.</span></span> <span data-ttu-id="edca0-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 包含的組態選項可控制如資源使用狀況等行為，或是如稽核或觸發程序遞迴等功能的可用性。</span><span class="sxs-lookup"><span data-stu-id="edca0-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] includes configuration options that control behaviors such as resource usage and the availability of features such as auditing or trigger recursion.</span></span>  
  
## <a name="instance-configuration"></a><span data-ttu-id="edca0-105">執行個體組態</span><span class="sxs-lookup"><span data-stu-id="edca0-105">Instance Configuration</span></span>  
 <span data-ttu-id="edca0-106">將資料庫部署至實際執行環境時，通常會有服務等級合約 (SLA) 定義資料庫所需效能層級和資料庫所需可用性層級這類區域。</span><span class="sxs-lookup"><span data-stu-id="edca0-106">When a database is deployed into production there is often a service level agreement (SLA) defining areas such as the levels of performance required from the database and the required availability level of the database.</span></span> <span data-ttu-id="edca0-107">SLA 的條款通常會驅動執行個體的組態需求。</span><span class="sxs-lookup"><span data-stu-id="edca0-107">The terms of the SLA typically drive configuration requirements for the instance.</span></span>  
  
 <span data-ttu-id="edca0-108">執行個體通常是在安裝之後立即進行設定。</span><span class="sxs-lookup"><span data-stu-id="edca0-108">An instance is usually configured immediately after it has been installed.</span></span> <span data-ttu-id="edca0-109">初始組態通常是透過規劃要部署至執行個體之資料庫類型的 SLA 需求所決定。</span><span class="sxs-lookup"><span data-stu-id="edca0-109">The initial configuration is usually determined by the SLA requirements of the types of databases planned to be deployed to the instance.</span></span> <span data-ttu-id="edca0-110">部署資料庫之後，資料庫管理員會監視執行個體的效能，並在效能標準顯示執行個體不符合 SLA 需求時，視需要調整組態設定。</span><span class="sxs-lookup"><span data-stu-id="edca0-110">After the databases have been deployed, the database administrators monitor the performance of the instance and adjust the configuration settings as needed if the performance metrics show the instance is not meeting the SLA requirements.</span></span>  
  
## <a name="configuration-tasks"></a><span data-ttu-id="edca0-111">組態工作</span><span class="sxs-lookup"><span data-stu-id="edca0-111">Configuration Tasks</span></span>  
  
|<span data-ttu-id="edca0-112">工作描述</span><span class="sxs-lookup"><span data-stu-id="edca0-112">Task Description</span></span>|<span data-ttu-id="edca0-113">主題</span><span class="sxs-lookup"><span data-stu-id="edca0-113">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="edca0-114">描述各種執行個體組態選項以及如何檢視或變更這些選項。</span><span class="sxs-lookup"><span data-stu-id="edca0-114">Describes the various instance configuration options and how to view or change these options.</span></span>|[<span data-ttu-id="edca0-115">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="edca0-115">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)|  
|<span data-ttu-id="edca0-116">描述如何檢視及設定執行個體中新資料和記錄檔的預設位置。</span><span class="sxs-lookup"><span data-stu-id="edca0-116">Describes how to view and configure the default locations of new data and log files in the instance.</span></span>|[<span data-ttu-id="edca0-117">檢視或變更資料及記錄檔的預設位置 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="edca0-117">View or Change the Default Locations for Data and Log Files &#40;SQL Server Management Studio&#41;</span></span>](view-or-change-the-default-locations-for-data-and-log-files.md)|  
|<span data-ttu-id="edca0-118">描述如何設定 SQL Server 使用軟體 NUMA。</span><span class="sxs-lookup"><span data-stu-id="edca0-118">Describes how to configure SQL Server to use soft-NUMA.</span></span>|[<span data-ttu-id="edca0-119">將 SQL Server 設定為使用軟體 NUMA &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="edca0-119">Configure SQL Server to Use Soft-NUMA &#40;SQL Server&#41;</span></span>](soft-numa-sql-server.md)|  
|<span data-ttu-id="edca0-120">描述如何將 TCP/IP 通訊埠對應到非統一記憶體存取 (NUMA) 節點相似性。</span><span class="sxs-lookup"><span data-stu-id="edca0-120">Describes how to map a TCP/IP port to non-uniform memory access (NUMA) node affinity.</span></span>|[<span data-ttu-id="edca0-121">將 TCP/IP 通訊埠對應到 NUMA 節點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="edca0-121">Map TCP IP Ports to NUMA Nodes &#40;SQL Server&#41;</span></span>](map-tcp-ip-ports-to-numa-nodes-sql-server.md)|  
|<span data-ttu-id="edca0-122">描述如何啟用 Windows 鎖定記憶體中的分頁原則。</span><span class="sxs-lookup"><span data-stu-id="edca0-122">Describes how to enable the Windows Lock Pages In Memory policy.</span></span> <span data-ttu-id="edca0-123">此原則決定哪些帳戶可以使用處理序將資料保留在實體記憶體中，以防止系統將資料傳送到磁碟上的虛擬記憶體。</span><span class="sxs-lookup"><span data-stu-id="edca0-123">This policy determines which accounts can use a process to keep data in physical memory, preventing the system from paging the data to virtual memory on disk.</span></span>|[<span data-ttu-id="edca0-124">啟用鎖定記憶體分頁選項 &#40;Windows&#41;</span><span class="sxs-lookup"><span data-stu-id="edca0-124">Enable the Lock Pages in Memory Option &#40;Windows&#41;</span></span>](enable-the-lock-pages-in-memory-option-windows.md)|  
  
## <a name="see-also"></a><span data-ttu-id="edca0-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edca0-125">See Also</span></span>  
 [<span data-ttu-id="edca0-126">Database Engine 執行個體 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="edca0-126">Database Engine Instances &#40;SQL Server&#41;</span></span>](database-engine-instances-sql-server.md)  
  
  
