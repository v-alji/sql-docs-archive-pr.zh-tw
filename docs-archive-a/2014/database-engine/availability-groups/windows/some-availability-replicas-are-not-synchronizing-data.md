---
title: 部分可用性複本未同步處理資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp4synchronizing.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 762b7da1f7b8a07257c2a900307eb1bb10408653
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596285"
---
# <a name="some-availability-replicas-are-not-synchronizing-data"></a><span data-ttu-id="77b4e-102">部分可用性複本未同步處理資料</span><span class="sxs-lookup"><span data-stu-id="77b4e-102">Some availability replicas are not synchronizing data</span></span>
    
## <a name="introduction"></a><span data-ttu-id="77b4e-103">簡介</span><span class="sxs-lookup"><span data-stu-id="77b4e-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77b4e-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="77b4e-104">**Policy Name**</span></span>|<span data-ttu-id="77b4e-105">可用性複本資料同步處理狀態</span><span class="sxs-lookup"><span data-stu-id="77b4e-105">Availability Replicas Data Synchronization State</span></span>|  
|<span data-ttu-id="77b4e-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="77b4e-106">**Issue**</span></span>|<span data-ttu-id="77b4e-107">某些可用性複本並未同步處理資料。</span><span class="sxs-lookup"><span data-stu-id="77b4e-107">Some availability replicas are not synchronizing data.</span></span>|  
|<span data-ttu-id="77b4e-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="77b4e-108">**Category**</span></span>|<span data-ttu-id="77b4e-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="77b4e-109">**Warning**</span></span>|  
|<span data-ttu-id="77b4e-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="77b4e-110">**Facet**</span></span>|<span data-ttu-id="77b4e-111">可用性群組</span><span class="sxs-lookup"><span data-stu-id="77b4e-111">Availability group</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77b4e-112">描述</span><span class="sxs-lookup"><span data-stu-id="77b4e-112">Description</span></span>  
 <span data-ttu-id="77b4e-113">這項原則會積存可用性群組中所有可用性複本的資料同步處理狀態，並檢查是否有任何可用性複本的同步處理無法運作。</span><span class="sxs-lookup"><span data-stu-id="77b4e-113">This policy rolls up the data synchronization state of all availability replicas in the availability group and checks if the synchronization of any availability replica is not operational.</span></span> <span data-ttu-id="77b4e-114">如果可用性複本的任何資料同步處理狀態為 NOT SYNCHRONIZING，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="77b4e-114">The policy is in an unhealthy state if any of the data synchronization states of the availability replica is NOT SYNCRONIZING.</span></span>  
  
 <span data-ttu-id="77b4e-115">如果可用性複本的任何資料同步處理狀態都不是 NOT SYNCHRONIZING，此原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="77b4e-115">This policy is in a healthy state if none of the data synchronization states of the availability replica is NOT SYNCHRONIZING.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="77b4e-116">在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [某些可用性複本並未同步處理資料](https://go.microsoft.com/fwlink/p/?LinkId=220852) 。</span><span class="sxs-lookup"><span data-stu-id="77b4e-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Some availability replicas are not synchronizing data](https://go.microsoft.com/fwlink/p/?LinkId=220852) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="77b4e-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="77b4e-117">Possible Causes</span></span>  
 <span data-ttu-id="77b4e-118">在這個可用性群組中，至少有一個次要複本具有 NOT SYNCHRONIZING 同步處理狀態，而且並未收到來自主要複本的資料。</span><span class="sxs-lookup"><span data-stu-id="77b4e-118">In this availability group, at least one secondary replica has a NOT SYNCHRONIZING synchronization state and is not receiving data from the primary replica.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="77b4e-119">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="77b4e-119">Possible Solution</span></span>  
 <span data-ttu-id="77b4e-120">使用可用性複本原則狀態，尋找具有 NOT SYNCHROINIZING 狀態的可用性複本，然後解決可用性複本上的問題。</span><span class="sxs-lookup"><span data-stu-id="77b4e-120">Use the availability replica policy state to find the availability replica with a NOT SYNCHROINIZING state, and then resolve the issue at the availability replica.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b4e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77b4e-121">See Also</span></span>  
 <span data-ttu-id="77b4e-122">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="77b4e-122">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="77b4e-123">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="77b4e-123">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
