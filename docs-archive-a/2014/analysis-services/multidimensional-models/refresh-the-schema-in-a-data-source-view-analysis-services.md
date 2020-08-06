---
title: 重新整理資料來源視圖中的架構 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services], schema updates
- refreshing data source views
- data source views [Analysis Services], refreshing
ms.assetid: 634b0504-1437-43e7-8ac7-3248ac7989a3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 808f6ea431592aaecadf6f20a1ae16850cdb20e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592946"
---
# <a name="refresh-the-schema-in-a-data-source-view-analysis-services"></a><span data-ttu-id="0eabd-102">在資料來源檢視中重新整理結構描述 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="0eabd-102">Refresh the Schema in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="0eabd-103">當您在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 專案或資料庫中定義資料來源檢視 (DSV) 之後，基礎資料來源中的結構描述可能會變更。</span><span class="sxs-lookup"><span data-stu-id="0eabd-103">After defining a data source view (DSV) in an [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] project or database, the schema in an underlying data source may change.</span></span> <span data-ttu-id="0eabd-104">但在開發專案中不會自動偵測或更新這些變更。</span><span class="sxs-lookup"><span data-stu-id="0eabd-104">These changes are not automatically detected or updated in a development project.</span></span> <span data-ttu-id="0eabd-105">此外，如果您將專案部署至伺服器，當 Analysis Services 無法再連接至外部資料來源時，您現在會發生處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="0eabd-105">Moreover, if you deployed the project to a server, you will now encounter processing errors if Analysis Services can no longer connect to the external data source.</span></span>

 <span data-ttu-id="0eabd-106">若要更新 DSV 以符合外部資料來源，您可以在 Business Intelligence Development Studio (BIDS) 中重新整理 DSV。</span><span class="sxs-lookup"><span data-stu-id="0eabd-106">To update the DSV so that it matches the external data source, you can refresh the DSV in Business Intelligence Development Studio (BIDS).</span></span> <span data-ttu-id="0eabd-107">重新整理 DSV 會偵測做為 DSV 基礎之外部資料來源的變更，並建立變更清單，以列舉外部資料來源中的加入或刪除。</span><span class="sxs-lookup"><span data-stu-id="0eabd-107">Refreshing the DSV detects changes to the external data sources upon which the DSV is based, and builds a change list that enumerates the additions or deletions in the external data source.</span></span> <span data-ttu-id="0eabd-108">然後，您可以將一組變更套用至 DSV，以將 DSV 重新調整為符合基礎資料來源。</span><span class="sxs-lookup"><span data-stu-id="0eabd-108">You can then apply the set of changes to the DSV that will realign it to the underlying data source.</span></span> <span data-ttu-id="0eabd-109">請注意，您通常需要額外的工作，以進一步更新專案中使用 DSV 的 Cube 和維度。</span><span class="sxs-lookup"><span data-stu-id="0eabd-109">Note that additional work is often required to further update the cubes and dimensions in the project that use the DSV.</span></span>

 <span data-ttu-id="0eabd-110">這個主題包括下列各節：</span><span class="sxs-lookup"><span data-stu-id="0eabd-110">This topic includes the following sections:</span></span>

 [<span data-ttu-id="0eabd-111">重新整理所支援的變更</span><span class="sxs-lookup"><span data-stu-id="0eabd-111">Changes Supported in Refresh</span></span>](#bkmk_changlist)

 [<span data-ttu-id="0eabd-112">在 SQL Server Data Tools 中重新整理 DSV</span><span class="sxs-lookup"><span data-stu-id="0eabd-112">Refresh a DSV in SQL Server Data Tools</span></span>](#bkmk_DSVrefresh)

##  <a name="changes-supported-in-refresh"></a><a name="bkmk_changlist"></a><span data-ttu-id="0eabd-113">重新整理中支援的變更</span><span class="sxs-lookup"><span data-stu-id="0eabd-113">Changes Supported in Refresh</span></span>
 <span data-ttu-id="0eabd-114">DSV 重新整理可以包含下列任何一項動作：</span><span class="sxs-lookup"><span data-stu-id="0eabd-114">DSV Refresh can include any of the following the actions:</span></span>

-   <span data-ttu-id="0eabd-115">刪除資料表、資料行及關聯性</span><span class="sxs-lookup"><span data-stu-id="0eabd-115">Deletion of tables, columns, and relationships</span></span>

-   <span data-ttu-id="0eabd-116">加入資料行和關聯性，並套用至已經包含在 DSV 中的資料表。</span><span class="sxs-lookup"><span data-stu-id="0eabd-116">Addition of columns and relationships, as applied to tables that are already included in the DSV</span></span>

-   <span data-ttu-id="0eabd-117">加入新的唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="0eabd-117">Addition of new unique constraints.</span></span> <span data-ttu-id="0eabd-118">如果 DSV 中有資料表的邏輯主索引鍵存在，而且資料來源中的資料表已加入實體索引鍵，則會移除此邏輯索引鍵，並由此實體索引鍵來加以取代。</span><span class="sxs-lookup"><span data-stu-id="0eabd-118">If a logical primary key exists for a table in the DSV and a physical key is added to the table in the data source, the logical key is removed and replaced by the physical key.</span></span>

 <span data-ttu-id="0eabd-119">重新整理永遠不會將新資料表加入至 DSV。</span><span class="sxs-lookup"><span data-stu-id="0eabd-119">Refresh never adds new tables to a DSV.</span></span> <span data-ttu-id="0eabd-120">如果您想加入新資料表，則必須手動加入。</span><span class="sxs-lookup"><span data-stu-id="0eabd-120">If you want to add a new table, you must add it manually.</span></span> <span data-ttu-id="0eabd-121">如需詳細資訊，請參閱 [在資料來源檢視中加入或移除資料表或檢視 &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)的 [方案總管] 中執行 [資料來源檢視精靈]。</span><span class="sxs-lookup"><span data-stu-id="0eabd-121">For more information, see [Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md).</span></span>

##  <a name="refresh-a-dsv-in-sql-server-data-tools"></a><a name="bkmk_DSVrefresh"></a><span data-ttu-id="0eabd-122">重新整理 SQL Server Data Tools 中的 DSV</span><span class="sxs-lookup"><span data-stu-id="0eabd-122">Refresh a DSV in SQL Server Data Tools</span></span>
 <span data-ttu-id="0eabd-123">若要重新整理 DSV，請從 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的方案總管中，按兩下 DSV，然後按一下 [重新整理資料來源檢視] 按鈕，或從 [資料來源檢視] 功能表中選擇 [重新整理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0eabd-123">To refresh a DSV, double-click the DSV from Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and then click the Refresh Data Source View button or choose **Refresh** from the Data Source View menu.</span></span>

 <span data-ttu-id="0eabd-124">在重新整理期間， [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 會查詢所有基礎關聯式資料來源，以判斷 DSV 中所包含的資料表/檢視表是否已有變更。</span><span class="sxs-lookup"><span data-stu-id="0eabd-124">During refresh, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] queries all underlying relational data sources to determine whether there have been changes in tables/views which are included in the DSV.</span></span> <span data-ttu-id="0eabd-125">如果可以對所有基礎資料來源建立連接，而且已經有變更，您將會在 [重新整理資料來源檢視]\*\*\*\* 對話方塊中看到這些變更。</span><span class="sxs-lookup"><span data-stu-id="0eabd-125">If connections can be established to all underlying data sources and there have been any changes, you will see them in the **Refresh Data Source View** dialog box.</span></span>

 <span data-ttu-id="0eabd-126">![重新整理資料來源視圖對話方塊](../media/ssas-olapdsv-refresh.gif "重新整理資料來源檢視對話方塊")</span><span class="sxs-lookup"><span data-stu-id="0eabd-126">![Refresh Data Source View dialog box](../media/ssas-olapdsv-refresh.gif "Refresh Data Source View dialog box")</span></span>

 <span data-ttu-id="0eabd-127">此對話方塊列出要在 DSV 中刪除或加入的資料表、資料行、條件約束和關聯性。</span><span class="sxs-lookup"><span data-stu-id="0eabd-127">The dialog box lists tables, columns, constraints, and relationships that will be deleted or added in the DSV.</span></span> <span data-ttu-id="0eabd-128">此報表亦列出無法順利準備的具名查詢或計算。</span><span class="sxs-lookup"><span data-stu-id="0eabd-128">The report also lists any named query or calculation that cannot be successfully prepared.</span></span> <span data-ttu-id="0eabd-129">受影響的物件會列在樹狀檢視中，其中資料行和關聯性是以巢狀方式建立在資料表之下，並指出每一個物件的變更類型 (刪除或加入)。</span><span class="sxs-lookup"><span data-stu-id="0eabd-129">The affected objects are listed in a tree view with columns and relationships nested under tables and the type of change (deletion or addition) indicated for each object.</span></span> <span data-ttu-id="0eabd-130">標準資料來源檢視物件圖示會指出受影響的物件類型。</span><span class="sxs-lookup"><span data-stu-id="0eabd-130">The standard data source view object icons indicate the type of object affected.</span></span>

 <span data-ttu-id="0eabd-131">重新整理完全以基礎物件的名稱為基礎。</span><span class="sxs-lookup"><span data-stu-id="0eabd-131">Refresh is based completely on the names of the underlying objects.</span></span> <span data-ttu-id="0eabd-132">因此，如果在資料來源中重新命名基礎物件，資料來源視圖設計工具會將重新命名的物件視為兩個不同的作業，也就是刪除和加入。</span><span class="sxs-lookup"><span data-stu-id="0eabd-132">Therefore, if an underlying object is renamed in the data source, Data Source View Designer treats the renamed object as two separate operations-a deletion and an addition.</span></span> <span data-ttu-id="0eabd-133">在此案例中，您必須手動加入已重新命名的物件，讓它回到資料來源檢視中。</span><span class="sxs-lookup"><span data-stu-id="0eabd-133">In this case, you may have to manually add the renamed object back to the data source view.</span></span> <span data-ttu-id="0eabd-134">您也必須重新建立關聯性或邏輯主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0eabd-134">You may also have to re-create relationships or logical primary keys.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="0eabd-135">如果您知道資料表在資料來源中已重新命名，則在您重新整理資料來源檢視之前，您可以使用 [取代資料表]\*\*\*\* 命令，以重新命名的資料表來取代該資料表。</span><span class="sxs-lookup"><span data-stu-id="0eabd-135">If you are aware that a table has been renamed in a data source, you may want to use the **Replace Table** command to replace the table with the renamed table before you refresh the data source view.</span></span> <span data-ttu-id="0eabd-136">如需詳細資訊，請參閱[取代資料來源檢視中的資料表或具名查詢 &#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0eabd-136">For more information, see [Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md).</span></span>

 <span data-ttu-id="0eabd-137">當您檢查報表之後，可以接受變更，或是取消更新來拒絕任何變更。</span><span class="sxs-lookup"><span data-stu-id="0eabd-137">After you examine the report, you can either accept the changes or cancel the update to reject any changes.</span></span> <span data-ttu-id="0eabd-138">您必須一起接受或拒絕所有變更。</span><span class="sxs-lookup"><span data-stu-id="0eabd-138">All changes must be accepted or rejected together.</span></span> <span data-ttu-id="0eabd-139">您無法選擇清單中的個別項目。</span><span class="sxs-lookup"><span data-stu-id="0eabd-139">You cannot choose individual items in the list.</span></span> <span data-ttu-id="0eabd-140">您也可以儲存一份含有變更的報表。</span><span class="sxs-lookup"><span data-stu-id="0eabd-140">You can also save a report of the changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="0eabd-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eabd-141">See Also</span></span>
 [<span data-ttu-id="0eabd-142">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="0eabd-142">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)


