---
title: 刪除資料庫 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database removal [SQL Server], SQL Server Management Studio
- removing databases
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- database removal [SQL Server]
ms.assetid: 1fd8c0f5-03e1-449a-af45-b8cacb479d9c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 633d97815cf69da12f1aa67fd8ef626a2d46e0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709558"
---
# <a name="delete-a-database"></a><span data-ttu-id="c0d02-102">刪除資料庫</span><span class="sxs-lookup"><span data-stu-id="c0d02-102">Delete a Database</span></span>
  <span data-ttu-id="c0d02-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [!INCLUDE[tsql](../../includes/tsql-md.md)]刪除使用者定義資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0d02-103">This topic describes how to delete a user-defined database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c0d02-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c0d02-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c0d02-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c0d02-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c0d02-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="c0d02-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c0d02-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="c0d02-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="c0d02-108">建議</span><span class="sxs-lookup"><span data-stu-id="c0d02-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c0d02-109">安全性</span><span class="sxs-lookup"><span data-stu-id="c0d02-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c0d02-110">**使用下列方法刪除資料庫：**</span><span class="sxs-lookup"><span data-stu-id="c0d02-110">**To delete a database, using:**</span></span>  
  
     [<span data-ttu-id="c0d02-111">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c0d02-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c0d02-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c0d02-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="c0d02-113">**後續操作：** [刪除資料庫之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="c0d02-113">**Follow Up:**  [After deleting a database](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c0d02-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="c0d02-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="c0d02-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="c0d02-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="c0d02-116">您無法刪除系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0d02-116">System databases cannot be deleted.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c0d02-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="c0d02-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="c0d02-118">刪除資料庫上的資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="c0d02-118">Delete any database snapshots that exist on the database.</span></span> <span data-ttu-id="c0d02-119">如需詳細資訊，請參閱 [卸除資料庫快照集 &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0d02-119">For more information, see [Drop a Database Snapshot &#40;Transact-SQL&#41;](drop-a-database-snapshot-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="c0d02-120">如果資料庫有相關的記錄傳送，請移除記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="c0d02-120">If the database is involved in log shipping, remove log shipping.</span></span>  
  
-   <span data-ttu-id="c0d02-121">如果資料庫已發行供異動複寫之用，或已發行至或訂閱合併式複寫，請移除資料庫的複寫。</span><span class="sxs-lookup"><span data-stu-id="c0d02-121">If the database is published for transactional replication, or published or subscribed to merge replication, remove replication from the database.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c0d02-122">建議</span><span class="sxs-lookup"><span data-stu-id="c0d02-122">Recommendations</span></span>  
  
-   <span data-ttu-id="c0d02-123">請考慮為資料庫進行完整備份。</span><span class="sxs-lookup"><span data-stu-id="c0d02-123">Consider taking a full backup of the database.</span></span> <span data-ttu-id="c0d02-124">已刪除的資料庫只能透過還原備份來重新建立。</span><span class="sxs-lookup"><span data-stu-id="c0d02-124">A deleted database can be re-created only by restoring a backup.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c0d02-125">Security</span><span class="sxs-lookup"><span data-stu-id="c0d02-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c0d02-126">權限</span><span class="sxs-lookup"><span data-stu-id="c0d02-126">Permissions</span></span>  
 <span data-ttu-id="c0d02-127">若要執行 DROP DATABASE，使用者至少必須對該資料庫具備 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="c0d02-127">To execute DROP DATABASE, at a minimum, a user must have CONTROL permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c0d02-128">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c0d02-128">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="c0d02-129">若要刪除資料庫</span><span class="sxs-lookup"><span data-stu-id="c0d02-129">To delete a database</span></span>  
  
1.  <span data-ttu-id="c0d02-130">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0d02-130">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="c0d02-131">展開 **[資料庫]** ，以滑鼠右鍵按一下要刪除的資料庫，再按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="c0d02-131">Expand **Databases**, right-click the database to delete, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="c0d02-132">確認已選取正確的資料庫，再按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="c0d02-132">Confirm the correct database is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c0d02-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c0d02-133">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-a-database"></a><span data-ttu-id="c0d02-134">若要刪除資料庫</span><span class="sxs-lookup"><span data-stu-id="c0d02-134">To delete a database</span></span>  
  
1.  <span data-ttu-id="c0d02-135">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c0d02-135">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c0d02-136">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c0d02-136">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c0d02-137">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="c0d02-137">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="c0d02-138">此範例會移除 `Sales` 和 `NewSales` 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0d02-138">The example removes the `Sales` and `NewSales` databases.</span></span>  
  
```sql  
USE master ;  
GO  
DROP DATABASE Sales, NewSales ;  
GO  
```  
  
##  <a name="follow-up-after-deleting-a-database"></a><a name="FollowUp"></a> <span data-ttu-id="c0d02-139">後續操作：刪除資料庫之後</span><span class="sxs-lookup"><span data-stu-id="c0d02-139">Follow Up: After deleting a database</span></span>  
 <span data-ttu-id="c0d02-140">備份 **master** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0d02-140">Back up the **master** database.</span></span> <span data-ttu-id="c0d02-141">如果必須還原 **master** ，在上次備份 **master** 之後被刪除的資料庫，還是會在系統目錄檢視中留有參考，並可能會造成錯誤訊息出現。</span><span class="sxs-lookup"><span data-stu-id="c0d02-141">If **master** must be restored, any database that has been deleted since the last backup of **master** will still have references in the system catalog views and may cause error messages to be raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d02-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0d02-142">See Also</span></span>  
 <span data-ttu-id="c0d02-143">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c0d02-143">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="c0d02-144">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c0d02-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
