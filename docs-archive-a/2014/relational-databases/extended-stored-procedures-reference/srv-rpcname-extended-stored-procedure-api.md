---
title: srv_rpcname (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcname
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcname
ms.assetid: 0a1424e4-3319-4836-b8d8-5e0344cc683f
author: rothja
ms.author: jroth
ms.openlocfilehash: 21530b3e7b8aaa8c5a3f8770762cde7e258e3a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709477"
---
# <a name="srv_rpcname-extended-stored-procedure-api"></a><span data-ttu-id="15b7d-102">srv_rpcname (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="15b7d-102">srv_rpcname (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="15b7d-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="15b7d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="15b7d-104">傳回目前遠端預存程序的程序名稱元件。</span><span class="sxs-lookup"><span data-stu-id="15b7d-104">Returns the procedure name component for the current remote stored procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15b7d-105">語法</span><span class="sxs-lookup"><span data-stu-id="15b7d-105">Syntax</span></span>  
  
```  
  
DBCHAR * srv_rpcname (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="15b7d-106">引數</span><span class="sxs-lookup"><span data-stu-id="15b7d-106">Arguments</span></span>  
 <span data-ttu-id="15b7d-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="15b7d-107">*srvproc*</span></span>  
 <span data-ttu-id="15b7d-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序)。</span><span class="sxs-lookup"><span data-stu-id="15b7d-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure).</span></span> <span data-ttu-id="15b7d-109">此結構包含了一些資訊，擴充預存程序 API 程式庫會使用這些資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="15b7d-109">The structure contains information that the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="15b7d-110">*len*</span><span class="sxs-lookup"><span data-stu-id="15b7d-110">*len*</span></span>  
 <span data-ttu-id="15b7d-111">這是整數變數的指標，此變數會接收資料庫名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="15b7d-111">Is a pointer to an integer variable that receives the length of the database name.</span></span> <span data-ttu-id="15b7d-112">如果 *len* 為 NULL，則不會傳回遠端預存程序名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="15b7d-112">If *len* is NULL, the length of the remote stored procedure name is not returned.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="15b7d-113">傳回</span><span class="sxs-lookup"><span data-stu-id="15b7d-113">Returns</span></span>  
 <span data-ttu-id="15b7d-114">目前遠端預存程序之遠端預存程序名稱元件中以 Null 結尾字串的 DBCHAR 指標。</span><span class="sxs-lookup"><span data-stu-id="15b7d-114">A DBCHAR pointer to the null-terminated string for the remote stored procedure name component of the current remote stored procedure.</span></span> <span data-ttu-id="15b7d-115">如果目前沒有遠端預存程序，則會傳回 NULL 且 *len* 設定為 - 1。</span><span class="sxs-lookup"><span data-stu-id="15b7d-115">If there is not a current remote stored procedure, NULL is returned and *len* is set to -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15b7d-116">備註</span><span class="sxs-lookup"><span data-stu-id="15b7d-116">Remarks</span></span>  
 <span data-ttu-id="15b7d-117">此函數只會傳回遠端預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="15b7d-117">This function returns only the name of the remote stored procedure.</span></span> <span data-ttu-id="15b7d-118">這不包含擁有者、資料庫名稱和遠端預存程序號碼的選擇性規範。</span><span class="sxs-lookup"><span data-stu-id="15b7d-118">It does not include the optional specifiers for owner, database name, and remote stored procedure number.</span></span>  
  
 <span data-ttu-id="15b7d-119">由於沒有遠端預存程序時呼叫 **srv_rpcname** 是有效的做法 (不會出現任何參考用錯誤)，所以這個函式會提供一種方法來判斷遠端預存程序是否存在。</span><span class="sxs-lookup"><span data-stu-id="15b7d-119">Because it is valid to call **srv_rpcname** when there is not a remote stored procedure (no informational error occurs), this function provides a method for determining whether a remote stored procedure exists.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="15b7d-120">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="15b7d-120">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="15b7d-121">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="15b7d-121">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
