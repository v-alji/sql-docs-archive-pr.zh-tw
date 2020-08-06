---
title: 設定報表的執行屬性 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report execution properties [Reporting Services]
- reports [Reporting Services], properties
- reports [Reporting Services], execution options
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 51cd7b5db225b39f5a061ed750b2ef5cdd265b9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607257"
---
# <a name="configure-execution-properties-for-a-report--report-manager"></a><span data-ttu-id="4cce7-102">設定報表的執行屬性 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="4cce7-102">Configure Execution Properties for a Report  (Report Manager)</span></span>
  <span data-ttu-id="4cce7-103">您可以設定報表處理選項，以便指定擷取報表資料的時間。</span><span class="sxs-lookup"><span data-stu-id="4cce7-103">You can set report processing options to specify when data is retrieved for a report.</span></span> <span data-ttu-id="4cce7-104">如果外部資料來源是在特定時間重新整理 (例如，每日或每週重新整理的資料倉儲)，而且您想要避免每次要求報表都擷取相同資料的負擔，排程報表的資料處理就很有用。</span><span class="sxs-lookup"><span data-stu-id="4cce7-104">It is useful to schedule data processing for a report if the external data source is refreshed at specific times (for example, a data warehouse that is refreshed daily or weekly) and you want to avoid the overhead of retrieving the same data each time a report is requested.</span></span> <span data-ttu-id="4cce7-105">此外，如果您想要控制外部資料庫伺服器的處理負載，或者當您想要針對必須使用相同資料集的多位使用者提供一致的結果時，排程資料處理也很有用。</span><span class="sxs-lookup"><span data-stu-id="4cce7-105">Scheduling data processing is also useful if you want to control the processing load on the external database server or when you want to provide consistent results for multiple users who must work with identical sets of data.</span></span> <span data-ttu-id="4cce7-106">若為變動資料，視需要報表可能會在不同的時間產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="4cce7-106">With volatile data, an on-demand report can produce different results from one minute to the next.</span></span> <span data-ttu-id="4cce7-107">相對地，報表快照集可讓您針對包含相同時間資料的其他報表或分析工具，進行有效的比較。</span><span class="sxs-lookup"><span data-stu-id="4cce7-107">A report snapshot, by contrast, allows you to make valid comparisons against other reports or analytical tools that contain data from the same point in time.</span></span>  
  
 <span data-ttu-id="4cce7-108">報表快照集是一種報表，它包含在特定時間點擷取的配置指示和查詢結果。</span><span class="sxs-lookup"><span data-stu-id="4cce7-108">A report snapshot is a report that contains layout instructions and query results that were retrieved at a specific point in time.</span></span> <span data-ttu-id="4cce7-109">報表快照集和視需要報表不同，視需要報表會在您選取報表時取得最新的查詢結果，而報表快照集是依排程處理，並儲存至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4cce7-109">Unlike on-demand reports, which get up-to-date query results when you select the report, report snapshots are processed on a schedule and then saved to a report server.</span></span> <span data-ttu-id="4cce7-110">您選取報表快照集以供檢視時，報表伺服器會從報表伺服器資料庫擷取儲存的報表，並顯示建立快照集當時的資料與配置。</span><span class="sxs-lookup"><span data-stu-id="4cce7-110">When you select a report snapshot for viewing, the report server retrieves the stored report from the report server database and shows the data and layout that were current for the report at the time the snapshot was created.</span></span>  
  
 <span data-ttu-id="4cce7-111">報表快照集不會以特定轉譯格式儲存。</span><span class="sxs-lookup"><span data-stu-id="4cce7-111">Report snapshots are not saved in a particular rendering format.</span></span> <span data-ttu-id="4cce7-112">而是只有在使用者或應用程式要求它時，報表快照集才以最後的檢視格式轉譯 (例如 HTML)。</span><span class="sxs-lookup"><span data-stu-id="4cce7-112">Instead, report snapshots are rendered in a final viewing format (such as HTML) only when a user or an application requests it.</span></span> <span data-ttu-id="4cce7-113">延遲轉譯讓快照集具有可攜性。</span><span class="sxs-lookup"><span data-stu-id="4cce7-113">Deferred rendering makes a snapshot portable.</span></span> <span data-ttu-id="4cce7-114">報表可以使用要求的裝置或 Web 瀏覽器的正確格式轉譯。</span><span class="sxs-lookup"><span data-stu-id="4cce7-114">The report can be rendered in the correct format for the requesting device or Web browser.</span></span>  
  
### <a name="to-configure-report-processing-options"></a><span data-ttu-id="4cce7-115">若要設定報表處理選項</span><span class="sxs-lookup"><span data-stu-id="4cce7-115">To configure report processing options</span></span>  
  
1.  <span data-ttu-id="4cce7-116">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="4cce7-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="4cce7-117">導覽至您想要設定處理選項的報表，然後開啟報表。</span><span class="sxs-lookup"><span data-stu-id="4cce7-117">Navigate to and open the report for which you want to set processing options.</span></span>  
  
 <span data-ttu-id="4cce7-118">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="4cce7-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
1.  <span data-ttu-id="4cce7-119">在下拉式功能表中，按一下 [管理]\*\*\*\*，然後選取 [處理選項]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4cce7-119">In the drop-down menu, click **Manage** and then select the **Processing Options** tab.</span></span>  
  
2.  <span data-ttu-id="4cce7-120">按一下 [從報表執行快照集轉譯此報表]\*\*\*\*，然後選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="4cce7-120">Click **Render this report from an execution snapshot, and then select one of the following options:**</span></span>  
  
    -   <span data-ttu-id="4cce7-121">如果想要建立快照集，請選取 [使用下列排程建立報表執行快照集]\*\*\*\*，然後定義報表特定的排程或從 [共用排程]\*\*\*\* 清單中選取。</span><span class="sxs-lookup"><span data-stu-id="4cce7-121">If you want to create a snapshot, select **Use the following schedule to create report execution snapshots**, and then either define a report-specific schedule or select from the **Shared schedule** list.</span></span>  
  
    -   <span data-ttu-id="4cce7-122">如果您要立即建立快照集，請選取 [當您在此頁面上按一下 [套用] 按鈕時，會建立報表快照集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4cce7-122">If you want to create a snapshot immediately, select **Create a report snapshot when you click the Apply button on this page**.</span></span>  
  
3.  <span data-ttu-id="4cce7-123">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="4cce7-123">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cce7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cce7-124">See Also</span></span>  
 <span data-ttu-id="4cce7-125">[設定報表處理屬性](../report-server/set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4cce7-125">[Set Report Processing Properties](../report-server/set-report-processing-properties.md) </span></span>  
 <span data-ttu-id="4cce7-126">[開啟並關閉報表 &#40;報表管理員&#41;](../reports/open-and-close-a-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4cce7-126">[Open and Close a Report &#40;Report Manager&#41;](../reports/open-and-close-a-report-report-manager.md) </span></span>  
 <span data-ttu-id="4cce7-127">[內容頁面 &#40;報表管理員&#41;](../contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4cce7-127">[Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="4cce7-128">[報表伺服器內容管理 &#40;SSRS 原生模式&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="4cce7-128">[Report Server Content Management &#40;SSRS Native Mode&#41;](../report-server/report-server-content-management-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="4cce7-129">處理選項屬性頁面 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="4cce7-129">Processing Options Properties Page &#40;Report Manager&#41;</span></span>](../processing-options-properties-page-report-manager.md)  
  
  
