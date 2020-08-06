---
title: 重新排列輸出資料行順序 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 97fa3f768b03f24b8c8d154624a2d7a91aba45f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596421"
---
# <a name="reorder-output-columns-visual-database-tools"></a><span data-ttu-id="ae4b2-102">重新排列輸出資料行順序 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ae4b2-102">Reorder Output Columns (Visual Database Tools)</span></span>
  <span data-ttu-id="ae4b2-103">資料行加入選取查詢中的順序，決定資料行出現在結果中的順序。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-103">The order in which you add data columns to a Select query determines the order in which they appear in the results.</span></span> <span data-ttu-id="ae4b2-104">第一個加入的資料行會出現在結果的最左側，接著是第二個資料行，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-104">The first column you add to the query appears leftmost in the results, the second column next, and so on.</span></span>  
  
 <span data-ttu-id="ae4b2-105">如果您建立了更新或插入查詢，加入資料行的順序會影響資料處理的順序。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-105">If you are creating Update or Insert queries, the order in which you add columns affects the order in which data is processed.</span></span>  
  
 <span data-ttu-id="ae4b2-106">若要控制資料行出現在結果集的位置，或是使用的順序，您可以重新排序資料行。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-106">To control where a data column appears in the result set, or in what order it is used, you can reorder the columns.</span></span>  
  
### <a name="to-reorder-columns-for-output"></a><span data-ttu-id="ae4b2-107">若要重新排序輸出的資料行</span><span class="sxs-lookup"><span data-stu-id="ae4b2-107">To reorder columns for output</span></span>  
  
1.  <span data-ttu-id="ae4b2-108">在 [準則窗格](visual-database-tools.md)中，按一下資料列左側的資料列資料列選取器按鈕，選取包含資料行的資料列。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-108">In the [Criteria pane](visual-database-tools.md), select the row containing the column by clicking the row selector button to the left of the row.</span></span>  
  
2.  <span data-ttu-id="ae4b2-109">指向資料列選取器按鈕，將資料列拖曳到新的位置。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-109">Point to the row selector button and drag the row to a new location.</span></span>  
  
     <span data-ttu-id="ae4b2-110">-或-</span><span class="sxs-lookup"><span data-stu-id="ae4b2-110">-or-</span></span>  
  
     <span data-ttu-id="ae4b2-111">在 [SQL 窗格](sql-pane-visual-database-tools.md)中編輯資料行名稱順序。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-111">Edit the order of the column names in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ae4b2-112">您可以在 [準則] 窗格中先插入空白資料列，然後指定想要插入的資料行，這樣就可以將資料列加入到 [準則] 窗格中的指定位置。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-112">You can add a data row at a specific location in the Criteria pane by inserting a blank row into the Criteria pane, and then specifying the data column to insert.</span></span> <span data-ttu-id="ae4b2-113">如需詳細資訊，請參閱[將資料行新增至查詢 &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ae4b2-113">For details, see [Add Columns to Queries &#40;Visual Database Tools&#41;](add-columns-to-queries-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4b2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae4b2-114">See Also</span></span>  
 <span data-ttu-id="ae4b2-115">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ae4b2-115">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ae4b2-116">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ae4b2-116">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ae4b2-117">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ae4b2-117">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
