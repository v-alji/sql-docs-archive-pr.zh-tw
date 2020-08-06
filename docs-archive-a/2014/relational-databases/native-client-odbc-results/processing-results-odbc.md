---
title: " (ODBC) 處理結果 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: rothja
ms.author: jroth
ms.openlocfilehash: 72c0d15231b07a23f10a03b0fca270d1d014891c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709330"
---
# <a name="processing-results-odbc"></a><span data-ttu-id="f8537-102">處理結果 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="f8537-102">Processing Results (ODBC)</span></span>
  <span data-ttu-id="f8537-103">應用程式提交 SQL 陳述式後，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會傳回產生的任何資料，做為一個或多個結果集。</span><span class="sxs-lookup"><span data-stu-id="f8537-103">After an application submits a SQL statement, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns any resulting data as one or more result sets.</span></span> <span data-ttu-id="f8537-104">結果集是一組符合查詢準則的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="f8537-104">A result set is a set of rows and columns that match the criteria of the query.</span></span> <span data-ttu-id="f8537-105">SELECT 陳述式、目錄函數以及某些預存程序會產生表格形式的結果集，供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="f8537-105">SELECT statements, catalog functions, and some stored procedures produce a result set made available to an application in tabular form.</span></span> <span data-ttu-id="f8537-106">如果已執行的 SQL 陳述式是一個預存程序、包含多個命令的批次，或包含關鍵字的 SELECT 陳述式，則會有多個要處理的結果集。</span><span class="sxs-lookup"><span data-stu-id="f8537-106">If the executed SQL statement is a stored procedure, a batch containing multiple commands, or a SELECT statement containing keywords, there will be multiple result sets to process.</span></span>  
  
 <span data-ttu-id="f8537-107">ODBC 目錄函數也可以擷取資料。</span><span class="sxs-lookup"><span data-stu-id="f8537-107">ODBC catalog functions also can retrieve data.</span></span> <span data-ttu-id="f8537-108">例如， [SQLColumns](../native-client-odbc-api/sqlcolumns.md)會抓取資料來源中有關資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="f8537-108">For example, [SQLColumns](../native-client-odbc-api/sqlcolumns.md) retrieves data about columns in the data source.</span></span> <span data-ttu-id="f8537-109">這些結果集可以包含零或多個資料列。</span><span class="sxs-lookup"><span data-stu-id="f8537-109">These result sets can contain zero or more rows.</span></span>  
  
 <span data-ttu-id="f8537-110">GRANT 或 REVOKE 之類的 SQL 陳述式不會傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="f8537-110">Other SQL statements, such as GRANT or REVOKE, do not return result sets.</span></span> <span data-ttu-id="f8537-111">針對這些語句， **SQLExecute**或**SQLExecDirect**的傳回碼通常是語句成功的唯一指示。</span><span class="sxs-lookup"><span data-stu-id="f8537-111">For these statements, the return code from **SQLExecute** or **SQLExecDirect** is usually the only indication the statement was successful.</span></span>  
  
 <span data-ttu-id="f8537-112">每個 INSERT、UPDATE 和 DELETE 陳述式都會傳回只包含受到修改影響之資料列數目的結果集。</span><span class="sxs-lookup"><span data-stu-id="f8537-112">Each INSERT, UPDATE, and DELETE statement returns a result set containing only the number of rows affected by the modification.</span></span> <span data-ttu-id="f8537-113">當應用程式呼叫[SQLRowCount](../native-client-odbc-api/sqlrowcount.md)時，就可以使用此計數。</span><span class="sxs-lookup"><span data-stu-id="f8537-113">This count is made available when application calls [SQLRowCount](../native-client-odbc-api/sqlrowcount.md).</span></span> <span data-ttu-id="f8537-114">ODBC 3。*x*應用程式必須呼叫**SQLRowCount**來取得結果集或[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) ，才能將它取消。</span><span class="sxs-lookup"><span data-stu-id="f8537-114">ODBC 3.*x* applications must either call **SQLRowCount** to retrieve the result set or [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to cancel it.</span></span> <span data-ttu-id="f8537-115">當應用程式執行包含多個 INSERT、UPDATE 或 DELETE 子句的批次或預存程式時，必須使用**SQLRowCount**來處理每個修改語句的結果集，或使用**SQLMoreResults**來取消。</span><span class="sxs-lookup"><span data-stu-id="f8537-115">When an application executes a batch or stored procedure containing multiple INSERT, UPDATE, or DELETE statements, the result set from each modification statement must be processed using **SQLRowCount** or cancelled using **SQLMoreResults**.</span></span> <span data-ttu-id="f8537-116">在批次或預存程序中加入 SET NOCOUNT ON 陳述式可以取消這些計數。</span><span class="sxs-lookup"><span data-stu-id="f8537-116">These counts can be cancelled by including a SET NOCOUNT ON statement in the batch or stored procedure.</span></span>  
  
 <span data-ttu-id="f8537-117">Transact-SQL 包括 SET NOCOUNT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8537-117">Transact-SQL includes the SET NOCOUNT statement.</span></span> <span data-ttu-id="f8537-118">當 NOCOUNT 選項設定為 on 時，SQL Server 不會傳回受語句影響的資料列計數，而**SQLRowCount**會傳回0。</span><span class="sxs-lookup"><span data-stu-id="f8537-118">When the NOCOUNT option is set on, SQL Server does not return the counts of the rows affected by a statement and **SQLRowCount** returns 0.</span></span> <span data-ttu-id="f8537-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式版本引進驅動程式特有的[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)選項 SQL_SOPT_SS_NOCOUNT_STATUS，以報告 NOCOUNT 選項為開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="f8537-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver version introduces a driver-specific [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) option, SQL_SOPT_SS_NOCOUNT_STATUS, to report on whether the NOCOUNT option is on or off.</span></span> <span data-ttu-id="f8537-120">每當**SQLRowCount**傳回0時，應用程式應該測試 SQL_SOPT_SS_NOCOUNT_STATUS。</span><span class="sxs-lookup"><span data-stu-id="f8537-120">Anytime **SQLRowCount** returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="f8537-121">如果傳回 SQL_NC_ON，則**SQLRowCount**中0的值只表示 SQL Server 未傳回資料列計數。</span><span class="sxs-lookup"><span data-stu-id="f8537-121">If SQL_NC_ON is returned, the value of 0 from **SQLRowCount** only indicates that SQL Server has not returned a row count.</span></span> <span data-ttu-id="f8537-122">如果傳回 SQL_NC_OFF，則表示 NOCOUNT 是 OFF，而**SQLRowCount**的值則表示語句不會影響任何資料列。</span><span class="sxs-lookup"><span data-stu-id="f8537-122">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from **SQLRowCount** indicates that the statement did not affect any rows.</span></span> <span data-ttu-id="f8537-123">當 SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF 時，應用程式不應該顯示**SQLRowCount**的值。</span><span class="sxs-lookup"><span data-stu-id="f8537-123">Applications should not display the value of **SQLRowCount** when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="f8537-124">大型批次或預存程序可能包含多個 SET NOCOUNT 陳述式，因此，程式設計人員無法假設 SQL_SOPT_SS_NOCOUNT_STATUS 仍為常數。</span><span class="sxs-lookup"><span data-stu-id="f8537-124">Large batches or stored procedures may contain multiple SET NOCOUNT statements so programmers cannot assume SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="f8537-125">每次**SQLRowCount**傳回0時，應該測試此選項。</span><span class="sxs-lookup"><span data-stu-id="f8537-125">The option should be tested each time **SQLRowCount** returns 0.</span></span>  
  
 <span data-ttu-id="f8537-126">其他數個 Transact-SQL 陳述式會在訊息 (而非結果集) 中傳回其資料。</span><span class="sxs-lookup"><span data-stu-id="f8537-126">Several other Transact-SQL statements return their data in messages rather than result sets.</span></span> <span data-ttu-id="f8537-127">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式收到這些訊息時，它會傳回 SQL_SUCCESS_WITH_INFO，讓應用程式知道有參考用訊息。</span><span class="sxs-lookup"><span data-stu-id="f8537-127">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver receives these messages, it returns SQL_SUCCESS_WITH_INFO to let the application know that informational messages are available.</span></span> <span data-ttu-id="f8537-128">然後，應用程式可以呼叫**SQLGetDiagRec**來取得這些訊息。</span><span class="sxs-lookup"><span data-stu-id="f8537-128">The application can then call **SQLGetDiagRec** to retrieve these messages.</span></span> <span data-ttu-id="f8537-129">使用此種方式運作的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式為：</span><span class="sxs-lookup"><span data-stu-id="f8537-129">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that work this way are:</span></span>  
  
-   <span data-ttu-id="f8537-130">DBCC</span><span class="sxs-lookup"><span data-stu-id="f8537-130">DBCC</span></span>  
  
-   <span data-ttu-id="f8537-131">SET SHOWPLAN (適用於舊版的 SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f8537-131">SET SHOWPLAN (available with earlier versions of SQL Server)</span></span>  
  
-   <span data-ttu-id="f8537-132">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="f8537-132">SET STATISTICS</span></span>  
  
-   <span data-ttu-id="f8537-133">PRINT</span><span class="sxs-lookup"><span data-stu-id="f8537-133">PRINT</span></span>  
  
-   <span data-ttu-id="f8537-134">RAISERROR</span><span class="sxs-lookup"><span data-stu-id="f8537-134">RAISERROR</span></span>  
  
 <span data-ttu-id="f8537-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會在嚴重性為11（含）以上的 RAISERROR 上傳回 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="f8537-135">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns SQL_ERROR on a RAISERROR with a severity of 11 or higher.</span></span> <span data-ttu-id="f8537-136">如果 RAISERROR 的嚴重性為 19 以上，也會中斷連接。</span><span class="sxs-lookup"><span data-stu-id="f8537-136">If the severity of the RAISERROR is 19 or higher, the connection is also dropped.</span></span>  
  
 <span data-ttu-id="f8537-137">若要從 SQL 陳述式處理結果集，應用程式會：</span><span class="sxs-lookup"><span data-stu-id="f8537-137">To process the result sets from an SQL statement, the application:</span></span>  
  
-   <span data-ttu-id="f8537-138">決定結果集的特性。</span><span class="sxs-lookup"><span data-stu-id="f8537-138">Determines the characteristics of the result set.</span></span>  
  
-   <span data-ttu-id="f8537-139">將資料行繫結到程式變數。</span><span class="sxs-lookup"><span data-stu-id="f8537-139">Binds the columns to program variables.</span></span>  
  
-   <span data-ttu-id="f8537-140">擷取單一值、整個資料列的值，或多個資料列的值。</span><span class="sxs-lookup"><span data-stu-id="f8537-140">Retrieves a single value, an entire row of values, or multiple rows of values.</span></span>  
  
-   <span data-ttu-id="f8537-141">測試是否有其他結果集，如果有，回到決定新結果集的特性。</span><span class="sxs-lookup"><span data-stu-id="f8537-141">Tests to see if there are more result sets, and if so, loops back to determining the characteristics of the new result set.</span></span>  
  
 <span data-ttu-id="f8537-142">從資料來源擷取資料列，然後將其傳回應用程式的過程稱為提取。</span><span class="sxs-lookup"><span data-stu-id="f8537-142">The process of retrieving rows from the data source and returning them to the application is called fetching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f8537-143">本節內容</span><span class="sxs-lookup"><span data-stu-id="f8537-143">In This Section</span></span>  
  
-   [<span data-ttu-id="f8537-144">判斷結果集的特性 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="f8537-144">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [<span data-ttu-id="f8537-145">指派儲存體</span><span class="sxs-lookup"><span data-stu-id="f8537-145">Assigning Storage</span></span>](assigning-storage.md)  
  
-   [<span data-ttu-id="f8537-146">提取結果資料</span><span class="sxs-lookup"><span data-stu-id="f8537-146">Fetching Result Data</span></span>](fetching-result-data.md)  
  
-   [<span data-ttu-id="f8537-147">&#40;ODBC&#41;對應資料類型</span><span class="sxs-lookup"><span data-stu-id="f8537-147">Mapping Data Types &#40;ODBC&#41;</span></span>](mapping-data-types-odbc.md)  
  
-   [<span data-ttu-id="f8537-148">資料類型使用方式</span><span class="sxs-lookup"><span data-stu-id="f8537-148">Data Type Usage</span></span>](data-type-usage.md)  
  
-   [<span data-ttu-id="f8537-149">字元資料的自動轉譯</span><span class="sxs-lookup"><span data-stu-id="f8537-149">Autotranslation of Character Data</span></span>](autotranslation-of-character-data.md)  
  
## <a name="see-also"></a><span data-ttu-id="f8537-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8537-150">See Also</span></span>  
 <span data-ttu-id="f8537-151">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="f8537-151">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="f8537-152">處理結果如何 &#40;ODBC&#41;的 how to 主題</span><span class="sxs-lookup"><span data-stu-id="f8537-152">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
