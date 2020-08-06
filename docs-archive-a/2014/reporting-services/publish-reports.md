---
title: 發行報表 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], publishing
- publishing reports [Reporting Services]
ms.assetid: ef5a514e-e818-4041-a8b0-15835f9a046b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb54308a6b15260d4c336950f231d0ee40836430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585111"
---
# <a name="publish-reports"></a><span data-ttu-id="d5d9a-102">發行報表</span><span class="sxs-lookup"><span data-stu-id="d5d9a-102">Publish Reports</span></span>
  <span data-ttu-id="d5d9a-103">您可以從[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]部署專案，將報表伺服器專案中的所有報表與共用資料來源發行至報表伺服器，或者發行單一報表。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-103">From[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can publish either all the reports and shared data sources in a Report Server project to a report server by deploying the project, or you can publish a single report.</span></span> <span data-ttu-id="d5d9a-104">在可以發行報表之前，您必須指定目標報表伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-104">Before you can publish a report you must specify the URL of the target report server.</span></span> <span data-ttu-id="d5d9a-105">如需詳細資訊，請參閱[設定部署屬性 &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-105">For more information, see [Set Deployment Properties &#40;Reporting Services&#41;](tools/set-deployment-properties-reporting-services.md).</span></span>  
  
 <span data-ttu-id="d5d9a-106">您可以使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 版的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 來開啟、修改、預覽、儲存，以及同時發行 [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] 和 [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] 報表。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-106">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to open, modify, preview, save, and publish both [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] and [!INCLUDE[ssRSversion10](../includes/ssrsversion10-md.md)] reports.</span></span> <span data-ttu-id="d5d9a-107">如需詳細資訊，請參閱 [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-107">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
### <a name="to-publish-all-reports-in-a-project"></a><span data-ttu-id="d5d9a-108">若要發行專案中的所有報表</span><span class="sxs-lookup"><span data-stu-id="d5d9a-108">To publish all reports in a project</span></span>  
  
-   <span data-ttu-id="d5d9a-109">在 [**建立**] 功能表上，按一下 [\*\*部署 \<report project name> \*\*]。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-109">On the **Build** menu, click **Deploy \<report project name>**.</span></span> <span data-ttu-id="d5d9a-110">或者，在方案總管中，以滑鼠右鍵按一下報表專案，然後按一下 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-110">Alternatively, in Solution Explorer, right-click the report project and then click **Deploy**.</span></span> <span data-ttu-id="d5d9a-111">您可以在 [輸出] 視窗中，檢視發行程序的狀態。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-111">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d5d9a-112">當您部署報表伺服器專案時，也會部署報表專案中的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-112">When you deploy a Report Server project, the shared data sources in the report project are also deployed.</span></span>  
  
### <a name="to-publish-a-single-report"></a><span data-ttu-id="d5d9a-113">若要發行單一報表</span><span class="sxs-lookup"><span data-stu-id="d5d9a-113">To publish a single report</span></span>  
  
-   <span data-ttu-id="d5d9a-114">在 [方案總管] 中，以滑鼠右鍵按一下報表，然後按一下 **[部署]**。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-114">In Solution Explorer, right-click the report and then click **Deploy**.</span></span> <span data-ttu-id="d5d9a-115">您可以在 [輸出] 視窗中，檢視發行程序的狀態。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-115">You can view the status of the publishing process in the Output window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d5d9a-116">當您發行報表時，也必須部署該報表所使用的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="d5d9a-116">When you publish a report, you must also deploy the shared data sources that the report uses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d9a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d9a-117">See Also</span></span>  
 <span data-ttu-id="d5d9a-118">[發行資料來源與報表](reports/publishing-data-sources-and-reports.md) </span><span class="sxs-lookup"><span data-stu-id="d5d9a-118">[Publishing Data Sources and Reports](reports/publishing-data-sources-and-reports.md) </span></span>  
 <span data-ttu-id="d5d9a-119">[預覽報表](reports/previewing-reports.md) </span><span class="sxs-lookup"><span data-stu-id="d5d9a-119">[Previewing Reports](reports/previewing-reports.md) </span></span>  
 <span data-ttu-id="d5d9a-120">[將報表發行至報表伺服器](reports/publishing-reports-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="d5d9a-120">[Publishing Reports to a Report Server](reports/publishing-reports-to-a-report-server.md) </span></span>  
 <span data-ttu-id="d5d9a-121">[尋找、查看和管理報表 &#40;報表產生器和 SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d5d9a-121">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d5d9a-122">匯出報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d5d9a-122">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
