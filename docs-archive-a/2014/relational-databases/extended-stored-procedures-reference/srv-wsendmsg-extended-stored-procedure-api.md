---
title: srv_wsendmsg (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_wsendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
ms.openlocfilehash: 4cc915cce0befccb5c5af58e703c11b750af855b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709466"
---
# <a name="srv_wsendmsg-extended-stored-procedure-api"></a><span data-ttu-id="5590d-102">srv_wsendmsg (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="5590d-102">srv_wsendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="5590d-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="5590d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="5590d-104">將 Unicode 訊息傳送給用戶端。</span><span class="sxs-lookup"><span data-stu-id="5590d-104">Sends a Unicode message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5590d-105">語法</span><span class="sxs-lookup"><span data-stu-id="5590d-105">Syntax</span></span>  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="5590d-106">引數</span><span class="sxs-lookup"><span data-stu-id="5590d-106">Arguments</span></span>  
 <span data-ttu-id="5590d-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="5590d-107">*srvproc*</span></span>  
 <span data-ttu-id="5590d-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5590d-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="5590d-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="5590d-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="5590d-110">*M*</span><span class="sxs-lookup"><span data-stu-id="5590d-110">*Msgnum*</span></span>  
 <span data-ttu-id="5590d-111">這是 4 位元組的訊息編號。</span><span class="sxs-lookup"><span data-stu-id="5590d-111">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="5590d-112">*嚴重性*</span><span class="sxs-lookup"><span data-stu-id="5590d-112">*Severity*</span></span>  
 <span data-ttu-id="5590d-113">指定錯誤的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="5590d-113">Specifies the severity of the error.</span></span> <span data-ttu-id="5590d-114">嚴重性小於或等於 10 視為參考用訊息，否則就是錯誤。</span><span class="sxs-lookup"><span data-stu-id="5590d-114">A severity less than or equal to 10 is considered an informational message; otherwise, it is an error.</span></span>  
  
 <span data-ttu-id="5590d-115">*message*</span><span class="sxs-lookup"><span data-stu-id="5590d-115">*message*</span></span>  
 <span data-ttu-id="5590d-116">這是要傳送給用戶端之 Unicode 字串的指標。</span><span class="sxs-lookup"><span data-stu-id="5590d-116">Is a pointer to a Unicode string to be sent to the client.</span></span>  
  
 <span data-ttu-id="5590d-117">*msglen*</span><span class="sxs-lookup"><span data-stu-id="5590d-117">*msglen*</span></span>  
 <span data-ttu-id="5590d-118">指定 *message* 的長度 (以字元為單位)。</span><span class="sxs-lookup"><span data-stu-id="5590d-118">Specifies the length, in characters, of *message*.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="5590d-119">傳回</span><span class="sxs-lookup"><span data-stu-id="5590d-119">Returns</span></span>  
 <span data-ttu-id="5590d-120">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="5590d-120">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5590d-121">備註</span><span class="sxs-lookup"><span data-stu-id="5590d-121">Remarks</span></span>  
 <span data-ttu-id="5590d-122">使用這個函數來以 Unicode 傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="5590d-122">Use this function to send messages in Unicode.</span></span> <span data-ttu-id="5590d-123">這類似於 **srv_sendmsg**，但是它所傳送的訊息是 WCHAR 字串，而不是 DBCHAR 類型的字串。</span><span class="sxs-lookup"><span data-stu-id="5590d-123">It is similar to **srv_sendmsg**, but the message it sends is a WCHAR string rather than type DBCHAR string.</span></span> <span data-ttu-id="5590d-124">請注意，訊息長度是以字元報告，而不是以位元組報告，而且 *msglen* 絕對不會等於 SRV_NULLTERM。</span><span class="sxs-lookup"><span data-stu-id="5590d-124">Note that message length is reported in characters rather than bytes, and *msglen* will never be equal to SRV_NULLTERM.</span></span>  
  
 <span data-ttu-id="5590d-125">此函數在下列情況下會傳回 FAIL</span><span class="sxs-lookup"><span data-stu-id="5590d-125">The function returns FAIL when</span></span>  
  
-   <span data-ttu-id="5590d-126">指定的 *msglen* 不在 0-32242 範圍內。</span><span class="sxs-lookup"><span data-stu-id="5590d-126">The *msglen* given is not in the range of 0-32242.</span></span>  
  
-   <span data-ttu-id="5590d-127">指定的 *msglen* 為 0，但是訊息指標為 NULL。</span><span class="sxs-lookup"><span data-stu-id="5590d-127">The *msglen* given is 0 but the message pointer is NULL.</span></span>  
  
-   <span data-ttu-id="5590d-128">當透過網路傳送錯誤訊息時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5590d-128">There is error when sending the error message through network.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5590d-129">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="5590d-129">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="5590d-130">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="5590d-130">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5590d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5590d-131">See Also</span></span>  
 [<span data-ttu-id="5590d-132">srv_sendmsg &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="5590d-132">srv_sendmsg &#40;Extended Stored Procedure API&#41;</span></span>](srv-sendmsg-extended-stored-procedure-api.md)  
  
  
