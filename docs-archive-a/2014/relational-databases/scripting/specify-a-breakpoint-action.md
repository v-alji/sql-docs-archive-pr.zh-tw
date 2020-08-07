---
title: 指定中斷點動作
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint action
- Transact-SQL debugger, breakpoint when hit action
ms.assetid: f97f0097-6f51-40c1-b2e0-294a93ce1e1b
author: rothja
ms.author: jroth
ms.openlocfilehash: 57b3c445e738752400e716538e038349e04e7bd2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596625"
---
# <a name="specify-a-breakpoint-action"></a><span data-ttu-id="0c9fb-102">指定中斷點動作</span><span class="sxs-lookup"><span data-stu-id="0c9fb-102">Specify a Breakpoint Action</span></span>
  <span data-ttu-id="0c9fb-103">中斷點 [叫用時]  動作指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具針對中斷點所執行的自訂工作。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-103">A breakpoint **When Hit** action specifies a custom task that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger performs for a breakpoint.</span></span> <span data-ttu-id="0c9fb-104">如果已到達指定的叫用計數而且滿足任何指定的中斷點條件時，偵錯工具就會執行為中斷點指定的動作。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
##  <a name="action-considerations"></a><a name="BKMK_ActionConsiderations"></a> <span data-ttu-id="0c9fb-105">動作考量因素</span><span class="sxs-lookup"><span data-stu-id="0c9fb-105">Action Considerations</span></span>  
 <span data-ttu-id="0c9fb-106">中斷點的預設動作是在已滿足叫用計數和中斷點條件時中斷執行。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-106">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="0c9fb-107">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具中 [叫用時] 動作的主要用法是透過指定列印訊息，將資訊列印至偵錯工具 [輸出] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-107">The primary use of a **When Hit** action in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger is to instead print information to the debugger **Output** window by specifying a print message.</span></span>  
  
 <span data-ttu-id="0c9fb-108">列印訊息是在 [列印訊息]  選項中指定，並指定為文字字串，其中的運算式包含來自偵錯中 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的資訊。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-108">A print message is specified in the **Print a Message** option, and is specified as a text string that includes expressions containing information from the [!INCLUDE[tsql](../../includes/tsql-md.md)] being debugged.</span></span> <span data-ttu-id="0c9fb-109">運算式包含：</span><span class="sxs-lookup"><span data-stu-id="0c9fb-109">Expressions include:</span></span>  
  
-   <span data-ttu-id="0c9fb-110">以大括號 ({}) 括住的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-110">A [!INCLUDE[tsql](../../includes/tsql-md.md)] expression contained in curly braces ({}).</span></span> <span data-ttu-id="0c9fb-111">運算式可以包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 變數、參數和內建函數。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-111">The expressions can include [!INCLUDE[tsql](../../includes/tsql-md.md)] variables, parameters, and built-in functions.</span></span> <span data-ttu-id="0c9fb-112">範例包括 {@MyVariable}、{@NameParameter}、{@@SPID} 或 {SERVERPROPERTY('ProcessID')}。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-112">Examples include {@MyVariable}, {@NameParameter}, {@@SPID}, or {SERVERPROPERTY('ProcessID')}.</span></span>  
  
-   <span data-ttu-id="0c9fb-113">下列其中一個關鍵字：</span><span class="sxs-lookup"><span data-stu-id="0c9fb-113">One of the following keywords:</span></span>  
  
    1.  <span data-ttu-id="0c9fb-114">$ADDRESS 傳回設定中斷點之預存程序或使用者定義函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-114">$ADDRESS returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="0c9fb-115">如果中斷點是在編輯器視窗中設定，$ADDRESS 會傳回編輯中指令碼檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-115">If the breakpoint is set in the editor window, $ADDRESS returns the name of the script file being edited.</span></span> <span data-ttu-id="0c9fb-116">$ADDRESS 和 $FUNCTION 會在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具中傳回相同資訊。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-116">$ADDRESS and $FUNCTION return the same information in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
    2.  <span data-ttu-id="0c9fb-117">$CALLER 傳回呼叫預存程序或函數之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼單元的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-117">$CALLER returns the name of the unit of [!INCLUDE[tsql](../../includes/tsql-md.md)] code that called a stored procedure or function.</span></span> <span data-ttu-id="0c9fb-118">如果中斷點是在編輯器視窗中，$CALLER 會傳回 \<No caller available> 。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-118">If the breakpoint is in the editor window, $CALLER returns \<No caller available>.</span></span> <span data-ttu-id="0c9fb-119">如果中斷點是在編輯器視窗中程式碼所呼叫的預存程序或使用者定義函數中，$CALLER 會傳回編輯中檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-119">If the breakpoint is in a stored procedure or user-defined function called from the code in the editor window, $CALLER returns the name of the file being edited.</span></span> <span data-ttu-id="0c9fb-120">如果中斷點是在另一個預存程序或函數所呼叫的預存程序或使用者定義函數中，$CALLER 會傳回呼叫程序或函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-120">If the breakpoint is in a stored procedure or user-defined function called from another stored procedure or function, $CALLER returns the name of the calling procedure or function.</span></span>  
  
    3.  <span data-ttu-id="0c9fb-121">$CALLSTACK 傳回鏈結中呼叫目前預存程序或使用者定義函數之函數的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-121">$CALLSTACK returns the call stack of functions in the chain that called the current stored procedure or user-defined function.</span></span> <span data-ttu-id="0c9fb-122">如果中斷點是在編輯器視窗中，$CALLSTACK 會傳回編輯中指令碼檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-122">If the breakpoint is in the editor window, $CALLSTACK returns the name of the script file being edited.</span></span>  
  
    4.  <span data-ttu-id="0c9fb-123">$FUNCTION 傳回設定中斷點之預存程序或使用者定義函數的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-123">$FUNCTION returns the name of the stored procedure or user-defined function where the breakpoint is set.</span></span> <span data-ttu-id="0c9fb-124">如果中斷點是在編輯器視窗中設定，$FUNCTION 會傳回編輯中指令碼檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-124">If the breakpoint is set in the editor window, $FUNCTION returns the name of the script file being edited.</span></span>  
  
    5.  <span data-ttu-id="0c9fb-125">$PID 與 $PNAME 會傳回執行 Database Engine 執行個體且執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 之作業系統處理序的識別碼及名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-125">$PID and $PNAME return the ID and name of the operating system process running the instance of the Database Engine where the [!INCLUDE[tsql](../../includes/tsql-md.md)] is running.</span></span> <span data-ttu-id="0c9fb-126">$PID 和 SERVERPROPERTY('ProcessID') 傳回相同的識別碼，不同之處在於 $PID 是十六進位值，而 SERVERPROPERTY('ProcessID') 是十進位值。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-126">$PID returns the same ID as SERVERPROPERTY('ProcessID'), except that $PID is a hexadecimal value while SERVERPROPERTY('ProcessID') is a decimal value.</span></span>  
  
    6.  <span data-ttu-id="0c9fb-127">$TID 與 $TNAME 會傳回執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批次之作業系統執行緒的識別碼及名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-127">$TID and $TNAME return the ID and name of the operating system thread running the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch.</span></span> <span data-ttu-id="0c9fb-128">執行緒與執行 Database Engine 執行個體的處理序相關聯。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-128">The thread is one associated with the process running the instance of the Database Engine.</span></span> <span data-ttu-id="0c9fb-129">$TID 與 SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID 傳回相同的值，不同之處在於 $TID 是十六進位值，而 kpid 是十進位值。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-129">$TID returns the same value as SELECT kpid FROM sys.sysprocesses WHERE spid = @@SPID, except that $TID is a hexadecimal value while kpid is a decimal value.</span></span>  
  
-   <span data-ttu-id="0c9fb-130">您也可以使用反斜線字元 (\\) 當做逸出字元，允許在訊息中使用大括號和反斜線： \\{、 \\} 和 \\\\。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-130">You can also use the backslash character (\\) as an escape character to allow curly braces and backslashes in the message: \\{, \\}, and \\\\.</span></span>  
  
#### <a name="to-specify-a-when-hit-action"></a><span data-ttu-id="0c9fb-131">若要指定叫用時動作</span><span class="sxs-lookup"><span data-stu-id="0c9fb-131">To Specify a When Hit Action</span></span>  
  
1.  <span data-ttu-id="0c9fb-132">在編輯器視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [叫用時]  。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-132">In the editor window, right-click the breakpoint glyph, and then click **When Hit** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="0c9fb-133">-或-</span><span class="sxs-lookup"><span data-stu-id="0c9fb-133">-or-</span></span>  
  
     <span data-ttu-id="0c9fb-134">在 [中斷點]  視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [叫用時]  。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-134">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **When hit** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="0c9fb-135">在 [叫用中斷點時]  對話方塊中，選取所要的行為：</span><span class="sxs-lookup"><span data-stu-id="0c9fb-135">In the **When Breakpoint Is Hit** dialog box, select the behavior you want:</span></span>  
  
    1.  <span data-ttu-id="0c9fb-136">選取 [列印訊息]  ，以便在叫用中斷點時，在偵錯工具的 [輸出] 視窗中列印訊息。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-136">Select **Print a Message** to print a message in the debugger Output window when the breakpoint is hit.</span></span>  
  
    2.  <span data-ttu-id="0c9fb-137">[執行巨集]  選項無法在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具中使用，會呈現灰色。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-137">The **Run a Macro** option is not available from the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, and is greyed out.</span></span>  
  
    3.  <span data-ttu-id="0c9fb-138">如果不要讓中斷點暫停執行，請選取 [繼續執行]  。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-138">Select **Continue execution** if you do not want the breakpoint to pause execution.</span></span> <span data-ttu-id="0c9fb-139">只有當您選取了 [列印訊息]  選項時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-139">This option is active only if you have selected the **Print a Message** option.</span></span>  
  
3.  <span data-ttu-id="0c9fb-140">按一下 **[確定]** 實作變更，或按一下 **[取消]** 結束而不套用變更。</span><span class="sxs-lookup"><span data-stu-id="0c9fb-140">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c9fb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c9fb-141">See Also</span></span>  
 <span data-ttu-id="0c9fb-142">[指定中斷點條件](specify-a-breakpoint-condition.md) </span><span class="sxs-lookup"><span data-stu-id="0c9fb-142">[Specify a Breakpoint Condition](specify-a-breakpoint-condition.md) </span></span>  
 [<span data-ttu-id="0c9fb-143">指定叫用計數</span><span class="sxs-lookup"><span data-stu-id="0c9fb-143">Specify a Hit Count</span></span>](specify-a-hit-count.md)  
