---
title: 在原生模式中建立、修改和刪除標準訂閱 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- standard subscriptions [Reporting Services]
- subscriptions [Reporting Services], standard
ms.assetid: 5ab1c661-9bfa-434a-b315-faac34ed12b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 035462f53e91a0ac29c756f8fcfdef7ad65cb984
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593799"
---
# <a name="create-modify-and-delete-standard-subscriptions-reporting-services-in-native-mode"></a><span data-ttu-id="606a7-102">Create, Modify, and Delete Standard Subscriptions (Reporting Services in Native Mode)</span><span class="sxs-lookup"><span data-stu-id="606a7-102">Create, Modify, and Delete Standard Subscriptions (Reporting Services in Native Mode)</span></span>
  <span data-ttu-id="606a7-103">標準訂閱是希望能透過電子郵件傳遞報表，或傳遞到共用資料夾之個別使用者所建立的訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-103">A standard subscription is one that is created by individual users who want to have a report delivered through e-mail or to a shared folder.</span></span> <span data-ttu-id="606a7-104">標準訂閱一律是透過它所依據的報表定義。</span><span class="sxs-lookup"><span data-stu-id="606a7-104">A standard subscription is always defined through the report on which it is based.</span></span>  
  
 <span data-ttu-id="606a7-105">建立訂閱的使用者便擁有該訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-105">A user who creates a subscription owns that subscription.</span></span> <span data-ttu-id="606a7-106">每一個使用者都可以修改或刪除自己所擁有的訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-106">Each user can modify or delete the subscriptions that he or she owns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="606a7-107">從 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 開始，您可以用程式設計的方式傳送訂閱的擁有權。</span><span class="sxs-lookup"><span data-stu-id="606a7-107">Starting with [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] you can transfer the ownership of a subscription programmatically.</span></span> <span data-ttu-id="606a7-108">沒有任何使用者介面可以用來傳送訂閱的擁有權。</span><span class="sxs-lookup"><span data-stu-id="606a7-108">There is no user interface you can use to transfer ownership of subscriptions.</span></span> <span data-ttu-id="606a7-109">如需詳細資訊，請參閱＜<xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>＞</span><span class="sxs-lookup"><span data-stu-id="606a7-109">For more information, see <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>  
  
 <span data-ttu-id="606a7-110">視**RSReportServer.config**的設定檔設定而定，使用者可能可以將更多使用者新增至訂用帳戶 (例如，管理員會新增其直屬員工的電子郵件地址，讓他們各自收到一份報表) 的複本。</span><span class="sxs-lookup"><span data-stu-id="606a7-110">Depending on **RSReportServer.config** configuration file settings, users may be able to add more users to a subscription (for example, a manager adds the e-mail addresses of his or her direct reports so that they each receive a copy of the report).</span></span> <span data-ttu-id="606a7-111">是否支援此功能取決於在定義個別訂閱時，[收件者:] 欄位是否為可見的。</span><span class="sxs-lookup"><span data-stu-id="606a7-111">Whether this is supported depends on whether the To: field is visible when defining individual subscriptions.</span></span> <span data-ttu-id="606a7-112">如需詳細資訊，請參閱[為電子郵件傳遞設定報表伺服器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="606a7-112">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="606a7-113">此主題提供有關由個別使用者建立或管理的標準訂閱資訊。</span><span class="sxs-lookup"><span data-stu-id="606a7-113">This topic provides information about standard subscriptions that are created and managed by individual users.</span></span> <span data-ttu-id="606a7-114">資料驅動訂閱有不同的需求和步驟，且會在另一個主題中討論。</span><span class="sxs-lookup"><span data-stu-id="606a7-114">Data-driven subscriptions have different requirements and steps, and are discussed in a separate topic.</span></span> <span data-ttu-id="606a7-115">如需詳細資訊，請參閱[建立、修改和刪除資料驅動訂閱](data-driven-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="606a7-115">For more information, see [Create, Modify, and Delete a Data-Driven Subscription](data-driven-subscriptions.md).</span></span>  
  
 <span data-ttu-id="606a7-116">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="606a7-116">In this topic:</span></span>  
  
-   [<span data-ttu-id="606a7-117">若要建立訂閱</span><span class="sxs-lookup"><span data-stu-id="606a7-117">To Create a Subscription</span></span>](#bkmk_create_subscription)  
  
-   [<span data-ttu-id="606a7-118">若要建立檔案共用訂閱</span><span class="sxs-lookup"><span data-stu-id="606a7-118">To Create a File Share Subscription</span></span>](#bkmk_create_fileshare_subscription)  
  
-   [<span data-ttu-id="606a7-119">若要建立電子郵件訂閱</span><span class="sxs-lookup"><span data-stu-id="606a7-119">To Create an E-mail Subscription</span></span>](#bkmk_create_email_subscription)  
  
-   [<span data-ttu-id="606a7-120">若要修改訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="606a7-120">To Modify a Subscription</span></span>](#bkmk_modify_subscription)  
  
-   [<span data-ttu-id="606a7-121">若要刪除訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="606a7-121">To Delete a Subscription</span></span>](#bkmk_delete_subscription)  
  
##  <a name="to-create-a-subscription"></a><a name="bkmk_create_subscription"></a><span data-ttu-id="606a7-122">若要建立訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="606a7-122">To Create a Subscription</span></span>  
 <span data-ttu-id="606a7-123">若要建立訂閱，請選擇適用於報表伺服器部署的工具和方法：</span><span class="sxs-lookup"><span data-stu-id="606a7-123">To create a subscription, choose the tool and approach that is valid for your report server deployment:</span></span>  
  
-   <span data-ttu-id="606a7-124">本主題的內容描述如何使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表管理員在原生模式報表伺服器上建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-124">The content in this topic explains how to create subscriptions on a native mode report server using [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Report Manager.</span></span> <span data-ttu-id="606a7-125">定義了訂閱之後，您可以在報表管理員中，透過特定報表的 [我的訂閱] 頁面或 **[訂閱]** 索引標籤存取訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-125">After you define a subscription, you can access it in Report Manager through the My Subscriptions page or the **Subscriptions** tab of a specific report.</span></span>  
  
-   <span data-ttu-id="606a7-126">[建立及管理 Sharepoint 模式報表伺服器的訂閱](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md)說明如何使用 sharepoint 網站中的應用程式頁面，訂閱以 sharepoint 整合模式執行之報表伺服器上的報表。</span><span class="sxs-lookup"><span data-stu-id="606a7-126">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) explains how to use the application pages in a SharePoint site to subscribe to reports on a report server that runs in SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="606a7-127">此主題提供建立電子郵件訂閱與檔案共用傳遞訂閱的指示。</span><span class="sxs-lookup"><span data-stu-id="606a7-127">This topic provides instructions for creating an e-mail subscription and a file share delivery subscription.</span></span>  
  
-   <span data-ttu-id="606a7-128">若要使用電子郵件傳遞，您必須先針對 SMTP 伺服器或閘道連接設定報表伺服器，才可以建立訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-128">To use e-mail delivery, the report server must be configured for an SMTP server or gateway connection before you create the subscription.</span></span>  
  
-   <span data-ttu-id="606a7-129">若要使用檔案共用傳遞，您必須已經定義目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="606a7-129">To use file share delivery, you must have target folder already defined.</span></span> <span data-ttu-id="606a7-130">如需詳細資訊，請參閱[為電子郵件傳遞設定報表伺服器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="606a7-130">For more information, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="606a7-131">報表資料來源必須設定為使用預存認證或不使用認證，然後才能訂閱報表。</span><span class="sxs-lookup"><span data-stu-id="606a7-131">Before you can subscribe to a report, the report data source must be configured to use stored credentials or no credentials.</span></span> <span data-ttu-id="606a7-132">如需詳細資訊，請參閱 [在 Reporting Services 資料來源中儲存認證](../report-data/store-credentials-in-a-reporting-services-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="606a7-132">For more information, see [Store Credentials in a Reporting Services Data Source](../report-data/store-credentials-in-a-reporting-services-data-source.md).</span></span> <span data-ttu-id="606a7-133">否則的話， **[新增訂閱]** 按鈕便無法使用。</span><span class="sxs-lookup"><span data-stu-id="606a7-133">If it does not, the **New Subscription** button is not available.</span></span>  
  
 <span data-ttu-id="606a7-134">本主題並未說明如何建立資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-134">This topic does not explain how to create a data-driven subscription.</span></span> <span data-ttu-id="606a7-135">如需如何建立資料驅動訂閱的指示，請參閱[建立資料驅動訂閱 &#40;SSRS 教學課程&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) 或報表管理員中 [建立資料驅動訂閱] 頁面的線上說明。</span><span class="sxs-lookup"><span data-stu-id="606a7-135">For instructions on how to create a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md) or the online help for the Create a Data-driven Subscription page in Report Manager.</span></span>  
  
###  <a name="to-create-a-file-share-subscription"></a><a name="bkmk_create_fileshare_subscription"></a><span data-ttu-id="606a7-136">若要建立檔案共用訂閱</span><span class="sxs-lookup"><span data-stu-id="606a7-136">To Create a File Share Subscription</span></span>  
  
1.  <span data-ttu-id="606a7-137">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="606a7-137">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="606a7-138">在報表管理員的 **[內容]** 頁面上，瀏覽至您要訂閱的報表。</span><span class="sxs-lookup"><span data-stu-id="606a7-138">In Report Manager, on the **Contents** page, navigate to the report you want to subscribe to.</span></span> <span data-ttu-id="606a7-139">按一下報表以開啟它。</span><span class="sxs-lookup"><span data-stu-id="606a7-139">Click the report to open it.</span></span>  
  
3.  <span data-ttu-id="606a7-140">按一下 **[訂閱]** 索引標籤，然後按一下 **[新增訂閱]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-140">Click the **Subscriptions** tab, and then click **New Subscription**.</span></span>  
  
4.  <span data-ttu-id="606a7-141">在 **[傳遞者]** 中，選取 **[Windows 檔案共用]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-141">In **Delivered by**, select **Windows File Share**.</span></span>  
  
5.  <span data-ttu-id="606a7-142">在 **[檔案名稱]** 中，輸入報表的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="606a7-142">In **File Name**, type a file name for the report.</span></span>  
  
6.  <span data-ttu-id="606a7-143">選取 **[建立檔案時加入副檔名]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-143">Select **Add a file extension when the file is created**.</span></span> <span data-ttu-id="606a7-144">這個選項會將三個字元的副檔名加入至檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="606a7-144">This option adds a three-character file extension to the file name.</span></span> <span data-ttu-id="606a7-145">副檔名是由您選取的報表輸出格式所決定。</span><span class="sxs-lookup"><span data-stu-id="606a7-145">The file extension is determined by the report output format you select.</span></span>  
  
7.  <span data-ttu-id="606a7-146">在 [**路徑**] 文字方塊中，輸入您要傳遞 (報表之現有資料夾的通用命名慣例 (UNC) 路徑，例如 \\ \\<servername \> \\<myreports 都 \>) 。</span><span class="sxs-lookup"><span data-stu-id="606a7-146">In the **Path** text box, type a Universal Naming Convention (UNC) path to an existing folder where you want to deliver the reports (for example, \\\\<servername\>\\<myreports\>).</span></span> <span data-ttu-id="606a7-147">在路徑的開頭包含雙反斜線字元。</span><span class="sxs-lookup"><span data-stu-id="606a7-147">Include double backslash characters at the beginning of the path.</span></span> <span data-ttu-id="606a7-148">請勿在尾端指定反斜線。</span><span class="sxs-lookup"><span data-stu-id="606a7-148">Do not specify a trailing backslash.</span></span>  
  
8.  <span data-ttu-id="606a7-149">在 [轉譯格式] 中，選取檔案傳遞的報表輸出格式。</span><span class="sxs-lookup"><span data-stu-id="606a7-149">In Render Format, select a report output format for file delivery.</span></span> <span data-ttu-id="606a7-150">選擇對應至將用於開啟報表之桌面應用程式的格式。</span><span class="sxs-lookup"><span data-stu-id="606a7-150">Choose a format that corresponds to the desktop application that will be used to open the report.</span></span> <span data-ttu-id="606a7-151">請避免使用無法在單一資料流完成報表轉譯的格式，或者會導入靜態檔案無法支援之互動性的格式 (例如 HTML 4.0)。</span><span class="sxs-lookup"><span data-stu-id="606a7-151">Avoid formats that do not render a report in a single stream or that introduce interactivity that cannot be supported in a static file (for example, HTML 4.0).</span></span>  
  
9. <span data-ttu-id="606a7-152">在 [**使用者名稱**] 和 [**密碼**] 文字方塊中，使用 *\<domain>* \\ 使用者名稱的格式，指定存取檔案共用所需的認證 *\<user name>* 。</span><span class="sxs-lookup"><span data-stu-id="606a7-152">In the **User name** and **Password** text boxes, specify the credentials required to access the file share, using the format *\<domain>*\\*\<user name>* for the user name.</span></span>  
  
10. <span data-ttu-id="606a7-153">指定覆寫選項。</span><span class="sxs-lookup"><span data-stu-id="606a7-153">Specify overwrite options.</span></span> <span data-ttu-id="606a7-154">如果您按一下 **[如果舊版存在，不要覆寫檔案]**，則若是偵測到現有的檔案，將不會傳遞。</span><span class="sxs-lookup"><span data-stu-id="606a7-154">If you click **Do not overwrite the file if a previous version exists**, the delivery will not occur if an existing file is detected.</span></span> <span data-ttu-id="606a7-155">如果您按一下 **[加入較新版本時，遞增檔案名稱]**，報表伺服器就會在檔案名稱後面附加一個數字，以便與相同名稱的現有檔案區別。</span><span class="sxs-lookup"><span data-stu-id="606a7-155">If you click **Increment file names as newer versions are added**, the report server appends a number to the file name to distinguish it from existing files of the same name.</span></span>  
  
11. <span data-ttu-id="606a7-156">指定您要傳遞報表的時機：</span><span class="sxs-lookup"><span data-stu-id="606a7-156">Specify when you want the report delivered:</span></span>  
  
    -   <span data-ttu-id="606a7-157">若要排程傳遞時間，請按一下 **[排程報表執行完成時]** ，然後按一下 **[選取排程]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="606a7-157">To schedule a delivery time, click **When the scheduled report run is complete** and click the **Select Schedule** button.</span></span> <span data-ttu-id="606a7-158">就會開啟排程頁面。</span><span class="sxs-lookup"><span data-stu-id="606a7-158">A schedule page opens.</span></span>  
  
    -   <span data-ttu-id="606a7-159">若要選取預先定義的共用排程，其中已經具有您想要使用的日期、時間和循環資訊，請按一下 **[在共用排程上]**，然後選取要用的排程。</span><span class="sxs-lookup"><span data-stu-id="606a7-159">To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.</span></span>  
  
    -   <span data-ttu-id="606a7-160">若要在以更新的版本更新報表快照集時傳遞報表，請按一下 [重新整理報表內容時]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="606a7-160">To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**.</span></span> <span data-ttu-id="606a7-161">如果您要訂閱以排程間隔擷取資料的報表，用來重新整理資料的排程就會決定處理訂閱的時間。</span><span class="sxs-lookup"><span data-stu-id="606a7-161">If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="606a7-162">只有當快照集已經和更新排程相關聯時可使用此選項。</span><span class="sxs-lookup"><span data-stu-id="606a7-162">This option is available only for snapshots that are already associated with an update schedule.</span></span>  
  
12. <span data-ttu-id="606a7-163">如果是參數化報表，請指定要用於此訂閱之報表的參數。</span><span class="sxs-lookup"><span data-stu-id="606a7-163">For parameterized reports, specify parameters to use for the report for this subscription.</span></span> <span data-ttu-id="606a7-164">參數可以與視需要執行報表或依其他排程作業執行報表所用的參數不同。</span><span class="sxs-lookup"><span data-stu-id="606a7-164">The parameters can be different from those used to run the report on demand or in other scheduled operations.</span></span>  
  
 <span data-ttu-id="606a7-165">報表會以靜態檔案傳遞。</span><span class="sxs-lookup"><span data-stu-id="606a7-165">The report is delivered as a static file.</span></span> <span data-ttu-id="606a7-166">如果報表包括互動式功能 (例如，連結到其他資料列或資料行)，則那些功能無法使用。</span><span class="sxs-lookup"><span data-stu-id="606a7-166">If the report includes interactive features (for example, links to additional rows and columns), those features are not available.</span></span>  
  
###  <a name="to-create-an-e-mail-subscription"></a><a name="bkmk_create_email_subscription"></a><span data-ttu-id="606a7-167">若要建立電子郵件訂閱</span><span class="sxs-lookup"><span data-stu-id="606a7-167">To Create an E-mail Subscription</span></span>  
  
1.  <span data-ttu-id="606a7-168">在報表管理員的 **[內容]** 頁面上，瀏覽至您要訂閱的報表。</span><span class="sxs-lookup"><span data-stu-id="606a7-168">In Report Manager, on the **Contents** page, navigate to the report you want to subscribe to.</span></span> <span data-ttu-id="606a7-169">按一下報表以開啟它。</span><span class="sxs-lookup"><span data-stu-id="606a7-169">Click the report to open it.</span></span>  
  
2.  <span data-ttu-id="606a7-170">按一下 **[訂閱]** 索引標籤，然後按一下 **[新增訂閱]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-170">Click the **Subscriptions** tab, and then click **New Subscription**.</span></span>  
  
3.  <span data-ttu-id="606a7-171">在 [**傳遞者**] 中，選取 [**電子郵件**]。</span><span class="sxs-lookup"><span data-stu-id="606a7-171">In **Delivered by**, select **E-Mail**.</span></span> <span data-ttu-id="606a7-172">如果這種傳遞類型無法使用，表示您的報表伺服器尚未針對電子郵件訂閱進行設定。</span><span class="sxs-lookup"><span data-stu-id="606a7-172">If this delivery type is not available, your report server has not been configured for e-mail subscriptions.</span></span>  
  
4.  <span data-ttu-id="606a7-173">**在 [收**件者] 文字方塊中，會使用您的網域使用者帳戶來自我定址 [收件者：] 欄位中的收件者名稱。</span><span class="sxs-lookup"><span data-stu-id="606a7-173">In the **To** text box, the recipient name in the To: field is self-addressed using your domain user account.</span></span> <span data-ttu-id="606a7-174">報表伺服器組態設定會決定系統是否會使用您的使用者帳戶來自行處理 [收件者]  欄位。</span><span class="sxs-lookup"><span data-stu-id="606a7-174">Report server configuration settings determine whether the **To** field is self-addressed with your user account.</span></span> <span data-ttu-id="606a7-175">如需變更設定電子郵件地址的詳細資訊，請參閱[為電子郵件傳遞設定報表伺服器 &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="606a7-175">For more information about changing the configuration settings e-mail addresses, see [Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="606a7-176">根據您的權限，可能可以輸入想要傳遞報表的目標電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="606a7-176">Depending on your permissions, you might be able to type the e-mail address you want the report delivered to.</span></span> <span data-ttu-id="606a7-177">若要指定多個電子郵件地址，請使用分號 (;) 隔開。</span><span class="sxs-lookup"><span data-stu-id="606a7-177">To specify multiple e-mail addresses, separate them with a semicolon (;).</span></span> <span data-ttu-id="606a7-178">您也可以在 [副本]  、[密件副本]  和 [回覆至]  文字方塊中，鍵入其他電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="606a7-178">You can also type additional e-mail addresses in the **Cc**, **Bcc**, and **Reply-To** text boxes.</span></span> <span data-ttu-id="606a7-179">這需要您具有管理所有訂閱的權限。</span><span class="sxs-lookup"><span data-stu-id="606a7-179">This requires that you have permission to manage all subscriptions.</span></span>  
  
5.  <span data-ttu-id="606a7-180">選取傳遞選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="606a7-180">Select the delivery options as follows:</span></span>  
  
    -   <span data-ttu-id="606a7-181">若要內嵌或附加報表的副本，請選取 **[包含報表]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-181">To embed or attach a copy of the report, select **Include Report**.</span></span> <span data-ttu-id="606a7-182">報表的格式是由您選取的轉譯格式所決定。</span><span class="sxs-lookup"><span data-stu-id="606a7-182">The format of the report is determined by the rendering format you select.</span></span> <span data-ttu-id="606a7-183">如果您認為報表大小將超出您為電子郵件系統所定義的限制，請勿選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="606a7-183">Do not choose this option if you think the report size will exceed the limit defined for your e-mail system.</span></span>  
  
    -   <span data-ttu-id="606a7-184">若要在電子郵件訊息主體中包含報表的 URL 連結，請選取 [**包含連結**]。</span><span class="sxs-lookup"><span data-stu-id="606a7-184">To include a URL link to the report in the body of the e-mail message, select **Include Link**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="606a7-185">如果您清除這兩個選項，就只會傳送主旨行中的通知文字。</span><span class="sxs-lookup"><span data-stu-id="606a7-185">If you clear both of these options, only the notification text in the Subject line is sent.</span></span>  
  
6.  <span data-ttu-id="606a7-186">從 **[轉譯格式]** 清單方塊中選擇轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="606a7-186">Choose a rendering format from the **Render Format** list box.</span></span> <span data-ttu-id="606a7-187">如果選取 **[包含報表]** 以內嵌或附加報表的副本，就可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="606a7-187">This option is available if you select **Include Report** to embed or attach a copy of the report.</span></span>  
  
    -   <span data-ttu-id="606a7-188">若要將報表內嵌於電子郵件訊息的主體，請選取 [網頁封存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="606a7-188">To embed the report in the body of the e-mail message, select **Web archive**.</span></span>  
  
    -   <span data-ttu-id="606a7-189">若要將報表當成附加檔案傳送，請選擇其他任一種轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="606a7-189">To send the report as an attachment, choose any of the other rendering formats.</span></span>  
  
7.  <span data-ttu-id="606a7-190">從 **[優先權]** 清單方塊中，選取優先權。</span><span class="sxs-lookup"><span data-stu-id="606a7-190">Select a priority from the **Priority** list box.</span></span> <span data-ttu-id="606a7-191">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange 中，此設定會設定電子郵件訊息重要性層級的旗標。</span><span class="sxs-lookup"><span data-stu-id="606a7-191">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] Exchange, this setting sets a flag for the importance level of the e-mail message.</span></span>  
  
8.  <span data-ttu-id="606a7-192">指定您要傳遞報表的時機：</span><span class="sxs-lookup"><span data-stu-id="606a7-192">Specify when you want the report delivered:</span></span>  
  
    -   <span data-ttu-id="606a7-193">若要排程傳遞時間，請按一下 **[排程報表執行完成時]** ，然後按一下 **[選取排程]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-193">To schedule a delivery time, click **When the scheduled report run is complete** and click **Select Schedule**.</span></span> <span data-ttu-id="606a7-194">就會為您開啟排程頁面。</span><span class="sxs-lookup"><span data-stu-id="606a7-194">A schedule page opens for you.</span></span>  
  
    -   <span data-ttu-id="606a7-195">若要選取預先定義的共用排程，其中已經具有您想要使用的日期、時間和循環資訊，請按一下 **[在共用排程上]**，然後選取要用的排程。</span><span class="sxs-lookup"><span data-stu-id="606a7-195">To select a predefined shared schedule that already has the date, time, and recurrence information that you want to use, click **On a shared schedule**, and then select the schedule to use.</span></span>  
  
    -   <span data-ttu-id="606a7-196">若要在以更新的版本更新報表快照集時傳遞報表，請按一下 [重新整理報表內容時]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="606a7-196">To deliver the report when a report snapshot is updated with a newer version,click**When the report content is refreshed**.</span></span> <span data-ttu-id="606a7-197">如果您要訂閱以排程間隔擷取資料的報表，用來重新整理資料的排程就會決定處理訂閱的時間。</span><span class="sxs-lookup"><span data-stu-id="606a7-197">If you are subscribing to a report that retrieves data at scheduled intervals, the schedule used to refresh the data determines when your subscription is processed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="606a7-198">只有當快照集已經和更新排程相關聯時可使用此選項。</span><span class="sxs-lookup"><span data-stu-id="606a7-198">This option is available only for snapshots that are already associated with an update schedule.</span></span>  
  
9. <span data-ttu-id="606a7-199">如果是參數化報表，請指定要用於此訂閱之報表的參數。</span><span class="sxs-lookup"><span data-stu-id="606a7-199">For parameterized reports, specify parameters to use for the report for this subscription.</span></span> <span data-ttu-id="606a7-200">您指定的參數，可以與視需要執行報表或依其他排程作業執行報表所用的參數不同。</span><span class="sxs-lookup"><span data-stu-id="606a7-200">The parameters that you specify can be different from those used to run the report on demand or in other scheduled operations.</span></span>  
  
##  <a name="to-modify-a-subscription"></a><a name="bkmk_modify_subscription"></a><span data-ttu-id="606a7-201">若要修改訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="606a7-201">To Modify a Subscription</span></span>  
 <span data-ttu-id="606a7-202">您可以在任何時間修改訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-202">You can modify a subscription at any time.</span></span> <span data-ttu-id="606a7-203">如果您在處理訂閱時修改訂閱，當更新的設定在傳遞延伸模組接收到訂閱資料之前，儲存到報表伺服器資料庫中時，就會使用更新的設定。</span><span class="sxs-lookup"><span data-stu-id="606a7-203">If you modify a subscription while it is being processed, the updated settings are used if they are saved to the report server database before the delivery extension receives the subscription data.</span></span> <span data-ttu-id="606a7-204">否則，會使用現有的設定。</span><span class="sxs-lookup"><span data-stu-id="606a7-204">Otherwise, the existing settings are used.</span></span>  
  
 <span data-ttu-id="606a7-205">若要找出訂閱，請使用 **[我的訂閱]** 頁面，或檢視與報表相關聯的訂閱定義。</span><span class="sxs-lookup"><span data-stu-id="606a7-205">To locate a subscription, use the **My Subscriptions** page or view the subscription definitions that are associated with a report.</span></span> <span data-ttu-id="606a7-206">您無法直接搜尋訂閱，也無法依擁有者名稱、觸發程序資訊、狀態資訊等等搜尋訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-206">You cannot search for subscriptions directly, nor can you search for a subscription based on owner name, trigger information, status information, and so forth.</span></span>  
  
 <span data-ttu-id="606a7-207">訂閱也可以由報表伺服器管理員修改或刪除。</span><span class="sxs-lookup"><span data-stu-id="606a7-207">Subscriptions can also be modified or deleted by report server administrators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="606a7-208">報表伺服器管理員無法從一個位置，管理在給定報表伺服器上使用的所有個別訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-208">A report server administrator cannot manage from one place all the individual subscriptions that are in use on a given report server.</span></span> <span data-ttu-id="606a7-209">然而，報表伺服器管理員可以存取個別訂閱以修改或刪除。</span><span class="sxs-lookup"><span data-stu-id="606a7-209">However, report server administrators can access each individual subscription to modify or delete it.</span></span>  
  
##  <a name="to-delete-a-subscription"></a><a name="bkmk_delete_subscription"></a><span data-ttu-id="606a7-210">若要刪除訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="606a7-210">To Delete a Subscription</span></span>  
 <span data-ttu-id="606a7-211">刪除訂閱：</span><span class="sxs-lookup"><span data-stu-id="606a7-211">To delete a subscription"</span></span>  
  
1.  <span data-ttu-id="606a7-212">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="606a7-212">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="606a7-213">在報表管理員中，按一下全域工具列上的 **[我的訂閱]** ，然後導覽至您要修改或刪除的訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-213">In Report Manager, click **My Subscriptions** on the global toolbar and navigate to the subscription you want to modify or delete.</span></span>  
  
3.  <span data-ttu-id="606a7-214">或者，在開啟之報表的 **[訂閱]** 索引標籤上，找到您要修改或刪除的訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-214">Alternatively, on the **Subscriptions** tab of an open report, find the subscription that you want to modify or delete.</span></span> <span data-ttu-id="606a7-215">執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="606a7-215">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="606a7-216">若要修改訂閱，請按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-216">To modify a subscription, click **Edit**.</span></span>  
  
    2.  <span data-ttu-id="606a7-217">若要刪除訂閱，請選取訂閱旁的核取方塊，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="606a7-217">To delete a subscription, select the check box next to the subscription, and then click **Delete**.</span></span>  
  
 <span data-ttu-id="606a7-218">本主題並未說明如何取消目前正在報表伺服器上處理的訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-218">This topic does not explain how to cancel a subscription that is currently processing on the report server.</span></span> <span data-ttu-id="606a7-219">如需取消訂閱的詳細資訊，請參閱[管理執行中的進程](manage-a-running-process.md)</span><span class="sxs-lookup"><span data-stu-id="606a7-219">For more information about canceling subscriptions, see [Manage a Running Process](manage-a-running-process.md)</span></span>  
  
 <span data-ttu-id="606a7-220">如果您想要結束訂閱但無法輕易的找到該訂閱，請在所收到的報表上註明，然後依名稱搜尋。</span><span class="sxs-lookup"><span data-stu-id="606a7-220">If you want to end a subscription and you cannot locate the subscription easily, make a note of the report you are receiving and search for it by name.</span></span> <span data-ttu-id="606a7-221">存取到報表之後，您就可以將自己從訂閱中移除。</span><span class="sxs-lookup"><span data-stu-id="606a7-221">Once you access the report, you can remove yourself from the subscription.</span></span> <span data-ttu-id="606a7-222">如果您找不到訂閱，則該訂閱可能是資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-222">If you cannot locate the subscription, the subscription may be a data-driven subscription.</span></span> <span data-ttu-id="606a7-223">如需詳細資訊，請洽詢您的報表伺服器管理員。</span><span class="sxs-lookup"><span data-stu-id="606a7-223">For more information, see your report server administrator.</span></span>  
  
 <span data-ttu-id="606a7-224">如果基礎報表被刪除，則會自動刪除訂閱。</span><span class="sxs-lookup"><span data-stu-id="606a7-224">A subscription is deleted automatically if the underlying report is deleted.</span></span> <span data-ttu-id="606a7-225">如果您在處理訂閱時刪除訂閱，當刪除作業在傳遞延伸模組接收到訂閱資料之前發生，訂閱就會停止。</span><span class="sxs-lookup"><span data-stu-id="606a7-225">If you delete a subscription while it is being processed, the subscription stops if the delete operation occurs before the delivery extension receives subscription data.</span></span> <span data-ttu-id="606a7-226">否則，訂閱會繼續處理。</span><span class="sxs-lookup"><span data-stu-id="606a7-226">Otherwise, the subscription continues to be processed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606a7-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="606a7-227">See Also</span></span>  
 <span data-ttu-id="606a7-228">[工作和權限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="606a7-228">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="606a7-229">[建立及管理 SharePoint 模式報表伺服器的訂閱](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="606a7-229">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span></span>  
 <span data-ttu-id="606a7-230">[建立及管理原生模式報表伺服器的訂閱](../create-manage-subscriptions-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="606a7-230">[Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="606a7-231">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="606a7-231">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="606a7-232">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="606a7-232">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="606a7-233">[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="606a7-233">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="606a7-234">使用我的訂閱</span><span class="sxs-lookup"><span data-stu-id="606a7-234">Use My Subscriptions</span></span>](use-my-subscriptions-native-mode-report-server.md)  
  
  
