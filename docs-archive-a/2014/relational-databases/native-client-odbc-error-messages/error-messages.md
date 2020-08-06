---
title: 錯誤訊息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: rothja
ms.author: jroth
ms.openlocfilehash: d004ba320b50896b6f57c5de335d7f7b3d33e87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706457"
---
# <a name="error-messages"></a><span data-ttu-id="4a4a4-102">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="4a4a4-102">Error Messages</span></span>
  <span data-ttu-id="4a4a4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式所傳回的訊息文字會放在**SQLGetDiagRec**的*MessageText*參數中。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-103">The text of messages returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver is placed in the *MessageText* parameter of **SQLGetDiagRec**.</span></span> <span data-ttu-id="4a4a4-104">錯誤的來源會由訊息的標頭指出：</span><span class="sxs-lookup"><span data-stu-id="4a4a4-104">The source of an error is indicated by the header of the message:</span></span>  
  
 <span data-ttu-id="4a4a4-105">[Microsoft][ODBC Driver Manager]</span><span class="sxs-lookup"><span data-stu-id="4a4a4-105">[Microsoft][ODBC Driver Manager]</span></span>  
 <span data-ttu-id="4a4a4-106">這些錯誤是由 ODBC 驅動程式管理員所引發。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-106">These errors are raised by the ODBC Driver Manager.</span></span>  
  
 <span data-ttu-id="4a4a4-107">[Microsoft][ODBC Cursor Library]</span><span class="sxs-lookup"><span data-stu-id="4a4a4-107">[Microsoft][ODBC Cursor Library]</span></span>  
 <span data-ttu-id="4a4a4-108">這些錯誤是由 ODBC 資料指標程式庫所引發。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-108">These errors are raised by the ODBC cursor library.</span></span>  
  
 <span data-ttu-id="4a4a4-109">[Microsoft][SQL Server Native Client]</span><span class="sxs-lookup"><span data-stu-id="4a4a4-109">[Microsoft][SQL Server Native Client]</span></span>  
 <span data-ttu-id="4a4a4-110">這些錯誤是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式所引發。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-110">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="4a4a4-111">如果沒有具有 Net-Library 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 名稱的任何其他節點，則驅動程式會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-111">If there are no other nodes with either the name of a Net-Library or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], then the error was encountered in the driver.</span></span>  
  
 <span data-ttu-id="4a4a4-112">Microsoft[SQL Server Native Client][*Net-net-transportname*]</span><span class="sxs-lookup"><span data-stu-id="4a4a4-112">[Microsoft][SQL Server Native Client][*Net-Transportname*]</span></span>  
 <span data-ttu-id="4a4a4-113">這些錯誤是由網路連結 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 庫引發，其中*net net-transportname*是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端網路傳輸的顯示名稱 (例如具名管道、共用記憶體、tcp/ip 通訊端，或透過) 。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-113">These errors are raised by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library, where *Net-Transportname* is the display name of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client network transport (for example, Named Pipes, Shared Memory, TCP/IP Sockets, or VIA).</span></span> <span data-ttu-id="4a4a4-114">錯誤訊息的其餘部份則包含呼叫的 Net-Library 函數，以及由 TDS 函數在基礎網路 API 中所呼叫的函數。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-114">The remainder of the error message contains the Net-Library function called and the function called in the underlying network API by the TDS function.</span></span> <span data-ttu-id="4a4a4-115">這些錯誤所傳回的*pfNative*錯誤碼是來自基礎網路通訊協定堆疊的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-115">The *pfNative* error code returned with these errors is the error code from the underlying network protocol stack.</span></span>  
  
 <span data-ttu-id="4a4a4-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span><span class="sxs-lookup"><span data-stu-id="4a4a4-116">[Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]</span></span>  
 <span data-ttu-id="4a4a4-117">這些錯誤是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所引發。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-117">These errors are raised by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4a4a4-118">錯誤訊息的其餘部分是來自於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的錯誤訊息文字。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-118">The remainder of the error message is the text of the error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4a4a4-119">這些錯誤所傳回的*pfNative*程式碼是中的錯誤號碼 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-119">The *pfNative* code returned with these errors is the error number from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4a4a4-120">如需 (的錯誤訊息清單，以及可由傳回) 的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱中**master**資料庫內**sysmessages**系統資料表的 description 和 error 資料行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4a4a4-120">For more information about a list of error messages (and their numbers) that can be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see the description and error columns of the **sysmessages** system table in the **master** database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a4a4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a4a4-121">See Also</span></span>  
 [<span data-ttu-id="4a4a4-122">處理錯誤與訊息</span><span class="sxs-lookup"><span data-stu-id="4a4a4-122">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
