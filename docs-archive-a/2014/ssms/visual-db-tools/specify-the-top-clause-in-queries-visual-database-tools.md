---
title: 在查詢中指定 TOP 子句 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8228779703b1bbe3753f1e2728e83b4b5c3a3d17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708009"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a><span data-ttu-id="fafa6-102">在查詢中指定 TOP 子句 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fafa6-102">Specify the TOP Clause in Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="fafa6-103">TOP 子句只傳回查詢中的前 *n* 或百分之 *n* 個資料列。</span><span class="sxs-lookup"><span data-stu-id="fafa6-103">The TOP clause returns only the first *n* or *n percent* rows from a query.</span></span> <span data-ttu-id="fafa6-104">當您要調查結果的一部份，以了解查詢是否如預期運作時，TOP 子句會很有用，它不會使用傳回全部查詢結果所需的資源。</span><span class="sxs-lookup"><span data-stu-id="fafa6-104">The TOP clause is useful when you want to inspect a portion of your results to find out if your query does what you expect it to do, without taking the resources necessary to return all of the query results.</span></span>  
  
### <a name="to-specify-the-top-clause-in-queries"></a><span data-ttu-id="fafa6-105">若要指定查詢中的 TOP 子句</span><span class="sxs-lookup"><span data-stu-id="fafa6-105">To specify the TOP clause in queries</span></span>  
  
1.  <span data-ttu-id="fafa6-106">在 [方案總管] 中開啟查詢或建立新查詢。</span><span class="sxs-lookup"><span data-stu-id="fafa6-106">Open a query from Solution Explorer or create a new one.</span></span>  
  
2.  <span data-ttu-id="fafa6-107">從 [檢視]  功能表中，按一下 [屬性視窗]  。</span><span class="sxs-lookup"><span data-stu-id="fafa6-107">From the **View** menu, click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="fafa6-108">在 [屬性視窗]  中，找出並展開 [Top 規格]  屬性。</span><span class="sxs-lookup"><span data-stu-id="fafa6-108">In the **Properties Window**, locate and expand the **Top Specification** property.</span></span>  
  
4.  <span data-ttu-id="fafa6-109">按一下 [(Top)]  子屬性，並將其設定為 [Yes]  。</span><span class="sxs-lookup"><span data-stu-id="fafa6-109">Click the **(Top)** child property and set it to **Yes**.</span></span>  
  
5.  <span data-ttu-id="fafa6-110">在 [Expression]  子屬性中，輸入有數字結果 (例如 10 或 2\*5) 的運算式。</span><span class="sxs-lookup"><span data-stu-id="fafa6-110">In the **Expression** child property, type an expression that has a numeric result (for example, "10" or "2\*5").</span></span>  
  
6.  <span data-ttu-id="fafa6-111">按一下 [Percent]  子屬性，並指示是否將 [Expression]  屬性視為所有傳回資料列的百分比 (Yes)，或視為傳回資料列的絕對值 (No)。</span><span class="sxs-lookup"><span data-stu-id="fafa6-111">Click the **Percent** child property and indicate whether or not to treat the **Expression** property as a percentage of all rows returned (Yes) or as the absolute number of rows returned (No).</span></span>  
  
7.  <span data-ttu-id="fafa6-112">如果查詢使用 ORDER BY 子句，請按一下 [With Ties]  子屬性，並選擇 [Yes]  以顯示群組中的所有資料列 (如果此群組有一部份包含在內)，或選擇 [No]  將它們截斷。</span><span class="sxs-lookup"><span data-stu-id="fafa6-112">If your query uses the ORDER BY clause, click the **With Ties** child property and choose **Yes** to display all rows in a group if only part of the group is included or **No** to truncate them.</span></span>  
  
 <span data-ttu-id="fafa6-113">在進行先前的程序之後，注意 SQL 窗格中顯示的 TOP 子句會變更，以反映目前的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="fafa6-113">As you work through the preceding procedure, notice that the TOP clause, displayed in the SQL pane, changes to reflect the current settings of the properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fafa6-114">您也可以編輯 SQL 窗格中的 TOP 子句，以變更 [Top 規格]  中的子屬性值。</span><span class="sxs-lookup"><span data-stu-id="fafa6-114">You can also change the values of the child properties of the **Top Specification** by editing the TOP clause in the SQL pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafa6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fafa6-115">See Also</span></span>  
 <span data-ttu-id="fafa6-116">[設計查詢和觀看 how to 主題 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="fafa6-116">[Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="fafa6-117">查詢屬性 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fafa6-117">Query Properties &#40;Visual Database Tools&#41;</span></span>](query-properties-visual-database-tools.md)  
  
  
