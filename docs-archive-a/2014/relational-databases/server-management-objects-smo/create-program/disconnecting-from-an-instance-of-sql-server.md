---
title: 中斷與 SQL Server 實例的連線 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3514fce8fb8f1ccc8bd1b54acfa27825eaebbd34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606198"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a><span data-ttu-id="6958c-102">從 SQL Server 的執行個體中斷連接</span><span class="sxs-lookup"><span data-stu-id="6958c-102">Disconnecting from an Instance of SQL Server</span></span>
  <span data-ttu-id="6958c-103">您並不需要以手動方式關閉和中斷 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 物件的連接。</span><span class="sxs-lookup"><span data-stu-id="6958c-103">Manually closing and disconnecting [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) objects is not required.</span></span> <span data-ttu-id="6958c-104">連接會視需要開啟和關閉。</span><span class="sxs-lookup"><span data-stu-id="6958c-104">Connections are opened and closed as required.</span></span>  
  
## <a name="connection-pooling"></a><span data-ttu-id="6958c-105">連接共用</span><span class="sxs-lookup"><span data-stu-id="6958c-105">Connection Pooling</span></span>  
 <span data-ttu-id="6958c-106">呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法時，並不會自動釋放連接。</span><span class="sxs-lookup"><span data-stu-id="6958c-106">When the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method is called, the connection is not automatically released.</span></span> <span data-ttu-id="6958c-107">您必須明確地呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 方法，才能釋放對連接集區的連接。</span><span class="sxs-lookup"><span data-stu-id="6958c-107">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method must be called explicitly to release the connection to the connection pool.</span></span> <span data-ttu-id="6958c-108">此外，您也可以要求非共用連接。</span><span class="sxs-lookup"><span data-stu-id="6958c-108">Also, you can request a non-pooled connection.</span></span> <span data-ttu-id="6958c-109">執行此作業的方法是設定 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 屬性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 屬性，該屬性會參考 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="6958c-109">You do this by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> property that references the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a><span data-ttu-id="6958c-110">從 RMO 的 SQL Server 執行個體中斷連接</span><span class="sxs-lookup"><span data-stu-id="6958c-110">Disconnecting from an Instance of SQL Server for RMO</span></span>  
 <span data-ttu-id="6958c-111">在使用 RMO 進行程式開發時關閉伺服器連接，與使用 SMO 時稍有不同。</span><span class="sxs-lookup"><span data-stu-id="6958c-111">Closing server connections when you are programming with RMO works slightly different from SMO.</span></span>  
  
 <span data-ttu-id="6958c-112">由於 RMO 物件的伺服器連接是由物件維護，因此 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 當您使用 RMO 進行程式設計時，也會使用這個物件來與的實例中斷連接。</span><span class="sxs-lookup"><span data-stu-id="6958c-112">Because the server connection for an RMO object is maintained by the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, this object is also used when disconnecting from an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when you program by using RMO.</span></span> <span data-ttu-id="6958c-113">若要使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件關閉連接，請呼叫 RMO 物件的 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6958c-113">To close a connection by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object, call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method of the RMO object.</span></span> <span data-ttu-id="6958c-114">在關閉連接之後，就無法使用 RMO 物件。</span><span class="sxs-lookup"><span data-stu-id="6958c-114">After the connection has been closed, RMO objects cannot be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6958c-115">範例</span><span class="sxs-lookup"><span data-stu-id="6958c-115">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a><span data-ttu-id="6958c-116">在 Visual Basic 中關閉和中斷 SMO 物件的連接</span><span class="sxs-lookup"><span data-stu-id="6958c-116">Closing and Disconnecting an SMO Object in Visual Basic</span></span>  
 <span data-ttu-id="6958c-117">此程式碼範例示範如何設定 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 物件屬性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 屬性以要求非共用連接。</span><span class="sxs-lookup"><span data-stu-id="6958c-117">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VB4](SMO How to#SMO_VB4)]  -->  
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a><span data-ttu-id="6958c-118">在 Visual C# 中關閉和中斷 SMO 物件的連接</span><span class="sxs-lookup"><span data-stu-id="6958c-118">Closing and Disconnecting an SMO Object in Visual C#</span></span>  
 <span data-ttu-id="6958c-119">此程式碼範例示範如何設定 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 物件屬性的 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 屬性以要求非共用連接。</span><span class="sxs-lookup"><span data-stu-id="6958c-119">This code example shows how to request a non-pooled connection by setting the <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> object property.</span></span>  
  
```  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6958c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6958c-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  
