---
title: MSSQLSERVER_1205 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1205 (Database Engine error)
ms.assetid: 9fe3f67c-df3c-4642-a3a4-ccc0e138b632
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b6afa81a05eea37bc67cd2e9ac2433b6c82f35b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584557"
---
# <a name="mssqlserver_1205"></a><span data-ttu-id="8a8d6-102">MSSQLSERVER_1205</span><span class="sxs-lookup"><span data-stu-id="8a8d6-102">MSSQLSERVER_1205</span></span>
    
## <a name="details"></a><span data-ttu-id="8a8d6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8a8d6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a8d6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8a8d6-104">Product Name</span></span>|<span data-ttu-id="8a8d6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8a8d6-105">SQL Server</span></span>|  
|<span data-ttu-id="8a8d6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8a8d6-106">Event ID</span></span>|<span data-ttu-id="8a8d6-107">1205</span><span class="sxs-lookup"><span data-stu-id="8a8d6-107">1205</span></span>|  
|<span data-ttu-id="8a8d6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8a8d6-108">Event Source</span></span>|<span data-ttu-id="8a8d6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8a8d6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8a8d6-110">元件</span><span class="sxs-lookup"><span data-stu-id="8a8d6-110">Component</span></span>|<span data-ttu-id="8a8d6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8a8d6-111">SQLEngine</span></span>|  
|<span data-ttu-id="8a8d6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8a8d6-112">Symbolic Name</span></span>|<span data-ttu-id="8a8d6-113">LK_VICTIM</span><span class="sxs-lookup"><span data-stu-id="8a8d6-113">LK_VICTIM</span></span>|  
|<span data-ttu-id="8a8d6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8a8d6-114">Message Text</span></span>|<span data-ttu-id="8a8d6-115">交易 (處理序識別碼 %d) 在 %.\*ls 資源上被另一個處理序鎖死，並已被選為死結的犧牲者。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-115">Transaction (Process ID %d) was deadlocked on %.\*ls resources with another process and has been chosen as the deadlock victim.</span></span> <span data-ttu-id="8a8d6-116">請重新執行該交易。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-116">Rerun the transaction.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8a8d6-117">說明</span><span class="sxs-lookup"><span data-stu-id="8a8d6-117">Explanation</span></span>  
 <span data-ttu-id="8a8d6-118">在不同交易上以衝突的順序存取資源，而導致鎖死。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-118">Resources are accessed in conflicting order on separate transactions, causing a deadlock.</span></span> <span data-ttu-id="8a8d6-119">例如：</span><span class="sxs-lookup"><span data-stu-id="8a8d6-119">For example:</span></span>  
  
-   <span data-ttu-id="8a8d6-120">Transaction1 會更新 **Table1.Row1**，而 Transaction2 會更新 **Table2.Row2**。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-120">Transaction1 updates **Table1.Row1**, while Transaction2 updates **Table2.Row2**.</span></span>  
  
-   <span data-ttu-id="8a8d6-121">Transaction1 會嘗試更新 **Table2.Row2**，但是卻因為 Transaction2 尚未獲得認可而遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-121">Transaction1 tries to update **Table2.Row2** but is blocked because Transaction2 has not yet committed.</span></span>  
  
-   <span data-ttu-id="8a8d6-122">現在 Transaction2 會嘗試更新 **Table1.Row1**，但是因為 Transaction1 尚未獲得認可而遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-122">Transaction2 now tries to update **Table1.Row1** but is blocked because Transaction1 has not committed.</span></span>  
  
-   <span data-ttu-id="8a8d6-123">由於 Transaction1 正在等候 Transaction2 完成執行，而同時 Transaction2 也在等候 Transaction1 執行完成，因此發生死結。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-123">A deadlock occurs because Transaction1 is waiting for Transaction2 to complete, but Transaction2 is waiting for Transaction1 to complete.</span></span>  
  
 <span data-ttu-id="8a8d6-124">系統會偵測到此鎖死情形，並且會選擇其中一個涉及的交易來作為「犠牲者」，並發出此訊息：正在復原犧牲者的交易。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-124">The system will detect this deadlock and will choose one of the transactions involved as a 'victim' and will issue this message, rolling back the victim's transaction.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8a8d6-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8a8d6-125">User Action</span></span>  
 <span data-ttu-id="8a8d6-126">重新執行交易。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-126">Execute the transaction again.</span></span> <span data-ttu-id="8a8d6-127">您也可以修訂應用程式以避免死結。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-127">You can also revise the application to avoid deadlocks.</span></span> <span data-ttu-id="8a8d6-128">您可以重試系統選擇做為犠牲者的交易，而且該交易可能會成功 (依據同時執行的作業而定)。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-128">The transaction that was chosen as a victim can be retried and will likely succeed, depending on what operations are being executed simultaneously.</span></span>  
  
 <span data-ttu-id="8a8d6-129">若要防止或避免發生死結，請考慮讓所有的交易都以相同的順序來存取資料列 (先存取 **Table1**，然後存取 **Table2**)；如此，雖然可能會發生封鎖，但是不會發生死結。</span><span class="sxs-lookup"><span data-stu-id="8a8d6-129">To prevent or avoid deadlocks from occurring, consider having all transactions access rows in the same order (**Table1**, then **Table2**); this way, although blocking might occur, a deadlock will not occur.</span></span>  
  
  
