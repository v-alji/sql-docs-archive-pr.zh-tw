---
title: 唯一條件約束與檢查條件約束 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], Visual Database Tools
- Visual Database Tools [SQL Server], constraints
ms.assetid: 637098af-2567-48f8-90f4-b41df059833e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 205e4ae3d6f89f10a933bf357d1eeda458852584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686868"
---
# <a name="unique-constraints-and-check-constraints"></a><span data-ttu-id="3feaf-102">唯一條件約束與檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-102">Unique Constraints and Check Constraints</span></span>
  <span data-ttu-id="3feaf-103">UNIQUE 和 CHECK 是兩種類型的條件約束，可用來強制執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表中的資料完整性。</span><span class="sxs-lookup"><span data-stu-id="3feaf-103">UNIQUE constraints and CHECK constraints are two types of constraints that can be used to enforce data integrity in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span> <span data-ttu-id="3feaf-104">這些都是重要的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="3feaf-104">These are important database objects.</span></span>  
  
 <span data-ttu-id="3feaf-105">本主題包含下列各節。</span><span class="sxs-lookup"><span data-stu-id="3feaf-105">This topic contains the following sections.</span></span>  
  
 [<span data-ttu-id="3feaf-106">UNIQUE 條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-106">UNIQUE Constraints</span></span>](#Unique)  
  
 [<span data-ttu-id="3feaf-107">CHECK 條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-107">CHECK Constraints</span></span>](#Check)  
  
 [<span data-ttu-id="3feaf-108">相關工作</span><span class="sxs-lookup"><span data-stu-id="3feaf-108">Related Tasks</span></span>](#Tasks)  
  
##  <a name="unique-constraints"></a><a name="Unique"></a> <span data-ttu-id="3feaf-109">UNIQUE 條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-109">UNIQUE Constraints</span></span>  
 <span data-ttu-id="3feaf-110">條件約束是 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 為您強制執行的規則。</span><span class="sxs-lookup"><span data-stu-id="3feaf-110">Constraints are rules that the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] enforces for you.</span></span> <span data-ttu-id="3feaf-111">例如，您可以使用 UNIQUE 條件約束，確定在未參與主索引鍵的特定資料行中沒有重複值。</span><span class="sxs-lookup"><span data-stu-id="3feaf-111">For example, you can use UNIQUE constraints to make sure that no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="3feaf-112">雖然 UNIQUE 條件約束和 PRIMARY KEY 條件約束兩者都強制唯一性，但是當您想要強制非主索引鍵之資料行 (或資料行組合) 的唯一性時，請使用 UNIQUE 條件約束而不要使用 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-112">Although both a UNIQUE constraint and a PRIMARY KEY constraint enforce uniqueness, use a UNIQUE constraint instead of a PRIMARY KEY constraint when you want to enforce the uniqueness of a column, or combination of columns, that is not the primary key.</span></span>  
  
 <span data-ttu-id="3feaf-113">UNIQUE 條件約束允許 NULL 值，這與 PRIMARY KEY 條件約束不同。</span><span class="sxs-lookup"><span data-stu-id="3feaf-113">Unlike PRIMARY KEY constraints, UNIQUE constraints allow for the value NULL.</span></span> <span data-ttu-id="3feaf-114">但是，就像參與 UNIQUE 條件約束的任何值，一個資料行只能有一個 Null 值。</span><span class="sxs-lookup"><span data-stu-id="3feaf-114">However, as with any value participating in a UNIQUE constraint, only one null value is allowed per column.</span></span> <span data-ttu-id="3feaf-115">UNIQUE 條件約束也可被 FOREIGN KEY 條件約束所參考。</span><span class="sxs-lookup"><span data-stu-id="3feaf-115">A UNIQUE constraint can be referenced by a FOREIGN KEY constraint.</span></span>  
  
 <span data-ttu-id="3feaf-116">當 UNIQUE 條件約束加入資料表現有的一個或多個資料行時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會檢查資料行中的現有資料，以確保所有數值都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3feaf-116">When a UNIQUE constraint is added to an existing column or columns in the table, by default, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] examines the existing data in the columns to make sure all values are unique.</span></span> <span data-ttu-id="3feaf-117">如果將 UNIQUE 條件約束加入包含重複數值的資料行內， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會傳回錯誤訊息，而且不加入條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-117">If a UNIQUE constraint is added to a column that has duplicated values, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error and does not add the constraint.</span></span>  
  
 <span data-ttu-id="3feaf-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 將自動建立 UNIQUE 索引，以強制執行 UNIQUE 條件約束的唯一性要求。</span><span class="sxs-lookup"><span data-stu-id="3feaf-118">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] automatically creates a UNIQUE index to enforce the uniqueness requirement of the UNIQUE constraint.</span></span> <span data-ttu-id="3feaf-119">因此，如果嘗試插入重複的資料列， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會傳回錯誤訊息，告訴您違反了 UNIQUE 條件約束，並且不會將資料列加入資料表內。</span><span class="sxs-lookup"><span data-stu-id="3feaf-119">Therefore, if an attempt to insert a duplicate row is made, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] returns an error message that states the UNIQUE constraint has been violated and does not add the row to the table.</span></span> <span data-ttu-id="3feaf-120">除非明確設定叢集索引，否則預設會建立一個非叢集索引來執行 UNIQUE 條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-120">Unless a clustered index is explicitly specified, a unique, nonclustered index is created by default to enforce the UNIQUE constraint.</span></span>  
  
##  <a name="check-constraints"></a><a name="Check"></a> <span data-ttu-id="3feaf-121">CHECK 條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-121">CHECK Constraints</span></span>  
 <span data-ttu-id="3feaf-122">CHECK 條件約束限制一個或多個資料行接受的值，藉此強制值域完整性。</span><span class="sxs-lookup"><span data-stu-id="3feaf-122">CHECK constraints enforce domain integrity by limiting the values that are accepted by one or more columns.</span></span> <span data-ttu-id="3feaf-123">您可使用能根據邏輯運算子傳回 TRUE 或 FALSE 的任何邏輯 (布林) 運算式來建立 CHECK 條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-123">You can create a CHECK constraint with any logical (Boolean) expression that returns TRUE or FALSE based on the logical operators.</span></span> <span data-ttu-id="3feaf-124">例如，可以藉由建立只允許範圍從 $15,000 到 $100,000 之資料的 CHECK 條件約束，以限制 **salary** 資料行的值範圍。</span><span class="sxs-lookup"><span data-stu-id="3feaf-124">For example, the range of values for a **salary** column can be limited by creating a CHECK constraint that allows for only data that ranges from $15,000 through $100,000.</span></span> <span data-ttu-id="3feaf-125">這可防止輸入的薪水超過一般的薪水範圍。</span><span class="sxs-lookup"><span data-stu-id="3feaf-125">This prevents salaries from being entered beyond the regular salary range.</span></span> <span data-ttu-id="3feaf-126">邏輯運算式可以是： `salary >= 15000 AND salary <= 100000`。</span><span class="sxs-lookup"><span data-stu-id="3feaf-126">The logical expression would be the following: `salary >= 15000 AND salary <= 100000`.</span></span>  
  
 <span data-ttu-id="3feaf-127">您可以將多個 CHECK 條件約束套用到單一資料行。</span><span class="sxs-lookup"><span data-stu-id="3feaf-127">You can apply multiple CHECK constraints to a single column.</span></span> <span data-ttu-id="3feaf-128">您也可以在資料表層級建立單一 CHECK 條件約束，將它套用到多個資料行。</span><span class="sxs-lookup"><span data-stu-id="3feaf-128">You can also apply a single CHECK constraint to multiple columns by creating it at the table level.</span></span> <span data-ttu-id="3feaf-129">例如，多重資料行的 CHECK 條件約束可用來確認 **country_region** 資料行值為 **USA** 的任何資料列，其 **state** 資料行內也會有兩個字元的值。</span><span class="sxs-lookup"><span data-stu-id="3feaf-129">For example, a multiple-column CHECK constraint could be used to confirm that any row with a **country_region** column value of **USA** also has a two-character value in the **state** column.</span></span> <span data-ttu-id="3feaf-130">這允許可在某一個位置上檢查多個條件。</span><span class="sxs-lookup"><span data-stu-id="3feaf-130">This allows for multiple conditions to be checked in one location.</span></span>  
  
 <span data-ttu-id="3feaf-131">CHECK 條件約束類似於 FOREIGN KEY 條件約束，用來控制放入資料行的值。</span><span class="sxs-lookup"><span data-stu-id="3feaf-131">CHECK constraints are similar to FOREIGN KEY constraints in that they control the values that are put in a column.</span></span> <span data-ttu-id="3feaf-132">其間的差異在於它們如何判定哪些值有效：FOREIGN KEY 條件約束從另一個資料表取得有效值清單，而 CHECK 條件約束則會從邏輯運算式來判定有效值。</span><span class="sxs-lookup"><span data-stu-id="3feaf-132">The difference is in how they determine which values are valid: FOREIGN KEY constraints obtain the list of valid values from another table, while CHECK constraints determine the valid values from a logical expression.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="3feaf-133">包括明確或隱含資料類型轉換的條件約束可能會導致某些作業失敗。</span><span class="sxs-lookup"><span data-stu-id="3feaf-133">Constraints that include implicit or explicit data type conversion may cause certain operations to fail.</span></span> <span data-ttu-id="3feaf-134">例如，在資料分割切換來源的資料表上所定義的此類條件約束，可能會導致 ALTER TABLE...SWITCH 作業失敗。</span><span class="sxs-lookup"><span data-stu-id="3feaf-134">For example, such constraints defined on tables that are sources of partition switching may cause an ALTER TABLE...SWITCH operation to fail.</span></span> <span data-ttu-id="3feaf-135">應避免在條件約束定義中進行資料類型轉換。</span><span class="sxs-lookup"><span data-stu-id="3feaf-135">Avoid data type conversion in constraint definitions.</span></span>  
  
### <a name="limitations-of-check-constraints"></a><span data-ttu-id="3feaf-136">CHECK 條件約束的限制</span><span class="sxs-lookup"><span data-stu-id="3feaf-136">Limitations of CHECK Constraints</span></span>  
 <span data-ttu-id="3feaf-137">CHECK 條件約束會拒絕評估為 FALSE 的值。</span><span class="sxs-lookup"><span data-stu-id="3feaf-137">CHECK constraints reject values that evaluate to FALSE.</span></span> <span data-ttu-id="3feaf-138">因為 Null 值會評估為 UNKNOWN，所以若其出現於運算式中，可能會覆寫條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-138">Because null values evaluate to UNKNOWN, their presence in expressions may override a constraint.</span></span> <span data-ttu-id="3feaf-139">例如，假設您將條件約束放在資料 `int` 行**MyColumn**上，指定**MyColumn**只能包含值 10 (**MyColumn = 10**) 。</span><span class="sxs-lookup"><span data-stu-id="3feaf-139">For example, suppose you place a constraint on an `int` column **MyColumn** specifying that **MyColumn** can contain only the value 10 (**MyColumn=10**).</span></span> <span data-ttu-id="3feaf-140">如果您將 NULL 值插入 **MyColumn**，則 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會插入 NULL 且不會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="3feaf-140">If you insert the value NULL into **MyColumn**, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] inserts NULL and does not return an error.</span></span>  
  
 <span data-ttu-id="3feaf-141">CHECK 條件約束會針對資料表中的所有資料列進行檢查，當檢查的條件不為 FALSE 時，會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="3feaf-141">A CHECK constraint returns TRUE when the condition it is checking is not FALSE for any row in the table.</span></span> <span data-ttu-id="3feaf-142">CHECK 條件約束可在資料列層級運作。</span><span class="sxs-lookup"><span data-stu-id="3feaf-142">A CHECK constraint works at the row level.</span></span> <span data-ttu-id="3feaf-143">如果剛建立的資料表沒有任何資料列，則這個資料表上的任何 CHECK 條件約束都將視為有效。</span><span class="sxs-lookup"><span data-stu-id="3feaf-143">If a table that has just been created does not have any rows, any CHECK constraint on this table is considered valid.</span></span> <span data-ttu-id="3feaf-144">這種情況可能會產生非預期結果，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3feaf-144">This situation can produce unexpected results, as in the following example.</span></span>  
  
```  
CREATE TABLE CheckTbl (col1 int, col2 int);  
GO  
CREATE FUNCTION CheckFnctn()  
RETURNS int  
AS   
BEGIN  
   DECLARE @retval int  
   SELECT @retval = COUNT(*) FROM CheckTbl  
   RETURN @retval  
END;  
GO  
ALTER TABLE CheckTbl  
ADD CONSTRAINT chkRowCount CHECK (dbo.CheckFnctn() >= 1 );  
GO  
```  
  
 <span data-ttu-id="3feaf-145">要加入的 `CHECK` 條件約束會指定 `CheckTbl`資料表中至少要有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="3feaf-145">The `CHECK` constraint being added specifies that there must be at least one row in table `CheckTbl`.</span></span> <span data-ttu-id="3feaf-146">不過，因為資料表中沒有任何資料列，能據以檢查這個條件約束的條件，所以 ALTER TABLE 陳述式會成功執行。</span><span class="sxs-lookup"><span data-stu-id="3feaf-146">However, because there are no rows in the table against which to check the condition of this constraint, the ALTER TABLE statement succeeds.</span></span>  
  
 <span data-ttu-id="3feaf-147">CHECK 條件約束不會在 DELETE 陳述式執行期間進行驗證。</span><span class="sxs-lookup"><span data-stu-id="3feaf-147">CHECK constraints are not validated during DELETE statements.</span></span> <span data-ttu-id="3feaf-148">因此，若在具有某些類型之 CHECK 條件約束的資料表上執行 DELETE 陳述式，可能會產生非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="3feaf-148">Therefore, executing DELETE statements on tables with certain types of check constraints may produce unexpected results.</span></span> <span data-ttu-id="3feaf-149">例如，考慮在 `CheckTbl`資料表上執行的下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="3feaf-149">For example, consider the following statements executed on table `CheckTbl`.</span></span>  
  
```  
INSERT INTO CheckTbl VALUES (10, 10);  
GO  
DELETE CheckTbl WHERE col1 = 10;  
```  
  
 <span data-ttu-id="3feaf-150">即使 `DELETE` 條件約束會指定資料表 `CHECK` 至少必須具有 `CheckTbl` 個資料列， `1` 陳述式也會執行成功。</span><span class="sxs-lookup"><span data-stu-id="3feaf-150">The `DELETE` statement succeeds, even though the `CHECK` constraint specifies that table `CheckTbl` must have at least `1` row.</span></span>  
  
##  <a name="related-tasks"></a><a name="Tasks"></a> <span data-ttu-id="3feaf-151">相關工作</span><span class="sxs-lookup"><span data-stu-id="3feaf-151">Related Tasks</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3feaf-152">如果資料表是要發佈以進行複寫，則必須使用 Transact-SQL 陳述式 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 或 SQL Server 管理物件 (SMO) 變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="3feaf-152">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="3feaf-153">使用 [資料表設計工具] 或 [資料庫圖表設計工具] 變更結構描述時，會嘗試卸除並重新建立資料表。</span><span class="sxs-lookup"><span data-stu-id="3feaf-153">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="3feaf-154">您無法卸除已發行的物件，因此結構描述變更將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3feaf-154">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
|<span data-ttu-id="3feaf-155">Task</span><span class="sxs-lookup"><span data-stu-id="3feaf-155">Task</span></span>|<span data-ttu-id="3feaf-156">主題</span><span class="sxs-lookup"><span data-stu-id="3feaf-156">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="3feaf-157">描述如何建立唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-157">Describes how to create a unique constraint.</span></span>|[<span data-ttu-id="3feaf-158">建立唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-158">Create Unique Constraints</span></span>](../tables/create-unique-constraints.md)|  
|<span data-ttu-id="3feaf-159">描述如何修改唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-159">Describes how to modify a unique constraint.</span></span>|[<span data-ttu-id="3feaf-160">修改唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-160">Modify Unique Constraints</span></span>](../tables/modify-unique-constraints.md)|  
|<span data-ttu-id="3feaf-161">描述如何刪除唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-161">Describes how to delete a unique constraint.</span></span>|[<span data-ttu-id="3feaf-162">刪除唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-162">Delete Unique Constraints</span></span>](../tables/delete-unique-constraints.md)|  
|<span data-ttu-id="3feaf-163">描述如何在複寫代理程式在資料表中插入或更新資料時，停用檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-163">Describes how to disable a check constraint when a replication agent inserts or updates data in your table.</span></span>|[<span data-ttu-id="3feaf-164">停用複寫的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-164">Disable Check Constraints for Replication</span></span>](../tables/disable-check-constraints-for-replication.md)|  
|<span data-ttu-id="3feaf-165">描述如何在加入資料表資料、更新資料表資料或刪除資料表資料時，停用檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-165">Describes how to disable a check constraint when data is added to, updated in, or deleted from a table.</span></span>|[<span data-ttu-id="3feaf-166">停用 INSERT 與 UPDATE 陳述式的檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-166">Disable Check Constraints with INSERT and UPDATE Statements</span></span>](../tables/disable-check-constraints-with-insert-and-update-statements.md)|  
|<span data-ttu-id="3feaf-167">描述如何變更條件約束運算式或啟用或停用特定條件之條件約束的選項。</span><span class="sxs-lookup"><span data-stu-id="3feaf-167">Describes how to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>|[<span data-ttu-id="3feaf-168">修改檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-168">Modify Check Constraints</span></span>](../tables/modify-check-constraints.md)|  
|<span data-ttu-id="3feaf-169">描述如何刪除檢查條件約束。</span><span class="sxs-lookup"><span data-stu-id="3feaf-169">Describes how to delete a check constraint.</span></span>|[<span data-ttu-id="3feaf-170">刪除檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-170">Delete Check Constraints</span></span>](../tables/delete-check-constraints.md)|  
|<span data-ttu-id="3feaf-171">描述如何檢視檢查條件約束的屬性。</span><span class="sxs-lookup"><span data-stu-id="3feaf-171">Describes how to view the properties of a check constraint.</span></span>|[<span data-ttu-id="3feaf-172">唯一條件約束與檢查條件約束</span><span class="sxs-lookup"><span data-stu-id="3feaf-172">Unique Constraints and Check Constraints</span></span>](../tables/unique-constraints-and-check-constraints.md)|  
  
  
