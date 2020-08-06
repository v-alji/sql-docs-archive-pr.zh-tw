---
title: MSSQLSERVER_-1 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 880212b1d2e9572bbb31535a5ba68b445c7e6f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704118"
---
# <a name="mssqlserver_-1"></a><span data-ttu-id="cd1d0-102">MSSQLSERVER_-1</span><span class="sxs-lookup"><span data-stu-id="cd1d0-102">MSSQLSERVER_-1</span></span>
    
## <a name="details"></a><span data-ttu-id="cd1d0-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cd1d0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd1d0-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cd1d0-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="cd1d0-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cd1d0-105">Event ID</span></span>|<span data-ttu-id="cd1d0-106">-1</span><span class="sxs-lookup"><span data-stu-id="cd1d0-106">-1</span></span>|  
|<span data-ttu-id="cd1d0-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="cd1d0-107">Event Source</span></span>|<span data-ttu-id="cd1d0-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cd1d0-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cd1d0-109">元件</span><span class="sxs-lookup"><span data-stu-id="cd1d0-109">Component</span></span>|<span data-ttu-id="cd1d0-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cd1d0-110">SQLEngine</span></span>|  
|<span data-ttu-id="cd1d0-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cd1d0-111">Symbolic Name</span></span>||  
|<span data-ttu-id="cd1d0-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cd1d0-112">Message Text</span></span>|<span data-ttu-id="cd1d0-113">建立伺服器的連接時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-113">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="cd1d0-114">連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可能因為在預設的設定下 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允許遠端連接而引起此失敗</span><span class="sxs-lookup"><span data-stu-id="cd1d0-114">When connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this failure may be caused by the fact that under the default settings [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow remote connections.</span></span> <span data-ttu-id="cd1d0-115">(提供者：SQL 網路介面，錯誤：28 - 伺服器不支援要求的通訊協定) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，錯誤：-1)</span><span class="sxs-lookup"><span data-stu-id="cd1d0-115">(provider: SQL Network Interfaces, error: 28 - Server doesn't support requested protocol) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Error: -1)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cd1d0-116">說明</span><span class="sxs-lookup"><span data-stu-id="cd1d0-116">Explanation</span></span>  
 <span data-ttu-id="cd1d0-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端無法連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="cd1d0-118">此錯誤可能是由下列其中一項原因所造成：</span><span class="sxs-lookup"><span data-stu-id="cd1d0-118">This error could be caused by one of the following reasons:</span></span>  
  
-   <span data-ttu-id="cd1d0-119">指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-119">A specified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name is not valid.</span></span>  
  
-   <span data-ttu-id="cd1d0-120">未啟用 TCP 或具名管道通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-120">The TCP, or named pipes protocols are not enabled.</span></span>  
  
-   <span data-ttu-id="cd1d0-121">伺服器上的防火牆拒絕連接。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-121">The firewall on the server has refused the connection.</span></span>  
  
-   <span data-ttu-id="cd1d0-122">未啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務 (sqlbrowser)。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-122">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service (sqlbrowser) is not started.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cd1d0-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cd1d0-123">User Action</span></span>  
 <span data-ttu-id="cd1d0-124">若要解決這個錯誤，請嘗試下列任一動作：</span><span class="sxs-lookup"><span data-stu-id="cd1d0-124">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="cd1d0-125">檢查在連接字串中指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體名稱的拼字。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-125">Check the spelling of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name that is specified in the connection string.</span></span>  
  
-   <span data-ttu-id="cd1d0-126">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員工具，讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接受透過 TCP 或具名管道通訊協定的遠端連接。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-126">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to enable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections over the TCP or named pipes protocols.</span></span>  
  
-   <span data-ttu-id="cd1d0-127">確認您已經將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 伺服器執行個體上的防火牆設為開啟 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的通訊埠以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 通訊埠 (UDP 1434)。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-127">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to open ports for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser port (UDP 1434).</span></span>  
  
-   <span data-ttu-id="cd1d0-128">確認 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務已在伺服器上啟動。</span><span class="sxs-lookup"><span data-stu-id="cd1d0-128">Make sure that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service is started on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1d0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd1d0-129">See Also</span></span>  
 <span data-ttu-id="cd1d0-130">[設定資料庫引擎存取的 Windows 防火牆](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="cd1d0-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="cd1d0-131">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="cd1d0-131">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="cd1d0-132">[網路通訊協定和網路程式庫](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="cd1d0-132">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="cd1d0-133">[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="cd1d0-133">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="cd1d0-134">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="cd1d0-134">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="cd1d0-135">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="cd1d0-135">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
