---
title: CLR 整合和交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
ms.openlocfilehash: de72a2113aeb568decbdc9b5ee0174160cc0d3ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709661"
---
# <a name="clr-integration-and-transactions"></a><span data-ttu-id="b80b4-102">CLR 整合和交易</span><span class="sxs-lookup"><span data-stu-id="b80b4-102">CLR Integration and Transactions</span></span>
  <span data-ttu-id="b80b4-103">`System.Transactions` 命名空間會提供與 ADO.NET 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Common Language Runtime (CLR) 整合完全整合的交易架構。</span><span class="sxs-lookup"><span data-stu-id="b80b4-103">The `System.Transactions` namespace provides a transaction framework that is fully integrated with ADO.NET and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language runtime (CLR) integration.</span></span> <span data-ttu-id="b80b4-104">`System.Transactions` 和 ADO.NET 能搭配使用，以擴充並簡化本機和分散式交易在 Managed 應用程式中的使用。</span><span class="sxs-lookup"><span data-stu-id="b80b4-104">`System.Transactions` and ADO.NET work together to extend and simplify the use of local and distributed transactions in managed applications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b80b4-105">CLR 使用者定義程序 (UDP) 不能與執行所在的同一台伺服器建立連接 (回送連接)，也不能編列在相同的交易中。</span><span class="sxs-lookup"><span data-stu-id="b80b4-105">A CLR user-defined procedure (UDP) cannot establish a connection to the same server it is running on (a loopback connection) and enlist in the same transaction.</span></span> <span data-ttu-id="b80b4-106">如果嘗試這麼做，系統就會封鎖連接嘗試，而控制權將不會傳回給 UDP。</span><span class="sxs-lookup"><span data-stu-id="b80b4-106">If this is attempted, the connection attempt will be blocked and control will not be passed back to the UDP.</span></span> <span data-ttu-id="b80b4-107">這樣將導致 UDP 上產生逾時錯誤 (訊息 1206)。</span><span class="sxs-lookup"><span data-stu-id="b80b4-107">This will result in a timeout error (Msg 1206) on the UDP.</span></span>  
  
 <span data-ttu-id="b80b4-108">如需有關交易和 .NET Framework 的詳細資訊，請參閱 .NET Framework SDK 中的＜執行交易＞和＜利用交易＞。</span><span class="sxs-lookup"><span data-stu-id="b80b4-108">For more information about transactions and the .NET Framework, see "Performing Transactions" and "Leveraging Transactions" in the .NET Framework SDK.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b80b4-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="b80b4-109">In This Section</span></span>  
 [<span data-ttu-id="b80b4-110">交易升級</span><span class="sxs-lookup"><span data-stu-id="b80b4-110">Transaction Promotion</span></span>](transaction-promotion.md)  
 <span data-ttu-id="b80b4-111">描述升級交易的功能，以及如何使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="b80b4-111">Describes the ability to promote transactions, and how to use this feature.</span></span>  
  
 [<span data-ttu-id="b80b4-112">存取目前交易</span><span class="sxs-lookup"><span data-stu-id="b80b4-112">Accessing the Current Transaction</span></span>](accessing-the-current-transaction.md)  
 <span data-ttu-id="b80b4-113">描述如何存取目前在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上於同處理序 (In-Process) 中執行的交易。</span><span class="sxs-lookup"><span data-stu-id="b80b4-113">Describes how to access a transaction currently running in-process on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="b80b4-114">使用 System.Transactions</span><span class="sxs-lookup"><span data-stu-id="b80b4-114">Using System.Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
 <span data-ttu-id="b80b4-115">描述如何在 Managed 應用程式中使用 `System.Transactions` 應用程式開發介面 (API)。</span><span class="sxs-lookup"><span data-stu-id="b80b4-115">Describes how to use the `System.Transactions` application programming interface (API) in your managed application.</span></span>  
  
 [<span data-ttu-id="b80b4-116">交易存留期間</span><span class="sxs-lookup"><span data-stu-id="b80b4-116">Transaction Lifetimes</span></span>](transaction-lifetimes.md)  
 <span data-ttu-id="b80b4-117">描述在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序中所啟動的交易和在 CLR 應用程式中所啟動的交易在存留期間上的差異。</span><span class="sxs-lookup"><span data-stu-id="b80b4-117">Describes the difference in lifetime between transactions started in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and transactions started in CLR applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b80b4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b80b4-118">See Also</span></span>  
 [<span data-ttu-id="b80b4-119">從 CLR 資料庫物件進行資料存取</span><span class="sxs-lookup"><span data-stu-id="b80b4-119">Data Access from CLR Database Objects</span></span>](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
