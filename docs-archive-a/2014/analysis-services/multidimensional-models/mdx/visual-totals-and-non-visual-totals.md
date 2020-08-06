---
title: 視覺效果總計和非視覺效果總計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ddff047be6a819d05276848cbeb430fb8e4c9c2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705565"
---
# <a name="visual-totals-and-non-visual-totals"></a><span data-ttu-id="f80a3-102">視覺化總計和非視覺化總計</span><span class="sxs-lookup"><span data-stu-id="f80a3-102">Visual Totals and Non Visual Totals</span></span>
  <span data-ttu-id="f80a3-103">視覺化總計是在資料行或資料列結尾加總該資料行或資料列中之所有可見項目的總計。</span><span class="sxs-lookup"><span data-stu-id="f80a3-103">Visual Totals are totals at the end of a column or row that add up all of the items visible in the column or row.</span></span> <span data-ttu-id="f80a3-104">這是大部分資料表顯示時的預設行為。</span><span class="sxs-lookup"><span data-stu-id="f80a3-104">This is the default behavior for most tables when displayed.</span></span> <span data-ttu-id="f80a3-105">不過，有時候使用者只想要顯示資料表中的某些資料行，但保持整個資料列的總計，包括未顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="f80a3-105">However, there are times when the user wants to display only certain columns in a table but keep the totals for the entire row, including those that are not displayed.</span></span> <span data-ttu-id="f80a3-106">這些稱為「非視覺化總計」(`Non Visual Totals`)，因為總計來自可見和不可見的值。</span><span class="sxs-lookup"><span data-stu-id="f80a3-106">These are called `Non Visual Totals`, because the total comes from both the visible and non-visible values.</span></span>  
  
 <span data-ttu-id="f80a3-107">下列案例示範非視覺化總計的行為。</span><span class="sxs-lookup"><span data-stu-id="f80a3-107">The following scenario demonstrates the behavior of Non Visual totals.</span></span> <span data-ttu-id="f80a3-108">第一個步驟示範視覺化總計的預設行為。</span><span class="sxs-lookup"><span data-stu-id="f80a3-108">The first step shows the default behavior of Visual Totals.</span></span>  
  
 <span data-ttu-id="f80a3-109">下列範例示範 [Adventure Works] 的查詢如何在包含產品類別目錄資料行和轉售商商務類型資料列的資料表中，取得 [Reseller Sales Amount] 數字。</span><span class="sxs-lookup"><span data-stu-id="f80a3-109">The following example is a query of [Adventure Works] to obtain [Reseller Sales Amount] figures in a table where the product categories are the columns and the reseller business types are the rows.</span></span> <span data-ttu-id="f80a3-110">請注意，在發出下列 SELECT 陳述式時，會提供產品和轉售商的總計：</span><span class="sxs-lookup"><span data-stu-id="f80a3-110">Note that totals are given for both products and resellers when the following SELECT statement is issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="f80a3-111">會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="f80a3-111">Produces the following results:</span></span>  
  
|||||||  
|-|-|-|-|-|-|  
||<span data-ttu-id="f80a3-112">**所有產品**</span><span class="sxs-lookup"><span data-stu-id="f80a3-112">**All Products**</span></span>|<span data-ttu-id="f80a3-113">**Accessories**</span><span class="sxs-lookup"><span data-stu-id="f80a3-113">**Accessories**</span></span>|<span data-ttu-id="f80a3-114">**自行車**</span><span class="sxs-lookup"><span data-stu-id="f80a3-114">**Bikes**</span></span>|<span data-ttu-id="f80a3-115">**Clothing**</span><span class="sxs-lookup"><span data-stu-id="f80a3-115">**Clothing**</span></span>|<span data-ttu-id="f80a3-116">**元件**</span><span class="sxs-lookup"><span data-stu-id="f80a3-116">**Components**</span></span>|  
|<span data-ttu-id="f80a3-117">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="f80a3-117">**All Resellers**</span></span>|<span data-ttu-id="f80a3-118">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="f80a3-118">**$80,450,596.98**</span></span>|<span data-ttu-id="f80a3-119">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="f80a3-119">**$571,297.93**</span></span>|<span data-ttu-id="f80a3-120">**$66,302,381.56**</span><span class="sxs-lookup"><span data-stu-id="f80a3-120">**$66,302,381.56**</span></span>|<span data-ttu-id="f80a3-121">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="f80a3-121">**$1,777,840.84**</span></span>|<span data-ttu-id="f80a3-122">**$11,799,076.66**</span><span class="sxs-lookup"><span data-stu-id="f80a3-122">**$11,799,076.66**</span></span>|  
|<span data-ttu-id="f80a3-123">**Specialty Bike Shop**</span><span class="sxs-lookup"><span data-stu-id="f80a3-123">**Specialty Bike Shop**</span></span>|<span data-ttu-id="f80a3-124">**$6,756,166.18**</span><span class="sxs-lookup"><span data-stu-id="f80a3-124">**$6,756,166.18**</span></span>|<span data-ttu-id="f80a3-125">**$65,125.48**</span><span class="sxs-lookup"><span data-stu-id="f80a3-125">**$65,125.48**</span></span>|<span data-ttu-id="f80a3-126">**$6,080,117.73**</span><span class="sxs-lookup"><span data-stu-id="f80a3-126">**$6,080,117.73**</span></span>|<span data-ttu-id="f80a3-127">**$252,933.91**</span><span class="sxs-lookup"><span data-stu-id="f80a3-127">**$252,933.91**</span></span>|<span data-ttu-id="f80a3-128">**$357,989.07**</span><span class="sxs-lookup"><span data-stu-id="f80a3-128">**$357,989.07**</span></span>|  
|<span data-ttu-id="f80a3-129">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="f80a3-129">**Value Added Reseller**</span></span>|<span data-ttu-id="f80a3-130">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="f80a3-130">**$34,967,517.33**</span></span>|<span data-ttu-id="f80a3-131">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="f80a3-131">**$175,002.81**</span></span>|<span data-ttu-id="f80a3-132">**$30,892,354.33**</span><span class="sxs-lookup"><span data-stu-id="f80a3-132">**$30,892,354.33**</span></span>|<span data-ttu-id="f80a3-133">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="f80a3-133">**$592,385.71**</span></span>|<span data-ttu-id="f80a3-134">**$3,307,774.48**</span><span class="sxs-lookup"><span data-stu-id="f80a3-134">**$3,307,774.48**</span></span>|  
|<span data-ttu-id="f80a3-135">**倉儲**</span><span class="sxs-lookup"><span data-stu-id="f80a3-135">**Warehouse**</span></span>|<span data-ttu-id="f80a3-136">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="f80a3-136">**$38,726,913.48**</span></span>|<span data-ttu-id="f80a3-137">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="f80a3-137">**$331,169.64**</span></span>|<span data-ttu-id="f80a3-138">**$29,329,909.50**</span><span class="sxs-lookup"><span data-stu-id="f80a3-138">**$29,329,909.50**</span></span>|<span data-ttu-id="f80a3-139">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="f80a3-139">**$932,521.23**</span></span>|<span data-ttu-id="f80a3-140">**$8,133,313.11**</span><span class="sxs-lookup"><span data-stu-id="f80a3-140">**$8,133,313.11**</span></span>|  
  
## <a name="non-visual-on-rows-and-columns"></a><span data-ttu-id="f80a3-141">資料行和資料列上的非視覺化</span><span class="sxs-lookup"><span data-stu-id="f80a3-141">Non-Visual on rows and columns</span></span>  
 <span data-ttu-id="f80a3-142">若要只針對產品為 Accessories 和 Clothing，且轉售商為 Value Added Reseller 和 Warehouse 的資料產生資料表，但同時保留全部項目的總計，可以使用 NON VISUAL 撰寫如下：</span><span class="sxs-lookup"><span data-stu-id="f80a3-142">To produce a table with data only for the Accessories and Clothing products, the Value Added Reseller and Warehouse resellers, yet keeping the overall totals could be written as follows using NON VISUAL:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="f80a3-143">會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="f80a3-143">Produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="f80a3-144">**所有產品**</span><span class="sxs-lookup"><span data-stu-id="f80a3-144">**All Products**</span></span>|<span data-ttu-id="f80a3-145">**Accessories**</span><span class="sxs-lookup"><span data-stu-id="f80a3-145">**Accessories**</span></span>|<span data-ttu-id="f80a3-146">**Clothing**</span><span class="sxs-lookup"><span data-stu-id="f80a3-146">**Clothing**</span></span>|  
|<span data-ttu-id="f80a3-147">**All Resellers**</span><span class="sxs-lookup"><span data-stu-id="f80a3-147">**All Resellers**</span></span>|<span data-ttu-id="f80a3-148">**$80,450,596.98**</span><span class="sxs-lookup"><span data-stu-id="f80a3-148">**$80,450,596.98**</span></span>|<span data-ttu-id="f80a3-149">**$571,297.93**</span><span class="sxs-lookup"><span data-stu-id="f80a3-149">**$571,297.93**</span></span>|<span data-ttu-id="f80a3-150">**$1,777,840.84**</span><span class="sxs-lookup"><span data-stu-id="f80a3-150">**$1,777,840.84**</span></span>|  
|<span data-ttu-id="f80a3-151">**Value Added Reseller**</span><span class="sxs-lookup"><span data-stu-id="f80a3-151">**Value Added Reseller**</span></span>|<span data-ttu-id="f80a3-152">**$34,967,517.33**</span><span class="sxs-lookup"><span data-stu-id="f80a3-152">**$34,967,517.33**</span></span>|<span data-ttu-id="f80a3-153">**$175,002.81**</span><span class="sxs-lookup"><span data-stu-id="f80a3-153">**$175,002.81**</span></span>|<span data-ttu-id="f80a3-154">**$592,385.71**</span><span class="sxs-lookup"><span data-stu-id="f80a3-154">**$592,385.71**</span></span>|  
|<span data-ttu-id="f80a3-155">**倉儲**</span><span class="sxs-lookup"><span data-stu-id="f80a3-155">**Warehouse**</span></span>|<span data-ttu-id="f80a3-156">**$38,726,913.48**</span><span class="sxs-lookup"><span data-stu-id="f80a3-156">**$38,726,913.48**</span></span>|<span data-ttu-id="f80a3-157">**$331,169.64**</span><span class="sxs-lookup"><span data-stu-id="f80a3-157">**$331,169.64**</span></span>|<span data-ttu-id="f80a3-158">**$932,521.23**</span><span class="sxs-lookup"><span data-stu-id="f80a3-158">**$932,521.23**</span></span>|  
  
## <a name="non-visual-on-rows"></a><span data-ttu-id="f80a3-159">資料列上的非視覺化</span><span class="sxs-lookup"><span data-stu-id="f80a3-159">Non-Visual on rows</span></span>  
 <span data-ttu-id="f80a3-160">若要產生可以視覺化總計資料行，但就資料列總計傳回所有 [Category] 的實際總計，應發出下列查詢：</span><span class="sxs-lookup"><span data-stu-id="f80a3-160">To produce a table that visually totals the columns but for row totals brings the true total of all [Category], the following query should be issued:</span></span>  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 <span data-ttu-id="f80a3-161">請注意如何將 NON VISUAL 只套用到 [Category]。</span><span class="sxs-lookup"><span data-stu-id="f80a3-161">Note how NON VISUAL is only applied to [Category].</span></span>  
  
 <span data-ttu-id="f80a3-162">上述的查詢會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="f80a3-162">The above query produces the following results:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="f80a3-163">All Products</span><span class="sxs-lookup"><span data-stu-id="f80a3-163">All Products</span></span>|<span data-ttu-id="f80a3-164">Accessories</span><span class="sxs-lookup"><span data-stu-id="f80a3-164">Accessories</span></span>|<span data-ttu-id="f80a3-165">Clothing</span><span class="sxs-lookup"><span data-stu-id="f80a3-165">Clothing</span></span>|  
|<span data-ttu-id="f80a3-166">All Resellers</span><span class="sxs-lookup"><span data-stu-id="f80a3-166">All Resellers</span></span>|<span data-ttu-id="f80a3-167">$73,694,430.80</span><span class="sxs-lookup"><span data-stu-id="f80a3-167">$73,694,430.80</span></span>|<span data-ttu-id="f80a3-168">$506,172.45</span><span class="sxs-lookup"><span data-stu-id="f80a3-168">$506,172.45</span></span>|<span data-ttu-id="f80a3-169">$1,524,906.93</span><span class="sxs-lookup"><span data-stu-id="f80a3-169">$1,524,906.93</span></span>|  
|<span data-ttu-id="f80a3-170">Value Added Reseller</span><span class="sxs-lookup"><span data-stu-id="f80a3-170">Value Added Reseller</span></span>|<span data-ttu-id="f80a3-171">$34,967,517.33</span><span class="sxs-lookup"><span data-stu-id="f80a3-171">$34,967,517.33</span></span>|<span data-ttu-id="f80a3-172">$175,002.81</span><span class="sxs-lookup"><span data-stu-id="f80a3-172">$175,002.81</span></span>|<span data-ttu-id="f80a3-173">$592,385.71</span><span class="sxs-lookup"><span data-stu-id="f80a3-173">$592,385.71</span></span>|  
|<span data-ttu-id="f80a3-174">Warehouse</span><span class="sxs-lookup"><span data-stu-id="f80a3-174">Warehouse</span></span>|<span data-ttu-id="f80a3-175">$38,726,913.48</span><span class="sxs-lookup"><span data-stu-id="f80a3-175">$38,726,913.48</span></span>|<span data-ttu-id="f80a3-176">$331,169.64</span><span class="sxs-lookup"><span data-stu-id="f80a3-176">$331,169.64</span></span>|<span data-ttu-id="f80a3-177">$932,521.23</span><span class="sxs-lookup"><span data-stu-id="f80a3-177">$932,521.23</span></span>|  
  
 <span data-ttu-id="f80a3-178">與前一個結果相比，您可以發現 [All Resellers] 資料列現在只總計 [Value Added Reseller] 和 [Warehouse] 的顯示值，但 [All Products] 資料行顯示所有產品 (包括未顯示產品) 的總計值。</span><span class="sxs-lookup"><span data-stu-id="f80a3-178">When compared with the previous results, you can observe that the [All Resellers] row now adds up to the displayed values for [Value Added Reseller] and [Warehouse] but that the [All Products] column shows the total value for all products, including those not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80a3-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f80a3-179">See Also</span></span>  
 <span data-ttu-id="f80a3-180">[MDX 中的重要概念 &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f80a3-180">[Key Concepts in MDX &#40;Analysis Services&#41;](../key-concepts-in-mdx-analysis-services.md) </span></span>  
 <span data-ttu-id="f80a3-181">[自動存在](autoexists.md) </span><span class="sxs-lookup"><span data-stu-id="f80a3-181">[Autoexists](autoexists.md) </span></span>  
 <span data-ttu-id="f80a3-182">[使用成員、元組和集合 &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="f80a3-182">[Working with Members, Tuples, and Sets &#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md) </span></span>  
 <span data-ttu-id="f80a3-183">[MDX 查詢基本概念 &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="f80a3-183">[MDX Query Fundamentals &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md) </span></span>  
 <span data-ttu-id="f80a3-184">[&#40;MDX 的基本 MDX 查詢&#41;](mdx-query-the-basic-query.md) </span><span class="sxs-lookup"><span data-stu-id="f80a3-184">[The Basic MDX Query &#40;MDX&#41;](mdx-query-the-basic-query.md) </span></span>  
 <span data-ttu-id="f80a3-185">[使用查詢和交叉分析篩選器軸來限制查詢 &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md) </span><span class="sxs-lookup"><span data-stu-id="f80a3-185">[Restricting the Query with Query and Slicer Axes &#40;MDX&#41;](mdx-query-and-slicer-axes-restricting-the-query.md) </span></span>  
 [<span data-ttu-id="f80a3-186">建立查詢中的 Cube 內容 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="f80a3-186">Establishing Cube Context in a Query &#40;MDX&#41;</span></span>](establishing-cube-context-in-a-query-mdx.md)  
  
  
