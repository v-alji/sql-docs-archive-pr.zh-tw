---
title: SQL Server Native Client (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, about SQL Server Native Client OLE DB provider
- OLE DB, SQL Server Native Client OLE DB provider
- data access [SQL Server Native Client], OLE DB
- SQLNCLI, OLE DB
- OLE DB
- SQL Server Native Client OLE DB provider
- SQL Server Native Client, OLE DB
ms.assetid: da846da4-ec19-4a4f-81fb-7d5a2b2bf80a
author: rothja
ms.author: jroth
ms.openlocfilehash: 46b948eb1d075edc6000849dcb2d18ea372809d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594514"
---
# <a name="sql-server-native-client-ole-db"></a><span data-ttu-id="8992a-102">SQL Server Native Client (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="8992a-102">SQL Server Native Client (OLE DB)</span></span>
  <span data-ttu-id="8992a-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者是用於存取資料的低階 COM API。</span><span class="sxs-lookup"><span data-stu-id="8992a-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a low-level COM API that is used for accessing data.</span></span> <span data-ttu-id="8992a-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 建議將 Native Client OLE DB 提供者用於開發工具、公用程式或需要高效能的低階元件。</span><span class="sxs-lookup"><span data-stu-id="8992a-104">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is recommended for developing tools, utilities, or low-level components that need high performance.</span></span> <span data-ttu-id="8992a-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者是原生、高效能的提供者，會直接存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表格式資料流 (TDS) 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8992a-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is a native, high performance provider that accesses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabular Data Stream (TDS) protocol directly.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="8992a-106">Native Client 會對連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的應用程式提供 OLE DB 支援。</span><span class="sxs-lookup"><span data-stu-id="8992a-106">Native Client provides OLE DB support to applications connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8992a-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者是 OLE DB 版本2.0 相容提供者。</span><span class="sxs-lookup"><span data-stu-id="8992a-107">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider is an OLE DB version 2.0-compliant provider.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8992a-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="8992a-108">In This Section</span></span>  
  
-   [<span data-ttu-id="8992a-109">建立 SQL Server Native Client OLE DB 提供者應用程式</span><span class="sxs-lookup"><span data-stu-id="8992a-109">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](../../native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [<span data-ttu-id="8992a-110">資料來源物件 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-110">Data Source Objects &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [<span data-ttu-id="8992a-111">命令</span><span class="sxs-lookup"><span data-stu-id="8992a-111">Commands</span></span>](../../native-client-ole-db-commands/commands.md)  
  
-   [<span data-ttu-id="8992a-112">資料列集</span><span class="sxs-lookup"><span data-stu-id="8992a-112">Rowsets</span></span>](../../native-client-ole-db-rowsets/rowsets.md)  
  
-   [<span data-ttu-id="8992a-113">預存程式</span><span class="sxs-lookup"><span data-stu-id="8992a-113">Stored Procedures</span></span>](stored-procedures.md)  
  
-   [<span data-ttu-id="8992a-114">BLOB 與 OLE 物件</span><span class="sxs-lookup"><span data-stu-id="8992a-114">BLOBs and OLE Objects</span></span>](../../native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [<span data-ttu-id="8992a-115">資料表和索引</span><span class="sxs-lookup"><span data-stu-id="8992a-115">Tables and Indexes</span></span>](../../native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [<span data-ttu-id="8992a-116">資料類型 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-116">Data Types &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [<span data-ttu-id="8992a-117">結構描述資料列集支援 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-117">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
-   [<span data-ttu-id="8992a-118">資料表值參數 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-118">Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [<span data-ttu-id="8992a-119">日期和時間改善 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-119">Date and Time Improvements &#40;OLE DB&#41;</span></span>](../../native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [<span data-ttu-id="8992a-120">大型 CLR 使用者定義型別 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-120">Large CLR User-Defined Types &#40;OLE DB&#41;</span></span>](large-clr-user-defined-types-ole-db.md)  
  
-   [<span data-ttu-id="8992a-121">FILESTREAM 支援 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-121">FILESTREAM Support &#40;OLE DB&#41;</span></span>](filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="8992a-122">交易</span><span class="sxs-lookup"><span data-stu-id="8992a-122">Transactions</span></span>](../../native-client-ole-db-transactions/transactions.md)  
  
-   [<span data-ttu-id="8992a-123">錯誤</span><span class="sxs-lookup"><span data-stu-id="8992a-123">Errors</span></span>](../../native-client-ole-db-errors/errors.md)  
  
-   [<span data-ttu-id="8992a-124">用戶端連接 &#40;OLE DB&#41; 中的服務主體名稱 &#40;SPN&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-124">Service Principal Names &#40;SPNs&#41; in Client Connections &#40;OLE DB&#41;</span></span>](service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [<span data-ttu-id="8992a-125">疏鬆資料行支援 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8992a-125">Sparse Columns Support &#40;OLE DB&#41;</span></span>](sparse-columns-support-ole-db.md)  
  
-   [<span data-ttu-id="8992a-126">SQL Server Native Client &#40;OLE DB&#41; 參考</span><span class="sxs-lookup"><span data-stu-id="8992a-126">SQL Server Native Client &#40;OLE DB&#41; Reference</span></span>](../../native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [<span data-ttu-id="8992a-127">OLE DB 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="8992a-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="8992a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8992a-128">See Also</span></span>  
 [<span data-ttu-id="8992a-129">SQL Server Native Client 程式設計</span><span class="sxs-lookup"><span data-stu-id="8992a-129">SQL Server Native Client Programming</span></span>](../sql-server-native-client-programming.md)  
  
  
