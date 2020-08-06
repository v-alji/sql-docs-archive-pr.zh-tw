---
title: 使用 SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Management Studio [SQL Server]
- Enterprise Manager (See SQL Server Management Studio [Analysis Services])
- SQL Server Management Studio [SQL Server], about SQL Server Management Studio
ms.assetid: f289e978-14ca-46ef-9e61-e1fe5fd593be
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fed75ae8d4a1cfba7fb890a5b0b9c159c13366f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585542"
---
# <a name="use-sql-server-management-studio"></a><span data-ttu-id="16deb-102">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16deb-102">Use SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="16deb-103">(SSMS) 是一個整合式環境，可用於存取、設定、管理、管理及開發的所有元件 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="16deb-103">(SSMS) is an integrated environment for accessing, configuring, managing, administering, and developing all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="16deb-104">SSMS 利用許多豐富的指令碼編輯器來組合一群非常廣泛的圖形工具，使所有開發人員和管理員 (不管他們的技術水準如何) 都能夠存取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="16deb-104">SSMS combines a broad group of graphical tools with a number of rich script editors to provide access to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to developers and administrators of all skill levels.</span></span>  
  
 <span data-ttu-id="16deb-105">SSMS 將上一版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中所含的 Enterprise Manager、Query Analyzer 與 Analysis Manager 功能，結合在單一環境中。</span><span class="sxs-lookup"><span data-stu-id="16deb-105">SSMS combines the features of Enterprise Manager, Query Analyzer, and Analysis Manager, included in previous releases of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], into a single environment.</span></span> <span data-ttu-id="16deb-106">此外，SSMS 也能夠使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的所有元件，例如 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 及 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="16deb-106">In addition, SSMS works with all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] such as [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="16deb-107">開發人員會感到非常熟悉，資料庫管理員則會得到其中組合了簡單易用的圖形工具及非常豐富的指令碼功能的單一綜合性公用程式。</span><span class="sxs-lookup"><span data-stu-id="16deb-107">Developers get a familiar experience, and database administrators get a single comprehensive utility that combines easy-to-use graphical tools with rich scripting capabilities.</span></span>  
  
 <span data-ttu-id="16deb-108">從[Microsoft Developer Network](https://msdn.microsoft.com/library/dn434042.aspx)下載並安裝 SSMS。</span><span class="sxs-lookup"><span data-stu-id="16deb-108">Download and install SSMS from the [Microsoft Developer Network](https://msdn.microsoft.com/library/dn434042.aspx).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16deb-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="16deb-109">In This Section</span></span>  
 [<span data-ttu-id="16deb-110">SQL Server Management Studio 中的功能</span><span class="sxs-lookup"><span data-stu-id="16deb-110">Features in SQL Server Management Studio</span></span>](features-in-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-111">列出 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]所包含之非常豐富的功能集。</span><span class="sxs-lookup"><span data-stu-id="16deb-111">Lists the rich feature set included in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="16deb-112">SQL Server Management Studio 中的工具視窗</span><span class="sxs-lookup"><span data-stu-id="16deb-112">Tool Windows in SQL Server Management Studio</span></span>](../ssms/tool-windows-in-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-113">描述本身是 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]之元件的工具。</span><span class="sxs-lookup"><span data-stu-id="16deb-113">Describes the tools that are components of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="16deb-114">了解 SQL Server Management Studio 視窗管理</span><span class="sxs-lookup"><span data-stu-id="16deb-114">Understand SQL Server Management Studio Windows Management</span></span>](../ssms/understand-sql-server-management-studio-windows-management.md)  
 <span data-ttu-id="16deb-115">描述如何管理 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]所顯示的視窗。</span><span class="sxs-lookup"><span data-stu-id="16deb-115">Describes how to manage the windows displayed in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="16deb-116">利用 SQL Server Management Studio 管理伺服器</span><span class="sxs-lookup"><span data-stu-id="16deb-116">Administer Servers with SQL Server Management Studio</span></span>](../ssms/administer-servers-with-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-117">描述如何管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="16deb-117">Describes how to administer instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="16deb-118">從 SQL Server Management Studio 連接到任何 SQL Server 元件</span><span class="sxs-lookup"><span data-stu-id="16deb-118">Connect to Any SQL Server Component from SQL Server Management Studio</span></span>](../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-119">描述如何連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體，以及如何在沒有連接的情況下執行某些工作。</span><span class="sxs-lookup"><span data-stu-id="16deb-119">Describes how to connect to instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and how to perform certain tasks without a connection.</span></span>  
  
 [<span data-ttu-id="16deb-120">物件總管</span><span class="sxs-lookup"><span data-stu-id="16deb-120">Object Explorer</span></span>](../ssms/object/object-explorer.md)  
 <span data-ttu-id="16deb-121">描述物件總管的功能。</span><span class="sxs-lookup"><span data-stu-id="16deb-121">Describes the features of the Object Explorer.</span></span>  
  
 [<span data-ttu-id="16deb-122">SQL Server Management Studio 中的使用者協助</span><span class="sxs-lookup"><span data-stu-id="16deb-122">User Assistance in SQL Server Management Studio</span></span>](../ssms/user-assistance-in-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-123">描述如何在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中設定使用者輔助，如 [說明]。</span><span class="sxs-lookup"><span data-stu-id="16deb-123">Describes how to configure user assistance, such as Help, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="16deb-124">查詢與文字編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="16deb-124">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-125">描述如何利用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中非常豐富的編輯環境來編輯 [!INCLUDE[tsql](../includes/tsql-md.md)]、MDX、DMX 和 XML/A 指令碼。</span><span class="sxs-lookup"><span data-stu-id="16deb-125">Describes how to use the rich editing environment in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to edit [!INCLUDE[tsql](../includes/tsql-md.md)], MDX, DMX and XML/A scripts.</span></span>  
  
 [<span data-ttu-id="16deb-126">使用查詢編輯器編輯 SQLCMD 指令碼</span><span class="sxs-lookup"><span data-stu-id="16deb-126">Edit SQLCMD Scripts with Query Editor</span></span>](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)  
 <span data-ttu-id="16deb-127">描述在 SQLCMD 模式中使用查詢編輯器的功能和限制。</span><span class="sxs-lookup"><span data-stu-id="16deb-127">Describes the capabilities and limitations of using Query Editor in SQLCMD mode.</span></span>  
  
 [<span data-ttu-id="16deb-128">查詢編輯器中的色彩編碼</span><span class="sxs-lookup"><span data-stu-id="16deb-128">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
 <span data-ttu-id="16deb-129">描述在 [程式碼編輯器] 視窗中之色彩編碼的意義。</span><span class="sxs-lookup"><span data-stu-id="16deb-129">Describes the meaning of the color coding in Code Editor windows.</span></span>  
  
 [<span data-ttu-id="16deb-130">SQL Server Management Studio 鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="16deb-130">SQL Server Management Studio Keyboard Shortcuts</span></span>](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
 <span data-ttu-id="16deb-131">列出 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中所能使用的鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="16deb-131">Lists the keyboard shortcuts available in the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="16deb-132">自訂功能表與快速鍵</span><span class="sxs-lookup"><span data-stu-id="16deb-132">Customize Menus and Shortcut Keys</span></span>](../ssms/customize-menus-and-shortcut-keys.md)  
 <span data-ttu-id="16deb-133">描述如何建立自訂功能表和快速鍵。</span><span class="sxs-lookup"><span data-stu-id="16deb-133">Describes how to create custom menus and shortcuts.</span></span>  
  
 [<span data-ttu-id="16deb-134">解決方案 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="16deb-134">Solutions &#40;SQL Server Management Studio&#41;</span></span>](../ssms/solution/solutions-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-135">描述如何開發指令碼專案和方案。</span><span class="sxs-lookup"><span data-stu-id="16deb-135">Describes how to develop script projects and solutions.</span></span>  
  
 [<span data-ttu-id="16deb-136">範本總管</span><span class="sxs-lookup"><span data-stu-id="16deb-136">Template Explorer</span></span>](../ssms/template/template-explorer.md)  
 <span data-ttu-id="16deb-137">描述如何使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 範本及如何建立自訂範本。</span><span class="sxs-lookup"><span data-stu-id="16deb-137">Describes how to use the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] templates and how to create custom templates.</span></span>  
  
 [<span data-ttu-id="16deb-138">SQL Server Management Studio 中的屬性頁</span><span class="sxs-lookup"><span data-stu-id="16deb-138">Property Pages in SQL Server Management Studio</span></span>](../ssms/property-pages-in-sql-server-management-studio.md)  
 <span data-ttu-id="16deb-139">描述 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中的新屬性視窗配置。</span><span class="sxs-lookup"><span data-stu-id="16deb-139">Describes the new property window layout in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [<span data-ttu-id="16deb-140">Visual Database Tool 設計工具</span><span class="sxs-lookup"><span data-stu-id="16deb-140">Visual Database Tool Designers</span></span>](../ssms/visual-db-tools/visual-database-tool-designers.md)  
 <span data-ttu-id="16deb-141">描述您可以用來建立查詢、設計或修改資料庫結構，或是更新資料的 Visual Database Tools。</span><span class="sxs-lookup"><span data-stu-id="16deb-141">Describes the Visual Database Tools that you can use to create queries, design or modify a database structure, or update data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16deb-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16deb-142">See Also</span></span>  
 [<span data-ttu-id="16deb-143">檢視或變更伺服器屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="16deb-143">View or Change Server Properties &#40;SQL Server&#41;</span></span>](configure-windows/view-or-change-server-properties-sql-server.md)  
  
  
