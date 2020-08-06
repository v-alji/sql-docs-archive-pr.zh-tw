---
title: srv_paramtype (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramtype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c4b4006f8214670e3bd2bddfbaabe917fb9d778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593394"
---
# <a name="srv_paramtype-extended-stored-procedure-api"></a><span data-ttu-id="1cde7-102">srv_paramtype (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="1cde7-102">srv_paramtype (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="1cde7-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="1cde7-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="1cde7-104">傳回遠端預存程序呼叫參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1cde7-104">Returns the data type of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cde7-105">語法</span><span class="sxs-lookup"><span data-stu-id="1cde7-105">Syntax</span></span>  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1cde7-106">引數</span><span class="sxs-lookup"><span data-stu-id="1cde7-106">Arguments</span></span>  
 <span data-ttu-id="1cde7-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="1cde7-107">*srvproc*</span></span>  
 <span data-ttu-id="1cde7-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="1cde7-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="1cde7-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="1cde7-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="1cde7-110">*n*</span><span class="sxs-lookup"><span data-stu-id="1cde7-110">*n*</span></span>  
 <span data-ttu-id="1cde7-111">這指出參數的數目。</span><span class="sxs-lookup"><span data-stu-id="1cde7-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="1cde7-112">第一個參數是 1。</span><span class="sxs-lookup"><span data-stu-id="1cde7-112">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1cde7-113">傳回</span><span class="sxs-lookup"><span data-stu-id="1cde7-113">Returns</span></span>  
 <span data-ttu-id="1cde7-114">參數資料類型的 Token 值。</span><span class="sxs-lookup"><span data-stu-id="1cde7-114">A token value for the data type of the parameter.</span></span> <span data-ttu-id="1cde7-115">如需資料類型的資訊，請參閱[資料類型 &#40;擴充預存程序 API&#41;](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="1cde7-115">For information about data types, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="1cde7-116">如果沒有第 *n* 個參數或是沒有任何遠端預存程序，會傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="1cde7-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns - 1.</span></span>  
  
 <span data-ttu-id="1cde7-117">如果參數是其中一個資料類型，此函數會傳回下列值 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1cde7-117">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="1cde7-118">新的資料類型</span><span class="sxs-lookup"><span data-stu-id="1cde7-118">New data types</span></span>|<span data-ttu-id="1cde7-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="1cde7-119">Return value</span></span>|  
|--------------------|------------------|  
|`BITN`|<span data-ttu-id="1cde7-120">SRVBIT</span><span class="sxs-lookup"><span data-stu-id="1cde7-120">SRVBIT</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="1cde7-121">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="1cde7-121">VARCHAR</span></span>|  
|`BIGCHAR`|<span data-ttu-id="1cde7-122">CHAR</span><span class="sxs-lookup"><span data-stu-id="1cde7-122">CHAR</span></span>|  
|`BIGBINARY`|<span data-ttu-id="1cde7-123">BINARY</span><span class="sxs-lookup"><span data-stu-id="1cde7-123">BINARY</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="1cde7-124">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="1cde7-124">VARBINARY</span></span>|  
|`NCHAR`|<span data-ttu-id="1cde7-125">CHAR</span><span class="sxs-lookup"><span data-stu-id="1cde7-125">CHAR</span></span>|  
|`NVARCHAR`|<span data-ttu-id="1cde7-126">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="1cde7-126">VARCHAR</span></span>|  
|`NTEXT`|<span data-ttu-id="1cde7-127">-1</span><span class="sxs-lookup"><span data-stu-id="1cde7-127">-1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cde7-128">備註</span><span class="sxs-lookup"><span data-stu-id="1cde7-128">Remarks</span></span>  
 <span data-ttu-id="1cde7-129">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="1cde7-129">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="1cde7-130">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1cde7-130">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="1cde7-131">SRV_RPC 的處理常式仍會被呼叫，但看起來就好像沒有任何參數， **srv_rpcparams**會傳回0。</span><span class="sxs-lookup"><span data-stu-id="1cde7-131">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1cde7-132">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="1cde7-132">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="1cde7-133">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="1cde7-133">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cde7-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cde7-134">See Also</span></span>  
 <span data-ttu-id="1cde7-135">[srv_paraminfo &#40;擴充預存程式 API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="1cde7-135">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="1cde7-136">srv_rpcparams &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="1cde7-136">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
