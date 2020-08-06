---
title: srv_setcollen (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcollen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e3023e2ac239e074656329da7d8af3aba3afa88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698215"
---
# <a name="srv_setcollen-extended-stored-procedure-api"></a><span data-ttu-id="cfdfa-102">srv_setcollen (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="cfdfa-102">srv_setcollen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="cfdfa-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="cfdfa-104">以位元組為單位，指定可變長度資料行或允許 NULL 值之資料行目前的資料長度。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-104">Specifies the current data length in bytes of a variable-length column or a column that allows NULL values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfdfa-105">語法</span><span class="sxs-lookup"><span data-stu-id="cfdfa-105">Syntax</span></span>  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cfdfa-106">引數</span><span class="sxs-lookup"><span data-stu-id="cfdfa-106">Arguments</span></span>  
 <span data-ttu-id="cfdfa-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="cfdfa-107">*srvproc*</span></span>  
 <span data-ttu-id="cfdfa-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="cfdfa-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="cfdfa-110">*column*</span><span class="sxs-lookup"><span data-stu-id="cfdfa-110">*column*</span></span>  
 <span data-ttu-id="cfdfa-111">這表示要指定其資料長度的資料行編號。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-111">Indicates the number of the column for which the data length is being specified.</span></span> <span data-ttu-id="cfdfa-112">資料行的編號會從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="cfdfa-113">*len*</span><span class="sxs-lookup"><span data-stu-id="cfdfa-113">*len*</span></span>  
 <span data-ttu-id="cfdfa-114">這表示資料行資料的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-114">Indicates the length, in bytes, of the column data.</span></span> <span data-ttu-id="cfdfa-115">0 的長度代表資料行資料值為 Null。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-115">A length of 0 means the column data value is null.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="cfdfa-116">傳回</span><span class="sxs-lookup"><span data-stu-id="cfdfa-116">Returns</span></span>  
 <span data-ttu-id="cfdfa-117">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfdfa-118">備註</span><span class="sxs-lookup"><span data-stu-id="cfdfa-118">Remarks</span></span>  
 <span data-ttu-id="cfdfa-119">資料列的每個資料行必須先用 **srv_describe** 定義。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-119">Each column of the row must first be defined with **srv_describe**.</span></span> <span data-ttu-id="cfdfa-120">資料行的資料長度是由對 **srv_describe** 或 **srv_setcollen** 的最後呼叫所設定。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-120">The column data length is set by the last call to **srv_describe** or **srv_setcollen**.</span></span> <span data-ttu-id="cfdfa-121">如果資料列的可變長度資料 (以 Null 結束的資料) 變更，則必須先使用 **srv_setcollen** 來將它設定為新長度，再呼叫 **srv_sendrow**。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-121">If variable-length data (null-terminated data) changes for a row, **srv_setcollen** must be used to set it to the new length before calling **srv_sendrow**.</span></span> <span data-ttu-id="cfdfa-122">如果是允許 Null 值的資料行，則必須以 *desttype* 設定為允許 Null 的資料類型 (例如 SRVINTN) 來呼叫 **srv_describe**，而且以設定為 0 的 *len* 呼叫 **srv_setcollen** 來指定 Null 資料。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-122">For a column that allows null values, **srv_describe** must have been called with *desttype* set to a data type that allows nulls (like SRVINTN) and null data is specified by calling **srv_setcollen** with *len* set to 0.</span></span> <span data-ttu-id="cfdfa-123">零長度的資料不能使用擴充預存程序 API 指定。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-123">Zero length data cannot be specified using the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="cfdfa-124">請注意，當資料行的資料類型是可變長度時，就不會檢查 *len*。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-124">Note that when the data type of the column is variable-length, *len* is not checked.</span></span> <span data-ttu-id="cfdfa-125">如果針對固定長度資料行呼叫此函數，此函數會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-125">This function returns FAIL if called for a fixed-length column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cfdfa-126">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="cfdfa-127">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="cfdfa-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdfa-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfdfa-128">See Also</span></span>  
 [<span data-ttu-id="cfdfa-129">srv_describe &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="cfdfa-129">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
