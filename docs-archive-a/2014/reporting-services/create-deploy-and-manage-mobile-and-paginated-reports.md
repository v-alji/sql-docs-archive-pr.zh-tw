---
title: Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services]
- SSRS
- reports [Reporting Services], about reports
- Reporting Services
- SQL Server Reporting Services
ms.assetid: b8d18d3d-9db0-43e7-8286-7b46cc3a37ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0418acaab54032148f4bc6d42d06c97070b89e1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686848"
---
# <a name="reporting-services-ssrs"></a><span data-ttu-id="9d340-102">Reporting Services (SSRS)</span><span class="sxs-lookup"><span data-stu-id="9d340-102">Reporting Services (SSRS)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="9d340-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]提供完整的現成工具和服務，協助您建立、部署及管理組織的報告。</span><span class="sxs-lookup"><span data-stu-id="9d340-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides a full range of ready-to-use tools and services to help you create, deploy, and manage reports for your organization.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="9d340-104">包含可讓您擴充和自訂報表功能的程式設計功能。</span><span class="sxs-lookup"><span data-stu-id="9d340-104">includes programming features that enable you to extend and customize your reporting functionality.</span></span>

 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="9d340-105">是以伺服器為基礎的報告平臺，可針對各種資料來源提供完整的報告功能。</span><span class="sxs-lookup"><span data-stu-id="9d340-105">is a server-based reporting platform that provides comprehensive reporting functionality for a variety of data sources.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="9d340-106">包括一組完整的工具，可讓您建立、管理和傳遞報表，以及可讓開發人員在自訂應用程式中整合或擴充資料和報表處理的 Api。</span><span class="sxs-lookup"><span data-stu-id="9d340-106">includes a complete set of tools for you to create, manage, and deliver reports, and APIs that enable developers to integrate or extend data and report processing in custom applications.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="9d340-107">工具會在環境中工作 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，並與 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 工具和元件完全整合。</span><span class="sxs-lookup"><span data-stu-id="9d340-107">tools work within the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environment and are fully integrated with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tools and components.</span></span>

 <span data-ttu-id="9d340-108">您可以使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]，從關聯式、多維度或以 XML 為基礎的資料來源，建立互動式、表格式、圖形或自由形式報表。</span><span class="sxs-lookup"><span data-stu-id="9d340-108">With [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], you can create interactive, tabular, graphical, or free-form reports from relational, multidimensional, or XML-based data sources.</span></span> <span data-ttu-id="9d340-109">報表可以包含豐富的資料視覺效果，包括圖表、地圖和走勢圖。</span><span class="sxs-lookup"><span data-stu-id="9d340-109">Reports can include rich data visualization, including charts, maps, and sparklines.</span></span> <span data-ttu-id="9d340-110">您可以發行報表、排程報表處理，或是視需要存取報表。</span><span class="sxs-lookup"><span data-stu-id="9d340-110">You can publish reports, schedule report processing, or access reports on-demand.</span></span> <span data-ttu-id="9d340-111">您可以從各種檢視格式進行選取、將報表匯出到其他應用程式 (例如 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)])，以及訂閱已發行的報表。</span><span class="sxs-lookup"><span data-stu-id="9d340-111">You can select from a variety of viewing formats, export reports to other applications such as [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)], and subscribe to published reports.</span></span> <span data-ttu-id="9d340-112">您所建立的報表可透過以 Web 為基礎的連接進行檢視，或是當做 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 應用程式或 SharePoint 網站的一部分進行檢視。</span><span class="sxs-lookup"><span data-stu-id="9d340-112">The reports that you create can be viewed over a Web-based connection or as part of a [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows application or SharePoint site.</span></span> <span data-ttu-id="9d340-113">您也可以在發行到 SharePoint 網站的報表上建立資料警示，並在報表資料變更時，接收電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="9d340-113">You can also create data alerts on reports published to a SharePoint site and receive email messages when report data changes.</span></span>

 <span data-ttu-id="9d340-114">如需中新功能的詳細資訊 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，請參閱[什麼是新的 &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9d340-114">For more information about features new in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [What's New &#40;Reporting Services&#41;](../../2014/reporting-services/what-s-new-reporting-services.md).</span></span>

 <span data-ttu-id="9d340-115">如需有關其他 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 元件、工具和資源的詳細資訊，請參閱《 [SQL Server 線上叢書](../index.yml)》。</span><span class="sxs-lookup"><span data-stu-id="9d340-115">For information about other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] components, tools, and resources, see [SQL Server Books Online](../index.yml).</span></span>

 <span data-ttu-id="9d340-116">**依區域資料夾流覽內容**![圖示](media/hlp-16folder.gif "資料夾圖示") [Reporting Services 報表伺服器](../../2014/reporting-services/reporting-services-report-server.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-116">**Browse Content by Area** ![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Report Server](../../2014/reporting-services/reporting-services-report-server.md)</span></span>

 <span data-ttu-id="9d340-117">[&#40;SSRS Reporting Services 報表](reports/reporting-services-reports-ssrs.md)的![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")&#41;</span><span class="sxs-lookup"><span data-stu-id="9d340-117">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Reports &#40;SSRS&#41;](reports/reporting-services-reports-ssrs.md)</span></span>

 <span data-ttu-id="9d340-118">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")[報表資料 &#40;SSRS&#41;](report-data/report-data-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-118">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Data &#40;SSRS&#41;](report-data/report-data-ssrs.md)</span></span>

 <span data-ttu-id="9d340-119">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")[報表參數 &#40;報表產生器和報表設計師&#41;](report-design/report-parameters-report-builder-and-report-designer.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-119">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md)</span></span>

 <span data-ttu-id="9d340-120">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")[報表報表設計師 &#40;SSRS 中的元件&#41;](report-design/report-parts-in-report-designer-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-120">![Folder icon](media/hlp-16folder.gif "Folder icon") [Report Parts in Report Designer &#40;SSRS&#41;](report-design/report-parts-in-report-designer-ssrs.md)</span></span>

 <span data-ttu-id="9d340-121">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示") [Schedules](subscriptions/schedules.md)排程</span><span class="sxs-lookup"><span data-stu-id="9d340-121">![Folder icon](media/hlp-16folder.gif "Folder icon") [Schedules](subscriptions/schedules.md)</span></span>

 <span data-ttu-id="9d340-122">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")[訂閱和傳遞 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-122">![Folder icon](media/hlp-16folder.gif "Folder icon") [Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)</span></span>

 <span data-ttu-id="9d340-123">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示") [Reporting Services 資料警示](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-123">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>

 <span data-ttu-id="9d340-124">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示") [Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx)</span><span class="sxs-lookup"><span data-stu-id="9d340-124">![Folder icon](media/hlp-16folder.gif "Folder icon") [Power View](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx)</span></span>

 <span data-ttu-id="9d340-125">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示") [Reporting Services 安全性與保護](security/reporting-services-security-and-protection.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-125">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Security and Protection](security/reporting-services-security-and-protection.md)</span></span>

 <span data-ttu-id="9d340-126">[&#40;SSRS&#41;](url-access-ssrs.md)的![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")URL 存取</span><span class="sxs-lookup"><span data-stu-id="9d340-126">![Folder icon](media/hlp-16folder.gif "Folder icon") [URL Access &#40;SSRS&#41;](url-access-ssrs.md)</span></span>

 <span data-ttu-id="9d340-127">[&#40;SSRS&#41;](extensions-ssrs.md)的![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")延伸模組</span><span class="sxs-lookup"><span data-stu-id="9d340-127">![Folder icon](media/hlp-16folder.gif "Folder icon") [Extensions &#40;SSRS&#41;](extensions-ssrs.md)</span></span>

 <span data-ttu-id="9d340-128">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示") [Reporting Services 工具](tools/reporting-services-tools.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-128">![Folder icon](media/hlp-16folder.gif "Folder icon") [Reporting Services Tools](tools/reporting-services-tools.md)</span></span>

 <span data-ttu-id="9d340-129">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")[錯誤和事件參考 &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-129">![Folder icon](media/hlp-16folder.gif "Folder icon") [Errors and Events Reference &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md)</span></span>

 <span data-ttu-id="9d340-130">![資料夾圖示](media/hlp-16folder.gif "資料夾圖示")[功能參考 &#40;Reporting Services&#41;](feature-reference-reporting-services.md)</span><span class="sxs-lookup"><span data-stu-id="9d340-130">![Folder icon](media/hlp-16folder.gif "Folder icon") [Feature Reference &#40;Reporting Services&#41;](feature-reference-reporting-services.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="9d340-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d340-131">See Also</span></span>
 [<span data-ttu-id="9d340-132">SQL Server 資源中心</span><span class="sxs-lookup"><span data-stu-id="9d340-132">SQL Server Resource Center</span></span>](https://go.microsoft.com/fwlink/?linkID=219676)


