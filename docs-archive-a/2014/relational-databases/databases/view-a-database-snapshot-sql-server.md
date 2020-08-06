---
title: 檢視資料庫快照集 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], viewing
- displaying database snapshots
- viewing database snapshots
ms.assetid: 123f19b2-0850-4033-8507-59ebdfb368ee
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92c5c557656e87be562e9d5477f14f66b2c39e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708434"
---
# <a name="view-a-database-snapshot-sql-server"></a><span data-ttu-id="32ba9-102">檢視資料庫快照集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="32ba9-102">View a Database Snapshot (SQL Server)</span></span>
  <span data-ttu-id="32ba9-103">此主題說明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="32ba9-103">This topic explains how to view a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database snapshot using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32ba9-104">若要建立、刪除或還原為資料庫快照集，都必須使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="32ba9-104">To create, revert to, or delete a database snapshot, you must use [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="32ba9-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="32ba9-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="32ba9-106">**若要檢視資料庫快照集，請使用：**</span><span class="sxs-lookup"><span data-stu-id="32ba9-106">**To view a database snapshot, using:**</span></span>  
  
     [<span data-ttu-id="32ba9-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="32ba9-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="32ba9-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32ba9-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="32ba9-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="32ba9-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="32ba9-110">**若要檢視資料庫快照集**</span><span class="sxs-lookup"><span data-stu-id="32ba9-110">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="32ba9-111">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="32ba9-111">In Object Explorer, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="32ba9-112">展開 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="32ba9-112">Expand **Databases.**</span></span>  
  
3.  <span data-ttu-id="32ba9-113">展開 **[資料庫快照集]** ，然後選取想要檢視的快照集。</span><span class="sxs-lookup"><span data-stu-id="32ba9-113">Expand **Database Snapshots**, and select the snapshot you want to view.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="32ba9-114">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="32ba9-114">Using Transact-SQL</span></span>  
 <span data-ttu-id="32ba9-115">**若要檢視資料庫快照集**</span><span class="sxs-lookup"><span data-stu-id="32ba9-115">**To view a database snapshot**</span></span>  
  
1.  <span data-ttu-id="32ba9-116">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="32ba9-116">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="32ba9-117">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="32ba9-117">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="32ba9-118">若要列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的資料庫快照集，請查詢 **sys.databases** 目錄檢視的 [source_database_id](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 資料行看看是否有非 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="32ba9-118">To list the database snapshots of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], query the **source_database_id** column of the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view for non-NULL values.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="32ba9-119">相關工作</span><span class="sxs-lookup"><span data-stu-id="32ba9-119">Related Tasks</span></span>  
  
-   [<span data-ttu-id="32ba9-120">建立資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32ba9-120">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="32ba9-121">將資料庫還原成資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="32ba9-121">Revert a Database to a Database Snapshot</span></span>](revert-a-database-to-a-database-snapshot.md)  
  
-   [<span data-ttu-id="32ba9-122">卸除資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="32ba9-122">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="32ba9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32ba9-123">See Also</span></span>  
 [<span data-ttu-id="32ba9-124">資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="32ba9-124">Database Snapshots &#40;SQL Server&#41;</span></span>](database-snapshots-sql-server.md)  
  
  
