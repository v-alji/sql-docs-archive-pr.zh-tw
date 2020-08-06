---
title: 更新 XMLA) 的資料格 (|Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c3d9a7c27533666c75102d9eac3b8311bfe4af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706873"
---
# <a name="updating-cells-xmla"></a><span data-ttu-id="de1c1-102">更新資料格 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="de1c1-102">Updating Cells (XMLA)</span></span>
  <span data-ttu-id="de1c1-103">您可以使用[UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla)命令來變更已針對 cube 回寫啟用的 cube 中一個或多個資料格的值。</span><span class="sxs-lookup"><span data-stu-id="de1c1-103">You can use the [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) command to change the value of one or more cells in a cube enabled for cube writeback.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="de1c1-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會針對包含要更新之資料格的每個資料分割，在個別的回寫資料表中儲存更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="de1c1-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stores the updated information in a separate writeback table for each partition that contains cells to be updated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="de1c1-105">`UpdateCells` 命令不支援在 Cube 回寫期間的配置。</span><span class="sxs-lookup"><span data-stu-id="de1c1-105">The `UpdateCells` command does not support allocations during cube writeback.</span></span> <span data-ttu-id="de1c1-106">若要使用已配置的回寫，您應該使用[語句](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla)命令來傳送多維度運算式 (MDX) UPDATE 語句。</span><span class="sxs-lookup"><span data-stu-id="de1c1-106">To use allocated writeback, you should use the [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command to send a Multidimensional Expressions (MDX) UPDATE statement.</span></span> <span data-ttu-id="de1c1-107">如需詳細資訊，請參閱[&#40;MDX&#41;的 UPDATE CUBE 語句](/sql/mdx/mdx-data-manipulation-update-cube)。</span><span class="sxs-lookup"><span data-stu-id="de1c1-107">For more information, see [UPDATE CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).</span></span>  
  
## <a name="specifying-cells"></a><span data-ttu-id="de1c1-108">指定資料格</span><span class="sxs-lookup"><span data-stu-id="de1c1-108">Specifying Cells</span></span>  
 <span data-ttu-id="de1c1-109">命令的[Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)屬性 `UpdateCells` 包含要更新的資料格。</span><span class="sxs-lookup"><span data-stu-id="de1c1-109">The [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) property of the `UpdateCells` command contains the cells to be updated.</span></span> <span data-ttu-id="de1c1-110">您可以使用資料格的序數，來識別 `Cell` 屬性中的每個資料格。</span><span class="sxs-lookup"><span data-stu-id="de1c1-110">You identify each cell in the `Cell` property using that cell's ordinal number.</span></span> <span data-ttu-id="de1c1-111">就概念而言， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cube 中的資料格數目就如同 cube*是*一維陣列，其中*p*是軸的數目。</span><span class="sxs-lookup"><span data-stu-id="de1c1-111">Conceptually, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numbers cells in a cube as if the cube were a *p*-dimensional array, where *p* is the number of axes.</span></span> <span data-ttu-id="de1c1-112">資料格的處理順序是以資料列為主。</span><span class="sxs-lookup"><span data-stu-id="de1c1-112">Cells are addressed in row-major order.</span></span> <span data-ttu-id="de1c1-113">下圖顯示計算資料格序數的公式。</span><span class="sxs-lookup"><span data-stu-id="de1c1-113">The following illustration shows the formula for calculating the ordinal number of a cell.</span></span>  
  
 <span data-ttu-id="de1c1-114">![計算資料格序數位置的公式](../../analysis-services/dev-guide/media/cellordinalformula.gif "計算資料格序數位置的公式")</span><span class="sxs-lookup"><span data-stu-id="de1c1-114">![Formula to calculate the cell ordinal position](../../analysis-services/dev-guide/media/cellordinalformula.gif "Formula to calculate the cell ordinal position")</span></span>  
  
 <span data-ttu-id="de1c1-115">一旦您知道資料格的序數之後，就可以在資料[格](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla)屬性的[value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla)屬性中，指定資料格的預期值。</span><span class="sxs-lookup"><span data-stu-id="de1c1-115">Once you know a cell's ordinal number, you can indicate the intended value of the cell in the [Value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) property of the [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de1c1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de1c1-116">See Also</span></span>  
 <span data-ttu-id="de1c1-117">[Update 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="de1c1-117">[Update Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span></span>  
 [<span data-ttu-id="de1c1-118">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="de1c1-118">Developing with XMLA in Analysis Services</span></span>](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
