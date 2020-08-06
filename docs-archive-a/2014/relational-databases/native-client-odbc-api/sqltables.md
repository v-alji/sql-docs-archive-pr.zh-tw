---
title: SQLTables |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: rothja
ms.author: jroth
ms.openlocfilehash: bad60aa102a7771935e37ac963e6fa0d3cb2fd57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595951"
---
# <a name="sqltables"></a><span data-ttu-id="d51a3-102">SQLTables</span><span class="sxs-lookup"><span data-stu-id="d51a3-102">SQLTables</span></span>
  <span data-ttu-id="d51a3-103">SQLTables 可以在靜態伺服器資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="d51a3-103">SQLTables can be executed on a static server cursor.</span></span> <span data-ttu-id="d51a3-104">嘗試在可更新的 (動態或索引鍵集) 資料指標上執行 SQLTables 時，將會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="d51a3-104">An attempt to execute SQLTables on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="d51a3-105">當 SQL_ALL_CATALOGS *CatalogName*參數，而且所有其他參數都包含 (Null 指標) 的預設值時，SQLTables 會報告所有資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="d51a3-105">SQLTables reports tables from all databases when the *CatalogName* parameter is SQL_ALL_CATALOGS and all other parameters contain default values (NULL pointers).</span></span>  
  
 <span data-ttu-id="d51a3-106">若要報告可用的目錄、架構和資料表類型，SQLTables 會特別使用空字串 (長度為零的位元組指標) 。</span><span class="sxs-lookup"><span data-stu-id="d51a3-106">To report available catalogs, schemas, and table types, SQLTables makes special use of empty strings (zero-length byte pointers).</span></span> <span data-ttu-id="d51a3-107">空字串不是預設值 (NULL 指標)。</span><span class="sxs-lookup"><span data-stu-id="d51a3-107">Empty strings are not default values (NULL pointers).</span></span>  
  
 <span data-ttu-id="d51a3-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式藉由接受*CatalogName*參數的兩部分名稱，支援連結伺服器上之資料表的報告資訊： *Linked_Server_Name. Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="d51a3-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
 <span data-ttu-id="d51a3-109">SQLTables 會傳回名稱符合*TableName*且由目前使用者擁有之任何資料表的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d51a3-109">SQLTables returns information about any tables whose names match *TableName* and are owned by the current user.</span></span>  
  
## <a name="sqltables-and-table-valued-parameters"></a><span data-ttu-id="d51a3-110">SQLTables 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="d51a3-110">SQLTables and Table-Valued Parameters</span></span>  
 <span data-ttu-id="d51a3-111">當語句屬性 SQL_SOPT_SS_NAME_SCOPE 的值 SQL_SS_NAME_SCOPE_TABLE_TYPE，而不是其預設值 SQL_SS_NAME_SCOPE_TABLE 時，SQLTables 會傳回資料表類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d51a3-111">When the statement attribute SQL_SOPT_SS_NAME_SCOPE has the value SQL_SS_NAME_SCOPE_TABLE_TYPE, rather than its default value of SQL_SS_NAME_SCOPE_TABLE, SQLTables returns information about table types.</span></span> <span data-ttu-id="d51a3-112">在 SQLTables 所傳回之結果集的資料行4中，針對資料表類型傳回的 TABLE_TYPE 值為 TABLE 類型。</span><span class="sxs-lookup"><span data-stu-id="d51a3-112">The TABLE_TYPE value returned for a table type in column 4 of the result set returned by SQLTables is TABLE TYPE.</span></span> <span data-ttu-id="d51a3-113">如需 SQL_SOPT_SS_NAME_SCOPE 的詳細資訊，請參閱[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="d51a3-113">For more information on SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="d51a3-114">資料表、檢視與同義字共用與資料表類型所使用之命名空間不同的一般命名空間。</span><span class="sxs-lookup"><span data-stu-id="d51a3-114">Tables, views, and synonyms share a common namespace that is distinct from the namespace used by table types.</span></span> <span data-ttu-id="d51a3-115">雖然不可能擁有具有相同名稱的資料表和檢視，但是在相同的目錄和結構描述中，可能擁有具有相同名稱的資料表和資料表類型。</span><span class="sxs-lookup"><span data-stu-id="d51a3-115">Although it is not possible to have a table and a view with the same name, it is possible to have a table and a table type with the same in the same catalog and schema.</span></span>  
  
 <span data-ttu-id="d51a3-116">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="d51a3-116">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d51a3-117">範例</span><span class="sxs-lookup"><span data-stu-id="d51a3-117">Example</span></span>  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d51a3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d51a3-118">See Also</span></span>  
 <span data-ttu-id="d51a3-119">[SQLTables 函式](https://go.microsoft.com/fwlink/?LinkId=59374) </span><span class="sxs-lookup"><span data-stu-id="d51a3-119">[SQLTables Function](https://go.microsoft.com/fwlink/?LinkId=59374) </span></span>  
 [<span data-ttu-id="d51a3-120">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="d51a3-120">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
