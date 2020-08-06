---
title: 將資料行加入查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- queries [SQL Server], columns
- adding columns
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 49c6e575eea2d4437be1f16b400ca22120471fcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593768"
---
# <a name="add-columns-to-queries-visual-database-tools"></a><span data-ttu-id="aa85a-102">將資料行加入查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="aa85a-102">Add Columns to Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="aa85a-103">若要在查詢中使用資料行，您必須將資料行加入至查詢。</span><span class="sxs-lookup"><span data-stu-id="aa85a-103">To use a column in a query, you must add it to the query.</span></span> <span data-ttu-id="aa85a-104">您可能會加入資料行以便在查詢輸出中顯示資料行、使用資料行進行排序、搜尋資料行內容，或者摘要資料行內容。</span><span class="sxs-lookup"><span data-stu-id="aa85a-104">You might add a column to display it in query output, to use it for sorting, to search the contents of the column, or to summarize its contents.</span></span> <span data-ttu-id="aa85a-105">您可以決定在執行查詢時，結果窗格中包含哪些查詢中所使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="aa85a-105">You can decide which of the columns you use in the query are included in the results pane when the query is run.</span></span> <span data-ttu-id="aa85a-106">如需詳細資訊，請參閱[移除查詢結果的資料行 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="aa85a-106">For more information see [Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa85a-107">若要在查詢和檢視表設計工具中檢視資料類型，可以在 [圖表]  窗格中選取資料表或資料表值物件，並且在 [屬性] 視窗中按一下 [資料行清單]。</span><span class="sxs-lookup"><span data-stu-id="aa85a-107">To view the data type of a column in Query and View Designer; select the table or table-valued object in the **Diagram Pane** and in the properties window click Column List.</span></span> <span data-ttu-id="aa85a-108">然後按一下**省略符號 (…)** 以開啟 [資料行清單]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="aa85a-108">Then click the **ellipses (...)** to open the **Column List** dialog box.</span></span>  
  
 <span data-ttu-id="aa85a-109">無論在何處使用查詢中的資料行，您也可以使用由任何資料行、常值、運算子和函數組合所組成的運算式。</span><span class="sxs-lookup"><span data-stu-id="aa85a-109">Wherever you use a column in a query, you can also use an expression that can consist of any combination of columns, literals, operators, and functions.</span></span>  
  
### <a name="to-add-an-individual-column"></a><span data-ttu-id="aa85a-110">若要新增個別資料行</span><span class="sxs-lookup"><span data-stu-id="aa85a-110">To add an individual column</span></span>  
  
-   <span data-ttu-id="aa85a-111">在 [圖表]  窗格中，選取您要加入的資料行旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="aa85a-111">In the **Diagram Pane**, select the check box next to the column that you want to include.</span></span>  
  
     <span data-ttu-id="aa85a-112">-或-</span><span class="sxs-lookup"><span data-stu-id="aa85a-112">-or-</span></span>  
  
-   <span data-ttu-id="aa85a-113">在 [準則]  窗格中，移至第一個空白的方格資料列，按一下 [ 資料行]  資料行中的欄位，然後從下拉式清單中選取資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="aa85a-113">In the **Criteria Pane**, move to the first blank grid row, click the field in the **Column** column, and select a column name from the drop-down list.</span></span>  
  
### <a name="to-add-all-columns-for-one-table-or-table-valued-object"></a><span data-ttu-id="aa85a-114">若要針對一個資料表或資料表值物件新增所有資料行</span><span class="sxs-lookup"><span data-stu-id="aa85a-114">To add all columns for one table or table-valued object</span></span>  
  
-   <span data-ttu-id="aa85a-115">在 [**圖表] 窗格**中，選取 [ \*\* \* (所有資料行\*\*] 旁的核取方塊) 。</span><span class="sxs-lookup"><span data-stu-id="aa85a-115">In the **Diagram Pane**, select the check box next to **\*(All Columns)**.</span></span>  
  
### <a name="to-add-all-columns-for-all-tables-and-table-structured-objects"></a><span data-ttu-id="aa85a-116">若要針對所有資料表和表格化物件 (Table-Structured Object) 新增所有資料表</span><span class="sxs-lookup"><span data-stu-id="aa85a-116">To add all columns for all tables and table-structured objects</span></span>  
  
1.  <span data-ttu-id="aa85a-117">請確定 [資料表運算]  窗格中未選取任何聯結線 (Join Line)。</span><span class="sxs-lookup"><span data-stu-id="aa85a-117">Make sure no join lines in the **Table Operations Pane** are selected.</span></span>  
  
2.  <span data-ttu-id="aa85a-118">在 [設計] 視窗的空白處按一下滑鼠右鍵，然後從快速鍵功能表中選擇 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="aa85a-118">Right-click in the empty space of the Design window and choose **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="aa85a-119">在 [屬性] 視窗中，按一下 [輸出全部資料行]  ，然後從下拉式清單中選擇 [是]  或 [否]  。</span><span class="sxs-lookup"><span data-stu-id="aa85a-119">In the Properties window click **Output all columns** and choose **Yes** or **No** from the dropdown list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa85a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa85a-120">See Also</span></span>  
 <span data-ttu-id="aa85a-121">[從查詢結果中移除資料行 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="aa85a-121">[Remove Columns from Query Results &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="aa85a-122">[從查詢中移除資料行 &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="aa85a-122">[Remove Columns from Queries &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="aa85a-123">[&#40;Visual Database Tools 指定搜尋準則&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="aa85a-123">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="aa85a-124">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="aa85a-124">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="aa85a-125">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="aa85a-125">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
