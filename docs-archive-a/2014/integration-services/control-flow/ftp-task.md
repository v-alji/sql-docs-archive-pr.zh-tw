---
title: FTP 工作 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.f1
helpviewer_keywords:
- FTP task [Integration Services]
ms.assetid: 41c3f2c4-ee04-460a-9822-bb9ae4036c2e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63ec58c1bff9894d0aa73112686c4b1fe9421b98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584686"
---
# <a name="ftp-task"></a><span data-ttu-id="871be-102">FTP 工作</span><span class="sxs-lookup"><span data-stu-id="871be-102">FTP Task</span></span>
  <span data-ttu-id="871be-103">FTP 工作會下載和上傳資料檔以及管理伺服器上的目錄。</span><span class="sxs-lookup"><span data-stu-id="871be-103">The FTP task downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="871be-104">例如，封裝可從遠端伺服器或網際網路位置下載資料檔，此工作可視為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝工作流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="871be-104">For example, a package can download data files from a remote server or an Internet location as part of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="871be-105">您可將 FTP 工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="871be-105">You can use the FTP task for the following purposes:</span></span>  
  
-   <span data-ttu-id="871be-106">在移動資料之前或之後於目錄之間複製目錄和資料檔，以及將轉換套用至資料。</span><span class="sxs-lookup"><span data-stu-id="871be-106">Copying directories and data files from one directory to another, before or after moving data, and applying transformations to the data.</span></span>  
  
-   <span data-ttu-id="871be-107">登入來源 FTP 位置並複製檔案或封裝至目的地目錄。</span><span class="sxs-lookup"><span data-stu-id="871be-107">Logging in to a source FTP location and copying files or packages to a destination directory.</span></span>  
  
-   <span data-ttu-id="871be-108">從 FTP 位置下載檔案，並在將資料載入資料庫之前，將轉換套用至資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="871be-108">Downloading files from an FTP location and applying transformations to column data before loading the data into a database.</span></span>  
  
 <span data-ttu-id="871be-109">在執行階段中，FTP 工作會使用 FTP 連接管理員連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="871be-109">At run time, the FTP task connects to a server by using an FTP connection manager.</span></span> <span data-ttu-id="871be-110">FTP 連接管理員會在 FTP 工作以外另行設定，然後在 FTP 中參考。</span><span class="sxs-lookup"><span data-stu-id="871be-110">The FTP connection manager is configured separately from the FTP task, and then is referenced in the FTP task.</span></span> <span data-ttu-id="871be-111">FTP 連接管理員包含伺服器設定、存取 FTP 伺服器的認證，以及一些選項如逾時和連接伺服器的重試次數。</span><span class="sxs-lookup"><span data-stu-id="871be-111">The FTP connection manager includes the server settings, the credentials for accessing the FTP server, and options such as the time-out and the number of retries for connecting to the server.</span></span> <span data-ttu-id="871be-112">如需詳細資訊，請參閱 [FTP Connection Manager](../connection-manager/ftp-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="871be-112">For more information, see [FTP Connection Manager](../connection-manager/ftp-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="871be-113">FTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="871be-113">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="871be-114">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="871be-114">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="871be-115">存取本機檔案或本機目錄時，FTP 工作會使用「檔案」連接管理員或變數中儲存的路徑資訊。</span><span class="sxs-lookup"><span data-stu-id="871be-115">When accessing a local file or a local directory, the FTP task uses a File connection manager or path information stored in a variable.</span></span> <span data-ttu-id="871be-116">但 FTP 工作存取遠端檔案或遠端目錄時則相反，是使用遠端伺服器上直接指定的路徑 (如 FTP 連接管理員中所指定)，或變數中儲存的路徑資訊。</span><span class="sxs-lookup"><span data-stu-id="871be-116">In contrast, when accessing a remote file or a remote directory, the FTP task uses a directly specified path on the remote server, as specified in the FTP connection manager, or path information stored in a variable.</span></span> <span data-ttu-id="871be-117">如需詳細資訊，請參閱[檔案連線管理員](../connection-manager/file-connection-manager.md)和 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="871be-117">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="871be-118">這表示，FTP 工作可接收多個檔案和刪除多個遠端檔案；而如果此工作使用連接管理員，則只能傳送一個檔案且只能刪除一個本機檔案，因為「檔案」連接管理員只能存取一個檔案。</span><span class="sxs-lookup"><span data-stu-id="871be-118">This means that the FTP task can receive multiple files and delete multiple remote files; but the task can send only one file and delete only one local file if it uses a connection manager, because a File connection manager can access only one file.</span></span> <span data-ttu-id="871be-119">若要存取多個本機檔案，FTP 工作必須使用變數提供路徑資訊。</span><span class="sxs-lookup"><span data-stu-id="871be-119">To access multiple local files, the FTP task must use a variable to provide the path information.</span></span> <span data-ttu-id="871be-120">例如，含有 "C:\Test\\*.txt" 的變數會提供支援刪除或傳送 Test 目錄中所有副檔名為 .txt 的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="871be-120">For example, a variable that contains "C:\Test\\*.txt" provides a path that supports deleting or sending all the files that have a .txt extension in the Test directory.</span></span>  
  
 <span data-ttu-id="871be-121">若要傳送多個檔案及存取多個本機檔案和目錄，您也可以將 FTP 工作加入「Foreach 迴圈」中，藉此多次執行 FTP 工作。</span><span class="sxs-lookup"><span data-stu-id="871be-121">To send multiple files and access multiple local files and directories, you can also execute the FTP task multiple times by including the task in a Foreach Loop.</span></span> <span data-ttu-id="871be-122">「Foreach 迴圈」可使用 For Each File 列舉值，於目錄中跨檔案列舉。</span><span class="sxs-lookup"><span data-stu-id="871be-122">The Foreach Loop can enumerate across files in a directory using the For Each File enumerator.</span></span> <span data-ttu-id="871be-123">如需詳細資訊，請參閱 [Foreach 迴圈容器](foreach-loop-container.md)＞。</span><span class="sxs-lookup"><span data-stu-id="871be-123">For more information, see [Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="871be-124">FTP 工作支援在路徑中使用 *?*</span><span class="sxs-lookup"><span data-stu-id="871be-124">The FTP task supports the *?*</span></span> <span data-ttu-id="871be-125">及 *\** 萬用字元。</span><span class="sxs-lookup"><span data-stu-id="871be-125">and *\** wildcard characters in paths.</span></span> <span data-ttu-id="871be-126">如此即可讓工作存取多個檔案。</span><span class="sxs-lookup"><span data-stu-id="871be-126">This lets the task access multiple files.</span></span> <span data-ttu-id="871be-127">不過，您只能在指定檔名的路徑部分使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="871be-127">However, you can use wildcard characters only in the part of the path that specifies the file name.</span></span> <span data-ttu-id="871be-128">例如，C:\MyDirectory\\*.txt 是有效的路徑，而 C:\\\*\MyText.txt 則無效。</span><span class="sxs-lookup"><span data-stu-id="871be-128">For example, C:\MyDirectory\\*.txt is a valid path, but C:\\\*\MyText.txt is not.</span></span>  
  
 <span data-ttu-id="871be-129">FTP 作業可設定成在作業失敗時停止「檔案系統」工作，或以 ASCII 模式傳送檔案。</span><span class="sxs-lookup"><span data-stu-id="871be-129">The FTP operations can be configured to stop the File System task when the operation fails, or to transfer files in ASCII mode.</span></span> <span data-ttu-id="871be-130">傳送和接收檔案副本的作業可設定成覆寫目的地檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="871be-130">The operations that send and receive files copy can be configured to overwrite destination files and directories.</span></span>  
  
## <a name="predefined-ftp-operations"></a><span data-ttu-id="871be-131">預先定義的 FTP 作業</span><span class="sxs-lookup"><span data-stu-id="871be-131">Predefined FTP Operations</span></span>  
 <span data-ttu-id="871be-132">FTP 工作包括一組預先定義的作業。</span><span class="sxs-lookup"><span data-stu-id="871be-132">The FTP task includes a predefined set of operations.</span></span> <span data-ttu-id="871be-133">下表描述這些作業。</span><span class="sxs-lookup"><span data-stu-id="871be-133">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="871be-134">作業</span><span class="sxs-lookup"><span data-stu-id="871be-134">Operation</span></span>|<span data-ttu-id="871be-135">描述</span><span class="sxs-lookup"><span data-stu-id="871be-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="871be-136">傳送檔案</span><span class="sxs-lookup"><span data-stu-id="871be-136">Send files</span></span>|<span data-ttu-id="871be-137">從本機電腦將檔案傳送到 FTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="871be-137">Sends a file from the local computer to the FTP server.</span></span>|  
|<span data-ttu-id="871be-138">接收檔案</span><span class="sxs-lookup"><span data-stu-id="871be-138">Receive files</span></span>|<span data-ttu-id="871be-139">從 FTP 伺服器將檔案儲存到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="871be-139">Saves a file from the FTP server to the local computer.</span></span>|  
|<span data-ttu-id="871be-140">建立本機目錄</span><span class="sxs-lookup"><span data-stu-id="871be-140">Create local directory</span></span>|<span data-ttu-id="871be-141">在本機電腦上建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="871be-141">Creates a folder on the local computer.</span></span>|  
|<span data-ttu-id="871be-142">建立遠端目錄</span><span class="sxs-lookup"><span data-stu-id="871be-142">Create remote directory</span></span>|<span data-ttu-id="871be-143">在 FTP 伺服器上建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="871be-143">Creates a folder on the FTP server.</span></span>|  
|<span data-ttu-id="871be-144">移除本機目錄</span><span class="sxs-lookup"><span data-stu-id="871be-144">Remove local directory</span></span>|<span data-ttu-id="871be-145">刪除本機電腦上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="871be-145">Deletes a folder on the local computer.</span></span>|  
|<span data-ttu-id="871be-146">移除遠端目錄</span><span class="sxs-lookup"><span data-stu-id="871be-146">Remove remote directory</span></span>|<span data-ttu-id="871be-147">刪除 FTP 伺服器上的資料夾。</span><span class="sxs-lookup"><span data-stu-id="871be-147">Deletes a folder on the FTP server.</span></span>|  
|<span data-ttu-id="871be-148">刪除本機檔案</span><span class="sxs-lookup"><span data-stu-id="871be-148">Delete local files</span></span>|<span data-ttu-id="871be-149">刪除本機電腦上的檔案。</span><span class="sxs-lookup"><span data-stu-id="871be-149">Deletes a file on the local computer.</span></span>|  
|<span data-ttu-id="871be-150">刪除遠端檔案</span><span class="sxs-lookup"><span data-stu-id="871be-150">Delete remote files</span></span>|<span data-ttu-id="871be-151">刪除 FTP 伺服器上的檔案。</span><span class="sxs-lookup"><span data-stu-id="871be-151">Deletes a file on the FTP server.</span></span>|  
  
## <a name="custom-log-entries-available-on-the-ftp-task"></a><span data-ttu-id="871be-152">FTP 工作上可用的自訂記錄項目</span><span class="sxs-lookup"><span data-stu-id="871be-152">Custom Log Entries Available on the FTP Task</span></span>  
 <span data-ttu-id="871be-153">下表列出 FTP 工作的自訂記錄項目。</span><span class="sxs-lookup"><span data-stu-id="871be-153">The following table lists the custom log entries for the FTP task.</span></span> <span data-ttu-id="871be-154">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)和[自訂訊息以進行記錄](../custom-messages-for-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="871be-154">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="871be-155">記錄項目</span><span class="sxs-lookup"><span data-stu-id="871be-155">Log entry</span></span>|<span data-ttu-id="871be-156">描述</span><span class="sxs-lookup"><span data-stu-id="871be-156">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="871be-157">指出工作已經起始與 FTP 伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="871be-157">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="871be-158">報告工作執行之 FTP 作業的開始及其類型。</span><span class="sxs-lookup"><span data-stu-id="871be-158">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="871be-159">相關工作</span><span class="sxs-lookup"><span data-stu-id="871be-159">Related Tasks</span></span>  
 <span data-ttu-id="871be-160">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="871be-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="871be-161">如需如何在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具中設定這些屬性的詳細資訊，請參閱 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="871be-161">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
 <span data-ttu-id="871be-162">如需以程式設計方式設定這些屬性的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>。</span><span class="sxs-lookup"><span data-stu-id="871be-162">For more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871be-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="871be-163">See Also</span></span>  
 <span data-ttu-id="871be-164">[FTP 工作編輯器 &#40;一般頁面&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="871be-164">[FTP Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="871be-165">[FTP 工作編輯器 &#40;檔案傳輸頁面&#41;](../ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="871be-165">[FTP Task Editor &#40;File Transfer Page&#41;](../ftp-task-editor-file-transfer-page.md) </span></span>  
 <span data-ttu-id="871be-166">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="871be-166">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="871be-167">控制流程</span><span class="sxs-lookup"><span data-stu-id="871be-167">Control Flow</span></span>](control-flow.md)  
  
  
