---
title: 開始 SQL Server Profiler |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], starting
- SQL Server Profiler, starting
- starting SQL Server Profiler
ms.assetid: 22e57ffa-63b0-4de3-b92e-df297dda1226
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05743927420865a9b6341fc050ca999f494d64d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703577"
---
# <a name="start-sql-server-profiler"></a><span data-ttu-id="d33c4-102">啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d33c4-102">Start SQL Server Profiler</span></span>
  <span data-ttu-id="d33c4-103">您可以利用多種不同的方式來啟動 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，以支援在各種狀況中收集追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="d33c4-103">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in several different ways to support gathering trace output in a variety of scenarios.</span></span> <span data-ttu-id="d33c4-104">啟動 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的方式包括：從 **[開始]** 功能表、從 **Tuning Advisor 中的** [工具] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 功能表，以及從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的數個位置。</span><span class="sxs-lookup"><span data-stu-id="d33c4-104">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] include from the **Start** menu, from the **Tools** menu in [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor, and from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d33c4-105">當您第一次啟動 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，且從 **[檔案]** 功能表中選取 **[新增追蹤]** 時，應用程式會顯示一個 **[連接到伺服器]** 對話方塊，供您指定要連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d33c4-105">When you first start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and select **New Trace** from the **File** menu, the application displays a **Connect to Server** dialog box where you can specify the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to which you want to connect.</span></span>  
  
### <a name="to-start-sql-server-profiler-from-the-start-menu"></a><span data-ttu-id="d33c4-106">從 [開始] 功能表啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d33c4-106">To start SQL Server Profiler from the Start menu</span></span>  
  
1.  <span data-ttu-id="d33c4-107">在 **[開始]** 功能表中，依序指向 **[所有程式]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]] 和 **[效能工具]**，然後按一下 **[SQL Server Profiler]**。</span><span class="sxs-lookup"><span data-stu-id="d33c4-107">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Performance Tools**, and then click **SQL Server Profiler**.</span></span>  
  
### <a name="to-start-sql-server-profiler-in-database-engine-tuning-advisor"></a><span data-ttu-id="d33c4-108">在 Database Engine Tuning Advisor 中啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d33c4-108">To start SQL Server Profiler in Database Engine Tuning Advisor</span></span>  
  
1.  <span data-ttu-id="d33c4-109">在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor 的 **[工具]** 功能表上，按一下 **[SQL Server Profiler]** 。</span><span class="sxs-lookup"><span data-stu-id="d33c4-109">On the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Tuning Advisor **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
## <a name="starting-sql-server-profiler-in-management-studio"></a><span data-ttu-id="d33c4-110">在 Management Studio 中啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d33c4-110">Starting SQL Server Profiler in Management Studio</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="d33c4-111">會在自己的執行個體中啟動每個分析工具工作階段，並在關閉 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d33c4-111">starts each profiler session in its own instance and continues to run if you shutdown [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d33c4-112">您可以從 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 中的數個位置啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，如下列程序所示。</span><span class="sxs-lookup"><span data-stu-id="d33c4-112">You can start [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] from several locations in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], as illustrated in the following procedures.</span></span> <span data-ttu-id="d33c4-113">當 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 啟動時，它會載入連接內容、追蹤範本及其啟動點的篩選內容。</span><span class="sxs-lookup"><span data-stu-id="d33c4-113">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] starts it loads the connection context, trace template, and filter context of its launch point.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-tools-menu"></a><span data-ttu-id="d33c4-114">從工具功能表啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d33c4-114">To start SQL Server Profiler from the Tools menu</span></span>  
  
1.  <span data-ttu-id="d33c4-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [工具] 功能表中，按一下 [SQL Server Profiler]。</span><span class="sxs-lookup"><span data-stu-id="d33c4-115">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Tools** menu, click **SQL Server Profiler**.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-the-query-editor"></a><span data-ttu-id="d33c4-116">從查詢編輯器啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d33c4-116">To start SQL Server Profiler from the Query Editor</span></span>  
  
1.  <span data-ttu-id="d33c4-117">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 功能表列上，按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="d33c4-117">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] menu bar, click **New Query**.</span></span>  
  
2.  <span data-ttu-id="d33c4-118">在查詢編輯器中按一下滑鼠右鍵，然後選取 [在 SQL Server Profiler 中追蹤查詢]。</span><span class="sxs-lookup"><span data-stu-id="d33c4-118">In Query Editor, right-click and then select **Trace Query in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d33c4-119">連接內容是編輯器連接、追蹤範本為 TSQL_SPs，而套用的篩選為 SPID = 查詢視窗 SPID。</span><span class="sxs-lookup"><span data-stu-id="d33c4-119">The connection context is the editor connection, the trace template is TSQL_SPs, and the applied filter is SPID = query window SPID.</span></span>  
  
#### <a name="to-start-sql-server-profiler-from-activity-monitor"></a><span data-ttu-id="d33c4-120">若要從活動監視器啟動 SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="d33c4-120">To start SQL Server Profiler from Activity Monitor</span></span>  
  
1.  <span data-ttu-id="d33c4-121">在物件總管中，以滑鼠右鍵按一下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，然後按一下 [活動監視器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d33c4-121">In Object Explorer, right-click an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and then click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="d33c4-122">按一下 [處理序]\*\*\*\* 窗格，以滑鼠右鍵按一下您要分析的處理序，然後按一下 [在 SQL Server Profiler 中追蹤處理序]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d33c4-122">Click the **Processes** pane, right-click the process that you want to profile, and then click **Trace Process in SQL Server Profiler**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d33c4-123">選取處理序時，如果有開啟 [活動監視器]，則連接內容為 [物件總管] 連接。</span><span class="sxs-lookup"><span data-stu-id="d33c4-123">When a process is selected, the connection context is the Object Explorer connection when Activity Monitor was opened.</span></span> <span data-ttu-id="d33c4-124">追蹤範本是以伺服器類型為基礎的預設值，而且 SPID 等於所選處理序的 SPID。</span><span class="sxs-lookup"><span data-stu-id="d33c4-124">The trace template is the default based on the server type, and the SPID equals the SPID for the selected process.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d33c4-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="d33c4-125">.NET Framework Security</span></span>  
 <span data-ttu-id="d33c4-126">在 Windows 驗證模式中，執行 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的使用者帳戶必須有連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的權限。</span><span class="sxs-lookup"><span data-stu-id="d33c4-126">In Windows Authentication mode, the user account that runs [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] must have permission to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d33c4-127">若要利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]來執行追蹤，使用者也必須有 ALTER TRACE 權限。</span><span class="sxs-lookup"><span data-stu-id="d33c4-127">To perform tracing with [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], users must also have the ALTER TRACE permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33c4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d33c4-128">See Also</span></span>  
 <span data-ttu-id="d33c4-129">[SQL Server Profiler](sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="d33c4-129">[SQL Server Profiler](sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="d33c4-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="d33c4-130">Use SQL Server Management Studio</span></span>](../../database-engine/use-sql-server-management-studio.md)  
  
  
