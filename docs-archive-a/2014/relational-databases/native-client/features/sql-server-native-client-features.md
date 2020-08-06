---
title: SQL Server Native Client 功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], features
ms.assetid: 7bb32865-5afb-41ab-98b4-3fa545ee8953
author: rothja
ms.author: jroth
ms.openlocfilehash: bb4ba07f84848f754519f8f4fa1c3e56485e85a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593366"
---
# <a name="sql-server-native-client-features"></a><span data-ttu-id="e663d-102">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="e663d-102">SQL Server Native Client Features</span></span>
  <span data-ttu-id="e663d-103">除了公開 Windows (先前稱為 Microsoft) Data Access Components (WDAC) 的功能之外，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 也會實作其他許多功能來公開 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="e663d-103">In addition to exposing features of the Windows (formerly Microsoft) Data Access Components (WDAC), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client also implements many other features to expose [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e663d-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="e663d-104">In This Section</span></span>  
 [<span data-ttu-id="e663d-105">ODBC 驅動程式在處理字元轉換上的行為變更</span><span class="sxs-lookup"><span data-stu-id="e663d-105">ODBC Driver Behavior Change When Handling Character Conversions</span></span>](odbc-driver-behavior-change-when-handling-character-conversions.md)  
 <span data-ttu-id="e663d-106">討論自從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client 起的行為變更。</span><span class="sxs-lookup"><span data-stu-id="e663d-106">Discusses a change of behavior beginning in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client.</span></span>  
  
 [<span data-ttu-id="e663d-107">使用資料庫鏡像</span><span class="sxs-lookup"><span data-stu-id="e663d-107">Using Database Mirroring</span></span>](using-database-mirroring.md)  
 <span data-ttu-id="e663d-108">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援鏡像資料庫的使用，這是在待命伺服器上保留資料庫複本或鏡像的功能 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e663d-108">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the use of mirrored databases, which is the ability to keep a copy, or mirror, of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database on a standby server.</span></span>  
  
 [<span data-ttu-id="e663d-109">執行非同步作業</span><span class="sxs-lookup"><span data-stu-id="e663d-109">Performing Asynchronous Operations</span></span>](performing-asynchronous-operations.md)  
 <span data-ttu-id="e663d-110">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援非同步作業，這是立即傳回而不在呼叫執行緒上封鎖的功能。</span><span class="sxs-lookup"><span data-stu-id="e663d-110">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports asynchronous operations, which is the ability to return immediately without blocking on the calling thread.</span></span>  
  
 [<span data-ttu-id="e663d-111">使用 Multiple Active Result Set &#40;MARS&#41;</span><span class="sxs-lookup"><span data-stu-id="e663d-111">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](using-multiple-active-result-sets-mars.md)  
 <span data-ttu-id="e663d-112">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援 Multiple Active Result Set (MARS)。</span><span class="sxs-lookup"><span data-stu-id="e663d-112">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports multiple active result sets (MARS).</span></span> <span data-ttu-id="e663d-113">MARS 可讓您使用單一資料庫連接執行與接收多個結果集</span><span class="sxs-lookup"><span data-stu-id="e663d-113">MARS enables you to execute and receive multiple result sets using a single database connection</span></span>  
  
 [<span data-ttu-id="e663d-114">使用 XML 資料類型</span><span class="sxs-lookup"><span data-stu-id="e663d-114">Using XML Data Types</span></span>](using-xml-data-types.md)  
 <span data-ttu-id="e663d-115">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援 XML 資料類型，這是以 XML 為基礎的資料類型，可以當做資料行類型、變數類型、參數類型或函數傳回類型使用。</span><span class="sxs-lookup"><span data-stu-id="e663d-115">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the XML data type, which is a XML-based data type that can be used as a column type, variable type, parameter type, or function return type.</span></span>  
  
 [<span data-ttu-id="e663d-116">使用使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="e663d-116">Using User-Defined Types</span></span>](using-user-defined-types.md)  
 <span data-ttu-id="e663d-117">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援 (UDT) 的使用者定義型別，這可讓您將物件和自訂資料結構儲存在資料庫中，藉此擴充 SQL 型別系統 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e663d-117">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports User-Defined Types (UDT), which extends the SQL type system by allowing you to store objects and custom data structures in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
 [<span data-ttu-id="e663d-118">使用大數值類型</span><span class="sxs-lookup"><span data-stu-id="e663d-118">Using Large Value Types</span></span>](using-large-value-types.md)  
 <span data-ttu-id="e663d-119">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援大數值資料類型，也就是大型物件資料類型 (LOB)。</span><span class="sxs-lookup"><span data-stu-id="e663d-119">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports large value data types, which are large object data types (LOB).</span></span>  
  
 [<span data-ttu-id="e663d-120">以程式設計方式變更密碼</span><span class="sxs-lookup"><span data-stu-id="e663d-120">Changing Passwords Programmatically</span></span>](changing-passwords-programmatically.md)  
 <span data-ttu-id="e663d-121">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援過期密碼的處理方式，讓密碼現在可以在用戶端上變更，而不需要系統管理員介入。</span><span class="sxs-lookup"><span data-stu-id="e663d-121">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the handling of expired passwords so that passwords can now be changed on the client without administrator involvement.</span></span>  
  
 [<span data-ttu-id="e663d-122">使用快照集隔離</span><span class="sxs-lookup"><span data-stu-id="e663d-122">Working with Snapshot Isolation</span></span>](working-with-snapshot-isolation.md)  
 <span data-ttu-id="e663d-123">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援資料列版本設定的增強功能，藉由避免發生讀取器-寫入器封鎖的情況來改善效能。</span><span class="sxs-lookup"><span data-stu-id="e663d-123">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports the enhancement to row versioning that improves database performance by avoiding reader-writer blocking scenarios.</span></span>  
  
 [<span data-ttu-id="e663d-124">使用查詢通知</span><span class="sxs-lookup"><span data-stu-id="e663d-124">Working with Query Notifications</span></span>](working-with-query-notifications.md)  
 <span data-ttu-id="e663d-125">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援在資料列集修改時使用取用者通知。</span><span class="sxs-lookup"><span data-stu-id="e663d-125">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports consumer notification on rowset modification.</span></span>  
  
 [<span data-ttu-id="e663d-126">執行大量複製作業</span><span class="sxs-lookup"><span data-stu-id="e663d-126">Performing Bulk Copy Operations</span></span>](performing-bulk-copy-operations.md)  
 <span data-ttu-id="e663d-127">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 如何支援大量複製作業，以允許在資料表或視圖中傳入或傳出大量資料 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e663d-127">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supports bulk copy operations that allow the transfer of large amounts of data into or out of a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table or view.</span></span>  
  
 [<span data-ttu-id="e663d-128">使用加密而不需驗證</span><span class="sxs-lookup"><span data-stu-id="e663d-128">Using Encryption Without Validation</span></span>](using-encryption-without-validation.md)  
 <span data-ttu-id="e663d-129">討論如何使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 加密傳送到伺服器的資料，而不驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="e663d-129">Discusses how to use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to encrypt data sent to the server without validating the certificate.</span></span>  
  
 [<span data-ttu-id="e663d-130">資料表值參數 &#40;SQL Server Native Client&#41;</span><span class="sxs-lookup"><span data-stu-id="e663d-130">Table-Valued Parameters &#40;SQL Server Native Client&#41;</span></span>](table-valued-parameters-sql-server-native-client.md)  
 <span data-ttu-id="e663d-131">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 對於資料表值參數的支援。</span><span class="sxs-lookup"><span data-stu-id="e663d-131">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the table-valued parameters.</span></span>  
  
 [<span data-ttu-id="e663d-132">大型 CLR 使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="e663d-132">Large CLR User-Defined Types</span></span>](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 <span data-ttu-id="e663d-133">討論大型 Common Language Runtime (CLR) 使用者定義型別 (UDT) 的支援。</span><span class="sxs-lookup"><span data-stu-id="e663d-133">Discusses support for large common language runtime (CLR) user-defined types (UDTs).</span></span>  
  
 [<span data-ttu-id="e663d-134">FILESTREAM 支援</span><span class="sxs-lookup"><span data-stu-id="e663d-134">FILESTREAM Support</span></span>](filestream-support.md)  
 <span data-ttu-id="e663d-135">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 對增強型 FILESTREAM 功能的支援。</span><span class="sxs-lookup"><span data-stu-id="e663d-135">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the enhanced FILESTREAM feature.</span></span>  
  
 [<span data-ttu-id="e663d-136">用戶端連接中的服務主要名稱 &#40;SPN&#41; 支援</span><span class="sxs-lookup"><span data-stu-id="e663d-136">Service Principal Name &#40;SPN&#41; Support in Client Connections</span></span>](service-principal-name-spn-support-in-client-connections.md)  
 <span data-ttu-id="e663d-137">討論如何擴充服務主要名稱 (SPN) 的支援以便跨所有通訊協定進行相互驗證。</span><span class="sxs-lookup"><span data-stu-id="e663d-137">Discusses how support for service principal names (SPNs) has been extended to enable mutual authentication across all protocols.</span></span>  
  
 [<span data-ttu-id="e663d-138">SQL Server Native Client 中的疏鬆資料行支援</span><span class="sxs-lookup"><span data-stu-id="e663d-138">Sparse Columns Support in SQL Server Native Client</span></span>](sparse-columns-support-in-sql-server-native-client.md)  
 <span data-ttu-id="e663d-139">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 對疏鬆資料行的支援。</span><span class="sxs-lookup"><span data-stu-id="e663d-139">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for sparse columns.</span></span>  
  
 [<span data-ttu-id="e663d-140">日期和時間改善</span><span class="sxs-lookup"><span data-stu-id="e663d-140">Date and Time Improvements</span></span>](date-and-time-improvements.md)  
 <span data-ttu-id="e663d-141">討論針對新日期和時間資料類型加入到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 的支援。</span><span class="sxs-lookup"><span data-stu-id="e663d-141">Discusses support added to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the date and time data types.</span></span>  
  
 [<span data-ttu-id="e663d-142">中繼資料探索</span><span class="sxs-lookup"><span data-stu-id="e663d-142">Metadata Discovery</span></span>](metadata-discovery.md)  
 <span data-ttu-id="e663d-143">討論在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 內所做的中繼資料探索改進。</span><span class="sxs-lookup"><span data-stu-id="e663d-143">Discusses metadata discovery improvements that were made in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="e663d-144">SQL Server Native Client 11.0 中的 UTF-16 支援</span><span class="sxs-lookup"><span data-stu-id="e663d-144">UTF-16 Support in SQL Server Native Client 11.0</span></span>](utf-16-support-in-sql-server-native-client-11-0.md)  
 <span data-ttu-id="e663d-145">討論 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中導入的行為變更。</span><span class="sxs-lookup"><span data-stu-id="e663d-145">Discusses a behavior change introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="e663d-146">如果您在繫結資料行結果或輸出參數時提供固定長度的緩衝區、`wchar` 字元在終止字元成為 Surrogate 字組的高 Surrogate 字碼指標之前寫入緩衝區，而且下一個 `wchar` 字元是低 Surrogate 字碼指標，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 就不會將高 Surrogate 字碼指標加入至緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e663d-146">If you supply a fixed-length buffer when binding a column result or output parameter and if the `wchar` character written into the buffer before the terminating character is a high surrogate code point of a surrogate pair, and if the next `wchar` character is a low surrogate code point, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will not add the high surrogate code point to the buffer.</span></span>  
  
 [<span data-ttu-id="e663d-147">高可用性/災害復原的 SQL Server Native Client 支援</span><span class="sxs-lookup"><span data-stu-id="e663d-147">SQL Server Native Client Support for High Availability, Disaster Recovery</span></span>](sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="e663d-148">討論如何設定應用程式以利用 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中新增的高可用性災害復原功能。</span><span class="sxs-lookup"><span data-stu-id="e663d-148">Discusses how your application can be configured to take advantage of the high-availability, disaster recovery features added in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="e663d-149">存取擴展事件記錄檔中的診斷資訊</span><span class="sxs-lookup"><span data-stu-id="e663d-149">Accessing Diagnostic Information in the Extended Events Log</span></span>](accessing-diagnostic-information-in-the-extended-events-log.md)  
 <span data-ttu-id="e663d-150">討論可讓您存取信號緩衝區和 XEvents 記錄檔中之診斷資訊的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 及資料追蹤增強功能。</span><span class="sxs-lookup"><span data-stu-id="e663d-150">Discusses enhancements to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data tracing that gives you access to diagnostic information in the ring buffer and XEvents log.</span></span>  
  
 [<span data-ttu-id="e663d-151">SQL Server Native Client 對 LocalDB 的支援</span><span class="sxs-lookup"><span data-stu-id="e663d-151">SQL Server Native Client Support for LocalDB</span></span>](sql-server-native-client-support-for-localdb.md)  
 <span data-ttu-id="e663d-152">討論 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 對 LocalDB 功能的支援。</span><span class="sxs-lookup"><span data-stu-id="e663d-152">Discusses [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client support for the LocalDB feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e663d-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e663d-153">See Also</span></span>  
 <span data-ttu-id="e663d-154">[SQL Server Native Client 程式設計](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="e663d-154">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="e663d-155">[ODBC 的使用說明主題](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="e663d-155">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 <span data-ttu-id="e663d-156">[OLE DB how to 主題](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="e663d-156">[OLE DB How-to Topics](../../native-client-ole-db-how-to/ole-db-how-to-topics.md) </span></span>  
 [<span data-ttu-id="e663d-157">安裝 SQL Server Native Client</span><span class="sxs-lookup"><span data-stu-id="e663d-157">Installing SQL Server Native Client</span></span>](../applications/installing-sql-server-native-client.md)  
  
  
