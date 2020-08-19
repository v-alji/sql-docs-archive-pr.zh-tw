---
title: 調試 CLR 資料庫物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 084b2494ec55b502f71154ca1f174a6de6d2ab70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584573"
---
# <a name="debugging-clr-database-objects"></a><span data-ttu-id="708d5-102">偵錯 CLR 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="708d5-102">Debugging CLR Database Objects</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="708d5-103">支援在資料庫中偵錯 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 和 Common Language Runtime (CLR) 物件。</span><span class="sxs-lookup"><span data-stu-id="708d5-103">provides support for debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="708d5-104">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中偵錯的關鍵層面是設定和使用的簡易性，以及 SQL Server 偵錯程式與 Microsoft Visual Studio 偵錯程式的整合。</span><span class="sxs-lookup"><span data-stu-id="708d5-104">The key aspects of debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are the ease of setup and use, and the integration of the SQL Server debugger with the Microsoft Visual Studio debugger.</span></span> <span data-ttu-id="708d5-105">此外，偵錯可跨語言運作。</span><span class="sxs-lookup"><span data-stu-id="708d5-105">Furthermore, debugging works across languages.</span></span> <span data-ttu-id="708d5-106">使用者可以從 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 順利地逐步執行 CLR 物件，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="708d5-106">Users can step seamlessly into CLR objects from [!INCLUDE[tsql](../../../includes/tsql-md.md)], and vice versa.</span></span> <span data-ttu-id="708d5-107">SQL Server Management Studio 中的 Transact-SQL 偵錯工具無法用於偵錯 Managed 資料庫物件，但您可以使用 Visual Studio 中的偵錯工具來偵錯物件。</span><span class="sxs-lookup"><span data-stu-id="708d5-107">The Transact-SQL debugger in SQL Server Management Studio cannot be used to debug managed database objects, but you can debug the objects by using the debuggers in Visual Studio.</span></span> <span data-ttu-id="708d5-108">在 Visual Studio 中的 Managed 資料物件支援所有通用偵錯功能，例如伺服器上執行之常式內的「逐步執行」和「不進入函數」陳述式。</span><span class="sxs-lookup"><span data-stu-id="708d5-108">Managed database object debugging in Visual Studio supports all common debugging features, such as "step into" and "step over" statements within routines executing on the server.</span></span> <span data-ttu-id="708d5-109">偵錯工具可在偵錯期間，設定中斷點、檢查呼叫堆疊，檢查變數，以及修改變數值。</span><span class="sxs-lookup"><span data-stu-id="708d5-109">Debuggers can set breakpoints, inspect the call stack, inspect variables, and modify variable values while debugging.</span></span> <span data-ttu-id="708d5-110">請注意，Visual Studio .NET 2003 無法用於 CLR 整合程式設計或偵錯。</span><span class="sxs-lookup"><span data-stu-id="708d5-110">Note that Visual Studio .NET 2003 cannot be used for CLR integration programming or debugging.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="708d5-111">包含預先安裝的 .NET Framework，而且 Visual Studio .NET 2003 無法使用 .NET Framework 2.0 組件。</span><span class="sxs-lookup"><span data-stu-id="708d5-111">includes the .NET Framework pre-installed, and Visual Studio .NET 2003 cannot use the .NET Framework 2.0 assemblies.</span></span>  
  
 <span data-ttu-id="708d5-112">如需使用 Visual Studio 來對 managed 程式碼進行偵錯工具的詳細資訊，請參閱 Visual Studio 檔中的「將[managed 程式碼調試](https://go.microsoft.com/fwlink/?LinkId=120377)程式」主題。</span><span class="sxs-lookup"><span data-stu-id="708d5-112">For more information about debugging managed code using Visual Studio, see the "[Debugging Managed Code](https://go.microsoft.com/fwlink/?LinkId=120377)" topic in the Visual Studio documentation.</span></span>  
  
## <a name="debugging-permissions-and-restrictions"></a><span data-ttu-id="708d5-113">偵錯使用權限及限制</span><span class="sxs-lookup"><span data-stu-id="708d5-113">Debugging Permissions and Restrictions</span></span>  
 <span data-ttu-id="708d5-114">偵錯工具是具有高度許可權的作業，因此只允許 **系統管理員（sysadmin** ）固定伺服器角色的成員在中執行此作業 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="708d5-114">Debugging is a highly privileged operation, and therefore only members of the **sysadmin** fixed server role are allowed to do so in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="708d5-115">偵錯時會套用下列限制：</span><span class="sxs-lookup"><span data-stu-id="708d5-115">The following restrictions apply while debugging:</span></span>  
  
-   <span data-ttu-id="708d5-116">偵錯 CLR 常式一次只限於一個偵錯工具執行個體。</span><span class="sxs-lookup"><span data-stu-id="708d5-116">Debugging CLR routines is restricted to one debugger instance at a time.</span></span> <span data-ttu-id="708d5-117">因為在叫用中斷點時，所有 CLR 程式碼執行都會凍結，在偵錯工具從中斷點繼續前進之前不會繼續執行，所以要套用此限制。</span><span class="sxs-lookup"><span data-stu-id="708d5-117">This limitation applies because all CLR code execution freezes when a break point is hit and execution does not continue until the debugger advances from the break point.</span></span> <span data-ttu-id="708d5-118">但是，您可以在其他連接中繼續偵錯 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="708d5-118">However, you can continue debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] in other connections.</span></span> <span data-ttu-id="708d5-119">雖然 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 偵錯不會凍結伺服器上的其他執行，但仍會因保留鎖定而讓其他連接等待。</span><span class="sxs-lookup"><span data-stu-id="708d5-119">Although [!INCLUDE[tsql](../../../includes/tsql-md.md)] debugging does not freeze other executions on the server, it could cause other connections to wait by holding a lock.</span></span>  
  
-   <span data-ttu-id="708d5-120">無法偵錯現有連接，只能偵錯新連接。這是因為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 需要用戶端及偵錯工具環境的詳細資訊，才能建立連接。</span><span class="sxs-lookup"><span data-stu-id="708d5-120">Existing connections cannot be debugged, only new connections, as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] requires information about the client and debugger environment before the connection can be made.</span></span>  
  
 <span data-ttu-id="708d5-121">由於上述限制，我們建議應在測試伺服器而不是生產伺服器上偵錯 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 和 CLR 程式碼。</span><span class="sxs-lookup"><span data-stu-id="708d5-121">Due to the above restrictions, we recommend that [!INCLUDE[tsql](../../../includes/tsql-md.md)] and CLR code be debugged on a test server, and not on a production server.</span></span>  
  
## <a name="overview-of-debugging-managed-database-objects"></a><span data-ttu-id="708d5-122">偵錯 Managed 資料庫物件的概觀</span><span class="sxs-lookup"><span data-stu-id="708d5-122">Overview of Debugging Managed Database Objects</span></span>  
 <span data-ttu-id="708d5-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的偵錯遵循每個連接模型。</span><span class="sxs-lookup"><span data-stu-id="708d5-123">Debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follows a per-connection model.</span></span> <span data-ttu-id="708d5-124">偵錯工具僅會偵測及偵錯其與用戶端之連接的活動。</span><span class="sxs-lookup"><span data-stu-id="708d5-124">A debugger can detect and debug activities only to the client connection to which it is attached.</span></span> <span data-ttu-id="708d5-125">因為偵錯工具的功能不受連接類型的限制，所以可以對表格式資料流 (TDS) 及 HTTP 連接進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="708d5-125">Because the functionality of the debugger is not limited by the type of connection, both tabular data stream (TDS) and HTTP connections can be debugged.</span></span> <span data-ttu-id="708d5-126">不過，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不允許偵錯現有的連接。</span><span class="sxs-lookup"><span data-stu-id="708d5-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not allow debugging existing connections.</span></span> <span data-ttu-id="708d5-127">偵錯支援在伺服器上執行的常式內的所有通用偵錯功能。</span><span class="sxs-lookup"><span data-stu-id="708d5-127">Debugging supports all common debugging features within routines executing on the server.</span></span> <span data-ttu-id="708d5-128">偵錯工具與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 可透過分散式元件物件模式 (COM) 進行互動。</span><span class="sxs-lookup"><span data-stu-id="708d5-128">The interaction between a debugger and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] happens through distributed Component Object Model (COM).</span></span>  
  
 <span data-ttu-id="708d5-129">如需有關調試 managed 預存程式、函數、觸發程式、使用者定義型別和匯總的詳細資訊和案例，請參閱 Visual Studio 檔中的「[SQL SERVER CLR 整合資料庫的調試](https://go.microsoft.com/fwlink/?LinkId=120378)程式」主題。</span><span class="sxs-lookup"><span data-stu-id="708d5-129">For more information and scenarios about debugging managed stored procedures, functions, triggers, user-defined types, and aggregates, see the "[SQL Server CLR Integration Database Debugging](https://go.microsoft.com/fwlink/?LinkId=120378)" topic in the Visual Studio documentation.</span></span>  
  
 <span data-ttu-id="708d5-130">必須在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上啟用 TCP/IP 網路通訊協定，才能針對遠端開發、偵錯和開發使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="708d5-130">The TCP/IP network protocol must be enabled on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in order to use Visual Studio for remote development, debugging, and development.</span></span> <span data-ttu-id="708d5-131">如需在伺服器上啟用 TCP/IP 通訊協定的詳細資訊，請參閱 [設定用戶端通訊](../../database-engine/configure-windows/configure-client-protocols.md)協定。</span><span class="sxs-lookup"><span data-stu-id="708d5-131">For more information about enabling TCP/IP protocol on the server, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
  
#### <a name="to-debug-a-managed-database-object"></a><span data-ttu-id="708d5-132">偵錯 Managed 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="708d5-132">To debug a managed database object</span></span>  
  
1.  <span data-ttu-id="708d5-133">開啟 Microsoft Visual Studio、建立新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專案，然後在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上建立資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="708d5-133">Open Microsoft Visual Studio, create a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] project, and establish a connection to a database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="708d5-134">建立新類型。</span><span class="sxs-lookup"><span data-stu-id="708d5-134">Create a new type.</span></span> <span data-ttu-id="708d5-135">在 **方案總管**中，以滑鼠右鍵按一下專案，然後選取 [ **加入** ] 和 [ **新增專案** ]。從 [ **加入新專案** ] 視窗中，選取 [ **預存**程式]、[ **使用者定義函數**]、[ **使用者定義類型**]、[ **觸發**程式]、[ **匯總**] 或 [ **類別**]</span><span class="sxs-lookup"><span data-stu-id="708d5-135">In **Solution Explorer**, right-click the project, select **Add** and **New Item...** From the **Add New Item** window, select **Stored Procedure**, **User-Defined Function**, **User-Defined Type**, **Trigger**, **Aggregate**, or **Class**.</span></span> <span data-ttu-id="708d5-136">指定新類型之來源檔案的名稱，然後按一下 [ **新增**]。</span><span class="sxs-lookup"><span data-stu-id="708d5-136">Specify a name for the source file of the new type and click **Add**.</span></span>  
  
3.  <span data-ttu-id="708d5-137">將新類型的程式碼加入至文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="708d5-137">Add code for the new type to the text editor.</span></span> <span data-ttu-id="708d5-138">如需範例預存程序的範例程式碼，請參閱本主題稍後的章節。</span><span class="sxs-lookup"><span data-stu-id="708d5-138">For sample code for an example stored procedure, see the section later in this topic.</span></span>  
  
4.  <span data-ttu-id="708d5-139">加入測試類型的指令碼。</span><span class="sxs-lookup"><span data-stu-id="708d5-139">Add a script that tests the type.</span></span> <span data-ttu-id="708d5-140">在 **方案總管**中，展開 [ **TestScripts** ] 目錄按兩下 [ **test** ] 以開啟預設測試腳本來源檔案。</span><span class="sxs-lookup"><span data-stu-id="708d5-140">In **Solution Explorer**, expand the **TestScripts** directory double-click **Test.sql** to open the default test script source file.</span></span> <span data-ttu-id="708d5-141">將叫用要偵錯之程式碼的測試指令碼加入至文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="708d5-141">Add the test script, one that invokes the code to be debugged, to the text editor.</span></span> <span data-ttu-id="708d5-142">如需範例指令碼，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="708d5-142">See below for a sample script.</span></span>  
  
5.  <span data-ttu-id="708d5-143">在原始程式碼中放置一或多個中斷點。</span><span class="sxs-lookup"><span data-stu-id="708d5-143">Place one or more breakpoints in the source code.</span></span> <span data-ttu-id="708d5-144">以滑鼠右鍵按一下文字編輯器中您要進行調試的函式或常式內的一行程式碼，然後選取 [ **中斷點** ] 和 [ **插入中斷點**]。</span><span class="sxs-lookup"><span data-stu-id="708d5-144">Right-click on a line of code in the text editor, within the function or routine you want to debug, and select **Breakpoint** and **Insert Breakpoint**.</span></span> <span data-ttu-id="708d5-145">中斷點隨即加入，程式碼行則以紅色反白顯示。</span><span class="sxs-lookup"><span data-stu-id="708d5-145">The breakpoint is added, highlighting the line of code in red.</span></span>  
  
6.  <span data-ttu-id="708d5-146">在 [ **調試** ] 功能表中，選取 [ **開始調試** ] 以編譯、部署和測試專案。</span><span class="sxs-lookup"><span data-stu-id="708d5-146">In the **Debug** menu, select **Start Debugging** to compile, deploy, and test the project.</span></span> <span data-ttu-id="708d5-147">Test.sql 中的測試指令碼將會執行，並會叫用 Managed 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="708d5-147">The test script in Test.sql will be run and the managed database object will be invoked.</span></span>  
  
7.  <span data-ttu-id="708d5-148">當中斷點出現表示指令指標的黃色箭頭時，程式碼執行會暫停，而您可以開始針錯 Managed 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="708d5-148">When the yellow arrow designating the instruction pointer appears at the breakpoint code execution pauses and you can begin debugging your managed database object.</span></span> <span data-ttu-id="708d5-149">您可以從 [**調試**程式] 功能表**逐步執行**，將指令指標前進至下一行程式碼。</span><span class="sxs-lookup"><span data-stu-id="708d5-149">You can **Step Over** from the **Debug** menu to advance the instruction pointer to the next line of code.</span></span> <span data-ttu-id="708d5-150">[ **區域變數** ] 視窗是用來觀察指令指標目前反白顯示之物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="708d5-150">The **Locals** window is used to observe the state of the objects currently highlighted by the instruction pointer.</span></span> <span data-ttu-id="708d5-151">變數可以加入至 [ **監看** 式] 視窗。</span><span class="sxs-lookup"><span data-stu-id="708d5-151">Variables can be added to the **Watch** window.</span></span> <span data-ttu-id="708d5-152">在整個偵錯工作階段中都可以觀察受監看變數的狀態，而不只是變數在程式碼行中由指令指標反白顯示時。</span><span class="sxs-lookup"><span data-stu-id="708d5-152">The state of watched variables can be observed throughout the entire debugging session, not only when the variable is in the line of code currently highlighted by instruction pointer.</span></span> <span data-ttu-id="708d5-153">從 [偵錯] 功能表選取 [繼續]，將指令指標前進至下一個中斷點，或者如果沒有中斷點了，就完成常式的執行。</span><span class="sxs-lookup"><span data-stu-id="708d5-153">Select Continue from the Debug menu to advance the instruction pointer to the next breakpoint or to complete execution of the routine if there are no more breakpoints.</span></span>  
  
### <a name="example"></a><span data-ttu-id="708d5-154">範例</span><span class="sxs-lookup"><span data-stu-id="708d5-154">Example</span></span>  
 <span data-ttu-id="708d5-155">下列範例會將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="708d5-155">The following example returns the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version to the caller.</span></span>  
  
 <span data-ttu-id="708d5-156">C#</span><span class="sxs-lookup"><span data-stu-id="708d5-156">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void GetVersion()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version",  
                                           connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="708d5-157">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="708d5-157">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Partial Public Class StoredProcedures   
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub GetVersion()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="708d5-158">下列的測試指令碼會叫用以上定義的 GetVersion 預存程序。</span><span class="sxs-lookup"><span data-stu-id="708d5-158">The following is a test script that invokes the GetVersion stored procedure defined above.</span></span>  
  
```  
EXEC GetVersion  
```  
  
## <a name="see-also"></a><span data-ttu-id="708d5-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="708d5-159">See Also</span></span>  
 [<span data-ttu-id="708d5-160">Common Language Runtime &#40;CLR&#41; 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="708d5-160">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
