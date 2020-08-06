---
title: 語句的批次 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
author: rothja
ms.author: jroth
ms.openlocfilehash: 4818b67766dafe851035041c8fd5137a0dfade73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585360"
---
# <a name="batches-of-statements"></a><span data-ttu-id="c4d34-102">陳述式的批次</span><span class="sxs-lookup"><span data-stu-id="c4d34-102">Batches of Statements</span></span>
  <span data-ttu-id="c4d34-103">語句的批次 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 包含兩個或多個語句，以分號分隔 (; ) ，內建于傳遞至**SQLExecDirect**或[SQLPrepare 函數](https://go.microsoft.com/fwlink/?LinkId=59360)的單一字串中。</span><span class="sxs-lookup"><span data-stu-id="c4d34-103">A batch of [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements contains two or more statements, separated by a semicolon (;), built into a single string passed to **SQLExecDirect** or [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span> <span data-ttu-id="c4d34-104">例如：</span><span class="sxs-lookup"><span data-stu-id="c4d34-104">For example:</span></span>  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 <span data-ttu-id="c4d34-105">批次可能會比個別提交陳述式更有效率，因為其網路傳輸量通常較低。</span><span class="sxs-lookup"><span data-stu-id="c4d34-105">Batches can be more efficient than submitting statements separately because network traffic is often reduced.</span></span> <span data-ttu-id="c4d34-106">當使用目前的結果集完成時，請使用[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)來取得下一個結果集的位置。</span><span class="sxs-lookup"><span data-stu-id="c4d34-106">Use [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to get positioned on the next result set when finished with the current result set.</span></span>  
  
 <span data-ttu-id="c4d34-107">當 ODBC 資料指標屬性設定為預設值 (資料列集大小為 1 的順向唯讀資料指標) 時，就一定可以使用批次。</span><span class="sxs-lookup"><span data-stu-id="c4d34-107">Batches can always be used when the ODBC cursor attributes are set to the defaults of a forward-only, read-only cursor with a rowset size of 1.</span></span>  
  
 <span data-ttu-id="c4d34-108">如果針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用伺服器資料指標時執行了批次，伺服器資料指標就會隱含地轉換成預設的結果集。</span><span class="sxs-lookup"><span data-stu-id="c4d34-108">If a batch is executed when using server cursors against [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="c4d34-109">**SQLExecDirect**或**SQLExecute**會傳回 SQL_SUCCESS_WITH_INFO，而對**SQLGetDiagRec**的呼叫會傳回：</span><span class="sxs-lookup"><span data-stu-id="c4d34-109">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and a call to **SQLGetDiagRec** returns:</span></span>  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4d34-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4d34-110">See Also</span></span>  
 [<span data-ttu-id="c4d34-111">&#40;ODBC&#41;執行語句</span><span class="sxs-lookup"><span data-stu-id="c4d34-111">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
