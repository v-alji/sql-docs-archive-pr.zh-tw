---
title: 次要資料庫未聯結 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81275e85fd865924778f6d6f985e170a5bda9f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707890"
---
# <a name="secondary-database-is-not-joined"></a><span data-ttu-id="5bb68-102">次要資料庫未加入</span><span class="sxs-lookup"><span data-stu-id="5bb68-102">Secondary database is not joined</span></span>
    
## <a name="introduction"></a><span data-ttu-id="5bb68-103">簡介</span><span class="sxs-lookup"><span data-stu-id="5bb68-103">Introduction</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bb68-104">**原則名稱**</span><span class="sxs-lookup"><span data-stu-id="5bb68-104">**Policy Name**</span></span>|<span data-ttu-id="5bb68-105">可用性資料庫聯結狀態</span><span class="sxs-lookup"><span data-stu-id="5bb68-105">Availability Database Join State</span></span>|  
|<span data-ttu-id="5bb68-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="5bb68-106">**Issue**</span></span>|<span data-ttu-id="5bb68-107">次要資料庫並未聯結。</span><span class="sxs-lookup"><span data-stu-id="5bb68-107">Secondary database is not joined.</span></span>|  
|<span data-ttu-id="5bb68-108">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="5bb68-108">**Category**</span></span>|<span data-ttu-id="5bb68-109">**警告**</span><span class="sxs-lookup"><span data-stu-id="5bb68-109">**Warning**</span></span>|  
|<span data-ttu-id="5bb68-110">**Facet**</span><span class="sxs-lookup"><span data-stu-id="5bb68-110">**Facet**</span></span>|<span data-ttu-id="5bb68-111">可用性資料庫</span><span class="sxs-lookup"><span data-stu-id="5bb68-111">Availability database</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5bb68-112">描述</span><span class="sxs-lookup"><span data-stu-id="5bb68-112">Description</span></span>  
 <span data-ttu-id="5bb68-113">此原則會檢查次要資料庫 (也稱為「次要資料庫複本」) 的聯結狀態。</span><span class="sxs-lookup"><span data-stu-id="5bb68-113">This policy checks the join state of the secondary database (also known as a "secondary database replica").</span></span> <span data-ttu-id="5bb68-114">當資料庫複本未聯結時，原則為狀況不良。</span><span class="sxs-lookup"><span data-stu-id="5bb68-114">The policy is in an unhealthy state when the dataset replica is not joined.</span></span> <span data-ttu-id="5bb68-115">否則原則為狀況良好。</span><span class="sxs-lookup"><span data-stu-id="5bb68-115">The policy is otherwise in a healthy state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bb68-116">在此 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]版本中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [Secondary database is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220862) (次要資料庫並未聯結)。</span><span class="sxs-lookup"><span data-stu-id="5bb68-116">For this release of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], information about possible causes and solutions is located at [Secondary database is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220862) on the TechNet Wiki.</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="5bb68-117">可能的原因</span><span class="sxs-lookup"><span data-stu-id="5bb68-117">Possible Causes</span></span>  
 <span data-ttu-id="5bb68-118">此次要資料庫並未聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="5bb68-118">This secondary database is not joined to the availability group.</span></span> <span data-ttu-id="5bb68-119">此次要資料庫的組態不完整。</span><span class="sxs-lookup"><span data-stu-id="5bb68-119">The configuration of this secondary database is incomplete.</span></span>  
  
## <a name="possible-solution"></a><span data-ttu-id="5bb68-120">可能的解決方案</span><span class="sxs-lookup"><span data-stu-id="5bb68-120">Possible Solution</span></span>  
 <span data-ttu-id="5bb68-121">使用 Transact-SQL、PowerShell 或 SQL Server Management Studio，將次要複本聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="5bb68-121">Use Transact-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group.</span></span> <span data-ttu-id="5bb68-122">如需將次要複本聯結至可用性群組的詳細資訊，請參閱 [將次要複本聯結至可用性群組 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="5bb68-122">For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb68-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bb68-123">See Also</span></span>  
 <span data-ttu-id="5bb68-124">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5bb68-124">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="5bb68-125">使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5bb68-125">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
