---
title: 使用未命名的參數來建立查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ea53afd1fa4d44390f5805d6b28494428608b90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584944"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a><span data-ttu-id="63903-102">使用未命名的參數建立查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="63903-102">Create Queries with Unnamed Parameters (Visual Database Tools)</span></span>
  <span data-ttu-id="63903-103">您可以指定問號 (?) 做為常值的替代符號 (Placeholder)，以未命名的參數建立查詢。</span><span class="sxs-lookup"><span data-stu-id="63903-103">You can create a query with an unnamed parameter by specifying a question mark (?) as a placeholder for a literal value.</span></span> <span data-ttu-id="63903-104">查詢和檢視設計工具會為參數指定暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="63903-104">Query and View Designer will give it a temporary name.</span></span> <span data-ttu-id="63903-105">必要時，您可以在查詢中指定多個未命名參數。</span><span class="sxs-lookup"><span data-stu-id="63903-105">You can specify as many unnamed parameters in the query as you need.</span></span>  
  
 <span data-ttu-id="63903-106">當您在查詢和檢視設計工具中執行查詢時，[查詢參數] 對話方塊會顯示出暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="63903-106">When you run the query in the Query and View Designer, the Query Parameters Dialog Box is displayed with the temporary name.</span></span>  
  
### <a name="to-specify-an-unnamed-parameter"></a><span data-ttu-id="63903-107">若要指定未命名參數</span><span class="sxs-lookup"><span data-stu-id="63903-107">To specify an unnamed parameter</span></span>  
  
1.  <span data-ttu-id="63903-108">在 [[準則窗格]](visual-database-tools.md)中，新增您要搜尋的資料行或運算式。</span><span class="sxs-lookup"><span data-stu-id="63903-108">Add the columns or expressions that you want to search to the [Criteria pane](visual-database-tools.md).</span></span> <span data-ttu-id="63903-109">如果不想讓搜尋資料行或運算式出現在查詢輸出中，請將它們從輸出資料行移除。</span><span class="sxs-lookup"><span data-stu-id="63903-109">If you do not want the search columns or expressions to appear in the query output, remove them as output columns.</span></span>  
  
2.  <span data-ttu-id="63903-110">尋找內含您要搜尋之資料行或運算式的資料列，然後在 [篩選]  格線欄中輸入問號 (?)。</span><span class="sxs-lookup"><span data-stu-id="63903-110">Locate the row containing the data column or expression to search, and then in the **Filter** grid column, enter a question mark (?).</span></span>  
  
     <span data-ttu-id="63903-111">依照預設，查詢和檢視設計工具會加入 "=" 運算子。</span><span class="sxs-lookup"><span data-stu-id="63903-111">By default, the Query and View Designer adds the "=" operator.</span></span> <span data-ttu-id="63903-112">不過，您可以編輯資料格，以替代 ">"、"<" 或其他 SQL 比較運算子。</span><span class="sxs-lookup"><span data-stu-id="63903-112">However, you can edit the cell to substitute ">", "<", or any other SQL comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63903-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63903-113">See Also</span></span>  
 [<span data-ttu-id="63903-114">使用參數查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="63903-114">Query with Parameters &#40;Visual Database Tools&#41;</span></span>](query-with-parameters-visual-database-tools.md)  
  
  
