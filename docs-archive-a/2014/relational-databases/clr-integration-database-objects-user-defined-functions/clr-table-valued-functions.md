---
title: CLR 資料表值函式 |Microsoft Docs
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
- Transact-SQL table-valued functions
- table-valued functions [CLR integration]
- TVFs [CLR integration]
ms.assetid: 9a6133ea-36e9-45bf-b572-1c0df3d6c194
author: rothja
ms.author: jroth
ms.openlocfilehash: b700aba5a753ecd8ee50ee9b7679cafb2f1f8581
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596735"
---
# <a name="clr-table-valued-functions"></a><span data-ttu-id="305a6-102">CLR 資料表值函式</span><span class="sxs-lookup"><span data-stu-id="305a6-102">CLR Table-Valued Functions</span></span>
  <span data-ttu-id="305a6-103">資料表值函式是會傳回資料表的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="305a6-103">A table-valued function is a user-defined function that returns a table.</span></span>  
  
 <span data-ttu-id="305a6-104">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可讓您以任何 Managed 語言定義資料表值函式，藉以擴充資料表值函式的功能。</span><span class="sxs-lookup"><span data-stu-id="305a6-104">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] extends the functionality of table-valued functions by allowing you to define a table-valued function in any managed language.</span></span> <span data-ttu-id="305a6-105">資料會透過 `IEnumerable` 或 `IEnumerator` 物件，從資料表值函式傳回。</span><span class="sxs-lookup"><span data-stu-id="305a6-105">Data is returned from a table-valued function through an `IEnumerable` or `IEnumerator` object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="305a6-106">對於資料表值函式而言，傳回資料表類型的資料行不得包含時間戳記資料行或非 Unicode 字串資料類型資料行 (例如，`char`、`varchar` 和 `text`)。</span><span class="sxs-lookup"><span data-stu-id="305a6-106">For table-valued functions, the columns of the return table type cannot include timestamp columns or non-Unicode string data type columns (such as `char`, `varchar`, and `text`).</span></span> <span data-ttu-id="305a6-107">不支援 NOT NULL 條件約束。</span><span class="sxs-lookup"><span data-stu-id="305a6-107">The NOT NULL constraint is not supported.</span></span>  
  
## <a name="differences-between-transact-sql-and-clr-table-valued-functions"></a><span data-ttu-id="305a6-108">Transact-SQL 和 CLR 資料表值函式之間的差異</span><span class="sxs-lookup"><span data-stu-id="305a6-108">Differences Between Transact-SQL and CLR Table-Valued Functions</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="305a6-109">資料表值函式會將呼叫函數的結果具體化為中繼資料表。</span><span class="sxs-lookup"><span data-stu-id="305a6-109">table-valued functions materialize the results of calling the function into an intermediate table.</span></span> <span data-ttu-id="305a6-110">由於 TVF 使用中繼資料表，因此可以透過結果支援條件約束和唯一的索引。</span><span class="sxs-lookup"><span data-stu-id="305a6-110">Since they use an intermediate table, they can support constraints and unique indexes over the results.</span></span> <span data-ttu-id="305a6-111">當傳回較大的結果時，這些功能會非常有用。</span><span class="sxs-lookup"><span data-stu-id="305a6-111">These features can be extremely useful when large results are returned.</span></span>  
  
 <span data-ttu-id="305a6-112">相反地，CLR 資料表值函式則是屬於以資料流模型進行處理的替代方案。</span><span class="sxs-lookup"><span data-stu-id="305a6-112">In contrast, CLR table-valued functions represent a streaming alternative.</span></span> <span data-ttu-id="305a6-113">整組結果不需要在單一資料表中具體化。</span><span class="sxs-lookup"><span data-stu-id="305a6-113">There is no requirement that the entire set of results be materialized in a single table.</span></span> <span data-ttu-id="305a6-114">Managed 函數所傳回的 `IEnumerable` 物件會透過呼叫資料表值函式的查詢執行計畫直接呼叫，而其結果會以累加的方式取用。</span><span class="sxs-lookup"><span data-stu-id="305a6-114">The `IEnumerable` object returned by the managed function is directly called by the execution plan of the query that calls the table-valued function, and the results are consumed in an incremental manner.</span></span> <span data-ttu-id="305a6-115">此資料流模型能確保第一個資料列可供使用之後，就立即使用結果，而不會等待整個資料表填入完成。</span><span class="sxs-lookup"><span data-stu-id="305a6-115">This streaming model ensures that results can be consumed immediately after the first row is available, instead of waiting for the entire table to be populated.</span></span> <span data-ttu-id="305a6-116">如果傳回大量的資料列，這也是一個較好的替代方式，因為它們不必整體在記憶體中進行實體化。</span><span class="sxs-lookup"><span data-stu-id="305a6-116">It is also a better alternative if you have very large numbers of rows returned, because they do not have to be materialized in memory as a whole.</span></span> <span data-ttu-id="305a6-117">例如，Managed 資料表值函式可用來剖析文字檔案，並將每一行以資料列的方式傳回。</span><span class="sxs-lookup"><span data-stu-id="305a6-117">For example, a managed table-valued function could be used to parse a text file and return each line as a row.</span></span>  
  
## <a name="implementing-table-valued-functions"></a><span data-ttu-id="305a6-118">實作資料表數值函數</span><span class="sxs-lookup"><span data-stu-id="305a6-118">Implementing Table-Valued Functions</span></span>  
 <span data-ttu-id="305a6-119">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 組件中，將資料表值函式當做類別上的方法實作。</span><span class="sxs-lookup"><span data-stu-id="305a6-119">Implement table-valued functions as methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="305a6-120">您的資料表值函式程式碼必須實作 `IEnumerable` 介面。</span><span class="sxs-lookup"><span data-stu-id="305a6-120">Your table-valued function code must implement the `IEnumerable` interface.</span></span> <span data-ttu-id="305a6-121">`IEnumerable` 介面是在 .NET Framework 中定義的。</span><span class="sxs-lookup"><span data-stu-id="305a6-121">The `IEnumerable` interface is defined in the .NET Framework.</span></span> <span data-ttu-id="305a6-122">在 .NET Framework 中，代表陣列和集合的類型已經實作 `IEnumerable` 介面。</span><span class="sxs-lookup"><span data-stu-id="305a6-122">Types representing arrays and collections in the .NET Framework already implement the `IEnumerable` interface.</span></span> <span data-ttu-id="305a6-123">這樣您就可以輕易地撰寫出能將集合或陣列轉換為結果集的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="305a6-123">This makes it easy for writing table-valued functions that convert a collection or an array into a result set.</span></span>  
  
## <a name="table-valued-parameters"></a><span data-ttu-id="305a6-124">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="305a6-124">Table-Valued Parameters</span></span>  
 <span data-ttu-id="305a6-125">資料表值參數是傳入到程序或函數中的使用者定義資料表類型，能提供有效的方式將資料的多個資料列傳遞到伺服器。</span><span class="sxs-lookup"><span data-stu-id="305a6-125">Table-valued parameters are user-defined table types that are passed into a procedure or function and provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="305a6-126">資料表值參數提供的功能與參數陣列相似，但是具備了更大的彈性並且和 [!INCLUDE[tsql](../../includes/tsql-md.md)] 更緊密地整合。</span><span class="sxs-lookup"><span data-stu-id="305a6-126">Table-valued parameters provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="305a6-127">它們也能夠協助您獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="305a6-127">They also provide the potential for better performance.</span></span> <span data-ttu-id="305a6-128">資料表值參數也可以減少與伺服器之間的往返次數。</span><span class="sxs-lookup"><span data-stu-id="305a6-128">Table-valued parameters also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="305a6-129">資料能以資料表值參數的形式傳送到伺服器，而不是傳送多個要求到伺服器，例如一併傳送純量參數的清單。</span><span class="sxs-lookup"><span data-stu-id="305a6-129">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a table-valued parameter.</span></span> <span data-ttu-id="305a6-130">使用者定義資料表類型無法以資料表值參數的形式傳遞到 Managed 預存程序或在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序中執行的函數，也無法從該預存程序或函數傳回。</span><span class="sxs-lookup"><span data-stu-id="305a6-130">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="305a6-131">如需詳細資訊，請參閱[使用資料表值參數 &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="305a6-131">For more information about table-valued parameters, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="output-parameters-and-table-valued-functions"></a><span data-ttu-id="305a6-132">輸出參數和資料表值函式</span><span class="sxs-lookup"><span data-stu-id="305a6-132">Output Parameters and Table-Valued Functions</span></span>  
 <span data-ttu-id="305a6-133">資訊可以使用輸出參數，從資料表值函式傳回。</span><span class="sxs-lookup"><span data-stu-id="305a6-133">Information may be returned from table-valued functions using output parameters.</span></span> <span data-ttu-id="305a6-134">實作程式碼資料表值函式中的對應參數應使用依參照傳遞的參數做為引數。</span><span class="sxs-lookup"><span data-stu-id="305a6-134">The corresponding parameter in the implementation code table-valued function should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="305a6-135">請注意，Visual Basic 不支援輸出參數的方式，與 Visual C# 所使用的方式不同。</span><span class="sxs-lookup"><span data-stu-id="305a6-135">Note that Visual Basic does not support output parameters in the same way that Visual C# does.</span></span> <span data-ttu-id="305a6-136">您必須依參考指定參數，並套用 \<Out()> 屬性來表示輸出參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="305a6-136">You must specify the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
...  
Public Shared Sub FillRow ( <Out()> ByRef value As SqlInt32)  
```  
  
### <a name="defining-a-table-valued-function-in-transact-sql"></a><span data-ttu-id="305a6-137">在 Transact-SQL 中定義資料表值函式</span><span class="sxs-lookup"><span data-stu-id="305a6-137">Defining a Table-Valued Function in Transact-SQL</span></span>  
 <span data-ttu-id="305a6-138">定義 CLR 資料表值函式的語法類似於 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料表值函式的語法，但是加入了 `EXTERNAL NAME` 子句。</span><span class="sxs-lookup"><span data-stu-id="305a6-138">The syntax for defining a CLR table-valued function is similar to that of a [!INCLUDE[tsql](../../includes/tsql-md.md)] table-valued function, with the addition of the `EXTERNAL NAME` clause.</span></span> <span data-ttu-id="305a6-139">例如：</span><span class="sxs-lookup"><span data-stu-id="305a6-139">For example:</span></span>  
  
```  
CREATE FUNCTION GetEmpFirstLastNames()  
RETURNS TABLE (FirstName NVARCHAR(4000), LastName NVARCHAR(4000))  
EXTERNAL NAME MyDotNETAssembly.[MyNamespace.MyClassname]. GetEmpFirstLastNames;  
```  
  
 <span data-ttu-id="305a6-140">資料表值函式用於以關聯式形式表示資料，以便在查詢中進行進一步的處理，例如：</span><span class="sxs-lookup"><span data-stu-id="305a6-140">Table-valued functions are used to represent data in relational form for further processing in queries such as:</span></span>  
  
```  
select * from function();  
select * from tbl join function() f on tbl.col = f.col;  
select * from table t cross apply function(t.column);  
```  
  
 <span data-ttu-id="305a6-141">當資料表值函式符合下列條件時，便會傳回資料表：</span><span class="sxs-lookup"><span data-stu-id="305a6-141">Table-valued functions can return a table when:</span></span>  
  
-   <span data-ttu-id="305a6-142">當資料表值函式是從純量輸入引數建立時。</span><span class="sxs-lookup"><span data-stu-id="305a6-142">Created from scalar input arguments.</span></span> <span data-ttu-id="305a6-143">例如，採用逗號分隔數字字串，並將它們樞紐至資料表的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="305a6-143">For example, a table-valued function that takes a comma-delimited string of numbers and pivots them into a table.</span></span>  
  
-   <span data-ttu-id="305a6-144">當資料表值函式是從外部資料產生時。</span><span class="sxs-lookup"><span data-stu-id="305a6-144">Generated from external data.</span></span> <span data-ttu-id="305a6-145">例如，讀取事件記錄檔並將其以資料表的方式公開的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="305a6-145">For example, a table-valued function that reads the event log and exposes it as a table.</span></span>  
  
 <span data-ttu-id="305a6-146">**注意**資料表值函式只能透過 [!INCLUDE[tsql](../../includes/tsql-md.md)] 方法中的查詢 `InitMethod` ，而不是在方法中執行資料存取 `FillRow` 。</span><span class="sxs-lookup"><span data-stu-id="305a6-146">**Note** A table-valued function can only perform data access through a [!INCLUDE[tsql](../../includes/tsql-md.md)] query in the `InitMethod` method, and not in the `FillRow` method.</span></span> <span data-ttu-id="305a6-147">如果執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢，應該以 `InitMethod` 屬性 (Attribute) 的屬性 (Property) 來標記 `SqlFunction.DataAccess.Read`。</span><span class="sxs-lookup"><span data-stu-id="305a6-147">The `InitMethod` should be marked with the `SqlFunction.DataAccess.Read` attribute property if a [!INCLUDE[tsql](../../includes/tsql-md.md)] query is performed.</span></span>  
  
## <a name="a-sample-table-valued-function"></a><span data-ttu-id="305a6-148">資料表值函式範例</span><span class="sxs-lookup"><span data-stu-id="305a6-148">A Sample Table-Valued Function</span></span>  
 <span data-ttu-id="305a6-149">下列資料表值函式會從系統事件記錄檔傳回資訊。</span><span class="sxs-lookup"><span data-stu-id="305a6-149">The following table-valued function returns information from the system event log.</span></span> <span data-ttu-id="305a6-150">該函數使用包含要讀取之事件記錄檔名稱的單一字串引數。</span><span class="sxs-lookup"><span data-stu-id="305a6-150">The function takes a single string argument containing the name of the event log to read.</span></span>  
  
###### <a name="sample-code"></a><span data-ttu-id="305a6-151">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="305a6-151">Sample Code</span></span>  
  
```csharp  
using System;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Collections;  
using System.Data.SqlTypes;  
using System.Diagnostics;  
  
public class TabularEventLog  
{  
    [SqlFunction(FillRowMethodName = "FillRow")]  
    public static IEnumerable InitMethod(String logname)  
    {  
        return new EventLog(logname).Entries;    }  
  
    public static void FillRow(Object obj, out SqlDateTime timeWritten, out SqlChars message, out SqlChars category, out long instanceId)  
    {  
        EventLogEntry eventLogEntry = (EventLogEntry)obj;  
        timeWritten = new SqlDateTime(eventLogEntry.TimeWritten);  
        message = new SqlChars(eventLogEntry.Message);  
        category = new SqlChars(eventLogEntry.Category);  
        instanceId = eventLogEntry.InstanceId;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data.Sql  
Imports Microsoft.SqlServer.Server  
Imports System.Collections  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Public Class TabularEventLog  
    <SqlFunction(FillRowMethodName:="FillRow")> _  
    Public Shared Function InitMethod(ByVal logname As String) As IEnumerable  
        Return New EventLog(logname).Entries  
    End Function  
  
    Public Shared Sub FillRow(ByVal obj As Object, <Out()> ByRef timeWritten As SqlDateTime, <Out()> ByRef message As SqlChars, <Out()> ByRef category As SqlChars, <Out()> ByRef instanceId As Long)  
        Dim eventLogEnTry As EventLogEntry = CType(obj, EventLogEntry)  
        timeWritten = New SqlDateTime(eventLogEnTry.TimeWritten)  
        message = New SqlChars(eventLogEnTry.Message)  
        category = New SqlChars(eventLogEnTry.Category)  
        instanceId = eventLogEnTry.InstanceId  
    End Sub  
End Class  
```  
  
###### <a name="declaring-and-using-the-sample-table-valued-function"></a><span data-ttu-id="305a6-152">宣告和使用範例資料表值函式</span><span class="sxs-lookup"><span data-stu-id="305a6-152">Declaring and Using the Sample Table-Valued Function</span></span>  
 <span data-ttu-id="305a6-153">在範例資料表值函式經過編譯之後，就可以在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中以下列的方式宣告：</span><span class="sxs-lookup"><span data-stu-id="305a6-153">After the sample table-valued function has been compiled, it can be declared in [!INCLUDE[tsql](../../includes/tsql-md.md)] like this:</span></span>  
  
```  
use master;  
-- Replace SQL_Server_logon with your SQL Server user credentials.  
GRANT EXTERNAL ACCESS ASSEMBLY TO [SQL_Server_logon];   
-- Modify the following line to specify a different database.  
ALTER DATABASE master SET TRUSTWORTHY ON;  
  
-- Modify the next line to use the appropriate database.  
CREATE ASSEMBLY tvfEventLog   
FROM 'D:\assemblies\tvfEventLog\tvfeventlog.dll'   
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
CREATE FUNCTION ReadEventLog(@logname nvarchar(100))  
RETURNS TABLE   
(logTime datetime,Message nvarchar(4000),Category nvarchar(4000),InstanceId bigint)  
AS   
EXTERNAL NAME tvfEventLog.TabularEventLog.InitMethod;  
GO  
```  
  
 <span data-ttu-id="305a6-154">不支援在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 上執行使用 /clr:pure 編譯的 Visual C++ 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="305a6-154">Visual C++ database objects compiled with /clr:pure are not supported for execution on [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="305a6-155">例如，這類資料庫物件包括資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="305a6-155">For example, such database objects include table-valued functions.</span></span>  
  
 <span data-ttu-id="305a6-156">若要測試範例，請嘗試下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼：</span><span class="sxs-lookup"><span data-stu-id="305a6-156">To test the sample, try the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
```  
-- Select the top 100 events,  
SELECT TOP 100 *  
FROM dbo.ReadEventLog(N'Security') as T;  
go  
  
-- Select the last 10 login events.  
SELECT TOP 10 T.logTime, T.Message, T.InstanceId   
FROM dbo.ReadEventLog(N'Security') as T  
WHERE T.Category = N'Logon/Logoff';  
go  
```  
  
## <a name="sample-returning-the-results-of-a-sql-server-query"></a><span data-ttu-id="305a6-157">範例：傳回 SQL Server 查詢的結果</span><span class="sxs-lookup"><span data-stu-id="305a6-157">Sample: Returning the Results of a SQL Server Query</span></span>  
 <span data-ttu-id="305a6-158">下列範例示範查詢 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="305a6-158">The following sample shows a table-valued function that queries a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="305a6-159">這個範例使用 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 的 AdventureWorks Light 資料庫。</span><span class="sxs-lookup"><span data-stu-id="305a6-159">This sample uses the AdventureWorks Light database from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="305a6-160">[https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843)如需下載 AdventureWorks 的詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="305a6-160">See [https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843) for more information on downloading AdventureWorks.</span></span>  
  
 <span data-ttu-id="305a6-161">將原始程式碼檔命名為 FindInvalidEmails.cs 或 FindInvalidEmails.vb。</span><span class="sxs-lookup"><span data-stu-id="305a6-161">Name your source code file FindInvalidEmails.cs or FindInvalidEmails.vb.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
  
using Microsoft.SqlServer.Server;  
  
public partial class UserDefinedFunctions {  
   private class EmailResult {  
      public SqlInt32 CustomerId;  
      public SqlString EmailAdress;  
  
      public EmailResult(SqlInt32 customerId, SqlString emailAdress) {  
         CustomerId = customerId;  
         EmailAdress = emailAdress;  
      }  
   }  
  
   public static bool ValidateEmail(SqlString emailAddress) {  
      if (emailAddress.IsNull)  
         return false;  
  
      if (!emailAddress.Value.EndsWith("@adventure-works.com"))  
         return false;  
  
      // Validate the address. Put any more rules here.  
      return true;  
   }  
  
   [SqlFunction(  
       DataAccess = DataAccessKind.Read,  
       FillRowMethodName = "FindInvalidEmails_FillRow",  
       TableDefinition="CustomerId int, EmailAddress nvarchar(4000)")]  
   public static IEnumerable FindInvalidEmails(SqlDateTime modifiedSince) {  
      ArrayList resultCollection = new ArrayList();  
  
      using (SqlConnection connection = new SqlConnection("context connection=true")) {  
         connection.Open();  
  
         using (SqlCommand selectEmails = new SqlCommand(  
             "SELECT " +  
             "[CustomerID], [EmailAddress] " +  
             "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " +  
             "WHERE [ModifiedDate] >= @modifiedSince",  
             connection)) {  
            SqlParameter modifiedSinceParam = selectEmails.Parameters.Add(  
                "@modifiedSince",  
                SqlDbType.DateTime);  
            modifiedSinceParam.Value = modifiedSince;  
  
            using (SqlDataReader emailsReader = selectEmails.ExecuteReader()) {  
               while (emailsReader.Read()) {  
                  SqlString emailAddress = emailsReader.GetSqlString(1);  
                  if (ValidateEmail(emailAddress)) {  
                     resultCollection.Add(new EmailResult(  
                         emailsReader.GetSqlInt32(0),  
                         emailAddress));  
                  }  
               }  
            }  
         }  
      }  
  
      return resultCollection;  
   }  
  
   public static void FindInvalidEmails_FillRow(  
       object emailResultObj,  
       out SqlInt32 customerId,  
       out SqlString emailAdress) {  
      EmailResult emailResult = (EmailResult)emailResultObj;  
  
      customerId = emailResult.CustomerId;  
      emailAdress = emailResult.EmailAdress;  
   }  
};  
```  
  
```vb  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, ByRef customerId As SqlInt32, ByRef emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End ClassImports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, customerId As SqlInt32, emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="305a6-162">將原始程式碼編譯為 DLL，並且將這個 DLL 複製到 C 磁碟機的根目錄。</span><span class="sxs-lookup"><span data-stu-id="305a6-162">Compile the source code to a DLL and copy the DLL to the root directory of your C drive.</span></span>  <span data-ttu-id="305a6-163">接著執行下列的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="305a6-163">Then, execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] query.</span></span>  
  
```  
use AdventureWorksLT2008;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'FindInvalidEmails')  
   DROP FUNCTION FindInvalidEmails;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\FindInvalidEmails.dll'  
WITH PERMISSION_SET = SAFE -- EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION FindInvalidEmails(@ModifiedSince datetime)   
RETURNS TABLE (  
   CustomerId int,  
   EmailAddress nvarchar(4000)  
)  
AS EXTERNAL NAME MyClrCode.UserDefinedFunctions.[FindInvalidEmails];  
go  
  
SELECT * FROM FindInvalidEmails('2000-01-01');  
go  
```  
  
