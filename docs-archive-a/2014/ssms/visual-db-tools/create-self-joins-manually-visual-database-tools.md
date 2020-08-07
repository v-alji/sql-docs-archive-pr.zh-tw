---
title: 手動建立自我聯結 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- self-joins
- manual joins [SQL Server]
- joins [SQL Server], self
ms.assetid: 910ed516-cb84-481b-95d0-cba3e89afdba
author: stevestein
ms.author: sstein
ms.openlocfilehash: 31e125fdfe0f7f285ea679cfe85356d1aa10353a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596996"
---
# <a name="create-self-joins-manually-visual-database-tools"></a><span data-ttu-id="ca565-102">手動建立自我聯結 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="ca565-102">Create Self-Joins Manually (Visual Database Tools)</span></span>
  <span data-ttu-id="ca565-103">即使資料表沒有資料庫中的自反關聯性，也可以將資料表聯結至它本身。</span><span class="sxs-lookup"><span data-stu-id="ca565-103">You can join a table to itself even if the table does not have a reflexive relationship in the database.</span></span> <span data-ttu-id="ca565-104">例如，可以使用自我聯結 (Self-Join) 來找出住在同一城市的作者。</span><span class="sxs-lookup"><span data-stu-id="ca565-104">For example, you can use a self-join to find pairs of authors living in the same city.</span></span>  
  
 <span data-ttu-id="ca565-105">如同任何聯結一樣，自我聯結至少需要兩個資料表。</span><span class="sxs-lookup"><span data-stu-id="ca565-105">As with any join, a self-join requires at least two tables.</span></span> <span data-ttu-id="ca565-106">其差異在於並未將第二個資料表加入查詢中，而是加入同一資料表的第二個執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca565-106">The difference is that, instead of adding a second table to the query, you add a second instance of the same table.</span></span> <span data-ttu-id="ca565-107">如此就可以比較資料表第一個執行個體的資料行，與第二個執行個體中的同一資料行，以便讓您比較資料行中的各值。</span><span class="sxs-lookup"><span data-stu-id="ca565-107">That way, you can compare a column in the first instance of the table to the same column in the second instance, which allows you to compare the values in a column to each other.</span></span> <span data-ttu-id="ca565-108">[查詢和檢視表設計工具](visual-database-tools.md) 會指派別名給資料表的第二個執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca565-108">The [Query and View Designer](visual-database-tools.md) assigns an alias to the second instance of the table.</span></span>  
  
 <span data-ttu-id="ca565-109">例如，若要建立自我聯結以找出住在 Berkeley 的所有作者對，您可以比較資料表第一個執行個體中的 `city` 資料行與第二個執行個體中的 `city` 資料行。</span><span class="sxs-lookup"><span data-stu-id="ca565-109">For example, if you are creating a self-join to find all pairs of authors within Berkeley, you compare the `city` column in the first instance of the table against the `city` column in the second instance.</span></span> <span data-ttu-id="ca565-110">產生的查詢可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="ca565-110">The resulting query might look like the following:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="ca565-111">建立自我聯結通常需要多重聯結條件。</span><span class="sxs-lookup"><span data-stu-id="ca565-111">Creating a self-join often requires multiple join conditions.</span></span> <span data-ttu-id="ca565-112">若要暸解其原因，請考量先前查詢的結果：</span><span class="sxs-lookup"><span data-stu-id="ca565-112">To understand why, consider the result of the preceding query:</span></span>  
  
```  
Cheryl Carson       Cheryl Carson  
Abraham Bennet      Abraham Bennet  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="ca565-113">第一個資料列毫無用處，其中指出 Cheryl Carson 與 Cheryl Carson 住在同一城市。</span><span class="sxs-lookup"><span data-stu-id="ca565-113">The first row is useless; it indicates that Cheryl Carson lives in the same city as Cheryl Carson.</span></span> <span data-ttu-id="ca565-114">第二個資料列也毫無用處。</span><span class="sxs-lookup"><span data-stu-id="ca565-114">The second row is equally useless.</span></span> <span data-ttu-id="ca565-115">若要消除這些無用的資料，可以加入另一個條件，使其只保留作者姓名不同的結果資料列。</span><span class="sxs-lookup"><span data-stu-id="ca565-115">To eliminate this useless data, you add another condition retaining only those result rows in which the two author names describe different authors.</span></span> <span data-ttu-id="ca565-116">產生的查詢可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="ca565-116">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             <> authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="ca565-117">結果集則改善為：</span><span class="sxs-lookup"><span data-stu-id="ca565-117">The result set is improved:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
Abraham Bennet      Cheryl Carson  
```  
  
 <span data-ttu-id="ca565-118">但這兩個資料列互為冗餘。</span><span class="sxs-lookup"><span data-stu-id="ca565-118">But the two result rows are redundant.</span></span> <span data-ttu-id="ca565-119">第一個資料列說明 Carson 與 Bennet 住在同一城市，第二個資料列則說明 Bennet 與 Carson 住在同一城市。</span><span class="sxs-lookup"><span data-stu-id="ca565-119">The first says Carson lives in the same city as Bennet, and the second says the Bennet lives in the same city as Carson.</span></span> <span data-ttu-id="ca565-120">若要消除這種冗餘，可以將第二個聯結條件由 "not equals"變更為 " less than"。</span><span class="sxs-lookup"><span data-stu-id="ca565-120">To eliminate this redundancy, you can alter the second join condition from "not equals" to "less than."</span></span> <span data-ttu-id="ca565-121">產生的查詢可能如下所示：</span><span class="sxs-lookup"><span data-stu-id="ca565-121">The resulting query might look like this:</span></span>  
  
```  
SELECT   
      authors.au_fname,   
      authors.au_lname,   
      authors1.au_fname AS Expr2,   
      authors1.au_lname AS Expr3  
   FROM   
      authors   
         INNER JOIN  
         authors authors1   
            ON authors.city   
             = authors1.city  
            AND authors.au_id  
             < authors1.au_id  
   WHERE  
      authors.city = 'Berkeley'  
```  
  
 <span data-ttu-id="ca565-122">結果集則如下所示：</span><span class="sxs-lookup"><span data-stu-id="ca565-122">And the result set looks like this:</span></span>  
  
```  
Cheryl Carson       Abraham Bennet  
```  
  
### <a name="to-create-a-self-join-manually"></a><span data-ttu-id="ca565-123">手動建立自我聯結</span><span class="sxs-lookup"><span data-stu-id="ca565-123">To create a self-join manually</span></span>  
  
1.  <span data-ttu-id="ca565-124">將要使用的資料表或資料表值物件新增至 [圖表窗格](diagram-pane-visual-database-tools.md) 中。</span><span class="sxs-lookup"><span data-stu-id="ca565-124">Add to the [Diagram pane](diagram-pane-visual-database-tools.md) the table or table-valued object you want to work with.</span></span>  
  
2.  <span data-ttu-id="ca565-125">再加入同一資料表，使 [圖表] 窗格顯示兩次相同的資料表或資料表值物件。</span><span class="sxs-lookup"><span data-stu-id="ca565-125">Add the same table again, so that the Diagram pane shows the same table or table-valued object twice within the Diagram pane.</span></span>  
  
     <span data-ttu-id="ca565-126">查詢和檢視設計師藉由在資料表名稱加入連續編號，來指派第二個執行個體的別名。</span><span class="sxs-lookup"><span data-stu-id="ca565-126">The Query and View Designer assigns an alias to the second instance by adding a sequential number to the table name.</span></span> <span data-ttu-id="ca565-127">此外，[查詢和檢視設計師] 會在 [圖表] 窗格的兩個資料表或資料表值物件之間建立聯結線。</span><span class="sxs-lookup"><span data-stu-id="ca565-127">In addition, the Query and View Designer creates a join line between the two occurrences of the table or table-valued object within the Diagram pane.</span></span>  
  
3.  <span data-ttu-id="ca565-128">在聯結線上按一下滑鼠右鍵，然後在捷徑功能表中選擇 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="ca565-128">Right-click the join line and choose **Properties** from the shortcut menu.</span></span>  
  
4.  <span data-ttu-id="ca565-129">在 [屬性] 視窗中，按一下 [聯結條件及類型]  ，再按一下屬性右邊的省略符號 ([...]  )。</span><span class="sxs-lookup"><span data-stu-id="ca565-129">In the Properties window click **Join Condition and Type** and click the **ellipses (...)** to the right of the property.</span></span>  
  
5.  <span data-ttu-id="ca565-130">在[聯結對話方塊](join-dialog-box-visual-database-tools.md)中，在必要時變更主索引鍵之間的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="ca565-130">In the [Join Dialog Box](join-dialog-box-visual-database-tools.md) change the comparison operator between the primary keys as required.</span></span> <span data-ttu-id="ca565-131">例如，您可以會將運算子變更為小於 (<)。</span><span class="sxs-lookup"><span data-stu-id="ca565-131">For example, you might change the operator to less than (<).</span></span>  
  
6.  <span data-ttu-id="ca565-132">將資料表或資料表值物件的第一個執行個體的主聯結 (Primary Join) 資料行名稱，拖放至第二個執行個體的對應資料行，即可建立其他聯結條件 (例如，authors.zip = authors1.zip)。</span><span class="sxs-lookup"><span data-stu-id="ca565-132">Create the additional join condition (for example, authors.zip = authors1.zip) by dragging the name of the primary join column in the first occurrence of the table or table-valued object and dropping it on the corresponding column in the second occurrence.</span></span>  
  
7.  <span data-ttu-id="ca565-133">指定查詢的其他選項，例如輸出資料行、搜尋條件和排序順序。</span><span class="sxs-lookup"><span data-stu-id="ca565-133">Specify other options for the query such as output columns, search conditions, and sort order.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca565-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca565-134">See Also</span></span>  
 <span data-ttu-id="ca565-135">[&#40;Visual Database Tools 自動建立自我聯結&#41;](create-self-joins-automatically-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="ca565-135">[Create Self-Joins Automatically &#40;Visual Database Tools&#41;](create-self-joins-automatically-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="ca565-136">使用聯結查詢 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="ca565-136">Query with Joins &#40;Visual Database Tools&#41;</span></span>](query-with-joins-visual-database-tools.md)  
  
  
