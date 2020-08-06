---
title: 以 SharePoint 整合模式連接篩選或檔網頁元件 (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Filter Web Part [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
- Documents Web Part [Reporting Services]
ms.assetid: 6a303135-c0ef-44cd-a423-1cea8df3dcf3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5ea7b9f9aba128052ae6ac7f05ef40517eb50e6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593337"
---
# <a name="connect-filter-or-documents-web-part-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="579f5-102">連接篩選或文件網頁組件 (SharePoint 整合模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="579f5-102">Connect Filter or Documents Web Part (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="579f5-103">如果您使用的是 SharePoint 產品，可以建立包含篩選網頁組件或文件網頁組件以及報表檢視器網頁組件的儀表板或網頁組件頁面。</span><span class="sxs-lookup"><span data-stu-id="579f5-103">If you are using a SharePoint product, you can create a dashboard or Web Part Page that includes a Filter Web Part or Documents Web part and a Report Viewer Web Part.</span></span> <span data-ttu-id="579f5-104">支援的版本為 [!INCLUDE[SPF2010](../includes/spf2010-md.md)] 或 [!INCLUDE[SPS2010](../includes/sps2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="579f5-104">Supported versions are [!INCLUDE[SPF2010](../includes/spf2010-md.md)] or [!INCLUDE[SPS2010](../includes/sps2010-md.md)].</span></span> <span data-ttu-id="579f5-105">另外也支援 [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] 或 [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007。</span><span class="sxs-lookup"><span data-stu-id="579f5-105">Also supported are [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] or [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007.</span></span> <span data-ttu-id="579f5-106">藉由連接篩選網頁組件，使用者可以在篩選網頁組件中選取篩選值，並將值傳送到相同頁面上的參數化報表；</span><span class="sxs-lookup"><span data-stu-id="579f5-106">By connecting a Filter Web Part, users who select filter values in a Filter Web Part can send the value to a parameterized report on the same page.</span></span> <span data-ttu-id="579f5-107">藉由連接文件網頁組件，使用者則可在文件庫中按一下報表，並在相鄰的報表檢視器網頁組件中檢視該報表。</span><span class="sxs-lookup"><span data-stu-id="579f5-107">By connecting a Documents Web Part, users who click on reports in the Documents library can view the report in an adjacent Report Viewer Web Part.</span></span>  
  
 <span data-ttu-id="579f5-108">篩選網頁組件可用來將值傳送給報表中的一個或多個參數。</span><span class="sxs-lookup"><span data-stu-id="579f5-108">The Filter Web Part is used to send values to one or more parameters on a report.</span></span> <span data-ttu-id="579f5-109">若要使用篩選網頁組件，報表必須定義與網頁組件傳送之值、資料類型和格式相容的參數。</span><span class="sxs-lookup"><span data-stu-id="579f5-109">To use a Filter Web Part, the report must have parameters defined for it that are compatible with the values, data type, and format sent by the Web Part.</span></span>  
  
 <span data-ttu-id="579f5-110">文件網頁組件與主網站的文件庫相關聯。</span><span class="sxs-lookup"><span data-stu-id="579f5-110">The Documents Web Part is associated with the Documents library of the Home site.</span></span> <span data-ttu-id="579f5-111">若要檢視、新增或移除文件庫中的項目，請按一下 [檢視所有網站內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="579f5-111">To view, add, or remove items from the Documents library, click **View All Site Content**.</span></span> <span data-ttu-id="579f5-112">在 [程式庫] 中按一下 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="579f5-112">In Libraries, click **Documents**.</span></span> <span data-ttu-id="579f5-113">您可以使用 [新增]\*\*\*\*、[上傳]\*\*\*\* 和 [動作]\*\*\*\* 功能表來管理文件庫中的項目。</span><span class="sxs-lookup"><span data-stu-id="579f5-113">You can use the **New**, **Upload**, and **Actions** menu to manage the items in the Documents library.</span></span>  
  
### <a name="to-connect-a-filter-web-part"></a><span data-ttu-id="579f5-114">連接篩選網頁組件</span><span class="sxs-lookup"><span data-stu-id="579f5-114">To connect a Filter Web Part</span></span>  
  
1.  <span data-ttu-id="579f5-115">開啟或建立網頁組件頁面或儀表板。</span><span class="sxs-lookup"><span data-stu-id="579f5-115">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="579f5-116">在 [網站動作]\*\*\*\* 功能表中，按一下 [編輯頁面]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="579f5-116">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="579f5-117">按一下 [**新增網頁元件**]。</span><span class="sxs-lookup"><span data-stu-id="579f5-117">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="579f5-118">在 [**所有 Web 組件**的 [**其他**] 分類中，選取 [ **SQL Server Reporting Services 報表檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="579f5-118">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer**.</span></span>  
  
5.  <span data-ttu-id="579f5-119">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="579f5-119">Click **Add**.</span></span> <span data-ttu-id="579f5-120">Web 組件會加入區域頂端。</span><span class="sxs-lookup"><span data-stu-id="579f5-120">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="579f5-121">在相同網頁元件頁面或儀表板的另一個區域中，按一下 [**新增網頁元件**]。</span><span class="sxs-lookup"><span data-stu-id="579f5-121">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
7.  <span data-ttu-id="579f5-122">在 [**所有 Web 組件**的 [**篩選器**] 區段中，選取 [Web 元件]。</span><span class="sxs-lookup"><span data-stu-id="579f5-122">In **All Web Parts**, in the **Filters** section, select a Web Part.</span></span>  
  
8.  <span data-ttu-id="579f5-123">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="579f5-123">Click **Add**.</span></span> <span data-ttu-id="579f5-124">Web 組件會加入區域頂端。</span><span class="sxs-lookup"><span data-stu-id="579f5-124">The Web Part is added at the top of the zone.</span></span>  
  
9. <span data-ttu-id="579f5-125">在包含網頁元件的區域中，按一下 [網頁元件] [**編輯**] 功能表，指向 [**連接**]，再指向 [**傳送篩選值至**]，然後選取 [**報表檢視器**  -  *報表名稱*]。</span><span class="sxs-lookup"><span data-stu-id="579f5-125">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Send Filter Values To**, and then select **Report Viewer** - *report name*.</span></span>  
  
10. <span data-ttu-id="579f5-126">簽入變更並儲存頁面。</span><span class="sxs-lookup"><span data-stu-id="579f5-126">Check in your changes and save the page.</span></span>  
  
### <a name="to-connect-a-documents-web-part"></a><span data-ttu-id="579f5-127">連接文件網頁組件</span><span class="sxs-lookup"><span data-stu-id="579f5-127">To connect a Documents Web Part</span></span>  
  
1.  <span data-ttu-id="579f5-128">開啟或建立網頁組件頁面或儀表板。</span><span class="sxs-lookup"><span data-stu-id="579f5-128">Open or create the Web Part page or dashboard.</span></span>  
  
2.  <span data-ttu-id="579f5-129">在 [網站動作]\*\*\*\* 功能表中，按一下 [編輯頁面]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="579f5-129">On the **Site Actions** menu, click **Edit Page**.</span></span>  
  
3.  <span data-ttu-id="579f5-130">按一下 [**新增網頁元件**]。</span><span class="sxs-lookup"><span data-stu-id="579f5-130">Click **Add a Web Part**.</span></span>  
  
4.  <span data-ttu-id="579f5-131">在 [**所有 Web 組件**的 [**清單和程式庫**] 區段中，選取 [**檔]。**</span><span class="sxs-lookup"><span data-stu-id="579f5-131">In **All Web Parts**, in the **Lists and Library** section, select **Documents.**</span></span>  
  
5.  <span data-ttu-id="579f5-132">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="579f5-132">Click **Add**.</span></span> <span data-ttu-id="579f5-133">Web 組件會加入區域頂端。</span><span class="sxs-lookup"><span data-stu-id="579f5-133">The Web Part is added at the top of the zone.</span></span>  
  
6.  <span data-ttu-id="579f5-134">按一下工具窗格底部的 [套用]\*\*\*\*，然後按一下 [確定]\*\*\*\* 關閉窗格。</span><span class="sxs-lookup"><span data-stu-id="579f5-134">Click **Apply** at the bottom of the tool pane, and then click **OK** to close the pane.</span></span>  
  
7.  <span data-ttu-id="579f5-135">在相同網頁元件頁面或儀表板的另一個區域中，按一下 [**新增網頁元件**]。</span><span class="sxs-lookup"><span data-stu-id="579f5-135">On another zone in the same Web Part page or dashboard, click **Add a Web Part**.</span></span>  
  
8.  <span data-ttu-id="579f5-136">在 [**所有 Web 組件**的 [**其他**] 分類中，選取 [ **SQL Server Reporting Services 報表檢視器]。**</span><span class="sxs-lookup"><span data-stu-id="579f5-136">In **All Web Parts**, in the **Miscellaneous** category, select **SQL Server Reporting Services Report Viewer.**</span></span>  
  
9. <span data-ttu-id="579f5-137">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="579f5-137">Click **Add**.</span></span> <span data-ttu-id="579f5-138">Web 組件會加入區域頂端。</span><span class="sxs-lookup"><span data-stu-id="579f5-138">The Web Part is added at the top of the zone.</span></span>  
  
10. <span data-ttu-id="579f5-139">在包含網頁元件的區域中，按一下 [網頁元件] [**編輯**] 功能表，指向 [**連接**]，指向 [**取得報表定義來源**]，然後選取 [**檔**]。</span><span class="sxs-lookup"><span data-stu-id="579f5-139">In the zone that contains the Web Part, click the Web Part **edit** menu, point to **Connections**, point to **Get report definitions from**, and then select **Documents**.</span></span>  
  
11. <span data-ttu-id="579f5-140">簽入變更並儲存頁面。</span><span class="sxs-lookup"><span data-stu-id="579f5-140">Check in your changes and save the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="579f5-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="579f5-141">See Also</span></span>  
 <span data-ttu-id="579f5-142">[將報表檢視器 Web 元件加入至 SharePoint 整合模式中的網頁 &#40;Reporting Services&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="579f5-142">[Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="579f5-143">[SharePoint 網站上的報表檢視器 Web 元件](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="579f5-143">[Report Viewer Web Part on a SharePoint Site](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="579f5-144">自訂報表檢視器 Web 組件</span><span class="sxs-lookup"><span data-stu-id="579f5-144">Customize the Report Viewer Web Part</span></span>](../../2014/reporting-services/customize-the-report-viewer-web-part.md)  
  
  
