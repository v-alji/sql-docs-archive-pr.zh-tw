---
title: 瞭解行程順序和解決順序 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- evaluation order [MDX]
- calculation order [MDX]
- SOLVE_ORDER property
- queries [MDX], solve orders
- solve orders [MDX]
- pass orders [MDX]
- expressions [MDX], solve orders
ms.assetid: 7ed7d4ee-4644-4c5d-99a4-c4b429d0203c
author: minewiskan
ms.author: owend
ms.openlocfilehash: d92ccd9d1eeb05272a95c6f429f8c756bcb0022e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594739"
---
# <a name="understanding-pass-order-and-solve-order-mdx"></a><span data-ttu-id="5b261-102">了解行程順序與解決順序 (MDX)</span><span class="sxs-lookup"><span data-stu-id="5b261-102">Understanding Pass Order and Solve Order (MDX)</span></span>
  <span data-ttu-id="5b261-103">當 Cube 做為 MDX 指令碼的計算結果時，Cube 會根據所使用的各種計算相關功能來進行多個計算階段。</span><span class="sxs-lookup"><span data-stu-id="5b261-103">When a cube is calculated as the result of an MDX script, it can go through many stages of computation depending on the use of various calculation-related features.</span></span> <span data-ttu-id="5b261-104">每個階段都稱為一個計算行程。</span><span class="sxs-lookup"><span data-stu-id="5b261-104">Each of these stages is referred to as a calculation pass.</span></span>  
  
 <span data-ttu-id="5b261-105">計算行程可以是序數位置，稱為計算行程數目。</span><span class="sxs-lookup"><span data-stu-id="5b261-105">A calculation pass can be referred to by an ordinal position, called the calculation pass number.</span></span> <span data-ttu-id="5b261-106">完整計算 Cube 中所有資料格所需的計算行程數目稱為 Cube 的計算行程深度。</span><span class="sxs-lookup"><span data-stu-id="5b261-106">The count of calculation passes that are required to fully compute all the cells of a cube is referred to as the calculation pass depth of the cube.</span></span>  
  
 <span data-ttu-id="5b261-107">事實資料表和回寫資料只會影響行程 0。</span><span class="sxs-lookup"><span data-stu-id="5b261-107">Fact table and writeback data only impact pass 0.</span></span> <span data-ttu-id="5b261-108">行程 0 之後，指令碼會擴展資料；指令碼中每個指派和計算陳述式都會建立新的行程。</span><span class="sxs-lookup"><span data-stu-id="5b261-108">Scripts populate data after pass 0; each assignment and calculate statement in a script creates a new pass.</span></span> <span data-ttu-id="5b261-109">在 MDX 指令碼之外，對絕對行程 0 的參考會參考指令碼為 Cube 所建立的最後行程。</span><span class="sxs-lookup"><span data-stu-id="5b261-109">Outside the MDX script, references to absolute pass 0 refer to the last pass created by the script for the cube.</span></span>  
  
 <span data-ttu-id="5b261-110">導出成員會在所有行程建立，但運算式只會在目前行程套用。</span><span class="sxs-lookup"><span data-stu-id="5b261-110">Calculated members are created at all passes, but the expression is applied at the current pass.</span></span> <span data-ttu-id="5b261-111">先前的行程包含導出量值，不過會是 Null 值。</span><span class="sxs-lookup"><span data-stu-id="5b261-111">Prior passes contain the calculated measure, but with a null value.</span></span>  
  
## <a name="solve-order"></a><span data-ttu-id="5b261-112">解決順序</span><span class="sxs-lookup"><span data-stu-id="5b261-112">Solve Order</span></span>  
 <span data-ttu-id="5b261-113">解決順序決定在運算式發生競爭事件時，計算的優先權。</span><span class="sxs-lookup"><span data-stu-id="5b261-113">Solve order determines the priority of calculation in the event of competing expressions.</span></span> <span data-ttu-id="5b261-114">在單一行程內，解決順序決定兩件事情：</span><span class="sxs-lookup"><span data-stu-id="5b261-114">Within a single pass, solve order determines two things:</span></span>  
  
-   <span data-ttu-id="5b261-115">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 評估維度、成員、匯出成員、自訂匯總和匯出資料格的順序。</span><span class="sxs-lookup"><span data-stu-id="5b261-115">The order in which [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates dimensions, members, calculated members, custom rollups, and calculated cells.</span></span>  
  
-   <span data-ttu-id="5b261-116">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 評估自訂成員、導出成員、自訂積存和導出資料格的順序。</span><span class="sxs-lookup"><span data-stu-id="5b261-116">The order in which [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates custom members, calculated members, custom rollup, and calculated cells.</span></span>  
  
 <span data-ttu-id="5b261-117">擁有最高解決順序的成員優先。</span><span class="sxs-lookup"><span data-stu-id="5b261-117">The member with the highest solve order takes precedence.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b261-118">此優先順序的例外狀況是彙總函式。</span><span class="sxs-lookup"><span data-stu-id="5b261-118">The exception to this precedence is the Aggregate function.</span></span> <span data-ttu-id="5b261-119">具有彙總函式的導出成員，其解決順序比任何交集的導出量值還低。</span><span class="sxs-lookup"><span data-stu-id="5b261-119">Calculated members with the Aggregate function have a lower solve order than any intersecting calculated measure.</span></span>  
  
## <a name="solve-order-values-and-precedence"></a><span data-ttu-id="5b261-120">解決順序值和優先順序</span><span class="sxs-lookup"><span data-stu-id="5b261-120">Solve Order Values and Precedence</span></span>  
 <span data-ttu-id="5b261-121">解決順序值的範圍可以從 -8181 到 65535。</span><span class="sxs-lookup"><span data-stu-id="5b261-121">Solve order values can range from -8181 to 65535.</span></span> <span data-ttu-id="5b261-122">在此範圍中，某些解決順序值是對應到特定的計算種類，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="5b261-122">In this range, some solve order values correspond to specific kinds of calculations, as shown in the following table.</span></span>  
  
|<span data-ttu-id="5b261-123">計算</span><span class="sxs-lookup"><span data-stu-id="5b261-123">Calculation</span></span>|<span data-ttu-id="5b261-124">解決順序</span><span class="sxs-lookup"><span data-stu-id="5b261-124">Solve Order</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5b261-125">自訂成員公式</span><span class="sxs-lookup"><span data-stu-id="5b261-125">Custom member formulas</span></span>|<span data-ttu-id="5b261-126">-5119</span><span class="sxs-lookup"><span data-stu-id="5b261-126">-5119</span></span>|  
|<span data-ttu-id="5b261-127">一元運算子</span><span class="sxs-lookup"><span data-stu-id="5b261-127">Unary operators</span></span>|<span data-ttu-id="5b261-128">-5119</span><span class="sxs-lookup"><span data-stu-id="5b261-128">-5119</span></span>|  
|<span data-ttu-id="5b261-129">視覺化總計計算</span><span class="sxs-lookup"><span data-stu-id="5b261-129">Visual totals calculation</span></span>|<span data-ttu-id="5b261-130">-4096</span><span class="sxs-lookup"><span data-stu-id="5b261-130">-4096</span></span>|  
|<span data-ttu-id="5b261-131">其他所有計算 (若沒有特別指定)</span><span class="sxs-lookup"><span data-stu-id="5b261-131">All other calculations (if not otherwise specified)</span></span>|<span data-ttu-id="5b261-132">0</span><span class="sxs-lookup"><span data-stu-id="5b261-132">0</span></span>|  
  
 <span data-ttu-id="5b261-133">強烈建議您在設定解決順序值時只使用正整數。</span><span class="sxs-lookup"><span data-stu-id="5b261-133">It is highly recommended that you use only positive integers when setting solve order values.</span></span> <span data-ttu-id="5b261-134">如果您指定比上表中解決順序值還低的值，計算行程可能會變得無法預測。</span><span class="sxs-lookup"><span data-stu-id="5b261-134">If you assign values that are lower than the solve order values shown in the previous table, the calculation pass can become unpredictable.</span></span> <span data-ttu-id="5b261-135">例如，導出成員的計算會收到一個低於預設自訂積存公式值 -5119 的解決順序值。</span><span class="sxs-lookup"><span data-stu-id="5b261-135">For example, the calculation for a calculated member receives a solve order value that is lower than the default custom rollup formula value of -5119.</span></span> <span data-ttu-id="5b261-136">這類低的解決順序值會造成導出成員的計算早於自訂積存公式，所以會產生不正確的結果。</span><span class="sxs-lookup"><span data-stu-id="5b261-136">Such a low solve order value causes the calculated members to be calculated before the custom rollup formulas, and can produce incorrect results.</span></span>  
  
### <a name="creating-and-changing-solve-order"></a><span data-ttu-id="5b261-137">建立與變更解決順序</span><span class="sxs-lookup"><span data-stu-id="5b261-137">Creating and Changing Solve Order</span></span>  
 <span data-ttu-id="5b261-138">在 [Cube 設計師] 的 [計算窗格]\*\*\*\* 上，您可以變更計算的順序，來變更導出成員和導出資料格的解決順序。</span><span class="sxs-lookup"><span data-stu-id="5b261-138">In Cube Designer, on the **Calculations Pane**, you can change the solve order for calculated members and calculated cells by changing the order of the calculations.</span></span>  
  
 <span data-ttu-id="5b261-139">在 MDX 中，您可以使用 `SOLVE_ORDER` 關鍵字來建立或變更導出成員與導出資料格。</span><span class="sxs-lookup"><span data-stu-id="5b261-139">In MDX, you can use the `SOLVE_ORDER` keyword to create or change calculated members and calculated cells.</span></span>  
  
## <a name="solve-order-examples"></a><span data-ttu-id="5b261-140">解決順序範例</span><span class="sxs-lookup"><span data-stu-id="5b261-140">Solve Order Examples</span></span>  
 <span data-ttu-id="5b261-141">為了方便說明解決順序的可能複雜性，下列 MDX 查詢以兩個查詢開始，而個別查詢沒有解決順序的問題。</span><span class="sxs-lookup"><span data-stu-id="5b261-141">To illustrate the potential complexities of solve order, the following series of MDX queries starts with two queries that each individually have no solve order issues.</span></span> <span data-ttu-id="5b261-142">當這兩個查詢結合成一個查詢時，就需要解決順序。</span><span class="sxs-lookup"><span data-stu-id="5b261-142">These two queries are then combined into a query that requires solve order.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b261-143">您可以針對 Adventure Works 範例多維度資料庫執行這些 MDX 查詢。</span><span class="sxs-lookup"><span data-stu-id="5b261-143">You can run these MDX queries against the Adventure Works sample multidimensional database.</span></span> <span data-ttu-id="5b261-144">您可以從 codeplex 網站下載 [AdventureWorks Multidimensional Models SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) (AdventureWorks 多維度模型 SQL Server 2012) 範例。</span><span class="sxs-lookup"><span data-stu-id="5b261-144">You can download the [AdventureWorks Multidimensional Models SQL Server 2012](https://msftdbprodsamples.codeplex.com/releases/view/55330) sample from the codeplex site.</span></span>  
  
### <a name="query-1-differences-in-income-and-expenses"></a><span data-ttu-id="5b261-145">查詢 1-收益和費用的差異</span><span class="sxs-lookup"><span data-stu-id="5b261-145">Query 1-Differences in Income and Expenses</span></span>  
 <span data-ttu-id="5b261-146">在第一個 MDX 查詢中，建構一個簡單的 MDX 查詢來計算每年銷售和成本的差異，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="5b261-146">For the first MDX query, calculate the difference in sales and costs for each year by constructing a simple MDX query similar to the following example:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] )  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="5b261-147">在此查詢中，只有一個導出成員 `Year Difference`。</span><span class="sxs-lookup"><span data-stu-id="5b261-147">In this query, there is only one calculated member, `Year Difference`.</span></span> <span data-ttu-id="5b261-148">因為只有一個導出成員，只要 Cube 不使用任何導出成員，就沒有解決順序的問題。</span><span class="sxs-lookup"><span data-stu-id="5b261-148">Because there is only one calculated member, solve order is not an issue, as long as the cube does not use any calculated members.</span></span>  
  
 <span data-ttu-id="5b261-149">此 MDX 查詢產生類似下表的結果集。</span><span class="sxs-lookup"><span data-stu-id="5b261-149">This MDX query produces a result set similar to the following table.</span></span>  
  
||<span data-ttu-id="5b261-150">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="5b261-150">Internet Sales Amount</span></span>|<span data-ttu-id="5b261-151">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="5b261-151">Internet Total Product Cost</span></span>|  
|-|---------------------------|---------------------------------|  
|<span data-ttu-id="5b261-152">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="5b261-152">**CY 2007**</span></span>|<span data-ttu-id="5b261-153">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="5b261-153">$9,791,060.30</span></span>|<span data-ttu-id="5b261-154">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="5b261-154">$5,718,327.17</span></span>|  
|<span data-ttu-id="5b261-155">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="5b261-155">**CY 2008**</span></span>|<span data-ttu-id="5b261-156">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="5b261-156">$9,770,899.74</span></span>|<span data-ttu-id="5b261-157">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="5b261-157">$5,721,205.24</span></span>|  
|<span data-ttu-id="5b261-158">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="5b261-158">**Year Difference**</span></span>|<span data-ttu-id="5b261-159">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="5b261-159">($20,160.56)</span></span>|<span data-ttu-id="5b261-160">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="5b261-160">$2,878.06</span></span>|  
  
### <a name="query-2-percentage-of-income-after-expenses"></a><span data-ttu-id="5b261-161">查詢 2-費用後的收入百分比</span><span class="sxs-lookup"><span data-stu-id="5b261-161">Query 2-Percentage of Income after Expenses</span></span>  
 <span data-ttu-id="5b261-162">在第二個查詢中，使用以下 MDX 查詢來計算每年扣除費用後的收益百分比：</span><span class="sxs-lookup"><span data-stu-id="5b261-162">For the second query, calculate the percentage of income after expenses for each year using the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Measures].[Profit Margin] AS   
([Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent"  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="5b261-163">此 MDX 查詢和前一個查詢類似，只有一個導出成員 `Profit Margin`，因此也沒有任何求解順序的問題。</span><span class="sxs-lookup"><span data-stu-id="5b261-163">This MDX query, like the previous one, has only a single calculated member, `Profit Margin`, and therefore does not have any solve order complications.</span></span>  
  
 <span data-ttu-id="5b261-164">此 MDX 查詢產生類似下表，但有些微差異的結果集。</span><span class="sxs-lookup"><span data-stu-id="5b261-164">This MDX query produces a slightly different result set, similar to the following table.</span></span>  
  
||<span data-ttu-id="5b261-165">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="5b261-165">Internet Sales Amount</span></span>|<span data-ttu-id="5b261-166">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="5b261-166">Internet Total Product Cost</span></span>|<span data-ttu-id="5b261-167">獲利率</span><span class="sxs-lookup"><span data-stu-id="5b261-167">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="5b261-168">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="5b261-168">**CY 2007**</span></span>|<span data-ttu-id="5b261-169">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="5b261-169">$9,791,060.30</span></span>|<span data-ttu-id="5b261-170">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="5b261-170">$5,718,327.17</span></span>|<span data-ttu-id="5b261-171">41.60%</span><span class="sxs-lookup"><span data-stu-id="5b261-171">41.60%</span></span>|  
|<span data-ttu-id="5b261-172">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="5b261-172">**CY 2008**</span></span>|<span data-ttu-id="5b261-173">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="5b261-173">$9,770,899.74</span></span>|<span data-ttu-id="5b261-174">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="5b261-174">$5,721,205.24</span></span>|<span data-ttu-id="5b261-175">41.45%</span><span class="sxs-lookup"><span data-stu-id="5b261-175">41.45%</span></span>|  
  
 <span data-ttu-id="5b261-176">第一個查詢和第二個查詢之間的結果集差異，在於導出成員的位置差異。</span><span class="sxs-lookup"><span data-stu-id="5b261-176">The difference in result sets between the first query and the second query comes from the difference in placement of the calculated member.</span></span> <span data-ttu-id="5b261-177">在第一個查詢中，導出成員是 ROWS 座標軸的一部份，而不是第二個查詢中的 COLUMNS 座標軸。</span><span class="sxs-lookup"><span data-stu-id="5b261-177">In the first query, the calculated member is part of the ROWS axis, not the COLUMNS axis shown in the second query.</span></span> <span data-ttu-id="5b261-178">此種位置的差異在下一個查詢 (結合單一 MDX 查詢的兩個導出成員) 中就變得很重要。</span><span class="sxs-lookup"><span data-stu-id="5b261-178">This difference in placement becomes important in the next query, which combines the two calculated members in a single MDX query.</span></span>  
  
### <a name="query-3-combined-year-difference-and-net-income-calculations"></a><span data-ttu-id="5b261-179">查詢 3-結合年份差異和淨收益計算</span><span class="sxs-lookup"><span data-stu-id="5b261-179">Query 3-Combined Year Difference and Net Income Calculations</span></span>  
 <span data-ttu-id="5b261-180">在結合上述兩個範例到單一 MDX 查詢的最終查詢中，求解順序就變得很重要，因為會同時計算資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="5b261-180">In this final query combining both of the previous examples into a single MDX query, solve order becomes important because of the calculations on both columns and rows.</span></span> <span data-ttu-id="5b261-181">若要確定以正確的順序進行計算，請使用 `SOLVE_ORDER` 關鍵字定義計算順序。</span><span class="sxs-lookup"><span data-stu-id="5b261-181">To make sure that the calculations occur in the correct sequence, define the sequence in which the calculations occur by using the `SOLVE_ORDER` keyword.</span></span>  
  
 <span data-ttu-id="5b261-182">`SOLVE_ORDER` 關鍵字指定 MDX 查詢中導出成員或 `CREATE MEMBER` 命令的解決順序。</span><span class="sxs-lookup"><span data-stu-id="5b261-182">The `SOLVE_ORDER` keyword specifies the solve order of calculated members in an MDX query or a `CREATE MEMBER` command.</span></span> <span data-ttu-id="5b261-183">和 `SOLVE_ORDER` 關鍵字並用的整數值是相對值，不需要從零開始，也不需要連續。</span><span class="sxs-lookup"><span data-stu-id="5b261-183">The integer values used with the `SOLVE_ORDER` keyword are relative, do not need to start at zero, and do not need to be consecutive.</span></span> <span data-ttu-id="5b261-184">此數值只是告知 MDX 根據有較高值的成員計算所得出的值來導出成員。</span><span class="sxs-lookup"><span data-stu-id="5b261-184">The value simply tells MDX to calculate a member based on values derived from calculating members with a higher value.</span></span> <span data-ttu-id="5b261-185">如果導出成員沒有以 `SOLVE_ORDER` 關鍵字定義，該導出成員的預設值為零。</span><span class="sxs-lookup"><span data-stu-id="5b261-185">If a calculated member is defined without the `SOLVE_ORDER` keyword, the default value of that calculated member is zero.</span></span>  
  
 <span data-ttu-id="5b261-186">例如，如果您結合前兩個範例查詢中使用的計算，兩個導出成員 `Year Difference` 和 `Profit Margin`會在 MDX 查詢範例之結果資料集中的單一資料格中產生交集。</span><span class="sxs-lookup"><span data-stu-id="5b261-186">For example, if you combine the calculations used in the first two example queries, the two calculated members, `Year Difference` and `Profit Margin`, intersect at a single cell in the result dataset of the MDX query example.</span></span> <span data-ttu-id="5b261-187">決定 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 如何評估此資料格的唯一方式，就是解決順序。</span><span class="sxs-lookup"><span data-stu-id="5b261-187">The only way to determine how [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] will evaluate this cell is by the solve order.</span></span> <span data-ttu-id="5b261-188">用來建立此資料格的公式會根據兩個導出成員的解決順序，來產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="5b261-188">The formulas that are used to construct this cell will produce different results depending upon the solve order of the two calculated members.</span></span>  
  
 <span data-ttu-id="5b261-189">首先，請嘗試結合以下 MDX 查詢中前兩個查詢所使用的計算：</span><span class="sxs-lookup"><span data-stu-id="5b261-189">First, try combining the calculations used in the first two queries in the following MDX query:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 1  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 2  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="5b261-190">在此結合的 MDX 查詢範例中， `Profit Margin` 擁有最高的解決順序，所以當兩個運算式有交集時會優先處理它。</span><span class="sxs-lookup"><span data-stu-id="5b261-190">In this combined MDX query example, `Profit Margin` has the highest solve order, so it takes precedence when the two expressions interact.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="5b261-191">會使用 `Profit Margin` 公式來評估有問題的資料格。</span><span class="sxs-lookup"><span data-stu-id="5b261-191">evaluates the cell in question by using the `Profit Margin` formula.</span></span> <span data-ttu-id="5b261-192">此巢狀計算的結果，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="5b261-192">The results of this nested calculation, as shown in the following table.</span></span>  
  
||<span data-ttu-id="5b261-193">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="5b261-193">Internet Sales Amount</span></span>|<span data-ttu-id="5b261-194">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="5b261-194">Internet Total Product Cost</span></span>|<span data-ttu-id="5b261-195">獲利率</span><span class="sxs-lookup"><span data-stu-id="5b261-195">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="5b261-196">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="5b261-196">**CY 2007**</span></span>|<span data-ttu-id="5b261-197">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="5b261-197">$9,791,060.30</span></span>|<span data-ttu-id="5b261-198">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="5b261-198">$5,718,327.17</span></span>|<span data-ttu-id="5b261-199">41.60%</span><span class="sxs-lookup"><span data-stu-id="5b261-199">41.60%</span></span>|  
|<span data-ttu-id="5b261-200">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="5b261-200">**CY 2008**</span></span>|<span data-ttu-id="5b261-201">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="5b261-201">$9,770,899.74</span></span>|<span data-ttu-id="5b261-202">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="5b261-202">$5,721,205.24</span></span>|<span data-ttu-id="5b261-203">41.45%</span><span class="sxs-lookup"><span data-stu-id="5b261-203">41.45%</span></span>|  
|<span data-ttu-id="5b261-204">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="5b261-204">**Year Difference**</span></span>|<span data-ttu-id="5b261-205">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="5b261-205">($20,160.56)</span></span>|<span data-ttu-id="5b261-206">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="5b261-206">$2,878.06</span></span>|<span data-ttu-id="5b261-207">114.28%</span><span class="sxs-lookup"><span data-stu-id="5b261-207">114.28%</span></span>|  
  
 <span data-ttu-id="5b261-208">共用資料格中的結果是以 `Profit Margin`的公式為基礎。</span><span class="sxs-lookup"><span data-stu-id="5b261-208">The result in the shared cell is based on the formula for `Profit Margin`.</span></span> <span data-ttu-id="5b261-209">也就是說， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會計算含有 `Year Difference` 資料之共用資料格的結果，產生下列公式 (為了清楚起見，結果為四捨五入)：</span><span class="sxs-lookup"><span data-stu-id="5b261-209">That is, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell with the `Year Difference` data, producing the following formula (the result is rounded for clarity):</span></span>  
  
```  
((9,770,899.74 - 9,791,060.30) - (5,721,205.24 - 5,718,327.17)) / (9,770,899.74 - 9,791,060.30) = 1.14275744   
```  
  
 <span data-ttu-id="5b261-210">或</span><span class="sxs-lookup"><span data-stu-id="5b261-210">or</span></span>  
  
```  
(23,038.63) / (20,160.56) = 114.28%  
```  
  
 <span data-ttu-id="5b261-211">這明顯錯誤。</span><span class="sxs-lookup"><span data-stu-id="5b261-211">This is clearly incorrect.</span></span> <span data-ttu-id="5b261-212">但是，如果您在 MDX 查詢中切換導出成員的求解順序， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會以不同方式計算共用資料格的結果。</span><span class="sxs-lookup"><span data-stu-id="5b261-212">However, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] calculates the result in the shared cell differently if you switch the solve orders for the calculated members in the MDX query.</span></span> <span data-ttu-id="5b261-213">以下結合的 MDX 查詢改變了導出成員的解決順序：</span><span class="sxs-lookup"><span data-stu-id="5b261-213">The following combined MDX query reverses the solve order for the calculated members:</span></span>  
  
```  
WITH   
MEMBER  
[Date].[Calendar].[Year Difference] AS ([Date].[Calendar].[Calendar Year].&[2008] - [Date].[Calendar].[Calendar Year].&[2007] ) ,  
SOLVE_ORDER = 2  
MEMBER  
[Measures].[Profit Margin] AS   
( [Measures].[Internet Sales Amount] - [Measures].[Internet Total Product Cost] ) / [Measures].[Internet Sales Amount] ,  
FORMAT_STRING="Percent" ,  
SOLVE_ORDER = 1  
SELECT   
{[Measures].[Internet Sales Amount], [Measures].[Internet Total Product Cost], [Measures].[Profit Margin] }  
ON COLUMNS ,  
{ [Date].[Calendar].[Calendar Year].&[2007], [Date].[Calendar].[Calendar Year].&[2008], [Date].[Year Difference] }  
ON ROWS  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="5b261-214">當切換導出成員的求解順序後， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 就會使用 `Year Difference` 公式來評估資料格，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="5b261-214">As the order of the calculated members has been switched, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] uses the `Year Difference` formula to evaluate the cell, as shown in the following table.</span></span>  
  
||<span data-ttu-id="5b261-215">Internet Sales Amount</span><span class="sxs-lookup"><span data-stu-id="5b261-215">Internet Sales Amount</span></span>|<span data-ttu-id="5b261-216">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="5b261-216">Internet Total Product Cost</span></span>|<span data-ttu-id="5b261-217">獲利率</span><span class="sxs-lookup"><span data-stu-id="5b261-217">Profit Margin</span></span>|  
|-|---------------------------|---------------------------------|-------------------|  
|<span data-ttu-id="5b261-218">**CY 2007**</span><span class="sxs-lookup"><span data-stu-id="5b261-218">**CY 2007**</span></span>|<span data-ttu-id="5b261-219">$9,791,060.30</span><span class="sxs-lookup"><span data-stu-id="5b261-219">$9,791,060.30</span></span>|<span data-ttu-id="5b261-220">$5,718,327.17</span><span class="sxs-lookup"><span data-stu-id="5b261-220">$5,718,327.17</span></span>|<span data-ttu-id="5b261-221">41.60%</span><span class="sxs-lookup"><span data-stu-id="5b261-221">41.60%</span></span>|  
|<span data-ttu-id="5b261-222">**CY 2008**</span><span class="sxs-lookup"><span data-stu-id="5b261-222">**CY 2008**</span></span>|<span data-ttu-id="5b261-223">$9,770,899.74</span><span class="sxs-lookup"><span data-stu-id="5b261-223">$9,770,899.74</span></span>|<span data-ttu-id="5b261-224">$5,721,205.24</span><span class="sxs-lookup"><span data-stu-id="5b261-224">$5,721,205.24</span></span>|<span data-ttu-id="5b261-225">41.45%</span><span class="sxs-lookup"><span data-stu-id="5b261-225">41.45%</span></span>|  
|<span data-ttu-id="5b261-226">**Year Difference**</span><span class="sxs-lookup"><span data-stu-id="5b261-226">**Year Difference**</span></span>|<span data-ttu-id="5b261-227">($20,160.56)</span><span class="sxs-lookup"><span data-stu-id="5b261-227">($20,160.56)</span></span>|<span data-ttu-id="5b261-228">$2,878.06</span><span class="sxs-lookup"><span data-stu-id="5b261-228">$2,878.06</span></span>|<span data-ttu-id="5b261-229">(0.15%)</span><span class="sxs-lookup"><span data-stu-id="5b261-229">(0.15%)</span></span>|  
  
 <span data-ttu-id="5b261-230">因為此查詢使用含有 `Year Difference` 資料的 `Profit Margin` 公式，所以共用資料格的公式會類似以下計算：</span><span class="sxs-lookup"><span data-stu-id="5b261-230">Because this query uses the `Year Difference` formula with the `Profit Margin` data, the formula for the shared cell resembles the following calculation:</span></span>  
  
```  
(($9,770,899.74 - 5,721,205.24) / $9,770,899.74) - ((9,791,060.30 - 5,718,327.17) / 9,791,060.30) = -0.15   
```  
  
 <span data-ttu-id="5b261-231">或者</span><span class="sxs-lookup"><span data-stu-id="5b261-231">Or</span></span>  
  
```  
0.4145 - 0.4160= -0.15  
```  
  
## <a name="additional-considerations"></a><span data-ttu-id="5b261-232">其他考量</span><span class="sxs-lookup"><span data-stu-id="5b261-232">Additional Considerations</span></span>  
 <span data-ttu-id="5b261-233">若 Cube 有大量的維度，並牽涉到導出成員、自訂積存公式或導出資料格時，處理解決順序會是非常複雜的問題。</span><span class="sxs-lookup"><span data-stu-id="5b261-233">Solve order can be a very complex issue to deal with, especially in cubes with a high number of dimensions involving calculated member, custom rollup formulas, or calculated cells.</span></span> <span data-ttu-id="5b261-234">當 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 評估 MDX 查詢時， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會考慮給定行程內牽涉到的所有項目 (包括 MDX 查詢中指定之 Cube 的維度) 的解決順序值。</span><span class="sxs-lookup"><span data-stu-id="5b261-234">When [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] evaluates an MDX query, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] takes into account the solve order values for everything involved within a given pass, including the dimensions of the cube specified in the MDX query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b261-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b261-235">See Also</span></span>  
 <span data-ttu-id="5b261-236">[CalculationCurrentPass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span><span class="sxs-lookup"><span data-stu-id="5b261-236">[CalculationCurrentPass &#40;MDX&#41;](/sql/mdx/calculationcurrentpass-mdx) </span></span>  
 <span data-ttu-id="5b261-237">[CalculationPassValue &#40;MDX&#41;](/sql/mdx/calculationpassvalue-mdx) </span><span class="sxs-lookup"><span data-stu-id="5b261-237">[CalculationPassValue &#40;MDX&#41;](/sql/mdx/calculationpassvalue-mdx) </span></span>  
 <span data-ttu-id="5b261-238">[&#40;MDX&#41;的 CREATE MEMBER 語句](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="5b261-238">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 [<span data-ttu-id="5b261-239">操作資料 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="5b261-239">Manipulating Data &#40;MDX&#41;</span></span>](mdx-data-manipulation-manipulating-data.md)  
  
