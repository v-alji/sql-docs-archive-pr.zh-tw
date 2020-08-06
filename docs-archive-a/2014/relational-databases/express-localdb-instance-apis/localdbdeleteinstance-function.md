---
title: LocalDBDeleteInstance 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBDeleteInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 37cb2a7e-672a-4223-b6f3-a94d7b8d58cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8d4c873e045c5effed476ca9d147270d159ec3b2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598406"
---
# <a name="localdbdeleteinstance-function"></a><span data-ttu-id="d1f97-102">LocalDBDeleteInstance 函數</span><span class="sxs-lookup"><span data-stu-id="d1f97-102">LocalDBDeleteInstance Function</span></span>
  <span data-ttu-id="d1f97-103">移除指定的 SQL Server Express LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f97-103">Removes the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="d1f97-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="d1f97-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f97-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1f97-105">Syntax</span></span>  
  
```  
HRESULT LocalDBDeleteInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1f97-106">參數</span><span class="sxs-lookup"><span data-stu-id="d1f97-106">Parameters</span></span>  
 <span data-ttu-id="d1f97-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="d1f97-107">*pInstanceName*</span></span>  
 <span data-ttu-id="d1f97-108">[輸入] 要移除的 LocalDB 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="d1f97-108">[Input] The name of the LocalDB instance to remove.</span></span>  
  
 <span data-ttu-id="d1f97-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="d1f97-109">*dwFlags*</span></span>  
 <span data-ttu-id="d1f97-110">[輸入] 保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="d1f97-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="d1f97-111">目前應設為 0。</span><span class="sxs-lookup"><span data-stu-id="d1f97-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="d1f97-112">傳回</span><span class="sxs-lookup"><span data-stu-id="d1f97-112">Returns</span></span>  
 <span data-ttu-id="d1f97-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1f97-113">S_OK</span></span>  
 <span data-ttu-id="d1f97-114">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="d1f97-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="d1f97-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="d1f97-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="d1f97-116">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="d1f97-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="d1f97-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="d1f97-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="d1f97-118">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="d1f97-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="d1f97-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="d1f97-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="d1f97-120">指定的執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="d1f97-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="d1f97-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="d1f97-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="d1f97-122">指定的執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="d1f97-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="d1f97-123">LOCALDB_ERROR_INSTANCE_BUSY</span><span class="sxs-lookup"><span data-stu-id="d1f97-123">LOCALDB_ERROR_INSTANCE_BUSY</span></span>](../express-localdb-error-messages/localdb-error-instance-busy.md)  
 <span data-ttu-id="d1f97-124">指定的執行個體正在執行。</span><span class="sxs-lookup"><span data-stu-id="d1f97-124">The specified instance is running.</span></span>  
  
 [<span data-ttu-id="d1f97-125">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1f97-125">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="d1f97-126">嘗試取得同步處理鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="d1f97-126">A time-out occurred while trying to acquire synchronization locks.</span></span>  
  
 [<span data-ttu-id="d1f97-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="d1f97-127">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="d1f97-128">應儲存執行個體的路徑長度超過 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="d1f97-128">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="d1f97-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="d1f97-129">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="d1f97-130">無法擷取使用者設定檔資料夾。</span><span class="sxs-lookup"><span data-stu-id="d1f97-130">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="d1f97-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="d1f97-131">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="d1f97-132">無法存取執行個體資料夾。</span><span class="sxs-lookup"><span data-stu-id="d1f97-132">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="d1f97-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="d1f97-133">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="d1f97-134">無法存取執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="d1f97-134">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="d1f97-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="d1f97-135">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="d1f97-136">無法修改執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="d1f97-136">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="d1f97-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="d1f97-137">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="d1f97-138">執行個體組態已損毀。</span><span class="sxs-lookup"><span data-stu-id="d1f97-138">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="d1f97-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1f97-139">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="d1f97-140">API 呼叫端不是本機資料庫執行個體擁有者。</span><span class="sxs-lookup"><span data-stu-id="d1f97-140">API caller is not Local Database instance owner.</span></span>  
  
 [<span data-ttu-id="d1f97-141">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="d1f97-141">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="d1f97-142">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="d1f97-142">An unexpected error occurred.</span></span> <span data-ttu-id="d1f97-143">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d1f97-143">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1f97-144">備註</span><span class="sxs-lookup"><span data-stu-id="d1f97-144">Remarks</span></span>  
 <span data-ttu-id="d1f97-145">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="d1f97-145">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f97-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1f97-146">See Also</span></span>  
 [<span data-ttu-id="d1f97-147">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="d1f97-147">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
