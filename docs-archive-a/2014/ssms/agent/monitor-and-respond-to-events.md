---
title: 監視及回應事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- notifications [SQL Server], alert
- events [SQL Server], alerts
- alerts [SQL Server]
- notifications [SQL Server]
- events [SQL Server], automatically responding to
- administrator notifications [SQL Server Agent]
- automatic event responses
- SQL Server Agent alerts
- monitoring [SQL Server], events
- responding to events automatically
ms.assetid: f7fbe155-5b68-4777-bc71-a47637471f32
author: stevestein
ms.author: sstein
ms.openlocfilehash: afdf1beffd6099fce84f03a8ba65f7de9abb8f0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699181"
---
# <a name="monitor-and-respond-to-events"></a><span data-ttu-id="92dd6-102">監視及回應事件</span><span class="sxs-lookup"><span data-stu-id="92dd6-102">Monitor and Respond to Events</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92dd6-103">Agent 會監視及自動回應「事件」\*\*(Event)，例如：來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的訊息、特定效能狀況與 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="92dd6-103">Agent can monitor and automatically respond to *events*, such as messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specific performance conditions, and Windows Management Instrumentation (WMI) events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92dd6-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="92dd6-104">In This Section</span></span>  
 [<span data-ttu-id="92dd6-105">警示</span><span class="sxs-lookup"><span data-stu-id="92dd6-105">Alerts</span></span>](alerts.md)  
 <span data-ttu-id="92dd6-106">包含如何命名警示和選取警示所回應之事件或效能狀況的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="92dd6-106">Contains information about naming an alert and selecting the events or performance conditions to which alerts respond.</span></span>  
  
 [<span data-ttu-id="92dd6-107">建立使用者定義的事件</span><span class="sxs-lookup"><span data-stu-id="92dd6-107">Create a User-Defined Event</span></span>](create-a-user-defined-event.md)  
 <span data-ttu-id="92dd6-108">包含有關於如何建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]預先定義之事件以外的事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="92dd6-108">Contains information about how to create events other than those that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="92dd6-109">運算子</span><span class="sxs-lookup"><span data-stu-id="92dd6-109">Operators</span></span>](operators.md)  
 <span data-ttu-id="92dd6-110">包含當作業失敗或成功時，如何建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 可用來傳送通知的管理員別名。</span><span class="sxs-lookup"><span data-stu-id="92dd6-110">Contains information about creating aliases for administrators that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent can use to send notifications when jobs fail or succeed.</span></span>  
  
## <a name="about-monitoring-and-responding-to-events"></a><span data-ttu-id="92dd6-111">關於監視及回應事件</span><span class="sxs-lookup"><span data-stu-id="92dd6-111">About Monitoring and Responding to Events</span></span>  
 <span data-ttu-id="92dd6-112">對於事件的自動回應稱之為「警示」\*\*。</span><span class="sxs-lookup"><span data-stu-id="92dd6-112">Automated responses to events are called *alerts*.</span></span> <span data-ttu-id="92dd6-113">您可以在一或多個事件上定義警示，以指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 回應事件的方式。</span><span class="sxs-lookup"><span data-stu-id="92dd6-113">You can define an alert on one or more events to specify how you want [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to respond to their occurrence.</span></span> <span data-ttu-id="92dd6-114">警示可透過通知管理員或執行作業 (或兩者) 來回應事件。</span><span class="sxs-lookup"><span data-stu-id="92dd6-114">An alert can respond to an event by notifying an administrator or running a job, or both.</span></span> <span data-ttu-id="92dd6-115">警示也可以將事件轉送到在另一部電腦上登入的 Microsoft Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="92dd6-115">An alert can also forward an event to the Microsoft Windows application log on a different computer.</span></span> <span data-ttu-id="92dd6-116">例如，如果發生嚴重性 19 的事件，您可以指定要立即通知操作員。</span><span class="sxs-lookup"><span data-stu-id="92dd6-116">For example, you can specify that an operator be notified immediately if an event of severity 19 occurs.</span></span> <span data-ttu-id="92dd6-117">透過定義警示，資料庫管理員就可以更有效率地監視和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="92dd6-117">By defining alerts, database administrators can more effectively monitor and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92dd6-118">Agent 只會回應已定義警示的事件。</span><span class="sxs-lookup"><span data-stu-id="92dd6-118">Agent only responds to events for which an alert is defined.</span></span> <span data-ttu-id="92dd6-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 用來監視事件的方法會取決於事件的類型。</span><span class="sxs-lookup"><span data-stu-id="92dd6-119">The method that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent uses to monitor events depends on the type of event.</span></span>  
  
 <span data-ttu-id="92dd6-120">對效能計數器定義了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示後， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就會直接監視效能計數器。</span><span class="sxs-lookup"><span data-stu-id="92dd6-120">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert is defined for a performance counter, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent directly monitors the performance counter.</span></span> <span data-ttu-id="92dd6-121">若是 WMI 事件， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會登錄 WMI 事件的事件查詢。</span><span class="sxs-lookup"><span data-stu-id="92dd6-121">For a WMI event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registers an event query for the WMI event.</span></span>  
  
 <span data-ttu-id="92dd6-122">若要回應來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的訊息， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會監視 Windows 應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="92dd6-122">To respond to messages from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent monitors the Windows application log.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92dd6-123">Agent 只會回應出現在這個記錄檔中的訊息。</span><span class="sxs-lookup"><span data-stu-id="92dd6-123">Agent can only respond to messages that appear in this log.</span></span> <span data-ttu-id="92dd6-124">根據預設，SQL Server 會將下列訊息記錄在 Windows 應用程式記錄檔中：</span><span class="sxs-lookup"><span data-stu-id="92dd6-124">By default, SQL Server logs the following messages in the Windows application log:</span></span>  
  
-   <span data-ttu-id="92dd6-125">嚴重性 19 或更高的 sysmessages 錯誤。</span><span class="sxs-lookup"><span data-stu-id="92dd6-125">Severity 19 or higher sysmessages errors.</span></span>  
  
     <span data-ttu-id="92dd6-126">如果您還要記錄嚴重性低於 19 的特定 sysmessages 錯誤，請使用 sp_altermessage 預存程序將這類錯誤指定為「一律記錄」。</span><span class="sxs-lookup"><span data-stu-id="92dd6-126">If you also want to log specific sysmessages errors that have a severity lower than 19, use the sp_altermessage stored procedure to designate such errors as "always logged".</span></span>  
  
-   <span data-ttu-id="92dd6-127">使用 WITH LOG 語法叫用的任何 RAISERROR 陳述式。</span><span class="sxs-lookup"><span data-stu-id="92dd6-127">Any RAISERROR statement invoked by using the WITH LOG syntax.</span></span>  
  
     <span data-ttu-id="92dd6-128">建議您使用 PAISERROR WITH LOG，從 SQL Server 執行個體寫入 Windows 應用程式記錄檔。</span><span class="sxs-lookup"><span data-stu-id="92dd6-128">Using RAISERROR WITH LOG is the recommended way to write to the Windows application log from an instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="92dd6-129">使用 xp_logevent 記錄的任何應用程式事件。</span><span class="sxs-lookup"><span data-stu-id="92dd6-129">Any application event that is logged by using xp_logevent.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="92dd6-130">記錄應用程式事件會消耗記錄檔空間，並且造成 Windows 應用程式記錄檔超出其大小上限。</span><span class="sxs-lookup"><span data-stu-id="92dd6-130">Logging application events consumes log space and can cause the Windows application log to exceed its maximum size.</span></span> <span data-ttu-id="92dd6-131">請確定 Windows 應用程式記錄檔具有足夠的大小，以免遺失 SQL Server 事件資訊。</span><span class="sxs-lookup"><span data-stu-id="92dd6-131">Make sure that the maximum Windows application log size is large enough to avoid loss of SQL Server event information.</span></span>  
  
 <span data-ttu-id="92dd6-132">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄訊息時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務會比較訊息和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理員所定義的警示。</span><span class="sxs-lookup"><span data-stu-id="92dd6-132">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logs a message, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service compares the message against the alerts defined by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="92dd6-133">不管事件的來源為何， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務都會透過執行在事件警示中指定的工作來回應事件。</span><span class="sxs-lookup"><span data-stu-id="92dd6-133">Regardless of the source of the event, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service responds to the event by performing the tasks specified in the alert for the event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92dd6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92dd6-134">See Also</span></span>  
 [<span data-ttu-id="92dd6-135">sp_altermessage &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="92dd6-135">sp_altermessage &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
  
