---
title: 查看和停止在 Integration Services 伺服器上執行的封裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing running packages [Integration Services]
- packages [Integration Services], running
- running package [Integration Services], managing
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e63839d4ab5d8d50f7d86eea05c8d58107d6799
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599569"
---
# <a name="viewing-and-stopping-packages-running-on-the-integration-services-server"></a><span data-ttu-id="85c69-102">檢視及停止在 Integration Services 伺服器上執行的封裝</span><span class="sxs-lookup"><span data-stu-id="85c69-102">Viewing and Stopping Packages Running on the Integration Services Server</span></span>
  <span data-ttu-id="85c69-103">`SSISDB` 資料庫會將執行記錄儲存在不會對使用者顯示的內部資料表中。</span><span class="sxs-lookup"><span data-stu-id="85c69-103">The `SSISDB` database stores execution history in internal tables that are not visible to users.</span></span> <span data-ttu-id="85c69-104">不過，它會透過可供您查詢的公用檢視來公開您需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="85c69-104">However it exposes the information that you need through public views that you can query.</span></span> <span data-ttu-id="85c69-105">另外，它也會提供預存程序，讓您可以加以呼叫，以執行與封裝相關的一般工作。</span><span class="sxs-lookup"><span data-stu-id="85c69-105">It also provides stored procedures that you can call to perform common tasks related to packages.</span></span>  
  
 <span data-ttu-id="85c69-106">通常，您會在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中管理伺服器上的 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="85c69-106">Typically you manage [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects on the server in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="85c69-107">但您也可以直接查詢資料庫檢視並呼叫預存程序，或編寫可呼叫 Managed API 的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="85c69-107">However you can also query the database views and call the stored procedures directly, or write custom code that calls the managed API.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="85c69-108">和 Managed API 會查詢檢視並呼叫預存程序，以執行許多工作。</span><span class="sxs-lookup"><span data-stu-id="85c69-108">and the managed API query the views and call the stored procedures to perform many of their tasks.</span></span> <span data-ttu-id="85c69-109">例如，您可以檢視目前正在伺服器上執行之 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的清單，並在需要時要求停止封裝。</span><span class="sxs-lookup"><span data-stu-id="85c69-109">For example, you can view the list of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages that are currently running on the server, and request packages to stop if you have to.</span></span>  
  
## <a name="viewing-the-list-of-running-packages"></a><span data-ttu-id="85c69-110">檢視執行中封裝的清單</span><span class="sxs-lookup"><span data-stu-id="85c69-110">Viewing the List of Running Packages</span></span>  
 <span data-ttu-id="85c69-111">您可以在 **[作用中的作業]** 對話方塊中檢視目前正在伺服器上執行之封裝的清單。</span><span class="sxs-lookup"><span data-stu-id="85c69-111">You can view the list of packages that are currently running on the server in the **Active Operations** dialog box.</span></span> <span data-ttu-id="85c69-112">如需詳細資訊，請參閱 [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="85c69-112">For more information, see [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).</span></span>  
  
 <span data-ttu-id="85c69-113">如需有關可用來檢視執行中封裝清單之其他方法的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="85c69-113">For information about the other methods that you can use to view the list of running packages, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="85c69-114">access</span><span class="sxs-lookup"><span data-stu-id="85c69-114">access</span></span>  
 <span data-ttu-id="85c69-115">若要檢視正在伺服器上執行之封裝的清單，請針對狀態 2 的封裝查詢檢視 [catalog.executions &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) 。</span><span class="sxs-lookup"><span data-stu-id="85c69-115">To view the list of packages that are running on the server, query the view, [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) for packages that have a status of 2.</span></span>  
  
 <span data-ttu-id="85c69-116">透過 Managed API 來以設計程式方式存取</span><span class="sxs-lookup"><span data-stu-id="85c69-116">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="85c69-117">請參閱 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空間和其類別。</span><span class="sxs-lookup"><span data-stu-id="85c69-117">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="stopping-a-running-package"></a><span data-ttu-id="85c69-118">停止執行中的封裝</span><span class="sxs-lookup"><span data-stu-id="85c69-118">Stopping a Running Package</span></span>  
 <span data-ttu-id="85c69-119">您可以在 **[作用中的作業]** 對話方塊中要求執行中的封裝停止。</span><span class="sxs-lookup"><span data-stu-id="85c69-119">You can request a running package to stop in the **Active Operations** dialog box.</span></span> <span data-ttu-id="85c69-120">如需詳細資訊，請參閱 [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="85c69-120">For more information, see [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).</span></span>  
  
 <span data-ttu-id="85c69-121">如需有關可用來停止執行中封裝之其他方法的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="85c69-121">For information about the other methods that you can use to stop a running package, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="85c69-122">access</span><span class="sxs-lookup"><span data-stu-id="85c69-122">access</span></span>  
 <span data-ttu-id="85c69-123">若要停止正在伺服器上執行的封裝，請呼叫預存程序 [catalog.stop_operation &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="85c69-123">To stop a package that is running on the server, call the stored procedure, [catalog.stop_operation &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).</span></span>  
  
 <span data-ttu-id="85c69-124">透過 Managed API 來以設計程式方式存取</span><span class="sxs-lookup"><span data-stu-id="85c69-124">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="85c69-125">請參閱 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空間和其類別。</span><span class="sxs-lookup"><span data-stu-id="85c69-125">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="viewing-the-history-of-packages-that-have-run"></a><span data-ttu-id="85c69-126">檢視已執行封裝的記錄</span><span class="sxs-lookup"><span data-stu-id="85c69-126">Viewing the History of Packages That Have Run</span></span>  
 <span data-ttu-id="85c69-127">若要檢視已在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中執行之封裝的記錄，請使用 **[所有執行]** 報表。</span><span class="sxs-lookup"><span data-stu-id="85c69-127">To view the history of packages that have run in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], use the **All Executions** report.</span></span> <span data-ttu-id="85c69-128">如需 [所有執行]  報表和其他標準報表的詳細資訊，請參閱 [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md) (Integration Services 伺服器的報表)。</span><span class="sxs-lookup"><span data-stu-id="85c69-128">For more information on the **All Executions** report and other standard reports, see [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="85c69-129">如需有關可用來檢視執行中封裝記錄之其他方法的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="85c69-129">For information about the other methods that you can use to view the history of running packages, see the following topics.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="85c69-130">access</span><span class="sxs-lookup"><span data-stu-id="85c69-130">access</span></span>  
 <span data-ttu-id="85c69-131">若要檢視已執行封裝的資訊，請查詢檢視 [catalog.executions &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="85c69-131">To view information about packages that have run, query the view, [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database).</span></span>  
  
 <span data-ttu-id="85c69-132">透過 Managed API 來以設計程式方式存取</span><span class="sxs-lookup"><span data-stu-id="85c69-132">Programmatic access through the managed API</span></span>  
 <span data-ttu-id="85c69-133">請參閱 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空間和其類別。</span><span class="sxs-lookup"><span data-stu-id="85c69-133">See the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace and its classes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c69-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85c69-134">See Also</span></span>  
 <span data-ttu-id="85c69-135">[執行專案和套件](packages/run-integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="85c69-135">[Execution of Projects and Packages](packages/run-integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="85c69-136">套件執行的疑難排解報告</span><span class="sxs-lookup"><span data-stu-id="85c69-136">Troubleshooting Reports for Package Execution</span></span>](troubleshooting/troubleshooting-reports-for-package-execution.md)  
  
  
