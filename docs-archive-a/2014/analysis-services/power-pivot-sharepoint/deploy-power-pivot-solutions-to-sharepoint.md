---
title: 將 PowerPivot 方案部署到 SharePoint |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f202a2b7-34e0-43aa-90d5-c9a085a37c32
author: minewiskan
ms.author: owend
ms.openlocfilehash: 043647988598f932b70cc06e6bb5492d66864372
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598014"
---
# <a name="deploy-powerpivot-solutions-to-sharepoint"></a><span data-ttu-id="8dd0f-102">將 PowerPivot 方案部署到 SharePoint</span><span class="sxs-lookup"><span data-stu-id="8dd0f-102">Deploy PowerPivot Solutions to SharePoint</span></span>
  <span data-ttu-id="8dd0f-103">利用下列指示手動部署兩個方案套件，將 PowerPivot 功能加入至 SharePoint Server 2010 環境。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-103">Use the following instructions to manually deploy two solution packages that add PowerPivot features to a SharePoint Server 2010 environment.</span></span> <span data-ttu-id="8dd0f-104">部署方案是在 SharePoint 2010 伺服器上設定 PowerPivot for SharePoint 的必要步驟。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-104">Deploying the solutions is a required step for configuring PowerPivot for SharePoint on a SharePoint 2010 server.</span></span> <span data-ttu-id="8dd0f-105">若要查看必要步驟的完整清單，請參閱[管理中心的 PowerPivot 服務器管理和](power-pivot-server-administration-and-configuration-in-central-administration.md)設定。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-105">To view the complete list of required steps, see [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md).</span></span>  
  
 <span data-ttu-id="8dd0f-106">或者，您可以使用 PowerPivot 組態工具部署方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-106">Alternatively, you can use the PowerPivot Configuration Tool to deploy the solutions.</span></span> <span data-ttu-id="8dd0f-107">使用組態工具對於單一伺服器安裝來說，是較簡單且更有效率的方式，不過，如果您習慣使用熟悉的工具或是要同時設定多項功能，則建議您使用管理中心和 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-107">Using the configuration tool is easier and more efficient for a single server installation, but you might want to use Central Administration and PowerShell if you prefer using a familiar tool or if you are configuring multiple features at the same time.</span></span> <span data-ttu-id="8dd0f-108">如需使用設定工具的詳細資訊，請參閱[PowerPivot 組態工具](power-pivot-configuration-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-108">For more information about using the configuration tool, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
 <span data-ttu-id="8dd0f-109">在部署方案之前，必須先使用 SQL Server 2012 安裝媒體安裝 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-109">Before deploying the solutions, you must first install PowerPivot for SharePoint using the SQL Server 2012 installation media.</span></span> <span data-ttu-id="8dd0f-110">SQL Server 安裝程式會安裝您將要部署的方案套件。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-110">SQL Server Setup installs the solution packages that you are about to deploy.</span></span>  
  
 <span data-ttu-id="8dd0f-111">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="8dd0f-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="8dd0f-112">必要條件：確認 Web 應用程式使用傳統模式驗證</span><span class="sxs-lookup"><span data-stu-id="8dd0f-112">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>](#bkmk_classic)  
  
 [<span data-ttu-id="8dd0f-113">步驟 1：部署伺服器陣列方案</span><span class="sxs-lookup"><span data-stu-id="8dd0f-113">Step 1: Deploy the Farm Solution</span></span>](#bkmk_farm)  
  
 [<span data-ttu-id="8dd0f-114">步驟 2：將 PowerPivot Web 應用程式方案部署到管理中心</span><span class="sxs-lookup"><span data-stu-id="8dd0f-114">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>](#deployCA)  
  
 [<span data-ttu-id="8dd0f-115">步驟 3：將 PowerPivot Web 應用程式方案部署到其他 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8dd0f-115">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>](#deployUI)  
  
 [<span data-ttu-id="8dd0f-116">重新部署或撤銷方案</span><span class="sxs-lookup"><span data-stu-id="8dd0f-116">Redeploy or retract the Solution</span></span>](#retract)  
  
 [<span data-ttu-id="8dd0f-117">關於 PowerPivot 方案</span><span class="sxs-lookup"><span data-stu-id="8dd0f-117">About the PowerPivot Solutions</span></span>](#intro)  
  
##  <a name="prerequisite-verify-the-web-application-uses-classic-mode-authentication"></a><a name="bkmk_classic"></a> <span data-ttu-id="8dd0f-118">必要條件：驗證 Web 應用程式是否使用傳統模式驗證</span><span class="sxs-lookup"><span data-stu-id="8dd0f-118">Prerequisite: Verify the Web Application uses Classic Mode Authentication</span></span>  
 <span data-ttu-id="8dd0f-119">使用 Windows 傳統模式驗證的 Web 應用程式才支援 PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-119">PowerPivot for SharePoint is only supported for web applications that use Windows-classic mode authentication.</span></span> <span data-ttu-id="8dd0f-120">若要檢查應用程式是否使用傳統模式，請從**sharepoint 2010 管理命令**介面執行下列 PowerShell Cmdlet， `http://<top-level site name>` 並將取代為您的 sharepoint 網站名稱：</span><span class="sxs-lookup"><span data-stu-id="8dd0f-120">To check whether the application uses Classic mode, run the following PowerShell cmdlet from the **SharePoint 2010 Management Shell**, replacing `http://<top-level site name>` with the name of your SharePoint site:</span></span>  
  
```powershell
Get-SPWebApplication http://<top-level site name> | Format-List UseClaimsAuthentication  
```  
  
 <span data-ttu-id="8dd0f-121">傳回值應為 **false**。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-121">The return value should be **false**.</span></span> <span data-ttu-id="8dd0f-122">若為**true**，則無法使用此 web 應用程式來存取 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-122">If it is **true**, you cannot access PowerPivot data with this web application.</span></span>  
  
##  <a name="step-1-deploy-the-farm-solution"></a><a name="bkmk_farm"></a><span data-ttu-id="8dd0f-123">步驟1：部署伺服器陣列方案</span><span class="sxs-lookup"><span data-stu-id="8dd0f-123">Step 1: Deploy the Farm Solution</span></span>  
 <span data-ttu-id="8dd0f-124">本節示範如何使用 PowerShell 部署方案，但是您也可以使用 PowerPivot 組態工具完成此工作。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-124">This section shows you how to deploy solutions using PowerShell, but you can also use the PowerPivot Configuration Tool to complete this task.</span></span> <span data-ttu-id="8dd0f-125">如需詳細資訊，請參閱[設定或修復 PowerPivot for SharePoint 2010 &#40;PowerPivot 設定工具&#41;](../configure-repair-powerpivot-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-125">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="8dd0f-126">此工作只需要在安裝 PowerPivot for SharePoint 之後執行一次。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-126">This task only needs to be performed once, after you install PowerPivot for SharePoint.</span></span>  
  
1.  <span data-ttu-id="8dd0f-127">在安裝 PowerPivot for SharePoint 的伺服器上，使用 [以**系統管理員身分執行**] 選項開啟 SharePoint 2010 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-127">On a server that has an installation of PowerPivot for SharePoint, open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="8dd0f-128">執行下列指令程式加入伺服器陣列方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-128">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="8dd0f-129">此指令程式會傳回方案的名稱、方案識別碼及 Deployed=False。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-129">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="8dd0f-130">在下個步驟中，您將部署方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-130">In the next step, you will deploy the solution.</span></span>  
  
3.  <span data-ttu-id="8dd0f-131">執行下一個指令程式來部署伺服器陣列方案：</span><span class="sxs-lookup"><span data-stu-id="8dd0f-131">Run the next cmdlet to deploy the farm solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
##  <a name="step-2-deploy-the-powerpivot-web-application-solution-to-central-administration"></a><a name="deployCA"></a><span data-ttu-id="8dd0f-132">步驟2：將 PowerPivot Web 應用程式方案部署到管理中心</span><span class="sxs-lookup"><span data-stu-id="8dd0f-132">Step 2: Deploy the PowerPivot Web Application Solution to Central Administration</span></span>  
 <span data-ttu-id="8dd0f-133">部署伺服器陣列方案之後，您必須將 Web 應用程式方案部署到管理中心。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-133">After you deploy the farm solution, you must deploy the Web application solution to Central Administration.</span></span> <span data-ttu-id="8dd0f-134">此步驟會將 PowerPivot 管理儀表板加入至管理中心。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-134">This step adds the PowerPivot Management Dashboard to Central Administration.</span></span>  
  
1.  <span data-ttu-id="8dd0f-135">使用 **[以系統管理員身分執行]** 選項，開啟 SharePoint 2010 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-135">Open a SharePoint 2010 Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="8dd0f-136">執行下列指令程式建立管理中心的參考：</span><span class="sxs-lookup"><span data-stu-id="8dd0f-136">Run the following cmdlet to create a reference to Central Administration:</span></span>  
  
    ```powershell
    $centralAdmin = $(Get-SPWebApplication -IncludeCentralAdministration | Where { $_.IsAdministrationWebApplication -eq $TRUE})  
    ```  
  
3.  <span data-ttu-id="8dd0f-137">執行下列指令程式加入伺服器陣列方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-137">Run the following cmdlet to add the farm solution.</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotWebApp.wsp"  
    ```  
  
     <span data-ttu-id="8dd0f-138">此指令程式會傳回方案的名稱、方案識別碼及 Deployed=False。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-138">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="8dd0f-139">在下個步驟中，您將部署方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-139">In the next step, you will deploy the solution.</span></span>  
  
4.  <span data-ttu-id="8dd0f-140">執行下一個指令程式，將 Web 應用程式方案安裝到管理中心。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-140">Run the next cmdlet to install the web application solution to Central Administration.</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotWebApp.wsp -GACDeployment -Force -WebApplication $centralAdmin  
    ```  
  
 <span data-ttu-id="8dd0f-141">現在 Web 應用程式方案已部署到管理中心，您可以使用管理中心完成所有其餘組態步驟。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-141">Now that the web application solution is deployed to Central Administration, you can use Central Administration to complete all remaining configuration steps.</span></span>  
  
##  <a name="step-3-deploy-the-powerpivot-web-application-solution-to-other-web-applications"></a><a name="deployUI"></a><span data-ttu-id="8dd0f-142">步驟3：將 PowerPivot Web 應用程式方案部署到其他 Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="8dd0f-142">Step 3: Deploy the PowerPivot Web Application Solution to Other Web Applications</span></span>  
 <span data-ttu-id="8dd0f-143">在上一個工作中，您已經將 Powerpivotwebapp.wsp 部署到管理中心。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-143">In the previous task, you deployed Powerpivotwebapp.wsp to Central Administration.</span></span> <span data-ttu-id="8dd0f-144">在本節中，您會在支援 PowerPivot 資料存取的每個現有 Web 應用程式上部署 powerpivotwebapp.wsp。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-144">In this section, you deploy the powerpivotwebapp.wsp on each existing web application that supports PowerPivot data access.</span></span> <span data-ttu-id="8dd0f-145">如果您之後加入更多 Web 應用程式，務必針對其他 Web 應用程式重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-145">If you add more web applications later, be sure to repeat this step for those additional web applications.</span></span>  
  
1.  <span data-ttu-id="8dd0f-146">在管理中心的 [系統設定] 中，按一下 **[管理伺服器陣列方案]**。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-146">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="8dd0f-147">按一下 [ **powerpivotwebapp.wsp**]。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-147">Click **powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="8dd0f-148">按一下 **[部署方案]**。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-148">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="8dd0f-149">在 [**部署至？**] 中，選取您要加入 PowerPivot 功能支援的 SharePoint web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-149">In **Deploy To?**, select the SharePoint web application for which you want to add PowerPivot feature support.</span></span>  
  
5.  <span data-ttu-id="8dd0f-150">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-150">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="8dd0f-151">針對其他也支援 PowerPivot 資料存取的 SharePoint Web 應用程式重複以上步驟。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-151">Repeat for other SharePoint web applications that will also support PowerPivot data access.</span></span>  
  
##  <a name="redeploy-or-retract-the-solution"></a><a name="retract"></a><span data-ttu-id="8dd0f-152">重新部署或撤銷方案</span><span class="sxs-lookup"><span data-stu-id="8dd0f-152">Redeploy or retract the Solution</span></span>  
 <span data-ttu-id="8dd0f-153">雖然 SharePoint 管理中心會提供方案撤銷，但是除非您有系統地排除安裝或修補程式的部署問題，否則不需要撤銷 powerpivotwebapp.wsp 檔。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-153">Although SharePoint Central Administration provides solution retraction, you do not need to retract the powerpivotwebapp.wsp file unless you are systematically troubleshooting an installation or patch deployment problem.</span></span>  
  
1.  <span data-ttu-id="8dd0f-154">在 SharePoint 2010 管理中心的 [系統設定] 中，按一下 **[管理伺服陣列方案]**。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-154">In SharePoint 2010 Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="8dd0f-155">按一下 **[Powerpivotwebapp.wsp]**。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-155">Click **Powerpivotwebapp.wsp**.</span></span>  
  
3.  <span data-ttu-id="8dd0f-156">按一下 **[撤銷方案]**。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-156">Click **Retract Solution**.</span></span>  
  
 <span data-ttu-id="8dd0f-157">如果您遇到伺服器部署問題，而您追蹤至伺服器陣列方案，您可以在 PowerPivot 設定工具中執行 [**修復**] 選項來重新部署它。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-157">If you encounter server deployment issues that you trace back to the farm solution, you can redeploy it by running the **Repair** option in the PowerPivot Configuration Tool.</span></span> <span data-ttu-id="8dd0f-158">透過此工具的修復作業是慣用的方式，因為您需要執行的步驟比較少。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-158">Repair operations via the tool is preferred because it requires fewer steps on your part.</span></span> <span data-ttu-id="8dd0f-159">如需詳細資訊，請參閱[設定或修復 PowerPivot for SharePoint 2010 &#40;PowerPivot 設定工具&#41;](../configure-repair-powerpivot-sharepoint-2010.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-159">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../configure-repair-powerpivot-sharepoint-2010.md).</span></span>  
  
 <span data-ttu-id="8dd0f-160">如果您仍然要重新部署所有方案，請務必以下列順序進行：</span><span class="sxs-lookup"><span data-stu-id="8dd0f-160">If you still want to re-deploy all solutions, be sure to do so in this order:</span></span>  
  
1.  <span data-ttu-id="8dd0f-161">從使用 PowerPivot Web 應用程式方案的所有 SharePoint Web 應用程式撤銷它。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-161">Retract the PowerPivot Web application solution from all SharePoint web applications that use it.</span></span>  
  
2.  <span data-ttu-id="8dd0f-162">撤銷 PowerPivot 伺服陣列方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-162">Retract the PowerPivot farm solution.</span></span>  
  
3.  <span data-ttu-id="8dd0f-163">重新部署 PowerPivot 伺服陣列方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-163">Redeploy the PowerPivot farm solution.</span></span>  
  
4.  <span data-ttu-id="8dd0f-164">將 PowerPivot Web 應用程式方案重新部署至所有 SharePoint Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-164">Redeploy the PowerPivot Web application solution to all SharePoint web applications.</span></span>  
  
##  <a name="about-the-powerpivot-solutions"></a><a name="intro"></a><span data-ttu-id="8dd0f-165">關於 PowerPivot 方案</span><span class="sxs-lookup"><span data-stu-id="8dd0f-165">About the PowerPivot Solutions</span></span>  
 <span data-ttu-id="8dd0f-166">PowerPivot for SharePoint 會使用兩個方案套件，將它的應用程式頁面和程式檔案從伺服陣列部署到個別 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-166">PowerPivot for SharePoint uses two solution packages to deploy its application pages and program files to the farm and to individual web applications.</span></span>  
  
-   <span data-ttu-id="8dd0f-167">伺服器陣列方案為全域所通用，</span><span class="sxs-lookup"><span data-stu-id="8dd0f-167">The farm solution is global.</span></span> <span data-ttu-id="8dd0f-168">這個方案會部署一次，然後自動提供給您之後加入至伺服器陣列的任何新 PowerPivot for SharePoint 伺服器使用。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-168">It is deployed once and then becomes automatically available to any new PowerPivot for SharePoint servers that you add to the farm later.</span></span>  
  
-   <span data-ttu-id="8dd0f-169">此 Web 應用程式方案是應用程式所特有，而且必須部署到伺服器陣列中的每一個 Web 應用程式，包括管理中心 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-169">The web application solution is application-specific and must be deployed to each web application in the farm, including the Central Administration web application.</span></span>  
  
 <span data-ttu-id="8dd0f-170">每一個方案都會以不同方式部署。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-170">Each solution is deployed differently.</span></span>  <span data-ttu-id="8dd0f-171">伺服器陣列方案會在安裝第一個 PowerPivot for SharePoint 執行個體之後部署一次。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-171">The farm solution is deployed once, after the first PowerPivot for SharePoint instance is installed.</span></span> <span data-ttu-id="8dd0f-172">若要部署伺服器陣列方案，您必須使用 PowerPivot 組態工具或 PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-172">To deploy the farm solution, you use the PowerPivot Configuration Tool or PowerShell cmdlets.</span></span>  
  
 <span data-ttu-id="8dd0f-173">此 Web 應用程式方案一開始會部署到管理中心，隨後會將後續方案部署到支援 PowerPivot 資料要求的其他任何 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-173">The web application solution is initially deployed to Central Administration, followed by subsequent solution deployments to any additional web applications that will support requests for PowerPivot data.</span></span> <span data-ttu-id="8dd0f-174">若要將 Web 應用程式方案部署到管理中心，您必須使用 PowerPivot 組態工具或 PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-174">To deploy the web application solution to Central Administration, you must use the PowerPivot Configuration Tool or PowerShell cmdlet.</span></span> <span data-ttu-id="8dd0f-175">如果是所有其他 Web 應用程式，您可以使用管理中心或 PowerShell 來手動部署 Web 應用程式方案。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-175">For all other web applications, you can deploy the web application solution manually using Central Administration or PowerShell.</span></span>  
  
|<span data-ttu-id="8dd0f-176">解決方法</span><span class="sxs-lookup"><span data-stu-id="8dd0f-176">Solution</span></span>|<span data-ttu-id="8dd0f-177">描述</span><span class="sxs-lookup"><span data-stu-id="8dd0f-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8dd0f-178">Powerpivotfarm.wsp</span><span class="sxs-lookup"><span data-stu-id="8dd0f-178">Powerpivotfarm.wsp</span></span>|<span data-ttu-id="8dd0f-179">將 Microsoft.AnalysisServices.SharePoint.Integration.dll 加入至全域組件。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-179">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="8dd0f-180">將 Microsoft.AnalysisServices.ChannelTransport.dll 加入至全域組件。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-180">Adds Microsoft.AnalysisServices.ChannelTransport.dll to the global assembly.</span></span><br /><br /> <span data-ttu-id="8dd0f-181">安裝功能和資源檔，並註冊內容類型。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-181">Installs features and resources files, and registers content types.</span></span><br /><br /> <span data-ttu-id="8dd0f-182">加入 PowerPivot 圖庫和資料摘要庫的文件庫範本。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-182">Adds library templates for PowerPivot Gallery and Data Feed libraries.</span></span><br /><br /> <span data-ttu-id="8dd0f-183">為服務應用程式組態、PowerPivot 管理儀表板、資料重新整理及 PowerPivot 圖庫加入應用程式頁面。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-183">Adds application pages for service application configuration, PowerPivot Management Dashboard, data refresh, and PowerPivot Gallery.</span></span>|  
|<span data-ttu-id="8dd0f-184">[powerpivotwebapp.wsp]</span><span class="sxs-lookup"><span data-stu-id="8dd0f-184">Powerpivotwebapp.wsp</span></span>|<span data-ttu-id="8dd0f-185">將 Microsoft.AnalysisServices.SharePoint.Integration.dll 資源檔加入至 Web 前端的 Web Server Extensions 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-185">Adds Microsoft.AnalysisServices.SharePoint.Integration.dll resources files to the web server extensions folder on the Web front-end.</span></span><br /><br /> <span data-ttu-id="8dd0f-186">將 PowerPivot Web 服務加入至 Web 前端。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-186">Adds PowerPivot Web service to the Web-front end.</span></span><br /><br /> <span data-ttu-id="8dd0f-187">加入 PowerPivot 圖庫產生的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="8dd0f-187">Adds thumbnail image generation for PowerPivot Gallery.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dd0f-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd0f-188">See Also</span></span>  
 <span data-ttu-id="8dd0f-189">[升級 PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="8dd0f-189">[Upgrade PowerPivot for SharePoint](../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="8dd0f-190">[管理中心的 PowerPivot 服務器管理和設定](power-pivot-server-administration-and-configuration-in-central-administration.md) </span><span class="sxs-lookup"><span data-stu-id="8dd0f-190">[PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) </span></span>  
 [<span data-ttu-id="8dd0f-191">使用 Windows PowerShell 的 PowerPivot 設定</span><span class="sxs-lookup"><span data-stu-id="8dd0f-191">PowerPivot Configuration using Windows PowerShell</span></span>](power-pivot-configuration-using-windows-powershell.md)  
