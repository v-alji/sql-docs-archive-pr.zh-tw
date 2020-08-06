---
title: 使用資料表以外的專案建立查詢 (Visual Database Tools) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- user-defined functions [SQL Server], queries
- queries [SQL Server], creating
ms.assetid: 8e4a1f0a-8a42-4733-be8d-e21d6dbddb33
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0444c20fe10080949930f23623d5699f7fd3712c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584946"
---
# <a name="create-queries-using-something-besides-a-table-visual-database-tools"></a><span data-ttu-id="1936f-102">使用資料表以外的項目建立查詢 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1936f-102">Create Queries using Something Besides a Table (Visual Database Tools)</span></span>
  <span data-ttu-id="1936f-103">當您編寫擷取查詢時，應該明白指出您要的資料行、您要的資料列和查詢處理器尋找原始資料的位置。</span><span class="sxs-lookup"><span data-stu-id="1936f-103">Whenever you write a retrieval query, you articulate what columns you want, what rows you want, and where the query processor should find the original data.</span></span> <span data-ttu-id="1936f-104">通常其原始資料是由某資料表組成或由數個資料表聯結在一起。</span><span class="sxs-lookup"><span data-stu-id="1936f-104">Typically, this original data consists of a table or several tables joined together.</span></span> <span data-ttu-id="1936f-105">但原始資料可能源自資料表以外的來源。</span><span class="sxs-lookup"><span data-stu-id="1936f-105">But the original data can come from sources other than tables.</span></span> <span data-ttu-id="1936f-106">其實，原始資料可以來自檢視、查詢、同義資料表或傳回資料表的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1936f-106">In fact, it can come from views, queries, synonyms, or user-defined functions that return a table.</span></span>  
  
## <a name="using-a-view-in-place-of-a-table"></a><span data-ttu-id="1936f-107">使用檢視取代資料表</span><span class="sxs-lookup"><span data-stu-id="1936f-107">Using a View in Place of a Table</span></span>  
 <span data-ttu-id="1936f-108">您可以選取檢視的資料列。</span><span class="sxs-lookup"><span data-stu-id="1936f-108">You can select rows from a view.</span></span> <span data-ttu-id="1936f-109">例如，假設資料庫中含有名為「ExpensiveBooks」的檢視，其中每個資料列將說明價錢超過 19.99 的書名。</span><span class="sxs-lookup"><span data-stu-id="1936f-109">For example, suppose the database includes a view called "ExpensiveBooks," in which each row describes a title whose price exceeds 19.99.</span></span> <span data-ttu-id="1936f-110">其檢視定義將如下所示：</span><span class="sxs-lookup"><span data-stu-id="1936f-110">The view definition might look like this:</span></span>  
  
```  
SELECT *  
FROM titles  
WHERE price > 19.99  
  
```  
  
 <span data-ttu-id="1936f-111">只要選取 [ExpensiveBooks] 檢視中的心理書籍，您就可以選取昂貴的心理書籍。</span><span class="sxs-lookup"><span data-stu-id="1936f-111">You can select the expensive psychology books merely by selecting the psychology books from the ExpensiveBooks view.</span></span> <span data-ttu-id="1936f-112">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="1936f-112">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM ExpensiveBooks  
WHERE type = 'psychology'  
  
```  
  
 <span data-ttu-id="1936f-113">同樣的，JOIN 作業中也可以使用檢視。</span><span class="sxs-lookup"><span data-stu-id="1936f-113">Similarly, a view can participate in a JOIN operation.</span></span> <span data-ttu-id="1936f-114">例如，只要將銷售資料表聯結至 [ExpensiveBooks] 檢視，您就可以尋找昂貴書籍的銷售量。</span><span class="sxs-lookup"><span data-stu-id="1936f-114">For example, you can find the sales of expensive books merely by joining the sales table to the ExpensiveBooks view.</span></span> <span data-ttu-id="1936f-115">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="1936f-115">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *  
FROM sales   
         INNER JOIN   
         ExpensiveBooks   
         ON sales.title_id   
         =  ExpensiveBooks.title_id  
  
```  
  
 <span data-ttu-id="1936f-116">如需新增檢視至查詢的詳細資訊，請參閱[將資料表新增至查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1936f-116">For more information about adding a view to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-query-in-place-of-a-table"></a><span data-ttu-id="1936f-117">使用查詢取代資料表</span><span class="sxs-lookup"><span data-stu-id="1936f-117">Using a Query in Place of a Table</span></span>  
 <span data-ttu-id="1936f-118">您可以選取查詢中的資料列。</span><span class="sxs-lookup"><span data-stu-id="1936f-118">You can select rows from a query.</span></span> <span data-ttu-id="1936f-119">例如，假設您已撰寫某查詢來擷取合著書籍 (具有一位以上作者的書籍) 的書名和識別碼。</span><span class="sxs-lookup"><span data-stu-id="1936f-119">For example, suppose you have already written a query retrieving titles and identifiers of the coauthored books - the books with more than one author.</span></span> <span data-ttu-id="1936f-120">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="1936f-120">The SQL might look like this:</span></span>  
  
```  
SELECT   
     titles.title_id, title, type  
FROM   
     titleauthor   
         INNER JOIN  
         titles   
         ON titleauthor.title_id   
         =  titles.title_id   
GROUP BY   
     titles.title_id, title, type  
HAVING COUNT(*) > 1  
  
```  
  
 <span data-ttu-id="1936f-121">您可以再編寫其他查詢來建置該結果。</span><span class="sxs-lookup"><span data-stu-id="1936f-121">You can then write another query that builds on this result.</span></span> <span data-ttu-id="1936f-122">例如，您可以編寫擷取由多位作者合著的心理書籍之查詢。</span><span class="sxs-lookup"><span data-stu-id="1936f-122">For example, you can write a query that retrieves the coauthored psychology books.</span></span> <span data-ttu-id="1936f-123">若要編寫此新查詢，您可以使用現有查詢做為新查詢資料的來源。</span><span class="sxs-lookup"><span data-stu-id="1936f-123">To write this new query, you can use the existing query as the source of the new query's data.</span></span> <span data-ttu-id="1936f-124">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="1936f-124">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    title  
FROM   
    (  
    SELECT   
        titles.title_id,   
        title,   
        type  
    FROM   
        titleauthor   
            INNER JOIN  
            titles   
            ON titleauthor.title_id   
            =  titles.title_id   
    GROUP BY   
        titles.title_id,   
        title,   
        type  
    HAVING COUNT(*) > 1  
    )   
    co_authored_books  
WHERE     type = 'psychology'  
  
```  
  
 <span data-ttu-id="1936f-125">加強顯示的文字表示做為新查詢資料來源的現有查詢。</span><span class="sxs-lookup"><span data-stu-id="1936f-125">The emphasized text shows the existing query used as the source of the new query's data.</span></span> <span data-ttu-id="1936f-126">請注意新的查詢使用別名 (「co_authored_books」) 來稱呼現有查詢。</span><span class="sxs-lookup"><span data-stu-id="1936f-126">Note that the new query uses an alias ("co_authored_books") for the existing query.</span></span> <span data-ttu-id="1936f-127">如需別名的詳細資訊，請參閱[建立資料表別名 &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) 和[建立資料行別名 &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1936f-127">For more information about aliases, see [Create Table Aliases &#40;Visual Database Tools&#41;](create-table-aliases-visual-database-tools.md) and [Create Column Aliases &#40;Visual Database Tools&#41;](create-column-aliases-visual-database-tools.md).</span></span>  
  
 <span data-ttu-id="1936f-128">同樣的，JOIN 作業中可使用查詢。</span><span class="sxs-lookup"><span data-stu-id="1936f-128">Similarly, a query can participate in a JOIN operation.</span></span> <span data-ttu-id="1936f-129">例如，只要將 [ExpensiveBooks] 檢視聯結至擷取由多位作者合著的書籍的查詢，您便可以尋找昂貴的合著書籍之銷售。</span><span class="sxs-lookup"><span data-stu-id="1936f-129">For example, you can find the sales of expensive coauthored books merely by joining the ExpensiveBooks view to the query retrieving the coauthored books.</span></span> <span data-ttu-id="1936f-130">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="1936f-130">The resulting SQL might look like this:</span></span>  
  
```  
SELECT   
    ExpensiveBooks.title  
FROM   
    ExpensiveBooks   
        INNER JOIN  
        (  
        SELECT   
            titles.title_id,   
            title,   
            type  
        FROM   
            titleauthor   
                INNER JOIN  
                titles   
                ON titleauthor.title_id   
                =  titles.title_id   
        GROUP BY   
            titles.title_id,   
            title,   
            type  
        HAVING COUNT(*) > 1  
        )  
```  
  
 <span data-ttu-id="1936f-131">如需新增查詢至查詢的詳細資訊，請參閱[將資料表新增至查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1936f-131">For more information about adding a query to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="using-a-user-defined-function-in-place-of-a-table"></a><span data-ttu-id="1936f-132">使用使用者定義函數取代資料表</span><span class="sxs-lookup"><span data-stu-id="1936f-132">Using a User-Defined Function in Place of a Table</span></span>  
 <span data-ttu-id="1936f-133">在 SQL Server 2000 (含) 以上版本中，您可以建立可傳回資料表的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1936f-133">In SQL Server 2000 or higher, you can create a user-defined function that returns a table.</span></span> <span data-ttu-id="1936f-134">執行複雜或程序邏輯時，這類函數便非常有用。</span><span class="sxs-lookup"><span data-stu-id="1936f-134">Such functions are useful for performing complex or procedural logic.</span></span>  
  
 <span data-ttu-id="1936f-135">例如，假設員工資料表含有額外的資料行 employee.manager_emp_id，而且外部索引鍵存在於 manager_emp_id 到 employee.emp_id 之間。</span><span class="sxs-lookup"><span data-stu-id="1936f-135">For example, suppose the employee table contains an additional column, employee.manager_emp_id, and that a foreign key exists from manager_emp_id to employee.emp_id.</span></span> <span data-ttu-id="1936f-136">在員工資料表的每個資料列中，manager_emp_id 資料行將指出員工的上司。</span><span class="sxs-lookup"><span data-stu-id="1936f-136">Within each row of the employee table, the manager_emp_id column indicates the employee's boss.</span></span> <span data-ttu-id="1936f-137">更明確地說，它會指出員工上司的 emp_id。</span><span class="sxs-lookup"><span data-stu-id="1936f-137">More precisely, it indicates the employee's boss's emp_id.</span></span> <span data-ttu-id="1936f-138">您可以建立傳回資料表的使用者定義函數，其中該資料表將包含一資料列列出在特定職等管理人員的組織結構中工作的員工。</span><span class="sxs-lookup"><span data-stu-id="1936f-138">You can create a user-defined function that returns a table containing one row for each employee working within a particular high-level manager's organizational hierarchy.</span></span> <span data-ttu-id="1936f-139">您可以呼叫 fn_GetWholeTeam 函式，並設計該函式採用輸入變數，即管理人員 (您想要擷取該管理人員所屬小組) 的 emp_id。</span><span class="sxs-lookup"><span data-stu-id="1936f-139">You might call the function fn_GetWholeTeam, and design it to take an input variable - the emp_id of the manager whose team you want to retrieve.</span></span>  
  
 <span data-ttu-id="1936f-140">您可以編寫使用 fn_GetWholeTeam 函數做為資料來源的查詢。</span><span class="sxs-lookup"><span data-stu-id="1936f-140">You can write a query that uses the fn_GetWholeTeam function as a source of data.</span></span> <span data-ttu-id="1936f-141">產生的 SQL 將如下所示：</span><span class="sxs-lookup"><span data-stu-id="1936f-141">The resulting SQL might look like this:</span></span>  
  
```  
SELECT *   
FROM   
     fn_GetWholeTeam ('VPA30890F')  
  
```  
  
 <span data-ttu-id="1936f-142">"VPA30890F" 是管理人員的 emp_id，您將擷取該管理人員的組織。</span><span class="sxs-lookup"><span data-stu-id="1936f-142">"VPA30890F" is the emp_id of the manager whose organization you want to retrieve.</span></span> <span data-ttu-id="1936f-143">如需新增使用者定義函數至查詢的詳細資訊，請參閱[將資料表新增至查詢 &#40;Visual Database Tools&#41;](visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1936f-143">For more information about adding a user-defined function to a query, see [Add Tables to Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span> <span data-ttu-id="1936f-144">如需使用者定義函數的完整描述，請參閱 [使用者定義函數](../../relational-databases/user-defined-functions/user-defined-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="1936f-144">For a complete description of user-defined functions, see [User-Defined Functions](../../relational-databases/user-defined-functions/user-defined-functions.md).</span></span>  
  
  
