---
title: 排序資料列 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- sorting rows [SQL Server]
- sorting query results [SQL Server]
ms.assetid: 780ef467-f96e-4373-8235-6dacbedb05a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4939c08a4be8c6a7aa3a52d55928abe077f25d76
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705821"
---
# <a name="sort-rows-visual-database-tools"></a><span data-ttu-id="a0178-102">排序資料列 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="a0178-102">Sort Rows (Visual Database Tools)</span></span>
  <span data-ttu-id="a0178-103">您可以排列查詢結果中的資料列。</span><span class="sxs-lookup"><span data-stu-id="a0178-103">You can order the rows in a query result.</span></span> <span data-ttu-id="a0178-104">也就是說，您可以命名特定的資料行或資料行組合，其值將決定結果集中的資料列排列順序。</span><span class="sxs-lookup"><span data-stu-id="a0178-104">That is, you can name a particular column or set of columns whose values determine the order of rows in the result set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0178-105">排序次序一部份取決於資料行的定序序列。</span><span class="sxs-lookup"><span data-stu-id="a0178-105">The sort order is determined in part by the column's collation sequence.</span></span> <span data-ttu-id="a0178-106">您可以在 [定序對話方塊](visual-database-tools.md)中變更定序序列。</span><span class="sxs-lookup"><span data-stu-id="a0178-106">You can change the collation sequence in the [Collation Dialog Box](visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="a0178-107">您可以使用以下幾種方法來排序查詢結果：</span><span class="sxs-lookup"><span data-stu-id="a0178-107">There are several ways in which you can sort query results:</span></span>  
  
-   <span data-ttu-id="a0178-108">**您可以使用遞增或遞減順序來排列資料列** ：根據預設值，SQL 會使用資料行排序依據以遞增方式排列資料列。</span><span class="sxs-lookup"><span data-stu-id="a0178-108">**You can arrange rows in ascending or descending order** By default, SQL uses order-by columns to arrange rows in ascending order.</span></span> <span data-ttu-id="a0178-109">例如，若要使用遞減價格來排列書名，只要在價格資料行中排序資料列即可。</span><span class="sxs-lookup"><span data-stu-id="a0178-109">For example, to arrange the book titles by ascending price, simply sort the rows by the price column.</span></span> <span data-ttu-id="a0178-110">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0178-110">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price  
  
    ```  
  
     <span data-ttu-id="a0178-111">另一方面，若要先排列較昂貴的書籍名稱，您可以明確的指定使用先排列最貴的書籍的排列順序。</span><span class="sxs-lookup"><span data-stu-id="a0178-111">On the other hand, if you want to arrange the titles with the more expensive books first, you can explicitly specify a highest-first ordering.</span></span> <span data-ttu-id="a0178-112">也就是說，您可以指定在價格資料行使用遞減值的方式來排列結果資料列。</span><span class="sxs-lookup"><span data-stu-id="a0178-112">That is, you indicate that the result rows should be arranged by descending values of the price column.</span></span> <span data-ttu-id="a0178-113">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0178-113">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="a0178-114">**您可以依多重資料行排序** ：例如，您可以建立結果集，其中一個資料列列出所有作者，並先使用州來排序，然後再使用城市來排序。</span><span class="sxs-lookup"><span data-stu-id="a0178-114">**You can sort by multiple columns** For example, you can create a result set with one row for each author, ordering first by state and then by city.</span></span> <span data-ttu-id="a0178-115">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0178-115">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT *  
    FROM authors   
    ORDER BY state, city  
  
    ```  
  
-   <span data-ttu-id="a0178-116">**您可以依不在結果集顯示的資料行排序** ：例如，您可以建立結果集並先列出昂貴的書籍，即使該結果集中並未顯示價格。</span><span class="sxs-lookup"><span data-stu-id="a0178-116">**You can sort by columns not appearing in the result set** For example, you can create a result set with the most expensive titles first, even though the prices do not appear.</span></span> <span data-ttu-id="a0178-117">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0178-117">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title_id, title  
    FROM titles  
    ORDER BY price DESC  
  
    ```  
  
-   <span data-ttu-id="a0178-118">**您可以依衍生資料行排序**：例如，您可以建立結果集，其中每個資料列都含有書名；需付較高版稅的書將優先顯示。</span><span class="sxs-lookup"><span data-stu-id="a0178-118">**You can sort by derived columns** For example, you can create a result set in which each row contains a book title - with the books that pay the highest royalty per copy appearing first.</span></span> <span data-ttu-id="a0178-119">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0178-119">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title, price * royalty / 100 as royalty_per_unit  
    FROM titles  
    ORDER BY royalty_per_unit DESC  
  
    ```  
  
     <span data-ttu-id="a0178-120">(強調顯示的文字部份為計算每本書所賺取的版稅公式)。</span><span class="sxs-lookup"><span data-stu-id="a0178-120">(The formula for calculating the royalty that each book earns per copy is emphasized.)</span></span>  
  
     <span data-ttu-id="a0178-121">若要計算衍生的資料行，您可以如同前述的範例使用 SQL 語法，或者使用會傳回數值類值的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="a0178-121">To calculate a derived column, you can use SQL syntax, as in the preceding example, or you can use a user-defined function that returns a scalar value.</span></span> <span data-ttu-id="a0178-122">如需使用者定義函數的詳細資訊，請參閱 SQL Server 文件。</span><span class="sxs-lookup"><span data-stu-id="a0178-122">For more information about user-defined functions, see the SQL Server documentation.</span></span>  
  
-   <span data-ttu-id="a0178-123">**您可以排序群組資料列**：例如，您可以建立結果集，其中每個資料列描述某個城市，以及該城市中的作者數目；包含多位作者的城市將優先顯示。</span><span class="sxs-lookup"><span data-stu-id="a0178-123">**You can sort grouped rows** For example; you can create a result set in which each row describes a city, plus the number of authors in that city - with the cities containing many authors appearing first.</span></span> <span data-ttu-id="a0178-124">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0178-124">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    ORDER BY COUNT(*) DESC, state  
  
    ```  
  
     <span data-ttu-id="a0178-125">注意，查詢會使用 `state` 做為次要排序資料行。</span><span class="sxs-lookup"><span data-stu-id="a0178-125">Notice that the query uses `state` as a secondary sort column.</span></span> <span data-ttu-id="a0178-126">因此，如果有兩個州擁有相同數量的作者，該州將以字母順序排列。</span><span class="sxs-lookup"><span data-stu-id="a0178-126">Thus, if two states have the same number of authors, those states will appear in alphabetical order.</span></span>  
  
-   <span data-ttu-id="a0178-127">**您可以使用國際資料排序** ：也就是說，您可以使用定序慣例來排序資料行，這種定序慣例與該資料行的預設慣例不同。</span><span class="sxs-lookup"><span data-stu-id="a0178-127">**You can sort using international data** That is; you can sort a column using collating conventions that differ from the default conventions for that column.</span></span> <span data-ttu-id="a0178-128">例如，您可以撰寫查詢來 Jaime Pati？來抓取所有書名嗎？i/o.</span><span class="sxs-lookup"><span data-stu-id="a0178-128">For example, you can write a query that retrieves all the book titles by Jaime Pati??o.</span></span> <span data-ttu-id="a0178-129">若要以字母順序顯示名稱，您可以使用西班牙文定序序列來排列名稱資料行。</span><span class="sxs-lookup"><span data-stu-id="a0178-129">To display the titles in alphabetical order, you use a Spanish collating sequence for the title column.</span></span> <span data-ttu-id="a0178-130">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="a0178-130">The resulting SQL might look like this:</span></span>  
  
    ```  
    SELECT title  
    FROM   
        authors   
        INNER JOIN   
            titleauthor   
            ON authors.au_id   
            =  titleauthor.au_id   
            INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
    WHERE   
         au_fname = 'Jaime' AND   
         au_lname = 'Pati??o'  
    ORDER BY   
         title COLLATE SQL_Spanish_Pref_CP1_CI_AS  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a0178-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0178-131">See Also</span></span>  
 <span data-ttu-id="a0178-132">[排序和分組查詢結果 &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="a0178-132">[Sort and Group Query Results &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="a0178-133">設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="a0178-133">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
