---
title: '? : (條件) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- conditional operator (?:)
- '?: (conditional operator)'
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e607f9ed495184ef47ac2e4f1139b9a9566055ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606432"
---
# <a name="--conditional-ssis-expression"></a><span data-ttu-id="ffdce-103">?</span><span class="sxs-lookup"><span data-stu-id="ffdce-103">?</span></span> <span data-ttu-id="ffdce-104">: (條件) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="ffdce-104">: (Conditional) (SSIS Expression)</span></span>
  <span data-ttu-id="ffdce-105">依據布林運算式的評估傳回兩個運算式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="ffdce-105">Returns one of two expressions based on the evaluation of a Boolean expression.</span></span> <span data-ttu-id="ffdce-106">如果布林運算式的評估結果為 TRUE，則會評估第一個運算式，且結果為運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="ffdce-106">If the Boolean expression evaluates to TRUE, then the first expression is evaluated and the result is the expression result.</span></span> <span data-ttu-id="ffdce-107">如果布林運算式的評估結果為 FALSE，則會評估第二個運算式，且其結果為運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="ffdce-107">If the Boolean expression evaluates to FALSE then the second expression is evaluated and its result is the expression result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdce-108">語法</span><span class="sxs-lookup"><span data-stu-id="ffdce-108">Syntax</span></span>  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ffdce-109">引數</span><span class="sxs-lookup"><span data-stu-id="ffdce-109">Arguments</span></span>  
 <span data-ttu-id="ffdce-110">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="ffdce-110">*boolean_expression*</span></span>  
 <span data-ttu-id="ffdce-111">評估為 TRUE、FALSE 或 NULL 的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="ffdce-111">Is any valid expression that evaluates to TRUE, FALSE, or NULL.</span></span>  
  
 <span data-ttu-id="ffdce-112">*expression1*</span><span class="sxs-lookup"><span data-stu-id="ffdce-112">*expression1*</span></span>  
 <span data-ttu-id="ffdce-113">為任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="ffdce-113">Is any valid expression.</span></span>  
  
 <span data-ttu-id="ffdce-114">*expression2*</span><span class="sxs-lookup"><span data-stu-id="ffdce-114">*expression2*</span></span>  
 <span data-ttu-id="ffdce-115">為任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="ffdce-115">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ffdce-116">結果類型</span><span class="sxs-lookup"><span data-stu-id="ffdce-116">Result Types</span></span>  
 <span data-ttu-id="ffdce-117">*expression1* 或 *expression2*的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffdce-117">The data type of *expression1* or *expression2*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffdce-118">備註</span><span class="sxs-lookup"><span data-stu-id="ffdce-118">Remarks</span></span>  
 <span data-ttu-id="ffdce-119">如果 *boolean_expression* 評估為 NULL，則運算式結果為 NULL。</span><span class="sxs-lookup"><span data-stu-id="ffdce-119">If the *boolean_expression* evaluates to NULL, the expression result is NULL.</span></span> <span data-ttu-id="ffdce-120">如果選取的運算式 ( *expression1* 或 *expression2* ) 為 NULL，則結果為 NULL。</span><span class="sxs-lookup"><span data-stu-id="ffdce-120">If a selected expression, either *expression1* or *expression2* is NULL, the result is NULL.</span></span> <span data-ttu-id="ffdce-121">如果選取的運算式不為 NULL，但未選取的運算式為 NULL，則結果為所選運算式的值。</span><span class="sxs-lookup"><span data-stu-id="ffdce-121">If a selected expression is not NULL, but the one not selected is NULL, the result is the value of the selected expression.</span></span>  
  
 <span data-ttu-id="ffdce-122">如果 *expression1* 和 *expression2* 的資料類型相同，則結果即為該資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffdce-122">If *expression1* and *expression2* have the same data type, the result is that data type.</span></span> <span data-ttu-id="ffdce-123">下列其他規則適用於結果類型：</span><span class="sxs-lookup"><span data-stu-id="ffdce-123">The following additional rules apply to result types:</span></span>  
  
-   <span data-ttu-id="ffdce-124">DT_TEXT 資料類型需要 *expression1* 和 *expression2* 擁有相同的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ffdce-124">The DT_TEXT data type requires that *expression1* and *expression2* have the same code page.</span></span>  
  
-   <span data-ttu-id="ffdce-125">DT_BYTES 資料類型的結果，其長度為較長引數的長度。</span><span class="sxs-lookup"><span data-stu-id="ffdce-125">The length of a result with the DT_BYTES data type is the length of the longer argument.</span></span>  
  
 <span data-ttu-id="ffdce-126">運算式組合 *expression1* 和 *expression2*必須評估為有效的資料類型並遵循下列其中一個規則：</span><span class="sxs-lookup"><span data-stu-id="ffdce-126">The expression set, *expression1* and *expression2*, must evaluate to valid data types and follow one of these rules:</span></span>  
  
-   <span data-ttu-id="ffdce-127">**數值** — *expression1* 與 *expression2* 都必須是數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffdce-127">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="ffdce-128">資料類型的交集必須是運算式評估工具執行之隱含數值轉換規則中所指定的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffdce-128">The intersection of the data types must be a numeric data type as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="ffdce-129">兩個數值資料類型的交集不能是 Null。</span><span class="sxs-lookup"><span data-stu-id="ffdce-129">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="ffdce-130">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ffdce-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="ffdce-131">\**字串\*\*\*expression1* 和 *expression2* 都必須是字串資料類型：DT_STR 或 DT_WSTR。</span><span class="sxs-lookup"><span data-stu-id="ffdce-131">**String** Both *expression1* and *expression2* must be a string data type: DT_STR or DT_WSTR.</span></span> <span data-ttu-id="ffdce-132">兩個運算式可以評估為不同的字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffdce-132">The two expressions can evaluate to different string data types.</span></span> <span data-ttu-id="ffdce-133">結果的資料類型為 DT_WSTR，且長度為較長引數的長度。</span><span class="sxs-lookup"><span data-stu-id="ffdce-133">The result has the DT_WSTR data type with a length of the longer argument.</span></span>  
  
-   <span data-ttu-id="ffdce-134">**日期、時間或日期/時間** ： *expression1* 和 *expression2* 都必須評估為下列其中一種資料類型：DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET 或 DT_FILETIME。</span><span class="sxs-lookup"><span data-stu-id="ffdce-134">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ffdce-135">系統不支援評估為時間資料類型之運算式與評估為日期或日期/時間資料類型之運算式之間的比較。</span><span class="sxs-lookup"><span data-stu-id="ffdce-135">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="ffdce-136">系統會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ffdce-136">The system generates an error.</span></span>  
  
     <span data-ttu-id="ffdce-137">比較運算式時，系統會以列出的順序套用下列轉換規則：</span><span class="sxs-lookup"><span data-stu-id="ffdce-137">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="ffdce-138">當兩個運算式評估為相同的資料類型時，會擲行該資料類型的比較。</span><span class="sxs-lookup"><span data-stu-id="ffdce-138">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="ffdce-139">如果一個運算式為 DT_DBTIMESTAMPOFFSET 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIMESTAMPOFFSET，而且會執行 DT_DBTIMESTAMPOFFSET 比較。</span><span class="sxs-lookup"><span data-stu-id="ffdce-139">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="ffdce-140">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ffdce-140">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="ffdce-141">如果一個運算式為 DT_DBTIMESTAMP2 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIMESTAMP2，而且會執行 DT_DBTIMESTAMP2 比較。</span><span class="sxs-lookup"><span data-stu-id="ffdce-141">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="ffdce-142">如果一個運算式為 DT_DBTIME2 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIME2，而且會執行 DT_DBTIME2 比較。</span><span class="sxs-lookup"><span data-stu-id="ffdce-142">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="ffdce-143">如果一個運算式的類型不屬於 DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2 或 DT_DBTIME2，運算式會在進行比較前，轉換為 DT_DBTIMESTAMP 資料類型。</span><span class="sxs-lookup"><span data-stu-id="ffdce-143">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="ffdce-144">比較運算式時，系統會進行下列假設：</span><span class="sxs-lookup"><span data-stu-id="ffdce-144">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="ffdce-145">如果每個運算式都是包含毫秒的資料類型，系統會假設毫秒位數最少之資料類型的其餘位數為零。</span><span class="sxs-lookup"><span data-stu-id="ffdce-145">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="ffdce-146">如果每個運算式都是日期資料類型，但是只有一個運算式具有時區時差，則系統會假設沒有時區時差的日期資料類型為 Coordinated Universal Time (UTC)。</span><span class="sxs-lookup"><span data-stu-id="ffdce-146">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
 <span data-ttu-id="ffdce-147">如需有關資料類型的詳細資訊，請參閱＜ [Integration Services Data Types](../data-flow/integration-services-data-types.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ffdce-147">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="ffdce-148">運算式範例</span><span class="sxs-lookup"><span data-stu-id="ffdce-148">Expression Examples</span></span>  
 <span data-ttu-id="ffdce-149">此範例顯示條件式地評估為 `savannah` 或 `unknown`的運算式。</span><span class="sxs-lookup"><span data-stu-id="ffdce-149">This example shows an expression that conditionally evaluates to `savannah` or `unknown`.</span></span>  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 <span data-ttu-id="ffdce-150">此範例顯示參考 **ListPrice** 資料行的運算式。</span><span class="sxs-lookup"><span data-stu-id="ffdce-150">This example shows an expression that references a **ListPrice** column.</span></span> <span data-ttu-id="ffdce-151">**ListPrice** 的資料類型為 DT_CY。</span><span class="sxs-lookup"><span data-stu-id="ffdce-151">**ListPrice** has the DT_CY data type.</span></span> <span data-ttu-id="ffdce-152">此運算式會條件式地將 **ListPrice** 乘以 .2 或 .1。</span><span class="sxs-lookup"><span data-stu-id="ffdce-152">The expression conditionally multiplies **ListPrice** by .2 or .1.</span></span>  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffdce-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffdce-153">See Also</span></span>  
 <span data-ttu-id="ffdce-154">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="ffdce-154">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="ffdce-155">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="ffdce-155">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
