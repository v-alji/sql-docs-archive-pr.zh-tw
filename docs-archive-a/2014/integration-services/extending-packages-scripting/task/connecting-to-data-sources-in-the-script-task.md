---
title: 連接至指令碼工作中的資料來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c8374271c7972498361a83e4bbe87ad12265827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700051"
---
# <a name="connecting-to-data-sources-in-the-script-task"></a><span data-ttu-id="49afc-102">連接至指令碼工作中的資料來源</span><span class="sxs-lookup"><span data-stu-id="49afc-102">Connecting to Data Sources in the Script Task</span></span>
  <span data-ttu-id="49afc-103">連接管理員會提供已在封裝中設定的資料來源存取權。</span><span class="sxs-lookup"><span data-stu-id="49afc-103">Connection managers provide access to data sources that have been configured in the package.</span></span> <span data-ttu-id="49afc-104">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](../../connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="49afc-104">For more information, see [Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
 <span data-ttu-id="49afc-105">指令碼工作可以透過 **Dts** 物件的 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 屬性來存取這些連線管理員。</span><span class="sxs-lookup"><span data-stu-id="49afc-105">The Script task can access these connection managers through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property of the **Dts** object.</span></span> <span data-ttu-id="49afc-106">在 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 集合中的每個連接管理員儲存有關如何連接至基礎資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="49afc-106">Each connection manager in the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection stores information about how to connect to the underlying data source.</span></span>  
  
 <span data-ttu-id="49afc-107">當您呼叫連接管理員的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> 方法時，如果連接管理員尚未連接，連接管理員會連接至資料來源，並傳回適當的連接或是連接資訊，供您在指令碼工作程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="49afc-107">When you call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of a connection manager, the connection manager connects to the data source, if it is not already connected, and returns the appropriate connection or connection information for you to use in your Script task code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49afc-108">您必須知道連接管理員傳回的連接類型，才能呼叫 `AcquireConnection`。</span><span class="sxs-lookup"><span data-stu-id="49afc-108">You must know the type of connection returned by the connection manager before calling `AcquireConnection`.</span></span> <span data-ttu-id="49afc-109">因為指令碼工作已啟用 `Option Strict`，所以您必須將以 `Object` 類型傳回的連接，轉換為適當的連接類型，才能使用它。</span><span class="sxs-lookup"><span data-stu-id="49afc-109">Because the Script task has `Option Strict` enabled, you must cast the connection, which is returned as type `Object`, to the appropriate connection type before you can use it.</span></span>  
  
 <span data-ttu-id="49afc-110">您可以在程式碼中使用連接之前，先透過 <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> 屬性傳回的 <xref:Microsoft.SqlServer.Dts.Runtime.Connections> 集合之 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> 方法，尋找現有的連接。</span><span class="sxs-lookup"><span data-stu-id="49afc-110">You can use the <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection returned by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property to look for an existing connection before using the connection in your code.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="49afc-111">在指令碼工作的 Managed 程式碼中，無法呼叫傳回 Unmanaged 物件之連線管理員的 AcquireConnection 方法，例如 OLE DB 連線管理員與 Excel 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="49afc-111">You cannot call the AcquireConnection method of connection managers that return unmanaged objects, such as the OLE DB connection manager and the Excel connection manager, in the managed code of a Script task.</span></span> <span data-ttu-id="49afc-112">不過，您可以讀取這些連接管理員的 ConnectionString 屬性，並直接在程式碼中連接到資料來源，方法是使用的連接字串搭配 `OledbConnection` **system.web**命名空間中的。</span><span class="sxs-lookup"><span data-stu-id="49afc-112">However, you can read the ConnectionString property of these connection managers, and connect to the data source directly in your code by using the connection string with an `OledbConnection` from the **System.Data.OleDb** namespace.</span></span>  
>   
>  <span data-ttu-id="49afc-113">如果您必須呼叫會傳回 Unmanaged 物件之連線管理員的 AcquireConnection 方法，請使用 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="49afc-113">If you must call the AcquireConnection method of a connection manager that returns an unmanaged object, use an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager.</span></span> <span data-ttu-id="49afc-114">當您設定 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 連接管理員以使用 OLE DB 提供者時，它會透過使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB 來連接。</span><span class="sxs-lookup"><span data-stu-id="49afc-114">When you configure the [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager to use an OLE DB provider, it connects by using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB.</span></span> <span data-ttu-id="49afc-115">在此情況下，AcquireConnection 方法會傳回， `System.Data.OleDb.OleDbConnection` 而不是非受控物件。</span><span class="sxs-lookup"><span data-stu-id="49afc-115">In this case, the AcquireConnection method returns a `System.Data.OleDb.OleDbConnection` instead of an unmanaged object.</span></span> <span data-ttu-id="49afc-116">若要將 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 連線管理員設定成與 Excel 資料來源搭配使用，請選取 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Jet，指定 Excel 檔案，然後在 [連線管理員] 對話方塊的 [全部] 頁面上輸入 `Excel 8.0` (針對 Excel 97 和更新的版本)，作為 [擴充屬性] 的值。</span><span class="sxs-lookup"><span data-stu-id="49afc-116">To configure an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager for use with an Excel data source, select the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Jet, specify an Excel file, and enter `Excel 8.0` (for Excel 97 and later) as the value of **Extended Properties** on the **All** page of the **Connection Manager** dialog box.</span></span>  
  
## <a name="connections-example"></a><span data-ttu-id="49afc-117">連接範例</span><span class="sxs-lookup"><span data-stu-id="49afc-117">Connections Example</span></span>  
 <span data-ttu-id="49afc-118">在下列程式碼範例中，示範如何從指令碼工作存取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="49afc-118">The following example demonstrates how to access connection managers from within the Script task.</span></span> <span data-ttu-id="49afc-119">範例假設您已建立和設定名為 **Test ADO.NET Connection** 的 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 連接管理員，以及名為 **Test Flat File Connection** 的一般檔案連線管理員。</span><span class="sxs-lookup"><span data-stu-id="49afc-119">The sample assumes that you have created and configured an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager named **Test ADO.NET Connection** and a Flat File connection manager named **Test Flat File Connection**.</span></span> <span data-ttu-id="49afc-120">請注意，[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 連接管理員會傳回您可立即用以連接至資料來源的 `SqlConnection` 物件。</span><span class="sxs-lookup"><span data-stu-id="49afc-120">Note that the [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager returns a `SqlConnection` object that you can use immediately to connect to the data source.</span></span> <span data-ttu-id="49afc-121">另一方面，一般檔案連接管理員只會傳回包含路徑與檔案名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="49afc-121">The Flat File connection manager, on the other hand, returns only a string that contains the path and file name.</span></span> <span data-ttu-id="49afc-122">您必須使用 `System.IO` 命名空間的方法，以開啟和處理一般檔案。</span><span class="sxs-lookup"><span data-stu-id="49afc-122">You must use methods from the `System.IO` namespace to open and work with the flat file.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
<span data-ttu-id="49afc-123">![Integration Services 圖示 (小型) ](../../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="49afc-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="49afc-124">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="49afc-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="49afc-125">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="49afc-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="49afc-126">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="49afc-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49afc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49afc-127">See Also</span></span>  
 <span data-ttu-id="49afc-128">[Integration Services &#40;SSIS&#41; 連接](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="49afc-128">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="49afc-129">建立連接管理員</span><span class="sxs-lookup"><span data-stu-id="49afc-129">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
