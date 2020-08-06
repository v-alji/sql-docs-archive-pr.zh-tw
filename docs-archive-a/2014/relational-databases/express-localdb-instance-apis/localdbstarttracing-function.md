---
title: LocalDBStartTracing 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1b10482e9839d43e29da72dbe2c194a01d8248eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710626"
---
# <a name="localdbstarttracing-function"></a><span data-ttu-id="3ba23-102">LocalDBStartTracing 函數</span><span class="sxs-lookup"><span data-stu-id="3ba23-102">LocalDBStartTracing Function</span></span>
  <span data-ttu-id="3ba23-103">針對目前 Windows 使用者擁有的所有 SQL Server Express LocalDB 執行個體啟用 API 呼叫的追蹤。</span><span class="sxs-lookup"><span data-stu-id="3ba23-103">Enables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="3ba23-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="3ba23-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba23-105">語法</span><span class="sxs-lookup"><span data-stu-id="3ba23-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="3ba23-106">傳回</span><span class="sxs-lookup"><span data-stu-id="3ba23-106">Returns</span></span>  
 <span data-ttu-id="3ba23-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ba23-107">S_OK</span></span>  
 <span data-ttu-id="3ba23-108">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="3ba23-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="3ba23-109">LOCALDB_ERROR_XEVENT_FAILED</span><span class="sxs-lookup"><span data-stu-id="3ba23-109">LOCALDB_ERROR_XEVENT_FAILED</span></span>](../express-localdb-error-messages/localdb-error-xevent-failed.md)  
 <span data-ttu-id="3ba23-110">無法啟動 LocalDB 執行個體 API 內的 XEvent 引擎。</span><span class="sxs-lookup"><span data-stu-id="3ba23-110">Failed to start XEvent engine within the LocalDB Instance API.</span></span>  
  
 [<span data-ttu-id="3ba23-111">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="3ba23-111">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="3ba23-112">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="3ba23-112">An unexpected error occurred.</span></span> <span data-ttu-id="3ba23-113">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3ba23-113">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ba23-114">備註</span><span class="sxs-lookup"><span data-stu-id="3ba23-114">Remarks</span></span>  
 <span data-ttu-id="3ba23-115">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba23-115">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba23-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ba23-116">See Also</span></span>  
 [<span data-ttu-id="3ba23-117">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="3ba23-117">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
