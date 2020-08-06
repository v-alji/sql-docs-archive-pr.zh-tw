---
title: 檢視 SQL Server 執行個體上的資料庫清單 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- current databases
- databases currently on server [SQL Server]
- database list [SQL Server]
- viewing database list
- displaying database list
- databases [SQL Server], viewing
- servers [SQL Server], databases listed on
- listing databases
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 47283fa9065a0b9d6238dab804094d9a65d17897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708433"
---
# <a name="view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="1b23d-102">檢視 SQL Server 執行個體上的資料庫清單</span><span class="sxs-lookup"><span data-stu-id="1b23d-102">View a List of Databases on an Instance of SQL Server</span></span>
  <span data-ttu-id="1b23d-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來檢視 [!INCLUDE[tsql](../../includes/tsql-md.md)]執行個體上的資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="1b23d-103">This topic describes how to view a list of databases on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1b23d-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="1b23d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1b23d-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1b23d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1b23d-106">安全性</span><span class="sxs-lookup"><span data-stu-id="1b23d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1b23d-107">**使用下列方法檢視 SQL Server 執行個體上的資料庫清單：**</span><span class="sxs-lookup"><span data-stu-id="1b23d-107">**To view a list of databases on an instance of SQL Server, using:**</span></span>  
  
     [<span data-ttu-id="1b23d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1b23d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1b23d-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1b23d-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1b23d-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="1b23d-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1b23d-111">Security</span><span class="sxs-lookup"><span data-stu-id="1b23d-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1b23d-112">權限</span><span class="sxs-lookup"><span data-stu-id="1b23d-112">Permissions</span></span>  
 <span data-ttu-id="1b23d-113">如果 **sys.databases** 的呼叫端不是資料庫的擁有者，而且該資料庫不是 **master** 或 **tempdb**，那麼要查看對應資料列所需具備的最低權限，就是 ALTER ANY DATABASE 或 VIEW ANY DATABASE 伺服器層級權限，或是 **master** 資料庫中的 CREATE DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="1b23d-113">If the caller of **sys.databases** is not the owner of the database and the database is not **master** or **tempdb**, the minimum permissions required to see the corresponding row are ALTER ANY DATABASE or VIEW ANY DATABASE server-level permission, or CREATE DATABASE permission in the **master** database.</span></span> <span data-ttu-id="1b23d-114">呼叫端所連接的資料庫，永遠可以在 **sys.databases**中進行檢視。</span><span class="sxs-lookup"><span data-stu-id="1b23d-114">The database to which the caller is connected can always be viewed in **sys.databases**.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1b23d-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1b23d-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="1b23d-116">若要檢視 SQL Server 執行個體上的資料庫清單</span><span class="sxs-lookup"><span data-stu-id="1b23d-116">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="1b23d-117">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b23d-117">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="1b23d-118">若要查看執行個體上所有資料庫的清單，請展開 **[資料庫]** 。</span><span class="sxs-lookup"><span data-stu-id="1b23d-118">To see a list of all databases on the instance, expand **Databases**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1b23d-119">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1b23d-119">Using Transact-SQL</span></span>  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a><span data-ttu-id="1b23d-120">若要檢視 SQL Server 執行個體上的資料庫清單</span><span class="sxs-lookup"><span data-stu-id="1b23d-120">To view a list of databases on an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="1b23d-121">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1b23d-121">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1b23d-122">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="1b23d-122">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1b23d-123">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="1b23d-123">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1b23d-124">此範例會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上的資料庫清單。</span><span class="sxs-lookup"><span data-stu-id="1b23d-124">This example returns a list of databases on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1b23d-125">此清單包含資料庫名稱、其資料庫識別碼和建立資料庫的日期。</span><span class="sxs-lookup"><span data-stu-id="1b23d-125">The list includes the names of the databases, their database IDs, and the dates when the databases were created.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b23d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b23d-126">See Also</span></span>  
 <span data-ttu-id="1b23d-127">[資料庫和檔案目錄檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="1b23d-127">[Databases and Files Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql) </span></span>  
 [<span data-ttu-id="1b23d-128">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1b23d-128">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
