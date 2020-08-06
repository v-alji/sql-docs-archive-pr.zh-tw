---
title: 建立、修改或刪除屬性關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], member properties
- member properties [Analysis Services], creating
ms.assetid: 137b2f40-5dfb-4141-9110-70f961f259cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0e25140a75feda708850a2328498fb13df28a0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585656"
---
# <a name="create-modify-or-delete-an-attribute-relationship"></a><span data-ttu-id="79316-102">建立、修改或刪除屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="79316-102">Create, Modify, or Delete an Attribute Relationship</span></span>
  <span data-ttu-id="79316-103">您可以在 **中，使用 [維度設計師] 的** [屬性關聯性] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]索引標籤，建立、修改或刪除維度中各屬性之間的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="79316-103">You can create, modify, or delete an attribute relationship between attributes in a dimension by using the **Attribute Relationships** tab of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-an-attribute-relationship"></a><span data-ttu-id="79316-104">建立屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="79316-104">To create an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="79316-105">在 [維度設計師] 中，開啟包含您想要建立屬性關聯性之屬性的維度。</span><span class="sxs-lookup"><span data-stu-id="79316-105">In Dimension Designer, open the dimension that contains the attributes that you want to create an attribute relationship between.</span></span>  
  
2.  <span data-ttu-id="79316-106">在 [屬性關聯性]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下圖表中或 [屬性]\*\*\*\* 窗格中的屬性，然後選取 [新增屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="79316-106">On the **Attribute Relationships** tab, right-click an attribute in the diagram or in the **Attributes** pane, and then select **New Attribute Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="79316-107"> 若要顯示 **[屬性]** 窗格，按一下工具列上的 **[顯示清單檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="79316-107">To display the **Attributes** pane, click **Show List Views** on the toolbar.</span></span>  
  
3.  <span data-ttu-id="79316-108">在 **[建立屬性關聯性]** 對話方塊中，選取來源屬性和相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="79316-108">In the **Create Attribute Relationship** dialog box, select a source attribute and a related attribute.</span></span>  
  
4.  <span data-ttu-id="79316-109">在 **[關聯性類型]** 清單中，選取關聯性類型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="79316-109">In the **Relationship type** list, select a relationship type, and then click **OK**.</span></span>  
  
### <a name="to-modify-an-attribute-relationship"></a><span data-ttu-id="79316-110">修改屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="79316-110">To modify an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="79316-111">在 [維度設計師] 中，開啟包含您要修改之屬性關聯性的維度。</span><span class="sxs-lookup"><span data-stu-id="79316-111">In Dimension Designer, open the dimension that contains the attribute relationship that you want to modify.</span></span>  
  
2.  <span data-ttu-id="79316-112">按一下 **[屬性關聯性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="79316-112">Click the **Attribute Relationships** tab.</span></span>  
  
3.  <span data-ttu-id="79316-113">在圖表或 [屬性關聯性]\*\*\*\* 窗格中，以滑鼠右鍵按一下屬性關聯性，然後選取 [編輯屬性關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="79316-113">Right-click the attribute relationship in the diagram or in the **Attribute Relationships** pane, and select **Edit Attribute Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="79316-114"> 若要顯示 **[屬性關聯性]** 窗格，按一下工具列上的 **[顯示清單檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="79316-114">To display the **Attribute Relationships** pane, click **Show List Views** on the toolbar.</span></span>  
  
4.  <span data-ttu-id="79316-115">在 **[編輯屬性關聯性]** 對話方塊中，選取來源屬性和相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="79316-115">In the **Edit Attribute Relationship** dialog box, select a source attribute and a related attribute.</span></span>  
  
5.  <span data-ttu-id="79316-116">在 **[關聯性類型]** 清單中，選取關聯性類型，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="79316-116">In the **Relationship type** list, select a relationship type, and then click **OK**.</span></span>  
  
### <a name="to-delete-an-attribute-relationship"></a><span data-ttu-id="79316-117">刪除屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="79316-117">To delete an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="79316-118">在 [維度設計師] 中，開啟包含您要刪除之屬性關聯性的維度。</span><span class="sxs-lookup"><span data-stu-id="79316-118">In Dimension Designer, open the dimension that contains the attribute relationship that you want to delete.</span></span>  
  
2.  <span data-ttu-id="79316-119">在 [屬性關聯性]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下圖表中或 [屬性關聯性]\*\*\*\* 窗格中的屬性關聯性，然後選取 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="79316-119">On the **Attribute Relationships** tab, right-click the attribute relationship in the diagram or in the **Attribute Relationships** pane, and then select **Delete**.</span></span>  
  
3.  <span data-ttu-id="79316-120">在 **[刪除物件]** 對話方塊中，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="79316-120">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79316-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79316-121">See Also</span></span>  
 [<span data-ttu-id="79316-122">屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="79316-122">Attribute Relationships</span></span>](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
