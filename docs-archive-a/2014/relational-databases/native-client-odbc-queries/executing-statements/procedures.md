---
title: 程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: rothja
ms.author: jroth
ms.openlocfilehash: a7ae4678d324ba7d07ae429793b1f75b57bb15e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585349"
---
# <a name="procedures"></a><span data-ttu-id="8030c-102">程序</span><span class="sxs-lookup"><span data-stu-id="8030c-102">Procedures</span></span>
  <span data-ttu-id="8030c-103">預存程序是包含一個或多個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的先行編譯可執行物件。</span><span class="sxs-lookup"><span data-stu-id="8030c-103">A stored procedure is a precompiled executable object that contains one or more [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="8030c-104">預存程序可以有輸入和輸出參數，也可以輸出整數傳回碼。</span><span class="sxs-lookup"><span data-stu-id="8030c-104">Stored procedures can have input and output parameters and can also put out an integer return code.</span></span> <span data-ttu-id="8030c-105">應用程式可以使用目錄函數來列舉可用的預存程序。</span><span class="sxs-lookup"><span data-stu-id="8030c-105">An application can enumerate available stored procedures by using catalog functions.</span></span>  
  
 <span data-ttu-id="8030c-106">目標為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 ODBC 應用程式僅能使用直接執行來呼叫預存程序。</span><span class="sxs-lookup"><span data-stu-id="8030c-106">ODBC applications that target [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] should only use direct execution to call a stored procedure.</span></span> <span data-ttu-id="8030c-107">當連接到舊版時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驅動程式會藉由建立暫存預存程序來執行[SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360)函式，然後在**SQLExecute**上呼叫它。</span><span class="sxs-lookup"><span data-stu-id="8030c-107">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver implements [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) by creating a temporary stored procedure, which is then called on **SQLExecute**.</span></span> <span data-ttu-id="8030c-108">它會增加額外負荷，讓**SQLPrepare**建立只呼叫目標預存程式的暫存預存程序，而不是直接執行目標預存程式。</span><span class="sxs-lookup"><span data-stu-id="8030c-108">It adds overhead to have **SQLPrepare** create a temporary stored procedure that only calls the target stored procedure versus directly executing the target stored procedure.</span></span> <span data-ttu-id="8030c-109">即使在連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體時，跨網路準備呼叫都需要額外的往返，而且需要建立只呼叫預存程序執行計畫的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="8030c-109">Even when connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], preparing a call requires an extra round trip across the network and the building of an execution plan that just calls the stored procedure execution plan.</span></span>  
  
 <span data-ttu-id="8030c-110">執行預存程序時，ODBC 應用程式應該會使用 ODBC CALL 語法。</span><span class="sxs-lookup"><span data-stu-id="8030c-110">ODBC applications should use the ODBC CALL syntax when executing a stored procedure.</span></span> <span data-ttu-id="8030c-111">使用 ODBC CALL 語法時，系統會最佳化驅動程式，使用遠端程序呼叫機制來呼叫程序。</span><span class="sxs-lookup"><span data-stu-id="8030c-111">The driver is optimized to use a remote procedure call mechanism to call the procedure when the ODBC CALL syntax is used.</span></span> <span data-ttu-id="8030c-112">這比將 [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE 陳述式傳送到伺服器所使用的機制更有效率。</span><span class="sxs-lookup"><span data-stu-id="8030c-112">This is more efficient than the mechanism used to send a [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE statement to the server.</span></span>  
  
 <span data-ttu-id="8030c-113">如需詳細資訊，請參閱執行[預存程式](../../native-client-odbc-stored-procedures/running-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="8030c-113">For more information, see [Running Stored Procedures](../../native-client-odbc-stored-procedures/running-stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8030c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8030c-114">See Also</span></span>  
 [<span data-ttu-id="8030c-115">&#40;ODBC&#41;執行語句</span><span class="sxs-lookup"><span data-stu-id="8030c-115">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
