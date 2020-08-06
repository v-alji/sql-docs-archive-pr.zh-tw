---
title: 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- OLE/COM errors
- errors [OLE DB]
- OLE DB error handling, about error handling
- OLE DB error handling
ms.assetid: bd0612f4-96ef-4919-b0f9-b5447210fe93
author: rothja
ms.author: jroth
ms.openlocfilehash: 0560a31b60a10e278f621aa53f1c7fa038fe8039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598849"
---
# <a name="errors"></a><span data-ttu-id="0908f-102">Errors</span><span class="sxs-lookup"><span data-stu-id="0908f-102">Errors</span></span>
  <span data-ttu-id="0908f-103">OLE/COM 物件會透過物件成員函數的 HRESULT 傳回碼報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="0908f-103">OLE/COM objects report errors through the HRESULT return code of object member functions.</span></span> <span data-ttu-id="0908f-104">OLE/COM HRESULT 是一個位元封裝的結構。</span><span class="sxs-lookup"><span data-stu-id="0908f-104">An OLE/COM HRESULT is a bit-packed structure.</span></span> <span data-ttu-id="0908f-105">OLE 會提供為結構成員取值 (Dereference) 的巨集。</span><span class="sxs-lookup"><span data-stu-id="0908f-105">OLE provides macros that dereference structure members.</span></span>  
  
 <span data-ttu-id="0908f-106">OLE/COM 會指定 **IErrorInfo** 介面。</span><span class="sxs-lookup"><span data-stu-id="0908f-106">OLE/COM specifies the **IErrorInfo** interface.</span></span> <span data-ttu-id="0908f-107">介面會公開方法，例如 **GetDescription**。</span><span class="sxs-lookup"><span data-stu-id="0908f-107">The interface exposes methods such as **GetDescription**.</span></span> <span data-ttu-id="0908f-108">這可讓用戶端從 OLE/COM 伺服器擷取錯誤詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0908f-108">This allows clients to extract error details from OLE/COM servers.</span></span> <span data-ttu-id="0908f-109">OLE DB 會擴充 **IErrorInfo**，在執行單一成員函數時，支援傳回多個錯誤資訊封包。</span><span class="sxs-lookup"><span data-stu-id="0908f-109">OLE DB extends **IErrorInfo** to support the return of multiple error information packets on a single-member function execution.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0908f-110">可以傳回多個錯誤。</span><span class="sxs-lookup"><span data-stu-id="0908f-110">can return multiple errors.</span></span> <span data-ttu-id="0908f-111">應用程式可以呼叫與 ISQLErrorInfo 和 IErrorRecords 結合的 [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630)，一次擷取一個伺服器錯誤。</span><span class="sxs-lookup"><span data-stu-id="0908f-111">An application can retrieve server errors one at a time by calling [IMultipleResults::GetResult](https://go.microsoft.com/fwlink/?LinkId=129630) combined with ISQLErrorInfo and IErrorRecords.</span></span>  
  
 <span data-ttu-id="0908f-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開 OLE DB 記錄增強的**IErrorInfo**、自訂 `ISQLErrorInfo` 和提供者特定的[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)錯誤物件介面。</span><span class="sxs-lookup"><span data-stu-id="0908f-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the OLE DB record-enhanced **IErrorInfo**, the custom `ISQLErrorInfo`, and the provider-specific [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) error object interfaces.</span></span>  
  
 <span data-ttu-id="0908f-113">如需追蹤錯誤的資訊，請參閱 [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805) (資料存取追蹤)。</span><span class="sxs-lookup"><span data-stu-id="0908f-113">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="0908f-114">如需有關 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中加入之錯誤追蹤增強功能的詳細資訊，請參閱[存取擴充事件記錄檔中的診斷資訊](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)。</span><span class="sxs-lookup"><span data-stu-id="0908f-114">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0908f-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="0908f-115">In This Section</span></span>  
  
-   [<span data-ttu-id="0908f-116">傳回碼</span><span class="sxs-lookup"><span data-stu-id="0908f-116">Return Codes</span></span>](return-codes.md)  
  
-   [<span data-ttu-id="0908f-117">錯誤介面中的資訊</span><span class="sxs-lookup"><span data-stu-id="0908f-117">Information in Error Interfaces</span></span>](information-in-error-interfaces.md)  
  
-   [<span data-ttu-id="0908f-118">SQL Server 錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="0908f-118">SQL Server Error Detail</span></span>](sql-server-error-detail.md)  
  
-   [<span data-ttu-id="0908f-119">擷取錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="0908f-119">Retrieving Error Information</span></span>](retrieving-error-information.md)  
  
-   [<span data-ttu-id="0908f-120">SQL Server 訊息結果</span><span class="sxs-lookup"><span data-stu-id="0908f-120">SQL Server Message Results</span></span>](sql-server-message-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="0908f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0908f-121">See Also</span></span>  
 [<span data-ttu-id="0908f-122">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="0908f-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
