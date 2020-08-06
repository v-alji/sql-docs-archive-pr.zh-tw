---
title: 利用 SQL Server Management Studio 管理伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], servers
- servers [SQL Server], administering
ms.assetid: 938bb035-e07a-4082-9f93-229d9feb6b06
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb2a6b9afba7d838cf71144f88ed7866c54ad796
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705922"
---
# <a name="administer-servers-with-sql-server-management-studio"></a><span data-ttu-id="1248a-102">利用 SQL Server Management Studio 管理伺服器</span><span class="sxs-lookup"><span data-stu-id="1248a-102">Administer Servers with SQL Server Management Studio</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="1248a-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]是一個豐富的整合式管理用戶端，專為符合 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 系統管理員的伺服器管理需求而設計。</span><span class="sxs-lookup"><span data-stu-id="1248a-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] is a rich, integrated administrative client designed to meet the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] administrator's server management requirements.</span></span> <span data-ttu-id="1248a-104">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中可以使用 [物件總管] 來完成管理工作，其中可以讓您連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 系列的任何伺服器，並以圖形方式瀏覽其內容。</span><span class="sxs-lookup"><span data-stu-id="1248a-104">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], administrative tasks are accomplished using Object Explorer, which allows you to connect to any server in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] family and graphically browse its contents.</span></span> <span data-ttu-id="1248a-105">伺服器可以是 [!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1248a-105">A server can be an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], or [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="1248a-106">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的工具元件包括已註冊的伺服器、物件總管、方案總管、範本總管、物件總管詳細資料頁面，以及文件視窗。</span><span class="sxs-lookup"><span data-stu-id="1248a-106">The tool components of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] include Registered Servers, Object Explorer, Solution Explorer, Template Explorer, the Object Explorer Details page, and the document window.</span></span> <span data-ttu-id="1248a-107">若要顯示工具，請在 [檢視]  功能表上按一下工具名稱。</span><span class="sxs-lookup"><span data-stu-id="1248a-107">To display a tool, on the **View** menu, click the tool name.</span></span> <span data-ttu-id="1248a-108">若要顯示查詢編輯器工具，請在工具列上按一下 [新增查詢]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="1248a-108">To display the Query Editor tool, click the **New Query** button on the toolbar.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1248a-109">依預設，不會加密 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之間的網路傳輸。</span><span class="sxs-lookup"><span data-stu-id="1248a-109">Network traffic between [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is unencrypted by default.</span></span> <span data-ttu-id="1248a-110">除非您已建立加密連接，否則，請勿在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 中使用機密資料 (包括密碼)。</span><span class="sxs-lookup"><span data-stu-id="1248a-110">Do not work with sensitive data (including passwords) in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] unless you have established an encrypted connection.</span></span> <span data-ttu-id="1248a-111">如需詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="1248a-111">For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).</span></span>  
  
 <span data-ttu-id="1248a-112">請利用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1248a-112">Use [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="1248a-113">註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="1248a-113">Register servers.</span></span>  
  
-   <span data-ttu-id="1248a-114">連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]、[!INCLUDE[ssAS](../includes/ssas-md.md)]、[!INCLUDE[ssRS](../includes/ssrs.md)] 或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1248a-114">Connect to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)], [!INCLUDE[ssAS](../includes/ssas-md.md)], [!INCLUDE[ssRS](../includes/ssrs.md)], or [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
-   <span data-ttu-id="1248a-115">設定伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="1248a-115">Configure server properties.</span></span>  
  
-   <span data-ttu-id="1248a-116">管理資料庫和 [!INCLUDE[ssAS](../includes/ssas-md.md)] 物件，如 Cube、維度和組件。</span><span class="sxs-lookup"><span data-stu-id="1248a-116">Manage database and [!INCLUDE[ssAS](../includes/ssas-md.md)] objects such as cubes, dimensions, and assemblies.</span></span>  
  
-   <span data-ttu-id="1248a-117">建立物件，如資料庫、資料表、Cube、資料庫使用者和登入。</span><span class="sxs-lookup"><span data-stu-id="1248a-117">Create objects, such as databases, tables, cubes, database users, and logins.</span></span>  
  
-   <span data-ttu-id="1248a-118">管理檔案和檔案群組。</span><span class="sxs-lookup"><span data-stu-id="1248a-118">Manage files and filegroups.</span></span>  
  
-   <span data-ttu-id="1248a-119">附加或卸離資料庫。</span><span class="sxs-lookup"><span data-stu-id="1248a-119">Attach or detach databases.</span></span>  
  
-   <span data-ttu-id="1248a-120">啟動指令碼工具。</span><span class="sxs-lookup"><span data-stu-id="1248a-120">Launch scripting tools.</span></span>  
  
-   <span data-ttu-id="1248a-121">管理安全性。</span><span class="sxs-lookup"><span data-stu-id="1248a-121">Manage security.</span></span>  
  
-   <span data-ttu-id="1248a-122">檢視系統記錄。</span><span class="sxs-lookup"><span data-stu-id="1248a-122">View system logs.</span></span>  
  
-   <span data-ttu-id="1248a-123">監視目前的活動。</span><span class="sxs-lookup"><span data-stu-id="1248a-123">Monitor current activity.</span></span>  
  
-   <span data-ttu-id="1248a-124">設定複寫。</span><span class="sxs-lookup"><span data-stu-id="1248a-124">Configure replication.</span></span>  
  
-   <span data-ttu-id="1248a-125">管理全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="1248a-125">Manage full-text indexes.</span></span>  
  
 <span data-ttu-id="1248a-126">若要啟動和停止 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent，請使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 組態管理員。</span><span class="sxs-lookup"><span data-stu-id="1248a-126">To start and stop [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1248a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1248a-127">See Also</span></span>  
 <span data-ttu-id="1248a-128">[使用 SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="1248a-128">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="1248a-129">檢視或變更伺服器屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1248a-129">View or Change Server Properties &#40;SQL Server&#41;</span></span>](../database-engine/configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
