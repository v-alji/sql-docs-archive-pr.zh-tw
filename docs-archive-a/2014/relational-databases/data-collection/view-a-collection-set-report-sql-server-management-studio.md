---
title: 檢視收集組報表 (SQL Server Management Studio) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.reporthistory.calendar.f1
helpviewer_keywords:
- collection sets [SQL Server], viewing reports
- reports [SQL Server], viewing collection set
ms.assetid: c3b1e791-9aa1-4bba-9622-4954568e1820
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cb8755c67e6c03bb318fdb86d703f6d647d5a3eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599013"
---
# <a name="view-a-collection-set-report-sql-server-management-studio"></a><span data-ttu-id="cb37c-102">檢視收集組報表 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="cb37c-102">View a Collection Set Report (SQL Server Management Studio)</span></span>
  <span data-ttu-id="cb37c-103">設定管理資料倉儲之後，您就可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中檢視收集組報表。</span><span class="sxs-lookup"><span data-stu-id="cb37c-103">After you have configured the management data warehouse, you can view a collection set report in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cb37c-104">這些報表是針對安裝期間所安裝的系統資料收集組提供的。</span><span class="sxs-lookup"><span data-stu-id="cb37c-104">Reports are provided for the System Data collection sets that are installed during Setup.</span></span> <span data-ttu-id="cb37c-105">這些報表包括：</span><span class="sxs-lookup"><span data-stu-id="cb37c-105">The reports include the following:</span></span>  
  
-   <span data-ttu-id="cb37c-106">磁碟使用量摘要</span><span class="sxs-lookup"><span data-stu-id="cb37c-106">Disk Usage Summary</span></span>  
  
-   <span data-ttu-id="cb37c-107">查詢統計資料記錄</span><span class="sxs-lookup"><span data-stu-id="cb37c-107">Query Statistics History</span></span>  
  
-   <span data-ttu-id="cb37c-108">伺服器活動記錄</span><span class="sxs-lookup"><span data-stu-id="cb37c-108">Server Activity History</span></span>  
  
 <span data-ttu-id="cb37c-109">這個程序會顯示 [磁碟使用量]  收集組的報表。</span><span class="sxs-lookup"><span data-stu-id="cb37c-109">This procedure displays the report for the **Disk Usage** collection set.</span></span> <span data-ttu-id="cb37c-110">您可以遵循相同的一般程序來檢視其他系統資料收集組的報表。</span><span class="sxs-lookup"><span data-stu-id="cb37c-110">You can follow the same general procedure to view the reports for the other System Data collection sets.</span></span>  
  
### <a name="to-view-a-collection-set-report"></a><span data-ttu-id="cb37c-111">若要檢視收集組報表</span><span class="sxs-lookup"><span data-stu-id="cb37c-111">To view a collection set report</span></span>  
  
1.  <span data-ttu-id="cb37c-112">報表的資料表是在第一次上傳所收集的資料時建立的。</span><span class="sxs-lookup"><span data-stu-id="cb37c-112">The tables for a report are created the first time that the collected data is uploaded.</span></span> <span data-ttu-id="cb37c-113">如果您嘗試在第一次上傳之前檢視報表，將會發生錯誤，而且不會顯示任何報表。</span><span class="sxs-lookup"><span data-stu-id="cb37c-113">If you try to view a report before this first upload, an error occurs and no report is displayed.</span></span> <span data-ttu-id="cb37c-114">若要上傳 [磁碟使用量] 收集組的資料，請在物件總管中，依序展開 [管理]  資料夾、[資料收集]  和 [系統資料收集組]  ，以滑鼠右鍵按一下 [磁碟使用量]  收集組，然後按一下 [立即收集和上傳]  。</span><span class="sxs-lookup"><span data-stu-id="cb37c-114">To upload data for the Disk Usage collection set, in Object Explorer, expand the **Management** folder, expand **Data Collection**, expand **System Data Collection Sets**, right-click the **Disk Usage** collection set, and then click **Collect and Upload Now**.</span></span>  
  
2.  <span data-ttu-id="cb37c-115">若要檢視報表，請在物件總管中，展開 [管理]  資料夾，以滑鼠右鍵按一下 [資料收集]  ，依序指向 [報表]  和 [管理資料倉儲]  ，然後按一下 [磁碟使用量摘要]  。</span><span class="sxs-lookup"><span data-stu-id="cb37c-115">To view the report, in Object Explorer, expand the **Management** folder, right-click **Data Collection**, point to **Reports**, point to **Management Data Warehouse**, and then click **Disk Usage Summary**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb37c-116">有些報告可能會在資料收集時間表下方顯示行事曆按鈕。</span><span class="sxs-lookup"><span data-stu-id="cb37c-116">Some reports might display a calendar button under the data collection timeline.</span></span> <span data-ttu-id="cb37c-117">按一下此按鈕可存取 [資料收集報表行事曆]  。</span><span class="sxs-lookup"><span data-stu-id="cb37c-117">Click this button to access the **Data Collection Report Calendar**.</span></span>  
  
#### <a name="data-collection-report-calendar"></a><span data-ttu-id="cb37c-118">資料收集報表行事曆</span><span class="sxs-lookup"><span data-stu-id="cb37c-118">Data Collection Report Calendar</span></span>  
 <span data-ttu-id="cb37c-119">使用這個對話方塊指定開始日期、開始時間以及您要報告之資料的持續時間。</span><span class="sxs-lookup"><span data-stu-id="cb37c-119">Use this dialog box to specify the start date, start time, and duration of the data that you want to report on.</span></span> <span data-ttu-id="cb37c-120">例如，您可能想要針對上週三的特定 12 小時期間，報告伺服器的磁碟使用量活動。</span><span class="sxs-lookup"><span data-stu-id="cb37c-120">For example, you may want to report on the disk usage activity of a server for a specific 12-hour period last Wednesday.</span></span>  
  
 <span data-ttu-id="cb37c-121">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="cb37c-121">**Start date**</span></span>  
 <span data-ttu-id="cb37c-122">輸入報告資料的開始日期，或從行事曆選取日期。</span><span class="sxs-lookup"><span data-stu-id="cb37c-122">Enter a beginning date for the report data, or select one from the calendar.</span></span>  
  
 <span data-ttu-id="cb37c-123">**開始時間**</span><span class="sxs-lookup"><span data-stu-id="cb37c-123">**Start time**</span></span>  
 <span data-ttu-id="cb37c-124">輸入報告資料的開始時間，或按一下箭頭來指定時間。</span><span class="sxs-lookup"><span data-stu-id="cb37c-124">Enter a beginning time for the report data or specify one by clicking the arrows.</span></span>  
  
 <span data-ttu-id="cb37c-125">**有效期間**</span><span class="sxs-lookup"><span data-stu-id="cb37c-125">**Duration**</span></span>  
 <span data-ttu-id="cb37c-126">指定報告中要包含的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="cb37c-126">Specify the time range to include in the report.</span></span> <span data-ttu-id="cb37c-127">預設值為 240 分鐘。</span><span class="sxs-lookup"><span data-stu-id="cb37c-127">The default value is 240 minutes.</span></span> <span data-ttu-id="cb37c-128">可選取的值包括 15 分鐘、60 分鐘、240 分鐘 (4 小時)、720 分鐘 (12 小時) 和 1440 分鐘 (24 小時)。</span><span class="sxs-lookup"><span data-stu-id="cb37c-128">The possible values to select from are 15 minutes, 60 minutes, 240 minutes (4 hours), 720 minutes (12 hours), and 1440 minutes (24 hours).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb37c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb37c-129">See Also</span></span>  
 <span data-ttu-id="cb37c-130">[資料收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="cb37c-130">[Data Collection](data-collection.md) </span></span>  
 <span data-ttu-id="cb37c-131">[Management Studio 中的自訂報表](../../ssms/object/custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="cb37c-131">[Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) </span></span>  
 [<span data-ttu-id="cb37c-132">設定管理資料倉儲 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="cb37c-132">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
  
