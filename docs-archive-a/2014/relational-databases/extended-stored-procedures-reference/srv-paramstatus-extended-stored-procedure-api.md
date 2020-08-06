---
title: srv_paramstatus (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramstatus
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
author: rothja
ms.author: jroth
ms.openlocfilehash: d89d4ccbb6a97ff47669ad4ed9c0b4c22ac934eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686926"
---
# <a name="srv_paramstatus-extended-stored-procedure-api"></a><span data-ttu-id="90efc-102">srv_paramstatus (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="90efc-102">srv_paramstatus (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="90efc-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="90efc-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="90efc-104">傳回特定遠端預存程序呼叫參數的狀態。</span><span class="sxs-lookup"><span data-stu-id="90efc-104">Returns the status of a particular remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90efc-105">語法</span><span class="sxs-lookup"><span data-stu-id="90efc-105">Syntax</span></span>  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="90efc-106">引數</span><span class="sxs-lookup"><span data-stu-id="90efc-106">Arguments</span></span>  
 <span data-ttu-id="90efc-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="90efc-107">*srvproc*</span></span>  
 <span data-ttu-id="90efc-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="90efc-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="90efc-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="90efc-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="90efc-110">*n*</span><span class="sxs-lookup"><span data-stu-id="90efc-110">*n*</span></span>  
 <span data-ttu-id="90efc-111">這指出參數的數目。</span><span class="sxs-lookup"><span data-stu-id="90efc-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="90efc-112">第一個參數是數字 1。</span><span class="sxs-lookup"><span data-stu-id="90efc-112">The first parameter is number 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="90efc-113">傳回</span><span class="sxs-lookup"><span data-stu-id="90efc-113">Returns</span></span>  
 <span data-ttu-id="90efc-114">包含參數之狀態旗標的 `int`。</span><span class="sxs-lookup"><span data-stu-id="90efc-114">An `int` that contains status flags for the parameter.</span></span> <span data-ttu-id="90efc-115">目前只有一個旗標：如果位元 0 設定為 1，參數為傳回參數。</span><span class="sxs-lookup"><span data-stu-id="90efc-115">Currently, there is only one flag: If bit 0 is set to 1, the parameter is a return parameter.</span></span> <span data-ttu-id="90efc-116">如果沒有第 *n* 個參數或是沒有任何遠端預存程序，其會傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="90efc-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90efc-117">備註</span><span class="sxs-lookup"><span data-stu-id="90efc-117">Remarks</span></span>  
 <span data-ttu-id="90efc-118">此常式會傳回遠端預存程序呼叫參數的狀態旗標。</span><span class="sxs-lookup"><span data-stu-id="90efc-118">This routine returns the status flags for a remote stored procedure call parameter.</span></span>  
  
 <span data-ttu-id="90efc-119">參數包含了在用戶端和應用程式之間傳遞的資料，其中包含遠端預存程序。</span><span class="sxs-lookup"><span data-stu-id="90efc-119">Parameters contain data passed between clients and the application with remote stored procedures.</span></span> <span data-ttu-id="90efc-120">用戶端可以將某些參數指定為傳回參數。</span><span class="sxs-lookup"><span data-stu-id="90efc-120">The client can specify certain parameters as return parameters.</span></span> <span data-ttu-id="90efc-121">這些傳回參數可包含應用程式傳回給用戶端的值。</span><span class="sxs-lookup"><span data-stu-id="90efc-121">These return parameters can contain values that the application passes back to the client.</span></span>  
  
 <span data-ttu-id="90efc-122">目前唯一的狀態旗標為指出參數是否為傳回參數的旗標。</span><span class="sxs-lookup"><span data-stu-id="90efc-122">Currently, the only status flag is one that indicates whether the parameter is a return parameter.</span></span>  
  
 <span data-ttu-id="90efc-123">當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。</span><span class="sxs-lookup"><span data-stu-id="90efc-123">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="90efc-124">如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="90efc-124">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="90efc-125">如果發生錯誤，仍然會呼叫 SRV_RPC 處理常式，但看起來就好像沒有任何參數， **srv_rpcparams**會傳回0。</span><span class="sxs-lookup"><span data-stu-id="90efc-125">If an error occurs, the SRV_RPC handler is still called, but it appears as if there were no parameters, and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="90efc-126">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="90efc-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="90efc-127">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="90efc-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90efc-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90efc-128">See Also</span></span>  
 [<span data-ttu-id="90efc-129">srv_rpcparams &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="90efc-129">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
