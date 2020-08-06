---
title: 追蹤檔案屬性 (事件選取範圍索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracefileproperties.eventsselection.f1
helpviewer_keywords:
- Trace File Properties dialog box
ms.assetid: 158d442f-2225-4173-8545-fb1cf611b4d0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: abfadc2b1df4cda039d7e413e5ba0c7777e7c04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703233"
---
# <a name="trace-file-properties-events-selection-tab"></a><span data-ttu-id="7a158-102">追蹤檔案屬性 (事件選取範圍索引標籤)</span><span class="sxs-lookup"><span data-stu-id="7a158-102">Trace File Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="7a158-103">使用 **[追蹤檔案範本屬性]** 對話方塊的 **[事件選取範圍]** 索引標籤，以檢視追蹤的資料行屬性，或者從追蹤移除資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-103">Use the **Events Selection** tab of the **Trace File Template Properties** dialog box to view the column properties of the trace or remove data columns from the trace.</span></span>  
  
 <span data-ttu-id="7a158-104">若要檢視此視窗，請開啟追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="7a158-104">To view this window, open a trace file.</span></span> <span data-ttu-id="7a158-105">接著在 **[檔案]** 功能表上，按一下 **[屬性]**，然後按一下 **[事件選取範圍]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7a158-105">Then, on the **File** menu, click **Properties**, and then click the **Events Selection** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7a158-106">選項</span><span class="sxs-lookup"><span data-stu-id="7a158-106">Options</span></span>  
 <span data-ttu-id="7a158-107">[事件]\*\*\*\* 資料行</span><span class="sxs-lookup"><span data-stu-id="7a158-107">**Events** column</span></span>  
 <span data-ttu-id="7a158-108">檢視依事件類別目錄所組織的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="7a158-108">View traced events which are organized by event category.</span></span> <span data-ttu-id="7a158-109">起初會選取追蹤內的所有事件。</span><span class="sxs-lookup"><span data-stu-id="7a158-109">Initially, all events in the trace are selected.</span></span> <span data-ttu-id="7a158-110">勾選方塊或勾選事件的資料行即可選取事件。</span><span class="sxs-lookup"><span data-stu-id="7a158-110">Events can be selected by checking the box or by checking a data column for an event.</span></span> <span data-ttu-id="7a158-111">如果勾選事件方塊，就會選取所有適用於該事件的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-111">If the event box is checked, all data columns available for that event are selected.</span></span> <span data-ttu-id="7a158-112">如果勾選事件的資料行，就會勾選事件，也會自動勾選任何其他必要的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-112">If the data column for an event is checked, the event is checked and any other required column is also automatically checked.</span></span> <span data-ttu-id="7a158-113">如果您正在檢視追蹤檔案或資料表，清除事件或資料行的核取方塊會減少追蹤視窗中的可見資料量，以便進行分析。</span><span class="sxs-lookup"><span data-stu-id="7a158-113">If you are viewing a trace file or table, clearing check boxes for events or data columns reduces the amount of visible data in the trace window for easier analysis.</span></span> <span data-ttu-id="7a158-114">您也可以變更資料行篩選，來減少追蹤視窗中的可見資料量。</span><span class="sxs-lookup"><span data-stu-id="7a158-114">You can also change column filters to reduce the amount of visible data in the trace window.</span></span> <span data-ttu-id="7a158-115">如需有關事件類別的詳細資訊，請參閱＜ [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)＞。</span><span class="sxs-lookup"><span data-stu-id="7a158-115">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="7a158-116">資料行</span><span class="sxs-lookup"><span data-stu-id="7a158-116">Data Columns</span></span>  
 <span data-ttu-id="7a158-117">檢視追蹤的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-117">View traced data columns.</span></span> <span data-ttu-id="7a158-118">依預設，針對追蹤內所包含的每個事件，都會勾選追蹤內的所有相關資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-118">All relevant data columns in the trace are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="7a158-119">按一下資料行標頭並輸入篩選準則，即可指定篩選。</span><span class="sxs-lookup"><span data-stu-id="7a158-119">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="7a158-120">篩選的資料行在 **[編輯篩選]** 對話方塊中，會以資料行標籤左方的篩選圖示指出。</span><span class="sxs-lookup"><span data-stu-id="7a158-120">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="7a158-121">**顯示所有事件**</span><span class="sxs-lookup"><span data-stu-id="7a158-121">**Show all events**</span></span>  
 <span data-ttu-id="7a158-122">顯示所有可用的事件。</span><span class="sxs-lookup"><span data-stu-id="7a158-122">Show all available events.</span></span> <span data-ttu-id="7a158-123">依預設，僅會顯示在 **[事件選取範圍]** 方格中選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="7a158-123">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="7a158-124">取消選取此方塊，即可隱藏 **[事件選取範圍]** 方格中所有未選取的事件。</span><span class="sxs-lookup"><span data-stu-id="7a158-124">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span> <span data-ttu-id="7a158-125">如果勾選 **[顯示所有事件]** 而且您正在檢視追蹤檔案或資料表，在追蹤內記錄的所有事件就會顯示在追蹤視窗中。</span><span class="sxs-lookup"><span data-stu-id="7a158-125">If **Show all events** is checked and you are viewing a trace file or table, all events that were recorded in the trace display in the trace window.</span></span>  
  
 <span data-ttu-id="7a158-126">**顯示所有資料行**</span><span class="sxs-lookup"><span data-stu-id="7a158-126">**Show all columns**</span></span>  
 <span data-ttu-id="7a158-127">顯示所有可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-127">Show all available data columns.</span></span> <span data-ttu-id="7a158-128">依預設，僅會顯示選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-128">By default, only data columns that are selected display.</span></span> <span data-ttu-id="7a158-129">取消選取此方塊，即可隱藏 **[事件選取範圍]** 方格中所有未選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-129">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="7a158-130">**資料行篩選**</span><span class="sxs-lookup"><span data-stu-id="7a158-130">**Column Filters**</span></span>  
 <span data-ttu-id="7a158-131">啟動 [編輯篩選]\*\*\*\* 對話方塊，會在資料行標籤左方顯示篩選圖示，以便篩選資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-131">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the column label for filtered data columns.</span></span> <span data-ttu-id="7a158-132">使用 **[編輯篩選]** 對話方塊，即可編輯資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="7a158-132">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="7a158-133">**組織資料行**</span><span class="sxs-lookup"><span data-stu-id="7a158-133">**Organize Columns**</span></span>  
 <span data-ttu-id="7a158-134">選取要追蹤的 [事件]\*\*\*\* 和資料行之後，按一下 [組織資料行]\*\*\*\* 即可強制方格重新排序追蹤結果視窗中的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a158-134">After selecting **Events** and data columns to trace, click **Organize Columns** to force the grid to reorder the column in the trace results window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a158-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a158-135">See Also</span></span>  
 <span data-ttu-id="7a158-136">[指定追蹤檔案的事件和資料行 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7a158-136">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7a158-137">[篩選追蹤中的事件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7a158-137">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7a158-138">[視圖篩選資訊 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7a158-138">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7a158-139">[修改篩選 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7a158-139">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="7a158-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="7a158-140">[SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="7a158-141">SQL Server Profiler 範本和權限</span><span class="sxs-lookup"><span data-stu-id="7a158-141">SQL Server Profiler Templates and Permissions</span></span>](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)  
  
  
