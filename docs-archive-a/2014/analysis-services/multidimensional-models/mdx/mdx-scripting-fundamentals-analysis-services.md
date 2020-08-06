---
title: MDX 腳本基礎 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2f7638339d8fc366ee384d453f6df683f3bd41f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598613"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a><span data-ttu-id="44a3e-102">MDX 指令碼基礎觀念 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="44a3e-102">MDX Scripting Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="44a3e-103">在中 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ，多維度運算式 (MDX) 腳本是由一個或多個 mdx 運算式或語句所組成，其中會填入具有計算的 cube。</span><span class="sxs-lookup"><span data-stu-id="44a3e-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script is made up of one or more MDX expressions or statements that populate a cube with calculations.</span></span>  
  
 <span data-ttu-id="44a3e-104">MDX 指令碼可定義 Cube 的計算處理序。</span><span class="sxs-lookup"><span data-stu-id="44a3e-104">An MDX script defines the calculation process for a cube.</span></span> <span data-ttu-id="44a3e-105">MDX 指令碼也會被視為 Cube 本身的一部分。</span><span class="sxs-lookup"><span data-stu-id="44a3e-105">An MDX script is also considered part of the cube itself.</span></span> <span data-ttu-id="44a3e-106">因此，變更與 Cube 相關的 MDX 指令碼，會立即變更 Cube 的計算處理序。</span><span class="sxs-lookup"><span data-stu-id="44a3e-106">Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.</span></span>  
  
 <span data-ttu-id="44a3e-107">若要建立 MDX 指令碼，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中的 Cube 設計師。</span><span class="sxs-lookup"><span data-stu-id="44a3e-107">To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="44a3e-108">如需詳細資訊，請參閱 [定義指派和其他指令碼命令](../define-assignments-and-other-script-commands.md)[Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892)(Microsoft SQL Server 2005 中 MDX 指令碼的簡介)。</span><span class="sxs-lookup"><span data-stu-id="44a3e-108">For more information, see [Define Assignments and Other Script Commands](../define-assignments-and-other-script-commands.md) and [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span>  
  
 <span data-ttu-id="44a3e-109">如需 MDX 查詢和計算的效能相關問題，請參閱 [SQL Server Analysis Services Performance Guide](https://go.microsoft.com/fwlink/p/?LinkId=399050)(SQL Server Analysis Services 效能指南) 中的＜MDX optimization (MDX 最佳化)＞一節。</span><span class="sxs-lookup"><span data-stu-id="44a3e-109">For performance issues related to MDX queries and calculations, see the MDX optimization section in the [SQL Server Analysis Services Performance Guide](https://go.microsoft.com/fwlink/p/?LinkId=399050).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44a3e-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="44a3e-110">In This Section</span></span>  
  
|<span data-ttu-id="44a3e-111">主題</span><span class="sxs-lookup"><span data-stu-id="44a3e-111">Topic</span></span>|<span data-ttu-id="44a3e-112">描述</span><span class="sxs-lookup"><span data-stu-id="44a3e-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="44a3e-113">基本 MDX 指令碼 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="44a3e-113">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)|<span data-ttu-id="44a3e-114">詳細說明基本的 MDX 指令碼，包括每個 Cube 提供的預設 MDX 指令碼，以及在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]中，MDX 指令碼一般會如何在 Cube 內運作。</span><span class="sxs-lookup"><span data-stu-id="44a3e-114">Details the basic MDX script, including the default MDX script provided in each cube, and how MDX scripts generally function within a cube in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="44a3e-115">管理範圍及內容 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="44a3e-115">Managing Scope and Context &#40;MDX&#41;</span></span>](managing-scope-and-context-mdx.md)|<span data-ttu-id="44a3e-116">描述如何使用 [CALCULATE](/sql/mdx/mdx-scripting-calculate) 陳述式、 [SCOPE](/sql/mdx/mdx-scripting-scope) 陳述式及 [This](/sql/mdx/this-mdx) 函數，管理 MDX 指令碼內的內容與範圍。</span><span class="sxs-lookup"><span data-stu-id="44a3e-116">Describes how to use the [CALCULATE](/sql/mdx/mdx-scripting-calculate) statement, the [SCOPE](/sql/mdx/mdx-scripting-scope) statement, and the [This](/sql/mdx/this-mdx) function to manage context and scope within an MDX script.</span></span>|  
|[<span data-ttu-id="44a3e-117">使用變數與參數 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="44a3e-117">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="44a3e-118">描述如何使用 MDX 指令碼中的變數與參數。</span><span class="sxs-lookup"><span data-stu-id="44a3e-118">Describes how to use variables and parameters in an MDX script.</span></span>|  
|[<span data-ttu-id="44a3e-119">錯誤處理 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="44a3e-119">Error Handling &#40;MDX&#41;</span></span>](error-handling-mdx.md)|<span data-ttu-id="44a3e-120">說明 MDX 指令碼內的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="44a3e-120">Explains error handling within an MDX script.</span></span>|  
|[<span data-ttu-id="44a3e-121">支援的 MDX &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="44a3e-121">Supported MDX &#40;MDX&#41;</span></span>](supported-mdx-mdx.md)|<span data-ttu-id="44a3e-122">提供 MDX 指令碼內支援的 MDX 運算子、陳述式及函數的清單。</span><span class="sxs-lookup"><span data-stu-id="44a3e-122">Provides a list of supported MDX operators, statements, and functions within an MDX script.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44a3e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44a3e-123">See Also</span></span>  
 [<span data-ttu-id="44a3e-124">MDX 語言參考 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="44a3e-124">MDX Language Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-language-reference-mdx)  
  
  
