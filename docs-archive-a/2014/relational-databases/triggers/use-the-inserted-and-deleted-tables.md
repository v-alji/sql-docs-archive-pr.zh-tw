---
title: 使用插入或刪除的資料表 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- inserted tables
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- INSTEAD OF triggers
- deleted tables
- INSERT statement [SQL Server], DML triggers
- DML triggers, deleted or inserted tables
ms.assetid: ed84567f-7b91-4b44-b5b2-c400bda4590d
author: rothja
ms.author: jroth
ms.openlocfilehash: facc534177113bd93e56e50fca3ae14c3e6b2cfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606115"
---
# <a name="use-the-inserted-and-deleted-tables"></a><span data-ttu-id="88795-102">使用插入或刪除的資料表</span><span class="sxs-lookup"><span data-stu-id="88795-102">Use the inserted and deleted Tables</span></span>
  <span data-ttu-id="88795-103">DML 觸發程序陳述式使用兩個特殊的資料表：已刪除的資料表和已插入的資料表。</span><span class="sxs-lookup"><span data-stu-id="88795-103">DML trigger statements use two special tables: the deleted table and the inserted tables.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="88795-104">會自動建立及管理這些資料表。</span><span class="sxs-lookup"><span data-stu-id="88795-104">automatically creates and manages these tables.</span></span> <span data-ttu-id="88795-105">您可以使用這些暫存、常駐記憶體的資料表來測試某些資料修改的效果，以及設定 DML 觸發程序動作的條件。</span><span class="sxs-lookup"><span data-stu-id="88795-105">You can use these temporary, memory-resident tables to test the effects of certain data modifications and to set conditions for DML trigger actions.</span></span> <span data-ttu-id="88795-106">您無法直接修改這些資料表的資料，或是在這些資料表上執行資料定義語言 (DDL) 作業，例如 CREATE INDEX。</span><span class="sxs-lookup"><span data-stu-id="88795-106">You cannot directly modify the data in the tables or perform data definition language (DDL) operations on the tables, such as CREATE INDEX.</span></span>  
  
 <span data-ttu-id="88795-107">在 DML 觸發程序中，inserted 和 deleted 資料表主要是用來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="88795-107">In DML triggers, the inserted and deleted tables are primarily used to perform the following:</span></span>  
  
-   <span data-ttu-id="88795-108">擴充資料表之間的參考完整性。</span><span class="sxs-lookup"><span data-stu-id="88795-108">Extend referential integrity between tables.</span></span>  
  
-   <span data-ttu-id="88795-109">在檢視底下的基底資料表中插入或更新資料。</span><span class="sxs-lookup"><span data-stu-id="88795-109">Insert or update data in base tables underlying a view.</span></span>  
  
-   <span data-ttu-id="88795-110">測試錯誤，並根據錯誤採取動作。</span><span class="sxs-lookup"><span data-stu-id="88795-110">Test for errors and take action based on the error.</span></span>  
  
-   <span data-ttu-id="88795-111">尋找資料修改前後之資料表狀態的差異，並依據這些差異採取動作。</span><span class="sxs-lookup"><span data-stu-id="88795-111">Find the difference between the state of a table before and after a data modification and take actions based on that difference.</span></span>  
  
 <span data-ttu-id="88795-112">deleted 資料表會儲存被 DELETE 及 UPDATE 陳述式影響的資料列副本。</span><span class="sxs-lookup"><span data-stu-id="88795-112">The deleted table stores copies of the affected rows during DELETE and UPDATE statements.</span></span> <span data-ttu-id="88795-113">在執行 DELETE 或 UPDATE 陳述式時，資料列會從觸發程序資料表刪除，並傳送到 deleted 資料表。</span><span class="sxs-lookup"><span data-stu-id="88795-113">During the execution of a DELETE or UPDATE statement, rows are deleted from the trigger table and transferred to the deleted table.</span></span> <span data-ttu-id="88795-114">deleted 資料表及其觸發程序資料表兩者通常不會有相同的資料列。</span><span class="sxs-lookup"><span data-stu-id="88795-114">The deleted table and the trigger table ordinarily have no rows in common.</span></span>  
  
 <span data-ttu-id="88795-115">inserted 資料表會儲存被 INSERT 及 UPDATE 陳述式影響的資料列副本。</span><span class="sxs-lookup"><span data-stu-id="88795-115">The inserted table stores copies of the affected rows during INSERT and UPDATE statements.</span></span> <span data-ttu-id="88795-116">在插入或更新交易期間，新的資料列會同時加入 inserted 資料表和觸發程序資料表。</span><span class="sxs-lookup"><span data-stu-id="88795-116">During an insert or update transaction, new rows are added to both the inserted table and the trigger table.</span></span> <span data-ttu-id="88795-117">inserted 資料表中的資料列即為觸發程序資料表中新資料列的副本。</span><span class="sxs-lookup"><span data-stu-id="88795-117">The rows in the inserted table are copies of the new rows in the trigger table.</span></span>  
  
 <span data-ttu-id="88795-118">更新交易就像是刪除後再插入的動作；首先，舊資料列被複製到 deleted 資料表，接著將新資料列再複製到觸發程序資料表以及 inserted 資料表。</span><span class="sxs-lookup"><span data-stu-id="88795-118">An update transaction is similar to a delete operation followed by an insert operation; the old rows are copied to the deleted table first, and then the new rows are copied to the trigger table and to the inserted table.</span></span>  
  
 <span data-ttu-id="88795-119">設定觸發程序的條件時，可以適當地利用 inserted 與 deleted 資料表設定引發觸發條件的動作。</span><span class="sxs-lookup"><span data-stu-id="88795-119">When you set trigger conditions, use the inserted and deleted tables appropriately for the action that fired the trigger.</span></span> <span data-ttu-id="88795-120">雖然參考 deleted 資料表來測試 INSERT 陳述式或是參考 inserted 資料表測試 DELETE 陳述式時，並不會有任何錯誤發生，但在這種情形下，觸發程序測試資料表內將不會有任何資料列產生。</span><span class="sxs-lookup"><span data-stu-id="88795-120">Although referencing the deleted table when testing an INSERT or the inserted table when testing a DELETE does not cause any errors, these trigger test tables do not contain any rows in these cases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88795-121">若觸發程序動作依據被修改的資料列數目來決定啟動與否時，則可利用對多資料列資料修改 (依據 SELECT 陳述式的 INSERT、DELETE 或 UPDATE) 的測試 (如 @@ROWCOUNT 的檢查)，以決定執行何者動作。</span><span class="sxs-lookup"><span data-stu-id="88795-121">If trigger actions depend on the number of rows a data modification effects, use tests (such as an examination of @@ROWCOUNT) for multirow data modifications (an INSERT, DELETE, or UPDATE based on a SELECT statement), and take appropriate actions.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="88795-122">在使用 AFTER 觸發程序時，不允許參考 inserted 和 deleted 資料表中的 `text`、`ntext` 或 `image` 資料行。</span><span class="sxs-lookup"><span data-stu-id="88795-122">does not allow for `text`, `ntext`, or `image` column references in the inserted and deleted tables for AFTER triggers.</span></span> <span data-ttu-id="88795-123">但還是包含這些資料類型，僅做為回溯相容性的目的使用。</span><span class="sxs-lookup"><span data-stu-id="88795-123">However, these data types are included for backward compatibility purposes only.</span></span> <span data-ttu-id="88795-124">對於大量資料，較佳的儲存方式是使用 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="88795-124">The preferred storage for large data is to use the `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types.</span></span> <span data-ttu-id="88795-125">AFTER 和 INSTEAD OF 觸發程序都支援 inserted 和 deleted 資料表中的 `varchar(max)`、`nvarchar(max)` 和 `varbinary(max)` 資料。</span><span class="sxs-lookup"><span data-stu-id="88795-125">Both AFTER and INSTEAD OF triggers support `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data in the inserted and deleted tables.</span></span> <span data-ttu-id="88795-126">如需詳細資訊，請參閱 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="88795-126">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
 <span data-ttu-id="88795-127">**在觸發程序中使用 inserted 資料表來強制執行商務規則的範例**</span><span class="sxs-lookup"><span data-stu-id="88795-127">**An Example of Using the inserted Table in a Trigger to Enforce Business Rules**</span></span>  
  
 <span data-ttu-id="88795-128">由於 CHECK 條件約束只能參考定義了資料行層級或資料表層級條件約束的資料行，任何跨資料表的條件約束 (這裡是商務規則) 都必須定義成觸發程序。</span><span class="sxs-lookup"><span data-stu-id="88795-128">Because CHECK constraints can reference only the columns on which the column-level or table-level constraint is defined, any cross-table constraints (in this case, business rules) must be defined as triggers.</span></span>  
  
 <span data-ttu-id="88795-129">下列範例會建立一個 DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="88795-129">The following example creates a DML trigger.</span></span> <span data-ttu-id="88795-130">當試圖在 `PurchaseOrderHeader` 資料表中插入新的採購單時，這個觸發程序會檢查確認供應商的信用等級良好。</span><span class="sxs-lookup"><span data-stu-id="88795-130">This trigger checks to make sure the credit rating for the vendor is good when an attempt is made to insert a new purchase order into the `PurchaseOrderHeader` table.</span></span> <span data-ttu-id="88795-131">若要取得對應至剛插入之採購單的供應商信用等級，您必須參考 `Vendor` 資料表，而此資料表也必須與 inserted 資料表聯結。</span><span class="sxs-lookup"><span data-stu-id="88795-131">To obtain the credit rating of the vendor corresponding to the purchase order that was just inserted, the `Vendor` table must be referenced and joined with the inserted table.</span></span> <span data-ttu-id="88795-132">如果信用等級太低，將會顯示訊息，且不會執行插入動作。</span><span class="sxs-lookup"><span data-stu-id="88795-132">If the credit rating is too low, a message is displayed and the insertion does not execute.</span></span> <span data-ttu-id="88795-133">請注意此範例不允許進行多資料列資料修改。</span><span class="sxs-lookup"><span data-stu-id="88795-133">Note that this example does not allow for multirow data modifications.</span></span> <span data-ttu-id="88795-134">如需詳細資訊，請參閱 [建立 DML 觸發程序以處理多重資料列](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md)。</span><span class="sxs-lookup"><span data-stu-id="88795-134">For more information, see [Create DML Triggers to Handle Multiple Rows of Data](../triggers/create-dml-triggers-to-handle-multiple-rows-of-data.md).</span></span>  
  
 [!code-sql[TriggerDDL#CreateTrigger3](../../snippets/tsql/SQL14/tsql/triggerddl/transact-sql/snippet_create_alter_drop_trigger.sql#createtrigger3)]  
  
## <a name="using-the-inserted-and-deleted-tables-in-instead-of-triggers"></a><span data-ttu-id="88795-135">在 INSTEAD OF 觸發程序中使用已插入與已刪除的資料表</span><span class="sxs-lookup"><span data-stu-id="88795-135">Using the inserted and deleted Tables in INSTEAD OF Triggers</span></span>  
 <span data-ttu-id="88795-136">傳遞到依據資料表定義的 INSTEAD OF 觸發程序之 inserted 及 deleted 資料表，會與傳遞到 AFTER 觸發程序的 inserted 及 deleted 資料表遵循相同的規則。</span><span class="sxs-lookup"><span data-stu-id="88795-136">The inserted and deleted tables passed to INSTEAD OF triggers defined on tables follow the same rules as the inserted and deleted tables passed to AFTER triggers.</span></span> <span data-ttu-id="88795-137">inserted 及 deleted 資料表的格式，與據以定義 INSTEAD OF 觸發程序的資料表格式相同。</span><span class="sxs-lookup"><span data-stu-id="88795-137">The format of the inserted and deleted tables is the same as the format of the table on which the INSTEAD OF trigger is defined.</span></span> <span data-ttu-id="88795-138">inserted 及 deleted 資料表中的每一資料行，都會直接對應到基底資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="88795-138">Each column in the inserted and deleted tables maps directly to a column in the base table.</span></span>  
  
 <span data-ttu-id="88795-139">下列規則是有關參考含 INSTEAD OF 觸發程序之資料表的 INSERT 或 UPDATE 陳述式何時必須提供資料行值，即使資料表不含 INSTEAD OF 觸發程序時也一樣：</span><span class="sxs-lookup"><span data-stu-id="88795-139">The following rules regarding when an INSERT or UPDATE statement referencing a table with an INSTEAD OF trigger must supply values for columns are the same as if the table did not have an INSTEAD OF trigger:</span></span>  
  
-   <span data-ttu-id="88795-140">無法為計算的資料行或資料類型為 `timestamp` 的資料行指定值。</span><span class="sxs-lookup"><span data-stu-id="88795-140">Values cannot be specified for computed columns or columns with a `timestamp` data type.</span></span>  
  
-   <span data-ttu-id="88795-141">除非資料表的 IDENTITY_INSERT 是 ON，否則無法為帶有 IDENTITY 屬性的資料表指定值。</span><span class="sxs-lookup"><span data-stu-id="88795-141">Values cannot be specified for columns with an IDENTITY property, unless IDENTITY_INSERT is ON for that table.</span></span> <span data-ttu-id="88795-142">當 IDENTITY_INSERT 為 ON 時，INSERT 陳述式必須提供一個值。</span><span class="sxs-lookup"><span data-stu-id="88795-142">When IDENTITY_INSERT is ON, INSERT statements must supply a value.</span></span>  
  
-   <span data-ttu-id="88795-143">INSERT 陳述式必須為不含 DEFAULT 條件約束的所有 NOT NULL 資料行提供值。</span><span class="sxs-lookup"><span data-stu-id="88795-143">INSERT statements must supply values for all NOT NULL columns that do not have DEFAULT constraints.</span></span>  
  
-   <span data-ttu-id="88795-144">除了計算、識別或 `timestamp` 資料行之外，只要是允許 Null 值的任意資料行，或含 DEFAULT 的任何 NOT NULL 資料行，其值都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="88795-144">For any columns except computed, identity, or `timestamp` columns, values are optional for any column that allows nulls, or any NOT NULL column that has a DEFAULT definition.</span></span>  
  
 <span data-ttu-id="88795-145">當 INSERT、UPDATE 或 DELETE 陳述式參考含有 INSTEAD OF 觸發程序的檢視時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會呼叫觸發程序，而不會直接對任何資料表採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="88795-145">When an INSERT, UPDATE, or DELETE statement references a view that has an INSTEAD OF trigger, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] calls the trigger instead of taking any direct action against any table.</span></span> <span data-ttu-id="88795-146">觸發程序必須使用 inserted 及 deleted 資料表中的資訊，來建立實作基底資料表中要求的動作所需的陳述式，即使為檢視所建立的 inserted 及 deleted 資料表中的資訊格式與基底資料表中的資料格式並不相同也一樣。</span><span class="sxs-lookup"><span data-stu-id="88795-146">The trigger must use the information presented in the inserted and deleted tables to build any statements required to implement the requested action in the base tables, even when the format of the information in the inserted and deleted tables built for the view is different from the format of the data in the base tables.</span></span>  
  
 <span data-ttu-id="88795-147">傳遞給定義在檢視上 INSTEAD OF 觸發程序的 inserted 及 deleted 資料表格式，必須與針對檢視定義的 SELECT 陳述式之選取清單相符。</span><span class="sxs-lookup"><span data-stu-id="88795-147">The format of the inserted and deleted tables passed to an INSTEAD OF trigger defined on a view matches the select list of the SELECT statement defined for the view.</span></span> <span data-ttu-id="88795-148">例如：</span><span class="sxs-lookup"><span data-stu-id="88795-148">For example:</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
CREATE VIEW dbo.EmployeeNames (BusinessEntityID, LName, FName)  
AS  
SELECT e.BusinessEntityID, p.LastName, p.FirstName  
FROM HumanResources.Employee AS e   
JOIN Person.Person AS p  
ON e.BusinessEntityID = p.BusinessEntityID;  
```  
  
 <span data-ttu-id="88795-149">這個檢視的結果集有三個資料行：一個 `int` 資料行和兩個 `nvarchar` 資料行。</span><span class="sxs-lookup"><span data-stu-id="88795-149">The result set for this view has three columns: an `int` column and two `nvarchar` columns.</span></span> <span data-ttu-id="88795-150">傳遞給在檢視表上定義之 INSTEAD OF 觸發程序的 inserted 和 deleted 資料表，也必須有名稱為 `BusinessEntityID` 的 `int` 資料行、名稱為 `LName` 的 `nvarchar` 資料行，以及名稱為 `FName` 的 `nvarchar` 資料行。</span><span class="sxs-lookup"><span data-stu-id="88795-150">The inserted and deleted tables passed to an INSTEAD OF trigger defined on the view also have an `int` column named `BusinessEntityID`, an `nvarchar` column named `LName`, and an `nvarchar` column named `FName`.</span></span>  
  
 <span data-ttu-id="88795-151">檢視的選取清單也可以包含不直接對應到單一基底資料表資料行的運算式。</span><span class="sxs-lookup"><span data-stu-id="88795-151">The select list of a view can also contain expressions that do not directly map to a single base-table column.</span></span> <span data-ttu-id="88795-152">有些檢視運算式，例如條件約束或函數引動過程，無法參考任何資料行且可以被忽略。</span><span class="sxs-lookup"><span data-stu-id="88795-152">Some view expressions, such as a constant or function invocation, may not reference any columns and can be ignored.</span></span> <span data-ttu-id="88795-153">複雜運算式可以參考多個資料行，但 inserted 及 deleted 資料表的每個插入資料列只能有一個值。</span><span class="sxs-lookup"><span data-stu-id="88795-153">Complex expressions can reference multiple columns, yet the inserted and deleted tables have only one value for each inserted row.</span></span> <span data-ttu-id="88795-154">同樣的原則亦適用於檢視中的簡單運算式，前提是它們參考的計算資料行含有複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="88795-154">The same issues apply to simple expressions in a view if they reference a computed column that has a complex expression.</span></span> <span data-ttu-id="88795-155">檢視的 INSTEAD OF 觸發程序必須處理這些類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="88795-155">An INSTEAD OF trigger on the view must handle these types of expressions.</span></span>  
  
  
