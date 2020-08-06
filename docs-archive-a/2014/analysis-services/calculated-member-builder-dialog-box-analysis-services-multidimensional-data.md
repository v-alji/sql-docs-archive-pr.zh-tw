---
title: 匯出成員產生器對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.calculatedmemberbuilderdialog.f1
ms.assetid: 73b89a9f-f403-4ab8-99f7-e3ceb870c260
author: minewiskan
ms.author: owend
ms.openlocfilehash: 240e2f2471bf77c403119fd51278a975badc8358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593095"
---
# <a name="calculated-member-builder-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="3c585-102">導出成員產生器對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="3c585-102">Calculated Member Builder Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3c585-103">使用 **中的** [導出成員產生器] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 對話方塊，即可建立導出成員。</span><span class="sxs-lookup"><span data-stu-id="3c585-103">Use the **Calculated Member Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to build a calculated member.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3c585-104">選項</span><span class="sxs-lookup"><span data-stu-id="3c585-104">Options</span></span>  
  
|<span data-ttu-id="3c585-105">詞彙</span><span class="sxs-lookup"><span data-stu-id="3c585-105">Term</span></span>|<span data-ttu-id="3c585-106">定義</span><span class="sxs-lookup"><span data-stu-id="3c585-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="3c585-107">**名稱**</span><span class="sxs-lookup"><span data-stu-id="3c585-107">**Name**</span></span>|<span data-ttu-id="3c585-108">鍵入導出成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c585-108">Type the name of the calculated member.</span></span>|  
|<span data-ttu-id="3c585-109">**父階層**</span><span class="sxs-lookup"><span data-stu-id="3c585-109">**Parent Hierarchy**</span></span>|<span data-ttu-id="3c585-110">選取導出成員建立所在的階層。</span><span class="sxs-lookup"><span data-stu-id="3c585-110">Select the hierarchy in which to create the calculated member.</span></span>|  
|<span data-ttu-id="3c585-111">**父成員**</span><span class="sxs-lookup"><span data-stu-id="3c585-111">**Parent Member**</span></span>|<span data-ttu-id="3c585-112">如果您選取有一個以上層級的父階層 (不同於 `Measures` 維度)，就會啟用這個選項。</span><span class="sxs-lookup"><span data-stu-id="3c585-112">This option is enabled if you select a parent hierarchy (other than the `Measures` dimension) that has more than one level.</span></span> <span data-ttu-id="3c585-113">按一下省略號 (**...**) ] 按鈕以選取父成員。</span><span class="sxs-lookup"><span data-stu-id="3c585-113">Click the ellipsis (**...**) button to select a parent member.</span></span> <span data-ttu-id="3c585-114">此父成員會決定導出成員在維度結構內的位置。</span><span class="sxs-lookup"><span data-stu-id="3c585-114">The parent member determines the location of the calculated member in the dimension structure.</span></span>|  
|<span data-ttu-id="3c585-115">**運算式**</span><span class="sxs-lookup"><span data-stu-id="3c585-115">**Expression**</span></span>|<span data-ttu-id="3c585-116">輸入將要使用的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="3c585-116">Type the MDX expression that will be used.</span></span>|  
|<span data-ttu-id="3c585-117">**檢查**</span><span class="sxs-lookup"><span data-stu-id="3c585-117">**Check**</span></span>|<span data-ttu-id="3c585-118">按一下 **[檢查]** 即可測試 **[運算式]** 中所定義的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="3c585-118">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="3c585-119">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="3c585-119">**Metadata**</span></span>|<span data-ttu-id="3c585-120">顯示目前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的中繼資料，這可以包含在 **[運算式]** 中所定義的 MDX 運算式內。</span><span class="sxs-lookup"><span data-stu-id="3c585-120">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="3c585-121">以滑鼠右鍵按一下選取的項目，並選取 [複製]\*\*\*\*，或是將選取的項目拖曳至 [運算式]\*\*\*\*，即可複製該項目的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="3c585-121">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="3c585-122">**函式**</span><span class="sxs-lookup"><span data-stu-id="3c585-122">**Functions**</span></span>|<span data-ttu-id="3c585-123">顯示目前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體可用的 MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="3c585-123">Displays the available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="3c585-124">列出的項目擷取自 MDSCHEMA_FUNCTIONS 結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="3c585-124">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="3c585-125">以滑鼠右鍵按一下選取的項目，並選取 [複製]\*\*\*\*，或是將選取的項目拖曳至 [運算式]\*\*\*\*，即可複製該項目的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="3c585-125">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy**, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c585-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c585-126">See Also</span></span>  
 [<span data-ttu-id="3c585-127">多維度運算式 &#40;MDX&#41 參考</span><span class="sxs-lookup"><span data-stu-id="3c585-127">Multidimensional Expressions &#40;MDX&#41; Reference</span></span>](/sql/mdx/multidimensional-expressions-mdx-reference)  
  
  
