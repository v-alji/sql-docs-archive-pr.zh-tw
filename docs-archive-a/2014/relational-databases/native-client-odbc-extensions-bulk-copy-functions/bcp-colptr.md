---
title: bcp_colptr |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
author: rothja
ms.author: jroth
ms.openlocfilehash: 8b725ace58ee1768fbca1a433cdea27e3e0e546e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709373"
---
# <a name="bcp_colptr"></a><span data-ttu-id="f6cfd-102">bcp_colptr</span><span class="sxs-lookup"><span data-stu-id="f6cfd-102">bcp_colptr</span></span>
  <span data-ttu-id="f6cfd-103">將目前副本的程式變數資料位址設定成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-103">Sets the program variable data address for the current copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6cfd-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6cfd-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6cfd-105">引數</span><span class="sxs-lookup"><span data-stu-id="f6cfd-105">Arguments</span></span>  
 <span data-ttu-id="f6cfd-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="f6cfd-106">*hdbc*</span></span>  
 <span data-ttu-id="f6cfd-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="f6cfd-108">*pData*</span><span class="sxs-lookup"><span data-stu-id="f6cfd-108">*pData*</span></span>  
 <span data-ttu-id="f6cfd-109">這是要複製之資料的指標。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-109">Is a pointer to the data to copy.</span></span> <span data-ttu-id="f6cfd-110">如果系結資料類型是大數數值型別 (例如 SQLTEXT 或 SQLIMAGE) ，則*pData*可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-110">If the bound data type is large value type (such as SQLTEXT or SQLIMAGE), *pData* can be NULL.</span></span> <span data-ttu-id="f6cfd-111">Null *pData*表示 long 資料值將使用[bcp_moretext](bcp-moretext.md)以區區塊轉送至 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-111">A NULL *pData* indicates long data values will be sent to SQL Server in chunks using [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="f6cfd-112">如果*pData*設定為 Null，且對應至系結欄位的資料行不是大數數值型別， **bcp_colptr**會失敗。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-112">If *pData* is set to NULL and the column corresponding to the bound field is not a large value type, **bcp_colptr** fails.</span></span>  
  
 <span data-ttu-id="f6cfd-113">如需有關大數數值型別的詳細資訊，請參閱[bcp_bind](bcp-bind.md)**。**</span><span class="sxs-lookup"><span data-stu-id="f6cfd-113">For more information on large value types, see [bcp_bind](bcp-bind.md)**.**</span></span>  
  
 <span data-ttu-id="f6cfd-114">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="f6cfd-114">*idxServerCol*</span></span>  
 <span data-ttu-id="f6cfd-115">這是資料庫資料表中要將資料複製到其中之資料行的序數位置。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-115">Is the ordinal position of the column in the database table to which the data is copied.</span></span> <span data-ttu-id="f6cfd-116">資料表中的第一個資料行是資料行 1。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-116">The first column in a table is column 1.</span></span> <span data-ttu-id="f6cfd-117">資料行的序數位置是由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)所報告。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-117">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f6cfd-118">傳回</span><span class="sxs-lookup"><span data-stu-id="f6cfd-118">Returns</span></span>  
 <span data-ttu-id="f6cfd-119">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-119">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6cfd-120">備註</span><span class="sxs-lookup"><span data-stu-id="f6cfd-120">Remarks</span></span>  
 <span data-ttu-id="f6cfd-121">當您將資料複製到具有[bcp_sendrow](bcp-sendrow.md)的 SQL Server 時， **bcp_colptr**函數可讓您變更特定資料行的來源資料位址。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-121">The **bcp_colptr** function allows you to change the address of source data for a particular column when copying data to SQL Server with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="f6cfd-122">一開始，使用者資料的指標是由**bcp_bind**的呼叫所設定。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-122">Initially, the pointer to user data is set by a call to **bcp_bind**.</span></span> <span data-ttu-id="f6cfd-123">如果程式變數資料位址在**bcp_sendrow**的呼叫之間變更，您可以呼叫**bcp_colptr** ，將指標重設為數據。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-123">If the program variable data address changes between calls to **bcp_sendrow**, you can call **bcp_colptr** to reset the pointer to the data.</span></span> <span data-ttu-id="f6cfd-124">下一次呼叫**bcp_sendrow**會將呼叫所定址的資料傳送給**bcp_colptr**。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-124">The next call to **bcp_sendrow** sends the data addressed by the call to **bcp_colptr**.</span></span>  
  
 <span data-ttu-id="f6cfd-125">您想要修改其資料位址之資料表中的每個資料行都必須有個別的**bcp_colptr**呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6cfd-125">There must be a separate **bcp_colptr** call for every column in the table whose data address you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6cfd-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6cfd-126">See Also</span></span>  
 [<span data-ttu-id="f6cfd-127">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="f6cfd-127">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
