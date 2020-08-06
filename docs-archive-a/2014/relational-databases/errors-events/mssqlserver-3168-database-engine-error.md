---
title: MSSQLSERVER_3168 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3168 (Database Engine error)
ms.assetid: 991111d9-1eb3-43e9-9333-a75a775c3200
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 764f456653365c085e9f756a749910bbd03b4259
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596025"
---
# <a name="mssqlserver_3168"></a><span data-ttu-id="48908-102">MSSQLSERVER_3168</span><span class="sxs-lookup"><span data-stu-id="48908-102">MSSQLSERVER_3168</span></span>
    
## <a name="details"></a><span data-ttu-id="48908-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="48908-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48908-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="48908-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="48908-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="48908-105">Event ID</span></span>|<span data-ttu-id="48908-106">3168</span><span class="sxs-lookup"><span data-stu-id="48908-106">3168</span></span>|  
|<span data-ttu-id="48908-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="48908-107">Event Source</span></span>|<span data-ttu-id="48908-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="48908-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="48908-109">元件</span><span class="sxs-lookup"><span data-stu-id="48908-109">Component</span></span>|<span data-ttu-id="48908-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="48908-110">SQLEngine</span></span>|  
|<span data-ttu-id="48908-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="48908-111">Symbolic Name</span></span>|<span data-ttu-id="48908-112">LDDB_SYSTEMWRONGVER</span><span class="sxs-lookup"><span data-stu-id="48908-112">LDDB_SYSTEMWRONGVER</span></span>|  
|<span data-ttu-id="48908-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="48908-113">Message Text</span></span>|<span data-ttu-id="48908-114">裝置 %ls 上的系統資料庫備份無法還原，因為它是由不同於這個伺服器版本 (%ls) 的版本 (%ls) 所建立。</span><span class="sxs-lookup"><span data-stu-id="48908-114">The backup of the system database on the device %ls cannot be restored because it was created by a different version of the server (%ls) than this server (%ls).</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="48908-115">說明</span><span class="sxs-lookup"><span data-stu-id="48908-115">Explanation</span></span>  
 <span data-ttu-id="48908-116">在不同於原先執行備份之組建的伺服器組建上，您無法還原系統資料庫 (**master**、**model** 或 **msdb**) 的備份。</span><span class="sxs-lookup"><span data-stu-id="48908-116">You cannot restore a backup of a system database (**master**, **model**, or **msdb**) on a server build that differs from the build on which the backup was originally performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48908-117">安裝 Service Pack 或 Hotfix 組建會變更伺服器的組建編號，而且伺服器的組建一定是累加的。</span><span class="sxs-lookup"><span data-stu-id="48908-117">Installing a service pack or a hotfix build changes the server build number, and server builds are always incremental.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="48908-118">可能的原因</span><span class="sxs-lookup"><span data-stu-id="48908-118">Possible Causes</span></span>  
 <span data-ttu-id="48908-119">在不同的伺服器組建之間，系統資料庫的資料庫結構描述可能已有所變更。</span><span class="sxs-lookup"><span data-stu-id="48908-119">The database schema for system databases may be changed across server builds.</span></span> <span data-ttu-id="48908-120">為了確保這項結構描述變更不會造成任何不一致性，RESTORE 陳述式會將備份檔案的伺服器組建編號，與您嘗試還原備份所在之伺服器的組建編號進行比較。</span><span class="sxs-lookup"><span data-stu-id="48908-120">To make sure that a schema change does not cause inconsistencies, the RESTORE statement compares the server build number on the backup file to the build number of the server on which you are trying to restore the backup.</span></span> <span data-ttu-id="48908-121">如果這兩個組建不同，陳述式將發出 3168 錯誤訊息，並且還原作業會異常終止。</span><span class="sxs-lookup"><span data-stu-id="48908-121">If the builds are different, the statement issues the 3168 error message, and the restore operation terminates abnormally.</span></span>  
  
 <span data-ttu-id="48908-122">下列是可能會發生這個問題的案例：</span><span class="sxs-lookup"><span data-stu-id="48908-122">Some scenarios in which this problem may occur include the following:</span></span>  
  
-   <span data-ttu-id="48908-123">使用者嘗試在伺服器 A 上還原取自伺服器 B 的系統資料庫備份。伺服器 A 和伺服器 B 是不同的伺服器組建。</span><span class="sxs-lookup"><span data-stu-id="48908-123">A user tries to restore a system database on Server A from a backup taken on Server B. Servers A and B are on different server builds.</span></span> <span data-ttu-id="48908-124">例如，伺服器 A 可能是原始發行版本組建，而伺服器 B 是 Service Pack 1 (SP1) 組建。</span><span class="sxs-lookup"><span data-stu-id="48908-124">For example, Server A might be on the original release version build and Server B might be on a service pack 1 (SP1) build.</span></span>  
  
-   <span data-ttu-id="48908-125">使用者嘗試還原取自相同伺服器的系統資料庫備份，</span><span class="sxs-lookup"><span data-stu-id="48908-125">A user tries to restore a system database from a backup taken on the same server.</span></span> <span data-ttu-id="48908-126">但在進行備份時，伺服器執行的是不同的組建。</span><span class="sxs-lookup"><span data-stu-id="48908-126">However, the server was running a different build when the backup occurred.</span></span> <span data-ttu-id="48908-127">也就是說，自從執行備份之後，伺服器已升級。</span><span class="sxs-lookup"><span data-stu-id="48908-127">That is, the server was upgraded since the backup was performed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="48908-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="48908-128">User Action</span></span>  
 <span data-ttu-id="48908-129">這種情況下的還原程序相當複雜，如非必要，請勿使用。</span><span class="sxs-lookup"><span data-stu-id="48908-129">The restore process in this situation is fairly involved, and used only as a last resort.</span></span> <span data-ttu-id="48908-130">如需詳細資訊，請參閱[您無法將系統資料庫備份還原至不同的 SQL Server 組建](https://support.microsoft.com/kb/264474)。</span><span class="sxs-lookup"><span data-stu-id="48908-130">For more information, see"[You cannot restore system database backups to a different build of SQL Server](https://support.microsoft.com/kb/264474)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48908-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48908-131">See Also</span></span>  
 [<span data-ttu-id="48908-132">系統資料庫的備份與還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="48908-132">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
  
