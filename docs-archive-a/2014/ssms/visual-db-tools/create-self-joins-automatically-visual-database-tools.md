---
title: 自動建立自我聯結 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a428a44d33b5990e849772b43841df472ca7f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584943"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a><span data-ttu-id="5c02d-102">自動建立自我聯結 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5c02d-102">Create Self-Joins Automatically (Visual Database Tools)</span></span>
  <span data-ttu-id="5c02d-103">如果資料表具有資料庫中的自反關聯性 (Reflexive relationship)，就可讓它自動聯結至它本身。</span><span class="sxs-lookup"><span data-stu-id="5c02d-103">If a table has a reflexive relationship in the database, you can join it to itself automatically.</span></span>  
  
### <a name="to-create-a-self-join-automatically"></a><span data-ttu-id="5c02d-104">若要自動建立自我聯結</span><span class="sxs-lookup"><span data-stu-id="5c02d-104">To create a self-join automatically</span></span>  
  
1.  <span data-ttu-id="5c02d-105">將要使用的資料表新增至 [圖表窗格](visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="5c02d-105">Add to the [Diagram pane](visual-database-tools.md) the table you want to work with.</span></span>  
  
2.  <span data-ttu-id="5c02d-106">再加入同一資料表，使 [圖表] 窗格顯示兩次相同的資料表。</span><span class="sxs-lookup"><span data-stu-id="5c02d-106">Add the same table again, so that the Diagram pane shows the same table twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="5c02d-107">[查詢和檢視表設計工具](query-and-view-designer-tools-visual-database-tools.md) 藉由在資料表名稱新增連續編號，來指派第二個執行個體的別名。</span><span class="sxs-lookup"><span data-stu-id="5c02d-107">The [Query and View Designer](query-and-view-designer-tools-visual-database-tools.md) assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="5c02d-108">此外，查詢和檢視設計師會在代表這兩個以不同方式加入查詢的資料表之兩個矩形間建立聯結線。</span><span class="sxs-lookup"><span data-stu-id="5c02d-108">In addition, the Query and View Designer creates a join line between the two rectangles representing the two different ways the table participates in the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c02d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c02d-109">See Also</span></span>  
 [<span data-ttu-id="5c02d-110">使用聯結查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5c02d-110">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
