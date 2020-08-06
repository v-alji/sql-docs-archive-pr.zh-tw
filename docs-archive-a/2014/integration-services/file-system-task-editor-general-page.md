---
title: '[檔案系統工作編輯器] (一般頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e893f667c2a32fbc667c375dc57647d1aff1b806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708497"
---
# <a name="file-system-task-editor-general-page"></a><span data-ttu-id="8e228-102">檔案系統工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="8e228-102">File System Task Editor (General Page)</span></span>
  <span data-ttu-id="8e228-103">使用 [檔案系統工作編輯器]  對話方塊的 [一般]  頁面，即可設定工作執行的檔案系統作業。</span><span class="sxs-lookup"><span data-stu-id="8e228-103">Use the **General** page of the **File System Task Editor** dialog to configure the file system operation that the task performs.</span></span>  
  
 <span data-ttu-id="8e228-104">若要了解這項工作，請參閱 [檔案系統工作](control-flow/file-system-task.md)。</span><span class="sxs-lookup"><span data-stu-id="8e228-104">To learn about this task, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="8e228-105">您必須透過設定 SourceConnection 和 DestinationConnection 屬性，以指定來源和目的地連線管理員。</span><span class="sxs-lookup"><span data-stu-id="8e228-105">You must specify a source and destination connection manager by setting the SourceConnection and DestinationConnection properties.</span></span> <span data-ttu-id="8e228-106">您可以提供指向工作做為來源或目的地使用之檔案的檔案連接管理員名稱，而如果檔案路徑是儲存在變數中，則可以提供變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e228-106">You can either provide the names of File connection managers that point to the files that the task uses as a source or destination, or if the paths of the files are stored in variables, you can provide the names of the variables.</span></span> <span data-ttu-id="8e228-107">若要使用變數來儲存檔案路徑，您必須先將來源連接的 [IsSourcePathVariable] 選項和目的地連接的 [IsDestinationPatheVariable] 選項設定為 [True]  。</span><span class="sxs-lookup"><span data-stu-id="8e228-107">To use variables to store the file paths, you must set first set the IsSourcePathVariable option for the source connection and the IsDestinationPatheVariable option for the destination connection to **True**.</span></span> <span data-ttu-id="8e228-108">接著您就可以選擇要使用的現有系統或使用者自訂變數，或是建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="8e228-108">You can then choose the existing system or user-defined variables to use, or you can create new variables.</span></span> <span data-ttu-id="8e228-109">您可以在 [加入變數]  對話方塊中，設定和指定變數的範圍。</span><span class="sxs-lookup"><span data-stu-id="8e228-109">In the **Add Variable** dialog box, you can configure and specify the scope of the variables.</span></span> <span data-ttu-id="8e228-110">此範圍必須是「檔案系統」工作或父容器。</span><span class="sxs-lookup"><span data-stu-id="8e228-110">The scope must be the File System task or a parent container.</span></span> <span data-ttu-id="8e228-111">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)和[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="8e228-111">For more information see, [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e228-112">若要覆寫您為和屬性選取的變數 `SourceConnection` `DestinationConnection` ，請在 [**來源**] 和 [**目的地**] 屬性中輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="8e228-112">To override the variables you selected for the `SourceConnection` and `DestinationConnection` properties, enter an expression for the **Source** and **Destination** properties.</span></span> <span data-ttu-id="8e228-113">您可在 [檔案系統工作編輯器]  的 [運算式]  頁面上輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="8e228-113">You enter expressions on the **Expressions** page of the **File System Task Editor**.</span></span> <span data-ttu-id="8e228-114">例如，為了設定做為工作目的地使用的檔案路徑，在某些情況下您可能想要使用變數 A，而在其他情況下使用變數 B。</span><span class="sxs-lookup"><span data-stu-id="8e228-114">For example, to set the path of the files that the task uses as a destination, you may want to use variable A under certain conditions and use variable B under other conditions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e228-115">「檔案系統」工作會在單一檔案或目錄上運作。</span><span class="sxs-lookup"><span data-stu-id="8e228-115">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="8e228-116">因此，這項工作不支援使用萬用字元在多個檔案或目錄上執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="8e228-116">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files or directories.</span></span> <span data-ttu-id="8e228-117">為了要讓「檔案系統」工作在多個檔案或目錄上重複作業，請將此「檔案系統」工作放入 Foreach 迴圈容器內。</span><span class="sxs-lookup"><span data-stu-id="8e228-117">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container.</span></span> <span data-ttu-id="8e228-118">如需詳細資訊，請參閱 [檔案系統工作](control-flow/file-system-task.md)。</span><span class="sxs-lookup"><span data-stu-id="8e228-118">For more information, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="8e228-119">您可以使用運算式，將不同的變數用於</span><span class="sxs-lookup"><span data-stu-id="8e228-119">You can use expressions to use different variables for the</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e228-120">選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-120">Options</span></span>  
 <span data-ttu-id="8e228-121">**IsDestinationPathVariable**</span><span class="sxs-lookup"><span data-stu-id="8e228-121">**IsDestinationPathVariable**</span></span>  
 <span data-ttu-id="8e228-122">指出目的地路徑是否儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="8e228-122">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="8e228-123">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-123">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="8e228-124">值</span><span class="sxs-lookup"><span data-stu-id="8e228-124">Value</span></span>|<span data-ttu-id="8e228-125">描述</span><span class="sxs-lookup"><span data-stu-id="8e228-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e228-126">**True**</span><span class="sxs-lookup"><span data-stu-id="8e228-126">**True**</span></span>|<span data-ttu-id="8e228-127">目的地路徑儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="8e228-127">The destination path is stored in a variable.</span></span> <span data-ttu-id="8e228-128">選取這個值會顯示動態選項 [DestinationVariable]  。</span><span class="sxs-lookup"><span data-stu-id="8e228-128">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
|<span data-ttu-id="8e228-129">**False**</span><span class="sxs-lookup"><span data-stu-id="8e228-129">**False**</span></span>|<span data-ttu-id="8e228-130">目的地路徑是在檔案連接管理員中指定。</span><span class="sxs-lookup"><span data-stu-id="8e228-130">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="8e228-131">選取此值會顯示動態選項： `DestinationConnection` 。</span><span class="sxs-lookup"><span data-stu-id="8e228-131">Selecting this value displays the dynamic option, `DestinationConnection`.</span></span>|  
  
 <span data-ttu-id="8e228-132">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="8e228-132">**OverwriteDestination**</span></span>  
 <span data-ttu-id="8e228-133">指定作業是否可覆寫目的地目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="8e228-133">Specify whether the operation can overwrite files in the destination directory.</span></span>  
  
 <span data-ttu-id="8e228-134">**名稱**</span><span class="sxs-lookup"><span data-stu-id="8e228-134">**Name**</span></span>  
 <span data-ttu-id="8e228-135">為檔案系統工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e228-135">Provide a unique name for the File System task.</span></span> <span data-ttu-id="8e228-136">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="8e228-136">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e228-137">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8e228-137">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="8e228-138">**說明**</span><span class="sxs-lookup"><span data-stu-id="8e228-138">**Description**</span></span>  
 <span data-ttu-id="8e228-139">輸入檔案系統工作的描述。</span><span class="sxs-lookup"><span data-stu-id="8e228-139">Type a description of the File System task.</span></span>  
  
 <span data-ttu-id="8e228-140">**運算**</span><span class="sxs-lookup"><span data-stu-id="8e228-140">**Operation**</span></span>  
 <span data-ttu-id="8e228-141">選取要執行的檔案系統作業。</span><span class="sxs-lookup"><span data-stu-id="8e228-141">Select the file-system operation to perform.</span></span> <span data-ttu-id="8e228-142">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-142">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="8e228-143">值</span><span class="sxs-lookup"><span data-stu-id="8e228-143">Value</span></span>|<span data-ttu-id="8e228-144">描述</span><span class="sxs-lookup"><span data-stu-id="8e228-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e228-145">**複製目錄**</span><span class="sxs-lookup"><span data-stu-id="8e228-145">**Copy directory**</span></span>|<span data-ttu-id="8e228-146">複製目錄。</span><span class="sxs-lookup"><span data-stu-id="8e228-146">Copy a directory.</span></span> <span data-ttu-id="8e228-147">選取此值會顯示來源與目的地的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-147">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="8e228-148">**複製檔案**</span><span class="sxs-lookup"><span data-stu-id="8e228-148">**Copy file**</span></span>|<span data-ttu-id="8e228-149">複製檔案。</span><span class="sxs-lookup"><span data-stu-id="8e228-149">Copy a file.</span></span> <span data-ttu-id="8e228-150">選取此值會顯示來源與目的地的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-150">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="8e228-151">**建立目錄**</span><span class="sxs-lookup"><span data-stu-id="8e228-151">**Create directory**</span></span>|<span data-ttu-id="8e228-152">建立目錄。</span><span class="sxs-lookup"><span data-stu-id="8e228-152">Create a directory.</span></span> <span data-ttu-id="8e228-153">選取此值會顯示來源和目的地目錄的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-153">Selecting this value displays the dynamic options for a source and a destination directory.</span></span>|  
|<span data-ttu-id="8e228-154">**刪除目錄**</span><span class="sxs-lookup"><span data-stu-id="8e228-154">**Delete directory**</span></span>|<span data-ttu-id="8e228-155">刪除目錄。</span><span class="sxs-lookup"><span data-stu-id="8e228-155">Delete a directory.</span></span> <span data-ttu-id="8e228-156">選取此值會顯示來源的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-156">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="8e228-157">**刪除目錄內容**</span><span class="sxs-lookup"><span data-stu-id="8e228-157">**Delete directory content**</span></span>|<span data-ttu-id="8e228-158">刪除目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="8e228-158">Delete the content of a directory.</span></span> <span data-ttu-id="8e228-159">選取此值會顯示來源的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-159">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="8e228-160">**刪除檔案**</span><span class="sxs-lookup"><span data-stu-id="8e228-160">**Delete file**</span></span>|<span data-ttu-id="8e228-161">刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="8e228-161">Delete a file.</span></span> <span data-ttu-id="8e228-162">選取此值會顯示來源的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-162">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="8e228-163">**移動目錄**</span><span class="sxs-lookup"><span data-stu-id="8e228-163">**Move directory**</span></span>|<span data-ttu-id="8e228-164">移動目錄。</span><span class="sxs-lookup"><span data-stu-id="8e228-164">Move a directory.</span></span> <span data-ttu-id="8e228-165">選取此值會顯示來源與目的地的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-165">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="8e228-166">**移動檔案**</span><span class="sxs-lookup"><span data-stu-id="8e228-166">**Move file**</span></span>|<span data-ttu-id="8e228-167">移動檔案。</span><span class="sxs-lookup"><span data-stu-id="8e228-167">Move a file.</span></span> <span data-ttu-id="8e228-168">選取此值會顯示來源與目的地的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-168">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="8e228-169">注意：移動檔案時，請勿在您提供作為目的地的目錄路徑中包含檔案名。</span><span class="sxs-lookup"><span data-stu-id="8e228-169">Note: When moving a file, do not include a file name in the directory path that you provide as the destination.</span></span>|  
|<span data-ttu-id="8e228-170">**重新命名檔案**</span><span class="sxs-lookup"><span data-stu-id="8e228-170">**Rename file**</span></span>|<span data-ttu-id="8e228-171">重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="8e228-171">Rename a file.</span></span> <span data-ttu-id="8e228-172">選取此值會顯示來源與目的地的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-172">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="8e228-173">注意：重新命名檔案時，請在您提供給目的地的目錄路徑中包含新的檔案名。</span><span class="sxs-lookup"><span data-stu-id="8e228-173">Note: When renaming a file, include the new file name in the directory path that you provide for the destination.</span></span>|  
|<span data-ttu-id="8e228-174">**設定屬性**</span><span class="sxs-lookup"><span data-stu-id="8e228-174">**Set attributes**</span></span>|<span data-ttu-id="8e228-175">設定檔案或目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="8e228-175">Set the attributes of a file or directory.</span></span> <span data-ttu-id="8e228-176">選取此值會顯示來源與作業的動態選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-176">Selecting this value displays the dynamic options for a source and operation.</span></span>|  
  
 `IsSourcePathVariable`  
 <span data-ttu-id="8e228-177">指出目的地路徑是否儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="8e228-177">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="8e228-178">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="8e228-178">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="8e228-179">值</span><span class="sxs-lookup"><span data-stu-id="8e228-179">Value</span></span>||  
|-----------|-|  
|<span data-ttu-id="8e228-180">**True**</span><span class="sxs-lookup"><span data-stu-id="8e228-180">**True**</span></span>|<span data-ttu-id="8e228-181">目的地路徑儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="8e228-181">The destination path is stored in a variable.</span></span> <span data-ttu-id="8e228-182">選取此值會顯示動態選項 [SourceVariable]  。</span><span class="sxs-lookup"><span data-stu-id="8e228-182">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
|<span data-ttu-id="8e228-183">**False**</span><span class="sxs-lookup"><span data-stu-id="8e228-183">**False**</span></span>|<span data-ttu-id="8e228-184">目的地路徑是在檔案連接管理員中指定。</span><span class="sxs-lookup"><span data-stu-id="8e228-184">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="8e228-185">選取這個值會顯示動態選項 [DestinationVariable]  。</span><span class="sxs-lookup"><span data-stu-id="8e228-185">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a><span data-ttu-id="8e228-186">IsDestinationPathVariable 動態選項</span><span class="sxs-lookup"><span data-stu-id="8e228-186">IsDestinationPathVariable Dynamic Options</span></span>  
  
### <a name="isdestinationpathvariable--true"></a><span data-ttu-id="8e228-187">IsDestinationPathVariable = True</span><span class="sxs-lookup"><span data-stu-id="8e228-187">IsDestinationPathVariable = True</span></span>  
 <span data-ttu-id="8e228-188">**DestinationVariable**</span><span class="sxs-lookup"><span data-stu-id="8e228-188">**DestinationVariable**</span></span>  
 <span data-ttu-id="8e228-189">選取清單中的變數名稱，或按一下 \<**New variable...**> 建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="8e228-189">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="8e228-190">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="8e228-190">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="isdestinationpathvariable--false"></a><span data-ttu-id="8e228-191">IsDestinationPathVariable = False</span><span class="sxs-lookup"><span data-stu-id="8e228-191">IsDestinationPathVariable = False</span></span>  
 `DestinationConnection`  
 <span data-ttu-id="8e228-192">在清單中選取檔案連線管理員，或按一下 \<**New connection...**> 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="8e228-192">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="8e228-193">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="8e228-193">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="issourcepathvariable-dynamic-options"></a><span data-ttu-id="8e228-194">IsSourcePathVariable 動態選項</span><span class="sxs-lookup"><span data-stu-id="8e228-194">IsSourcePathVariable Dynamic Options</span></span>  
  
### <a name="issourcepathvariable--true"></a><span data-ttu-id="8e228-195">IsSourcePathVariable = True</span><span class="sxs-lookup"><span data-stu-id="8e228-195">IsSourcePathVariable = True</span></span>  
 <span data-ttu-id="8e228-196">**SourceVariable**</span><span class="sxs-lookup"><span data-stu-id="8e228-196">**SourceVariable**</span></span>  
 <span data-ttu-id="8e228-197">選取清單中的變數名稱，或按一下 \<**New variable...**> 建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="8e228-197">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="8e228-198">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="8e228-198">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="issourcepathvariable--false"></a><span data-ttu-id="8e228-199">IsSourcePathVariable = False</span><span class="sxs-lookup"><span data-stu-id="8e228-199">IsSourcePathVariable = False</span></span>  
 `SourceConnection`  
 <span data-ttu-id="8e228-200">在清單中選取檔案連線管理員，或按一下 \<**New connection...**> 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="8e228-200">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="8e228-201">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="8e228-201">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="operation-dynamic-options"></a><span data-ttu-id="8e228-202">作業動態選項</span><span class="sxs-lookup"><span data-stu-id="8e228-202">Operation Dynamic Options</span></span>  
  
### <a name="operation--set-attributes"></a><span data-ttu-id="8e228-203">作業 = 設定屬性</span><span class="sxs-lookup"><span data-stu-id="8e228-203">Operation = Set Attributes</span></span>  
 <span data-ttu-id="8e228-204">**Hidden**</span><span class="sxs-lookup"><span data-stu-id="8e228-204">**Hidden**</span></span>  
 <span data-ttu-id="8e228-205">指出檔案或目錄是否可見。</span><span class="sxs-lookup"><span data-stu-id="8e228-205">Indicate whether the file or directory is visible.</span></span>  
  
 <span data-ttu-id="8e228-206">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="8e228-206">**ReadOnly**</span></span>  
 <span data-ttu-id="8e228-207">指出檔案是否為唯讀。</span><span class="sxs-lookup"><span data-stu-id="8e228-207">Indicate whether the file is read-only.</span></span>  
  
 <span data-ttu-id="8e228-208">**封存**</span><span class="sxs-lookup"><span data-stu-id="8e228-208">**Archive**</span></span>  
 <span data-ttu-id="8e228-209">指出檔案或目錄是否準備就緒，可供封存。</span><span class="sxs-lookup"><span data-stu-id="8e228-209">Indicate whether the file or directory is ready for archiving.</span></span>  
  
 <span data-ttu-id="8e228-210">**系統**</span><span class="sxs-lookup"><span data-stu-id="8e228-210">**System**</span></span>  
 <span data-ttu-id="8e228-211">指出檔案是否為作業系統檔案。</span><span class="sxs-lookup"><span data-stu-id="8e228-211">Indicate whether the file is an operating system file.</span></span>  
  
### <a name="operation--create-directory"></a><span data-ttu-id="8e228-212">作業 = 建立目錄</span><span class="sxs-lookup"><span data-stu-id="8e228-212">Operation = Create directory</span></span>  
 `UseDirectoryIfExists`  
 <span data-ttu-id="8e228-213">指出 [建立目錄]  作業是否會使用具有指定之名稱的現有目錄，而不是建立新的目錄。</span><span class="sxs-lookup"><span data-stu-id="8e228-213">Indicates whether the **Create directory** operation uses an existing directory with the specified name instead of creating a new directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e228-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e228-214">See Also</span></span>  
 <span data-ttu-id="8e228-215">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8e228-215">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="8e228-216">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="8e228-216">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
