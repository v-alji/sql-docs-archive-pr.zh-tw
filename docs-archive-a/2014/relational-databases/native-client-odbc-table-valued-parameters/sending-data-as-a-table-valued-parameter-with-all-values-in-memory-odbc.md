---
title: 使用記憶體中的所有值，將資料當做資料表值參數傳送 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), sending data to a stored procedure with all values in memory
ms.assetid: 8b96282f-00d5-4e28-8111-0a87ae6d7781
author: rothja
ms.author: jroth
ms.openlocfilehash: f53e129ea49b1faa08be5247c51b5e74353e2f31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708258"
---
# <a name="sending-data-as-a-table-valued-parameter-with-all-values-in-memory-odbc"></a><span data-ttu-id="c8f55-102">使用記憶體中的所有值，將資料當做資料表值參數傳送 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="c8f55-102">Sending Data as a Table-Valued Parameter with All Values in Memory (ODBC)</span></span>
  <span data-ttu-id="c8f55-103">本主題描述所有的值都在記憶體中時，如何將資料當做資料表值參數傳送至預存程序。</span><span class="sxs-lookup"><span data-stu-id="c8f55-103">This topic describes how to send data to a stored procedure as a table-valued parameter when all values are in memory.</span></span> <span data-ttu-id="c8f55-104">如需示範資料表值參數的另一個範例，請參閱[使用資料表值參數 &#40;ODBC&#41;](table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c8f55-104">For another sample demonstrating table-valued parameters, see [Use Table-Valued Parameters &#40;ODBC&#41;](table-valued-parameters-odbc.md).</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="c8f55-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="c8f55-105">Prerequisite</span></span>  
 <span data-ttu-id="c8f55-106">此程序假設已在伺服器上執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="c8f55-106">This procedure assumes that the following [!INCLUDE[tsql](../../includes/tsql-md.md)] has been executed on the server:</span></span>  
  
```  
create type TVParam as table(ProdCode integer, Qty integer)  
create procedure TVPOrderEntry(@CustCode varchar(5), @Items TVPParam,   
            @OrdNo integer output, @OrdDate datetime output)  
         as   
         set @OrdDate = GETDATE();  
         insert into TVPOrd (OrdDate, CustCode)   
values (@OrdDate, @CustCode) output OrdNo);   
         select @OrdNo = SCOPE_IDENTITY();   
         insert into TVPItem (OrdNo, ProdCode, Qty)  
select @OrdNo, @Items.ProdCode, @Items.Qty   
from @Items  
```  
  
## <a name="to-send-the-data"></a><span data-ttu-id="c8f55-107">傳送資料</span><span class="sxs-lookup"><span data-stu-id="c8f55-107">To Send the Data</span></span>  
  
1.  <span data-ttu-id="c8f55-108">宣告 SQL 參數的變數。</span><span class="sxs-lookup"><span data-stu-id="c8f55-108">Declare variables for the SQL parameters.</span></span> <span data-ttu-id="c8f55-109">在此情況下，資料表值會完整保留在記憶體中，因此會將資料表值資料行的值宣告為陣列。</span><span class="sxs-lookup"><span data-stu-id="c8f55-109">In this case, the table value is held entirely in memory, so values for the columns of the table value are declared as arrays.</span></span>  
  
    ```  
    SQLRETURN r;  
    // Variables for SQL parameters.  
    #define ITEM_ARRAY_SIZE 20  
  
    SQLCHAR CustCode[6];  
    SQLCHAR *TVP = (SQLCHAR *) "TVParam";  
    SQLINTEGER ProdCode[ITEM_ARRAY_SIZE], Qty[ITEM_ARRAY_SIZE];  
    SQLINTEGER OrdNo;  
    char OrdDate[23];  
  
    // Variables for indicator/length variables associated with parameters.  
    SQLLEN cbCustCode, cbTVP, cbProdCode[ITEM_ARRAY_SIZE], cbQty[ITEM_ARRAY_SIZE], cbOrdNo, cbOrdDate;  
    ```  
  
2.  <span data-ttu-id="c8f55-110">繫結參數。</span><span class="sxs-lookup"><span data-stu-id="c8f55-110">Bind the parameters.</span></span> <span data-ttu-id="c8f55-111">使用資料表值參數時，繫結參數是一個兩個階段的程序。</span><span class="sxs-lookup"><span data-stu-id="c8f55-111">Binding parameters is a two stage process when table-valued parameters are used.</span></span> <span data-ttu-id="c8f55-112">在第一個階段中，預存程序的 step 參數會以正常的方式繫結，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c8f55-112">In the first stage, step parameters for the stored procedure are bound in the normal way, as follows.</span></span>  
  
    ```  
    // Bind parameters for call to TVPOrderEntryDirect.  
    // 1 - Custcode input  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_VARCHAR, SQL_C_CHAR, 5, 0, CustCode, sizeof(CustCode), &cbCustCode);  
  
    // 2 - Items TVP  
    r = SQLBindParameter(hstmt,   
        2,// ParameterNumber  
        SQL_PARAM_INPUT,// InputOutputType  
        SQL_C_DEFAULT,// ValueType   
        SQL_SS_TABLE,// Parametertype  
        ITEM_ARRAY_SIZE,// ColumnSize: For a table-valued parameter this is the row array size.  
        0,// DecimalDigits: For a table-valued parameter this is always 0.   
        TVP,// ParameterValuePtr: For a table-valued parameter this is the type name of the   
    //table-valued parameter, and also a token returned by SQLParamData.  
        SQL_NTS,// BufferLength: For a table-valued parameter this is the length of the type name or SQL_NTS.  
        &cbTVP);// StrLen_or_IndPtr: For a table-valued parameter this is the number of rows actually used.  
  
    // 3 - OrdNo output  
    r = SQLBindParameter(hstmt, 3, SQL_PARAM_OUTPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, &OrdNo,  
       sizeof(SQLINTEGER), &cbOrdNo);  
    // 4 - OrdDate output  
    r = SQLBindParameter(hstmt, 4, SQL_PARAM_OUTPUT,SQL_TYPE_TIMESTAMP, SQL_C_CHAR, 23, 3, &OrdDate,   
       sizeof(OrdDate), &cbOrdDate);  
    ```  
  
3.  <span data-ttu-id="c8f55-113">參數繫結的第二個階段是建立資料表值參數的資料行。</span><span class="sxs-lookup"><span data-stu-id="c8f55-113">The second stage of parameter binding is to bind the columns for the table-valued parameter.</span></span> <span data-ttu-id="c8f55-114">參數焦點會先設定為資料表值參數的序數。</span><span class="sxs-lookup"><span data-stu-id="c8f55-114">The parameter focus is first set to the ordinal of the table-valued parameter.</span></span> <span data-ttu-id="c8f55-115">然後，使用 SQLBindParameter 來系結資料表值的資料行，其方式與預存程式的參數相同，但具有 ParameterNumber 的資料行序數。</span><span class="sxs-lookup"><span data-stu-id="c8f55-115">Then columns of the table value are bound by using SQLBindParameter in the same way as they would be if they were parameters of the stored procedure, but with column ordinals for ParameterNumber.</span></span> <span data-ttu-id="c8f55-116">如果有其他資料表值參數，則會輪流將焦點設定為每個資料表值參數，並繫結其資料行。</span><span class="sxs-lookup"><span data-stu-id="c8f55-116">If there were more table-valued parameters, we would set the focus to each in turn and bind their columns.</span></span> <span data-ttu-id="c8f55-117">最後，參數焦點就會重設為 0。</span><span class="sxs-lookup"><span data-stu-id="c8f55-117">Finally, the parameter focus is reset to 0.</span></span>  
  
    ```  
    // Bind columns for the table-valued parameter (param 2).  
    // First set focus on param 2.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 2, SQL_IS_INTEGER);  
  
    // Col 1 - ProdCode  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, ProdCode, sizeof(SQLINTEGER), cbProdCode);  
    // Col 2 - Qty  
    r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, Qty, sizeof(SQLINTEGER), cbQty);  
  
    // Reset param focus.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 0, SQL_IS_INTEGER);  
    ```  
  
4.  <span data-ttu-id="c8f55-118">擴充參數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c8f55-118">Populate the parameter buffers.</span></span> <span data-ttu-id="c8f55-119">`cbTVP` 會設定為要傳送到伺服器的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="c8f55-119">`cbTVP` is set to the number of rows to be sent to the server.</span></span>  
  
    ```  
    // Populate parameters.  
    cbTVP = 0; // Number of rows available for input.  
    strcpy_s((char *) CustCode, sizeof(CustCode), "CUST1"); cbCustCode = SQL_NTS;  
  
    ProdCode[cbTVP] = 1215;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 5;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input  
  
    ProdCode[cbTVP] = 1017;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 2;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input.  
    ```  
  
5.  <span data-ttu-id="c8f55-120">呼叫程序：</span><span class="sxs-lookup"><span data-stu-id="c8f55-120">Call the procedure:</span></span>  
  
    ```  
    // Call the procedure.  
    r = SQLExecDirect(hstmt, (SQLCHAR *) "{call TVPOrderEntry(?, ?, ?, ?)}",SQL_NTS);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c8f55-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8f55-121">See Also</span></span>  
 [<span data-ttu-id="c8f55-122">ODBC 資料表值參數程式設計範例</span><span class="sxs-lookup"><span data-stu-id="c8f55-122">ODBC Table-Valued Parameter Programming Examples</span></span>](../../database-engine/dev-guide/odbc-table-valued-parameter-programming-examples.md)  
  
  
