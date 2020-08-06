---
title: Upgrade Advisor 總覽 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- SQL Server Upgrade Advisor, components
- tools [Upgrade Advisor]
- Upgrade Advisor [SQL Server], components
- components [Upgrade Advisor]
- Upgrade Advisor Analysis Wizard
- limitations [Upgrade Advisor]
- analyzing system [Upgrade Advisor]
- analyzing system [Upgrade Advisor], about analysis
ms.assetid: f5c56f63-4478-40af-abb9-642f58a0026c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d787f41eba97314986ec77df4cfcff580ae9915
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595418"
---
# <a name="upgrade-advisor-overview"></a><span data-ttu-id="6448a-102">Upgrade Advisor 概觀</span><span class="sxs-lookup"><span data-stu-id="6448a-102">Upgrade Advisor Overview</span></span>
  <span data-ttu-id="6448a-103">Upgrade Advisor 提供了一個中央主控台，可讓您分析 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 和 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 元件，並檢視包含有關分析結果資訊的報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-103">Upgrade Advisor provides a central console to analyze [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] components, and to view reports that contain information about the results of the analysis.</span></span>  
  
## <a name="how-upgrade-advisor-works"></a><span data-ttu-id="6448a-104">Upgrade Advisor 如何運作</span><span class="sxs-lookup"><span data-stu-id="6448a-104">How Upgrade Advisor Works</span></span>  
 <span data-ttu-id="6448a-105">當您執行 Upgrade Advisor 時，Upgrade Advisor 開始頁面隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="6448a-105">When you run Upgrade Advisor, the Upgrade Advisor start page appears.</span></span> <span data-ttu-id="6448a-106">Upgrade Advisor 開始頁面是下列元件的啟動點：</span><span class="sxs-lookup"><span data-stu-id="6448a-106">The Upgrade Advisor start page is the launching point for the following:</span></span>  
  
-   <span data-ttu-id="6448a-107">Upgrade Advisor 分析精靈</span><span class="sxs-lookup"><span data-stu-id="6448a-107">Upgrade Advisor Analysis Wizard</span></span>  
  
-   <span data-ttu-id="6448a-108">Upgrade Advisor 報表檢視器</span><span class="sxs-lookup"><span data-stu-id="6448a-108">Upgrade Advisor Report Viewer</span></span>  
  
-   <span data-ttu-id="6448a-109">Upgrade Advisor 說明</span><span class="sxs-lookup"><span data-stu-id="6448a-109">Upgrade Advisor Help</span></span>  
  
 <span data-ttu-id="6448a-110">第一次使用 Upgrade Advisor 時，請執行 Upgrade Advisor 分析精靈來分析伺服器。</span><span class="sxs-lookup"><span data-stu-id="6448a-110">The first time that you use Upgrade Advisor, run the Upgrade Advisor Analysis Wizard to analyze a server.</span></span> <span data-ttu-id="6448a-111">當 wizard 完成分析時，請按一下嚮導中的 [**啟動報表**]，或返回 Upgrade Advisor 起始頁。</span><span class="sxs-lookup"><span data-stu-id="6448a-111">When the wizard completes the analysis, click **Launch Report** from the wizard or return to the Upgrade Advisor start page.</span></span> <span data-ttu-id="6448a-112">如此，您就可以執行 Upgrade Advisor 報表檢視器來檢視報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-112">From there, run the Upgrade Advisor Report Viewer to view the report.</span></span> <span data-ttu-id="6448a-113">此報表會提供一些資訊的連結，以便協助您解決已知的問題。</span><span class="sxs-lookup"><span data-stu-id="6448a-113">The report provides links to information that will help you resolve known issues.</span></span>  
  
## <a name="upgrade-advisor-analysis-wizard"></a><span data-ttu-id="6448a-114">Upgrade Advisor 分析精靈</span><span class="sxs-lookup"><span data-stu-id="6448a-114">Upgrade Advisor Analysis Wizard</span></span>  
 <span data-ttu-id="6448a-115">若要執行分析，請在 Upgrade Advisor 開始頁面上按一下 [**啟動 Upgrade Advisor 分析嚮導]** 。</span><span class="sxs-lookup"><span data-stu-id="6448a-115">To perform an analysis, click **Launch Upgrade Advisor Analysis Wizard** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="6448a-116">Upgrade Advisor 分析精靈會蒐集有關您想要分析之電腦、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件和追蹤檔案的資訊。</span><span class="sxs-lookup"><span data-stu-id="6448a-116">The Upgrade Advisor Analysis Wizard gathers information about the computer, instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, and trace files that you want to analyze.</span></span> <span data-ttu-id="6448a-117">在蒐集並確認所有資訊之後，Upgrade Advisor 分析精靈便分析 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="6448a-117">After all the information has been gathered and confirmed, the Upgrade Advisor Analysis Wizard analyzes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6448a-118">每當您執行 Upgrade Advisor 分析精靈時，系統會產生不同的報表，而不會覆寫選取之元件的現有報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-118">Each time you run the Upgrade Advisor Analysis Wizard, a separate report is generated, and existing reports for the selected components are not overwritten.</span></span> <span data-ttu-id="6448a-119">但是，報表檢視器只顯示最新的五個報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-119">However, the report viewer displays only the five latest reports.</span></span>  
  
 <span data-ttu-id="6448a-120">當 Upgrade Advisor 分析精靈完成分析時，它會針對您在分析中加入的每個元件建立一個 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6448a-120">When the Upgrade Advisor Analysis Wizard finishes its analysis, it creates an XML file for each component that you have included in the analysis.</span></span> <span data-ttu-id="6448a-121">XML 檔案包含每個元件中發現的項目和問題。</span><span class="sxs-lookup"><span data-stu-id="6448a-121">The XML files contain the items and issues discovered in each component.</span></span>  
  
### <a name="what-upgrade-advisor-analyzes"></a><span data-ttu-id="6448a-122">Upgrade Advisor 的分析內容</span><span class="sxs-lookup"><span data-stu-id="6448a-122">What Upgrade Advisor Analyzes</span></span>  
 <span data-ttu-id="6448a-123">專用分析器會在每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的 Upgrade Advisor 內容中執行。</span><span class="sxs-lookup"><span data-stu-id="6448a-123">A dedicated analyzer runs in the context of Upgrade Advisor for each [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] component.</span></span> <span data-ttu-id="6448a-124">每個分析器的輸出都是該元件的 XML 報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-124">The output of each analyzer is an XML report for that component.</span></span>  
  
 <span data-ttu-id="6448a-125">Upgrade Advisor 會查詢下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件：</span><span class="sxs-lookup"><span data-stu-id="6448a-125">Upgrade Advisor queries the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="6448a-126">資料庫伺服器 (《[!INCLUDE[ssDE](../../includes/ssde-md.md)] 線上叢書》中也稱為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 包含複寫、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式、全文檢索搜尋和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span><span class="sxs-lookup"><span data-stu-id="6448a-126">Database Server (also referred to as the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online), which includes Replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, Full-Text Search, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="6448a-127">在分析期間，每個分析器都會建立記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6448a-127">During analysis, each analyzer creates a log file.</span></span> <span data-ttu-id="6448a-128">您可以使用這些記錄檔針對分析進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="6448a-128">You can use these log files to troubleshoot the analysis.</span></span> <span data-ttu-id="6448a-129">例如，如果 Upgrade Advisor 執行速度很慢，您就可以檢視記錄檔來判斷延遲的原因。</span><span class="sxs-lookup"><span data-stu-id="6448a-129">For example, if Upgrade Advisor is running slowly, you can view the log files to determine the cause of the delay.</span></span>  
  
### <a name="upgrade-advisor-limitations"></a><span data-ttu-id="6448a-130">Upgrade Advisor 的限制</span><span class="sxs-lookup"><span data-stu-id="6448a-130">Upgrade Advisor Limitations</span></span>  
 <span data-ttu-id="6448a-131">Upgrade Advisor 無法偵測可能會影響升級的所有問題。</span><span class="sxs-lookup"><span data-stu-id="6448a-131">Upgrade Advisor cannot detect every issue that might affect an upgrade.</span></span> <span data-ttu-id="6448a-132">例如，如果您已在使用者桌上型電腦上執行的用戶端應用程式中嵌入 SQL 程式碼，Upgrade Advisor 便無法分析這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="6448a-132">For example, if you have embedded SQL code in a client application that runs on end-user desktops, it will not be possible for Upgrade Advisor to analyze the applications.</span></span> <span data-ttu-id="6448a-133">針對這些項目，您仍然必須考慮上述問題並視需要升級、移轉或修改安裝中的資訊。</span><span class="sxs-lookup"><span data-stu-id="6448a-133">For these items, you still must consider the issues and upgrade, migrate, or modify the information as required in your installation.</span></span>  
  
 <span data-ttu-id="6448a-134">Upgrade Advisor 不會分析加密的預存程序、擴充預存程序中的程式碼，以及使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 以外語言撰寫的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6448a-134">Upgrade Advisor does not analyze encrypted stored procedures, code in extended stored procedures, and source code in languages other than [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="upgrade-advisor-report-viewer"></a><span data-ttu-id="6448a-135">Upgrade Advisor 報表檢視器</span><span class="sxs-lookup"><span data-stu-id="6448a-135">Upgrade Advisor Report Viewer</span></span>  
 <span data-ttu-id="6448a-136">若要查看 Upgrade Advisor 報表，請在 Upgrade Advisor 開始頁面上，按一下 [**啟動 Upgrade Advisor 報表檢視器]** 。</span><span class="sxs-lookup"><span data-stu-id="6448a-136">To view an Upgrade Advisor report, click **Launch Upgrade Advisor Report Viewer** on the Upgrade Advisor start page.</span></span> <span data-ttu-id="6448a-137">當 Upgrade Advisor 報表檢視器啟動時，它就會載入預設目錄中的報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-137">When the Upgrade Advisor Report Viewer starts, the reports in the default directory are loaded.</span></span> <span data-ttu-id="6448a-138">如果 Upgrade Advisor 報表檢視器在預設目錄中找不到任何報表，它就不會顯示報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-138">Reports are not displayed if the Upgrade Advisor Report Viewer does not find any reports in the default directory.</span></span> <span data-ttu-id="6448a-139">如果預設目錄中沒有任何報表，您可以執行 Upgrade Advisor 分析精靈來建立報表，或是從其他伺服器或子目錄載入現有的報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-139">If there are no reports in the default directory, you can either run the Upgrade Advisor Analysis Wizard to create a report or load an existing report from another server or from a subdirectory.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="6448a-140">Upgrade Advisor 不會覆寫現有報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-140">Upgrade Advisor does not overwrite existing reports.</span></span> <span data-ttu-id="6448a-141">但是，報表檢視器只顯示最新的五個報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-141">However, the report viewer displays only the five latest reports.</span></span> <span data-ttu-id="6448a-142">若要查看先前的報表，請從 [**報表**] 下拉式清單方塊中選取報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-142">To view an earlier report, select the report from the **Report** drop-down list box.</span></span> <span data-ttu-id="6448a-143">時間戳記表示產生報表的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="6448a-143">The timestamp indicates the date and time the report was generated.</span></span>  
  
 <span data-ttu-id="6448a-144">當 Upgrade Advisor 報表檢視器中載入 Upgrade Advisor 分析精靈的 XML 檔案時，它就會顯示每個元件的報表。</span><span class="sxs-lookup"><span data-stu-id="6448a-144">When XML files from the Upgrade Advisor Analysis Wizard are loaded into the Upgrade Advisor Report Viewer, a report for each component is displayed.</span></span> <span data-ttu-id="6448a-145">此報表包含所有您必須處理的已知問題，同時包括可偵測和無法偵測的問題。</span><span class="sxs-lookup"><span data-stu-id="6448a-145">The report contains all the known issues, both detectable and undetectable, that you need to address.</span></span> <span data-ttu-id="6448a-146">針對每個問題，系統會顯示一個圖示 (指出重要性)、一個標籤 (告知您必須修正此問題的時間)，以及一則簡短描述。</span><span class="sxs-lookup"><span data-stu-id="6448a-146">For each issue there is an icon indicating importance, a label informing you when the issue must be fixed, and a short description.</span></span> <span data-ttu-id="6448a-147">當您展開問題時，將會看見更長的描述、問題詳細資料的連結和說明檔的連結。</span><span class="sxs-lookup"><span data-stu-id="6448a-147">When you expand an issue, you will see a longer description, a link to issue details, and a link to the Help file.</span></span> <span data-ttu-id="6448a-148">每個問題的資訊都設計成提供足夠的資訊，可讓您修正問題。</span><span class="sxs-lookup"><span data-stu-id="6448a-148">The information for each issue is designed to provide enough information for you to fix the issue.</span></span>  
  
 <span data-ttu-id="6448a-149">大部分元件都具有無法偵測的問題。</span><span class="sxs-lookup"><span data-stu-id="6448a-149">Most components have issues that cannot be detected.</span></span> <span data-ttu-id="6448a-150">若要查看這些問題，請展開元件的 [**其他升級問題**] 專案，然後按一下連結以在檔中查看有關問題的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="6448a-150">To view these issues, expand the **Other Upgrade Issues** item for the component, and then click the link to view additional information about the issues in the documentation.</span></span> <span data-ttu-id="6448a-151">如需有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 回溯相容性問題的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="6448a-151">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backward compatibility issues, see [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6448a-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6448a-152">See Also</span></span>  
 [<span data-ttu-id="6448a-153">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="6448a-153">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
