---
title: ODBC 中的交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, transactions
- transactions [ODBC]
- ODBC, transactions
ms.assetid: c5a87fa5-827a-4e6f-a0d9-924bac881eb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 386b248edfdb6e0ac5eb97b3aeb6c0bbc505a5a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593354"
---
# <a name="transactions-in-odbc"></a><span data-ttu-id="894c1-102">ODBC 中的交易</span><span class="sxs-lookup"><span data-stu-id="894c1-102">Transactions in ODBC</span></span>
  <span data-ttu-id="894c1-103">ODBC 中的交易會在連接層級進行管理。</span><span class="sxs-lookup"><span data-stu-id="894c1-103">Transactions in ODBC are managed at the connection level.</span></span> <span data-ttu-id="894c1-104">當應用程式完成交易時，它會認可或回復透過該連接之所有陳述式控制代碼完成的所有工作。</span><span class="sxs-lookup"><span data-stu-id="894c1-104">When an application completes a transaction, it commits or rolls back all work completed through all statement handles on that connection.</span></span> <span data-ttu-id="894c1-105">若要認可或回復交易，應用程式應該呼叫[SQLEndTran](../../native-client-odbc-api/sqlendtran.md) ，而不是提交 COMMIT 或 ROLLBACK 語句。</span><span class="sxs-lookup"><span data-stu-id="894c1-105">To commit or roll back a transaction, applications should call [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) instead of submitting a COMMIT or ROLLBACK statement.</span></span>  
  
 <span data-ttu-id="894c1-106">應用程式會呼叫[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) ，以便在管理交易的兩個 ODBC 模式之間切換：</span><span class="sxs-lookup"><span data-stu-id="894c1-106">An application calls [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) to switch between the two ODBC modes of managing transactions:</span></span>  
  
-   <span data-ttu-id="894c1-107">自動認可模式</span><span class="sxs-lookup"><span data-stu-id="894c1-107">Autocommit mode</span></span>  
  
     <span data-ttu-id="894c1-108">每個陳述式都會在成功完成時自動認可。</span><span class="sxs-lookup"><span data-stu-id="894c1-108">Each statement is automatically committed when it is completed successfully.</span></span> <span data-ttu-id="894c1-109">當您在自動認可模式下執行時，不需要其他任何交易管理函數。</span><span class="sxs-lookup"><span data-stu-id="894c1-109">When you run in autocommit mode, no other transaction management functions are required.</span></span>  
  
-   <span data-ttu-id="894c1-110">手動認可模式</span><span class="sxs-lookup"><span data-stu-id="894c1-110">Manual-commit mode</span></span>  
  
     <span data-ttu-id="894c1-111">所有執行的語句都會包含在相同的交易中，直到藉由呼叫**SQLEndTran**特別停止為止。</span><span class="sxs-lookup"><span data-stu-id="894c1-111">All executed statements are included in the same transaction until it is specifically stopped by calling **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="894c1-112">自動認可模式是 ODBC 的預設交易模式。</span><span class="sxs-lookup"><span data-stu-id="894c1-112">Autocommit mode is the default transaction mode for ODBC.</span></span> <span data-ttu-id="894c1-113">建立連線時，它會處於自動認可模式，直到呼叫**SQLSetConnectAttr** ，藉由設定自動認可模式來切換為手動認可模式。</span><span class="sxs-lookup"><span data-stu-id="894c1-113">When a connection is made, it is in autocommit mode until **SQLSetConnectAttr** is called to switch to manual-commit mode by setting autocommit mode off.</span></span> <span data-ttu-id="894c1-114">當應用程式關閉自動認可時，傳送到資料庫的下一個陳述式會啟動交易。</span><span class="sxs-lookup"><span data-stu-id="894c1-114">When an application turns autocommit off, the next statement sent to the database starts a transaction.</span></span> <span data-ttu-id="894c1-115">然後，交易會維持有效，直到應用程式使用 SQL_COMMIT 或 SQL_ROLLBACK 選項呼叫**SQLEndTran**為止。</span><span class="sxs-lookup"><span data-stu-id="894c1-115">The transaction then remains in effect until the application calls **SQLEndTran** with either the SQL_COMMIT or SQL_ROLLBACK options.</span></span> <span data-ttu-id="894c1-116">**SQLEndTran**啟動下一個交易之後，傳送至資料庫的命令。</span><span class="sxs-lookup"><span data-stu-id="894c1-116">The command sent to the database after **SQLEndTran** starts the next transaction.</span></span>  
  
 <span data-ttu-id="894c1-117">如果應用程式從手動認可模式切換到自動認可模式，驅動程式會認可目前在連接上開啟的所有交易。</span><span class="sxs-lookup"><span data-stu-id="894c1-117">If an application switches from manual-commit to autocommit mode, the driver commits any transactions currently open on the connection.</span></span>  
  
 <span data-ttu-id="894c1-118">ODBC 應用程式不應使用 Transact-SQL 交易陳述式 (例如，BEGIN TRANSACTION、COMMIT TRANSACTION 或 ROLLBACK TRANSACTION)，因為這可能會在驅動程式上造成未定的行為。</span><span class="sxs-lookup"><span data-stu-id="894c1-118">ODBC applications should not use Transact-SQL transaction statements such as BEGIN TRANSACTION, COMMIT TRANSACTION, or ROLLBACK TRANSACTION because this can cause indeterminate behavior in the driver.</span></span> <span data-ttu-id="894c1-119">ODBC 應用程式應該在自動認可模式中執行，而不是使用任何交易管理函數或語句，或在手動認可模式下執行，並使用 ODBC **SQLEndTran**函數來認可或回復交易。</span><span class="sxs-lookup"><span data-stu-id="894c1-119">An ODBC application should run in autocommit mode and not use any transaction management functions or statements, or run in manual-commit mode and use the ODBC **SQLEndTran** function to either commit or roll back transactions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894c1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="894c1-120">See Also</span></span>  
 [<span data-ttu-id="894c1-121">&#40;ODBC&#41;執行交易</span><span class="sxs-lookup"><span data-stu-id="894c1-121">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
