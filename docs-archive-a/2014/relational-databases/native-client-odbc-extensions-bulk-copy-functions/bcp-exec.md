---
title: bcp_exec |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_exec
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: rothja
ms.author: jroth
ms.openlocfilehash: f925c6cb1e3a36f79ba4f560a06c5b6d499ece4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584476"
---
# <a name="bcp_exec"></a><span data-ttu-id="0931f-102">bcp_exec</span><span class="sxs-lookup"><span data-stu-id="0931f-102">bcp_exec</span></span>
  <span data-ttu-id="0931f-103">在資料庫資料表和使用者檔案間執行資料的完整大量複製。</span><span class="sxs-lookup"><span data-stu-id="0931f-103">Executes a complete bulk copy of data between a database table and a user file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0931f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0931f-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_exec (  
HDBC   
hdbc  
,  
LPDBINT   
pnRowsProcessed  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="0931f-105">引數</span><span class="sxs-lookup"><span data-stu-id="0931f-105">Arguments</span></span>  
 <span data-ttu-id="0931f-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="0931f-106">*hdbc*</span></span>  
 <span data-ttu-id="0931f-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0931f-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="0931f-108">*pnRowsProcessed*</span><span class="sxs-lookup"><span data-stu-id="0931f-108">*pnRowsProcessed*</span></span>  
 <span data-ttu-id="0931f-109">這是 DBINT 的指標。</span><span class="sxs-lookup"><span data-stu-id="0931f-109">Is a pointer to a DBINT.</span></span> <span data-ttu-id="0931f-110">**Bcp_exec**函式會將成功複製的資料列數目填入此 DBINT。</span><span class="sxs-lookup"><span data-stu-id="0931f-110">The **bcp_exec** function fills this DBINT with the number of rows successfully copied.</span></span> <span data-ttu-id="0931f-111">如果*pnRowsProcessed*為 Null， **bcp_exec**會將它忽略。</span><span class="sxs-lookup"><span data-stu-id="0931f-111">If *pnRowsProcessed* is NULL, it is ignored by **bcp_exec**.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="0931f-112">傳回</span><span class="sxs-lookup"><span data-stu-id="0931f-112">Returns</span></span>  
 <span data-ttu-id="0931f-113">SUCCEED、SUCCEED_ASYNC 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="0931f-113">SUCCEED, SUCCEED_ASYNC, or FAIL.</span></span> <span data-ttu-id="0931f-114">如果所有資料列都已複製， **bcp_exec**函數會傳回成功。</span><span class="sxs-lookup"><span data-stu-id="0931f-114">The **bcp_exec** function returns SUCCEED if all rows are copied.</span></span> <span data-ttu-id="0931f-115">如果非同步大量複製作業仍未完成， **bcp_exec**會傳回 SUCCEED_ASYNC。</span><span class="sxs-lookup"><span data-stu-id="0931f-115">**bcp_exec** returns SUCCEED_ASYNC if an asynchronous bulk copy operation is still outstanding.</span></span> <span data-ttu-id="0931f-116">如果發生完整失敗，或如果產生錯誤的資料列數到達使用[BCP_CONTROL](bcp-control.md)BCPMAXERRS 指定的值， **BCP_EXEC**會傳回 FAIL。</span><span class="sxs-lookup"><span data-stu-id="0931f-116">**bcp_exec** returns FAIL if a complete failure occurs, or if the number of rows generating errors reaches the value specified for BCPMAXERRS using [bcp_control](bcp-control.md).</span></span> <span data-ttu-id="0931f-117">BCPMAXERRS 預設為 10。</span><span class="sxs-lookup"><span data-stu-id="0931f-117">BCPMAXERRS defaults to 10.</span></span> <span data-ttu-id="0931f-118">BCPMAXERRS 選項僅會影響提供者在從資料檔讀取資料列 (而非傳送到伺服器的資料列) 時所偵測到的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="0931f-118">The BCPMAXERRS option affects only the syntax errors detected by the provider while reading the rows from the data file (and not the rows sent to the server).</span></span> <span data-ttu-id="0931f-119">伺服器會在偵測到資料列的錯誤時中止批次。</span><span class="sxs-lookup"><span data-stu-id="0931f-119">Server aborts the batch when it detects an error with a row.</span></span> <span data-ttu-id="0931f-120">檢查*pnRowsProcessed*參數是否有成功複製的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="0931f-120">Check the *pnRowsProcessed* parameter for the number of rows successfully copied.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0931f-121">備註</span><span class="sxs-lookup"><span data-stu-id="0931f-121">Remarks</span></span>  
 <span data-ttu-id="0931f-122">此函數會根據[bcp_init](bcp-init.md)中的*eDirection*參數值，將資料從使用者檔案複製到資料庫資料表，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="0931f-122">This function copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter in [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="0931f-123">呼叫**bcp_exec**之前，請使用有效的使用者檔案名來呼叫**bcp_init** 。</span><span class="sxs-lookup"><span data-stu-id="0931f-123">Before calling **bcp_exec**, call **bcp_init** with a valid user file name.</span></span> <span data-ttu-id="0931f-124">無法執行這項操作時，會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0931f-124">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="0931f-125">**bcp_exec**是唯一可能會在任何時間長度內待處理的大量複製函數。</span><span class="sxs-lookup"><span data-stu-id="0931f-125">**bcp_exec** is the only bulk copy function that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="0931f-126">因此，它是唯一支援非同步模式的大量複製函數。</span><span class="sxs-lookup"><span data-stu-id="0931f-126">It is therefore the only bulk copy function that supports asynchronous mode.</span></span> <span data-ttu-id="0931f-127">若要設定非同步模式，請使用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，將 SQL_ATTR_ASYNC_ENABLE 設定為 SQL_ASYNC_ENABLE_ON，然後再呼叫**bcp_exec**。</span><span class="sxs-lookup"><span data-stu-id="0931f-127">To set asynchronous mode, use [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_ON before calling **bcp_exec**.</span></span> <span data-ttu-id="0931f-128">若要測試是否完成，請使用相同的參數來呼叫**bcp_exec** 。</span><span class="sxs-lookup"><span data-stu-id="0931f-128">To test for completion, call **bcp_exec** with the same parameters.</span></span> <span data-ttu-id="0931f-129">如果大量複製尚未完成， **bcp_exec**會傳回 SUCCEED_ASYNC。</span><span class="sxs-lookup"><span data-stu-id="0931f-129">If the bulk copy has not yet completed, **bcp_exec** returns SUCCEED_ASYNC.</span></span> <span data-ttu-id="0931f-130">它也會在*pnRowsProcessed*中傳回已傳送到伺服器之資料列數目的狀態計數。</span><span class="sxs-lookup"><span data-stu-id="0931f-130">It also returns in *pnRowsProcessed* a status count of the number of rows that have been sent to the server.</span></span> <span data-ttu-id="0931f-131">到達批次的結尾之前，不會認可傳送至伺服器的資料列。</span><span class="sxs-lookup"><span data-stu-id="0931f-131">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
 <span data-ttu-id="0931f-132">如需從開始大量複製的重大變更相關資訊 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，請參閱[&#40;ODBC&#41;執行大量複製作業](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0931f-132">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0931f-133">範例</span><span class="sxs-lookup"><span data-stu-id="0931f-133">Example</span></span>  
 <span data-ttu-id="0931f-134">下列範例顯示如何使用**bcp_exec**：</span><span class="sxs-lookup"><span data-stu-id="0931f-134">The following example shows how to use **bcp_exec**:</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="0931f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0931f-135">See Also</span></span>  
 [<span data-ttu-id="0931f-136">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="0931f-136">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
