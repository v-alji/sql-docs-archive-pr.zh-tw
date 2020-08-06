---
title: 使用目錄函數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cac35e658343f606c1953f265c752335c70d81f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599480"
---
# <a name="using-catalog-functions"></a><span data-ttu-id="595fc-102">使用目錄函數</span><span class="sxs-lookup"><span data-stu-id="595fc-102">Using Catalog Functions</span></span>
  <span data-ttu-id="595fc-103">所有資料庫都有包含儲存在資料庫之資料的結構。</span><span class="sxs-lookup"><span data-stu-id="595fc-103">All databases have a structure containing the data stored in the database.</span></span> <span data-ttu-id="595fc-104">此結構的定義以及權限之類的其他資訊會儲存在目錄 (當做一組系統資料表實作) 中，也就是所謂的資料字典。</span><span class="sxs-lookup"><span data-stu-id="595fc-104">A definition of this structure, along with other information such as permissions, is stored in a catalog (implemented as a set of system tables), also known as a data dictionary.</span></span>  
  
 <span data-ttu-id="595fc-105">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式可讓應用程式透過呼叫 ODBC 目錄函數來判斷資料庫結構。</span><span class="sxs-lookup"><span data-stu-id="595fc-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver enables an application to determine the database structure through calls to ODBC catalog functions.</span></span> <span data-ttu-id="595fc-106">目錄函數會在結果集中傳回資訊，而且會使用目錄預存程序進行實作以便查詢目錄中的系統資料表。</span><span class="sxs-lookup"><span data-stu-id="595fc-106">Catalog functions return information in result sets and are implemented using catalog stored procedures to query the system tables in the catalog.</span></span> <span data-ttu-id="595fc-107">例如，應用程式可能要求的結果集包含系統上所有資料表，或是特定資料表中所有資料行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="595fc-107">For example, an application might request a result set containing information about all the tables on the system or all the columns in a particular table.</span></span> <span data-ttu-id="595fc-108">標準 ODBC 目錄函數用於取得應用程式所連接之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="595fc-108">The standard ODBC catalog functions are used to get catalog information from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which the application connected.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="595fc-109">支援分散式查詢，其中來自多個異質 OLE DB 資料來源的資料會以單一查詢進行存取。</span><span class="sxs-lookup"><span data-stu-id="595fc-109">supports distributed queries in which data from multiple, heterogeneous OLE DB data sources is accessed in a single query.</span></span> <span data-ttu-id="595fc-110">存取遠端 OLE DB 資料來源的其中一個方法是將資料來源定義為連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="595fc-110">One of the methods of accessing a remote OLE DB data source is to define the data source as a linked server.</span></span> <span data-ttu-id="595fc-111">您可以使用[sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="595fc-111">This can be done by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span> <span data-ttu-id="595fc-112">在定義連結伺服器之後，您可以在 Transact-SQL 陳述式中使用四部份名稱來參考該伺服器中的物件：</span><span class="sxs-lookup"><span data-stu-id="595fc-112">After the linked server has been defined, objects in that server can be referenced in Transact-SQL statements by using a four-part name:</span></span>  
  
 <span data-ttu-id="595fc-113">*linked_server_name. catalog. schema. object_name*。</span><span class="sxs-lookup"><span data-stu-id="595fc-113">*linked_server_name.catalog.schema.object_name*.</span></span>  
  
 <span data-ttu-id="595fc-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援兩種驅動程式專用的函數，可協助取得連結伺服器的目錄資訊：</span><span class="sxs-lookup"><span data-stu-id="595fc-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports two driver-specific functions that help get catalog information from linked servers:</span></span>  
  
-   <span data-ttu-id="595fc-115">**SQLLinkedServers**</span><span class="sxs-lookup"><span data-stu-id="595fc-115">**SQLLinkedServers**</span></span>  
  
     <span data-ttu-id="595fc-116">傳回在本機伺服器上定義的連結伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="595fc-116">Returns a list of the linked servers defined to the local server.</span></span>  
  
-   <span data-ttu-id="595fc-117">**SQLLinkedCatalogs**</span><span class="sxs-lookup"><span data-stu-id="595fc-117">**SQLLinkedCatalogs**</span></span>  
  
     <span data-ttu-id="595fc-118">傳回連結伺服器中所包含的目錄清單。</span><span class="sxs-lookup"><span data-stu-id="595fc-118">Returns a list of the catalogs contained in a linked server.</span></span>  
  
 <span data-ttu-id="595fc-119">當您擁有連結的伺服器名稱和目錄名稱之後， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式支援使用兩部分名稱的_linked_server_name_從目錄中取得資訊 **。** 下列 ODBC 目錄函數的*CatalogName* _目錄_：</span><span class="sxs-lookup"><span data-stu-id="595fc-119">After you have a linked server name and a catalog name, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports getting information from the catalog by using a two-part name of _linked_server_name_**.**_catalog_ for *CatalogName* on the following ODBC catalog functions:</span></span>  
  
-   <span data-ttu-id="595fc-120">**SQLColumnPrivileges**</span><span class="sxs-lookup"><span data-stu-id="595fc-120">**SQLColumnPrivileges**</span></span>  
  
-   <span data-ttu-id="595fc-121">**SQLColumns**</span><span class="sxs-lookup"><span data-stu-id="595fc-121">**SQLColumns**</span></span>  
  
-   <span data-ttu-id="595fc-122">**SQLPrimaryKeys**</span><span class="sxs-lookup"><span data-stu-id="595fc-122">**SQLPrimaryKeys**</span></span>  
  
-   <span data-ttu-id="595fc-123">**SQLStatistics**</span><span class="sxs-lookup"><span data-stu-id="595fc-123">**SQLStatistics**</span></span>  
  
-   <span data-ttu-id="595fc-124">**SQLTablePrivileges**</span><span class="sxs-lookup"><span data-stu-id="595fc-124">**SQLTablePrivileges**</span></span>  
  
-   <span data-ttu-id="595fc-125">**SQLTables**</span><span class="sxs-lookup"><span data-stu-id="595fc-125">**SQLTables**</span></span>  
  
 <span data-ttu-id="595fc-126">兩部分_linked_server_name_**。**[SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md)上的*FKCatalogName*和*sqlforeignkeys*也支援_目錄_。</span><span class="sxs-lookup"><span data-stu-id="595fc-126">The two-part _linked_server_name_**.**_catalog_ is also supported for *FKCatalogName* and *PKCatalogName* on [SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md).</span></span>  
  
 <span data-ttu-id="595fc-127">使用 SQLLinkedServers 和 SQLLinkedCatalogs 需要下列檔案：</span><span class="sxs-lookup"><span data-stu-id="595fc-127">Using SQLLinkedServers and SQLLinkedCatalogs requires the following files:</span></span>  
  
-   <span data-ttu-id="595fc-128">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="595fc-128">sqlncli.h</span></span>  
  
     <span data-ttu-id="595fc-129">包括適用於連結伺服器目錄函數的函數原型與常數定義。</span><span class="sxs-lookup"><span data-stu-id="595fc-129">Includes function prototypes and constant definitions for the linked server catalog functions.</span></span> <span data-ttu-id="595fc-130">sqlncli.h 必須包含在 ODBC 應用程式中，而且必須在應用程式編譯時的 Include 路徑中。</span><span class="sxs-lookup"><span data-stu-id="595fc-130">sqlncli.h must be included in the ODBC application and must be in the include path when the application is compiled.</span></span>  
  
-   <span data-ttu-id="595fc-131">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="595fc-131">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="595fc-132">必須位於連結器 (Linker) 的程式庫路徑中，並指定為要連結的檔案。</span><span class="sxs-lookup"><span data-stu-id="595fc-132">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="595fc-133">sqlncli11.lib 是透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式散發。</span><span class="sxs-lookup"><span data-stu-id="595fc-133">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="595fc-134">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="595fc-134">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="595fc-135">在執行時間必須存在。</span><span class="sxs-lookup"><span data-stu-id="595fc-135">Must be present at execution time.</span></span> <span data-ttu-id="595fc-136">sqlncli11.dll 是透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式散發。</span><span class="sxs-lookup"><span data-stu-id="595fc-136">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595fc-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="595fc-137">See Also</span></span>  
 <span data-ttu-id="595fc-138">[SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="595fc-138">[SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="595fc-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="595fc-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span></span>  
 <span data-ttu-id="595fc-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span><span class="sxs-lookup"><span data-stu-id="595fc-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span></span>  
 <span data-ttu-id="595fc-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span><span class="sxs-lookup"><span data-stu-id="595fc-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span></span>  
 <span data-ttu-id="595fc-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="595fc-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span></span>  
 <span data-ttu-id="595fc-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span><span class="sxs-lookup"><span data-stu-id="595fc-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span></span>  
 [<span data-ttu-id="595fc-144">SQLStatistics</span><span class="sxs-lookup"><span data-stu-id="595fc-144">SQLStatistics</span></span>](../../statistics/statistics.md)  
  
  
