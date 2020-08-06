---
title: 建立命名集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
author: minewiskan
ms.author: owend
ms.openlocfilehash: e92984102ceb8ad0ac049c15870e9f1efd6090fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687297"
---
# <a name="create-named-sets"></a><span data-ttu-id="bca3e-102">建立命名集</span><span class="sxs-lookup"><span data-stu-id="bca3e-102">Create Named Sets</span></span>
  <span data-ttu-id="bca3e-103">命名集是維度成員集或為了重複使用而建立的集運算式，例如使用於多維度運算式 (MDX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="bca3e-103">A named set is a set of dimension members or a set expression that is created for reuse, for example in Multidimensional Expressions (MDX) queries.</span></span> <span data-ttu-id="bca3e-104">您可以結合 Cube 資料、算術運算子、數字和函數來建立命名集。</span><span class="sxs-lookup"><span data-stu-id="bca3e-104">You can create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="bca3e-105">例如，您可以建立一個叫作 Top Ten Factories 的命名集，包含 Factories 維度中 Production 量值最高的 10 個成員。</span><span class="sxs-lookup"><span data-stu-id="bca3e-105">For example, you can create a named set called Top Ten Factories that contains the ten members of the Factories dimension that have the highest values for the Production measure.</span></span> <span data-ttu-id="bca3e-106">然後使用者可以在查詢中使用 Top Ten Factories。</span><span class="sxs-lookup"><span data-stu-id="bca3e-106">Top Ten Factories can then be used in queries by end users.</span></span> <span data-ttu-id="bca3e-107">例如，使用者可將 Top Ten Factories 放在一個軸上，將 Measures 維度 (包括 Production 在內) 放在另一個軸上。</span><span class="sxs-lookup"><span data-stu-id="bca3e-107">For example, an end user can place Top Ten Factories on one axis and the Measures dimension, including Production, on another axis.</span></span> <span data-ttu-id="bca3e-108">如需詳細資訊，請參閱 [Calculations in Multidimensional Models](calculations-in-multidimensional-models.md) (多維度模型中的計算) 和 [Building Named Sets in MDX &#40;MDX&#41;](mdx/mdx-named-sets-building-named-sets.md) (在 MDX 中建立命名集 (MDX))。</span><span class="sxs-lookup"><span data-stu-id="bca3e-108">For more information, see [Calculations in Multidimensional Models](calculations-in-multidimensional-models.md), and [Building Named Sets in MDX &#40;MDX&#41;](mdx/mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="bca3e-109">若要建立命名集，請在 Cube 設計師的 **[計算]** 索引標籤上，使用 **[新增命名集]** 命令。</span><span class="sxs-lookup"><span data-stu-id="bca3e-109">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="bca3e-110">可在 **[計算]** 索引標籤工具列的 **[Cube]** 功能表上叫用此命令。</span><span class="sxs-lookup"><span data-stu-id="bca3e-110">This command can be invoked on the **Cube** menu on the **Calculations** tab toolbar.</span></span> <span data-ttu-id="bca3e-111">此命令顯示一個表單來指定命名集的下列選項：</span><span class="sxs-lookup"><span data-stu-id="bca3e-111">This command displays a form to specify the following options for the named set:</span></span>  
  
 <span data-ttu-id="bca3e-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="bca3e-112">**Name**</span></span>  
 <span data-ttu-id="bca3e-113">選取命名集的名稱。</span><span class="sxs-lookup"><span data-stu-id="bca3e-113">Select the name of the named set.</span></span> <span data-ttu-id="bca3e-114">使用者瀏覽 Cube 時出現的名稱。</span><span class="sxs-lookup"><span data-stu-id="bca3e-114">This name appears to end users when they browse the cube.</span></span>  
  
 <span data-ttu-id="bca3e-115">**運算式**</span><span class="sxs-lookup"><span data-stu-id="bca3e-115">**Expression**</span></span>  
 <span data-ttu-id="bca3e-116">指定產生命名集的運算式。</span><span class="sxs-lookup"><span data-stu-id="bca3e-116">Specify the expression that produces the named set.</span></span> <span data-ttu-id="bca3e-117">可以用 MDX 撰寫此運算式。</span><span class="sxs-lookup"><span data-stu-id="bca3e-117">This expression can be written in MDX.</span></span> <span data-ttu-id="bca3e-118">運算式可以包含下列任一項：</span><span class="sxs-lookup"><span data-stu-id="bca3e-118">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="bca3e-119">代表 Cube 元件 (例如維度、層級、量值等等) 的資料運算式。</span><span class="sxs-lookup"><span data-stu-id="bca3e-119">Data expressions that represent cube components such as dimensions, levels, measures, and so on.</span></span>  
  
-   <span data-ttu-id="bca3e-120">算術運算子。</span><span class="sxs-lookup"><span data-stu-id="bca3e-120">Arithmetic operators.</span></span>  
  
-   <span data-ttu-id="bca3e-121">數字。</span><span class="sxs-lookup"><span data-stu-id="bca3e-121">Numbers.</span></span>  
  
-   <span data-ttu-id="bca3e-122">函數。</span><span class="sxs-lookup"><span data-stu-id="bca3e-122">Functions.</span></span>  
  
 <span data-ttu-id="bca3e-123">您可以從 **[計算工具]** 窗格的 **[中繼資料]** 索引標籤中，將 Cube 元件複製或拖曳至 **[命名集表單編輯器]** 窗格的 **[運算式]** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="bca3e-123">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span> <span data-ttu-id="bca3e-124">您可以從 **[計算工具]** 窗格的 **[函數]** 索引標籤中，將函數複製或拖曳至 **[命名集表單編輯器]** 窗格的 **[運算式]** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="bca3e-124">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bca3e-125">如果您藉由明確命名集合中的成員來建立集合運算式，請以一對大括弧括住成員清單， ({}) 。</span><span class="sxs-lookup"><span data-stu-id="bca3e-125">If you create the set expression by explicitly naming the members in the set, enclose the list of members in a pair of braces ({}).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca3e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bca3e-126">See Also</span></span>  
 [<span data-ttu-id="bca3e-127">多維度模型中的計算</span><span class="sxs-lookup"><span data-stu-id="bca3e-127">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
