---
title: 資料庫狀態 | Microsoft 文件
ms.custom: ''
ms.date: 07/15/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASESTATES.F1
helpviewer_keywords:
- emergency database state [SQL Server]
- verifying database states
- viewing database states
- displaying database states
- database states [SQL Server]
- current database state
- offline database state [SQL Server]
- suspect database state
- recovery pending database state [SQL Server]
- states [SQL Server], databases
- online database state
- states [SQL Server]
- restoring database state [SQL Server]
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0aec4e5fb367f5fe9bf8fca5ed056269930cf2db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709566"
---
# <a name="database-states"></a><span data-ttu-id="f27f4-102">資料庫狀態</span><span class="sxs-lookup"><span data-stu-id="f27f4-102">Database States</span></span>
  <span data-ttu-id="f27f4-103">資料庫永遠都在特定的狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-103">A database is always in one specific state.</span></span> <span data-ttu-id="f27f4-104">例如，這些狀態包括 ONLINE、OFFLINE 或 SUSPECT。</span><span class="sxs-lookup"><span data-stu-id="f27f4-104">For example, these states include ONLINE, OFFLINE, or SUSPECT.</span></span> <span data-ttu-id="f27f4-105">若要驗證資料庫目前的狀態，請選取 **sys.databases** 目錄檢視中的 [state_desc](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 資料行或是在 **DATABASEPROPERTYEX** 函數中的 [Status](/sql/t-sql/functions/databasepropertyex-transact-sql) 屬性。</span><span class="sxs-lookup"><span data-stu-id="f27f4-105">To verify the current state of a database, select the **state_desc** column in the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view or the **Status** property in the [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) function.</span></span>  
  
## <a name="database-state-definitions"></a><span data-ttu-id="f27f4-106">資料庫狀態定義</span><span class="sxs-lookup"><span data-stu-id="f27f4-106">Database State Definitions</span></span>  
 <span data-ttu-id="f27f4-107">下表定義資料表狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-107">The following table defines the database states.</span></span>  
  
|<span data-ttu-id="f27f4-108">State</span><span class="sxs-lookup"><span data-stu-id="f27f4-108">State</span></span>|<span data-ttu-id="f27f4-109">定義</span><span class="sxs-lookup"><span data-stu-id="f27f4-109">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="f27f4-110">ONLINE</span><span class="sxs-lookup"><span data-stu-id="f27f4-110">ONLINE</span></span>|<span data-ttu-id="f27f4-111">資料庫可供存取。</span><span class="sxs-lookup"><span data-stu-id="f27f4-111">Database is available for access.</span></span> <span data-ttu-id="f27f4-112">主要檔案群組是在線上，雖然可能尚未完成恢復的恢復階段。</span><span class="sxs-lookup"><span data-stu-id="f27f4-112">The primary filegroup is online, although the undo phase of recovery may not have been completed.</span></span>|  
|<span data-ttu-id="f27f4-113">OFFLINE</span><span class="sxs-lookup"><span data-stu-id="f27f4-113">OFFLINE</span></span>|<span data-ttu-id="f27f4-114">資料庫是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="f27f4-114">Database is unavailable.</span></span> <span data-ttu-id="f27f4-115">明確的使用者動作可使資料庫變成離線狀態，並且在採取其他的使用者動作之前都是離線狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-115">A database becomes offline by explicit user action and remains offline until additional user action is taken.</span></span> <span data-ttu-id="f27f4-116">例如，可以將資料庫設成離線，好讓檔案移到新的磁碟中。</span><span class="sxs-lookup"><span data-stu-id="f27f4-116">For example, the database may be taken offline in order to move a file to a new disk.</span></span> <span data-ttu-id="f27f4-117">在完成移動後，就會將資料庫重新啟動為線上狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-117">The database is then brought back online after the move has been completed.</span></span>|  
|<span data-ttu-id="f27f4-118">RESTORING</span><span class="sxs-lookup"><span data-stu-id="f27f4-118">RESTORING</span></span>|<span data-ttu-id="f27f4-119">在離線狀態還原主要檔案群組的一或多個檔案，或還原一或多個次要檔案。</span><span class="sxs-lookup"><span data-stu-id="f27f4-119">One or more files of the primary filegroup are being restored, or one or more secondary files are being restored offline.</span></span> <span data-ttu-id="f27f4-120">資料庫是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="f27f4-120">The database is unavailable.</span></span>|  
|<span data-ttu-id="f27f4-121">RECOVERING</span><span class="sxs-lookup"><span data-stu-id="f27f4-121">RECOVERING</span></span>|<span data-ttu-id="f27f4-122">資料庫恢復中。</span><span class="sxs-lookup"><span data-stu-id="f27f4-122">Database is being recovered.</span></span> <span data-ttu-id="f27f4-123">恢復程序是暫時性的狀態；如果恢復成功，資料庫就會自動變成線上狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-123">The recovering process is a transient state; the database will automatically become online if the recovery succeeds.</span></span> <span data-ttu-id="f27f4-124">如果恢復失敗，資料庫就會變成有疑問的狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-124">If the recovery fails, the database will become suspect.</span></span> <span data-ttu-id="f27f4-125">資料庫是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="f27f4-125">The database is unavailable.</span></span>|  
|<span data-ttu-id="f27f4-126">RECOVERY PENDING</span><span class="sxs-lookup"><span data-stu-id="f27f4-126">RECOVERY PENDING</span></span>|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f27f4-127">在恢復期間發生資源相關的錯誤。</span><span class="sxs-lookup"><span data-stu-id="f27f4-127">has encountered a resource-related error during recovery.</span></span> <span data-ttu-id="f27f4-128">資料庫並未損毀，但是檔案有可能遺失或系統資源限制有可能造成它無法啟動。</span><span class="sxs-lookup"><span data-stu-id="f27f4-128">The database is not damaged, but files may be missing or system resource limitations may be preventing it from starting.</span></span> <span data-ttu-id="f27f4-129">資料庫是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="f27f4-129">The database is unavailable.</span></span> <span data-ttu-id="f27f4-130">需要使用者執行其他動作以解決錯誤並讓恢復處理得以完成。</span><span class="sxs-lookup"><span data-stu-id="f27f4-130">Additional action by the user is required to resolve the error and let the recovery process be completed.</span></span>|  
|<span data-ttu-id="f27f4-131">SUSPECT</span><span class="sxs-lookup"><span data-stu-id="f27f4-131">SUSPECT</span></span>|<span data-ttu-id="f27f4-132">至少主要檔案群組為有疑問的，而且有可能會損毀。</span><span class="sxs-lookup"><span data-stu-id="f27f4-132">At least the primary filegroup is suspect and may be damaged.</span></span> <span data-ttu-id="f27f4-133">資料庫在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]啟動期間無法恢復資料庫。</span><span class="sxs-lookup"><span data-stu-id="f27f4-133">The database cannot be recovered during startup of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f27f4-134">資料庫是無法使用的。</span><span class="sxs-lookup"><span data-stu-id="f27f4-134">The database is unavailable.</span></span> <span data-ttu-id="f27f4-135">需要使用者執行其他動作來解決問題。</span><span class="sxs-lookup"><span data-stu-id="f27f4-135">Additional action by the user is required to resolve the problem.</span></span>|  
|<span data-ttu-id="f27f4-136">EMERGENCY</span><span class="sxs-lookup"><span data-stu-id="f27f4-136">EMERGENCY</span></span>|<span data-ttu-id="f27f4-137">使用者已變更資料庫並將狀態設為 EMERGENCY。</span><span class="sxs-lookup"><span data-stu-id="f27f4-137">User has changed the database and set the status to EMERGENCY.</span></span> <span data-ttu-id="f27f4-138">資料庫是在單一使用者模式下，而且可以進行修復或還原。</span><span class="sxs-lookup"><span data-stu-id="f27f4-138">The database is in single-user mode and may be repaired or restored.</span></span> <span data-ttu-id="f27f4-139">資料庫是標示為 READ_ONLY、記錄已停用並限定只有 **系統管理員** 固定伺服器角色的成員才可存取。</span><span class="sxs-lookup"><span data-stu-id="f27f4-139">The database is marked READ_ONLY, logging is disabled, and access is limited to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="f27f4-140">EMERGENCY 主要是做為疑難排解的用途。</span><span class="sxs-lookup"><span data-stu-id="f27f4-140">EMERGENCY is primarily used for troubleshooting purposes.</span></span> <span data-ttu-id="f27f4-141">例如，標示為有疑問的資料庫可以設為 EMERGENCY 狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-141">For example, a database marked as suspect can be set to the EMERGENCY state.</span></span> <span data-ttu-id="f27f4-142">這將可允許系統管理員唯讀存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="f27f4-142">This could permit the system administrator read-only access to the database.</span></span> <span data-ttu-id="f27f4-143">只有 **系統管理員** 固定伺服器角色的成員，可以將資料庫設定為 EMERGENCY 狀態。</span><span class="sxs-lookup"><span data-stu-id="f27f4-143">Only members of the **sysadmin** fixed server role can set a database to the EMERGENCY state.</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="f27f4-144">相關內容</span><span class="sxs-lookup"><span data-stu-id="f27f4-144">Related Content</span></span>  
 [<span data-ttu-id="f27f4-145">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f27f4-145">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="f27f4-146">鏡像狀態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f27f4-146">Mirroring States &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [<span data-ttu-id="f27f4-147">檔案狀態</span><span class="sxs-lookup"><span data-stu-id="f27f4-147">File States</span></span>](file-states.md)  
  
  
