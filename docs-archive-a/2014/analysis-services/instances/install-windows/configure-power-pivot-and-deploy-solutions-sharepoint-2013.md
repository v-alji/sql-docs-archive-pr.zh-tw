---
title: 設定 PowerPivot 及部署方案 (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6401fd92-f43b-450e-8298-12db644c25bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7eaea7f9c490fd320d6dbd0777519eeca218b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688362"
---
# <a name="configure-powerpivot-and-deploy-solutions-sharepoint-2013"></a><span data-ttu-id="0b903-102">設定 PowerPivot 及部署方案 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="0b903-102">Configure PowerPivot and Deploy Solutions (SharePoint 2013)</span></span>
  <span data-ttu-id="0b903-103">本主題將描述如何部署和設定 [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] 中 PowerPivot 功能的中介層增強功能，包括 PowerPivot 圖庫、排程資料重新整理、管理儀表板和資料提供者。</span><span class="sxs-lookup"><span data-stu-id="0b903-103">This topics describes the deployment and configuration of middle-tier enhancements to the PowerPivot features in [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] including PowerPivot Gallery, Schedule data refresh, Management Dashboard, and data providers.</span></span> <span data-ttu-id="0b903-104">請執行 **PowerPivot for SharePoint 2013 組態** 工具以完成下列作業：</span><span class="sxs-lookup"><span data-stu-id="0b903-104">Run **PowerPivot for SharePoint 2013 Configuration** tool to complete the following:</span></span>  
  
-   <span data-ttu-id="0b903-105">部署 SharePoint 方案檔。</span><span class="sxs-lookup"><span data-stu-id="0b903-105">Deploy SharePoint solution files.</span></span>  
  
-   <span data-ttu-id="0b903-106">建立 PowerPivot 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="0b903-106">Create a PowerPivot service application.</span></span>  
  
-   <span data-ttu-id="0b903-107">將 Excel Services 應用程式設定為使用 SharePoint 模式的 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0b903-107">Configure an Excel Services Application to use an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode.</span></span> <span data-ttu-id="0b903-108">如需後端服務以及 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 在 SharePoint 模式中安裝伺服器的相關資訊，請參閱 [PowerPivot for SharePoint 2013 安裝](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)。</span><span class="sxs-lookup"><span data-stu-id="0b903-108">For information on backend services and installing a [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] server in SharePoint mode, see [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode).</span></span>  
  
 <span data-ttu-id="0b903-109">如需安裝 PowerPivot for SharePoint 2013 Configuration tool 的詳細資訊，請參閱 [安裝或卸載 PowerPivot for SharePoint 增益集 &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span><span class="sxs-lookup"><span data-stu-id="0b903-109">For information on installing the PowerPivot for SharePoint 2013 Configuration tool, see [Install or Uninstall the PowerPivot for SharePoint Add-in &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)</span></span>  
  
 <span data-ttu-id="0b903-110">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="0b903-110">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="0b903-111">執行 PowerPivot for SharePoint 2013 組態</span><span class="sxs-lookup"><span data-stu-id="0b903-111">Run PowerPivot for SharePoint 2013 configuration</span></span>](#bkmk_run_configuration_tool)  
  
 [<span data-ttu-id="0b903-112">確認 PowerPivot 組態</span><span class="sxs-lookup"><span data-stu-id="0b903-112">Verify PowerPivot Configuration</span></span>](#bkmk_verify_powerpivot)  
  
 [<span data-ttu-id="0b903-113">針對問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0b903-113">Troubleshoot Issues</span></span>](#bkmk_troubleshoot_issues)  
  
##  <a name="run-powerpivot-for-sharepoint-2013-configuration"></a><a name="bkmk_run_configuration_tool"></a> <span data-ttu-id="0b903-114">執行 PowerPivot for SharePoint 2013 設定</span><span class="sxs-lookup"><span data-stu-id="0b903-114">Run PowerPivot for SharePoint 2013 configuration</span></span>  
 <span data-ttu-id="0b903-115">**注意** ： [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 安裝精靈會為 [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)]安裝兩個不同的組態工具。</span><span class="sxs-lookup"><span data-stu-id="0b903-115">**Note:** The [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] setup wizard installs two different configuration tools for [!INCLUDE[ssGeminiLong](../../../includes/ssgeminilong-md.md)].</span></span> <span data-ttu-id="0b903-116">它們各支援不同的 SharePoint 版本。</span><span class="sxs-lookup"><span data-stu-id="0b903-116">They each support a different version of SharePoint.</span></span>  
  
|<span data-ttu-id="0b903-117">名稱</span><span class="sxs-lookup"><span data-stu-id="0b903-117">Name</span></span>|<span data-ttu-id="0b903-118">描述</span><span class="sxs-lookup"><span data-stu-id="0b903-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="0b903-119">PowerPivot for SharePoint 2013 組態</span><span class="sxs-lookup"><span data-stu-id="0b903-119">PowerPivot for SharePoint 2013 Configuration</span></span>|<span data-ttu-id="0b903-120">SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="0b903-120">SharePoint 2013</span></span>|  
|<span data-ttu-id="0b903-121">PowerPivot 組態工具</span><span class="sxs-lookup"><span data-stu-id="0b903-121">PowerPivot Configuration Tool</span></span>|<span data-ttu-id="0b903-122">SharePoint 2010 含 SharePoint 2010 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="0b903-122">SharePoint 2010 with SharePoint 2010 Service Pack 1 (SP1)</span></span>|  
  
 <span data-ttu-id="0b903-123">**注意：** 若要完成下列步驟，您必須是伺服器陣列管理員。</span><span class="sxs-lookup"><span data-stu-id="0b903-123">**Note:** To complete the following steps, you must be a farm administrator.</span></span> <span data-ttu-id="0b903-124">如果您看到類似下列的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0b903-124">If you see an error message similar to the following:</span></span>  
  
-   <span data-ttu-id="0b903-125">「使用者不是伺服器陣列管理員。</span><span class="sxs-lookup"><span data-stu-id="0b903-125">"The user is not a farm administrator.</span></span> <span data-ttu-id="0b903-126">請解決驗證失敗問題，並再試一次。」</span><span class="sxs-lookup"><span data-stu-id="0b903-126">Please address the validation failures and try again."</span></span>  
  
 <span data-ttu-id="0b903-127">請以安裝 SharePoint 的帳戶登入或將安裝帳戶設定為 SharePoint 管理中心網站的主要管理員。</span><span class="sxs-lookup"><span data-stu-id="0b903-127">Either login as the account that installed SharePoint or configure the setup account as the primary administrator of the SharePoint Central Administration Site.</span></span>  
  
1.  <span data-ttu-id="0b903-128">在 **[開始]** 功能表上，依序按一下 **[所有程式]**、[ [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]]、 **[組態工具]** 和 **[PowerPivot For SharePoint 2013 組態]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-128">On the **Start** menu, click **All Programs**, and then click [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], click **Configuration Tools**, and then click **PowerPivot For SharePoint 2013 Configuration**.</span></span> <span data-ttu-id="0b903-129">只有在本機伺服器上安裝了 PowerPivot for SharePoint 時，才會列出此工具。</span><span class="sxs-lookup"><span data-stu-id="0b903-129">Toold is listed only when PowerPivot for SharePoint is installed on the local server.</span></span>  
  
2.  <span data-ttu-id="0b903-130">按一下 **[設定或修復 PowerPivot for SharePoint]** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-130">Click **Configure or Repair PowerPivot for SharePoint** and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="0b903-131">此工具會執行驗證，以確認 PowerPivot 的目前狀態，而且需要哪些步驟來完成組態。</span><span class="sxs-lookup"><span data-stu-id="0b903-131">The tool runs validation to verify the current state of PowerPivot and what steps are required to complete configuration.</span></span> <span data-ttu-id="0b903-132">將視窗展開為全螢幕。</span><span class="sxs-lookup"><span data-stu-id="0b903-132">Expand the window to full size.</span></span> <span data-ttu-id="0b903-133">您應該會在視窗底部看到一個按鈕列，其中包含 **[驗證]** 、 **[執行]** 和 **[結束]** 命令。</span><span class="sxs-lookup"><span data-stu-id="0b903-133">You should see a button bar at the bottom of the window that includes **Validate**, **Run**, and **Exit** commands.</span></span>  
  
4.  <span data-ttu-id="0b903-134">在 **[參數]** 索引標籤上：</span><span class="sxs-lookup"><span data-stu-id="0b903-134">On the **Parameters** tab:</span></span>  
  
    1.  <span data-ttu-id="0b903-135">**預設帳戶使用者名稱**：輸入預設帳戶的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="0b903-135">**Default Account UserName**: Enter a domain user account for the default account.</span></span> <span data-ttu-id="0b903-136">此帳戶將用來佈建服務，包括 PowerPivot 服務應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="0b903-136">This account will be used to provision services, including the PowerPivot service application pool.</span></span> <span data-ttu-id="0b903-137">請勿指定內建帳戶，例如 Network Service 或 Local System。</span><span class="sxs-lookup"><span data-stu-id="0b903-137">Do not specify a built-in account such as Network Service or Local System.</span></span> <span data-ttu-id="0b903-138">此工具會封鎖指定內建帳戶的組態。</span><span class="sxs-lookup"><span data-stu-id="0b903-138">The tool blocks configurations that specify built-in accounts.</span></span>  
  
    2.  <span data-ttu-id="0b903-139">**資料庫伺服器**：您可以使用支援 SharePoint 伺服器陣列的 SQL Server Database Engine。</span><span class="sxs-lookup"><span data-stu-id="0b903-139">**Database Server**: You can use SQL Server Database engine that is supported for the SharePoint farm.</span></span>  
  
    3.  <span data-ttu-id="0b903-140">**複雜密碼**：輸入複雜密碼。</span><span class="sxs-lookup"><span data-stu-id="0b903-140">**Passphrase**: Enter a passphrase.</span></span> <span data-ttu-id="0b903-141">如果是建立新的 SharePoint 伺服器陣列，則在您將伺服器或應用程式加入至該 SharePoint 伺服器陣列時，都會使用此複雜密碼。</span><span class="sxs-lookup"><span data-stu-id="0b903-141">If you are creating a new SharePoint farm, the passphrase is used whenever you add a server or application to the SharePoint farm.</span></span> <span data-ttu-id="0b903-142">如果伺服器陣列已存在，則輸入可讓您將伺服器應用程式加入至該伺服器陣列的複雜密碼。</span><span class="sxs-lookup"><span data-stu-id="0b903-142">If the farm already exists, enter the passphrase that allows you to add a server application to the farm.</span></span>  
  
    4.  <span data-ttu-id="0b903-143">**適用於 Excel Services 的 PowerPivot 伺服器**：輸入 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint 模式伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0b903-143">**PowerPivot Server for Excel Services**: Type the name of an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] SharePoint mode server.</span></span> <span data-ttu-id="0b903-144">在單一伺服器部署中，這個名稱與資料庫伺服器相同。</span><span class="sxs-lookup"><span data-stu-id="0b903-144">In a single-server deployment, it is the same as the database server.</span></span> `[ServerName]\powerpivot`  
  
    5.  <span data-ttu-id="0b903-145">按一下左邊視窗中的 **[建立網站集合]** 。</span><span class="sxs-lookup"><span data-stu-id="0b903-145">Click **Create Site Collection** in the left window.</span></span> <span data-ttu-id="0b903-146">請記下 **[網站 URL]** ，以便在後續步驟中參考。</span><span class="sxs-lookup"><span data-stu-id="0b903-146">Note **Site URL** so you can reference it in later steps.</span></span> <span data-ttu-id="0b903-147">如果尚未設定 SharePoint 伺服器，組態精靈會將 Web 應用程式和網站集合 URL 預設為 `http://[ServerName]`的根目錄。</span><span class="sxs-lookup"><span data-stu-id="0b903-147">If the SharePoint server is not already configured, then the configuration wizard defaults the web application, and site collection URLs to the root of `http://[ServerName]`.</span></span> <span data-ttu-id="0b903-148">若要修改預設值，請在左邊視窗中檢閱下列頁面： **[建立預設 Web 應用程式]** 和 **[部署 Web 應用程式方案]**</span><span class="sxs-lookup"><span data-stu-id="0b903-148">To modify the defaults review the following pages in the left window: **Create Default Web application** and **Deploy Web Application Solution**</span></span>  
  
5.  <span data-ttu-id="0b903-149">(選擇性) 檢閱用來完成每個動作的其餘輸入值。</span><span class="sxs-lookup"><span data-stu-id="0b903-149">Optionally, review the remaining input values used to complete each action.</span></span> <span data-ttu-id="0b903-150">按一下左邊視窗中的每個動作，查看並檢閱動作的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0b903-150">Click each action in the left window to see and review the details of the action.</span></span> <span data-ttu-id="0b903-151">如需每一項的詳細資訊，請參閱本主題中的「 [設定或修復 PowerPivot for SharePoint 2010 &#40;PowerPivot 設定&#41;工具 ](../../configure-repair-powerpivot-sharepoint-2010.md) 中用來設定伺服器的輸入值」一節。</span><span class="sxs-lookup"><span data-stu-id="0b903-151">For more information about each one, see the section "Input values used to configure the server in [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md) in this topic.</span></span>  
  
6.  <span data-ttu-id="0b903-152">選擇性地移除您不想在此時處理的任何動作。</span><span class="sxs-lookup"><span data-stu-id="0b903-152">Optionally, remove any actions that you do not want to process at this time.</span></span> <span data-ttu-id="0b903-153">例如，如果您想要在稍後設定 Secure Store Service，請按一下 **[設定 Secure Store Service]**，然後清除 **[在工作清單中包含這個動作]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="0b903-153">For example, if you want to configure Secure Store Service later, click **Configure Secure Store Service**, and then clear the checkbox **Include this action in the task list**.</span></span>  
  
7.  <span data-ttu-id="0b903-154">按一下 **[驗證]** ，檢查此工具是否有足夠的資訊來處理清單中的動作。</span><span class="sxs-lookup"><span data-stu-id="0b903-154">Click **Validate** to check whether the tool has sufficient information to process the actions in the list.</span></span> <span data-ttu-id="0b903-155">如果您看到驗證錯誤，請按一下左窗格中的警告，查看驗證錯誤的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0b903-155">If you see validation errors, click the warnings in the left pane to see details of the validation error.</span></span> <span data-ttu-id="0b903-156">更正任何驗證錯誤，然後再按一下 **[驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="0b903-156">Correct any validation errors and then click **Validate** again.</span></span>  
  
8.  <span data-ttu-id="0b903-157">按一下 **[執行]** ，處理工作清單中的所有動作。</span><span class="sxs-lookup"><span data-stu-id="0b903-157">Click **Run** to process all of the actions in the task list.</span></span> <span data-ttu-id="0b903-158">請注意， **[執行]** 只在驗證動作之後才可供使用。</span><span class="sxs-lookup"><span data-stu-id="0b903-158">Note that **Run** becomes available after you validate the actions.</span></span> <span data-ttu-id="0b903-159">如果 **[執行]** 未啟用，請先按一下 **[驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="0b903-159">If **Run** is not enabled, click **Validate** first.</span></span>  
  
 <span data-ttu-id="0b903-160">如需詳細資訊，請參閱 [設定或修復 PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="0b903-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../configure-repair-powerpivot-sharepoint-2010.md)</span></span>  
  
##  <a name="verify-powerpivot-configuration"></a><a name="bkmk_verify_powerpivot"></a> <span data-ttu-id="0b903-161">驗證 PowerPivot 設定</span><span class="sxs-lookup"><span data-stu-id="0b903-161">Verify PowerPivot Configuration</span></span>  
 <span data-ttu-id="0b903-162">**服務：**</span><span class="sxs-lookup"><span data-stu-id="0b903-162">**Services:**</span></span>  
  
1.  <span data-ttu-id="0b903-163">在 [管理中心] 的 [系統設定] 中，按一下 [ **管理伺服器上的服務**]。</span><span class="sxs-lookup"><span data-stu-id="0b903-163">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="0b903-164">確認 **SQL Server Analysis Services** 和 **SQL Server PowerPivot 系統服務** 都已啟動。</span><span class="sxs-lookup"><span data-stu-id="0b903-164">Verify that **SQL Server Analysis Services** and **SQL Server PowerPivot System Service** are started.</span></span>  
  
 <span data-ttu-id="0b903-165">**伺服器陣列功能：**</span><span class="sxs-lookup"><span data-stu-id="0b903-165">**Farm Feature:**</span></span>  
  
1.  <span data-ttu-id="0b903-166">在管理中心的 [系統設定] 中，按一下 **[管理伺服器陣列功能]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-166">In Central Administration, in System Settings, click **Manage farm features**.</span></span>  
  
2.  <span data-ttu-id="0b903-167">確認 **[PowerPivot 整合功能]** 為 **[使用中]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-167">Verify that **PowerPivot Integration Feature** is **Active**.</span></span>  
  
 <span data-ttu-id="0b903-168">**網站集合功能：**</span><span class="sxs-lookup"><span data-stu-id="0b903-168">**Site Collection Feature:**</span></span>  
  
1.  <span data-ttu-id="0b903-169">瀏覽至組態工具所建立的網站 URL。</span><span class="sxs-lookup"><span data-stu-id="0b903-169">Browse to your site URL that was created by the Configuration tool.</span></span>  
  
     <span data-ttu-id="0b903-170">按一下 [ **設定**![SharePoint 設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")]，然後按一下 [ **網站設定**]。</span><span class="sxs-lookup"><span data-stu-id="0b903-170">Click **Settings**![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings"), and then click **Site Settings**.</span></span>  
  
     <span data-ttu-id="0b903-171">按一下 [ **網站集合功能**]。</span><span class="sxs-lookup"><span data-stu-id="0b903-171">Click **Site Collection Features**.</span></span>  
  
2.  <span data-ttu-id="0b903-172">確認 **[網站集合的 PowerPivot 功能整合]** 為 **[使用中]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-172">Verify that **PowerPivot Feature Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="0b903-173">**PowerPivot 服務應用程式：**</span><span class="sxs-lookup"><span data-stu-id="0b903-173">**PowerPivot Service Application:**</span></span>  
  
1.  <span data-ttu-id="0b903-174">在管理中心的 **[應用程式管理]** 中，按一下 **[管理服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-174">In Central Administration, in the **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="0b903-175">確認服務應用程式狀態為 **[已啟動]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-175">Verify the service application status is **started**.</span></span> <span data-ttu-id="0b903-176">預設名稱是 **[預設的 PowerPivot 服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-176">The default name is **Default PowerPivot Service Application**.</span></span>  
  
     <span data-ttu-id="0b903-177">按一下服務應用程式的名稱，即可針對已開啟的服務應用程式開啟 PowerPivot 管理儀表板。</span><span class="sxs-lookup"><span data-stu-id="0b903-177">Click the name of the services application to open the PowerPivot Management Dashboard for the service application opens.</span></span> <span data-ttu-id="0b903-178">在第一次使用時，需要數分鐘才能載入儀表板。</span><span class="sxs-lookup"><span data-stu-id="0b903-178">On first use, the dashboard takes several minutes to load.</span></span>  
  
 <span data-ttu-id="0b903-179">如需詳細資訊，請參閱 [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation)。</span><span class="sxs-lookup"><span data-stu-id="0b903-179">For more information, see [Verify a PowerPivot for SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).</span></span>  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk_troubleshoot_issues"></a> <span data-ttu-id="0b903-180">針對問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="0b903-180">Troubleshoot Issues</span></span>  
 <span data-ttu-id="0b903-181">為了協助疑難排解問題，建議您最好先確認診斷記錄是否已啟用。</span><span class="sxs-lookup"><span data-stu-id="0b903-181">To assist in troubleshooting issues, it is a good idea to verify the diagnostic logging is enabled.</span></span>  
  
1.  <span data-ttu-id="0b903-182">在 SharePoint 管理中心內，按一下 **[監視]** ，然後按一下 **[設定 Usage and Health Data Collection]**。</span><span class="sxs-lookup"><span data-stu-id="0b903-182">In SharePoint Central Administration, click **Monitoring** and then click **Configure usage and health data collection**.</span></span>  
  
2.  <span data-ttu-id="0b903-183">確認已選取 **[啟用使用狀況資料收集]** 。</span><span class="sxs-lookup"><span data-stu-id="0b903-183">Verify **Enable usage data collection** is selected.</span></span>  
  
3.  <span data-ttu-id="0b903-184">確認已選取下列事件：</span><span class="sxs-lookup"><span data-stu-id="0b903-184">Verify the following events are selected:</span></span>  
  
    -   <span data-ttu-id="0b903-185">教育遙測系統使用欄位定義</span><span class="sxs-lookup"><span data-stu-id="0b903-185">Definition of usage fields for Education telemetry</span></span>  
  
    -   <span data-ttu-id="0b903-186">PowerPivot 連接</span><span class="sxs-lookup"><span data-stu-id="0b903-186">PowerPivot Connects</span></span>  
  
    -   <span data-ttu-id="0b903-187">PowerPivot 載入資料使用量</span><span class="sxs-lookup"><span data-stu-id="0b903-187">PowerPivot Load Data Usage</span></span>  
  
    -   <span data-ttu-id="0b903-188">PowerPivot 查詢使用量</span><span class="sxs-lookup"><span data-stu-id="0b903-188">PowerPivot Query Usage</span></span>  
  
    -   <span data-ttu-id="0b903-189">PowerPivot 卸載資料使用量</span><span class="sxs-lookup"><span data-stu-id="0b903-189">PowerPivot Unload Data Usage</span></span>  
  
4.  <span data-ttu-id="0b903-190">確認已選取 **[啟用健康情況資料收集]** 。</span><span class="sxs-lookup"><span data-stu-id="0b903-190">Verify **Enable health data collection** is selected.</span></span>  
  
5.  <span data-ttu-id="0b903-191">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0b903-191">Click **OK**.</span></span>  
  
 <span data-ttu-id="0b903-192">如需有關疑難排解資料重新整理問題的詳細資訊，請參閱 [疑難排解 PowerPivot 資料](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) 重新整理 (https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="0b903-192">For more information on trouble shooting data refresh, see [Troubleshooting PowerPivot Data Refresh](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).</span></span>  
  
 <span data-ttu-id="0b903-193">如需有關組態工具的詳細資訊，請參閱＜ [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0b903-193">For more information on the configuration tool, see [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).</span></span>  
  
  
