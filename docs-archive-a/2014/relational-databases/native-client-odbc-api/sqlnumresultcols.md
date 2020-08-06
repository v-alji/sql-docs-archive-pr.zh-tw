---
title: SQLNumResultCols |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: rothja
ms.author: jroth
ms.openlocfilehash: 45e72165eef621dc377b02ed3d2e7e1e3cf7ab8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606266"
---
# <a name="sqlnumresultcols"></a><span data-ttu-id="32d84-102">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="32d84-102">SQLNumResultCols</span></span>
  <span data-ttu-id="32d84-103">對於執行的語句， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式不會造訪伺服器來報告結果集中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="32d84-103">For executed statements, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not visit the server to report the number of columns in a result set.</span></span> <span data-ttu-id="32d84-104">在此情況下， `SQLNumResultCols` 並不會造成伺服器往返。</span><span class="sxs-lookup"><span data-stu-id="32d84-104">In this case, `SQLNumResultCols` does not cause a server roundtrip.</span></span> <span data-ttu-id="32d84-105">如同[SQLDescribeCol](sqldescribecol.md)和[SQLColAttribute](sqlcolattribute.md)， `SQLNumResultCols` 在已備妥但未執行的語句上呼叫，會產生伺服器往返。</span><span class="sxs-lookup"><span data-stu-id="32d84-105">Like [SQLDescribeCol](sqldescribecol.md) and [SQLColAttribute](sqlcolattribute.md), calling `SQLNumResultCols` on prepared but not executed statements generates a server roundtrip.</span></span>  
  
 <span data-ttu-id="32d84-106">當 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或陳述式批次傳回多個結果資料列集時，結果集資料行的數目有可能從某個資料列集變成另一個資料列集。</span><span class="sxs-lookup"><span data-stu-id="32d84-106">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statement batch returns multiple result row sets, it is possible for the number of result set columns to change from one set to another.</span></span> <span data-ttu-id="32d84-107">`SQLNumResultCols`應針對每個集合呼叫。</span><span class="sxs-lookup"><span data-stu-id="32d84-107">`SQLNumResultCols` should be called for each set.</span></span> <span data-ttu-id="32d84-108">當資料行數目變更時，應用程式應該在提取資料列結果以前先重新繫結資料值。</span><span class="sxs-lookup"><span data-stu-id="32d84-108">When the number of columns changes, the application should rebind data values prior to fetching row results.</span></span> <span data-ttu-id="32d84-109">如需有關處理多個結果集傳回的詳細資訊，請參閱[SQLMoreResults](sqlmoreresults.md)。</span><span class="sxs-lookup"><span data-stu-id="32d84-109">For more information about handling multiple result set returns, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="32d84-110">從開始，database engine 的改進 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可讓 SQLNumResultCols 取得預期結果的更精確描述。</span><span class="sxs-lookup"><span data-stu-id="32d84-110">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow SQLNumResultCols to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="32d84-111">這些更精確的結果可能與舊版的 SQLNumResultCols 所傳回的值不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="32d84-111">These more accurate results may differ from the values returned by SQLNumResultCols in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="32d84-112">如需詳細資訊，請參閱[中繼資料探索](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="32d84-112">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d84-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32d84-113">See Also</span></span>  
 <span data-ttu-id="32d84-114">[SQLNumResultCols 函式](https://go.microsoft.com/fwlink/?LinkId=59359) </span><span class="sxs-lookup"><span data-stu-id="32d84-114">[SQLNumResultCols Function](https://go.microsoft.com/fwlink/?LinkId=59359) </span></span>  
 [<span data-ttu-id="32d84-115">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="32d84-115">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
