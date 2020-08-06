---
title: bcp_collen |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3099e26b0c2cd0d1cfee7578f5b149b812f01765
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709369"
---
# <a name="bcp_collen"></a><span data-ttu-id="b545f-102">bcp_collen</span><span class="sxs-lookup"><span data-stu-id="b545f-102">bcp_collen</span></span>
  <span data-ttu-id="b545f-103">設定目前大量複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之程式變數中的資料長度。</span><span class="sxs-lookup"><span data-stu-id="b545f-103">Sets the data length in the program variable for the current bulk copy into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b545f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b545f-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b545f-105">引數</span><span class="sxs-lookup"><span data-stu-id="b545f-105">Arguments</span></span>  
 <span data-ttu-id="b545f-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="b545f-106">*hdbc*</span></span>  
 <span data-ttu-id="b545f-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b545f-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="b545f-108">*cbData*</span><span class="sxs-lookup"><span data-stu-id="b545f-108">*cbData*</span></span>  
 <span data-ttu-id="b545f-109">這是資料在程式變數中的長度，不包括任何長度指標或結束字元的長度。</span><span class="sxs-lookup"><span data-stu-id="b545f-109">Is the length of the data in the program variable, not including the length of any length indicator or terminator.</span></span> <span data-ttu-id="b545f-110">將*cbData*設定為 SQL_Null_DATA 表示複製到伺服器的所有資料列都包含資料行的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="b545f-110">Setting *cbData* to SQL_NULL_DATA indicates all rows copied to the server contain a NULL value for the column.</span></span> <span data-ttu-id="b545f-111">將它設定為 SQL_VARLEN_DATA 表示系統將會使用字串結束字元或其他方法來判斷已複製之資料的長度。</span><span class="sxs-lookup"><span data-stu-id="b545f-111">Setting it to SQL_VARLEN_DATA indicates that a string terminator or other method is used to determine the length of data copied.</span></span> <span data-ttu-id="b545f-112">如果長度指標與結束字元同時存在，系統會使用造成複製的資料較少的那一個結果。</span><span class="sxs-lookup"><span data-stu-id="b545f-112">If both a length indicator and a terminator exist, the system uses whichever one results in less data being copied.</span></span>  
  
 <span data-ttu-id="b545f-113">*idxServerCol*</span><span class="sxs-lookup"><span data-stu-id="b545f-113">*idxServerCol*</span></span>  
 <span data-ttu-id="b545f-114">這是資料表中要將資料複製到其中之資料行的序數位置。</span><span class="sxs-lookup"><span data-stu-id="b545f-114">Is the ordinal position of the column in the table to which the data is copied.</span></span> <span data-ttu-id="b545f-115">第一個資料行是 1。</span><span class="sxs-lookup"><span data-stu-id="b545f-115">The first column is 1.</span></span> <span data-ttu-id="b545f-116">資料行的序數位置是由[SQLColumns](../native-client-odbc-api/sqlcolumns.md)所報告。</span><span class="sxs-lookup"><span data-stu-id="b545f-116">The ordinal position of a column is reported by [SQLColumns](../native-client-odbc-api/sqlcolumns.md).</span></span>  
  
## <a name="returns"></a><span data-ttu-id="b545f-117">傳回</span><span class="sxs-lookup"><span data-stu-id="b545f-117">Returns</span></span>  
 <span data-ttu-id="b545f-118">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="b545f-118">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b545f-119">備註</span><span class="sxs-lookup"><span data-stu-id="b545f-119">Remarks</span></span>  
 <span data-ttu-id="b545f-120">**Bcp_collen**函數可讓您在使用 bcp_sendrow 將資料複製到時，變更特定資料行之程式變數中的資料長度 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="b545f-120">The **bcp_collen** function allows you to change the data length in the program variable for a particular column when copying data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
 <span data-ttu-id="b545f-121">一開始，資料長度是在呼叫[bcp_bind](bcp-bind.md)時決定。</span><span class="sxs-lookup"><span data-stu-id="b545f-121">Initially, the data length is determined when [bcp_bind](bcp-bind.md) is called.</span></span> <span data-ttu-id="b545f-122">如果**bcp_sendrow**的呼叫之間的資料長度變更，且未使用長度前置詞或結束字元，您可以呼叫**bcp_collen**以重設長度。</span><span class="sxs-lookup"><span data-stu-id="b545f-122">If the data length changes between calls to **bcp_sendrow** and no length prefix or terminator is being used, you can call **bcp_collen** to reset the length.</span></span> <span data-ttu-id="b545f-123">下一次呼叫**bcp_sendrow**會使用**bcp_collen**的呼叫所設定的長度。</span><span class="sxs-lookup"><span data-stu-id="b545f-123">The next call to **bcp_sendrow** uses the length set by the call to **bcp_collen**.</span></span>  
  
 <span data-ttu-id="b545f-124">您必須針對您想要修改其資料長度的資料表中的每個資料行，呼叫一次**bcp_collen** 。</span><span class="sxs-lookup"><span data-stu-id="b545f-124">You must call **bcp_collen** once for each column in the table whose data length you want to modify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b545f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b545f-125">See Also</span></span>  
 [<span data-ttu-id="b545f-126">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="b545f-126">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
