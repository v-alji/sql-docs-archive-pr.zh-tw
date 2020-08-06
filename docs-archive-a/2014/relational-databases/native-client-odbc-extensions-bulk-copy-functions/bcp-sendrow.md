---
title: bcp_sendrow |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d2f55486ba57101ffc7b1903de5d19ac8eaaca2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594048"
---
# <a name="bcp_sendrow"></a><span data-ttu-id="85df3-102">bcp_sendrow</span><span class="sxs-lookup"><span data-stu-id="85df3-102">bcp_sendrow</span></span>
  <span data-ttu-id="85df3-103">將程式變數中的資料列傳送給 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="85df3-103">Sends a row of data from program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85df3-104">語法</span><span class="sxs-lookup"><span data-stu-id="85df3-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="85df3-105">引數</span><span class="sxs-lookup"><span data-stu-id="85df3-105">Arguments</span></span>  
 <span data-ttu-id="85df3-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="85df3-106">*hdbc*</span></span>  
 <span data-ttu-id="85df3-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="85df3-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="85df3-108">傳回</span><span class="sxs-lookup"><span data-stu-id="85df3-108">Returns</span></span>  
 <span data-ttu-id="85df3-109">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="85df3-109">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85df3-110">備註</span><span class="sxs-lookup"><span data-stu-id="85df3-110">Remarks</span></span>  
 <span data-ttu-id="85df3-111">**Bcp_sendrow**函式會從程式變數建立資料列，並將它傳送至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85df3-111">The **bcp_sendrow** function builds a row from program variables and sends it to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="85df3-112">呼叫**bcp_sendrow**之前，您必須先呼叫[bcp_bind](bcp-bind.md) ，以指定包含資料列資料的程式變數。</span><span class="sxs-lookup"><span data-stu-id="85df3-112">Before calling **bcp_sendrow**, you must make calls to [bcp_bind](bcp-bind.md) to specify the program variables containing row data.</span></span>  
  
 <span data-ttu-id="85df3-113">如果呼叫**bcp_bind**指定長的可變長度資料類型（例如，SQLTEXT 的*eDataType*參數和非 null *pData*參數），則**bcp_sendrow**會傳送 entiredata 值，就如同任何其他資料類型一樣。</span><span class="sxs-lookup"><span data-stu-id="85df3-113">If **bcp_bind** is called specifying a long, variable-length data type, for example, an *eDataType* parameter of SQLTEXT and a nonNULL *pData* parameter, **bcp_sendrow** sends the entiredata value, just as it does for any other data type.</span></span> <span data-ttu-id="85df3-114">不過，如果**bcp_bind**具有 Null *pData*參數， **bcp_sendrow**將控制權傳回給應用程式，並在所有具有指定資料的資料行都傳送至之後立即傳回控制項 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85df3-114">If, however, **bcp_bind** has a NULL *pData* parameter, **bcp_sendrow** returns control to the application immediately after all columns with data specified are sent to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="85df3-115">然後，應用程式就可以重複呼叫[bcp_moretext](bcp-moretext.md) ，將長的可變長度資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一次傳送給一個區塊。</span><span class="sxs-lookup"><span data-stu-id="85df3-115">The application can then call [bcp_moretext](bcp-moretext.md) repeatedly to send the long, variable-length data to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a chunk at a time.</span></span> <span data-ttu-id="85df3-116">如需詳細資訊，請參閱[bcp_moretext](bcp-moretext.md)。</span><span class="sxs-lookup"><span data-stu-id="85df3-116">For more information, see [bcp_moretext](bcp-moretext.md).</span></span>  
  
 <span data-ttu-id="85df3-117">當**bcp_sendrow**用來將程式變數中的資料列大量複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表時，只有當使用者呼叫[bcp_batch](bcp-batch.md)或[bcp_done](bcp-done.md)時，才會認可資料列。</span><span class="sxs-lookup"><span data-stu-id="85df3-117">When **bcp_sendrow** is used to bulk copy rows from program variables into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables, rows are committed only when the user calls [bcp_batch](bcp-batch.md) or [bcp_done](bcp-done.md).</span></span> <span data-ttu-id="85df3-118">使用者可以選擇在每個*n*個數據列或在傳入資料的期間牢靠時，呼叫**bcp_batch**一次。</span><span class="sxs-lookup"><span data-stu-id="85df3-118">The user can choose to call **bcp_batch** once every *n* rows or when there is a lull between periods of incoming data.</span></span> <span data-ttu-id="85df3-119">如果永遠不會呼叫**bcp_batch** ，則會在呼叫**bcp_done**時認可資料列。</span><span class="sxs-lookup"><span data-stu-id="85df3-119">If **bcp_batch** is never called, the rows are committed when **bcp_done** is called.</span></span>  
  
 <span data-ttu-id="85df3-120">如需從開始大量複製的重大變更相關資訊 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ，請參閱[&#40;ODBC&#41;執行大量複製作業](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="85df3-120">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85df3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85df3-121">See Also</span></span>  
 [<span data-ttu-id="85df3-122">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="85df3-122">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
