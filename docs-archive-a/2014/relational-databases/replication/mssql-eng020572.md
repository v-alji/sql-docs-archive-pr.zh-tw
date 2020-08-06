---
title: MSSQL_ENG020572 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5762f160e119012f4fdc0ca1a205ba0ecf690378
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606789"
---
# <a name="mssql_eng020572"></a><span data-ttu-id="66ba1-102">MSSQL_ENG020572</span><span class="sxs-lookup"><span data-stu-id="66ba1-102">MSSQL_ENG020572</span></span>
    
## <a name="message-details"></a><span data-ttu-id="66ba1-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="66ba1-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66ba1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="66ba1-104">Product Name</span></span>|<span data-ttu-id="66ba1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="66ba1-105">SQL Server</span></span>|  
|<span data-ttu-id="66ba1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="66ba1-106">Event ID</span></span>|<span data-ttu-id="66ba1-107">20572</span><span class="sxs-lookup"><span data-stu-id="66ba1-107">20572</span></span>|  
|<span data-ttu-id="66ba1-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="66ba1-108">Event Source</span></span>|<span data-ttu-id="66ba1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="66ba1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="66ba1-110">元件</span><span class="sxs-lookup"><span data-stu-id="66ba1-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="66ba1-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="66ba1-111">Symbolic Name</span></span>||  
|<span data-ttu-id="66ba1-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="66ba1-112">Message Text</span></span>|<span data-ttu-id="66ba1-113">訂閱者 '%s' 訂閱的發行項 '%s' (在發行集 '%s' 中)，已經在驗證失敗後重新初始化。</span><span class="sxs-lookup"><span data-stu-id="66ba1-113">Subscriber '%s' subscription to article '%s' in publication '%s' has been reinitialized after a validation failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="66ba1-114">說明</span><span class="sxs-lookup"><span data-stu-id="66ba1-114">Explanation</span></span>  
 <span data-ttu-id="66ba1-115">訂閱者端的資料是依據發行者端的資料進行驗證，而資料不相符，因此驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="66ba1-115">The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed.</span></span> <span data-ttu-id="66ba1-116">在指定應該執行驗證時，您選取了如果驗證失敗則訂閱應該重新初始化的選項。</span><span class="sxs-lookup"><span data-stu-id="66ba1-116">When you specified that validation should be performed, you selected the option that a subscription should be reinitialized if validation failed.</span></span> <span data-ttu-id="66ba1-117">重新初始化訂閱涉及了在訂閱者端套用新的快照集。</span><span class="sxs-lookup"><span data-stu-id="66ba1-117">Reinitializing a subscription involves applying a new snapshot at the Subscriber.</span></span> <span data-ttu-id="66ba1-118">如需驗證的相關資訊，請參閱 [Validate Replicated Data](validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="66ba1-118">For more information about validation, see [Validate Replicated Data](validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="66ba1-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="66ba1-119">User Action</span></span>  
 <span data-ttu-id="66ba1-120">在訂閱者端套用新快照集之後，發行者端和訂閱者端的資料將會相符。</span><span class="sxs-lookup"><span data-stu-id="66ba1-120">Data at the Publisher and Subscriber will match after the new snapshot is applied at the Subscriber.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ba1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66ba1-121">See Also</span></span>  
 [<span data-ttu-id="66ba1-122">錯誤和事件參考 &#40;複寫&#41;</span><span class="sxs-lookup"><span data-stu-id="66ba1-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
