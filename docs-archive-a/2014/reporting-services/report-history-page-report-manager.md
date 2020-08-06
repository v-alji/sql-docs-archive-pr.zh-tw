---
title: 報表記錄頁面 (報表管理員) |Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: 4070be8c1d6b0633131e96c665d4551c1b676a9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595646"
---
# <a name="report-history-page-report-manager"></a><span data-ttu-id="87ae1-102">報表記錄頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="87ae1-102">Report History Page (Report Manager)</span></span>

<span data-ttu-id="87ae1-103">使用 [報表記錄] 頁面來檢視產生和儲存一段時間的報表快照集。</span><span class="sxs-lookup"><span data-stu-id="87ae1-103">Use the Report History page to view report snapshots that are generated and stored over time.</span></span> <span data-ttu-id="87ae1-104">依據在報表伺服器上設定的選項，報表記錄可能只包含最近的快照集。</span><span class="sxs-lookup"><span data-stu-id="87ae1-104">Depending on options that are set on the report server, report history may contain only the more recent snapshots.</span></span>  
  

<span data-ttu-id="87ae1-105">報表記錄一定是在資源報表的內容中提供檢視的。</span><span class="sxs-lookup"><span data-stu-id="87ae1-105">Report history is always viewed within the context of the report from which it originates.</span></span> <span data-ttu-id="87ae1-106">您無法在某個位置中檢視報表伺服器上所有報表的記錄。</span><span class="sxs-lookup"><span data-stu-id="87ae1-106">You cannot view the history of all reports on a report server in one place.</span></span>  
  
<span data-ttu-id="87ae1-107">若要產生報表記錄，報表必須可以自主式執行 (亦即它必須使用預存認證；參數化的報表必須包含所有參數的預設參數值)。</span><span class="sxs-lookup"><span data-stu-id="87ae1-107">To generate report history, the report must be able to run unattended (that is, it must use stored credentials; parameterized reports must contain default parameter values for all parameters).</span></span> <span data-ttu-id="87ae1-108">可以手動或以排程作業來產生報表記錄。</span><span class="sxs-lookup"><span data-stu-id="87ae1-108">Report history can be generated manually or as a scheduled operation.</span></span> <span data-ttu-id="87ae1-109">報表的記錄屬性決定建立報表記錄的方式。</span><span class="sxs-lookup"><span data-stu-id="87ae1-109">History properties on the report determine the ways in which report history can be created.</span></span>  
  
<span data-ttu-id="87ae1-110">按一下報表記錄快照集即可檢視該快照集。</span><span class="sxs-lookup"><span data-stu-id="87ae1-110">You can click a report history snapshot to view it.</span></span> <span data-ttu-id="87ae1-111">報表記錄中顯示的快照集只能以建立日期和時間來區分。</span><span class="sxs-lookup"><span data-stu-id="87ae1-111">Snapshots that appear in report history are distinguished only by the date and time at which they were created.</span></span> <span data-ttu-id="87ae1-112">沒有視覺指示可以區分快照集是回應排程而建立或是手動作業所建立。</span><span class="sxs-lookup"><span data-stu-id="87ae1-112">There is no visual indication to distinguish whether a snapshot was generated in response to a schedule or a manual operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="87ae1-113">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="87ae1-113">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="87ae1-114">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="87ae1-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="87ae1-115">導覽</span><span class="sxs-lookup"><span data-stu-id="87ae1-115">Navigation</span></span>  
 <span data-ttu-id="87ae1-116">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="87ae1-116">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-report-history-page"></a><span data-ttu-id="87ae1-117">若要開啟報表記錄頁面</span><span class="sxs-lookup"><span data-stu-id="87ae1-117">To open the Report History page</span></span>  
  
1.  <span data-ttu-id="87ae1-118">開啟報表管理員，然後找出您想要檢視報表快照集的報表。</span><span class="sxs-lookup"><span data-stu-id="87ae1-118">Open Report Manager, and locate the report for which you want to view report snapshots.</span></span>  
  
2.  <span data-ttu-id="87ae1-119">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="87ae1-119">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="87ae1-120">在下拉式功能表中，按一下 **[檢視報表記錄]**。</span><span class="sxs-lookup"><span data-stu-id="87ae1-120">In the drop-down menu, click **View Report History**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="87ae1-121">選項</span><span class="sxs-lookup"><span data-stu-id="87ae1-121">Options</span></span>  
 <span data-ttu-id="87ae1-122">**刪除**</span><span class="sxs-lookup"><span data-stu-id="87ae1-122">**Delete**</span></span>  
 <span data-ttu-id="87ae1-123">按一下即可刪除一個或多個快照集。</span><span class="sxs-lookup"><span data-stu-id="87ae1-123">Click to delete one or more snapshots.</span></span> <span data-ttu-id="87ae1-124">在按一下 **[刪除]** 之前，請先選取要刪除之快照集旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="87ae1-124">Before clicking **Delete**, select the check box next to the snapshot that you want to delete.</span></span>  
  
 <span data-ttu-id="87ae1-125">**新增快照集**</span><span class="sxs-lookup"><span data-stu-id="87ae1-125">**New Snapshot**</span></span>  
 <span data-ttu-id="87ae1-126">按一下即可將快照集加入至報表記錄。</span><span class="sxs-lookup"><span data-stu-id="87ae1-126">Click to add a snapshot to report history.</span></span> <span data-ttu-id="87ae1-127">只有在報表的記錄屬性頁面上選擇 **[允許手動建立記錄]** 選項時，才能使用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="87ae1-127">This button is available when you choose the option **Allow history to be created manually** on the History properties page of the report.</span></span>  
  
 <span data-ttu-id="87ae1-128">**最後執行**</span><span class="sxs-lookup"><span data-stu-id="87ae1-128">**Last Run**</span></span>  
 <span data-ttu-id="87ae1-129">顯示建立快照集的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="87ae1-129">Displays the date and time at which the snapshot was created.</span></span> <span data-ttu-id="87ae1-130">按一下描述以檢視特殊快照集。</span><span class="sxs-lookup"><span data-stu-id="87ae1-130">Click a description to view a particular snapshot.</span></span>  
  
 <span data-ttu-id="87ae1-131">**大小**</span><span class="sxs-lookup"><span data-stu-id="87ae1-131">**Size**</span></span>  
 <span data-ttu-id="87ae1-132">顯示報表定義加報表中資料的大小。</span><span class="sxs-lookup"><span data-stu-id="87ae1-132">Displays the size of the report definition plus the data in the report.</span></span> <span data-ttu-id="87ae1-133">此值指出報表定義和資料使用報表伺服器資料庫中多少空間。</span><span class="sxs-lookup"><span data-stu-id="87ae1-133">This value indicates how much space in the report server database is used by the report definition and data.</span></span> <span data-ttu-id="87ae1-134">轉譯報表的大小 (包括格式) 實際上會比較大。</span><span class="sxs-lookup"><span data-stu-id="87ae1-134">The size of the rendered report, which includes formatting, is actually larger.</span></span> <span data-ttu-id="87ae1-135">括號中指出的總大小是目前報表的報表記錄中之所有快照集大小的總和。</span><span class="sxs-lookup"><span data-stu-id="87ae1-135">The total size, indicated in parentheses, sums the sizes of all snapshots in the report history for the current report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ae1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87ae1-136">See Also</span></span>  
 <span data-ttu-id="87ae1-137">[查看或刪除報表記錄 &#40;報表管理員&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="87ae1-137">[View or Delete Report History &#40;Report Manager&#41;](../../2014/reporting-services/view-or-delete-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="87ae1-138">[將快照集加入至報表記錄 &#40;報表管理員&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="87ae1-138">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="87ae1-139">[一般屬性頁面、報表 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="87ae1-139">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="87ae1-140">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="87ae1-140">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="87ae1-141">快照集選項屬性頁面 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="87ae1-141">Snapshot Options Properties Page &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/snapshot-options-properties-page-report-manager.md)