---
title: 在 VM 環境中使用記憶體內部 OLTP |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 27ec7eb3-3a24-41db-aa65-2f206514c6f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83cf785fbcd2df9449d61e328e3bf8e374a6656d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700198"
---
# <a name="using-in-memory-oltp-in-a-vm-environment"></a><span data-ttu-id="c6a49-102">在 VM 環境使用記憶體中的 OLTP</span><span class="sxs-lookup"><span data-stu-id="c6a49-102">Using In-Memory OLTP in a VM Environment</span></span>
  <span data-ttu-id="c6a49-103">伺服器虛擬化技術可協助您降低 IT 資本和作業成本，並透過改善的應用程式佈建、維護、可用性和備份/復原程序，達到更高的 IT 效率。</span><span class="sxs-lookup"><span data-stu-id="c6a49-103">Server virtualization can help you lower IT capital and operational costs and attain greater IT efficiency with improved application provisioning, maintenance, availability, and backup/recovery processes.</span></span> <span data-ttu-id="c6a49-104">隨著最近的技術進步，可以更輕易地運用虛擬化技術，將複雜的資料庫工作負載合併。</span><span class="sxs-lookup"><span data-stu-id="c6a49-104">With recent technological advances, complex database workloads can be more readily consolidated using virtualization.</span></span> <span data-ttu-id="c6a49-105">本主題包括在虛擬化環境中使用 [!INCLUDE[hek_1](../includes/hek-1-md.md)] 的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="c6a49-105">This topic covers best practices for using [!INCLUDE[hek_1](../includes/hek-1-md.md)] in a virtualized environment.</span></span>  
  
##  <a name="memory-pre-allocation"></a><a name="bkmk_memoryPreAllocation"></a><span data-ttu-id="c6a49-106">記憶體預先配置</span><span class="sxs-lookup"><span data-stu-id="c6a49-106">Memory pre-allocation</span></span>  
 <span data-ttu-id="c6a49-107">對虛擬化環境中的記憶體而言，更好的效能與增強的支援是基本考量。</span><span class="sxs-lookup"><span data-stu-id="c6a49-107">For memory in a virtualized environment, better performance and enhanced support are essential considerations.</span></span> <span data-ttu-id="c6a49-108">您必須能夠依據虛擬機器的需求 (尖峰和非尖峰負載)，快速配置記憶體給虛擬機器，同時也要確保不會浪費記憶體。</span><span class="sxs-lookup"><span data-stu-id="c6a49-108">You must be able to both quickly allocate memory to virtual machines depending on their requirements (peak and off-peak loads) and ensure that the memory is not wasted.</span></span> <span data-ttu-id="c6a49-109">有關如何在主機上執行的虛擬機器之間配置和管理記憶體，Hyper-V 動態記憶體功能可以加強這方面的靈活度。</span><span class="sxs-lookup"><span data-stu-id="c6a49-109">The Hyper-V Dynamic Memory feature increases agility in how the memory is allocated and managed between virtual machines running on a host.</span></span>  
  
 <span data-ttu-id="c6a49-110">將具有記憶體最佳化資料表的資料庫虛擬化時，需要修改虛擬化和管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的一些最佳做法。</span><span class="sxs-lookup"><span data-stu-id="c6a49-110">Some best practices for virtualizing and managing [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] need to be modified when virtualizing a database with memory-optimized tables.</span></span> <span data-ttu-id="c6a49-111">如果沒有記憶體最佳化資料表，則其中兩個最佳作法如下：</span><span class="sxs-lookup"><span data-stu-id="c6a49-111">Without memory-optimized tables, two of the best practices are:</span></span>  
  
-   <span data-ttu-id="c6a49-112">如果您使用 MIN_SERVER_MEMORY，最好僅指派所需的記憶體數量，這樣才能保留足夠的記憶體給其他程序 (進而避免分頁)。</span><span class="sxs-lookup"><span data-stu-id="c6a49-112">If you use MIN_SERVER_MEMORY, it is better to assign only the amount of memory that is required so sufficient memory remains for other processes (thereby avoiding paging).</span></span>  
  
-   <span data-ttu-id="c6a49-113">不要設定太高的記憶體預先配置值。</span><span class="sxs-lookup"><span data-stu-id="c6a49-113">Do not set the memory pre-allocation value too high.</span></span> <span data-ttu-id="c6a49-114">否則，其他程序可能會在需要時，無法得到足夠的記憶體，而導致記憶體分頁。</span><span class="sxs-lookup"><span data-stu-id="c6a49-114">Otherwise, other processes may not get sufficient memory at the time when they require it, and this can result in memory paging.</span></span>  
  
 <span data-ttu-id="c6a49-115">如果您為具有經記憶體最佳化資料表的資料庫遵循上述作法，即使您有足夠的記憶體來復原資料庫，在嘗試還原和復原資料庫時，還是會導致資料庫陷入「復原暫止」狀態。</span><span class="sxs-lookup"><span data-stu-id="c6a49-115">If you follow the above practices for a database with memory-optimized tables, an attempt to restore and recover a database could result in the database being in a "Recovery Pending" state, even if you have sufficient memory to recover the database.</span></span> <span data-ttu-id="c6a49-116">原因如下，當 [!INCLUDE[hek_2](../includes/hek-2-md.md)] 啟動時，會將資料帶入記憶體的積極程度，更勝於動態記憶體配置將記憶體配置給資料庫。</span><span class="sxs-lookup"><span data-stu-id="c6a49-116">The reason for this is that, when starting up, [!INCLUDE[hek_2](../includes/hek-2-md.md)] brings data into memory more aggressively than dynamic memory allocation allocates memory to the database.</span></span>  
  
 <span data-ttu-id="c6a49-117">**解決方案**</span><span class="sxs-lookup"><span data-stu-id="c6a49-117">**Resolution**</span></span>  
  
 <span data-ttu-id="c6a49-118">若要緩和這個問題，請預先配置足夠的記憶體給資料庫，以復原或重新啟動資料庫，而不是提供最小值，依賴動態記憶體在需要時提供額外的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c6a49-118">To mitigate this, pre-allocate sufficient memory to the database to recover or restart the database, not a minimum value relying on dynamic memory to provide the additional memory when needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a49-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6a49-119">See Also</span></span>  
 [<span data-ttu-id="c6a49-120">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="c6a49-120">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
