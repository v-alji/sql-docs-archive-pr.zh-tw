---
title: srv_paraminfo (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paraminfo
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
ms.openlocfilehash: cc3d51acc2ca560246c46267840db72934223999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709498"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a><span data-ttu-id="a4552-102">srv_paraminfo (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="a4552-102">srv_paraminfo (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="a4552-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="a4552-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="a4552-104">傳回有關參數的資訊。</span><span class="sxs-lookup"><span data-stu-id="a4552-104">Returns information about a parameter.</span></span> <span data-ttu-id="a4552-105">這個函式會取代以下函式：[srv_paramtype](srv-paramtype-extended-stored-procedure-api.md)、[srv_paramlen](srv-paramlen-extended-stored-procedure-api.md)、[srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md) 和 [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="a4552-105">This function supersedes the following functions: [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md), and [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="a4552-106">**srv_paraminfo** 支援[資料類型](data-types-extended-stored-procedure-api.md)中的資料類型和零長度的資料。</span><span class="sxs-lookup"><span data-stu-id="a4552-106">**srv_paraminfo** supports the data types in [Data Types](data-types-extended-stored-procedure-api.md) and zero-length data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4552-107">語法</span><span class="sxs-lookup"><span data-stu-id="a4552-107">Syntax</span></span>  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4552-108">引數</span><span class="sxs-lookup"><span data-stu-id="a4552-108">Arguments</span></span>  
 <span data-ttu-id="a4552-109">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="a4552-109">*srvproc*</span></span>  
 <span data-ttu-id="a4552-110">用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a4552-110">A handle for a client connection.</span></span>  
  
 <span data-ttu-id="a4552-111">*n*</span><span class="sxs-lookup"><span data-stu-id="a4552-111">*n*</span></span>  
 <span data-ttu-id="a4552-112">要設定之參數的序數。</span><span class="sxs-lookup"><span data-stu-id="a4552-112">The ordinal number of the parameter to be set.</span></span> <span data-ttu-id="a4552-113">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="a4552-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="a4552-114">*pbType*</span><span class="sxs-lookup"><span data-stu-id="a4552-114">*pbType*</span></span>  
 <span data-ttu-id="a4552-115">參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a4552-115">The data type of the parameter.</span></span>  
  
 <span data-ttu-id="a4552-116">*pcbMaxLen*</span><span class="sxs-lookup"><span data-stu-id="a4552-116">*pcbMaxLen*</span></span>  
 <span data-ttu-id="a4552-117">參數之最大長度的指標。</span><span class="sxs-lookup"><span data-stu-id="a4552-117">Pointer to the maximum length of the parameter.</span></span>  
  
 <span data-ttu-id="a4552-118">*pcbActualLen*</span><span class="sxs-lookup"><span data-stu-id="a4552-118">*pcbActualLen*</span></span>  
 <span data-ttu-id="a4552-119">參數之實際長度的指標。</span><span class="sxs-lookup"><span data-stu-id="a4552-119">Pointer to the actual length of the parameter.</span></span> <span data-ttu-id="a4552-120">0 (\**pcbActualLen* == 0) 的值表示長度為零的資料 (如果 \**pfNull* 設定為 FALSE)。</span><span class="sxs-lookup"><span data-stu-id="a4552-120">A value of 0 (\**pcbActualLen* == 0) signifies zero-length data if \**pfNull* is set to FALSE.</span></span>  
  
 <span data-ttu-id="a4552-121">*pbData*</span><span class="sxs-lookup"><span data-stu-id="a4552-121">*pbData*</span></span>  
 <span data-ttu-id="a4552-122">參數資料之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="a4552-122">Pointer to the buffer for parameter data.</span></span> <span data-ttu-id="a4552-123">如果 *pbData* 不是 NULL，擴充預存程序 API 會將 \**pcbActualLen* 位元組的資料寫入 \**pbData*。</span><span class="sxs-lookup"><span data-stu-id="a4552-123">If *pbData* is not NULL, the Extended Store Procedure API writes \**pcbActualLen* bytes of data to \**pbData*.</span></span> <span data-ttu-id="a4552-124">如果 *pbData* 為 NULL，則不會將任何資料寫入 \**pbData*，但此函式會傳回 \**pbType*、\**pcbMaxLen*、\**pcbActualLen* 和 \**pfNull*。</span><span class="sxs-lookup"><span data-stu-id="a4552-124">If *pbData* is NULL, no data is written to \**pbData* but the function returns \**pbType*, \**pcbMaxLen*, \**pcbActualLen*, and \**pfNull*.</span></span> <span data-ttu-id="a4552-125">此緩衝區的記憶體必須由應用程式管理。</span><span class="sxs-lookup"><span data-stu-id="a4552-125">The memory for this buffer must be managed by the application.</span></span>  
  
 <span data-ttu-id="a4552-126">*pfNull*</span><span class="sxs-lookup"><span data-stu-id="a4552-126">*pfNull*</span></span>  
 <span data-ttu-id="a4552-127">null 旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="a4552-127">Pointer to a null flag.</span></span><span data-ttu-id="a4552-128">如果參數值為 NULL， \**pfNull* 會設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a4552-128">\ **pfNull* is set to TRUE if the value of the parameter is NULL.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a4552-129">傳回</span><span class="sxs-lookup"><span data-stu-id="a4552-129">Returns</span></span>  
 <span data-ttu-id="a4552-130">如果成功取得參數資訊，則會傳回 SUCCEED，否則會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="a4552-130">If the parameter information was successfully obtained, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="a4552-131">目前沒有任何遠端預存程序，且沒有第 *n* 個遠端預存程序參數時，會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="a4552-131">FAIL is returned when there is no current remote stored procedure and when there is no *n*th remote stored procedure parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4552-132">備註</span><span class="sxs-lookup"><span data-stu-id="a4552-132">Remarks</span></span>  
 <span data-ttu-id="a4552-133">**安全性注意事項**：您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a4552-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="a4552-134">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="a4552-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4552-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4552-135">See Also</span></span>  
 [<span data-ttu-id="a4552-136">擴充預存程序程式設計人員參考</span><span class="sxs-lookup"><span data-stu-id="a4552-136">Extended Stored Procedures Programmer's Reference</span></span>](database-engine-extended-stored-procedures-reference.md)  
  
  
