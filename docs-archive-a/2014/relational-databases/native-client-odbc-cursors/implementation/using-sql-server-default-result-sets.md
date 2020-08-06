---
title: 使用 SQL Server 預設結果集 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 18cd10dd95329f68a42497d2bea5ce63f345ceff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594065"
---
# <a name="using-sql-server-default-result-sets"></a><span data-ttu-id="a2f68-102">使用 QL Server 預設結果集</span><span class="sxs-lookup"><span data-stu-id="a2f68-102">Using SQL Server Default Result Sets</span></span>
  <span data-ttu-id="a2f68-103">預設的 ODBC 資料指標屬性為：</span><span class="sxs-lookup"><span data-stu-id="a2f68-103">The default ODBC cursor attributes are:</span></span>  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="a2f68-104">每當這些屬性設定為預設值時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式就會使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設的結果集。</span><span class="sxs-lookup"><span data-stu-id="a2f68-104">Whenever these attributes are set to their defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result set.</span></span> <span data-ttu-id="a2f68-105">預設結果集可用於任何受到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支援的 SQL 陳述式，而且是將整個結果集傳送到用戶端的最有效率的方法。</span><span class="sxs-lookup"><span data-stu-id="a2f68-105">Default result sets can be used for any SQL statement supported by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and are the most efficient method of transferring an entire result set to the client.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]<span data-ttu-id="a2f68-106">引進了支援多個 active result sets (MARS) ;應用程式現在每個連接都可以有一個以上的使用中預設結果集。</span><span class="sxs-lookup"><span data-stu-id="a2f68-106">introduced support for multiple active result sets (MARS); applications can now have more than one active default result set per connection.</span></span> <span data-ttu-id="a2f68-107">預設不會啟用 MARS。</span><span class="sxs-lookup"><span data-stu-id="a2f68-107">MARS is not enabled by default.</span></span>  
  
 <span data-ttu-id="a2f68-108">在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以前，預設結果集不能在相同連接上支援多個作用中陳述式。</span><span class="sxs-lookup"><span data-stu-id="a2f68-108">Before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], default result sets did not support multiple active statements on the same connection.</span></span> <span data-ttu-id="a2f68-109">在連接上執行 SQL 陳述式以後，伺服器要等到結果集中的所有資料列都已經處理過後，才能在該連接上接受來自用戶端的命令 (取消其餘結果集的要求除外)。</span><span class="sxs-lookup"><span data-stu-id="a2f68-109">After an SQL statement is executed on a connection, the server does not accept commands (except a request to cancel the rest of the result set) from the client on that connection until all the rows in the result set have been processed.</span></span> <span data-ttu-id="a2f68-110">若要取消部分處理之結果集的其餘部分，請呼叫[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)或[SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) ，並將*fOption*參數設定為 SQL_CLOSE。</span><span class="sxs-lookup"><span data-stu-id="a2f68-110">To cancel the remainder of a partially processed result set, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with the *fOption* parameter set to SQL_CLOSE.</span></span> <span data-ttu-id="a2f68-111">若要完成部分處理的結果集，並測試另一個結果集是否存在，請呼叫[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)。</span><span class="sxs-lookup"><span data-stu-id="a2f68-111">To finish a partially processed result set and test for the presence of another result set, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md).</span></span> <span data-ttu-id="a2f68-112">如果 ODBC 應用程式在預設結果集已完全處理之前，在連接控制碼上嘗試命令，則呼叫會產生 SQL_ERROR 而且**SQLGetDiagRec**的呼叫會傳回：</span><span class="sxs-lookup"><span data-stu-id="a2f68-112">If an ODBC application attempts a command on a connection handle before a default result set has been completely processed, the call generates SQL_ERROR and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2f68-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2f68-113">See Also</span></span>  
 [<span data-ttu-id="a2f68-114">如何實作資料指標</span><span class="sxs-lookup"><span data-stu-id="a2f68-114">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  
