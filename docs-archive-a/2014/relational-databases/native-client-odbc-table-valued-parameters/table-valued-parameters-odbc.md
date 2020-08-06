---
title: ODBC)  (的資料表值參數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC)
- ODBC, table-valued parameters
ms.assetid: ef06cd13-18e2-4c65-8ede-c3955d820e54
author: rothja
ms.author: jroth
ms.openlocfilehash: fedfd63f7cbafd68d39aeb62dd29c046df8ab100
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585340"
---
# <a name="table-valued-parameters-odbc"></a><span data-ttu-id="36415-102">資料表值參數 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="36415-102">Table-Valued Parameters (ODBC)</span></span>
  <span data-ttu-id="36415-103">ODBC 對資料表值參數的支援可讓用戶端應用程式有效率地將參數化資料傳送給伺服器，其方式是使用一個呼叫來傳送多個資料列給伺服器。</span><span class="sxs-lookup"><span data-stu-id="36415-103">ODBC support for table-valued parameters lets a client application send parameterized data to the server more efficiently, by sending multiple rows to the server with one call.</span></span>  
  
 <span data-ttu-id="36415-104">如需伺服器上資料表值參數的詳細資訊，請參閱[使用資料表值參數 &#40;資料庫引擎&#41;](../tables/use-table-valued-parameters-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="36415-104">For information about table-valued parameters on the server, see [Use Table-Valued Parameters &#40;Database Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).</span></span>  
  
 <span data-ttu-id="36415-105">在 ODBC 中，這是您可以將資料表值參數傳送給伺服器的兩種方式：</span><span class="sxs-lookup"><span data-stu-id="36415-105">In ODBC, there are two ways that you can send table-valued parameters to the server:</span></span>  
  
-   <span data-ttu-id="36415-106">呼叫 SQLExecDirect 或 SQLExecute 時，所有資料表值參數資料都可以在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="36415-106">All the table-valued parameter data can be in memory at the time SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="36415-107">如果資料表值中有多個資料列，這些資料會儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="36415-107">This data is stored in arrays if there are multiple rows in the table-value.</span></span>  
  
-   <span data-ttu-id="36415-108">呼叫 SQLExecDirect 或 SQLExecute 時，應用程式可以指定資料表值參數的資料執行中。</span><span class="sxs-lookup"><span data-stu-id="36415-108">An application can specify data-at-execution for a table-valued parameter when SQLExecDirect or SQLExecute is called.</span></span> <span data-ttu-id="36415-109">在此情況下，可以在批次中提供資料表值的資料列，或是一次一個來減少記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="36415-109">In this case, rows of data for the table-value can be provided in batches, or one at a time to reduce memory requirements.</span></span>  
  
 <span data-ttu-id="36415-110">第一個選項可讓預存程序封裝更多商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="36415-110">The first option enables stored procedures to encapsulate more business logic.</span></span> <span data-ttu-id="36415-111">例如，將其他項目當做資料表值參數傳遞時，單一預存程序可封裝整個訂單輸入交易。</span><span class="sxs-lookup"><span data-stu-id="36415-111">For example, a single stored procedure could encapsulate a whole order entry transaction when the order items are passed as a table-valued parameter.</span></span> <span data-ttu-id="36415-112">這個選項非常有效率，因為只需要單一次往返伺服器。</span><span class="sxs-lookup"><span data-stu-id="36415-112">This option is very efficient, because only a single round trip to the server is required.</span></span> <span data-ttu-id="36415-113">另外，您也可以使用不同程序來個別處理訂單標頭和訂單項目，這樣需要在用戶端與伺服器之間有更多的程式碼和更複雜的合約。</span><span class="sxs-lookup"><span data-stu-id="36415-113">Alternatively, you could use different procedures to handle the order header and order items separately, which would require more code and a more complex contract between the client and server.</span></span>  
  
 <span data-ttu-id="36415-114">第二個方法針對具有極大量資料的大量作業提供了一種有效率的機制。</span><span class="sxs-lookup"><span data-stu-id="36415-114">The second method provides an efficient mechanism for bulk operations with very large amounts of data.</span></span> <span data-ttu-id="36415-115">這可讓應用程式以資料流方式將資料列傳送到伺服器，而不必先在記憶體中緩衝處理所有的資料。</span><span class="sxs-lookup"><span data-stu-id="36415-115">This enables an application to stream rows of data to the server without having to buffer them all in memory first.</span></span>  
  
 <span data-ttu-id="36415-116">當您建立資料表變數時，可以建立條件約束和主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="36415-116">You can create constraints and primary keys when you create the table variable.</span></span> <span data-ttu-id="36415-117">條件約束是確保資料表中的資料符合特定需求的一種很好方式。</span><span class="sxs-lookup"><span data-stu-id="36415-117">Constraints are a good way to ensure that the data in a table meets specific requirements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36415-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="36415-118">In This Section</span></span>  
 [<span data-ttu-id="36415-119">使用 ODBC 資料表值參數</span><span class="sxs-lookup"><span data-stu-id="36415-119">Uses of ODBC Table-Valued Parameters</span></span>](uses-of-odbc-table-valued-parameters.md)  
 <span data-ttu-id="36415-120">描述資料表值參數和 ODBC 的主要使用者案例。</span><span class="sxs-lookup"><span data-stu-id="36415-120">Describes the primary user scenarios for table-valued parameters and ODBC.</span></span>  
  
 [<span data-ttu-id="36415-121">資料表值參數的 ODBC SQL 類型</span><span class="sxs-lookup"><span data-stu-id="36415-121">ODBC SQL Type for Table-Valued Parameters</span></span>](odbc-sql-type-for-table-valued-parameters.md)  
 <span data-ttu-id="36415-122">描述 SQL_SS_TABLE 類型。</span><span class="sxs-lookup"><span data-stu-id="36415-122">Describes the SQL_SS_TABLE type.</span></span> <span data-ttu-id="36415-123">這是可支援資料表值參數的新 ODBC SQL 類型。</span><span class="sxs-lookup"><span data-stu-id="36415-123">This is a new ODBC SQL type that supports table-valued parameters.</span></span>  
  
 [<span data-ttu-id="36415-124">資料表值參數描述項欄位</span><span class="sxs-lookup"><span data-stu-id="36415-124">Table-Valued Parameter Descriptor Fields</span></span>](table-valued-parameter-descriptor-fields.md)  
 <span data-ttu-id="36415-125">描述可支援資料表值參數的描述項欄位。</span><span class="sxs-lookup"><span data-stu-id="36415-125">Describes descriptor fields that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="36415-126">資料表值參數組成資料行的描述項欄位</span><span class="sxs-lookup"><span data-stu-id="36415-126">Descriptor Fields for Table-Valued Parameter Constituent Columns</span></span>](descriptor-fields-for-table-valued-parameter-constituent-columns.md)  
 <span data-ttu-id="36415-127">描述對於資料表值參數具有意義的描述項欄位。</span><span class="sxs-lookup"><span data-stu-id="36415-127">Describes descriptor fields that have meaning for table-valued parameters.</span></span>  
  
 [<span data-ttu-id="36415-128">資料表值參數診斷記錄欄位</span><span class="sxs-lookup"><span data-stu-id="36415-128">Table-Valued Parameter Diagnostic Record Fields</span></span>](table-valued-parameter-diagnostic-record-fields.md)  
 <span data-ttu-id="36415-129">描述已經加入到診斷記錄中來支援資料表值參數的兩個診斷欄位。</span><span class="sxs-lookup"><span data-stu-id="36415-129">Describes two diagnostic fields that have been added to diagnostic records to support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="36415-130">影響資料表值參數的陳述式屬性</span><span class="sxs-lookup"><span data-stu-id="36415-130">Statement Attributes that Affect Table-Valued Parameters</span></span>](statement-attributes-that-affect-table-valued-parameters.md)  
 <span data-ttu-id="36415-131">描述可讓資料表值參數資料行得以處理的新描述項標頭欄位。</span><span class="sxs-lookup"><span data-stu-id="36415-131">Describes a new descriptor header field that enables table-valued parameters columns to be addressed.</span></span>  
  
 [<span data-ttu-id="36415-132">資料表值參數和資料行值的繫結與資料傳送</span><span class="sxs-lookup"><span data-stu-id="36415-132">Binding and Data Transfer of Table-Valued Parameters and Column Values</span></span>](binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
 <span data-ttu-id="36415-133">描述參數繫結以及如何將資料表值參數傳遞給伺服器。</span><span class="sxs-lookup"><span data-stu-id="36415-133">Describes parameter binding and how to pass a table-valued parameter to the server.</span></span>  
  
 [<span data-ttu-id="36415-134">已備妥之陳述式的資料表值參數中繼資料</span><span class="sxs-lookup"><span data-stu-id="36415-134">Table-Valued Parameter Metadata for Prepared Statements</span></span>](table-valued-parameter-metadata-for-prepared-statements.md)  
 <span data-ttu-id="36415-135">描述應用程式要如何針對預備好的程序呼叫取得中繼資料。</span><span class="sxs-lookup"><span data-stu-id="36415-135">Describes how an application can obtain metadata for a prepared procedure call.</span></span>  
  
 [<span data-ttu-id="36415-136">其他資料表值參數中繼資料</span><span class="sxs-lookup"><span data-stu-id="36415-136">Additional Table-Valued Parameter Metadata</span></span>](additional-table-valued-parameter-metadata.md)  
 <span data-ttu-id="36415-137">描述如何使用 SQLProcedureColumns、SQLTables 和 SQLColumns 來取得資料表值參數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="36415-137">Describes how to use SQLProcedureColumns, SQLTables, and SQLColumns to retrieve metadata for a table-valued parameter.</span></span>  
  
 [<span data-ttu-id="36415-138">資料表值參數資料轉換及其他錯誤和警告</span><span class="sxs-lookup"><span data-stu-id="36415-138">Table-Valued Parameter Data Conversion and Other Errors and Warnings</span></span>](table-valued-parameter-data-conversion-and-other-errors-and-warnings.md)  
 <span data-ttu-id="36415-139">描述如何處理有關資料表值參數資料行值的錯誤。</span><span class="sxs-lookup"><span data-stu-id="36415-139">Describes how to process errors on table-valued parameter column values.</span></span>  
  
 [<span data-ttu-id="36415-140">跨版本相容性</span><span class="sxs-lookup"><span data-stu-id="36415-140">Cross-Version Compatibility</span></span>](cross-version-compatibility.md)  
 <span data-ttu-id="36415-141">描述當早於 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 版本的用戶端或伺服器使用資料表值參數時，可能發生的衝突。</span><span class="sxs-lookup"><span data-stu-id="36415-141">Describes conflicts that can occur when table-valued parameters are used by a client or server of a version earlier than [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].</span></span>  
  
 [<span data-ttu-id="36415-142">ODBC 資料表值參數 API 摘要</span><span class="sxs-lookup"><span data-stu-id="36415-142">ODBC Table-Valued Parameter API Summary</span></span>](odbc-table-valued-parameter-api-summary.md)  
 <span data-ttu-id="36415-143">列出可支援資料表值參數的 ODBC 函數。</span><span class="sxs-lookup"><span data-stu-id="36415-143">Lists the ODBC functions that support table-valued parameters.</span></span>  
  
 [<span data-ttu-id="36415-144">ODBC 資料表值參數程式設計範例</span><span class="sxs-lookup"><span data-stu-id="36415-144">ODBC Table-Valued Parameter Programming Examples</span></span>](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
 <span data-ttu-id="36415-145">描述如何執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="36415-145">Describes how to perform common tasks.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36415-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36415-146">See Also</span></span>  
 <span data-ttu-id="36415-147">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="36415-147">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="36415-148">資料表值參數 &#40;SQL Server Native Client&#41;</span><span class="sxs-lookup"><span data-stu-id="36415-148">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](../native-client/features/table-valued-parameters-sql-server-native-client.md)  
  
  
