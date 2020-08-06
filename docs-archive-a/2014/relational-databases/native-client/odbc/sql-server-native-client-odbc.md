---
title: SQL Server Native Client (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: rothja
ms.author: jroth
ms.openlocfilehash: 16c73966e318ed1e7d326fa77f56195ebbd830df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702858"
---
# <a name="sql-server-native-client-odbc"></a><span data-ttu-id="34a2d-102">SQL Server Native Client (ODBC)</span><span class="sxs-lookup"><span data-stu-id="34a2d-102">SQL Server Native Client (ODBC)</span></span>
  <span data-ttu-id="34a2d-103">ODBC 是應用程式開發介面 (API) 的標準定義，用於存取關聯式資料庫或索引循序存取方法 (ISAM) 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="34a2d-103">ODBC is a standard definition of an application programming interface (API) used to access data in relational or indexed sequential access method (ISAM) databases.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="34a2d-104">透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援 ODBC 做為其中一個原生應用程式開發介面，來撰寫與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行通訊的 C 和 C++ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="34a2d-104">supports ODBC, via the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver, as one of the native APIs for writing C and C++ applications that communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="34a2d-105">使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式撰寫的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 程式會透過 C 函數呼叫，與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="34a2d-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] programs that are written using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver communicate with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] through C function calls.</span></span> <span data-ttu-id="34a2d-106">ODBC 函數的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專屬版本會在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式中實作。</span><span class="sxs-lookup"><span data-stu-id="34a2d-106">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific versions of the ODBC functions are implemented in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="34a2d-107">此驅動程式會將 SQL 陳述式傳遞到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，然後將陳述式的結果傳回到應用程式。</span><span class="sxs-lookup"><span data-stu-id="34a2d-107">The driver passes SQL statements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and returns the results of the statements to the application.</span></span>  
  
 <span data-ttu-id="34a2d-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式符合 Microsoft Win32 ODBC 3.51 規格。</span><span class="sxs-lookup"><span data-stu-id="34a2d-108">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver complies with the Microsoft Win32 ODBC 3.51 specification.</span></span> <span data-ttu-id="34a2d-109">此驅動程式支援使用舊版 ODBC，以 ODBC 3.51 規格中定義之方式撰寫的應用程式。</span><span class="sxs-lookup"><span data-stu-id="34a2d-109">The driver supports applications written using earlier versions of ODBC in the manner defined in the ODBC 3.51 specification.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34a2d-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="34a2d-110">In This Section</span></span>  
  
-   [<span data-ttu-id="34a2d-111">資料來源名稱和 64 位元作業系統</span><span class="sxs-lookup"><span data-stu-id="34a2d-111">Data Source Names and 64-Bit Operating Systems</span></span>](data-source-names-and-64-bit-operating-systems.md)  
  
-   [<span data-ttu-id="34a2d-112">建立 SQL Server Native Client ODBC 驅動程式應用程式</span><span class="sxs-lookup"><span data-stu-id="34a2d-112">Creating a SQL Server Native Client ODBC Driver Application</span></span>](creating-a-driver-application.md)  
  
-   [<span data-ttu-id="34a2d-113">與 SQL Server &#40;ODBC&#41;通訊</span><span class="sxs-lookup"><span data-stu-id="34a2d-113">Communicating with SQL Server &#40;ODBC&#41;</span></span>](../../native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [<span data-ttu-id="34a2d-114">&#40;ODBC&#41;執行查詢</span><span class="sxs-lookup"><span data-stu-id="34a2d-114">Executing Queries &#40;ODBC&#41;</span></span>](../../native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [<span data-ttu-id="34a2d-115">&#40;ODBC&#41;處理結果</span><span class="sxs-lookup"><span data-stu-id="34a2d-115">Processing Results &#40;ODBC&#41;</span></span>](../../native-client-odbc-results/processing-results-odbc.md)  
  
-   [<span data-ttu-id="34a2d-116">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="34a2d-116">Using Cursors &#40;ODBC&#41;</span></span>](../../native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [<span data-ttu-id="34a2d-117">&#40;ODBC&#41;執行交易</span><span class="sxs-lookup"><span data-stu-id="34a2d-117">Performing Transactions &#40;ODBC&#41;</span></span>](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
-   [<span data-ttu-id="34a2d-118">處理錯誤與訊息</span><span class="sxs-lookup"><span data-stu-id="34a2d-118">Handling Errors and Messages</span></span>](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [<span data-ttu-id="34a2d-119">執行預存程序</span><span class="sxs-lookup"><span data-stu-id="34a2d-119">Running Stored Procedures</span></span>](../../native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [<span data-ttu-id="34a2d-120">使用目錄函式</span><span class="sxs-lookup"><span data-stu-id="34a2d-120">Using Catalog Functions</span></span>](using-catalog-functions.md)  
  
-   [<span data-ttu-id="34a2d-121">&#40;ODBC&#41;執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="34a2d-121">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [<span data-ttu-id="34a2d-122">管理 Text 和 Image 資料行</span><span class="sxs-lookup"><span data-stu-id="34a2d-122">Managing Text and Image Columns</span></span>](../../native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [<span data-ttu-id="34a2d-123">分析 ODBC 驅動程式效能</span><span class="sxs-lookup"><span data-stu-id="34a2d-123">Profiling ODBC Driver Performance</span></span>](profiling-odbc-driver-performance.md)  
  
-   [<span data-ttu-id="34a2d-124">ODBC&#41;&#40;的資料表值參數</span><span class="sxs-lookup"><span data-stu-id="34a2d-124">Table-Valued Parameters &#40;ODBC&#41;</span></span>](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [<span data-ttu-id="34a2d-125">ODBC&#41;&#40;的日期和時間改善</span><span class="sxs-lookup"><span data-stu-id="34a2d-125">Date and Time Improvements &#40;ODBC&#41;</span></span>](../../native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [<span data-ttu-id="34a2d-126">&#40;ODBC&#41;的大型 CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="34a2d-126">Large CLR User-Defined Types &#40;ODBC&#41;</span></span>](large-clr-user-defined-types-odbc.md)  
  
-   [<span data-ttu-id="34a2d-127">FILESTREAM 支援 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="34a2d-127">FILESTREAM Support &#40;ODBC&#41;</span></span>](filestream-support-odbc.md)  
  
-   [<span data-ttu-id="34a2d-128">用戶端連接 &#40;ODBC&#41; 中的服務主體名稱 &#40;SPN&#41;</span><span class="sxs-lookup"><span data-stu-id="34a2d-128">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;</span></span>](service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [<span data-ttu-id="34a2d-129">&#40;ODBC&#41;的稀疏資料行支援</span><span class="sxs-lookup"><span data-stu-id="34a2d-129">Sparse Columns Support &#40;ODBC&#41;</span></span>](sparse-columns-support-odbc.md)  
  
-   [<span data-ttu-id="34a2d-130">SQL Server Native Client &#40;ODBC&#41; 參考</span><span class="sxs-lookup"><span data-stu-id="34a2d-130">SQL Server Native Client &#40;ODBC&#41; Reference</span></span>](../../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)  
  
-   [<span data-ttu-id="34a2d-131">ODBC 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="34a2d-131">ODBC How-to Topics</span></span>](../../native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="34a2d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34a2d-132">See Also</span></span>  
 <span data-ttu-id="34a2d-133">[SQL Server Native Client 程式設計](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="34a2d-133">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 [<span data-ttu-id="34a2d-134">安裝 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="34a2d-134">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  
