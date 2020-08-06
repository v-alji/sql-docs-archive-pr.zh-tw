---
title: 在 Microsoft Surface 裝置和 Apple iOS 裝置上查看 Reporting Services 報表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- iPad
- Safari
- SSRS
- Report Viewer [Reporting Services]
- iOS
ms.assetid: 2124bcf5-d60a-475f-a4ae-de6df44d2860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: db52ed500559969ae52eb9477caa6b410889c1d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598206"
---
# <a name="view-reporting-services-reports-on-microsoft-surface-devices-and--apple-ios-devices"></a><span data-ttu-id="096e1-102">在 Microsoft Surface 裝置及 Apple iOS 裝置上檢視 Reporting Services 報表</span><span class="sxs-lookup"><span data-stu-id="096e1-102">View Reporting Services Reports on Microsoft Surface Devices and  Apple iOS Devices</span></span>
  <span data-ttu-id="096e1-103">本文將描述支援 Microsoft Surface 裝置以及具有 Apple iOS 6 與 Apple Safari 之裝置 (例如 iPad) 的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能和工作流程。</span><span class="sxs-lookup"><span data-stu-id="096e1-103">This article describes the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features and workflows supported for Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari such as the iPad.</span></span>

## <a name="view-and-interact-with-reports"></a><span data-ttu-id="096e1-104">檢視報表並進行互動</span><span class="sxs-lookup"><span data-stu-id="096e1-104">View and Interact With Reports</span></span>
 <span data-ttu-id="096e1-105">從 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]開始， [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 就支援在 Microsoft Surface 裝置以及具有 Apple iOS 6 與 Apple Safari 瀏覽器的裝置 (例如 iPad) 上檢視報表並進行基本互動。</span><span class="sxs-lookup"><span data-stu-id="096e1-105">Starting with [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] supports viewing and basic interactivity with reports on Microsoft Surface devices, and devices with Apple iOS 6 and Apple Safari browser such as the iPad.</span></span> <span data-ttu-id="096e1-106">使用 Microsoft Surface 裝置，也可以發行報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-106">You can also publish reports using Microsoft Surface devices.</span></span>

 <span data-ttu-id="096e1-107">![IPad Desktop](media/videothumbnail.jpg "IPad 桌面")觀看在 iPad 上查看報表的示範。</span><span class="sxs-lookup"><span data-stu-id="096e1-107">![IPad Desktop](media/videothumbnail.jpg "IPad Desktop") Watch a demonstration of viewing reports on an iPad.</span></span>

 <span data-ttu-id="096e1-108">您也可以在 Windows Phone 8 裝置上檢視 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-108">You can also view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports on a Windows Phone 8 device.</span></span>

 <span data-ttu-id="096e1-109">若要使用本主題所描述的功能，請安裝下列其中一個元件：</span><span class="sxs-lookup"><span data-stu-id="096e1-109">To utilize the features described in this topic, install one of the following:</span></span>

-   <span data-ttu-id="096e1-110">如果是原生模式報表伺服器，請安裝 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="096e1-110">For a native mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later.</span></span>

     [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)]<span data-ttu-id="096e1-111">可以從[Microsoft 下載中心](https://www.microsoft.com/download/details.aspx?id=35575)下載。</span><span class="sxs-lookup"><span data-stu-id="096e1-111">is available for download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=35575).</span></span>

-   <span data-ttu-id="096e1-112">如果是 SharePoint 模式報表伺服器，請安裝適用於 SharePoint 產品之 [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] 增益集的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="096e1-112">For a SharePoint mode report server, install [!INCLUDE[ssSQL11SP1long](../includes/sssql11sp1long-md.md)] or later of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products.</span></span>

 <span data-ttu-id="096e1-113">**若要在 iPad 裝置或 Microsoft Surface 裝置上檢視報表以及與報表互動**</span><span class="sxs-lookup"><span data-stu-id="096e1-113">**To view and interact with a report on an iPad device or Microsoft Surface device**</span></span>

1.  <span data-ttu-id="096e1-114">請確定您可以連接到報表所在的報表伺服器或 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="096e1-114">Make sure that you can connect to the report server or SharePoint site where the report resides.</span></span>

2.  <span data-ttu-id="096e1-115">執行下列其中一項動作來開啟報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-115">Open the report by doing one of the following.</span></span>

    -   <span data-ttu-id="096e1-116">**從電子郵件啟動** ：在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 訂用帳戶所建立的電子郵件中，點選報表的 URL。</span><span class="sxs-lookup"><span data-stu-id="096e1-116">**Start from e-mail:** From an e-mail that is created by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] subscription, tap the URL of the report.</span></span> <span data-ttu-id="096e1-117">報表將在瀏覽器中開啟。</span><span class="sxs-lookup"><span data-stu-id="096e1-117">The report will open in the browser.</span></span>

    -   <span data-ttu-id="096e1-118">**從報表伺服器啟動** ：在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器上瀏覽目錄，然後點選報表名稱開啟報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-118">**Start from Report Server:** Browse the directory on the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server, and then tap the report name to open the report.</span></span>

    -   <span data-ttu-id="096e1-119">**從 SharePoint 文件庫啟動** ：瀏覽至包含 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表的 SharePoint 文件庫，然後點選報表名稱。</span><span class="sxs-lookup"><span data-stu-id="096e1-119">**Start from a SharePoint document library:** Browse to a SharePoint document library that contains [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports, and then tap the report name.</span></span> <span data-ttu-id="096e1-120">您就可以檢視報表並進行互動。</span><span class="sxs-lookup"><span data-stu-id="096e1-120">You can view and interact with the report.</span></span>

        > [!IMPORTANT]
        >  <span data-ttu-id="096e1-121"> 如果是 iPad，請確定 Safari 的 **[私密瀏覽]** 屬性已關閉。</span><span class="sxs-lookup"><span data-stu-id="096e1-121">For the iPad, ensure that the **Private Browsing** property for Safari is turned off.</span></span>

    -   <span data-ttu-id="096e1-122">**SharePoint Web 組件** ：如果 Web 組件已經加入至 SharePoint 頁面，您就可以檢視 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-122">**SharePoint web part:** If the web part has been added to a SharePoint page, you can view [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] reports.</span></span>

3.  <span data-ttu-id="096e1-123">您也可以在您的 Microsoft Surface 裝置上，使用報表管理員來開啟報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-123">On your Microsoft Surface device, you can also open the report by using Report Manager.</span></span> <span data-ttu-id="096e1-124">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表管理員中瀏覽目錄，然後點選報表名稱開啟報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-124">Browse the directory in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager, and then tap the report name to open the report.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="096e1-125">iPad 不支援在報表管理員中檢視報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-125">Viewing reports in Report Manager is not supported on an iPad.</span></span>

4.  <span data-ttu-id="096e1-126">執行下列操作進行捲動和縮放。</span><span class="sxs-lookup"><span data-stu-id="096e1-126">Scroll and zoom by doing the following.</span></span>

    -   <span data-ttu-id="096e1-127">若要捲動報表，請拖曳手指橫過畫面 (上、下、左或右)。</span><span class="sxs-lookup"><span data-stu-id="096e1-127">To scroll the report, drag your finger across the screen (up, down, left or right).</span></span> <span data-ttu-id="096e1-128">這是撥動手勢。</span><span class="sxs-lookup"><span data-stu-id="096e1-128">This is the swipe gesture.</span></span>

    -   <span data-ttu-id="096e1-129">若要放大，請將兩隻手指放在畫面上，然後分開手指。</span><span class="sxs-lookup"><span data-stu-id="096e1-129">To zoom in, place two fingers on the screen and separate the fingers.</span></span> <span data-ttu-id="096e1-130">若要縮小，請將兩隻手指放在畫面上，然後將手指併攏。</span><span class="sxs-lookup"><span data-stu-id="096e1-130">To zoom out, place two fingers on the screen and move the fingers together.</span></span> <span data-ttu-id="096e1-131">這是捏合手勢。</span><span class="sxs-lookup"><span data-stu-id="096e1-131">This is the pinch gesture.</span></span>

5.  <span data-ttu-id="096e1-132">執行下列動作導覽報表以及與報表互動。</span><span class="sxs-lookup"><span data-stu-id="096e1-132">Navigate and interact with the report by doing the following.</span></span>

    -   <span data-ttu-id="096e1-133">藉由點選加號 (+) 摺疊以及減號 (-) 展開的方式，摺疊和展開報表項目，以及與群組相關聯的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="096e1-133">Collapse and expand report items, and rows and columns that are associated with groups, by taping the plus (+) sign to collapse and the minus (-) sign to expand.</span></span>

    -   <span data-ttu-id="096e1-134">藉由點選排序按鈕的方式，在資料表中切換資料列的遞增和遞減順序，或在矩陣中切換資料列及資料行的遞增和遞減順序。</span><span class="sxs-lookup"><span data-stu-id="096e1-134">Toggle between ascending and descending order for rows in a table or for rows and columns in a matrix, by tapping the sort button.</span></span> <span data-ttu-id="096e1-135">排序按鈕通常位於資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="096e1-135">The sort button is usually located in the column header.</span></span>

    -   <span data-ttu-id="096e1-136">藉由點選報表頂端附近的箭頭按鈕，展開和摺疊參數窗格。</span><span class="sxs-lookup"><span data-stu-id="096e1-136">Expand and collapse the parameter pane, by tapping the arrow button near the top of the report.</span></span>

    -   <span data-ttu-id="096e1-137">藉由點選參數旁的方塊或控制項，選取參數值。</span><span class="sxs-lookup"><span data-stu-id="096e1-137">Select a parameter value by tapping the box or control next to the parameter.</span></span> <span data-ttu-id="096e1-138">點選 **[檢視報表]** ，將參數值套用至報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-138">Tap **View Report** to apply the parameter value to the report.</span></span>

    -   <span data-ttu-id="096e1-139">藉由點選 **[尋找]** 旁的方塊、輸入搜尋詞彙，然後點選 **[尋找]** 的方式，搜尋報表內容。</span><span class="sxs-lookup"><span data-stu-id="096e1-139">Search the report content by taping the box next to **Find**, typing a search term, and then taping **Find**.</span></span>

    -   <span data-ttu-id="096e1-140">藉由點選導覽按鈕，或點選按鈕旁的文字方塊並輸入頁碼的方式，導覽報表頁面。</span><span class="sxs-lookup"><span data-stu-id="096e1-140">Navigate the report pages by tapping the navigation buttons, or tapping the text box next to the buttons and typing the page number.</span></span>

    -   <span data-ttu-id="096e1-141">藉由點選已加入報表項目的超連結導覽至 URL，例如文字方塊、影像、圖表和量測計。</span><span class="sxs-lookup"><span data-stu-id="096e1-141">Navigate to URLs by taping hyperlinks that have been added to report items such as text boxes, images, charts, and gauges.</span></span>

    -   <span data-ttu-id="096e1-142">藉由點選 **[匯出下拉式功能表]** 圖示，然後點選檔案格式，匯出報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-142">Export the report by tapping the icon for the **Export drop down menu** and then tapping a file format.</span></span>

        -   <span data-ttu-id="096e1-143">如果您要在 Microsoft Surface 裝置上查看報表，您可以將報表匯出為下列其中一種格式。</span><span class="sxs-lookup"><span data-stu-id="096e1-143">If you're viewing the report on a Microsoft Surface device, you can export the report to one of the following formats.</span></span>

            -   <span data-ttu-id="096e1-144">包含報表資料的 XML 檔</span><span class="sxs-lookup"><span data-stu-id="096e1-144">XML file with report data</span></span>

            -   <span data-ttu-id="096e1-145">CSV (逗號分隔)</span><span class="sxs-lookup"><span data-stu-id="096e1-145">CSV (comma delimited)</span></span>

            -   <span data-ttu-id="096e1-146">PDF</span><span class="sxs-lookup"><span data-stu-id="096e1-146">PDF</span></span>

            -   <span data-ttu-id="096e1-147">MHTML (網頁封存)</span><span class="sxs-lookup"><span data-stu-id="096e1-147">MHTML (web archive)</span></span>

            -   <span data-ttu-id="096e1-148">Excel</span><span class="sxs-lookup"><span data-stu-id="096e1-148">Excel</span></span>

            -   <span data-ttu-id="096e1-149">TIFF</span><span class="sxs-lookup"><span data-stu-id="096e1-149">TIFF</span></span>

            -   <span data-ttu-id="096e1-150">Word</span><span class="sxs-lookup"><span data-stu-id="096e1-150">Word</span></span>

        -   <span data-ttu-id="096e1-151">如果您要在 iPad 上查看報表，您可以將報表匯出為 TIFF 或 PDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="096e1-151">If you're viewing the report on an iPad, you can export the report as a TIFF or PDF file.</span></span>

## <a name="authentication"></a><span data-ttu-id="096e1-152">驗證</span><span class="sxs-lookup"><span data-stu-id="096e1-152">Authentication</span></span>
 <span data-ttu-id="096e1-153">RSWindowsNTLM 驗證和 RSWindowsBasic 驗證可搭配原生模式下的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 和 iPad 一起運作。</span><span class="sxs-lookup"><span data-stu-id="096e1-153">RSWindowsNTLM authentication and RSWindowsBasic authentication work with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in native mode and the iPad.</span></span>

 <span data-ttu-id="096e1-154">一般來說，建議不要在非 https 環境中使用 RSWindowsBasic，因為這種驗證類型不會對傳輸的認證提供機密性。</span><span class="sxs-lookup"><span data-stu-id="096e1-154">In general, it is recommended that RSWindowsBasic is not used in non-https environments because this type of authentication provides no confidentiality for the transmitted credentials.</span></span>

 <span data-ttu-id="096e1-155">如需有關 RSWindowsNTLM 和 RSWindowsBasic 驗證的詳細資訊，請參閱＜ [Authentication with the Report Server](security/authentication-with-the-report-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="096e1-155">For more information about RSWindowsNTLM and RSWindowsBasic authentication, see [Authentication with the Report Server](security/authentication-with-the-report-server.md).</span></span>

## <a name="uploading-reports"></a><span data-ttu-id="096e1-156">上傳報表</span><span class="sxs-lookup"><span data-stu-id="096e1-156">Uploading Reports</span></span>
 <span data-ttu-id="096e1-157">如果您有適當的權限，可透過下列其中一個方法，從 Microsoft Surface 裝置發行報表。</span><span class="sxs-lookup"><span data-stu-id="096e1-157">You can publish reports from a Microsoft Surface device using one of the following methods, if you have the appropriate permissions.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="096e1-158">iPad 不支援這些方法。</span><span class="sxs-lookup"><span data-stu-id="096e1-158">These methods are not supported on the iPad.</span></span>

-   <span data-ttu-id="096e1-159">開啟文件庫並點選 **[上傳文件]**，將報表定義檔案 (.rdl) 上傳至 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="096e1-159">Upload a report definition file (.rdl) to a SharePoint document library by opening the library and tapping **Upload Document**.</span></span>

-   <span data-ttu-id="096e1-160">開啟報表管理員並點選 **[上傳檔案]**，將報表定義檔案上傳至報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="096e1-160">Upload a report definition file to the report server database by opening Report Manager and tapping **Upload File**.</span></span>

## <a name="additional-information"></a><span data-ttu-id="096e1-161">其他資訊</span><span class="sxs-lookup"><span data-stu-id="096e1-161">Additional Information</span></span>
 <span data-ttu-id="096e1-162">如需有關 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 和支援之瀏覽器的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="096e1-162">For more information on [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] and supported browsers, see:</span></span>

-   [<span data-ttu-id="096e1-163">規劃 Reporting Services 和 Power View 瀏覽器支援 &#40;Reporting Services 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="096e1-163">Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;</span></span>](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)

 <span data-ttu-id="096e1-164">如需有關 Microsoft Business Intelligence 和行動裝置的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="096e1-164">For more information on Microsoft Business Intelligence and Mobile devices, see the following:</span></span>

-   <span data-ttu-id="096e1-165">行動[裝置和 SharePoint 2013 (的總覽](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) https://technet.microsoft.com/library/fp161351(v=office.15).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="096e1-165">[Overview of mobile devices and SharePoint 2013](https://technet.microsoft.com/library/fp161351\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161351(v=office.15).aspx).</span></span>

-   <span data-ttu-id="096e1-166">[SharePoint 2013 (中支援的行動裝置瀏覽器](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) https://technet.microsoft.com/library/fp161353(v=office.15).aspx) 。</span><span class="sxs-lookup"><span data-stu-id="096e1-166">[Supported mobile device browsers in SharePoint 2013](https://technet.microsoft.com/library/fp161353\(v=office.15\).aspx) (https://technet.microsoft.com/library/fp161353(v=office.15).aspx).</span></span>

-   <span data-ttu-id="096e1-167">[在 Apple iPad 裝置上查看報表和計分卡 (SharePoint Server 2010) ](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="096e1-167">[Viewing reports and scorecards on Apple iPad devices (SharePoint Server 2010)](https://technet.microsoft.com/library/hh697482.aspx) (https://technet.microsoft.com/library/hh697482.aspx).</span></span>

-   <span data-ttu-id="096e1-168">[在 iPad (video)  (上，觀看 Reporting Services 的報表](https://technet.microsoft.com/sqlserver/jj873792.aspx) https://technet.microsoft.com/sqlserver/jj873792.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="096e1-168">[Viewing Reporting Services Reports on an iPad (video)](https://technet.microsoft.com/sqlserver/jj873792.aspx) (https://technet.microsoft.com/sqlserver/jj873792.aspx).</span></span>

-   [<span data-ttu-id="096e1-169">在 Microsoft Surface RT 裝置上檢視 Reporting Services 報表 (影片)</span><span class="sxs-lookup"><span data-stu-id="096e1-169">Viewing Reporting Services Reports on a Microsoft Surface RT Device (video)</span></span>](https://technet.microsoft.com/sqlserver/dn146017)


