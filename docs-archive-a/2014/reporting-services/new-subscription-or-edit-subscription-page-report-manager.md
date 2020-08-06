---
title: 新增訂閱或編輯訂閱頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e02d6529-ce67-4305-b7f0-433997e99c21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d74f5bf9bee537522d625f37d6b077fdfed5b2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592500"
---
# <a name="new-subscription-or-edit-subscription-page-report-manager"></a><span data-ttu-id="0beb1-102">新增訂閱或編輯訂閱頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="0beb1-102">New Subscription or Edit Subscription Page (Report Manager)</span></span>
  <span data-ttu-id="0beb1-103">使用 [新增訂閱] 或 [編輯訂閱] 頁面，即可在報表中建立新的訂閱或修改現有的訂閱。</span><span class="sxs-lookup"><span data-stu-id="0beb1-103">Use the New Subscription or Edit Subscription page to create a new subscription or modify an existing subscription to a report.</span></span> <span data-ttu-id="0beb1-104">這個頁面的此選項隨著您的角色指派而改變。</span><span class="sxs-lookup"><span data-stu-id="0beb1-104">The options on this page vary depending on your role assignment.</span></span> <span data-ttu-id="0beb1-105">具有進階權限的使用者可以使用額外的選項。</span><span class="sxs-lookup"><span data-stu-id="0beb1-105">Users with advanced permissions can work with additional options.</span></span>  
  
 <span data-ttu-id="0beb1-106">可自主式執行的報表支援訂閱。</span><span class="sxs-lookup"><span data-stu-id="0beb1-106">Subscriptions are supported for reports that can run unattended.</span></span> <span data-ttu-id="0beb1-107">報表至少必須使用預存認證或無認證。</span><span class="sxs-lookup"><span data-stu-id="0beb1-107">At a minimum, the report must use stored or no credentials.</span></span> <span data-ttu-id="0beb1-108">如果報表使用參數，就必須指定預設值。</span><span class="sxs-lookup"><span data-stu-id="0beb1-108">If the report uses parameters, a default value must be specified.</span></span> <span data-ttu-id="0beb1-109">如果您變更報表執行設定或移除參數屬性的預設值，就可能會造成訂閱停用。</span><span class="sxs-lookup"><span data-stu-id="0beb1-109">Subscriptions may become inactive if you change report execution settings or remove the default values used by parameter properties.</span></span> <span data-ttu-id="0beb1-110">如需詳細資訊，請參閱 [建立和管理原生模式報表伺服器的訂閱](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="0beb1-110">For more information, see [Create and Manage Subscriptions for Native Mode Report Servers](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0beb1-111">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="0beb1-111">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0beb1-112">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="0beb1-112">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="0beb1-113">導覽</span><span class="sxs-lookup"><span data-stu-id="0beb1-113">Navigation</span></span>  
 <span data-ttu-id="0beb1-114">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="0beb1-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-new-subscription-or-edit-subscription-page"></a><span data-ttu-id="0beb1-115">若要開啟新增訂閱或編輯訂閱頁面</span><span class="sxs-lookup"><span data-stu-id="0beb1-115">To open the New Subscription or Edit Subscription page</span></span>  
  
1.  <span data-ttu-id="0beb1-116">開啟報表管理員，然後找出您想要加入訂閱的報表。</span><span class="sxs-lookup"><span data-stu-id="0beb1-116">Open Report Manager, and locate the report for which you want to add a subscription.</span></span>  
  
2.  <span data-ttu-id="0beb1-117">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="0beb1-117">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="0beb1-118">在下拉式功能表中，執行下列其中一項步驟：</span><span class="sxs-lookup"><span data-stu-id="0beb1-118">In the drop-down menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="0beb1-119">按一下 [管理] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0beb1-119">Click **Manage**.</span></span> <span data-ttu-id="0beb1-120">這樣就會開啟該報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="0beb1-120">This opens the General properties page for the report.</span></span> <span data-ttu-id="0beb1-121">然後選取 [**訂閱**] 索引標籤。在工具列中，按一下 [**新增訂閱**]，或選取現有的訂用帳戶，然後按一下 [**編輯**]。</span><span class="sxs-lookup"><span data-stu-id="0beb1-121">Then select the **Subscriptions** tab. In the toolbar, click **New Subscription**, or select an existing subscription and click **Edit**.</span></span>  
  
    -   <span data-ttu-id="0beb1-122">按一下 **[訂閱]**。</span><span class="sxs-lookup"><span data-stu-id="0beb1-122">Click **Subscribe**.</span></span> <span data-ttu-id="0beb1-123">這樣就會開啟該報表的 **[新增訂閱]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="0beb1-123">This opens the **New Subscription** page for the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0beb1-124">選項</span><span class="sxs-lookup"><span data-stu-id="0beb1-124">Options</span></span>  
 <span data-ttu-id="0beb1-125">**傳遞者**</span><span class="sxs-lookup"><span data-stu-id="0beb1-125">**Delivered by**</span></span>  
 <span data-ttu-id="0beb1-126">選取要用來散發報表的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="0beb1-126">Select the delivery extension to use to distribute the report.</span></span> <span data-ttu-id="0beb1-127">系統會根據您所選取的傳遞延伸模組顯示下列設定：</span><span class="sxs-lookup"><span data-stu-id="0beb1-127">Depending on the delivery extension you select, the following settings appear:</span></span>  
  
-   <span data-ttu-id="0beb1-128">電子郵件訂閱提供電子郵件使用者熟悉的欄位 (例如， **to**、 **Subject**和**Priority**欄位) 。</span><span class="sxs-lookup"><span data-stu-id="0beb1-128">E-mail subscriptions provide fields that are familiar to e-mail users (for example, **To**, **Subject**, and **Priority** fields).</span></span> <span data-ttu-id="0beb1-129">指定 **[包含報表]** 即可內嵌或附加報表，或是指定 **[包含連結]** 以包含連結到報表的 URL。</span><span class="sxs-lookup"><span data-stu-id="0beb1-129">Specify **Include Report** to embed or attach the report, or **Include Link** to include a URL to the report.</span></span> <span data-ttu-id="0beb1-130">指定 **[轉譯格式]** 即可為附加或內嵌的報表選擇呈現格式。</span><span class="sxs-lookup"><span data-stu-id="0beb1-130">Specify **Render Format** to choose a presentation format for the attached or embedded report.</span></span>  
  
-   <span data-ttu-id="0beb1-131">檔案共用訂閱提供讓您指定目標位置的欄位。</span><span class="sxs-lookup"><span data-stu-id="0beb1-131">File share subscriptions provide fields that allow you to specify a target location.</span></span> <span data-ttu-id="0beb1-132">您可以傳遞任何報表至檔案共用。</span><span class="sxs-lookup"><span data-stu-id="0beb1-132">You can deliver any report to a file share.</span></span> <span data-ttu-id="0beb1-133">不過，支援互動式功能的報表 (包括支援針對資料列和資料行向下鑽研的矩陣報表) 將轉譯成靜態檔案。</span><span class="sxs-lookup"><span data-stu-id="0beb1-133">However, reports that support interactive features (including matrix reports that support drill-down to supporting rows and columns) are rendered as static files.</span></span> <span data-ttu-id="0beb1-134">您無法在靜態檔案中檢視向下鑽研資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="0beb1-134">You cannot view drill-down rows and columns in a static file.</span></span> <span data-ttu-id="0beb1-135">檔案共用名稱必須以統一命名慣例指定 (UNC) 格式 (例如 \\ \mycomputer\public\myreportfiles) 。</span><span class="sxs-lookup"><span data-stu-id="0beb1-135">The file share name must be specified in Uniform Naming Convention (UNC) format (for example, \\\mycomputer\public\myreportfiles).</span></span> <span data-ttu-id="0beb1-136">在路徑名稱中不可包含反斜線。</span><span class="sxs-lookup"><span data-stu-id="0beb1-136">Do not include a trailing backslash in the path name.</span></span> <span data-ttu-id="0beb1-137">報表檔案會使用以轉譯格式為基礎的檔案格式進行傳遞 (例如，如果您選擇了 **[Excel]**，報表就會以 .xls 檔案來傳遞)。</span><span class="sxs-lookup"><span data-stu-id="0beb1-137">The report file will be delivered in a file format that is based on the render format (for example, if you choose **Excel**, the report is delivered as an .xls file).</span></span>  
  
 <span data-ttu-id="0beb1-138">傳遞延伸模組是否可用，取決於該模組是否安裝和設定於報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0beb1-138">The availability of a delivery extension depends on whether it is installed and configured on the report server.</span></span> <span data-ttu-id="0beb1-139">報表伺服器電子郵件是預設傳遞延伸模組，但您必須先設定它才能夠使用。</span><span class="sxs-lookup"><span data-stu-id="0beb1-139">Report Server E-mail is the default delivery extension, but it must be configured before you can use it.</span></span> <span data-ttu-id="0beb1-140">檔案共用傳遞不需要進行設定，但您必須先定義共用資料夾，才能加以使用。</span><span class="sxs-lookup"><span data-stu-id="0beb1-140">File Share delivery does not require configuration, but you must define a shared folder before you can use it.</span></span>  
  
## <a name="subscription-processing-options"></a><span data-ttu-id="0beb1-141">訂閱處理選項</span><span class="sxs-lookup"><span data-stu-id="0beb1-141">Subscription Processing Options</span></span>  
 <span data-ttu-id="0beb1-142">使用這些設定來定義使訂閱開始處理的狀況。</span><span class="sxs-lookup"><span data-stu-id="0beb1-142">Use these settings to define the conditions that cause a subscription to process.</span></span> <span data-ttu-id="0beb1-143">有些選項只能在使用參數的報表或以報表執行快照集執行的報表中使用。</span><span class="sxs-lookup"><span data-stu-id="0beb1-143">Some of the options are only available for reports that use parameters or that run as report execution snapshots.</span></span>  
  
 <span data-ttu-id="0beb1-144">**重新整理報表內容時**</span><span class="sxs-lookup"><span data-stu-id="0beb1-144">**When the report content is refreshed**</span></span>  
 <span data-ttu-id="0beb1-145">選擇此選項以訂閱依排程重新整理的報表快照集。</span><span class="sxs-lookup"><span data-stu-id="0beb1-145">Select this option to subscribe to a report snapshot that is refreshed on a scheduled basis.</span></span> <span data-ttu-id="0beb1-146">只有在訂閱以報表執行快照集執行的報表時，才看得見這個選項。</span><span class="sxs-lookup"><span data-stu-id="0beb1-146">This option is visible only when you are subscribing to a report that runs as a report execution snapshot.</span></span> <span data-ttu-id="0beb1-147">報表執行快照集的內容通常會定期重新整理。</span><span class="sxs-lookup"><span data-stu-id="0beb1-147">The content for a report execution snapshot is typically refreshed on a schedule.</span></span> <span data-ttu-id="0beb1-148">對於以此模式執行的報表，您可以將訂閱定義為重新整理快照集時發生。</span><span class="sxs-lookup"><span data-stu-id="0beb1-148">For reports that run in this mode, you can define a subscription to occur when the snapshot is refreshed.</span></span>  
  
 <span data-ttu-id="0beb1-149">**排程報表執行完成時**</span><span class="sxs-lookup"><span data-stu-id="0beb1-149">**When the scheduled report run is complete**</span></span>  
 <span data-ttu-id="0beb1-150">建立決定何時處理訂閱的排程。</span><span class="sxs-lookup"><span data-stu-id="0beb1-150">Create a schedule that determines when the subscription is processed.</span></span>  
  
 <span data-ttu-id="0beb1-151">**在共用排程上**</span><span class="sxs-lookup"><span data-stu-id="0beb1-151">**On a shared schedule**</span></span>  
 <span data-ttu-id="0beb1-152">選擇預先定義的排程以處理訂閱。</span><span class="sxs-lookup"><span data-stu-id="0beb1-152">Select a predefined schedule to process the subscription.</span></span>  
  
 <span data-ttu-id="0beb1-153">**輸入參數值**</span><span class="sxs-lookup"><span data-stu-id="0beb1-153">**Enter parameter values**</span></span>  
 <span data-ttu-id="0beb1-154">當您訂閱具有參數的報表時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0beb1-154">Use this option when you are subscribing to a report that has parameters.</span></span> <span data-ttu-id="0beb1-155">此選項只能用於參數化的報表。</span><span class="sxs-lookup"><span data-stu-id="0beb1-155">This option is available only for parameterized reports.</span></span> <span data-ttu-id="0beb1-156">訂閱參數化報表時，可以指定用來建立透過訂閱傳遞之報表版本所使用的參數值。</span><span class="sxs-lookup"><span data-stu-id="0beb1-156">When subscribing to a parameterized report, you can specify the parameter values that are used to create the version of the report that is delivered through the subscription.</span></span> <span data-ttu-id="0beb1-157">例如，您可以指定區域碼，以選取特定區域的業務資料。</span><span class="sxs-lookup"><span data-stu-id="0beb1-157">For example, you can specify a region code to select sales data for a particular region.</span></span> <span data-ttu-id="0beb1-158">若未指定任何值，就會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="0beb1-158">If you do not specify a value, the default value is used.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0beb1-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0beb1-159">See Also</span></span>  
 <span data-ttu-id="0beb1-160">[針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="0beb1-160">[Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) </span></span>  
 <span data-ttu-id="0beb1-161">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="0beb1-161">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="0beb1-162">[建立、修改和刪除共用排程](subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="0beb1-162">[Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 [<span data-ttu-id="0beb1-163">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="0beb1-163">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
