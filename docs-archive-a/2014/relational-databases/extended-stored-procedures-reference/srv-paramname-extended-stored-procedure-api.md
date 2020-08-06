---
title: srv_paramname (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramname
ms.assetid: 1a53d707-7b06-49cc-a0df-ac727cfe953f
author: rothja
ms.author: jroth
ms.openlocfilehash: 2227ac3d46efe7d09abc05964248229f3533d42d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709485"
---
# <a name="srv_paramname-extended-stored-procedure-api"></a><span data-ttu-id="89cc7-102">srv_paramname (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="89cc7-102">srv_paramname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="89cc7-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="89cc7-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="89cc7-104">傳回遠端預存程序呼叫參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="89cc7-104">Returns the name of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89cc7-105">語法</span><span class="sxs-lookup"><span data-stu-id="89cc7-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_paramname (  
SRV_PROC * srvproc,intn, int *len );  
```  
  
## <a name="arguments"></a><span data-ttu-id="89cc7-106">引數</span><span class="sxs-lookup"><span data-stu-id="89cc7-106">Arguments</span></span>  
 <span data-ttu-id="89cc7-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="89cc7-107">*srvproc*</span></span>  
 <span data-ttu-id="89cc7-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="89cc7-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="89cc7-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="89cc7-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="89cc7-110">*n*</span><span class="sxs-lookup"><span data-stu-id="89cc7-110">*n*</span></span>  
 <span data-ttu-id="89cc7-111">這指出參數的數目。</span><span class="sxs-lookup"><span data-stu-id="89cc7-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="89cc7-112">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="89cc7-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="89cc7-113">*len*</span><span class="sxs-lookup"><span data-stu-id="89cc7-113">*len*</span></span>  
 <span data-ttu-id="89cc7-114">提供包含參數名稱長度 (以位元組為單位) 之 `int` 變數的指標。</span><span class="sxs-lookup"><span data-stu-id="89cc7-114">Provides a pointer to an `int` variable that contains the length, in bytes, of the parameter name.</span></span> <span data-ttu-id="89cc7-115">如果 *len* 為 NULL，則不會傳回遠端預存程序參數名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="89cc7-115">If *len* is NULL, the length of the remote stored procedure parameter name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="89cc7-116">傳回</span><span class="sxs-lookup"><span data-stu-id="89cc7-116">Returns</span></span>  
 <span data-ttu-id="89cc7-117">包含參數名稱且以 Null 結束之字元字串的指標。</span><span class="sxs-lookup"><span data-stu-id="89cc7-117">A pointer to a null-terminated character string that contains the parameter name.</span></span> <span data-ttu-id="89cc7-118">參數名稱的長度會儲存在 *len* 中。</span><span class="sxs-lookup"><span data-stu-id="89cc7-118">The length of the parameter name is stored in *len*.</span></span> <span data-ttu-id="89cc7-119">如果沒有第 *n* 個參數或沒有任何遠端預存程序，其會傳回 NULL、將 *len* 設定為 -1，並會傳送參考用錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="89cc7-119">If there is no *n*th parameter or no remote stored procedure, it returns NULL, *len* is set to -1, and an informational error message is sent.</span></span> <span data-ttu-id="89cc7-120">如果參數名稱為 NULL，*len* 就會設定為 0，而且傳回以 Null 結束的空字串。</span><span class="sxs-lookup"><span data-stu-id="89cc7-120">If the parameter name is NULL, *len* is set to 0 and a null-terminated empty string is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89cc7-121">備註</span><span class="sxs-lookup"><span data-stu-id="89cc7-121">Remarks</span></span>  
 <span data-ttu-id="89cc7-122">這個函數會取得遠端預存程序呼叫參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="89cc7-122">This function gets the name of a remote stored procedure call parameter.</span></span> <span data-ttu-id="89cc7-123">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="89cc7-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="89cc7-124">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="89cc7-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="89cc7-125">雖然仍會呼叫 SRV_RPC 處理常式，但是看起來好像沒有參數，而且 **srv_rpcparams** 會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="89cc7-125">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="89cc7-126">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="89cc7-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="89cc7-127">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="89cc7-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89cc7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89cc7-128">See Also</span></span>  
 [<span data-ttu-id="89cc7-129">srv_rpcparams &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="89cc7-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
