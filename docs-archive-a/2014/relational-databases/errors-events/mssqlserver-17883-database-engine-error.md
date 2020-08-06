---
title: MSSQLSERVER_17883 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46488fb6f7adac2c1109871f2aad4c79352829ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687925"
---
# <a name="mssqlserver_17883"></a><span data-ttu-id="77d84-102">MSSQLSERVER_17883</span><span class="sxs-lookup"><span data-stu-id="77d84-102">MSSQLSERVER_17883</span></span>
    
## <a name="details"></a><span data-ttu-id="77d84-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="77d84-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77d84-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="77d84-104">Product Name</span></span>|<span data-ttu-id="77d84-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="77d84-105">SQL Server</span></span>|  
|<span data-ttu-id="77d84-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="77d84-106">Event ID</span></span>|<span data-ttu-id="77d84-107">17883</span><span class="sxs-lookup"><span data-stu-id="77d84-107">17883</span></span>|  
|<span data-ttu-id="77d84-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="77d84-108">Event Source</span></span>|<span data-ttu-id="77d84-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="77d84-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="77d84-110">元件</span><span class="sxs-lookup"><span data-stu-id="77d84-110">Component</span></span>|<span data-ttu-id="77d84-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="77d84-111">SQLEngine</span></span>|  
|<span data-ttu-id="77d84-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="77d84-112">Symbolic Name</span></span>|<span data-ttu-id="77d84-113">SRV_SCHEDULER_NONYIELDING</span><span class="sxs-lookup"><span data-stu-id="77d84-113">SRV_SCHEDULER_NONYIELDING</span></span>|  
|<span data-ttu-id="77d84-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="77d84-114">Message Text</span></span>|<span data-ttu-id="77d84-115">處理序 %ld:%ld:%ld (0x%lx) 工作者 0x%p 在排程器 %ld 上似乎沒有產量。</span><span class="sxs-lookup"><span data-stu-id="77d84-115">Process %ld:%ld:%ld (0x%lx) Worker 0x%p appears to be non-yielding on Scheduler %ld.</span></span> <span data-ttu-id="77d84-116">執行緒建立時間: %I64d.</span><span class="sxs-lookup"><span data-stu-id="77d84-116">Thread creation time: %I64d.</span></span> <span data-ttu-id="77d84-117">已使用的約略執行緒 CPU：核心 %I64d ms，使用者 %I64d ms。</span><span class="sxs-lookup"><span data-stu-id="77d84-117">Approx Thread CPU Used: kernel %I64d ms, user %I64d ms.</span></span> <span data-ttu-id="77d84-118">處理序使用情形 %d%%。</span><span class="sxs-lookup"><span data-stu-id="77d84-118">Process Utilization %d%%.</span></span> <span data-ttu-id="77d84-119">系統閒置率 %d%%。</span><span class="sxs-lookup"><span data-stu-id="77d84-119">System Idle %d%%.</span></span> <span data-ttu-id="77d84-120">間隔: %I64d 毫秒。</span><span class="sxs-lookup"><span data-stu-id="77d84-120">Interval: %I64d ms.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="77d84-121">說明</span><span class="sxs-lookup"><span data-stu-id="77d84-121">Explanation</span></span>  
 <span data-ttu-id="77d84-122">表示執行緒在排程器上沒有任何產量可能有問題。</span><span class="sxs-lookup"><span data-stu-id="77d84-122">Indicates that there is a possible problem with a thread not yielding on a scheduler.</span></span>  <span data-ttu-id="77d84-123">這個問題可能是由於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的錯誤或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 沒有取得足夠的循環可執行所造成。</span><span class="sxs-lookup"><span data-stu-id="77d84-123">This could be caused by a bug in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is not getting enough cycles to execute.</span></span>  <span data-ttu-id="77d84-124">如果執行緒最後有產量，這個錯誤就可能會消失。</span><span class="sxs-lookup"><span data-stu-id="77d84-124">This error could go away if the thread eventually yields.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="77d84-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="77d84-125">User Action</span></span>  
 <span data-ttu-id="77d84-126">如果系統負載過大，請減少負載，否則請連絡 Microsoft 客戶支援服務。</span><span class="sxs-lookup"><span data-stu-id="77d84-126">If excessive load on system reduce load otherwise contact Microsoft Customer Support Services.</span></span>  
  
  
