---
title: 部署自訂組件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3d88e1db844304b5cbb51f4af52b4715ef7e8c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708998"
---
# <a name="deploying-a-custom-assembly"></a><span data-ttu-id="76445-102">部署自訂組件</span><span class="sxs-lookup"><span data-stu-id="76445-102">Deploying a Custom Assembly</span></span>
  <span data-ttu-id="76445-103">若要在中部署自訂群組件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，請將元件放在報表設計師和報表伺服器的應用程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="76445-103">To deploy a custom assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], place the assembly in the application folders of both Report Designer and the report server.</span></span> <span data-ttu-id="76445-104">依預設，會授與自訂組件在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中的 `Execution` 權限。</span><span class="sxs-lookup"><span data-stu-id="76445-104">By default, custom assemblies are granted `Execution` permission in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="76445-105">若要授與執行權限以外的自訂組件權限，您必須編輯報表伺服器的 rssrvpolicy.config 設定檔，以及報表設計師預覽視窗的 rspreviewpolicy.config 設定檔。</span><span class="sxs-lookup"><span data-stu-id="76445-105">To grant custom assemblies privileges beyond Execute permission, you will need to edit the rssrvpolicy.config configuration file for the report server and the rspreviewpolicy.config configuration file for the Report Designer preview window.</span></span> <span data-ttu-id="76445-106">或者，您可以在全域組件快取 (GAC) 中安裝自訂組件。</span><span class="sxs-lookup"><span data-stu-id="76445-106">Alternatively, you can install your custom assembly in the global assembly cache (GAC).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="76445-107">報表設計師有兩個預覽模式：當在 `DebugLocal` 模式中啟動報表專案時，會啟動[預覽] 索引標籤與快顯預覽視窗。</span><span class="sxs-lookup"><span data-stu-id="76445-107">There are two preview modes for Report Designer: the Preview tab and the pop-up preview window that is launched when your report project is started in `DebugLocal` mode.</span></span> <span data-ttu-id="76445-108">[預覽] 索引標籤會使用 `FullTrust` 權限來執行所有的報表運算式，而且不會套用安全性原則設定。</span><span class="sxs-lookup"><span data-stu-id="76445-108">The Preview tab executes all report expressions using the `FullTrust` permission set and does not apply security policy settings.</span></span> <span data-ttu-id="76445-109">快顯預覽視窗是用以模擬報表伺服器功能，因此具有原則組態檔，而且您或系統管理員必須修改該檔案，才能在報表設計師中使用自訂組件。</span><span class="sxs-lookup"><span data-stu-id="76445-109">The pop-up preview window is meant to simulate the report server functionality and therefore has a policy configuration file that you or an administrator must modify to use custom assemblies in Report Designer.</span></span> <span data-ttu-id="76445-110">此快顯預覽也會鎖定自訂組件。</span><span class="sxs-lookup"><span data-stu-id="76445-110">This pop-up preview also locks the custom assembly.</span></span> <span data-ttu-id="76445-111">因此，您需要關閉預覽視窗，才能修改或是更新自訂組件程式碼。</span><span class="sxs-lookup"><span data-stu-id="76445-111">Therefore, you need to close the preview window in order to modify or update your custom assembly code.</span></span>  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a><span data-ttu-id="76445-112">在 Reporting Services 中部署自訂組件</span><span class="sxs-lookup"><span data-stu-id="76445-112">To deploy a custom assembly in Reporting Services</span></span>  
  
1.  <span data-ttu-id="76445-113">將自訂組件從建立位置複製到報表伺服器 bin 資料夾或是報表設計師資料夾。</span><span class="sxs-lookup"><span data-stu-id="76445-113">Copy your custom assembly from your build location to the report server bin folder or the Report Designer folder.</span></span> <span data-ttu-id="76445-114">報表伺服器 bin 資料夾的預設位置是 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin。</span><span class="sxs-lookup"><span data-stu-id="76445-114">The default location of the bin folder for the report server is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.</span></span> <span data-ttu-id="76445-115">報表設計師的預設位置是 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies。</span><span class="sxs-lookup"><span data-stu-id="76445-115">The default location of the Report Designer is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
     <span data-ttu-id="76445-116">將自訂組件放在報表伺服器 bin 資料夾中，可讓您發行參考自訂組件的報表，而將它放在報表設計師資料夾中，則可讓您在報表設計師中執行並偵錯參考自訂組件的報表。</span><span class="sxs-lookup"><span data-stu-id="76445-116">Placing your custom assembly in the report server bin folder enables you to publish reports that reference your custom assembly, and placing it in the Report Designer folder enables you to run and debug reports that reference your custom assembly in Report Designer.</span></span>  
  
     <span data-ttu-id="76445-117">如果除了預設執行權限之外，您需要授與自訂組件程式碼權限：</span><span class="sxs-lookup"><span data-stu-id="76445-117">If you need to grant your custom assembly code permissions beyond the default execute permissions:</span></span>  
  
2.  <span data-ttu-id="76445-118">開啟適當的組態檔。</span><span class="sxs-lookup"><span data-stu-id="76445-118">Open the appropriate configuration file.</span></span> <span data-ttu-id="76445-119">rssrvpolicy.config 的預設位置是 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer。</span><span class="sxs-lookup"><span data-stu-id="76445-119">The default location of rssrvpolicy.config is %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer.</span></span> <span data-ttu-id="76445-120">rspreviewpolicy.config 的預設位置是 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies。</span><span class="sxs-lookup"><span data-stu-id="76445-120">The default location of rspreviewpolicy.config is %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.</span></span>  
  
3.  <span data-ttu-id="76445-121">為您的自訂組件加入程式碼群組。</span><span class="sxs-lookup"><span data-stu-id="76445-121">Add a code group for your custom assembly.</span></span> <span data-ttu-id="76445-122">如需詳細資訊，請參閱[安全開發 &#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="76445-122">For more information, see [Secure Development &#40;Reporting Services&#41;](../extensions/secure-development/secure-development-reporting-services.md).</span></span>  
  
## <a name="updating-custom-assemblies"></a><span data-ttu-id="76445-123">更新自訂組件</span><span class="sxs-lookup"><span data-stu-id="76445-123">Updating Custom Assemblies</span></span>  
 <span data-ttu-id="76445-124">在某些時候，您可能需要更新一些已發行報表目前已參考的自訂組件版本。</span><span class="sxs-lookup"><span data-stu-id="76445-124">At some point, you may need to update a version of a custom assembly that is currently being referenced by several published reports.</span></span> <span data-ttu-id="76445-125">如果在報表伺服器或是報表設計師的 bin 目錄中已經有該組件，而且已遞增或是在某些方面已變更該組件的版本號碼，則目前發行的報表將無法再正常運作。</span><span class="sxs-lookup"><span data-stu-id="76445-125">If that assembly already exists in the bin directory of the report server or Report Designer and the version number of the assembly is incremented or changed in some way, the currently published reports will no longer work properly.</span></span> <span data-ttu-id="76445-126">您將需要更新報表定義的 `CodeModules` 元素中所參考的組件版本，並重新發行報表。</span><span class="sxs-lookup"><span data-stu-id="76445-126">You will need to update the version of the assembly that is referenced in the `CodeModules` element of the report definition and republish the reports.</span></span> <span data-ttu-id="76445-127">如果您知道會經常更新自訂組件，而且目前發行的報表需要參考新組件，則可能會考慮在特定組件的所有更新之間使用相同的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="76445-127">If you know that you will frequently update a custom assembly and your currently published reports need to reference the new assembly, you may want to consider using the same version number across all updates of a particular assembly.</span></span>  
  
 <span data-ttu-id="76445-128">如果您不需要目前發行的報表參考組件的新版本，可以將自訂組件部署到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="76445-128">If you do not need your currently published reports to reference the new version of the assembly, you can deploy your custom assembly to the global assembly cache.</span></span> <span data-ttu-id="76445-129">全域組件快取可以維護相同組件的多個版本，因此您目前的報表可以參考舊版的組件，而且新發行的報表可以參考更新的組件。</span><span class="sxs-lookup"><span data-stu-id="76445-129">The global assembly cache can maintain multiple versions of the same assembly, so that your current reports can reference the previous version of your assembly and your newly published reports can reference the updated assembly.</span></span> <span data-ttu-id="76445-130">但是另一項方法將會設定報表伺服器的繫結重新導向，以強制將舊組件的所有要求重新導向至新組件。</span><span class="sxs-lookup"><span data-stu-id="76445-130">Yet another approach would be to set the binding redirect of the report server to force a redirect of all requests for the old assembly to the new assembly.</span></span> <span data-ttu-id="76445-131">您將需要修改報表伺服器 Web.config 檔以及報表伺服器 ReportService.exe.config 檔。</span><span class="sxs-lookup"><span data-stu-id="76445-131">You would need to modify the report server Web.config file and the report server ReportService.exe.config file.</span></span> <span data-ttu-id="76445-132">項目可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="76445-132">The entry might look like the following:</span></span>  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76445-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76445-133">See Also</span></span>  
 <span data-ttu-id="76445-134">[將自訂群組件與報表搭配使用](using-custom-assemblies-with-reports.md) </span><span class="sxs-lookup"><span data-stu-id="76445-134">[Using Custom Assemblies with Reports](using-custom-assemblies-with-reports.md) </span></span>  
 [<span data-ttu-id="76445-135">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="76445-135">Working with Assemblies and the Global Assembly Cache</span></span>](https://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
