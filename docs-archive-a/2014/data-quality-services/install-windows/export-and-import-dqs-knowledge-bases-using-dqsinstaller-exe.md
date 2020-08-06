---
title: 使用 DQSInstaller.exe 匯出及匯入 DQS 知識庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8234c63b-a018-4e55-8184-9a6bdf03274d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 64a8feb7bfded742da7563642b07181166fcbeab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705434"
---
# <a name="export-and-import-dqs-knowledge-bases-using-dqsinstallerexe"></a><span data-ttu-id="69245-102">使用 DQSInstaller.exe 匯出及匯入 DQS 知識庫</span><span class="sxs-lookup"><span data-stu-id="69245-102">Export and Import DQS Knowledge Bases Using DQSInstaller.exe</span></span>
  <span data-ttu-id="69245-103">若為 DQS 的現有安裝，您可以在 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 中將所有知識庫一次匯出到 DQS 備份檔案 (.dqsb)，然後從命令提示字元執行 DQSInstaller.exe 檔案，即可使用此 .dqsb 檔案一次將所有知識庫匯入不同的 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="69245-103">For an existing installation of DQS, you can export all the knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb) at once, and then later use the .dqsb file to import all the knowledge bases to a different [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once by running the DQSInstaller.exe file from the command prompt.</span></span> <span data-ttu-id="69245-104">如需有關從命令提示字元執行 DQSInstaller.exe 的詳細資訊，請參閱＜ [從命令提示字元執行 DQSInstaller.exe](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) ＞中的＜ [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)＞。</span><span class="sxs-lookup"><span data-stu-id="69245-104">For more information about running DQSInstaller.exe from the command prompt, see [Run DQSInstaller.exe from Command Prompt](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#CommandPrompt) in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
 <span data-ttu-id="69245-105">這項功能可讓您在 *中一次備份所有*[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 知識庫，而不必個別使用 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]將每一個知識庫匯出到 .dqs 檔案。</span><span class="sxs-lookup"><span data-stu-id="69245-105">This feature enables you to take a backup of *all* your knowledge bases in [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually export each knowledge base to a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="69245-106">同樣地，您可以從備份檔案一次將所有 \*\* 知識庫匯入另一個 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ，而不必使用 [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]從 .dqs 檔案個別匯入每一個知識庫。</span><span class="sxs-lookup"><span data-stu-id="69245-106">Similarly, you can import *all* the knowledge bases from the backup file into another [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at once without having to individually import each knowledge base from a .dqs file by using [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="69245-107">當您在電腦上解除安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ，然後將它重新安裝在另一部電腦上時，這對於備份和還原知識庫特別有用處。</span><span class="sxs-lookup"><span data-stu-id="69245-107">This is particularly useful for backing up and restoring your knowledge bases when you are uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a computer, and then reinstalling it on a different computer.</span></span> <span data-ttu-id="69245-108">您可以在現有的 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 安裝中輕鬆將所有知識庫匯出到 DQS 備份檔案 (.dqsb)，然後在另一部電腦上安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 之後從備份檔案匯入所有知識庫。</span><span class="sxs-lookup"><span data-stu-id="69245-108">You can easily export all the knowledge bases in an existing installation of [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), and then import all the knowledge bases from the backup file after installing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] on a different computer.</span></span>  
  
##  <a name="exporting-knowledge-bases-to-dqsb-file"></a><a name="export"></a> <span data-ttu-id="69245-109">將知識庫匯出到 .dqsb 檔案</span><span class="sxs-lookup"><span data-stu-id="69245-109">Exporting Knowledge Bases to .dqsb File</span></span>  
 <span data-ttu-id="69245-110">您可以在任何時間或是解除安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 時，於現有的 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]中匯出所有知識庫。</span><span class="sxs-lookup"><span data-stu-id="69245-110">You can export all the knowledge bases in the existing [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] at any time or while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].</span></span>  
  
-   <span data-ttu-id="69245-111">若要在 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 中將所有知識庫匯出到 DQS 備份檔案 (.dqsb)，請從命令提示字元使用 `exportkbs` 參數執行 DQSInstaller.exe，連同您想要匯出知識庫之目標的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="69245-111">To export all the knowledge bases in a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] to a DQS backup file (.dqsb), run DQSInstaller.exe with the `exportkbs` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="69245-112">例如，若要將所有知識庫匯出到 C: 磁碟機中的 DQSBackup.dqsb 檔案：</span><span class="sxs-lookup"><span data-stu-id="69245-112">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive:</span></span>  
  
    ```  
    dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="69245-113">如果提供的檔案名稱已經存在於指定的位置，安裝程式會提示您是否要覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="69245-113">If the provided file name already exists at the specified location, the installer prompts you whether to overwrite the file.</span></span>  
  
-   <span data-ttu-id="69245-114">若要在解除安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]時將所有知識庫匯出到 DQS 備份檔案，請從命令提示字元使用 `uninstall` 參數執行 DQSInstaller.exe，連同您想要匯出知識庫之目標的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="69245-114">To export all the knowledge bases to a DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)], run DQSInstaller.exe with the `uninstall` parameter from the command prompt, along with the full path and file name where you want to export the knowledge bases.</span></span> <span data-ttu-id="69245-115">例如，若要將所有知識庫匯出到 C: 磁碟機中的 DQSBackup.dqsb 檔案，然後解除安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="69245-115">For example, to export all the knowledge bases to the DQSBackup.dqsb file in the C: drive, and then uninstall [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]:</span></span>  
  
    ```  
    dqsinstaller.exe -uninstall c:\DQSBackup.dqsb  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="69245-116">如果當您從命令提示字元使用 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 參數解除安裝 `uninstall` 時，並未指定 DQS 備份檔案的完整路徑和檔案名稱，則會顯示一則訊息，表示所有知識庫都將遭到刪除，並可讓您選擇是否要繼續解除安裝程序。</span><span class="sxs-lookup"><span data-stu-id="69245-116">If you do not specify the full path and file name of the DQS backup file while uninstalling [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] from the command prompt using the `uninstall` parameter, a message is displayed stating that all the knowledge bases will be deleted, and allows you to choose whether to continue with the uninstall process.</span></span>  
  
##  <a name="importing-knowledge-bases-from-dqsb-file"></a><a name="import"></a> <span data-ttu-id="69245-117">從 .dqsb 檔案匯入知識庫</span><span class="sxs-lookup"><span data-stu-id="69245-117">Importing Knowledge Bases from .dqsb File</span></span>  
 <span data-ttu-id="69245-118">完成 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 安裝後，您可以從 DQS 備份檔 (.dqsb) 匯入所有知識庫。</span><span class="sxs-lookup"><span data-stu-id="69245-118">You can import all the knowledge bases from a DQS backup file (.dqsb) after completing the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation.</span></span> <span data-ttu-id="69245-119">若要匯入知識庫，您必須擁有有效的 DQS 備份檔案 (.dqsb)。</span><span class="sxs-lookup"><span data-stu-id="69245-119">To import knowledge bases, you must have a valid DQS backup file (.dqsb).</span></span>  
  
 <span data-ttu-id="69245-120">從命令提示字元使用 `importkbs` 參數執行 DQSInstaller.exe 檔案，連同您想要匯入知識庫之來源的完整路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="69245-120">Run the DQSInstaller.exe file with the `importkbs` parameter from the command prompt, along with the full path and file name from where you want to import the knowledge bases.</span></span> <span data-ttu-id="69245-121">例如，若要從 C: 磁碟機中的 DQSBackup.dqsb 檔案匯入所有知識庫：</span><span class="sxs-lookup"><span data-stu-id="69245-121">For example, to import all the knowledge bases from the DQSBackup.dqsb file in the C: drive:</span></span>  
  
```  
dqsinstaller.exe -importkbs c:\DQSBackup.dqsb  
```  
  
 <span data-ttu-id="69245-122">如果 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 中目前已經存在與您要匯入的知識庫同名的知識庫，則匯入的知識庫名稱將會附加底線 (_)，後面緊接著以 1 開頭的整數值。</span><span class="sxs-lookup"><span data-stu-id="69245-122">If there are existing knowledge bases in your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] with the same name as the ones you are importing, the names of the imported knowledge bases will be appended with an underscore (_) followed by an integer value starting with 1.</span></span> <span data-ttu-id="69245-123">例如，如果 "CompanyName" 網域是重複的，則匯入的網域名稱將會是 "CompanyName_1"。</span><span class="sxs-lookup"><span data-stu-id="69245-123">For example, if the "CompanyName" domain is duplicate, the imported domain name will be "CompanyName_1."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69245-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69245-124">See Also</span></span>  
 <span data-ttu-id="69245-125">[執行 DQSInstaller.exe 以完成 Data Quality Server 安裝](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="69245-125">[Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md) </span></span>  
 <span data-ttu-id="69245-126">[安裝 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="69245-126">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 <span data-ttu-id="69245-127">[將知識庫匯出至 dqs 檔案](../export-a-knowledge-base-to-a-dqs-file.md) </span><span class="sxs-lookup"><span data-stu-id="69245-127">[Export a Knowledge Base to a .dqs File](../export-a-knowledge-base-to-a-dqs-file.md) </span></span>  
 [<span data-ttu-id="69245-128">從 .dqs 檔案匯入知識庫</span><span class="sxs-lookup"><span data-stu-id="69245-128">Import a Knowledge Base from a .dqs File</span></span>](../import-a-knowledge-base-from-a-dqs-file.md)  
  
  
