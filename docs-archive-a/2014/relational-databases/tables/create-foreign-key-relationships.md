---
title: 建立外部索引鍵關聯性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], creating
ms.assetid: 867a54b8-5be4-46e6-9702-49ae6dabf67c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ee0de3311eb6abffcdb71ab725d0650fe96b04c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607340"
---
# <a name="create-foreign-key-relationships"></a><span data-ttu-id="4d76a-102">建立外部索引鍵關聯性</span><span class="sxs-lookup"><span data-stu-id="4d76a-102">Create Foreign Key Relationships</span></span>
  <span data-ttu-id="4d76a-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中建立外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="4d76a-103">This topic describes how to create foreign key relationships in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4d76a-104">當想要將一個資料表的資料列，與其他資料表的資料列建立相關時，可以建立兩者間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4d76a-104">You create a relationship between two tables when you want to associate rows of one table with rows of another.</span></span>  
  
 <span data-ttu-id="4d76a-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4d76a-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4d76a-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4d76a-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d76a-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="4d76a-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4d76a-108">安全性</span><span class="sxs-lookup"><span data-stu-id="4d76a-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4d76a-109">**使用下列方法建立外部索引鍵關聯性：**</span><span class="sxs-lookup"><span data-stu-id="4d76a-109">**To Create Foreign Key Relationships by using:**</span></span>  
  
     [<span data-ttu-id="4d76a-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d76a-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4d76a-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d76a-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d76a-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="4d76a-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4d76a-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="4d76a-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4d76a-114">外部索引鍵條件約束不一定只能連結到另一個資料表中的主索引鍵條件約束；它也可以定義成參考另一個資料表中 UNIQUE 條件約束的資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-114">A foreign key constraint does not have to be linked only to a primary key constraint in another table; it can also be defined to reference the columns of a UNIQUE constraint in another table.</span></span>  
  
-   <span data-ttu-id="4d76a-115">在 FOREIGN KEY 條件約束的資料行中輸入 NULL 以外的值時，值必須在參考的資料行中；否則，系統會傳回外部索引鍵違規錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="4d76a-115">When a value other than NULL is entered into the column of a FOREIGN KEY constraint, the value must exist in the referenced column; otherwise, a foreign key violation error message is returned.</span></span> <span data-ttu-id="4d76a-116">若要確定會驗證複合外部索引鍵條件約束的所有值，請對所有參與的資料行指定 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="4d76a-116">To make sure that all values of a composite foreign key constraint are verified, specify NOT NULL on all the participating columns.</span></span>  
  
-   <span data-ttu-id="4d76a-117">FOREIGN KEY 條件約束只能參考在相同伺服器之相同資料庫內的資料表。</span><span class="sxs-lookup"><span data-stu-id="4d76a-117">FOREIGN KEY constraints can reference only tables within the same database on the same server.</span></span> <span data-ttu-id="4d76a-118">跨資料庫參考完整性必須利用觸發程序來實作。</span><span class="sxs-lookup"><span data-stu-id="4d76a-118">Cross-database referential integrity must be implemented through triggers.</span></span> <span data-ttu-id="4d76a-119">如需詳細資訊，請參閱 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4d76a-119">For more information, see [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).</span></span>  
  
-   <span data-ttu-id="4d76a-120">FOREIGN KEY 條件約束可以參考相同資料表中的另一個資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-120">FOREIGN KEY constraints can reference another column in the same table.</span></span> <span data-ttu-id="4d76a-121">這稱為自我參考。</span><span class="sxs-lookup"><span data-stu-id="4d76a-121">This is referred to as a self-reference.</span></span>  
  
-   <span data-ttu-id="4d76a-122">資料行層級上指定的 FOREIGN KEY 條件約束只能列出一個參考資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-122">A FOREIGN KEY constraint specified at the column level can list only one reference column.</span></span> <span data-ttu-id="4d76a-123">這個資料行必須有定義了條件約束的資料行之相同資料類型。</span><span class="sxs-lookup"><span data-stu-id="4d76a-123">This column must have the same data type as the column on which the constraint is defined.</span></span>  
  
-   <span data-ttu-id="4d76a-124">資料表層級上指定的 FOREIGN KEY 條件約束，必須有與條件約束資料行清單中資料行一樣多的參考資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-124">A FOREIGN KEY constraint specified at the table level must have the same number of reference columns as the number of columns in the constraint column list.</span></span> <span data-ttu-id="4d76a-125">每個參考資料行的資料類型，也必須與資料行清單中的對應資料行相同。</span><span class="sxs-lookup"><span data-stu-id="4d76a-125">The data type of each reference column must also be the same as the corresponding column in the column list.</span></span>  
  
-   <span data-ttu-id="4d76a-126">在資料表所能包含參考其他資料表的 FOREIGN KEY 條件約束數目，及其他資料表所擁有參考特定資料表的 FOREIGN KEY 條件約束數目上， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 並沒有預先定義的限制。</span><span class="sxs-lookup"><span data-stu-id="4d76a-126">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not have a predefined limit on either the number of FOREIGN KEY constraints a table can contain that reference other tables, or the number of FOREIGN KEY constraints that are owned by other tables that reference a specific table.</span></span> <span data-ttu-id="4d76a-127">不過，FOREIGN KEY 條件約束的實際可用數目，會受到硬體組態及資料庫和應用程式設計的限制。</span><span class="sxs-lookup"><span data-stu-id="4d76a-127">Nevertheless, the actual number of FOREIGN KEY constraints that can be used is limited by the hardware configuration and by the design of the database and application.</span></span> <span data-ttu-id="4d76a-128">建議資料表所包含的 FOREIGN KEY 條件約束數目不要超出 253 個，參考資料表的 FOREIGN KEY 條件約束數目也不要超出 253 個。</span><span class="sxs-lookup"><span data-stu-id="4d76a-128">We recommend that a table contain no more than 253 FOREIGN KEY constraints, and that it be referenced by no more than 253 FOREIGN KEY constraints.</span></span>  
  
-   <span data-ttu-id="4d76a-129">暫存資料表不會強制執行 FOREIGN KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="4d76a-129">FOREIGN KEY constraints are not enforced on temporary tables.</span></span>  
  
-   <span data-ttu-id="4d76a-130">如果在 CLR 使用者定義的類型資料行上定義外部索引鍵，類型的實作必須支援二進位順序。</span><span class="sxs-lookup"><span data-stu-id="4d76a-130">If a foreign key is defined on a CLR user-defined type column, the implementation of the type must support binary ordering.</span></span> <span data-ttu-id="4d76a-131">如需詳細資訊，請參閱 [CLR 使用者定義型別](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4d76a-131">For more information, see [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md).</span></span>  
  
-   <span data-ttu-id="4d76a-132">只有在所參考的主索引鍵也定義成 `varchar(max)` 類型時，`varchar(max)` 類型的資料行才能夠參與 FOREIGN KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="4d76a-132">A column of type `varchar(max)` can participate in a FOREIGN KEY constraint only if the primary key it references is also defined as type `varchar(max)`.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4d76a-133">Security</span><span class="sxs-lookup"><span data-stu-id="4d76a-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4d76a-134">權限</span><span class="sxs-lookup"><span data-stu-id="4d76a-134">Permissions</span></span>  
 <span data-ttu-id="4d76a-135">建立具有外部索引鍵的新資料表，需要資料庫中的 CREATE TABLE 權限及建立資料表的結構描述之 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4d76a-135">Creating a new table with a foreign key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="4d76a-136">在現有資料表中建立外部索引鍵需要此資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4d76a-136">Creating a foreign key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d76a-137">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d76a-137">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-foreign-key-relationship-in-table-designer"></a><span data-ttu-id="4d76a-138">若要在資料表設計工具建立外部索引鍵關聯性</span><span class="sxs-lookup"><span data-stu-id="4d76a-138">To create a foreign key relationship in Table Designer</span></span>  
  
1.  <span data-ttu-id="4d76a-139">在物件總管中，以滑鼠右鍵按一下位於關聯性之外部索引鍵端上的資料表，然後按一下 [設計]。</span><span class="sxs-lookup"><span data-stu-id="4d76a-139">In Object Explorer, right-click the table that will be on the foreign-key side of the relationship and click **Design**.</span></span>  
  
     <span data-ttu-id="4d76a-140">資料表會在**資料表設計工具**中開啟。</span><span class="sxs-lookup"><span data-stu-id="4d76a-140">The table opens in **Table Designer**.</span></span>  
  
2.  <span data-ttu-id="4d76a-141">從 **[資料表設計工具]** 功能表中，按一下 **[關聯性]** 。</span><span class="sxs-lookup"><span data-stu-id="4d76a-141">From the **Table Designer** menu, click **Relationships**.</span></span>  
  
3.  <span data-ttu-id="4d76a-142">在 [外部索引鍵關聯性] 對話方塊中，按一下 [加入]。</span><span class="sxs-lookup"><span data-stu-id="4d76a-142">In the **Foreign-key Relationships** dialog box, click **Add**.</span></span>  
  
     <span data-ttu-id="4d76a-143">關聯性會出現在 [選取的關聯性] 清單中，並顯示系統提供的名稱，格式為 FK_\<*tablename*>_\<*tablename*>，其中 *tablename* 為外部索引鍵資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d76a-143">The relationship appears in the **Selected Relationship** list with a system-provided name in the format FK_\<*tablename*>_\<*tablename*>, where *tablename* is the name of the foreign key table.</span></span>  
  
4.  <span data-ttu-id="4d76a-144">在 [ **選取的關聯性** ] 清單中，按一下關聯性。</span><span class="sxs-lookup"><span data-stu-id="4d76a-144">Click the relationship in the **Selected Relationship** list.</span></span>  
  
5.  <span data-ttu-id="4d76a-145">按一下方格右邊的 [資料表及資料行規格]，然後按一下屬性右邊的省略符號 ( **...** )。</span><span class="sxs-lookup"><span data-stu-id="4d76a-145">Click **Tables and Columns Specification** in the grid to the right and click the ellipses (**...**) to the right of the property.</span></span>  
  
6.  <span data-ttu-id="4d76a-146">在 [資料表和資料行] 對話視窗的 [主索引鍵] 下拉式清單中，選擇將要成為關聯性主索引鍵端的資料表。</span><span class="sxs-lookup"><span data-stu-id="4d76a-146">In the **Tables and Columns** dialog box, in the **Primary Key** drop-down list, choose the table that will be on the primary-key side of the relationship.</span></span>  
  
7.  <span data-ttu-id="4d76a-147">在方格的下方，選擇組成資料表主索引鍵的資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-147">In the grid beneath, choose the columns contributing to the table's primary key.</span></span> <span data-ttu-id="4d76a-148">在每個資料行左側的鄰近方格資料格，選擇對應到外部索引鍵資料表的外部索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-148">In the adjacent grid cell to the left of each column, choose the corresponding foreign-key column of the foreign-key table.</span></span>  
  
     <span data-ttu-id="4d76a-149">**[資料表設計工具]** 會提供關聯性的建議名稱。</span><span class="sxs-lookup"><span data-stu-id="4d76a-149">**Table Designer** suggests a name for the relationship.</span></span> <span data-ttu-id="4d76a-150">若要變更這個名稱，請編輯 **[關聯性名稱]** 文字方塊的內容。</span><span class="sxs-lookup"><span data-stu-id="4d76a-150">To change this name, edit the contents of the **Relationship Name** text box.</span></span>  
  
8.  <span data-ttu-id="4d76a-151">選擇 **[確定]** 建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="4d76a-151">Choose **OK** to create the relationship.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4d76a-152">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d76a-152">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-foreign-key-in-a-new-table"></a><span data-ttu-id="4d76a-153">在新的資料表建立外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="4d76a-153">To create a foreign key in a new table</span></span>  
  
1.  <span data-ttu-id="4d76a-154">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d76a-154">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d76a-155">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4d76a-155">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4d76a-156">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d76a-156">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4d76a-157">此範例會建立資料表並在 `TempID` 資料行上定義外部索引鍵條件約束，而此資料行會參考 `SalesReasonID` 資料表中的 `Sales.SalesReason` 資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-157">The example creates a table and defines a foreign key constraint on the column `TempID` that references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span> <span data-ttu-id="4d76a-158">ON DELETE CASCADE 和 ON UPDATE CASCADE 子句用來確定對 `Sales.SalesReason` 資料表所做的變更會自動傳播至 `Sales.TempSalesReason` 資料表。</span><span class="sxs-lookup"><span data-stu-id="4d76a-158">The ON DELETE CASCADE and ON UPDATE CASCADE clauses are used to ensure that changes made to `Sales.SalesReason` table are automatically propagated to the `Sales.TempSalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Sales.TempSalesReason (TempID int NOT NULL, Name nvarchar(50),   
    CONSTRAINT PK_TempSales PRIMARY KEY NONCLUSTERED (TempID),   
    CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    );GO  
  
    ```  
  
#### <a name="to-create-a-foreign-key-in-an-existing-table"></a><span data-ttu-id="4d76a-159">在現有的資料表建立外部索引鍵</span><span class="sxs-lookup"><span data-stu-id="4d76a-159">To create a foreign key in an existing table</span></span>  
  
1.  <span data-ttu-id="4d76a-160">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d76a-160">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d76a-161">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4d76a-161">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4d76a-162">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d76a-162">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4d76a-163">此範例會在 `TempID` 資料行上建立外部索引鍵，並參考 `SalesReasonID` 資料表中的 `Sales.SalesReason` 資料行。</span><span class="sxs-lookup"><span data-stu-id="4d76a-163">The example creates a foreign key on the column `TempID` and references the column `SalesReasonID` in the `Sales.SalesReason` table.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Sales.TempSalesReason   
    ADD CONSTRAINT FK_TempSales_SalesReason FOREIGN KEY (TempID)   
        REFERENCES Sales.SalesReason (SalesReasonID)   
        ON DELETE CASCADE  
        ON UPDATE CASCADE  
    ;  
    GO  
  
    ```  
  
     <span data-ttu-id="4d76a-164">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)、[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 和 [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4d76a-164">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
  
