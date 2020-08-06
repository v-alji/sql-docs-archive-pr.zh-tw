---
title: 追蹤屬性 (事件選取範圍索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.traceproperties.eventsselection.f1
helpviewer_keywords:
- Trace Properties dialog box
ms.assetid: e1892f24-7272-4d5d-8926-6150cc82b2c3
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11f4725865d39c21e36f5fd09eaf2afd4cde3017
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703230"
---
# <a name="trace-properties-events-selection-tab"></a><span data-ttu-id="575dd-102">追蹤屬性 (事件選取範圍索引標籤)</span><span class="sxs-lookup"><span data-stu-id="575dd-102">Trace Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="575dd-103">使用 **[追蹤屬性]** 對話方塊的 **[事件選取範圍]** 索引標籤，來檢視或指定追蹤的事件和資料行。</span><span class="sxs-lookup"><span data-stu-id="575dd-103">Use the **Events Selection** tab of the **Trace Properties** dialog box to view or specify traced events and data columns.</span></span>  
  
## <a name="options"></a><span data-ttu-id="575dd-104">選項</span><span class="sxs-lookup"><span data-stu-id="575dd-104">Options</span></span>  
 <span data-ttu-id="575dd-105">[事件]\*\*\*\* 資料行</span><span class="sxs-lookup"><span data-stu-id="575dd-105">**Events** column</span></span>  
 <span data-ttu-id="575dd-106">選取或清除事件資料行中的核取方塊，來指定追蹤的事件。</span><span class="sxs-lookup"><span data-stu-id="575dd-106">Specify traced events by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="575dd-107">依事件類別目錄所組織的**事件** 。</span><span class="sxs-lookup"><span data-stu-id="575dd-107">**Events** are organized by event category.</span></span> <span data-ttu-id="575dd-108">範本中所指定的事件類別會自動選取。</span><span class="sxs-lookup"><span data-stu-id="575dd-108">Event classes specified in the template are automatically selected.</span></span> <span data-ttu-id="575dd-109">如需詳細資訊，請參閱 [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="575dd-109">For more information, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="575dd-110">資料行</span><span class="sxs-lookup"><span data-stu-id="575dd-110">Data columns</span></span>  
 <span data-ttu-id="575dd-111">核取對應到所需事件和資料行的方塊，來指定追蹤的資料行。</span><span class="sxs-lookup"><span data-stu-id="575dd-111">Specify traced data columns by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="575dd-112">依預設，針對追蹤內所包含的每個事件，都會核取所有相關的事件資料行。</span><span class="sxs-lookup"><span data-stu-id="575dd-112">All relevant event columns are checked by default for each event included in the trace.</span></span>  
  
 <span data-ttu-id="575dd-113">按一下資料行標頭並輸入篩選準則，即可指定篩選。</span><span class="sxs-lookup"><span data-stu-id="575dd-113">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="575dd-114">篩選的資料行在 **[編輯篩選]** 對話方塊中，會以資料行標籤左方的篩選圖示指出。</span><span class="sxs-lookup"><span data-stu-id="575dd-114">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span> <span data-ttu-id="575dd-115">如需詳細資訊，請參閱 [SQL Server Profiler - 編輯篩選](../../2014/database-engine/sql-server-profiler-edit-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="575dd-115">For more information, see [SQL Server Profiler - Edit Filter](../../2014/database-engine/sql-server-profiler-edit-filter.md).</span></span>  
  
 <span data-ttu-id="575dd-116">**顯示所有事件**</span><span class="sxs-lookup"><span data-stu-id="575dd-116">**Show all events**</span></span>  
 <span data-ttu-id="575dd-117">顯示所有可用的事件。</span><span class="sxs-lookup"><span data-stu-id="575dd-117">Show all available events.</span></span> <span data-ttu-id="575dd-118">依預設，僅會顯示在 **[事件選取範圍]** 方格中選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="575dd-118">By default, only rows in the **Events Selection** grid that are selected display.</span></span> <span data-ttu-id="575dd-119">取消選取此方塊，即可隱藏 **[事件選取範圍]** 方格中所有未選取的事件。</span><span class="sxs-lookup"><span data-stu-id="575dd-119">Uncheck this box to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="575dd-120">**顯示所有資料行**</span><span class="sxs-lookup"><span data-stu-id="575dd-120">**Show all columns**</span></span>  
 <span data-ttu-id="575dd-121">顯示所有可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="575dd-121">Show all available data columns.</span></span> <span data-ttu-id="575dd-122">依預設，僅會顯示選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="575dd-122">By default, only data columns that are selected display.</span></span> <span data-ttu-id="575dd-123">取消選取此方塊，即可隱藏 **[事件選取範圍]** 方格中所有未選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="575dd-123">Uncheck this box to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="575dd-124">**資料行篩選**</span><span class="sxs-lookup"><span data-stu-id="575dd-124">**Column Filters**</span></span>  
 <span data-ttu-id="575dd-125">啟動 [編輯篩選]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="575dd-125">Launches the **Edit Filter** dialog box.</span></span> <span data-ttu-id="575dd-126">您可以使用此對話來編輯資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="575dd-126">You can use this dialog to edit data column filters.</span></span>  
  
 <span data-ttu-id="575dd-127">**組織資料行**</span><span class="sxs-lookup"><span data-stu-id="575dd-127">**Organize Columns**</span></span>  
 <span data-ttu-id="575dd-128">變更追蹤中資料行的順序，並且依據一或多個資料行對結果進行分組。</span><span class="sxs-lookup"><span data-stu-id="575dd-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575dd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="575dd-129">See Also</span></span>  
 <span data-ttu-id="575dd-130">[指定追蹤檔案的事件和資料行 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="575dd-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="575dd-131">[組織追蹤中所顯示的資料行 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="575dd-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="575dd-132">[篩選追蹤中的事件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="575dd-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="575dd-133">[視圖篩選資訊 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="575dd-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="575dd-134">[修改篩選 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="575dd-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="575dd-135">[SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="575dd-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="575dd-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="575dd-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
