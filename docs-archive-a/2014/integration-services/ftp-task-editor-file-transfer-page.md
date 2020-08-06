---
title: FTP 工作編輯器 (檔案傳輸頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8094051e93c4165be6ae186bde394f9271d60669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593448"
---
# <a name="ftp-task-editor-file-transfer-page"></a><span data-ttu-id="e29e5-102">FTP 工作編輯器 (檔案傳輸頁面)</span><span class="sxs-lookup"><span data-stu-id="e29e5-102">FTP Task Editor (File Transfer Page)</span></span>
  <span data-ttu-id="e29e5-103">使用 **[FTP 工作編輯器]** 對話方塊的 **[檔案傳輸]** 頁面，來設定工作執行的 FTP 作業。</span><span class="sxs-lookup"><span data-stu-id="e29e5-103">Use the **File Transfer** page of the **FTP Task Editor** dialog box to configure the FTP operation that the task performs.</span></span>  
  
 <span data-ttu-id="e29e5-104">若要深入了解此工作，請參閱 [FTP 工作](control-flow/ftp-task.md)。</span><span class="sxs-lookup"><span data-stu-id="e29e5-104">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e29e5-105">選項。</span><span class="sxs-lookup"><span data-stu-id="e29e5-105">Options</span></span>  
 <span data-ttu-id="e29e5-106">**IsRemotePathVariable**</span><span class="sxs-lookup"><span data-stu-id="e29e5-106">**IsRemotePathVariable**</span></span>  
 <span data-ttu-id="e29e5-107">指出遠端路徑是否儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="e29e5-107">Indicate whether the remote path is stored in a variable.</span></span> <span data-ttu-id="e29e5-108">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="e29e5-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e29e5-109">值</span><span class="sxs-lookup"><span data-stu-id="e29e5-109">Value</span></span>|<span data-ttu-id="e29e5-110">描述</span><span class="sxs-lookup"><span data-stu-id="e29e5-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e29e5-111">**True**</span><span class="sxs-lookup"><span data-stu-id="e29e5-111">**True**</span></span>|<span data-ttu-id="e29e5-112">目的地路徑儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="e29e5-112">The destination path is stored in a variable.</span></span> <span data-ttu-id="e29e5-113">選取此值會顯示動態選項 **[RemoteVariable]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-113">Selecting the value displays the dynamic option, **RemoteVariable**.</span></span>|  
|<span data-ttu-id="e29e5-114">**False**</span><span class="sxs-lookup"><span data-stu-id="e29e5-114">**False**</span></span>|<span data-ttu-id="e29e5-115">目的地路徑是在檔案連接管理員中指定。</span><span class="sxs-lookup"><span data-stu-id="e29e5-115">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="e29e5-116">選取此值會顯示動態選項 **[RemotePath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-116">Selecting the value displays the dynamic option, **RemotePath**.</span></span>|  
  
 <span data-ttu-id="e29e5-117">**OverwriteFileAtDestination**</span><span class="sxs-lookup"><span data-stu-id="e29e5-117">**OverwriteFileAtDestination**</span></span>  
 <span data-ttu-id="e29e5-118">指定是否可以覆寫目的地端的檔案。</span><span class="sxs-lookup"><span data-stu-id="e29e5-118">Specify whether a file at the destination can be overwritten.</span></span>  
  
 <span data-ttu-id="e29e5-119">**IsLocalPathVariable**</span><span class="sxs-lookup"><span data-stu-id="e29e5-119">**IsLocalPathVariable**</span></span>  
 <span data-ttu-id="e29e5-120">指出本機路徑是否儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="e29e5-120">Indicate whether the local path is stored in a variable.</span></span> <span data-ttu-id="e29e5-121">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="e29e5-121">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e29e5-122">值</span><span class="sxs-lookup"><span data-stu-id="e29e5-122">Value</span></span>|<span data-ttu-id="e29e5-123">描述</span><span class="sxs-lookup"><span data-stu-id="e29e5-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e29e5-124">**True**</span><span class="sxs-lookup"><span data-stu-id="e29e5-124">**True**</span></span>|<span data-ttu-id="e29e5-125">目的地路徑儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="e29e5-125">The destination path is stored in a variable.</span></span> <span data-ttu-id="e29e5-126">選取此值會顯示動態選項 **[LocalVariable]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-126">Selecting the value displays the dynamic option, **LocalVariable**.</span></span>|  
|<span data-ttu-id="e29e5-127">**False**</span><span class="sxs-lookup"><span data-stu-id="e29e5-127">**False**</span></span>|<span data-ttu-id="e29e5-128">目的地路徑是在檔案連接管理員中指定。</span><span class="sxs-lookup"><span data-stu-id="e29e5-128">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="e29e5-129">選取此值會顯示動態選項 **[LocalPath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-129">Selecting the value displays the dynamic option, **LocalPath**.</span></span>|  
  
 <span data-ttu-id="e29e5-130">**運算**</span><span class="sxs-lookup"><span data-stu-id="e29e5-130">**Operation**</span></span>  
 <span data-ttu-id="e29e5-131">選取要執行的 FTP 作業。</span><span class="sxs-lookup"><span data-stu-id="e29e5-131">Select the FTP operation to perform.</span></span> <span data-ttu-id="e29e5-132">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="e29e5-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="e29e5-133">值</span><span class="sxs-lookup"><span data-stu-id="e29e5-133">Value</span></span>|<span data-ttu-id="e29e5-134">描述</span><span class="sxs-lookup"><span data-stu-id="e29e5-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e29e5-135">**傳送檔案**</span><span class="sxs-lookup"><span data-stu-id="e29e5-135">**Send files**</span></span>|<span data-ttu-id="e29e5-136">傳送檔案。</span><span class="sxs-lookup"><span data-stu-id="e29e5-136">Send files.</span></span> <span data-ttu-id="e29e5-137">選取此值會顯示動態選項 **LocalVariable**、 **LocalPathRemoteVariable** 和 **RemotePath**。</span><span class="sxs-lookup"><span data-stu-id="e29e5-137">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="e29e5-138">**接收檔案**</span><span class="sxs-lookup"><span data-stu-id="e29e5-138">**Receive files**</span></span>|<span data-ttu-id="e29e5-139">接收檔案。</span><span class="sxs-lookup"><span data-stu-id="e29e5-139">Receive files.</span></span> <span data-ttu-id="e29e5-140">選取此值會顯示動態選項 **LocalVariable**、 **LocalPathRemoteVariable** 和 **RemotePath**。</span><span class="sxs-lookup"><span data-stu-id="e29e5-140">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="e29e5-141">**建立本機目錄**</span><span class="sxs-lookup"><span data-stu-id="e29e5-141">**Create local directory**</span></span>|<span data-ttu-id="e29e5-142">建立本機目錄。</span><span class="sxs-lookup"><span data-stu-id="e29e5-142">Create a local directory.</span></span> <span data-ttu-id="e29e5-143">選取此值會顯示動態選項 **[LocalVariable]** 和 **[LocalPath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-143">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="e29e5-144">**建立遠端目錄**</span><span class="sxs-lookup"><span data-stu-id="e29e5-144">**Create remote directory**</span></span>|<span data-ttu-id="e29e5-145">建立遠端目錄。</span><span class="sxs-lookup"><span data-stu-id="e29e5-145">Create a remote directory.</span></span> <span data-ttu-id="e29e5-146">選取此值會顯示動態選項 **[RemoteVariable]** 和 **[RemotelPath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-146">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotelPath**.</span></span>|  
|<span data-ttu-id="e29e5-147">**移除本機目錄**</span><span class="sxs-lookup"><span data-stu-id="e29e5-147">**Remove local directory**</span></span>|<span data-ttu-id="e29e5-148">移除本機目錄。</span><span class="sxs-lookup"><span data-stu-id="e29e5-148">Removes a local directory.</span></span> <span data-ttu-id="e29e5-149">選取此值會顯示動態選項 **[LocalVariable]** 和 **[LocalPath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-149">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="e29e5-150">**移除遠端目錄**</span><span class="sxs-lookup"><span data-stu-id="e29e5-150">**Remove remote directory**</span></span>|<span data-ttu-id="e29e5-151">移除遠端目錄。</span><span class="sxs-lookup"><span data-stu-id="e29e5-151">Remove a remote directory.</span></span> <span data-ttu-id="e29e5-152">選取此值會顯示動態選項 **[RemoteVariable]** 和 **[RemotePath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-152">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="e29e5-153">**刪除本機檔案**</span><span class="sxs-lookup"><span data-stu-id="e29e5-153">**Delete local files**</span></span>|<span data-ttu-id="e29e5-154">刪除本機檔案。</span><span class="sxs-lookup"><span data-stu-id="e29e5-154">Delete local files.</span></span> <span data-ttu-id="e29e5-155">選取此值會顯示動態選項 **[LocalVariable]** 和 **[LocalPath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-155">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="e29e5-156">**刪除遠端檔案**</span><span class="sxs-lookup"><span data-stu-id="e29e5-156">**Delete remote files**</span></span>|<span data-ttu-id="e29e5-157">刪除遠端檔案。</span><span class="sxs-lookup"><span data-stu-id="e29e5-157">Delete remote files.</span></span> <span data-ttu-id="e29e5-158">選取此值會顯示動態選項 **[RemoteVariable]** 和 **[RemotePath]** 。</span><span class="sxs-lookup"><span data-stu-id="e29e5-158">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
  
 <span data-ttu-id="e29e5-159">**IsTransferASCII**</span><span class="sxs-lookup"><span data-stu-id="e29e5-159">**IsTransferASCII**</span></span>  
 <span data-ttu-id="e29e5-160">指出往返遠端 FTP 伺服器的檔案，是否應以 ASCII 模式傳輸。</span><span class="sxs-lookup"><span data-stu-id="e29e5-160">Indicate whether files transferred to and from the remote FTP server should be transferred in ASCII mode.</span></span>  
  
## <a name="isremotepathvariable-dynamic-options"></a><span data-ttu-id="e29e5-161">IsRemotePathVariable 動態選項</span><span class="sxs-lookup"><span data-stu-id="e29e5-161">IsRemotePathVariable Dynamic Options</span></span>  
  
### <a name="isremotepathvariable--true"></a><span data-ttu-id="e29e5-162">IsRemotePathVariable = True</span><span class="sxs-lookup"><span data-stu-id="e29e5-162">IsRemotePathVariable = True</span></span>  
 <span data-ttu-id="e29e5-163">**[RemoteVariable]**</span><span class="sxs-lookup"><span data-stu-id="e29e5-163">**RemoteVariable**</span></span>  
 <span data-ttu-id="e29e5-164">選取現有的使用者定義變數，或按一下 \<**New variable...**> 來建立使用者定義變數。</span><span class="sxs-lookup"><span data-stu-id="e29e5-164">Select an existing user-defined variable, or click \<**New variable...**> to create a user-defined variable.</span></span>  
  
 <span data-ttu-id="e29e5-165">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、新增變數</span><span class="sxs-lookup"><span data-stu-id="e29e5-165">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="isremotepathvariable--false"></a><span data-ttu-id="e29e5-166">IsRemotePathVariable = False</span><span class="sxs-lookup"><span data-stu-id="e29e5-166">IsRemotePathVariable = False</span></span>  
 <span data-ttu-id="e29e5-167">**[RemotePath]**</span><span class="sxs-lookup"><span data-stu-id="e29e5-167">**RemotePath**</span></span>  
 <span data-ttu-id="e29e5-168">選取現有的 FTP 連線管理員，或按一下 \<**New connection...**> 來建立連線管理員。</span><span class="sxs-lookup"><span data-stu-id="e29e5-168">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="e29e5-169">**相關主題：** [FTP 連線管理員](connection-manager/ftp-connection-manager.md)、[FTP 連線管理員編輯器](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e29e5-169">**Related Topics:** [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
## <a name="islocalpathvariable-dynamic-options"></a><span data-ttu-id="e29e5-170">IsLocalPathVariable 動態選項</span><span class="sxs-lookup"><span data-stu-id="e29e5-170">IsLocalPathVariable Dynamic Options</span></span>  
  
### <a name="islocalpathvariable--true"></a><span data-ttu-id="e29e5-171">IsLocalPathVariable = True</span><span class="sxs-lookup"><span data-stu-id="e29e5-171">IsLocalPathVariable = True</span></span>  
 <span data-ttu-id="e29e5-172">**[LocalVariable]**</span><span class="sxs-lookup"><span data-stu-id="e29e5-172">**LocalVariable**</span></span>  
 <span data-ttu-id="e29e5-173">選取現有的使用者定義變數，或按一下 \<**New variable...**> 來建立變數。</span><span class="sxs-lookup"><span data-stu-id="e29e5-173">Select an existing user-defined variable, or click \<**New variable...**> to create a variable.</span></span>  
  
 <span data-ttu-id="e29e5-174">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、新增變數</span><span class="sxs-lookup"><span data-stu-id="e29e5-174">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="islocalpathvariable--false"></a><span data-ttu-id="e29e5-175">IsLocalPathVariable = False</span><span class="sxs-lookup"><span data-stu-id="e29e5-175">IsLocalPathVariable = False</span></span>  
 <span data-ttu-id="e29e5-176">**[LocalPath]**</span><span class="sxs-lookup"><span data-stu-id="e29e5-176">**LocalPath**</span></span>  
 <span data-ttu-id="e29e5-177">選取現有的檔案連線管理員，或按一下 \<**New connection...**> 來建立連線管理員。</span><span class="sxs-lookup"><span data-stu-id="e29e5-177">Select an existing File connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="e29e5-178">**相關主題**： [一般檔案連線管理員](connection-manager/file-connection-manager.md)、 [檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="e29e5-178">**Related Topics**: [Flat File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e29e5-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e29e5-179">See Also</span></span>  
 <span data-ttu-id="e29e5-180">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e29e5-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="e29e5-181">[FTP 工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="e29e5-181">[FTP Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="e29e5-182">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="e29e5-182">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
