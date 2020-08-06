---
title: 正在抓取 UDT 資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SqlDataReader object
- ADO.NET [CLR integration]
- binding UDTs [CLR integration]
- UDTs [CLR integration], ADO.NET
- assemblies [CLR integration], user-defined types
- query parameters [CLR integration]
- user-defined types [CLR integration], ADO.NET
- bytes [CLR integration]
ms.assetid: 6a98ac8c-0e69-4c03-83a4-2062cb782049
author: rothja
ms.author: jroth
ms.openlocfilehash: cb9133ea45069f76e7590f6b74d3c1e1cb98c7bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597881"
---
# <a name="retrieving-udt-data"></a><span data-ttu-id="d8986-102">擷取 UDT 資料</span><span class="sxs-lookup"><span data-stu-id="d8986-102">Retrieving UDT Data</span></span>
  <span data-ttu-id="d8986-103">為了在用戶端上建立使用者定義型別 (UDT)，用戶端應用程式必須提供在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中登錄為 UDT 的組件。</span><span class="sxs-lookup"><span data-stu-id="d8986-103">In order to create a user-defined type (UDT) on the client, the assembly that was registered as a UDT in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database must be available to the client application.</span></span> <span data-ttu-id="d8986-104">您可以將 UDT 組件置於與應用程式相同的目錄中，或置於全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="d8986-104">The UDT assembly can be placed in the same directory with the application, or in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="d8986-105">您還可以在專案中設定組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d8986-105">You can also set a reference to the assembly in your project.</span></span>  
  
## <a name="requirements-for-using-udts-in-adonet"></a><span data-ttu-id="d8986-106">在 ADO.NET 中使用 UDT 的需求</span><span class="sxs-lookup"><span data-stu-id="d8986-106">Requirements for Using UDTs in ADO.NET</span></span>  
 <span data-ttu-id="d8986-107">載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的組件與用戶端上的組件必須相容，才可以在用戶端上建立 UDT。</span><span class="sxs-lookup"><span data-stu-id="d8986-107">The assembly loaded in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the assembly on the client must be compatible in order for the UDT to be created on the client.</span></span> <span data-ttu-id="d8986-108">針對以 `Native` 序列化格式定義的 UDT，組件在結構上必須相容。</span><span class="sxs-lookup"><span data-stu-id="d8986-108">For UDTs defined with the `Native` serialization format, the assemblies must be structurally compatible.</span></span> <span data-ttu-id="d8986-109">針對以 `UserDefined` 格式定義的組件，組件在用戶端上必須可用。</span><span class="sxs-lookup"><span data-stu-id="d8986-109">For assemblies defined with the `UserDefined` format, the assembly must be available on the client.</span></span>  
  
 <span data-ttu-id="d8986-110">不需藉助用戶端上的 UDT 組件複本，便可從資料表的 UDT 資料行中擷取未經處理的資料。</span><span class="sxs-lookup"><span data-stu-id="d8986-110">You do not need a copy of the UDT assembly on the client in order to retrieve the raw data from a UDT column in a table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8986-111">當 UDT 版本或其他問題不相符時， **SqlClient**可能無法載入 udt。</span><span class="sxs-lookup"><span data-stu-id="d8986-111">**SqlClient** may fail to load a UDT in the event of mismatched UDT versions or other problems.</span></span> <span data-ttu-id="d8986-112">在此情況下，請使用一般疑難排解機制，判斷呼叫應用程式找不到包含 UDT 之組件的原因。</span><span class="sxs-lookup"><span data-stu-id="d8986-112">In this case, use regular troubleshooting mechanisms to determine why the assembly containing the UDT cannot be found by the calling application.</span></span> <span data-ttu-id="d8986-113">如需詳細資訊，請閱讀 .NET Framework 文件集中名為＜診斷 Managed 偵錯助理的錯誤＞的主題。</span><span class="sxs-lookup"><span data-stu-id="d8986-113">For more information, read the topic titled "Diagnosing Errors with Managed Debugging Assistants" in the .NET Framework documentation.</span></span>  
  
## <a name="accessing-udts-with-a-sqldatareader"></a><span data-ttu-id="d8986-114">使用 SqlDataReader 存取 UDT</span><span class="sxs-lookup"><span data-stu-id="d8986-114">Accessing UDTs with a SqlDataReader</span></span>  
 <span data-ttu-id="d8986-115">您可以從用戶端程式碼使用 `System.Data.SqlClient.SqlDataReader`，以擷取包含 UDT 資料行的結果集，其會公開為物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8986-115">A `System.Data.SqlClient.SqlDataReader` can be used from client code to retrieve a result set that contains a UDT column, which is exposed as an instance of the object.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d8986-116">範例</span><span class="sxs-lookup"><span data-stu-id="d8986-116">Example</span></span>  
 <span data-ttu-id="d8986-117">此範例顯示如何使用 `Main` 方法建立新的 `SqlDataReader` 物件。</span><span class="sxs-lookup"><span data-stu-id="d8986-117">This example shows how to use the `Main` method to create a new `SqlDataReader` object.</span></span> <span data-ttu-id="d8986-118">該程式碼範例內會發生下列動作：</span><span class="sxs-lookup"><span data-stu-id="d8986-118">The following actions occur within the code example:</span></span>  
  
1.  <span data-ttu-id="d8986-119">Main 方法建立新的 `SqlDataReader` 物件，並擷取 Point 資料表 (擁有名為 Point 的 UDT 資料行) 的值。</span><span class="sxs-lookup"><span data-stu-id="d8986-119">The Main method creates a new `SqlDataReader` object and retrieves the values from the Points table, which has a UDT column named Point.</span></span>  
  
2.  <span data-ttu-id="d8986-120">Point UDT 公開定義為整數的 X 及 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="d8986-120">The Point UDT exposes X and Y coordinates defined as integers.</span></span>  
  
3.  <span data-ttu-id="d8986-121">UDT 定義 `Distance` 方法及 `GetDistanceFromXY` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8986-121">The UDT defines a `Distance` method and a `GetDistanceFromXY` method.</span></span>  
  
4.  <span data-ttu-id="d8986-122">範例程式碼會擷取主索引鍵及 UDT 資料行的值，以示範 UDT 的功能。</span><span class="sxs-lookup"><span data-stu-id="d8986-122">The sample code retrieves the values of the primary key and UDT columns in order to demonstrate the capabilities of the UDT.</span></span>  
  
5.  <span data-ttu-id="d8986-123">範例程式碼呼叫 `Point.Distance` 及 `Point.GetDistanceFromXY` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8986-123">The sample code calls the `Point.Distance` and `Point.GetDistanceFromXY` methods.</span></span>  
  
6.  <span data-ttu-id="d8986-124">結果顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="d8986-124">The results are displayed in the console window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8986-125">應用程式必須已具有對 UDT 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d8986-125">The application must already have a reference to the UDT assembly.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module ReadPoints  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the value of the UDT  
                Dim pnt As Point = CType(rdr(1), Point)  
  
             ' You can also use GetSqlValue and GetValue  
             ' Dim pnt As Point = CType(rdr.GetSqlValue(1), Point)  
             ' Dim pnt As Point = CType(rdr.GetValue(1), Point)  
  
                ' Print values  
                Console.WriteLine( _  
                 "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}", _  
                  id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance())  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
         & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
namespace Microsoft.Samples.SqlServer  
{  
class ReadPoints  
{  
static void Main()  
{  
  string connectionString = GetConnectionString();  
  using (SqlConnection cnn = new SqlConnection(connectionString))  
  {  
    cnn.Open();  
    SqlCommand cmd = new SqlCommand(  
       "SELECT ID, Pnt FROM dbo.Points", cnn);  
    SqlDataReader rdr = cmd.ExecuteReader();  
  
    while (rdr.Read())  
    {  
      // Retrieve the value of the Primary Key column  
      int id = rdr.GetInt32(0);  
  
        // Retrieve the value of the UDT  
        Point pnt = (Point)rdr[1];  
  
        // You can also use GetSqlValue and GetValue  
        // Point pnt = (Point)rdr.GetSqlValue(1);  
        // Point pnt = (Point)rdr.GetValue(1);  
  
        Console.WriteLine(  
        "ID={0} Point={1} X={2} Y={3} DistanceFromXY={4} Distance={5}",   
        id, pnt, pnt.X, pnt.Y, pnt.DistanceFromXY(1, 9), pnt.Distance());  
    }  
  rdr.Close();  
  Console.WriteLine("done");  
  }  
  static private string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,   
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Initial Catalog=AdventureWorks;"  
        + "Integrated Security=SSPI";  
  }  
}  
```  
  
## <a name="binding-udts-as-bytes"></a><span data-ttu-id="d8986-126">以位元組繫結 UDT</span><span class="sxs-lookup"><span data-stu-id="d8986-126">Binding UDTs as Bytes</span></span>  
 <span data-ttu-id="d8986-127">在某些情況下，您可能要從 UDT 資料行擷取未經處理資料。</span><span class="sxs-lookup"><span data-stu-id="d8986-127">In some situations, you may want to retrieve the raw data from the UDT column.</span></span> <span data-ttu-id="d8986-128">可能該型別在本機不可使用，或您不想要具現化 UDT 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8986-128">Perhaps the type is not available locally, or you do not wish to instantiate an instance of the UDT.</span></span> <span data-ttu-id="d8986-129">您可以使用的**GetBytes**方法，將未經處理的位元組讀取到位元組陣列 `SqlDataReader` 。</span><span class="sxs-lookup"><span data-stu-id="d8986-129">You can read the raw bytes into a byte array using the **GetBytes** method of a `SqlDataReader`.</span></span> <span data-ttu-id="d8986-130">此方法可將指定資料行位移的位元組資料流，讀取至始於指定緩衝區位移的陣列緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d8986-130">This method reads a stream of bytes from the specified column offset into the buffer of an array starting at a specified buffer offset.</span></span> <span data-ttu-id="d8986-131">另一個選項是使用其中一個**GetSqlBytes**或**GetSqlBinary**方法，並在單一作業中讀取所有內容。</span><span class="sxs-lookup"><span data-stu-id="d8986-131">Another option is to use one of the **GetSqlBytes** or **GetSqlBinary** methods and read all of the contents in a single operation.</span></span> <span data-ttu-id="d8986-132">在任何一種情況中，都不會具現化 UDT 物件，所以您無需設定用戶端組件的 UDT 參考。</span><span class="sxs-lookup"><span data-stu-id="d8986-132">In either case, the UDT object is never instantiated, so you do not need to set a reference to the UDT in the client assembly.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d8986-133">範例</span><span class="sxs-lookup"><span data-stu-id="d8986-133">Example</span></span>  
 <span data-ttu-id="d8986-134">這個範例會示範如何使用，將**點**資料以未經處理的位元組形式捕獲到位元組陣列 `SqlDataReader` 。</span><span class="sxs-lookup"><span data-stu-id="d8986-134">This example shows how to retrieve the **Point** data as raw bytes into a byte array using a `SqlDataReader`.</span></span> <span data-ttu-id="d8986-135">該程式碼使用 `System.Text.StringBuilder`，將未經處理位元組轉換成要顯示於主控台視窗的字串表示。</span><span class="sxs-lookup"><span data-stu-id="d8986-135">The code uses a `System.Text.StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Retrieve the raw bytes into a byte array  
                Dim buffer(31) As Byte  
                Dim byteCount As Integer = _  
                 CInt(rdr.GetBytes(1, 0, buffer, 0, 31))  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", buffer(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
        string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand("SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Retrieve the raw bytes into a byte array  
                byte[] buffer = new byte[32];  
                long byteCount = rdr.GetBytes(1, 0, buffer, 0, 32);  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", buffer[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
### <a name="example-using-getsqlbytes"></a><span data-ttu-id="d8986-136">使用 GetSqlBytes 的範例</span><span class="sxs-lookup"><span data-stu-id="d8986-136">Example Using GetSqlBytes</span></span>  
 <span data-ttu-id="d8986-137">這個範例示範如何使用**GetSqlBytes**方法，在單一作業中以原始位元組形式抓取**點**資料。</span><span class="sxs-lookup"><span data-stu-id="d8986-137">This example shows how to retrieve the **Point** data as raw bytes in a single operation using the **GetSqlBytes** method.</span></span> <span data-ttu-id="d8986-138">該程式碼使用 `StringBuilder`，將未經處理位元組轉換成要顯示於主控台視窗的字串表示。</span><span class="sxs-lookup"><span data-stu-id="d8986-138">The code uses a `StringBuilder` to convert the raw bytes to a string representation to be displayed in the console window.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Text  
  
Module GetRawBytes  
    Sub Main()  
        Dim connectionString As String = GetConnectionString()  
        Using cnn As New SqlConnection(connectionString)  
            cnn.Open()  
            Dim cmd As New SqlCommand( _  
             "SELECT ID, Pnt FROM dbo.Points", cnn)  
            Dim rdr As SqlDataReader  
            rdr = cmd.ExecuteReader  
  
            While rdr.Read()  
                ' Retrieve the value of the Primary Key column  
                Dim id As Int32 = rdr.GetInt32(0)  
  
                ' Use SqlBytes to retrieve raw bytes  
                Dim sb As SqlBytes = rdr.GetSqlBytes(1)  
                Dim byteCount As Long = sb.Length  
  
                ' Format and print bytes   
                Dim str As New StringBuilder  
                str.AppendFormat("ID={0} Point=", id)  
  
                Dim i As Integer  
                For i = 0 To (byteCount - 1)  
                    str.AppendFormat("{0:x}", sb(i))  
                Next  
                Console.WriteLine(str.ToString)  
  
            End While  
            rdr.Close()  
            Console.WriteLine("done")  
        End Using  
    End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data.Sql;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Text;  
  
class GetRawBytes  
{  
    static void Main()  
    {  
         string connectionString = GetConnectionString();  
        using (SqlConnection cnn = new SqlConnection(connectionString))  
        {  
            cnn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT ID, Pnt FROM dbo.Points", cnn);  
            SqlDataReader rdr = cmd.ExecuteReader();  
  
            while (rdr.Read())  
            {  
                // Retrieve the value of the Primary Key column  
                int id = rdr.GetInt32(0);  
  
                // Use SqlBytes to retrieve raw bytes  
                SqlBytes sb = rdr.GetSqlBytes(1);  
                long byteCount = sb.Length;  
  
                // Format and print bytes   
                StringBuilder str = new StringBuilder();  
                str.AppendFormat("ID={0} Point=", id);  
  
                for (int i = 0; i < byteCount; i++)  
                    str.AppendFormat("{0:x}", sb[i]);  
                Console.WriteLine(str.ToString());  
            }  
            rdr.Close();  
            Console.WriteLine("done");  
        }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="working-with-udt-parameters"></a><span data-ttu-id="d8986-139">使用 UDT 參數</span><span class="sxs-lookup"><span data-stu-id="d8986-139">Working with UDT Parameters</span></span>  
 <span data-ttu-id="d8986-140">在 ADO.NET 程式碼中，UDT 可以同時當做輸入及輸出參數使用。</span><span class="sxs-lookup"><span data-stu-id="d8986-140">UDTs can be used as both input and output parameters in your ADO.NET code.</span></span>  
  
## <a name="using-udts-in-query-parameters"></a><span data-ttu-id="d8986-141">在查詢參數中使用 UDT</span><span class="sxs-lookup"><span data-stu-id="d8986-141">Using UDTs in Query Parameters</span></span>  
 <span data-ttu-id="d8986-142">設定 `SqlParameter` 物件的 `System.Data.SqlClient.SqlCommand` 時，可以使用 UDT 做為參數值。</span><span class="sxs-lookup"><span data-stu-id="d8986-142">UDTs can be used as parameter values when setting up a `SqlParameter` for a `System.Data.SqlClient.SqlCommand` object.</span></span> <span data-ttu-id="d8986-143">對 `SqlDbType.Udt` 集合呼叫 `SqlParameter` 方法時，可使用 `Add` 物件的 `Parameters` 列舉型別表示參數是 UDT。</span><span class="sxs-lookup"><span data-stu-id="d8986-143">The `SqlDbType.Udt` enumeration of a `SqlParameter` object is used to indicate that the parameter is a UDT when calling the `Add` method to the `Parameters` collection.</span></span> <span data-ttu-id="d8986-144">`UdtTypeName`物件的屬性 `SqlCommand` 是用來指定資料庫中 UDT 的完整名稱，使用*schema_name. object_name*語法。</span><span class="sxs-lookup"><span data-stu-id="d8986-144">The `UdtTypeName` property of a `SqlCommand` object is used to specify the fully qualified name of the UDT in the database using the *database.schema_name.object_name* syntax.</span></span> <span data-ttu-id="d8986-145">儘管並非必須如此，但使用完整名稱可消除程式碼的模稜兩可性。</span><span class="sxs-lookup"><span data-stu-id="d8986-145">Although it is not required, using the fully qualified name removes ambiguity from your code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8986-146">UDT 組件的本機複本必須可讓用戶端專案使用。</span><span class="sxs-lookup"><span data-stu-id="d8986-146">A local copy of the UDT assembly must be available to the client project.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d8986-147">範例</span><span class="sxs-lookup"><span data-stu-id="d8986-147">Example</span></span>  
 <span data-ttu-id="d8986-148">此範例中的程式碼會建立 `SqlCommand` 及 `SqlParameter` 物件，以將資料插入資料表中的 UDT 資料行。</span><span class="sxs-lookup"><span data-stu-id="d8986-148">The code in this example creates `SqlCommand` and `SqlParameter` objects to insert data into a UDT column in a table.</span></span> <span data-ttu-id="d8986-149">該程式碼使用 `SqlDbType.Udt` 列舉型別來指定資料型別，並使用 `UdtTypeName` 物件的 `SqlParameter` 屬性來指定資料庫中 UDT 的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d8986-149">The code uses the `SqlDbType.Udt` enumeration to specify the data type, and the `UdtTypeName` property of the `SqlParameter` object to specify the fully qualified name of the UDT in the database.</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports system.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim ConnectionString As String = GetConnectionString()  
    Dim cnn As New SqlConnection(ConnectionString)  
    Using cnn  
      Dim cmd As SqlCommand = cnn.CreateCommand()  
      cmd.CommandText = "INSERT INTO dbo.Points (Pnt) VALUES (@Point)"  
      cmd.CommandType = CommandType.Text  
  
      Dim param As New SqlParameter("@Point", SqlDbType.Udt)      param.UdtTypeName = "TestPoint.dbo.Point"      param.Direction = ParameterDirection.Input      param.Value = New Point(5, 6)      cmd.Parameters.Add(param)  
  
      cnn.Open()  
      cmd.ExecuteNonQuery()  
      Console.WriteLine("done")  
    End Using  
  End Sub  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,    
        ' you can retrieve it from a configuration file.  
        Return "Data Source=(local);Initial Catalog=AdventureWorks;" _  
           & "Integrated Security=SSPI;"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  string ConnectionString = GetConnectionString();  
     using (SqlConnection cnn = new SqlConnection(ConnectionString))  
     {  
       SqlCommand cmd = cnn.CreateCommand();  
       cmd.CommandText =   
         "INSERT INTO dbo.Points (Pnt) VALUES (@Point)";  
       cmd.CommandType = CommandType.Text;  
  
       SqlParameter param = new SqlParameter("@Point", SqlDbType.Udt);       param.UdtTypeName = "TestPoint.dbo.Point";       param.Direction = ParameterDirection.Input;       param.Value = new Point(5, 6);       cmd.Parameters.Add(param);  
  
       cnn.Open();  
       cmd.ExecuteNonQuery();  
       Console.WriteLine("done");  
     }  
    static private string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,   
        // you can retrieve it from a configuration file.  
        return "Data Source=(local);Initial Catalog=AdventureWorks;"  
            + "Integrated Security=SSPI";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8986-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8986-150">See Also</span></span>  
 [<span data-ttu-id="d8986-151">存取 ADO.NET 中的使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="d8986-151">Accessing User-Defined Types in ADO.NET</span></span>](accessing-user-defined-types-in-ado-net.md)  
  
  
