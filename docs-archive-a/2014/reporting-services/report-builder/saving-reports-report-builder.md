---
title: 儲存報表 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 59ddc4b8-9517-4d3f-9c88-a07e9907cecb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9210eafb65ee7adced8d0cd821d88b5f0cbcb9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585103"
---
# <a name="saving-reports-report-builder"></a><span data-ttu-id="7bb7f-102">儲存報表 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="7bb7f-102">Saving Reports (Report Builder)</span></span>
  <span data-ttu-id="7bb7f-103">在報表產生器中，您可以將報表儲存到報表伺服器、SharePoint 文件庫、您具有寫入權限的檔案共用位置或是您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-103">In Report Builder you can save a report to a report server, SharePoint library, file share on which you have write permission, or your computer.</span></span> <span data-ttu-id="7bb7f-104">您可以將報表儲存到開啟它的相同位置，也可以儲存到另一個位置，或是以新的名稱儲存到相同或不同的位置。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-104">You can save a report to the same location from which you opened it, save it to a different location, or save it with a new name to the same or different location.</span></span> <span data-ttu-id="7bb7f-105">根據預設，報表會重新儲存到開啟它的相同位置。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-105">By default, a report is resaved to the location from which you opened it.</span></span> <span data-ttu-id="7bb7f-106">當您儲存報表時，您實際上儲存的是報表定義，報表定義會描述報表配置。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-106">When you save the report, what you are really saving is the report definition, which describes the report layout.</span></span> <span data-ttu-id="7bb7f-107">您不會儲存資料。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-107">You are not saving the data.</span></span> <span data-ttu-id="7bb7f-108">每當您執行報表時，便會重新整理報表資料，而且報表資料可能會與您上次執行報表時的資料不同。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-108">Every time you run the report, the report data is refreshed and is likely to be different than the previous time you ran the report.</span></span>  
  
 <span data-ttu-id="7bb7f-109">如果您想要將報表儲存到另一個格式或是儲存具有資料的報表定義，請使用下列其中一個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 功能：</span><span class="sxs-lookup"><span data-stu-id="7bb7f-109">If you want to save the report to a different format or save the report definition with the data, use one of the following [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] features:</span></span>  
  
-   <span data-ttu-id="7bb7f-110">將轉譯的報表匯出成另一個檔案格式，如逗號分隔的檔案 (CSV) 或 Excel 活頁簿，然後使用該格式儲存報表。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-110">Export a rendered report to a different file format such as comma separated files (CSV) or Excel workbooks and save the report in that format.</span></span> <span data-ttu-id="7bb7f-111">您也可以從報表產生資料摘要，並儲存報表資料。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-111">You can also generate data feeds from reports and save the report data.</span></span>  
  
-   <span data-ttu-id="7bb7f-112">建立要傳遞的報表訂閱，並將報表儲存到檔案共用位置。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-112">Create report subscriptions to deliver and save reports to a file share.</span></span>  
  
-   <span data-ttu-id="7bb7f-113">使用報表記錄，將轉譯的報表版本儲存為歷程記錄複本。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-113">Use report history to save versions of rendered reports as historical copies.</span></span>  
  
 <span data-ttu-id="7bb7f-114">若要深入了解如何直接在報表伺服器上檢視及管理報表，請參閱[尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) 和 msdn.microsoft.com 上《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [線上叢書](https://go.microsoft.com/fwlink/?LinkId=154888)》中的 [Reporting Services 報表伺服器 &#40;原生模式&#41;](../report-server/reporting-services-report-server-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-114">To learn more about viewing and managing reports directly on the report server, see [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) and [Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
##  <a name="saving-report-definitions"></a><a name="SavingReportDefinitions"></a><span data-ttu-id="7bb7f-115">儲存報表定義</span><span class="sxs-lookup"><span data-stu-id="7bb7f-115">Saving Report Definitions</span></span>  
 <span data-ttu-id="7bb7f-116">雖然您可以將報表儲存到電腦，但是將報表儲存到報表伺服器會提供許多優點。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-116">Although you can save reports to your computer, saving reports to a report server offers many advantages.</span></span>  
  
 <span data-ttu-id="7bb7f-117">將報表儲存到報表伺服器會提供下列優點：</span><span class="sxs-lookup"><span data-stu-id="7bb7f-117">Saving a report to a report server offers the following advantages:</span></span>  
  
-   <span data-ttu-id="7bb7f-118">報表會提供給有權存取報表儲存所在之資料夾的其他人使用。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-118">Reports become available to others who have permission to access the folder in which you saved the report.</span></span>  
  
-   <span data-ttu-id="7bb7f-119">您可以從報表管理員來管理及檢視報表。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-119">Reports can be managed and viewed from Report Manager.</span></span>  
  
-   <span data-ttu-id="7bb7f-120">類似資料來源、影像和子報表的報表資源會儲存在一個地方，讓使用者方便存取。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-120">Report resources such as data sources, images, and subreports are stored in one place for easier access.</span></span>  
  
-   <span data-ttu-id="7bb7f-121">報表可以透過訂閱傳遞給其他人。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-121">Reports can be delivered to others by subscriptions.</span></span>  
  
-   <span data-ttu-id="7bb7f-122">報表會安全地儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-122">Reports are securely stored in the report server database.</span></span>  
  
-   <span data-ttu-id="7bb7f-123">報表執行可以記錄下來，並提供效能和稽核資訊。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-123">Report runs can be logged and provide performance and auditing information.</span></span>  
  
 <span data-ttu-id="7bb7f-124">將報表儲存到報表伺服器也稱為發行報表。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-124">Saving a report to a report server is also known as publishing a report.</span></span> <span data-ttu-id="7bb7f-125">當您儲存報表時，您只會儲存報表定義。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-125">When you save the report you save the report definition only.</span></span> <span data-ttu-id="7bb7f-126">每當您執行報表時，便會重新整理報表資料，而且報表資料可能會與您上次執行報表時的資料不同。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-126">Every time you run the report, the report data is refreshed and likely different that the previous time you ran the report.</span></span> <span data-ttu-id="7bb7f-127">如果您想要儲存包含資料的報表定義，您應該使用報表記錄功能。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-127">If you want to save the report definition with the data you should use the report history feature.</span></span> <span data-ttu-id="7bb7f-128">使用這個功能時，您就可以儲存報表的複本連同報表資料。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-128">Using this feature, you save a copy of the report with its data.</span></span>  
  

  
##  <a name="exporting-and-saving-reports"></a><a name="ExportingAndSavingReports"></a> <span data-ttu-id="7bb7f-129">匯出與儲存報表</span><span class="sxs-lookup"><span data-stu-id="7bb7f-129">Exporting and Saving Reports</span></span>  
 <span data-ttu-id="7bb7f-130">若您要封存的報表數量很少，請考慮將報表匯出，並將它儲存成檔案。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-130">If you have a small number of reports to archive, consider exporting a report and saving it as a file.</span></span> <span data-ttu-id="7bb7f-131">在您將報表匯出至應用程式 (例如 PDF 或 Excel) 後，可以將它另存新檔，並放在網路上一個受保護的共用目錄下。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-131">After you export a report to an application (such as PDF or Excel), you can save it as a file and place it in a protected shared directory on the network.</span></span> <span data-ttu-id="7bb7f-132">或者，如果您想要在報表伺服器資料庫中，保留報表的所有複本 (不論何種格式)，您可以將已經儲存的 PDF 或 Excel 檔案，做為資源項目進行上傳。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-132">Alternatively, you can upload a saved PDF or Excel file as a resource item if you want to keep all copies of a report, regardless of the format, in the report server database.</span></span> <span data-ttu-id="7bb7f-133">如需匯出報表的詳細資訊，請參閱[匯出報表 &#40;報表產生器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md)並[上傳檔案或報表 &#40;報表管理員&#41;](../reports/upload-a-file-or-report-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-133">For more information about exporting a report, see [Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) and [Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md).</span></span>  
  

  
##  <a name="using-file-share-delivery"></a><a name="UsingFileShareDelivery"></a> <span data-ttu-id="7bb7f-134">使用檔案共用傳遞</span><span class="sxs-lookup"><span data-stu-id="7bb7f-134">Using File-Share Delivery</span></span>  
 <span data-ttu-id="7bb7f-135">如果您要封存的報表數量很多，請建立訂閱，將報表直接傳遞到檔案系統。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-135">If you have a large number of reports to archive, create a subscription that delivers the report directly to the file system.</span></span> <span data-ttu-id="7bb7f-136">若要使用此方式，您必須對每一個報表建立訂閱、選擇共用資料夾來儲存報表，並且定義排程以決定何時建立檔案。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-136">For this approach, you must create a subscription for each report, choose a shared folder to store the reports, and define a schedule that determines when the file is created.</span></span> <span data-ttu-id="7bb7f-137">一旦完成訂閱的定義，報表伺服器就可以使用您所提供的排程，自動執行報表並將報表檔案加入封存。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-137">Once you define a subscription, the report server can run the report unattended and add report files to the archive using the schedule that you provide.</span></span> <span data-ttu-id="7bb7f-138">如果只是偶爾要封存報表，就可以建立僅使用一次的排程。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-138">You can also create single-use schedules if you want to archive reports on an occasional basis.</span></span> <span data-ttu-id="7bb7f-139">如需有關訂閱和檔案共用傳遞的詳細資訊，請參閱《SQL Server 線上叢書》中 [Reporting Services 文件集](https://go.microsoft.com/fwlink/?linkid=121312) 的＜Reporting Services 中的檔案傳遞＞。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-139">For more information about subscriptions and file share delivery, see "File Delivery in Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="using-report-history"></a><a name="UsingReportHistory"></a> <span data-ttu-id="7bb7f-140">使用報表記錄</span><span class="sxs-lookup"><span data-stu-id="7bb7f-140">Using Report History</span></span>  
 <span data-ttu-id="7bb7f-141">您也可以使用報表記錄功能來建立歷程記錄複本。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-141">You can also use the report history feature to create historical copies.</span></span> <span data-ttu-id="7bb7f-142">然後就可以備份報表伺服器資料庫，並將備份儲存於安全的位置以供未來使用。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-142">You can then back up the report server database and store the backup in a safe location for future use.</span></span> <span data-ttu-id="7bb7f-143">所有的報表記錄 (連同報表、共用資料來源項目、資料夾、訂閱和共用排程) 都會儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-143">All report history (along with reports, shared data source items, folders, subscriptions, and shared schedules) is stored in the report server database.</span></span> <span data-ttu-id="7bb7f-144">您可以建立備份，以永久保留一份報表記錄和中繼資料的副本 (例如指出報表收件者的訂閱資訊)。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-144">You can create a backup to maintain a permanent copy of report history and metadata such as subscription information that indicates the recipients of a report.</span></span> <span data-ttu-id="7bb7f-145">如需詳細資訊，請參閱《SQL Server 線上叢書》中 [Reporting Services 文件集](https://go.microsoft.com/fwlink/?linkid=121312) 的＜管理報表記錄＞。</span><span class="sxs-lookup"><span data-stu-id="7bb7f-145">For more information, see "Managing Report History" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="7bb7f-146">How To 主題</span><span class="sxs-lookup"><span data-stu-id="7bb7f-146">How-To Topics</span></span>  
  
-   [<span data-ttu-id="7bb7f-147">將報表儲存到報表伺服器 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="7bb7f-147">Save Reports to a Report Server &#40;Report Builder&#41;</span></span>](save-reports-to-a-report-server-report-builder.md)  
  
-   [<span data-ttu-id="7bb7f-148">將報表儲存至 SharePoint 文件庫 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="7bb7f-148">Save a Report to a SharePoint Library &#40;Report Builder&#41;</span></span>](save-a-report-to-a-sharepoint-library-report-builder.md)  
  
-   [<span data-ttu-id="7bb7f-149">將報表儲存至您的電腦 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="7bb7f-149">Save Reports to Your Computer &#40;Report Builder&#41;</span></span>](../save-reports-to-your-computer-report-builder.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="7bb7f-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bb7f-150">See Also</span></span>  
 <span data-ttu-id="7bb7f-151">[報表、報表元件和報表定義 &#40;報表產生器和 SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7bb7f-151">[Reports, Report Parts, and Report Definitions &#40;Report Builder and SSRS&#41;](../report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7bb7f-152">[安裝、卸載和報表產生器支援](../install-uninstall-and-report-builder-support.md) </span><span class="sxs-lookup"><span data-stu-id="7bb7f-152">[Install, Uninstall, and Report Builder Support](../install-uninstall-and-report-builder-support.md) </span></span>  
 <span data-ttu-id="7bb7f-153">[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7bb7f-153">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7bb7f-154">[匯出報表 &#40;報表產生器和 SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7bb7f-154">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="7bb7f-155">列印報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7bb7f-155">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](print-reports-report-builder-and-ssrs.md)  
  
  
