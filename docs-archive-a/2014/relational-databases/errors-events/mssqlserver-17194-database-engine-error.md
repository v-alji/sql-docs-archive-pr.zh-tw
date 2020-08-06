---
title: MSSQLSERVER_17194 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "17194"
helpviewer_keywords:
- 17194 (Database Engine error)
ms.assetid: 0d03eb20-28a7-4ceb-8903-7f9420a620f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d3f56a104841c4825bba1f60b3588fadd63555c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595083"
---
# <a name="mssqlserver_17194"></a><span data-ttu-id="6833f-102">MSSQLSERVER_17194</span><span class="sxs-lookup"><span data-stu-id="6833f-102">MSSQLSERVER_17194</span></span>
    
## <a name="details"></a><span data-ttu-id="6833f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6833f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6833f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6833f-104">Product Name</span></span>|<span data-ttu-id="6833f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6833f-105">SQL Server</span></span>|  
|<span data-ttu-id="6833f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6833f-106">Event ID</span></span>|<span data-ttu-id="6833f-107">17194</span><span class="sxs-lookup"><span data-stu-id="6833f-107">17194</span></span>|  
|<span data-ttu-id="6833f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="6833f-108">Event Source</span></span>|<span data-ttu-id="6833f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6833f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6833f-110">元件</span><span class="sxs-lookup"><span data-stu-id="6833f-110">Component</span></span>|<span data-ttu-id="6833f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6833f-111">SQLEngine</span></span>|  
|<span data-ttu-id="6833f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6833f-112">Symbolic Name</span></span>||  
|<span data-ttu-id="6833f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6833f-113">Message Text</span></span>|<span data-ttu-id="6833f-114">伺服器無法載入登入所需的 SSL 提供者程式庫，此連接已經關閉。</span><span class="sxs-lookup"><span data-stu-id="6833f-114">The server was unable to load the SSL provider library needed to log in; the connection has been closed.</span></span> <span data-ttu-id="6833f-115">SSL 可用來加密登入順序或所有通訊，視管理員對伺服器所做的設定而定。</span><span class="sxs-lookup"><span data-stu-id="6833f-115">SSL is used to encrypt either the login sequence or all communications, depending on how the administrator has configured the server.</span></span> <span data-ttu-id="6833f-116">請參閱線上叢書，以取得有關此錯誤訊息的資訊：0xXXXX。</span><span class="sxs-lookup"><span data-stu-id="6833f-116">See Books Online for information on this error message:  0xXXXX.</span></span> <span data-ttu-id="6833f-117">[用戶端：11.11.11.11]</span><span class="sxs-lookup"><span data-stu-id="6833f-117">[CLIENT: 11.11.11.11]</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6833f-118">說明</span><span class="sxs-lookup"><span data-stu-id="6833f-118">Explanation</span></span>  
 <span data-ttu-id="6833f-119">這個錯誤表示用戶端已經關閉連接。</span><span class="sxs-lookup"><span data-stu-id="6833f-119">This error indicates that the client has closed the connection.</span></span> <span data-ttu-id="6833f-120">發生這個錯誤是因為連接逾時期限已到。</span><span class="sxs-lookup"><span data-stu-id="6833f-120">This error could occur because the connection time-out has expired.</span></span> <span data-ttu-id="6833f-121">錯誤訊息中顯示的值來自作業系統，提供基礎問題的說明。</span><span class="sxs-lookup"><span data-stu-id="6833f-121">The error message displays a value from the operating system that describes the underlying problem.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6833f-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6833f-122">User Action</span></span>  
 <span data-ttu-id="6833f-123">如果訊息中的錯誤碼是 0x2746 (十進位值 10054)，即表示用戶端已經重設連接，通常是因為逾時之故。若要解決錯誤，請增加用戶端或呼叫端程式的連接逾時值。</span><span class="sxs-lookup"><span data-stu-id="6833f-123">If the error code in the message is 0x2746 (decimal value 10054), this means that the connection was reset by the client, typically because of a time-out. To resolve the error, increase the connection time-out on the client or calling program.</span></span>  
  
 <span data-ttu-id="6833f-124">如需得知其他錯誤訊息值可行的解決方案，請使用作業系統命令 **net helpmsg** 並指定錯誤碼的十進位值。</span><span class="sxs-lookup"><span data-stu-id="6833f-124">To determine a possible solution for other error message values, use the operating system command **net helpmsg** and specify the decimal value of the error code.</span></span>  
  
 <span data-ttu-id="6833f-125">如需如何連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的詳細資訊，請參閱[伺服器網路組態](../../database-engine/configure-windows/server-network-configuration.md)和[用戶端網路組態](../../database-engine/configure-windows/client-network-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="6833f-125">For more information about how to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Server Network Configuration](../../database-engine/configure-windows/server-network-configuration.md) and [Client Network Configuration](../../database-engine/configure-windows/client-network-configuration.md).</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="6833f-126">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="6833f-126">Internal-Only</span></span>  
  
