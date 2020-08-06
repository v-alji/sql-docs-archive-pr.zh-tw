---
title: SQL Server Profiler-效能計數器限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.performancecounterlimit.f1
helpviewer_keywords:
- Performance Counters List dialog box
ms.assetid: d10140ef-36c4-449c-b365-1cff1b2524e4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27bda135abaf9d91b078e36a69a87098a734acbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705374"
---
# <a name="sql-server-profiler---performance-counters-limit"></a><span data-ttu-id="8548e-102">SQL Server Profiler - 效能計數器限制</span><span class="sxs-lookup"><span data-stu-id="8548e-102">SQL Server Profiler - Performance Counters Limit</span></span>
  <span data-ttu-id="8548e-103">使用 [效能計數器限制] 對話方塊，即可在與 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 追蹤建立相互關聯時，限制系統監視器效能記錄檔的資訊。</span><span class="sxs-lookup"><span data-stu-id="8548e-103">Use the Performance Counters Limit dialog box to limit the information from a System Monitor performance log file when correlating it with a [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace.</span></span> <span data-ttu-id="8548e-104">您可以使用此對話方塊，來選取應該顯示及用於建立相互關聯的計數器。</span><span class="sxs-lookup"><span data-stu-id="8548e-104">You can use this dialog box to select counters that should be displayed and used for correlation.</span></span>  
  
 <span data-ttu-id="8548e-105">**[效能計數器限制]** 對話方塊，會以效能記錄檔所包含的效能物件和計數器來擴展。</span><span class="sxs-lookup"><span data-stu-id="8548e-105">The **Performance Counters Limit** dialog box is populated with the performance objects and counters that the performance log file contains.</span></span>  
  
### <a name="to-select-performance-objects-and-counters-to-correlate-with-a-trace"></a><span data-ttu-id="8548e-106">若要選取效能物件和計數器來建立追蹤的相互關聯</span><span class="sxs-lookup"><span data-stu-id="8548e-106">To select performance objects and counters to correlate with a trace</span></span>  
  
1.  <span data-ttu-id="8548e-107">展開效能物件來查看哪些計數器已包含在效能記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="8548e-107">Expand a performance object to see which counters are included in the performance log file.</span></span>  
  
2.  <span data-ttu-id="8548e-108">核取您要與 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 追蹤檔建立相互關聯的計數器。</span><span class="sxs-lookup"><span data-stu-id="8548e-108">Check the counters that you want to correlate with the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace file.</span></span>  
  
     <span data-ttu-id="8548e-109">如果您要選取效能物件的所有計數器，請核取該效能物件相鄰的方塊。</span><span class="sxs-lookup"><span data-stu-id="8548e-109">If you want to select all counters for a performance object, check the box that is adjacent to the performance object.</span></span> <span data-ttu-id="8548e-110">核取最頂端的節點 (指出電腦)，就會選取效能記錄檔中所包含的所有效能物件和計數器。</span><span class="sxs-lookup"><span data-stu-id="8548e-110">Checking the topmost node, which indicates the computer, selects all performance objects and counters contained in the performance log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8548e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8548e-111">See Also</span></span>  
 [<span data-ttu-id="8548e-112">使追蹤與 Windows 效能記錄資料產生相互關聯 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="8548e-112">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)  
  
  
