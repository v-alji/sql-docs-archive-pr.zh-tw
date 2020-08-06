---
title: '[訊息佇列工作編輯器] (傳送頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.send.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 565aa079-ac44-4407-8efc-cddab839de30
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3534e1a8b475f22064ef7f2283c2e70eb561294f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710714"
---
# <a name="message-queue-task-editor-send-page"></a><span data-ttu-id="9cbdb-102">訊息佇列工作編輯器 (傳送頁面)</span><span class="sxs-lookup"><span data-stu-id="9cbdb-102">Message Queue Task Editor (Send Page)</span></span>
  <span data-ttu-id="9cbdb-103">使用 [訊息佇列工作編輯器]  對話方塊的 [傳送]  頁面，即可設定從 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 套件傳送訊息的「訊息佇列」工作。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-103">Use the **Send** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to send messages from a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span>  
  
 <span data-ttu-id="9cbdb-104">若要了解這個工作，請參閱＜ [Message Queue Task](control-flow/message-queue-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9cbdb-105">選項。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-105">Options</span></span>  
 <span data-ttu-id="9cbdb-106">**UseEncryption**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-106">**UseEncryption**</span></span>  
 <span data-ttu-id="9cbdb-107">指出是否要加密訊息。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-107">Indicate whether to encrypt the message.</span></span> <span data-ttu-id="9cbdb-108">預設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-108">The default is `False`.</span></span>  
  
 <span data-ttu-id="9cbdb-109">**EncryptionAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-109">**EncryptionAlgorithm**</span></span>  
 <span data-ttu-id="9cbdb-110">如果您選擇使用加密，請指定要使用之加密演算法的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-110">If you choose to use encryption, specify the name of the encryption algorithm to use.</span></span> <span data-ttu-id="9cbdb-111">「訊息佇列」工作可以使用 RC2 和 RC4 演算法。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-111">The Message Queue task can use the RC2 and RC4 algorithms.</span></span> <span data-ttu-id="9cbdb-112">預設值是 **[RC2]** 。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-112">The default is **RC2**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cbdb-113">只有 RC4 演算法支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-113">The RC4 algorithm is only supported for backward compatibility.</span></span> <span data-ttu-id="9cbdb-114">只有在資料庫相容性層級為 90 或 100 時，才能使用 RC4 或 RC4_128 加密新資料</span><span class="sxs-lookup"><span data-stu-id="9cbdb-114">New material can only be encrypted using RC4 or RC4_128 when the database is in compatibility level 90 or 100.</span></span> <span data-ttu-id="9cbdb-115">(不建議使用)。請改用較新的演算法，例如其中一個 AES 演算法。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-115">(Not recommended.) Use a newer algorithm such as one of the AES algorithms instead.</span></span> <span data-ttu-id="9cbdb-116">在最新版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，使用 RC4 或 RC4_128 加密的資料，可以在任何相容性層級進行解密。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-116">In the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], material encrypted using RC4 or RC4_128 can be decrypted in any compatibility level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9cbdb-117">這些是 Message Queuing (又稱為 MSMQ) 技術支援的加密演算法。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-117">These are the encryption algorithms that the Message Queuing (also known as MSMQ) technology supports.</span></span> <span data-ttu-id="9cbdb-118">這兩種加密演算法目前被認為在密碼編譯技術上不如較新的演算法，不過 Message Queuing 目前還不支援較新的演算法。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-118">Both of these encryption algorithms are now considered cryptographically weak compared to newer algorithms, which Message Queuing does not yet support.</span></span> <span data-ttu-id="9cbdb-119">因此，在使用「訊息佇列」工作傳送訊息時，應仔細考慮您的加密需求。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-119">Therefore, you should consider your cryptography needs carefully when sending messages using the Message Queue task.</span></span>  
  
 <span data-ttu-id="9cbdb-120">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-120">**MessageType**</span></span>  
 <span data-ttu-id="9cbdb-121">選取訊息類型。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-121">Select the message type.</span></span> <span data-ttu-id="9cbdb-122">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-122">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="9cbdb-123">值</span><span class="sxs-lookup"><span data-stu-id="9cbdb-123">Value</span></span>|<span data-ttu-id="9cbdb-124">描述</span><span class="sxs-lookup"><span data-stu-id="9cbdb-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9cbdb-125">**資料檔訊息**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-125">**Data file message**</span></span>|<span data-ttu-id="9cbdb-126">訊息儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-126">The message is stored in a file.</span></span> <span data-ttu-id="9cbdb-127">選取此值會顯示動態選項 **[DataFileMessage]** 。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-127">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="9cbdb-128">**變數訊息**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-128">**Variable message**</span></span>|<span data-ttu-id="9cbdb-129">訊息儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-129">The message is stored in a variable.</span></span> <span data-ttu-id="9cbdb-130">選取此值會顯示動態選項 **[VariableMessage]** 。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-130">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="9cbdb-131">**字串訊息**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-131">**String message**</span></span>|<span data-ttu-id="9cbdb-132">訊息儲存在訊息佇列工作中。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-132">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="9cbdb-133">選取此值會顯示動態選項 **[StringMessage]** 。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-133">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="9cbdb-134">MessageType 動態選項</span><span class="sxs-lookup"><span data-stu-id="9cbdb-134">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="9cbdb-135">MessageType = 資料檔訊息</span><span class="sxs-lookup"><span data-stu-id="9cbdb-135">MessageType = Data file message</span></span>  
 <span data-ttu-id="9cbdb-136">**[DataFileMessage]**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-136">**DataFileMessage**</span></span>  
 <span data-ttu-id="9cbdb-137">鍵入資料檔的路徑，或按一下省略符號 **(...)** ，然後尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-137">Type the path of the data file, or click the ellipsis **(...)** and then locate the file.</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="9cbdb-138">MessageType = 變數訊息</span><span class="sxs-lookup"><span data-stu-id="9cbdb-138">MessageType = Variable message</span></span>  
 <span data-ttu-id="9cbdb-139">**[VariableMessage]**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-139">**VariableMessage**</span></span>  
 <span data-ttu-id="9cbdb-140">鍵入變數名稱，或按一下省略符號 **(...)** ，然後選取變數。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-140">Type the variable names, or click the ellipsis **(...)** and then select the variables.</span></span> <span data-ttu-id="9cbdb-141">變數以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-141">Variables are separated by commas.</span></span>  
  
 <span data-ttu-id="9cbdb-142">**相關主題：** 選取變數</span><span class="sxs-lookup"><span data-stu-id="9cbdb-142">**Related Topics:** Select Variables</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="9cbdb-143">MessageType = 字串訊息</span><span class="sxs-lookup"><span data-stu-id="9cbdb-143">MessageType = String message</span></span>  
 <span data-ttu-id="9cbdb-144">**[StringMessage]**</span><span class="sxs-lookup"><span data-stu-id="9cbdb-144">**StringMessage**</span></span>  
 <span data-ttu-id="9cbdb-145">鍵入字串訊息，或按一下省略符號 **(...)** ，然後在 [鍵入字串訊息]  對話方塊中鍵入訊息。</span><span class="sxs-lookup"><span data-stu-id="9cbdb-145">Type the string message, or click the ellipsis **(...)** and then type the message in the **Enter String Message** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cbdb-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cbdb-146">See Also</span></span>  
 <span data-ttu-id="9cbdb-147">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9cbdb-147">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9cbdb-148">[[訊息佇列工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="9cbdb-148">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="9cbdb-149">[[訊息佇列工作編輯器] &#40;接收頁面&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span><span class="sxs-lookup"><span data-stu-id="9cbdb-149">[Message Queue Task Editor &#40;Receive Page&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md) </span></span>  
 [<span data-ttu-id="9cbdb-150">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="9cbdb-150">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
