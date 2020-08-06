---
title: 方案總管原始檔控制 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual SourceSafe
- SQL Server Management Studio [SQL Server], source control services
- source-controlled files [SQL Server]
- source controls [SQL Server Management Studio], services
- version control services [SQL Server]
- file source control services [SQL Server]
- VSS [Visual SourceSafe]
ms.assetid: 6373adb8-3d81-4945-a9fc-1d0d5799d29a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 46471ba8149c26f80e78006bc3a8befc2e81b416
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597987"
---
# <a name="solution-explorer-source-control"></a><span data-ttu-id="14e21-102">方案總管原始檔控制</span><span class="sxs-lookup"><span data-stu-id="14e21-102">Solution Explorer Source Control</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="14e21-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]方案總管可以整合到不同的原始檔控制系統中。</span><span class="sxs-lookup"><span data-stu-id="14e21-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Solution Explorer can be integrated into a separate source control system.</span></span> <span data-ttu-id="14e21-104">將方案或專案整合為原始檔控制系統之後，就可以控制專案中指令碼和查詢的檔案存取權和版本設定。</span><span class="sxs-lookup"><span data-stu-id="14e21-104">Once a solution or project is integrated into a source control system, you can control file access and versioning for the scripts and queries in your projects.</span></span>  
  
## <a name="solution-and-project-source-control"></a><span data-ttu-id="14e21-105">方案和專案原始檔控制</span><span class="sxs-lookup"><span data-stu-id="14e21-105">Solution and Project Source Control</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]  
  
 <span data-ttu-id="14e21-106">「原始檔控制」是指利用一段中央伺服器軟體來儲存和追蹤檔案版本及控制檔案存取動作的系統。</span><span class="sxs-lookup"><span data-stu-id="14e21-106">Source control refers to a system in which a central piece of server software stores and tracks file versions, and also controls access to files.</span></span> <span data-ttu-id="14e21-107">典型的原始檔控制系統包括一個原始檔控制提供者及兩個或更多原始檔控制用戶端。</span><span class="sxs-lookup"><span data-stu-id="14e21-107">A typical source control system includes a source control provider and two or more source control clients.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="14e21-108">可以與原始檔控制服務整合。</span><span class="sxs-lookup"><span data-stu-id="14e21-108">can be integrated with a source control service.</span></span> <span data-ttu-id="14e21-109">這表示此工具可用來做為您的原始檔控制提供者的用戶端。</span><span class="sxs-lookup"><span data-stu-id="14e21-109">This means you can use the tool as a client for your source control provider.</span></span> <span data-ttu-id="14e21-110">在不離開環境的情況下，您很容易管理您的個別和團隊專案。</span><span class="sxs-lookup"><span data-stu-id="14e21-110">Without leaving the environment, you can manage your individual and team projects easily.</span></span> <span data-ttu-id="14e21-111">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 並未隨附原始檔控制提供者。</span><span class="sxs-lookup"><span data-stu-id="14e21-111">The source control provider is not included with [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
#### <a name="to-select-a-source-control-provider"></a><span data-ttu-id="14e21-112">若要選取原始檔控制提供者</span><span class="sxs-lookup"><span data-stu-id="14e21-112">To select a source control provider</span></span>  
  
1.  <span data-ttu-id="14e21-113">安裝原始檔控制提供者的用戶端部份。</span><span class="sxs-lookup"><span data-stu-id="14e21-113">Install the client portion of your source control provider.</span></span>  
  
2.  <span data-ttu-id="14e21-114">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]的 **[工具]** 功能表上，按一下 **[選項]**。</span><span class="sxs-lookup"><span data-stu-id="14e21-114">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="14e21-115">在 [**選項**] 對話方塊中，展開 [**原始檔控制**]，然後按一下 [**外掛程式選取範圍]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="14e21-115">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
4.  <span data-ttu-id="14e21-116">在 [**目前的原始檔控制外掛程式]** 方塊中，選取原始檔控制外掛程式。</span><span class="sxs-lookup"><span data-stu-id="14e21-116">In the **Current source control plug-in** box, select the source control plug-in.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14e21-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="14e21-117">In This Section</span></span>  
  
|<span data-ttu-id="14e21-118">主題</span><span class="sxs-lookup"><span data-stu-id="14e21-118">Topic</span></span>|<span data-ttu-id="14e21-119">描述</span><span class="sxs-lookup"><span data-stu-id="14e21-119">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="14e21-120">原始檔控制基本概念</span><span class="sxs-lookup"><span data-stu-id="14e21-120">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)|<span data-ttu-id="14e21-121">定義基本的原始檔控制專有名詞，以及說明使用原始檔控制服務如何使專案受益。</span><span class="sxs-lookup"><span data-stu-id="14e21-121">Defines basic source control terminology, and explains how your project can benefit from using source control services.</span></span>|  
|[<span data-ttu-id="14e21-122">將方案與專案加入原始檔控制</span><span class="sxs-lookup"><span data-stu-id="14e21-122">Add Solutions and Projects to Source Control</span></span>](../../2014/database-engine/add-solutions-and-projects-to-source-control.md)|<span data-ttu-id="14e21-123">說明如何利用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境，將方案和專案加入原始檔控制中。</span><span class="sxs-lookup"><span data-stu-id="14e21-123">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to add solutions and projects to source control.</span></span>|  
|[<span data-ttu-id="14e21-124">從原始檔控制中開啟方案和專案</span><span class="sxs-lookup"><span data-stu-id="14e21-124">Open Solutions and Projects from Source Control</span></span>](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)|<span data-ttu-id="14e21-125">說明如何利用 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境來開啟接受原始檔控制的方案和專案。</span><span class="sxs-lookup"><span data-stu-id="14e21-125">Explains how to use the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to open source-controlled solutions and projects.</span></span>|  
|[<span data-ttu-id="14e21-126">管理簽出</span><span class="sxs-lookup"><span data-stu-id="14e21-126">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)|<span data-ttu-id="14e21-127">說明如何從原始檔控制中簽出方案和檔案。</span><span class="sxs-lookup"><span data-stu-id="14e21-127">Explains how to check out solutions and files from source control.</span></span>|  
|[<span data-ttu-id="14e21-128">管理簽入</span><span class="sxs-lookup"><span data-stu-id="14e21-128">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)|<span data-ttu-id="14e21-129">說明如何將方案和檔案簽入原始檔控制中。</span><span class="sxs-lookup"><span data-stu-id="14e21-129">Explains how to check solutions and files into source control.</span></span>|  
|[<span data-ttu-id="14e21-130">設定及擷取版本資訊</span><span class="sxs-lookup"><span data-stu-id="14e21-130">Set and Retrieve Version Information</span></span>](../../2014/database-engine/set-and-retrieve-version-information.md)|<span data-ttu-id="14e21-131">說明如何擷取專案或項目的記錄、擷取項目的本機副本，或比較兩個項目版本。</span><span class="sxs-lookup"><span data-stu-id="14e21-131">Explains how to retrieve the history of a project or item, retrieve a local copy of an item, or compare two item versions.</span></span>|  
|||  
  
## <a name="see-also"></a><span data-ttu-id="14e21-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14e21-132">See Also</span></span>  
 <span data-ttu-id="14e21-133">[方案總管](../ssms/solution/solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="14e21-133">[Solution Explorer](../ssms/solution/solution-explorer.md) </span></span>  
 <span data-ttu-id="14e21-134">[解決方案 &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="14e21-134">[Solutions &#40;SQL Server Management Studio&#41;](../ssms/sql-server-management-studio-ssms.md) </span></span>  
 <span data-ttu-id="14e21-135">[專案 &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="14e21-135">[Projects &#40;SQL Server Management Studio&#41;](../ssms/solution/projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="14e21-136">管理方案和專案的檔案</span><span class="sxs-lookup"><span data-stu-id="14e21-136">Files That Manage Solutions and Projects</span></span>](../ssms/solution/files-that-manage-solutions-and-projects.md)  
  
  
