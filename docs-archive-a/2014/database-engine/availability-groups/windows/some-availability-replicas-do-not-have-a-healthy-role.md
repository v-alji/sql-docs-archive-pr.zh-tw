---
title: 某些可用性複本沒有狀況良好的角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 801fe20edf6f2dbe09bc800722cf4210988ebc69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596284"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a><span data-ttu-id="c47d4-102">某些可用性複本沒有狀況良好的角色</span><span class="sxs-lookup"><span data-stu-id="c47d4-102">Some availability replicas do not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="c47d4-103">簡介</span><span class="sxs-lookup"><span data-stu-id="c47d4-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c47d4-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="c47d4-104">**Policy Name**</span></span>|<span data-ttu-id="c47d4-105">可用性複本角色狀態</span><span class="sxs-lookup"><span data-stu-id="c47d4-105">Availability Replicas Role State</span></span>|  
|<span data-ttu-id="c47d4-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="c47d4-106">**Issue**</span></span>|<span data-ttu-id="c47d4-107">某些可用性複本沒有狀況良好的角色。</span><span class="sxs-lookup"><span data-stu-id="c47d4-107">Some availability replicas do not have a healthy role.</span></span>|  
|<span data-ttu-id="c47d4-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="c47d4-108">**Category**</span></span>|<span data-ttu-id="c47d4-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="c47d4-109">**Warning**</span></span>|  
|<span data-ttu-id="c47d4-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="c47d4-110">**Facet**</span></span>|<span data-ttu-id="c47d4-111">可用性群組</span><span class="sxs-lookup"><span data-stu-id="c47d4-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c47d4-112">描述</span><span class="sxs-lookup"><span data-stu-id="c47d4-112">Description</span></span>  
 <span data-ttu-id="c47d4-113">這項原則會積存所有可用性複本的連接狀態，並檢查是否有任何可用性複本沒有狀況良好的角色。</span><span class="sxs-lookup"><span data-stu-id="c47d4-113">This policy rolls up the connection state of all availability replicas and checks if there are any availability replicas that are not in a healthy role.</span></span> <span data-ttu-id="c47d4-114">當可用性複本既不是主要也不是次要時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="c47d4-114">The policy is in an unhealthy state when any availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="c47d4-115">否則原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="c47d4-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c47d4-116">在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [某些可用性複本沒有狀況良好的角色](https://go.microsoft.com/fwlink/p/?LinkId=220854) 。</span><span class="sxs-lookup"><span data-stu-id="c47d4-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas do not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220854) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="c47d4-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="c47d4-117">Possible Causes</span></span>  
 <span data-ttu-id="c47d4-118">在此可用性群組中，至少一個可用性複本目前沒有主要或次要角色。</span><span class="sxs-lookup"><span data-stu-id="c47d4-118">In this availability group, at least one availability replica does not currently have the primary or secondary role.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="c47d4-119">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="c47d4-119">Possible Solution</span></span>  
 <span data-ttu-id="c47d4-120">使用可用性複本原則狀態，尋找其角色不是主要或次要的可用性複本，然後解決可用性複本上的問題。</span><span class="sxs-lookup"><span data-stu-id="c47d4-120">Use the availability replica policy state to find the availability replica whose role is not primary or secondary, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c47d4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c47d4-121">See Also</span></span>  
 <span data-ttu-id="c47d4-122">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c47d4-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="c47d4-123">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="c47d4-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
