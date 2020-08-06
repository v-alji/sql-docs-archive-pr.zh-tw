---
title: 指定群組條件 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: stevestein
ms.author: sstein
ms.openlocfilehash: da9bc1b70fbfae8bf2a68a3a3ba332020020f310
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584220"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a><span data-ttu-id="1121b-102">指定群組條件 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1121b-102">Specify Conditions for Groups (Visual Database Tools)</span></span>
  <span data-ttu-id="1121b-103">您可以指定套用至整體群組的條件 (即 HAVING 子句)，以限制出現在查詢中的群組。</span><span class="sxs-lookup"><span data-stu-id="1121b-103">You can limit the groups that appear in a query by specifying a condition that applies to groups as a whole - a HAVING clause.</span></span> <span data-ttu-id="1121b-104">在資料經過分組及彙總 (Aggregate) 之後，便會套用 HAVING 子句中的條件。</span><span class="sxs-lookup"><span data-stu-id="1121b-104">After the data has been grouped and aggregated, the conditions in the HAVING clause are applied.</span></span> <span data-ttu-id="1121b-105">只有符合條件的群組才會出現在查詢結果中。</span><span class="sxs-lookup"><span data-stu-id="1121b-105">Only the groups that meet the conditions appear in the query.</span></span>  
  
 <span data-ttu-id="1121b-106">例如，您可能想查看 `titles` 資料表中每個發行者的所有書籍的平均價格，但是只限於平均價格超過 $10.00。</span><span class="sxs-lookup"><span data-stu-id="1121b-106">For example, you might want to see the average price of all books for each publisher in a `titles` table, but only if the average price exceeds $10.00.</span></span> <span data-ttu-id="1121b-107">在此情況下，您可以指定包含 `AVG(price) > 10`之類條件的 HAVING 子句。</span><span class="sxs-lookup"><span data-stu-id="1121b-107">In that case, you could specify a HAVING clause with a condition such as `AVG(price) > 10`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1121b-108">在某些情況下，您可能想在將條件套用到整體群組之前，從群組排除個別的資料列。</span><span class="sxs-lookup"><span data-stu-id="1121b-108">In some instances, you might want to exclude individual rows from groups before applying a condition to groups as a whole.</span></span> <span data-ttu-id="1121b-109">如需詳細資訊，請參閱[在相同查詢中使用 HAVING 和 WHERE 子句 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1121b-109">For details, see [Use HAVING and WHERE Clauses in the Same Query &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="1121b-110">您可以使用 AND 和 OR 連結條件，以建立 HAVING 子句的複雜條件。</span><span class="sxs-lookup"><span data-stu-id="1121b-110">You can create complex conditions for a HAVING clause by using AND and OR to link conditions.</span></span> <span data-ttu-id="1121b-111">如需在搜尋條件中使用 AND 和 OR 的詳細資訊，請參閱[指定單一資料行的多重搜尋條件 &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1121b-111">For details about using AND and OR in search conditions, see [Specify Multiple Search Conditions for One Column &#40;Visual Database Tools&#41;](specify-multiple-search-conditions-for-one-column-visual-database-tools.md).</span></span>  
  
### <a name="to-specify-a-condition-for-a-group"></a><span data-ttu-id="1121b-112">若要指定群組條件</span><span class="sxs-lookup"><span data-stu-id="1121b-112">To specify a condition for a group</span></span>  
  
1.  <span data-ttu-id="1121b-113">為您的查詢指定群組。</span><span class="sxs-lookup"><span data-stu-id="1121b-113">Specify the groups for your query.</span></span> <span data-ttu-id="1121b-114">如需詳細資訊，請參閱[群組查詢結果中的資料列 &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1121b-114">For details, see [Group Rows in Query Results &#40;Visual Database Tools&#41;](group-rows-in-query-results-visual-database-tools.md).</span></span>  
  
2.  <span data-ttu-id="1121b-115">如果[準則窗格](criteria-pane-visual-database-tools.md)中沒有您要做為條件基礎的資料行，請新增它。</span><span class="sxs-lookup"><span data-stu-id="1121b-115">If it is not already in the [Criteria pane](criteria-pane-visual-database-tools.md), add the column on which you want to base the condition.</span></span> <span data-ttu-id="1121b-116">(條件通常牽涉已經是群組或摘要資料行的資料行)。您無法使用不屬於彙總函式 (Aggregate Function) 或 GROUP BY 子句一部分的資料行。</span><span class="sxs-lookup"><span data-stu-id="1121b-116">(Most often the condition involves a column that is already a group or summary column.) You cannot use a column that is not part of an aggregate function or of the GROUP BY clause.</span></span>  
  
3.  <span data-ttu-id="1121b-117">在 [篩選條件]  欄位中，指定要套用至群組的條件。</span><span class="sxs-lookup"><span data-stu-id="1121b-117">In the **Filter** column, specify the condition to apply to the group.</span></span>  
  
     <span data-ttu-id="1121b-118">[查詢和檢視表設計工具](query-and-view-designer-tools-visual-database-tools.md)會自動在 [SQL 窗格](sql-pane-visual-database-tools.md)的陳述式中建立 HAVING 子句，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1121b-118">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) automatically creates a HAVING clause in the statement in the [SQL pane](sql-pane-visual-database-tools.md), such as in the following example:</span></span>  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
  
    ```  
  
4.  <span data-ttu-id="1121b-119">對想要指定的每個額外條件重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="1121b-119">Repeat steps 2 and 3 for each additional condition you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1121b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1121b-120">See Also</span></span>  
 [<span data-ttu-id="1121b-121">排序及分組查詢結果 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1121b-121">Sort and Group Query Results &#40;Visual Database Tools&#41;</span></span>](sort-and-group-query-results-visual-database-tools.md)  
  
  
