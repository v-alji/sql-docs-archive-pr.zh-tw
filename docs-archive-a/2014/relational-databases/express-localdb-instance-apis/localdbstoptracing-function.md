---
title: LocalDBStopTracing 函式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStopTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2bf6051fe8c86728c2ebf0a0b2bc34fabb98edb9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592027"
---
# <a name="localdbstoptracing-function"></a><span data-ttu-id="a39ac-102">LocalDBStopTracing 函數</span><span class="sxs-lookup"><span data-stu-id="a39ac-102">LocalDBStopTracing Function</span></span>
  <span data-ttu-id="a39ac-103">針對目前 Windows 使用者擁有的所有 SQL Server Express LocalDB 執行個體停用 API 呼叫的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a39ac-103">Disables tracing of API calls for all the SQL Server Express LocalDB instances owned by the current Windows user.</span></span>  
  
 <span data-ttu-id="a39ac-104">**標頭檔：** sqlncli。h</span><span class="sxs-lookup"><span data-stu-id="a39ac-104">**Header file:** sqlncli.h</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39ac-105">語法</span><span class="sxs-lookup"><span data-stu-id="a39ac-105">Syntax</span></span>  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a><span data-ttu-id="a39ac-106">傳回</span><span class="sxs-lookup"><span data-stu-id="a39ac-106">Returns</span></span>  
 <span data-ttu-id="a39ac-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="a39ac-107">S_OK</span></span>  
 <span data-ttu-id="a39ac-108">此函數已成功。</span><span class="sxs-lookup"><span data-stu-id="a39ac-108">The function succeeded.</span></span>  
  
 [<span data-ttu-id="a39ac-109">LOCALDB_ERROR_INTERNAL_ERROR</span><span class="sxs-lookup"><span data-stu-id="a39ac-109">LOCALDB_ERROR_INTERNAL_ERROR</span></span>](../express-localdb-error-messages/localdb-error-internal-error.md)  
 <span data-ttu-id="a39ac-110">發生意外錯誤。</span><span class="sxs-lookup"><span data-stu-id="a39ac-110">An unexpected error occurred.</span></span> <span data-ttu-id="a39ac-111">請參閱事件記錄檔，以取得詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a39ac-111">See the event log for details.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a39ac-112">備註</span><span class="sxs-lookup"><span data-stu-id="a39ac-112">Remarks</span></span>  
 <span data-ttu-id="a39ac-113">如需使用 LocalDB API 的程式碼範例，請參閱[SQL Server Express Localdb 參考](../sql-server-express-localdb-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="a39ac-113">For a code sample that uses LocalDB API, see [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39ac-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a39ac-114">See Also</span></span>  
 [<span data-ttu-id="a39ac-115">SQL Server Express LocalDB 標頭和版本資訊</span><span class="sxs-lookup"><span data-stu-id="a39ac-115">SQL Server Express LocalDB Header and Version Information</span></span>](sql-server-express-localdb-header-and-version-information.md)  
  
  
