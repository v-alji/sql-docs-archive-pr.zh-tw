---
title: 如何：查看 Upgrade Advisor 報表 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9e6df35b869186a601458889c348153093ccbce4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606036"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a><span data-ttu-id="e142c-102">如何：檢視 Upgrade Advisor 報表</span><span class="sxs-lookup"><span data-stu-id="e142c-102">How to: View an Upgrade Advisor Report</span></span>
  <span data-ttu-id="e142c-103">Upgrade Advisor 會針對您選取要分析的每個元件建立報表。</span><span class="sxs-lookup"><span data-stu-id="e142c-103">Upgrade Advisor creates reports for each component that you select to analyze.</span></span> <span data-ttu-id="e142c-104">此主題描述如何從 Upgrade Advisor 開始頁面檢視 Upgrade Advisor 報表。</span><span class="sxs-lookup"><span data-stu-id="e142c-104">This topic describes how to view an Upgrade Advisor report from the Upgrade Advisor start page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e142c-105">報表檢視器會根據標準檔案名稱載入檔案。</span><span class="sxs-lookup"><span data-stu-id="e142c-105">The report viewer loads files based on standard file names.</span></span> <span data-ttu-id="e142c-106">如果檔案已經重新命名，報表檢視器將不會載入它們。</span><span class="sxs-lookup"><span data-stu-id="e142c-106">If the files have been renamed, the report viewer will not load them.</span></span>  
  
### <a name="to-view-a-report"></a><span data-ttu-id="e142c-107">若要檢視報表</span><span class="sxs-lookup"><span data-stu-id="e142c-107">To view a report</span></span>  
  
1.  <span data-ttu-id="e142c-108">依序按一下 [**開始**]、[**所有程式**]、[] **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** ，然後按一下 [ \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor\*\*]。</span><span class="sxs-lookup"><span data-stu-id="e142c-108">Click **Start**, click **All Programs**, click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, and then click **[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor**.</span></span>  
  
2.  <span data-ttu-id="e142c-109">在 Upgrade Advisor 開始頁面上，按一下 [**啟動 Upgrade Advisor 報表檢視器]**。</span><span class="sxs-lookup"><span data-stu-id="e142c-109">On the Upgrade Advisor start page, click **Launch Upgrade Advisor Report Viewer**.</span></span>  
  
3.  <span data-ttu-id="e142c-110">若要選取電腦上預設位置中的報表：</span><span class="sxs-lookup"><span data-stu-id="e142c-110">To select a report in the default location on your computer:</span></span>  
  
    1.  <span data-ttu-id="e142c-111">在 [**伺服器**] 清單中，選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="e142c-111">In the **Server** list, select a server.</span></span>  
  
    2.  <span data-ttu-id="e142c-112">在 [**實例或元件**] 清單中，選取 [元件] 或 [元件/實例] 組合。</span><span class="sxs-lookup"><span data-stu-id="e142c-112">In the **Instance or component** list, select a component or component/instance combination.</span></span>  
  
     <span data-ttu-id="e142c-113">若要選取另一個位置的報表：</span><span class="sxs-lookup"><span data-stu-id="e142c-113">To select a report at another location:</span></span>  
  
    1.  <span data-ttu-id="e142c-114">按一下 [**開啟報表**] 連結。</span><span class="sxs-lookup"><span data-stu-id="e142c-114">Click the **Open Report** link.</span></span>  
  
    2.  <span data-ttu-id="e142c-115">瀏覽至報表位置，然後按兩下 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="e142c-115">Browse to the report location and then double-click the XML file.</span></span>  
  
     <span data-ttu-id="e142c-116">Upgrade Advisor 最多儲存先前分析的五個報表做為歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="e142c-116">Upgrade Advisor stores up to five reports from previous analysis as history.</span></span> <span data-ttu-id="e142c-117">若要查看這些報表，請按一下 [**報表**] 下拉式清單方塊，然後選取報表。</span><span class="sxs-lookup"><span data-stu-id="e142c-117">To view these reports, click the **Report** drop-down list box, and select a report.</span></span> <span data-ttu-id="e142c-118">這些報表是依其產生時的時間戳記列出。</span><span class="sxs-lookup"><span data-stu-id="e142c-118">The reports are listed by the timestamp from when they were generated.</span></span>  
  
     <span data-ttu-id="e142c-119">報表包含所有已偵測之問題的下列詳細資料：</span><span class="sxs-lookup"><span data-stu-id="e142c-119">The report contains the following details for all detected issues:</span></span>  
  
    -   <span data-ttu-id="e142c-120">[**重要性**]，表示修正問題的重要程度。</span><span class="sxs-lookup"><span data-stu-id="e142c-120">**Importance**, which indicates how important it is to fix the issue.</span></span>  
  
    -   <span data-ttu-id="e142c-121">**修正**時機，這會指出您是否應該 (或必須在升級至之前或之後，或在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 遷移應用程式或資料之前或之後，或是在任何時間之前，) 修正此問題。</span><span class="sxs-lookup"><span data-stu-id="e142c-121">**When to fix**, which indicates if you should (or must) fix the issue before or after upgrading to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], before or after migrating the application or data, or anytime.</span></span>  
  
    -   <span data-ttu-id="e142c-122">問題的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="e142c-122">A brief description of the issue.</span></span>  
  
4.  <span data-ttu-id="e142c-123">如果報表包含超過 20 個項目，按一下報表頂端或底部的綠色前進箭頭，即可檢視下一組項目。</span><span class="sxs-lookup"><span data-stu-id="e142c-123">If the report contains more than 20 items, click the green forward arrow at the top or bottom of the report to view the next set of items.</span></span> <span data-ttu-id="e142c-124">按一下綠色後退箭頭則可檢視前 20 個項目。</span><span class="sxs-lookup"><span data-stu-id="e142c-124">Click the green back button to view the previous 20 items.</span></span>  
  
5.  <span data-ttu-id="e142c-125">若要排序報表，請按一下資料行標題。</span><span class="sxs-lookup"><span data-stu-id="e142c-125">To sort the report, click a column heading.</span></span>  
  
6.  <span data-ttu-id="e142c-126">若要檢視特定項目的詳細資料，請按一下該項目。</span><span class="sxs-lookup"><span data-stu-id="e142c-126">To view details for a specific item, click the item.</span></span> <span data-ttu-id="e142c-127">問題的描述隨即顯示，並提供其他選項：</span><span class="sxs-lookup"><span data-stu-id="e142c-127">A description of the issue appears, along with additional options:</span></span>  
  
    -   <span data-ttu-id="e142c-128">若要查看找到這個問題的物件，請按一下 [**顯示受影響的物件**]。</span><span class="sxs-lookup"><span data-stu-id="e142c-128">To view the objects where this issue was found, click **Show affected objects**.</span></span>  
  
    -   <span data-ttu-id="e142c-129">若要查看問題的說明，請按一下 [**告訴我有關此問題的詳細資訊] 和 [解決方法**]。</span><span class="sxs-lookup"><span data-stu-id="e142c-129">To view help for the issue, click **Tell me more about this issue and how to resolve it**.</span></span>  
  
    -   <span data-ttu-id="e142c-130">若要將問題標示為已解決，這會在您再次查看報表時隱藏問題，請選取 [**此問題已解決**]。</span><span class="sxs-lookup"><span data-stu-id="e142c-130">To mark the issue as resolved, which hides the issue when you view the report again, select **This issue has been resolved**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e142c-131">報表可能會包含無法偵測之問題的項目。</span><span class="sxs-lookup"><span data-stu-id="e142c-131">The report may contain an item for undetectable issues.</span></span> <span data-ttu-id="e142c-132">這些是無法偵測或是會產生過多誤判結果的問題。</span><span class="sxs-lookup"><span data-stu-id="e142c-132">These are issues that cannot be detected or that would generate too many false-positive results.</span></span> <span data-ttu-id="e142c-133">按一下 [**告訴我有關此問題的詳細資訊] 和 [如何解決它**] 連結，以查看元件的無法偵測問題清單。</span><span class="sxs-lookup"><span data-stu-id="e142c-133">Click the **Tell me more about this issue and how to resolve it** link to see a list of undetectable issues for the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e142c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e142c-134">See Also</span></span>  
 <span data-ttu-id="e142c-135">[如何：匯出報表](../../../2014/sql-server/install/how-to-export-reports.md) </span><span class="sxs-lookup"><span data-stu-id="e142c-135">[How to: Export Reports](../../../2014/sql-server/install/how-to-export-reports.md) </span></span>  
 <span data-ttu-id="e142c-136">[如何：執行 Upgrade Advisor 分析嚮導](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="e142c-136">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="e142c-137">[解決升級問題](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="e142c-137">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="e142c-138">[Upgrade Advisor 的 how to 主題](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="e142c-138">[Upgrade Advisor How-to Topics](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span></span>  
 [<span data-ttu-id="e142c-139">使用升級建議程式</span><span class="sxs-lookup"><span data-stu-id="e142c-139">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
