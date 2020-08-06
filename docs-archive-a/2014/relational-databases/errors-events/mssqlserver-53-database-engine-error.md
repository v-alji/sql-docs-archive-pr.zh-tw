---
title: MSSQLSERVER_53 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "53"
helpviewer_keywords:
- 53 (Database Engine error)
ms.assetid: 1234f5a2-b3d1-425a-b29f-480fa792305f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 85fda292fb956047f51b9c7cd1d229ac0afce6b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596730"
---
# <a name="mssqlserver_53"></a><span data-ttu-id="30778-102">MSSQLSERVER_53</span><span class="sxs-lookup"><span data-stu-id="30778-102">MSSQLSERVER_53</span></span>
    
## <a name="details"></a><span data-ttu-id="30778-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="30778-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30778-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="30778-104">Product Name</span></span>|<span data-ttu-id="30778-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="30778-105">SQL Server</span></span>|  
|<span data-ttu-id="30778-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="30778-106">Event ID</span></span>|<span data-ttu-id="30778-107">53</span><span class="sxs-lookup"><span data-stu-id="30778-107">53</span></span>|  
|<span data-ttu-id="30778-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="30778-108">Event Source</span></span>|<span data-ttu-id="30778-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="30778-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="30778-110">元件</span><span class="sxs-lookup"><span data-stu-id="30778-110">Component</span></span>|<span data-ttu-id="30778-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="30778-111">SQLEngine</span></span>|  
|<span data-ttu-id="30778-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="30778-112">Symbolic Name</span></span>||  
|<span data-ttu-id="30778-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="30778-113">Message Text</span></span>|<span data-ttu-id="30778-114">建立伺服器的連接時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="30778-114">An error has occurred while establishing a connection to the server.</span></span>  <span data-ttu-id="30778-115">連接到 SQL Server 時，可能因為在預設的設定下 SQL Server 不允許遠端連接而引起此失敗。</span><span class="sxs-lookup"><span data-stu-id="30778-115">When connecting to SQL Server, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections.</span></span> <span data-ttu-id="30778-116">(提供者：具名管道提供者，錯誤: 40 - 無法開啟至 SQL Server 的連接) (.Net SqlClient 資料提供者)</span><span class="sxs-lookup"><span data-stu-id="30778-116">(provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="30778-117">說明</span><span class="sxs-lookup"><span data-stu-id="30778-117">Explanation</span></span>  
 <span data-ttu-id="30778-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端無法連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="30778-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="30778-119">發生這個錯誤的原因，可能是用戶端無法解析伺服器的名稱，或伺服器的名稱不正確。</span><span class="sxs-lookup"><span data-stu-id="30778-119">This error could occur because either the client cannot resolve the name of the server or the name of the server is incorrect.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="30778-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="30778-120">User Action</span></span>  
 <span data-ttu-id="30778-121">確定在用戶端上輸入的伺服器名稱正確，並且可從用戶端解析伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="30778-121">Make sure that you have entered the correct server name on the client, and that you can resolve the name of the server from the client.</span></span> <span data-ttu-id="30778-122">若要檢查 TCP/IP 名稱解析，您可以使用 Windows 作業系統的 **ping** 命令。</span><span class="sxs-lookup"><span data-stu-id="30778-122">To check TCP/IP name resolution, you can use the **ping** command in the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30778-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30778-123">See Also</span></span>  
 <span data-ttu-id="30778-124">[網路通訊協定和網路程式庫](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="30778-124">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="30778-125">[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="30778-125">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="30778-126">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="30778-126">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="30778-127">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="30778-127">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
