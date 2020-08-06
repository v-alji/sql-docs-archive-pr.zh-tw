---
title: 開發自訂連線管理員的使用者介面 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], developing user interface
- custom user interface [Integration Services], custom connection manager
ms.assetid: 908bf2ac-fc84-4af8-a869-1cb43573d2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc0e9f2a76f3d97c925c44219683ca6cd655e43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595197"
---
# <a name="developing-a-user-interface-for-a-custom-connection-manager"></a><span data-ttu-id="038fb-102">開發自訂連接管理員的使用者介面</span><span class="sxs-lookup"><span data-stu-id="038fb-102">Developing a User Interface for a Custom Connection Manager</span></span>
  <span data-ttu-id="038fb-103">在您覆寫基底類別的屬性與方法的實作，以提供自訂功能之後，可能會想要建立連接管理員的自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="038fb-103">After you have overridden the implementation of the properties and methods of the base class to provide your custom functionality, you may want to create a custom user interface for your connection manager.</span></span> <span data-ttu-id="038fb-104">如果您不建立自訂使用者介面，使用者只能透過使用 [屬性] 視窗設定您的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="038fb-104">If you do not create a custom user interface, users can configure your connection manager only by using the Properties window.</span></span>  
  
 <span data-ttu-id="038fb-105">在自訂使用者介面專案或組件中，通常有兩個類別：實作 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 的類別，以及它所顯示的 Windows Form，以收集使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="038fb-105">In a custom user interface project or assembly, you normally have two classes-a class that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>, and the Windows form that it displays to gather information from the user.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="038fb-106">在簽署和建立自訂使用者介面，以及在全域組件快取中安裝它之後 (如[撰寫自訂連線管理員的程式碼](../building-deploying-and-debugging-custom-objects.md)中所述)，請記得在 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 的 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> 屬性中提供這個類別的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="038fb-106">After signing and building your custom user interface and installing it in the global assembly cache as described in [Coding a Custom Connection Manager](../building-deploying-and-debugging-custom-objects.md), remember to provide the fully qualified name of this class in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="038fb-107">已經建置到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中的大多數工作、來源和目的地只能搭配特定類型的內建連接管理員一起使用。</span><span class="sxs-lookup"><span data-stu-id="038fb-107">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="038fb-108">因此，不能使用內建工作和元件來測試這些範例。</span><span class="sxs-lookup"><span data-stu-id="038fb-108">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="coding-the-user-interface-class"></a><span data-ttu-id="038fb-109">撰寫使用者介面類別的程式碼</span><span class="sxs-lookup"><span data-stu-id="038fb-109">Coding the User Interface Class</span></span>  
 <span data-ttu-id="038fb-110"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 介面具有四種方法：<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A>。</span><span class="sxs-lookup"><span data-stu-id="038fb-110">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface has four methods: <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A>.</span></span> <span data-ttu-id="038fb-111">下列各節將描述這四種方法。</span><span class="sxs-lookup"><span data-stu-id="038fb-111">The following sections describe these four methods.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="038fb-112">當使用者刪除連接管理員的執行個體時，如果不需要清除，則不需要為 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> 方法撰寫任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="038fb-112">You may not need to write any code for the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> method if no cleanup is required when the user deletes an instance of the connection manager.</span></span>  
  
### <a name="initializing-the-user-interface"></a><span data-ttu-id="038fb-113">初始化使用者介面</span><span class="sxs-lookup"><span data-stu-id="038fb-113">Initializing the User Interface</span></span>  
 <span data-ttu-id="038fb-114">在 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> 方法中，設計工具會提供設定中連接管理員的參考，如此使用者介面類別就可以修改連接管理員的屬性。</span><span class="sxs-lookup"><span data-stu-id="038fb-114">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> method, the designer provides a reference to the connection manager that is being configured so that the user interface class can modify the connection manager's properties.</span></span> <span data-ttu-id="038fb-115">如下列程式碼所示，您的程式碼需要快取連線管理員的參考，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="038fb-115">As shown in the following code, your code needs to cache the reference to the connection managerfor later use.</span></span>  
  
```vb  
Public Sub Initialize(ByVal connectionManager As Microsoft.SqlServer.Dts.Runtime.ConnectionManager, ByVal serviceProvider As System.IServiceProvider) Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize  
  
    _connectionManager = connectionManager  
    _serviceProvider = serviceProvider  
  
  End Sub  
```  
  
```csharp  
public void Initialize(Microsoft.SqlServer.Dts.Runtime.ConnectionManager connectionManager, System.IServiceProvider serviceProvider)  
{  
  
  _connectionManager = connectionManager;  
  _serviceProvider = serviceProvider;  
  
}  
```  
  
### <a name="creating-a-new-instance-of-the-user-interface"></a><span data-ttu-id="038fb-116">建立使用者介面的新執行個體</span><span class="sxs-lookup"><span data-stu-id="038fb-116">Creating a New Instance of the User Interface</span></span>  
 <span data-ttu-id="038fb-117">當使用者建立連接管理員的新執行個體時，會在 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> 方法之後呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> 方法 (不是建構函式)。</span><span class="sxs-lookup"><span data-stu-id="038fb-117">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> method, which is not a constructor, is called after the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> method when the user creates a new instance of the connection manager.</span></span> <span data-ttu-id="038fb-118">在 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> 方法中，除非使用者已複製和貼上現有的連接管理員，否則您通常會希望顯示供編輯之用的表單。</span><span class="sxs-lookup"><span data-stu-id="038fb-118">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> method, you usually want to display the form for editing, unless the user has copied and pasted an existing connection manager.</span></span> <span data-ttu-id="038fb-119">下列程式碼會顯示此方法的實作。</span><span class="sxs-lookup"><span data-stu-id="038fb-119">The following code shows an implementation of this method.</span></span>  
  
```vb  
Public Function [New](ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, ByVal connectionUIArgs As Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs) As Boolean Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New  
  
  Dim clipboardService As IDtsClipboardService  
  
  clipboardService = _  
    DirectCast(_serviceProvider.GetService(GetType(IDtsClipboardService)), IDtsClipboardService)  
  If Not clipboardService Is Nothing Then  
    ' If the connection manager has been copied and pasted, take no action.  
    If clipboardService.IsPasteActive Then  
      Return True  
    End If  
  End If  
  
  Return EditSqlConnection(parentWindow)  
  
End Function  
```  
  
```csharp  
public bool New(System.Windows.Forms.IWin32Window parentWindow, Microsoft.SqlServer.Dts.Runtime.Connections connections, Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs connectionUIArgs)  
  {  
    IDtsClipboardService clipboardService;  
  
    clipboardService = (IDtsClipboardService)_serviceProvider.GetService(typeof(IDtsClipboardService));  
    if (clipboardService != null)  
    // If connection manager has been copied and pasted, take no action.  
    {  
      if (clipboardService.IsPasteActive)  
      {  
        return true;  
      }  
    }  
  
    return EditSqlConnection(parentWindow);  
  }  
```  
  
### <a name="editing-the-connection-manager"></a><span data-ttu-id="038fb-120">編輯連接管理員</span><span class="sxs-lookup"><span data-stu-id="038fb-120">Editing the Connection Manager</span></span>  
 <span data-ttu-id="038fb-121">因為會從 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> 和 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> 方法呼叫要編輯的表單，所以使用 Helper 函數封裝顯示表單的程式碼，會很方便。</span><span class="sxs-lookup"><span data-stu-id="038fb-121">Because the form for editing is called from both the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> methods, it is convenient to use a helper function to encapsulate the code that displays the form.</span></span> <span data-ttu-id="038fb-122">下列程式碼會顯示此 Helper 函數的實作。</span><span class="sxs-lookup"><span data-stu-id="038fb-122">The following code shows an implementation of this helper function.</span></span>  
  
```vb  
Private Function EditSqlConnection(ByVal parentWindow As IWin32Window) As Boolean  
  
  Dim sqlCMUIForm As New SqlConnMgrUIFormVB  
  
  sqlCMUIForm.Initialize(_connectionManager, _serviceProvider)  
  If sqlCMUIForm.ShowDialog(parentWindow) = DialogResult.OK Then  
    Return True  
  Else  
    Return False  
  End If  
  
End Function  
```  
  
```csharp  
private bool EditSqlConnection(IWin32Window parentWindow)  
 {  
  
   SqlConnMgrUIFormCS sqlCMUIForm = new SqlConnMgrUIFormCS();  
  
   sqlCMUIForm.Initialize(_connectionManager, _serviceProvider);  
   if (sqlCMUIForm.ShowDialog(parentWindow) == DialogResult.OK)  
   {  
     return true;  
   }  
   else  
   {  
     return false;  
   }  
  
 }  
```  
  
 <span data-ttu-id="038fb-123">在 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> 方法中，您只需要顯示供編輯之用的表單。</span><span class="sxs-lookup"><span data-stu-id="038fb-123">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> method, you simply have to display the form for editing.</span></span> <span data-ttu-id="038fb-124">下列程式碼顯示 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> 方法的實作，該方法使用 Helper 函數以封裝表單的程式碼。</span><span class="sxs-lookup"><span data-stu-id="038fb-124">The following code shows an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> method that uses a helper function to encapsulate the code for the form.</span></span>  
  
```vb  
Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, ByVal connectionUIArg As Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs) As Boolean Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit  
  
  Return EditSqlConnection(parentWindow)  
  
End Function  
```  
  
```csharp  
public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Microsoft.SqlServer.Dts.Runtime.Connections connections, Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs connectionUIArg)  
{  
  
  return EditSqlConnection(parentWindow);  
  
}  
```  
  
## <a name="coding-the-user-interface-form"></a><span data-ttu-id="038fb-125">撰寫使用者介面表單的程式碼</span><span class="sxs-lookup"><span data-stu-id="038fb-125">Coding the User Interface Form</span></span>  
 <span data-ttu-id="038fb-126">在建立使用者介面類別以實作 <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> 介面的方法之後，您必須建立 Windows Form，讓使用者能夠在其中設定連接管理員的屬性。</span><span class="sxs-lookup"><span data-stu-id="038fb-126">After creating the user interface class that implements the methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface, you must create a Windows form where the user can configure the properties of your connection manager.</span></span>  
  
### <a name="initializing-the-user-interface-form"></a><span data-ttu-id="038fb-127">初始化使用者介面表單</span><span class="sxs-lookup"><span data-stu-id="038fb-127">Initializing the User Interface Form</span></span>  
 <span data-ttu-id="038fb-128">當您顯示供編輯之用的自訂表單時，可以傳遞編輯中連接管理員的參考。</span><span class="sxs-lookup"><span data-stu-id="038fb-128">When you display your custom form for editing, you can pass a reference to the connection manager that is being edited.</span></span> <span data-ttu-id="038fb-129">您可以使用表單類別的自訂建構函式，或建立自己的 `Initialize` 方法 (如此處所示) 傳遞此參考。</span><span class="sxs-lookup"><span data-stu-id="038fb-129">You can pass this reference either by using a custom constructor for the form class, or by creating your own `Initialize` method as shown here.</span></span>  
  
```vb  
Public Sub Initialize(ByVal connectionManager As ConnectionManager, ByVal serviceProvider As IServiceProvider)  
  
  _connectionManager = connectionManager  
  _serviceProvider = serviceProvider  
  ConfigureControlsFromConnectionManager()  
  EnableControls()  
  
End Sub  
```  
  
```csharp  
public void Initialize(ConnectionManager connectionManager, IServiceProvider serviceProvider)  
 {  
  
   _connectionManager = connectionManager;  
   _serviceProvider = serviceProvider;  
   ConfigureControlsFromConnectionManager();  
   EnableControls();  
  
 }  
```  
  
### <a name="setting-properties-on-the-user-interface-form"></a><span data-ttu-id="038fb-130">設定使用者介面表單的屬性</span><span class="sxs-lookup"><span data-stu-id="038fb-130">Setting Properties on the User Interface Form</span></span>  
 <span data-ttu-id="038fb-131">最後，您的表單類別需要 Helper 函數，以便在初次以連接管理員的屬性現有值或預設值載入時，擴展表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="038fb-131">Finally, your form class needs a helper function that populates the controls on the form when it is first loaded with the existing or the default values of the properties of the connection manager.</span></span> <span data-ttu-id="038fb-132">您的表單類別也需要類似的函數，以便在使用者按一下 [確定] 並關閉表單時，將屬性值設定成使用者輸入的值。</span><span class="sxs-lookup"><span data-stu-id="038fb-132">Your form class also needs a similar function that sets the values of the properties to the values entered by the user when the user clicks OK and closes the form.</span></span>  
  
```vb  
Private Const CONNECTIONNAME_BASE As String = "SqlConnectionManager"  
  
Private Sub ConfigureControlsFromConnectionManager()  
  
  Dim tempName As String  
  Dim tempServerName As String  
  Dim tempDatabaseName As String  
  
  With _connectionManager  
  
    tempName = .Properties("Name").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempName) Then  
      _connectionName = tempName  
    Else  
      _connectionName = CONNECTIONNAME_BASE  
    End If  
  
    tempServerName = .Properties("ServerName").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempServerName) Then  
      _serverName = tempServerName  
      txtServerName.Text = _serverName  
    End If  
  
    tempDatabaseName = .Properties("DatabaseName").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempDatabaseName) Then  
      _databaseName = tempDatabaseName  
      txtDatabaseName.Text = _databaseName  
    End If  
  
  End With  
  
End Sub  
  
Private Sub ConfigureConnectionManagerFromControls()  
  
  With _connectionManager  
    .Properties("Name").SetValue(_connectionManager, _connectionName)  
    .Properties("ServerName").SetValue(_connectionManager, _serverName)  
    .Properties("DatabaseName").SetValue(_connectionManager, _databaseName)  
  End With  
  
End Sub  
```  
  
```csharp  
private const string CONNECTIONNAME_BASE = "SqlConnectionManager";  
  
private void ConfigureControlsFromConnectionManager()  
 {  
  
   string tempName;  
   string tempServerName;  
   string tempDatabaseName;  
  
   {  
     tempName = _connectionManager.Properties["Name"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempName))  
     {  
       _connectionName = tempName;  
     }  
     else  
     {  
       _connectionName = CONNECTIONNAME_BASE;  
     }  
  
     tempServerName = _connectionManager.Properties["ServerName"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempServerName))  
     {  
       _serverName = tempServerName;  
       txtServerName.Text = _serverName;  
     }  
  
     tempDatabaseName = _connectionManager.Properties["DatabaseName"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempDatabaseName))  
     {  
       _databaseName = tempDatabaseName;  
       txtDatabaseName.Text = _databaseName;  
     }  
  
   }  
  
 }  
  
 private void ConfigureConnectionManagerFromControls()  
 {  
  
   {  
     _connectionManager.Properties["Name"].SetValue(_connectionManager, _connectionName);  
     _connectionManager.Properties["ServerName"].SetValue(_connectionManager, _serverName);  
     _connectionManager.Properties["DatabaseName"].SetValue(_connectionManager, _databaseName);  
   }  
  
 }  
```  
  
<span data-ttu-id="038fb-133">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="038fb-133">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="038fb-134">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="038fb-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="038fb-135">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="038fb-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="038fb-136">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="038fb-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038fb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="038fb-137">See Also</span></span>  
 <span data-ttu-id="038fb-138">[建立自訂連線管理員](creating-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="038fb-138">[Creating a Custom Connection Manager](creating-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="038fb-139">撰寫自訂連接管理員的程式碼</span><span class="sxs-lookup"><span data-stu-id="038fb-139">Coding a Custom Connection Manager</span></span>](coding-a-custom-connection-manager.md)  
  
  
