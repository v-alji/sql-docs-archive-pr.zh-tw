---
title: 子封裝的執行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- child packages
ms.assetid: ab0c09d7-ce2e-487d-a1ed-a4b5adb6cc01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4fa4fa7c523c55c595341c7aee6a530c5918a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698452"
---
# <a name="implementation-of-child-packages"></a><span data-ttu-id="449f3-102">子封裝的實作</span><span class="sxs-lookup"><span data-stu-id="449f3-102">Implementation of Child Packages</span></span>
  <span data-ttu-id="449f3-103">使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]實作負載平衡時，其他伺服器上會安裝子封裝，以充分利用可用的 CPU 或伺服器時間。</span><span class="sxs-lookup"><span data-stu-id="449f3-103">When you implement load balancing using [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], child packages are installed on other servers to take advantage of the available CPU or server time.</span></span> <span data-ttu-id="449f3-104">建立及執行子封裝需要下列步驟：</span><span class="sxs-lookup"><span data-stu-id="449f3-104">To create and run the child packages requires the following steps:</span></span>  
  
-   <span data-ttu-id="449f3-105">設計子封裝。</span><span class="sxs-lookup"><span data-stu-id="449f3-105">Designing the child packages.</span></span>  
  
-   <span data-ttu-id="449f3-106">將封裝移到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="449f3-106">Moving the packages to the remote server.</span></span>  
  
-   <span data-ttu-id="449f3-107">在包含執行子封裝之步驟的遠端伺服器上建立 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="449f3-107">Creating a SQL Server Agent Job on the remote server that contains a step that runs the child package.</span></span>  
  
-   <span data-ttu-id="449f3-108">測試及偵錯 SQL Server Agent 作業和子封裝。</span><span class="sxs-lookup"><span data-stu-id="449f3-108">Testing and debugging the SQL Server Agent Job and child packages.</span></span>  
  
 <span data-ttu-id="449f3-109">設計子封裝時，封裝的設計並無任何限制，您可以放入任何所需的功能。</span><span class="sxs-lookup"><span data-stu-id="449f3-109">When you design the child packages, the packages have no limitations in their design, and you can put in any functionality you desire.</span></span> <span data-ttu-id="449f3-110">但是，如果封裝會存取資料，您必須確定執行封裝的伺服器擁有資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="449f3-110">However, if the package accesses data, you must ensure that the server that runs the package has access to the data.</span></span>  
  
 <span data-ttu-id="449f3-111">若要識別執行子封裝的父封裝，請在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下 [方案總管] 中的封裝，然後按一下 **[進入點封裝]**。</span><span class="sxs-lookup"><span data-stu-id="449f3-111">To identify the parent package that executes child packages, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] right click the package in Solution Explorer and then click **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="449f3-112">子封裝設計完成之後，下一個步驟是將子封裝部署在遠端伺服器上。</span><span class="sxs-lookup"><span data-stu-id="449f3-112">After the child packages have been designed, the next step is to deploy them on the remote servers.</span></span>  
  
## <a name="moving-the-child-package-to-the-remote-instance"></a><span data-ttu-id="449f3-113">將子封裝移到遠端執行個體</span><span class="sxs-lookup"><span data-stu-id="449f3-113">Moving the Child Package to the Remote Instance</span></span>  
 <span data-ttu-id="449f3-114">有幾種方法可以將封裝移到其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="449f3-114">There are multiple ways to move packages to other servers.</span></span> <span data-ttu-id="449f3-115">建議的兩種方法為：</span><span class="sxs-lookup"><span data-stu-id="449f3-115">The two suggested methods are:</span></span>  
  
-   <span data-ttu-id="449f3-116">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]來匯出封裝。</span><span class="sxs-lookup"><span data-stu-id="449f3-116">Exporting packages by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="449f3-117">為包含想要部署之封裝的專案建立部署公用程式，然後執行「封裝安裝精靈」，將封裝安裝到檔案系統或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體，以部署封裝。</span><span class="sxs-lookup"><span data-stu-id="449f3-117">Deploying packages by building a deployment utility for the project that contains the packages you want to deploy, and then running the Package Installation Wizard to install the packages to the file system or to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="449f3-118">如需詳細資訊，請參閱[&#40;SSIS&#41;的封裝部署](packages/legacy-package-deployment-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="449f3-118">For more information, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>  
  
 <span data-ttu-id="449f3-119">您必須重複部署到想要使用的每一部遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="449f3-119">You must repeat the deployment to each remote server you want to use.</span></span>  
  
## <a name="creating-the-sql-server-agent-jobs"></a><span data-ttu-id="449f3-120">建立 SQL Server Agent 作業</span><span class="sxs-lookup"><span data-stu-id="449f3-120">Creating the SQL Server Agent Jobs</span></span>  
 <span data-ttu-id="449f3-121">將子封裝部署到各種伺服器之後，請在包含子封裝的每一部伺服器上建立一項 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="449f3-121">After the child packages have been deployed to the various servers, create a SQL Server Agent job on each server that contains a child package.</span></span> <span data-ttu-id="449f3-122">SQL Server Agent 作業包含一個在呼叫作業代理程式時執行子封裝的步驟。</span><span class="sxs-lookup"><span data-stu-id="449f3-122">The SQL Server Agent job contains a step that runs the child package when the job agent is called.</span></span> <span data-ttu-id="449f3-123">SQL Server Agent 作業不是排程作業；只有在父封裝呼叫這些作業時，它們才會執行子封裝。</span><span class="sxs-lookup"><span data-stu-id="449f3-123">The SQL Server Agent jobs are not scheduled jobs; they run the child packages only when they are called by the parent package.</span></span> <span data-ttu-id="449f3-124">傳回給父封裝的作業成功或失敗通知，反映的是 SQL Server Agent 作業的成功或失敗，以及是否已成功呼叫作業，而非子封裝成功與否或其是否已執行。</span><span class="sxs-lookup"><span data-stu-id="449f3-124">Notification of success or failure of the job back to the parent package reflects the success or failure of the SQL Server Agent job and whether it was called successfully, not the success or failure of the child package or whether it was executed.</span></span>  
  
## <a name="debugging-the-sql-server-agent-jobs-and-child-packages"></a><span data-ttu-id="449f3-125">偵錯 SQL Server Agent 作業和子封裝</span><span class="sxs-lookup"><span data-stu-id="449f3-125">Debugging the SQL Server Agent Jobs and Child Packages</span></span>  
 <span data-ttu-id="449f3-126">您可以使用下列其中一種方法來建立 SQL Server Agent 作業及其子封裝：</span><span class="sxs-lookup"><span data-stu-id="449f3-126">You can test the SQL Server Agent jobs and their child packages by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="449f3-127">在 SSIS 設計師中執行每個子封裝，方法是按一下 [ **Debug**] [  /  **啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="449f3-127">Running each child package in SSIS Designer, by clicking **Debug** / **Start Without Debugging**.</span></span>  
  
-   <span data-ttu-id="449f3-128">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]執行遠端電腦上的個別 SQL Server Agent 作業，以確定封裝執行無誤。</span><span class="sxs-lookup"><span data-stu-id="449f3-128">Running the individual SQL Server Agent job on the remote computer by using [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to make sure that the package runs.</span></span>  
  
 <span data-ttu-id="449f3-129">如需有關如何為您從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 作業執行的封裝進行疑難排解，請參閱 [支援知識庫中的](https://support.microsoft.com/kb/918760) 從 SQL Server Agent 作業步驟呼叫 SSIS 封裝時，SSIS 封裝未執行 [!INCLUDE[msCoName](../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="449f3-129">For information about how to troubleshoot packages that you run from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs, see [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760) in the [!INCLUDE[msCoName](../includes/msconame-md.md)] Support Knowledge Base.</span></span>  
  
 <span data-ttu-id="449f3-130">SQL Server Agent 會檢查 Proxy 的子系統存取權，而且每當作業步驟執行時，就會提供 Proxy 的存取權。</span><span class="sxs-lookup"><span data-stu-id="449f3-130">The SQL Server Agent checks subsystem access for a proxy and gives access to the proxy every time the job step runs.</span></span>  
  
 <span data-ttu-id="449f3-131">您可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中建立 Proxy。</span><span class="sxs-lookup"><span data-stu-id="449f3-131">You can create a proxy in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="449f3-132">相關工作</span><span class="sxs-lookup"><span data-stu-id="449f3-132">Related Tasks</span></span>  
  
-   [<span data-ttu-id="449f3-133">使用 SQL Server Management Studio 在 SSIS 伺服器上執行套件</span><span class="sxs-lookup"><span data-stu-id="449f3-133">Run a Package on the SSIS Server Using SQL Server Management Studio</span></span>](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a><span data-ttu-id="449f3-134">相關內容</span><span class="sxs-lookup"><span data-stu-id="449f3-134">Related Content</span></span>  
  
-   <span data-ttu-id="449f3-135">Blog 專案（SSIS）：在 andyleonard 上[存取父封裝中的變數](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/)。</span><span class="sxs-lookup"><span data-stu-id="449f3-135">Blog entry, [SSIS: Accessing variables in a parent package](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/), on andyleonard.blog.</span></span>  
  
-   <span data-ttu-id="449f3-136">[執行封裝](../integration-services/control-flow/execute-package-task.md)工作的文章。</span><span class="sxs-lookup"><span data-stu-id="449f3-136">Article, [Execute Package Task](../integration-services/control-flow/execute-package-task.md).</span></span>  
  
  
