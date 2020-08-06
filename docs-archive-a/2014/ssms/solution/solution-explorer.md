---
title: 方案總管 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], solutions
- projects [SQL Server Management Studio], about projects
- SQL Server Management Studio [SQL Server], projects
- solutions [SQL Server Management Studio], about solutions
- SQL Server Management Studio [SQL Server], items
- items [SQL Server]
ms.assetid: 0df09843-0d4f-4925-bc6c-99265035a0c1
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa312f5e097fa1c59b9ba545709dc964a184c3f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594310"
---
# <a name="solution-explorer"></a><span data-ttu-id="b19a0-102">方案總管</span><span class="sxs-lookup"><span data-stu-id="b19a0-102">Solution Explorer</span></span>
  <span data-ttu-id="b19a0-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中 [方案總管] 窗格提供的容器稱為專案，可用來管理資料庫指令碼、查詢、資料連線和檔案等項目。</span><span class="sxs-lookup"><span data-stu-id="b19a0-103">The Solution Explorer pane in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides containers called projects for managing items such as database scripts, queries, data connections, and files.</span></span> <span data-ttu-id="b19a0-104">一個或多個彼此相關的專案會合併到稱為方案的容器。</span><span class="sxs-lookup"><span data-stu-id="b19a0-104">One or more projects that are related to each other can be combined in a container called a solution.</span></span>  
  
 <span data-ttu-id="b19a0-105">方案包括一個或多個專案，加上有助於將方案當做一個整體來定義的檔案和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b19a0-105">A solution includes one or more projects, plus files and metadata that help define the solution as a whole.</span></span> <span data-ttu-id="b19a0-106">專案是一組檔案，加上連接資訊等相關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b19a0-106">A project is a set of files, plus related metadata such as connection information.</span></span> <span data-ttu-id="b19a0-107">方案和專案包含代表建立資料庫方案時所需要之指令碼、查詢、連接資訊和檔案的項目。</span><span class="sxs-lookup"><span data-stu-id="b19a0-107">Solutions and projects contain items that represent the scripts, queries, connection information and files that you need to create your database solution.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="benefits-of-using-solutions"></a><span data-ttu-id="b19a0-108">使用方案的優點</span><span class="sxs-lookup"><span data-stu-id="b19a0-108">Benefits of Using Solutions</span></span>  
 <span data-ttu-id="b19a0-109">請利用這些容器來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b19a0-109">Use these containers to:</span></span>  
  
-   <span data-ttu-id="b19a0-110">實作查詢和指令碼的原始檔控制。</span><span class="sxs-lookup"><span data-stu-id="b19a0-110">Implement source control on queries and scripts.</span></span>  
  
-   <span data-ttu-id="b19a0-111">將方案的設定當做一個整體來管理，或管理個別專案的設定。</span><span class="sxs-lookup"><span data-stu-id="b19a0-111">Manage settings for your solution as a whole or for individual projects.</span></span>  
  
-   <span data-ttu-id="b19a0-112">處理檔案管理細節，同時將焦點集中在組成資料庫方案的項目。</span><span class="sxs-lookup"><span data-stu-id="b19a0-112">Handle the details of file management while you focus on items that make up your database solution.</span></span>  
  
-   <span data-ttu-id="b19a0-113">在各個專案中都未參考項目的情況下，加入對方案或方案中的多個專案有用的項目。</span><span class="sxs-lookup"><span data-stu-id="b19a0-113">Add items that are useful to multiple projects in the solution or to the solution without referencing the item in each project.</span></span>  
  
-   <span data-ttu-id="b19a0-114">處理與方案或專案無關的其他檔案。</span><span class="sxs-lookup"><span data-stu-id="b19a0-114">Work on miscellaneous files that are independent from solutions or projects.</span></span>  
  
 <span data-ttu-id="b19a0-115">專案所包含的項目會隨著專案類型和您是否使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]而不同。</span><span class="sxs-lookup"><span data-stu-id="b19a0-115">The items contained in projects depend on the project type and whether you are using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b19a0-116">相關工作</span><span class="sxs-lookup"><span data-stu-id="b19a0-116">Related Tasks</span></span>  
 <span data-ttu-id="b19a0-117">若要開始使用 SQL Server 方案，請使用下列主題：</span><span class="sxs-lookup"><span data-stu-id="b19a0-117">Use the following topics to get started with SQL Server Solutions:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b19a0-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="b19a0-118">**Description**</span></span>|<span data-ttu-id="b19a0-119">**主題**</span><span class="sxs-lookup"><span data-stu-id="b19a0-119">**Topic**</span></span>|  
|<span data-ttu-id="b19a0-120">描述如何收集方案中的一個或多個專案。</span><span class="sxs-lookup"><span data-stu-id="b19a0-120">Describes how to collect one or more projects in a solution.</span></span>|[<span data-ttu-id="b19a0-121">方案 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b19a0-121">Solutions &#40;SQL Server Management Studio&#41;</span></span>](solutions-sql-server-management-studio.md)|  
|<span data-ttu-id="b19a0-122">描述如何建立專案並加入指令碼和連接等項目。</span><span class="sxs-lookup"><span data-stu-id="b19a0-122">Describes how to create a project and add items like scripts and connections.</span></span>|[<span data-ttu-id="b19a0-123">專案 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b19a0-123">Projects &#40;SQL Server Management Studio&#41;</span></span>](projects-sql-server-management-studio.md)|  
|<span data-ttu-id="b19a0-124">描述如何將方案或個別專案整合到原始程式碼控制系統。</span><span class="sxs-lookup"><span data-stu-id="b19a0-124">Describes how to integrate solutions or individual projects into a source code control system.</span></span>|[<span data-ttu-id="b19a0-125">方案總管原始檔控制</span><span class="sxs-lookup"><span data-stu-id="b19a0-125">Solution Explorer Source Control</span></span>](../../database-engine/solution-explorer-source-control.md)|  
|<span data-ttu-id="b19a0-126">提供 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 用來管理方案和檔案之檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b19a0-126">Provides information about the files used by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to manage solutions and files.</span></span>|[<span data-ttu-id="b19a0-127">管理方案和專案的檔案</span><span class="sxs-lookup"><span data-stu-id="b19a0-127">Files That Manage Solutions and Projects</span></span>](files-that-manage-solutions-and-projects.md)|  
  
  
