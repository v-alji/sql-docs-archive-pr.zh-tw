---
title: srv_setutype (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: e9e02605995e44f5869633d5e8778a955236005f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707565"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a><span data-ttu-id="6ddd3-102">srv_setutype (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="6ddd3-102">srv_setutype (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="6ddd3-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6ddd3-104">針對資料列中的資料行設定使用者定義資料類型。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-104">Sets the user-defined data type for a column in a row.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ddd3-105">語法</span><span class="sxs-lookup"><span data-stu-id="6ddd3-105">Syntax</span></span>  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ddd3-106">引數</span><span class="sxs-lookup"><span data-stu-id="6ddd3-106">Arguments</span></span>  
 <span data-ttu-id="6ddd3-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="6ddd3-107">*srvproc*</span></span>  
 <span data-ttu-id="6ddd3-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="6ddd3-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="6ddd3-110">*column*</span><span class="sxs-lookup"><span data-stu-id="6ddd3-110">*column*</span></span>  
 <span data-ttu-id="6ddd3-111">指出要設定的資料行。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-111">Indicates which column to set.</span></span> <span data-ttu-id="6ddd3-112">資料行的編號會從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="6ddd3-113">*user_type*</span><span class="sxs-lookup"><span data-stu-id="6ddd3-113">*user_type*</span></span>  
 <span data-ttu-id="6ddd3-114">指定使用者定義資料類型程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-114">Specifies the user-defined data type code.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6ddd3-115">傳回</span><span class="sxs-lookup"><span data-stu-id="6ddd3-115">Returns</span></span>  
 <span data-ttu-id="6ddd3-116">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-116">SUCCEED or FAIL.</span></span> <span data-ttu-id="6ddd3-117">如果此資料行不存在，則會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-117">Returns FAIL if the column does not exist.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ddd3-118">備註</span><span class="sxs-lookup"><span data-stu-id="6ddd3-118">Remarks</span></span>  
 <span data-ttu-id="6ddd3-119">一個資料行有兩個資料類型：其實際資料類型與其使用者定義資料類型。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-119">A column has two data types: its actual data type and its user-defined data type.</span></span> <span data-ttu-id="6ddd3-120">使用者定義資料類型是由用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來儲存資料行的實際使用者定義資料類型（如果有的話）以及資料行描述資訊，例如資料行的 null 屬性和可更新性。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-120">The user-defined data type is used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to store the actual user-defined data type of the column, if any, and column description information, such as nullability and updatability, for the column.</span></span>  
  
 <span data-ttu-id="6ddd3-121">利用 **srv_describe** 定義 *column* 時，以及最後一個資料列送出之前，可以呼叫 **srv_setutype** 函式。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-121">The **srv_setutype** function can be called any time that *column* has been defined with **srv_describe** and before the last row has been sent.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6ddd3-122">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-122">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6ddd3-123">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="6ddd3-123">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ddd3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ddd3-124">See Also</span></span>  
 [<span data-ttu-id="6ddd3-125">srv_describe &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="6ddd3-125">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
