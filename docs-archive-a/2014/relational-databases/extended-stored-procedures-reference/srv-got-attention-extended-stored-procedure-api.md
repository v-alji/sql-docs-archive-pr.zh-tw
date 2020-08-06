---
title: srv_got_attention (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_got_attention
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
author: rothja
ms.author: jroth
ms.openlocfilehash: bb5432e2f5e259187e506237842fbb9110e27a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709501"
---
# <a name="srv_got_attention-extended-stored-procedure-api"></a><span data-ttu-id="c82f7-102">srv_got_attention (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="c82f7-102">srv_got_attention (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="c82f7-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="c82f7-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="c82f7-104">檢查是否需要中止目前的連接或工作，並在連接遭到清除或批次遭到中止時傳回 TRUE</span><span class="sxs-lookup"><span data-stu-id="c82f7-104">Checks whether the current connection or task needs to be aborted and returns TRUE if the connection is killed or the batch is aborted</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c82f7-105">語法</span><span class="sxs-lookup"><span data-stu-id="c82f7-105">Syntax</span></span>  
  
```  
  
BOOL srv_got_attention  
(SRV_PROC *  
srvproc  
);  
  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c82f7-106">參數</span><span class="sxs-lookup"><span data-stu-id="c82f7-106">Parameters</span></span>  
 <span data-ttu-id="c82f7-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="c82f7-107">*srvproc*</span></span>  
 <span data-ttu-id="c82f7-108">識別資料庫連接的指標。</span><span class="sxs-lookup"><span data-stu-id="c82f7-108">Pointer identifying a database connection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c82f7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c82f7-109">Return Value</span></span>  
 <span data-ttu-id="c82f7-110">如果連接遭到清除或批次遭到中止，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="c82f7-110">TRUE if the connection is killed or the batch is aborted.</span></span> <span data-ttu-id="c82f7-111">如果連接或批次作用中，則為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="c82f7-111">FALSE if the connection or batch is active.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c82f7-112">備註</span><span class="sxs-lookup"><span data-stu-id="c82f7-112">Remarks</span></span>  
 <span data-ttu-id="c82f7-113">長時間執行的擴充預存程序應該透過定期呼叫 **srv_got_attention** 來檢查伺服器的注意事項，讓該程序可以在連線到終止或批次遭到中止時自行結束。</span><span class="sxs-lookup"><span data-stu-id="c82f7-113">A long-running extended stored procedure should check the server attention by calling **srv_got_attention** periodically so that the procedure may terminate itself when the connection is killed or the batch is aborted.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c82f7-114">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="c82f7-114">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="c82f7-115">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="c82f7-115">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
