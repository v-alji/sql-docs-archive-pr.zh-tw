---
title: 警示屬性-新增警示 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471b0062ecc805e83020495e422f8914baec5f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705909"
---
# <a name="alert-properties-new-alert-general-page"></a><span data-ttu-id="42fa5-102">警示屬性-新增警示 (一般頁面) </span><span class="sxs-lookup"><span data-stu-id="42fa5-102">Alert Properties-New Alert (General Page)</span></span>
  <span data-ttu-id="42fa5-103">使用此頁面來查看及修改 Agent 警示的一般屬性 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="42fa5-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="42fa5-104">選項。</span><span class="sxs-lookup"><span data-stu-id="42fa5-104">Options</span></span>  
 <span data-ttu-id="42fa5-105">**名稱**</span><span class="sxs-lookup"><span data-stu-id="42fa5-105">**Name**</span></span>  
 <span data-ttu-id="42fa5-106">變更警示的名稱。</span><span class="sxs-lookup"><span data-stu-id="42fa5-106">Change the name of the alert.</span></span>  
  
 <span data-ttu-id="42fa5-107">**啟用**</span><span class="sxs-lookup"><span data-stu-id="42fa5-107">**Enable**</span></span>  
 <span data-ttu-id="42fa5-108">啟用警示。</span><span class="sxs-lookup"><span data-stu-id="42fa5-108">Enable the alert.</span></span> <span data-ttu-id="42fa5-109">若警示尚未啟用，警示中所指定的動作就不會發生。</span><span class="sxs-lookup"><span data-stu-id="42fa5-109">When the alert is not enabled, the actions specified in the alert do not occur.</span></span>  
  
 <span data-ttu-id="42fa5-110">**型別**</span><span class="sxs-lookup"><span data-stu-id="42fa5-110">**Type**</span></span>  
 <span data-ttu-id="42fa5-111">選取警示的類型：</span><span class="sxs-lookup"><span data-stu-id="42fa5-111">Select the type of alert:</span></span>  
  
-   <span data-ttu-id="42fa5-112">**SQL Server 事件警示** 會回應 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 事件記錄檔中的訊息。</span><span class="sxs-lookup"><span data-stu-id="42fa5-112">**SQL Server event alert** responds to messages in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows event log.</span></span>  
  
-   <span data-ttu-id="42fa5-113">**SQL Server 效能條件警示** 會回應效能計數器中的特定條件。</span><span class="sxs-lookup"><span data-stu-id="42fa5-113">**SQL Server performance condition alert** responds to a specific condition in a performance counter.</span></span>  
  
-   <span data-ttu-id="42fa5-114">**WMI 事件警示** 會回應 Windows Management Instrumentation (WMI) 事件。</span><span class="sxs-lookup"><span data-stu-id="42fa5-114">**WMI event alert** responds to a Windows Management Instrumentation (WMI) event.</span></span>  
  
## <a name="sql-server-event-alert-options"></a><span data-ttu-id="42fa5-115">SQL Server 事件警示選項</span><span class="sxs-lookup"><span data-stu-id="42fa5-115">SQL Server Event Alert Options</span></span>  
 <span data-ttu-id="42fa5-116">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="42fa5-116">**Database name**</span></span>  
 <span data-ttu-id="42fa5-117">不論事件發生所在的資料庫為何，針對該事件指定一個資料庫或 **所有資料庫** ，來回應訊息。</span><span class="sxs-lookup"><span data-stu-id="42fa5-117">Specify a database for the event, or **all databases** to respond to a message regardless of the database where the event occurs.</span></span>  
  
 <span data-ttu-id="42fa5-118">**錯誤號碼**</span><span class="sxs-lookup"><span data-stu-id="42fa5-118">**Error number**</span></span>  
 <span data-ttu-id="42fa5-119">指定此事件會回應錯誤，並指定錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="42fa5-119">Specify that this event responds to an error, and specify the error number.</span></span>  
  
 <span data-ttu-id="42fa5-120">**嚴重性**</span><span class="sxs-lookup"><span data-stu-id="42fa5-120">**Severity**</span></span>  
 <span data-ttu-id="42fa5-121">指定此事件會回應具特定嚴重性層級的任何訊息，並指定嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="42fa5-121">Specify that this event responds to any message with a specific severity level, and specify the severity level.</span></span>  
  
 <span data-ttu-id="42fa5-122">**訊息包含下列內容時引發警示**</span><span class="sxs-lookup"><span data-stu-id="42fa5-122">**Raise alert when message contains**</span></span>  
 <span data-ttu-id="42fa5-123">依特定字串來篩選事件。</span><span class="sxs-lookup"><span data-stu-id="42fa5-123">Filter events by a specific string.</span></span> <span data-ttu-id="42fa5-124">若選取此選項，警示就只會回應包含特定字串的事件。</span><span class="sxs-lookup"><span data-stu-id="42fa5-124">When this option is selected, the alert only responds to events that contain a specific string.</span></span>  
  
 <span data-ttu-id="42fa5-125">**郵件內文**</span><span class="sxs-lookup"><span data-stu-id="42fa5-125">**Message text**</span></span>  
 <span data-ttu-id="42fa5-126">指定要用來篩選事件的字串。</span><span class="sxs-lookup"><span data-stu-id="42fa5-126">Specify the string to use to filter events.</span></span>  
  
## <a name="sql-server-performance-condition-alerts"></a><span data-ttu-id="42fa5-127">SQL Server 效能條件警示</span><span class="sxs-lookup"><span data-stu-id="42fa5-127">SQL Server Performance Condition Alerts</span></span>  
 <span data-ttu-id="42fa5-128">**Object**</span><span class="sxs-lookup"><span data-stu-id="42fa5-128">**Object**</span></span>  
 <span data-ttu-id="42fa5-129">指定要監視的效能物件。</span><span class="sxs-lookup"><span data-stu-id="42fa5-129">Specify the performance object to monitor.</span></span>  
  
 <span data-ttu-id="42fa5-130">**計數器**</span><span class="sxs-lookup"><span data-stu-id="42fa5-130">**Counter**</span></span>  
 <span data-ttu-id="42fa5-131">指定要監視之效能物件內的計數器。</span><span class="sxs-lookup"><span data-stu-id="42fa5-131">Specify the counter within the performance object to monitor.</span></span>  
  
 <span data-ttu-id="42fa5-132">**執行個體**</span><span class="sxs-lookup"><span data-stu-id="42fa5-132">**Instance**</span></span>  
 <span data-ttu-id="42fa5-133">指定要監視之計數器的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42fa5-133">Specify the instance of the counter to monitor.</span></span>  
  
 <span data-ttu-id="42fa5-134">**發出警示的時機為計數器達**</span><span class="sxs-lookup"><span data-stu-id="42fa5-134">**Alert if counter**</span></span>  
 <span data-ttu-id="42fa5-135">指定警示要回應的計數器行為。</span><span class="sxs-lookup"><span data-stu-id="42fa5-135">Specify the behavior of the counter that the alert responds to.</span></span> <span data-ttu-id="42fa5-136">例如，當 [Free space in tempdb (KB)]\*\*\*\* 計數器的值低於某個值時，您可能會希望警示針對如此的條件做出回應，或者當 [SQL Compilations/sec]\*\*\*\* 高於某個值時，您可能會希望警示針對如此的條件做出回應。</span><span class="sxs-lookup"><span data-stu-id="42fa5-136">For example, you may want the alert to respond to a condition where the value of the **Free space in tempdb (KB)** counter falls below a certain value, or you may want the alert to respond to a condition where the **SQL Compilations/sec** rises above a certain value.</span></span>  
  
 <span data-ttu-id="42fa5-137">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="42fa5-137">**Value**</span></span>  
 <span data-ttu-id="42fa5-138">指定計數器的值。</span><span class="sxs-lookup"><span data-stu-id="42fa5-138">Specify a value for the counter.</span></span>  
  
## <a name="wmi-event-alert-options"></a><span data-ttu-id="42fa5-139">WMI 事件警示選項</span><span class="sxs-lookup"><span data-stu-id="42fa5-139">WMI Event Alert Options</span></span>  
 <span data-ttu-id="42fa5-140">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="42fa5-140">**Namespace**</span></span>  
 <span data-ttu-id="42fa5-141">指定針對 WMI 查詢語言 (WQL) 陳述式使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="42fa5-141">Specify the namespace to use for the WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="42fa5-142">僅支援執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 之電腦上的命名空間。</span><span class="sxs-lookup"><span data-stu-id="42fa5-142">Only namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
 <span data-ttu-id="42fa5-143">**查詢**</span><span class="sxs-lookup"><span data-stu-id="42fa5-143">**Query**</span></span>  
 <span data-ttu-id="42fa5-144">指定會識別警示所回應之事件的 WQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="42fa5-144">Specify the WQL statement that identifies the event that the alert responds to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42fa5-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42fa5-145">See Also</span></span>  
 <span data-ttu-id="42fa5-146">[警示](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="42fa5-146">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="42fa5-147">[搭配伺服器事件的 WMI 提供者使用 WQL](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span><span class="sxs-lookup"><span data-stu-id="42fa5-147">[Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span></span>  
 <span data-ttu-id="42fa5-148">[使用錯誤號碼建立警示](create-an-alert-using-an-error-number.md) </span><span class="sxs-lookup"><span data-stu-id="42fa5-148">[Create an Alert Using an Error Number](create-an-alert-using-an-error-number.md) </span></span>  
 [<span data-ttu-id="42fa5-149">Create an Alert Using Severity Level</span><span class="sxs-lookup"><span data-stu-id="42fa5-149">Create an Alert Using Severity Level</span></span>](create-an-alert-using-severity-level.md)  
  
  
