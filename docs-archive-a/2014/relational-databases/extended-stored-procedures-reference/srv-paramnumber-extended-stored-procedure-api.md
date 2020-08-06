---
title: srv_paramnumber (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramnumber
ms.assetid: d7a6dbff-71d9-4297-8a4f-bfd2876fe204
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e621101c909ef251c40f38713e438d8e40d08a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598390"
---
# <a name="srv_paramnumber-extended-stored-procedure-api"></a><span data-ttu-id="5177d-102">srv_paramnumber (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="5177d-102">srv_paramnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="5177d-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="5177d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="5177d-104">傳回遠端預存程序呼叫參數的編號。</span><span class="sxs-lookup"><span data-stu-id="5177d-104">Returns the number of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5177d-105">語法</span><span class="sxs-lookup"><span data-stu-id="5177d-105">Syntax</span></span>  
  
```  
  
int srv_paramnumber (  
SRV_PROC *  
srvproc  
,  
DBCHAR *  
name  
,   
int  
namelen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="5177d-106">引數</span><span class="sxs-lookup"><span data-stu-id="5177d-106">Arguments</span></span>  
 <span data-ttu-id="5177d-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="5177d-107">*srvproc*</span></span>  
 <span data-ttu-id="5177d-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="5177d-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="5177d-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="5177d-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="5177d-110">*name*</span><span class="sxs-lookup"><span data-stu-id="5177d-110">*name*</span></span>  
 <span data-ttu-id="5177d-111">這是 *name* 參數的指標。</span><span class="sxs-lookup"><span data-stu-id="5177d-111">Is a pointer to the parameter *name*.</span></span>  
  
 <span data-ttu-id="5177d-112">*namelen*</span><span class="sxs-lookup"><span data-stu-id="5177d-112">*namelen*</span></span>  
 <span data-ttu-id="5177d-113">這是 *name* 的長度。</span><span class="sxs-lookup"><span data-stu-id="5177d-113">Is the length of *name*.</span></span> <span data-ttu-id="5177d-114">如果 *name* 是以 null 結尾，請將 *namelen* 設定為 SRV_NULLTERM。</span><span class="sxs-lookup"><span data-stu-id="5177d-114">If *name* is null-terminated, set *namelen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5177d-115">傳回</span><span class="sxs-lookup"><span data-stu-id="5177d-115">Returns</span></span>  
 <span data-ttu-id="5177d-116">是具名參數的參數編號。</span><span class="sxs-lookup"><span data-stu-id="5177d-116">The parameter number of the named parameter.</span></span> <span data-ttu-id="5177d-117">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="5177d-117">The first parameter is 1.</span></span> <span data-ttu-id="5177d-118">如果沒有命名為 *name* 的參數，或者沒有遠端預存程序，則會傳回 0，並且產生訊息。</span><span class="sxs-lookup"><span data-stu-id="5177d-118">If there is no parameter named *name* or no remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5177d-119">備註</span><span class="sxs-lookup"><span data-stu-id="5177d-119">Remarks</span></span>  
 <span data-ttu-id="5177d-120">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="5177d-120">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="5177d-121">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5177d-121">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="5177d-122">雖然仍會呼叫 SRV_RPC 處理常式，但是看起來好像沒有參數，而且 **srv_rpcparams** 會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="5177d-122">The SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5177d-123">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="5177d-123">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="5177d-124">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="5177d-124">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5177d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5177d-125">See Also</span></span>  
 [<span data-ttu-id="5177d-126">srv_rpcparams &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="5177d-126">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
