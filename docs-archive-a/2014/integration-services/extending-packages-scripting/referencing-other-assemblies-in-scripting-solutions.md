---
title: 參考指令碼解決方案中的其他組件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, .NET Framework
- Script task [Integration Services], adding references
- referencing custom assemblies
- SSIS Script task, VisualBasic namespace
- assemblies [Integration Services]
- VisualBasic namespace
- Script task [Integration Services], VisualBasic namespace
- Microsoft.VisualBasic namespace
- Script task [Integration Services], .NET Framework
- .NET Framework [Integration Services]
- referencing Web services
ms.assetid: 9b655bcd-19f6-43d8-9f89-1b4d299c6380
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 685bbaa62da88e84cd848eb49dcf5bedb03d5390
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592762"
---
# <a name="referencing-other-assemblies-in-scripting-solutions"></a><span data-ttu-id="9a132-102">參考指令碼解決方案中的其他組件</span><span class="sxs-lookup"><span data-stu-id="9a132-102">Referencing Other Assemblies in Scripting Solutions</span></span>
  <span data-ttu-id="9a132-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別庫提供指令碼開發人員一組強大的工具，以實作 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件中的自訂功能。</span><span class="sxs-lookup"><span data-stu-id="9a132-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library provides the script developer with a powerful set of tools for implementing custom functionality in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="9a132-104">指令碼工作和指令碼元件也可以使用自訂 Managed 組件。</span><span class="sxs-lookup"><span data-stu-id="9a132-104">The Script task and the Script component can also use custom managed assemblies.</span></span>

> [!NOTE]
>  <span data-ttu-id="9a132-105">若要讓您的封裝能夠使用 Web 服務中的物件和方法，請使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) 所提供的 [加入 Web 參考] 命令。</span><span class="sxs-lookup"><span data-stu-id="9a132-105">To enable your packages to use the objects and methods from a Web service, use the **Add Web Reference** command available in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="9a132-106">在舊版的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，您必須產生 Proxy 類別以使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="9a132-106">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you had to generate a proxy class to use a Web service.</span></span>

## <a name="using-a-managed-assembly"></a><span data-ttu-id="9a132-107">使用 Managed 組件</span><span class="sxs-lookup"><span data-stu-id="9a132-107">Using a Managed Assembly</span></span>
 <span data-ttu-id="9a132-108">若要讓 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 在設計階段尋找 Managed 組件，您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9a132-108">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find a managed assembly at design time, you must do the following steps:</span></span>

1.  <span data-ttu-id="9a132-109">在電腦上的任何資料夾中儲存 Managed 組件。</span><span class="sxs-lookup"><span data-stu-id="9a132-109">Store the managed assembly in any folder on your computer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="9a132-110">在舊版的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中，您只能加入儲存在 %windir%\Microsoft.NET\Framework\vx.x.xxxxx 資料夾或是 %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies 資料夾中的 Managed 組件參考。</span><span class="sxs-lookup"><span data-stu-id="9a132-110">In earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you could only add a reference to a managed assembly that was stored in the %windir%\Microsoft.NET\Framework\vx.x.xxxxx folder or the %ProgramFiles%\Microsoft SQL Server\100\SDK\Assemblies folder.</span></span>

2.  <span data-ttu-id="9a132-111">加入 Managed 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="9a132-111">Add a reference to the managed assembly.</span></span>

     <span data-ttu-id="9a132-112">若要加入參考，請在 VSTA 中，於 [加入參考]  對話方塊的 [瀏覽]  索引標籤上，找到並加入 Managed 組件。</span><span class="sxs-lookup"><span data-stu-id="9a132-112">To add the reference, in VSTA, in the **Add Reference** dialog box, on the **Browse** tab, locate and add the managed assembly.</span></span>

 <span data-ttu-id="9a132-113">若要 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 在執行階段尋找 Managed 組件，您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9a132-113">For [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to find the managed assembly at run time, you must do the following steps:</span></span>

1.  <span data-ttu-id="9a132-114">使用強式名稱簽署 Managed 組件。</span><span class="sxs-lookup"><span data-stu-id="9a132-114">Sign the managed assembly with a strong name.</span></span>

2.  <span data-ttu-id="9a132-115">在執行封裝的電腦上之全域組件快取中安裝組件。</span><span class="sxs-lookup"><span data-stu-id="9a132-115">Install the assembly in the global assembly cache on the computer on which the package is run.</span></span>

     <span data-ttu-id="9a132-116">如需詳細資訊，請參閱[建立、部署和偵錯自訂物件](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="9a132-116">For more information, see [Building, Deploying, and Debugging Custom Objects](../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).</span></span>

## <a name="using-the-microsoft-net-framework-class-library"></a><span data-ttu-id="9a132-117">使用 Microsoft .NET Framework 類別庫</span><span class="sxs-lookup"><span data-stu-id="9a132-117">Using the Microsoft .NET Framework Class Library</span></span>
 <span data-ttu-id="9a132-118">指令碼工作與指令碼元件可以利用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別庫公開的所有其他物件與功能。</span><span class="sxs-lookup"><span data-stu-id="9a132-118">The Script task and the Script component can take advantage of all the other objects and functionality exposed by the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class library.</span></span> <span data-ttu-id="9a132-119">例如，透過使用 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]，可以擷取您的環境相關資訊，並與執行封裝的電腦互動。</span><span class="sxs-lookup"><span data-stu-id="9a132-119">For example, by using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], you can retrieve information about your environment and interact with the computer that is running the package.</span></span>

 <span data-ttu-id="9a132-120">這個清單說明幾個較常使用的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別：</span><span class="sxs-lookup"><span data-stu-id="9a132-120">This list describes several of the more frequently used [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes:</span></span>

-   <span data-ttu-id="9a132-121">`System.Data`包含 ADO.NET 架構。</span><span class="sxs-lookup"><span data-stu-id="9a132-121">`System.Data` Contains the ADO.NET architecture.</span></span>

-   <span data-ttu-id="9a132-122">`System.IO`提供檔案系統和資料流程的介面。</span><span class="sxs-lookup"><span data-stu-id="9a132-122">`System.IO` Provides an interface to the file system and streams.</span></span>

-   <span data-ttu-id="9a132-123">`System.Windows.Forms`提供表單建立。</span><span class="sxs-lookup"><span data-stu-id="9a132-123">`System.Windows.Forms` Provides form creation.</span></span>

-   <span data-ttu-id="9a132-124">`System.Text.RegularExpressions`提供用來處理正則運算式的類別。</span><span class="sxs-lookup"><span data-stu-id="9a132-124">`System.Text.RegularExpressions` Provides classes for working with regular expressions.</span></span>

-   <span data-ttu-id="9a132-125">`System.Environment`傳回本機電腦、目前使用者以及電腦與使用者設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9a132-125">`System.Environment` Returns information about the local computer, the current user, and computer and user settings.</span></span>

-   <span data-ttu-id="9a132-126">`System.Net`提供網路通訊。</span><span class="sxs-lookup"><span data-stu-id="9a132-126">`System.Net` Provides network communications.</span></span>

-   <span data-ttu-id="9a132-127">`System.DirectoryServices`公開 Active Directory。</span><span class="sxs-lookup"><span data-stu-id="9a132-127">`System.DirectoryServices` Exposes Active Directory.</span></span>

-   <span data-ttu-id="9a132-128">`System.Drawing`提供大量的影像操作程式庫。</span><span class="sxs-lookup"><span data-stu-id="9a132-128">`System.Drawing` Provides extensive image manipulation libraries.</span></span>

-   <span data-ttu-id="9a132-129">`System.Threading`啟用多執行緒程式設計。</span><span class="sxs-lookup"><span data-stu-id="9a132-129">`System.Threading` Enables multithreaded programming.</span></span>

 <span data-ttu-id="9a132-130">如需有關 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 的相細資訊，請參閱 MSDN Library。</span><span class="sxs-lookup"><span data-stu-id="9a132-130">For more information about the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see the MSDN Library.</span></span>

<span data-ttu-id="9a132-131">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="9a132-131">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="9a132-132">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="9a132-132">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="9a132-133">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="9a132-133">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="9a132-134">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="9a132-134">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a132-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a132-135">See Also</span></span>
 [<span data-ttu-id="9a132-136">使用指令碼擴充套件</span><span class="sxs-lookup"><span data-stu-id="9a132-136">Extending Packages with Scripting</span></span>](extending-packages-with-scripting.md)


