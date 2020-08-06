---
title: SSIS 套件基本概念 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package requirements
ms.assetid: b0c86c35-e3d3-4724-9a96-4087e9d74bf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7c58ddc13b5c149b84fa550f312782b02786d062
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703149"
---
# <a name="ssis-package-essentials"></a><span data-ttu-id="caec1-102">SSIS 封裝基本功能</span><span class="sxs-lookup"><span data-stu-id="caec1-102">SSIS Package Essentials</span></span>
  <span data-ttu-id="caec1-103">封裝是實作 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 功能以擷取、轉換和載入資料的物件。</span><span class="sxs-lookup"><span data-stu-id="caec1-103">A package is the object that implements [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] functionality to extract, transform, and load data.</span></span> <span data-ttu-id="caec1-104">您可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 中使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]設計師來建立封裝。</span><span class="sxs-lookup"><span data-stu-id="caec1-104">You create a package by using the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="caec1-105">您也可以執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 匯入和匯出精靈或 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 連接專案精靈來建立封裝。</span><span class="sxs-lookup"><span data-stu-id="caec1-105">You can also create a package by running the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard or the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Connections Project Wizard.</span></span> <span data-ttu-id="caec1-106">如需詳細資訊，請在 SSIS 設計師的[SQL Server Data Tools 中建立封裝](create-packages-in-sql-server-data-tools.md)和匯[入專案嚮導](../../2014/integration-services/import-project-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="caec1-106">For more information, [Create Packages in SQL Server Data Tools](create-packages-in-sql-server-data-tools.md) in SSIS Designer and [Import Project Wizard](../../2014/integration-services/import-project-wizard.md).</span></span>  
  
 <span data-ttu-id="caec1-107">基本的套件包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="caec1-107">A basic package includes the following elements:</span></span>  
  
 <span data-ttu-id="caec1-108">**控制流程元素**</span><span class="sxs-lookup"><span data-stu-id="caec1-108">**Control flow elements**</span></span>  
 <span data-ttu-id="caec1-109">這些必要的元素可執行多種功能、提供結構，並控制元素執行的順序。</span><span class="sxs-lookup"><span data-stu-id="caec1-109">These required elements perform various functions, provide structure, and control the order in which elements run.</span></span> <span data-ttu-id="caec1-110">主要的控制流程元素為工作、容器和優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="caec1-110">The main control flow elements are tasks, containers, and precedence constraints.</span></span> <span data-ttu-id="caec1-111">封裝中至少要有一個控制流程元素。</span><span class="sxs-lookup"><span data-stu-id="caec1-111">There must be at least one control flow element in a package.</span></span>  
  
 <span data-ttu-id="caec1-112">如需詳細資訊，請參閱 [控制流程](control-flow/control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="caec1-112">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>  
  
 <span data-ttu-id="caec1-113">**資料流程元素**</span><span class="sxs-lookup"><span data-stu-id="caec1-113">**Data flow elements**</span></span>  
 <span data-ttu-id="caec1-114">這些選擇性的元素會擷取資料、修改資料並將資料載入資料來源。</span><span class="sxs-lookup"><span data-stu-id="caec1-114">These optional elements extract data, modify data, and load data into data sources.</span></span> <span data-ttu-id="caec1-115">主要資料流程元素為來源、轉換及目的地。</span><span class="sxs-lookup"><span data-stu-id="caec1-115">The main data flow elements are sources, transformations, and destinations.</span></span> <span data-ttu-id="caec1-116">封裝中不必有任何資料流程元素。</span><span class="sxs-lookup"><span data-stu-id="caec1-116">There does not have to be any data flow elements in package.</span></span>  
  
 <span data-ttu-id="caec1-117">如需詳細資訊，請參閱 [資料流程](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="caec1-117">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>  
  
 <span data-ttu-id="caec1-118">如需如何建立基本封裝的範例，請參閱[第1課：建立專案和基本封裝](lesson-1-create-a-project-and-basic-package-with-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="caec1-118">For an example of how to create a basic package, see [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="caec1-119">相關工作</span><span class="sxs-lookup"><span data-stu-id="caec1-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="caec1-120">在 SQL Server Data Tools 中建立套件</span><span class="sxs-lookup"><span data-stu-id="caec1-120">Create Packages in SQL Server Data Tools</span></span>](create-packages-in-sql-server-data-tools.md)  
  
-   [<span data-ttu-id="caec1-121">在控制流程中加入或刪除工作或容器</span><span class="sxs-lookup"><span data-stu-id="caec1-121">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [<span data-ttu-id="caec1-122">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="caec1-122">Set the Properties of a Task or Container</span></span>](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)  
  
-   [<span data-ttu-id="caec1-123">在資料流程中加入或刪除元件</span><span class="sxs-lookup"><span data-stu-id="caec1-123">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
## <a name="related-content"></a><span data-ttu-id="caec1-124">相關內容</span><span class="sxs-lookup"><span data-stu-id="caec1-124">Related Content</span></span>  
  
1.  <span data-ttu-id="caec1-125">MSDN.Microsoft.com 上的影片： [建立基本封裝 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=131023)</span><span class="sxs-lookup"><span data-stu-id="caec1-125">Video, [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023), on MSDN.Microsoft.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caec1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caec1-126">See Also</span></span>  
 <span data-ttu-id="caec1-127">[Integration Services &#40;SSIS&#41; 封裝](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="caec1-127">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="caec1-128">優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="caec1-128">Precedence Constraints</span></span>](control-flow/precedence-constraints.md)  
  
  
