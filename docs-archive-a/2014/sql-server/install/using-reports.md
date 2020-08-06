---
title: 使用報表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- overriding reports
- Upgrade Advisor Report Viewer
- reports [Upgrade Advisor], about reports
- formatting reports
- resolved issues [Upgrade Advisor]
- distributing reports [Reporting Services]
- filtering reports [Reporting Services]
- removing report items
- viewing reports
- rerunning analysis
- information issues [Upgrade Advisor]
- deleting report items
- icons [Upgrade Advisor]
- Upgrade Advisor [SQL Server], reports
- sending reports
- blocking issues [Upgrade Advisor]
- sharing reports
- reports [Upgrade Advisor]
- SQL Server Upgrade Advisor, reports
- modifying reports
- distributing reports [Reporting Services], about report distribution
- warnings [Upgrade Advisor]
- analyzing system [Upgrade Advisor], reports
ms.assetid: 4a3cb94a-a7ac-4cec-94c7-db26fcf6d161
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f52afcfdaa7de33d83d64a049f9a350f0463b4c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710117"
---
# <a name="using-reports"></a><span data-ttu-id="9943d-102">使用報表</span><span class="sxs-lookup"><span data-stu-id="9943d-102">Using Reports</span></span>
  <span data-ttu-id="9943d-103">Upgrade Advisor 分析精靈會為伺服器上分析的每個元件和每個執行個體 (如有必要) 產生個別報表。</span><span class="sxs-lookup"><span data-stu-id="9943d-103">A separate report is generated for each component, and, where necessary, each instance, that the Upgrade Advisor Analysis Wizard analyzes on a server.</span></span> <span data-ttu-id="9943d-104">報表會提供影響升級之已知問題的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9943d-104">The report provides details about known issues that affect an upgrade.</span></span> <span data-ttu-id="9943d-105">報表還會提供解決識別問題之資訊和建議動作的連結。</span><span class="sxs-lookup"><span data-stu-id="9943d-105">It also provides links to information and suggested actions for addressing the identified issues.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9943d-106">如果 Upgrade Advisor 報表檢視器在預設報表目錄中找不到任何報表，您可以使用 [**開啟報表**] 連結，從不同的目錄載入報表。</span><span class="sxs-lookup"><span data-stu-id="9943d-106">If the Upgrade Advisor Report Viewer does not find any reports in the default reports directory, you can load a report from a different directory by using the **Open Report** link.</span></span>  
  
## <a name="viewing-reports"></a><span data-ttu-id="9943d-107">檢視報表</span><span class="sxs-lookup"><span data-stu-id="9943d-107">Viewing Reports</span></span>  
 <span data-ttu-id="9943d-108">您可以使用 Upgrade Advisor 報表檢視器來檢視 Upgrade Advisor 報表。</span><span class="sxs-lookup"><span data-stu-id="9943d-108">You use the Upgrade Advisor Report Viewer to view Upgrade Advisor reports.</span></span> <span data-ttu-id="9943d-109">若要查看報表，請在 Upgrade Advisor 開始頁面上，按一下 [**啟動 Upgrade Advisor 報表檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="9943d-109">To view reports, on the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
 <span data-ttu-id="9943d-110">當您載入伺服器的報表之後，就可以選取想要查看升級問題的元件。</span><span class="sxs-lookup"><span data-stu-id="9943d-110">After you load a report for a server, you can select a component for which you want to see upgrade issues.</span></span> <span data-ttu-id="9943d-111">您可以從 [**篩選依據**] 方塊套用篩選，以查看下列各項：</span><span class="sxs-lookup"><span data-stu-id="9943d-111">You can apply a filter from the **Filter By** box to see the following:</span></span>  
  
-   <span data-ttu-id="9943d-112">所有問題</span><span class="sxs-lookup"><span data-stu-id="9943d-112">All issues</span></span>  
  
-   <span data-ttu-id="9943d-113">所有升級的問題</span><span class="sxs-lookup"><span data-stu-id="9943d-113">All upgrade issues</span></span>  
  
-   <span data-ttu-id="9943d-114">升級前的問題</span><span class="sxs-lookup"><span data-stu-id="9943d-114">Pre-upgrade issues</span></span>  
  
-   <span data-ttu-id="9943d-115">所有移轉的問題</span><span class="sxs-lookup"><span data-stu-id="9943d-115">All migration issues</span></span>  
  
-   <span data-ttu-id="9943d-116">已解決的問題</span><span class="sxs-lookup"><span data-stu-id="9943d-116">Resolved issues</span></span>  
  
-   <span data-ttu-id="9943d-117">未解決的問題</span><span class="sxs-lookup"><span data-stu-id="9943d-117">Unresolved issues</span></span>  
  
 <span data-ttu-id="9943d-118">如果您的報表有超過20個問題，您可以按一下問題清單頂端或底部的 **[下一步 20]** 或 [**前 20** ]，移至下一個或上一個問題群組。</span><span class="sxs-lookup"><span data-stu-id="9943d-118">If your report has more than 20 issues, you can move to the next or previous group of issues by clicking **Next 20** or **Previous 20** at the top or bottom of the issues list.</span></span>  
  
 <span data-ttu-id="9943d-119">您可以從 [**報表**] 下拉式清單方塊中選取報表，以查看最多五個已儲存的報表。</span><span class="sxs-lookup"><span data-stu-id="9943d-119">You can view up to five saved reports by selecting the reports from the **Report** drop-down list box.</span></span> <span data-ttu-id="9943d-120">這些報表是依其產生時的時間戳記列出。</span><span class="sxs-lookup"><span data-stu-id="9943d-120">The reports are listed by the timestamp from when they were generated.</span></span>  
  
## <a name="report-format"></a><span data-ttu-id="9943d-121">報表格式</span><span class="sxs-lookup"><span data-stu-id="9943d-121">Report Format</span></span>  
 <span data-ttu-id="9943d-122">報表檢視器會在三個資料行中顯示報表問題。</span><span class="sxs-lookup"><span data-stu-id="9943d-122">The report viewer displays report issues in three columns.</span></span> <span data-ttu-id="9943d-123">每個問題都是可摺疊的，如此您就可以隱藏描述，而單獨檢視主要資訊。</span><span class="sxs-lookup"><span data-stu-id="9943d-123">Each issue is collapsible so that you can hide the description and view only the key information.</span></span>  
  
 <span data-ttu-id="9943d-124">第一個資料行是 [**重要性**] 資料行。</span><span class="sxs-lookup"><span data-stu-id="9943d-124">The first column is the **Importance** column.</span></span> <span data-ttu-id="9943d-125">圖示會顯示帶有 X 的紅色圓形 (表示阻礙或重要問題)，或顯示帶有驚嘆號的黃色三角形 (表示「警告」和「資訊」問題)，藉以指出每個問題的重要性。</span><span class="sxs-lookup"><span data-stu-id="9943d-125">Icons indicate the importance for each issue by displaying either a red circle with an X for blocking or important issues or a yellow triangle with an exclamation mark for Warning and Information issues.</span></span> <span data-ttu-id="9943d-126">第二個數據行 [**修正**時機] 表示您必須解決問題的時間。</span><span class="sxs-lookup"><span data-stu-id="9943d-126">The second column, **When to fix**, indicates when you must resolve the issue.</span></span> <span data-ttu-id="9943d-127">您可以針對 [**重要性**] 或 [**修正時間**] 資料行來排序報表。</span><span class="sxs-lookup"><span data-stu-id="9943d-127">You can sort the report on either the **Importance** or **When to fix** column.</span></span> <span data-ttu-id="9943d-128">第三個數據行 [**描述**] 會列出問題的標題。</span><span class="sxs-lookup"><span data-stu-id="9943d-128">The third column, **Description**, lists the title of the issue.</span></span>  
  
 <span data-ttu-id="9943d-129">您可以展開問題來顯示其他資訊、展開連結來顯示有關解決問題的詳細資訊，還可以展開連結來顯示問題詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9943d-129">You can expand an issue to display additional information, a link to detailed information about resolving the issue, and a link to show issue details.</span></span> <span data-ttu-id="9943d-130">當您按一下連結以取得問題的詳細資訊時，即會顯示「說明」主題並提供問題的資訊以及解決問題的指示。</span><span class="sxs-lookup"><span data-stu-id="9943d-130">When you click the link to get detailed information for the issue, a Help topic with information about the issue and instructions for addressing the issue is displayed.</span></span> <span data-ttu-id="9943d-131">修正問題或管理您的動作專案之後，您可以選取 [已**解決這個問題**] 核取方塊，將問題標示為完成。</span><span class="sxs-lookup"><span data-stu-id="9943d-131">After you have fixed an issue, or to manage your action items, you can mark issues as complete by selecting the **This issue has been resolved** check box.</span></span> <span data-ttu-id="9943d-132">如果您想要從升級問題清單中移除已解決的問題，請**按一下 [** 重新整理]。</span><span class="sxs-lookup"><span data-stu-id="9943d-132">If you want to remove the resolved issues from the list of upgrade issues, click **Refresh**.</span></span> <span data-ttu-id="9943d-133">在您針對同一個元件執行 Upgrade Advisor 分析嚮導，或從 [**篩選依據**] 選項套用 [**已解決的問題**] 篩選器之前，不會再次顯示此問題。</span><span class="sxs-lookup"><span data-stu-id="9943d-133">The issue is not displayed again until you either run the Upgrade Advisor Analysis Wizard against the same component or apply the **Resolved Issues** filter from the **Filter By** option.</span></span>  
  
## <a name="report-files"></a><span data-ttu-id="9943d-134">報表檔案</span><span class="sxs-lookup"><span data-stu-id="9943d-134">Report Files</span></span>  
 <span data-ttu-id="9943d-135">Upgrade Advisor 分析 Wizard 會在 [我的文件] \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級 upgrade advisor\110\reports 目錄中建立報表，並為您分析的每部伺服器建立子目錄。</span><span class="sxs-lookup"><span data-stu-id="9943d-135">The Upgrade Advisor Analysis Wizard creates reports in the My Documents\\[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports directory and creates a subdirectory for each server that you analyze.</span></span> <span data-ttu-id="9943d-136">這些報表檔案是遵循特定命名慣例的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="9943d-136">The report files are XML files that follow a specific naming convention.</span></span> <span data-ttu-id="9943d-137">當您啟動 Upgrade Advisor 報表檢視器時，就會顯示預設目錄中的報表檔案。</span><span class="sxs-lookup"><span data-stu-id="9943d-137">When you launch the Upgrade Advisor Report Viewer, the report files in the default directory are displayed.</span></span> <span data-ttu-id="9943d-138">如果您將報表檔案複製到這個資料夾中，它們必須遵守命名慣例，否則報表檢視器將不會自動顯示它們。</span><span class="sxs-lookup"><span data-stu-id="9943d-138">If you copy report files into this folder, they must adhere to the naming convention or the report viewer will not display them automatically.</span></span>  
  
 <span data-ttu-id="9943d-139">如果您想要與其他人共用這項資訊，可以將 XML 報表傳送給他們。</span><span class="sxs-lookup"><span data-stu-id="9943d-139">If you want to share the information with other people, you can send them the XML report.</span></span> <span data-ttu-id="9943d-140">或者，如果您想要使用其他應用程式，就可以將報表匯出成逗號分隔值檔案，以便用來建立試算表、文字檔或電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="9943d-140">Or, if you want to use another application, you can export the report into a comma-separated value file that you can use to create a spreadsheet, text file, or e-mail message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9943d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9943d-141">See Also</span></span>  
 <span data-ttu-id="9943d-142">[如何：查看 Upgrade Advisor 報表](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span><span class="sxs-lookup"><span data-stu-id="9943d-142">[How to: View an Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md) </span></span>  
 <span data-ttu-id="9943d-143">[如何：匯出報表](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="9943d-143">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="9943d-144">[如何：篩選報表](../../../2014/sql-server/install/how-to-filter-reports.md) </span><span class="sxs-lookup"><span data-stu-id="9943d-144">[How to: Filter Reports](../../../2014/sql-server/install/how-to-filter-reports.md) </span></span>  
 <span data-ttu-id="9943d-145">[解決升級問題](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9943d-145">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9943d-146">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="9943d-146">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
