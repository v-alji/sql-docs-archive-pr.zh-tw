---
title: LocalDBCreateInstance 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBCreateInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 3eebb485-8a53-4a79-82a9-57b8de9f8e84
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ff822c552176ad8c083a1c8ea6c0f2430f72972f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598411"
---
# <a name="localdbcreateinstance-function"></a><span data-ttu-id="faf95-102">LocalDBCreateInstance 函數</span><span class="sxs-lookup"><span data-stu-id="faf95-102">LocalDBCreateInstance Function</span></span>
  <span data-ttu-id="faf95-103">建立新的 SQL Server Express LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="faf95-103">Creates a new SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="faf95-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="faf95-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf95-105">語法</span><span class="sxs-lookup"><span data-stu-id="faf95-105">Syntax</span></span>  
  
```  
HRESULT LocalDBCreateInstance(  
           PCWSTR wszVersion,  
           PCWSTR pInstanceName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faf95-106">參數</span><span class="sxs-lookup"><span data-stu-id="faf95-106">Parameters</span></span>  
 <span data-ttu-id="faf95-107">*wszVersion*</span><span class="sxs-lookup"><span data-stu-id="faf95-107">*wszVersion*</span></span>  
 <span data-ttu-id="faf95-108">[輸入] LocalDB 版本，例如 11.0 或 11.0.1094.2。</span><span class="sxs-lookup"><span data-stu-id="faf95-108">[Input] The LocalDB version, for example 11.0 or 11.0.1094.2.</span></span>  
  
 <span data-ttu-id="faf95-109">*pInstanceName*</span><span class="sxs-lookup"><span data-stu-id="faf95-109">*pInstanceName*</span></span>  
 <span data-ttu-id="faf95-110">[輸入] 要建立的 LocalDB 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="faf95-110">[Input] The name for the LocalDB instance to create.</span></span>  
  
 <span data-ttu-id="faf95-111">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="faf95-111">*dwFlags*</span></span>  
 <span data-ttu-id="faf95-112">[輸入] 保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="faf95-112">[Input] Reserved for future use.</span></span> <span data-ttu-id="faf95-113">目前應設為 0。</span><span class="sxs-lookup"><span data-stu-id="faf95-113">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="faf95-114">傳回</span><span class="sxs-lookup"><span data-stu-id="faf95-114">Returns</span></span>  
 <span data-ttu-id="faf95-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="faf95-115">S_OK</span></span>  
 <span data-ttu-id="faf95-116">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="faf95-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="faf95-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="faf95-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="faf95-118">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="faf95-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="faf95-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="faf95-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="faf95-120">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="faf95-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="faf95-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="faf95-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="faf95-122">指定的執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="faf95-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="faf95-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="faf95-123">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="faf95-124">應儲存執行個體的路徑長度超過 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="faf95-124">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="faf95-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span><span class="sxs-lookup"><span data-stu-id="faf95-125">LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION</span></span>](../express-localdb-error-messages/localdb-error-instance-exists-with-lower-version.md)  
 <span data-ttu-id="faf95-126">指定的執行個體已經存在，但是其版本低於要求的版本。</span><span class="sxs-lookup"><span data-stu-id="faf95-126">The specified instance already exists but its version is lower than requested.</span></span>  
  
 [<span data-ttu-id="faf95-127">LOCALDB_ERROR_UNKNOWN_VERSION</span><span class="sxs-lookup"><span data-stu-id="faf95-127">LOCALDB_ERROR_UNKNOWN_VERSION</span></span>](../express-localdb-error-messages/localdb-error-unknown-version.md)  
 <span data-ttu-id="faf95-128">沒有指定的版本。</span><span class="sxs-lookup"><span data-stu-id="faf95-128">The specified version is not available.</span></span>  
  
 [<span data-ttu-id="faf95-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="faf95-129">LOCALDB_ERROR_VERSION_REQUESTED_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-version-requested-not-installed.md)  
 <span data-ttu-id="faf95-130">未安裝指定的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="faf95-130">The specified patch level is not installed.</span></span>  
  
 [<span data-ttu-id="faf95-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="faf95-131">LOCALDB_ERROR_CANNOT_CREATE_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-create-instance-folder.md)  
 <span data-ttu-id="faf95-132">無法在 %userprofile% 下建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="faf95-132">A folder cannot be created under %userprofile%.</span></span>  
  
 [<span data-ttu-id="faf95-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="faf95-133">LOCALDB_ERROR_CANNOT_GET_USER_PROFILE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-get-user-profile-folder.md)  
 <span data-ttu-id="faf95-134">無法擷取使用者設定檔資料夾。</span><span class="sxs-lookup"><span data-stu-id="faf95-134">A user profile folder cannot be retrieved.</span></span>  
  
 [<span data-ttu-id="faf95-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="faf95-135">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="faf95-136">無法存取執行個體資料夾。</span><span class="sxs-lookup"><span data-stu-id="faf95-136">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="faf95-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="faf95-137">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="faf95-138">無法存取執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="faf95-138">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="faf95-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="faf95-139">LOCALDB_ERROR_CANNOT_MODIFY_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-modify-instance-registry.md)  
 <span data-ttu-id="faf95-140">無法修改執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="faf95-140">An instance registry cannot be modified.</span></span>  
  
 [<span data-ttu-id="faf95-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span><span class="sxs-lookup"><span data-stu-id="faf95-141">LOCALDB_ERROR_SQL_SERVER_STARTUP_FAILED</span></span>](../express-localdb-error-messages/localdb-error-sql-server-startup-failed.md)  
 <span data-ttu-id="faf95-142">已啟動 SQL Server 處理序，但是 SQL Server 啟動失敗。</span><span class="sxs-lookup"><span data-stu-id="faf95-142">A SQL Server process is started but SQL Server startup failed.</span></span>  
  
 [<span data-ttu-id="faf95-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="faf95-143">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="faf95-144">執行個體組態已損毀。</span><span class="sxs-lookup"><span data-stu-id="faf95-144">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="faf95-145">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="faf95-145">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="faf95-146">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="faf95-146">An unexpected error occurred.</span></span> <span data-ttu-id="faf95-147">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="faf95-147">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faf95-148">備註</span><span class="sxs-lookup"><span data-stu-id="faf95-148">Remarks</span></span>  
 <span data-ttu-id="faf95-149">如果具有指定名稱且完整運作的 LocalDB 執行個體已經存在，且其版本等於或高於要求的版本，則結果為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="faf95-149">If a fully functional LocalDB instance with the specified name already exists and its version is equal to or higher than requested, the result is S_OK.</span></span>  
  
 <span data-ttu-id="faf95-150">如果現有的執行個體損毀，`LocalDBCreateInstance` API 方法的後續呼叫會失敗。</span><span class="sxs-lookup"><span data-stu-id="faf95-150">In cases when an existing instance becomes corrupted, subsequent calls to the `LocalDBCreateInstance` API method will fail.</span></span> <span data-ttu-id="faf95-151">您必須手動修復或明確刪除已損毀的執行個體，才可以再次使用這些執行個體。</span><span class="sxs-lookup"><span data-stu-id="faf95-151">Corrupted instances must be fixed manually or explicitly deleted before they can be used again.</span></span>  
  
 <span data-ttu-id="faf95-152">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="faf95-152">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf95-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faf95-153">See Also</span></span>  
 [<span data-ttu-id="faf95-154">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="faf95-154">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
