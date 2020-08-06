---
title: " (ODBC) 執行查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: rothja
ms.author: jroth
ms.openlocfilehash: adc51186803148056401f58f1207d3e9a7abf9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585361"
---
# <a name="executing-queries-odbc"></a><span data-ttu-id="c1a6e-102">執行查詢 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="c1a6e-102">Executing Queries (ODBC)</span></span>
  <span data-ttu-id="c1a6e-103">當 ODBC 應用程式將連接控制代碼初始化並連接資料來源後，會在連接控制代碼上配置一個或多個陳述式控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-103">After an ODBC application initializes a connection handle and connects with a data source, it allocates one or more statement handles on the connection handle.</span></span> <span data-ttu-id="c1a6e-104">然後，應用程式可以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在語句控制碼上執行語句。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-104">The application can then execute [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements on the statement handle.</span></span> <span data-ttu-id="c1a6e-105">執行 SQL 陳述式的一般事件序列是：</span><span class="sxs-lookup"><span data-stu-id="c1a6e-105">The general sequence of events in executing an SQL statement is:</span></span>  
  
1.  <span data-ttu-id="c1a6e-106">設定任何需要的陳述式屬性。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-106">Set any required statement attributes.</span></span>  
  
2.  <span data-ttu-id="c1a6e-107">建構陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-107">Construct the statement.</span></span>  
  
3.  <span data-ttu-id="c1a6e-108">執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-108">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="c1a6e-109">擷取任何結果集。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-109">Retrieve any result sets.</span></span>  
  
 <span data-ttu-id="c1a6e-110">當應用程式擷取在 (由 SQL 陳述式傳回的) 所有結果集的資料列後，可以在相同陳述式控制代碼上執行另一個查詢。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-110">After an application retrieves all the rows in all of the result sets returned by the SQL statement, it can execute another query on the same statement handle.</span></span> <span data-ttu-id="c1a6e-111">如果應用程式判斷不需要取得特定結果集中的所有資料列，它可以藉由呼叫[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)或[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)來取消其餘的結果集。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-111">If an application determines that it is not required to retrieve all the rows in a particular result set, it can cancel the rest of the result set by calling either [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
 <span data-ttu-id="c1a6e-112">在 ODBC 應用程式中，如果您必須用不同資料多次執行相同的 SQL 陳述式，則在 SQL 陳述式的建構中使用由問號 (?) 所代表的參數標記：</span><span class="sxs-lookup"><span data-stu-id="c1a6e-112">If, in an ODBC application, you must execute the same SQL statement multiple times with different data, use a parameter marker denoted by a question mark (?) in the construction of an SQL statement:</span></span>  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="c1a6e-113">然後，每個參數標記都可以藉由呼叫[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)來系結至程式變數。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-113">Each parameter marker can then be bound to a program variable by calling [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md).</span></span>  
  
 <span data-ttu-id="c1a6e-114">在執行所有 SQL 陳述式，而且也處理其結果集之後，應用程式會釋放陳述式控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-114">After all SQL statements execute and their result sets process, the application frees the statement handle.</span></span>  
  
 <span data-ttu-id="c1a6e-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式支援每個連接控制碼有多個語句控制碼。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-115">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports multiple statement handles per connection handle.</span></span> <span data-ttu-id="c1a6e-116">由於交易是在連接層級管理，因此在所有陳述式控制代碼上所執行的所有工作，會在單一連接控制代碼上管理成為相同交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="c1a6e-116">Transactions are managed at the connection level, so that all work performed on all statement handles on a single connection handle are managed as part of the same transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1a6e-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="c1a6e-117">In This Section</span></span>  
  
-   [<span data-ttu-id="c1a6e-118">配置陳述式控制代碼</span><span class="sxs-lookup"><span data-stu-id="c1a6e-118">Allocating a Statement Handle</span></span>](allocating-a-statement-handle.md)  
  
-   [<span data-ttu-id="c1a6e-119">&#40;ODBC&#41;來建立 SQL 語句</span><span class="sxs-lookup"><span data-stu-id="c1a6e-119">Constructing an SQL Statement &#40;ODBC&#41;</span></span>](constructing-an-sql-statement-odbc.md)  
  
-   [<span data-ttu-id="c1a6e-120">建構資料指標的 SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="c1a6e-120">Constructing SQL Statements for Cursors</span></span>](constructing-sql-statements-for-cursors.md)  
  
-   [<span data-ttu-id="c1a6e-121">使用陳述式參數</span><span class="sxs-lookup"><span data-stu-id="c1a6e-121">Using Statement Parameters</span></span>](using-statement-parameters.md)  
  
-   [<span data-ttu-id="c1a6e-122">&#40;ODBC&#41;執行語句</span><span class="sxs-lookup"><span data-stu-id="c1a6e-122">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements/executing-statements-odbc.md)  
  
-   [<span data-ttu-id="c1a6e-123">釋放陳述式控制代碼</span><span class="sxs-lookup"><span data-stu-id="c1a6e-123">Freeing a Statement Handle</span></span>](freeing-a-statement-handle.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1a6e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1a6e-124">See Also</span></span>  
 [<span data-ttu-id="c1a6e-125">SQL Server Native Client &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="c1a6e-125">SQL Server Native Client &#40;ODBC&#41;</span></span>](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
