---
title: 部分可用性複本已中斷連接 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1bb6535b513770b9b4718a0e8372c0a5bc3cba84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596288"
---
# <a name="some-availability-replicas-are-disconnected"></a><span data-ttu-id="35538-102">部分可用性複本已中斷連接</span><span class="sxs-lookup"><span data-stu-id="35538-102">Some availability replicas are disconnected</span></span>
    
## <a name="introduction"></a><span data-ttu-id="35538-103">簡介</span><span class="sxs-lookup"><span data-stu-id="35538-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35538-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="35538-104">**Policy Name**</span></span>|<span data-ttu-id="35538-105">可用性複本連接狀態</span><span class="sxs-lookup"><span data-stu-id="35538-105">Availability Replicas Connection State</span></span>|  
|<span data-ttu-id="35538-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="35538-106">**Issue**</span></span>|<span data-ttu-id="35538-107">某些可用性複本已中斷連接。</span><span class="sxs-lookup"><span data-stu-id="35538-107">Some availability replicas are disconnected.</span></span>|  
|<span data-ttu-id="35538-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="35538-108">**Category**</span></span>|<span data-ttu-id="35538-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="35538-109">**Warning**</span></span>|  
|<span data-ttu-id="35538-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="35538-110">**Facet**</span></span>|<span data-ttu-id="35538-111">可用性群組</span><span class="sxs-lookup"><span data-stu-id="35538-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="35538-112">描述</span><span class="sxs-lookup"><span data-stu-id="35538-112">Description</span></span>  
 <span data-ttu-id="35538-113">這項原則會積存所有可用性複本的連接狀態，並檢查是否有任何 DISCONENCTED 的可用性複本。</span><span class="sxs-lookup"><span data-stu-id="35538-113">This policy rolls up the connection state of all availability replicas and checks for any availability replicas that are DISCONENCTED.</span></span> <span data-ttu-id="35538-114">當任何可用性複本為 DISCONNECTED 時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="35538-114">The policy is in an unhealthy state when any availability replica is DISCONNECTED.</span></span> <span data-ttu-id="35538-115">否則原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="35538-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35538-116"> 在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [某些可用性複本已中斷連接](https://go.microsoft.com/fwlink/p/?LinkId=220855) 。</span><span class="sxs-lookup"><span data-stu-id="35538-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are disconnected](https://go.microsoft.com/fwlink/p/?LinkId=220855) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="35538-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="35538-117">Possible Causes</span></span>  
 <span data-ttu-id="35538-118">在此可用性群組中，至少一個次要複本未連接至主要複本。</span><span class="sxs-lookup"><span data-stu-id="35538-118">In this availability group, at least one secondary replica is not connected to the primary replica.</span></span> <span data-ttu-id="35538-119">連接狀態為 DISCONNECTED。</span><span class="sxs-lookup"><span data-stu-id="35538-119">The connected state is DISCONNECTED.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="35538-120">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="35538-120">Possible Solution</span></span>  
 <span data-ttu-id="35538-121">使用可用性複本原則狀態，尋找 DISCONNECTED 的可用性複本，然後解決可用性複本上的問題。</span><span class="sxs-lookup"><span data-stu-id="35538-121">Use the availability replica policy state to find the availability replica that is DISCONNECTED, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35538-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35538-122">See Also</span></span>  
 <span data-ttu-id="35538-123">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="35538-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="35538-124">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="35538-124">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
