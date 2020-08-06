---
title: 衍生的資料行轉換編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntransformation.f1
helpviewer_keywords:
- Derived Column Transformation Editor
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41a0f0dcd253473f78f2f38426b5fbd3d2ac2812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599610"
---
# <a name="derived-column-transformation-editor"></a><span data-ttu-id="11aca-102">衍生的資料行轉換編輯器</span><span class="sxs-lookup"><span data-stu-id="11aca-102">Derived Column Transformation Editor</span></span>
  <span data-ttu-id="11aca-103">使用 [衍生的資料行轉換編輯器]\*\*\*\* 對話方塊，即可建立會擴展新的資料行或取代資料行的運算式。</span><span class="sxs-lookup"><span data-stu-id="11aca-103">Use the **Derived Column Transformation Editor** dialog box to create expressions that populate new or replacement columns.</span></span>  
  
 <span data-ttu-id="11aca-104">若要深入了解「衍生的資料行」轉換，請參閱 [衍生的資料行轉換](data-flow/transformations/derived-column-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="11aca-104">To learn more about the Derived Column transformation, see [Derived Column Transformation](data-flow/transformations/derived-column-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="11aca-105">選項</span><span class="sxs-lookup"><span data-stu-id="11aca-105">Options</span></span>  
 <span data-ttu-id="11aca-106">**變數和資料行**</span><span class="sxs-lookup"><span data-stu-id="11aca-106">**Variables and Columns**</span></span>  
 <span data-ttu-id="11aca-107">將變數或資料行從可用之變數與資料行清單中拖曳至下面窗格中現有的資料表資料列，或是拖曳至清單底部的新資料列，即可建立使用變數或輸入資料行的運算式。</span><span class="sxs-lookup"><span data-stu-id="11aca-107">Build an expression that uses a variable or an input column by dragging the variable or column from the list of available variables and columns to an existing table row in the pane below, or to a new row at the bottom of the list.</span></span>  
  
 <span data-ttu-id="11aca-108">**函數和運算子**</span><span class="sxs-lookup"><span data-stu-id="11aca-108">**Functions and Operators**</span></span>  
 <span data-ttu-id="11aca-109">從清單中將函數和運算子拖曳至下面的窗格，即可建立使用函數或運算子來評估輸入資料與直接輸出資料的運算式。</span><span class="sxs-lookup"><span data-stu-id="11aca-109">Build an expression that uses a function or an operator to evaluate input data and direct output data by dragging functions and operators from the list to the pane below.</span></span>  
  
 <span data-ttu-id="11aca-110">**衍生的資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="11aca-110">**Derived Column Name**</span></span>  
 <span data-ttu-id="11aca-111">提供衍生的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="11aca-111">Provide a derived column name.</span></span> <span data-ttu-id="11aca-112">預設為衍生資料行的已編號清單；然而，您可以選擇任何唯一的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="11aca-112">The default is a numbered list of derived columns; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="11aca-113">**衍生的資料行**</span><span class="sxs-lookup"><span data-stu-id="11aca-113">**Derived Column**</span></span>  
 <span data-ttu-id="11aca-114">從清單中選取衍生的資料行。</span><span class="sxs-lookup"><span data-stu-id="11aca-114">Select a derived column from the list.</span></span> <span data-ttu-id="11aca-115">選擇是否要將衍生的資料行加入為新的輸出資料行，或是要取代現有資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="11aca-115">Choose whether to add the derived column as a new output column, or to replace the data in an existing column.</span></span>  
  
 <span data-ttu-id="11aca-116">**運算式**</span><span class="sxs-lookup"><span data-stu-id="11aca-116">**Expression**</span></span>  
 <span data-ttu-id="11aca-117">輸入運算式，或是從先前的可用資料行、變數、函數以及運算子清單中拖曳過來，以建立一個運算式。</span><span class="sxs-lookup"><span data-stu-id="11aca-117">Type an expression or build one by dragging from the previous list of available columns, variables, functions, and operators.</span></span>  
  
 <span data-ttu-id="11aca-118">此屬性的值可以使用屬性運算式指定。</span><span class="sxs-lookup"><span data-stu-id="11aca-118">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="11aca-119">**相關主題**︰[Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)、[運算子 &#40;SSIS 運算式&#41;](expressions/operators-ssis-expression.md)和[函數 &#40;SSIS 運算式&#41;](expressions/functions-ssis-expression.md)</span><span class="sxs-lookup"><span data-stu-id="11aca-119">**Related topics**: [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Operators &#40;SSIS Expression&#41;](expressions/operators-ssis-expression.md), and [Functions &#40;SSIS Expression&#41;](expressions/functions-ssis-expression.md)</span></span>  
  
 <span data-ttu-id="11aca-120">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="11aca-120">**Data Type**</span></span>  
 <span data-ttu-id="11aca-121">如果將資料加入新的資料行，[衍生的資料行轉換編輯器]\*\*\*\* 對話方塊就會自動評估運算式，並且適當設定資料類型。</span><span class="sxs-lookup"><span data-stu-id="11aca-121">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the data type appropriately.</span></span> <span data-ttu-id="11aca-122">這個資料行的值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="11aca-122">The value of this column is read-only.</span></span> <span data-ttu-id="11aca-123">如需詳細資訊，請參閱 [Integration Services 資料類型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="11aca-123">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="11aca-124">**長度**</span><span class="sxs-lookup"><span data-stu-id="11aca-124">**Length**</span></span>  
 <span data-ttu-id="11aca-125">如果將資料加入新的資料行，[衍生的資料行轉換編輯器]\*\*\*\* 對話方塊就會自動評估運算式，並且設定字串資料的資料行長度。</span><span class="sxs-lookup"><span data-stu-id="11aca-125">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the column length for string data.</span></span> <span data-ttu-id="11aca-126">這個資料行的值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="11aca-126">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="11aca-127">**有效位數**</span><span class="sxs-lookup"><span data-stu-id="11aca-127">**Precision**</span></span>  
 <span data-ttu-id="11aca-128">如果將資料加入新的資料行，[衍生的資料行轉換編輯器]\*\*\*\* 對話方塊就會自動根據資料類型來設定數值資料的有效位數。</span><span class="sxs-lookup"><span data-stu-id="11aca-128">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the precision for numeric data based on the data type.</span></span> <span data-ttu-id="11aca-129">這個資料行的值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="11aca-129">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="11aca-130">**縮放比例**</span><span class="sxs-lookup"><span data-stu-id="11aca-130">**Scale**</span></span>  
 <span data-ttu-id="11aca-131">如果將資料加入新的資料行，[衍生的資料行轉換編輯器]\*\*\*\* 對話方塊就會自動根據資料類型來設定數值資料的小數位數。</span><span class="sxs-lookup"><span data-stu-id="11aca-131">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the scale for numeric data based on the data type.</span></span> <span data-ttu-id="11aca-132">這個資料行的值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="11aca-132">The value of this column is read-only.</span></span>  
  
 <span data-ttu-id="11aca-133">**字碼頁**</span><span class="sxs-lookup"><span data-stu-id="11aca-133">**Code Page**</span></span>  
 <span data-ttu-id="11aca-134">如果將資料加入新的資料行，[衍生的資料行轉換編輯器]\*\*\*\* 對話方塊就會自動設定 DT_STR 資料類型的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="11aca-134">If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets code page for the DT_STR data type.</span></span> <span data-ttu-id="11aca-135">您可以更新 [字碼頁]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="11aca-135">You can update **Code Page**.</span></span>  
  
 <span data-ttu-id="11aca-136">**設定錯誤輸出**</span><span class="sxs-lookup"><span data-stu-id="11aca-136">**Configure error output**</span></span>  
 <span data-ttu-id="11aca-137">使用 [ [設定錯誤輸出](../../2014/integration-services/configure-error-output.md) ] 對話方塊來指定如何處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="11aca-137">Specify how to handle errors by using the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11aca-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11aca-138">See Also</span></span>  
 <span data-ttu-id="11aca-139">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="11aca-139">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="11aca-140">使用衍生的資料行轉換來衍生資料行值</span><span class="sxs-lookup"><span data-stu-id="11aca-140">Derive Column Values by Using the Derived Column Transformation</span></span>](data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  
