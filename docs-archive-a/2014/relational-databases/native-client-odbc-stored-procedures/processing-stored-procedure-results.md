---
title: 處理預存程式結果 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f37a6d8beff88748fa944293bd67f449d29eff2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709317"
---
# <a name="processing-stored-procedure-results"></a><span data-ttu-id="6d691-102">處理預存程序結果</span><span class="sxs-lookup"><span data-stu-id="6d691-102">Processing Stored Procedure Results</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6d691-103">預存程序有四個用於傳回資料的機制：</span><span class="sxs-lookup"><span data-stu-id="6d691-103">stored procedures have four mechanisms used to return data:</span></span>  
  
-   <span data-ttu-id="6d691-104">程序中的每個 SELECT 陳述式都會產生一個結果集。</span><span class="sxs-lookup"><span data-stu-id="6d691-104">Each SELECT statement in the procedure generates a result set.</span></span>  
  
-   <span data-ttu-id="6d691-105">程序可以透過輸出參數傳回資料。</span><span class="sxs-lookup"><span data-stu-id="6d691-105">The procedure can return data through output parameters.</span></span>  
  
-   <span data-ttu-id="6d691-106">資料指標輸出參數可以傳回 [!INCLUDE[tsql](../../includes/tsql-md.md)] 伺服器資料指標。</span><span class="sxs-lookup"><span data-stu-id="6d691-106">A cursor output parameter can pass back a [!INCLUDE[tsql](../../includes/tsql-md.md)] server cursor.</span></span>  
  
-   <span data-ttu-id="6d691-107">程序可以有一個整數的傳回碼。</span><span class="sxs-lookup"><span data-stu-id="6d691-107">The procedure can have an integer return code.</span></span>  
  
 <span data-ttu-id="6d691-108">應用程式必須能夠處理預存程序中的所有這些輸出。</span><span class="sxs-lookup"><span data-stu-id="6d691-108">Applications must be able to handle all these outputs from stored procedures.</span></span> <span data-ttu-id="6d691-109">CALL 或 EXECUTE 陳述式應該包含適用於傳回碼和輸出參數的參數標記。</span><span class="sxs-lookup"><span data-stu-id="6d691-109">The CALL or EXECUTE statement should include parameter markers for the return code and output parameters.</span></span> <span data-ttu-id="6d691-110">使用[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)將它們全部系結為輸出參數， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會將輸出值傳送至系結變數。</span><span class="sxs-lookup"><span data-stu-id="6d691-110">Use [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) to bind them all as output parameters and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver will transfer the output values to the bound variables.</span></span> <span data-ttu-id="6d691-111">輸出參數和傳回碼是上傳給用戶端的最後一個專案 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; 在[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)傳回 SQL_NO_DATA 之前，不會將它們傳回到應用程式。</span><span class="sxs-lookup"><span data-stu-id="6d691-111">Output parameters and return codes are the last items returned to the client by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they are not returned to the application until [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="6d691-112">ODBC 不支援繫結 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料指標參數。</span><span class="sxs-lookup"><span data-stu-id="6d691-112">ODBC does not support binding [!INCLUDE[tsql](../../includes/tsql-md.md)] cursor parameters.</span></span> <span data-ttu-id="6d691-113">由於所有輸出參數都必須在執行程序之前進行繫結，因此，ODBC 應用程式無法呼叫包含輸出資料指標參數的任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序。</span><span class="sxs-lookup"><span data-stu-id="6d691-113">Because all output parameters must be bound before executing a procedure, any [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure that contains an output cursor parameter cannot be called by ODBC applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d691-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d691-114">See Also</span></span>  
 [<span data-ttu-id="6d691-115">執行預存程序</span><span class="sxs-lookup"><span data-stu-id="6d691-115">Running Stored Procedures</span></span>](running-stored-procedures.md)  
  
  
