---
title: 建立效能基準 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], baselines
- monitoring performance [SQL Server], baselines
- tuning databases [SQL Server], baselines
- server performance [SQL Server], baselines
- performance [SQL Server], baselines
- baseline performance [SQL Server]
- measurements for baseline statistics [SQL Server]
- monitoring server performance [SQL Server], establishing baseline
- database monitoring [SQL Server], baselines
ms.assetid: dc5aa8d6-2507-448f-ad86-4196443915fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0cb85ae8ad370b816c6240b58aabd247c7593c16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687782"
---
# <a name="establish-a-performance-baseline"></a><span data-ttu-id="c4eb9-102">建立效能基準</span><span class="sxs-lookup"><span data-stu-id="c4eb9-102">Establish a Performance Baseline</span></span>
  <span data-ttu-id="c4eb9-103">若要判斷您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統是否以最佳方式執行，請長時間定期測量效能 (即使沒有問題發生)，以建立伺服器效能基準。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-103">To determine whether your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system is performing optimally, take performance measurements at regular intervals over time, even when no problems occur, to establish a server performance baseline.</span></span> <span data-ttu-id="c4eb9-104">請將每個新的組測量的結果與先前的測量進行比較。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-104">Compare each new set of measurements with those taken earlier.</span></span>  
  
 <span data-ttu-id="c4eb9-105">以下各方面會影響 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的效能：</span><span class="sxs-lookup"><span data-stu-id="c4eb9-105">The following areas affect the performance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="c4eb9-106">系統資源 (硬體)</span><span class="sxs-lookup"><span data-stu-id="c4eb9-106">System resources (hardware)</span></span>  
  
-   <span data-ttu-id="c4eb9-107">網路架構</span><span class="sxs-lookup"><span data-stu-id="c4eb9-107">Network architecture</span></span>  
  
-   <span data-ttu-id="c4eb9-108">作業系統</span><span class="sxs-lookup"><span data-stu-id="c4eb9-108">The operating system</span></span>  
  
-   <span data-ttu-id="c4eb9-109">資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="c4eb9-109">Database applications</span></span>  
  
-   <span data-ttu-id="c4eb9-110">用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="c4eb9-110">Client applications</span></span>  
  
 <span data-ttu-id="c4eb9-111">至少需使用基準線測量來判斷：</span><span class="sxs-lookup"><span data-stu-id="c4eb9-111">At a minimum, use baseline measurements to determine:</span></span>  
  
-   <span data-ttu-id="c4eb9-112">作業的尖峰與離峰期間。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-112">Peak and off-peak hours of operation.</span></span>  
  
-   <span data-ttu-id="c4eb9-113">產生查詢或批次命令的回應時間。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-113">Production-query or batch-command response times.</span></span>  
  
-   <span data-ttu-id="c4eb9-114">資料庫備份與還原的完成時間。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-114">Database backup and restore completion times.</span></span>  
  
 <span data-ttu-id="c4eb9-115">建立伺服器效能基準線之後，請將基準線統計資料表與目前的伺服器效能進行比較。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-115">After you establish a server performance baseline, compare the baseline statistics to current server performance.</span></span> <span data-ttu-id="c4eb9-116">與基準線差距過高或過低的數值即為必須進一步調查的候選項目。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-116">Numbers far above or far below your baseline are candidates for further investigation.</span></span> <span data-ttu-id="c4eb9-117">這些項目可能代表必須調整或重設設定的範圍。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-117">They may indicate areas in need of tuning or reconfiguration.</span></span> <span data-ttu-id="c4eb9-118">例如，當執行一組查詢的時間量增加時，請檢查查詢以判斷是否可以重寫查詢，或者是否必須加入資料行統計資料或新的索引。</span><span class="sxs-lookup"><span data-stu-id="c4eb9-118">For example, if the amount of time to execute a set of queries increases, examine the queries to determine if they can be rewritten, or if column statistics or new indexes must be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4eb9-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4eb9-119">See Also</span></span>  
 [<span data-ttu-id="c4eb9-120">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c4eb9-120">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
