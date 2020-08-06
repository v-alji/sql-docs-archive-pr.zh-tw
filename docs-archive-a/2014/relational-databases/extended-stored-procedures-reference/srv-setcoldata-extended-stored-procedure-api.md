---
title: srv_setcoldata (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
ms.openlocfilehash: b67aa2f7b5a37057d2ed87846689919d84ec4aaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707566"
---
# <a name="srv_setcoldata-extended-stored-procedure-api"></a><span data-ttu-id="1071d-102">srv_setcoldata (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="1071d-102">srv_setcoldata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="1071d-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="1071d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="1071d-104">指定資料行資料的目前位址。</span><span class="sxs-lookup"><span data-stu-id="1071d-104">Specifies the current address for a column's data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1071d-105">語法</span><span class="sxs-lookup"><span data-stu-id="1071d-105">Syntax</span></span>  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1071d-106">引數</span><span class="sxs-lookup"><span data-stu-id="1071d-106">Arguments</span></span>  
 <span data-ttu-id="1071d-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="1071d-107">*srvproc*</span></span>  
 <span data-ttu-id="1071d-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1071d-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="1071d-109">擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。</span><span class="sxs-lookup"><span data-stu-id="1071d-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="1071d-110">*column*</span><span class="sxs-lookup"><span data-stu-id="1071d-110">*column*</span></span>  
 <span data-ttu-id="1071d-111">表示指定位址之目標資料行的編號。</span><span class="sxs-lookup"><span data-stu-id="1071d-111">Indicates the number of the column the address is being specified for.</span></span> <span data-ttu-id="1071d-112">資料行的編號會從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="1071d-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="1071d-113">*data*</span><span class="sxs-lookup"><span data-stu-id="1071d-113">*data*</span></span>  
 <span data-ttu-id="1071d-114">這是資料行資料的指標。</span><span class="sxs-lookup"><span data-stu-id="1071d-114">Is a pointer for a column's data.</span></span> <span data-ttu-id="1071d-115">配置給 *data* 的記憶體要等到另一個 **srv_setcoldata** 呼叫取代資料行資料或是呼叫 **srv_senddone** 之後，才能釋放。</span><span class="sxs-lookup"><span data-stu-id="1071d-115">Memory allocated for *data* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="1071d-116">傳回</span><span class="sxs-lookup"><span data-stu-id="1071d-116">Returns</span></span>  
 <span data-ttu-id="1071d-117">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="1071d-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1071d-118">備註</span><span class="sxs-lookup"><span data-stu-id="1071d-118">Remarks</span></span>  
 <span data-ttu-id="1071d-119">資料列的每個資料行必須先用 **srv_describe** 定義。</span><span class="sxs-lookup"><span data-stu-id="1071d-119">Each column of the row must be defined first with **srv_describe**.</span></span> <span data-ttu-id="1071d-120">資料行資料位址最初是以 **srv_describe** 設定。</span><span class="sxs-lookup"><span data-stu-id="1071d-120">Column data addresses are initially set with **srv_describe**.</span></span> <span data-ttu-id="1071d-121">如果資料行資料的位址變更，則必須呼叫 **srv_setcoldata** 來指定資料的新位址，而且必須針對每一個變更的資料行個別呼叫 **srv_setcoldata**。</span><span class="sxs-lookup"><span data-stu-id="1071d-121">If the address of the column data changes, **srv_setcoldata** must be called to specify the new address of the data and **srv_setcoldata** must be called separately for each changed column.</span></span>  
  
 <span data-ttu-id="1071d-122">Null 資料的表示方式是使用 **srv_setcollen** 將資料行的長度設定為 0。</span><span class="sxs-lookup"><span data-stu-id="1071d-122">Null data is represented by setting the column's length to 0 with **srv_setcollen**.</span></span> <span data-ttu-id="1071d-123">然後會忽略資料位址。</span><span class="sxs-lookup"><span data-stu-id="1071d-123">The data address is then ignored.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1071d-124">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="1071d-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="1071d-125">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="1071d-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1071d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1071d-126">See Also</span></span>  
 [<span data-ttu-id="1071d-127">srv_describe &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="1071d-127">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
