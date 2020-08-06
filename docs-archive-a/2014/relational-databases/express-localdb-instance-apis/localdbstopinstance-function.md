---
title: LocalDBStopInstance 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 4bd73187-0aac-4f03-ac54-2b78e41917e5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 48b014e65e0a02a5f866e5301b12dae3cd255b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686933"
---
# <a name="localdbstopinstance-function"></a><span data-ttu-id="bc5b3-102">LocalDBStopInstance 函數</span><span class="sxs-lookup"><span data-stu-id="bc5b3-102">LocalDBStopInstance Function</span></span>
  <span data-ttu-id="bc5b3-103">停止執行指定的 SQL Server Express LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-103">Stops the specified SQL Server Express LocalDB instance from running.</span></span>  
  
 <span data-ttu-id="bc5b3-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="bc5b3-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc5b3-105">語法</span><span class="sxs-lookup"><span data-stu-id="bc5b3-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           ULONG ulTimeout   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc5b3-106">參數</span><span class="sxs-lookup"><span data-stu-id="bc5b3-106">Parameters</span></span>  
 <span data-ttu-id="bc5b3-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="bc5b3-107">*pInstanceName*</span></span>  
 <span data-ttu-id="bc5b3-108">[輸入] 要停止的 LocalDB 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-108">[Input] The name of the LocalDB instance to stop.</span></span>  
  
 <span data-ttu-id="bc5b3-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="bc5b3-109">*dwFlags*</span></span>  
 <span data-ttu-id="bc5b3-110">[輸入] 指定執行個體停止方式的一個或一組旗標值。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-110">[Input] One or a combination of the flag values specifying the way to stop the instance.</span></span>  
  
 <span data-ttu-id="bc5b3-111">可用的旗標：</span><span class="sxs-lookup"><span data-stu-id="bc5b3-111">Available flags:</span></span>  
  
 <span data-ttu-id="bc5b3-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="bc5b3-112">LOCALDB_SHUTDOWN_KILL_PROCESS</span></span>  
 <span data-ttu-id="bc5b3-113">使用終止處理序作業系統命令立即關閉。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-113">Shut down immediately using the kill process operating system command.</span></span>  
  
 <span data-ttu-id="bc5b3-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span><span class="sxs-lookup"><span data-stu-id="bc5b3-114">LOCALDB_SHUTDOWN_WITH_NOWAIT</span></span>  
 <span data-ttu-id="bc5b3-115">使用 WITH NOWAIT 選項 Transact-SQL 命令關閉。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-115">Shut down using the WITH NOWAIT option Transact-SQL command.</span></span>  
  
 <span data-ttu-id="bc5b3-116">如果未設定任何旗標，則會使用 SHUTDOWN Transact-SQL 命令關閉 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-116">If none of the flags is set, the LocalDB instance will be shut down using the SHUTDOWN Transact-SQL command.</span></span> <span data-ttu-id="bc5b3-117">如果設定了這兩個旗標，則會優先使用 LOCALDB_SHUTDOWN_KILL_PROCESS 旗標。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-117">If both flags are set, the LOCALDB_SHUTDOWN_KILL_PROCESS flag takes precedence.</span></span>  
  
 <span data-ttu-id="bc5b3-118">*ulTimeout*</span><span class="sxs-lookup"><span data-stu-id="bc5b3-118">*ulTimeout*</span></span>  
 <span data-ttu-id="bc5b3-119">[輸入] 等候此作業完成的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-119">[Input] The time in seconds to wait for this operation to complete.</span></span> <span data-ttu-id="bc5b3-120">如果此值為 0，此函數會立即傳回，而不等候 LocalDB 執行個體停止。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-120">If this value is 0, this function will return immediately without waiting for the LocalDB instance to stop.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="bc5b3-121">傳回</span><span class="sxs-lookup"><span data-stu-id="bc5b3-121">Returns</span></span>  
 <span data-ttu-id="bc5b3-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc5b3-122">S_OK</span></span>  
 <span data-ttu-id="bc5b3-123">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-123">The function succeeded.</span></span>  
  
 [<span data-ttu-id="bc5b3-124">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="bc5b3-124">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="bc5b3-125">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-125">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="bc5b3-126">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="bc5b3-126">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="bc5b3-127">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-127">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="bc5b3-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="bc5b3-128">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="bc5b3-129">指定的執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-129">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="bc5b3-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="bc5b3-130">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="bc5b3-131">執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-131">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="bc5b3-132">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc5b3-132">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="bc5b3-133">嘗試取得同步處理鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-133">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="bc5b3-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span><span class="sxs-lookup"><span data-stu-id="bc5b3-134">LOCALDB_ERROR_INSTANCE_STOP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-instance-stop-failed.md)  
 <span data-ttu-id="bc5b3-135">停止作業無法在指定時間內完成。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-135">The stop operation failed to complete within the given time.</span></span>  
  
 [<span data-ttu-id="bc5b3-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="bc5b3-136">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="bc5b3-137">應儲存執行個體的路徑長度超過 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-137">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="bc5b3-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="bc5b3-138">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="bc5b3-139">無法擷取使用者設定檔資料夾。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-139">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="bc5b3-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="bc5b3-140">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="bc5b3-141">無法存取執行個體資料夾。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-141">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="bc5b3-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="bc5b3-142">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="bc5b3-143">無法存取執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-143">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="bc5b3-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="bc5b3-144">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="bc5b3-145">執行個體組態已損毀。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-145">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="bc5b3-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc5b3-146">LOCALDB_ERROR_CALLER_IS_NOT_OWNER</span></span>](../express-localdb-error-messages/localdb-error-caller-is-not-owner.md)  
 <span data-ttu-id="bc5b3-147">API 呼叫端不是 LocalDB 執行個體擁有者。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-147">API caller is not LocalDB instance owner.</span></span>  
  
 [<span data-ttu-id="bc5b3-148">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="bc5b3-148">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="bc5b3-149">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-149">An unexpected error occurred.</span></span> <span data-ttu-id="bc5b3-150">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-150">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc5b3-151">備註</span><span class="sxs-lookup"><span data-stu-id="bc5b3-151">Remarks</span></span>  
 <span data-ttu-id="bc5b3-152">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="bc5b3-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc5b3-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc5b3-153">See Also</span></span>  
 [<span data-ttu-id="bc5b3-154">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="bc5b3-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
