---
title: LocalDBFormatMessage 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBFormatMessage
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 31b3152a-94cf-4f75-a31b-296d7dd16dbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ece28f19e3488fae248bf26c3a54a018ba6efd0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710622"
---
# <a name="localdbformatmessage-function"></a><span data-ttu-id="3dab2-102">LocalDBFormatMessage 函數</span><span class="sxs-lookup"><span data-stu-id="3dab2-102">LocalDBFormatMessage Function</span></span>
  <span data-ttu-id="3dab2-103">傳回指定之 SQL Server Express LocalDB 錯誤的當地語系化文字描述。</span><span class="sxs-lookup"><span data-stu-id="3dab2-103">Returns the localized textual description for the specified SQL Server Express LocalDB error.</span></span>  
  
 <span data-ttu-id="3dab2-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="3dab2-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dab2-105">語法</span><span class="sxs-lookup"><span data-stu-id="3dab2-105">Syntax</span></span>  
  
```  
HRESULT LocalDBFormatMessage(  
           HRESULT hrLocalDB,  
           DWORD dwFlags,   
           DWORD dwLanguageId,   
           LPWSTR wszMessage,   
           LPDWORD lpcchMessage   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dab2-106">參數</span><span class="sxs-lookup"><span data-stu-id="3dab2-106">Parameters</span></span>  
 <span data-ttu-id="3dab2-107">*hrLocalDB*</span><span class="sxs-lookup"><span data-stu-id="3dab2-107">*hrLocalDB*</span></span>  
 <span data-ttu-id="3dab2-108">[輸入] LocalDB 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3dab2-108">[Input] The LocalDB error code.</span></span>  
  
 <span data-ttu-id="3dab2-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="3dab2-109">*dwFlags*</span></span>  
 <span data-ttu-id="3dab2-110">[輸入] 指定此函數行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="3dab2-110">[Input] The flags specifying the behavior of this function.</span></span>  
  
 <span data-ttu-id="3dab2-111">可用的旗標：</span><span class="sxs-lookup"><span data-stu-id="3dab2-111">Available flags:</span></span>  
  
 <span data-ttu-id="3dab2-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span><span class="sxs-lookup"><span data-stu-id="3dab2-112">LOCALDB_TRUNCATE_ERR_MESSAGE</span></span>  
 <span data-ttu-id="3dab2-113">如果輸入緩衝區太短，則會截斷錯誤訊息以符合緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3dab2-113">If the input buffer is too short, the error message will be truncated to fit the buffer.</span></span>  
  
 <span data-ttu-id="3dab2-114">*dwLanguageId*</span><span class="sxs-lookup"><span data-stu-id="3dab2-114">*dwLanguageId*</span></span>  
 <span data-ttu-id="3dab2-115">[輸入] 所需語言 (LANGID) 或 0，在任何情況下都會使用 Win32 FormatMessage 語言順序。</span><span class="sxs-lookup"><span data-stu-id="3dab2-115">[Input] The language desired (LANGID) or 0, in which case the Win32 FormatMessage language order is used.</span></span>  
  
 <span data-ttu-id="3dab2-116">*wszMessage*</span><span class="sxs-lookup"><span data-stu-id="3dab2-116">*wszMessage*</span></span>  
 <span data-ttu-id="3dab2-117">[輸出] 儲存 LocalDB 錯誤訊息的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3dab2-117">[Output] The buffer to store the LocalDB error message.</span></span>  
  
 <span data-ttu-id="3dab2-118">*lpcchMessage*</span><span class="sxs-lookup"><span data-stu-id="3dab2-118">*lpcchMessage*</span></span>  
 <span data-ttu-id="3dab2-119">[輸入/輸出][輸入] 包含*wszMessage*緩衝區的大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="3dab2-119">[Input/Output] On input contains the size of the *wszMessage* buffer in characters.</span></span> <span data-ttu-id="3dab2-120">輸出時，如果指定的緩衝區大小太小，則會包含所需的緩衝區大小 (以字元為單位)，包括尾端的 Null。</span><span class="sxs-lookup"><span data-stu-id="3dab2-120">On output, if the given buffer size is too small, contains the buffer size required in characters, including any trailing nulls.</span></span> <span data-ttu-id="3dab2-121">如果函數成功，則會在訊息中包含字元數，尾端的 Null 不計。</span><span class="sxs-lookup"><span data-stu-id="3dab2-121">If the function succeeds, contains the number of characters in the message, excluding any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="3dab2-122">傳回</span><span class="sxs-lookup"><span data-stu-id="3dab2-122">Returns</span></span>  
 <span data-ttu-id="3dab2-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="3dab2-123">S_OK</span></span>  
 <span data-ttu-id="3dab2-124">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="3dab2-124">The function succeeded.</span></span>  
  
 [<span data-ttu-id="3dab2-125">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="3dab2-125">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="3dab2-126">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="3dab2-126">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="3dab2-127">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="3dab2-127">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="3dab2-128">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="3dab2-128">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="3dab2-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span><span class="sxs-lookup"><span data-stu-id="3dab2-129">LOCALDB_ERROR_UNKNOWN_ERROR_CODE</span></span>](../express-localdb-error-messages/localdb-error-unknown-error-code.md)  
 <span data-ttu-id="3dab2-130">要求的訊息不存在。</span><span class="sxs-lookup"><span data-stu-id="3dab2-130">The requested message does not exist.</span></span>  
  
 [<span data-ttu-id="3dab2-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span><span class="sxs-lookup"><span data-stu-id="3dab2-131">LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID</span></span>](../express-localdb-error-messages/localdb-error-unknown-language-id.md)  
 <span data-ttu-id="3dab2-132">未提供要求語言的訊息。</span><span class="sxs-lookup"><span data-stu-id="3dab2-132">The message is not available in the requested language.</span></span>  
  
 [<span data-ttu-id="3dab2-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3dab2-133">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="3dab2-134">輸入緩衝區*wszMessage*太短，且未要求截斷。</span><span class="sxs-lookup"><span data-stu-id="3dab2-134">The input buffer *wszMessage* is too short, and truncation is not requested.</span></span>  
  
 [<span data-ttu-id="3dab2-135">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="3dab2-135">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="3dab2-136">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="3dab2-136">An unexpected error occurred.</span></span> <span data-ttu-id="3dab2-137">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3dab2-137">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dab2-138">備註</span><span class="sxs-lookup"><span data-stu-id="3dab2-138">Remarks</span></span>  
 <span data-ttu-id="3dab2-139">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="3dab2-139">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dab2-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dab2-140">See Also</span></span>  
 [<span data-ttu-id="3dab2-141">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="3dab2-141">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
