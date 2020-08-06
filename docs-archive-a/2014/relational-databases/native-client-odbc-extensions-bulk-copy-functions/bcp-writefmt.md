---
title: bcp_writefmt |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_writefmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_writefmt function
ms.assetid: cb4c1d37-667d-4bcd-b13c-eb638bcc9b69
author: rothja
ms.author: jroth
ms.openlocfilehash: 13785469e0b02f63f14d28f0db87e77df3a15cfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597099"
---
# <a name="bcp_writefmt"></a><span data-ttu-id="4d08c-102">bcp_writefmt</span><span class="sxs-lookup"><span data-stu-id="4d08c-102">bcp_writefmt</span></span>
  <span data-ttu-id="4d08c-103">建立包含目前大量複製資料檔格式之描述的格式檔。</span><span class="sxs-lookup"><span data-stu-id="4d08c-103">Creates a format file containing a description of the format of the current bulk copy data file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d08c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d08c-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_writefmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d08c-105">引數</span><span class="sxs-lookup"><span data-stu-id="4d08c-105">Arguments</span></span>  
 <span data-ttu-id="4d08c-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="4d08c-106">*hdbc*</span></span>  
 <span data-ttu-id="4d08c-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="4d08c-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="4d08c-108">*szFormatFile*</span><span class="sxs-lookup"><span data-stu-id="4d08c-108">*szFormatFile*</span></span>  
 <span data-ttu-id="4d08c-109">這是用來接收資料檔格式值之使用者檔案的路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4d08c-109">Is the path and file name of the user file to receive format values for the data file.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="4d08c-110">傳回</span><span class="sxs-lookup"><span data-stu-id="4d08c-110">Returns</span></span>  
 <span data-ttu-id="4d08c-111">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="4d08c-111">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d08c-112">備註</span><span class="sxs-lookup"><span data-stu-id="4d08c-112">Remarks</span></span>  
 <span data-ttu-id="4d08c-113">格式檔案會指定大量複製所建立之資料檔的資料格式。</span><span class="sxs-lookup"><span data-stu-id="4d08c-113">The format file specifies the data format of a data file created by bulk copy.</span></span> <span data-ttu-id="4d08c-114">呼叫[bcp_columns](bcp-columns.md)和[bcp_colfmt](bcp-colfmt.md)定義資料檔案的格式。</span><span class="sxs-lookup"><span data-stu-id="4d08c-114">Calls to [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md) define the format of the data file.</span></span> <span data-ttu-id="4d08c-115">**bcp_writefmt**會將此定義儲存在*szformatfile 中*所參考的檔案中。</span><span class="sxs-lookup"><span data-stu-id="4d08c-115">**bcp_writefmt** saves this definition in the file referenced by *szFormatFile*.</span></span> <span data-ttu-id="4d08c-116">如需詳細資訊，請參閱[bcp_init](bcp-init.md)。</span><span class="sxs-lookup"><span data-stu-id="4d08c-116">For more information, see [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="4d08c-117">如需**bcp**資料格式檔案結構的詳細資訊，請參閱[使用 bcp 公用程式匯入和匯出大量資料 &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d08c-117">For more information about the structure of **bcp** data format files, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).</span></span>  
  
 <span data-ttu-id="4d08c-118">若要載入儲存的格式檔案，請使用[bcp_readfmt](bcp-readfmt.md)。</span><span class="sxs-lookup"><span data-stu-id="4d08c-118">To load a saved format file, use [bcp_readfmt](bcp-readfmt.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d08c-119">只有與7.0 版和更新版本一起散發的**bcp**公用程式版本才支援**bcp_writefmt**所產生的格式檔案 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4d08c-119">The format file produced by **bcp_writefmt** is supported only by versions of the **bcp** utility distributed with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d08c-120">範例</span><span class="sxs-lookup"><span data-stu-id="4d08c-120">Example</span></span>  
  
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
   _T("myErrors"),    DB_OUT) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_columns(hdbc, 3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
bcp_colfmt(hdbc, 1, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 1);  
bcp_colfmt(hdbc, 2, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 2);  
bcp_colfmt(hdbc, 3, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 3);  
  
if (bcp_writefmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   printf_s("%ld rows copied from SQL Server\n", nRowsProcessed);  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d08c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d08c-121">See Also</span></span>  
 [<span data-ttu-id="4d08c-122">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="4d08c-122">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
