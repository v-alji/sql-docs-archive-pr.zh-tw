---
title: SQLPrimaryKeys |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: rothja
ms.author: jroth
ms.openlocfilehash: 67a932996ccbf52f5ab21fd6aa62381184ebc510
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606263"
---
# <a name="sqlprimarykeys"></a><span data-ttu-id="b1fcb-102">SQLPrimaryKeys</span><span class="sxs-lookup"><span data-stu-id="b1fcb-102">SQLPrimaryKeys</span></span>
  <span data-ttu-id="b1fcb-103">資料表可能會有一個或多個資料行可以做為唯一的資料列識別碼，而不含 PRIMARY KEY 條件約束建立的資料表則會將空的結果集傳回給 SQLPrimaryKeys。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-103">A table might have a column or columns that can serve as unique row identifiers, and tables created without a PRIMARY KEY constraint return an empty result set to SQLPrimaryKeys.</span></span> <span data-ttu-id="b1fcb-104">ODBC 函數[SQLSpecialColumns](sqlspecialcolumns.md)會報告沒有主鍵之資料表的資料列識別碼候選項。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-104">The ODBC function [SQLSpecialColumns](sqlspecialcolumns.md) reports row identifier candidates for tables without primary keys.</span></span>  
  
 <span data-ttu-id="b1fcb-105">SQLPrimaryKeys 會傳回 SQL_SUCCESS *CatalogName*、 *SchemaName*或*TableName*參數的值是否存在。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-105">SQLPrimaryKeys returns SQL_SUCCESS whether or not values exist for *CatalogName*, *SchemaName*, or *TableName* parameters.</span></span> <span data-ttu-id="b1fcb-106">當這些參數中使用無效值時，SQLFetch 會傳回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-106">SQLFetch returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="b1fcb-107">SQLPrimaryKeys 可以在靜態伺服器資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-107">SQLPrimaryKeys can be executed on a static server cursor.</span></span> <span data-ttu-id="b1fcb-108">嘗試在可更新的 (動態或索引鍵集) 資料指標上執行 SQLPrimaryKeys 時，將會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-108">An attempt to execute SQLPrimaryKeys on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="b1fcb-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式藉由接受*CatalogName*參數的兩部分名稱，支援連結伺服器上之資料表的報告資訊： *Linked_Server_Name. Catalog_Name*。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports reporting information for tables on linked servers by accepting a two-part name for the *CatalogName* parameter: *Linked_Server_Name.Catalog_Name*.</span></span>  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a><span data-ttu-id="b1fcb-110">SQLPrimaryKeys 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="b1fcb-110">SQLPrimaryKeys and Table-Valued Parameters</span></span>  
 <span data-ttu-id="b1fcb-111">如果 SQL_SOPT_SS_NAME_SCOPE 語句屬性的值 SQL_SS_NAME_SCOPE_TABLE_TYPE，而不是其預設值 SQL_SS_NAME_SCOPE_TABLE，則 SQLPrimaryKeys 會傳回資料表類型之主鍵資料行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-111">If the statement attribute SQL_SOPT_SS_NAME_SCOPE has the value SQL_SS_NAME_SCOPE_TABLE_TYPE, rather than its default value of SQL_SS_NAME_SCOPE_TABLE, SQLPrimaryKeys will return information about primary key columns of table types.</span></span> <span data-ttu-id="b1fcb-112">如需 SQL_SOPT_SS_NAME_SCOPE 的詳細資訊，請參閱[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-112">For more information on SQL_SOPT_SS_NAME_SCOPE, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="b1fcb-113">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="b1fcb-113">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1fcb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1fcb-114">See Also</span></span>  
 <span data-ttu-id="b1fcb-115">[SQLPrimaryKeys 函式](https://go.microsoft.com/fwlink/?LinkId=59361) </span><span class="sxs-lookup"><span data-stu-id="b1fcb-115">[SQLPrimaryKeys Function](https://go.microsoft.com/fwlink/?LinkId=59361) </span></span>  
 [<span data-ttu-id="b1fcb-116">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="b1fcb-116">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
