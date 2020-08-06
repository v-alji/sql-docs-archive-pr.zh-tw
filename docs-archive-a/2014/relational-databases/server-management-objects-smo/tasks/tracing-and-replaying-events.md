---
title: 追蹤和重新執行事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7f0d570c70ef1cba080217e6c3a0f9b6055a4d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700933"
---
# <a name="tracing-and-replaying-events"></a><span data-ttu-id="9dfc6-102">追蹤及重新執行事件</span><span class="sxs-lookup"><span data-stu-id="9dfc6-102">Tracing and Replaying Events</span></span>
  <span data-ttu-id="9dfc6-103">在 SMO 中，`Trace` 命名空間中的 `Replay` 和 <xref:Microsoft.SqlServer.Management.Trace> 物件會提供 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 功能的程式設計存取方式，該功能是用來監視 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-103">In SMO, the `Trace` and `Replay` objects in the <xref:Microsoft.SqlServer.Management.Trace> namespace provide programmatic access to the [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] functionality, which is used for monitoring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9dfc6-104">您可以擷取每一個事件的相關資料，並將資料儲存至檔案或資料表，以供稍後分析。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-104">You can capture and save data about each event to a file or table to analyze later.</span></span> <span data-ttu-id="9dfc6-105">例如，您可以監視實際環境，查看哪些程序由於執行速度過慢而妨礙效能。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-105">For example, you can monitor a production environment to see which procedures are impeding performance by executing too slowly.</span></span>  
  
 <span data-ttu-id="9dfc6-106"> 和  物件會提供一組物件，這一組物件可在  執行個體上用來建立追蹤。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-106">The `Trace` and `Replay` objects provide a set of objects that can be used to create traces on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9dfc6-107">您可以從自己的應用程式中使用這些物件，以手動方式為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 建立追蹤。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-107">These objects can be used from within your own applications to create traces manually for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9dfc6-108">另外，SMO `Trace` 物件也可用來讀取之前透過監視 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 或 DTS 記錄所建立的 SQL 追蹤檔案和資料表。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-108">Additionally, SMO `Trace` objects can be used to read SQL Trace files and tables that were created by monitoring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], or DTS logging.</span></span>  
  
 <span data-ttu-id="9dfc6-109">SMO `Trace` 物件可讓您執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="9dfc6-109">SMO `Trace` objects let you perform the following functions:</span></span>  
  
-   <span data-ttu-id="9dfc6-110">建立追蹤。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-110">Create a trace.</span></span>  
  
-   <span data-ttu-id="9dfc6-111">設定追蹤的篩選。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-111">Set filters on the trace.</span></span>  
  
-   <span data-ttu-id="9dfc6-112">設定正在追蹤的事件。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-112">Set the events that are being traced.</span></span>  
  
-   <span data-ttu-id="9dfc6-113">停止或啟動追蹤。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-113">Stop or start a trace.</span></span>  
  
-   <span data-ttu-id="9dfc6-114">讀取追蹤檔案和追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-114">Read trace files, and trace tables.</span></span>  
  
-   <span data-ttu-id="9dfc6-115">取得有關追蹤事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-115">Get information about events on a trace.</span></span>  
  
-   <span data-ttu-id="9dfc6-116">取得有關追蹤篩選的資訊。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-116">Get information about filters on a trace.</span></span>  
  
-   <span data-ttu-id="9dfc6-117">以程式設計方式操作追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-117">Manipulate trace data programmatically.</span></span>  
  
-   <span data-ttu-id="9dfc6-118">撰寫追蹤資料表和追蹤檔案。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-118">Write trace tables and trace files.</span></span>  
  
-   <span data-ttu-id="9dfc6-119">重新執行追蹤檔案或追蹤資料表。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-119">Replay trace files or trace tables.</span></span>  
  
 <span data-ttu-id="9dfc6-120">和物件中的追蹤 `Trace` 資料 `Replay` 可由 SMO 應用程式使用，也可以使用[SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md)以手動方式進行檢查。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-120">The trace data from the `Trace` and `Replay` objects can be used by the SMO application, or it can be examined manually by using [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md).</span></span> <span data-ttu-id="9dfc6-121">追蹤資料也與也提供追蹤功能的[SQL 追蹤](../../sql-trace/sql-trace.md)預存程式相容。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-121">The trace data is also compatible with the [SQL Trace](../../sql-trace/sql-trace.md) stored procedures that also provide tracing capabilities.</span></span>  
  
 <span data-ttu-id="9dfc6-122">SMO 追蹤物件位於 <xref:Microsoft.SqlServer.Management.Trace> 命名空間內，該命名空間需要參考 Microsoft.SQLServer.ConnectionInfo.dll 檔。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-122">The SMO trace objects reside in the <xref:Microsoft.SqlServer.Management.Trace> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
 <span data-ttu-id="9dfc6-123">`Trace` 和 `Replay` 物件會要求 <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> 物件建立與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-123">The `Trace` and `Replay` objects require a <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> object to establish a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9dfc6-124"> 物件位於  命名空間內，該命名空間需要參考 Microsoft.SQLServer.ConnectionInfo.dll 檔。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-124">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object resides in the <xref:Microsoft.SqlServer.Management.Common> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dfc6-125">64 位元平台上不支援 `Trace` 和 `Replay` 物件。</span><span class="sxs-lookup"><span data-stu-id="9dfc6-125">The `Trace` and `Replay` objects are not supported on a 64-bit platform.</span></span>  
  
  
