---
title: LocalDBGetVersions 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersions
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 033a9c6b-0d7f-4f8a-ab60-33cd6fee0d33
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 37d2a927346252f1b126f5e3a4ec78ea03cde0a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708417"
---
# <a name="localdbgetversions-function"></a><span data-ttu-id="7f409-102">LocalDBGetVersions 函數</span><span class="sxs-lookup"><span data-stu-id="7f409-102">LocalDBGetVersions Function</span></span>
  <span data-ttu-id="7f409-103">傳回電腦上所有可用的 SQL Server Express LocalDB 版本。</span><span class="sxs-lookup"><span data-stu-id="7f409-103">Returns all SQL Server Express LocalDB versions available on the computer.</span></span>  
  
 <span data-ttu-id="7f409-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="7f409-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f409-105">語法</span><span class="sxs-lookup"><span data-stu-id="7f409-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_VERSION_LENGTH 43typedef WCHAR TLocalDBVersion[MAX_LOCALDB_VERSION_LENGTH + 1];typedef TLocalDBVersion* PTLocalDBVersion;HRESULT LocalDBGetVersions(           PTLocalDBVersion pVersion,           LPDWORD lpdwNumberOfVersions);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f409-106">參數</span><span class="sxs-lookup"><span data-stu-id="7f409-106">Parameters</span></span>  
 <span data-ttu-id="7f409-107">*pVersionNames*</span><span class="sxs-lookup"><span data-stu-id="7f409-107">*pVersionNames*</span></span>  
 <span data-ttu-id="7f409-108">輸出包含使用者工作站上可用的 LocalDB 版本名稱。</span><span class="sxs-lookup"><span data-stu-id="7f409-108">[Output] Contains names of the LocalDB versions that are available on the user's workstation.</span></span>  
  
 <span data-ttu-id="7f409-109">*lpdwNumberOfVersions*</span><span class="sxs-lookup"><span data-stu-id="7f409-109">*lpdwNumberOfVersions*</span></span>  
 <span data-ttu-id="7f409-110">[輸入/輸出]在輸入時，會保留*pVersionNames*緩衝區中版本的插槽數目。</span><span class="sxs-lookup"><span data-stu-id="7f409-110">[Input/Output] On input holds the number of slots for versions in the *pVersionNames* buffer.</span></span>   
<span data-ttu-id="7f409-111">在輸出時，保存現有 LocalDB 版本的數目。</span><span class="sxs-lookup"><span data-stu-id="7f409-111">On output, holds the number of existing LocalDB versions.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7f409-112">傳回</span><span class="sxs-lookup"><span data-stu-id="7f409-112">Returns</span></span>  
 <span data-ttu-id="7f409-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f409-113">S_OK</span></span>  
 <span data-ttu-id="7f409-114">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="7f409-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="7f409-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="7f409-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="7f409-116">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="7f409-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="7f409-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="7f409-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="7f409-118">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="7f409-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="7f409-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7f409-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="7f409-120">輸入緩衝區太短，且未要求截斷。</span><span class="sxs-lookup"><span data-stu-id="7f409-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="7f409-121">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="7f409-121">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="7f409-122">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f409-122">An unexpected error occurred.</span></span> <span data-ttu-id="7f409-123">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7f409-123">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f409-124">備註</span><span class="sxs-lookup"><span data-stu-id="7f409-124">Remarks</span></span>  
 <span data-ttu-id="7f409-125">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="7f409-125">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f409-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f409-126">See Also</span></span>  
 [<span data-ttu-id="7f409-127">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="7f409-127">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
