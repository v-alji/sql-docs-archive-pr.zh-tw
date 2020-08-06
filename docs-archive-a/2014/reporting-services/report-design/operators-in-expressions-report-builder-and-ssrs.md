---
title: 運算式中的運算子 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d22dc8b6-4353-40e7-91a1-65e8dae6325d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa8042df39e535425a05414c1e39ee6a12ff2f39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595734"
---
# <a name="operators-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="17f92-102">運算式中的運算子 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="17f92-102">Operators in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="17f92-103">運算子是一個符號，代表套用至運算式中一個或多個詞彙的動作。</span><span class="sxs-lookup"><span data-stu-id="17f92-103">An operator is a symbol that represents actions applied to one or more terms in an expression.</span></span> <span data-ttu-id="17f92-104">在運算式中支援下列的運算子類別：算術、比較、串連、邏輯或位元，以及位元移位。</span><span class="sxs-lookup"><span data-stu-id="17f92-104">The following categories of operators are supported in an expression: arithmetic, comparison, concatenation, logical or bitwise, and bit shift.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="arithmetic"></a><span data-ttu-id="17f92-105">算術</span><span class="sxs-lookup"><span data-stu-id="17f92-105">Arithmetic</span></span>  
 <span data-ttu-id="17f92-106">算術運算子會針對運算式中的兩個數值詞彙執行數學運算。</span><span class="sxs-lookup"><span data-stu-id="17f92-106">Arithmetic operators perform mathematical operations on two numeric terms in an expression.</span></span>  
  
|<span data-ttu-id="17f92-107">運算子</span><span class="sxs-lookup"><span data-stu-id="17f92-107">Operator</span></span>|<span data-ttu-id="17f92-108">描述</span><span class="sxs-lookup"><span data-stu-id="17f92-108">Description</span></span>|  
|--------------|-----------------|  
|^|<span data-ttu-id="17f92-109">將一數值對另一數值做乘冪運算。</span><span class="sxs-lookup"><span data-stu-id="17f92-109">Raises a number to the power of another number.</span></span>|  
|*|<span data-ttu-id="17f92-110">兩個數目相乘。</span><span class="sxs-lookup"><span data-stu-id="17f92-110">Multiplies two numbers.</span></span>|  
|/|<span data-ttu-id="17f92-111">兩數相除並傳回浮點結果。</span><span class="sxs-lookup"><span data-stu-id="17f92-111">Divides two numbers and returns a floating-point result.</span></span>|  
|<span data-ttu-id="17f92-112">\|兩數相除並傳回整數結果。</span><span class="sxs-lookup"><span data-stu-id="17f92-112">\|Divides two numbers and returns an integer result.</span></span>|  
|<span data-ttu-id="17f92-113">Mod</span><span class="sxs-lookup"><span data-stu-id="17f92-113">Mod</span></span>|<span data-ttu-id="17f92-114">傳回除法的整數餘數。</span><span class="sxs-lookup"><span data-stu-id="17f92-114">Returns the integer remainder of a division.</span></span> <span data-ttu-id="17f92-115">例如，7 Mod 5 = 2，因為 7 除以 5 的餘數是 2。</span><span class="sxs-lookup"><span data-stu-id="17f92-115">For example, 7 Mod 5 = 2 because the remainder of 7 divided by 5 is 2.</span></span>|  
|+|<span data-ttu-id="17f92-116">將兩個數目相加。</span><span class="sxs-lookup"><span data-stu-id="17f92-116">Adds two numbers together.</span></span>|  
|-|<span data-ttu-id="17f92-117">傳回兩個數值運算式之間的差異，或指出數值詞彙的負值。</span><span class="sxs-lookup"><span data-stu-id="17f92-117">Returns the difference between two numbers or indicates the negative value of a numeric term.</span></span>|  
  
### <a name="comparison"></a><span data-ttu-id="17f92-118">比較</span><span class="sxs-lookup"><span data-stu-id="17f92-118">Comparison</span></span>  
 <span data-ttu-id="17f92-119">比較運算子用來測試兩個運算式是否相同。</span><span class="sxs-lookup"><span data-stu-id="17f92-119">Comparison operators test whether two expressions are the same.</span></span>  
  
|<span data-ttu-id="17f92-120">運算子</span><span class="sxs-lookup"><span data-stu-id="17f92-120">Operator</span></span>|<span data-ttu-id="17f92-121">描述</span><span class="sxs-lookup"><span data-stu-id="17f92-121">Description</span></span>|  
|--------------|-----------------|  
|<|<span data-ttu-id="17f92-122">小於。</span><span class="sxs-lookup"><span data-stu-id="17f92-122">Less than.</span></span>|  
|\<=|<span data-ttu-id="17f92-123">小於或等於。</span><span class="sxs-lookup"><span data-stu-id="17f92-123">Less than or equal to.</span></span>|  
|>|<span data-ttu-id="17f92-124">大於。</span><span class="sxs-lookup"><span data-stu-id="17f92-124">Greater than.</span></span>|  
|>=|<span data-ttu-id="17f92-125">大於或等於。</span><span class="sxs-lookup"><span data-stu-id="17f92-125">Greater than or equal to.</span></span>|  
|=|<span data-ttu-id="17f92-126">等於。</span><span class="sxs-lookup"><span data-stu-id="17f92-126">Equal to.</span></span>|  
|<>|<span data-ttu-id="17f92-127">不等於。</span><span class="sxs-lookup"><span data-stu-id="17f92-127">Not equal to.</span></span>|  
|<span data-ttu-id="17f92-128">相似</span><span class="sxs-lookup"><span data-stu-id="17f92-128">Like</span></span>|<span data-ttu-id="17f92-129">判斷特定字元字串是否符合指定的模式。</span><span class="sxs-lookup"><span data-stu-id="17f92-129">Determines whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="17f92-130">模式中可以包含一般字元及萬用字元。</span><span class="sxs-lookup"><span data-stu-id="17f92-130">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="17f92-131">在模式比對期間，一般字元必須與字元字串中所指定的字元完全相符。</span><span class="sxs-lookup"><span data-stu-id="17f92-131">During pattern matching, regular characters must exactly match the characters specified in the character string.</span></span> <span data-ttu-id="17f92-132">不過，萬用字元可以符合任意字元字串片段。</span><span class="sxs-lookup"><span data-stu-id="17f92-132">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="17f92-133">使用萬用字元要比使用 = 與 != 字串比較運算子能讓 LIKE 運算子更有彈性。</span><span class="sxs-lookup"><span data-stu-id="17f92-133">Using wildcard characters makes the LIKE operator more flexible than using the = and != string comparison operators.</span></span><br /><br /> <span data-ttu-id="17f92-134">下列列出可當做萬用字元使用的字元：</span><span class="sxs-lookup"><span data-stu-id="17f92-134">The following lists characters that can be used as wildcards:</span></span><br /><br /> <span data-ttu-id="17f92-135">**%**：任何零或多個字元的字串。</span><span class="sxs-lookup"><span data-stu-id="17f92-135">**%**: Any string of zero or more characters.</span></span><br /><br /> <span data-ttu-id="17f92-136">**_**：任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="17f92-136">**_**: Any single character.</span></span><br /><br /> <span data-ttu-id="17f92-137">**[]**：指定範圍內的任何單一字元 (例如，[a-f] ) 或設定 (例如 [aeiou] ) 。</span><span class="sxs-lookup"><span data-stu-id="17f92-137">**[ ]**: Any single character within the specified range (for example, [a-f]) or set (for example, [aeiou]).</span></span><br /><br /> <span data-ttu-id="17f92-138">**[^]**：不在指定範圍內的任何單一字元 (例如 [^ a-f] ) 或設定 (例如 [^ aeiou] ) 。</span><span class="sxs-lookup"><span data-stu-id="17f92-138">**[^]**: Any single character not within the specified range (for example, [^a-f]) or set (for example, [^aeiou]).</span></span>|  
|<span data-ttu-id="17f92-139">Is</span><span class="sxs-lookup"><span data-stu-id="17f92-139">Is</span></span>|<span data-ttu-id="17f92-140">比較兩個物件參考。</span><span class="sxs-lookup"><span data-stu-id="17f92-140">Compares two object references.</span></span>|  
  
### <a name="string-concatenation"></a><span data-ttu-id="17f92-141">字串串連</span><span class="sxs-lookup"><span data-stu-id="17f92-141">String Concatenation</span></span>  
 <span data-ttu-id="17f92-142">字串串連會在運算式中將第二個字串附加至第一個字串。</span><span class="sxs-lookup"><span data-stu-id="17f92-142">String concatenation appends the second string to the first string in an expression.</span></span> <span data-ttu-id="17f92-143">如果要進行其他字串作業，請使用內建的函數。</span><span class="sxs-lookup"><span data-stu-id="17f92-143">For other string operations, use built-in functions.</span></span>  
  
|<span data-ttu-id="17f92-144">運算子</span><span class="sxs-lookup"><span data-stu-id="17f92-144">Operator</span></span>|<span data-ttu-id="17f92-145">描述</span><span class="sxs-lookup"><span data-stu-id="17f92-145">Description</span></span>|  
|--------------|-----------------|  
|&|<span data-ttu-id="17f92-146">串連兩個字串</span><span class="sxs-lookup"><span data-stu-id="17f92-146">Concatenates two strings</span></span>|  
|+|<span data-ttu-id="17f92-147">串連兩個字串</span><span class="sxs-lookup"><span data-stu-id="17f92-147">Concatenates two strings</span></span>|  
  
### <a name="logical-and-bitwise"></a><span data-ttu-id="17f92-148">邏輯和位元</span><span class="sxs-lookup"><span data-stu-id="17f92-148">Logical and Bitwise</span></span>  
 <span data-ttu-id="17f92-149">邏輯和位元運算子會在運算式的兩個整數詞彙之間，執行邏輯操作。</span><span class="sxs-lookup"><span data-stu-id="17f92-149">Logical and bitwise operators perform logical manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="17f92-150">運算子</span><span class="sxs-lookup"><span data-stu-id="17f92-150">Operator</span></span>|<span data-ttu-id="17f92-151">描述</span><span class="sxs-lookup"><span data-stu-id="17f92-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="17f92-152">And</span><span class="sxs-lookup"><span data-stu-id="17f92-152">And</span></span>|<span data-ttu-id="17f92-153">對兩個布林運算式執行邏輯結合，或對兩個數值運算式 (Numeric Expression) 執行位元結合。</span><span class="sxs-lookup"><span data-stu-id="17f92-153">Performs a logical conjunction on two Boolean expressions, or bitwise conjunction on two numeric expressions.</span></span>|  
|<span data-ttu-id="17f92-154">Not</span><span class="sxs-lookup"><span data-stu-id="17f92-154">Not</span></span>|<span data-ttu-id="17f92-155">對布林運算式執行邏輯否定，或對數值運算式執行位元否定。</span><span class="sxs-lookup"><span data-stu-id="17f92-155">Performs logical negation on a Boolean expression, or bitwise negation on a numeric expression.</span></span>|  
|<span data-ttu-id="17f92-156">Or</span><span class="sxs-lookup"><span data-stu-id="17f92-156">Or</span></span>|<span data-ttu-id="17f92-157">對兩個布林運算式執行邏輯分離，或對兩個數值運算式執行位元分離。</span><span class="sxs-lookup"><span data-stu-id="17f92-157">Performs a logical disjunction on two Boolean expressions, or bitwise disjunction on two numeric values.</span></span>|  
|<span data-ttu-id="17f92-158">Xor</span><span class="sxs-lookup"><span data-stu-id="17f92-158">Xor</span></span>|<span data-ttu-id="17f92-159">對兩個布林運算式執行邏輯互斥作業，或對兩個數值運算式執行位元互斥。</span><span class="sxs-lookup"><span data-stu-id="17f92-159">Performs a logical exclusion operation on two Boolean expressions, or a bitwise exclusion on two numeric expressions.</span></span>|  
|<span data-ttu-id="17f92-160">AndAlso</span><span class="sxs-lookup"><span data-stu-id="17f92-160">AndAlso</span></span>|<span data-ttu-id="17f92-161">對兩個運算式執行邏輯結合。</span><span class="sxs-lookup"><span data-stu-id="17f92-161">Performs logical conjunction on two expressions.</span></span>|  
|<span data-ttu-id="17f92-162">OrElse</span><span class="sxs-lookup"><span data-stu-id="17f92-162">OrElse</span></span>|<span data-ttu-id="17f92-163">對兩個運算式執行邏輯分離。</span><span class="sxs-lookup"><span data-stu-id="17f92-163">Performs logical disjunction on two expressions.</span></span>|  
  
### <a name="bit-shift"></a><span data-ttu-id="17f92-164">位元位移</span><span class="sxs-lookup"><span data-stu-id="17f92-164">Bit Shift</span></span>  
 <span data-ttu-id="17f92-165">位元運算子會在運算式的兩個整數詞彙之間，執行位元操作。</span><span class="sxs-lookup"><span data-stu-id="17f92-165">Bitwise operators perform bit manipulations between two integer terms in an expression.</span></span>  
  
|<span data-ttu-id="17f92-166">運算子</span><span class="sxs-lookup"><span data-stu-id="17f92-166">Operator</span></span>|<span data-ttu-id="17f92-167">描述</span><span class="sxs-lookup"><span data-stu-id="17f92-167">Description</span></span>|  
|--------------|-----------------|  
|<\<|<span data-ttu-id="17f92-168">執行位元模式的算術左移位。</span><span class="sxs-lookup"><span data-stu-id="17f92-168">Performs an arithmetic left-shift on a bit pattern.</span></span>|  
|>>|<span data-ttu-id="17f92-169">執行位元模式的算術右移位。</span><span class="sxs-lookup"><span data-stu-id="17f92-169">Performs an arithmetic right-shift on a bit pattern.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17f92-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17f92-170">See Also</span></span>  
 <span data-ttu-id="17f92-171">[運算式對話方塊](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="17f92-171">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="17f92-172">[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="17f92-172">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="17f92-173">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="17f92-173">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="17f92-174">[運算式中的資料類型 &#40;報表產生器及 SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="17f92-174">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="17f92-175">運算式對話方塊 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="17f92-175">Expression Dialog Box &#40;Report Builder&#41;</span></span>](../expression-dialog-box-report-builder.md)  
  
  
