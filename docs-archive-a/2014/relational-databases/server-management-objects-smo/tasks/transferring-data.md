---
title: 傳送資料 |Microsoft Docs
ms.custom: ''
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- data transfers [SMO]
- transferring data
ms.assetid: eea255c3-8251-40f0-973b-fe4ef6cb5261
author: stevestein
ms.author: sstein
ms.openlocfilehash: dcbcdc1e61c2d18f6a98f797385145f04dfecc7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700921"
---
# <a name="transferring-data"></a><span data-ttu-id="380e0-102">傳送資料</span><span class="sxs-lookup"><span data-stu-id="380e0-102">Transferring Data</span></span>
  <span data-ttu-id="380e0-103"> 類別是一種公用程式類別，可提供工具來傳送物件和資料。</span><span class="sxs-lookup"><span data-stu-id="380e0-103">The <xref:Microsoft.SqlServer.Management.Smo.Transfer> class is a utility class that provides tools to transfer objects and data.</span></span>  
  
 <span data-ttu-id="380e0-104">資料庫結構描述中物件的傳送方式是藉由執行目標伺服器上產生的指令碼。</span><span class="sxs-lookup"><span data-stu-id="380e0-104">Objects in the database schema are transferred by executing a generated script on the target server.</span></span> <span data-ttu-id="380e0-105"><xref:Microsoft.SqlServer.Management.Smo.Table> 資料會隨著動態建立的 DTS 封裝一起傳送。</span><span class="sxs-lookup"><span data-stu-id="380e0-105"><xref:Microsoft.SqlServer.Management.Smo.Table> data is transferred with a dynamically created DTS package.</span></span>  
  
 <span data-ttu-id="380e0-106"> 物件包含了 DMO 中  物件的所有功能和其他  功能。</span><span class="sxs-lookup"><span data-stu-id="380e0-106">The <xref:Microsoft.SqlServer.Management.Smo.Transfer> object contains all the functionality of the <xref:Microsoft.SqlServer.Management.Smo.Transfer> objects in DMO and additional [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span> <span data-ttu-id="380e0-107">不過，在的 SMO 中 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ， <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件會使用[SQLBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx) API 來傳送資料。</span><span class="sxs-lookup"><span data-stu-id="380e0-107">However, in SMO in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object uses the [SQLBulkCopy](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopy\(v=VS.90\).aspx) API to transfer data.</span></span> <span data-ttu-id="380e0-108">此外，用來執行資料傳送的方法和屬性是位於 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件上，而不是 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件上。</span><span class="sxs-lookup"><span data-stu-id="380e0-108">Also, the methods and properties that are used to perform data transfers reside on the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object instead of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span> <span data-ttu-id="380e0-109">將功能從執行個體類別移到公用程式類別與較輕的物件模型一致，因為只有在需要時才會載入特定工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="380e0-109">Moving functionality from the instance classes to utility classes is consistent with a lighter object model because the code for specific tasks is loaded only when it is required.</span></span>  
  
 <span data-ttu-id="380e0-110"> 物件不支援將資料傳送到  小於  執行個體版本的目標資料庫。</span><span class="sxs-lookup"><span data-stu-id="380e0-110">The <xref:Microsoft.SqlServer.Management.Smo.Transfer> object does not support data transfers to a target database that has a <xref:Microsoft.SqlServer.Management.Smo.Database.CompatibilityLevel%2A> less than the version of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="380e0-111">範例</span><span class="sxs-lookup"><span data-stu-id="380e0-111">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-basic"></a><span data-ttu-id="380e0-112">在 Visual Basic 中將結構描述和資料從某個資料庫傳送到另一個資料庫</span><span class="sxs-lookup"><span data-stu-id="380e0-112">Transferring Schema and Data from One Database to Another in Visual Basic</span></span>  
 <span data-ttu-id="380e0-113">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件，將結構描述和資料從某個資料庫傳送到另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="380e0-113">This code example shows how to transfer schema and data from one database to another using the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object.</span></span>  
  
```vb
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Create a new database that is to be destination database.
Dim dbCopy As Database
dbCopy = New Database(srv, "AdventureWorks2012Copy")
dbCopy.Create()
'Define a Transfer object and set the required options and properties.
Dim xfr As Transfer
xfr = New Transfer(db)
xfr.CopyAllTables = True
xfr.Options.WithDependencies = True
xfr.Options.ContinueScriptingOnError = True
xfr.DestinationDatabase = "AdventureWorks2012Copy"
xfr.DestinationServer = srv.Name
xfr.DestinationLoginSecure = True
xfr.CopySchema = True
'Script the transfer. Alternatively perform immediate data transfer with TransferData method.
xfr.ScriptTransfer()
```
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-visual-c"></a><span data-ttu-id="380e0-114">在 Visual C# 中將結構描述和資料從某個資料庫傳送到另一個資料庫</span><span class="sxs-lookup"><span data-stu-id="380e0-114">Transferring Schema and Data from One Database to Another in Visual C#</span></span>  
 <span data-ttu-id="380e0-115">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件，將結構描述和資料從某個資料庫傳送到另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="380e0-115">This code example shows how to transfer schema and data from one database to another using the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object.</span></span>  
  
```csharp
{  
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Create a new database that is to be destination database.   
            Database dbCopy;  
            dbCopy = new Database(srv, "AdventureWorks2012Copy");  
            dbCopy.Create();  
            //Define a Transfer object and set the required options and properties.   
            Transfer xfr;  
            xfr = new Transfer(db);  
            xfr.CopyAllTables = true;  
            xfr.Options.WithDependencies = true;  
            xfr.Options.ContinueScriptingOnError = true;  
            xfr.DestinationDatabase = "AdventureWorks2012Copy";  
            xfr.DestinationServer = srv.Name;  
            xfr.DestinationLoginSecure = true;  
            xfr.CopySchema = true;  
            //Script the transfer. Alternatively perform immediate data transfer   
            // with TransferData method.   
            xfr.ScriptTransfer();  
        }   
```  
  
## <a name="transferring-schema-and-data-from-one-database-to-another-in-powershell"></a><span data-ttu-id="380e0-116">在 PowerShell 中將結構描述和資料從某個資料庫傳送到另一個資料庫</span><span class="sxs-lookup"><span data-stu-id="380e0-116">Transferring Schema and Data from One Database to Another in PowerShell</span></span>  
 <span data-ttu-id="380e0-117">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.Transfer> 物件，將結構描述和資料從某個資料庫傳送到另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="380e0-117">This code example shows how to transfer schema and data from one database to another using the <xref:Microsoft.SqlServer.Management.Smo.Transfer> object.</span></span>  
  
```powershell
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Reference the AdventureWorks2012 database.  
$db = $srv.Databases["AdventureWorks2012"]  
  
#Create a database to hold the copy of AdventureWorks  
$dbCopy = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Database -ArgumentList $srv, "AdventureWorksCopy"  
$dbCopy.Create()  
  
#Define a Transfer object and set the required options and properties.  
$xfr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Transfer -ArgumentList $db  
  
#Set this objects properties  
$xfr.CopyAllTables = $true  
$xfr.Options.WithDependencies = $true  
$xfr.Options.ContinueScriptingOnError = $true  
$xfr.DestinationDatabase = "AdventureWorksCopy"  
$xfr.DestinationServer = $srv.Name  
$xfr.DestinationLoginSecure = $true  
$xfr.CopySchema = $true  
"Scripting Data Transfer"  
#Script the transfer. Alternatively perform immediate data transfer with TransferData method.  
$xfr.ScriptTransfer()  
```  
