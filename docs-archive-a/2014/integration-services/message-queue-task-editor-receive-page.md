---
title: '[訊息佇列工作編輯器] (接收頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f45aa579d37d1fdd3a3124eea972014ce839fdc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710717"
---
# <a name="message-queue-task-editor-receive-page"></a><span data-ttu-id="fb4b0-102">訊息佇列工作編輯器 (接收頁面)</span><span class="sxs-lookup"><span data-stu-id="fb4b0-102">Message Queue Task Editor (Receive Page)</span></span>
  <span data-ttu-id="fb4b0-103">使用 [訊息佇列工作編輯器]  對話方塊的 [接收]  頁面，即可設定訊息佇列工作，以接收 [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ) 訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-103">Use the **Receive** page of the **Message Queue Task Editor** dialog box to configure a Message Queue task to receive [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ) messages.</span></span>  
  
 <span data-ttu-id="fb4b0-104">若要了解這個工作，請參閱＜ [Message Queue Task](control-flow/message-queue-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-104">To learn about this task, see [Message Queue Task](control-flow/message-queue-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fb4b0-105">選項。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-105">Options</span></span>  
 <span data-ttu-id="fb4b0-106">**RemoveFromMessageQueue**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-106">**RemoveFromMessageQueue**</span></span>  
 <span data-ttu-id="fb4b0-107">指出接收訊息之後，是否從佇列中移除該訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-107">Indicate whether to remove the message from the queue after it is received.</span></span> <span data-ttu-id="fb4b0-108">依預設，此值設定為 `False`。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-108">By default, this value is set to `False`.</span></span>  
  
 <span data-ttu-id="fb4b0-109">**ErrorIfMessageTimeOut**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-109">**ErrorIfMessageTimeOut**</span></span>  
 <span data-ttu-id="fb4b0-110">指出當訊息逾時的時侯工作是否失敗，並顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-110">Indicate whether the task fails when the message times out, displaying an error message.</span></span> <span data-ttu-id="fb4b0-111">預設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-111">The default is `False`.</span></span>  
  
 <span data-ttu-id="fb4b0-112">**TimeoutAfter**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-112">**TimeoutAfter**</span></span>  
 <span data-ttu-id="fb4b0-113">如果您選擇在工作失敗時要顯示錯誤訊息，請指定顯示逾時訊息之前要等候的秒數。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-113">If you choose to display an error message on task failure, specify the number of seconds to wait before displaying the time-out message.</span></span>  
  
 <span data-ttu-id="fb4b0-114">**MessageType**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-114">**MessageType**</span></span>  
 <span data-ttu-id="fb4b0-115">選取訊息類型。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-115">Select the message type.</span></span> <span data-ttu-id="fb4b0-116">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-116">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="fb4b0-117">值</span><span class="sxs-lookup"><span data-stu-id="fb4b0-117">Value</span></span>|<span data-ttu-id="fb4b0-118">描述</span><span class="sxs-lookup"><span data-stu-id="fb4b0-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb4b0-119">**資料檔訊息**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-119">**Data file message**</span></span>|<span data-ttu-id="fb4b0-120">訊息儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-120">The message is stored in a file.</span></span> <span data-ttu-id="fb4b0-121">選取此值會顯示動態選項 **[DataFileMessage]** 。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-121">Selecting the value displays the dynamic option, **DataFileMessage**.</span></span>|  
|<span data-ttu-id="fb4b0-122">**變數訊息**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-122">**Variable message**</span></span>|<span data-ttu-id="fb4b0-123">訊息儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-123">The message is stored in a variable.</span></span> <span data-ttu-id="fb4b0-124">選取此值會顯示動態選項 **[VariableMessage]** 。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-124">Selecting the value displays the dynamic option, **VariableMessage**.</span></span>|  
|<span data-ttu-id="fb4b0-125">**字串訊息**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-125">**String message**</span></span>|<span data-ttu-id="fb4b0-126">訊息儲存在訊息佇列工作中。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-126">The message is stored in the Message Queue task.</span></span> <span data-ttu-id="fb4b0-127">選取此值會顯示動態選項 **[StringMessage]** 。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-127">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
|<span data-ttu-id="fb4b0-128">**字串訊息至變數**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-128">**String message to variable**</span></span>|<span data-ttu-id="fb4b0-129">訊息</span><span class="sxs-lookup"><span data-stu-id="fb4b0-129">The message</span></span><br /><br /> <span data-ttu-id="fb4b0-130">選取此值會顯示動態選項 **[StringMessage]** 。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-130">Selecting the value displays the dynamic option, **StringMessage**.</span></span>|  
  
## <a name="messagetype-dynamic-options"></a><span data-ttu-id="fb4b0-131">MessageType 動態選項</span><span class="sxs-lookup"><span data-stu-id="fb4b0-131">MessageType Dynamic Options</span></span>  
  
### <a name="messagetype--data-file-message"></a><span data-ttu-id="fb4b0-132">MessageType = 資料檔訊息</span><span class="sxs-lookup"><span data-stu-id="fb4b0-132">MessageType = Data file message</span></span>  
 <span data-ttu-id="fb4b0-133">**SaveFileAs**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-133">**SaveFileAs**</span></span>  
 <span data-ttu-id="fb4b0-134">鍵入要使用的檔案路徑，或按一下省略符號按鈕 **(...)** ，然後尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-134">Type the path of the file to use, or click the ellipsis button **(...)** and then locate the file.</span></span>  
  
 <span data-ttu-id="fb4b0-135">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-135">**Overwrite**</span></span>  
 <span data-ttu-id="fb4b0-136">指出儲存資料檔訊息的內容時，是否要覆寫現有檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-136">Indicate whether to overwrite the data in an existing file when saving the contents of a data file message.</span></span> <span data-ttu-id="fb4b0-137">預設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-137">The default is `False`.</span></span>  
  
 <span data-ttu-id="fb4b0-138">**Filter**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-138">**Filter**</span></span>  
 <span data-ttu-id="fb4b0-139">指定是否要將篩選套用至訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-139">Specify whether to apply a filter to the message.</span></span> <span data-ttu-id="fb4b0-140">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-140">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="fb4b0-141">值</span><span class="sxs-lookup"><span data-stu-id="fb4b0-141">Value</span></span>|<span data-ttu-id="fb4b0-142">描述</span><span class="sxs-lookup"><span data-stu-id="fb4b0-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb4b0-143">**沒有篩選**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-143">**No filter**</span></span>|<span data-ttu-id="fb4b0-144">工作不會篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-144">The task does not filter messages.</span></span> <span data-ttu-id="fb4b0-145">選取此值會顯示動態選項 **IdentifierReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-145">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="fb4b0-146">**來自封裝**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-146">**From package**</span></span>|<span data-ttu-id="fb4b0-147">訊息只接收來自指定之封裝的訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-147">The message receives only messages from the specified package.</span></span> <span data-ttu-id="fb4b0-148">選取此值會顯示動態選項 **識別碼**＞。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-148">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="fb4b0-149">篩選動態選項</span><span class="sxs-lookup"><span data-stu-id="fb4b0-149">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="fb4b0-150">篩選 = 沒有篩選</span><span class="sxs-lookup"><span data-stu-id="fb4b0-150">Filter = No filter</span></span>  
 <span data-ttu-id="fb4b0-151">**IdentifierReadOnly**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-151">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="fb4b0-152">此選項是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-152">This option is read-only.</span></span> <span data-ttu-id="fb4b0-153">當先前有設定篩選屬性時，此選項可能是空白或包含封裝的 GUID。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-153">It may be blank or contain the GUID of a package when the Filter property was previously set.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="fb4b0-154">篩選 = 來自封裝</span><span class="sxs-lookup"><span data-stu-id="fb4b0-154">Filter = From package</span></span>  
 <span data-ttu-id="fb4b0-155">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-155">**Identifier**</span></span>  
 <span data-ttu-id="fb4b0-156">如果您選擇套用篩選，請鍵入訊息接收來源套件的唯一識別碼，或按一下省略符號按鈕 **(...)** ，然後指定套件。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-156">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="fb4b0-157">**相關主題：** [選取套件](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="fb4b0-157">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--variable-message"></a><span data-ttu-id="fb4b0-158">MessageType = 變數訊息</span><span class="sxs-lookup"><span data-stu-id="fb4b0-158">MessageType = Variable message</span></span>  
 <span data-ttu-id="fb4b0-159">**Filter**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-159">**Filter**</span></span>  
 <span data-ttu-id="fb4b0-160">指定是否要將篩選套用至訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-160">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="fb4b0-161">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-161">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="fb4b0-162">值</span><span class="sxs-lookup"><span data-stu-id="fb4b0-162">Value</span></span>|<span data-ttu-id="fb4b0-163">描述</span><span class="sxs-lookup"><span data-stu-id="fb4b0-163">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb4b0-164">**沒有篩選**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-164">**No filter**</span></span>|<span data-ttu-id="fb4b0-165">工作不會篩選訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-165">The task does not filter messages.</span></span> <span data-ttu-id="fb4b0-166">選取此值會顯示動態選項 **IdentifierReadOnly**。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-166">Selecting the value displays the dynamic option, **IdentifierReadOnly**.</span></span>|  
|<span data-ttu-id="fb4b0-167">**來自封裝**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-167">**From package**</span></span>|<span data-ttu-id="fb4b0-168">訊息只接收來自指定之封裝的訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-168">The message receives only messages from the specified package.</span></span> <span data-ttu-id="fb4b0-169">選取此值會顯示動態選項 **識別碼**＞。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-169">Selecting the value displays the dynamic option, **Identifier**.</span></span>|  
  
 <span data-ttu-id="fb4b0-170">**變數**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-170">**Variable**</span></span>  
 <span data-ttu-id="fb4b0-171">輸入變數名稱，或按一下 \<**New variable...**>，然後設定新的變數。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-171">Type the variable name, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="fb4b0-172">**相關主題：** [新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="fb4b0-172">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="filter-dynamic-options"></a><span data-ttu-id="fb4b0-173">篩選動態選項</span><span class="sxs-lookup"><span data-stu-id="fb4b0-173">Filter Dynamic Options</span></span>  
  
#### <a name="filter--no-filter"></a><span data-ttu-id="fb4b0-174">篩選 = 沒有篩選</span><span class="sxs-lookup"><span data-stu-id="fb4b0-174">Filter = No filter</span></span>  
 <span data-ttu-id="fb4b0-175">**IdentifierReadOnly**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-175">**IdentifierReadOnly**</span></span>  
 <span data-ttu-id="fb4b0-176">此選項是空白。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-176">This option is blank.</span></span>  
  
#### <a name="filter--from-package"></a><span data-ttu-id="fb4b0-177">篩選 = 來自封裝</span><span class="sxs-lookup"><span data-stu-id="fb4b0-177">Filter = From package</span></span>  
 <span data-ttu-id="fb4b0-178">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-178">**Identifier**</span></span>  
 <span data-ttu-id="fb4b0-179">如果您選擇套用篩選，請鍵入訊息接收來源套件的唯一識別碼，或按一下省略符號按鈕 **(...)** ，然後指定套件。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-179">If you choose to apply a filter, type the unique identifier of the package from which messages can be received, or click the ellipsis button **(...)** and then specify the package.</span></span>  
  
 <span data-ttu-id="fb4b0-180">**相關主題：** [選取套件](control-flow/select-a-package.md)</span><span class="sxs-lookup"><span data-stu-id="fb4b0-180">**Related Topics:** [Select a Package](control-flow/select-a-package.md)</span></span>  
  
### <a name="messagetype--string-message"></a><span data-ttu-id="fb4b0-181">MessageType = 字串訊息</span><span class="sxs-lookup"><span data-stu-id="fb4b0-181">MessageType = String message</span></span>  
 <span data-ttu-id="fb4b0-182">**比較**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-182">**Compare**</span></span>  
 <span data-ttu-id="fb4b0-183">指定是否要將篩選套用至訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-183">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="fb4b0-184">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-184">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="fb4b0-185">值</span><span class="sxs-lookup"><span data-stu-id="fb4b0-185">Value</span></span>|<span data-ttu-id="fb4b0-186">描述</span><span class="sxs-lookup"><span data-stu-id="fb4b0-186">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb4b0-187">**None**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-187">**None**</span></span>|<span data-ttu-id="fb4b0-188">不會比較訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-188">Messages are not compared.</span></span>|  
|<span data-ttu-id="fb4b0-189">**完全相符**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-189">**Exact match**</span></span>|<span data-ttu-id="fb4b0-190">訊息必須與 **CompareString** 選項中的字串完全相符。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-190">Messages must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="fb4b0-191">**忽略大小寫**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-191">**Ignore case**</span></span>|<span data-ttu-id="fb4b0-192">訊息必須與 **CompareString** 選項中的字串相符，但是比較時不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-192">Message must match the string in the **CompareString** option, but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="fb4b0-193">**包含**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-193">**Containing**</span></span>|<span data-ttu-id="fb4b0-194">訊息必須包含 **CompareString** 選項中的字串。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-194">Message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="fb4b0-195">**CompareString**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-195">**CompareString**</span></span>  
 <span data-ttu-id="fb4b0-196">除非 [比較]  選項設定為 [無]  ，否則請提供訊息要比較的字串。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-196">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
### <a name="messagetype--string-message-to-variable"></a><span data-ttu-id="fb4b0-197">MessageType = 字串訊息至變數</span><span class="sxs-lookup"><span data-stu-id="fb4b0-197">MessageType = String message to variable</span></span>  
 <span data-ttu-id="fb4b0-198">**比較**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-198">**Compare**</span></span>  
 <span data-ttu-id="fb4b0-199">指定是否要將篩選套用至訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-199">Specify whether to apply a filter to messages.</span></span> <span data-ttu-id="fb4b0-200">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-200">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="fb4b0-201">值</span><span class="sxs-lookup"><span data-stu-id="fb4b0-201">Value</span></span>|<span data-ttu-id="fb4b0-202">描述</span><span class="sxs-lookup"><span data-stu-id="fb4b0-202">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fb4b0-203">**None**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-203">**None**</span></span>|<span data-ttu-id="fb4b0-204">不會比較訊息。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-204">Messages are not compared.</span></span>|  
|<span data-ttu-id="fb4b0-205">**完全相符**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-205">**Exact match**</span></span>|<span data-ttu-id="fb4b0-206">訊息必須與 **CompareString** 選項中的字串完全相符。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-206">The message must match exactly the string in the **CompareString** option.</span></span>|  
|<span data-ttu-id="fb4b0-207">**忽略大小寫**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-207">**Ignore case**</span></span>|<span data-ttu-id="fb4b0-208">訊息必須與 **CompareString** 選項中的字串相符，但是比較時不會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-208">The message must match the string in the **CompareString** option but the comparison is not case sensitive.</span></span>|  
|<span data-ttu-id="fb4b0-209">**包含**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-209">**Containing**</span></span>|<span data-ttu-id="fb4b0-210">訊息必須包含 **CompareString** 選項中的字串。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-210">The message must contain the string in the **CompareString** option.</span></span>|  
  
 <span data-ttu-id="fb4b0-211">**CompareString**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-211">**CompareString**</span></span>  
 <span data-ttu-id="fb4b0-212">除非 [比較]  選項設定為 [無]  ，否則請提供訊息要比較的字串。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-212">Unless the **Compare** option is set to **None**, provide the string to which the message is compared.</span></span>  
  
 <span data-ttu-id="fb4b0-213">**變數**</span><span class="sxs-lookup"><span data-stu-id="fb4b0-213">**Variable**</span></span>  
 <span data-ttu-id="fb4b0-214">鍵入要保存已接收訊息的變數名稱，或按一下 \<**New variable...**>，然後設定新的變數。</span><span class="sxs-lookup"><span data-stu-id="fb4b0-214">Type the name of the variable to hold the received message, or click \<**New variable...**> and then configure a new variable.</span></span>  
  
 <span data-ttu-id="fb4b0-215">**相關主題：** [新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="fb4b0-215">**Related Topics:** [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4b0-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb4b0-216">See Also</span></span>  
 <span data-ttu-id="fb4b0-217">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fb4b0-217">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="fb4b0-218">[[訊息佇列工作編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="fb4b0-218">[Message Queue Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="fb4b0-219">[[訊息佇列工作編輯器] &#40;傳送頁面&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span><span class="sxs-lookup"><span data-stu-id="fb4b0-219">[Message Queue Task Editor &#40;Send Page&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md) </span></span>  
 <span data-ttu-id="fb4b0-220">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="fb4b0-220">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="fb4b0-221">訊息佇列工作</span><span class="sxs-lookup"><span data-stu-id="fb4b0-221">Message Queue Task</span></span>](control-flow/message-queue-task.md)  
  
  
