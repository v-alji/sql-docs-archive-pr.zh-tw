---
title: 以程式設計方式建立套件 | Microsoft Docs
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
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: e44bcc70-32d3-43e8-a84b-29aef819d5d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1159784fc95dd86d9d33c4354291cc7c52812982
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700150"
---
# <a name="creating-a-package-programmatically"></a><span data-ttu-id="5b378-102">以程式設計方式建立封裝</span><span class="sxs-lookup"><span data-stu-id="5b378-102">Creating a Package Programmatically</span></span>
  <span data-ttu-id="5b378-103"><xref:Microsoft.SqlServer.Dts.Runtime.Package> 物件是 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 專案方案中所有其他物件的最上層容器。</span><span class="sxs-lookup"><span data-stu-id="5b378-103">The <xref:Microsoft.SqlServer.Dts.Runtime.Package> object is the top-level container for all other objects in an [!INCLUDE[ssIS](../../includes/ssis-md.md)] project solution.</span></span> <span data-ttu-id="5b378-104">做為最上層容器，封裝是第一個建立的物件，而且後續的物件會加入其中，然後在封裝的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="5b378-104">As the top-level container, the package is the first object created, and subsequent objects are added to it, and then executed within the context of the package.</span></span> <span data-ttu-id="5b378-105">封裝本身不會移動或是轉換資料。</span><span class="sxs-lookup"><span data-stu-id="5b378-105">The package itself does not move or transform data.</span></span> <span data-ttu-id="5b378-106">封裝依賴它所含的工作 (Task) 以執行工作 (Work)。</span><span class="sxs-lookup"><span data-stu-id="5b378-106">The package relies on the tasks it contains to perform the work.</span></span> <span data-ttu-id="5b378-107">工作 (Task) 會執行封裝所執行的大部分工作 (Work)，並定義封裝的功能。</span><span class="sxs-lookup"><span data-stu-id="5b378-107">Tasks perform most of the work performed by a package, and define the functionality of a package.</span></span> <span data-ttu-id="5b378-108">只需要三行程式碼就可以建立和執行封裝，但是還需要將各種工作與 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件加入，以便為您的封裝提供其他功能。</span><span class="sxs-lookup"><span data-stu-id="5b378-108">A package is created and executed with just three lines of code, but various tasks and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects are added to give additional functionality to your package.</span></span> <span data-ttu-id="5b378-109">本節討論如何以程式設計方式建立封裝。</span><span class="sxs-lookup"><span data-stu-id="5b378-109">This section discusses how to programmatically create a package.</span></span> <span data-ttu-id="5b378-110">有關如何建立工作或 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 的詳細資訊並非在此提供，</span><span class="sxs-lookup"><span data-stu-id="5b378-110">It does not provide information about how to create the tasks or the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span> <span data-ttu-id="5b378-111">這些內容將於後續章節說明。</span><span class="sxs-lookup"><span data-stu-id="5b378-111">These are covered in later sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b378-112">範例</span><span class="sxs-lookup"><span data-stu-id="5b378-112">Example</span></span>  
 <span data-ttu-id="5b378-113">若要使用 Visual Studio IDE 撰寫程式碼，會需要 Microsoft.SqlServer.ManagedDTS.DLL 的參考，才能建立 Microsoft.SqlServer.Dts.Runtime 的 `using` 陳述式 (在 Visual Basic .NET 中則是 `Imports`)。</span><span class="sxs-lookup"><span data-stu-id="5b378-113">To write code using the Visual Studio IDE, a reference to Microsoft.SqlServer.ManagedDTS.DLL is required in order to create a `using` statement (`Imports` in Visual Basic .NET) to the Microsoft.SqlServer.Dts.Runtime.</span></span> <span data-ttu-id="5b378-114">下列程式碼範例示範建立空的封裝。</span><span class="sxs-lookup"><span data-stu-id="5b378-114">The following code sample demonstrates creating an empty package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Package package;  
      package = new Package();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Package  
    package = New Package  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="5b378-115">若要編譯和執行範例，請在 Visual Studio 中按 F5。</span><span class="sxs-lookup"><span data-stu-id="5b378-115">To compile and run the sample, press F5 in Visual Studio.</span></span> <span data-ttu-id="5b378-116">若要使用 C# 編譯器 **csc.exe** 建置程式碼，請在要編譯的命令提示字元之下，使用下列命令與檔案參考，以 .cs 或 .vb 檔案的名稱取代 *\<filename>* ，並提供所選的 *\<outputfilename>* 。</span><span class="sxs-lookup"><span data-stu-id="5b378-116">To build the code using the C# compiler, **csc.exe**, at the command prompt to compile, use the following command and file references, replacing the *\<filename>* with the name of the .cs or .vb file, and giving it an *\<outputfilename>* of your choice.</span></span>  
  
 <span data-ttu-id="5b378-117">**csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span><span class="sxs-lookup"><span data-stu-id="5b378-117">**csc /target:library /out: \<outputfilename>.dll \<filename>.cs /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="5b378-118">若要使用 Visual Basic .NET 編譯器 **vbc.exe** 建置程式碼，請在要編譯的命令提示字元之下，使用下列命令與檔案參考。</span><span class="sxs-lookup"><span data-stu-id="5b378-118">To build the code using the Visual Basic .NET compiler, **vbc.exe**, at the command prompt to compile, use the following command and file references.</span></span>  
  
 <span data-ttu-id="5b378-119">**vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span><span class="sxs-lookup"><span data-stu-id="5b378-119">**vbc /target:library /out: \<outputfilename>.dll \<filename>.vb /r:Microsoft.SqlServer.Managed DTS.dll" /r:System.dll**</span></span>  
  
 <span data-ttu-id="5b378-120">您也可以載入儲存在磁碟上、在檔案系統或是儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的現有封裝以建立封裝。</span><span class="sxs-lookup"><span data-stu-id="5b378-120">You can also create a package by loading an existing package that was saved on disk, in the file system, or to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5b378-121">其差異在於會先建立 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 物件，然後其中一個應用程式的多載方法會填入封裝物件：`LoadPackage` 用於一般檔案、`LoadFromSQLServer` 用於儲存到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的封裝，或是 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> 用於儲存到檔案系統的封裝。</span><span class="sxs-lookup"><span data-stu-id="5b378-121">The difference is that the <xref:Microsoft.SqlServer.Dts.Runtime.Application> object is first created, and then the package object is filled by one of the Application's overloaded methods: `LoadPackage` for flat files, `LoadFromSQLServer` for packages saved to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> for packages saved to the file system.</span></span> <span data-ttu-id="5b378-122">下列範例會從磁碟載入現有封裝，然後檢視封裝上的數個屬性。</span><span class="sxs-lookup"><span data-stu-id="5b378-122">The following example loads an existing package from disk, and then views several properties on the package.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class ApplicationTests  
  {  
    static void Main(string[] args)  
    {  
      // The variable pkg points to the location of the  
      // ExecuteProcess package sample that was installed with  
      // the SSIS samples.  
      string pkg = @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx";  
  
      Application app = new Application();  
      Package p = app.LoadPackage(pkg, null);  
  
      // Now that the package is loaded, we can query on  
      // its properties.  
      int n = p.Configurations.Count;  
      DtsProperty p2 = p.Properties["VersionGUID"];  
      DTSProtectionLevel pl = p.ProtectionLevel;  
  
      Console.WriteLine("Number of configurations = " + n.ToString());  
      Console.WriteLine("VersionGUID = " + (string)p2.GetValue(p));  
      Console.WriteLine("ProtectionLevel = " + pl.ToString());  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module ApplicationTests  
  
  Sub Main()  
  
    ' The variable pkg points to the location of the  
    ' ExecuteProcess package sample that was installed with  
    ' the SSIS samples.  
    Dim pkg As String = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\ExecuteProcess Sample\ExecuteProcess\UsingExecuteProcess.dtsx"  
  
    Dim app As Application = New Application()  
    Dim p As Package = app.LoadPackage(pkg, Nothing)  
  
    ' Now that the package is loaded, we can query on  
    ' its properties.  
    Dim n As Integer = p.Configurations.Count  
    Dim p2 As DtsProperty = p.Properties("VersionGUID")  
    Dim pl As DTSProtectionLevel = p.ProtectionLevel  
  
    Console.WriteLine("Number of configurations = " & n.ToString())  
    Console.WriteLine("VersionGUID = " & CType(p2.GetValue(p), String))  
    Console.WriteLine("ProtectionLevel = " & pl.ToString())  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
 <span data-ttu-id="5b378-123">**範例輸出：**</span><span class="sxs-lookup"><span data-stu-id="5b378-123">**Sample Output:**</span></span>  
  
 `Number of configurations = 2`  
  
 `VersionGUID = {09016682-89B8-4406-AAC9-AF1E527FF50F}`  
  
 `ProtectionLevel = DontSaveSensitive`  
  
## <a name="external-resources"></a><span data-ttu-id="5b378-124">外部資源</span><span class="sxs-lookup"><span data-stu-id="5b378-124">External Resources</span></span>  
  
-   <span data-ttu-id="5b378-125">blogs.msdn.com 上的部落格文章：[API Sample - OleDB source and OleDB destination](https://go.microsoft.com/fwlink/?LinkId=220824) (API 範例 - OleDB 來源與 OleDB 目的地)。</span><span class="sxs-lookup"><span data-stu-id="5b378-125">Blog entry, [API Sample - OleDB source and OleDB destination](https://go.microsoft.com/fwlink/?LinkId=220824), on blogs.msdn.com.</span></span>  
  
-   <span data-ttu-id="5b378-126">blogs.msdn.com 上的部落格文章：[EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223) (EzAPI - 針對 SQL Server 2012 更新)。</span><span class="sxs-lookup"><span data-stu-id="5b378-126">Blog entry, [EzAPI - Updated for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=243223), on blogs.msdn.com.</span></span>  
  
<span data-ttu-id="5b378-127">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="5b378-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="5b378-128">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="5b378-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="5b378-129">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="5b378-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="5b378-130">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="5b378-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b378-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b378-131">See Also</span></span>  
 [<span data-ttu-id="5b378-132">以程式設計方式新增工作</span><span class="sxs-lookup"><span data-stu-id="5b378-132">Adding Tasks Programmatically</span></span>](../building-packages-programmatically/adding-tasks-programmatically.md)  
  
  
