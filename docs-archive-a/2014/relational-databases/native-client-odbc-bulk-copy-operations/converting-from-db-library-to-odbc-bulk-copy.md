---
title: 從 DB-LIBRARY 轉換成 ODBC 大量複製 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- converting DB-Library to ODBC bulk copy
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [ODBC], DB-Library bulk copy
- ODBC, bulk copy operations
- DB-Library bulk copy
ms.assetid: 0bc15bdb-f19f-4537-ac6c-f249f42cf07f
author: rothja
ms.author: jroth
ms.openlocfilehash: 866900606e582f08695fd4695a1098f34fb2b426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598350"
---
# <a name="converting-from-db-library-to-odbc-bulk-copy"></a><span data-ttu-id="7d24e-102">從 DB-Library 轉換成 ODBC 大量複製</span><span class="sxs-lookup"><span data-stu-id="7d24e-102">Converting from DB-Library to ODBC Bulk Copy</span></span>
  <span data-ttu-id="7d24e-103">將 DB-LIBRARY 大量複製程式轉換成 ODBC 很簡單，因為 Native Client ODBC 驅動程式所支援的大量複製函數與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] db-library 大量複製函數類似，但有下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7d24e-103">Converting a DB-Library bulk copy program to ODBC is easy because the bulk copy functions supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver are similar to the DB-Library bulk copy functions, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="7d24e-104">DB-Library 應用程式會將指向 DBPROCESS 結構的指標當做大量複製函數的第一個參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="7d24e-104">DB-Library applications pass a pointer to a DBPROCESS structure as the first parameter of bulk copy functions.</span></span> <span data-ttu-id="7d24e-105">在 ODBC 應用程式中，DBPROCESS 指標會由 ODBC 連接控制代碼所取代。</span><span class="sxs-lookup"><span data-stu-id="7d24e-105">In ODBC applications, the DBPROCESS pointer is replaced with an ODBC connection handle.</span></span>  
  
-   <span data-ttu-id="7d24e-106">DB-LIBRARY 應用程式會在連接之前呼叫**BCP_SETL** ，以在 DBPROCESS 上啟用大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="7d24e-106">DB-Library applications call **BCP_SETL** before connecting to enable bulk copy operations on a DBPROCESS.</span></span> <span data-ttu-id="7d24e-107">ODBC 應用程式會改為在連接之前呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以在連接控制碼上啟用大量作業：</span><span class="sxs-lookup"><span data-stu-id="7d24e-107">ODBC applications instead call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) before connecting to enable bulk operations on a connection handle:</span></span>  
  
    ```  
    SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP,  
        (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
    ```  
  
-   <span data-ttu-id="7d24e-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式不支援 db-library 訊息和錯誤處理常式; 您必須呼叫**SQLGetDiagRec** ，以取得 ODBC 大量複製函數所引發的錯誤和訊息。</span><span class="sxs-lookup"><span data-stu-id="7d24e-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support DB-Library message and error handlers; you must call **SQLGetDiagRec** to get errors and messages raised by the ODBC bulk copy functions.</span></span> <span data-ttu-id="7d24e-109">大量複製函數的 ODBC 版本會傳回標準的大量複製傳回碼 SUCCEED 或 FAILED，而非 ODBC 樣式的傳回碼，例如 SQL_SUCCESS 或 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="7d24e-109">The ODBC versions of bulk copy functions return the standard bulk copy return codes of SUCCEED or FAILED, not ODBC-style return codes, such as SQL_SUCCESS or SQL_ERROR.</span></span>  
  
-   <span data-ttu-id="7d24e-110">針對 DB-LIBRARY [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen*參數所指定的值，與 ODBC **bcp_bind**_cbData_參數的轉譯方式不同。</span><span class="sxs-lookup"><span data-stu-id="7d24e-110">The values specified for the DB-Library [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)*varlen* parameter are interpreted differently than the ODBC **bcp_bind**_cbData_ parameter.</span></span>  
  
    |<span data-ttu-id="7d24e-111">指示的條件</span><span class="sxs-lookup"><span data-stu-id="7d24e-111">Condition indicated</span></span>|<span data-ttu-id="7d24e-112">DB-LIBRARY *varlen*值</span><span class="sxs-lookup"><span data-stu-id="7d24e-112">DB-Library *varlen* value</span></span>|<span data-ttu-id="7d24e-113">ODBC *cbData*值</span><span class="sxs-lookup"><span data-stu-id="7d24e-113">ODBC *cbData* value</span></span>|  
    |-------------------------|--------------------------------|-------------------------|  
    |<span data-ttu-id="7d24e-114">提供了 Null 值</span><span class="sxs-lookup"><span data-stu-id="7d24e-114">Null values supplied</span></span>|<span data-ttu-id="7d24e-115">0</span><span class="sxs-lookup"><span data-stu-id="7d24e-115">0</span></span>|<span data-ttu-id="7d24e-116">-1 (SQL_NULL_DATA)</span><span class="sxs-lookup"><span data-stu-id="7d24e-116">-1 (SQL_NULL_DATA)</span></span>|  
    |<span data-ttu-id="7d24e-117">提供了變數資料</span><span class="sxs-lookup"><span data-stu-id="7d24e-117">Variable data supplied</span></span>|<span data-ttu-id="7d24e-118">-1</span><span class="sxs-lookup"><span data-stu-id="7d24e-118">-1</span></span>|<span data-ttu-id="7d24e-119">-10 (SQL_VARLEN_DATA)</span><span class="sxs-lookup"><span data-stu-id="7d24e-119">-10 (SQL_VARLEN_DATA)</span></span>|  
    |<span data-ttu-id="7d24e-120">長度為零的字元或二進位字串</span><span class="sxs-lookup"><span data-stu-id="7d24e-120">Zero length character or binary string</span></span>|<span data-ttu-id="7d24e-121">NA</span><span class="sxs-lookup"><span data-stu-id="7d24e-121">NA</span></span>|<span data-ttu-id="7d24e-122">0</span><span class="sxs-lookup"><span data-stu-id="7d24e-122">0</span></span>|  
  
     <span data-ttu-id="7d24e-123">在 DB-LIBRARY 中， *varlen*值-1 表示正在提供可變長度的資料，而在 ODBC *cbData*中會將它解讀為表示只提供 Null 值。</span><span class="sxs-lookup"><span data-stu-id="7d24e-123">In DB-Library, a *varlen* value of -1 indicates that variable length data is being supplied, which in the ODBC *cbData* is interpreted to mean that only NULL values are being supplied.</span></span> <span data-ttu-id="7d24e-124">將任何-1 的 DB-LIBRARY *varlen*規格變更為 SQL_VARLEN_DATA，並將任何0的*varlen*規格變更為 SQL_Null_DATA。</span><span class="sxs-lookup"><span data-stu-id="7d24e-124">Change any DB-Library *varlen* specifications of -1 to SQL_VARLEN_DATA and any *varlen* specifications of 0 to SQL_NULL_DATA.</span></span>  
  
-   <span data-ttu-id="7d24e-125">DB-LIBRARY **bcp \_ colfmt**_file \_ collen_和 ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*CbUserData*與上面所述的**bcp_bind**_varlen_和*cbData*參數有相同的問題。</span><span class="sxs-lookup"><span data-stu-id="7d24e-125">The DB-Library **bcp\_colfmt**_file\_collen_ and the ODBC [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)*cbUserData* have the same issue as the **bcp_bind**_varlen_ and *cbData* parameters noted above.</span></span> <span data-ttu-id="7d24e-126">將任何-1 的 DB-LIBRARY *file_collen*規格變更為 SQL_VARLEN_DATA，並將任何*file_collen*規格0變更為 SQL_Null_DATA。</span><span class="sxs-lookup"><span data-stu-id="7d24e-126">Change any DB-Library *file_collen* specifications of -1 to SQL_VARLEN_DATA and any *file_collen* specifications of 0 to SQL_NULL_DATA.</span></span>  
  
-   <span data-ttu-id="7d24e-127">ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)函數的*iValue*參數是 void 指標。</span><span class="sxs-lookup"><span data-stu-id="7d24e-127">The *iValue* parameter of the ODBC [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) function is a void pointer.</span></span> <span data-ttu-id="7d24e-128">在 DB-LIBRARY 中， *iValue*是整數。</span><span class="sxs-lookup"><span data-stu-id="7d24e-128">In DB-Library, *iValue* was an integer.</span></span> <span data-ttu-id="7d24e-129">將 ODBC *iValue*的值轉換為 void \*。</span><span class="sxs-lookup"><span data-stu-id="7d24e-129">Cast the values for the ODBC *iValue* to void \*.</span></span>  
  
-   <span data-ttu-id="7d24e-130">**Bcp_control**選項 BCPMAXERRS 指定大量複製作業失敗之前，有多少個個別的資料列可以有錯誤。</span><span class="sxs-lookup"><span data-stu-id="7d24e-130">The **bcp_control** option BCPMAXERRS specifies how many individual rows can have errors before a bulk copy operation fails.</span></span> <span data-ttu-id="7d24e-131">BCPMAXERRS 的預設值為 0 (在 ODBC 版本的**bcp_control**的 db-library 版本和10中的第一個錯誤) 失敗。</span><span class="sxs-lookup"><span data-stu-id="7d24e-131">The default for BCPMAXERRS is 0 (fail on first error) in the DB-Library version of **bcp_control** and 10 in the ODBC version.</span></span> <span data-ttu-id="7d24e-132">相依于預設值0來終止大量複製作業的 DB-LIBRARY 應用程式，必須變更為呼叫 ODBC **bcp_control**以將 BCPMAXERRS 設定為0。</span><span class="sxs-lookup"><span data-stu-id="7d24e-132">DB-Library applications that depend on the default of 0 to terminate a bulk copy operation must be changed to call the ODBC **bcp_control** to set BCPMAXERRS to 0.</span></span>  
  
-   <span data-ttu-id="7d24e-133">ODBC **bcp_control**函數支援下列不受 db-library 版本的**bcp_control**支援的選項：</span><span class="sxs-lookup"><span data-stu-id="7d24e-133">The ODBC **bcp_control** function supports the following options not supported by the DB-Library version of **bcp_control**:</span></span>  
  
    -   <span data-ttu-id="7d24e-134">BCPODBC</span><span class="sxs-lookup"><span data-stu-id="7d24e-134">BCPODBC</span></span>  
  
         <span data-ttu-id="7d24e-135">當設定為 TRUE 時，指定以字元格式儲存的**datetime**和**Smalldatetime**值會有 ODBC 時間戳記 escape 序列前置詞和後置詞。</span><span class="sxs-lookup"><span data-stu-id="7d24e-135">When set to TRUE, specifies that **datetime** and **smalldatetime** values saved in character format will have the ODBC timestamp escape sequence prefix and suffix.</span></span> <span data-ttu-id="7d24e-136">這僅適用於 BCP_OUT 作業。</span><span class="sxs-lookup"><span data-stu-id="7d24e-136">This only applies to BCP_OUT operations.</span></span>  
  
         <span data-ttu-id="7d24e-137">當 BCPODBC.BCP 設定為 FALSE 時，轉換為字元字串的**日期時間**值會輸出為：</span><span class="sxs-lookup"><span data-stu-id="7d24e-137">With BCPODBC set to FALSE, a **datetime** value converted to a character string is output as:</span></span>  
  
        ```  
        1997-01-01 00:00:00.000  
        ```  
  
         <span data-ttu-id="7d24e-138">當 BCPODBC.BCP 設定為 TRUE 時，相同的**datetime**值會輸出為：</span><span class="sxs-lookup"><span data-stu-id="7d24e-138">With BCPODBC set to TRUE, the same **datetime** value is output as:</span></span>  
  
        ```  
        {ts '1997-01-01 00:00:00.000' }  
        ```  
  
    -   <span data-ttu-id="7d24e-139">BCPKEEPIDENTITY</span><span class="sxs-lookup"><span data-stu-id="7d24e-139">BCPKEEPIDENTITY</span></span>  
  
         <span data-ttu-id="7d24e-140">當設定為 TRUE 時，這個選項會指定大量複製函數插入提供給含有識別條件約束之資料行的資料值。</span><span class="sxs-lookup"><span data-stu-id="7d24e-140">When set to TRUE, specifies that bulk copy functions insert data values supplied for columns with identity constraints.</span></span> <span data-ttu-id="7d24e-141">如果沒有設定，就會為插入的資料列產生新的識別值。</span><span class="sxs-lookup"><span data-stu-id="7d24e-141">If this is not set, new identity values are generated for the inserted rows.</span></span>  
  
    -   <span data-ttu-id="7d24e-142">BCPHINTS</span><span class="sxs-lookup"><span data-stu-id="7d24e-142">BCPHINTS</span></span>  
  
         <span data-ttu-id="7d24e-143">指定各種大量複製最佳化。</span><span class="sxs-lookup"><span data-stu-id="7d24e-143">Specifies various bulk copy optimizations.</span></span> <span data-ttu-id="7d24e-144">這個選項無法在 6.5 或舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上使用。</span><span class="sxs-lookup"><span data-stu-id="7d24e-144">This option cannot be used on 6.5 or earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="7d24e-145">BCPFILECP</span><span class="sxs-lookup"><span data-stu-id="7d24e-145">BCPFILECP</span></span>  
  
         <span data-ttu-id="7d24e-146">指定大量複製檔案的字碼頁。</span><span class="sxs-lookup"><span data-stu-id="7d24e-146">Specifies the code page of the bulk copy file.</span></span>  
  
    -   <span data-ttu-id="7d24e-147">BCPUNICODEFILE</span><span class="sxs-lookup"><span data-stu-id="7d24e-147">BCPUNICODEFILE</span></span>  
  
         <span data-ttu-id="7d24e-148">指定字元模式大量複製檔案為 Unicode 檔案。</span><span class="sxs-lookup"><span data-stu-id="7d24e-148">Specifies that a character mode bulk copy file is a Unicode file.</span></span>  
  
-   <span data-ttu-id="7d24e-149">ODBC **bcp_colfmt**函數不支援 SQLCHAR 的*file_type*指標，因為它與 ODBC SQLCHAR typedef 衝突。</span><span class="sxs-lookup"><span data-stu-id="7d24e-149">The ODBC **bcp_colfmt** function does not support the *file_type* indicator of SQLCHAR because it conflicts with the ODBC SQLCHAR typedef.</span></span> <span data-ttu-id="7d24e-150">請改用 SQLCHARACTER 來進行**bcp_colfmt**。</span><span class="sxs-lookup"><span data-stu-id="7d24e-150">Use SQLCHARACTER instead for **bcp_colfmt**.</span></span>  
  
-   <span data-ttu-id="7d24e-151">在 ODBC 版本的大量複製函式中，在字元字串中使用**datetime**和**Smalldatetime**值的格式為 yyyy-mm-dd hh： MM： ss 的 odbc 格式。**Smalldatetime**值使用 yyyy-mm-dd hh： mm： SS 的 ODBC 格式。</span><span class="sxs-lookup"><span data-stu-id="7d24e-151">In the ODBC versions of bulk copy functions, the format for working with **datetime** and **smalldatetime** values in character strings is the ODBC format of yyyy-mm-dd hh:mm:ss.sss; **smalldatetime** values use the ODBC format of yyyy-mm-dd hh:mm:ss.</span></span>  
  
     <span data-ttu-id="7d24e-152">大量複製函數的 DB-LIBRARY 版本會使用數種格式，接受字元字串中的**datetime**和**Smalldatetime**值：</span><span class="sxs-lookup"><span data-stu-id="7d24e-152">The DB-Library versions of the bulk copy functions accept **datetime** and **smalldatetime** values in character strings using several formats:</span></span>  
  
    -   <span data-ttu-id="7d24e-153">預設格式為*mmm dd yyyy hh： mmxx* ，其中*xx*為 AM 或 PM。</span><span class="sxs-lookup"><span data-stu-id="7d24e-153">The default format is *mmm dd yyyy hh:mmxx* where *xx* is either AM or PM.</span></span>  
  
    -   <span data-ttu-id="7d24e-154">以 DB-LIBRARY **dbconvert**函數支援的任何格式的**datetime**和**Smalldatetime**字元字串。</span><span class="sxs-lookup"><span data-stu-id="7d24e-154">**datetime** and **smalldatetime** character strings in any format supported by the DB-Library **dbconvert** function.</span></span>  
  
    -   <span data-ttu-id="7d24e-155">在用戶端網路公用程式的 [DB-LIBRARY**選項**] 索引標籤上核取 [**使用國際設定**] 方塊時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，db-library 大量複製函數也會接受針對用戶端電腦登錄的地區設定所定義之地區日期格式的日期。</span><span class="sxs-lookup"><span data-stu-id="7d24e-155">When the **Use international settings** box is checked on the DB-Library **Options** tab of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Network Utility, the DB-Library bulk copy functions also accept dates in the regional date format defined for the locale setting of the client computer registry.</span></span>  
  
     <span data-ttu-id="7d24e-156">DB-LIBRARY 大量複製函數不接受 ODBC **datetime**和**Smalldatetime**格式。</span><span class="sxs-lookup"><span data-stu-id="7d24e-156">The DB-Library bulk copy functions do not accept the ODBC **datetime** and **smalldatetime** formats.</span></span>  
  
     <span data-ttu-id="7d24e-157">如果 SQL_SOPT_SS_REGIONALIZE 陳述式屬性設定為 SQL_RE_ON，ODBC 大量複製函數會接受採用針對用戶端電腦登錄地區設定所定義之地區日期格式的日期。</span><span class="sxs-lookup"><span data-stu-id="7d24e-157">If the SQL_SOPT_SS_REGIONALIZE statement attribute is set to SQL_RE_ON, the ODBC bulk copy functions accept dates in the regional date format defined for the locale setting of the client computer registry.</span></span>  
  
-   <span data-ttu-id="7d24e-158">以字元格式輸出**money**值時，ODBC 大量複製函數會提供四位數的精確度，而且不會有逗號分隔符號;DB-LIBRARY 版本只提供兩位數的精確度，並包含逗號分隔符號。</span><span class="sxs-lookup"><span data-stu-id="7d24e-158">When outputting **money** values in character format, ODBC bulk copy functions supply four digits of precision and no comma separators; DB-Library versions only supply two digits of precision and include the comma separators.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d24e-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d24e-159">See Also</span></span>  
 <span data-ttu-id="7d24e-160">[&#40;ODBC&#41;執行大量複製作業](performing-bulk-copy-operations-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="7d24e-160">[Performing Bulk Copy Operations &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md) </span></span>  
 [<span data-ttu-id="7d24e-161">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="7d24e-161">Bulk Copy Functions</span></span>](../native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
