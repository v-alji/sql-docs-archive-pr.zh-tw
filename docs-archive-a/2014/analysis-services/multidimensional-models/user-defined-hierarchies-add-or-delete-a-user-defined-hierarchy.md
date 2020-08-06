---
title: 新增或刪除使用者定義階層 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], adding
- removing hierarchies
- adding hierarchies
- deleting hierarchies
- hierarchies [Analysis Services], removing
ms.assetid: 953818b4-9543-4c01-bb20-1d45ec6dfb91
author: minewiskan
ms.author: owend
ms.openlocfilehash: d20404a1d93d57221eb830366392eb90600f26c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597394"
---
# <a name="add-or-delete-a-user-defined-hierarchy"></a><span data-ttu-id="81caa-102">加入或刪除使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="81caa-102">Add or Delete a User-Defined Hierarchy</span></span>
  <span data-ttu-id="81caa-103">您會在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，維度設計師的 [維度結構]\*\*\*\* 索引標籤上，從維度中加入或移除使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="81caa-103">You add a user-defined hierarchy to or remove a user-defined hierarchy from a dimension on the **Dimension Structure** tab in Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="81caa-104">當您加入使用者自訂階層時，要等到在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體中具現化使用者自訂階層，而且處理維度之後，才可以提供此階層給使用者使用。</span><span class="sxs-lookup"><span data-stu-id="81caa-104">When you add a user-defined hierarchy, it is not available to users until it is instantiated in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the dimension is processed.</span></span> <span data-ttu-id="81caa-105">如需詳細資訊，請參閱多[維度模型資料庫 &#40;SSAS&#41;](multidimensional-model-databases-ssas.md)和多[維度模型物件處理](processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="81caa-105">For more information, see [Multidimensional Model Databases &#40;SSAS&#41;](multidimensional-model-databases-ssas.md) and [Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
### <a name="to-add-a-user-defined-hierarchy-to-a-dimension"></a><span data-ttu-id="81caa-106">將使用者自訂階層加入維度</span><span class="sxs-lookup"><span data-stu-id="81caa-106">To add a user-defined hierarchy to a dimension</span></span>  
  
1.  <span data-ttu-id="81caa-107">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟適當的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案，然後開啟您想要使用的維度。</span><span class="sxs-lookup"><span data-stu-id="81caa-107">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the appropriate [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, and then open the dimension with which you want to work.</span></span>  
  
     <span data-ttu-id="81caa-108">此維度會在 [維度設計師] 的 [維度結構]\*\*\*\* 索引標籤上開啟。</span><span class="sxs-lookup"><span data-stu-id="81caa-108">The dimension opens in Dimension Designer on the **Dimension Structure** tab.</span></span>  
  
2.  <span data-ttu-id="81caa-109">從 [屬性]\*\*\*\* 窗格中，將您要在使用者自訂階層中使用的屬性拖曳到 [階層]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="81caa-109">From the **Attributes** pane, drag an attribute that you want to use in the user-defined hierarchy to the **Hierarchies** pane.</span></span>  
  
3.  <span data-ttu-id="81caa-110">拖曳其他屬性，以便在使用者自訂階層中形成層級。</span><span class="sxs-lookup"><span data-stu-id="81caa-110">Drag additional attributes to form levels in the user-defined hierarchy.</span></span>  
  
     <span data-ttu-id="81caa-111">屬性列在階層中的順序很重要。</span><span class="sxs-lookup"><span data-stu-id="81caa-111">The order in which attributes are listed in the hierarchy is important.</span></span> <span data-ttu-id="81caa-112">例如，在時間階層中，年應該出現在高於天的階層清單中。</span><span class="sxs-lookup"><span data-stu-id="81caa-112">For example, in a time hierarchy, years should appear higher in the hierarchy list than days.</span></span>  
  
4.  <span data-ttu-id="81caa-113">也可以選擇，將使用者自訂階層中的層級拖曳到正確位置上，以重新排列這些階層。</span><span class="sxs-lookup"><span data-stu-id="81caa-113">Optionally, rearrange the levels in the user-defined hierarchy by dragging them to the correct positions.</span></span>  
  
5.  <span data-ttu-id="81caa-114">也可以選擇，修改使用者自訂階層或其層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="81caa-114">Optionally, modify properties of the user-defined hierarchy or its levels.</span></span>  
  
     <span data-ttu-id="81caa-115">例如，您可能會想要指定使用者自訂階層的名稱，也可能重新命名一個或多個層級，然後定義「全部」層級的自訂名稱。</span><span class="sxs-lookup"><span data-stu-id="81caa-115">For example, you might want to specify a name for the user-defined hierarchy, rename one or more of its levels, and define a custom name for the All level.</span></span> <span data-ttu-id="81caa-116">如需詳細資訊，請參閱[使用者階層屬性](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)和[層級屬性 &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="81caa-116">For more information, see [User Hierarchy Properties](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md), and [Level Properties &#91;Paved Over&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="81caa-117">依預設，使用者自訂階層就是可以讓使用者向下鑽研資訊的路徑。</span><span class="sxs-lookup"><span data-stu-id="81caa-117">By default, a user-defined hierarchy is just a path that enables users to drill down for information.</span></span> <span data-ttu-id="81caa-118">但是，如果層級之間有關聯性存在，則可以設定層級之間的屬性關聯性來提升查詢效能。</span><span class="sxs-lookup"><span data-stu-id="81caa-118">However, if relationships exist between levels, you can increase query performance by configuring attribute relationships between levels.</span></span> <span data-ttu-id="81caa-119">如需詳細資訊，請參閱 [屬性關聯性](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) 和 [定義屬性關聯性](attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="81caa-119">For more information, see [Attribute Relationships](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md) and [Define Attribute Relationships](attribute-relationships-define.md).</span></span>  
  
### <a name="to-remove-a-user-defined-hierarchy-from-a-dimension"></a><span data-ttu-id="81caa-120">從維度中移除使用者自訂階層</span><span class="sxs-lookup"><span data-stu-id="81caa-120">To remove a user-defined hierarchy from a dimension</span></span>  
  
-   <span data-ttu-id="81caa-121">在 [維度結構]\*\*\*\* 索引標籤上，按一下要在 [階層]\*\*\*\* 窗格中移除的使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="81caa-121">On the **Dimension Structure** tab, click the user-defined hierarchy that you want to remove in the **Hierarchies** pane.</span></span> <span data-ttu-id="81caa-122">在工具列上，按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81caa-122">On the toolbar, click **Delete**.</span></span>  
  
     - <span data-ttu-id="81caa-123">或 -</span><span class="sxs-lookup"><span data-stu-id="81caa-123">or -</span></span>  
  
-   <span data-ttu-id="81caa-124">在 [階層]\*\*\*\* 窗格中以滑鼠右鍵按一下要移除的使用者定義階層，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="81caa-124">Right-click the user-defined hierarchy that you want to remove in the **Hierarchies** pane and then click **Delete**.</span></span>  
  
     - <span data-ttu-id="81caa-125">或 -</span><span class="sxs-lookup"><span data-stu-id="81caa-125">or -</span></span>  
  
-   <span data-ttu-id="81caa-126">將使用者自訂階層拖曳出設計介面。</span><span class="sxs-lookup"><span data-stu-id="81caa-126">Drag the user-defined hierarchy off of the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81caa-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81caa-127">See Also</span></span>  
 <span data-ttu-id="81caa-128">[使用者階層](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span><span class="sxs-lookup"><span data-stu-id="81caa-128">[User Hierarchies](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md) </span></span>  
 [<span data-ttu-id="81caa-129">建立使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="81caa-129">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
  
  
