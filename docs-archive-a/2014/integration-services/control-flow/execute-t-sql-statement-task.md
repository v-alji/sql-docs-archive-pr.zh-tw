---
title: 執行 T-SQL 陳述式工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7ebc73ad843ac7fcf1dfbe7699ecd8ea53edcdad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688106"
---
# <a name="execute-t-sql-statement-task"></a><span data-ttu-id="c0f09-102">執行 T-SQL 陳述式工作</span><span class="sxs-lookup"><span data-stu-id="c0f09-102">Execute T-SQL Statement Task</span></span>
  <span data-ttu-id="c0f09-103">「執行 T-SQL 陳述式」工作會執行 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0f09-103">The Execute T-SQL Statement task runs Transact-SQL statements.</span></span> <span data-ttu-id="c0f09-104">如需詳細資訊，請參閱 [Transact-SQL 參考 &#40;資料庫引擎&#41;](/sql/t-sql/language-reference) 和 [Integration Services &#40;SSIS&#41; 查詢](../integration-services-ssis-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f09-104">For more information, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference) and [Integration Services &#40;SSIS&#41; Queries](../integration-services-ssis-queries.md).</span></span>  
  
 <span data-ttu-id="c0f09-105">此工作與執行 SQL 工作類似。</span><span class="sxs-lookup"><span data-stu-id="c0f09-105">This task is similar to the Execute SQL task.</span></span> <span data-ttu-id="c0f09-106">不過，「執行 T-SQL 陳述式」工作僅支援 Transact-SQL 版的 SQL 語言，而且您無法在使用其他 SQL 語言方言的伺服器上使用此工作執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0f09-106">However, the Execute T-SQL Statement task supports only the Transact-SQL version of the SQL language and you cannot use this task to run statements on servers that use other dialects of the SQL language.</span></span> <span data-ttu-id="c0f09-107">如果您需要執行參數化查詢、將查詢結果儲存至變數，或使用屬性運算式，則應使用執行 SQL 工作而非「執行 T-SQL 陳述式」工作。</span><span class="sxs-lookup"><span data-stu-id="c0f09-107">If you need to run parameterized queries, save the query results to variables, or use property expressions, you should use the Execute SQL task instead of the Execute T-SQL Statement task.</span></span> <span data-ttu-id="c0f09-108">如需相關資訊，請參閱 [Execute SQL Task](execute-sql-task.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f09-108">For more information, see [Execute SQL Task](execute-sql-task.md).</span></span>  
  
## <a name="configuration-of-the-execute-t-sql-task"></a><span data-ttu-id="c0f09-109">設定執行 T-SQL 工作</span><span class="sxs-lookup"><span data-stu-id="c0f09-109">Configuration of the Execute T-SQL Task</span></span>  
 <span data-ttu-id="c0f09-110">您可以透過 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="c0f09-110">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="c0f09-111">這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 區段。</span><span class="sxs-lookup"><span data-stu-id="c0f09-111">This task is in the **Maintenance Plan Tasks** section of the **Toolbox** in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="c0f09-112">如需有關可在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="c0f09-112">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="c0f09-113">執行 T-SQL 陳述式工作 &#40;維護計畫&#41;</span><span class="sxs-lookup"><span data-stu-id="c0f09-113">Execute T-SQL Statement Task &#40;Maintenance Plan&#41;</span></span>](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 <span data-ttu-id="c0f09-114">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="c0f09-114">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="c0f09-115">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="c0f09-115">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="c0f09-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f09-116">See Also</span></span>  
 <span data-ttu-id="c0f09-117">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="c0f09-117">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="c0f09-118">[控制流程](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="c0f09-118">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="c0f09-119">Integration Services 套件中的 MERGE</span><span class="sxs-lookup"><span data-stu-id="c0f09-119">MERGE in Integration Services Packages</span></span>](merge-in-integration-services-packages.md)  
  
  
