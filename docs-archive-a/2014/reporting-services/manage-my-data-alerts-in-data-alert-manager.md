---
title: 在資料警示管理員中管理我的資料警示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 371c62c2f97334e20280a659c8039ab20852ccfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704957"
---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a><span data-ttu-id="98d3d-102">在資料警示管理員中管理我的資料警示</span><span class="sxs-lookup"><span data-stu-id="98d3d-102">Manage My Data Alerts in Data Alert Manager</span></span>
  <span data-ttu-id="98d3d-103">SharePoint 使用者可以檢視自己所建立資料警示的清單，以及警示的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="98d3d-103">SharePoint users can view a list of the data alerts that they created and information about the alerts.</span></span> <span data-ttu-id="98d3d-104">使用者還可以在 [資料警示設計工具] 中刪除自己的警示、開啟警示定義進行編輯，以及執行自己的警示。</span><span class="sxs-lookup"><span data-stu-id="98d3d-104">Users can also delete their alerts, open alert definitions for edit in Data Alert Designer, and run their alerts.</span></span> <span data-ttu-id="98d3d-105">下圖說明 [資料警示管理員] 中可供使用者使用的功能。</span><span class="sxs-lookup"><span data-stu-id="98d3d-105">The following picture shows the features available to users in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="98d3d-106">![SharePoint 使用者的警示管理員功能](media/rs-alertmanageriw.gif "SharePoint 使用者的警示管理員功能")</span><span class="sxs-lookup"><span data-stu-id="98d3d-106">![Alert Manager features for SharePoint users](media/rs-alertmanageriw.gif "Alert Manager features for SharePoint users")</span></span>  
  
### <a name="to-view-a-list-of-your-alerts"></a><span data-ttu-id="98d3d-107">若要檢視警示清單</span><span class="sxs-lookup"><span data-stu-id="98d3d-107">To view a list of your alerts</span></span>  
  
1.  <span data-ttu-id="98d3d-108">移至您儲存已建立資料警示之報表的 SharePoint 文件庫。</span><span class="sxs-lookup"><span data-stu-id="98d3d-108">Go to the SharePoint library where you saved the reports on which you created data alerts.</span></span>  
  
2.  <span data-ttu-id="98d3d-109">按一下報表上展開下拉式功能表的圖示，然後按一下 [管理資料警示]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98d3d-109">Click the icon for the expand drop-down menu on a report and click **Manage Data Alerts**.</span></span> <span data-ttu-id="98d3d-110">下圖顯示下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="98d3d-110">The following picture shows the drop-down menu.</span></span>  
  
     <span data-ttu-id="98d3d-111">![從報表操作功能表開啟警示管理員](media/rs-openalertmanager.gif "從報表操作功能表開啟警示管理員")</span><span class="sxs-lookup"><span data-stu-id="98d3d-111">![Open Alert Manager from report context menu](media/rs-openalertmanager.gif "Open Alert Manager from report context menu")</span></span>  
  
     <span data-ttu-id="98d3d-112">[資料警示管理員] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="98d3d-112">Data Alert Manager opens.</span></span> <span data-ttu-id="98d3d-113">根據預設，其中會列出您在文件庫中所選取報表的警示。</span><span class="sxs-lookup"><span data-stu-id="98d3d-113">By default, it lists the alerts for the report that you selected in the library.</span></span>  
  
3.  <span data-ttu-id="98d3d-114">按一下 [檢視報表的警示]\*\*\*\* 清單旁邊的向下箭號，然後選取要檢視其警示的報表，或是按一下 [全部顯示]\*\*\*\* 列出所有警示。</span><span class="sxs-lookup"><span data-stu-id="98d3d-114">Click the down arrow next to the **View alerts for report** list and select a report to view its alerts, or click **Show All** to list all alerts.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98d3d-115">如果您選取的報表沒有任何警示，您不必返回 SharePoint 文件庫也能尋找並選取擁有警示的報表。</span><span class="sxs-lookup"><span data-stu-id="98d3d-115">If the report that you selected does not have any alerts, you do not have to return to the SharePoint library to locate and select a report that hasalerts.</span></span> <span data-ttu-id="98d3d-116">只要按一下 [全部顯示]\*\*\*\* 就可以查看所有警示的清單。</span><span class="sxs-lookup"><span data-stu-id="98d3d-116">Instead, click **Show All** to see a list of all your alerts.</span></span>  
  
     <span data-ttu-id="98d3d-117">資料表會列出警示名稱、報表名稱、您 (也就是警示建立者) 的名稱、傳送的警示數目、上一次修改警示定義的時間，以及警示的狀態。</span><span class="sxs-lookup"><span data-stu-id="98d3d-117">A table lists the alert name, report name, your name as the creator of the alert, the number the alert was sent, the last time the alert definition was modified, and the status of the alert.</span></span> <span data-ttu-id="98d3d-118">如果警示無法產生或是傳送，狀態資料行就會包含有關錯誤的資訊並協助您疑難排解問題。</span><span class="sxs-lookup"><span data-stu-id="98d3d-118">If the alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-edit-an-alert-definition"></a><span data-ttu-id="98d3d-119">若要編輯警示定義</span><span class="sxs-lookup"><span data-stu-id="98d3d-119">To edit an alert definition</span></span>  
  
-   <span data-ttu-id="98d3d-120">以滑鼠右鍵按一下要編輯其警示定義的資料警示，然後按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98d3d-120">Right-click the data alert for which you want to edit the alert definition and click **Edit**.</span></span>  
  
     <span data-ttu-id="98d3d-121">警示定義會在 [資料警示設計工具] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="98d3d-121">The alert definition opens in Data Alert Designer.</span></span> <span data-ttu-id="98d3d-122">如需詳細資訊，請參閱 [在警示設計工具中編輯資料警示](edit-a-data-alert-in-alert-designer.md) 和 [資料警示設計工具](../../2014/reporting-services/data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="98d3d-122">For more information, see [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md) and [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98d3d-123">只有建立資料警示定義的使用者才能進行編輯。</span><span class="sxs-lookup"><span data-stu-id="98d3d-123">Only the user that created the data alert definition can edit it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="98d3d-124">如果報表已變更，而且從報表產生的資料摘要也已變更，則警示定義可能已無效。</span><span class="sxs-lookup"><span data-stu-id="98d3d-124">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="98d3d-125">當警示參考其規則的資料行已從報表中刪除、變更資料類型，或是包含在不同的資料摘要中或報表已刪除或移動時，就會發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="98d3d-125">This occurs when a column that the alert references in its rules is deleted from the report, changes data type, or is included in a different data feed or the report is deleted or moved.</span></span> <span data-ttu-id="98d3d-126">您可以開啟無效的警示定義，但是無法重新儲存它，除非依據建立定義的目前版本報表資料摘要成為有效的警示定義。</span><span class="sxs-lookup"><span data-stu-id="98d3d-126">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="98d3d-127">若要深入了解如何從多個報表產生資料摘要，請參閱[從多個報表產生資料摘要 &#40;報表產生器及 SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="98d3d-127">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="98d3d-128">若要刪除警示定義</span><span class="sxs-lookup"><span data-stu-id="98d3d-128">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="98d3d-129">以滑鼠右鍵按一下您想要刪除的資料警示，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98d3d-129">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
     <span data-ttu-id="98d3d-130">刪除警示時，就不會再傳送任何警示訊息。</span><span class="sxs-lookup"><span data-stu-id="98d3d-130">When you delete the alert, no further alert messages are sent.</span></span>  
  
### <a name="to-run-an-alert"></a><span data-ttu-id="98d3d-131">若要執行警示</span><span class="sxs-lookup"><span data-stu-id="98d3d-131">To run an alert</span></span>  
  
-   <span data-ttu-id="98d3d-132">以滑鼠右鍵按一下您要執行的資料警示，然後按一下 [執行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="98d3d-132">Right-click the data alert that you want to run and click **Run**.</span></span>  
  
     <span data-ttu-id="98d3d-133">無論您在 [資料警示設計工具] 中指定的排程選項為何，警示執行個體都會建立，而且資料警示訊息也會立即傳送。</span><span class="sxs-lookup"><span data-stu-id="98d3d-133">The alert instance is created and the data alert message is immediately sent, regardless of the schedule options you specified in Data Alert Designer.</span></span> <span data-ttu-id="98d3d-134">例如，設定為每週且僅在結果變更時傳送的警示便會傳送。</span><span class="sxs-lookup"><span data-stu-id="98d3d-134">For example, an alert configured to be sent weekly and then only if the results change is sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d3d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98d3d-135">See Also</span></span>  
 <span data-ttu-id="98d3d-136">[警示系統管理員的資料警示管理員](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="98d3d-136">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="98d3d-137">Reporting Services 資料警示</span><span class="sxs-lookup"><span data-stu-id="98d3d-137">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
