---
title: 使用瀏覽器尋找及檢視報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: edf4843a-2a0a-486f-be25-14a3c1c6bc72
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b864188fc5152a11ad66ac9cd986891b88849a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707206"
---
# <a name="finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs"></a><span data-ttu-id="db2ee-102">使用瀏覽器尋找及檢視報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="db2ee-102">Finding and Viewing Reports with a Browser (Report Builder and SSRS)</span></span>
  <span data-ttu-id="db2ee-103">您可以使用任何支援的網頁瀏覽器，透過報表伺服器的直接連接來檢視報表。</span><span class="sxs-lookup"><span data-stu-id="db2ee-103">You can use any supported Web browser to view a report through a direct connection to a report server.</span></span> <span data-ttu-id="db2ee-104">每一個報表在報表伺服器上都有一個 URL 位址。</span><span class="sxs-lookup"><span data-stu-id="db2ee-104">Every report has a URL address on a report server.</span></span> <span data-ttu-id="db2ee-105">您可以輸入報表的 Web 位址，在任何 Web 應用程式的瀏覽器視窗中開啟該報表。</span><span class="sxs-lookup"><span data-stu-id="db2ee-105">You can enter the Web address of a report to open it in a browser window independently of a Web application.</span></span> <span data-ttu-id="db2ee-106">該報表會以 HTML 格式開啟，而且其中包含報表工具列，讓您可以在報表中瀏覽頁面或搜尋資料值。</span><span class="sxs-lookup"><span data-stu-id="db2ee-106">The report opens in HTML format and includes the report toolbar so that you can navigate pages or search on data values within the report.</span></span> <span data-ttu-id="db2ee-107">您可以在 URL 上設定參數，以隱藏工具列或選取報表的輸出格式。</span><span class="sxs-lookup"><span data-stu-id="db2ee-107">You can set parameters on the URL to hide the toolbar or select the output format of the report.</span></span>  
  
 <span data-ttu-id="db2ee-108">透過報表的 Web 位址來開啟報表適合檢視報表，但不適合管理報表。</span><span class="sxs-lookup"><span data-stu-id="db2ee-108">Opening a report through its Web address is suitable for viewing a report, but not managing a report.</span></span> <span data-ttu-id="db2ee-109">您無法存取項目的屬性頁或訂閱定義頁面。</span><span class="sxs-lookup"><span data-stu-id="db2ee-109">You cannot access an item's property pages or subscription definition pages.</span></span> <span data-ttu-id="db2ee-110">您必須使用「報表管理員」或 SharePoint 網站處理這些工作。</span><span class="sxs-lookup"><span data-stu-id="db2ee-110">You must use Report Manager or a SharePoint site for those tasks.</span></span>  
  
 <span data-ttu-id="db2ee-111">如果您不知道報表的 Web 位址，您可以開啟報表伺服器的 Web 位址，然後瀏覽報表伺服器的資料夾階層，以選取您要檢視的報表。</span><span class="sxs-lookup"><span data-stu-id="db2ee-111">If you do not know the Web address of a report, you can open the Web address of the report server and then browse the report server folder hierarchy to select the report you want to view.</span></span> <span data-ttu-id="db2ee-112">下圖說明瀏覽器視窗中所顯示的資料夾階層。</span><span class="sxs-lookup"><span data-stu-id="db2ee-112">The following diagram illustrates a folder hierarchy as it appears in a browser window.</span></span>  
  
 <span data-ttu-id="db2ee-113">![瀏覽器中的資料夾](../media/rs-browserfolder.GIF "瀏覽器中的資料夾")</span><span class="sxs-lookup"><span data-stu-id="db2ee-113">![Folders in a browser](../media/rs-browserfolder.GIF "Folders in a browser")</span></span>  
<span data-ttu-id="db2ee-114">瀏覽器中的資料夾</span><span class="sxs-lookup"><span data-stu-id="db2ee-114">Folders in a browser</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db2ee-115">如果您要從手持式裝置存取報表，就必須使用瀏覽器來開啟報表。</span><span class="sxs-lookup"><span data-stu-id="db2ee-115">If you are accessing a report from a handheld device, you must use a browser to open a report.</span></span> <span data-ttu-id="db2ee-116">報表管理員的設計不適用於手持式裝置。</span><span class="sxs-lookup"><span data-stu-id="db2ee-116">Report Manager is not scaled for handheld devices.</span></span>  
  
 <span data-ttu-id="db2ee-117">如需您可以使用之瀏覽器類型的詳細資訊，請參閱《SQL Server 線上叢書》中 [Reporting Services 文件集](https://go.microsoft.com/fwlink/?linkid=121312) 的＜Reporting Services 所支援的瀏覽器類型＞。</span><span class="sxs-lookup"><span data-stu-id="db2ee-117">For more information about types of browsers that you can use, see "Browser Types Supported by Reporting Services" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="navigating-report-server-folders-in-a-web-browser"></a><span data-ttu-id="db2ee-118">在網頁瀏覽器中導覽報表伺服器資料夾</span><span class="sxs-lookup"><span data-stu-id="db2ee-118">Navigating Report Server Folders in a Web Browser</span></span>  
 <span data-ttu-id="db2ee-119">您可以使用網頁瀏覽器來導覽報表伺服器資料夾以及執行報表。</span><span class="sxs-lookup"><span data-stu-id="db2ee-119">You can use a Web browser to navigate report server folders and run reports.</span></span> <span data-ttu-id="db2ee-120">報表和項目在資料夾階層中，會以連結顯示。</span><span class="sxs-lookup"><span data-stu-id="db2ee-120">Reports and items are displayed as links in the folder hierarchy.</span></span> <span data-ttu-id="db2ee-121">您可以按一下連結以開啟報表、資源或資料夾，或檢視共用資料來源的內容。</span><span class="sxs-lookup"><span data-stu-id="db2ee-121">You can click links to open a report, resource, or folder, or view the contents of a shared data source.</span></span> <span data-ttu-id="db2ee-122">若您不知道報表的 URL，則導覽資料夾階層很有用。</span><span class="sxs-lookup"><span data-stu-id="db2ee-122">Navigating the folder hierarchy is useful if you do not know the URL of a report.</span></span> <span data-ttu-id="db2ee-123">您可以指定讓報表伺服器的 Web 位址，使用瀏覽器開啟資料夾階層的根節點連接，然後按一下資料夾的連結來導覽階層。</span><span class="sxs-lookup"><span data-stu-id="db2ee-123">You can specify the report server Web address to open a browser connection at the root node of the folder hierarchy, and then click folder links to navigate through the hierarchy.</span></span>  
  
 <span data-ttu-id="db2ee-124">當您存取報表伺服器的虛擬目錄時，只可以查看您有權存取的資料夾、報表和上傳的項目。</span><span class="sxs-lookup"><span data-stu-id="db2ee-124">When you access a report server virtual directory, you see only the folders, reports, and uploaded items to which you have access.</span></span> <span data-ttu-id="db2ee-125">使用者介面只會顯示資料夾階層和基本資訊，例如個別項目的建立或修改日期、檔案大小和項目類型：</span><span class="sxs-lookup"><span data-stu-id="db2ee-125">The user interface shows only the folder hierarchy and basic information, such as creation or modification date, file size, and item type for individual items:</span></span>  
  
-   <span data-ttu-id="db2ee-126">沒有其他指標的連結就是報表或模型。</span><span class="sxs-lookup"><span data-stu-id="db2ee-126">A link with no other indicator is a report or a model.</span></span>  
  
-   <span data-ttu-id="db2ee-127">標記 \<ds> 表示共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="db2ee-127">The tag \<ds> indicates a shared data source.</span></span>  
  
-   <span data-ttu-id="db2ee-128">標記 \<dir> 表示資料夾專案。</span><span class="sxs-lookup"><span data-stu-id="db2ee-128">The tag \<dir> indicates a folder item.</span></span>  
  
-   <span data-ttu-id="db2ee-129">副檔名代表資源。</span><span class="sxs-lookup"><span data-stu-id="db2ee-129">A file name extension indicates a resource.</span></span> <span data-ttu-id="db2ee-130">副檔名可識別資源的 MIME 類型。</span><span class="sxs-lookup"><span data-stu-id="db2ee-130">The file name extension identifies the MIME type of the resource.</span></span> <span data-ttu-id="db2ee-131">例如，.jpg 代表 JPEG 格式的影像。</span><span class="sxs-lookup"><span data-stu-id="db2ee-131">For example, .jpg indicates an image in JPEG format.</span></span>  
  
## <a name="typing-the-url-address-of-a-report"></a><span data-ttu-id="db2ee-132">輸入報表的 URL 位址</span><span class="sxs-lookup"><span data-stu-id="db2ee-132">Typing the URL Address of a Report</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="db2ee-133">支援對報表伺服器上的特定項目進行 URL 存取。</span><span class="sxs-lookup"><span data-stu-id="db2ee-133">supports URL access to specific items on a report server.</span></span> <span data-ttu-id="db2ee-134">URL 必須包含報表和命令的完整路徑，才能轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="db2ee-134">The URL must include a fully qualified path to the report and commands to render the report.</span></span> <span data-ttu-id="db2ee-135">如果報表包含參數，您也必須指定開啟報表所需的任何值。</span><span class="sxs-lookup"><span data-stu-id="db2ee-135">If the report includes parameters, you must also specify any values that are required to open the report.</span></span> <span data-ttu-id="db2ee-136">如果您要輸入的報表 URL 之路徑、參數值或轉譯延伸模組中含有空格，就必須將 URL 已編碼的字元納入 URL 中，才能獲得預期的結果。</span><span class="sxs-lookup"><span data-stu-id="db2ee-136">If you are typing a URL for a report that includes spaces in the path, parameter values, or a rendering extension, you must incorporate URL encoded characters into the URL to get the results you expect.</span></span> <span data-ttu-id="db2ee-137">下列範例呈現在報表 URL 中的路徑名稱、參數和轉譯延伸模組中含有空格時，所使用的編碼：</span><span class="sxs-lookup"><span data-stu-id="db2ee-137">The following example illustrates a report URL that includes encoding for spaces in the path name, parameters, and a rendering extension:</span></span>  
  
 `http://<Webservername>/reportserver?/<reportfolder>/employee+sales+summary&ReportYear=2004&ReportMonth=06&EmpID=24&rs:Command=Render&rs:Format=HTML4.0`  
  
 <span data-ttu-id="db2ee-138">URL 在 Internet Explorer 中的限制上限為 2,083 個字元。</span><span class="sxs-lookup"><span data-stu-id="db2ee-138">The maximum limit for a URL in Internet Explorer is 2,083 characters.</span></span> <span data-ttu-id="db2ee-139">如需詳細資訊，請參閱 [Internet Explorer 的 URL 長度上限](https://support.microsoft.com/kb/208427)。</span><span class="sxs-lookup"><span data-stu-id="db2ee-139">For more information, see [Maximum URL length in Internet Explorer](https://support.microsoft.com/kb/208427).</span></span>  
  
 <span data-ttu-id="db2ee-140">如需如何透過 URL 存取報表的詳細資訊，包括如何建構 URL 的資訊，請參閱《SQL Server 線上叢書》中 [Reporting Services 文件集](https://go.microsoft.com/fwlink/?linkid=121312) 的＜URL 存取＞。</span><span class="sxs-lookup"><span data-stu-id="db2ee-140">For more information about how to access a report through a URL, including information on how a URL is constructed, see "URL Access" in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db2ee-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db2ee-141">See Also</span></span>  
 [<span data-ttu-id="db2ee-142">在報表管理員中尋找及檢視報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="db2ee-142">Finding and Viewing Reports in Report Manager &#40;Report Builder and SSRS&#41;</span></span>](finding-and-viewing-reports-in-the-web-portal-report-builder-and-ssrs.md)  
  
  
