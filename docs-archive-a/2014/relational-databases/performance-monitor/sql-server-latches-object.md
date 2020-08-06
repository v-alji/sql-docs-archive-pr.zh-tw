---
title: SQL Server 的 Latches 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6f49ac00114065e971c0893f9217ab883eb2d7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592634"
---
# <a name="sql-server-latches-object"></a><span data-ttu-id="0bee6-102">SQL Server 的 Latches 物件</span><span class="sxs-lookup"><span data-stu-id="0bee6-102">SQL Server, Latches Object</span></span>
  <span data-ttu-id="0bee6-103">Microsoft **的** SQLServer:Latches [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件提供計數器，可監視稱為閂鎖的內部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源鎖定。</span><span class="sxs-lookup"><span data-stu-id="0bee6-103">The **SQLServer:Latches** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor internal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource locks called latches.</span></span> <span data-ttu-id="0bee6-104">監視閂鎖來判斷使用者活動和資源使用狀況，可協助您找出效能的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="0bee6-104">Monitoring the latches to determine user activity and resource usage can help you to identify performance bottlenecks.</span></span>  
  
 <span data-ttu-id="0bee6-105">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** 計數器。</span><span class="sxs-lookup"><span data-stu-id="0bee6-105">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** counters.</span></span>  
  
|<span data-ttu-id="0bee6-106">SQL Server 的 Latches 計數器</span><span class="sxs-lookup"><span data-stu-id="0bee6-106">SQL Server Latches counters</span></span>|<span data-ttu-id="0bee6-107">描述</span><span class="sxs-lookup"><span data-stu-id="0bee6-107">Description</span></span>|  
|---------------------------------|-----------------|  
|<span data-ttu-id="0bee6-108">**Average Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="0bee6-108">**Average Latch Wait Time (ms)**</span></span>|<span data-ttu-id="0bee6-109">必須等候之閂鎖要求的平均閂鎖等候時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="0bee6-109">Average latch wait time (in milliseconds) for latch requests that had to wait.</span></span>|  
|<span data-ttu-id="0bee6-110">**Latch Waits/sec**</span><span class="sxs-lookup"><span data-stu-id="0bee6-110">**Latch Waits/sec**</span></span>|<span data-ttu-id="0bee6-111">無法立即授權的閂鎖要求次數。</span><span class="sxs-lookup"><span data-stu-id="0bee6-111">Number of latch requests that could not be granted immediately.</span></span>|  
|<span data-ttu-id="0bee6-112">**SuperLatch 數目**</span><span class="sxs-lookup"><span data-stu-id="0bee6-112">**Number of SuperLatches**</span></span>|<span data-ttu-id="0bee6-113">目前為 SuperLatch 的閂鎖數目。</span><span class="sxs-lookup"><span data-stu-id="0bee6-113">Number of latches that are currently SuperLatches.</span></span>|  
|<span data-ttu-id="0bee6-114">**SuperLatch Demotions/sec**</span><span class="sxs-lookup"><span data-stu-id="0bee6-114">**SuperLatch Demotions/sec**</span></span>|<span data-ttu-id="0bee6-115">在上一秒內已降級為一般閂鎖的 SuperLatch 數目。</span><span class="sxs-lookup"><span data-stu-id="0bee6-115">Number of SuperLatches that have been demoted to regular latches in the last second.</span></span>|  
|<span data-ttu-id="0bee6-116">**SuperLatch Promotions/sec**</span><span class="sxs-lookup"><span data-stu-id="0bee6-116">**SuperLatch Promotions/sec**</span></span>|<span data-ttu-id="0bee6-117">在上一秒內已升級為 SuperLatch 的閂鎖數目。</span><span class="sxs-lookup"><span data-stu-id="0bee6-117">Number of latches that have been promoted to SuperLatches in the last second.</span></span>|  
|<span data-ttu-id="0bee6-118">**Total Latch Wait Time (ms)**</span><span class="sxs-lookup"><span data-stu-id="0bee6-118">**Total Latch Wait Time (ms)**</span></span>|<span data-ttu-id="0bee6-119">最後一秒內的鎖定總等候時間 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="0bee6-119">Total latch wait time (in milliseconds) for latch requests in the last second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bee6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bee6-120">See Also</span></span>  
 [<span data-ttu-id="0bee6-121">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="0bee6-121">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
