---
title: Integration Services 工作 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Integration Services], tasks
- files [Integration Services], task options
- workflow tasks [Integration Services]
- Integration Services, tasks
- adding package tasks
- tasks [Integration Services], listed
- SSIS tasks
- SSIS, tasks
- control flow [Integration Services], tasks
- tasks [Integration Services]
- grouping tasks
- tasks [Integration Services], about tasks
- SQL Server Integration Services tasks
- data preparation tasks [Integration Services]
- directory operations [Integration Services]
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5fa58dec1e05a0333c295efc7f00a1d6df935792
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594626"
---
# <a name="integration-services-tasks"></a><span data-ttu-id="85bb6-102">Integration Services 工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-102">Integration Services Tasks</span></span>
  <span data-ttu-id="85bb6-103">工作為控制流程元素，用來定義封裝控制流程中所執行工作的單位。</span><span class="sxs-lookup"><span data-stu-id="85bb6-103">Tasks are control flow elements that define units of work that are performed in a package control flow.</span></span> <span data-ttu-id="85bb6-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件是由一或多項工作所組成。</span><span class="sxs-lookup"><span data-stu-id="85bb6-104">An [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package is made up of one or more tasks.</span></span> <span data-ttu-id="85bb6-105">如果封裝包含超過一項工作，則會在控制流程中按照優先順序條件約束連接並排列順序。</span><span class="sxs-lookup"><span data-stu-id="85bb6-105">If the package contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span>  
  
 <span data-ttu-id="85bb6-106">您也可以使用支援 COM 的程式設計語言 (例如 Visual Basic) 或 .NET 程式設計語言 (例如 C#) 撰寫自訂工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-106">You can also write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span>  
  
 <span data-ttu-id="85bb6-107">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中用於處理套件的圖形化工具，提供用來建立套件控制流程的設計介面，以及用來設定工作的自訂編輯器。</span><span class="sxs-lookup"><span data-stu-id="85bb6-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the graphical tool in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] for working with packages, provides the design surface for creating package control flow, and provides custom editors for configuring tasks.</span></span> <span data-ttu-id="85bb6-108">您也可以設計 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 物件模型的程式，以透過程式設計方式來建立套件。</span><span class="sxs-lookup"><span data-stu-id="85bb6-108">You can also program the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] object model to create packages programmatically.</span></span>  
  
## <a name="types-of-tasks"></a><span data-ttu-id="85bb6-109">工作的類型</span><span class="sxs-lookup"><span data-stu-id="85bb6-109">Types of Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="85bb6-110">包括下列工作類型。</span><span class="sxs-lookup"><span data-stu-id="85bb6-110">includes the following types of tasks.</span></span>  
  
 <span data-ttu-id="85bb6-111">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-111">Data Flow Task</span></span>  
 <span data-ttu-id="85bb6-112">執行資料流程以擷取資料、套用資料行層級轉換，以及載入資料的工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-112">The task that runs data flows to extract data, apply column level transformations, and load data.</span></span>  
  
 <span data-ttu-id="85bb6-113">資料準備工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-113">Data Preparation Tasks</span></span>  
 <span data-ttu-id="85bb6-114">這些工作會執行下列程序：複製檔案和目錄、下載檔案和資料、執行 Web 方法、將作業套用到 XML 文件，以及分析要清除的資料。</span><span class="sxs-lookup"><span data-stu-id="85bb6-114">These tasks do the following processes: copy files and directories; download files and data; run Web methods; apply operations to XML documents; and profile data for cleansing.</span></span>  
  
 <span data-ttu-id="85bb6-115">工作流程工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-115">Workflow Tasks</span></span>  
 <span data-ttu-id="85bb6-116">與其他程序進行通訊以便執行封裝、執行程式或批次檔、在封裝之間傳送和接收訊息、傳送電子郵件、讀取 Windows Management Instrumentation (WMI) 資料，以及監看 WMI 事件的工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-116">The tasks that communicate with other processes to run packages, run programs or batch files, send and receive messages between packages, send e-mail messages, read Windows Management Instrumentation (WMI) data, and watch for WMI events.</span></span>  
  
 <span data-ttu-id="85bb6-117">SQL Server 工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-117">SQL Server Tasks</span></span>  
 <span data-ttu-id="85bb6-118">存取、複製、插入、刪除以及修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件和資料的工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-118">The tasks that access, copy, insert, delete, and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects and data.</span></span>  
  
 <span data-ttu-id="85bb6-119">指令碼工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-119">Scripting Tasks</span></span>  
 <span data-ttu-id="85bb6-120">使用指令碼擴充封裝功能的工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-120">The tasks that extend package functionality by using scripts.</span></span>  
  
 <span data-ttu-id="85bb6-121">Analysis Services 工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-121">Analysis Services Tasks</span></span>  
 <span data-ttu-id="85bb6-122">建立、修改、刪除以及處理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件的工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-122">The tasks that create, modify, delete, and process [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="85bb6-123">維護工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-123">Maintenance Tasks</span></span>  
 <span data-ttu-id="85bb6-124">執行管理功能如備份和壓縮 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫、重建和重新組織索引，以及執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 工作的工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-124">The tasks that perform administrative functions such as backing up and shrinking [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases, rebuilding and reorganizing indexes, and running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
 <span data-ttu-id="85bb6-125">自訂工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-125">Custom Tasks</span></span>  
 <span data-ttu-id="85bb6-126">此外，您可以使用支援 COM 的程式設計語言 (例如 Visual Basic) 或 .NET 程式設計語言 (例如 C#) 撰寫自訂工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-126">Additionally, you can write custom tasks using a programming language that supports COM, such as Visual Basic, or a .NET programming language, such as C#.</span></span> <span data-ttu-id="85bb6-127">如果您要在 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 中存取自訂工作，可為該工作建立及註冊使用者介面。</span><span class="sxs-lookup"><span data-stu-id="85bb6-127">If you want to access your custom task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can create and register a user interface for the task.</span></span> <span data-ttu-id="85bb6-128">如需詳細資訊，請參閱 [開發自訂工作](../extending-packages-custom-objects/task/developing-a-custom-task.md)。</span><span class="sxs-lookup"><span data-stu-id="85bb6-128">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="configuration-of-tasks"></a><span data-ttu-id="85bb6-129">設定工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-129">Configuration of Tasks</span></span>  
 <span data-ttu-id="85bb6-130">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝可包含單一工作，例如，在封裝執行時刪除資料庫資料表中各項記錄的執行 SQL 工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-130">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can contain a single task, such as an Execute SQL task that deletes records in a database table when the package runs.</span></span> <span data-ttu-id="85bb6-131">不過，封裝通常包含數項工作，且各項工作均設定為在封裝控制流程的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="85bb6-131">However, packages typically contain several tasks, and each task is set to run within the context of the package control flow.</span></span> <span data-ttu-id="85bb6-132">若事件處理常式為回應執行階段事件的工作流程，則亦可擁有工作。</span><span class="sxs-lookup"><span data-stu-id="85bb6-132">Event handlers, which are workflows that run in response to run-time events, can also have tasks.</span></span>  
  
 <span data-ttu-id="85bb6-133">如需使用 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 將工作加入封裝的詳細資訊，請參閱 [在控制流程中加入或刪除工作或容器](add-or-delete-a-task-or-a-container-in-a-control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="85bb6-133">For more information about adding a task to a package using [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>  
  
 <span data-ttu-id="85bb6-134">如需利用撰寫程式的方式將工作加入封裝的詳細資訊，請參閱 [以程式設計方式加入工作](../building-packages-programmatically/adding-tasks-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="85bb6-134">For more information about adding a task to a package programmatically, see [Adding Tasks Programmatically](../building-packages-programmatically/adding-tasks-programmatically.md).</span></span>  
  
 <span data-ttu-id="85bb6-135">每項工作均可使用 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 針對各項工作提供的自訂對話方塊，或 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中包括的 [屬性] 視窗另行設定。</span><span class="sxs-lookup"><span data-stu-id="85bb6-135">Each task can be configured individually using the custom dialog boxes for each task that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides, or the Properties window included in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="85bb6-136">封裝可包括多項相同類型的工作，例如六項執行 SQL 工作，而每項工作皆可分別設定。</span><span class="sxs-lookup"><span data-stu-id="85bb6-136">A package can include multiple tasks of the same type-for example, six Execute SQL tasks-and each task can be configured differently.</span></span> <span data-ttu-id="85bb6-137">如需詳細資訊，請參閱 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="85bb6-137">For more information, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="tasks-connections-and-groups"></a><span data-ttu-id="85bb6-138">工作連接和群組</span><span class="sxs-lookup"><span data-stu-id="85bb6-138">Tasks Connections and Groups</span></span>  
 <span data-ttu-id="85bb6-139">如果工作包含超過一項工作，則會在控制流程中按照優先順序條件約束連接並排列順序。</span><span class="sxs-lookup"><span data-stu-id="85bb6-139">If the task contains more than one task, they are connected and sequenced in the control flow by precedence constraints.</span></span> <span data-ttu-id="85bb6-140">如需詳細資訊，請參閱 [優先順序條件約束](precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="85bb6-140">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="85bb6-141">您可將多項工作設為群組，並做為單一工作單位執行，或於迴圈中重複。</span><span class="sxs-lookup"><span data-stu-id="85bb6-141">Tasks can be grouped together and performed as a single unit of work, or repeated in a loop.</span></span> <span data-ttu-id="85bb6-142">如需詳細資訊，請參閱 [Foreach 迴圈容器](foreach-loop-container.md)、 [For 迴圈容器](for-loop-container.md)和 [時序容器](sequence-container.md)。</span><span class="sxs-lookup"><span data-stu-id="85bb6-142">For more information, see [Foreach Loop Container](foreach-loop-container.md), [For Loop Container](for-loop-container.md), and [Sequence Container](sequence-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="85bb6-143">相關工作</span><span class="sxs-lookup"><span data-stu-id="85bb6-143">Related Tasks</span></span>  
 [<span data-ttu-id="85bb6-144">在控制流程中新增或刪除工作或容器</span><span class="sxs-lookup"><span data-stu-id="85bb6-144">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
  
