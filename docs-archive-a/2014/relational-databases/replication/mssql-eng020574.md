---
title: MSSQL_ENG020574 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e224e9a87d40fa826a05c669216649c45185037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606788"
---
# <a name="mssql_eng020574"></a><span data-ttu-id="a00dc-102">MSSQL_ENG020574</span><span class="sxs-lookup"><span data-stu-id="a00dc-102">MSSQL_ENG020574</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a00dc-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="a00dc-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a00dc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a00dc-104">Product Name</span></span>|<span data-ttu-id="a00dc-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a00dc-105">SQL Server</span></span>|  
|<span data-ttu-id="a00dc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a00dc-106">Event ID</span></span>|<span data-ttu-id="a00dc-107">20574</span><span class="sxs-lookup"><span data-stu-id="a00dc-107">20574</span></span>|  
|<span data-ttu-id="a00dc-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a00dc-108">Event Source</span></span>|<span data-ttu-id="a00dc-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a00dc-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a00dc-110">元件</span><span class="sxs-lookup"><span data-stu-id="a00dc-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a00dc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a00dc-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a00dc-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a00dc-112">Message Text</span></span>|<span data-ttu-id="a00dc-113">訂閱者 '%s' 訂閱的發行項 '%s' (在發行集 '%s' 中)，未通過資料驗證。</span><span class="sxs-lookup"><span data-stu-id="a00dc-113">Subscriber '%s' subscription to article '%s' in publication '%s' failed data validation.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a00dc-114">說明</span><span class="sxs-lookup"><span data-stu-id="a00dc-114">Explanation</span></span>  
 <span data-ttu-id="a00dc-115">訂閱者端的資料是依據發行者端的資料進行驗證，而資料不相符，因此驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="a00dc-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="a00dc-116">如需驗證的相關資訊，請參閱 [Validate Replicated Data](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="a00dc-116">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a00dc-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a00dc-117">User Action</span></span>  
 <span data-ttu-id="a00dc-118">建議您採取下列動作︰</span><span class="sxs-lookup"><span data-stu-id="a00dc-118">We recommend that you do the following:</span></span>  
  
-   <span data-ttu-id="a00dc-119">判斷驗證失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="a00dc-119">Determine why validation failed.</span></span>  
  
-   <span data-ttu-id="a00dc-120">更正導致失敗的根本問題。</span><span class="sxs-lookup"><span data-stu-id="a00dc-120">Correct the underlying issue that caused the failure.</span></span>  
  
-   <span data-ttu-id="a00dc-121">重新初始化訂閱或透過其他方法，讓資料聚合。</span><span class="sxs-lookup"><span data-stu-id="a00dc-121">Bring the data into convergence by reinitializing the subscription or through another method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00dc-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a00dc-122">See Also</span></span>  
 [<span data-ttu-id="a00dc-123">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="a00dc-123">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
