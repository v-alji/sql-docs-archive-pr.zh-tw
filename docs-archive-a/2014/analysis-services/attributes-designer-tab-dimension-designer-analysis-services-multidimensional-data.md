---
title: 屬性 (屬性關聯性設計工具索引標籤、維度設計工具)  (Analysis Services 多維資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.attributes.f1
ms.assetid: 850a68aa-1d70-4f0f-ba39-aeca834596c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: baced7debe540827d603d39f9978a1e18bc17762
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593162"
---
# <a name="attributes-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="3a3c6-102">屬性 (屬性關聯性設計師索引標籤，維度設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="3a3c6-102">Attributes (Attribute Relationship Designer Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="3a3c6-103">使用 **[屬性]** 清單，即可在屬性關聯性圖表中找到特定屬性，或定義新的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-103">Use the **Attributes** list to locate a specific attribute in the attribute relationship diagram or to define a new attribute relationship.</span></span> <span data-ttu-id="3a3c6-104">這個窗格會緊鄰在包含屬性關聯性圖表的窗格底下。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-104">This pane appears immediately under the pane that contains the attribute relationship diagram.</span></span>  
  
 <span data-ttu-id="3a3c6-105">**檢視屬性窗格**</span><span class="sxs-lookup"><span data-stu-id="3a3c6-105">**To view the Attributes pane**</span></span>  
  
1.  <span data-ttu-id="3a3c6-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的方案總管中，按兩下維度即可開啟 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, double-click a dimension to open the Dimension Designer, and then click the **Attribute Relationship** tab.</span></span>  
  
2.  <span data-ttu-id="3a3c6-107">在工具列上，按一下 **[顯示清單檢視]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-107">On the toolbar, click the **Show List Views** icon.</span></span>  
  
## <a name="using-the-attributes-list"></a><span data-ttu-id="3a3c6-108">使用屬性清單</span><span class="sxs-lookup"><span data-stu-id="3a3c6-108">Using the Attributes List</span></span>  
 <span data-ttu-id="3a3c6-109">**[屬性]** 清單會顯示維度中的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-109">The **Attributes** list displays all of the attributes in the dimension.</span></span>  
  
 <span data-ttu-id="3a3c6-110">若要在屬性關聯性圖表中找到特定屬性，請按兩下清單中的屬性。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-110">To locate a specific attribute in the attribute relationship diagram, double-click the attribute in the list.</span></span> <span data-ttu-id="3a3c6-111">該屬性 (Attribute) 將在屬性關聯性圖表中反白顯示，而且其屬性 (Property) 會顯示在 [屬性] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-111">The attribute will be highlighted in the attribute relationship diagram and its properties will appear in the Properties window.</span></span> <span data-ttu-id="3a3c6-112">如果該屬性 (Attribute) 沒有顯示於屬性關聯性圖表中，就只有該屬性的屬性 (Property) 會顯示在 **[屬性]** 視窗中。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-112">If the attribute is not shown in the attribute relationship diagram, only the attribute's properties will appear in the **Properties** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3a3c6-113">您可以在清單中選取多個屬性，然後進行變更。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-113">You can select multiple attributes in the list and make changes.</span></span>  
  
 <span data-ttu-id="3a3c6-114">若要定義新的關聯性或重新命名屬性，請以滑鼠右鍵按一下屬性，然後按一下快速鍵功能表中的對應命令。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-114">To define a new relationship or rename the attribute, right-click the attribute and click the corresponding command in the shortcut menu.</span></span>  
  
### <a name="shortcut-menu-options"></a><span data-ttu-id="3a3c6-115">快速鍵功能表選項</span><span class="sxs-lookup"><span data-stu-id="3a3c6-115">Shortcut Menu Options</span></span>  
 <span data-ttu-id="3a3c6-116">**新增屬性關聯性**</span><span class="sxs-lookup"><span data-stu-id="3a3c6-116">**New Attribute Relationship**</span></span>  
 <span data-ttu-id="3a3c6-117">開啟 [建立屬性關聯性]\*\*\*\* 對話方塊，而且您可以在其中定義新的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-117">Opens the **Create Attribute Relationship** dialog box in which you can define a new attribute relationship.</span></span>  
  
 <span data-ttu-id="3a3c6-118">如需詳細資訊，請參閱[建立屬性關聯性和編輯屬性關聯性對話方塊 &#40;屬性關聯性設計師索引標籤，維度設計師&#41; &#40;Analysis Services - 多維度資料&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) 和[定義屬性關聯性](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-118">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="3a3c6-119">**重新命名**</span><span class="sxs-lookup"><span data-stu-id="3a3c6-119">**Rename**</span></span>  
 <span data-ttu-id="3a3c6-120">在清單中反白顯示屬性的名稱，然後讓您修改此文字。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-120">Highlights the attribute's name in the list and enables you to modify this text.</span></span>  
  
 <span data-ttu-id="3a3c6-121">**屬性**</span><span class="sxs-lookup"><span data-stu-id="3a3c6-121">**Properties**</span></span>  
 <span data-ttu-id="3a3c6-122">在 [屬性]\*\*\*\* 視窗中顯示屬性 (Attribute) 的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="3a3c6-122">Displays the attribute's properties in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a3c6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a3c6-123">See Also</span></span>  
 <span data-ttu-id="3a3c6-124">[屬性關聯性 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3a3c6-124">[Attribute Relationships &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3a3c6-125">[工具列 &#40;屬性關聯性設計師索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3a3c6-125">[Toolbar &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="3a3c6-126">[屬性關聯性圖表 &#40;屬性關聯性設計工具索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](attribute-relationship-diagram-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="3a3c6-126">[Attribute Relationship Diagram &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationship-diagram-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="3a3c6-127">屬性關聯性 &#40;屬性關聯性設計工具索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="3a3c6-127">Attribute Relationships &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](attribute-relationships-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
