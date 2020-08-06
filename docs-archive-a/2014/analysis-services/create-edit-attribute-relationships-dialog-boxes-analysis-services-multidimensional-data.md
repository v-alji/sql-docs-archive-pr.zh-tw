---
title: '[建立屬性關聯性] 和 [編輯屬性關聯性] 對話方塊 (屬性關聯性設計工具索引標籤、維度設計師)  (Analysis Services 多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.createrelationshipdialog.f1
ms.assetid: cb3bc7d8-9d4d-4da9-979d-bdad5e27e526
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7e720d31803057156c9b465f3e932bc734d03631
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592994"
---
# <a name="create-attribute-relationship-and-edit-attribute-relationship-dialog-boxes-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="f8bfb-102">建立屬性關聯性和編輯屬性關聯性對話方塊 (屬性關聯性設計師索引標籤，維度設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="f8bfb-102">Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes (Attribute Relationship Designer Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f8bfb-103">使用 [建立屬性關聯性]\*\*\*\* 對話方塊，即可定義新的屬性關聯性，而使用 [編輯屬性關聯性]\*\*\*\* 對話方塊，即可變更屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-103">Use the **Create Attribute Relationship** dialog box to define new attribute relationships and the **Edit Attribute Relationship** dialog box to change an attribute relationship.</span></span> <span data-ttu-id="f8bfb-104">如需詳細資訊，請參閱 [定義屬性關聯性](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-104">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="f8bfb-105">**檢視建立屬性關聯性對話方塊**</span><span class="sxs-lookup"><span data-stu-id="f8bfb-105">**To view the Create Attribute Relationship dialog box**</span></span>  
  
1.  <span data-ttu-id="f8bfb-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的方案總管中，按兩下維度即可開啟 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, double-click a dimension to open the Dimension Designer, and then click the **Attribute Relationship** tab.</span></span>  
  
2.  <span data-ttu-id="f8bfb-107">在工具列上，按一下 [新增屬性關聯性] 圖示。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-107">On the toolbar, click the New Attribute Relationship icon.</span></span>  
  
     <span data-ttu-id="f8bfb-108">-或-</span><span class="sxs-lookup"><span data-stu-id="f8bfb-108">-or-</span></span>  
  
     <span data-ttu-id="f8bfb-109">在屬性關聯性圖表或 [屬性]\*\*\*\* 清單中，以滑鼠右鍵按一下屬性，然後按一下 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-109">In the attribute relationship diagram or **Attributes** list, right-click an attribute, and then click **New Attribute Relationship**.</span></span>  
  
 <span data-ttu-id="f8bfb-110">**檢視編輯屬性關聯性對話方塊**</span><span class="sxs-lookup"><span data-stu-id="f8bfb-110">**To view the Edit Attribute Relationship dialog box**</span></span>  
  
1.  <span data-ttu-id="f8bfb-111">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的方案總管中，按兩下維度即可開啟 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, double-click a dimension to open the Dimension Designer, and then click the **Attribute Relationship** tab.</span></span>  
  
2.  <span data-ttu-id="f8bfb-112">在屬性關聯性圖表或 [屬性關聯性]\*\*\*\* 清單中，以滑鼠右鍵按一下屬性關聯性，然後按一下 [編輯屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-112">In the attribute relationship diagram or **Attribute Relationships** list, right-click an attribute relationship, and then click **Edit Attribute Relationship**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f8bfb-113">選項。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-113">Options</span></span>  
 <span data-ttu-id="f8bfb-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f8bfb-114">**Name**</span></span>  
 <span data-ttu-id="f8bfb-115">在 [來源屬性]\*\*\*\* 群組中，指定產生關聯性之來源屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-115">In the **Source Attribute** group, specifies the name of the attribute from which the relationship originates.</span></span>  
  
 <span data-ttu-id="f8bfb-116">在 [相關屬性]\*\*\*\* 群組中，指定關聯性導向之目標屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-116">In the **Related Attribute** group, specifies the name of the attribute to which the relationship is directed.</span></span>  
  
 <span data-ttu-id="f8bfb-117">**成員計數**</span><span class="sxs-lookup"><span data-stu-id="f8bfb-117">**Member Count**</span></span>  
 <span data-ttu-id="f8bfb-118">指定指定之屬性成員的估計數目。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-118">Specifies the estimated number of members of the specified attribute.</span></span>  
  
 <span data-ttu-id="f8bfb-119">**索引鍵資料行**</span><span class="sxs-lookup"><span data-stu-id="f8bfb-119">**Key Columns**</span></span>  
 <span data-ttu-id="f8bfb-120">指定針對屬性定義的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-120">Specifies the key columns that are defined for the attribute.</span></span>  
  
 <span data-ttu-id="f8bfb-121">**關聯性類型**</span><span class="sxs-lookup"><span data-stu-id="f8bfb-121">**Relationship type**</span></span>  
 <span data-ttu-id="f8bfb-122">指定要建立的關聯性類型：[彈性 (可能隨時間而改變)]\*\*\*\* 或 [固定 (不會隨時間而改變)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f8bfb-122">Specifies the type of relationship to create, either **Flexible (may change over time)** or **Rigid (will not change over time)**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bfb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8bfb-123">See Also</span></span>  
 [<span data-ttu-id="f8bfb-124">屬性關聯性 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="f8bfb-124">Attribute Relationships &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
