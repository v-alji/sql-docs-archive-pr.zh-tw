---
title: srv_willconvert (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_willconvert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b9adfbd2a73b30cbfc0229b7942f79d3ddc1a82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709473"
---
# <a name="srv_willconvert-extended-stored-procedure-api"></a><span data-ttu-id="868fe-102">srv_willconvert (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="868fe-102">srv_willconvert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="868fe-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="868fe-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="868fe-104">決定 ODS 程式庫中是否提供特定資料類型轉換。</span><span class="sxs-lookup"><span data-stu-id="868fe-104">Determines whether a specific data type conversion is available within the ODS Library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="868fe-105">語法</span><span class="sxs-lookup"><span data-stu-id="868fe-105">Syntax</span></span>  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="868fe-106">引數</span><span class="sxs-lookup"><span data-stu-id="868fe-106">Arguments</span></span>  
 <span data-ttu-id="868fe-107">*srctype*</span><span class="sxs-lookup"><span data-stu-id="868fe-107">*srctype*</span></span>  
 <span data-ttu-id="868fe-108">表示要轉換之資料的資料類型。</span><span class="sxs-lookup"><span data-stu-id="868fe-108">Indicates the data type of the data to be converted.</span></span> <span data-ttu-id="868fe-109">此參數可以是任何擴充預存程序 API 資料類型。</span><span class="sxs-lookup"><span data-stu-id="868fe-109">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
 <span data-ttu-id="868fe-110">*desttype*</span><span class="sxs-lookup"><span data-stu-id="868fe-110">*desttype*</span></span>  
 <span data-ttu-id="868fe-111">表示轉換來源資料的目標資料類型。</span><span class="sxs-lookup"><span data-stu-id="868fe-111">Indicates the data type to which the source data is converted.</span></span> <span data-ttu-id="868fe-112">此參數可以是任何擴充預存程序 API 資料類型。</span><span class="sxs-lookup"><span data-stu-id="868fe-112">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="868fe-113">傳回</span><span class="sxs-lookup"><span data-stu-id="868fe-113">Returns</span></span>  
 <span data-ttu-id="868fe-114">支援資料類型轉換時為 TRUE；不支援資料類型轉換時則為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="868fe-114">TRUE if the data type conversion is supported; FALSE if the data type conversion is not supported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="868fe-115">備註</span><span class="sxs-lookup"><span data-stu-id="868fe-115">Remarks</span></span>  
 <span data-ttu-id="868fe-116">如需每種資料類型的描述，請參閱[資料類型 &#40;擴充預存程序 API&#41;](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="868fe-116">For a description of each data type, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="868fe-117">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="868fe-117">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="868fe-118">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="868fe-118">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="868fe-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="868fe-119">See Also</span></span>  
 [<span data-ttu-id="868fe-120">srv_convert &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="868fe-120">srv_convert &#40;Extended Stored Procedure API&#41;</span></span>](srv-convert-extended-stored-procedure-api.md)  
  
  
