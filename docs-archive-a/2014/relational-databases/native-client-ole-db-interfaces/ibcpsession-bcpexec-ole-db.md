---
title: IBCPSession::BCPExec (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPExec (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
author: rothja
ms.author: jroth
ms.openlocfilehash: 1452888e046b6223c64a6cdf6fe09b074b815702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687842"
---
# <a name="ibcpsessionbcpexec-ole-db"></a><span data-ttu-id="46220-102">IBCPSession::BCPExec (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="46220-102">IBCPSession::BCPExec (OLE DB)</span></span>
  <span data-ttu-id="46220-103">執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="46220-103">Performs the bulk copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46220-104">語法</span><span class="sxs-lookup"><span data-stu-id="46220-104">Syntax</span></span>  
  
```  
  
HRESULT BCPExec(   
DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a><span data-ttu-id="46220-105">備註</span><span class="sxs-lookup"><span data-stu-id="46220-105">Remarks</span></span>  
 <span data-ttu-id="46220-106">根據與 [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) 方法搭配使用之 *eDirection* 參數的值，**BCPExec** 方法會將資料從使用者檔案複製到資料庫資料表，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="46220-106">The **BCPExec** method copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter used with the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="46220-107">呼叫 **BCPExec** 之前，請使用有效的使用者檔案名稱來呼叫 **BCPInit** 方法。</span><span class="sxs-lookup"><span data-stu-id="46220-107">Before calling **BCPExec**, call the **BCPInit** method with a valid user file name.</span></span> <span data-ttu-id="46220-108">無法執行這項操作時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="46220-108">Failure to do so results in an error.</span></span> <span data-ttu-id="46220-109">唯一的例外狀況是針對大量複製輸出作業使用查詢。</span><span class="sxs-lookup"><span data-stu-id="46220-109">The only exception is if a query is to be used for a bulk copy out operation.</span></span> <span data-ttu-id="46220-110">在該情況下，請針對 **BCPInit** 方法中的資料表名稱指定 NULL，然後使用 BCP_OPTION_HINTS 選項來指定查詢。</span><span class="sxs-lookup"><span data-stu-id="46220-110">In that case specify NULL for the table name in the **BCPInit** method and then specify the query using the BCP_OPTION_HINTS option.</span></span>  
  
 <span data-ttu-id="46220-111">**BCPExec** 方法是唯一可能持續任何時間長度的大量複製方法。</span><span class="sxs-lookup"><span data-stu-id="46220-111">The **BCPExec** method is the only bulk copy method that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="46220-112">因此，它是唯一支援非同步模式的大量複製方法。</span><span class="sxs-lookup"><span data-stu-id="46220-112">It is therefore the only bulk copy method that supports asynchronous mode.</span></span> <span data-ttu-id="46220-113">若要使用非同步模式，請在呼叫**BCPExec**方法之前，將提供者特定的會話屬性 SSPROP_ASYNCH_BULKCOPY 設定為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="46220-113">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the **BCPExec** method.</span></span> <span data-ttu-id="46220-114">DBPROPSET_SQLSERVERSESSION 屬性集中有提供這個屬性。</span><span class="sxs-lookup"><span data-stu-id="46220-114">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span> <span data-ttu-id="46220-115">若要測試是否完成，請使用相同的參數來呼叫 **BCPExec** 方法。</span><span class="sxs-lookup"><span data-stu-id="46220-115">To test for completion, call the **BCPExec** method with the same parameters.</span></span> <span data-ttu-id="46220-116">如果大量複製尚未完成，**BCPExec** 方法就會傳回 DB_S_ASYNCHRONOUS。</span><span class="sxs-lookup"><span data-stu-id="46220-116">If the bulk copy has not yet completed, the **BCPExec** method returns DB_S_ASYNCHRONOUS.</span></span> <span data-ttu-id="46220-117">它也會在 *pRowsCopied* 引數中傳回已經傳送至伺服器或從伺服器接收之資料列數目的狀態計數。</span><span class="sxs-lookup"><span data-stu-id="46220-117">It also returns in the *pRowsCopied* argument a status count of the number of rows that have been sent to or received from the server.</span></span> <span data-ttu-id="46220-118">到達批次的結尾之前，不會認可傳送至伺服器的資料列。</span><span class="sxs-lookup"><span data-stu-id="46220-118">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="46220-119">引數</span><span class="sxs-lookup"><span data-stu-id="46220-119">Arguments</span></span>  
 <span data-ttu-id="46220-120">*pRowsCopied*[out]</span><span class="sxs-lookup"><span data-stu-id="46220-120">*pRowsCopied*[out]</span></span>  
 <span data-ttu-id="46220-121">DWORD 的指標。</span><span class="sxs-lookup"><span data-stu-id="46220-121">A pointer to a DWORD.</span></span> <span data-ttu-id="46220-122">**BCPExec** 方法會將成功複製的資料列數目填入 DWORD。</span><span class="sxs-lookup"><span data-stu-id="46220-122">The **BCPExec** method fills the DWORD with the number of rows successfully copied.</span></span> <span data-ttu-id="46220-123">如果 *pRowsCopied* 引數設定為 NULL，**BCPExec** 方法就會忽略此引數。</span><span class="sxs-lookup"><span data-stu-id="46220-123">If the *pRowsCopied* argument is set to NULL, it is ignored by the **BCPExec** method.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="46220-124">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="46220-124">Return Code Values</span></span>  
 <span data-ttu-id="46220-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="46220-125">S_OK</span></span>  
 <span data-ttu-id="46220-126">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="46220-126">The method succeeded.</span></span>  
  
 <span data-ttu-id="46220-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="46220-127">E_FAIL</span></span>  
 <span data-ttu-id="46220-128">發生提供者特定的錯誤;如需詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。</span><span class="sxs-lookup"><span data-stu-id="46220-128">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="46220-129">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="46220-129">E_UNEXPECTED</span></span>  
 <span data-ttu-id="46220-130">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="46220-130">The call to the method was unexpected.</span></span> <span data-ttu-id="46220-131">例如，在呼叫這個方法之前，不會呼叫 **BCPInit** 方法。</span><span class="sxs-lookup"><span data-stu-id="46220-131">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="46220-132">此外，如果已經透過使用 BCP_OPTION_ABORT 選項來中止此作業，之後再呼叫 **BCPExec** 方法，也會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="46220-132">Also occurs if the operation has been aborted through using the BCP_OPTION_ABORT option, and the **BCPExec** method was called afterwards.</span></span>  
  
 <span data-ttu-id="46220-133">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="46220-133">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="46220-134">記憶體不足錯誤</span><span class="sxs-lookup"><span data-stu-id="46220-134">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="46220-135">DB_S_ENDOFROWSET</span><span class="sxs-lookup"><span data-stu-id="46220-135">DB_S_ENDOFROWSET</span></span>  
 <span data-ttu-id="46220-136">大量複製作業已完成，而且所有資料傳送都已完成。</span><span class="sxs-lookup"><span data-stu-id="46220-136">The bulk copy operation finished, and all the data transfer was completed.</span></span>  
  
 <span data-ttu-id="46220-137">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="46220-137">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="46220-138">已經複製目前的資料列批次。</span><span class="sxs-lookup"><span data-stu-id="46220-138">The current batch of rows has been copied.</span></span> <span data-ttu-id="46220-139">請再次呼叫 **BCPExec** 方法來傳送下一個批次。</span><span class="sxs-lookup"><span data-stu-id="46220-139">Call the **BCPExec** method again to transfer the next batch.</span></span>  
  
 <span data-ttu-id="46220-140">DB_S_ERRORSOCCURRED</span><span class="sxs-lookup"><span data-stu-id="46220-140">DB_S_ERRORSOCCURRED</span></span>  
 <span data-ttu-id="46220-141">在大量複製作業期間發生了錯誤，而且可能尚未複製某些資料列。</span><span class="sxs-lookup"><span data-stu-id="46220-141">Errors occurred during the bulk copy operation, and some rows might not have been copied.</span></span> <span data-ttu-id="46220-142">錯誤數目仍然少於允許的最大錯誤。</span><span class="sxs-lookup"><span data-stu-id="46220-142">The number of errors is still less than the maximum errors allowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46220-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46220-143">See Also</span></span>  
 <span data-ttu-id="46220-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="46220-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="46220-145">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="46220-145">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
