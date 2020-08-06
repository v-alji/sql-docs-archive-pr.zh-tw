---
title: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: rothja
ms.author: jroth
ms.openlocfilehash: f57211d1c62535828704dc971e345b412c284cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594041"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a><span data-ttu-id="70f0f-102">ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="70f0f-102">ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)</span></span>
  <span data-ttu-id="70f0f-103">等到非同步執行的作業完成或發生逾時為止。</span><span class="sxs-lookup"><span data-stu-id="70f0f-103">Waits until the asynchronously executing operation is complete or until a time-out occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f0f-104">語法</span><span class="sxs-lookup"><span data-stu-id="70f0f-104">Syntax</span></span>  
  
```  
  
HRESULT WaitForAsynchCompletion(   
  DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a><span data-ttu-id="70f0f-105">引數</span><span class="sxs-lookup"><span data-stu-id="70f0f-105">Arguments</span></span>  
 <span data-ttu-id="70f0f-106">*dwMillisecTimeOut*[in]</span><span class="sxs-lookup"><span data-stu-id="70f0f-106">*dwMillisecTimeOut*[in]</span></span>  
 <span data-ttu-id="70f0f-107">逾時 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="70f0f-107">Time-out in milliseconds.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="70f0f-108">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="70f0f-108">Return Code Values</span></span>  
 <span data-ttu-id="70f0f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="70f0f-109">S_OK</span></span>  
 <span data-ttu-id="70f0f-110">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="70f0f-110">The method succeeded.</span></span>  
  
 <span data-ttu-id="70f0f-111">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="70f0f-111">E_UNEXPECTED</span></span>  
 <span data-ttu-id="70f0f-112">因為已呼叫**ITransaction：： Commit**或**ITransaction：： Abort** ，或資料列集在其初始化階段已取消，所以資料列集處於未使用的狀態。</span><span class="sxs-lookup"><span data-stu-id="70f0f-112">A rowset is in an unused state because **ITransaction::Commit** or **ITransaction::Abort** has been called or the rowset was cancelled during its initialization phase.</span></span>  
  
 <span data-ttu-id="70f0f-113">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="70f0f-113">DB_E_CANCELED</span></span>  
 <span data-ttu-id="70f0f-114">非同步處理已在資料列集擴展或資料來源物件初始化期間取消。</span><span class="sxs-lookup"><span data-stu-id="70f0f-114">Asynchronous processing was cancelled during rowset population or data source object initialization.</span></span>  
  
 <span data-ttu-id="70f0f-115">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="70f0f-115">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="70f0f-116">即使已經達到指定的逾時，此作業還是尚未完成。</span><span class="sxs-lookup"><span data-stu-id="70f0f-116">The operation has not yet completed even though specified time-out has been reached.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70f0f-117">除了以上列出的傳回碼值，**ISSAsynchStatus::WaitForAsynchCompletion** 方法也支援透過核心 OLEDB **ICommand::Execute** 和 **IDBInitialize::Initialize** 方法所傳回的傳回碼值。</span><span class="sxs-lookup"><span data-stu-id="70f0f-117">In addition to the return code values listed above, the **ISSAsynchStatus::WaitForAsynchCompletion** method also supports the return code values returned by the core OLEDB **ICommand::Execute** and **IDBInitialize::Initialize** methods.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70f0f-118">備註</span><span class="sxs-lookup"><span data-stu-id="70f0f-118">Remarks</span></span>  
 <span data-ttu-id="70f0f-119">在逾時值 (以毫秒為單位) 已過，或暫止的作業完成前，**ISSAsynchStatus::WaitForAsynchCompletion** 方法將不會傳回。</span><span class="sxs-lookup"><span data-stu-id="70f0f-119">The **ISSAsynchStatus::WaitForAsynchCompletion** method will not return until the time-out value (in milliseconds) has passed or the pending operation is done.</span></span> <span data-ttu-id="70f0f-120">**Command**物件具有**CommandTimeout**屬性，可控制查詢將在超時前執行的秒數。如果搭配**ISSAsynchStatus：： WaitForAsynchCompletion**方法使用，將會忽略**CommandTimeout**屬性。</span><span class="sxs-lookup"><span data-stu-id="70f0f-120">The **Command** object has a **CommandTimeout** property that controls the number of seconds a query will run before timing out. The **CommandTimeout** property will be ignored if used in conjunction with **ISSAsynchStatus::WaitForAsynchCompletion** method.</span></span>  
  
 <span data-ttu-id="70f0f-121">非同步作業會忽略逾時屬性。</span><span class="sxs-lookup"><span data-stu-id="70f0f-121">The time-out property is ignored for asynchronous operations.</span></span> <span data-ttu-id="70f0f-122">**ISSAsynchStatus::WaitForAsynchCompletion** 的逾時參數會指定將控制項傳回給呼叫端前經過的時間上限。</span><span class="sxs-lookup"><span data-stu-id="70f0f-122">The time-out parameter of **ISSAsynchStatus::WaitForAsynchCompletion** specifies the maximum amount of time that will elapse before control is returned to the caller.</span></span> <span data-ttu-id="70f0f-123">如果這個逾時過期，會傳回 DB_S_ASYNCHRONOUS。</span><span class="sxs-lookup"><span data-stu-id="70f0f-123">If this time-out expires, DB_S_ASYNCHRONOUS will be returned.</span></span> <span data-ttu-id="70f0f-124">逾時絕不會取消非同步作業。</span><span class="sxs-lookup"><span data-stu-id="70f0f-124">Time-outs never cancel asynchronous operations.</span></span> <span data-ttu-id="70f0f-125">如果應用程式需要取消沒有在逾時期間內完成的非同步作業，它必須等到逾時，然後明確地取消此作業 (如果有傳回 DB_S_ASYNCHRONOUS)。</span><span class="sxs-lookup"><span data-stu-id="70f0f-125">If the application needs to cancel an asynchronous operation that does not complete within a time-out period, it must wait for the time-out and then explicitly cancel the operation if DB_S_ASYNCHRONOUS is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="70f0f-126">使用 OLE DB 服務元件時，如果為 DB_S_ASYNCHRONOUS，可能會傳回 S_OK；因此，應用程式應該呼叫 [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) 來檢查傳回 S_OK 或 DB_S_ASYNCHRONOUS 時，作業是否完成。</span><span class="sxs-lookup"><span data-stu-id="70f0f-126">When the OLE DB Service Components are used, S_OK may be returned when DB_S_ASYNCHRONOUS is expected, so applications should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) to check for completion when S_OK or DB_S_ASYNCHRONOUS is returned.</span></span>  
  
 <span data-ttu-id="70f0f-127">如果 *dwMillisecTimeOut* 值設定為 INFINITE，**ISSAsynchStatus::WaitForAsynchCompletion** 方法會封鎖，直到作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="70f0f-127">If the *dwMillisecTimeOut* value is set to INFINITE, the **ISSAsynchStatus::WaitForAsynchCompletion** method blocks until the operation is done.</span></span> <span data-ttu-id="70f0f-128">如果 *dwMillisecTimeOut* 值設定為 0，則方法將會立即傳回暫止之作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="70f0f-128">If the *dwMillisecTimeOut* value is set to 0, then the method will return immediately with the status of the pending operation.</span></span> <span data-ttu-id="70f0f-129">如果逾時在作業完成前過期，將會傳回 DB_S_ASYNCHRONOUS。</span><span class="sxs-lookup"><span data-stu-id="70f0f-129">If the time-out expires before the operation is complete DB_S_ASYNCHRONOUS will be returned.</span></span>  
  
 <span data-ttu-id="70f0f-130">如果作業在逾時過期前完成，傳回的 HRESULT 將會是此作業所傳回的 HRESULT (已經傳回的 HRESULT 已經讓此作業以同步方式執行)。</span><span class="sxs-lookup"><span data-stu-id="70f0f-130">If the operation completes before the time-out expires, the returned HRESULT will be the HRESULT returned by the operation (the HRESULT that would have been returned had the operation been performed synchronously).</span></span>  
  
 <span data-ttu-id="70f0f-131">此外，SSPROP_ISSAsynchStatus 屬性已加入到 DBPROPSET_SQLSERVERROWSET 屬性集。</span><span class="sxs-lookup"><span data-stu-id="70f0f-131">In addition, the SSPROP_ISSAsynchStatus property has been added to the DBPROPSET_SQLSERVERROWSET property set.</span></span> <span data-ttu-id="70f0f-132">支援 [ISSAsynchStatus](issasynchstatus-ole-db.md) 介面的提供者必須使用 VARIANT_TRUE 的值實作此屬性。</span><span class="sxs-lookup"><span data-stu-id="70f0f-132">Providers that support the [ISSAsynchStatus](issasynchstatus-ole-db.md) interface must implement this property with a value of VARIANT_TRUE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f0f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70f0f-133">See Also</span></span>  
 <span data-ttu-id="70f0f-134">[執行非同步作業](../native-client/features/performing-asynchronous-operations.md) </span><span class="sxs-lookup"><span data-stu-id="70f0f-134">[Performing Asynchronous Operations](../native-client/features/performing-asynchronous-operations.md) </span></span>  
 [<span data-ttu-id="70f0f-135">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="70f0f-135">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-ole-db.md)  
  
  
