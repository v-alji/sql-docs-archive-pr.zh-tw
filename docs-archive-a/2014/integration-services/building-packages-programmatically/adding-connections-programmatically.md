---
title: 以程式設計方式新增連線 | Microsoft Docs
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
- connection managers [Integration Services], packages
- Integration Services packages, connections
- connections [Integration Services], packages
- SSIS packages, connections
- packages [Integration Services], connections
- intrinsic properties [Integration Services]
- SQL Server Integration Services packages, connections
- ConnectionManager class
- SSIS connection managers
- adding package connections
ms.assetid: d90716d1-4c65-466c-b82c-4aabbee1e3e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5952221dbf2689d2328695baf965ce884dc07fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594654"
---
# <a name="adding-connections-programmatically"></a><span data-ttu-id="ba977-102">以程式設計方式加入連接</span><span class="sxs-lookup"><span data-stu-id="ba977-102">Adding Connections Programmatically</span></span>
  <span data-ttu-id="ba977-103"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 類別代表外部資料來源的實體連接。</span><span class="sxs-lookup"><span data-stu-id="ba977-103">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class represents physical connections to external data sources.</span></span> <span data-ttu-id="ba977-104"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 類別會將連接的實作詳細資料與執行階段隔離。</span><span class="sxs-lookup"><span data-stu-id="ba977-104">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class isolates the implementation details of the connection from the runtime.</span></span> <span data-ttu-id="ba977-105">這可讓執行階段使用一致且可預測的方式與每個連接管理員互動。</span><span class="sxs-lookup"><span data-stu-id="ba977-105">This enables the runtime to interact with each connection manager in a consistent and predictable manner.</span></span> <span data-ttu-id="ba977-106">連接管理員包含一組所有連接共有的內建屬性，例如 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> 以及 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="ba977-106">Connection managers contain a set of stock properties that all connections have in common, such as the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ID%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>.</span></span> <span data-ttu-id="ba977-107">不過，<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> 屬性通常是唯一需要設定連接管理員的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba977-107">However, the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> properties are ordinarily the only properties required to configure a connection manager.</span></span> <span data-ttu-id="ba977-108">與其他程式設計範例不同的是，連接類別會公開像是 `Open` 或 `Connect` 等方法，以實體建立連至資料來源的連接，執行階段引擎則會在執行時管理封裝的所有連接。</span><span class="sxs-lookup"><span data-stu-id="ba977-108">Unlike other programming paradigms, where connection classes expose methods such as `Open` or `Connect` to physically establish a connection to the data source, the run-time engine manages all the connections for the package while it runs.</span></span>  
  
 <span data-ttu-id="ba977-109"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> 類別是一種已經加入該封裝的連接管理員集合，而且可供在執行階段使用。</span><span class="sxs-lookup"><span data-stu-id="ba977-109">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections> class is a collection of the connection managers that have been added to that package and are available for use at run time.</span></span> <span data-ttu-id="ba977-110">您可以使用集合的 <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> 方法，並提供指出連接管理員類型的字串，將更多的連接管理員加入集合。</span><span class="sxs-lookup"><span data-stu-id="ba977-110">You can add more connection managers to the collection by using the <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method of the collection, and supplying a string that indicates the connection manager type.</span></span> <span data-ttu-id="ba977-111"><xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> 方法會傳回加入封裝的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="ba977-111">The <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Add%2A> method returns the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> instance that was added to the package.</span></span>  
  
## <a name="intrinsic-properties"></a><span data-ttu-id="ba977-112">內建屬性</span><span class="sxs-lookup"><span data-stu-id="ba977-112">Intrinsic Properties</span></span>  
 <span data-ttu-id="ba977-113"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 類別會公開一組所有連接都共有的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba977-113">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class exposes a set of properties that are common to all connections.</span></span> <span data-ttu-id="ba977-114">然而，有時您需要存取特定連接類型特有的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba977-114">However, sometimes you need access to properties that are unique to the specific connection type.</span></span> <span data-ttu-id="ba977-115"><xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> 類別的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 集合提供這些屬性的存取權。</span><span class="sxs-lookup"><span data-stu-id="ba977-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Properties%2A> collection of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> class provides access to these properties.</span></span> <span data-ttu-id="ba977-116">可以使用索引子或是屬性名稱以及 **GetValue** 方法，從集合擷取屬性，並且會使用 **SetValue** 方法來設定值。</span><span class="sxs-lookup"><span data-stu-id="ba977-116">The properties can be retrieved from the collection using the indexer or the property name and the **GetValue** method, and the values are set using the **SetValue** method.</span></span> <span data-ttu-id="ba977-117">基礎連接物件屬性的屬性也可以透過取得物件的實際執行個體以及直接設定其屬性來設定。</span><span class="sxs-lookup"><span data-stu-id="ba977-117">The properties of the underlying connection object properties can also be set by acquiring an actual instance of the object and setting its properties directly.</span></span> <span data-ttu-id="ba977-118">若要取得基礎連接，請使用連接管埋員的 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ba977-118">To get the underlying connection, use the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.InnerObject%2A> property of the connection manager.</span></span> <span data-ttu-id="ba977-119">下列程式碼行顯示以 C# 撰寫的程式碼，將建立具有基礎類別 <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass> 的 ADO.NET 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-119">The following line of code shows a C# line that creates an ADO.NET connection manager that has the underlying class, <xref:Microsoft.SqlServer.Dts.Runtime.Wrapper.ConnectionManagerAdoNetClass>.</span></span>  
  
 `ConnectionManagerAdoNetClass cmado = cm.InnerObject as ConnectionManagerAdoNet;`  
  
 <span data-ttu-id="ba977-120">這會將 Managed 連接管理員物件轉換為它的基礎連接物件。</span><span class="sxs-lookup"><span data-stu-id="ba977-120">This casts the managed connection manager object to its underlying connection object.</span></span> <span data-ttu-id="ba977-121">如果您是使用 C++，會呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 物件的 `QueryInterface` 方法，而且會要求基礎連接物件的介面。</span><span class="sxs-lookup"><span data-stu-id="ba977-121">If you are using C++, the `QueryInterface` method of the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> object is called and the interface of the underlying connection object is requested.</span></span>  
  
 <span data-ttu-id="ba977-122">下表列出包含在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-122">The following table lists the connection managers included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="ba977-123">以及用在 `package.Connections.Add("xxx")` 陳述式中的字串。</span><span class="sxs-lookup"><span data-stu-id="ba977-123">and the string that is used in the `package.Connections.Add("xxx")` statement.</span></span> <span data-ttu-id="ba977-124">如需所有連線管理員的清單，請參閱 [Integration Services &#40;SSIS&#41; 連線](../connection-manager/integration-services-ssis-connections.md)。</span><span class="sxs-lookup"><span data-stu-id="ba977-124">For a list of all connection managers, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
|<span data-ttu-id="ba977-125">String</span><span class="sxs-lookup"><span data-stu-id="ba977-125">String</span></span>|<span data-ttu-id="ba977-126">[ODBC 來源編輯器]</span><span class="sxs-lookup"><span data-stu-id="ba977-126">Connection manager</span></span>|  
|------------|------------------------|  
|<span data-ttu-id="ba977-127">"OLEDB"</span><span class="sxs-lookup"><span data-stu-id="ba977-127">"OLEDB"</span></span>|<span data-ttu-id="ba977-128">OLE DB 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-128">Connection manager for OLE DB connections.</span></span>|  
|<span data-ttu-id="ba977-129">"ODBC"</span><span class="sxs-lookup"><span data-stu-id="ba977-129">"ODBC"</span></span>|<span data-ttu-id="ba977-130">ODBC 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-130">Connection manager for ODBC connections.</span></span>|  
|<span data-ttu-id="ba977-131">"ADO"</span><span class="sxs-lookup"><span data-stu-id="ba977-131">"ADO"</span></span>|<span data-ttu-id="ba977-132">ADO 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-132">Connection manager for ADO connections.</span></span>|  
|<span data-ttu-id="ba977-133">"ADO.NET:SQL"</span><span class="sxs-lookup"><span data-stu-id="ba977-133">"ADO.NET:SQL"</span></span>|<span data-ttu-id="ba977-134">ADO.NET (SQL 資料提供者) 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-134">Connection manager for ADO.NET (SQL data provider) connections.</span></span>|  
|<span data-ttu-id="ba977-135">"ADO.NET:OLEDB"</span><span class="sxs-lookup"><span data-stu-id="ba977-135">"ADO.NET:OLEDB"</span></span>|<span data-ttu-id="ba977-136">ADO.NET (OLE DB 資料提供者) 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-136">Connection manager for ADO.NET (OLE DB data provider) connections.</span></span>|  
|<span data-ttu-id="ba977-137">"FLATFILE"</span><span class="sxs-lookup"><span data-stu-id="ba977-137">"FLATFILE"</span></span>|<span data-ttu-id="ba977-138">一般檔案連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-138">Connection manager for flat file connections.</span></span>|  
|<span data-ttu-id="ba977-139">"FILE"</span><span class="sxs-lookup"><span data-stu-id="ba977-139">"FILE"</span></span>|<span data-ttu-id="ba977-140">檔案連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-140">Connection manager for file connections.</span></span>|  
|<span data-ttu-id="ba977-141">"MULTIFLATFILE"</span><span class="sxs-lookup"><span data-stu-id="ba977-141">"MULTIFLATFILE"</span></span>|<span data-ttu-id="ba977-142">多個一般檔案連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-142">Connection manager for multiple flat file connections.</span></span>|  
|<span data-ttu-id="ba977-143">"MULTIFILE"</span><span class="sxs-lookup"><span data-stu-id="ba977-143">"MULTIFILE"</span></span>|<span data-ttu-id="ba977-144">多個一般檔案連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-144">Connection manager for multiple file connections.</span></span>|  
|<span data-ttu-id="ba977-145">"SQLMOBILE"</span><span class="sxs-lookup"><span data-stu-id="ba977-145">"SQLMOBILE"</span></span>|<span data-ttu-id="ba977-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact 連線的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-146">Connection manager for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact connections.</span></span>|  
|<span data-ttu-id="ba977-147">"MSOLAP100"</span><span class="sxs-lookup"><span data-stu-id="ba977-147">"MSOLAP100"</span></span>|<span data-ttu-id="ba977-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-148">Connection manager for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connections.</span></span>|  
|<span data-ttu-id="ba977-149">"FTP"</span><span class="sxs-lookup"><span data-stu-id="ba977-149">"FTP"</span></span>|<span data-ttu-id="ba977-150">FTP 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-150">Connection manager for FTP connections.</span></span>|  
|<span data-ttu-id="ba977-151">"HTTP"</span><span class="sxs-lookup"><span data-stu-id="ba977-151">"HTTP"</span></span>|<span data-ttu-id="ba977-152">HTTP 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-152">Connection manager for HTTP connections.</span></span>|  
|<span data-ttu-id="ba977-153">"MSMQ"</span><span class="sxs-lookup"><span data-stu-id="ba977-153">"MSMQ"</span></span>|<span data-ttu-id="ba977-154">Message Queuing (又稱為 MSMQ) 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-154">Connection manager for Message Queuing (also known as MSMQ) connections.</span></span>|  
|<span data-ttu-id="ba977-155">"SMTP"</span><span class="sxs-lookup"><span data-stu-id="ba977-155">"SMTP"</span></span>|<span data-ttu-id="ba977-156">SMTP 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-156">Connection manager for SMTP connections.</span></span>|  
|<span data-ttu-id="ba977-157">"WMI"</span><span class="sxs-lookup"><span data-stu-id="ba977-157">"WMI"</span></span>|<span data-ttu-id="ba977-158">Microsoft Windows Management Instrumentation (WMI) 連接的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ba977-158">Connection manager for Microsoft Windows Management Instrumentation (WMI) connections.</span></span>|  
  
 <span data-ttu-id="ba977-159">下列程式碼範例示範將 OLE DB 與 FILE 連接加入 <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> 的 <xref:Microsoft.SqlServer.Dts.Runtime.Package> 集合。</span><span class="sxs-lookup"><span data-stu-id="ba977-159">The following code example demonstrates adding an OLE DB and FILE connection to the <xref:Microsoft.SqlServer.Dts.Runtime.Package.Connections%2A> collection of a <xref:Microsoft.SqlServer.Dts.Runtime.Package>.</span></span> <span data-ttu-id="ba977-160">範例接著會設定 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A> 與 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ba977-160">The example then sets the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.ConnectionString%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Name%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.Description%2A> properties.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      // Create a package, and retrieve its connections.  
      Package pkg = new Package();  
      Connections pkgConns = pkg.Connections;  
  
      // Add an OLE DB connection to the package, using the   
      // method defined in the AddConnection class.  
      CreateConnection myOLEDBConn = new CreateConnection();  
      myOLEDBConn.CreateOLEDBConnection(pkg);  
  
      // View the new connection in the package.  
      Console.WriteLine("Connection description: {0}",  
         pkg.Connections["SSIS Connection Manager for OLE DB"].Description);  
  
      // Add a second connection to the package.  
      CreateConnection myFileConn = new CreateConnection();  
      myFileConn.CreateFileConnection(pkg);  
  
      // View the second connection in the package.  
      Console.WriteLine("Connection description: {0}",  
        pkg.Connections["SSIS Connection Manager for Files"].Description);  
  
      Console.WriteLine();  
      Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count);  
  
      Console.Read();  
    }  
  }  
  // <summary>  
  // This class contains the definitions for multiple  
  // connection managers.  
  // </summary>  
  public class CreateConnection  
  {  
    // Private data.  
    private ConnectionManager ConMgr;  
  
    // Class definition for OLE DB Provider.  
    public void CreateOLEDBConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("OLEDB");  
      ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" +  
        "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" +  
        "Data Source=(local);";  
      ConMgr.Name = "SSIS Connection Manager for OLE DB";  
      ConMgr.Description = "OLE DB connection to the AdventureWorks database.";  
    }  
    public void CreateFileConnection(Package p)  
    {  
      ConMgr = p.Connections.Add("File");  
      ConMgr.ConnectionString = @"\\<yourserver>\<yourfolder>\books.xml";  
      ConMgr.Name = "SSIS Connection Manager for Files";  
      ConMgr.Description = "Flat File connection";  
    }  
  }  
  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    ' Create a package, and retrieve its connections.  
    Dim pkg As New Package()  
    Dim pkgConns As Connections = pkg.Connections  
  
    ' Add an OLE DB connection to the package, using the   
    ' method defined in the AddConnection class.  
    Dim myOLEDBConn As New CreateConnection()  
    myOLEDBConn.CreateOLEDBConnection(pkg)  
  
    ' View the new connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for OLE DB").Description)  
  
    ' Add a second connection to the package.  
    Dim myFileConn As New CreateConnection()  
    myFileConn.CreateFileConnection(pkg)  
  
    ' View the second connection in the package.  
    Console.WriteLine("Connection description: {0}", _  
      pkg.Connections("SSIS Connection Manager for Files").Description)  
  
    Console.WriteLine()  
    Console.WriteLine("Number of connections in package: {0}", pkg.Connections.Count)  
  
    Console.Read()  
  
  End Sub  
  
End Module  
  
' This class contains the definitions for multiple  
' connection managers.  
  
Public Class CreateConnection  
  ' Private data.  
  Private ConMgr As ConnectionManager  
  
  ' Class definition for OLE DB provider.  
  Public Sub CreateOLEDBConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("OLEDB")  
    ConMgr.ConnectionString = "Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;Initial Catalog=AdventureWorks;" & _  
      "Data Source=(local);"  
    ConMgr.Name = "SSIS Connection Manager for OLE DB"  
    ConMgr.Description = "OLE DB connection to the AdventureWorks database."  
  End Sub  
  
  Public Sub CreateFileConnection(ByVal p As Package)  
    ConMgr = p.Connections.Add("File")  
    ConMgr.ConnectionString = "\\<yourserver>\<yourfolder>\books.xml"  
    ConMgr.Name = "SSIS Connection Manager for Files"  
    ConMgr.Description = "Flat File connection"  
  End Sub  
  
End Class  
```  
  
 <span data-ttu-id="ba977-161">**範例輸出：**</span><span class="sxs-lookup"><span data-stu-id="ba977-161">**Sample Output:**</span></span>  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Connection description: OLE DB connection to the AdventureWorks database.`  
  
 `Number of connections in package: 2`  
  
## <a name="external-resources"></a><span data-ttu-id="ba977-162">外部資源</span><span class="sxs-lookup"><span data-stu-id="ba977-162">External Resources</span></span>  
 <span data-ttu-id="ba977-163">carlprothman.net 上的技術文章：[連接字串](https://go.microsoft.com/fwlink/?LinkId=220743)。</span><span class="sxs-lookup"><span data-stu-id="ba977-163">Technical article, [Connection Strings](https://go.microsoft.com/fwlink/?LinkId=220743), on carlprothman.net.</span></span>  
  
<span data-ttu-id="ba977-164">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="ba977-164">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="ba977-165">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="ba977-165">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="ba977-166">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="ba977-166">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="ba977-167">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="ba977-167">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba977-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba977-168">See Also</span></span>  
 <span data-ttu-id="ba977-169">[Integration Services &#40;SSIS&#41; 連接](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="ba977-169">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="ba977-170">建立連接管理員</span><span class="sxs-lookup"><span data-stu-id="ba977-170">Create Connection Managers</span></span>](../create-connection-managers.md)  
  
  
