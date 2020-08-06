---
title: LocalDBStartInstance 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: cb325f5d-10ee-4a56-ba28-db0074ab3926
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 748bc373e8b0dbad0a91247e068d21b67f2dbc1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606327"
---
# <a name="localdbstartinstance-function"></a><span data-ttu-id="23481-102">LocalDBStartInstance 函數</span><span class="sxs-lookup"><span data-stu-id="23481-102">LocalDBStartInstance Function</span></span>
  <span data-ttu-id="23481-103">啟動指定的 SQL Server Express LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="23481-103">Starts the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="23481-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="23481-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23481-105">語法</span><span class="sxs-lookup"><span data-stu-id="23481-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartInstance(  
           PCWSTR pInstanceName,  
           DWORD dwFlags,   
           LPWSTR wszSqlConnection,   
           LPDWORD lpcchSqlConnection   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23481-106">參數</span><span class="sxs-lookup"><span data-stu-id="23481-106">Parameters</span></span>  
 <span data-ttu-id="23481-107">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="23481-107">*pInstanceName*</span></span>  
 <span data-ttu-id="23481-108">[輸入] 要啟動的 LocalDB 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="23481-108">[Input] The name of the LocalDB instance to start.</span></span>  
  
 <span data-ttu-id="23481-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="23481-109">*dwFlags*</span></span>  
 <span data-ttu-id="23481-110">[輸入] 保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="23481-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="23481-111">目前應設為 0。</span><span class="sxs-lookup"><span data-stu-id="23481-111">Currently should be set to 0.</span></span>  
  
 <span data-ttu-id="23481-112">*wszSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="23481-112">*wszSqlConnection*</span></span>  
 <span data-ttu-id="23481-113">[輸出] 儲存 LocalDB 執行個體連接字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="23481-113">[Output] The buffer to store the connection string to the LocalDB instance.</span></span>  
  
 <span data-ttu-id="23481-114">*lpcchSqlConnection*</span><span class="sxs-lookup"><span data-stu-id="23481-114">*lpcchSqlConnection*</span></span>  
 <span data-ttu-id="23481-115">[輸入/輸出][輸入] 包含*wszSqlConnection*緩衝區的大小（以字元為單位），包括任何尾端的 null。</span><span class="sxs-lookup"><span data-stu-id="23481-115">[Input/Output] On input contains the size of the *wszSqlConnection* buffer in characters, including any trailing nulls.</span></span> <span data-ttu-id="23481-116">輸出時，如果指定的緩衝區大小太小，則會包含所需的緩衝區大小 (以字元為單位)，包括尾端的 Null。</span><span class="sxs-lookup"><span data-stu-id="23481-116">On output, if the given buffer size is too small, contains the required buffer size in characters, including any trailing nulls.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="23481-117">傳回</span><span class="sxs-lookup"><span data-stu-id="23481-117">Returns</span></span>  
 <span data-ttu-id="23481-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="23481-118">S_OK</span></span>  
 <span data-ttu-id="23481-119">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="23481-119">The function succeeded.</span></span>  
  
 [<span data-ttu-id="23481-120">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="23481-120">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="23481-121">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="23481-121">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="23481-122">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="23481-122">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="23481-123">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="23481-123">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="23481-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="23481-124">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="23481-125">指定的執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="23481-125">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="23481-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="23481-126">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="23481-127">執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="23481-127">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="23481-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="23481-128">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="23481-129">指定的緩衝區*wszSqlConnection*太小。</span><span class="sxs-lookup"><span data-stu-id="23481-129">The specified buffer *wszSqlConnection* is too small.</span></span>  
  
 [<span data-ttu-id="23481-130">LOCALDB_ERROR_WAIT_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23481-130">LOCALDB_ERROR_WAIT_TIMEOUT</span></span>](../express-localdb-error-messages/localdb-error-wait-timeout.md)  
 <span data-ttu-id="23481-131">嘗試取得同步處理鎖定時發生逾時。</span><span class="sxs-lookup"><span data-stu-id="23481-131">A time-out occurred while trying to acquire the synchronization locks.</span></span>  
  
 [<span data-ttu-id="23481-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="23481-132">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="23481-133">應儲存執行個體的路徑長度超過 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="23481-133">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="23481-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="23481-134">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="23481-135">無法擷取使用者設定檔資料夾。</span><span class="sxs-lookup"><span data-stu-id="23481-135">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="23481-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="23481-136">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="23481-137">無法存取執行個體資料夾。</span><span class="sxs-lookup"><span data-stu-id="23481-137">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="23481-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="23481-138">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="23481-139">無法存取執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="23481-139">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="23481-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="23481-140">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="23481-141">無法修改執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="23481-141">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="23481-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span><span class="sxs-lookup"><span data-stu-id="23481-142">LOCALDB_ERROR_CANNOT_CREATE_SQL_PROCESS</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-sql-process.md)  
 <span data-ttu-id="23481-143">無法建立 SQL Server 處理序。</span><span class="sxs-lookup"><span data-stu-id="23481-143">A process for SQL Server cannot be created.</span></span>  
  
 [<span data-ttu-id="23481-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="23481-144">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="23481-145">已啟動 SQL Server 處理序，但是 SQL Server 啟動失敗。</span><span class="sxs-lookup"><span data-stu-id="23481-145">A SQL Server process was started, but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="23481-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="23481-146">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="23481-147">執行個體組態已損毀。</span><span class="sxs-lookup"><span data-stu-id="23481-147">An instance configuration was corrupted.</span></span>  
  
 [<span data-ttu-id="23481-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span><span class="sxs-lookup"><span data-stu-id="23481-148">LOCALDB_ERROR_AUTO_INSTANCE_CREATE_FAILED</span></span>](../express-localdb-error-messages/localdb-error-auto-instance-create-failed.md)  
 <span data-ttu-id="23481-149">無法建立自動執行個體。</span><span class="sxs-lookup"><span data-stu-id="23481-149">Cannot create an automatic instance.</span></span> <span data-ttu-id="23481-150">請參閱 Windows 應用程式事件記錄檔，以取得錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="23481-150">See the Windows Application event log for error details.</span></span>  
  
 [<span data-ttu-id="23481-151">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="23481-151">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="23481-152">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="23481-152">An unexpected error occurred.</span></span> <span data-ttu-id="23481-153">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="23481-153">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="23481-154">詳細資料</span><span class="sxs-lookup"><span data-stu-id="23481-154">Details</span></span>  
 <span data-ttu-id="23481-155">連接緩衝區引數 (*wszSqlConnection*) 和連接緩衝區大小引數 (*lpcchSqlConnection*) 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="23481-155">Both the connection buffer argument (*wszSqlConnection*) and the connection buffer size argument (*lpcchSqlConnection*) are optional.</span></span> <span data-ttu-id="23481-156">下表顯示使用這些引數的選項及其結果。</span><span class="sxs-lookup"><span data-stu-id="23481-156">The following table shows options for using these arguments and their results.</span></span>  
  
|<span data-ttu-id="23481-157">Buffer</span><span class="sxs-lookup"><span data-stu-id="23481-157">Buffer</span></span>|<span data-ttu-id="23481-158">緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="23481-158">Buffer size</span></span>|<span data-ttu-id="23481-159">基本原理</span><span class="sxs-lookup"><span data-stu-id="23481-159">Rationale</span></span>|<span data-ttu-id="23481-160">動作</span><span class="sxs-lookup"><span data-stu-id="23481-160">Action</span></span>|  
|------------|-----------------|---------------|------------|  
|<span data-ttu-id="23481-161">NULL</span><span class="sxs-lookup"><span data-stu-id="23481-161">NULL</span></span>|<span data-ttu-id="23481-162">NULL</span><span class="sxs-lookup"><span data-stu-id="23481-162">NULL</span></span>|<span data-ttu-id="23481-163">使用者想要啟動實例，而不需要管道名稱。</span><span class="sxs-lookup"><span data-stu-id="23481-163">User wants to start the instance and doesn't need a pipe name.</span></span>|<span data-ttu-id="23481-164">啟動執行個體 (不傳回管道且不傳回所需的緩衝區大小)。</span><span class="sxs-lookup"><span data-stu-id="23481-164">Starts an instance (no pipe return and no required buffer size return).</span></span>|  
|<span data-ttu-id="23481-165">NULL</span><span class="sxs-lookup"><span data-stu-id="23481-165">NULL</span></span>|<span data-ttu-id="23481-166">存在</span><span class="sxs-lookup"><span data-stu-id="23481-166">Present</span></span>|<span data-ttu-id="23481-167">使用者要求輸出緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="23481-167">User asks for the output buffer size.</span></span> <span data-ttu-id="23481-168">(在下一個呼叫中，使用者可能會要求實際啟動。)</span><span class="sxs-lookup"><span data-stu-id="23481-168">(In the next call the user will probably ask for an actual start.)</span></span>|<span data-ttu-id="23481-169">傳回所需的緩衝區大小 (不啟動且不傳回管道)。</span><span class="sxs-lookup"><span data-stu-id="23481-169">Returns a required buffer size (no start and no pipe return).</span></span> <span data-ttu-id="23481-170">結果為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="23481-170">Result is S_OK.</span></span>|  
|<span data-ttu-id="23481-171">存在</span><span class="sxs-lookup"><span data-stu-id="23481-171">Present</span></span>|<span data-ttu-id="23481-172">NULL</span><span class="sxs-lookup"><span data-stu-id="23481-172">NULL</span></span>|<span data-ttu-id="23481-173">不允許；輸入不正確。</span><span class="sxs-lookup"><span data-stu-id="23481-173">Not allowed; incorrect input.</span></span>|<span data-ttu-id="23481-174">傳回的結果為 LOCALDB_ERROR_INVALID_PARAMETER。</span><span class="sxs-lookup"><span data-stu-id="23481-174">Returned result is LOCALDB_ERROR_INVALID_PARAMETER.</span></span>|  
|<span data-ttu-id="23481-175">存在</span><span class="sxs-lookup"><span data-stu-id="23481-175">Present</span></span>|<span data-ttu-id="23481-176">存在</span><span class="sxs-lookup"><span data-stu-id="23481-176">Present</span></span>|<span data-ttu-id="23481-177">使用者想要啟動執行個體，且在啟動後，需要管道名稱以連接至此執行個體。</span><span class="sxs-lookup"><span data-stu-id="23481-177">User wants to start the instance and needs the pipe name to connect to it after it is started.</span></span>|<span data-ttu-id="23481-178">檢查緩衝區大小、啟動執行個體，然後傳回緩衝區中的管道名稱。</span><span class="sxs-lookup"><span data-stu-id="23481-178">Checks the buffer size, starts the instance, and returns the pipe name in the buffer.</span></span> <br /><span data-ttu-id="23481-179">緩衝區大小引數會傳回 "server =" 字串的長度，不包括終止的 null。</span><span class="sxs-lookup"><span data-stu-id="23481-179">The buffer size argument returns the length of the "server=" string, not including terminating nulls.</span></span>|  
  
 <span data-ttu-id="23481-180">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="23481-180">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23481-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23481-181">See Also</span></span>  
 [<span data-ttu-id="23481-182">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="23481-182">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
