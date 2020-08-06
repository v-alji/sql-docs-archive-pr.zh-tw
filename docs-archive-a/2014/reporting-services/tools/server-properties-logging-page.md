---
title: 伺服器屬性 (記錄頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a04c27fd790a1ad5c4ba453b43af5983a6440e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597014"
---
# <a name="server-properties-logging-page"></a><span data-ttu-id="815fb-102">伺服器屬性 (記錄頁面)</span><span class="sxs-lookup"><span data-stu-id="815fb-102">Server Properties (Logging Page)</span></span>
  <span data-ttu-id="815fb-103">使用此頁面，即可對報表伺服器所收集的報表執行資料設定限制。</span><span class="sxs-lookup"><span data-stu-id="815fb-103">Use this page to set limits on the report execution data that is collected by a report server.</span></span> <span data-ttu-id="815fb-104">執行資料會儲存在報表伺服器資料庫內部。</span><span class="sxs-lookup"><span data-stu-id="815fb-104">Execution data is stored internally in the report server database.</span></span> <span data-ttu-id="815fb-105">您可以針對以原生模式或 SharePoint 整合模式執行的報表伺服器追蹤報表活動。</span><span class="sxs-lookup"><span data-stu-id="815fb-105">You can track report activity for report server that runs in native mode or SharePoint integrated mode.</span></span> <span data-ttu-id="815fb-106">如果報表伺服器屬於向外延展部署的一部分，報表執行記錄就會在單一記錄檔中維護整個部署之所有報表活動的記錄。</span><span class="sxs-lookup"><span data-stu-id="815fb-106">If the report server is part of a scale-out deployment, the report execution log maintains a record of all report activity for the entire deployment in a single log file.</span></span>  
  
 <span data-ttu-id="815fb-107">若要開啟此頁面，請啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 、連接至報表伺服器、以滑鼠右鍵按一下報表伺服器名稱，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="815fb-107">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="815fb-108">按一下 **[記錄]** ，即可開啟此頁面。</span><span class="sxs-lookup"><span data-stu-id="815fb-108">Click **Logging** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="815fb-109">選項</span><span class="sxs-lookup"><span data-stu-id="815fb-109">Options</span></span>  
 <span data-ttu-id="815fb-110">**啟用報表執行記錄**</span><span class="sxs-lookup"><span data-stu-id="815fb-110">**Enable report execution logging**</span></span>  
 <span data-ttu-id="815fb-111">按一下即可建立和儲存有關伺服器之報表活動的資訊。</span><span class="sxs-lookup"><span data-stu-id="815fb-111">Click to create and store information about report activity on the server.</span></span> <span data-ttu-id="815fb-112">如果此選項已啟用，報表伺服器將會追蹤使用的報表、報表處理的頻率、執行的報表作業類型、輸出格式，以及執行報表的人員。</span><span class="sxs-lookup"><span data-stu-id="815fb-112">If this option is enabled, the report server will track which reports are used, the frequency of report processing, the type of report operation that was performed, the output format, and who ran the report.</span></span> <span data-ttu-id="815fb-113">如需有關記錄檔中所捕捉其他資料點的詳細資訊，請參閱[報表伺服器執行記錄和 ExecutionLog3 視圖](../report-server/report-server-executionlog-and-the-executionlog3-view.md)。</span><span class="sxs-lookup"><span data-stu-id="815fb-113">For more information about additional data points that are captured in the log, see [Report Server Execution Log and the ExecutionLog3 View](../report-server/report-server-executionlog-and-the-executionlog3-view.md).</span></span>  
  
 <span data-ttu-id="815fb-114">**移除此天數之前的記錄項目**</span><span class="sxs-lookup"><span data-stu-id="815fb-114">**Remove log entries older than this number of days**</span></span>  
 <span data-ttu-id="815fb-115">指定天數，在此天數後的記錄項目會從報表執行記錄中刪除。</span><span class="sxs-lookup"><span data-stu-id="815fb-115">Specify the number of days after which log entries will be trimmed from the report execution log.</span></span> <span data-ttu-id="815fb-116">預設值為 60 天。</span><span class="sxs-lookup"><span data-stu-id="815fb-116">The default value is 60 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815fb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="815fb-117">See Also</span></span>  
 <span data-ttu-id="815fb-118">[將報表伺服器屬性設定 &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="815fb-118">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="815fb-119">[連接到 Management Studio 中的報表伺服器](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="815fb-119">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="815fb-120">[Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="815fb-120">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="815fb-121">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="815fb-121">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="815fb-122">報表伺服器執行記錄和 ExecutionLog3 檢視</span><span class="sxs-lookup"><span data-stu-id="815fb-122">Report Server Execution Log and the ExecutionLog3 View</span></span>](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
