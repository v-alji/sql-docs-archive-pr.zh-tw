---
title: MDX 產生器 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.mdxbuilderdialof.f1
helpviewer_keywords:
- MDX Builder dialog box
ms.assetid: fecbf093-65ea-4e1b-b637-f04876f1cb0f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 391f4abe953184470be60cca41d53ee20e965423
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596944"
---
# <a name="mdx-builder-analysis-services---multidimensional-data"></a><span data-ttu-id="4156f-102">MDX 產生器 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="4156f-102">MDX Builder (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="4156f-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 或 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [MDX 產生器]\*\*\*\* 對話方塊，即可建立多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="4156f-103">Use the **MDX Builder** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to build a Multidimensional Expressions (MDX) expression.</span></span> <span data-ttu-id="4156f-104">若要顯示 [ **mdx**產生器] 對話方塊，您可以按一下 [**允許讀取 cube 內容**] 選項、[允許讀取資料格內容（在資料**格之安全性上**）] 選項，或 [**角色設計師**] 的 [**資料格資料**] 頁面上的 [允許讀取**和寫入 cube**內容] 選項，) 的 [**編輯 MDX** ] 省略號按鈕 (**...** ]。</span><span class="sxs-lookup"><span data-stu-id="4156f-104">You can display the **MDX Builder** dialog box by clicking the **Edit MDX** ellipsis button (**...**) for the **Allow reading of cube content** option, the **Allow reading of cell content contingent on cell security** option, or the **Allow reading and writing of cube content** option on the **Cell Data** page of **Role Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4156f-105">選項</span><span class="sxs-lookup"><span data-stu-id="4156f-105">Options</span></span>  
  
|<span data-ttu-id="4156f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="4156f-106">Term</span></span>|<span data-ttu-id="4156f-107">定義</span><span class="sxs-lookup"><span data-stu-id="4156f-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="4156f-108">**運算式**</span><span class="sxs-lookup"><span data-stu-id="4156f-108">**Expression**</span></span>|<span data-ttu-id="4156f-109">鍵入要使用的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4156f-109">Type the MDX expression to be used.</span></span>|  
|<span data-ttu-id="4156f-110">**檢查**</span><span class="sxs-lookup"><span data-stu-id="4156f-110">**Check**</span></span>|<span data-ttu-id="4156f-111">按一下 **[檢查]** 即可測試 **[運算式]** 中所定義的 MDX 運算式。</span><span class="sxs-lookup"><span data-stu-id="4156f-111">Click **Check** to test the MDX expression defined in **Expression**.</span></span>|  
|<span data-ttu-id="4156f-112">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="4156f-112">**Metadata**</span></span>|<span data-ttu-id="4156f-113">顯示目前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件的中繼資料，這可以包含在 **[運算式]** 中所定義的 MDX 運算式內。</span><span class="sxs-lookup"><span data-stu-id="4156f-113">Displays metadata for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] object that can be included in the MDX expression defined in **Expression**.</span></span><br /><br /> <span data-ttu-id="4156f-114">以滑鼠右鍵按一下選取的項目，並從操作功能表中選取 [複製]\*\*\*\*，或是將選取的項目拖曳至 [運算式]\*\*\*\*，即可複製該項目的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4156f-114">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
|<span data-ttu-id="4156f-115">**函式**</span><span class="sxs-lookup"><span data-stu-id="4156f-115">**Functions**</span></span>|<span data-ttu-id="4156f-116">顯示目前 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體可用的 MDX 函數。</span><span class="sxs-lookup"><span data-stu-id="4156f-116">Displays available MDX functions for the current [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="4156f-117">列出的項目擷取自 MDSCHEMA_FUNCTIONS 結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="4156f-117">The items listed are retrieved from the MDSCHEMA_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="4156f-118">以滑鼠右鍵按一下選取的項目，並從操作功能表中選取 [複製]\*\*\*\*，或是將選取的項目拖曳至 [運算式]\*\*\*\*，即可複製該項目的 MDX 語法。</span><span class="sxs-lookup"><span data-stu-id="4156f-118">You can copy the MDX syntax for the selected item by right-clicking the item and selecting **Copy** from the context menu, or by dragging the selected item to **Expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4156f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4156f-119">See Also</span></span>  
 <span data-ttu-id="4156f-120">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="4156f-120">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="4156f-121">[&#40;角色設計工具的資料格資料&#41; &#40;Analysis Services 多維度資料&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="4156f-121">[Cell Data &#40;Role Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](https://msdn.microsoft.com/library/ms177279(v=sql.120).aspx)</span></span>  
  
  
