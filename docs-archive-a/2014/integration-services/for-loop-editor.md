---
title: For 迴圈編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainer.f1
ms.assetid: c4db9df6-d2f4-44da-9f4d-628893e86956
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b610805808e0f392e675ad79f16d2d39886c7f70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592138"
---
# <a name="for-loop-editor"></a><span data-ttu-id="9afd0-102">For 迴圈編輯器</span><span class="sxs-lookup"><span data-stu-id="9afd0-102">For Loop Editor</span></span>
  <span data-ttu-id="9afd0-103">使用 **[For 迴圈編輯器]** 對話方塊的 **[For 迴圈]** 頁面，即可設定迴圈，使工作流程重複到指定的條件評估為 False 為止。</span><span class="sxs-lookup"><span data-stu-id="9afd0-103">Use the **For Loop** page of the **For Loop Editor** dialog box to configure a loop that repeats a workflow until a specified condition evaluates to false.</span></span>  
  
 <span data-ttu-id="9afd0-104">若要了解 For 迴圈容器以及如何在封裝中使用該容器，請參閱＜ [For Loop Container](control-flow/for-loop-container.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9afd0-104">To learn about the For Loop container and how to use it in packages, see [For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9afd0-105">選項。</span><span class="sxs-lookup"><span data-stu-id="9afd0-105">Options</span></span>  
 <span data-ttu-id="9afd0-106">**InitExpression**</span><span class="sxs-lookup"><span data-stu-id="9afd0-106">**InitExpression**</span></span>  
 <span data-ttu-id="9afd0-107">選擇性地提供運算式，以初始化迴圈使用的值。</span><span class="sxs-lookup"><span data-stu-id="9afd0-107">Optionally, provide an expression that initializes values used by the loop.</span></span>  
  
 <span data-ttu-id="9afd0-108">**EvalExpression**</span><span class="sxs-lookup"><span data-stu-id="9afd0-108">**EvalExpression**</span></span>  
 <span data-ttu-id="9afd0-109">提供運算式以評估迴圈應停止或繼續。</span><span class="sxs-lookup"><span data-stu-id="9afd0-109">Provide an expression to evaluate whether the loop should stop or continue.</span></span>  
  
 <span data-ttu-id="9afd0-110">**AssignExpression**</span><span class="sxs-lookup"><span data-stu-id="9afd0-110">**AssignExpression**</span></span>  
 <span data-ttu-id="9afd0-111">選擇性地提供運算式，在每次迴圈重複時就變更條件。</span><span class="sxs-lookup"><span data-stu-id="9afd0-111">Optionally, provide an expression that changes a condition each time that the loop repeats.</span></span>  
  
 <span data-ttu-id="9afd0-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="9afd0-112">**Name**</span></span>  
 <span data-ttu-id="9afd0-113">提供 For 迴圈容器的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9afd0-113">Provide a unique name for the For Loop container.</span></span> <span data-ttu-id="9afd0-114">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="9afd0-114">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9afd0-115">物件名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9afd0-115">Object names must be unique within a package.</span></span>  
  
 <span data-ttu-id="9afd0-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="9afd0-116">**Description**</span></span>  
 <span data-ttu-id="9afd0-117">提供 For 迴圈容器的描述。</span><span class="sxs-lookup"><span data-stu-id="9afd0-117">Provide a description of the For Loop container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9afd0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9afd0-118">See Also</span></span>  
 <span data-ttu-id="9afd0-119">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9afd0-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9afd0-120">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="9afd0-120">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="9afd0-121">[Foreach 迴圈容器](control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="9afd0-121">[Foreach Loop Container](control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="9afd0-122">設定 For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="9afd0-122">Configure a For Loop Container</span></span>](../../2014/integration-services/configure-a-for-loop-container.md)  
  
  
