---
title: 專案 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c13af859-ca66-4e43-b76a-0650ac6566c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8fed02e84b154a86788b350812ad8fd5137c14b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606022"
---
# <a name="projects-sql-server-management-studio"></a><span data-ttu-id="4297c-102">專案 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="4297c-102">Projects (SQL Server Management Studio)</span></span>
  <span data-ttu-id="4297c-103">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 專案是邏輯關聯之指令碼和檔案的集合，它們可以儲存在一起，以便進行資料庫的管理和開發。</span><span class="sxs-lookup"><span data-stu-id="4297c-103">A [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] project is a collection of logically related scripts and files that can be saved together for database administration and development.</span></span>  
  
## <a name="script-project-overview"></a><span data-ttu-id="4297c-104">指令碼專案概觀</span><span class="sxs-lookup"><span data-stu-id="4297c-104">Script Project Overview</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4297c-105">指令碼專案會顯示在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]的方案總管元件中。</span><span class="sxs-lookup"><span data-stu-id="4297c-105">script projects are displayed in the Solution Explorer component of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="4297c-106">指令碼專案可以包含零或多個專案檔。</span><span class="sxs-lookup"><span data-stu-id="4297c-106">A script project can contain zero or more project files.</span></span> <span data-ttu-id="4297c-107">您可以將專案加入方案中，或在方案內組合多個專案。</span><span class="sxs-lookup"><span data-stu-id="4297c-107">You can add a project to a solution or combine more than one project within a solution.</span></span>  
  
 <span data-ttu-id="4297c-108">專案可以包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="4297c-108">Projects can include the following:</span></span>  
  
-   <span data-ttu-id="4297c-109">**連接**。</span><span class="sxs-lookup"><span data-stu-id="4297c-109">**Connections**.</span></span> <span data-ttu-id="4297c-110">連接會保存在專案內，其中含有登入資訊、伺服器名稱、預設資料庫、慣用的通訊協定、驗證類型，以及連接屬性。</span><span class="sxs-lookup"><span data-stu-id="4297c-110">A connection, as persisted within a project, will contain login information, server name, default database, preferred protocol, authentication type, and connection properties.</span></span> <span data-ttu-id="4297c-111">連接資訊可以選擇性地隨著指令碼而一併儲存 (請參閱下文)。</span><span class="sxs-lookup"><span data-stu-id="4297c-111">Connection information may optionally be stored with a script (see below).</span></span>  
  
-   <span data-ttu-id="4297c-112">**SQLScripts**。</span><span class="sxs-lookup"><span data-stu-id="4297c-112">**SQLScripts**.</span></span> <span data-ttu-id="4297c-113">使用者常用的 SQL 指令碼。</span><span class="sxs-lookup"><span data-stu-id="4297c-113">Frequently used SQL scripts for the user.</span></span> <span data-ttu-id="4297c-114">按兩下專案內的 .sql 檔，會使 SQL 編輯器開啟所選的指令碼。</span><span class="sxs-lookup"><span data-stu-id="4297c-114">Double-clicking a .sql file within the project will cause the SQL Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="4297c-115">**MDX、DMX 和 XMLA 指令碼**。</span><span class="sxs-lookup"><span data-stu-id="4297c-115">**MDX, DMX, and XMLAScripts**.</span></span> <span data-ttu-id="4297c-116">使用者常用的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="4297c-116">Frequently used MDX scripts for the user.</span></span> <span data-ttu-id="4297c-117">按兩下專案內的 .mdx 檔，會使編輯器開啟所選的指令碼。</span><span class="sxs-lookup"><span data-stu-id="4297c-117">Double-clicking an .mdx file within the project will cause the Editor to open the selected script.</span></span>  
  
-   <span data-ttu-id="4297c-118">**其他**。不完全符合任何其他預設節點類型的檔案，如包含專案目標的文字檔，可以使用這個資料夾。</span><span class="sxs-lookup"><span data-stu-id="4297c-118">**Misc**. This folder can be used for files that do not neatly fit into any of the other default node types, such as a text file that contains the project objectives.</span></span>  
  
 <span data-ttu-id="4297c-119">專案也可以整合為一個原始程式碼控制系統。</span><span class="sxs-lookup"><span data-stu-id="4297c-119">Projects can also be integrated into a source code control system.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-from-a-script-project"></a><span data-ttu-id="4297c-120">從指令碼專案連接到 SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="4297c-120">Connecting to an Instance of SQL Server from a Script Project</span></span>  
 <span data-ttu-id="4297c-121">指令碼專案可包含指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="4297c-121">A script project may contain connections to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4297c-122">按一下該連接，就可以連接到專案中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4297c-122">You can connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in a project by clicking the connection.</span></span> <span data-ttu-id="4297c-123">此時會開啟一個 [SQL 指令碼] 視窗，這個視窗會連接到您選取的連接所定義的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4297c-123">This will open an SQL Script window that is connected to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defined in the connection you selected.</span></span> <span data-ttu-id="4297c-124">如果您利用採取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的連接來開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 MDX 指令碼，在啟動編輯器及載入指令碼之後，系統會利用 [連接到 SQL Server]  對話方塊來提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="4297c-124">If you open a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or MDX script with a connection that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authentication, you will be prompted for the password using the **Connect to SQL Server** dialog box after the Editor has been opened and the script loaded.</span></span>  
  
 <span data-ttu-id="4297c-125">對應視窗關閉之後，連接也會關閉。</span><span class="sxs-lookup"><span data-stu-id="4297c-125">The connection will be closed after the corresponding window is closed.</span></span>  
  
 <span data-ttu-id="4297c-126">若要修改有關連接的資訊，請使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="4297c-126">To modify information about a connection, use the properties window in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="project-tasks"></a><span data-ttu-id="4297c-127">專案工作</span><span class="sxs-lookup"><span data-stu-id="4297c-127">Project Tasks</span></span>  
  
|<span data-ttu-id="4297c-128">工作描述</span><span class="sxs-lookup"><span data-stu-id="4297c-128">Task Description</span></span>|<span data-ttu-id="4297c-129">主題</span><span class="sxs-lookup"><span data-stu-id="4297c-129">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="4297c-130">描述如何在方案中建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="4297c-130">Describes how to create a new project in a solution.</span></span>|[<span data-ttu-id="4297c-131">建立專案</span><span class="sxs-lookup"><span data-stu-id="4297c-131">Create a Project</span></span>](create-a-project.md)|  
|<span data-ttu-id="4297c-132">描述如何將現有的專案加入方案中。</span><span class="sxs-lookup"><span data-stu-id="4297c-132">Describes how to add an existing project to a solution.</span></span>|[<span data-ttu-id="4297c-133">將現有專案加入方案中</span><span class="sxs-lookup"><span data-stu-id="4297c-133">Add an Existing Project to a Solution</span></span>](add-an-existing-project-to-a-solution.md)|  
|<span data-ttu-id="4297c-134">描述如何變更儲存專案檔案的預設位置。</span><span class="sxs-lookup"><span data-stu-id="4297c-134">Describes how to change the default location at which project files are saved.</span></span>|[<span data-ttu-id="4297c-135">變更專案的預設位置</span><span class="sxs-lookup"><span data-stu-id="4297c-135">Change the Default Location for Projects</span></span>](change-the-default-location-for-projects.md)|  
|<span data-ttu-id="4297c-136">描述如何檢視專案的目前屬性。</span><span class="sxs-lookup"><span data-stu-id="4297c-136">Describes how to view the current properties for a project.</span></span>|[<span data-ttu-id="4297c-137">檢視專案屬性</span><span class="sxs-lookup"><span data-stu-id="4297c-137">View Project Properties</span></span>](view-project-properties.md)|  
|<span data-ttu-id="4297c-138">描述如何將新的項目 (例如連接或指令碼檔案) 加入專案中。</span><span class="sxs-lookup"><span data-stu-id="4297c-138">Describes how to add new items, such as connections or script files, to a project.</span></span>|[<span data-ttu-id="4297c-139">將新項目加入專案</span><span class="sxs-lookup"><span data-stu-id="4297c-139">Add New Items to a Project</span></span>](add-new-items-to-a-project.md)|  
|<span data-ttu-id="4297c-140">描述如何建立查詢的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="4297c-140">Describes how to establish the connection information for a query.</span></span>|[<span data-ttu-id="4297c-141">建立查詢與專案中連接的關聯性</span><span class="sxs-lookup"><span data-stu-id="4297c-141">Associate a Query with a Connection in a Project</span></span>](associate-a-query-with-a-connection-in-a-project.md)|  
|<span data-ttu-id="4297c-142">描述如何變更查詢的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="4297c-142">Describes how to change the connection information for a query.</span></span>|[<span data-ttu-id="4297c-143">變更與查詢相關聯的連接</span><span class="sxs-lookup"><span data-stu-id="4297c-143">Change the Connection Associated with a Query</span></span>](change-the-connection-associated-with-a-query.md)|  
|<span data-ttu-id="4297c-144">描述如何變更連接屬性。</span><span class="sxs-lookup"><span data-stu-id="4297c-144">Describes how to change connection properties.</span></span>|[<span data-ttu-id="4297c-145">檢視或變更專案中連接的屬性</span><span class="sxs-lookup"><span data-stu-id="4297c-145">View or Change the Properties of a Connection in a Project</span></span>](view-or-change-the-properties-of-a-connection-in-a-project.md)|  
  
## <a name="see-also"></a><span data-ttu-id="4297c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4297c-146">See Also</span></span>  
 <span data-ttu-id="4297c-147">[方案總管](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="4297c-147">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="4297c-148">[解決方案 &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="4297c-148">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="4297c-149">方案總管原始檔控制</span><span class="sxs-lookup"><span data-stu-id="4297c-149">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
