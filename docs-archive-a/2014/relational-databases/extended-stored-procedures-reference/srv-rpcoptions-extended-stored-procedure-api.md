---
title: srv_rpcoptions (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
ms.openlocfilehash: f5ebe4ab48721002e679ce149293b474a934e348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710609"
---
# <a name="srv_rpcoptions-extended-stored-procedure-api"></a><span data-ttu-id="1f306-102">srv_rpcoptions (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="1f306-102">srv_rpcoptions (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="1f306-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="1f306-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="1f306-104">傳回目前遠端預存程序的執行階段選項。</span><span class="sxs-lookup"><span data-stu-id="1f306-104">Returns run-time options for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f306-105">語法</span><span class="sxs-lookup"><span data-stu-id="1f306-105">Syntax</span></span>  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f306-106">引數</span><span class="sxs-lookup"><span data-stu-id="1f306-106">Arguments</span></span>  
 <span data-ttu-id="1f306-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="1f306-107">*srvproc*</span></span>  
 <span data-ttu-id="1f306-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序)。</span><span class="sxs-lookup"><span data-stu-id="1f306-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="1f306-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="1f306-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1f306-110">傳回</span><span class="sxs-lookup"><span data-stu-id="1f306-110">Returns</span></span>  
 <span data-ttu-id="1f306-111">是點陣圖，包含聯結在目前遠端預存程序的邏輯 OR 之執行階段旗標。</span><span class="sxs-lookup"><span data-stu-id="1f306-111">A bitmap that contains the run-time flags joined in a logical OR for the current remote stored procedure.</span></span> <span data-ttu-id="1f306-112">如果沒有目前遠端預存程序，則會傳回 0 ，並且產生訊息。</span><span class="sxs-lookup"><span data-stu-id="1f306-112">If there is not a current remote stored procedure, 0 is returned and a message is generated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f306-113">備註</span><span class="sxs-lookup"><span data-stu-id="1f306-113">Remarks</span></span>  
 <span data-ttu-id="1f306-114">下表描述每個執行階段旗標。</span><span class="sxs-lookup"><span data-stu-id="1f306-114">The following table describes each run-time flag.</span></span>  
  
|<span data-ttu-id="1f306-115">執行階段旗標</span><span class="sxs-lookup"><span data-stu-id="1f306-115">Run-time flag</span></span>|<span data-ttu-id="1f306-116">描述</span><span class="sxs-lookup"><span data-stu-id="1f306-116">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1f306-117">SRV_NOMETADATA</span><span class="sxs-lookup"><span data-stu-id="1f306-117">SRV_NOMETADATA</span></span>|<span data-ttu-id="1f306-118">用戶端已要求不含中繼資料資訊的結果。</span><span class="sxs-lookup"><span data-stu-id="1f306-118">The client has requested results without metadata information.</span></span> <span data-ttu-id="1f306-119">只有在用戶端與實例通訊時，才會使用這個旗標 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1f306-119">This flag is only used when the client is communicating with an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1f306-120">擴充預存程序 API 應用程式無法省略中繼資料資訊。</span><span class="sxs-lookup"><span data-stu-id="1f306-120">An Extended Stored Procedure API application cannot omit metadata information.</span></span>|  
|<span data-ttu-id="1f306-121">SRV_RECOMPILE</span><span class="sxs-lookup"><span data-stu-id="1f306-121">SRV_RECOMPILE</span></span>|<span data-ttu-id="1f306-122">用戶端已經要求先重新編譯遠端預存程序，再執行它。</span><span class="sxs-lookup"><span data-stu-id="1f306-122">The client has requested to recompile the remote stored procedure before executing it.</span></span> <span data-ttu-id="1f306-123">這個旗標可能無法套用至擴充預存程序 API 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1f306-123">This flag may not apply to an Extended Stored Procedure API application.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1f306-124">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="1f306-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="1f306-125">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="1f306-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
