---
title: 計畫指南 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- SQL plan guides
- OPTIMIZE FOR query hint
- RECOMPILE query hint
- OBJECT plan guide
- plan guides [SQL Server], about plan guides
- OPTION clause
- plan guides [SQL Server]
- USE PLAN query hint
ms.assetid: bfc97632-c14c-4768-9dc5-a9c512f6b2bd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c97682163313a56acb8521174fa8d4012a69b529
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597788"
---
# <a name="plan-guides"></a><span data-ttu-id="b042c-102">計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-102">Plan Guides</span></span>
  <span data-ttu-id="b042c-103">當您無法或不想要在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中直接變更實際查詢的文字時，您可以使用計畫指南來最佳化查詢的效能。</span><span class="sxs-lookup"><span data-stu-id="b042c-103">Plan guides let you optimize the performance of queries when you cannot or do not want to directly change the text of the actual query in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="b042c-104">計畫指南是將查詢提示或固定的查詢計畫附加至查詢，藉以影響查詢的最佳化。</span><span class="sxs-lookup"><span data-stu-id="b042c-104">Plan guides influence the optimization of queries by attaching query hints or a fixed query plan to them.</span></span> <span data-ttu-id="b042c-105">當協力廠商所提供的資料庫應用程式中有少量查詢子集的執行情況不如預期時，使用計畫指南會非常有用。</span><span class="sxs-lookup"><span data-stu-id="b042c-105">Plan guides can be useful when a small subset of queries in a database application provided by a third-party vendor are not performing as expected.</span></span> <span data-ttu-id="b042c-106">在計畫指南中，指定您要最佳化的 Transact-SQL 陳述式以及包含您想要使用之查詢提示的 OPTION 子句，或者是您想要用來將查詢進行最佳化的特定查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="b042c-106">In the plan guide, you specify the Transact-SQL statement that you want optimized and either an OPTION clause that contains the query hints you want to use or a specific query plan you want to use to optimize the query.</span></span> <span data-ttu-id="b042c-107">執行查詢時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會比對 Transact-SQL 陳述式與計畫指南，然後在執行階段中，將 OPTION 子句附加至查詢或使用指定的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="b042c-107">When the query executes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the Transact-SQL statement to the plan guide and attaches the OPTION clause to the query at run time or uses the specified query plan.</span></span>  
  
 <span data-ttu-id="b042c-108">您可以建立的計畫指南總數僅限於可用的系統資源。</span><span class="sxs-lookup"><span data-stu-id="b042c-108">The total number of plan guides you can create is limited only by available system resources.</span></span> <span data-ttu-id="b042c-109">因此，您應該限制計畫指南，只用於可改善或穩定效能的關鍵任務查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-109">Nevertheless, plan guides should be limited to mission-critical queries that are targeted for improved or stabilized performance.</span></span> <span data-ttu-id="b042c-110">計畫指南不應用來影響已部署之應用程式的大部分查詢負載。</span><span class="sxs-lookup"><span data-stu-id="b042c-110">Plan guides should not be used to influence most of the query load of a deployed application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b042c-111">並非每個 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本都可使用計劃指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-111">Plan guides cannot be used in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b042c-112">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2014 版本支援的功能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="b042c-112">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="b042c-113">在任何版本中都可以看到計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-113">Plan guides are visible in any edition.</span></span> <span data-ttu-id="b042c-114">您也可以將包含計畫指南的資料庫附加到任何版本中。</span><span class="sxs-lookup"><span data-stu-id="b042c-114">You can also attach a database that contains plan guides to any edition.</span></span> <span data-ttu-id="b042c-115">當您將資料庫還原或附加至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的升級版本時，計畫指南仍維持不變。</span><span class="sxs-lookup"><span data-stu-id="b042c-115">Plan guides remain intact when you restore or attach a database to an upgraded version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="types-of-plan-guides"></a><span data-ttu-id="b042c-116">計畫指南的類型</span><span class="sxs-lookup"><span data-stu-id="b042c-116">Types of Plan Guides</span></span>  
 <span data-ttu-id="b042c-117">您可以建立下列類型的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-117">The following types of plan guides can be created.</span></span>  
  
 <span data-ttu-id="b042c-118">OBJECT 計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-118">OBJECT plan guide</span></span>  
 <span data-ttu-id="b042c-119">OBJECT 計畫指南可搭配在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序、純量使用者定義函數、多個陳述式資料表值使用者定義函數以及 DML 觸發程序內容中執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-119">An OBJECT plan guide matches queries that execute in the context of [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, scalar user-defined functions, multi-statement table-valued user-defined functions, and DML triggers.</span></span>  
  
 <span data-ttu-id="b042c-120">假設下列採用 `@Country`_`region` 參數的預存程序位於針對 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫所部署的資料庫應用程式中：</span><span class="sxs-lookup"><span data-stu-id="b042c-120">Suppose the following stored procedure, which takes the `@Country`_`region` parameter, is in a database application that is deployed against the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
CREATE PROCEDURE Sales.GetSalesOrderByCountry (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h, Sales.Customer AS c,   
        Sales.SalesTerritory AS t  
    WHERE h.CustomerID = c.CustomerID  
        AND c.TerritoryID = t.TerritoryID  
        AND CountryRegionCode = @Country_region  
END;  
```  
  
 <span data-ttu-id="b042c-121">假設此預存程序已針對 `@Country`_`region = N'AU'` (澳洲) 編譯及最佳化。</span><span class="sxs-lookup"><span data-stu-id="b042c-121">Assume that this stored procedure has been compiled and optimized for `@Country`_`region = N'AU'` (Australia).</span></span> <span data-ttu-id="b042c-122">不過，由於來自澳洲的銷售訂單相當少，因此當查詢在多個銷售訂單上使用國家 (地區) 的參數值執行時，效能就會降低。</span><span class="sxs-lookup"><span data-stu-id="b042c-122">However, because there are relatively few sales orders that originate from Australia, performance decreases when the query executes using parameter values of countries with more sales orders.</span></span> <span data-ttu-id="b042c-123">由於大部分的銷售訂單都是來自美國，所以針對 `@Country`\_`region = N'US'` 所產生的查詢計劃可能會比 `@Country`\_`region` 參數的所有可能值具有更好的執行效能。</span><span class="sxs-lookup"><span data-stu-id="b042c-123">Because the most sales orders originate in the United States, a query plan that is generated for `@Country`\_`region = N'US'` would likely perform better for all possible values of the `@Country`\_`region` parameter.</span></span>  
  
 <span data-ttu-id="b042c-124">您可以修改預存程序並將 `OPTIMIZE FOR` 查詢提示加入查詢以處理此問題。</span><span class="sxs-lookup"><span data-stu-id="b042c-124">You could address this problem by modifying the stored procedure to add the `OPTIMIZE FOR` query hint to the query.</span></span> <span data-ttu-id="b042c-125">不過，因為預存程序是在已部署的應用程式中，所以您無法直接修改應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b042c-125">However, because the stored procedure is in a deployed application, you cannot directly modify the application code.</span></span> <span data-ttu-id="b042c-126">您只能在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中建立下列計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-126">Instead, you can create the following plan guide in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT *FROM Sales.SalesOrderHeader AS h,  
        Sales.Customer AS c,  
        Sales.SalesTerritory AS t  
        WHERE h.CustomerID = c.CustomerID   
            AND c.TerritoryID = t.TerritoryID  
            AND CountryRegionCode = @Country_region',  
@type = N'OBJECT',  
@module_or_batch = N'Sales.GetSalesOrderByCountry',  
@params = NULL,  
@hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
 <span data-ttu-id="b042c-127">執行在 `sp_create_plan_guide` 陳述式中指定的查詢時，在最佳化前會先修改查詢以包含 `OPTIMIZE FOR (@Country = N''US'')` 子句。</span><span class="sxs-lookup"><span data-stu-id="b042c-127">When the query specified in the `sp_create_plan_guide` statement executes, the query is modified before optimization to include the `OPTIMIZE FOR (@Country = N''US'')` clause.</span></span>  
  
 <span data-ttu-id="b042c-128">SQL 計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-128">SQL plan guide</span></span>  
 <span data-ttu-id="b042c-129">SQL 計畫指南可搭配在不屬於資料庫物件的獨立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式與批次內容中執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-129">An SQL plan guide matches queries that execute in the context of stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches that are not part of a database object.</span></span> <span data-ttu-id="b042c-130">以 SQL 為基礎的計畫指南可用以搭配參數化為指定形式的查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-130">SQL-based plan guides can also be used to match queries that parameterize to a specified form.</span></span> <span data-ttu-id="b042c-131">SQL 計畫指南會套用至獨立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式和批次。</span><span class="sxs-lookup"><span data-stu-id="b042c-131">SQL plan guides apply to stand-alone [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and batches.</span></span> <span data-ttu-id="b042c-132">這些陳述式通常是由應用程式使用 [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) 系統預存程序進行提交。</span><span class="sxs-lookup"><span data-stu-id="b042c-132">Frequently, these statements are submitted by an application by using the [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) system stored procedure.</span></span> <span data-ttu-id="b042c-133">例如，請考慮下列獨立批次：</span><span class="sxs-lookup"><span data-stu-id="b042c-133">For example, consider the following stand-alone batch:</span></span>  
  
```  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 <span data-ttu-id="b042c-134">若要防止這項查詢產生平行執行計畫，請建立下列計畫指南並將 `MAXDOP` 參數中的 `1` 查詢提示設定為 `@hints` 。</span><span class="sxs-lookup"><span data-stu-id="b042c-134">To prevent a parallel execution plan from being generated on this query, create the following plan guide and set the `MAXDOP` query hint to `1` in the `@hints` parameter.</span></span>  
  
```  
sp_create_plan_guide   
@name = N'Guide2',   
@stmt = N'SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC',  
@type = N'SQL',  
@module_or_batch = NULL,   
@params = NULL,   
@hints = N'OPTION (MAXDOP 1)';  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b042c-135">針對 `@module_or_batch` 陳述式的 `@params` 與 `sp_create_plan guide` 引數所提供的值必須符合在實際查詢中所提交的對應文字。</span><span class="sxs-lookup"><span data-stu-id="b042c-135">The values that are supplied for the `@module_or_batch` and `@params` arguments of the `sp_create_plan guide` statement must match the corresponding text submitted in the actual query.</span></span> <span data-ttu-id="b042c-136">如需詳細資訊，請參閱 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) 陳述式的 [使用 SQL Server Profiler 建立及測試計畫指南](plan-guides.md)中直接變更實際查詢的文字時，您可以使用計畫指南來最佳化查詢的效能。</span><span class="sxs-lookup"><span data-stu-id="b042c-136">For more information, see [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) and [Use SQL Server Profiler to Create and Test Plan Guides](plan-guides.md).</span></span>  
  
 <span data-ttu-id="b042c-137">當 PARAMETERIZATION 資料庫選項 SET 為 FORCED 時，或是當建立 TEMPLATE 計畫指南以指定要參數化的查詢類別時，SQL 計畫指南也可在參數化為相同形式的查詢上建立 SQL 計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-137">SQL plan guides can also be created on queries that parameterize to the same form when the PARAMETERIZATION database option is SET to FORCED, or when a TEMPLATE plan guide is created specifying that a parameterized class of queries.</span></span>  
  
 <span data-ttu-id="b042c-138">TEMPLATE 計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-138">TEMPLATE plan guide</span></span>  
 <span data-ttu-id="b042c-139">TEMPLATE 計畫指南可搭配參數化為指定形式的獨立查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-139">A TEMPLATE plan guide matches stand-alone queries that parameterize to a specified form.</span></span> <span data-ttu-id="b042c-140">這些計畫指南可用以針對查詢類別，覆寫資料庫目前的 PARAMETERIZATION 資料庫 SET 選項。</span><span class="sxs-lookup"><span data-stu-id="b042c-140">These plan guides are used to override the current PARAMETERIZATION database SET option of a database for a class of queries.</span></span>  
  
 <span data-ttu-id="b042c-141">您可以在下列其中一種情況下建立 TEMPLATE 計畫指南：</span><span class="sxs-lookup"><span data-stu-id="b042c-141">You can create a TEMPLATE plan guide in either of the following situations:</span></span>  
  
-   <span data-ttu-id="b042c-142">PARAMETERIZATION 資料庫選項設定成 FORCED，但有一些要根據簡單參數化規則編譯的查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-142">The PARAMETERIZATION database option is SET to FORCED, but there are queries you want compiled according to the rules of simple parameterization.</span></span>  
  
-   <span data-ttu-id="b042c-143">PARAMETERIZATION 資料庫選項設定成 SIMPLE (預設值)，但是您要在某個查詢類別嘗試強制參數化。</span><span class="sxs-lookup"><span data-stu-id="b042c-143">The PARAMETERIZATION database option is SET to SIMPLE (the default setting), but you want forced parameterization to be tried on a class of queries.</span></span>  
  
## <a name="plan-guide-matching-requirements"></a><span data-ttu-id="b042c-144">計畫指南比對需求</span><span class="sxs-lookup"><span data-stu-id="b042c-144">Plan Guide Matching Requirements</span></span>  
 <span data-ttu-id="b042c-145">計畫指南的範圍僅限於建立它們的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b042c-145">Plan guides are scoped to the database in which they are created.</span></span> <span data-ttu-id="b042c-146">因此，當查詢執行時，只有位於目前資料庫中的計畫指南才可以配合查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-146">Therefore, only plan guides that are in the database that is current when a query executes can be matched to the query.</span></span> <span data-ttu-id="b042c-147">例如，如果 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 是目前的資料庫且執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="b042c-147">For example, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following query executes:</span></span>  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="b042c-148">只有在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中的計畫指南能夠配合此查詢。</span><span class="sxs-lookup"><span data-stu-id="b042c-148">Only plan guides in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database are eligible to be matched to this query.</span></span> <span data-ttu-id="b042c-149">不過，如果 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 是目前的資料庫且執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b042c-149">However, if [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] is the current database and the following statements are run:</span></span>  
  
 `USE DB1;`  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 <span data-ttu-id="b042c-150">只有 `DB1` 中的計畫指南才能夠配合查詢，因為查詢是在 `DB1`的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="b042c-150">Only plan guides in `DB1` are eligible to be matched to the query because the query is executing in the context of `DB1`.</span></span>  
  
 <span data-ttu-id="b042c-151">對於以 SQL 或 TEMPLATE 為基礎的計畫指南而言，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會逐字元比較查詢的 @module_or_batch 和 @params 引數值，使兩個值相符。</span><span class="sxs-lookup"><span data-stu-id="b042c-151">For SQL- or TEMPLATE-based plan guides, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] matches the values for the @module_or_batch and @params arguments to a query by comparing the two values character by character.</span></span> <span data-ttu-id="b042c-152">這表示您必須提供與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在實際批次中所收到的文字完全相符的文字。</span><span class="sxs-lookup"><span data-stu-id="b042c-152">This means you must provide the text exactly as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] receives it in the actual batch.</span></span>  
  
 <span data-ttu-id="b042c-153">@type = 'SQL' 且 @module_or_batch 設定為 NULL 時，@module_or_batch 的值會設定為值 @stmt。這表示，提供的 *statement_text* 值必須與提交給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的值採用相同的格式 (逐字元)。</span><span class="sxs-lookup"><span data-stu-id="b042c-153">When @type = 'SQL' and @module_or_batch is set to NULL, the value of @module_or_batch is set to the value of @stmt. This means that the value for *statement_text* must be provided in the identical format, character-for-character, as it is submitted to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b042c-154">不會執行內部轉換來簡化這個比對作業。</span><span class="sxs-lookup"><span data-stu-id="b042c-154">No internal conversion is performed to facilitate this match.</span></span>  
  
 <span data-ttu-id="b042c-155">當一般 (SQL 或 OBJECT) 計畫指南和 TEMPLATE 計畫指南都適用於陳述式時，只會使用一般計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-155">When both a regular (SQL or OBJECT) plan guide and a TEMPLATE plan guide can apply to a statement, only the regular plan guide will be used.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b042c-156">在包含要建立計劃指南的陳述式之批次中，將無法包含 USE *database* 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b042c-156">The batch that contains the statement on which you want to create a plan guide cannot contain a USE *database* statement.</span></span>  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a><span data-ttu-id="b042c-157">計畫指南對於計畫快取的影響</span><span class="sxs-lookup"><span data-stu-id="b042c-157">Plan Guide Effect on the Plan Cache</span></span>  
 <span data-ttu-id="b042c-158">針對某個模組建立計畫指南時，就會從計畫快取中移除該模組的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="b042c-158">Creating a plan guide on a module removes the query plan for that module from the plan cache.</span></span> <span data-ttu-id="b042c-159">針對某個批次建立 OBJECT 或 SQL 類型的計畫指南時，就會移除具有相同雜湊值之批次的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="b042c-159">Creating a plan guide of type OBJECT or SQL on a batch removes the query plan for a batch that has the same hash value.</span></span> <span data-ttu-id="b042c-160">建立 TEMPLATE 類型的計畫指南時，就會從該資料庫內部的計畫快取中移除所有單一陳述式批次。</span><span class="sxs-lookup"><span data-stu-id="b042c-160">Creating a plan guide of type TEMPLATE removes all single-statement batches from the plan cache within that database.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="b042c-161">相關工作</span><span class="sxs-lookup"><span data-stu-id="b042c-161">Related Tasks</span></span>  
  
|<span data-ttu-id="b042c-162">Task</span><span class="sxs-lookup"><span data-stu-id="b042c-162">Task</span></span>|<span data-ttu-id="b042c-163">主題</span><span class="sxs-lookup"><span data-stu-id="b042c-163">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="b042c-164">描述如何建立計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-164">Describes how to create a plan guide.</span></span>|[<span data-ttu-id="b042c-165">建立新的計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-165">Create a New Plan Guide</span></span>](create-a-new-plan-guide.md)|  
|<span data-ttu-id="b042c-166">描述如何建立參數化查詢的計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-166">Describes how to create a plan guide for parameterized queries.</span></span>|[<span data-ttu-id="b042c-167">建立參數化查詢的計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-167">Create a Plan Guide for Parameterized Queries</span></span>](create-a-plan-guide-for-parameterized-queries.md)|  
|<span data-ttu-id="b042c-168">描述如何使用計畫指南控制查詢參數化行為。</span><span class="sxs-lookup"><span data-stu-id="b042c-168">Describes how to control query parameterization behavior by using plan guides.</span></span>|[<span data-ttu-id="b042c-169">使用計畫指南指定查詢參數化行為</span><span class="sxs-lookup"><span data-stu-id="b042c-169">Specify Query Parameterization Behavior by Using Plan Guides</span></span>](specify-query-parameterization-behavior-by-using-plan-guides.md)|  
|<span data-ttu-id="b042c-170">描述如何將固定的查詢計畫併入計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-170">Describes how to include a fixed query plan in a plan guide.</span></span>|[<span data-ttu-id="b042c-171">將固定的查詢計畫套用至計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-171">Apply a Fixed Query Plan to a Plan Guide</span></span>](apply-a-fixed-query-plan-to-a-plan-guide.md)|  
|<span data-ttu-id="b042c-172">描述如何在計畫指南中指定查詢提示。</span><span class="sxs-lookup"><span data-stu-id="b042c-172">Describes how to specify query hints in a plan guide.</span></span>|[<span data-ttu-id="b042c-173">將查詢提示附加至計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-173">Attach Query Hints to a Plan Guide</span></span>](attach-query-hints-to-a-plan-guide.md)|  
|<span data-ttu-id="b042c-174">描述如何檢視計畫指南屬性。</span><span class="sxs-lookup"><span data-stu-id="b042c-174">Describes how to view plan guide properties.</span></span>|[<span data-ttu-id="b042c-175">檢視計畫指南屬性</span><span class="sxs-lookup"><span data-stu-id="b042c-175">View Plan Guide Properties</span></span>](view-plan-guide-properties.md)|  
|<span data-ttu-id="b042c-176">描述如何使用 SQL Server Profiler 建立和測試計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-176">Describes how to use SQL Server Profiler to create and test plan guides.</span></span>|[<span data-ttu-id="b042c-177">使用 SQL Server Profiler 建立及測試計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-177">Use SQL Server Profiler to Create and Test Plan Guides</span></span>](plan-guides.md)|  
|<span data-ttu-id="b042c-178">描述如何驗證計畫指南。</span><span class="sxs-lookup"><span data-stu-id="b042c-178">Describes how to validate plan guides.</span></span>|[<span data-ttu-id="b042c-179">升級之後驗證計畫指南</span><span class="sxs-lookup"><span data-stu-id="b042c-179">Validate Plan Guides After Upgrade</span></span>](validate-plan-guides-after-upgrade.md)|  
  
## <a name="see-also"></a><span data-ttu-id="b042c-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b042c-180">See Also</span></span>  
 <span data-ttu-id="b042c-181">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b042c-181">[sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="b042c-182">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b042c-182">[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql) </span></span>  
 <span data-ttu-id="b042c-183">[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b042c-183">[sp_control_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql) </span></span>  
 <span data-ttu-id="b042c-184">[sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b042c-184">[sys.plan_guides &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql) </span></span>  
 [<span data-ttu-id="b042c-185">sys.fn_validate_plan_guide &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b042c-185">sys.fn_validate_plan_guide &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql)  
  
  
