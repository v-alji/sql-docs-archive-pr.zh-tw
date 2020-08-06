---
title: 基本 MDX 腳本 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default MDX scripts
- statements [MDX]
- expressions [MDX], scripts
- scripts [MDX], about scripts
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
author: minewiskan
ms.author: owend
ms.openlocfilehash: de0d2fea002beda0eca480bd27140bdd202fcb83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705578"
---
# <a name="the-basic-mdx-script-mdx"></a><span data-ttu-id="78b75-102">基本 MDX 指令碼 (MDX)</span><span class="sxs-lookup"><span data-stu-id="78b75-102">The Basic MDX Script (MDX)</span></span>
  <span data-ttu-id="78b75-103"> (MDX) 腳本的多維度運算式會定義中 cube 的計算進程 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="78b75-103">A Multidimensional Expressions (MDX) script defines the calculation process for a cube in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="78b75-104">MDX 指令碼有以下兩種類型：</span><span class="sxs-lookup"><span data-stu-id="78b75-104">There are two types of MDX scripts:</span></span>  
  
 <span data-ttu-id="78b75-105">**預設的 MDX 指令碼**</span><span class="sxs-lookup"><span data-stu-id="78b75-105">**The default MDX script**</span></span>  
 <span data-ttu-id="78b75-106">當您建立 Cube 時， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會為那個 Cube 建立預設的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="78b75-106">At the time that you create a cube, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates a default MDX script for that cube.</span></span> <span data-ttu-id="78b75-107">此指令碼會定義整個 Cube 的計算行程。</span><span class="sxs-lookup"><span data-stu-id="78b75-107">This script defines a calculation pass for the whole cube.</span></span>  
  
 <span data-ttu-id="78b75-108">**使用者自訂 MDX 指令碼**</span><span class="sxs-lookup"><span data-stu-id="78b75-108">**User-defined MDX script**</span></span>  
 <span data-ttu-id="78b75-109">建立 Cube 之後，您可以增加擴充 Cube 之計算能力的使用者自訂 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="78b75-109">After you have created a cube, you can add user-defined MDX scripts that extend the calculation capabilities of the cube.</span></span>  
  
## <a name="the-default-mdx-script"></a><span data-ttu-id="78b75-110">預設的 MDX 指令碼</span><span class="sxs-lookup"><span data-stu-id="78b75-110">The Default MDX Script</span></span>  
 <span data-ttu-id="78b75-111">當您定義的 Cube 包含一個 CALCULATE 陳述式時， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 就會建立預設的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="78b75-111">The default MDX script that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] creates when you define a cube contains a single CALCULATE statement.</span></span> <span data-ttu-id="78b75-112">這一個 CALCULATE 陳述式位於預設 MDX 指令碼的開始處，而且可指出在第一個計算行程期間應要計算的整個 Cube。</span><span class="sxs-lookup"><span data-stu-id="78b75-112">This single CALCULATE statement is at the beginning of the default MDX script, and indicates that the entire cube should be calculated during the first calculation pass.</span></span>  
  
 <span data-ttu-id="78b75-113">預設的 MDX 指令碼也包含指令碼命令，此命令可以建立命名集、指派，以及「Cube 設計師」中建立的導出成員：</span><span class="sxs-lookup"><span data-stu-id="78b75-113">The default MDX script also contains the script commands that create named sets, assignments, and calculated members created in Cube Designer:</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="78b75-114">會將指令碼命令直接增加到預設的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="78b75-114">directly adds script commands to the default MDX script.</span></span>  
  
-   <span data-ttu-id="78b75-115">對於 Cube 中的每個命名集，預設的 MDX 指令碼中會有對應的 CREATE SET 陳述式存在。</span><span class="sxs-lookup"><span data-stu-id="78b75-115">For each named set in the cube, a corresponding CREATE SET statement exists in the default MDX script.</span></span>  
  
-   <span data-ttu-id="78b75-116">對於 Cube 中定義的每個導出成員，預設的 MDX 指令碼中會有對應的 CREATE MEMBER 陳述式存在。</span><span class="sxs-lookup"><span data-stu-id="78b75-116">For each calculated member defined in the cube, a corresponding CREATE MEMBER statement exists in the default MDX script.</span></span>  
  
 <span data-ttu-id="78b75-117">您可以使用 Cube 設計師的 [計算]\*\*\*\* 索引標籤，在預設的 MDX 指令碼中、控制指令碼命令、命名集與導出成員的順序。</span><span class="sxs-lookup"><span data-stu-id="78b75-117">You can control the order of script commands, named sets, and calculated members in the default MDX script by using the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="78b75-118">如需定義預設 MDX 指令碼中儲存之計算的詳細資訊，請參閱 [多維度模型中的計算](../calculations-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="78b75-118">For more information on defining calculations stored in the default MDX script, see [Calculations in Multidimensional Models](../calculations-in-multidimensional-models.md).</span></span>  
  
 <span data-ttu-id="78b75-119">如果沒有與 Cube 相關的  MDX 指令碼，Cube 會假設與其相關的是預設的 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="78b75-119">If there is no MDX script associated with a cube, the cube assumes the default MDX script.</span></span> <span data-ttu-id="78b75-120">因為 Cube 仰賴 MDX 指令碼來決定計算行為，所以 Cube 必須至少與一個 MDX 指令碼相關。</span><span class="sxs-lookup"><span data-stu-id="78b75-120">A cube needs to be associated with at least one MDX script because a cube relies on the MDX script to determine calculation behavior.</span></span> <span data-ttu-id="78b75-121">換句話說，沒有與 Cube 相關的 MDX 指令碼，或是與空白 MDX 指令碼相關的 Cube ，無法計算任何資料格。</span><span class="sxs-lookup"><span data-stu-id="78b75-121">In other words, a cube that was not associated with an MDX script or was associated with an empty MDX script could not and would not be able to calculate any cells.</span></span> <span data-ttu-id="78b75-122">如果使用 Analysis Services 指令碼語言 (ASSL) 命令，或使用分析管理物件 (AMO)， 透過設計程式的方式建立 Cube，建議您建立會包含該 Cube 的單一 CALCULATE 陳述式的預設 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="78b75-122">If you programmatically create cubes, either by using Analysis Services Scripting Language (ASSL) commands or by using Analysis Management Objects (AMO), it is recommended that you create a default MDX script containing a single CALCULATE statement for the cube.</span></span>  
  
## <a name="mdx-script-content"></a><span data-ttu-id="78b75-123">MDX 指令碼內容</span><span class="sxs-lookup"><span data-stu-id="78b75-123">MDX Script Content</span></span>  
 <span data-ttu-id="78b75-124">MDX 指令碼可包含以下陳述式及運算式：</span><span class="sxs-lookup"><span data-stu-id="78b75-124">An MDX script can contain the following statements and expressions:</span></span>  
  
 <span data-ttu-id="78b75-125">所有 MDX 指令碼陳述式</span><span class="sxs-lookup"><span data-stu-id="78b75-125">All MDX scripting statements</span></span>  
 <span data-ttu-id="78b75-126">在 MDX 指令碼中，MDX 指令碼陳述式可控制計算的內容及範圍，還能管理 MDX 指令碼中其他陳述式的行為。</span><span class="sxs-lookup"><span data-stu-id="78b75-126">In MDX scripts, MDX scripting statements control the context and scope of calculations, and manage the behavior of other statements in the MDX script.</span></span> <span data-ttu-id="78b75-127">此類別目錄包括以下陳述式：</span><span class="sxs-lookup"><span data-stu-id="78b75-127">This category includes the following statements:</span></span>  
  
-   [<span data-ttu-id="78b75-128">算</span><span class="sxs-lookup"><span data-stu-id="78b75-128">CALCULATE</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
-   [<span data-ttu-id="78b75-129">暫時</span><span class="sxs-lookup"><span data-stu-id="78b75-129">FREEZE</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
-   [<span data-ttu-id="78b75-130">範圍</span><span class="sxs-lookup"><span data-stu-id="78b75-130">SCOPE</span></span>](/sql/mdx/mdx-scripting-scope)  
  
 <span data-ttu-id="78b75-131">如需 MDX 指令碼陳述式的詳細資訊，請參閱 [MDX 指令碼陳述式 &#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx)。</span><span class="sxs-lookup"><span data-stu-id="78b75-131">For more information on MDX scripting statements, see [MDX Scripting Statements &#40;MDX&#41;](/sql/mdx/mdx-scripting-statements-mdx).</span></span>  
  
 [<span data-ttu-id="78b75-132">CREATE MEMBER</span><span class="sxs-lookup"><span data-stu-id="78b75-132">CREATE MEMBER</span></span>](/sql/mdx/mdx-data-definition-create-member)  
 <span data-ttu-id="78b75-133">CREATE MEMBER 陳述式可建立導出成員。</span><span class="sxs-lookup"><span data-stu-id="78b75-133">The CREATE MEMBER statement creates calculated members.</span></span> <span data-ttu-id="78b75-134">如需如何建立導出成員的詳細資訊，請參閱[在 MDX 中建立導出成員 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)。</span><span class="sxs-lookup"><span data-stu-id="78b75-134">For more information about how to create calculated members, see [Building Calculated Members in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).</span></span>  
  
 [<span data-ttu-id="78b75-135">CREATE SET</span><span class="sxs-lookup"><span data-stu-id="78b75-135">CREATE SET</span></span>](/sql/mdx/mdx-data-definition-create-set)  
 <span data-ttu-id="78b75-136">CREATE SET 陳述式可建立命名集。</span><span class="sxs-lookup"><span data-stu-id="78b75-136">The CREATE SET statement creates named sets.</span></span> <span data-ttu-id="78b75-137">如需如何建立命名集的詳細資訊，請參閱[在 MDX 中建立命名集 &#40;MDX&#41;](mdx-named-sets-building-named-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="78b75-137">For more information about how to create names sets, see [Building Named Sets in MDX &#40;MDX&#41;](mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="78b75-138">條件陳述式</span><span class="sxs-lookup"><span data-stu-id="78b75-138">Conditional statements</span></span>  
 <span data-ttu-id="78b75-139">條件陳述式可將條件式邏輯加入 MDX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="78b75-139">Conditional statements add conditional logic to MDX scripts.</span></span> <span data-ttu-id="78b75-140">此類別目錄包括 [CASE](/sql/mdx/case-statement-mdx) 及 [IF](/sql/mdx/mdx-scripting-if) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="78b75-140">This category includes the [CASE](/sql/mdx/case-statement-mdx) and [IF](/sql/mdx/mdx-scripting-if) statements.</span></span>  
  
 <span data-ttu-id="78b75-141">指派運算式</span><span class="sxs-lookup"><span data-stu-id="78b75-141">Assignment expressions</span></span>  
 <span data-ttu-id="78b75-142">指派陳述式可將運算式 (例如一個值) 指派給受條件約束的 Subcube。</span><span class="sxs-lookup"><span data-stu-id="78b75-142">An assignment expression assigns an expression, such as a value, to a constrained subcube.</span></span> <span data-ttu-id="78b75-143">受條件約束的 Subcube 運算式是受條件約束之集合運算式的集合，定義了 MDX 指令碼內 Subcube 的「邊緣」。</span><span class="sxs-lookup"><span data-stu-id="78b75-143">A constrained subcube expression is a collection of constrained set expressions that define the "edges" of a subcube within an MDX script.</span></span> <span data-ttu-id="78b75-144">以下程式顯示受條件約束的 Subcube 運算式語法：</span><span class="sxs-lookup"><span data-stu-id="78b75-144">The following codes shows the syntax for a constrained subcube expression:</span></span>  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## <a name="see-also"></a><span data-ttu-id="78b75-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78b75-145">See Also</span></span>  
 <span data-ttu-id="78b75-146">[Mdx 語言參考 &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="78b75-146">[MDX Language Reference &#40;MDX&#41;](/sql/mdx/mdx-language-reference-mdx) </span></span>  
 [<span data-ttu-id="78b75-147">MDX 指令碼基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="78b75-147">MDX Scripting Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-scripting-fundamentals-analysis-services.md)  
  
  
