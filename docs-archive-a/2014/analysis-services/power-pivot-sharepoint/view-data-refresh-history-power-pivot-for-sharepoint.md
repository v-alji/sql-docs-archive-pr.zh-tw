---
title: 查看資料重新整理記錄 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- data refresh history [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 4c8d8aa8-794d-4f72-ace3-78d0e688e1a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: c7a858aedcbca7aa1436ff06bdf9ebc61724f511
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706869"
---
# <a name="view-data-refresh-history-powerpivot-for-sharepoint"></a><span data-ttu-id="095e6-102">檢視資料重新整理記錄 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="095e6-102">View Data Refresh History (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="095e6-103">資料重新整理記錄是 Excel 活頁簿中 PowerPivot 資料之所有資料重新整理活動的記錄。</span><span class="sxs-lookup"><span data-stu-id="095e6-103">Data refresh history is a record of all data refresh activity for PowerPivot data in an Excel workbook.</span></span> <span data-ttu-id="095e6-104">資料重新整理作業會依您提供的排程，在 SharePoint 伺服器陣列中 Analysis Services 伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="095e6-104">Data refresh operations are performed on an Analysis Services server instance in a SharePoint farm on a schedule that you provide.</span></span> <span data-ttu-id="095e6-105">根據預設，資料重新整理記錄會保留一年。</span><span class="sxs-lookup"><span data-stu-id="095e6-105">By default, data refresh history is retained for one year.</span></span> <span data-ttu-id="095e6-106">但是，伺服器陣列管理員可以為使用量和事件記錄指定不同的保留原則，用來決定資料重新整理記錄的保存時間。</span><span class="sxs-lookup"><span data-stu-id="095e6-106">However, a farm administrator can specify a different retention policy for usage and event history that determines how long data refresh records are kept.</span></span>  
  
 <span data-ttu-id="095e6-107">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 |SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="095e6-107">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 | SharePoint 2010</span></span>  
  
 <span data-ttu-id="095e6-108">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="095e6-108">**In this topic:**</span></span>  
  
 [<span data-ttu-id="095e6-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="095e6-109">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="095e6-110">檢視個別活頁簿的資料重新整理記錄</span><span class="sxs-lookup"><span data-stu-id="095e6-110">View Data Refresh History for an Individual Workbook</span></span>](#viewhistory)  
  
 [<span data-ttu-id="095e6-111">檢視所有活頁簿的資料重新整理記錄</span><span class="sxs-lookup"><span data-stu-id="095e6-111">View Data Refresh History for All Workbooks</span></span>](#viewITOps)  
  
 [<span data-ttu-id="095e6-112">使用記錄資訊</span><span class="sxs-lookup"><span data-stu-id="095e6-112">Use History Information</span></span>](#pageelements)  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="095e6-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="095e6-113">Prerequisites</span></span>  
 <span data-ttu-id="095e6-114">您必須擁有「參與」或以上的權限，才能檢視資料重新整理記錄。</span><span class="sxs-lookup"><span data-stu-id="095e6-114">You must have Contribute permissions or greater to view the data refresh history.</span></span>  
  
 <span data-ttu-id="095e6-115">您必須已在含 PowerPivot 資料的活頁簿上，啟用並排程資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="095e6-115">You must have enabled and scheduled data refresh on a workbook that contains PowerPivot data.</span></span> <span data-ttu-id="095e6-116">如果未排程資料重新整理，就會看到 [排程定義] 頁面，而不是 [記錄資訊] 頁面。</span><span class="sxs-lookup"><span data-stu-id="095e6-116">If you have not scheduled data refresh, you will see the schedule definition page instead of history information.</span></span>  
  
##  <a name="view-data-refresh-history-for-an-individual-workbook"></a><a name="viewhistory"></a><span data-ttu-id="095e6-117">查看個別活頁簿的資料重新整理記錄</span><span class="sxs-lookup"><span data-stu-id="095e6-117">View Data Refresh History for an Individual Workbook</span></span>  
  
1.  <span data-ttu-id="095e6-118">在 SharePoint 網站上，開啟包含具有 PowerPivot 資料之 Excel 活頁簿的文件庫。</span><span class="sxs-lookup"><span data-stu-id="095e6-118">On a SharePoint site, open the library that contains an Excel workbook that contains PowerPivot data.</span></span>  
  
     <span data-ttu-id="095e6-119">沒有任何視覺指標，可識別在 SharePoint 文件庫中的哪個活頁簿包含 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="095e6-119">There is no visual indicator that identifies which workbooks in a SharePoint library contain PowerPivot data.</span></span> <span data-ttu-id="095e6-120">您必須事先知道哪個活頁簿包含可重新整理的 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="095e6-120">You must know in advance which workbook contains refreshable PowerPivot data.</span></span>  
  
2.  <span data-ttu-id="095e6-121">選取該活頁簿，然後按一下出現在右邊的向下箭號。</span><span class="sxs-lookup"><span data-stu-id="095e6-121">Select the workbook, and then click the down arrow that appears to the right.</span></span>  
  
3.  <span data-ttu-id="095e6-122">選取 **[管理 PowerPivot 資料重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="095e6-122">Select **Manage PowerPivot Data Refresh**.</span></span>  
  
 <span data-ttu-id="095e6-123">記錄頁面隨即出現，其中顯示目前 Excel 活頁簿中 PowerPivot 資料之所有重新整理活動的完整記錄。</span><span class="sxs-lookup"><span data-stu-id="095e6-123">The history page appears, showing a complete record for all refresh activity for PowerPivot data in the current Excel workbook.</span></span>  
  
##  <a name="view-data-refresh-history-for-all-workbooks"></a><a name="viewITOps"></a><span data-ttu-id="095e6-124">查看所有活頁簿的資料重新整理記錄</span><span class="sxs-lookup"><span data-stu-id="095e6-124">View Data Refresh History for All Workbooks</span></span>  
 <span data-ttu-id="095e6-125">伺服器陣列管理員和服務應用程式管理員可以使用管理中心的 PowerPivot 管理儀表板，取得完整的資料重新整理記錄檢視，以及所有 PowerPivot 活頁簿的狀態。</span><span class="sxs-lookup"><span data-stu-id="095e6-125">Using the PowerPivot Management Dashboard in Central administration, farm administrators and service application administrators can get a comprehensive view of data refresh history and status for all PowerPivot workbooks.</span></span> <span data-ttu-id="095e6-126">如需詳細資訊，請參閱＜ [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md)＞。</span><span class="sxs-lookup"><span data-stu-id="095e6-126">For more information, see [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).</span></span>  
  
##  <a name="use-history-information"></a><a name="pageelements"></a><span data-ttu-id="095e6-127">使用歷程記錄資訊</span><span class="sxs-lookup"><span data-stu-id="095e6-127">Use History Information</span></span>  
 <span data-ttu-id="095e6-128">[資料重新整理記錄] 頁面提供有關每項重新整理作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="095e6-128">The data refresh history page provides detailed information about each refresh operation.</span></span> <span data-ttu-id="095e6-129">您可以使用此頁面上的資訊，以確認是否已進行重新整理，或判斷作業失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="095e6-129">You can use the information on this page to confirm whether refresh occurred or determine why it failed.</span></span>  
  
|<span data-ttu-id="095e6-130">項目</span><span class="sxs-lookup"><span data-stu-id="095e6-130">Item</span></span>|<span data-ttu-id="095e6-131">描述</span><span class="sxs-lookup"><span data-stu-id="095e6-131">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="095e6-132">名稱</span><span class="sxs-lookup"><span data-stu-id="095e6-132">Name</span></span>|<span data-ttu-id="095e6-133">指定含 PowerPivot 資料之 Excel 活頁簿的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="095e6-133">Specifies the file name of the Excel workbook that contains PowerPivot data.</span></span>|  
|<span data-ttu-id="095e6-134">目前狀態</span><span class="sxs-lookup"><span data-stu-id="095e6-134">Current status</span></span>|<span data-ttu-id="095e6-135">值包括：[已排程]\*\*\*\*、[正在重新整理]\*\*\*\*、[成功]\*\*\*\* 或 [失敗]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="095e6-135">Values include **Scheduled**, **Refreshing**, **Succeeded**, or **Failed**.</span></span><br /><br /> <span data-ttu-id="095e6-136">**已排程** ：當您初次建立排程時會顯示此值。</span><span class="sxs-lookup"><span data-stu-id="095e6-136">**Scheduled** appears when you first create the schedule.</span></span> <span data-ttu-id="095e6-137">資料重新整理執行過第一次後，就不會再出現此狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="095e6-137">After data refresh runs the first time, this status message no longer appears.</span></span><br /><br /> <span data-ttu-id="095e6-138">**正在重新整理** ：表示該資料重新整理在進行中。</span><span class="sxs-lookup"><span data-stu-id="095e6-138">**Refreshing** indicates that data refresh is in progress.</span></span> <span data-ttu-id="095e6-139">要求是在程序佇列中，或正在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="095e6-139">A request is either in the process queue or actively running on the server.</span></span><br /><br /> <span data-ttu-id="095e6-140">**成功** ：表示上次資料重新整理作業已完成，而且已將更新的活頁簿存回 SharePoint 文件庫中。</span><span class="sxs-lookup"><span data-stu-id="095e6-140">**Succeeded** indicates that the last data refresh operation completed and the updated workbook is checked back into the SharePoint library.</span></span><br /><br /> <span data-ttu-id="095e6-141">**失敗** ：表示上次資料重新整理作業並未成功。</span><span class="sxs-lookup"><span data-stu-id="095e6-141">**Failed** indicates that the last data refresh operation did not succeed.</span></span> <span data-ttu-id="095e6-142">已重新整理資料並未儲存。</span><span class="sxs-lookup"><span data-stu-id="095e6-142">The refreshed data was not saved.</span></span> <span data-ttu-id="095e6-143">活頁簿中所包含的資料與資料重新整理開始之前相同。</span><span class="sxs-lookup"><span data-stu-id="095e6-143">The workbook contains the same data it had before data refresh began.</span></span>|  
|<span data-ttu-id="095e6-144">上次成功重新整理</span><span class="sxs-lookup"><span data-stu-id="095e6-144">Last successful refresh</span></span>|<span data-ttu-id="095e6-145">指定上次順利完成資料重新整理的日期。</span><span class="sxs-lookup"><span data-stu-id="095e6-145">Specifies the date on which the last data refresh completed successfully.</span></span>|  
|<span data-ttu-id="095e6-146">下次排程更新</span><span class="sxs-lookup"><span data-stu-id="095e6-146">Next schedule refresh</span></span>|<span data-ttu-id="095e6-147">指定下次排程要進行資料重新整理的日期。</span><span class="sxs-lookup"><span data-stu-id="095e6-147">Specifies the date on which the next data refresh is scheduled to occur.</span></span><br /><br /> <span data-ttu-id="095e6-148">[正在設定排程]\*\*\*\* 連結會跳至 [排程定義] 頁面。</span><span class="sxs-lookup"><span data-stu-id="095e6-148">The **Configure schedule** link takes you to the schedule definition page.</span></span> <span data-ttu-id="095e6-149">如果您在活頁簿上擁有「參與」權限，您可以按一下連結以檢視及修改排程資訊，控制活頁簿中 PowerPivot 資料的自動資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="095e6-149">If you have Contribute permissions on the workbook, you can click the link to view and modify the schedule information that controls unattended data refresh for PowerPivot data in the workbook.</span></span>|  
|<span data-ttu-id="095e6-150">已開始</span><span class="sxs-lookup"><span data-stu-id="095e6-150">Started</span></span>|<span data-ttu-id="095e6-151">在 [記錄詳細資料] 區段之中，[已啟動]\*\*\*\* 會指出實際的處理時間。</span><span class="sxs-lookup"><span data-stu-id="095e6-151">Within the history details section, **Started** indicates the actual processing time.</span></span> <span data-ttu-id="095e6-152">實際的處理時間可能與您的排程不同。</span><span class="sxs-lookup"><span data-stu-id="095e6-152">The actual processing time might be different from what you scheduled.</span></span> <span data-ttu-id="095e6-153">在伺服器上有足夠記憶體可用時，就會開始進行處理。</span><span class="sxs-lookup"><span data-stu-id="095e6-153">Processing will begin when sufficient memory is available on the server.</span></span> <span data-ttu-id="095e6-154">如果伺服器非常忙碌，可能會在您指定的開始時間之後數小時，才開始進行處理。</span><span class="sxs-lookup"><span data-stu-id="095e6-154">If the server is very busy, the processing might begin several hours after the start time you specified.</span></span>|  
|<span data-ttu-id="095e6-155">Completed</span><span class="sxs-lookup"><span data-stu-id="095e6-155">Completed</span></span>|<span data-ttu-id="095e6-156">在 [記錄詳細資料] 區段之中，[已完成]\*\*\*\* 會指出資料重新整理作業完成的時間。</span><span class="sxs-lookup"><span data-stu-id="095e6-156">Within the history details section, **Completed** indicates when the data refresh operation finished.</span></span> <span data-ttu-id="095e6-157">日期和時間表示活頁簿存回文件庫時的時間。</span><span class="sxs-lookup"><span data-stu-id="095e6-157">The date and time indicates when the workbook was checked back into the library.</span></span><br /><br /> <span data-ttu-id="095e6-158">如果資料重新整理失敗，會有一則或多則錯誤訊息說明失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="095e6-158">If data refresh fails, one or more error messages explain the cause of the failure.</span></span> <span data-ttu-id="095e6-159">您可以展開每項記錄，以檢視詳細的狀態。</span><span class="sxs-lookup"><span data-stu-id="095e6-159">You can expand each record to view detailed status.</span></span> <span data-ttu-id="095e6-160">每個資料來源都會個別列出，旁邊會有成功或失敗訊息，說明資料重新整理未完成的原因。</span><span class="sxs-lookup"><span data-stu-id="095e6-160">Each data source is listed individually, alongside success or failure messages that explain why data refresh did not complete.</span></span>|  
|<span data-ttu-id="095e6-161">Time</span><span class="sxs-lookup"><span data-stu-id="095e6-161">Time</span></span>|<span data-ttu-id="095e6-162">提供從資料重新整理開始到完成的累計時間。</span><span class="sxs-lookup"><span data-stu-id="095e6-162">Provides the cumulative time from when data refresh started to when it was completed.</span></span>|  
|<span data-ttu-id="095e6-163">狀態</span><span class="sxs-lookup"><span data-stu-id="095e6-163">Status</span></span>|<span data-ttu-id="095e6-164">提供重新整理作業成功或失敗的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="095e6-164">Provides a historical record of whether a refresh operation succeeded or failed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="095e6-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="095e6-165">See Also</span></span>  
 <span data-ttu-id="095e6-166">[設定 &#40;PowerPivot for SharePoint 的使用量資料收集](configure-usage-data-collection-for-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="095e6-166">[Configure Usage Data Collection for &#40;PowerPivot for SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="095e6-167">[排程資料重新整理 &#40;PowerPivot for SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="095e6-167">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="095e6-168">PowerPivot 資料重新整理</span><span class="sxs-lookup"><span data-stu-id="095e6-168">PowerPivot Data Refresh</span></span>](power-pivot-data-refresh.md)  
  
  
