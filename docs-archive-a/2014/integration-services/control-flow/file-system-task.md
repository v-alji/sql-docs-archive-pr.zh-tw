---
title: 檔案系統工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.f1
helpviewer_keywords:
- File System task [Integration Services]
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ce3d31ceb720704fb61c33043a4c7319607caff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584693"
---
# <a name="file-system-task"></a><span data-ttu-id="28bce-102">檔案系統工作</span><span class="sxs-lookup"><span data-stu-id="28bce-102">File System Task</span></span>
  <span data-ttu-id="28bce-103">「檔案系統」工作會在檔案系統中的檔案和目錄上執行作業。</span><span class="sxs-lookup"><span data-stu-id="28bce-103">The File System task performs operations on files and directories in the file system.</span></span> <span data-ttu-id="28bce-104">例如，封裝可使用「檔案系統」工作建立、移動或刪除目錄和檔案。</span><span class="sxs-lookup"><span data-stu-id="28bce-104">For example, by using the File System task, a package can create, move, or delete directories and files.</span></span> <span data-ttu-id="28bce-105">您也可以使用「檔案系統」工作設定檔案和目錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="28bce-105">You can also use the File System task to set attributes on files and directories.</span></span> <span data-ttu-id="28bce-106">例如，「檔案系統」工作可將檔案設為隱藏或唯讀。</span><span class="sxs-lookup"><span data-stu-id="28bce-106">For example, the File System task can make files hidden or read-only.</span></span>  
  
 <span data-ttu-id="28bce-107">所有「檔案系統」工作作業均使用來源，其可為檔案或目錄。</span><span class="sxs-lookup"><span data-stu-id="28bce-107">All File System task operations use a source, which can be a file or a directory.</span></span> <span data-ttu-id="28bce-108">例如，工作所複製的檔案或刪除的目錄即為來源。</span><span class="sxs-lookup"><span data-stu-id="28bce-108">For example, the file that the task copies or the directory it deletes is a source.</span></span> <span data-ttu-id="28bce-109">來源可使用指向目錄或檔案的「檔案」連接管理員指定，或藉由提供包含來源路徑的變數名稱指定。</span><span class="sxs-lookup"><span data-stu-id="28bce-109">The source can be specified by using a File connection manager that points to the directory or file or by providing the name of a variable that contains the source path.</span></span> <span data-ttu-id="28bce-110">如需詳細資訊，請參閱[檔案連線管理員](../connection-manager/file-connection-manager.md)和 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="28bce-110">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="28bce-111">複製和移動檔案與目錄以及重新命名檔案的作業會使用目的地和來源。</span><span class="sxs-lookup"><span data-stu-id="28bce-111">The operations that copy and move file and directories and rename files use a destination and a source.</span></span> <span data-ttu-id="28bce-112">目的地是使用「檔案」連接管理員或變數指定。</span><span class="sxs-lookup"><span data-stu-id="28bce-112">The destination is specified by using a File connection manager or a variable.</span></span> <span data-ttu-id="28bce-113">檔案系統工作的作業可設定為允許覆寫目的地檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="28bce-113">File system task operations can be configured to permit overwriting of destination files and directories.</span></span> <span data-ttu-id="28bce-114">建立新目錄的作業可設定為當目錄已存在時使用具有指定名稱的現有目錄，而不會失敗。</span><span class="sxs-lookup"><span data-stu-id="28bce-114">The operation that creates a new directory can be configured to use an existing directory that has the specified name instead of failing when the directory already exists.</span></span>  
  
## <a name="predefined-file-system-operations"></a><span data-ttu-id="28bce-115">預先定義的檔案系統作業</span><span class="sxs-lookup"><span data-stu-id="28bce-115">Predefined File System Operations</span></span>  
 <span data-ttu-id="28bce-116">「檔案系統」工作包括一組預先定義的作業。</span><span class="sxs-lookup"><span data-stu-id="28bce-116">The File System task includes a predefined set of operations.</span></span> <span data-ttu-id="28bce-117">下表描述這些作業。</span><span class="sxs-lookup"><span data-stu-id="28bce-117">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="28bce-118">作業</span><span class="sxs-lookup"><span data-stu-id="28bce-118">Operation</span></span>|<span data-ttu-id="28bce-119">描述</span><span class="sxs-lookup"><span data-stu-id="28bce-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28bce-120">複製目錄</span><span class="sxs-lookup"><span data-stu-id="28bce-120">Copy directory</span></span>|<span data-ttu-id="28bce-121">將資料夾從一個位置複製到另一個。</span><span class="sxs-lookup"><span data-stu-id="28bce-121">Copies a folder from one location to another.</span></span>|  
|<span data-ttu-id="28bce-122">複製檔案</span><span class="sxs-lookup"><span data-stu-id="28bce-122">Copy file</span></span>|<span data-ttu-id="28bce-123">將檔案從一個位置複製到另一個。</span><span class="sxs-lookup"><span data-stu-id="28bce-123">Copies a file from one location to another.</span></span>|  
|<span data-ttu-id="28bce-124">建立目錄</span><span class="sxs-lookup"><span data-stu-id="28bce-124">Create directory</span></span>|<span data-ttu-id="28bce-125">在指定的位置建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="28bce-125">Creates a folder in a specified location.</span></span>|  
|<span data-ttu-id="28bce-126">刪除目錄</span><span class="sxs-lookup"><span data-stu-id="28bce-126">Delete directory</span></span>|<span data-ttu-id="28bce-127">刪除指定位置的資料夾。</span><span class="sxs-lookup"><span data-stu-id="28bce-127">Deletes a folder in a specified location.</span></span>|  
|<span data-ttu-id="28bce-128">刪除目錄內容</span><span class="sxs-lookup"><span data-stu-id="28bce-128">Delete directory content</span></span>|<span data-ttu-id="28bce-129">刪除某個資料夾中的所有檔案和資料夾。</span><span class="sxs-lookup"><span data-stu-id="28bce-129">Deletes all files and folders in a folder.</span></span>|  
|<span data-ttu-id="28bce-130">刪除檔案</span><span class="sxs-lookup"><span data-stu-id="28bce-130">Delete file</span></span>|<span data-ttu-id="28bce-131">刪除指定位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="28bce-131">Deletes a file in a specified location.</span></span>|  
|<span data-ttu-id="28bce-132">移動目錄</span><span class="sxs-lookup"><span data-stu-id="28bce-132">Move directory</span></span>|<span data-ttu-id="28bce-133">將資料夾從一個位置移到另一個。</span><span class="sxs-lookup"><span data-stu-id="28bce-133">Moves a folder from one location to another.</span></span>|  
|<span data-ttu-id="28bce-134">移動檔案</span><span class="sxs-lookup"><span data-stu-id="28bce-134">Move file</span></span>|<span data-ttu-id="28bce-135">將檔案從一個位置移到另一個。</span><span class="sxs-lookup"><span data-stu-id="28bce-135">Moves a file from one location to another.</span></span>|  
|<span data-ttu-id="28bce-136">重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="28bce-136">Rename file</span></span>|<span data-ttu-id="28bce-137">重新命名指定位置的檔案。</span><span class="sxs-lookup"><span data-stu-id="28bce-137">Renames a file in a specified location.</span></span>|  
|<span data-ttu-id="28bce-138">設定屬性</span><span class="sxs-lookup"><span data-stu-id="28bce-138">Set attributes</span></span>|<span data-ttu-id="28bce-139">設定檔案和資料夾的屬性。</span><span class="sxs-lookup"><span data-stu-id="28bce-139">Sets attributes on files and folders.</span></span> <span data-ttu-id="28bce-140">屬性包括「封存」、「隱藏」、「一般」「唯讀」和「系統」。</span><span class="sxs-lookup"><span data-stu-id="28bce-140">Attributes include Archive, Hidden, Normal, ReadOnly, and System.</span></span> <span data-ttu-id="28bce-141">「一般」表示無任何屬性，且不可與其他屬性結合。</span><span class="sxs-lookup"><span data-stu-id="28bce-141">Normal is the lack of attributes, and it cannot be combined with other attributes.</span></span> <span data-ttu-id="28bce-142">其他所有屬性都可互相結合使用。</span><span class="sxs-lookup"><span data-stu-id="28bce-142">All other attributes can be used in combination.</span></span>|  
  
 <span data-ttu-id="28bce-143">「檔案系統」工作會在單一檔案或目錄上運作。</span><span class="sxs-lookup"><span data-stu-id="28bce-143">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="28bce-144">因此，這項工作不支援使用萬用字元在多個檔案上執行相同的作業。</span><span class="sxs-lookup"><span data-stu-id="28bce-144">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files.</span></span> <span data-ttu-id="28bce-145">為了要讓「檔案系統」工作在多個檔案或目錄上重複作業，請將「檔案系統」工作放入 Foreach 迴圈容器內，如以下步驟所述：</span><span class="sxs-lookup"><span data-stu-id="28bce-145">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container, as described in the following steps:</span></span>  
  
-   <span data-ttu-id="28bce-146">**設定 Foreach 迴圈容器** ：在 [Foreach 迴圈編輯器] 的 **[集合]** 頁面上，將列舉值設定為 **[Foreach 檔案列舉值]** 然後輸入萬用字元運算式，做為 **[檔案]** 的列舉值組態。</span><span class="sxs-lookup"><span data-stu-id="28bce-146">**Configure the Foreach Loop container** On the **Collection** page of the Foreach Loop Editor, set the enumerator to **Foreach File Enumerator** and enter the wildcard expression as the enumerator configuration for **Files**.</span></span> <span data-ttu-id="28bce-147">在 [Foreach 迴圈編輯器] 的 **[變數對應]** 頁面上，對應您要使用的變數，以便將檔案名稱傳遞到 [檔案系統] 工作，一次一個。</span><span class="sxs-lookup"><span data-stu-id="28bce-147">On the **Variable Mappings** page of the Foreach Loop Editor, map a variable that you want to use to pass the file names one at a time to the File System task.</span></span>  
  
-   <span data-ttu-id="28bce-148">**加入和設定檔案系統工作** ：將「檔案系統」工作加入到「Foreach 迴圈」容易。</span><span class="sxs-lookup"><span data-stu-id="28bce-148">**Add and configure a File System task** Add a File System task to the Foreach Loop container.</span></span> <span data-ttu-id="28bce-149">在「檔案系統工作編輯器」的 **[一般]** 頁面上，將 **[SourceVariable]** 或 **[DestinationVariable]** 屬性設定為您在「Foreach 迴圈」容器中定義的變數。</span><span class="sxs-lookup"><span data-stu-id="28bce-149">On the **General** page of the File System Task Editor, set the **SourceVariable** or **DestinationVariable** property to the variable that you defined in the Foreach Loop container.</span></span>  
  
## <a name="custom-log-entries-available-on-the-file-system-task"></a><span data-ttu-id="28bce-150">檔案系統工作上可用的自訂記錄項目</span><span class="sxs-lookup"><span data-stu-id="28bce-150">Custom Log Entries Available on the File System Task</span></span>  
 <span data-ttu-id="28bce-151">下表描述「檔案系統」工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="28bce-151">The following table describes the custom log entry for the File System task.</span></span> <span data-ttu-id="28bce-152">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="28bce-152">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="28bce-153">記錄項目</span><span class="sxs-lookup"><span data-stu-id="28bce-153">Log entry</span></span>|<span data-ttu-id="28bce-154">描述</span><span class="sxs-lookup"><span data-stu-id="28bce-154">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="28bce-155">報告工作執行的作業。</span><span class="sxs-lookup"><span data-stu-id="28bce-155">Reports the operation that the task performs.</span></span> <span data-ttu-id="28bce-156">記錄項目會在檔案系統作業開始時寫入，項目中包含有關來源和目的地的資訊。</span><span class="sxs-lookup"><span data-stu-id="28bce-156">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
## <a name="configuring-the-file-system-task"></a><span data-ttu-id="28bce-157">設定檔案系統工作</span><span class="sxs-lookup"><span data-stu-id="28bce-157">Configuring the File System Task</span></span>  
 <span data-ttu-id="28bce-158">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="28bce-158">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="28bce-159">如需有關可在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="28bce-159">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="28bce-160">檔案系統工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="28bce-160">File System Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="28bce-161">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="28bce-161">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="28bce-162">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="28bce-162">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="28bce-163">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="28bce-163">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
 <span data-ttu-id="28bce-164">如需有關如何以程式設計的方式設定這些屬性的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="28bce-164">For more information about how to set these properties programmatically, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="28bce-165">相關工作</span><span class="sxs-lookup"><span data-stu-id="28bce-165">Related Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="28bce-166">包括下載和上傳資料檔以及管理伺服器上目錄的工作。</span><span class="sxs-lookup"><span data-stu-id="28bce-166">includes a task that downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="28bce-167">如需相關資訊，請參閱 [FTP Task](ftp-task.md)。</span><span class="sxs-lookup"><span data-stu-id="28bce-167">For more information, see [FTP Task](ftp-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bce-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28bce-168">See Also</span></span>  
 <span data-ttu-id="28bce-169">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="28bce-169">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="28bce-170">控制流程</span><span class="sxs-lookup"><span data-stu-id="28bce-170">Control Flow</span></span>](control-flow.md)  
  
  
