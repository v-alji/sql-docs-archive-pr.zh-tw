---
title: 執行預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e5de6a9a13c95b417657a1d108403fa27abe34b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709306"
---
# <a name="running-stored-procedures"></a><span data-ttu-id="948d3-102">執行預存程序</span><span class="sxs-lookup"><span data-stu-id="948d3-102">Running Stored Procedures</span></span>
  <span data-ttu-id="948d3-103">預存程序是一種儲存在資料庫中的可執行物件。</span><span class="sxs-lookup"><span data-stu-id="948d3-103">A stored procedure is an executable object stored in a database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="948d3-104">支援：</span><span class="sxs-lookup"><span data-stu-id="948d3-104">supports:</span></span>  
  
-   <span data-ttu-id="948d3-105">預存程序：</span><span class="sxs-lookup"><span data-stu-id="948d3-105">Stored procedures:</span></span>  
  
     <span data-ttu-id="948d3-106">已經先行編譯為單一可執行程序的一或多個 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="948d3-106">One or more SQL statements precompiled into a single executable procedure.</span></span>  
  
-   <span data-ttu-id="948d3-107">擴充預存程序：</span><span class="sxs-lookup"><span data-stu-id="948d3-107">Extended stored procedures:</span></span>  
  
     <span data-ttu-id="948d3-108">寫入到擴充預存程序之 SQL Server 開放式資料服務 API 的 C 或 C++ 動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="948d3-108">C or C++ dynamic-link libraries (DLL) written to the SQL Server Open Data Services API for extended stored procedures.</span></span> <span data-ttu-id="948d3-109">開放式資料服務 API 會擴充預存程序的功能以包含 C 或 C++ 程式碼。</span><span class="sxs-lookup"><span data-stu-id="948d3-109">The Open Data Services API extends the capabilities of stored procedures to include C or C++ code.</span></span>  
  
 <span data-ttu-id="948d3-110">執行陳述式時，在資料來源上呼叫預存程序 (而非直接在用戶端應用程式中執行或準備陳述式) 可以提供：</span><span class="sxs-lookup"><span data-stu-id="948d3-110">When executing statements, calling a stored procedure on the data source (instead of directly executing or preparing a statement in the client application) can provide:</span></span>  
  
-   <span data-ttu-id="948d3-111">較高的效能</span><span class="sxs-lookup"><span data-stu-id="948d3-111">Higher performance</span></span>  
  
     <span data-ttu-id="948d3-112">SQL 陳述式會在建立程序時進行剖析和編譯。</span><span class="sxs-lookup"><span data-stu-id="948d3-112">SQL statements are parsed and compiled when procedures are created.</span></span> <span data-ttu-id="948d3-113">接著，這個負擔會在執行程序時儲存起來。</span><span class="sxs-lookup"><span data-stu-id="948d3-113">This overhead is then saved when the procedures are executed.</span></span>  
  
-   <span data-ttu-id="948d3-114">降低的網路負擔</span><span class="sxs-lookup"><span data-stu-id="948d3-114">Reduced network overhead</span></span>  
  
     <span data-ttu-id="948d3-115">執行程序而非跨網路傳送複雜查詢可以減少網路流量。</span><span class="sxs-lookup"><span data-stu-id="948d3-115">Executing a procedure instead of sending complex queries across the network can reduce network traffic.</span></span> <span data-ttu-id="948d3-116">如果 ODBC 應用程式使用 ODBC { CALL } 語法執行預存程序，ODBC 驅動程式會進行額外的最佳化，以排除轉換參數資料的需要。</span><span class="sxs-lookup"><span data-stu-id="948d3-116">If an ODBC application uses the ODBC { CALL } syntax to execute a stored procedure, the ODBC driver makes additional optimizations that eliminate the need to convert parameter data.</span></span>  
  
-   <span data-ttu-id="948d3-117">更好的一致性</span><span class="sxs-lookup"><span data-stu-id="948d3-117">Greater consistency</span></span>  
  
     <span data-ttu-id="948d3-118">如果組織的規則是在中央資源 (例如預存程序) 實作，則這些規則可以進行一次的編碼、測試與偵錯。</span><span class="sxs-lookup"><span data-stu-id="948d3-118">If an organization's rules are implemented in a central resource, such as a stored procedure, they can be coded, tested, and debugged once.</span></span> <span data-ttu-id="948d3-119">接著，各個程式設計師可以使用經過測試的預存程序，而不用開發自己的實作。</span><span class="sxs-lookup"><span data-stu-id="948d3-119">Individual programmers can then use the tested stored procedures instead of developing their own implementations.</span></span>  
  
-   <span data-ttu-id="948d3-120">更好的精確度</span><span class="sxs-lookup"><span data-stu-id="948d3-120">Greater accuracy</span></span>  
  
     <span data-ttu-id="948d3-121">預存程序通常是由具經驗的程式設計師開發，因此這些預存程序會比不同技術層級之程式設計師開發多次的程式碼更有效率，而且錯誤更少。</span><span class="sxs-lookup"><span data-stu-id="948d3-121">Because stored procedures are usually developed by experienced programmers, they tend to be more efficient and have fewer errors than code developed multiple times by programmers of varying skill levels.</span></span>  
  
-   <span data-ttu-id="948d3-122">增加的功能</span><span class="sxs-lookup"><span data-stu-id="948d3-122">Added functionality</span></span>  
  
     <span data-ttu-id="948d3-123">擴充預存程序可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式中未提供的 C 和 C++ 功能。</span><span class="sxs-lookup"><span data-stu-id="948d3-123">Extended stored procedures can use C and C++ features not available in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="948d3-124">如需如何呼叫預存程式的範例，請參閱[&#40;ODBC&#41;處理傳回碼和輸出參數](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="948d3-124">For an example of how to call a stored procedure, see [Process Return Codes and Output Parameters &#40;ODBC&#41;](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="948d3-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="948d3-125">In This Section</span></span>  
  
-   [<span data-ttu-id="948d3-126">呼叫預存程序</span><span class="sxs-lookup"><span data-stu-id="948d3-126">Calling a Stored Procedure</span></span>](calling-a-stored-procedure.md)  
  
-   [<span data-ttu-id="948d3-127">批次預存程序呼叫</span><span class="sxs-lookup"><span data-stu-id="948d3-127">Batching Stored Procedure Calls</span></span>](batching-stored-procedure-calls.md)  
  
-   [<span data-ttu-id="948d3-128">處理預存程序結果</span><span class="sxs-lookup"><span data-stu-id="948d3-128">Processing Stored Procedure Results</span></span>](processing-stored-procedure-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="948d3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="948d3-129">See Also</span></span>  
 <span data-ttu-id="948d3-130">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="948d3-130">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="948d3-131">執行預存程式的 how to 主題 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="948d3-131">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
