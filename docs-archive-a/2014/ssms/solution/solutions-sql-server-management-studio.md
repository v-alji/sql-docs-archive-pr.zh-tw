---
title: 方案 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- solutions [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- scripts [SQL Server], SQL Server Management Studio
ms.assetid: d06a8a05-7201-4055-8cf3-21bcb4e82c25
author: stevestein
ms.author: sstein
ms.openlocfilehash: 836d3b3002d72541ad88ae55eac6d951530e0ca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594308"
---
# <a name="solutions-sql-server-management-studio"></a><span data-ttu-id="078ba-102">方案 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="078ba-102">Solutions (SQL Server Management Studio)</span></span>
  <span data-ttu-id="078ba-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 方案是一個或多個相關專案的集合。</span><span class="sxs-lookup"><span data-stu-id="078ba-103">A [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution is a collection of one or more related projects.</span></span> <span data-ttu-id="078ba-104">專案是開發人員用來組織相關檔案 (例如常用管理指令碼的集合) 的容器。</span><span class="sxs-lookup"><span data-stu-id="078ba-104">Projects are containers that developers use to organize related files, such as sets of commonly used administration scripts.</span></span>  
  
## <a name="solution-overview"></a><span data-ttu-id="078ba-105">方案概觀</span><span class="sxs-lookup"><span data-stu-id="078ba-105">Solution Overview</span></span>  
 <span data-ttu-id="078ba-106">您可以使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 做為 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]的指令碼開發平台。</span><span class="sxs-lookup"><span data-stu-id="078ba-106">You can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] as a script development platform for [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="078ba-107">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 程式碼編輯器可用來開發關聯式和多維資料庫的指令碼和查詢，以及將相關指令碼和查詢都收集至專案中。</span><span class="sxs-lookup"><span data-stu-id="078ba-107">Use the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] code editors to develop scripts and queries for relational and multidimensional databases, and collect related scripts and queries together in projects.</span></span>  
  
 <span data-ttu-id="078ba-108">專案可以包含：</span><span class="sxs-lookup"><span data-stu-id="078ba-108">Projects can contain:</span></span>  
  
-   <span data-ttu-id="078ba-109">實作實際執行程序的查詢和指令碼。</span><span class="sxs-lookup"><span data-stu-id="078ba-109">Queries and scripts that implement production processes.</span></span>  
  
-   <span data-ttu-id="078ba-110">查詢和指令碼所使用的連接資訊和檔案。</span><span class="sxs-lookup"><span data-stu-id="078ba-110">Connection information and files used by the queries and scripts.</span></span>  
  
 <span data-ttu-id="078ba-111">一個或多個相關的專案可以合併為一個方案。</span><span class="sxs-lookup"><span data-stu-id="078ba-111">One or more related projects can be combined in a solution.</span></span> <span data-ttu-id="078ba-112">使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的 [方案總管] 窗格，就可以管理方案和專案。</span><span class="sxs-lookup"><span data-stu-id="078ba-112">Solutions and projects can be managed by using the Solution Explorer pane in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="078ba-113">方案和專案可以整合為一個 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe (VSS) 資料庫或其他協力廠商原始檔控制提供者，以便追蹤開發的變更及管理生命週期。</span><span class="sxs-lookup"><span data-stu-id="078ba-113">Solutions and projects can be integrated into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe (VSS) database or other third-party source control providers, for development change tracking and life-cycle management.</span></span>  
  
## <a name="solution-tasks"></a><span data-ttu-id="078ba-114">方案工作</span><span class="sxs-lookup"><span data-stu-id="078ba-114">Solution Tasks</span></span>  
  
|<span data-ttu-id="078ba-115">工作描述</span><span class="sxs-lookup"><span data-stu-id="078ba-115">Task Description</span></span>|<span data-ttu-id="078ba-116">主題</span><span class="sxs-lookup"><span data-stu-id="078ba-116">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="078ba-117">描述如何建立新方案，然後使用新方案來包含一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="078ba-117">Describes how to create a new solution that can then be used to contain one or more projects.</span></span>|[<span data-ttu-id="078ba-118">建立新方案</span><span class="sxs-lookup"><span data-stu-id="078ba-118">Create a New Solution</span></span>](create-a-new-solution.md)|  
|<span data-ttu-id="078ba-119">描述如何在 [方案總管] 中開啟現有的方案。</span><span class="sxs-lookup"><span data-stu-id="078ba-119">Describes how to open an existing solution in Solution Explorer.</span></span>|[<span data-ttu-id="078ba-120">開啟現有的方案</span><span class="sxs-lookup"><span data-stu-id="078ba-120">Open an Existing Solution</span></span>](open-an-existing-solution.md)|  
|<span data-ttu-id="078ba-121">描述如何關閉方案。</span><span class="sxs-lookup"><span data-stu-id="078ba-121">Describes how to close a solution.</span></span>|[<span data-ttu-id="078ba-122">關閉方案</span><span class="sxs-lookup"><span data-stu-id="078ba-122">Close a Solution</span></span>](close-a-solution.md)|  
|<span data-ttu-id="078ba-123">描述如何刪除方案。</span><span class="sxs-lookup"><span data-stu-id="078ba-123">Describes how to delete a solution.</span></span>|[<span data-ttu-id="078ba-124">刪除方案</span><span class="sxs-lookup"><span data-stu-id="078ba-124">Delete a Solution</span></span>](delete-a-solution.md)|  
|<span data-ttu-id="078ba-125">描述如何複製專案之間的項目。</span><span class="sxs-lookup"><span data-stu-id="078ba-125">Describes how to copy items between projects.</span></span>|[<span data-ttu-id="078ba-126">複製方案中的項目</span><span class="sxs-lookup"><span data-stu-id="078ba-126">Copy Items in a Solution</span></span>](copy-items-in-a-solution.md)|  
|<span data-ttu-id="078ba-127">描述如何刪除專案中的項目或整個專案。</span><span class="sxs-lookup"><span data-stu-id="078ba-127">Describes how to delete items in a project, or an entire project.</span></span>|[<span data-ttu-id="078ba-128">移除或刪除項目或專案</span><span class="sxs-lookup"><span data-stu-id="078ba-128">Remove or Delete an Item or Project</span></span>](remove-or-delete-an-item-or-project.md)|  
|<span data-ttu-id="078ba-129">描述如何在方案的專案之間移動項目。</span><span class="sxs-lookup"><span data-stu-id="078ba-129">Describes how to move items between projects in a solution.</span></span>|[<span data-ttu-id="078ba-130">移動方案中的項目</span><span class="sxs-lookup"><span data-stu-id="078ba-130">Move Items in a Solution</span></span>](move-items-in-a-solution.md)|  
|<span data-ttu-id="078ba-131">描述如何重新命名方案或方案中的項目。</span><span class="sxs-lookup"><span data-stu-id="078ba-131">Describes how to rename a solution or the items in the solution.</span></span>|[<span data-ttu-id="078ba-132">重新命名方案和專案項目</span><span class="sxs-lookup"><span data-stu-id="078ba-132">Rename Solutions and Project Items</span></span>](rename-solutions-and-project-items.md)|  
  
## <a name="see-also"></a><span data-ttu-id="078ba-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="078ba-133">See Also</span></span>  
 <span data-ttu-id="078ba-134">[方案總管](solution-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="078ba-134">[Solution Explorer](solution-explorer.md) </span></span>  
 <span data-ttu-id="078ba-135">[專案 &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="078ba-135">[Projects &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="078ba-136">方案總管原始檔控制</span><span class="sxs-lookup"><span data-stu-id="078ba-136">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)  
  
  
