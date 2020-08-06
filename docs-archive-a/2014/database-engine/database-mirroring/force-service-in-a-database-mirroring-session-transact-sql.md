---
title: 在資料庫鏡像工作階段中強制服務 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b909f3602a78f3244ab3cf4479b8745956a7bd62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709929"
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a><span data-ttu-id="2f61e-102">在資料庫鏡像工作階段中強制服務 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2f61e-102">Force Service in a Database Mirroring Session (Transact-SQL)</span></span>
  <span data-ttu-id="2f61e-103">在高效能模式與不含自動容錯移轉的高安全性模式中，若主體伺服器失敗而鏡像伺服器可用，則資料庫擁有者就可以強制將服務容錯移轉到鏡像資料庫 (有遺失資料的可能)，讓資料庫成為可用。</span><span class="sxs-lookup"><span data-stu-id="2f61e-103">In high-performance mode and high-safety mode without automatic failover, if the principal server fails while the mirror server is available, the database owner can make the database available by forcing service to fail over (with possible data loss) to the mirror database.</span></span> <span data-ttu-id="2f61e-104">只在下列所有狀況成立時才可使用此選項：</span><span class="sxs-lookup"><span data-stu-id="2f61e-104">This option is available only under all the following conditions:</span></span>  
  
-   <span data-ttu-id="2f61e-105">主體伺服器已關閉。</span><span class="sxs-lookup"><span data-stu-id="2f61e-105">The principal server is down.</span></span>  
  
-   <span data-ttu-id="2f61e-106">WITNESS 設定為 OFF，或連接到鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f61e-106">WITNESS is set to OFF or is connected to the mirror server.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2f61e-107">強制服務主要是一種損毀復原方法。</span><span class="sxs-lookup"><span data-stu-id="2f61e-107">Forced service is strictly a disaster recovery method.</span></span> <span data-ttu-id="2f61e-108">強制服務可能造成部分資料遺失。</span><span class="sxs-lookup"><span data-stu-id="2f61e-108">Forcing service may involve some data loss.</span></span> <span data-ttu-id="2f61e-109">因此，只有在您願意冒著遺失一些資料的風險來立即還原資料庫的服務時，才進行強制服務。</span><span class="sxs-lookup"><span data-stu-id="2f61e-109">Therefore, force service only if you are willing to risk losing some data in order to restore service to the database immediately.</span></span> <span data-ttu-id="2f61e-110">如果強制服務有遺失重要資料的風險，建議您停止鏡像並手動重新同步處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f61e-110">If forcing service risks losing significant data, we recommend that you stop mirroring and manually resynchronize the databases.</span></span> <span data-ttu-id="2f61e-111">如需強制服務風險的詳細資訊，請參閱 [資料庫鏡像作業模式](database-mirroring-operating-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="2f61e-111">For more information about the risks of forcing service, see [Database Mirroring Operating Modes](database-mirroring-operating-modes.md).</span></span>  
  
 <span data-ttu-id="2f61e-112">強制服務會暫停工作階段並啟動新的復原分岔。</span><span class="sxs-lookup"><span data-stu-id="2f61e-112">Forcing service suspends the session and starts a new recovery fork.</span></span> <span data-ttu-id="2f61e-113">強制服務的效果類似於移除鏡像並復原之前的主體資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f61e-113">The effect of forcing service is similar to removing mirroring and recovering the former principal database.</span></span> <span data-ttu-id="2f61e-114">不過，在鏡像繼續進行時，強制服務可方便您重新同步處理資料庫 (有遺失資料的可能)。</span><span class="sxs-lookup"><span data-stu-id="2f61e-114">However, forcing service facilitates resynchronizing the databases (with possible data loss) when mirroring resumes.</span></span>  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a><span data-ttu-id="2f61e-115">若要在資料庫鏡像工作階段強制服務</span><span class="sxs-lookup"><span data-stu-id="2f61e-115">To force service in a database mirroring session</span></span>  
  
1.  <span data-ttu-id="2f61e-116">連接鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="2f61e-116">Connect to the mirror server.</span></span>  
  
2.  <span data-ttu-id="2f61e-117">發出下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="2f61e-117">Issue the following statement:</span></span>  
  
     <span data-ttu-id="2f61e-118">ALTER DATABASE <資料庫名稱> SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span><span class="sxs-lookup"><span data-stu-id="2f61e-118">ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS</span></span>  
  
     <span data-ttu-id="2f61e-119">其中 <資料庫名稱> 是鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f61e-119">where *<database_name>* is the mirrored database.</span></span>  
  
     <span data-ttu-id="2f61e-120">鏡像伺服器會立即轉換為主體伺服器，並暫停鏡像。</span><span class="sxs-lookup"><span data-stu-id="2f61e-120">The mirror server immediately transitions to principal server, and mirroring is suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f61e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f61e-121">See Also</span></span>  
 <span data-ttu-id="2f61e-122">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2f61e-122">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="2f61e-123">Database Mirroring Operating Modes</span><span class="sxs-lookup"><span data-stu-id="2f61e-123">Database Mirroring Operating Modes</span></span>](database-mirroring-operating-modes.md)  
  
  
