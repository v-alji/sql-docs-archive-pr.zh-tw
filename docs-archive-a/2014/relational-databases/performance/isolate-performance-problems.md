---
title: 隔離效能問題 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- isolating performance problems [SQL Server]
- monitoring performance [SQL Server], isolating problems
- database monitoring [SQL Server], isolating problems
- tuning databases [SQL Server], isolating problems
- monitoring server performance [SQL Server], isolating problems
- database performance [SQL Server], isolating problems
- server performance [SQL Server], isolating problems
ms.assetid: 2eb425cb-9166-4027-ae08-c8fc2d236f44
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b42d780a8174ab57d00de72e8b00ef7af0abc17e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701101"
---
# <a name="isolate-performance-problems"></a><span data-ttu-id="6c912-102">隔離效能問題</span><span class="sxs-lookup"><span data-stu-id="6c912-102">Isolate Performance Problems</span></span>
  <span data-ttu-id="6c912-103">通常，同時使用數種 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 Microsoft Windows 工具來隔離資料庫效能問題，會比一次使用一種工具要更有效率。</span><span class="sxs-lookup"><span data-stu-id="6c912-103">It is often more effective to use several [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or Microsoft Windows tools together to isolate database performance problems than to use one tool at a time.</span></span> <span data-ttu-id="6c912-104">例如，稱為 Showplan 的圖形「執行計畫」功能可協助您快速識別出單一查詢中的死結。</span><span class="sxs-lookup"><span data-stu-id="6c912-104">For example, the graphical Execution Plan feature, also called Showplan, helps you quickly recognize deadlocks in a single query.</span></span> <span data-ttu-id="6c912-105">不過，如果同時使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 Windows 的監視功能，可以更容易辨識出其他效能問題。</span><span class="sxs-lookup"><span data-stu-id="6c912-105">However, you can recognize some other performance problems more easily if you use the monitoring features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows together.</span></span>  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="6c912-106">可以用來監視和疑難排解 Transact-SQL 及應用程式的相關問題。</span><span class="sxs-lookup"><span data-stu-id="6c912-106">can be used to monitor and troubleshoot Transact-SQL and application-related problems.</span></span> <span data-ttu-id="6c912-107">「系統監視器」可以用來監視硬體與其他跟系統相關的問題。</span><span class="sxs-lookup"><span data-stu-id="6c912-107">System Monitor can be used to monitor hardware and other system-related problems.</span></span>  
  
 <span data-ttu-id="6c912-108">您可以監視下列範圍來進行問題的疑難排解：</span><span class="sxs-lookup"><span data-stu-id="6c912-108">You can monitor the following areas to troubleshoot problems:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6c912-109">預存程序或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的批次。</span><span class="sxs-lookup"><span data-stu-id="6c912-109">stored procedures or batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements submitted by user applications.</span></span>  
  
-   <span data-ttu-id="6c912-110">使用者活動，例如封鎖的鎖定或死結。</span><span class="sxs-lookup"><span data-stu-id="6c912-110">User activity, such as blocking locks or deadlocks.</span></span>  
  
-   <span data-ttu-id="6c912-111">硬體活動，例如磁碟使用量。</span><span class="sxs-lookup"><span data-stu-id="6c912-111">Hardware activity, such as disk usage.</span></span>  
  
 <span data-ttu-id="6c912-112">問題涵蓋了：</span><span class="sxs-lookup"><span data-stu-id="6c912-112">Problems can include:</span></span>  
  
-   <span data-ttu-id="6c912-113">跟撰寫不正確的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式有關的應用程式開發錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c912-113">Application development errors involving incorrectly written [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
-   <span data-ttu-id="6c912-114">硬體錯誤，例如磁碟或網路相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c912-114">Hardware errors, such as disk- or network-related errors.</span></span>  
  
-   <span data-ttu-id="6c912-115">因資料庫設計不正確而造成的過度封鎖。</span><span class="sxs-lookup"><span data-stu-id="6c912-115">Excessive blocking due to an incorrectly designed database.</span></span>  
  
## <a name="tools-for-common-performance-problems"></a><span data-ttu-id="6c912-116">一般效能問題的工具</span><span class="sxs-lookup"><span data-stu-id="6c912-116">Tools for Common Performance Problems</span></span>  
 <span data-ttu-id="6c912-117">能謹慎選取要各個工具監視或微調的效能問題同樣很重要。</span><span class="sxs-lookup"><span data-stu-id="6c912-117">Equally important is careful selection of the performance problem that you want each tool to monitor or tune.</span></span> <span data-ttu-id="6c912-118">工具與公用程式會根據想要解決的效能問題類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="6c912-118">The tool and the utility depend on the type of performance problem you want to resolve.</span></span>  
  
 <span data-ttu-id="6c912-119">以下主題描述許多監視與微調工具以及這些工具可發現的問題。</span><span class="sxs-lookup"><span data-stu-id="6c912-119">The following topics describe a variety of monitoring and tuning tools and the problems they uncover.</span></span>  
  
 [<span data-ttu-id="6c912-120">找出瓶頸</span><span class="sxs-lookup"><span data-stu-id="6c912-120">Identify Bottlenecks</span></span>](identify-bottlenecks.md)  
  
 [<span data-ttu-id="6c912-121">監視記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="6c912-121">Monitor Memory Usage</span></span>](../performance-monitor/monitor-memory-usage.md)  
  
  
