---
title: 以程式設計方式管理執行中的封裝 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95c5f9c28b407631764d64523b37a6295870542a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707669"
---
# <a name="managing-running-packages-programmatically"></a><span data-ttu-id="e971b-102">以程式設計方式管理執行中的封裝</span><span class="sxs-lookup"><span data-stu-id="e971b-102">Managing Running Packages Programmatically</span></span>
  <span data-ttu-id="e971b-103">當您以程式設計方式處理 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時，您可能會想要判斷目前正在執行的封裝。</span><span class="sxs-lookup"><span data-stu-id="e971b-103">As you work programmatically with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, you may want to determine which packages are currently running.</span></span> <span data-ttu-id="e971b-104"><xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空間的 <xref:Microsoft.SqlServer.Dts.Runtime> 類別提供了各種方法和類別來滿足這些需求。</span><span class="sxs-lookup"><span data-stu-id="e971b-104">The <xref:Microsoft.SqlServer.Dts.Runtime.Application> class of the <xref:Microsoft.SqlServer.Dts.Runtime> namespace provides methods and classes to satisfy these requirements.</span></span>  
  
 <span data-ttu-id="e971b-105">如需監視封裝的詳細資訊，請參閱[封裝管理 &#40;SSIS 服務&#41;](../service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="e971b-105">For more information about monitoring packages, see [Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md).</span></span>  
  
 <span data-ttu-id="e971b-106">本主題中討論的所有方法都需要 `Microsoft.SqlServer.ManagedDTS` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e971b-106">All the methods discussed in this topic require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="e971b-107">在新專案中加入參考之後，請使用 `using` 或 `Imports` 陳述式來匯入 <xref:Microsoft.SqlServer.Dts.Runtime> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="e971b-107">After you add the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e971b-108">用以搭配 SSIS 封裝存放區使用的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別之方法，僅支援 "."、localhost 或是本機伺服器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="e971b-108">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="e971b-109">您無法使用 "(local)"。</span><span class="sxs-lookup"><span data-stu-id="e971b-109">You cannot use "(local)".</span></span>  
  
## <a name="determining-which-packages-are-currently-running"></a><span data-ttu-id="e971b-110">判斷目前正在執行的封裝</span><span class="sxs-lookup"><span data-stu-id="e971b-110">Determining Which Packages Are Currently Running</span></span>  
 <span data-ttu-id="e971b-111">若要判斷目前有哪些封裝正在指定的伺服器上執行，請呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e971b-111">To determine which packages are currently running on the specified server, call the <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> method.</span></span> <span data-ttu-id="e971b-112">這個方法會傳回 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 物件的 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 集合。</span><span class="sxs-lookup"><span data-stu-id="e971b-112">This method returns a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection of <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e971b-113">管理員會看到目前正在電腦上執行的所有封裝；其他使用者只能看到已經啟動的封裝。</span><span class="sxs-lookup"><span data-stu-id="e971b-113">Administrators see all packages that are currently executing on the computer; other users see only those packages that they have launched.</span></span>  
  
## <a name="working-with-running-packages"></a><span data-ttu-id="e971b-114">處理執行中的封裝</span><span class="sxs-lookup"><span data-stu-id="e971b-114">Working with Running Packages</span></span>  
 <span data-ttu-id="e971b-115">當您判斷哪些封裝目前正在執行之後，您可以擷取有關封裝的資訊，並要求封裝停止。</span><span class="sxs-lookup"><span data-stu-id="e971b-115">After you have determined which packages are currently running, you can retrieve information about the packages and request that a package be stopped.</span></span>  
  
### <a name="getting-information-about-a-running-package"></a><span data-ttu-id="e971b-116">取得有關執行中封裝的資訊</span><span class="sxs-lookup"><span data-stu-id="e971b-116">Getting Information about a Running Package</span></span>  
 <span data-ttu-id="e971b-117">當您反覆運算 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> 集合時，您可以使用 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 物件的屬性，以尋找封裝或取得有關正在執行之封裝的其他資訊：</span><span class="sxs-lookup"><span data-stu-id="e971b-117">As you iterate through the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> collection, you can use the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to locate a package or to obtain additional information about the packages that are running:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a><span data-ttu-id="e971b-118">停止執行中的封裝</span><span class="sxs-lookup"><span data-stu-id="e971b-118">Stopping a Running Package</span></span>  
 <span data-ttu-id="e971b-119">您可以呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> 物件的 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> 方法，要求此封裝停止。</span><span class="sxs-lookup"><span data-stu-id="e971b-119">You can call the <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> method of a <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> object to request that the package be stopped.</span></span> <span data-ttu-id="e971b-120">在發出停止要求的時間與封裝實際停止的時間之間可能會有延遲。</span><span class="sxs-lookup"><span data-stu-id="e971b-120">There may be a delay between the time that a stop request is issued and the time that the package actually stops.</span></span>  
  
<span data-ttu-id="e971b-121">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="e971b-121">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e971b-122">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="e971b-122">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e971b-123">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="e971b-123">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e971b-124">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="e971b-124">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e971b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e971b-125">See Also</span></span>  
 <span data-ttu-id="e971b-126">[套件管理 &#40;SSIS 服務&#41;](../service/package-management-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="e971b-126">[Package Management &#40;SSIS Service&#41;](../service/package-management-ssis-service.md) </span></span>  
 [<span data-ttu-id="e971b-127">以程式設計方式列舉可用的套件</span><span class="sxs-lookup"><span data-stu-id="e971b-127">Enumerating Available Packages Programmatically</span></span>](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
