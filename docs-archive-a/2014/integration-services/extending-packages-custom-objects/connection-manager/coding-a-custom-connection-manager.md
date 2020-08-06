---
title: 撰寫自訂連線管理員的程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], coding
ms.assetid: b12b6778-1f01-4a7d-984d-73f2f7630aa5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 793d70ba0a9ae6176ab35c82e16b9aba8c9ba2cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705301"
---
# <a name="coding-a-custom-connection-manager"></a><span data-ttu-id="7b9f0-102">撰寫自訂連接管理員的程式碼</span><span class="sxs-lookup"><span data-stu-id="7b9f0-102">Coding a Custom Connection Manager</span></span>
  <span data-ttu-id="7b9f0-103">建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基底類別的類別，並將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 屬性 (attribute) 套用到類別之後，必須覆寫基底類別的屬性 (properties) 與方法的實作，才可提供自訂功能。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="7b9f0-104">如需連線管理員範例，請參閱[開發自訂連線管理員的使用者介面](developing-a-user-interface-for-a-custom-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-104">For samples of custom connection managers, see [Developing a User Interface for a Custom Connection Manager](developing-a-user-interface-for-a-custom-connection-manager.md).</span></span> <span data-ttu-id="7b9f0-105">在本主題中所顯示的程式碼範例是取自＜SQL Server 自訂連接管理員＞範例。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-105">The code examples shown in this topic are drawn from the SQL Server Custom Connection Manager sample.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b9f0-106">已經建置到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中的大多數工作、來源和目的地只能搭配特定類型的內建連接管理員一起使用。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-106">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="7b9f0-107">因此，不能使用內建工作和元件來測試這些範例。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-107">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="configuring-the-connection-manager"></a><span data-ttu-id="7b9f0-108">設定連接管理員</span><span class="sxs-lookup"><span data-stu-id="7b9f0-108">Configuring the Connection Manager</span></span>  
  
### <a name="setting-the-connectionstring-property"></a><span data-ttu-id="7b9f0-109">設定 ConnectionString 屬性</span><span class="sxs-lookup"><span data-stu-id="7b9f0-109">Setting the ConnectionString Property</span></span>  
 <span data-ttu-id="7b9f0-110"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 屬性是重要的屬性，而且是自訂連接管理員特有的唯一屬性。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-110">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property is an important property and the only property unique to a custom connection manager.</span></span> <span data-ttu-id="7b9f0-111">連接管理員使用此屬性值，以連接至外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-111">The connection manager uses the value of this property to connect to the external data source.</span></span> <span data-ttu-id="7b9f0-112">如果您要結合數個其他的屬性 (例如伺服器名稱與資料庫名稱) 來建立連接字串，可以使用 Helper 函數組合字串，方法是以使用者提供的新值取代連接字串範本中的某些值。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-112">If you are combining several other properties, such as server name and database name, to create the connection string, you can use a helper function to assemble the string by replacing certain values in a connection string template with the new value supplied by the user.</span></span> <span data-ttu-id="7b9f0-113">下列程式碼範例顯示 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 屬性的實作，此屬性依賴 Helper 函數組合字串。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-113">The following code example shows an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property that relies on a helper function to assemble the string.</span></span>  
  
```vb  
' Default values.  
Private _serverName As String = "(local)"  
Private _databaseName As String = "AdventureWorks"  
Private _connectionString As String = String.Empty  
  
Private Const CONNECTIONSTRING_TEMPLATE As String = _  
  "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI"  
  
Public Property ServerName() As String  
  Get  
    Return _serverName  
  End Get  
  Set(ByVal value As String)  
    _serverName = value  
  End Set  
End Property  
  
Public Property DatabaseName() As String  
  Get  
    Return _databaseName  
  End Get  
  Set(ByVal value As String)  
    _databaseName = value  
  End Set  
End Property  
  
Public Overrides Property ConnectionString() As String  
  Get  
    UpdateConnectionString()  
    Return _connectionString  
  End Get  
  Set(ByVal value As String)  
    _connectionString = value  
  End Set  
End Property  
  
Private Sub UpdateConnectionString()  
  
  Dim temporaryString As String = CONNECTIONSTRING_TEMPLATE  
  
  If Not String.IsNullOrEmpty(_serverName) Then  
    temporaryString = temporaryString.Replace("<servername>", _serverName)  
  End If  
  If Not String.IsNullOrEmpty(_databaseName) Then  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName)  
  End If  
  
  _connectionString = temporaryString  
  
End Sub  
```  
  
```csharp  
// Default values.  
private string _serverName = "(local)";  
private string _databaseName = "AdventureWorks";  
private string _connectionString = String.Empty;  
  
private const string CONNECTIONSTRING_TEMPLATE = "Data Source=<servername>;Initial Catalog=<databasename>;Integrated Security=SSPI";  
  
public string ServerName  
{  
  get  
  {  
    return _serverName;  
  }  
  set  
  {  
    _serverName = value;  
  }  
}  
  
public string DatabaseName  
{  
  get  
  {  
    return _databaseName;  
  }  
  set  
  {  
    _databaseName = value;  
  }  
}  
  
public override string ConnectionString  
{  
  get  
  {  
    UpdateConnectionString();  
    return _connectionString;  
  }  
  set  
  {  
    _connectionString = value;  
  }  
}  
  
private void UpdateConnectionString()  
{  
  
  string temporaryString = CONNECTIONSTRING_TEMPLATE;  
  
  if (!String.IsNullOrEmpty(_serverName))  
  {  
    temporaryString = temporaryString.Replace("<servername>", _serverName);  
  }  
  
  if (!String.IsNullOrEmpty(_databaseName))  
  {  
    temporaryString = temporaryString.Replace("<databasename>", _databaseName);  
  }  
  
  _connectionString = temporaryString;  
  
}  
```  
  
### <a name="validating-the-connection-manager"></a><span data-ttu-id="7b9f0-114">驗證連接管理員</span><span class="sxs-lookup"><span data-stu-id="7b9f0-114">Validating the Connection Manager</span></span>  
 <span data-ttu-id="7b9f0-115">您覆寫 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> 方法以確定已正確設定連接管理員。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-115">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method to make sure that the connection manager has been configured correctly.</span></span> <span data-ttu-id="7b9f0-116">至少，您應該驗證連接字串的格式，並確定已為所有的引數提供值。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-116">At a minimum, you should validate the format of the connection string and make sure that values have been provided for all arguments.</span></span> <span data-ttu-id="7b9f0-117">必須等到連接管理員從 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> 方法傳回 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A>，執行才能繼續。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-117">Execution cannot continue until the connection manager returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="7b9f0-118">下列程式碼範例顯示 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> 的實作，以確定使用者已指定連接的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-118">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.Validate%2A> that makes sure that the user has specified a server name for the connection.</span></span>  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents) As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  If String.IsNullOrEmpty(_serverName) Then  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0)  
    Return DTSExecResult.Failure  
  Else  
    Return DTSExecResult.Success  
  End If  
  
End Function  
```  
  
```csharp  
public override Microsoft.SqlServer.Dts.Runtime.DTSExecResult Validate(Microsoft.SqlServer.Dts.Runtime.IDTSInfoEvents infoEvents)  
{  
  
  if (String.IsNullOrEmpty(_serverName))  
  {  
    infoEvents.FireError(0, "SqlConnectionManager", "No server name specified", String.Empty, 0);  
    return DTSExecResult.Failure;  
  }  
  else  
  {  
    return DTSExecResult.Success;  
  }  
  
}  
```  
  
### <a name="persisting-the-connection-manager"></a><span data-ttu-id="7b9f0-119">保存連接管理員</span><span class="sxs-lookup"><span data-stu-id="7b9f0-119">Persisting the Connection Manager</span></span>  
 <span data-ttu-id="7b9f0-120">通常，您不必實作連接管理員的自訂持續性。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-120">Usually, you do not have to implement custom persistence for a connection manager.</span></span> <span data-ttu-id="7b9f0-121">只有在物件的屬性使用複雜的資料類型時，才需要自訂持續性。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-121">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="7b9f0-122">如需詳細資訊，請參閱[開發 Integration Services 的自訂物件](../developing-custom-objects-for-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-122">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>  
  
## <a name="working-with-the-external-data-source"></a><span data-ttu-id="7b9f0-123">使用外部資料來源</span><span class="sxs-lookup"><span data-stu-id="7b9f0-123">Working with the External Data Source</span></span>  
 <span data-ttu-id="7b9f0-124">支援連接至外部資料來源的方法是自訂連接管理員最重要的方法。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-124">The methods that support connecting to an external data source are the most important methods of a custom connection manager.</span></span> <span data-ttu-id="7b9f0-125"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 方法是在設計階段與執行階段的不同時間呼叫。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-125">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods are called at various times during both design time and run time.</span></span>  
  
### <a name="acquiring-the-connection"></a><span data-ttu-id="7b9f0-126">取得連接</span><span class="sxs-lookup"><span data-stu-id="7b9f0-126">Acquiring the Connection</span></span>  
 <span data-ttu-id="7b9f0-127">您需要決定哪些類型的物件適用於 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 方法，從自訂連接管理員傳回。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-127">You need to decide what type of object it is appropriate for the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method to return from your custom connection manager.</span></span> <span data-ttu-id="7b9f0-128">例如，檔案連接管理員只會傳回包含路徑與檔案名稱的字串，而 ADO.NET 連接管理員則會傳回已經開啟的 Managed 連接物件。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-128">For example, a File connection manager returns only a string that contains a path and filename, whereas an ADO.NET connection manager returns a managed connection object that is already open.</span></span> <span data-ttu-id="7b9f0-129">OLE DB 連接管理員會傳回原生 OLE DB 連接物件，而此物件無法從 Managed 程式碼中加以使用。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-129">An OLE DB connection manager returns a native OLE DB connection object that cannot be used from managed code.</span></span> <span data-ttu-id="7b9f0-130">本主題中的程式碼片段是取自 SQL Server 連接管理員，它會傳回已開啟的 `SqlConnection` 物件。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-130">The custom SQL Server connection manager, from which the code snippets in this topic are taken, returns an open `SqlConnection` object.</span></span>  
  
 <span data-ttu-id="7b9f0-131">連接管理員的使用者需要事先知道需要哪些類型的物件，這樣他們才能將傳回的物件轉換為適當的類型，並存取其方法與屬性。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-131">Users of your connection manager need to know in advance what type of object to expect, so that they can cast the returned object to the appropriate type and access its methods and properties.</span></span>  
  
```vb  
Public Overrides Function AcquireConnection(ByVal txn As Object) As Object  
  
  Dim sqlConnection As New SqlConnection  
  
  UpdateConnectionString()  
  
  With sqlConnection  
    .ConnectionString = _connectionString  
    .Open()  
  End With  
  
  Return sqlConnection  
  
End Function  
```  
  
```csharp  
public override object AcquireConnection(object txn)  
{  
  
  SqlConnection sqlConnection = new SqlConnection();  
  
  UpdateConnectionString();  
  
  {  
    sqlConnection.ConnectionString = _connectionString;  
    sqlConnection.Open();  
  }  
  
  return sqlConnection;  
  
}  
```  
  
### <a name="releasing-the-connection"></a><span data-ttu-id="7b9f0-132">解除連接</span><span class="sxs-lookup"><span data-stu-id="7b9f0-132">Releasing the Connection</span></span>  
 <span data-ttu-id="7b9f0-133">您在 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> 方法中所採取的動作，取決於從 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 方法傳回的物件類型。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-133">The action that you take in the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> method depends on the type of object that you returned from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> method.</span></span> <span data-ttu-id="7b9f0-134">如果有開啟的連接物件，您應該關閉它並釋放其所使用的任何資源。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-134">If there is an open connection object, you should close it and to release any resources that it is using.</span></span> <span data-ttu-id="7b9f0-135">如果 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 只傳回字串值，則不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-135">If <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> returned only a string value, no action needs to be taken.</span></span>  
  
```vb  
Public Overrides Sub ReleaseConnection(ByVal connection As Object)  
  
  Dim sqlConnection As SqlConnection  
  
  sqlConnection = DirectCast(connection, SqlConnection)  
  
  If sqlConnection.State <> ConnectionState.Closed Then  
    sqlConnection.Close()  
  End If  
  
End Sub  
```  
  
```csharp  
public override void ReleaseConnection(object connection)  
{  
  SqlConnection sqlConnection;  
  sqlConnection = (SqlConnection)connection;  
  if (sqlConnection.State != ConnectionState.Closed)  
    sqlConnection.Close();  
}  
```  
  
<span data-ttu-id="7b9f0-136">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="7b9f0-136">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7b9f0-137">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="7b9f0-137">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7b9f0-138">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="7b9f0-138">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7b9f0-139">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="7b9f0-139">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b9f0-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b9f0-140">See Also</span></span>  
 <span data-ttu-id="7b9f0-141">[建立自訂連線管理員](creating-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7b9f0-141">[Creating a Custom Connection Manager](creating-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="7b9f0-142">開發自訂連接管理員的使用者介面</span><span class="sxs-lookup"><span data-stu-id="7b9f0-142">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
