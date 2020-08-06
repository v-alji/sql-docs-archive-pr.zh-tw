---
title: 篩選追蹤中的事件 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: fef9dd6956d407011261c54f796a751a0bf94941
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706929"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a><span data-ttu-id="b7e0e-102">篩選追蹤中的事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="b7e0e-102">Filter Events in a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="b7e0e-103">篩選可限制追蹤中收集的事件。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-103">Filters limit the events collected in a trace.</span></span> <span data-ttu-id="b7e0e-104">如果沒有設定篩選條件，選定事件類別的所有事件都會傳回到追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-104">If a filter is not set, all events of the selected event classes are returned in the trace output.</span></span> <span data-ttu-id="b7e0e-105">替追蹤設定篩選並非強制的。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-105">It is not mandatory to set a filter for a trace.</span></span> <span data-ttu-id="b7e0e-106">不過，篩選可以讓追蹤期間造成的負擔降到最低。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-106">However, a filter minimizes the overhead that is incurred during tracing.</span></span>  
  
 <span data-ttu-id="b7e0e-107">使用 **[追蹤屬性]** 或 **[追蹤範本屬性]** 對話方塊的 **[事件選取範圍]** 索引標籤，可以將篩選加入到追蹤定義。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-107">You add filters to trace definitions by using the **Events Selection** tab of the **Trace Properties** or **Trace Template Properties** dialog box.</span></span>  
  
### <a name="to-filter-events-in-a-trace"></a><span data-ttu-id="b7e0e-108">若要篩選追蹤中的事件</span><span class="sxs-lookup"><span data-stu-id="b7e0e-108">To filter events in a trace</span></span>  
  
1.  <span data-ttu-id="b7e0e-109">在 **[追蹤檔案屬性]** 或 **[追蹤資料表屬性]** 對話方塊中，按一下 **[事件選取範圍]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-109">In the **Trace Properties** or **Trace Template Properties** dialog box, click the **Events Selection** tab.</span></span>  
  
     <span data-ttu-id="b7e0e-110">**[事件選取範圍]** 索引標籤包含方格控制項。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-110">The **Events Selection** tab contains a grid control.</span></span> <span data-ttu-id="b7e0e-111">方格控制項是包含每一個可追蹤事件類別的資料表。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-111">The grid control is a table that contains each of the traceable event classes.</span></span> <span data-ttu-id="b7e0e-112">資料表針對每個事件類別包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-112">The table contains one row for each event class.</span></span> <span data-ttu-id="b7e0e-113">事件類別可能會依您所連接的伺服器類型與版本而稍有不同。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-113">The event classes may differ slightly, depending on the type and version of server to which you are connected.</span></span> <span data-ttu-id="b7e0e-114">事件類別在方格的 [事件]\*\*\*\* 資料行中識別，並依事件類別目錄分組。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-114">The event classes are identified in the **Events**column of the grid and are grouped by event category.</span></span> <span data-ttu-id="b7e0e-115">其餘資料行會列出可針對每個事件類別傳回的資料行。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-115">The remaining columns list the data columns that can be returned for each event class.</span></span>  
  
2.  <span data-ttu-id="b7e0e-116">按一下 [資料行篩選]。 </span><span class="sxs-lookup"><span data-stu-id="b7e0e-116">Click **Column Filters.**</span></span>  
  
     <span data-ttu-id="b7e0e-117">[編輯篩選]\*\*\*\* 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-117">The **Edit Filter**dialog box appears.</span></span> <span data-ttu-id="b7e0e-118">您可以使用 [編輯篩選]\*\*\*\* 對話方塊包含的比較運算子清單，篩選追蹤中的事件。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-118">The **Edit Filter**dialog box contains a list of comparison operators that you can use to filter events in a trace.</span></span>  
  
3.  <span data-ttu-id="b7e0e-119">若要套用篩選，請按一下比較運算子，再輸入篩選要用的值。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-119">To apply a filter, click the comparison operator, and type a value to use for the filter.</span></span>  
  
4.  <span data-ttu-id="b7e0e-120">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-120">Click **OK**.</span></span>  
  
 <span data-ttu-id="b7e0e-121">**考量因素：**</span><span class="sxs-lookup"><span data-stu-id="b7e0e-121">**Considerations:**</span></span>  
  
-   <span data-ttu-id="b7e0e-122">如果在 [事件選取範圍] 索引標籤的 **StartTime** 與 **EndTime** 資料行上，設定篩選條件，請確定：</span><span class="sxs-lookup"><span data-stu-id="b7e0e-122">If you set filter conditions on the **StartTime** and **EndTime** data columns of the Events Selection tab, then make sure that:</span></span>  
  
    -   <span data-ttu-id="b7e0e-123">輸入的日期符合以下格式： `YYYY/MM/DD HH:mm:sec`。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-123">The date you enter matches this format: `YYYY/MM/DD HH:mm:sec`.</span></span>  
  
         <span data-ttu-id="b7e0e-124">-或-</span><span class="sxs-lookup"><span data-stu-id="b7e0e-124">-OR-</span></span>  
  
    -   <span data-ttu-id="b7e0e-125">已在 **[一般選項]** 對話方塊中，核取 **[使用地區設定來顯示日期和時間值]** 。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-125">**Use regional settings to display date and time values** is checked in the **General Options** dialog box.</span></span> <span data-ttu-id="b7e0e-126">若要檢視 [一般選項]  對話方塊，請在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [工具]  功能表上，按一下 [選項]  。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-126">To view the **General Options** dialog box, on the [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tools** menu, click **Option**.</span></span>  
  
         <span data-ttu-id="b7e0e-127">-且-</span><span class="sxs-lookup"><span data-stu-id="b7e0e-127">-AND-</span></span>  
  
    -   <span data-ttu-id="b7e0e-128">輸入的日期必須介於 1753 年 1 月 1 日與 9999 年 12 月 31 日。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-128">The date you enter is between January 1, 1753 and December 31, 9999.</span></span>  
  
-   <span data-ttu-id="b7e0e-129">如果從 **osql** 公用程式或 **sqlcmd** 公用程式追蹤事件，對 **%** 資料行篩選時會附加 **%** 。</span><span class="sxs-lookup"><span data-stu-id="b7e0e-129">If tracing events from the **osql** utility or from the **sqlcmd** utility, always append **%** to filters on the **TextData** data column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e0e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7e0e-130">See Also</span></span>  
 [<span data-ttu-id="b7e0e-131">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="b7e0e-131">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
