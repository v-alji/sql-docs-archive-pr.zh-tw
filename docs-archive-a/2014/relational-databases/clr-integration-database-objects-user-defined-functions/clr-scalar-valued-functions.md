---
title: CLR 純量值函式 |Microsoft Docs
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
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
ms.openlocfilehash: be8f9616fb285d6a68d6734924874ded06fb3bd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698314"
---
# <a name="clr-scalar-valued-functions"></a><span data-ttu-id="3cfa3-102">CLR 純量值函式</span><span class="sxs-lookup"><span data-stu-id="3cfa3-102">CLR Scalar-Valued Functions</span></span>
  <span data-ttu-id="3cfa3-103">純量值函式 (SVF) 傳回單一值，如字串、整數或位元值。您可以使用任何 .NET Framework 程式語言，以 Managed 程式碼建立純量值的使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-103">A scalar-valued function (SVF) returns a single value, such as a string, integer, or bit value.You can create scalar-valued user-defined functions in managed code using any .NET Framework programming language.</span></span> <span data-ttu-id="3cfa3-104">這些函數可供 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或其他 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-104">These functions are accessible to [!INCLUDE[tsql](../../includes/tsql-md.md)] or other managed code.</span></span> <span data-ttu-id="3cfa3-105">如需 CLR 整合的優點，以及在 managed 程式碼和之間選擇的詳細資訊 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，請參閱[CLR 整合的總覽](../clr-integration/clr-integration-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-105">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a><span data-ttu-id="3cfa3-106">CLR 純量值函式的需求</span><span class="sxs-lookup"><span data-stu-id="3cfa3-106">Requirements for CLR Scalar-Valued Functions</span></span>  
 <span data-ttu-id="3cfa3-107">.NET Framework SVF 會在 .NET Framework 組件中實作為類別上的方法。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-107">.NET Framework SVFs are implemented as methods on a class in a .NET Framework assembly.</span></span> <span data-ttu-id="3cfa3-108">從 SVF 傳回的輸入參數和類型可以是所支援的任何純量資料類型，但、、、、、、、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `varchar` `char` 或除外 `rowversion` `text` `ntext` `image` `timestamp` `table` `cursor` 。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-108">The input parameters and the type returned from a SVF can be any of the scalar data types supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], except `varchar`, `char`, `rowversion`, `text`, `ntext`, `image`, `timestamp`, `table`, or `cursor`.</span></span> <span data-ttu-id="3cfa3-109">SVF 必須確保 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型與實作方法的傳回資料類型相符。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-109">SVFs must ensure a match between the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and the return data type of the implementation method.</span></span> <span data-ttu-id="3cfa3-110">如需類型轉換的詳細資訊，請參閱[對應 CLR 參數資料](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-110">For more information about type conversions, see [Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).</span></span>  
  
 <span data-ttu-id="3cfa3-111">當以 .NET Framework 語言實作 .NET Framework SVF 時，您可藉由指定 `SqlFunction` 自訂屬性，併入有關此函數的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-111">When implementing a .NET Framework SVF in a .NET Framework language, the `SqlFunction` custom attribute can be specified to include additional information about the function.</span></span> <span data-ttu-id="3cfa3-112">`SqlFunction` 屬性會指出當函數具有決定性或涉及浮點運算時，是否可以存取或修改資料。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-112">The `SqlFunction` attribute indicates whether or not the function accesses or modifies data, if it is deterministic, and if the function involves floating point operations.</span></span>  
  
 <span data-ttu-id="3cfa3-113">純量值使用者定義函數可能具有決定性，也可能不具決定性。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-113">Scalar-valued user-defined functions may be deterministic or non-deterministic.</span></span> <span data-ttu-id="3cfa3-114">當以一組特定的輸入參數呼叫具有決定性的函數時，一律會傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-114">A deterministic function always returns the same result when it is called with a specific set of input parameters.</span></span> <span data-ttu-id="3cfa3-115">當以一組特定的輸入參數呼叫不具決定性的函數時，它可能會傳回不同的結果。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-115">A non-deterministic function may return different results when it is called with a specific set of input parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cfa3-116">在提供相同輸入值和相同資料庫狀態時，如果某個函數不一定會產生相同輸出值，請勿將這個函數標示為具有決定性。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-116">Do not mark a function as deterministic if the function does not always produces the same output values, given the same input values and the same database state.</span></span> <span data-ttu-id="3cfa3-117">當某個函數不是真的具有決定性卻將它標示為具有決定性時，可能會導致索引檢視表和計算資料行損毀。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-117">Marking a function as deterministic, when the function isn't truly deterministic can result in corrupted indexed views and computed columns.</span></span> <span data-ttu-id="3cfa3-118">您可以將 `IsDeterministic` 屬性設定為 true，將函數標示為具有決定性。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-118">You mark a function as deterministic by setting the `IsDeterministic` property to true.</span></span>  
  
### <a name="table-valued-parameters"></a><span data-ttu-id="3cfa3-119">資料表值參數</span><span class="sxs-lookup"><span data-stu-id="3cfa3-119">Table-Valued Parameters</span></span>  
 <span data-ttu-id="3cfa3-120">資料表值參數 (TVP) 是使用者定義資料表類型，會傳入到程序或函數中，提供有效的方式將資料的多個資料列傳遞到伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-120">Table-valued parameters (TVPs), user-defined table types that are passed into a procedure or function, provide an efficient way to pass multiple rows of data to the server.</span></span> <span data-ttu-id="3cfa3-121">雖然 TVP 提供相似的功能給參數陣列，但是也提供更大的彈性和與 [!INCLUDE[tsql](../../includes/tsql-md.md)] 更緊密的整合。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-121">TVPs provide similar functionality to parameter arrays, but offer greater flexibility and closer integration with [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3cfa3-122">它們也能夠協助您獲得更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-122">They also provide the potential for better performance.</span></span> <span data-ttu-id="3cfa3-123">TVP 也減少與伺服器之間的往返次數。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-123">TVPs also help reduce the number of round trips to the server.</span></span> <span data-ttu-id="3cfa3-124">除了傳送多個要求到伺服器 (例如夾帶純量參數的清單)，資料能以 TVP 的形式傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-124">Instead of sending multiple requests to the server, such as with a list of scalar parameters, data can be sent to the server as a TVP.</span></span> <span data-ttu-id="3cfa3-125">使用者定義資料表類型無法以資料表值參數的形式傳遞到 Managed 預存程序或在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序中執行的函數，也無法從該預存程序或函數傳回。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-125">A user-defined table type cannot be passed as a table-valued parameter to, or be returned from, a managed stored procedure or function executing in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="3cfa3-126">如需 Tvp 的詳細資訊，請參閱[使用資料表值參數 &#40;資料庫引擎&#41;](../tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-126">For more information about TVPs, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
## <a name="example-of-a-clr-scalar-valued-function"></a><span data-ttu-id="3cfa3-127">CLR 純量值函式的範例</span><span class="sxs-lookup"><span data-stu-id="3cfa3-127">Example of a CLR Scalar-Valued Function</span></span>  
 <span data-ttu-id="3cfa3-128">以下是可存取資料並傳回整數值的簡單 SVF：</span><span class="sxs-lookup"><span data-stu-id="3cfa3-128">Here is a simple SVF that accesses data and returns an integer value:</span></span>  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 <span data-ttu-id="3cfa3-129">第一行程式碼會參考 `Microsoft.SqlServer.Server` 來存取屬性，並參考 `System.Data.SqlClient` 來存取 ADO.NET 命名空間 </span><span class="sxs-lookup"><span data-stu-id="3cfa3-129">The first line of code references `Microsoft.SqlServer.Server` to access attributes and `System.Data.SqlClient` to access the ADO.NET namespace.</span></span> <span data-ttu-id="3cfa3-130">(此命名空間包含 `SqlClient`，也就是 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-130">(This namespace contains `SqlClient`, the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)</span></span>  
  
 <span data-ttu-id="3cfa3-131">接下來，此函數會接收 `SqlFunction` 自訂屬性，該屬性可在 `Microsoft.SqlServer.Server` 命名空間中找到。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-131">Next, the function receives the `SqlFunction` custom attribute, which is found in the `Microsoft.SqlServer.Server` namespace.</span></span> <span data-ttu-id="3cfa3-132">此自訂屬性會指出使用者定義函數 (UDF) 是否會使用同處理序提供者來讀取伺服器上的資料。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-132">The custom attribute indicates whether or not the user-defined function (UDF) uses the in-process provider to read data in the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3cfa3-133">不允許 UDF 更新、插入或刪除資料。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-133">does not allow UDFs to update, insert, or delete data.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3cfa3-134">可以讓不使用同處理序提供者之 UDF 的執行最佳化。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-134">can optimize execution of a UDF that does not use the in-process provider.</span></span> <span data-ttu-id="3cfa3-135">將 `DataAccessKind` 設定為 `DataAccessKind.None` 可表示這一點。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-135">This is indicated by setting `DataAccessKind` to `DataAccessKind.None`.</span></span> <span data-ttu-id="3cfa3-136">在下一行中，目標方法為 public static (Visual Basic .NET 中則為 shared)。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-136">On the next line, the target method is a public static (shared in Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="3cfa3-137">然後位於 `SqlContext` 命名空間的 `Microsoft.SqlServer.Server` 類別可以使用已經設定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的連接來存取 `SqlCommand` 物件。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-137">The `SqlContext` class, located in the `Microsoft.SqlServer.Server` namespace, can then access a `SqlCommand` object with a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is already set up.</span></span> <span data-ttu-id="3cfa3-138">也可透過 `System.Transactions` 應用程式開發介面 (API) 來使用目前的交易內容，不過這裡並不會使用。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-138">Although not used here, the current transaction context is also available through the `System.Transactions` application programming interface (API).</span></span>  
  
 <span data-ttu-id="3cfa3-139">如果開發人員已經撰寫會使用 `System.Data.SqlClient` 命名空間內之類型的用戶端應用程式，應該會覺得函數主體內的大多數程式碼行看起來很類似。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-139">Most of the lines of code in the function body should look familiar to developers who have written client applications that use the types found in the `System.Data.SqlClient` namespace.</span></span>  
  
 <span data-ttu-id="3cfa3-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="3cfa3-140">[C#]</span></span>  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 <span data-ttu-id="3cfa3-141">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="3cfa3-141">[Visual Basic]</span></span>  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 <span data-ttu-id="3cfa3-142">適當的命令文字是藉由初始化 `SqlCommand` 物件來指定。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-142">The appropriate command text is specified by initializing the `SqlCommand` object.</span></span> <span data-ttu-id="3cfa3-143">上述範例會計算 `SalesOrderHeader` 資料表中的資料列數。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-143">The previous example counts the number of rows in table `SalesOrderHeader`.</span></span> <span data-ttu-id="3cfa3-144">接下來會呼叫 `ExecuteScalar` 物件的 `cmd` 方法。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-144">Next, the `ExecuteScalar` method of the `cmd` object is called.</span></span> <span data-ttu-id="3cfa3-145">這樣會根據查詢傳回 `int` 類型的值。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-145">This returns a value of type `int` based on the query.</span></span> <span data-ttu-id="3cfa3-146">最後，訂單計數會傳回到呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-146">Finally, the order count is returned to the caller.</span></span>  
  
 <span data-ttu-id="3cfa3-147">如果將這段程式碼儲存在名為 FirstUdf.cs 的檔案中，它可以依照以下方式編譯成組件：</span><span class="sxs-lookup"><span data-stu-id="3cfa3-147">If this code is saved in a file called FirstUdf.cs, it could be compiled into as assembly as follows:</span></span>  
  
 <span data-ttu-id="3cfa3-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="3cfa3-148">[C#]</span></span>  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 <span data-ttu-id="3cfa3-149">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="3cfa3-149">[Visual Basic]</span></span>  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  <span data-ttu-id="3cfa3-150">`/t:library` 表示應該產生程式庫，而不是可執行檔。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-150">`/t:library` indicates that a library, rather than an executable, should be produced.</span></span> <span data-ttu-id="3cfa3-151">可執行檔無法在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中註冊。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-151">Executables cannot be registered in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cfa3-152">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，不支援以 `/clr:pure` 編譯之 Visual C++ 資料庫物件的執行。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-152">Visual C++ database objects compiled with `/clr:pure` are not supported for execution on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3cfa3-153">例如，這類資料庫物件包括純量值函式。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-153">For example, such database objects include scalar-valued functions.</span></span>  
  
 <span data-ttu-id="3cfa3-154">[!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢及註冊組件和 UDF 的範例引動過程為：</span><span class="sxs-lookup"><span data-stu-id="3cfa3-154">The [!INCLUDE[tsql](../../includes/tsql-md.md)] query and a sample invocation to register the assembly and UDF are:</span></span>  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 <span data-ttu-id="3cfa3-155">請注意，[!INCLUDE[tsql](../../includes/tsql-md.md)] 中公開的函數名稱不必符合目標 public static 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="3cfa3-155">Note that the function name as exposed in [!INCLUDE[tsql](../../includes/tsql-md.md)] does not need to match the name of the target public static method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cfa3-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cfa3-156">See Also</span></span>  
 <span data-ttu-id="3cfa3-157">[對應 CLR 參數資料](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span><span class="sxs-lookup"><span data-stu-id="3cfa3-157">[Mapping CLR Parameter Data](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md) </span></span>  
 <span data-ttu-id="3cfa3-158">[CLR 整合自訂屬性的總覽](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="3cfa3-158">[Overview of CLR Integration Custom Attributes](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md) </span></span>  
 <span data-ttu-id="3cfa3-159">[使用者定義函數](../user-defined-functions/user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="3cfa3-159">[User-Defined Functions](../user-defined-functions/user-defined-functions.md) </span></span>  
 [<span data-ttu-id="3cfa3-160">從 CLR 資料庫物件進行資料存取</span><span class="sxs-lookup"><span data-stu-id="3cfa3-160">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
