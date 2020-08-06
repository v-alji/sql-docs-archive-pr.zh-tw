---
title: " (ODBC) 執行語句 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: rothja
ms.author: jroth
ms.openlocfilehash: 3066a09cb1f5e63105ca3ffe2441f19e4bbe0101
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585355"
---
# <a name="executing-statements-odbc"></a><span data-ttu-id="814d5-102">執行陳述式 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="814d5-102">Executing Statements (ODBC)</span></span>
  <span data-ttu-id="814d5-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式提供各種方式來執行資料庫中的 SQL 語句 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="814d5-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers a variety ways to execute SQL statements in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="814d5-104">直接執行</span><span class="sxs-lookup"><span data-stu-id="814d5-104">Direct execution</span></span>  
  
-   <span data-ttu-id="814d5-105">準備執行</span><span class="sxs-lookup"><span data-stu-id="814d5-105">Prepared execution</span></span>  
  
 <span data-ttu-id="814d5-106">直接執行牽涉到建立包含語句的字元字串 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ，並提交它以使用**SQLExecDirect**函數執行。</span><span class="sxs-lookup"><span data-stu-id="814d5-106">Direct execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submitting it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="814d5-107">準備執行則包括建立含有 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的字元字串，然後在兩個階段中執行此字串。</span><span class="sxs-lookup"><span data-stu-id="814d5-107">Prepared execution involves building a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and then executing it in two stages.</span></span> <span data-ttu-id="814d5-108">第一個階段會使用[SQLPrepare 函數](https://go.microsoft.com/fwlink/?LinkId=59360)函式來剖析並編譯中語句的執行計畫 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="814d5-108">The first stage uses the [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) function to parse and compile the execution plan for the statement in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="814d5-109">第二個階段會使用**SQLExecute**函數來執行先前已備妥的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="814d5-109">The second stage uses the **SQLExecute** function to execute the previously prepared execution plan.</span></span> <span data-ttu-id="814d5-110">這樣會省下每次執行時的剖析和編譯負擔。</span><span class="sxs-lookup"><span data-stu-id="814d5-110">This saves the parsing and compiling overhead on each execution.</span></span> <span data-ttu-id="814d5-111">應用程式通常會使用備妥的執行來重複執行相同且參數化的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="814d5-111">Prepared execution is commonly used by applications to repeatedly execute the same, parameterized SQL statement.</span></span>  
  
 <span data-ttu-id="814d5-112">直接和準備執行都可以執行單一 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式或 SQL 陳述式批次，也可以呼叫預存程序。</span><span class="sxs-lookup"><span data-stu-id="814d5-112">Both direct and prepared execution can execute a single [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement or a batch of SQL statements, or they can call a stored procedure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="814d5-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="814d5-113">In This Section</span></span>  
  
-   [<span data-ttu-id="814d5-114">直接執行</span><span class="sxs-lookup"><span data-stu-id="814d5-114">Direct Execution</span></span>](direct-execution.md)  
  
-   [<span data-ttu-id="814d5-115">備妥的執行</span><span class="sxs-lookup"><span data-stu-id="814d5-115">Prepared Execution</span></span>](prepared-execution.md)  
  
-   [<span data-ttu-id="814d5-116">程序</span><span class="sxs-lookup"><span data-stu-id="814d5-116">Procedures</span></span>](procedures.md)  
  
-   [<span data-ttu-id="814d5-117">陳述式的批次</span><span class="sxs-lookup"><span data-stu-id="814d5-117">Batches of Statements</span></span>](batches-of-statements.md)  
  
-   [<span data-ttu-id="814d5-118">ISO 選項的作用</span><span class="sxs-lookup"><span data-stu-id="814d5-118">Effects of ISO Options</span></span>](effects-of-iso-options.md)  
  
## <a name="see-also"></a><span data-ttu-id="814d5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="814d5-119">See Also</span></span>  
 [<span data-ttu-id="814d5-120">&#40;ODBC&#41;執行查詢</span><span class="sxs-lookup"><span data-stu-id="814d5-120">Executing Queries &#40;ODBC&#41;</span></span>](../executing-queries-odbc.md)  
  
  
