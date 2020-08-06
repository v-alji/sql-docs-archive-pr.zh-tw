---
title: 追蹤範本屬性 (事件選取範圍索引標籤) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.tracetemplateproperties.eventsselection.f1
helpviewer_keywords:
- Trace Template Properties dialog box
ms.assetid: 5b202457-ab42-4902-8012-7f3f40aa09f5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: da497db6e9373c63836753dc2be96deb3ce90244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707769"
---
# <a name="trace-template-properties-events-selection-tab"></a><span data-ttu-id="95e37-102">追蹤範本屬性 (事件選取範圍索引標籤)</span><span class="sxs-lookup"><span data-stu-id="95e37-102">Trace Template Properties (Events Selection Tab)</span></span>
  <span data-ttu-id="95e37-103">使用 **[追蹤範本屬性]** 對話方塊的 **[事件選取範圍]** 索引標籤，來檢視、編輯或指定要包含在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 追蹤範本中的事件類別和資料行。</span><span class="sxs-lookup"><span data-stu-id="95e37-103">Use the **Events Selection** tab of the **Trace Template Properties** dialog box to view, edit, or specify event classes and data columns to include in a [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace template.</span></span>  
  
## <a name="options"></a><span data-ttu-id="95e37-104">選項</span><span class="sxs-lookup"><span data-stu-id="95e37-104">Options</span></span>  
 <span data-ttu-id="95e37-105">[事件]\*\*\*\* 資料行</span><span class="sxs-lookup"><span data-stu-id="95e37-105">**Events** column</span></span>  
 <span data-ttu-id="95e37-106">選取或清除事件資料行中的核取方塊，來指定應追蹤的事件。</span><span class="sxs-lookup"><span data-stu-id="95e37-106">Specify events that should be traced by selecting or clearing the check box in the event column.</span></span> <span data-ttu-id="95e37-107">依事件類別目錄所組織的事件。</span><span class="sxs-lookup"><span data-stu-id="95e37-107">Events are organized by event category.</span></span>  
  
 <span data-ttu-id="95e37-108">如果選取 **[一般]** 索引標籤上的 **[以現有的範本作為新範本的基礎]** ，就會根據指定的範本自動選取事件。</span><span class="sxs-lookup"><span data-stu-id="95e37-108">If you selected **Base new template on existing one** on the **General** tab, events are automatically selected according to the specified template.</span></span> <span data-ttu-id="95e37-109">如需有關事件類別的詳細資訊，請參閱＜ [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md)＞。</span><span class="sxs-lookup"><span data-stu-id="95e37-109">For more information about event classes, see [SQL Server Event Class Reference](../relational-databases/event-classes/sql-server-event-class-reference.md).</span></span>  
  
 <span data-ttu-id="95e37-110">資料行</span><span class="sxs-lookup"><span data-stu-id="95e37-110">Data columns</span></span>  
 <span data-ttu-id="95e37-111">勾選對應到所需事件和資料行的方塊，來指定應追蹤的資料行。</span><span class="sxs-lookup"><span data-stu-id="95e37-111">Specify data columns that should be traced by checking the box that corresponds with the event and the data column you need.</span></span> <span data-ttu-id="95e37-112">依預設，如果已勾選對應到事件的核取方塊，追蹤所包含之每個事件的所有相關事件資料行也都會被勾選。</span><span class="sxs-lookup"><span data-stu-id="95e37-112">All relevant event columns are checked by default for each event included in the trace, if the checkbox corresponding to the event is checked.</span></span> <span data-ttu-id="95e37-113">如果勾選 **[一般]** 索引標籤上的 **[以現有的範本作為新範本的基礎]** ，就會根據指定的範本自動選取資料行和篩選。</span><span class="sxs-lookup"><span data-stu-id="95e37-113">If you checked **Base new template on existing one** on the **General** tab, data columns and filters are automatically selected according to the specified template.</span></span>  
  
 <span data-ttu-id="95e37-114">按一下資料行標頭並輸入篩選準則，即可指定篩選。</span><span class="sxs-lookup"><span data-stu-id="95e37-114">Specify filters by clicking the data column heading and entering the filter criteria.</span></span> <span data-ttu-id="95e37-115">篩選的資料行在 **[編輯篩選]** 對話方塊中，會以資料行標籤左方的篩選圖示指出。</span><span class="sxs-lookup"><span data-stu-id="95e37-115">Filtered data columns are indicated by a filter icon to the left of the column label in the **Edit Filter** dialog box.</span></span>  
  
 <span data-ttu-id="95e37-116">**顯示所有事件**</span><span class="sxs-lookup"><span data-stu-id="95e37-116">**Show all events**</span></span>  
 <span data-ttu-id="95e37-117">顯示所有可用的事件。</span><span class="sxs-lookup"><span data-stu-id="95e37-117">Show all available events.</span></span> <span data-ttu-id="95e37-118">如果您正在建立一個不是以現有的範本為基礎的新範本，這個選項依預設為核取的。</span><span class="sxs-lookup"><span data-stu-id="95e37-118">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="95e37-119">取消選取以隱藏 **[事件選取範圍]** 方格中所有未選取的事件。</span><span class="sxs-lookup"><span data-stu-id="95e37-119">Uncheck to hide all unselected events in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="95e37-120">**顯示所有資料行**</span><span class="sxs-lookup"><span data-stu-id="95e37-120">**Show all columns**</span></span>  
 <span data-ttu-id="95e37-121">顯示所有可用的資料行。</span><span class="sxs-lookup"><span data-stu-id="95e37-121">Show all available data columns.</span></span> <span data-ttu-id="95e37-122">如果您正在建立一個不是以現有的範本為基礎的新範本，這個選項依預設為核取的。</span><span class="sxs-lookup"><span data-stu-id="95e37-122">This option is checked by default if you are creating a new template that is not based on an existing template.</span></span> <span data-ttu-id="95e37-123">取消選取以隱藏 **[事件選取範圍]** 方格中所有未選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="95e37-123">Uncheck to hide all unselected data columns in the **Events Selection** grid.</span></span>  
  
 <span data-ttu-id="95e37-124">**資料行篩選**</span><span class="sxs-lookup"><span data-stu-id="95e37-124">**Column Filters**</span></span>  
 <span data-ttu-id="95e37-125">啟動 [編輯篩選]\*\*\*\* 對話方塊，它會在資料行標籤的左方顯示篩選圖示。</span><span class="sxs-lookup"><span data-stu-id="95e37-125">Launches the **Edit Filter** dialog box, which displays a filter icon to the left of the data column label.</span></span> <span data-ttu-id="95e37-126">使用 **[編輯篩選]** 對話方塊，即可編輯資料行篩選。</span><span class="sxs-lookup"><span data-stu-id="95e37-126">Use the **Edit Filter** dialog box to edit data column filters.</span></span>  
  
 <span data-ttu-id="95e37-127">**組織資料行**</span><span class="sxs-lookup"><span data-stu-id="95e37-127">**Organize Columns**</span></span>  
 <span data-ttu-id="95e37-128">變更追蹤中資料行的順序，並且依據一或多個資料行對結果進行分組。</span><span class="sxs-lookup"><span data-stu-id="95e37-128">Changes the order of columns in the trace and groups results by one or more columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e37-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95e37-129">See Also</span></span>  
 <span data-ttu-id="95e37-130">[指定追蹤檔案的事件和資料行 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="95e37-130">[Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="95e37-131">[組織追蹤中所顯示的資料行 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="95e37-131">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="95e37-132">[篩選追蹤中的事件 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="95e37-132">[Filter Events in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="95e37-133">[視圖篩選資訊 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="95e37-133">[View Filter Information &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="95e37-134">[修改篩選 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="95e37-134">[Modify a Filter &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="95e37-135">[SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="95e37-135">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="95e37-136">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="95e37-136">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
