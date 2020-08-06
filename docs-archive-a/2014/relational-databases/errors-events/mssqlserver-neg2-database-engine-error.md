---
title: MSSQLSERVER_-2 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "2"
helpviewer_keywords:
- -2 (Database Engine error)
ms.assetid: f37a7b7d-26e1-4b9e-bcb4-57f7805393d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d39b4a11387a60056bba3f87adffcb2653b60f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701221"
---
# <a name="mssqlserver_-2"></a><span data-ttu-id="62536-102">MSSQLSERVER_-2</span><span class="sxs-lookup"><span data-stu-id="62536-102">MSSQLSERVER_-2</span></span>
    
## <a name="details"></a><span data-ttu-id="62536-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="62536-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62536-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="62536-104">Product Name</span></span>|<span data-ttu-id="62536-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="62536-105">SQL Server</span></span>|  
|<span data-ttu-id="62536-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="62536-106">Event ID</span></span>|<span data-ttu-id="62536-107">-2</span><span class="sxs-lookup"><span data-stu-id="62536-107">-2</span></span>|  
|<span data-ttu-id="62536-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="62536-108">Event Source</span></span>|<span data-ttu-id="62536-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="62536-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="62536-110">元件</span><span class="sxs-lookup"><span data-stu-id="62536-110">Component</span></span>|<span data-ttu-id="62536-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="62536-111">SQLEngine</span></span>|  
|<span data-ttu-id="62536-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="62536-112">Symbolic Name</span></span>||  
|<span data-ttu-id="62536-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="62536-113">Message Text</span></span>|<span data-ttu-id="62536-114">已超過逾時的設定。</span><span class="sxs-lookup"><span data-stu-id="62536-114">Timeout expired.</span></span>  <span data-ttu-id="62536-115">在作業完成前就已超過逾時期間，或是伺服器沒有回應。</span><span class="sxs-lookup"><span data-stu-id="62536-115">The timeout period elapsed prior to completion of the operation or the server is not responding.</span></span> <span data-ttu-id="62536-116">(Microsoft SQL Server，錯誤: -2)</span><span class="sxs-lookup"><span data-stu-id="62536-116">(Microsoft SQL Server, Error: -2)</span></span>|   
  
## <a name="explanation"></a><span data-ttu-id="62536-117">說明</span><span class="sxs-lookup"><span data-stu-id="62536-117">Explanation</span></span>  
 <span data-ttu-id="62536-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端無法連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="62536-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client cannot connect to the server.</span></span> <span data-ttu-id="62536-119">發生這個錯誤可能是因為伺服器上的防火牆拒絕連接。</span><span class="sxs-lookup"><span data-stu-id="62536-119">This error could occur because the firewall on the server has refused the connection.</span></span> 
  
## <a name="user-action"></a><span data-ttu-id="62536-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="62536-120">User Action</span></span>  
 <span data-ttu-id="62536-121">確定已將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 伺服器執行個體上的防火牆設定成接受連線。</span><span class="sxs-lookup"><span data-stu-id="62536-121">Make sure that you have configured the firewall on the server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to accept connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62536-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62536-122">See Also</span></span>  
 <span data-ttu-id="62536-123">[設定 Windows 防火牆以允許 SQL Server 存取](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span><span class="sxs-lookup"><span data-stu-id="62536-123">[Configure the Windows Firewall to Allow SQL Server Access](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md) </span></span>  
 <span data-ttu-id="62536-124">[設定資料庫引擎存取的 Windows 防火牆](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span><span class="sxs-lookup"><span data-stu-id="62536-124">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md) </span></span>  
 <span data-ttu-id="62536-125">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="62536-125">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 <span data-ttu-id="62536-126">[網路通訊協定和網路程式庫](../../sql-server/install/network-protocols-and-network-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="62536-126">[Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md) </span></span>  
 <span data-ttu-id="62536-127">[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="62536-127">[Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md) </span></span>  
 <span data-ttu-id="62536-128">[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md) </span><span class="sxs-lookup"><span data-stu-id="62536-128">[Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md) </span></span>  
 [<span data-ttu-id="62536-129">啟用或停用伺服器網路通訊協定</span><span class="sxs-lookup"><span data-stu-id="62536-129">Enable or Disable a Server Network Protocol</span></span>](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
