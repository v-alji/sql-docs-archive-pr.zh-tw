---
title: 資料表與索引 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: rothja
ms.author: jroth
ms.openlocfilehash: abc7c314e433eb9f107bd191738d951706f1b50d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597082"
---
# <a name="tables-and-indexes"></a><span data-ttu-id="21140-102">資料表和索引</span><span class="sxs-lookup"><span data-stu-id="21140-102">Tables and Indexes</span></span>
  <span data-ttu-id="21140-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會公開**IIndexDefinition**和**ITableDefinition**介面，讓取用者建立、改變和卸載 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表和索引。</span><span class="sxs-lookup"><span data-stu-id="21140-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition** and **ITableDefinition** interfaces, allowing consumers to create, alter, and drop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and indexes.</span></span> <span data-ttu-id="21140-104">有效的資料表和索引定義是取決於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本。</span><span class="sxs-lookup"><span data-stu-id="21140-104">Valid table and index definitions depend on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="21140-105">建立或卸除資料表和索引的能力，取決於取用者應用程式使用者的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取權限。</span><span class="sxs-lookup"><span data-stu-id="21140-105">The ability to create or drop tables and indexes depends on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access rights of the consumer-application user.</span></span> <span data-ttu-id="21140-106">卸除資料表可藉由宣告式參考完整性條件約束或其他因數的存在，而受進一步的條件約束。</span><span class="sxs-lookup"><span data-stu-id="21140-106">Dropping a table can be further constrained by the presence of declarative referential integrity constraints or other factors.</span></span>  
  
 <span data-ttu-id="21140-107">大部分的應用程式目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 都使用 sql-dmo，而不是這些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者介面。</span><span class="sxs-lookup"><span data-stu-id="21140-107">Most applications targeting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use SQL-DMO instead of these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interfaces.</span></span> <span data-ttu-id="21140-108">SQL-DMO 是 OLE Automation 物件的集合，可支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所有的管理功能。</span><span class="sxs-lookup"><span data-stu-id="21140-108">SQL-DMO is a collection of OLE Automation objects that support all the administrative functions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="21140-109">以多個 OLE DB 提供者為目標的應用程式會使用這些受多個 OLE DB 提供者支援的一般 OLE DB 介面。</span><span class="sxs-lookup"><span data-stu-id="21140-109">Applications targeting multiple OLE DB providers use these generic OLE DB interfaces that are supported by the various OLE DB providers.</span></span>  
  
 <span data-ttu-id="21140-110">在提供者特定屬性集 DBPROPSET_SQLSERVERCOLUMN 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會定義下列屬性。</span><span class="sxs-lookup"><span data-stu-id="21140-110">In the provider-specific property set DBPROPSET_SQLSERVERCOLUMN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defines the following property.</span></span>  
  
|<span data-ttu-id="21140-111">屬性識別碼</span><span class="sxs-lookup"><span data-stu-id="21140-111">Property ID</span></span>|<span data-ttu-id="21140-112">描述</span><span class="sxs-lookup"><span data-stu-id="21140-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="21140-113">SSPROP_COL_COLLATIONNAME</span><span class="sxs-lookup"><span data-stu-id="21140-113">SSPROP_COL_COLLATIONNAME</span></span>|<span data-ttu-id="21140-114">輸入：VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="21140-114">Type: VT_BSTR</span></span><br /><br /> <span data-ttu-id="21140-115">R/W：寫入</span><span class="sxs-lookup"><span data-stu-id="21140-115">R/W: Write</span></span><br /><br /> <span data-ttu-id="21140-116">預設值：Null</span><span class="sxs-lookup"><span data-stu-id="21140-116">Default: Null</span></span><br /><br /> <span data-ttu-id="21140-117">描述：此屬性只能用於 **ITableDefinition**。</span><span class="sxs-lookup"><span data-stu-id="21140-117">Description: This property is used only in **ITableDefinition**.</span></span> <span data-ttu-id="21140-118">在建立 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 時會使用這個屬性指定的字串</span><span class="sxs-lookup"><span data-stu-id="21140-118">The string specified in this property is used when creating a [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)</span></span><br /><br /> <span data-ttu-id="21140-119">陳述式。</span><span class="sxs-lookup"><span data-stu-id="21140-119">statement.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="21140-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="21140-120">In This Section</span></span>  
  
-   [<span data-ttu-id="21140-121">建立 SQL Server 資料表</span><span class="sxs-lookup"><span data-stu-id="21140-121">Creating SQL Server Tables</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [<span data-ttu-id="21140-122">將資料行新增至 SQL Server 資料表</span><span class="sxs-lookup"><span data-stu-id="21140-122">Adding a Column to a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [<span data-ttu-id="21140-123">從 SQL Server 資料表中移除資料行</span><span class="sxs-lookup"><span data-stu-id="21140-123">Removing a Column from a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [<span data-ttu-id="21140-124">卸除 SQL Server 資料表</span><span class="sxs-lookup"><span data-stu-id="21140-124">Dropping a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [<span data-ttu-id="21140-125">建立 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="21140-125">Creating SQL Server Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
-   [<span data-ttu-id="21140-126">卸除 SQL Server 索引</span><span class="sxs-lookup"><span data-stu-id="21140-126">Dropping a SQL Server Index</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a><span data-ttu-id="21140-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21140-127">See Also</span></span>  
 <span data-ttu-id="21140-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="21140-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 <span data-ttu-id="21140-129">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="21140-129">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 <span data-ttu-id="21140-130">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="21140-130">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="21140-131">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="21140-131">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
