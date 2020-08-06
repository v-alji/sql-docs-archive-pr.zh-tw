---
title: LocalDBGetVersionInfo 函式 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetVersionInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e30bb4dcd4c258db899883f650dbfe7100171ef8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709509"
---
# <a name="localdbgetversioninfo-function"></a><span data-ttu-id="16032-102">LocalDBGetVersionInfo 函數</span><span class="sxs-lookup"><span data-stu-id="16032-102">LocalDBGetVersionInfo Function</span></span>
  <span data-ttu-id="16032-103">傳回指定之 SQL Server Express LocalDB 版本的資訊，例如此版本是否存在，以及完整的 LocalDB 版本號碼 (包括組建和發行版本號碼)。</span><span class="sxs-lookup"><span data-stu-id="16032-103">Returns information for the specified SQL Server Express LocalDB version, such as whether it exists and the full LocalDB version number (including build and release numbers).</span></span>  
  
 <span data-ttu-id="16032-104">此資訊會以 `struct` 名為**LocalDBVersionInfo**的形式傳回，其具有下列定義。</span><span class="sxs-lookup"><span data-stu-id="16032-104">The information is returned in the form of a `struct` named **LocalDBVersionInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 <span data-ttu-id="16032-105">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="16032-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16032-106">語法</span><span class="sxs-lookup"><span data-stu-id="16032-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16032-107">參數</span><span class="sxs-lookup"><span data-stu-id="16032-107">Parameters</span></span>  
 <span data-ttu-id="16032-108">*wszVersionName*</span><span class="sxs-lookup"><span data-stu-id="16032-108">*wszVersionName*</span></span>  
 <span data-ttu-id="16032-109">[輸入] LocalDB 版本名稱。</span><span class="sxs-lookup"><span data-stu-id="16032-109">[Input] The LocalDB version name.</span></span>  
  
 <span data-ttu-id="16032-110">*pVersionInfo*</span><span class="sxs-lookup"><span data-stu-id="16032-110">*pVersionInfo*</span></span>  
 <span data-ttu-id="16032-111">[輸出] 儲存 LocalDB 版本資訊的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="16032-111">[Output] The buffer to store the information about the LocalDB version.</span></span>  
  
 <span data-ttu-id="16032-112">*dwVersionInfoSize*</span><span class="sxs-lookup"><span data-stu-id="16032-112">*dwVersionInfoSize*</span></span>  
 <span data-ttu-id="16032-113">源保留*VersionInfo*緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="16032-113">[Input] Holds the size of the *VersionInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="16032-114">傳回</span><span class="sxs-lookup"><span data-stu-id="16032-114">Returns</span></span>  
 <span data-ttu-id="16032-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="16032-115">S_OK</span></span>  
 <span data-ttu-id="16032-116">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="16032-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="16032-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="16032-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="16032-118">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="16032-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="16032-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="16032-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="16032-120">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="16032-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="16032-121">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="16032-121">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="16032-122">指定的 LocalDB 版本不存在。</span><span class="sxs-lookup"><span data-stu-id="16032-122">The specified LocalDB version does not exist.</span></span>  
  
 [<span data-ttu-id="16032-123">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="16032-123">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="16032-124">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="16032-124">An unexpected error occurred.</span></span> <span data-ttu-id="16032-125">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="16032-125">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16032-126">詳細資料</span><span class="sxs-lookup"><span data-stu-id="16032-126">Details</span></span>  
 <span data-ttu-id="16032-127">`struct` (*lpVersionInfoSize*) 引進大小引數背後的原理，是要讓 API 傳回不同版本的**LocalDBVersionInfostruct**，有效地啟用向前和向後相容性。</span><span class="sxs-lookup"><span data-stu-id="16032-127">The rationale behind the introduction of the `struct` size argument (*lpVersionInfoSize*) is to enable the API to return different versions of the **LocalDBVersionInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="16032-128">如果 `struct` 大小引數 (*LpVersionInfoSize*) 符合已知的**LocalDBVersionInfostruct**版本大小， `struct` 則會傳回該版本的。</span><span class="sxs-lookup"><span data-stu-id="16032-128">If the `struct` size argument (*lpVersionInfoSize*) matches the size of a known version of the **LocalDBVersionInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="16032-129">否則會傳回 LOCALDB_ERROR_INVALID_PARAMETER。</span><span class="sxs-lookup"><span data-stu-id="16032-129">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="16032-130">**LocalDBGetVersionInfo** API 使用方式的典型範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="16032-130">A typical example of **LocalDBGetVersionInfo** API usage looks like this:</span></span>  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a><span data-ttu-id="16032-131">備註</span><span class="sxs-lookup"><span data-stu-id="16032-131">Remarks</span></span>  
 <span data-ttu-id="16032-132">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="16032-132">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16032-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16032-133">See Also</span></span>  
 [<span data-ttu-id="16032-134">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="16032-134">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
