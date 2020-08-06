---
title: 將共用資料來源發行至 SharePoint 文件庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], publishing to a SharePoint library
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77ee25535ccb98638ae02ca64e3bcbfc88291c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687445"
---
# <a name="publish-a-shared-data-source-to-a-sharepoint-library"></a><span data-ttu-id="a825d-102">將共用資料來源發行至 SharePoint 文件庫</span><span class="sxs-lookup"><span data-stu-id="a825d-102">Publish a Shared Data Source to a SharePoint Library</span></span>
  <span data-ttu-id="a825d-103">若要將共用資料來源發行到以 SharePoint 整合模式執行的報表伺服器，您必須在報表設計師中設定報表專案屬性。</span><span class="sxs-lookup"><span data-stu-id="a825d-103">To publish a shared data source to a report server that is running in SharePoint integrated mode, you must set the report project properties in Report Designer.</span></span> <span data-ttu-id="a825d-104">在專案屬性中，伺服器、報表和共用資料來源的所有參考都必須是完整 URL。</span><span class="sxs-lookup"><span data-stu-id="a825d-104">In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.</span></span>  
  
 <span data-ttu-id="a825d-105">您必須擁有 SharePoint 網站的**成員**或**擁有者**權限。</span><span class="sxs-lookup"><span data-stu-id="a825d-105">You must have **Member** or **Owner** permission on the SharePoint site.</span></span> <span data-ttu-id="a825d-106">如需詳細資訊，請參閱 [SharePoint 模式在報表伺服器上已發行報表項目的 URL 範例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a825d-106">For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).</span></span>  
  
### <a name="to-publish-a-shared-data-source-to-a-sharepoint-site"></a><span data-ttu-id="a825d-107">將共用資料來源發行到 SharePoint 網站</span><span class="sxs-lookup"><span data-stu-id="a825d-107">To publish a shared data source to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="a825d-108">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟現有或新的報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="a825d-108">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open your existing or new Report Server project.</span></span>  
  
2.  <span data-ttu-id="a825d-109">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a825d-109">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="a825d-110">[ _\<project>_ **屬性頁**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a825d-110">The _\<project>_**Property Pages** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="a825d-111">選擇您用來發行至 SharePoint 網站的 [組態]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a825d-111">Choose the **Configuration** you use to publish to a SharePoint site.</span></span>  
  
4.  <span data-ttu-id="a825d-112">如果您想要發行專案中的共用資料來源，並覆寫之前發行的共用資料來源，請將 **OverwriteDataSources** 設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="a825d-112">If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.</span></span>  
  
5.  <span data-ttu-id="a825d-113">(選擇性) 為 **TargetDataSourceFolder**輸入 SharePoint 文件庫或文件庫資料夾的 URL。</span><span class="sxs-lookup"><span data-stu-id="a825d-113">(Optional) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder.</span></span> <span data-ttu-id="a825d-114">例如： *http://TestServer/TestSite/Documents/DataSources* 。</span><span class="sxs-lookup"><span data-stu-id="a825d-114">For example, *http://TestServer/TestSite/Documents/DataSources*.</span></span>  
  
     <span data-ttu-id="a825d-115">如果您未指定值，則會使用 **TargetReportFolder** 值。</span><span class="sxs-lookup"><span data-stu-id="a825d-115">If you do not specify a value, the **TargetReportFolder** value is used.</span></span>  
  
6.  <span data-ttu-id="a825d-116">為 **TargetReportFolder**輸入文件庫或文件庫資料夾的 URL。</span><span class="sxs-lookup"><span data-stu-id="a825d-116">For **TargetReportFolder**, type a URL to a library or library folder.</span></span> <span data-ttu-id="a825d-117">例如，http:*//TestServer/TestSite/Documents/Reports*。</span><span class="sxs-lookup"><span data-stu-id="a825d-117">For example, http:*//TestServer/TestSite/Documents/Reports*.</span></span>  
  
7.  <span data-ttu-id="a825d-118">為 **TargetServerURL**輸入 SharePoint 頂層網站或子網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="a825d-118">For **TargetServerURL**, type a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="a825d-119">若未指定網站，則會使用預設的最上層網站。</span><span class="sxs-lookup"><span data-stu-id="a825d-119">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="a825d-120">例如，http://*servername*、http://*servername*/*site*或 http://*servername*/*site*/*subsite*。</span><span class="sxs-lookup"><span data-stu-id="a825d-120">For example, http://*servername*, http://*servername*/*site*, or http://*servername*/*site*/*subsite*.</span></span>  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="a825d-121">在方案總管中，以滑鼠右鍵按一下您要發行的共用資料來源，然後按一下 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a825d-121">In Solution Explorer, right-click the shared data source you want to publish, and click **Deploy**.</span></span> <span data-ttu-id="a825d-122">資料來源便會發行到 **TargetDataSourceFolder**中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="a825d-122">The data source is published to the location specified in **TargetDataSourceFolder**.</span></span> <span data-ttu-id="a825d-123">此時，部署錯誤會出現在 [輸出] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="a825d-123">Deployment errors appear in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a825d-124">當您將共用資料來源發行到 SharePoint 網站時，副檔名會變更為 .rsds。</span><span class="sxs-lookup"><span data-stu-id="a825d-124">After you publish a shared data source to a SharePoint site, the file name extension is changed to .rsds.</span></span> <span data-ttu-id="a825d-125">您可以直接在 SharePoint 網站上編輯及管理共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="a825d-125">You can edit and manage a shared data source directly on the SharePoint site.</span></span> <span data-ttu-id="a825d-126">如需詳細資訊，請參閱[建立及管理共用資料來源 &#40;SharePoint 整合模式的 Reporting Services&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="a825d-126">For more information, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a825d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a825d-127">See Also</span></span>  
 <span data-ttu-id="a825d-128">[將報表發行至 SharePoint 文件庫](publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="a825d-128">[Publish a Report to a SharePoint Library](publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="a825d-129">[SharePoint 模式中報表伺服器上已發行報表專案的 URL 範例 &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="a825d-129">[URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="a825d-130">[專案屬性頁對話方塊](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="a825d-130">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="a825d-131">[將部署屬性設定 &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a825d-131">[Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md) </span></span>  
 <span data-ttu-id="a825d-132">[將報表發行至報表伺服器](publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="a825d-132">[Publishing Reports to a Report Server](publishing-reports-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="a825d-133">搭配報表使用 Office 資料連接 &#40;.odc&#41; &#40;SharePoint 整合模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a825d-133">Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
