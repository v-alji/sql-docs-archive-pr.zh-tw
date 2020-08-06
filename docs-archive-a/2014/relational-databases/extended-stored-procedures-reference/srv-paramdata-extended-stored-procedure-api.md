---
title: srv_paramdata (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramdata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramdata
ms.assetid: 3104514d-b404-47c9-b6d7-928106384874
author: rothja
ms.author: jroth
ms.openlocfilehash: 092ca5b811a12c3e6b199a6041ce6e4f8e02f4b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598393"
---
# <a name="srv_paramdata-extended-stored-procedure-api"></a><span data-ttu-id="7064a-102">srv_paramdata (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="7064a-102">srv_paramdata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="7064a-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="7064a-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="7064a-104">傳回遠端預存程序呼叫參數的值。</span><span class="sxs-lookup"><span data-stu-id="7064a-104">Returns the value of a remote stored procedure call parameter.</span></span> <span data-ttu-id="7064a-105">此函式已被 **srv_paraminfo** 函式取代。</span><span class="sxs-lookup"><span data-stu-id="7064a-105">This function has been superseded by the **srv_paraminfo** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7064a-106">語法</span><span class="sxs-lookup"><span data-stu-id="7064a-106">Syntax</span></span>  
  
```  
  
void * srv_paramdata (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="7064a-107">引數</span><span class="sxs-lookup"><span data-stu-id="7064a-107">Arguments</span></span>  
 <span data-ttu-id="7064a-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="7064a-108">*srvproc*</span></span>  
 <span data-ttu-id="7064a-109">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="7064a-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="7064a-110">擴充預存程序程式庫會使用該結構所包含的資訊，來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="7064a-110">The structure contains information the Extended Stored Procedure library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="7064a-111">*n*</span><span class="sxs-lookup"><span data-stu-id="7064a-111">*n*</span></span>  
 <span data-ttu-id="7064a-112">這是參數的數目。</span><span class="sxs-lookup"><span data-stu-id="7064a-112">Is the number of the parameter.</span></span> <span data-ttu-id="7064a-113">第一個參數是數字 1。</span><span class="sxs-lookup"><span data-stu-id="7064a-113">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7064a-114">傳回</span><span class="sxs-lookup"><span data-stu-id="7064a-114">Returns</span></span>  
 <span data-ttu-id="7064a-115">參數值的指標。</span><span class="sxs-lookup"><span data-stu-id="7064a-115">A pointer to the parameter value.</span></span> <span data-ttu-id="7064a-116">如果第 *n* 個參數為 NULL、沒有第 *n* 個參數，或是沒有任何遠端預存程序，會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="7064a-116">If the *n*th parameter is NULL, there is no *n*th parameter, or there is no remote stored procedure, returns NULL.</span></span> <span data-ttu-id="7064a-117">如果參數值為字串，則可能不會以 Null 結束。</span><span class="sxs-lookup"><span data-stu-id="7064a-117">If the parameter value is a string, it might not be null-terminated.</span></span> <span data-ttu-id="7064a-118">請使用 **srv_paramlen** 來判斷字串的長度。</span><span class="sxs-lookup"><span data-stu-id="7064a-118">Use **srv_paramlen** to determine the length of the string.</span></span>  
  
 <span data-ttu-id="7064a-119">如果參數是其中一個資料類型，此函數會傳回下列值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7064a-119">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types.</span></span> <span data-ttu-id="7064a-120">指標資料包含資料類型的指標是否為有效 (VP)、NULL 或不適用 (N/A)，以及資料所指向的內容。</span><span class="sxs-lookup"><span data-stu-id="7064a-120">Pointer data includes whether the pointer for the data type is valid (VP), NULL, or not applicable (N/A), and the contents of the data pointed to.</span></span>  
  
|<span data-ttu-id="7064a-121">新的資料類型</span><span class="sxs-lookup"><span data-stu-id="7064a-121">New data types</span></span>|<span data-ttu-id="7064a-122">輸入資料長度</span><span class="sxs-lookup"><span data-stu-id="7064a-122">Input data length</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="7064a-123">BITN</span><span class="sxs-lookup"><span data-stu-id="7064a-123">BITN</span></span>|<span data-ttu-id="7064a-124">**NULL：** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="7064a-124">**NULL:** VP, NULL</span></span><br /><br /> <span data-ttu-id="7064a-125">**ZERO：** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="7064a-125">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="7064a-126">**>= 255：** N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-126">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="7064a-127">**<255：** N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-127">**<255:** N/A</span></span>|  
|<span data-ttu-id="7064a-128">BIGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="7064a-128">BIGVARCHAR</span></span>|<span data-ttu-id="7064a-129">**NULL：** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-129">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="7064a-130">**ZERO：** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="7064a-130">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="7064a-131">**>=255：** VP、255 個字元</span><span class="sxs-lookup"><span data-stu-id="7064a-131">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="7064a-132">**<255：** VP、實際資料</span><span class="sxs-lookup"><span data-stu-id="7064a-132">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="7064a-133">BIGCHAR</span><span class="sxs-lookup"><span data-stu-id="7064a-133">BIGCHAR</span></span>|<span data-ttu-id="7064a-134">**NULL：** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-134">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="7064a-135">**ZERO：** VP、255 個空格</span><span class="sxs-lookup"><span data-stu-id="7064a-135">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="7064a-136">**>=255：** VP、255 個字元</span><span class="sxs-lookup"><span data-stu-id="7064a-136">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="7064a-137">**<255：** VP、實際資料 + 填補 (最多 255)</span><span class="sxs-lookup"><span data-stu-id="7064a-137">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="7064a-138">BIGBINARY</span><span class="sxs-lookup"><span data-stu-id="7064a-138">BIGBINARY</span></span>|<span data-ttu-id="7064a-139">**NULL：** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-139">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="7064a-140">**ZERO：** VP、255 0x00</span><span class="sxs-lookup"><span data-stu-id="7064a-140">**ZERO:** VP, 255 0x00</span></span><br /><br /> <span data-ttu-id="7064a-141">**>=255：** VP、255 個位元組</span><span class="sxs-lookup"><span data-stu-id="7064a-141">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="7064a-142">**<255：** VP、實際資料 + 填補 (最多 255)</span><span class="sxs-lookup"><span data-stu-id="7064a-142">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="7064a-143">BIGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="7064a-143">BIGVARBINARY</span></span>|<span data-ttu-id="7064a-144">**NULL：** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-144">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="7064a-145">**ZERO：** VP、0x00</span><span class="sxs-lookup"><span data-stu-id="7064a-145">**ZERO:** VP, 0x00</span></span><br /><br /> <span data-ttu-id="7064a-146">**>=255：** VP、255 個位元組</span><span class="sxs-lookup"><span data-stu-id="7064a-146">**>=255:** VP, 255 bytes</span></span><br /><br /> <span data-ttu-id="7064a-147">**<255：** VP、實際資料</span><span class="sxs-lookup"><span data-stu-id="7064a-147">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="7064a-148">NCHAR</span><span class="sxs-lookup"><span data-stu-id="7064a-148">NCHAR</span></span>|<span data-ttu-id="7064a-149">**NULL：** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-149">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="7064a-150">**ZERO：** VP、255 個空格</span><span class="sxs-lookup"><span data-stu-id="7064a-150">**ZERO:** VP, 255 spaces</span></span><br /><br /> <span data-ttu-id="7064a-151">**>=255：** VP、255 個字元</span><span class="sxs-lookup"><span data-stu-id="7064a-151">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="7064a-152">**<255：** VP、實際資料 + 填補 (最多 255)</span><span class="sxs-lookup"><span data-stu-id="7064a-152">**<255:** VP, actual data + padding (up to 255)</span></span>|  
|<span data-ttu-id="7064a-153">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="7064a-153">NVARCHAR</span></span>|<span data-ttu-id="7064a-154">**NULL：** NULL、N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-154">**NULL:** NULL, N/A</span></span><br /><br /> <span data-ttu-id="7064a-155">**ZERO：** VP、NULL</span><span class="sxs-lookup"><span data-stu-id="7064a-155">**ZERO:** VP, NULL</span></span><br /><br /> <span data-ttu-id="7064a-156">**>=255：** VP、255 個字元</span><span class="sxs-lookup"><span data-stu-id="7064a-156">**>=255:** VP, 255 chars</span></span><br /><br /> <span data-ttu-id="7064a-157">**<255：** VP、實際資料</span><span class="sxs-lookup"><span data-stu-id="7064a-157">**<255:** VP, actual data</span></span>|  
|<span data-ttu-id="7064a-158">NTEXT</span><span class="sxs-lookup"><span data-stu-id="7064a-158">NTEXT</span></span>|<span data-ttu-id="7064a-159">**NULL：** N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-159">**NULL:** N/A</span></span><br /><br /> <span data-ttu-id="7064a-160">**ZERO：** N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-160">**ZERO:** N/A</span></span><br /><br /> <span data-ttu-id="7064a-161">**>= 255：** N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-161">**>=255:** N/A</span></span><br /><br /> <span data-ttu-id="7064a-162">\*\* \< 255：\*\* N/A</span><span class="sxs-lookup"><span data-stu-id="7064a-162">**\<255:** N/A</span></span>|  
  
 <span data-ttu-id="7064a-163">\*   資料不是以 Null 結束；在截斷 >255 個字元的資料時，不會發出警告。</span><span class="sxs-lookup"><span data-stu-id="7064a-163">\*   data is not null-terminated; no warning is issued on truncation for data >255 characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7064a-164">備註</span><span class="sxs-lookup"><span data-stu-id="7064a-164">Remarks</span></span>  
 <span data-ttu-id="7064a-165">如果您知道參數名稱，可以使用 **srv_paramnumber** 來取得參數數目。</span><span class="sxs-lookup"><span data-stu-id="7064a-165">If you know the parameter name, you can use **srv_paramnumber** to get the parameter number.</span></span> <span data-ttu-id="7064a-166">若要判斷參數是否為 NULL，請使用 **srv_paramlen**。</span><span class="sxs-lookup"><span data-stu-id="7064a-166">To determine whether a parameter is NULL, use **srv_paramlen**.</span></span>  
  
 <span data-ttu-id="7064a-167">當遠端預存程序呼叫是用參數進行時，可以依名稱或位置 (未命名) 傳遞參數。</span><span class="sxs-lookup"><span data-stu-id="7064a-167">When a remote stored procedure call is made with parameters, the parameters can be passed by name or by position (unnamed).</span></span> <span data-ttu-id="7064a-168">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7064a-168">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="7064a-169">如果發生錯誤，則仍會呼叫 SRV_RPC 處理常式，但會看來好像沒有參數一般，而且 **srv_rpcparams** 會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="7064a-169">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7064a-170">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="7064a-170">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="7064a-171">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="7064a-171">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7064a-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7064a-172">See Also</span></span>  
 [<span data-ttu-id="7064a-173">srv_rpcparams &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="7064a-173">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
