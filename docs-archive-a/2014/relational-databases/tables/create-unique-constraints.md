---
title: 建立唯一的條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- UNIQUE constraints [SQL Server], creating
- constraints [SQL Server], creating
- constraints [SQL Server], unique
ms.assetid: a86f9d6f-f242-43be-b65d-b3435b71b62a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 252de63f965f98734a6d62d94bfff9dc5774cab6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706354"
---
# <a name="create-unique-constraints"></a><span data-ttu-id="4d666-102">建立唯一的條件約束</span><span class="sxs-lookup"><span data-stu-id="4d666-102">Create Unique Constraints</span></span>
  <span data-ttu-id="4d666-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中建立唯一條件約束，確保在沒有參與主索引鍵之特定資料行中輸入的值不會重複。</span><span class="sxs-lookup"><span data-stu-id="4d666-103">You can create a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] to ensure no duplicate values are entered in specific columns that do not participate in a primary key.</span></span> <span data-ttu-id="4d666-104">建立唯一條件約束會自動建立對應的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="4d666-104">Creating a unique constraint automatically creates a corresponding unique index.</span></span>  
  
 <span data-ttu-id="4d666-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="4d666-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="4d666-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="4d666-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="4d666-107">安全性</span><span class="sxs-lookup"><span data-stu-id="4d666-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="4d666-108">**若要使用下列項目來建立唯一條件約束：**</span><span class="sxs-lookup"><span data-stu-id="4d666-108">**To create a unique constraint, using:**</span></span>  
  
     [<span data-ttu-id="4d666-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d666-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="4d666-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d666-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="4d666-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="4d666-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="4d666-112">Security</span><span class="sxs-lookup"><span data-stu-id="4d666-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="4d666-113">權限</span><span class="sxs-lookup"><span data-stu-id="4d666-113">Permissions</span></span>  
 <span data-ttu-id="4d666-114">需要資料表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="4d666-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="4d666-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="4d666-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="4d666-116">若要建立唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="4d666-116">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="4d666-117">在**物件總管**中，以滑鼠右鍵按一下要加入唯一條件約束的資料表，然後按一下 [設計]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d666-117">In **Object Explorer**, right-click the table to which you want to add a unique constraint, and click **Design**.</span></span>  
  
2.  <span data-ttu-id="4d666-118">在 [**資料表設計工具**] 功能表上，按一下 [**索引/索引鍵**]。</span><span class="sxs-lookup"><span data-stu-id="4d666-118">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
3.  <span data-ttu-id="4d666-119">在 [索引/索引鍵]\*\*\*\* 對話方塊中，按一下 [加入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d666-119">In the **Indexes/Keys** dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="4d666-120">在 [一般]\*\*\*\* 底下的方格中，按一下 [類型]\*\*\*\*，然後從屬性右邊的下拉式清單方塊中選擇 [唯一索引鍵]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d666-120">In the grid under **General**, click **Type** and choose **Unique Key** from the drop-down list box to the right of the property.</span></span>  
  
5.  <span data-ttu-id="4d666-121">在 [檔案] \*\*\*\* 功能表上，按一下 [儲存「資料表名稱」__]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4d666-121">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="4d666-122">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="4d666-122">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-unique-constraint"></a><span data-ttu-id="4d666-123">若要建立唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="4d666-123">To create a unique constraint</span></span>  
  
1.  <span data-ttu-id="4d666-124">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d666-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d666-125">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4d666-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4d666-126">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d666-126">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4d666-127">此範例會建立 `TransactionHistoryArchive4` 資料表並且在 `TransactionID`資料行上建立唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="4d666-127">The example creates the table `TransactionHistoryArchive4` and creates a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive4  
     (  
       TransactionID int NOT NULL,   
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)   
    );   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-on-an-existing-table"></a><span data-ttu-id="4d666-128">若要在現有的資料表上建立唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="4d666-128">To create a unique constraint on an existing table</span></span>  
  
1.  <span data-ttu-id="4d666-129">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d666-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d666-130">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4d666-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4d666-131">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d666-131">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4d666-132">此範例會在 `PasswordHash` 資料表中的 `PasswordSalt` 和 `Person.Password`資料行上建立唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="4d666-132">The example creates a unique constraint on the columns `PasswordHash` and `PasswordSalt` in the table `Person.Password`.</span></span>  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    ALTER TABLE Person.Password   
    ADD CONSTRAINT AK_Password UNIQUE (PasswordHash, PasswordSalt);   
    GO  
  
    ```  
  
#### <a name="to-create-a-unique-constraint-in-an-new-table"></a><span data-ttu-id="4d666-133">若要在新的資料表中建立唯一條件約束</span><span class="sxs-lookup"><span data-stu-id="4d666-133">To create a unique constraint in an new table</span></span>  
  
1.  <span data-ttu-id="4d666-134">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d666-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="4d666-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="4d666-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="4d666-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="4d666-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="4d666-137">此範例會建立資料表並且在 `TransactionID`資料行上定義唯一條件約束。</span><span class="sxs-lookup"><span data-stu-id="4d666-137">The example creates a table and defines a unique constraint on the column `TransactionID`.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive2  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT AK_TransactionID UNIQUE(TransactionID)  
    );  
    GO  
  
    ```  
  
     <span data-ttu-id="4d666-138">如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)、[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) 和 [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4d666-138">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql), [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql), and [table_constraint &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/table-constraints-transact-sql).</span></span>  
  
###  <a name="TsqlExample"></a>  
