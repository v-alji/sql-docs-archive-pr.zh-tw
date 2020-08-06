---
title: 指定中斷點篩選條件
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
author: rothja
ms.author: jroth
ms.openlocfilehash: 9fc320397da1bddc0d28191c359c4d311b23e044
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596622"
---
# <a name="specify-a-breakpoint-filter"></a><span data-ttu-id="a0409-102">指定中斷點篩選條件</span><span class="sxs-lookup"><span data-stu-id="a0409-102">Specify a Breakpoint Filter</span></span>
  <span data-ttu-id="a0409-103">中斷點篩選條件會限制中斷點只能在指定的電腦、作業系統處理序和執行緒上運作。</span><span class="sxs-lookup"><span data-stu-id="a0409-103">A breakpoint filter limits the breakpoint to acting only on specified computers, operating system processes, and threads.</span></span> <span data-ttu-id="a0409-104">中斷點篩選條件通常是在偵錯平行應用程式時使用。</span><span class="sxs-lookup"><span data-stu-id="a0409-104">Breakpoint filters are typically used when debugging parallel applications.</span></span>  
  
##  <a name="filter-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="a0409-105">篩選考量</span><span class="sxs-lookup"><span data-stu-id="a0409-105">Filter Considerations</span></span>  
 <span data-ttu-id="a0409-106">中斷點篩選條件通常不會搭配 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具使用，因為 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼和預存程序不是平行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0409-106">Breakpoint filters are not typically used with the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger because [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and stored procedures are not parallel applications.</span></span>  
  
#### <a name="to-specify-a-breakpoint-filter"></a><span data-ttu-id="a0409-107">若要指定中斷點篩選條件</span><span class="sxs-lookup"><span data-stu-id="a0409-107">To Specify a Breakpoint Filter</span></span>  
  
1.  <span data-ttu-id="a0409-108">在編輯器視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [篩選]  。</span><span class="sxs-lookup"><span data-stu-id="a0409-108">In the editor window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="a0409-109">-或-</span><span class="sxs-lookup"><span data-stu-id="a0409-109">-or-</span></span>  
  
     <span data-ttu-id="a0409-110">在 [中斷點]  視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [篩選]  。</span><span class="sxs-lookup"><span data-stu-id="a0409-110">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Filter** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="a0409-111">在 [中斷點篩選條件]  對話方塊中，使用 [篩選]  方塊來指定電腦 (依名稱) 或作業系統處理序和執行緒 (依名稱或識別碼)：</span><span class="sxs-lookup"><span data-stu-id="a0409-111">In the **Breakpoint Filters** dialog box, use the **Filter** box to specify computers by name, or operating system processes and threads by either name or ID number:</span></span>  
  
    -   <span data-ttu-id="a0409-112">`MachineName` 是執行 Database Engine 執行個體的電腦。</span><span class="sxs-lookup"><span data-stu-id="a0409-112">`MachineName` is the computer running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="a0409-113">`ProcessID` 和 `ProcessName` 是執行 Database Engine 執行個體的作業系統處理序。</span><span class="sxs-lookup"><span data-stu-id="a0409-113">`ProcessID`, and `ProcessName` are the operating system process running the instance of the Database Engine.</span></span>  
  
    -   <span data-ttu-id="a0409-114">`ThreadID` 和 `ThreadName` 是在 Database Engine 執行個體中執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次、程序或函數的作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="a0409-114">`ThreadID` and `ThreadName` are the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch, procedure, or function in the instance of the Database Engine.</span></span>  
  
3.  <span data-ttu-id="a0409-115">按一下 **[確定]** 實作變更，或按一下 **[取消]** 結束而不套用變更。</span><span class="sxs-lookup"><span data-stu-id="a0409-115">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0409-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0409-116">See Also</span></span>  
 <span data-ttu-id="a0409-117">[指定中斷點條件](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="a0409-117">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 <span data-ttu-id="a0409-118">[指定叫用計數](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="a0409-118">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="a0409-119">指定中斷點動作</span><span class="sxs-lookup"><span data-stu-id="a0409-119">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
