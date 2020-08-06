---
title: 分割區來源對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionsourcedialog.f1
ms.assetid: c414dabe-9bad-49b7-9a3c-dfca87fef92b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6732e8f00dc0d01e0d3b708794a1d9c497ae4cf5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686499"
---
# <a name="partition-source-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="43694-102">資料分割來源對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="43694-102">Partition Source Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="43694-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [資料分割來源]\*\*\*\* 對話方塊，即可指定資料分割之事實資料表資料的來源。</span><span class="sxs-lookup"><span data-stu-id="43694-103">Use the **Partition Source** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to specify the source of fact table data for a partition.</span></span> <span data-ttu-id="43694-104">您可依下列方式顯示 [資料分割來源]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="43694-104">You can display the **Partition Source** dialog box by:</span></span>  
  
-   <span data-ttu-id="43694-105">在 [Cube 設計師] 中的 [資料分割]\*\*\*\* 索引標籤上，於 [量值群組]\*\*\*\* 窗格中所選取量值群組的 [資料分割]\*\*\*\* 方格中，按一下資料格上的 [...]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="43694-105">Clicking the **...** button on a cell from the **Partitions** grid of a selected measure group in the **Measure Groups** pane on the **Partitions** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="43694-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [屬性]\*\*\*\* 視窗中，於 [資料分割]\*\*\*\* 物件的 [來源]\*\*\*\* 屬性值上，按一下 [...]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="43694-106">Clicking the **...** button on the **Source** property value of a **Partition** object in the **Properties** window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="43694-107">選項</span><span class="sxs-lookup"><span data-stu-id="43694-107">Options</span></span>  
  
|<span data-ttu-id="43694-108">選項</span><span class="sxs-lookup"><span data-stu-id="43694-108">Option</span></span>|<span data-ttu-id="43694-109">定義</span><span class="sxs-lookup"><span data-stu-id="43694-109">Definition</span></span>|  
|------------|----------------|  
|<span data-ttu-id="43694-110">**系結類型**</span><span class="sxs-lookup"><span data-stu-id="43694-110">**Binding type**</span></span>|<span data-ttu-id="43694-111">選取用於指定之資料分割來源的繫結類型。</span><span class="sxs-lookup"><span data-stu-id="43694-111">Select the binding type to use for the source of the specified partition.</span></span> <span data-ttu-id="43694-112">有下列選項可供使用：</span><span class="sxs-lookup"><span data-stu-id="43694-112">The following options are available:</span></span><br /><br /> <span data-ttu-id="43694-113">**資料表**系結：選取即可顯示 [資料表系結**詳細資料**] 窗格，並指出資料分割系結至資料來源或資料來源視圖中的資料表內容。</span><span class="sxs-lookup"><span data-stu-id="43694-113">**Table binding**: Select to display the **Table Binding Detail** pane and indicate that the partition is bound to the contents of a table in a data source or data source view.</span></span> <span data-ttu-id="43694-114">如需 [Table Binding Detail (資料表繫結詳細資料)]\*\*\*\* 窗格的詳細資訊，請參閱 [資料表繫結詳細資料 &#40;資料分割來源對話方塊&#41; &#40;Analysis Services - 多維度資料&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="43694-114">For more information about the **Table Binding Detail** pane, see [Table Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](table-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="43694-115">**詳細資料**：選取即可顯示 [查詢系結**詳細資料**] 窗格，並指出資料分割系結至在資料來源上執行之查詢的內容。</span><span class="sxs-lookup"><span data-stu-id="43694-115">**Detail**: Select to display the **Query Binding Detail** pane and indicate that the partition is bound to the contents of a query executed on a data source.</span></span> <span data-ttu-id="43694-116">如需 [Query Binding Detail (查詢繫結詳細資料)]\*\*\*\* 窗格的詳細資訊，請參閱 [查詢繫結詳細資料 &#40;資料分割來源對話方塊&#41; &#40;Analysis Services - 多維度資料&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="43694-116">For more information about the **Query Binding Detail** pane, see [Query Binding Detail &#40;Partition Source Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](query-binding-partition-source-dialog-analysis-services-multidimensional-data.md).</span></span>|  
|<span data-ttu-id="43694-117">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="43694-117">**Detail**</span></span>|<span data-ttu-id="43694-118">根據 [繫結類型]\*\*\*\* 選項的值而定，會顯示 [Table Binding Detail (資料表繫結詳細資料)]\*\*\*\* 對話方塊或 [Query Binding Detail (查詢繫結詳細資料)]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="43694-118">Displays either the **Table Binding Detail** dialog box or the **Query Binding Detail** dialog box, depending on the value of the **Binding type** option.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43694-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43694-119">See Also</span></span>  
 <span data-ttu-id="43694-120">[資料分割 &#40;Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="43694-120">[Partitions &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](partitions-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="43694-121">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="43694-121">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
