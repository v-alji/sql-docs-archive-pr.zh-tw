---
title: " (SSAS 表格式) 中刪除關聯性 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c63324918eb6919ce0abd65b5ee0765f9d7243b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687246"
---
# <a name="delete-relationships-ssas-tabular"></a><span data-ttu-id="72d28-102">刪除關聯性 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="72d28-102">Delete Relationships (SSAS Tabular)</span></span>
  <span data-ttu-id="72d28-103">您可以刪除現有的關聯性，方法是使用 [圖表檢視] 中的模型設計師或使用 [管理關聯性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="72d28-103">You can delete existing relationships by using the model designer in Diagram View or by using the Manage Relationships dialog box.</span></span> <span data-ttu-id="72d28-104">如需如何在表格式模型中使用關聯性的資訊，請參閱 [關聯性 &#40;SSAS 表格式&#41;](relationships-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="72d28-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="considerations-for-deleting-relationships"></a><span data-ttu-id="72d28-105">刪除關聯性的考量</span><span class="sxs-lookup"><span data-stu-id="72d28-105">Considerations for Deleting Relationships</span></span>  
 <span data-ttu-id="72d28-106">當您決定是否要刪除關聯性時，請牢記以下問題：</span><span class="sxs-lookup"><span data-stu-id="72d28-106">Keep the following issues in mind when deciding whether to delete a relationship:</span></span>  
  
-   <span data-ttu-id="72d28-107">您無法復原關聯性的刪除。</span><span class="sxs-lookup"><span data-stu-id="72d28-107">There is no way to undo the deletion of a relationship.</span></span> <span data-ttu-id="72d28-108">您可以重新建立關聯性，但是這個動作需要全面重新計算模型中的公式。</span><span class="sxs-lookup"><span data-stu-id="72d28-108">You can re-create the relationship, but this action requires a complete recalculation of formulas in the model.</span></span> <span data-ttu-id="72d28-109">因此，在刪除公式中使用的關聯性之前，請務必先檢查。</span><span class="sxs-lookup"><span data-stu-id="72d28-109">Therefore, always check first before deleting a relationship that is used in formulas.</span></span>  
  
-   <span data-ttu-id="72d28-110">刪除兩個資料表之間的關聯性會造成參考這些資料表的公式發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="72d28-110">Deleting a relationship between two tables can cause errors in formulas that reference these tables.</span></span>  
  
-   <span data-ttu-id="72d28-111">Data Analysis Expression (DAX) RELATED 函數會使用資料表之間的關聯性來查閱另一個資料表中相關的值。</span><span class="sxs-lookup"><span data-stu-id="72d28-111">The Data Analysis Expression (DAX) RELATED function uses the relationships between tables to look up related values in another table.</span></span> <span data-ttu-id="72d28-112">它會在關聯性遭刪除之後傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="72d28-112">It will return different results after the relationship is deleted.</span></span> <span data-ttu-id="72d28-113">如需詳細資訊，請參閱 RELATED 函數 (DAX)。</span><span class="sxs-lookup"><span data-stu-id="72d28-113">For more information, see the RELATED Function (DAX).</span></span>  
  
-   <span data-ttu-id="72d28-114">除了變更樞紐分析表和公式結果以外，建立及刪除關聯性都會使活頁簿重新計算，這可能要花費一些時間。</span><span class="sxs-lookup"><span data-stu-id="72d28-114">In addition to changing PivotTable and formula results, both the creation and deletion of relationships will cause the workbook to be recalculated, which can take some time.</span></span>  
  
## <a name="delete-relationships"></a><span data-ttu-id="72d28-115">刪除關聯性</span><span class="sxs-lookup"><span data-stu-id="72d28-115">Delete Relationships</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a><span data-ttu-id="72d28-116">若要使用圖表檢視刪除關聯性</span><span class="sxs-lookup"><span data-stu-id="72d28-116">To delete a relationship by using Diagram View</span></span>  
  
1.  <span data-ttu-id="72d28-117">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，按一下 **[模型]** 功能表，然後指向 **[模型檢視]**，再按一下 **[圖表檢視]**。</span><span class="sxs-lookup"><span data-stu-id="72d28-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="72d28-118">以滑鼠右鍵按一下兩個資料表之間的關聯性線條，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="72d28-118">Right-click a relationship line between two tables, and then click **Delete**.</span></span>  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a><span data-ttu-id="72d28-119">若要使用 [管理關聯性] 對話方塊刪除關聯性</span><span class="sxs-lookup"><span data-stu-id="72d28-119">To delete a relationship by using the Manage Relationships dialog box</span></span>  
  
1.  <span data-ttu-id="72d28-120">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中按一下 **[資料表]** 功能表，然後按一下 **[管理關聯性]**。</span><span class="sxs-lookup"><span data-stu-id="72d28-120">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Manage Relationships**.</span></span>  
  
2.  <span data-ttu-id="72d28-121">在 **[管理關聯性]** 對話方塊中，選取清單中的一個或多個關聯性。</span><span class="sxs-lookup"><span data-stu-id="72d28-121">In the **Manage Relationships** dialog box, select one or more relationships from the list.</span></span>  
  
     <span data-ttu-id="72d28-122">若要選取多個關聯性，請按住 CTRL 同時按一下每個關聯性。</span><span class="sxs-lookup"><span data-stu-id="72d28-122">To select multiple relationships, hold down CTRL while you click each relationship.</span></span>  
  
3.  <span data-ttu-id="72d28-123">按一下 **[刪除關聯性]**。</span><span class="sxs-lookup"><span data-stu-id="72d28-123">Click **Delete Relationship**.</span></span>  
  
4.  <span data-ttu-id="72d28-124">按一下 **[管理關聯性]** 對話方塊中的 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="72d28-124">In the **Manage Relationships** dialog box, click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d28-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72d28-125">See Also</span></span>  
 <span data-ttu-id="72d28-126">[SSAS 表格式&#41;的關聯性 &#40;](relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="72d28-126">[Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="72d28-127">建立兩個資料表之間的關聯性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="72d28-127">Create a Relationship Between Two Tables &#40;SSAS Tabular&#41;</span></span>](create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
