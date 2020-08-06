---
title: 監視 CPU 使用量 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], CPU usage
- tuning databases [SQL Server], CPU usage
- processors [SQL Server], monitoring usage
- database performance [SQL Server], CPU usage
- monitoring CPU usage [SQL Server]
- server performance [SQL Server], CPU usage
- database monitoring [SQL Server], CPU usage
- monitoring [SQL Server], CPU usage
- processors [SQL Server]
- CPU [SQL Server], monitoring
- monitoring server performance [SQL Server], CPU usage
ms.assetid: 2a02a3b6-07b2-4ad0-8a24-670414d19812
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f08d49348fd25593f27a87f2b0123f7ce43e35b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707409"
---
# <a name="monitor-cpu-usage"></a><span data-ttu-id="d0cb7-102">監視 CPU 使用量</span><span class="sxs-lookup"><span data-stu-id="d0cb7-102">Monitor CPU Usage</span></span>
  <span data-ttu-id="d0cb7-103">請定期監視 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，以判定 CPU 使用率是否在正常範圍內。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-103">Monitor an instance of Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] periodically to determine whether CPU usage rates are within normal ranges.</span></span> <span data-ttu-id="d0cb7-104">持續偏高的 CPU 使用量比率可能代表必須將 CPU 升級，或增加多個處理器。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-104">A continually high rate of CPU usage may indicate the need to upgrade the CPU or add multiple processors.</span></span> <span data-ttu-id="d0cb7-105">此外，偏高的 CPU 使用率可能代表應用程式的微調或設計不良。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-105">Alternatively, a high CPU usage rate may indicate a poorly tuned or designed application.</span></span> <span data-ttu-id="d0cb7-106">將應用程式最佳化後可降低 CPU 的使用率。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-106">Optimizing the application can lower CPU utilization.</span></span>  
  
 <span data-ttu-id="d0cb7-107">使用「系統監視器」中的 **Processor:% Processor Time** 計數器是判定 CPU 使用量的一種有效方法。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-107">An efficient way to determine CPU usage is to use the **Processor:% Processor Time** counter in System Monitor.</span></span> <span data-ttu-id="d0cb7-108">此計數器可監視 CPU 花費在執行非閒置執行緒上的時間量。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-108">This counter monitors the amount of time the CPU spends executing a thread that is not idle.</span></span> <span data-ttu-id="d0cb7-109">狀態維持在 80% 到 90%，可能代表必須將 CPU 升級或增加更多處理器。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-109">A consistent state of 80 percent to 90 percent may indicate the need to upgrade your CPU or add more processors.</span></span> <span data-ttu-id="d0cb7-110">使用多處理器系統時，可針對每個處理器監視此計數器的不同執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-110">For multiprocessor systems, monitor a separate instance of this counter for each processor.</span></span> <span data-ttu-id="d0cb7-111">此值代表特定處理器上的處理器時間總和。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-111">This value represents the sum of processor time on a specific processor.</span></span> <span data-ttu-id="d0cb7-112">若要判定所有處理器的平均值，請改為使用 **System: %Total Processor Time** 計數器。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-112">To determine the average for all processors, use the **System: %Total Processor Time** counter instead.</span></span>  
  
 <span data-ttu-id="d0cb7-113">(選擇性) 您也可以監視下列計數器，來監視處理器使用量：</span><span class="sxs-lookup"><span data-stu-id="d0cb7-113">Optionally, you can also monitor the following counters to monitor processor usage:</span></span>  
  
-   <span data-ttu-id="d0cb7-114">**Processor: % Privileged Time**</span><span class="sxs-lookup"><span data-stu-id="d0cb7-114">**Processor: % Privileged Time**</span></span>  
  
     <span data-ttu-id="d0cb7-115">相當於處理器花費在執行 Microsoft Windows 核心命令 (如處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O 要求) 的時間百分比。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-115">Corresponds to the percentage of time the processor spends on execution of Microsoft Windows kernel commands, such as processing of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O requests.</span></span> <span data-ttu-id="d0cb7-116">當 **Physical Disk** 計數器很高時，如果這個計數器也持續偏高，請考慮換用較快或較有效率的磁碟子系統 (Disk Subsystem)。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-116">If this counter is consistently high when the **Physical Disk** counters are high, consider installing a faster or more efficient disk subsystem.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d0cb7-117">不同的磁碟控制器和驅動程式會使用不同的核心處理 (kernel Process) 時間量。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-117">Different disk controllers and drivers use different amounts of kernel processing time.</span></span> <span data-ttu-id="d0cb7-118">有效率的控制器和驅動程式將使用較少的授權時間，留下較多的處理時間供使用者應用程式使用，同時增加整體的處理能力。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-118">Efficient controllers and drivers use less privileged time, leaving more processing time available for user applications, increasing overall throughput.</span></span>  
  
-   <span data-ttu-id="d0cb7-119">**Processor: %User Time**</span><span class="sxs-lookup"><span data-stu-id="d0cb7-119">**Processor: %User Time**</span></span>  
  
     <span data-ttu-id="d0cb7-120">相當於處理器花費在執行使用者處理序 (如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 的時間百分比。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-120">Corresponds to the percentage of time that the processor spends on executing user processes such as [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d0cb7-121">**系統：Processor Queue Length**</span><span class="sxs-lookup"><span data-stu-id="d0cb7-121">**System: Processor Queue Length**</span></span>  
  
     <span data-ttu-id="d0cb7-122">相當於等候處理器時間的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-122">Corresponds to the number of threads waiting for processor time.</span></span> <span data-ttu-id="d0cb7-123">當處理序的執行緒所需的處理器循環超過可用數量時，就會形成處理器瓶頸。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-123">A processor bottleneck develops when threads of a process require more processor cycles than are available.</span></span> <span data-ttu-id="d0cb7-124">如果會有許多處理序嘗試利用處理器時間，您可能必須安裝更快的處理器。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-124">If more than a few processes attempt to utilize the processor's time, you might need to install a faster processor.</span></span> <span data-ttu-id="d0cb7-125">或者，如果使用多處理器系統，則可以增加一個處理器。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-125">Or, if you have a multiprocessor system, you could add a processor.</span></span>  
  
 <span data-ttu-id="d0cb7-126">在檢查處理器使用量時，請考慮 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體所執行的工作類型。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-126">When you examine processor usage, consider the type of work that the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs.</span></span> <span data-ttu-id="d0cb7-127">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在執行許多計算，例如牽涉到彙總的查詢，或不需要磁碟 I/O 的記憶體繫結查詢 (Memory-bound Query) 時，就可以使用 100 % 的處理器時間。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs many calculations, such as queries involving aggregates or memory-bound queries that require no disk I/O, 100 percent of the processor's time can be used.</span></span> <span data-ttu-id="d0cb7-128">如果這導致其他應用程式的效能降低，請變更工作負載。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-128">If this causes the performance of other applications to suffer, try changing the workload.</span></span> <span data-ttu-id="d0cb7-129">例如，讓此電腦專門用來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-129">For example, dedicate the computer to running the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d0cb7-130">正在處理許多用戶端要求而使用率約達 100% 時，可能代表佇列中已有處理序在等候處理器時間，而造成瓶頸。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-130">Usage rates around 100 percent, where many client requests are being processed, may indicate that processes are queuing up, waiting for processor time, and causing a bottleneck.</span></span> <span data-ttu-id="d0cb7-131">增加更快的處理器可解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="d0cb7-131">Resolve the problem by adding faster processors.</span></span>  
  
  
