---
title: " (SSAS 表格式) 篩選資料表中的資料 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f4003457df4068713e75e6bb5c0ab78c15ac03c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687241"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a><span data-ttu-id="cd2b3-102">篩選資料表中的資料 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="cd2b3-102">Filter Data in a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="cd2b3-103">您可以在匯入資料時套用篩選，以控制要載入資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-103">You can apply filters when you import data to control the rows that are loaded into a table.</span></span> <span data-ttu-id="cd2b3-104">匯入資料之後，您就無法刪除個別的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-104">After you have imported the data, you cannot delete individual rows.</span></span> <span data-ttu-id="cd2b3-105">但是，您可以套用自訂篩選來控制資料列的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-105">However, you can apply custom filters to control the way that rows are displayed.</span></span> <span data-ttu-id="cd2b3-106">不符合篩選準則的資料列則會隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-106">Rows that do not meet the filtering criteria are hidden.</span></span> <span data-ttu-id="cd2b3-107">您可以依一個或多個資料行進行篩選。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-107">You can filter by one or more columns.</span></span> <span data-ttu-id="cd2b3-108">篩選會加總，也就是說，每一個額外的篩選都會以目前的篩選為基礎，並進一步減少資料子集。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-108">Filters are additive, which means that each additional filter is based on the current filter and further reduces the subset of data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd2b3-109">篩選預覽視窗會限制顯示的不同值數量。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-109">The filter preview window limits the number of different values displayed.</span></span> <span data-ttu-id="cd2b3-110">如果超出限制，將顯示一則訊息。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-110">If the limit is exceeded, a message is displayed.</span></span>  
  
### <a name="to-filter-data-based-on-column-values"></a><span data-ttu-id="cd2b3-111">若要根據資料行值篩選資料</span><span class="sxs-lookup"><span data-stu-id="cd2b3-111">To filter data based on column values</span></span>  
  
1.  <span data-ttu-id="cd2b3-112">在模型設計師中，選取資料表，然後按一下您要做為篩選依據之資料行標頭的箭頭。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-112">In the model designer, select a table, and then click the arrow in the header of the column that you want to filter by.</span></span>  
  
2.  <span data-ttu-id="cd2b3-113">在 [自動篩選] 功能表中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="cd2b3-113">In the AutoFilter menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="cd2b3-114">在資料行值清單中，選取或清除做為篩選依據的一個或多個值，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-114">In the list of column values, select or clear one or more values to filter by, and then click **OK**.</span></span>  
  
         <span data-ttu-id="cd2b3-115">如果值的數量非常大，在清單中可能不會顯示個別的項目。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-115">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="cd2b3-116">但是您會看到「要顯示的項目太多」這個訊息。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-116">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="cd2b3-117">按一下 [**數位篩選**] 或 [**文字篩選** (]，視) 的資料行類型而定，然後按一下其中一個比較運算子命令 (例如**Equals**) ，或按一下 [**自訂篩選**]。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-117">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as **Equals**), or click **Custom Filter**.</span></span> <span data-ttu-id="cd2b3-118">在 **[自訂篩選]** 對話方塊中，建立篩選，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-118">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
### <a name="to-clear-a-filter-for-a-column"></a><span data-ttu-id="cd2b3-119">若要清除資料行的篩選</span><span class="sxs-lookup"><span data-stu-id="cd2b3-119">To clear a filter for a column</span></span>  
  
1.  <span data-ttu-id="cd2b3-120">按一下您要清除篩選之資料行標頭中的箭號。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-120">Click the arrow in the header of the column for which you want to clear a filter.</span></span>  
  
2.  <span data-ttu-id="cd2b3-121">按一下 [**清除篩選 \<Column Name> 來源**]。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-121">Click **Clear Filter from \<Column Name>**.</span></span>  
  
### <a name="to-clear-all-filters-for-a-table"></a><span data-ttu-id="cd2b3-122">清除資料表的所有篩選</span><span class="sxs-lookup"><span data-stu-id="cd2b3-122">To clear all filters for a table</span></span>  
  
1.  <span data-ttu-id="cd2b3-123">在模型設計師中，選取您要為其清除篩選的資料表。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-123">In the model designer, select the table for which you want to clear filters.</span></span>  
  
2.  <span data-ttu-id="cd2b3-124">按一下 **[資料行]** 功能表，然後按一下 **[清除所有篩選]**。</span><span class="sxs-lookup"><span data-stu-id="cd2b3-124">Click on the **Column** menu, and then click **Clear All Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2b3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd2b3-125">See Also</span></span>  
 <span data-ttu-id="cd2b3-126">[&#40;SSAS 表格式&#41;篩選和排序資料](../filter-and-sort-data-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="cd2b3-126">[Filter and Sort Data &#40;SSAS Tabular&#41;](../filter-and-sort-data-ssas-tabular.md) </span></span>  
 <span data-ttu-id="cd2b3-127">[SSAS 表格式 &#40;的觀點&#41;](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="cd2b3-127">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="cd2b3-128">角色 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="cd2b3-128">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
