---
title: 以程式設計方式連線工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- constraints [Integration Services]
ms.assetid: 23668e88-cef4-4009-a9cf-38e607eab7a2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5aeeb70ed5741cc7372fdfc63e637fd53d932f91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594645"
---
# <a name="connecting-tasks-programmatically"></a><span data-ttu-id="a2544-102">以程式設計方式連接工作</span><span class="sxs-lookup"><span data-stu-id="a2544-102">Connecting Tasks Programmatically</span></span>
  <span data-ttu-id="a2544-103">在物件模型中由 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 類別表示的優先順序條件約束會建立 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 物件在封裝內執行的順序。</span><span class="sxs-lookup"><span data-stu-id="a2544-103">A precedence constraint, represented in the object model by the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> class, establishes the order in which <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects run in a package.</span></span> <span data-ttu-id="a2544-104">此優先順序條件約束可允許根據上一個工作或容器的執行結果來執行封裝中的容器和工作。</span><span class="sxs-lookup"><span data-stu-id="a2544-104">The precedence constraint allows the execution of the containers and tasks in a package to be dependent on the result of the execution of a previous task or container.</span></span> <span data-ttu-id="a2544-105">優先順序條件約束會在 <xref:Microsoft.SqlServer.Dts.Runtime.Executable> 物件配對之間建立，其方式是在容器物件上呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> 集合的 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> 方法。</span><span class="sxs-lookup"><span data-stu-id="a2544-105">Precedence constraints are established between pairs of <xref:Microsoft.SqlServer.Dts.Runtime.Executable> objects by calling the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints.Add%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraints> collection on the container object.</span></span> <span data-ttu-id="a2544-106">當您在兩個可執行物件之間建立條件約束時，您會設定 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> 屬性，以建立用來執行此條件約束內定義之第二個可執行物件的準則。</span><span class="sxs-lookup"><span data-stu-id="a2544-106">After you create a constraint between two executable objects, you set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> property to establish the criteria for executing the second executable defined in the constraint.</span></span>  
  
 <span data-ttu-id="a2544-107">您可以在單一優先順序條件約束內同時使用條件約束和運算式，這是根據您為 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A> 屬性指定的值而定，如下表所述：</span><span class="sxs-lookup"><span data-stu-id="a2544-107">You can use both a constraint and an expression in a single precedence constraint, depending on the value that you specify for the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.EvalOp%2A> property, as described in the following table:</span></span>  
  
|<span data-ttu-id="a2544-108">EvalOp 屬性的值</span><span class="sxs-lookup"><span data-stu-id="a2544-108">Value of the EvalOp property</span></span>|<span data-ttu-id="a2544-109">描述</span><span class="sxs-lookup"><span data-stu-id="a2544-109">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Constraint>|<span data-ttu-id="a2544-110">指定執行結果會決定是否執行受條件約束的容器或工作。</span><span class="sxs-lookup"><span data-stu-id="a2544-110">Specifies that the execution outcome determines whether the constrained container or task runs.</span></span> <span data-ttu-id="a2544-111">將 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 屬性設定為 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 列舉中所要的值。</span><span class="sxs-lookup"><span data-stu-id="a2544-111">Set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> to the desired value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> enumeration.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.Expression>|<span data-ttu-id="a2544-112">指定運算式的值會決定是否執行受條件約束的容器或工作。</span><span class="sxs-lookup"><span data-stu-id="a2544-112">Specifies that the value of an expression determines whether the constrained container or task runs.</span></span> <span data-ttu-id="a2544-113">設定 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a2544-113">Set the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionAndConstraint>|<span data-ttu-id="a2544-114">指定條件約束結果必須發生而且運算式必須評估，受條件約束的容器或工作才能執行。</span><span class="sxs-lookup"><span data-stu-id="a2544-114">Specifies that the constraint outcome must occur and the expression must evaluate for the constrained container or task to run.</span></span> <span data-ttu-id="a2544-115">設定 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 屬性，並且將其 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a2544-115">Set both the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> properties of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, and set its <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> property to `true`.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DTSPrecedenceEvalOp.ExpressionOrConstraint>|<span data-ttu-id="a2544-116">指定必須發生條件約束結果或者必須評估運算式，受條件約束的容器或工作才能執行。</span><span class="sxs-lookup"><span data-stu-id="a2544-116">Specifies that either the constraint outcome must occur, or the expression must evaluate, for the constrained container or task to run.</span></span> <span data-ttu-id="a2544-117">設定 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> 屬性，並且將其 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> 屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a2544-117">Set both the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Value%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.Expression%2A> properties of the <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>, and set its <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint.LogicalAnd%2A> property to `false`.</span></span>|  
  
 <span data-ttu-id="a2544-118">下列程式碼範例示範如何將兩個工作加入封裝中。</span><span class="sxs-lookup"><span data-stu-id="a2544-118">The following code sample demonstrates adding two tasks to a package.</span></span> <span data-ttu-id="a2544-119">在兩者之間建立了 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>，防止第二個工作在第一個工作完成以前執行。</span><span class="sxs-lookup"><span data-stu-id="a2544-119">A <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint> is created between them that prevents the second task from running until the first task finishes.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package p = new Package();  
  
      // Add a File System task.  
      Executable eFileTask1 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost1 = eFileTask1 as TaskHost;  
  
      // Add a second File System task.  
      Executable eFileTask2 = p.Executables.Add("STOCK:FileSystemTask");  
      TaskHost thFileHost2 = eFileTask2 as TaskHost;  
  
      // Put a precedence constraint between the tasks.  
      // Set the constraint to specify that the second File System task cannot run  
      // until the first File System task finishes.  
      PrecedenceConstraint pcFileTasks =   
        p.PrecedenceConstraints.Add((Executable)thFileHost1, (Executable)thFileHost2);  
      pcFileTasks.Value = DTSExecResult.Completion;  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim p As Package = New Package()  
    ' Add a File System task.  
    Dim eFileTask1 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost1 As TaskHost = CType(eFileTask1, TaskHost)  
  
    ' Add a second File System task.  
    Dim eFileTask2 As Executable = p.Executables.Add("STOCK:FileSystemTask")  
    Dim thFileHost2 As TaskHost = CType(eFileTask2, TaskHost)  
  
    ' Put a precedence constraint between the tasks.  
    ' Set the constraint to specify that the second File System task cannot run  
    ' until the first File System task finishes.  
    Dim pcFileTasks As PrecedenceConstraint = _  
      p.PrecedenceConstraints.Add(CType(thFileHost1, Executable), CType(thFileHost2, Executable))  
    pcFileTasks.Value = DTSExecResult.Completion  
  
  End Sub  
  
End Module  
```  
  
<span data-ttu-id="a2544-120">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="a2544-120">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a2544-121">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="a2544-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a2544-122">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="a2544-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a2544-123">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="a2544-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2544-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2544-124">See Also</span></span>  
 [<span data-ttu-id="a2544-125">以程式設計方式加入資料流程工作</span><span class="sxs-lookup"><span data-stu-id="a2544-125">Adding the Data Flow Task Programmatically</span></span>](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
  
  
