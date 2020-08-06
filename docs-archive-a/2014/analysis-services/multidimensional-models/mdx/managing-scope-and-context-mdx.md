---
title: " (MDX) 管理範圍和內容 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], context
- scope [MDX]
- CALCULATE statement
- This function [MDX]
- SCOPE statement
- scripts [MDX], scope
ms.assetid: 631e7c20-8be9-4c35-8609-76516aef19d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: f7cf1e6cea8df00b632e114a5a8756373738ca6e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594743"
---
# <a name="managing-scope-and-context-mdx"></a><span data-ttu-id="ab18e-102">管理範圍及內容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="ab18e-102">Managing Scope and Context (MDX)</span></span>
  <span data-ttu-id="ab18e-103">在中 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ， (MDX) 腳本的多維度運算式可以在腳本執行內的特定點套用至整個 cube 或 cube 的特定部分。</span><span class="sxs-lookup"><span data-stu-id="ab18e-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script can apply to the entire cube, or to specific portions of the cube, at specific points within the execution of the script.</span></span> <span data-ttu-id="ab18e-104">MDX 指令碼會透過使用計算行程，對 Cube 內的計算採用分層方法。</span><span class="sxs-lookup"><span data-stu-id="ab18e-104">The MDX script can take a layered approach to calculations within a cube through the use of calculation passes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab18e-105">如需計算行程如何影響計算的詳細資訊，請參閱[了解行程順序和解決順序 &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md)。</span><span class="sxs-lookup"><span data-stu-id="ab18e-105">For more information on how calculation passes can affect calculations, see [Understanding Pass Order and Solve Order &#40;MDX&#41;](mdx-data-manipulation-understanding-pass-order-and-solve-order.md).</span></span>  
  
 <span data-ttu-id="ab18e-106">若要控制計算行程、範圍及 MDX 指令碼內的內容，您可以特別使用 CACULATE 陳述式、`This` 函數及 SCOPE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab18e-106">To control the calculation pass, scope, and context within an MDX script, you specifically use the CACULATE statement, the `This` function, and the SCOPE statement.</span></span>  
  
## <a name="using-the-calculate-statement"></a><span data-ttu-id="ab18e-107">使用 CALCULATE 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab18e-107">Using the CALCULATE Statement</span></span>  
 <span data-ttu-id="ab18e-108">CALCULATE 陳述式會以彙總資料擴展 Cube 中的每個資料格。</span><span class="sxs-lookup"><span data-stu-id="ab18e-108">The CALCULATE statement populates each cell in the cube with aggregated data.</span></span> <span data-ttu-id="ab18e-109">例如，MDX 指令碼在指令碼的開始處會有一個 CALCULATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab18e-109">For example, the default MDX script has a single CALCULATE statement at the beginning of the script.</span></span>  
  
 <span data-ttu-id="ab18e-110">如需 CALCULATE 陳述式語法的詳細資訊，請參閱 [CALCULATE 陳述式 &#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate)。</span><span class="sxs-lookup"><span data-stu-id="ab18e-110">For more information on the syntax of the CALCULATE statement, see [CALCULATE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-calculate).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab18e-111">如果指令碼包含了內含 CALCULATE 陳述式的 SCOPE 陳述式，MDX 會評估 SCOPE 陳述式定義之 Subcube 內容內的 CALCULATE 陳述式，而不是評估整個 Cube。</span><span class="sxs-lookup"><span data-stu-id="ab18e-111">If the script contains a SCOPE statement that contains a CALCULATE statement, MDX evaluates the CALCULATE statement within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
## <a name="using-the-this-function"></a><span data-ttu-id="ab18e-112">使用 This 函數</span><span class="sxs-lookup"><span data-stu-id="ab18e-112">Using the This Function</span></span>  
 <span data-ttu-id="ab18e-113">您可以使用 `This` 函數擷取目前在 MDX 指令碼內的 Subcube。</span><span class="sxs-lookup"><span data-stu-id="ab18e-113">The `This` function lets you retrieve the current subcube within an MDX script.</span></span> <span data-ttu-id="ab18e-114">您可以使用 `This` 函數對 MDX 運算式快速地設定目前  Subcube 內的資料格值。</span><span class="sxs-lookup"><span data-stu-id="ab18e-114">You can use the `This` function to quickly set the value of cells within the current subcube to an MDX expression.</span></span> <span data-ttu-id="ab18e-115">您通常會使用 `This` 函數配合 SCOPE 陳述式，在特定的計算行程期間變更特定  Subcube 的內容。</span><span class="sxs-lookup"><span data-stu-id="ab18e-115">You often use the `This` function in conjunction with the SCOPE statement to change the contents of a specific subcube during a specific calculation pass.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab18e-116">如果指令碼包含了內含 `This` 函數的 SCOPE 陳述式，MDX 會評估 SCOPE 陳述式定義之 Subcube 的內容內的 `This` 函數，而不是評估整個 Cube。</span><span class="sxs-lookup"><span data-stu-id="ab18e-116">If the script contains a SCOPE statement that contains a `This` function, MDX evaluates the `This` function within the context of the subcube defined by the SCOPE statement, not against the whole cube.</span></span>  
  
### <a name="this-function-example"></a><span data-ttu-id="ab18e-117">This 函數範例</span><span class="sxs-lookup"><span data-stu-id="ab18e-117">This Function Example</span></span>  
 <span data-ttu-id="ab18e-118">在 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] 範例 Cube 的 Finance 量值群組中，下列 MDX 指令碼命令範例是使用 `This` 函數增加 Amount 量值的值，其比 Customer 維度中 Redmond 成員的子系高出 10%：</span><span class="sxs-lookup"><span data-stu-id="ab18e-118">The following MDX script command example uses the `This` function to increase the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension:</span></span>  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="ab18e-119">如需函數語法的詳細資訊 `This` ，請參閱[這 &#40;MDX&#41;](/sql/mdx/this-mdx)。</span><span class="sxs-lookup"><span data-stu-id="ab18e-119">For more information on the syntax of the `This` function, see [This &#40;MDX&#41;](/sql/mdx/this-mdx).</span></span>  
  
## <a name="using-the-scope-statement"></a><span data-ttu-id="ab18e-120">使用 SCOPE 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab18e-120">Using the SCOPE Statement</span></span>  
 <span data-ttu-id="ab18e-121">SCOPE 陳述式會定義目前的 Subcube，此 Subcube 包含 MDX 指令碼內的其他 MDX 運算式及陳述式，而且會指定它們的範圍。</span><span class="sxs-lookup"><span data-stu-id="ab18e-121">The SCOPE statement defines the current subcube that contains, and specifies the scope of, other MDX expressions and statements within an MDX script.</span></span> <span data-ttu-id="ab18e-122">MDX 會評估 Subcube 內容中此其他的 MDX 運算式及陳述式，包括 `This` 函數及 CALCULATE 陳述式在內。</span><span class="sxs-lookup"><span data-stu-id="ab18e-122">MDX evaluates this other MDX expressions and statements, including the `This` function and the CALCULATE statement, within the context of the subcube.</span></span>  
  
 <span data-ttu-id="ab18e-123">SCOPE 陳述式本質上是動態但不反覆。</span><span class="sxs-lookup"><span data-stu-id="ab18e-123">A SCOPE statement is dynamic, but not iterative in nature.</span></span> <span data-ttu-id="ab18e-124">SCOPE 陳述式內包含的陳述式只會執行一次，但可以動態地決定 Subcube 本身。</span><span class="sxs-lookup"><span data-stu-id="ab18e-124">The statements contained within a SCOPE statement run once, but the subcube itself can be dynamically determined.</span></span> <span data-ttu-id="ab18e-125">例如，您有一個稱為 SampleCube 的 Cube。</span><span class="sxs-lookup"><span data-stu-id="ab18e-125">For example, you have a cube named SampleCube.</span></span> <span data-ttu-id="ab18e-126">您可以對 SampleCube Cube 套用以下 SCOPE 陳述式，以定義在 Measures 維度內將內容定義為 ALLMEMBERS 的 Subcube：</span><span class="sxs-lookup"><span data-stu-id="ab18e-126">Against the SampleCube cube, you apply the following SCOPE statement to define a subcube the defines the context as the ALLMEMBERS within the Measures dimension:</span></span>  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 <span data-ttu-id="ab18e-127">this 函數的 SCOPE 陳述式內的陳述式及運算式只會執行一次。</span><span class="sxs-lookup"><span data-stu-id="ab18e-127">The statements and expressions within this SCOPE statement run once.</span></span>  
  
 <span data-ttu-id="ab18e-128">現在，商業使用者可以對 SampleCube Cube 執行以下包含一個稱為 ExistingMeasure 之量值的 MDX 查詢：</span><span class="sxs-lookup"><span data-stu-id="ab18e-128">Now, a business user runs the following MDX query that contains one measure, named ExistingMeasure, against the SampleCube cube:</span></span>  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 <span data-ttu-id="ab18e-129">查詢傳回的資料格集與下表顯示的輸出類似。</span><span class="sxs-lookup"><span data-stu-id="ab18e-129">The cellset returned from the query resembles the output shown in the following table.</span></span>  
  
||<span data-ttu-id="ab18e-130">[ExistingMeasure]</span><span class="sxs-lookup"><span data-stu-id="ab18e-130">[ExistingMeasure]</span></span>|<span data-ttu-id="ab18e-131">[NewMeasure]</span><span class="sxs-lookup"><span data-stu-id="ab18e-131">[NewMeasure]</span></span>|  
|-|-------------------------|--------------------|  
|<span data-ttu-id="ab18e-132">[Customer].[All]</span><span class="sxs-lookup"><span data-stu-id="ab18e-132">[Customer].[All]</span></span>|<span data-ttu-id="ab18e-133">2</span><span class="sxs-lookup"><span data-stu-id="ab18e-133">2</span></span>|<span data-ttu-id="ab18e-134">2</span><span class="sxs-lookup"><span data-stu-id="ab18e-134">2</span></span>|  
  
 <span data-ttu-id="ab18e-135">請查看傳回的資料格集，注意在定義量值 NewMeasure 之後，是如何動態更新 MDX 指令碼內的 SCOPE 陳述式包括的 ExistingMeasure 值，</span><span class="sxs-lookup"><span data-stu-id="ab18e-135">Looking at the returned cellset, notice how the ExistingMeasure value, included in the SCOPE statement within the MDX script, is dynamically updated after the measure NewMeasure was defined.</span></span>  
  
 <span data-ttu-id="ab18e-136">SCOPE 陳述式在另一個 SCOPE 陳述式內可為巢狀。</span><span class="sxs-lookup"><span data-stu-id="ab18e-136">A SCOPE statement can be nested within another SCOPE statement.</span></span> <span data-ttu-id="ab18e-137">但是，因為 SCOPE 陳述式不會反覆執行，巢狀 SCOPE 陳述式的主要用途是為了進行特殊處理而進一步細分 Subcube。</span><span class="sxs-lookup"><span data-stu-id="ab18e-137">However, as the SCOPE statement is not iterative, the primary purpose for nesting SCOPE statements is to further subdivide a subcube for special treatment.</span></span>  
  
### <a name="scope-statement-example"></a><span data-ttu-id="ab18e-138">SCOPE 陳述式範例</span><span class="sxs-lookup"><span data-stu-id="ab18e-138">SCOPE Statement Example</span></span>  
 <span data-ttu-id="ab18e-139">下列 MDX 指令碼範例在 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] 範例 Cube 的 Finance 量值群組中，使用 SCOPE 陳述式將 Amount 量值的值設為高於 Customer 維度中 Redmond 成員的子系 10%。</span><span class="sxs-lookup"><span data-stu-id="ab18e-139">The following MDX script example uses a SCOPE statement to sets the value of the Amount measure, in the Finance measure group of the [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] sample cube, to 10% higher for the children of the Redmond member in the Customer dimension.</span></span> <span data-ttu-id="ab18e-140">但是，其他 SCOPE 陳述式會變更 Subcube 以包括 2002 日曆年度之子系的 Amount 量值。</span><span class="sxs-lookup"><span data-stu-id="ab18e-140">However, another SCOPE statement changes the subcube to include the Amount measure for the children of the 2002 calendar year.</span></span> <span data-ttu-id="ab18e-141">最後，Amount 量值指會對那個 Subcube 進行彙總，而讓其他日曆年度中 Amount 量值的彙總值保持不變。</span><span class="sxs-lookup"><span data-stu-id="ab18e-141">Finally, the Amount measure is then aggregated only for that subcube, leaving the aggregated values for the Amount measure in other calendar years unchanged.</span></span>  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 <span data-ttu-id="ab18e-142">如需 SCOPE 陳述式語法的詳細資訊，請參閱 [SCOPE 陳述式 &#40;MDX&#41;](/sql/mdx/mdx-scripting-scope)。</span><span class="sxs-lookup"><span data-stu-id="ab18e-142">For more information on the syntax of the SCOPE statement, see [SCOPE Statement &#40;MDX&#41;](/sql/mdx/mdx-scripting-scope).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab18e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab18e-143">See Also</span></span>  
 <span data-ttu-id="ab18e-144">[Mdx 語言參考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="ab18e-144">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 <span data-ttu-id="ab18e-145">[基本 MDX 腳本 &#40;MDX&#41;](the-basic-mdx-script-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="ab18e-145">[The Basic MDX Script &#40;MDX&#41;](the-basic-mdx-script-mdx.md) </span></span>  
 [<span data-ttu-id="ab18e-146">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ab18e-146">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
