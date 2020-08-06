---
title: bcp_readfmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: rothja
ms.author: jroth
ms.openlocfilehash: 37032ec276be8b914d73e834453cc5d87cdedbbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594056"
---
# <a name="bcp_readfmt"></a><span data-ttu-id="8227e-102">bcp_readfmt</span><span class="sxs-lookup"><span data-stu-id="8227e-102">bcp_readfmt</span></span>
  <span data-ttu-id="8227e-103">從指定的格式檔案讀取資料檔格式定義。</span><span class="sxs-lookup"><span data-stu-id="8227e-103">Reads a data file format definition from the specified format file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8227e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8227e-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="8227e-105">引數</span><span class="sxs-lookup"><span data-stu-id="8227e-105">Arguments</span></span>  
 <span data-ttu-id="8227e-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="8227e-106">*hdbc*</span></span>  
 <span data-ttu-id="8227e-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="8227e-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="8227e-108">*szFormatFile*</span><span class="sxs-lookup"><span data-stu-id="8227e-108">*szFormatFile*</span></span>  
 <span data-ttu-id="8227e-109">這是包含資料檔格式值之檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8227e-109">Is the path and file name of the file containing the format values for the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="8227e-110">傳回</span><span class="sxs-lookup"><span data-stu-id="8227e-110">Returns</span></span>  
 <span data-ttu-id="8227e-111">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="8227e-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8227e-112">備註</span><span class="sxs-lookup"><span data-stu-id="8227e-112">Remarks</span></span>  
 <span data-ttu-id="8227e-113">在 `bcp_readfmt` 讀取格式值之後，它會對[bcp_columns](bcp-columns.md)和[bcp_colfmt](bcp-colfmt.md)進行適當的呼叫。</span><span class="sxs-lookup"><span data-stu-id="8227e-113">After `bcp_readfmt` reads the format values, it makes the appropriate calls to [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md).</span></span> <span data-ttu-id="8227e-114">您不需要剖析格式檔案，也不需要進行這些呼叫。</span><span class="sxs-lookup"><span data-stu-id="8227e-114">There is no need for you to parse a format file and make these calls.</span></span>  
  
 <span data-ttu-id="8227e-115">若要保存格式檔案，請呼叫[bcp_writefmt](bcp-writefmt.md)。</span><span class="sxs-lookup"><span data-stu-id="8227e-115">To persist a format file, call [bcp_writefmt](bcp-writefmt.md).</span></span> <span data-ttu-id="8227e-116">對的呼叫 `bcp_readfmt` 可以參考儲存的格式。</span><span class="sxs-lookup"><span data-stu-id="8227e-116">Calls to `bcp_readfmt` can reference saved formats.</span></span> <span data-ttu-id="8227e-117">如需詳細資訊，請參閱[bcp_init](bcp-init.md)。</span><span class="sxs-lookup"><span data-stu-id="8227e-117">For more information, see [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="8227e-118">或者，大量複製公用程式 (**bcp**) 可以將使用者定義的資料格式儲存在可供參考的檔案中 `bcp_readfmt` 。</span><span class="sxs-lookup"><span data-stu-id="8227e-118">Alternately, the bulk-copy utility (**bcp**) can save user-defined data formats in files that can be referenced by `bcp_readfmt`.</span></span> <span data-ttu-id="8227e-119">如需**bcp**公用程式和**bcp**資料格式檔案結構的詳細資訊，請參閱[大量匯入和匯出資料 &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8227e-119">For more information about the **bcp** utility and the structure of **bcp** data format files, see [Bulk Import and Export of Data &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="8227e-120">`BCPDELAYREADFMT` [Bcp_control](bcp-control.md)的*eOption*參數值會修改 bcp_readfmt 的行為。</span><span class="sxs-lookup"><span data-stu-id="8227e-120">The `BCPDELAYREADFMT` value of the *eOption* parameter of [bcp_control](bcp-control.md) modifies the behavior of bcp_readfmt.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8227e-121">格式檔案必須已由**bcp**公用程式的4.2 或更新版本所產生。</span><span class="sxs-lookup"><span data-stu-id="8227e-121">The format file must have been produced by version 4.2 or later of the **bcp** utility.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8227e-122">範例</span><span class="sxs-lookup"><span data-stu-id="8227e-122">Example</span></span>  
  
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
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="8227e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8227e-123">See Also</span></span>  
 [<span data-ttu-id="8227e-124">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="8227e-124">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
