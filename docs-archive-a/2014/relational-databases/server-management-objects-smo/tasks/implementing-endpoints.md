---
title: 執行端點 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- endpoints [SMO]
ms.assetid: f8674dbb-9bc0-488f-9def-e9e0ce1ddf86
author: stevestein
ms.author: sstein
ms.openlocfilehash: 293a661c6e1ad6f6139e30e0824e99686af98f90
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707322"
---
# <a name="implementing-endpoints"></a><span data-ttu-id="75c82-102">實作端點</span><span class="sxs-lookup"><span data-stu-id="75c82-102">Implementing Endpoints</span></span>
  <span data-ttu-id="75c82-103">端點是可以透過原生方式接聽要求的服務。</span><span class="sxs-lookup"><span data-stu-id="75c82-103">An endpoint is a service that can listen natively for requests.</span></span> <span data-ttu-id="75c82-104">SMO 藉由使用 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 物件來支援各種端點類型。</span><span class="sxs-lookup"><span data-stu-id="75c82-104">SMO supports various types of endpoints by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object.</span></span> <span data-ttu-id="75c82-105">您可以藉由建立 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 物件的執行個體和設定其屬性，建立處理特定裝載類型的端點服務 (此類服務使用特定的通訊協定)。</span><span class="sxs-lookup"><span data-stu-id="75c82-105">You can create an endpoint service that handles a specific type of payload, which uses a specific protocol, by creating an instance of an <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object and setting its properties.</span></span>  
  
 <span data-ttu-id="75c82-106"><xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Endpoint> 屬性可用於指定下列其中一個裝載類型：</span><span class="sxs-lookup"><span data-stu-id="75c82-106">The <xref:Microsoft.SqlServer.Management.Smo.Endpoint.EndpointType%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Endpoint> object can be used to specify on of the following payload types:</span></span>  
  
-   <span data-ttu-id="75c82-107">資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="75c82-107">Database mirroring</span></span>  
  
-   <span data-ttu-id="75c82-108">SOAP ( [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 及更早的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本中存在 SOAP 端點的支援)</span><span class="sxs-lookup"><span data-stu-id="75c82-108">SOAP (support for SOAP endpoints is present in [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] and earlier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions)</span></span>  
  
-   <span data-ttu-id="75c82-109">Service Broker</span><span class="sxs-lookup"><span data-stu-id="75c82-109">Service Broker</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)]  
  
 <span data-ttu-id="75c82-110">此外，<xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 屬性也可用於指定下列兩種支援的通訊協定：</span><span class="sxs-lookup"><span data-stu-id="75c82-110">Also, the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property can be used to specify the following two supported protocols:</span></span>  
  
-   <span data-ttu-id="75c82-111">HTTP 通訊協定</span><span class="sxs-lookup"><span data-stu-id="75c82-111">HTTP protocol</span></span>  
  
-   <span data-ttu-id="75c82-112">TCP 通訊協定</span><span class="sxs-lookup"><span data-stu-id="75c82-112">TCP protocol</span></span>  
  
 <span data-ttu-id="75c82-113">在指定裝載類型之後，就可以使用 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> 物件屬性設定實際的裝載。</span><span class="sxs-lookup"><span data-stu-id="75c82-113">Having specified the type of payload, the actual payload can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Payload%2A> object property.</span></span> <span data-ttu-id="75c82-114"><xref:Microsoft.SqlServer.Management.Smo.Payload> 物件屬性針對可修改其屬性的指定類型，提供裝載物件的參考。</span><span class="sxs-lookup"><span data-stu-id="75c82-114">The <xref:Microsoft.SqlServer.Management.Smo.Payload> object property provides a reference to a payload object of the specified type, for which the properties can be modified.</span></span>  
  
 <span data-ttu-id="75c82-115">如果是 <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> 物件，則您必須指定鏡像角色以及是否啟用加密。</span><span class="sxs-lookup"><span data-stu-id="75c82-115">For the <xref:Microsoft.SqlServer.Management.Smo.DatabaseMirroringPayload> object, you must specify the mirroring role and whether encryption is enabled.</span></span> <span data-ttu-id="75c82-116"><xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> 物件需要訊息轉送、允許的最大連接數目以及驗證模式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75c82-116">The <xref:Microsoft.SqlServer.Management.Smo.ServiceBrokerPayload> object requires information about message forwarding, maximum number of connections allowed and the authentication mode.</span></span> <span data-ttu-id="75c82-117"><xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> 物件需要設定多個屬性，包括 <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> 物件屬性，此屬性會指定用戶端可用的 SOAP 裝載方法 (預存程序和使用者定義函數)。</span><span class="sxs-lookup"><span data-stu-id="75c82-117">The <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethod.%23ctor%2A> object requires various properties to be set including the <xref:Microsoft.SqlServer.Management.Smo.SoapPayloadMethodCollection.Add%2A> object property that specifies the SOAP payload methods available to clients (stored procedures and user-defined functions).</span></span>  
  
 <span data-ttu-id="75c82-118">同樣地，實際的通訊協定也可使用 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> 物件屬性來設定，此屬性會參考 <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> 屬性所指定類型的通訊協定物件。</span><span class="sxs-lookup"><span data-stu-id="75c82-118">Similarly, the actual protocol can be set by using the <xref:Microsoft.SqlServer.Management.Smo.Endpoint.Protocol%2A> object property that references a protocol object of the type specified by <xref:Microsoft.SqlServer.Management.Smo.Endpoint.ProtocolType%2A> property.</span></span> <span data-ttu-id="75c82-119"><xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> 物件需要受限 IP 位址的清單，以及通訊埠、網站和驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="75c82-119">The <xref:Microsoft.SqlServer.Management.Smo.HttpProtocol> object requires a list of restricted IP addresses, and port, website, and authentication information.</span></span> <span data-ttu-id="75c82-120"><xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> 物件也需要受限 IP 位址的清單和通訊埠資訊。</span><span class="sxs-lookup"><span data-stu-id="75c82-120">The <xref:Microsoft.SqlServer.Management.Smo.TcpProtocol> object also requires a list of restricted IP addresses and port information.</span></span>  
  
 <span data-ttu-id="75c82-121">在建立和完整地定義端點後，就可以對資料庫使用者、群組、角色和登入等授與、撤銷和拒絕存取權限。</span><span class="sxs-lookup"><span data-stu-id="75c82-121">When the endpoint has been created and fully defined, access can be granted to, revoked from, and denied to database users, groups, roles, and logons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75c82-122">範例</span><span class="sxs-lookup"><span data-stu-id="75c82-122">Example</span></span>  
 <span data-ttu-id="75c82-123">在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="75c82-123">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="75c82-124">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="75c82-124">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-basic"></a><span data-ttu-id="75c82-125">在 Visual Basic 中建立資料庫鏡像端點服務</span><span class="sxs-lookup"><span data-stu-id="75c82-125">Creating a Database Mirroring Endpoint Service in Visual Basic</span></span>  
 <span data-ttu-id="75c82-126">此程式碼範例示範如何在 SMO 中建立資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="75c82-126">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="75c82-127">您必須先進行這項作業，才能建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="75c82-127">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="75c82-128">請使用 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 物件上的 <xref:Microsoft.SqlServer.Management.Smo.Database> 和其他屬性建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="75c82-128">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBEndpoints1](SMO How to#SMO_VBEndpoints1)]  -->  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-visual-c"></a><span data-ttu-id="75c82-129">在 Visual C# 中建立資料庫鏡像端點服務</span><span class="sxs-lookup"><span data-stu-id="75c82-129">Creating a Database Mirroring Endpoint Service in Visual C#</span></span>  
 <span data-ttu-id="75c82-130">此程式碼範例示範如何在 SMO 中建立資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="75c82-130">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="75c82-131">您必須先進行這項作業，才能建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="75c82-131">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="75c82-132">請使用 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 物件上的 <xref:Microsoft.SqlServer.Management.Smo.Database> 和其他屬性建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="75c82-132">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```csharp
{  
            //Set up a database mirroring endpoint on the server before   
        //setting up a database mirror.   
        //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Define an Endpoint object variable for database mirroring.   
            Endpoint ep = default(Endpoint);  
            ep = new Endpoint(srv, "Mirroring_Endpoint");  
            ep.ProtocolType = ProtocolType.Tcp;  
            ep.EndpointType = EndpointType.DatabaseMirroring;  
            //Specify the protocol ports.   
            ep.Protocol.Http.SslPort = 5024;  
            ep.Protocol.Tcp.ListenerPort = 6666;  
            //Specify the role of the payload.   
            ep.Payload.DatabaseMirroring.ServerMirroringRole = ServerMirroringRole.All;  
            //Create the endpoint on the instance of SQL Server.   
            ep.Create();  
            //Start the endpoint.   
            ep.Start();  
            Console.WriteLine(ep.EndpointState);  
        }  
```  
  
## <a name="creating-a-database-mirroring-endpoint-service-in-powershell"></a><span data-ttu-id="75c82-133">在 PowerShell 中建立資料庫鏡像端點服務</span><span class="sxs-lookup"><span data-stu-id="75c82-133">Creating a Database Mirroring Endpoint Service in PowerShell</span></span>  
 <span data-ttu-id="75c82-134">此程式碼範例示範如何在 SMO 中建立資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="75c82-134">The code example demonstrates how to create a Database Mirroring endpoint in SMO.</span></span> <span data-ttu-id="75c82-135">您必須先進行這項作業，才能建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="75c82-135">This is necessary before you create a database mirror.</span></span> <span data-ttu-id="75c82-136">請使用 <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> 物件上的 <xref:Microsoft.SqlServer.Management.Smo.Database> 和其他屬性建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="75c82-136">Use the <xref:Microsoft.SqlServer.Management.Smo.Database.IsMirroringEnabled%2A> and other properties on the <xref:Microsoft.SqlServer.Management.Smo.Database> object to create a database mirror.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get a new endpoint to congure and add  
$ep = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Endpoint -argumentlist $srv,"Mirroring_Endpoint"  
  
#Set some properties  
$ep.ProtocolType = [Microsoft.SqlServer.Management.SMO.ProtocolType]::Tcp  
$ep.EndpointType = [Microsoft.SqlServer.Management.SMO.EndpointType]::DatabaseMirroring  
$ep.Protocol.Http.SslPort = 5024  
$ep.Protocol.Tcp.ListenerPort = 6666 #inline comment  
$ep.Payload.DatabaseMirroring.ServerMirroringRole = [Microsoft.SqlServer.Management.SMO.ServerMirroringRole]::All  
  
# Create the endpoint on the instance  
$ep.Create()  
  
# Start the endpoint  
$ep.Start()  
  
# Report its state  
$ep.EndpointState;  
```  
  
## <a name="see-also"></a><span data-ttu-id="75c82-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75c82-137">See Also</span></span>  
 [<span data-ttu-id="75c82-138">資料庫鏡像端點 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="75c82-138">The Database Mirroring Endpoint &#40;SQL Server&#41;</span></span>](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
