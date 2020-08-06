---
title: SQL Server 的 ExecStatistics 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d1a50c97add4708a58b9edc45fd49982b97a51ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592637"
---
# <a name="sql-server-execstatistics-object"></a><span data-ttu-id="a3243-102">SQL Server 的 ExecStatistics 物件</span><span class="sxs-lookup"><span data-stu-id="a3243-102">SQL Server, ExecStatistics Object</span></span>
  <span data-ttu-id="a3243-103">Microsoft SQL Server 中的 **SQLServer:ExecStatistics** 物件提供計數器來監視各種執行情形。</span><span class="sxs-lookup"><span data-stu-id="a3243-103">The **SQLServer:ExecStatistics** object in Microsoft SQL Server provides counters to monitor various executions.</span></span>  
  
 <span data-ttu-id="a3243-104">下表描述 SQL Server **Exec Statistics** 計數器。</span><span class="sxs-lookup"><span data-stu-id="a3243-104">This table describes the SQL Server **Exec Statistics** counters.</span></span>  
  
|<span data-ttu-id="a3243-105">SQL Server Exec Statistics 計數器</span><span class="sxs-lookup"><span data-stu-id="a3243-105">SQL Server Exec Statistics counters</span></span>|<span data-ttu-id="a3243-106">描述</span><span class="sxs-lookup"><span data-stu-id="a3243-106">Description</span></span>|  
|-----------------------------------------|-----------------|  
|<span data-ttu-id="a3243-107">**Distributed Query**</span><span class="sxs-lookup"><span data-stu-id="a3243-107">**Distributed Query**</span></span>|<span data-ttu-id="a3243-108">執行分散式查詢的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3243-108">Statistics relevant to execution of distributed queries.</span></span>|  
|<span data-ttu-id="a3243-109">**DTC calls**</span><span class="sxs-lookup"><span data-stu-id="a3243-109">**DTC calls**</span></span>|<span data-ttu-id="a3243-110">執行 DTC 呼叫的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3243-110">Statistics relevant to execution of DTC calls.</span></span>|  
|<span data-ttu-id="a3243-111">**Extended Procedures**</span><span class="sxs-lookup"><span data-stu-id="a3243-111">**Extended Procedures**</span></span>|<span data-ttu-id="a3243-112">執行擴充程序的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3243-112">Statistics relevant to execution of extended procedures.</span></span>|  
|<span data-ttu-id="a3243-113">**OLEDB calls**</span><span class="sxs-lookup"><span data-stu-id="a3243-113">**OLEDB calls**</span></span>|<span data-ttu-id="a3243-114">執行 OLEDB 呼叫的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="a3243-114">Statistics relevant to execution of OLEDB calls.</span></span>|  
  
 <span data-ttu-id="a3243-115">物件中的每個計數器均包含下列執行個體：</span><span class="sxs-lookup"><span data-stu-id="a3243-115">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="a3243-116">項目</span><span class="sxs-lookup"><span data-stu-id="a3243-116">Item</span></span>|<span data-ttu-id="a3243-117">描述</span><span class="sxs-lookup"><span data-stu-id="a3243-117">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a3243-118">**平均執行時間 (ms)**</span><span class="sxs-lookup"><span data-stu-id="a3243-118">**Average execution time (ms)**</span></span>|<span data-ttu-id="a3243-119">選取的執行類型之平均執行時間。</span><span class="sxs-lookup"><span data-stu-id="a3243-119">Average execution time of the selected type of execution.</span></span>|  
|<span data-ttu-id="a3243-120">**每秒累計執行時間 (ms)**</span><span class="sxs-lookup"><span data-stu-id="a3243-120">**Cumulative execution time (ms) per second**</span></span>|<span data-ttu-id="a3243-121">選取的執行類型之每秒彙總執行時間。</span><span class="sxs-lookup"><span data-stu-id="a3243-121">Aggregated execution time per second, of the selected type of execution.</span></span>|  
|<span data-ttu-id="a3243-122">**正在執行數目**</span><span class="sxs-lookup"><span data-stu-id="a3243-122">**Execs in progress**</span></span>|<span data-ttu-id="a3243-123">選取的執行類型之進行中執行數目。</span><span class="sxs-lookup"><span data-stu-id="a3243-123">Number of execs in progress of the selected type of execution.</span></span>|  
|<span data-ttu-id="a3243-124">**每秒開始執行數目**</span><span class="sxs-lookup"><span data-stu-id="a3243-124">**Exec started per second**</span></span>|<span data-ttu-id="a3243-125">選取的執行類型之每秒開始的執行數目。</span><span class="sxs-lookup"><span data-stu-id="a3243-125">Number of exes started per second of the selected type of execution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3243-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3243-126">See Also</span></span>  
 [<span data-ttu-id="a3243-127">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="a3243-127">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
