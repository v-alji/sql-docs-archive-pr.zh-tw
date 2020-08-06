---
title: 繪製自反關聯性 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e5056b1a5d0d884edbc4fc818fe8c7ef5cc8ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597497"
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a><span data-ttu-id="7a0ed-102">繪製自反關聯性 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7a0ed-102">Draw Reflexive Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="7a0ed-103">您可建立自反關聯性 (Reflexive Relationship)，將資料表中的一或多個資料行與相同資料表中的其他資料行連結。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-103">You create a reflexive relationship to link a column or columns in a table with another column or columns in the same table.</span></span> <span data-ttu-id="7a0ed-104">例如，假設 `employee` 資料表包含 `emp_id` 資料行和 `mgr_id` 資料行。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-104">For example, suppose the `employee` table has an `emp_id` column and a `mgr_id` column.</span></span> <span data-ttu-id="7a0ed-105">由於每位經理同時兼具員工的身分，您可繪製一條從資料表至其本身的關聯線，將這兩個資料行相關聯。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-105">Because each manager is also an employee, you relate these two columns by drawing a relationship line from the table to itself.</span></span> <span data-ttu-id="7a0ed-106">此關聯性可確保每個加入資料表的經理識別碼，都與現有員工識別碼相符。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-106">This relationship ensures each manager ID that is added to the table matches an existing employee ID.</span></span>  
  
 <span data-ttu-id="7a0ed-107">在建立關聯性之前，必須先為您的資料表定義主索引鍵或唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-107">Before you create a relationship, you must first define a primary key or unique constraint for your table.</span></span> <span data-ttu-id="7a0ed-108">然後，將主索引鍵資料行關聯至相符的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-108">You then relate the primary key column to a matching column.</span></span> <span data-ttu-id="7a0ed-109">建立關聯性之後，相符的資料行會成為資料表的外部索引鍵。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-109">Once you create the relationship, the matching column becomes a foreign key of the table.</span></span>  
  
### <a name="to-draw-a-reflexive-relationship"></a><span data-ttu-id="7a0ed-110">若要繪製自反關聯性</span><span class="sxs-lookup"><span data-stu-id="7a0ed-110">To draw a reflexive relationship</span></span>  
  
1.  <span data-ttu-id="7a0ed-111">在資料庫圖表中，在要關聯至其他資料行的資料庫資料行上按一下資料列選取器，並將指標拖曳至資料表外部，直到線條顯示為止。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-111">In your database diagram, click the row selector for the database column that you want to relate to another column and drag the pointer outside the table until a line appears.</span></span>  
  
2.  <span data-ttu-id="7a0ed-112">將線條拖曳回選取的資料表。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-112">Drag the line back to the selected table.</span></span>  
  
3.  <span data-ttu-id="7a0ed-113">放開滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-113">Release the mouse button.</span></span> <span data-ttu-id="7a0ed-114">隨即出現 [資料表和資料行]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-114">The **Tables and Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="7a0ed-115">選取要用來形成關聯性的外部索引鍵資料行及主索引鍵資料表與資料行。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-115">Select the foreign key column and the primary key table and column with which you want form a relationship.</span></span>  
  
5.  <span data-ttu-id="7a0ed-116">選擇兩次 [確定]  以建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-116">Choose **OK** twice to create the relationship.</span></span>  
  
 <span data-ttu-id="7a0ed-117">當您對資料表執行查詢時，可使用自反關聯性來建立自我聯結 (Self-Join)。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-117">When you run queries against a table, you can use a reflexive relationship to create a self-join.</span></span> <span data-ttu-id="7a0ed-118">如需使用聯結查詢資料表的相關資訊，請參閱 [使用聯結查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="7a0ed-118">For information about querying tables with joins, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0ed-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a0ed-119">See Also</span></span>  
 [<span data-ttu-id="7a0ed-120">使用聯結查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="7a0ed-120">Query with Joins &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
