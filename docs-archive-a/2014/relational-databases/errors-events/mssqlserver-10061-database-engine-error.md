---
title: MSSQLSERVER_10061 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10061"
helpviewer_keywords:
- 10061 (Database Engine error)
ms.assetid: 729602f3-08df-474c-8740-8dea13c1eee3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0c866bd8dce01f65036f1d508a94252a97613424
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704113"
---
# <a name="mssqlserver_10061"></a><span data-ttu-id="18517-102">MSSQLSERVER_10061</span><span class="sxs-lookup"><span data-stu-id="18517-102">MSSQLSERVER_10061</span></span>
    
## <a name="details"></a><span data-ttu-id="18517-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="18517-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18517-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="18517-104">Product Name</span></span>|<span data-ttu-id="18517-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="18517-105">SQL Server</span></span>|  
|<span data-ttu-id="18517-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="18517-106">Event ID</span></span>|<span data-ttu-id="18517-107">10061</span><span class="sxs-lookup"><span data-stu-id="18517-107">10061</span></span>|  
|<span data-ttu-id="18517-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="18517-108">Event Source</span></span>|<span data-ttu-id="18517-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="18517-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="18517-110">元件</span><span class="sxs-lookup"><span data-stu-id="18517-110">Component</span></span>|<span data-ttu-id="18517-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="18517-111">SQLEngine</span></span>|  
|<span data-ttu-id="18517-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="18517-112">Symbolic Name</span></span>||  
|<span data-ttu-id="18517-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="18517-113">Message Text</span></span>|<span data-ttu-id="18517-114">建立伺服器的連接時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="18517-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="18517-115">連接到 SQL Server 時，可能因為在預設的設定下 SQL Server 不允許遠端連接而引起此失敗。</span><span class="sxs-lookup"><span data-stu-id="18517-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="18517-116">(提供者：TCP 提供者，錯誤: 0 - 無法連線，因為目標電腦拒絕連線。) (Microsoft SQL Server，錯誤:10061)</span><span class="sxs-lookup"><span data-stu-id="18517-116">(provider: TCP Provider, error: 0 - No connection could be made because the target machine actively refused it.) (Microsoft SQL Server, Error: 10061)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="18517-117">說明</span><span class="sxs-lookup"><span data-stu-id="18517-117">Explanation</span></span>  
 <span data-ttu-id="18517-118">伺服器並未回應用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="18517-118">The server did not respond to the client request.</span></span> <span data-ttu-id="18517-119">發生這個錯誤可能是因為伺服器尚未啟動。</span><span class="sxs-lookup"><span data-stu-id="18517-119">This error could occur because the server is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="18517-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="18517-120">User Action</span></span>  
 <span data-ttu-id="18517-121">請確定伺服器已經啟動。</span><span class="sxs-lookup"><span data-stu-id="18517-121">Make sure that the server is started.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18517-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18517-122">See Also</span></span>  
 <span data-ttu-id="18517-123">[管理 Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span><span class="sxs-lookup"><span data-stu-id="18517-123">[Manage the Database Engine Services](../../database-engine/configure-windows/manage-the-database-engine-services.md) </span></span>  
 <span data-ttu-id="18517-124">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="18517-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="18517-125">[網路通訊協定和網路程式庫](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="18517-125">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="18517-126">[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="18517-126">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="18517-127">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="18517-127">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="18517-128">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="18517-128">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
