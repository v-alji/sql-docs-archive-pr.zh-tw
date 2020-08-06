---
title: 建立主索引鍵 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- primary keys [SQL Server], creating
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
author: stevestein
ms.author: sstein
ms.openlocfilehash: c515ef8f978b41225ff45e87646b0aa7a9706a34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607341"
---
# <a name="create-primary-keys"></a><span data-ttu-id="4b47f-102">建立主索引鍵</span><span class="sxs-lookup"><span data-stu-id="4b47f-102">Create Primary Keys</span></span>
  <span data-ttu-id="4b47f-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中定義主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4b47f-103">You can define a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4b47f-104">建立主索引鍵會自動建立對應的唯一叢集或非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="4b47f-104">Creating a primary key automatically creates a corresponding unique, clustered or nonclustered index.</span></span>  
  
 <span data-ttu-id="4b47f-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4b47f-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4b47f-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4b47f-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4b47f-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="4b47f-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="4b47f-108">安全性</span><span class="sxs-lookup"><span data-stu-id="4b47f-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4b47f-109">**使用下列方法建立主索引鍵：**</span><span class="sxs-lookup"><span data-stu-id="4b47f-109">**To create a primary key, using:**</span></span>  
  
     [<span data-ttu-id="4b47f-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4b47f-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4b47f-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4b47f-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4b47f-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="4b47f-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="4b47f-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="4b47f-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="4b47f-114">一份資料表只能有一個 PRIMARY KEY 條件約束。</span><span class="sxs-lookup"><span data-stu-id="4b47f-114">A table can contain only one PRIMARY KEY constraint.</span></span>  
  
-   <span data-ttu-id="4b47f-115">PRIMARY KEY 條件約束內所定義的所有資料行，都必須定義成 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="4b47f-115">All columns defined within a PRIMARY KEY constraint must be defined as NOT NULL.</span></span> <span data-ttu-id="4b47f-116">如果未指定 Null 屬性，參與 PRIMARY KEY 條件約束的所有資料行，其 Null 屬性都會設成 NOT NULL。</span><span class="sxs-lookup"><span data-stu-id="4b47f-116">If nullability is not specified, all columns participating in a PRIMARY KEY constraint have their nullability set to NOT NULL.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4b47f-117">Security</span><span class="sxs-lookup"><span data-stu-id="4b47f-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4b47f-118">權限</span><span class="sxs-lookup"><span data-stu-id="4b47f-118">Permissions</span></span>  
 <span data-ttu-id="4b47f-119">建立具有主索引鍵的新資料表，需要資料庫中的 CREATE TABLE 權限及建立資料表的結構描述之 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4b47f-119">Creating a new table with a primary key requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span>  
  
 <span data-ttu-id="4b47f-120">在現有資料表中建立主索引鍵需要此資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4b47f-120">Creating a primary key in an existing table requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4b47f-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4b47f-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-primary-key"></a><span data-ttu-id="4b47f-122">若要建立主索引鍵</span><span class="sxs-lookup"><span data-stu-id="4b47f-122">To create a primary key</span></span>  
  
1.  <span data-ttu-id="4b47f-123">在物件總管中，以滑鼠右鍵按一下您要加入唯一條件約束的資料表，然後按一下 [**設計**]。</span><span class="sxs-lookup"><span data-stu-id="4b47f-123">In Object Explorer, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="4b47f-124">在 **[資料表設計工具]** 中，按一下要定義為主索引鍵的資料庫資料行的資料列選取器。</span><span class="sxs-lookup"><span data-stu-id="4b47f-124">In **Table Designer**, click the row selector for the database column you want to define as the primary key.</span></span> <span data-ttu-id="4b47f-125">若要選取多個資料行，請按住 CTRL 鍵，同時按一下其他資料行的資料列選取器。</span><span class="sxs-lookup"><span data-stu-id="4b47f-125">If you want to select multiple columns, hold down the CTRL key while you click the row selectors for the other columns.</span></span>  
  
3.  <span data-ttu-id="4b47f-126">在資料行的資料列選取器中，按一下滑鼠右鍵，然後選取 [設定主索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4b47f-126">Right-click the row selector for the column and select **Set Primary Key**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="4b47f-127">若要重新定義主索引鍵，必須在建立新的主索引鍵前，先刪除所有現有主索引鍵的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4b47f-127">If you want to redefine the primary key, any relationships to the existing primary key must be deleted before the new primary key can be created.</span></span> <span data-ttu-id="4b47f-128">出現訊息警告您，這個程序中會自動刪除現有的關聯性。</span><span class="sxs-lookup"><span data-stu-id="4b47f-128">A message will warn you that existing relationships will be automatically deleted as part of this process.</span></span>  
  
 <span data-ttu-id="4b47f-129">主索引鍵資料行是由資料列選取器中的主索引鍵符號識別。</span><span class="sxs-lookup"><span data-stu-id="4b47f-129">A primary key column is identified by a primary key symbol in its row selector.</span></span>  
  
 <span data-ttu-id="4b47f-130">如果主索引鍵由一個以上的資料行組成，一個資料行中允許有重複的值，但是主索引鍵中所有資料行的組合值必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4b47f-130">If a primary key consists of more than one column, duplicate values are allowed in one column, but each combination of values from all the columns in the primary key must be unique.</span></span>  
  
 <span data-ttu-id="4b47f-131">如果您定義了複合索引鍵，主索引鍵中的資料行順序必須符合資料表所顯示的資料行順序。</span><span class="sxs-lookup"><span data-stu-id="4b47f-131">If you define a compound key, the order of columns in the primary key matches the order of columns as shown in the table.</span></span> <span data-ttu-id="4b47f-132">然而，您可以在建立主索引鍵之後變更資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="4b47f-132">However, you can change the order of columns after the primary key is created.</span></span> <span data-ttu-id="4b47f-133">如需詳細資訊，請參閱 [修改主索引鍵](modify-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="4b47f-133">For more information, see [Modify Primary Keys](modify-primary-keys.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4b47f-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4b47f-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-primary-key-in-an-existing-table"></a><span data-ttu-id="4b47f-135">在現有的資料表建立主索引鍵</span><span class="sxs-lookup"><span data-stu-id="4b47f-135">To create a primary key in an existing table</span></span>  
  
1.  <span data-ttu-id="4b47f-136">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4b47f-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4b47f-137">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4b47f-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4b47f-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4b47f-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4b47f-139">此範例會在 `TransactionID`資料行上建立主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4b47f-139">The example creates a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### <a name="to-create-a-primary-key-in-a-new-table"></a><span data-ttu-id="4b47f-140">在新的資料表建立主索引鍵</span><span class="sxs-lookup"><span data-stu-id="4b47f-140">To create a primary key in a new table</span></span>  
  
1.  <span data-ttu-id="4b47f-141">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4b47f-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4b47f-142">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4b47f-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4b47f-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4b47f-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4b47f-144">此範例會建立資料表並在 `TransactionID`資料行上定義主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="4b47f-144">The example creates a table and defines a primary key on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="4b47f-145">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)、[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 和 [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4b47f-145">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
