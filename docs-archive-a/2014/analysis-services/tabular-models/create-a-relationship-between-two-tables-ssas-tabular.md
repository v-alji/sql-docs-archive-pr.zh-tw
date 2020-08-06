---
title: 在 (SSAS 表格式) 的兩個數據表之間建立關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.managereldb.f1
- sql12.asvs.bidtoolset.createrelatdb.f1
ms.assetid: 052d77b7-7922-408a-a200-786016ee4d15
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33481b8d50be9ca632bcade932d51df86c1910a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594219"
---
# <a name="create-a-relationship-between-two-tables-ssas-tabular"></a><span data-ttu-id="e7620-102">建立兩個資料表之間的關聯性 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="e7620-102">Create a Relationship Between Two Tables (SSAS Tabular)</span></span>
  <span data-ttu-id="e7620-103">如果您資料來源中的資料表並沒有關聯性存在，或如果您要新增資料表，則可以使用模型設計師中的工具來建立新的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e7620-103">If the tables in your data source do not have existing relationships, or if you add new tables, you can use the tools in the model designer to create new relationships.</span></span> <span data-ttu-id="e7620-104">如需如何在表格式模型中使用關聯性的資訊，請參閱 [關聯性 &#40;SSAS 表格式&#41;](relationships-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="e7620-104">For information about how relationships are used in tabular models, see [Relationships &#40;SSAS Tabular&#41;](relationships-ssas-tabular.md).</span></span>  
  
## <a name="create-a-relationship-between-two-tables"></a><span data-ttu-id="e7620-105">建立兩個資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="e7620-105">Create a relationship between two tables</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a><span data-ttu-id="e7620-106">在圖表檢視中建立兩個資料表之間的關聯性 (按住並拖曳)</span><span class="sxs-lookup"><span data-stu-id="e7620-106">To create a relationship between two tables in Diagram View (Click and drag)</span></span>  
  
1.  <span data-ttu-id="e7620-107">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[模型檢視]**，再按一下 **[圖表檢視]**。</span><span class="sxs-lookup"><span data-stu-id="e7620-107">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="e7620-108">按住資料表中的資料行，再將游標拖曳至相關查閱資料表中的相關查閱資料行，然後放開。</span><span class="sxs-lookup"><span data-stu-id="e7620-108">Click (and hold) on a column within a table, then drag the cursor to a related lookup column in a related lookup table, and then release.</span></span> <span data-ttu-id="e7620-109">即可以正確的順序自動建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="e7620-109">The relationship will be created in the correct order automatically.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a><span data-ttu-id="e7620-110">在圖表檢視中建立兩個資料表之間的關聯性 (按一下滑鼠右鍵)</span><span class="sxs-lookup"><span data-stu-id="e7620-110">To create a relationship between two tables in Diagram View (Right-click)</span></span>  
  
1.  <span data-ttu-id="e7620-111">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[模型檢視]**，再按一下 **[圖表檢視]**。</span><span class="sxs-lookup"><span data-stu-id="e7620-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, then click **Model View**, and then click **Diagram View**.</span></span>  
  
2.  <span data-ttu-id="e7620-112">以滑鼠右鍵按一下資料表標題或資料行，然後按一下 [建立關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e7620-112">Right-click a table heading or column, and then click **Create Relationship**.</span></span>  
  
3.  <span data-ttu-id="e7620-113">在 **[建立關聯性]** 對話方塊的 **[資料表]** 中，按一下向下鍵，然後從下拉式清單中選取資料表。</span><span class="sxs-lookup"><span data-stu-id="e7620-113">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="e7620-114">在「一對多」關聯性中，這個資料表應該是「多」邊。</span><span class="sxs-lookup"><span data-stu-id="e7620-114">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
4.  <span data-ttu-id="e7620-115">針對 **[資料行]**，選取包含與 **[相關查閱資料行]** 相關之資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="e7620-115">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span> <span data-ttu-id="e7620-116">若您以滑鼠右鍵按一下資料行來建立關聯性，則會自動選取資料行。</span><span class="sxs-lookup"><span data-stu-id="e7620-116">The column is automatically selected if you right-clicked on a column to create the relationship.</span></span>  
  
5.  <span data-ttu-id="e7620-117">針對 **[相關查閱資料表]** 選取資料表，其中至少有一個資料行與剛才針對 **[資料表]** 選取的資料表相關聯。</span><span class="sxs-lookup"><span data-stu-id="e7620-117">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="e7620-118">在「一對多」關聯性中，此資料表應該是「一」邊，也就是說，所選資料行中的值不包含重複的項目。</span><span class="sxs-lookup"><span data-stu-id="e7620-118">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="e7620-119">如果您嘗試以錯誤的順序 (一對多而非多對一) 建立關聯性，圖示將會出現在 [相關查閱資料行]\*\*\*\* 欄位的旁邊。</span><span class="sxs-lookup"><span data-stu-id="e7620-119">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="e7620-120">反轉順序來建立有效的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e7620-120">Reverse the order to create a valid relationship.</span></span>  
  
6.  <span data-ttu-id="e7620-121">針對 **[相關查閱資料行]** 選取資料行，其唯一值與針對 **[資料行]** 選取之資料行中的值相符。</span><span class="sxs-lookup"><span data-stu-id="e7620-121">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
7.  <span data-ttu-id="e7620-122">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="e7620-122">Click **Create**.</span></span>  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a><span data-ttu-id="e7620-123">在資料檢視中建立兩個資料表之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="e7620-123">To create a relationship between two tables in Data View</span></span>  
  
1.  <span data-ttu-id="e7620-124">在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[資料表]** 功能表，然後按一下 **[建立關聯性]**。</span><span class="sxs-lookup"><span data-stu-id="e7620-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Create Relationships**.</span></span>  
  
2.  <span data-ttu-id="e7620-125">在 **[建立關聯性]** 對話方塊的 **[資料表]** 中，按一下向下鍵，然後從下拉式清單中選取資料表。</span><span class="sxs-lookup"><span data-stu-id="e7620-125">In the **Create Relationship** dialog box, click the down arrow for **Table**, and select a table from the dropdown list.</span></span>  
  
     <span data-ttu-id="e7620-126">在「一對多」關聯性中，這個資料表應該是「多」邊。</span><span class="sxs-lookup"><span data-stu-id="e7620-126">In a "one-to-many" relationship, this table should be on the "many" side.</span></span>  
  
3.  <span data-ttu-id="e7620-127">針對 **[資料行]**，選取包含與 **[相關查閱資料行]** 相關之資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="e7620-127">For **Column**, select the column that contains the data that is related to **Related Lookup Column**.</span></span>  
  
4.  <span data-ttu-id="e7620-128">針對 **[相關查閱資料表]** 選取資料表，其中至少有一個資料行與剛才針對 **[資料表]** 選取的資料表相關聯。</span><span class="sxs-lookup"><span data-stu-id="e7620-128">For **Related Lookup Table**, select a table that has at least one column of data that is related to the table you just selected for **Table**.</span></span>  
  
     <span data-ttu-id="e7620-129">在「一對多」關聯性中，此資料表應該是「一」邊，也就是說，所選資料行中的值不包含重複的項目。</span><span class="sxs-lookup"><span data-stu-id="e7620-129">In a "one-to-many" relationship, this table should be on the "one" side, meaning that the values in the selected column do not contain duplicates.</span></span> <span data-ttu-id="e7620-130">如果您嘗試以錯誤的順序 (一對多而非多對一) 建立關聯性，圖示將會出現在 [相關查閱資料行]\*\*\*\* 欄位的旁邊。</span><span class="sxs-lookup"><span data-stu-id="e7620-130">If you attempt to create the relationship in the wrong order (one-to-many instead of many-to-one), an icon will appear next to the **Related Lookup Column** field.</span></span> <span data-ttu-id="e7620-131">反轉順序來建立有效的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e7620-131">Reverse the order to create a valid relationship.</span></span>  
  
5.  <span data-ttu-id="e7620-132">針對 **[相關查閱資料行]** 選取資料行，其唯一值與針對 **[資料行]** 選取之資料行中的值相符。</span><span class="sxs-lookup"><span data-stu-id="e7620-132">For **Related Lookup Column**, select a column that has unique values that match the values in the column you selected for **Column**.</span></span>  
  
6.  <span data-ttu-id="e7620-133">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="e7620-133">Click **Create**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7620-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7620-134">See Also</span></span>  
 <span data-ttu-id="e7620-135">[&#40;SSAS 表格式&#41;中刪除關聯性](delete-relationships-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="e7620-135">[Delete Relationships &#40;SSAS Tabular&#41;](delete-relationships-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="e7620-136">關聯性 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="e7620-136">Relationships &#40;SSAS Tabular&#41;</span></span>](relationships-ssas-tabular.md)  
  
  
