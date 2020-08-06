---
title: 使用 SQL Server Management Studio 建置資料庫專案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- scripts [SQL Server], database projects
- database projects [SQL Server]
- projects [SQL Server Management Studio], about projects
- projects [SQL Server Management Studio]
ms.assetid: c2e80045-894d-44cf-b65c-e547ed738947
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ddf3f61e69623716b2987c5c4d849398e822d18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584278"
---
# <a name="build-database-projects-by-using-sql-server-management-studio"></a><span data-ttu-id="edec7-102">使用 SQL Server Management Studio 建置資料庫專案</span><span class="sxs-lookup"><span data-stu-id="edec7-102">Build Database Projects by Using SQL Server Management Studio</span></span>
  <span data-ttu-id="edec7-103">資料庫指令碼專案是一組有組織的指令碼、連接資訊及範本，而且全都與資料庫或資料庫某一部分有所關聯。</span><span class="sxs-lookup"><span data-stu-id="edec7-103">A database script project is an organized set of scripts, connection information, and templates that are all associated with a database or one part of a database.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="edec7-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，可讓您在指令碼專案的內容中管理及設計 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="edec7-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for administering and designing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databases within the context of a script project.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="edec7-105">包含設計工具、編輯器、指南及精靈，可協助使用者開發、部署及維護資料庫。</span><span class="sxs-lookup"><span data-stu-id="edec7-105">includes designers, editors, guides and wizards to assist users in developing, deploying and maintaining databases.</span></span>  
  
## <a name="sql-server-management-studio"></a><span data-ttu-id="edec7-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="edec7-106">SQL Server Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="edec7-107">是一套系統管理工具，用以管理屬於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的元件。</span><span class="sxs-lookup"><span data-stu-id="edec7-107">is a suite of administrative tools for managing the components belonging to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="edec7-108">這個整合式環境可讓使用者執行各種工作，如備份資料、編輯查詢，以及自動執行單一介面內的一般功能。</span><span class="sxs-lookup"><span data-stu-id="edec7-108">This integrated environment allows users to perform a variety of tasks, such as backing up data, editing queries, and automating common functions within a single interface.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="edec7-109">包括下列工具：</span><span class="sxs-lookup"><span data-stu-id="edec7-109">includes the following tools:</span></span>  
  
-   <span data-ttu-id="edec7-110">程式碼編輯器是一個豐富的指令碼編輯器，用以撰寫及編輯指令碼。</span><span class="sxs-lookup"><span data-stu-id="edec7-110">Code Editor is a rich script editor for writing and editing scripts.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="edec7-111">提供四種版本的程式碼編輯器：適用於 [!INCLUDE[ssDE](../includes/ssde-md.md)] 指令碼的 [!INCLUDE[tsql](../includes/tsql-md.md)] 查詢編輯器、DMX 查詢編輯器、MDX 查詢編輯器及 XML/A 查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="edec7-111">provides four versions of the Code Editor; the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor for [!INCLUDE[tsql](../includes/tsql-md.md)] scripts, the DMX Query Editor, the MDX Query Editor, and the XML/A Query Editor.</span></span>  
  
-   <span data-ttu-id="edec7-112">物件總管，用以尋找、修改、執行屬於 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的物件，或撰寫該物件的指令碼。</span><span class="sxs-lookup"><span data-stu-id="edec7-112">Object Explorer for locating, modifying, scripting or running objects belonging to instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="edec7-113">範本總管，用以尋找範本及撰寫範本的指令碼。</span><span class="sxs-lookup"><span data-stu-id="edec7-113">Template Explorer for locating and scripting templates.</span></span>  
  
-   <span data-ttu-id="edec7-114">方案總管，用以組織相關的指令碼並將其儲存為專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="edec7-114">Solution Explorer for organizing and storing related scripts as parts of a project.</span></span>  
  
-   <span data-ttu-id="edec7-115">屬性視窗，用以顯示所選物件的目前屬性。</span><span class="sxs-lookup"><span data-stu-id="edec7-115">Properties Window for displaying the current properties of selected objects.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="edec7-116">藉由提供下列項目，支援有效率的工作程序：</span><span class="sxs-lookup"><span data-stu-id="edec7-116">supports efficient work processes by providing:</span></span>  
  
-   <span data-ttu-id="edec7-117">已中斷連接的存取。</span><span class="sxs-lookup"><span data-stu-id="edec7-117">Disconnected access.</span></span> <span data-ttu-id="edec7-118">您不需連接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體，即可撰寫及編輯指令碼。</span><span class="sxs-lookup"><span data-stu-id="edec7-118">You can write and edit scripts without connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="edec7-119">從任何對話方塊撰寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="edec7-119">Scripting from any dialog box.</span></span> <span data-ttu-id="edec7-120">您可以從任何對話方塊建立指令碼，以便可在建立指令碼之後加以讀取、修改及重複使用。</span><span class="sxs-lookup"><span data-stu-id="edec7-120">You can create a script from any dialog box so that you can read, modify, store and reuse the scripts after you create them.</span></span>  
  
-   <span data-ttu-id="edec7-121">非典型對話方塊。</span><span class="sxs-lookup"><span data-stu-id="edec7-121">Nonmodal dialog boxes.</span></span> <span data-ttu-id="edec7-122">當您存取 UI 對話方塊時，不需關閉此對話方塊，即可瀏覽 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的其他資源。</span><span class="sxs-lookup"><span data-stu-id="edec7-122">When you access a UI dialog box you can browse other resources in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] without closing the dialog box.</span></span>  
  
## <a name="solutions-and-script-projects"></a><span data-ttu-id="edec7-123">方案及指令碼專案</span><span class="sxs-lookup"><span data-stu-id="edec7-123">Solutions and Script Projects</span></span>  
 <span data-ttu-id="edec7-124">方案總管是用以儲存及重新開啟資料庫方案的公用程式。</span><span class="sxs-lookup"><span data-stu-id="edec7-124">Solution Explorer is a utility to store and reopen database solutions.</span></span> <span data-ttu-id="edec7-125">方案會組織相關的指令碼專案及檔案。</span><span class="sxs-lookup"><span data-stu-id="edec7-125">Solutions organize related script projects and files.</span></span> <span data-ttu-id="edec7-126">指令碼專案會儲存 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 指令碼檔案、SQL 範本、連接資訊以及其他檔案。</span><span class="sxs-lookup"><span data-stu-id="edec7-126">Script projects store [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] script files, SQL templates, connection information and other miscellaneous files.</span></span> <span data-ttu-id="edec7-127">當指令碼儲存到指令碼專案後，使用者可以：</span><span class="sxs-lookup"><span data-stu-id="edec7-127">When a script is saved in a script project, users are able to:</span></span>  
  
-   <span data-ttu-id="edec7-128">維護指令碼的版本控制。</span><span class="sxs-lookup"><span data-stu-id="edec7-128">Maintain version control on scripts.</span></span>  
  
-   <span data-ttu-id="edec7-129">利用指令碼儲存結果選項。</span><span class="sxs-lookup"><span data-stu-id="edec7-129">Store results options with a script.</span></span>  
  
-   <span data-ttu-id="edec7-130">在單一指令碼專案中組織相關的指令碼。</span><span class="sxs-lookup"><span data-stu-id="edec7-130">Organize related scripts in a single script project.</span></span>  
  
-   <span data-ttu-id="edec7-131">利用指令碼儲存連接資訊。</span><span class="sxs-lookup"><span data-stu-id="edec7-131">Save connection information with scripts.</span></span>  
  
 <span data-ttu-id="edec7-132">[方案總管] 為開發人員所適用的工具，他們會建立及重複使用與同一專案相關的指令碼。</span><span class="sxs-lookup"><span data-stu-id="edec7-132">Solution Explorer is a tool for developers who are creating and reusing scripts that are related to the same project.</span></span> <span data-ttu-id="edec7-133">如果稍後需要類似工作，您可以使用已儲存在專案中的指令碼群組。</span><span class="sxs-lookup"><span data-stu-id="edec7-133">If a similar task is required later, you can use group of scripts that were stored in a project.</span></span> <span data-ttu-id="edec7-134">如果曾經使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 來建立應用程式，則您應該對 [方案總管] 非常熟悉。</span><span class="sxs-lookup"><span data-stu-id="edec7-134">If you have created applications by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], you will find Solution Explorer very familiar.</span></span>  
  
 <span data-ttu-id="edec7-135">方案是由一或多個指令碼專案所組成。</span><span class="sxs-lookup"><span data-stu-id="edec7-135">A solution consists of one or more script projects.</span></span> <span data-ttu-id="edec7-136">專案是由一或多個指令碼或連接所組成。</span><span class="sxs-lookup"><span data-stu-id="edec7-136">A project consists of one or more scripts or connections.</span></span> <span data-ttu-id="edec7-137">專案也可包含非指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="edec7-137">A project may also include nonscript files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edec7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edec7-138">See Also</span></span>  
 <span data-ttu-id="edec7-139">[使用 SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="edec7-139">[Use SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="edec7-140">[查詢和文字編輯器 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="edec7-140">[Query and Text Editors &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="edec7-141">方案 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="edec7-141">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solution/solutions-sql-server-management-studio.md)  
  
  
