---
title: LocalDBUnshareInstance 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBUnshareInstance
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 54012ccb-eded-43f7-8ea5-da5ce79224c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77ebf8cad9d410b047fccede4360ca0041637986
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592028"
---
# <a name="localdbunshareinstance-function"></a><span data-ttu-id="64aa2-102">LocalDBUnshareInstance 函數</span><span class="sxs-lookup"><span data-stu-id="64aa2-102">LocalDBUnshareInstance Function</span></span>
  <span data-ttu-id="64aa2-103">停止共用指定的 SQL Server Express LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="64aa2-103">Stops the sharing of the specified SQL Server Express LocalDB instance.</span></span>  
  
 <span data-ttu-id="64aa2-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="64aa2-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64aa2-105">語法</span><span class="sxs-lookup"><span data-stu-id="64aa2-105">Syntax</span></span>  
  
```  
HRESULT LocalDBUnShareInstance(  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64aa2-106">參數</span><span class="sxs-lookup"><span data-stu-id="64aa2-106">Parameters</span></span>  
 <span data-ttu-id="64aa2-107">*pInstanceSharedName*</span><span class="sxs-lookup"><span data-stu-id="64aa2-107">*pInstanceSharedName*</span></span>  
 <span data-ttu-id="64aa2-108">[輸入] 要取消共用之 LocalDB 執行個體的共用名稱。</span><span class="sxs-lookup"><span data-stu-id="64aa2-108">[Input] The shared name for the LocalDB instance to unshare.</span></span>  
  
 <span data-ttu-id="64aa2-109">*dwFlags*</span><span class="sxs-lookup"><span data-stu-id="64aa2-109">*dwFlags*</span></span>  
 <span data-ttu-id="64aa2-110">[輸入] 保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="64aa2-110">[Input] Reserved for future use.</span></span> <span data-ttu-id="64aa2-111">目前應設為 0。</span><span class="sxs-lookup"><span data-stu-id="64aa2-111">Currently should be set to 0.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="64aa2-112">傳回</span><span class="sxs-lookup"><span data-stu-id="64aa2-112">Returns</span></span>  
 <span data-ttu-id="64aa2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="64aa2-113">S_OK</span></span>  
 <span data-ttu-id="64aa2-114">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="64aa2-114">The function succeeded.</span></span>  
  
 [<span data-ttu-id="64aa2-115">LOCALDB_ERROR_NOT_INSTALLED</span><span class="sxs-lookup"><span data-stu-id="64aa2-115">LOCALDB_ERROR_NOT_INSTALLED</span></span>](../express-localdb-error-messages/localdb-error-not-installed.md)  
 <span data-ttu-id="64aa2-116">SQL Server Express LocalDB 未安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="64aa2-116">SQL Server Express LocalDB is not installed on the computer.</span></span>  
  
 [<span data-ttu-id="64aa2-117">LOCALDB_ERROR_INVALID_PARAMETER</span><span class="sxs-lookup"><span data-stu-id="64aa2-117">LOCALDB_ERROR_INVALID_PARAMETER</span></span>](../express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 <span data-ttu-id="64aa2-118">一個或多個指定的輸入參數無效。</span><span class="sxs-lookup"><span data-stu-id="64aa2-118">One or more specified input parameters are invalid.</span></span>  
  
 [<span data-ttu-id="64aa2-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span><span class="sxs-lookup"><span data-stu-id="64aa2-119">LOCALDB_ERROR_INVALID_INSTANCE_NAME</span></span>](../express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 <span data-ttu-id="64aa2-120">指定的執行個體名稱無效。</span><span class="sxs-lookup"><span data-stu-id="64aa2-120">The specified instance name is invalid.</span></span>  
  
 [<span data-ttu-id="64aa2-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span><span class="sxs-lookup"><span data-stu-id="64aa2-121">LOCALDB_ERROR_UNKNOWN_INSTANCE</span></span>](../express-localdb-error-messages/localdb-error-unknown-instance.md)  
 <span data-ttu-id="64aa2-122">指定的執行個體不存在。</span><span class="sxs-lookup"><span data-stu-id="64aa2-122">The specified instance does not exist.</span></span>  
  
 [<span data-ttu-id="64aa2-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="64aa2-123">LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED</span></span>](../express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 <span data-ttu-id="64aa2-124">您必須擁有管理員權限才能執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="64aa2-124">Administrator privileges are required in order to execute this operation.</span></span>  
  
 [<span data-ttu-id="64aa2-125">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="64aa2-125">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="64aa2-126">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="64aa2-126">An unexpected error occurred.</span></span> <span data-ttu-id="64aa2-127">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="64aa2-127">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64aa2-128">備註</span><span class="sxs-lookup"><span data-stu-id="64aa2-128">Remarks</span></span>  
 <span data-ttu-id="64aa2-129">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="64aa2-129">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64aa2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64aa2-130">See Also</span></span>  
 [<span data-ttu-id="64aa2-131">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="64aa2-131">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
