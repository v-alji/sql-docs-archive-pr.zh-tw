---
title: srv_parammaxlen (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_parammaxlen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
ms.openlocfilehash: b289743b3de4b115a67a029dcc0261854ee3a40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709486"
---
# <a name="srv_parammaxlen-extended-stored-procedure-api"></a><span data-ttu-id="92ab8-102">srv_parammaxlen (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="92ab8-102">srv_parammaxlen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="92ab8-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="92ab8-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="92ab8-104">傳回遠端預存程序呼叫參數的最大資料長度。</span><span class="sxs-lookup"><span data-stu-id="92ab8-104">Returns the maximum data length of a remote stored procedure call parameter.</span></span> <span data-ttu-id="92ab8-105">此函式已被 **srv_paraminfo** 函式取代。</span><span class="sxs-lookup"><span data-stu-id="92ab8-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92ab8-106">語法</span><span class="sxs-lookup"><span data-stu-id="92ab8-106">Syntax</span></span>  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="92ab8-107">引數</span><span class="sxs-lookup"><span data-stu-id="92ab8-107">Arguments</span></span>  
 <span data-ttu-id="92ab8-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="92ab8-108">*srvproc*</span></span>  
 <span data-ttu-id="92ab8-109">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="92ab8-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="92ab8-110">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="92ab8-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="92ab8-111">*n*</span><span class="sxs-lookup"><span data-stu-id="92ab8-111">*n*</span></span>  
 <span data-ttu-id="92ab8-112">這指出參數的數目。</span><span class="sxs-lookup"><span data-stu-id="92ab8-112">Indicates the number of the parameter.</span></span> <span data-ttu-id="92ab8-113">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="92ab8-113">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="92ab8-114">傳回</span><span class="sxs-lookup"><span data-stu-id="92ab8-114">Returns</span></span>  
 <span data-ttu-id="92ab8-115">這是參數資料的最大長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="92ab8-115">The maximum length, in bytes, of the parameter data.</span></span> <span data-ttu-id="92ab8-116">如果沒有第 *n* 個參數或是沒有任何遠端預存程序，其會傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="92ab8-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
 <span data-ttu-id="92ab8-117">如果參數是下列其中一種資料類型，此函數會傳回下列值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="92ab8-117">This function returns the following values, if the parameter is one of the following [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span>  
  
|<span data-ttu-id="92ab8-118">新的資料類型</span><span class="sxs-lookup"><span data-stu-id="92ab8-118">New data types</span></span>|<span data-ttu-id="92ab8-119">輸入資料長度</span><span class="sxs-lookup"><span data-stu-id="92ab8-119">Input data length</span></span>|  
|--------------------|-----------------------|  
|`BITN`|<span data-ttu-id="92ab8-120">**NULL：** 1</span><span class="sxs-lookup"><span data-stu-id="92ab8-120">**NULL:** 1</span></span><br /><br /> <span data-ttu-id="92ab8-121">**零：** 1</span><span class="sxs-lookup"><span data-stu-id="92ab8-121">**ZERO:** 1</span></span><br /><br /> <span data-ttu-id="92ab8-122">**>= 255：** N/A</span><span class="sxs-lookup"><span data-stu-id="92ab8-122">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="92ab8-123">**<255：** N/A</span><span class="sxs-lookup"><span data-stu-id="92ab8-123">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="92ab8-124">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-124">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-125">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-125">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-126">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-126">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-127">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-127">**<255:** 255</span></span>|  
|`BIGCHAR`|<span data-ttu-id="92ab8-128">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-128">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-129">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-129">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-130">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-130">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-131">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-131">**<255:** 255</span></span>|  
|`BIGBINARY`|<span data-ttu-id="92ab8-132">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-132">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-133">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-133">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-134">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-134">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-135">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-135">**<255:** 255</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="92ab8-136">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-136">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-137">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-137">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-138">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-138">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-139">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-139">**<255:** 255</span></span>|  
|`NCHAR`|<span data-ttu-id="92ab8-140">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-140">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-141">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-141">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-142">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-142">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-143">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-143">**<255:** 255</span></span>|  
|`NVARCHAR`|<span data-ttu-id="92ab8-144">**NULL：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-144">**NULL:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-145">**ZERO：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-145">**ZERO:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-146">**>= 255：** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-146">**>=255:** 255</span></span><br /><br /> <span data-ttu-id="92ab8-147">**<255:** 255</span><span class="sxs-lookup"><span data-stu-id="92ab8-147">**<255:** 255</span></span>|  
|`NTEXT`|<span data-ttu-id="92ab8-148">**Null：** -1</span><span class="sxs-lookup"><span data-stu-id="92ab8-148">**NULL:** -1</span></span><br /><br /> <span data-ttu-id="92ab8-149">**ZERO：**-1</span><span class="sxs-lookup"><span data-stu-id="92ab8-149">**ZERO:** -1</span></span><br /><br /> <span data-ttu-id="92ab8-150">**>= 255：** -1</span><span class="sxs-lookup"><span data-stu-id="92ab8-150">**>=255:** -1</span></span><br /><br /> <span data-ttu-id="92ab8-151">\*\* \< 255：\*\* -1</span><span class="sxs-lookup"><span data-stu-id="92ab8-151">**\<255:** -1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92ab8-152">備註</span><span class="sxs-lookup"><span data-stu-id="92ab8-152">Remarks</span></span>  
 <span data-ttu-id="92ab8-153">每個遠端預存程序參數都具有實際和最大的資料長度。</span><span class="sxs-lookup"><span data-stu-id="92ab8-153">Each remote stored procedure parameter has an actual and a maximum data length.</span></span> <span data-ttu-id="92ab8-154">對於不允許 null 值的標準固定長度資料類型，實際和最大的長度是相同的。</span><span class="sxs-lookup"><span data-stu-id="92ab8-154">For standard fixed-length data types that do not allow null values, the actual and maximum lengths are the same.</span></span> <span data-ttu-id="92ab8-155">對於可變長度資料類型，長度則可以有所不同。</span><span class="sxs-lookup"><span data-stu-id="92ab8-155">For variable-length data types, the lengths can vary.</span></span> <span data-ttu-id="92ab8-156">例如，宣告為 **varchar(30)** 的參數可能擁有只有 10 個位元組長的資料。</span><span class="sxs-lookup"><span data-stu-id="92ab8-156">For example, a parameter declared as **varchar(30)** can have data that is only 10 bytes long.</span></span> <span data-ttu-id="92ab8-157">參數的實際長度為 10，而其最大長度為 30。</span><span class="sxs-lookup"><span data-stu-id="92ab8-157">The parameter's actual length is 10 and its maximum length is 30.</span></span> <span data-ttu-id="92ab8-158">**srv_parammaxlen** 函式會取得遠端預存程序的最大資料長度。</span><span class="sxs-lookup"><span data-stu-id="92ab8-158">The **srv_parammaxlen** function gets the maximum data length of a remote stored procedure.</span></span> <span data-ttu-id="92ab8-159">若要取得參數的實際長度，請使用 **srv_paramlen**。</span><span class="sxs-lookup"><span data-stu-id="92ab8-159">To obtain the actual length of a parameter, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="92ab8-160">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="92ab8-160">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="92ab8-161">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="92ab8-161">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="92ab8-162">雖然仍會呼叫 SRV_RPC 處理常式，但是看起來好像沒有參數，而且 **srv_rpcparams** 會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="92ab8-162">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="92ab8-163">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="92ab8-163">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="92ab8-164">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="92ab8-164">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ab8-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92ab8-165">See Also</span></span>  
 <span data-ttu-id="92ab8-166">[srv_paraminfo &#40;擴充預存程式 API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="92ab8-166">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="92ab8-167">srv_rpcparams &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="92ab8-167">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
