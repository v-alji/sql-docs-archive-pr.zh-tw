---
title: 支援分散式交易 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a30a44dc007852922aa71685728b26e5bb872c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706406"
---
# <a name="supporting-distributed-transactions"></a><span data-ttu-id="be740-102">支援分散式交易</span><span class="sxs-lookup"><span data-stu-id="be740-102">Supporting Distributed Transactions</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="be740-103">Native Client OLE DB 提供者取用者可以使用**ITransactionJoin：： JoinTransaction**方法來參與 Microsoft 分散式交易協調器 (MS DTC) 協調的分散式交易。</span><span class="sxs-lookup"><span data-stu-id="be740-103">Native Client OLE DB provider consumers can use the **ITransactionJoin::JoinTransaction** method to participate in a distributed transaction coordinated by Microsoft Distributed Transaction Coordinator (MS DTC).</span></span>  
  
 <span data-ttu-id="be740-104">MS DTC 會公開 COM 物件，讓用戶端跨各種資料存放區的多個連接，起始並參與協調的交易。</span><span class="sxs-lookup"><span data-stu-id="be740-104">MS DTC exposes COM objects that allow clients to initiate and participate in coordinated transactions across multiple connections to a variety of data stores.</span></span> <span data-ttu-id="be740-105">若要起始交易， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者會使用 MS DTC **ITransactionDispenser**介面。</span><span class="sxs-lookup"><span data-stu-id="be740-105">To initiate a transaction, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer uses the MS DTC **ITransactionDispenser** interface.</span></span> <span data-ttu-id="be740-106">**ITransactionDispenser** 的 **BeginTransaction** 成員會傳回分散式交易物件的參考。</span><span class="sxs-lookup"><span data-stu-id="be740-106">The **BeginTransaction** member of **ITransactionDispenser** returns a reference on a distributed transaction object.</span></span> <span data-ttu-id="be740-107">此參考會 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用**JoinTransaction**傳遞至 Native Client OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="be740-107">This reference is passed to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider using **JoinTransaction**.</span></span>  
  
 <span data-ttu-id="be740-108">MS DTC 在分散式交易上支援非同步認可和中止。</span><span class="sxs-lookup"><span data-stu-id="be740-108">MS DTC supports asynchronous commit and abort on distributed transactions.</span></span> <span data-ttu-id="be740-109">為取得非同步交易狀態的通知，取用者會實作 **ITransactionOutcomeEvents** 介面，並將介面連接到 MS DTC 交易物件。</span><span class="sxs-lookup"><span data-stu-id="be740-109">For notification on asynchronous transaction status, the consumer implements the **ITransactionOutcomeEvents** interface and connects the interface to an MS DTC transaction object.</span></span>  
  
 <span data-ttu-id="be740-110">若為分散式交易， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會依照下列方式來執行**ITransactionJoin：： JoinTransaction**參數。</span><span class="sxs-lookup"><span data-stu-id="be740-110">For distributed transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransactionJoin::JoinTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="be740-111">參數</span><span class="sxs-lookup"><span data-stu-id="be740-111">Parameter</span></span>|<span data-ttu-id="be740-112">描述</span><span class="sxs-lookup"><span data-stu-id="be740-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be740-113">*punkTransactionCoord*</span><span class="sxs-lookup"><span data-stu-id="be740-113">*punkTransactionCoord*</span></span>|<span data-ttu-id="be740-114">MS DTC 交易物件的指標。</span><span class="sxs-lookup"><span data-stu-id="be740-114">A pointer to an MS DTC transaction object.</span></span>|  
|<span data-ttu-id="be740-115">*IsoLevel*</span><span class="sxs-lookup"><span data-stu-id="be740-115">*IsoLevel*</span></span>|<span data-ttu-id="be740-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者已忽略。</span><span class="sxs-lookup"><span data-stu-id="be740-116">Ignored by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="be740-117">取用者從 MS DTC 取得交易物件時，會判斷 MS DTC 協調交易的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="be740-117">The isolation level for MS DTC-coordinated transactions is determined when the consumer acquires a transaction object from MS DTC.</span></span>|  
|<span data-ttu-id="be740-118">*IsoFlags*</span><span class="sxs-lookup"><span data-stu-id="be740-118">*IsoFlags*</span></span>|<span data-ttu-id="be740-119">必須是 0。</span><span class="sxs-lookup"><span data-stu-id="be740-119">Must be 0.</span></span> <span data-ttu-id="be740-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果取用者指定了任何其他值，Native Client OLE DB 提供者就會傳回 XACT_E_NOISORETAIN。</span><span class="sxs-lookup"><span data-stu-id="be740-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOISORETAIN if any other value is specified by the consumer.</span></span>|  
|<span data-ttu-id="be740-121">*POtherOptions*</span><span class="sxs-lookup"><span data-stu-id="be740-121">*POtherOptions*</span></span>|<span data-ttu-id="be740-122">如果不是 Null， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會向介面要求 options 物件。</span><span class="sxs-lookup"><span data-stu-id="be740-122">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="be740-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果 options 物件的*ulTimeout*成員不是零，Native Client OLE DB 提供者會傳回 XACT_E_NOTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="be740-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="be740-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會忽略*szDescription*成員的值。</span><span class="sxs-lookup"><span data-stu-id="be740-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
  
 <span data-ttu-id="be740-125">這個範例會使用 MS DTC 協調交易。</span><span class="sxs-lookup"><span data-stu-id="be740-125">This example coordinates transaction by using MS DTC.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="be740-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be740-126">See Also</span></span>  
 [<span data-ttu-id="be740-127">交易</span><span class="sxs-lookup"><span data-stu-id="be740-127">Transactions</span></span>](transactions.md)  
  
  
