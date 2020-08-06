---
title: FTP 工作編輯器 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0cb4ffe2fa44e76890f6b70912f84dbcaa8f2cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593443"
---
# <a name="ftp-task-editor-general-page"></a><span data-ttu-id="5954d-102">FTP 工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="5954d-102">FTP Task Editor (General Page)</span></span>
  <span data-ttu-id="5954d-103">使用 **[FTP 工作編輯器]** 對話方塊的 **[一般]** 頁面，即可指定 FTP 連接管理員，以連接到工作進行通訊的 FTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5954d-103">Use the **General** page of the **FTP Task Editor** dialog box to specify the FTP connection manager that connects to the FTP server that the task communicates with.</span></span> <span data-ttu-id="5954d-104">您也可以命名和描述 FTP 工作。</span><span class="sxs-lookup"><span data-stu-id="5954d-104">You can also name and describe the FTP task.</span></span>  
  
 <span data-ttu-id="5954d-105">若要深入了解此工作，請參閱 [FTP 工作](control-flow/ftp-task.md)。</span><span class="sxs-lookup"><span data-stu-id="5954d-105">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5954d-106">選項。</span><span class="sxs-lookup"><span data-stu-id="5954d-106">Options</span></span>  
 <span data-ttu-id="5954d-107">**FtpConnection**</span><span class="sxs-lookup"><span data-stu-id="5954d-107">**FtpConnection**</span></span>  
 <span data-ttu-id="5954d-108">選取現有的 FTP 連線管理員，或按一下 \<**New connection...**> 來建立連線管理員。</span><span class="sxs-lookup"><span data-stu-id="5954d-108">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5954d-109">FTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="5954d-109">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="5954d-110">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="5954d-110">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="5954d-111">**相關主題**：[FTP 連線管理員](connection-manager/ftp-connection-manager.md)、[FTP 連線管理員編輯器](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="5954d-111">**Related Topics**: [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="5954d-112">**StopOnFailure**</span><span class="sxs-lookup"><span data-stu-id="5954d-112">**StopOnFailure**</span></span>  
 <span data-ttu-id="5954d-113">指出當 FTP 作業失敗時，FTP 工作是否結束。</span><span class="sxs-lookup"><span data-stu-id="5954d-113">Indicate whether the FTP task terminates if an FTP operation fails.</span></span>  
  
 <span data-ttu-id="5954d-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5954d-114">**Name**</span></span>  
 <span data-ttu-id="5954d-115">為 FTP 工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="5954d-115">Provide a unique name for the FTP task.</span></span> <span data-ttu-id="5954d-116">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="5954d-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5954d-117">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="5954d-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="5954d-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="5954d-118">**Description**</span></span>  
 <span data-ttu-id="5954d-119">輸入 FTP 工作的描述。</span><span class="sxs-lookup"><span data-stu-id="5954d-119">Type a description of the FTP task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5954d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5954d-120">See Also</span></span>  
 <span data-ttu-id="5954d-121">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5954d-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="5954d-122">[FTP 工作編輯器 &#40;檔案傳輸頁面&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="5954d-122">[FTP Task Editor &#40;File Transfer Page&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span></span>  
 [<span data-ttu-id="5954d-123">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="5954d-123">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
