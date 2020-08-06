---
title: SQL Server 2014 中的報表產生器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10428"
helpviewer_keywords:
- overview of Report Builder
- getting started
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b2fb8994272eb24594239551d623021f7b87694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592490"
---
# <a name="report-builder-in-sql-server-2014"></a><span data-ttu-id="62aa5-102">SQL Server 2014 中的報表產生器</span><span class="sxs-lookup"><span data-stu-id="62aa5-102">Report Builder in SQL Server 2014</span></span>
  <span data-ttu-id="62aa5-103">報表產生器是一個報表撰寫環境，適合喜歡在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office 環境中工作的商務使用者使用。</span><span class="sxs-lookup"><span data-stu-id="62aa5-103">Report Builder is a report authoring environment for business users who prefer to work in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Office environment.</span></span> <span data-ttu-id="62aa5-104">當您設計報表時，可以指定要取得資料的位置、要取得的資料，以及要顯示資料的方式。</span><span class="sxs-lookup"><span data-stu-id="62aa5-104">When you design a report, you specify where to get the data, which data to get, and how to display the data.</span></span> <span data-ttu-id="62aa5-105">當您執行報表時，報表處理器會採用已指定的所有資訊、擷取資料，然後將它與報表配置結合，以便產生報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-105">When you run the report, the report processor takes all the information you have specified, retrieves the data, and combines it with the report layout to generate the report.</span></span> <span data-ttu-id="62aa5-106">您可以在報表產生器中預覽報表，也可以將報表發行至報表伺服器或處於 SharePoint 整合模式的報表伺服器，讓其他人執行報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-106">You can preview your reports in Report Builder, or you can publish your report to a report server or a report server in SharePoint integrated mode, where others can run it.</span></span>  
  
 <span data-ttu-id="62aa5-107">下圖中的報表提供一個矩陣，內含資料列和資料行群組、走勢圖、指標以及位於邊角資料格的摘要圓形圖，並附有一份地圖，地圖中具有兩組以色彩和圓形大小呈現的地理資料。</span><span class="sxs-lookup"><span data-stu-id="62aa5-107">The report in this illustration features a matrix with row and column groups, sparklines, indicators, and a summary pie chart in the corner cell, accompanied by a map with two sets of geographic data represented by color and by circle size.</span></span>  
  
 <span data-ttu-id="62aa5-108">![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")</span><span class="sxs-lookup"><span data-stu-id="62aa5-108">![rs_GettingStartedReport](../media/rs-gettingstartedreport.gif "rs_GettingStartedReport")</span></span>  
  
##  <a name="jump-start-report-creation"></a><a name="JumpStartReptCreation"></a><span data-ttu-id="62aa5-109">快速入門報表建立</span><span class="sxs-lookup"><span data-stu-id="62aa5-109">Jump-Start Report Creation</span></span>  
  
-   <span data-ttu-id="62aa5-110">啟動您小組中其他人所建立的**報表 withreport 元件**。</span><span class="sxs-lookup"><span data-stu-id="62aa5-110">**Start your report withreport parts** created by someone else on your team.</span></span> <span data-ttu-id="62aa5-111">報表組件是已個別發行至報表伺服器或與報表伺服器整合之 SharePoint 網站上的報表項目。</span><span class="sxs-lookup"><span data-stu-id="62aa5-111">Report parts are report items that have been published separately to a report server or a SharePoint site that is integrated with a report server.</span></span> <span data-ttu-id="62aa5-112">報表組件可以在其他報表中重複使用。</span><span class="sxs-lookup"><span data-stu-id="62aa5-112">They can be reused in other reports.</span></span> <span data-ttu-id="62aa5-113">諸如資料表、矩陣、圖表和影像等報表項目都可以發行為報表組件。</span><span class="sxs-lookup"><span data-stu-id="62aa5-113">Report items such as tables, matrices, charts, and images can be published as report parts.</span></span>  
  
-   <span data-ttu-id="62aa5-114">從小組中其他人所建立的**共用資料集開始**。</span><span class="sxs-lookup"><span data-stu-id="62aa5-114">**Start with a shared dataset** created by someone else on your team.</span></span> <span data-ttu-id="62aa5-115">共用資料集是以儲存到報表伺服器或與報表伺服器整合之 SharePoint 網站上之共用資料來源做為基礎的查詢。</span><span class="sxs-lookup"><span data-stu-id="62aa5-115">Shared datasets are queries based on a shared data source that are saved to a report server or a SharePoint site that is integrated with a report server.</span></span>  
  
-   <span data-ttu-id="62aa5-116">**開始使用 [資料表精靈]、[矩陣精靈] 或 [圖表精靈]** 。</span><span class="sxs-lookup"><span data-stu-id="62aa5-116">**Start with the Table, Matrix, or Chart wizard**.</span></span> <span data-ttu-id="62aa5-117">您可以選擇資料來源連接、拖放欄位以建立資料集查詢、選取配置和樣式，以及自訂報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-117">Choose a data source connection, drag and drop fields to create a dataset query, select a layout and style, and customize your report.</span></span>  
  
-   <span data-ttu-id="62aa5-118">**開始使用 [地圖精靈]** ，以建立根據地理或幾何背景顯示彙總資料的報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-118">**Start with the Map wizard** to create reports that display aggregated data against a geographic or geometric background.</span></span> <span data-ttu-id="62aa5-119">地圖資料可能是來自 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢或環境系統研究協會 (Environmental Systems Research Institute, Inc.) 的空間資料。(ESRI) 形狀檔。</span><span class="sxs-lookup"><span data-stu-id="62aa5-119">Map data can be spatial data from a [!INCLUDE[tsql](../../includes/tsql-md.md)] query or an Environmental Systems Research Institute, Inc. (ESRI) shapefile.</span></span> <span data-ttu-id="62aa5-120">您也可以加入 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing 地圖底圖背景。</span><span class="sxs-lookup"><span data-stu-id="62aa5-120">You can also add a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Bing map tile background.</span></span>  
  

  
##  <a name="design-your-report"></a><a name="DesignRept"></a><span data-ttu-id="62aa5-121">設計您的報表</span><span class="sxs-lookup"><span data-stu-id="62aa5-121">Design Your Report</span></span>  
  
-   <span data-ttu-id="62aa5-122">**建立含有資料表、矩陣、圖表和自由形式報表配置的報表。**</span><span class="sxs-lookup"><span data-stu-id="62aa5-122">**Create reports with table, matrix, chart, and free-form report layouts.**</span></span> <span data-ttu-id="62aa5-123">針對以資料行為基礎的資料建立資料表報表，針對摘要資料建立矩陣報表 (例如交叉分析或樞紐分析表報表)，針對圖形化資料建立圖表報表，以及針對其他任何內容建立任意格式的報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-123">Create table reports for column-based data, matrix reports (like cross-tab or PivotTable reports) for summarized data, chart reports for graphical data, and free-form reports for anything else.</span></span> <span data-ttu-id="62aa5-124">報表可以內嵌其他報表和圖表，連同動態 Web 應用程式的清單、圖形和控制項。</span><span class="sxs-lookup"><span data-stu-id="62aa5-124">Reports can embed other reports and charts, together with lists, graphics, and controls for dynamic Web-based applications.</span></span>  
  
-   <span data-ttu-id="62aa5-125">**來自各種資料來源的報表。**</span><span class="sxs-lookup"><span data-stu-id="62aa5-125">**Report from a variety of data sources.**</span></span> <span data-ttu-id="62aa5-126">使用具有 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 管理的資料提供者、OLE DB 提供者或 ODBC 資料來源之任何資料來源類型中的資料建立報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-126">Build reports using data from any data source type that has a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-managed data provider, OLE DB provider, or ODBC data source.</span></span> <span data-ttu-id="62aa5-127">您可以建立使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、Oracle、Hyperion 及其他資料庫中關聯式和多維度資料的報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-127">You can create reports that use relational and multidimensional data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], Oracle, Hyperion, and other databases.</span></span> <span data-ttu-id="62aa5-128">您可以使用 XML 資料處理延伸模組，從任何 XML 資料來源擷取資料。</span><span class="sxs-lookup"><span data-stu-id="62aa5-128">You can use an XML data processing extension to retrieve data from any XML data source.</span></span> <span data-ttu-id="62aa5-129">您可以使用資料表值函數來設計自訂資料來源。</span><span class="sxs-lookup"><span data-stu-id="62aa5-129">You can use table-valued functions to design custom data sources.</span></span>  
  
-   <span data-ttu-id="62aa5-130">**修改現有的報表。**</span><span class="sxs-lookup"><span data-stu-id="62aa5-130">**Modify existing reports.**</span></span> <span data-ttu-id="62aa5-131">藉由使用報表產生器，您可以自訂及更新在報表設計師中建立的報表 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="62aa5-131">By using Report Builder, you can customize and update reports that were created in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Report Designer.</span></span>  
  
-   <span data-ttu-id="62aa5-132">藉由篩選、分組和排序資料，或是加入公式或運算式來**修改您的資料**。</span><span class="sxs-lookup"><span data-stu-id="62aa5-132">**Modify your data** by filtering, grouping and sorting data, or by adding formulas or expressions.</span></span>  
  
-   <span data-ttu-id="62aa5-133">**加入圖表、量測計、走勢圖和指標** ，以視覺化格式摘要列出資料，並且一次展示大量的彙總資訊。</span><span class="sxs-lookup"><span data-stu-id="62aa5-133">**Add charts, gauges, sparklines, and indicators** to summarize data in a visual format, and present large volumes of aggregated information at a glance.</span></span>  
  
-   <span data-ttu-id="62aa5-134">**新增互動式功能**，例如文件引導模式、顯示/隱藏按鈕，以及子報表和鑽研報表的鑽研連結。</span><span class="sxs-lookup"><span data-stu-id="62aa5-134">**Add interactive features** such as document maps, show/hide buttons, and drillthrough links to subreports and drillthrough reports.</span></span> <span data-ttu-id="62aa5-135">使用參數和篩選來篩選自訂檢視的資料。</span><span class="sxs-lookup"><span data-stu-id="62aa5-135">Use parameters and filters to filter data for customized views.</span></span>  
  
-   <span data-ttu-id="62aa5-136">**內嵌或參考影像**與其他資源，包括外部內容。</span><span class="sxs-lookup"><span data-stu-id="62aa5-136">**Embed or reference images** and other resources, including external content.</span></span>  
  

  
##  <a name="manage-your-report"></a><a name="ManageRpt"></a><span data-ttu-id="62aa5-137">管理您的報表</span><span class="sxs-lookup"><span data-stu-id="62aa5-137">Manage Your Report</span></span>  
  
-   <span data-ttu-id="62aa5-138">**儲存報表的定義**至您的電腦或報表伺服器，以便您進行管理並與其他人共用。</span><span class="sxs-lookup"><span data-stu-id="62aa5-138">**Save the definition of the report** to your computer or to the report server, where you can manage it and share it with others.</span></span>  
  
-   <span data-ttu-id="62aa5-139">當您開啟報表時，或在您開啟報表之後，**選擇呈現格式**。</span><span class="sxs-lookup"><span data-stu-id="62aa5-139">**Choose a presentation format** when you open the report, or after you open the report.</span></span> <span data-ttu-id="62aa5-140">您可以選取 Web 導向、頁面導向和傳統型應用程式格式。</span><span class="sxs-lookup"><span data-stu-id="62aa5-140">You can select Web-oriented, page-oriented, and desktop application formats.</span></span> <span data-ttu-id="62aa5-141">格式包括 HTML、MHTML、PDF、XML、CSV、TIFF、Word 及 Excel。</span><span class="sxs-lookup"><span data-stu-id="62aa5-141">Formats include HTML, MHTML, PDF, XML, CSV, TIFF, Word, and Excel.</span></span>  
  
-   <span data-ttu-id="62aa5-142">**設定訂閱。**</span><span class="sxs-lookup"><span data-stu-id="62aa5-142">**Set up subscriptions.**</span></span> <span data-ttu-id="62aa5-143">當您將報表發行至報表伺服器或處於 SharePoint 整合模式的報表伺服器之後，就可以將報表設定成在特定時間執行、建立報表記錄，以及設定電子郵件訂閱。</span><span class="sxs-lookup"><span data-stu-id="62aa5-143">After you publish the report to the report server or a report server in SharePoint integrated mode, you can configure your report to run at a specific time, create a report history, and set up e-mail subscriptions.</span></span>  
  
-   <span data-ttu-id="62aa5-144">使用 Reporting Services Atom 轉譯延伸模組，從報表**產生資料摘要** 。</span><span class="sxs-lookup"><span data-stu-id="62aa5-144">**Generate data feeds** from your report by using the Reporting Services Atom rendering extension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62aa5-145">報表伺服器管理員會在報表伺服器或處於 SharePoint 整合模式的報表伺服器上管理已發行的報表。</span><span class="sxs-lookup"><span data-stu-id="62aa5-145">Published reports are managed on a report server or a report server in SharePoint integrated mode by a report server administrator.</span></span> <span data-ttu-id="62aa5-146">報表伺服器管理員可以定義安全性、設定屬性以及排程作業，例如報表記錄和電子郵件報表傳遞。</span><span class="sxs-lookup"><span data-stu-id="62aa5-146">Report server administrators can define security, set properties, and schedule operations such as report history and e-mail report delivery.</span></span> <span data-ttu-id="62aa5-147">他們可以建立共用排程和共用資料來源，讓它們可供一般使用。</span><span class="sxs-lookup"><span data-stu-id="62aa5-147">They can create shared schedules and shared data sources and make them available for general use.</span></span> <span data-ttu-id="62aa5-148">管理員也會管理所有報表伺服器資料夾。</span><span class="sxs-lookup"><span data-stu-id="62aa5-148">Administrators also manage all of the report server folders.</span></span> <span data-ttu-id="62aa5-149">執行管理工作的能力需視使用者權限而定。</span><span class="sxs-lookup"><span data-stu-id="62aa5-149">The ability to perform management tasks depends on user permissions.</span></span>  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="62aa5-150">本節內容</span><span class="sxs-lookup"><span data-stu-id="62aa5-150">In This Section</span></span>  
 [<span data-ttu-id="62aa5-151">SQL Server 2014 報表產生器的新功能</span><span class="sxs-lookup"><span data-stu-id="62aa5-151">What's New in Report Builder for SQL Server 2014</span></span>](../what-s-new-in-report-builder-for-sql-server-2014.md)  
 <span data-ttu-id="62aa5-152">描述此版本報表產生器的新功能，包括地圖。</span><span class="sxs-lookup"><span data-stu-id="62aa5-152">Describes the new features in this version of Report Builder, including maps.</span></span>  
  
 [<span data-ttu-id="62aa5-153">教學課程：離線建立快速圖表報表</span><span class="sxs-lookup"><span data-stu-id="62aa5-153">Tutorial: Creating a Quick Chart Report Offline</span></span>](tutorial-create-a-quick-chart-report-offline-report-builder.md)  
 <span data-ttu-id="62aa5-154">介紹報表產生器以及可協助您建立報表的精靈。</span><span class="sxs-lookup"><span data-stu-id="62aa5-154">Introduces Report Builder and the wizards available to help you create reports.</span></span> <span data-ttu-id="62aa5-155">此教學課程會提供一組資料供您使用，所以您不需要連接至資料來源以便開始作業。</span><span class="sxs-lookup"><span data-stu-id="62aa5-155">The tutorial provides a set of data for you to work with so you do not need to connect to a data source to get started.</span></span>  
  
 [<span data-ttu-id="62aa5-156">規劃報表 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="62aa5-156">Planning a Report &#40;Report Builder&#41;</span></span>](../report-design/planning-a-report-report-builder.md)  
 <span data-ttu-id="62aa5-157">提供有關開始建立報表之前應該考量之事項的資訊。</span><span class="sxs-lookup"><span data-stu-id="62aa5-157">Provides information on what you should consider before you start to build your report.</span></span>  
  
 [<span data-ttu-id="62aa5-158">報表撰寫概念 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="62aa5-158">Report Authoring Concepts &#40;Report Builder and SSRS&#41;</span></span>](../report-design/report-authoring-concepts-report-builder-and-ssrs.md)  
 <span data-ttu-id="62aa5-159">定義整個報表產生器文件集中使用的重要概念。</span><span class="sxs-lookup"><span data-stu-id="62aa5-159">Defines key concepts used in throughout Report Builder documentation.</span></span>  
  
 [<span data-ttu-id="62aa5-160">報表設計檢視 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="62aa5-160">Report Design View &#40;Report Builder&#41;</span></span>](report-design-view-report-builder.md)  
 <span data-ttu-id="62aa5-161">說明報表設計檢視的不同窗格和區域。</span><span class="sxs-lookup"><span data-stu-id="62aa5-161">Explains the different panes and regions of report design view.</span></span>  
  
 [<span data-ttu-id="62aa5-162">共用資料集設計檢視 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="62aa5-162">Shared Dataset Design View &#40;Report Builder&#41;</span></span>](shared-dataset-design-view-report-builder.md)  
 <span data-ttu-id="62aa5-163">說明共用資料集設計檢視的不同窗格和區域。</span><span class="sxs-lookup"><span data-stu-id="62aa5-163">Explains the different panes and regions of shared dataset design view.</span></span>  
  
 [<span data-ttu-id="62aa5-164">鍵盤快速鍵 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="62aa5-164">Keyboard Shortcuts &#40;Report Builder&#41;</span></span>](keyboard-shortcuts-report-builder.md)  
 <span data-ttu-id="62aa5-165">概述報表產生器中可用於導覽及設計報表的快速鍵。</span><span class="sxs-lookup"><span data-stu-id="62aa5-165">Outlines the shortcut keys available for navigating and designing reports in Report Builder.</span></span>  
  
 [<span data-ttu-id="62aa5-166">開始報表產生器 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="62aa5-166">Start Report Builder &#40;Report Builder&#41;</span></span>](start-report-builder.md)  
 <span data-ttu-id="62aa5-167">說明如何啟動兩種不同版本的報表產生器：單機版和 [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] 版。</span><span class="sxs-lookup"><span data-stu-id="62aa5-167">Explains how to start the two different versions of Report Builder: stand-alone and [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)].</span></span>  
  
  
