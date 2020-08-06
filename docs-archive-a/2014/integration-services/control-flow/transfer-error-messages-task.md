---
title: 傳送錯誤訊息工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.f1
helpviewer_keywords:
- Transfer Error Messages task [Integration Services]
ms.assetid: da702289-035a-4d14-bd74-04461fbfee1b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952acc28a79fef7e7351c97400e05bc7ba5b9243
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584665"
---
# <a name="transfer-error-messages-task"></a><span data-ttu-id="0ecad-102">傳送錯誤訊息工作</span><span class="sxs-lookup"><span data-stu-id="0ecad-102">Transfer Error Messages Task</span></span>
  <span data-ttu-id="0ecad-103">[傳送錯誤訊息] 工作會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體之間傳送一或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用者自訂的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-103">The Transfer Error Messages task transfers one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user-defined error messages between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0ecad-104">使用者定義的訊息是識別碼等於或大於 50000 的訊息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-104">User-defined messages are messages with an identifier that is equal to or greater than 50000.</span></span> <span data-ttu-id="0ecad-105">識別碼小於 50000 的訊息是系統錯誤訊息，這種訊息無法使用「傳送錯誤訊息」工作進行傳送。</span><span class="sxs-lookup"><span data-stu-id="0ecad-105">Messages with an identifier less than 50000 are system error messages, and cannot be transferred by using the Transfer Error Messages task.</span></span>  
  
 <span data-ttu-id="0ecad-106">「傳送錯誤訊息」工作可以設定為傳送所有錯誤訊息，或只傳送指定的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-106">The Transfer Error Messages task can be configured to transfer all error messages, or only the specified error messages.</span></span> <span data-ttu-id="0ecad-107">使用者自訂的錯誤訊息可能有很多不同的語言版本，您可以設定工作只傳送所選語言的訊息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-107">User-defined error messages may be available in a number of different languages and the task can be configured to transfer only messages in selected languages.</span></span> <span data-ttu-id="0ecad-108">在您可以傳送其他語言版本的訊息至目的地伺服器之前，使用字碼頁 1033 的 us_english 版訊息必須存在於該伺服器上。</span><span class="sxs-lookup"><span data-stu-id="0ecad-108">A us_english version of the message that uses code page 1033 must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
 <span data-ttu-id="0ecad-109">master 資料庫中的 sysmessages 資料表包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的所有錯誤訊息 (包括系統和使用者定義的訊息)。</span><span class="sxs-lookup"><span data-stu-id="0ecad-109">The sysmessages table in the master database contains all the error messages-both system and user-defined-that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses.</span></span>  
  
 <span data-ttu-id="0ecad-110">要傳送的使用者自訂訊息可能已存在於目的地上。</span><span class="sxs-lookup"><span data-stu-id="0ecad-110">The user-defined messages to be transferred may already exist on the destination.</span></span> <span data-ttu-id="0ecad-111">如果識別碼和語言相同，則會將錯誤訊息定義為重複錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-111">An error message is defined as a duplicate error message if the identifier and the language are the same.</span></span> <span data-ttu-id="0ecad-112">可以設定「傳送錯誤訊息」工作以下列方式處理現有的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="0ecad-112">The Transfer Error Messages task can be configured to handle existing error messages in the following ways:</span></span>  
  
-   <span data-ttu-id="0ecad-113">覆寫現有的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-113">Overwrite existing error messages.</span></span>  
  
-   <span data-ttu-id="0ecad-114">存在重複的訊息時讓工作失敗。</span><span class="sxs-lookup"><span data-stu-id="0ecad-114">Fail the task when duplicate messages exist.</span></span>  
  
-   <span data-ttu-id="0ecad-115">略過重複的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="0ecad-115">Skip duplicate error messages.</span></span>  
  
 <span data-ttu-id="0ecad-116">在執行階段，「傳送錯誤訊息」工作會使用一或多個 SMO 連接管理員，連接到來源和目的地伺服器。</span><span class="sxs-lookup"><span data-stu-id="0ecad-116">At run time, the Transfer Error Messages task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="0ecad-117">SMO 連接管理員會在「傳送錯誤訊息」工作以外另行設定，然後在「傳送錯誤訊息」工作中參考。</span><span class="sxs-lookup"><span data-stu-id="0ecad-117">The SMO connection manager is configured separately from the Transfer Error Messages task, and then is referenced in the Transfer Error Messages task.</span></span> <span data-ttu-id="0ecad-118">存取伺服器時，SMO 連接管理員會指定要使用的伺服器和驗證模式。</span><span class="sxs-lookup"><span data-stu-id="0ecad-118">The SMO connection manager specifies the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="0ecad-119">如需詳細資訊，請參閱 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="0ecad-119">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="0ecad-120">[傳送錯誤訊息] 工作支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源和目的地。</span><span class="sxs-lookup"><span data-stu-id="0ecad-120">The Transfer Error Messages task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span> <span data-ttu-id="0ecad-121">將哪一個用作來源或目的地是沒有限制的。</span><span class="sxs-lookup"><span data-stu-id="0ecad-121">There are no restrictions on which version to use as a source or destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="0ecad-122">事件</span><span class="sxs-lookup"><span data-stu-id="0ecad-122">Events</span></span>  
 <span data-ttu-id="0ecad-123">「傳送錯誤訊息」工作會引發報告已傳送錯誤訊息數目的資訊事件。</span><span class="sxs-lookup"><span data-stu-id="0ecad-123">The task raises an information event that reports the number of error messages that have been transferred.</span></span>  
  
 <span data-ttu-id="0ecad-124">該工作並不報告錯誤訊息傳送的累加進度，它只報告 0% 和 100 % 完成。</span><span class="sxs-lookup"><span data-stu-id="0ecad-124">The Transfer Error Messages task does not report incremental progress of the error message transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="0ecad-125">執行值</span><span class="sxs-lookup"><span data-stu-id="0ecad-125">Execution Value</span></span>  
 <span data-ttu-id="0ecad-126">工作之 `ExecutionValue` 屬性中定義的執行值會傳回已傳送的錯誤訊息數目。</span><span class="sxs-lookup"><span data-stu-id="0ecad-126">The execution value, defined in the `ExecutionValue` property of the task, returns the number of error messages that have been transferred.</span></span> <span data-ttu-id="0ecad-127">透過將使用者自訂變數指派給「傳送錯誤訊息」工作的 `ExecValueVariable` 屬性，可將與錯誤訊息傳送相關的資訊用於封裝中的其他物件。</span><span class="sxs-lookup"><span data-stu-id="0ecad-127">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Error Message task, information about the error message transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="0ecad-128">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)和[在封裝中使用變數](../use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="0ecad-128">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="0ecad-129">記錄項目</span><span class="sxs-lookup"><span data-stu-id="0ecad-129">Log Entries</span></span>  
 <span data-ttu-id="0ecad-130">「傳送錯誤訊息」工作包含下列自訂記錄項目：</span><span class="sxs-lookup"><span data-stu-id="0ecad-130">The Transfer Error Messages task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="0ecad-131">TransferErrorMessagesTaskStartTransferringObjects    此記錄項目報告傳送已開始。</span><span class="sxs-lookup"><span data-stu-id="0ecad-131">TransferErrorMessagesTaskStartTransferringObjects    This log entry reports that the transfer has started.</span></span> <span data-ttu-id="0ecad-132">記錄項目會包含開始時間。</span><span class="sxs-lookup"><span data-stu-id="0ecad-132">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="0ecad-133">TransferErrorMessagesTaskFinishedTransferringObjects   此記錄項目報告傳送已完成。</span><span class="sxs-lookup"><span data-stu-id="0ecad-133">TransferErrorMessagesTaskFinishedTransferringObjects   This log entry reports that the transfer has finished.</span></span> <span data-ttu-id="0ecad-134">記錄項目會包含結束時間。</span><span class="sxs-lookup"><span data-stu-id="0ecad-134">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="0ecad-135">此外，`OnInformation` 事件的記錄項目會報告已傳送的錯誤訊息數，並會為在目的地上覆寫的每個錯誤訊息寫入 `OnWarning event` 的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="0ecad-135">In addition, a log entry for the `OnInformation` event reports the number of error messages that were transferred, and a log entry for the `OnWarning event` is written for each error message on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="0ecad-136">安全性和權限</span><span class="sxs-lookup"><span data-stu-id="0ecad-136">Security and Permissions</span></span>  
 <span data-ttu-id="0ecad-137">若要建立新的錯誤訊息，執行封裝的使用者必須是目的地伺服器上 sysadmin 或 serveradmin 伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="0ecad-137">To create new error messages, the user that runs the package must be a member of the sysadmin or serveradmin server role on the destination server.</span></span>  
  
## <a name="configuration-of-the-transfer-error-messages-task"></a><span data-ttu-id="0ecad-138">傳送錯誤訊息工作的組態</span><span class="sxs-lookup"><span data-stu-id="0ecad-138">Configuration of the Transfer Error Messages Task</span></span>  
 <span data-ttu-id="0ecad-139">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0ecad-139">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="0ecad-140">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="0ecad-140">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="0ecad-141">傳送錯誤訊息工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="0ecad-141">Transfer Error Messages Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="0ecad-142">傳送錯誤訊息工作編輯器 &#40;訊息頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="0ecad-142">Transfer Error Messages Task Editor &#40;Messages Page&#41;</span></span>](../transfer-error-messages-task-editor-messages-page.md)  
  
-   [<span data-ttu-id="0ecad-143">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="0ecad-143">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="0ecad-144">如需有關如何以程式設計方式設定這些屬性的詳細資訊，請按以下主題：</span><span class="sxs-lookup"><span data-stu-id="0ecad-144">For information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferErrorMessagesTask.TransferErrorMessagesTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="0ecad-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="0ecad-145">Related Tasks</span></span>  
 <span data-ttu-id="0ecad-146">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="0ecad-146">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="0ecad-147">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="0ecad-147">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="0ecad-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ecad-148">See Also</span></span>  
 <span data-ttu-id="0ecad-149">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="0ecad-149">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="0ecad-150">控制流程</span><span class="sxs-lookup"><span data-stu-id="0ecad-150">Control Flow</span></span>](control-flow.md)  
  
  
