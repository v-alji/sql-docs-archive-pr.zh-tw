---
title: " (SSAS 表格式) 重新命名資料表或資料行 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.renametableorcolumn.f1
ms.assetid: 88061a39-c5aa-403d-a52b-7fdb365fc235
author: minewiskan
ms.author: owend
ms.openlocfilehash: d3a2e9a9f41434e64f9ec5ea2180861b459e8f97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706801"
---
# <a name="rename-a-table-or-column-ssas-tabular"></a><span data-ttu-id="fb42c-102">重新命名資料表或資料行 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="fb42c-102">Rename a Table or Column (SSAS Tabular)</span></span>
  <span data-ttu-id="fb42c-103">您可以在匯入程序期間，於 **[資料表匯入精靈]** 的 **[選取資料表和檢視表]** 頁面中輸入 **[易記名稱]** 來變更資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb42c-103">You can change the name of a table during the import process by typing a **Friendly Name** in the **Select Tables and Views** page of the **Table Import Wizard**.</span></span> <span data-ttu-id="fb42c-104">如果在 **[資料表匯入精靈]** 的 **[指定 SQL 查詢]** 頁面上指定查詢來匯入資料，也可以變更資料表和資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="fb42c-104">You can also change table and column names if you import data by specifying a query on the **Specify a SQL Query** page of the **Table Import Wizard**.</span></span>  
  
 <span data-ttu-id="fb42c-105">在您將資料加入至模型之後，資料表的名稱 (或標題) 會出現在模型設計師底部的資料表索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="fb42c-105">After you have added the data to the model, the name (or title) of a table appears on the table tab, at the bottom of the model designer.</span></span> <span data-ttu-id="fb42c-106">您可以變更資料表的名稱，為它提供一個更適合的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb42c-106">You can change the name of your table to give it a more appropriate name.</span></span> <span data-ttu-id="fb42c-107">您也可以在將資料加入到模型之後重新命名資料行。</span><span class="sxs-lookup"><span data-stu-id="fb42c-107">You can also rename a column after the data has been added to the model.</span></span> <span data-ttu-id="fb42c-108">如果您是從多個來源匯入資料，並想要確保不同資料表中的資料行具有容易區分的名稱時，這個選項特別重要。</span><span class="sxs-lookup"><span data-stu-id="fb42c-108">This option is especially important when you have imported data from multiple sources, and want to ensure that columns in different tables have names that are easy to distinguish.</span></span>  
  
### <a name="to-rename-a-table"></a><span data-ttu-id="fb42c-109">重新命名資料表</span><span class="sxs-lookup"><span data-stu-id="fb42c-109">To rename a table</span></span>  
  
1.  <span data-ttu-id="fb42c-110">在模型設計師中，以滑鼠右鍵按一下包含您要重新命名之資料表的索引標籤，然後按一下 **[重新命名]**。</span><span class="sxs-lookup"><span data-stu-id="fb42c-110">In the model designer, right-click the tab that contains the table that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="fb42c-111">輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb42c-111">Type the new name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fb42c-112">您可以使用 **[編輯資料表屬性]** 對話方塊，編輯資料表的其他屬性，包括連接資訊和資料行對應。</span><span class="sxs-lookup"><span data-stu-id="fb42c-112">You can edit other properties of a table, including the connection information and column mappings, by using the **Edit Table Properties** dialog box.</span></span> <span data-ttu-id="fb42c-113">不過，您無法在此對話方塊中變更名稱。</span><span class="sxs-lookup"><span data-stu-id="fb42c-113">However, you cannot change the name in this dialog box.</span></span>  
  
### <a name="to-rename-a-column"></a><span data-ttu-id="fb42c-114">重新命名資料行</span><span class="sxs-lookup"><span data-stu-id="fb42c-114">To rename a column</span></span>  
  
1.  <span data-ttu-id="fb42c-115">在模型設計師中，按兩下您要重新命名之資料行的標頭，或以滑鼠右鍵按一下標頭，然後從內容功能表中選取 **[重新命名資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="fb42c-115">In the model designer, double-click the header of the column that you want to rename, or right-click the header and select **Rename Column** from the context menu.</span></span>  
  
2.  <span data-ttu-id="fb42c-116">輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb42c-116">Type the new name.</span></span>  
  
## <a name="naming-requirements-for-columns-and-tables"></a><span data-ttu-id="fb42c-117">資料行和資料表的命名需求</span><span class="sxs-lookup"><span data-stu-id="fb42c-117">Naming Requirements for Columns and Tables</span></span>  
 <span data-ttu-id="fb42c-118">下列文字和字元無法用於資料表或資料行的名稱：</span><span class="sxs-lookup"><span data-stu-id="fb42c-118">The following words and characters cannot be used in the name of a table or column:</span></span>  
  
-   <span data-ttu-id="fb42c-119">開頭或尾端空白</span><span class="sxs-lookup"><span data-stu-id="fb42c-119">Leading or trailing spaces</span></span>  
  
-   <span data-ttu-id="fb42c-120">控制字元</span><span class="sxs-lookup"><span data-stu-id="fb42c-120">Control characters</span></span>  
  
-   <span data-ttu-id="fb42c-121">下列字元 (在 Analysis Services 物件的名稱中無效) ：.、; '：/ \\*|?&% $！ + = ( # A3 [] {}<></span><span class="sxs-lookup"><span data-stu-id="fb42c-121">The following characters (which are not valid in the names of Analysis Services objects): .,;':/\\*|?&%$!+=()[]{}<></span></span>  
  
-   <span data-ttu-id="fb42c-122">Analysis Services 保留關鍵字，包括多維度運算式 (MDX) 和資料採礦延伸模組 (DMX) 的函數名稱與運算子。</span><span class="sxs-lookup"><span data-stu-id="fb42c-122">Analysis Services reserved keywords, including Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) function names and operators.</span></span>  
  
## <a name="effect-of-renaming-on-existing-tables-columns-and-calculations"></a><span data-ttu-id="fb42c-123">重新命名對於現有的資料表、資料行和計算的影響</span><span class="sxs-lookup"><span data-stu-id="fb42c-123">Effect of Renaming on Existing Tables, Columns, and Calculations</span></span>  
 <span data-ttu-id="fb42c-124">每當您變更資料表的名稱時，您都會變更基礎資料表物件的名稱，其中可能包含多個資料行或量值。</span><span class="sxs-lookup"><span data-stu-id="fb42c-124">Whenever you change the name of a table, you change the name of the underlying table object, which may contain multiple columns or measures.</span></span> <span data-ttu-id="fb42c-125">因此，資料表中的任何資料行以及使用資料表的任何關聯性都必須更新，才能使用其定義中的新名稱。</span><span class="sxs-lookup"><span data-stu-id="fb42c-125">Therefore, any columns that are in the table, and any relationships that use the table, must be updated to use the new name in their definitions.</span></span> <span data-ttu-id="fb42c-126">在某些情況下，這個更新作業將會自動發生。</span><span class="sxs-lookup"><span data-stu-id="fb42c-126">This update happens automatically in some cases.</span></span> <span data-ttu-id="fb42c-127">量值並不會自動更新。</span><span class="sxs-lookup"><span data-stu-id="fb42c-127">Measures are not updated automatically.</span></span>  
  
 <span data-ttu-id="fb42c-128">此外，如果計算使用重新命名之資料表或是使用重新命名之資料表中的資料行，則也必須更新這些計算，而且從這些計算衍生的資料也必須重新整理及重新計算。</span><span class="sxs-lookup"><span data-stu-id="fb42c-128">Moreover, any calculations that use the renamed table, or that use columns from the renamed table, must also be updated, and the data derived from those calculations must be refreshed and recalculated.</span></span> <span data-ttu-id="fb42c-129">根據受到影響之資料表和計算的數目而定，完成這個程序可能需要一點時間。</span><span class="sxs-lookup"><span data-stu-id="fb42c-129">Depending on how many tables and calculations are affected, this can take some time to complete.</span></span> <span data-ttu-id="fb42c-130">因此，重新命名資料表的最佳時機是匯入期間，或是在您開始建立複雜關聯性和計算之前。</span><span class="sxs-lookup"><span data-stu-id="fb42c-130">Therefore, the best time to rename tables is either during the import process, or before you start to build complex relationships and calculations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb42c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb42c-131">See Also</span></span>  
 <span data-ttu-id="fb42c-132">[&#40;SSAS 表格式&#41;的資料表和資料行](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fb42c-132">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="fb42c-133">[從 PowerPivot 匯入 &#40;SSAS 表格式&#41;](import-from-power-pivot-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fb42c-133">[Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="fb42c-134">從 Analysis Services 匯入 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb42c-134">Import from Analysis Services &#40;SSAS Tabular&#41;</span></span>](import-from-analysis-services-ssas-tabular.md)  
  
  
