---
title: 指定資料表中的計算資料行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- computed columns, define
ms.assetid: 731a4576-09c1-47f0-a8f6-edd0b55679f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 22e4df8d67b61e50383ffd8e33f982990ff3f2ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598757"
---
# <a name="specify-computed-columns-in-a-table"></a><span data-ttu-id="2c1d2-102">指定資料表中的計算資料行</span><span class="sxs-lookup"><span data-stu-id="2c1d2-102">Specify Computed Columns in a Table</span></span>
  <span data-ttu-id="2c1d2-103">計算資料行是一個虛擬資料行，除非資料行標示了 PERSISTED，否則，並未實際儲存在資料表中。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-103">A computed column is a virtual column that is not physically stored in the table, unless the column is marked PERSISTED.</span></span> <span data-ttu-id="2c1d2-104">計算資料行運算式可以使用來自其他資料行的資料來計算其所屬資料行的值。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-104">A computed column expression can use data from other columns to calculate a value for the column to which it belongs.</span></span> <span data-ttu-id="2c1d2-105">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中指定計算資料行的運算式。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-105">You can specify an expression for a computed column in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2c1d2-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="2c1d2-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2c1d2-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="2c1d2-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2c1d2-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="2c1d2-108">Limitations and Restrictions</span></span>](#Limitations)  
  
     [<span data-ttu-id="2c1d2-109">安全性</span><span class="sxs-lookup"><span data-stu-id="2c1d2-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2c1d2-110">**若要使用下列項目來指定計算資料行：**</span><span class="sxs-lookup"><span data-stu-id="2c1d2-110">**To specify a computed column, using:**</span></span>  
  
     [<span data-ttu-id="2c1d2-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2c1d2-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2c1d2-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2c1d2-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2c1d2-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="2c1d2-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Limitations"></a> <span data-ttu-id="2c1d2-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="2c1d2-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="2c1d2-115">計算資料行不能用來做為 DEFAULT 或 FOREIGN KEY 條件約束定義，也不能搭配 NOT NULL 條件約束定義來使用。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-115">A computed column cannot be used as a DEFAULT or FOREIGN KEY constraint definition or with a NOT NULL constraint definition.</span></span> <span data-ttu-id="2c1d2-116">不過，如果計算資料行值是由具決定性的運算式所定義，且索引資料行接受結果的資料類型，計算資料行便可用來做為索引中的索引鍵資料行，也可用在任何 PRIMARY KEY 或 UNIQUE 條件約束中。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-116">However, if the computed column value is defined by a deterministic expression and the data type of the result is allowed in index columns, a computed column can be used as a key column in an index or as part of any PRIMARY KEY or UNIQUE constraint.</span></span> <span data-ttu-id="2c1d2-117">例如，如果資料表有整數資料行 a 和 b，您可以建立計算資料行 a + b 的索引，但不能建立計算資料行 a +DATEPART(dd, GETDATE()) 的索引，因為在後續叫用時，值可能會改變。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-117">For example, if the table has integer columns a and b, the computed column a + b may be indexed, but computed column a + DATEPART(dd, GETDATE()) cannot be indexed, because the value might change in subsequent invocations.</span></span>  
  
-   <span data-ttu-id="2c1d2-118">計算資料行不能是 INSERT 或 UPDATE 陳述式的目標。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-118">A computed column cannot be the target of an INSERT or UPDATE statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2c1d2-119">Security</span><span class="sxs-lookup"><span data-stu-id="2c1d2-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2c1d2-120">權限</span><span class="sxs-lookup"><span data-stu-id="2c1d2-120">Permissions</span></span>  
 <span data-ttu-id="2c1d2-121">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-121">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2c1d2-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2c1d2-122">Using SQL Server Management Studio</span></span>  
  
###  <a name="to-add-a-new-computed-column"></a><a name="NewColumn"></a> <span data-ttu-id="2c1d2-123">若要加入新的計算資料行</span><span class="sxs-lookup"><span data-stu-id="2c1d2-123">To add a new computed column</span></span>  
  
1.  <span data-ttu-id="2c1d2-124">在 **[物件總管]** 中，展開要在其中加入新的計算資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-124">In **Object Explorer**, expand the table for which you want to add the new computed column.</span></span> <span data-ttu-id="2c1d2-125">以滑鼠右鍵按一下 [資料行]  ，然後選取 [新增資料行]  。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-125">Right-click **Columns** and select **New Column**.</span></span>  
  
2.  <span data-ttu-id="2c1d2-126">輸入資料行名稱並接受預設資料類型 (`nchar`(10))。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-126">Enter the column name and accept the default data type (`nchar`(10)).</span></span> <span data-ttu-id="2c1d2-127">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會判斷計算資料行的資料類型，方法是將資料類型優先順序規則套用至公式中指定的運算式。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-127">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines the data type of the computed column by applying the rules of data type precedence to the expressions specified in the formula.</span></span> <span data-ttu-id="2c1d2-128">例如，如果公式參考 `money` 類型的資料行以及 `int` 類型的資料行，則計算資料行會是 `money` 類型，因為該資料類型的優先順序較高。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-128">For example, if the formula references a column of type `money` and a column of type `int`, the computed column will be of type `money` because that data type has the higher precedence.</span></span> <span data-ttu-id="2c1d2-129">如需詳細資訊，請參閱[資料類型優先順序 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-type-precedence-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-129">For more information, see [Data Type Precedence &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-type-precedence-transact-sql).</span></span>  
  
3.  <span data-ttu-id="2c1d2-130">在 **[資料行屬性]** 索引標籤中，展開 **[計算資料行規格]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-130">In the **Column Properties** tab, expand the **Computed Column Specification** property.</span></span>  
  
4.  <span data-ttu-id="2c1d2-131">在 [(Formula)]  子屬性右邊的方格資料格中，輸入此資料行的運算式。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-131">In the **(Formula)** child property, enter the expression for this column in the grid cell to the right.</span></span> <span data-ttu-id="2c1d2-132">例如，在 `SalesTotal` 資料行中，您輸入的公式可能是 `SubTotal+TaxAmt+Freight`，該公式會將資料表中每一個資料列的這些資料行中的值相加。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-132">For example, in a `SalesTotal` column, the formula you enter might be `SubTotal+TaxAmt+Freight`, which adds the value in these columns for each row in the table.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2c1d2-133">當一個公式結合兩個不同資料類型的運算式時，資料類型優先順序的規則，會指定將低優先順序的資料類型，轉換為高優先順序的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-133">When a formula combines two expressions of different data types, the rules for data type precedence specify that the data type with the lower precedence is converted to the data type with the higher precedence.</span></span> <span data-ttu-id="2c1d2-134">如果轉換不是支援的隱含轉換，就會傳回錯誤 "`Error validating the formula for column column_name.`"。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-134">If the conversion is not a supported implicit conversion, the error "`Error validating the formula for column column_name.`" is returned.</span></span> <span data-ttu-id="2c1d2-135">使用 CAST 或 CONVERT 函數解決資料類型衝突。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-135">Use the CAST or CONVERT function to resolve the data type conflict.</span></span> <span data-ttu-id="2c1d2-136">例如，如果 `nvarchar` 類型的資料行與 `int` 類型的資料行結合，則整數類型必須轉圜為 `nvarchar`，如 `('Prod'+CONVERT(nvarchar(23),ProductID))` 這個公式所示。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-136">For example, if a column of type `nvarchar` is combined with a column of type `int`, the integer type must be converted to `nvarchar` as shown in this formula `('Prod'+CONVERT(nvarchar(23),ProductID))`.</span></span> <span data-ttu-id="2c1d2-137">如需詳細資訊，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-137">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
5.  <span data-ttu-id="2c1d2-138">藉由從 [Is Persisted]  子屬性的下拉式清單中選擇 [是]  或 [否]  ，指示資料是否為永續性。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-138">Indicate whether the data is persisted by choosing **Yes** or **No** from the drop-down for the **Is Persisted** child property.</span></span>  
  
6.  <span data-ttu-id="2c1d2-139">在 [檔案] \*\*\*\* 功能表上，按一下 [儲存「資料表名稱」__]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-139">On the **File** menu, click **Save**_table name_.</span></span>  
  
#### <a name="to-add-a-computed-column-definition-to-an-existing-column"></a><span data-ttu-id="2c1d2-140">若要將計算資料行定義新增至現有資料行</span><span class="sxs-lookup"><span data-stu-id="2c1d2-140">To add a computed column definition to an existing column</span></span>  
  
1.  <span data-ttu-id="2c1d2-141">在物件總管  中，以滑鼠右鍵按一下包含您要變更之資料行的資料表，然後展開 [資料行]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-141">In **Object Explorer**, right-click the table with the column for which you want to change and expand the **Columns** folder.</span></span>  
  
2.  <span data-ttu-id="2c1d2-142">以滑鼠右鍵按一下要指定其計算資料行公式的資料行，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-142">Right-click the column for which you want to specify a computed column formula and click **Delete**.</span></span> <span data-ttu-id="2c1d2-143">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-143">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="2c1d2-144">加入新的資料行，並依照上述程序加入新的計算料行，藉此指定計算資料行公式。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-144">Add a new column and specify the computed column formula by following the previous procedure to add a new computed column.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2c1d2-145">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2c1d2-145">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-computed-column-when-creating-a-table"></a><span data-ttu-id="2c1d2-146">建立資料表時加入計算資料行</span><span class="sxs-lookup"><span data-stu-id="2c1d2-146">To add a computed column when creating a table</span></span>  
  
1.  <span data-ttu-id="2c1d2-147">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c1d2-148">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2c1d2-149">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-149">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="2c1d2-150">此範例會建立包含計算資料行的資料表，該計算資料行會乘以 `QtyAvailable` 資料行的值乘 `UnitPrice` 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-150">The example creates a table with a computed column that multiplies the value in the `QtyAvailable` column times the value in the `UnitPrice` column.</span></span>  
  
    ```  
    CREATE TABLE dbo.Products   
    (  
        ProductID int IDENTITY (1,1) NOT NULL  
      , QtyAvailable smallint  
      , UnitPrice money  
      , InventoryValue AS QtyAvailable * UnitPrice  
    );  
  
    -- Insert values into the table.  
    INSERT INTO dbo.Products (QtyAvailable, UnitPrice)  
    VALUES (25, 2.00), (10, 1.5);  
  
    -- Display the rows in the table.  
    SELECT ProductID, QtyAvailable, UnitPrice, InventoryValue  
    FROM dbo.Products;  
  
    ```  
  
#### <a name="to-add-a-new-computed-column-to-an-existing-table"></a><span data-ttu-id="2c1d2-151">若要將新的計算資料行加入至現有資料表</span><span class="sxs-lookup"><span data-stu-id="2c1d2-151">To add a new computed column to an existing table</span></span>  
  
1.  <span data-ttu-id="2c1d2-152">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-152">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c1d2-153">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-153">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2c1d2-154">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-154">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="2c1d2-155">下列範例會將新的資料行加入至上一個範例中建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-155">The following example adds a new column to the table created in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.35);  
  
    ```  
  
#### <a name="to-change-an-existing-column-to-a-computed-column"></a><span data-ttu-id="2c1d2-156">若要將現有的資料行變更為計算資料行</span><span class="sxs-lookup"><span data-stu-id="2c1d2-156">To change an existing column to a computed column</span></span>  
  
1.  <span data-ttu-id="2c1d2-157">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-157">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c1d2-158">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-158">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2c1d2-159">若要將現有的資料行變更為計算資料行，您必須卸除並重新建立計算資料行。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-159">To change an existing column to a computed column you must drop and re-create the computed column.</span></span> <span data-ttu-id="2c1d2-160">將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-160">Copy and paste the following example into the query window and then click **Execute**.</span></span> <span data-ttu-id="2c1d2-161">下列範例會修改上一個範例中加入的資料行。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-161">The following example modifies the column added in the previous example.</span></span>  
  
    ```  
    ALTER TABLE dbo.Products DROP COLUMN RetailValue;  
    GO  
    ALTER TABLE dbo.Products ADD RetailValue AS (QtyAvailable * UnitPrice * 1.5);  
  
    ```  
  
     <span data-ttu-id="2c1d2-162">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2c1d2-162">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
