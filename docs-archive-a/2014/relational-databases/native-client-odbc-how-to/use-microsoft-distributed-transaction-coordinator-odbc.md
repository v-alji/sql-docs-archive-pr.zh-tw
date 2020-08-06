---
title: 使用 Microsoft 分散式交易協調器 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: rothja
ms.author: jroth
ms.openlocfilehash: f7b7da33066a9f4edd01037738ed91155340e6ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594982"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a><span data-ttu-id="5250d-102">使用 Microsoft 分散式交易協調器 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="5250d-102">Use Microsoft Distributed Transaction Coordinator (ODBC)</span></span>
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a><span data-ttu-id="5250d-103">若要使用 MS DTC 來更新兩個或多個 SQL Server</span><span class="sxs-lookup"><span data-stu-id="5250d-103">To update two or more SQL Servers by using MS DTC</span></span>  
  
1.  <span data-ttu-id="5250d-104">使用 MS DTC OLE DtcGetTransactionManager 函數來連接至 MS DTC。</span><span class="sxs-lookup"><span data-stu-id="5250d-104">Connect to MS DTC by using the MS DTC OLE DtcGetTransactionManager function.</span></span> <span data-ttu-id="5250d-105">如需有關 MS DTC 的詳細資訊，請參閱 Microsoft 分散式交易協調器。</span><span class="sxs-lookup"><span data-stu-id="5250d-105">For information about MS DTC, see Microsoft Distributed Transaction Coordinator.</span></span>  
  
2.  <span data-ttu-id="5250d-106">針對您想要建立的每個 Microsoft SQL Server 連接呼叫 SQL DriverConnect 一次。</span><span class="sxs-lookup"><span data-stu-id="5250d-106">Call SQL DriverConnect once for each Microsoft SQL Server connection you want to establish.</span></span>  
  
3.  <span data-ttu-id="5250d-107">呼叫 MS DTC OLE ITransactionDispenser::BeginTransaction 函數來開始 MS DTC 交易並取得代表此交易的交易物件。</span><span class="sxs-lookup"><span data-stu-id="5250d-107">Call the MS DTC OLE ITransactionDispenser::BeginTransaction function to begin an MS DTC transaction and obtain a Transaction object that represents the transaction.</span></span>  
  
4.  <span data-ttu-id="5250d-108">針對您想要在 MS DTC 交易中編列的每個 ODBC 連接，呼叫 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 一次或多次。</span><span class="sxs-lookup"><span data-stu-id="5250d-108">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) one or more times for each ODBC connection you want to enlist in the MS DTC transaction.</span></span> <span data-ttu-id="5250d-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 第二個參數必須是 SQL_ATTR_ENLIST_IN_DTC，且第三個參數必須是交易物件 (在步驟 3 中取得)。</span><span class="sxs-lookup"><span data-stu-id="5250d-109">[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) second parameter must be SQL_ATTR_ENLIST_IN_DTC and third parameter must be the Transaction object (obtained in Step 3).</span></span>  
  
5.  <span data-ttu-id="5250d-110">針對您想要更新的每個 SQL Server，呼叫 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 一次。</span><span class="sxs-lookup"><span data-stu-id="5250d-110">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) once for each SQL Server you want to update.</span></span>  
  
6.  <span data-ttu-id="5250d-111">呼叫 MS DTC OLE ITransaction::Commit 函數來認可 MS DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="5250d-111">Call the MS DTC OLE ITransaction::Commit function to commit the MS DTC transaction.</span></span> <span data-ttu-id="5250d-112">此時，交易物件便不再有效。</span><span class="sxs-lookup"><span data-stu-id="5250d-112">The Transaction object is no longer valid.</span></span>  
  
 <span data-ttu-id="5250d-113">若要執行一連串 MS DTC 交易，請重複步驟 3 到 6。</span><span class="sxs-lookup"><span data-stu-id="5250d-113">To perform a series of MS DTC transactions, repeat Steps 3 through 6.</span></span>  
  
 <span data-ttu-id="5250d-114">若要釋放交易物件的參考，請呼叫 MS DTC OLE ITransaction::Return 函數。</span><span class="sxs-lookup"><span data-stu-id="5250d-114">To release the reference to the Transaction object, call the MS DTC OLE ITransaction::Return function.</span></span>  
  
 <span data-ttu-id="5250d-115">若要使用 ODBC 連接搭配 MS DTC 交易，然後使用相同的連接搭配本機 SQL Server 交易，請使用 SQL_DTC_DONE 來呼叫 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)。</span><span class="sxs-lookup"><span data-stu-id="5250d-115">To use an ODBC connection with an MS DTC transaction, and then use the same connection with a local SQL Server transaction, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_DTC_DONE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5250d-116">您也可以針對每個 SQL Server 依序呼叫 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 和 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)，而非依照先前步驟 4 和 5 所建議的方式呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="5250d-116">You can also call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) and [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) in turn for each SQL Server instead of calling them as suggested earlier in Steps 4 and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5250d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5250d-117">See Also</span></span>  
 [<span data-ttu-id="5250d-118">&#40;ODBC&#41;執行交易</span><span class="sxs-lookup"><span data-stu-id="5250d-118">Performing Transactions &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
