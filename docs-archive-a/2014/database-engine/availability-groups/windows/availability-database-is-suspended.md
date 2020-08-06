---
title: 可用性資料庫已暫停 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07a547f217367f13df739348325461c862d831f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585623"
---
# <a name="availability-database-is-suspended"></a><span data-ttu-id="079d6-102">可用性資料庫已暫停</span><span class="sxs-lookup"><span data-stu-id="079d6-102">Availability database is suspended</span></span>
    
## <a name="introduction"></a><span data-ttu-id="079d6-103">簡介</span><span class="sxs-lookup"><span data-stu-id="079d6-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="079d6-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="079d6-104">**Policy Name**</span></span>|<span data-ttu-id="079d6-105">可用性資料庫暫停狀態</span><span class="sxs-lookup"><span data-stu-id="079d6-105">Availability Database Suspension State</span></span>|  
|<span data-ttu-id="079d6-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="079d6-106">**Issue**</span></span>|<span data-ttu-id="079d6-107">可用性資料庫已暫停。</span><span class="sxs-lookup"><span data-stu-id="079d6-107">Availability database is suspended.</span></span>|  
|<span data-ttu-id="079d6-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="079d6-108">**Category**</span></span>|<span data-ttu-id="079d6-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="079d6-109">**Warning**</span></span>|  
|<span data-ttu-id="079d6-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="079d6-110">**Facet**</span></span>|<span data-ttu-id="079d6-111">可用性資料庫</span><span class="sxs-lookup"><span data-stu-id="079d6-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="079d6-112">描述</span><span class="sxs-lookup"><span data-stu-id="079d6-112">Description</span></span>  
 <span data-ttu-id="079d6-113">此原則會檢查次要資料庫 (也稱為「次要資料庫複本」) 的資料移動。</span><span class="sxs-lookup"><span data-stu-id="079d6-113">This policy checks the state of data movement of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="079d6-114">當資料移動已暫停時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="079d6-114">The policy is in an unhealthy state when the data movement is suspended.</span></span> <span data-ttu-id="079d6-115">否則原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="079d6-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="079d6-116">在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [可用性資料庫已暫停](https://go.microsoft.com/fwlink/p/?LinkId=220860) 。</span><span class="sxs-lookup"><span data-stu-id="079d6-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability database is suspended](https://go.microsoft.com/fwlink/p/?LinkId=220860) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="079d6-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="079d6-117">Possible Causes</span></span>  
 <span data-ttu-id="079d6-118">由於下列原因，此可用性資料庫上的資料同步處理可能已暫停：</span><span class="sxs-lookup"><span data-stu-id="079d6-118">Data synchronization on this availability database might have been suspended because of the following:</span></span>  
  
-   <span data-ttu-id="079d6-119">由於錯誤，系統可能已暫停資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="079d6-119">Due to an error, the system might have suspended data synchronization.</span></span>  
  
-   <span data-ttu-id="079d6-120">資料庫管理員可能為了進行維護已暫停資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="079d6-120">The database administrator might have suspended data synchronization for maintenance purposes.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="079d6-121">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="079d6-121">Possible Solution</span></span>  
 <span data-ttu-id="079d6-122">繼續資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="079d6-122">Resume data synchronization.</span></span> <span data-ttu-id="079d6-123">如果問題仍然存在，請檢查事件記錄檔中的可用性群組，然後診斷為什麼系統暫停資料移動。</span><span class="sxs-lookup"><span data-stu-id="079d6-123">If the issue persists, check the availability group in the Event log, and then diagnose why the system suspended data movement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079d6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="079d6-124">See Also</span></span>  
 <span data-ttu-id="079d6-125">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="079d6-125">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="079d6-126">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="079d6-126">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
