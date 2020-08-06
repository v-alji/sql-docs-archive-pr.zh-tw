---
title: 支援本機交易 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: rothja
ms.author: jroth
ms.openlocfilehash: a9bc11a038e56517aa42619117c371c1319b9ffe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598826"
---
# <a name="supporting-local-transactions"></a><span data-ttu-id="38808-102">支援本機交易</span><span class="sxs-lookup"><span data-stu-id="38808-102">Supporting Local Transactions</span></span>
  <span data-ttu-id="38808-103">會話會分隔 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者本機交易的交易範圍。</span><span class="sxs-lookup"><span data-stu-id="38808-103">A session delimits transaction scope for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider local transaction.</span></span> <span data-ttu-id="38808-104">當取用者的方向， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 提供者將要求提交至已連接的實例時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，此要求會構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native client OLE DB 提供者的工作單位。</span><span class="sxs-lookup"><span data-stu-id="38808-104">When, at the direction of a consumer, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider submits a request to a connected instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the request constitutes a unit of work for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="38808-105">本機交易永遠會在單一 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會話上包裝一或多個工作單位。</span><span class="sxs-lookup"><span data-stu-id="38808-105">Local transactions always wrap one or more units of work on a single [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider session.</span></span>  
  
 <span data-ttu-id="38808-106">使用預設的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者自動認可模式時，會將單一工作單位視為本機交易的範圍。</span><span class="sxs-lookup"><span data-stu-id="38808-106">Using the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider autocommit mode, a single unit of work is treated as the scope of a local transaction.</span></span> <span data-ttu-id="38808-107">只有一個單位會參與本機交易。</span><span class="sxs-lookup"><span data-stu-id="38808-107">Only one unit participates in the local transaction.</span></span> <span data-ttu-id="38808-108">建立會話時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會開始會話的交易。</span><span class="sxs-lookup"><span data-stu-id="38808-108">When a session is created, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a transaction for the session.</span></span> <span data-ttu-id="38808-109">成功完成工作單位之後，就會認可該工作。</span><span class="sxs-lookup"><span data-stu-id="38808-109">Upon successful completion of a work unit, the work is committed.</span></span> <span data-ttu-id="38808-110">失敗時，系統會回復開始的任何工作，而且會將錯誤回報給取用者。</span><span class="sxs-lookup"><span data-stu-id="38808-110">On failure, any work begun is rolled back and the error is reported to the consumer.</span></span> <span data-ttu-id="38808-111">不論是哪一種情況， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者都會針對會話開始新的本機交易，讓所有工作都在交易內進行。</span><span class="sxs-lookup"><span data-stu-id="38808-111">In either case, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider begins a new local transaction for the session so that all work is conducted within a transaction.</span></span>  
  
 <span data-ttu-id="38808-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者取用者可以使用**ITransactionLocal**介面，直接對本機交易範圍進行更精確的控制。</span><span class="sxs-lookup"><span data-stu-id="38808-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer can direct more precise control over local transaction scope by using the **ITransactionLocal** interface.</span></span> <span data-ttu-id="38808-113">當取用者工作階段起始交易時，交易起始點和最終的 **Commit** 或 **Abort** 方法呼叫之間的所有工作階段工作單位都會視為一個不可部分完成的單位。</span><span class="sxs-lookup"><span data-stu-id="38808-113">When a consumer session initiates a transaction, all session work units between the transaction start point and the eventual **Commit** or **Abort** method calls are treated as an atomic unit.</span></span> <span data-ttu-id="38808-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會在用戶端導向執行此動作時，隱含地開始交易。</span><span class="sxs-lookup"><span data-stu-id="38808-114">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implicitly begins a transaction when directed to do so by the consumer.</span></span> <span data-ttu-id="38808-115">如果取用者不要求保留，工作階段會還原到父交易層級的行為，也就是最常見的自動認可模式。</span><span class="sxs-lookup"><span data-stu-id="38808-115">If the consumer does not request retention, the session reverts to parent transaction-level behavior, most commonly autocommit mode.</span></span>  
  
 <span data-ttu-id="38808-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援**ITransactionLocal：： StartTransaction**參數，如下所示。</span><span class="sxs-lookup"><span data-stu-id="38808-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ITransactionLocal::StartTransaction** parameters as follows.</span></span>  
  
|<span data-ttu-id="38808-117">參數</span><span class="sxs-lookup"><span data-stu-id="38808-117">Parameter</span></span>|<span data-ttu-id="38808-118">描述</span><span class="sxs-lookup"><span data-stu-id="38808-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38808-119">*isoLevel*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-119">*isoLevel*[in]</span></span>|<span data-ttu-id="38808-120">與此交易搭配使用的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="38808-120">The isolation level to be used with this transaction.</span></span> <span data-ttu-id="38808-121">在本機交易中， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者支援下列各項：</span><span class="sxs-lookup"><span data-stu-id="38808-121">In local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports the following:</span></span><br /><br /> <span data-ttu-id="38808-122">-ISOLATIONLEVEL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="38808-122">-   ISOLATIONLEVEL_UNSPECIFIED</span></span><br /><span data-ttu-id="38808-123">-ISOLATIONLEVEL_CHAOS</span><span class="sxs-lookup"><span data-stu-id="38808-123">-   ISOLATIONLEVEL_CHAOS</span></span><br /><span data-ttu-id="38808-124">-ISOLATIONLEVEL_READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="38808-124">-   ISOLATIONLEVEL_READUNCOMMITTED</span></span><br /><span data-ttu-id="38808-125">-ISOLATIONLEVEL_READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="38808-125">-   ISOLATIONLEVEL_READCOMMITTED</span></span><br /><span data-ttu-id="38808-126">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="38808-126">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="38808-127">-ISOLATIONLEVEL_CURSORSTABILITY</span><span class="sxs-lookup"><span data-stu-id="38808-127">-   ISOLATIONLEVEL_CURSORSTABILITY</span></span><br /><span data-ttu-id="38808-128">-ISOLATIONLEVEL_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="38808-128">-   ISOLATIONLEVEL_REPEATABLEREAD</span></span><br /><span data-ttu-id="38808-129">-ISOLATIONLEVEL_SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="38808-129">-   ISOLATIONLEVEL_SERIALIZABLE</span></span><br /><span data-ttu-id="38808-130">-ISOLATIONLEVEL_ISOLATED</span><span class="sxs-lookup"><span data-stu-id="38808-130">-   ISOLATIONLEVEL_ISOLATED</span></span><br /><span data-ttu-id="38808-131">-ISOLATIONLEVEL_SNAPSHOT**注意：** 從開始 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，ISOLATIONLEVEL_SNAPSHOT 適用于*isoLevel*引數，不論是否已針對資料庫啟用版本控制。</span><span class="sxs-lookup"><span data-stu-id="38808-131">-   ISOLATIONLEVEL_SNAPSHOT **Note:**  Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], ISOLATIONLEVEL_SNAPSHOT is valid for the *isoLevel* argument whether or not versioning is enabled for the database.</span></span> <span data-ttu-id="38808-132">不過，如果使用者嘗試執行執行陳述式，而未啟用版本控制且/或資料庫不是唯讀的，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="38808-132">However, an error will occur if the user attempts to execute a statement and versioning is not enabled and/or the database is not read-only.</span></span> <span data-ttu-id="38808-133">此外，如果在連接到早於 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本時，將 ISOLATIONLEVEL_SNAPSHOT 指定為 *isoLevel*，則會發生 XACT_E_ISOLATIONLEVEL 錯誤。</span><span class="sxs-lookup"><span data-stu-id="38808-133">In addition, the error XACT_E_ISOLATIONLEVEL will occur if ISOLATIONLEVEL_SNAPSHOT is specified as the *isoLevel* when connected to a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>|  
|<span data-ttu-id="38808-134">*isoFlags*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-134">*isoFlags*[in]</span></span>|<span data-ttu-id="38808-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會針對零以外的任何值傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="38808-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns an error for any value other than zero.</span></span>|  
|<span data-ttu-id="38808-136">*pOtherOptions*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-136">*pOtherOptions*[in]</span></span>|<span data-ttu-id="38808-137">如果不是 Null， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會向介面要求 options 物件。</span><span class="sxs-lookup"><span data-stu-id="38808-137">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider requests the options object from the interface.</span></span> <span data-ttu-id="38808-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果 options 物件的*ulTimeout*成員不是零，Native Client OLE DB 提供者會傳回 XACT_E_NOTIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="38808-138">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTIMEOUT if the options object's *ulTimeout* member is not zero.</span></span> <span data-ttu-id="38808-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會忽略*szDescription*成員的值。</span><span class="sxs-lookup"><span data-stu-id="38808-139">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider ignores the value of the *szDescription* member.</span></span>|  
|<span data-ttu-id="38808-140">*pulTransactionLevel*[out]</span><span class="sxs-lookup"><span data-stu-id="38808-140">*pulTransactionLevel*[out]</span></span>|<span data-ttu-id="38808-141">如果不是 Null， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會傳回交易的嵌套層級。</span><span class="sxs-lookup"><span data-stu-id="38808-141">If not NULL, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns the nested level of the transaction.</span></span>|  
  
 <span data-ttu-id="38808-142">若是本機交易， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會依照下列方式來執行**ITransaction：： Abort**參數。</span><span class="sxs-lookup"><span data-stu-id="38808-142">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Abort** parameters as follows.</span></span>  
  
|<span data-ttu-id="38808-143">參數</span><span class="sxs-lookup"><span data-stu-id="38808-143">Parameter</span></span>|<span data-ttu-id="38808-144">描述</span><span class="sxs-lookup"><span data-stu-id="38808-144">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38808-145">*pboidReason*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-145">*pboidReason*[in]</span></span>|<span data-ttu-id="38808-146">如果設定，則略過。</span><span class="sxs-lookup"><span data-stu-id="38808-146">Ignored if set.</span></span> <span data-ttu-id="38808-147">可以安全地成為 NULL。</span><span class="sxs-lookup"><span data-stu-id="38808-147">Can safely be NULL.</span></span>|  
|<span data-ttu-id="38808-148">*fRetaining*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-148">*fRetaining*[in]</span></span>|<span data-ttu-id="38808-149">當為 TRUE 時，就會針對工作階段隱含地開始新的交易。</span><span class="sxs-lookup"><span data-stu-id="38808-149">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="38808-150">此交易必須由取用者認可或結束。</span><span class="sxs-lookup"><span data-stu-id="38808-150">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="38808-151">若為 FALSE， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會還原為會話的自動認可模式。</span><span class="sxs-lookup"><span data-stu-id="38808-151">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="38808-152">*fAsync*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-152">*fAsync*[in]</span></span>|<span data-ttu-id="38808-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者不支援非同步中止。</span><span class="sxs-lookup"><span data-stu-id="38808-153">Asynchronous abort is not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="38808-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]如果值不是 FALSE，Native Client OLE DB 提供者會傳回 XACT_E_NOTSUPPORTED。</span><span class="sxs-lookup"><span data-stu-id="38808-154">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED if the value is not FALSE.</span></span>|  
  
 <span data-ttu-id="38808-155">若是本機交易， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會依照下列方式來執行**ITransaction：： Commit**參數。</span><span class="sxs-lookup"><span data-stu-id="38808-155">For local transactions, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider implements **ITransaction::Commit** parameters as follows.</span></span>  
  
|<span data-ttu-id="38808-156">參數</span><span class="sxs-lookup"><span data-stu-id="38808-156">Parameter</span></span>|<span data-ttu-id="38808-157">描述</span><span class="sxs-lookup"><span data-stu-id="38808-157">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38808-158">*fRetaining*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-158">*fRetaining*[in]</span></span>|<span data-ttu-id="38808-159">當為 TRUE 時，就會針對工作階段隱含地開始新的交易。</span><span class="sxs-lookup"><span data-stu-id="38808-159">When TRUE, a new transaction is implicitly begun for the session.</span></span> <span data-ttu-id="38808-160">此交易必須由取用者認可或結束。</span><span class="sxs-lookup"><span data-stu-id="38808-160">The transaction must be committed or terminated by the consumer.</span></span> <span data-ttu-id="38808-161">若為 FALSE， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會還原為會話的自動認可模式。</span><span class="sxs-lookup"><span data-stu-id="38808-161">When FALSE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reverts to autocommit mode for the session.</span></span>|  
|<span data-ttu-id="38808-162">*grfTC*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-162">*grfTC*[in]</span></span>|<span data-ttu-id="38808-163">Native Client OLE DB 提供者不支援非同步和第一階段傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="38808-163">Asynchronous and phase one returns are not supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span> <span data-ttu-id="38808-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會針對 XACTTC_SYNC 以外的任何值傳回 XACT_E_NOTSUPPORTED。</span><span class="sxs-lookup"><span data-stu-id="38808-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns XACT_E_NOTSUPPORTED for any value other than XACTTC_SYNC.</span></span>|  
|<span data-ttu-id="38808-165">*grfRM*[in]</span><span class="sxs-lookup"><span data-stu-id="38808-165">*grfRM*[in]</span></span>|<span data-ttu-id="38808-166">必須是 0。</span><span class="sxs-lookup"><span data-stu-id="38808-166">Must be 0.</span></span>|  
  
 <span data-ttu-id="38808-167">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]系統會根據資料列集屬性 DBPROP_ABORTPRESERVE 和 DBPROP_COMMITPRESERVE 的值，將會話上的 Native Client OLE DB 提供者資料列集保留在本機認可或中止作業上。</span><span class="sxs-lookup"><span data-stu-id="38808-167">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are preserved on a local commit or abort operation based on the values of the rowset properties DBPROP_ABORTPRESERVE and DBPROP_COMMITPRESERVE.</span></span> <span data-ttu-id="38808-168">根據預設，這些屬性都 VARIANT_FALSE，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會話上的所有 Native Client OLE DB 提供者資料列集會在中止或認可作業之後遺失。</span><span class="sxs-lookup"><span data-stu-id="38808-168">By default, these properties are both VARIANT_FALSE and all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets on the session are lost following an abort or commit operation.</span></span>  
  
 <span data-ttu-id="38808-169">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者不會執行**ITransactionObject**介面。</span><span class="sxs-lookup"><span data-stu-id="38808-169">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not implement the **ITransactionObject** interface.</span></span> <span data-ttu-id="38808-170">取用者在介面上擷取參考的嘗試會傳回 E_NOINTERFACE。</span><span class="sxs-lookup"><span data-stu-id="38808-170">A consumer attempt to retrieve a reference on the interface returns E_NOINTERFACE.</span></span>  
  
 <span data-ttu-id="38808-171">此範例會使用 **ITransactionLocal**。</span><span class="sxs-lookup"><span data-stu-id="38808-171">This example uses **ITransactionLocal**.</span></span>  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
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
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a><span data-ttu-id="38808-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38808-172">See Also</span></span>  
 <span data-ttu-id="38808-173">[交易](transactions.md) </span><span class="sxs-lookup"><span data-stu-id="38808-173">[Transactions](transactions.md) </span></span>  
 [<span data-ttu-id="38808-174">使用快照集隔離</span><span class="sxs-lookup"><span data-stu-id="38808-174">Working with Snapshot Isolation</span></span>](../native-client/features/working-with-snapshot-isolation.md)  
  
  
