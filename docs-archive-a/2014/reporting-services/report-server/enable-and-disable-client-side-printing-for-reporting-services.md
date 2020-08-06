---
title: 啟用和停用 Reporting Services 的用戶端列印功能 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0e709c96-7517-4547-8ef6-5632f8118524
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 031a7cd9b5da07b03b76b6bf49db63572a8fe546
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597580"
---
# <a name="enable-and-disable-client-side-printing-for-reporting-services"></a><span data-ttu-id="30a7b-102">啟用和停用 Reporting Services 的用戶端列印功能</span><span class="sxs-lookup"><span data-stu-id="30a7b-102">Enable and Disable Client-Side Printing for Reporting Services</span></span>
  <span data-ttu-id="30a7b-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]ActiveX 控制項（ **RSClientPrint**）會針對瀏覽器中所查看的報表，提供用戶端列印功能。</span><span class="sxs-lookup"><span data-stu-id="30a7b-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX control, **RSClientPrint**, provides client-side printing for reports viewed in a browser.</span></span> <span data-ttu-id="30a7b-104">此控制項會顯示自訂列印對話方塊，其中支援與其他列印對話方塊一樣的一般功能。</span><span class="sxs-lookup"><span data-stu-id="30a7b-104">The control displays a custom print dialog box that supports features common to other print dialog boxes.</span></span> <span data-ttu-id="30a7b-105">這些功能包括預覽列印、可指定要列印的特定頁面及範圍、頁面邊界和列印方向。</span><span class="sxs-lookup"><span data-stu-id="30a7b-105">The features include print preview, page selections for specifying specific pages and ranges, page margins, and orientation.</span></span> <span data-ttu-id="30a7b-106">雖然依預設會啟用用戶端列印，但如果您不想提供此功能，也可以停用它。</span><span class="sxs-lookup"><span data-stu-id="30a7b-106">Although client-side printing is enabled by default, you can disable the feature to prevent it from being used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30a7b-107">下載 ActiveX 控制項需要具有管理員權限。</span><span class="sxs-lookup"><span data-stu-id="30a7b-107">Downloading ActiveX controls requires administrator permissions.</span></span>  
  
## <a name="downloading-the-activex-control"></a><span data-ttu-id="30a7b-108">下載 ActiveX 控制項</span><span class="sxs-lookup"><span data-stu-id="30a7b-108">Downloading the ActiveX Control</span></span>  
 <span data-ttu-id="30a7b-109">每一個想要使用列印功能的使用者，都必須下載並安裝提供用戶端列印功能的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="30a7b-109">Each user who wants to use the print feature must download and install the ActiveX control that provides client print functionality.</span></span> <span data-ttu-id="30a7b-110">使用者第一次按一下 [報表] 工具列上的 [**印表機**] 圖示時，會將 Microsoft ActiveX 控制項下載至電腦。</span><span class="sxs-lookup"><span data-stu-id="30a7b-110">The first time a user clicks the **Printer** icon on the report toolbar, the Microsoft ActiveX control is downloaded to the computer.</span></span> <span data-ttu-id="30a7b-111">下載控制項之後，每當使用者按一下**印表機**圖示時，就會顯示 [**列印**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="30a7b-111">After the control is downloaded, the **Print** dialog box displays whenever the user clicks the **Printer** icon.</span></span>  
  
 <span data-ttu-id="30a7b-112">視瀏覽器設定而定，也許會提示使用者安裝此控制項、防止安裝此控制項，或在背景中無障礙地安裝此控制項。</span><span class="sxs-lookup"><span data-stu-id="30a7b-112">Depending on browser settings, the user may be prompted to install the control, be prevented from installing the control, or have the control install transparently in the background.</span></span>  
  
 <span data-ttu-id="30a7b-113">對於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer，影響 activex 控制項下載和安裝的設定是透過 Web 內容區域之 [**安全性設定**] 頁面中的 [ **ActiveX 控制項與外掛程式]** 節點來指定。</span><span class="sxs-lookup"><span data-stu-id="30a7b-113">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer, settings that affect ActiveX control download and installation are specified through the **ActiveX controls and plug-ins** node in the **Security Settings** page for the Web content zone.</span></span> <span data-ttu-id="30a7b-114">下列設定將根據網際網路區域安全性喜好設定，決定使用者是否可以下載及執行列印控制項：</span><span class="sxs-lookup"><span data-stu-id="30a7b-114">The following settings determine whether users can download and run the print control, based on Web zone security preferences:</span></span>  
  
-   <span data-ttu-id="30a7b-115">下載簽署的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="30a7b-115">Download signed ActiveX controls.</span></span>  
  
-   <span data-ttu-id="30a7b-116">為標示為安全可供撰寫指令碼的 ActiveX 控制項撰寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="30a7b-116">Script ActiveX controls marked safe for scripting.</span></span>  
  
-   <span data-ttu-id="30a7b-117">執行 ActiveX 控制項和外掛程式。</span><span class="sxs-lookup"><span data-stu-id="30a7b-117">Run ActiveX controls and plug-ins.</span></span>  
  
 <span data-ttu-id="30a7b-118">想要使用**RSClientPrint**執行用戶端列印的使用者必須啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="30a7b-118">Users who want to use **RSClientPrint** to perform client-side printing must enable the following:</span></span>  
  
-   <span data-ttu-id="30a7b-119">**下載已簽署的 activex 控制項**，並**編寫標示為安全的 activex 控制項腳本**，以供安裝之用。</span><span class="sxs-lookup"><span data-stu-id="30a7b-119">**Download signed ActiveX controls** and **Script ActiveX control marked safe for scripting** for installation purposes.</span></span>  
  
-   <span data-ttu-id="30a7b-120">**執行 ActiveX 控制項和外掛程式**進行進行中的列印工作。</span><span class="sxs-lookup"><span data-stu-id="30a7b-120">**Run ActiveX controls and plug-ins** for ongoing print operations.</span></span>  
  
 <span data-ttu-id="30a7b-121">**RSClientPrint** ActiveX 控制項已簽署，這表示它包含來自的有效數位憑證 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="30a7b-121">The **RSClientPrint** ActiveX control is signed, meaning it contains a valid digital certificate from [!INCLUDE[msCoName](../../includes/msconame-md.md)].</span></span>  
  
## <a name="enabling-and-disabling-client-side-printing"></a><span data-ttu-id="30a7b-122">啟用及停用用戶端列印</span><span class="sxs-lookup"><span data-stu-id="30a7b-122">Enabling and Disabling Client-Side Printing</span></span>  
 <span data-ttu-id="30a7b-123">報表伺服器管理員可以選擇停用列印功能，方法是將報表伺服器系統屬性**EnableClientPrinting**設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="30a7b-123">Report server administrators have the option of disabling the print feature by setting the report server system property **EnableClientPrinting** to `false`.</span></span> <span data-ttu-id="30a7b-124">這樣會停用由該伺服器管理的所有報表的用戶端列印功能。</span><span class="sxs-lookup"><span data-stu-id="30a7b-124">This will disable client-side printing for all reports managed by that server.</span></span> <span data-ttu-id="30a7b-125">根據預設， **EnableClientPrinting**會設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="30a7b-125">By default, **EnableClientPrinting** is set to `true`.</span></span> <span data-ttu-id="30a7b-126">您可以採用下列方式來停用用戶端列印：</span><span class="sxs-lookup"><span data-stu-id="30a7b-126">You can disable client-side printing in the following ways:</span></span>  
  
-   <span data-ttu-id="30a7b-127">針對 **原生模式報表伺服器**：</span><span class="sxs-lookup"><span data-stu-id="30a7b-127">For a **Native mode report server**:</span></span>  
  
    1.  <span data-ttu-id="30a7b-128">使用系統管理權限來啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="30a7b-128">Start [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    2.  <span data-ttu-id="30a7b-129">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，連接到報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="30a7b-129">Connect to a report server instance in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
    3.  <span data-ttu-id="30a7b-130">以滑鼠右鍵按一下報表伺服器節點，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="30a7b-130">Right-click the report server node, and then click **Properties**.</span></span> <span data-ttu-id="30a7b-131">如果 **[屬性]** 選項已停用，請確認您已使用系統管理權限來啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="30a7b-131">If the **Properties** option is disabled, verify you started [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] with administrative privileges.</span></span>  
  
    4.  <span data-ttu-id="30a7b-132">選取 **[啟用 ActiveX 用戶端列印控制項的下載**]。</span><span class="sxs-lookup"><span data-stu-id="30a7b-132">Select **Enable download for the ActiveX client print control**.</span></span>  
  
    5.  <span data-ttu-id="30a7b-133">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="30a7b-133">Click **OK**.</span></span>  
  
-   <span data-ttu-id="30a7b-134">針對 **SharePoint 模式報表伺服器**：</span><span class="sxs-lookup"><span data-stu-id="30a7b-134">For a **SharePoint mode report server**:</span></span>  
  
    1.  <span data-ttu-id="30a7b-135">在 SharePoint 管理中心內，按一下 **[應用程式管理]**。</span><span class="sxs-lookup"><span data-stu-id="30a7b-135">In SharePoint Central Administration, click **Application Management**.</span></span>  
  
    2.  <span data-ttu-id="30a7b-136">按一下 **[管理服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="30a7b-136">Click **Manage service applications**.</span></span>  
  
    3.  <span data-ttu-id="30a7b-137">按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的名稱，然後按一下 SharePoint 功能區中的 **[管理]** 。</span><span class="sxs-lookup"><span data-stu-id="30a7b-137">Click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, and then click **Manage** in the SharePoint ribbon.</span></span>  
  
    4.  <span data-ttu-id="30a7b-138">按一下 **[系統設定]**。</span><span class="sxs-lookup"><span data-stu-id="30a7b-138">Click **System Settings**.</span></span>  
  
    5.  <span data-ttu-id="30a7b-139">選取 **[啟用用戶端列印]**。</span><span class="sxs-lookup"><span data-stu-id="30a7b-139">Select **Enable Client Printing**.</span></span> <span data-ttu-id="30a7b-140">**[啟用用戶端列印]** 選項位於靠近頁面底部的位置。</span><span class="sxs-lookup"><span data-stu-id="30a7b-140">The **Enable Client Printing** option is near the bottom of the page.</span></span>  
  
    6.  <span data-ttu-id="30a7b-141">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="30a7b-141">Click **OK**.</span></span>  
  
-   <span data-ttu-id="30a7b-142">撰寫腳本或程式碼，將報表伺服器系統屬性**EnableClientPrinting**設定為`false.`</span><span class="sxs-lookup"><span data-stu-id="30a7b-142">Write script or code to set the report server system property **EnableClientPrinting** to `false.`</span></span>  
  
 <span data-ttu-id="30a7b-143">下列範例指令碼說明停用用戶端列印功能的方法之一。</span><span class="sxs-lookup"><span data-stu-id="30a7b-143">The following sample script illustrates one approach for disabling client-side printing.</span></span> <span data-ttu-id="30a7b-144">編譯後執行下列 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 程式碼，將 **EnableClientPrinting** 屬性設定為 **False**。</span><span class="sxs-lookup"><span data-stu-id="30a7b-144">Compile and then run the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code to set the **EnableClientPrinting** property to **False**.</span></span> <span data-ttu-id="30a7b-145">執行程式碼之後，請重新啟動 IIS。</span><span class="sxs-lookup"><span data-stu-id="30a7b-145">After you run the code, restart IIS.</span></span>  
  
### <a name="sample-script"></a><span data-ttu-id="30a7b-146">範例指令碼</span><span class="sxs-lookup"><span data-stu-id="30a7b-146">Sample Script</span></span>  
  
```  
Imports System  
Imports System.Web.Services.Protocols  
Class Sample  
   Public Shared Sub Main()  
Dim rs As New ReportingService()  
      rs.Credentials = System.Net.CredentialCache.DefaultCredentials  
        Dim props(0) As [Property]  
        Dim setProp As New [Property]  
        setProp.Name = "EnableClientPrinting"  
        setProp.Value = "False"   
        props(0) = setProp  
        Try  
            rs.SetSystemProperties(props)  
        Catch ex As System.Web.Services.Protocols.SoapException  
            Console.Write(ex.Detail.InnerXml)  
        Catch e as Exception  
            Console.Write(e.Message)  
        End Try  
    End Sub 'Main  
End Class 'Sample  
```  
  
  
