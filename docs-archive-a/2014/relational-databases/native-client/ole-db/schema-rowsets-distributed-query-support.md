---
title: 結構描述資料列集中的分散式查詢支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: rothja
ms.author: jroth
ms.openlocfilehash: 48b57bbf40590f8ad5c049268f25fe66d2f94357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592654"
---
# <a name="distributed-query-support-in-schema-rowsets"></a><span data-ttu-id="f6520-102">結構描述資料列集中的分散式查詢支援</span><span class="sxs-lookup"><span data-stu-id="f6520-102">Distributed Query Support in Schema Rowsets</span></span>
  <span data-ttu-id="f6520-103">為了支援 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散式查詢， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者**IDBSchemaRowset**介面會傳回連結伺服器上的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f6520-103">To support [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider **IDBSchemaRowset** interface returns metadata on linked servers.</span></span>  
  
 <span data-ttu-id="f6520-104">如果 DBPROPSET_SQLSERVERSESSION 屬性 SSPROP_QUOTEDCATALOGNAMES 是 VARIANT_TRUE，您就可以針對目錄名稱指定引號識別碼 (例如 "my.catalog")。</span><span class="sxs-lookup"><span data-stu-id="f6520-104">If the DBPROPSET_SQLSERVERSESSION property SSPROP_QUOTEDCATALOGNAMES is VARIANT_TRUE, a quoted identifier can be specified for the catalog name (for example "my.catalog").</span></span> <span data-ttu-id="f6520-105">當根據目錄來限制架構資料列集輸出時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者會辨識包含連結伺服器和目錄名稱的兩部分名稱。</span><span class="sxs-lookup"><span data-stu-id="f6520-105">When restricting schema rowset output by catalog, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes a two-part name containing the linked server and catalog name.</span></span> <span data-ttu-id="f6520-106">針對下表中的架構資料列集，將兩部分的目錄名稱指定為_linked_server_**。**_目錄_會將輸出限制為所指定連結伺服器的適用類別目錄。</span><span class="sxs-lookup"><span data-stu-id="f6520-106">For the schema rowsets in the table below, specifying a two-part catalog name as _linked_server_**.**_catalog_ restricts output to the applicable catalog of the named linked server.</span></span>  
  
|<span data-ttu-id="f6520-107">結構描述資料列集</span><span class="sxs-lookup"><span data-stu-id="f6520-107">Schema rowset</span></span>|<span data-ttu-id="f6520-108">目錄限制</span><span class="sxs-lookup"><span data-stu-id="f6520-108">Catalog restriction</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="f6520-109">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="f6520-109">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="f6520-110">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="f6520-110">CATALOG_NAME</span></span>|  
|<span data-ttu-id="f6520-111">DBSCHEMA_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="f6520-111">DBSCHEMA_COLUMNS</span></span>|<span data-ttu-id="f6520-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6520-112">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="f6520-113">DBSCHEMA_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="f6520-113">DBSCHEMA_PRIMARY_KEYS</span></span>|<span data-ttu-id="f6520-114">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6520-114">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="f6520-115">DBSCHEMA_TABLES</span><span class="sxs-lookup"><span data-stu-id="f6520-115">DBSCHEMA_TABLES</span></span>|<span data-ttu-id="f6520-116">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6520-116">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="f6520-117">DBSCHEMA_FOREIGN_KEYS</span><span class="sxs-lookup"><span data-stu-id="f6520-117">DBSCHEMA_FOREIGN_KEYS</span></span>|<span data-ttu-id="f6520-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6520-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span></span>|  
|<span data-ttu-id="f6520-119">DBSCHEMA_INDEXES</span><span class="sxs-lookup"><span data-stu-id="f6520-119">DBSCHEMA_INDEXES</span></span>|<span data-ttu-id="f6520-120">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6520-120">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="f6520-121">DBSCHEMA_COLUMN_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="f6520-121">DBSCHEMA_COLUMN_PRIVILEGES</span></span>|<span data-ttu-id="f6520-122">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6520-122">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="f6520-123">DBSCHEMA_TABLE_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="f6520-123">DBSCHEMA_TABLE_PRIVILEGES</span></span>|<span data-ttu-id="f6520-124">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f6520-124">TABLE_CATALOG</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="f6520-125">若要將結構描述資料列集限制為連結伺服器的所有目錄，請使用語法 *linked_server* (其中句號分隔符號是名稱規格的一部分)。</span><span class="sxs-lookup"><span data-stu-id="f6520-125">To restrict a schema rowset to all catalogs from a linked server, use the syntax *linked_server* (where the period separator is part of the name specification).</span></span> <span data-ttu-id="f6520-126">這個語法相當於針對目錄名稱限制指定 NULL，而且也會在連結的伺服器指出不支援目錄的資料來源時使用。</span><span class="sxs-lookup"><span data-stu-id="f6520-126">This syntax is equivalent to specifying NULL for the catalog name restriction and is also used when the linked server indicates a data source that does not support catalogs.</span></span>  
  
 <span data-ttu-id="f6520-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會定義架構資料列集 LINKEDSERVERS，並傳回註冊為連結伺服器之 OLE DB 資料來源的清單。</span><span class="sxs-lookup"><span data-stu-id="f6520-127">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the schema rowset LINKEDSERVERS, returning a list of OLE DB data sources registered as linked servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6520-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6520-128">See Also</span></span>  
 <span data-ttu-id="f6520-129">[架構資料列集支援 &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="f6520-129">[Schema Rowset Support &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span></span>  
 [<span data-ttu-id="f6520-130">LINKEDSERVERS 資料列集 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="f6520-130">LINKEDSERVERS Rowset &#40;OLE DB&#41;</span></span>](schema-rowsets-linkedservers-rowset.md)  
  
  
