---
title: 指定追蹤檔案的事件及資料行 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- adding events
- traces [SQL Server], data columns
- deleting events
- removing events
- traces [SQL Server], events
ms.assetid: 7da715a3-2f03-4063-b6a4-20fd7b44e675
author: stevestein
ms.author: sstein
ms.openlocfilehash: ffb8639a187f1e7e091e382031886659bd47d7d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584212"
---
# <a name="specify-events-and-data-columns-for-a-trace-file-sql-server-profiler"></a><span data-ttu-id="a6316-102">指定追蹤檔案的事件及資料行 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="a6316-102">Specify Events and Data Columns for a Trace File (SQL Server Profiler)</span></span>
  <span data-ttu-id="a6316-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來指定追蹤的事件類別及資料行。</span><span class="sxs-lookup"><span data-stu-id="a6316-103">This topic describes how to specify event classes and data columns for traces by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-specify-events-and-data-columns-for-a-trace"></a><span data-ttu-id="a6316-104">若要指定追蹤的事件及資料行</span><span class="sxs-lookup"><span data-stu-id="a6316-104">To specify events and data columns for a trace</span></span>  
  
1.  <span data-ttu-id="a6316-105">在 [追蹤屬性]  或 [追蹤範本屬性]  對話方塊上，按一下 [事件選取範圍]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a6316-105">On the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="a6316-106">**[事件選取範圍]** 索引標籤包含方格控制項。</span><span class="sxs-lookup"><span data-stu-id="a6316-106">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="a6316-107">方格控制項是包含每一個可追蹤事件類別的資料表。</span><span class="sxs-lookup"><span data-stu-id="a6316-107">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="a6316-108">資料表針對每個事件類別包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a6316-108">The table contains one row for each event class.</span></span> <span data-ttu-id="a6316-109">依據您所連接之伺服器的類型及版本，事件類別會有些許不同。</span><span class="sxs-lookup"><span data-stu-id="a6316-109">The event classes can differ slightly depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="a6316-110">事件類別在方格的 [事件]  資料行中識別，並依事件類別目錄分組。</span><span class="sxs-lookup"><span data-stu-id="a6316-110">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="a6316-111">其餘資料行會列出可針對每個事件類別傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="a6316-111">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="a6316-112">在 [事件選取範圍]  索引標籤上，使用方格控制項在追蹤檔案中新增或移除事件及資料行。</span><span class="sxs-lookup"><span data-stu-id="a6316-112">On the **Events Selection**tab, use the grid control to add or remove events and data columns from the trace file.</span></span>  
  
3.  <span data-ttu-id="a6316-113">若要將事件從追蹤中移除，請清除每個事件類別之 [事件]  資料行中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a6316-113">To remove events from the trace, clear the check box in the **Events** column for each event class.</span></span>  
  
4.  <span data-ttu-id="a6316-114">若要在追蹤中加入事件，請核取每個事件類別之 [事件]  資料行中的方塊，或是核取對應至事件的資料行。</span><span class="sxs-lookup"><span data-stu-id="a6316-114">To include events in a trace, check the box in the **Events** column for each event class, or check a data column that corresponds to an event.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a6316-115">如果追蹤將會與「系統監視器」或「效能監視器」的資料產生關聯，則 [開始時間]  及 [結束時間]  資料行都必須納入追蹤中。</span><span class="sxs-lookup"><span data-stu-id="a6316-115">If the trace is going be correlated with System Monitor or Performance Monitor data, both **Start Time** and **End Time** data columns must be included in the trace.</span></span>  
  
 <span data-ttu-id="a6316-116">當您納入事件類別時，若有核取事件所對應的方塊，則每個相關聯的資料行也都會納入追蹤中。</span><span class="sxs-lookup"><span data-stu-id="a6316-116">When you include an event class, every associated data column is also included to the trace, if you have checked the box corresponding to an event.</span></span> <span data-ttu-id="a6316-117">若您核取了特定資料行的方塊，就只會將該資料行加入追蹤中。</span><span class="sxs-lookup"><span data-stu-id="a6316-117">If you checked the box for a particular column, only that column is included in the trace.</span></span>  
  
1.  <span data-ttu-id="a6316-118">若要從事件類別中移除資料行，請清除事件類別資料列中資料行的核取方塊，或是以滑鼠右鍵按一下資料行標頭，然後選取 [取消選取資料行]  選項。</span><span class="sxs-lookup"><span data-stu-id="a6316-118">To remove data columns from an event class, clear the check boxes from the data column in the event class row, or right-click on the column header and select the **Deselect column** option.</span></span>  
  
2.  <span data-ttu-id="a6316-119">您可以選擇將篩選套用至追蹤。</span><span class="sxs-lookup"><span data-stu-id="a6316-119">Optionally, apply filters to the trace.</span></span> <span data-ttu-id="a6316-120">如需詳細資訊，請參閱[篩選追蹤中的事件 &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)</span><span class="sxs-lookup"><span data-stu-id="a6316-120">For more information, see [Filter Events in a Trace &#40;SQL Server Profiler&#41;](filter-events-in-a-trace-sql-server-profiler.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6316-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6316-121">See Also</span></span>  
 [<span data-ttu-id="a6316-122">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="a6316-122">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
