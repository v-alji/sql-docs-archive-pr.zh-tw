---
title: CLR 預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f8c69435e28bfa67c72e26b7a54e419cd91ef220
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593544"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="d298a-102">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="d298a-102">CLR Stored Procedures</span></span>
  <span data-ttu-id="d298a-103">預存程序是無法在純量運算式中使用的常式。</span><span class="sxs-lookup"><span data-stu-id="d298a-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="d298a-104">不像純量函數，它們可以將表格式結果及訊息傳回到用戶端、叫用資料定義語言 (DDL) 及資料操作語言 (DML) 陳述式，並傳回輸出參數。</span><span class="sxs-lookup"><span data-stu-id="d298a-104">Unlike scalar functions, they can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span> <span data-ttu-id="d298a-105">如需 CLR 整合的優點，以及在 managed 程式碼和之間選擇的詳細資訊 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，請參閱[CLR 整合的總覽](../../relational-databases/clr-integration/clr-integration-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d298a-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-stored-procedures"></a><span data-ttu-id="d298a-106">CLR 預存程序的需求</span><span class="sxs-lookup"><span data-stu-id="d298a-106">Requirements for CLR Stored Procedures</span></span>  
 <span data-ttu-id="d298a-107">在 common language runtime (CLR) 中，預存程式會實作為元件中類別的公用靜態方法 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d298a-107">In the common language runtime (CLR), stored procedures are implemented as public static methods on a class in a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] assembly.</span></span> <span data-ttu-id="d298a-108">靜態方法可宣告為 Void，或傳回整數值。</span><span class="sxs-lookup"><span data-stu-id="d298a-108">The static method can either be declared as void, or return an integer value.</span></span> <span data-ttu-id="d298a-109">如果它傳回整數值，則會將傳回的整數視為程序的傳回碼。</span><span class="sxs-lookup"><span data-stu-id="d298a-109">If it returns an integer value, the integer returned is treated as the return code from the procedure.</span></span> <span data-ttu-id="d298a-110">例如：</span><span class="sxs-lookup"><span data-stu-id="d298a-110">For example:</span></span>  
  
 `EXECUTE @return_status = procedure_name`  
  
 <span data-ttu-id="d298a-111">@return_status變數會包含方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d298a-111">The @return_status variable will contain the value returned by the method.</span></span> <span data-ttu-id="d298a-112">如果方法宣告為 Void，則傳回碼會是 0。</span><span class="sxs-lookup"><span data-stu-id="d298a-112">If the method is declared void, the return code is 0.</span></span>  
  
 <span data-ttu-id="d298a-113">如果方法採用參數，則 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 實作中的參數數目應與預存程序之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 宣告中使用的參數數目相同。</span><span class="sxs-lookup"><span data-stu-id="d298a-113">If the method takes parameters, the number of parameters in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] implementation should be the same as the number of parameters used in the [!INCLUDE[tsql](../../includes/tsql-md.md)] declaration of the stored procedure.</span></span>  
  
 <span data-ttu-id="d298a-114">傳遞至 CLR 預存程序的參數可以是在 Managed 程式碼中具有對等類型的任何原生 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型。</span><span class="sxs-lookup"><span data-stu-id="d298a-114">Parameters passed to a CLR stored procedure can be any of the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types that have an equivalent in managed code.</span></span> <span data-ttu-id="d298a-115">對於用以建立程序的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語法，應使用最適合的原生 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型對等類型來指定這些類型。</span><span class="sxs-lookup"><span data-stu-id="d298a-115">For the [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax to create the procedure, these types should be specified with the most appropriate native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type equivalent.</span></span> <span data-ttu-id="d298a-116">如需類型轉換的詳細資訊，請參閱[對應 CLR 參數資料](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d298a-116">For more information about type conversions, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="d298a-117">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="d298a-117">Table-Valued Parameters</span></span>  
 <span data-ttu-id="d298a-118">資料表值參數 (TVP) 是使用者定義資料表類型，會傳入到程序或函數中，提供有效的方式將資料的多個資料列傳遞到伺服器。</span><span class="sxs-lookup"><span data-stu-id="d298a-118">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="d298a-119">雖然 TVP 提供相似的功能給參數陣列，但是也提供更大的彈性和與 [!INCLUDE[tsql](../../includes/tsql-md.md)] 更緊密的整合。</span><span class="sxs-lookup"><span data-stu-id="d298a-119">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d298a-120">它們也能夠協助您獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="d298a-120">They also provide the potential for better performance.</span></span> <span data-ttu-id="d298a-121">TVP 也減少與伺服器之間的往返次數。</span><span class="sxs-lookup"><span data-stu-id="d298a-121">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="d298a-122">除了傳送多個要求到伺服器 (例如夾帶純量參數的清單)，資料能以 TVP 的形式傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="d298a-122">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="d298a-123">使用者定義資料表類型無法以資料表值參數的形式傳遞到 Managed 預存程序或在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序中執行的函數，也無法從該預存程序或函數傳回。</span><span class="sxs-lookup"><span data-stu-id="d298a-123">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="d298a-124">如需 Tvp 的詳細資訊，請參閱[使用資料表值參數 &#40;資料庫引擎&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="d298a-124">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="returning-results-from-clr-stored-procedures"></a><span data-ttu-id="d298a-125">傳回 CLR 預存程序的結果</span><span class="sxs-lookup"><span data-stu-id="d298a-125">Returning Results from CLR Stored Procedures</span></span>  
 <span data-ttu-id="d298a-126">有數種方式可從 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 預存程序傳回資訊。</span><span class="sxs-lookup"><span data-stu-id="d298a-126">Information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures in several ways.</span></span> <span data-ttu-id="d298a-127">這包括輸出參數、表格式結果及訊息。</span><span class="sxs-lookup"><span data-stu-id="d298a-127">This includes output parameters, tabular results, and messages.</span></span>  
  
### <a name="output-parameters-and-clr-stored-procedures"></a><span data-ttu-id="d298a-128">OUTPUT 參數與 CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="d298a-128">OUTPUT Parameters and CLR Stored Procedures</span></span>  
 <span data-ttu-id="d298a-129">與 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序一樣，資訊可透過 OUTPUT 參數，從 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 預存程序傳回。</span><span class="sxs-lookup"><span data-stu-id="d298a-129">As with [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures, information may be returned from [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures using OUTPUT parameters.</span></span> <span data-ttu-id="d298a-130">用於建立 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] DML 語法，與用於建立寫入 [!INCLUDE[tsql](../../includes/tsql-md.md)] 之預存程序的語法相同。</span><span class="sxs-lookup"><span data-stu-id="d298a-130">The [!INCLUDE[tsql](../../includes/tsql-md.md)] DML syntax used for creating [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stored procedures is the same as that used for creating stored procedures written in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="d298a-131">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別內實作程式碼中的對應參數應使用依參照傳遞的參數做為引數。</span><span class="sxs-lookup"><span data-stu-id="d298a-131">The corresponding parameter in the implementation code in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] class should use a pass-by-reference parameter as the argument.</span></span> <span data-ttu-id="d298a-132">請注意，Visual Basic 不支援與 c # 相同的輸出參數。</span><span class="sxs-lookup"><span data-stu-id="d298a-132">Note that Visual Basic does not support output parameters in the same way that C# does.</span></span> <span data-ttu-id="d298a-133">您必須依參考指定參數，並套用 \<Out()> 屬性來表示輸出參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d298a-133">You must specify the parameter by reference and apply the \<Out()> attribute to represent an OUTPUT parameter, as in the following:</span></span>  
  
```vb
Imports System.Runtime.InteropServices  
...  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 <span data-ttu-id="d298a-134">以下範例示範透過 OUT 參數傳回資訊的預存程序：</span><span class="sxs-lookup"><span data-stu-id="d298a-134">The following shows a stored procedure returning information through an OUTPUT parameter:</span></span>  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 <span data-ttu-id="d298a-135">一旦包含上述 CLR 預存程式的元件在伺服器上建立並建立之後， [!INCLUDE[tsql](../../includes/tsql-md.md)] 就會使用下列方法在資料庫中建立程式，並將*sum*指定為 OUTPUT 參數。</span><span class="sxs-lookup"><span data-stu-id="d298a-135">Once the assembly containing the above CLR stored procedure has been built and created on the server, the following [!INCLUDE[tsql](../../includes/tsql-md.md)] is used to create the procedure in the database, and specifies *sum* as an OUTPUT parameter.</span></span>  
  
```sql
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 <span data-ttu-id="d298a-136">請注意， *sum*會宣告為 `int` SQL Server 資料類型，並將 clr 預存程式中定義的*值*參數指定為 `SqlInt32` clr 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d298a-136">Note that *sum* is declared as an `int` SQL Server data type, and that the *value* parameter defined in the CLR stored procedure is specified as a `SqlInt32` CLR data type.</span></span> <span data-ttu-id="d298a-137">當呼叫程式執行 CLR 預存程式時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會自動將 `SqlInt32` clr 資料類型轉換成 `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型。</span><span class="sxs-lookup"><span data-stu-id="d298a-137">When a calling program executes the CLR stored procedure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatically converts the `SqlInt32` CLR data type to an `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  <span data-ttu-id="d298a-138">如需哪些 CLR 資料類型可以和無法轉換的詳細資訊，請參閱[對應 Clr 參數資料](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d298a-138">For more information about which CLR data types can and cannot be converted, see [Mapping CLR Parameter Data](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
### <a name="returning-tabular-results-and-messages"></a><span data-ttu-id="d298a-139">傳回表格式結果和訊息</span><span class="sxs-lookup"><span data-stu-id="d298a-139">Returning Tabular Results and Messages</span></span>  
 <span data-ttu-id="d298a-140">將表格式結果及訊息傳回到用戶端可透過 `SqlPipe` 物件完成，該物件可藉由使用 `Pipe` 類別的 `SqlContext` 屬性來取得。</span><span class="sxs-lookup"><span data-stu-id="d298a-140">Returning tabular results and messages to the client is done through the `SqlPipe` object, which is obtained by using the `Pipe` property of the `SqlContext` class.</span></span> <span data-ttu-id="d298a-141">`SqlPipe` 物件具有 `Send` 方法。</span><span class="sxs-lookup"><span data-stu-id="d298a-141">The `SqlPipe` object has a `Send` method.</span></span> <span data-ttu-id="d298a-142">藉由呼叫 `Send` 方法，您可透過管道將資料傳輸給呼叫應用程式。</span><span class="sxs-lookup"><span data-stu-id="d298a-142">By calling the `Send` method, you can transmit data through the pipe to the calling application.</span></span>  
  
 <span data-ttu-id="d298a-143">這些是 `SqlPipe.Send` 方法的數個多載，包括傳送 `SqlDataReader` 多載及僅傳送文字字串的多載。</span><span class="sxs-lookup"><span data-stu-id="d298a-143">These are several overloads of the `SqlPipe.Send` method, including one that sends a `SqlDataReader` and another that simply sends a text string.</span></span>  
  
###### <a name="returning-messages"></a><span data-ttu-id="d298a-144">傳回訊息</span><span class="sxs-lookup"><span data-stu-id="d298a-144">Returning Messages</span></span>  
 <span data-ttu-id="d298a-145">使用 `SqlPipe.Send(string)` 將訊息傳送到用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="d298a-145">Use `SqlPipe.Send(string)` to send messages to the client application.</span></span> <span data-ttu-id="d298a-146">訊息的文字限制在 8000 個字元以內。</span><span class="sxs-lookup"><span data-stu-id="d298a-146">The text of the message is limited to 8000 characters.</span></span> <span data-ttu-id="d298a-147">如果訊息超過 8000 個字元，則會被截斷。</span><span class="sxs-lookup"><span data-stu-id="d298a-147">If the message exceeds 8000 characters, it will be truncated.</span></span>  
  
###### <a name="returning-tabular-results"></a><span data-ttu-id="d298a-148">傳回表格式結果</span><span class="sxs-lookup"><span data-stu-id="d298a-148">Returning Tabular Results</span></span>  
 <span data-ttu-id="d298a-149">若要將查詢結果直接傳送至用戶端，請在 `Execute` 物件上使用 `SqlPipe` 方法的其中一個多載。</span><span class="sxs-lookup"><span data-stu-id="d298a-149">To send the results of a query directly to the client, use one of the overloads of the `Execute` method on the `SqlPipe` object.</span></span> <span data-ttu-id="d298a-150">這是將結果傳回至用戶端的最有效方式，因為資料會傳輸到網域緩衝區，而不是複製到 Managed 記憶體中。</span><span class="sxs-lookup"><span data-stu-id="d298a-150">This is the most efficient way to return results to the client, since the data is transferred to the network buffers without being copied into managed memory.</span></span> <span data-ttu-id="d298a-151">例如：</span><span class="sxs-lookup"><span data-stu-id="d298a-151">For example:</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="d298a-152">若要傳送先前透過同處理序提供者執行的查詢結果 (或要使用 `SqlDataReader` 的自訂實作前置處理資料)，請使用採用 `Send` 之 `SqlDataReader` 方法的多載。</span><span class="sxs-lookup"><span data-stu-id="d298a-152">To send the results of a query that was executed previously through the in-process provider (or to pre-process the data using a custom implementation of `SqlDataReader`), use the overload of the `Send` method that takes a `SqlDataReader`.</span></span> <span data-ttu-id="d298a-153">與先前描述的直接方法相比，此方法會稍微慢一點，但在將資料傳送到用戶端之前，它可以為操作資料提供更大彈性。</span><span class="sxs-lookup"><span data-stu-id="d298a-153">This method is slightly slower than the direct method described previously, but it offers greater flexibility to manipulate the data before it is sent to the client.</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
 
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="d298a-154">若要建立動態結果集、填入它並將它傳送至用戶端，您可建立目前連接的記錄，並使用 `SqlPipe.Send` 傳送該記錄。</span><span class="sxs-lookup"><span data-stu-id="d298a-154">To create a dynamic result set, populate it and send it to the client, you can create records from the current connection and send them using `SqlPipe.Send`.</span></span>  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 <span data-ttu-id="d298a-155">此範例是透過 `SqlPipe` 傳送表格式結果及訊息。</span><span class="sxs-lookup"><span data-stu-id="d298a-155">Here is an example of sending a tabular result and a message through `SqlPipe`.</span></span>  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 <span data-ttu-id="d298a-156">第一個 `Send` 會將訊息傳送至用戶端，而第二個則使用 `SqlDataReader` 傳送表格式結果。</span><span class="sxs-lookup"><span data-stu-id="d298a-156">The first `Send` sends a message to the client, while the second sends a tabular result using `SqlDataReader`.</span></span>  
  
 <span data-ttu-id="d298a-157">請注意，這些範例僅做為說明之用。</span><span class="sxs-lookup"><span data-stu-id="d298a-157">Note that these examples are for illustrative purposes only.</span></span> <span data-ttu-id="d298a-158">對於需要大量計算的應用程式，CLR 函數比簡單的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式更為適合。</span><span class="sxs-lookup"><span data-stu-id="d298a-158">CLR functions are more appropriate than simple [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for computation-intensive applications.</span></span> <span data-ttu-id="d298a-159">幾乎等同於先前範例的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序為：</span><span class="sxs-lookup"><span data-stu-id="d298a-159">An almost equivalent [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure to the previous example is:</span></span>  
  
```sql
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  <span data-ttu-id="d298a-160">在用戶端應用程式中，擷取訊息及結果集的方式不同。</span><span class="sxs-lookup"><span data-stu-id="d298a-160">Messages and result sets are retrieved differently in the client application.</span></span> <span data-ttu-id="d298a-161">例如， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 結果集會出現在 [**結果**] 視圖中，而訊息則會出現在 [**訊息**] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="d298a-161">For instance, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] result sets appear in the **Results** view, and messages appear in the **Messages** pane.</span></span>  
  
 <span data-ttu-id="d298a-162">如果上述的 Visual C# 程式碼儲存在 MyFirstUdp.cs 檔案中，而且使用下列方式編譯：</span><span class="sxs-lookup"><span data-stu-id="d298a-162">If the above Visual C# code is saved in a file MyFirstUdp.cs and compiled with:</span></span>  
  
```console
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 <span data-ttu-id="d298a-163">或者，如果上述的 Visual Basic 程式碼儲存在 MyFirstUdp.vb 檔案中，而且使用下列方式編譯：</span><span class="sxs-lookup"><span data-stu-id="d298a-163">Or, if the above Visual Basic code is saved in a file MyFirstUdp.vb and compiled with:</span></span>  
  
```console
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  <span data-ttu-id="d298a-164">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，就不支援以 `/clr:pure` 編譯之 Visual C++ 資料庫物件 (如預存程序) 的執行。</span><span class="sxs-lookup"><span data-stu-id="d298a-164">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], Visual C++ database objects (such as stored procedures) compiled with `/clr:pure` are not supported for execution.</span></span>  
  
 <span data-ttu-id="d298a-165">利用下列 DDL，可以註冊所產生的組件，並叫用進入點：</span><span class="sxs-lookup"><span data-stu-id="d298a-165">The resulting assembly can be registered, and the entry point invoked, with the following DDL:</span></span>  
  
```sql
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a><span data-ttu-id="d298a-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d298a-166">See Also</span></span>  
 <span data-ttu-id="d298a-167">[CLR 使用者定義函數](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="d298a-167">[CLR User-Defined Functions](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="d298a-168">[CLR 使用者定義類型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="d298a-168">[CLR User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 [<span data-ttu-id="d298a-169">CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="d298a-169">CLR Triggers</span></span>](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  
