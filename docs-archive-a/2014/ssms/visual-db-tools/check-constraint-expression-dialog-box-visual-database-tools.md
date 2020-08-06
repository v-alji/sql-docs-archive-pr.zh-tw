---
title: 檢查條件約束運算式對話方塊 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraintexpression
ms.assetid: beb6ce43-3913-4d66-8826-8e885335b790
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38268d4e49a9c674c100bc22c0782e3e61477967
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584239"
---
# <a name="check-constraint-expression-dialog-box-visual-database-tools"></a><span data-ttu-id="38ffd-102">檢查條件約束運算式對話方塊 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="38ffd-102">Check Constraint Expression Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="38ffd-103">當附加檢查條件約束至資料表或資料行時，必須包含 SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="38ffd-103">When you attach a check constraint to a table or column, you must include an SQL expression.</span></span> <span data-ttu-id="38ffd-104">在提供的方塊中輸入檢查條件約束運算式。</span><span class="sxs-lookup"><span data-stu-id="38ffd-104">Type the check constraint expression in the box provided.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="38ffd-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="38ffd-105">UI element list</span></span>  
 <span data-ttu-id="38ffd-106">運算是</span><span class="sxs-lookup"><span data-stu-id="38ffd-106">Expression</span></span>  
 <span data-ttu-id="38ffd-107">輸入運算式</span><span class="sxs-lookup"><span data-stu-id="38ffd-107">Enter the expression</span></span>  
  
 <span data-ttu-id="38ffd-108">您可以建立簡單的條件約束運算式以檢查簡單條件的資料，或是可以建立使用布林運算子的複雜運算式，檢查數種條件的資料。</span><span class="sxs-lookup"><span data-stu-id="38ffd-108">You can create a simple constraint expression to check data for a simple condition; or you can create a complex expression, using Boolean operators, to check data for several conditions.</span></span> <span data-ttu-id="38ffd-109">例如，假設 authors 資料表有 zip 資料行，而其中需要 5 位數的字串。</span><span class="sxs-lookup"><span data-stu-id="38ffd-109">For example, suppose the authors table has a zip column where a 5-digit character string is required.</span></span> <span data-ttu-id="38ffd-110">這個簡單的條件約束運算式保證只會允許 5 位數的資料：</span><span class="sxs-lookup"><span data-stu-id="38ffd-110">This sample constraint expression guarantees that only 5-digit numbers are allowed:</span></span>  
  
```  
zip LIKE '[0-9][0-9][0-9][0-9][0-9]'  
```  
  
 <span data-ttu-id="38ffd-111">或者，假設銷售資料表有名為 qty 的資料行，該資料航需要大於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="38ffd-111">Or suppose the sales table has a column called qty which requires a value greater than 0.</span></span> <span data-ttu-id="38ffd-112">這個簡單的條件約束保證只會允許正值：</span><span class="sxs-lookup"><span data-stu-id="38ffd-112">This sample constraint guarantees that only positive values are allowed:</span></span>  
  
```  
qty > 0  
```  
  
 <span data-ttu-id="38ffd-113">或假設 orders 資料表限制所有信用卡訂單所接受的信用卡類型。</span><span class="sxs-lookup"><span data-stu-id="38ffd-113">Or suppose the orders table limits the type of credit cards accepted for all credit card orders.</span></span> <span data-ttu-id="38ffd-114">則這個範例條件約束保證如果是使用信用卡進行訂購，則只接受 Visa、MasterCard 或 American Express：</span><span class="sxs-lookup"><span data-stu-id="38ffd-114">This sample constraint guarantees that if the order is placed on a credit card, then only Visa, MasterCard, or American Express is accepted:</span></span>  
  
```  
NOT (payment_method = 'credit card') OR  
   (card_type IN ('VISA', 'MASTERCARD', 'AMERICAN EXPRESS'))  
```  
  
## <a name="to-define-a-constraint-expression"></a><span data-ttu-id="38ffd-115">若要定義條件約束運算式</span><span class="sxs-lookup"><span data-stu-id="38ffd-115">To define a constraint expression</span></span>  
 <span data-ttu-id="38ffd-116">在屬性頁面的 [檢查條件約束] 索引標籤中，使用下列語法，在 [檢查條件約束運算式] 方塊中輸入運算式：</span><span class="sxs-lookup"><span data-stu-id="38ffd-116">In the Check Constraints tab of the property pages, type an expression in the Constraint expression box using the following syntax:</span></span>  
  
 `{constant | column_name | function | (subquery)}`  
  
 `[{operator | AND | OR | NOT}`  
  
 `{constant | column_name | function | (subquery)}...]`  
  
 <span data-ttu-id="38ffd-117">SQL 語法是由下列參數組成：</span><span class="sxs-lookup"><span data-stu-id="38ffd-117">The SQL syntax is made up of the following parameters:</span></span>  
  
|<span data-ttu-id="38ffd-118">參數</span><span class="sxs-lookup"><span data-stu-id="38ffd-118">Parameter</span></span>|<span data-ttu-id="38ffd-119">描述</span><span class="sxs-lookup"><span data-stu-id="38ffd-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38ffd-120">常數</span><span class="sxs-lookup"><span data-stu-id="38ffd-120">constant</span></span>|<span data-ttu-id="38ffd-121">常值，例如數值或字元資料。</span><span class="sxs-lookup"><span data-stu-id="38ffd-121">A literal value, such as numeric or character data.</span></span> <span data-ttu-id="38ffd-122">字元資料必須使用單引號 (') 括起來。</span><span class="sxs-lookup"><span data-stu-id="38ffd-122">Character data must be enclosed within single quotation marks (').</span></span>|  
|<span data-ttu-id="38ffd-123">column_name</span><span class="sxs-lookup"><span data-stu-id="38ffd-123">column_name</span></span>|<span data-ttu-id="38ffd-124">指定資料行。</span><span class="sxs-lookup"><span data-stu-id="38ffd-124">Specifies a column.</span></span>|  
|<span data-ttu-id="38ffd-125">函數</span><span class="sxs-lookup"><span data-stu-id="38ffd-125">function</span></span>|<span data-ttu-id="38ffd-126">內建函數。</span><span class="sxs-lookup"><span data-stu-id="38ffd-126">A built-in function.</span></span>|  
|<span data-ttu-id="38ffd-127">! 運算子之後</span><span class="sxs-lookup"><span data-stu-id="38ffd-127">operator</span></span>|<span data-ttu-id="38ffd-128">算術、位元、比較或字串運算子。</span><span class="sxs-lookup"><span data-stu-id="38ffd-128">Arithmetic, bitwise, comparison, or string operators.</span></span>|  
|<span data-ttu-id="38ffd-129">AND</span><span class="sxs-lookup"><span data-stu-id="38ffd-129">AND</span></span>|<span data-ttu-id="38ffd-130">使用於布林運算式中，用於連接兩個運算式。</span><span class="sxs-lookup"><span data-stu-id="38ffd-130">Use in Boolean expressions to connect two expressions.</span></span> <span data-ttu-id="38ffd-131">當兩個運算式都是 true 時傳回結果。</span><span class="sxs-lookup"><span data-stu-id="38ffd-131">Results are returned when both expressions are true.</span></span><br /><br /> <span data-ttu-id="38ffd-132">當 AND 和 OR 同時在陳述式中使用時，會先處理 AND。</span><span class="sxs-lookup"><span data-stu-id="38ffd-132">When AND and OR are both used in a statement, AND is processed first.</span></span> <span data-ttu-id="38ffd-133">您可以使用括號來變更執行的順序。</span><span class="sxs-lookup"><span data-stu-id="38ffd-133">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="38ffd-134">OR</span><span class="sxs-lookup"><span data-stu-id="38ffd-134">OR</span></span>|<span data-ttu-id="38ffd-135">使用於布林運算式中，用於連接兩個條件。</span><span class="sxs-lookup"><span data-stu-id="38ffd-135">Use in Boolean expressions to connect two or more conditions.</span></span> <span data-ttu-id="38ffd-136">當任一條件為 true 時，傳回結果。</span><span class="sxs-lookup"><span data-stu-id="38ffd-136">Results are returned when either condition is true.</span></span><br /><br /> <span data-ttu-id="38ffd-137">當 AND 和 OR 同時在陳述式中使用時，OR 是在 AND 之後進行檢驗。</span><span class="sxs-lookup"><span data-stu-id="38ffd-137">When AND and OR are both used in a statement, OR is evaluated after AND.</span></span> <span data-ttu-id="38ffd-138">您可以使用括號來變更執行的順序。</span><span class="sxs-lookup"><span data-stu-id="38ffd-138">You can change the order of execution by using parentheses.</span></span>|  
|<span data-ttu-id="38ffd-139">NOT</span><span class="sxs-lookup"><span data-stu-id="38ffd-139">NOT</span></span>|<span data-ttu-id="38ffd-140">否定任何布林運算式 (可以包括關鍵字，例如 LIKE、NULL、BETWEEN、IN 和 EXISTS)。</span><span class="sxs-lookup"><span data-stu-id="38ffd-140">Negates any Boolean expression (which can include keywords, such as LIKE, NULL, BETWEEN, IN, and EXISTS).</span></span><br /><br /> <span data-ttu-id="38ffd-141">當在陳述式中使用一個以上的邏輯運算子時，會首先處理 NOT。</span><span class="sxs-lookup"><span data-stu-id="38ffd-141">When more than one logical operator is used in a statement, NOT is processed first.</span></span> <span data-ttu-id="38ffd-142">您可以使用括號來變更執行的順序。</span><span class="sxs-lookup"><span data-stu-id="38ffd-142">You can change the order of execution by using parentheses.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38ffd-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38ffd-143">See Also</span></span>  
 <span data-ttu-id="38ffd-144">[Unique 條件約束和 Check 條件約束](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="38ffd-144">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="38ffd-145">建立唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="38ffd-145">Create Unique Constraints</span></span>](../../relational-databases/tables/create-unique-constraints.md)  
  
  
