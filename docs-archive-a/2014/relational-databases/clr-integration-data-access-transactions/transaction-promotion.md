---
title: 交易升級 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- distributed transactions [CLR integration]
- promoting transactions [CLR integration]
- Enlist keyword
- transaction promotion [CLR integration]
ms.assetid: 5bc7e26e-28ad-4198-a40d-8b2c648ba304
author: rothja
ms.author: jroth
ms.openlocfilehash: e78cbb3d2fc888e56c0b55780daf7b449fe6dc40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709649"
---
# <a name="transaction-promotion"></a><span data-ttu-id="f2c2d-102">交易升級</span><span class="sxs-lookup"><span data-stu-id="f2c2d-102">Transaction Promotion</span></span>
  <span data-ttu-id="f2c2d-103">交易*升級*描述輕量的本機交易，可以視需要自動升級為完全可散發的交易。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-103">Transaction *promotion* describes a lightweight, local transaction that can be automatically promoted to a fully distributable transaction as needed.</span></span> <span data-ttu-id="f2c2d-104">當 Managed 預存程序在伺服器的資料庫交易內叫用時，Common Language Runtime (CLR) 程式碼會在本機交易的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-104">When a managed stored procedure is invoked within a database transaction on the server, the common language runtime (CLR) code is run in the context of a local transaction.</span></span>  <span data-ttu-id="f2c2d-105">如果遠端伺服器的連接是在交易資料庫內開啟的，則會將遠端伺服器的連接編列至分散式交易，而且會將本機交易自動升級為分散式交易。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-105">If a connection to a remote server is opened within a database transaction, the connection to the remote server is enlisted into the distributed transaction and the local transaction is automatically promoted to a distributed transaction.</span></span> <span data-ttu-id="f2c2d-106">因此，交易升級可以藉由直到需要時才建立分散式交易的方式，將分散式交易的負擔降至最低。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-106">So, transaction promotion minimizes the overhead of distributed transactions by deferring the creation of a distributed transaction until it is needed.</span></span> <span data-ttu-id="f2c2d-107">如果您已經使用 `Enlist` 關鍵字啟用交易升級，則交易升級是自動的，無需開發人員從中操作。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-107">Transaction promotion is automatic, if it has been enabled using the `Enlist` keyword, and does not require intervention from the developer.</span></span> <span data-ttu-id="f2c2d-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 .NET Framework 資料提供者支援交易升級，可透過 .NET Framework `System.Data.SqlClient` 命名空間中的類別來處理。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-108">The .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides support for transaction promotion, handled through the classes in the .NET Framework `System.Data.SqlClient` namespace.</span></span>  
  
## <a name="the-enlist-keyword"></a><span data-ttu-id="f2c2d-109">編列關鍵字</span><span class="sxs-lookup"><span data-stu-id="f2c2d-109">The Enlist Keyword</span></span>  
 <span data-ttu-id="f2c2d-110">`ConnectionString` 物件的 `SqlConnection` 屬性支援 `Enlist` 關鍵字，它表示 `System.Data.SqlClient` 是否會偵測到交易內容，並自動在分散式交易中編列連接。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-110">The `ConnectionString` property of a `SqlConnection` object supports the `Enlist` keyword, which indicates whether `System.Data.SqlClient` detects transactional contexts and automatically enlists the connection in a distributed transaction.</span></span> <span data-ttu-id="f2c2d-111">如果此關鍵字設定為 True (預設值)，則會在開啟之執行緒的目前交易內容中自動編列連接。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-111">If this keyword is set to true (the default), the connection is automatically enlisted in the current transaction context of the opening thread.</span></span> <span data-ttu-id="f2c2d-112">如果此關鍵字設定為 False，則 SqlClient 連接不會與分散式交易進行互動。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-112">If this keyword is set to false, the SqlClient connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="f2c2d-113">如果未在連接字串中指定 `Enlist`，則若在開啟連接時偵測到連接，便會自動在分散式交易中編列該連接。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-113">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected at the time the connection is opened.</span></span>  
  
## <a name="distributed-transactions"></a><span data-ttu-id="f2c2d-114">分散式異動</span><span class="sxs-lookup"><span data-stu-id="f2c2d-114">Distributed Transactions</span></span>  
 <span data-ttu-id="f2c2d-115">分散式交易通常會消耗大量的系統資源。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-115">Distributed transactions typically consume significant system resources.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="f2c2d-116">分散式交易協調器 (MS DTC) 會管理此類交易，並整合在這些交易中存取的所有資源管理員。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-116">Distributed Transaction Coordinator (MS DTC) manages such transactions, and integrates all of the resource managers accessed in these transactions.</span></span> <span data-ttu-id="f2c2d-117">另一方面，交易升級是 `System.Transactions` 交易的特殊形式，可有效地委派工作給簡單的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 交易。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-117">Transaction promotion, on the other hand, is a special form of a `System.Transactions` transaction that effectively delegates the work to a simple [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction.</span></span> <span data-ttu-id="f2c2d-118">`System.Transactions`、`System.Data.SqlClient` 及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會協調處理交易時所涉及的工作，並視需要將其提升為完全分散式交易。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-118">`System.Transactions`, `System.Data.SqlClient`, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="f2c2d-119">使用交易升級的好處是：當以作用中的 `TransactionScope` 交易開啟連接，且未開啟其他連接時，會將交易認可為輕量型交易，不會產生完全分散式交易的額外負擔。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-119">The benefit of using transaction promotion is that when a connection is opened with an active `TransactionScope` transaction, and no other connections are opened, the transaction commits as a lightweight transaction, rather than incurring the additional overhead of a full distributed transaction.</span></span> <span data-ttu-id="f2c2d-120">如需的詳細資訊 `TransactionScope` ，請參閱[使用 System. 交易](../native-client-ole-db-transactions/transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="f2c2d-120">For more information about `TransactionScope`, see [Using System.Transactions](../native-client-ole-db-transactions/transactions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c2d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2c2d-121">See Also</span></span>  
 [<span data-ttu-id="f2c2d-122">CLR 整合和交易</span><span class="sxs-lookup"><span data-stu-id="f2c2d-122">CLR Integration and Transactions</span></span>](clr-integration-and-transactions.md)  
  
  
