---
title: 指定搜尋條件 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa5dab8326de079c385a3a508bc1b01b1ee1247d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595353"
---
# <a name="specify-search-conditions-visual-database-tools"></a><span data-ttu-id="3f632-102">指定搜尋條件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3f632-102">Specify Search Conditions (Visual Database Tools)</span></span>
  <span data-ttu-id="3f632-103">您可以藉由指定搜尋條件來指定出現在查詢中的資料列。</span><span class="sxs-lookup"><span data-stu-id="3f632-103">You can specify the data rows that appear in your query by specifying search conditions.</span></span> <span data-ttu-id="3f632-104">例如，若是正在查詢 `employee` 資料表，可以指定只尋找在特定區域工作的員工。</span><span class="sxs-lookup"><span data-stu-id="3f632-104">For example, if you are querying an `employee` table, you can specify that you want to find only the employees who work in a particular region.</span></span>  
  
 <span data-ttu-id="3f632-105">使用運算式指定搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="3f632-105">You specify search conditions using an expression.</span></span> <span data-ttu-id="3f632-106">通常運算式包含運算子和搜尋值。</span><span class="sxs-lookup"><span data-stu-id="3f632-106">Most commonly the expression consists of an operator and a search value.</span></span> <span data-ttu-id="3f632-107">例如，若要尋找在特定銷售區域的員工，可以在 `region` 資料行指定下列搜尋準則：</span><span class="sxs-lookup"><span data-stu-id="3f632-107">For example, to find employees in a particular sales region, you might specify the following search criterion for the `region` column:</span></span>  
  
```  
='UK'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3f632-108">如果使用多個資料表，[查詢和檢視設計師] 會檢查每個搜尋條件，判斷您所做的比較是否會產生聯結。</span><span class="sxs-lookup"><span data-stu-id="3f632-108">If you are working with multiple tables, the Query and View Designer examines each search condition to determine whether the comparison you are making results in a join.</span></span> <span data-ttu-id="3f632-109">若是如此，[查詢和檢視設計師] 會自動將搜尋條件轉換至聯結。</span><span class="sxs-lookup"><span data-stu-id="3f632-109">If so, the Query and View Designer automatically converts the search condition into a join.</span></span> <span data-ttu-id="3f632-110">如需詳細資訊，請參閱[自動聯結資料表 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="3f632-110">For more information, see [Join Tables Automatically &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
### <a name="to-specify-search-conditions"></a><span data-ttu-id="3f632-111">若要指定搜尋條件</span><span class="sxs-lookup"><span data-stu-id="3f632-111">To specify search conditions</span></span>  
  
1.  <span data-ttu-id="3f632-112">如果尚未這麼做，請將想要在搜尋條件中使用的資料行或運算式加入至 [準則] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="3f632-112">If you have not done so already, add the columns or expressions that you want to use within your search condition to the Criteria pane.</span></span>  
  
     <span data-ttu-id="3f632-113">如果您正在建立選取查詢，而不想讓搜尋資料行或運算式出現在查詢輸出中，請清除每一個搜尋資料行或運算式的 [輸出]  欄位，將它們當成輸出資料行而加以移除。</span><span class="sxs-lookup"><span data-stu-id="3f632-113">If you are creating a Select query and do not want the search columns or expressions to appear in the query output, clear the **Output** column for each search column or expression to remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="3f632-114">尋找包含想要搜尋之資料行或運算式的資料列，然後在 [篩選條件]  欄位中輸入搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="3f632-114">Locate the row containing the data column or expression to search, and then in the **Filter** column, enter a search condition.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3f632-115">如果尚未輸入運算子，[查詢和檢視設計師] 會自動插入相等運算子「=」。</span><span class="sxs-lookup"><span data-stu-id="3f632-115">If you do not enter an operator, the Query and View Designer automatically inserts the equality operator "=".</span></span>  
  
 <span data-ttu-id="3f632-116">查詢和檢視表設計工具藉由加入或修改 WHERE 子句，更新 [SQL 窗格](sql-pane-visual-database-tools.md) 中的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3f632-116">The Query and View Designer updates the SQL statement in the [SQL Pane](sql-pane-visual-database-tools.md) by adding or modifying the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f632-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f632-117">See Also</span></span>  
 <span data-ttu-id="3f632-118">[&#40;Visual Database Tools 輸入搜尋值的規則&#41;](rules-for-entering-search-values-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="3f632-118">[Rules for Entering Search Values &#40;Visual Database Tools&#41;](rules-for-entering-search-values-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="3f632-119">指定搜尋準則 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="3f632-119">Specify Search Criteria &#40;Visual Database Tools&#41;</span></span>](specify-search-criteria-visual-database-tools.md)  
  
  
