---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: rothja
ms.author: jroth
ms.openlocfilehash: 3daad53087c876af8dc46bccc9c4bf7952976067
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702886"
---
# <a name="issabortabort-ole-db"></a><span data-ttu-id="a8e29-102">ISSAbort::Abort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="a8e29-102">ISSAbort::Abort (OLE DB)</span></span>
  <span data-ttu-id="a8e29-103">取消目前的資料列集加上與目前命令相關聯之任何批次處理的命令。</span><span class="sxs-lookup"><span data-stu-id="a8e29-103">Cancels the current rowset plus any batched commands associated with the current command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e29-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8e29-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a8e29-105">備註</span><span class="sxs-lookup"><span data-stu-id="a8e29-105">Remarks</span></span>  
 <span data-ttu-id="a8e29-106">如果要中止的命令位於預存程序中，預存程序 (以及已經呼叫該程序的任何程序) 以及包含預存程序呼叫之命令批次的執行將會結束。</span><span class="sxs-lookup"><span data-stu-id="a8e29-106">If the command being aborted is in a stored procedure, execution of the stored procedure (and any procedures which had called that procedure) will be terminated as well as the command batch which contains the stored procedure call.</span></span> <span data-ttu-id="a8e29-107">如果伺服器正在將結果集傳送到用戶端，將會停止這個動作。</span><span class="sxs-lookup"><span data-stu-id="a8e29-107">If the server is in the process of transferring a result set to the client, this will be stopped.</span></span> <span data-ttu-id="a8e29-108">如果用戶端不想要取用結果集，在釋放資料列集前呼叫 **ISSAbort::Abort** 將會加速資料列集的釋放，但是如果有開啟的交易，而且 XACT_ABORT 為 ON，呼叫 **ISSAbort::Abort** 時，將會回復交易</span><span class="sxs-lookup"><span data-stu-id="a8e29-108">If the client does not want to consume a result set, calling **ISSAbort::Abort** before releasing the rowset will speed up the rowset release, but if there is an open transaction and XACT_ABORT is ON, the transaction will be rolled back when **ISSAbort::Abort** is called</span></span>  
  
 <span data-ttu-id="a8e29-109">在**ISSAbort：： Abort**傳回 S_OK 之後，相關聯的**IMultipleResults**介面會進入無法使用的狀態，並將 DB_E_CANCELED 傳回給所有方法呼叫 (但**IUnknown**) 介面定義的方法除外，除非已釋放。</span><span class="sxs-lookup"><span data-stu-id="a8e29-109">After **ISSAbort::Abort** returns S_OK, the associated **IMultipleResults** interface enters a unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface) until it is released.</span></span> <span data-ttu-id="a8e29-110">如果在呼叫 **Abort** 前已經從 **IMultipleResults** 取得 **IRowset**，它也會進入無法使用狀態，並將 DB_E_CANCELED 傳回到所有方法呼叫 (除了 **IUnknown** 介面和 **IRowset::ReleaseRows** 所定義的方法以外)，直到成功呼叫 **ISSAbort::Abort** 後釋放它為止。</span><span class="sxs-lookup"><span data-stu-id="a8e29-110">If an **IRowset** had been obtained from **IMultipleResults** prior to a call to **Abort**, it also enters an unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface and **IRowset::ReleaseRows**) until it is released after a successful call to **ISSAbort::Abort**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8e29-111">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，如果伺服器 XACT_ABORT 狀態為 ON，執行 **ISSAbort::Abort** 會終止並回復連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的任何目前隱含或明確交易。</span><span class="sxs-lookup"><span data-stu-id="a8e29-111">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if the server XACT_ABORT state is ON, executing **ISSAbort::Abort** will terminate and roll back any current implicit or explicit transaction when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a8e29-112">舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將不會中止目前的交易。</span><span class="sxs-lookup"><span data-stu-id="a8e29-112">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not abort the current transaction.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="a8e29-113">引數</span><span class="sxs-lookup"><span data-stu-id="a8e29-113">Arguments</span></span>  
 <span data-ttu-id="a8e29-114">無。</span><span class="sxs-lookup"><span data-stu-id="a8e29-114">None.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="a8e29-115">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="a8e29-115">Return Code Values</span></span>  
 <span data-ttu-id="a8e29-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8e29-116">S_OK</span></span>  
 <span data-ttu-id="a8e29-117">**ISSAbort::Abort** 方法會傳回 S_OK，如果批次遭到取消，則為 DB_E_CANTCANCEL。</span><span class="sxs-lookup"><span data-stu-id="a8e29-117">The **ISSAbort::Abort** method returns S_OK if the batch was canceled and DB_E_CANTCANCEL otherwise.</span></span> <span data-ttu-id="a8e29-118">如果批次已經遭到取消，就會傳回 DB_E_CANCELED。</span><span class="sxs-lookup"><span data-stu-id="a8e29-118">If the batch has already been canceled, DB_E_CANCELED is returned.</span></span>  
  
 <span data-ttu-id="a8e29-119">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="a8e29-119">DB_E_CANCELED</span></span>  
 <span data-ttu-id="a8e29-120">批次已經遭到取消。</span><span class="sxs-lookup"><span data-stu-id="a8e29-120">The batch has already been canceled.</span></span>  
  
 <span data-ttu-id="a8e29-121">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="a8e29-121">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="a8e29-122">批次未取消。</span><span class="sxs-lookup"><span data-stu-id="a8e29-122">The batch was not canceled.</span></span>  
  
 <span data-ttu-id="a8e29-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a8e29-123">E_FAIL</span></span>  
 <span data-ttu-id="a8e29-124">發生提供者特定的錯誤;如需詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。</span><span class="sxs-lookup"><span data-stu-id="a8e29-124">A provider specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="a8e29-125">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="a8e29-125">E_UNEXPECTED</span></span>  
 <span data-ttu-id="a8e29-126">此方法的呼叫是非預期的。</span><span class="sxs-lookup"><span data-stu-id="a8e29-126">The call to the method was unexpected.</span></span> <span data-ttu-id="a8e29-127">例如，物件會因為已經呼叫 **ISSAbort::Abort** 而處於廢止狀態。</span><span class="sxs-lookup"><span data-stu-id="a8e29-127">For example, the object is in a zombie state because **ISSAbort::Abort** has already been called.</span></span>  
  
 <span data-ttu-id="a8e29-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a8e29-128">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a8e29-129">記憶體不足的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a8e29-129">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e29-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8e29-130">See Also</span></span>  
 [<span data-ttu-id="a8e29-131">ISSAbort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a8e29-131">ISSAbort &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
