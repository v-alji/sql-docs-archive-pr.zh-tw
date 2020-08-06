---
title: 使用快照集隔離 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], snapshot isolation
- SQLNCLI, snapshot isolation
- isolation levels [SQL Server], snapshot
- DBPROPSET_SESSION property set
- DBDROPSET_DATASOURCEINFO property set
- snapshot isolation [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, snapshot isolation
- SQL Server Native Client ODBC driver, snapshot isolation
- SQL Server Native Client, snapshot isolation
- SQLGetInfo function
- concurrency [SQL Server Native Client]
- SQLSetConnectAttr function
ms.assetid: 39e87eb1-677e-45dd-bc61-83a4025a7756
author: rothja
ms.author: jroth
ms.openlocfilehash: 242d054a5fd2ad12a8811bebc834d423f547a499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598307"
---
# <a name="working-with-snapshot-isolation"></a><span data-ttu-id="46b66-102">使用快照隔離</span><span class="sxs-lookup"><span data-stu-id="46b66-102">Working with Snapshot Isolation</span></span>
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="46b66-103">引進了新的「快照」隔離等級，目的是增強線上交易處理 (OLTP) 應用程式的並行存取。</span><span class="sxs-lookup"><span data-stu-id="46b66-103">introduced a new "snapshot" isolation level that is intended to enhance concurrency for online transaction processing (OLTP) applications.</span></span> <span data-ttu-id="46b66-104">在舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，並行存取完全以鎖定為基礎，因此導致某些應用程式發生封鎖及死結問題。</span><span class="sxs-lookup"><span data-stu-id="46b66-104">In earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], concurrency was based solely on locking, which can cause blocking and deadlocking problems for some applications.</span></span> <span data-ttu-id="46b66-105">快照集隔離相依於對資料列版本設定的增強功能，目的是藉由避免發生讀取器-寫入器封鎖的案例來改善效能。</span><span class="sxs-lookup"><span data-stu-id="46b66-105">Snapshot isolation depends on enhancements to row versioning and is intended to improve performance by avoiding reader-writer blocking scenarios.</span></span>  
  
 <span data-ttu-id="46b66-106">在快照隔離下啟動的交易會根據交易啟動的時間而讀取資料庫快照。</span><span class="sxs-lookup"><span data-stu-id="46b66-106">Transactions that start under snapshot isolation read a database snapshot as of the time when the transaction starts.</span></span> <span data-ttu-id="46b66-107">其結果之一，就是索引鍵集、動態和靜態伺服器資料指標在快照交易內容內開啟時，其行為與在可序列化交易內開啟的靜態資料指標非常類似。</span><span class="sxs-lookup"><span data-stu-id="46b66-107">One result of this is that keyset, dynamic and static server cursors, when opened within a snapshot transaction context, behave much like static cursors opened within serializable transactions.</span></span> <span data-ttu-id="46b66-108">不過，當資料指標開啟時，快照隔離等級並不會鎖定，因而可能減少伺服器上發生封鎖的機會。</span><span class="sxs-lookup"><span data-stu-id="46b66-108">However, when the cursors are opened under the snapshot isolation level locks are not taken, which can reduce blocking on the server.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="46b66-109">SQL Server Native Client OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="46b66-109">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="46b66-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者具有增強功能，可利用中引進的快照集隔離 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="46b66-110">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider has enhancements that take advantage of the snapshot isolation introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="46b66-111">這些增強功能包括對 DBPROPSET_DATASOURCEINFO 和 DBPROPSET_SESSION 屬性集所做的變更。</span><span class="sxs-lookup"><span data-stu-id="46b66-111">These enhancements include changes to the DBPROPSET_DATASOURCEINFO and DBPROPSET_SESSION property sets.</span></span>  
  
### <a name="dbpropset_datasourceinfo"></a><span data-ttu-id="46b66-112">DBPROPSET_DATASOURCEINFO</span><span class="sxs-lookup"><span data-stu-id="46b66-112">DBPROPSET_DATASOURCEINFO</span></span>  
 <span data-ttu-id="46b66-113">DBPROPSET_DATASOURCEINFO 屬性集已變更，現藉由加入用於 DBPROP_SUPPORTEDTXNISOLEVELS 屬性中的 DBPROPVAL_TI_SNAPSHOT 值來支援快照隔離等級。</span><span class="sxs-lookup"><span data-stu-id="46b66-113">The DBPROPSET_DATASOURCEINFO property set has been changed to indicate that the snapshot isolation level is supported by the addition of the DBPROPVAL_TI_SNAPSHOT value that is used in the DBPROP_SUPPORTEDTXNISOLEVELS property.</span></span> <span data-ttu-id="46b66-114">這個新值代表不論資料庫上是否啟用版本控制，快照隔離等級都受到支援。</span><span class="sxs-lookup"><span data-stu-id="46b66-114">This new value indicates that the snapshot isolation level is supported whether or not versioning has been enabled on the database.</span></span> <span data-ttu-id="46b66-115">下列是 DBPROP_SUPPORTEDTXNISOLEVELS 值的清單：</span><span class="sxs-lookup"><span data-stu-id="46b66-115">The following is a list of the DBPROP_SUPPORTEDTXNISOLEVELS values:</span></span>  
  
|<span data-ttu-id="46b66-116">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="46b66-116">Property ID</span></span>|<span data-ttu-id="46b66-117">描述</span><span class="sxs-lookup"><span data-stu-id="46b66-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="46b66-118">DBPROP_SUPPORTEDTXNISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="46b66-118">DBPROP_SUPPORTEDTXNISOLEVELS</span></span>|<span data-ttu-id="46b66-119">類型：VT_I4</span><span class="sxs-lookup"><span data-stu-id="46b66-119">Type: VT_I4</span></span><br /><br /> <span data-ttu-id="46b66-120">R/W：唯讀</span><span class="sxs-lookup"><span data-stu-id="46b66-120">R/W: Read only</span></span><br /><br /> <span data-ttu-id="46b66-121">說明：指定受支援之交易隔離等級的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="46b66-121">Description: A bitmask specifying the supported transaction isolation levels.</span></span> <span data-ttu-id="46b66-122">下列零或多個項目的組合：</span><span class="sxs-lookup"><span data-stu-id="46b66-122">A combination of zero or more of the following:</span></span><br /><br /> <span data-ttu-id="46b66-123">-DBPROPVAL_TI_CHAOS</span><span class="sxs-lookup"><span data-stu-id="46b66-123">-   DBPROPVAL_TI_CHAOS</span></span><br /><span data-ttu-id="46b66-124">-DBPROPVAL_TI_READUNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="46b66-124">-   DBPROPVAL_TI_READUNCOMMITTED</span></span><br /><span data-ttu-id="46b66-125">-DBPROPVAL_TI_BROWSE</span><span class="sxs-lookup"><span data-stu-id="46b66-125">-   DBPROPVAL_TI_BROWSE</span></span><br /><span data-ttu-id="46b66-126">-DBPROPVAL_TI_CURSORSTABILITY</span><span class="sxs-lookup"><span data-stu-id="46b66-126">-   DBPROPVAL_TI_CURSORSTABILITY</span></span><br /><span data-ttu-id="46b66-127">-DBPROPVAL_TI_READCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="46b66-127">-   DBPROPVAL_TI_READCOMMITTED</span></span><br /><span data-ttu-id="46b66-128">-DBPROPVAL_TI_REPEATABLEREAD</span><span class="sxs-lookup"><span data-stu-id="46b66-128">-   DBPROPVAL_TI_REPEATABLEREAD</span></span><br /><span data-ttu-id="46b66-129">-DBPROPVAL_TI_SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="46b66-129">-   DBPROPVAL_TI_SERIALIZABLE</span></span><br /><span data-ttu-id="46b66-130">-DBPROPVAL_TI_ISOLATED</span><span class="sxs-lookup"><span data-stu-id="46b66-130">-   DBPROPVAL_TI_ISOLATED</span></span><br /><span data-ttu-id="46b66-131">-DBPROPVAL_TI_SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="46b66-131">-   DBPROPVAL_TI_SNAPSHOT</span></span>|  
  
### <a name="dbpropset_session"></a><span data-ttu-id="46b66-132">DBPROPSET_SESSION</span><span class="sxs-lookup"><span data-stu-id="46b66-132">DBPROPSET_SESSION</span></span>  
 <span data-ttu-id="46b66-133">DBPROPSET_SESSION 屬性集已變更，現藉由加入用於 DBPROP_SESS_AUTOCOMMITISOLEVELS 屬性中的 DBPROPVAL_TI_SNAPSHOT 值來支援快照隔離等級。</span><span class="sxs-lookup"><span data-stu-id="46b66-133">The DBPROPSET_SESSION property set has been changed to indicate that the snapshot isolation level is supported by the addition of the DBPROPVAL_TI_SNAPSHOT value that is used in the DBPROP_SESS_AUTOCOMMITISOLEVELS property.</span></span> <span data-ttu-id="46b66-134">這個新值代表不論資料庫上是否啟用版本控制，快照隔離等級都受到支援。</span><span class="sxs-lookup"><span data-stu-id="46b66-134">This new value indicates that the snapshot isolation level is supported whether or not versioning has been enabled on the database.</span></span> <span data-ttu-id="46b66-135">下列是 DBPROP_SESS_AUTOCOMMITISOLEVELS 值的清單：</span><span class="sxs-lookup"><span data-stu-id="46b66-135">The following is a list of the DBPROP_SESS_AUTOCOMMITISOLEVELS values:</span></span>  
  
|<span data-ttu-id="46b66-136">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="46b66-136">Property ID</span></span>|<span data-ttu-id="46b66-137">描述</span><span class="sxs-lookup"><span data-stu-id="46b66-137">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="46b66-138">DBPROP_SESS_AUTOCOMMITISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="46b66-138">DBPROP_SESS_AUTOCOMMITISOLEVELS</span></span>|<span data-ttu-id="46b66-139">類型：VT_I4</span><span class="sxs-lookup"><span data-stu-id="46b66-139">Type: VT_I4</span></span><br /><br /> <span data-ttu-id="46b66-140">R/W：唯讀</span><span class="sxs-lookup"><span data-stu-id="46b66-140">R/W: Read only</span></span><br /><br /> <span data-ttu-id="46b66-141">說明：指定自動認可模式時之交易隔離等級的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="46b66-141">Description: Specifies a bitmask that indicates the transaction isolation level while in auto-commit mode.</span></span> <span data-ttu-id="46b66-142">在此位元遮罩中設定的值，與針對 DBPROP_SUPPORTEDTXNISOLEVELS 而設定的值相同。</span><span class="sxs-lookup"><span data-stu-id="46b66-142">The values that can be set in this bitmask are the same as those that can be set for DBPROP_SUPPORTEDTXNISOLEVELS.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="46b66-143">如果使用早於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 版本時設定 DBPROPVAL_TI_SNAPSHOT，就會發生 DB_S_ERRORSOCCURRED 或 DB_E_ERRORSOCCURRED 錯誤。</span><span class="sxs-lookup"><span data-stu-id="46b66-143">The errors DB_S_ERRORSOCCURRED or DB_E_ERRORSOCCURRED will occur if DBPROPVAL_TI_SNAPSHOT is set when using versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] earlier than [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="46b66-144">如需如何在交易中支援快照集隔離的詳細資訊，請參閱[支援本機交易](../../native-client-ole-db-transactions/transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="46b66-144">For information about how snapshot isolation is supported in transactions, see [Supporting Local Transactions](../../native-client-ole-db-transactions/transactions.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="46b66-145">SQL Server Native Client ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="46b66-145">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="46b66-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會提供快照集隔離的支援，但對[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)和[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)函式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="46b66-146">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver provides support for snapshot isolation though enhancements made to the [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) and [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) functions.</span></span>  
  
### <a name="sqlsetconnectattr"></a><span data-ttu-id="46b66-147">SQLSetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="46b66-147">SQLSetConnectAttr</span></span>  
 <span data-ttu-id="46b66-148">**SQLSetConnectAttr**函數現在支援 SQL_COPT_SS_TXN_ISOLATION 屬性的使用。</span><span class="sxs-lookup"><span data-stu-id="46b66-148">The **SQLSetConnectAttr** function now supports the use of the SQL_COPT_SS_TXN_ISOLATION attribute.</span></span> <span data-ttu-id="46b66-149">將 SQL_COPT_SS_TXN_ISOLATION 設定為 SQL_TXN_SS_SNAPSHOT 代表交易會在快照隔離等級之下發生。</span><span class="sxs-lookup"><span data-stu-id="46b66-149">Setting SQL_COPT_SS_TXN_ISOLATION to SQL_TXN_SS_SNAPSHOT indicates that the transaction will take place under the snapshot isolation level.</span></span>  
  
### <a name="sqlgetinfo"></a><span data-ttu-id="46b66-150">SQLGetInfo</span><span class="sxs-lookup"><span data-stu-id="46b66-150">SQLGetInfo</span></span>  
 <span data-ttu-id="46b66-151">[SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md)函數現在支援已加入 SQL_TXN_ISOLATION_OPTION info 類型的 SQL_TXN_SS_SNAPSHOT 值。</span><span class="sxs-lookup"><span data-stu-id="46b66-151">The [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) function now supports the SQL_TXN_SS_SNAPSHOT value that has been added to the SQL_TXN_ISOLATION_OPTION info type.</span></span>  
  
 <span data-ttu-id="46b66-152">如需如何在交易中支援快照集隔離的詳細資訊，請參閱資料[指標交易隔離等級](../../native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md)。</span><span class="sxs-lookup"><span data-stu-id="46b66-152">For information about how snapshot isolation is supported in transactions, see [Cursor Transaction Isolation Level](../../native-client-odbc-cursors/properties/cursor-transaction-isolation-level.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b66-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46b66-153">See Also</span></span>  
 <span data-ttu-id="46b66-154">[SQL Server Native Client 功能](sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="46b66-154">[SQL Server Native Client Features](sql-server-native-client-features.md) </span></span>  
 [<span data-ttu-id="46b66-155">資料列集屬性和行為</span><span class="sxs-lookup"><span data-stu-id="46b66-155">Rowset Properties and Behaviors</span></span>](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)  
  
  
