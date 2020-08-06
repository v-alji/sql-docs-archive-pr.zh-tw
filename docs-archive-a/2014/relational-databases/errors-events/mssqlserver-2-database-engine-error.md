---
title: MSSQLSERVER_2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- 2 (Database Engine error)
ms.assetid: 567fb571-7cda-4ce8-a702-cdff2df5d419
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 87d19a24219fda79de2cad4c06af4f1936b37b24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598928"
---
# <a name="mssqlserver_2"></a><span data-ttu-id="3c6b9-102">MSSQLSERVER_2</span><span class="sxs-lookup"><span data-stu-id="3c6b9-102">MSSQLSERVER_2</span></span>
    
## <a name="details"></a><span data-ttu-id="3c6b9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3c6b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c6b9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3c6b9-104">Product Name</span></span>|<span data-ttu-id="3c6b9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3c6b9-105">SQL Server</span></span>|  
|<span data-ttu-id="3c6b9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3c6b9-106">Event ID</span></span>|<span data-ttu-id="3c6b9-107">2</span><span class="sxs-lookup"><span data-stu-id="3c6b9-107">2</span></span>|  
|<span data-ttu-id="3c6b9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3c6b9-108">Event Source</span></span>|<span data-ttu-id="3c6b9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3c6b9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3c6b9-110">元件</span><span class="sxs-lookup"><span data-stu-id="3c6b9-110">Component</span></span>|<span data-ttu-id="3c6b9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3c6b9-111">SQLEngine</span></span>|  
|<span data-ttu-id="3c6b9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3c6b9-112">Symbolic Name</span></span>||  
|<span data-ttu-id="3c6b9-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3c6b9-113">Message Text</span></span>|<span data-ttu-id="3c6b9-114">建立伺服器的連接時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c6b9-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="3c6b9-115">連接到 SQL Server 時，可能因為在預設的設定下 SQL Server 不允許遠端連接而引起此失敗。</span><span class="sxs-lookup"><span data-stu-id="3c6b9-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="3c6b9-116">(提供者：具名管道提供者，錯誤: 40 - 無法開啟至 SQL Server 的連接) (.Net SqlClient 資料提供者)</span><span class="sxs-lookup"><span data-stu-id="3c6b9-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3c6b9-117">說明</span><span class="sxs-lookup"><span data-stu-id="3c6b9-117">Explanation</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3c6b9-118">無法回應用戶端要求，可能是因為伺服器尚未啟動。</span><span class="sxs-lookup"><span data-stu-id="3c6b9-118">did not respond to the client request because the server is probably not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3c6b9-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3c6b9-119">User Action</span></span>  
 <span data-ttu-id="3c6b9-120">請確定伺服器已經啟動。</span><span class="sxs-lookup"><span data-stu-id="3c6b9-120">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6b9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c6b9-121">See Also</span></span>  
 <span data-ttu-id="3c6b9-122">[管理 Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="3c6b9-122">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="3c6b9-123">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="3c6b9-123">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="3c6b9-124">[網路通訊協定和網路程式庫](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="3c6b9-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="3c6b9-125">[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3c6b9-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="3c6b9-126">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="3c6b9-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="3c6b9-127">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="3c6b9-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
