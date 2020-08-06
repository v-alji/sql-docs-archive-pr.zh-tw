---
title: 管理大量複製批次大小 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
author: rothja
ms.author: jroth
ms.openlocfilehash: 1f24ece176cbb834e4162f9e516ff23013fd256a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598351"
---
# <a name="managing-bulk-copy-batch-sizes"></a><span data-ttu-id="ffd1d-102">管理大量複製批次大小</span><span class="sxs-lookup"><span data-stu-id="ffd1d-102">Managing Bulk Copy Batch Sizes</span></span>
  <span data-ttu-id="ffd1d-103">大量複製作業中批次的主要用途是定義交易的範圍。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-103">The primary purpose of a batch in bulk copy operations is to define the scope of a transaction.</span></span> <span data-ttu-id="ffd1d-104">如果沒有設定批次大小，則大量複製函數會將整個大量複製作業視為一筆交易。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-104">If a batch size is not set, then bulk copy functions consider an entire bulk copy to be one transaction.</span></span> <span data-ttu-id="ffd1d-105">如果有設定批次大小，則每一個批次都構成一筆在批次完成時認可的交易。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-105">If a batch size is set, then each batch constitutes a transaction that is committed when the batch finishes.</span></span>  
  
 <span data-ttu-id="ffd1d-106">如果大量複製在執行時沒有指定任何批次大小，而且發生了錯誤，則整個大量複製都會回復。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-106">If a bulk copy is performed with no batch size specified and an error is encountered, the entire bulk copy is rolled back.</span></span> <span data-ttu-id="ffd1d-107">長時間執行的大量複製的復原可能要花一段很長的時間。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-107">The recovery of a long-running bulk copy can take a long time.</span></span> <span data-ttu-id="ffd1d-108">如果有設定批次大小，則大量複製會將每個批次視為一筆交易並認可每個批次。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-108">When a batch size is set, bulk copy considers each batch a transaction and commits each batch.</span></span> <span data-ttu-id="ffd1d-109">如果發生錯誤，只需要回復最後一個沒有完成的批次。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-109">If an error is encountered, only the last outstanding batch needs to be rolled back.</span></span>  
  
 <span data-ttu-id="ffd1d-110">批次大小也會影響鎖定負擔。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-110">The batch size can also affect locking overhead.</span></span> <span data-ttu-id="ffd1d-111">對執行大量複製時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，可以使用[bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)來指定 TABLOCK 提示，以取得表鎖，而不是資料列鎖定。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-111">When performing a bulk copy against [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the TABLOCK hint can be specified using [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) to acquire a table lock instead of row locks.</span></span> <span data-ttu-id="ffd1d-112">對於整個大量複製作業而言，設定單一資料表鎖定所需的負擔最低。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-112">The single table lock can be held with minimal overhead for an entire bulk copy operation.</span></span> <span data-ttu-id="ffd1d-113">如果沒有指定 TABLOCK，則會在個別的資料列上設定鎖定，而在大量複製期間維持所有鎖定的負擔可能會使效能降低。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-113">If TABLOCK is not specified then locks are held on individual rows and the overhead of maintaining all the locks for the duration of the bulk copy can slow performance.</span></span> <span data-ttu-id="ffd1d-114">因為鎖定只會在交易期間設定，所以指定批次大小可以藉由定期產生釋放目前所設定之鎖定的認可來解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-114">Because locks are only held for the length of a transaction, specifying a batch size addresses this problem by periodically generating a commit that frees the locks currently held.</span></span>  
  
 <span data-ttu-id="ffd1d-115">在大量複製許多資料列時，組成批次的資料列數可能會對效能造成很大的影響。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-115">The number of rows making up a batch can have significant performance effects when bulk copying a large number of rows.</span></span> <span data-ttu-id="ffd1d-116">批次大小的建議是依所執行之大量複製的類型而定。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-116">The recommendations for batch size depend on the type of bulk copy being performed.</span></span>  
  
-   <span data-ttu-id="ffd1d-117">大量複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，請指定 TABLOCK 大量複製提示並設定大型的批次大小。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-117">When bulk copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specify the TABLOCK bulk copy hint and set a large batch size.</span></span>  
  
-   <span data-ttu-id="ffd1d-118">如果沒有指定 TABLOCK，則將批次大小限制為小於 1,000 資料列。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-118">When TABLOCK is not specified, limit batch sizes to less than 1,000 rows.</span></span>  
  
 <span data-ttu-id="ffd1d-119">從資料檔案大量複製時，在呼叫[bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)之前，會使用 BCPBATCH 選項呼叫**bcp_control**來指定批次大小。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-119">When bulk copying in from a data file, the batch size is specified by calling **bcp_control** with the BCPBATCH option before calling [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md).</span></span> <span data-ttu-id="ffd1d-120">使用[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)和[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)從程式變數大量複製時，批次大小是藉由在呼叫[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x*次後呼叫[bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)來控制，其中*x*是批次中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-120">When bulk copying from program variables using [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) and [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), the batch size is controlled by calling [bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) after calling [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* times, where *x* is the number of rows in a batch.</span></span>  
  
 <span data-ttu-id="ffd1d-121">除了指定交易大小外，批次也會影響資料列何時會透過網路傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-121">In addition to specifying the size of a transaction, batches also affect when rows are sent across the network to the server.</span></span> <span data-ttu-id="ffd1d-122">大量複製函數通常會快取**bcp_sendrow**的資料列，直到網路封包填滿為止，然後將完整封包傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-122">Bulk copy functions normally cache the rows from **bcp_sendrow** until a network packet is filled, and then send the full packet to the server.</span></span> <span data-ttu-id="ffd1d-123">不過，當應用程式呼叫**bcp_batch**時，就會將目前的封包傳送至伺服器，不論是否已填入。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-123">When an application calls **bcp_batch**, however, the current packet is sent to the server regardless of whether it has been filled.</span></span> <span data-ttu-id="ffd1d-124">使用很小的批次大小如果造成傳送許多部分填滿的封包到伺服器，則可能會使效能降低。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-124">Using a very low batch size can slow performance if it results in sending many partially filled packets to the server.</span></span> <span data-ttu-id="ffd1d-125">例如，在每個**bcp_sendrow**後呼叫**bcp_batch**都會導致個別封包中傳送每個資料列，而除非資料列很大，否則會浪費每個封包中的空間。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-125">For example, calling **bcp_batch** after every **bcp_sendrow** causes each row to be sent in a separate packet and, unless the rows are very large, wastes space in each packet.</span></span> <span data-ttu-id="ffd1d-126">SQL Server 的網路封包的預設大小是 4 KB，雖然應用程式可以藉由呼叫指定 SQL_ATTR_PACKET_SIZE 屬性的[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)來變更大小。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-126">The default size of network packets for SQL Server is 4 KB, although an application can change the size by calling [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) specifying the SQL_ATTR_PACKET_SIZE attribute.</span></span>  
  
 <span data-ttu-id="ffd1d-127">批次的另一個副作用是，每個批次都會被視為未完成的結果集，直到使用**bcp_batch**完成為止。</span><span class="sxs-lookup"><span data-stu-id="ffd1d-127">Another side effect of batches is that each batch is considered an outstanding result set until it is completed with **bcp_batch**.</span></span> <span data-ttu-id="ffd1d-128">當批次未完成時，如果在連接控制碼上嘗試任何其他作業， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會發出 SQLState = "HY000" 的錯誤，並提供錯誤訊息字串：</span><span class="sxs-lookup"><span data-stu-id="ffd1d-128">If any other operations are attempted on a connection handle while a batch is outstanding, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver issues an error with SQLState = "HY000" and an error message string of:</span></span>  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffd1d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffd1d-129">See Also</span></span>  
 <span data-ttu-id="ffd1d-130">[&#40;ODBC&#41;執行大量複製作業](performing-bulk-copy-operations-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="ffd1d-130">[Performing Bulk Copy Operations &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md) </span></span>  
 [<span data-ttu-id="ffd1d-131">資料的大量匯入及匯出 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ffd1d-131">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
