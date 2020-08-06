---
title: srv_senddone (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_senddone
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
author: rothja
ms.author: jroth
ms.openlocfilehash: 877acdc1b666c7f4cbaab737590a1c55e474eb05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710598"
---
# <a name="srv_senddone-extended-stored-procedure-api"></a><span data-ttu-id="f6575-102">srv_senddone (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="f6575-102">srv_senddone (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="f6575-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="f6575-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="f6575-104">將結果完成訊息傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="f6575-104">Sends a result completion message to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6575-105">語法</span><span class="sxs-lookup"><span data-stu-id="f6575-105">Syntax</span></span>  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6575-106">引數</span><span class="sxs-lookup"><span data-stu-id="f6575-106">Arguments</span></span>  
 <span data-ttu-id="f6575-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="f6575-107">*srvproc*</span></span>  
 <span data-ttu-id="f6575-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (此案例中為接收語言要求的控制代碼)。</span><span class="sxs-lookup"><span data-stu-id="f6575-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="f6575-109">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="f6575-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="f6575-110">*status*</span><span class="sxs-lookup"><span data-stu-id="f6575-110">*status*</span></span>  
 <span data-ttu-id="f6575-111">這是各種 *status* 旗標的 2 位元組欄位。</span><span class="sxs-lookup"><span data-stu-id="f6575-111">Is a 2-byte field for various *status* flags.</span></span> <span data-ttu-id="f6575-112">可以搭配 *status* 旗標值使用 AND 和 OR 邏輯運算子來設定多個旗標。</span><span class="sxs-lookup"><span data-stu-id="f6575-112">Multiple flags can be set by using the AND and OR logical operators with *status* flag values.</span></span> <span data-ttu-id="f6575-113">下表列出可能的 *status* 旗標。</span><span class="sxs-lookup"><span data-stu-id="f6575-113">The following table lists possible *status* flags.</span></span>  
  
|<span data-ttu-id="f6575-114">狀態旗標</span><span class="sxs-lookup"><span data-stu-id="f6575-114">Status flag</span></span>|<span data-ttu-id="f6575-115">描述</span><span class="sxs-lookup"><span data-stu-id="f6575-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f6575-116">SRV_DONE_COUNT</span><span class="sxs-lookup"><span data-stu-id="f6575-116">SRV_DONE_COUNT</span></span>|<span data-ttu-id="f6575-117">*count* 參數包含有效的計數。</span><span class="sxs-lookup"><span data-stu-id="f6575-117">The *count* parameter contains a valid count.</span></span>|  
|<span data-ttu-id="f6575-118">SRV_DONE_ERROR</span><span class="sxs-lookup"><span data-stu-id="f6575-118">SRV_DONE_ERROR</span></span>|<span data-ttu-id="f6575-119">目前的用戶端命令收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6575-119">The current client command received an error.</span></span>|  
  
 <span data-ttu-id="f6575-120">*info*</span><span class="sxs-lookup"><span data-stu-id="f6575-120">*info*</span></span>  
 <span data-ttu-id="f6575-121">這是保留的 2 位元組欄位。</span><span class="sxs-lookup"><span data-stu-id="f6575-121">Is a reserved, 2-byte field.</span></span> <span data-ttu-id="f6575-122">將這個值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="f6575-122">Set this value to 0.</span></span>  
  
 <span data-ttu-id="f6575-123">*計數*</span><span class="sxs-lookup"><span data-stu-id="f6575-123">*count*</span></span>  
 <span data-ttu-id="f6575-124">這是用來指示目前結果集計數的 4 位元組欄位。</span><span class="sxs-lookup"><span data-stu-id="f6575-124">Is a 4-byte field used to indicate a count for the current result set.</span></span> <span data-ttu-id="f6575-125">如果在 *status* 欄位中設定 SRV_DONE_COUNT 旗標，*count* 會保留有效的計數。</span><span class="sxs-lookup"><span data-stu-id="f6575-125">If the SRV_DONE_COUNT flag is set in the *status* field, *count* holds a valid count.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f6575-126">傳回</span><span class="sxs-lookup"><span data-stu-id="f6575-126">Returns</span></span>  
 <span data-ttu-id="f6575-127">SUCCEED 或 FAIL</span><span class="sxs-lookup"><span data-stu-id="f6575-127">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6575-128">備註</span><span class="sxs-lookup"><span data-stu-id="f6575-128">Remarks</span></span>  
 <span data-ttu-id="f6575-129">用戶端要求會造成伺服器執行一些命令，並傳回一些結果集。</span><span class="sxs-lookup"><span data-stu-id="f6575-129">A client request can cause the server to execute a number of commands and to return a number of result sets.</span></span> <span data-ttu-id="f6575-130">**srv_senddone** 必須針對每一個結果集傳回結果完成訊息給用戶端。</span><span class="sxs-lookup"><span data-stu-id="f6575-130">For each result set, **srv_senddone** must return a result completion message to the client.</span></span>  
  
 <span data-ttu-id="f6575-131">*count* 欄位指出受到命令影響的資料列數。</span><span class="sxs-lookup"><span data-stu-id="f6575-131">The *count* field indicates the number of rows affected by a command.</span></span> <span data-ttu-id="f6575-132">如果 *count* 欄位包含計數，就應該在 *status* 欄位中設定 SRV_DONE_COUNT 旗標。</span><span class="sxs-lookup"><span data-stu-id="f6575-132">If the *count* field contains a count, the SRV_DONE_COUNT flag should be set in the *status* field.</span></span> <span data-ttu-id="f6575-133">此設定可讓用戶端區分 0 的 *count* 值及未使用的 *count* 欄位。</span><span class="sxs-lookup"><span data-stu-id="f6575-133">This setting allows the client to distinguish between a *count* value of 0 and an unused *count* field.</span></span>  
  
 <span data-ttu-id="f6575-134">請勿從 SRV_CONNECT 處理常式呼叫 **srv_senddone**。</span><span class="sxs-lookup"><span data-stu-id="f6575-134">Do not call **srv_senddone** from the SRV_CONNECT handler.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f6575-135">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="f6575-135">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="f6575-136">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="f6575-136">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
