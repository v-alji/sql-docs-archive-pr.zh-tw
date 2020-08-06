---
title: SQLFetchScroll |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: rothja
ms.author: jroth
ms.openlocfilehash: eecf9714a97577ff490b642cee5b9c380333e40b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594079"
---
# <a name="sqlfetchscroll"></a><span data-ttu-id="ee08c-102">SQLFetchScroll</span><span class="sxs-lookup"><span data-stu-id="ee08c-102">SQLFetchScroll</span></span>
  <span data-ttu-id="ee08c-103">**SQLFetchScroll**會將一個資料列集傳回給應用程式。</span><span class="sxs-lookup"><span data-stu-id="ee08c-103">**SQLFetchScroll** returns one row set of data to the application.</span></span> <span data-ttu-id="ee08c-104">資料列集的大小是使用[SQLSetStmtAttr](sqlsetstmtattr.md)設定的。</span><span class="sxs-lookup"><span data-stu-id="ee08c-104">The size of the row set is set using [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span> <span data-ttu-id="ee08c-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式支援所有定義的提取指示 (例如，SQL_FETCH_RELATIVE) ，但有下列限制：</span><span class="sxs-lookup"><span data-stu-id="ee08c-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports all defined fetch instructions (for example, SQL_FETCH_RELATIVE) with the following limitations:</span></span>  
  
-   <span data-ttu-id="ee08c-106">如果有針對陳述式而定義順向資料指標，則需要 SQL_FETCH_NEXT，而且以任何其他格式嘗試提取會導致錯誤傳回。</span><span class="sxs-lookup"><span data-stu-id="ee08c-106">If a forward-only cursor is defined for the statement, SQL_FETCH_NEXT is required and attempts to fetch in any other fashion will result in an error return.</span></span>  
  
-   <span data-ttu-id="ee08c-107">僅針對靜態和索引鍵集導向的資料指標支援 SQL_FETCH_BOOKMARK。</span><span class="sxs-lookup"><span data-stu-id="ee08c-107">SQL_FETCH_BOOKMARK is supported for static and keyset-driven cursors only.</span></span>  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="ee08c-108">增強型日期和時間功能的 SQLFetchScroll 支援</span><span class="sxs-lookup"><span data-stu-id="ee08c-108">SQLFetchScroll Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="ee08c-109">日期/時間類型的結果資料行值會轉換，如[從 SQL 轉換為 C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="ee08c-109">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="ee08c-110">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="ee08c-110">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a><span data-ttu-id="ee08c-111">大型 CLR UDT 的 SQLFetchScroll 支援</span><span class="sxs-lookup"><span data-stu-id="ee08c-111">SQLFetchScroll Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="ee08c-112">**SQLFetchScroll**支援 (udt) 的大型 CLR 使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="ee08c-112">**SQLFetchScroll** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="ee08c-113">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="ee08c-113">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee08c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee08c-114">See Also</span></span>  
 <span data-ttu-id="ee08c-115">[SQLFetchScroll 函式](https://go.microsoft.com/fwlink/?LinkId=59343) </span><span class="sxs-lookup"><span data-stu-id="ee08c-115">[SQLFetchScroll Function](https://go.microsoft.com/fwlink/?LinkId=59343) </span></span>  
 [<span data-ttu-id="ee08c-116">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee08c-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
