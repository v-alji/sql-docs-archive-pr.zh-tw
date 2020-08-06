---
title: srv_getbindtoken (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_getbindtoken
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_getbindtoken
ms.assetid: c947d011-08ac-4fb8-b925-3da6e0999277
author: rothja
ms.author: jroth
ms.openlocfilehash: d42f95c8a7df87f20ebaa30501b96b5f2a00815a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606312"
---
# <a name="srv_getbindtoken-extended-stored-procedure-api"></a><span data-ttu-id="39312-102">srv_getbindtoken (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="39312-102">srv_getbindtoken (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="39312-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="39312-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="39312-104">在目前的用戶端工作階段中取得叫用擴充預存程序之交易的繫結 Token。</span><span class="sxs-lookup"><span data-stu-id="39312-104">Obtains a bind token of the transaction in the current client session that invokes the extended stored procedure.</span></span>  
  
 <span data-ttu-id="39312-105">接著，擴充預存程序可以使用 **sp_bindsession**，將針對相同伺服器建立的任何新工作階段繫結至現有的交易，讓新的工作階段可以與叫用擴充預存程序的用戶端工作階段共用相同的交易鎖定空間。</span><span class="sxs-lookup"><span data-stu-id="39312-105">The extended stored procedure can then use **sp_bindsession** to bind any new session it creates against the same server to the existing transaction so that the new session can share the same transaction lock space with the client session that invoked the extended stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39312-106">語法</span><span class="sxs-lookup"><span data-stu-id="39312-106">Syntax</span></span>  
  
```  
  
int srv_getbindtoken (  
SRV_PROC*  
srvproc  
,  
char*  
bindtoken  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="39312-107">引數</span><span class="sxs-lookup"><span data-stu-id="39312-107">Arguments</span></span>  
 <span data-ttu-id="39312-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="39312-108">*srvproc*</span></span>  
 <span data-ttu-id="39312-109">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="39312-109">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="39312-110">此結構包含了擴充預存程序 API 程式庫用來管理應用程式與用戶端之間之通訊和資料的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="39312-110">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="39312-111">*bindtoken*</span><span class="sxs-lookup"><span data-stu-id="39312-111">*bindtoken*</span></span>  
 <span data-ttu-id="39312-112">這是將複製繫結 Token 所在緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="39312-112">Is a pointer to a buffer where the bind token will be copied.</span></span> <span data-ttu-id="39312-113">繫結 Token 會表示為以 null 結尾的字串。</span><span class="sxs-lookup"><span data-stu-id="39312-113">The bind token is represented as a null-terminated string.</span></span> <span data-ttu-id="39312-114">您指定的緩衝區長度至少應該為 255 個位元組。</span><span class="sxs-lookup"><span data-stu-id="39312-114">The buffer you specify should be at least 255 bytes in length.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="39312-115">傳回</span><span class="sxs-lookup"><span data-stu-id="39312-115">Returns</span></span>  
 <span data-ttu-id="39312-116">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="39312-116">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39312-117">備註</span><span class="sxs-lookup"><span data-stu-id="39312-117">Remarks</span></span>  
  
### <a name="to-bind-an-extended-stored-procedure-session-to-the-client-session-that-called-it-so-they-share-the-same-transaction-lock-space"></a><span data-ttu-id="39312-118">將擴充預存程序工作階段繫結到呼叫它的用戶端工作階段，讓它們可以共用相同的交易鎖定空間</span><span class="sxs-lookup"><span data-stu-id="39312-118">To bind an extended stored procedure session to the client session that called it so they share the same transaction lock space</span></span>  
  
1.  <span data-ttu-id="39312-119">擴充預存程序會呼叫 **svr_getbindtoken** 來取得工作階段中目前交易的繫結 Token。</span><span class="sxs-lookup"><span data-stu-id="39312-119">The extended stored procedure calls **svr_getbindtoken** to get the bind token for the current transaction in the session.</span></span> <span data-ttu-id="39312-120">此 Token 會以指定的 *bindtoken* 參數傳回。</span><span class="sxs-lookup"><span data-stu-id="39312-120">The token is returned in the given *bindtoken* parameter.</span></span>  
  
2.  <span data-ttu-id="39312-121">擴充預存程序會針對相同的伺服器開啟新的工作階段。</span><span class="sxs-lookup"><span data-stu-id="39312-121">The extended stored procedure opens new session(s) against the same server.</span></span> <span data-ttu-id="39312-122">在該工作階段內部，擴充預存程序會搭配 **sp_bindsession** 使用繫結 Token，將新的工作階段繫結到相同的交易。</span><span class="sxs-lookup"><span data-stu-id="39312-122">Inside that session, the extended stored procedure uses the bind token with **sp_bindsession** to bind the new session to the same transaction.</span></span> <span data-ttu-id="39312-123">擴充預存程序可以建立多個工作階段，並將所有工作階段繫結到相同的交易。</span><span class="sxs-lookup"><span data-stu-id="39312-123">The extended stored procedure can create multiple sessions and bind all the sessions to the same transaction.</span></span>  
  
3.  <span data-ttu-id="39312-124">當外部預存程序傳回時，或使用空字串呼叫 **sp_bindsession** 時，會取消繫結已繫結的工作階段。</span><span class="sxs-lookup"><span data-stu-id="39312-124">A bound session is unbound when the external stored procedure returns or when **sp_bindsession** is called with an empty string.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39312-125">一次只有一個繫結的工作階段可以存取共用連接。</span><span class="sxs-lookup"><span data-stu-id="39312-125">Only one bound session at a time can have access to a shared connection.</span></span> <span data-ttu-id="39312-126">如果某個工作階段目前正在伺服器上執行陳述式或等待伺服器的暫止結果，共用相同繫結連接的其他工作階段都無法存取伺服器，直到目前的工作階段完成執行目前的陳述式為止。</span><span class="sxs-lookup"><span data-stu-id="39312-126">If one session is currently executing a statement at the server or has results pending from the server, no other sessions sharing the same bound connection can gain access to the server until the current session has finished executing the current statement.</span></span> <span data-ttu-id="39312-127">如果有工作階段嘗試在伺服器忙線時存取連接，就會將錯誤傳回到發生衝突的工作階段，表示連接正在使用中，而且工作階段應該在稍後重試。</span><span class="sxs-lookup"><span data-stu-id="39312-127">If a session attempts to gain access to the connection while the server is busy, an error is returned to the conflicting session indicating the connection is in use and the session should retry later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="39312-128">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="39312-128">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="39312-129">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="39312-129">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39312-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39312-130">See Also</span></span>  
 <span data-ttu-id="39312-131">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="39312-131">[sp_bindsession &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindsession-transact-sql) </span></span>  
 [<span data-ttu-id="39312-132">sp_getbindtoken &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="39312-132">sp_getbindtoken &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql)  
  
  
