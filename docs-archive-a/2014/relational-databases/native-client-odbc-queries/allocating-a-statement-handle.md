---
title: 配置語句控制碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: rothja
ms.author: jroth
ms.openlocfilehash: fac0802b474f38f6a6c314dd727fa335d14598d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709345"
---
# <a name="allocating-a-statement-handle"></a><span data-ttu-id="22553-102">配置陳述式控制代碼</span><span class="sxs-lookup"><span data-stu-id="22553-102">Allocating a Statement Handle</span></span>
  <span data-ttu-id="22553-103">在應用程式可以執行陳述式之前，它必須配置陳述式控制代碼。</span><span class="sxs-lookup"><span data-stu-id="22553-103">Before an application can execute a statement, it must allocate a statement handle.</span></span> <span data-ttu-id="22553-104">其方式是呼叫**SQLAllocHandle** ，並將*HandleType*參數設定為 SQL_HANDLE_STMT，並將*InputHandle*指向連接控制碼。</span><span class="sxs-lookup"><span data-stu-id="22553-104">It does this by calling **SQLAllocHandle** with the *HandleType* parameter set to SQL_HANDLE_STMT and *InputHandle* pointing to a connection handle.</span></span>  
  
 <span data-ttu-id="22553-105">陳述式屬性是陳述式控制代碼的特性。</span><span class="sxs-lookup"><span data-stu-id="22553-105">Statement attributes are characteristics of the statement handle.</span></span> <span data-ttu-id="22553-106">範例陳述式屬性可以包含使用書籤和搭配陳述式結果集使用的資料指標種類。</span><span class="sxs-lookup"><span data-stu-id="22553-106">Sample statement attributes can include using bookmarks and the kind of cursor to use with the statement's result set.</span></span> <span data-ttu-id="22553-107">語句屬性是以[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)設定，而且其目前的設定是使用[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)來抓取。</span><span class="sxs-lookup"><span data-stu-id="22553-107">Statement attributes are set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md), and their current settings are retrieved by using [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md).</span></span> <span data-ttu-id="22553-108">應用程式不需要設定任何陳述式屬性；所有陳述式屬性都有預設值，而且有些是驅動程式專屬的。</span><span class="sxs-lookup"><span data-stu-id="22553-108">There is no requirement that an application set any statement attributes; all statement attributes have defaults, and some are driver specific.</span></span>  
  
 <span data-ttu-id="22553-109">使用數個 ODBC 陳述式與連接選項時請小心。</span><span class="sxs-lookup"><span data-stu-id="22553-109">Use caution in the use of several ODBC statement and connection options.</span></span> <span data-ttu-id="22553-110">呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)並將*fOption*設為 SQL_ATTR_LOGIN_TIMEOUT 可控制應用程式在等候建立連接時等待連線嘗試超時的時間 (0 指定無限等候) 。</span><span class="sxs-lookup"><span data-stu-id="22553-110">Calling [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with *fOption* set to SQL_ATTR_LOGIN_TIMEOUT controls the time that an application waits for a connection attempt to time-out while waiting to establish a connection (0 specifies an infinite wait).</span></span> <span data-ttu-id="22553-111">回應時間緩慢的網站可以將這個值設高一點，以確認連接有充足的時間可以完成。</span><span class="sxs-lookup"><span data-stu-id="22553-111">Sites that have slow response times can set this value high to make sure that connections have sufficient time to be completed.</span></span> <span data-ttu-id="22553-112">不過，如果驅動程式無法連接，間隔應該一律夠低，才能在合理的時間內回應使用者。</span><span class="sxs-lookup"><span data-stu-id="22553-112">However, the interval should always be low enough to give the user a response in a reasonable time if the driver cannot connect.</span></span>  
  
 <span data-ttu-id="22553-113">呼叫**SQLSetStmtAttr**並將*fOption*設定為 SQL_ATTR_QUERY_TIMEOUT 會設定查詢逾時間隔，以協助保護伺服器和使用者不受長時間執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="22553-113">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_QUERY_TIMEOUT sets a query time-out interval to help protect the server and the user from long-running queries.</span></span>  
  
 <span data-ttu-id="22553-114">呼叫**SQLSetStmtAttr**並將*fOption*設為 SQL_ATTR_MAX_LENGTH 會限制個別語句可以抓取的**文字**和**影像**資料量。</span><span class="sxs-lookup"><span data-stu-id="22553-114">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_LENGTH limits the amount of **text** and **image** data that an individual statement can retrieve.</span></span> <span data-ttu-id="22553-115">呼叫**SQLSetStmtAttr**並將*fOption*設為 SQL_ATTR_MAX_ROWS 也會將資料列集限制為前*n*個數據列（如果這是所有應用程式都需要）。</span><span class="sxs-lookup"><span data-stu-id="22553-115">Calling **SQLSetStmtAttr** with *fOption* set to SQL_ATTR_MAX_ROWS also limits a rowset to the first *n* rows if that is all the application requires.</span></span> <span data-ttu-id="22553-116">請注意，設定 SQL_ATTR_MAX_ROWS 會使驅動程式對伺服器發出 SET ROWCOUNT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="22553-116">Note that setting SQL_ATTR_MAX_ROWS causes the driver to issue a SET ROWCOUNT statement to the server.</span></span> <span data-ttu-id="22553-117">這會影響所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 語句，包括觸發程式和更新。</span><span class="sxs-lookup"><span data-stu-id="22553-117">This affects all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statements, including triggers and updates.</span></span>  
  
 <span data-ttu-id="22553-118">當您要設定這些選項時，請小心使用。</span><span class="sxs-lookup"><span data-stu-id="22553-118">Use caution when you are setting these options.</span></span> <span data-ttu-id="22553-119">連接控制代碼上的所有陳述式控制代碼對於 SQL_ATTR_MAX_LENGTH 和 SQL_ATTR_MAX_ROWS 最好都有相同的設定。</span><span class="sxs-lookup"><span data-stu-id="22553-119">It is best if all statement handles on a connection handle have the same settings for SQL_ATTR_MAX_LENGTH and SQL_ATTR_MAX_ROWS.</span></span> <span data-ttu-id="22553-120">如果驅動程式從陳述式控制代碼切換到包含這些選項不同值的其他控制代碼，驅動程式必須產生適當的 SET TEXTSIZE 和 SET ROWCOUNT 陳述式才能變更設定。</span><span class="sxs-lookup"><span data-stu-id="22553-120">If the driver switches from a statement handle to another with different values for these options, the driver must generate the appropriate SET TEXTSIZE and SET ROWCOUNT statements to change the settings.</span></span> <span data-ttu-id="22553-121">驅動程式無法將這些陳述式放在與使用者 SQL 陳述式相同的批次中，因為使用者 SQL 陳述式可能包含必須是批次中第一個陳述式的陳述式。</span><span class="sxs-lookup"><span data-stu-id="22553-121">The driver cannot put these statements in the same batch as the user SQL statement because the user SQL statement can contain a statement that must be the first statement in a batch.</span></span> <span data-ttu-id="22553-122">驅動程式必須以單獨的批次傳送 SET TEXTSIZE 和 SET ROWCOUNT 陳述式，這樣會對伺服器自動產生額外的往返。</span><span class="sxs-lookup"><span data-stu-id="22553-122">The driver must send the SET TEXTSIZE and SET ROWCOUNT statements in a separate batch, which automatically generates an additional roundtrip to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22553-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22553-123">See Also</span></span>  
 [<span data-ttu-id="22553-124">&#40;ODBC&#41;執行查詢</span><span class="sxs-lookup"><span data-stu-id="22553-124">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
