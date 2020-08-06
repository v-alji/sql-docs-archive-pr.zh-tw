---
title: 設定追蹤資料表的資料表大小上限 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5f48efbe02e300e06faf857ed0fb36ae340ad979
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686585"
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a><span data-ttu-id="ccd78-102">設定追蹤資料表的資料表大小上限 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="ccd78-102">Set a Maximum Table Size for a Trace Table (SQL Server Profiler)</span></span>
  <span data-ttu-id="ccd78-103">本主題說明如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來設定追蹤資料表的資料表大小上限。</span><span class="sxs-lookup"><span data-stu-id="ccd78-103">This topic describes how to set a maximum table size for trace tables by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a><span data-ttu-id="ccd78-104">若要設定追蹤資料表的大小上限</span><span class="sxs-lookup"><span data-stu-id="ccd78-104">To set a maximum table size for a trace table</span></span>  
  
1.  <span data-ttu-id="ccd78-105">在 **[檔案]** 功能表上按一下 **[新增追蹤]** ，然後連接到 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ccd78-105">On the **File** menu, click **New Trace**, and then connect to an instance of SQL Server.</span></span>  
  
     <span data-ttu-id="ccd78-106">會出現 [追蹤屬性] **[追蹤屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ccd78-106">The **Trace Properties**dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccd78-107">如果選取 [進行連接後立即啟動追蹤]  ，將不會顯示 [追蹤屬性]  對話方塊，而是開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="ccd78-107">If **Start tracing immediately after making connection**is selected, the **Trace Properties**dialog box fails to appear and the trace begins instead.</span></span> <span data-ttu-id="ccd78-108">於 [工具]  功能表，按一下 [選項]  ，並清除 [連接後立即啟動追蹤]  核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="ccd78-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="ccd78-109">在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="ccd78-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="ccd78-110">在 [範本名稱]  清單中，選取追蹤範本。</span><span class="sxs-lookup"><span data-stu-id="ccd78-110">In the **Template name**list, select a trace template.</span></span>  
  
4.  <span data-ttu-id="ccd78-111">選取 [儲存至資料表]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ccd78-111">Select the **Save to table**check box.</span></span>  
  
5.  <span data-ttu-id="ccd78-112">連接到您要儲存追蹤的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ccd78-112">Connect to the server on which you want the trace to be stored.</span></span>  
  
     <span data-ttu-id="ccd78-113">畫面上出現 [目的地資料表]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ccd78-113">The **Destination Table** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="ccd78-114">從 [資料庫]  清單中選取追蹤的資料庫。</span><span class="sxs-lookup"><span data-stu-id="ccd78-114">Select a database for the trace from the **Database** list.</span></span>  
  
7.  <span data-ttu-id="ccd78-115">在 [資料表]  方塊中，輸入或選取資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="ccd78-115">In the **Table** box, type or select a table name.</span></span>  
  
8.  <span data-ttu-id="ccd78-116">選取 [設定最大資料列數]  核取方塊，並指定追蹤資料表的最大資料列數。</span><span class="sxs-lookup"><span data-stu-id="ccd78-116">Select the **Set maximum rows** check box, and specify a maximum number of rows for the trace table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccd78-117">當資料表的資料列數超過您所指定的最大值時，就不會再記錄追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="ccd78-117">When the number of rows in the table exceeds the maximum that you have specified, the trace events are no longer recorded.</span></span> <span data-ttu-id="ccd78-118">不過，仍會繼續追蹤。</span><span class="sxs-lookup"><span data-stu-id="ccd78-118">However, tracing continues.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd78-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccd78-119">See Also</span></span>  
 <span data-ttu-id="ccd78-120">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ccd78-120">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="ccd78-121">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="ccd78-121">SQL Server Profiler</span></span>](sql-server-profiler.md)  
  
  
