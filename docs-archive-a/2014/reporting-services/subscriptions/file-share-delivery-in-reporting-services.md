---
title: Reporting Services 中的檔案共用傳遞 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
ms.assetid: 9f338dd3-f68a-4355-b9d7-9b25dacf3b5e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9bba83a89612f8601adedd827edad0e587d096d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606062"
---
# <a name="file-share-delivery-in-reporting-services"></a><span data-ttu-id="c02eb-102">Reporting Services 中的檔案共用傳遞</span><span class="sxs-lookup"><span data-stu-id="c02eb-102">File Share Delivery in Reporting Services</span></span>
  <span data-ttu-id="c02eb-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 包括檔案共用傳遞延伸模組，讓您可以傳遞報表到資料夾。</span><span class="sxs-lookup"><span data-stu-id="c02eb-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] includes a file share delivery extension so that you can deliver a report to a folder.</span></span> <span data-ttu-id="c02eb-104">依預設，可以使用檔案共用傳遞延伸模組，且不需額外的組態。</span><span class="sxs-lookup"><span data-stu-id="c02eb-104">The file share delivery extension is available by default and requires no additional configuration.</span></span> <span data-ttu-id="c02eb-105">若要順利完成檔案傳遞，您必須設定共用資料夾的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="c02eb-105">In order for file delivery to succeed, you must set write access permissions on the shared folder.</span></span> <span data-ttu-id="c02eb-106">此外，需要存取報表的使用者必須擁有共用資料夾的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="c02eb-106">In addition, users who require access to the reports must have read permissions on the shared folder.</span></span>  
  
 <span data-ttu-id="c02eb-107">若要散發報表到檔案共用，您必須定義標準訂閱或資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="c02eb-107">To distribute a report to a file share, you define either a standard subscription or a data-driven subscription.</span></span> <span data-ttu-id="c02eb-108">在同一時間，您只能夠訂閱並要求一個報表傳遞。</span><span class="sxs-lookup"><span data-stu-id="c02eb-108">You can subscribe to and request delivery for only one report at a time.</span></span> <span data-ttu-id="c02eb-109">若要了解如何在資料驅動訂閱中使用檔案共用傳遞，請參閱[建立資料驅動訂閱 &#40;SSRS 教學課程&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="c02eb-109">To learn how to use file share delivery in a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span> <span data-ttu-id="c02eb-110">此外，執行遠端檔案共用訂閱的帳戶需要在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 電腦上進行本機登入的權限。</span><span class="sxs-lookup"><span data-stu-id="c02eb-110">Additionally, the account that runs remote file share subscriptions requires rights to log on locally on the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] computer.</span></span>  
  
||  
|-|  
|<span data-ttu-id="c02eb-111">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="c02eb-111">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="c02eb-112">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="c02eb-112">In this topic:</span></span>  
  
-   [<span data-ttu-id="c02eb-113">傳遞給共用資料夾之報表的特性</span><span class="sxs-lookup"><span data-stu-id="c02eb-113">Characteristics of a Report That is Delivered to a Shared Folder</span></span>](#bkmk_Characteristics)  
  
-   [<span data-ttu-id="c02eb-114">目的檔案夾</span><span class="sxs-lookup"><span data-stu-id="c02eb-114">Target Folders</span></span>](#bkmk_target_folders)  
  
-   [<span data-ttu-id="c02eb-115">檔案格式</span><span class="sxs-lookup"><span data-stu-id="c02eb-115">File Formats</span></span>](#bkmk_file_formats)  
  
-   [<span data-ttu-id="c02eb-116">檔案選項</span><span class="sxs-lookup"><span data-stu-id="c02eb-116">File Options</span></span>](#bkmk_file_options)  
  
##  <a name="characteristics-of-a-report-that-is-delivered-to-a-shared-folder"></a><a name="bkmk_Characteristics"></a><span data-ttu-id="c02eb-117">傳遞至共用資料夾之報表的特性</span><span class="sxs-lookup"><span data-stu-id="c02eb-117">Characteristics of a Report That is Delivered to a Shared Folder</span></span>  
 <span data-ttu-id="c02eb-118">傳遞給共用資料夾的報表屬於靜態檔案，這和報表伺服器所主控及管理的報表不同。</span><span class="sxs-lookup"><span data-stu-id="c02eb-118">Unlike reports that are hosted and managed by a report server, reports that are delivered to a shared folder are static files.</span></span> <span data-ttu-id="c02eb-119">為報表定義的互動式功能不適用於以檔案形式儲存在檔案系統中的報表，</span><span class="sxs-lookup"><span data-stu-id="c02eb-119">Interactive features that are defined for the report do not work for reports that are stored as files on the file system.</span></span> <span data-ttu-id="c02eb-120">互動式功能是以靜態元素來表示。</span><span class="sxs-lookup"><span data-stu-id="c02eb-120">Interaction features are represented as static elements.</span></span> <span data-ttu-id="c02eb-121">例如，如果您傳遞矩陣報表，所產生的檔案會顯示報表的最上層檢視；您無法展開資料列和資料行來檢視支援的資料。</span><span class="sxs-lookup"><span data-stu-id="c02eb-121">For example, if you deliver a matrix report, the resulting file shows the top-level view of the report; you cannot expand rows and columns to view supporting data.</span></span> <span data-ttu-id="c02eb-122">如果報表包括圖表，則使用預設呈現方式。</span><span class="sxs-lookup"><span data-stu-id="c02eb-122">If the report includes charts, the default presentation is used.</span></span> <span data-ttu-id="c02eb-123">如果報表連結到其他報表，則連結會轉譯成靜態文字。</span><span class="sxs-lookup"><span data-stu-id="c02eb-123">If the report links through to another report, the link is rendered as static text.</span></span> <span data-ttu-id="c02eb-124">如果您想要在傳遞的報表中保留互動式功能，請改用電子郵件傳遞。</span><span class="sxs-lookup"><span data-stu-id="c02eb-124">If you want to retain interactive features in a delivered report, use e-mail delivery instead.</span></span> <span data-ttu-id="c02eb-125">如需詳細資訊，請參閱 [Reporting Services 中的電子郵件傳遞](e-mail-delivery-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c02eb-125">For more information, see [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md).</span></span>  
  
##  <a name="target-folders"></a><a name="bkmk_target_folders"></a><span data-ttu-id="c02eb-126">目的檔案夾</span><span class="sxs-lookup"><span data-stu-id="c02eb-126">Target Folders</span></span>  
 <span data-ttu-id="c02eb-127">定義使用檔案共用傳遞的訂閱時，必須指定現有的資料夾做為目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="c02eb-127">When defining a subscription that uses file share delivery, you must specify an existing folder as the target folder.</span></span> <span data-ttu-id="c02eb-128">報表伺服器不會在檔案系統中建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="c02eb-128">The report server does not create folders on the file system.</span></span> <span data-ttu-id="c02eb-129">您指定的資料夾必須可以透過網路連接來存取。</span><span class="sxs-lookup"><span data-stu-id="c02eb-129">The folder that you specify must be accessible over a network connection.</span></span>  
  
 <span data-ttu-id="c02eb-130">確認要檢視共用資料夾中報表的使用者擁有讀取權限。</span><span class="sxs-lookup"><span data-stu-id="c02eb-130">Verify that users who will view the reports in the shared folder have Read permission.</span></span>  
  
 <span data-ttu-id="c02eb-131">在訂閱中指定目標資料夾時，請使用包含電腦網路名稱的統一命名慣例 (UNC) 格式。</span><span class="sxs-lookup"><span data-stu-id="c02eb-131">When specifying the target folder in a subscription, use Uniform Naming Convention (UNC) format that includes the computer's network name.</span></span> <span data-ttu-id="c02eb-132">資料夾路徑中不要包含尾端的反斜線。</span><span class="sxs-lookup"><span data-stu-id="c02eb-132">Do not include trailing backslashes in the folder path.</span></span> <span data-ttu-id="c02eb-133">下列範例說明 UNC 路徑：</span><span class="sxs-lookup"><span data-stu-id="c02eb-133">The following example illustrates a UNC path:</span></span>  
  
```  
\\<servername>\reportarchive\operations\2003  
```  
  
 <span data-ttu-id="c02eb-134">建立資料夾時，請考慮您需要的連接限制。</span><span class="sxs-lookup"><span data-stu-id="c02eb-134">When you create the folder, consider the connection limits you require.</span></span> <span data-ttu-id="c02eb-135">雖然報表伺服器只需要兩個連接，但您必須包含足夠的連接來滿足其他想要開啟共用資料夾報表的使用者。</span><span class="sxs-lookup"><span data-stu-id="c02eb-135">The report server requires two connections, but you must include enough connections to accommodate additional users who want to open reports on the shared folder.</span></span>  
  
##  <a name="file-formats"></a><a name="bkmk_file_formats"></a> <span data-ttu-id="c02eb-136">檔案格式</span><span class="sxs-lookup"><span data-stu-id="c02eb-136">File Formats</span></span>  
 <span data-ttu-id="c02eb-137">可以使用各種檔案格式來轉譯報表，例如 HTML 或 Excel。</span><span class="sxs-lookup"><span data-stu-id="c02eb-137">Reports can be rendered in a variety of file formats, such as HTML or Excel.</span></span> <span data-ttu-id="c02eb-138">若要以特定的檔案格式儲存報表，請在建立您的訂閱時選取該轉譯格式。</span><span class="sxs-lookup"><span data-stu-id="c02eb-138">To save the report in a specific file format, select that rendering format when creating your subscription.</span></span> <span data-ttu-id="c02eb-139">例如，選擇 **[Excel]** 會將報表儲存為 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 檔案。</span><span class="sxs-lookup"><span data-stu-id="c02eb-139">For example, choosing **Excel** saves the report as a [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] file.</span></span> <span data-ttu-id="c02eb-140">雖然您可以選擇任何支援的轉譯格式，當轉譯檔案時有些格式會運作的比較好。</span><span class="sxs-lookup"><span data-stu-id="c02eb-140">Although you can choose from any supported rendering format, some formats work better than others when rendering to a file.</span></span>  
  
 <span data-ttu-id="c02eb-141">若為檔案共用傳遞，請選擇以單一檔案傳遞報表的格式，其中所有影像和相關內容會包括在報表內。</span><span class="sxs-lookup"><span data-stu-id="c02eb-141">For file share delivery, choose a format that delivers the report in a single file, where all images and related content are included in the report.</span></span> <span data-ttu-id="c02eb-142">適當的格式包括網頁封存、PDF、TIFF 和 Excel。</span><span class="sxs-lookup"><span data-stu-id="c02eb-142">Suitable formats include Web archive, PDF, TIFF, and Excel.</span></span> <span data-ttu-id="c02eb-143">請避免使用 HTML4.0。</span><span class="sxs-lookup"><span data-stu-id="c02eb-143">Avoid HTML4.0.</span></span> <span data-ttu-id="c02eb-144">如果您的報表包含影像，HTML 4.0 格式就不會在檔案中包含這些影像。</span><span class="sxs-lookup"><span data-stu-id="c02eb-144">If your report includes images, the HTML 4.0 formats will not include them in the file.</span></span>  
  
##  <a name="file-options"></a><a name="bkmk_file_options"></a> <span data-ttu-id="c02eb-145">檔案選項</span><span class="sxs-lookup"><span data-stu-id="c02eb-145">File Options</span></span>  
 <span data-ttu-id="c02eb-146">當您建立訂閱時，您可選擇選項來決定要如何建立檔案名稱以及在一段時間後，是否會以較新的版本來取代。</span><span class="sxs-lookup"><span data-stu-id="c02eb-146">When you create a subscription, you can choose options that determine how the file name is created and whether it is replaced by newer versions over time.</span></span> <span data-ttu-id="c02eb-147">完整的檔案名稱有三個部分：名稱、副檔名，以及附加至檔案以建立唯一檔案名稱的文字或數字。</span><span class="sxs-lookup"><span data-stu-id="c02eb-147">A fully qualified file name has three parts: a name, an extension, and text or a number that is appended to the file to create a unique file name.</span></span> <span data-ttu-id="c02eb-148">覆寫選項會決定要將文字或數字加入至檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c02eb-148">Overwrite options determine whether the text or number is added to the file name.</span></span>  
  
 <span data-ttu-id="c02eb-149">檔案名稱是以報表名稱為依據，但是您可以提供訂閱中的自訂名稱。</span><span class="sxs-lookup"><span data-stu-id="c02eb-149">The file name is based on the report name, but you can provide a custom name in the subscription.</span></span> <span data-ttu-id="c02eb-150">副檔名為選擇性，但是如果您有指定副檔名，報表伺服器將會建立對應到轉譯格式的副檔名。</span><span class="sxs-lookup"><span data-stu-id="c02eb-150">The extension is optional, but if you specify it, the report server will create an extension that corresponds to the rendering format.</span></span>  
  
 <span data-ttu-id="c02eb-151">您可以指定覆寫選項，針對每一次報表傳遞重複使用相同的檔案名稱，或者也可以建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="c02eb-151">You can specify overwrite options to reuse the same file name for each report delivery or to create a new file.</span></span> <span data-ttu-id="c02eb-152">若要覆寫檔案，您必須使用相同的檔案名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="c02eb-152">To overwrite the file, you must use the same file name and extension.</span></span>  
  
 <span data-ttu-id="c02eb-153">有一個替代方式可以在每一次傳遞中建立唯一的檔案，就是在檔案名稱中加入時間戳記。</span><span class="sxs-lookup"><span data-stu-id="c02eb-153">An alternative approach to creating unique files for every delivery is to include a timestamp in the file name.</span></span> <span data-ttu-id="c02eb-154">若要這樣做，請將 `@timestamp` 變數加入檔案名稱 (例如 *CompanySales@timestamp*)。</span><span class="sxs-lookup"><span data-stu-id="c02eb-154">To do this, add the `@timestamp` variable to the file name (for example, *CompanySales@timestamp*).</span></span> <span data-ttu-id="c02eb-155">使用這個方法時，會讓檔案名稱依照定義成為唯一的檔案名稱，所以絕對不會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="c02eb-155">With this approach, the file name is unique by definition, so it will never be overwritten.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c02eb-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c02eb-156">See Also</span></span>  
 [<span data-ttu-id="c02eb-157">以原生模式 &#40;Reporting Services 建立、修改和刪除標準訂閱&#41;</span><span class="sxs-lookup"><span data-stu-id="c02eb-157">Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;</span></span>](create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  
