---
title: 刪除資料表 (Database Engine) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- table deletions [SQL Server]
- deleting tables
- removing tables
- dropping tables
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e361456534f565f854d348bbef5751c7d66c0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706349"
---
# <a name="delete-tables-database-engine"></a><span data-ttu-id="cfd93-102">刪除資料表 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="cfd93-102">Delete Tables (Database Engine)</span></span>
  <span data-ttu-id="cfd93-103">您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中刪除 (卸除) 資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="cfd93-103">You can delete (drop) a table from your database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cfd93-104">在刪除資料表之前請仔細考慮。</span><span class="sxs-lookup"><span data-stu-id="cfd93-104">Think carefully before you delete a table.</span></span> <span data-ttu-id="cfd93-105">如果現有的查詢、檢視表、使用者定義函數、預存程序或程式參考此資料表，則刪除將使這些物件失效。</span><span class="sxs-lookup"><span data-stu-id="cfd93-105">If existing queries, views, user-defined functions, stored procedures, or programs refer to that table, the deletion will make these objects invalid.</span></span>  
  
 <span data-ttu-id="cfd93-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="cfd93-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cfd93-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="cfd93-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cfd93-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="cfd93-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cfd93-109">安全性</span><span class="sxs-lookup"><span data-stu-id="cfd93-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cfd93-110">**若要使用下列項目來刪除資料表：**</span><span class="sxs-lookup"><span data-stu-id="cfd93-110">**To Delete a Table, using:**</span></span>  
  
     [<span data-ttu-id="cfd93-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cfd93-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cfd93-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cfd93-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cfd93-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="cfd93-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cfd93-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="cfd93-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cfd93-115">您無法卸除 FOREIGN KEY 條件約束所參考的資料表。</span><span class="sxs-lookup"><span data-stu-id="cfd93-115">You cannot drop a table that is referenced by a FOREIGN KEY constraint.</span></span> <span data-ttu-id="cfd93-116">您必須先卸除參考 FOREIGN KEY 條件約束或參考資料表。</span><span class="sxs-lookup"><span data-stu-id="cfd93-116">The referencing FOREIGN KEY constraint or the referencing table must first be dropped.</span></span> <span data-ttu-id="cfd93-117">如果參考資料表和持有要卸除的主索引鍵之資料表在相同的 DROP TABLE 陳述式中，就必須先列出參考資料表。</span><span class="sxs-lookup"><span data-stu-id="cfd93-117">If both the referencing table and the table that holds the primary key are being dropped in the same DROP TABLE statement, the referencing table must be listed first.</span></span>  
  
-   <span data-ttu-id="cfd93-118">當卸除資料表時，資料表的規則或預設值會失去它們的繫結，資料表的任何相關條件約束或觸發程序也都會自動卸除。</span><span class="sxs-lookup"><span data-stu-id="cfd93-118">When a table is dropped, rules or defaults on the table lose their binding, and any constraints or triggers associated with the table are automatically dropped.</span></span> <span data-ttu-id="cfd93-119">如果重新建立資料表，您必須重新繫結適當的規則和預設值、重新建立任何觸發程序，以及加入所有必要的條件約束。</span><span class="sxs-lookup"><span data-stu-id="cfd93-119">If you re-create a table, you must rebind the appropriate rules and defaults, re-create any triggers, and add all required constraints.</span></span>  
  
-   <span data-ttu-id="cfd93-120">如果卸除的資料表包含具有 FILESTREAM 屬性的 `varbinary (max)` 資料行，則儲存在檔案系統中的任何資料都不會遭到移除。</span><span class="sxs-lookup"><span data-stu-id="cfd93-120">If you drop a table that contains a `varbinary (max)` column with the FILESTREAM attribute, any data stored in the file system will not be removed.</span></span>  
  
-   <span data-ttu-id="cfd93-121">DROP TABLE 和 CREATE TABLE 不得在相同批次的相同資料表上執行。</span><span class="sxs-lookup"><span data-stu-id="cfd93-121">DROP TABLE and CREATE TABLE should not be executed on the same table in the same batch.</span></span> <span data-ttu-id="cfd93-122">否則，系統可能會發生非預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cfd93-122">Otherwise an unexpected error may occur.</span></span>  
  
-   <span data-ttu-id="cfd93-123">對於參考已卸除之資料表的任何檢視表或預存程序，您必須明確刪除或修改它們，以便移除資料表的參考。</span><span class="sxs-lookup"><span data-stu-id="cfd93-123">Any view or stored procedure that references the dropped table must be explicitly deleted or modified to remove the reference to the table.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cfd93-124">Security</span><span class="sxs-lookup"><span data-stu-id="cfd93-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cfd93-125">權限</span><span class="sxs-lookup"><span data-stu-id="cfd93-125">Permissions</span></span>  
 <span data-ttu-id="cfd93-126">需要資料表所屬結構描述的 ALTER 權限、資料表的 CONTROL 權限，或 **db_ddladmin** 固定資料庫角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="cfd93-126">Requires ALTER permission on the schema to which the table belongs, CONTROL permission on the table, or membership in the **db_ddladmin** fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cfd93-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cfd93-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-table-from-the-database"></a><span data-ttu-id="cfd93-128">若要從資料庫刪除資料表</span><span class="sxs-lookup"><span data-stu-id="cfd93-128">To delete a table from the database</span></span>  
  
1.  <span data-ttu-id="cfd93-129">在 [物件總管] 中選取要刪除的資料表。</span><span class="sxs-lookup"><span data-stu-id="cfd93-129">In Object Explorer, select the table you want to delete.</span></span>  
  
2.  <span data-ttu-id="cfd93-130">在資料表上按一下滑鼠右鍵，再從快速鍵功能表中選擇 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="cfd93-130">Right-click the table and choose **Delete** from the shortcut menu.</span></span>  
  
3.  <span data-ttu-id="cfd93-131">訊息方塊會提示您確認是否刪除。</span><span class="sxs-lookup"><span data-stu-id="cfd93-131">A message box prompts you to confirm the deletion.</span></span> <span data-ttu-id="cfd93-132">按一下 [是]  。</span><span class="sxs-lookup"><span data-stu-id="cfd93-132">Click **Yes**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cfd93-133">刪除資料表會自動移除它的所有關聯性。</span><span class="sxs-lookup"><span data-stu-id="cfd93-133">Deleting a table automatically removes any relationships to it.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cfd93-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cfd93-134">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-table-in-query-editor"></a><span data-ttu-id="cfd93-135">若要在查詢編輯器中刪除資料表</span><span class="sxs-lookup"><span data-stu-id="cfd93-135">To delete a table in Query Editor</span></span>  
  
1.  <span data-ttu-id="cfd93-136">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cfd93-136">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cfd93-137">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cfd93-137">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cfd93-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="cfd93-138">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 <span data-ttu-id="cfd93-139">如需詳細資訊，請參閱 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="cfd93-139">For more information, see [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)</span></span>  
  
  
