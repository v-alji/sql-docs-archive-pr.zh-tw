---
title: srv_paramsetoutput (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramsetoutput
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
author: rothja
ms.author: jroth
ms.openlocfilehash: 2847367fe5d6052728cebf30467b68cb14fb8e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592016"
---
# <a name="srv_paramsetoutput-extended-stored-procedure-api"></a><span data-ttu-id="da655-102">srv_paramsetoutput (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="da655-102">srv_paramsetoutput (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="da655-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="da655-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="da655-104">設定傳回參數的值。</span><span class="sxs-lookup"><span data-stu-id="da655-104">Sets the value of a return parameter.</span></span> <span data-ttu-id="da655-105">這個函式會取代 **srv_paramset** 函式。</span><span class="sxs-lookup"><span data-stu-id="da655-105">This function supersedes the **srv_paramset** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da655-106">語法</span><span class="sxs-lookup"><span data-stu-id="da655-106">Syntax</span></span>  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="da655-107">引數</span><span class="sxs-lookup"><span data-stu-id="da655-107">Arguments</span></span>  
 <span data-ttu-id="da655-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="da655-108">*srvproc*</span></span>  
 <span data-ttu-id="da655-109">這是用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="da655-109">Is a handle for a client connection.</span></span>  
  
 <span data-ttu-id="da655-110">*n*</span><span class="sxs-lookup"><span data-stu-id="da655-110">*n*</span></span>  
 <span data-ttu-id="da655-111">這是要設定之參數的序數。</span><span class="sxs-lookup"><span data-stu-id="da655-111">Is the ordinal number of the parameter to be set.</span></span> <span data-ttu-id="da655-112">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="da655-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="da655-113">*pbData*</span><span class="sxs-lookup"><span data-stu-id="da655-113">*pbData*</span></span>  
 <span data-ttu-id="da655-114">這是指向要當做程序傳回參數傳回給用戶端之資料值的指標。</span><span class="sxs-lookup"><span data-stu-id="da655-114">Is a pointer to the data value to be sent back to the client as a procedure return parameter.</span></span>  
  
 <span data-ttu-id="da655-115">*cbLen*</span><span class="sxs-lookup"><span data-stu-id="da655-115">*cbLen*</span></span>  
 <span data-ttu-id="da655-116">這是要傳回之資料的實際長度。</span><span class="sxs-lookup"><span data-stu-id="da655-116">Is the actual length of the data to be returned.</span></span> <span data-ttu-id="da655-117">如果參數的資料類型會指定固定長度的值，而且不允許 null 值 (例如 *srvbit* 或 *srvint1*)，則會忽略 *cbLen*。</span><span class="sxs-lookup"><span data-stu-id="da655-117">If the data type of the parameter specifies values of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *cbLen* is ignored.</span></span> <span data-ttu-id="da655-118">如果 *fNull* 為 FALSE，0 的值代表長度為零的資料。</span><span class="sxs-lookup"><span data-stu-id="da655-118">A value of 0 signifies zero-length data if *fNull* is FALSE.</span></span>  
  
 <span data-ttu-id="da655-119">*fNull*</span><span class="sxs-lookup"><span data-stu-id="da655-119">*fNull*</span></span>  
 <span data-ttu-id="da655-120">這是一個旗標，可指出傳回參數的值是否為 NULL。</span><span class="sxs-lookup"><span data-stu-id="da655-120">Is a flag indicating whether the value of the return parameter is NULL.</span></span> <span data-ttu-id="da655-121">如果此參數應該設定為 NULL，請將此旗標設定為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="da655-121">Set this flag to TRUE if the parameter should be set to NULL.</span></span> <span data-ttu-id="da655-122">預設值為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="da655-122">The default value is FALSE.</span></span> <span data-ttu-id="da655-123">如果 *fNull* 設定為 TRUE，*cbLen* 應該設定為 0，否則此函式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="da655-123">If *fNull* is set to TRUE, *cbLen* should be set to 0 or the function will fail.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="da655-124">傳回</span><span class="sxs-lookup"><span data-stu-id="da655-124">Returns</span></span>  
 <span data-ttu-id="da655-125">如果成功設定參數資訊，則會傳回 SUCCEED，否則會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="da655-125">If the parameter information was successfully set, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="da655-126">在以下情況下會傳回 FAIL</span><span class="sxs-lookup"><span data-stu-id="da655-126">FAIL is returned when</span></span>  
  
-   <span data-ttu-id="da655-127">此參數不是傳回參數，或是</span><span class="sxs-lookup"><span data-stu-id="da655-127">the parameter is not a return parameter, or</span></span>  
  
-   <span data-ttu-id="da655-128">*cbLen* 引數無效。</span><span class="sxs-lookup"><span data-stu-id="da655-128">the *cbLen* argument is invalid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da655-129">備註</span><span class="sxs-lookup"><span data-stu-id="da655-129">Remarks</span></span>  
 <span data-ttu-id="da655-130">**安全性注意事項**：您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="da655-130">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="da655-131">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="da655-131">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
