---
title: == (等於) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- equal operator (==)
- == (equal operator)
ms.assetid: 36fd2354-7b93-4c95-9cf3-51ee24568950
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 12f92a267543c366dee4905010aeb84d93c4f408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701476"
---
# <a name="-equal-ssis-expression"></a><span data-ttu-id="c01d6-102">== (等於) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="c01d6-102">== (Equal) (SSIS Expression)</span></span>
  <span data-ttu-id="c01d6-103">執行比較來決定兩個運算式是否相等。</span><span class="sxs-lookup"><span data-stu-id="c01d6-103">Performs a comparison to determine if two expressions are equal.</span></span> <span data-ttu-id="c01d6-104">運算式評估工具會在執行比較之前，自動轉換許多資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-104">The expression evaluator automatically converts many data types before it performs the comparison.</span></span> <span data-ttu-id="c01d6-105">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-105">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
 <span data-ttu-id="c01d6-106">但是，某些資料類型要求運算式先包含明確轉換，才能成功評估運算式。</span><span class="sxs-lookup"><span data-stu-id="c01d6-106">However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully.</span></span> <span data-ttu-id="c01d6-107">如需在資料類型間合法轉換的詳細資訊，請參閱[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-107">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c01d6-108">語法</span><span class="sxs-lookup"><span data-stu-id="c01d6-108">Syntax</span></span>  
  
```  
  
expression1 == expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c01d6-109">引數</span><span class="sxs-lookup"><span data-stu-id="c01d6-109">Arguments</span></span>  
 <span data-ttu-id="c01d6-110">*expression1, expression2*</span><span class="sxs-lookup"><span data-stu-id="c01d6-110">*expression1, expression2*</span></span>  
 <span data-ttu-id="c01d6-111">為任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="c01d6-111">Is any valid expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c01d6-112">結果類型</span><span class="sxs-lookup"><span data-stu-id="c01d6-112">Result Types</span></span>  
 <span data-ttu-id="c01d6-113">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="c01d6-113">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c01d6-114">備註</span><span class="sxs-lookup"><span data-stu-id="c01d6-114">Remarks</span></span>  
 <span data-ttu-id="c01d6-115">如果比較中的任一個運算式為 Null，則比較結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="c01d6-115">If either expression in the comparison is null, the comparison result is null.</span></span> <span data-ttu-id="c01d6-116">如果兩個運算式都是 Null，結果則為 Null。</span><span class="sxs-lookup"><span data-stu-id="c01d6-116">If both expressions are null, the result is null.</span></span>  
  
 <span data-ttu-id="c01d6-117">運算式集 *expression1* 與 *expression2*必須遵循下列規則之一：</span><span class="sxs-lookup"><span data-stu-id="c01d6-117">The expression set, *expression1* and *expression2*, must follow one of these rules:</span></span>  
  
-   <span data-ttu-id="c01d6-118">**數值** — *expression1* 與 *expression2* 都必須是數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-118">**Numeric** Both *expression1* and *expression2* must be a numeric data type.</span></span> <span data-ttu-id="c01d6-119">資料類型的交集必須是運算式評估工具執行之隱含數值轉換規則中所指定的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-119">The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs.</span></span> <span data-ttu-id="c01d6-120">兩個數值資料類型的交集不能是 Null。</span><span class="sxs-lookup"><span data-stu-id="c01d6-120">The intersection of the two numeric data types cannot be null.</span></span> <span data-ttu-id="c01d6-121">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-121">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
-   <span data-ttu-id="c01d6-122">**字元** ： *expression1* 和 *expression2* 都必須評估為 DT_STR 或 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-122">**Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type.</span></span> <span data-ttu-id="c01d6-123">兩個運算式可以評估為不同的字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-123">The two expressions can evaluate to different string data types.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c01d6-124">字串比較有區分大小寫、腔調字、假名與全半形。</span><span class="sxs-lookup"><span data-stu-id="c01d6-124">String comparisons are case, accent, kana, and width-sensitive.</span></span>  
  
-   <span data-ttu-id="c01d6-125">**日期、時間或日期/時間** ： *expression1* 和 *expression2* 都必須評估為下列其中一種資料類型：DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET 或 DT_FILETIME。</span><span class="sxs-lookup"><span data-stu-id="c01d6-125">**Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c01d6-126">系統不支援評估為時間資料類型之運算式與評估為日期或日期/時間資料類型之運算式之間的比較。</span><span class="sxs-lookup"><span data-stu-id="c01d6-126">The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type.</span></span> <span data-ttu-id="c01d6-127">系統會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c01d6-127">The system generates an error.</span></span>  
  
     <span data-ttu-id="c01d6-128">比較運算式時，系統會以列出的順序套用下列轉換規則：</span><span class="sxs-lookup"><span data-stu-id="c01d6-128">When comparing the expressions, the system applies the following conversion rules in the order listed:</span></span>  
  
    -   <span data-ttu-id="c01d6-129">當兩個運算式評估為相同的資料類型時，會擲行該資料類型的比較。</span><span class="sxs-lookup"><span data-stu-id="c01d6-129">When the two expressions evaluate to the same data type, a comparison of that data type is performed.</span></span>  
  
    -   <span data-ttu-id="c01d6-130">如果一個運算式為 DT_DBTIMESTAMPOFFSET 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIMESTAMPOFFSET，而且會執行 DT_DBTIMESTAMPOFFSET 比較。</span><span class="sxs-lookup"><span data-stu-id="c01d6-130">If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed.</span></span> <span data-ttu-id="c01d6-131">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-131">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
    -   <span data-ttu-id="c01d6-132">如果一個運算式為 DT_DBTIMESTAMP2 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIMESTAMP2，而且會執行 DT_DBTIMESTAMP2 比較。</span><span class="sxs-lookup"><span data-stu-id="c01d6-132">If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="c01d6-133">如果一個運算式為 DT_DBTIME2 資料類型，另一個運算式會以隱含的方式轉換為 DT_DBTIME2，而且會執行 DT_DBTIME2 比較。</span><span class="sxs-lookup"><span data-stu-id="c01d6-133">If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.</span></span>  
  
    -   <span data-ttu-id="c01d6-134">如果一個運算式的類型不屬於 DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2 或 DT_DBTIME2，運算式會在進行比較前，轉換為 DT_DBTIMESTAMP 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-134">If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.</span></span>  
  
     <span data-ttu-id="c01d6-135">比較運算式時，系統會進行下列假設：</span><span class="sxs-lookup"><span data-stu-id="c01d6-135">When comparing the expressions, the system makes the following assumptions:</span></span>  
  
    -   <span data-ttu-id="c01d6-136">如果每個運算式都是包含毫秒的資料類型，系統會假設毫秒位數最少之資料類型的其餘位數為零。</span><span class="sxs-lookup"><span data-stu-id="c01d6-136">If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.</span></span>  
  
    -   <span data-ttu-id="c01d6-137">如果每個運算式都是日期資料類型，但是只有一個運算式具有時區時差，則系統會假設沒有時區時差的日期資料類型為 Coordinated Universal Time (UTC)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-137">If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).</span></span>  
  
-   <span data-ttu-id="c01d6-138">**邏輯** — *expression1* 與 *expression2* 都必須評估為布林。</span><span class="sxs-lookup"><span data-stu-id="c01d6-138">**Logical** Both *expression1* and *expression2* must evaluate to a Boolean.</span></span>  
  
-   <span data-ttu-id="c01d6-139">**GUID** ： *expression1* 和 *expression2* 都必須評估為 DT_GUID 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-139">**GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.</span></span>  
  
-   <span data-ttu-id="c01d6-140">**二進位** ： *expression1* 和 *expression2* 都必須評估為 DT_BYTES 資料類型。</span><span class="sxs-lookup"><span data-stu-id="c01d6-140">**Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.</span></span>  
  
-   <span data-ttu-id="c01d6-141">**BLOB** ： *expression1* 和 *expression2* 都必須評估為相同的二進位大型物件區塊 (BLOB) 資料類型：DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="c01d6-141">**BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="c01d6-142">如需有關資料類型的詳細資訊，請參閱＜ [Integration Services Data Types](../data-flow/integration-services-data-types.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c01d6-142">For more information about data types, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="c01d6-143">運算式範例</span><span class="sxs-lookup"><span data-stu-id="c01d6-143">Expression Examples</span></span>  
 <span data-ttu-id="c01d6-144">如果目前日期為 2003 年 7 月 4 日，則此範例評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c01d6-144">This example evaluates to TRUE if the current date is July 4, 2003.</span></span> <span data-ttu-id="c01d6-145">如需詳細資訊，請參閱 [GETDATE &#40;SSIS 運算式&#41;](getdate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-145">For more information, see [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="c01d6-146">"7/4/2003" == GETDATE()</span><span class="sxs-lookup"><span data-stu-id="c01d6-146">"7/4/2003" == GETDATE()</span></span>  
  
 <span data-ttu-id="c01d6-147">如果 **ListPrice** 資料行中的值為 500，則此範例評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c01d6-147">This example evaluates to TRUE if the value in the **ListPrice** column is 500.</span></span>  
  
```  
ListPrice == 500  
```  
  
 <span data-ttu-id="c01d6-148">這個範例使用變數 **LPrice**。</span><span class="sxs-lookup"><span data-stu-id="c01d6-148">This example uses the variable **LPrice**.</span></span> <span data-ttu-id="c01d6-149">如果 **LPrice** 的值為 500，則其評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c01d6-149">It evaluates to TRUE if the value of **LPrice** is 500.</span></span> <span data-ttu-id="c01d6-150">變數的資料類型必須是數值，運算式才能成功剖析。</span><span class="sxs-lookup"><span data-stu-id="c01d6-150">The data type of the variable must be numeric for the expression to parse successfully.</span></span>  
  
```  
@LPrice == 500  
```  
  
## <a name="see-also"></a><span data-ttu-id="c01d6-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c01d6-151">See Also</span></span>  
 <span data-ttu-id="c01d6-152">[\!= &#40;不等於&#41; &#40;SSIS 運算式&#41;](equal-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="c01d6-152">[!= &#40;Unequal&#41; &#40;SSIS Expression&#41;](equal-ssis-expression.md) </span></span>  
 <span data-ttu-id="c01d6-153">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="c01d6-153">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="c01d6-154">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="c01d6-154">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
