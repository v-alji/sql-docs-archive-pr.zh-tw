---
title: 監視磁碟使用量 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51479b024864322d34dc3b0208e29e93d7454184
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707405"
---
# <a name="monitor-disk-usage"></a><span data-ttu-id="4aabf-102">監視磁碟使用量</span><span class="sxs-lookup"><span data-stu-id="4aabf-102">Monitor Disk Usage</span></span>
  <span data-ttu-id="4aabf-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用 Microsoft Windows 作業系統輸入/輸出 (I/O) 呼叫，在您的磁碟上執行讀取和寫入作業。</span><span class="sxs-lookup"><span data-stu-id="4aabf-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses Microsoft Windows operating system input/output (I/O) calls to perform read and write operations on your disk.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="4aabf-104">會管理何時及如何執行磁碟 I/O，但是 Windows 作業系統會執行基礎 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="4aabf-104">manages when and how disk I/O is performed, but the Windows operating system performs the underlying I/O operations.</span></span> <span data-ttu-id="4aabf-105">I/O 子系統包含了系統匯流排、磁碟控制卡、磁碟、磁帶機、光碟機和許多其他的 I/O 裝置。</span><span class="sxs-lookup"><span data-stu-id="4aabf-105">The I/O subsystem includes the system bus, disk controller cards, disks, tape drives, CD-ROM drive, and many other I/O devices.</span></span> <span data-ttu-id="4aabf-106">磁碟 I/O 經常是造成系統瓶頸的原因。</span><span class="sxs-lookup"><span data-stu-id="4aabf-106">Disk I/O is frequently the cause of bottlenecks in a system.</span></span>  
  
 <span data-ttu-id="4aabf-107">監視磁碟活動涉及兩個重點：</span><span class="sxs-lookup"><span data-stu-id="4aabf-107">Monitoring disk activity involves two areas of focus:</span></span>  
  
-   <span data-ttu-id="4aabf-108">監視磁碟 I/O 與偵測額外的分頁方式</span><span class="sxs-lookup"><span data-stu-id="4aabf-108">Monitoring Disk I/O and Detecting Excess Paging</span></span>  
  
-   <span data-ttu-id="4aabf-109">隔離 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 建立的磁碟活動</span><span class="sxs-lookup"><span data-stu-id="4aabf-109">Isolating Disk Activity That [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Creates</span></span>  
  
 <span data-ttu-id="4aabf-110">如需詳細資訊，請參閱[監視磁片使用量](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)</span><span class="sxs-lookup"><span data-stu-id="4aabf-110">For more information see, [Monitoring Disk Usage](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)</span></span>  
  
  
