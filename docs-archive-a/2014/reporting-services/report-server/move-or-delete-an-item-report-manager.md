---
title: 移動或刪除項目 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- moving items
- items [Reporting Services], moving
ms.assetid: 980a66c7-a18b-4af7-8954-45726fa517d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a61ad56ea9e20e7fdf38d5acf05529b685ee896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686768"
---
# <a name="move-or-delete-an-item-report-manager"></a><span data-ttu-id="a8265-102">移動或刪除項目 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="a8265-102">Move or Delete an Item (Report Manager)</span></span>
  <span data-ttu-id="a8265-103">您發行至報表伺服器的報表和報表相關項目會儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a8265-103">Reports and report-related items that you publish to a report server are stored in folders.</span></span> <span data-ttu-id="a8265-104">您可以將項目移至不同的資料夾，報表伺服器會自動維護這些項目的參考。</span><span class="sxs-lookup"><span data-stu-id="a8265-104">You can move items to a different folder and references to those items are maintained automatically by the report server.</span></span> <span data-ttu-id="a8265-105">刪除某個項目之前，請考慮是否有其他項目相依於該項目。</span><span class="sxs-lookup"><span data-stu-id="a8265-105">Before you delete an item, consider whether other items depend on it.</span></span>  
  
## <a name="move-an-item"></a><span data-ttu-id="a8265-106">移動項目</span><span class="sxs-lookup"><span data-stu-id="a8265-106">Move an Item</span></span>  
 <span data-ttu-id="a8265-107">您可以將報表伺服器項目移至報表伺服器資料夾階層中不同的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="a8265-107">You can move report server items to different folder locations in the report server folder hierarchy.</span></span> <span data-ttu-id="a8265-108">當您移動項目時，所有屬性 (包括安全性設定) 都會跟著項目移到新位置。</span><span class="sxs-lookup"><span data-stu-id="a8265-108">When you move an item, all properties (including security settings) move with the item to the new location.</span></span> <span data-ttu-id="a8265-109">您移動資料夾時，資料夾內的所有項目都會隨著一起移動。</span><span class="sxs-lookup"><span data-stu-id="a8265-109">When you move a folder, all the items in the folder move with it.</span></span>  
  
 <span data-ttu-id="a8265-110">在報表管理員中，資料夾階層中會指出可以移動的項目。</span><span class="sxs-lookup"><span data-stu-id="a8265-110">In Report Manager, the items that you can move are indicated in the folder hierarchy.</span></span> <span data-ttu-id="a8265-111">下表顯示每一個可移動項目的圖示。</span><span class="sxs-lookup"><span data-stu-id="a8265-111">The following table shows the icon for each movable item.</span></span>  
  
|<span data-ttu-id="a8265-112">圖示</span><span class="sxs-lookup"><span data-stu-id="a8265-112">Icon</span></span>|<span data-ttu-id="a8265-113">可移動項目</span><span class="sxs-lookup"><span data-stu-id="a8265-113">Moveable item</span></span>|  
|----------|-------------------|  
|<span data-ttu-id="a8265-114">![Report icon](../media/hlp-16doc.gif "報表圖示")</span><span class="sxs-lookup"><span data-stu-id="a8265-114">![Report icon](../media/hlp-16doc.gif "Report icon")</span></span>|<span data-ttu-id="a8265-115">Report</span><span class="sxs-lookup"><span data-stu-id="a8265-115">Report</span></span>|  
|<span data-ttu-id="a8265-116">![連結報表圖示](../media/hlp-16linked.gif "連結報表圖示")</span><span class="sxs-lookup"><span data-stu-id="a8265-116">![Linked report icon](../media/hlp-16linked.gif "Linked report icon")</span></span>|<span data-ttu-id="a8265-117">連結報表</span><span class="sxs-lookup"><span data-stu-id="a8265-117">Linked report</span></span>|  
|<span data-ttu-id="a8265-118">![資料夾圖示](../media/hlp-16folder.gif "資料夾圖示")</span><span class="sxs-lookup"><span data-stu-id="a8265-118">![Folder icon](../media/hlp-16folder.gif "Folder icon")</span></span>|<span data-ttu-id="a8265-119">資料夾</span><span class="sxs-lookup"><span data-stu-id="a8265-119">Folder</span></span>|  
|<span data-ttu-id="a8265-120">![一般資源圖示](../media/hlp-16file.gif "一般資源圖示")</span><span class="sxs-lookup"><span data-stu-id="a8265-120">![generic resource icon](../media/hlp-16file.gif "generic resource icon")</span></span>|<span data-ttu-id="a8265-121">一般資源</span><span class="sxs-lookup"><span data-stu-id="a8265-121">Generic resource</span></span>|  
|<span data-ttu-id="a8265-122">![Shared data source icon](../media/hlp-16datasource.png "共用資料來源圖示")</span><span class="sxs-lookup"><span data-stu-id="a8265-122">![Shared data source icon](../media/hlp-16datasource.png "Shared data source icon")</span></span>|<span data-ttu-id="a8265-123">共用資料來源</span><span class="sxs-lookup"><span data-stu-id="a8265-123">Shared data source</span></span>|  
||<span data-ttu-id="a8265-124">共用資料集</span><span class="sxs-lookup"><span data-stu-id="a8265-124">Shared dataset</span></span>|  
  
 <span data-ttu-id="a8265-125">並非所有的項目都可以移動。</span><span class="sxs-lookup"><span data-stu-id="a8265-125">Not all items that you work with can be moved.</span></span> <span data-ttu-id="a8265-126">您無法移動與報表相關聯的項目，例如訂閱或報表記錄。</span><span class="sxs-lookup"><span data-stu-id="a8265-126">You cannot move items that are associated with a report, such as subscriptions or report history.</span></span> <span data-ttu-id="a8265-127">那些項目會隨著相關聯的報表移動。</span><span class="sxs-lookup"><span data-stu-id="a8265-127">Those items move with their associated reports.</span></span> <span data-ttu-id="a8265-128">同樣地，您無法移動存在於資料夾階層之外的項目 (例如共用排程)。</span><span class="sxs-lookup"><span data-stu-id="a8265-128">Similarly, you cannot move items, such as shared schedules, that exist outside of the folder hierarchy.</span></span> <span data-ttu-id="a8265-129">如果您沒有權限也無法移動項目。</span><span class="sxs-lookup"><span data-stu-id="a8265-129">You cannot move items if you lack permission to do so.</span></span> <span data-ttu-id="a8265-130">在您的角色指派中為目標項目選取下列工作時，即涵蓋移動項目的權限：「管理報表」、「管理模型」、「管理資料夾」，以及「管理資料來源」。</span><span class="sxs-lookup"><span data-stu-id="a8265-130">Permission to move an item is conveyed when the following tasks are selected in your role assignment for the item in question: "Manage reports," "Manage models", "Manage folders," and "Manage data sources."</span></span>  
  
#### <a name="to-move-an-item-from-within-the-contents-page"></a><span data-ttu-id="a8265-131">若要從內容頁面中移動項目</span><span class="sxs-lookup"><span data-stu-id="a8265-131">To move an item from within the Contents page</span></span>  
  
1.  <span data-ttu-id="a8265-132">啟動 [報表管理員 &#40;SSRS 原生模式&#41;].。/report-manager-ssrs-native-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="a8265-132">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="a8265-133">在報表管理員中，巡覽至 [內容]  頁面，然後找出您要移動的項目。</span><span class="sxs-lookup"><span data-stu-id="a8265-133">In Report Manager, navigate to the **Contents** page, and locate the item that you want to move.</span></span>  
  
3.  <span data-ttu-id="a8265-134">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="a8265-134">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="a8265-135">在下拉式功能表中，按一下 **[移動]** 。</span><span class="sxs-lookup"><span data-stu-id="a8265-135">In the drop-down menu, click **Move**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="a8265-136">針對 [位置]  ，請指定您要移動項目的目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="a8265-136">For **Location**, specify the folder you want to move the item to.</span></span> <span data-ttu-id="a8265-137">您可以輸入完整資料夾名稱，或使用樹狀目錄控制項導覽至資料夾。</span><span class="sxs-lookup"><span data-stu-id="a8265-137">You can type the fully qualified folder name or use the tree control to navigate to the folder.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="a8265-138">或者，您可以巡覽至要移動的物件、按一下 [屬性]  ，然後按一下頁面頂端的 [移動]  。</span><span class="sxs-lookup"><span data-stu-id="a8265-138">Alternatively, you can navigate to the object you want to move, click **Properties**, and then click **Move** at the top of the page.</span></span>  
  
## <a name="delete-an-item"></a><span data-ttu-id="a8265-139">刪除項目</span><span class="sxs-lookup"><span data-stu-id="a8265-139">Delete an item</span></span>  
 <span data-ttu-id="a8265-140">刪除某個項目之前，請判斷是否有其他項目使用該項目。</span><span class="sxs-lookup"><span data-stu-id="a8265-140">Before you delete an item, determine if it is used by other items.</span></span> <span data-ttu-id="a8265-141">例如，如果您刪除了某個共用資料來源，使用該資料來源的報表和模型將無法再執行。</span><span class="sxs-lookup"><span data-stu-id="a8265-141">For example, if you delete a shared data source, reports and models that use that data source will no longer run.</span></span> <span data-ttu-id="a8265-142">如果您刪除了某份報表，就會一併刪除與該報表相關聯的訂閱和報表記錄。</span><span class="sxs-lookup"><span data-stu-id="a8265-142">If you delete a report, subscriptions and report history associated with that report are also deleted.</span></span> <span data-ttu-id="a8265-143">若要尋找專案的相依專案，請參閱 [相依專案] 頁面 &#40;報表管理員&#41;]。/dependent-items-page-report-manager.md) 。</span><span class="sxs-lookup"><span data-stu-id="a8265-143">To find dependent items for an item, see [Dependent Items Page &#40;Report Manager&#41;]../dependent-items-page-report-manager.md).</span></span>  
  
#### <a name="to-delete-a-report-or-item"></a><span data-ttu-id="a8265-144">若要刪除報表或項目</span><span class="sxs-lookup"><span data-stu-id="a8265-144">To delete a report or item</span></span>  
  
1.  <span data-ttu-id="a8265-145">啟動 [報表管理員 &#40;SSRS 原生模式&#41;].。/report-manager-ssrs-native-mode.md) 。</span><span class="sxs-lookup"><span data-stu-id="a8265-145">Start [Report Manager  &#40;SSRS Native Mode&#41;]../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="a8265-146">在報表管理員中，巡覽至 [內容]  頁面，然後找出您要刪除的項目。</span><span class="sxs-lookup"><span data-stu-id="a8265-146">In Report Manager, navigate to the **Contents** page, and locate the item that you want to delete.</span></span>  
  
3.  <span data-ttu-id="a8265-147">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="a8265-147">Hover over the item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="a8265-148">在下拉式功能表中，按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="a8265-148">In the drop-down menu, click **Delete**.</span></span>  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a8265-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8265-149">See Also</span></span>  
 <span data-ttu-id="a8265-150">[內容頁 &#40;報表管理員&#41;].。/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="a8265-150">[Contents Page &#40;Report Manager&#41;]../contents-page-report-manager.md)</span></span>   
 [<span data-ttu-id="a8265-151">尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;</span><span class="sxs-lookup"><span data-stu-id="a8265-151">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
