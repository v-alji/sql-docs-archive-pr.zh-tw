---
title: SQL Server 的 Backup Device 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e3126310ad31dcc153fc79508dbfaccf86f5da78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594504"
---
# <a name="sql-server-backup-device-object"></a><span data-ttu-id="4ff7e-102">SQL Server 的 Backup Device 物件</span><span class="sxs-lookup"><span data-stu-id="4ff7e-102">SQL Server, Backup Device Object</span></span>
  <span data-ttu-id="4ff7e-103">**Backup Device** 物件提供計數器來監視備份與還原作業所使用的 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份裝置。</span><span class="sxs-lookup"><span data-stu-id="4ff7e-103">The **Backup Device** object provides counters to monitor Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices used for backup and restore operations.</span></span> <span data-ttu-id="4ff7e-104">藉由監視備份裝置，即可決定產能，或每個裝置的備份與還原作業的進度與效能。</span><span class="sxs-lookup"><span data-stu-id="4ff7e-104">Monitor backup devices when you want to determine the throughput or the progress and performance of your backup and restore operations on a per device basis.</span></span> <span data-ttu-id="4ff7e-105">若要監視整個資料庫備份或還原作業的輸送量，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** 物件的 **Backup/Restore Throughput/sec** 計數器。</span><span class="sxs-lookup"><span data-stu-id="4ff7e-105">To monitor the throughput of the entire database backup or restore operation, use the **Backup/Restore Throughput/sec** counter of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object.</span></span> <span data-ttu-id="4ff7e-106">如需詳細資訊，請參閱 [SQL Server, Databases Object](sql-server-databases-object.md)。</span><span class="sxs-lookup"><span data-stu-id="4ff7e-106">For more information, see [SQL Server, Databases Object](sql-server-databases-object.md).</span></span>  
  
 <span data-ttu-id="4ff7e-107">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** 計數器。</span><span class="sxs-lookup"><span data-stu-id="4ff7e-107">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** counter.</span></span>  
  
|<span data-ttu-id="4ff7e-108">SQL Server Backup Device 計數器</span><span class="sxs-lookup"><span data-stu-id="4ff7e-108">SQL Server Backup Device counters</span></span>|<span data-ttu-id="4ff7e-109">描述</span><span class="sxs-lookup"><span data-stu-id="4ff7e-109">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="4ff7e-110">**Device Throughput Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="4ff7e-110">**Device Throughput Bytes/sec**</span></span>|<span data-ttu-id="4ff7e-111">備份或還原資料庫時，所使用備份裝置的讀取與寫入作業輸送量 (位元組/秒)。</span><span class="sxs-lookup"><span data-stu-id="4ff7e-111">Throughput of read and write operations (in bytes per second) for a backup device used when backing up or restoring databases.</span></span> <span data-ttu-id="4ff7e-112">只有在備份或還原作業執行時，才會出現此計數器。</span><span class="sxs-lookup"><span data-stu-id="4ff7e-112">This counter exists only while the backup or restore operation is executing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ff7e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ff7e-113">See Also</span></span>  
 <span data-ttu-id="4ff7e-114">[備份裝置 &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4ff7e-114">[Backup Devices &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="4ff7e-115">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="4ff7e-115">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
