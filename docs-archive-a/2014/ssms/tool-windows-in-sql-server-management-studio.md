---
title: SQL Server Management Studio 中的工具視窗 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], tool windows
- tool windows [SQL Server Management Studio]
ms.assetid: d3be5062-234c-43a8-8d47-cce111dd3c25
author: stevestein
ms.author: sstein
ms.openlocfilehash: c3cc4c44e00e4c16a6211086b16861f3e9233357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686728"
---
# <a name="tool-windows-in-sql-server-management-studio"></a><span data-ttu-id="092e7-102">SQL Server Management Studio 中的工具視窗</span><span class="sxs-lookup"><span data-stu-id="092e7-102">Tool Windows in SQL Server Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="092e7-103">提供了許多功能強大的工具視窗，讓您可以在不同的開發及管理階段中使用。</span><span class="sxs-lookup"><span data-stu-id="092e7-103">provides many powerful tool windows for all phases of development and administration.</span></span> <span data-ttu-id="092e7-104">有些工具適用於所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 元件，有些工具只適用於特定元件。</span><span class="sxs-lookup"><span data-stu-id="092e7-104">Some tools can be used on any [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] component, and others are for certain components only.</span></span> <span data-ttu-id="092e7-105">下表指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的所有元件都能使用的工具。</span><span class="sxs-lookup"><span data-stu-id="092e7-105">The following table identifies the tools that can be used for all components of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="092e7-106">**工具**</span><span class="sxs-lookup"><span data-stu-id="092e7-106">**Tool**</span></span>|<span data-ttu-id="092e7-107">**目的**</span><span class="sxs-lookup"><span data-stu-id="092e7-107">**Purpose**</span></span>|  
|[<span data-ttu-id="092e7-108">物件總管</span><span class="sxs-lookup"><span data-stu-id="092e7-108">Object Explorer</span></span>](object/object-explorer.md)|<span data-ttu-id="092e7-109">瀏覽伺服器、建立和尋找物件、管理資料來源，以及檢視記錄。</span><span class="sxs-lookup"><span data-stu-id="092e7-109">Browse servers, create and locate objects, manage data sources, and view logs.</span></span> <span data-ttu-id="092e7-110">此工具可從 [檢視]  功能表加以存取。</span><span class="sxs-lookup"><span data-stu-id="092e7-110">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="092e7-111">方案總管</span><span class="sxs-lookup"><span data-stu-id="092e7-111">Solution Explorer</span></span>](solution/solution-explorer.md)|<span data-ttu-id="092e7-112">儲存和組織稱為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 指令碼之專案中的指令碼和相關連接資訊。</span><span class="sxs-lookup"><span data-stu-id="092e7-112">Store and organize scripts and related connection information in projects called [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Scripts.</span></span> <span data-ttu-id="092e7-113">您可以將許多 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 指令碼儲存成方案，當指令碼隨著時間而進展時，您可以利用原始檔控制來管理它們。</span><span class="sxs-lookup"><span data-stu-id="092e7-113">You can store several [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Scripts as Solutions and use source control to manage scripts as they evolve over time.</span></span> <span data-ttu-id="092e7-114">此工具可從 [檢視]  功能表加以存取。</span><span class="sxs-lookup"><span data-stu-id="092e7-114">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="092e7-115">範本總管</span><span class="sxs-lookup"><span data-stu-id="092e7-115">Template Explorer</span></span>](template/template-explorer.md)|<span data-ttu-id="092e7-116">根據現有的範本來建立查詢。</span><span class="sxs-lookup"><span data-stu-id="092e7-116">Create queries based on existing templates.</span></span> <span data-ttu-id="092e7-117">您也可以建立您的自訂查詢，或變更現有的範本來配合您的狀況。</span><span class="sxs-lookup"><span data-stu-id="092e7-117">You can also create your custom queries or alter the existing templates to fit your scenarios.</span></span> <span data-ttu-id="092e7-118">此工具可從 [檢視]  功能表加以存取。</span><span class="sxs-lookup"><span data-stu-id="092e7-118">This tool is accessed from the **View** menu.</span></span>|  
|[<span data-ttu-id="092e7-119">動態說明</span><span class="sxs-lookup"><span data-stu-id="092e7-119">Dynamic Help</span></span>](sql-server-management-studio-ssms.md)|<span data-ttu-id="092e7-120">在您按一下元件或類型程式碼時，顯示一份相關說明主題的清單。</span><span class="sxs-lookup"><span data-stu-id="092e7-120">Show a list of related Help topics as you click on a component or type code.</span></span>|  
  
 <span data-ttu-id="092e7-121">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的各項工具能夠協同運作。</span><span class="sxs-lookup"><span data-stu-id="092e7-121">The tools in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] work together.</span></span> <span data-ttu-id="092e7-122">例如，您可以：</span><span class="sxs-lookup"><span data-stu-id="092e7-122">For example, you can:</span></span>  
  
-   <span data-ttu-id="092e7-123">利用物件總管來註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="092e7-123">Register a server with Object Explorer.</span></span>  
  
-   <span data-ttu-id="092e7-124">開啟一個從物件總管連接特定資料庫的 [SQL 編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="092e7-124">Open a SQL Editor window connected to a specific database from Object Explorer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092e7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="092e7-125">See Also</span></span>  
 [<span data-ttu-id="092e7-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="092e7-126">Use SQL Server Management Studio</span></span>](../database-engine/use-sql-server-management-studio.md)  
  
  
