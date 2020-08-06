---
title: 根據事件開始時間篩選事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event start times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7f652952ec6706580b876e3e9a20f96e62598f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706926"
---
# <a name="filter-events-based-on-the-event-start-time-sql-server-profiler"></a><span data-ttu-id="c0fae-102">依據事件開始時間篩選事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="c0fae-102">Filter Events Based on the Event Start Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="c0fae-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]，依據事件開始時間來篩選追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="c0fae-103">This topic describes how to filter trace events based on the event start time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-an-event-based-on-the-event-start-time"></a><span data-ttu-id="c0fae-104">若要依據事件開始時間篩選事件</span><span class="sxs-lookup"><span data-stu-id="c0fae-104">To filter an event based on the event start time</span></span>  
  
1.  <span data-ttu-id="c0fae-105">在 [檔案]  功能表上，按一下 [新增追蹤]  ，接著連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0fae-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="c0fae-106">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0fae-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0fae-107">如果選取 [進行連接後立即啟動追蹤]  ，將不會顯示 [追蹤屬性]  對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="c0fae-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear, and the trace begins instead.</span></span> <span data-ttu-id="c0fae-108">於 [工具]  功能表，按一下 [選項]  ，並清除 [連接後立即啟動追蹤]  核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="c0fae-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="c0fae-109">在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0fae-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="c0fae-110">在 [使用範本]  名稱清單中，選取追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="c0fae-110">In the **Use the template**name list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="c0fae-111">選擇性地指定追蹤結果的目的地。</span><span class="sxs-lookup"><span data-stu-id="c0fae-111">Optionally specify a destination for the trace results.</span></span>  
  
5.  <span data-ttu-id="c0fae-112">在 [事件選取範圍]  索引標籤上，按一下 [開始時間]  資料行標題。</span><span class="sxs-lookup"><span data-stu-id="c0fae-112">On the **Events Selection**tab, click the **StartTime** column heading.</span></span> <span data-ttu-id="c0fae-113">您也可以用滑鼠右鍵按一下資料行標題，然後按一下 [編輯資料行篩選]  以啟動 [編輯篩選]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0fae-113">You can also right-click the column heading, and then click **Edit Column Filter** to launch the **Edit Filter** dialog box.</span></span>  
  
6.  <span data-ttu-id="c0fae-114">展開 [**大於**] 或 [**小於**]，然後在 `datetime` 比較運算子下方的欄位中輸入值。</span><span class="sxs-lookup"><span data-stu-id="c0fae-114">Expand **Greater than** or **Less than**, and then enter a `datetime` value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fae-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0fae-115">See Also</span></span>  
 [<span data-ttu-id="c0fae-116">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="c0fae-116">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
