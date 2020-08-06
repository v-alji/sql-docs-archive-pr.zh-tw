---
title: srv_paramset (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramset
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ebe308e5e0c8fc24382582fb71db2f48c77541e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592019"
---
# <a name="srv_paramset-extended-stored-procedure-api"></a><span data-ttu-id="47fae-102">srv_paramset (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="47fae-102">srv_paramset (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="47fae-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="47fae-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="47fae-104">設定遠端預存程序呼叫傳回參數的值。</span><span class="sxs-lookup"><span data-stu-id="47fae-104">Sets the value of a remote stored procedure call return parameter.</span></span> <span data-ttu-id="47fae-105">此函式已被 **srv_paramsetoutput** 函式取代。</span><span class="sxs-lookup"><span data-stu-id="47fae-105">This function has been superseded by the **srv_paramsetoutput** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47fae-106">語法</span><span class="sxs-lookup"><span data-stu-id="47fae-106">Syntax</span></span>  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="47fae-107">引數</span><span class="sxs-lookup"><span data-stu-id="47fae-107">Arguments</span></span>  
 <span data-ttu-id="47fae-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="47fae-108">*srvproc*</span></span>  
 <span data-ttu-id="47fae-109">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="47fae-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="47fae-110">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="47fae-110">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="47fae-111">*n*</span><span class="sxs-lookup"><span data-stu-id="47fae-111">*n*</span></span>  
 <span data-ttu-id="47fae-112">表示要設定的參數數目。</span><span class="sxs-lookup"><span data-stu-id="47fae-112">Indicates the number of the parameter to set.</span></span> <span data-ttu-id="47fae-113">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="47fae-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="47fae-114">*data*</span><span class="sxs-lookup"><span data-stu-id="47fae-114">*data*</span></span>  
 <span data-ttu-id="47fae-115">這是指向要當做遠端預存程序傳回參數傳回給用戶端之資料值的指標。</span><span class="sxs-lookup"><span data-stu-id="47fae-115">Is a pointer to the data value to be sent back to the client as the remote stored procedure return parameter.</span></span>  
  
 <span data-ttu-id="47fae-116">*len*</span><span class="sxs-lookup"><span data-stu-id="47fae-116">*len*</span></span>  
 <span data-ttu-id="47fae-117">指定要傳回之資料的實際長度。</span><span class="sxs-lookup"><span data-stu-id="47fae-117">Specifies the actual length of the data to be returned.</span></span> <span data-ttu-id="47fae-118">如果參數的資料類型具有固定長度，而且不允許 null 值 (例如 *srvbit* 或 *srvint1*)，則會忽略 *len*。</span><span class="sxs-lookup"><span data-stu-id="47fae-118">If the data type of the parameter is of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *len* is ignored.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="47fae-119">傳回</span><span class="sxs-lookup"><span data-stu-id="47fae-119">Returns</span></span>  
 <span data-ttu-id="47fae-120">如果參數值設定成功則會傳回 SUCCEED，否則會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="47fae-120">SUCCEED if the parameter value was successfully set; otherwise, FAIL.</span></span> <span data-ttu-id="47fae-121">目前沒有任何遠端預存程序、沒有第 *n* 個遠端預存程序參數、此參數並非傳回參數，以及 *len* 引數不合法時，會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="47fae-121">FAIL is returned when there is no current remote stored procedure, when there is no *n*th remote stored procedure parameter, when the parameter is not a return parameter, and when the *len* argument is not legal.</span></span>  
  
 <span data-ttu-id="47fae-122">如果 *len* 是 0，它會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="47fae-122">If *len*is 0, it returns NULL.</span></span> <span data-ttu-id="47fae-123">將 *len* 設定為 0 是將 NULL 傳回給用戶端的唯一方法。</span><span class="sxs-lookup"><span data-stu-id="47fae-123">Setting *len* to 0 is the only way to return NULL to the client.</span></span>  
  
 <span data-ttu-id="47fae-124">如果參數是其中一種資料類型，此函數會傳回下列值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="47fae-124">This function returns the following values, if the parameter is one of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="47fae-125">新的資料類型</span><span class="sxs-lookup"><span data-stu-id="47fae-125">New data types</span></span>|<span data-ttu-id="47fae-126">傳回資料長度</span><span class="sxs-lookup"><span data-stu-id="47fae-126">Return data length</span></span>|  
|--------------------|------------------------|  
|`BITN`|<span data-ttu-id="47fae-127">**NULL：** *len* = 0、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-127">**NULL:** *len* = 0, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-128">**ZERO：** N/A</span><span class="sxs-lookup"><span data-stu-id="47fae-128">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="47fae-129">**>= 255：** N/A</span><span class="sxs-lookup"><span data-stu-id="47fae-129">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="47fae-130">**<255：** N/A</span><span class="sxs-lookup"><span data-stu-id="47fae-130">**<255:** N/A</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="47fae-131">**NULL：** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-131">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="47fae-132">**ZERO：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-132">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-133">**>=255：** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-133">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-134">**<255：** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-134">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGCHAR`|<span data-ttu-id="47fae-135">**NULL：** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-135">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="47fae-136">**ZERO：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-136">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-137">**>=255：** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-137">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-138">**<255：** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-138">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGBINARY`|<span data-ttu-id="47fae-139">**NULL：** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-139">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="47fae-140">**ZERO：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-140">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-141">**>=255：** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-141">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-142">**<255：** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-142">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="47fae-143">**NULL：** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-143">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="47fae-144">**ZERO：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-144">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-145">**>=255：** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-145">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-146">**<255：** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-146">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="47fae-147">NCHAR</span><span class="sxs-lookup"><span data-stu-id="47fae-147">NCHAR</span></span>|<span data-ttu-id="47fae-148">**NULL：** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-148">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="47fae-149">**ZERO：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-149">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-150">**>=255：** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-150">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-151">**<255：** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-151">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|<span data-ttu-id="47fae-152">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="47fae-152">NVARCHAR</span></span>|<span data-ttu-id="47fae-153">**NULL：** *len* = 0、data = IG、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-153">**NULL:** *len* = 0, data = IG, RET = 1</span></span><br /><br /> <span data-ttu-id="47fae-154">**ZERO：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-154">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-155">**>=255：** *len* = max8k、data = valid、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-155">**>=255:** *len* = max8k, data = valid, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-156">**<255：** *len* = <8k、data = valid、RET = 1</span><span class="sxs-lookup"><span data-stu-id="47fae-156">**<255:** *len* = <8k, data = valid, RET = 1</span></span>|  
|`NTEXT`|<span data-ttu-id="47fae-157">**NULL：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-157">**NULL:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-158">**ZERO：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-158">**ZERO:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-159">**>=255：** *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-159">**>=255:** *len* = IG, data = IG, RET = 0</span></span><br /><br /> <span data-ttu-id="47fae-160">\*\* \< 255：\*\* *len* = IG、data = IG、RET = 0</span><span class="sxs-lookup"><span data-stu-id="47fae-160">**\<255:** *len* = IG, data = IG, RET = 0</span></span>|  
|<span data-ttu-id="47fae-161">RET = srv_paramset 的傳回值</span><span class="sxs-lookup"><span data-stu-id="47fae-161">RET = Return value of srv_paramset</span></span>||  
|<span data-ttu-id="47fae-162">IG = 值將會被略過</span><span class="sxs-lookup"><span data-stu-id="47fae-162">IG = Value will be ignored</span></span>||  
|<span data-ttu-id="47fae-163">valid = 資料的任何有效指標</span><span class="sxs-lookup"><span data-stu-id="47fae-163">valid = Any valid pointer to data</span></span>||  
  
## <a name="remarks"></a><span data-ttu-id="47fae-164">備註</span><span class="sxs-lookup"><span data-stu-id="47fae-164">Remarks</span></span>  
 <span data-ttu-id="47fae-165">參數包含了在用戶端和應用程式之間傳遞的資料，其中包含遠端預存程序。</span><span class="sxs-lookup"><span data-stu-id="47fae-165">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="47fae-166">用戶端可以將某些參數指定為傳回參數。</span><span class="sxs-lookup"><span data-stu-id="47fae-166">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="47fae-167">這些傳回參數可包含「開放式資料服務」伺服器應用程式傳回給用戶端的值。</span><span class="sxs-lookup"><span data-stu-id="47fae-167">These return parameters can contain values that the Open Data Services server application passes back to the client.</span></span> <span data-ttu-id="47fae-168">使用傳回參數類似於依參考方式傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="47fae-168">Using return parameters is analogous to passing parameters by reference.</span></span>  
  
 <span data-ttu-id="47fae-169">您不能針對未當做傳回參數叫用的參數來設定傳回值。</span><span class="sxs-lookup"><span data-stu-id="47fae-169">You cannot set the return value for a parameter that wasn't invoked as a return parameter.</span></span> <span data-ttu-id="47fae-170">您可以使用 **srv_paramstatus** 來決定要如何叫用此參數。</span><span class="sxs-lookup"><span data-stu-id="47fae-170">You can use **srv_paramstatus** to determine how the parameter was invoked.</span></span>  
  
 <span data-ttu-id="47fae-171">這個函數會設定參數的傳回值，但是實際上並不會將傳回值傳給用戶端。</span><span class="sxs-lookup"><span data-stu-id="47fae-171">This function sets the return value for a parameter but it does not actually send the return value to the client.</span></span> <span data-ttu-id="47fae-172">當呼叫 **srv_senddone** 並有設定狀態旗標 SRV_DONE_FINAL 時，所有傳回參數 (不論是否已經使用 **srv_paramset** 來設定其傳回值) 都會自動傳給用戶端。</span><span class="sxs-lookup"><span data-stu-id="47fae-172">All return parameters, whether their return values have been set with **srv_paramset** or not, are automatically sent to the client when **srv_senddone** is called with the status flag SRV_DONE_FINAL set.</span></span>  
  
 <span data-ttu-id="47fae-173">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="47fae-173">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="47fae-174">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="47fae-174">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="47fae-175">雖然仍會呼叫 SRV_RPC 處理常式，但是看起來好像沒有參數，而且 **srv_rpcparams** 會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="47fae-175">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47fae-176">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="47fae-176">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="47fae-177">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="47fae-177">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47fae-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47fae-178">See Also</span></span>  
 [<span data-ttu-id="47fae-179">srv_paramsetoutput &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="47fae-179">srv_paramsetoutput &#40;Extended Stored Procedure API&#41;</span></span>](srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
