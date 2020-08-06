---
title: 建立及管理 SharePoint 模式報表伺服器的訂用帳戶 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], creating
- subscriptions [Reporting Services], deleting
- subscriptions [Reporting Services], managing
ms.assetid: 44be7ee2-33ce-46e4-9d1a-a20aaf43a227
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0e8798142f2284d1454b42104984424cbe7353a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598735"
---
# <a name="create-and-manage-subscriptions-for-sharepoint-mode-report-servers"></a><span data-ttu-id="894c7-102">建立及管理 SharePoint 模式報表伺服器的訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-102">Create and Manage Subscriptions for SharePoint Mode Report Servers</span></span>
  <span data-ttu-id="894c7-103">您可以建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱，傳遞以 SharePoint 模式報表伺服器整合的 SharePoint Web 應用程式報表。</span><span class="sxs-lookup"><span data-stu-id="894c7-103">You can create [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions to deliver reports from a SharePoint Web application that is integrated with a SharePoint mode report server.</span></span> <span data-ttu-id="894c7-104">訂閱可以將報表傳遞至文件庫、檔案資料夾，或以電子郵件傳送。</span><span class="sxs-lookup"><span data-stu-id="894c7-104">Subscriptions can deliver reports to a document library, file folder, or as e-mail.</span></span> <span data-ttu-id="894c7-105">本主題摘要說明建立 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 訂閱的需求與步驟。</span><span class="sxs-lookup"><span data-stu-id="894c7-105">This topic summarizes the requirements and steps for creating a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscription.</span></span>  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**<br /><br /> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="894c7-106">SharePoint 模式 &#124; SharePoint 2010 和 SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="894c7-106">SharePoint mode &#124; SharePoint 2010 and SharePoint 2013</span></span>|  
  
 <span data-ttu-id="894c7-107">建立訂閱時，有三種方式可以指定其傳遞：</span><span class="sxs-lookup"><span data-stu-id="894c7-107">When you create a subscription, there are three ways to specify its delivery:</span></span>  
  
-   <span data-ttu-id="894c7-108">**文件庫**：您可建立訂閱，以便將以原始報表為基礎的文件傳遞至與原始報表位於相同 SharePoint 網站中文件庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-108">**Document library**: You can create a subscription that delivers a document based on the original report to a library within the same SharePoint site as the original report.</span></span> <span data-ttu-id="894c7-109">您無法將文件傳遞至相同網站集合中另一部伺服器或另一個網站上的程式庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-109">You cannot deliver the document to a library on another server or another site within the same site collection.</span></span> <span data-ttu-id="894c7-110">若要傳遞文件，您必須在報表要傳遞至其中的程式庫上擁有「新增項目」權限。</span><span class="sxs-lookup"><span data-stu-id="894c7-110">To deliver the document, you must have Add Items permission on the library to which the report is delivered.</span></span>  
  
-   <span data-ttu-id="894c7-111">**檔案資料夾：** 您可將以原始報表為基礎的文件傳遞至檔案系統上共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="894c7-111">**File folder:** You can deliver a document based on the original report to a shared folder on the file system.</span></span> <span data-ttu-id="894c7-112">您必須選取可透過網路連接存取的現有資料夾。</span><span class="sxs-lookup"><span data-stu-id="894c7-112">You must select an existing folder that is accessible over a network connection.</span></span>  
  
-   <span data-ttu-id="894c7-113">**電子郵件：** 如果報表伺服器設定為使用報表伺服器電子郵件傳遞延伸模組，即可建立將報表或已匯出報表檔案 (以輸出格式儲存) 傳送至收件匣的訂閱。</span><span class="sxs-lookup"><span data-stu-id="894c7-113">**E-mail:** If the report server is configured to use the Report Server E-mail delivery extension, you can create a subscription that sends a report or an exported report file (saved in an output format) to your in-box.</span></span> <span data-ttu-id="894c7-114">若只要接收通知，但不接收報表或報表 URL，請清除 **[包含這個報表的連結]** 和 **[在訊息內顯示報表]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="894c7-114">To receive just the notification without the report or report URL, clear the **Include a link to this report** and the **Show report inside message** checkboxes.</span></span>  
  
 <span data-ttu-id="894c7-115">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="894c7-115">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="894c7-116">訂閱的一般需求</span><span class="sxs-lookup"><span data-stu-id="894c7-116">General Requirements for Subscriptions</span></span>](#bkmk_subscription_requirements)  
  
-   [<span data-ttu-id="894c7-117">若要建立傳遞報表至 SharePoint 文件庫的訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-117">To create a subscription to deliver a report to a SharePoint library</span></span>](#bkmk_tosharepoint_library)  
  
-   [<span data-ttu-id="894c7-118">若要建立傳遞報表至 SharePoint 文件庫的訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-118">To create a subscription to deliver a report to a SharePoint library</span></span>](#bkmk_tosharepoint_library)  
  
-   [<span data-ttu-id="894c7-119">建立報表伺服器電子郵件傳遞的訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-119">To create a subscription for report server e-mail delivery</span></span>](#bkmk_subscription_for_email)  
  
-   [<span data-ttu-id="894c7-120">檢視或修改訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-120">To view or modify a subscription</span></span>](#bkmk_to_modify_subscription)  
  
-   [<span data-ttu-id="894c7-121">刪除訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-121">To delete a subscription</span></span>](#bkmk_to_delete_subscription)  
  
##  <a name="general-requirements-for-subscriptions"></a><a name="bkmk_subscription_requirements"></a> <span data-ttu-id="894c7-122">訂閱的一般需求</span><span class="sxs-lookup"><span data-stu-id="894c7-122">General Requirements for Subscriptions</span></span>  
 <span data-ttu-id="894c7-123">若要建立訂閱，報表必須使用預存認證，而且您必須具有檢視報表和建立警示的權限。</span><span class="sxs-lookup"><span data-stu-id="894c7-123">To create a subscription, the report must use stored credentials and you must have permission to view the report and create alerts.</span></span>  
  
 <span data-ttu-id="894c7-124">當您建立訂閱時，可以選取輸出檔案格式。</span><span class="sxs-lookup"><span data-stu-id="894c7-124">When you create a subscription, you can select an output file format.</span></span> <span data-ttu-id="894c7-125">並非每份報表都適用於每種格式。</span><span class="sxs-lookup"><span data-stu-id="894c7-125">Not every report works well in every format.</span></span> <span data-ttu-id="894c7-126">在您選取訂閱的格式之前，請開啟報表並將它匯出成不同的格式，以便確認它是否如預期方式顯示。</span><span class="sxs-lookup"><span data-stu-id="894c7-126">Before you select a format in a subscription, open the report and export it to different formats to verify that it appears as expected.</span></span>  
  
 <span data-ttu-id="894c7-127">若要能夠建立 **訂閱，使用者需要 SharePoint 中的** [編輯項目] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 清單權限。</span><span class="sxs-lookup"><span data-stu-id="894c7-127">Users require **Edit Items** list permission in SharePoint if they want to be able to create [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] subscriptions.</span></span> <span data-ttu-id="894c7-128">如需相關資訊，請參閱 [報表伺服器項目的 SharePoint 網站和清單權限參考](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)</span><span class="sxs-lookup"><span data-stu-id="894c7-128">For more information, see [SharePoint Site and List Permission Reference for Report Server Items](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="894c7-129">將報表傳遞至文件庫或共用資料夾的訂閱會建立以原始報表為基礎的新靜態檔案，但是此檔案並非在報表檢視器 Web 組件中執行的真正報表定義。</span><span class="sxs-lookup"><span data-stu-id="894c7-129">A subscription that delivers a report to a library or to a shared folder creates a new, static file that is based on the original report, but it is not a true report definition that runs in the Report Viewer Web Part.</span></span> <span data-ttu-id="894c7-130">如果原始報表具有互動式功能 (例如，鑽研連結) 或動態內容，這些功能將無法在傳遞至目標位置的靜態檔案中使用。</span><span class="sxs-lookup"><span data-stu-id="894c7-130">If the original report has interactive features (such as drillthrough links) or dynamic content, those features will not be available in the static file that is delivered to the target location.</span></span> <span data-ttu-id="894c7-131">如果您選取「網頁」，就可以保留某些互動性，但是因為文件不是在報表檢視器中執行的 .rdl 檔，所以按一下連結報表將會在瀏覽器工作階段中建立新頁面，導致您必須捲動才能回到網站。</span><span class="sxs-lookup"><span data-stu-id="894c7-131">If you select a "Web Page" you can preserve some interactivity, but because the document is not an .rdl file that runs in the Report Viewer, clicking through a report creates new pages in the browser session that you must scroll through to return to the site.</span></span>  
  
 <span data-ttu-id="894c7-132">您無法將匯出之報表的副檔名重新命名為 .rdl，並讓它在報表檢視器 Web 組件中執行。</span><span class="sxs-lookup"><span data-stu-id="894c7-132">You cannot rename the file name extension of an exported report to .rdl and have it run in the Report Viewer Web Part.</span></span> <span data-ttu-id="894c7-133">如果您想要建立可提供實際報表的訂閱，請使用報表伺服器電子郵件傳遞延伸模組並將選項設定為包含報表的連結。</span><span class="sxs-lookup"><span data-stu-id="894c7-133">If you want to create a subscription that provides an actual report, use the Report Server E-mail delivery extension and set options to include a link to the report.</span></span>  
  
 <span data-ttu-id="894c7-134">包含傳遞文件之文件庫的版本設定會決定每次傳遞該文件時是否會建立新的版本。</span><span class="sxs-lookup"><span data-stu-id="894c7-134">Version settings on the library that contains the delivered document determine whether a new version of the document is created with each delivery.</span></span> <span data-ttu-id="894c7-135">依預設，每個文件庫都會啟用版本設定。</span><span class="sxs-lookup"><span data-stu-id="894c7-135">By default, version settings are enabled for each library.</span></span> <span data-ttu-id="894c7-136">除非您明確選擇 **[無版本設定]** ，否則只要一傳遞就會建立文件新的主要版本。</span><span class="sxs-lookup"><span data-stu-id="894c7-136">Unless you specifically choose **No versioning**, a new major version of the document will be created upon delivery.</span></span> <span data-ttu-id="894c7-137">訂閱傳遞的結果只會建立文件的主要版本，絕不會建立次要版本，即使所選取的版本設定選項允許次要版本。</span><span class="sxs-lookup"><span data-stu-id="894c7-137">Only major versions of the document are created; minor versions are never created as a result of subscription delivery, even if you select a versioning option that allows minor versions.</span></span> <span data-ttu-id="894c7-138">如果限制要保留的主要版本數目，則在達到上限時，新傳遞項目將會取代舊傳遞項目。</span><span class="sxs-lookup"><span data-stu-id="894c7-138">If you limit the number of major versions that are retained, older deliveries will be replaced by newer ones when the maximum limit is reached.</span></span>  
  
 <span data-ttu-id="894c7-139">您針對訂閱所選取的輸出格式會以報表伺服器上安裝的轉譯延伸模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="894c7-139">Output formats that you select for a subscription are based on rendering extensions that are installed on the report server.</span></span> <span data-ttu-id="894c7-140">您只能選取報表伺服器之轉譯延伸模組所支援的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="894c7-140">You can only select output formats that are supported by the rendering extensions on the report server.</span></span>  
  
###  <a name="to-create-a-subscription-to-deliver-a-report-to-a-sharepoint-library"></a><a name="bkmk_tosharepoint_library"></a> <span data-ttu-id="894c7-141">若要建立傳遞報表至 SharePoint 文件庫的訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-141">To create a subscription to deliver a report to a SharePoint library</span></span>  
  
1.  <span data-ttu-id="894c7-142">瀏覽至包含報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-142">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="894c7-143">按一下報表旁的向下箭頭，然後選取 **[管理訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-143">Click the down arrow next to the report and then select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="894c7-144">按一下 [ **加入訂閱**]。</span><span class="sxs-lookup"><span data-stu-id="894c7-144">Click **Add Subscription**.</span></span>  
  
4.  <span data-ttu-id="894c7-145">在 **[傳遞延伸模組]** 中，選取 **[SharePoint 文件庫]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-145">In **Delivery Extension**, select **SharePoint Document Library**.</span></span>  
  
5.  <span data-ttu-id="894c7-146">在 **[文件庫]** 中，選取相同網站內的文件庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-146">In **Document Library**, select a library within the same site.</span></span>  
  
6.  <span data-ttu-id="894c7-147">在 **[檔案選項]** 中，指定訂閱將建立之文件的檔案名稱和標題。</span><span class="sxs-lookup"><span data-stu-id="894c7-147">In **File Options**, specify the file name and title for the document that will be created by the subscription.</span></span>  
  
7.  <span data-ttu-id="894c7-148">在 **[輸出格式]** 中，選取應用程式格式。</span><span class="sxs-lookup"><span data-stu-id="894c7-148">In **Output Format**, select the application format.</span></span>  
  
     <span data-ttu-id="894c7-149">網頁封存 (MHTML) 是預設值，因為它會產生獨立的 HTML 檔案，但是它將不會保留原始報表中可能存在的互動式報表功能。</span><span class="sxs-lookup"><span data-stu-id="894c7-149">Web archive (MHTML) is the default because it produces a self-contained HTML file, but it will not preserve interactive report features that might be in the original report.</span></span>  
  
8.  <span data-ttu-id="894c7-150">在 **[覆寫選項]** 中，指定可決定後續傳遞項目是否會覆寫檔案的選項。</span><span class="sxs-lookup"><span data-stu-id="894c7-150">In **Overwrite Options**, specify an option that determines whether subsequent deliveries overwrite a file.</span></span> <span data-ttu-id="894c7-151">如果您要保留之前的傳遞項目，可以選取 **[使用唯一的名稱建立檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-151">If you want to preserve previous deliveries, you can select **Create a file with a unique name**.</span></span> <span data-ttu-id="894c7-152">如此就會將數字附加至新的檔案，以便建立唯一的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="894c7-152">A number will be appended to new files to create a unique file name.</span></span>  
  
9. <span data-ttu-id="894c7-153">在 **[傳遞事件]** 中，指定導致訂閱執行的排程或事件。</span><span class="sxs-lookup"><span data-stu-id="894c7-153">In **Delivery Event**, specify a schedule or event that causes the subscription to run.</span></span> <span data-ttu-id="894c7-154">每當使用快照集資料執行之報表的資料重新整理時，您就可以建立自訂排程、選取共用排程 (如果可用的話) 或執行訂閱。</span><span class="sxs-lookup"><span data-stu-id="894c7-154">You can create a custom schedule, select a shared schedule if one is available, or run the subscription whenever the data is refreshed for a report that runs with snapshot data.</span></span> <span data-ttu-id="894c7-155">如需排程和資料處理的詳細資訊，請參閱[設定處理選項 &#40;SharePoint 整合模式的 Reporting Services&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="894c7-155">For more information about schedules and data processing, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
10. <span data-ttu-id="894c7-156">在 **[參數]** 中，如果您要建立參數化報表的訂閱，請指定您想要在處理訂閱時搭配報表使用的值。</span><span class="sxs-lookup"><span data-stu-id="894c7-156">In **Parameters**, if you are creating a subscription to a parameterized report, specify the values that you want to use with the report when the subscription is processed.</span></span> <span data-ttu-id="894c7-157">如果您選取的報表不包含參數，表示在此頁面上看不到報表區段。</span><span class="sxs-lookup"><span data-stu-id="894c7-157">The parameters section is not visible on this page if the report you select does not contain parameters.</span></span> <span data-ttu-id="894c7-158">如需參數的詳細資訊，請參閱[在已發行的報表上設定參數 &#40;SharePoint 整合模式的 Reporting Services&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="894c7-158">For more information about parameters, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
###  <a name="to-create-a-subscription-for-shared-folder-delivery"></a><a name="bkmk_subscription_for_sharedfolder"></a> <span data-ttu-id="894c7-159">若要建立共用資料夾傳遞的訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-159">To create a subscription for shared folder delivery</span></span>  
  
1.  <span data-ttu-id="894c7-160">瀏覽至包含報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-160">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="894c7-161">按一下報表旁的向下箭頭，然後選取 **[管理訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-161">Click the down arrow next to the report and then select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="894c7-162">按一下 [ **加入訂閱**]。</span><span class="sxs-lookup"><span data-stu-id="894c7-162">Click **Add Subscription**.</span></span>  
  
4.  <span data-ttu-id="894c7-163">在 **[傳遞延伸模組]** 中，選取 **[Windows 檔案共用]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-163">In **Delivery Extension**, select **Windows File Share**.</span></span>  
  
5.  <span data-ttu-id="894c7-164">在 **[檔案名稱]** 中，輸入將在共用資料夾中建立之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="894c7-164">In **File Name**, enter the name of the file that will be created in the shared folder.</span></span>  
  
6.  <span data-ttu-id="894c7-165">在 [路徑]  中，以統一命名慣例 (UNC) 格式輸入包含電腦網路名稱的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="894c7-165">In **Path**, enter a folder path in Uniform Naming Convention (UNC) format that includes the computer's network name.</span></span> <span data-ttu-id="894c7-166">資料夾路徑中不要包含尾端的反斜線。</span><span class="sxs-lookup"><span data-stu-id="894c7-166">Do not include trailing backslashes in the folder path.</span></span> <span data-ttu-id="894c7-167">範例路徑可能是 `\\ComputerName01\Public\MyReports`，其中 Public 和 MyReports 都是共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="894c7-167">An example path might be `\\ComputerName01\Public\MyReports`, where Public and MyReports are shared folders.</span></span>  
  
7.  <span data-ttu-id="894c7-168">在 **[轉譯格式]** 中，選取報表的應用程式格式。</span><span class="sxs-lookup"><span data-stu-id="894c7-168">In **Render Format**, select the application format for the report.</span></span>  
  
8.  <span data-ttu-id="894c7-169">在 **[寫入模式]** 中，選擇 **[無]** 、 **[自動遞增]** 或 **[覆寫]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-169">In **Write Mode**, choose between **None**, **Autoincrement**, or **Overwrite**.</span></span> <span data-ttu-id="894c7-170">這些選項會決定後續傳遞項目是否會覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="894c7-170">These options determine whether subsequent deliveries overwrite a file.</span></span> <span data-ttu-id="894c7-171">如果要保留之前的傳遞項目，可以選擇 **[自動遞增]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-171">If you want to preserve previous deliveries, you can choose **Autoincrement**.</span></span> <span data-ttu-id="894c7-172">如此就會將數字附加至新的檔案，以便建立唯一的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="894c7-172">A number will be appended to new files to create a unique file name.</span></span> <span data-ttu-id="894c7-173">如果選擇 **[無]** ，而且目標位置中已存在相同名稱的檔案，就不會進行任何傳遞。</span><span class="sxs-lookup"><span data-stu-id="894c7-173">If you choose **None**, no delivery will occur if a file of the same name already exists in the target location.</span></span>  
  
9. <span data-ttu-id="894c7-174">在 **[副檔名]** 中，選擇 **[True]** 加入對應至應用程式檔案格式的副檔名，或 [False] 建立不含副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="894c7-174">In **File Extension**, choose **True** to add a file name extension that corresponds to the application file format, or False to create the file without an extension.</span></span>  
  
10. <span data-ttu-id="894c7-175">在 **[使用者名稱]** 和 **[密碼]** 中，輸入在共用資料夾上具有寫入權限的認證。</span><span class="sxs-lookup"><span data-stu-id="894c7-175">In **User Name** and **Password**, enter credentials that have write permissions on the shared folder.</span></span>  
  
11. <span data-ttu-id="894c7-176">在 **[傳遞事件]** 中，指定導致訂閱執行的排程或事件。</span><span class="sxs-lookup"><span data-stu-id="894c7-176">In **Delivery Event**, specify a schedule or event that causes the subscription to run.</span></span> <span data-ttu-id="894c7-177">每當使用快照集資料執行之報表的資料重新整理時，您就可以建立自訂排程、選取共用排程 (如果可用的話) 或執行訂閱。</span><span class="sxs-lookup"><span data-stu-id="894c7-177">You can create a custom schedule, select a shared schedule if one is available, or run the subscription whenever the data is refreshed for a report that runs with snapshot data.</span></span> <span data-ttu-id="894c7-178">如需排程和資料處理的詳細資訊，請參閱[設定處理選項 &#40;SharePoint 整合模式的 Reporting Services&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="894c7-178">For more information about schedules and data processing, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
12. <span data-ttu-id="894c7-179">在 **[參數]** 中，如果您要建立參數化報表的訂閱，請指定您想要在處理訂閱時搭配報表使用的值。</span><span class="sxs-lookup"><span data-stu-id="894c7-179">In **Parameters**, if you are creating a subscription to a parameterized report, specify the values that you want to use with the report when the subscription is processed.</span></span> <span data-ttu-id="894c7-180">如需參數的詳細資訊，請參閱[在已發行的報表上設定參數 &#40;SharePoint 整合模式的 Reporting Services&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="894c7-180">For more information about parameters, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
###  <a name="to-create-a-subscription-for-report-server-e-mail-delivery"></a><a name="bkmk_subscription_for_email"></a> <span data-ttu-id="894c7-181">建立報表伺服器電子郵件傳遞的訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-181">To create a subscription for report server e-mail delivery</span></span>  
  
1.  <span data-ttu-id="894c7-182">瀏覽至包含報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-182">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="894c7-183">按一下報表旁的向下箭頭，然後選取 **[管理訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-183">Click the down arrow next to the report and then select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="894c7-184">按一下 [ **加入訂閱**]。</span><span class="sxs-lookup"><span data-stu-id="894c7-184">Click **Add Subscription**.</span></span>  
  
4.  <span data-ttu-id="894c7-185">在 [傳遞延伸模組]  中，選取 [電子郵件]  。</span><span class="sxs-lookup"><span data-stu-id="894c7-185">In **Delivery Extension**, select **E-mail**.</span></span>  
  
5.  <span data-ttu-id="894c7-186">在 [傳遞選項]  中，指定要將報表傳送至其中的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="894c7-186">In **Delivery options**, specify an e-mail address to send the report to.</span></span>  
  
6.  <span data-ttu-id="894c7-187">或者，您可以修改 [主旨] 行。</span><span class="sxs-lookup"><span data-stu-id="894c7-187">Optionally, you can modify the Subject line.</span></span> <span data-ttu-id="894c7-188">[主旨] 行會使用內建參數，以便擷取報表名稱和處理報表的時間。</span><span class="sxs-lookup"><span data-stu-id="894c7-188">The Subject line uses built-in parameters that capture the report name and time when it was processed.</span></span> <span data-ttu-id="894c7-189">這些參數是唯一可用的內建參數。</span><span class="sxs-lookup"><span data-stu-id="894c7-189">These are the only built-in parameters that can be used.</span></span> <span data-ttu-id="894c7-190">雖然這些參數是可自訂 [主旨] 行中顯示之文字的預留位置，但是您可以將它取代成靜態文字。</span><span class="sxs-lookup"><span data-stu-id="894c7-190">The parameters are placeholders that customize the text that appears in the Subject line, but you can replace it with static text.</span></span>  
  
7.  <span data-ttu-id="894c7-191">如果要在訊息主體中內嵌報表 URL，請選擇 **[包含這個報表的連結]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-191">Choose **Include a link to this report** if you want to embed a report URL in the body of the message.</span></span>  
  
8.  <span data-ttu-id="894c7-192">在 **[報表內容]** 中，指定您是否想要在訊息主體中內嵌實際的報表。</span><span class="sxs-lookup"><span data-stu-id="894c7-192">In **Report Contents**, specify whether you want to embed the actual report in the body of the message.</span></span>  
  
     <span data-ttu-id="894c7-193">轉譯格式和瀏覽器會決定是否要內嵌或附加報表。</span><span class="sxs-lookup"><span data-stu-id="894c7-193">The rendering format and browser determine whether the report is embedded or attached.</span></span> <span data-ttu-id="894c7-194">如果您的瀏覽器支援 HTML 4.0 與 MHTML，而且您選取網頁封存轉譯格式，則報表會內嵌為訊息的一部分。</span><span class="sxs-lookup"><span data-stu-id="894c7-194">If your browser supports HTML 4.0 and MHTML, and you select the Web archive rendering format, the report is embedded as part of the message.</span></span> <span data-ttu-id="894c7-195">所有其他轉譯格式 (CSV、PDF 等等) 均以附加檔案傳遞報表。</span><span class="sxs-lookup"><span data-stu-id="894c7-195">All other rendering formats (CSV, PDF, and so on) deliver reports as attachments.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="894c7-196">在傳送報表之前，不會檢查附加檔案或訊息的大小。</span><span class="sxs-lookup"><span data-stu-id="894c7-196">does not check the size of the attachment or message before sending the report.</span></span> <span data-ttu-id="894c7-197">如果附加檔案或訊息超過郵件伺服器所允許的上限，將不會傳遞報表。</span><span class="sxs-lookup"><span data-stu-id="894c7-197">If the attachment or message exceeds the maximum limit allowed by your mail server, the report will not be delivered.</span></span> <span data-ttu-id="894c7-198">如果是大型報表，請選擇其中一個傳遞選項 (例如 URL 或通知)。</span><span class="sxs-lookup"><span data-stu-id="894c7-198">Choose one of the other delivery options (such as URL or notification) for large reports.</span></span>  
  
9. <span data-ttu-id="894c7-199">在 **[傳遞事件]** 中，指定導致訂閱執行的排程或事件。</span><span class="sxs-lookup"><span data-stu-id="894c7-199">In **Delivery Event**, specify a schedule or event that causes the subscription to run.</span></span> <span data-ttu-id="894c7-200">每當使用快照集資料執行之報表的資料重新整理時，您就可以建立自訂排程、選取共用排程 (如果可用的話) 或執行訂閱。</span><span class="sxs-lookup"><span data-stu-id="894c7-200">You can create a custom schedule, select a shared schedule if one is available, or run the subscription whenever the data is refreshed for a report that runs with snapshot data.</span></span> <span data-ttu-id="894c7-201">如需排程和資料處理的詳細資訊，請參閱[設定處理選項 &#40;SharePoint 整合模式的 Reporting Services&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="894c7-201">For more information about schedules and data processing, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
10. <span data-ttu-id="894c7-202">在 **[參數]** 中，如果您要建立參數化報表的訂閱，請指定您想要在處理訂閱時搭配報表使用的值。</span><span class="sxs-lookup"><span data-stu-id="894c7-202">In **Parameters**, if you are creating a subscription to a parameterized report, specify the values that you want to use with the report when the subscription is processed.</span></span> <span data-ttu-id="894c7-203">如需參數的詳細資訊，請參閱[在已發行的報表上設定參數 &#40;SharePoint 整合模式的 Reporting Services&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="894c7-203">For more information about parameters, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
###  <a name="to-view-or-modify-a-subscription"></a><a name="bkmk_to_modify_subscription"></a> <span data-ttu-id="894c7-204">檢視或修改訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-204">To view or modify a subscription</span></span>  
  
1.  <span data-ttu-id="894c7-205">瀏覽至包含報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-205">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="894c7-206">按一下報表旁的向下箭頭，然後按一下 **[管理訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-206">Click the down arrow next to the report and then click **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="894c7-207">每個訂閱都可由傳遞類型加以識別。</span><span class="sxs-lookup"><span data-stu-id="894c7-207">Each subscription is identified by the type of delivery.</span></span> <span data-ttu-id="894c7-208">按一下訂閱類型，即可檢視並變更現有的屬性。</span><span class="sxs-lookup"><span data-stu-id="894c7-208">Click the subscription type to view and change the existing properties.</span></span>  
  
###  <a name="to-delete-a-subscription"></a><a name="bkmk_to_delete_subscription"></a> <span data-ttu-id="894c7-209">刪除訂閱</span><span class="sxs-lookup"><span data-stu-id="894c7-209">To delete a subscription</span></span>  
  
1.  <span data-ttu-id="894c7-210">瀏覽至包含報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="894c7-210">Browse to a SharePoint library that contains your report.</span></span>  
  
2.  <span data-ttu-id="894c7-211">按一下報表旁的向下箭頭，然後按一下 **[管理訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-211">Click the down arrow next to the report and then click **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="894c7-212">按一下訂閱旁的核取方塊，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="894c7-212">Click the checkbox next to the subscription, and click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894c7-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="894c7-213">See Also</span></span>  
 <span data-ttu-id="894c7-214">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="894c7-214">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="894c7-215">[Reporting Services 中的電子郵件傳遞](e-mail-delivery-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="894c7-215">[E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md) </span></span>  
 <span data-ttu-id="894c7-216">[Reporting Services 中的檔案共用傳遞](file-share-delivery-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="894c7-216">[File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) </span></span>  
 <span data-ttu-id="894c7-217">[Reporting Services 中的 SharePoint 文件庫傳遞](sharepoint-library-delivery-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="894c7-217">[SharePoint Library Delivery in Reporting Services](sharepoint-library-delivery-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="894c7-218">針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;</span><span class="sxs-lookup"><span data-stu-id="894c7-218">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)  
  
  
