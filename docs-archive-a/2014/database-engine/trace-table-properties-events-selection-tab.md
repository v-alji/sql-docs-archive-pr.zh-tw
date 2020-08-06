---
title: 追蹤資料表屬性 (事件選取範圍索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetableproperties.eventsselection.f1
helpviewer_keywords:
- Trace Table Properties dialog box
ms.assetid: fa21df6a-b6b5-4b15-9104-957385821594
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2e72f299c9d83762876ce250f750924430ba2f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708570"
---
# <a name="trace-table-properties-events-selection-tab"></a><span data-ttu-id="738a0-102">追蹤資料表屬性 (事件選取範圍索引標籤)</span><span class="sxs-lookup"><span data-stu-id="738a0-102">Trace Table Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="738a0-103">使用 **[追蹤資料表屬性]** 對話方塊的 **[事件選取範圍]** 索引標籤，即可檢視追蹤的事件和資料行屬性，或從追蹤中移除事件或資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-103">Use the **Events Selection** tab of the **Trace Table Properties** dialog box to view the events and data column properties of the trace or to remove events or columns from the trace.</span></span>  
  
 <span data-ttu-id="738a0-104">若要檢視此視窗，請使用 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 來開啟追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="738a0-104">To view this window, use [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] to open a trace table.</span></span> <span data-ttu-id="738a0-105">在 [檔案] 功能表上，**按一下 [** **屬性**]，然後按一下 [**事件選取範圍**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="738a0-105">Then on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="738a0-106">選項</span><span class="sxs-lookup"><span data-stu-id="738a0-106">Options</span></span>  
 <span data-ttu-id="738a0-107">[事件]\*\*\*\* 資料行</span><span class="sxs-lookup"><span data-stu-id="738a0-107">**Events** column</span></span>  
 <span data-ttu-id="738a0-108">檢視依事件類別目錄所組織的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="738a0-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="738a0-109">勾選方塊或勾選事件的資料行即可選取事件。</span><span class="sxs-lookup"><span data-stu-id="738a0-109">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="738a0-110">如果勾選事件方塊，就會選取所有適用於該事件的資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-110">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="738a0-111">如果勾選事件的資料行，就會勾選事件，也會自動勾選任何其他必要的資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-111">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="738a0-112">如果您正在檢視追蹤檔案或資料表，清除事件或資料行的核取方塊會減少追蹤視窗中的可見資料量，以便進行分析。</span><span class="sxs-lookup"><span data-stu-id="738a0-112">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="738a0-113">您也可以變更資料行篩選，來減少追蹤視窗中的可見資料量。</span><span class="sxs-lookup"><span data-stu-id="738a0-113">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="738a0-114">如需有關事件類別的詳細資訊，請參閱＜ [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)＞。</span><span class="sxs-lookup"><span data-stu-id="738a0-114">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="738a0-115">其他資料行</span><span class="sxs-lookup"><span data-stu-id="738a0-115">Other data columns</span></span>  
 <span data-ttu-id="738a0-116">檢視追蹤的資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-116">View traced data columns.</span></span> <span data-ttu-id="738a0-117">依預設，針對追蹤內所包含的每個事件，都會勾選追蹤內的所有相關資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-117">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="738a0-118">按一下資料行標頭並輸入篩選準則，即可指定篩選。</span><span class="sxs-lookup"><span data-stu-id="738a0-118">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="738a0-119">篩選的資料行在 **[編輯篩選]** 對話方塊中，會以資料行標籤左方的篩選圖示指出。</span><span class="sxs-lookup"><span data-stu-id="738a0-119">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="738a0-120">**顯示所有事件**</span><span class="sxs-lookup"><span data-stu-id="738a0-120">**Show all events**</span></span>  
 <span data-ttu-id="738a0-121">顯示所有可用的事件。</span><span class="sxs-lookup"><span data-stu-id="738a0-121">Show all available events.</span></span> <span data-ttu-id="738a0-122">依預設，僅會顯示在 **[事件選取範圍]** 方格中選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="738a0-122">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="738a0-123">取消選取此方塊，即可隱藏 **[事件選取範圍]** 方格中所有未選取的事件。</span><span class="sxs-lookup"><span data-stu-id="738a0-123">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="738a0-124">如果勾選 **[顯示所有事件]** 而且您正在檢視追蹤檔案或資料表，在追蹤內記錄的所有事件就會顯示在追蹤視窗中。</span><span class="sxs-lookup"><span data-stu-id="738a0-124">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="738a0-125">**顯示所有資料行**</span><span class="sxs-lookup"><span data-stu-id="738a0-125">**Show all columns**</span></span>  
 <span data-ttu-id="738a0-126">顯示所有可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-126">Show all available data columns.</span></span> <span data-ttu-id="738a0-127">依預設，僅會顯示選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-127">By default, only data columns that are selected display.</span></span> <span data-ttu-id="738a0-128">取消選取此方塊，即可隱藏 **[事件選取範圍]** 方格中所有未選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-128">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="738a0-129">**資料行篩選**</span><span class="sxs-lookup"><span data-stu-id="738a0-129">**Column Filters**</span></span>  
 <span data-ttu-id="738a0-130">啟動 [編輯篩選]\*\*\*\* 對話方塊，其中在資料行標籤左方會顯示篩選圖示。</span><span class="sxs-lookup"><span data-stu-id="738a0-130">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label.</span></span> <span data-ttu-id="738a0-131">您可以使用此對話方塊來編輯資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="738a0-131">You can use this dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="738a0-132">**組織資料行**</span><span class="sxs-lookup"><span data-stu-id="738a0-132">**Organize Columns**</span></span>  
 <span data-ttu-id="738a0-133">選取要追蹤的 [事件]\*\*\*\* 和資料行之後，按一下 [組織資料行]\*\*\*\* 即可強制方格重新排序追蹤結果視窗中的資料行。</span><span class="sxs-lookup"><span data-stu-id="738a0-133">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738a0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="738a0-134">See Also</span></span>  
 <span data-ttu-id="738a0-135">[開啟追蹤資料表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="738a0-135">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="738a0-136">[SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="738a0-136">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="738a0-137">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="738a0-137">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
