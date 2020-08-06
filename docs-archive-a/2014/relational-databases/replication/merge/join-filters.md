---
title: 聯結篩選 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- publications [SQL Server replication], join filters
- merge replication join filters [SQL Server replication]
- join filters
ms.assetid: dd78fd8f-56e3-4582-9abd-6bc25c91e075
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b97e7d7b53e6a3fdb242d1272e013bbd45f0ed17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584436"
---
# <a name="join-filters"></a><span data-ttu-id="7b418-102">聯結篩選</span><span class="sxs-lookup"><span data-stu-id="7b418-102">Join Filters</span></span>
  <span data-ttu-id="7b418-103">聯結篩選可讓您根據發行集內相關資料表的篩選方式來篩選資料表。</span><span class="sxs-lookup"><span data-stu-id="7b418-103">A join filter allows a table to be filtered based on how a related table in the publication is filtered.</span></span> <span data-ttu-id="7b418-104">通常，父資料表會使用參數化篩選進行篩選，然後一或多個聯結篩選會以您在資料表之間定義聯結的相同方式進行定義。</span><span class="sxs-lookup"><span data-stu-id="7b418-104">Typically a parent table is filtered using a parameterized filter; then one or more join filters are defined in much the same way that you define a join between tables.</span></span> <span data-ttu-id="7b418-105">聯結篩選可以擴充參數化篩選，以便僅當資料與聯結篩選子句相符時，才複寫相關資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="7b418-105">The join filters extend the parameterized filter so that the data in the related tables is only replicated if it matches the join filter clause.</span></span>  
  
 <span data-ttu-id="7b418-106">聯結篩選通常會遵循為套用到之資料表所定義的主索引鍵/外部索引鍵關聯性，但並非嚴格受限於主索引鍵/外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="7b418-106">Join filters typically follow the primary key/foreign key relationships defined for the tables to which they are applied, but they are not limited strictly to primary key/foreign key relationships.</span></span> <span data-ttu-id="7b418-107">聯結篩選可基於任何比較兩資料表中相關資料的邏輯。</span><span class="sxs-lookup"><span data-stu-id="7b418-107">The join filter can be based on any logic that compares related data in two tables.</span></span>  
  
 <span data-ttu-id="7b418-108">請考慮使用 [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] 範本資料庫中的下列資料表，這些資料表透過主索引鍵到外部索引鍵的關聯性相關聯：</span><span class="sxs-lookup"><span data-stu-id="7b418-108">Consider the following tables in the [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] sample database, which are related through primary key to foreign key relationships:</span></span>  
  
-   <span data-ttu-id="7b418-109">**HumanResources.Employee**</span><span class="sxs-lookup"><span data-stu-id="7b418-109">**HumanResources.Employee**</span></span>  
  
-   <span data-ttu-id="7b418-110">**Sales.SalesOrderHeader**</span><span class="sxs-lookup"><span data-stu-id="7b418-110">**Sales.SalesOrderHeader**</span></span>  
  
-   <span data-ttu-id="7b418-111">**Sales.SalesOrderDetail**</span><span class="sxs-lookup"><span data-stu-id="7b418-111">**Sales.SalesOrderDetail**</span></span>  
  
 <span data-ttu-id="7b418-112">上述資料表可在應用程式中使用，以支援行動銷售團隊，但這些資料表必須經過篩選，以便 **HumanResources.Employee** 資料表中的每位業務員只會收到其客戶訂單的相關資料。</span><span class="sxs-lookup"><span data-stu-id="7b418-112">These tables could be used in an application to support a mobile sales force, but they must be filtered so that each sales person in the **HumanResources.Employee** table receives only the data relevant to their customers' orders.</span></span>  
  
 <span data-ttu-id="7b418-113">第一步要在父資料表中定義參數化篩選，此範例中的父資料表是 **HumanResources.Employee** 資料表。</span><span class="sxs-lookup"><span data-stu-id="7b418-113">The first step is to define a parameterized filter on the parent table, which in this example is the **HumanResources.Employee** table.</span></span> <span data-ttu-id="7b418-114">此資料表包括 **LoginID**資料行，其中含有格式為 *domain\login*的每位員工的登入。</span><span class="sxs-lookup"><span data-stu-id="7b418-114">This table includes the column **LoginID**, which contains the login for each employee in the form *domain\login*.</span></span> <span data-ttu-id="7b418-115">若要篩選此資料表，以使各員工僅收到與其相關的資料，請指定參數化篩選子句：</span><span class="sxs-lookup"><span data-stu-id="7b418-115">To filter this table so that each employee receives only the data related to them, specify a parameterized filter clause of:</span></span>  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 <span data-ttu-id="7b418-116">此篩選可確保每位員工的訂閱僅包含 **HumanResources.Employee** 資料表中與該員工自己有關的資料 (本範例中是單一資料列)。</span><span class="sxs-lookup"><span data-stu-id="7b418-116">This filter ensures that each employee's subscription only contains data from the **HumanResources.Employee** table that is relevant to that employee (which in this case is a single row).</span></span> <span data-ttu-id="7b418-117">如需詳細資訊，請參閱＜ [參數化資料列篩選器](parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7b418-117">For more information, see [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
 <span data-ttu-id="7b418-118">第二步要使用與指定兩資料表之間聯結類似的語法，將此篩選擴充到所有相關資料表。</span><span class="sxs-lookup"><span data-stu-id="7b418-118">The next step is to extend this filter to each of the related tables, using syntax similar to that used to specify a join between two tables.</span></span> <span data-ttu-id="7b418-119">第一個聯結篩選子句為：</span><span class="sxs-lookup"><span data-stu-id="7b418-119">The first join filter clause is:</span></span>  
  
```  
Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
```  
  
 <span data-ttu-id="7b418-120">此子句可確保訂閱中只包含與各業務員相關的訂單資料。</span><span class="sxs-lookup"><span data-stu-id="7b418-120">This ensures the subscription contains only the order data relevant to each sales person.</span></span> <span data-ttu-id="7b418-121">第二個聯結篩選子句為：</span><span class="sxs-lookup"><span data-stu-id="7b418-121">The second join filter clause is:</span></span>  
  
```  
SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
```  
  
 <span data-ttu-id="7b418-122">此子句可確保訂閱中只包含與各業務員訂單資料相關的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7b418-122">This ensures the subscription contains only the detail data related to the order data for each sales person.</span></span> <span data-ttu-id="7b418-123">此範例只顯示每個聯結點聯結一個資料表的情況，您還可在每個聯結點上聯結多個資料表。</span><span class="sxs-lookup"><span data-stu-id="7b418-123">This example shows a single table being joined at each point; it is also possible to join more than one table at each point.</span></span>  
  
 <span data-ttu-id="7b418-124">透過「新增發行集精靈」和 **[發行集屬性]** 對話方塊可一次新增一個聯結篩選，或者也可以程式化新增。</span><span class="sxs-lookup"><span data-stu-id="7b418-124">Join filters can be added one at a time through the New Publication Wizard and the **Publication Properties** dialog box, or they can be added programmatically.</span></span> <span data-ttu-id="7b418-125">透過「新增發行集精靈」可自動產生聯結篩選：為資料表指定一個資料列篩選，然後聯結篩選會套用到所有相關的資料表。</span><span class="sxs-lookup"><span data-stu-id="7b418-125">They can also be generated automatically through the New Publication Wizard: you specify a row filter for a table and join filters are applied to all related tables.</span></span> <span data-ttu-id="7b418-126">如需詳細資訊，請參閱[定義和修改合併發行項之間的聯結篩選](../publish/define-and-modify-a-join-filter-between-merge-articles.md)、[在合併發行項之間自動產生一組聯結篩選 &#40;SQL Server Management Studio&#41;](../publish/automatically-generate-join-filters-between-merge-articles.md) 以及[定義發行項](../publish/define-an-article.md)。</span><span class="sxs-lookup"><span data-stu-id="7b418-126">For more information, see [Define and Modify a Join Filter Between Merge Articles](../publish/define-and-modify-a-join-filter-between-merge-articles.md), [Automatically Generate a Set of Join Filters Between Merge Articles &#40;SQL Server Management Studio&#41;](../publish/automatically-generate-join-filters-between-merge-articles.md), and [Define an Article](../publish/define-an-article.md).</span></span>  
  
## <a name="optimizing-join-filter-performance"></a><span data-ttu-id="7b418-127">最佳化聯結篩選效能</span><span class="sxs-lookup"><span data-stu-id="7b418-127">Optimizing Join Filter Performance</span></span>  
 <span data-ttu-id="7b418-128">下列指導方針有助於最佳化聯結篩選效能：</span><span class="sxs-lookup"><span data-stu-id="7b418-128">Join filter performance can be optimized by following these guidelines:</span></span>  
  
-   <span data-ttu-id="7b418-129">限制聯結篩選階層中資料表的數量。</span><span class="sxs-lookup"><span data-stu-id="7b418-129">Limit the number of tables in the join filter hierarchy.</span></span>  
  
     <span data-ttu-id="7b418-130">聯結篩選可以包含無限數量的資料表，但如果篩選中的資料表數量過多，會嚴重影響合併處理過程中的效能。</span><span class="sxs-lookup"><span data-stu-id="7b418-130">Join Filters can involve an unlimited number of tables, but filters with a large number of tables can significantly impact performance during merge processing.</span></span> <span data-ttu-id="7b418-131">若您正在產生五個以上資料表的聯結篩選，請考慮其他方案：不要篩選小型、無法變更或主要為查詢資料表的資料表。</span><span class="sxs-lookup"><span data-stu-id="7b418-131">If you are generating join filters of five or more tables, consider other solutions: do not filter tables that are small, not subject to change, or are primarily lookup tables.</span></span> <span data-ttu-id="7b418-132">聯結篩選只能用於必須在訂閱中分割的資料表之間。</span><span class="sxs-lookup"><span data-stu-id="7b418-132">Use join filters only between tables that must be partitioned among subscriptions.</span></span>  
  
-   <span data-ttu-id="7b418-133">在適當處，將 **聯結唯一索引鍵** 選項設為 **True** 。</span><span class="sxs-lookup"><span data-stu-id="7b418-133">Set the **join unique key** option to **True** where appropriate.</span></span>  
  
     <span data-ttu-id="7b418-134">如果父資料表中聯結資料行是唯一的，則合併處理可實現特殊效能最佳化。</span><span class="sxs-lookup"><span data-stu-id="7b418-134">The merge process has special performance optimizations available if the joined column in the parent is unique.</span></span> <span data-ttu-id="7b418-135">如果聯結條件基於唯一資料行，請為聯結篩選設定 **聯結唯一索引鍵** 選項。</span><span class="sxs-lookup"><span data-stu-id="7b418-135">If the join condition is based on a unique column, set the **join unique key** option for the join filter.</span></span> <span data-ttu-id="7b418-136">如需設定此選項的詳細資訊，請參閱上一節列出的如何主題。</span><span class="sxs-lookup"><span data-stu-id="7b418-136">For information about setting this option, see the how-to topics listed in the previous section.</span></span>  
  
-   <span data-ttu-id="7b418-137">確定聯結篩選中參考的資料行已進行索引。</span><span class="sxs-lookup"><span data-stu-id="7b418-137">Ensure that the columns referenced in join filters are indexed.</span></span>  
  
     <span data-ttu-id="7b418-138">如果篩選中參考的資料行已進行索引，則複寫能夠更有效地處理篩選。</span><span class="sxs-lookup"><span data-stu-id="7b418-138">If the columns referenced in the filter are indexed, replication can process the filters more efficiently.</span></span>  
  
-   <span data-ttu-id="7b418-139">請勿建立模仿聯結篩選的資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="7b418-139">Do not create row filters that mimic join filters.</span></span>  
  
     <span data-ttu-id="7b418-140">在 WHERE 子句中使用子查詢可建立模仿聯結篩選的資料列篩選，例如：</span><span class="sxs-lookup"><span data-stu-id="7b418-140">It is possible to create row filters that mimic join filters by using a subquery in a WHERE clause, such as:</span></span>  
  
    ```  
    WHERE Customer.SalesPersonID IN (SELECT EmployeeID FROM Employee WHERE LoginID = SUSER_SNAME())   
    ```  
  
     <span data-ttu-id="7b418-141">強烈建議以聯結篩選而不是子查詢表示所有上述邏輯。</span><span class="sxs-lookup"><span data-stu-id="7b418-141">It is strongly recommended that all such logic be expressed in a join filter rather than a subquery.</span></span> <span data-ttu-id="7b418-142">如果應用程式要求資料列篩選使用子查詢，請確定子查詢僅參考查閱資料 (不進行變更)。</span><span class="sxs-lookup"><span data-stu-id="7b418-142">If your application requires a row filter to use a subsquery, ensure that the subquery only references lookup data that does not change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b418-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b418-143">See Also</span></span>  
 <span data-ttu-id="7b418-144">[針對合併式複寫篩選發行的資料](filter-published-data-for-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="7b418-144">[Filter Published Data for Merge Replication](filter-published-data-for-merge-replication.md) </span></span>  
 [<span data-ttu-id="7b418-145">參數化資料列篩選器</span><span class="sxs-lookup"><span data-stu-id="7b418-145">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  
