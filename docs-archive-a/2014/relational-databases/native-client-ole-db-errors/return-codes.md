---
title: 傳回碼 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- SQL Server Native Client OLE DB provider, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
ms.assetid: 7f7457e9-fce4-400c-82e5-ee02e9e811c6
author: rothja
ms.author: jroth
ms.openlocfilehash: dd033d16b1e95773d2cab1c4e1fca733dc491b96
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598841"
---
# <a name="return-codes"></a><span data-ttu-id="33a0c-102">傳回碼</span><span class="sxs-lookup"><span data-stu-id="33a0c-102">Return Codes</span></span>
  <span data-ttu-id="33a0c-103">在大部分的基本層級，成員函數不是成功就是失敗。</span><span class="sxs-lookup"><span data-stu-id="33a0c-103">At the most basic level, a member function either succeeds or fails.</span></span> <span data-ttu-id="33a0c-104">在更精確一點的層級，函數可能會成功，但是其成功可能不是應用程式開發人員所樂見的。</span><span class="sxs-lookup"><span data-stu-id="33a0c-104">At a somewhat more precise level, a function can succeed, but its success may not be what the application developer intended.</span></span>  
  
 <span data-ttu-id="33a0c-105">如需 OLE DB 傳回碼的詳細資訊，請參閱 [Return Codes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631) (傳回碼 (OLE DB))。</span><span class="sxs-lookup"><span data-stu-id="33a0c-105">For more information about OLE DB return codes, see [Return Codes (OLE DB)](https://go.microsoft.com/fwlink/?LinkId=101631).</span></span>  
  
 <span data-ttu-id="33a0c-106">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者成員函式傳回 S_OK 時，函數會成功。</span><span class="sxs-lookup"><span data-stu-id="33a0c-106">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function returns S_OK, the function succeeded.</span></span>  
  
 <span data-ttu-id="33a0c-107">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者成員函式未傳回 S_OK 時，OLE/COM HRESULT 解除封裝失敗，而 IS_ERROR 宏可以判斷函式的整體成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="33a0c-107">When a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function does not return S_OK, the OLE/COM HRESULT-unpacking FAILED and IS_ERROR macros can determine the overall success or failure of a function.</span></span>  
  
 <span data-ttu-id="33a0c-108">如果 FAILED 或 IS_ERROR 傳回 TRUE， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者就能確保成員函式執行失敗。</span><span class="sxs-lookup"><span data-stu-id="33a0c-108">If FAILED or IS_ERROR returns TRUE, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is assured that member function execution failed.</span></span> <span data-ttu-id="33a0c-109">當 FAILED 或 IS_ERROR 傳回 FALSE，而且 HRESULT 不等於 S_OK 時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者可確保函數在某種意義上會成功。</span><span class="sxs-lookup"><span data-stu-id="33a0c-109">When FAILED or IS_ERROR return FALSE and the HRESULT does not equal S_OK, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is assured that the function succeeded in some sense.</span></span> <span data-ttu-id="33a0c-110">取用者可以從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者錯誤介面，取得此「具有資訊的成功」傳回的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="33a0c-110">The consumer can retrieve detailed information on this "success with information" return from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider error interfaces.</span></span> <span data-ttu-id="33a0c-111">此外，如果函式清楚地失敗 (失敗的宏會傳回 TRUE) ，則可從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者錯誤介面取得擴充的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="33a0c-111">Also, in the case where a function clearly fails (the FAILED macro returns TRUE), extended error information is available from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider error interfaces.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="33a0c-112">Native Client OLE DB 提供者取用者通常會遇到「具有資訊的成功」 HRESULT 傳回的 DB_S_ERRORSOCCURRED。</span><span class="sxs-lookup"><span data-stu-id="33a0c-112">Native Client OLE DB provider consumers commonly encounter the DB_S_ERRORSOCCURRED "success with information" HRESULT return.</span></span> <span data-ttu-id="33a0c-113">傳回 DB_S_ERRORSOCCURRED 的成員函數通常會定義一或多個可提供狀態值給取用者的參數。</span><span class="sxs-lookup"><span data-stu-id="33a0c-113">Typically, member functions that return DB_S_ERRORSOCCURRED define one or more parameters that deliver status values to the consumer.</span></span> <span data-ttu-id="33a0c-114">取用者無法取得在狀態值參數中傳回之錯誤資訊以外的錯誤資訊，因此取用者應該在可取得錯誤資訊時，實作應用程式邏輯來擷取狀態值。</span><span class="sxs-lookup"><span data-stu-id="33a0c-114">No error information may be available to the consumer other than that returned in status-value parameters, so consumers should implement application logic to retrieve status values when they are available.</span></span>  
  
 <span data-ttu-id="33a0c-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者成員函式不會傳回成功的程式碼 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="33a0c-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member functions do not return the success code S_FALSE.</span></span> <span data-ttu-id="33a0c-116">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者成員函式一律會傳回 S_OK 以表示成功。</span><span class="sxs-lookup"><span data-stu-id="33a0c-116">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member functions always return S_OK to indicate success.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a0c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33a0c-117">See Also</span></span>  
 [<span data-ttu-id="33a0c-118">錯誤</span><span class="sxs-lookup"><span data-stu-id="33a0c-118">Errors</span></span>](errors.md)  
  
  
