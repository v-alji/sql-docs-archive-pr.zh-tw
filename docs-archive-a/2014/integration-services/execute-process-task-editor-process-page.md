---
title: 執行處理工作編輯器 (進程頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce8629be2c07ae4caac4586b266936a908e71499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686457"
---
# <a name="execute-process-task-editor-process-page"></a><span data-ttu-id="e1d94-102">執行處理工作編輯器 (處理頁面)</span><span class="sxs-lookup"><span data-stu-id="e1d94-102">Execute Process Task Editor (Process Page)</span></span>
  <span data-ttu-id="e1d94-103">使用 **[執行處理工作編輯器]** 對話方塊的 **[處理]** 頁面，即可設定執行處理的選項。</span><span class="sxs-lookup"><span data-stu-id="e1d94-103">Use the **Process** page of the **Execute Process Task Editor** dialog box to configure the options that execute the process.</span></span> <span data-ttu-id="e1d94-104">這些選項包括要執行的可執行檔、其位置、命令提示字元引數，以及提供輸入和擷取輸出的變數。</span><span class="sxs-lookup"><span data-stu-id="e1d94-104">These options include the executable to run, its location, command prompt arguments, and the variables that provide input and capture output.</span></span>  
  
 <span data-ttu-id="e1d94-105">若要了解這個工作，請參閱＜ [Execute Process Task](control-flow/execute-process-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e1d94-105">To learn about this task, see [Execute Process Task](control-flow/execute-process-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e1d94-106">選項。</span><span class="sxs-lookup"><span data-stu-id="e1d94-106">Options</span></span>  
 <span data-ttu-id="e1d94-107">**RequireFullFileName**</span><span class="sxs-lookup"><span data-stu-id="e1d94-107">**RequireFullFileName**</span></span>  
 <span data-ttu-id="e1d94-108">指出如果在指定位置找不到可執行檔時，工作是否失敗。</span><span class="sxs-lookup"><span data-stu-id="e1d94-108">Indicate whether the task should fail if the executable is not found at the specified location.</span></span>  
  
 <span data-ttu-id="e1d94-109">**可執行檔**</span><span class="sxs-lookup"><span data-stu-id="e1d94-109">**Executable**</span></span>  
 <span data-ttu-id="e1d94-110">輸入要執行的可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="e1d94-110">Type the name of the executable to run.</span></span>  
  
 <span data-ttu-id="e1d94-111">**引數**</span><span class="sxs-lookup"><span data-stu-id="e1d94-111">**Arguments**</span></span>  
 <span data-ttu-id="e1d94-112">提供命令提示字元引數。</span><span class="sxs-lookup"><span data-stu-id="e1d94-112">Provide command prompt arguments.</span></span>  
  
 <span data-ttu-id="e1d94-113">**WorkingDirectory**</span><span class="sxs-lookup"><span data-stu-id="e1d94-113">**WorkingDirectory**</span></span>  
 <span data-ttu-id="e1d94-114">鍵入包含可執行檔的資料夾路徑，或按一下瀏覽按鈕 **(...)** 並尋找資料夾。</span><span class="sxs-lookup"><span data-stu-id="e1d94-114">Type the path of the folder that contains the executable, or click the browse button **(...)** and locate the folder.</span></span>  
  
 <span data-ttu-id="e1d94-115">**StandardInputVariable**</span><span class="sxs-lookup"><span data-stu-id="e1d94-115">**StandardInputVariable**</span></span>  
 <span data-ttu-id="e1d94-116">選取變數來提供處理序的輸入，或按一下 [\<**New variable...**>] 以建立新的變數：</span><span class="sxs-lookup"><span data-stu-id="e1d94-116">Select a variable to provide the input to the process, or click \<**New variable...**> to create a new variable:</span></span>  
  
 <span data-ttu-id="e1d94-117">**相關主題：**  [新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="e1d94-117">**Related Topics:**  [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="e1d94-118">**StandardOutputVariable**</span><span class="sxs-lookup"><span data-stu-id="e1d94-118">**StandardOutputVariable**</span></span>  
 <span data-ttu-id="e1d94-119">選取變數來擷取處理序的輸出，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="e1d94-119">Select a variable to capture the output of the process, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="e1d94-120">**StandardErrorVariable**</span><span class="sxs-lookup"><span data-stu-id="e1d94-120">**StandardErrorVariable**</span></span>  
 <span data-ttu-id="e1d94-121">選取變數來擷取處理器的錯誤輸出，或按一下 [\<**New variable...**>] 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="e1d94-121">Select a variable to capture the error output of the processor, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="e1d94-122">**FailTaskIfReturnCodeIsNotSuccessValue**</span><span class="sxs-lookup"><span data-stu-id="e1d94-122">**FailTaskIfReturnCodeIsNotSuccessValue**</span></span>  
 <span data-ttu-id="e1d94-123">指出如果處理序的結束碼和 **SuccessValue**中指定的值不同時，工作是否失敗。</span><span class="sxs-lookup"><span data-stu-id="e1d94-123">Indicate whether the task fails if the process exit code is different from the value specified in **SuccessValue**.</span></span>  
  
 <span data-ttu-id="e1d94-124">**SuccessValue**</span><span class="sxs-lookup"><span data-stu-id="e1d94-124">**SuccessValue**</span></span>  
 <span data-ttu-id="e1d94-125">指定可執行檔要表示成功時將傳回的值。</span><span class="sxs-lookup"><span data-stu-id="e1d94-125">Specify the value returned by the executable to indicate success.</span></span> <span data-ttu-id="e1d94-126">依預設，此值設定為 **0**。</span><span class="sxs-lookup"><span data-stu-id="e1d94-126">By default this value is set to **0**.</span></span>  
  
 <span data-ttu-id="e1d94-127">**TimeOut**</span><span class="sxs-lookup"><span data-stu-id="e1d94-127">**TimeOut**</span></span>  
 <span data-ttu-id="e1d94-128">指定處理序可以執行的秒數。</span><span class="sxs-lookup"><span data-stu-id="e1d94-128">Specify the number of seconds that the process can run.</span></span> <span data-ttu-id="e1d94-129">若值為 **0** ，表示不使用逾時值，則處理序會一直執行到完成或發生錯誤為止。</span><span class="sxs-lookup"><span data-stu-id="e1d94-129">A value of **0** indicates that no time-out value is used, and the process runs until it is completed or until an error occurs.</span></span>  
  
 <span data-ttu-id="e1d94-130">**TerminateProcessAfterTimeOut**</span><span class="sxs-lookup"><span data-stu-id="e1d94-130">**TerminateProcessAfterTimeOut**</span></span>  
 <span data-ttu-id="e1d94-131">指出是否要在 **TimeOut** 選項指定的逾時期限之後，強制結束處理序。</span><span class="sxs-lookup"><span data-stu-id="e1d94-131">Indicate whether the process is forced to end after the time-out period specified by the **TimeOut** option.</span></span> <span data-ttu-id="e1d94-132">只有在 **TimeOut** 不是 **0**時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="e1d94-132">This option is available only if **TimeOut** is not **0**.</span></span>  
  
 <span data-ttu-id="e1d94-133">**WindowStyle**</span><span class="sxs-lookup"><span data-stu-id="e1d94-133">**WindowStyle**</span></span>  
 <span data-ttu-id="e1d94-134">指定用來執行處理序的視窗樣式。</span><span class="sxs-lookup"><span data-stu-id="e1d94-134">Specify the window style in which to run the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d94-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d94-135">See Also</span></span>  
 <span data-ttu-id="e1d94-136">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e1d94-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="e1d94-137">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="e1d94-137">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
