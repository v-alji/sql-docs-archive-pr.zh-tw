---
title: srv_rpcparams (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcparams
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
author: rothja
ms.author: jroth
ms.openlocfilehash: 443b9ea8a67341afdb92f0c384148c8b1b42f752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710601"
---
# <a name="srv_rpcparams-extended-stored-procedure-api"></a><span data-ttu-id="4b048-102">srv_rpcparams (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="4b048-102">srv_rpcparams (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="4b048-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="4b048-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="4b048-104">傳回目前遠端預存程序的參數數目。</span><span class="sxs-lookup"><span data-stu-id="4b048-104">Returns the number of parameters for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b048-105">語法</span><span class="sxs-lookup"><span data-stu-id="4b048-105">Syntax</span></span>  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b048-106">引數</span><span class="sxs-lookup"><span data-stu-id="4b048-106">Arguments</span></span>  
 <span data-ttu-id="4b048-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="4b048-107">*srvproc*</span></span>  
 <span data-ttu-id="4b048-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序)。</span><span class="sxs-lookup"><span data-stu-id="4b048-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="4b048-109">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="4b048-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="4b048-110">傳回</span><span class="sxs-lookup"><span data-stu-id="4b048-110">Returns</span></span>  
 <span data-ttu-id="4b048-111">遠端預存程序中的參數數目。</span><span class="sxs-lookup"><span data-stu-id="4b048-111">The number of parameters in the remote stored procedure.</span></span> <span data-ttu-id="4b048-112">如果在遠端預存程序中沒有參數，或者沒有目前的遠端預存程序，則會傳回 -1，並發生資訊錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b048-112">If there are no parameters in the remote stored procedure or if there is not a current remote stored procedure, -1 is returned and an information error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b048-113">備註</span><span class="sxs-lookup"><span data-stu-id="4b048-113">Remarks</span></span>  
 <span data-ttu-id="4b048-114">此函數會傳回目前遠端預存程序中的參數數目。</span><span class="sxs-lookup"><span data-stu-id="4b048-114">This function returns the number of parameters in the current remote stored procedure.</span></span> <span data-ttu-id="4b048-115">它通常會從遠端預存程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="4b048-115">It is usually called from the remote stored procedure.</span></span>  
  
 <span data-ttu-id="4b048-116">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="4b048-116">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="4b048-117">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b048-117">If the remote stored procedure call was made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="4b048-118">發生這個錯誤時，會呼叫遠端預存程序處理常式，但是它不會接收參數，而且 **srv_rpcparams** 會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="4b048-118">When this error occurs, the remote stored procedure handler is called, but it does not receive the parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4b048-119">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="4b048-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="4b048-120">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="4b048-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
