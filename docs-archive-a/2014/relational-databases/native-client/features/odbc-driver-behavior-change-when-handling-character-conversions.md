---
title: 處理字元轉換時的 ODBC 驅動程式行為變更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 682a232a-bf89-4849-88a1-95b2fbac1467
author: rothja
ms.author: jroth
ms.openlocfilehash: 5334b4268559ba155a53b3be655d87f7867779df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698065"
---
# <a name="odbc-driver-behavior-change-when-handling-character-conversions"></a><span data-ttu-id="c3104-102">ODBC 驅動程式在處理字元轉換上的行為變更</span><span class="sxs-lookup"><span data-stu-id="c3104-102">ODBC Driver Behavior Change When Handling Character Conversions</span></span>
  <span data-ttu-id="c3104-103">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]Native CLIENT ODBC 驅動程式 ( # A0) 變更了 SQL_WCHAR \* (NCHAR/Nvarchar/Nvarchar (max) # A6 和 SQL_CHAR \* (CHAR/VARCHAR/NARCHAR (max) # A10 轉換的方式。</span><span class="sxs-lookup"><span data-stu-id="c3104-103">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC Driver (SQLNCLI11.dll) changed how it does of SQL_WCHAR\* (NCHAR/NVARCHAR/NVARCHAR(MAX)) and SQL_CHAR\* (CHAR/VARCHAR/NARCHAR(MAX)) conversions.</span></span> <span data-ttu-id="c3104-104">當使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC 驅動程式時，ODBC 函數如 SQLGetData、SQLBindCol、SQLBindParameter 等傳回的長度/指標參數將會是 (-4) SQL_NO_TOTAL。</span><span class="sxs-lookup"><span data-stu-id="c3104-104">ODBC functions, such as SQLGetData, SQLBindCol, SQLBindParameter, return (-4) SQL_NO_TOTAL as the length/indicator parameter when using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client ODBC driver.</span></span> <span data-ttu-id="c3104-105">舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式以往傳回長度值，而這可能不正確。</span><span class="sxs-lookup"><span data-stu-id="c3104-105">Prior versions of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver returned a length value, which can be incorrect.</span></span>  
  
## <a name="sqlgetdata-behavior"></a><span data-ttu-id="c3104-106">SQLGetData 行為</span><span class="sxs-lookup"><span data-stu-id="c3104-106">SQLGetData Behavior</span></span>  
 <span data-ttu-id="c3104-107">許多 Windows 函數都可讓您指定緩衝區大小為 0，且傳回的長度會是所傳回資料的大小。</span><span class="sxs-lookup"><span data-stu-id="c3104-107">Many Windows functions let you specify a buffer size of 0 and the returned length is the size of the returned data.</span></span> <span data-ttu-id="c3104-108">以下的寫法對 Windows 程式設計人員而言應已司空見慣：</span><span class="sxs-lookup"><span data-stu-id="c3104-108">The following pattern is common for Windows programmers:</span></span>  
  
```  
int iSize = 0;  
BYTE * pBuffer = NULL;  
GetMyFavoriteAPI(pBuffer, &iSize);   // Returns needed size in iSize  
pBuffer = new BYTE[iSize];   // Allocate buffer   
GetMyFavoriteAPI(pBuffer, &iSize);   // Retrieve actual data  
```  
  
 <span data-ttu-id="c3104-109">不過，此案例中不應該使用**SQLGetData** 。</span><span class="sxs-lookup"><span data-stu-id="c3104-109">However, **SQLGetData** should not be used in this scenario.</span></span> <span data-ttu-id="c3104-110">請勿使用這種寫法：</span><span class="sxs-lookup"><span data-stu-id="c3104-110">The following pattern should not be used:</span></span>  
  
```  
// bad  
int iSize = 0;  
WCHAR * pBuffer = NULL;  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)0x1, 0, &iSize);   // Get storage size needed  
pBuffer = new WCHAR[(iSize/sizeof(WCHAR)) + 1];   // Allocate buffer  
SQLGetData(hstmt, SQL_W_CHAR, ...., (SQLPOINTER*)pBuffer, iSize, &iSize);   // Retrieve data  
```  
  
 <span data-ttu-id="c3104-111">**SQLGetData**只能呼叫來取得實際資料的區塊。</span><span class="sxs-lookup"><span data-stu-id="c3104-111">**SQLGetData** can only be called to retrieve chunks of actual data.</span></span> <span data-ttu-id="c3104-112">不支援使用**SQLGetData**來取得資料大小。</span><span class="sxs-lookup"><span data-stu-id="c3104-112">Using **SQLGetData** to get the size of data is not unsupported.</span></span>  
  
 <span data-ttu-id="c3104-113">以下說明當您使用不正確的寫法時，驅動程式變更所造成的影響。</span><span class="sxs-lookup"><span data-stu-id="c3104-113">The following shows the impact of the driver change when you use the incorrect pattern.</span></span> <span data-ttu-id="c3104-114">此應用程式將查詢 `varchar` 資料行並以 Unicode (SQL_UNICODE/SQL_WCHAR) 的形式進行繫結：</span><span class="sxs-lookup"><span data-stu-id="c3104-114">This application queries a `varchar` column and binding as Unicode (SQL_UNICODE/SQL_WCHAR):</span></span>  
  
 <span data-ttu-id="c3104-115">查詢`select convert(varchar(36), '123')`</span><span class="sxs-lookup"><span data-stu-id="c3104-115">Query:  `select convert(varchar(36), '123')`</span></span>  
  
```  
SQLGetData(hstmt, SQL_WCHAR, ....., (SQLPOINTER*) 0x1, 0 , &iSize);   // Attempting to determine storage size needed  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c3104-116">Native Client ODBC 驅動程式版本</span><span class="sxs-lookup"><span data-stu-id="c3104-116">Native Client ODBC Driver version</span></span>|<span data-ttu-id="c3104-117">長度或指標結果</span><span class="sxs-lookup"><span data-stu-id="c3104-117">Length or Indicator Outcome</span></span>|<span data-ttu-id="c3104-118">描述</span><span class="sxs-lookup"><span data-stu-id="c3104-118">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="c3104-119">Native Client 或更早版本</span><span class="sxs-lookup"><span data-stu-id="c3104-119">Native Client or earlier</span></span>|<span data-ttu-id="c3104-120">6</span><span class="sxs-lookup"><span data-stu-id="c3104-120">6</span></span>|<span data-ttu-id="c3104-121">驅動程式誤認為只要長度 \* 2 即可將 CHAR 轉換成 WCHAR。</span><span class="sxs-lookup"><span data-stu-id="c3104-121">The driver incorrectly assumed that converting CHAR to WCHAR could be accomplished as length \* 2.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="c3104-122">Native Client (11.0.2100.60 版) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c3104-122">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="c3104-123">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="c3104-123">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="c3104-124">驅動程式不會再假設從 CHAR 轉換成 WCHAR 或 WCHAR 到 CHAR 是 (乘) \* 2 或 (除以) /2 動作。</span><span class="sxs-lookup"><span data-stu-id="c3104-124">The driver no longer assumes that converting from CHAR to WCHAR or WCHAR to CHAR is a (multiply) \*2 or (divide)/2 action.</span></span><br /><br /> <span data-ttu-id="c3104-125">呼叫**SQLGetData**不再傳回預期轉換的長度。</span><span class="sxs-lookup"><span data-stu-id="c3104-125">Calling **SQLGetData** no longer returns the length of the expected conversion.</span></span> <span data-ttu-id="c3104-126">驅動程式將偵測出這是 CHAR 與 WCHAR 之間的相互轉換，並且傳回 (-4) SQL_NO_TOTAL 而不至於會有 \*2 或 /2 的錯誤行為。</span><span class="sxs-lookup"><span data-stu-id="c3104-126">The driver detects the conversion to or from CHAR and WCHAR and returns (-4) SQL_NO_TOTAL instead of \*2 or /2 behavior that could be incorrect.</span></span>|  
  
 <span data-ttu-id="c3104-127">使用**SQLGetData**來取出資料的區塊。</span><span class="sxs-lookup"><span data-stu-id="c3104-127">Use **SQLGetData** to retrieve the chunks of the data.</span></span> <span data-ttu-id="c3104-128">(虛擬程式碼如下所示)</span><span class="sxs-lookup"><span data-stu-id="c3104-128">(Pseudo code shown:)</span></span>  
  
```  
while( (SQL_SUCCESS or SQL_SUCCESS_WITH_INFO) == SQLFetch(...) ) {  
   SQLNumCols(...iTotalCols...)  
   for(int iCol = 1; iCol < iTotalCols; iCol++) {  
      WCHAR* pBufOrig, pBuffer = new WCHAR[100];  
      SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get original chunk  
      while(NOT ALL DATA RETREIVED (SQL_NO_TOTAL, ...) ) {  
         pBuffer += 50;   // Advance buffer for data retrieved  
         // May need to realloc the buffer when you reach current size  
         SQLGetData(.... iCol ... pBuffer, 100, &iSize);   // Get next chunk  
      }  
   }  
}  
```  
  
## <a name="sqlbindcol-behavior"></a><span data-ttu-id="c3104-129">SQLBindCol 行為</span><span class="sxs-lookup"><span data-stu-id="c3104-129">SQLBindCol Behavior</span></span>  
 <span data-ttu-id="c3104-130">查詢`select convert(varchar(36), '1234567890')`</span><span class="sxs-lookup"><span data-stu-id="c3104-130">Query:  `select convert(varchar(36), '1234567890')`</span></span>  
  
```  
SQLBindCol(... SQL_W_CHAR, ...)   // Only bound a buffer of WCHAR[4] - Expecting String Data Right Truncation behavior  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c3104-131">Native Client ODBC 驅動程式版本</span><span class="sxs-lookup"><span data-stu-id="c3104-131">Native Client ODBC Driver version</span></span>|<span data-ttu-id="c3104-132">長度或指標結果</span><span class="sxs-lookup"><span data-stu-id="c3104-132">Length or Indicator Outcome</span></span>|<span data-ttu-id="c3104-133">描述</span><span class="sxs-lookup"><span data-stu-id="c3104-133">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="c3104-134">Native Client 或更早版本</span><span class="sxs-lookup"><span data-stu-id="c3104-134">Native Client or earlier</span></span>|<span data-ttu-id="c3104-135">20</span><span class="sxs-lookup"><span data-stu-id="c3104-135">20</span></span>|<span data-ttu-id="c3104-136">-   **SQLFetch**會報告資料右側有截斷。</span><span class="sxs-lookup"><span data-stu-id="c3104-136">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="c3104-137">-Length 是傳回的資料長度，而不是所儲存的 (假設 \* 2 CHAR WCHAR 轉換，這對圖像) 而言可能不正確。</span><span class="sxs-lookup"><span data-stu-id="c3104-137">-   Length is the length of the data returned, not what was stored (assumes \*2 CHAR to WCHAR conversion which can be incorrect for glyphs).</span></span><br /><span data-ttu-id="c3104-138">-儲存在 buffer 中的資料是 123 \ 0。</span><span class="sxs-lookup"><span data-stu-id="c3104-138">-   Data stored in buffer is 123\0.</span></span> <span data-ttu-id="c3104-139">緩衝區一定是以 NULL 結尾。</span><span class="sxs-lookup"><span data-stu-id="c3104-139">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="c3104-140">Native Client (11.0.2100.60 版) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c3104-140">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="c3104-141">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="c3104-141">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="c3104-142">-   **SQLFetch**會報告資料右側有截斷。</span><span class="sxs-lookup"><span data-stu-id="c3104-142">-   **SQLFetch** reports that there is a truncation on the right side of the data.</span></span><br /><span data-ttu-id="c3104-143">-Length 表示-4 (SQL_NO_TOTAL) ，因為其餘的資料並未轉換。</span><span class="sxs-lookup"><span data-stu-id="c3104-143">-   Length indicates -4 (SQL_NO_TOTAL) because the rest of the data was not converted.</span></span><br /><span data-ttu-id="c3104-144">-儲存在緩衝區中的資料是 123 \ 0。</span><span class="sxs-lookup"><span data-stu-id="c3104-144">-   Data stored in the buffer is 123\0.</span></span> <span data-ttu-id="c3104-145">- 緩衝區一定是以 NULL 結尾。</span><span class="sxs-lookup"><span data-stu-id="c3104-145">- Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="sqlbindparameter-output-parameter-behavior"></a><span data-ttu-id="c3104-146">SQLBindParameter (OUTPUT 參數行為)</span><span class="sxs-lookup"><span data-stu-id="c3104-146">SQLBindParameter (OUTPUT Parameter Behavior)</span></span>  
 <span data-ttu-id="c3104-147">查詢`create procedure spTest @p1 varchar(max) OUTPUT`</span><span class="sxs-lookup"><span data-stu-id="c3104-147">Query:  `create procedure spTest @p1 varchar(max) OUTPUT`</span></span>  
  
 `select @p1 = replicate('B', 1234)`  
  
```  
SQLBindParameter(... SQL_W_CHAR, ...)   // Only bind up to first 64 characters  
```  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="c3104-148">Native Client ODBC 驅動程式版本</span><span class="sxs-lookup"><span data-stu-id="c3104-148">Native Client ODBC Driver version</span></span>|<span data-ttu-id="c3104-149">長度或指標結果</span><span class="sxs-lookup"><span data-stu-id="c3104-149">Length or Indicator Outcome</span></span>|<span data-ttu-id="c3104-150">描述</span><span class="sxs-lookup"><span data-stu-id="c3104-150">Description</span></span>|  
|-----------------------------------------------------------------|---------------------------------|-----------------|  
|[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] <span data-ttu-id="c3104-151">Native Client 或更早版本</span><span class="sxs-lookup"><span data-stu-id="c3104-151">Native Client or earlier</span></span>|<span data-ttu-id="c3104-152">2468</span><span class="sxs-lookup"><span data-stu-id="c3104-152">2468</span></span>|<span data-ttu-id="c3104-153">-   **SQLFetch**不會傳回更多可用的資料。</span><span class="sxs-lookup"><span data-stu-id="c3104-153">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="c3104-154">-   **SQLMoreResults**不會傳回更多可用的資料。</span><span class="sxs-lookup"><span data-stu-id="c3104-154">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="c3104-155">-Length 表示從伺服器傳回的資料大小，而不是儲存在 buffer 中。</span><span class="sxs-lookup"><span data-stu-id="c3104-155">-   Length indicates the size of the data returned from server, not stored in buffer.</span></span><br /><span data-ttu-id="c3104-156">-原始緩衝區包含63個位元組和一個 Null 結束字元。</span><span class="sxs-lookup"><span data-stu-id="c3104-156">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="c3104-157">緩衝區一定是以 NULL 結尾。</span><span class="sxs-lookup"><span data-stu-id="c3104-157">Buffer is guaranteed to be NULL terminated.</span></span>|  
|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] <span data-ttu-id="c3104-158">Native Client (11.0.2100.60 版) 或更新版本</span><span class="sxs-lookup"><span data-stu-id="c3104-158">Native Client (version 11.0.2100.60) or later</span></span>|<span data-ttu-id="c3104-159">-4 (SQL_NO_TOTAL)</span><span class="sxs-lookup"><span data-stu-id="c3104-159">-4 (SQL_NO_TOTAL)</span></span>|<span data-ttu-id="c3104-160">-   **SQLFetch**不會傳回更多可用的資料。</span><span class="sxs-lookup"><span data-stu-id="c3104-160">-   **SQLFetch** returns no more data available.</span></span><br /><span data-ttu-id="c3104-161">-   **SQLMoreResults**不會傳回更多可用的資料。</span><span class="sxs-lookup"><span data-stu-id="c3104-161">-   **SQLMoreResults** returns no more data available.</span></span><br /><span data-ttu-id="c3104-162">-Length 表示 (-4) SQL_NO_TOTAL，因為其餘的資料並未轉換。</span><span class="sxs-lookup"><span data-stu-id="c3104-162">-   Length indicates (-4) SQL_NO_TOTAL because the rest of the data was not converted.</span></span><br /><span data-ttu-id="c3104-163">-原始緩衝區包含63個位元組和一個 Null 結束字元。</span><span class="sxs-lookup"><span data-stu-id="c3104-163">-   Original buffer contains 63 bytes and a NULL terminator.</span></span> <span data-ttu-id="c3104-164">緩衝區一定是以 NULL 結尾。</span><span class="sxs-lookup"><span data-stu-id="c3104-164">Buffer is guaranteed to be NULL terminated.</span></span>|  
  
## <a name="performing-char-and-wchar-conversions"></a><span data-ttu-id="c3104-165">執行 CHAR 和 WCHAR 轉換</span><span class="sxs-lookup"><span data-stu-id="c3104-165">Performing CHAR and WCHAR Conversions</span></span>  
 <span data-ttu-id="c3104-166">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC 驅動程式提供了幾種方法來執行 CHAR 和 WCHAR 轉換。</span><span class="sxs-lookup"><span data-stu-id="c3104-166">The [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client ODBC driver offers several ways to perform CHAR and WCHAR conversions.</span></span> <span data-ttu-id="c3104-167">邏輯類似于將 blob 操作 (Varchar (max) 、Nvarchar (max) ... ) ：</span><span class="sxs-lookup"><span data-stu-id="c3104-167">The logic is similar to manipulating blobs (varchar(max), nvarchar(max), ...):</span></span>  
  
-   <span data-ttu-id="c3104-168">當使用**SQLBindCol**或**SQLBindParameter**系結時，資料會儲存或截斷至指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c3104-168">Data is saved or truncated into the specified buffer when binding with **SQLBindCol** or **SQLBindParameter**.</span></span>  
  
-   <span data-ttu-id="c3104-169">如果您未系結，您可以使用**SQLGetData**和**SQLParamData**，以區塊形式抓取資料。</span><span class="sxs-lookup"><span data-stu-id="c3104-169">If you do not bind, you can retrieve the data in chunks by using **SQLGetData** and **SQLParamData**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3104-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3104-170">See Also</span></span>  
 [<span data-ttu-id="c3104-171">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="c3104-171">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
