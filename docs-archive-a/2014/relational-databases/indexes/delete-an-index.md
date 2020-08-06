---
title: 刪除索引 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4552ba701782e5790f95f54c0c1c66f82573f1e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708293"
---
# <a name="delete-an-index"></a><span data-ttu-id="b3fb9-102">刪除索引</span><span class="sxs-lookup"><span data-stu-id="b3fb9-102">Delete an Index</span></span>
  <span data-ttu-id="b3fb9-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除 (卸除) 索引。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-103">This topic describes how to delete (drop) an index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b3fb9-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="b3fb9-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b3fb9-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="b3fb9-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b3fb9-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="b3fb9-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b3fb9-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b3fb9-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b3fb9-108">**使用下列方法刪除索引：**</span><span class="sxs-lookup"><span data-stu-id="b3fb9-108">**To delete an index, using:**</span></span>  
  
     [<span data-ttu-id="b3fb9-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3fb9-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b3fb9-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3fb9-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b3fb9-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="b3fb9-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b3fb9-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="b3fb9-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b3fb9-113">使用此方法無法刪除以 PRIMARY KEY 或 UNIQUE 條件約束之結果所建立的索引。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-113">Indexes created as the result of a PRIMARY KEY or UNIQUE constraint cannot be deleted by using this method.</span></span> <span data-ttu-id="b3fb9-114">而是必須刪除條件約束。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-114">Instead, the constraint must be deleted.</span></span> <span data-ttu-id="b3fb9-115">若要移除條件約束和對應的索引，請搭配 [中的 DROP CONSTRAINT 子句來使用](/sql/t-sql/statements/alter-table-transact-sql) ALTER TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-115">To remove the constraint and corresponding index, use [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) with the DROP CONSTRAINT clause in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b3fb9-116">如需詳細資訊，請參閱 [Delete Primary Keys](../tables/delete-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-116">For more information, see [Delete Primary Keys](../tables/delete-primary-keys.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b3fb9-117">Security</span><span class="sxs-lookup"><span data-stu-id="b3fb9-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b3fb9-118">權限</span><span class="sxs-lookup"><span data-stu-id="b3fb9-118">Permissions</span></span>  
 <span data-ttu-id="b3fb9-119">需要資料表或檢視表的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-119">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="b3fb9-120">依預設，這個權限會授與 **系統管理員** 固定伺服器角色以及 **db_ddladmin** 和 **db_owner** 固定資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-120">This permission is granted by default to the **sysadmin** fixed server role and the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b3fb9-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b3fb9-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a><span data-ttu-id="b3fb9-122">若要使用物件總管刪除索引</span><span class="sxs-lookup"><span data-stu-id="b3fb9-122">To delete an index by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="b3fb9-123">在 [物件總管] 中，展開包含您要刪除索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-123">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="b3fb9-124">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-124">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="b3fb9-125">展開包含您要刪除之索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-125">Expand the table that contains the index you want to delete.</span></span>  
  
4.  <span data-ttu-id="b3fb9-126">展開 **[索引]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-126">Expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="b3fb9-127">以滑鼠右鍵按一下您想刪除的索引，然後選取 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-127">Right-click the index you want to delete and select **Delete**.</span></span>  
  
6.  <span data-ttu-id="b3fb9-128">在 **[刪除物件]** 對話方塊中，確認 **[要刪除的物件]** 方格中有正確索引，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-128">In the **Delete Object** dialog box, verify that the correct index is in the **Object to be deleted** grid and click **OK**.</span></span>  
  
#### <a name="to-delete-an-index-using-table-designer"></a><span data-ttu-id="b3fb9-129">使用資料表設計工具刪除索引</span><span class="sxs-lookup"><span data-stu-id="b3fb9-129">To delete an index using Table Designer</span></span>  
  
1.  <span data-ttu-id="b3fb9-130">在 [物件總管] 中，展開包含您要刪除索引之資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-130">In Object Explorer, expand the database that contains the table on which you want to delete an index.</span></span>  
  
2.  <span data-ttu-id="b3fb9-131">展開 **[資料表]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-131">Expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="b3fb9-132">以滑鼠右鍵按一下包含您要刪除索引的資料表，然後按一下 [設計]。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-132">Right-click the table that contains the index you want to delete and click Design.</span></span>  
  
4.  <span data-ttu-id="b3fb9-133">在 [資料表設計工具]  功能表上，按一下 [索引/索引鍵]  。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-133">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="b3fb9-134">在 [索引/索引鍵]  對話方塊中，選取要刪除的索引。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-134">In the **Indexes/Keys** dialog box, select the index you want to delete.</span></span>  
  
6.  <span data-ttu-id="b3fb9-135">按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-135">Click **Delete**.</span></span>  
  
7.  <span data-ttu-id="b3fb9-136">按一下 [關閉]  。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-136">Click **Close**.</span></span>  
  
8.  <span data-ttu-id="b3fb9-137">在 [檔案] 功能表上，選取 [儲存 _table_name_]。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-137">On the **File** menu, select **Save**_table_name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b3fb9-138">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b3fb9-138">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-index"></a><span data-ttu-id="b3fb9-139">若要刪除索引</span><span class="sxs-lookup"><span data-stu-id="b3fb9-139">To delete an index</span></span>  
  
1.  <span data-ttu-id="b3fb9-140">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-140">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b3fb9-141">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-141">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b3fb9-142">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-142">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 <span data-ttu-id="b3fb9-143">如需詳細資訊，請參閱 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b3fb9-143">For more information, see [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql).</span></span>  
  
  
