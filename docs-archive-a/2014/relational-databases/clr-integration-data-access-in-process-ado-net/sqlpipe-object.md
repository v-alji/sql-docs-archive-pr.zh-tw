---
title: SqlPipe 物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 0044815a0b20d72b48b87bfe8f693d7196aaeaf3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597167"
---
# <a name="sqlpipe-object"></a><span data-ttu-id="fb96d-102">SqlPipe 物件</span><span class="sxs-lookup"><span data-stu-id="fb96d-102">SqlPipe Object</span></span>
  <span data-ttu-id="fb96d-103">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，通常會撰寫將結果或輸出參數傳送至呼叫用戶端的預存程序 (或擴充的預存程序)。</span><span class="sxs-lookup"><span data-stu-id="fb96d-103">In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it is very common to write a stored procedure (or an extended stored procedure) that sends results or output parameters to the calling client.</span></span>  
  
 <span data-ttu-id="fb96d-104">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序中，傳回零或多個資料列的任何 `SELECT` 陳述式都會將結果傳送至已連接之呼叫端的「管道」。</span><span class="sxs-lookup"><span data-stu-id="fb96d-104">In a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, any `SELECT` statement that returns zero or more rows sends the results to the connected caller's "pipe."</span></span>  
  
 <span data-ttu-id="fb96d-105">如果是在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中執行的 Common Language Runtime (CLR) 資料庫物件，您可以使用 `Send` 物件的 `SqlPipe` 方法，將結果傳送至已連接的管道。</span><span class="sxs-lookup"><span data-stu-id="fb96d-105">For common language runtime (CLR) database objects running in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you can send results to the connected pipe using the `Send` methods of the `SqlPipe` object.</span></span> <span data-ttu-id="fb96d-106">請存取 `Pipe` 物件的 `SqlContext` 屬性來取得 `SqlPipe` 物件。</span><span class="sxs-lookup"><span data-stu-id="fb96d-106">Access the `Pipe` property of the `SqlContext` object to obtain the `SqlPipe` object.</span></span> <span data-ttu-id="fb96d-107">`SqlPipe` 類別在概念上類似於在 ASP.NET 中找到的 `Response` 類別。</span><span class="sxs-lookup"><span data-stu-id="fb96d-107">The `SqlPipe` class is conceptually similar to the `Response` class found in ASP.NET.</span></span> <span data-ttu-id="fb96d-108">如需詳細資訊，請參閱 .NET Framework 軟體開發套件中的 SqlPipe 類別參考文件集。</span><span class="sxs-lookup"><span data-stu-id="fb96d-108">For more information, see the SqlPipe Class reference documentation in the .NET Framework software development kit.</span></span>  
  
## <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="fb96d-109">傳回表格式結果和訊息</span><span class="sxs-lookup"><span data-stu-id="fb96d-109">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="fb96d-110">`SqlPipe` 有一個 `Send` 方法，這個方法具有三個多載。</span><span class="sxs-lookup"><span data-stu-id="fb96d-110">The `SqlPipe` has a `Send` method, which has three overloads.</span></span> <span data-ttu-id="fb96d-111">其中包括：</span><span class="sxs-lookup"><span data-stu-id="fb96d-111">They are:</span></span>  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 <span data-ttu-id="fb96d-112">`Send` 方法會將資料直接傳送至用戶端或呼叫端。</span><span class="sxs-lookup"><span data-stu-id="fb96d-112">The `Send` method sends data straight to the client or caller.</span></span> <span data-ttu-id="fb96d-113">取用 `SqlPipe` 輸出的通常是用戶端，但在巢狀 CLR 預存程序的情況下，輸出取用者也可能是預存程序。</span><span class="sxs-lookup"><span data-stu-id="fb96d-113">It is usually the client that consumes the output from the `SqlPipe`, but in the case of nested CLR stored procedures the output consumer can also be a stored procedure.</span></span> <span data-ttu-id="fb96d-114">例如，Procedure1 會使用命令文字 "EXEC Procedure2" 呼叫 SqlCommand.ExecuteReader()。</span><span class="sxs-lookup"><span data-stu-id="fb96d-114">For example, Procedure1 calls SqlCommand.ExecuteReader() with the command text "EXEC Procedure2".</span></span> <span data-ttu-id="fb96d-115">而 Procedure2 也是 Managed 預存程序。</span><span class="sxs-lookup"><span data-stu-id="fb96d-115">Procedure2 is also a managed stored procedure.</span></span> <span data-ttu-id="fb96d-116">如果 Procedure2 此時呼叫 SqlPipe.Send( SqlDataRecord )，資料列便會傳送至 Procedure1 的讀取器 (Reader)，而非用戶端。</span><span class="sxs-lookup"><span data-stu-id="fb96d-116">If Procedure2 now calls SqlPipe.Send( SqlDataRecord ), the row is sent to Procedure1's reader, not the client.</span></span>  
  
 <span data-ttu-id="fb96d-117">`Send` 方法會傳送字串訊息，此訊息會以資訊訊息顯示在用戶端上，與 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中的 PRINT 相等。</span><span class="sxs-lookup"><span data-stu-id="fb96d-117">The `Send` method sends a string message that appears on the client as an information message, equivalent to PRINT in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fb96d-118">它也可以使用 `SqlDataRecord` 傳送單一資料列的結果集，或使用 `SqlDataReader` 傳送多重資料列的結果集。</span><span class="sxs-lookup"><span data-stu-id="fb96d-118">It can also send a single-row result-set using `SqlDataRecord`, or a multi-row result-set using a `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="fb96d-119">`SqlPipe` 物件還擁有 `ExecuteAndSend` 方法。</span><span class="sxs-lookup"><span data-stu-id="fb96d-119">The `SqlPipe` object also has an `ExecuteAndSend` method.</span></span> <span data-ttu-id="fb96d-120">此方法可用來執行命令 (做為 `SqlCommand` 物件傳遞)，並將結果直接傳送回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="fb96d-120">This method can be used to execute a command (passed as a `SqlCommand` object) and send results directly back to the caller.</span></span> <span data-ttu-id="fb96d-121">如果已提交的命令中出現錯誤，便會將例外狀況 (Exception) 傳送至管道，但也會傳送複本給呼叫的 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="fb96d-121">If there are errors in the command that was submitted, exceptions are sent to the pipe, but a copy is also sent to calling managed code.</span></span> <span data-ttu-id="fb96d-122">如果呼叫程式碼未攔截到例外狀況，它會將堆疊向上傳播至 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，並在輸出中出現兩次。</span><span class="sxs-lookup"><span data-stu-id="fb96d-122">If the calling code does not catch the exception, it propagates up the stack to the [!INCLUDE[tsql](../../includes/tsql-md.md)] code and appears in the output twice.</span></span> <span data-ttu-id="fb96d-123">如果呼叫程式碼攔截到例外狀況，管道取用者還是會看到錯誤，但是不會有重複的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fb96d-123">If the calling code does catch the exception, the pipe consumer still sees the error, but there is not a duplicate error.</span></span>  
  
 <span data-ttu-id="fb96d-124">它只能使用與內容連接相關聯的 `SqlCommand`；而無法使用與非內容連接相關聯的命令。</span><span class="sxs-lookup"><span data-stu-id="fb96d-124">It can only take a `SqlCommand` that is associated with the context connection; it cannot take a command that is associated with the non-context connection.</span></span>  
  
## <a name="returning-custom-result-sets"></a><span data-ttu-id="fb96d-125">傳回自訂結果集</span><span class="sxs-lookup"><span data-stu-id="fb96d-125">Returning Custom Result Sets</span></span>  
 <span data-ttu-id="fb96d-126">Managed 預存程序可以傳送並非來自 `SqlDataReader` 的結果集。</span><span class="sxs-lookup"><span data-stu-id="fb96d-126">Managed stored procedures can send result sets that do not come from a `SqlDataReader`.</span></span> <span data-ttu-id="fb96d-127">`SendResultsStart` 方法及 `SendResultsRow` 與 `SendResultsEnd` 允許預存程序將自訂結果集傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="fb96d-127">The `SendResultsStart` method, along with `SendResultsRow` and `SendResultsEnd`, allows stored procedures to send custom result sets to the client.</span></span>  
  
 <span data-ttu-id="fb96d-128">`SendResultsStart` 會將 `SqlDataRecord` 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="fb96d-128">`SendResultsStart` takes a `SqlDataRecord` as an input.</span></span> <span data-ttu-id="fb96d-129">它會標示結果集的開頭，並使用記錄中繼資料來建構說明結果集的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fb96d-129">It marks the beginning of a result set and uses the record metadata to construct the metadata that describes the result set.</span></span> <span data-ttu-id="fb96d-130">它不使用 `SendResultsStart` 傳送記錄的值。</span><span class="sxs-lookup"><span data-stu-id="fb96d-130">It does not send the value of the record with `SendResultsStart`.</span></span> <span data-ttu-id="fb96d-131">所有使用 `SendResultsRow` 傳送的後續資料列，都必須符合該中繼資料定義。</span><span class="sxs-lookup"><span data-stu-id="fb96d-131">All the subsequent rows, sent using `SendResultsRow`, must match that metadata definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fb96d-132">呼叫 `SendResultsStart` 方法之後，只能呼叫 `SendResultsRow` 及 `SendResultsEnd`。</span><span class="sxs-lookup"><span data-stu-id="fb96d-132">After calling the `SendResultsStart` method only `SendResultsRow` and `SendResultsEnd` can be called.</span></span> <span data-ttu-id="fb96d-133">在相同的 `SqlPipe` 執行個體中呼叫任何其他方法會導致 `InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="fb96d-133">Calling any other method in the same instance of `SqlPipe` causes an `InvalidOperationException`.</span></span> <span data-ttu-id="fb96d-134">`SendResultsEnd` 會將 `SqlPipe` 設定為可以呼叫其他方法的初始狀態。</span><span class="sxs-lookup"><span data-stu-id="fb96d-134">`SendResultsEnd` sets `SqlPipe` back to the initial state in which other methods can be called.</span></span>  
  
### <a name="example"></a><span data-ttu-id="fb96d-135">範例</span><span class="sxs-lookup"><span data-stu-id="fb96d-135">Example</span></span>  
 <span data-ttu-id="fb96d-136">`uspGetProductLine` 預存程序會傳回指定產品線內所有產品的名稱、產品編號、色彩和標價。</span><span class="sxs-lookup"><span data-stu-id="fb96d-136">The `uspGetProductLine` stored procedure returns the name, product number, color, and list price of all products within a specified product line.</span></span> <span data-ttu-id="fb96d-137">這個預存程式會接受與*prodLine*完全相符的專案。</span><span class="sxs-lookup"><span data-stu-id="fb96d-137">This stored procedure accepts exact matches for *prodLine*.</span></span>  
  
 <span data-ttu-id="fb96d-138">C#</span><span class="sxs-lookup"><span data-stu-id="fb96d-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 <span data-ttu-id="fb96d-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb96d-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="fb96d-140">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會執行 `uspGetProduct` 程序，以傳回休閒車產品的清單。</span><span class="sxs-lookup"><span data-stu-id="fb96d-140">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement executes the `uspGetProduct` procedure, which returns a list of touring bike products.</span></span>  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb96d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb96d-141">See Also</span></span>  
 <span data-ttu-id="fb96d-142">[SqlDataRecord 物件](sqldatarecord-object.md) </span><span class="sxs-lookup"><span data-stu-id="fb96d-142">[SqlDataRecord Object](sqldatarecord-object.md) </span></span>  
 <span data-ttu-id="fb96d-143">[CLR 預存程式](../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="fb96d-143">[CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="fb96d-144">ADO.NET 的 SQL Server 同處理序特定擴充</span><span class="sxs-lookup"><span data-stu-id="fb96d-144">SQL Server In-Process Specific Extensions to ADO.NET</span></span>](sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
