---
title: 新增自訂工作中的偵錯支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BreakpointManager class
- breakpoints [Integration Services]
- custom tasks [Integration Services], debugging
- IDTSSuspend interface
- IDTSBreakpointSite interface
- SSIS custom tasks, debugging
- debugging [Integration Services], custom tasks
ms.assetid: 7f06e49b-0b60-4e81-97da-d32dc248264a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fcc1d0c18cd559b547eadb9c1fa77e8f143389d3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597229"
---
# <a name="adding-support-for-debugging-in-a-custom-task"></a><span data-ttu-id="5c7b8-102">新增自訂工作中的偵錯支援</span><span class="sxs-lookup"><span data-stu-id="5c7b8-102">Adding Support for Debugging in a Custom Task</span></span>
  <span data-ttu-id="5c7b8-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段引擎允許在執行期間，使用中斷點暫停封裝、工作和其他類型的容器。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine enables packages, tasks, and other types of containers to be suspended during execution by using breakpoints.</span></span> <span data-ttu-id="5c7b8-104">使用中斷點可讓您檢閱和修正妨礙應用程式或工作正確執行的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-104">The use of breakpoints lets you review and correct errors that prevent your application or tasks from running correctly.</span></span> <span data-ttu-id="5c7b8-105">中斷點架構可讓用戶端在定義的執行點暫停工作處理，以評估封裝中物件的執行階段值。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-105">The breakpoint architecture enables the client to evaluate the run-time value of objects in the package at defined points of execution while task processing is suspended.</span></span>  
  
 <span data-ttu-id="5c7b8-106">自訂工作開發人員可以使用 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 介面及其父介面 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend>，以利用此架構建立自訂中斷點目標。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-106">Custom task developers can use this architecture to create custom breakpoint targets by using the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface, and its parent interface, <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend>.</span></span> <span data-ttu-id="5c7b8-107"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 介面會定義執行階段引擎與工作之間的互動，以建立和管理自訂中斷點位置或目標。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-107">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface defines the interaction between the run-time engine and the task for creating and managing custom breakpoint sites or targets.</span></span> <span data-ttu-id="5c7b8-108"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 介面提供執行階段引擎呼叫的方法與屬性，通知工作暫停或是繼續其執行。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-108">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface provides methods and properties that are called by the run-time engine to notify the task to suspend or resume its execution.</span></span>  
  
 <span data-ttu-id="5c7b8-109">中斷點位置或目標是在工作執行中可以暫停處理的點。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-109">A breakpoint site or target is a point in the execution of the task where processing can be suspended.</span></span> <span data-ttu-id="5c7b8-110">使用者可以從 [設定中斷點]  對話方塊中的可用中斷點位置選取。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-110">Users select from available breakpoint sites in the **Set Breakpoints** dialog box.</span></span> <span data-ttu-id="5c7b8-111">例如，除了預設中斷點選項之外，[Foreach 迴圈容器] 提供 [在迴圈的每一次反覆運算開始時中斷] 選項。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-111">For example, in addition to the default breakpoint options, the Foreach Loop Container offers the "Break at the beginning of every iteration of the loop" option.</span></span>  
  
 <span data-ttu-id="5c7b8-112">當工作在執行期間到達中斷點目標時，它會評估中斷點目標以決定是否啟用中斷點。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-112">When a task reaches a breakpoint target during execution, it evaluates the breakpoint target to determine whether a breakpoint is enabled.</span></span> <span data-ttu-id="5c7b8-113">這指出使用者希望在該中斷點停止執行。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-113">This indicates that the user wants execution to stop at that breakpoint.</span></span> <span data-ttu-id="5c7b8-114">如果啟用中斷點，工作會將 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> 事件引發至執行階段引擎。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-114">If the breakpoint is enabled, the task raises the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> event to the run-time engine.</span></span> <span data-ttu-id="5c7b8-115">執行階段引擎會呼叫目前在封裝中執行的每項工作之 `Suspend` 方法以回應事件。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-115">The run-time engine responds to the event by calling the `Suspend` method of each task that is currently running in the package.</span></span> <span data-ttu-id="5c7b8-116">當執行階段呼叫已暫停工作的 `ResumeExecution` 方法時，工作執行會繼續。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-116">Execution of the task resumes when the runtime calls the `ResumeExecution` method of the suspended task.</span></span>  
  
 <span data-ttu-id="5c7b8-117">不使用中斷點的工作仍應實作 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 與 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 介面。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-117">Tasks that do not use breakpoints should still implement the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> and <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interfaces.</span></span> <span data-ttu-id="5c7b8-118">這可確保當封裝中的其他物件引發 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> 事件時，正確地暫停工作。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-118">This ensures that the task is suspended correctly when other objects in the package raise <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> events.</span></span>  
  
## <a name="idtsbreakpointsite-interface-and-breakpointmanager"></a><span data-ttu-id="5c7b8-119">IDTSBreakpointSite 介面與 BreakpointManager</span><span class="sxs-lookup"><span data-stu-id="5c7b8-119">IDTSBreakpointSite Interface and BreakpointManager</span></span>  
 <span data-ttu-id="5c7b8-120">工作透過呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.CreateBreakpointTarget%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> 方法，並提供整數識別碼和字串描述做為參數，以建立中斷點目標。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-120">Tasks create breakpoint targets by calling the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.CreateBreakpointTarget%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>, providing an integer ID and string description as parameters.</span></span> <span data-ttu-id="5c7b8-121">當工作到達其程式碼中包含中斷點目標的點時，它會使用 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.IsBreakpointTargetEnabled%2A> 方法評估中斷點目標，以判斷是否已啟用該中斷點。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-121">When the task reaches the point in its code that contains a breakpoint target, it evaluates the breakpoint target by using the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager.IsBreakpointTargetEnabled%2A> method to determine whether that breakpoint is enabled.</span></span> <span data-ttu-id="5c7b8-122">如果是 `true`，工作會引發 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A>事件，以通知執行階段引擎。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-122">If `true`, the task notifies the run-time engine by raising the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> event.</span></span>  
  
 <span data-ttu-id="5c7b8-123"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 介面會定義單一方法 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite.AcceptBreakpointManager%2A>，後者會由執行階段引擎於工作建立期間呼叫。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-123">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface defines a single method, <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite.AcceptBreakpointManager%2A>, which is called by the run-time engine during task creation.</span></span> <span data-ttu-id="5c7b8-124">這個方法會以參數形式提供 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> 物件，然後由工作使用該物件來建立並管理其中斷點。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-124">This method provides as a parameter the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> object, which is then used by the task to create and manage its breakpoints.</span></span> <span data-ttu-id="5c7b8-125">工作會在本機上儲存 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>，以供在 `Validate` 與 `Execute` 方法期間使用。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-125">Tasks should store the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> locally for use during the `Validate` and `Execute` methods.</span></span>  
  
 <span data-ttu-id="5c7b8-126">下列範例程式碼示範如何使用 <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager> 來建立中斷點目標。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-126">The following sample code demonstrates how to create a breakpoint target by using the <xref:Microsoft.SqlServer.Dts.Runtime.BreakpointManager>.</span></span> <span data-ttu-id="5c7b8-127">範例會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> 方法以引發事件。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-127">The sample calls the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents.OnBreakpointHit%2A> method to raise the event.</span></span>  
  
```csharp  
public void AcceptBreakpointManager( BreakpointManager breakPointManager )  
{  
   //   Store the breakpoint manager locally.  
   this.bpm  = breakPointManager;  
}  
public override DTSExecResult Execute( Connections connections,  
  Variables variables, IDTSComponentEvents events,  
  IDTSLogging log, DtsTransaction txn)  
{  
   //   Create a breakpoint.  
   this.bpm.CreateBreakPointTarget( 1 , "A sample breakpoint target." );  
...  
   if( this.bpm.IsBreakpointTargetEnabled( 1 ) == true )  
      events.OnBreakpointHit( this.bpm.GetBreakpointTarget( 1 ) );  
}  
```  
  
```vb  
Public Sub AcceptBreakpointManager(ByVal breakPointManager As BreakpointManager)  
  
   ' Store the breakpoint manager locally.  
   Me.bpm  = breakPointManager  
  
End Sub  
  
Public Overrides Function Execute(ByVal connections As Connections, _  
  ByVal variables As Variables, ByVal events As IDTSComponentEvents, _  
  ByVal log As IDTSLogging, ByVal txn As DtsTransaction) As DTSExecResult  
  
   ' Create a breakpoint.  
   Me.bpm.CreateBreakPointTarget(1 , "A sample breakpoint target.")  
  
   If Me.bpm.IsBreakpointTargetEnabled(1) = True Then  
      events.OnBreakpointHit(Me.bpm.GetBreakpointTarget(1))  
   End If  
  
End Function  
```  
  
## <a name="idtssuspend-interface"></a><span data-ttu-id="5c7b8-128">IDTSSuspend 介面</span><span class="sxs-lookup"><span data-stu-id="5c7b8-128">IDTSSuspend Interface</span></span>  
 <span data-ttu-id="5c7b8-129"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 介面會定義當執行階段引擎暫停或是繼續工作的執行時，該引擎呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-129">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface defines the methods that are called by the run-time engine when it pauses or resumes execution of a task.</span></span> <span data-ttu-id="5c7b8-130"><xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> 介面是由 <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> 介面實作，而且自訂工作通常會覆寫其 `Suspend` 與 `ResumeExecution` 方法。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-130">The <xref:Microsoft.SqlServer.Dts.Runtime.IDTSSuspend> interface is implemented by the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSBreakpointSite> interface, and its `Suspend` and `ResumeExecution` methods are usually overridden by the custom task.</span></span> <span data-ttu-id="5c7b8-131">當執行階段引擎從工作收到 `OnBreakpointHit` 事件時，它會呼叫每個執行中工作的 `Suspend` 方法，以通知工作暫停。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-131">When the run-time engine receives an `OnBreakpointHit` event from a task, it calls the `Suspend` method of each running task, notifying the tasks to pause.</span></span> <span data-ttu-id="5c7b8-132">當用戶端繼續執行時，執行階段引擎會呼叫已暫停工作的 `ResumeExecution` 方法。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-132">When the client resumes execution, the run-time engine calls the `ResumeExecution` method of the tasks that are suspended.</span></span>  
  
 <span data-ttu-id="5c7b8-133">暫停和繼續工作執行需要暫停和繼續工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-133">Suspending and resuming task execution involves pausing and resuming the task's execution thread.</span></span> <span data-ttu-id="5c7b8-134">在 Managed 程式碼中，您使用 .NET Framework 之 `ManualResetEvent` 命名空間中的 `System.Threading` 類別，來執行這項動作。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-134">In managed code, you do this using the `ManualResetEvent` class in `System.Threading` namespace of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5c7b8-135">下列程式碼範例示範工作執行的暫停與繼續。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-135">The following code sample demonstrates suspension and resumption of task execution.</span></span> <span data-ttu-id="5c7b8-136">請注意，`Execute` 方法和上一個程式碼範例不同，而且會在引發中斷點時暫停執行緒。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-136">Notice that the `Execute` method has changed from the previous code sample, and the execution thread is paused when firing the breakpoint.</span></span>  
  
```csharp  
private ManualResetEvent m_suspended = new ManualResetEvent( true );  
private ManualResetEvent m_canExecute = new ManualResetEvent( true );  
private int   m_suspendRequired = 0;  
private int   m_debugMode = 0;  
  
public override DTSExecResult Execute( Connections connections, Variables variables, IDTSComponentEvents events, IDTSLogging log, DtsTransaction txn)  
{  
   // While a task is not executing, it is suspended.    
   // Now that we are executing,  
   // change to not suspended.  
   ChangeEvent(m_suspended, false);  
  
   // Check for a suspend before doing any work,   
   // in case the suspend and execute calls  
   // were initiated at virtually the same time.  
   CheckAndSuspend();  
   CheckAndFireBreakpoint( componentEvents, 1);  
}  
private void CheckAndSuspend()  
{  
   // Loop until we can execute.    
   // The loop is required rather than a simple If  
   // because there is a time between the return from WaitOne and the  
   // reset that we might receive another Suspend call.    
   // Suspend() will see that we are suspended  
   // and return.  So we need to rewait.  
   while (!m_canExecute.WaitOne(0, false))  
   {  
      ChangeEvent(m_suspended, true);  
      m_canExecute.WaitOne();  
      ChangeEvent(m_suspended, false);  
   }  
}  
private void CheckAndFireBreakpoint(IDTSComponentEvents events, int breakpointID)  
{  
   // If the breakpoint is enabled, fire it.  
   if (m_debugMode != 0 &&    this.bpm.IsBreakpointTargetEnabled(breakpointID))  
   {  
      //   Enter a suspend mode before firing the breakpoint.    
      //   Firing the breakpoint will cause the runtime   
      //   to call Suspend on this task.    
      //   Because we are blocked on the breakpoint,   
      //   we are suspended.  
      ChangeEvent(m_suspended, true);  
      events.OnBreakpointHit(this.bpm.GetBreakpointTarget(breakpointID));  
      ChangeEvent(m_suspended, false);  
   }  
   // Check for a suspension for two reasons:   
   //   1. If we are at a point where we could fire a breakpoint,   
   //      we are at a valid suspend point.  Even if we didn't hit a  
   //      breakpoint, the runtime may have called suspend,   
   //      so check for it.       
   //   2. Between the return from OnBreakpointHit   
   //      and the reset of the event, it is possible to have  
   //      received a suspend call from which we returned because   
   //      we were already suspended.  We need to be sure it is okay  
   //      to continue executing now.  
   CheckAndSuspend();  
}  
static void ChangeEvent(ManualResetEvent e, bool shouldSet)  
{  
   bool succeeded;  
   if (shouldSet)  
      succeeded = e.Set();  
   else  
      succeeded = e.Reset();  
  
   if (!succeeded)  
      throw new Exception("Synchronization object failed.");  
  
}  
public bool SuspendRequired  
{  
   get   {return m_suspendRequired != 0;}  
   set  
   {  
      // This lock is also taken by Suspend().    
      // Because it is possible for the package to be  
      // suspended and resumed in quick succession,   
      // this property might be set before  
      // the actual Suspend() call.    
      // Without the lock, the Suspend() might reset the canExecute  
      // event after we set it to abort the suspension.  
      lock (this)  
      {  
         Interlocked.Exchange(ref m_suspendRequired, value ? 1 : 0);  
         if (!value)  
            ResumeExecution();  
      }  
   }  
}  
public void ResumeExecution()  
{  
   ChangeEvent( m_canExecute,true );  
}  
public void Suspend()  
{  
   // This lock is also taken by the set SuspendRequired method.    
   // It prevents this call from overriding an   
   // aborted suspension.  See comments in set SuspendRequired.  
   lock (this)  
   {  
      // If a Suspend is required, do it.  
      if (m_suspendRequired != 0)  
         ChangeEvent(m_canExecute, false);  
   }  
   // We can't return from Suspend until the task is "suspended".  
   // This can happen one of two ways:   
   // the m_suspended event occurs, indicating that the execute thread  
   // has suspended, or the canExecute flag is set,   
   // indicating that a suspend is no longer required.  
   WaitHandle [] suspendOperationComplete = {m_suspended, m_canExecute};  
   WaitHandle.WaitAny(suspendOperationComplete);  
}  
```  
  
```vb  
Private m_suspended As ManualResetEvent = New ManualResetEvent(True)  
Private m_canExecute As ManualResetEvent = New ManualResetEvent(True)  
Private m_suspendRequired As Integer = 0  
Private m_debugMode As Integer = 0  
  
Public Overrides Function Execute(ByVal connections As Connections, _  
ByVal variables As Variables, ByVal events As IDTSComponentEvents, _  
ByVal log As IDTSLogging, ByVal txn As DtsTransaction) As DTSExecResult  
  
   ' While a task is not executing it is suspended.    
   ' Now that we are executing,  
   ' change to not suspended.  
   ChangeEvent(m_suspended, False)  
  
   ' Check for a suspend before doing any work,   
   ' in case the suspend and execute calls  
   ' were initiated at virtually the same time.  
   CheckAndSuspend()  
   CheckAndFireBreakpoint(componentEvents, 1)  
  
End Function  
  
Private Sub CheckAndSuspend()  
  
   ' Loop until we can execute.    
   ' The loop is required rather than a simple if  
   ' because there is a time between the return from WaitOne and the  
   ' reset that we might receive another Suspend call.    
   ' Suspend() will see that we are suspended  
   ' and return.  So we need to rewait.  
   Do While Not m_canExecute.WaitOne(0, False)  
              ChangeEvent(m_suspended, True)  
              m_canExecute.WaitOne()  
              ChangeEvent(m_suspended, False)  
   Loop  
  
End Sub  
  
Private Sub CheckAndFireBreakpoint(ByVal events As IDTSComponentEvents, _  
ByVal breakpointID As Integer)  
  
   ' If the breakpoint is enabled, fire it.  
   If m_debugMode <> 0 AndAlso Me.bpm.IsBreakpointTargetEnabled(breakpointID) Then  
              '   Enter a suspend mode before firing the breakpoint.    
              '   Firing the breakpoint will cause the runtime   
              '   to call Suspend on this task.    
              '   Because we are blocked on the breakpoint,   
              '   we are suspended.  
              ChangeEvent(m_suspended, True)  
              events.OnBreakpointHit(Me.bpm.GetBreakpointTarget(breakpointID))  
              ChangeEvent(m_suspended, False)  
   End If  
  
   ' Check for a suspension for two reasons:   
   '   1. If we are at a point where we could fire a breakpoint,   
   '         we are at a valid suspend point.  Even if we didn't hit a  
   '         breakpoint, the runtime may have called suspend,   
   '         so check for it.     
   '   2. Between the return from OnBreakpointHit   
   '         and the reset of the event, it is possible to have  
   '         received a suspend call from which we returned because   
   '         we were already suspended.  We need to be sure it is okay  
   '         to continue executing now.  
   CheckAndSuspend()  
  
End Sub  
  
Shared Sub ChangeEvent(ByVal e As ManualResetEvent, ByVal shouldSet As Boolean)  
  
   Dim succeeded As Boolean  
   If shouldSet Then  
              succeeded = e.Set()  
   Else  
              succeeded = e.Reset()  
   End If  
  
   If (Not succeeded) Then  
              Throw New Exception("Synchronization object failed.")  
   End If  
  
End Sub  
  
Public Property SuspendRequired() As Boolean  
   Get  
               Return m_suspendRequired <> 0  
  End Get  
  Set  
    ' This lock is also taken by Suspend().    
     '   Because it is possible for the package to be  
     '   suspended and resumed in quick succession,   
     '   this property might be set before  
     '   the actual Suspend() call.    
     '   Without the lock, the Suspend() might reset the canExecute  
     '   event after we set it to abort the suspension.  
              SyncLock Me  
                         Interlocked.Exchange(m_suspendRequired,IIf(Value, 1, 0))  
                         If (Not Value) Then  
                                    ResumeExecution()  
                         End If  
              End SyncLock  
   End Set  
End Property  
  
Public Sub ResumeExecution()  
   ChangeEvent(m_canExecute,True)  
End Sub  
  
Public Sub Suspend()  
  
   ' This lock is also taken by the set SuspendRequired method.    
   ' It prevents this call from overriding an   
   ' aborted suspension.  See comments in set SuspendRequired.  
   SyncLock Me  
   ' If a Suspend is required, do it.  
              If m_suspendRequired <> 0 Then  
                         ChangeEvent(m_canExecute, False)  
              End If  
   End SyncLock  
   ' We can't return from Suspend until the task is "suspended".  
   ' This can happen one of two ways:   
   ' the m_suspended event occurs, indicating that the execute thread  
   ' has suspended, or the canExecute flag is set,   
   ' indicating that a suspend is no longer required.  
   Dim suspendOperationComplete As WaitHandle() = {m_suspended, m_canExecute}  
   WaitHandle.WaitAny(suspendOperationComplete)  
  
End Sub  
```  
  
<span data-ttu-id="5c7b8-137">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="5c7b8-137">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5c7b8-138">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="5c7b8-138">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5c7b8-139">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="5c7b8-139">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5c7b8-140">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="5c7b8-140">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c7b8-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c7b8-141">See Also</span></span>  
 [<span data-ttu-id="5c7b8-142">偵錯控制流程</span><span class="sxs-lookup"><span data-stu-id="5c7b8-142">Debugging Control Flow</span></span>](../../troubleshooting/debugging-control-flow.md)  
  
  
