---
title: 條件式分割轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.conditionalsplittrans.f1
helpviewer_keywords:
- Conditional Split transformation
- route rows to different outputs [Integration Services]
ms.assetid: 3f8b5825-226f-413c-ba8f-0bb931ca3770
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 96ff4b177992c329908ebc93df8f6220168e634d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597244"
---
# <a name="conditional-split-transformation"></a><span data-ttu-id="4438d-102">條件式分割轉換</span><span class="sxs-lookup"><span data-stu-id="4438d-102">Conditional Split Transformation</span></span>
  <span data-ttu-id="4438d-103">「條件式分割」轉換可根據資料的內容，將資料列傳送至不同的輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-103">The Conditional Split transformation can route data rows to different outputs depending on the content of the data.</span></span> <span data-ttu-id="4438d-104">條件式分割轉換的實作類似程式設計語言中的 CASE 決策結構。</span><span class="sxs-lookup"><span data-stu-id="4438d-104">The implementation of the Conditional Split transformation is similar to a CASE decision structure in a programming language.</span></span> <span data-ttu-id="4438d-105">轉換會評估運算式，並根據結果將資料列導向指定的輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-105">The transformation evaluates expressions, and based on the results, directs the data row to the specified output.</span></span> <span data-ttu-id="4438d-106">此轉換也提供預設輸出，因此若某個資料列不符合任何運算式，它會被導向到預設輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-106">This transformation also provides a default output, so that if a row matches no expression it is directed to the default output.</span></span>  
  
## <a name="configuration-of-the-conditional-split-transformation"></a><span data-ttu-id="4438d-107">設定條件式分割轉換</span><span class="sxs-lookup"><span data-stu-id="4438d-107">Configuration of the Conditional Split Transformation</span></span>  
 <span data-ttu-id="4438d-108">您可以利用下列方式設定「條件式分割」轉換：</span><span class="sxs-lookup"><span data-stu-id="4438d-108">You can configure the Conditional Split transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="4438d-109">針對您要讓轉換測試的每項條件，提供評估為布林的運算式。</span><span class="sxs-lookup"><span data-stu-id="4438d-109">Provide an expression that evaluates to a Boolean for each condition you want the transformation to test.</span></span>  
  
-   <span data-ttu-id="4438d-110">指定評估條件的順序。</span><span class="sxs-lookup"><span data-stu-id="4438d-110">Specify the order in which the conditions are evaluated.</span></span> <span data-ttu-id="4438d-111">順序相當重要，因為資料列會傳送至對應評估為 True 之第一項條件的輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-111">Order is significant, because a row is sent to the output corresponding to the first condition that evaluates to true.</span></span>  
  
-   <span data-ttu-id="4438d-112">指定轉換的預設輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-112">Specify the default output for the transformation.</span></span> <span data-ttu-id="4438d-113">轉換需要指定預設輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-113">The transformation requires that a default output be specified.</span></span>  
  
 <span data-ttu-id="4438d-114">每一個輸出資料列只能傳送至一項輸出，也就是評估為 True 之第一項條件的輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-114">Each input row can be sent to only one output, that being the output for the first condition that evaluates to true.</span></span> <span data-ttu-id="4438d-115">例如，下列條件會將 **FirstName** 資料行中任何以字母 *A* 開頭的資料列導向一項輸出，以字母 *B* 開頭的資料列導向另一項輸出，而其他所有資料列則導向預設輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-115">For example, the following conditions direct any rows in the **FirstName** column that begin with the letter *A* to one output, rows that begin with the letter *B* to a different output, and all other rows to the default output.</span></span>  
  
 <span data-ttu-id="4438d-116">輸出 1</span><span class="sxs-lookup"><span data-stu-id="4438d-116">Output 1</span></span>  
  
 `SUBSTRING(FirstName,1,1) == "A"`  
  
 <span data-ttu-id="4438d-117">輸出 2</span><span class="sxs-lookup"><span data-stu-id="4438d-117">Output 2</span></span>  
  
 `SUBSTRING(FirstName,1,1) == "B"`  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="4438d-118">包含各種函數和運算子，可用來建立評估輸入資料和導向輸出資料的運算式。</span><span class="sxs-lookup"><span data-stu-id="4438d-118">includes functions and operators that you can use to create the expressions that evaluate input data and direct output data.</span></span> <span data-ttu-id="4438d-119">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)為止。</span><span class="sxs-lookup"><span data-stu-id="4438d-119">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>  
  
 <span data-ttu-id="4438d-120">條件式分割轉換包括 `FriendlyExpression` 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="4438d-120">The Conditional Split transformation includes the `FriendlyExpression` custom property.</span></span> <span data-ttu-id="4438d-121">屬性運算式可以在載入封裝時更新這個屬性。</span><span class="sxs-lookup"><span data-stu-id="4438d-121">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="4438d-122">如需詳細資訊，請參閱 [在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md) 和 [轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4438d-122">For more information, see [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md) and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="4438d-123">此轉換擁有一項輸入、一項或多項輸出，以及一項錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="4438d-123">This transformation has one input, one or more outputs, and one error output.</span></span>  
  
 <span data-ttu-id="4438d-124">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4438d-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4438d-125">如需有關 **[條件式分割轉換編輯器]** 對話方塊中可設定屬性的詳細資訊，請參閱＜ [Conditional Split Transformation Editor](../../conditional-split-transformation-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4438d-125">For more information about the properties that you can set in the **Conditional Split Transformation Editor** dialog box, see [Conditional Split Transformation Editor](../../conditional-split-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="4438d-126">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之屬性。</span><span class="sxs-lookup"><span data-stu-id="4438d-126">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="4438d-127">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4438d-127">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4438d-128">Common Properties</span><span class="sxs-lookup"><span data-stu-id="4438d-128">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="4438d-129">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="4438d-129">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="4438d-130">如需有關如何設定屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4438d-130">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4438d-131">使用條件式分割轉換來分割資料集</span><span class="sxs-lookup"><span data-stu-id="4438d-131">Split a Dataset by Using the Conditional Split Transformation</span></span>](conditional-split-transformation.md)  
  
-   [<span data-ttu-id="4438d-132">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="4438d-132">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="4438d-133">相關工作</span><span class="sxs-lookup"><span data-stu-id="4438d-133">Related Tasks</span></span>  
 [<span data-ttu-id="4438d-134">使用條件式分割轉換來分割資料集</span><span class="sxs-lookup"><span data-stu-id="4438d-134">Split a Dataset by Using the Conditional Split Transformation</span></span>](conditional-split-transformation.md)  
  
## <a name="see-also"></a><span data-ttu-id="4438d-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4438d-135">See Also</span></span>  
 <span data-ttu-id="4438d-136">[資料流程](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="4438d-136">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="4438d-137">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="4438d-137">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
