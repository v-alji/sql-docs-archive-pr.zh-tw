---
title: SQL Server Service Broker | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d3877dd8311e0fe5b65bd4b1e7f9c40fbd84751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707833"
---
# <a name="sql-server-service-broker"></a><span data-ttu-id="b404c-102">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="b404c-102">SQL Server Service Broker</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="b404c-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)]在中提供訊息和佇列應用程式的原生支援 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b404c-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)] provides native support for messaging and queuing applications in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="b404c-104">這讓開發人員更容易建立使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 元件在不同資料庫間進行通訊的複雜應用程式。</span><span class="sxs-lookup"><span data-stu-id="b404c-104">This makes it easier for developers to create sophisticated applications that use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] components to communicate between disparate databases.</span></span> <span data-ttu-id="b404c-105">開發人員可以使用 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 輕鬆地建立可靠的分散式應用程式。</span><span class="sxs-lookup"><span data-stu-id="b404c-105">Developers can use [!INCLUDE[ssSB](../../includes/sssb-md.md)] to easily build distributed and reliable applications.</span></span>  
  
 <span data-ttu-id="b404c-106">使用 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 的應用程式開發人員不需要撰寫複雜的通訊和傳訊間隔程式，即可將資料工作負載分散在多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="b404c-106">Application developers who use [!INCLUDE[ssSB](../../includes/sssb-md.md)] can distribute data workloads across several databases without programming complex communication and messaging internals.</span></span> <span data-ttu-id="b404c-107">這可減少開發和測試工作，因為 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 會處理交談內容中的通訊路徑。</span><span class="sxs-lookup"><span data-stu-id="b404c-107">This reduces development and test work because [!INCLUDE[ssSB](../../includes/sssb-md.md)] handles the communication paths in the context of a conversation.</span></span> <span data-ttu-id="b404c-108">此外，還可提升效能。</span><span class="sxs-lookup"><span data-stu-id="b404c-108">It also improves performance.</span></span> <span data-ttu-id="b404c-109">例如，支援網站的前端資料庫可記錄資訊，並將具有大量處理序的工作傳送到後端資料庫的佇列中。</span><span class="sxs-lookup"><span data-stu-id="b404c-109">For example, front-end databases supporting Web sites can record information and send process intensive tasks to queue in back-end databases.</span></span> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="b404c-110">可確保所有工作都在交易內容中管理，以確保可靠性和技術一致性。</span><span class="sxs-lookup"><span data-stu-id="b404c-110">ensures that all tasks are managed in the context of transactions to assure reliability and technical consistency.</span></span>  
  
## <a name="where-is-the-documentation-for-service-broker"></a><span data-ttu-id="b404c-111">Service Broker 的文件集在哪裡？</span><span class="sxs-lookup"><span data-stu-id="b404c-111">Where is the documentation for Service Broker?</span></span>  
 <span data-ttu-id="b404c-112">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 的參考文件集包含在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 文件集內。</span><span class="sxs-lookup"><span data-stu-id="b404c-112">The reference documentation for [!INCLUDE[ssSB](../../includes/sssb-md.md)] is included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation.</span></span> <span data-ttu-id="b404c-113">此參考文件集包含下列章節：</span><span class="sxs-lookup"><span data-stu-id="b404c-113">This reference documentation includes the following sections:</span></span>  
  
-   <span data-ttu-id="b404c-114">[資料定義語言 &#40;DDL&#41; 陳述式 &#40;Transact-SQL&#41;](/sql/odbc/reference/develop-app/ddl-statements)，適用 CREATE、ALTER 和 DROP 陳述式</span><span class="sxs-lookup"><span data-stu-id="b404c-114">[Data Definition Language &#40;DDL&#41; Statements &#40;Transact-SQL&#41;](/sql/odbc/reference/develop-app/ddl-statements) for CREATE, ALTER, and DROP statements</span></span>  
  
-   [<span data-ttu-id="b404c-115">Service Broker 目錄檢視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b404c-115">Service Broker Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql)  
  
-   [<span data-ttu-id="b404c-116">Service Broker 相關的動態管理檢視 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b404c-116">Service Broker Related Dynamic Management Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql)  
  
-   [<span data-ttu-id="b404c-117">ssbdiagnose 公用程式 &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="b404c-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 <span data-ttu-id="b404c-118">請參閱＜ [舊版文件集](https://go.microsoft.com/fwlink/?LinkId=231312) ＞，了解 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 概念及開發和管理工作。</span><span class="sxs-lookup"><span data-stu-id="b404c-118">See the [previously published documentation](https://go.microsoft.com/fwlink/?LinkId=231312) for [!INCLUDE[ssSB](../../includes/sssb-md.md)] concepts and for development and management tasks.</span></span> <span data-ttu-id="b404c-119">此文件集未在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 文件集中重製，因為 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 中只有少數 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]的變更。</span><span class="sxs-lookup"><span data-stu-id="b404c-119">This documentation is not reproduced in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation due to the small number of changes in [!INCLUDE[ssSB](../../includes/sssb-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="whats-new-in-service-broker"></a><span data-ttu-id="b404c-120">Service Broker 的新功能</span><span class="sxs-lookup"><span data-stu-id="b404c-120">What's new in Service Broker</span></span>  
 <span data-ttu-id="b404c-121">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]並無導入重大變更。</span><span class="sxs-lookup"><span data-stu-id="b404c-121">No significant changes are introduced in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  <span data-ttu-id="b404c-122">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中導入了下列變更。</span><span class="sxs-lookup"><span data-stu-id="b404c-122">The following changes were introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a><span data-ttu-id="b404c-123">訊息可以傳送至多個目標服務 (多點傳送)</span><span class="sxs-lookup"><span data-stu-id="b404c-123">Messages can be sent to multiple target services (multicast)</span></span>  
 <span data-ttu-id="b404c-124">[SEND &#40;Transact-SQL&#41;](/sql/t-sql/statements/send-transact-sql) 陳述式的語法已延伸，可透過支援多個交談控制代碼進行多點傳送。</span><span class="sxs-lookup"><span data-stu-id="b404c-124">The syntax of the [SEND &#40;Transact-SQL&#41;](/sql/t-sql/statements/send-transact-sql) statement has been extended to enable multicast by supporting multiple conversation handles.</span></span>  
  
### <a name="queues-expose-the-message-enqueued-time"></a><span data-ttu-id="b404c-125">佇列會公開訊息加入佇列的時間</span><span class="sxs-lookup"><span data-stu-id="b404c-125">Queues expose the message enqueued time</span></span>  
 <span data-ttu-id="b404c-126">佇列包含一個新的資料行 **message_enqueue_time**，其中顯示訊息已在佇列中的時間。</span><span class="sxs-lookup"><span data-stu-id="b404c-126">Queues have a new column, **message_enqueue_time**, that shows how long a message has been in the queue.</span></span>  
  
### <a name="poison-message-handling-can-be-disabled"></a><span data-ttu-id="b404c-127">有害訊息處理可以停用</span><span class="sxs-lookup"><span data-stu-id="b404c-127">Poison message handling can be disabled</span></span>  
 <span data-ttu-id="b404c-128">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) 和 [ALTER QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-queue-transact-sql) 陳述式現在能夠藉由加入子句 `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)` 的方式啟用或停用有害訊息處理。</span><span class="sxs-lookup"><span data-stu-id="b404c-128">The [CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) and [ALTER QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-queue-transact-sql) statements now have the ability to enable or disable poison message handling by adding the clause, `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)`.</span></span> <span data-ttu-id="b404c-129">目錄檢視 **sys.service_queues** 現在包含 **is_poison_message_handling_enabled** 資料行，用來指出有害訊息為啟用或停用狀態。</span><span class="sxs-lookup"><span data-stu-id="b404c-129">The catalog view **sys.service_queues** now has the column **is_poison_message_handling_enabled** to indicate whether poison message is enabled or disabled.</span></span>  
  
### <a name="alwayson-support-in-service-broker"></a><span data-ttu-id="b404c-130">Service Broker 中的 AlwaysOn 支援</span><span class="sxs-lookup"><span data-stu-id="b404c-130">AlwaysOn support in Service Broker</span></span>  
 <span data-ttu-id="b404c-131">如需詳細資訊，請參閱 [Service Broker 與 AlwaysOn 可用性群組 &#40;SQL Server&#41;](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b404c-131">For more information, see [Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).</span></span>  
  
  
