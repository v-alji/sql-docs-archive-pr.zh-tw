---
title: 建立追蹤 (SQL Server Profiler) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], creating
ms.assetid: 0302fa6d-d2b5-43fe-ad70-7a337575b112
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d73333bbf0ba985ed4952e03584b4e4c130ab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686604"
---
# <a name="create-a-trace-sql-server-profiler"></a><span data-ttu-id="d9fa5-102">建立追蹤 (SQL Server Profiler)</span><span class="sxs-lookup"><span data-stu-id="d9fa5-102">Create a Trace (SQL Server Profiler)</span></span>
  <span data-ttu-id="d9fa5-103">此主題描述如何使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來建立追蹤。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-103">This topic describes how to use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create a trace.</span></span>  
  
### <a name="to-create-a-trace"></a><span data-ttu-id="d9fa5-104">若要建立追蹤</span><span class="sxs-lookup"><span data-stu-id="d9fa5-104">To create a trace</span></span>  
  
1.  <span data-ttu-id="d9fa5-105">在 **[檔案]** 功能表上，按一下 **[新增追蹤]** ，並連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-105">On the **File** menu, click **New Trace**, and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="d9fa5-106">會出現 [追蹤屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-106">The **Trace Properties** dialog box appears.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d9fa5-107">**[追蹤屬性]** 對話方塊無法顯示，但若已選取 **[進行連接後立即啟動追蹤]** ，便會開始追蹤。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-107">The **Trace Properties** dialog box fails to appear, and the trace begins instead, if **Start tracing immediately after making connection** is selected.</span></span> <span data-ttu-id="d9fa5-108">於 [工具] 功能表，按一下 [選項]，並清除 [連接後立即啟動追蹤] 核取方塊，以關閉這項設定。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-108">To turn off this setting, on the **Tools**menu, click **Options**, and clear the **Start tracing immediately after making connection** check box.</span></span>  
  
2.  <span data-ttu-id="d9fa5-109">在 **[追蹤名稱]** 方塊中，輸入追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-109">In the **Trace name** box, type a name for the trace.</span></span>  
  
3.  <span data-ttu-id="d9fa5-110">在 **[使用範本]** 清單中，選取追蹤使用為基礎的追蹤範本；若不想要使用範本，請選取 **[空白]** 。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-110">In the **Use the template** list, select a trace template on which to base the trace, or select **Blank** if you do not want to use a template.</span></span>  
  
4.  <span data-ttu-id="d9fa5-111">若要儲存追蹤結果，請執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="d9fa5-111">To save the trace results, do one of the following:</span></span>  
  
    -   <span data-ttu-id="d9fa5-112">按一下 [儲存至檔案]\*\*\*\*，將追蹤擷取至檔案。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-112">Click **Save to file**to capture the trace to a file.</span></span> <span data-ttu-id="d9fa5-113">在 **[設定最大檔案大小]** 中指定一個值。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-113">Specify a value for **Set maximum file size**.</span></span> <span data-ttu-id="d9fa5-114">預設值為 5 MB。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-114">The default value is 5 megabytes (MB).</span></span>  
  
         <span data-ttu-id="d9fa5-115">(選擇性) 選取 **[啟用檔案換用]** ，在達到檔案大小上限時自動建立新檔案。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-115">Optionally, select **Enable file rollover** to automatically create new files when the maximum file size is reached.</span></span> <span data-ttu-id="d9fa5-116">您也可以選取 **[伺服器處理追蹤資料]** ，選取此選項後會由執行追蹤的服務處理追蹤資料，而非由用戶端應用程式來處理。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-116">You can also optionally select **Server processes trace data**, which causes the service that is running the trace to process trace data instead of the client application.</span></span> <span data-ttu-id="d9fa5-117">當伺服器處理追蹤資料時，即使在負擔極重情況下，也不會略過事件，但伺服器效能將受到影響。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-117">When the server processes trace data, no events are skipped even under stress conditions, but server performance may be affected.</span></span>  
  
    -   <span data-ttu-id="d9fa5-118">按一下 **[儲存至資料表]** 以將追蹤擷取至資料庫的資料表。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-118">Click **Save to table** to capture the trace to a database table.</span></span>  
  
         <span data-ttu-id="d9fa5-119">(選擇性) 按一下 **[設定最大資料列數]** ，然後指定一個值。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-119">Optionally, click **Set maximum rows**, and specify a value.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="d9fa5-120">當您不將追蹤結果儲存至檔案或資料表時，您可以在 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 開啟時檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-120">When you do not save the trace results to a file or table, you can view the trace while [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is open.</span></span> <span data-ttu-id="d9fa5-121">但是，當您停止追蹤並關閉 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]後會遺失追蹤結果。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-121">However, you lose the trace results after you stop the trace and close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="d9fa5-122">若要使用此方式以避免遺失追蹤結果，請在關閉 **之前，按一下** [檔案] **功能表上的** [儲存] [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來儲存結果。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-122">To avoid losing the trace results in this way, click **Save** on the **File** menu to save the results before you close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
5.  <span data-ttu-id="d9fa5-123">(選擇性) 選取 **[啟用追蹤停止時間]** 核取方塊，然後指定停止日期和時間。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-123">Optionally, select the **Enable trace stop time** check box, and specify a stop date and time.</span></span>  
  
6.  <span data-ttu-id="d9fa5-124">若要加入或移除事件、資料行或篩選，請按一下 [事件選取範圍]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-124">To add or remove events, data columns or filters, click the **Events Selection**tab.</span></span> <span data-ttu-id="d9fa5-125">如需詳細資訊，請參閱[指定追蹤檔案的事件及資料行 &#40;SQL Server Profiler&#41;](sql-server-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-125">For more information, see: [Specify Events and Data Columns for a Trace File &#40;SQL Server Profiler&#41;](sql-server-profiler.md)</span></span>  
  
7.  <span data-ttu-id="d9fa5-126">按一下 **[執行]** 啟動追蹤。</span><span class="sxs-lookup"><span data-stu-id="d9fa5-126">Click **Run** to start the trace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9fa5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9fa5-127">See Also</span></span>  
 <span data-ttu-id="d9fa5-128">[執行 SQL Server Profiler 所需的權限](permissions-required-to-run-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="d9fa5-128">[Permissions Required to Run SQL Server Profiler](permissions-required-to-run-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="d9fa5-129">[SQL Server Profiler 範本和權限](sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="d9fa5-129">[SQL Server Profiler Templates and Permissions](sql-server-profiler-templates-and-permissions.md) </span></span>  
 <span data-ttu-id="d9fa5-130">[[SQL Server Profiler]](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="d9fa5-130">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="d9fa5-131">使追蹤與 Windows 效能記錄資料產生相互關聯 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="d9fa5-131">Correlate a Trace with Windows Performance Log Data &#40;SQL Server Profiler&#41;</span></span>](../../database-engine/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)  
  
  
