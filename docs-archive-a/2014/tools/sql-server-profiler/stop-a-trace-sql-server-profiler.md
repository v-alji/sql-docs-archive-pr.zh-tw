---
title: 停止追蹤 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], stopping
- stopping traces
ms.assetid: 47c4f33d-63e0-4444-bec8-4c1c91f8e25c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 501ea4a4838f8e2ea42fc475c486466d48020a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703573"
---
# <a name="stop-a-trace-sql-server-profiler"></a><span data-ttu-id="43e2e-102">停止追蹤 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="43e2e-102">Stop a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="43e2e-103">此主題說明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來停止執行中的追蹤。</span><span class="sxs-lookup"><span data-stu-id="43e2e-103">This topic describes how to stop a trace that is running by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
 <span data-ttu-id="43e2e-104">停止追蹤便會停止擷取資料。</span><span class="sxs-lookup"><span data-stu-id="43e2e-104">Stopping a trace stops data from being captured.</span></span> <span data-ttu-id="43e2e-105">追蹤一旦停止，重新啟動之後將會遺失先前所擷取的資料，除非已經將資料擷取到追蹤檔或追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="43e2e-105">After a trace is stopped, it cannot be restarted without losing previously captured data, unless the data has been captured to a trace file or trace table.</span></span> <span data-ttu-id="43e2e-106">您也可以在停止追蹤之後，將收集的資料儲存至資料表或檔案。</span><span class="sxs-lookup"><span data-stu-id="43e2e-106">You can also save the collected data to a table or file after stopping a trace.</span></span> <span data-ttu-id="43e2e-107">追蹤停止時，先前所選取的所有追蹤屬性將會保留。</span><span class="sxs-lookup"><span data-stu-id="43e2e-107">All trace properties that were previously selected are preserved when a trace is stopped.</span></span> <span data-ttu-id="43e2e-108">此時您可以變更名稱、事件、欄位及篩選條件。</span><span class="sxs-lookup"><span data-stu-id="43e2e-108">When a trace is stopped, you can change the name, events, columns, and filters.</span></span>  
  
### <a name="to-stop-a-trace"></a><span data-ttu-id="43e2e-109">若要停止追蹤</span><span class="sxs-lookup"><span data-stu-id="43e2e-109">To stop a trace</span></span>  
  
1.  <span data-ttu-id="43e2e-110">選擇執行中的追蹤。</span><span class="sxs-lookup"><span data-stu-id="43e2e-110">Select a trace that is running.</span></span>  
  
2.  <span data-ttu-id="43e2e-111">在 **[檔案]** 功能表上，按一下 **[停止追蹤]** 。</span><span class="sxs-lookup"><span data-stu-id="43e2e-111">On the **File** menu, click **Stop Trace**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e2e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43e2e-112">See Also</span></span>  
 [<span data-ttu-id="43e2e-113">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="43e2e-113">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
