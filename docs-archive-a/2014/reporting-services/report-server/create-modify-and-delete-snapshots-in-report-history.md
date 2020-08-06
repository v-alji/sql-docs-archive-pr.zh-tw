---
title: 建立、修改及刪除報表記錄中的快照集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- snapshots [Reporting Services]
- report snapshots [Reporting Services]
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ee091ad3361280c4da258eb86c83492ade8b3bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597586"
---
# <a name="create-modify-and-delete-snapshots-in-report-history"></a><span data-ttu-id="f2444-102">建立、修改及刪除報表記錄中的快照集</span><span class="sxs-lookup"><span data-stu-id="f2444-102">Create, Modify, and Delete Snapshots in Report History</span></span>
  <span data-ttu-id="f2444-103">報表記錄是報表快照集的集合。</span><span class="sxs-lookup"><span data-stu-id="f2444-103">Report history is a collection of report snapshots.</span></span> <span data-ttu-id="f2444-104">您可以加入和刪除快照集，或修改影響報表記錄儲存區的屬性，來維護報表記錄。</span><span class="sxs-lookup"><span data-stu-id="f2444-104">You can maintain report history by adding and deleting snapshots, or by modifying properties that affect report history storage.</span></span> <span data-ttu-id="f2444-105">您可以用手動方式或依據排程來建立報表記錄。</span><span class="sxs-lookup"><span data-stu-id="f2444-105">You can create report history manually or on a schedule.</span></span>  
  
 <span data-ttu-id="f2444-106">若要建立報表記錄，您的角色指派必須包括「管理報表記錄」工作。</span><span class="sxs-lookup"><span data-stu-id="f2444-106">To create report history, your role assignment must include the "Manage report history" task.</span></span> <span data-ttu-id="f2444-107">若要檢視報表記錄，您的角色指派必須包括「檢視報表」工作。</span><span class="sxs-lookup"><span data-stu-id="f2444-107">To view report history, your role assignment must include the "View reports" task.</span></span> <span data-ttu-id="f2444-108">有報表存取權的使用者，都可以使用報表記錄。</span><span class="sxs-lookup"><span data-stu-id="f2444-108">Report history is available to all users who have access to the report.</span></span> <span data-ttu-id="f2444-109">您無法選擇性地針對部分使用者啟用或停用報表記錄。</span><span class="sxs-lookup"><span data-stu-id="f2444-109">You cannot selectively enable or disable report history for a subset of users.</span></span>  
  
 <span data-ttu-id="f2444-110">報表記錄中的快照集可以由建立的日期及時間加以識別。</span><span class="sxs-lookup"><span data-stu-id="f2444-110">Snapshots in report history are identified by the date and time that they were created.</span></span> <span data-ttu-id="f2444-111">日期及時間是以查詢的執行時間為準。</span><span class="sxs-lookup"><span data-stu-id="f2444-111">The date and time is based on when the query executed.</span></span>  
  
## <a name="creating-snapshots-in-report-history"></a><span data-ttu-id="f2444-112">在報表記錄中建立快照集</span><span class="sxs-lookup"><span data-stu-id="f2444-112">Creating Snapshots in Report History</span></span>  
 <span data-ttu-id="f2444-113">您可以用手動方式建立快照集，如果是可以自動執行的報表，就能夠依排定間隔建立快照集。</span><span class="sxs-lookup"><span data-stu-id="f2444-113">Snapshots can be created manually or at scheduled intervals for any report that can run unattended.</span></span> <span data-ttu-id="f2444-114">若要自動執行，報表必須使用預存認證，或完全不使用認證。</span><span class="sxs-lookup"><span data-stu-id="f2444-114">To run unattended, the report must use stored credentials or no credentials at all.</span></span> <span data-ttu-id="f2444-115">此外，若報表使用參數，您必須指定報表執行時使用的預設值。</span><span class="sxs-lookup"><span data-stu-id="f2444-115">Furthermore, if the report uses parameters, you must specify default values to use when the report runs.</span></span> <span data-ttu-id="f2444-116">您可以在報表的屬性頁面指定預存認證和參數值。</span><span class="sxs-lookup"><span data-stu-id="f2444-116">You can specify stored credentials and parameter values in the property pages for the report.</span></span> <span data-ttu-id="f2444-117">如需詳細資訊，請參閱[參數屬性頁面 &#40;報表管理員&#41;](../parameters-properties-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="f2444-117">For more information, see [Parameters Properties Page &#40;Report Manager&#41;](../parameters-properties-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="f2444-118">當您在建立報表快照集時，下列元素會和報表快照集一起儲存在報表伺服器資料庫中：</span><span class="sxs-lookup"><span data-stu-id="f2444-118">When you create a report snapshot, the following elements are stored along with the report snapshot in the report server database:</span></span>  
  
-   <span data-ttu-id="f2444-119">結果集 (就是報表中的資料，透過在報表的 [資料來源] 屬性頁面所指定的認證擷取而來的)。</span><span class="sxs-lookup"><span data-stu-id="f2444-119">The result set (that is, the data in the report, retrieved through the credentials specified in the Data Sources properties page of the report).</span></span>  
  
-   <span data-ttu-id="f2444-120">基礎報表定義，當快照集建立時便存在的定義。</span><span class="sxs-lookup"><span data-stu-id="f2444-120">The underlying report definition, as it exists at the time the snapshot was created.</span></span> <span data-ttu-id="f2444-121">如果在快照集產生之後，對報表定義做修改，所做的變更不會反映在快照集內。</span><span class="sxs-lookup"><span data-stu-id="f2444-121">If the report definition is subsequently modified after the snapshot is generated, those changes are not reflected in the snapshot.</span></span>  
  
-   <span data-ttu-id="f2444-122">用來取得或篩選結果集的參數值。</span><span class="sxs-lookup"><span data-stu-id="f2444-122">Parameter values that are used to obtain or filter the result set.</span></span>  
  
-   <span data-ttu-id="f2444-123">內嵌來源，例如影像。</span><span class="sxs-lookup"><span data-stu-id="f2444-123">Embedded resources, such as images.</span></span> <span data-ttu-id="f2444-124">連結到報表的外部來源，不會和報表快照集儲存在一起。</span><span class="sxs-lookup"><span data-stu-id="f2444-124">External resources that are linked to a report are not stored with the report snapshot.</span></span>  
  
 <span data-ttu-id="f2444-125">建立報表記錄的方式以及可儲存的報表快照集數量，是由設定值所決定。</span><span class="sxs-lookup"><span data-stu-id="f2444-125">The ways in which report history can be created and the number of report snapshots that can be stored are determined by settings.</span></span>  
  
 <span data-ttu-id="f2444-126">如果報表產生錯誤，就不會建立快照集。</span><span class="sxs-lookup"><span data-stu-id="f2444-126">If a report produces an error, a snapshot is not created.</span></span> <span data-ttu-id="f2444-127">產生警告的報表若可繼續執行，則可以用來產生快照集。</span><span class="sxs-lookup"><span data-stu-id="f2444-127">Reports that produce warnings, yet still run, can be used to generate snapshots.</span></span>  
  
## <a name="modifying-properties-and-deleting-report-history"></a><span data-ttu-id="f2444-128">修改屬性與刪除報表記錄</span><span class="sxs-lookup"><span data-stu-id="f2444-128">Modifying Properties and Deleting Report History</span></span>  
 <span data-ttu-id="f2444-129">一旦報表快照集已存在，便無法加以修改。</span><span class="sxs-lookup"><span data-stu-id="f2444-129">Once a report snapshot exists, you cannot modify it.</span></span> <span data-ttu-id="f2444-130">然而，您可以藉由修改屬性來刪除報表記錄。</span><span class="sxs-lookup"><span data-stu-id="f2444-130">However, you can modify properties in a way that deletes report history.</span></span>  
  
 <span data-ttu-id="f2444-131">以下為刪除報表記錄的方式：</span><span class="sxs-lookup"><span data-stu-id="f2444-131">Report history can be deleted in the following ways:</span></span>  
  
-   <span data-ttu-id="f2444-132">針對單一或群組，以手動的方式刪除快照集。</span><span class="sxs-lookup"><span data-stu-id="f2444-132">Manually delete snapshots singly or in groups.</span></span>  
  
     <span data-ttu-id="f2444-133">您可以從報表管理員的 [記錄] 頁面中刪除快照集。</span><span class="sxs-lookup"><span data-stu-id="f2444-133">You can delete snapshots from the History page in Report Manager.</span></span> <span data-ttu-id="f2444-134">導覽至報表，按一下 [記錄]，選取您要刪除的快照集旁邊的核取方塊，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="f2444-134">Navigate to the report, click History, select the check box next to the snapshots that you want to delete, and then click **Delete**.</span></span>  
  
-   <span data-ttu-id="f2444-135">降低報表記錄限制，以減少儲存的快照集數量。</span><span class="sxs-lookup"><span data-stu-id="f2444-135">Lower the report history limit to reduce the number of snapshots that are stored.</span></span> <span data-ttu-id="f2444-136">報表記錄限制可以針對報表伺服器或特定的報表進行設定。</span><span class="sxs-lookup"><span data-stu-id="f2444-136">The report history limit can be set for the report server or for specific reports.</span></span> <span data-ttu-id="f2444-137">當限制降低時，系統會從記錄中刪除最舊的快照集。</span><span class="sxs-lookup"><span data-stu-id="f2444-137">When the limit is lowered, the oldest snapshots are deleted from history.</span></span>  
  
 <span data-ttu-id="f2444-138">您無法以大量作業的方式，刪除儲存在報表伺服器中的所有報表記錄。</span><span class="sxs-lookup"><span data-stu-id="f2444-138">You cannot delete all report history stored on a report server in a bulk operation.</span></span>  
  
 <span data-ttu-id="f2444-139">刪除報表時，報表記錄也會一併刪除。</span><span class="sxs-lookup"><span data-stu-id="f2444-139">Report history is also deleted when you delete a report.</span></span> <span data-ttu-id="f2444-140">例如，若您刪除每月銷售額報表而以較新版本加以取代，則所有和該報表關聯的報表記錄也會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="f2444-140">For example, if you delete a monthly sales report because you are replacing it with a newer version, all report history that is associated with the report is also deleted.</span></span> <span data-ttu-id="f2444-141">然而，如果您移動報表，則所有報表記錄會隨著移動。</span><span class="sxs-lookup"><span data-stu-id="f2444-141">However, if you move a report, all report history moves with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2444-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2444-142">See Also</span></span>  
 <span data-ttu-id="f2444-143">[建立報表記錄 &#40;SharePoint 整合模式的 Reporting Services&#41;](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f2444-143">[Create Report History &#40;Reporting Services in SharePoint Integrated Mode&#41;](create-report-history-reporting-services-in-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="f2444-144">[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f2444-144">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f2444-145">[報表伺服器內容管理 &#40;SSRS 原生模式&#41;](report-server-content-management-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f2444-145">[Report Server Content Management &#40;SSRS Native Mode&#41;](report-server-content-management-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f2444-146">[將快照集加入報表記錄 &#40;報表管理員&#41;](add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f2444-146">[Add a Snapshot to Report History &#40;Report Manager&#41;](add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 [<span data-ttu-id="f2444-147">限制報表記錄 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="f2444-147">Limit Report History &#40;Report Manager&#41;</span></span>](../reports/limit-report-history-report-manager.md)  
  
  
