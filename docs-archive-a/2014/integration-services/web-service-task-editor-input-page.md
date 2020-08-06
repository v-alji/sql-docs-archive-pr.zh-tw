---
title: Web 服務工作編輯器 (輸入頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ae876572747b9bb1088fe8b0a1c2c2fdde9f4f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599568"
---
# <a name="web-service-task-editor-input-page"></a><span data-ttu-id="5fdb7-102">Web 服務工作編輯器 (輸入頁面)</span><span class="sxs-lookup"><span data-stu-id="5fdb7-102">Web Service Task Editor (Input Page)</span></span>
  <span data-ttu-id="5fdb7-103">使用 [Web 服務工作編輯器]  對話方塊的 [輸入]  頁面，即可指定 Web 服務、Web 方法，以及提供給 Web 方法的輸入值。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-103">Use the **Input** page of the **Web Service Task Editor** dialog box to specify the Web Service, the Web method, and the values to provide to the Web method as input.</span></span> <span data-ttu-id="5fdb7-104">在 [值] 資料行中直接輸入字串，或是在 [值] 資料行中選取變數，即可提供這些值。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-104">The values can be provided either by typing strings directly in the Value column, or by selecting variables in the Value column.</span></span>  
  
 <span data-ttu-id="5fdb7-105">若要了解這個工作，請參閱 [Web 服務工作](control-flow/web-service-task.md)。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-105">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5fdb7-106">選項。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-106">Options</span></span>  
 <span data-ttu-id="5fdb7-107">**服務**</span><span class="sxs-lookup"><span data-stu-id="5fdb7-107">**Service**</span></span>  
 <span data-ttu-id="5fdb7-108">從清單中選取要用於執行 Web 方法的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-108">Select a Web service from the list to use to execute the Web method.</span></span>  
  
 <span data-ttu-id="5fdb7-109">**方法**</span><span class="sxs-lookup"><span data-stu-id="5fdb7-109">**Method**</span></span>  
 <span data-ttu-id="5fdb7-110">從清單中選取要用於執行工作的 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-110">Select a Web method from the list for the task to execute.</span></span>  
  
 <span data-ttu-id="5fdb7-111">**WebMethodDocumentation**</span><span class="sxs-lookup"><span data-stu-id="5fdb7-111">**WebMethodDocumentation**</span></span>  
 <span data-ttu-id="5fdb7-112">鍵入 Web 方法的描述，或按一下瀏覽按鈕 **(...)** ，然後在 [Web 方法文件集]  對話方塊中鍵入描述。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-112">Type a description of Web method, or the click the browse button **(...)** and then type the description in the **Web Method Documentation** dialog box.</span></span>  
  
 <span data-ttu-id="5fdb7-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5fdb7-113">**Name**</span></span>  
 <span data-ttu-id="5fdb7-114">列出 Web 方法之輸入的名稱。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-114">Lists the names of the inputs to the Web method.</span></span>  
  
 <span data-ttu-id="5fdb7-115">**型別**</span><span class="sxs-lookup"><span data-stu-id="5fdb7-115">**Type**</span></span>  
 <span data-ttu-id="5fdb7-116">列出輸入的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-116">Lists the data type of the inputs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5fdb7-117">「Web 服務」工作只支援下列資料類型的參數：基本類型 (如整數和字串)、基本類型的陣列和順序以及列舉。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-117">The Web Service task supports parameters of the following data types only: primitive types such as integers and strings; arrays and sequences of primitive types; and enumerations.</span></span>  
  
 <span data-ttu-id="5fdb7-118">**變數**</span><span class="sxs-lookup"><span data-stu-id="5fdb7-118">**Variable**</span></span>  
 <span data-ttu-id="5fdb7-119">選取該核取方塊，即可使用變數來提供輸入。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-119">Select the check boxes to use variables to provide inputs.</span></span>  
  
 <span data-ttu-id="5fdb7-120">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="5fdb7-120">**Value**</span></span>  
 <span data-ttu-id="5fdb7-121">如果選取了 [變數] 核取方塊，請從清單中選取要用於提供輸入的變數，否則請直接輸入要用於輸入的值。</span><span class="sxs-lookup"><span data-stu-id="5fdb7-121">If the Variable check-boxes are selected, select the variables in the list to provide the inputs; otherwise, type the values to use in the inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdb7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fdb7-122">See Also</span></span>  
 <span data-ttu-id="5fdb7-123">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="5fdb7-123">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="5fdb7-124">[&#40;一般頁面&#41;的 Web 服務工作編輯器](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="5fdb7-124">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="5fdb7-125">[[Web 服務工作編輯器] &#40;[輸出] 頁面&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="5fdb7-125">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 [<span data-ttu-id="5fdb7-126">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="5fdb7-126">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
