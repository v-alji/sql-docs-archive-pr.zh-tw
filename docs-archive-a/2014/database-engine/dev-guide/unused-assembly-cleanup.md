---
title: 未使用的元件清除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: e03c2b6f-8f39-4382-9cf3-7f766a1bd929
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ea7b1ea583d7c0295f292ff8326c93892b6de7ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701701"
---
# <a name="unused-assembly-cleanup"></a><span data-ttu-id="454d0-102">未使用的組件清除</span><span class="sxs-lookup"><span data-stu-id="454d0-102">Unused Assembly Cleanup</span></span>
  <span data-ttu-id="454d0-103">這個 `AssemblyCleanup` 範例包含一個 .NET 預存程序，該預存程序會查詢中繼資料目錄，藉以在目前的資料庫中清除未使用的組件。</span><span class="sxs-lookup"><span data-stu-id="454d0-103">The `AssemblyCleanup` sample contains a .NET Stored Procedure that cleans-up unused assemblies in the current database by querying the metadata catalogs.</span></span> <span data-ttu-id="454d0-104">其唯一的參數 `visible_assemblies` 用於指定是否應該卸除未使用的可見組件。</span><span class="sxs-lookup"><span data-stu-id="454d0-104">Its only parameter, `visible_assemblies`, is used to specify whether unused visible assemblies should be dropped or not.</span></span> <span data-ttu-id="454d0-105">'false' 這個值表示預設只會卸除未使用的不可見組件，否則，將會卸除所有未使用的組件。</span><span class="sxs-lookup"><span data-stu-id="454d0-105">A value of 'false' means by default only unused invisible assemblies will be dropped, otherwise all unused assemblies will be dropped.</span></span> <span data-ttu-id="454d0-106">未使用組件的集合就是尚未定義任何進入點 (常式/類型和彙總)，而且沒有已使用的組件直接或間接參考它們的組件。</span><span class="sxs-lookup"><span data-stu-id="454d0-106">The set of unused assemblies are those assemblies that do not have any entry points defined (routines / types and aggregates) and there are no used assemblies referencing them directly or indirectly.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="454d0-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="454d0-107">Prerequisites</span></span>  
 <span data-ttu-id="454d0-108">若要建立並執行這個專案，您必須安裝下列軟體：</span><span class="sxs-lookup"><span data-stu-id="454d0-108">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="454d0-109">或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="454d0-109">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="454d0-110">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express 文件集和範例[網站](https://www.microsoft.com/sql-server/sql-server-editions-express)免費取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express</span><span class="sxs-lookup"><span data-stu-id="454d0-110">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="454d0-111">您可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 開發人員[網站](https://go.microsoft.com/fwlink/?linkid=62796)取得 AdventureWorks 資料庫</span><span class="sxs-lookup"><span data-stu-id="454d0-111">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="454d0-112">.NET Framework SDK 2.0 或更新版本或是 Microsoft Visual Studio 2005 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="454d0-112">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="454d0-113">您可以免費取得 .NET Framework SDK。</span><span class="sxs-lookup"><span data-stu-id="454d0-113">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="454d0-114">此外，您也必須符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="454d0-114">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="454d0-115">您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須啟用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="454d0-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="454d0-116">若要啟用 CLR 整合，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="454d0-116">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="454d0-117">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="454d0-117">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="454d0-118">執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令：</span><span class="sxs-lookup"><span data-stu-id="454d0-118">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="454d0-119">若要啟用 CLR 整合，您必須擁有 `ALTER SETTINGS` 伺服器層級權限，此權限是由系統管理員 (`sysadmin`) 和伺服器管理員 (`serveradmin`) 固定伺服器角色的成員以隱含方式持有。</span><span class="sxs-lookup"><span data-stu-id="454d0-119">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="454d0-120">AdventureWorks 資料庫必須安裝在您所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="454d0-120">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="454d0-121">如果您不是正在使用之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的管理員，則必須讓管理員授與您 **CreateAssembly** 權限來完成安裝。</span><span class="sxs-lookup"><span data-stu-id="454d0-121">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly**  permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="454d0-122">建立範例</span><span class="sxs-lookup"><span data-stu-id="454d0-122">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="454d0-123">使用下列指示來建立並執行範例：</span><span class="sxs-lookup"><span data-stu-id="454d0-123">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="454d0-124">開啟 Visual Studio 或 .NET Framework 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="454d0-124">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="454d0-125">必要時，請建立範例的目錄。</span><span class="sxs-lookup"><span data-stu-id="454d0-125">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="454d0-126">在此範例中，我們將使用 C:\MySample。</span><span class="sxs-lookup"><span data-stu-id="454d0-126">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="454d0-127">在 c:\MySample 中，建立 `AssemblyCleanup.vb` (適用於 Visual Basic 範例) 或 `AssemblyCleanup.cs` (適用於 C# 範例) 並將適當的 Visual Basic 或 C# 範例程式碼 (下面) 複製到檔案中。</span><span class="sxs-lookup"><span data-stu-id="454d0-127">In c:\MySample, create `AssemblyCleanup.vb` (for the Visual Basic sample) or `AssemblyCleanup.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="454d0-128">根據您選擇的語言，在命令列提示字元中執行下列其中一段程式碼，藉以編譯範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="454d0-128">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Transactions.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /target:library AssemblyCleanup.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /target:library AssemblyCleanup.cs`  
  
5.  <span data-ttu-id="454d0-129">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝程式碼複製到檔案中，並將它儲存成範例目錄中的 `Install.sql`。</span><span class="sxs-lookup"><span data-stu-id="454d0-129">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="454d0-130">如果此範例安裝在 `C:\MySample\` 以外的目錄中，請依照指示編輯 `Install.sql` 檔案，以指向該位置。</span><span class="sxs-lookup"><span data-stu-id="454d0-130">If the sample is installed in a directory other then `C:\MySample\`, edit the file `Install.sql` as indicated to point to that location.</span></span>  
  
7.  <span data-ttu-id="454d0-131">部署組件和預存程序，方法是執行</span><span class="sxs-lookup"><span data-stu-id="454d0-131">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql`  
  
8.  <span data-ttu-id="454d0-132">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 測試命令腳本複製到檔案中，並將它儲存成 `test.sql` 範例目錄中的。</span><span class="sxs-lookup"><span data-stu-id="454d0-132">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
9. <span data-ttu-id="454d0-133">使用下列命令來執行測試指令碼</span><span class="sxs-lookup"><span data-stu-id="454d0-133">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
10. <span data-ttu-id="454d0-134">將 [!INCLUDE[tsql](../../includes/tsql-md.md)] 清除指令碼複製到檔案中，並將它儲存成範例目錄中的 `cleanup.sql`。</span><span class="sxs-lookup"><span data-stu-id="454d0-134">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
11. <span data-ttu-id="454d0-135">使用下列命令來執行指令碼</span><span class="sxs-lookup"><span data-stu-id="454d0-135">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="454d0-136">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="454d0-136">Sample Code</span></span>  
 <span data-ttu-id="454d0-137">下面是此範例的程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="454d0-137">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="454d0-138">C#</span><span class="sxs-lookup"><span data-stu-id="454d0-138">C#</span></span>  
  
```  
using System;  
using System.Text;  
using System.Diagnostics;  
using System.Data.SqlClient;  
using System.Collections.Generic;  
using System.Globalization;  
using Microsoft.SqlServer.Server;  
  
    /// <summary>  
    /// Defines a CLR user defined function CleanupUnusedAssemblies that drops   
    /// all the invisible assemblies with no references.  
    /// </summary>  
    public sealed class AssemblyCleanup  
    {  
        private SqlTransaction transaction;  
  
        internal class AssemblySet  
        {  
            private Dictionary<int, object> m_dictionary;  
  
            /// <summary>  
            /// Initialize internal structures  
            /// </summary>  
            /// <returns></returns>  
            public AssemblySet()  
            {  
                m_dictionary = new Dictionary<int, object>();  
            }  
  
            /// <summary>  
            /// Adds an assembly id into the current AssemblySet if it is not   
            /// already part of it.  
            /// </summary>  
            /// <returns></returns>  
            public void Add(int assemblyId)  
            {  
                if (!m_dictionary.ContainsKey(assemblyId))  
                {  
                    m_dictionary.Add(assemblyId, null);  
                }  
            }  
  
            /// <summary>  
            /// Number of assembly ids stored in this instance  
            /// </summary>  
            /// <returns></returns>  
            public int Count  
            {  
                get  
                {  
                    return m_dictionary.Count;  
                }  
            }  
  
            /// <summary>  
            /// Returns the comma-separated list of assembly ids contained in this instance  
            /// </summary>  
            /// <returns>string value that represents a comma-separated list   
            /// of assembly ids</returns>  
            public string ToCommaSeparatedList()  
            {  
                StringBuilder sb = new StringBuilder();  
  
                if (m_dictionary.Count > 0)  
                {  
                    foreach (KeyValuePair<int, object> kv in m_dictionary)  
                    {  
                        sb.Append(kv.Key);  
                        sb.Append(",");  
                    }  
  
                    sb.Length--; // remove the trailing comma  
                }  
  
                return sb.ToString();  
            }  
        }  
  
        /// <summary>  
        /// Initializes an instance of AssemblyCleanup with a SqlTransaction  
        /// </summary>  
        /// <returns></returns>  
        private AssemblyCleanup(SqlTransaction transaction)  
        {  
            this.transaction = transaction;  
        }  
  
        /// <summary>  
        /// Helper function that creates a SqlCommand object as part of the current   
        /// transaction  
        /// </summary>  
        /// <returns></returns>  
        private SqlCommand CreateCommandInTransaction()  
        {  
            SqlCommand cmd = this.transaction.Connection.CreateCommand();  
  
            cmd.Transaction = this.transaction;  
  
            return cmd;  
        }  
  
        /// <summary>  
        /// Helper function that constructs an AssemblySet instance using the   
        /// first column of the resultset resulting from the query that was passed in.  
        /// </summary>  
        /// <param name="query"></param>  
        /// <returns></returns>  
        private AssemblySet GetAssemblySetFromQuery(string query)  
        {  
            SqlCommand cmd = CreateCommandInTransaction();  
  
            AssemblySet set = new AssemblySet();  
  
            cmd.CommandText = query;  
            using (SqlDataReader rd = cmd.ExecuteReader())  
            {  
                while (rd.Read())  
                {  
                    set.Add(rd.GetInt32(0));  
                }  
            }  
  
            return set;  
        }  
  
        /// <summary>  
        /// Constructs a DROP ASSEMBLY T-SQL statement using the AssemblySet   
        /// passed in as a parameter.  
        /// </summary>  
        /// <param name="set"></param>  
        /// <returns></returns>  
        private void DropAssemblies(AssemblySet unusedAssemblySet)  
        {  
            if (unusedAssemblySet.Count > 0)  
            {  
                StringBuilder assemblyNamesToDrop = new StringBuilder();  
  
                // Gather the list of assembly names we will drop later  
                SqlCommand cmd = CreateCommandInTransaction();  
  
                cmd.CommandText = String.Format(CultureInfo.InvariantCulture,  
                    "SELECT name FROM sys.assemblies WHERE assembly_id IN ({0});",  
                    unusedAssemblySet.ToCommaSeparatedList());  
                using (SqlDataReader rd = cmd.ExecuteReader())  
                {  
                    while (rd.Read())  
                    {  
                        assemblyNamesToDrop.Append("[");  
                        assemblyNamesToDrop.Append(rd.GetString(0));  
                        assemblyNamesToDrop.Append("],");  
                    }  
                }  
  
                // Remove trailing comma  
                assemblyNamesToDrop.Length--;  
  
                // Drop all assemblies at the same time  
                cmd.CommandText = String.Format(CultureInfo.InvariantCulture,  
                    "DROP ASSEMBLY {0}", assemblyNamesToDrop.ToString());  
                cmd.ExecuteNonQuery();  
            }  
        }  
  
        /// <summary>  
        /// Serves as the stored procedure entry point and drives the process   
        /// of expanding the "assemblies in use" set, negating it, and   
        /// dropping the results  
        /// </summary>  
        /// <param name="visibleAssemblies">If set to true, will also drop   
        /// unused visible assemblies. Otherwise, will only drop unused invisible   
        /// assemblies.</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlProcedure()]  
        public static void CleanupUnusedAssemblies(bool visibleAssemblies)  
        {  
            bool succeeded = false;  
            SqlConnection conn;  
            SqlTransaction transaction;  
            string sqlStatement;  
            AssemblySet assembliesToDrop;  
            AssemblyCleanup assemblyCleanup;  
  
            conn = new SqlConnection("context connection=true");  
            conn.Open();  
            transaction = conn.BeginTransaction();  
  
            try  
            {  
                // Create a set of assemblies in use by looking at   
                // the metadata of the current database  
                sqlStatement =  
                    "DECLARE @UsedAssembly TABLE (AssemblyID int NOT NULL); " +  
                    "DECLARE @RowCount int; " +  
                    "INSERT INTO @UsedAssembly " +  
                    "SELECT DISTINCT([assembly_id]) " +  
                    "FROM sys.assembly_modules " +  
                    "UNION " +  
                    "SELECT [assembly_id] " +  
                    "FROM sys.assembly_types; " +  
                    "SET @RowCount = @@ROWCOUNT; " +  
                    "WHILE @RowCount > 0 " +  
                    "BEGIN " +  
                    "INSERT INTO @UsedAssembly " +  
                    "SELECT [referenced_assembly_id] " +  
                    "FROM sys.assembly_references ar " +  
                    "INNER JOIN @UsedAssembly ua " +  
                    "ON ar.[assembly_id] = ua.AssemblyID " +  
                    "WHERE NOT EXISTS (SELECT * FROM @UsedAssembly WHERE AssemblyID = [referenced_assembly_id]) " +  
                    "SET @RowCount = @@ROWCOUNT; " +  
                    "END;";  
  
                if (visibleAssemblies)  
                {  
                    sqlStatement +=  
                        "SELECT assembly_id " +  
                        "FROM sys.assemblies " +  
                        "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly);";  
                }  
                else  
                {  
                    sqlStatement +=  
                        "SELECT assembly_id " +  
                        "FROM sys.assemblies " +  
                        "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly) " +  
                        "    AND is_visible = 0;";  
                }  
  
                // This marks the beginning of the transaction  
                assemblyCleanup = new AssemblyCleanup(transaction);  
  
                // Assemblies that are currently in use  
                assembliesToDrop  
                    = assemblyCleanup.GetAssemblySetFromQuery(sqlStatement);  
  
                assemblyCleanup.DropAssemblies(assembliesToDrop);  
  
                // Mark as succeeded  
                succeeded = true;  
            }  
            finally  
            {  
                // We must guarantee that we explicitly call either Commit()   
                // or Rollback() before we return.  
                if (succeeded)  
                {  
                    transaction.Commit();  
                }  
                else  
                {  
                    transaction.Rollback();  
                }  
                conn.Dispose();  
            }  
        }  
    }  
  
```  
  
 <span data-ttu-id="454d0-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="454d0-139">Visual Basic</span></span>  
  
```  
Imports Microsoft.SqlServer.Server  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Collections.Generic  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Globalization  
Imports System.Text  
Imports System.Transactions  
Public NotInheritable Class AssemblyCleanup  
    Private transaction As SqlTransaction  
  
    Friend Class AssemblySet  
        Private m_dictionary As Dictionary(Of Integer, Object)  
  
        ''' <summary>  
        ''' Initialize internal structures  
        ''' </summary>  
        ''' <returns></returns>  
        Public Sub New()  
            m_dictionary = New Dictionary(Of Integer, Object)  
        End Sub  
  
        ''' <summary>  
        ''' Adds an assembly id into the current AssemblySet if it is not already part of it.  
        ''' </summary>  
        ''' <returns></returns>  
        Public Sub Add(ByVal assemblyId As Integer)  
            If Not m_dictionary.ContainsKey(assemblyId) Then  
                m_dictionary.Add(assemblyId, Nothing)  
            End If  
        End Sub  
  
        ''' <summary>  
        ''' Number of assembly ids stored in this instance  
        ''' </summary>  
        ''' <returns></returns>  
        Public ReadOnly Property Count() As Integer  
            Get  
                Return m_dictionary.Count  
            End Get  
        End Property  
  
        ''' <summary>  
        ''' Returns the comma-separated list of assembly ids contained in this instance  
        ''' </summary>  
        ''' <returns>string value that represents a comma-separated list of assembly ids</returns>  
        Public Function ToCommaSeparatedList() As String  
            Dim sb As New StringBuilder()  
  
            If m_dictionary.Count > 0 Then  
                For Each kv As KeyValuePair(Of Integer, Object) In m_dictionary  
                    If (True) Then  
                        sb.Append(kv.Key)  
                        sb.Append(",")  
                    End If  
                Next  
  
                sb.Length -= 1 ' remove the trailing comma  
            End If  
  
            Return sb.ToString()  
  
        End Function  
    End Class  
  
    ''' <summary>  
    ''' Initializes an instance of AssemblyCleanup with a SqlTransaction  
    ''' </summary>  
    ''' <returns></returns>  
    Private Sub New(ByVal trans As SqlTransaction)  
        Me.transaction = trans  
    End Sub  
  
    ''' <summary>  
    ''' Helper function that creates a SqlCommand object as part of the   
    ''' current transaction  
    ''' </summary>  
    ''' <returns></returns>  
    Private Function CreateCommandInTransaction() As SqlCommand  
        Dim cmd As SqlCommand = transaction.Connection.CreateCommand()  
  
        cmd.Transaction = Me.transaction  
  
        Return cmd  
    End Function  
  
    ''' <summary>  
    ''' Helper function that constructs an AssemblySet instance using the   
    ''' first column of the resultset resulting from the query that was passed in.  
    ''' </summary>  
    ''' <param name="query"></param>  
    ''' <returns></returns>  
    Private Function GetAssemblySetFromQuery(ByVal query As String) As AssemblySet  
        Dim cmd As SqlCommand = CreateCommandInTransaction()  
        Dim [set] As New AssemblySet()  
  
        cmd.CommandText = query  
        Dim rd As SqlDataReader = cmd.ExecuteReader()  
        Try  
            While rd.Read()  
                [set].Add(rd.GetInt32(0))  
            End While  
        Finally  
            rd.Dispose()  
        End Try  
  
        Return [set]  
    End Function  
  
    ''' <summary>  
    ''' Constructs a DROP ASSEMBLY T-SQL statement using the AssemblySet   
    ''' passed in as a parameter.  
    ''' </summary>  
    ''' <param name="set"></param>  
    ''' <returns></returns>  
    Private Sub DropAssemblies(ByVal unusedAssemblySet As AssemblySet)  
        If unusedAssemblySet.Count > 0 Then  
            Dim assemblyNamesToDrop As New StringBuilder()  
  
            ' Gather the list of assembly names we will drop later  
            Dim cmd As SqlCommand = CreateCommandInTransaction()  
  
            cmd.CommandText = String.Format(CultureInfo.InvariantCulture, _  
                "SELECT name FROM sys.assemblies WHERE assembly_id IN ({0});", _  
                unusedAssemblySet.ToCommaSeparatedList())  
            Dim rd As SqlDataReader = cmd.ExecuteReader()  
            Try  
                While rd.Read()  
                    assemblyNamesToDrop.Append("[")  
                    assemblyNamesToDrop.Append(rd.GetString(0))  
                    assemblyNamesToDrop.Append("],")  
                End While  
            Finally  
                rd.Dispose()  
            End Try  
  
            ' Remove trailing comma  
            assemblyNamesToDrop.Length -= 1  
  
            ' Drop all assemblies at the same time  
            cmd.CommandText = String.Format(CultureInfo.InvariantCulture, _  
                "DROP ASSEMBLY {0}", assemblyNamesToDrop.ToString())  
            cmd.ExecuteNonQuery()  
        End If  
    End Sub  
  
    ''' <summary>  
    ''' Serves as the stored procedure entry point and drives the process of   
    ''' expanding the "assemblies in use" set, negating it, and dropping   
    ''' the results.  
    ''' </summary>  
    ''' <param name="visibleAssemblies">If set to true, will also drop unused   
    ''' visible assemblies. Otherwise, will only drop unused invisible assemblies.</param>  
    ''' <returns></returns>  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub CleanupUnusedAssemblies(ByVal visibleAssemblies As Boolean)  
  
        Dim succeeded As Boolean = False  
        Dim conn As SqlConnection  
        Dim transaction As SqlTransaction  
        Dim sqlStatement As String  
        Dim assembliesToDrop As AssemblySet  
        Dim assemblyCleanup As AssemblyCleanup  
  
        conn = New SqlConnection("context connection=true")  
        conn.Open()  
        transaction = conn.BeginTransaction()  
  
        Try  
            ' Create a set of assemblies in use by looking at   
            ' the metadata of the current database  
            sqlStatement = "DECLARE @UsedAssembly TABLE (AssemblyID int NOT NULL); " & _  
                "DECLARE @RowCount int; " & _  
                "INSERT INTO @UsedAssembly " & _  
                "SELECT DISTINCT([assembly_id]) " & _  
                "FROM sys.assembly_modules " & _  
                "UNION " & _  
                "SELECT [assembly_id] " & _  
                "FROM sys.assembly_types; " & _  
                "SET @RowCount = @@ROWCOUNT; " & _  
                "WHILE @RowCount > 0 " & _  
                "BEGIN " & _  
                "INSERT INTO @UsedAssembly " & _  
                "SELECT [referenced_assembly_id] " & _  
                "FROM sys.assembly_references ar " & _  
                "INNER JOIN @UsedAssembly ua " & _  
                "ON ar.[assembly_id] = ua.AssemblyID " & _  
                "WHERE NOT EXISTS (SELECT * FROM @UsedAssembly WHERE AssemblyID = [referenced_assembly_id]) " & _  
                "SET @RowCount = @@ROWCOUNT; " & _  
                "END;"  
  
            If visibleAssemblies Then  
                sqlStatement += "SELECT assembly_id " & _  
                    "FROM sys.assemblies " & _  
                    "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly);"  
            Else  
                sqlStatement += "SELECT assembly_id " & _  
                    "FROM sys.assemblies " & _  
                    "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly) " & _  
                    "    AND is_visible = 0;"  
            End If  
  
            ' This marks the beginning of the transaction  
            assemblyCleanup = New AssemblyCleanup(transaction)  
  
            ' Assemblies that are currently in use  
            assembliesToDrop _  
                = assemblyCleanup.GetAssemblySetFromQuery(sqlStatement)  
  
            assemblyCleanup.DropAssemblies(assembliesToDrop)  
  
            ' Mark as succeeded  
            succeeded = True  
        Finally  
            ' We must guarantee that we explicitly call either Commit()   
            ' or Rollback() before we return.  
            If succeeded Then  
                transaction.Commit()  
            Else  
                transaction.Rollback()  
            End If  
            conn.Dispose()  
        End Try  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="454d0-140">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 安裝指令碼 (`Install.sql`)，它會部署組件並在資料庫中建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="454d0-140">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure in the database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'CleanupUnusedAssemblies')  
DROP PROCEDURE CleanupUnusedAssemblies;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'AssemblyCleanupUtils')   
DROP ASSEMBLY AssemblyCleanupUtils;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = 'C:\MySample\'  
  
CREATE ASSEMBLY AssemblyCleanupUtils   
FROM @SamplesPath + 'AssemblyCleanup.dll'   
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE CleanupUnusedAssemblies (  
@visible_assemblies bit  
) AS  
EXTERNAL NAME [AssemblyCleanupUtils].[AssemblyCleanup].CleanupUnusedAssemblies;  
GO  
```  
  
 <span data-ttu-id="454d0-141">這是 `test.sql`，它會執行預存程序，藉以測試範例。</span><span class="sxs-lookup"><span data-stu-id="454d0-141">This is `test.sql`, which tests the sample by executing the stored procedure.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
PRINT 'Before cleanup...'  
SELECT [name] FROM sys.assemblies;  
GO  
  
-- pass in false, which means the cleanup will only include invisible assemblies  
EXEC dbo.CleanupUnusedAssemblies false;  
GO  
  
PRINT 'After cleanup'  
SELECT [name] FROM sys.assemblies;  
```  
  
 <span data-ttu-id="454d0-142">下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會從資料庫中移除組件和預存程序。</span><span class="sxs-lookup"><span data-stu-id="454d0-142">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'CleanupUnusedAssemblies')  
DROP PROCEDURE CleanupUnusedAssemblies;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'AssemblyCleanupUtils')   
DROP ASSEMBLY AssemblyCleanupUtils;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="454d0-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="454d0-143">See Also</span></span>  
 [<span data-ttu-id="454d0-144">通用語言執行平台 &#40;CLR&#41; 整合的使用案例和範例</span><span class="sxs-lookup"><span data-stu-id="454d0-144">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
