---
title: PowerPivot 管理儀表板和使用量資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 541c8b1f-c6c2-423d-a97d-65c379967e0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581ed571661d54b1cfe9a63224b05f4f8b0267e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596326"
---
# <a name="powerpivot-management-dashboard-and-usage-data"></a><span data-ttu-id="1d251-102">PowerPivot 管理儀表板和使用量資料</span><span class="sxs-lookup"><span data-stu-id="1d251-102">PowerPivot Management Dashboard and Usage Data</span></span>
  <span data-ttu-id="1d251-103">PowerPivot 管理儀表板是 SharePoint 管理中心內預先定義之報表和網頁組件的集合，可讓您管理 SQL Server PowerPivot for SharePoint 部署。</span><span class="sxs-lookup"><span data-stu-id="1d251-103">PowerPivot Management Dashboard is a collection of predefined reports and web parts in SharePoint Central Administration that help you administer a SQL Server PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="1d251-104">管理儀表板會提供伺服器健全狀況、活頁簿活動和資料重新整理的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1d251-104">The Management Dashboard provides information related to server health, workbook activity, and data refresh.</span></span> <span data-ttu-id="1d251-105">儀表板會使用 SharePoint 使用量資料收集的資料。</span><span class="sxs-lookup"><span data-stu-id="1d251-105">The dashboard uses data from the SharePoint usage data collection.</span></span>  
  
 [<span data-ttu-id="1d251-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="1d251-106">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="1d251-107">儀表板區段的總覽</span><span class="sxs-lookup"><span data-stu-id="1d251-107">Overview of the sections of the Dashboard</span></span>](#items)  
  
 [<span data-ttu-id="1d251-108">開啟 PowerPivot 管理儀表板</span><span class="sxs-lookup"><span data-stu-id="1d251-108">Open PowerPivot Management Dashboard</span></span>](#open)  
  
 [<span data-ttu-id="1d251-109">儀表板中的來源資料</span><span class="sxs-lookup"><span data-stu-id="1d251-109">Source Data in Dashboards</span></span>](#sourcedata)  
  
 [<span data-ttu-id="1d251-110">編輯 PowerPivot 儀表板</span><span class="sxs-lookup"><span data-stu-id="1d251-110">Edit PowerPivot Dashboard</span></span>](#edit)  
  
 [<span data-ttu-id="1d251-111">建立 PowerPivot 管理儀表板中的自訂報表</span><span class="sxs-lookup"><span data-stu-id="1d251-111">Create Custom Reports for PowerPivot Management Dashboard</span></span>](#reports)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="1d251-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="1d251-112">Prerequisites</span></span>  
 <span data-ttu-id="1d251-113">您必須是服務管理員，才能開啟所管理 PowerPivot 服務應用程式的 PowerPivot 管理儀表板。</span><span class="sxs-lookup"><span data-stu-id="1d251-113">You must be a service administrator to open PowerPivot Management Dashboard for a PowerPivot service application that you manage.</span></span>  
  
##  <a name="overview-of-the-sections-of-the-dashboard"></a><a name="items"></a> <span data-ttu-id="1d251-114">儀表板中各區段的概觀</span><span class="sxs-lookup"><span data-stu-id="1d251-114">Overview of the sections of the Dashboard</span></span>  
 <span data-ttu-id="1d251-115">PowerPivot 管理儀表板包含 Web 組件和向下鑽研至特定資訊類別的內嵌報表。</span><span class="sxs-lookup"><span data-stu-id="1d251-115">PowerPivot Management Dashboard contains Web Parts and embedded reports that drill down into specific information categories.</span></span> <span data-ttu-id="1d251-116">下列清單描述的是儀表板的每個部分：</span><span class="sxs-lookup"><span data-stu-id="1d251-116">The following list describes each part of the dashboard:</span></span>  
  
|<span data-ttu-id="1d251-117">儀表板</span><span class="sxs-lookup"><span data-stu-id="1d251-117">Dashboard</span></span>|<span data-ttu-id="1d251-118">描述</span><span class="sxs-lookup"><span data-stu-id="1d251-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d251-119">基礎結構 - 伺服器健全狀況</span><span class="sxs-lookup"><span data-stu-id="1d251-119">Infrastructure - Server Health</span></span>|<span data-ttu-id="1d251-120">顯示隨時間經過的 CPU 使用量、記憶體消耗量和查詢回應時間趨勢，以便評估系統資源是已接近最大容量，或利用率極低。</span><span class="sxs-lookup"><span data-stu-id="1d251-120">Shows trends in CPU usage, memory consumption, and query response times over time so that you can assess whether system resources are nearing maximum capacity or are under utilized.</span></span>|  
|<span data-ttu-id="1d251-121">[動作]</span><span class="sxs-lookup"><span data-stu-id="1d251-121">Actions</span></span>|<span data-ttu-id="1d251-122">包含管理中心內其他頁面的連結，包括目前的服務應用程式、服務應用程式的清單以及使用量記錄。</span><span class="sxs-lookup"><span data-stu-id="1d251-122">Contains links to other pages in Central Administration including the current service application, a list of service applications, and usage logging.</span></span>|  
|<span data-ttu-id="1d251-123">活頁簿活動 - 圖表</span><span class="sxs-lookup"><span data-stu-id="1d251-123">Workbook Activity - Chart</span></span>|<span data-ttu-id="1d251-124">報告資料存取頻率。</span><span class="sxs-lookup"><span data-stu-id="1d251-124">Reports on frequency of data access.</span></span> <span data-ttu-id="1d251-125">您可以了解每日或每週發生 PowerPivot 資料來源連接的頻率。</span><span class="sxs-lookup"><span data-stu-id="1d251-125">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="1d251-126">活頁簿活動 - 清單</span><span class="sxs-lookup"><span data-stu-id="1d251-126">Workbook Activity - Lists</span></span>|<span data-ttu-id="1d251-127">報告資料存取頻率。</span><span class="sxs-lookup"><span data-stu-id="1d251-127">Reports on frequency of data access.</span></span> <span data-ttu-id="1d251-128">您可以了解每日或每週發生 PowerPivot 資料來源連接的頻率。</span><span class="sxs-lookup"><span data-stu-id="1d251-128">You can learn how often connections to PowerPivot data sources occur on a daily or weekly basis.</span></span>|  
|<span data-ttu-id="1d251-129">資料重新整理 - 最近的活動</span><span class="sxs-lookup"><span data-stu-id="1d251-129">Data Refresh - Recent Activity</span></span>|<span data-ttu-id="1d251-130">報告資料重新整理的狀態，包括無法執行的工作。</span><span class="sxs-lookup"><span data-stu-id="1d251-130">Reports on the status of data refresh jobs, including jobs that failed to run.</span></span> <span data-ttu-id="1d251-131">此報告會提供應用程式層級的資料重新整理作業綜合檢視。</span><span class="sxs-lookup"><span data-stu-id="1d251-131">This report provides a composite view into data refresh operations at the application level.</span></span> <span data-ttu-id="1d251-132">管理員一眼就能看清為整個 PowerPivot 服務應用程式所定義的資料重新整理工作數。</span><span class="sxs-lookup"><span data-stu-id="1d251-132">Administrators can see at a glance the number of data refresh jobs that are defined for the entire PowerPivot service application.</span></span>|  
|<span data-ttu-id="1d251-133">資料重新整理 - 最近的失敗</span><span class="sxs-lookup"><span data-stu-id="1d251-133">Data Refresh - Recent Failures</span></span>|<span data-ttu-id="1d251-134">列出未順利完成資料重新整理的 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="1d251-134">Lists the PowerPivot workbooks that did not complete data refresh successfully.</span></span>|  
|<span data-ttu-id="1d251-135">報表</span><span class="sxs-lookup"><span data-stu-id="1d251-135">Reports</span></span>|<span data-ttu-id="1d251-136">包含您可以在 Excel 中開啟的報表連結。</span><span class="sxs-lookup"><span data-stu-id="1d251-136">Contains links to reports that you can open in Excel.</span></span>|  
  
##  <a name="open-powerpivot-management-dashboard"></a><a name="open"></a><span data-ttu-id="1d251-137">開啟 PowerPivot 管理儀表板</span><span class="sxs-lookup"><span data-stu-id="1d251-137">Open PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="1d251-138">儀表板一次只為一個 PowerPivot 服務應用程式顯示資訊。</span><span class="sxs-lookup"><span data-stu-id="1d251-138">The dashboard shows information for one PowerPivot service application at a time.</span></span> <span data-ttu-id="1d251-139">您可以從兩個不同的位置開啟管理儀表板。</span><span class="sxs-lookup"><span data-stu-id="1d251-139">You can open the management dashboard from two different locations.</span></span>  
  
### <a name="open-the-dashboard-from-general-application-settings"></a><span data-ttu-id="1d251-140">從一般應用程式設定開啟儀表板</span><span class="sxs-lookup"><span data-stu-id="1d251-140">Open the dashboard from General Application Settings</span></span>  
  
1.  <span data-ttu-id="1d251-141">在 [管理中心] 的 **[一般應用程式設定]** 群組中，按一下 **[PowerPivot 管理儀表板]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-141">In Central Administration, in the **General Application Settings** group, click **PowerPivot Management Dashboard**.</span></span>  
  
2.  <span data-ttu-id="1d251-142">在主頁面上選取您要檢視作業資料的 PowerPivot 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d251-142">On the main page, select the PowerPivot service application for which you want to view operations data.</span></span>  
  
### <a name="open-the-dashboard-from-a-powerpivot-service-application"></a><span data-ttu-id="1d251-143">從 PowerPivot 服務應用程式開啟儀表板</span><span class="sxs-lookup"><span data-stu-id="1d251-143">Open the dashboard from a PowerPivot service application</span></span>  
  
1.  <span data-ttu-id="1d251-144">在 [管理中心] 的 [**應用程式管理**] 中，按一下 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="1d251-144">In Central Administration, in **Application Management**, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="1d251-145">按一下 PowerPivot 服務應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d251-145">Click the name of the PowerPivot service application.</span></span> <span data-ttu-id="1d251-146">PowerPivot 管理儀表板就會顯示目前服務應用程式的作業資料。</span><span class="sxs-lookup"><span data-stu-id="1d251-146">The PowerPivot Management Dashboard displays operational data for the current service application.</span></span>  
  
### <a name="change-the-current-service-application"></a><span data-ttu-id="1d251-147">變更目前的服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="1d251-147">Change the current service application.</span></span>  
 <span data-ttu-id="1d251-148">若要在管理儀表板中變更目前的 PowerPivot 服務應用程式：</span><span class="sxs-lookup"><span data-stu-id="1d251-148">To change current PowerPivot service application in the management dashboard:</span></span>  
  
1.  <span data-ttu-id="1d251-149">在 PowerPivot 管理儀表板的頂端，記下目前服務應用程式的名稱，例如 [**預設的 PowerPivot 服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="1d251-149">At the top of the PowerPivot management dashboard, note the name of the current service application, for example **Default PowerPivot Service Application**.</span></span>  
  
2.  <span data-ttu-id="1d251-150">在 **[動作]** 儀表板中，按一下 **[列示服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-150">In the **Actions** dashboard, click **List Service Applications**.</span></span>  
  
3.  <span data-ttu-id="1d251-151">按一下您想要查看管理儀表板報表之 PowerPivot 服務應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1d251-151">Click the name of the PowerPivot Service application for which you want to see management dashboard reports.</span></span>  
  
##  <a name="source-data-in-dashboards"></a><a name="sourcedata"></a> <span data-ttu-id="1d251-152">儀表板中的來源資料</span><span class="sxs-lookup"><span data-stu-id="1d251-152">Source Data in Dashboards</span></span>  
 <span data-ttu-id="1d251-153">儀表板、報表和網頁組件會顯示內部資料模型的資料，而該模型會從系統和 PowerPivot 應用程式資料庫中提取資料。</span><span class="sxs-lookup"><span data-stu-id="1d251-153">Dashboards, reports and web parts show data from an internal data model that pulls data from the system and PowerPivot application databases.</span></span> <span data-ttu-id="1d251-154">內部資料模型內嵌在管理中心網站所裝載 PowerPivot 活頁簿中。</span><span class="sxs-lookup"><span data-stu-id="1d251-154">The internal data model is embedded in a PowerPivot workbook hosted in the Central Administration site.</span></span> <span data-ttu-id="1d251-155">資料模型的結構是固定的。</span><span class="sxs-lookup"><span data-stu-id="1d251-155">The structure of the data model is fixed.</span></span> <span data-ttu-id="1d251-156">雖然您可以使用 PowertPivot 活頁簿做為資料來源建立新報表，但是不得以任何方式修改結構而中斷了使用該來源的預先定義報表。</span><span class="sxs-lookup"><span data-stu-id="1d251-156">Although you can use the PowertPivot workbook as a data source to create new reports, you must not modify the structure in a way that breaks the predefined reports that use it.</span></span>  
  
 <span data-ttu-id="1d251-157">如需有關如何收集資料的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="1d251-157">For more information about how data is collected, see the following:</span></span>  
  
-   [<span data-ttu-id="1d251-158">PowerPivot 使用量資料收集</span><span class="sxs-lookup"><span data-stu-id="1d251-158">PowerPivot Usage Data Collection</span></span>](power-pivot-usage-data-collection.md)  
  
-   [<span data-ttu-id="1d251-159">設定 &#40;PowerPivot for SharePoint 的使用量資料收集</span><span class="sxs-lookup"><span data-stu-id="1d251-159">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
 <span data-ttu-id="1d251-160">若要擷取 PowerPivot 伺服器系統的相關資料，請確認已針對每個 PowerPivot 服務應用程式啟用事件訊息、資料重新整理記錄和其他使用量記錄。</span><span class="sxs-lookup"><span data-stu-id="1d251-160">To capture data about the PowerPivot server system, verify event messaging, data refresh history, and other usage history is enabled for each PowerPivot service application.</span></span> <span data-ttu-id="1d251-161">一般伺服器作業期間所蒐集的伺服器與使用量資料就是來源資料，最後會送入內部資料模型中。</span><span class="sxs-lookup"><span data-stu-id="1d251-161">The server and usage data gathered during normal server operations is the source data that ends up in the internal data model.</span></span> <span data-ttu-id="1d251-162">**注意** ：如果關閉事件或使用量記錄，綜合報表會不完整或發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d251-162">**Note:** If you turn off events or usage history, the composite reports will be incomplete or erroneous.</span></span>  
  
##  <a name="edit-powerpivot-dashboard"></a><a name="edit"></a><span data-ttu-id="1d251-163">編輯 PowerPivot 儀表板</span><span class="sxs-lookup"><span data-stu-id="1d251-163">Edit PowerPivot Dashboard</span></span>  
 <span data-ttu-id="1d251-164">如果您擁有開發或自訂儀表板的專業技術，可以編輯儀表板以包含新的網頁組件。</span><span class="sxs-lookup"><span data-stu-id="1d251-164">If you have expertise in dashboard development or customization, you can edit the dashboard to include new web parts.</span></span> <span data-ttu-id="1d251-165">您也可以編輯包含於儀表板中的網頁組件屬性。</span><span class="sxs-lookup"><span data-stu-id="1d251-165">You can also edit the web part properties that are included in the dashboard.</span></span>  
  
##  <a name="create-custom-reports-for-powerpivot-management-dashboard"></a><a name="reports"></a><span data-ttu-id="1d251-166">建立 PowerPivot 管理儀表板的自訂報表</span><span class="sxs-lookup"><span data-stu-id="1d251-166">Create Custom Reports for PowerPivot Management Dashboard</span></span>  
 <span data-ttu-id="1d251-167">基於報表用途，PowerPivot 使用量資料與記錄會保留在與儀表板一起建立和設定的內部 PowerPivot 活頁簿中。</span><span class="sxs-lookup"><span data-stu-id="1d251-167">For reporting purposes, PowerPivot usage data and history is kept in an internal PowerPivot workbook that is created and configured along with the dashboard.</span></span> <span data-ttu-id="1d251-168">如果預設報表沒有提供您所需要的資訊，可以在 Excel 中，根據活頁簿建立自訂報表。</span><span class="sxs-lookup"><span data-stu-id="1d251-168">If the default reports do not provide the information you require, you can create custom reports in Excel based on the workbook.</span></span> <span data-ttu-id="1d251-169">如果您稍後升級或解除安裝 PowerPivot 方案檔，您所建立的活頁簿和所有自訂報表都會保留下來。</span><span class="sxs-lookup"><span data-stu-id="1d251-169">Both the workbook and any custom reports that you create will be preserved if you upgrade or uninstall the PowerPivot solution files later.</span></span> <span data-ttu-id="1d251-170">這些活頁簿和報表會儲存在管理中心網站內的 PowerPivot 管理庫中。</span><span class="sxs-lookup"><span data-stu-id="1d251-170">The workbook and reports are stored in the PowerPivot Management library within the Central Administration site.</span></span> <span data-ttu-id="1d251-171">預設看不到這個管理庫，但是您可以使用 [網站動作] 底下的 [檢視所有網站內容] 動作檢視此管理庫。</span><span class="sxs-lookup"><span data-stu-id="1d251-171">This library is not visible by default, but you can view the library using the View All Site Content action under Site Actions.</span></span>  
  
 <span data-ttu-id="1d251-172">為了協助您開始使用自訂報表，PowerPivot 管理儀表板會提供 Office 資料連線 (.odc) 檔案以連線到來源活頁簿。</span><span class="sxs-lookup"><span data-stu-id="1d251-172">To help you get started with custom reporting, PowerPivot Management Dashboard provides an Office Data Connection (.odc) file to connect to the source workbook.</span></span> <span data-ttu-id="1d251-173">例如，您可以在 Excel 中使用 .odc 檔案來建立其他報表。</span><span class="sxs-lookup"><span data-stu-id="1d251-173">Dor example, you can use the .odc file in Excel to create additional reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1d251-174">當您嘗試在 Excel 中使用 .odc 檔案時，請編輯該檔案以防止下列錯誤：「初始化資料來源失敗」。</span><span class="sxs-lookup"><span data-stu-id="1d251-174">Edit the file to avoid the following error when attempting to use the .odc file in Excel: "Initialization of the data source failed".</span></span> <span data-ttu-id="1d251-175">自動產生的 .odc 檔案包含 MSOLAP OLE DB 提供者不支援的參數。</span><span class="sxs-lookup"><span data-stu-id="1d251-175">The auto-generated .odc file includes a parameter that are not supported by the MSOLAP OLE DB provider.</span></span> <span data-ttu-id="1d251-176">下列指示提供移除參數的因應措施。</span><span class="sxs-lookup"><span data-stu-id="1d251-176">The following instructions provide the workaround for removing the parameters.</span></span>  
  
 <span data-ttu-id="1d251-177">您必須是伺服陣列或服務管理員，才能根據管理中心的 PowerPivot 活頁簿建立報表。</span><span class="sxs-lookup"><span data-stu-id="1d251-177">You must be a farm or service administrator to build reports that are based on the PowerPivot workbook in Central Administration.</span></span>  
  
1.  <span data-ttu-id="1d251-178">開啟 PowerPivot 管理儀表板。</span><span class="sxs-lookup"><span data-stu-id="1d251-178">Open the PowerPivot Management Dashboard.</span></span>  
  
2.  <span data-ttu-id="1d251-179">捲動到頁面底部的 **[報表]** 區段。</span><span class="sxs-lookup"><span data-stu-id="1d251-179">Scroll to the **Reports** section at the bottom of the page.</span></span>  
  
3.  <span data-ttu-id="1d251-180">按一下 **[PowerPivot 管理資料]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-180">Click **PowerPivot Management Data**.</span></span>  
  
4.  <span data-ttu-id="1d251-181">將 .odc 檔案儲存至本機資料夾。</span><span class="sxs-lookup"><span data-stu-id="1d251-181">Save the .odc file to a local folder.</span></span>  
  
5.  <span data-ttu-id="1d251-182">在文字編輯器中開啟 .odc 檔。</span><span class="sxs-lookup"><span data-stu-id="1d251-182">Open the .odc file in a text editor.</span></span>  
  
6.  <span data-ttu-id="1d251-183">在 `<odc:ConnectionString>` 元素中，捲動至行尾並移除 `Embedded Data=False`，然後移除 `Edit Mode=0`。</span><span class="sxs-lookup"><span data-stu-id="1d251-183">In the `<odc:ConnectionString>` element, scroll to the end of the line and remove `Embedded Data=False`, and then remove `Edit Mode=0`.</span></span> <span data-ttu-id="1d251-184">如果字串中的最後一個字元是分號，請將它移除。</span><span class="sxs-lookup"><span data-stu-id="1d251-184">If the last character in the string is a semicolon, remove it now.</span></span>  
  
7.  <span data-ttu-id="1d251-185">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="1d251-185">Save the File.</span></span> <span data-ttu-id="1d251-186">其餘步驟取決於您所使用的 PowerPivot 與 Excel 版本。</span><span class="sxs-lookup"><span data-stu-id="1d251-186">The remaining steps depend on which version of PowerPivot and Excel you are using.</span></span>  
  
8.  1.  <span data-ttu-id="1d251-187">啟動 Excel 2013。</span><span class="sxs-lookup"><span data-stu-id="1d251-187">Start Excel 2013</span></span>  
  
    2.  <span data-ttu-id="1d251-188">在 **[PowerPivot]** 功能區中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-188">In the **PowerPivot** ribbon, click **Manage**.</span></span>  
  
    3.  <span data-ttu-id="1d251-189">按一下 **[取得外部資料]** ，然後按一下 **[現有連接]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-189">Click **Get External Data** and then click **Existing connections**.</span></span>  
  
    4.  <span data-ttu-id="1d251-190">如果您看到 .ODC 檔案，請按一下該檔案。</span><span class="sxs-lookup"><span data-stu-id="1d251-190">Click the .ODC file if you see it.</span></span> <span data-ttu-id="1d251-191">如果您看不到 .ODC 檔案，請按一下 **[瀏覽其他]** ，然後在檔案路徑中，指定 .odc 檔案。</span><span class="sxs-lookup"><span data-stu-id="1d251-191">If you do not see the .ODC file, click **Browse for More** and then in the file path, specify the .odc file.</span></span>  
  
    5.  <span data-ttu-id="1d251-192">按一下 [**開啟**]</span><span class="sxs-lookup"><span data-stu-id="1d251-192">Click **Open**</span></span>  
  
    6.  <span data-ttu-id="1d251-193">按一下 **[測試連接]** 確認連接是否成功。</span><span class="sxs-lookup"><span data-stu-id="1d251-193">Click **Test Connection** to verify the connection succeeds.</span></span>  
  
    7.  <span data-ttu-id="1d251-194">輸入連接的名稱，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-194">Click type a name for the connection and then click **Next**.</span></span>  
  
    8.  <span data-ttu-id="1d251-195">在 [指定 MDX 查詢] 中，按一下 [**設計**] 開啟 MDX 查詢設計工具，以組合您要使用的資料，**如果您看到錯誤訊息**「編輯模式屬性名稱的格式不正確。」，請確認您已編輯。ODC 檔案。</span><span class="sxs-lookup"><span data-stu-id="1d251-195">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with **If you see the error message** "The Edit Mode property name is not formatted correctly.", verify you edits the .ODC file.</span></span>  
  
    9. <span data-ttu-id="1d251-196">按一下 **[確定]** ，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-196">Click **OK** and then click **Finish**.</span></span>  
  
    10. <span data-ttu-id="1d251-197">建立樞紐分析表或樞紐分析圖報表，將 Excel 中的資料視覺化。</span><span class="sxs-lookup"><span data-stu-id="1d251-197">Create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
9. 1.  <span data-ttu-id="1d251-198">啟動 Excel 2010。</span><span class="sxs-lookup"><span data-stu-id="1d251-198">Start Excel 2010.</span></span>  
  
    2.  <span data-ttu-id="1d251-199">按一下 [PowerPivot] 功能區上的 **[啟動 PowerPivot 視窗]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-199">On the PowerPivot ribbon, click **Launch PowerPivot Window**.</span></span>  
  
    3.  <span data-ttu-id="1d251-200">在 PowerPivot 視窗的 [設計] 功能區中，按一下 **[現有連接]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-200">On the Design ribbon in the PowerPivot window, click **Existing Connections**.</span></span>  
  
    4.  <span data-ttu-id="1d251-201">按一下 **[瀏覽其他]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-201">Click **Browse for More**.</span></span>  
  
    5.  <span data-ttu-id="1d251-202">在檔案路徑中，指定 .odc 檔。</span><span class="sxs-lookup"><span data-stu-id="1d251-202">In the file path, specify the .odc file.</span></span>  
  
    6.  <span data-ttu-id="1d251-203">按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="1d251-203">Click **Open**.</span></span> <span data-ttu-id="1d251-204">「資料表匯入精靈」隨即使用包含使用方式資料之 PowerPivot 活頁簿的連接字串啟動。</span><span class="sxs-lookup"><span data-stu-id="1d251-204">The Table Import Wizard starts, using the connection string to the PowerPivot workbook that contains usage data.</span></span>  
  
    7.  <span data-ttu-id="1d251-205">按一下 **[測試連接]** 確認您是否擁有存取權。</span><span class="sxs-lookup"><span data-stu-id="1d251-205">Click **Test Connection** to verify that you have access.</span></span>  
  
    8.  <span data-ttu-id="1d251-206">為連接輸入易記的名稱，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="1d251-206">Enter a friendly name for the connection, and then click **Next**.</span></span>  
  
    9. <span data-ttu-id="1d251-207">在 [指定 MDX 查詢] 中，按一下 **[設計]** 開啟 MDX 查詢設計工具以組合您要使用的資料，然後建立樞紐分析表或樞紐分析圖報表，將 Excel 中的資料視覺化。</span><span class="sxs-lookup"><span data-stu-id="1d251-207">In Specify MDX Query, click **Design** to open the MDX query designer to assemble the data you want to work with, and then create PivotTable or PivotChart reports to visualize the data in Excel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d251-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d251-208">See Also</span></span>  
 <span data-ttu-id="1d251-209">[PowerPivot 資料重新整理與 SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="1d251-209">[PowerPivot Data Refresh with SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 [<span data-ttu-id="1d251-210">設定 &#40;PowerPivot for SharePoint 的使用量資料收集</span><span class="sxs-lookup"><span data-stu-id="1d251-210">Configure Usage Data Collection for &#40;PowerPivot for SharePoint</span></span>](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
