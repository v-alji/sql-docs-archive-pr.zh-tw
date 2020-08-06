---
title: 非同步模式和 SQLCancel |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- asynchronous operations [SQL Server Native Client]
- SQLCancel function
- SQLSetConnectAttr function
- SQL Server Native Client, asynchronous operations
- ODBC functions
- ODBC applications, asynchronous operations
- SQL Server Native Client ODBC driver, asynchronous mode
ms.assetid: f31702a2-df76-4589-ac3b-da5412c03dc2
author: rothja
ms.author: jroth
ms.openlocfilehash: 9071c6821e6edeb577b639223e42899d2927bced
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598302"
---
# <a name="asynchronous-mode-and-sqlcancel"></a><span data-ttu-id="683c1-102">非同步模式和 SQLCancel</span><span class="sxs-lookup"><span data-stu-id="683c1-102">Asynchronous Mode and SQLCancel</span></span>
  <span data-ttu-id="683c1-103">某些 ODBC 函數可以透過同步或非同步方式來操作。</span><span class="sxs-lookup"><span data-stu-id="683c1-103">Some ODBC functions can operate either synchronously or asynchronously.</span></span> <span data-ttu-id="683c1-104">應用程式可以針對陳述式控制代碼或連接控制代碼來啟用非同步作業。</span><span class="sxs-lookup"><span data-stu-id="683c1-104">The application can enable asynchronous operations for either a statement handle or a connection handle.</span></span> <span data-ttu-id="683c1-105">如果針對連接控制代碼來設定此選項，它會影響連接控制代碼上的所有陳述式控制代碼。</span><span class="sxs-lookup"><span data-stu-id="683c1-105">If the option is set for a connection handle, it affects all statement handles on the connection handle.</span></span> <span data-ttu-id="683c1-106">應用程式會使用以下陳述式來啟用或停用非同步作業：</span><span class="sxs-lookup"><span data-stu-id="683c1-106">The application uses the following statements to enable or disable asynchronous operations:</span></span>  
  
```  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetConnectAttr(hdbc, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ASYNC_ENABLE,  
                        SQL_ASYNC_ENABLE_OFF, SQL_IS_INTEGER);  
```  
  
 <span data-ttu-id="683c1-107">當應用程式在同步模式下呼叫 ODBC 函數時，此驅動程式要等到被通知伺服器已經完成命令之後，才會將控制權送回應用程式。</span><span class="sxs-lookup"><span data-stu-id="683c1-107">When an application calls an ODBC function in synchronous mode, the driver does not return control to the application until it is notified that the server has completed the command.</span></span>  
  
 <span data-ttu-id="683c1-108">當以非同步方式操作時，此驅動程式會立即將控制權送回應用程式，即使是在傳送命令給伺服器以前。</span><span class="sxs-lookup"><span data-stu-id="683c1-108">When operating asynchronously, the driver immediately returns control to the application, even before sending the command to the server.</span></span> <span data-ttu-id="683c1-109">此驅動程式會將傳回碼設定為 SQL_STILL_EXECUTING。</span><span class="sxs-lookup"><span data-stu-id="683c1-109">The driver sets the return code to SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="683c1-110">然後應用程式可以執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="683c1-110">The application can then perform other work.</span></span>  
  
 <span data-ttu-id="683c1-111">當應用程式測試是否完成命令時，它會使用相同的驅動程式參數來進行相同的函數呼叫。</span><span class="sxs-lookup"><span data-stu-id="683c1-111">When the application tests for completion of the command, it makes the same function call with the same parameters to the driver.</span></span> <span data-ttu-id="683c1-112">如果此驅動程式尚未收到伺服器的回應，它將會再次傳回 SQL_STILL_EXECUTING。</span><span class="sxs-lookup"><span data-stu-id="683c1-112">If the driver has not yet received an answer from the server, it will again return SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="683c1-113">應用程式必須定期測試命令，直到程式碼為 SQL_STILL_EXECUTING 以外的項目為止。</span><span class="sxs-lookup"><span data-stu-id="683c1-113">The application must test the command periodically until the return code is something other than SQL_STILL_EXECUTING.</span></span> <span data-ttu-id="683c1-114">當應用程式取得某個其他傳回碼 (甚至是 SQL_ERROR) 時，它可以判斷出命令已經完成。</span><span class="sxs-lookup"><span data-stu-id="683c1-114">When the application gets some other return code, even SQL_ERROR, it can determine that the command has completed.</span></span>  
  
 <span data-ttu-id="683c1-115">有時命令會持續一段很長的時間未處理。</span><span class="sxs-lookup"><span data-stu-id="683c1-115">Sometimes a command is outstanding for a long time.</span></span> <span data-ttu-id="683c1-116">如果應用程式需要取消命令而不等待回復，則可以使用與未處理的命令相同的語句控制碼呼叫**SQLCancel**來完成此動作。</span><span class="sxs-lookup"><span data-stu-id="683c1-116">If the application needs to cancel the command without waiting for a reply, it can do so by calling **SQLCancel** with the same statement handle as the outstanding command.</span></span> <span data-ttu-id="683c1-117">這是唯一應該使用**SQLCancel**的時間。</span><span class="sxs-lookup"><span data-stu-id="683c1-117">This is the only time **SQLCancel** should be used.</span></span> <span data-ttu-id="683c1-118">有些程式設計人員會在透過結果集處理部分方式時使用**SQLCancel** ，並想要取消其餘的結果集。</span><span class="sxs-lookup"><span data-stu-id="683c1-118">Some programmers use **SQLCancel** when they have processed part way through a result set and want to cancel the rest of the result set.</span></span> <span data-ttu-id="683c1-119">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)或[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)應該用來取消未完成的結果集的其餘部分，而不是**SQLCancel**。</span><span class="sxs-lookup"><span data-stu-id="683c1-119">[SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) or [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) should be used to cancel the remainder of an outstanding result set, not **SQLCancel**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683c1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="683c1-120">See Also</span></span>  
 [<span data-ttu-id="683c1-121">建立 SQL Server Native Client ODBC 驅動程式應用程式</span><span class="sxs-lookup"><span data-stu-id="683c1-121">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
  
