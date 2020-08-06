---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: rothja
ms.author: jroth
ms.openlocfilehash: c3e325cd99276e04a178b89c19b233289edc09fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702894"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a><span data-ttu-id="98e8f-102">ISQLServerErrorInfo::GetErrorInfo (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="98e8f-102">ISQLServerErrorInfo::GetErrorInfo (OLE DB)</span></span>
  <span data-ttu-id="98e8f-103">傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤詳細資料之 Native Client OLE DB 提供者 SSERRORINFO 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="98e8f-103">Returns a pointer to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider SSERRORINFO structure containing the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error details.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="98e8f-104">Syntax</span></span>  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a><span data-ttu-id="98e8f-105">引數</span><span class="sxs-lookup"><span data-stu-id="98e8f-105">Arguments</span></span>  
 <span data-ttu-id="98e8f-106">*ppSSErrorInfo*[out]</span><span class="sxs-lookup"><span data-stu-id="98e8f-106">*ppSSErrorInfo*[out]</span></span>  
 <span data-ttu-id="98e8f-107">SSERRORINFO 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="98e8f-107">A pointer to a SSERRORINFO structure.</span></span> <span data-ttu-id="98e8f-108">如果方法失敗，或者沒有與錯誤建立關聯的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資訊，提供者就不會配置任何記憶體，也無法確保輸出時，*ppSSErrorInfo* 引數為 Null 指標。</span><span class="sxs-lookup"><span data-stu-id="98e8f-108">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with the error, the provider does not allocate any memory, and ensures that the *ppSSErrorInfo* argument is a null pointer on output.</span></span>  
  
 <span data-ttu-id="98e8f-109">*ppErrorStrings*[out]</span><span class="sxs-lookup"><span data-stu-id="98e8f-109">*ppErrorStrings*[out]</span></span>  
 <span data-ttu-id="98e8f-110">Unicode 字元字串指標的指標。</span><span class="sxs-lookup"><span data-stu-id="98e8f-110">A pointer to a Unicode character-string pointer.</span></span> <span data-ttu-id="98e8f-111">如果方法失敗，或者沒有與錯誤建立關聯的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資訊，提供者就不會配置任何記憶體，也無法確保輸出時，*ppErrorStrings* 引數為 Null 指標。</span><span class="sxs-lookup"><span data-stu-id="98e8f-111">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with an error, the provider does not allocate any memory, and ensures that the *ppErrorStrings* argument is a null pointer on output.</span></span> <span data-ttu-id="98e8f-112">使用 *IMalloc::Free* 方法釋放 **ppErrorStrings** 引數時，會釋放傳回之 SSERRORINFO 結構的三個個別字串成員，因為有在區塊中配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="98e8f-112">Freeing the *ppErrorStrings* argument with the **IMalloc::Free** method frees the three individual string members of the returned SSERRORINFO structure, as the memory is allocated in a block.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="98e8f-113">傳回碼值</span><span class="sxs-lookup"><span data-stu-id="98e8f-113">Return Code Values</span></span>  
 <span data-ttu-id="98e8f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="98e8f-114">S_OK</span></span>  
 <span data-ttu-id="98e8f-115">此方法已成功。</span><span class="sxs-lookup"><span data-stu-id="98e8f-115">The method succeeded.</span></span>  
  
 <span data-ttu-id="98e8f-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="98e8f-116">E_INVALIDARG</span></span>  
 <span data-ttu-id="98e8f-117">*ppSSErrorInfo* 或 *ppErrorStrings* 引數為 NULL。</span><span class="sxs-lookup"><span data-stu-id="98e8f-117">Either the *ppSSErrorInfo* or the *ppErrorStrings* argument was NULL.</span></span>  
  
 <span data-ttu-id="98e8f-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="98e8f-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="98e8f-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者無法配置足夠的記憶體來完成要求。</span><span class="sxs-lookup"><span data-stu-id="98e8f-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider could not allocate sufficient memory to complete the request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98e8f-120">備註</span><span class="sxs-lookup"><span data-stu-id="98e8f-120">Remarks</span></span>  
 <span data-ttu-id="98e8f-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會針對透過取用者傳遞之指標所傳回的 SSERRORINFO 和 OLECHAR 字串配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="98e8f-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider allocates memory for the SSERRORINFO and OLECHAR strings returned through the pointers passed by the consumer.</span></span> <span data-ttu-id="98e8f-122">當取用者不再需要存取錯誤資料時，必須使用 **IMalloc::Free** 方法來取消配置這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="98e8f-122">The consumer must deallocate this memory by using the **IMalloc::Free** method when it no longer requires access to the error data.</span></span>  
  
 <span data-ttu-id="98e8f-123">SSERRORINFO 結構定義如下：</span><span class="sxs-lookup"><span data-stu-id="98e8f-123">The SSERRORINFO structure is defined as follows:</span></span>  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|<span data-ttu-id="98e8f-124">成員</span><span class="sxs-lookup"><span data-stu-id="98e8f-124">Member</span></span>|<span data-ttu-id="98e8f-125">描述</span><span class="sxs-lookup"><span data-stu-id="98e8f-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="98e8f-126">*pwszMessage*</span><span class="sxs-lookup"><span data-stu-id="98e8f-126">*pwszMessage*</span></span>|<span data-ttu-id="98e8f-127">來自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="98e8f-127">The error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="98e8f-128">此訊息會透過 **IErrorInfo::GetDescription** 方法傳回。</span><span class="sxs-lookup"><span data-stu-id="98e8f-128">The message is returned through the **IErrorInfo::GetDescription** method.</span></span>|  
|<span data-ttu-id="98e8f-129">*pwszServer*</span><span class="sxs-lookup"><span data-stu-id="98e8f-129">*pwszServer*</span></span>|<span data-ttu-id="98e8f-130">發生錯誤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="98e8f-130">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which the error occurred.</span></span>|  
|<span data-ttu-id="98e8f-131">*pwszProcedure*</span><span class="sxs-lookup"><span data-stu-id="98e8f-131">*pwszProcedure*</span></span>|<span data-ttu-id="98e8f-132">如果在預存程序中發生錯誤，則是產生錯誤之預存程序的名稱，否則為空字串。</span><span class="sxs-lookup"><span data-stu-id="98e8f-132">The name of the stored procedure generating the error if the error occurred in a stored procedure; otherwise, an empty string.</span></span>|  
|<span data-ttu-id="98e8f-133">*lNative*</span><span class="sxs-lookup"><span data-stu-id="98e8f-133">*lNative*</span></span>|<span data-ttu-id="98e8f-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="98e8f-134">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number.</span></span> <span data-ttu-id="98e8f-135">此錯誤號碼與 **ISQLErrorInfo::GetSQLInfo** 方法之 *plNativeError* 參數中所傳回的錯誤號碼相同。</span><span class="sxs-lookup"><span data-stu-id="98e8f-135">The error number is identical to that returned in the *plNativeError* parameter of the **ISQLErrorInfo::GetSQLInfo** method.</span></span>|  
|<span data-ttu-id="98e8f-136">*bState*</span><span class="sxs-lookup"><span data-stu-id="98e8f-136">*bState*</span></span>|<span data-ttu-id="98e8f-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤的狀態。</span><span class="sxs-lookup"><span data-stu-id="98e8f-137">The state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="98e8f-138">*bClass*</span><span class="sxs-lookup"><span data-stu-id="98e8f-138">*bClass*</span></span>|<span data-ttu-id="98e8f-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="98e8f-139">The severity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="98e8f-140">*wLineNumber*</span><span class="sxs-lookup"><span data-stu-id="98e8f-140">*wLineNumber*</span></span>|<span data-ttu-id="98e8f-141">在適用時，這是產生錯誤訊息之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序的行號。</span><span class="sxs-lookup"><span data-stu-id="98e8f-141">When applicable, the line of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure that generated the error message.</span></span> <span data-ttu-id="98e8f-142">如果不包含任何程序，預設值為 1。</span><span class="sxs-lookup"><span data-stu-id="98e8f-142">If no procedure is involved, the default value is 1.</span></span>|  
  
 <span data-ttu-id="98e8f-143">結構中的指標會參考 *ppErrorStrings* 引數所傳回之字串中的地址。</span><span class="sxs-lookup"><span data-stu-id="98e8f-143">Pointers in the structure reference addresses in the string returned in the *ppErrorStrings* argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e8f-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98e8f-144">See Also</span></span>  
 <span data-ttu-id="98e8f-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="98e8f-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span></span>  
 [<span data-ttu-id="98e8f-146">RAISERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="98e8f-146">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
