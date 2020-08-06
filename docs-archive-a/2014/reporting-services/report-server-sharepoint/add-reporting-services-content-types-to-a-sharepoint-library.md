---
title: 將報表檢視器 Web 元件加入至 SharePoint 整合模式中的網頁 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d9b933fad8bc566b3cb0ef04303a85c5f034e620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704877"
---
# <a name="add-the-report-viewer-web-part-to-a-web-page-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="8ea55-102">將報表檢視器 Web 組件加入至網頁 (SharePoint 整合模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="8ea55-102">Add the Report Viewer Web Part to a Web Page (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="8ea55-103">您可以使用報表檢視器 Web 組件來檢視在設定為以 SharePoint 整合模式執行之報表伺服器上執行的報表。</span><span class="sxs-lookup"><span data-stu-id="8ea55-103">You can use the Report Viewer Web Part to view reports that run on report server that is configured to run in SharePoint integrated mode.</span></span> <span data-ttu-id="8ea55-104">您可以使用 Web 組件顯示在報表產生器或報表設計師中建立，並且上傳至文件庫的報表定義 (.rdl) 檔案。</span><span class="sxs-lookup"><span data-stu-id="8ea55-104">You can use the Web Part to display report definition (.rdl) files that you created in Report Builder or Report Designer and uploaded to a library.</span></span>  
  
 <span data-ttu-id="8ea55-105">如果您要在網頁上內嵌報表，您可以將報表檢視器 Web 組件加入至該網頁中。</span><span class="sxs-lookup"><span data-stu-id="8ea55-105">You can add the Report Viewer Web Part to a Web page if you want to embed a report on that page.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ea55-106">雖然它們有相同的名稱，但是透過 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集安裝的報表檢視器 Web 組件，與包含在 RSWebParts.cab 檔案中的報表檢視器 Web 組件不同。</span><span class="sxs-lookup"><span data-stu-id="8ea55-106">Although they have identical names, the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in is different from the Report Viewer Web Part that is included in the RSWebParts.cab file.</span></span> <span data-ttu-id="8ea55-107">本主題中的指示是特別針對透過 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集安裝的報表檢視器 Web 組件。</span><span class="sxs-lookup"><span data-stu-id="8ea55-107">The instructions in this topic are specifically for the Report Viewer Web Part that is installed through the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.</span></span>  
  
 <span data-ttu-id="8ea55-108">若要將 Web 組件加入至網頁中，您必須在網站層級，擁有「新增並自訂頁面」權限。</span><span class="sxs-lookup"><span data-stu-id="8ea55-108">To add a Web Part to a Web page, you must have the Add and Customize Pages permission at the site level.</span></span> <span data-ttu-id="8ea55-109">如果您要使用預設的安全性設定，此權限會授與具備「完整控制」等級之權限的**擁有者**群組成員。</span><span class="sxs-lookup"><span data-stu-id="8ea55-109">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission.</span></span>  
  
### <a name="to-embed-a-report-in-a-web-page"></a><span data-ttu-id="8ea55-110">在網頁中內嵌報表</span><span class="sxs-lookup"><span data-stu-id="8ea55-110">To embed a report in a Web page</span></span>  
  
1.  <span data-ttu-id="8ea55-111">開啟或建立網頁組件頁面或儀表板。</span><span class="sxs-lookup"><span data-stu-id="8ea55-111">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="8ea55-112">在 [網站動作]\*\*\*\* 中，按一下 [編輯頁面]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ea55-112">On **Site Actions**, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="8ea55-113">按一下 [**新增網頁元件**]。</span><span class="sxs-lookup"><span data-stu-id="8ea55-113">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="8ea55-114">在網頁組件類別目錄的清單中，選取 [其他]\*\*\*\* 類別目錄，然後選取 [SQL Server Reporting Services 報表檢視器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ea55-114">In the list of web part categories, select the **Miscellaneous** category, and then select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="8ea55-115">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="8ea55-115">Click **Add**.</span></span> <span data-ttu-id="8ea55-116">Web 組件會加入區域頂端。</span><span class="sxs-lookup"><span data-stu-id="8ea55-116">The Web Part is added at the top of the zone.</span></span> <span data-ttu-id="8ea55-117">您可將它拖曳至該區域中的其他位置。</span><span class="sxs-lookup"><span data-stu-id="8ea55-117">You can drag it to a different location in the zone.</span></span>  
  
6.  <span data-ttu-id="8ea55-118">在檢視器中，按一下 [請按這裡開啟工具窗格]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ea55-118">Within the viewer, click **Click here to open the tool pane**.</span></span>  
  
7.  <span data-ttu-id="8ea55-119">按一下瀏覽 ([...]\*\*\*\*) 按鈕，選取目前網站集合中任意文件庫的報表。</span><span class="sxs-lookup"><span data-stu-id="8ea55-119">Select a report from any library in the current site collection by clicking the browse (**...**) button.</span></span> <span data-ttu-id="8ea55-120">您也可以輸入報表的 URL。</span><span class="sxs-lookup"><span data-stu-id="8ea55-120">You can also type the report URL.</span></span> <span data-ttu-id="8ea55-121">若要判斷任何報表的 URL，請以滑鼠右鍵按一下報表，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8ea55-121">To determine the URL for any report, right-click the report and select **Properties**.</span></span> <span data-ttu-id="8ea55-122">請勿按報表旁邊的向下箭號，因為在項目的 [檢視屬性] 頁面中不會指示報表 URL。</span><span class="sxs-lookup"><span data-stu-id="8ea55-122">Do not click the down arrow next to the report; the report URL is not indicated in the View Properties page of the item.</span></span> <span data-ttu-id="8ea55-123">如果您從 [屬性]\*\*\*\* 對話方塊複製並貼上 URL，請將 "%20" URL 編碼取代為空格 (例如，"Company%20Sales" 應該是 "Company Sales")。</span><span class="sxs-lookup"><span data-stu-id="8ea55-123">If you copy and paste the URL from the **Properties** dialog box, replace the "%20" URL encoding with a space (for example, "Company%20Sales" should be "Company Sales").</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ea55-124">每一個報表檢視器 Web 組件都包含單一報表。</span><span class="sxs-lookup"><span data-stu-id="8ea55-124">Each Report Viewer Web Part contains a single report.</span></span> <span data-ttu-id="8ea55-125">URL 必須是完整的路徑，指向位於目前的 SharePoint 網站，或是位於相同 Web 應用程式或伺服陣列內之網站的報表。</span><span class="sxs-lookup"><span data-stu-id="8ea55-125">The URL must be the fully qualified path to a report that is on the current SharePoint site, or on a site within the same Web application or farm.</span></span> <span data-ttu-id="8ea55-126">URL 必須解析為文件庫，或包含該報表之文件庫內的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8ea55-126">The URL must resolve to a document library or to a folder within a document library that contains the report.</span></span> <span data-ttu-id="8ea55-127">報表 URL 必須包括副檔名 .rdl。</span><span class="sxs-lookup"><span data-stu-id="8ea55-127">The report URL must include the .rdl file extension.</span></span> <span data-ttu-id="8ea55-128">如果報表是根據模型或共用資料來源檔案，則不需要在 URL 中指定這些檔案。</span><span class="sxs-lookup"><span data-stu-id="8ea55-128">If the report depends on a model or shared data source files, you do not need to specify those files in the URL.</span></span> <span data-ttu-id="8ea55-129">報表會包含所需的檔案參考。</span><span class="sxs-lookup"><span data-stu-id="8ea55-129">The report contains references to the files it needs.</span></span>  
  
8.  <span data-ttu-id="8ea55-130">在工具窗格開啟時，可以設定屬性以修改預設的外觀和配置。</span><span class="sxs-lookup"><span data-stu-id="8ea55-130">While the tool pane is open, you can set properties to modify the default appearance and layout.</span></span>  
  
9. <span data-ttu-id="8ea55-131">按一下工具窗格底部的 [套用]\*\*\*\*，然後按一下 [確定]\*\*\*\* 關閉窗格。</span><span class="sxs-lookup"><span data-stu-id="8ea55-131">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea55-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ea55-132">See Also</span></span>  
 <span data-ttu-id="8ea55-133">[SharePoint 網站上的報表檢視器 Web 元件](../report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="8ea55-133">[Report Viewer Web Part on a SharePoint Site](../report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="8ea55-134">[自訂報表檢視器 Web 元件](../customize-the-report-viewer-web-part.md) </span><span class="sxs-lookup"><span data-stu-id="8ea55-134">[Customize the Report Viewer Web Part](../customize-the-report-viewer-web-part.md) </span></span>  
 <span data-ttu-id="8ea55-135">[授與 SharePoint 網站上報表伺服器專案的許可權](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="8ea55-135">[Granting Permissions on Report Server Items on a SharePoint Site](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="8ea55-136">安裝或卸載適用于 SharePoint &#40;SharePoint 2010 和 SharePoint 2013 的 Reporting Services 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="8ea55-136">Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
