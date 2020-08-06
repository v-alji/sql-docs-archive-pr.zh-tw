---
title: 將報表發行至報表伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 644db7cc0d6647c160836596e6c87d524a94a4aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594382"
---
# <a name="publishing-reports-to-a-report-server"></a><span data-ttu-id="d1e8b-102">將報表發行至報表伺服器</span><span class="sxs-lookup"><span data-stu-id="d1e8b-102">Publishing Reports to a Report Server</span></span>
  <span data-ttu-id="d1e8b-103">在您設計和測試完報表或報表集之後，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的內建部署功能，將報表發行至實際報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-103">After you have designed and tested a report or set of reports, you can use the built-in deployment features in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to publish the reports to a report server.</span></span> <span data-ttu-id="d1e8b-104">您可以發行個別的報表或報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-104">You can publish individual reports or a Report Server project.</span></span> <span data-ttu-id="d1e8b-105">發行報表伺服器專案是發行多份報表最簡單的方式。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-105">Publishing a Report Server project is the easiest way to publish multiple reports.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="d1e8b-106">使用「*部署*」一詞，而不是「*發行*」一詞。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-106">uses the term *deploy*, instead ofthe term *publish*.</span></span> <span data-ttu-id="d1e8b-107">這兩個詞可以互換。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-107">The two terms are interchangeable.</span></span>  
  
 <span data-ttu-id="d1e8b-108">在您發行報表之前，您必須具有可執行此動作的權限。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-108">Before you can publish a report, you must have permission to do so.</span></span> <span data-ttu-id="d1e8b-109">權限是透過由您報表伺服器管理員所定義的角色安全性所決定。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-109">Permission is determined through role-based security that is defined by your report server administrator.</span></span> <span data-ttu-id="d1e8b-110">發佈作業一般是透過「發行者」角色授與。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-110">Publishing operations are typically granted through the Publisher role.</span></span>  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="d1e8b-111">會提供專案組態來管理報表發行。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-111">provides project configurations for managing report publication.</span></span> <span data-ttu-id="d1e8b-112">組態會指定報表伺服器的位置、報表伺服器上所安裝之 SQL Server Reporting Services 的版本、是否覆寫發行到報表伺服器的資料來源等等。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-112">The configuration specifies the location of the report server, the version of SQL Server Reporting Services installed on the report server, whether the data sources published to the report server are overwritten and so forth.</span></span> <span data-ttu-id="d1e8b-113">除了使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 所提供的組態，您還可以建立其他組態。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-113">In addition to using the configurations that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides, you can create additional configurations.</span></span>  
  
## <a name="project-configurations"></a><span data-ttu-id="d1e8b-114">專案組態</span><span class="sxs-lookup"><span data-stu-id="d1e8b-114">Project Configurations</span></span>  
 <span data-ttu-id="d1e8b-115">報表會在發行前建立，以確保只有有效的報表定義會發行到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-115">Reports are built before they are published to ensure that only valid report definitions are published to the report server.</span></span> <span data-ttu-id="d1e8b-116">專案組態包括建立報表的屬性，例如，暫時儲存已建立之報表的資料夾，以及如何處理建立問題。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-116">Project configurations include properties for building reports, such as the folder in which to temporarily store the built reports, and how to handle build issues.</span></span> <span data-ttu-id="d1e8b-117">組態也包含您用來指定報表伺服器之位置與版本、報表伺服器上之資料夾的屬性。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-117">The configurations also have properties that you use to specify the location and version of the report server, the folders on the report server.</span></span>  
  
 <span data-ttu-id="d1e8b-118">根據預設，[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 提供三種專案組態：DebugLocal、Debug 與 Release。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-118">By default, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provides three project configurations: DebugLocal, Debug, and Release.</span></span> <span data-ttu-id="d1e8b-119">預設組態為 DebugLocal。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-119">The default configuration is DebugLocal.</span></span> <span data-ttu-id="d1e8b-120">您通常可以使用 DebugLocal 組態在本機預覽視窗中檢視報表、使用 Debug 組態將報表發行至測試伺服器，以及使用 Release 組態將報表發行至實際伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-120">You typically use the DebugLocal configuration to view reports in a local preview window, the Debug configuration to publish reports to a test server, and the Release configuration to publish reports to a production server.</span></span> <span data-ttu-id="d1e8b-121">在標準工具列上的方案組態下拉式清單中會顯示使用中的組態。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-121">The solution configurations drop-down list on the Standard toolbar shows the active configuration.</span></span> <span data-ttu-id="d1e8b-122">若要使用不同的組態，請從清單中進行選取。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-122">To use a different configuration, select it from the list.</span></span>  
  
 <span data-ttu-id="d1e8b-123">您的報表環境可能已安裝多部報表伺服器以及不同版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-123">Your reporting environment might have multiple report servers and different versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installed.</span></span> <span data-ttu-id="d1e8b-124">您可以建立多個組態，然後根據部署狀況，使用不同的組態。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-124">You can create multiple configurations and then use a different one depending the deployment scenario.</span></span> <span data-ttu-id="d1e8b-125">如需詳細資訊，請參閱[SQL Server Data Tools &#40;SSRS&#41;中的部署和版本支援](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)，以及[&#40;Reporting Services&#41;設定部署屬性](../tools/set-deployment-properties-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-125">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md) and [Set Deployment Properties &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md).</span></span>  
  
## <a name="publishing-reports"></a><span data-ttu-id="d1e8b-126">發行報表</span><span class="sxs-lookup"><span data-stu-id="d1e8b-126">Publishing Reports</span></span>  
 <span data-ttu-id="d1e8b-127">您可以發行單一報表或包含多個報表的報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-127">You can publish a single report or a Report Server project that contains multiple reports.</span></span> <span data-ttu-id="d1e8b-128">如需發行報表的相關指示，請參閱[發行報表](../publish-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-128">For instructions about publishing reports, see [Publish Reports](../publish-reports.md).</span></span>  
  
### <a name="publishing-a-single-report"></a><span data-ttu-id="d1e8b-129">發行單一報表</span><span class="sxs-lookup"><span data-stu-id="d1e8b-129">Publishing a Single Report</span></span>  
 <span data-ttu-id="d1e8b-130">如果您不要發行專案中的所有報表，可以只選擇發行單一報表。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-130">If you do not want to publish all reports in a project, you can chose to publish only a single report.</span></span> <span data-ttu-id="d1e8b-131">若要這樣做，請選取部署報表的設定 (例如 Release 設定)，以滑鼠右鍵按一下報表，然後按一下 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-131">To do this, select a configuration that deploys the report (for example, the Release configuration), right-click the report, and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="d1e8b-132">如果報表使用共用資料來源，您也必須部署共用資料來源，否則將不會執行部署的報表。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-132">If a report uses a shared data source, you need to also deploy the shared data source or the deployed report will not run.</span></span> <span data-ttu-id="d1e8b-133">以滑鼠右鍵按一下共用資料來源，然後按一下 [部署]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-133">Right-click the shared data source and then click **Deploy**.</span></span>  
  
 <span data-ttu-id="d1e8b-134">您必須指定報表伺服器的目標伺服器 URL，並視需要變更負責部署報表和共用資料來源的預設資料夾。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-134">The target server URL of the report server must be specified and you might want to change the default folders to which reports and shared data sources deploy.</span></span>  
  
### <a name="publishing-multiple-reports"></a><span data-ttu-id="d1e8b-135">發行多個報表</span><span class="sxs-lookup"><span data-stu-id="d1e8b-135">Publishing Multiple Reports</span></span>  
 <span data-ttu-id="d1e8b-136">當您發行報表伺服器專案時，您可以發行該專案中的所有報表。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-136">When you publish a Report Server project, you publish all reports in that project.</span></span> <span data-ttu-id="d1e8b-137">所有報表都可以使用相同的報表組態，部署至相同的報表伺服器、伺服器上相同的資料夾等等。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-137">All reports are deployed using the same project configuration: to the same report server, the same folder on the server, and so on.</span></span> <span data-ttu-id="d1e8b-138">若要將報表發行至不同的伺服器，請逐個報表發行，或僅包含報表伺服器專案中您要發行的報表。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-138">To publish reports to different servers, either publish them one by one or include only reports you want to in the Report Server project.</span></span> <span data-ttu-id="d1e8b-139">一個方案可以包含多個報表伺服器專案，而且，使用多個專案可能會讓報表部署的管理更為容易，因為您可以使用不同的組態部署不同的專案。</span><span class="sxs-lookup"><span data-stu-id="d1e8b-139">A solution can include multiple Report Server projects, and using multiple project might make it easier to manage the deployment of reports because you can use a different configuration to deploy different projects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e8b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1e8b-140">See Also</span></span>  
 <span data-ttu-id="d1e8b-141">[專案屬性頁對話方塊](../tools/project-property-pages-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="d1e8b-141">[Project Property Pages Dialog Box](../tools/project-property-pages-dialog-box.md) </span></span>  
 <span data-ttu-id="d1e8b-142">[報表伺服器內容管理 &#40;SSRS 原生模式&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="d1e8b-142">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="d1e8b-143">升級報表</span><span class="sxs-lookup"><span data-stu-id="d1e8b-143">Upgrade Reports</span></span>](../install-windows/upgrade-reports.md)  
  
  
