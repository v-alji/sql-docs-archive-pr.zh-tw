---
title: SQL Server Profiler-組織資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.organize.columns.f1
ms.assetid: bf5674f4-da5e-43f9-aeb2-76ca37993790
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b63c2f7d882bac05fc6baf10614170ec23125c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705389"
---
# <a name="sql-server-profiler---organize-columns"></a><span data-ttu-id="f761a-102">SQL Server Profiler - 組織資料行</span><span class="sxs-lookup"><span data-stu-id="f761a-102">SQL Server Profiler - Organize Columns</span></span>
  <span data-ttu-id="f761a-103">使用 **[組織資料行]** 對話方塊來選取在追蹤中所顯示的群組或彙總事件的資料行，讓您易於檢視和分析大型追蹤檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="f761a-103">Use the **Organize Columns** dialog box to select data columns for grouping or aggregating events that are displayed in a trace, which makes large trace files or tables easier to view and analyze.</span></span>  
  
 <span data-ttu-id="f761a-104">彙總會移動和摺疊在追蹤中的各事件類別類型之下的所有事件。</span><span class="sxs-lookup"><span data-stu-id="f761a-104">Aggregating moves and collapses all events in the trace under its respective event class type.</span></span> <span data-ttu-id="f761a-105">**+** 事件類別名稱的左邊會出現一個加號 () 。</span><span class="sxs-lookup"><span data-stu-id="f761a-105">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="f761a-106">按一下加號會展開事件類別，使您可以檢視該類型的所有事件。</span><span class="sxs-lookup"><span data-stu-id="f761a-106">Clicking the plus sign expands the event class so you can view all events of that type.</span></span>  
  
 <span data-ttu-id="f761a-107">群組會將特定類型的所有事件類別，組織在一起並顯示在追蹤視窗中。</span><span class="sxs-lookup"><span data-stu-id="f761a-107">Grouping organizes all event classes of a specific type together in the trace window display.</span></span> <span data-ttu-id="f761a-108">不過，事件並不會摺疊在事件類別類型之下。</span><span class="sxs-lookup"><span data-stu-id="f761a-108">However, the events are not collapsed under the event class type.</span></span>  
  
 <span data-ttu-id="f761a-109">當您群組或彙總追蹤視窗顯示中的事件時，針對要進行群組或彙總所選取的資料行會固定地顯示在視窗中，但是您可以向左或向右捲動，以檢視所有其他資料行。</span><span class="sxs-lookup"><span data-stu-id="f761a-109">When you group or aggregate events in a trace window display, the columns selected for grouping or aggregating remain fixed in the display window, but you can scroll to the right or left to view all other data columns.</span></span>  
  
 <span data-ttu-id="f761a-110">若要存取此對話方塊，請開啟現有的追蹤檔案或資料表，然後按一下  [檔案][!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] \*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f761a-110">To access this dialog box, open an existing trace file or table, and click **Properties** on the [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] **File** menu.</span></span> <span data-ttu-id="f761a-111">在 **[追蹤屬性]** 對話方塊中，按一下 **[事件選取範圍]** 索引標籤，然後按一下 **[組織資料行]**。</span><span class="sxs-lookup"><span data-stu-id="f761a-111">In the **Trace Properties** dialog box, click the **Events Selection** tab, and then click **Organize Columns**.</span></span> <span data-ttu-id="f761a-112">在建立新的追蹤時，您也可以按一下 **[事件選取範圍]** 索引標籤上的 **[組織資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="f761a-112">You can also click **Organize Columns** on the **Events Selection** tab when you are creating a new trace.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f761a-113">選項</span><span class="sxs-lookup"><span data-stu-id="f761a-113">Options</span></span>  
 <span data-ttu-id="f761a-114">**群組**</span><span class="sxs-lookup"><span data-stu-id="f761a-114">**Groups**</span></span>  
 <span data-ttu-id="f761a-115">將 [群組]\*\*\*\* 之下的資料行名稱移至追蹤視窗中的群組或彙總事件類別。</span><span class="sxs-lookup"><span data-stu-id="f761a-115">Move data column names under **Groups** to group or aggregate event classes in the trace window.</span></span>  
  
 <span data-ttu-id="f761a-116">若要彙總事件，請將一個資料行移至 **[群組]**。</span><span class="sxs-lookup"><span data-stu-id="f761a-116">To aggregate events, move one data column into **Groups**.</span></span> <span data-ttu-id="f761a-117">這會使特定類型的所有事件，都摺疊在追蹤視窗顯示中的事件類別類型名稱之下。</span><span class="sxs-lookup"><span data-stu-id="f761a-117">This causes all events of a specific type to be collapsed under event class type name in the trace window display.</span></span> <span data-ttu-id="f761a-118">**+** 事件類別名稱的左邊會出現一個加號 () 。</span><span class="sxs-lookup"><span data-stu-id="f761a-118">A plus sign (**+**) appears to the left of the event class name.</span></span> <span data-ttu-id="f761a-119">按一下加號即可展開事件類別類型並檢視所有事件。</span><span class="sxs-lookup"><span data-stu-id="f761a-119">Click the plus sign to expand the event class type and view all events.</span></span> <span data-ttu-id="f761a-120">按一下 **[檢視]** 功能表上的 **[彙總檢視]** 或 **[群組檢視]** ，您可以設定開啟或關閉彙總和群組。</span><span class="sxs-lookup"><span data-stu-id="f761a-120">You can set aggregation and grouping on and off by clicking **Aggregated View** or **Grouped View** on the **View** menu.</span></span>  
  
 <span data-ttu-id="f761a-121">若要群組事件，請將多個資料行移至 **[群組]**。</span><span class="sxs-lookup"><span data-stu-id="f761a-121">To group events, move more than one data column into **Groups**.</span></span> <span data-ttu-id="f761a-122">這會使特定類型的所有事件群組在追蹤視窗顯示中，但是不會將事件摺疊在每個事件類別類型名稱之下。</span><span class="sxs-lookup"><span data-stu-id="f761a-122">This causes all events of a specific type to be grouped together in the trace window display, but does not collapse the events under each event class type name.</span></span> <span data-ttu-id="f761a-123">按一下 [檢視] 功能表上的 **[群組檢視]** ，您可以在群組檢視和非群組檢視之間來回切換。</span><span class="sxs-lookup"><span data-stu-id="f761a-123">You can switch back and forth between a grouped view and an ungrouped view by clicking **Grouped View** on the View menu.</span></span> <span data-ttu-id="f761a-124">當多個資料行移至 **[群組]** 時，不能使用切換至 **[彙總檢視]** 的選項。</span><span class="sxs-lookup"><span data-stu-id="f761a-124">When more than one data column is moved into **Groups**, the option to switch to **Aggregated View** is not available.</span></span>  
  
 <span data-ttu-id="f761a-125">**資料行**</span><span class="sxs-lookup"><span data-stu-id="f761a-125">**Columns**</span></span>  
 <span data-ttu-id="f761a-126">可移至 [群組]\*\*\*\* 的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="f761a-126">List of data columns available to move into **Groups**.</span></span> <span data-ttu-id="f761a-127">按一下 [資料行] 左邊的加號 (**+**) **Columns**以展開清單。</span><span class="sxs-lookup"><span data-stu-id="f761a-127">Click the plus sign (**+**) to the left of **Columns** to expand the list.</span></span>  
  
 <span data-ttu-id="f761a-128">**設定**</span><span class="sxs-lookup"><span data-stu-id="f761a-128">**Up**</span></span>  
 <span data-ttu-id="f761a-129">選取資料行之後，按一下 [向上]\*\*\*\* 將資料行向上移至 [群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f761a-129">After selecting a data column, click **Up** to move data columns up into **Groups**.</span></span> <span data-ttu-id="f761a-130">您也可以按一下 **[向上]** ，來重新排列追蹤視窗所顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="f761a-130">You can also click **Up** to rearrange the display of columns in the trace window display.</span></span>  
  
 <span data-ttu-id="f761a-131">**Down**</span><span class="sxs-lookup"><span data-stu-id="f761a-131">**Down**</span></span>  
 <span data-ttu-id="f761a-132">選取資料行之後，按一下 [向下]\*\*\*\* 將資料行從 [群組]\*\*\*\* 中移出。</span><span class="sxs-lookup"><span data-stu-id="f761a-132">After selecting a data column, click **Down** to move data columns out of **Groups**.</span></span> <span data-ttu-id="f761a-133">您也可以按一下 **[向下]** ，來重新排列追蹤視窗所顯示的資料行。</span><span class="sxs-lookup"><span data-stu-id="f761a-133">You can also click **Down** to rearrange the display of columns in the trace window display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f761a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f761a-134">See Also</span></span>  
 <span data-ttu-id="f761a-135">[組織追蹤中所顯示的資料行 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f761a-135">[Organize Columns Displayed in a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="f761a-136">[建立追蹤 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f761a-136">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="f761a-137">[建立追蹤範本 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f761a-137">[Create a Trace Template &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="f761a-138">[開啟追蹤檔案 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="f761a-138">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="f761a-139">開啟追蹤資料表 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="f761a-139">Open a Trace Table &#40;SQL Server Profiler&#41;</span></span>](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)  
  
  
