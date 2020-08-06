---
title: srv_paramlen (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramlen
ms.assetid: d1fe92ff-cad6-4396-8216-125e5642e81e
author: rothja
ms.author: jroth
ms.openlocfilehash: fc2a0fa7f8409767a2afaa9c4c621ea72732b701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709490"
---
# <a name="srv_paramlen-extended-stored-procedure-api"></a><span data-ttu-id="39d0d-102">srv_paramlen (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="39d0d-102">srv_paramlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="39d0d-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="39d0d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="39d0d-104">傳回遠端預存程序呼叫參數的資料長度。</span><span class="sxs-lookup"><span data-stu-id="39d0d-104">Returns the data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="39d0d-105">此函式已被 **srv_paraminfo** 函式取代。</span><span class="sxs-lookup"><span data-stu-id="39d0d-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d0d-106">語法</span><span class="sxs-lookup"><span data-stu-id="39d0d-106">Syntax</span></span>  
  
```  
  
int srv_paramlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="39d0d-107">引數</span><span class="sxs-lookup"><span data-stu-id="39d0d-107">Arguments</span></span>  
 <span data-ttu-id="39d0d-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="39d0d-108">*srvproc*</span></span>  
 <span data-ttu-id="39d0d-109">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="39d0d-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="39d0d-110">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="39d0d-110">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="39d0d-111">*n*</span><span class="sxs-lookup"><span data-stu-id="39d0d-111">*n*</span></span>  
 <span data-ttu-id="39d0d-112">這指出參數的數目。</span><span class="sxs-lookup"><span data-stu-id="39d0d-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="39d0d-113">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="39d0d-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="39d0d-114">傳回</span><span class="sxs-lookup"><span data-stu-id="39d0d-114">Returns</span></span>  
 <span data-ttu-id="39d0d-115">這是參數資料的實際長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="39d0d-115">The actual length, in bytes, of the parameter data.</span></span> <span data-ttu-id="39d0d-116">如果沒有第 *n* 個參數或是沒有任何遠端預存程序，其會傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="39d0d-116">If there is no *n*th parameter or there is no remote stored procedure, it returns -1.</span></span> <span data-ttu-id="39d0d-117">如果第 *n* 個參數為 NULL，其會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="39d0d-117">If the *n*th parameter is NULL, it returns 0.</span></span>  
  
 <span data-ttu-id="39d0d-118">如果參數是下列其中一個 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 系統資料類型，此函數會傳回下列值 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="39d0d-118">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] system data types.</span></span>  
  
|<span data-ttu-id="39d0d-119">新的資料類型</span><span class="sxs-lookup"><span data-stu-id="39d0d-119">New data types</span></span>|<span data-ttu-id="39d0d-120">輸入資料長度</span><span class="sxs-lookup"><span data-stu-id="39d0d-120">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="39d0d-121">**NULL：** 1</span><span class="sxs-lookup"><span data-stu-id="39d0d-121">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="39d0d-122">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="39d0d-122">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="39d0d-123">**>= 255：** N/A</span><span class="sxs-lookup"><span data-stu-id="39d0d-123">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="39d0d-124">**<255：** N/A</span><span class="sxs-lookup"><span data-stu-id="39d0d-124">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="39d0d-125">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="39d0d-125">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="39d0d-126">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="39d0d-126">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="39d0d-127">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-127">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-128">**<255：** 實際 *len*</span><span class="sxs-lookup"><span data-stu-id="39d0d-128">**<255:** actual *len*</span></span>|  
|`BIGCHAR`|<span data-ttu-id="39d0d-129">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="39d0d-129">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="39d0d-130">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-130">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-131">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-131">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-132">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-132">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="39d0d-133">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="39d0d-133">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="39d0d-134">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-134">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-135">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-135">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-136">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-136">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="39d0d-137">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="39d0d-137">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="39d0d-138">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="39d0d-138">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="39d0d-139">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-139">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-140">**<255：** 實際 *len*</span><span class="sxs-lookup"><span data-stu-id="39d0d-140">**<255:** actual *len*</span></span>|  
|`NCHAR`|<span data-ttu-id="39d0d-141">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="39d0d-141">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="39d0d-142">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-142">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-143">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-143">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-144">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-144">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="39d0d-145">**NULL：** 0</span><span class="sxs-lookup"><span data-stu-id="39d0d-145">**NULL:** 0</span></span><br /><br /> <span data-ttu-id="39d0d-146">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="39d0d-146">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="39d0d-147">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="39d0d-147">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="39d0d-148">**<255：** 實際 *len*</span><span class="sxs-lookup"><span data-stu-id="39d0d-148">**<255:** actual *len*</span></span>|  
|`NTEXT`|<span data-ttu-id="39d0d-149">**Null：** -1</span><span class="sxs-lookup"><span data-stu-id="39d0d-149">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="39d0d-150">**ZERO：**-1</span><span class="sxs-lookup"><span data-stu-id="39d0d-150">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="39d0d-151">**>= 255：** -1</span><span class="sxs-lookup"><span data-stu-id="39d0d-151">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="39d0d-152">**<255：** -1</span><span class="sxs-lookup"><span data-stu-id="39d0d-152">**<255:** -1</span></span>|  
  
 <span data-ttu-id="39d0d-153">\*   實際 *len* = 多位元組字元字串 (cch) 的長度</span><span class="sxs-lookup"><span data-stu-id="39d0d-153">\*   actual *len* = Length of multibyte character string (cch)</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39d0d-154">備註</span><span class="sxs-lookup"><span data-stu-id="39d0d-154">Remarks</span></span>  
 <span data-ttu-id="39d0d-155">每個遠端預存程序參數都具有實際和最大的資料長度。</span><span class="sxs-lookup"><span data-stu-id="39d0d-155">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="39d0d-156">對於不允許 null 值的標準固定長度資料類型，實際和最大的長度是相同的。</span><span class="sxs-lookup"><span data-stu-id="39d0d-156">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="39d0d-157">對於可變長度資料類型，長度則可以有所不同。</span><span class="sxs-lookup"><span data-stu-id="39d0d-157">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="39d0d-158">例如，宣告為 `varchar(30)` 的參數可能擁有只有 10 個位元組長的資料。</span><span class="sxs-lookup"><span data-stu-id="39d0d-158">For example, a parameter declared as `varchar(30)` can have data that is only 10 bytes long.</span></span> <span data-ttu-id="39d0d-159">參數的實際長度為 10，而其最大長度為 30。</span><span class="sxs-lookup"><span data-stu-id="39d0d-159">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="39d0d-160">**srv_paramlen** 函式會取得遠端預存程序的實際資料長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="39d0d-160">The **srv_paramlen** function gets the actual data length, in bytes, of a remote stored procedure.</span></span> <span data-ttu-id="39d0d-161">若要取得參數的最大資料長度，請使用 **srv_parammaxlen**。</span><span class="sxs-lookup"><span data-stu-id="39d0d-161">To obtain the maximum data length of a parameter, use **srv_parammaxlen**.</span></span>  
  
 <span data-ttu-id="39d0d-162">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="39d0d-162">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="39d0d-163">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="39d0d-163">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="39d0d-164">SRV_RPC 的處理常式仍會被呼叫，但看起來就好像沒有任何參數， **srv_rpcparams**會傳回0。</span><span class="sxs-lookup"><span data-stu-id="39d0d-164">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="39d0d-165">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="39d0d-165">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="39d0d-166">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="39d0d-166">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d0d-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39d0d-167">See Also</span></span>  
 <span data-ttu-id="39d0d-168">[srv_paraminfo &#40;擴充預存程式 API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="39d0d-168">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="39d0d-169">srv_rpcparams &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="39d0d-169">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
