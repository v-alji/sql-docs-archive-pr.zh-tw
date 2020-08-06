---
title: 管理 Service Broker |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Service Broker [SMO]
ms.assetid: b29d7432-d1e5-4bb6-b544-57b3a9430f95
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce166825bb7adea241bac13defeca1a78b4f29cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686882"
---
# <a name="managing-service-broker"></a><span data-ttu-id="9e0eb-102">管理 Service Broker</span><span class="sxs-lookup"><span data-stu-id="9e0eb-102">Managing Service Broker</span></span>
  <span data-ttu-id="9e0eb-103">在 SMO 中，[!INCLUDE[ssSB](../../../includes/sssb-md.md)] 物件位於 `Microsoft.SqlServer.Management.Smo.Broker` 命名空間內，該命名空間需要參考 Microsoft.SqlServer.Smo.dll。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-103">In SMO, the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects are found in the `Microsoft.SqlServer.Management.Smo.Broker` namespace, which requires a reference to the Microsoft.SqlServer.Smo.dll.</span></span> <span data-ttu-id="9e0eb-104">支援類別資訊也需要參考 Microsoft.SqlServer.ServiceBrokerEnum.dll。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-104">A reference to the Microsoft.SqlServer.ServiceBrokerEnum.dll is also required for supporting class information.</span></span>  
  
 <span data-ttu-id="9e0eb-105">SMO 會提供一組 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 物件，允許 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 的程式設計管理 (DDL) 實作。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-105">SMO provides a set of [!INCLUDE[ssSB](../../../includes/sssb-md.md)] objects that permit programmatic management (DDL) of the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation.</span></span> <span data-ttu-id="9e0eb-106">這包括定義訊息類型、合約、佇列與服務。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-106">This includes defining the message types, contracts, queues, and services.</span></span> <span data-ttu-id="9e0eb-107">SMO 是一個其用途並不在於資料操作的管理工具，因此，SMO 不支援傳送和接收 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 訊息。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-107">Because SMO is a management tool that is not intended for data manipulation, sending and receiving [!INCLUDE[ssSB](../../../includes/sssb-md.md)] messages is not supported by SMO.</span></span>  
  
 <span data-ttu-id="9e0eb-108">在 SMO 中，<xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> 物件是最上層的類別，其下則為所有 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 功能所在之處。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-108">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Database.ServiceBroker%2A> object is the top-level class under which all the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] functionality resides.</span></span> <span data-ttu-id="9e0eb-109">對於參與分散式訊息應用程式的每個資料庫而言，都需要 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 實作。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-109">A [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation is required for each database that is participating in the distributed messaging application.</span></span> <span data-ttu-id="9e0eb-110">因此，<xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> 物件是 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件的子系。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-110">Therefore, the <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="9e0eb-111"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> 物件包含下列物件的集合，用於定義 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 實作：</span><span class="sxs-lookup"><span data-stu-id="9e0eb-111">The <xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceBroker> object contains collections of the following objects that are used to define the [!INCLUDE[ssSB](../../../includes/sssb-md.md)] implementation:</span></span>  
  
-   <span data-ttu-id="9e0eb-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> 物件代表定義訊息內容的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-112"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageType> objects represent message types that define the content of messages.</span></span>  
  
-   <span data-ttu-id="9e0eb-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> 物件代表指定給定交談中訊息方向和類型的合約。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-113"><xref:Microsoft.SqlServer.Management.Smo.Broker.MessageTypeMapping> objects represent contracts that specify the direction and type of messages in a given conversation.</span></span>  
  
-   <span data-ttu-id="9e0eb-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> 物件會在傳送訊息前以及收到訊息後儲存訊息。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-114"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceQueue> objects store messages prior to sending and after they are received.</span></span> <span data-ttu-id="9e0eb-115">它們提供服務之間的非同步通訊，以及其他優點，如自動鎖定同一交談群組中的訊息。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-115">They provide asynchronous communication between services, as well as other benefits, such as automatically locking messages in the same conversation group.</span></span>  
  
-   <span data-ttu-id="9e0eb-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> 物件代表 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 服務，也就是交談的可定址端點。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-116"><xref:Microsoft.SqlServer.Management.Smo.Broker.BrokerService> objects represent [!INCLUDE[ssSB](../../../includes/sssb-md.md)] services, which are the addressable endpoints for conversations.</span></span> [!INCLUDE[ssSB](../../../includes/sssb-md.md)] <span data-ttu-id="9e0eb-117">訊息會從某個服務傳送至另一個服務。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-117">messages are sent from one service to another service.</span></span> <span data-ttu-id="9e0eb-118">服務會指定要保存訊息的佇列，並指定哪個服務可做為目標的合約。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-118">A service specifies a queue to hold messages, and specifies the contracts for which the service can be the target.</span></span>  
  
-   <span data-ttu-id="9e0eb-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> 物件代表 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 在與遠端服務進行通訊時，用於安全性與驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-119"><xref:Microsoft.SqlServer.Management.Smo.Broker.RemoteServiceBinding> objects represent the settings that [!INCLUDE[ssSB](../../../includes/sssb-md.md)] uses for security and authentication when communicating with a remote service.</span></span>  
  
-   <span data-ttu-id="9e0eb-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> 物件代表 [!INCLUDE[ssSB](../../../includes/sssb-md.md)] 路由，其中包含服務的位置資訊以及所定義的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-120"><xref:Microsoft.SqlServer.Management.Smo.Broker.ServiceRoute> objects represents a [!INCLUDE[ssSB](../../../includes/sssb-md.md)] route, which contains the location information for the service and the database on which it is defined.</span></span> <span data-ttu-id="9e0eb-121">訊息傳遞需要路由。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-121">A route is required for message delivery.</span></span> <span data-ttu-id="9e0eb-122">根據預設，每個資料庫包含的路由都會將位置指定為目前的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9e0eb-122">By default, each database contains a route that specifies the location as the current instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0eb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e0eb-123">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>   
 [<span data-ttu-id="9e0eb-124">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="9e0eb-124">SQL Server Service Broker</span></span>](../../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
