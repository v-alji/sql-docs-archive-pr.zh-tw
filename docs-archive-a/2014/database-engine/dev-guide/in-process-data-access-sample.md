---
title: 同進程資料存取範例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 155be272-4f9a-4d86-9f4f-714c4f45b49a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 62201474be26abdc5fe6e8f470b4896d51b9b106
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709861"
---
# <a name="in-process-data-access-sample"></a><span data-ttu-id="509cb-102">同處理序資料存取範例</span><span class="sxs-lookup"><span data-stu-id="509cb-102">In-Process Data Access Sample</span></span>
  <span data-ttu-id="509cb-103">`InProcessDataAccess` 範例包含許多簡單的函數，這些函數會示範 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR 同處理序資料存取提供者的各種功能。</span><span class="sxs-lookup"><span data-stu-id="509cb-103">The `InProcessDataAccess` sample contains a number of simple functions that demonstrate various features of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR in-process data access provider.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="509cb-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="509cb-104">Prerequisites</span></span>  
 <span data-ttu-id="509cb-105">若要建立並執行這個專案，您必須安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="509cb-105">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="509cb-106">或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="509cb-106">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="509cb-107">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 文件集和範例[網站](https://www.microsoft.com/sql-server/sql-server-editions-express)免費取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="509cb-107">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="509cb-108">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開發人員[網站](https://go.microsoft.com/fwlink/?linkid=62796)取得 AdventureWorks 資料庫</span><span class="sxs-lookup"><span data-stu-id="509cb-108">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="509cb-109">.NET Framework SDK 2.0 或更新版本或是 Microsoft Visual Studio 2005 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="509cb-109">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="509cb-110">您可以免費取得 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="509cb-110">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="509cb-111">此外，您也必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="509cb-111">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="509cb-112">您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須啟用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="509cb-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="509cb-113">若要啟用 CLR 整合，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="509cb-113">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="509cb-114">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="509cb-114">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="509cb-115">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="509cb-115">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="509cb-116">若要啟用 CLR 整合，您必須擁有 `ALTER SETTINGS` 伺服器層級權限，此權限是由系統管理員 (`sysadmin`) 和伺服器管理員 (`serveradmin`) 固定伺服器角色的成員以隱含方式持有。</span><span class="sxs-lookup"><span data-stu-id="509cb-116">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="509cb-117">AdventureWorks 資料庫必須安裝在您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="509cb-117">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="509cb-118">如果您不是所使用之實例的系統管理員 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，則必須讓系統管理員授與您**CreateAssembly**許可權，才能完成安裝。</span><span class="sxs-lookup"><span data-stu-id="509cb-118">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly** permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="509cb-119">建立範例</span><span class="sxs-lookup"><span data-stu-id="509cb-119">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="509cb-120">使用下列指示來建立並執行範例：</span><span class="sxs-lookup"><span data-stu-id="509cb-120">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="509cb-121">開啟 Visual Studio 或 .NET Framework 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="509cb-121">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="509cb-122">必要時，請建立範例的目錄。</span><span class="sxs-lookup"><span data-stu-id="509cb-122">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="509cb-123">在此範例中，我們將使用 C:\MySample。</span><span class="sxs-lookup"><span data-stu-id="509cb-123">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="509cb-124">在 c:\MySample 中，建立 `inprocda.vb` (適用於 Visual Basic 範例) 或 `inprocda.cs` (適用於 C# 範例) 並將適當的 Visual Basic 或 C# 範例程式碼 (下面) 複製到檔案中。</span><span class="sxs-lookup"><span data-stu-id="509cb-124">In c:\MySample, create `inprocda.vb` (for the Visual Basic sample) or `inprocda.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="509cb-125">根據您選擇的語言，在命令列提示字元中執行下列其中一段程式碼，藉以將範例程式碼編譯成必要的組件。</span><span class="sxs-lookup"><span data-stu-id="509cb-125">Compile the sample code into the required assembly from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /target:library InProcDA.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /target:library inprocda.cs`  
  
5.  <span data-ttu-id="509cb-126">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝程式碼複製到檔案中，並將它儲存成範例目錄中的 `Install.sql`。</span><span class="sxs-lookup"><span data-stu-id="509cb-126">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="509cb-127">如果此範例安裝在 `C:\MySample\` 以外的目錄中，請依照指示編輯 `Install.sql` 檔案，以指向該位置。</span><span class="sxs-lookup"><span data-stu-id="509cb-127">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
7.  <span data-ttu-id="509cb-128">部署組件、預存程序和函數，方法是執行</span><span class="sxs-lookup"><span data-stu-id="509cb-128">Deploy the assembly, stored procedure and functions by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
8.  <span data-ttu-id="509cb-129">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝程式碼複製到檔案中，並將它儲存成範例目錄中的 `test.sql`。</span><span class="sxs-lookup"><span data-stu-id="509cb-129">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `test.sql` in the sample directory.</span></span>  
  
9. <span data-ttu-id="509cb-130">在命令提示字元中執行下列程式碼行，藉以測試應用程式：</span><span class="sxs-lookup"><span data-stu-id="509cb-130">Test the application by executing the following line at the command prompt:</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
10. <span data-ttu-id="509cb-131">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 清除指令碼複製到檔案中，並將它儲存成範例目錄中的 `cleanup.sql`。</span><span class="sxs-lookup"><span data-stu-id="509cb-131">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
11. <span data-ttu-id="509cb-132">使用下列命令來執行指令碼</span><span class="sxs-lookup"><span data-stu-id="509cb-132">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="509cb-133">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="509cb-133">Sample Code</span></span>  
 <span data-ttu-id="509cb-134">下面是此範例的程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="509cb-134">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="509cb-135">C#</span><span class="sxs-lookup"><span data-stu-id="509cb-135">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
public sealed class DataAccessDemo  
{  
        private DataAccessDemo()  
        {  
        }  
  
        /// <summary>  
/// Simple example to send a message to the client.  
/// </summary>  
public static void SendMessage(string msg)  
{  
SqlContext.Pipe.Send("Message from server: " + msg);  
}  
  
/// <summary>  
/// Simple example of performing data access within  
/// a function  
/// </summary>  
/// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlFunction(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.Read)]  
public static string ReportSqlVersion()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                //create a command from the current context  
                SqlCommand cmd = conn.CreateCommand();  
  
                //execute something  
                cmd.CommandText = "select @@version";  
  
                conn.Open();  
                //return results as scalar  
                return (string)cmd.ExecuteScalar();  
            }  
}  
  
/// <summary>  
/// Create a result set on the fly and send it to the client.  
/// </summary>  
public static void SendTransientResultSet()  
{  
//create the metadata for the columns  
            Microsoft.SqlServer.Server.SqlMetaData[] columnSchema   
                = new Microsoft.SqlServer.Server.SqlMetaData[] {  
new Microsoft.SqlServer.Server.SqlMetaData("stringcol", SqlDbType.NVarChar, 128)  
};  
  
//create a record based on that metadata  
            SqlDataRecord newRecord = new SqlDataRecord(columnSchema);  
  
//populate it  
newRecord.SetString(0, "Hello World!");  
  
//send it  
SqlContext.Pipe.Send(newRecord);  
}  
  
/// <summary>  
/// Execute a command and send the results to the client directly.  
/// </summary>  
public static void ExecuteToClient()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                SqlCommand cmd = conn.CreateCommand();  
  
                cmd.CommandText = "select @@version";  
                conn.Open();  
                SqlContext.Pipe.ExecuteAndSend(cmd);  
            }  
}  
  
/// <summary>  
/// Execute a command and send the resultig reader to the client  
/// </summary>  
public static void SendReaderToClient()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                SqlCommand cmd = conn.CreateCommand();  
  
                cmd.CommandText = "select @@version";  
                conn.Open();  
                SqlDataReader rdr = cmd.ExecuteReader();  
                try  
                {  
                    SqlContext.Pipe.Send(rdr);  
                }  
                finally  
                {  
                    rdr.Close();  
                }  
            }  
}  
  
};  
```  
  
 <span data-ttu-id="509cb-136">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="509cb-136">Visual Basic</span></span>  
  
```  
Imports Microsoft.SqlServer.Server  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Partial Public NotInheritable Class DataAccessDemo  
    Private Sub New()  
    End Sub  
  
    ''' <summary>  
    ''' Simple example of performing data access within a function  
    ''' </summary>  
    ''' <returns></returns>  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReportSqlVersion() As SqlString  
        Using conn As New SqlConnection("context connection=true")  
            'create a command from the current context  
            Dim cmd As SqlCommand = conn.CreateCommand()  
  
            'execute something  
            cmd.CommandText = "SELECT @@VERSION"  
  
            conn.Open()  
  
            'return results as scalar  
            Return CType(cmd.ExecuteScalar(), String)  
        End Using  
    End Function  
  
    ''' <summary>  
    ''' Simple example to send a message to the client.  
    ''' </summary>  
    Public Shared Sub SendMessage(ByVal msg As String)  
        SqlContext.Pipe.Send(("Message from server: " & msg))  
    End Sub  
  
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    Public Shared Sub SendTransientResultSet()  
        'create the metadata for the columns  
        Dim columnSchema() As Microsoft.SqlServer.Server.SqlMetaData _  
            = {New SqlMetaData("stringcol", SqlDbType.NVarChar, 128)}  
  
        'create a record based on that metadata  
        Dim newRecord As New SqlDataRecord(columnSchema)  
  
        'populate it  
        newRecord.SetString(0, "Hello World!")  
  
        'send it  
        SqlContext.Pipe.Send(newRecord)  
    End Sub  
  
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    Public Shared Sub ExecuteToClient()  
        Using conn As New SqlConnection("context connection=true")  
            Dim cmd As SqlCommand = conn.CreateCommand()  
  
            cmd.CommandText = "SELECT @@VERSION"  
            conn.Open()  
            SqlContext.Pipe.ExecuteAndSend(cmd)  
        End Using  
    End Sub  
  
    ''' <summary>  
    ''' Execute a command and send the resulting reader to the client  
    ''' </summary>  
    Public Shared Sub SendReaderToClient()  
        Using conn As New SqlConnection("context connection=true")  
            Dim cmd As SqlCommand = conn.CreateCommand()  
            cmd.CommandText = "SELECT @@VERSION"  
            conn.Open()  
            Dim rdr As SqlDataReader = cmd.ExecuteReader()  
            Try  
                SqlContext.Pipe.Send(rdr)  
            Finally  
                rdr.Close()  
            End Try  
        End Using  
    End Sub  
  
End Class  
  
```  
  
 <span data-ttu-id="509cb-137">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝指令碼 (`Install.sql`)，它會部署組件並建立此範例所需的預存程序和函數。</span><span class="sxs-lookup"><span data-stu-id="509cb-137">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedures and function required by this example.</span></span>  
  
```  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendMessage')  
DROP PROCEDURE SendMessage;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendTransientResultSet')  
DROP PROCEDURE SendTransientResultSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'ExecuteToClient')  
DROP PROCEDURE ExecuteToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendReaderToClient')  
DROP PROCEDURE SendReaderToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'ReportSqlVersion' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [ReportSqlVersion];  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'InProcDA') DROP ASSEMBLY InProcDA;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath = N'C:\MySample\'  
CREATE ASSEMBLY InProcDA FROM @SamplesPath + 'InProcDA.dll'  
WITH permission_set = SAFE;  
GO  
  
CREATE PROCEDURE [SendMessage] @msg nvarchar(4000)  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendMessage];  
GO  
  
CREATE FUNCTION [ReportSqlVersion]() RETURNS nvarchar(4000)  
AS EXTERNAL NAME [InProcDA].[DataAccessDemo].[ReportSqlVersion];  
GO  
  
CREATE PROCEDURE [SendTransientResultSet]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendTransientResultSet];  
GO  
  
CREATE PROCEDURE [ExecuteToClient]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[ExecuteToClient];  
GO  
  
CREATE PROCEDURE [SendReaderToClient]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendReaderToClient];  
GO  
```  
  
 <span data-ttu-id="509cb-138">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] (`test.sql`) 藉由執行此範例中定義的預存程式和函式來測試範例。</span><span class="sxs-lookup"><span data-stu-id="509cb-138">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] (`test.sql`) tests the example by exercising the stored procedures and function defined in this sample.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
-- send a message to the client  
EXEC SendMessage  N'This is a test message.';  
  
-- exec a function that does data access  
SELECT dbo.ReportSqlVersion();  
  
-- exec the proc that sends a result set to the client  
EXEC SendTransientResultSet;  
  
EXEC ExecuteToClient;  
  
EXEC SendReaderToClient;  
  
USE master;  
GO  
  
```  
  
 <span data-ttu-id="509cb-139">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會從資料庫中移除組件、函數和預存程序。</span><span class="sxs-lookup"><span data-stu-id="509cb-139">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly, function and stored procedures from the database.</span></span>  
  
```  
  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendMessage')  
DROP PROCEDURE SendMessage;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendTransientResultSet')  
DROP PROCEDURE SendTransientResultSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'ExecuteToClient')  
DROP PROCEDURE ExecuteToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendReaderToClient')  
DROP PROCEDURE SendReaderToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'ReportSqlVersion' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [ReportSqlVersion];  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'InProcDA') DROP ASSEMBLY InProcDA;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="509cb-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="509cb-140">See Also</span></span>  
 [<span data-ttu-id="509cb-141">通用語言執行平台 &#40;CLR&#41; 整合的使用案例和範例</span><span class="sxs-lookup"><span data-stu-id="509cb-141">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
