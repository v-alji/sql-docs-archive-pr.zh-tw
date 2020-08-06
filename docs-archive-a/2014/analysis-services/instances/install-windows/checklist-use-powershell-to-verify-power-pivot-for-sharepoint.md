---
title: 檢查清單：使用 PowerShell 驗證 PowerPivot for SharePoint |Microsoft Docs
ms.custom: ''
ms.date: 07/20/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 73a13f05-3450-411f-95f9-4b6167cc7607
author: minewiskan
ms.author: owend
ms.openlocfilehash: 001b3fae82851b9ec08b0383bb3db9e6d011ae32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688361"
---
# <a name="checklist-use-powershell-to-verify-powerpivot-for-sharepoint"></a><span data-ttu-id="814c0-102">檢查清單：使用 PowerShell 驗證 PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="814c0-102">CheckList: Use PowerShell to Verify PowerPivot for SharePoint</span></span>
  <span data-ttu-id="814c0-103">一定要通過穩固的驗證測試來確認您的服務和資料可運作， [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 安裝或復原作業才會是完整的。</span><span class="sxs-lookup"><span data-stu-id="814c0-103">No [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] installation or recovery operation is complete without a solid verification test pass that confirms your services and data are operational.</span></span> <span data-ttu-id="814c0-104">在本文中，我們會示範如何使用 Windows PowerShell 執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="814c0-104">In this article, we show you how to perform these steps using Windows PowerShell.</span></span> <span data-ttu-id="814c0-105">我們將每個步驟放在各自的章節中，好讓您可以直接前往特定工作。</span><span class="sxs-lookup"><span data-stu-id="814c0-105">We put each step into its own section so that you can go straight to specific tasks.</span></span> <span data-ttu-id="814c0-106">例如，請執行本主題＜ [資料庫](#bkmk_databases) ＞一節中的指令碼來驗證服務應用程式和內容資料庫的名稱，以便排程這些應用程式或資料庫進行維護或備份。</span><span class="sxs-lookup"><span data-stu-id="814c0-106">For example, run the script in the [Databases](#bkmk_databases) section of this topic to verify the name of the service application and content databases if you want to schedule them for maintenance or backup.</span></span>

|||
|-|-|
|<span data-ttu-id="814c0-107">![PowerShell 相關內容](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="814c0-107">![PowerShell related content](../../../reporting-services/media/rs-powershellicon.jpg "PowerShell related content")</span></span>|<span data-ttu-id="814c0-108">本主題的底部包含了完整的 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="814c0-108">A full PowerShell script is included at the bottom of the topic.</span></span> <span data-ttu-id="814c0-109">請使用完整指令碼做為起點來建立自訂指令碼，以便稽核完整的 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 部署。</span><span class="sxs-lookup"><span data-stu-id="814c0-109">Use the full script as a starting point to build a custom script for auditing your full [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] deployment.</span></span>|

||
|-|
|<span data-ttu-id="814c0-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="814c0-110">**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010</span></span>|

 <span data-ttu-id="814c0-111">**本主題內容**：以下目錄中的字母項目對應到圖表的區域。</span><span class="sxs-lookup"><span data-stu-id="814c0-111">**In this topic**: The lettered items in the following the TOC correspond to areas of the diagram.</span></span> <span data-ttu-id="814c0-112">此圖表將說明</span><span class="sxs-lookup"><span data-stu-id="814c0-112">The diagram illustrates the</span></span>

|||
|-|-|
|[<span data-ttu-id="814c0-113">準備您的 PowerShell 環境</span><span class="sxs-lookup"><span data-stu-id="814c0-113">Prepare your PowerShell environment</span></span>](#bkmk_prerequisites)<br /><br /> [<span data-ttu-id="814c0-114">徵兆和建議的動作</span><span class="sxs-lookup"><span data-stu-id="814c0-114">Symptoms and Recommended Actions</span></span>](#bkmk_symptoms)<br /><br /> <span data-ttu-id="814c0-115">**(A)** [Analysis Services Windows 服務](#bkmk_windows_service)</span><span class="sxs-lookup"><span data-stu-id="814c0-115">**(A)** [Analysis Services Windows Service](#bkmk_windows_service)</span></span><br /><br /> <span data-ttu-id="814c0-116">\*\* (B) \*\* [PowerPivotSystemService 和 PowerPivotEngineService](#bkmk_engine_and_system_service)</span><span class="sxs-lookup"><span data-stu-id="814c0-116">**(B)** [PowerPivotSystemService and PowerPivotEngineService](#bkmk_engine_and_system_service)</span></span><br /><br /> <span data-ttu-id="814c0-117">**(C)** [PowerPivot 服務應用程式與 Proxy](#bkmk_powerpivot_service_application)</span><span class="sxs-lookup"><span data-stu-id="814c0-117">**(C)** [PowerPivot Service Application(s) and proxies](#bkmk_powerpivot_service_application)</span></span><br /><br /> <span data-ttu-id="814c0-118">**(D)** [資料庫](#bkmk_databases)</span><span class="sxs-lookup"><span data-stu-id="814c0-118">**(D)** [Databases](#bkmk_databases)</span></span><br /><br /> [<span data-ttu-id="814c0-119">SharePoint 功能</span><span class="sxs-lookup"><span data-stu-id="814c0-119">SharePoint Features</span></span>](#bkmk_features)<br /><br /> [<span data-ttu-id="814c0-120">計時器工作</span><span class="sxs-lookup"><span data-stu-id="814c0-120">Timer Jobs</span></span>](#bkmk_timer_jobs)<br /><br /> [<span data-ttu-id="814c0-121">健全狀況規則</span><span class="sxs-lookup"><span data-stu-id="814c0-121">Health Rules</span></span>](#bkmk_health_rules)<br /><br /> <span data-ttu-id="814c0-122">**(E)** [Windows 和 ULS 記錄](#bkmk_logs)</span><span class="sxs-lookup"><span data-stu-id="814c0-122">**(E)** [Windows and ULS Logs](#bkmk_logs)</span></span><br /><br /> [<span data-ttu-id="814c0-123">MSOLAP 提供者</span><span class="sxs-lookup"><span data-stu-id="814c0-123">MSOLAP Provider</span></span>](#bkmk_msolap)<br /><br /> [<span data-ttu-id="814c0-124">ADOMD.Net 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="814c0-124">ADOMD.Net client Library</span></span>](#bkmk_adomd)<br /><br /> [<span data-ttu-id="814c0-125">健全狀況資料收集規則</span><span class="sxs-lookup"><span data-stu-id="814c0-125">Health Data Collection Rules</span></span>](#bkmk_health_collection)<br /><br /> [<span data-ttu-id="814c0-126">方案</span><span class="sxs-lookup"><span data-stu-id="814c0-126">Solutions</span></span>](#bkmk_solutions)<br /><br /> [<span data-ttu-id="814c0-127">手動驗證步驟</span><span class="sxs-lookup"><span data-stu-id="814c0-127">Manual Verification Steps</span></span>](#bkmk_manual)<br /><br /> [<span data-ttu-id="814c0-128">其他資源</span><span class="sxs-lookup"><span data-stu-id="814c0-128">More Resources</span></span>](#bkmk_more_resources)<br /><br /> [<span data-ttu-id="814c0-129">完整 PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="814c0-129">Full PowerShell Script</span></span>](#bkmk_full_script)|<span data-ttu-id="814c0-130">![powershell 的 powerpivot 驗證](../../../sql-server/install/media/ssas-powershell-component-verification.png "powershell 的 powerpivot 驗證")</span><span class="sxs-lookup"><span data-stu-id="814c0-130">![powershell verification of powerpivot](../../../sql-server/install/media/ssas-powershell-component-verification.png "powershell verification of powerpivot")</span></span>|

##  <a name="prepare-your-powershell-environment"></a><a name="bkmk_prerequisites"></a><span data-ttu-id="814c0-131">準備您的 PowerShell 環境</span><span class="sxs-lookup"><span data-stu-id="814c0-131">Prepare your PowerShell environment</span></span>
 <span data-ttu-id="814c0-132">本節的步驟會準備您的 PowerShell 環境。</span><span class="sxs-lookup"><span data-stu-id="814c0-132">The steps in this section prepare your PowerShell environment.</span></span> <span data-ttu-id="814c0-133">根據目前設定指令碼環境的方式，可能不需要這些步驟。</span><span class="sxs-lookup"><span data-stu-id="814c0-133">The steps may not be required, depending on how your scripting environment is currently configured.</span></span>

 <span data-ttu-id="814c0-134">**PowerShell 權限**</span><span class="sxs-lookup"><span data-stu-id="814c0-134">**PowerShell Permissions**</span></span>

 <span data-ttu-id="814c0-135">使用 **系統管理權限**開啟 PowerShell 視窗或 PowerShell ISE (整合式指令碼環境)。</span><span class="sxs-lookup"><span data-stu-id="814c0-135">Open a Powershell window or the PowerShell ISE (Integrated Scripting Environment) with **administrative privileges**.</span></span> <span data-ttu-id="814c0-136">如果當您執行命令時沒有系統管理權限，您將會看到類似下面的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="814c0-136">If you do not have administrative privileges when you run commands, you will see an error message similar to the following:</span></span>

 <span data-ttu-id="814c0-137">Get-SPLogEvent：您必須擁有電腦的 **系統管理員權限** 才能執行此指令程式。</span><span class="sxs-lookup"><span data-stu-id="814c0-137">Get-SPLogEvent : You need to have Machine **administrator privileges** to run this cmdlet.</span></span>

 <span data-ttu-id="814c0-138">**SharePoint 和 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** 模組</span><span class="sxs-lookup"><span data-stu-id="814c0-138">**SharePoint and [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]** Module</span></span>

 <span data-ttu-id="814c0-139">如果當您執行 SharePoint 相關的指令程式時看到類似下面的錯誤訊息，請執行 Add-PSSnapin 命令：</span><span class="sxs-lookup"><span data-stu-id="814c0-139">If you see an error message similar to the following when you run SharePoint related cmdlets, run the Add-PSSnapin command:</span></span>

 <span data-ttu-id="814c0-140">**無法辨識**'Get-PowerPivotSystemService' 詞彙是否為 Cmdlet、函數、指令檔或可執行程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="814c0-140">The term 'Get-PowerPivotSystemService' **is not recognized as the name of a cmdlet**, function, script file, or operable program.</span></span> <span data-ttu-id="814c0-141">請檢查名稱拼字，如果名稱含有路徑，請確認路徑正確，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="814c0-141">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>

```
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0
```

 <span data-ttu-id="814c0-142">**Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="814c0-142">**Windows PowerShell**</span></span>

 <span data-ttu-id="814c0-143">如需有關 PowerShell ISE 的詳細資訊，請參閱＜ [Windows PowerShell ISE 簡介](https://technet.microsoft.com/library/dd315244.aspx) ＞和＜ [使用 Windows Powershell 管理 SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx)＞。</span><span class="sxs-lookup"><span data-stu-id="814c0-143">For more information on the PowerShell ISE, see [Introducing the Windows PowerShell ISE](https://technet.microsoft.com/library/dd315244.aspx) and [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878\(v=office.15\).aspx).</span></span>

|||
|-|-|
|<span data-ttu-id="814c0-144">![sharepoint 一般應用程式設定中的 powerpivot](../../../sql-server/install/media/ssas-powerpivot-logo.png "sharepoint 一般應用程式設定中的 powerpivot")</span><span class="sxs-lookup"><span data-stu-id="814c0-144">![powerpivot in sharepoint general application set](../../../sql-server/install/media/ssas-powerpivot-logo.png "powerpivot in sharepoint general application set")</span></span>|<span data-ttu-id="814c0-145">您可以選擇使用 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 管理儀表板來驗證管理中心的大多數元件。</span><span class="sxs-lookup"><span data-stu-id="814c0-145">You can optionally verify a majority of the components in Central Administration, using the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] management dashboard.</span></span> <span data-ttu-id="814c0-146">若要在管理中心開啟儀表板，請按一下 **[一般應用程式設定]**，然後按一下 **[PowerPivot]** 中的 **[管理儀表板]**。</span><span class="sxs-lookup"><span data-stu-id="814c0-146">To open the dashboard in Central Administration, click **General Application Settings**, and then click **Management Dashboard** in the **PowerPivot**.</span></span> <span data-ttu-id="814c0-147">如需有關儀表板的詳細資訊，請參閱＜ [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)＞。</span><span class="sxs-lookup"><span data-stu-id="814c0-147">For more information on the dashboard, see [PowerPivot Management Dashboard and Usage Data](../../power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).</span></span>|

##  <a name="symptoms-and-recommended-actions"></a><a name="bkmk_symptoms"></a><span data-ttu-id="814c0-148">徵兆和建議的動作</span><span class="sxs-lookup"><span data-stu-id="814c0-148">Symptoms and Recommended Actions</span></span>
 <span data-ttu-id="814c0-149">下表是徵兆或問題清單以及這個主題的建議章節，您可參考這些章節來幫助您解決問題。</span><span class="sxs-lookup"><span data-stu-id="814c0-149">The following table is a list of symptoms or issues and the suggested section of this topic to consult to help you resolve the issue.</span></span>

|<span data-ttu-id="814c0-150">徵狀</span><span class="sxs-lookup"><span data-stu-id="814c0-150">Symptom</span></span>|<span data-ttu-id="814c0-151">請參閱章節</span><span class="sxs-lookup"><span data-stu-id="814c0-151">See section</span></span>|
|-------------|-----------------|
|<span data-ttu-id="814c0-152">資料重新整理並未執行</span><span class="sxs-lookup"><span data-stu-id="814c0-152">Data refresh is not running</span></span>|<span data-ttu-id="814c0-153">請參閱＜ [Timer Jobs](#bkmk_timer_jobs) ＞一節，並確認 **線上 PowerPivot 資料重新整理計時器工作** 在線上。</span><span class="sxs-lookup"><span data-stu-id="814c0-153">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Online PowerPivot Data Refresh Timer Job** is online.</span></span>|
|<span data-ttu-id="814c0-154">管理儀表板資料是舊的</span><span class="sxs-lookup"><span data-stu-id="814c0-154">Management dashboard data is old</span></span>|<span data-ttu-id="814c0-155">請參閱＜ [計時器工作](#bkmk_timer_jobs) ＞一節，並確認 **管理儀表板處理計時器工作** 在線上。</span><span class="sxs-lookup"><span data-stu-id="814c0-155">See the section [Timer Jobs](#bkmk_timer_jobs) and verify the **Management Dashboard Processing Timer Job** is online.</span></span>|
|<span data-ttu-id="814c0-156">管理儀表板的某些部分</span><span class="sxs-lookup"><span data-stu-id="814c0-156">Some portions of the Management Dashboard</span></span>|<span data-ttu-id="814c0-157">如果您將 PowerPivot for SharePoint 安裝到具有管理中心拓撲的伺服陣列中，但沒有 Excel Services 或 PowerPivot for SharePoint，如果您想要完整存取 PowerPivot 管理儀表板中的內建報表，您必須下載及安裝 Microsoft ADOMD.NET 用戶端程式庫。</span><span class="sxs-lookup"><span data-stu-id="814c0-157">If you install PowerPivot for SharePoint into a farm that has the topology of Central Administration, without Excel Services or PowerPivot for SharePoint, you must download and install the Microsoft ADOMD.NET client library if you want full access to the built-in reports in the PowerPivot management dashboard.</span></span> <span data-ttu-id="814c0-158">儀表板中的某些報表會使用 ADOMD.NET 來存取內部資料，這些資料會提供關於在伺服陣列中 PowerPivot 查詢處理和伺服器健全狀況的報告資料。</span><span class="sxs-lookup"><span data-stu-id="814c0-158">Some reports in the dashboard use ADOMD.NET to access internal data that provides reporting data on PowerPivot query processing and server health in the farm.</span></span> <span data-ttu-id="814c0-159">請參閱 [ADOMD.Net 用戶端程式庫](#bkmk_adomd) 一節和 [在執行管理中心的 Web 前端伺服器上安裝 ADOMD.NET](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)主題。</span><span class="sxs-lookup"><span data-stu-id="814c0-159">See the section [ADOMD.Net client Library](#bkmk_adomd) and the topic [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>|
|\<future content>||

##  <a name="analysis-services-windows-service"></a><a name="bkmk_windows_service"></a><span data-ttu-id="814c0-160">Analysis Services Windows 服務</span><span class="sxs-lookup"><span data-stu-id="814c0-160">Analysis Services Windows Service</span></span>
 <span data-ttu-id="814c0-161">本節的指令碼會在 SharePoint 模式下驗證 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="814c0-161">The script in this section verifies the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="814c0-162">確認**服務正在執行。**</span><span class="sxs-lookup"><span data-stu-id="814c0-162">Verify the service is **running**.</span></span>

```powershell
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name              DisplayName                                Status
----              -----------                                ------
MSOLAP$POWERPIVOT SQL Server Analysis Services (POWERPIVOT) Running
```

##  <a name="powerpivotsystemservice-and-powerpivotengineservice"></a><a name="bkmk_engine_and_system_service"></a><span data-ttu-id="814c0-163">PowerPivotSystemService 和 PowerPivotEngineService</span><span class="sxs-lookup"><span data-stu-id="814c0-163">PowerPivotSystemService and PowerPivotEngineService</span></span>
 <span data-ttu-id="814c0-164">本節的指令碼會驗證 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 系統服務。</span><span class="sxs-lookup"><span data-stu-id="814c0-164">The scripts in this section verify the [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] system services.</span></span> <span data-ttu-id="814c0-165">有一個適用於 SharePoint 2013 部署的系統服務以及適用於 SharePoint 2010 部署的兩個服務。</span><span class="sxs-lookup"><span data-stu-id="814c0-165">There is one system service for a SharePoint 2013 deployment and two services for a SharePoint 2010 deployment.</span></span>

 <span data-ttu-id="814c0-166">**PowerPivotSystemService**</span><span class="sxs-lookup"><span data-stu-id="814c0-166">**PowerPivotSystemService**</span></span>

 <span data-ttu-id="814c0-167">確認狀態為**線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-167">Verify the Status is **Online**.</span></span>

```powershell
Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                  Status Applications                             Farm
--------                                  ------ ------------                             ----
SQL Server PowerPivot Service Application Online {Default PowerPivot Service Application} SPFarm Name=SharePoint_Config_77d8ab0744a34e8aa27c806a2b8c760c
```

 <span data-ttu-id="814c0-168">**PowerPivotEngineService**</span><span class="sxs-lookup"><span data-stu-id="814c0-168">**PowerPivotEngineService**</span></span>

> [!NOTE]
>  <span data-ttu-id="814c0-169">如果您正在使用 SharePoint 2013，請**略過這個指令碼** 。</span><span class="sxs-lookup"><span data-stu-id="814c0-169">**Skip this script if** you are using SharePoint 2013.</span></span> <span data-ttu-id="814c0-170">PowerPivotEngineService 不是 SharePoint 2013 部署的一部分。</span><span class="sxs-lookup"><span data-stu-id="814c0-170">The PowerPivotEngineService is not part of a SharePoint 2013 deployment.</span></span> <span data-ttu-id="814c0-171">如果您在 SharePoint 2013 上執行 Get-PowerPivot**Engine**Service 指令程式，您將會看到類似下面的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="814c0-171">If you run the Get-PowerPivot**Engine**Service cmdlet on SharePoint 2013, you will see an error message similar to the following.</span></span> <span data-ttu-id="814c0-172">即使您已經執行本主題的＜必要條件＞一節所描述的 Add-PSSnapin 命令，還是會傳回這個錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="814c0-172">This error message is returned even if you have run the Add-PSSnapin command described in the prerequisites section of this topic.</span></span>
> 
>  <span data-ttu-id="814c0-173">'Get-PowerPivotEngineService' 詞彙無法辨識為指令程式名稱</span><span class="sxs-lookup"><span data-stu-id="814c0-173">The term 'Get-PowerPivotEngineService' is not recognized as the name of a cmdlet</span></span>

 <span data-ttu-id="814c0-174">在 SharePoint 2010 部署中，確認狀態為 **線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-174">In a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName  : SQL Server Analysis Services
Status    : Online
Name      : MSOLAP$POWERPIVOT
Instances : {POWERPIVOT}
Farm      : SPFarm Name=SharePoint_Config
```

##  <a name="powerpivot-service-applications-and-proxies"></a><a name="bkmk_powerpivot_service_application"></a><span data-ttu-id="814c0-175">PowerPivot 服務應用程式 (s) 和 proxy</span><span class="sxs-lookup"><span data-stu-id="814c0-175">PowerPivot Service Application(s) and proxies</span></span>
 <span data-ttu-id="814c0-176">確認狀態為 **線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-176">Verify the status is **Online**.</span></span> <span data-ttu-id="814c0-177">Excel Services 應用程式不會使用服務應用程式資料庫，因此指令程式不會傳回資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="814c0-177">The Excel Services Application does not use a service application database and therefore the cmdlet does not return a database name.</span></span> <span data-ttu-id="814c0-178">請記下 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 服務應用程式所使用的資料庫，好讓您能夠在本主題稍後的＜資料庫＞一節中確認資料庫為線上狀態。</span><span class="sxs-lookup"><span data-stu-id="814c0-178">Note the database used by the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] service application so you can verify the database is online in the database section later in this topic.</span></span>

 <span data-ttu-id="814c0-179">**PowerPivot 和 Excel 服務應用程式**</span><span class="sxs-lookup"><span data-stu-id="814c0-179">**PowerPivot and Excel Service Application(s)**</span></span>

 <span data-ttu-id="814c0-180">針對 SharePoint 2010 部署，確認狀態為 **線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-180">For a SharePoint 2010 deployment, verify the status is **Online**.</span></span>

```powershell
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename, DisplayName, status
```

```Output
TypeName          : PowerPivot Service Application
Name              : PowerPivotServiceApplication1
Status            : Online
UnattendedAccount : PowerPivotUnattendedAccount
ApplicationPool   : SPIisWebServiceApplicationPool Name=sqlbi_serviceapp
Farm              : SPFarm Name=SharePoint_Config
Database          : GeminiServiceDatabase Name=PowerPivotServiceApplication1_19648f3f2c944e27acdc6c20aab8487a

TypeName    : Excel Services Application Web Service Application
DisplayName : Excel Services Application
Status      : Online
```

 <span data-ttu-id="814c0-181">**服務應用程式集區**</span><span class="sxs-lookup"><span data-stu-id="814c0-181">**Service Application Pool**</span></span>

> [!NOTE]
>  <span data-ttu-id="814c0-182">下列程式碼範例會先傳回預設 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 服務應用程式的 applicationpool 屬性。</span><span class="sxs-lookup"><span data-stu-id="814c0-182">The following code sample first returns the applicationpool property of the default [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] service application.</span></span> <span data-ttu-id="814c0-183">從名稱會從字串剖析並用來取得應用程式集區物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="814c0-183">The name is parsed from the string and used to get the status of the application pool object.</span></span>
> 
>  <span data-ttu-id="814c0-184">確認狀態為**線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-184">Verify the Status is **Online**.</span></span> <span data-ttu-id="814c0-185">如果狀態不是線上，或當您流覽網站時看到「HTTP 錯誤」 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ，請確認 IIS 應用程式集區中的身分識別認證仍然正確。</span><span class="sxs-lookup"><span data-stu-id="814c0-185">If the status is not Online or you see "http error" when you browse the [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] site, verify the identity credentials in the IIS application pools are still correct.</span></span> <span data-ttu-id="814c0-186">IIS 集區名稱將會是 Get-SPServiceApplicationPool 命令所傳回之 ID 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="814c0-186">The IIS pool name will is the value of the ID property returned by the Get-SPServiceApplicationPool command.</span></span>

```powershell
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)

Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                           Status ProcessAccountName Id
----                           ------ ------------------ ------- 
SharePoint Web Services System Online DOMAIN\account     89b50ec3-49e3-4de7-881a-2cec4b8b73ea
```

 ![注意](../../../reporting-services/media/rs-fyinote.png "注意")應用程式集區也可以在管理中心的 [**管理服務應用程式**] 頁面上進行驗證。 <span data-ttu-id="814c0-188">按一下服務應用程式的名稱，然後按一下功能區中的 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="814c0-188">Click the name of the service application and then click **properties** in the ribbon.</span></span>

 <span data-ttu-id="814c0-189">**PowerPivot 和 Excel 服務應用程式 Proxy**</span><span class="sxs-lookup"><span data-stu-id="814c0-189">**PowerPivot and Excel Service Application proxies**</span></span>

 <span data-ttu-id="814c0-190">確認狀態為**線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-190">Verify the Status is **Online**.</span></span>

```powershell
Get-SPServiceApplicationProxy | Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -Like "*powerpivot*" -Or $_.TypeName -Like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
TypeName                                                 Status UnattendedAccount           DisplayName
--------                                                 ------ -----------------           -----------
PowerPivot Service Application Proxy                     Online PowerPivotUnattendedAccount PowerPivotServiceApplication1
Excel Services Application Web Service Application Proxy Online                             Excel Services Application
```

##  <a name="databases"></a><a name="bkmk_databases"></a><span data-ttu-id="814c0-191">資料庫</span><span class="sxs-lookup"><span data-stu-id="814c0-191">Databases</span></span>
 <span data-ttu-id="814c0-192">下列指令碼會傳回服務應用程式資料庫及所有內容資料庫的狀態。</span><span class="sxs-lookup"><span data-stu-id="814c0-192">The following script returns the status of the service application databases and all content databases.</span></span> <span data-ttu-id="814c0-193">確認狀態為 **線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-193">Verify the status is **Online**.</span></span>

```powershell
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -Or $_.TypeName -Like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                                                                       Status Server                  TypeName 
----                                                                       ------ ------                  -------- 
DefaultPowerPivotServiceApplicationDB-38422181-2b68-4ab2-b2bb-9c00c39e5a5e Online SPServer Name=TESTSERVER Microsoft.AnalysisServices.SPAddin.GeminiServiceDatabase
DefaultWebApplicationDB-f0db1a8e-4c22-408c-b9b9-153bd74b0312               Online TESTSERVER\POWERPIVOT    Content Database 
SharePoint_Admin_3cadf0b098bf49e0bb15abd487f5c684                          Online TESTSERVER\POWERPIVOT    Content Database
```

##  <a name="sharepoint-features"></a><a name="bkmk_features"></a><span data-ttu-id="814c0-194">SharePoint 功能</span><span class="sxs-lookup"><span data-stu-id="814c0-194">SharePoint Features</span></span>
 <span data-ttu-id="814c0-195">確認網站、Web 和伺服器陣列功能都在線上。</span><span class="sxs-lookup"><span data-stu-id="814c0-195">Verify the site, web, and farm features are online.</span></span>

```powershell
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
DisplayName     Status Scope Farm                         
-----------     ------ ----- ----                         
PowerPivotSite  Online  Site SPFarm Name=SharePoint_Config
PowerPivotAdmin Online   Web SPFarm Name=SharePoint_Config
PowerPivot      Online  Farm SPFarm Name=SharePoint_Config
```

##  <a name="timer-jobs"></a><a name="bkmk_timer_jobs"></a><span data-ttu-id="814c0-196">計時器工作</span><span class="sxs-lookup"><span data-stu-id="814c0-196">Timer Jobs</span></span>
 <span data-ttu-id="814c0-197">確認計時器工作在 **線上**。</span><span class="sxs-lookup"><span data-stu-id="814c0-197">Verify the Time Jobs are **Online**.</span></span> <span data-ttu-id="814c0-198">SharePoint 2013 上並未安裝 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService，因此指令碼將不會在 SharePoint 2013 部署中列出 EngineService 計時器工作。</span><span class="sxs-lookup"><span data-stu-id="814c0-198">The [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] EngineService is not installed on SharePoint 2013, therefore the script will not list EngineService timer jobs in a SharePoint 2013 deployment.</span></span>

```powershell
Get-SPTimerJob | Where {$_.service -Like "*power*" -Or $_.service -Like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default
```

```Output
      Status DisplayName                                                                          LastRunTime          Service                             
------ -----------                                                                          -----------          -------                             
Online Health Analysis Job (Daily, SQL Server Analysis Services, All Servers)               4/9/2014 12:00:01 AM EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Hourly, SQL Server Analysis Services, All Servers)              4/9/2014 1:00:01 PM  EngineService Name=MSOLAP$POWERPIVOT
Online Health Analysis Job (Weekly, SQL Server Analysis Services, All Servers)              4/6/2014 12:00:10 AM EngineService Name=MSOLAP$POWERPIVOT
Online PowerPivot Management Dashboard Processing Timer Job                                 4/8/2014 3:45:38 AM  MidTierService
Online PowerPivot Health Statistics Collector Timer Job                                     4/9/2014 1:00:12 PM  MidTierService
Online PowerPivot Data Refresh Timer Job                                                    4/9/2014 1:09:36 PM  MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, All Servers)  4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Daily, SQL Server PowerPivot Service Application, Any Server)   4/9/2014 12:00:00 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, All Servers) 4/6/2014 12:00:03 AM MidTierService
Online Health Analysis Job (Weekly, SQL Server PowerPivot Service Application, Any Server)  4/6/2014 12:00:03 AM MidTierService
Online PowerPivot Setup Extension Timer Job                                                 4/1/2014 1:40:31 AM  MidTierService
```

##  <a name="health-rules"></a><a name="bkmk_health_rules"></a><span data-ttu-id="814c0-199">健全狀況規則</span><span class="sxs-lookup"><span data-stu-id="814c0-199">Health Rules</span></span>
 <span data-ttu-id="814c0-200">SharePoint 2013 部署中的規則較少。</span><span class="sxs-lookup"><span data-stu-id="814c0-200">There are fewer rules in a SharePoint 2013 deployment.</span></span> <span data-ttu-id="814c0-201">如需每個 SharePoint 環境的完整規則清單以及如何使用規則的說明，請參閱[PowerPivot 健全狀況規則-設定](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="814c0-201">For a full list of rules for each SharePoint environment and an explanation of how to use the rules, see [PowerPivot Health Rules - Configure](../../power-pivot-sharepoint/configure-power-pivot-health-rules.md).</span></span>

```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                          Enabled Summary
----                          ------- -------         
SecondaryLogonHealthRule         True PowerPivot:  Secondary Logon service (seclogon) is disabled
DataRefreshTimerJobHealthRule    True PowerPivot: The PowerPivot Data Refresh timer job is disabled.
ASUsageLoadHealthRule            True PowerPivot: The ratio of load events to connections is too high.
ASMiniDumpHealthRule             True PowerPivot: One or more minidump files were found in the Logs directory, indicating a program crash
ASUsageCubeRule                  True PowerPivot: Usage data is not getting updated at the expected frequency.
ASADOMDNETHealthRule             True PowerPivot: ADOMD.NET is not installed on a standalone WFE that is configured for central admin
MidTierAcctReadPermissionRule    True PowerPivot: MidTier process account should have 'Full Read' permission on all associated SPWebApplications.
```

##  <a name="windows-and-uls-logs"></a><a name="bkmk_logs"></a><span data-ttu-id="814c0-202">Windows 和 ULS 記錄檔</span><span class="sxs-lookup"><span data-stu-id="814c0-202">Windows and ULS Logs</span></span>
 <span data-ttu-id="814c0-203">**Windows 事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="814c0-203">**Windows event log**</span></span>

 <span data-ttu-id="814c0-204">下列命令將會搜尋 Windows 事件記錄檔，以便找出 SharePoint 模式下與 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體有關的事件。</span><span class="sxs-lookup"><span data-stu-id="814c0-204">The following command will search the windows event log for events related to the instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="814c0-205">如需停用事件或變更事件層級的詳細資訊，請參閱[設定及查看 SharePoint 記錄檔和診斷記錄 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="814c0-205">For information on disabling events or changing the event level, see [Configure and View SharePoint Log Files  and Diagnostic Logging &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md).</span></span>

 <span data-ttu-id="814c0-206">**服務名稱** ：MSOLAP$POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="814c0-206">**Service Name:** MSOLAP$POWERPIVOT</span></span>

 <span data-ttu-id="814c0-207">**Windows 服務中的顯示名稱** ：SQL Server Analysis Services (POWERPIVOT)</span><span class="sxs-lookup"><span data-stu-id="814c0-207">**Display name in Windows Services:** SQL Server Analysis Services (POWERPIVOT)</span></span>

```powershell
Get-EventLog "application" | Where-Object {$_.source -Like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -property * -AutoSize | Out-Default
```

```Output
TimeGenerated           EntryType Source            Message
-------------           --------- ------            -------
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
4/16/2014 1:45:19 PM  Information MSOLAP$POWERPIVOT Service started. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM 12.0.1997.5.
4/16/2014 1:45:18 PM  Information MSOLAP$POWERPIVOT The flight recorder was started.
4/14/2014 6:45:37 PM  Information MSOLAP$POWERPIVOT Software usage metrics are disabled.
```

 <span data-ttu-id="814c0-208">**SharePoint ULS 記錄 (過去 48 個小時)**</span><span class="sxs-lookup"><span data-stu-id="814c0-208">**SharePoint ULS Log, last 48 hours**</span></span>

 <span data-ttu-id="814c0-209">下列命令將會從過去 48 小時內建立的 ULS 記錄傳回 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 訊息。</span><span class="sxs-lookup"><span data-stu-id="814c0-209">The following command will return [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] messages from the ULS log that were created in the last 48 hours.</span></span> <span data-ttu-id="814c0-210">針對您的需要調整 addhours 參數。</span><span class="sxs-lookup"><span data-stu-id="814c0-210">Adjust the addhours parameter for your need.</span></span>

```powershell
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid,level, message | Format-Table -Property * -AutoSize | Out-Default
```

 <span data-ttu-id="814c0-211">以下的命令變化只會傳回 **資料重新整理** 類別目錄的記錄事件。</span><span class="sxs-lookup"><span data-stu-id="814c0-211">The following variation of the command only returns log events for the **data refresh** category.</span></span>

```powershell
Get-SPLogEvent -starttime(Get-Date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message
```

```Output
Timestamp   : 4/14/2014 7:15:01 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 43
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : The following error occurred when working with the service application, Default PowerPivot Service Application. Skipping the service application..

Timestamp   : 4/14/2014 7:15:02 PM
Area        : PowerPivot Service
Category    : Data Refresh
EventID     : 99
Level       : High
Correlation : 5755879c-7cab-e097-8f80-f27895d44a77
Message     : EXCEPTION: System.TimeoutException: The request channel timed out while waiting for a reply after 00:00:47.0625313. Increase the timeout value passed to 
              the call to Request or increase the SendTimeout value on the Binding. The time allotted to this operation may have been a portion of a longer timeout. 
              ---> System.TimeoutException: The HTTP request to 'http://localhost:32843/SecurityTokenServiceApplication/securitytoken.svc/actas' has exceeded the 
              allotted timeout of 00:00:54.5930000. The time allotted to this operation may have been a portion of a longer timeout. ---> System.Net.WebException: The 
              operation has timed out     at System.Net.HttpWebRequest.GetResponse()     at 
              System.ServiceModel.Channels.HttpChannelFactory`1.HttpRequestChannel.HttpChannelRequest.WaitForReply(TimeSpan timeout...
```

##  <a name="msolap-provider"></a><a name="bkmk_msolap"></a><span data-ttu-id="814c0-212">MSOLAP 提供者</span><span class="sxs-lookup"><span data-stu-id="814c0-212">MSOLAP Provider</span></span>
 <span data-ttu-id="814c0-213">驗證 MSOLAP 提供者。</span><span class="sxs-lookup"><span data-stu-id="814c0-213">Verify the provider MSOLAP provider.</span></span> [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]<span data-ttu-id="814c0-214">和 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 需要 MSOLAP. 5。</span><span class="sxs-lookup"><span data-stu-id="814c0-214">and [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] require MSOLAP.5.</span></span>

```powershell
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default
```

```Output
ProviderId ProviderType Description
---------- ------------ -----------
MSOLAP     Oledb        Microsoft OLE DB Provider for OLAP Services     
MSOLAP.3   Oledb        Microsoft OLE DB Provider for OLAP Services 9.0 
MSOLAP.4   Oledb        Microsoft OLE DB Provider for OLAP Services 10.0
MSOLAP.5   Oledb        Microsoft OLE DB Provider for OLAP Services 11.0
```

 <span data-ttu-id="814c0-215">如需詳細資訊，請參閱 [在 SharePoint 伺服器上安裝 Analysis Services OLE DB 提供者](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) 和 [加入 MSOLAP.5 做為 Excel Services 中受信任的資料提供者](https://technet.microsoft.com/library/hh758436.aspx)。</span><span class="sxs-lookup"><span data-stu-id="814c0-215">For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](../../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md) and [Add MSOLAP.5 as a Trusted Data Provider in Excel Services](https://technet.microsoft.com/library/hh758436.aspx).</span></span>

##  <a name="adomdnet-client-library"></a><a name="bkmk_adomd"></a><span data-ttu-id="814c0-216">ADOMD.Net 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="814c0-216">ADOMD.Net client Library</span></span>

```powershell
Get-WMIObject -Class win32_product | Where-Object {$_.name -Like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | out-default
```

```Output
name                                                  version      vendor
----                                                  -------      ------
Microsoft SQL Server 2008 Analysis Services ADOMD.NET 10.1.2531.0  Microsoft Corporation
Microsoft SQL Server 2005 Analysis Services ADOMD.NET 9.00.1399.06 Microsoft Corporation
```

 <span data-ttu-id="814c0-217">如需詳細資訊，請參閱 [在執行管理中心的 Web 前端伺服器上安裝 ADOMD.NET](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="814c0-217">For more information, see [Install ADOMD.NET on Web Front-End Servers Running Central Administration](../../../sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).</span></span>

##  <a name="health-data-collection-rules"></a><a name="bkmk_health_collection"></a><span data-ttu-id="814c0-218">健全狀況資料收集規則</span><span class="sxs-lookup"><span data-stu-id="814c0-218">Health Data Collection Rules</span></span>
 <span data-ttu-id="814c0-219">確認 **[狀態]** 為線上，而且 **[已啟用]** 成立。</span><span class="sxs-lookup"><span data-stu-id="814c0-219">Verify the **Status** is Online and **Enabled** is True.</span></span>

```powershell
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -Like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

```Output
Name                         Status Enabled TableName                   DaysToKeepDetailedData
----                         ------ ------- ---------                   ----------------------
PowerPivot Connections       OnlineTrue AnalysisServicesConnections  14
PowerPivot Load Data Usage   Online    True AnalysisServicesLoads                           14
PowerPivot Query Usage       Online    True AnalysisServicesRequests                        14
PowerPivot Unload Data Usage Online    True AnalysisServicesUnloads                         14
```

 <span data-ttu-id="814c0-220">如需詳細資訊，請參閱 [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="814c0-220">For more information, see [PowerPivot Usage Data Collection](../../power-pivot-sharepoint/power-pivot-usage-data-collection.md).</span></span>

##  <a name="solutions"></a><a name="bkmk_solutions"></a><span data-ttu-id="814c0-221">適用</span><span class="sxs-lookup"><span data-stu-id="814c0-221">Solutions</span></span>
 <span data-ttu-id="814c0-222">如果其他元件在線上，您可以略過方案的驗證。</span><span class="sxs-lookup"><span data-stu-id="814c0-222">If the other components are online then you can skip verifying the solutions.</span></span> <span data-ttu-id="814c0-223">不過，如果遺漏了健全狀況規則，請確認這兩個方案都存在，並確認兩個 PowerPivot 方案為 **線上** 和 **已部署**狀態。</span><span class="sxs-lookup"><span data-stu-id="814c0-223">If however the Health rules are missing, verify the two solutions exist and showed Verify the two PowerPivot solutions are **Online** and **Deployed**.</span></span>

```powershell
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -Like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
```

<span data-ttu-id="814c0-224">SharePoint 2013：</span><span class="sxs-lookup"><span data-stu-id="814c0-224">SharePoint 2013:</span></span>

```Output
Name                                 Status Deployed        DeploymentState DeployedServers
----                                 ------ --------        --------------- ---------------
powerpivotfarm14solution.wsp         Online     True         GlobalDeployed {UETESTA00}
powerpivotfarmsolution.wsp           Online     True         GlobalDeployed {UETESTA00}
powerpivotwebapplicationsolution.wsp Online     True WebApplicationDeployed {UETESTA00}
```

<span data-ttu-id="814c0-225">SharePoint 2010：</span><span class="sxs-lookup"><span data-stu-id="814c0-225">SharePoint 2010:</span></span>

```Output
Name                 Status Deployed        DeploymentState DeployedServers 
----                 ------ --------        --------------- --------------- 
powerpivotfarm.wsp   Online     True         GlobalDeployed {uesql11spoint2}
powerpivotwebapp.wsp Online     True WebApplicationDeployed {uesql11spoint2}
```

 <span data-ttu-id="814c0-226">如需如何部署 SharePoint 方案的詳細資訊，請參閱 [部署方案套件 (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="814c0-226">For more information on how to deploy SharePoint solutions, see [Deploy solution packages (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262995\(v=office.14\).aspx).</span></span>

##  <a name="manual-verification-steps"></a><a name="bkmk_manual"></a><span data-ttu-id="814c0-227">手動驗證步驟</span><span class="sxs-lookup"><span data-stu-id="814c0-227">Manual Verification Steps</span></span>
 <span data-ttu-id="814c0-228">本節描述無法使用 PowerShell 指令程式完成的步驟。</span><span class="sxs-lookup"><span data-stu-id="814c0-228">This section describes verification steps that cannot be completed with PowerShell cmdlets.</span></span>

 <span data-ttu-id="814c0-229">**排定的資料重新整理** ：將重新整理活頁簿排程設定為 **[並且盡快重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="814c0-229">**Scheduled Data Refresh:** Configure the refresh schedule a workbook to **Also refresh as soon as possible**.</span></span>  <span data-ttu-id="814c0-230">如需詳細資訊，請參閱[排程資料重新整理和不支援 Windows 驗證的資料來源 &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md)中的「確認資料重新整理」一節。</span><span class="sxs-lookup"><span data-stu-id="814c0-230">For more information, see the "Verify Data Refresh" section of [Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/schedule-data-refresh-and-data-sources-no-windows-authentication.md).</span></span>

##  <a name="more-resources"></a><a name="bkmk_more_resources"></a><span data-ttu-id="814c0-231">其他資源</span><span class="sxs-lookup"><span data-stu-id="814c0-231">More Resources</span></span>
 <span data-ttu-id="814c0-232">[Windows PowerShell 中的 Web 伺服器 (IIS) 管理指令程式](https://technet.microsoft.com/library/ee790599.aspx)。</span><span class="sxs-lookup"><span data-stu-id="814c0-232">[Web Server (IIS) Administration Cmdlets in Windows PowerShell](https://technet.microsoft.com/library/ee790599.aspx).</span></span>

 <span data-ttu-id="814c0-233">[要在 SharePoint 中檢查服務、IIS 網站和應用程式集區狀態的 PowerShell](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0)。</span><span class="sxs-lookup"><span data-stu-id="814c0-233">[PowerShell to check services, IIS sites and Application Pool status in SharePoint](https://gallery.technet.microsoft.com/office/PowerShell-to-check-a6ed72a0).</span></span>

 <span data-ttu-id="814c0-234">[SharePoint Server 2013 的 Windows PowerShell 參考](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span><span class="sxs-lookup"><span data-stu-id="814c0-234">[Windows PowerShell for SharePoint 2013 reference](https://technet.microsoft.com/library/ee890108\(v=office.15\).aspx)</span></span>

 <span data-ttu-id="814c0-235">[SharePoint Foundation 2010 的 Windows PowerShell 參考](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="814c0-235">[Windows PowerShell for SharePoint Foundation 2010 reference](https://technet.microsoft.com/library/ee890105\(v=office.14\).aspx)</span></span>

 <span data-ttu-id="814c0-236">[使用 Windows PowerShell 管理 Excel Services (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="814c0-236">[Manage Excel Services with Windows PowerShell (SharePoint Server 2010)](https://technet.microsoft.com/library/ff191201\(v=office.14\).aspx)</span></span>

 [<span data-ttu-id="814c0-237">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="814c0-237">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)

 [<span data-ttu-id="814c0-238">使用 Get-EvenLog 指令程式</span><span class="sxs-lookup"><span data-stu-id="814c0-238">Use the Get-EvenLog cmdlet</span></span>](https://technet.microsoft.com/library/ee176846.aspx)

##  <a name="full-powershell-script"></a><a name="bkmk_full_script"></a><span data-ttu-id="814c0-239">完整的 PowerShell 腳本</span><span class="sxs-lookup"><span data-stu-id="814c0-239">Full PowerShell Script</span></span>
 <span data-ttu-id="814c0-240">下列指令碼包含之前章節中的所有命令。</span><span class="sxs-lookup"><span data-stu-id="814c0-240">The Following script contains all of the commands from the previous sections.</span></span> <span data-ttu-id="814c0-241">此指令碼會依照命令出現在本主題的相同順序來執行命令。</span><span class="sxs-lookup"><span data-stu-id="814c0-241">The script runs the commands in the same order as they are presented in this topic.</span></span> <span data-ttu-id="814c0-242">此指令碼包含本主題所註明的一些選擇性命令變化，以免您需要額外的篩選。</span><span class="sxs-lookup"><span data-stu-id="814c0-242">The script contains some optional variations of the commands noted in this topic in case you need additional filtering.</span></span> <span data-ttu-id="814c0-243">這些變化會以註解字元 (#) 停用。</span><span class="sxs-lookup"><span data-stu-id="814c0-243">The variations are disabled with a comment character (#).</span></span> <span data-ttu-id="814c0-244">此指令碼也包含用來驗證 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式的一些陳述式。</span><span class="sxs-lookup"><span data-stu-id="814c0-244">The script also includes some statements for verifying [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="814c0-245">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 陳述式會以註解字元 (#) 停用。</span><span class="sxs-lookup"><span data-stu-id="814c0-245">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] statements are disabled with a comment character (#).</span></span>

```powershell
# This script audits services related to PowerPivot for SharePoint
$starttime = Get-Date
write-host -foregroundcolor DarkGray StartTime $starttime

Write-Host  "Import the SharePoint PowerShell snappin"
Add-PSSnapin Microsoft.Sharepoint.Powershell -EA 0

Write-Host -ForegroundColor Green "Analysis Services Windows Service"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-Service | Select name, displayname, status | Where {$_.Name -eq "msolap`$powerpivot"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "PowerPivotEngineService and PowerPivotSystemService"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"

Get-PowerPivotSystemService | Select typename, status, applications, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotSystemService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

Get-PowerPivotEngineService | Select typename, status, name, instances, farm | Format-Table -property * -AutoSize | Out-Default
# If needed, you can run the following to compare job definitions specific to the service against the results of the timer job definition section
#Get-PowerPivotEngineService | select -ExpandProperty jobdefinitions | select displayname, schedule, service | format-table -property * -autosize | out-default

#Write-Host -ForegroundColor Green "Service Instances - optional if you want to associate services with the server"
#Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
#Get-SPServiceInstance | select typename, status, server, service, instance | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel*" -or $_.TypeName -like "*Analysis Services*"} | format-table -property * -autosize | out-default
#Get-PowerPivotEngineServiceInstance  | select typename, ASServername, status, server, service, instance
#Get-PowerPivotSystemServiceInstance  | select typename, ASSServerName, status, server, service, instance

Write-Host -ForegroundColor Green "PowerPivot And Excel Service Applications"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-PowerPivotServiceApplication | Select typename,name, status, unattendedaccount, applicationpool, farm, database
Get-SPExcelServiceApplication | Select typename,  DisplayName, status

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot Service Application pool"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
# the following assumes there is only 1 PowerPivot Service Application, and returns that application's pool name.  if you have more than one, use the 2nd version
$poolname = [string](Get-PowerPivotServiceApplication | Select -Property applicationpool)
$position = $poolname.lastindexof("=")
$poolname = $poolname.substring($position+1)
$poolname = $poolname.substring(0,$poolname.length-1)
Get-SPServiceApplicationPool | Select name, status, processaccountname, id | Where {$_.Name -eq $poolname} | Format-Table -Property * -AutoSize | Out-Default

#Write-Host ""
Write-Host -ForegroundColor Green "PowerPivot and Excel Service Application Proxy"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPServiceApplicationProxy |  Select typename, status, unattendedaccount, displayname | Where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*excel services*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPServiceApplicationProxy |  select typename, status, unattendedaccount, displayname | where {$_.TypeName -like "*powerpivot*" -or $_.TypeName -like "*Reporting Services*" -or $_.TypeName -like "*excel services*"} | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "DATABASES"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPDatabase | Select name, status, server, typename | Where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPDatabase | select name, status, server, typename | where {$_.TypeName -eq "content database" -or $_.TypeName -like "*Gemini*" -or $_.TypeName -like "*ReportingServices*"}

Write-Host -ForegroundColor Green "features"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPFeature | Select displayname, status, scope, farm | Where {$_.displayName -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default
#Get-SPFeature | select displayname, status, scope, farm | where {$_.displayName -like "*powerpivot*" -or $_.displayName -like "*ReportServer*"}  | format-table -property * -autosize | out-default

Write-Host -ForegroundColor Green "Timer Jobs (Job Definitions) -- list is the same as seen in the 'Review timer job definitions' section of the management dashboard"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPTimerJob | Where {$_.service -like "*power*" -or $_.service -like "*mid*"} | Select status, displayname, LastRunTime, service | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "health rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -Like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "Windows Event Log data MSSQL$POWERPIVOT and "
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*"}  | Select timegenerated, entrytype , source, message | Format-Table -Property * -autosize | Out-Default
#The following is the same command but with the Inforamtion events filtered out.
#Get-EventLog "application" | Where-Object {$_.source -like "msolap`$powerpivot*" -and ($_.entrytype -match "error" -or $_.entrytype -match "critical" -or $_.entrytype -match "warning")}  |select timegenerated, entrytype , source, message | format-table -property * -autosize | out-default

#Write-Host ""
Write-Host -ForegroundColor Green "ULS Log data"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPLogEvent -StartTime(Get-Date).AddHours(-48) | Where-Object {$_.Area -eq "powerpivot service" -and $_.level -eq "high"} | Select timestamp, area, category, eventid, level, correlation, message | Format-Table -Property * -AutoSize | Out-Default
#the following example filters for the category 'data refresh'
#Get-SPLogEvent -starttime(get-date).addhours(-48) | Where-Object {$_.category -eq "data refresh" -and $_.level -eq "high"} | select timestamp, area, category, eventid, level, correlation, message

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time

Write-Host -ForegroundColor Green "MSOLAP data provider for Excel Servivces, service application"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
$excelApp = Get-SPExcelServiceApplication
Get-SPExcelDataProvider -ExcelServiceApplication $excelApp | Select providerid, providertype, description | Where {$_.providerid -like "msolap*" } | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "ADOMD.net client library"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-WMIObject -Class win32_product | Where-Object {$_.name -like "*ado*"} | Select name, version, vendor | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Usage Data Rules"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPUsageDefinition | Select name, status, enabled, tablename, DaysToKeepDetailedData | Where {$_.name -like "powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

Write-Host -ForegroundColor Green "Solutions"
Write-Host -ForegroundColor Green ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
Get-SPSolution | Select name, status, deployed, DeploymentState, DeployedServers | Where {$_.Name -like "*powerpivot*"} | Format-Table -Property * -AutoSize | Out-Default

$time = Get-Date
Write-Host -ForegroundColor DarkGray StartTime $starttime
Write-Host -ForegroundColor DarkGray EndTime $time
```
