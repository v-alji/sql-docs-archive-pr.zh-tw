---
title: MSSQLSERVER_2020 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2020 (Database Engine error)
ms.assetid: 4a8bf90f-a083-4c53-84f0-d23c711c8081
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5939267c37e90e7b8456dc01a4af79545e775656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598925"
---
# <a name="mssqlserver_2020"></a><span data-ttu-id="e2067-102">MSSQLSERVER_2020</span><span class="sxs-lookup"><span data-stu-id="e2067-102">MSSQLSERVER_2020</span></span>
    
## <a name="details"></a><span data-ttu-id="e2067-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e2067-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2067-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e2067-104">Product Name</span></span>|<span data-ttu-id="e2067-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e2067-105">SQL Server</span></span>|  
|<span data-ttu-id="e2067-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e2067-106">Event ID</span></span>|<span data-ttu-id="e2067-107">2020</span><span class="sxs-lookup"><span data-stu-id="e2067-107">2020</span></span>|  
|<span data-ttu-id="e2067-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e2067-108">Event Source</span></span>|<span data-ttu-id="e2067-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e2067-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e2067-110">元件</span><span class="sxs-lookup"><span data-stu-id="e2067-110">Component</span></span>|<span data-ttu-id="e2067-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e2067-111">SQLEngine</span></span>|  
|<span data-ttu-id="e2067-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e2067-112">Symbolic Name</span></span>||  
|<span data-ttu-id="e2067-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e2067-113">Message Text</span></span>|<span data-ttu-id="e2067-114">針對實體 "%.\*ls" 所報告的相依性不包含資料行的參考。</span><span class="sxs-lookup"><span data-stu-id="e2067-114">The dependencies reported for entity "%.\*ls" do not include references to columns.</span></span> <span data-ttu-id="e2067-115">這是因為此實體參考了不存在的物件，或是此實體中的一個或多個陳述式發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2067-115">This is either because the entity references an object that does not exist or because of an error in one or more statements in the entity.</span></span>  <span data-ttu-id="e2067-116">在重新執行查詢以前，請確定此實體中沒有任何錯誤，而且此實體參考的所有物件都存在。</span><span class="sxs-lookup"><span data-stu-id="e2067-116">Before rerunning the query, ensure that there are no errors in the entity and that all objects referenced by the entity exist.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e2067-117">說明</span><span class="sxs-lookup"><span data-stu-id="e2067-117">Explanation</span></span>  
 <span data-ttu-id="e2067-118">**sys.dm_sql_referenced_entities** 系統函數會回報任何資料行層級相依性，以進行結構描述繫結參考。</span><span class="sxs-lookup"><span data-stu-id="e2067-118">The **sys.dm_sql_referenced_entities** system function will report any column-level dependency for schema-bound references.</span></span> <span data-ttu-id="e2067-119">例如，此函數將會報告索引檢視表的所有資料行層級相依性，因為索引檢視表需要結構描述繫結。</span><span class="sxs-lookup"><span data-stu-id="e2067-119">For example, the function will report all column-level dependencies for an indexed view because an indexed view requires schema binding.</span></span> <span data-ttu-id="e2067-120">不過，如果受參考實體並未結構描述繫結，只有當參考資料行的所有陳述式都可以繫結時，才會報告資料行相依性。</span><span class="sxs-lookup"><span data-stu-id="e2067-120">However, when the referenced entity is not schema-bound, column dependencies are reported only when all statements in which the columns are referenced can be bound.</span></span> <span data-ttu-id="e2067-121">只有當剖析陳述式時所有物件都存在時，陳述式才能成功繫結。</span><span class="sxs-lookup"><span data-stu-id="e2067-121">Statements can be successfully bound only if all objects exist at the time the statements are parsed.</span></span> <span data-ttu-id="e2067-122">如果實體中定義的任何陳述式無法繫結，即不會回報資料行相依性，而且 **referenced_minor_id** 資料行會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="e2067-122">If any statement defined in the entity fails to bind, column dependencies will not be reported and the **referenced_minor_id** column will return 0.</span></span> <span data-ttu-id="e2067-123">無法解析資料行相依性時，就會引發錯誤 2020。</span><span class="sxs-lookup"><span data-stu-id="e2067-123">When column dependencies cannot be resolved, error 2020 is raised.</span></span> <span data-ttu-id="e2067-124">這個錯誤不會讓查詢無法傳回物件層級相依性。</span><span class="sxs-lookup"><span data-stu-id="e2067-124">This error does not prevent the query from returning object-level dependencies.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e2067-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e2067-125">User Action</span></span>  
 <span data-ttu-id="e2067-126">更正發生錯誤 2020 之前，在訊息中識別的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="e2067-126">Correct any errors identified in the message before error 2020.</span></span> <span data-ttu-id="e2067-127">例如，在下列程式碼範例中，`Production.ApprovedDocuments` 檢視表定義於 `Title` 資料表中的 `ChangeNumber`、`Status` 和 `Production.Document` 資料行上。</span><span class="sxs-lookup"><span data-stu-id="e2067-127">For example, in the following code example the view `Production.ApprovedDocuments` is defined on the columns `Title`, `ChangeNumber`, and `Status` in the `Production.Document` table.</span></span> <span data-ttu-id="e2067-128">系統會針對 `ApprovedDocuments` 檢視表所相依的物件和資料行查詢 **sys.dm_sql_referenced_entities** 系統函數。</span><span class="sxs-lookup"><span data-stu-id="e2067-128">The **sys.dm_sql_referenced_entities** system function is queried for the objects and columns on which the `ApprovedDocuments` view depends.</span></span> <span data-ttu-id="e2067-129">因為此檢視表並非使用 WITH SCHEMA_BINDING 子句建立，所以檢視表中參考的資料行可能會在參考的資料表中修改。</span><span class="sxs-lookup"><span data-stu-id="e2067-129">Because the view is not created using the WITH SCHEMA_BINDING clause, the columns referenced in the view can be modified in the referenced table.</span></span> <span data-ttu-id="e2067-130">此範例會將 `ChangeNumber` 資料表中的 `Production.Document` 資料行重新命名為 `TrackingNumber`，藉以更改此資料行。</span><span class="sxs-lookup"><span data-stu-id="e2067-130">The example alters the column `ChangeNumber` in the `Production.Document` table by renaming it to `TrackingNumber`.</span></span> <span data-ttu-id="e2067-131">系統會再次針對 `ApprovedDocuments` 檢視表查詢目錄檢視。不過，它無法繫結至檢視表中定義的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="e2067-131">The catalog view is queried again for the `ApprovedDocuments` view; however it cannot bind to all the columns defined in the view.</span></span> <span data-ttu-id="e2067-132">然後，系統會傳回識別此問題的錯誤 207 和 2020。</span><span class="sxs-lookup"><span data-stu-id="e2067-132">Errors 207 and 2020 are returned identifying the problem.</span></span> <span data-ttu-id="e2067-133">若要解決此問題，您必須更改檢視表，以便反映資料行的新名稱。</span><span class="sxs-lookup"><span data-stu-id="e2067-133">To resolve the problem, the view must be altered to reflect the new name of the column.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `CREATE VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title, ChangeNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 `EXEC sp_rename 'Production.Document.ChangeNumber', 'TrackingNumber', 'COLUMN';`  
  
 `GO`  
  
 `SELECT referenced_schema_name AS schema_name`  
  
 `,referenced_entity_name AS table_name`  
  
 `,referenced_minor_name AS referenced_column`  
  
 `FROM sys.dm_sql_referenced_entities ('Production.ApprovedDocuments', 'OBJECT');`  
  
 `GO`  
  
 <span data-ttu-id="e2067-134">此查詢會傳回下列錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="e2067-134">The query returns the following error messages.</span></span>  
  
 `Msg 207, Level 16, State 1, Procedure ApprovedDocuments, Line 3`  
  
 `Invalid column name 'ChangeNumber'.`  
  
 `Msg 2020, Level 16, State 1, Line 1`  
  
 `The dependencies reported for entity`  
  
 `"Production.ApprovedDocuments" do not include references to`  
  
 `columns. This is either because the entity references an`  
  
 `object that does not exist or because of an error in one or`  
  
 `more statements in the entity. Before rerunning the query,`  
  
 `ensure that there are no errors in the entity and that all`  
  
 `objects referenced by the entity exist.`  
  
 <span data-ttu-id="e2067-135">下列範例會更正檢視表中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="e2067-135">The following example corrects the column name in the view.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `ALTER VIEW Production.ApprovedDocuments`  
  
 `AS`  
  
 `SELECT Title,TrackingNumber, Status`  
  
 `FROM Production.Document`  
  
 `WHERE Status = 2;`  
  
 `GO`  
  
## <a name="see-also"></a><span data-ttu-id="e2067-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2067-136">See Also</span></span>  
 [<span data-ttu-id="e2067-137">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e2067-137">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
  
