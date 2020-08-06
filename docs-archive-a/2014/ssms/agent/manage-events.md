---
title: 管理事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- event-triggered jobs [SQL Server]
- forwarding events [SQL Server]
- alerts [SQL Server], forwarded events
- alerts [SQL Server], management servers
- SQL Server Agent alerts, management servers
ms.assetid: 8f4ee7f5-80df-49fd-b2b8-d020e04b6e1b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7ca6d56440b06d285cbb90f8d92325d59a452c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686755"
---
# <a name="manage-events"></a><span data-ttu-id="1f9d8-102">管理事件</span><span class="sxs-lookup"><span data-stu-id="1f9d8-102">Manage Events</span></span>
  <span data-ttu-id="1f9d8-103">您可以將達到或超過特定錯誤嚴重性層級的所有事件訊息轉送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-103">You can forward to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all event messages that meet or exceed a specific error severity level.</span></span> <span data-ttu-id="1f9d8-104">這稱為「事件轉送」\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-104">This is called *event forwarding*.</span></span> <span data-ttu-id="1f9d8-105">轉送伺服器是一個專用的伺服器，它也可以當做主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-105">The forwarding server is a dedicated server that can also be a master server.</span></span> <span data-ttu-id="1f9d8-106">您可以利用事件轉送功能將伺服器群組的警示管理集中化，藉以減輕使用頻繁之伺服器的工作負載。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-106">You can use event forwarding to centralize alert management for a group of servers, thereby reducing the workload on heavily used servers.</span></span>  
  
 <span data-ttu-id="1f9d8-107">當某伺服器接收到其他伺服器群組的事件時，接收事件的伺服器稱為「警示管理伺服器」\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-107">When one server receives events for a group of other servers, the server that receives events is called an *alerts management server*.</span></span> <span data-ttu-id="1f9d8-108">在多伺服器的環境中，您可以將主要伺服器指定為警示管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-108">In a multiserver environment, you designate the master server as the alerts management server.</span></span>  
  
## <a name="advantages-of-using-an-alerts-management-server"></a><span data-ttu-id="1f9d8-109">使用警示管理伺服器的優點</span><span class="sxs-lookup"><span data-stu-id="1f9d8-109">Advantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="1f9d8-110">設定警示管理伺服器的優點包括：</span><span class="sxs-lookup"><span data-stu-id="1f9d8-110">The advantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="1f9d8-111">**集中化**。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-111">**Centralization**.</span></span> <span data-ttu-id="1f9d8-112">可從單一伺服器集中控制和合併檢視多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的事件。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-112">Centralized control and a consolidated view of the events of several instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are possible from a single server.</span></span>  
  
-   <span data-ttu-id="1f9d8-113">**延展性**。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-113">**Scalability**.</span></span> <span data-ttu-id="1f9d8-114">能以一個邏輯伺服器的方式管理很多實體的伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-114">Many physical servers can be administered as one logical server.</span></span> <span data-ttu-id="1f9d8-115">您可以依照需要對這個實體的伺服器群組新增或移除伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-115">You can add or remove servers to this physical server group as needed.</span></span>  
  
-   <span data-ttu-id="1f9d8-116">**效率**。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-116">**Efficiency**.</span></span> <span data-ttu-id="1f9d8-117">組態時間減少，因為您只需要定義一次警示和運算子。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-117">Configuration time is reduced, because you need to define alerts and operators only once.</span></span>  
  
## <a name="disadvantages-of-using-an-alerts-management-server"></a><span data-ttu-id="1f9d8-118">使用警示管理伺服器的缺點</span><span class="sxs-lookup"><span data-stu-id="1f9d8-118">Disadvantages of Using an Alerts Management Server</span></span>  
 <span data-ttu-id="1f9d8-119">設定警示管理伺服器的缺點包括：</span><span class="sxs-lookup"><span data-stu-id="1f9d8-119">The disadvantages of setting up an alerts management server include:</span></span>  
  
-   <span data-ttu-id="1f9d8-120">**網路流量增加**。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-120">**Increased traffic**.</span></span> <span data-ttu-id="1f9d8-121">將事件轉送至警示管理伺服器會增加網路傳輸量。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-121">Forwarding events to an alerts management server can increase network traffic.</span></span> <span data-ttu-id="1f9d8-122">將事件轉送限制在高於指定嚴重性層級的事件，可減緩流量增加的情況。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-122">This increase can be moderated by restricting event forwarding to events that are above a designated severity level.</span></span>  
  
-   <span data-ttu-id="1f9d8-123">**單一失敗點**。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-123">**Single point of failure**.</span></span> <span data-ttu-id="1f9d8-124">如果警示管理伺服器離線，則不會對受管理伺服器群組上的任何事件發出警示。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-124">If the alerts management server goes offline, no alerts are issued for any event on the managed group of servers.</span></span>  
  
-   <span data-ttu-id="1f9d8-125">**伺服器負載**。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-125">**Server load**.</span></span> <span data-ttu-id="1f9d8-126">處理轉送事件的警示會造成警示管理伺服器的處理負載增加。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-126">Handling alerts for the forwarded events causes an increased processing load on the alerts management server.</span></span>  
  
## <a name="guidelines-for-using-an-alerts-management-server"></a><span data-ttu-id="1f9d8-127">使用警示管理伺服器的指導方針</span><span class="sxs-lookup"><span data-stu-id="1f9d8-127">Guidelines for Using an Alerts Management Server</span></span>  
 <span data-ttu-id="1f9d8-128">在設定警示管理伺服器時，請遵守下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="1f9d8-128">When configuring an alerts management server, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="1f9d8-129">若要接收轉送的事件，則警示管理伺服器必須是預設的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-129">In order to receive forwarded events, the alerts management server must be a default instance of SQL Server.</span></span>  
  
-   <span data-ttu-id="1f9d8-130">避免在警示管理伺服器上執行重要或使用頻繁的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-130">Avoid running critical or heavily used applications on the alerts management server.</span></span>  
  
-   <span data-ttu-id="1f9d8-131">小心規劃網路傳輸量，包括設定許多伺服器來共用相同的警示管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-131">Carefully plan for the network traffic involved in configuring many servers to share the same alerts management server.</span></span> <span data-ttu-id="1f9d8-132">如果發生阻塞，請減少使用某一特別警示管理伺服器的伺服器數量。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-132">If congestion results, reduce the number of servers that use a particular alerts management server.</span></span>  
  
     <span data-ttu-id="1f9d8-133">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 內註冊的伺服器構成一份清單，其中就是可供該伺服器用來選擇作為警示轉送伺服器的伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-133">The servers that are registered within [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] constitute the list of servers available to be chosen by that server as the alerts-forwarding server.</span></span>  
  
-   <span data-ttu-id="1f9d8-134">在需要伺服器特定回應的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 本機執行個體上定義警示，而不要將警示轉送到警示管理伺服器。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-134">Define alerts on the local instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that require a server-specific response, instead of forwarding the alerts to the alerts management server.</span></span>  
  
     <span data-ttu-id="1f9d8-135">警示管理伺服器會將轉送來的所有伺服器視為一個邏輯整體。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-135">The alerts management server views all the servers forwarding to it as a logical whole.</span></span> <span data-ttu-id="1f9d8-136">例如，警示管理伺服器會以相同的方式，回應來自伺服器 A 的 605 事件和來自伺服器 B 的 605 事件。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-136">For example, an alerts management server responds in the same way to a 605 event from server A and a 605 event from server B.</span></span>  
  
-   <span data-ttu-id="1f9d8-137">請在設定警示系統後，定期檢查 Microsoft Windows 應用程式記錄檔中的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 事件。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-137">After configuring your alert system, periodically check the Microsoft Windows application log for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent events.</span></span>  
  
     <span data-ttu-id="1f9d8-138">警示引擎所遇到的失敗狀況，會以來源名稱 "SQL Server Agent" 寫入本機 Windows 應用程式記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-138">Failure conditions encountered by the alerts engine are written to the local Windows application log with a source name of "SQL Server Agent."</span></span> <span data-ttu-id="1f9d8-139">例如，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 無法傳送已定義的電子郵件通知，則會在應用程式記錄檔中記錄一個事件。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-139">For example, if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent cannot send an e-mail notification as it has been defined, an event is logged in the application log.</span></span>  
  
 <span data-ttu-id="1f9d8-140">如果本機定義的警示未啟動，卻發生了會引發警示的事件，則會將事件轉送至警示管理伺服器 (如果它符合警示轉送條件的話)。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-140">If a locally defined alert is inactivated, and an event occurs that would have caused the alert to fire, the event is forwarded to the alerts management server (if it satisfies the alert-forwarding condition).</span></span> <span data-ttu-id="1f9d8-141">轉送時可依據本機站台的使用者需求，來關閉或開啟本機覆寫 (本機定義的警示，也定義於警示管理伺服器上)。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-141">This forwarding allows local overrides (alerts defined locally that are also defined on the alerts management server) to be turned off and on as needed by the user at the local site.</span></span> <span data-ttu-id="1f9d8-142">即使事件也是由本機警示所處理的，您仍舊可以要求一律轉送事件。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-142">You can also request that events always be forwarded, even if they are also handled by local alerts.</span></span>  
  
 <span data-ttu-id="1f9d8-143">下列是在多伺服器環境中管理事件的一般工作：</span><span class="sxs-lookup"><span data-stu-id="1f9d8-143">The following are common tasks for managing events in a multiserver environment:</span></span>  
  
 <span data-ttu-id="1f9d8-144">**若要指定警示管理伺服器**</span><span class="sxs-lookup"><span data-stu-id="1f9d8-144">**To designate an alerts management server**</span></span>  
  
-   [<span data-ttu-id="1f9d8-145">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1f9d8-145">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
 <span data-ttu-id="1f9d8-146">**若要定義對警示的回應**</span><span class="sxs-lookup"><span data-stu-id="1f9d8-146">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="1f9d8-147">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f9d8-147">SQL Server Management Studio</span></span>](define-the-response-to-an-alert-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="1f9d8-148">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1f9d8-148">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
## <a name="running-event-triggered-jobs"></a><span data-ttu-id="1f9d8-149">執行事件觸發作業</span><span class="sxs-lookup"><span data-stu-id="1f9d8-149">Running Event-Triggered Jobs</span></span>  
 <span data-ttu-id="1f9d8-150">您可以定義執行一個作業來回應警示。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-150">You can define a job to be executed in response to an alert.</span></span> <span data-ttu-id="1f9d8-151">例如，您可以執行一個作業來更正或進一步診斷由警示所偵測到的問題。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-151">For example, you can execute a job that corrects or further diagnoses a problem detected by the alert.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f9d8-152">因為作業可能引發事件，請小心不要建立遞迴式警示作業迴圈。</span><span class="sxs-lookup"><span data-stu-id="1f9d8-152">Because a job can raise an event, be careful not to create a recursive alert-job loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9d8-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f9d8-153">See Also</span></span>  
 [<span data-ttu-id="1f9d8-154">sys.sys訊息 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="1f9d8-154">sys.sysmessages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysmessages-transact-sql)  
  
  
