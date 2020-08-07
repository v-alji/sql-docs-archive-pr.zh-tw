---
title: 建立資料表別名 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f9e6269fe6e24e8d98922094e799fbf4b5af584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596993"
---
# <a name="create-table-aliases-visual-database-tools"></a><span data-ttu-id="92f29-102">建立資料表別名 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="92f29-102">Create Table Aliases (Visual Database Tools)</span></span>
  <span data-ttu-id="92f29-103">別名可以更容易使用資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="92f29-103">Aliases can make it easier to work with table names.</span></span> <span data-ttu-id="92f29-104">在下列狀況時，使用別名會非常有用：</span><span class="sxs-lookup"><span data-stu-id="92f29-104">Using aliases is helpful when:</span></span>  
  
-   <span data-ttu-id="92f29-105">讓 [SQL 窗格](visual-database-tools.md) 中的陳述式更簡短、更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="92f29-105">You want to make the statement in the [SQL Pane](visual-database-tools.md) shorter and easier to read.</span></span>  
  
-   <span data-ttu-id="92f29-106">您經常在查詢中參閱資料表名稱 - 例如在限定資料行名稱中 - 並且希望確保維持在查詢的特定字元長度限制內。</span><span class="sxs-lookup"><span data-stu-id="92f29-106">You refer to the table name often in your query - such as in qualifying column names - and want to be sure you stay within a specific character-length limit for your query.</span></span> <span data-ttu-id="92f29-107">(某些資料庫會限制查詢的最大長度)。</span><span class="sxs-lookup"><span data-stu-id="92f29-107">(Some databases impose a maximum length for queries.)</span></span>  
  
-   <span data-ttu-id="92f29-108">您使用相同資料表的多個執行個體 (例如自我聯結)，然後需要參考到一個或另外一個執行個體的方式。</span><span class="sxs-lookup"><span data-stu-id="92f29-108">You are working with multiple instances of the same table (such as in a self-join) and need a way to refer to one instance or the other.</span></span>  
  
 <span data-ttu-id="92f29-109">例如，您可以針對資料表名稱 `"e"` _ `employee`建立別名`information`，然後在整個查詢的其他部份以 `"e"` 的方式參考資料表。</span><span class="sxs-lookup"><span data-stu-id="92f29-109">For example, you can create an alias `"e"` for a table name `employee`_`information`, and then refer to the table as `"e"` throughout the rest of the query.</span></span>  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a><span data-ttu-id="92f29-110">若要建立資料表或資料表值物件的別名</span><span class="sxs-lookup"><span data-stu-id="92f29-110">To create an alias for a table or table-valued object</span></span>  
  
1.  <span data-ttu-id="92f29-111">將資料表或資料表值物件加入到查詢。</span><span class="sxs-lookup"><span data-stu-id="92f29-111">Add the table or table-valued object to your query.</span></span>  
  
2.  <span data-ttu-id="92f29-112">在 [圖表]  窗格中，在想要建立別名的物件按一下滑鼠右鍵，然後從快速鍵功能表中選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="92f29-112">In the **Diagram Pane**, right-click the object for which you want to create an alias, then select **Properties** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="92f29-113">在 [屬性]  視窗中的 [別名]  欄位，輸入別名。</span><span class="sxs-lookup"><span data-stu-id="92f29-113">In the **Properties** window, enter the alias in the **Alias** field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f29-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92f29-114">See Also</span></span>  
 <span data-ttu-id="92f29-115">[將資料表加入至查詢 &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="92f29-115">[Add Tables to Queries &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md) </span></span>  
 <span data-ttu-id="92f29-116">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="92f29-116">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 <span data-ttu-id="92f29-117">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="92f29-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="92f29-118">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="92f29-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
