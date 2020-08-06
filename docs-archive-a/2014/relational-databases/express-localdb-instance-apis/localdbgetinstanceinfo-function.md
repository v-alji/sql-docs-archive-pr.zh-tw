---
title: LocalDBGetInstanceInfo 函式 |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstanceInfo
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 231706f5-26c6-42eb-ab47-315df6b8f824
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dc7cbe2c59a7502a1fd0c8b4f92fb14e5defd50b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593400"
---
# <a name="localdbgetinstanceinfo-function"></a><span data-ttu-id="078db-102">LocalDBGetInstanceInfo 函數</span><span class="sxs-lookup"><span data-stu-id="078db-102">LocalDBGetInstanceInfo Function</span></span>
  <span data-ttu-id="078db-103">傳回指定之 SQL Server Express LocalDB 執行個體的資訊，例如執行個體是否存在、執行個體使用的 LocalDB 版本、執行個體是否正在執行等等。</span><span class="sxs-lookup"><span data-stu-id="078db-103">Returns information for the specified SQL Server Express LocalDB instance, such as whether it exists, the LocalDB version it uses, whether it is running, and so on.</span></span>  
  
 <span data-ttu-id="078db-104">此資訊會在 `struct` 名為的**LocalDBInstanceInfo**中傳回，其具有下列定義。</span><span class="sxs-lookup"><span data-stu-id="078db-104">The information is returned in a `struct` named **LocalDBInstanceInfo**, which has the following definition.</span></span>  
  
```  
typedef struct _LocalDBInstanceInfo  
{  
      // Contains the size of the LocalDBInstanceInfo struct  
      DWORD  cbLocalDBInstanceInfoSize;  
  
      // Holds the instance name  
      TLocalDBInstanceNamewszInstanceName;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // TRUE if the instance configuration registry is corrupted, FALSE otherwise  
      BOOLbConfigurationCorrupted;  
  
      // TRUE if the instance is running at the moment, FALSE otherwise  
      BOOL   bIsRunning;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
  
      // Holds the date and time when the instance was started for the last time  
      FILETIME ftLastStartUTC;  
  
      // Holds the name of the TDS named pipe to connect to the instance  
      WCHARwszConnection;  
  
      // TRUE if the instance is shared, FALSE otherwise  
      BOOLbIsShared;  
  
      // Holds the shared name for the instance (if the instance is shared)  
      TLocalDBInstanceNamewszSharedInstanceName;  
  
      // Holds the SID of the instance owner (if the instance is shared)  
      WCHARwszOwnerSID;   
  
      // TRUE if the instance is Automatic, FALSE otherwise  
      BOOLbIsAutomatic;  
} LocalDBInstanceInfo;  
  
```  
  
 <span data-ttu-id="078db-105">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="078db-105">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="078db-106">語法</span><span class="sxs-lookup"><span data-stu-id="078db-106">Syntax</span></span>  
  
```  
HRESULT LocalDBGetInstanceInfo(  
           PCWSTR wszInstanceName,  
           PLocalDBInstanceInfo pInstanceInfo,  
           DWORD dwInstanceInfoSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="078db-107">參數</span><span class="sxs-lookup"><span data-stu-id="078db-107">Parameters</span></span>  
 <span data-ttu-id="078db-108">*wszInstanceName*</span><span class="sxs-lookup"><span data-stu-id="078db-108">*wszInstanceName*</span></span>  
 <span data-ttu-id="078db-109">[輸入] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="078db-109">[Input] The instance name.</span></span>  
  
 <span data-ttu-id="078db-110">*pInstanceInfo*</span><span class="sxs-lookup"><span data-stu-id="078db-110">*pInstanceInfo*</span></span>  
 <span data-ttu-id="078db-111">[輸出] 儲存 LocalDB 執行個體資訊的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="078db-111">[Output] The buffer to store the information about the LocalDB instance.</span></span>  
  
 <span data-ttu-id="078db-112">*dwInstanceInfoSize*</span><span class="sxs-lookup"><span data-stu-id="078db-112">*dwInstanceInfoSize*</span></span>  
 <span data-ttu-id="078db-113">源保留*InstanceInfo*緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="078db-113">[Input] Holds the size of the *InstanceInfo* buffer.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="078db-114">傳回</span><span class="sxs-lookup"><span data-stu-id="078db-114">Returns</span></span>  
 <span data-ttu-id="078db-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="078db-115">S_OK</span></span>  
 <span data-ttu-id="078db-116">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="078db-116">The function succeeded.</span></span>  
  
 [<span data-ttu-id="078db-117">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="078db-117">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="078db-118">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="078db-118">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="078db-119">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="078db-119">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="078db-120">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="078db-120">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="078db-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="078db-121">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="078db-122">指定的執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="078db-122">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="078db-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="078db-123">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="078db-124">執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="078db-124">The instance does not exist.</span></span>  
  
 [<span data-ttu-id="078db-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="078db-125">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="078db-126">應儲存執行個體的路徑長度超過 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="078db-126">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="078db-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span><span class="sxs-lookup"><span data-stu-id="078db-127">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 <span data-ttu-id="078db-128">無法存取執行個體資料夾。</span><span class="sxs-lookup"><span data-stu-id="078db-128">An instance folder cannot be accessed.</span></span>  
  
 [<span data-ttu-id="078db-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="078db-129">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="078db-130">無法存取執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="078db-130">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="078db-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="078db-131">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="078db-132">執行個體組態已損毀。</span><span class="sxs-lookup"><span data-stu-id="078db-132">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="078db-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="078db-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="078db-134">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="078db-134">An unexpected error occurred.</span></span> <span data-ttu-id="078db-135">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="078db-135">See the event log for details.</span></span>  
  
## <a name="details"></a><span data-ttu-id="078db-136">詳細資料</span><span class="sxs-lookup"><span data-stu-id="078db-136">Details</span></span>  
 <span data-ttu-id="078db-137">`struct` (*lpInstanceInfoSize*) 引進大小引數背後的原理，是要讓 API 傳回不同版本的**LocalDBInstanceInfostruct**，有效地啟用向前和向後相容性。</span><span class="sxs-lookup"><span data-stu-id="078db-137">The rationale behind the introduction of the `struct` size argument (*lpInstanceInfoSize*) is to enable the API to return different versions of the **LocalDBInstanceInfostruct**, effectively enabling forward and backward compatibility.</span></span>  
  
 <span data-ttu-id="078db-138">如果 `struct` 大小引數 (*LpInstanceInfoSize*) 符合已知的**LocalDBInstanceInfostruct**版本大小， `struct` 則會傳回該版本的。</span><span class="sxs-lookup"><span data-stu-id="078db-138">If the `struct` size argument (*lpInstanceInfoSize*) matches the size of a known version of the **LocalDBInstanceInfostruct**, that version of the `struct` is returned.</span></span> <span data-ttu-id="078db-139">否則會傳回 LOCALDB_ERROR_INVALID_PARAMETER。</span><span class="sxs-lookup"><span data-stu-id="078db-139">Otherwise, LOCALDB_ERROR_INVALID_PARAMETER is returned.</span></span>  
  
 <span data-ttu-id="078db-140">**LocalDBGetInstanceInfo** API 使用方式的典型範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="078db-140">A typical example of **LocalDBGetInstanceInfo** API usage looks like this:</span></span>  
  
```  
LocalDBInstanceInfo ii;  
LocalDBInstanceInfo(L"Test", &ii, sizeof(LocalDBInstanceInfo));  
  
```  
  
 <span data-ttu-id="078db-141">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="078db-141">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078db-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="078db-142">See Also</span></span>  
 [<span data-ttu-id="078db-143">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="078db-143">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
