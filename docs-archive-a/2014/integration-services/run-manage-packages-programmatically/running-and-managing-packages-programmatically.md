---
title: 以程式設計方式執行及管理套件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0b07b0b98674fa17891dbbcb01ec42934c2a72e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698446"
---
# <a name="running-and-managing-packages-programmatically"></a><span data-ttu-id="de6f9-102">以程式設計方式執行及管理封裝</span><span class="sxs-lookup"><span data-stu-id="de6f9-102">Running and Managing Packages Programmatically</span></span>
  <span data-ttu-id="de6f9-103">如果您需要在開發環境以外的地方管理和執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，可以使用程式設計方式操作封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-103">If you need manage and run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages outside the development environment, you can manipulate packages programmatically.</span></span> <span data-ttu-id="de6f9-104">在這種方法中，您有許多的選擇：</span><span class="sxs-lookup"><span data-stu-id="de6f9-104">In this approach, you have a range of options:</span></span>  
  
-   <span data-ttu-id="de6f9-105">在不須修改的情況下載入並執行現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-105">Load and run an existing package without modification.</span></span>  
  
-   <span data-ttu-id="de6f9-106">載入現有的封裝、重新設定 (例如，針對不同的資料來源) 然後加以執行。</span><span class="sxs-lookup"><span data-stu-id="de6f9-106">Load an existing package, reconfigure it (for example, for a different data source), and run it.</span></span>  
  
-   <span data-ttu-id="de6f9-107">建立新封裝、逐物件和逐屬性地加入與設定元件、儲存，然後加以執行。</span><span class="sxs-lookup"><span data-stu-id="de6f9-107">Create a new package, add and configure components object by object and property by property, save it, and run it.</span></span>  
  
 <span data-ttu-id="de6f9-108">您可以只撰寫幾行程式碼，從用戶端應用程式載入及執行現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-108">You can load and run an existing package from a client application by writing only a few lines of code.</span></span>  
  
 <span data-ttu-id="de6f9-109">本章節描述及示範如何以程式設計方式執行現有的封裝，以及如何從其他應用程式存取資料流程的輸出。</span><span class="sxs-lookup"><span data-stu-id="de6f9-109">This section describes and demonstrates how to run an existing package programmatically and how to access the output of the data flow from other applications.</span></span> <span data-ttu-id="de6f9-110">如同進階程式設計選項，您能夠以程式設計方式逐行建立 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件 (如[以程式設計方式建置套件](../building-packages-programmatically/building-packages-programmatically.md)主題中所述)。</span><span class="sxs-lookup"><span data-stu-id="de6f9-110">As an advanced programming option, you can programmatically create an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package line by line as described in the topic, [Building Packages Programmatically](../building-packages-programmatically/building-packages-programmatically.md).</span></span>  
  
 <span data-ttu-id="de6f9-111">本章節也會討論您可以使用程式設計方式執行的其他管理工作，以管理預存程序、執行中的封裝和封裝角色。</span><span class="sxs-lookup"><span data-stu-id="de6f9-111">This section also discusses other administrative tasks that you can perform programmatically to manage stored packages, running packages, and package roles.</span></span>  
  
## <a name="running-packages-on-the-integration-services-server"></a><span data-ttu-id="de6f9-112">在 Integration Services 伺服器上執行封裝</span><span class="sxs-lookup"><span data-stu-id="de6f9-112">Running Packages on the Integration Services Server</span></span>  
 <span data-ttu-id="de6f9-113">當您將封裝部署至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器時，可以使用 <xref:Microsoft.SqlServer.Management.IntegrationServices> 命名空間，以程式設計方式執行封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-113">When you deploy packages to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can run the packages programmatically by using the <xref:Microsoft.SqlServer.Management.IntegrationServices> namespace.</span></span> <span data-ttu-id="de6f9-114">Microsoft.SqlServer.Management.IntegrationServices 組件是使用 .NET Framework 3.5 編譯的。</span><span class="sxs-lookup"><span data-stu-id="de6f9-114">The Microsoft.SqlServer.Management.IntegrationServices assembly is compiled with .NET Framework 3.5.</span></span> <span data-ttu-id="de6f9-115">如果您要建置 .NET Framework 4.0 應用程式，可能需要將組件參考直接加入至專案檔案。</span><span class="sxs-lookup"><span data-stu-id="de6f9-115">If you are building a .NET Framework 4.0 application, you might need to add the assembly reference directly to your project file.</span></span>  
  
 <span data-ttu-id="de6f9-116">您也可以使用此命名空間，在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器上部署和管理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="de6f9-116">You can also use the namespace to deploy and manage [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projects on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="de6f9-117">如需命名空間的概觀和程式碼片段，請參閱 blogs.msdn.com 上的部落格文章：[SSIS 目錄管理物件模型初探](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892)。</span><span class="sxs-lookup"><span data-stu-id="de6f9-117">For an overview of the namespace and code snippets, see the blog entry, [A Glimpse of the SSIS Catalog Managed Object Model](https://techcommunity.microsoft.com/t5/sql-server-integration-services/a-glimpse-of-the-ssis-catalog-managed-object-model/ba-p/387892), on blogs.msdn.com.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de6f9-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="de6f9-118">In This Section</span></span>  
 [<span data-ttu-id="de6f9-119">了解本機和遠端執行之間的差異</span><span class="sxs-lookup"><span data-stu-id="de6f9-119">Understanding the Differences between Local and Remote Execution</span></span>](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 <span data-ttu-id="de6f9-120">討論在本機執行封裝以及在伺服器上執行封裝之間的重大差異。</span><span class="sxs-lookup"><span data-stu-id="de6f9-120">Discusses critical differences between executing a package locally or on the server.</span></span>  
  
 [<span data-ttu-id="de6f9-121">以程式設計方式載入和執行本機套件</span><span class="sxs-lookup"><span data-stu-id="de6f9-121">Loading and Running a Local Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 <span data-ttu-id="de6f9-122">描述如何在本機電腦上從用戶端應用程式執行現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-122">Describes how to execute an existing package from a client application on the local computer.</span></span>  
  
 [<span data-ttu-id="de6f9-123">以程式設計方式載入和執行遠端套件</span><span class="sxs-lookup"><span data-stu-id="de6f9-123">Loading and Running a Remote Package Programmatically</span></span>](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 <span data-ttu-id="de6f9-124">描述如何從用戶端應用程式執行現有的封裝，並確保此封裝是在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="de6f9-124">Describes how to execute an existing package from a client application and to ensure that the package runs on the server.</span></span>  
  
 [<span data-ttu-id="de6f9-125">載入本機套件的輸出</span><span class="sxs-lookup"><span data-stu-id="de6f9-125">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 <span data-ttu-id="de6f9-126">描述如何使用 DataReader 目的地和 DtsClient 命名空間在本機電腦上執行封裝，以及如何將資料流程輸出載入用戶端應用程式內。</span><span class="sxs-lookup"><span data-stu-id="de6f9-126">Describes how to execute a package on the local computer and how to load the data flow output into a client application by using the DataReader destination and the DtsClient namespace.</span></span>  
  
 [<span data-ttu-id="de6f9-127">以程式設計方式列舉可用的套件</span><span class="sxs-lookup"><span data-stu-id="de6f9-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 <span data-ttu-id="de6f9-128">描述如何探索受到 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務所管理的可用封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-128">Describes how to discover available packages that are managed by the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] service.</span></span>  
  
 [<span data-ttu-id="de6f9-129">以程式設計方式管理套件與資料夾</span><span class="sxs-lookup"><span data-stu-id="de6f9-129">Managing Packages and Folders Programmatically</span></span>](../run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 <span data-ttu-id="de6f9-130">描述如何建立、重新命名及刪除封裝和資料夾。</span><span class="sxs-lookup"><span data-stu-id="de6f9-130">Describes how to create, rename, and delete both packages and folders.</span></span>  
  
 [<span data-ttu-id="de6f9-131">以程式設計方式管理執行中的套件</span><span class="sxs-lookup"><span data-stu-id="de6f9-131">Managing Running Packages Programmatically</span></span>](../run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 <span data-ttu-id="de6f9-132">描述如何列出目前正在執行的封裝、檢查封裝的屬性，並停止執行中的封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-132">Describes how to list packages that are currently running, examine their properties, and stop a running package.</span></span>  
  
 [<span data-ttu-id="de6f9-133">以程式設計方式管理套件角色 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="de6f9-133">Managing Package Roles Programmatically &#40;SSIS Service&#41;</span></span>](../run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 <span data-ttu-id="de6f9-134">描述如何取得或設定指派給封裝或資料夾之角色的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="de6f9-134">Describes how to get or set information about the roles assigned to a package or a folder.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="de6f9-135">參考</span><span class="sxs-lookup"><span data-stu-id="de6f9-135">Reference</span></span>  
 [<span data-ttu-id="de6f9-136">Integration Services 錯誤和訊息參考</span><span class="sxs-lookup"><span data-stu-id="de6f9-136">Integration Services Error and Message Reference</span></span>](../integration-services-error-and-message-reference.md)  
 <span data-ttu-id="de6f9-137">列出預先定義的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 錯誤碼，以及其符號名稱與描述。</span><span class="sxs-lookup"><span data-stu-id="de6f9-137">Lists the predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error codes with their symbolic names and descriptions.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="de6f9-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="de6f9-138">Related Sections</span></span>  
 [<span data-ttu-id="de6f9-139">使用指令碼擴充套件</span><span class="sxs-lookup"><span data-stu-id="de6f9-139">Extending Packages with Scripting</span></span>](../extending-packages-scripting/extending-packages-with-scripting.md)  
 <span data-ttu-id="de6f9-140">討論如何透過使用指令碼工作擴充控制流程，或是如何透過使用指令碼元件擴充資料流程。</span><span class="sxs-lookup"><span data-stu-id="de6f9-140">Discusses how to extend the control flow by using the Script task, and how to extend the data flow by using the Script component.</span></span>  
  
 [<span data-ttu-id="de6f9-141">使用自訂物件擴充封裝</span><span class="sxs-lookup"><span data-stu-id="de6f9-141">Extending Packages with Custom Objects</span></span>](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 <span data-ttu-id="de6f9-142">討論如何建立程式自訂工作、資料流程元件以及其他封裝物件，以供在多個封裝中使用。</span><span class="sxs-lookup"><span data-stu-id="de6f9-142">Discusses how to create program custom tasks, data flow components, and other package objects for use in multiple packages.</span></span>  
  
 [<span data-ttu-id="de6f9-143">以程式設計方式建置套件</span><span class="sxs-lookup"><span data-stu-id="de6f9-143">Building Packages Programmatically</span></span>](../building-packages-programmatically/building-packages-programmatically.md)  
 <span data-ttu-id="de6f9-144">討論如何以程式設計方式建立、設定和儲存 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="de6f9-144">Discusses how to create, configure, and save [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages programmatically.</span></span>  
  
<span data-ttu-id="de6f9-145">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="de6f9-145">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="de6f9-146">若要取得 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的最新下載、文件、範例和影片以及社群中的選定方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="de6f9-146">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="de6f9-147">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="de6f9-147">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="de6f9-148">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="de6f9-148">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6f9-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de6f9-149">See Also</span></span>  
 [<span data-ttu-id="de6f9-150">SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="de6f9-150">SQL Server Integration Services</span></span>](../sql-server-integration-services.md)  
  
  
