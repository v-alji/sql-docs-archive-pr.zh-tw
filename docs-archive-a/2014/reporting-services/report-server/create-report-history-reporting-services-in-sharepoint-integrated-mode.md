---
title: 建立報表記錄 (SharePoint 整合模式的 Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report history [Reporting Services], SharePoint
ms.assetid: e57ec746-05ae-4ff6-8e39-6cde87310daa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 996202580bbacc24080460c2c43218db27294d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597582"
---
# <a name="create-report-history-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="11584-102">建立報表記錄 (SharePoint 整合模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="11584-102">Create Report History (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="11584-103">報表記錄是您在經過一段時間後建立之報表快照集的集合。</span><span class="sxs-lookup"><span data-stu-id="11584-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="11584-104">每個快照集都是報表的副本，因為它在報表建立時就存在了。</span><span class="sxs-lookup"><span data-stu-id="11584-104">Each snapshot is a copy of the report as it existed when it was created.</span></span> <span data-ttu-id="11584-105">它包含了快照集建立時報表最新的配置和資料。</span><span class="sxs-lookup"><span data-stu-id="11584-105">It includes the layout and data that was current for the report when the snapshot was created.</span></span> <span data-ttu-id="11584-106">轉譯資訊不會與快照集一起儲存。</span><span class="sxs-lookup"><span data-stu-id="11584-106">Rendering information is not stored with the snapshot.</span></span> <span data-ttu-id="11584-107">當您在報表記錄中開啟快照集時，它就會以 HTML 在報表檢視器 Web 組件中開啟。</span><span class="sxs-lookup"><span data-stu-id="11584-107">When you open a snapshot in report history, it opens in HTML in the Report Viewer Web Part.</span></span> <span data-ttu-id="11584-108">轉譯完成之後，您可以將它匯出成其他的應用程式格式。</span><span class="sxs-lookup"><span data-stu-id="11584-108">After it is rendered, you can export it to other application formats.</span></span>  
  
 <span data-ttu-id="11584-109">若要建立報表記錄，報表必須能夠自動執行 (亦即，報表伺服器必須能夠在使用者不介入的情況下執行)。</span><span class="sxs-lookup"><span data-stu-id="11584-109">To create report history, the report must be able to run unattended (that is, the report server must be able to run the report without user interaction).</span></span> <span data-ttu-id="11584-110">您必須在包含報表的文件庫上擁有「編輯項目」權限。</span><span class="sxs-lookup"><span data-stu-id="11584-110">You must have Edit Items permission on the library that contains the report.</span></span> <span data-ttu-id="11584-111">若要檢視或刪除報表記錄，則必須擁有「檢視版本」或「刪除版本」的權限。</span><span class="sxs-lookup"><span data-stu-id="11584-111">To view or delete report history, you must have View Versions or Delete Versions permissions.</span></span>  
  
### <a name="to-create-a-snapshot-or-report-history-on-demand"></a><span data-ttu-id="11584-112">若要視需要建立快照集或報表記錄</span><span class="sxs-lookup"><span data-stu-id="11584-112">To create a snapshot or report history on demand</span></span>  
  
1.  <span data-ttu-id="11584-113">指向報表。</span><span class="sxs-lookup"><span data-stu-id="11584-113">Point to the report.</span></span>  
  
2.  <span data-ttu-id="11584-114">按一下以顯示向下箭頭，然後選取 [檢視報表記錄]  。</span><span class="sxs-lookup"><span data-stu-id="11584-114">Click to display the down arrow, and then select **View Report History**.</span></span>  
  
3.  <span data-ttu-id="11584-115">按一下 **[新增快照集]** 。</span><span class="sxs-lookup"><span data-stu-id="11584-115">Click **New Snapshot**.</span></span> <span data-ttu-id="11584-116">如果沒有顯示此按鈕，就是因為您沒有在報表記錄中建立快照集的權限。</span><span class="sxs-lookup"><span data-stu-id="11584-116">If the button is not visible, it is because you do not have permission to create snapshots in report history.</span></span>  
  
4.  <span data-ttu-id="11584-117">若要檢視您剛建立的快照集，請從清單中選取它。</span><span class="sxs-lookup"><span data-stu-id="11584-117">To view the snapshot you just created, select it from the list.</span></span> <span data-ttu-id="11584-118">每個快照集都可由快照集建立時顯示的時間戳記加以識別。</span><span class="sxs-lookup"><span data-stu-id="11584-118">Each snapshot is identified by a timestamp that shows when the snapshot was created.</span></span> <span data-ttu-id="11584-119">您不能重新命名、移動或修改快照集。</span><span class="sxs-lookup"><span data-stu-id="11584-119">You cannot rename the snapshot, move it to another location, or modify it.</span></span>  
  
### <a name="to-schedule-report-history"></a><span data-ttu-id="11584-120">排程報表記錄</span><span class="sxs-lookup"><span data-stu-id="11584-120">To schedule report history</span></span>  
  
1.  <span data-ttu-id="11584-121">指向報表。</span><span class="sxs-lookup"><span data-stu-id="11584-121">Point to the report.</span></span>  
  
2.  <span data-ttu-id="11584-122">按一下以顯示向下箭頭，然後選取 [管理處理選項]  。</span><span class="sxs-lookup"><span data-stu-id="11584-122">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="11584-123">在 [記錄快照集選項]  中，按一下 [在排程上建立報表記錄快照集]  。</span><span class="sxs-lookup"><span data-stu-id="11584-123">In **History Snapshot Options**, click **Create report history snapshots on a schedule**.</span></span>  
  
4.  <span data-ttu-id="11584-124">如果您設有包含想要使用之排程資訊的共用排程，請按一下 [在共用排程上]  ，然後選取想要使用的排程。</span><span class="sxs-lookup"><span data-stu-id="11584-124">If you have a shared schedule that contains the schedule information you want to use, click **On a shared schedule** and select the schedule you want to use.</span></span> <span data-ttu-id="11584-125">否則，請按一下 [在自訂排程上]  ，然後按一下 [設定]  指定依據重複執行排程建立報表記錄的選項。</span><span class="sxs-lookup"><span data-stu-id="11584-125">Otherwise, click **On a custom schedule**, and then click **Configure** to specify options to create report history on a recurring schedule.</span></span>  
  
### <a name="to-create-report-history-when-data-is-refreshed-in-a-report"></a><span data-ttu-id="11584-126">在報表中的資料重新整理時建立報表記錄</span><span class="sxs-lookup"><span data-stu-id="11584-126">To create report history when data is refreshed in a report</span></span>  
  
1.  <span data-ttu-id="11584-127">指向報表。</span><span class="sxs-lookup"><span data-stu-id="11584-127">Point to the report.</span></span>  
  
2.  <span data-ttu-id="11584-128">按一下以顯示向下箭頭，然後選取 [管理處理選項]  。</span><span class="sxs-lookup"><span data-stu-id="11584-128">Click to display the down arrow, and then select **Manage Processing Options**.</span></span>  
  
3.  <span data-ttu-id="11584-129">在 [記錄快照集選項]  中，按一下 [在報表記錄中儲存所有報表資料快照集]  。</span><span class="sxs-lookup"><span data-stu-id="11584-129">In **History Snapshot Options**, click **Store all report data snapshots in report history**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11584-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11584-130">See Also</span></span>  
 [<span data-ttu-id="11584-131">設定處理選項 &#40;SharePoint 整合模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="11584-131">Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
  
