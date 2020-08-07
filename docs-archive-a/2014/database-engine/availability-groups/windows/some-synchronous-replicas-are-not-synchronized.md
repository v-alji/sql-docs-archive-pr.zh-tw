---
title: 未同步處理某些同步複本 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ecef2d16e80e128834a71e1f1f112096f8ccc9cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596279"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a><span data-ttu-id="8c00a-102">未同步處理某些同步複本</span><span class="sxs-lookup"><span data-stu-id="8c00a-102">Some synchronous replicas are not synchronized</span></span>
    
## <a name="introduction"></a><span data-ttu-id="8c00a-103">簡介</span><span class="sxs-lookup"><span data-stu-id="8c00a-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c00a-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="8c00a-104">**Policy Name**</span></span>|<span data-ttu-id="8c00a-105">同步複本的資料同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="8c00a-105">Synchronous Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="8c00a-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="8c00a-106">**Issue**</span></span>|<span data-ttu-id="8c00a-107">某些同步複本並未同步處理。</span><span class="sxs-lookup"><span data-stu-id="8c00a-107">Some synchronous replicas are not synchronized.</span></span>|  
|<span data-ttu-id="8c00a-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="8c00a-108">**Category**</span></span>|<span data-ttu-id="8c00a-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="8c00a-109">**Warning**</span></span>|  
|<span data-ttu-id="8c00a-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="8c00a-110">**Facet**</span></span>|<span data-ttu-id="8c00a-111">可用性群組</span><span class="sxs-lookup"><span data-stu-id="8c00a-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c00a-112">描述</span><span class="sxs-lookup"><span data-stu-id="8c00a-112">Description</span></span>  
 <span data-ttu-id="8c00a-113">這項原則會積存所有可用性複本的資料同步處理狀態，並檢查是否有任何可用性複本未處於預期的同步處理狀態。</span><span class="sxs-lookup"><span data-stu-id="8c00a-113">This policy rolls up the data synchronization state of all availability replicas and checks for any availability replicas that are not in the expected synchronization state.</span></span> <span data-ttu-id="8c00a-114">當任何非同步複本不是處於 SYNCHRONIZING 狀態，而且任何同步複本不是處於 SYNCHRONIZED 狀態時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="8c00a-114">The policy is in an unhealthy state when any asynchronous replica is not in a SYNCHRONIZING state and any synchronous replica is not in a SYNCHRONIZED state.</span></span> <span data-ttu-id="8c00a-115">否則原則狀態良好。</span><span class="sxs-lookup"><span data-stu-id="8c00a-115">The policy state is otherwise healthy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8c00a-116">在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [未同步處理某些同步複本](https://go.microsoft.com/fwlink/p/?LinkId=220853) 。</span><span class="sxs-lookup"><span data-stu-id="8c00a-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some synchronous replicas are not synchronized](https://go.microsoft.com/fwlink/p/?LinkId=220853) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="8c00a-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="8c00a-117">Possible Causes</span></span>  
 <span data-ttu-id="8c00a-118">在這個可用性群組中，至少有一個可用性複本目前並未同步處理。</span><span class="sxs-lookup"><span data-stu-id="8c00a-118">In this availability group, at least one synchronous replica is not currently synchronized.</span></span> <span data-ttu-id="8c00a-119">複本同步處理狀態可能是 SYNCHONIZING 或 NOT SYNCHRONIZING。</span><span class="sxs-lookup"><span data-stu-id="8c00a-119">The replica synchronization state could be either SYNCHONIZING or NOT SYNCHRONIZING.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="8c00a-120">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="8c00a-120">Possible Solution</span></span>  
 <span data-ttu-id="8c00a-121">使用可用性複本原則狀態，尋找同步處理狀態不正確的可用性複本，然後解決可用性複本上的問題。</span><span class="sxs-lookup"><span data-stu-id="8c00a-121">Use the availability replica policy state to find the availability replica with the incorrect synchronization state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c00a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c00a-122">See Also</span></span>  
 <span data-ttu-id="8c00a-123">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8c00a-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="8c00a-124">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8c00a-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
