---
title: 透過檢視修改資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- data modifications [SQL Server], views
- views [SQL Server], modifying data through
- modifying data [SQL Server], views
ms.assetid: 410e2812-4ebe-48b2-b95f-c7784f1c4336
author: stevestein
ms.author: sstein
ms.openlocfilehash: df1eb4a33d1d10e63363e52760dad805b20c0a8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585203"
---
# <a name="modify-data-through-a-view"></a><span data-ttu-id="9b89d-102">透過檢視修改資料</span><span class="sxs-lookup"><span data-stu-id="9b89d-102">Modify Data Through a View</span></span>
  <span data-ttu-id="9b89d-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改基礎基底資料表的資料。</span><span class="sxs-lookup"><span data-stu-id="9b89d-103">You can modify the data of an underlying base table in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="9b89d-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="9b89d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="9b89d-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9b89d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9b89d-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="9b89d-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9b89d-107">安全性</span><span class="sxs-lookup"><span data-stu-id="9b89d-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9b89d-108">**使用下列方法，透過檢視修改資料表資料：**</span><span class="sxs-lookup"><span data-stu-id="9b89d-108">**To modify table data through a view, using:**</span></span>  
  
     [<span data-ttu-id="9b89d-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9b89d-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9b89d-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9b89d-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9b89d-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="9b89d-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="9b89d-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="9b89d-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="9b89d-113">請參閱 [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql) 中的＜可更新的檢視＞一節。</span><span class="sxs-lookup"><span data-stu-id="9b89d-113">See the section 'Updatable Views' in [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9b89d-114">Security</span><span class="sxs-lookup"><span data-stu-id="9b89d-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9b89d-115">權限</span><span class="sxs-lookup"><span data-stu-id="9b89d-115">Permissions</span></span>  
 <span data-ttu-id="9b89d-116">根據執行的動作，需要目標資料表的 UPDATE、INSERT 或 DELETE 權限。</span><span class="sxs-lookup"><span data-stu-id="9b89d-116">Requires UPDATE, INSERT, or DELETE permissions on the target table, depending on the action being performed.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9b89d-117">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9b89d-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-table-data-through-a-view"></a><span data-ttu-id="9b89d-118">透過檢視修改資料表資料</span><span class="sxs-lookup"><span data-stu-id="9b89d-118">To modify table data through a view</span></span>  
  
1.  <span data-ttu-id="9b89d-119">在 **[物件總管]** 中，展開包含檢視的資料庫，然後展開 **[檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="9b89d-119">In **Object Explorer**, expand the database that contains the view and then expand **Views**.</span></span>  
  
2.  <span data-ttu-id="9b89d-120">以滑鼠右鍵按一下檢視，然後選取 [編輯前 200 個資料列]  。</span><span class="sxs-lookup"><span data-stu-id="9b89d-120">Right-click the view and select **Edit Top 200 Rows**.</span></span>  
  
3.  <span data-ttu-id="9b89d-121">您可能需要修改 **[SQL]** 窗格中的 SELECT 陳述式，才能傳回要修改的資料列。</span><span class="sxs-lookup"><span data-stu-id="9b89d-121">You may need to modify the SELECT statement in the **SQL** pane to return the rows to be modified.</span></span>  
  
4.  <span data-ttu-id="9b89d-122">在 **[結果]** 窗格中，尋找要變更或刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="9b89d-122">In the **Results** pane, locate the row to be changed or deleted.</span></span> <span data-ttu-id="9b89d-123">若要刪除資料列，請以滑鼠右鍵按一下此資料列，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="9b89d-123">To delete the row, right-click the row and select **Delete**.</span></span> <span data-ttu-id="9b89d-124">若要變更一個或多個資料行中的資料，請修改資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="9b89d-124">To change data in one or more columns, modify the data in the column.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9b89d-125">如果檢視參考多個基底資料表，就不能刪除資料列。</span><span class="sxs-lookup"><span data-stu-id="9b89d-125">You cannot delete a row if the view references more than one base table.</span></span> <span data-ttu-id="9b89d-126">您只可以更新屬於單一基底資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="9b89d-126">You can only update columns that belong to a single base table.</span></span>  
  
5.  <span data-ttu-id="9b89d-127">若要插入資料列，向下捲動到資料列的結尾，然後插入新值。</span><span class="sxs-lookup"><span data-stu-id="9b89d-127">To insert a row, scroll down to the end of the rows and insert the new values.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9b89d-128">如果檢視參考多個基底資料表，就不能插入資料列。</span><span class="sxs-lookup"><span data-stu-id="9b89d-128">You cannot insert a row if the view references more than one base table.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9b89d-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9b89d-129">Using Transact-SQL</span></span>  
  
#### <a name="to-update-table-data-through-a-view"></a><span data-ttu-id="9b89d-130">透過檢視更新資料表資料</span><span class="sxs-lookup"><span data-stu-id="9b89d-130">To update table data through a view</span></span>  
  
1.  <span data-ttu-id="9b89d-131">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b89d-131">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9b89d-132">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9b89d-132">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9b89d-133">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9b89d-133">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9b89d-134">這個範例會透過參考 `StartDate` 檢視中的資料行，變更特定員工的 `EndDate` 和 `HumanResources.vEmployeeDepartmentHistory`資料行值。</span><span class="sxs-lookup"><span data-stu-id="9b89d-134">This example changes the value in the `StartDate` and `EndDate` columns for a specific employee by referencing columns in the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="9b89d-135">此檢視從兩個資料表傳回值。</span><span class="sxs-lookup"><span data-stu-id="9b89d-135">This view returns values from two tables.</span></span> <span data-ttu-id="9b89d-136">此陳述式會成功，因為修改的資料行只來自其中一個基底資料表。</span><span class="sxs-lookup"><span data-stu-id="9b89d-136">This statement succeeds because the columns being modified are from only one of the base tables.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    UPDATE HumanResources.vEmployeeDepartmentHistory  
    SET StartDate = '20110203', EndDate = GETDATE()   
    WHERE LastName = N'Smith' AND FirstName = 'Samantha';   
    GO  
    ```  
  
 <span data-ttu-id="9b89d-137">如需詳細資訊，請參閱 [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9b89d-137">For more information, see [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql).</span></span>  
  
#### <a name="to-insert-table-data-through-a-view"></a><span data-ttu-id="9b89d-138">透過檢視插入資料表資料</span><span class="sxs-lookup"><span data-stu-id="9b89d-138">To insert table data through a view</span></span>  
  
1.  <span data-ttu-id="9b89d-139">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9b89d-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="9b89d-140">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9b89d-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9b89d-141">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="9b89d-141">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="9b89d-142">此範例會藉由指定 `HumanResouces.Department` 檢視中的相關資料行，將新資料列插入 `HumanResources.vEmployeeDepartmentHistory`基底資料表。</span><span class="sxs-lookup"><span data-stu-id="9b89d-142">The example inserts a new row into the base table `HumanResouces.Department` by specifying the relevant columns from the view `HumanResources.vEmployeeDepartmentHistory`.</span></span> <span data-ttu-id="9b89d-143">此陳述式會成功，因為只指定單一基底資料表中的資料行，而且此基底資料表中的其他資料行有預設值。</span><span class="sxs-lookup"><span data-stu-id="9b89d-143">The statement succeeds because only columns from a single base table are specified and the other columns in the base table have default values.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    INSERT INTO HumanResources.vEmployeeDepartmentHistory (Department, GroupName)   
    VALUES ('MyDepartment', 'MyGroup');   
    GO  
    ```  
  
 <span data-ttu-id="9b89d-144">如需詳細資訊，請參閱 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="9b89d-144">For more information, see [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).</span></span>  
  
  
