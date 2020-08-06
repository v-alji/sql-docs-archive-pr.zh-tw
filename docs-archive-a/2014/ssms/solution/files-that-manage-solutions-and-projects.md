---
title: 管理方案和專案的檔案 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: stevestein
ms.author: sstein
ms.openlocfilehash: c94f1f853263c3969961de91ec95b921f5d78ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700561"
---
# <a name="files-that-manage-solutions-and-projects"></a><span data-ttu-id="30922-102">管理方案和專案的檔案</span><span class="sxs-lookup"><span data-stu-id="30922-102">Files That Manage Solutions and Projects</span></span>
  <span data-ttu-id="30922-103">本主題描述 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 特定的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="30922-103">This topic describes the file types that are specific to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="30922-104">依預設，所有方案及其專案都建立在 \My Documents\SQL Server Management Studio Projects 中。</span><span class="sxs-lookup"><span data-stu-id="30922-104">By default, all solutions and their projects are created in \My Documents\SQL Server Management Studio Projects.</span></span>  
  
## <a name="management-studio-solution-files"></a><span data-ttu-id="30922-105">Management Studio 方案檔</span><span class="sxs-lookup"><span data-stu-id="30922-105">Management Studio Solution Files</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="30922-106">使用不同於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 或 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="30922-106">uses different file types than [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio.</span></span> <span data-ttu-id="30922-107">這代表您無法在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Visual Studio 中開啟 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="30922-107">This means you cannot open a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or in Visual Studio.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="30922-108">方案檔可讓方案總管顯示一個用以管理檔案的圖形介面。</span><span class="sxs-lookup"><span data-stu-id="30922-108">solution files allow Solution Explorer to display a graphical interface for managing your files.</span></span>  
  
|<span data-ttu-id="30922-109">分機</span><span class="sxs-lookup"><span data-stu-id="30922-109">Extension</span></span>|<span data-ttu-id="30922-110">檔案類型</span><span class="sxs-lookup"><span data-stu-id="30922-110">File type</span></span>|<span data-ttu-id="30922-111">描述</span><span class="sxs-lookup"><span data-stu-id="30922-111">Description</span></span>|<span data-ttu-id="30922-112">建立者</span><span class="sxs-lookup"><span data-stu-id="30922-112">Created by</span></span>|  
|---------------|---------------|-----------------|----------------|  
|<span data-ttu-id="30922-113">.ssmssln</span><span class="sxs-lookup"><span data-stu-id="30922-113">.ssmssln</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="30922-114">方案物件</span><span class="sxs-lookup"><span data-stu-id="30922-114">Solution Object</span></span>|<span data-ttu-id="30922-115">提供參考 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 專案、專案項目和方案磁碟位置的環境</span><span class="sxs-lookup"><span data-stu-id="30922-115">Provides the environment with references to the location on disk of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] projects, project items, and solution</span></span>|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a><span data-ttu-id="30922-116">Management Studio 專案檔</span><span class="sxs-lookup"><span data-stu-id="30922-116">Management Studio Project Files</span></span>  
 <span data-ttu-id="30922-117">專案依照方案包含方案檔 (用來管理方案中的物件) 的相同方式來包含專案檔。</span><span class="sxs-lookup"><span data-stu-id="30922-117">In the same way that solutions contain solution files that manage objects in a solution, projects contain project files.</span></span> <span data-ttu-id="30922-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 針對專案所建立之專案檔的類型，會隨著用來建立專案的範本而不同。</span><span class="sxs-lookup"><span data-stu-id="30922-118">The type of project file that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] creates for a project depends on the template used to create the project.</span></span> <span data-ttu-id="30922-119">下表說明針對每個專案所建立之檔案的類型。</span><span class="sxs-lookup"><span data-stu-id="30922-119">The following table describes the type of file created for each project.</span></span>  
  
|<span data-ttu-id="30922-120">分機</span><span class="sxs-lookup"><span data-stu-id="30922-120">Extension</span></span>|<span data-ttu-id="30922-121">專案範本</span><span class="sxs-lookup"><span data-stu-id="30922-121">Project template</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="30922-122">.ssmssqlproj</span><span class="sxs-lookup"><span data-stu-id="30922-122">.ssmssqlproj</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="30922-123">指令碼專案</span><span class="sxs-lookup"><span data-stu-id="30922-123">Scripts Project</span></span>|  
|<span data-ttu-id="30922-124">.ssmsasproj</span><span class="sxs-lookup"><span data-stu-id="30922-124">.ssmsasproj</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="30922-125">指令碼專案</span><span class="sxs-lookup"><span data-stu-id="30922-125">Scripts Project</span></span>|  
  
## <a name="location-of-solution-level-files"></a><span data-ttu-id="30922-126">方案層級檔案的位置</span><span class="sxs-lookup"><span data-stu-id="30922-126">Location of Solution-Level Files</span></span>  
 <span data-ttu-id="30922-127">依預設，方案層級的檔案是建立在方案所建立的第一個專案之實體目錄中。</span><span class="sxs-lookup"><span data-stu-id="30922-127">By default, solution-level files are created in the physical directory of the first project that is created with the solution.</span></span> <span data-ttu-id="30922-128">您可以建立一個方案來指定方案的目錄，也可以在建立新專案時指定目錄。</span><span class="sxs-lookup"><span data-stu-id="30922-128">You can specify a directory for the solution by creating a solution, or you can specify the directory when you create a new project.</span></span>  
  
 <span data-ttu-id="30922-129">如果目錄結構類似於 [方案總管] 所顯示的邏輯結構，專案和方案檔會比較容易尋找，團隊的其他開發人員也比較容易共用它們。</span><span class="sxs-lookup"><span data-stu-id="30922-129">If you have a directory structure similar to the logical structure shown in Solution Explorer, project and solution files are easier to locate and share with other developers on a team.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30922-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30922-130">See Also</span></span>  
 <span data-ttu-id="30922-131">[以編碼管理檔案](manage-files-with-encoding.md) </span><span class="sxs-lookup"><span data-stu-id="30922-131">[Manage Files with Encoding](manage-files-with-encoding.md) </span></span>  
 <span data-ttu-id="30922-132">[其他檔案](miscellaneous-files.md) </span><span class="sxs-lookup"><span data-stu-id="30922-132">[Miscellaneous Files](miscellaneous-files.md) </span></span>  
 <span data-ttu-id="30922-133">[方案總管](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="30922-133">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="30922-134">[解決方案 &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="30922-134">[Solutions &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="30922-135">[專案 &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="30922-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="30922-136">方案總管原始檔控制</span><span class="sxs-lookup"><span data-stu-id="30922-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
