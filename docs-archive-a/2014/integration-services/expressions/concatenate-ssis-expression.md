---
title: + (串連) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1c01f82a50962f42862db836171b0ad683c97453
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701485"
---
# <a name="-concatenate-ssis-expression"></a><span data-ttu-id="ea7bf-102">+ (串連) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="ea7bf-102">+ (Concatenate) (SSIS Expression)</span></span>
  <span data-ttu-id="ea7bf-103">將兩個運算式串連成一個運算式。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-103">Concatenates two expressions into one expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea7bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea7bf-104">Syntax</span></span>  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ea7bf-105">引數</span><span class="sxs-lookup"><span data-stu-id="ea7bf-105">Arguments</span></span>  
 <span data-ttu-id="ea7bf-106">*expression1, expression2*</span><span class="sxs-lookup"><span data-stu-id="ea7bf-106">*expression1, expression2*</span></span>  
 <span data-ttu-id="ea7bf-107">是任何有效的 DT_STR、DT_WSTR、DT_TEXT、DT_NTEXT 或 DT_IMAGE 資料類型運算式。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-107">Is any valid DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ea7bf-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="ea7bf-108">Result Types</span></span>  
 <span data-ttu-id="ea7bf-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="ea7bf-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea7bf-110">備註</span><span class="sxs-lookup"><span data-stu-id="ea7bf-110">Remarks</span></span>  
 <span data-ttu-id="ea7bf-111">運算式可使用 DT_STR 和 DT_WSTR 資料類型的其中之一或兩者。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-111">The expression can use either or both of the DT_STR and DT_WSTR data types.</span></span>  
  
 <span data-ttu-id="ea7bf-112">串連 DT_STR 和 DT_WSTR 資料類型會傳回 DT_WSTR 類型的結果。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-112">The concatenation of the DT_STR and DT_WSTR data types returns a result of the DT_WSTR type.</span></span> <span data-ttu-id="ea7bf-113">字串長度是以字元表示的原始字串之長度總和。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-113">The length of the string is the sum of the lengths of the original strings expressed in characters.</span></span>  
  
 <span data-ttu-id="ea7bf-114">您只能串連具有字串資料類型 DT_STR 和 DT_WSTR 的資料，或是具有「二進位大型物件區塊」(BLOB) 資料類型 DT_TEXT、DT_NTEXT 和 DT_IMAGE 的資料。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-114">Only data with the string data types DT_STR and DT_WSTR or the Binary Large Object Block (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE can be concatenated.</span></span> <span data-ttu-id="ea7bf-115">在串連發生前，其他資料類型必須明確轉換成這些資料類型的其中之一。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-115">Other data types must be explicitly converted to one of these data types before concatenation occurs.</span></span> <span data-ttu-id="ea7bf-116">如需在資料類型間合法轉換的詳細資訊，請參閱[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-116">For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="ea7bf-117">兩個運算式的資料類型必須相同，或者其中一個運算式必須隱含轉換成另一個運算式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-117">Both expressions must be of the same data type, or one expression must be implicitly convertible to the data type of the other expression.</span></span> <span data-ttu-id="ea7bf-118">例如，如果串連 "Order date is " 字串和 **OrderDate** 資料行，則 **OrderDate** 中的值會隱含轉換成字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-118">For example, if the string "Order date is " and the column **OrderDate** are concatenated, the values in **OrderDate** are implicitly converted to a string data type.</span></span> <span data-ttu-id="ea7bf-119">若要串連兩個數值，這兩個數值都必須明確轉換成字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-119">To concatenate two numeric values, both numeric values must be explicitly cast to a string data type.</span></span>  
  
 <span data-ttu-id="ea7bf-120">串連只能使用一種 BLOB 資料類型：DT_TEXT、DT_NTEXT 或 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-120">A concatenation can use only one BLOB data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span>  
  
 <span data-ttu-id="ea7bf-121">如果任一元素為 Null，則結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-121">If either element is null, the result is null.</span></span>  
  
 <span data-ttu-id="ea7bf-122">字串常值必須以引號括住。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-122">String literals must be enclosed in quotation marks.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="ea7bf-123">運算式範例</span><span class="sxs-lookup"><span data-stu-id="ea7bf-123">Expression Examples</span></span>  
 <span data-ttu-id="ea7bf-124">此範例會串連 **FirstName** 和 **LastName** 資料行中的值，並在兩者之間插入空格。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-124">This example concatenates the values in the **FirstName** and **LastName** columns and inserts a space between them.</span></span>  
  
```  
FirstName + ' ' + LastName  
```  
  
 <span data-ttu-id="ea7bf-125">此範例會串連 **ZIPCode** 和 **ZIPCode+4**變數。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-125">This example concatenates the variables **ZIPCode** and **ZIPCode+4**.</span></span> <span data-ttu-id="ea7bf-126">兩個變數都具有字串資料類型。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-126">Both variables have a string data type.</span></span> <span data-ttu-id="ea7bf-127">**ZIPCode+4** 必須加上方括弧，這是因為變數名稱包含 + 字元。</span><span class="sxs-lookup"><span data-stu-id="ea7bf-127">**ZIPCode+4** must be enclosed in brackets because the variable name includes the + character.</span></span>  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea7bf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea7bf-128">See Also</span></span>  
 <span data-ttu-id="ea7bf-129">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="ea7bf-129">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="ea7bf-130">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="ea7bf-130">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
