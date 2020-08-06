---
title: '[Web 服務工作編輯器] (輸出頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ad034ae78a096ebe5998ac2c3d2573fe7c3bfd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599565"
---
# <a name="web-service-task-editor-output-page"></a><span data-ttu-id="b1c9f-102">Web 服務工作編輯器 (輸出頁面)</span><span class="sxs-lookup"><span data-stu-id="b1c9f-102">Web Service Task Editor (Output Page)</span></span>
  <span data-ttu-id="b1c9f-103">使用 [Web 服務工作編輯器]  對話方塊的 [輸出]  頁面，即可指定 Web 方法傳回的結果之儲存位置。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-103">Use the **Output** page of the **Web Service Task Editor** dialog box to specify where to store the result returned by the Web method.</span></span>  
  
 <span data-ttu-id="b1c9f-104">若要了解這個工作，請參閱 [Web 服務工作](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-104">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="b1c9f-105">靜態選項</span><span class="sxs-lookup"><span data-stu-id="b1c9f-105">Static Options</span></span>  
 <span data-ttu-id="b1c9f-106">**OutputType**</span><span class="sxs-lookup"><span data-stu-id="b1c9f-106">**OutputType**</span></span>  
 <span data-ttu-id="b1c9f-107">選取儲存結果時使用的儲存類型。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-107">Select the storage type to use when storing the results.</span></span> <span data-ttu-id="b1c9f-108">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="b1c9f-109">值</span><span class="sxs-lookup"><span data-stu-id="b1c9f-109">Value</span></span>|<span data-ttu-id="b1c9f-110">描述</span><span class="sxs-lookup"><span data-stu-id="b1c9f-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1c9f-111">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="b1c9f-111">**File Connection**</span></span>|<span data-ttu-id="b1c9f-112">在檔案中儲存結果。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-112">Store the results in a file.</span></span> <span data-ttu-id="b1c9f-113">選取此值會顯示動態選項 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-113">Selecting this value displays the dynamic option, **File**.</span></span>|  
|<span data-ttu-id="b1c9f-114">**變數**</span><span class="sxs-lookup"><span data-stu-id="b1c9f-114">**Variable**</span></span>|<span data-ttu-id="b1c9f-115">在變數中儲存結果。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-115">Store the results in a variable.</span></span> <span data-ttu-id="b1c9f-116">選取此值會顯示動態選項 [變數]  。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-116">Selecting this value displays the dynamic option, **Variable**.</span></span>|  
  
## <a name="outputtype-dynamic-options"></a><span data-ttu-id="b1c9f-117">OutputType 動態選項</span><span class="sxs-lookup"><span data-stu-id="b1c9f-117">OutputType Dynamic Options</span></span>  
  
### <a name="outputtype--file-connection"></a><span data-ttu-id="b1c9f-118">OutputType = 檔案連接</span><span class="sxs-lookup"><span data-stu-id="b1c9f-118">OutputType = File Connection</span></span>  
 <span data-ttu-id="b1c9f-119">**檔案**</span><span class="sxs-lookup"><span data-stu-id="b1c9f-119">**File**</span></span>  
 <span data-ttu-id="b1c9f-120">在清單中選取檔案連線管理員，或按一下 \<**New Connection...**> 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-120">Select a File connection manager in the list or click \<**New Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="b1c9f-121">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="b1c9f-121">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="outputtype--variable"></a><span data-ttu-id="b1c9f-122">OutputType = 變數</span><span class="sxs-lookup"><span data-stu-id="b1c9f-122">OutputType = Variable</span></span>  
 <span data-ttu-id="b1c9f-123">**變數**</span><span class="sxs-lookup"><span data-stu-id="b1c9f-123">**Variable**</span></span>  
 <span data-ttu-id="b1c9f-124">在清單中選取變數，或按一下 \<**New Variable...**> 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="b1c9f-124">Select a variable in the list or click \<**New Variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="b1c9f-125">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="b1c9f-125">**Related Topics:**  [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c9f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1c9f-126">See Also</span></span>  
 <span data-ttu-id="b1c9f-127">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b1c9f-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="b1c9f-128">[&#40;一般頁面&#41;的 Web 服務工作編輯器](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="b1c9f-128">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="b1c9f-129">[Web 服務工作編輯器 &#40;輸入頁面&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="b1c9f-129">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 [<span data-ttu-id="b1c9f-130">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="b1c9f-130">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
