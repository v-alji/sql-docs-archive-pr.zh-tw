---
title: 處理錯誤和訊息 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, about error handling
- errors [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], about messages
- ODBC error handling
- SQL_INVALID_HANDLE return code
- errors [ODBC], about error handling
- messages [ODBC]
ms.assetid: 74ea9630-e482-4a46-bb45-f5234f079b48
author: rothja
ms.author: jroth
ms.openlocfilehash: 4701b3224b87e7d19f1121f193d4be20f9d4c441
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698185"
---
# <a name="handling-errors-and-messages"></a><span data-ttu-id="68eca-102">處理錯誤與訊息</span><span class="sxs-lookup"><span data-stu-id="68eca-102">Handling Errors and Messages</span></span>
  <span data-ttu-id="68eca-103">當應用程式呼叫 ODBC 函數時，驅動程式會以兩種方式執行函數並傳回診斷資訊：傳回碼會指出整體 ODBC 函數成功或失敗，而診斷記錄會提供函數的相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="68eca-103">When an application calls an ODBC function, the driver executes the function and returns diagnostic information in two ways: A return code indicates the overall success or failure of an ODBC function, and diagnostic records provide detailed information about the function.</span></span> <span data-ttu-id="68eca-104">診斷記錄包含標頭記錄和狀態記錄。</span><span class="sxs-lookup"><span data-stu-id="68eca-104">Diagnostic records include a header record and status records.</span></span> <span data-ttu-id="68eca-105">即使函數成功，也會傳回至少一個診斷記錄，也就是標頭記錄。</span><span class="sxs-lookup"><span data-stu-id="68eca-105">At least one diagnostic record, the header record, is returned even if the function succeeds.</span></span>  
  
 <span data-ttu-id="68eca-106">診斷資訊會在開發時間用於捕捉程式設計錯誤，例如，在硬式編碼 SQL 陳述式中發生無效的控制代碼和語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="68eca-106">Diagnostic information is used at development time to catch programming errors, such as invalid handles and syntax errors in hard-coded SQL statements.</span></span> <span data-ttu-id="68eca-107">該資訊也會在執行階段用於捕捉執行階段錯誤和警告，例如，使用者傳回的 SQL 陳述式中發生資料截斷、規則違規和語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="68eca-107">It is also used at run time to catch run-time errors and warnings, such as data truncation, rule violations, and syntax errors in SQL statements entered by the user.</span></span> <span data-ttu-id="68eca-108">程式邏輯通常會以傳回碼為基礎。</span><span class="sxs-lookup"><span data-stu-id="68eca-108">Program logic is generally based on return codes.</span></span>  
  
 <span data-ttu-id="68eca-109">例如，在應用程式呼叫**SQLFetch**來抓取結果集中的資料列之後，傳回碼會指出是否已達到結果集的結尾 (SQL_NO_DATA) 、是否有任何參考訊息 (SQL_SUCCESS_WITH_INFO) ，或 (SQL_ERROR) 發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="68eca-109">For example, after an application calls **SQLFetch** to retrieve the rows in a result set, the return code indicates whether the end of the result set was reached (SQL_NO_DATA), if any informational messages were returned (SQL_SUCCESS_WITH_INFO), or if an error occurred (SQL_ERROR).</span></span>  
  
 <span data-ttu-id="68eca-110">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式傳回 SQL_SUCCESS 以外的任何專案，應用程式可以呼叫**SQLGetDiagRec**來取得任何資訊或錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="68eca-110">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns anything other than SQL_SUCCESS, the application can call **SQLGetDiagRec** to retrieve any informational or error messages.</span></span> <span data-ttu-id="68eca-111">如果有一個以上的訊息，請使用**SQLGetDiagRec**來向上和向下移動訊息集。</span><span class="sxs-lookup"><span data-stu-id="68eca-111">Use **SQLGetDiagRec** to scroll up and down the message set if there is more than one message.</span></span>  
  
 <span data-ttu-id="68eca-112">傳回碼 SQL_INVALID_HANDLE 永遠會指出程式設計錯誤，而且絕不會在執行階段發生。</span><span class="sxs-lookup"><span data-stu-id="68eca-112">The return code SQL_INVALID_HANDLE always indicates a programming error and should never be encountered at run time.</span></span> <span data-ttu-id="68eca-113">雖然 SQL_ERROR 可能會指出程式設計錯誤，其他所有傳回碼還是會提供執行階段資訊。</span><span class="sxs-lookup"><span data-stu-id="68eca-113">All other return codes provide run-time information, although SQL_ERROR may indicate a programming error.</span></span>  
  
 <span data-ttu-id="68eca-114">原始的原 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生 API （適用于 C 的 db-library）可讓應用程式安裝回呼錯誤處理，以及傳回錯誤或訊息的訊息處理函式。</span><span class="sxs-lookup"><span data-stu-id="68eca-114">The original [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native API, DB-Library for C, allows an application to install callback error-handling and message-handling functions that return errors or messages.</span></span> <span data-ttu-id="68eca-115">有些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式 (例如，PRINT、RAISERROR、DBCC 和 SET) 會將其結果傳回 DB-Library 訊息處理常式函數，而非結果集。</span><span class="sxs-lookup"><span data-stu-id="68eca-115">Some [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, such as PRINT, RAISERROR, DBCC, and SET, return their results to the DB-Library message handler function instead of to a result set.</span></span> <span data-ttu-id="68eca-116">不過，ODBC API 沒有此種回撥能力。</span><span class="sxs-lookup"><span data-stu-id="68eca-116">However, the ODBC API has no such callback capability.</span></span> <span data-ttu-id="68eca-117">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式偵測到來自的訊息時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，它會將 ODBC 傳回碼設定為 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，並傳回訊息做為一或多個診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="68eca-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver detects messages coming back from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], it sets the ODBC return code to SQL_SUCCESS_WITH_INFO or SQL_ERROR and returns the message as one or more diagnostic records.</span></span> <span data-ttu-id="68eca-118">因此，ODBC 應用程式必須仔細測試這些傳回碼，並呼叫**SQLGetDiagRec**來捕獲訊息資料。</span><span class="sxs-lookup"><span data-stu-id="68eca-118">Therefore, an ODBC application must carefully test for these return codes and call **SQLGetDiagRec** to retrieve message data.</span></span>  
  
 <span data-ttu-id="68eca-119">如需追蹤錯誤的資訊，請參閱 [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805) (資料存取追蹤)。</span><span class="sxs-lookup"><span data-stu-id="68eca-119">For information about tracing errors, see [Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805).</span></span> <span data-ttu-id="68eca-120">如需有關 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 中加入之錯誤追蹤增強功能的詳細資訊，請參閱[存取擴充事件記錄檔中的診斷資訊](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)。</span><span class="sxs-lookup"><span data-stu-id="68eca-120">For information about enhancements to error tracing added in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68eca-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="68eca-121">In This Section</span></span>  
  
-   [<span data-ttu-id="68eca-122">處理產生訊息的陳述式</span><span class="sxs-lookup"><span data-stu-id="68eca-122">Processing Statements That Generate Messages</span></span>](processing-statements-that-generate-messages.md)  
  
-   [<span data-ttu-id="68eca-123">診斷記錄和欄位</span><span class="sxs-lookup"><span data-stu-id="68eca-123">Diagnostic Records and Fields</span></span>](diagnostic-records-and-fields.md)  
  
-   [<span data-ttu-id="68eca-124">原生錯誤號碼</span><span class="sxs-lookup"><span data-stu-id="68eca-124">Native Error Numbers</span></span>](native-error-numbers.md)  
  
-   [<span data-ttu-id="68eca-125">SQLSTATE &#40;ODBC 錯誤碼&#41;</span><span class="sxs-lookup"><span data-stu-id="68eca-125">SQLSTATE &#40;ODBC Error Codes&#41;</span></span>](sqlstate-odbc-error-codes.md)  
  
-   [<span data-ttu-id="68eca-126">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="68eca-126">Error Messages</span></span>](error-messages.md)  
  
## <a name="see-also"></a><span data-ttu-id="68eca-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68eca-127">See Also</span></span>  
 [<span data-ttu-id="68eca-128">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="68eca-128">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
