---
title: 連接到指令碼元件中的資料來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], connecting to data sources
ms.assetid: 96de63ab-ff48-4e7e-89e0-ffd6a89c63b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9272f946abb68a1c54cd6f4851806ec6a1b15de7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597215"
---
# <a name="connecting-to-data-sources-in-the-script-component"></a><span data-ttu-id="0d0a6-102">連接到指令碼元件中的資料來源</span><span class="sxs-lookup"><span data-stu-id="0d0a6-102">Connecting to Data Sources in the Script Component</span></span>
  <span data-ttu-id="0d0a6-103">連接管理員只是一種便利的單位，用以封裝和儲存連接至特定類型的資料來源所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-103">A connection manager is a convenient unit that encapsulates and stores the information that is required to connect to a data source of a particular type.</span></span> <span data-ttu-id="0d0a6-104">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](../../connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-104">For more information, see [Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
 <span data-ttu-id="0d0a6-105">您可以在 [指令碼轉換編輯器] 的 [連線管理員] 頁面上，按一下 [加入] 與 [移除] 按鈕，讓來源或目的地元件中的自訂指令碼可以存取現有的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-105">You can make existing connection managers available for access by the custom script in the source or destination component by clicking the **Add** and **Remove** buttons on the **Connection Managers** page of the **Script Transformation Editor**.</span></span> <span data-ttu-id="0d0a6-106">不過，您必須撰寫自己的自訂程式碼，以載入或是儲存資料，以及 (可能的話) 開啟和關閉連至資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-106">However, you must write your own custom code to load or save your data, and possibly to open and close the connection to the data source.</span></span> <span data-ttu-id="0d0a6-107">如需 [指令碼轉換編輯器] 之 [連線管理員] 頁面的詳細資訊，請參閱[在指令碼元件編輯器中設定指令碼元件](configuring-the-script-component-in-the-script-component-editor.md)和[指令碼轉換編輯器 &#40;連線管理員頁面&#41;](../../script-transformation-editor-connection-managers-page.md)。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-107">For more information about the **Connection Managers** page of the **Script Transformation Editor**, see [Configuring the Script Component in the Script Component Editor](configuring-the-script-component-in-the-script-component-editor.md) and [Script Transformation Editor &#40;Connection Managers Page&#41;](../../script-transformation-editor-connection-managers-page.md).</span></span>  
  
 <span data-ttu-id="0d0a6-108">指令碼元件會建立 `Connections` 專案項目中的 `ComponentWrapper` 集合類別，它含有每個連接管理員之強式類型存取子，具有與連接管理員本身相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-108">The Script component creates a `Connections` collection class in the `ComponentWrapper` project item that contains a strongly-typed accessor for each connection manager that has the same name as the connection manager itself.</span></span> <span data-ttu-id="0d0a6-109">此集合是透過 `Connections` 類別的 `ScriptMain` 屬性來公開。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-109">This collection is exposed through the `Connections` property of the `ScriptMain` class.</span></span> <span data-ttu-id="0d0a6-110">存取子屬性會傳回連接管理員的參考，以做為 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-110">The accessor property returns a reference to the connection manager as an instance of <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.IDTSConnectionManager100>.</span></span> <span data-ttu-id="0d0a6-111">例如，如果您已在對話方塊的 [連接管理員] 頁面中加入名為 `MyADONETConnection` 的連接管理員，就可以加入下列程式碼，取得指令碼中該連接管理員的參考：</span><span class="sxs-lookup"><span data-stu-id="0d0a6-111">For example, if you have added a connection manager named `MyADONETConnection` on the Connection Managers page of the dialog box, you can obtain a reference to it in your script by adding the following code:</span></span>  
  
 `Dim myADONETConnectionManager As IDTSConnectionManager100 = _`  
  
 `Me.Connections.MyADONETConnection`  
  
> [!NOTE]  
>  <span data-ttu-id="0d0a6-112">您必須知道連接管理員傳回的連接類型，才能呼叫 `AcquireConnection`。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-112">You must know the type of connection that is returned by the connection manager before you call `AcquireConnection`.</span></span> <span data-ttu-id="0d0a6-113">因為指令碼工作已啟用 `Option Strict`，所以您必須將以 `Object` 類型傳回的連接，轉換為適當的連接類型，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-113">Because the Script task has `Option Strict` enabled, you must cast the connection, which is returned as type `Object`, to the appropriate connection type before you can use it.</span></span>  
  
 <span data-ttu-id="0d0a6-114">接下來，您呼叫特定連接管理員的 `AcquireConnection` 方法，以取得基礎連接或是連接至資料來源所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-114">Next, you call the `AcquireConnection` method of the specific connection manager to obtain either the underlying connection or the information that is required to connect to the data source.</span></span> <span data-ttu-id="0d0a6-115">例如，您透過使用下列程式碼取得 ADO.NET 連線管理員所包裝的 **System.Data.SqlConnection** 之參考：</span><span class="sxs-lookup"><span data-stu-id="0d0a6-115">For example, you obtain a reference to the **System.Data.SqlConnection** wrapped by an ADO.NET connection manager by using the following code:</span></span>  
  
 `Dim myADOConnection As SqlConnection = _`  
  
 `CType(MyADONETConnectionManager.AcquireConnection(Nothing), SqlConnection)`  
  
 <span data-ttu-id="0d0a6-116">相反的，對於一般檔案連接管理員的相同呼叫，只會傳回檔案資料來源的路徑與檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-116">In contrast, the same call to a flat file connection manager returns only the path and file name of the file data source.</span></span>  
  
 `Dim myFlatFile As String = _`  
  
 `CType(MyFlatFileConnectionManager.AcquireConnection(Nothing), String)`  
  
 <span data-ttu-id="0d0a6-117">然後您必須將此路徑和檔案名稱提供給 `System.IO.StreamReader` 或 `Streamwriter`，才可在一般檔案中讀取或寫入資料。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-117">You then must provide this path and file name to a `System.IO.StreamReader` or `Streamwriter` to read or write the data in the flat file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0d0a6-118">當您在指令碼元件中撰寫 Managed 程式碼時，無法呼叫傳回 Unmanaged 物件之連線管理員的 AcquireConnection 方法，例如 OLE DB 連線管理員與 Excel 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-118">When you write managed code in a Script component, you cannot call the AcquireConnection method of connection managers that return unmanaged objects, such as the OLE DB connection manager and the Excel connection manager.</span></span> <span data-ttu-id="0d0a6-119">不過，您可以讀取這些連線管理員的 ConnectionString 屬性，而且可以透過使用來自 **System.Data.OleDb** 命名空間的 OLEDB **連接**之連接字串，直接在程式碼中連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-119">However, you can read the ConnectionString property of these connection managers, and connect to the data source directly in your code by using the connection string of an OLEDB **connection** from the **System.Data.OleDb** namespace.</span></span>  
>   
>  <span data-ttu-id="0d0a6-120">如果您需要呼叫會傳回 Unmanaged 物件之連線管理員的 AcquireConnection 方法，請使用 ADO.NET 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-120">If you need to call the AcquireConnection method of a connection manager that returns an unmanaged object, use an ADO.NET connection manager.</span></span> <span data-ttu-id="0d0a6-121">當您設定 ADO.NET 連接管理員以使用 OLE DB 提供者時，它會透過使用 .NET Framework Data Provider for OLE DB 來連接。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-121">When you configure the ADO.NET connection manager to use an OLE DB provider, it connects by using the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="0d0a6-122">在此情況下，AcquireConnection 方法會傳回， `System.Data.OleDb.OleDbConnection` 而不是非受控物件。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-122">In this case, the AcquireConnection method returns a `System.Data.OleDb.OleDbConnection` instead of an unmanaged object.</span></span> <span data-ttu-id="0d0a6-123">若要將 ADO.NET 連線管理員設定成與 Excel 資料來源搭配使用，請選取 Microsoft OLE DB Provider for Jet，指定 Excel 活頁簿，然後在 [連線管理員] 對話方塊的 [全部] 頁面上輸入 `Excel 8.0` (針對 Excel 97 和更新的版本)，作為 [擴充屬性] 的值。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-123">To configure an ADO.NET connection manager for use with an Excel data source, select the Microsoft OLE DB Provider for Jet, specify an Excel workbook, and then enter `Excel 8.0` (for Excel 97 and later) as the value of **Extended Properties** on the **All** page of the **Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="0d0a6-124">如需如何透過指令碼元件使用連線管理員的詳細資訊，請參閱[以指令碼元件建立來源](../../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)和[以指令碼元件建立目的地](../../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-124">For more information about how to use connection managers with the script component, see [Creating a Source with the Script Component](../../extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md) and [Creating a Destination with the Script Component](../../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span>  
  
<span data-ttu-id="0d0a6-125">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="0d0a6-125">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="0d0a6-126">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="0d0a6-126">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="0d0a6-127">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="0d0a6-127">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="0d0a6-128">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="0d0a6-128">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0a6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d0a6-129">See Also</span></span>  
 <span data-ttu-id="0d0a6-130">[Integration Services &#40;SSIS&#41; 連接](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="0d0a6-130">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="0d0a6-131">建立連接管理員</span><span class="sxs-lookup"><span data-stu-id="0d0a6-131">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
