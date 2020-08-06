---
title: 使用 Windows PowerShell 的 PowerPivot 設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83b42da3e676a291bb021c02ee52e9a810207397
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599201"
---
# <a name="powerpivot-configuration-using-windows-powershell"></a><span data-ttu-id="775be-102">使用 Windows PowerShell 的 PowerPivot 組態</span><span class="sxs-lookup"><span data-stu-id="775be-102">PowerPivot Configuration using Windows PowerShell</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="775be-103">包括您可以用來設定 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]安裝的 Windows PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="775be-103">includes Windows PowerShell cmdlets that you can use to configure an installation of [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].</span></span> <span data-ttu-id="775be-104">若要使用 PowerShell 完整設定安裝，需要使用 SharePoint 指令程式和 PowerPivot for SharePoint 指令程式。</span><span class="sxs-lookup"><span data-stu-id="775be-104">To fully configure an installation with PowerShell requires the use of both SharePoint cmdlets and PowerPivot for SharePoint cmdlets.</span></span> <span data-ttu-id="775be-105">大部分組態都可以使用其中一項 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 工具來完成。</span><span class="sxs-lookup"><span data-stu-id="775be-105">A majority of configuration can be completed using one of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] tools.</span></span> <span data-ttu-id="775be-106">如需這些工具的詳細資訊，請參閱[PowerPivot 組態工具](power-pivot-configuration-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="775be-106">For more information on the tools, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="775be-107">如果是 SharePoint 2010 伺服器陣列，您必須先安裝 SharePoint 2010 SP1，才可設定 PowerPivot for SharePoint 或使用 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 資料庫伺服器的 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="775be-107">For a SharePoint 2010 farm, SharePoint 2010 SP1 must be installed before you can configure either PowerPivot for SharePoint, or a SharePoint farm that uses a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database server.</span></span> <span data-ttu-id="775be-108">如果您尚未安裝該 Service Pack，請在開始設定伺服器之前先加以安裝。</span><span class="sxs-lookup"><span data-stu-id="775be-108">If you have not yet installed the service pack, install it before you begin configuring the server.</span></span>  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-powershell"></a><span data-ttu-id="775be-109">使用 PowerShell 設定 PowerPivot for SharePoint 的優點</span><span class="sxs-lookup"><span data-stu-id="775be-109">Benefits of Configuring PowerPivot for SharePoint Using PowerShell</span></span>  
 <span data-ttu-id="775be-110">您可以建立 Windows PowerShell (.ps1) 檔案，將組態工作自動化。</span><span class="sxs-lookup"><span data-stu-id="775be-110">You can build Windows PowerShell script (.ps1) files to automate configuration tasks.</span></span> <span data-ttu-id="775be-111">如果您需要可以在任何伺服器上執行的指令碼式安裝和設定步驟，建議使用此方法。</span><span class="sxs-lookup"><span data-stu-id="775be-111">This approach is recommended if you require scripted installation and configuration steps that you can run on any server.</span></span> <span data-ttu-id="775be-112">您可以需要此種指令碼做為災難復原計畫的一部分，才能在發生硬體故障時重建伺服器。</span><span class="sxs-lookup"><span data-stu-id="775be-112">You might require such a script as part of a disaster recovery plan for rebuilding a server in the event of a hardware failure.</span></span>  
  
## <a name="view-a-list-of-the-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="775be-113">在伺服器上檢視 PowerPivot 指令程式的清單</span><span class="sxs-lookup"><span data-stu-id="775be-113">View a list of the PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="775be-114">若要查看 Cmdlet 的內容和範例 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ，請參閱[PowerPivot for SharePoint 的 PowerShell 參考](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)。</span><span class="sxs-lookup"><span data-stu-id="775be-114">To see content and examples of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cmdlets, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>  
  
 <span data-ttu-id="775be-115">使用 PowerShell 檢視 PowerPivot 指令程式的清單：</span><span class="sxs-lookup"><span data-stu-id="775be-115">To use PowerShell to view a list of the PowerPivot cmdlets:</span></span>  
  
1.  <span data-ttu-id="775be-116">使用 [以系統管理員身分執行]\*\*\*\* 選項，開啟 SharePoint 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="775be-116">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="775be-117">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="775be-117">Enter the following command:</span></span>  
  
    ```powershell
    Get-Help *powerpivot*  
    ```  
  
     <span data-ttu-id="775be-118">您應該查看在指令程式名稱中包含 PowerPivot 的指令程式清單。</span><span class="sxs-lookup"><span data-stu-id="775be-118">You should see a list of cmdlets that include PowerPivot in the cmdlet name.</span></span> <span data-ttu-id="775be-119">例如 `Get-PowerPivotServiceApplication`。</span><span class="sxs-lookup"><span data-stu-id="775be-119">For example `Get-PowerPivotServiceApplication`.</span></span> <span data-ttu-id="775be-120">可用的指令程式數目取決於您使用的 Analysis Services 版本。</span><span class="sxs-lookup"><span data-stu-id="775be-120">The number of cmdlets available depends on the version of Analysis Services you are using.</span></span>  
  
    -   <span data-ttu-id="775be-121">SQL Server 2012 SP1 Analysis Services 伺服器附帶的 10 個指令程式是在 SharePoint 模式和 SharePoint 2013 中進行設定。</span><span class="sxs-lookup"><span data-stu-id="775be-121">10 cmdlets with SQL Server 2012 SP1 Analysis Services server configured in SharePoint mode, and SharePoint 2013.</span></span> <span data-ttu-id="775be-122">2012 SP1 版使用新的架構，允許 Analysis Server 從 SharePoint 伺服器陣列外部執行，而且所需的 Windows PowerShell 指令程式管理更少。</span><span class="sxs-lookup"><span data-stu-id="775be-122">The 2012 SP1 version utilizes a new architecture that allows the Analysis Server to run outside the SharePoint farm and requires fewer management Windows PowerShell cmdlets.</span></span>  
  
    -   <span data-ttu-id="775be-123">SQL Server 2012 Analysis Services 伺服器附帶的 17 個指令程式是在 SharePoint 模式和 SharePoint 2010 中進行設定。</span><span class="sxs-lookup"><span data-stu-id="775be-123">17 cmdlets with SQL Server 2012 Analysis Services server configured in SharePoint mode, and SharePoint 2010.</span></span>  
  
     <span data-ttu-id="775be-124">如果清單中未傳回任何命令，或您看到類似 "" 的錯誤訊息 `get-help could not find *powerpivot* in a help file in this session.` ，請參閱本主題中的下一節，以取得有關如何在伺服器上啟用 PowerPivot Cmdlet 的指示。</span><span class="sxs-lookup"><span data-stu-id="775be-124">If no commands are returned in the list or you see an error message similar to "`get-help could not find *powerpivot* in a help file in this session.`", see the next section in this topic for instructions on how to enable the PowerPivot cmdlets on the server.</span></span>  
  
     <span data-ttu-id="775be-125">所有指令程式都有線上說明。</span><span class="sxs-lookup"><span data-stu-id="775be-125">All cmdlets have online help.</span></span> <span data-ttu-id="775be-126">下列範例顯示如何檢視 `New-PowerPivotServiceApplication` 指令程式的線上說明：</span><span class="sxs-lookup"><span data-stu-id="775be-126">The following example shows how to view the online help for the `New-PowerPivotServiceApplication` cmdlet:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Full  
    ```  
  
     <span data-ttu-id="775be-127">或者，若只要檢視範例，影使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="775be-127">Alternatively, to view just the examples, use the following syntax:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Example  
    ```  
  
## <a name="enable-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="775be-128">在伺服器上啟用 PowerPivot 指令程式</span><span class="sxs-lookup"><span data-stu-id="775be-128">Enable PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="775be-129">在您安裝 PowerPivot for SharePoint 並部署伺服器陣列方案之後，可以使用 PowerPivot 指令程式。</span><span class="sxs-lookup"><span data-stu-id="775be-129">PowerPivot cmdlets are available after you install PowerPivot for SharePoint and deploy the farm solution.</span></span> <span data-ttu-id="775be-130">這些方案會在您執行 PowerPivot 組態工具時部署。</span><span class="sxs-lookup"><span data-stu-id="775be-130">The solutions are deployed when you ran the PowerPivot Configuration tool.</span></span> <span data-ttu-id="775be-131">請依照下列步驟啟用指令程式：</span><span class="sxs-lookup"><span data-stu-id="775be-131">Follow these steps to enable the use of cmdlets:</span></span>  
  
1.  <span data-ttu-id="775be-132">使用 [以系統管理員身分執行]\*\*\*\* 選項，開啟 SharePoint 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="775be-132">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="775be-133">執行第一個 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="775be-133">Run the first cmdlet:</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="775be-134">此指令程式會傳回方案的名稱、方案識別碼及 Deployed=False。</span><span class="sxs-lookup"><span data-stu-id="775be-134">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="775be-135">在下個步驟中，您將部署方案。</span><span class="sxs-lookup"><span data-stu-id="775be-135">In the next step, you deploy the solution.</span></span>  
  
3.  <span data-ttu-id="775be-136">執行第二個 Cmdlet 部署方案：</span><span class="sxs-lookup"><span data-stu-id="775be-136">Run the second cmdlet to deploy the solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  <span data-ttu-id="775be-137">關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="775be-137">Close the window.</span></span> <span data-ttu-id="775be-138">再次使用 [以系統管理員身分執行]\*\*\*\* 選項重新開啟該視窗。</span><span class="sxs-lookup"><span data-stu-id="775be-138">Reopen it, again using the **Run as Administrator** option.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="775be-139">相關內容</span><span class="sxs-lookup"><span data-stu-id="775be-139">Related Content</span></span>  
 [<span data-ttu-id="775be-140">管理中心的 PowerPivot 伺服器管理和設定</span><span class="sxs-lookup"><span data-stu-id="775be-140">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="775be-141">PowerPivot 設定工具</span><span class="sxs-lookup"><span data-stu-id="775be-141">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="775be-142">PowerPivot for SharePoint 的 PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="775be-142">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
