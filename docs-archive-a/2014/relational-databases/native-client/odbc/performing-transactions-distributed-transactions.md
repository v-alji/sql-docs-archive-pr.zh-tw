---
title: 執行分散式交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: rothja
ms.author: jroth
ms.openlocfilehash: 9ec23fd1883749e35e67f888e26bdf031ccf7fb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593357"
---
# <a name="performing-distributed-transactions"></a><span data-ttu-id="5e332-102">執行分散式交易</span><span class="sxs-lookup"><span data-stu-id="5e332-102">Performing Distributed Transactions</span></span>
  <span data-ttu-id="5e332-103">Microsoft 分散式交易協調器 (MS DTC) 可讓應用程式在兩個或多個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之間擴充交易。</span><span class="sxs-lookup"><span data-stu-id="5e332-103">The Microsoft Distributed Transaction Coordinator (MS DTC) allows applications to extend transactions across two or more instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5e332-104">也可讓應用程式參與交易管理員所管理且符合 Open Group DTP XA 標準的交易。</span><span class="sxs-lookup"><span data-stu-id="5e332-104">It also allows applications to participate in transactions managed by transaction managers that comply with the Open Group DTP XA standard.</span></span>  
  
 <span data-ttu-id="5e332-105">一般來說，所有交易管理命令都是透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="5e332-105">Normally, all transaction management commands are sent through the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver to the server.</span></span> <span data-ttu-id="5e332-106">應用程式會藉由在關閉自動認可模式的情況下呼叫[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)來啟動交易。</span><span class="sxs-lookup"><span data-stu-id="5e332-106">The application starts a transaction by calling [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) with the autocommit mode turned off.</span></span> <span data-ttu-id="5e332-107">應用程式接著會執行組成交易的更新，並使用 SQL_COMMIT 或 SQL_ROLLBACK 選項來呼叫[SQLEndTran](../../native-client-odbc-api/sqlendtran.md) 。</span><span class="sxs-lookup"><span data-stu-id="5e332-107">The application then performs the updates comprising the transaction and calls [SQLEndTran](../../native-client-odbc-api/sqlendtran.md) with either the SQL_COMMIT or SQL_ROLLBACK option.</span></span>  
  
 <span data-ttu-id="5e332-108">不過，在使用 MS DTC 時，MS DTC 會變成交易管理員，而應用程式不會再使用**SQLEndTran**。</span><span class="sxs-lookup"><span data-stu-id="5e332-108">When using MS DTC, however, MS DTC becomes the transaction manager and the application no longer uses **SQLEndTran**.</span></span>  
  
 <span data-ttu-id="5e332-109">當編列在分散式交易內，然後編列在第二個分散式交易內時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會從原始分散式交易脫離，並編列在新的交易中。</span><span class="sxs-lookup"><span data-stu-id="5e332-109">When enlisted in a distributed transaction, and then enlist in a second distributed transaction, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC Driver defects from the original distributed transaction and enlists in the new transaction.</span></span> <span data-ttu-id="5e332-110">如需詳細資訊，請參閱 DTC 程式設計[人員參考](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="5e332-110">For more information, see [DTC Programmer's Reference](https://msdn.microsoft.com/library/ms686108\(VS.85\).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e332-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e332-111">See Also</span></span>  
 [<span data-ttu-id="5e332-112">&#40;ODBC&#41;執行交易</span><span class="sxs-lookup"><span data-stu-id="5e332-112">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
