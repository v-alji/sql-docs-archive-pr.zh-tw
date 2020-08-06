---
title: 驗證報表執行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- auditing [Reporting Services]
- verifying report execution
- logs [Reporting Services], verifying report run
- report execution data [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services], verifying execution
- checking report execution
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c11c57f7c5f67b2557f5637ad10658abc9f80606
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595616"
---
# <a name="verifying-a-report-run"></a><span data-ttu-id="86770-102">驗證報表執行</span><span class="sxs-lookup"><span data-stu-id="86770-102">Verifying a Report Run</span></span>
  <span data-ttu-id="86770-103">若要檢視有關報表處理的狀態資訊，您可以使用記錄檔或參考報表管理員中與報表同時顯示的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="86770-103">To view information about the status of report processing, you can use log files or refer to status information that is displayed with the report in Report Manager.</span></span>  
  
## <a name="sources-of-report-execution-data"></a><span data-ttu-id="86770-104">報表執行資料的來源</span><span class="sxs-lookup"><span data-stu-id="86770-104">Sources of Report Execution Data</span></span>  
 <span data-ttu-id="86770-105">報表執行記錄提供有關報表執行的詳細資訊，包括報表的名稱、執行報表的使用者名稱、報表執行時間，以及用於散發報表的傳遞延伸模組。</span><span class="sxs-lookup"><span data-stu-id="86770-105">The report execution logs provide comprehensive information about report execution, including the name of the report, the name of the user who ran the report, report execution time, and the delivery extension used to distribute the report.</span></span> <span data-ttu-id="86770-106">若要檢視與分析此資料，您可以複製報表執行記錄至資料庫資料表，以便於查詢和報告。</span><span class="sxs-lookup"><span data-stu-id="86770-106">To view and analyze this data, you can copy the report execution log into database tables that are easy to query and report on.</span></span>  
  
 <span data-ttu-id="86770-107">記錄檔包含許多有關報表執行與其他伺服器活動的項目。</span><span class="sxs-lookup"><span data-stu-id="86770-107">Log files contain many entries about report execution and other server activity.</span></span> <span data-ttu-id="86770-108">因為記錄檔包含的資料很多，所以如果您只想確認報表上次執行的時間，就可以使用報表管理員。</span><span class="sxs-lookup"><span data-stu-id="86770-108">Because log files contain so much data, you may want to use Report Manager if you only want to verify when the report last ran.</span></span> <span data-ttu-id="86770-109">如果您需要其他資訊，就必須檢視記錄檔。</span><span class="sxs-lookup"><span data-stu-id="86770-109">If you require additional information, you must view the log files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="86770-110">報表管理員不會顯示在需要時執行之報表的處理時間。</span><span class="sxs-lookup"><span data-stu-id="86770-110">Report Manager does not show the processing times of reports that run on demand.</span></span>  
  
 <span data-ttu-id="86770-111">下表描述如何檢視不同類型報表的處理日期和時間。</span><span class="sxs-lookup"><span data-stu-id="86770-111">The following table describes how to view the processing date and time for various types of reports.</span></span>  
  
|<span data-ttu-id="86770-112">報表類型</span><span class="sxs-lookup"><span data-stu-id="86770-112">For this type of report</span></span>|<span data-ttu-id="86770-113">日期和時間資訊的記錄位置</span><span class="sxs-lookup"><span data-stu-id="86770-113">Date and time information is located here</span></span>|<span data-ttu-id="86770-114">若要檢視資訊，請執行下列步驟</span><span class="sxs-lookup"><span data-stu-id="86770-114">To view the information, do the following</span></span>|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|<span data-ttu-id="86770-115">以報表快照集形式執行的報表。</span><span class="sxs-lookup"><span data-stu-id="86770-115">A report that runs as a report snapshot.</span></span>|<span data-ttu-id="86770-116">在 [內容] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="86770-116">On the Contents page.</span></span> <span data-ttu-id="86770-117">如需詳細資訊，請參閱[內容頁面 &#40;報表管理員&#41;](../contents-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="86770-117">For more information, see [Contents Page &#40;Report Manager&#41;](../contents-page-report-manager.md).</span></span>|<span data-ttu-id="86770-118">1) 尋找包含報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="86770-118">1) Locate the folder that contains the report.</span></span><br /><span data-ttu-id="86770-119">2) 在 [詳細資料] 檢視中設定資料夾。</span><span class="sxs-lookup"><span data-stu-id="86770-119">2) Set the folder in Details view.</span></span><br /><span data-ttu-id="86770-120">3) 3) 記下 [**執行時**] 資料行中的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="86770-120">3) 3) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="86770-121">報表記錄中的快照集。</span><span class="sxs-lookup"><span data-stu-id="86770-121">A snapshot in report history.</span></span>|<span data-ttu-id="86770-122">在 [記錄屬性] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="86770-122">On the History Properties page.</span></span> <span data-ttu-id="86770-123">如需詳細資訊，請參閱[快照集選項屬性頁 &#40;報表管理員&#41;](../snapshot-options-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="86770-123">For more information, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../snapshot-options-properties-page-report-manager.md).</span></span>|<span data-ttu-id="86770-124">1) 開啟報表。</span><span class="sxs-lookup"><span data-stu-id="86770-124">1) Open the report.</span></span><br /><span data-ttu-id="86770-125">2) 按一下 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="86770-125">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="86770-126">3) 按一下 [記錄]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="86770-126">3) Click the **History** tab.</span></span><br /><span data-ttu-id="86770-127">4) 記下 [執行時]  資料行中的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="86770-127">4) Note the date and time in the **When Run** column.</span></span>|  
|<span data-ttu-id="86770-128">快取報表。</span><span class="sxs-lookup"><span data-stu-id="86770-128">A cached report.</span></span>|<span data-ttu-id="86770-129">在用於建立與重新整理快取報表的排程中。</span><span class="sxs-lookup"><span data-stu-id="86770-129">In the schedule used to create and refresh the cached report.</span></span>|<span data-ttu-id="86770-130">1) 開啟報表。</span><span class="sxs-lookup"><span data-stu-id="86770-130">1) Open the report.</span></span><br /><span data-ttu-id="86770-131">2) 按一下 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="86770-131">2) Click the **Properties** page.</span></span><br /><span data-ttu-id="86770-132">3) 按一下 [執行]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="86770-132">3) Click the **Execution** tab.</span></span><br /><span data-ttu-id="86770-133">4) 開啟排程。</span><span class="sxs-lookup"><span data-stu-id="86770-133">4) Open the schedule.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86770-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86770-134">See Also</span></span>  
 <span data-ttu-id="86770-135">[Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="86770-135">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 <span data-ttu-id="86770-136">[設定報表處理屬性](set-report-processing-properties.md) </span><span class="sxs-lookup"><span data-stu-id="86770-136">[Set Report Processing Properties](set-report-processing-properties.md) </span></span>  
 [<span data-ttu-id="86770-137">報表管理員 &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="86770-137">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
