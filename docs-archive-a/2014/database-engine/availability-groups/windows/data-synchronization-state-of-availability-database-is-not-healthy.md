---
title: 可用性資料庫的資料同步處理狀態不健全 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a179008c20b108a2f6aaefd5dd80b22708e94a8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710806"
---
# <a name="data-synchronization-state-of-availability-database-is-not-healthy"></a><span data-ttu-id="bfa7d-102">可用性資料庫的資料同步處理狀態不健全</span><span class="sxs-lookup"><span data-stu-id="bfa7d-102">Data synchronization state of availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="bfa7d-103">簡介</span><span class="sxs-lookup"><span data-stu-id="bfa7d-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bfa7d-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="bfa7d-104">**Policy Name**</span></span>|<span data-ttu-id="bfa7d-105">可用性資料庫資料同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="bfa7d-105">Availability Database Data Synchronization State</span></span>|  
|<span data-ttu-id="bfa7d-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="bfa7d-106">**Issue**</span></span>|<span data-ttu-id="bfa7d-107">可用性資料庫的資料同步處理狀態不良。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-107">Data synchronization state of availability database is not healthy.</span></span>|  
|<span data-ttu-id="bfa7d-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="bfa7d-108">**Category**</span></span>|<span data-ttu-id="bfa7d-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="bfa7d-109">**Warning**</span></span>|  
|<span data-ttu-id="bfa7d-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="bfa7d-110">**Facet**</span></span>|<span data-ttu-id="bfa7d-111">可用性資料庫</span><span class="sxs-lookup"><span data-stu-id="bfa7d-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bfa7d-112">描述</span><span class="sxs-lookup"><span data-stu-id="bfa7d-112">Description</span></span>  
 <span data-ttu-id="bfa7d-113">這項原則會積存可用性複本中所有可用性資料庫 (也稱為「資料庫複本」) 的資料同步處理狀態。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-113">This policy rolls up the data synchronization state of all availability databases (also known as "database replicas") in the availability replica.</span></span> <span data-ttu-id="bfa7d-114">當任何資料庫複本不在預期的資料同步處理狀態時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-114">The policy is in an unhealthy sate when any database replica is not in the expected data synchronization state.</span></span> <span data-ttu-id="bfa7d-115">否則原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bfa7d-116">在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [可用性資料庫的資料同步處理狀態不良](https://go.microsoft.com/fwlink/p/?LinkId=220858) 。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of some availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220858) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="bfa7d-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="bfa7d-117">Possible Causes</span></span>  
 <span data-ttu-id="bfa7d-118">此可用性資料庫的資料同步處理狀態不良。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-118">The data synchronization state of this availability database is unhealthy.</span></span> <span data-ttu-id="bfa7d-119">在非同步認可可用性複本上，每個可用性資料庫都應該處於 SYNCHRONIZING 狀態。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-119">On an asynchronous-commit availability replica, every availability database should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="bfa7d-120">在同步認可複本上，每個可用性資料庫都必須處於 SYNCHRONIZED 狀態。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-120">On a synchronous-commit replica, every availability database must be in the SYNCHRONIZED state.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="bfa7d-121">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="bfa7d-121">Possible Solution</span></span>  
 <span data-ttu-id="bfa7d-122">使用此資料庫複本原則，尋找資料同步處理狀態不良的資料庫複本，然後解決資料庫複本上的問題。</span><span class="sxs-lookup"><span data-stu-id="bfa7d-122">Use the database replica policy to find the database replica with an unhealthy data synchronization state, and then resolve the issue at the database replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa7d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfa7d-123">See Also</span></span>  
 <span data-ttu-id="bfa7d-124">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bfa7d-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="bfa7d-125">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="bfa7d-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
