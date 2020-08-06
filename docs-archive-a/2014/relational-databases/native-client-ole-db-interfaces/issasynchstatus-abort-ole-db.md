---
title: ISSAsynchStatus::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fb352b6541240126dcd4c60521b93d57d6839f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702882"
---
# <a name="issasynchstatusabort-ole-db"></a><span data-ttu-id="87e68-102">ISSAsynchStatus::Abort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="87e68-102">ISSAsynchStatus::Abort (OLE DB)</span></span>
  <span data-ttu-id="87e68-103">取消非同步執行的作業。</span><span class="sxs-lookup"><span data-stu-id="87e68-103">Cancels an asynchronously executing operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e68-104">語法</span><span class="sxs-lookup"><span data-stu-id="87e68-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a><span data-ttu-id="87e68-105">引數</span><span class="sxs-lookup"><span data-stu-id="87e68-105">Arguments</span></span>  
 <span data-ttu-id="87e68-106">*hChapter*[in]</span><span class="sxs-lookup"><span data-stu-id="87e68-106">*hChapter*[in]</span></span>  
 <span data-ttu-id="87e68-107">要中止作業之章節的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="87e68-107">The handle of the chapter for which to abort the operation.</span></span> <span data-ttu-id="87e68-108">如果所呼叫的物件不是資料列集物件，或作業不適用於某個章節，則呼叫端必須將*hchapter 設定*設定為 DB_Null_HCHAPTER。</span><span class="sxs-lookup"><span data-stu-id="87e68-108">If the object being called is not a rowset object or the operation does not apply to a chapter, the caller must set *hChapter* to DB_NULL_HCHAPTER.</span></span>  
  
 <span data-ttu-id="87e68-109">*eOperation*[in]</span><span class="sxs-lookup"><span data-stu-id="87e68-109">*eOperation*[in]</span></span>  
 <span data-ttu-id="87e68-110">要中止的作業。</span><span class="sxs-lookup"><span data-stu-id="87e68-110">The operation to abort.</span></span> <span data-ttu-id="87e68-111">這應該為下列值：</span><span class="sxs-lookup"><span data-stu-id="87e68-111">This should be the following value:</span></span>  
  
 <span data-ttu-id="87e68-112">DBASYNCHOP_OPEN：取消的要求適用於非同步開啟或擴展資料列集，或是非同步初始化資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="87e68-112">DBASYNCHOP_OPEN-The request to cancel applies to the asynchronous opening or population of a rowset or to the asynchronous initialization of a data source object.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="87e68-113">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="87e68-113">Return Code Values</span></span>  
 <span data-ttu-id="87e68-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="87e68-114">S_OK</span></span>  
 <span data-ttu-id="87e68-115">已經處理取消非同步作業的要求。</span><span class="sxs-lookup"><span data-stu-id="87e68-115">The request to cancel the asynchronous operation was processed.</span></span> <span data-ttu-id="87e68-116">這不保證作業本身已被取消。</span><span class="sxs-lookup"><span data-stu-id="87e68-116">This does not guarantee that the operation itself was canceled.</span></span> <span data-ttu-id="87e68-117">若要判斷此作業是否已被取消，取用者應該呼叫 [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) 並檢查是否有 DB_E_CANCELED；但是，下一次呼叫時可能不會傳回它。</span><span class="sxs-lookup"><span data-stu-id="87e68-117">To determine whether the operation was canceled, the consumer should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) and check for DB_E_CANCELED; however, it might not be returned in the very next call.</span></span>  
  
 <span data-ttu-id="87e68-118">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="87e68-118">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="87e68-119">無法取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="87e68-119">The asynchronous operation cannot be canceled.</span></span>  
  
 <span data-ttu-id="87e68-120">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="87e68-120">DB_E_CANCELED</span></span>  
 <span data-ttu-id="87e68-121">已經在通知期間取消中止非同步作業的要求。</span><span class="sxs-lookup"><span data-stu-id="87e68-121">The request to abort the asynchronous operation was canceled during notifications.</span></span> <span data-ttu-id="87e68-122">此作業仍然以非同步的方式執行。</span><span class="sxs-lookup"><span data-stu-id="87e68-122">The operation is still being executed asynchronously.</span></span>  
  
 <span data-ttu-id="87e68-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87e68-123">E_FAIL</span></span>  
 <span data-ttu-id="87e68-124">發生了提供者特定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="87e68-124">A provider-specific error occurred.</span></span>  
  
 <span data-ttu-id="87e68-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="87e68-125">E_INVALIDARG</span></span>  
 <span data-ttu-id="87e68-126">*Hchapter 設定*參數不 DB_Null_HCHAPTER，或*eOperation*不 DBASYNCH_OPEN。</span><span class="sxs-lookup"><span data-stu-id="87e68-126">The *hChapter* parameter is not DB_NULL_HCHAPTER or *eOperation* is not DBASYNCH_OPEN.</span></span>  
  
 <span data-ttu-id="87e68-127">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="87e68-127">E_UNEXPECTED</span></span>  
 <span data-ttu-id="87e68-128">在尚未呼叫**IDBInitialize：： Initialize**的資料來源物件上呼叫**ISSAsynchStatus：： Abort** ，或尚未完成。</span><span class="sxs-lookup"><span data-stu-id="87e68-128">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** has not been called, or has not completed.</span></span>  
  
 <span data-ttu-id="87e68-129">在呼叫了**IDBInitialize：： Initialize**的資料來源物件上呼叫了**ISSAsynchStatus：： Abort** ，但後來在初始化之前取消，或已超時。資料來源物件仍未初始化。</span><span class="sxs-lookup"><span data-stu-id="87e68-129">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** was called but subsequently canceled before initialization, or has timed out. The data source object is still uninitialized.</span></span>  
  
 <span data-ttu-id="87e68-130">在先前呼叫了**ITransaction：： Commit**或**ITransaction：： abort**的資料列集上呼叫**ISSAsynchStatus：： Abort** ，而且資料列集不會存留在 Commit 或 Abort，而且處於廢止狀態。</span><span class="sxs-lookup"><span data-stu-id="87e68-130">**ISSAsynchStatus::Abort** was called on a rowset on which **ITransaction::Commit** or **ITransaction::Abort** was previously called, and the rowset did not survive the commit or abort and is in a zombie state.</span></span>  
  
 <span data-ttu-id="87e68-131">已在資料列集上呼叫 **ISSAsynchStatus::Abort**，這個資料列集已在其初始化階段非同步地取消。</span><span class="sxs-lookup"><span data-stu-id="87e68-131">**ISSAsynchStatus::Abort** was called on a rowset that was asynchronously canceled in its initialization phase.</span></span> <span data-ttu-id="87e68-132">此資料列集處於廢止狀態。</span><span class="sxs-lookup"><span data-stu-id="87e68-132">The rowset is in a zombie state.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87e68-133">備註</span><span class="sxs-lookup"><span data-stu-id="87e68-133">Remarks</span></span>  
 <span data-ttu-id="87e68-134">中止資料列集或資料來源物件的初始化可能會讓該資料列集或資料來源物件處於廢止狀態，因此造成 **IUnknown** 方法以外的所有方法都會傳回 E_UNEXPECTED。</span><span class="sxs-lookup"><span data-stu-id="87e68-134">Aborting the initialization of a rowset or data source object might leave the rowset or data source object in a zombie state, such that all methods other than **IUnknown** methods return E_UNEXPECTED.</span></span> <span data-ttu-id="87e68-135">當發生這個情況時，取用者唯一可行的動作就是釋放此資料列集或資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="87e68-135">When this happens, the only possible action for the consumer is to release the rowset or data source object.</span></span>  
  
 <span data-ttu-id="87e68-136">呼叫 **ISSAsynchStatus::Abort** 並針對 *eOperation* 傳回 DBASYNCHOP_OPEN 以外的值將會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="87e68-136">Calling **ISSAsynchStatus::Abort** and passing a value for *eOperation* other than DBASYNCHOP_OPEN returns S_OK.</span></span> <span data-ttu-id="87e68-137">這不表示此作業已被取消或完成。</span><span class="sxs-lookup"><span data-stu-id="87e68-137">This does not imply that the operation completed or was canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e68-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87e68-138">See Also</span></span>  
 [<span data-ttu-id="87e68-139">執行非同步作業</span><span class="sxs-lookup"><span data-stu-id="87e68-139">Performing Asynchronous Operations</span></span>](../native-client/features/performing-asynchronous-operations.md)  
  
  
