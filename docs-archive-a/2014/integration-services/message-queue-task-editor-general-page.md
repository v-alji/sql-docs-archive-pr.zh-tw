---
title: '[訊息佇列工作編輯器] (一般頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dcec75f3a4dd85efb7c97226c592d6b1e1bb26ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606980"
---
# <a name="message-queue-task-editor-general-page"></a><span data-ttu-id="554cc-102">訊息佇列工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="554cc-102">Message Queue Task Editor (General Page)</span></span>
  <span data-ttu-id="554cc-103">使用 **[訊息佇列工作編輯器]** 對話方塊的 **[一般頁面]** ，即可命名和描述訊息佇列工作、指定訊息格式以及指出工作是否傳送或接收訊息。</span><span class="sxs-lookup"><span data-stu-id="554cc-103">Use the **General page** of the **Message Queue Task Editor** dialog box to name and describe the Message Queue task, to specify the message format, and to indicate whether the task sends or receives messages.</span></span>  
  
 <span data-ttu-id="554cc-104">若要了解這個工作，請參閱＜ [Message Queue Task](control-flow/message-queue-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="554cc-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="554cc-105">選項。</span><span class="sxs-lookup"><span data-stu-id="554cc-105">Options</span></span>  
 <span data-ttu-id="554cc-106">**名稱**</span><span class="sxs-lookup"><span data-stu-id="554cc-106">**Name**</span></span>  
 <span data-ttu-id="554cc-107">為訊息佇列工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="554cc-107">Provide a unique name for the Message Queue task.</span></span> <span data-ttu-id="554cc-108">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="554cc-108">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="554cc-109">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="554cc-109">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="554cc-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="554cc-110">**Description**</span></span>  
 <span data-ttu-id="554cc-111">輸入訊息佇列工作的描述。</span><span class="sxs-lookup"><span data-stu-id="554cc-111">Type a description of the Message Queue task.</span></span>  
  
 <span data-ttu-id="554cc-112">**Use2000Format**</span><span class="sxs-lookup"><span data-stu-id="554cc-112">**Use2000Format**</span></span>  
 <span data-ttu-id="554cc-113">指示是否使用 Message Queuing (又稱為 MSMQ) 的 2000 格式。</span><span class="sxs-lookup"><span data-stu-id="554cc-113">Indicate whether to use the 2000 format of Message Queuing (also known as MSMQ).</span></span> <span data-ttu-id="554cc-114">預設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="554cc-114">The default is `False`.</span></span>  
  
 <span data-ttu-id="554cc-115">**MSMQConnection**</span><span class="sxs-lookup"><span data-stu-id="554cc-115">**MSMQConnection**</span></span>  
 <span data-ttu-id="554cc-116">選取現有的 MSMQ 連線管理員或按一下 \<**New connection...**>，即可建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="554cc-116">Select an existing MSMQ connection manager or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="554cc-117">**相關主題**：[MSMQ 連線管理員](connection-manager/msmq-connection-manager.md)、[MSMQ 連線管理員編輯器](../../2014/integration-services/msmq-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="554cc-117">**Related Topics**: [MSMQ Connection Manager](connection-manager/msmq-connection-manager.md), [MSMQ Connection Manager Editor](../../2014/integration-services/msmq-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="554cc-118">**訊息**</span><span class="sxs-lookup"><span data-stu-id="554cc-118">**Message**</span></span>  
 <span data-ttu-id="554cc-119">指定訊息佇列工作是否傳送或接收訊息。</span><span class="sxs-lookup"><span data-stu-id="554cc-119">Specify whether the Message Queue task sends or receive messages.</span></span> <span data-ttu-id="554cc-120">如果選取 **[傳送訊息]** ，對話方塊的左窗格會列出 [傳送] 頁面，如果選取 **[接收訊息]** ，則會列出 [接收] 頁面。</span><span class="sxs-lookup"><span data-stu-id="554cc-120">If you select **Send message**, the Send page is listed in the left pane of the dialog box; if you select **Receive message**, the Receive page is listed.</span></span> <span data-ttu-id="554cc-121">依預設，此值設定為 **[傳送訊息]** 。</span><span class="sxs-lookup"><span data-stu-id="554cc-121">By default, this value is set to **Send message**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554cc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="554cc-122">See Also</span></span>  
 <span data-ttu-id="554cc-123">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="554cc-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="554cc-124">[[訊息佇列工作編輯器] &#40;接收頁面&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="554cc-124">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 <span data-ttu-id="554cc-125">[[訊息佇列工作編輯器] &#40;傳送頁面&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="554cc-125">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 [<span data-ttu-id="554cc-126">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="554cc-126">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
