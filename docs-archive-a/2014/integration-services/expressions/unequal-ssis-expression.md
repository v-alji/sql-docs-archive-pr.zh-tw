---
title: '!= (不等於) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- unequal operator (!=)
- '!= (not equal to)'
ms.assetid: fad20e85-c0e6-42bf-af70-2bc80ee09be5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be3eadbac77d76a2b3aac9555d9f40cb56e38949
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701320"
---
# <a name="-unequal-ssis-expression"></a><span data-ttu-id="16cd2-102">!= (不等於) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="16cd2-102">!= (Unequal) (SSIS Expression)</span></span>
  <span data-ttu-id="16cd2-103">執行比較來決定兩個資料類型相容的運算式是否不相等。</span><span class="sxs-lookup"><span data-stu-id="16cd2-103">Performs a comparison to determine if two expressions with compatible data types are not equal.</span></span> <span data-ttu-id="16cd2-104">運算式評估工具會在執行比較之前，自動轉換許多資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span>  
  
 <span data-ttu-id="16cd2-105">但是，某些資料類型要求運算式先包含明確轉換，才能成功評估運算式。</span><span class="sxs-lookup"><span data-stu-id="16cd2-105">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="16cd2-106">如需在資料類型間合法轉換的詳細資訊，請參閱[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="16cd2-106">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16cd2-107">語法</span><span class="sxs-lookup"><span data-stu-id="16cd2-107">Syntax</span></span>  
  
```  
  
expression1 != expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="16cd2-108">引數</span><span class="sxs-lookup"><span data-stu-id="16cd2-108">Arguments</span></span>  
 <span data-ttu-id="16cd2-109">*expression1, expression2*</span><span class="sxs-lookup"><span data-stu-id="16cd2-109">*expression1, expression2*</span></span>  
 <span data-ttu-id="16cd2-110">為任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="16cd2-110">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="16cd2-111">結果類型</span><span class="sxs-lookup"><span data-stu-id="16cd2-111">Result Types</span></span>  
 <span data-ttu-id="16cd2-112">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="16cd2-112">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16cd2-113">備註</span><span class="sxs-lookup"><span data-stu-id="16cd2-113">Remarks</span></span>  
 <span data-ttu-id="16cd2-114">如果比較中的任一個運算式為 Null，則比較結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="16cd2-114">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="16cd2-115">如果兩個運算式都是 Null，結果則為 Null。</span><span class="sxs-lookup"><span data-stu-id="16cd2-115">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="16cd2-116">運算式集 *expression1* 與 *expression2*必須遵循下列規則之一：</span><span class="sxs-lookup"><span data-stu-id="16cd2-116">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="16cd2-117">**數值** — *expression1* 與 *expression2* 都必須是數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-117">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="16cd2-118">資料類型的交集必須是運算式評估工具執行之隱含數值轉換規則中所指定的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-118">The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="16cd2-119">兩個數值資料類型的交集不能是 Null。</span><span class="sxs-lookup"><span data-stu-id="16cd2-119">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="16cd2-120">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="16cd2-120">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="16cd2-121">**字元** ： *expression1* 和 *expression2* 都必須評估為 DT_STR 或 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-121">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="16cd2-122">兩個運算式可以評估為不同的字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-122">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="16cd2-123">字串比較有區分大小寫、腔調字、假名與全半形。</span><span class="sxs-lookup"><span data-stu-id="16cd2-123">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="16cd2-124">**日期、時間或日期/時間** ： *expression1* 和 *expression2* 都必須評估為下列其中一種資料類型：DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET 或 DT_FILETIME。</span><span class="sxs-lookup"><span data-stu-id="16cd2-124">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="16cd2-125">系統不支援評估為時間資料類型之運算式與評估為日期或日期/時間資料類型之運算式之間的比較。</span><span class="sxs-lookup"><span data-stu-id="16cd2-125">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="16cd2-126">系統會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="16cd2-126">The system generates an error.</span></span>  
  
     <span data-ttu-id="16cd2-127">比較運算式時，系統會以列出的順序套用下列轉換規則：</span><span class="sxs-lookup"><span data-stu-id="16cd2-127">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="16cd2-128">當兩個運算式評估為相同的資料類型時，會擲行該資料類型的比較。</span><span class="sxs-lookup"><span data-stu-id="16cd2-128">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="16cd2-129">如果一個運算式為 DT_DBTIMESTAMPOFFSET 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIMESTAMPOFFSET，而且會執行 DT_DBTIMESTAMPOFFSET 比較。</span><span class="sxs-lookup"><span data-stu-id="16cd2-129">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="16cd2-130">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="16cd2-130">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="16cd2-131">如果一個運算式為 DT_DBTIMESTAMP2 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIMESTAMP2，而且會執行 DT_DBTIMESTAMP2 比較。</span><span class="sxs-lookup"><span data-stu-id="16cd2-131">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="16cd2-132">如果一個運算式為 DT_DBTIME2 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIME2，而且會執行 DT_DBTIME2 比較。</span><span class="sxs-lookup"><span data-stu-id="16cd2-132">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="16cd2-133">如果一個運算式的類型不屬於 DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2 或 DT_DBTIME2，運算式會在進行比較前，轉換為 DT_DBTIMESTAMP 資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-133">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="16cd2-134">比較運算式時，系統會進行下列假設：</span><span class="sxs-lookup"><span data-stu-id="16cd2-134">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="16cd2-135">如果每個運算式都是包含毫秒的資料類型，系統會假設毫秒位數最少之資料類型的其餘位數為零。</span><span class="sxs-lookup"><span data-stu-id="16cd2-135">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="16cd2-136">如果每個運算式都是日期資料類型，但是只有一個運算式具有時區時差，則系統會假設沒有時區時差的日期資料類型為 Coordinated Universal Time (UTC)。</span><span class="sxs-lookup"><span data-stu-id="16cd2-136">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
-   <span data-ttu-id="16cd2-137">**邏輯** — *expression1* 與 *expression2* 都必須評估為布林。</span><span class="sxs-lookup"><span data-stu-id="16cd2-137">**Logical** Both *expression1* and *expression2* must evaluate to a Boolean.</span></span>  
  
-   <span data-ttu-id="16cd2-138">**GUID** ： *expression1* 和 *expression2* 都必須評估為 DT_GUID 資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-138">**GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.</span></span>  
  
-   <span data-ttu-id="16cd2-139">**二進位** ： *expression1* 和 *expression2* 都必須評估為 DT_BYTES 資料類型。</span><span class="sxs-lookup"><span data-stu-id="16cd2-139">**Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.</span></span>  
  
-   <span data-ttu-id="16cd2-140">**BLOB** ： *expression1* 和 *expression2* 都必須評估為相同的二進位大型物件區塊 (BLOB) 資料類型：DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="16cd2-140">**BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="16cd2-141">如需有關資料類型的詳細資訊，請參閱＜ [Integration Services Data Types](../data-flow/integration-services-data-types.md)＞。</span><span class="sxs-lookup"><span data-stu-id="16cd2-141">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="16cd2-142">運算式範例</span><span class="sxs-lookup"><span data-stu-id="16cd2-142">Expression Examples</span></span>  
 <span data-ttu-id="16cd2-143">只有在目前日期不是 2003 年 7 月 4 日時，此範例的評估結果才會是 TRUE。</span><span class="sxs-lookup"><span data-stu-id="16cd2-143">This example evaluates to TRUE only if the current date is not July 4, 2003.</span></span> <span data-ttu-id="16cd2-144">如需詳細資訊，請參閱 [GETDATE &#40;SSIS 運算式&#41;](getdate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="16cd2-144">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
"7/4/2003" != GETDATE()  
```  
  
 <span data-ttu-id="16cd2-145">如果 **ListPrice** 資料行中的值不是 500，則此範例評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="16cd2-145">This example evaluates to TRUE if the value in the **ListPrice** column is not 500.</span></span>  
  
```  
ListPrice != 500  
```  
  
 <span data-ttu-id="16cd2-146">這個範例使用變數 **LPrice**。</span><span class="sxs-lookup"><span data-stu-id="16cd2-146">This example uses the variable **LPrice**.</span></span> <span data-ttu-id="16cd2-147">如果 **LPrice** 的值不是 500，則其評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="16cd2-147">It evaluates to TRUE if the value of **LPrice** is not 500.</span></span> <span data-ttu-id="16cd2-148">變數的資料類型必須是數值，運算式才能進行剖析。</span><span class="sxs-lookup"><span data-stu-id="16cd2-148">The data type on the variable must be numeric in order for the expression to parse.</span></span>  
  
```  
@LPrice != 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="16cd2-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16cd2-149">See Also</span></span>  
 <span data-ttu-id="16cd2-150">[== &#40;等於&#41; &#40;SSIS 運算式&#41;](equal-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="16cd2-150">[== &#40;Equal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md) </span></span>  
 <span data-ttu-id="16cd2-151">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="16cd2-151">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="16cd2-152">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="16cd2-152">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
