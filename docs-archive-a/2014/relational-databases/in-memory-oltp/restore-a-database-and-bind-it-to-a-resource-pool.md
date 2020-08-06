---
title: 還原資料庫並將其繫結至資源集區 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0d20a569-8a27-409c-bcab-0effefb48013
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0b518c93ca9d5e7157ceaa20d9548d7b6061017d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584509"
---
# <a name="restore-a-database-and-bind-it-to-a-resource-pool"></a><span data-ttu-id="82ffc-102">還原資料庫並將其繫結至資源集區</span><span class="sxs-lookup"><span data-stu-id="82ffc-102">Restore a Database and Bind it to a Resource Pool</span></span>
  <span data-ttu-id="82ffc-103">即使您有足夠的記憶體來還原含有記憶體最佳化資料表的資料庫，建議您還是依照最佳做法，將資料庫繫結至具名資源集區。</span><span class="sxs-lookup"><span data-stu-id="82ffc-103">Even though you have enough memory to restore a database with memory-optimized tables, you want to follow best practices and bind the database to a named resource pool.</span></span> <span data-ttu-id="82ffc-104">因為資料庫必須先存在，然後您才能將它繫結至集區，而且還原資料庫是一項具有多重步驟的程序。</span><span class="sxs-lookup"><span data-stu-id="82ffc-104">Since the database must exist before you can bind it to the pool restoring your database is a multi-step process.</span></span> <span data-ttu-id="82ffc-105">本主題會逐步引導您完成該程序。</span><span class="sxs-lookup"><span data-stu-id="82ffc-105">This topic walks you through that process.</span></span>  
  
##  <a name="restore-with-norecovery"></a><span data-ttu-id="82ffc-106">使用 NORECOVERY 還原</span><span class="sxs-lookup"><span data-stu-id="82ffc-106">Restore with NORECOVERY</span></span>  
 <span data-ttu-id="82ffc-107">當您還原資料庫時，NORECOVERY 會建立資料庫並還原磁碟映像，但不會耗用任何記憶體。</span><span class="sxs-lookup"><span data-stu-id="82ffc-107">When you restore a database, NORECOVERY causes the database to be created and the disk image restored without consuming memory.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   FROM DISK = 'C:\IMOLTP_test\IMOLTP_DB.bak'  
   WITH NORECOVERY  
```  
  
##  <a name="create-the-resource-pool"></a><span data-ttu-id="82ffc-108">建立資源集區</span><span class="sxs-lookup"><span data-stu-id="82ffc-108">Create the resource pool</span></span>  
 <span data-ttu-id="82ffc-109">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會建立名為 Pool_IMOLTP 的資源集區，而且有 50% 的記憶體可供它使用。</span><span class="sxs-lookup"><span data-stu-id="82ffc-109">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] creates a resource pool named Pool_IMOLTP with 50% of memory available for its use.</span></span>  <span data-ttu-id="82ffc-110">建立集區之後，資源管理員會重新設定為包含 Pool_IMOLTP。</span><span class="sxs-lookup"><span data-stu-id="82ffc-110">After the pool is created, the Resource Governor is reconfigured to include Pool_IMOLTP.</span></span>  
  
```sql  
CREATE RESOURCE POOL Pool_IMOLTP WITH (MAX_MEMORY_PERCENT = 50);  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
##  <a name="bind-the-database-and-resource-pool"></a><span data-ttu-id="82ffc-111">繫結資料庫和資源集區</span><span class="sxs-lookup"><span data-stu-id="82ffc-111">Bind the database and resource pool</span></span>  
 <span data-ttu-id="82ffc-112">您可以使用系統函數 `sp_xtp_bind_db_resource_pool` ，將資料庫繫結至資源集區。</span><span class="sxs-lookup"><span data-stu-id="82ffc-112">Use the system function `sp_xtp_bind_db_resource_pool` to bind the database to the resource pool.</span></span> <span data-ttu-id="82ffc-113">此函數會採用兩個參數：資料庫名稱，後面接著資源集區名稱。</span><span class="sxs-lookup"><span data-stu-id="82ffc-113">The function takes two parameters: the database name followed by the resource pool name.</span></span>  
  
 <span data-ttu-id="82ffc-114">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會定義 IMOLTP_DB 資料庫與 Pool_IMOLTP 資源集區的繫結。</span><span class="sxs-lookup"><span data-stu-id="82ffc-114">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] defines a binding of the database IMOLTP_DB to the resource pool Pool_IMOLTP.</span></span> <span data-ttu-id="82ffc-115">在您完成下一個步驟之前，此繫結不會生效。</span><span class="sxs-lookup"><span data-stu-id="82ffc-115">The binding does not become effective until you complete the next step.</span></span>  
  
```sql  
EXEC sp_xtp_bind_db_resource_pool 'IMOLTP_DB', 'Pool_IMOLTP'  
GO  
```  
  
##  <a name="restore-with-recovery"></a><span data-ttu-id="82ffc-116">使用 RECOVERY 還原</span><span class="sxs-lookup"><span data-stu-id="82ffc-116">Restore with RECOVERY</span></span>  
 <span data-ttu-id="82ffc-117">當您使用 RECOVERY 來還原資料庫時，資料庫就會重新上線並且還原所有資料。</span><span class="sxs-lookup"><span data-stu-id="82ffc-117">When you restore the database with recovery the database is brought online and all the data restored.</span></span>  
  
```sql  
RESTORE DATABASE IMOLTP_DB   
   WITH RECOVERY  
```  
  
##  <a name="monitor-the-resource-pool-performance"></a><span data-ttu-id="82ffc-118">監視資源集區效能</span><span class="sxs-lookup"><span data-stu-id="82ffc-118">Monitor the resource pool performance</span></span>  
 <span data-ttu-id="82ffc-119">一旦將資料庫繫結至具名資源集區並使用復原功能還原之後，請監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、Resource Pool Stats 物件。</span><span class="sxs-lookup"><span data-stu-id="82ffc-119">Once the database is bound to the named resource pool and restored with recovery, monitor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Resource Pool Stats Object.</span></span> <span data-ttu-id="82ffc-120">如需詳細資訊，請參閱＜ [SQL Server、Resource Pool Stats 物件](../performance-monitor/sql-server-resource-pool-stats-object.md)＞。</span><span class="sxs-lookup"><span data-stu-id="82ffc-120">For more information see [SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82ffc-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82ffc-121">See Also</span></span>  
 <span data-ttu-id="82ffc-122">[資料庫並繫結至資源集區的指引，請參閱](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="82ffc-122">[Bind a Database with Memory-Optimized Tables to a Resource Pool](bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md) </span></span>  
 <span data-ttu-id="82ffc-123">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="82ffc-123">[sys.sp_xtp_bind_db_resource_pool &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="82ffc-124">[SQL Server, Resource Pool Stats 物件](../performance-monitor/sql-server-resource-pool-stats-object.md) </span><span class="sxs-lookup"><span data-stu-id="82ffc-124">[SQL Server, Resource Pool Stats Object](../performance-monitor/sql-server-resource-pool-stats-object.md) </span></span>  
 [<span data-ttu-id="82ffc-125">sys.dm_resource_governor_resource_pools</span><span class="sxs-lookup"><span data-stu-id="82ffc-125">sys.dm_resource_governor_resource_pools</span></span>](/sql/relational-databases/system-stored-procedures/sys-sp-xtp-unbind-db-resource-pool-transact-sql)  
  
  
