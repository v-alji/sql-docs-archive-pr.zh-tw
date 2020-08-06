---
title: 在資料警示管理員中管理 SharePoint 網站上的所有資料警示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b41fdbd18a0b1b4a7a69a3ca202de1c555c070de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704954"
---
# <a name="manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager"></a><span data-ttu-id="e1d25-102">在資料警示管理員中管理 SharePoint 網站上的所有資料警示</span><span class="sxs-lookup"><span data-stu-id="e1d25-102">Manage All Data Alerts on a SharePoint Site in Data Alert Manager</span></span>
  <span data-ttu-id="e1d25-103">SharePoint 警示系統管理員可以檢視任何網站使用者建立之資料警示的清單，以及警示的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e1d25-103">SharePoint alerting administrators can view a list of the data alerts that were created by any site user and information about the alerts.</span></span> <span data-ttu-id="e1d25-104">警示系統管理員還可以刪除警示。</span><span class="sxs-lookup"><span data-stu-id="e1d25-104">Alerting administrators can also delete alerts.</span></span> <span data-ttu-id="e1d25-105">下圖說明 [資料警示管理員] 中可供警示系統管理員使用的功能。</span><span class="sxs-lookup"><span data-stu-id="e1d25-105">The following picture shows the features available to alerting administrators in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="e1d25-106">![SharePoint 網站管理員的警示管理員](media/rs-alertmanagersite.gif "SharePoint 網站管理員的警示管理員")</span><span class="sxs-lookup"><span data-stu-id="e1d25-106">![Alert Manager for SharePoin tsite administrators](media/rs-alertmanagersite.gif "Alert Manager for SharePoin tsite administrators")</span></span>  
  
### <a name="to-view-a-list-of-alerts-created-by-a-site-user"></a><span data-ttu-id="e1d25-107">若要檢視網站使用者建立之警示的清單</span><span class="sxs-lookup"><span data-stu-id="e1d25-107">To view a list of alerts created by a site user</span></span>  
  
1.  <span data-ttu-id="e1d25-108">移至儲存資料警示定義的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="e1d25-108">Go to the SharePoint site where data alerts definitions are saved.</span></span>  
  
2.  <span data-ttu-id="e1d25-109">在首頁上，按一下 [網站動作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1d25-109">On the Home page, click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="e1d25-110">捲動到清單底部，然後按一下 [網站設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1d25-110">Scroll to the bottom of the list and click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="e1d25-111">在 [Reporting Services]\*\*\*\* 底下，按一下 [管理資料警示]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1d25-111">Under **Reporting Services**, click **Manage Data Alerts**.</span></span>  
  
5.  <span data-ttu-id="e1d25-112">按一下 [檢視使用者的警示]\*\*\*\* 清單旁邊的向下箭號，然後選取您要檢視其警示的使用者。</span><span class="sxs-lookup"><span data-stu-id="e1d25-112">Click the down arrow by the **View alerts for user** list and select the user whose alerts you want to view.</span></span>  
  
6.  <span data-ttu-id="e1d25-113">按一下 [檢視報表的警示]\*\*\*\* 清單旁邊的向下箭號，然後選取要檢視的特定警示，或是按一下 [全部顯示]\*\*\*\*，列出所選取使用者建立的所有警示。</span><span class="sxs-lookup"><span data-stu-id="e1d25-113">Click the down arrow next to the **View alerts for report** list and select a specific alert to view, or click **Show All** to list all alerts created by the selected user.</span></span>  
  
     <span data-ttu-id="e1d25-114">資料表會列出名稱、報表名稱、資料警示建立者的名稱、傳送資料警示的次數、上一次修改資料警示定義的時間，以及資料警示的狀態。</span><span class="sxs-lookup"><span data-stu-id="e1d25-114">A table lists the name, report name, name of the person who created the data alert, the number times the data alert was sent, the last time the data alert definition was modified, and the status of the data alert.</span></span> <span data-ttu-id="e1d25-115">如果資料警示無法產生或是傳送，狀態資料行就會包含有關錯誤的資訊並協助您疑難排解問題。</span><span class="sxs-lookup"><span data-stu-id="e1d25-115">If the data alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="e1d25-116">若要刪除警示定義</span><span class="sxs-lookup"><span data-stu-id="e1d25-116">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="e1d25-117">以滑鼠右鍵按一下您想要刪除的資料警示，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1d25-117">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e1d25-118">您刪除警示之後，就不會再傳送任何警示訊息。</span><span class="sxs-lookup"><span data-stu-id="e1d25-118">After you delete the alert, no further alert messages are sent.</span></span> <span data-ttu-id="e1d25-119">不過，如果您查詢警示資料庫，可能會發現警示定義仍然存在。</span><span class="sxs-lookup"><span data-stu-id="e1d25-119">However, if you query the alerting database you might find that the alert definition still exists.</span></span> <span data-ttu-id="e1d25-120">警示服務會依照排程執行清除，而警示定義會在下一次清除時永久刪除。</span><span class="sxs-lookup"><span data-stu-id="e1d25-120">The alerting service performs clean up on a schedule and the alert definition is deleted permanently in the next cleanup.</span></span> <span data-ttu-id="e1d25-121">預設的清除間隔是 20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="e1d25-121">The default cleanup interval is 20 minutes.</span></span> <span data-ttu-id="e1d25-122">此清除間隔和其他清除間隔都可以加以設定。</span><span class="sxs-lookup"><span data-stu-id="e1d25-122">This and other cleanup intervals are configurable.</span></span> <span data-ttu-id="e1d25-123">如需詳細資訊，請參閱 [Reporting Services 資料警示](../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d25-123">For more information, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d25-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d25-124">See Also</span></span>  
 <span data-ttu-id="e1d25-125">[警示系統管理員的資料警示管理員](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="e1d25-125">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="e1d25-126">Reporting Services 資料警示</span><span class="sxs-lookup"><span data-stu-id="e1d25-126">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
