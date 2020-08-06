---
title: srv_alloc (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b372c1b43987e5bebd1fb82e995dc6d262455ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593398"
---
# <a name="srv_alloc-extended-stored-procedure-api"></a><span data-ttu-id="a3c77-102">srv_alloc (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="a3c77-102">srv_alloc (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="a3c77-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="a3c77-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="a3c77-104">以動態方式配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="a3c77-104">Allocates memory dynamically.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3c77-105">語法</span><span class="sxs-lookup"><span data-stu-id="a3c77-105">Syntax</span></span>  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3c77-106">引數</span><span class="sxs-lookup"><span data-stu-id="a3c77-106">Arguments</span></span>  
 <span data-ttu-id="a3c77-107">*size*</span><span class="sxs-lookup"><span data-stu-id="a3c77-107">*size*</span></span>  
 <span data-ttu-id="a3c77-108">指定要配置的位元組數。</span><span class="sxs-lookup"><span data-stu-id="a3c77-108">Specifies the number of bytes to allocate.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a3c77-109">傳回</span><span class="sxs-lookup"><span data-stu-id="a3c77-109">Returns</span></span>  
 <span data-ttu-id="a3c77-110">新配置空間的指標。</span><span class="sxs-lookup"><span data-stu-id="a3c77-110">A pointer to the newly allocated space.</span></span> <span data-ttu-id="a3c77-111">如果無法配置 *size* 個位元組，就會傳回 Null 指標。</span><span class="sxs-lookup"><span data-stu-id="a3c77-111">If *size* bytes cannot be allocated, a null pointer is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3c77-112">備註</span><span class="sxs-lookup"><span data-stu-id="a3c77-112">Remarks</span></span>  
 <span data-ttu-id="a3c77-113">**srv_alloc** 函式相當於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API **GlobalAlloc** 函式。</span><span class="sxs-lookup"><span data-stu-id="a3c77-113">The **srv_alloc** function is equivalent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API  **GlobalAlloc** function.</span></span> <span data-ttu-id="a3c77-114">一般 Windows API C 執行階段記憶體管理函數可用在擴充預存程序 API 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a3c77-114">Normal Windows API C run-time memory management functions can be used in an Extended Stored Procedure API application.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a3c77-115">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="a3c77-115">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="a3c77-116">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="a3c77-116">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
