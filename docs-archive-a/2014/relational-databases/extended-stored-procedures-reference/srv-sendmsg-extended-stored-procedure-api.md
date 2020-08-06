---
title: srv_sendmsg (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendmsg
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
author: rothja
ms.author: jroth
ms.openlocfilehash: 0821ad88f48313cfadea634a489def9b242a49f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710594"
---
# <a name="srv_sendmsg-extended-stored-procedure-api"></a><span data-ttu-id="d9459-102">srv_sendmsg (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="d9459-102">srv_sendmsg (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="d9459-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="d9459-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="d9459-104">傳送訊息給用戶端。</span><span class="sxs-lookup"><span data-stu-id="d9459-104">Sends a message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9459-105">語法</span><span class="sxs-lookup"><span data-stu-id="d9459-105">Syntax</span></span>  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="d9459-106">引數</span><span class="sxs-lookup"><span data-stu-id="d9459-106">Arguments</span></span>  
 <span data-ttu-id="d9459-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="d9459-107">*srvproc*</span></span>  
 <span data-ttu-id="d9459-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (此案例中為接收語言要求的控制代碼)。</span><span class="sxs-lookup"><span data-stu-id="d9459-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="d9459-109">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="d9459-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="d9459-110">*msgtype*</span><span class="sxs-lookup"><span data-stu-id="d9459-110">*msgtype*</span></span>  
 <span data-ttu-id="d9459-111">這是 SRV_MSG_INFO 或 SRV_MSG_ERROR (取決於伺服器要傳送參考用訊息還是錯誤訊息而定)。</span><span class="sxs-lookup"><span data-stu-id="d9459-111">Is either SRV_MSG_INFO or SRV_MSG_ERROR, depending on whether the server is sending an informational or error message.</span></span>  
  
 <span data-ttu-id="d9459-112">*msgnum*</span><span class="sxs-lookup"><span data-stu-id="d9459-112">*msgnum*</span></span>  
 <span data-ttu-id="d9459-113">這是 4 位元組的訊息編號。</span><span class="sxs-lookup"><span data-stu-id="d9459-113">Is a 4-byte message number.</span></span>  
  
 <span data-ttu-id="d9459-114">*class*</span><span class="sxs-lookup"><span data-stu-id="d9459-114">*class*</span></span>  
 <span data-ttu-id="d9459-115">指定錯誤嚴重性。</span><span class="sxs-lookup"><span data-stu-id="d9459-115">Specifies the error severity.</span></span> <span data-ttu-id="d9459-116">嚴重性小於或等於 10 視為參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="d9459-116">A severity less than or equal to 10 is considered an informational message.</span></span>  
  
 <span data-ttu-id="d9459-117">*state*</span><span class="sxs-lookup"><span data-stu-id="d9459-117">*state*</span></span>  
 <span data-ttu-id="d9459-118">提供目前訊息的錯誤狀態編號。</span><span class="sxs-lookup"><span data-stu-id="d9459-118">Provides the error state number for the current message.</span></span> <span data-ttu-id="d9459-119">錯誤狀態編號會提供有關錯誤內容的資訊。</span><span class="sxs-lookup"><span data-stu-id="d9459-119">The error state number provides information about the context of the error.</span></span> <span data-ttu-id="d9459-120">有效的狀態編號是從 0 到 255。</span><span class="sxs-lookup"><span data-stu-id="d9459-120">Valid state numbers are from 0 through 255.</span></span>  
  
 <span data-ttu-id="d9459-121">*rpcname*</span><span class="sxs-lookup"><span data-stu-id="d9459-121">*rpcname*</span></span>  
 <span data-ttu-id="d9459-122">目前不支援。</span><span class="sxs-lookup"><span data-stu-id="d9459-122">Is currently not supported.</span></span>  
  
 <span data-ttu-id="d9459-123">*rpcnamelen*</span><span class="sxs-lookup"><span data-stu-id="d9459-123">*rpcnamelen*</span></span>  
 <span data-ttu-id="d9459-124">目前不支援。</span><span class="sxs-lookup"><span data-stu-id="d9459-124">Is currently not supported.</span></span>  
  
 <span data-ttu-id="d9459-125">*linenum*</span><span class="sxs-lookup"><span data-stu-id="d9459-125">*linenum*</span></span>  
 <span data-ttu-id="d9459-126">這是此訊息在語言命令批次中所適用的行號。</span><span class="sxs-lookup"><span data-stu-id="d9459-126">Is the line number in the language command batch where the message applies.</span></span> <span data-ttu-id="d9459-127">行號從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="d9459-127">Line numbers start at 1.</span></span> <span data-ttu-id="d9459-128">如果 *linenum* 不會套用到訊息，請將它設定為 0。</span><span class="sxs-lookup"><span data-stu-id="d9459-128">If *linenum* does not apply to the message, set to 0.</span></span>  
  
 <span data-ttu-id="d9459-129">*message*</span><span class="sxs-lookup"><span data-stu-id="d9459-129">*message*</span></span>  
 <span data-ttu-id="d9459-130">這是要傳送給用戶端之字元字串的指標。</span><span class="sxs-lookup"><span data-stu-id="d9459-130">Is a pointer to the character string to be sent to the client.</span></span>  
  
 <span data-ttu-id="d9459-131">*msglen*</span><span class="sxs-lookup"><span data-stu-id="d9459-131">*msglen*</span></span>  
 <span data-ttu-id="d9459-132">指定 *message* 的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="d9459-132">Specifies the length, in bytes, of *message*.</span></span> <span data-ttu-id="d9459-133">如果 *message* 是以 null 結尾，請將 *msglen* 設定為 SRV_NULLTERM。</span><span class="sxs-lookup"><span data-stu-id="d9459-133">If *message* is null-terminated, set *msglen* to SRV_NULLTERM.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d9459-134">傳回</span><span class="sxs-lookup"><span data-stu-id="d9459-134">Returns</span></span>  
 <span data-ttu-id="d9459-135">SUCCEED 或 FAIL</span><span class="sxs-lookup"><span data-stu-id="d9459-135">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9459-136">備註</span><span class="sxs-lookup"><span data-stu-id="d9459-136">Remarks</span></span>  
 <span data-ttu-id="d9459-137">這個函數會將錯誤或參考用訊息傳送給用戶端。</span><span class="sxs-lookup"><span data-stu-id="d9459-137">This function sends error or informational messages to the client.</span></span> <span data-ttu-id="d9459-138">將會針對每一個要傳送的訊息呼叫此函數一次。</span><span class="sxs-lookup"><span data-stu-id="d9459-138">It is called once for each message to be sent.</span></span>  
  
 <span data-ttu-id="d9459-139">在使用 **srv_sendrow** 傳送所有資料列 (如果有的話) 之前或之後，都可以依照任何順序使用 **srv_sendmsg** 將訊息傳送給用戶端。</span><span class="sxs-lookup"><span data-stu-id="d9459-139">Messages can be sent to the client with **srv_sendmsg** in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="d9459-140">必須在使用 **srv_senddone** 傳送完成狀態以前將所有訊息 (如果有的話) 傳送給用戶端。</span><span class="sxs-lookup"><span data-stu-id="d9459-140">All messages, if any, must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
 <span data-ttu-id="d9459-141">若要以 Unicode 傳送訊息，請使用 **srv_wsendmsg**，而不是 **srv_sendmsg**。</span><span class="sxs-lookup"><span data-stu-id="d9459-141">To send messages in Unicode, use **srv_wsendmsg** rather than **srv_sendmsg**.</span></span>  
  
 <span data-ttu-id="d9459-142">如需詳細資訊，請參閱 [Unicode 資料和伺服器字碼頁](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="d9459-142">For more information see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d9459-143">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="d9459-143">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="d9459-144">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="d9459-144">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
