---
title: 預設追蹤已啟用伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], traces
- traces [SQL Server], logs
- default trace enabled option
ms.assetid: 1322d668-44f4-469e-8fd6-e0d02a81c8f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d40305de7375f2ae10d563871fd40b7acfa463f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707857"
---
# <a name="default-trace-enabled-server-configuration-option"></a><span data-ttu-id="76a30-102">預設追蹤已啟用伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="76a30-102">default trace enabled Server Configuration Option</span></span>
  <span data-ttu-id="76a30-103">使用 **default trace enabled** 選項，啟用或停用預設的追蹤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="76a30-103">Use the **default trace enabled** option to enable or disable the default trace log files.</span></span> <span data-ttu-id="76a30-104">預設追蹤功能可針對主要與組態選項相關的活動和變更提供豐富、永續的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="76a30-104">The default trace functionality provides a rich, persistent log of activity and changes primarily related to the configuration options.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="76a30-105">請改用擴充事件。</span><span class="sxs-lookup"><span data-stu-id="76a30-105">Use Extended Events instead.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="76a30-106">目的</span><span class="sxs-lookup"><span data-stu-id="76a30-106">Purpose</span></span>  
 <span data-ttu-id="76a30-107">預設追蹤可為資料庫管理員提供疑難排解協助，確定他們有必要的記錄檔資料，能在問題發生的第一時間進行診斷。</span><span class="sxs-lookup"><span data-stu-id="76a30-107">Default trace provides troubleshooting assistance to database administrators by ensuring that they have the log data necessary to diagnose problems the first time they occur.</span></span>  
  
## <a name="viewing"></a><span data-ttu-id="76a30-108">檢視</span><span class="sxs-lookup"><span data-stu-id="76a30-108">Viewing</span></span>  
 <span data-ttu-id="76a30-109">預設追蹤記錄檔可由 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 開啟和檢查，或使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 系統函數，利用 `fn_trace_gettable` 進行查詢。</span><span class="sxs-lookup"><span data-stu-id="76a30-109">The default trace logs can be opened and examined by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or queried with [!INCLUDE[tsql](../../includes/tsql-md.md)] by using the `fn_trace_gettable` system function.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="76a30-110">開啟預設追蹤記錄檔的方式，與開啟一般追蹤輸出檔案一樣。</span><span class="sxs-lookup"><span data-stu-id="76a30-110">can open the default trace log files just as it does normal trace output files.</span></span> <span data-ttu-id="76a30-111">根據預設，預設追蹤記錄檔是使用換用追蹤檔案，儲存在 `\MSSQL\LOG` 目錄中。</span><span class="sxs-lookup"><span data-stu-id="76a30-111">The default trace log is stored by default in the `\MSSQL\LOG` directory using a rollover trace file.</span></span> <span data-ttu-id="76a30-112">預設追蹤記錄檔的基底檔案名稱是 `log.trc`。</span><span class="sxs-lookup"><span data-stu-id="76a30-112">The base file name for the default trace log file is `log.trc`.</span></span> <span data-ttu-id="76a30-113">在典型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安裝中，會啟用預設追蹤，因此它會變成 TraceID 1。</span><span class="sxs-lookup"><span data-stu-id="76a30-113">In a typical installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the default trace is enabled and thus becomes TraceID 1.</span></span> <span data-ttu-id="76a30-114">如果在安裝之後及建立其他追蹤之後啟用它，此 TraceID 可能會變成較大的數目。</span><span class="sxs-lookup"><span data-stu-id="76a30-114">If enabled after installation and after creating other traces, the TraceID can become a larger number.</span></span>  
  
 <span data-ttu-id="76a30-115">如需使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler 來檢視此追蹤檔案的詳細資訊，請參閱[開啟追蹤檔案 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)</span><span class="sxs-lookup"><span data-stu-id="76a30-115">For more information about using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler to view this trace file, see [Open a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)</span></span>  
  
### <a name="example"></a><span data-ttu-id="76a30-116">範例：</span><span class="sxs-lookup"><span data-stu-id="76a30-116">Example:</span></span>  
 <span data-ttu-id="76a30-117">以下陳述式可開啟預設位置中的預設追蹤記錄檔：</span><span class="sxs-lookup"><span data-stu-id="76a30-117">The following statement opens the default trace log in the default location:</span></span>  
  
```  
SELECT *   
FROM fn_trace_gettable  
('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG\log.trc', default);  
GO  
  
```  
  
## <a name="configuring"></a><span data-ttu-id="76a30-118">進行設定</span><span class="sxs-lookup"><span data-stu-id="76a30-118">Configuring</span></span>  
 <span data-ttu-id="76a30-119">設為 1 時， **default trace enabled** 選項會啟用 **「預設的追蹤」** 功能。</span><span class="sxs-lookup"><span data-stu-id="76a30-119">When set to 1, the **default trace enabled** option enables **Default Trace**.</span></span> <span data-ttu-id="76a30-120">這個選項的預設值是 1 (ON)。</span><span class="sxs-lookup"><span data-stu-id="76a30-120">The default setting for this option is 1 (ON).</span></span> <span data-ttu-id="76a30-121">設為 0 則會關閉追蹤功能。</span><span class="sxs-lookup"><span data-stu-id="76a30-121">A value of 0 turns off the trace.</span></span>  
  
 <span data-ttu-id="76a30-122">**default trace enabled** 屬於進階選項。</span><span class="sxs-lookup"><span data-stu-id="76a30-122">The **default trace enabled** option is an advanced option.</span></span> <span data-ttu-id="76a30-123">如果您要使用 **sp_configure** 系統預存程序來變更設定，只有在 [顯示進階選項] 設定為 1 時，才能變更 [預設追蹤已啟用] 選項。</span><span class="sxs-lookup"><span data-stu-id="76a30-123">If you are using the **sp_configure** system stored procedure to change the setting, you can change the **default trace enabled** option only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="76a30-124">設定會立即生效，伺服器不必重新啟動。</span><span class="sxs-lookup"><span data-stu-id="76a30-124">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a30-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76a30-125">See Also</span></span>  
 <span data-ttu-id="76a30-126">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="76a30-126">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="76a30-127">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="76a30-127">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="76a30-128">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="76a30-128">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
