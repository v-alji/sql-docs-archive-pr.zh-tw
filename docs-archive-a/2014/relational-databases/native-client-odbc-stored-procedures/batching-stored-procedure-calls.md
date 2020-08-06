---
title: 批次處理預存程序呼叫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], batching
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- batches [ODBC]
- ODBC CALL escape sequence
ms.assetid: b7f53e11-15f0-4602-8134-b166160888f0
author: rothja
ms.author: jroth
ms.openlocfilehash: a0df58ce59853ee15b863cbc7bce34041c37fee4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709325"
---
# <a name="batching-stored-procedure-calls"></a><span data-ttu-id="f1e63-102">批次預存程序呼叫</span><span class="sxs-lookup"><span data-stu-id="f1e63-102">Batching Stored Procedure Calls</span></span>
  <span data-ttu-id="f1e63-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會在適當時，自動將預存程序呼叫分批批次處理至伺服器。</span><span class="sxs-lookup"><span data-stu-id="f1e63-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver automatically batches stored procedure calls to the server when appropriate.</span></span> <span data-ttu-id="f1e63-104">只有在使用 ODBC CALL 逸出序列時，驅動程式才會執行此動作；它不會針對 [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE 陳述式執行此動作。</span><span class="sxs-lookup"><span data-stu-id="f1e63-104">The driver only does this when the ODBC CALL escape sequence is used; it does not do this for the [!INCLUDE[tsql](../../includes/tsql-md.md)] EXECUTE statement.</span></span> <span data-ttu-id="f1e63-105">批次預存程序呼叫可以減少往返伺服器的次數，並明顯增加效能。</span><span class="sxs-lookup"><span data-stu-id="f1e63-105">Batching stored procedure calls can reduce the number of round trips to the server and significantly increase performance.</span></span>  
  
 <span data-ttu-id="f1e63-106">當您執行包含多個 ODBC CALL 逸出序列的批次時，驅動程式會批次處理伺服器的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1e63-106">The driver batches procedure calls to the server when you execute a batch that contains multiple ODBC CALL escape sequences.</span></span> <span data-ttu-id="f1e63-107">搭配 ODBC CALL 逸出序列使用繫結的參數陣列時，它也會批次處理程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1e63-107">It also batches procedure calls when bound parameter arrays are used with an ODBC CALL escape sequence.</span></span> <span data-ttu-id="f1e63-108">例如，如果您使用資料列取向或資料行取向的參數系結，將具有五個元素的陣列系結至 ODBC CALL SQL 語句的參數，則在呼叫**SQLExecute**或**SQLExecDirect**時，驅動程式會將具有五個程序呼叫的單一批次傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="f1e63-108">For example, if you use either row-wise or column-wise parameter binding to bind an array with five elements to the parameters of an ODBC CALL SQL statement, when **SQLExecute** or **SQLExecDirect** is called, the driver sends a single batch with five procedure calls to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e63-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1e63-109">See Also</span></span>  
 [<span data-ttu-id="f1e63-110">執行預存程序</span><span class="sxs-lookup"><span data-stu-id="f1e63-110">Running Stored Procedures</span></span>](running-stored-procedures.md)  
  
  
