---
title: srv_convert (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_convert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_convert
ms.assetid: 216b4a31-786e-4361-8a33-e5f6e9790f90
author: rothja
ms.author: jroth
ms.openlocfilehash: 30a0ea356f017ed3d1b3ecc85cf483b4553e120a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606314"
---
# <a name="srv_convert-extended-stored-procedure-api"></a><span data-ttu-id="13079-102">srv_convert (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="13079-102">srv_convert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="13079-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="13079-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="13079-104">將資料從某個資料類型變成另一個資料類型。</span><span class="sxs-lookup"><span data-stu-id="13079-104">Changes data from one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13079-105">語法</span><span class="sxs-lookup"><span data-stu-id="13079-105">Syntax</span></span>  
  
```  
  
int srv_convert (  
SRV_PROC *  
srvproc  
,  
int  
srctype  
,  
void *  
src  
,  
DBINT  
srclen  
,  
int  
desttype  
,  
void *  
dest  
,  
DBINT  
destlen  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="13079-106">引數</span><span class="sxs-lookup"><span data-stu-id="13079-106">Arguments</span></span>  
 <span data-ttu-id="13079-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="13079-107">*srvproc*</span></span>  
 <span data-ttu-id="13079-108">是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="13079-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="13079-109">此結構包含了擴充預存程序 API 用來管理應用程式與用戶端之間之通訊和資料的所有控制資訊。</span><span class="sxs-lookup"><span data-stu-id="13079-109">The structure contains all the control information that the Extended Stored Procedure API uses to manage communications and data between the application and the client.</span></span> <span data-ttu-id="13079-110">如果提供了 *srvproc* 控制代碼，則當發生錯誤時會將它傳遞給擴充預存程序 API 錯誤處理函式。</span><span class="sxs-lookup"><span data-stu-id="13079-110">If the *srvproc* handle is supplied, it is passed to the Extended Stored Procedure API error handler function when an error occurs.</span></span>  
  
 <span data-ttu-id="13079-111">*srctype*</span><span class="sxs-lookup"><span data-stu-id="13079-111">*srctype*</span></span>  
 <span data-ttu-id="13079-112">指定要轉換之資料的資料類型。</span><span class="sxs-lookup"><span data-stu-id="13079-112">Specifies the data type of the data to be converted.</span></span> <span data-ttu-id="13079-113">此參數可以是任何擴充預存程序 API 資料類型。</span><span class="sxs-lookup"><span data-stu-id="13079-113">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="13079-114">*src*</span><span class="sxs-lookup"><span data-stu-id="13079-114">*src*</span></span>  
 <span data-ttu-id="13079-115">這是要轉換之資料的指標。</span><span class="sxs-lookup"><span data-stu-id="13079-115">Is a pointer to the data to be converted.</span></span> <span data-ttu-id="13079-116">此參數可以是任何擴充預存程序 API 資料類型。</span><span class="sxs-lookup"><span data-stu-id="13079-116">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="13079-117">*srclen*</span><span class="sxs-lookup"><span data-stu-id="13079-117">*srclen*</span></span>  
 <span data-ttu-id="13079-118">指定要轉換之資料的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="13079-118">Specifies the length, in bytes, of the data to be converted.</span></span> <span data-ttu-id="13079-119">如果 *srclen* 為 0，**srv_convert** 會將 null 值放在目的地變數內。</span><span class="sxs-lookup"><span data-stu-id="13079-119">If *srclen* is 0, **srv_convert** places a null value in the destination variable.</span></span> <span data-ttu-id="13079-120">除非它是 0，否則固定長度的資料類型會忽略這個參數，此時假設來源資料為 NULL。</span><span class="sxs-lookup"><span data-stu-id="13079-120">Unless it is 0, this parameter is ignored for fixed-length data types, in which case the source data is assumed to be NULL.</span></span> <span data-ttu-id="13079-121">如果是 SRVCHAR 資料類型的資料，-1 的長度表示字串是以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="13079-121">For data of the SRVCHAR data type, a length of -1 indicates the string is null-terminated.</span></span>  
  
 <span data-ttu-id="13079-122">*desttype*</span><span class="sxs-lookup"><span data-stu-id="13079-122">*desttype*</span></span>  
 <span data-ttu-id="13079-123">指定要將來源轉換成那一種資料類型。</span><span class="sxs-lookup"><span data-stu-id="13079-123">Specifies the data type to convert the source to.</span></span> <span data-ttu-id="13079-124">此參數可以是任何擴充預存程序 API 資料類型。</span><span class="sxs-lookup"><span data-stu-id="13079-124">This parameter can be any of the Extended Store Procedure API data types.</span></span>  
  
 <span data-ttu-id="13079-125">*dest*</span><span class="sxs-lookup"><span data-stu-id="13079-125">*dest*</span></span>  
 <span data-ttu-id="13079-126">這是接收已轉換之資料的目的地變數的指標。</span><span class="sxs-lookup"><span data-stu-id="13079-126">Is a pointer to the destination variable that receives converted data.</span></span> <span data-ttu-id="13079-127">如果此指標為 NULL，**srv_convert** 會呼叫使用者提供的錯誤處理常式 (如果有的話)，並傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="13079-127">If this pointer is NULL, **srv_convert** calls the user-supplied error handler ,if any, and returns -1.</span></span>  
  
 <span data-ttu-id="13079-128">如果 *desttype* 為 SRVDECIMAL 或 SRVNUMERIC，則 *dest* 參數必須是 DBNUMERIC 或 DBDECIMAL 結構的指標，而且此結構的有效位數及小數位數欄位已設定為您想要的值。</span><span class="sxs-lookup"><span data-stu-id="13079-128">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *dest* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the desired values.</span></span> <span data-ttu-id="13079-129">您可以使用 DEFAULTPRECISION 來指定預設有效位數，並使用 DEFAULTSCALE 來指定預設小數位數。</span><span class="sxs-lookup"><span data-stu-id="13079-129">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
 <span data-ttu-id="13079-130">*destlen*</span><span class="sxs-lookup"><span data-stu-id="13079-130">*destlen*</span></span>  
 <span data-ttu-id="13079-131">指定目的地變數的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="13079-131">Specifies the length, in bytes, of the destination variable.</span></span> <span data-ttu-id="13079-132">固定長度的資料類型會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="13079-132">This parameter is ignored for fixed-length data types.</span></span> <span data-ttu-id="13079-133">如果是 SRVCHAR 類型的目的地變數，*destlen* 的值必須是目的地緩衝區空間的總長度。</span><span class="sxs-lookup"><span data-stu-id="13079-133">For a destination variable of type SRVCHAR, the value of *destlen* must be the total length of the destination buffer space.</span></span> <span data-ttu-id="13079-134">如果 SRVCHAR 或 SRVBINARY 類型的目的地變數長度為 -1，這表示可用的空間很充足。</span><span class="sxs-lookup"><span data-stu-id="13079-134">A length of -1 for a destination variable of type SRVCHAR or SRVBINARY indicates there is sufficient space available.</span></span> <span data-ttu-id="13079-135">如果是 *srvchar* 類型的目的地變數，則 -1 的長度會造成字元字串以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="13079-135">For a destination variable of type *srvchar*, a length of -1 causes the character string to be null-terminated.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="13079-136">傳回</span><span class="sxs-lookup"><span data-stu-id="13079-136">Returns</span></span>  
 <span data-ttu-id="13079-137">如果資料類型轉換成功，則為轉換之資料的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="13079-137">The length of the converted data, in bytes, if the data type conversion succeeds.</span></span> <span data-ttu-id="13079-138">當 **srv_convert** 遇到所不支援的轉換要求時，它會呼叫開發人員提供的錯誤處理常式 (如果有的話)、設定全域錯誤號碼，並傳回 -1。</span><span class="sxs-lookup"><span data-stu-id="13079-138">When **srv_convert** encounters a request for a conversion it does not support, it calls the developer-supplied error handler, if any, sets a global error number, and returns -1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13079-139">備註</span><span class="sxs-lookup"><span data-stu-id="13079-139">Remarks</span></span>  
 <span data-ttu-id="13079-140">**srv_willconvert** 函式會決定是否允許特定的轉換。</span><span class="sxs-lookup"><span data-stu-id="13079-140">The **srv_willconvert** function determines whether a particular conversion is allowed.</span></span>  
  
 <span data-ttu-id="13079-141">轉換成近似的數值資料類型 SRVFLT4 或 SRVFLT8 可能會造成部分有效位數遺失。</span><span class="sxs-lookup"><span data-stu-id="13079-141">Converting to the approximate numeric data types SRVFLT4 or SRVFLT8 can result in some loss of precision.</span></span> <span data-ttu-id="13079-142">從近似的數值資料類型 SRVFLT4 或 SRVFLT8 轉換成 SRVCHAR 或 SRVTEXT 可能會造成部分有效位數遺失。</span><span class="sxs-lookup"><span data-stu-id="13079-142">Converting from the approximate numeric data types SRVFLT4 or SRVFLT8 to SRVCHAR or SRVTEXT can also result in some loss of precision.</span></span>  
  
 <span data-ttu-id="13079-143">轉換成 SRVFLT*x*、SRVINT*x*、SRVMONEY、SRVMONEY4、SRVDECIMAL 或 SRVNUMERIC 可能會造成溢位 (如果此數字大於目的地的最大值) 或是反向溢位 (如果此數字小於目的地的最小值)。</span><span class="sxs-lookup"><span data-stu-id="13079-143">Converting to SRVFLT*x*, SRVINT*x*, SRVMONEY, SRVMONEY4, SRVDECIMAL, or SRVNUMERIC can result in overflow if the number is larger than the maximum value of the destination, or in underflow if the number is smaller than the minimum value of the destination.</span></span> <span data-ttu-id="13079-144">如果轉換成 SRVCHAR 或 SRVTEXT 時發生溢位，結果值的第一個字元會包含星號 (\*) 來指示錯誤。</span><span class="sxs-lookup"><span data-stu-id="13079-144">If overflow occurs when converting to SRVCHAR or SRVTEXT, the first character of the resulting value contains an asterisk (\*) to indicate the error.</span></span>  
  
 <span data-ttu-id="13079-145">將 SRVCHAR 轉換成 SRVBINARY 時，**srv_convert** 會將 SRVCHAR 解譯為十六進位，不論字串是否包含前置 0。</span><span class="sxs-lookup"><span data-stu-id="13079-145">When converting SRVCHAR to SRVBINARY, **srv_convert** interprets SRVCHAR as hexadecimal, whether or not the string contains a leading 0.</span></span> <span data-ttu-id="13079-146">將 SRVBINARY 轉換成 SRVCHAR 時，**srv_convert** 會建立一個十六進位字串，而不含前置 0。</span><span class="sxs-lookup"><span data-stu-id="13079-146">When converting SRVBINARY to SRVCHAR, **srv_convert** creates a hexadecimal string without a leading 0.</span></span> <span data-ttu-id="13079-147">在所有其他狀況下，與 SRVBINARY 資料類型之間的來回轉換純粹是位元複製。</span><span class="sxs-lookup"><span data-stu-id="13079-147">In all other cases, a conversion to or from the SRVBINARY data type is a straight bit-copy.</span></span>  
  
 <span data-ttu-id="13079-148">在某些情況下，將資料類型轉換成它本身會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="13079-148">In certain cases, it can be useful to convert a data type to itself.</span></span> <span data-ttu-id="13079-149">例如，將 SRVCHAR 轉換成 SRVCHAR 並將 *destlen* 設定為 -1 會將 null 結束字元新增至字串。</span><span class="sxs-lookup"><span data-stu-id="13079-149">For example, converting SRVCHAR to SRVCHAR with a *destlen* of -1 adds a null terminator to a string.</span></span>  
  
 <span data-ttu-id="13079-150">如需資料類型及擴充預存程序 API 資料類型轉換的描述，請參閱[資料類型 &#40;擴充預存程序 API&#41;](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="13079-150">For a description of data types and Extended Store Procedure API data type conversions, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="13079-151">**srv_convert** 函式失敗的原因有好幾個：</span><span class="sxs-lookup"><span data-stu-id="13079-151">The **srv_convert** function can fail for several reasons:</span></span>  
  
-   <span data-ttu-id="13079-152">無法使用要求的轉換。</span><span class="sxs-lookup"><span data-stu-id="13079-152">The requested conversion is not available.</span></span>  
  
-   <span data-ttu-id="13079-153">轉換導致目的地變數中的有效位數遭到截斷、溢位或遺失。</span><span class="sxs-lookup"><span data-stu-id="13079-153">The conversion resulted in truncation, overflow, or loss of precision in the destination variable.</span></span>  
  
-   <span data-ttu-id="13079-154">將字元字串轉換成數值資料類型時所發生的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="13079-154">A syntax error occurred while converting a character string to a numeric data type.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13079-155">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="13079-155">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="13079-156">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="13079-156">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13079-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13079-157">See Also</span></span>  
 <span data-ttu-id="13079-158">[srv_setutype &#40;擴充預存程式 API&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="13079-158">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="13079-159">srv_willconvert &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="13079-159">srv_willconvert &#40;Extended Stored Procedure API&#41;</span></span>](srv-willconvert-extended-stored-procedure-api.md)  
  
  
