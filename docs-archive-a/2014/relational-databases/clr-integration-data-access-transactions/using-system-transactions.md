---
title: 使用 System.object |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
author: rothja
ms.author: jroth
ms.openlocfilehash: 277edd75ea0437dc532ed5672e3c7b8a0569af8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709645"
---
# <a name="using-systemtransactions"></a><span data-ttu-id="59c99-102">使用 System.Transactions</span><span class="sxs-lookup"><span data-stu-id="59c99-102">Using System.Transactions</span></span>
  <span data-ttu-id="59c99-103">`System.Transactions` 命名空間會提供與 ADO.NET 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Common Language Runtime (CLR) 整合完全整合的交易架構。</span><span class="sxs-lookup"><span data-stu-id="59c99-103">The `System.Transactions` namespace provides a transaction framework that is fully integrated with ADO.NET and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] common language runtime (CLR) integration.</span></span> <span data-ttu-id="59c99-104">`System.Transactions.TransactionScope` 類別可藉由在分散式交易中隱含地編列連接，讓程式碼區塊可進行交易。</span><span class="sxs-lookup"><span data-stu-id="59c99-104">The `System.Transactions.TransactionScope` class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="59c99-105">您必須呼叫 `Complete` 所標示之程式碼區塊結尾的 `TransactionScope` 方法。</span><span class="sxs-lookup"><span data-stu-id="59c99-105">You must call the `Complete` method at the end of the code block marked by the `TransactionScope`.</span></span> <span data-ttu-id="59c99-106">當程式執行離開程式碼區塊時，會叫用 `Dispose` 方法，如果不呼叫 `Complete` 方法，則會讓交易停止。</span><span class="sxs-lookup"><span data-stu-id="59c99-106">The `Dispose` method is invoked when program execution leaves a code block, causing the transaction to be discontinued if the `Complete` method is not called.</span></span> <span data-ttu-id="59c99-107">如果已擲回造成程式碼離開範圍的例外狀況，則會將交易視為停止。</span><span class="sxs-lookup"><span data-stu-id="59c99-107">If an exception has been thrown that causes the code to leave scope, the transaction is considered to be discontinued.</span></span>  
  
 <span data-ttu-id="59c99-108">建議您使用 `using` 區塊，以確保結束 `Dispose` 區塊時，會在 `TransactionScope` 物件上呼叫 `using` 方法。</span><span class="sxs-lookup"><span data-stu-id="59c99-108">We recommend that you employ a `using` block to ensure that the `Dispose` method is called on the `TransactionScope` object when the `using` block is exited.</span></span> <span data-ttu-id="59c99-109">無法認可或復原暫止的交易可能會使效能嚴重下降，因為 `TransactionScope` 的預設逾時是一分鐘。</span><span class="sxs-lookup"><span data-stu-id="59c99-109">Failure to commit or roll back pending transactions can seriously degrade performance because the default time-out for the `TransactionScope` is one minute.</span></span> <span data-ttu-id="59c99-110">如果您不使用 `using` 陳述式，則必須在 `Try` 區塊中執行所有工作，並明確呼叫 `Dispose` 區塊中的 `Finally` 方法。</span><span class="sxs-lookup"><span data-stu-id="59c99-110">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the `Dispose` method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="59c99-111">如果 `TransactionScope` 中發生例外狀況，則會將交易標記為不一致並放棄。</span><span class="sxs-lookup"><span data-stu-id="59c99-111">If an exception occurs within the `TransactionScope`, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="59c99-112">處置 `TransactionScope` 時，則會復原該交易。</span><span class="sxs-lookup"><span data-stu-id="59c99-112">It is rolled back when the `TransactionScope` is disposed.</span></span> <span data-ttu-id="59c99-113">如果沒有發生任何例外狀況，則會認可參與的交易。</span><span class="sxs-lookup"><span data-stu-id="59c99-113">If no exception occurs, participating transactions commit.</span></span>  
  
 <span data-ttu-id="59c99-114">只有在存取本機和遠端資料來源或外部資原管理員時，才應該使用 `TransactionScope`。</span><span class="sxs-lookup"><span data-stu-id="59c99-114">`TransactionScope` should be used only when local and remote data sources or external resource managers are being accessed.</span></span> <span data-ttu-id="59c99-115">這是因為即使是在內容連接內使用 `TransactionScope`，還是永遠會使交易升級。</span><span class="sxs-lookup"><span data-stu-id="59c99-115">This is because `TransactionScope` always causes transactions to promote, even if it is being used only within a context connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59c99-116">`TransactionScope` 類別預設會以 `System.Transactions.Transaction.IsolationLevel` 的 `Serializable` 建立交易。</span><span class="sxs-lookup"><span data-stu-id="59c99-116">The `TransactionScope` class creates a transaction with a `System.Transactions.Transaction.IsolationLevel` of `Serializable` by default.</span></span> <span data-ttu-id="59c99-117">根據應用程式，您可能會考慮降低隔離等級，以避免應用程式中發生劇烈的競爭現象。</span><span class="sxs-lookup"><span data-stu-id="59c99-117">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59c99-118">建議您針對遠端伺服器，在分散式交易內僅執行更新、插入及刪除作業，因為它們會耗用大量的資料庫資源。</span><span class="sxs-lookup"><span data-stu-id="59c99-118">We recommend that you perform only updates, inserts, and deletes within distributed transactions against remote servers because they consume significant database resources.</span></span> <span data-ttu-id="59c99-119">如果要在本機伺服器上執行作業，就不需要使用分散式交易，而且本機交易就已經足夠。</span><span class="sxs-lookup"><span data-stu-id="59c99-119">If the operation is going to be performed on the local server, a distributed transaction is not necessary and a local transaction will suffice.</span></span> <span data-ttu-id="59c99-120">SELECT 陳述式可能會不必要地鎖定資料庫資源，而且在某些案例中，可能需要使用交易來進行選取。</span><span class="sxs-lookup"><span data-stu-id="59c99-120">SELECT statements may lock database resources unnecessarily, and in some scenarios it may be necessary to use transactions for selects.</span></span> <span data-ttu-id="59c99-121">除非涉及其他已交易的資源管理者，否則所有非資料庫工作都應在交易範圍外執行。</span><span class="sxs-lookup"><span data-stu-id="59c99-121">Any non-database work should be done outside of the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="59c99-122">雖然交易範圍內的例外狀況會防止認可交易，但 `TransactionScope` 類別不支援針對在交易本身範圍外所做的任何程式碼變更，進行復原。</span><span class="sxs-lookup"><span data-stu-id="59c99-122">Although an exception within the scope of the transaction prevents the transaction from committing, the `TransactionScope` class has no provision for rolling back any changes your code has made outside of the scope of the transaction itself.</span></span> <span data-ttu-id="59c99-123">如果在復原交易時需要採取某些動作，則必須撰寫您自己的 `System.Transactions.IEnlistmentNotification` 介面實作，並在交易中明確編列。</span><span class="sxs-lookup"><span data-stu-id="59c99-123">If you need to take some action when the transaction is rolled back, you must write your own implementation of the `System.Transactions.IEnlistmentNotification` interface, and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59c99-124">範例</span><span class="sxs-lookup"><span data-stu-id="59c99-124">Example</span></span>  
 <span data-ttu-id="59c99-125">若要使用 `System.Transactions`，您必須參考 System.Transactions.dll 檔。</span><span class="sxs-lookup"><span data-stu-id="59c99-125">To work with `System.Transactions`, you must have a reference to the System.Transactions.dll file.</span></span>  
  
 <span data-ttu-id="59c99-126">下列程式碼示範如何針對兩個不同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，建立可以升級的交易。</span><span class="sxs-lookup"><span data-stu-id="59c99-126">The following code demonstrates how to create a transaction that can be promoted against two different instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="59c99-127">這些執行個體會以兩個不同的 `System.Data.SqlClient.SqlConnection` 物件代表，並包裝在 `TransactionScope` 區塊中。</span><span class="sxs-lookup"><span data-stu-id="59c99-127">These instances are represented by two different `System.Data.SqlClient.SqlConnection` objects, which are wrapped in a `TransactionScope` block.</span></span> <span data-ttu-id="59c99-128">程式碼會使用 `TransactionScope` 陳述式來建立 `using` 區塊，並開啟第一個連接，這樣會自動在 `TransactionScope` 中編列它。</span><span class="sxs-lookup"><span data-stu-id="59c99-128">The code creates the `TransactionScope` block with a `using` statement, and opens the first connection, which automatically enlists it in the `TransactionScope`.</span></span> <span data-ttu-id="59c99-129">一開始交易登記為輕量型交易，而不是完全分散式交易。</span><span class="sxs-lookup"><span data-stu-id="59c99-129">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="59c99-130">程式碼假設條件式邏輯存在 (已為了簡潔而省略該條件式邏輯)。</span><span class="sxs-lookup"><span data-stu-id="59c99-130">The code assumes the existence of conditional logic (which has been omitted for brevity).</span></span> <span data-ttu-id="59c99-131">僅當需要時，才會開啟第二個連接，並在 `TransactionScope` 中登記它。</span><span class="sxs-lookup"><span data-stu-id="59c99-131">It opens the second connection only if it is needed, enlisting it in the `TransactionScope`.</span></span> <span data-ttu-id="59c99-132">開啟連接時，交易會自動提升為完全分散式交易。</span><span class="sxs-lookup"><span data-stu-id="59c99-132">When the connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="59c99-133">然後，程式碼會叫用認可交易的 `TransactionScope.Complete`。</span><span class="sxs-lookup"><span data-stu-id="59c99-133">The code then invokes `TransactionScope.Complete`, which commits the transaction.</span></span> <span data-ttu-id="59c99-134">當結束連接的 `using` 陳述式時，程式碼會處置兩個連接。</span><span class="sxs-lookup"><span data-stu-id="59c99-134">The code disposes of the two connections when exiting the `using` statements for the connections.</span></span> <span data-ttu-id="59c99-135">結束 `TransactionScope.Dispose` 的 `TransactionScope` 區塊時，會自動呼叫 `using` 的 `TransactionScope` 方法。</span><span class="sxs-lookup"><span data-stu-id="59c99-135">The `TransactionScope.Dispose` method for the `TransactionScope` is automatically called at the termination of the `using` block for the `TransactionScope`.</span></span> <span data-ttu-id="59c99-136">如果在 `TransactionScope` 區塊中的任何一點擲回例外狀況，便不會呼叫 `Complete`，且分散式交易會在處置 `TransactionScope` 時復原。</span><span class="sxs-lookup"><span data-stu-id="59c99-136">If an exception has been thrown at any point in the `TransactionScope` block, `Complete` does not get called, and the distributed transaction will roll back when the `TransactionScope` is disposed.</span></span>  
  
 <span data-ttu-id="59c99-137">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59c99-137">Visual Basic</span></span>  
  
```  
Using transScope As New TransactionScope()  
    Using connection1 As New SqlConnection(connectString1)  
        ' Opening connection1 automatically enlists it in the   
        ' TransactionScope as a lightweight transaction.  
        connection1.Open()  
  
        ' Do work in the first connection.  
  
        ' Assumes conditional logic in place where the second  
        ' connection will only be opened as needed.  
        Using connection2 As New SqlConnection(connectString2)  
            ' Open the second connection, which enlists the   
            ' second connection and promotes the transaction to  
            ' a full distributed transaction.  
            connection2.Open()  
  
            ' Do work in the second connection.  
  
        End Using  
    End Using  
  
    ' Commit the transaction.  
    transScope.Complete()  
End Using  
```  
  
 <span data-ttu-id="59c99-138">C#</span><span class="sxs-lookup"><span data-stu-id="59c99-138">C#</span></span>  
  
```  
using (TransactionScope transScope = new TransactionScope())  
{  
    using (SqlConnection connection1 = new   
       SqlConnection(connectString1))  
    {  
        // Opening connection1 automatically enlists it in the   
        // TransactionScope as a lightweight transaction.  
        connection1.Open();  
  
        // Do work in the first connection.  
  
        // Assumes conditional logic in place where the second  
        // connection will only be opened as needed.  
        using (SqlConnection connection2 = new   
            SqlConnection(connectString2))  
        {  
            // Open the second connection, which enlists the   
            // second connection and promotes the transaction to  
            // a full distributed transaction.   
            connection2.Open();  
  
            // Do work in the second connection.  
        }  
    }  
    //  The Complete method commits the transaction.  
    transScope.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="59c99-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c99-139">See Also</span></span>  
 [<span data-ttu-id="59c99-140">CLR 整合和交易</span><span class="sxs-lookup"><span data-stu-id="59c99-140">CLR Integration and Transactions</span></span>](../native-client-ole-db-transactions/transactions.md)  
  
  
