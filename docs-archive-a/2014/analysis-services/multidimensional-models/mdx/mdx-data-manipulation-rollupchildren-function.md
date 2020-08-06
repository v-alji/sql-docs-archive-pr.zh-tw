---
title: 使用 RollupChildren 函數 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- queries [MDX], RollupChildren function
- RollupChildren function
- custom member properties [MDX]
- IIf function
ms.assetid: 03c624d4-f277-451d-9995-623a07ea2f86
author: minewiskan
ms.author: owend
ms.openlocfilehash: 341468d521cebe1fda33d73ea999f3b6571cb01e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705601"
---
# <a name="working-with-the-rollupchildren-function-mdx"></a><span data-ttu-id="a1001-102">使用 RollupChildren 函數 (MDX)</span><span class="sxs-lookup"><span data-stu-id="a1001-102">Working with the RollupChildren Function (MDX)</span></span>
  <span data-ttu-id="a1001-103">多維度運算式 (MDX) [RollupChildren](/sql/mdx/rollupchildren-mdx) [Script for Search 和 Replace] 函式會匯總成員的子系，並將不同的一元運算子套用至每個子系，並傳回此 rollup 的值做為數位。</span><span class="sxs-lookup"><span data-stu-id="a1001-103">The Multidimensional Expressions (MDX) [RollupChildren](/sql/mdx/rollupchildren-mdx) [Script for Search and Replace] function rolls up the children of a member, applying a different unary operator to each child, and returns the value of this rollup as a number.</span></span> <span data-ttu-id="a1001-104">一元運算子可由與子成員相關的成員屬性提供，或者可能是字串運算式直接將運算子提供給函數。</span><span class="sxs-lookup"><span data-stu-id="a1001-104">The unary operator can be supplied by a member property associated with the child member, or the operator can be a string expression provided directly to the function.</span></span>  
  
## <a name="rollupchildren-function-examples"></a><span data-ttu-id="a1001-105">RollupChildren 函數範例</span><span class="sxs-lookup"><span data-stu-id="a1001-105">RollupChildren Function Examples</span></span>  
 <span data-ttu-id="a1001-106">要說明使用多維度運算式 (MDX) 陳述式的 `RollupChildren` 函數是很簡單，但此函數對 MDX 查詢的影響相當廣泛。</span><span class="sxs-lookup"><span data-stu-id="a1001-106">The use of the `RollupChildren` function in Multidimensional Expressions (MDX) statements is simple to explain, but the effect of this function on MDX queries can be wide-ranging.</span></span>  
  
 <span data-ttu-id="a1001-107">`RollupChildren` 函數會對為了對現有的 Cube 資料，執行選擇性分析而設計 MDX 查詢的產生影響。</span><span class="sxs-lookup"><span data-stu-id="a1001-107">The effect of the `RollupChildren` function occurs in MDX queries designed to perform selective analysis on existing cube data.</span></span> <span data-ttu-id="a1001-108">例如，下表包含 Net Sales 父成員的子成員清單，以及在括號中顯示它們的一元運算子 (以 `UNARY_OPERATOR` 成員屬性代表)。</span><span class="sxs-lookup"><span data-stu-id="a1001-108">For example, the following table contains a list of child members for the Net Sales parent member, with their unary operators (represented by the `UNARY_OPERATOR` member property) shown in parentheses.</span></span>  
  
|<span data-ttu-id="a1001-109">父成員</span><span class="sxs-lookup"><span data-stu-id="a1001-109">Parent member</span></span>|<span data-ttu-id="a1001-110">子成員</span><span class="sxs-lookup"><span data-stu-id="a1001-110">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="a1001-111">Net Sales</span><span class="sxs-lookup"><span data-stu-id="a1001-111">Net Sales</span></span>|<span data-ttu-id="a1001-112">Domestic Sales (+)</span><span class="sxs-lookup"><span data-stu-id="a1001-112">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="a1001-113">Domestic Returns (-)</span><span class="sxs-lookup"><span data-stu-id="a1001-113">Domestic Returns (-)</span></span><br /><br /> <span data-ttu-id="a1001-114">Foreign Sales (+)</span><span class="sxs-lookup"><span data-stu-id="a1001-114">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="a1001-115">Foreign Returns (-)</span><span class="sxs-lookup"><span data-stu-id="a1001-115">Foreign Returns (-)</span></span>|  
  
 <span data-ttu-id="a1001-116">Net Sales 父成員目前是淨銷售量的總和減去國內外總銷售量值，而國內外退貨量則當做積存減去。</span><span class="sxs-lookup"><span data-stu-id="a1001-116">The Net Sales parent member currently provides a total of net sales minus the gross domestic and foreign sales values, with the domestic and foreign returns subtracted as part of the rollup.</span></span>  
  
 <span data-ttu-id="a1001-117">但是，您想要外加 10% 以簡單、快速地預測國內外銷售總額，而不理會國內外的退貨量。</span><span class="sxs-lookup"><span data-stu-id="a1001-117">However, you want to provide a quick and easy forecast of domestic and foreign gross sales plus 10%, ignoring the domestic and foreign returns.</span></span> <span data-ttu-id="a1001-118">若要計算此值，您能以下其中一個方式使用 `RollupChildren` 函數：利用自訂成員屬性，或利用`IIf` 函數。</span><span class="sxs-lookup"><span data-stu-id="a1001-118">To calculate this value, you can use the `RollupChildren` function in one of two ways: with a custom member property or with the `IIf` function.</span></span>  
  
### <a name="using-a-custom-member-property"></a><span data-ttu-id="a1001-119">使用自訂成員屬性</span><span class="sxs-lookup"><span data-stu-id="a1001-119">Using a Custom Member Property</span></span>  
 <span data-ttu-id="a1001-120">如果將會經常執行積存計算作業，其中一個方法是建立一個成員屬性，儲存供每個子系當做特定函數使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="a1001-120">If the rollup calculation is to be a frequently performed operation, one method is to create a member property that stores the operator that will be used for each child for a specific function.</span></span> <span data-ttu-id="a1001-121">下表顯示有效的一元運算子，而且描述了預期的結果。</span><span class="sxs-lookup"><span data-stu-id="a1001-121">The following table displays valid unary operators and describes the expected result.</span></span>  
  
|<span data-ttu-id="a1001-122">運算子</span><span class="sxs-lookup"><span data-stu-id="a1001-122">Operator</span></span>|<span data-ttu-id="a1001-123">結果</span><span class="sxs-lookup"><span data-stu-id="a1001-123">Result</span></span>|  
|--------------|------------|  
|+|<span data-ttu-id="a1001-124">總計 = 總計 + 目前的子系</span><span class="sxs-lookup"><span data-stu-id="a1001-124">total = total + current child</span></span>|  
|-|<span data-ttu-id="a1001-125">總計 = 總計 - 目前的子系</span><span class="sxs-lookup"><span data-stu-id="a1001-125">total = total - current child</span></span>|  
|*|<span data-ttu-id="a1001-126">總計 =總計 \* 目前的子系</span><span class="sxs-lookup"><span data-stu-id="a1001-126">total = total \* current child</span></span>|  
|/|<span data-ttu-id="a1001-127">總計 =總計 / 目前的子系</span><span class="sxs-lookup"><span data-stu-id="a1001-127">total = total / current child</span></span>|  
|~|<span data-ttu-id="a1001-128">子系不會被用在積存中。</span><span class="sxs-lookup"><span data-stu-id="a1001-128">Child is not used in the rollup.</span></span> <span data-ttu-id="a1001-129">子系的值會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a1001-129">The child's value is ignored.</span></span>|  
  
 <span data-ttu-id="a1001-130">例如，您可以建立一個稱為 `SALES_OPERATOR` 的成員屬性，將以下的一元運算子指派給此成員屬性，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="a1001-130">For example, a member property called `SALES_OPERATOR` could be created, and the following unary operators would be assigned to that member property, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a1001-131">父成員</span><span class="sxs-lookup"><span data-stu-id="a1001-131">Parent member</span></span>|<span data-ttu-id="a1001-132">子成員</span><span class="sxs-lookup"><span data-stu-id="a1001-132">Child member</span></span>|  
|-------------------|------------------|  
|<span data-ttu-id="a1001-133">Net Sales</span><span class="sxs-lookup"><span data-stu-id="a1001-133">Net Sales</span></span>|<span data-ttu-id="a1001-134">Domestic Sales (+)</span><span class="sxs-lookup"><span data-stu-id="a1001-134">Domestic Sales (+)</span></span><br /><br /> <span data-ttu-id="a1001-135">Domestic Returns (~)</span><span class="sxs-lookup"><span data-stu-id="a1001-135">Domestic Returns (~)</span></span><br /><br /> <span data-ttu-id="a1001-136">Foreign Sales (+)</span><span class="sxs-lookup"><span data-stu-id="a1001-136">Foreign Sales (+)</span></span><br /><br /> <span data-ttu-id="a1001-137">Foreign Returns (~)</span><span class="sxs-lookup"><span data-stu-id="a1001-137">Foreign Returns (~)</span></span>|  
  
 <span data-ttu-id="a1001-138">有了這個新的成員屬性，以下 MDX 陳述式就可以快速且有效地執行銷售總額估計作業 (忽略國內外退貨量)：</span><span class="sxs-lookup"><span data-stu-id="a1001-138">With this new member property, the following MDX statement would perform the gross sales estimate operation quickly and efficiently (ignoring Foreign and Domestic returns):</span></span>  
  
```  
RollupChildren([Net Sales], [Net Sales].CurrentMember.Properties("SALES_OPERATOR")) * 1.1  
```  
  
 <span data-ttu-id="a1001-139">當呼叫此函數時，就會使用成員屬性中儲存的運算子，將每個子系的值套用到總計。</span><span class="sxs-lookup"><span data-stu-id="a1001-139">When the function is called, the value of each child is applied to a total using the operator stored in the member property.</span></span> <span data-ttu-id="a1001-140">國內外退貨量會被忽略，而且 `RollupChildren` 函數所傳回的積存總計會乘以 1.1。</span><span class="sxs-lookup"><span data-stu-id="a1001-140">The members for domestic and foreign returns are ignored, and the rollup total returned by the `RollupChildren` function is multiplied by 1.1.</span></span>  
  
### <a name="using-the-iif-function"></a><span data-ttu-id="a1001-141">使用 IIf 函數</span><span class="sxs-lookup"><span data-stu-id="a1001-141">Using the IIf Function</span></span>  
 <span data-ttu-id="a1001-142">如果範例作業不是常見的，或作業只套用至一個 MDX 查詢，則[IIf](/sql/mdx/iif-mdx)函式可與函數搭配使用， `RollupChildren` 以提供相同的結果。</span><span class="sxs-lookup"><span data-stu-id="a1001-142">If the example operation is not commonplace or if the operation applies only to one MDX query, the [IIf](/sql/mdx/iif-mdx) function can be used with the `RollupChildren` function to provide the same result.</span></span> <span data-ttu-id="a1001-143">以下的 MDX 查詢可以提供跟先前 MDX 範例一樣的結果，但不需要使用自訂的成員屬性就可以做到。</span><span class="sxs-lookup"><span data-stu-id="a1001-143">The following MDX query provides the same result as the earlier MDX example, but does so without resorting to the use of a custom member property:</span></span>  
  
```  
RollupChildren([Net Sales], IIf([Net Sales].CurrentMember.Properties("UNARY_OPERATOR") = "-", "~", [Net Sales].CurrentMember.Properties("UNARY_OPERATOR))) * 1.1  
```  
  
 <span data-ttu-id="a1001-144">MDX 陳述式會檢查子成員的一元運算子。</span><span class="sxs-lookup"><span data-stu-id="a1001-144">The MDX statement examines the unary operator of the child member.</span></span> <span data-ttu-id="a1001-145">如果一元運算子用於減法 (如同在處理國內外退貨量成員的情況下)，則 `IIf` 函數會取代波狀符號 (~) 一元運算子。</span><span class="sxs-lookup"><span data-stu-id="a1001-145">If the unary operator is used for subtraction (as in the case with the domestic and foreign returns members), the `IIf` function substitutes the tilde (~) unary operator.</span></span> <span data-ttu-id="a1001-146">否則，`IIf` 函數會使用子成員的一元運算子。</span><span class="sxs-lookup"><span data-stu-id="a1001-146">Otherwise, the `IIf` function uses the unary operator of the child member.</span></span> <span data-ttu-id="a1001-147">最後，傳回的積存總計會乘以 1.1，做為國內外銷售總額的預測值。</span><span class="sxs-lookup"><span data-stu-id="a1001-147">Finally, the returned rollup total is then multiplied by 1.1 to provide the domestic and foreign gross sales forecast value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1001-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1001-148">See Also</span></span>  
 [<span data-ttu-id="a1001-149">操作資料 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="a1001-149">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
  
