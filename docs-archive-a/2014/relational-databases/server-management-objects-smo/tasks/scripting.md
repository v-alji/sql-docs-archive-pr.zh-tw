---
title: 指令碼 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- dependencies [SMO]
- scripts [SMO]
ms.assetid: 13a35511-3987-426b-a3b7-3b2e83900dc7
author: stevestein
ms.author: sstein
ms.openlocfilehash: bf46798597de021976cefa943a17500e773f9274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700927"
---
# <a name="scripting"></a><span data-ttu-id="088b4-102">指令碼</span><span class="sxs-lookup"><span data-stu-id="088b4-102">Scripting</span></span>
  <span data-ttu-id="088b4-103">在 SMO 中，指令碼是由 <xref:Microsoft.SqlServer.Management.Smo.Scripter> 物件及其子物件控制，或是由個別物件的 `Script` 方法控制。</span><span class="sxs-lookup"><span data-stu-id="088b4-103">Scripting in SMO is controlled by the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects, or the `Script` method on individual objects.</span></span> <span data-ttu-id="088b4-104"><xref:Microsoft.SqlServer.Management.Smo.Scripter>物件會針對實例上物件的相依性關聯性控制對應 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="088b4-104">The <xref:Microsoft.SqlServer.Management.Smo.Scripter> object controls the mapping out of dependency relationships for objects on an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="088b4-105">使用 <xref:Microsoft.SqlServer.Management.Smo.Scripter> 物件及其子物件所進行的進階指令碼作業是三階段的程序：</span><span class="sxs-lookup"><span data-stu-id="088b4-105">Advanced scripting by using the <xref:Microsoft.SqlServer.Management.Smo.Scripter> object and its child objects is a three phase process:</span></span>  
  
1.  <span data-ttu-id="088b4-106">探索</span><span class="sxs-lookup"><span data-stu-id="088b4-106">Discovery</span></span>  
  
2.  <span data-ttu-id="088b4-107">產生清單</span><span class="sxs-lookup"><span data-stu-id="088b4-107">List generation</span></span>  
  
3.  <span data-ttu-id="088b4-108">產生指令碼</span><span class="sxs-lookup"><span data-stu-id="088b4-108">Script generation</span></span>  
  
 <span data-ttu-id="088b4-109">探索階段會使用 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> 物件。</span><span class="sxs-lookup"><span data-stu-id="088b4-109">The discovery phase uses the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object.</span></span> <span data-ttu-id="088b4-110">如果已給定物件 URN 清單，則 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> 方法會針對 URN 清單中的物件傳回 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> 物件。</span><span class="sxs-lookup"><span data-stu-id="088b4-110">Given an URN list of objects, the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.DiscoverDependencies%2A> method of the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker> object returns a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object for the objects in the URN list.</span></span> <span data-ttu-id="088b4-111">布林值*fParents*參數是用來選取是否要探索指定物件的父系或子系。</span><span class="sxs-lookup"><span data-stu-id="088b4-111">The Boolean *fParents* parameter is used to select whether the parents or the children of the specified object are to be discovered.</span></span> <span data-ttu-id="088b4-112">在這個階段可以修改相依性樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="088b4-112">The dependency tree can be modified at this stage.</span></span>  
  
 <span data-ttu-id="088b4-113">在產生清單階段會傳入樹狀目錄並傳回產生的清單。</span><span class="sxs-lookup"><span data-stu-id="088b4-113">In the list generation phase, the tree is passed in and the resulting list is returned.</span></span> <span data-ttu-id="088b4-114">這個物件清單會以指令碼作業順序排列，且可以操作。</span><span class="sxs-lookup"><span data-stu-id="088b4-114">This object list is in scripting order and can be manipulated.</span></span>  
  
 <span data-ttu-id="088b4-115">產生清單階段會使用 <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> 方法傳回 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>。</span><span class="sxs-lookup"><span data-stu-id="088b4-115">The list generation phases use the <xref:Microsoft.SqlServer.Management.Smo.DependencyWalker.WalkDependencies%2A> method to return a <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>.</span></span> <span data-ttu-id="088b4-116">在這個階段可以修改 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree>。</span><span class="sxs-lookup"><span data-stu-id="088b4-116">The <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> can be modified at this stage.</span></span>  
  
 <span data-ttu-id="088b4-117">在第三個也就是最後階段時，會產生具有指定清單和指令碼選項的指令碼。</span><span class="sxs-lookup"><span data-stu-id="088b4-117">In the third and final phase, a script is generated with the specified list and scripting options.</span></span> <span data-ttu-id="088b4-118">結果會以 <xref:System.Collections.Specialized.StringCollection> 系統物件傳回。</span><span class="sxs-lookup"><span data-stu-id="088b4-118">The result is returned as a <xref:System.Collections.Specialized.StringCollection> system object.</span></span> <span data-ttu-id="088b4-119">接下來在這個階段中會從 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> 物件的 Items 集合以及 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A> 之類的屬性擷取相依物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="088b4-119">In this phase the dependent object names are then extracted from the Items collection of the <xref:Microsoft.SqlServer.Management.Smo.DependencyTree> object and properties such as <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.NumberOfSiblings%2A> and <xref:Microsoft.SqlServer.Management.Smo.DependencyTree.FirstChild%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="088b4-120">範例</span><span class="sxs-lookup"><span data-stu-id="088b4-120">Example</span></span>  
 <span data-ttu-id="088b4-121">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="088b4-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="088b4-122">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="088b4-122">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
 <span data-ttu-id="088b4-123">這個程式碼範例需要針對 System.Collections.Specialized 命名空間使用 `Imports` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="088b4-123">This code example requires an `Imports` statement for the System.Collections.Specialized namespace.</span></span> <span data-ttu-id="088b4-124">請在應用程式中，將這個陳述式與其他的 Imports 陳述式一同插入任何宣告之前。</span><span class="sxs-lookup"><span data-stu-id="088b4-124">Insert this with the other Imports statements, before any declarations in the application.</span></span>  
  
```vb
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
Imports System.Collections.Specialized  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-basic"></a><span data-ttu-id="088b4-125">針對 Visual Basic 中的資料庫撰寫相依性的指令碼</span><span class="sxs-lookup"><span data-stu-id="088b4-125">Scripting Out the Dependencies for a Database in Visual Basic</span></span>  
 <span data-ttu-id="088b4-126">這個程式碼範例示範如何探索相依性，並反覆運算清單以顯示結果。</span><span class="sxs-lookup"><span data-stu-id="088b4-126">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
  
Public Class A  
   Public Shared Sub Main()  
      ' database name  
      Dim dbName As [String] = "AdventureWorksLT2012"   ' database name  
  
      ' Connect to the local, default instance of SQL Server.   
      Dim srv As New Server()  
  
      ' Reference the database.    
      Dim db As Database = srv.Databases(dbName)  
  
      ' Define a Scripter object and set the required scripting options.   
      Dim scrp As New Scripter(srv)  
      scrp.Options.ScriptDrops = False  
      scrp.Options.WithDependencies = True  
      scrp.Options.Indexes = True   ' To include indexes  
      scrp.Options.DriAllConstraints = True   ' to include referential constraints in the script  
  
      ' Iterate through the tables in database and script each one. Display the script.  
      For Each tb As Table In db.Tables  
         ' check if the table is not a system table  
         If tb.IsSystemObject = False Then  
            Console.WriteLine("-- Scripting for table " + tb.Name)  
  
            ' Generating script for table tb  
            Dim sc As System.Collections.Specialized.StringCollection = scrp.Script(New Urn() {tb.Urn})  
            For Each st As String In sc  
               Console.WriteLine(st)  
            Next  
            Console.WriteLine("--")  
         End If  
      Next  
   End Sub  
End Class  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-visual-c"></a><span data-ttu-id="088b4-127">針對 Visual C# 中的資料庫撰寫相依性的指令碼</span><span class="sxs-lookup"><span data-stu-id="088b4-127">Scripting Out the Dependencies for a Database in Visual C#</span></span>  
 <span data-ttu-id="088b4-128">這個程式碼範例示範如何探索相依性，並反覆運算清單以顯示結果。</span><span class="sxs-lookup"><span data-stu-id="088b4-128">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
  
public class A {  
   public static void Main() {   
      String dbName = "AdventureWorksLT2012"; // database name  
  
      // Connect to the local, default instance of SQL Server.   
      Server srv = new Server();  
  
      // Reference the database.    
      Database db = srv.Databases[dbName];  
  
      // Define a Scripter object and set the required scripting options.   
      Scripter scrp = new Scripter(srv);  
      scrp.Options.ScriptDrops = false;  
      scrp.Options.WithDependencies = true;  
      scrp.Options.Indexes = true;   // To include indexes  
      scrp.Options.DriAllConstraints = true;   // to include referential constraints in the script  
  
      // Iterate through the tables in database and script each one. Display the script.     
      foreach (Table tb in db.Tables) {   
         // check if the table is not a system table  
         if (tb.IsSystemObject == false) {  
            Console.WriteLine("-- Scripting for table " + tb.Name);  
  
            // Generating script for table tb  
            System.Collections.Specialized.StringCollection sc = scrp.Script(new Urn[]{tb.Urn});  
            foreach (string st in sc) {  
               Console.WriteLine(st);  
            }  
            Console.WriteLine("--");  
         }  
      }   
   }  
}  
```  
  
## <a name="scripting-out-the-dependencies-for-a-database-in-powershell"></a><span data-ttu-id="088b4-129">在 PowerShell 中針對資料庫撰寫相依性的指令碼</span><span class="sxs-lookup"><span data-stu-id="088b4-129">Scripting Out the Dependencies for a Database in PowerShell</span></span>  
 <span data-ttu-id="088b4-130">這個程式碼範例示範如何探索相依性，並反覆運算清單以顯示結果。</span><span class="sxs-lookup"><span data-stu-id="088b4-130">This code example shows how to discover the dependencies and iterate through the list to display the results.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
# Create a Scripter object and set the required scripting options.  
$scrp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Scripter -ArgumentList (Get-Item .)  
$scrp.Options.ScriptDrops = $false  
$scrp.Options.WithDependencies = $true  
$scrp.Options.IncludeIfNotExists = $true  
  
# Set the path context to the tables in AdventureWorks2012.  
CD Databases\AdventureWorks2012\Tables  
  
foreach ($Item in Get-ChildItem)  
 {    
 $scrp.Script($Item)  
 }  
```  
