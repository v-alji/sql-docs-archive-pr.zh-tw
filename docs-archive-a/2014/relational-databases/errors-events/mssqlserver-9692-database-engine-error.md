---
title: MSSQLSERVER_9692 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b6ba95771aafffa5a322ffa1b7443419936addd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595036"
---
# <a name="mssqlserver_9692"></a><span data-ttu-id="5b69e-102">MSSQLSERVER_9692</span><span class="sxs-lookup"><span data-stu-id="5b69e-102">MSSQLSERVER_9692</span></span>
    
## <a name="details"></a><span data-ttu-id="5b69e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5b69e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b69e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5b69e-104">Product Name</span></span>|<span data-ttu-id="5b69e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5b69e-105">SQL Server</span></span>|  
|<span data-ttu-id="5b69e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5b69e-106">Event ID</span></span>|<span data-ttu-id="5b69e-107">9692</span><span class="sxs-lookup"><span data-stu-id="5b69e-107">9692</span></span>|  
|<span data-ttu-id="5b69e-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="5b69e-108">Event Source</span></span>|<span data-ttu-id="5b69e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5b69e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5b69e-110">元件</span><span class="sxs-lookup"><span data-stu-id="5b69e-110">Component</span></span>|<span data-ttu-id="5b69e-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5b69e-111">SQLEngine</span></span>|  
|<span data-ttu-id="5b69e-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5b69e-112">Symbolic Name</span></span>|<span data-ttu-id="5b69e-113">SB2_CANT_LISTEN_PORT_IN_USE</span><span class="sxs-lookup"><span data-stu-id="5b69e-113">SB2_CANT_LISTEN_PORT_IN_USE</span></span>|  
|<span data-ttu-id="5b69e-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5b69e-114">Message Text</span></span>|<span data-ttu-id="5b69e-115">%S_MSG 通訊協定傳輸無法在連接埠 %d 上接聽，因為它正由另一個處理序所使用。</span><span class="sxs-lookup"><span data-stu-id="5b69e-115">The %S_MSG protocol transport cannot listen on port %d because it is in use by another process.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5b69e-116">說明</span><span class="sxs-lookup"><span data-stu-id="5b69e-116">Explanation</span></span>  
 <span data-ttu-id="5b69e-117">電腦上的另一個程式正在使用指定的 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="5b69e-117">Another program on the computer is using the TCP port indicated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5b69e-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5b69e-118">User Action</span></span>  
 <span data-ttu-id="5b69e-119">執行 `netstat -aon` 以判斷哪一個程式正在使用該埠。</span><span class="sxs-lookup"><span data-stu-id="5b69e-119">Run `netstat -aon` to determine what program is using the port.</span></span> <span data-ttu-id="5b69e-120">停用該應用程式，或者為 Service Broker 指定不同的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="5b69e-120">Disable that application or specify a different port for Service Broker.</span></span>  
  
  
