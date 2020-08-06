---
title: Web 服務工作編輯器 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dbacf2a2a867ab01039678ff4f43eebac839c11a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599570"
---
# <a name="web-service-task-editor-general-page"></a><span data-ttu-id="283d6-102">Web 服務工作編輯器 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="283d6-102">Web Service Task Editor (General Page)</span></span>
  <span data-ttu-id="283d6-103">使用 [Web 服務工作編輯器]  對話方塊的 [一般]  頁面，來指定 HTTP 連接管理員、指定 Web 服務工作使用的 Web 服務描述語言 (WSDL) 檔案的位置、描述 Web 服務工作，以及下載 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-103">Use the **General** page of the **Web Services Task Editor** dialog box to specify an HTTP connection manager, specify the location of the Web Services Description Language (WSDL) file the Web Service task uses, describe the Web Services task, and download the WSDL file.</span></span>  
  
 <span data-ttu-id="283d6-104">如需這項工作的詳細資訊，請參閱 [Web 服務工作](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="283d6-104">For more information about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="283d6-105">選項。</span><span class="sxs-lookup"><span data-stu-id="283d6-105">Options</span></span>  
 <span data-ttu-id="283d6-106">**HTTPConnection**</span><span class="sxs-lookup"><span data-stu-id="283d6-106">**HTTPConnection**</span></span>  
 <span data-ttu-id="283d6-107">在清單中選取連線管理員，或按一下 \<**New connection...**> 來建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="283d6-107">Select a connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="283d6-108">HTTP 連接管理員僅支援匿名驗證和基本驗證，</span><span class="sxs-lookup"><span data-stu-id="283d6-108">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="283d6-109">而不支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="283d6-109">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="283d6-110">**相關主題：** [HTTP 連接管理員](connection-manager/http-connection-manager.md)、[HTTP 連接管理員編輯器 &#40;伺服器頁面&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span><span class="sxs-lookup"><span data-stu-id="283d6-110">**Related Topics:**  [HTTP Connection Manager](connection-manager/http-connection-manager.md), [HTTP Connection Manager Editor &#40;Server Page&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span></span>  
  
 <span data-ttu-id="283d6-111">**WSDLFile**</span><span class="sxs-lookup"><span data-stu-id="283d6-111">**WSDLFile**</span></span>  
 <span data-ttu-id="283d6-112">鍵入本機電腦的 WSDL 檔案完整路徑，或按一下瀏覽按鈕 **(...)** 並找出此檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-112">Type the fully qualified path of a WSDL file that is local to the computer, or click the browse button **(...)** and locate this file.</span></span>  
  
 <span data-ttu-id="283d6-113">如果您已經將 WSDL 檔案手動下載到電腦中，請選取該檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-113">If you have already manually downloaded the WSDL file to the computer, select this file.</span></span> <span data-ttu-id="283d6-114">如果尚未下載 WSDL 檔案，則請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="283d6-114">However, if the WSDL file has not yet been downloaded, follow these steps:</span></span>  
  
-   <span data-ttu-id="283d6-115">建立副檔名為 ".wsdl" 的空白檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-115">Create an empty file that has the ".wsdl" file name extension.</span></span>  
  
-   <span data-ttu-id="283d6-116">在 [WSDLFile]  選項中選取此空白檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-116">Select this empty file for the **WSDLFile** option.</span></span>  
  
-   <span data-ttu-id="283d6-117">將**OverwriteWSDLFile**的值設定為 `True` ，即可讓空的檔案以實際的 WSDL 檔案覆寫。</span><span class="sxs-lookup"><span data-stu-id="283d6-117">Set the value of **OverwriteWSDLFile** to `True` to enable the empty file to be overwritten with the actual WSDL file.</span></span>  
  
-   <span data-ttu-id="283d6-118">按一下 [下載 WSDL]  ，下載實際的 WSDL 檔案並覆寫空白檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-118">Click **Download WSDL** to download the actual WSDL file and overwrite the empty file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="283d6-119">您必須先在 [WSDLFile]  方塊中提供現有的本機檔案名稱，才能啟用 [下載 WSDL]  選項。</span><span class="sxs-lookup"><span data-stu-id="283d6-119">The **Download WSDL** option is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
 <span data-ttu-id="283d6-120">**OverwriteWSDLFile**</span><span class="sxs-lookup"><span data-stu-id="283d6-120">**OverwriteWSDLFile**</span></span>  
 <span data-ttu-id="283d6-121">指出是否可以覆寫 Web 服務工作的 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-121">Indicate whether the WSDL file for the Web Service task can be overwritten.</span></span>  
  
 <span data-ttu-id="283d6-122">如果您想要使用 [**下載 wsdl** ] 按鈕來下載 wsdl 檔案，請將此值設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="283d6-122">If you intend to download the WSDL file by using the **Download WSDL** button, set this value to `True`.</span></span>  
  
 <span data-ttu-id="283d6-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="283d6-123">**Name**</span></span>  
 <span data-ttu-id="283d6-124">為 Web 服務工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="283d6-124">Provide a unique name for the Web Service task.</span></span> <span data-ttu-id="283d6-125">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="283d6-125">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="283d6-126">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="283d6-126">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="283d6-127">**說明**</span><span class="sxs-lookup"><span data-stu-id="283d6-127">**Description**</span></span>  
 <span data-ttu-id="283d6-128">輸入 Web 服務工作的描述。</span><span class="sxs-lookup"><span data-stu-id="283d6-128">Type a description of the Web Service task.</span></span>  
  
 <span data-ttu-id="283d6-129">**下載 WSDL**</span><span class="sxs-lookup"><span data-stu-id="283d6-129">**Download WSDL**</span></span>  
 <span data-ttu-id="283d6-130">下載 WSDL 檔案。</span><span class="sxs-lookup"><span data-stu-id="283d6-130">Download the WSDL file.</span></span>  
  
 <span data-ttu-id="283d6-131">您必須先在 [WSDLFile]  方塊中提供現有的本機檔案名稱，才能啟用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="283d6-131">This button is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="283d6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="283d6-132">See Also</span></span>  
 <span data-ttu-id="283d6-133">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="283d6-133">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="283d6-134">[Web 服務工作編輯器 &#40;輸入頁面&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="283d6-134">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 <span data-ttu-id="283d6-135">[[Web 服務工作編輯器] &#40;[輸出] 頁面&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="283d6-135">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 [<span data-ttu-id="283d6-136">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="283d6-136">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
