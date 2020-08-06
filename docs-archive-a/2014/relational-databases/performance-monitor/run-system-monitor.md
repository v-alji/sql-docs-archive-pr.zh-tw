---
title: 執行活動監視器 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- System Monitor [SQL Server], running
- Windows System Monitor [SQL Server], running
- remote procedure calls [SQL Server]
- starting Windows NT System Monitor
- RPC
ms.assetid: 05297984-bc8d-43df-829c-032387f7ea61
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dd0baf32402d69e36dc5120d0259b2f8d689897
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707390"
---
# <a name="run-system-monitor"></a><span data-ttu-id="39bf9-102">執行系統監視器</span><span class="sxs-lookup"><span data-stu-id="39bf9-102">Run System Monitor</span></span>
  <span data-ttu-id="39bf9-103">「系統監視器」會使用遠端程序呼叫 (RPC) 從 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]收集資訊。</span><span class="sxs-lookup"><span data-stu-id="39bf9-103">System Monitor uses remote procedure calls (RPCs) to collect information from Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39bf9-104">任何擁有 Microsoft Windows 權限可執行「系統監視器」的使用者都可以使用「系統監視器」來監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="39bf9-104">Any user who has Microsoft Windows permissions to run System Monitor can use System Monitor to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39bf9-105">在使用「系統監視器」或「效能監視器」時，您不能連接到在 Windows 98 上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="39bf9-105">When using System Monitor or Performance Monitor, you cannot connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is running on Windows 98.</span></span>  
  
 <span data-ttu-id="39bf9-106">「系統監視器」和所有的效能監視工具一樣，當使用系統監視器監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，必定會對某些效能帶來額外負擔。</span><span class="sxs-lookup"><span data-stu-id="39bf9-106">As with all performance monitoring tools, expect some performance overhead when you use System Monitor to monitor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="39bf9-107">任何特定執行個體的實際負擔取決於硬體平台、計數器數目與選取的更新間隔。</span><span class="sxs-lookup"><span data-stu-id="39bf9-107">The actual overhead in any specific instance depends on the hardware platform, the number of counters, and the selected update interval.</span></span> <span data-ttu-id="39bf9-108">但是，整合「系統監視器」與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的目的是要將會致使效能變差的影響降到最低。</span><span class="sxs-lookup"><span data-stu-id="39bf9-108">However, the integration of System Monitor with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is designed to minimize any reduction in performance.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="39bf9-109">若已在「系統監視器」嵌入式管理單元中選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 效能計數器來進行監視，即使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不在執行中，您也會看到計數器。</span><span class="sxs-lookup"><span data-stu-id="39bf9-109">If you have selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performance counters to monitor in the System Monitor snap-in, you will see the counters even if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not running.</span></span>  
  
 <span data-ttu-id="39bf9-110">如需啟動「系統監視器」的詳細資訊，請參閱[啟動系統監視器 &#40;Windows&#41;](../performance/start-system-monitor-windows.md)。</span><span class="sxs-lookup"><span data-stu-id="39bf9-110">For information about starting System Monitor, see [Start System Monitor &#40;Windows&#41;](../performance/start-system-monitor-windows.md).</span></span>  
  
  
