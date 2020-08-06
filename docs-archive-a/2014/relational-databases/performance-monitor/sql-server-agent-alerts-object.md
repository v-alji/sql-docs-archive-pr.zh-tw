---
title: SQL Server Agent、Alerts 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9aa6fa871730af8cf129b3ea6b0aa4f1853d7e4d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593352"
---
# <a name="sql-server-agent-alerts-object"></a><span data-ttu-id="ac82d-102">SQL Server Agent、Alerts 物件</span><span class="sxs-lookup"><span data-stu-id="ac82d-102">SQL Server Agent, Alerts Object</span></span>
  <span data-ttu-id="ac82d-103">SQL Server Agent 的「 **警示** 」效能物件包含效能計數器，用來報告 SQL Server Agent 警示的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ac82d-103">The SQL Server Agent **Alerts** performance object contains performance counters that report information about SQL Server Agent alerts.</span></span> <span data-ttu-id="ac82d-104">下表列出這個物件包含的計數器。</span><span class="sxs-lookup"><span data-stu-id="ac82d-104">The table below lists the counters that this object contains.</span></span>  
  
 <span data-ttu-id="ac82d-105">下表包含 **SQLAgent:Alerts** 計數器。</span><span class="sxs-lookup"><span data-stu-id="ac82d-105">The table below contains the **SQLAgent:Alerts** counters.</span></span>  
  
|<span data-ttu-id="ac82d-106">Name</span><span class="sxs-lookup"><span data-stu-id="ac82d-106">Name</span></span>|<span data-ttu-id="ac82d-107">描述</span><span class="sxs-lookup"><span data-stu-id="ac82d-107">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="ac82d-108">**Activated alerts**</span><span class="sxs-lookup"><span data-stu-id="ac82d-108">**Activated alerts**</span></span>|<span data-ttu-id="ac82d-109">這個計數器報告自從 SQL Server Agent 上次重新啟動後，SQL Server Agent 已啟動的警示總數。</span><span class="sxs-lookup"><span data-stu-id="ac82d-109">This counter reports the total number of alerts that SQL Server Agent has activated since the last time that SQL Server Agent restarted.</span></span>|  
|<span data-ttu-id="ac82d-110">**Alerts activated/minute**</span><span class="sxs-lookup"><span data-stu-id="ac82d-110">**Alerts activated/minute**</span></span>|<span data-ttu-id="ac82d-111">這個計數器報告 SQL Server Agent 在前一分鐘內所啟動的警示數目。</span><span class="sxs-lookup"><span data-stu-id="ac82d-111">This counter reports the number of alerts that SQL Server Agent activated within the last minute.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="ac82d-112">若要使用此 SQL Server Agent 物件，使用者必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="ac82d-112">To use this SQL Server Agent object, users must be a member of the **sysadmin** fixed server role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac82d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac82d-113">See Also</span></span>  
 <span data-ttu-id="ac82d-114">[警示](../../ssms/agent/alerts.md) </span><span class="sxs-lookup"><span data-stu-id="ac82d-114">[Alerts](../../ssms/agent/alerts.md) </span></span>  
 <span data-ttu-id="ac82d-115">[使用效能物件](../../ssms/agent/use-performance-objects.md) </span><span class="sxs-lookup"><span data-stu-id="ac82d-115">[Use Performance Objects](../../ssms/agent/use-performance-objects.md) </span></span>  
 [<span data-ttu-id="ac82d-116">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="ac82d-116">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
