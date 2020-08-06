---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 006e616d80ef7e8d083f60675b02b4e6a4e8dc24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585482"
---
# <a name="mssqlserver_17887"></a><span data-ttu-id="59c81-102">MSSQLSERVER_17887</span><span class="sxs-lookup"><span data-stu-id="59c81-102">MSSQLSERVER_17887</span></span>
    
## <a name="details"></a><span data-ttu-id="59c81-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="59c81-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59c81-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="59c81-104">Product Name</span></span>|<span data-ttu-id="59c81-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="59c81-105">SQL Server</span></span>|  
|<span data-ttu-id="59c81-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="59c81-106">Event ID</span></span>|<span data-ttu-id="59c81-107">17887</span><span class="sxs-lookup"><span data-stu-id="59c81-107">17887</span></span>|  
|<span data-ttu-id="59c81-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="59c81-108">Event Source</span></span>|<span data-ttu-id="59c81-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="59c81-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="59c81-110">元件</span><span class="sxs-lookup"><span data-stu-id="59c81-110">Component</span></span>|<span data-ttu-id="59c81-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="59c81-111">SQLEngine</span></span>|  
|<span data-ttu-id="59c81-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="59c81-112">Symbolic Name</span></span>|<span data-ttu-id="59c81-113">SRV_IO_COMP_LISTENER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="59c81-113">SRV_IO_COMP_LISTENER_NONYIELDING</span></span>|  
|<span data-ttu-id="59c81-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="59c81-114">Message Text</span></span>|<span data-ttu-id="59c81-115">IO Completion Listener (0x%lx) 工作者 0x%p 在節點 %ld 上似乎沒有產量。</span><span class="sxs-lookup"><span data-stu-id="59c81-115">IO Completion Listener (0x%lx) Worker 0x%p appears to be non-yielding on Node %ld.</span></span> <span data-ttu-id="59c81-116">已使用的約略 CPU: 核心 %I64d ms，使用者 %I64d ms，間隔: %I64d。</span><span class="sxs-lookup"><span data-stu-id="59c81-116">Approx CPU Used: kernel %I64d ms, user %I64d ms, Interval: %I64d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="59c81-117">說明</span><span class="sxs-lookup"><span data-stu-id="59c81-117">Explanation</span></span>  
 <span data-ttu-id="59c81-118">表示針對網路讀取/寫入事件執行 I/O 完成常式時，指定之節點上的 I/O 完成通訊埠 (Completion Port) 接聽程式可能發生問題。</span><span class="sxs-lookup"><span data-stu-id="59c81-118">Indicates that there is a possible problem with the I/O Completion Port Listener on the specified node when executing the I/O Completion routine for a network read/write event.</span></span> <span data-ttu-id="59c81-119">當 I/O 完成通訊埠接聽程式從執行 I/O 完成常式返回時，這個錯誤就會消失。</span><span class="sxs-lookup"><span data-stu-id="59c81-119">This error will go away when the I/O Completion Port Listener returns from executing the I/O Completion routine.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="59c81-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="59c81-120">User Action</span></span>  
 <span data-ttu-id="59c81-121">請連絡 Microsoft 客戶支援服務 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="59c81-121">Contact Microsoft Customer Support Services (CSS).</span></span>  
  
  
