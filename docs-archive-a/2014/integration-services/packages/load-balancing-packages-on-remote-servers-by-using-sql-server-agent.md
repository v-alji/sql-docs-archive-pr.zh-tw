---
title: 使用 SQL Server Agent 在遠端伺服器上設定套件負載平衡 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- load-balancing [Integration Services]
- parent packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: 9281c5f8-8da3-4ae8-8142-53c5919a4cfe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea7b132d8cf86d2f211da25989df937d0db34ab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597195"
---
# <a name="load-balancing-packages-on-remote-servers-by-using-sql-server-agent"></a><span data-ttu-id="2fe7d-102">使用 SQL Server Agent 在遠端伺服器上設定封裝負載平衡</span><span class="sxs-lookup"><span data-stu-id="2fe7d-102">Load-Balancing Packages on Remote Servers by Using SQL Server Agent</span></span>
  <span data-ttu-id="2fe7d-103">當您必須執行許多封裝時，使用其他可用的伺服器會更方便。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-103">When many packages have to be run, it is convenient to use other servers that are available.</span></span> <span data-ttu-id="2fe7d-104">當封裝全都受單一父封裝控制時，使用其他伺服器來執行封裝的這種方法，即稱為負載平衡。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-104">This method of using other servers to run packages when the packages are all under the control of one parent package is called load balancing.</span></span> <span data-ttu-id="2fe7d-105">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，負載平衡是一種必須由套件擁有者建構的手動程序。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-105">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], load balancing is a manual procedure that must be architected by the owners of the packages.</span></span> <span data-ttu-id="2fe7d-106">伺服器並不會自動執行負載平衡。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-106">Load balancing is not performed automatically by the servers.</span></span> <span data-ttu-id="2fe7d-107">此外，遠端伺服器上執行的封裝也必須是完整的封裝，而不是其他封裝中的個別工作。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-107">Also, the packages that are run on the remote servers must be whole packages, not individual tasks in other packages.</span></span>  
  
 <span data-ttu-id="2fe7d-108">在下列狀況下，負載平衡非常有用：</span><span class="sxs-lookup"><span data-stu-id="2fe7d-108">Load balancing is useful in the following scenarios:</span></span>  
  
-   <span data-ttu-id="2fe7d-109">封裝可以同時執行。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-109">Packages can run at the same time.</span></span>  
  
-   <span data-ttu-id="2fe7d-110">封裝規模很大，而且如果連續執行，其執行時間可能超過允許處理的時間。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-110">Packages are large and, if run sequentially, can run longer than the time allowed for processing.</span></span>  
  
 <span data-ttu-id="2fe7d-111">管理員和架構設計師可以判斷使用其他伺服器進行處理是否能夠改善其處理效能。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-111">Administrators and architects can determine whether using additional servers for processing would benefit their processes.</span></span>  
  
## <a name="illustration-of-load-balancing"></a><span data-ttu-id="2fe7d-112">負載平衡的圖例說明</span><span class="sxs-lookup"><span data-stu-id="2fe7d-112">Illustration of Load-Balancing</span></span>  
 <span data-ttu-id="2fe7d-113">下圖顯示伺服器上的父封裝。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-113">The following diagram shows a parent package on a server.</span></span> <span data-ttu-id="2fe7d-114">此父封裝包含多項「執行 SQL 作業代理程式」工作。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-114">The parent package contains multiple Execute SQL Job Agent tasks.</span></span> <span data-ttu-id="2fe7d-115">父封裝中的每項工作都會呼叫遠端伺服器上的 SQL Server Agent。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-115">Each task in the parent package calls a SQL Server Agent on a remote server.</span></span> <span data-ttu-id="2fe7d-116">這些遠端伺服器包含 SQL Server Agent 作業，而這些作業都有一個步驟可以呼叫該伺服器上的封裝。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-116">Those remote servers contain SQL Server Agent jobs that include a step that calls a package on that server.</span></span>  
  
 <span data-ttu-id="2fe7d-117">![SSIS 負載平衡架構概觀](../media/loadbalancingoverview.gif "SSIS 負載平衡架構概觀")</span><span class="sxs-lookup"><span data-stu-id="2fe7d-117">![Overview of SSIS load balancing architecture](../media/loadbalancingoverview.gif "Overview of SSIS load balancing architecture")</span></span>  
  
 <span data-ttu-id="2fe7d-118">以這種架構設定負載平衡所需要的步驟並不是新的概念。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-118">The steps required for load balancing in this architecture are not new concepts.</span></span> <span data-ttu-id="2fe7d-119">相反地，負載平衡是利用現有概念和一般 SSIS 物件，以新的方式來達成。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-119">Instead, load balancing is achieved by using existing concepts and common SSIS objects in a new way.</span></span>  
  
## <a name="execution-of-packages-on-a-remote-instance-by-using-sql-server-agent"></a><span data-ttu-id="2fe7d-120">使用 SQL Server Agent 在遠端執行個體執行封裝</span><span class="sxs-lookup"><span data-stu-id="2fe7d-120">Execution of Packages on a Remote Instance by using SQL Server Agent</span></span>  
 <span data-ttu-id="2fe7d-121">在遠端封裝執行的基本架構中，中央封裝位於控制其他遠端封裝的 SQL Server 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-121">In the basic architecture for remote package execution, a central package resides on the instance of SQL Server that controls the other remote packages.</span></span> <span data-ttu-id="2fe7d-122">圖中顯示這個中央封裝，其名稱為 SSIS Parent。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-122">The diagram shows this central package, named the SSIS Parent.</span></span> <span data-ttu-id="2fe7d-123">這個父封裝所在的執行個體可控制執行子封裝之 SQL Server Agent 作業的執行。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-123">The instance where this parent package resides controls execution of the SQL Server Agent jobs that run the child packages.</span></span> <span data-ttu-id="2fe7d-124">這些子封裝的執行並未依照遠端伺服器上 SQL Server Agent 所控制的固定排程。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-124">The child packages are not run according to a fixed schedule controlled by the SQL Server Agent on the remote server.</span></span> <span data-ttu-id="2fe7d-125">而是在父封裝呼叫時由 SQL Server Agent 啟動這些子封裝，並於 SQL Server Agent 所在的同一個 SQL Server 執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-125">Instead, the child packages are started by the SQL Server Agent when called by the parent package and are run on the same instance of SQL Server on which the SQL Server Agent resides.</span></span>  
  
 <span data-ttu-id="2fe7d-126">您必須先設定父封裝和子封裝，並設定控制子封裝的 SQL Server Agent 作業，才能使用 SQL Server Agent 執行遠端封裝。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-126">Before you can run a remote package by using SQL Server Agent, you must configure the parent and child packages and set up the SQL Server Agent jobs that control the child packages.</span></span> <span data-ttu-id="2fe7d-127">下列章節提供有關如何建立、設定、執行及維護遠端伺服器上執行之封裝的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-127">The following sections provide more information about how to create, configure, run, and maintain packages that run on remote servers.</span></span> <span data-ttu-id="2fe7d-128">這個處理程序包含幾個步驟：</span><span class="sxs-lookup"><span data-stu-id="2fe7d-128">There are several steps to this process:</span></span>  
  
-   <span data-ttu-id="2fe7d-129">建立子封裝並將它們安裝在遠端伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-129">Creating the child packages and installing them on remote servers.</span></span>  
  
-   <span data-ttu-id="2fe7d-130">在要執行封裝的遠端執行個體上建立 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-130">Creating the SQL Server Agent jobs on the remote instances that will run the packages.</span></span>  
  
-   <span data-ttu-id="2fe7d-131">建立父封裝。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-131">Creating the parent package.</span></span>  
  
-   <span data-ttu-id="2fe7d-132">決定子封裝的記錄狀況。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-132">Determine the logging scenario for the child packages.</span></span>  
  
 <span data-ttu-id="2fe7d-133">下表提供引導您完成這個處理程序的主題連結。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-133">The following table provides links to topics that guide you through the process.</span></span>  
  
|<span data-ttu-id="2fe7d-134">主題</span><span class="sxs-lookup"><span data-stu-id="2fe7d-134">Topic</span></span>|<span data-ttu-id="2fe7d-135">描述</span><span class="sxs-lookup"><span data-stu-id="2fe7d-135">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2fe7d-136">子封裝的實作</span><span class="sxs-lookup"><span data-stu-id="2fe7d-136">Implementation of Child Packages</span></span>](../implementation-of-child-packages.md)|<span data-ttu-id="2fe7d-137">描述如何安裝封裝，以及建立 SQL Server Agent 作業來執行封裝。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-137">Describes the installation of packages, and creation of the SQL Server Agent jobs to run the packages.</span></span>|  
|[<span data-ttu-id="2fe7d-138">父封裝的實作</span><span class="sxs-lookup"><span data-stu-id="2fe7d-138">Implementation of the Parent Package</span></span>](../implementation-of-the-parent-package.md)|<span data-ttu-id="2fe7d-139">描述如何建立包含許多「執行 SQL Server Agent 作業」工作的父封裝。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-139">Describes the creation of the parent package that contains many Execute SQL Server Agent Job tasks.</span></span> <span data-ttu-id="2fe7d-140">每項工作將分別執行其中一個子封裝。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-140">Each task runs one of the child packages.</span></span>|  
|[<span data-ttu-id="2fe7d-141">遠端伺服器上負載平衡封裝的記錄</span><span class="sxs-lookup"><span data-stu-id="2fe7d-141">Logging for Load Balanced Packages on Remote Servers</span></span>](../logging-for-load-balanced-packages-on-remote-servers.md)|<span data-ttu-id="2fe7d-142">描述遠端封裝的記錄狀況。</span><span class="sxs-lookup"><span data-stu-id="2fe7d-142">Describes the logging scenario for the remote packages.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="2fe7d-143">相關工作</span><span class="sxs-lookup"><span data-stu-id="2fe7d-143">Related Tasks</span></span>  
 [<span data-ttu-id="2fe7d-144">使用 SQL Server Agent 排程封裝</span><span class="sxs-lookup"><span data-stu-id="2fe7d-144">Schedule a Package by using SQL Server Agent</span></span>](../schedule-a-package-by-using-sql-server-agent.md)  
  
  
