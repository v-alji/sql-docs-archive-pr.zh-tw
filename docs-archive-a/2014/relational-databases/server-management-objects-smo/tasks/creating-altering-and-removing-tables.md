---
title: 建立、改變和移除資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- tables [SMO]
ms.assetid: ff0bcfff-812f-4999-b0c7-736a97804c2b
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce2053009b3cba44f061401061ef603f222d65f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606184"
---
# <a name="creating-altering-and-removing-tables"></a><span data-ttu-id="a9c69-102">建立、改變和移除資料表</span><span class="sxs-lookup"><span data-stu-id="a9c69-102">Creating, Altering, and Removing Tables</span></span>
  <span data-ttu-id="a9c69-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 中，資料表是由 <xref:Microsoft.SqlServer.Management.Smo.Table> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="a9c69-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), tables are represented by the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span> <span data-ttu-id="a9c69-104">在 SMO 物件階層中，<xref:Microsoft.SqlServer.Management.Smo.Table> 物件位於 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件之下。</span><span class="sxs-lookup"><span data-stu-id="a9c69-104">In the SMO object hierarchy, the <xref:Microsoft.SqlServer.Management.Smo.Table> object is below the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9c69-105">範例</span><span class="sxs-lookup"><span data-stu-id="a9c69-105">Example</span></span>  
 <span data-ttu-id="a9c69-106">若要使用所提供的任何程式碼範例，您必須選擇可用於建立應用程式的程式設計環境、範本和計語言。</span><span class="sxs-lookup"><span data-stu-id="a9c69-106">To use any code example that is provided, you have to choose the programming environment, template, and language in which to create your application.</span></span> <span data-ttu-id="a9c69-107">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="a9c69-107">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-table-in-visual-basic"></a><span data-ttu-id="a9c69-108">在 Visual Basic 中建立、改變和移除資料表</span><span class="sxs-lookup"><span data-stu-id="a9c69-108">Creating, Altering, and Removing a Table in Visual Basic</span></span>  
 <span data-ttu-id="a9c69-109">此程式碼範例所建立的資料表擁有數個具有不同類型和用途的資料行。</span><span class="sxs-lookup"><span data-stu-id="a9c69-109">This code example creates a table that has several columns with different types and purposes.</span></span> <span data-ttu-id="a9c69-110">此程式碼也提供如何建立識別欄位、如何建立主索引鍵以及如何改變資料表屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="a9c69-110">The code also provides examples of how to create an identity field, how to create a primary key, and how to alter table properties.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTable1](SMO How to#SMO_VBTable1)]  -->  
  
## <a name="creating-altering-and-removing-a-table-in-visual-c"></a><span data-ttu-id="a9c69-111">在 Visual C# 中建立、改變和移除資料表</span><span class="sxs-lookup"><span data-stu-id="a9c69-111">Creating, Altering, and Removing a Table in Visual C#</span></span>  
 <span data-ttu-id="a9c69-112">此程式碼範例所建立的資料表擁有數個具有不同類型和用途的資料行。</span><span class="sxs-lookup"><span data-stu-id="a9c69-112">This code example creates a table that has several columns with different types and purposes.</span></span> <span data-ttu-id="a9c69-113">此程式碼也提供如何建立識別欄位、如何建立主索引鍵以及如何改變資料表屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="a9c69-113">The code also provides examples of how to create an identity field, how to create a primary key, and how to alter table properties.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a Table object variable by supplying the parent database and table name in the constructor.   
        Table tb;   
        tb = new Table(db, "Test_Table");   
        //Add various columns to the table.   
        Column col1;   
        col1 = new Column(tb, "Name", DataType.NChar(50));   
        col1.Collation = "Latin1_General_CI_AS";   
        col1.Nullable = true;   
        tb.Columns.Add(col1);   
        Column col2;   
        col2 = new Column(tb, "ID", DataType.Int);   
        col2.Identity = true;   
        col2.IdentitySeed = 1;   
        col2.IdentityIncrement = 1;   
        tb.Columns.Add(col2);   
        Column col3;   
        col3 = new Column(tb, "Value", DataType.Real);   
        tb.Columns.Add(col3);   
        Column col4;   
        col4 = new Column(tb, "Date", DataType.DateTime);   
        col4.Nullable = false;   
        tb.Columns.Add(col4);   
        //Create the table on the instance of SQL Server.   
        tb.Create();   
        //Add another column.   
        Column col5;   
        col5 = new Column(tb, "ExpiryDate", DataType.DateTime);   
        col5.Nullable = false;   
        tb.Columns.Add(col5);   
        //Run the Alter method to make the change on the instance of SQL Server.   
        tb.Alter();   
        //Remove the table from the database.   
        tb.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-table-in-powershell"></a><span data-ttu-id="a9c69-114">在 PowerShell 中建立、改變和移除資料表</span><span class="sxs-lookup"><span data-stu-id="a9c69-114">Creating, Altering, and Removing a Table in PowerShell</span></span>  
 <span data-ttu-id="a9c69-115">此程式碼範例所建立的資料表擁有數個具有不同類型和用途的資料行。</span><span class="sxs-lookup"><span data-stu-id="a9c69-115">This code example creates a table that has several columns with different types and purposes.</span></span> <span data-ttu-id="a9c69-116">此程式碼也提供如何建立識別欄位、如何建立主索引鍵以及如何改變資料表屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="a9c69-116">The code also provides examples of how to create an identity field, how to create a primary key, and how to alter table properties.</span></span>  
  
```powershell
#Load the assembly containing the objects used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.Types")  
  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012.  
$db = Get-Item AdventureWorks2012  
  
#Create a SMO Table  
$tb = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Table -argumentlist $db, "Test_Table"  
  
#Add various columns to the table.   
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::NChar(50)  
$col1 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Name", $Type  
$col1.Collation = "Latin1_General_CI_AS"  
$col1.Nullable = $true  
$tb.Columns.Add($col1)  
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::Int  
$col2 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"ID", $Type  
$col2.Identity = $true  
$col2.IdentitySeed = 1  
$col2.IdentityIncrement = 1  
$tb.Columns.Add($col2)
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::Real  
$col3 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Value", $Type  
$tb.Columns.Add($col3)
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$col4 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"Date", $Type  
$col4.Nullable = $false  
$tb.Columns.Add($col4)
  
#Create the table  
$tb.Create()  
  
$Type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$col5 =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.Column -argumentlist $tb,"ExpiryDate", $Type  
$col5.Nullable = $false  
$tb.Columns.Add($col5)
  
#Run the Alter method to make the change on the instance of SQL Server.
$tb.Alter()  
  
#Remove the table from the database.
$tb.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9c69-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9c69-117">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Table>
