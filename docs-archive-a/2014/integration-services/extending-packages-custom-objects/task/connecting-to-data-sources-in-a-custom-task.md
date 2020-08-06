---
title: 在自訂工作中連線至資料來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ConnectionManager objects
- connection managers [Integration Services], external data sources
- data sources [Integration Services], external
- custom tasks [Integration Services], external data sources
- external data sources [Integration Services]
- connections [Integration Services], external data sources
- SSIS custom tasks, external data sources
ms.assetid: 9f0b3a43-3eaa-4b3c-bb08-29b630c11306
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71c504f4b528a0c9809d00de74de4beb9c67c4f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597227"
---
# <a name="connecting-to-data-sources-in-a-custom-task"></a><span data-ttu-id="41efd-102">連接至自訂工作中的資料來源</span><span class="sxs-lookup"><span data-stu-id="41efd-102">Connecting to Data Sources in a Custom Task</span></span>
  <span data-ttu-id="41efd-103">工作會利用連接管理員連接至外部資料來源，以擷取或儲存資料。</span><span class="sxs-lookup"><span data-stu-id="41efd-103">Tasks connect to external data sources to retrieve or save data by using a connection manager.</span></span> <span data-ttu-id="41efd-104">在設計階段，連接管理員代表邏輯連接，並描述伺服器名稱與任何驗證屬性等主要資訊。</span><span class="sxs-lookup"><span data-stu-id="41efd-104">At design time, a connection manager represents a logical connection, and describes key information such as the server name and any authentication properties.</span></span> <span data-ttu-id="41efd-105">在執行階段，工作會呼叫連接管理員的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 方法，以建立連至資料來源的實體連接。</span><span class="sxs-lookup"><span data-stu-id="41efd-105">At run time, tasks call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of the connection manager to establish the physical connection to the data source.</span></span>  
  
 <span data-ttu-id="41efd-106">因為封裝可以包含許多工作，每個工作都可能有連至不同資料來源的連接，所以封裝會追蹤在 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 集合中的所有連接管理員。</span><span class="sxs-lookup"><span data-stu-id="41efd-106">Because a package can contain many tasks, each of which may have connections to different data sources, the package tracks all the connection managers in a collection, the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection.</span></span> <span data-ttu-id="41efd-107">工作會使用其封裝中的集合，以尋找它們在驗證和執行期間將使用的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="41efd-107">Tasks use the collection in their package to find the connection manager that they will use during validation and execution.</span></span> <span data-ttu-id="41efd-108"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> 集合是 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> 方法的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="41efd-108">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection is the first parameter to the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> methods.</span></span>  
  
 <span data-ttu-id="41efd-109">您可以使用圖形化使用者介面中的對話方塊或是下拉式清單，對使用者顯示集合的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件，以防止工作使用錯誤的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="41efd-109">You can prevent the task from using the wrong connection manager by displaying the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects from the collection to the user, by using a dialog box or drop-down list in the graphical user interface.</span></span> <span data-ttu-id="41efd-110">這個方法可讓使用者只能從封裝內適當類型的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件中進行選取。</span><span class="sxs-lookup"><span data-stu-id="41efd-110">This gives the user a way to select from among only those <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects of the appropriate type that are contained in the package.</span></span>  
  
 <span data-ttu-id="41efd-111">工作會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 方法以建立連至資料來源的實體連接。</span><span class="sxs-lookup"><span data-stu-id="41efd-111">Tasks call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the physical connection to the data source.</span></span> <span data-ttu-id="41efd-112">方法會傳回基礎連接物件，以供工作使用。</span><span class="sxs-lookup"><span data-stu-id="41efd-112">The method returns the underlying connection object that can then be used by the task.</span></span> <span data-ttu-id="41efd-113">因為連接管理員會將基礎連接物件的實作詳細資料與工作隔離開來，所以工作只需要呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 方法建立連接，而不必顧慮連接的其他層面。</span><span class="sxs-lookup"><span data-stu-id="41efd-113">Because the connection manager isolates the implementation details of the underlying connection object from the task, the task only has to call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the connection, and does not have to be concerned with other aspects of the connection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41efd-114">範例</span><span class="sxs-lookup"><span data-stu-id="41efd-114">Example</span></span>  
 <span data-ttu-id="41efd-115">下列範例程式碼示範 Validate 與 Execute 方法中的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 名稱之驗證，並顯示如何使用 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 方法來建立 Execute 方法中的實體連接。</span><span class="sxs-lookup"><span data-stu-id="41efd-115">The following sample code demonstrates validation of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> name in the Validate and Execute methods, and shows how to use the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method to establish the physical connection in the Execute method.</span></span>  
  
```csharp  
private string connectionManagerName = "";  
  
public string ConnectionManagerName  
{  
  get { return this.connectionManagerName; }  
  set { this.connectionManagerName = value; }  
}  
  
public override DTSExecResult Validate(  
  Connections connections, VariableDispenser variableDispenser,  
  IDTSComponentEvents componentEvents, IDTSLogging log)  
{  
  // If the connection manager exists, validation is successful;  
  // otherwise, fail validation.  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception e)  
  {  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
  
public override DTSExecResult Execute(Connections connections,   
  VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,   
  IDTSLogging log, object transaction)  
{  
  try  
  {  
    ConnectionManager cm = connections[this.connectionManagerName];  
    object connection = cm.AcquireConnection(transaction);  
    return DTSExecResult.Success;  
  }  
  catch (System.Exception exception)  
  {  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0);  
    return DTSExecResult.Failure;  
  }  
}  
```  
  
```vb  
Private _connectionManagerName As String = ""  
  
Public Property ConnectionManagerName() As String  
  Get  
    Return Me._connectionManagerName  
  End Get  
  Set(ByVal Value As String)  
    Me._connectionManagerName = value  
  End Set  
End Property  
  
Public Overrides Function Validate( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  ' If the connection manager exists, validation is successful;  
  ' otherwise fail validation.  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Return DTSExecResult.Success  
  Catch e As System.Exception  
    componentEvents.FireError(0, "SampleTask", "Invalid connection manager.", "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
  
Public Overrides Function Execute( _  
  ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, _  
  ByVal variableDispenser As Microsoft.SqlServer.Dts.Runtime.VariableDispenser, _  
  ByVal componentEvents As Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents, _  
  ByVal log As Microsoft.SqlServer.Dts.Runtime.IDTSLogging, ByVal transaction As Object) _  
  As Microsoft.SqlServer.Dts.Runtime.DTSExecResult  
  
  Try  
    Dim cm As ConnectionManager = connections(Me._connectionManagerName)  
    Dim connection As Object = cm.AcquireConnection(transaction)  
    Return DTSExecResult.Success  
  Catch exception As System.Exception  
    componentEvents.FireError(0, "SampleTask", exception.Message, "", 0)  
    Return DTSExecResult.Failure  
  End Try  
  
End Function  
```  
  
<span data-ttu-id="41efd-116">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="41efd-116">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="41efd-117">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="41efd-117">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="41efd-118">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="41efd-118">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="41efd-119">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="41efd-119">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41efd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41efd-120">See Also</span></span>  
 <span data-ttu-id="41efd-121">[Integration Services &#40;SSIS&#41; 連接](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="41efd-121">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="41efd-122">建立連接管理員</span><span class="sxs-lookup"><span data-stu-id="41efd-122">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
