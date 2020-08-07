---
title: 在 [管理中心] 中建立 PowerPivot 網站的信任位置 |Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
author: minewiskan
ms.author: owend
ms.openlocfilehash: 70b1317db7ce413f3a593056f3b8a140b3bdc446
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598574"
---
# <a name="create-a-trusted-location-for-powerpivot-sites-in-central-administration"></a><span data-ttu-id="963a4-102">Create a trusted location for PowerPivot sites in Central Administration</span><span class="sxs-lookup"><span data-stu-id="963a4-102">Create a trusted location for PowerPivot sites in Central Administration</span></span>
  <span data-ttu-id="963a4-103">Excel Services 可讓您指定哪些位置對於在 SharePoint 伺服器上開啟的活頁簿而言是有效的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="963a4-103">Excel Services lets you specify which locations are valid repositories for workbooks that you open on a SharePoint server.</span></span> <span data-ttu-id="963a4-104">這些位置稱為「信任位置」，而且您可以針對每個建立的信任位置使用不同的組態設定。</span><span class="sxs-lookup"><span data-stu-id="963a4-104">These locations are called 'trusted locations', and you can use different configuration settings for each trusted location you create.</span></span> <span data-ttu-id="963a4-105">對於 PowerPivot for SharePoint 部署，您可以考慮針對包含 PowerPivot 活頁簿的網站建立信任位置，讓您可以套用最適合 PowerPivot 資料存取的設定，同時針對其餘的伺服陣列保留預設值。</span><span class="sxs-lookup"><span data-stu-id="963a4-105">For a deployment of PowerPivot for SharePoint, you might consider creating a trusted location for sites that contain PowerPivot workbooks so that you can apply the settings that work best for PowerPivot data access, while preserving default settings for the rest of the farm.</span></span>  
  
  
  
## <a name="prerequisites"></a><span data-ttu-id="963a4-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="963a4-106">Prerequisites</span></span>  
 <span data-ttu-id="963a4-107">您必須是伺服陣列管理員或服務管理員，才能將 URL 指定為信任位置。</span><span class="sxs-lookup"><span data-stu-id="963a4-107">You must be a farm or service administrator to designate a URL as a trusted location.</span></span>  
  
 <span data-ttu-id="963a4-108">您必須知道包含 PowerPivot 圖庫或儲存活頁簿之其他文件庫的 SharePoint 網站之 URL 位址。</span><span class="sxs-lookup"><span data-stu-id="963a4-108">You must know the URL address of the SharePoint site that contains the PowerPivot Gallery or other library that stores your workbooks.</span></span> <span data-ttu-id="963a4-109">若要取得位址，請開啟包含文件庫的網站，以滑鼠右鍵按一下 [ **PowerPivot 圖庫**]，選取 [**屬性**]，然後複製包含伺服器名稱和網站路徑之位址 (URL) 的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="963a4-109">To get the address, open the site that contains the library, right-click **PowerPivot Gallery**, select **Properties**, and then copy the first part of the Address (URL) that contains the server name and site path.</span></span>  
  
##  <a name="overview"></a><a name="overview"></a> <span data-ttu-id="963a4-110">概觀</span><span class="sxs-lookup"><span data-stu-id="963a4-110">Overview</span></span>  
 <span data-ttu-id="963a4-111">一開始安裝 Excel Services 時，會指定 'http://' 做為其信任位置，也就是說，來自伺服陣列之任何網站的活頁簿都可以在伺服器上開啟。</span><span class="sxs-lookup"><span data-stu-id="963a4-111">An initial installation of Excel Services specifies 'http://' as its trusted location, which means that workbooks from any site in the farm can be opened on the server.</span></span> <span data-ttu-id="963a4-112">如果您需要更嚴格控制視為值得信任的位置，您可以建立對應到伺服陣列中特定網站的新信任位置，然後針對每個位置變更設定與權限。</span><span class="sxs-lookup"><span data-stu-id="963a4-112">If you require tighter control over which locations are considered trustworthy, you can create new trusted locations that map to specific sites in your farm, and then vary the settings and permissions for each one.</span></span>  
  
 <span data-ttu-id="963a4-113">如果您想要針對其餘的伺服陣列保留預設值，同時套用對 PowerPivot 資料存取最有效的不同設定，針對主控 PowerPivot 活頁簿的網站建立新的信任位置將會很實用。</span><span class="sxs-lookup"><span data-stu-id="963a4-113">Creating a new trusted location for sites that host PowerPivot workbooks is especially useful if you want to preserve default values for the rest of the farm, while applying different settings that work best for PowerPivot data access.</span></span> <span data-ttu-id="963a4-114">例如，針對 PowerPivot 活頁簿最佳化之信任位置的活頁簿大小上限為 50 MB，而其餘伺服陣列則使用預設值 10MB。</span><span class="sxs-lookup"><span data-stu-id="963a4-114">For example, a trusted location that is optimized for PowerPivot workbooks could have a maximum workbook size of 50 MB, while the rest of the farm uses the default value of 10MB.</span></span>  
  
 <span data-ttu-id="963a4-115">如果您使用 PowerPivot 圖庫文件庫來預覽發行的活頁簿，而且您遇到資料重新整理警告而不是您所預期的預覽影像，建議您建立信任的位置。</span><span class="sxs-lookup"><span data-stu-id="963a4-115">Creating a trusted location is recommended if you are using PowerPivot Gallery libraries to preview published workbooks and you encounter data refresh warnings instead of the preview image you expect.</span></span> <span data-ttu-id="963a4-116">PowerPivot 圖庫使用文件中的資料和簡報資訊，來轉譯報表和活頁簿的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="963a4-116">PowerPivot Gallery renders thumbnail images of reports and workbooks using data and presentation information within the document.</span></span> <span data-ttu-id="963a4-117">如果為信任位置啟用資料重新整理時警告，則 PowerPivot 圖庫可能沒有足夠的權限來執行重新整理，這將會造成顯示錯誤，而不是顯示縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="963a4-117">If Warn on Data Refresh is enabled for a trusted location, PowerPivot Gallery might not have sufficient permissions to perform the refresh, causing an error to appear instead of the thumbnail image.</span></span> <span data-ttu-id="963a4-118">加入包含 PowerPivot 圖庫的網站做為新的信任位置可以排除這個問題。</span><span class="sxs-lookup"><span data-stu-id="963a4-118">Adding a site that contains PowerPivot Gallery as a new trusted location can eliminate this problem.</span></span>  
  
##  <a name="create-a-trusted-location-for-powerpivot-data-access"></a><a name="create"></a><span data-ttu-id="963a4-119">建立 PowerPivot 資料存取的信任位置</span><span class="sxs-lookup"><span data-stu-id="963a4-119">Create a Trusted Location for PowerPivot Data Access</span></span>  
  
1.  <span data-ttu-id="963a4-120">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="963a4-120">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="963a4-121">按一下 [Excel Services 服務應用程式]。</span><span class="sxs-lookup"><span data-stu-id="963a4-121">Click the Excel Services Service Application.</span></span>  
  
3.  <span data-ttu-id="963a4-122">按一下 [信任的檔案位置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="963a4-122">Click **Trusted File Locations**.</span></span>  
  
4.  <span data-ttu-id="963a4-123">按一下 [新增信任的檔案位置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="963a4-123">Click **Add Trusted File Location**.</span></span>  
  
5.  <span data-ttu-id="963a4-124">輸入包含 PowerPivot 圖庫文件庫之網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="963a4-124">Enter the URL of a site that contains a PowerPivot Gallery library.</span></span>  
  
6.  <span data-ttu-id="963a4-125">在 [位置類型] 中，選取 [Microsoft SharePoint Foundation]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="963a4-125">In Location Type, select **Microsoft SharePoint Foundation**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="963a4-126">PowerPivot 資料存取不支援 UNC 和 HTTP 位置類型。</span><span class="sxs-lookup"><span data-stu-id="963a4-126">UNC and HTTP location types are not supported for PowerPivot data access.</span></span>  
  
7.  <span data-ttu-id="963a4-127">接受 [工作階段管理]、[活頁簿內容] 及 [計算方式] 中屬性的所有預設值。</span><span class="sxs-lookup"><span data-stu-id="963a4-127">Accept all of the default settings for properties in Session Management, Workbook Properties, and Calculation Behavior.</span></span>  
  
8.  <span data-ttu-id="963a4-128">在 [活頁簿內容] 中，將 [最大活頁簿大小]\*\*\*\* 設定為 **50**。</span><span class="sxs-lookup"><span data-stu-id="963a4-128">In Workbook Properties, set **Maximum Workbook Size** to **50**.</span></span> <span data-ttu-id="963a4-129">這樣會將活頁簿檔案大小的上限對齊父 Web 應用程式的檔案上傳上限。</span><span class="sxs-lookup"><span data-stu-id="963a4-129">This aligns the upper limit for workbook file size to the upper limit for file uploads to the parent web application.</span></span> <span data-ttu-id="963a4-130">如果您的活頁簿大於 50 MB，您必須進一步增加檔案大小的限制。</span><span class="sxs-lookup"><span data-stu-id="963a4-130">If your workbooks are larger than 50 megabytes, you must further increase the file size limit.</span></span> <span data-ttu-id="963a4-131">如需詳細資訊，請參閱[設定最大檔案上傳大小 &#40;PowerPivot for SharePoint&#41;](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="963a4-131">For more information, see [Configure Maximum File Upload Size &#40;PowerPivot for SharePoint&#41;](configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).</span></span>  
  
9. <span data-ttu-id="963a4-132">在 [外部資料] 中，請確認 [允許外部資料] 設定為 [信任的資料連線庫與內嵌連線]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="963a4-132">In External Data, verify that Allow External Data is set to **Trusted data connection libraries and embedded**.</span></span> <span data-ttu-id="963a4-133">活頁簿中的 PowerPivot 資料存取需要這項設定。</span><span class="sxs-lookup"><span data-stu-id="963a4-133">This setting is required for PowerPivot data access in a workbook.</span></span>  
  
10. <span data-ttu-id="963a4-134">此外，請在 [外部資料] 的 [重新整理時警告] 中，清除 [啟用重新整理警告]\*\*\*\* 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="963a4-134">Also in External Data, for Warn on Refresh, clear the checkbox for **Refresh warning enabled**.</span></span> <span data-ttu-id="963a4-135">清除此核取方塊可讓 PowerPivot 圖庫略過例行的警告訊息，並改為顯示活頁簿的預覽影像。</span><span class="sxs-lookup"><span data-stu-id="963a4-135">Clearing the checkbox allows PowerPivot Gallery to bypass routine warning messages and show preview images of a workbook instead.</span></span>  
  
11. <span data-ttu-id="963a4-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="963a4-136">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963a4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="963a4-137">See Also</span></span>  
 [<span data-ttu-id="963a4-138">PowerPivot 圖庫</span><span class="sxs-lookup"><span data-stu-id="963a4-138">PowerPivot Gallery</span></span>](../../index.yml)  
 <span data-ttu-id="963a4-139">[建立和自訂 PowerPivot 圖庫](create-and-customize-power-pivot-gallery.md) </span><span class="sxs-lookup"><span data-stu-id="963a4-139">[Create and Customize PowerPivot Gallery](create-and-customize-power-pivot-gallery.md) </span></span>  
 [<span data-ttu-id="963a4-140">使用 PowerPivot 圖庫</span><span class="sxs-lookup"><span data-stu-id="963a4-140">Use PowerPivot Gallery</span></span>](use-power-pivot-gallery.md)  
  
  
