---
title: srv_pfieldex (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: a474eafcb6b6d42161a7e67ce7f93636269c46c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593393"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a><span data-ttu-id="c9783-102">srv_pfieldex (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="c9783-102">srv_pfieldex (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="c9783-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="c9783-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="c9783-104">傳回含有要求之 SRV_PROC 欄位的資料的指標。</span><span class="sxs-lookup"><span data-stu-id="c9783-104">Returns a pointer to data containing the requested SRV_PROC field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9783-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9783-105">Syntax</span></span>  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9783-106">引數</span><span class="sxs-lookup"><span data-stu-id="c9783-106">Arguments</span></span>  
 <span data-ttu-id="c9783-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="c9783-107">*srvproc*</span></span>  
 <span data-ttu-id="c9783-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c9783-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="c9783-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="c9783-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="c9783-110">*欄位*</span><span class="sxs-lookup"><span data-stu-id="c9783-110">*field*</span></span>  
 <span data-ttu-id="c9783-111">指定要傳回的 *srvproc* 欄位。</span><span class="sxs-lookup"><span data-stu-id="c9783-111">Specifies the *srvproc* field to return.</span></span>  
  
|<span data-ttu-id="c9783-112">欄位</span><span class="sxs-lookup"><span data-stu-id="c9783-112">Field</span></span>|<span data-ttu-id="c9783-113">描述</span><span class="sxs-lookup"><span data-stu-id="c9783-113">Description</span></span>|<span data-ttu-id="c9783-114">傳回類型</span><span class="sxs-lookup"><span data-stu-id="c9783-114">Return-type</span></span>|  
|-----------|-----------------|------------------|  
|<span data-ttu-id="c9783-115">SRV_MSGLCID</span><span class="sxs-lookup"><span data-stu-id="c9783-115">SRV_MSGLCID</span></span>|<span data-ttu-id="c9783-116">目前的工作階段訊息 LCID。</span><span class="sxs-lookup"><span data-stu-id="c9783-116">Current session message LCID.</span></span>|<span data-ttu-id="c9783-117">ULONG\*</span><span class="sxs-lookup"><span data-stu-id="c9783-117">ULONG\*</span></span>|  
|<span data-ttu-id="c9783-118">SRV_INSTANCENAME</span><span class="sxs-lookup"><span data-stu-id="c9783-118">SRV_INSTANCENAME</span></span>|<span data-ttu-id="c9783-119">執行個體名稱 (如果是具名的)；否則，傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="c9783-119">Instance name (if named); otherwise, returns NULL.</span></span>|<span data-ttu-id="c9783-120">WCHAR\*</span><span class="sxs-lookup"><span data-stu-id="c9783-120">WCHAR\*</span></span>|  
  
 <span data-ttu-id="c9783-121">*len*</span><span class="sxs-lookup"><span data-stu-id="c9783-121">*len*</span></span>  
 <span data-ttu-id="c9783-122">這是指向 **int** 變數的指標，該變數含有傳回 *field* 值的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="c9783-122">Is a pointer to an **int** variable that contains the length of the returned *field* value in bytes.</span></span> <span data-ttu-id="c9783-123">如果 *len* 為 NULL，則不會傳回長度。</span><span class="sxs-lookup"><span data-stu-id="c9783-123">If *len* is NULL, the length is not returned.</span></span> <span data-ttu-id="c9783-124">當傳回 NULL 時，\**len* 會設定為 0。</span><span class="sxs-lookup"><span data-stu-id="c9783-124">When NULL is returned \**len* is set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="c9783-125">傳回</span><span class="sxs-lookup"><span data-stu-id="c9783-125">Returns</span></span>  
 <span data-ttu-id="c9783-126">指向資料的指標，其資料類型取決於 *field*。</span><span class="sxs-lookup"><span data-stu-id="c9783-126">A pointer to data whose type depends on *field*.</span></span> <span data-ttu-id="c9783-127">當 *len* 為 NULL 或 *srvproc* 為 NULL 時，會傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="c9783-127">NULL is returned when *len* is NULL or *srvproc* is NULL.</span></span> <span data-ttu-id="c9783-128">如果 *field* 為未知，則傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="c9783-128">If the *field* is unknown, NULL is returned.</span></span> <span data-ttu-id="c9783-129">當傳回 NULL 時，\**len* 會設定為 0。</span><span class="sxs-lookup"><span data-stu-id="c9783-129">When NULL is returned \**len* is set to 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c9783-130">從伺服器傳回的緩衝區應該是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c9783-130">The buffer returned from the server should be read only.</span></span> <span data-ttu-id="c9783-131">否則，伺服器狀態可能會損毀。</span><span class="sxs-lookup"><span data-stu-id="c9783-131">Otherwise, the server state may be corrupted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9783-132">備註</span><span class="sxs-lookup"><span data-stu-id="c9783-132">Remarks</span></span>  
 <span data-ttu-id="c9783-133">**安全性注意事項**：您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="c9783-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="c9783-134">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="c9783-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
