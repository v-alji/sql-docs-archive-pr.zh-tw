---
title: 條件式分割轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittransformation.f1
helpviewer_keywords:
- Conditional Split Transformation Editor
ms.assetid: c30e1633-537a-4837-9991-6203c6f2a21e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 386a93eb7c3058c7c3e98f2b652199d115d841f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592173"
---
# <a name="conditional-split-transformation-editor"></a><span data-ttu-id="acb18-102">條件式分割轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="acb18-102">Conditional Split Transformation Editor</span></span>
  <span data-ttu-id="acb18-103">使用 **[條件式分割轉換編輯器]** 對話方塊，即可建立運算式、設定評估運算式的順序，以及命名條件式分割的輸出。</span><span class="sxs-lookup"><span data-stu-id="acb18-103">Use the **Conditional Split Transformation Editor** dialog box to create expressions, set the order in which expressions are evaluated, and name the outputs of a conditional split.</span></span> <span data-ttu-id="acb18-104">此對話方塊包含可用來建立運算式的數學、字串，以及日期/時間函數與運算子。</span><span class="sxs-lookup"><span data-stu-id="acb18-104">This dialog box includes mathematical, string, and date/time functions and operators that you can use to build expressions.</span></span> <span data-ttu-id="acb18-105">評估為 True 的第一個條件會決定資料列的輸出導向。</span><span class="sxs-lookup"><span data-stu-id="acb18-105">The first condition that evaluates as true determines the output to which a row is directed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="acb18-106">條件式分割轉換會將每個輸入資料列導向至單一輸出。</span><span class="sxs-lookup"><span data-stu-id="acb18-106">The Conditional Split transformation directs each input row to one output only.</span></span> <span data-ttu-id="acb18-107">如果輸入多重條件，轉換會將每個資料列傳送到條件為 True 的第一個輸出，而略過該資料列後續的條件。</span><span class="sxs-lookup"><span data-stu-id="acb18-107">If you enter multiple conditions, the transformation sends each row to the first output for which the condition is true and disregards subsequent conditions for that row.</span></span> <span data-ttu-id="acb18-108">如果您需要連續評估數個條件，就可能需要在資料流程中串連多重條件式分割轉換。</span><span class="sxs-lookup"><span data-stu-id="acb18-108">If you need to evaluate several conditions successively, you may need to concatenate multiple Conditional Split transformations in the data flow.</span></span>  
  
 <span data-ttu-id="acb18-109">若要深入了解條件式分割轉換，請參閱 [條件式分割轉換](data-flow/transformations/conditional-split-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="acb18-109">To learn more about the Conditional Split transformation, see [Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="acb18-110">選項</span><span class="sxs-lookup"><span data-stu-id="acb18-110">Options</span></span>  
 <span data-ttu-id="acb18-111">**順序**</span><span class="sxs-lookup"><span data-stu-id="acb18-111">**Order**</span></span>  
 <span data-ttu-id="acb18-112">選取資料列並使用右邊的方向鍵來變更評估運算式的順序。</span><span class="sxs-lookup"><span data-stu-id="acb18-112">Select a row and use the arrow keys at right to change the order in which to evaluate expressions.</span></span>  
  
 <span data-ttu-id="acb18-113">**輸出名稱**</span><span class="sxs-lookup"><span data-stu-id="acb18-113">**Output Name**</span></span>  
 <span data-ttu-id="acb18-114">提供輸出名稱。</span><span class="sxs-lookup"><span data-stu-id="acb18-114">Provide an output name.</span></span> <span data-ttu-id="acb18-115">預設為已編號的案例清單；然而，您可選擇任何唯一的、描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="acb18-115">The default is a numbered list of cases; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="acb18-116">**條件**</span><span class="sxs-lookup"><span data-stu-id="acb18-116">**Condition**</span></span>  
 <span data-ttu-id="acb18-117">輸入運算式或從可用的資料行、變數、函數以及運算子的清單中拖曳來建立運算式。</span><span class="sxs-lookup"><span data-stu-id="acb18-117">Type an expression or build one by dragging from the list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="acb18-118">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="acb18-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="acb18-119">**相關主題︰**  [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)[運算子 &#40;SSIS 運算式&#41;](expressions/operators-ssis-expression.md)和[函數 &#40;SSIS 運算式&#41;](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="acb18-119">**Related topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="acb18-120">**預設輸出名稱**</span><span class="sxs-lookup"><span data-stu-id="acb18-120">**Default output name**</span></span>  
 <span data-ttu-id="acb18-121">輸入預設輸出的名稱，或使用預設值。</span><span class="sxs-lookup"><span data-stu-id="acb18-121">Type a name for the default output, or use the default.</span></span>  
  
 <span data-ttu-id="acb18-122">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="acb18-122">**Configure error output**</span></span>  
 <span data-ttu-id="acb18-123">使用 [ [設定錯誤輸出](../../2014/integration-services/configure-error-output.md) ] 對話方塊來指定如何處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="acb18-123">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb18-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acb18-124">See Also</span></span>  
 <span data-ttu-id="acb18-125">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="acb18-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="acb18-126">使用條件式分割轉換來分割資料集</span><span class="sxs-lookup"><span data-stu-id="acb18-126">Split a Dataset by Using the Conditional Split Transformation</span></span>](data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
