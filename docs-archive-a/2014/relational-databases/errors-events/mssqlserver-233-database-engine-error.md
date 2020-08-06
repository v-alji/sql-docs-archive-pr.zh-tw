---
title: MSSQLSERVER_233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "233"
helpviewer_keywords:
- 233 (Database Engine error)
ms.assetid: 201665dc-7ac8-4c19-90d3-33354c5caa72
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c51fac7c0af16c520d7cf5538e512912e62cf87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698254"
---
# <a name="mssqlserver_233"></a><span data-ttu-id="f7bd2-102">MSSQLSERVER_233</span><span class="sxs-lookup"><span data-stu-id="f7bd2-102">MSSQLSERVER_233</span></span>
    
## <a name="details"></a><span data-ttu-id="f7bd2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f7bd2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7bd2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f7bd2-104">Product Name</span></span>|<span data-ttu-id="f7bd2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f7bd2-105">SQL Server</span></span>|  
|<span data-ttu-id="f7bd2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f7bd2-106">Event ID</span></span>|<span data-ttu-id="f7bd2-107">233</span><span class="sxs-lookup"><span data-stu-id="f7bd2-107">233</span></span>|  
|<span data-ttu-id="f7bd2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f7bd2-108">Event Source</span></span>|<span data-ttu-id="f7bd2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f7bd2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f7bd2-110">元件</span><span class="sxs-lookup"><span data-stu-id="f7bd2-110">Component</span></span>|<span data-ttu-id="f7bd2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f7bd2-111">SQLEngine</span></span>|  
|<span data-ttu-id="f7bd2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f7bd2-112">Symbolic Name</span></span>||  
|<span data-ttu-id="f7bd2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f7bd2-113">Message Text</span></span>|<span data-ttu-id="f7bd2-114">已順利建立與伺服器的連接，但隨後在登入過程中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f7bd2-114">A connection was successfully established with the server, but then an error occurred during the login process.</span></span> <span data-ttu-id="f7bd2-115">(提供者：共用記憶體提供者，錯誤:0 - 管道的另一端上無任何處理程序。) (Microsoft SQL Server，錯誤:233)</span><span class="sxs-lookup"><span data-stu-id="f7bd2-115">(provider: Shared Memory Provider, error: 0 - No process is on the other end of the pipe.) (Microsoft SQL Server, Error: 233)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f7bd2-116">說明</span><span class="sxs-lookup"><span data-stu-id="f7bd2-116">Explanation</span></span>  
 <span data-ttu-id="f7bd2-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端無法連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f7bd2-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="f7bd2-118">發生這個錯誤可能是因為伺服器未設定成接受遠端連接。</span><span class="sxs-lookup"><span data-stu-id="f7bd2-118">This error could occur because the server is not configured to accept remote connections.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f7bd2-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f7bd2-119">User Action</span></span>  
 <span data-ttu-id="f7bd2-120">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員工具，將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定成接受遠端連接。</span><span class="sxs-lookup"><span data-stu-id="f7bd2-120">Use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager tool to allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept remote connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bd2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7bd2-121">See Also</span></span>  
 <span data-ttu-id="f7bd2-122">[網路通訊協定和網路程式庫](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="f7bd2-122">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="f7bd2-123">[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f7bd2-123">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="f7bd2-124">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="f7bd2-124">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="f7bd2-125">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="f7bd2-125">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
