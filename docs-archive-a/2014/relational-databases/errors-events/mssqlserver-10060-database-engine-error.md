---
title: MSSQLSERVER_10060 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "10060"
helpviewer_keywords:
- 10060 (Database Engine error)
ms.assetid: 28c21277-cad8-406c-a955-07933a56982a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d634cfb06381fb916ef2e421e0677e76edb9ae02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706545"
---
# <a name="mssqlserver_10060"></a><span data-ttu-id="409a3-102">MSSQLSERVER_10060</span><span class="sxs-lookup"><span data-stu-id="409a3-102">MSSQLSERVER_10060</span></span>
    
## <a name="details"></a><span data-ttu-id="409a3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="409a3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="409a3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="409a3-104">Product Name</span></span>|<span data-ttu-id="409a3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="409a3-105">SQL Server</span></span>|  
|<span data-ttu-id="409a3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="409a3-106">Event ID</span></span>|<span data-ttu-id="409a3-107">10060</span><span class="sxs-lookup"><span data-stu-id="409a3-107">10060</span></span>|  
|<span data-ttu-id="409a3-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="409a3-108">Event Source</span></span>|<span data-ttu-id="409a3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="409a3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="409a3-110">元件</span><span class="sxs-lookup"><span data-stu-id="409a3-110">Component</span></span>|<span data-ttu-id="409a3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="409a3-111">SQLEngine</span></span>|  
|<span data-ttu-id="409a3-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="409a3-112">Symbolic Name</span></span>||  
|<span data-ttu-id="409a3-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="409a3-113">Message Text</span></span>|<span data-ttu-id="409a3-114">建立伺服器的連接時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="409a3-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="409a3-115">連接到 SQL Server 時，可能因為在預設的設定下 SQL Server 不允許遠端連接而引起此失敗。</span><span class="sxs-lookup"><span data-stu-id="409a3-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="409a3-116">(提供者：TCP 提供者，錯誤: 0 - 連線嘗試失敗，因為連線對象有一段時間並未正確回應，或是連線建立失敗，因為連線的主機無法回應。) (Microsoft SQL Server，錯誤:10060)</span><span class="sxs-lookup"><span data-stu-id="409a3-116">(provider: TCP Provider, error: 0 - A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.) (Microsoft SQL Server, Error: 10060)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="409a3-117">說明</span><span class="sxs-lookup"><span data-stu-id="409a3-117">Explanation</span></span>  
 <span data-ttu-id="409a3-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端無法連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="409a3-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="409a3-119">發生這個錯誤的原因，可能是伺服器上的防火牆拒絕連接，或伺服器未設定成接受遠端連接。</span><span class="sxs-lookup"><span data-stu-id="409a3-119">This error could occur because either the firewall on the server has refused the connection or the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="409a3-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="409a3-120">User Action</span></span>  
 <span data-ttu-id="409a3-121">若要解決這個錯誤，請嘗試下列任一動作：</span><span class="sxs-lookup"><span data-stu-id="409a3-121">To resolve this error, try one of the following actions:</span></span>  
  
-   <span data-ttu-id="409a3-122">確定已將電腦上的防火牆設定成允許這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體接受連接。</span><span class="sxs-lookup"><span data-stu-id="409a3-122">Make sure that you have configured the firewall on the computer to allow this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
-   <span data-ttu-id="409a3-123">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員工具，將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定成接受遠端連接。</span><span class="sxs-lookup"><span data-stu-id="409a3-123">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409a3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="409a3-124">See Also</span></span>  
 <span data-ttu-id="409a3-125">[設定資料庫引擎存取的 Windows 防火牆](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="409a3-125">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="409a3-126">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="409a3-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="409a3-127">[網路通訊協定和網路程式庫](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="409a3-127">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="409a3-128">[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="409a3-128">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="409a3-129">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="409a3-129">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="409a3-130">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="409a3-130">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
