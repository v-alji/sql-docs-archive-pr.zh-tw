---
title: Broker 事件類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Broker event category
- Broker event category [SQL Server]
- event classes [SQL Server], Broker event category
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
author: stevestein
ms.author: sstein
ms.openlocfilehash: 23f839416e3404bfdf0a7e61d1b1e8dbbb90ec95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592068"
---
# <a name="broker-event-category"></a><span data-ttu-id="2f14a-102">Broker 事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="2f14a-102">Broker Event Category</span></span>
  <span data-ttu-id="2f14a-103">**Broker** 事件類別目錄包含一般的 Service Broker 事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-103">The **Broker** event category contains general Service Broker events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f14a-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="2f14a-104">In This Section</span></span>  
  
|<span data-ttu-id="2f14a-105">主題</span><span class="sxs-lookup"><span data-stu-id="2f14a-105">Topic</span></span>|<span data-ttu-id="2f14a-106">描述</span><span class="sxs-lookup"><span data-stu-id="2f14a-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2f14a-107">Broker:Activation 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-107">Broker:Activation Event Class</span></span>](broker-activation-event-class.md)|<span data-ttu-id="2f14a-108">當佇列監視器啟動一個啟用預存程序時產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-108">An event generated when a queue monitor starts an activation stored procedure.</span></span>|  
|[<span data-ttu-id="2f14a-109">Broker:Connection 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-109">Broker:Connection Event Class</span></span>](broker-connection-event-class.md)|<span data-ttu-id="2f14a-110">為報告 Service Broker 所管理之傳輸連接的狀態而產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-110">An event generated to report the status of a transport connection managed by Service Broker.</span></span>|  
|[<span data-ttu-id="2f14a-111">Broker:Conversation 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-111">Broker:Conversation Event Class</span></span>](broker-conversation-event-class.md)|<span data-ttu-id="2f14a-112">為報告交談進度而產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-112">An event generated to report the progress of a conversation.</span></span>|  
|[<span data-ttu-id="2f14a-113">Broker:Conversation Group 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-113">Broker:Conversation Group Event Class</span></span>](broker-conversation-group-event-class.md)|<span data-ttu-id="2f14a-114">資料庫建立或卸除交談群組時產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-114">An event generated when the database creates or drops a conversation group.</span></span>|  
|[<span data-ttu-id="2f14a-115">Broker:Corrupted Message 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-115">Broker:Corrupted Message Event Class</span></span>](broker-corrupted-message-event-class.md)|<span data-ttu-id="2f14a-116">產生的事件，用以報告資料庫已接收到損毀的訊息。</span><span class="sxs-lookup"><span data-stu-id="2f14a-116">An event generated to report that the database has received a corrupt message.</span></span>|  
|[<span data-ttu-id="2f14a-117">Broker:Forwarded Message Dropped 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-117">Broker:Forwarded Message Dropped Event Class</span></span>](broker-forwarded-message-dropped-event-class.md)|<span data-ttu-id="2f14a-118">當 SQL Server 卸除已轉送的 Service Broker 訊息時產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-118">An event generated when SQL Server drops a Service Broker message that was to have been forwarded.</span></span>|  
|[<span data-ttu-id="2f14a-119">Broker:Forwarded Message Sent 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-119">Broker:Forwarded Message Sent Event Class</span></span>](broker-forwarded-message-sent-event-class.md)|<span data-ttu-id="2f14a-120">當 SQL Server 轉送 Service Broker 訊息時產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-120">An event generated when SQL Server forwards a Service Broker message.</span></span>|  
|[<span data-ttu-id="2f14a-121">Broker:Message Classify 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-121">Broker:Message Classify Event Class</span></span>](broker-message-classify-event-class.md)|<span data-ttu-id="2f14a-122">當 Service Broker 決定訊息的路由時產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-122">An event generated when Service Broker determines the routing for a message.</span></span>|  
|[<span data-ttu-id="2f14a-123">Broker:Message Drop 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-123">Broker:Message Drop Event Class</span></span>](broker-message-drop-event-class.md)|<span data-ttu-id="2f14a-124">當 Service Broker 無法保留已收到且應該已傳遞給此執行個體中服務的訊息時產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-124">An event generated when Service Broker is unable to retain a received message that should have been delivered to a service in this instance</span></span>|  
|[<span data-ttu-id="2f14a-125">Broker:Remote Message Ack 事件類別</span><span class="sxs-lookup"><span data-stu-id="2f14a-125">Broker:Remote Message Ack Event Class</span></span>](broker-remote-message-ack-event-class.md)|<span data-ttu-id="2f14a-126">當 Service Broker 傳送或接收訊息收條時產生的事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-126">An event generated when Service Broker sends or receives a message acknowledgement.</span></span>|  
  
 <span data-ttu-id="2f14a-127">還為 Service Broker 提供了兩個安全性稽核事件。</span><span class="sxs-lookup"><span data-stu-id="2f14a-127">Two security audit events are also provided for Service Broker.</span></span> <span data-ttu-id="2f14a-128">如需這些事件的詳細資訊，請參閱 [Audit Broker 登入事件類別](audit-broker-login-event-class.md) 和 [Audit Broker 交談事件類別](audit-broker-conversation-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="2f14a-128">For more information on those events, see [Audit Broker Login Event Class](audit-broker-login-event-class.md) and [Audit Broker Conversation Event Class](audit-broker-conversation-event-class.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f14a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f14a-129">See Also</span></span>  
 [<span data-ttu-id="2f14a-130">安全性稽核事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="2f14a-130">Security Audit Event Category</span></span>](https://docs.microsoft.com/bi-reference/trace-events/security-audit-event-category)  
  
  
