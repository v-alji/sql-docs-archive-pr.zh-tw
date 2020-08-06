---
title: 將報表發行至 SharePoint 文件庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23b74ffb04bf1e13523dcf6ec5d774089d80f73b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687449"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a><span data-ttu-id="cc568-102">將報表發行到 SharePoint 文件庫</span><span class="sxs-lookup"><span data-stu-id="cc568-102">Publish a Report to a SharePoint Library</span></span>
  <span data-ttu-id="cc568-103">若要將報表發行至有設定 SharePoint 整合的 SharePoint 網站，您必須在報表設計師中設定專案屬性。</span><span class="sxs-lookup"><span data-stu-id="cc568-103">To publish a report to a SharePoint site configured for SharePoint integration, you must set the project properties in Report Designer.</span></span> <span data-ttu-id="cc568-104">在專案屬性中，伺服器、報表和共用資料來源的所有參考都必須是完整 URL。</span><span class="sxs-lookup"><span data-stu-id="cc568-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span> <span data-ttu-id="cc568-105">在報表定義中，子報表、鑽研報表和資源 (如網路架構影像) 的所有參考都必須是完整 URLS。</span><span class="sxs-lookup"><span data-stu-id="cc568-105">In the report definition, all references to subreports, drillthrough reports, and resources such as Web-based images, must be fully qualified URLS.</span></span>  
  
 <span data-ttu-id="cc568-106">您在 SharePoint 網站上必須具有「 **成員** 」或「 **擁有者** 」權限才能設定專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="cc568-106">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span> <span data-ttu-id="cc568-107">如需詳細資訊，請參閱 [SharePoint 模式在報表伺服器上已發行報表項目的 URL 範例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="cc568-107">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a><span data-ttu-id="cc568-108">將報表發行至 SharePoint 網站</span><span class="sxs-lookup"><span data-stu-id="cc568-108">To publish a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="cc568-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟現有或新的報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="cc568-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open an existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="cc568-110">在 **[專案]** 功能表按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="cc568-110">From the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="cc568-111">[ _\<project>_ **屬性頁**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="cc568-111">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="cc568-112">在 **[組態]** 清單中，選取用來建立及發行報表的方案組建組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="cc568-112">In the **Configuration** list, select the name of a solution build configuration to use to build and publish your report.</span></span> <span data-ttu-id="cc568-113">目前的設定列為**Active** (*\<configuration>*) 。</span><span class="sxs-lookup"><span data-stu-id="cc568-113">The current configuration is listed as **Active**(*\<configuration>*).</span></span>  
  
4.  <span data-ttu-id="cc568-114">如果您想要發行專案中的共用資料來源，並覆寫之前發行的共用資料來源，請將 **OverwriteDataSources** 設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="cc568-114">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="cc568-115"> (**TargetDataSourceFolder**的選擇性) ，請輸入 SharePoint 文件庫或文件庫資料夾的 URL (例如 *http://TestServer/TestSite/Documents/DataSources)* 。</span><span class="sxs-lookup"><span data-stu-id="cc568-115">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder (for example, *http://TestServer/TestSite/Documents/DataSources)*.</span></span>  
  
     <span data-ttu-id="cc568-116">如果您未指定值，則會使用 **TargetReportFolder** 值。</span><span class="sxs-lookup"><span data-stu-id="cc568-116">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="cc568-117">針對 [ **TargetReportFolder**]，輸入文件庫或文件庫資料夾的 URL (例如， *http://TestServer/TestSite/Documents/Reports)* 。</span><span class="sxs-lookup"><span data-stu-id="cc568-117">For **TargetReportFolder**, type a URL to a library or library folder (for example, *http://TestServer/TestSite/Documents/Reports)*.</span></span>  
  
7.  <span data-ttu-id="cc568-118">為 **TargetServerURL**輸入 SharePoint 頂層網站或子網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="cc568-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="cc568-119">如果您未指定網站，則會使用預設的頂層網站 (例如，、 *http://servername* *http://servername/site* 或 *http://servername/site/subsite*) 。</span><span class="sxs-lookup"><span data-stu-id="cc568-119">If you do not specify a site, the default top-level site is used (for example, *http://servername*, *http://servername/site*, or *http://servername/site/subsite*).</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="cc568-120">在方案總管中，以滑鼠右鍵按一下要發行的報表，然後按一下 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cc568-120">In Solution Explorer, right-click the report you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="cc568-121">報表便會發行至 **[TargetReportFolder]** 中所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="cc568-121">The report is published to the location specified in **TargetReportFolder**.</span></span> <span data-ttu-id="cc568-122">此時，部署錯誤會出現在 [輸出] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="cc568-122">Deployment errors appear in the Output window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc568-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc568-123">See Also</span></span>  
 <span data-ttu-id="cc568-124">[專案屬性頁對話方塊](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="cc568-124">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="cc568-125">[將部署屬性設定 &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="cc568-125">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="cc568-126">[將報表發行至報表伺服器](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="cc568-126">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="cc568-127">[SharePoint 模式中報表伺服器上已發行報表專案的 URL 範例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="cc568-127">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 [<span data-ttu-id="cc568-128">搭配報表使用 Office 資料連接 &#40;.odc&#41; &#40;SharePoint 整合模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cc568-128">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
