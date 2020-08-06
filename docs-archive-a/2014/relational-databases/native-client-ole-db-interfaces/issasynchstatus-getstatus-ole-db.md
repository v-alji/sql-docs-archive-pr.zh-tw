---
title: ISSAsynchStatus::GetStatus (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::GetStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetStatus method
ms.assetid: 354b6ee4-b5a1-48f6-9403-da3bdc911067
author: rothja
ms.author: jroth
ms.openlocfilehash: 14c20ae5d9a5cd31139db74aeedabb2d017f6ce6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592672"
---
# <a name="issasynchstatusgetstatus-ole-db"></a><span data-ttu-id="d2368-102">ISSAsynchStatus::GetStatus (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="d2368-102">ISSAsynchStatus::GetStatus (OLE DB)</span></span>
  <span data-ttu-id="d2368-103">傳回以非同步方式執行作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="d2368-103">Returns the status of an asynchronously executing operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2368-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2368-104">Syntax</span></span>  
  
```  
  
HRESULT GetStatus(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation,  
  DBCOUNTITEM *pulProgress,  
  DBCOUNTITEM *pulProgressMax,  
  DBASYNCHPHASE *peAsynchPhase,  
  LPOLESTR *ppwszStatusText);  
```  
  
## <a name="arguments"></a><span data-ttu-id="d2368-105">引數</span><span class="sxs-lookup"><span data-stu-id="d2368-105">Arguments</span></span>  
 <span data-ttu-id="d2368-106">*hChapter*[in]</span><span class="sxs-lookup"><span data-stu-id="d2368-106">*hChapter*[in]</span></span>  
 <span data-ttu-id="d2368-107">章節控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d2368-107">The chapter handle.</span></span> <span data-ttu-id="d2368-108">如果輪詢的物件不是資料列集物件，或者作業不適用於章節，則這應該設定為 DB_NULL_HCHAPTER (會由提供者忽略)。</span><span class="sxs-lookup"><span data-stu-id="d2368-108">If the object being polled is not a rowset object or the operation does not apply to a chapter, this should be set to DB_NULL_HCHAPTER, which is ignored by the provider.</span></span>  
  
 <span data-ttu-id="d2368-109">*eOperation*[in]</span><span class="sxs-lookup"><span data-stu-id="d2368-109">*eOperation*[in]</span></span>  
 <span data-ttu-id="d2368-110">正在要求其非同步狀態的作業。</span><span class="sxs-lookup"><span data-stu-id="d2368-110">The operation for which the asynchronous status is being requested.</span></span> <span data-ttu-id="d2368-111">這應該為下列值：</span><span class="sxs-lookup"><span data-stu-id="d2368-111">This should be the following value:</span></span>  
  
 <span data-ttu-id="d2368-112">DBASYNCHOP_OPEN：取用者會要求有關非同步開啟或資料列集擴展的資訊，或有關資料來源物件的非同步初始化的資訊。</span><span class="sxs-lookup"><span data-stu-id="d2368-112">DBASYNCHOP_OPEN-The consumer requests information about the asynchronous opening or population of a rowset or about the asynchronous initialization of a data source object.</span></span> <span data-ttu-id="d2368-113">如果提供者是 OLE DB 2.5 相容且支援 URL 直接繫結的提供者，則取用者會要求有關非同步初始化或資料來源、資料列集、資料列或資料流物件擴展的資訊。</span><span class="sxs-lookup"><span data-stu-id="d2368-113">If the provider is an OLE DB 2.5-compliant provider that supports direct URL binding, the consumer requests information about the asynchronous initialization or population of a data source, rowset, row, or stream object.</span></span>  
  
 <span data-ttu-id="d2368-114">*pulProgress*[out]</span><span class="sxs-lookup"><span data-stu-id="d2368-114">*pulProgress*[out]</span></span>  
 <span data-ttu-id="d2368-115">記憶體的指標，會從中傳回相對於 *pulProgressMax* 參數所指出之預期最大值的非同步作業的目前進度。</span><span class="sxs-lookup"><span data-stu-id="d2368-115">A pointer to memory in which to return the current progress of the asynchronous operation relative to the expected maximum indicated in the *pulProgressMax* parameter.</span></span> <span data-ttu-id="d2368-116">如需 *pulProgress* 之意義的詳細資訊，請參閱 *peAsynchPhase* 的描述。</span><span class="sxs-lookup"><span data-stu-id="d2368-116">For more information about the meaning of *pulProgress*, see the description of *peAsynchPhase*.</span></span>  
  
 <span data-ttu-id="d2368-117">如果 *pulProgress* 是 Null 指標，則不會傳回任何進度。</span><span class="sxs-lookup"><span data-stu-id="d2368-117">If *pulProgress* is a null pointer, no progress is returned.</span></span>  
  
 <span data-ttu-id="d2368-118">*pulProgressMax*[out]</span><span class="sxs-lookup"><span data-stu-id="d2368-118">*pulProgressMax*[out]</span></span>  
 <span data-ttu-id="d2368-119">記憶體的指標，會從中傳回 *pulProgress* 參數的預期最大值。</span><span class="sxs-lookup"><span data-stu-id="d2368-119">A pointer to memory in which to return the expected maximum value of the *pulProgress* parameter.</span></span> <span data-ttu-id="d2368-120">此值可能會在此方法的呼叫之間變更。</span><span class="sxs-lookup"><span data-stu-id="d2368-120">This value may change across calls to this method.</span></span> <span data-ttu-id="d2368-121">如需 *pulProgressMax* 之意義的詳細資訊，請參閱 *peAsynchPhase* 的描述。</span><span class="sxs-lookup"><span data-stu-id="d2368-121">For more information about the meaning of *pulProgressMax*, see the description of *peAsynchPhase*.</span></span>  
  
 <span data-ttu-id="d2368-122">如果 *pulProgressMax* 是 Null 指標，則不會傳回預期的最大值。</span><span class="sxs-lookup"><span data-stu-id="d2368-122">If *pulProgressMax* is a null pointer, no expected maximum value is returned.</span></span>  
  
 <span data-ttu-id="d2368-123">*peAsynchPhase*[out]</span><span class="sxs-lookup"><span data-stu-id="d2368-123">*peAsynchPhase*[out]</span></span>  
 <span data-ttu-id="d2368-124">記憶體的指標，會從中傳回有關非同步作業的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d2368-124">A pointer to memory in which to return additional information regarding the progress of the asynchronous operation.</span></span> <span data-ttu-id="d2368-125">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="d2368-125">Valid values include:</span></span>  
  
 <span data-ttu-id="d2368-126">DBASYNCHPHASE_INITIALIZATION：物件正處於初始化階段。</span><span class="sxs-lookup"><span data-stu-id="d2368-126">DBASYNCHPHASE_INITIALIZATION-The object is in an initialization phase.</span></span> <span data-ttu-id="d2368-127">*pulProgress* 和 *pulProgressMax* 引數指出預估的完成率。</span><span class="sxs-lookup"><span data-stu-id="d2368-127">The arguments *pulProgress* and *pulProgressMax* indicate an estimated ratio of completion.</span></span> <span data-ttu-id="d2368-128">物件尚未完全具體化。</span><span class="sxs-lookup"><span data-stu-id="d2368-128">The object is not yet fully materialized.</span></span> <span data-ttu-id="d2368-129">呼叫任何其他介面的嘗試可能失敗，而物件可能無法使用完整的介面集。</span><span class="sxs-lookup"><span data-stu-id="d2368-129">Attempting to call any other interfaces may fail, and the full set of interfaces may not be available on the object.</span></span> <span data-ttu-id="d2368-130">如果非同步作業是針對更新、刪除或插入資料列的命令呼叫 **ICommand::Execute** 的結果，而且如果 *cParamSets* 大於 1，則 *pulProgress* 和 *pulProgressMax* 可能代表單一參數集或參數集完整陣列的進度。</span><span class="sxs-lookup"><span data-stu-id="d2368-130">If the asynchronous operation was a result of calling **ICommand::Execute** for a command that updates, deletes, or inserts rows and if *cParamSets* is greater than 1, *pulProgress* and *pulProgressMax* may indicate the progress for a single set of parameters or for the full array of parameter sets.</span></span>  
  
 <span data-ttu-id="d2368-131">DBASYNCHPHASE_POPULATION：物件正處於擴展階段。</span><span class="sxs-lookup"><span data-stu-id="d2368-131">DBASYNCHPHASE_POPULATION-The object is in a population phase.</span></span> <span data-ttu-id="d2368-132">雖然資料列集會完全初始化，而且物件可以使用完整的介面範圍，則可能有其他的資料列尚未擴展到資料列集中。</span><span class="sxs-lookup"><span data-stu-id="d2368-132">Although the rowset is fully initialized and the full range of interfaces is available on the object, there may be additional rows not yet populated into the rowset.</span></span> <span data-ttu-id="d2368-133">*pulProgress* 和 *pulProgressMax* 雖然可以根據擴展的資料列數目而定，但通常是根據擴展資料列集所需的時間或努力來決定。</span><span class="sxs-lookup"><span data-stu-id="d2368-133">While *pulProgress* and *pulProgressMax* can be based on the number of rows populated, they are generally based on the time or effort required to populate the rowset.</span></span> <span data-ttu-id="d2368-134">因此呼叫者應該使用此項資訊 (而非最後的資料列計數) 做為處理序所可能花費時間的大略估計。</span><span class="sxs-lookup"><span data-stu-id="d2368-134">A caller should therefore use this information as a rough estimate of how long the process might take, not the eventual row count.</span></span> <span data-ttu-id="d2368-135">此階段只會在資料列集擴展期間傳回，而不會在初始化資料來源物件時傳回，或由更新、刪除或插入資料列的命令執行傳回。</span><span class="sxs-lookup"><span data-stu-id="d2368-135">This phase is returned only during population of a rowset; it is never returned in the initialization of a data source object or by the execution of a command that updates, deletes, or inserts rows.</span></span>  
  
 <span data-ttu-id="d2368-136">DBASYNCHPHASE_COMPLETE：物件的所有非同步處理已完成。</span><span class="sxs-lookup"><span data-stu-id="d2368-136">DBASYNCHPHASE_COMPLETE-All asynchronous processing of the object has completed.</span></span> <span data-ttu-id="d2368-137">**ISSAsynchStatus：： GetStatus**會傳回 HRESULT，指出作業的結果。</span><span class="sxs-lookup"><span data-stu-id="d2368-137">**ISSAsynchStatus::GetStatus** returns an HRESULT indicating the outcome of the operation.</span></span> <span data-ttu-id="d2368-138">一般而言，這會是在同步呼叫作業時所傳回的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="d2368-138">Typically, this will be the HRESULT that would have been returned had the operation been called synchronously.</span></span> <span data-ttu-id="d2368-139">如果非同步作業是針對更新、刪除或插入資料列的命令呼叫 **ICommand::Execute** 的結果，則 *pulProgress* 和 *pulProgressMax* 等於受到該命令影響的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="d2368-139">If the asynchronous operation was a result of calling **ICommand::Execute** for a command that updates, deletes, or inserts rows, *pulProgress* and *pulProgressMax* are equal to the total number of rows affected by the command.</span></span> <span data-ttu-id="d2368-140">如果 *cParamSets* 大於 1，這是受到執行所指定的所有參數集影響的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="d2368-140">If *cParamSets* is greater than 1, this is the total number of rows affected by all of the sets of parameters specified in the execution.</span></span> <span data-ttu-id="d2368-141">如果 *peAsynchPhase* 是 Null 指標，則不會傳回狀態碼。</span><span class="sxs-lookup"><span data-stu-id="d2368-141">If *peAsynchPhase* is a null pointer, no status code is returned.</span></span>  
  
 <span data-ttu-id="d2368-142">DBASYNCHPHASE_CANCELED：物件的非同步處理已中止。</span><span class="sxs-lookup"><span data-stu-id="d2368-142">DBASYNCHPHASE_CANCELED-Asynchronous processing of the object was aborted.</span></span> <span data-ttu-id="d2368-143">**ISSAsynchStatus：： GetStatus**會傳回 DB_E_CANCELED。</span><span class="sxs-lookup"><span data-stu-id="d2368-143">**ISSAsynchStatus::GetStatus** returns DB_E_CANCELED.</span></span> <span data-ttu-id="d2368-144">如果非同步作業是針對更新、刪除或插入資料列的命令呼叫 **ICommand::Execute** 的結果，則 *pulProgress* 等於所有參數集在該命令取消前受其影響的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="d2368-144">If the asynchronous operation was a result of calling **ICommand::Execute** for a command that updates, deletes, or inserts rows, *pulProgress* is equal to the total number of rows, for all parameter sets, affected by the command prior to cancellation.</span></span>  
  
 <span data-ttu-id="d2368-145">*ppwszStatusText*[in/out]</span><span class="sxs-lookup"><span data-stu-id="d2368-145">*ppwszStatusText*[in/out]</span></span>  
 <span data-ttu-id="d2368-146">記憶體的指標，這個記憶體包含有關作業的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d2368-146">A pointer to memory containing additional information about the operation.</span></span> <span data-ttu-id="d2368-147">提供者可以使用此值來區別作業的不同元素，例如，正在存取的不同資源。</span><span class="sxs-lookup"><span data-stu-id="d2368-147">A provider may use this value to distinguish between different elements of an operation-for example, different resources being accessed.</span></span> <span data-ttu-id="d2368-148">這個字串會根據資料來源物件的 DBPROP_INIT_LCID 屬性而當地語系化。</span><span class="sxs-lookup"><span data-stu-id="d2368-148">This string is localized according to the DBPROP_INIT_LCID property on the data source object.</span></span>  
  
 <span data-ttu-id="d2368-149">如果輸入上的 *ppwszStatusText* 非 Null，則提供者會傳回與 *ppwszStatusText* 所識別的特定元素相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="d2368-149">If *ppwszStatusText* is non-null on input, the provider returns status associated with the particular element identified by *ppwszStatusText*.</span></span> <span data-ttu-id="d2368-150">如果 *ppwszStatusText* 並不代表 *eOperation* 的元素，則提供者會傳回 S_OK，且 *pulProgress* 和 *pulProgressMax* 會設定為相同的值。</span><span class="sxs-lookup"><span data-stu-id="d2368-150">If *ppwszStatusText* does not indicate an element of *eOperation*, the provider returns S_OK with *pulProgress* and *pulProgressMax* set to the same value.</span></span> <span data-ttu-id="d2368-151">如果提供者並未根據文字識別碼來區分元素，則它會將 *ppwszStatusText* 設定為 NULL，並傳回整個作業的相關資訊；否則，如果輸入上的 *ppwszStatusText* 非 Null，提供者會保留 *ppwszStatusText* 不變。</span><span class="sxs-lookup"><span data-stu-id="d2368-151">If the provider does not distinguish between elements based on a textual identifier, it sets *ppwszStatusText* to NULL and returns information about the operation as a whole; otherwise, if *ppwszStatusText* is non-null on input, the provider leaves *ppwszStatusText* untouched.</span></span>  
  
 <span data-ttu-id="d2368-152">如果輸入上的*ppwszStatusText*為 null，則提供者會將*ppwszStatusText*設定為值，指出有關作業的詳細資訊，或如果沒有這類資訊，或**ISSAsynchStatus：： GetStatus**傳回錯誤，則設為 null。</span><span class="sxs-lookup"><span data-stu-id="d2368-152">If *ppwszStatusText* is null on input, the provider sets *ppwszStatusText* to a value indicating more information about the operation, or to NULL if no such information is available or if **ISSAsynchStatus::GetStatus** returns an error.</span></span> <span data-ttu-id="d2368-153">當輸入上的 *ppwszStatusText* 是 Null 時，提供者會為狀態字串配置記憶體，並將位址傳回給這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="d2368-153">When *ppwszStatusText* is null on input, the provider allocates memory for the status string and returns the address to this memory.</span></span> <span data-ttu-id="d2368-154">當取用者不再需要字串時，可以使用 **IMalloc::Free** 釋出這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="d2368-154">The consumer releases this memory with **IMalloc::Free** when it no longer needs the string.</span></span>  
  
 <span data-ttu-id="d2368-155">如果輸入上的 *ppwszStatusText* 是 NULL，則不會傳回任何狀態字串，而且提供者會傳回有關作業之任何元素或一般作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="d2368-155">If *ppwszStatusText* is NULL on input, no status string is returned and the provider returns information about any element of the operation or about the operation in general.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="d2368-156">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="d2368-156">Return Code Values</span></span>  
 <span data-ttu-id="d2368-157">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2368-157">S_OK</span></span>  
 <span data-ttu-id="d2368-158">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d2368-158">The method returned successfully.</span></span>  
  
-   <span data-ttu-id="d2368-159">如果 *peAsynchPhase* 等於 DBASYNCHPHASE_INITIALIZATION，則物件尚未完全初始化；嘗試呼叫任何其他的介面可能會失敗，而且物件上可能無法使用完整的介面集。</span><span class="sxs-lookup"><span data-stu-id="d2368-159">If *peAsynchPhase* is equal to DBASYNCHPHASE_INITIALIZATION, the object is not yet fully initialized; attempting to call any other interfaces might fail, and the full set of interfaces might not be available on the object.</span></span>  
  
-   <span data-ttu-id="d2368-160">如果 *peAsynchPhase* 等於 DBASYNCHPHASE_POPULATION，資料列集會完全初始化，而且物件上可以使用完整的介面範圍；不過可能有其他尚未擴展到資料列集中的資料列。</span><span class="sxs-lookup"><span data-stu-id="d2368-160">If *peAsynchPhase* is equal to DBASYNCHPHASE_POPULATION, the rowset is fully initialized and the full range of interfaces is available on the object; however, there might be additional rows not yet populated into the rowset.</span></span>  
  
-   <span data-ttu-id="d2368-161">如果 *peAsynchPhase* 等於 DBASYNCHPHASE_COMPLETE，物件的所有非同步處理都已完成。</span><span class="sxs-lookup"><span data-stu-id="d2368-161">If *peAsynchPhase* is equal to DBASYNCHPHASE_COMPLETE, all asynchronous processing of the object has completed.</span></span> <span data-ttu-id="d2368-162">該物件會完全初始化並擴展。</span><span class="sxs-lookup"><span data-stu-id="d2368-162">The object is fully initialized and populated.</span></span>  
  
 <span data-ttu-id="d2368-163">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="d2368-163">DB_E_CANCELED</span></span>  
 <span data-ttu-id="d2368-164">已在資料列集擴展期間取消非同步處理。</span><span class="sxs-lookup"><span data-stu-id="d2368-164">Asynchronous processing was canceled during rowset population.</span></span> <span data-ttu-id="d2368-165">擴展停止，但資料列集對於已擴展的資料列仍保持有效。</span><span class="sxs-lookup"><span data-stu-id="d2368-165">Population stops, but the rowset remains valid for the rows already populated.</span></span>  
  
 <span data-ttu-id="d2368-166">已在資料來源物件初始化期間取消非同步處理。</span><span class="sxs-lookup"><span data-stu-id="d2368-166">Asynchronous processing was canceled during data source object initialization.</span></span> <span data-ttu-id="d2368-167">資料來源物件處於未初始化的狀態。</span><span class="sxs-lookup"><span data-stu-id="d2368-167">The data source object is in an uninitialized state.</span></span>  
  
 <span data-ttu-id="d2368-168">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d2368-168">E_INVALIDARG</span></span>  
 <span data-ttu-id="d2368-169">*hChapter* 參數錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2368-169">The *hChapter* parameter is incorrect.</span></span>  
  
 <span data-ttu-id="d2368-170">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="d2368-170">E_UNEXPECTED</span></span>  
 <span data-ttu-id="d2368-171">在資料來源物件上呼叫了**ISSAsynchStatus：： GetStatus** ，但尚未在資料來源物件上呼叫**IDBInitialize：： Initialize** 。</span><span class="sxs-lookup"><span data-stu-id="d2368-171">**ISSAsynchStatus::GetStatus** was called on a data source object, and **IDBInitialize::Initialize** has not been called on the data source object.</span></span>  
  
 <span data-ttu-id="d2368-172">已在資料列集上呼叫**ISSAsynchStatus：： GetStatus** ，已呼叫**ITransaction：： Commit**或**ITransaction：： Abort** ，而且物件處於廢止狀態。</span><span class="sxs-lookup"><span data-stu-id="d2368-172">**ISSAsynchStatus::GetStatus** was called on a rowset, **ITransaction::Commit** or **ITransaction::Abort** was called, and the object is in a zombie state.</span></span>  
  
 <span data-ttu-id="d2368-173">已在初始化階段中以非同步方式取消的資料列集上呼叫**ISSAsynchStatus：： GetStatus** 。</span><span class="sxs-lookup"><span data-stu-id="d2368-173">**ISSAsynchStatus::GetStatus** was called on a rowset that was asynchronously canceled in its initialization phase.</span></span> <span data-ttu-id="d2368-174">此資料列集處於廢止狀態。</span><span class="sxs-lookup"><span data-stu-id="d2368-174">The rowset is in a zombie state.</span></span>  
  
 <span data-ttu-id="d2368-175">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2368-175">E_FAIL</span></span>  
 <span data-ttu-id="d2368-176">發生了提供者特定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d2368-176">A provider-specific error occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2368-177">備註</span><span class="sxs-lookup"><span data-stu-id="d2368-177">Remarks</span></span>  
 <span data-ttu-id="d2368-178">**ISSAsynchStatus::GetStatus** 方法的行為與 **IDBAsynchStatus::GetStatus** 方法完全相同，不同的是如果中止資料來源物件的初始化，便會傳回 E_UNEXPECTED，而不是 DB_E_CANCELED (雖然 [ISSAsynchStatus::WaitForAsynchCompletion](issasynchstatus-waitforasynchcompletion-ole-db.md) 會傳回 DB_E_CANCELED)。</span><span class="sxs-lookup"><span data-stu-id="d2368-178">The **ISSAsynchStatus::GetStatus** method behaves exactly as the **IDBAsynchStatus::GetStatus** method except that if initialization of a data source object is aborted, E_UNEXPECTED is returned rather than DB_E_CANCELED (although [ISSAsynchStatus::WaitForAsynchCompletion](issasynchstatus-waitforasynchcompletion-ole-db.md) will return DB_E_CANCELED).</span></span> <span data-ttu-id="d2368-179">這是因為資料來源物件在中止後不會保留在一般的廢止狀態，如此可以讓系統嘗試進一步的初始化作業。</span><span class="sxs-lookup"><span data-stu-id="d2368-179">This is because the data source object is not left in the usual zombie state following an abort, in order that further initialization operations may be attempted.</span></span>  
  
 <span data-ttu-id="d2368-180">如果資料列集是非同步地初始化或擴展，則必須支援此方法。</span><span class="sxs-lookup"><span data-stu-id="d2368-180">If the rowset is initialized or populated asynchronously, it must support this method.</span></span>  
  
 <span data-ttu-id="d2368-181">除了列出的傳回值外，**ISSAsynchStatus::GetStatus** 可以傳回任何的 HRESULT，此值會由初始化非同步作業的方法所傳回，指出作業是成功還是失敗。</span><span class="sxs-lookup"><span data-stu-id="d2368-181">In addition to the return values listed, **ISSAsynchStatus::GetStatus** can return any HRESULT that would have been returned by the method that initiated the asynchronous operation, indicating the success or failure of the operation.</span></span>  
  
 <span data-ttu-id="d2368-182">有些非同步作業可能不會傳回 "finished" 和 "not finished" 以外的任何狀態。</span><span class="sxs-lookup"><span data-stu-id="d2368-182">Some asynchronous operations might not be able to return any states other than "finished" and "not finished".</span></span> <span data-ttu-id="d2368-183">這些作業應該將 *pulProgressMax* 設定為 1 的值，指出其預估值全有或全無的資料粒度，所以其回應會是 0/1 或 1/1。</span><span class="sxs-lookup"><span data-stu-id="d2368-183">They should set *pulProgressMax* to a value of 1, indicating the all-or-nothing granularity of their estimate, so their answers would be either 0/1 or 1/1.</span></span>  
  
 <span data-ttu-id="d2368-184">提供者可能會在連續的呼叫中變更 *pulProgressMax*，而且甚至會傳回比先前更小的比率 (如果這反映出更為精確的工作完成度預估值)。</span><span class="sxs-lookup"><span data-stu-id="d2368-184">A provider may change *pulProgressMax* in successive calls and even return a smaller ratio than previously, if this reflects an improving estimate of the degree of completion of the task.</span></span>  
  
 <span data-ttu-id="d2368-185">提供者不必保證更高的精確度，但在可以提供合理的完成度預估值時，建議提供者加以提供。</span><span class="sxs-lookup"><span data-stu-id="d2368-185">The provider is not obliged to guarantee any further accuracy but is encouraged to do so in cases where reasonable estimates of completion are possible.</span></span> <span data-ttu-id="d2368-186">此類努力可以提升使用者介面的品質，因為此函數的主要用途很可能是為使用者提供進度回應。</span><span class="sxs-lookup"><span data-stu-id="d2368-186">Such efforts will improve user-interface quality because the main use of this function is likely to be to give progress feedback to the user.</span></span> <span data-ttu-id="d2368-187">使用者的滿意度會隨著不可見的長時間執行工作的回應品質而增加。</span><span class="sxs-lookup"><span data-stu-id="d2368-187">User satisfaction increases with the quality of feedback on an invisible, long-running task.</span></span>  
  
 <span data-ttu-id="d2368-188">在初始化的資料來源物件或擴展的資料列集上呼叫 **ISSAsynchStatus::GetStatus**，或者為 *eOperation* 傳遞 DBASYNCHOP_OPEN 以外的值，會傳回 S_OK，且 *pulProgress* 和 *pulProgressMax* 都設定為相同值。</span><span class="sxs-lookup"><span data-stu-id="d2368-188">Calling **ISSAsynchStatus::GetStatus** on an initialized data source object or a populated rowset, or passing a value for *eOperation* other than DBASYNCHOP_OPEN, returns S_OK with *pulProgress* and *pulProgressMax* set to the same value.</span></span> <span data-ttu-id="d2368-189">如果在用來執行更新、刪除或插入資料列的命令所建立的物件上呼叫**ISSAsynchStatus：： GetStatus** ， *pulProgress*和*pulProgressMax*都會指出受命令影響的資料列總數。</span><span class="sxs-lookup"><span data-stu-id="d2368-189">If **ISSAsynchStatus::GetStatus** is called on an object created from the execution of a command that updates, deletes, or inserts rows, both *pulProgress* and *pulProgressMax* indicate the total number of rows affected by the command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2368-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2368-190">See Also</span></span>  
 <span data-ttu-id="d2368-191">[執行非同步作業](../native-client/features/performing-asynchronous-operations.md) </span><span class="sxs-lookup"><span data-stu-id="d2368-191">[Performing Asynchronous Operations](../native-client/features/performing-asynchronous-operations.md) </span></span>  
 [<span data-ttu-id="d2368-192">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="d2368-192">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-ole-db.md)  
  
  
