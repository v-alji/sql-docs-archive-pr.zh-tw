---
title: srv_rpcnumber (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
author: rothja
ms.author: jroth
ms.openlocfilehash: 25f30f8288125cf64d6b10a867d6af03c0f8ee91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709474"
---
# <a name="srv_rpcnumber-extended-stored-procedure-api"></a><span data-ttu-id="01d17-102">srv_rpcnumber (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="01d17-102">srv_rpcnumber (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="01d17-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="01d17-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="01d17-104">傳回目前遠端預存程序呼叫的數字元件。</span><span class="sxs-lookup"><span data-stu-id="01d17-104">Returns the number component for the current remote stored procedure call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01d17-105">語法</span><span class="sxs-lookup"><span data-stu-id="01d17-105">Syntax</span></span>  
  
```  
  
int srv_rpcnumber ( SRV_PROC *  
srvproc   
)  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="01d17-106">引數</span><span class="sxs-lookup"><span data-stu-id="01d17-106">Arguments</span></span>  
 <span data-ttu-id="01d17-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="01d17-107">*srvproc*</span></span>  
 <span data-ttu-id="01d17-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序)。</span><span class="sxs-lookup"><span data-stu-id="01d17-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="01d17-109">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="01d17-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="01d17-110">傳回</span><span class="sxs-lookup"><span data-stu-id="01d17-110">Returns</span></span>  
 <span data-ttu-id="01d17-111">目前遠端預存程序的數字元件。</span><span class="sxs-lookup"><span data-stu-id="01d17-111">The number component for the current remote stored procedure.</span></span> <span data-ttu-id="01d17-112">如果用戶端在執行遠端預存程序時未使用數字元件，或者並沒有目前的遠端預存程序，則會傳回 – 1。</span><span class="sxs-lookup"><span data-stu-id="01d17-112">If the client does not use a number component when running the remote stored procedure or if there is no current remote stored procedure, it returns - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01d17-113">備註</span><span class="sxs-lookup"><span data-stu-id="01d17-113">Remarks</span></span>  
 <span data-ttu-id="01d17-114">此函數只會傳回遠端預存程序的數字元件。</span><span class="sxs-lookup"><span data-stu-id="01d17-114">This function returns only the number component of the remote stored procedure.</span></span> <span data-ttu-id="01d17-115">不包含擁有人、遠端預存程序名稱和資料庫名稱的選擇性規範。</span><span class="sxs-lookup"><span data-stu-id="01d17-115">It does not include the optional specifiers for owner, remote stored procedure name, and database name.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="01d17-116">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="01d17-116">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="01d17-117">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="01d17-117">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
