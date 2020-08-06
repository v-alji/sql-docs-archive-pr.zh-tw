---
title: srv_rpcowner (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcowner
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
ms.openlocfilehash: f903870d0ee01256addb1557eb7e9123853b39e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710606"
---
# <a name="srv_rpcowner-extended-stored-procedure-api"></a><span data-ttu-id="0c338-102">srv_rpcowner (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="0c338-102">srv_rpcowner (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="0c338-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="0c338-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="0c338-104">傳回目前遠端預存程序的擁有者元件。</span><span class="sxs-lookup"><span data-stu-id="0c338-104">Returns the owner component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c338-105">語法</span><span class="sxs-lookup"><span data-stu-id="0c338-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c338-106">引數</span><span class="sxs-lookup"><span data-stu-id="0c338-106">Arguments</span></span>  
 <span data-ttu-id="0c338-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="0c338-107">*srvproc*</span></span>  
 <span data-ttu-id="0c338-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序)。</span><span class="sxs-lookup"><span data-stu-id="0c338-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="0c338-109">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="0c338-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="0c338-110">*len*</span><span class="sxs-lookup"><span data-stu-id="0c338-110">*len*</span></span>  
 <span data-ttu-id="0c338-111">這是整數變數的指標，此變數會接收擁有者名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="0c338-111">Is a pointer to an integer variable that receives the length of the owner name.</span></span> <span data-ttu-id="0c338-112">參數 *len* 可以是 NULL，在此情況下將不會傳回擁有者元件的長度。</span><span class="sxs-lookup"><span data-stu-id="0c338-112">The parameter *len* can be NULL, in which case the length of the owner component is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="0c338-113">傳回</span><span class="sxs-lookup"><span data-stu-id="0c338-113">Returns</span></span>  
 <span data-ttu-id="0c338-114">DBCHAR 指標，指向目前遠端預存程序之以 null 結尾的擁有者元件。</span><span class="sxs-lookup"><span data-stu-id="0c338-114">A DBCHAR pointer to the null-terminated owner component for the current remote stored procedure.</span></span> <span data-ttu-id="0c338-115">如果目前沒有遠端預存程序，則會傳回 NULL 且 *len* 設定為 - 1。</span><span class="sxs-lookup"><span data-stu-id="0c338-115">If there is no current remote stored procedure, NULL is returned and *len* is set to - 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c338-116">備註</span><span class="sxs-lookup"><span data-stu-id="0c338-116">Remarks</span></span>  
 <span data-ttu-id="0c338-117">此函數只會傳回遠端預存程序的擁有者元件。</span><span class="sxs-lookup"><span data-stu-id="0c338-117">This function returns only the owner component of the remote stored procedure.</span></span> <span data-ttu-id="0c338-118">這不包含名稱、遠端預存程序名稱和遠端預存程序號碼的選擇性規範。</span><span class="sxs-lookup"><span data-stu-id="0c338-118">It does not include the optional specifiers for name, remote stored procedure name, and remote stored procedure number.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0c338-119">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="0c338-119">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="0c338-120">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="0c338-120">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
