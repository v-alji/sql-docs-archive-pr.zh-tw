---
title: 撰寫自訂記錄提供者的程式碼 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom log providers [Integration Services], coding
ms.assetid: 979a29ca-956e-4fdd-ab47-f06e84cead7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5d529420207ac065ae5ecb3c1d984de3021845b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701302"
---
# <a name="coding-a-custom-log-provider"></a><span data-ttu-id="bf377-102">撰寫自訂記錄提供者的程式碼</span><span class="sxs-lookup"><span data-stu-id="bf377-102">Coding a Custom Log Provider</span></span>
  <span data-ttu-id="bf377-103">建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基底類別的類別，並將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 屬性 (attribute) 套用到類別之後，必須覆寫基底類別的屬性 (properties) 與方法的實作，才可提供自訂功能。</span><span class="sxs-lookup"><span data-stu-id="bf377-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="bf377-104">如需自訂記錄提供者的實用範例，請參閱[開發自訂記錄提供者的使用者介面](developing-a-user-interface-for-a-custom-log-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="bf377-104">For working samples of custom log providers, see [Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md).</span></span>  
  
## <a name="configuring-the-log-provider"></a><span data-ttu-id="bf377-105">設定記錄提供者</span><span class="sxs-lookup"><span data-stu-id="bf377-105">Configuring the Log Provider</span></span>  
  
### <a name="initializing-the-log-provider"></a><span data-ttu-id="bf377-106">初始化記錄提供者</span><span class="sxs-lookup"><span data-stu-id="bf377-106">Initializing the Log Provider</span></span>  
 <span data-ttu-id="bf377-107">您覆寫 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.InitializeLogProvider%2A> 方法以快取連接集合與事件介面的參考。</span><span class="sxs-lookup"><span data-stu-id="bf377-107">You override the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.InitializeLogProvider%2A> method to cache references to the connections collection and the events interface.</span></span> <span data-ttu-id="bf377-108">您可以稍後在記錄提供者的其他方法中使用這些快取的參考。</span><span class="sxs-lookup"><span data-stu-id="bf377-108">You can use these cached references later in other methods of the log provider.</span></span>  
  
### <a name="using-the-configstring-property"></a><span data-ttu-id="bf377-109">使用 ConfigString 屬性</span><span class="sxs-lookup"><span data-stu-id="bf377-109">Using the ConfigString Property</span></span>  
 <span data-ttu-id="bf377-110">在設計階段，記錄提供者會從 [組態]  資料行接收組態資訊。</span><span class="sxs-lookup"><span data-stu-id="bf377-110">At design time, a log provider receives configuration information from the **Configuration** column.</span></span> <span data-ttu-id="bf377-111">這個組態資訊會對應至記錄提供者的 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="bf377-111">This configuration information corresponds to the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property of the log provider.</span></span> <span data-ttu-id="bf377-112">依預設，這個資料行包含您可以從中擷取任何字串資訊的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="bf377-112">By default, this column contains a text box from which you can retrieve any string information.</span></span> <span data-ttu-id="bf377-113">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 所含的大部分記錄提供者，都會使用此屬性儲存提供者用以連接外部資料來源之連接管理員的名稱。</span><span class="sxs-lookup"><span data-stu-id="bf377-113">Most of the log providers included with [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] use this property to store the name of the connection manager that the provider uses to connect to an external data source.</span></span> <span data-ttu-id="bf377-114">如果您的記錄提供者使用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 屬性，請使用 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> 方法驗證這個屬性，並確定已正確設定屬性。</span><span class="sxs-lookup"><span data-stu-id="bf377-114">If your log provider uses the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property, use the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method to validate this property and make sure that the property is set correctly.</span></span>  
  
### <a name="validating-the-log-provider"></a><span data-ttu-id="bf377-115">驗證記錄提供者</span><span class="sxs-lookup"><span data-stu-id="bf377-115">Validating the Log Provider</span></span>  
 <span data-ttu-id="bf377-116">您覆寫 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> 方法以確定已正確設定提供者，而且已準備執行。</span><span class="sxs-lookup"><span data-stu-id="bf377-116">You override the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method to make sure that the provider has been configured correctly and is ready for execution.</span></span> <span data-ttu-id="bf377-117">一般而言，驗證的最低層級是確定 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 已正確地設定。</span><span class="sxs-lookup"><span data-stu-id="bf377-117">Typically, a minimum level of validation is to make sure that the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> is set correctly.</span></span> <span data-ttu-id="bf377-118">必須等到記錄提供者從 <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> 方法傳回 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A>，執行才能繼續。</span><span class="sxs-lookup"><span data-stu-id="bf377-118">Execution cannot continue until the log provider returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="bf377-119">下列程式碼範例顯示 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> 的實作，以確定已指定連接管理員的名稱、連接管理員存在於封裝中，以及連接管理員傳回 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 屬性中的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="bf377-119">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> that makes sure that the name of a connection manager name is specified, that the connection manager exists in the package, and that the connection manager returns a file name in the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property.</span></span>  
  
```csharp  
public override DTSExecResult Validate(IDTSInfoEvents infoEvents)  
{  
    if (this.ConfigString.Length == 0 || connections.Contains(ConfigString) == false)  
    {  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
        return DTSExecResult.Failure;  
    }  
    else  
    {  
        string fileName = connections[ConfigString].AcquireConnection(null) as string;  
  
        if (fileName == null || fileName.Length == 0)  
        {  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
            return DTSExecResult.Failure;  
        }  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As IDTSInfoEvents) As DTSExecResult  
    If Me.ConfigString.Length = 0 Or connections.Contains(ConfigString) = False Then  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
        Return DTSExecResult.Failure  
    Else   
        Dim fileName As String =  connections(ConfigString).AcquireConnectionCType(as string, Nothing)  
  
        If fileName = Nothing Or fileName.Length = 0 Then  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
            Return DTSExecResult.Failure  
        End If  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
### <a name="persisting-the-log-provider"></a><span data-ttu-id="bf377-120">保存記錄提供者</span><span class="sxs-lookup"><span data-stu-id="bf377-120">Persisting the Log Provider</span></span>  
 <span data-ttu-id="bf377-121">一般而言，您不必實作連接管理員的自訂持續性。</span><span class="sxs-lookup"><span data-stu-id="bf377-121">Ordinarily you do not have to implement custom persistence for a connection manager.</span></span> <span data-ttu-id="bf377-122">只有在物件的屬性使用複雜的資料類型時，才需要自訂持續性。</span><span class="sxs-lookup"><span data-stu-id="bf377-122">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="bf377-123">如需詳細資訊，請參閱[開發 Integration Services 的自訂物件](../developing-custom-objects-for-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bf377-123">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>  
  
## <a name="logging-with-the-log-provider"></a><span data-ttu-id="bf377-124">使用記錄提供者進行記錄</span><span class="sxs-lookup"><span data-stu-id="bf377-124">Logging with the Log Provider</span></span>  
 <span data-ttu-id="bf377-125">有三個必須由所有記錄提供者覆寫的執行階段方法：<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>。</span><span class="sxs-lookup"><span data-stu-id="bf377-125">There are three run-time methods that must be overridden by all log providers: <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bf377-126">在單一封裝的驗證與執行期間，會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法一次以上。</span><span class="sxs-lookup"><span data-stu-id="bf377-126">During the validation and execution of a single package, the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> methods are called more than one time.</span></span> <span data-ttu-id="bf377-127">請確定您的自訂程式碼不會造成記錄的下一個開啟和關閉覆寫先前的記錄項目。</span><span class="sxs-lookup"><span data-stu-id="bf377-127">Make sure that your custom code does not cause earlier log entries to be overwritten by the next opening and closing of the log.</span></span> <span data-ttu-id="bf377-128">如果您已選擇記錄測試封裝中的驗證事件，第一個會看到的記錄事件應該是 OnPreValidate；如果您看到的第一個記錄的事件是 PackageStart，表示最初的驗證事件已被覆寫。</span><span class="sxs-lookup"><span data-stu-id="bf377-128">If you have selected to log validation events in your test package, the first logged event that you should see is OnPreValidate; if instead the first logged event that you see is PackageStart, the initial validation events have been overwritten.</span></span>  
  
### <a name="opening-the-log"></a><span data-ttu-id="bf377-129">開啟記錄</span><span class="sxs-lookup"><span data-stu-id="bf377-129">Opening the Log</span></span>  
 <span data-ttu-id="bf377-130">大部分的記錄提供者都會連接到外部資料來源，例如檔案或是資料庫，以儲存在封裝執行期間收集的事件資訊。</span><span class="sxs-lookup"><span data-stu-id="bf377-130">Most log providers connect to an external data source, such as a file or database, to store the event information that is collected during package execution.</span></span> <span data-ttu-id="bf377-131">如同執行階段中的任何其他物件，連接到外部資料來源通常是透過使用連接管理員物件來完成。</span><span class="sxs-lookup"><span data-stu-id="bf377-131">As with any other object in the runtime, connecting to the external data source is typically accomplished by using connection manager objects.</span></span>  
  
 <span data-ttu-id="bf377-132">在封裝執行開始時會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 方法。覆寫這個方法會建立連至外部資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="bf377-132">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> method is called at the start of package execution.Override this method to establish a connection to the external data source.</span></span>  
  
 <span data-ttu-id="bf377-133">下列範例程式碼顯示的記錄提供者會開啟一個文字檔案，以供 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 期間寫入。</span><span class="sxs-lookup"><span data-stu-id="bf377-133">The following sample code shows a log provider that opens a text file for writing during <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>.</span></span> <span data-ttu-id="bf377-134">它會透過呼叫由 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 屬性指定的連接管理員之 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> 方法，來開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="bf377-134">It opens the file by calling the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of the connection manager that was specified in the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property.</span></span>  
  
```csharp  
public override void OpenLog()  
{  
    if(!this.connections.Contains(this.ConfigString))  
        throw new Exception("The ConnectionManager " + this.ConfigString + " does not exist in the Connections collection.");  
  
    this.connectionManager = connections[ConfigString];  
    string filePath = this.connectionManager.AcquireConnection(null) as string;  
  
    if(filePath == null || filePath.Length == 0)  
        throw new Exception("The ConnectionManager " + this.ConfigString + " is not a valid FILE ConnectionManager");  
  
    //  Create a StreamWriter to append to.  
    sw = new StreamWriter(filePath,true);  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString());  
}  
```  
  
```vb  
Public Overrides  Sub OpenLog()  
    If Not Me.connections.Contains(Me.ConfigString) Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " does not exist in the Connections collection.")  
    End If  
  
    Me.connectionManager = connections(ConfigString)  
    Dim filePath As String =  Me.connectionManager.AcquireConnectionCType(as string, Nothing)  
  
    If filePath = Nothing Or filePath.Length = 0 Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " is not a valid FILE ConnectionManager")  
    End If  
  
    '  Create a StreamWriter to append to.  
    sw = New StreamWriter(filePath,True)  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString())  
End Sub  
```  
  
### <a name="writing-log-entries"></a><span data-ttu-id="bf377-135">寫入記錄項目</span><span class="sxs-lookup"><span data-stu-id="bf377-135">Writing Log Entries</span></span>  
 <span data-ttu-id="bf377-136">每次套件中物件呼叫其中一個事件介面上的 Fire\<event> 方法來引發事件時，就會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="bf377-136">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method is called every time that an object in the package raises an event by calling a Fire\<event> method on one of the event interfaces.</span></span> <span data-ttu-id="bf377-137">每個引發的事件都會帶有關於其內容且通常是說明訊息的資訊。</span><span class="sxs-lookup"><span data-stu-id="bf377-137">Each event is raised with information about its context and usually an explanatory message.</span></span> <span data-ttu-id="bf377-138">不過，並不是每次呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法都包括每個方法參數的資訊。</span><span class="sxs-lookup"><span data-stu-id="bf377-138">However, not every call to the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method includes information for every method parameter.</span></span> <span data-ttu-id="bf377-139">例如，有些其名稱字面意義明白的標準事件並未提供 MessageText，而且 DataCode 與 DataBytes 是為了提供選擇性的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="bf377-139">For example, some standard events whose names are self-explanatory do not provide MessageText, and DataCode and DataBytes are intended for optional supplemental information.</span></span>  
  
 <span data-ttu-id="bf377-140">下列程式碼範例會實作 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> 方法，並將事件寫入上一節所開啟的資料流。</span><span class="sxs-lookup"><span data-stu-id="bf377-140">The following code example implements the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method, and writes the events to the stream that was opened in the previous section.</span></span>  
  
```csharp  
public override void Log(string logEntryName, string computerName, string operatorName, string sourceName, string sourceID, string executionID, string messageText, DateTime startTime, DateTime endTime, int dataCode, byte[] dataBytes)  
{  
    sw.Write(logEntryName + ",");  
    sw.Write(computerName + ",");  
    sw.Write(operatorName + ",");  
    sw.Write(sourceName + ",");  
    sw.Write(sourceID + ",");  
    sw.Write(messageText + ",");  
    sw.Write(dataBytes + ",");  
    sw.WriteLine("");  
}  
```  
  
```vb  
Public Overrides  Sub Log(ByVal logEnTryName As String, ByVal computerName As String, ByVal operatorName As String, ByVal sourceName As String, ByVal sourceID As String, ByVal executionID As String, ByVal messageText As String, ByVal startTime As DateTime, ByVal endTime As DateTime, ByVal dataCode As Integer, ByVal dataBytes() As Byte)  
    sw.Write(logEnTryName + ",")  
    sw.Write(computerName + ",")  
    sw.Write(operatorName + ",")  
    sw.Write(sourceName + ",")  
    sw.Write(sourceID + ",")  
    sw.Write(messageText + ",")  
    sw.Write(dataBytes + ",")  
    sw.WriteLine("")  
End Sub  
```  
  
### <a name="closing-the-log"></a><span data-ttu-id="bf377-141">關閉記錄</span><span class="sxs-lookup"><span data-stu-id="bf377-141">Closing the Log</span></span>  
 <span data-ttu-id="bf377-142">在封裝中的所有物件都完成執行之後，或是當封裝因為錯誤而停止時，會在封裝執行結束時呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="bf377-142">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> method is called at the end of package execution, after all the objects in the package have completed execution, or, when the package stops because of errors.</span></span>  
  
 <span data-ttu-id="bf377-143">下列程式碼範例示範 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> 方法的實作，這個方法會關閉在 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> 方法期間開啟的檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="bf377-143">The following code example demonstrates an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> method that closes the file stream that was opened during the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> method.</span></span>  
  
```csharp  
public override void CloseLog()  
{  
    if (sw != null)  
    {  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString());  
        sw.Close();  
    }  
}  
```  
  
```vb  
Public Overrides  Sub CloseLog()  
    If Not sw Is Nothing Then  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString())  
        sw.Close()  
    End If  
End Sub  
```  
  
<span data-ttu-id="bf377-144">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="bf377-144">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bf377-145">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="bf377-145">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bf377-146">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="bf377-146">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bf377-147">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="bf377-147">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf377-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf377-148">See Also</span></span>  
 <span data-ttu-id="bf377-149">[建立自訂記錄提供者](creating-a-custom-log-provider.md) </span><span class="sxs-lookup"><span data-stu-id="bf377-149">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) </span></span>  
 [<span data-ttu-id="bf377-150">開發自訂記錄提供者的使用者介面</span><span class="sxs-lookup"><span data-stu-id="bf377-150">Developing a User Interface for a Custom Log Provider</span></span>](developing-a-user-interface-for-a-custom-log-provider.md)  
  
  
