---
title: 使用資料行集 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, column sets
- column sets
ms.assetid: a4f9de95-dc8f-4ad8-b957-137e32bfa500
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9cb496137c3986b78a55862e434c153d354a42ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606711"
---
# <a name="use-column-sets"></a><span data-ttu-id="1a28f-102">使用資料行集</span><span class="sxs-lookup"><span data-stu-id="1a28f-102">Use Column Sets</span></span>
  <span data-ttu-id="1a28f-103">使用疏鬆資料行的資料表可以指定資料行集，以傳回資料表中的所有疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-103">Tables that use sparse columns can designate a column set to return all sparse columns in the table.</span></span> <span data-ttu-id="1a28f-104">資料行集是不具類型的 XML 表示，可將資料表的所有疏鬆資料行結合到結構化輸出中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-104">A column set is an untyped XML representation that combines all the sparse columns of a table into a structured output.</span></span> <span data-ttu-id="1a28f-105">資料行集類似於計算資料行，因為資料行集並未實際儲存在資料表中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-105">A column set is like a calculated column in that the column set is not physically stored in the table.</span></span> <span data-ttu-id="1a28f-106">資料行集與計算資料行不同的地方在於資料行集可直接更新。</span><span class="sxs-lookup"><span data-stu-id="1a28f-106">A column set differs from a calculated column in that the column set is directly updatable.</span></span>  
  
 <span data-ttu-id="1a28f-107">當資料表中的資料行數目很大，而且個別操作資料行很麻煩時，您應該考慮使用資料行集。</span><span class="sxs-lookup"><span data-stu-id="1a28f-107">You should consider using column sets when the number of columns in a table is large, and operating on them individually is cumbersome.</span></span> <span data-ttu-id="1a28f-108">當應用程式在擁有許多資料行的資料表上使用資料行集來選取及插入資料時，可能會看到一些效能上的改善。</span><span class="sxs-lookup"><span data-stu-id="1a28f-108">Applications might see some performance improvement when they select and insert data by using column sets on tables that have lots of columns.</span></span> <span data-ttu-id="1a28f-109">但是，當資料表中的資料行上定義許多索引時，資料行集的效能可能會降低。</span><span class="sxs-lookup"><span data-stu-id="1a28f-109">However, the performance of column sets can be reduced when many indexes are defined on the columns in the table.</span></span> <span data-ttu-id="1a28f-110">這是因為執行計畫所需的記憶體數量增加的緣故。</span><span class="sxs-lookup"><span data-stu-id="1a28f-110">This is because the amount of memory that is required for an execution plan increases.</span></span>  
  
 <span data-ttu-id="1a28f-111">若要定義資料行集，請在 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 或 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 陳述式中使用 *<資料行集名稱>* FOR ALL_SPARSE_COLUMNS 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1a28f-111">To define a column set, use the *<column_set_name>* FOR ALL_SPARSE_COLUMNS keywords in the[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
## <a name="guidelines-for-using-column-sets"></a><span data-ttu-id="1a28f-112">使用資料行集的指導方針</span><span class="sxs-lookup"><span data-stu-id="1a28f-112">Guidelines for Using Column Sets</span></span>  
 <span data-ttu-id="1a28f-113">使用資料行集時，請考慮下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="1a28f-113">When you use column sets, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="1a28f-114">可以在相同的陳述式中加入疏鬆資料行和資料行集。</span><span class="sxs-lookup"><span data-stu-id="1a28f-114">Sparse columns and a column set can be added as part of the same statement.</span></span>  
  
-   <span data-ttu-id="1a28f-115">資料行集無法變更。</span><span class="sxs-lookup"><span data-stu-id="1a28f-115">The column set cannot be changed.</span></span> <span data-ttu-id="1a28f-116">若要變更資料行集，您必須先刪除資料行集然後再重新建立。</span><span class="sxs-lookup"><span data-stu-id="1a28f-116">To change a column set, you must delete and re-create the column set.</span></span>  
  
-   <span data-ttu-id="1a28f-117">如果資料表已包含疏鬆資料行，資料行集無法加入該資料表中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-117">A column set cannot be added to a table if that table already contains sparse columns.</span></span>  
  
-   <span data-ttu-id="1a28f-118">如果資料表未包含任何疏鬆資料行，資料行集便可加入該資料表中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-118">A column set can be added to a table that does not include any sparse columns.</span></span> <span data-ttu-id="1a28f-119">如果之後將疏鬆資料行加入此資料表，這些資料行將會出現在資料行集中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-119">If sparse columns are later added to the table, they will appear in the column set.</span></span>  
  
-   <span data-ttu-id="1a28f-120">一個資料表只能有一個資料行集。</span><span class="sxs-lookup"><span data-stu-id="1a28f-120">Only one column set is allowed per table.</span></span>  
  
-   <span data-ttu-id="1a28f-121">資料行集為選擇性，而且不必使用疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-121">A column set is optional and is not required to use sparse columns.</span></span>  
  
-   <span data-ttu-id="1a28f-122">資料行集上不能定義條件約束或預設值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-122">Constraints or default values cannot be defined on a column set.</span></span>  
  
-   <span data-ttu-id="1a28f-123">計算資料行不能包含資料行集資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-123">Computed columns cannot contain column set columns.</span></span>  
  
-   <span data-ttu-id="1a28f-124">包含資料行集的資料表上不支援分散式查詢。</span><span class="sxs-lookup"><span data-stu-id="1a28f-124">Distributed queries are not supported on tables that contain column sets.</span></span>  
  
-   <span data-ttu-id="1a28f-125">複寫不支援資料行集。</span><span class="sxs-lookup"><span data-stu-id="1a28f-125">Replication does not support column sets.</span></span>  
  
-   <span data-ttu-id="1a28f-126">異動資料擷取不支援資料行集。</span><span class="sxs-lookup"><span data-stu-id="1a28f-126">Change data capture does not support column sets.</span></span>  
  
-   <span data-ttu-id="1a28f-127">資料行集不能是任何索引類型的一部分。</span><span class="sxs-lookup"><span data-stu-id="1a28f-127">A column set cannot be part of any kind of index.</span></span> <span data-ttu-id="1a28f-128">其中包括 XML 索引、全文檢索索引和索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="1a28f-128">This includes XML indexes, full-text indexes, and indexed views.</span></span> <span data-ttu-id="1a28f-129">資料行集不能當做任何索引中併入的資料行來加入。</span><span class="sxs-lookup"><span data-stu-id="1a28f-129">A column set cannot be added as an included column in any index.</span></span>  
  
-   <span data-ttu-id="1a28f-130">資料行集不能用於篩選索引的篩選運算式中或篩選的統計資料中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-130">A column set cannot be used in the filter expression of a filtered index or filtered statistics.</span></span>  
  
-   <span data-ttu-id="1a28f-131">當檢視表包含資料行集時，此資料行集會當做 XML 資料行出現在檢視表中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-131">When a view includes a column set, the column set appears in the view as an XML column.</span></span>  
  
-   <span data-ttu-id="1a28f-132">資料行集不能併入索引檢視表定義中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-132">A column set cannot be included in an indexed view definition.</span></span>  
  
-   <span data-ttu-id="1a28f-133">當資料分割檢視依據名稱指定疏鬆資料行時，如果資料分割檢視包含了有包含資料行集的資料表，將可以進行更新。</span><span class="sxs-lookup"><span data-stu-id="1a28f-133">Partitioned views that include tables that contain column sets are updatable when the partitioned view specifies the sparse columns by name.</span></span> <span data-ttu-id="1a28f-134">如果資料分割檢視參考資料行集，將無法更新。</span><span class="sxs-lookup"><span data-stu-id="1a28f-134">A partitioned view is not updatable when it references the column set.</span></span>  
  
-   <span data-ttu-id="1a28f-135">不允許參考資料行集的查詢通知。</span><span class="sxs-lookup"><span data-stu-id="1a28f-135">Query notifications that refer to column sets are not permitted.</span></span>  
  
-   <span data-ttu-id="1a28f-136">XML 資料的大小限制為 2 GB。</span><span class="sxs-lookup"><span data-stu-id="1a28f-136">XML data has a size limit of 2 GB.</span></span> <span data-ttu-id="1a28f-137">如果資料列中所有非 null 疏鬆資料行的結合資料超出此限制，查詢或 DML 作業將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a28f-137">If the combined data of all the nonnull sparse columns in a row exceeds this limit, the query or DML operation will produce an error.</span></span>  
  
-   <span data-ttu-id="1a28f-138">如需 COLUMNS_UPDATED 函數傳回之資料的資訊，請參閱 [使用疏鬆資料行](use-sparse-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="1a28f-138">For information about the data that is returned by the COLUMNS_UPDATED function, see [Use Sparse Columns](use-sparse-columns.md).</span></span>  
  
## <a name="guidelines-for-selecting-data-from-a-column-set"></a><span data-ttu-id="1a28f-139">從資料行集內選取資料的指導方針</span><span class="sxs-lookup"><span data-stu-id="1a28f-139">Guidelines for Selecting Data from a Column Set</span></span>  
 <span data-ttu-id="1a28f-140">當您從資料行集選取資料時，請考量以下的指導方針：</span><span class="sxs-lookup"><span data-stu-id="1a28f-140">Consider the following guidelines for selecting data from a column set:</span></span>  
  
-   <span data-ttu-id="1a28f-141">在概念上，資料行集是一種可更新的 XML 計算資料行，可將一組基礎關聯式資料行彙總成單一 XML 表示。</span><span class="sxs-lookup"><span data-stu-id="1a28f-141">Conceptually, a column set is a type of updatable, computed XML column that aggregates a set of underlying relational columns into a single XML representation.</span></span> <span data-ttu-id="1a28f-142">此資料行集只支援 ALL_SPARSE_COLUMNS 屬性，</span><span class="sxs-lookup"><span data-stu-id="1a28f-142">The column set only supports the ALL_SPARSE_COLUMNS property.</span></span> <span data-ttu-id="1a28f-143">這個屬性是用來從特定資料列的所有疏鬆資料行中彙總所有非 null 值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-143">This property is used to aggregate all nonnull values from all sparse columns for a particular row.</span></span>  
  
-   <span data-ttu-id="1a28f-144">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 資料表編輯器中，資料行集會顯示為可編輯的 XML 欄位。</span><span class="sxs-lookup"><span data-stu-id="1a28f-144">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] table editor, column sets are displayed as an editable XML field.</span></span> <span data-ttu-id="1a28f-145">請使用以下格式定義資料行集：</span><span class="sxs-lookup"><span data-stu-id="1a28f-145">Define column sets in the format:</span></span>  
  
    ```  
    <column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...  
    ```  
  
     <span data-ttu-id="1a28f-146">資料行集的值範例如下：</span><span class="sxs-lookup"><span data-stu-id="1a28f-146">Examples of column set values are as follows:</span></span>  
  
    -   `<sparseProp1>10</sparseProp1><sparseProp3>20</sparseProp3>`  
  
    -   `<DocTitle>Bicycle Parts List</DocTitle><Region>West</Region>`  
  
-   <span data-ttu-id="1a28f-147">資料行集的 XML 表示中會省略包含 null 值的疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-147">Sparse columns that contain null values are omitted from the XML representation for the column set.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="1a28f-148">加入資料行集會變更 SELECT \* 查詢的行為</span><span class="sxs-lookup"><span data-stu-id="1a28f-148">Adding a column set changes the behavior of SELECT \* queries.</span></span> <span data-ttu-id="1a28f-149">此查詢會將資料行集當做 XML 資料行傳回，而且不會傳回個別的疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-149">The query will return the column set as an XML column and not return the individual sparse columns.</span></span> <span data-ttu-id="1a28f-150">結構描述設計人員和軟體開發人員必須要小心，不能破壞現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1a28f-150">Schema designers and software developers must be careful not to break existing applications.</span></span>  
  
## <a name="inserting-or-modifying-data-in-a-column-set"></a><span data-ttu-id="1a28f-151">在資料行集內插入或修改資料</span><span class="sxs-lookup"><span data-stu-id="1a28f-151">Inserting or Modifying Data in a Column Set</span></span>  
 <span data-ttu-id="1a28f-152">若要執行疏鬆資料行的資料操作，可以使用個別資料行的名稱，或是參考資料行集的名稱，以及使用資料行集的 XML 格式來指定資料行集的值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-152">Data manipulation of a sparse column can be performed by using the name of the individual columns, or by referencing the name of the column set and specifying the values of the column set by using the XML format of the column set.</span></span> <span data-ttu-id="1a28f-153">疏鬆資料行可依任何順序出現在 XML 資料行中。</span><span class="sxs-lookup"><span data-stu-id="1a28f-153">Sparse columns can appear in any order in the XML column.</span></span>  
  
 <span data-ttu-id="1a28f-154">當您使用 XML 資料行集來插入或更新疏鬆資料行值時，插入基礎疏鬆資料行內的值會從 `xml` 資料類型隱含地轉換。</span><span class="sxs-lookup"><span data-stu-id="1a28f-154">When sparse column values are inserted or updated by using the XML column set, the values that are inserted into the underlying sparse columns are implicitly converted from the `xml` data type.</span></span> <span data-ttu-id="1a28f-155">如果是數值資料行，數值資料行之 XML 內的空白值會轉換成空白字串。</span><span class="sxs-lookup"><span data-stu-id="1a28f-155">In the case of numeric columns, a blank value in the XML for the numeric column converts to an empty string.</span></span> <span data-ttu-id="1a28f-156">這樣會將零插入數值資料行中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1a28f-156">This causes a zero to be inserted into the numeric column as shown in the following example.</span></span>  
  
```  
CREATE TABLE t (i int SPARSE, cs xml column_set FOR ALL_SPARSE_COLUMNS);  
GO  
INSERT t(cs) VALUES ('<i/>');  
GO  
SELECT i FROM t;  
GO  
```  
  
 <span data-ttu-id="1a28f-157">在此範例中， `i`資料行未指定任何值，但是插入了 `0` 的值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-157">In this example, no value was specified for the column `i`, but the value `0` was inserted.</span></span>  
  
## <a name="using-the-sql_variant-data-type"></a><span data-ttu-id="1a28f-158">使用 sql_variant 資料類型</span><span class="sxs-lookup"><span data-stu-id="1a28f-158">Using the sql_variant Data Type</span></span>  
 <span data-ttu-id="1a28f-159">`sql_variant` 資料類型可以儲存多種不同的資料類型，例如 `int`、`char` 和 `date`。</span><span class="sxs-lookup"><span data-stu-id="1a28f-159">The `sql_variant` date type can store multiple different data types, such as `int`, `char`, and `date`.</span></span> <span data-ttu-id="1a28f-160">資料行集會將與 `sql_variant` 值相關的資料類型資訊 (如地區設定、有效位數和地區設定資訊) 輸出為產生之 XML 資料行內的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a28f-160">Column sets output the data type information such as scale, precision, and locale information that is associated with a `sql_variant` value as attributes in the generated XML column.</span></span> <span data-ttu-id="1a28f-161">如果您嘗試在自訂產生的 XML 陳述式內提供這些屬性當做資料行集上插入或更新作業的輸入，某些屬性會是必要的，而且其中一些屬性會指派預設值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-161">If you try to provide these attributes in a custom-generated XML statement as an input for an insert or update operation on a column set, some of these attributes are required and some of them are assigned a default value.</span></span> <span data-ttu-id="1a28f-162">下表列出當未提供值時，伺服器所產生的資料類型和預設值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-162">The following table lists the data types and the default values that the server generates when the value is not provided.</span></span>  
  
|<span data-ttu-id="1a28f-163">資料類型</span><span class="sxs-lookup"><span data-stu-id="1a28f-163">Data type</span></span>|<span data-ttu-id="1a28f-164">localeID\*</span><span class="sxs-lookup"><span data-stu-id="1a28f-164">localeID\*</span></span>|<span data-ttu-id="1a28f-165">sqlCompareOptions</span><span class="sxs-lookup"><span data-stu-id="1a28f-165">sqlCompareOptions</span></span>|<span data-ttu-id="1a28f-166">sqlCollationVersion</span><span class="sxs-lookup"><span data-stu-id="1a28f-166">sqlCollationVersion</span></span>|<span data-ttu-id="1a28f-167">SqlSortId</span><span class="sxs-lookup"><span data-stu-id="1a28f-167">SqlSortId</span></span>|<span data-ttu-id="1a28f-168">最大長度</span><span class="sxs-lookup"><span data-stu-id="1a28f-168">Maximum length</span></span>|<span data-ttu-id="1a28f-169">Precision</span><span class="sxs-lookup"><span data-stu-id="1a28f-169">Precision</span></span>|<span data-ttu-id="1a28f-170">調整</span><span class="sxs-lookup"><span data-stu-id="1a28f-170">Scale</span></span>|  
|---------------|----------------|-----------------------|-------------------------|---------------|--------------------|---------------|-----------|  
|<span data-ttu-id="1a28f-171">`char`, `varchar`, `binary`</span><span class="sxs-lookup"><span data-stu-id="1a28f-171">`char`, `varchar`, `binary`</span></span>|<span data-ttu-id="1a28f-172">-1</span><span class="sxs-lookup"><span data-stu-id="1a28f-172">-1</span></span>|<span data-ttu-id="1a28f-173">'Default'</span><span class="sxs-lookup"><span data-stu-id="1a28f-173">'Default'</span></span>|<span data-ttu-id="1a28f-174">0</span><span class="sxs-lookup"><span data-stu-id="1a28f-174">0</span></span>|<span data-ttu-id="1a28f-175">0</span><span class="sxs-lookup"><span data-stu-id="1a28f-175">0</span></span>|<span data-ttu-id="1a28f-176">8000</span><span class="sxs-lookup"><span data-stu-id="1a28f-176">8000</span></span>|<span data-ttu-id="1a28f-177">不適用\*\*</span><span class="sxs-lookup"><span data-stu-id="1a28f-177">Not applicable\*\*</span></span>|<span data-ttu-id="1a28f-178">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-178">Not applicable</span></span>|  
|`nvarchar`|<span data-ttu-id="1a28f-179">-1</span><span class="sxs-lookup"><span data-stu-id="1a28f-179">-1</span></span>|<span data-ttu-id="1a28f-180">'Default'</span><span class="sxs-lookup"><span data-stu-id="1a28f-180">'Default'</span></span>|<span data-ttu-id="1a28f-181">0</span><span class="sxs-lookup"><span data-stu-id="1a28f-181">0</span></span>|<span data-ttu-id="1a28f-182">0</span><span class="sxs-lookup"><span data-stu-id="1a28f-182">0</span></span>|<span data-ttu-id="1a28f-183">4000</span><span class="sxs-lookup"><span data-stu-id="1a28f-183">4000</span></span>|<span data-ttu-id="1a28f-184">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-184">Not applicable</span></span>|<span data-ttu-id="1a28f-185">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-185">Not applicable</span></span>|  
|<span data-ttu-id="1a28f-186">`decimal`, `float`, `real`</span><span class="sxs-lookup"><span data-stu-id="1a28f-186">`decimal`, `float`, `real`</span></span>|<span data-ttu-id="1a28f-187">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-187">Not applicable</span></span>|<span data-ttu-id="1a28f-188">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-188">Not applicable</span></span>|<span data-ttu-id="1a28f-189">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-189">Not applicable</span></span>|<span data-ttu-id="1a28f-190">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-190">Not applicable</span></span>|<span data-ttu-id="1a28f-191">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-191">Not applicable</span></span>|<span data-ttu-id="1a28f-192">18</span><span class="sxs-lookup"><span data-stu-id="1a28f-192">18</span></span>|<span data-ttu-id="1a28f-193">0</span><span class="sxs-lookup"><span data-stu-id="1a28f-193">0</span></span>|  
|<span data-ttu-id="1a28f-194">`integer`, `bigint`, `tinyint`, `smallint`</span><span class="sxs-lookup"><span data-stu-id="1a28f-194">`integer`, `bigint`, `tinyint`, `smallint`</span></span>|<span data-ttu-id="1a28f-195">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-195">Not applicable</span></span>|<span data-ttu-id="1a28f-196">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-196">Not applicable</span></span>|<span data-ttu-id="1a28f-197">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-197">Not applicable</span></span>|<span data-ttu-id="1a28f-198">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-198">Not applicable</span></span>|<span data-ttu-id="1a28f-199">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-199">Not applicable</span></span>|<span data-ttu-id="1a28f-200">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-200">Not applicable</span></span>|<span data-ttu-id="1a28f-201">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-201">Not applicable</span></span>|  
|`datetime2`|<span data-ttu-id="1a28f-202">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-202">Not applicable</span></span>|<span data-ttu-id="1a28f-203">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-203">Not applicable</span></span>|<span data-ttu-id="1a28f-204">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-204">Not applicable</span></span>|<span data-ttu-id="1a28f-205">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-205">Not applicable</span></span>|<span data-ttu-id="1a28f-206">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-206">Not applicable</span></span>|<span data-ttu-id="1a28f-207">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-207">Not applicable</span></span>|<span data-ttu-id="1a28f-208">7</span><span class="sxs-lookup"><span data-stu-id="1a28f-208">7</span></span>|  
|`datetime offset`|<span data-ttu-id="1a28f-209">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-209">Not applicable</span></span>|<span data-ttu-id="1a28f-210">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-210">Not applicable</span></span>|<span data-ttu-id="1a28f-211">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-211">Not applicable</span></span>|<span data-ttu-id="1a28f-212">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-212">Not applicable</span></span>|<span data-ttu-id="1a28f-213">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-213">Not applicable</span></span>|<span data-ttu-id="1a28f-214">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-214">Not applicable</span></span>|<span data-ttu-id="1a28f-215">7</span><span class="sxs-lookup"><span data-stu-id="1a28f-215">7</span></span>|  
|<span data-ttu-id="1a28f-216">`datetime`, `date`, `smalldatetime`</span><span class="sxs-lookup"><span data-stu-id="1a28f-216">`datetime`, `date`, `smalldatetime`</span></span>|<span data-ttu-id="1a28f-217">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-217">Not applicable</span></span>|<span data-ttu-id="1a28f-218">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-218">Not applicable</span></span>|<span data-ttu-id="1a28f-219">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-219">Not applicable</span></span>|<span data-ttu-id="1a28f-220">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-220">Not applicable</span></span>|<span data-ttu-id="1a28f-221">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-221">Not applicable</span></span>|<span data-ttu-id="1a28f-222">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-222">Not applicable</span></span>|<span data-ttu-id="1a28f-223">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-223">Not applicable</span></span>|  
|<span data-ttu-id="1a28f-224">`money`, `smallmoney`</span><span class="sxs-lookup"><span data-stu-id="1a28f-224">`money`, `smallmoney`</span></span>|<span data-ttu-id="1a28f-225">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-225">Not applicable</span></span>|<span data-ttu-id="1a28f-226">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-226">Not applicable</span></span>|<span data-ttu-id="1a28f-227">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-227">Not applicable</span></span>|<span data-ttu-id="1a28f-228">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-228">Not applicable</span></span>|<span data-ttu-id="1a28f-229">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-229">Not applicable</span></span>|<span data-ttu-id="1a28f-230">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-230">Not applicable</span></span>|<span data-ttu-id="1a28f-231">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-231">Not applicable</span></span>|  
|`time`|<span data-ttu-id="1a28f-232">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-232">Not applicable</span></span>|<span data-ttu-id="1a28f-233">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-233">Not applicable</span></span>|<span data-ttu-id="1a28f-234">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-234">Not applicable</span></span>|<span data-ttu-id="1a28f-235">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-235">Not applicable</span></span>|<span data-ttu-id="1a28f-236">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-236">Not applicable</span></span>|<span data-ttu-id="1a28f-237">不適用</span><span class="sxs-lookup"><span data-stu-id="1a28f-237">Not applicable</span></span>|<span data-ttu-id="1a28f-238">7</span><span class="sxs-lookup"><span data-stu-id="1a28f-238">7</span></span>|  
  
 <span data-ttu-id="1a28f-239">\*  localeID -1 表示預設地區設定。</span><span class="sxs-lookup"><span data-stu-id="1a28f-239">\*  localeID -1 means the default locale.</span></span> <span data-ttu-id="1a28f-240">英文地區設定是 1033。</span><span class="sxs-lookup"><span data-stu-id="1a28f-240">The English locale is 1033.</span></span>  
  
 <span data-ttu-id="1a28f-241">\*\*  不適用 = 在資料行集上的選取作業期間，沒有任何值是這些屬性的輸出。</span><span class="sxs-lookup"><span data-stu-id="1a28f-241">\*\*  Not applicable = No values are output for these attributes during a select operation on the column set.</span></span> <span data-ttu-id="1a28f-242">當提供給插入或更新作業內資料行集的 XML 表示中的呼叫端指定這個屬性的值時，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a28f-242">Generates an error when a value is specified for this attribute by the caller in the XML representation provided for a column set in an insert or update operation.</span></span>  
  
## <a name="security"></a><span data-ttu-id="1a28f-243">安全性</span><span class="sxs-lookup"><span data-stu-id="1a28f-243">Security</span></span>  
 <span data-ttu-id="1a28f-244">資料行集之安全性模型的運作方式，類似於資料表和資料行之間存在的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="1a28f-244">The security model for a column set works similar to the security model that exists between table and columns.</span></span> <span data-ttu-id="1a28f-245">資料行集可視為一個迷你資料表，而選取作業就像是此迷你資料表上的 SELECT \* 作業。</span><span class="sxs-lookup"><span data-stu-id="1a28f-245">Column sets can be visualized as a minitable and a select operation is like a SELECT \* operation on this minitable.</span></span> <span data-ttu-id="1a28f-246">但是，資料行集與疏鬆資料行之間的關聯性是一種群組關聯性，而不限為容器。</span><span class="sxs-lookup"><span data-stu-id="1a28f-246">But, the relationship between column set to sparse columns is a grouping relationship instead of strictly a container.</span></span> <span data-ttu-id="1a28f-247">此安全性模型會檢查資料行集資料行上的安全性，並接受基礎疏鬆資料行上的 DENY 作業。</span><span class="sxs-lookup"><span data-stu-id="1a28f-247">The security model checks the security on the column set column, and honors the DENY operations on the underlying sparse columns.</span></span> <span data-ttu-id="1a28f-248">此安全性模型的其他特性如下：</span><span class="sxs-lookup"><span data-stu-id="1a28f-248">Additional characteristics of the security model are as follows:</span></span>  
  
-   <span data-ttu-id="1a28f-249">可以從資料行集資料行授與及撤銷安全性權限，類似於資料表中的任何其他資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-249">Security permissions can be granted and revoked from the column set column, similar to any other column in the table.</span></span>  
  
-   <span data-ttu-id="1a28f-250">資料行集資料行上 SELECT、INSERT、UPDATE、DELETE 和 REFERENCES 權限的 GRANT 或 REVOKE 不會傳播給該資料行集的基礎成員資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-250">A GRANT or REVOKE of SELECT, INSERT, UPDATE, DELETE, and REFERENCES permission on a column set column does not propagate to the underlying member columns of that set.</span></span> <span data-ttu-id="1a28f-251">它只適用於資料行集資料行的使用。</span><span class="sxs-lookup"><span data-stu-id="1a28f-251">It applies only to the usage of the column set column.</span></span> <span data-ttu-id="1a28f-252">資料行集的 DENY 權限會傳播給資料表的基礎疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-252">DENY permission on a column set does propagate to the underlying sparse columns of the table.</span></span>  
  
-   <span data-ttu-id="1a28f-253">在資料行集資料行上執行 SELECT、INSERT、UPDATE 和 DELETE 陳述式會要求使用者具有資料行集資料行的對應權限，同時具有資料表內所有疏鬆資料行的對應權限。</span><span class="sxs-lookup"><span data-stu-id="1a28f-253">Executing SELECT, INSERT, UPDATE, and DELETE statements on the column set column require that the user has corresponding permissions on the column set column, and also the corresponding permission on all the sparse columns in the table.</span></span> <span data-ttu-id="1a28f-254">由於此資料行集表示資料表中的所有疏鬆資料行，所以您必須具有所有疏鬆資料行的權限，這包括您可能不要變更的疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-254">Because the column set represents all the sparse columns in the table, you must have permission on all the sparse columns, and this includes sparse columns that you might not be changing.</span></span>  
  
-   <span data-ttu-id="1a28f-255">在疏鬆資料行或資料行集上執行 REVOKE 陳述式會將安全性預設為其父物件。</span><span class="sxs-lookup"><span data-stu-id="1a28f-255">Executing a REVOKE statement on a sparse column or column set defaults the security to their parent object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1a28f-256">範例</span><span class="sxs-lookup"><span data-stu-id="1a28f-256">Examples</span></span>  
 <span data-ttu-id="1a28f-257">在下列範例中，文件資料表包含常用的一組 `DocID` 和 `Title`資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-257">In the following examples, a document table contains the common set of columns `DocID` and `Title`.</span></span> <span data-ttu-id="1a28f-258">生產小組想要所有生產文件的 `ProductionSpecification` 和 `ProductionLocation` 資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-258">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="1a28f-259">行銷小組想要行銷文件的 `MarketingSurveyGroup` 資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-259">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span>  
  
### <a name="a-creating-a-table-that-has-a-column-set"></a><span data-ttu-id="1a28f-260">A.</span><span class="sxs-lookup"><span data-stu-id="1a28f-260">A.</span></span> <span data-ttu-id="1a28f-261">建立具有資料行集的資料表</span><span class="sxs-lookup"><span data-stu-id="1a28f-261">Creating a table that has a column set</span></span>  
 <span data-ttu-id="1a28f-262">下列範例會建立一個資料表，此資料表將使用疏鬆資料行，並包括資料行集 `SpecialPurposeColumns`。</span><span class="sxs-lookup"><span data-stu-id="1a28f-262">The following example creates the table that uses sparse columns and includes the column set `SpecialPurposeColumns`.</span></span> <span data-ttu-id="1a28f-263">此範例會將兩個資料列插入資料表中，然後選取資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="1a28f-263">The example inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a28f-264">此資料表只有五個資料行，以方便顯示及閱讀。</span><span class="sxs-lookup"><span data-stu-id="1a28f-264">This table has only five columns to make it easier to display and read.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStoreWithColumnSet  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL,  
     MarketingProgramID int SPARSE NULL,  
     SpecialPurposeColumns XML COLUMN_SET FOR ALL_SPARSE_COLUMNS);  
GO  
```  
  
### <a name="b-inserting-data-to-a-table-by-using-the-names-of-the-sparse-columns"></a><span data-ttu-id="1a28f-265">B.</span><span class="sxs-lookup"><span data-stu-id="1a28f-265">B.</span></span> <span data-ttu-id="1a28f-266">使用疏鬆資料行的名稱，將資料插入資料表中</span><span class="sxs-lookup"><span data-stu-id="1a28f-266">Inserting data to a table by using the names of the sparse columns</span></span>  
 <span data-ttu-id="1a28f-267">下列範例會將兩個資料列插入範例 A 建立的資料表中。此範例會使用疏鬆資料行的名稱，而且不會參考資料行集。</span><span class="sxs-lookup"><span data-stu-id="1a28f-267">The following examples insert two rows into the table that is created in example A. The examples use the names of the sparse columns and do not reference the column set.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStoreWithColumnSet (DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
### <a name="c-inserting-data-to-a-table-by-using-the-name-of-the-column-set"></a><span data-ttu-id="1a28f-268">C.</span><span class="sxs-lookup"><span data-stu-id="1a28f-268">C.</span></span> <span data-ttu-id="1a28f-269">使用資料行集的名稱，將資料插入資料表中</span><span class="sxs-lookup"><span data-stu-id="1a28f-269">Inserting data to a table by using the name of the column set</span></span>  
 <span data-ttu-id="1a28f-270">下列範例會將第三個資料列插入範例 A 建立的資料表中。這次不會使用疏鬆資料行的名稱，</span><span class="sxs-lookup"><span data-stu-id="1a28f-270">The following example inserts a third row into the table that is created in example A. This time the names of the sparse columns are not used.</span></span> <span data-ttu-id="1a28f-271">而是使用資料行集的名稱，而且插入作業會提供四個疏鬆資料行其中兩個的值 (使用 XML 格式)。</span><span class="sxs-lookup"><span data-stu-id="1a28f-271">Instead, the name of the column set is used, and the insert provides the values for two of the four sparse columns in XML format.</span></span>  
  
```  
INSERT DocumentStoreWithColumnSet (DocID, Title, SpecialPurposeColumns)  
VALUES (3, 'Tire Spec 2', '<ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>');  
GO  
```  
  
### <a name="d-observing-the-results-of-a-column-set-when-select--is-used"></a><span data-ttu-id="1a28f-272">D.</span><span class="sxs-lookup"><span data-stu-id="1a28f-272">D.</span></span> <span data-ttu-id="1a28f-273">在使用 SELECT \* 時觀察資料行集的結果</span><span class="sxs-lookup"><span data-stu-id="1a28f-273">Observing the results of a column set when SELECT \* is used</span></span>  
 <span data-ttu-id="1a28f-274">以下範例會從包含資料行集的資料表中選取所有資料行，</span><span class="sxs-lookup"><span data-stu-id="1a28f-274">The following example selects all the columns from the table that contains a column set.</span></span> <span data-ttu-id="1a28f-275">它會傳回 XML 資料行，其中包含疏鬆資料行的結合值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-275">It returns an XML column with the combined values of the sparse columns.</span></span> <span data-ttu-id="1a28f-276">但是不會個別傳回疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-276">It does not return the sparse columns individually.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns FROM DocumentStoreWithColumnSet ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1      Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `2      Survey 2142  <MarketingSurveyGroup>Men 25 - 35</MarketingSurveyGroup>`  
  
 `3      Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="e-observing-the-results-of-selecting-the-column-set-by-name"></a><span data-ttu-id="1a28f-277">E.</span><span class="sxs-lookup"><span data-stu-id="1a28f-277">E.</span></span> <span data-ttu-id="1a28f-278">觀察依據名稱選取資料行集的結果</span><span class="sxs-lookup"><span data-stu-id="1a28f-278">Observing the results of selecting the column set by name</span></span>  
 <span data-ttu-id="1a28f-279">由於生產部門對於行銷資料不感興趣，所以此範例加入 `WHERE` 子句來限制輸出。</span><span class="sxs-lookup"><span data-stu-id="1a28f-279">Because the Production department is not interested in the marketing data, this example adds a `WHERE` clause to restrict the output.</span></span> <span data-ttu-id="1a28f-280">此範例會使用資料行集的名稱。</span><span class="sxs-lookup"><span data-stu-id="1a28f-280">The example uses the name of the column set.</span></span>  
  
```  
SELECT DocID, Title, SpecialPurposeColumns  
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        SpecialPurposeColumns`  
  
 `1     Tire Spec 1  <ProductionSpecification>AXZZ217</ProductionSpecification><ProductionLocation>27</ProductionLocation>`  
  
 `3     Tire Spec 2  <ProductionSpecification>AXW9R411</ProductionSpecification><ProductionLocation>38</ProductionLocation>`  
  
### <a name="f-observing-the-results-of-selecting-sparse-columns-by-name"></a><span data-ttu-id="1a28f-281">F.</span><span class="sxs-lookup"><span data-stu-id="1a28f-281">F.</span></span> <span data-ttu-id="1a28f-282">觀察依據名稱選取疏鬆資料行的結果</span><span class="sxs-lookup"><span data-stu-id="1a28f-282">Observing the results of selecting sparse columns by name</span></span>  
 <span data-ttu-id="1a28f-283">當資料表包含資料行集時，您仍然可以使用個別資料行名稱來查詢此資料表，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1a28f-283">When a table contains a column set, you can still query the table by using the individual column names as shown in the following example.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStoreWithColumnSet  
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID Title        ProductionSpecification ProductionLocation`  
  
 `1     Tire Spec 1  AXZZ217                 27`  
  
 `3     Tire Spec 2  AXW9R411                38`  
  
### <a name="g-updating-a-table-by-using-a-column-set"></a><span data-ttu-id="1a28f-284">G.</span><span class="sxs-lookup"><span data-stu-id="1a28f-284">G.</span></span> <span data-ttu-id="1a28f-285">使用資料行集更新資料表</span><span class="sxs-lookup"><span data-stu-id="1a28f-285">Updating a table by using a column set</span></span>  
 <span data-ttu-id="1a28f-286">下列範例會使用該資料列所用之兩個疏鬆資料行的新值來更新第三筆記錄。</span><span class="sxs-lookup"><span data-stu-id="1a28f-286">The following example updates the third record with new values for both sparse columns that are used by that row.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification><ProductionLocation>38</ProductionLocation>'  
WHERE DocID = 3 ;  
GO  
```  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1a28f-287">使用資料行集的 UPDATE 陳述式會更新資料表內的所有疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="1a28f-287">An UPDATE statement that uses a column set updates all the sparse columns in the table.</span></span> <span data-ttu-id="1a28f-288">未參考的疏鬆資料行將會更新為 NULL。</span><span class="sxs-lookup"><span data-stu-id="1a28f-288">Sparse columns that are not referenced are updated to NULL.</span></span>  
  
 <span data-ttu-id="1a28f-289">下列範例會更新第三筆記錄，但是只會指定兩個已填入之資料行其中一個的值。</span><span class="sxs-lookup"><span data-stu-id="1a28f-289">The following example updates the third record, but only specifies the value of one of the two populated columns.</span></span> <span data-ttu-id="1a28f-290">第二個資料行 `ProductionLocation` 不會併入 `UPDATE` 陳述式中，而且會更新為 NULL。</span><span class="sxs-lookup"><span data-stu-id="1a28f-290">The second column `ProductionLocation` is not included in the `UPDATE` statement and is updated to NULL.</span></span>  
  
```  
UPDATE DocumentStoreWithColumnSet  
SET SpecialPurposeColumns = '<ProductionSpecification>ZZ285W</ProductionSpecification>'  
WHERE DocID = 3 ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a28f-291">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a28f-291">See Also</span></span>  
 [<span data-ttu-id="1a28f-292">使用疏鬆資料行</span><span class="sxs-lookup"><span data-stu-id="1a28f-292">Use Sparse Columns</span></span>](use-sparse-columns.md)  
  
  
