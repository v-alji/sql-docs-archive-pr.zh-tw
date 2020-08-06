---
title: Performance 事件類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Performance event category
- Performance event category [SQL Server]
- event classes [SQL Server], Performance event category
ms.assetid: 708f3585-d8be-4980-bbff-672d7c59397e
author: stevestein
ms.author: sstein
ms.openlocfilehash: b0c076a4132298797313ecbf0874d9d2d4e453cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597815"
---
# <a name="performance-event-category"></a><span data-ttu-id="37256-102">Performance 事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="37256-102">Performance Event Category</span></span>
  <span data-ttu-id="37256-103">使用 **Performance** 事件類別目錄，可以監視 **Showplan** 事件類別，以及經由 SQL 資料操作語言 (DML) 運算子的執行而產生的事件類別。</span><span class="sxs-lookup"><span data-stu-id="37256-103">Use the **Performance** event category to monitor **Showplan** event classes and event classes that are produced from the execution of SQL data manipulation language (DML) operators.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37256-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="37256-104">In This Section</span></span>  
  
|<span data-ttu-id="37256-105">主題</span><span class="sxs-lookup"><span data-stu-id="37256-105">Topic</span></span>|<span data-ttu-id="37256-106">描述</span><span class="sxs-lookup"><span data-stu-id="37256-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="37256-107">Auto Stats 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-107">Auto Stats Event Class</span></span>](auto-stats-event-class.md)|<span data-ttu-id="37256-108">指出已自動更新索引和資料行統計資料。</span><span class="sxs-lookup"><span data-stu-id="37256-108">Indicates that an automatic updating of index and column statistics has occurred.</span></span>|  
|[<span data-ttu-id="37256-109">Degree of Parallelism &#40;7.0 Insert&#41; 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-109">Degree of Parallelism &#40;7.0 Insert&#41; Event Class</span></span>](degree-of-parallelism-7-0-insert-event-class.md)|<span data-ttu-id="37256-110">指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已經使用序列或平行計畫來執行 SELECT、INSERT、UPDATE 或 DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="37256-110">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a SELECT, INSERT, UPDATE, or DELETE statement using either a serial or parallel plan.</span></span> <span data-ttu-id="37256-111">此外，系統也會回報用來執行此作業的 CPU 數目。</span><span class="sxs-lookup"><span data-stu-id="37256-111">The number of CPUs used to perform the operation is also reported.</span></span>|  
|[<span data-ttu-id="37256-112">Performance Statistics 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-112">Performance Statistics Event Class</span></span>](performance-statistics-event-class.md)|<span data-ttu-id="37256-113">監視執行中的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="37256-113">Monitors performance of the queries that are being executed.</span></span>|  
|[<span data-ttu-id="37256-114">Showplan All 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-114">Showplan All Event Class</span></span>](showplan-all-event-class.md)|<span data-ttu-id="37256-115">識別 SQL 陳述式中的 **Showplan** 運算子。</span><span class="sxs-lookup"><span data-stu-id="37256-115">Identifies **Showplan** operators within a SQL statement.</span></span>|  
|[<span data-ttu-id="37256-116">Showplan All for Query Compile 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-116">Showplan All for Query Compile Event Class</span></span>](showplan-all-for-query-compile-event-class.md)|<span data-ttu-id="37256-117">顯示 **Showplan** 運算子的編譯時間資料。</span><span class="sxs-lookup"><span data-stu-id="37256-117">Displays compile time data for **Showplan** operators.</span></span>|  
|[<span data-ttu-id="37256-118">Showplan Statistics Profile 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-118">Showplan Statistics Profile Event Class</span></span>](showplan-statistics-profile-event-class.md)|<span data-ttu-id="37256-119">顯示查詢的估計成本。</span><span class="sxs-lookup"><span data-stu-id="37256-119">Displays the estimated cost of a query.</span></span>|  
|[<span data-ttu-id="37256-120">Showplan XML 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-120">Showplan XML Event Class</span></span>](showplan-xml-event-class.md)|<span data-ttu-id="37256-121">識別 SQL 陳述式中的 **Showplan** 運算子。</span><span class="sxs-lookup"><span data-stu-id="37256-121">Identifies the **Showplan** operators in a SQL statement.</span></span> <span data-ttu-id="37256-122">事件類別會以定義完善的 XML 文件來儲存每一個事件。</span><span class="sxs-lookup"><span data-stu-id="37256-122">The event class stores each event as a well defined XML document.</span></span>|  
|[<span data-ttu-id="37256-123">Showplan XML For Query Compile 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-123">Showplan XML for Query Compile Event Class</span></span>](showplan-xml-for-query-compile-event-class.md)|<span data-ttu-id="37256-124">以 XML 格式顯示 **Showplan** 運算子的編譯時間資料。</span><span class="sxs-lookup"><span data-stu-id="37256-124">Displays compile time data for **Showplan** operators in XML format.</span></span>|  
|[<span data-ttu-id="37256-125">Showplan XML Statistics Profile 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-125">Showplan XML Statistics Profile Event Class</span></span>](showplan-xml-statistics-profile-event-class.md)|<span data-ttu-id="37256-126">識別與 SQL 陳述式相關聯的 **Showplan** 運算子。</span><span class="sxs-lookup"><span data-stu-id="37256-126">Identifies the **Showplan** operators associated with a SQL statement.</span></span> <span data-ttu-id="37256-127">輸出是 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="37256-127">The output is an XML document.</span></span>|  
|[<span data-ttu-id="37256-128">SQL:FullTextQuery 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-128">SQL:FullTextQuery Event Class</span></span>](sql-fulltextquery-event-class.md)|<span data-ttu-id="37256-129">指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已執行全文檢索查詢。</span><span class="sxs-lookup"><span data-stu-id="37256-129">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has executed a full-text query.</span></span>|  
|[<span data-ttu-id="37256-130">Plan Guide Successful 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-130">Plan Guide Successful Event Class</span></span>](plan-guide-successful-event-class.md)|<span data-ttu-id="37256-131">指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 成功針對包含計畫指南的查詢或批次產生了執行計畫。</span><span class="sxs-lookup"><span data-stu-id="37256-131">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] successfully produced an execution plan for a query or batch that contained a plan guide.</span></span>|  
|[<span data-ttu-id="37256-132">Plan Guide Unsuccessful 事件類別</span><span class="sxs-lookup"><span data-stu-id="37256-132">Plan Guide Unsuccessful Event Class</span></span>](plan-guide-unsuccessful-event-class.md)|<span data-ttu-id="37256-133">指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 無法針對包含計畫指南的查詢或批次產生執行計畫。</span><span class="sxs-lookup"><span data-stu-id="37256-133">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] could not produce an execution plan for a query or batch that contained a plan guide.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37256-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37256-134">See Also</span></span>  
 [<span data-ttu-id="37256-135">擴充事件</span><span class="sxs-lookup"><span data-stu-id="37256-135">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
