---
title: 移除無用的檔案群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- piecemeal restores [SQL Server], defunct filegroups
- defunct filegroups
- restoring filegroups [SQL Server]
- deferred transactions
- filegroups [SQL Server], defunct
- unrestored filegroups
ms.assetid: 055f9c6a-5c18-4942-98e7-ec918f0ff975
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2bcba095d668c5c1ab317269a18af4dc996f63b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705197"
---
# <a name="remove-defunct-filegroups-sql-server"></a><span data-ttu-id="58cd0-102">移除無用的檔案群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="58cd0-102">Remove Defunct Filegroups (SQL Server)</span></span>
  <span data-ttu-id="58cd0-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來移除 [!INCLUDE[tsql](../../includes/tsql-md.md)]中無用的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="58cd0-103">This topic describes how to remove defunct filegroups in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="58cd0-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="58cd0-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="58cd0-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="58cd0-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="58cd0-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="58cd0-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="58cd0-107">建議</span><span class="sxs-lookup"><span data-stu-id="58cd0-107">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="58cd0-108">安全性</span><span class="sxs-lookup"><span data-stu-id="58cd0-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="58cd0-109">**若要使用下列項目移除無用的檔案群組：**</span><span class="sxs-lookup"><span data-stu-id="58cd0-109">**To remove defunct filegroups, using:**</span></span>  
  
     [<span data-ttu-id="58cd0-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58cd0-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="58cd0-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58cd0-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="58cd0-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="58cd0-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="58cd0-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="58cd0-113">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="58cd0-114">本主題與包含多個檔案或檔案群組而且在簡單模式下僅供唯讀之檔案群組的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="58cd0-114">This topic is relevant for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that contain multiple files or filegroups; and, under the simple model, only for read-only filegroups.</span></span>  
  
-   <span data-ttu-id="58cd0-115">當移除了離線檔案群組，在檔案群組中的所有檔案就會變成無用。</span><span class="sxs-lookup"><span data-stu-id="58cd0-115">All files in a filegroup become defunct when an offline filegroup is removed.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="58cd0-116">建議</span><span class="sxs-lookup"><span data-stu-id="58cd0-116">Recommendations</span></span>  
  
-   <span data-ttu-id="58cd0-117">如果未還原的檔案群組永遠都不需要還原，您可以從資料庫中將它移除，讓檔案群組成為 *「無用」* 。</span><span class="sxs-lookup"><span data-stu-id="58cd0-117">If an unrestored filegroup will never have to be restored, you can make the filegroup *defunct* by removing it from the database.</span></span> <span data-ttu-id="58cd0-118">無用的檔案群組永遠都不能還原至此資料庫，但其中繼資料繼續保留在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="58cd0-118">The defunct filegroup can never be restored to this database, but its metadata remains.</span></span> <span data-ttu-id="58cd0-119">檔案群組變成無用之後，資料庫可以重新啟動，復原會讓資料庫在已還原的檔案群組之間保持一致。</span><span class="sxs-lookup"><span data-stu-id="58cd0-119">After the filegroup is defunct, the database can be restarted, and recovery will make the database consistent across the restored filegroups.</span></span>  
  
     <span data-ttu-id="58cd0-120">例如，讓檔案群組成為無用是解決因資料庫中不再需要的離線群組而造成之延遲交易的一項選擇。</span><span class="sxs-lookup"><span data-stu-id="58cd0-120">For example, making a filegroup defunct is an option for resolving deferred transactions that were caused by an offline filegroup that you no longer want in the database.</span></span> <span data-ttu-id="58cd0-121">因檔案群組離線而延遲的交易會在檔案群組變成無用之後移出延遲狀態。</span><span class="sxs-lookup"><span data-stu-id="58cd0-121">Transactions that were deferred because the filegroup was offline are moved out of the deferred state after the filegroup becomes defunct.</span></span> <span data-ttu-id="58cd0-122">如需詳細資訊，請參閱 [延遲交易 &#40;SQL Server&#41;](deferred-transactions-sql-server.md)中無用的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="58cd0-122">For more information, see [Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="58cd0-123">Security</span><span class="sxs-lookup"><span data-stu-id="58cd0-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="58cd0-124">權限</span><span class="sxs-lookup"><span data-stu-id="58cd0-124">Permissions</span></span>  
 <span data-ttu-id="58cd0-125">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="58cd0-125">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="58cd0-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="58cd0-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="58cd0-127">若要移除無用的檔案群組</span><span class="sxs-lookup"><span data-stu-id="58cd0-127">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="58cd0-128">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="58cd0-128">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="58cd0-129">展開 **[資料庫]** ，以滑鼠右鍵按一下要從中刪除檔案的資料庫，再按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="58cd0-129">Expand **Databases**, right-click the database from which to delete the file, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="58cd0-130">選取 **[檔案]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="58cd0-130">Select the **Files** page.</span></span>  
  
4.  <span data-ttu-id="58cd0-131">在 **[資料庫檔案]** 方格中，選取要刪除的檔案，按一下 **[移除]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58cd0-131">In the **Database files** grid, select the files to delete, click **Remove**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="58cd0-132">選取 **[檔案群組]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="58cd0-132">Select the **Filegroups** page.</span></span>  
  
6.  <span data-ttu-id="58cd0-133">在 **[資料列]** 方格中，選取要刪除的檔案群組，按一下 **[移除]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="58cd0-133">In the **Rows** grid, select the filegroup to delete, click **Remove**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="58cd0-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="58cd0-134">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-defunct-filegroups"></a><span data-ttu-id="58cd0-135">若要移除無用的檔案群組</span><span class="sxs-lookup"><span data-stu-id="58cd0-135">To remove defunct filegroups</span></span>  
  
1.  <span data-ttu-id="58cd0-136">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="58cd0-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="58cd0-137">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="58cd0-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="58cd0-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="58cd0-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="58cd0-139">**注意：** 此範例假設檔案和檔案群組都已經存在。</span><span class="sxs-lookup"><span data-stu-id="58cd0-139">(**Note:** This example assumes that the files and filegroup already exist.</span></span> <span data-ttu-id="58cd0-140">若要建立這些物件，請參閱 [ALTER DATABASE 檔案及檔案群組選項](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)主題中的範例 B。)第一個範例會使用 `test1dat3` 陳述式搭配 `test1dat4` 子句，從無用的檔案群組中移除 `ALTER DATABASE` 和 `REMOVE FILE` 檔案。</span><span class="sxs-lookup"><span data-stu-id="58cd0-140">To create these objects, see example B in the [ALTER DATABASE File and Filegroup Options](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) topic.) The first example removes the `test1dat3` and `test1dat4` files from the defunct filegroup by using the `ALTER DATABASE` statement with the `REMOVE FILE` clause.</span></span> <span data-ttu-id="58cd0-141">第二個範例會使用 `Test1FG1`子句，移除無用的檔案群組 `REMOVE FILEGROUP` 。</span><span class="sxs-lookup"><span data-stu-id="58cd0-141">The second example removes the defunct filegroup `Test1FG1`by using the `REMOVE FILEGROUP` clause.</span></span>  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat3 ;  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4 ;  
GO  
  
```  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILEGROUP Test1FG1 ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="58cd0-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58cd0-142">See Also</span></span>  
 <span data-ttu-id="58cd0-143">[ALTER DATABASE 檔案及檔案群組選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span><span class="sxs-lookup"><span data-stu-id="58cd0-143">[ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options) </span></span>  
 <span data-ttu-id="58cd0-144">[延遲交易 &#40;SQL Server&#41;](deferred-transactions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="58cd0-144">[Deferred Transactions &#40;SQL Server&#41;](deferred-transactions-sql-server.md) </span></span>  
 <span data-ttu-id="58cd0-145">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="58cd0-145">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="58cd0-146">[檔案還原 &#40;簡單復原模式&#41;](file-restores-simple-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="58cd0-146">[File Restores &#40;Simple Recovery Model&#41;](file-restores-simple-recovery-model.md) </span></span>  
 <span data-ttu-id="58cd0-147">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="58cd0-147">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="58cd0-148">[還原頁面 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="58cd0-148">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 [<span data-ttu-id="58cd0-149">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="58cd0-149">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  
