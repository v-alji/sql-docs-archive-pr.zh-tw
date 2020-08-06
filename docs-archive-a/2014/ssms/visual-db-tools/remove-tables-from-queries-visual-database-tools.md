---
title: 移除查詢的資料表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
author: stevestein
ms.author: sstein
ms.openlocfilehash: fab5380e13742f3cd289ce17f26ad2e5fb9089ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595357"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a><span data-ttu-id="1300b-102">移除查詢的資料表 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1300b-102">Remove Tables from Queries (Visual Database Tools)</span></span>
  <span data-ttu-id="1300b-103">您可以從查詢移除資料表或任何資料表值物件。</span><span class="sxs-lookup"><span data-stu-id="1300b-103">You can remove a table - or any table-valued object - from the query.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1300b-104">移除資料表或資料表值物件並不會從資料庫刪除任何東西，只是從目前的查詢中移除。</span><span class="sxs-lookup"><span data-stu-id="1300b-104">Removing a table or table-valued object does not delete anything from the database; it only removes it from the current query.</span></span> <span data-ttu-id="1300b-105">如需從資料庫移除資料表的詳細資訊，請參閱[&#40;資料庫引擎&#41;中刪除資料表](../../relational-databases/tables/delete-tables-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="1300b-105">For details about removing a table from a database, see [Delete Tables &#40;Database Engine&#41;](../../relational-databases/tables/delete-tables-database-engine.md).</span></span>  
  
### <a name="to-remove-a-table-or-table-structured-object"></a><span data-ttu-id="1300b-106">若要移除資料表或表格化物件</span><span class="sxs-lookup"><span data-stu-id="1300b-106">To remove a table or table-structured object</span></span>  
  
-   <span data-ttu-id="1300b-107">在 [圖表]  窗格中，選取資料表、檢視、使用者定義函數、同義資料表或查詢，然後按下 DELETE，或是在物件上按一下滑鼠右鍵，然後在出現的對話方塊中選擇 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="1300b-107">In the **Diagram Pane**, select the table, view, user-defined function, synonym, or query, and then press DELETE, or right-click the object and then choose **Remove** in the resulting dialog box.</span></span> <span data-ttu-id="1300b-108">您可以一次選取並移除多個物件。</span><span class="sxs-lookup"><span data-stu-id="1300b-108">You can select and remove multiple objects at one time.</span></span>  
  
     <span data-ttu-id="1300b-109">-或-</span><span class="sxs-lookup"><span data-stu-id="1300b-109">-or-</span></span>  
  
-   <span data-ttu-id="1300b-110">在 [SQL]  窗格中移除物件的所有參考。</span><span class="sxs-lookup"><span data-stu-id="1300b-110">Remove all references to the object in the **SQL Pane.**</span></span>  
  
 <span data-ttu-id="1300b-111">當您移除資料表或資料表值物件時，查詢和檢視表設計工具會自動移除涉及資料表或資料表值物件的聯結，並且移除與 [SQL]  窗格及 [條件]  窗格中物件資料行的參考。</span><span class="sxs-lookup"><span data-stu-id="1300b-111">When you remove a table or table-valued object, the Query and View Designer automatically removes joins that involve that table or table-valued object and removes references to the object's columns in the **SQL Pane** and **Criteria Pane**.</span></span> <span data-ttu-id="1300b-112">但是，如果查詢包含牽涉到物件的複雜運算式，除非此物件的所有參考已經移除，否則物件將不會自動移除。</span><span class="sxs-lookup"><span data-stu-id="1300b-112">However, if the query contains complex expressions involving the object, the object is not automatically removed until all references to it are removed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1300b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1300b-113">See Also</span></span>  
 <span data-ttu-id="1300b-114">[將資料表加入至查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1300b-114">[Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="1300b-115">[&#40;Visual Database Tools 建立資料表別名&#41;](create-table-aliases-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1300b-115">[Create Table Aliases &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) </span></span>  
 <span data-ttu-id="1300b-116">[&#40;Visual Database Tools 指定搜尋準則&#41;](specify-search-criteria-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1300b-116">[Specify Search Criteria &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md) </span></span>  
 <span data-ttu-id="1300b-117">[&#40;Visual Database Tools&#41;匯總查詢結果](summarize-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1300b-117">[Summarize Query Results &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="1300b-118">使用查詢執行基本作業 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="1300b-118">Perform Basic Operations with Queries &#40;Visual Database Tools&#41;</span></span>](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
