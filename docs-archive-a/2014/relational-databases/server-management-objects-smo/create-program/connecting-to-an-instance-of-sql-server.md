---
title: 連接到 SQL Server 的實例 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, connections
- connections [SMO]
- instances of SQL Server, connections
- SMO [SQL Server], connections
ms.assetid: ad3cf354-b2e3-468b-b986-1232e375fd84
author: stevestein
ms.author: sstein
ms.openlocfilehash: efc21451f4a876c6edfe4a2389ca937d11bc5c8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606200"
---
# <a name="connecting-to-an-instance-of-sql-server"></a><span data-ttu-id="e055c-102">連接到 SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-102">Connecting to an Instance of SQL Server</span></span>
  <span data-ttu-id="e055c-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理物件 (SMO) 應用程式中的第一個程式設計步驟，是 <xref:Microsoft.SqlServer.Management.Smo.Server> 建立物件的實例，並建立其與實例的連接 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e055c-103">The first programming step in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) application is to create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and to establish its connection to an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e055c-104">您可以用三種方式建立 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件的執行個體，並建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="e055c-104">You can create an instance of the <xref:Microsoft.SqlServer.Management.Smo.Server> object and establish a connection to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in three ways.</span></span> <span data-ttu-id="e055c-105">第一種方式是，使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數來提供連接資訊。</span><span class="sxs-lookup"><span data-stu-id="e055c-105">The first is using a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable to provide the connection information.</span></span> <span data-ttu-id="e055c-106">第二種方式是，明確地設定 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件屬性來提供連接資訊。</span><span class="sxs-lookup"><span data-stu-id="e055c-106">The second is to provide the connection information by explicitly setting the <xref:Microsoft.SqlServer.Management.Smo.Server> object properties.</span></span> <span data-ttu-id="e055c-107">第三種方式是，在 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件建構函式中傳遞 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="e055c-107">The third is to pass the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span>  
  
 <span data-ttu-id="e055c-108">**使用 ServerConnection 物件**</span><span class="sxs-lookup"><span data-stu-id="e055c-108">**Using a ServerConnection object**</span></span>  
  
 <span data-ttu-id="e055c-109">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數的優點是，連接資訊可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="e055c-109">The advantage of using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable is that the connection information can be reused.</span></span> <span data-ttu-id="e055c-110">宣告 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件變數。</span><span class="sxs-lookup"><span data-stu-id="e055c-110">Declare a <xref:Microsoft.SqlServer.Management.Smo.Server> object variable.</span></span> <span data-ttu-id="e055c-111">接著，宣告 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件，並利用連接資訊 (例如，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱與驗證模式) 設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e055c-111">Then, declare a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object and set properties with connection information such as the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and the authentication mode.</span></span> <span data-ttu-id="e055c-112">然後，將 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數當做參數傳遞至物件的函式 <xref:Microsoft.SqlServer.Management.Smo.Server> 。</span><span class="sxs-lookup"><span data-stu-id="e055c-112">Then, pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable as a parameter to the <xref:Microsoft.SqlServer.Management.Smo.Server> object constructor.</span></span> <span data-ttu-id="e055c-113">不建議同時在不同的伺服器物件之間共用連接。</span><span class="sxs-lookup"><span data-stu-id="e055c-113">It is not recommended to share connections between different server objects at the same time.</span></span> <span data-ttu-id="e055c-114">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 方法來取得現有連接設定的複本。</span><span class="sxs-lookup"><span data-stu-id="e055c-114">Use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> method to get a copy of the existing connection settings.</span></span>  
  
 <span data-ttu-id="e055c-115">**明確地設定伺服器物件屬性**</span><span class="sxs-lookup"><span data-stu-id="e055c-115">**Setting Server object properties explicitly**</span></span>  
  
 <span data-ttu-id="e055c-116">或者，您可以宣告 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件變數，並呼叫預設的建構函式。</span><span class="sxs-lookup"><span data-stu-id="e055c-116">Alternatively, you can declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and call the default constructor.</span></span> <span data-ttu-id="e055c-117">同時，<xref:Microsoft.SqlServer.Management.Smo.Server> 物件會嘗試利用所有預設的連接設定，連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="e055c-117">As is, the <xref:Microsoft.SqlServer.Management.Smo.Server> object tries to connect to the default instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with all the default connection settings.</span></span>  
  
 <span data-ttu-id="e055c-118">**在 Server 物件建構函式中提供 SQL Server 執行個體名稱**</span><span class="sxs-lookup"><span data-stu-id="e055c-118">**Providing the SQL Server instance name in the Server object constructor**</span></span>  
  
 <span data-ttu-id="e055c-119">宣告 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件變數，然後傳遞 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體名稱，做為建構函式中的字串參數。</span><span class="sxs-lookup"><span data-stu-id="e055c-119">Declare the <xref:Microsoft.SqlServer.Management.Smo.Server> object variable and pass the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance name as a string parameter in the constructor.</span></span> <span data-ttu-id="e055c-120"><xref:Microsoft.SqlServer.Management.Smo.Server> 物件會利用包含預設連接設定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體建立連接。</span><span class="sxs-lookup"><span data-stu-id="e055c-120">The <xref:Microsoft.SqlServer.Management.Smo.Server> object establishes a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the default connection settings.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="e055c-121">連接共用</span><span class="sxs-lookup"><span data-stu-id="e055c-121">Connection Pooling</span></span>  
 <span data-ttu-id="e055c-122">通常不需要呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 物件的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 方法。</span><span class="sxs-lookup"><span data-stu-id="e055c-122">It is typically not required to call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span> <span data-ttu-id="e055c-123">SMO 將會在需要時，自動建立連接，並在執行作業完畢之後，將連接釋放到連接集區。</span><span class="sxs-lookup"><span data-stu-id="e055c-123">SMO will automatically establish a connection when required, and release the connection to the connection pool after it has finished performing operations.</span></span> <span data-ttu-id="e055c-124">呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法時，並不會將連接釋放到集區。</span><span class="sxs-lookup"><span data-stu-id="e055c-124">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not released to the pool.</span></span> <span data-ttu-id="e055c-125">若要將連接釋放到集區，必須明確地呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e055c-125">An explicit call to the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method is required to release the connection to the pool.</span></span> <span data-ttu-id="e055c-126">此外，您可以設定 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 物件的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 屬性來要求非集區的連接。</span><span class="sxs-lookup"><span data-stu-id="e055c-126">Additionally, you can request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="multithreaded-applications"></a><span data-ttu-id="e055c-127">多執行緒應用程式</span><span class="sxs-lookup"><span data-stu-id="e055c-127">Multithreaded Applications</span></span>  
 <span data-ttu-id="e055c-128">對於多執行緒應用程式，應該在每個執行緒中使用個別的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="e055c-128">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
## <a name="connecting-to-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="e055c-129">連接到 SQL Server for RMO 的執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-129">Connecting to an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="e055c-130">Replication Management Objects (RMO) 會使用與 SMO 稍微不同的方法來連接到複寫伺服器。</span><span class="sxs-lookup"><span data-stu-id="e055c-130">Replication Management Objects (RMO) uses a slightly different method from SMO to connect to a replication server.</span></span>  
  
 <span data-ttu-id="e055c-131">RMO 程式設計物件需要使用 `Microsoft.SqlServer.Management.Common` 命名空間實作的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件，來建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="e055c-131">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object implemented by the `Microsoft.SqlServer.Management.Common` namespace.</span></span> <span data-ttu-id="e055c-132">這個伺服器連接會獨立於 RMO 程式設計物件之外建立。</span><span class="sxs-lookup"><span data-stu-id="e055c-132">This connection to the server is made independently of an RMO programming object.</span></span> <span data-ttu-id="e055c-133">接著會在執行個體建立期間，或是將它指派到物件的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性，藉以將它傳遞到 RMO 物件。</span><span class="sxs-lookup"><span data-stu-id="e055c-133">It is then it is passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="e055c-134">以此方式，就可以個別建立和管理 RMO 程式設計物件與連接物件執行個體，而且多個 RMO 程式設計物件可以重複使用單一連接物件。</span><span class="sxs-lookup"><span data-stu-id="e055c-134">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="e055c-135">下列規則適用於應用程式伺服器的連接：</span><span class="sxs-lookup"><span data-stu-id="e055c-135">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="e055c-136">連接的所有屬性是針對指定的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件所定義。</span><span class="sxs-lookup"><span data-stu-id="e055c-136">All properties for the connection are defined for a specified <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="e055c-137">每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接都必須有它自己的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="e055c-137">Each connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="e055c-138">在 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件中，會提供所有建立連接及成功登入伺服器的驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="e055c-138">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="e055c-139">根據預設，連接都是使用「Microsoft Windows 驗證」所建立。</span><span class="sxs-lookup"><span data-stu-id="e055c-139">By default, connections are made by using Microsoft Windows Authentication.</span></span> <span data-ttu-id="e055c-140">若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證，必須將 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> 設定為 False 與 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A>，而且 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> 必須設定為有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入與密碼。</span><span class="sxs-lookup"><span data-stu-id="e055c-140">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to False and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="e055c-141">安全性認證必須以安全方式儲存和處理，而且每當有需要時必須在執行階段提供。</span><span class="sxs-lookup"><span data-stu-id="e055c-141">Security credentials must always be stored and handled securely, and supplied at run time whenever possible.</span></span>  
  
-   <span data-ttu-id="e055c-142">您必須明確地呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法，才能將連接傳遞到任何 RMO 程式設計物件。</span><span class="sxs-lookup"><span data-stu-id="e055c-142">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method must be called before passing the connection to any RMO programming object.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e055c-143">範例</span><span class="sxs-lookup"><span data-stu-id="e055c-143">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="e055c-144">在 Visual Basic 中使用 Windows 驗證連接到 SQL Server 的本機執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-144">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="e055c-145">連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本機執行個體不需要太多程式碼。</span><span class="sxs-lookup"><span data-stu-id="e055c-145">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="e055c-146">而是依賴驗證方法和伺服器的預設值。</span><span class="sxs-lookup"><span data-stu-id="e055c-146">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="e055c-147">需要擷取資料的第一個作業將會導致連接建立。</span><span class="sxs-lookup"><span data-stu-id="e055c-147">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="e055c-148">這個範例是 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 使用 Windows 驗證連接到本機實例的 .net 程式碼 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e055c-148">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB1](SMO How to#SMO_VB1)]  -->  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="e055c-149">在 Visual C# 中使用 Windows 驗證連接到 SQL Server 的本機執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-149">Connecting to the Local Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="e055c-150">連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本機執行個體不需要太多程式碼。</span><span class="sxs-lookup"><span data-stu-id="e055c-150">Connecting to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not require much code.</span></span> <span data-ttu-id="e055c-151">而是依賴驗證方法和伺服器的預設值。</span><span class="sxs-lookup"><span data-stu-id="e055c-151">Instead, it relies on default settings for authentication method and server.</span></span> <span data-ttu-id="e055c-152">需要擷取資料的第一個作業將會導致連接建立。</span><span class="sxs-lookup"><span data-stu-id="e055c-152">The first operation that requires data to be retrieved will cause a connection to be created.</span></span>  
  
 <span data-ttu-id="e055c-153">此範例為 Visual C# .NET 程式碼，會用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本機執行個體。</span><span class="sxs-lookup"><span data-stu-id="e055c-153">This example is Visual C# .NET code that connects to the local instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//The connection is established when a property is requested.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a><span data-ttu-id="e055c-154">在 Visual Basic 中使用 Windows 驗證連接到 SQL Server 的遠端執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-154">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual Basic</span></span>  
 <span data-ttu-id="e055c-155">當您使用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您不需要指定驗證類型。</span><span class="sxs-lookup"><span data-stu-id="e055c-155">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="e055c-156">Windows 驗證是預設值。</span><span class="sxs-lookup"><span data-stu-id="e055c-156">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="e055c-157">這個範例是 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 使用 Windows 驗證連接到遠端實例的 .net 程式碼 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e055c-157">This example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="e055c-158">字串變數*strServer*包含遠端實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="e055c-158">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB2](SMO How to#SMO_VB2)]  -->  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a><span data-ttu-id="e055c-159">在 Visual C# 中使用 Windows 驗證連接到 SQL Server 的遠端執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-159">Connecting to a Remote Instance of SQL Server by Using Windows Authentication in Visual C#</span></span>  
 <span data-ttu-id="e055c-160">當您使用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您不需要指定驗證類型。</span><span class="sxs-lookup"><span data-stu-id="e055c-160">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication, you do not have to specify the authentication type.</span></span> <span data-ttu-id="e055c-161">Windows 驗證是預設值。</span><span class="sxs-lookup"><span data-stu-id="e055c-161">Windows Authentication is the default.</span></span>  
  
 <span data-ttu-id="e055c-162">此範例為 Visual C# .NET 程式碼，會使用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的遠端執行個體。</span><span class="sxs-lookup"><span data-stu-id="e055c-162">This example is Visual C# .NET code that connects to the remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using Windows Authentication.</span></span> <span data-ttu-id="e055c-163">字串變數*strServer*包含遠端實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="e055c-163">The string variable *strServer* contains the name of the remote instance.</span></span>  
  
```  
{   
//Connect to a remote instance of SQL Server.   
Server srv;   
//The strServer string variable contains the name of a remote instance of SQL Server.   
srv = new Server(strServer);   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-basic"></a><span data-ttu-id="e055c-164">在 Visual Basic 中使用 SQL Server 驗證連接到 SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-164">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual Basic</span></span>  
 <span data-ttu-id="e055c-165">當您使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您必須指定驗證類型。</span><span class="sxs-lookup"><span data-stu-id="e055c-165">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="e055c-166">此範例示範宣告 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數的替代方法，讓連接資訊得以重複使用。</span><span class="sxs-lookup"><span data-stu-id="e055c-166">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="e055c-167">此範例為 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .net 程式碼，示範如何連接到遠端，而*vPassword*包含登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="e055c-167">The example is [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll  
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim sqlServerLogin As [String] = "user_id"  
      Dim password As [String] = "pwd"  
      Dim instanceName As [String] = "instance_name"  
      Dim remoteSvrName As [String] = "remote_server_name"  
  
      ' Connecting to an instance of SQL Server using SQL Server Authentication  
      Dim srv1 As New Server()   ' connects to default instance  
      srv1.ConnectionContext.LoginSecure = False   ' set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin  
      srv1.ConnectionContext.Password = password  
      Console.WriteLine(srv1.Information.Version)   ' connection is established  
  
      ' Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      Dim srvConn As New ServerConnection()  
      srvConn.ServerInstance = ".\" & instanceName   ' connects to named instance  
      srvConn.LoginSecure = False   ' set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin  
      srvConn.Password = password  
      Dim srv2 As New Server(srvConn)  
      Console.WriteLine(srv2.Information.Version)   ' connection is established  
  
      ' For remote connection, remote server name / ServerInstance needs to be specified  
      Dim srvConn2 As New ServerConnection(remoteSvrName)  
      srvConn2.LoginSecure = False  
      srvConn2.Login = sqlServerLogin  
      srvConn2.Password = password  
      Dim srv3 As New Server(srvConn2)  
      Console.WriteLine(srv3.Information.Version)   ' connection is established  
   End Sub  
End Class  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-c"></a><span data-ttu-id="e055c-168">在 Visual C# 中使用 SQL Server 驗證連接到 SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="e055c-168">Connecting to an Instance of SQL Server by Using SQL Server Authentication in Visual C#</span></span>  
 <span data-ttu-id="e055c-169">當您使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您必須指定驗證類型。</span><span class="sxs-lookup"><span data-stu-id="e055c-169">When you connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, you must specify the authentication type.</span></span> <span data-ttu-id="e055c-170">此範例示範宣告 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數的替代方法，讓連接資訊得以重複使用。</span><span class="sxs-lookup"><span data-stu-id="e055c-170">This example demonstrates the alternative method of declaring a <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object variable, which enables the connection information to be reused.</span></span>  
  
 <span data-ttu-id="e055c-171">此範例為 Visual c # .NET 程式碼，示範如何連接到遠端，而*vPassword*包含登入和密碼。</span><span class="sxs-lookup"><span data-stu-id="e055c-171">The example is Visual C# .NET code that demonstrates how to connect to the remote and *vPassword* contain the logon and password.</span></span>  
  
```  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll  
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {   
      String sqlServerLogin = "user_id";  
      String password = "pwd";  
      String instanceName = "instance_name";  
      String remoteSvrName = "remote_server_name";  
  
      // Connecting to an instance of SQL Server using SQL Server Authentication  
      Server srv1 = new Server();   // connects to default instance  
      srv1.ConnectionContext.LoginSecure = false;   // set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin;  
      srv1.ConnectionContext.Password = password;  
      Console.WriteLine(srv1.Information.Version);   // connection is established  
  
      // Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      ServerConnection srvConn = new ServerConnection();  
      srvConn.ServerInstance = @".\" + instanceName;   // connects to named instance  
      srvConn.LoginSecure = false;   // set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin;  
      srvConn.Password = password;  
      Server srv2 = new Server(srvConn);  
      Console.WriteLine(srv2.Information.Version);   // connection is established  
  
      // For remote connection, remote server name / ServerInstance needs to be specified  
      ServerConnection srvConn2 = new ServerConnection(remoteSvrName);  
      srvConn2.LoginSecure = false;  
      srvConn2.Login = sqlServerLogin;  
      srvConn2.Password = password;  
      Server srv3 = new Server(srvConn2);  
      Console.WriteLine(srv3.Information.Version);   // connection is established  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e055c-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e055c-172">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
