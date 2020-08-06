---
title: 根據事件結束時間篩選事件 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- event end times [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 74628f9e-2d39-496a-a443-0a3887db223d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d25d8e1adbd95f48d88fd1516c48dcc0f8374a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708850"
---
# <a name="filter-events-based-on-the-event-end-time-sql-server-profiler"></a><span data-ttu-id="13cf4-102">根據事件結束時間篩選事件 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="13cf4-102">Filter Events Based on the Event End Time (SQL Server Profiler)</span></span>
  <span data-ttu-id="13cf4-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]根據事件結束時間篩選追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="13cf4-103">This topic describes how to filter trace events based on the event ending time by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-filter-events-based-on-the-event-end-time"></a><span data-ttu-id="13cf4-104">若要根據事件結束時間篩選事件</span><span class="sxs-lookup"><span data-stu-id="13cf4-104">To filter events based on the event end time</span></span>  
  
1.  <span data-ttu-id="13cf4-105">在 [檔案]  功能表上，按一下 [新增追蹤]  ，接著連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="13cf4-105">On the **File** menu, click **New Trace**, and then connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="13cf4-106">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="13cf4-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13cf4-107">如果選取 [進行連接後立即啟動追蹤]  ，將不會顯示 [追蹤屬性]  對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="13cf4-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="13cf4-108">於 [工具]  功能表，按一下 [選項]  ，並清除 [連接後立即啟動追蹤]  核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="13cf4-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="13cf4-109">在 [追蹤屬性]  對話方塊中，請確定已選取 [一般]  索引標籤，並在 [追蹤名稱]  文字方塊中輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="13cf4-109">In the **Trace Properties** dialog box, make sure the **General** tab is selected, and enter a name in the **TraceName** text box.</span></span>  
  
3.  <span data-ttu-id="13cf4-110">在 [使用範本]  清單中，選取追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="13cf4-110">From the **Use the template**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="13cf4-111">選擇性，指定要儲存追蹤結果的目的地檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="13cf4-111">Optionally, specify a destination file or table in which to save the trace results.</span></span>  
  
5.  <span data-ttu-id="13cf4-112">在 [事件選取範圍]  索引標籤上，按一下 [結束時間]  資料行，以啟動 [編輯篩選]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="13cf4-112">On the **Events Selection**tab, click the **EndTime** data column to launch the **Edit Filter** dialog box.</span></span> <span data-ttu-id="13cf4-113">您也可以用滑鼠右鍵按一下資料行標題，然後選取 [編輯資料行篩選]  。</span><span class="sxs-lookup"><span data-stu-id="13cf4-113">You can also right-click the column heading, and select **Edit Column Filter**.</span></span>  
  
6.  <span data-ttu-id="13cf4-114">展開 [**大於**] 或 [**小於**]，然後 `datetime` 在比較運算子下方出現的欄位中輸入值。</span><span class="sxs-lookup"><span data-stu-id="13cf4-114">Expand **Greater than** or **Less than**, and enter a `datetime`value in the field that appears beneath the comparison operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13cf4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13cf4-115">See Also</span></span>  
 <span data-ttu-id="13cf4-116">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="13cf4-116">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="13cf4-117">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="13cf4-117">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
