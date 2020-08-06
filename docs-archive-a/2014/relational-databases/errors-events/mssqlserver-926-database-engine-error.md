---
title: MSSQLSERVER_926 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 926 (Database Engine error)
ms.assetid: 57e01668-883b-4be4-84a8-a111caaf0486
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ae6796c9f4869d45223ab1283a68fc2bfe78aa11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595042"
---
# <a name="mssqlserver_926"></a><span data-ttu-id="2c2dd-102">MSSQLSERVER_926</span><span class="sxs-lookup"><span data-stu-id="2c2dd-102">MSSQLSERVER_926</span></span>
    
## <a name="details"></a><span data-ttu-id="2c2dd-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2c2dd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c2dd-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2c2dd-104">Product Name</span></span>|<span data-ttu-id="2c2dd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2c2dd-105">SQL Server</span></span>|  
|<span data-ttu-id="2c2dd-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2c2dd-106">Event ID</span></span>|<span data-ttu-id="2c2dd-107">926</span><span class="sxs-lookup"><span data-stu-id="2c2dd-107">926</span></span>|  
|<span data-ttu-id="2c2dd-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2c2dd-108">Event Source</span></span>|<span data-ttu-id="2c2dd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2c2dd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2c2dd-110">元件</span><span class="sxs-lookup"><span data-stu-id="2c2dd-110">Component</span></span>|<span data-ttu-id="2c2dd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2c2dd-111">SQLEngine</span></span>|  
|<span data-ttu-id="2c2dd-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2c2dd-112">Symbolic Name</span></span>|<span data-ttu-id="2c2dd-113">DB_SUSPECT</span><span class="sxs-lookup"><span data-stu-id="2c2dd-113">DB_SUSPECT</span></span>|  
|<span data-ttu-id="2c2dd-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2c2dd-114">Message Text</span></span>|<span data-ttu-id="2c2dd-115">資料庫 '%.\*ls' 無法開啟。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-115">Database '%.\*ls' cannot be opened.</span></span> <span data-ttu-id="2c2dd-116">它已經由復原標示成 SUSPECT。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-116">It has been marked SUSPECT by recovery.</span></span> <span data-ttu-id="2c2dd-117">如需詳細資訊，請參閱 SQL Server 錯誤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-117">See the SQL Server errorlog for more information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2c2dd-118">說明</span><span class="sxs-lookup"><span data-stu-id="2c2dd-118">Explanation</span></span>  
 <span data-ttu-id="2c2dd-119">資料庫標示為有疑問，因為復原程序未能將資料庫回復為一致交易狀態。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-119">The database is marked as suspect because it failed the recovery process that brings a database to a consistent transactional state.</span></span> <span data-ttu-id="2c2dd-120">這可能發生在下列作業：</span><span class="sxs-lookup"><span data-stu-id="2c2dd-120">This can occur during the following operations:</span></span>  
  
-   <span data-ttu-id="2c2dd-121">啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-121">Starting up an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2c2dd-122">附加資料庫。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-122">Attaching a database.</span></span>  
  
-   <span data-ttu-id="2c2dd-123">使用 RESTORE 資料庫或 RESTORE LOG 程序。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-123">Using the RESTORE database or RESTORE LOG procedures.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2c2dd-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2c2dd-124">User Action</span></span>  
 <span data-ttu-id="2c2dd-125">查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，了解錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-125">Inspect the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and determine the cause of the error.</span></span> <span data-ttu-id="2c2dd-126">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 因復原失敗而重新啟動，請查看先前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，了解復原失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-126">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been restarted since the failed recovery, look at previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error logs to see the reason why recovery failed.</span></span>  
  
 <span data-ttu-id="2c2dd-127">如果復原程序是因為持續發生 I/O 錯誤、損毀頁或其他可能的硬體問題，請先解決根本的硬體問題，再使用備份還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-127">If the recovery failed because of a persistent I/O error, a torn page, or other possible hardware problem, resolve the underlying hardware problem and restore the database by using a backup.</span></span> <span data-ttu-id="2c2dd-128">如果沒有備份可供使用，請考慮使用 DBCC CHECKDB 的修復選項。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-128">If no backups are available, consider the repair options of DBCC CHECKDB.</span></span>  
  
 <span data-ttu-id="2c2dd-129">如果無法解決這個問題，請連絡您的主要支援提供者。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-129">If you are unable to resolve this problem, contact your primary support provider.</span></span> <span data-ttu-id="2c2dd-130">請準備好 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔以供檢閱。</span><span class="sxs-lookup"><span data-stu-id="2c2dd-130">Have the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log available for review.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2dd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c2dd-131">See Also</span></span>  
 <span data-ttu-id="2c2dd-132">[SQL Server 資料庫的備份與還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="2c2dd-132">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="2c2dd-133">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2c2dd-133">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="2c2dd-134">[sys.sys資料庫 &#40;Transact-sql&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2c2dd-134">[sys.sysdatabases &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql) </span></span>  
 [<span data-ttu-id="2c2dd-135">資料庫卸離與附加 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2c2dd-135">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  
