---
title: 其他非 SQL Server 訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3849ca717e82bcf1bed5769190c9f898209a454a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584392"
---
# <a name="other-non-sql-server-subscribers"></a><span data-ttu-id="cdeea-102">其他非 SQL Server 訂閱者</span><span class="sxs-lookup"><span data-stu-id="cdeea-102">Other Non-SQL Server Subscribers</span></span>
  <span data-ttu-id="cdeea-103">如需[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支援的非 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]訂閱者清單，請參閱＜ [Non-SQL Server Subscribers](non-sql-server-subscribers.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cdeea-103">For a list of non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers supported by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Non-SQL Server Subscribers](non-sql-server-subscribers.md).</span></span> <span data-ttu-id="cdeea-104">本主題包含 ODBC 驅動程式和 OLE DB 提供者需求的資訊。</span><span class="sxs-lookup"><span data-stu-id="cdeea-104">This topic includes information about requirements for ODBC drivers and OLE DB providers.</span></span>  
  
## <a name="odbc-driver-requirements"></a><span data-ttu-id="cdeea-105">ODBC 驅動程式需求</span><span class="sxs-lookup"><span data-stu-id="cdeea-105">ODBC Driver Requirements</span></span>  
 <span data-ttu-id="cdeea-106">ODBC 驅動程式：</span><span class="sxs-lookup"><span data-stu-id="cdeea-106">The ODBC driver:</span></span>  
  
-   <span data-ttu-id="cdeea-107">必須與 ODBC (層級 1) 相容。</span><span class="sxs-lookup"><span data-stu-id="cdeea-107">Must be ODBC level-1 compliant.</span></span>  
  
-   <span data-ttu-id="cdeea-108">必須為安全執行緒 (Thread-safe)，且適用於其上執行「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 散發者」的處理器架構 (Intel 或 Alpha) 和平台 (32 位元或 64 位元)。</span><span class="sxs-lookup"><span data-stu-id="cdeea-108">Must be thread-safe, and for the processor architecture (Intel or Alpha) and platform (32 bit or 64 bit) on which the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor runs.</span></span>  
  
-   <span data-ttu-id="cdeea-109">必須能處理交易 (Transaction capable)。</span><span class="sxs-lookup"><span data-stu-id="cdeea-109">Must be transaction capable.</span></span>  
  
-   <span data-ttu-id="cdeea-110">必須支援「資料定義語言」(Data Definition Language，DDL)。</span><span class="sxs-lookup"><span data-stu-id="cdeea-110">Must support the Data Definition Language (DDL).</span></span>  
  
-   <span data-ttu-id="cdeea-111">不能設定成唯讀。</span><span class="sxs-lookup"><span data-stu-id="cdeea-111">Cannot be read-only.</span></span>  
  
-   <span data-ttu-id="cdeea-112">必須支援長資料表名稱，例如 **MSreplication_subscriptions**。</span><span class="sxs-lookup"><span data-stu-id="cdeea-112">Must support long table names such as **MSreplication_subscriptions**.</span></span>  
  
## <a name="replicating-using-ole-db-interfaces"></a><span data-ttu-id="cdeea-113">使用 OLE DB 介面進行複寫</span><span class="sxs-lookup"><span data-stu-id="cdeea-113">Replicating Using OLE DB Interfaces</span></span>  
 <span data-ttu-id="cdeea-114">OLE DB Provider 必須支援下列物件，才能進行異動複寫：</span><span class="sxs-lookup"><span data-stu-id="cdeea-114">OLE DB providers must support these objects for transactional replication:</span></span>  
  
-   <span data-ttu-id="cdeea-115">**DataSource** 物件</span><span class="sxs-lookup"><span data-stu-id="cdeea-115">**DataSource** object</span></span>  
  
-   <span data-ttu-id="cdeea-116">**Session** 物件</span><span class="sxs-lookup"><span data-stu-id="cdeea-116">**Session** object</span></span>  
  
-   <span data-ttu-id="cdeea-117">**Command** 物件</span><span class="sxs-lookup"><span data-stu-id="cdeea-117">**Command** object</span></span>  
  
-   <span data-ttu-id="cdeea-118">**Rowset** 物件</span><span class="sxs-lookup"><span data-stu-id="cdeea-118">**Rowset** object</span></span>  
  
-   <span data-ttu-id="cdeea-119">**Error** 物件</span><span class="sxs-lookup"><span data-stu-id="cdeea-119">**Error** object</span></span>  
  
### <a name="datasource-object-interfaces"></a><span data-ttu-id="cdeea-120">DataSource 物件介面</span><span class="sxs-lookup"><span data-stu-id="cdeea-120">DataSource Object Interfaces</span></span>  
 <span data-ttu-id="cdeea-121">若要連接到某個資料來源，您必須具備下列介面：</span><span class="sxs-lookup"><span data-stu-id="cdeea-121">The following interfaces are required to connect to a data source:</span></span>  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 <span data-ttu-id="cdeea-122">如果提供者支援 **IDBInfo** 介面，[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 便會使用此介面來擷取引號識別項字元、SQL 陳述式長度上限、資料表和資料行名稱的最大字元數等資訊。</span><span class="sxs-lookup"><span data-stu-id="cdeea-122">If the provider supports the **IDBInfo** interface, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses the interface to retrieve information such as the quoted identifier character, maximum SQL statement length, and maximum number of characters in table and column names.</span></span>  
  
### <a name="session-object-interfaces"></a><span data-ttu-id="cdeea-123">Session 物件介面</span><span class="sxs-lookup"><span data-stu-id="cdeea-123">Session Object Interfaces</span></span>  
 <span data-ttu-id="cdeea-124">以下是必要的介面：</span><span class="sxs-lookup"><span data-stu-id="cdeea-124">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="cdeea-125">**IDBCreateCommand**</span><span class="sxs-lookup"><span data-stu-id="cdeea-125">**IDBCreateCommand**</span></span>  
  
-   <span data-ttu-id="cdeea-126">**ITransaction**</span><span class="sxs-lookup"><span data-stu-id="cdeea-126">**ITransaction**</span></span>  
  
-   <span data-ttu-id="cdeea-127">**ITransactionLocal**</span><span class="sxs-lookup"><span data-stu-id="cdeea-127">**ITransactionLocal**</span></span>  
  
-   <span data-ttu-id="cdeea-128">**IDBSchemaRowset**</span><span class="sxs-lookup"><span data-stu-id="cdeea-128">**IDBSchemaRowset**</span></span>  
  
### <a name="command-object-interfaces"></a><span data-ttu-id="cdeea-129">Command 物件介面</span><span class="sxs-lookup"><span data-stu-id="cdeea-129">Command Object Interfaces</span></span>  
 <span data-ttu-id="cdeea-130">以下是必要的介面：</span><span class="sxs-lookup"><span data-stu-id="cdeea-130">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="cdeea-131">**ICommand**</span><span class="sxs-lookup"><span data-stu-id="cdeea-131">**ICommand**</span></span>  
  
-   <span data-ttu-id="cdeea-132">**ICommandProperties**</span><span class="sxs-lookup"><span data-stu-id="cdeea-132">**ICommandProperties**</span></span>  
  
-   <span data-ttu-id="cdeea-133">**ICommandText**</span><span class="sxs-lookup"><span data-stu-id="cdeea-133">**ICommandText**</span></span>  
  
-   <span data-ttu-id="cdeea-134">**ICommandPrepare**</span><span class="sxs-lookup"><span data-stu-id="cdeea-134">**ICommandPrepare**</span></span>  
  
-   <span data-ttu-id="cdeea-135">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="cdeea-135">**IColumnsInfo**</span></span>  
  
-   <span data-ttu-id="cdeea-136">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="cdeea-136">**IAccessor**</span></span>  
  
-   <span data-ttu-id="cdeea-137">**ICommandWithParameters**</span><span class="sxs-lookup"><span data-stu-id="cdeea-137">**ICommandWithParameters**</span></span>  
  
 <span data-ttu-id="cdeea-138">需要**IAccessor** 才能建立參數存取子 (Accessor)。</span><span class="sxs-lookup"><span data-stu-id="cdeea-138">**IAccessor** is necessary to create parameter accessors.</span></span> <span data-ttu-id="cdeea-139">如果提供者支援**IColumnRowset**， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會使用該介面來判斷資料行是否為識別欄位。</span><span class="sxs-lookup"><span data-stu-id="cdeea-139">If the provider supports **IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] uses that interface to determine whether a column is an identity column.</span></span>  
  
### <a name="rowset-object-interfaces"></a><span data-ttu-id="cdeea-140">Rowset 物件介面</span><span class="sxs-lookup"><span data-stu-id="cdeea-140">Rowset Object Interfaces</span></span>  
 <span data-ttu-id="cdeea-141">以下是必要的介面：</span><span class="sxs-lookup"><span data-stu-id="cdeea-141">The following interfaces are required:</span></span>  
  
-   <span data-ttu-id="cdeea-142">**IRowset**</span><span class="sxs-lookup"><span data-stu-id="cdeea-142">**IRowset**</span></span>  
  
-   <span data-ttu-id="cdeea-143">**IAccessor**</span><span class="sxs-lookup"><span data-stu-id="cdeea-143">**IAccessor**</span></span>  
  
-   <span data-ttu-id="cdeea-144">**IColumnsInfo**</span><span class="sxs-lookup"><span data-stu-id="cdeea-144">**IColumnsInfo**</span></span>  
  
 <span data-ttu-id="cdeea-145">應用程式必須在訂閱資料庫中建立的複寫資料表內，開啟一個資料列集。</span><span class="sxs-lookup"><span data-stu-id="cdeea-145">An application should open a rowset on a replicated table that is created in the subscription database.</span></span> <span data-ttu-id="cdeea-146">**IColumnsInfo** 與 **IAccessor** 是存取此資料列集中的資料所必須具備的。</span><span class="sxs-lookup"><span data-stu-id="cdeea-146">**IColumnsInfo** and **IAccessor** are needed to access data in the rowset.</span></span>  
  
### <a name="error-object-interfaces"></a><span data-ttu-id="cdeea-147">Error 物件介面</span><span class="sxs-lookup"><span data-stu-id="cdeea-147">Error Object Interfaces</span></span>  
 <span data-ttu-id="cdeea-148">請使用以下介面來管理錯誤：</span><span class="sxs-lookup"><span data-stu-id="cdeea-148">Use the following interfaces to manage errors:</span></span>  
  
-   <span data-ttu-id="cdeea-149">**IErrorRecords**</span><span class="sxs-lookup"><span data-stu-id="cdeea-149">**IErrorRecords**</span></span>  
  
-   <span data-ttu-id="cdeea-150">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="cdeea-150">**IErrorInfo**</span></span>  
  
 <span data-ttu-id="cdeea-151">若 OLE DB 提供者支援 **ISQLErrorInfo** ，請使用此介面。</span><span class="sxs-lookup"><span data-stu-id="cdeea-151">Use **ISQLErrorInfo** if it is supported by the OLE DB provider.</span></span>  
  
 <span data-ttu-id="cdeea-152">如需 OLE DB 提供者的詳細資訊，請參閱您 OLE DB 提供者所附的文件。</span><span class="sxs-lookup"><span data-stu-id="cdeea-152">For more information about the OLE DB provider, see the documentation supplied with your OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdeea-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdeea-153">See Also</span></span>  
 [<span data-ttu-id="cdeea-154">非 SQL Server 訂閱者</span><span class="sxs-lookup"><span data-stu-id="cdeea-154">Non-SQL Server Subscribers</span></span>](non-sql-server-subscribers.md)  
  
  
