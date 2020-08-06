---
title: 自動聯結資料表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- joins [SQL Server], creating
- joins [SQL Server], automatic
ms.assetid: f152af82-bcb6-49ca-af19-48cdb7fc9ac6
author: stevestein
ms.author: sstein
ms.openlocfilehash: d05100f801d972759c1b5c105814f5cdbdccf84f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686686"
---
# <a name="join-tables-automatically-visual-database-tools"></a><span data-ttu-id="ddf68-102">自動聯結資料表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ddf68-102">Join Tables Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="ddf68-103">當您將兩個或多個資料表新增至查詢時， [查詢和檢視表設計工具](visual-database-tools.md) 會嘗試判斷它們是否相關。</span><span class="sxs-lookup"><span data-stu-id="ddf68-103">When you add two or more tables to a query, the [Query and View Designer](visual-database-tools.md) attempts to determine if they are related.</span></span> <span data-ttu-id="ddf68-104">如果相關聯，查詢和檢視設計師會自動在代表資料表或表格化物件的矩形之間加上聯結線 (Join Line)。</span><span class="sxs-lookup"><span data-stu-id="ddf68-104">If they are, the Query and View Designer automatically puts join lines between the rectangles representing the tables or table-structured objects.</span></span>  
  
 <span data-ttu-id="ddf68-105">在下列狀況下，查詢和檢視設計師會將資料表當做已聯結：</span><span class="sxs-lookup"><span data-stu-id="ddf68-105">The Query and View Designer will recognize tables as joined if:</span></span>  
  
-   <span data-ttu-id="ddf68-106">資料庫包含指定資料表為相關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="ddf68-106">The database contains information that specifies that the tables are related.</span></span>  
  
-   <span data-ttu-id="ddf68-107">如果兩個資料行 (每個資料表各一個資料行) 的名稱和資料類型相同，</span><span class="sxs-lookup"><span data-stu-id="ddf68-107">If two columns, one in each table, have the same name and data type.</span></span> <span data-ttu-id="ddf68-108">至少一個資料表中的資料行必須為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ddf68-108">The column must be a primary key in at least one of the tables.</span></span> <span data-ttu-id="ddf68-109">例如，如果加入 `employee` 和 `jobs` 資料表，如果 `job_id` 資料行為 `jobs` 資料表的主索引鍵，如果每個資料表中稱為 `job_id` 的資料行有相同的資料類型，則查詢和檢視設計師將自動聯結資料表。</span><span class="sxs-lookup"><span data-stu-id="ddf68-109">For example, if you add `employee` and `jobs` tables, if the `job_id` column is the primary key in the `jobs` table, and if each table has a column called `job_id` with the same data type, the Query and View Designer will automatically join the tables.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ddf68-110">查詢和檢視設計師將根據名稱和資料類型相同的資料行，來建立唯一的聯結。</span><span class="sxs-lookup"><span data-stu-id="ddf68-110">The Query and View Designer will create only one join based on columns with the same name and data type.</span></span> <span data-ttu-id="ddf68-111">如果可能有多個聯結，查詢和檢視設計師在根據它所找到的第一組符合的資料行來建立聯結之後就會停止。</span><span class="sxs-lookup"><span data-stu-id="ddf68-111">If more than one join is possible, the Query and View Designer stops after creating a join based on the first set of matching columns that it finds.</span></span>  
  
-   <span data-ttu-id="ddf68-112">查詢和檢視設計師偵測到搜尋條件 (WHERE 子句) 實際上就是聯結條件 (Join Condition)。</span><span class="sxs-lookup"><span data-stu-id="ddf68-112">The Query and View Designer detects that a search condition (a WHERE clause) is actually a join condition.</span></span> <span data-ttu-id="ddf68-113">例如，您可能加入資料表 `employee` 和 `jobs`，然後建立搜尋兩個資料表的 `job_id` 資料行中相同值的搜尋條件。</span><span class="sxs-lookup"><span data-stu-id="ddf68-113">For example, you might add the tables `employee` and `jobs`, then create a search condition that searches for the same value in the `job_id` column of both tables.</span></span> <span data-ttu-id="ddf68-114">在進行此作業時，查詢和檢視設計師會偵測到搜尋條件將導致聯結，然後根據此搜尋條件來建立聯結條件。</span><span class="sxs-lookup"><span data-stu-id="ddf68-114">When you do, the Query and View Designer detects that the search condition results in a join, and then creates a join condition based on the search condition.</span></span>  
  
 <span data-ttu-id="ddf68-115">如果查詢和檢視設計師已建立不適用於您的查詢的聯結，就可以修改或移除聯結。</span><span class="sxs-lookup"><span data-stu-id="ddf68-115">If the Query and View Designer has created a join that is not suitable to your query, you can modify the join or remove it.</span></span> <span data-ttu-id="ddf68-116">如需詳細資訊，請參閱[修改聯結運算子 &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) 和[移除聯結 &#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf68-116">For details, see [Modify Join Operators &#40;Visual Database Tools&#41;](modify-join-operators-visual-database-tools.md) and [Remove Joins &#40;Visual Database Tools&#41;](remove-joins-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="ddf68-117">如果查詢和檢視設計師不會自動聯結查詢中的資料表，則可以自行建立聯結。</span><span class="sxs-lookup"><span data-stu-id="ddf68-117">If the Query and View Designer does not automatically join the tables in your query, you can create a join yourself.</span></span> <span data-ttu-id="ddf68-118">如需詳細資料，請參閱[手動聯結資料表 &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="ddf68-118">For details, see [Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf68-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddf68-119">See Also</span></span>  
 <span data-ttu-id="ddf68-120">[查詢和視圖設計工具如何表示 &#40;Visual Database Tools 的聯結&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ddf68-120">[How the Query and View Designer Represents Joins &#40;Visual Database Tools&#41;](how-the-query-and-view-designer-represents-joins-visual-database-tools.md) </span></span>  
 <span data-ttu-id="ddf68-121">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ddf68-121">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ddf68-122">使用聯結查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ddf68-122">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
