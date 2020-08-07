---
title: 呼叫方法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- methods [SMO]
- calling methods
- SQL Server Management Objects, method calling
- SMO [SQL Server], method calling
ms.assetid: c88d5c5f-9ff0-4f84-b2b6-24c6b90fa15e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13216b4c533527d4249471073580d7c86f6b07e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704010"
---
# <a name="calling-methods"></a><span data-ttu-id="951e0-102">呼叫方法</span><span class="sxs-lookup"><span data-stu-id="951e0-102">Calling Methods</span></span>
  <span data-ttu-id="951e0-103">方法會執行與物件相關的特定工作，例如 `Checkpoint` 在資料庫上發出，或要求實例的登入列舉清單 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="951e0-103">Methods perform specific tasks related to the object, such as issuing a `Checkpoint` on a database or requesting an enumerated list of logons for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="951e0-104">方法會在物件上執行作業。</span><span class="sxs-lookup"><span data-stu-id="951e0-104">Methods perform an operation on an object.</span></span> <span data-ttu-id="951e0-105">方法可以採用參數，而且通常有一個傳回值。</span><span class="sxs-lookup"><span data-stu-id="951e0-105">Methods can take parameters and often have a return value.</span></span> <span data-ttu-id="951e0-106">傳回值可以是簡單資料類型、複雜物件，或包含許多成員的結構。</span><span class="sxs-lookup"><span data-stu-id="951e0-106">The return value can be a simple data type, a complex object, or a structure that contains many members.</span></span>  
  
 <span data-ttu-id="951e0-107">使用例外狀況處理來偵測方法是否成功。</span><span class="sxs-lookup"><span data-stu-id="951e0-107">Use exception handling to detect whether the method has been successful.</span></span> <span data-ttu-id="951e0-108">如需詳細資訊，請參閱 [Handling SMO Exceptions](handling-smo-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="951e0-108">For more information, see [Handling SMO Exceptions](handling-smo-exceptions.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="951e0-109">範例</span><span class="sxs-lookup"><span data-stu-id="951e0-109">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="using-a-simple-smo-method-in-visual-basic"></a><span data-ttu-id="951e0-110">在 Visual Basic 中使用簡單 SMO 方法</span><span class="sxs-lookup"><span data-stu-id="951e0-110">Using a Simple SMO Method in Visual Basic</span></span>  
 <span data-ttu-id="951e0-111">在此範例中，<xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> 方法不會採用任何參數，而且沒有傳回值。</span><span class="sxs-lookup"><span data-stu-id="951e0-111">In this example, the <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> method takes no parameters and has no return value.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods1](SMO How to#SMO_VBMethods1)]  -->  
  
## <a name="using-a-simple-smo-method-in-visual-c"></a><span data-ttu-id="951e0-112">在 Visual C# 中使用簡單 SMO 方法</span><span class="sxs-lookup"><span data-stu-id="951e0-112">Using a Simple SMO Method in Visual C#</span></span>  
 <span data-ttu-id="951e0-113">在此範例中，<xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> 方法不會採用任何參數，而且沒有傳回值。</span><span class="sxs-lookup"><span data-stu-id="951e0-113">In this example, the <xref:Microsoft.SqlServer.Management.Smo.Database.Create%2A> method takes no parameters and has no return value.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define a Database object variable by supplying the parent server and the database name arguments in the constructor.   
Database db;   
db = new Database(srv, "Test_SMO_Database");   
//Call the Create method to create the database on the instance of SQL Server.   
db.Create();   
```  
  
 <span data-ttu-id="951e0-114">}</span><span class="sxs-lookup"><span data-stu-id="951e0-114">}</span></span>  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-basic"></a><span data-ttu-id="951e0-115">在 Visual Basic 中搭配參數使用 SMO 方法</span><span class="sxs-lookup"><span data-stu-id="951e0-115">Using an SMO Method with a Parameter in Visual Basic</span></span>  
 <span data-ttu-id="951e0-116"><xref:Microsoft.SqlServer.Management.Smo.Table> 物件有一個稱為 <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A> 的方法。</span><span class="sxs-lookup"><span data-stu-id="951e0-116">The <xref:Microsoft.SqlServer.Management.Smo.Table> object has a method called <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>.</span></span> <span data-ttu-id="951e0-117">此方法需要指定 `FillFactor`的數值參數。</span><span class="sxs-lookup"><span data-stu-id="951e0-117">This method requires a numeric parameter that specifies the `FillFactor`.</span></span>  
  
```  
Dim srv As Server  
srv = New Server  
Dim tb As Table  
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources")  
tb.RebuildIndexes(70)  
```  
  
## <a name="using-an-smo-method-with-a-parameter-in-visual-c"></a><span data-ttu-id="951e0-118">在 Visual C# 中搭配參數使用 SMO 方法</span><span class="sxs-lookup"><span data-stu-id="951e0-118">Using an SMO Method with a Parameter in Visual C#</span></span>  
 <span data-ttu-id="951e0-119"><xref:Microsoft.SqlServer.Management.Smo.Table> 物件有一個稱為 <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A> 的方法。</span><span class="sxs-lookup"><span data-stu-id="951e0-119">The <xref:Microsoft.SqlServer.Management.Smo.Table> object has a method called <xref:Microsoft.SqlServer.Management.Smo.Table.RebuildIndexes%2A>.</span></span> <span data-ttu-id="951e0-120">此方法需要指定 `FillFactor`的數值參數。</span><span class="sxs-lookup"><span data-stu-id="951e0-120">This method requires a numeric parameter that specifies the `FillFactor`.</span></span>  
  
```  
{   
Server srv = default(Server);   
srv = new Server();   
Table tb = default(Table);   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
}   
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-basic"></a><span data-ttu-id="951e0-121">在 Visual Basic 中使用傳回 DataTable 物件的列舉方法</span><span class="sxs-lookup"><span data-stu-id="951e0-121">Using an Enumeration Method that Returns a DataTable Object in Visual Basic</span></span>  
 <span data-ttu-id="951e0-122">本節描述如何呼叫列舉方法，以及如何處理傳回之 <xref:System.Data.DataTable> 物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="951e0-122">This section describes how to call an enumeration method and how to handle the data in the returned <xref:System.Data.DataTable> object.</span></span>  
  
 <span data-ttu-id="951e0-123"><xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> 方法會傳回 <xref:System.Data.DataTable> 物件，此物件需要進一步導覽，才能存取有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的所有可用定序資訊。</span><span class="sxs-lookup"><span data-stu-id="951e0-123">The <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> method returns a <xref:System.Data.DataTable> object, which requires further navigation to access all available collation information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
'Connect to the local, default instance of SQL Server.  
Dim srv As Server  
srv = New Server  
'Call the EnumCollations method and return collation information to DataTable variable.  
Dim d As DataTable  
'Select the returned data into an array of DataRow.  
d = srv.EnumCollations  
'Iterate through the rows and display collation details for the instance of SQL Server.  
Dim r As DataRow  
Dim c As DataColumn  
For Each r In d.Rows  
    Console.WriteLine("==")  
    For Each c In r.Table.Columns  
        Console.WriteLine(c.ColumnName + " = " + r(c).ToString)  
    Next  
Next  
```  
  
## <a name="using-an-enumeration-method-that-returns-a-datatable-object-in-visual-c"></a><span data-ttu-id="951e0-124">在 Visual C# 中使用傳回 DataTable 物件的列舉方法</span><span class="sxs-lookup"><span data-stu-id="951e0-124">Using an Enumeration Method that Returns a DataTable Object in Visual C#</span></span>  
 <span data-ttu-id="951e0-125">本節描述如何呼叫列舉方法，以及如何處理傳回之 <xref:System.Data.DataTable> 物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="951e0-125">This section describes how to call an enumeration method and how to handle the data in the returned <xref:System.Data.DataTable> object.</span></span>  
  
 <span data-ttu-id="951e0-126"><xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> 方法會傳回系統 <xref:System.Data.DataTable> 物件。</span><span class="sxs-lookup"><span data-stu-id="951e0-126">The <xref:Microsoft.SqlServer.Management.Smo.Server.EnumCollations%2A> method returns a system <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="951e0-127"><xref:System.Data.DataTable> 物件需要進一步導覽，才能存取有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的所有可用定序資訊。</span><span class="sxs-lookup"><span data-stu-id="951e0-127">The <xref:System.Data.DataTable> object requires further navigation to access all available collation information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumCollations;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=========");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="constructing-an-object-in-visual-basic"></a><span data-ttu-id="951e0-128">在 Visual Basic 中建構物件</span><span class="sxs-lookup"><span data-stu-id="951e0-128">Constructing an Object in Visual Basic</span></span>  
 <span data-ttu-id="951e0-129">任何物件的建構函式都可以使用 `New` 運算子來呼叫。</span><span class="sxs-lookup"><span data-stu-id="951e0-129">The constructor of any object can be called by using the `New` operator.</span></span> <span data-ttu-id="951e0-130"><xref:Microsoft.SqlServer.Management.Smo.Database> 物件建構函式會超載，而範例中所使用的 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件建構函式版本會採用兩個參數：資料庫所屬的 <xref:Microsoft.SqlServer.Management.Smo.Server> 父物件，以及代表新資料庫名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="951e0-130">The <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor is overloaded and the version of the <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor that is used in the sample takes two parameters: the parent <xref:Microsoft.SqlServer.Management.Smo.Server> object to which the database belongs, and a string that represents the name of the new database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods4](SMO How to#SMO_VBMethods4)]  -->  
  
## <a name="constructing-an-object-in-visual-c"></a><span data-ttu-id="951e0-131">在 Visual C# 中建構物件</span><span class="sxs-lookup"><span data-stu-id="951e0-131">Constructing an Object in Visual C#</span></span>  
 <span data-ttu-id="951e0-132">任何物件的建構函式都可以使用 `New` 運算子來呼叫。</span><span class="sxs-lookup"><span data-stu-id="951e0-132">The constructor of any object can be called by using the `New` operator.</span></span> <span data-ttu-id="951e0-133"><xref:Microsoft.SqlServer.Management.Smo.Database> 物件建構函式會超載，而範例中所使用的 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件建構函式版本會採用兩個參數：資料庫所屬的 <xref:Microsoft.SqlServer.Management.Smo.Server> 父物件，以及代表新資料庫名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="951e0-133">The <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor is overloaded and the version of the <xref:Microsoft.SqlServer.Management.Smo.Database> object constructor that is used in the sample takes two parameters: the parent <xref:Microsoft.SqlServer.Management.Smo.Server> object to which the database belongs, and a string that represents the name of the new database.</span></span>  
  
```  
{   
Server srv;   
srv = new Server();   
Table tb;   
tb = srv.Databases("AdventureWorks2012").Tables("Employee", "HumanResources");   
tb.RebuildIndexes(70);   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Declare and define a Database object by supplying the parent server and the database name arguments in the constructor.   
Database d;   
d = new Database(srv, "Test_SMO_Database");   
//Create the database on the instance of SQL Server.   
d.Create();   
Console.WriteLine(d.Name);   
}  
```  
  
## <a name="copying-an-smo-object-in-visual-basic"></a><span data-ttu-id="951e0-134">在 Visual Basic 中複製 SMO 物件</span><span class="sxs-lookup"><span data-stu-id="951e0-134">Copying an SMO Object in Visual Basic</span></span>  
 <span data-ttu-id="951e0-135">此程式碼範例使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 方法來建立 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="951e0-135">This code example uses the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to create a copy of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="951e0-136"><xref:Microsoft.SqlServer.Management.Smo.Server> 物件代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="951e0-136">The <xref:Microsoft.SqlServer.Management.Smo.Server> object represents a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VCMethods6](SMO How to#SMO_VCMethods6)]  -->  
  
## <a name="copying-an-smo-object-in-visual-c"></a><span data-ttu-id="951e0-137">在 Visual C# 中複製 SMO 物件</span><span class="sxs-lookup"><span data-stu-id="951e0-137">Copying an SMO Object in Visual C#</span></span>  
 <span data-ttu-id="951e0-138">此程式碼範例使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 方法來建立 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="951e0-138">This code example uses the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to create a copy of the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span> <span data-ttu-id="951e0-139"><xref:Microsoft.SqlServer.Management.Smo.Server> 物件代表 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="951e0-139">The <xref:Microsoft.SqlServer.Management.Smo.Server> object represents a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv1;   
srv1 = new Server();   
//Modify the default database and the timeout period for the connection.   
srv1.ConnectionContext.DatabaseName = "AdventureWorks2012";   
srv1.ConnectionContext.ConnectTimeout = 30;   
//Make a second connection using a copy of the ConnectionContext property and verify settings.   
Server srv2;   
srv2 = new Server(srv1.ConnectionContext.Copy);   
Console.WriteLine(srv2.ConnectionContext.ConnectTimeout.ToString);   
}  
```  
  
## <a name="monitoring-server-processes-in-visual-basic"></a><span data-ttu-id="951e0-140">在 Visual Basic 中監視伺服器處理序</span><span class="sxs-lookup"><span data-stu-id="951e0-140">Monitoring Server Processes in Visual Basic</span></span>  
 <span data-ttu-id="951e0-141">您可以透過列舉方法取得 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體目前的狀態類型資訊。</span><span class="sxs-lookup"><span data-stu-id="951e0-141">You can obtain the current status type information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through enumeration methods.</span></span> <span data-ttu-id="951e0-142">程式碼範例會使用 <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> 方法來探索目前處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="951e0-142">The code example uses the <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> method to discover information about the current processes.</span></span> <span data-ttu-id="951e0-143">該範例也會示範如何使用傳回之 <xref:System.Data.DataTable> 物件中的資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="951e0-143">It also demonstrates how to work with the columns and rows in the returned <xref:System.Data.DataTable> object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMethods5](SMO How to#SMO_VBMethods5)]  -->  
  
## <a name="monitoring-server-processes-in-visual-c"></a><span data-ttu-id="951e0-144">在 Visual C# 中監視伺服器處理序</span><span class="sxs-lookup"><span data-stu-id="951e0-144">Monitoring Server Processes in Visual C#</span></span>  
 <span data-ttu-id="951e0-145">您可以透過列舉方法取得 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體目前的狀態類型資訊。</span><span class="sxs-lookup"><span data-stu-id="951e0-145">You can obtain the current status type information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through enumeration methods.</span></span> <span data-ttu-id="951e0-146">程式碼範例會使用 <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> 方法來探索目前處理序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="951e0-146">The code example uses the <xref:Microsoft.SqlServer.Management.Smo.Server.EnumProcesses%2A> method to discover information about the current processes.</span></span> <span data-ttu-id="951e0-147">該範例也會示範如何使用傳回之 <xref:System.Data.DataTable> 物件中的資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="951e0-147">It also demonstrates how to work with the columns and rows in the returned <xref:System.Data.DataTable> object.</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
//Call the EnumCollations method and return collation information to DataTable variable.   
DataTable d = default(DataTable);   
//Select the returned data into an array of DataRow.   
d = srv.EnumProcesses;   
//Iterate through the rows and display collation details for the instance of SQL Server.   
DataRow r = default(DataRow);   
DataColumn c = default(DataColumn);   
foreach ( r in d.Rows) {   
  Console.WriteLine("=====");   
  foreach ( c in r.Table.Columns) {   
    Console.WriteLine(c.ColumnName + " = " + r(c).ToString);   
  }   
}   
}   
```  
  
## <a name="see-also"></a><span data-ttu-id="951e0-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="951e0-148">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
