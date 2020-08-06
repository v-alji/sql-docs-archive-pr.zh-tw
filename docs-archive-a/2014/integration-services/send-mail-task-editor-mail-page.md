---
title: '[傳送郵件工作編輯器] ([郵件] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 52cab62f3c88ea248b76061664547fd8f1314099
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709766"
---
# <a name="send-mail-task-editor-mail-page"></a><span data-ttu-id="383d2-102">傳送郵件工作編輯器 (郵件頁面)</span><span class="sxs-lookup"><span data-stu-id="383d2-102">Send Mail Task Editor (Mail Page)</span></span>
  <span data-ttu-id="383d2-103">使用 [傳送郵件工作編輯器]  對話方塊的 [郵件]  頁面，即可指定收件者、訊息類型以及訊息的優先權。</span><span class="sxs-lookup"><span data-stu-id="383d2-103">Use the **Mail** page of the **Send Mail Task Editor** dialog box to specify recipients, message type, and priority for a message.</span></span> <span data-ttu-id="383d2-104">您也可以附加檔案至訊息。</span><span class="sxs-lookup"><span data-stu-id="383d2-104">You can also attach files to the message.</span></span> <span data-ttu-id="383d2-105">訊息文字可以是您提供的字串、包含文字之檔案的檔案連接，或包含文字之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="383d2-105">The message text can be a string you provide, a file connection to a file that contains the text, or the name of a variable that contains the text.</span></span>  
  
 <span data-ttu-id="383d2-106">若要了解這項工作，請參閱 [傳送郵件工作](control-flow/send-mail-task.md)。</span><span class="sxs-lookup"><span data-stu-id="383d2-106">To learn about this task, see [Send Mail Task](control-flow/send-mail-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="383d2-107">選項。</span><span class="sxs-lookup"><span data-stu-id="383d2-107">Options</span></span>  
 <span data-ttu-id="383d2-108">**SMTPConnection**</span><span class="sxs-lookup"><span data-stu-id="383d2-108">**SMTPConnection**</span></span>  
 <span data-ttu-id="383d2-109">在清單中選取 SMTP 連線管理員，或按一下 [\<New connection...>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="383d2-109">Select an SMTP connection manager in the list, or click **\<New connection...>** to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="383d2-110">SMTP 連接管理員僅支援匿名驗證和 Windows 驗證，</span><span class="sxs-lookup"><span data-stu-id="383d2-110">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="383d2-111">而不支援基本驗證。</span><span class="sxs-lookup"><span data-stu-id="383d2-111">It does not support basic authentication.</span></span>  
  
 <span data-ttu-id="383d2-112">**相關主題：** [SMTP 連線管理員](connection-manager/smtp-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="383d2-112">**Related Topics:** [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)</span></span>  
  
 <span data-ttu-id="383d2-113">**From**</span><span class="sxs-lookup"><span data-stu-id="383d2-113">**From**</span></span>  
 <span data-ttu-id="383d2-114">指定寄件者的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="383d2-114">Specify the e-mail address of the sender.</span></span>  
  
 <span data-ttu-id="383d2-115">**若要**</span><span class="sxs-lookup"><span data-stu-id="383d2-115">**To**</span></span>  
 <span data-ttu-id="383d2-116">提供收件者的電子郵件地址，以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="383d2-116">Provide the e-mail addresses of the recipients, delimited by semicolons.</span></span>  
  
 <span data-ttu-id="383d2-117">**副本**</span><span class="sxs-lookup"><span data-stu-id="383d2-117">**Cc**</span></span>  
 <span data-ttu-id="383d2-118">指定也會收到訊息副本之個人的電子郵件地址，以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="383d2-118">Specify the e-mail addresses, delimited by semicolons, of individuals who also receive copies of the message.</span></span>  
  
 <span data-ttu-id="383d2-119">**密件副本**</span><span class="sxs-lookup"><span data-stu-id="383d2-119">**Bcc**</span></span>  
 <span data-ttu-id="383d2-120">指定也會收到訊息密件副本 (Bcc) 之個人的電子郵件地址，以分號分隔。</span><span class="sxs-lookup"><span data-stu-id="383d2-120">Specify the e-mail addresses, delimited by semicolons, of individuals who receive blind carbon copies (Bcc) copies of the message.</span></span>  
  
 <span data-ttu-id="383d2-121">**主旨**</span><span class="sxs-lookup"><span data-stu-id="383d2-121">**Subject**</span></span>  
 <span data-ttu-id="383d2-122">提供電子郵件訊息的主旨。</span><span class="sxs-lookup"><span data-stu-id="383d2-122">Provide a subject for the e-mail message.</span></span>  
  
 <span data-ttu-id="383d2-123">**MessageSourceType**</span><span class="sxs-lookup"><span data-stu-id="383d2-123">**MessageSourceType**</span></span>  
 <span data-ttu-id="383d2-124">選取訊息的來源類型。</span><span class="sxs-lookup"><span data-stu-id="383d2-124">Select the source type of the message.</span></span> <span data-ttu-id="383d2-125">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="383d2-125">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="383d2-126">值</span><span class="sxs-lookup"><span data-stu-id="383d2-126">Value</span></span>|<span data-ttu-id="383d2-127">描述</span><span class="sxs-lookup"><span data-stu-id="383d2-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="383d2-128">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="383d2-128">**Direct input**</span></span>|<span data-ttu-id="383d2-129">將來源設定為訊息文字。</span><span class="sxs-lookup"><span data-stu-id="383d2-129">Set the source to the message text.</span></span> <span data-ttu-id="383d2-130">選取此值會顯示動態選項 [MessageSource]  。</span><span class="sxs-lookup"><span data-stu-id="383d2-130">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="383d2-131">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="383d2-131">**File connection**</span></span>|<span data-ttu-id="383d2-132">將來源設定為包含訊息文字的檔案。</span><span class="sxs-lookup"><span data-stu-id="383d2-132">Set the source to the file that contains the message text.</span></span> <span data-ttu-id="383d2-133">選取此值會顯示動態選項 [MessageSource]  。</span><span class="sxs-lookup"><span data-stu-id="383d2-133">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
|<span data-ttu-id="383d2-134">**變數**</span><span class="sxs-lookup"><span data-stu-id="383d2-134">**Variable**</span></span>|<span data-ttu-id="383d2-135">將來源設定為包含訊息文字的變數。</span><span class="sxs-lookup"><span data-stu-id="383d2-135">Set the source to a variable that contains the message text.</span></span> <span data-ttu-id="383d2-136">選取此值會顯示動態選項 [MessageSource]  。</span><span class="sxs-lookup"><span data-stu-id="383d2-136">Selecting this value displays the dynamic option, **MessageSource**.</span></span>|  
  
 <span data-ttu-id="383d2-137">**優先順序**</span><span class="sxs-lookup"><span data-stu-id="383d2-137">**Priority**</span></span>  
 <span data-ttu-id="383d2-138">設定訊息的優先權。</span><span class="sxs-lookup"><span data-stu-id="383d2-138">Set the priority of the message.</span></span>  
  
 <span data-ttu-id="383d2-139">**附加檔案**</span><span class="sxs-lookup"><span data-stu-id="383d2-139">**Attachments**</span></span>  
 <span data-ttu-id="383d2-140">提供電子郵件訊息之附加檔案的檔案名稱，以垂直線 (|) 字元分隔。</span><span class="sxs-lookup"><span data-stu-id="383d2-140">Provide the file names of attachments to the e-mail message, delimited by the pipe (|) character.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="383d2-141">根據網際網路標準，[收件者]、[副本] 和 [密件副本] 欄位限制為 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="383d2-141">The To, Cc, and Bcc lines are limited to 256 characters in accordance with Internet standards.</span></span>  
  
## <a name="messagesourcetype-dynamic-options"></a><span data-ttu-id="383d2-142">MessageSourceType 動態選項</span><span class="sxs-lookup"><span data-stu-id="383d2-142">MessageSourceType Dynamic Options</span></span>  
  
### <a name="messagesourcetype--direct-input"></a><span data-ttu-id="383d2-143">MessageSourceType = 直接輸入</span><span class="sxs-lookup"><span data-stu-id="383d2-143">MessageSourceType = Direct Input</span></span>  
 <span data-ttu-id="383d2-144">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="383d2-144">**MessageSource**</span></span>  
 <span data-ttu-id="383d2-145">輸入訊息文字或按一下瀏覽按鈕 ([...])，然後在 [訊息來源]  對話方塊中輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="383d2-145">Type the message text or click the browse button (...) and then type the message in the **Message source** dialog box.</span></span>  
  
### <a name="messagesourcetype--file-connection"></a><span data-ttu-id="383d2-146">MessageSourceType = 檔案連接</span><span class="sxs-lookup"><span data-stu-id="383d2-146">MessageSourceType = File connection</span></span>  
 <span data-ttu-id="383d2-147">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="383d2-147">**MessageSource**</span></span>  
 <span data-ttu-id="383d2-148">在清單中選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="383d2-148">Select a File connection manager in the list or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="383d2-149">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="383d2-149">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="messagesourcetype--variable"></a><span data-ttu-id="383d2-150">MessageSourceType = 變數</span><span class="sxs-lookup"><span data-stu-id="383d2-150">MessageSourceType = Variable</span></span>  
 <span data-ttu-id="383d2-151">**MessageSource**</span><span class="sxs-lookup"><span data-stu-id="383d2-151">**MessageSource**</span></span>  
 <span data-ttu-id="383d2-152">在清單中選取變數，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="383d2-152">Select a variable in the list or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="383d2-153">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="383d2-153">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383d2-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="383d2-154">See Also</span></span>  
 <span data-ttu-id="383d2-155">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="383d2-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="383d2-156">[[傳送郵件工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="383d2-156">[Send Mail Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="383d2-157">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="383d2-157">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
