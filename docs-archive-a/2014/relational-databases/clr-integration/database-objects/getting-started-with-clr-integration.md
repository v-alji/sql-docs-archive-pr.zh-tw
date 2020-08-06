---
title: 使用 CLR 整合的消費者入門 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 43c97e411a4d74aa48b88f2edbbe420ae17f3534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584574"
---
# <a name="getting-started-with-clr-integration"></a><span data-ttu-id="130c3-102">CLR 整合使用者入門</span><span class="sxs-lookup"><span data-stu-id="130c3-102">Getting Started with CLR Integration</span></span>
  <span data-ttu-id="130c3-103">本主題提供使用 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] 與 .NET Framework common language runtime (CLR) 整合來編譯資料庫物件所需之命名空間和程式庫的總覽。</span><span class="sxs-lookup"><span data-stu-id="130c3-103">This topic provides an overview of the namespaces and libraries required to compile database objects using the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] integration with the .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="130c3-104">此外，本主題還會為您示範如何撰寫、編譯及執行以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 所撰寫的簡單 CLR 預存程序。</span><span class="sxs-lookup"><span data-stu-id="130c3-104">The topic also shows you how to write, compile, and run a simple CLR stored procedure written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
## <a name="required-namespaces"></a><span data-ttu-id="130c3-105">必要命名空間</span><span class="sxs-lookup"><span data-stu-id="130c3-105">Required Namespaces</span></span>  
 <span data-ttu-id="130c3-106">從開始 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="130c3-106">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="130c3-107">CLR 整合功能會在稱為 system.data.dll (.NET Framework 的一部分) 的組件中公開。</span><span class="sxs-lookup"><span data-stu-id="130c3-107">CLR integration functionality is exposed in an assembly called system.data.dll, which is part of the .NET Framework.</span></span> <span data-ttu-id="130c3-108">此組件可以在全域組件快取 (GAC) 及 .NET Framework 目錄中找到。</span><span class="sxs-lookup"><span data-stu-id="130c3-108">This assembly can be found in the Global Assembly Cache (GAC) as well as in the .NET Framework directory.</span></span> <span data-ttu-id="130c3-109">命令列工具及 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 通常會自動加入此組件的參考，因此不需要手動加入。</span><span class="sxs-lookup"><span data-stu-id="130c3-109">A reference to this assembly is typically added automatically by both command line tools and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, so there is no need to add it manually.</span></span>  
  
 <span data-ttu-id="130c3-110">system.data.dll 組件包含下列編譯 CLR 資料庫物件所需的命名空間：</span><span class="sxs-lookup"><span data-stu-id="130c3-110">The system.data.dll assembly contains the following namespaces, which are required for compiling CLR database objects:</span></span>  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
## <a name="writing-a-simple-hello-world-stored-procedure"></a><span data-ttu-id="130c3-111">撰寫簡單的 "Hello World" 預存程序</span><span class="sxs-lookup"><span data-stu-id="130c3-111">Writing A Simple "Hello World" Stored Procedure</span></span>  
 <span data-ttu-id="130c3-112">將下列 Visual C# 或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 程式碼複製並貼至文字編輯器中，然後將其儲存在名為 "helloworld.cs" 或 "helloworld.vb" 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="130c3-112">Copy and paste the following Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic code into a text editor, and save it in a file named "helloworld.cs" or "helloworld.vb".</span></span>  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    <Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="130c3-113">此簡單的程式包含公用類別上的單一靜態方法。</span><span class="sxs-lookup"><span data-stu-id="130c3-113">This simple program contains a single static method on a public class.</span></span> <span data-ttu-id="130c3-114">此方法會使用 `SqlContext` 及 `SqlPipe` 這兩個新類別，來建立 Managed 資料庫物件以輸出簡單文字訊息。</span><span class="sxs-lookup"><span data-stu-id="130c3-114">This method uses two new classes, `SqlContext` and `SqlPipe`, for creating managed database objects to output a simple text message.</span></span> <span data-ttu-id="130c3-115">此方法也會將字串 "Hello world!" 指派</span><span class="sxs-lookup"><span data-stu-id="130c3-115">The method also assigns the string "Hello world!"</span></span> <span data-ttu-id="130c3-116">為 out 參數的值。</span><span class="sxs-lookup"><span data-stu-id="130c3-116">as the value of an out parameter.</span></span> <span data-ttu-id="130c3-117">這個方法可以宣告為預存程式中的預存程式 [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="130c3-117">This method can be declared as a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] stored procedure.</span></span>  
  
 <span data-ttu-id="130c3-118">現在，我們會將此程式編譯為程式庫，並將其載入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，然後做為預存程序來執行它。</span><span class="sxs-lookup"><span data-stu-id="130c3-118">We will now compile this program as a library, load it into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and run it as a stored procedure.</span></span>  
  
## <a name="compiling-the-hello-world-stored-procedure"></a><span data-ttu-id="130c3-119">編譯 "Hello World" 預存程序</span><span class="sxs-lookup"><span data-stu-id="130c3-119">Compiling the "Hello World" Stored Procedure</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)]<span data-ttu-id="130c3-120">預設 .NET Framework 轉散發檔案。</span><span class="sxs-lookup"><span data-stu-id="130c3-120">.NET Framework redistribution files by default.</span></span> <span data-ttu-id="130c3-121">這些檔案包括 csc.exe、vbc.exe 及 Visual C# 與 Visual Basic 程式的命令列編譯器。</span><span class="sxs-lookup"><span data-stu-id="130c3-121">These files include csc.exe and vbc.exe, the command-line compilers for Visual C# and Visual Basic programs.</span></span> <span data-ttu-id="130c3-122">若要編譯此範例，您必須修改路徑變數，使其指向包含 csc.exe 或 vbc.exe 的目錄。</span><span class="sxs-lookup"><span data-stu-id="130c3-122">In order to compile our sample, you must modify your path variable to point to the directory containing csc.exe or vbc.exe.</span></span> <span data-ttu-id="130c3-123">以下為 .NET Framework 的預設安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="130c3-123">The following is the default installation path of the .NET Framework.</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 <span data-ttu-id="130c3-124">Version 包含已安裝之 .NET Framework 可轉散發套件的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="130c3-124">Version contains the version number of the installed .NET Framework redistributable.</span></span> <span data-ttu-id="130c3-125">例如：</span><span class="sxs-lookup"><span data-stu-id="130c3-125">For example:</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\v2.0.31113  
```  
  
 <span data-ttu-id="130c3-126">將 .NET Framework 目錄加入路徑後，您就可以使用下列命令將範例預存程序編譯為組件。</span><span class="sxs-lookup"><span data-stu-id="130c3-126">Once you have added the .NET Framework directory to your path, you can compile the sample stored procedure into an assembly with the following command.</span></span> <span data-ttu-id="130c3-127">`/target` 選項可讓您將其編譯為組件。</span><span class="sxs-lookup"><span data-stu-id="130c3-127">The `/target` option allows you to compile it into an assembly.</span></span>  
  
 <span data-ttu-id="130c3-128">若為 Visual C# 來源檔案：</span><span class="sxs-lookup"><span data-stu-id="130c3-128">For Visual C# source files:</span></span>  
  
```  
csc /target:library helloworld.cs   
```  
  
 <span data-ttu-id="130c3-129">若為 Visual Basic 來源檔案：</span><span class="sxs-lookup"><span data-stu-id="130c3-129">For Visual Basic source files:</span></span>  
  
```  
vbc /target:library helloworld.vb  
```  
  
 <span data-ttu-id="130c3-130">這些命令會啟動 Visual C# 或 Visual Basic 編譯器，並使用 /target 選項來指定要建立程式庫 DLL。</span><span class="sxs-lookup"><span data-stu-id="130c3-130">These commands launch the Visual C# or Visual Basic compiler using the /target option to specify building a library DLL.</span></span>  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a><span data-ttu-id="130c3-131">在 SQL Server 中載入並執行 "Hello World" 預存程序</span><span class="sxs-lookup"><span data-stu-id="130c3-131">Loading and Running the "Hello World" Stored Procedure in SQL Server</span></span>  
 <span data-ttu-id="130c3-132">成功編譯範例程式後，您可以在中進行測試， [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] 並建立新的查詢，連接到適當的測試資料庫 (例如，AdventureWorks 範例資料庫) 。</span><span class="sxs-lookup"><span data-stu-id="130c3-132">Once the sample procedure has successfully compiled, you can test it in [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] and create a new query, connecting to a suitable test database (for example, the AdventureWorks sample database).</span></span>  
  
 <span data-ttu-id="130c3-133">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，執行 Common Language Runtime (CLR) 程式碼的功能預設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="130c3-133">The ability to execute common language runtime (CLR) code is set to OFF by default in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="130c3-134">您可以使用**sp_configure**系統預存程式來啟用 CLR 程式碼。</span><span class="sxs-lookup"><span data-stu-id="130c3-134">The CLR code can be enabled by using the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="130c3-135">如需詳細資訊，請參閱 [Enabling CLR Integration](../clr-integration-enabling.md)。</span><span class="sxs-lookup"><span data-stu-id="130c3-135">For more information, see [Enabling CLR Integration](../clr-integration-enabling.md).</span></span>  
  
 <span data-ttu-id="130c3-136">我們必須先建立組件後，才可以存取預存程序。</span><span class="sxs-lookup"><span data-stu-id="130c3-136">We will need to create the assembly so we can access the stored procedure.</span></span> <span data-ttu-id="130c3-137">針對此範例，假設已在 C:\ 目錄中建立 helloworld.dll 組件。</span><span class="sxs-lookup"><span data-stu-id="130c3-137">For this example, we will assume that you have created the helloworld.dll assembly in the C:\ directory.</span></span> <span data-ttu-id="130c3-138">將下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式加入至查詢。</span><span class="sxs-lookup"><span data-stu-id="130c3-138">Add the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to your query.</span></span>  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 <span data-ttu-id="130c3-139">組件建立完成後，您就可以使用 create procedure 陳述式存取 HelloWorld 方法。</span><span class="sxs-lookup"><span data-stu-id="130c3-139">Once the assembly has been created, we can now access our HelloWorld method by using the create procedure statement.</span></span> <span data-ttu-id="130c3-140">我們會將該預存程序稱為 hello：</span><span class="sxs-lookup"><span data-stu-id="130c3-140">We will call our stored procedure "hello":</span></span>  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 <span data-ttu-id="130c3-141">程序建立完成後，就可以使用與執行 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 中撰寫的一般預存程序一樣的方法來執行它。</span><span class="sxs-lookup"><span data-stu-id="130c3-141">Once the procedure has been created, it can be run just like a normal stored procedure written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="130c3-142">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="130c3-142">Execute the following command:</span></span>  
  
```  
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
 <span data-ttu-id="130c3-143">這將在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 訊息視窗中產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="130c3-143">This should result in the following output in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] messages window.</span></span>  
  
```  
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a><span data-ttu-id="130c3-144">移除 "Hello World" 預存程序範例</span><span class="sxs-lookup"><span data-stu-id="130c3-144">Removing the "Hello World" Stored Procedure Sample</span></span>  
 <span data-ttu-id="130c3-145">完成執行該範例預存程序時，您就可以從測試資料庫中移除該程序及組件。</span><span class="sxs-lookup"><span data-stu-id="130c3-145">When you are finished running the sample stored procedure, you can remove the procedure and the assembly from your test database.</span></span>  
  
 <span data-ttu-id="130c3-146">首先，使用 drop procedure 命令移除該程序。</span><span class="sxs-lookup"><span data-stu-id="130c3-146">First, remove the procedure using the drop procedure command.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 <span data-ttu-id="130c3-147">程序一旦刪除後，您就可以移除包含範例程式碼的組件。</span><span class="sxs-lookup"><span data-stu-id="130c3-147">Once the procedure has been dropped, you can remove the assembly containing your sample code.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a><span data-ttu-id="130c3-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="130c3-148">See Also</span></span>  
 <span data-ttu-id="130c3-149">[CLR 預存程式](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="130c3-149">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 <span data-ttu-id="130c3-150">[SQL Server ADO.NET 的同進程特定延伸模組](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span><span class="sxs-lookup"><span data-stu-id="130c3-150">[SQL Server In-Process Specific Extensions to ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span></span>  
 <span data-ttu-id="130c3-151">[調試 CLR 資料庫物件](../debugging-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="130c3-151">[Debugging CLR Database Objects](../debugging-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="130c3-152">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="130c3-152">CLR Integration Security</span></span>](../security/clr-integration-security.md)  
  
  
