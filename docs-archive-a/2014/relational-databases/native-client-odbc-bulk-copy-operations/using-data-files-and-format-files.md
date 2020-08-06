---
title: 使用資料檔案和格式檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e0ee92f79e2c8cab9605db0188e01898df8c23e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709389"
---
# <a name="using-data-files-and-format-files"></a><span data-ttu-id="e68d8-102">使用資料檔案與格式檔案</span><span class="sxs-lookup"><span data-stu-id="e68d8-102">Using Data Files and Format Files</span></span>
  <span data-ttu-id="e68d8-103">最簡單的大量複製程式會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e68d8-103">The simplest bulk copy program does the following:</span></span>  
  
1.  <span data-ttu-id="e68d8-104">呼叫[bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)來指定大量複製， (從資料表或視圖將 BCP_OUT) 設定為資料檔案。</span><span class="sxs-lookup"><span data-stu-id="e68d8-104">Calls [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to specify bulk copying out (set BCP_OUT) from a table or view to a data file.</span></span>  
  
2.  <span data-ttu-id="e68d8-105">呼叫[bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)來執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="e68d8-105">Calls [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="e68d8-106">資料檔案是在原生模式下建立的，因此，來自資料表或檢視之所有資料行的資料會以與資料庫相同的格式，儲存在資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="e68d8-106">The data file is created in native mode; therefore, data from all columns in the table or view are stored in the data file in the same format as in the database.</span></span> <span data-ttu-id="e68d8-107">接著，可以使用這些相同的步驟，並設定 DB_IN (而非 DB_OUT)，將檔案大量複製到伺服器中。</span><span class="sxs-lookup"><span data-stu-id="e68d8-107">The file can then be bulk copied into a server by using these same steps and setting DB_IN instead of DB_OUT.</span></span> <span data-ttu-id="e68d8-108">只有當來源資料表和目標資料表兩者都具有相同的結構時，才適用這種方法。</span><span class="sxs-lookup"><span data-stu-id="e68d8-108">This works only if both the source and target tables have exactly the same structure.</span></span> <span data-ttu-id="e68d8-109">您也可以使用 **/n** (原生模式) 參數，將產生的資料檔案輸入至**bcp**公用程式。</span><span class="sxs-lookup"><span data-stu-id="e68d8-109">The resulting data file can also be input to the **bcp** utility by using the **/n** (native mode) switch.</span></span>  
  
 <span data-ttu-id="e68d8-110">大量複製 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的結果集，而非直接從資料表或檢視大量複製：</span><span class="sxs-lookup"><span data-stu-id="e68d8-110">To bulk copy out the result set of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement instead of directly from a table or view:</span></span>  
  
1.  <span data-ttu-id="e68d8-111">呼叫**bcp_init**來指定大量複製，但針對資料表名稱指定 Null。</span><span class="sxs-lookup"><span data-stu-id="e68d8-111">Call **bcp_init** to specify bulk copying out, but specify NULL for the table name.</span></span>  
  
2.  <span data-ttu-id="e68d8-112">呼叫[bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) ，並將*EOPTION*設定為 BCPHINTS，並將*iValue*設定為包含 transact-sql 語句之 SQLTCHAR 字串的指標。</span><span class="sxs-lookup"><span data-stu-id="e68d8-112">Call [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) with *eOption* set to BCPHINTS and *iValue* set to a pointer to a SQLTCHAR string containing the Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="e68d8-113">呼叫**bcp_exec**以執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="e68d8-113">Call **bcp_exec** to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="e68d8-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式可能是會產生結果集的任何陳述式。</span><span class="sxs-lookup"><span data-stu-id="e68d8-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be any statement that generates a result set.</span></span> <span data-ttu-id="e68d8-115">系統會建立包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式第一個結果集的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="e68d8-115">The data file is created containing the first result set of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="e68d8-116">如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式產生多個結果集，則大量複製會忽略第一個結果集後的任何結果集。</span><span class="sxs-lookup"><span data-stu-id="e68d8-116">Bulk copy ignores any result set after the first if the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement generates multiple result sets.</span></span>  
  
 <span data-ttu-id="e68d8-117">若要建立資料檔，其中的資料行資料是以與資料表不同的格式儲存，請呼叫[bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)來指定要變更多少資料行，然後針對您想要變更其格式的每個資料行呼叫[bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) 。</span><span class="sxs-lookup"><span data-stu-id="e68d8-117">To create a data file in which column data is stored in a different format than in the table, call [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) to specify how many columns will be changed, then call [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) for each column whose format you want to change.</span></span> <span data-ttu-id="e68d8-118">這會在呼叫**bcp_init**之後，但在呼叫**bcp_exec**之前完成。</span><span class="sxs-lookup"><span data-stu-id="e68d8-118">This is done after calling **bcp_init** but before calling **bcp_exec**.</span></span> <span data-ttu-id="e68d8-119">**bcp_colfmt**指定資料行的資料儲存在資料檔案中的格式。</span><span class="sxs-lookup"><span data-stu-id="e68d8-119">**bcp_colfmt** specifies the format in which the column's data is stored in the data file.</span></span> <span data-ttu-id="e68d8-120">在大量複製或輸出時，可以使用它。您也可以使用**bcp_colfmt**來設定資料列和資料行結束字元。</span><span class="sxs-lookup"><span data-stu-id="e68d8-120">It can be used when bulk copying in or out. You can also use **bcp_colfmt** to set the row and column terminators.</span></span> <span data-ttu-id="e68d8-121">例如，如果您的資料未包含定位字元，您可以使用**bcp_colfmt**來建立 tab 鍵分隔的檔案，將定位字元設定為每個資料行的結束字元。</span><span class="sxs-lookup"><span data-stu-id="e68d8-121">For example, if your data contains no tab characters, you can create a tab-delimited file by using **bcp_colfmt** to set the tab character as the terminator for each column.</span></span>  
  
 <span data-ttu-id="e68d8-122">大量複製並使用**bcp_colfmt**時，您可以輕鬆地建立格式檔案，以描述您在最後一次呼叫**bcp_colfmt**之後所[bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)建立的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="e68d8-122">When bulk copying out and using **bcp_colfmt**, you can easily create a format file describing the data file you have created by calling [bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) after the last call to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="e68d8-123">從格式檔案所描述的資料檔案中大量複製時，請在**bcp_init**之後，但在**bcp_exec**之前呼叫[bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) ，以讀取格式檔案。</span><span class="sxs-lookup"><span data-stu-id="e68d8-123">When bulk copying in from a data file described by a format file, read the format file by calling [bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) after **bcp_init** but before **bcp_exec**.</span></span>  
  
 <span data-ttu-id="e68d8-124">從資料檔案大量複製到時， **bcp_control**函數會控制數個選項 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e68d8-124">The **bcp_control** function controls several options when bulk copying into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file.</span></span> <span data-ttu-id="e68d8-125">**bcp_control**設定選項，例如終止前的錯誤最大數目、開始大量複製之檔案中的資料列、停止的資料列，以及批次大小。</span><span class="sxs-lookup"><span data-stu-id="e68d8-125">**bcp_control** sets options, such as the maximum number of errors before termination, the row in the file on which to start the bulk copy, the row to stop on, and the batch size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e68d8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e68d8-126">See Also</span></span>  
 [<span data-ttu-id="e68d8-127">&#40;ODBC&#41;執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="e68d8-127">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  
