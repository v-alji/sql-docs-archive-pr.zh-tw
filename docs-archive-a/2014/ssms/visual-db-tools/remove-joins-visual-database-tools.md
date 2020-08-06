---
title: 移除聯結 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: stevestein
ms.author: sstein
ms.openlocfilehash: b037e317b629671f6ec5ea1fa90edfca6fafa627
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584221"
---
# <a name="remove-joins-visual-database-tools"></a><span data-ttu-id="9e9f7-102">移除聯結 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="9e9f7-102">Remove Joins (Visual Database Tools)</span></span>
  <span data-ttu-id="9e9f7-103">如果不要使用內部聯結或外部聯結來聯結資料表，則可以移除其間的聯結。</span><span class="sxs-lookup"><span data-stu-id="9e9f7-103">If you do not want tables to be joined via an inner join or an outer join, you can remove the join between them.</span></span> <span data-ttu-id="9e9f7-104">例如，您可以移除 [查詢和檢視設計工具](visual-database-tools.md) 自動在兩個資料表間建立的聯結。</span><span class="sxs-lookup"><span data-stu-id="9e9f7-104">For example, you might remove a join that the [Query and View Designer](visual-database-tools.md) has been created automatically between two tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e9f7-105">移除查詢中的聯結，並不會改變資料庫的基礎關聯性。</span><span class="sxs-lookup"><span data-stu-id="9e9f7-105">Removing a join from a query does not alter the underlying relationship in the database.</span></span>  
  
 <span data-ttu-id="9e9f7-106">如果兩個聯結的資料表是查詢的一部份，並且移除其間的所有聯結條件，則產生的查詢會成為兩個資料表相乘，亦即成為 CROSS JOIN。</span><span class="sxs-lookup"><span data-stu-id="9e9f7-106">If two joined tables are part of your query and you remove all join conditions between them, the resulting query becomes the product of both tables - that is, it becomes a CROSS JOIN.</span></span>  
  
### <a name="to-remove-a-join"></a><span data-ttu-id="9e9f7-107">若要移除聯結</span><span class="sxs-lookup"><span data-stu-id="9e9f7-107">To remove a join</span></span>  
  
-   <span data-ttu-id="9e9f7-108">在 [圖表窗格](diagram-pane-visual-database-tools.md)中，選取要移除之聯結的聯結線，然後按 DELETE 鍵。</span><span class="sxs-lookup"><span data-stu-id="9e9f7-108">In the [Diagram pane](diagram-pane-visual-database-tools.md), select the join line for the join to remove, and then press the DELETE key.</span></span> <span data-ttu-id="9e9f7-109">可以一次選取和刪除多重聯結線。</span><span class="sxs-lookup"><span data-stu-id="9e9f7-109">You can select and delete multiple join lines at one time.</span></span>  
  
 <span data-ttu-id="9e9f7-110">查詢和檢視設計工具會移除聯結線，並隨即變更 [SQL 窗格](sql-pane-visual-database-tools.md)中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="9e9f7-110">The Query and View Designer removes the join line and alters the statement in the [SQL pane](sql-pane-visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e9f7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e9f7-111">See Also</span></span>  
 <span data-ttu-id="9e9f7-112">[自動聯結資料表 &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9e9f7-112">[Join Tables Automatically &#40;Visual Database Tools&#41;](join-tables-automatically-visual-database-tools.md) </span></span>  
 <span data-ttu-id="9e9f7-113">[手動聯結資料表 &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="9e9f7-113">[Join Tables Manually &#40;Visual Database Tools&#41;](join-tables-manually-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="9e9f7-114">使用聯結查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9f7-114">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
