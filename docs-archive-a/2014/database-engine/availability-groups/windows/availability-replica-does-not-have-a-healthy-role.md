---
title: 可用性複本沒有狀況良好的角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.arp1rolehealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f7be26945903a5e3b602ef4a99c269de6a58b04a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701929"
---
# <a name="availability-replica-does-not-have-a-healthy-role"></a><span data-ttu-id="0c5cb-102">可用性複本沒有健全的角色</span><span class="sxs-lookup"><span data-stu-id="0c5cb-102">Availability replica does not have a healthy role</span></span>
    
## <a name="introduction"></a><span data-ttu-id="0c5cb-103">簡介</span><span class="sxs-lookup"><span data-stu-id="0c5cb-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c5cb-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="0c5cb-104">**Policy Name**</span></span>|<span data-ttu-id="0c5cb-105">可用性複本的角色狀態</span><span class="sxs-lookup"><span data-stu-id="0c5cb-105">Availability Replica Role State</span></span>|  
|<span data-ttu-id="0c5cb-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="0c5cb-106">**Issue**</span></span>|<span data-ttu-id="0c5cb-107">可用性複本沒有狀況良好的角色。</span><span class="sxs-lookup"><span data-stu-id="0c5cb-107">Availability replica does not have a healthy role.</span></span>|  
|<span data-ttu-id="0c5cb-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="0c5cb-108">**Category**</span></span>|<span data-ttu-id="0c5cb-109">**嚴重**</span><span class="sxs-lookup"><span data-stu-id="0c5cb-109">**Critical**</span></span>|  
|<span data-ttu-id="0c5cb-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="0c5cb-110">**Facet**</span></span>|<span data-ttu-id="0c5cb-111">可用性複本</span><span class="sxs-lookup"><span data-stu-id="0c5cb-111">Availability replica</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c5cb-112">描述</span><span class="sxs-lookup"><span data-stu-id="0c5cb-112">Description</span></span>  
 <span data-ttu-id="0c5cb-113">這項原則檢查可用性複本的角色狀態。</span><span class="sxs-lookup"><span data-stu-id="0c5cb-113">This policy checks the state of the role of the availability replica.</span></span> <span data-ttu-id="0c5cb-114">當可用性複本的角色既不是主要也不是次要時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="0c5cb-114">The policy is in an unhealthy state when the role of the availability replica is neither primary nor secondary.</span></span> <span data-ttu-id="0c5cb-115">否則原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="0c5cb-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c5cb-116">在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [可用性複本沒有狀況良好的角色](https://go.microsoft.com/fwlink/p/?LinkId=220856) 。</span><span class="sxs-lookup"><span data-stu-id="0c5cb-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Availability replica does not have a healthy role](https://go.microsoft.com/fwlink/p/?LinkId=220856) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="0c5cb-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="0c5cb-117">Possible Causes</span></span>  
 <span data-ttu-id="0c5cb-118">可用性複本的角色狀態為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="0c5cb-118">The role of this availability replica is unhealthy.</span></span> <span data-ttu-id="0c5cb-119">複本沒有主要或次要角色。</span><span class="sxs-lookup"><span data-stu-id="0c5cb-119">The replica does not have either the primary or secondary role.</span></span>  
  
## <a name="possible-solution-information_still_to_come"></a><span data-ttu-id="0c5cb-120">可能的解決方案：Information_still_to_come</span><span class="sxs-lookup"><span data-stu-id="0c5cb-120">Possible Solution: Information_still_to_come</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5cb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c5cb-121">See Also</span></span>  
 <span data-ttu-id="0c5cb-122">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0c5cb-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="0c5cb-123">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="0c5cb-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
