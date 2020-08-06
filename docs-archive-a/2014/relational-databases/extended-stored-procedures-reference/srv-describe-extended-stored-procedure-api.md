---
title: srv_describe (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_describe
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_describe
ms.assetid: 2115600e-5ce7-4be0-9cd3-a1dd1fab0729
author: rothja
ms.author: jroth
ms.openlocfilehash: 52a397b79f4fcecaa2ccacde7500cb852ae793fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606313"
---
# <a name="srv_describe-extended-stored-procedure-api"></a><span data-ttu-id="b6471-102">srv_describe (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="b6471-102">srv_describe (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="b6471-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="b6471-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="b6471-104">針對資料列中的特定資料行定義資料行名稱以及來源和目的地資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6471-104">Defines the column name and source and destination data types for a specific column in a row.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6471-105">語法</span><span class="sxs-lookup"><span data-stu-id="b6471-105">Syntax</span></span>  
  
```  
  
int srv_describe (  
SRV_PROC *  
srvproc  
,  
int  
colnumber  
,  
DBCHAR *  
column_name  
,  
int  
namelen  
,  
DBINT  
desttype  
,  
DBINT  
destlen  
,  
DBINT  
srctype  
,  
DBINT  
srclen  
,  
void *  
srcdata  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6471-106">引數</span><span class="sxs-lookup"><span data-stu-id="b6471-106">Arguments</span></span>  
 <span data-ttu-id="b6471-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="b6471-107">*srvproc*</span></span>  
 <span data-ttu-id="b6471-108">這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (此案例中為傳送資料列的用戶端)。</span><span class="sxs-lookup"><span data-stu-id="b6471-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the client sending the row).</span></span> <span data-ttu-id="b6471-109">此結構包含了擴充預存程序 API 程式庫用來管理應用程式與用戶端之間之通訊和資料的所有資訊。</span><span class="sxs-lookup"><span data-stu-id="b6471-109">The structure contains all the information that the Extended Stored Procedure API library uses to manage communications and data between the application and the client.</span></span>  
  
 <span data-ttu-id="b6471-110">*colnumber*</span><span class="sxs-lookup"><span data-stu-id="b6471-110">*colnumber*</span></span>  
 <span data-ttu-id="b6471-111">目前不支援。</span><span class="sxs-lookup"><span data-stu-id="b6471-111">Is currently not supported.</span></span> <span data-ttu-id="b6471-112">必須依序描述資料行。</span><span class="sxs-lookup"><span data-stu-id="b6471-112">Columns must be described in order.</span></span> <span data-ttu-id="b6471-113">所有資料行都必須在呼叫 **srv_sendrow** 之前描述。</span><span class="sxs-lookup"><span data-stu-id="b6471-113">All columns must be described before **srv_sendrow** is called.</span></span>  
  
 <span data-ttu-id="b6471-114">*column_name*</span><span class="sxs-lookup"><span data-stu-id="b6471-114">*column_name*</span></span>  
 <span data-ttu-id="b6471-115">指定資料所屬的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="b6471-115">Specifies the name of the column to which the data belongs.</span></span> <span data-ttu-id="b6471-116">這個參數可以是 NULL，因為資料行不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="b6471-116">This parameter can be NULL because a column is not required to have a name.</span></span>  
  
 <span data-ttu-id="b6471-117">*namelen*</span><span class="sxs-lookup"><span data-stu-id="b6471-117">*namelen*</span></span>  
 <span data-ttu-id="b6471-118">指定 *column_name* 的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="b6471-118">Specifies the length, in bytes, of *column_name*.</span></span> <span data-ttu-id="b6471-119">如果 *namelen* 是 SRV_NULLTERM，則 *column_name* 必須以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="b6471-119">If *namelen* is SRV_NULLTERM, then *column_name* must be null-terminated.</span></span>  
  
 <span data-ttu-id="b6471-120">*desttype*</span><span class="sxs-lookup"><span data-stu-id="b6471-120">*desttype*</span></span>  
 <span data-ttu-id="b6471-121">指定目的地資料列資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6471-121">Specifies the data type of the destination row column.</span></span> <span data-ttu-id="b6471-122">這是傳送給用戶端的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6471-122">This is the data type sent to the client.</span></span> <span data-ttu-id="b6471-123">即使資料為 NULL 仍然必須指定資料類型。如需詳細資訊，請參閱[資料類型 &#40;擴充預存程序 API&#41;](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="b6471-123">The data type must be specified even if the data is NULL, for more information, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="b6471-124">*destlen*</span><span class="sxs-lookup"><span data-stu-id="b6471-124">*destlen*</span></span>  
 <span data-ttu-id="b6471-125">指定傳送給用戶端之資料的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="b6471-125">Specifies the length, in bytes, of the data to be sent to the client.</span></span> <span data-ttu-id="b6471-126">如果是不允許 null 值的固定長度資料類型，則會忽略 *destlen*。</span><span class="sxs-lookup"><span data-stu-id="b6471-126">For fixed-length data types that do not allow null values, *destlen* is ignored.</span></span> <span data-ttu-id="b6471-127">如果是允許 null 值的可變長度資料類型和固定長度資料類型，*destlen* 會指定目的地資料的可能最大長度。</span><span class="sxs-lookup"><span data-stu-id="b6471-127">For variable-length data types and fixed-length data types that allow null values, *destlen* specifies the maximum length the destination data can be.</span></span>  
  
 <span data-ttu-id="b6471-128">*srctype*</span><span class="sxs-lookup"><span data-stu-id="b6471-128">*srctype*</span></span>  
 <span data-ttu-id="b6471-129">指定來源資料的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b6471-129">Specifies the data type of the source data.</span></span>  
  
 <span data-ttu-id="b6471-130">*srclen*</span><span class="sxs-lookup"><span data-stu-id="b6471-130">*srclen*</span></span>  
 <span data-ttu-id="b6471-131">指定來源資料的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="b6471-131">Specifies the length, in bytes, of the source data.</span></span> <span data-ttu-id="b6471-132">固定長度的資料類型會忽略這個值。</span><span class="sxs-lookup"><span data-stu-id="b6471-132">This value is ignored for fixed-length data types.</span></span>  
  
 <span data-ttu-id="b6471-133">*srcdata*</span><span class="sxs-lookup"><span data-stu-id="b6471-133">*srcdata*</span></span>  
 <span data-ttu-id="b6471-134">提供特定資料行的來源資料位址。</span><span class="sxs-lookup"><span data-stu-id="b6471-134">Provides the source data address for a particular column.</span></span> <span data-ttu-id="b6471-135">當呼叫 **srv_sendrow** 時，它會在 *srcdata* 上尋找 *colnumber* 的資料。</span><span class="sxs-lookup"><span data-stu-id="b6471-135">When **srv_sendrow** is called, it looks for the data for *colnumber* at *srcdata*.</span></span> <span data-ttu-id="b6471-136">因此在呼叫 **srv_sendrow** 之前不應該將它釋放。</span><span class="sxs-lookup"><span data-stu-id="b6471-136">Therefore it should not be freed before a call to **srv_sendrow**.</span></span> <span data-ttu-id="b6471-137">在 **srv_sendrow** 的呼叫之間可以使用 **srv_setcoldata** 來變更來源資料位址。</span><span class="sxs-lookup"><span data-stu-id="b6471-137">The source data address can be changed between calls to **srv_sendrow** by using **srv_setcoldata**.</span></span> <span data-ttu-id="b6471-138">配置給 *srcdata* 的記憶體要等到另一個 **srv_setcoldata** 呼叫取代資料行資料或是呼叫 **srv_senddone** 之後，才能釋放。</span><span class="sxs-lookup"><span data-stu-id="b6471-138">Memory allocated for *srcdata* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
 <span data-ttu-id="b6471-139">如果 *desttype* 為 SRVDECIMAL 或 SRVNUMERIC，則 *srcdata* 參數必須是 DBNUMERIC 或 DBDECIMAL 結構的指標，而且此結構的有效位數及小數位數欄位已設定為您想要的值。</span><span class="sxs-lookup"><span data-stu-id="b6471-139">If *desttype* is SRVDECIMAL or SRVNUMERIC, the *srcdata* parameter must be a pointer to a DBNUMERIC or DBDECIMAL structure with the precision and scale fields of the structure already set to the values you want.</span></span> <span data-ttu-id="b6471-140">您可以使用 DEFAULTPRECISION 來指定預設有效位數，並使用 DEFAULTSCALE 來指定預設小數位數。</span><span class="sxs-lookup"><span data-stu-id="b6471-140">You can use DEFAULTPRECISION to specify a default precision, and DEFAULTSCALE to specify a default scale.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b6471-141">傳回</span><span class="sxs-lookup"><span data-stu-id="b6471-141">Returns</span></span>  
 <span data-ttu-id="b6471-142">所描述之資料行的編號。</span><span class="sxs-lookup"><span data-stu-id="b6471-142">The number of the column described.</span></span> <span data-ttu-id="b6471-143">第一個資料行為資料行 1。</span><span class="sxs-lookup"><span data-stu-id="b6471-143">The first column is column 1.</span></span> <span data-ttu-id="b6471-144">若發生錯誤，就會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="b6471-144">If an error occurs, returns 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6471-145">備註</span><span class="sxs-lookup"><span data-stu-id="b6471-145">Remarks</span></span>  
 <span data-ttu-id="b6471-146">在第一次呼叫 **srv_sendrow** 之前，必須針對資料列中的每一個資料行呼叫 **srv_describe** 函式一次。</span><span class="sxs-lookup"><span data-stu-id="b6471-146">The **srv_describe** function must be called once for each column in the row before the first call to **srv_sendrow**.</span></span> <span data-ttu-id="b6471-147">資料列的資料行可以依照任何順序來描述。</span><span class="sxs-lookup"><span data-stu-id="b6471-147">The columns of a row can be described in any order.</span></span>  
  
 <span data-ttu-id="b6471-148">若要在傳送完整結果集之前變更資料行資料列中來源資料的位置和長度，請分別使用 **srv_setcoldata** 和 **srv_setcollen**。</span><span class="sxs-lookup"><span data-stu-id="b6471-148">To change the location and length of the source data in column rows before the complete result set has been sent, use **srv_setcoldata** and **srv_setcollen**, respectively.</span></span>  
  
 <span data-ttu-id="b6471-149">如需資料類型及擴充預存程序 API 資料類型轉換的描述，請參閱[資料類型 &#40;擴充預存程序 API&#41;](data-types-extended-stored-procedure-api.md)。</span><span class="sxs-lookup"><span data-stu-id="b6471-149">For a description of data types and Extended Store Procedure API data type conversions, see[Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
 <span data-ttu-id="b6471-150">如果應用程式內的資料行名稱為 Unicode 格式，您需要將它轉換成伺服器的多位元組字碼頁，然後才能呼叫 **srv_describe**。</span><span class="sxs-lookup"><span data-stu-id="b6471-150">If the column name in your application is in Unicode, you need to convert it to the multibyte code page of the server before calling **srv_describe**.</span></span> <span data-ttu-id="b6471-151">如需詳細資訊，請參閱[Unicode 資料和伺服器字碼頁](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="b6471-151">For more information, see [Unicode Data and Server Code Pages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b6471-152">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b6471-152">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="b6471-153">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="b6471-153">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6471-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6471-154">See Also</span></span>  
 <span data-ttu-id="b6471-155">[srv_sendrow &#40;擴充預存程式 API&#41;](srv-sendrow-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="b6471-155">[srv_sendrow &#40;Extended Stored Procedure API&#41;](srv-sendrow-extended-stored-procedure-api.md) </span></span>  
 <span data-ttu-id="b6471-156">[srv_setutype &#40;擴充預存程式 API&#41;](srv-setutype-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="b6471-156">[srv_setutype &#40;Extended Stored Procedure API&#41;](srv-setutype-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="b6471-157">srv_setcoldata &#40;擴充預存程序 API&#41;</span><span class="sxs-lookup"><span data-stu-id="b6471-157">srv_setcoldata &#40;Extended Stored Procedure API&#41;</span></span>](srv-setcoldata-extended-stored-procedure-api.md)  
  
  
