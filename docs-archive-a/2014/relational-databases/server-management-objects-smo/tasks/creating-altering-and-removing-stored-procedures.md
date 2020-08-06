---
title: 建立、改變和移除預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73e8313f3befd4c7c5cb20cdb6649c87ea72b037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606187"
---
# <a name="creating-altering-and-removing-stored-procedures"></a><span data-ttu-id="876c2-102">建立、改變和移除預存程序</span><span class="sxs-lookup"><span data-stu-id="876c2-102">Creating, Altering, and Removing Stored Procedures</span></span>
  <span data-ttu-id="876c2-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 中，預存程序會由 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="876c2-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), stored procedures are represented by the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
 <span data-ttu-id="876c2-104">若要在 SMO 中建立 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 物件，需要將 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> 屬性設定為定義預存程序的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="876c2-104">Creating a <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object in SMO requires setting the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> property to the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script that defines the stored procedure.</span></span> <span data-ttu-id="876c2-105">參數需要 \@ 前置詞，而且必須使用物件個別建立， <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> 並加入至 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> 物件的集合 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> 。</span><span class="sxs-lookup"><span data-stu-id="876c2-105">Parameters require the \@ prefix and must be created individually by using <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> objects and adding to the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="876c2-106">範例</span><span class="sxs-lookup"><span data-stu-id="876c2-106">Example</span></span>  
 <span data-ttu-id="876c2-107">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="876c2-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="876c2-108">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="876c2-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a><span data-ttu-id="876c2-109">在 Visual Basic 中建立、改變和移除預存程序</span><span class="sxs-lookup"><span data-stu-id="876c2-109">Creating, Altering, and Removing a Stored Procedure in Visual Basic</span></span>  
 <span data-ttu-id="876c2-110">此程式碼範例示範如何為 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="876c2-110">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="876c2-111">以下範例在給定員工識別碼時會傳回員工的姓。</span><span class="sxs-lookup"><span data-stu-id="876c2-111">The example returns the last name of an employee when it is given the employee ID number.</span></span> <span data-ttu-id="876c2-112">預存程序需要一個輸入參數來指定員工識別碼，以及一個輸出參數來傳回員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="876c2-112">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a><span data-ttu-id="876c2-113">在 Visual C# 中建立、改變和移除預存程序</span><span class="sxs-lookup"><span data-stu-id="876c2-113">Creating, Altering, and Removing a Stored Procedure in Visual C#</span></span>  
 <span data-ttu-id="876c2-114">此程式碼範例示範如何為 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="876c2-114">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="876c2-115">以下範例在給定員工識別碼 (`BusinessEntityID`) 時會傳回員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="876c2-115">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="876c2-116">預存程序需要一個輸入參數來指定員工識別碼，以及一個輸出參數來傳回員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="876c2-116">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a><span data-ttu-id="876c2-117">在 PowerShell 中建立、改變和移除預存程序</span><span class="sxs-lookup"><span data-stu-id="876c2-117">Creating, Altering, and Removing a Stored Procedure in PowerShell</span></span>  
 <span data-ttu-id="876c2-118">此程式碼範例示範如何為 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="876c2-118">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="876c2-119">以下範例在給定員工識別碼 (`BusinessEntityID`) 時會傳回員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="876c2-119">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="876c2-120">預存程序需要一個輸入參數來指定員工識別碼，以及一個輸出參數來傳回員工的姓氏。</span><span class="sxs-lookup"><span data-stu-id="876c2-120">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.
$sp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure -argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.
$sp.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="876c2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="876c2-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
