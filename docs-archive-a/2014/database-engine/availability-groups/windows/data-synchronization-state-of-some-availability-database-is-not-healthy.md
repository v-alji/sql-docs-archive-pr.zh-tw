---
title: 某些可用性資料庫的資料同步處理狀態不健全 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 221f25a1ee7e4a8719acc133372c742ca4a79303
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710797"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a><span data-ttu-id="841b9-102">某些可用性資料庫的資料同步處理狀態不健全</span><span class="sxs-lookup"><span data-stu-id="841b9-102">Data synchronization state of some availability database is not healthy</span></span>
    
## <a name="introduction"></a><span data-ttu-id="841b9-103">簡介</span><span class="sxs-lookup"><span data-stu-id="841b9-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="841b9-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="841b9-104">**Policy Name**</span></span>|<span data-ttu-id="841b9-105">可用性複本資料同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="841b9-105">Availability Replica Data Synchronization State</span></span>|  
|<span data-ttu-id="841b9-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="841b9-106">**Issue**</span></span>|<span data-ttu-id="841b9-107">某個可用性資料庫的資料同步處理狀態不良。</span><span class="sxs-lookup"><span data-stu-id="841b9-107">Data synchronization state of some availability database is not healthy.</span></span>|  
|<span data-ttu-id="841b9-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="841b9-108">**Category**</span></span>|<span data-ttu-id="841b9-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="841b9-109">**Warning**</span></span>|  
|<span data-ttu-id="841b9-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="841b9-110">**Facet**</span></span>|<span data-ttu-id="841b9-111">可用性複本</span><span class="sxs-lookup"><span data-stu-id="841b9-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="841b9-112">描述</span><span class="sxs-lookup"><span data-stu-id="841b9-112">Description</span></span>  
 <span data-ttu-id="841b9-113">此原則會檢查可用性資料庫 (也稱為「資料庫複本」) 的資料同步處理狀態。</span><span class="sxs-lookup"><span data-stu-id="841b9-113">This policy checks the data synchronization state of the availability database (also known as a "database replica").</span></span> <span data-ttu-id="841b9-114">當資料同步處理狀態為 NOT SYNCHRONIZING，或同步認可資料庫複本的狀態不是 SYNCHRONIZED 時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="841b9-114">The policy is in an unhealthy state when the data synchronization state is NOT SYNCHRONIZING or the state is not SYNCHRONIZED for the synchronous-commit database replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="841b9-115">在此 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]版本中，可能原因和解決方案的相關資訊位於 TechNet Wiki 上的 [Data synchronization state of availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220863) (可用性資料庫的資料同步處理狀態不良)。</span><span class="sxs-lookup"><span data-stu-id="841b9-115">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Data synchronization state of availability database is not healthy](https://go.microsoft.com/fwlink/p/?LinkId=220863) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="841b9-116">可能的原因</span><span class="sxs-lookup"><span data-stu-id="841b9-116">Possible Causes</span></span>  
 <span data-ttu-id="841b9-117">複本上至少一個可用性資料庫有狀況不良的資料同步處理狀態。</span><span class="sxs-lookup"><span data-stu-id="841b9-117">At least one availability database on the replica has an unhealthy data synchronization state.</span></span> <span data-ttu-id="841b9-118">如果這是非同步認可可用性複本，所有可用性資料庫都應該處於 SYNCHRONIZING 狀態。</span><span class="sxs-lookup"><span data-stu-id="841b9-118">If this is an asynchronous-commit availability replica, all availability databases should be in the SYNCHRONIZING state.</span></span> <span data-ttu-id="841b9-119">如果這是同步認可可用性複本，所有可用性資料庫都應該處於 SYNCHRONIZED 狀態。</span><span class="sxs-lookup"><span data-stu-id="841b9-119">If this is a synchronous-commit availability replica, all availability databases should be in the SYNCHRONIZED state.</span></span> <span data-ttu-id="841b9-120">這個問題可能是由於下列原因所造成：</span><span class="sxs-lookup"><span data-stu-id="841b9-120">This issue can be caused by the following:</span></span>  
  
-   <span data-ttu-id="841b9-121">可用性複本可能已中斷連接。</span><span class="sxs-lookup"><span data-stu-id="841b9-121">The availability replica might be disconnected.</span></span>  
  
-   <span data-ttu-id="841b9-122">資料移動可能已暫停。</span><span class="sxs-lookup"><span data-stu-id="841b9-122">The data movement might be suspended.</span></span>  
  
-   <span data-ttu-id="841b9-123">資料庫可能無法存取。</span><span class="sxs-lookup"><span data-stu-id="841b9-123">The database might not be accessible.</span></span>  
  
-   <span data-ttu-id="841b9-124">可能由於網路延遲或主要或次要複本上的負載，發生短暫的延遲問題。</span><span class="sxs-lookup"><span data-stu-id="841b9-124">There might be a temporary delay issue due to network latency or the load on the primary or secondary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="841b9-125">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="841b9-125">Possible Solution</span></span>  
 <span data-ttu-id="841b9-126">解決任何連接或資料移動暫停問題。</span><span class="sxs-lookup"><span data-stu-id="841b9-126">Resolve any connection or data movement suspend issues.</span></span> <span data-ttu-id="841b9-127">使用 SQL Server Management Studio，檢查此問題的事件，並尋找資料庫錯誤。</span><span class="sxs-lookup"><span data-stu-id="841b9-127">Check the events for this issue using SQL Server Management Studio, and find the database error.</span></span> <span data-ttu-id="841b9-128">依照特定錯誤的疑難排解步驟進行。</span><span class="sxs-lookup"><span data-stu-id="841b9-128">Follow the troubleshooting steps for the specific error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="841b9-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="841b9-129">See Also</span></span>  
 <span data-ttu-id="841b9-130">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="841b9-130">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="841b9-131">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="841b9-131">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
