---
title: TSQL 事件類別目錄 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, TSQL event category
- TSQL event category [SQL Server]
- event classes [SQL Server], TSQL event category
ms.assetid: 215f8747-64b5-4bf3-9845-d476b10cda3a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 763d5f31fd3562f54b274a74324ed4715b623a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686947"
---
# <a name="tsql-event-category"></a><span data-ttu-id="b1473-102">TSQL 事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="b1473-102">TSQL Event Category</span></span>
  <span data-ttu-id="b1473-103">**TSQL** 事件類別目錄包含一般 TSQL 事件。</span><span class="sxs-lookup"><span data-stu-id="b1473-103">The **TSQL** event category contains general TSQL events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1473-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="b1473-104">In This Section</span></span>  
  
|<span data-ttu-id="b1473-105">主題</span><span class="sxs-lookup"><span data-stu-id="b1473-105">Topic</span></span>|<span data-ttu-id="b1473-106">描述</span><span class="sxs-lookup"><span data-stu-id="b1473-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b1473-107">Exec Prepared SQL 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-107">Exec Prepared SQL Event Class</span></span>](exec-prepared-sql-event-class.md)|<span data-ttu-id="b1473-108">代表 SqlClient、ODBC、OLE DB、或 DB-Library 已經執行備妥的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b1473-108">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has executed a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="b1473-109">Prepare SQL 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-109">Prepare SQL Event Class</span></span>](prepare-sql-event-class.md)|<span data-ttu-id="b1473-110">代表 SqlClient、ODBC、OLE DB、或者 DB-Library 已經備妥要使用的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b1473-110">Indicates that SqlClient, ODBC, OLE DB, or DB-Library has prepared a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements for use.</span></span>|  
|[<span data-ttu-id="b1473-111">SQL:BatchCompleted 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-111">SQL:BatchCompleted Event Class</span></span>](sql-batchcompleted-event-class.md)|<span data-ttu-id="b1473-112">代表已經完成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次。</span><span class="sxs-lookup"><span data-stu-id="b1473-112">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch has completed.</span></span>|  
|[<span data-ttu-id="b1473-113">SQL:BatchStarting 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-113">SQL:BatchStarting Event Class</span></span>](sql-batchstarting-event-class.md)|<span data-ttu-id="b1473-114">代表 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次已經啟動。</span><span class="sxs-lookup"><span data-stu-id="b1473-114">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch is starting.</span></span>|  
|[<span data-ttu-id="b1473-115">SQL:StmtCompleted 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-115">SQL:StmtCompleted Event Class</span></span>](sql-stmtcompleted-event-class.md)|<span data-ttu-id="b1473-116">代表已經完成 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b1473-116">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement has completed.</span></span>|  
|[<span data-ttu-id="b1473-117">SQL:StmtRecompile 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-117">SQL:StmtRecompile Event Class</span></span>](sql-stmtrecompile-event-class.md)|<span data-ttu-id="b1473-118">代表造成陳述式層級重新編譯的所有批次類型：預存程序、觸發程序、特定批次與查詢。</span><span class="sxs-lookup"><span data-stu-id="b1473-118">Indicates statement-level recompilations caused by all types of batches: stored procedures, triggers, ad hoc batches, and queries.</span></span>|  
|[<span data-ttu-id="b1473-119">SQL:StmtStarting 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-119">SQL:StmtStarting Event Class</span></span>](sql-stmtstarting-event-class.md)|<span data-ttu-id="b1473-120">代表 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式已經啟動。</span><span class="sxs-lookup"><span data-stu-id="b1473-120">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is starting.</span></span>|  
|[<span data-ttu-id="b1473-121">Unprepare SQL 事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-121">Unprepare SQL Event Class</span></span>](unprepare-sql-event-class.md)|<span data-ttu-id="b1473-122">代表 SqlClient、ODBC、OLE DB、或 DB-Library 已經刪除備妥的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b1473-122">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has deleted a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="b1473-123">XQuery 靜態類型事件類別</span><span class="sxs-lookup"><span data-stu-id="b1473-123">XQuery Static Type Event Class</span></span>](xquery-static-type-event-class.md)|<span data-ttu-id="b1473-124">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行 XQuery 運算式時發生。</span><span class="sxs-lookup"><span data-stu-id="b1473-124">Occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes an XQuery expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1473-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1473-125">See Also</span></span>  
 [<span data-ttu-id="b1473-126">Transact-SQL 參考 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="b1473-126">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
