---
title: 父封裝的執行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- parent packages [Integration Services]
ms.assetid: d8f94830-fa27-4151-88df-cbdc6bf0fc80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04b99a2607e73bbcd612b43be1bdb30324a37e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592123"
---
# <a name="implementation-of-the-parent-package"></a><span data-ttu-id="41069-102">父封裝的實作</span><span class="sxs-lookup"><span data-stu-id="41069-102">Implementation of the Parent Package</span></span>
  <span data-ttu-id="41069-103">設定跨越各種伺服器之 SSIS 封裝的負載平衡時，在完成建立、部署子封裝，以及建立執行這些子封裝的遠端 SQL Server Agent 作業之後，下一個步驟就是建立父封裝。</span><span class="sxs-lookup"><span data-stu-id="41069-103">When load balancing SSIS packages across various servers, the next step after the child packages have been created, deployed, and remote SQL Server Agent Jobs created to run them, is to create the parent package.</span></span> <span data-ttu-id="41069-104">父封裝將包含許多「執行 SQL Server Agent 作業」工作，每一項工作負責呼叫執行其中一個子封裝的不同 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="41069-104">The parent package will contain many Execute SQL Server Agent Job tasks, each task responsible for calling a different SQL Server Agent job that runs one of the child packages.</span></span> <span data-ttu-id="41069-105">接著父封裝中的「執行 SQL Server Agent 作業」工作會執行各種 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="41069-105">The Execute SQL Server Agent Job tasks in the parent package in turn run the various SQL Server Agent jobs.</span></span> <span data-ttu-id="41069-106">父封裝中的每項工作都包含如何連接到遠端伺服器以及要在該伺服器上執行哪一項作業之類的資訊。</span><span class="sxs-lookup"><span data-stu-id="41069-106">Each task in the parent package contains information such as how to connect to the remote server and what job to run on that server.</span></span> <span data-ttu-id="41069-107">如需詳細資訊，請參閱 [Execute SQL Server Agent Job Task](control-flow/execute-sql-server-agent-job-task.md)。</span><span class="sxs-lookup"><span data-stu-id="41069-107">For more information, see [Execute SQL Server Agent Job Task](control-flow/execute-sql-server-agent-job-task.md).</span></span>  
  
 <span data-ttu-id="41069-108">若要識別執行子封裝的父封裝，請在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，以滑鼠右鍵按一下 [方案總管] 中的封裝，然後按一下 **[進入點封裝]**。</span><span class="sxs-lookup"><span data-stu-id="41069-108">To identify the parent package that executes child packages, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] right click the package in Solution Explorer and then click **Entry-point Package**.</span></span>  
  
## <a name="listing-child-packages"></a><span data-ttu-id="41069-109">列出子封裝</span><span class="sxs-lookup"><span data-stu-id="41069-109">Listing Child Packages</span></span>  
 <span data-ttu-id="41069-110">若您將包含父封裝及子封裝的專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器，可以檢視由父封裝執行的子封裝清單。</span><span class="sxs-lookup"><span data-stu-id="41069-110">If you deploy your project that contains a parent package and child package(s) to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you can view a list of the child packages that are executed by the parent package.</span></span> <span data-ttu-id="41069-111">當您執行父封裝時，會在 **中自動產生父封裝的 [概觀]**[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]報告。</span><span class="sxs-lookup"><span data-stu-id="41069-111">When you run the parent package, an **Overview** report for the parent package is automatically generated in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="41069-112">該告會列出父封裝中包含的執行封裝工作所執行之子封裝清單，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="41069-112">The report lists the child packages that were executed by the Execute Package task contained in the parent package, as shown in the following image.</span></span>  
  
 <span data-ttu-id="41069-113">![含有子套件清單的概觀報表](media/overviewreport-childpackagelisting.png "含有子套件清單的概觀報表")</span><span class="sxs-lookup"><span data-stu-id="41069-113">![Overview Report with list of child packages](media/overviewreport-childpackagelisting.png "Overview Report with list of child packages")</span></span>  
  
 <span data-ttu-id="41069-114">如需存取 [概觀] \*\*\*\* 報告的資訊，請參閱＜ [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="41069-114">For information about accessing the **Overview** report, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
## <a name="precedence-constraints-in-the-parent-package"></a><span data-ttu-id="41069-115">父封裝中的優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="41069-115">Precedence Constraints in the Parent Package</span></span>  
 <span data-ttu-id="41069-116">建立父封裝中「執行 SQL Server Agent 作業」工作之間的優先順序條件約束時，這些優先順序條件約束只會控制遠端伺服器上 SQL Server Agent 作業的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="41069-116">When you create precedence constraints between the Execute SQL Server Agent Job tasks in the parent package, these precedence constraints control only the time that the SQL Server Agent jobs on the remote servers are started.</span></span> <span data-ttu-id="41069-117">優先順序條件約束不會接收有關從 SQL Server Agent 作業步驟執行之子封裝成功或失敗的資訊。</span><span class="sxs-lookup"><span data-stu-id="41069-117">Precedence constraints cannot receive information regarding the success or failure of the child packages that are run from the steps of the SQL Server Agent jobs.</span></span>  
  
 <span data-ttu-id="41069-118">這表示子封裝的成功與否並不會傳播至父封裝，因為父封裝中「執行 SQL Server Agent」作業的唯一功能是要求 SQL Server Agent 作業執行子封裝。</span><span class="sxs-lookup"><span data-stu-id="41069-118">This means that success or failure of a child package does not propagate to the parent, because the sole function of the Execute SQL Server Agent job in the parent package is to request the SQL Server Agent job to run the child package.</span></span> <span data-ttu-id="41069-119">在成功呼叫 SQL Server Agent 作業之後，父封裝將會收到 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> 的結果。</span><span class="sxs-lookup"><span data-stu-id="41069-119">After the SQL Server Agent job is called successfully, the parent package receives a result of <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success>.</span></span>  
  
 <span data-ttu-id="41069-120">這種狀況下的失敗只代表呼叫遠端「SQL Server Agent 作業」工作的失敗。</span><span class="sxs-lookup"><span data-stu-id="41069-120">Failure in this scenario means only that there has been a failure in calling the remote SQL Server Agent Job task.</span></span> <span data-ttu-id="41069-121">可能發生這種錯誤的其中一種情況是遠端伺服器已經關閉而且代理程式無法回應。</span><span class="sxs-lookup"><span data-stu-id="41069-121">One situation where this can occur is when the remote server is down and the agent does not respond.</span></span> <span data-ttu-id="41069-122">不過，只要代理程式有反應，就代表父封裝已經順利完成其工作。</span><span class="sxs-lookup"><span data-stu-id="41069-122">However, as long as the agent fires, the parent package has successfully completed its task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41069-123">您可以使用包含 Transact-SQL 陳述式為 **sp_start_job N'package_name'** 的「執行 SQL 工作」。</span><span class="sxs-lookup"><span data-stu-id="41069-123">You can use an Execute SQL Task that contains a Transact-SQL statement of **sp_start_job N'package_name'**.</span></span> <span data-ttu-id="41069-124">如需詳細資訊，請參閱 [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="41069-124">For more information, see [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).</span></span>  
  
## <a name="debugging-environment"></a><span data-ttu-id="41069-125">環境偵錯</span><span class="sxs-lookup"><span data-stu-id="41069-125">Debugging Environment</span></span>  
 <span data-ttu-id="41069-126">測試父封裝時，請使用 [偵錯] / [開始偵錯] (F5) 來執行以使用設計師的偵錯環境。</span><span class="sxs-lookup"><span data-stu-id="41069-126">When testing the parent package, use the debugging environment of the designer by running it using Debug / Start Debugging (F5).</span></span> <span data-ttu-id="41069-127">或者，也可以使用命令提示公用程式 **dtexec**。</span><span class="sxs-lookup"><span data-stu-id="41069-127">Alternatively, you can use the command prompt utility, **dtexec**.</span></span> <span data-ttu-id="41069-128">如需詳細資訊，請參閱 [dtexec Utility](packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="41069-128">For more information, see [dtexec Utility](packages/dtexec-utility.md).</span></span>  
  
  
