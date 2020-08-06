---
title: LocalDBShareInstance 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBShareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 21eb3b9a-7d32-455b-89bb-f624198cd202
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 238bff0b3512ceb03ead186dc001165274bd4e30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595002"
---
# <a name="localdbshareinstance-function"></a><span data-ttu-id="9395a-102">LocalDBShareInstance 函數</span><span class="sxs-lookup"><span data-stu-id="9395a-102">LocalDBShareInstance Function</span></span>
  <span data-ttu-id="9395a-103">使用指定的共用名稱，與電腦的其他使用者共用指定的 SQL Server Express LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9395a-103">Shares the specified SQL Server Express LocalDB instance with other users of the computer, using the specified shared name.</span></span>  
  
 <span data-ttu-id="9395a-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="9395a-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9395a-105">語法</span><span class="sxs-lookup"><span data-stu-id="9395a-105">Syntax</span></span>  
  
```  
HRESULT LocalDBShareInstance(  
           PSID pOwnerSID,  
           PCWSTR pInstancePrivateName,  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9395a-106">參數</span><span class="sxs-lookup"><span data-stu-id="9395a-106">Parameters</span></span>  
 <span data-ttu-id="9395a-107">*pOwnerSID*</span><span class="sxs-lookup"><span data-stu-id="9395a-107">*pOwnerSID*</span></span>  
 <span data-ttu-id="9395a-108">[輸入] 執行個體擁有者的 SID。</span><span class="sxs-lookup"><span data-stu-id="9395a-108">[Input] The SID of the instance owner.</span></span>  
  
 <span data-ttu-id="9395a-109">*pInstancePrivateName*</span><span class="sxs-lookup"><span data-stu-id="9395a-109">*pInstancePrivateName*</span></span>  
 <span data-ttu-id="9395a-110">[輸入] 要共用之 LocalDB 執行個體的私用名稱。</span><span class="sxs-lookup"><span data-stu-id="9395a-110">[Input] The private name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="9395a-111">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="9395a-111">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="9395a-112">[輸入] 要共用之 LocalDB 執行個體的共用名稱。</span><span class="sxs-lookup"><span data-stu-id="9395a-112">[Input] The shared name for the LocalDB instance to share.</span></span>  
  
 <span data-ttu-id="9395a-113">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="9395a-113">*dwFlags*</span></span>  
 <span data-ttu-id="9395a-114">[輸入] 保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="9395a-114">[Input] Reserved for future use.</span></span> <span data-ttu-id="9395a-115">目前應設為 0。</span><span class="sxs-lookup"><span data-stu-id="9395a-115">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="9395a-116">傳回</span><span class="sxs-lookup"><span data-stu-id="9395a-116">Returns</span></span>  
 <span data-ttu-id="9395a-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="9395a-117">S_OK</span></span>  
 <span data-ttu-id="9395a-118">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="9395a-118">The function succeeded.</span></span>  
  
 [<span data-ttu-id="9395a-119">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="9395a-119">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="9395a-120">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="9395a-120">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="9395a-121">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="9395a-121">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="9395a-122">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="9395a-122">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="9395a-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="9395a-123">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="9395a-124">指定的執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="9395a-124">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="9395a-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="9395a-125">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="9395a-126">指定的執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="9395a-126">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="9395a-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="9395a-127">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="9395a-128">您必須擁有管理員權限才能執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="9395a-128">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="9395a-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span><span class="sxs-lookup"><span data-stu-id="9395a-129">LOCALDB_ERROR_SHARED_NAME_TAKEN</span></span>](../express-localdb-error-messages/localdb-error-shared-name-taken.md)  
 <span data-ttu-id="9395a-130">指定的共用名稱已被使用。</span><span class="sxs-lookup"><span data-stu-id="9395a-130">The specified shared name is already taken.</span></span>  
  
 [<span data-ttu-id="9395a-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span><span class="sxs-lookup"><span data-stu-id="9395a-131">LOCALDB_ERROR_INSTANCE_ALREADY_SHARED</span></span>](../express-localdb-error-messages/localdb-error-instance-already-shared.md)  
 <span data-ttu-id="9395a-132">已共用指定的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9395a-132">The specified instance is already shared.</span></span>  
  
 [<span data-ttu-id="9395a-133">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="9395a-133">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="9395a-134">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="9395a-134">An unexpected error occurred.</span></span> <span data-ttu-id="9395a-135">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9395a-135">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9395a-136">備註</span><span class="sxs-lookup"><span data-stu-id="9395a-136">Remarks</span></span>  
 <span data-ttu-id="9395a-137">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="9395a-137">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9395a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9395a-138">See Also</span></span>  
 [<span data-ttu-id="9395a-139">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="9395a-139">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
