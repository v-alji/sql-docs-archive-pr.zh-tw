---
title: 發行資料來源與報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing data sources [Reporting Services]
- publishing reports [Reporting Services]
- data sources [Reporting Services], managing
ms.assetid: 3a740f8a-1060-4ec3-938b-2305b6887ebd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 941362afde1cfe5dd3d235c9f243fb17875adadc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687438"
---
# <a name="publishing-data-sources-and-reports"></a><span data-ttu-id="0de3d-102">發行資料來源與報表</span><span class="sxs-lookup"><span data-stu-id="0de3d-102">Publishing Data Sources and Reports</span></span>
  <span data-ttu-id="0de3d-103">發行報表前，您應該預覽報表以查看報表執行時的外觀。</span><span class="sxs-lookup"><span data-stu-id="0de3d-103">Before publishing your report, you should preview the report to see how it will look when it is run.</span></span> <span data-ttu-id="0de3d-104">您可以持續精簡設計，直到您滿意其結果為止。</span><span class="sxs-lookup"><span data-stu-id="0de3d-104">You can continue to refine the design until you are satisfied with the results.</span></span>  
  
 <span data-ttu-id="0de3d-105">設計並測試報表之後，您可能想要與其他人共用該報表。</span><span class="sxs-lookup"><span data-stu-id="0de3d-105">After you design and test your report, you may want to share it with other individuals.</span></span> <span data-ttu-id="0de3d-106">若要共用報表，您必須將其發行或 *「部署」*(Deploy) 至報表伺服器或 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="0de3d-106">To share your report, you need to publish, or *deploy*, it to a report server or SharePoint site.</span></span> <span data-ttu-id="0de3d-107">報表經過發行之後，具備報表伺服器或 SharePoint 網站之權限的使用者都可以執行您的報表。</span><span class="sxs-lookup"><span data-stu-id="0de3d-107">After it has been published, individuals who have permissions to the report server or the SharePoint site can run your report.</span></span> <span data-ttu-id="0de3d-108">此外，具備報表伺服器之管理員權限的使用者可以訂閱報表，讓報表可以定期更新並傳送給使用者。</span><span class="sxs-lookup"><span data-stu-id="0de3d-108">In addition, a person with administrator permissions on the report server can create subscriptions to your report so that the report can be updated and sent to users on a regular schedule.</span></span>  
  
 <span data-ttu-id="0de3d-109">如果您使用共用資料來源來建立報表，您需要將報表發行到與該報表相同的位置。</span><span class="sxs-lookup"><span data-stu-id="0de3d-109">If you used a shared data source to create your report, you need to publish it to the same location as the report.</span></span> <span data-ttu-id="0de3d-110">共用資料來源跟報表一樣，可以在報表伺服器上個別管理。</span><span class="sxs-lookup"><span data-stu-id="0de3d-110">Like reports, shared data sources can be managed separately on the report server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0de3d-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="0de3d-111">In This Section</span></span>  
 [<span data-ttu-id="0de3d-112">預覽報表</span><span class="sxs-lookup"><span data-stu-id="0de3d-112">Previewing Reports</span></span>](previewing-reports.md)  
 <span data-ttu-id="0de3d-113">描述如何在發行報表前進行預覽。</span><span class="sxs-lookup"><span data-stu-id="0de3d-113">Describes how to preview a report before you publish it.</span></span>  
  
 [<span data-ttu-id="0de3d-114">將報表發行至報表伺服器</span><span class="sxs-lookup"><span data-stu-id="0de3d-114">Publishing Reports to a Report Server</span></span>](publishing-reports-to-a-report-server.md)  
 <span data-ttu-id="0de3d-115">描述如何將報表發行到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="0de3d-115">Describes how to publish a report to a report server.</span></span>  
  
 [<span data-ttu-id="0de3d-116">SharePoint 模式在報表伺服器上已發行報表項目的 URL 範例 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0de3d-116">URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;</span></span>](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)  
 <span data-ttu-id="0de3d-117">描述如何將報表發行到 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="0de3d-117">Describes how to publish a report to a SharePoint site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de3d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0de3d-118">See Also</span></span>  
 <span data-ttu-id="0de3d-119">[Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="0de3d-119">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="0de3d-120">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0de3d-120">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="0de3d-121">[頁面配置和轉譯 &#40;報表產生器和 SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0de3d-121">[Page Layout and Rendering &#40;Report Builder and SSRS&#41;](../report-design/page-layout-and-rendering-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0de3d-122">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](../report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0de3d-122">[Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="0de3d-123">[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0de3d-123">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0de3d-124">[匯出報表 &#40;報表產生器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0de3d-124">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="0de3d-125">列印報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0de3d-125">Print Reports &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/print-reports-report-builder-and-ssrs.md)  
  
  
