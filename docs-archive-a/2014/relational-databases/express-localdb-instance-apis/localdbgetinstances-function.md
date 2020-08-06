---
title: LocalDBGetInstances 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBGetInstances
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: f95a9980-8bc0-426c-8aa1-e2660b6784cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4a6f758bd647fd69a14f72a0651bb3e2e33a7c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686934"
---
# <a name="localdbgetinstances-function"></a><span data-ttu-id="2678a-102">LocalDBGetInstances 函數</span><span class="sxs-lookup"><span data-stu-id="2678a-102">LocalDBGetInstances Function</span></span>
  <span data-ttu-id="2678a-103">傳回指定之版本的所有 SQL Server Express LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2678a-103">Returns all SQL Server Express LocalDB instances with the given version.</span></span>  
  
 <span data-ttu-id="2678a-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="2678a-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2678a-105">語法</span><span class="sxs-lookup"><span data-stu-id="2678a-105">Syntax</span></span>  
  
```  
#define MAX_LOCALDB_INSTANCE_NAME_LENGTH 128typedef WCHAR TLocalDBInstanceName[MAX_LOCALDB_INSTANCE_NAME_LENGTH + 1];typedef TLocalDBInstanceName* PTLocalDBInstanceName;  
HRESULT LocalDBGetInstances(  
           PTLocalDBInstanceName pInstanceNames,  
           LPDWORD lpdwNumberOfInstances  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2678a-106">參數</span><span class="sxs-lookup"><span data-stu-id="2678a-106">Parameters</span></span>  
 <span data-ttu-id="2678a-107">*pInstanceNames*</span><span class="sxs-lookup"><span data-stu-id="2678a-107">*pInstanceNames*</span></span>  
 <span data-ttu-id="2678a-108">輸出當此函式傳回時，會包含使用者工作站上已命名和預設 LocalDB 實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="2678a-108">[Output] When this function returns, contains the names of both named and default LocalDB instances on the user's workstation.</span></span>  
  
 <span data-ttu-id="2678a-109">*lpdwNumberOfInstances*</span><span class="sxs-lookup"><span data-stu-id="2678a-109">*lpdwNumberOfInstances*</span></span>  
 <span data-ttu-id="2678a-110">[輸入/輸出]在輸入時，包含*pInstanceNames*緩衝區中實例名稱的位置數目。</span><span class="sxs-lookup"><span data-stu-id="2678a-110">[Input/Output] On input, contains the number of slots for instance names in the *pInstanceNames* buffer.</span></span> <span data-ttu-id="2678a-111">輸出時，包含在使用者工作站上找到的 LocalDB 實例數目。</span><span class="sxs-lookup"><span data-stu-id="2678a-111">On output, contains the number of LocalDB instances found on the user's workstation.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="2678a-112">傳回</span><span class="sxs-lookup"><span data-stu-id="2678a-112">Returns</span></span>  
 <span data-ttu-id="2678a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2678a-113">S_OK</span></span>  
 <span data-ttu-id="2678a-114">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="2678a-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="2678a-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="2678a-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="2678a-116">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="2678a-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="2678a-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="2678a-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="2678a-118">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="2678a-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="2678a-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2678a-119">LOCALDB_ERROR_INSUFFICIENT_BUFFER</span></span>](../express-localdb-error-messages/localdb-error-insufficient-buffer.md)  
 <span data-ttu-id="2678a-120">輸入緩衝區太短，且未要求截斷。</span><span class="sxs-lookup"><span data-stu-id="2678a-120">The input buffer is too short, and truncation was not requested.</span></span>  
  
 [<span data-ttu-id="2678a-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="2678a-121">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>](../express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 <span data-ttu-id="2678a-122">應儲存執行個體的路徑長度超過 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="2678a-122">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
 [<span data-ttu-id="2678a-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span><span class="sxs-lookup"><span data-stu-id="2678a-123">LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY</span></span>](../express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 <span data-ttu-id="2678a-124">無法存取執行個體登錄。</span><span class="sxs-lookup"><span data-stu-id="2678a-124">An instance registry cannot be accessed.</span></span>  
  
 [<span data-ttu-id="2678a-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="2678a-125">LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT</span></span>](../express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 <span data-ttu-id="2678a-126">執行個體組態已損毀。</span><span class="sxs-lookup"><span data-stu-id="2678a-126">An instance configuration is corrupted.</span></span>  
  
 [<span data-ttu-id="2678a-127">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="2678a-127">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="2678a-128">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="2678a-128">An unexpected error occurred.</span></span> <span data-ttu-id="2678a-129">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2678a-129">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2678a-130">備註</span><span class="sxs-lookup"><span data-stu-id="2678a-130">Remarks</span></span>  
 <span data-ttu-id="2678a-131">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="2678a-131">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2678a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2678a-132">See Also</span></span>  
 [<span data-ttu-id="2678a-133">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="2678a-133">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
