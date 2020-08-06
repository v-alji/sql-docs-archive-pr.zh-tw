---
title: srv_sendrow (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendrow
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: df40348b8792a70f84719abfb42152fda9487e6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710593"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a><span data-ttu-id="2ed62-102">srv_sendrow (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="2ed62-102">srv_sendrow (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="2ed62-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="2ed62-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="2ed62-104">將資料的資料列傳送到用戶端。</span><span class="sxs-lookup"><span data-stu-id="2ed62-104">Transmits a row of data to the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed62-105">語法</span><span class="sxs-lookup"><span data-stu-id="2ed62-105">Syntax</span></span>  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ed62-106">引數</span><span class="sxs-lookup"><span data-stu-id="2ed62-106">Arguments</span></span>  
 <span data-ttu-id="2ed62-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="2ed62-107">*srvproc*</span></span>  
 <span data-ttu-id="2ed62-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (此案例中為接收語言要求的控制代碼)。</span><span class="sxs-lookup"><span data-stu-id="2ed62-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the language request).</span></span> <span data-ttu-id="2ed62-109">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="2ed62-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="2ed62-110">傳回</span><span class="sxs-lookup"><span data-stu-id="2ed62-110">Returns</span></span>  
 <span data-ttu-id="2ed62-111">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="2ed62-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ed62-112">備註</span><span class="sxs-lookup"><span data-stu-id="2ed62-112">Remarks</span></span>  
 <span data-ttu-id="2ed62-113">系統會針對傳送到用戶端的每個資料列，呼叫 **srv_sendrow** 函式一次。</span><span class="sxs-lookup"><span data-stu-id="2ed62-113">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="2ed62-114">所有資料列都必須在使用 **srv_sendmsg**、**srv_status** 或 **srv_senddone** 傳送任何訊息、狀態值或完成狀態之前，傳送到用戶端。</span><span class="sxs-lookup"><span data-stu-id="2ed62-114">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, **srv_status**, or **srv_senddone**.</span></span>  
  
 <span data-ttu-id="2ed62-115">傳送已經使用 **srv_describe** 定義其所有資料行的資料列時，會使擴充預存程序 API 應用程式引發參考用錯誤訊息，並將 FAIL 傳回到用戶端。</span><span class="sxs-lookup"><span data-stu-id="2ed62-115">Sending a row that has not had all its columns defined with **srv_describe** causes the Extended Stored Procedure API application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="2ed62-116">在此情況下，不會傳送資料列。</span><span class="sxs-lookup"><span data-stu-id="2ed62-116">In this case, the row is not sent.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2ed62-117">擴充預存程序 API 不支援將計算資料列傳送到用戶端。</span><span class="sxs-lookup"><span data-stu-id="2ed62-117">The Extended Stored Procedure API does not support sending compute rows to the client.</span></span> <span data-ttu-id="2ed62-118">同時，如果將包含 `ntext`、`text` 或 `image` 資料的資料列傳送到用戶端，則不會包括文字指標與文字時間戳記。</span><span class="sxs-lookup"><span data-stu-id="2ed62-118">Also, if a row containing `ntext`, `text`, or `image` data is sent to the client, the text pointer and text timestamp are not included.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2ed62-119">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="2ed62-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="2ed62-120">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="2ed62-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed62-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ed62-121">See Also</span></span>  
 [<span data-ttu-id="2ed62-122">srv_describe &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="2ed62-122">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
