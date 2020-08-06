---
title: 卸除資料庫快照集 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
ms.openlocfilehash: e0d9d912a092e581fad7d3d53504309f63ba1806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584563"
---
# <a name="drop-a-database-snapshot-transact-sql"></a><span data-ttu-id="dca72-102">卸除資料庫快照集 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dca72-102">Drop a Database Snapshot (Transact-SQL)</span></span>
  <span data-ttu-id="dca72-103">卸除資料庫快照集，就會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 刪除資料庫快照集，並刪除快照集所使用的疏鬆檔案。</span><span class="sxs-lookup"><span data-stu-id="dca72-103">Dropping a database snapshot deletes the database snapshot from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and deletes the sparse files that are used by the snapshot.</span></span> <span data-ttu-id="dca72-104">卸除資料庫快照集後，快照集的所有使用者連接都會結束。</span><span class="sxs-lookup"><span data-stu-id="dca72-104">When you drop a database snapshot, all user connections to it are terminated.</span></span>  
  
## <a name="security"></a><span data-ttu-id="dca72-105">安全性</span><span class="sxs-lookup"><span data-stu-id="dca72-105">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="dca72-106">權限</span><span class="sxs-lookup"><span data-stu-id="dca72-106">Permissions</span></span>  
 <span data-ttu-id="dca72-107">具有 DROP DATABASE 權限的任何使用者都可以卸除資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="dca72-107">Any user with DROP DATABASE permissions can drop a database snapshot.</span></span>  
  
##  <a name="how-to-drop-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="dca72-108">如何卸除資料庫快照集 (使用 Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dca72-108">How to Drop a Database Snapshot (Using Transact-SQL)</span></span>  
 <span data-ttu-id="dca72-109">**若要卸除資料庫快照集**</span><span class="sxs-lookup"><span data-stu-id="dca72-109">**To drop a database snapshot**</span></span>  
  
1.  <span data-ttu-id="dca72-110">識別您想要卸除的資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="dca72-110">Identify the database snapshot that you want to drop.</span></span> <span data-ttu-id="dca72-111">您可以檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中之資料庫的快照集。</span><span class="sxs-lookup"><span data-stu-id="dca72-111">You can view the snapshots on a database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="dca72-112">如需詳細資訊，請參閱 [檢視資料庫快照集 &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)中之資料庫的快照集。</span><span class="sxs-lookup"><span data-stu-id="dca72-112">For more information, see [View a Database Snapshot &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="dca72-113">發出 [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) 陳述式，並指定所要卸除之資料庫快照集的名稱。</span><span class="sxs-lookup"><span data-stu-id="dca72-113">Issue a [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) statement, specifying the name of the database snapshot to be dropped.</span></span> <span data-ttu-id="dca72-114">語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="dca72-114">The syntax is as follows:</span></span>  
  
     <span data-ttu-id="dca72-115">DROP DATABASE *database_snapshot_name* [ **,** ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="dca72-115">DROP DATABASE *database_snapshot_name* [ **,**...*n* ]</span></span>  
  
     <span data-ttu-id="dca72-116">其中， *database_snapshot_name* 是所要卸除之資料庫快照集的名稱。</span><span class="sxs-lookup"><span data-stu-id="dca72-116">Where *database_snapshot_name* is the name of the database snapshot to be dropped.</span></span>  
  
####  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="dca72-117">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dca72-117">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="dca72-118">下列範例會卸除名為 SalesSnapshot0600 的資料庫快照集，而不會影響來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="dca72-118">This example drops a database snapshot named SalesSnapshot0600, without affecting the source database.</span></span>  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 <span data-ttu-id="dca72-119">SalesSnapshot0600 的任何使用者連接都會結束，而且快照集所使用的所有 NTFS 檔案系統疏鬆檔案也都會被刪除。</span><span class="sxs-lookup"><span data-stu-id="dca72-119">Any user connections to SalesSnapshot0600 are terminated, and all of the NTFS file system sparse files used by the snapshot are deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dca72-120">如需資料庫快照集使用疏鬆檔案的相關資訊，請參閱 [資料庫快照集 &#40;SQL Server&#41;](database-snapshots-sql-server.md)中之資料庫的快照集。</span><span class="sxs-lookup"><span data-stu-id="dca72-120">For information about the use of sparse files by database snapshots, see [Database Snapshots &#40;SQL Server&#41;](database-snapshots-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="dca72-121">相關工作</span><span class="sxs-lookup"><span data-stu-id="dca72-121">Related Tasks</span></span>  
  
-   [<span data-ttu-id="dca72-122">建立資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dca72-122">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="dca72-123">檢視資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dca72-123">View a Database Snapshot &#40;SQL Server&#41;</span></span>](view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="dca72-124">將資料庫還原成資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="dca72-124">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="dca72-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dca72-125">See Also</span></span>  
 <span data-ttu-id="dca72-126">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="dca72-126">[DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) </span></span>  
 [<span data-ttu-id="dca72-127">資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="dca72-127">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
