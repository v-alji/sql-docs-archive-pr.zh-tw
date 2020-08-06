---
title: SQLGetData |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetData function
ms.assetid: 204848be-8787-45b4-816f-a60ac9d56fcf
author: rothja
ms.author: jroth
ms.openlocfilehash: c351cf7340bc7b0afeb76b139bd75aa429f56e10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584489"
---
# <a name="sqlgetdata"></a><span data-ttu-id="bcc21-102">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="bcc21-102">SQLGetData</span></span>
  <span data-ttu-id="bcc21-103">**SQLGetData**是用來在不系結資料行值的情況下，抓取結果集資料。</span><span class="sxs-lookup"><span data-stu-id="bcc21-103">**SQLGetData** is used to retrieve result set data without binding column values.</span></span> <span data-ttu-id="bcc21-104">可以在相同資料行上連續呼叫**SQLGetData** ，以從具有**text**、 **Ntext**或**image**資料類型的資料行中取出大量資料。</span><span class="sxs-lookup"><span data-stu-id="bcc21-104">**SQLGetData** can be called successively on the same column to retrieve large amounts of data from a column with a **text**, **ntext**, or **image** data type.</span></span>  
  
 <span data-ttu-id="bcc21-105">不會要求應用程式繫結變數來擷取結果集資料。</span><span class="sxs-lookup"><span data-stu-id="bcc21-105">There is no requirement that an application bind variables to fetch result set data.</span></span> <span data-ttu-id="bcc21-106">您可以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用**SQLGetData**，從 Native Client ODBC 驅動程式中取出任何資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="bcc21-106">The data of any column can be retrieved from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver by using **SQLGetData**.</span></span>  
  
 <span data-ttu-id="bcc21-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式不支援使用**SQLGetData**以隨機的資料行順序來取得資料。</span><span class="sxs-lookup"><span data-stu-id="bcc21-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support using **SQLGetData** to retrieve data in random column order.</span></span> <span data-ttu-id="bcc21-108">所有使用**SQLGetData**處理的未系結資料行，都必須具有比結果集中系結資料行更高的資料行序數。</span><span class="sxs-lookup"><span data-stu-id="bcc21-108">All unbound columns processed with **SQLGetData** must have higher column ordinals than the bound columns in the result set.</span></span> <span data-ttu-id="bcc21-109">應用程式必須處理從最低未繫結序數資料行值到最高值的資料。</span><span class="sxs-lookup"><span data-stu-id="bcc21-109">The application must process data from the lowest unbound ordinal column value to the highest.</span></span> <span data-ttu-id="bcc21-110">嘗試從編號序數較低的資料行擷取資料將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bcc21-110">Attempting to retrieve data from a lower ordinally numbered column results in an error.</span></span> <span data-ttu-id="bcc21-111">如果應用程式使用伺服器資料指標來報告結果集資料列，則應用程式可以提取目前的資料列，然後再提取資料行的值。</span><span class="sxs-lookup"><span data-stu-id="bcc21-111">If the application is using server cursors to report result set rows, the application can refetch the current row and then fetch the value of a column.</span></span> <span data-ttu-id="bcc21-112">如果語句是在預設的唯讀、順向資料指標上執行，您必須重新執行語句來備份**SQLGetData**。</span><span class="sxs-lookup"><span data-stu-id="bcc21-112">If a statement is executed on the default read-only, forward-only cursor, you must re-execute the statement to back up **SQLGetData**.</span></span>  
  
 <span data-ttu-id="bcc21-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會使用**SQLGetData**，正確地報告**text**、 **Ntext**和**image**資料的長度。</span><span class="sxs-lookup"><span data-stu-id="bcc21-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver accurately reports the length of **text**, **ntext**, and **image** data retrieved using **SQLGetData**.</span></span> <span data-ttu-id="bcc21-114">應用程式可以充分利用*StrLen_or_IndPtr*參數 return 來快速取出長資料。</span><span class="sxs-lookup"><span data-stu-id="bcc21-114">The application can make good use of the *StrLen_or_IndPtr* parameter return to retrieve long data rapidly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bcc21-115">對於大數數值型別， *StrLen_or_IndPtr*將會在資料截斷的情況下傳回 SQL_NO_TOTAL。</span><span class="sxs-lookup"><span data-stu-id="bcc21-115">For large value types, *StrLen_or_IndPtr* will return SQL_NO_TOTAL in cases of data truncation.</span></span>  
  
## <a name="sqlgetdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="bcc21-116">增強型日期和時間功能的 SQLGetData 支援</span><span class="sxs-lookup"><span data-stu-id="bcc21-116">SQLGetData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="bcc21-117">日期/時間類型的結果資料行值會轉換，如[從 SQL 轉換為 C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="bcc21-117">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).</span></span>  
  
 <span data-ttu-id="bcc21-118">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc21-118">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgetdata-support-for-large-clr-udts"></a><span data-ttu-id="bcc21-119">大型 CLR UDT 的 SQLGetData 支援</span><span class="sxs-lookup"><span data-stu-id="bcc21-119">SQLGetData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="bcc21-120">**SQLGetData**支援 (udt) 的大型 CLR 使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="bcc21-120">**SQLGetData** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="bcc21-121">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="bcc21-121">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcc21-122">範例</span><span class="sxs-lookup"><span data-stu-id="bcc21-122">Example</span></span>  
  
```  
SQLHDBC     hDbc = NULL;  
SQLHSTMT    hStmt = NULL;  
long        lEmpID;  
PBYTE       pPicture;  
SQLINTEGER  pIndicators[2];  
  
// Get an environment, connection, and so on.  
...  
  
// Get a statement handle and execute a command.  
SQLAllocHandle(SQL_HANDLE_STMT, hDbc, &hStmt);  
  
if (SQLExecDirect(hStmt,  
    (SQLCHAR*) "SELECT EmployeeID, Photo FROM Employees",  
    SQL_NTS) == SQL_ERROR)  
    {  
    // Handle error and return.  
    }  
  
// Retrieve data from row set.  
SQLBindCol(hStmt, 1, SQL_C_LONG, (SQLPOINTER) &lEmpID, sizeof(long),  
    &pIndicators[0]);  
  
while (SQLFetch(hStmt) == SQL_SUCCESS)  
    {  
    cout << "EmployeeID: " << lEmpID << "\n";  
  
    // Call SQLGetData to determine the amount of data that's waiting.  
    if (SQLGetData(hStmt, 2, SQL_C_BINARY, pPicture, 0, &pIndicators[1])  
        == SQL_SUCCESS_WITH_INFO)  
        {  
        cout << "Photo size: " pIndicators[1] << "\n\n";  
  
        // Get all the data at once.  
        pPicture = new BYTE[pIndicators[1]];  
        if (SQLGetData(hStmt, 2, SQL_C_DEFAULT, pPicture,  
            pIndicators[1], &pIndicators[1]) != SQL_SUCCESS)  
            {  
            // Handle error and continue.  
            }  
  
        delete [] pPicture;  
        }  
    else  
        {  
        // Handle error on attempt to get data length.  
        }  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcc21-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcc21-123">See Also</span></span>  
 <span data-ttu-id="bcc21-124">[SQLGetData 函式](https://go.microsoft.com/fwlink/?LinkId=59350) </span><span class="sxs-lookup"><span data-stu-id="bcc21-124">[SQLGetData Function](https://go.microsoft.com/fwlink/?LinkId=59350) </span></span>  
 [<span data-ttu-id="bcc21-125">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="bcc21-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
