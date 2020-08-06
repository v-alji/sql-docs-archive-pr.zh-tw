---
title: 以程式設計方式載入和執行本機套件 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a29faf623c02fea4fd8722c235f595f0fe4492e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687957"
---
# <a name="loading-and-running-a-local-package-programmatically"></a><span data-ttu-id="5f397-102">以程式設計的方式載入和執行本機封裝</span><span class="sxs-lookup"><span data-stu-id="5f397-102">Loading and Running a Local Package Programmatically</span></span>
  <span data-ttu-id="5f397-103">您可以使用[執行套件](../packages/run-integration-services-ssis-packages.md)中所述的方法，視需要或是依預定的次數執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 套件。</span><span class="sxs-lookup"><span data-stu-id="5f397-103">You can run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages as needed or at predetermined times by using the methods described in [Running Packages](../packages/run-integration-services-ssis-packages.md).</span></span> <span data-ttu-id="5f397-104">然而，只需要幾行的程式碼，您就可以從 Windows Form 應用程式、主控台應用程式、ASP.NET Web 表單或 Web 服務，或是 Windows 服務等自訂應用程式執行封裝。</span><span class="sxs-lookup"><span data-stu-id="5f397-104">However, with only a few lines of code, you can also run a package from a custom application such as a Windows Forms application, a console application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
 <span data-ttu-id="5f397-105">此主題會討論：</span><span class="sxs-lookup"><span data-stu-id="5f397-105">This topic discusses:</span></span>  
  
-   <span data-ttu-id="5f397-106">以程式設計方式載入封裝</span><span class="sxs-lookup"><span data-stu-id="5f397-106">Loading a package programmatically</span></span>  
  
-   <span data-ttu-id="5f397-107">以程式設計方式執行封裝</span><span class="sxs-lookup"><span data-stu-id="5f397-107">Running a package programmatically</span></span>  
  
 <span data-ttu-id="5f397-108">本主題中用以載入和執行封裝的所有方法，都需要 `Microsoft.SqlServer.ManagedDTS` 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5f397-108">All of the methods used in this topic to load and run packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="5f397-109">在新專案中加入參考之後，請使用 `using` 或 `Imports` 陳述式匯入 <xref:Microsoft.SqlServer.Dts.Runtime> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="5f397-109">After adding the reference in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
## <a name="loading-a-package-programmatically"></a><span data-ttu-id="5f397-110">以程式設計方式載入封裝</span><span class="sxs-lookup"><span data-stu-id="5f397-110">Loading a Package Programmatically</span></span>  
 <span data-ttu-id="5f397-111">無論封裝儲存在本機或遠端，如果要在本機電腦上以程式設計方式載入封裝，請呼叫下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="5f397-111">To load a package programmatically on the local computer, whether the package is stored locally or remotely, call one of the following methods:</span></span>  
  
|<span data-ttu-id="5f397-112">儲存位置</span><span class="sxs-lookup"><span data-stu-id="5f397-112">Storage Location</span></span>|<span data-ttu-id="5f397-113">要呼叫的方法</span><span class="sxs-lookup"><span data-stu-id="5f397-113">Method to Call</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="5f397-114">檔案</span><span class="sxs-lookup"><span data-stu-id="5f397-114">File</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|<span data-ttu-id="5f397-115">SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="5f397-115">SSIS Package Store</span></span>|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5f397-116">搭配 SSIS 封裝存放區使用之 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別的方法，僅支援 "."、localhost 或本機伺服器的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="5f397-116">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store only support ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="5f397-117">您無法使用 "(local)"。</span><span class="sxs-lookup"><span data-stu-id="5f397-117">You cannot use "(local)".</span></span>  
  
## <a name="running-a-package-programmatically"></a><span data-ttu-id="5f397-118">以程式設計方式執行封裝</span><span class="sxs-lookup"><span data-stu-id="5f397-118">Running a Package Programmatically</span></span>  
 <span data-ttu-id="5f397-119">在本機電腦上執行封裝的 Managed 程式碼中開發自訂應用程式需要下列方法。</span><span class="sxs-lookup"><span data-stu-id="5f397-119">Developing a custom application in managed code that runs a package on the local computer requires the following approach.</span></span> <span data-ttu-id="5f397-120">接下來的範例主控台應用程式中將示範此處摘要的步驟。</span><span class="sxs-lookup"><span data-stu-id="5f397-120">The steps summarized here are demonstrated in the sample console application that follows.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a><span data-ttu-id="5f397-121">以程式設計的方式在本機電腦上執行封裝</span><span class="sxs-lookup"><span data-stu-id="5f397-121">To run a package on the local computer programmatically</span></span>  
  
1.  <span data-ttu-id="5f397-122">啟動 Visual Studio 開發環境，並以慣用的開發語言建立新應用程式。</span><span class="sxs-lookup"><span data-stu-id="5f397-122">Start the Visual Studio development environment, and create a new application in your preferred development language.</span></span> <span data-ttu-id="5f397-123">此範例使用主控台應用程式，不過，您也可以從 Windows Form 應用程式、ASP.NET Web 表單或 Web 服務或是 Windows 服務執行封裝。</span><span class="sxs-lookup"><span data-stu-id="5f397-123">This example uses a console application; however you can also run a package from a Windows Forms application, an ASP.NET Web form or Web service, or a Windows service.</span></span>  
  
2.  <span data-ttu-id="5f397-124">在 [專案]  功能表上，按一下 [新增參考]  ，然後新增 **Microsoft.SqlServer.ManagedDTS.dll** 的參考。</span><span class="sxs-lookup"><span data-stu-id="5f397-124">On the **Project** menu, click **Add Reference** and add a reference to **Microsoft.SqlServer.ManagedDTS.dll**.</span></span> <span data-ttu-id="5f397-125">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5f397-125">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="5f397-126">請使用 Visual Basic `Imports` 語句或 c # `using` 語句來匯入**Microsoft. SqlServer. （運行**時間）命名空間。</span><span class="sxs-lookup"><span data-stu-id="5f397-126">Use the Visual Basic `Imports` statement or the C# `using` statement to import the **Microsoft.SqlServer.Dts.Runtime** namespace.</span></span>  
  
4.  <span data-ttu-id="5f397-127">在主常式中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f397-127">Add the following code in the main routine.</span></span> <span data-ttu-id="5f397-128">完成的主控台應用程式應類似下列範例。</span><span class="sxs-lookup"><span data-stu-id="5f397-128">The completed console application should look like the following example.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5f397-129">範例程式碼會透過使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> 方法示範從檔案系統載入封裝。</span><span class="sxs-lookup"><span data-stu-id="5f397-129">The sample code demonstrates loading the package from the file system by using the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> method.</span></span> <span data-ttu-id="5f397-130">不過，您也可以呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> 方法從 MSDB 資料庫載入封裝，或是呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> 方法從 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝存放區載入封裝。</span><span class="sxs-lookup"><span data-stu-id="5f397-130">However you can also load the package from the MSDB database by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> method, or from the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package store by calling the <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> method.</span></span>  
  
5.  <span data-ttu-id="5f397-131">執行專案。</span><span class="sxs-lookup"><span data-stu-id="5f397-131">Run the project.</span></span> <span data-ttu-id="5f397-132">範例程式碼會執行隨 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 範例安裝的 CalculatedColumns 範例封裝。</span><span class="sxs-lookup"><span data-stu-id="5f397-132">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="5f397-133">封裝執行的結果會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="5f397-133">The result of package execution is displayed in the console window.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="5f397-134">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="5f397-134">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a><span data-ttu-id="5f397-135">從執行封裝擷取事件</span><span class="sxs-lookup"><span data-stu-id="5f397-135">Capturing Events from a Running Package</span></span>  
 <span data-ttu-id="5f397-136">當您以程式設計方式執行封裝 (如前面的範例所示)，可能也會想要擷取當封裝執行時所發生的錯誤及其他事件。</span><span class="sxs-lookup"><span data-stu-id="5f397-136">When you run a package programmatically as shown in the preceding sample, you may also want to capture errors and other events that occur as the package executes.</span></span> <span data-ttu-id="5f397-137">您可以藉由加入從 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 類別繼承的類別，以及藉由在載入封裝時將參考傳遞給該類別，來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="5f397-137">You can accomplish this by adding a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class, and by passing a reference to that class when you load the package.</span></span> <span data-ttu-id="5f397-138">雖然下列範例只會擷取 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> 事件，不過 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 類別可讓您擷取更多其他事件。</span><span class="sxs-lookup"><span data-stu-id="5f397-138">Although the following example captures only the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> event, there are many other events that the <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> class lets you capture.</span></span>  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a><span data-ttu-id="5f397-139">以程式設計的方式在本機電腦上執行封裝並擷取封裝事件</span><span class="sxs-lookup"><span data-stu-id="5f397-139">To run a package on the local computer programmatically and capture package events</span></span>  
  
1.  <span data-ttu-id="5f397-140">遵循上述範例中的步驟，為此範例建立專案。</span><span class="sxs-lookup"><span data-stu-id="5f397-140">Follow the steps in the preceding example to create a project for this example.</span></span>  
  
2.  <span data-ttu-id="5f397-141">在主常式中加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f397-141">Add the following code in the main routine.</span></span> <span data-ttu-id="5f397-142">完成的主控台應用程式應類似下列範例。</span><span class="sxs-lookup"><span data-stu-id="5f397-142">The completed console application should look like the following example.</span></span>  
  
3.  <span data-ttu-id="5f397-143">執行專案。</span><span class="sxs-lookup"><span data-stu-id="5f397-143">Run the project.</span></span> <span data-ttu-id="5f397-144">範例程式碼會執行隨 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 範例安裝的 CalculatedColumns 範例封裝。</span><span class="sxs-lookup"><span data-stu-id="5f397-144">The sample code executes the CalculatedColumns sample package that is installed with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] samples.</span></span> <span data-ttu-id="5f397-145">封裝執行的結果以及任何發生的錯誤都會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="5f397-145">The result of package execution is displayed in the console window, along with any errors that occur.</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="5f397-146">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="5f397-146">Sample Code</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application-specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
<span data-ttu-id="5f397-147">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="5f397-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5f397-148">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="5f397-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5f397-149">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="5f397-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5f397-150">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="5f397-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f397-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f397-151">See Also</span></span>  
 <span data-ttu-id="5f397-152">[瞭解本機和遠端執行之間的差異](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span><span class="sxs-lookup"><span data-stu-id="5f397-152">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span></span>  
 <span data-ttu-id="5f397-153">[以程式設計方式載入和執行遠端封裝](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="5f397-153">[Loading and Running a Remote Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md) </span></span>  
 [<span data-ttu-id="5f397-154">載入本機套件的輸出</span><span class="sxs-lookup"><span data-stu-id="5f397-154">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
