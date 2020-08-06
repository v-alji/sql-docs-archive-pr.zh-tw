---
title: Reporting Services 中的 SharePoint 文件庫傳遞 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], report delivery
- delivering reports [Reporting Services]
- subscriptions [Reporting Services], SharePoint library delivery
ms.assetid: cb4e4f71-f2d5-475a-9284-ea324c93c7de
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5ff109781233ca0c56db0c03ed37bdd13e6e75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706977"
---
# <a name="sharepoint-library-delivery-in-reporting-services"></a><span data-ttu-id="dd191-102">Reporting Services 中的 SharePoint 文件庫傳遞</span><span class="sxs-lookup"><span data-stu-id="dd191-102">SharePoint Library Delivery in Reporting Services</span></span>
  <span data-ttu-id="dd191-103">針對 SharePoint 整合所設定的報表伺服器包含您可以用來將報表傳送至 SharePoint 文件庫的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="dd191-103">A report server that is configured for SharePoint integration includes a delivery extension that you can use to send a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="dd191-104">若要使用 SharePoint 傳遞延伸模組，您必須從 SharePoint 網站上的應用程式頁面建立訂閱，然後選取 [SharePoint 文件庫]  作為傳遞類型。</span><span class="sxs-lookup"><span data-stu-id="dd191-104">To use the SharePoint delivery extension, you must create a subscription from an application page on a SharePoint site, and then select **SharePoint document library** as the delivery type.</span></span> <span data-ttu-id="dd191-105">您無法針對在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或報表管理員中建立的訂閱來使用 SharePoint 傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="dd191-105">You cannot use the SharePoint delivery extension for subscriptions that you create in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] or Report Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd191-106">如果報表伺服器以原生模式執行，傳遞延伸模組不支援將報表傳遞至 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="dd191-106">The delivery extension does not support the delivery of reports to a SharePoint site if the report server is running in native mode.</span></span> <span data-ttu-id="dd191-107">如果您嘗試以程式設計的方式呼叫原生模式報表伺服器的傳遞延伸模組，伺服器將會傳回 `rsDeliveryExtensionNotFound` 錯誤，並在報表伺服器的記錄檔中記錄 `rsOperationNotSupportedSharePointMode` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="dd191-107">If you attempt to call the delivery extension programmatically for a native mode report server, the server will return the `rsDeliveryExtensionNotFound` error and log the `rsOperationNotSupportedSharePointMode` error in the report server log files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd191-108">需求</span><span class="sxs-lookup"><span data-stu-id="dd191-108">Requirements</span></span>  
 <span data-ttu-id="dd191-109">將已轉譯報表傳遞至文件庫的需求包括：</span><span class="sxs-lookup"><span data-stu-id="dd191-109">Requirements for delivering rendered reports to a library include the following:</span></span>  
  
-   <span data-ttu-id="dd191-110">報表伺服器必須針對 SharePoint 整合模式設定。</span><span class="sxs-lookup"><span data-stu-id="dd191-110">The report server must be configured for SharePoint integration mode.</span></span>  
  
-   <span data-ttu-id="dd191-111">報表伺服器必須已經安裝並設定 SharePoint 傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="dd191-111">The report server must have the SharePoint delivery extension installed and configured.</span></span>  
  
-   <span data-ttu-id="dd191-112">報表必須是報表定義 (.rdl) 檔。</span><span class="sxs-lookup"><span data-stu-id="dd191-112">The report must be a report definition (.rdl) file.</span></span> <span data-ttu-id="dd191-113">您無法透過訂閱來傳遞其他報表伺服器內容類型，如模型或資源。</span><span class="sxs-lookup"><span data-stu-id="dd191-113">You cannot deliver other report server content types, such as models or resources, through a subscription.</span></span> <span data-ttu-id="dd191-114">您無法訂閱使用模型當做資料來源的特定報表。</span><span class="sxs-lookup"><span data-stu-id="dd191-114">You cannot subscribe to ad hoc reports that use models as a data source.</span></span>  
  
-   <span data-ttu-id="dd191-115">報表必須使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="dd191-115">The report must use stored credentials.</span></span> <span data-ttu-id="dd191-116">這是在報表上建立任何訂閱 (不管傳遞類型為何) 的必要條件。</span><span class="sxs-lookup"><span data-stu-id="dd191-116">This is a prerequisite for creating any subscription on a report, regardless of the delivery type.</span></span>  
  
-   <span data-ttu-id="dd191-117">目的地必須是 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="dd191-117">The destination must be a SharePoint library.</span></span> <span data-ttu-id="dd191-118">選擇目標文件庫時，您必須選擇位於相同 SharePoint 網站上的文件庫。</span><span class="sxs-lookup"><span data-stu-id="dd191-118">When choosing a target library, you must choose one that is on the same SharePoint site.</span></span> <span data-ttu-id="dd191-119">您無法將報表傳遞至相同網站集合中，另一部伺服器或另一個網站上的文件庫。</span><span class="sxs-lookup"><span data-stu-id="dd191-119">You cannot deliver a report to a library on another server or another site within the same site collection.</span></span>  
  
 <span data-ttu-id="dd191-120">報表傳遞時，不包含屬性與中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dd191-120">Properties and metadata are not part of report delivery.</span></span> <span data-ttu-id="dd191-121">首次傳遞報表時，此報表會繼承包含它之資料庫或清單的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd191-121">When the report is delivered for the first time, it inherits the security settings of the folder or list that contains it.</span></span> <span data-ttu-id="dd191-122">如果您之後修改安全性設定或設定報表屬性，就會保留這些設定。</span><span class="sxs-lookup"><span data-stu-id="dd191-122">If you subsequently modify security settings or set report properties, those settings are retained.</span></span> <span data-ttu-id="dd191-123">訂閱僅會重新整理儲存在指定位置的報表。</span><span class="sxs-lookup"><span data-stu-id="dd191-123">The subscription just refreshes the report that is stored at the specified location.</span></span>  
  
## <a name="sharepoint-permissions"></a><span data-ttu-id="dd191-124">SharePoint 權限</span><span class="sxs-lookup"><span data-stu-id="dd191-124">SharePoint Permissions</span></span>  
 <span data-ttu-id="dd191-125">若要建立訂閱，您必須在報表上擁有「檢視項目」權限。</span><span class="sxs-lookup"><span data-stu-id="dd191-125">To create the subscription, you must have View Items permission on the report.</span></span> <span data-ttu-id="dd191-126">若要傳遞報表，您必須在報表要傳遞至其中的文件庫上擁有「新增項目」權限。</span><span class="sxs-lookup"><span data-stu-id="dd191-126">To deliver the report, you must have Add Items permission on the library to which the report is delivered.</span></span>  
  
## <a name="how-to-create-modify-and-delete-subscriptions"></a><span data-ttu-id="dd191-127">如何建立、修改和刪除訂閱</span><span class="sxs-lookup"><span data-stu-id="dd191-127">How to Create, Modify and Delete Subscriptions</span></span>  
  
1.  <span data-ttu-id="dd191-128">移至您要存取報表的來源 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="dd191-128">Go to the SharePoint site from which you access the report.</span></span>  
  
2.  <span data-ttu-id="dd191-129">選取報表、按一下報表旁的向下箭號，然後選取 [管理訂閱]  。</span><span class="sxs-lookup"><span data-stu-id="dd191-129">Select the report, click the down arrow next to the report, and select **Manage Subscriptions**.</span></span>  
  
3.  <span data-ttu-id="dd191-130">按一下 [建立]  、[編輯]  或 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="dd191-130">Click **Create**, **Edit**, or **Delete**.</span></span>  
  
 <span data-ttu-id="dd191-131">[管理訂閱] 清單中的 [狀態] 訊息便會顯示關於訂閱的最新資訊，包括是否成功以及訂閱上次執行的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="dd191-131">A Status message on the Manage Subscriptions list displays current information about the subscription, including whether it succeeded and the date and time the subscription last ran.</span></span>  
  
## <a name="setting-delivery-options"></a><span data-ttu-id="dd191-132">設定傳遞選項</span><span class="sxs-lookup"><span data-stu-id="dd191-132">Setting Delivery Options</span></span>  
 <span data-ttu-id="dd191-133">您可以在將報表傳遞至 SharePoint 文件庫的訂閱上，設定下列傳遞選項。</span><span class="sxs-lookup"><span data-stu-id="dd191-133">You can set the following delivery options on a subscription that delivers a report to a SharePoint library.</span></span>  
  
 <span data-ttu-id="dd191-134">轉譯輸出格式</span><span class="sxs-lookup"><span data-stu-id="dd191-134">Render output format</span></span>  
 <span data-ttu-id="dd191-135">指定您要用來傳遞報表的應用程式格式。</span><span class="sxs-lookup"><span data-stu-id="dd191-135">Specify the application format in which you want the report delivered.</span></span> <span data-ttu-id="dd191-136">報表在傳遞之前，會以這個格式轉譯。</span><span class="sxs-lookup"><span data-stu-id="dd191-136">The report is rendered in this format before delivery.</span></span> <span data-ttu-id="dd191-137">您選取的輸出格式將會決定預設的副檔名。</span><span class="sxs-lookup"><span data-stu-id="dd191-137">The output format you select will determine the default file extension.</span></span>  
  
 <span data-ttu-id="dd191-138">您可以從其中選取輸出格式的清單是安裝在報表伺服器上的轉譯延伸模組集。</span><span class="sxs-lookup"><span data-stu-id="dd191-138">The list of output formats you can select from is the set of rendering extensions that are installed on the report server.</span></span>  
  
 <span data-ttu-id="dd191-139">請注意，您無法指定僅用於內部使用的輸出格式，或是以 SharePoint 整合模式執行之報表伺服器不支援的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="dd191-139">Note that you cannot specify output formats that are for internal use only, or that are not supported for report servers that run in SharePoint integrated mode.</span></span> <span data-ttu-id="dd191-140">這些格式包括 Null、RGDI 和 HTMLOWC。</span><span class="sxs-lookup"><span data-stu-id="dd191-140">These formats include Null, RGDI and HTMLOWC.</span></span>  
  
 <span data-ttu-id="dd191-141">檔案名稱與副檔名</span><span class="sxs-lookup"><span data-stu-id="dd191-141">File name and extension</span></span>  
 <span data-ttu-id="dd191-142">將報表的檔案名稱與副檔名指定為您要顯示在目標文件庫中的檔案名稱與副檔名。</span><span class="sxs-lookup"><span data-stu-id="dd191-142">Specify the file name and extension of the report as you want it to appear in the target library.</span></span> <span data-ttu-id="dd191-143">如果您沒有指定副檔名，報表伺服器會依據報表輸出格式來建立副檔名。</span><span class="sxs-lookup"><span data-stu-id="dd191-143">If you do not specify a file extension, the report server will create one based on the report output format.</span></span> <span data-ttu-id="dd191-144">這是必要的值。</span><span class="sxs-lookup"><span data-stu-id="dd191-144">This value is required.</span></span> <span data-ttu-id="dd191-145">檔案名稱不得包含下列字元：: \ / \* ?</span><span class="sxs-lookup"><span data-stu-id="dd191-145">The file name must not include the following characters: : \ / \* ?</span></span> <span data-ttu-id="dd191-146">" \< > | # { } %</span><span class="sxs-lookup"><span data-stu-id="dd191-146">" \< > | # { } %</span></span>  
  
 <span data-ttu-id="dd191-147">Title</span><span class="sxs-lookup"><span data-stu-id="dd191-147">Title</span></span>  
 <span data-ttu-id="dd191-148">在目標文件庫中，指定報表的選用 `Title` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd191-148">Specifies an optional `Title` property for the report in the target library.</span></span> <span data-ttu-id="dd191-149">這是儲存在文件庫中之所有項目的標準屬性。</span><span class="sxs-lookup"><span data-stu-id="dd191-149">This is a standard property for all items stored in a library.</span></span> <span data-ttu-id="dd191-150">使用者可以在檢視 SharePoint 網站上的文件庫內容時，指定要顯示或隱藏此屬性。</span><span class="sxs-lookup"><span data-stu-id="dd191-150">Users can specify whether to show or hide this property when viewing library contents on a SharePoint site.</span></span>  
  
 <span data-ttu-id="dd191-151">Path</span><span class="sxs-lookup"><span data-stu-id="dd191-151">Path</span></span>  
 <span data-ttu-id="dd191-152">指定指向 SharePoint 文件庫的完整 URL，包括 SharePoint Web 應用程式和網站。</span><span class="sxs-lookup"><span data-stu-id="dd191-152">Specifies a fully qualified URL to the SharePoint library, including the SharePoint Web application and site.</span></span> <span data-ttu-id="dd191-153">例如：， <http://mySharePointWeb/MySite/MyDocLib> 其中 " <http://mySharePointWeb> " 表示 Web 應用程式，"「我的」是 sharepoint 網站，而" MyDocLib "是要傳遞報表的 sharepoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="dd191-153">For example: <http://mySharePointWeb/MySite/MyDocLib>; where "<http://mySharePointWeb>" indicates the Web application, "MySite" is the SharePoint site, and "MyDocLib" is the SharePoint library where the report will be delivered.</span></span>  
  
 <span data-ttu-id="dd191-154">您無法指定頁面、網站或清單。</span><span class="sxs-lookup"><span data-stu-id="dd191-154">You cannot specify a page, site, or list.</span></span> <span data-ttu-id="dd191-155">目標容器必須是相同網站或伺服陣列中的文件庫。</span><span class="sxs-lookup"><span data-stu-id="dd191-155">The target container must be a library in the same site or farm.</span></span>  
  
 <span data-ttu-id="dd191-156">覆寫選項</span><span class="sxs-lookup"><span data-stu-id="dd191-156">Overwrite options</span></span>  
 <span data-ttu-id="dd191-157">指定在處理訂閱時，具有相同名稱與副檔名的檔案是否要由較新的版本取代。</span><span class="sxs-lookup"><span data-stu-id="dd191-157">Specifies whether a file with the same name and extension is replaced by a newer version when the subscription is processed.</span></span> <span data-ttu-id="dd191-158">如果您要以較新的版本取代現有的檔案，選擇 [覆寫]  。</span><span class="sxs-lookup"><span data-stu-id="dd191-158">Choose **Overwrite** if you want to replace an existing file with a newer version.</span></span> <span data-ttu-id="dd191-159">如果您不要訂閱取代檔案，選擇 [無]  。</span><span class="sxs-lookup"><span data-stu-id="dd191-159">Choose **None** if you do not want the subscription to replace a file.</span></span> <span data-ttu-id="dd191-160">在此情況下，如果有具有目標名稱與副檔名的檔案存在，則傳遞不會發生。</span><span class="sxs-lookup"><span data-stu-id="dd191-160">In this case, no delivery will occur if a file exists with the target name and extension.</span></span> <span data-ttu-id="dd191-161">如果您要在檔案名稱結尾附加一個數字，藉此新增相同檔案的連續版本，選擇 [自動遞增]  。</span><span class="sxs-lookup"><span data-stu-id="dd191-161">Choose **Autoincrement** if you want to add successive versions of the same file by appending a number at the end of the file name.</span></span>  
  
 <span data-ttu-id="dd191-162">自動複製</span><span class="sxs-lookup"><span data-stu-id="dd191-162">Autocopy</span></span>  
 <span data-ttu-id="dd191-163">如果您要使用 [自動複製] 功能，將檔案的最新版本自動複製到多個位置，當啟用 [覆寫]  時，就會複製該檔案。</span><span class="sxs-lookup"><span data-stu-id="dd191-163">If you are using the Autocopy feature to automatically copy the latest version of a file to multiple locations, the file will be copied if **Overwrite** is enabled.</span></span> <span data-ttu-id="dd191-164">如果您使用**自動遞增**或**無**，傳遞將會失敗，而且會 `rsDeliveryError` 發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dd191-164">If you used **Autoincrement** or **None**, the delivery will fail and the `rsDeliveryError` error will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd191-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd191-165">See Also</span></span>  
 <span data-ttu-id="dd191-166">[建立及管理 SharePoint 模式報表伺服器的訂閱](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="dd191-166">[Create and Manage Subscriptions for SharePoint Mode Report Servers](create-and-manage-subscriptions-for-sharepoint-mode-report-servers.md) </span></span>  
 <span data-ttu-id="dd191-167">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="dd191-167">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="dd191-168">指定報表資料來源的認證及連線資訊</span><span class="sxs-lookup"><span data-stu-id="dd191-168">Specify Credential and Connection Information for Report Data Sources</span></span>](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
