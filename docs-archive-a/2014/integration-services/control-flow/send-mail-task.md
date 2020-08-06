---
title: 傳送電子郵件工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.f1
helpviewer_keywords:
- mail [Integration Services]
- Send Mail task
- e-mail [Integration Services]
- messages [Integration Services]
- sending messages
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c93723f3c443705acc14226ce07f456da4d5a884
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592801"
---
# <a name="send-mail-task"></a><span data-ttu-id="a2702-102">傳送郵件工作</span><span class="sxs-lookup"><span data-stu-id="a2702-102">Send Mail Task</span></span>
  <span data-ttu-id="a2702-103">傳送郵件工作會傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="a2702-103">The Send Mail task sends an e-mail message.</span></span> <span data-ttu-id="a2702-104">藉由使用傳送郵件工作，封裝即可在封裝工作流程中的工作成功或失敗時傳送訊息，或傳送回應封裝在執行階段所引發事件的訊息。</span><span class="sxs-lookup"><span data-stu-id="a2702-104">By using the Send Mail task, a package can send messages if tasks in the package workflow succeed or fail, or send messages in response to an event that the package raises at run time.</span></span> <span data-ttu-id="a2702-105">例如，工作可通知資料庫管理員「備份資料庫」工作成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="a2702-105">For example, the task can notify a database administrator about the success or failure of the Backup Database task.</span></span>  
  
 <span data-ttu-id="a2702-106">您可以利用下列方式設定傳送郵件工作：</span><span class="sxs-lookup"><span data-stu-id="a2702-106">You can configure the Send Mail task in the following ways:</span></span>  
  
-   <span data-ttu-id="a2702-107">提供電子郵件訊息的訊息文字。</span><span class="sxs-lookup"><span data-stu-id="a2702-107">Provide the message text for the e-mail message.</span></span>  
  
-   <span data-ttu-id="a2702-108">提供電子郵件訊息的主旨。</span><span class="sxs-lookup"><span data-stu-id="a2702-108">Provide a subject line for the e-mail message.</span></span>  
  
-   <span data-ttu-id="a2702-109">設定訊息的優先順序等級。</span><span class="sxs-lookup"><span data-stu-id="a2702-109">Set the priority level of the message.</span></span> <span data-ttu-id="a2702-110">這項工作支援三種優先順序等級：一般、低和高。</span><span class="sxs-lookup"><span data-stu-id="a2702-110">The task supports three priority levels: normal, low, and high.</span></span>  
  
-   <span data-ttu-id="a2702-111">指定 [收件者]、[副本] 和 [密件副本] 欄位的收件者。</span><span class="sxs-lookup"><span data-stu-id="a2702-111">Specify the recipients on the To, Cc, and Bcc lines.</span></span> <span data-ttu-id="a2702-112">如果工作指定多位收件者，則會以分號分隔各收件者。</span><span class="sxs-lookup"><span data-stu-id="a2702-112">If the task specifies multiple recipients, they are separated by semicolons.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2702-113">根據網際網路標準，[收件者]、[副本] 和 [密件副本] 欄位限制為 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="a2702-113">The To, Cc, and Bcc lines are limited to 256 characters each in accordance with Internet standards.</span></span>  
  
-   <span data-ttu-id="a2702-114">包含附加檔案。</span><span class="sxs-lookup"><span data-stu-id="a2702-114">Include attachments.</span></span> <span data-ttu-id="a2702-115">如果工作指定多個附加檔案，則會以縱線 (|) 字元分隔各附加檔案。</span><span class="sxs-lookup"><span data-stu-id="a2702-115">If the task specifies multiple attachments, they are separated by the pipe (|) character.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2702-116">如果封裝執行時附加檔案不存在，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2702-116">If an attachment file does not exist when the package runs, an error occurs.</span></span>  
  
-   <span data-ttu-id="a2702-117">指定要使用的 SMTP 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="a2702-117">Specify the SMTP connection manager to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="a2702-118">SMTP 連接管理員僅支援匿名驗證和 Windows 驗證，</span><span class="sxs-lookup"><span data-stu-id="a2702-118">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="a2702-119">而不支援基本驗證。</span><span class="sxs-lookup"><span data-stu-id="a2702-119">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="a2702-120">訊息文字可以是您提供的字串、包含文字的檔案連接，或包含文字的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="a2702-120">The message text can be a string that you provide, a connection to a file that contains the text, or the name of a variable that contains the text.</span></span> <span data-ttu-id="a2702-121">工作會使用「檔案」連接管理員連接檔案。</span><span class="sxs-lookup"><span data-stu-id="a2702-121">The task uses a File connection manager to connect to a file.</span></span> <span data-ttu-id="a2702-122">如需相關資訊，請參閱 [Flat File Connection Manager](../connection-manager/file-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a2702-122">For more information, see [Flat File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="a2702-123">工作會使用 SMTP 連接管理員連接到郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="a2702-123">The task uses an SMTP connection manager to connect to a mail server.</span></span> <span data-ttu-id="a2702-124">如需相關資訊，請參閱 [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="a2702-124">For more information, see [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-send-mail-task"></a><span data-ttu-id="a2702-125">傳送郵件工作上可用的自訂記錄訊息</span><span class="sxs-lookup"><span data-stu-id="a2702-125">Custom Logging Messages Available on the Send Mail Task</span></span>  
 <span data-ttu-id="a2702-126">下表列出「傳送郵件」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="a2702-126">The following table lists the custom log entries for the Send Mail task.</span></span> <span data-ttu-id="a2702-127">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="a2702-127">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="a2702-128">記錄項目</span><span class="sxs-lookup"><span data-stu-id="a2702-128">Log entry</span></span>|<span data-ttu-id="a2702-129">描述</span><span class="sxs-lookup"><span data-stu-id="a2702-129">Description</span></span>|  
|---------------|-----------------|  
|`SendMailTaskBegin`|<span data-ttu-id="a2702-130">指出工作已經開始傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="a2702-130">Indicates that the task began to send an e-mail message.</span></span>|  
|`SendMailTaskEnd`|<span data-ttu-id="a2702-131">指出工作已經完成傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="a2702-131">Indicates that the task finished sending an e-mail message.</span></span>|  
|`SendMailTaskInfo`|<span data-ttu-id="a2702-132">提供有關工作的描述性資訊。</span><span class="sxs-lookup"><span data-stu-id="a2702-132">Provides descriptive information about the task.</span></span>|  
  
## <a name="configuring-the-send-mail-task"></a><span data-ttu-id="a2702-133">設定傳送郵件工作</span><span class="sxs-lookup"><span data-stu-id="a2702-133">Configuring the Send Mail Task</span></span>  
 <span data-ttu-id="a2702-134">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a2702-134">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="a2702-135">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="a2702-135">For information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="a2702-136">傳送郵件工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="a2702-136">Send Mail Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="a2702-137">傳送郵件工作編輯器 &#40;郵件頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="a2702-137">Send Mail Task Editor &#40;Mail Page&#41;</span></span>](../send-mail-task-editor-mail-page.md)  
  
-   [<span data-ttu-id="a2702-138">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="a2702-138">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="a2702-139">如需有關如何以程式設計方式設定這些屬性的詳細資訊，請按以下主題：</span><span class="sxs-lookup"><span data-stu-id="a2702-139">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="a2702-140">相關工作</span><span class="sxs-lookup"><span data-stu-id="a2702-140">Related Tasks</span></span>  
 <span data-ttu-id="a2702-141">如需如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定這些屬性的資訊，請按一下 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="a2702-141">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="a2702-142">相關內容</span><span class="sxs-lookup"><span data-stu-id="a2702-142">Related Content</span></span>  
  
-   <span data-ttu-id="a2702-143">shareourideas.com 上的技術文件： [如何在 C# 中傳送包含傳遞通知的電子郵件](https://go.microsoft.com/fwlink/?LinkId=237625)(如何在 C# 中傳送包含傳遞通知的電子郵件)</span><span class="sxs-lookup"><span data-stu-id="a2702-143">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2702-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2702-144">See Also</span></span>  
 <span data-ttu-id="a2702-145">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a2702-145">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="a2702-146">控制流程</span><span class="sxs-lookup"><span data-stu-id="a2702-146">Control Flow</span></span>](control-flow.md)  
  
  
