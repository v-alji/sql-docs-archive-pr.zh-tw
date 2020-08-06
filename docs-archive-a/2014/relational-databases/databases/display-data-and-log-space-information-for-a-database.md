---
title: 顯示資料庫的資料和記錄空間資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], space
- status information [SQL Server], space
- displaying space information
- disk space [SQL Server], displaying
- databases [SQL Server], space used
- viewing space information
- space allocation [SQL Server], displaying
- data space [SQL Server]
ms.assetid: c7b99463-4bab-4e9b-9217-fcb0898dc757
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1beb8cdedbc2b72eadeeb350ee1c3b6d16218205
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709554"
---
# <a name="display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="e94d1-102">顯示資料庫的資料和記錄空間資訊</span><span class="sxs-lookup"><span data-stu-id="e94d1-102">Display Data and Log Space Information for a Database</span></span>
  <span data-ttu-id="e94d1-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中顯示資料庫的資料和記錄檔空間資訊。</span><span class="sxs-lookup"><span data-stu-id="e94d1-103">This topic describes how to display the data and log space information for a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="e94d1-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="e94d1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e94d1-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e94d1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e94d1-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e94d1-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e94d1-107">**使用下列方法，顯示資料庫的資料和記錄空間資訊：**</span><span class="sxs-lookup"><span data-stu-id="e94d1-107">**To display data and log space information for a database, using:**</span></span>  
  
     [<span data-ttu-id="e94d1-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e94d1-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e94d1-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e94d1-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e94d1-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="e94d1-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e94d1-111">Security</span><span class="sxs-lookup"><span data-stu-id="e94d1-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e94d1-112">權限</span><span class="sxs-lookup"><span data-stu-id="e94d1-112">Permissions</span></span>  
 <span data-ttu-id="e94d1-113">執行 **sp_spaceused** 的權限會授與 **public** 角色。</span><span class="sxs-lookup"><span data-stu-id="e94d1-113">Permission to execute **sp_spaceused** is granted to the **public** role.</span></span> <span data-ttu-id="e94d1-114">只有 **db_owner** 固定資料庫角色的成員，才能夠指定 **@updateusage** 參數。</span><span class="sxs-lookup"><span data-stu-id="e94d1-114">Only members of the **db_owner** fixed database role can specify the **@updateusage** parameter.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e94d1-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e94d1-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database"></a><span data-ttu-id="e94d1-116">若要顯示資料庫的資料和記錄空間資訊</span><span class="sxs-lookup"><span data-stu-id="e94d1-116">To display data and log space information for a database</span></span>  
  
1.  <span data-ttu-id="e94d1-117">在物件總管中，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="e94d1-117">In Object Explorer, connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="e94d1-118">展開 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="e94d1-118">Expand **Databases**.</span></span>  
  
3.  <span data-ttu-id="e94d1-119">以滑鼠右鍵按一下資料庫，然後依序指向 [報表]、[標準報表]，再按一下 [磁碟使用量]。</span><span class="sxs-lookup"><span data-stu-id="e94d1-119">Right-click a database, point to **Reports**, point to **Standard Reports,**, and then click **Disk Usage**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e94d1-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e94d1-120">Using Transact-SQL</span></span>  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-using-sp_spaceused"></a><span data-ttu-id="e94d1-121">使用 sp_spaceused 顯示資料庫的資料和記錄空間資訊</span><span class="sxs-lookup"><span data-stu-id="e94d1-121">To display data and log space information for a database by using sp_spaceused</span></span>  
  
1.  <span data-ttu-id="e94d1-122">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e94d1-122">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e94d1-123">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e94d1-123">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e94d1-124">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e94d1-124">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e94d1-125">這個範例使用 [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) 系統預存程序來報告 `Vendor` 資料表及其索引的磁碟空間資訊。</span><span class="sxs-lookup"><span data-stu-id="e94d1-125">This example uses the [sp_spaceused](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) system stored procedure to report disk space information for the `Vendor` table and its indexes.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
#### <a name="to-display-data-and-log-space-information-for-a-database-by-querying-sysdatabase_files"></a><span data-ttu-id="e94d1-126">透過查詢 sys.database_files 來顯示資料庫的資料和記錄空間資訊</span><span class="sxs-lookup"><span data-stu-id="e94d1-126">To display data and log space information for a database by querying sys.database_files</span></span>  
  
1.  <span data-ttu-id="e94d1-127">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e94d1-127">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="e94d1-128">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="e94d1-128">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="e94d1-129">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="e94d1-129">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="e94d1-130">這個範例會查詢 [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) 目錄檢視，以傳回有關 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中資料和記錄檔的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="e94d1-130">This example queries the [sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) catalog view to return specific information about the data and log files in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name, type_desc, physical_name, size, max_size  
FROM sys.database_files ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="e94d1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e94d1-131">See Also</span></span>  
 <span data-ttu-id="e94d1-132">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e94d1-132">[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) </span></span>  
 <span data-ttu-id="e94d1-133">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e94d1-133">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="e94d1-134">[sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e94d1-134">[sp_spaceused &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-spaceused-transact-sql) </span></span>  
 <span data-ttu-id="e94d1-135">[將資料或記錄檔加入資料庫](add-data-or-log-files-to-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="e94d1-135">[Add Data or Log Files to a Database](add-data-or-log-files-to-a-database.md) </span></span>  
 [<span data-ttu-id="e94d1-136">刪除資料庫的資料或記錄檔</span><span class="sxs-lookup"><span data-stu-id="e94d1-136">Delete Data or Log Files from a Database</span></span>](delete-data-or-log-files-from-a-database.md)  
  
  
