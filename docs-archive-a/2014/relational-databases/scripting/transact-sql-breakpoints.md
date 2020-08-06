---
title: Transact-SQL 中斷點
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: rothja
ms.author: jroth
ms.openlocfilehash: c9595c9627ac3cc445b1193881c2d5b772e9b71d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598798"
---
# <a name="transact-sql-breakpoints"></a><span data-ttu-id="e5342-102">Transact-SQL 中斷點</span><span class="sxs-lookup"><span data-stu-id="e5342-102">Transact-SQL Breakpoints</span></span>
  <span data-ttu-id="e5342-103">中斷點指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具要在特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式上暫停執行，然後您就可以在該點檢視程式碼元素的狀態。</span><span class="sxs-lookup"><span data-stu-id="e5342-103">Breakpoints specify that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="e5342-104">中斷點</span><span class="sxs-lookup"><span data-stu-id="e5342-104">Breakpoints</span></span>  
 <span data-ttu-id="e5342-105">執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具時，您可以切換特定陳述式上的中斷點。</span><span class="sxs-lookup"><span data-stu-id="e5342-105">When running the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can toggle a breakpoint on specific statements.</span></span> <span data-ttu-id="e5342-106">執行到具有中斷點的陳述式時，偵錯工具會暫停執行，讓您可以檢視偵錯資訊，例如變數和參數中的值。</span><span class="sxs-lookup"><span data-stu-id="e5342-106">When execution reaches a statement with a breakpoint, the debugger pauses execution so you can view debugging information, such as the values present in variables and parameters.</span></span>  
  
 <span data-ttu-id="e5342-107">您可以在編輯器視窗中個別管理中斷點，或是使用 [中斷點]  視窗統一進行管理。</span><span class="sxs-lookup"><span data-stu-id="e5342-107">You can manage breakpoints individually in the editor window, or collectively by using the **Breakpoints** window.</span></span> <span data-ttu-id="e5342-108">您可以編輯中斷點以指定項目，例如應該暫停執行的特定條件，或要在執行中斷點時採取的動作。</span><span class="sxs-lookup"><span data-stu-id="e5342-108">You can edit breakpoints to specify items such as specific conditions under which execution should pause, or the actions to be taken if the breakpoint is executed.</span></span>  
  
## <a name="breakpoint-tasks"></a><span data-ttu-id="e5342-109">中斷點工作</span><span class="sxs-lookup"><span data-stu-id="e5342-109">Breakpoint Tasks</span></span>  
  
|<span data-ttu-id="e5342-110">工作描述</span><span class="sxs-lookup"><span data-stu-id="e5342-110">Task Description</span></span>|<span data-ttu-id="e5342-111">主題</span><span class="sxs-lookup"><span data-stu-id="e5342-111">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="e5342-112">描述如何指定您要暫停偵錯工具的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e5342-112">Describes how to specify the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement on which you want the debugger to pause.</span></span>|[<span data-ttu-id="e5342-113">切換中斷點</span><span class="sxs-lookup"><span data-stu-id="e5342-113">Toggle a Breakpoint</span></span>](../spatial/point.md)|  
|<span data-ttu-id="e5342-114">描述如何暫時停用中斷點，稍後再重新予以啟用。</span><span class="sxs-lookup"><span data-stu-id="e5342-114">Describes how to temporarily deactivate a breakpoint, and later reactivate it.</span></span> <span data-ttu-id="e5342-115">同時描述如何刪除中斷點。</span><span class="sxs-lookup"><span data-stu-id="e5342-115">Also describes how to delete a breakpoint.</span></span>|[<span data-ttu-id="e5342-116">啟用、停用以及刪除中斷點</span><span class="sxs-lookup"><span data-stu-id="e5342-116">Enable, Disable, and Delete Breakpoints</span></span>](enable-disable-and-delete-breakpoints.md)|  
|<span data-ttu-id="e5342-117">描述如何指定條件，而條件定義是否依據所指定 Transact-SQL 運算式的評估結果來中斷中斷點。</span><span class="sxs-lookup"><span data-stu-id="e5342-117">Describes how to specify a condition, which defines whether breakpoint breaks based on the evaluation of a specified Transact-SQL expression.</span></span>|[<span data-ttu-id="e5342-118">指定中斷點條件</span><span class="sxs-lookup"><span data-stu-id="e5342-118">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)|  
|<span data-ttu-id="e5342-119">描述如何指定叫用計數，而叫用計數只有在包含中斷點的陳述式已經執行指定的次數時才會導致中斷點中斷。</span><span class="sxs-lookup"><span data-stu-id="e5342-119">Describes how to specify a hit count, which causes a breakpoint to break only when the statement containing the breakpoint has been executed a specified number of times.</span></span>|[<span data-ttu-id="e5342-120">指定叫用計數</span><span class="sxs-lookup"><span data-stu-id="e5342-120">Specify a Hit Count</span></span>](specify-a-hit-count.md)|  
|<span data-ttu-id="e5342-121">描述如何指定篩選，而篩選只會中斷所指定處理序或執行緒的中斷點。</span><span class="sxs-lookup"><span data-stu-id="e5342-121">Describes how to specify a filter, which causes a breakpoint to break for only specified processes or threads.</span></span>|[<span data-ttu-id="e5342-122">指定中斷點篩選條件</span><span class="sxs-lookup"><span data-stu-id="e5342-122">Specify a Breakpoint Filter</span></span>](specify-a-breakpoint-filter.md)|  
|<span data-ttu-id="e5342-123">描述如何指定 [叫用時]  動作，而此動作是在執行中斷點陳述式時執行的自訂作業。</span><span class="sxs-lookup"><span data-stu-id="e5342-123">Describes how to specify a **When Hit** action, which is a custom operation that is performed when the breakpoint statement is executed.</span></span> <span data-ttu-id="e5342-124">範例為列印訊息。</span><span class="sxs-lookup"><span data-stu-id="e5342-124">An example would be to print a message.</span></span>|[<span data-ttu-id="e5342-125">指定中斷點動作</span><span class="sxs-lookup"><span data-stu-id="e5342-125">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)|  
|<span data-ttu-id="e5342-126">描述如何編輯中斷點的位置。</span><span class="sxs-lookup"><span data-stu-id="e5342-126">Describes how to edit the location of a breakpoint.</span></span>|[<span data-ttu-id="e5342-127">編輯中斷點位置</span><span class="sxs-lookup"><span data-stu-id="e5342-127">Edit a Breakpoint Location</span></span>](edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a><span data-ttu-id="e5342-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5342-128">See Also</span></span>  
 [<span data-ttu-id="e5342-129">Transact-SQL 偵錯工具資訊</span><span class="sxs-lookup"><span data-stu-id="e5342-129">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
