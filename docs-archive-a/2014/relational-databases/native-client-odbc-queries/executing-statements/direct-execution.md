---
title: 直接執行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: rothja
ms.author: jroth
ms.openlocfilehash: 29153f3e4e9265e87feb0e23ba9ae97118691e95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585357"
---
# <a name="direct-execution"></a><span data-ttu-id="f61b0-102">直接執行</span><span class="sxs-lookup"><span data-stu-id="f61b0-102">Direct Execution</span></span>
  <span data-ttu-id="f61b0-103">直接執行是執行陳述式的一種最基本的方式。</span><span class="sxs-lookup"><span data-stu-id="f61b0-103">Direct execution is the most basic way to execute a statement.</span></span> <span data-ttu-id="f61b0-104">應用程式會建立包含語句的字元字串 [!INCLUDE[tsql](../../../includes/tsql-md.md)] ，並使用**SQLExecDirect**函數提交它以供執行。</span><span class="sxs-lookup"><span data-stu-id="f61b0-104">An application builds a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submits it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="f61b0-105">當此陳述式到達伺服器時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會將它編譯成執行計畫，然後立即執行此執行計畫。</span><span class="sxs-lookup"><span data-stu-id="f61b0-105">When the statement reaches the server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compiles it into an execution plan and then immediately runs the execution plan.</span></span>  
  
 <span data-ttu-id="f61b0-106">直接執行通常是由執行階段建立及執行陳述式的應用程式所使用，而且對於將要單次執行的陳述式也是最有效率的方法。</span><span class="sxs-lookup"><span data-stu-id="f61b0-106">Direct execution is commonly used by applications that build and execute statements at run time and is the most efficient method for statements that will be executed a single time.</span></span> <span data-ttu-id="f61b0-107">但是它在許多資料庫中有一個缺點，就是每當執行此 SQL 陳述式時，都必須要剖析及編譯它，這樣會在該陳述式執行多次時增加負擔。</span><span class="sxs-lookup"><span data-stu-id="f61b0-107">Its drawback with many databases is that the SQL statement must be parsed and compiled each time it is executed, which adds overhead if the statement is executed multiple times.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f61b0-108">會大幅改善在多使用者環境中經常執行之陳述式的直接執行效能，而且針對經常執行的 SQL 陳述式搭配參數標記使用 SQLExecDirect 可以讓已備妥的執行提高效率。</span><span class="sxs-lookup"><span data-stu-id="f61b0-108">significantly improves the performance of direct execution of commonly executed statements in multiuser environments and using SQLExecDirect with parameter markers for commonly executed SQL statements can approach the efficiency of prepared execution.</span></span>  
  
 <span data-ttu-id="f61b0-109">當連接到的實例時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驅動程式會使用[sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql)來傳輸在**SQLExecDirect**上指定的 SQL 語句或批次。</span><span class="sxs-lookup"><span data-stu-id="f61b0-109">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) to transmit the SQL statement or batch specified on **SQLExecDirect**.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="f61b0-110">具有邏輯，可以快速判斷以**sp_executesql**執行的 SQL 語句或批次是否符合產生已存在於記憶體中之執行計畫的語句或批次。</span><span class="sxs-lookup"><span data-stu-id="f61b0-110">has logic to quickly determine if an SQL statement or batch executed with **sp_executesql** matches the statement or batch that generated an execution plan that already exists in memory.</span></span> <span data-ttu-id="f61b0-111">如果兩者相符，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 只會重複使用現有的計畫，而不是編譯新的計畫。</span><span class="sxs-lookup"><span data-stu-id="f61b0-111">If a match is made, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] simply reuses the existing plan rather than compile a new plan.</span></span> <span data-ttu-id="f61b0-112">這表示，在具有許多使用者的系統中，使用**SQLExecDirect**執行的常用 SQL 語句，將受益于舊版中的預存程式所提供的許多方案重複使用優勢 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f61b0-112">This means that commonly executed SQL statements executed with **SQLExecDirect** in a system with many users will benefit from many of the plan-reuse benefits that were only available to stored procedures in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="f61b0-113">只有當幾位使用者正在執行相同的 SQL 陳述式或批次時，重複使用執行計畫的這項好處才有效。</span><span class="sxs-lookup"><span data-stu-id="f61b0-113">This benefit of reusing execution plans only works when several users are executing the same SQL statement or batch.</span></span> <span data-ttu-id="f61b0-114">請遵循編碼慣例來增加不同用戶端執行的 SQL 陳述式非常類似於能夠重複使用執行計畫的機率：</span><span class="sxs-lookup"><span data-stu-id="f61b0-114">Follow these coding conventions to increase the probability that the SQL statements executed by different clients are similar enough to be able to reuse execution plans:</span></span>  
  
-   <span data-ttu-id="f61b0-115">請勿在 SQL 陳述式中包含資料常數，而是要改用繫結至程式變數的參數標記。</span><span class="sxs-lookup"><span data-stu-id="f61b0-115">Do not include data constants in the SQL statements; instead use parameter markers bound to program variables.</span></span> <span data-ttu-id="f61b0-116">如需詳細資訊，請參閱[Using 語句參數](../using-statement-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="f61b0-116">For more information, see [Using Statement Parameters](../using-statement-parameters.md).</span></span>  
  
-   <span data-ttu-id="f61b0-117">使用完整的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="f61b0-117">Use fully qualified object names.</span></span> <span data-ttu-id="f61b0-118">如果物件名稱不是完整的，就不會重複使用執行計畫。</span><span class="sxs-lookup"><span data-stu-id="f61b0-118">Execution plans are not reused if object names are not qualified.</span></span>  
  
-   <span data-ttu-id="f61b0-119">盡量讓應用程式連接使用一組常用的連接和陳述式選項。</span><span class="sxs-lookup"><span data-stu-id="f61b0-119">Have application connections as possible use a common set of connection and statement options.</span></span> <span data-ttu-id="f61b0-120">使用一組選項 (如 ANSI_NULLS) 為連接產生的執行計畫將不會重複用於具有另一組選項的連接。</span><span class="sxs-lookup"><span data-stu-id="f61b0-120">Execution plans generated for a connection with one set of options (such as ANSI_NULLS) are not reused for a connection having another set of options.</span></span> <span data-ttu-id="f61b0-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者都會針對這些選項使用相同的預設值。</span><span class="sxs-lookup"><span data-stu-id="f61b0-121">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider both have the same default settings for these options.</span></span>  
  
 <span data-ttu-id="f61b0-122">如果所有使用**SQLExecDirect**執行的語句都是使用這些慣例來編碼， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 就可以在發生商機時重複使用執行計畫。</span><span class="sxs-lookup"><span data-stu-id="f61b0-122">If all statements executed with **SQLExecDirect** are coded using these conventions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can reuse execution plans when the opportunity arises.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61b0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f61b0-123">See Also</span></span>  
 [<span data-ttu-id="f61b0-124">&#40;ODBC&#41;執行語句</span><span class="sxs-lookup"><span data-stu-id="f61b0-124">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
