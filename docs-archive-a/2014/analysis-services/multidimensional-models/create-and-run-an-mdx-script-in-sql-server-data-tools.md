---
title: 在 SQL Server Data Tools 中建立和執行 MDX 腳本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], scripts
- scripts [Analysis Services], creating
- scripts [MDX], creating
ms.assetid: aa54b8cc-ff3b-4ef6-a64e-11b9e9d7fa11
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0c1088bd9920364d46117624673f27f09cf38b34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585643"
---
# <a name="create-and-run-an-mdx-script-in-sql-server-data-tools"></a><span data-ttu-id="ccb30-102">在 SQL Server 資料工具中建立及執行 MDX 指令碼</span><span class="sxs-lookup"><span data-stu-id="ccb30-102">Create and Run an MDX Script in SQL Server Data Tools</span></span>
  <span data-ttu-id="ccb30-103">若要在  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中建立和執行 MDX 指令碼，您必須是在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中且已建立 Cube，並準備就緒可供編輯。</span><span class="sxs-lookup"><span data-stu-id="ccb30-103">To create and run an MDX Script in  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you need to be in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] with a cube already created and ready for editing.</span></span>  
  
### <a name="to-create-a-multidimensional-expressions-mdx-script"></a><span data-ttu-id="ccb30-104">若要建立多維度運算式 (MDX) 指令碼</span><span class="sxs-lookup"><span data-stu-id="ccb30-104">To create a Multidimensional Expressions (MDX) script</span></span>  
  
1.  <span data-ttu-id="ccb30-105">開啟要建立 MDX 指令碼的 Cube，然後在 [檢視]\*\*\*\* 之下，按一下 [計算]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ccb30-105">Open the cube for which you want to create an MDX script, and under **View**, click **Calculations**.</span></span>  
  
2.  <span data-ttu-id="ccb30-106">如果不是處於 [指令碼檢視]\*\*\*\* 模式，請按一下**指令碼檢視**圖示。</span><span class="sxs-lookup"><span data-stu-id="ccb30-106">If you are not in **Script View** mode, click the **Script View** icon.</span></span>  
  
3.  <span data-ttu-id="ccb30-107">在指令碼視窗中，於 CALCULATE 命令之下，輸入 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="ccb30-107">In the script window, under the CALCULATE command, type an MDX expression.</span></span> <span data-ttu-id="ccb30-108">按一下 **檢查語法** 圖示，並確認運算式的語法正確。</span><span class="sxs-lookup"><span data-stu-id="ccb30-108">Click the **Check Syntax** icon and verify that the expression is syntactically correct.</span></span>  
  
4.  <span data-ttu-id="ccb30-109">若要執行 MDX 指令碼，請使用新的 MDX 指令碼變更來部署和處理 Cube。</span><span class="sxs-lookup"><span data-stu-id="ccb30-109">To run the MDX script, deploy and process the cube with the new MDX script changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb30-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccb30-110">See Also</span></span>  
 <span data-ttu-id="ccb30-111">[基本 MDX 腳本 &#40;MDX&#41;](mdx/the-basic-mdx-script-mdx.md) </span><span class="sxs-lookup"><span data-stu-id="ccb30-111">[The Basic MDX Script &#40;MDX&#41;](mdx/the-basic-mdx-script-mdx.md) </span></span>  
 <span data-ttu-id="ccb30-112">[MDX 腳本基礎 &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="ccb30-112">[MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md) </span></span>  
 [<span data-ttu-id="ccb30-113">MDX 指令碼陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="ccb30-113">MDX Scripting Statements &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-statements-mdx)  
  
  
