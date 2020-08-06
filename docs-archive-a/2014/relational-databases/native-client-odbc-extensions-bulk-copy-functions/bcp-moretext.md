---
title: bcp_moretext |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
author: rothja
ms.author: jroth
ms.openlocfilehash: 00c0eb1c8739e94380b12034cebc70d8e22b79c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594059"
---
# <a name="bcp_moretext"></a><span data-ttu-id="049ac-102">bcp_moretext</span><span class="sxs-lookup"><span data-stu-id="049ac-102">bcp_moretext</span></span>
  <span data-ttu-id="049ac-103">將長的變動長度資料類型值的一部分傳送給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="049ac-103">Sends part of a long, variable-length data type value to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="049ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="049ac-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="049ac-105">引數</span><span class="sxs-lookup"><span data-stu-id="049ac-105">Arguments</span></span>  
 <span data-ttu-id="049ac-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="049ac-106">*hdbc*</span></span>  
 <span data-ttu-id="049ac-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="049ac-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="049ac-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="049ac-108">*cbData*</span></span>  
 <span data-ttu-id="049ac-109">這是要從*pData*所參考的資料中，複製到 SQL Server 的資料位元組數目。</span><span class="sxs-lookup"><span data-stu-id="049ac-109">Is the number of bytes of data being copied to SQL Server from the data referenced by *pData*.</span></span> <span data-ttu-id="049ac-110">SQL_NULL_DATA 的值表示 NULL。</span><span class="sxs-lookup"><span data-stu-id="049ac-110">A value of SQL_NULL_DATA indicates NULL.</span></span>  
  
 <span data-ttu-id="049ac-111">*pData*</span><span class="sxs-lookup"><span data-stu-id="049ac-111">*pData*</span></span>  
 <span data-ttu-id="049ac-112">這是要傳送給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之支援的長型、變動長度資料區塊的指標。</span><span class="sxs-lookup"><span data-stu-id="049ac-112">Is a pointer to the supported, long, variable-length data chunk to be sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="returns"></a><span data-ttu-id="049ac-113">傳回</span><span class="sxs-lookup"><span data-stu-id="049ac-113">Returns</span></span>  
 <span data-ttu-id="049ac-114">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="049ac-114">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="049ac-115">備註</span><span class="sxs-lookup"><span data-stu-id="049ac-115">Remarks</span></span>  
 <span data-ttu-id="049ac-116">此函式可與[bcp_bind](bcp-bind.md)和[bcp_sendrow](bcp-sendrow.md)搭配使用，以將長的可變長度資料值複製到數個較社區塊中的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="049ac-116">This function can be used in conjunction with [bcp_bind](bcp-bind.md) and [bcp_sendrow](bcp-sendrow.md) to copy long, variable-length data values to SQL Server in a number of smaller chunks.</span></span> <span data-ttu-id="049ac-117">**bcp_moretext**可以與具有下列 SQL Server 資料類型的資料行搭配使用： `text` 、 `ntext` 、 `image` 、 `varchar(max)` 、 `nvarchar(max)` 、 `varbinary(max)` 、使用者定義型別 (UDT) 和 XML。</span><span class="sxs-lookup"><span data-stu-id="049ac-117">**bcp_moretext** can be used with columns that have the following SQL Server data types: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, user-defined type (UDT), and XML.</span></span> <span data-ttu-id="049ac-118">**bcp_moretext**不支援資料轉換，所提供的資料必須符合目標資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="049ac-118">**bcp_moretext** does not support data conversions, the data supplied must match the data type of the target column.</span></span>  
  
 <span data-ttu-id="049ac-119">如果針對**bcp_moretext**支援的資料類型，以非 Null 的*pData*參數來呼叫**bcp_bind** ，就會傳送 `bcp_sendrow` 整個資料值，而不論長度為何。</span><span class="sxs-lookup"><span data-stu-id="049ac-119">If **bcp_bind** is called with a nonNULL *pData* parameter for data types that are supported by **bcp_moretext**, `bcp_sendrow` sends the entire data value, regardless of length.</span></span> <span data-ttu-id="049ac-120">不過，如果**bcp_bind**針對支援的資料類型具有 Null *pData*參數，則在成功傳回後，可以使用**bcp_moretext**來立即複製資料， `bcp_sendrow` 表示已處理任何具有資料的已系結資料行。</span><span class="sxs-lookup"><span data-stu-id="049ac-120">If, however, **bcp_bind** has a NULL *pData* parameter for supported data types, **bcp_moretext** can be used to copy data immediately after a successful return from `bcp_sendrow` indicating that any bound columns with data present have been processed.</span></span>  
  
 <span data-ttu-id="049ac-121">如果您使用**bcp_moretext**在資料列中傳送一個支援的資料類型資料行，您也必須使用它來傳送資料列中所有其他支援的資料類型資料行。</span><span class="sxs-lookup"><span data-stu-id="049ac-121">If you use **bcp_moretext** to send one supported data type column in a row, you must also use it to send all other supported data type columns in the row.</span></span> <span data-ttu-id="049ac-122">不能略過任何資料行。</span><span class="sxs-lookup"><span data-stu-id="049ac-122">No columns may be skipped.</span></span> <span data-ttu-id="049ac-123">支援的資料類型為 SQLTEXT、SQLNTEXT、SQLIMAGE、SQLUDT 和 SQLXML。</span><span class="sxs-lookup"><span data-stu-id="049ac-123">Supported data types are SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT and SQLXML.</span></span> <span data-ttu-id="049ac-124">如果此資料行分別為 varchar(max)、nvarchar(max) 或 varbinary(max)，則 SQLCHARACTER、SQLVARCHAR、SQNCHAR、SQLBINARY 和 SQLVARBINARY 也會列入這個類別目錄。</span><span class="sxs-lookup"><span data-stu-id="049ac-124">SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY and SQLVARBINARY also fall into this category if the column is a varchar(max), nvarchar(max) or varbinary(max), respectively.</span></span>  
  
 <span data-ttu-id="049ac-125">呼叫**bcp_bind**或[bcp_collen](bcp-collen.md)會設定要複製到 SQL Server 資料行之所有資料部分的總長度。</span><span class="sxs-lookup"><span data-stu-id="049ac-125">Calling either **bcp_bind** or [bcp_collen](bcp-collen.md) sets the total length of all data parts to be copied to the SQL Server column.</span></span> <span data-ttu-id="049ac-126">嘗試傳送 SQL Server 超過呼叫中所指定的位元組數， **bcp_bind**或 `bcp_collen` 產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="049ac-126">An attempt to send SQL Server more bytes than specified in the call to **bcp_bind** or `bcp_collen` generates an error.</span></span> <span data-ttu-id="049ac-127">例如，在用 `bcp_collen` 來將 SQL Server 資料行的可用資料長度設定為4500的應用程式中， `text` 呼叫**bcp_moretext**五次，並在每次呼叫中指出資料緩衝區長度為1000個位元組時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="049ac-127">This error would arise, for example, in an application which used `bcp_collen` to set the length of available data for an SQL Server `text` column to 4500, then called **bcp_moretext** five times while indicating on each call that the data buffer length was 1000 bytes long.</span></span>  
  
 <span data-ttu-id="049ac-128">如果複製的資料列包含一個以上的長時間可變長度資料行， **bcp_moretext**首先會將其資料傳送到最低的序數編號資料行，後面接著下一個最低的序數編號資料行，依此類推。</span><span class="sxs-lookup"><span data-stu-id="049ac-128">If a copied row contains more than one long, variable-length column, **bcp_moretext** first sends its data to the lowest ordinally numbered column, followed by the next lowest ordinally numbered column, and so on.</span></span> <span data-ttu-id="049ac-129">更正預期資料的總長度設定是很重要的一件事。</span><span class="sxs-lookup"><span data-stu-id="049ac-129">Correct setting of the total length of expected data is important.</span></span> <span data-ttu-id="049ac-130">除了使用長度設定以外，沒有任何方法可以指示大量複製已經收到資料行的所有資料。</span><span class="sxs-lookup"><span data-stu-id="049ac-130">There is no way to signal, outside of the length setting, that all data for a column has been received by bulk copy.</span></span>  
  
 <span data-ttu-id="049ac-131">當 `var(max)` 使用 bcp_sendrow 和 bcp_moretext 將值傳送至伺服器時，不需要呼叫 bcp_collen 來設定資料行長度。</span><span class="sxs-lookup"><span data-stu-id="049ac-131">When `var(max)` values are sent to the server using bcp_sendrow and bcp_moretext, it is not necessary to call bcp_collen to set the column length.</span></span> <span data-ttu-id="049ac-132">相反地，針對這些類型，值會藉由呼叫長度為零的 bcp_sendrow 來終止。</span><span class="sxs-lookup"><span data-stu-id="049ac-132">Instead, for these types only, the value is terminated by calling bcp_sendrow with a length of zero.</span></span>  
  
 <span data-ttu-id="049ac-133">應用程式通常會 `bcp_sendrow` 在迴圈內呼叫並**bcp_moretext** ，以傳送多個資料列。</span><span class="sxs-lookup"><span data-stu-id="049ac-133">An application normally calls `bcp_sendrow` and **bcp_moretext** within loops to send a number of rows of data.</span></span> <span data-ttu-id="049ac-134">以下概述如何針對包含兩個數據行的資料表執行這項 `text` 操作：</span><span class="sxs-lookup"><span data-stu-id="049ac-134">Here's an outline of how to do this for a table containing two `text` columns:</span></span>  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a><span data-ttu-id="049ac-135">範例</span><span class="sxs-lookup"><span data-stu-id="049ac-135">Example</span></span>  
 <span data-ttu-id="049ac-136">這個範例示範如何使用**bcp_moretext**搭配**bcp_bind**和 `bcp_sendrow` ：</span><span class="sxs-lookup"><span data-stu-id="049ac-136">This example shows how to use **bcp_moretext** with **bcp_bind** and `bcp_sendrow`:</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
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
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="049ac-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="049ac-137">See Also</span></span>  
 [<span data-ttu-id="049ac-138">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="049ac-138">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
