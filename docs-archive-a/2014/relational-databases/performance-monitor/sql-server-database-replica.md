---
title: SQL Server、資料庫複本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SQLServer:Database Replica
- performance counters [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], performance counters
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c8830ae30ad3514e107b718f9a02fef873e20295
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598295"
---
# <a name="sql-server-database-replica"></a><span data-ttu-id="bf79d-102">SQL Server、資料庫複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-102">SQL Server, Database Replica</span></span>
  <span data-ttu-id="bf79d-103">**SQLServer:Database Replica** 效能物件包含的效能計數器會報告 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中 AlwaysOn 可用性群組之次要資料庫的報表資訊。</span><span class="sxs-lookup"><span data-stu-id="bf79d-103">The **SQLServer:Database Replica** performance object contains performance counters that report information about the secondary databases of an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="bf79d-104">這個物件只有在裝載次要複本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上才有效。</span><span class="sxs-lookup"><span data-stu-id="bf79d-104">This object is valid only on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts a secondary replica.</span></span>  
  
|<span data-ttu-id="bf79d-105">計數器名稱</span><span class="sxs-lookup"><span data-stu-id="bf79d-105">Counter Name</span></span>|<span data-ttu-id="bf79d-106">描述</span><span class="sxs-lookup"><span data-stu-id="bf79d-106">Description</span></span>|<span data-ttu-id="bf79d-107">檢視位置...</span><span class="sxs-lookup"><span data-stu-id="bf79d-107">View on...</span></span>|  
|------------------|-----------------|--------------|  
|<span data-ttu-id="bf79d-108">**File Bytes Received/sec**</span><span class="sxs-lookup"><span data-stu-id="bf79d-108">**File Bytes Received/sec**</span></span>|<span data-ttu-id="bf79d-109">次要資料庫的次要複本在上一秒所收到的 FILESTREAM 資料量。</span><span class="sxs-lookup"><span data-stu-id="bf79d-109">Amount of FILESTREAM data received by the secondary replica for the secondary database in the last second.</span></span>|<span data-ttu-id="bf79d-110">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-110">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-111">**Log Bytes Received/sec**</span><span class="sxs-lookup"><span data-stu-id="bf79d-111">**Log Bytes Received/sec**</span></span>|<span data-ttu-id="bf79d-112">資料庫的次要複本在上一秒所收到的記錄檔記錄數量。</span><span class="sxs-lookup"><span data-stu-id="bf79d-112">Amount of log records received by the secondary replica for the database in the last second.</span></span>|<span data-ttu-id="bf79d-113">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-113">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-114">**Log remaining for undo**</span><span class="sxs-lookup"><span data-stu-id="bf79d-114">**Log remaining for undo**</span></span>|<span data-ttu-id="bf79d-115">完成復原階段所剩餘的記錄檔數量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="bf79d-115">The amount of log in kilobytes remaining to complete the undo phase.</span></span>|<span data-ttu-id="bf79d-116">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-116">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-117">**Log Send Queue**</span><span class="sxs-lookup"><span data-stu-id="bf79d-117">**Log Send Queue**</span></span>|<span data-ttu-id="bf79d-118">主要資料庫記錄檔中尚未傳送至次要複本的記錄檔記錄數量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="bf79d-118">Amount of log records in the log files of the primary database, in kilobytes, that has not yet been sent to the secondary replica.</span></span> <span data-ttu-id="bf79d-119">這個值是從主要複本傳送至次要複本。</span><span class="sxs-lookup"><span data-stu-id="bf79d-119">This value is sent to the secondary replica from the primary replica.</span></span> <span data-ttu-id="bf79d-120">佇列大小不包括傳送到次要複本的 FILESTREAM 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf79d-120">Queue size does not include FILESTREAM files that are sent to a secondary.</span></span>|<span data-ttu-id="bf79d-121">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-121">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-122">**Mirrored Write Transaction/sec**</span><span class="sxs-lookup"><span data-stu-id="bf79d-122">**Mirrored Write Transaction/sec**</span></span>|<span data-ttu-id="bf79d-123">在上一秒中，已寫入主要資料庫，然後在傳送至次要資料庫之前等候認可的交易數目。</span><span class="sxs-lookup"><span data-stu-id="bf79d-123">Number of transactions that were written to the primary database and then waited to commit until the log was sent to the secondary database, in the last second.</span></span>|<span data-ttu-id="bf79d-124">主要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-124">Primary replica</span></span>|  
|<span data-ttu-id="bf79d-125">**Recovery Queue**</span><span class="sxs-lookup"><span data-stu-id="bf79d-125">**Recovery Queue**</span></span>|<span data-ttu-id="bf79d-126">次要複本記錄檔中尚未重做的記錄檔記錄數量。</span><span class="sxs-lookup"><span data-stu-id="bf79d-126">Amount of log records in the log files of the secondary replica that has not yet been redone.</span></span>|<span data-ttu-id="bf79d-127">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-127">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-128">**Redo blocked/sec**</span><span class="sxs-lookup"><span data-stu-id="bf79d-128">**Redo blocked/sec**</span></span>|<span data-ttu-id="bf79d-129">資料庫的讀取者鎖定重做執行緒的次數。</span><span class="sxs-lookup"><span data-stu-id="bf79d-129">Number of times the redo thread is blocked on locks held by readers of the database.</span></span>|<span data-ttu-id="bf79d-130">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-130">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-131">**Redo Bytes Remaining**</span><span class="sxs-lookup"><span data-stu-id="bf79d-131">**Redo Bytes Remaining**</span></span>|<span data-ttu-id="bf79d-132">完成還原階段所要重做的剩餘記錄檔數量 (以 KB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="bf79d-132">The amount of log in kilobytes remaining to be redone to finish the reverting phase.</span></span>|<span data-ttu-id="bf79d-133">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-133">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-134">**Redone Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="bf79d-134">**Redone Bytes/sec**</span></span>|<span data-ttu-id="bf79d-135">次要資料庫在上一秒重做的記錄檔記錄數量。</span><span class="sxs-lookup"><span data-stu-id="bf79d-135">Amount of log records redone on the secondary database in the last second.</span></span>|<span data-ttu-id="bf79d-136">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-136">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-137">**Total Log requiring undo**</span><span class="sxs-lookup"><span data-stu-id="bf79d-137">**Total Log requiring undo**</span></span>|<span data-ttu-id="bf79d-138">必須復原之記錄檔的總 KB 數。</span><span class="sxs-lookup"><span data-stu-id="bf79d-138">Total kilobytes of log that must be undone.</span></span>|<span data-ttu-id="bf79d-139">次要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-139">Secondary replica</span></span>|  
|<span data-ttu-id="bf79d-140">**Transaction Delay**</span><span class="sxs-lookup"><span data-stu-id="bf79d-140">**Transaction Delay**</span></span>|<span data-ttu-id="bf79d-141">等候未終止之認可收條的延遲時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="bf79d-141">Delay in waiting for unterminated commit acknowledgement, in milliseconds.</span></span>|<span data-ttu-id="bf79d-142">主要複本</span><span class="sxs-lookup"><span data-stu-id="bf79d-142">Primary replica</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf79d-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf79d-143">See Also</span></span>  
 <span data-ttu-id="bf79d-144">[監視資源使用量 &#40;系統監視器&#41;](monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="bf79d-144">[Monitor Resource Usage &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="bf79d-145">[SQL Server、可用性複本](sql-server-availability-replica.md) </span><span class="sxs-lookup"><span data-stu-id="bf79d-145">[SQL Server, Availability Replica](sql-server-availability-replica.md) </span></span>  
 <span data-ttu-id="bf79d-146">[SQL Server、Databases 物件](sql-server-databases-object.md) </span><span class="sxs-lookup"><span data-stu-id="bf79d-146">[SQL Server, Databases Object](sql-server-databases-object.md) </span></span>  
 [<span data-ttu-id="bf79d-147">AlwaysOn Availability Groups (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="bf79d-147">AlwaysOn Availability Groups (SQL Server)</span></span>](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
