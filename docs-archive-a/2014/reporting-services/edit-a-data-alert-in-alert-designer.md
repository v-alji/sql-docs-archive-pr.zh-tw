---
title: 在警示設計工具中編輯資料警示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9906b33ae50d51733eaec1bf5c201c9f5b5d120e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703902"
---
# <a name="edit-a-data-alert-in-alert-designer"></a><span data-ttu-id="e64cb-102">在警示設計工具中編輯資料警示</span><span class="sxs-lookup"><span data-stu-id="e64cb-102">Edit a Data Alert in Alert Designer</span></span>
  <span data-ttu-id="e64cb-103">從 [資料警示管理員] 開啟您要編輯的資料警示定義。</span><span class="sxs-lookup"><span data-stu-id="e64cb-103">You open the data alert definition that you want to edit from Data Alert Manager.</span></span> <span data-ttu-id="e64cb-104">只有建立警示定義的使用者才能進行編輯。</span><span class="sxs-lookup"><span data-stu-id="e64cb-104">Only the user that created the alert definition can edit it.</span></span> <span data-ttu-id="e64cb-105">如需開啟資料警示管理員的詳細資訊，請參閱 [在資料警示管理員中管理我的資料警示](manage-my-data-alerts-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e64cb-105">For more information about opening Data Alert Manager, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

 <span data-ttu-id="e64cb-106">下圖說明 [資料警示管理員] 中資料警示的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="e64cb-106">The following picture shows you the context menu on a data alert in Data Alert Manager.</span></span>

 <span data-ttu-id="e64cb-107">![按一下 [編輯] 來開啟資料警示設計工具](media/rs-alertmanageriwopendesigner.gif "按一下 [編輯] 來開啟資料警示設計工具")</span><span class="sxs-lookup"><span data-stu-id="e64cb-107">![Open Data Alert Designer by clicking Edit](media/rs-alertmanageriwopendesigner.gif "Open Data Alert Designer by clicking Edit")</span></span>

 <span data-ttu-id="e64cb-108">下列程序包括從 [資料警示管理員] 開啟警示定義，以便在 [資料警示設計工具] 中進行編輯的步驟。</span><span class="sxs-lookup"><span data-stu-id="e64cb-108">The following procedure includes the steps to open the alert definition for editing in Data Alert Designer from Data Alert Manager.</span></span>

### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a><span data-ttu-id="e64cb-109">在資料警示設計工具中編輯資料警示定義</span><span class="sxs-lookup"><span data-stu-id="e64cb-109">To edit a data alert definition in Data Alert Designer</span></span>

1.  <span data-ttu-id="e64cb-110">在 [資料警示管理員] 中，以滑鼠右鍵按一下您要編輯的資料警示定義，然後按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e64cb-110">In Data Alert Manager, right-click the data alert definition that you want to edit and click **Edit**.</span></span>

     <span data-ttu-id="e64cb-111">警示定義會在 [資料警示設計工具] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="e64cb-111">The alert definition opens in Data Alert Designer.</span></span>

2.  <span data-ttu-id="e64cb-112">請更新規則、排程設定和電子郵件設定。</span><span class="sxs-lookup"><span data-stu-id="e64cb-112">Update the rules, schedule settings, and email settings.</span></span> <span data-ttu-id="e64cb-113">如需詳細資訊，請參閱 [資料警示設計工具](../../2014/reporting-services/data-alert-designer.md) 和 [在資料警示設計工具中建立資料警示](create-a-data-alert-in-data-alert-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="e64cb-113">For more information, see [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) and [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e64cb-114">您無法選擇不同的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="e64cb-114">You cannot choose a different data feed.</span></span> <span data-ttu-id="e64cb-115">若要使用不同的資料摘要，您必須建立新的資料警示定義。</span><span class="sxs-lookup"><span data-stu-id="e64cb-115">To use a different data feed, you must create a new data alert definition.</span></span>

3.  <span data-ttu-id="e64cb-116">按一下 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="e64cb-116">Click **Save**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e64cb-117">如果報表已變更，而且從報表產生的資料摘要也已變更，則警示定義可能已無效。</span><span class="sxs-lookup"><span data-stu-id="e64cb-117">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="e64cb-118">當警示定義參考其規則的資料行已從報表中刪除或變更資料類型，或是報表已刪除或移動時，就會發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="e64cb-118">This occurs when a column that the alert definition references in its rules is deleted from the report or changes data type or the report is deleted or moved.</span></span> <span data-ttu-id="e64cb-119">您可以開啟無效的警示定義，但是無法重新儲存它，除非依據建立定義的目前版本報表資料摘要成為有效的警示定義。</span><span class="sxs-lookup"><span data-stu-id="e64cb-119">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="e64cb-120">若要深入了解如何從多個報表產生資料摘要，請參閱[從多個報表產生資料摘要 &#40;報表產生器及 SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e64cb-120">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e64cb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e64cb-121">See Also</span></span>
 <span data-ttu-id="e64cb-122">警示系統管理員[Reporting Services 資料警示](../ssms/agent/alerts.md)[的資料警示管理員](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)</span><span class="sxs-lookup"><span data-stu-id="e64cb-122">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


